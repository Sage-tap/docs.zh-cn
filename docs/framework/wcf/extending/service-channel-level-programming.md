---
description: 了解详细信息：服务 Channel-Level 编程
title: 服务通道级编程
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8d8dcd85-0a05-4c44-8861-4a0b3b90cca9
ms.openlocfilehash: 9d89b073430ccdf80bdcbdfc50fd1e002fc807ff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99644056"
---
# <a name="service-channel-level-programming"></a><span data-ttu-id="c62f0-103">服务通道级编程</span><span class="sxs-lookup"><span data-stu-id="c62f0-103">Service Channel-Level Programming</span></span>

<span data-ttu-id="c62f0-104">本主题介绍如何 (WCF) 服务应用程序编写 Windows Communication Foundation，而无需使用 <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> 及其关联的对象模型。</span><span class="sxs-lookup"><span data-stu-id="c62f0-104">This topic describes how to write a Windows Communication Foundation (WCF) service application without using the <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> and its associated object model.</span></span>  
  
## <a name="receiving-messages"></a><span data-ttu-id="c62f0-105">接收消息</span><span class="sxs-lookup"><span data-stu-id="c62f0-105">Receiving Messages</span></span>  

 <span data-ttu-id="c62f0-106">若要准备接收并处理消息，必须执行下列步骤：</span><span class="sxs-lookup"><span data-stu-id="c62f0-106">To be ready to receive and process messages, the following steps are required:</span></span>  
  
1. <span data-ttu-id="c62f0-107">创建绑定。</span><span class="sxs-lookup"><span data-stu-id="c62f0-107">Create a binding.</span></span>  
  
2. <span data-ttu-id="c62f0-108">生成通道侦听器。</span><span class="sxs-lookup"><span data-stu-id="c62f0-108">Build a channel listener.</span></span>  
  
3. <span data-ttu-id="c62f0-109">打开通道侦听器。</span><span class="sxs-lookup"><span data-stu-id="c62f0-109">Open the channel listener.</span></span>  
  
4. <span data-ttu-id="c62f0-110">读取请求并发送答复。</span><span class="sxs-lookup"><span data-stu-id="c62f0-110">Read the request and send a reply.</span></span>  
  
5. <span data-ttu-id="c62f0-111">关闭所有通道对象。</span><span class="sxs-lookup"><span data-stu-id="c62f0-111">Close all channel objects.</span></span>  
  
#### <a name="creating-a-binding"></a><span data-ttu-id="c62f0-112">创建绑定</span><span class="sxs-lookup"><span data-stu-id="c62f0-112">Creating a Binding</span></span>  

 <span data-ttu-id="c62f0-113">侦听和接收消息的第一步是创建绑定。</span><span class="sxs-lookup"><span data-stu-id="c62f0-113">The first step in listening for and receiving messages is creating a binding.</span></span> <span data-ttu-id="c62f0-114">WCF 附带多个内置或系统提供的绑定，这些绑定可以通过实例化其中的一个来直接使用。</span><span class="sxs-lookup"><span data-stu-id="c62f0-114">WCF ships with several built-in or system-provided bindings that can be used directly by instantiating one of them.</span></span> <span data-ttu-id="c62f0-115">另外，你还可以创建自己的自定义绑定，方法是实例化 CustomBinding 类，这同时也是列表 1 中的代码所执行的操作。</span><span class="sxs-lookup"><span data-stu-id="c62f0-115">In addition, you can also create your own custom binding by instantiating a CustomBinding class which is what the code in listing 1 does.</span></span>  
  
 <span data-ttu-id="c62f0-116">下面的代码示例创建了 <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> 的一个实例，并将 <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> 添加到其 Elements 集合（这是用于生成通道堆栈的绑定元素的集合）。</span><span class="sxs-lookup"><span data-stu-id="c62f0-116">The code example below creates an instance of <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> and adds an <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> to its Elements collection which is a collection of binding elements that are used to build the channel stack.</span></span> <span data-ttu-id="c62f0-117">在此示例中，由于元素集合只有 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>，所以生成的通道堆栈仅具有 HTTP 传输通道。</span><span class="sxs-lookup"><span data-stu-id="c62f0-117">In this example, because the elements collection has only the <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, the resulting channel stack has only the HTTP transport channel.</span></span>  
  
