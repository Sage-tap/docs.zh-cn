---
description: 了解详细信息： One-Way 服务
title: 单向服务
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], one-way service contracts
- WCF [WCF], one-way service contracts
- service contracts [WCF], defining one-way
ms.assetid: 19053a36-4492-45a3-bfe6-0365ee0205a3
ms.openlocfilehash: c614db0103506022da72e8f4659ae09e8b949a27
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99733692"
---
# <a name="one-way-services"></a><span data-ttu-id="7c875-103">单向服务</span><span class="sxs-lookup"><span data-stu-id="7c875-103">One-Way Services</span></span>

<span data-ttu-id="7c875-104">服务操作的默认行为是请求-答复模式。</span><span class="sxs-lookup"><span data-stu-id="7c875-104">The default behavior of a service operation is the request-reply pattern.</span></span> <span data-ttu-id="7c875-105">在请求-答复模式中，即使服务操作以代码形式表示为 `void` 方法，客户端也会等待答复消息。</span><span class="sxs-lookup"><span data-stu-id="7c875-105">In a request-reply pattern, the client waits for the reply message, even if the service operation is represented in code as a `void` method.</span></span> <span data-ttu-id="7c875-106">使用单向操作时，只能传输一个消息。</span><span class="sxs-lookup"><span data-stu-id="7c875-106">With a one-way operation, only one message is transmitted.</span></span> <span data-ttu-id="7c875-107">接收方不发送答复消息，发送方也不需要获得答复消息。</span><span class="sxs-lookup"><span data-stu-id="7c875-107">The receiver does not send a reply message, nor does the sender expect one.</span></span>  
  
 <span data-ttu-id="7c875-108">可以在以下情况下使用单向设计模式：</span><span class="sxs-lookup"><span data-stu-id="7c875-108">Use the one-way design pattern:</span></span>  
  
- <span data-ttu-id="7c875-109">客户端必须调用操作且在操作级别不受操作结果的影响。</span><span class="sxs-lookup"><span data-stu-id="7c875-109">When the client must call operations and is not affected by the result of the operation at the operation level.</span></span>  
  
