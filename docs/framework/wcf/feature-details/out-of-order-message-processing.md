---
description: 了解详细信息：不排序消息处理
title: 无序消息处理
ms.date: 03/30/2017
ms.assetid: 33fc62a5-5d59-461c-a37a-0e1b51ac763d
ms.openlocfilehash: 4349b7d72c080dff579eda18ce51de99ab5e91fb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99733601"
---
# <a name="out-of-order-message-processing"></a><span data-ttu-id="ff3e7-103">无序消息处理</span><span class="sxs-lookup"><span data-stu-id="ff3e7-103">Out-of-Order Message Processing</span></span>

<span data-ttu-id="ff3e7-104">工作流服务可能依赖于按特定顺序发送的消息。</span><span class="sxs-lookup"><span data-stu-id="ff3e7-104">Workflow services may depend on messages being sent in a specific order.</span></span> <span data-ttu-id="ff3e7-105">工作流服务包含一个或多个 <xref:System.ServiceModel.Activities.Receive> 活动，而每个 <xref:System.ServiceModel.Activities.Receive> 活动需要一条特定消息。</span><span class="sxs-lookup"><span data-stu-id="ff3e7-105">A workflow service contains one or more <xref:System.ServiceModel.Activities.Receive> activities and each <xref:System.ServiceModel.Activities.Receive> activity is expecting a specific message.</span></span> <span data-ttu-id="ff3e7-106">如果无法保证单独传递传输，客户端发送的消息可能会延迟，从而可能无法按工作流服务所需的顺序传递消息。</span><span class="sxs-lookup"><span data-stu-id="ff3e7-106">Without particular transport delivery guarantees, messages sent by clients may be delayed and therefore delivered in an order the workflow service may not expect.</span></span> <span data-ttu-id="ff3e7-107">实现无需按特定顺序传送消息的工作流服务时，通常使用并行活动来完成此操作。</span><span class="sxs-lookup"><span data-stu-id="ff3e7-107">Implementing a workflow service that does not require messages be sent in a specific order is normally done using a Parallel activity.</span></span> <span data-ttu-id="ff3e7-108">对于更复杂的应用程序协议，工作流将很快变得极其复杂。</span><span class="sxs-lookup"><span data-stu-id="ff3e7-108">For a more complicated application protocol, the workflow would become very complex very quickly.</span></span>  <span data-ttu-id="ff3e7-109">Windows Communication Foundation 中的无序消息处理功能 (WCF) 允许您创建这样的工作流，而无需使用嵌套的并行活动的所有复杂性。</span><span class="sxs-lookup"><span data-stu-id="ff3e7-109">The out-of-order message processing feature in Windows Communication Foundation (WCF) allows you to create such a workflow without all of the complexity of nested Parallel activities.</span></span> <span data-ttu-id="ff3e7-110">只支持对支持的通道 <xref:System.ServiceModel.Channels.ReceiveContext> （例如 WCF MSMQ 绑定）进行不序消息处理。</span><span class="sxs-lookup"><span data-stu-id="ff3e7-110">Out-of-order message processing is only supported on channels that support <xref:System.ServiceModel.Channels.ReceiveContext> such as the WCF MSMQ bindings.</span></span>  
  
## <a name="enabling-out-of-order-message-processing"></a><span data-ttu-id="ff3e7-111">启用无序消息处理</span><span class="sxs-lookup"><span data-stu-id="ff3e7-111">Enabling Out-Of-Order Message Processing</span></span>  

 <span data-ttu-id="ff3e7-112">在 WorkflowService 上将 <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> 属性设置为`true` 即会启用无序消息处理。</span><span class="sxs-lookup"><span data-stu-id="ff3e7-112">Out-of-order message processing is enabled by setting the <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> property to `true` on the WorkflowService.</span></span> <span data-ttu-id="ff3e7-113">下面的示例演示如何在代码中设置 <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="ff3e7-113">The following example shows how to set the <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> property in code.</span></span>  
  
```csharp  
// Code: Opt-in to Buffered Receive processing...  
WorkflowService service = new WorkflowService  
{  
    Name="MyService",  
    Body = workflow,  
    AllowBufferedReceive = true  
};  
```  
  
 <span data-ttu-id="ff3e7-114">还可以将 `AllowBufferedReceive` 特性应用到 XAML 中的工作流服务，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="ff3e7-114">You can also apply the `AllowBufferedReceive` attribute to a workflow service in XAML as shown in the following example.</span></span>  
  
```xaml  
// Xaml: Opt-in to Buffered Receive processing...  
<WorkflowService AllowBufferedReceive="True">  
   <!--the actual children activities -->  
</Sequence>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ff3e7-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="ff3e7-115">See also</span></span>

- <xref:System.ServiceModel.Channels.ReceiveContext>
- [<span data-ttu-id="ff3e7-116">工作流服务</span><span class="sxs-lookup"><span data-stu-id="ff3e7-116">Workflow Services</span></span>](workflow-services.md)
- [<span data-ttu-id="ff3e7-117">队列和可靠会话</span><span class="sxs-lookup"><span data-stu-id="ff3e7-117">Queues and Reliable Sessions</span></span>](queues-and-reliable-sessions.md)