#### <a name="building-a-channellistener"></a><span data-ttu-id="c62f0-118">生成 ChannelListener</span><span class="sxs-lookup"><span data-stu-id="c62f0-118">Building a ChannelListener</span></span>  

 <span data-ttu-id="c62f0-119">在创建绑定后，我们调用 <xref:System.ServiceModel.Channels.Binding.BuildChannelListener%2A?displayProperty=nameWithType> 来生成通道侦听器，其中类型参数就是要创建的通道形状。</span><span class="sxs-lookup"><span data-stu-id="c62f0-119">After creating a binding, we call <xref:System.ServiceModel.Channels.Binding.BuildChannelListener%2A?displayProperty=nameWithType> to build the channel listener where the type parameter is the channel shape to create.</span></span> <span data-ttu-id="c62f0-120">在此示例中使用 <xref:System.ServiceModel.Channels.IReplyChannel?displayProperty=nameWithType>，这是因为我们希望以请求/答复消息交换模式侦听传入的消息。</span><span class="sxs-lookup"><span data-stu-id="c62f0-120">In this example we are using <xref:System.ServiceModel.Channels.IReplyChannel?displayProperty=nameWithType> because we want to listen for incoming messages in a request/reply message exchange pattern.</span></span>  
  
 <span data-ttu-id="c62f0-121"><xref:System.ServiceModel.Channels.IReplyChannel> 用于接收请求消息，并发回答复消息。</span><span class="sxs-lookup"><span data-stu-id="c62f0-121"><xref:System.ServiceModel.Channels.IReplyChannel> is used for receiving request messages and sending back reply messages.</span></span> <span data-ttu-id="c62f0-122">调用 <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A?displayProperty=nameWithType> 会返回一个 <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>，可以用于接收请求消息以及发回答复消息。</span><span class="sxs-lookup"><span data-stu-id="c62f0-122">Calling <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A?displayProperty=nameWithType> returns an <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>, which can be used to receive the request message and to send back a reply message.</span></span>  
  
 <span data-ttu-id="c62f0-123">当创建侦听器时，我们传递发生侦听的网络地址，在此示例中为 `http://localhost:8080/channelapp`。</span><span class="sxs-lookup"><span data-stu-id="c62f0-123">When creating the listener, we pass the network address on which it listens, in this case `http://localhost:8080/channelapp`.</span></span> <span data-ttu-id="c62f0-124">通常，每个传输通道支持一个或可能多个地址方案，例如，HTTP 传输对 http 和 https 方案均予以支持。</span><span class="sxs-lookup"><span data-stu-id="c62f0-124">In general, each transport channel supports one or possibly several address schemes, for example, the HTTP transport supports both http and https schemes.</span></span>  
  
 <span data-ttu-id="c62f0-125">在创建侦听器时，我们还传递空的 <xref:System.ServiceModel.Channels.BindingParameterCollection?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="c62f0-125">We also pass an empty <xref:System.ServiceModel.Channels.BindingParameterCollection?displayProperty=nameWithType> when creating the listener.</span></span> <span data-ttu-id="c62f0-126">绑定参数是一种机制，用于传递那些控制侦听器生成方式的参数。</span><span class="sxs-lookup"><span data-stu-id="c62f0-126">A binding parameter is a mechanism to pass parameters that control how the listener should be built.</span></span> <span data-ttu-id="c62f0-127">在此示例中，我们不使用任何此类参数，所以我们传递的是一个空集合。</span><span class="sxs-lookup"><span data-stu-id="c62f0-127">In our example, we are not using any such parameters so we pass an empty collection.</span></span>  
  
