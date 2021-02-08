---
description: 了解详细信息：服务和事务
title: 服务和事务
ms.date: 03/30/2017
helpviewer_keywords:
- service contracts [WCF], designing services and transactions
ms.assetid: 864813ff-2709-4376-912d-f5c8d318c460
ms.openlocfilehash: 4126ca139bd2097aeaaff756de694d0ff0061b5d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792968"
---
# <a name="services-and-transactions"></a><span data-ttu-id="e7653-103">服务和事务</span><span class="sxs-lookup"><span data-stu-id="e7653-103">Services and Transactions</span></span>

<span data-ttu-id="e7653-104">Windows Communication Foundation (WCF) 应用程序可以从客户端中启动事务，并在服务操作中协调事务。</span><span class="sxs-lookup"><span data-stu-id="e7653-104">Windows Communication Foundation (WCF) applications can initiate a transaction from within a client and coordinate the transaction within the service operation.</span></span> <span data-ttu-id="e7653-105">客户端可以启动事务和调用多个服务操作，并可确保服务操作作为一个单元提交或回滚。</span><span class="sxs-lookup"><span data-stu-id="e7653-105">Clients can initiate a transaction and invoke several service operations and ensure that the service operations are either committed or rolled back as a single unit.</span></span>  
  
 <span data-ttu-id="e7653-106">通过为需要客户端事务的服务操作指定 <xref:System.ServiceModel.ServiceBehaviorAttribute> 并设置其 <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> 和 <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> 属性，可以启用服务协定中的事务行为。</span><span class="sxs-lookup"><span data-stu-id="e7653-106">You can enable the transaction behavior in the service contract by specifying a <xref:System.ServiceModel.ServiceBehaviorAttribute> and setting its <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> and <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> properties for service operations that require client transactions.</span></span> <span data-ttu-id="e7653-107"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> 参数指定在没有引发未处理异常的情况下，在其中执行方法的事务是否自动完成。</span><span class="sxs-lookup"><span data-stu-id="e7653-107">The <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> parameter specifies whether the transaction in which the method executes is automatically completed if no unhandled exceptions are thrown.</span></span> <span data-ttu-id="e7653-108">有关这些属性的详细信息，请[参阅。](./feature-details/servicemodel-transaction-attributes.md)</span><span class="sxs-lookup"><span data-stu-id="e7653-108">For more information about these attributes, see [ServiceModel Transaction Attributes](./feature-details/servicemodel-transaction-attributes.md).</span></span>  
  
 <span data-ttu-id="e7653-109">在服务操作中执行并由资源管理器管理的工作（如记录数据库更新）是客户端事务的一部分。</span><span class="sxs-lookup"><span data-stu-id="e7653-109">The work that is performed in the service operations and managed by a resource manager, such as logging database updates, is part of the client’s transaction.</span></span>  
  
 <span data-ttu-id="e7653-110">下面的示例演示如何使用 <xref:System.ServiceModel.ServiceBehaviorAttribute> 和 <xref:System.ServiceModel.OperationBehaviorAttribute> 属性来控制服务端的事务行为。</span><span class="sxs-lookup"><span data-stu-id="e7653-110">The following sample demonstrates usage of the <xref:System.ServiceModel.ServiceBehaviorAttribute> and <xref:System.ServiceModel.OperationBehaviorAttribute> attributes to control service-side transaction behavior.</span></span>  
  
```csharp
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CalculatorService: ICalculatorLog  
{  
    [OperationBehavior(TransactionScopeRequired = true,  
                           TransactionAutoComplete = true)]  
    public double Add(double n1, double n2)  
    {  
        recordToLog($"Added {n1} to {n2}");
        return n1 + n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,
                               TransactionAutoComplete = true)]  
    public double Subtract(double n1, double n2)  
    {  
        recordToLog($"Subtracted {n1} from {n2}");
        return n1 - n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,
                                       TransactionAutoComplete = true)]  
    public double Multiply(double n1, double n2)  
    {  
        recordToLog($"Multiplied {n1} by {n2}");
        return n1 * n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,
                                       TransactionAutoComplete = true)]  
    public double Divide(double n1, double n2)  
    {  
        recordToLog($"Divided {n1} by {n2}", n1, n2);
        return n1 / n2;  
    }  
  
}  
```  
  
 <span data-ttu-id="e7653-111">可以通过将客户端和服务绑定配置为使用 WS-AtomicTransaction 协议，并将元素设置为，来启用事务和事务流 [\<transactionFlow>](../configure-apps/file-schema/wcf/transactionflow.md) `true` ，如下面的示例配置中所示。</span><span class="sxs-lookup"><span data-stu-id="e7653-111">You can enable transactions and transaction flow by configuring the client and service bindings to use the WS-AtomicTransaction protocol, and setting the [\<transactionFlow>](../configure-apps/file-schema/wcf/transactionflow.md) element to `true`, as shown in the following sample configuration.</span></span>  
  
```xml  
<client>  
    <endpoint address="net.tcp://localhost/ServiceModelSamples/service"
          binding="netTcpBinding"
          bindingConfiguration="netTcpBindingWSAT"
          contract="Microsoft.ServiceModel.Samples.ICalculatorLog" />  
</client>  
  
<bindings>  
    <netTcpBinding>  
        <binding name="netTcpBindingWSAT"  
                transactionFlow="true"  
                transactionProtocol="WSAtomicTransactionOctober2004" />  
     </netTcpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="e7653-112">客户端可以通过创建 <xref:System.Transactions.TransactionScope>，然后在该事务范围内调用服务操作来开始该事务。</span><span class="sxs-lookup"><span data-stu-id="e7653-112">Clients can begin a transaction by creating a <xref:System.Transactions.TransactionScope> and invoking service operations within the scope of the transaction.</span></span>  
  
```csharp
using (TransactionScope ts = new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    //Do work here  
    ts.Complete();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="e7653-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="e7653-113">See also</span></span>

- [<span data-ttu-id="e7653-114">System.ServiceModel 中的事务性支持</span><span class="sxs-lookup"><span data-stu-id="e7653-114">Transactional Support in System.ServiceModel</span></span>](./feature-details/transactional-support-in-system-servicemodel.md)
- [<span data-ttu-id="e7653-115">事务模型</span><span class="sxs-lookup"><span data-stu-id="e7653-115">Transaction Models</span></span>](./feature-details/transaction-models.md)
- [<span data-ttu-id="e7653-116">WS 事务流</span><span class="sxs-lookup"><span data-stu-id="e7653-116">WS Transaction Flow</span></span>](./samples/ws-transaction-flow.md)
