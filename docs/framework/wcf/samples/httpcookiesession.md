---
description: 了解详细信息： HttpCookieSession
title: HttpCookieSession
ms.date: 03/30/2017
ms.assetid: 101cb624-8303-448a-a3af-933247c1e109
ms.openlocfilehash: b5b5a94cd6c019e39d95c1581ce88dbca4460ba6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631952"
---
# <a name="httpcookiesession"></a><span data-ttu-id="45b33-103">HttpCookieSession</span><span class="sxs-lookup"><span data-stu-id="45b33-103">HttpCookieSession</span></span>

<span data-ttu-id="45b33-104">此示例演示如何生成自定义协议通道，以便使用 HTTP Cookie 进行会话管理。</span><span class="sxs-lookup"><span data-stu-id="45b33-104">This sample demonstrates how to build a custom protocol channel to use HTTP cookies for session management.</span></span> <span data-ttu-id="45b33-105">此通道可实现 Windows Communication Foundation (WCF) 服务和客户端之间或 WCF 客户端与服务之间的通信。</span><span class="sxs-lookup"><span data-stu-id="45b33-105">This channel enables communication between Windows Communication Foundation (WCF) services and ASMX clients or between WCF clients and ASMX services.</span></span>  
  
 <span data-ttu-id="45b33-106">当客户端在基于会话的 .ASMX Web 服务中调用 Web 方法时，ASP.NET 引擎将执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="45b33-106">When a client calls a Web method in an ASMX Web service that is session-based, the ASP.NET engine does the following:</span></span>  
  
- <span data-ttu-id="45b33-107">生成一个唯一的 ID（会话 ID）。</span><span class="sxs-lookup"><span data-stu-id="45b33-107">Generates a unique ID (session ID).</span></span>  
  
- <span data-ttu-id="45b33-108">生成会话对象并将其与该唯一 ID 相关联。</span><span class="sxs-lookup"><span data-stu-id="45b33-108">Generates the session object and associates it with the unique ID.</span></span>  
  
- <span data-ttu-id="45b33-109">将该唯一 ID 添加到 Set-Cookie HTTP 响应头中并发送给客户端。</span><span class="sxs-lookup"><span data-stu-id="45b33-109">Adds the unique ID to a Set-Cookie HTTP response header and sends it to the client.</span></span>  
  
- <span data-ttu-id="45b33-110">根据它发送给客户端的会话 ID 在后续调用中标识客户端。</span><span class="sxs-lookup"><span data-stu-id="45b33-110">Identifies the client on subsequent calls based on the session ID it sends to it.</span></span>  
  
 <span data-ttu-id="45b33-111">客户端将此会话 ID 包含在发送给服务器的后续请求中。</span><span class="sxs-lookup"><span data-stu-id="45b33-111">The client includes this session ID in its subsequent requests to the server.</span></span> <span data-ttu-id="45b33-112">服务器使用来自客户端的会话 ID 为当前 HTTP 上下文加载相应的会话对象。</span><span class="sxs-lookup"><span data-stu-id="45b33-112">The server uses the session ID from the client to load the appropriate session object for the current HTTP context.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="45b33-113">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="45b33-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="45b33-114">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="45b33-114">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="45b33-115">如果此目录不存在，请参阅[Windows Communication Foundation (wcf) ，并 Windows Workflow Foundation (的 WF](https://www.microsoft.com/download/details.aspx?id=21459)) .NET Framework Windows Communication Foundation ([!INCLUDE[wf1](../../../../includes/wf1-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45b33-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="45b33-116">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="45b33-116">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\HttpCookieSession`  
  