#### <a name="listening-for-incoming-messages"></a><span data-ttu-id="c62f0-128">侦听传入消息</span><span class="sxs-lookup"><span data-stu-id="c62f0-128">Listening for Incoming Messages</span></span>  

 <span data-ttu-id="c62f0-129">然后，我们对侦听器调用 <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType>，开始接受通道。</span><span class="sxs-lookup"><span data-stu-id="c62f0-129">We then call <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> on the listener and start accepting channels.</span></span> <span data-ttu-id="c62f0-130"><xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A?displayProperty=nameWithType> 的行为取决于传输是面向连接还是与连接无关。</span><span class="sxs-lookup"><span data-stu-id="c62f0-130">The behavior of <xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A?displayProperty=nameWithType> depends on whether the transport is connection-oriented or connection-less.</span></span> <span data-ttu-id="c62f0-131">对于面向连接的传输，<xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A> 会一直阻止，直到新的连接请求传入（此时它会返回一个表示该新连接的新通道）。</span><span class="sxs-lookup"><span data-stu-id="c62f0-131">For connection-oriented transports, <xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A> blocks until a new connection request comes in at which point it returns a new channel that represents that new connection.</span></span> <span data-ttu-id="c62f0-132">对于与连接无关的传输（如 HTTP），<xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A> 会立即返回传输侦听器创建的唯一通道。</span><span class="sxs-lookup"><span data-stu-id="c62f0-132">For connection-less transports, such as HTTP, <xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A> returns immediately with the one and only channel that the transport listener creates.</span></span>  
  
 <span data-ttu-id="c62f0-133">在此示例中，侦听器返回一个实现 <xref:System.ServiceModel.Channels.IReplyChannel> 的通道。</span><span class="sxs-lookup"><span data-stu-id="c62f0-133">In this example, the listener returns a channel that implements <xref:System.ServiceModel.Channels.IReplyChannel>.</span></span> <span data-ttu-id="c62f0-134">为了在此通道上接收消息，我们首先对其调用 <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType>，以便将其置于一个准备进行通信的状态。</span><span class="sxs-lookup"><span data-stu-id="c62f0-134">To receive messages on this channel we first call <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> on it to place it in a state ready for communication.</span></span> <span data-ttu-id="c62f0-135">然后，我们调用 <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A>，它会处于阻止状态，直到消息达到。</span><span class="sxs-lookup"><span data-stu-id="c62f0-135">We then call <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> which blocks until a message arrives.</span></span>  
  
#### <a name="reading-the-request-and-sending-a-reply"></a><span data-ttu-id="c62f0-136">读取请求并发送答复</span><span class="sxs-lookup"><span data-stu-id="c62f0-136">Reading the Request and Sending a Reply</span></span>  

 <span data-ttu-id="c62f0-137">当 <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> 返回一个 <xref:System.ServiceModel.Channels.RequestContext>，我们使用其 <xref:System.ServiceModel.Channels.RequestContext.RequestMessage%2A> 属性获取收到的消息。</span><span class="sxs-lookup"><span data-stu-id="c62f0-137">When <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> returns a <xref:System.ServiceModel.Channels.RequestContext>, we get the received message using its <xref:System.ServiceModel.Channels.RequestContext.RequestMessage%2A> property.</span></span> <span data-ttu-id="c62f0-138">我们写出消息的操作和正文内容（假设它是一个字符串）。</span><span class="sxs-lookup"><span data-stu-id="c62f0-138">We write out the message’s action and body content, (which we assume is a string).</span></span>  
  
 <span data-ttu-id="c62f0-139">为了发送答复，我们在此例中创建一个新的答复消息，它会将我们在请求中收到的字符串数据传递回去。</span><span class="sxs-lookup"><span data-stu-id="c62f0-139">To send a reply, we create a new reply message in this case passing back the string data we received in the request.</span></span> <span data-ttu-id="c62f0-140">然后，我们调用 <xref:System.ServiceModel.Channels.RequestContext.Reply%2A> 以发送答复消息。</span><span class="sxs-lookup"><span data-stu-id="c62f0-140">We then call <xref:System.ServiceModel.Channels.RequestContext.Reply%2A> to send the reply message.</span></span>  
  
#### <a name="closing-objects"></a><span data-ttu-id="c62f0-141">关闭对象</span><span class="sxs-lookup"><span data-stu-id="c62f0-141">Closing Objects</span></span>  

 <span data-ttu-id="c62f0-142">为避免泄漏资源，很重要的一点就是关闭通信中不再需要使用的对象。</span><span class="sxs-lookup"><span data-stu-id="c62f0-142">To avoid leaking resources, it is very important to close objects used in communications when they are no longer required.</span></span> <span data-ttu-id="c62f0-143">在此示例中，我们关闭了请求消息、请求上下文、通道和侦听器。</span><span class="sxs-lookup"><span data-stu-id="c62f0-143">In this example we close the request message, the request context, the channel and the listener.</span></span>  
  
 <span data-ttu-id="c62f0-144">下面的代码示例演示通道侦听器仅接收一条消息所用的基本服务。</span><span class="sxs-lookup"><span data-stu-id="c62f0-144">The following code example shows a basic service in which a channel listener receives only one message.</span></span> <span data-ttu-id="c62f0-145">实际的服务会一直接受通道及接收消息，直到服务退出。</span><span class="sxs-lookup"><span data-stu-id="c62f0-145">A real service keeps accepting channels and receiving messages until the service exits.</span></span>  
  
 [!code-csharp[ChannelProgrammingBasic#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/channelprogrammingbasic/cs/serviceprogram.cs#1)]
 [!code-vb[ChannelProgrammingBasic#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelprogrammingbasic/vb/serviceprogram.vb#1)]
