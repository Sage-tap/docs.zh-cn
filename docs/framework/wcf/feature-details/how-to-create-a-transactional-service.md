---
description: 了解详细信息：如何：创建事务性服务
title: 如何：创建事务性服务
ms.date: 03/30/2017
ms.assetid: 1bd2e4ed-a557-43f9-ba98-4c70cb75c154
ms.openlocfilehash: 78ad922a7e1f174715be7bd1a8466572425411be
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643431"
---
# <a name="how-to-create-a-transactional-service"></a><span data-ttu-id="44039-103">如何：创建事务性服务</span><span class="sxs-lookup"><span data-stu-id="44039-103">How to: Create a Transactional Service</span></span>

<span data-ttu-id="44039-104">本示例演示创建事务性服务和使用客户端启动的事务协调服务操作的各个方面。</span><span class="sxs-lookup"><span data-stu-id="44039-104">This sample demonstrates various aspects of creating a transactional service and the use of a client-initiated transaction to coordinate service operations.</span></span>  
  
### <a name="creating-a-transactional-service"></a><span data-ttu-id="44039-105">创建事务性服务</span><span class="sxs-lookup"><span data-stu-id="44039-105">Creating a transactional service</span></span>  
  
1. <span data-ttu-id="44039-106">创建服务协定并用 <xref:System.ServiceModel.TransactionFlowOption> 枚举中所需的设置对操作进行批注以指定传入事务需求。</span><span class="sxs-lookup"><span data-stu-id="44039-106">Create a service contract and annotate the operations with the desired setting from the <xref:System.ServiceModel.TransactionFlowOption> enumeration to specify the incoming transaction requirements.</span></span> <span data-ttu-id="44039-107">请注意，您也可以将 <xref:System.ServiceModel.TransactionFlowAttribute> 放在要实现的服务类上。</span><span class="sxs-lookup"><span data-stu-id="44039-107">Note that you can also place the <xref:System.ServiceModel.TransactionFlowAttribute> on the service class being implemented.</span></span> <span data-ttu-id="44039-108">这允许接口的单一实现（而不是每个实现）使用这些事务设置。</span><span class="sxs-lookup"><span data-stu-id="44039-108">This allows for a single implementation of an interface to use these transaction settings, instead of every implementation.</span></span>  
  
    ```csharp
    [ServiceContract]  
    public interface ICalculator  
    {  
        [OperationContract]  
        // Use this to require an incoming transaction  
        [TransactionFlow(TransactionFlowOption.Mandatory)]  
        double Add(double n1, double n2);  
        [OperationContract]  
        // Use this to permit an incoming transaction  
        [TransactionFlow(TransactionFlowOption.Allowed)]  
        double Subtract(double n1, double n2);  
    }  
    ```  
  
2. <span data-ttu-id="44039-109">创建一个实现类，并使用 <xref:System.ServiceModel.ServiceBehaviorAttribute> 有选择地指定 <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> 和 <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A>。</span><span class="sxs-lookup"><span data-stu-id="44039-109">Create an implementation class, and use the <xref:System.ServiceModel.ServiceBehaviorAttribute> to optionally specify a <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> and a <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A>.</span></span> <span data-ttu-id="44039-110">应该注意的是，默认值为 60 秒的 <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> 和默认值为 <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> 的 `Unspecified` 适用于许多情况。</span><span class="sxs-lookup"><span data-stu-id="44039-110">You should note that in many cases, the default <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> of 60 seconds and the default <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> of `Unspecified` are appropriate.</span></span> <span data-ttu-id="44039-111">对于每个操作，可以根据 <xref:System.ServiceModel.OperationBehaviorAttribute> 属性的值，使用 <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> 属性指定在方法中执行的工作是否应在事务范围内发生。</span><span class="sxs-lookup"><span data-stu-id="44039-111">For each operation, you can use the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute to specify whether work performed within the method should occur within the scope of a transaction scope according to the value of the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> attribute.</span></span> <span data-ttu-id="44039-112">在本例中，用于 `Add` 方法的事务与从客户端流入的强制传入事务相同，用于 `Subtract` 方法的事务与传入事务相同（如果已从客户端流入了一个事务）或者是一个以隐式方式在本地创建的新事务。</span><span class="sxs-lookup"><span data-stu-id="44039-112">In this case, the transaction used for the `Add` method is the same as the mandatory incoming transaction that is flowed from the client, and the transaction used for the `Subtract` method is either the same as the incoming transaction if one was flowed from the client, or a new implicitly and locally created transaction.</span></span>  
  
    ```csharp
    [ServiceBehavior(  
        TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable,  
        TransactionTimeout = "00:00:45")]  
    public class CalculatorService : ICalculator  
    {  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Add(double n1, double n2)  
        {  
            // Perform transactional operation  
            RecordToLog($"Adding {n1} to {n2}");
            return n1 + n2;  
        }  
  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Subtract(double n1, double n2)  
        {  
            // Perform transactional operation  
            RecordToLog($"Subtracting {n2} from {n1}");
            return n1 - n2;  
        }  
  
        private static void RecordToLog(string recordText)  
        {  
            // Database operations omitted for brevity  
            // This is where the transaction provides specific benefit  
            // - changes to the database will be committed only when  
            // the transaction completes.  
        }  
    }  
    ```  
  