## <a name="httpcookiesession-channel-message-exchange-pattern"></a><span data-ttu-id="45b33-117">HttpCookieSession 通道消息交换模式</span><span class="sxs-lookup"><span data-stu-id="45b33-117">HttpCookieSession Channel Message Exchange Pattern</span></span>  

 <span data-ttu-id="45b33-118">此示例为类似 ASMX 的方案启用会话。</span><span class="sxs-lookup"><span data-stu-id="45b33-118">This sample enables sessions for ASMX-like scenarios.</span></span> <span data-ttu-id="45b33-119">在通道堆栈的底部，我们使用了支持 <xref:System.ServiceModel.Channels.IRequestChannel> 和 <xref:System.ServiceModel.Channels.IReplyChannel> 的 HTTP 传输。</span><span class="sxs-lookup"><span data-stu-id="45b33-119">At the bottom of our channel stack, we have the HTTP transport that supports <xref:System.ServiceModel.Channels.IRequestChannel> and <xref:System.ServiceModel.Channels.IReplyChannel>.</span></span> <span data-ttu-id="45b33-120">通道的任务是向通道堆栈中的更高层提供会话。</span><span class="sxs-lookup"><span data-stu-id="45b33-120">It is the job of the channel to provide sessions to the higher levels of the channel stack.</span></span> <span data-ttu-id="45b33-121">此示例实现了两个支持会话的通道（<xref:System.ServiceModel.Channels.IRequestSessionChannel> 和 <xref:System.ServiceModel.Channels.IReplySessionChannel>）。</span><span class="sxs-lookup"><span data-stu-id="45b33-121">The sample implements two channels, (<xref:System.ServiceModel.Channels.IRequestSessionChannel> and <xref:System.ServiceModel.Channels.IReplySessionChannel>) that support sessions.</span></span>  
  
## <a name="service-channel"></a><span data-ttu-id="45b33-122">服务通道</span><span class="sxs-lookup"><span data-stu-id="45b33-122">Service Channel</span></span>  

 <span data-ttu-id="45b33-123">此示例在 `HttpCookieReplySessionChannelListener` 类中提供服务通道。</span><span class="sxs-lookup"><span data-stu-id="45b33-123">The sample provides a service channel in the `HttpCookieReplySessionChannelListener` class.</span></span> <span data-ttu-id="45b33-124">此类实现 <xref:System.ServiceModel.Channels.IChannelListener> 接口，并将通道堆栈中位于较低层的 <xref:System.ServiceModel.Channels.IReplyChannel> 通道转换为 <xref:System.ServiceModel.Channels.IReplySessionChannel>。</span><span class="sxs-lookup"><span data-stu-id="45b33-124">This class implements the <xref:System.ServiceModel.Channels.IChannelListener> interface and converts the <xref:System.ServiceModel.Channels.IReplyChannel> channel from lower in the channel stack to a <xref:System.ServiceModel.Channels.IReplySessionChannel>.</span></span> <span data-ttu-id="45b33-125">此过程可以分为以下几部分：</span><span class="sxs-lookup"><span data-stu-id="45b33-125">This process can be divided into the following parts:</span></span>  
  
- <span data-ttu-id="45b33-126">当通道侦听器打开时，它接受来自其内部侦听器的内部通道。</span><span class="sxs-lookup"><span data-stu-id="45b33-126">When the channel listener is opened, it accepts an inner channel from its inner listener.</span></span> <span data-ttu-id="45b33-127">因为内部侦听器是一个数据报侦听器，而被接受的通道的生存期与该侦听器的生存期相分离，所以我们可以关闭内部侦听器，只保留内部通道。</span><span class="sxs-lookup"><span data-stu-id="45b33-127">Because the inner listener is a datagram listener and the lifetime of an accepted channel is decoupled from the lifetime of the listener, we can close the inner listener and only hold on to the inner channel</span></span>  
  
    ```csharp  
                this.innerChannelListener.Open(timeoutHelper.RemainingTime());  
    this.innerChannel = this.innerChannelListener.AcceptChannel(timeoutHelper.RemainingTime());  
    this.innerChannel.Open(timeoutHelper.RemainingTime());  
    this.innerChannelListener.Close(timeoutHelper.RemainingTime());  
    ```  
  