- <span data-ttu-id="7c875-110">使用 <xref:System.ServiceModel.NetMsmqBinding> 或 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> 类。</span><span class="sxs-lookup"><span data-stu-id="7c875-110">When using the <xref:System.ServiceModel.NetMsmqBinding> or the <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> class.</span></span> <span data-ttu-id="7c875-111"> (有关此方案的详细信息，请参阅 [WCF 中的队列](queues-in-wcf.md)。 ) </span><span class="sxs-lookup"><span data-stu-id="7c875-111">(For more information about this scenario, see [Queues in WCF](queues-in-wcf.md).)</span></span>  
  
 <span data-ttu-id="7c875-112">如果是单向操作，则不会向客户端返回承载错误信息的响应消息。</span><span class="sxs-lookup"><span data-stu-id="7c875-112">When an operation is one-way, there is no response message to carry error information back to the client.</span></span> <span data-ttu-id="7c875-113">可以通过使用基础绑定的功能（如可靠会话）或通过设计一个可使用两个单向操作的双工服务协定（一个单向协定从客户端到服务，用于调用服务操作；另一个单向协定在服务和客户端之间，以使服务可以使用客户端实现的回调将错误发回到客户端）来检测错误条件。</span><span class="sxs-lookup"><span data-stu-id="7c875-113">You can detect error conditions by using features of the underlying binding, such as reliable sessions, or by designing a duplex service contract that uses two one-way operations—a one-way contract from the client to the service to call service operation and another one-way contract between the service and the client so that the service can send back faults to the client using a callback that the client implements.</span></span>  
  
 <span data-ttu-id="7c875-114">若要创建单向服务协定，请定义服务协定，将 <xref:System.ServiceModel.OperationContractAttribute> 类应用到每个操作，并将 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> 属性设置为 `true`，如下面的代码示例所示。</span><span class="sxs-lookup"><span data-stu-id="7c875-114">To create a one-way service contract, define your service contract, apply the <xref:System.ServiceModel.OperationContractAttribute> class to each operation, and set the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `true`, as shown in the following sample code.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOneWayCalculator  
{  
    [OperationContract(IsOneWay=true)]  
    void Add(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Subtract(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Multiply(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Divide(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="7c875-115">有关完整示例，请参阅 [单向](../samples/one-way.md) 示例。</span><span class="sxs-lookup"><span data-stu-id="7c875-115">For a complete example, see the [One-Way](../samples/one-way.md) sample.</span></span>  
  
## <a name="clients-blocking-with-one-way-operations"></a><span data-ttu-id="7c875-116">单向操作的客户端阻止</span><span class="sxs-lookup"><span data-stu-id="7c875-116">Clients Blocking with One-Way Operations</span></span>  

 <span data-ttu-id="7c875-117">必须认识到，尽管在将出站数据写入到网络连接后，某些单向应用程序会立即返回，但在某些情况下，绑定或服务的实现可能会导致 WCF 客户端使用单向操作阻止。</span><span class="sxs-lookup"><span data-stu-id="7c875-117">It is important to realize that while some one-way applications return as soon as the outbound data is written to the network connection, in several scenarios the implementation of a binding or of a service can cause a WCF client to block using one-way operations.</span></span> <span data-ttu-id="7c875-118">在 WCF 客户端应用程序中，在将出站数据写入到网络连接之前，WCF 客户端对象不会返回。</span><span class="sxs-lookup"><span data-stu-id="7c875-118">In WCF client applications, the WCF client object does not return until the outbound data has been written to the network connection.</span></span> <span data-ttu-id="7c875-119">所有消息交换模式都是如此，包括单向操作；这意味着在将数据写入传输时发生的任何问题都会阻止客户端返回。</span><span class="sxs-lookup"><span data-stu-id="7c875-119">This is true for all message exchange patterns, including one-way operations; this means that any problem writing the data to the transport prevents the client from returning.</span></span> <span data-ttu-id="7c875-120">结果可能是在将消息发送到服务的过程中出现异常或延迟，具体取决于所发生的问题。</span><span class="sxs-lookup"><span data-stu-id="7c875-120">Depending upon the problem, the result could be an exception or a delay in sending messages to the service.</span></span>  
  
 <span data-ttu-id="7c875-121">例如，如果传输找不到终结点，则会在短时间内引发 <xref:System.ServiceModel.EndpointNotFoundException?displayProperty=nameWithType> 异常。</span><span class="sxs-lookup"><span data-stu-id="7c875-121">For example, if the transport cannot find the endpoint, a <xref:System.ServiceModel.EndpointNotFoundException?displayProperty=nameWithType> exception is thrown without much delay.</span></span> <span data-ttu-id="7c875-122">但是，由于某种原因，服务也可能无法读取网络上的数据，这将阻止客户端传输发送操作返回。</span><span class="sxs-lookup"><span data-stu-id="7c875-122">However, it is also possible that the service is unable to read the data off the wire for some reason, which prevents the client transport send operation from returning.</span></span> <span data-ttu-id="7c875-123">在这些情况下，如果超出了客户端传输绑定上的 <xref:System.ServiceModel.Channels.Binding.SendTimeout%2A?displayProperty=nameWithType> 期限，则会引发 <xref:System.TimeoutException?displayProperty=nameWithType>，但会在超出超时期限后引发。</span><span class="sxs-lookup"><span data-stu-id="7c875-123">In these cases, if the <xref:System.ServiceModel.Channels.Binding.SendTimeout%2A?displayProperty=nameWithType> period on the client transport binding is exceeded, a <xref:System.TimeoutException?displayProperty=nameWithType> is thrown—but not until the timeout period has been exceeded.</span></span> <span data-ttu-id="7c875-124">也有可能向某一服务发送了过多的消息，而当超过某一特定点后，该服务无法处理这些消息。</span><span class="sxs-lookup"><span data-stu-id="7c875-124">It is also possible to fire so many messages at a service that the service cannot process them past a certain point.</span></span> <span data-ttu-id="7c875-125">在这种情况下，单向客户端也会发生阻止，直到服务可以处理这些消息或直到引发异常。</span><span class="sxs-lookup"><span data-stu-id="7c875-125">In this case, too, the one-way client blocks until the service can process the messages or until an exception is thrown.</span></span>  
  
 <span data-ttu-id="7c875-126">另一种不同的情况是服务的 <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> 属性设置为 <xref:System.ServiceModel.ConcurrencyMode.Single> 且绑定使用会话。</span><span class="sxs-lookup"><span data-stu-id="7c875-126">Another variation is the situation in which the service <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> property is set to <xref:System.ServiceModel.ConcurrencyMode.Single> and the binding uses sessions.</span></span> <span data-ttu-id="7c875-127">在这种情况下，调度程序会对传入消息强制执行排序（会话的需求），这会阻止从网络上读取后续的消息，直到服务处理完该会话的前一个消息为止。</span><span class="sxs-lookup"><span data-stu-id="7c875-127">In this case, the dispatcher enforces ordering on the incoming messages (a requirement of sessions), which prevents subsequent messages from being read off the network until the service has processed the preceding message for that session.</span></span> <span data-ttu-id="7c875-128">同样，客户端会发生阻止，但是否发生异常取决于客户端的超时设置结束前，服务是否能处理等待的数据。</span><span class="sxs-lookup"><span data-stu-id="7c875-128">Again, the client blocks, but whether an exception occurs depends upon whether the service is able to process the waiting data prior to the timeout settings on the client.</span></span>  
  
 <span data-ttu-id="7c875-129">通过在客户端对象和客户端传输发送操作之间插入一个缓冲器可以使此问题得到一些缓解。</span><span class="sxs-lookup"><span data-stu-id="7c875-129">You can mitigate some of this problem by inserting a buffer between the client object and the client transport's send operation.</span></span> <span data-ttu-id="7c875-130">例如，使用异步调用或使用内存中的消息队列可以使客户端对象迅速返回。</span><span class="sxs-lookup"><span data-stu-id="7c875-130">For example, using asynchronous calls or using an in-memory message queue can enable the client object to return quickly.</span></span> <span data-ttu-id="7c875-131">这两种方法都可以增强功能，但线程池和消息队列的大小仍具有限制。</span><span class="sxs-lookup"><span data-stu-id="7c875-131">Both approaches may increase functionality, but the size of the thread pool and the message queue still enforce limits.</span></span>  
  
 <span data-ttu-id="7c875-132">建议改为检查服务以及客户端上的各个控制机制，然后测试应用程序方案来确定任一端最佳配置。</span><span class="sxs-lookup"><span data-stu-id="7c875-132">It is recommended, instead, that you examine the various controls on the service as well as on the client, and then test your application scenarios to determine the best configuration on either side.</span></span> <span data-ttu-id="7c875-133">例如，如果使用会话会在服务上阻止消息的处理，则可以将 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> 属性设置为 <xref:System.ServiceModel.InstanceContextMode.PerCall>，使每个消息都可以通过不同的服务实例来处理，并将 <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> 设置为 <xref:System.ServiceModel.ConcurrencyMode.Multiple>，以便允许多个线程一次调度多个消息。</span><span class="sxs-lookup"><span data-stu-id="7c875-133">For example, if the use of sessions is blocking the processing of messages on your service, you can set the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> property to <xref:System.ServiceModel.InstanceContextMode.PerCall> so that each message can be processed by a different service instance, and set the <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> to <xref:System.ServiceModel.ConcurrencyMode.Multiple> in order to allow more than one thread to dispatch messages at a time.</span></span> <span data-ttu-id="7c875-134">另一个方法是提高服务和客户端绑定的读取配额。</span><span class="sxs-lookup"><span data-stu-id="7c875-134">Another approach is to increase the read quotas of the service and client bindings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c875-135">请参阅</span><span class="sxs-lookup"><span data-stu-id="7c875-135">See also</span></span>

- [<span data-ttu-id="7c875-136">单向</span><span class="sxs-lookup"><span data-stu-id="7c875-136">One-Way</span></span>](../samples/one-way.md)