3. <span data-ttu-id="44039-113">在配置文件中配置绑定，指定事务上下文应进行流处理，并指定要使用的协议执行此操作。</span><span class="sxs-lookup"><span data-stu-id="44039-113">Configure the bindings in the configuration file, specifying that the transaction context should be flowed, and the protocols to be used to do so.</span></span> <span data-ttu-id="44039-114">有关详细信息，请参阅配置 [配置](servicemodel-transaction-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="44039-114">For more information, see [ServiceModel Transaction Configuration](servicemodel-transaction-configuration.md).</span></span> <span data-ttu-id="44039-115">具体地说，绑定类型是在终结点元素的 `binding` 属性中指定的。</span><span class="sxs-lookup"><span data-stu-id="44039-115">Specifically, the binding type is specified in the endpoint element’s `binding` attribute.</span></span> <span data-ttu-id="44039-116">[\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md)元素包含一个 `bindingConfiguration` 属性，该属性引用名为的绑定配置 `transactionalOleTransactionsTcpBinding` ，如下面的示例配置中所示。</span><span class="sxs-lookup"><span data-stu-id="44039-116">The [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) element contains a `bindingConfiguration` attribute that references a binding configuration named `transactionalOleTransactionsTcpBinding`, as shown in the following sample configuration.</span></span>  
  
    ```xml  
    <service name="CalculatorService">  
      <endpoint address="net.tcp://localhost:8008/CalcService"  
        binding="netTcpBinding"  
        bindingConfiguration="transactionalOleTransactionsTcpBinding"  
        contract="ICalculator"  
        name="OleTransactions_endpoint" />  
    </service>  
    ```  
  
     <span data-ttu-id="44039-117">事务流是在配置级别通过使用 `transactionFlow` 属性启用的，而事务协议是使用 `transactionProtocol` 属性指定的，如下面的配置中所示。</span><span class="sxs-lookup"><span data-stu-id="44039-117">Transaction flow is enabled at the configuration level by using the `transactionFlow` attribute, and the transaction protocol is specified using the `transactionProtocol` attribute, as shown in the following configuration.</span></span>  
  
    ```xml  
    <bindings>  
      <netTcpBinding>  
        <binding name="transactionalOleTransactionsTcpBinding"  
          transactionFlow="true"  
          transactionProtocol="OleTransactions"/>  
      </netTcpBinding>  
    </bindings>  
    ```  
  
### <a name="supporting-multiple-transaction-protocols"></a><span data-ttu-id="44039-118">支持多事务协议</span><span class="sxs-lookup"><span data-stu-id="44039-118">Supporting multiple transaction protocols</span></span>  
  
1. <span data-ttu-id="44039-119">为了获得最佳性能，应将 OleTransactions 协议用于涉及使用 Windows Communication Foundation (WCF) 编写的客户端和服务的方案。</span><span class="sxs-lookup"><span data-stu-id="44039-119">For optimal performance, you should use the OleTransactions protocol for scenarios involving a client and service written using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="44039-120">但是，对于需要与第三方协议堆栈之间具有互操作性的方案，可以使用 WS-AtomicTransaction (WS-AT) 协议。</span><span class="sxs-lookup"><span data-stu-id="44039-120">However, the WS-AtomicTransaction (WS-AT) protocol is useful for scenarios when interoperability with third-party protocol stacks is required.</span></span> <span data-ttu-id="44039-121">可以通过提供多个具有相应协议特定绑定的终结点，将 WCF 服务配置为接受这两个协议，如下面的示例配置所示。</span><span class="sxs-lookup"><span data-stu-id="44039-121">You can configure WCF services to accept both protocols by providing multiple endpoints with appropriate protocol-specific bindings, as shown in the following sample configuration.</span></span>  
  
    ```xml  
    <service name="CalculatorService">  
      <endpoint address="http://localhost:8000/CalcService"  
        binding="wsHttpBinding"  
        bindingConfiguration="transactionalWsatHttpBinding"  
        contract="ICalculator"  
        name="WSAtomicTransaction_endpoint" />  
      <endpoint address="net.tcp://localhost:8008/CalcService"  
        binding="netTcpBinding"  
        bindingConfiguration="transactionalOleTransactionsTcpBinding"  
        contract="ICalculator"  
        name="OleTransactions_endpoint" />  
    </service>  
    ```  
  
     <span data-ttu-id="44039-122">事务协议是使用 `transactionProtocol` 属性指定的。</span><span class="sxs-lookup"><span data-stu-id="44039-122">The transaction protocol is specified using the `transactionProtocol` attribute.</span></span> <span data-ttu-id="44039-123">但是，系统提供的 `wsHttpBinding` 中没有此属性，因为此绑定只能使用 WS-AT 协议。</span><span class="sxs-lookup"><span data-stu-id="44039-123">However, this attribute is absent from the system-provided `wsHttpBinding`, because this binding can only use the WS-AT protocol.</span></span>  
  
    ```xml  
    <bindings>  
      <wsHttpBinding>  
        <binding name="transactionalWsatHttpBinding"  
          transactionFlow="true" />  
      </wsHttpBinding>  
      <netTcpBinding>  
        <binding name="transactionalOleTransactionsTcpBinding"  
          transactionFlow="true"  
          transactionProtocol="OleTransactions"/>  
      </netTcpBinding>  
    </bindings>  
    ```  
  
### <a name="controlling-the-completion-of-a-transaction"></a><span data-ttu-id="44039-124">控制事务的完成</span><span class="sxs-lookup"><span data-stu-id="44039-124">Controlling the completion of a transaction</span></span>  
  
1. <span data-ttu-id="44039-125">默认情况下，如果未引发未经处理的异常，WCF 操作会自动完成事务。</span><span class="sxs-lookup"><span data-stu-id="44039-125">By default, WCF operations automatically complete transactions if no unhandled exceptions are thrown.</span></span> <span data-ttu-id="44039-126">使用 <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> 属性和 <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> 方法可以修改此行为。</span><span class="sxs-lookup"><span data-stu-id="44039-126">You can modify this behavior by using the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property and the <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> method.</span></span> <span data-ttu-id="44039-127">当需要某一操作与另一操作（例如借贷操作）在同一个事务中发生时，可以通过将 <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> 属性设置为 `false` 来禁用自动完成行为，如下面的 `Debit` 操作示例所示。</span><span class="sxs-lookup"><span data-stu-id="44039-127">When an operation is required to occur within the same transaction as another operation (for example, a debit and credit operation), you can disable the autocomplete behavior by setting the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property to `false` as shown in the following `Debit` operation example.</span></span> <span data-ttu-id="44039-128">在调用 `Debit` 属性设置为 <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> 的方法前（如操作 `true` 所示）或调用 `Credit1` 方法以将事务显式标记为完成前（如操作 <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> 所示），`Credit2` 操作使用的事务不会完成。</span><span class="sxs-lookup"><span data-stu-id="44039-128">The transaction the `Debit` operation uses is not completed until a method with the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property set to `true` is called, as shown in the operation `Credit1`, or when the <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> method is called to explicitly mark the transaction as complete, as shown in the operation `Credit2`.</span></span> <span data-ttu-id="44039-129">请注意，所示的两个贷记操作仅供演示，更常见的情况是只使用一个贷记操作。</span><span class="sxs-lookup"><span data-stu-id="44039-129">Note that the two credit operations are shown for illustration purposes, and that a single credit operation would be more typical.</span></span>  
  
    ```csharp
    [ServiceBehavior]  
    public class CalculatorService : IAccount  
    {  
        [OperationBehavior(  
            TransactionScopeRequired = true, TransactionAutoComplete = false)]  
        public void Debit(double n)  
        {  
            // Perform debit operation  
  
            return;  
        }  
  
        [OperationBehavior(  
            TransactionScopeRequired = true, TransactionAutoComplete = true)]  
        public void Credit1(double n)  
        {  
            // Perform credit operation  
  
            return;  
        }  
  
        [OperationBehavior(  
            TransactionScopeRequired = true, TransactionAutoComplete = false)]  
        public void Credit2(double n)  
        {  
            // Perform alternate credit operation  
  
            OperationContext.Current.SetTransactionComplete();  
            return;  
        }  
    }  
    ```  
  
2. <span data-ttu-id="44039-130">出于事务关联的目的而将 <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> 属性设置为 `false` 需要使用会话绑定。</span><span class="sxs-lookup"><span data-stu-id="44039-130">For the purposes of transaction correlation, setting the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property to `false` requires the use of a sessionful binding.</span></span> <span data-ttu-id="44039-131">这一需求使用 `SessionMode` 属性在 <xref:System.ServiceModel.ServiceContractAttribute> 上指定。</span><span class="sxs-lookup"><span data-stu-id="44039-131">This requirement is specified with the `SessionMode` property on the <xref:System.ServiceModel.ServiceContractAttribute>.</span></span>  
  
    ```csharp
    [ServiceContract(SessionMode = SessionMode.Required)]  
    public interface IAccount  
    {  
        [OperationContract]  
        [TransactionFlow(TransactionFlowOption.Allowed)]  
        void Debit(double n);  
        [OperationContract]  
        [TransactionFlow(TransactionFlowOption.Allowed)]  
        void Credit1(double n);  
        [OperationContract]  
        [TransactionFlow(TransactionFlowOption.Allowed)]  
        void Credit2(double n);  
    }  
    ```  
  
### <a name="controlling-the-lifetime-of-a-transactional-service-instance"></a><span data-ttu-id="44039-132">控制事务性服务实例的生存期</span><span class="sxs-lookup"><span data-stu-id="44039-132">Controlling the lifetime of a transactional service instance</span></span>  
  
1. <span data-ttu-id="44039-133">WCF 使用 <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> 属性来指定在事务完成时是否释放基础服务实例。</span><span class="sxs-lookup"><span data-stu-id="44039-133">WCF uses the <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> property to specify whether the underlying service instance is released when a transaction completes.</span></span> <span data-ttu-id="44039-134">由于默认情况下默认为，因此， `true` WCF 展示了有效且可预测的 "实时" 激活行为。</span><span class="sxs-lookup"><span data-stu-id="44039-134">Since this defaults to `true`, unless configured otherwise, WCF exhibits an efficient and predictable "just-in-time" activation behavior.</span></span> <span data-ttu-id="44039-135">在后续事务上调用服务可确保新服务实例不会保留前一个事务的状态。</span><span class="sxs-lookup"><span data-stu-id="44039-135">Calls to a service on a subsequent transaction are assured a new service instance with no remnants of the previous transaction's state.</span></span> <span data-ttu-id="44039-136">虽然此行为通常很有用，但有时你可能希望服务实例在事务完成后仍然保持状态。</span><span class="sxs-lookup"><span data-stu-id="44039-136">While this is often useful, sometimes you may want to maintain state within the service instance beyond the transaction completion.</span></span> <span data-ttu-id="44039-137">例如，所需的状态或资源句柄成本昂贵，难以检索或重建时就属于这种情况。</span><span class="sxs-lookup"><span data-stu-id="44039-137">Examples of this would be when required state or handles to resources are expensive to retrieve or reconstitute.</span></span> <span data-ttu-id="44039-138">通过将 <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> 属性设置为 `false`，可以实现此目的。</span><span class="sxs-lookup"><span data-stu-id="44039-138">You can do this by setting the <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> property to `false`.</span></span> <span data-ttu-id="44039-139">使用该设置时，实例和任何关联状态将可用于后续调用。</span><span class="sxs-lookup"><span data-stu-id="44039-139">With that setting, the instance and any associated state will be available on subsequent calls.</span></span> <span data-ttu-id="44039-140">使用此设置时，应仔细考虑状态和事务何时清除和完成以及如何清除和完成。</span><span class="sxs-lookup"><span data-stu-id="44039-140">When using this, give careful consideration to when and how state and transactions will be cleared and completed.</span></span> <span data-ttu-id="44039-141">下面的示例演示如何通过对 `runningTotal` 变量保持实例来实现这一目的。</span><span class="sxs-lookup"><span data-stu-id="44039-141">The following sample demonstrates how to do this by maintaining the instance with the `runningTotal` variable.</span></span>  
  
    ```csharp
    [ServiceBehavior(TransactionIsolationLevel = [ServiceBehavior(  
        ReleaseServiceInstanceOnTransactionComplete = false)]  
    public class CalculatorService : ICalculator  
    {  
        double runningTotal = 0;  
  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Add(double n)  
        {  
            // Perform transactional operation  
            RecordToLog($"Adding {n} to {runningTotal}");
            runningTotal = runningTotal + n;  
            return runningTotal;  
        }  
  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Subtract(double n)  
        {  
            // Perform transactional operation  
            RecordToLog($"Subtracting {n} from {runningTotal}");
            runningTotal = runningTotal - n;  
            return runningTotal;  
        }  
  
        private static void RecordToLog(string recordText)  
        {  
            // Database operations omitted for brevity  
        }  
    }  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="44039-142">由于实例的生存期是服务的内在行为，并通过 <xref:System.ServiceModel.ServiceBehaviorAttribute> 属性进行控制，因此不需要修改服务配置或服务协定来设置实例行为。</span><span class="sxs-lookup"><span data-stu-id="44039-142">Since the instance lifetime is a behavior that is internal to the service, and controlled through the <xref:System.ServiceModel.ServiceBehaviorAttribute> property, no modification to the service configuration or service contract is required to set the instance behavior.</span></span> <span data-ttu-id="44039-143">另外，网络上也不包含这种表示形式。</span><span class="sxs-lookup"><span data-stu-id="44039-143">In addition, the wire will contain no representation of this.</span></span>