- <span data-ttu-id="45b33-128">当打开进程完成后，我们设置一个消息循环，以接收来自内部通道的消息。</span><span class="sxs-lookup"><span data-stu-id="45b33-128">When the open process completes, we set up a message loop to receive messages from the inner channel.</span></span>  
  
    ```csharp  
    IAsyncResult result = BeginInnerReceiveRequest();  
    if (result != null && result.CompletedSynchronously)  
    {  
       // do not block the user thread  
       this.completeReceiveCallback ??= new WaitCallback(CompleteReceiveCallback);
       ThreadPool.QueueUserWorkItem(this.completeReceiveCallback, result);  
    }  
    ```  
  
- <span data-ttu-id="45b33-129">当消息到达后，服务通道检查会话标识符并多路分解到相应的会话通道。</span><span class="sxs-lookup"><span data-stu-id="45b33-129">When a message arrives, the service channel examines the session identifier and de-multiplexes to the appropriate session channel.</span></span> <span data-ttu-id="45b33-130">通道侦听器维护一个字典，该字典将会话标识符映射到会话通道实例。</span><span class="sxs-lookup"><span data-stu-id="45b33-130">The channel listener maintains a dictionary that maps the session identifiers to the session channel instances.</span></span>  
  
    ```csharp  
    Dictionary<string, IReplySessionChannel> channelMapping;  
    ```  
  
 <span data-ttu-id="45b33-131">`HttpCookieReplySessionChannel` 类实现 <xref:System.ServiceModel.Channels.IReplySessionChannel>。</span><span class="sxs-lookup"><span data-stu-id="45b33-131">The `HttpCookieReplySessionChannel` class implements <xref:System.ServiceModel.Channels.IReplySessionChannel>.</span></span> <span data-ttu-id="45b33-132">通道堆栈的较高层调用 <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> 方法来读取此会话的请求。</span><span class="sxs-lookup"><span data-stu-id="45b33-132">Higher levels of the channel stack call the <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> method to read requests for this session.</span></span> <span data-ttu-id="45b33-133">每个会话通道具有一个专用的消息队列，该消息队列由服务通道进行填充。</span><span class="sxs-lookup"><span data-stu-id="45b33-133">Each session channel has a private message queue that is populated by the service channel.</span></span>  
  
```csharp  
InputQueue<RequestContext> requestQueue;  
```  
  
 <span data-ttu-id="45b33-134">当有人调用 <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> 方法，而消息队列中没有消息时，通道将等待指定的时间量，然后自行关闭。</span><span class="sxs-lookup"><span data-stu-id="45b33-134">In the case when someone calls the <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> method and there are no messages in the message queue, the channel waits for a specified amount of time before shutting itself down.</span></span> <span data-ttu-id="45b33-135">这会清除为非 WCF 客户端创建的会话通道。</span><span class="sxs-lookup"><span data-stu-id="45b33-135">This cleans up the session channels created for non-WCF clients.</span></span>  
  
 <span data-ttu-id="45b33-136">我们使用 `channelMapping` 跟踪 `ReplySessionChannels`，并且在所有已接受的通道全部关闭之前不会关闭基础 `innerChannel`。</span><span class="sxs-lookup"><span data-stu-id="45b33-136">We use the `channelMapping` to track the `ReplySessionChannels`, and we do not close our underlying `innerChannel` until all the accepted channels have been closed.</span></span> <span data-ttu-id="45b33-137">这样使 `HttpCookieReplySessionChannel` 的生存期可以超过 `HttpCookieReplySessionChannelListener`。</span><span class="sxs-lookup"><span data-stu-id="45b33-137">This way `HttpCookieReplySessionChannel` can exist beyond the lifetime of `HttpCookieReplySessionChannelListener`.</span></span> <span data-ttu-id="45b33-138">我们也无需担心侦听器会在我们下面收集垃圾，因为已接受的通道通过 `OnClosed` 回调保留对其侦听器的引用。</span><span class="sxs-lookup"><span data-stu-id="45b33-138">We also do not have to worry about the listener getting garbage collected underneath us because the accepted channels keep a reference to their listener through the `OnClosed` callback.</span></span>  
  
