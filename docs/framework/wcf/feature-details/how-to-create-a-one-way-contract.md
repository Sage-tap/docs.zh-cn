---
description: 了解详细信息：如何：创建 One-Way 协定
title: 如何：创建单向协定
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 85084cd9-31cc-4e95-b667-42ef01336622
ms.openlocfilehash: 465dc2da20288c918a70743fcbe3ed931620b33b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734719"
---
# <a name="how-to-create-a-one-way-contract"></a><span data-ttu-id="254f8-103">如何：创建单向协定</span><span class="sxs-lookup"><span data-stu-id="254f8-103">How to: Create a One-Way Contract</span></span>

<span data-ttu-id="254f8-104">本主题演示了创建使用单向协定的方法所需的基本步骤。</span><span class="sxs-lookup"><span data-stu-id="254f8-104">This topic shows the basic steps to create methods that use a one-way contract.</span></span> <span data-ttu-id="254f8-105">此类方法从客户端调用 Windows Communication Foundation (WCF) 服务，但不希望收到回复。</span><span class="sxs-lookup"><span data-stu-id="254f8-105">Such methods invoke operations on a Windows Communication Foundation (WCF) service from a client but do not expect a reply.</span></span> <span data-ttu-id="254f8-106">例如，可以使用这种类型的协定将通知发布给许多订户。</span><span class="sxs-lookup"><span data-stu-id="254f8-106">This type of contract can be used, for example, to publish notifications to many subscribers.</span></span> <span data-ttu-id="254f8-107">在创建双工（双向）协定（可使得客户端和服务器可以独立地相互通信，这样双方都可以启动对另一方的呼叫）时，还可以使用单向协定。</span><span class="sxs-lookup"><span data-stu-id="254f8-107">You can also use one-way contracts when creating a duplex (two-way) contract, which allows clients and servers to communicate with each other independently so that either can initiate calls to the other.</span></span> <span data-ttu-id="254f8-108">具体而言，这样做可允许服务器对客户端进行单向呼叫，而客户端可以将这些呼叫视为事件。</span><span class="sxs-lookup"><span data-stu-id="254f8-108">This can allow, in particular, the server to make one-way calls to the client that the client can treat as events.</span></span> <span data-ttu-id="254f8-109">有关指定单向方法的详细信息，请参见 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> 属性和 <xref:System.ServiceModel.OperationContractAttribute> 类。</span><span class="sxs-lookup"><span data-stu-id="254f8-109">For detailed information about specifying one-way methods, see the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property and the <xref:System.ServiceModel.OperationContractAttribute> class.</span></span>  
  
 <span data-ttu-id="254f8-110">有关创建双工协定的客户端应用程序的详细信息，请参阅 [如何：使用 One-Way 和 Request-Reply 协定访问服务](how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="254f8-110">For more information about creating a client application for a duplex contract, see [How to: Access Services with One-Way and Request-Reply Contracts](how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md).</span></span> <span data-ttu-id="254f8-111">有关工作示例，请参阅单向[示例。](../samples/one-way.md)</span><span class="sxs-lookup"><span data-stu-id="254f8-111">For a working sample, see the [One-Way](../samples/one-way.md) sample.</span></span>  
  
### <a name="to-create-a-one-way-contract"></a><span data-ttu-id="254f8-112">创建单向协定</span><span class="sxs-lookup"><span data-stu-id="254f8-112">To create a one-way contract</span></span>  
  
1. <span data-ttu-id="254f8-113">通过将 <xref:System.ServiceModel.ServiceContractAttribute> 类应用到定义服务将要实现的方法的接口，创建服务协定。</span><span class="sxs-lookup"><span data-stu-id="254f8-113">Create the service contract by applying the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface that defines the methods the service is to implement.</span></span>  
  
2. <span data-ttu-id="254f8-114">通过将 <xref:System.ServiceModel.OperationContractAttribute> 类应用到相应的方法，指示客户端可以调用接口中的哪些方法。</span><span class="sxs-lookup"><span data-stu-id="254f8-114">Indicate which methods in the interface a client can invoked by applying the <xref:System.ServiceModel.OperationContractAttribute> class to them.</span></span>  
  
3. <span data-ttu-id="254f8-115">通过将 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> 属性设置为 `true`，可将不得具有输出（没有返回值且没有 out 参数或 ref 参数）的操作指定为单向操作。</span><span class="sxs-lookup"><span data-stu-id="254f8-115">Designate operations that must have no output (no return value and no out or ref parameters) as one-way by setting the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `true`.</span></span> <span data-ttu-id="254f8-116">注意，默认情况下，使用 <xref:System.ServiceModel.OperationContractAttribute> 类的操作都满足请求-答复协定，原因是默认情况下 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> 属性为 `false`。</span><span class="sxs-lookup"><span data-stu-id="254f8-116">Note that the operations that carry the <xref:System.ServiceModel.OperationContractAttribute> class satisfy a request-reply contract by default because the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property is `false` by default.</span></span> <span data-ttu-id="254f8-117">因此，如果需要对方法使用单向协定，则必须将 attribute 属性的值显式指定为 `true`。</span><span class="sxs-lookup"><span data-stu-id="254f8-117">So you must explicitly specify the value of the attribute property to be `true` if you want a one-way contract for the method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="254f8-118">示例</span><span class="sxs-lookup"><span data-stu-id="254f8-118">Example</span></span>  

 <span data-ttu-id="254f8-119">下面的代码示例定义一个服务协定，其中包括几个单向方法。</span><span class="sxs-lookup"><span data-stu-id="254f8-119">The following code example defines a contract for a service that includes several one-way methods.</span></span> <span data-ttu-id="254f8-120">除了 `Equals` 默认设置为请求-答复并返回结果之外，所有的方法都具有单向协定。</span><span class="sxs-lookup"><span data-stu-id="254f8-120">All of the methods have one-way contracts except `Equals`, which defaults to request-reply and returns a result.</span></span>  
  
 [!code-csharp[S_Service_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_service_session/cs/service.cs#1)]
 [!code-vb[S_Service_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_service_session/vb/service.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="254f8-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="254f8-121">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [<span data-ttu-id="254f8-122">设计和实现服务</span><span class="sxs-lookup"><span data-stu-id="254f8-122">Designing and Implementing Services</span></span>](../designing-and-implementing-services.md)
- [<span data-ttu-id="254f8-123">如何：定义服务协定</span><span class="sxs-lookup"><span data-stu-id="254f8-123">How to: Define a Service Contract</span></span>](../how-to-define-a-wcf-service-contract.md)
- [<span data-ttu-id="254f8-124">会话</span><span class="sxs-lookup"><span data-stu-id="254f8-124">Session</span></span>](../samples/session.md)
- [<span data-ttu-id="254f8-125">如何：创建双工协定</span><span class="sxs-lookup"><span data-stu-id="254f8-125">How to: Create a Duplex Contract</span></span>](how-to-create-a-duplex-contract.md)