## <a name="client-channel"></a><span data-ttu-id="45b33-139">客户端通道</span><span class="sxs-lookup"><span data-stu-id="45b33-139">Client channel</span></span>  

 <span data-ttu-id="45b33-140">对应的客户端通道位于 `HttpCookieSessionChannelFactory` 类中。</span><span class="sxs-lookup"><span data-stu-id="45b33-140">The corresponding client channel is in the `HttpCookieSessionChannelFactory` class.</span></span> <span data-ttu-id="45b33-141">在创建通道的过程中，通道工厂使用 `HttpCookieRequestSessionChannel` 包装内部请求通道。</span><span class="sxs-lookup"><span data-stu-id="45b33-141">During channel creation, the channel factory wraps the inner request channel with an `HttpCookieRequestSessionChannel`.</span></span> <span data-ttu-id="45b33-142">`HttpCookieRequestSessionChannel` 类将调用转发给基础请求通道。</span><span class="sxs-lookup"><span data-stu-id="45b33-142">The `HttpCookieRequestSessionChannel` class forwards the calls to the underlying request channel.</span></span> <span data-ttu-id="45b33-143">当客户端关闭代理时，`HttpCookieRequestSessionChannel` 向服务发送一条指明该通道正在关闭的消息。</span><span class="sxs-lookup"><span data-stu-id="45b33-143">When the client closes the proxy, `HttpCookieRequestSessionChannel` sends a message to the service that indicates that the channel is being closed.</span></span> <span data-ttu-id="45b33-144">因此，服务通道堆栈可以正常关闭正在使用的会话通道。</span><span class="sxs-lookup"><span data-stu-id="45b33-144">Thus, the service channel stack can gracefully shutdown the session channel that is in use.</span></span>  
  
## <a name="binding-and-binding-element"></a><span data-ttu-id="45b33-145">绑定和绑定元素</span><span class="sxs-lookup"><span data-stu-id="45b33-145">Binding and Binding Element</span></span>  

 <span data-ttu-id="45b33-146">创建服务和客户端通道后，下一步是将它们集成到 WCF 运行时中。</span><span class="sxs-lookup"><span data-stu-id="45b33-146">After creating the service and client channels, the next step is to integrate them into the WCF runtime.</span></span> <span data-ttu-id="45b33-147">通道通过绑定和绑定元素向 WCF 公开。</span><span class="sxs-lookup"><span data-stu-id="45b33-147">Channels are exposed to WCF through bindings and binding elements.</span></span> <span data-ttu-id="45b33-148">绑定由一个或多个绑定元素组成。</span><span class="sxs-lookup"><span data-stu-id="45b33-148">A binding consists of one or many binding elements.</span></span> <span data-ttu-id="45b33-149">WCF 提供了多个系统定义的绑定;例如，BasicHttpBinding 或 WSHttpBinding。</span><span class="sxs-lookup"><span data-stu-id="45b33-149">WCF offers several system-defined bindings; for example, BasicHttpBinding or WSHttpBinding.</span></span> <span data-ttu-id="45b33-150">`HttpCookieSessionBindingElement` 类包含绑定元素的实现。</span><span class="sxs-lookup"><span data-stu-id="45b33-150">The `HttpCookieSessionBindingElement` class contains the implementation for the binding element.</span></span> <span data-ttu-id="45b33-151">它重写通道侦听器和通道工厂创建方法，以进行必要的通道侦听器或通道工厂实例化。</span><span class="sxs-lookup"><span data-stu-id="45b33-151">It overrides the channel listener and channel factory creation methods to do the necessary channel listener or channel factory instantiations.</span></span>  
  
 <span data-ttu-id="45b33-152">此示例使用策略断言作为服务说明。</span><span class="sxs-lookup"><span data-stu-id="45b33-152">The sample uses policy assertions for the service description.</span></span> <span data-ttu-id="45b33-153">这使得此示例能够将其通道要求发布给其他可以使用服务的客户端。</span><span class="sxs-lookup"><span data-stu-id="45b33-153">This allows the sample to publish its channel requirements to other clients that can consume the service.</span></span> <span data-ttu-id="45b33-154">例如，此绑定元素发布策略断言，以使潜在的客户端知道它支持会话。</span><span class="sxs-lookup"><span data-stu-id="45b33-154">For example, this binding element publishes policy assertions to let potential clients know that it supports sessions.</span></span> <span data-ttu-id="45b33-155">因为此示例在绑定元素配置中启用了 `ExchangeTerminateMessage` 属性，它增加了必要断言，以表明服务支持通过额外的消息交换操作终止会话对话。</span><span class="sxs-lookup"><span data-stu-id="45b33-155">Because the sample enables the `ExchangeTerminateMessage` property in the binding element configuration, it adds the necessary assertions to show that the service supports an extra message exchange action to terminate the session conversation.</span></span> <span data-ttu-id="45b33-156">客户端然后可以使用此操作。</span><span class="sxs-lookup"><span data-stu-id="45b33-156">Clients can then use this action.</span></span> <span data-ttu-id="45b33-157">下面的 WSDL 代码演示了从 `HttpCookieSessionBindingElement` 中创建的策略断言。</span><span class="sxs-lookup"><span data-stu-id="45b33-157">The following WSDL code shows the policy assertions created from the `HttpCookieSessionBindingElement`.</span></span>  
  
```xml  
<wsp:Policy wsu:Id="HttpCookieSessionBinding_IWcfCookieSessionService_policy" xmlns:wsp="http://schemas.xmlsoap.org/ws/2004/09/policy" xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
<wsp:ExactlyOne>  
<wsp:All>  
<wspe:Utf816FFFECharacterEncoding xmlns:wspe="http://schemas.xmlsoap.org/ws/2004/09/policy/encoding"/>  
<mhsc:httpSessionCookie xmlns:mhsc="http://samples.microsoft.com/wcf/mhsc/policy"/>  
</wsp:All>  
</wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="45b33-158">`HttpCookieSessionBinding` 类是一个系统提供的绑定，它使用上面介绍的绑定元素。</span><span class="sxs-lookup"><span data-stu-id="45b33-158">The `HttpCookieSessionBinding` class is a system-provided binding that uses the binding element described previously.</span></span>  
  
## <a name="adding-the-channel-to-the-configuration-system"></a><span data-ttu-id="45b33-159">向配置系统中添加通道</span><span class="sxs-lookup"><span data-stu-id="45b33-159">Adding the Channel to the Configuration System</span></span>  

 <span data-ttu-id="45b33-160">此示例提供了两个类，它们通过配置公开示例通道。</span><span class="sxs-lookup"><span data-stu-id="45b33-160">The sample provides two classes that expose the sample channel through configuration.</span></span> <span data-ttu-id="45b33-161">第一个类是适用于 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> 的 `HttpCookieSessionBindingElement`。</span><span class="sxs-lookup"><span data-stu-id="45b33-161">The first is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> for the `HttpCookieSessionBindingElement`.</span></span> <span data-ttu-id="45b33-162">批量实现委派给从 `HttpCookieSessionBindingConfigurationElement` 派生的 <xref:System.ServiceModel.Configuration.StandardBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="45b33-162">The bulk of the implementation is delegated to the `HttpCookieSessionBindingConfigurationElement`, which derives from <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span></span> <span data-ttu-id="45b33-163">`HttpCookieSessionBindingConfigurationElement` 的属性与 `HttpCookieSessionBindingElement` 上的属性相对应。</span><span class="sxs-lookup"><span data-stu-id="45b33-163">The `HttpCookieSessionBindingConfigurationElement` has properties that correspond to the properties on `HttpCookieSessionBindingElement`.</span></span>  
  
### <a name="binding-element-extension-section"></a><span data-ttu-id="45b33-164">绑定元素扩展节</span><span class="sxs-lookup"><span data-stu-id="45b33-164">Binding Element Extension Section</span></span>  

 <span data-ttu-id="45b33-165">`HttpCookieSessionBindingElementSection` 节是一个 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>，它向配置系统公开 `HttpCookieSessionBindingElement`。</span><span class="sxs-lookup"><span data-stu-id="45b33-165">The section `HttpCookieSessionBindingElementSection` is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> that exposes `HttpCookieSessionBindingElement` to the configuration system.</span></span> <span data-ttu-id="45b33-166">通过对配置节名称进行一些重写，可以定义绑定元素的类型以及如何创建绑定元素。</span><span class="sxs-lookup"><span data-stu-id="45b33-166">With a few overrides the configuration section name, the type of the binding element and how to create the binding element are defined.</span></span> <span data-ttu-id="45b33-167">然后，我们可以按如下方式注册配置文件中的扩展节：</span><span class="sxs-lookup"><span data-stu-id="45b33-167">We can then register the extension section in a configuration file as follows:</span></span>  
  
```xml  
<configuration>
    <system.serviceModel>
      <extensions>
        <bindingElementExtensions>
          <add name="httpCookieSession"
               type=  
"Microsoft.ServiceModel.Samples.HttpCookieSessionBindingElementElement,
                    HttpCookieSessionExtension, Version=1.0.0.0,
                    Culture=neutral, PublicKeyToken=null"/>  
        </bindingElementExtensions >  
      </extensions>  
  
      <bindings>  
      <customBinding>  
        <binding name="allowCookiesBinding">  
          <textMessageEncoding messageVersion="Soap11WSAddressing10" />  
          <httpCookieSession sessionTimeout="10" exchangeTerminateMessage="true" />  
          <httpTransport allowCookies="true" />  
        </binding>  
      </customBinding>  
      </bindings>
    </system.serviceModel>
</configuration>  
```  
  
## <a name="test-code"></a><span data-ttu-id="45b33-168">测试代码</span><span class="sxs-lookup"><span data-stu-id="45b33-168">Test Code</span></span>  

 <span data-ttu-id="45b33-169">使用此示例传输的测试代码位于 Client 和 Service 目录中。</span><span class="sxs-lookup"><span data-stu-id="45b33-169">Test code for using this sample transport is available in the Client and Service directories.</span></span> <span data-ttu-id="45b33-170">它包含两个测试-一个测试 `allowCookies` `true` 在客户端上使用设置为的绑定。</span><span class="sxs-lookup"><span data-stu-id="45b33-170">It consists of two tests—one test uses a binding with `allowCookies` set to `true` on the client.</span></span> <span data-ttu-id="45b33-171">第二个测试在该绑定上实现显式关闭（使用终止消息交换）。</span><span class="sxs-lookup"><span data-stu-id="45b33-171">The second test enables explicit shutdown (using the terminate message exchange) on the binding.</span></span>  
  
 <span data-ttu-id="45b33-172">运行示例时，您会看到以下输出：</span><span class="sxs-lookup"><span data-stu-id="45b33-172">When you run the sample, you should see the following output:</span></span>  
  
```console  
Simple binding:  
AddItem(10000,2): ItemCount=2  
AddItem(10550,5): ItemCount=7  
RemoveItem(10550,2): ItemCount=5  
Items  
10000, 2  
10550, 3  
Smart binding:  
AddItem(10000,2): ItemCount=2  
AddItem(10550,5): ItemCount=7  
RemoveItem(10550,2): ItemCount=5  
Items  
10000, 2  
10550, 3  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="45b33-173">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="45b33-173">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="45b33-174">使用以下命令安装 ASP.NET 4.0。</span><span class="sxs-lookup"><span data-stu-id="45b33-174">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="45b33-175">确保已对 [Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="45b33-175">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="45b33-176">若要生成解决方案，请按照 [生成 Windows Communication Foundation 示例](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="45b33-176">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="45b33-177">若要以单机配置或跨计算机配置来运行示例，请按照 [运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="45b33-177">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
