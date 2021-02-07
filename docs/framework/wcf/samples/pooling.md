---
description: 了解详细信息：池
title: Pooling
ms.date: 03/30/2017
ms.assetid: 688dfb30-b79a-4cad-a687-8302f8a9ad6a
ms.openlocfilehash: cb770b60a3011f95df5a2fdecea6cdc66b64710f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99703843"
---
# <a name="pooling"></a><span data-ttu-id="665ec-103">Pooling</span><span class="sxs-lookup"><span data-stu-id="665ec-103">Pooling</span></span>

<span data-ttu-id="665ec-104">此示例演示如何扩展 Windows Communication Foundation (WCF) 以支持对象池。</span><span class="sxs-lookup"><span data-stu-id="665ec-104">This sample demonstrates how to extend Windows Communication Foundation (WCF) to support object pooling.</span></span> <span data-ttu-id="665ec-105">本示例演示如何创建在语法和语义上与企业服务的 `ObjectPoolingAttribute` 属性功能相似的属性。</span><span class="sxs-lookup"><span data-stu-id="665ec-105">The sample demonstrates how to create an attribute that is syntactically and semantically similar to the `ObjectPoolingAttribute` attribute functionality of Enterprise Services.</span></span> <span data-ttu-id="665ec-106">对象池可以显著提高应用程序的性能。</span><span class="sxs-lookup"><span data-stu-id="665ec-106">Object pooling can provide a dramatic boost to an application's performance.</span></span> <span data-ttu-id="665ec-107">但是，如果使用不正确也可能产生负面影响。</span><span class="sxs-lookup"><span data-stu-id="665ec-107">However, it can have the opposite effect if it is not used properly.</span></span> <span data-ttu-id="665ec-108">对象池有助于减少重新创建经常使用且要求频繁进行初始化的对象的开销。</span><span class="sxs-lookup"><span data-stu-id="665ec-108">Object pooling helps reduce the overhead of recreating frequently used objects that require extensive initialization.</span></span> <span data-ttu-id="665ec-109">但是，如果调用缓冲池对象上的方法要花大量时间完成，则对象池在刚达到最大池大小时就会对其他请求排队。</span><span class="sxs-lookup"><span data-stu-id="665ec-109">However, if a call to a method on a pooled object takes a considerable amount of time to complete, object pooling queues additional requests as soon as the maximum pool size is reached.</span></span> <span data-ttu-id="665ec-110">因此可能不能为某些对象创建请求提供服务，这时将引发超时异常。</span><span class="sxs-lookup"><span data-stu-id="665ec-110">Thus it may fail to serve some object creation requests by throwing a timeout exception.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="665ec-111">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="665ec-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="665ec-112">创建 WCF 扩展的第一步是确定要使用的扩展点。</span><span class="sxs-lookup"><span data-stu-id="665ec-112">The first step in creating a WCF extension is to decide the extensibility point to use.</span></span>  
  
 <span data-ttu-id="665ec-113">在 WCF 中，术语 *发送器* 指的是一个运行时组件，该组件负责将传入消息转换为用户服务上的方法调用，并将返回值从该方法转换为传出消息。</span><span class="sxs-lookup"><span data-stu-id="665ec-113">In WCF the term *dispatcher* refers to a run-time component responsible for converting incoming messages into method invocations on the user’s service and for converting return values from that method to an outgoing message.</span></span> <span data-ttu-id="665ec-114">WCF 服务为每个终结点创建一个调度程序。</span><span class="sxs-lookup"><span data-stu-id="665ec-114">A WCF service creates a dispatcher for each endpoint.</span></span> <span data-ttu-id="665ec-115">如果与客户端关联的协定是双工协定，则 WCF 客户端必须使用调度程序。</span><span class="sxs-lookup"><span data-stu-id="665ec-115">A WCF client must use a dispatcher if the contract associated with that client is a duplex contract.</span></span>  
  
 <span data-ttu-id="665ec-116">通道和终结点调度程序通过公开用于控制调度程序行为的不同属性，来提供通道和协定范围的扩展性。</span><span class="sxs-lookup"><span data-stu-id="665ec-116">The channel and endpoint dispatchers offer channel-and contract-wide extensibility by exposing various properties that control the behavior of the dispatcher.</span></span> <span data-ttu-id="665ec-117">使用 <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> 属性还可以检查、修改或自定义调度过程。</span><span class="sxs-lookup"><span data-stu-id="665ec-117">The <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> property also enables you to inspect, modify, or customize the dispatching process.</span></span> <span data-ttu-id="665ec-118">本示例重点介绍 <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> 属性，该属性指向提供服务类实例的对象。</span><span class="sxs-lookup"><span data-stu-id="665ec-118">This sample focuses on the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property that points to the object that provides the instances of the service class.</span></span>  
  
## <a name="the-iinstanceprovider"></a><span data-ttu-id="665ec-119">IInstanceProvider</span><span class="sxs-lookup"><span data-stu-id="665ec-119">The IInstanceProvider</span></span>  

 <span data-ttu-id="665ec-120">在 WCF 中，调度程序使用实现接口的来创建服务类的实例 <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> <xref:System.ServiceModel.Dispatcher.IInstanceProvider> 。</span><span class="sxs-lookup"><span data-stu-id="665ec-120">In WCF, the dispatcher creates instances of the service class using a <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, which implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface.</span></span> <span data-ttu-id="665ec-121">此接口有三个方法：</span><span class="sxs-lookup"><span data-stu-id="665ec-121">This interface has three methods:</span></span>  
  
- <span data-ttu-id="665ec-122"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>：当消息到达调度程序时，调用 <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> 方法创建服务类的实例处理消息。</span><span class="sxs-lookup"><span data-stu-id="665ec-122"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: When a message arrives the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method to create an instance of the service class to process the message.</span></span> <span data-ttu-id="665ec-123">调用此方法的频率由 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> 属性决定。</span><span class="sxs-lookup"><span data-stu-id="665ec-123">The frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span> <span data-ttu-id="665ec-124">例如，如果 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> 属性设置为 <xref:System.ServiceModel.InstanceContextMode.PerCall>，则创建一个新的服务类实例来处理到达的每个消息，因此每当消息到达时，都将调用 <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>。</span><span class="sxs-lookup"><span data-stu-id="665ec-124">For example, if the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property is set to <xref:System.ServiceModel.InstanceContextMode.PerCall> a new instance of service class is created to process each message that arrives, so <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> is called whenever a message arrives.</span></span>  
  
- <span data-ttu-id="665ec-125"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>：与上一个方法基本相同，不同之处是此方法在没有 Message 自变量时调用。</span><span class="sxs-lookup"><span data-stu-id="665ec-125"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: This is identical to the previous method, except this is invoked when there is no Message argument.</span></span>  
  
- <span data-ttu-id="665ec-126"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>：当超过服务实例的生存期时，调度程序将调用 <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> 方法。</span><span class="sxs-lookup"><span data-stu-id="665ec-126"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: When a service instance's lifetime has elapsed, the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> method.</span></span> <span data-ttu-id="665ec-127">与 <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> 方法相同，调用此方法的频率是由 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> 属性确定的。</span><span class="sxs-lookup"><span data-stu-id="665ec-127">Just like for the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method, the frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span>  
  
## <a name="the-object-pool"></a><span data-ttu-id="665ec-128">对象池</span><span class="sxs-lookup"><span data-stu-id="665ec-128">The Object Pool</span></span>  

 <span data-ttu-id="665ec-129">自定义 <xref:System.ServiceModel.Dispatcher.IInstanceProvider> 实现为服务提供所需的对象池语义。</span><span class="sxs-lookup"><span data-stu-id="665ec-129">A custom <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementation provides the required object pooling semantics for a service.</span></span> <span data-ttu-id="665ec-130">因此，此示例有一个为池提供 `ObjectPoolingInstanceProvider` 自定义实现的 <xref:System.ServiceModel.Dispatcher.IInstanceProvider> 类型。</span><span class="sxs-lookup"><span data-stu-id="665ec-130">Therefore, this sample has an `ObjectPoolingInstanceProvider` type that provides custom implementation of <xref:System.ServiceModel.Dispatcher.IInstanceProvider> for pooling.</span></span> <span data-ttu-id="665ec-131">当 `Dispatcher` 调用 <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> 方法时，自定义实现将在内存池中寻找现有对象，而不是创建新的实例。</span><span class="sxs-lookup"><span data-stu-id="665ec-131">When the `Dispatcher` calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method, instead of creating a new instance, the custom implementation looks for an existing object in an in-memory pool.</span></span> <span data-ttu-id="665ec-132">如果找到一个对象，则返回该对象。</span><span class="sxs-lookup"><span data-stu-id="665ec-132">If one is available, it is returned.</span></span> <span data-ttu-id="665ec-133">否则，将创建新对象。</span><span class="sxs-lookup"><span data-stu-id="665ec-133">Otherwise, a new object is created.</span></span> <span data-ttu-id="665ec-134">下面的示例代码演示了 `GetInstance` 的实现。</span><span class="sxs-lookup"><span data-stu-id="665ec-134">The implementation for `GetInstance` is shown in the following sample code.</span></span>  
  
```csharp  
object IInstanceProvider.GetInstance(InstanceContext instanceContext, Message message)  
{  
    object obj = null;  
  
    lock (poolLock)  
    {  
        if (pool.Count > 0)  
        {  
            obj = pool.Pop();  
        }  
        else  
        {  
            obj = CreateNewPoolObject();  
        }  
        activeObjectsCount++;  
    }  
  
    WritePoolMessage(ResourceHelper.GetString("MsgNewObject"));  
  
    idleTimer.Stop();  
  
    return obj;
}  
```  
  
 <span data-ttu-id="665ec-135">自定义 `ReleaseInstance` 实现将已释放的实例重新添加回池中并减少 `ActiveObjectsCount` 值。</span><span class="sxs-lookup"><span data-stu-id="665ec-135">The custom `ReleaseInstance` implementation adds the released instance back to the pool and decrements the `ActiveObjectsCount` value.</span></span> <span data-ttu-id="665ec-136">`Dispatcher` 可从不同的线程调用这些方法，因此需要同步访问 `ObjectPoolingInstanceProvider` 类中的类级别成员。</span><span class="sxs-lookup"><span data-stu-id="665ec-136">The `Dispatcher` can call these methods from different threads, and therefore synchronized access to the class level members in the `ObjectPoolingInstanceProvider` class is required.</span></span>  
  
```csharp  
void IInstanceProvider.ReleaseInstance(InstanceContext instanceContext, object instance)  
{  
    lock (poolLock)  
    {  
        pool.Push(instance);  
        activeObjectsCount--;  
  
        WritePoolMessage(  
        ResourceHelper.GetString("MsgObjectPooled"));  
  
        // When the service goes completely idle (no requests
        // are being processed), the idle timer is started  
        if (activeObjectsCount == 0)  
            idleTimer.Start();
    }  
}  
```  
  
 <span data-ttu-id="665ec-137">`ReleaseInstance`方法提供 "清理初始化" 功能。</span><span class="sxs-lookup"><span data-stu-id="665ec-137">The `ReleaseInstance` method provides a "clean up initialization" feature.</span></span> <span data-ttu-id="665ec-138">通常，该池为其生存期保持最少数量的对象。</span><span class="sxs-lookup"><span data-stu-id="665ec-138">Normally the pool maintains a minimum number of objects for the lifetime of the pool.</span></span> <span data-ttu-id="665ec-139">但是，可能有过度使用的时期，此时需要在池中创建更多对象以达到配置中指定的最大限制。</span><span class="sxs-lookup"><span data-stu-id="665ec-139">However, there can be periods of excessive usage that require creating additional objects in the pool to reach the maximum limit specified in the configuration.</span></span> <span data-ttu-id="665ec-140">最终，当池变得不是很活跃时，那些多余的对象可能成为额外的开销。</span><span class="sxs-lookup"><span data-stu-id="665ec-140">Eventually, when the pool becomes less active, those surplus objects can become an extra overhead.</span></span> <span data-ttu-id="665ec-141">因此，当 `activeObjectsCount` 到达 0 时，会启用一个空闲计时器，该计时器将触发并执行清除循环。</span><span class="sxs-lookup"><span data-stu-id="665ec-141">Therefore, when the `activeObjectsCount` reaches zero, an idle timer is started that triggers and performs a clean-up cycle.</span></span>  
  
## <a name="adding-the-behavior"></a><span data-ttu-id="665ec-142">添加行为</span><span class="sxs-lookup"><span data-stu-id="665ec-142">Adding the Behavior</span></span>  

 <span data-ttu-id="665ec-143">使用下面的行为将调度程序层扩展挂钩：</span><span class="sxs-lookup"><span data-stu-id="665ec-143">Dispatcher-layer extensions are hooked up using the following behaviors:</span></span>  
  
- <span data-ttu-id="665ec-144">服务行为。</span><span class="sxs-lookup"><span data-stu-id="665ec-144">Service Behaviors.</span></span> <span data-ttu-id="665ec-145">这些行为允许自定义整个服务运行时。</span><span class="sxs-lookup"><span data-stu-id="665ec-145">These allow for the customization of the entire service runtime.</span></span>  
  
- <span data-ttu-id="665ec-146">终结点行为。</span><span class="sxs-lookup"><span data-stu-id="665ec-146">Endpoint Behaviors.</span></span> <span data-ttu-id="665ec-147">这些行为允许自定义服务终结点，特别是通道和终结点调度程序。</span><span class="sxs-lookup"><span data-stu-id="665ec-147">These allow for the customization of service endpoints, specifically a Channel and Endpoint Dispatcher.</span></span>  
  
- <span data-ttu-id="665ec-148">协定行为。</span><span class="sxs-lookup"><span data-stu-id="665ec-148">Contract Behaviors.</span></span> <span data-ttu-id="665ec-149">这些行为允许分别自定义客户端和服务上的 <xref:System.ServiceModel.Dispatcher.ClientRuntime> 和 <xref:System.ServiceModel.Dispatcher.DispatchRuntime> 类。</span><span class="sxs-lookup"><span data-stu-id="665ec-149">These allow for the customization of both <xref:System.ServiceModel.Dispatcher.ClientRuntime> and <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes on the client and the service respectively.</span></span>  
  
 <span data-ttu-id="665ec-150">为了实现对象池扩展，必须创建服务行为。</span><span class="sxs-lookup"><span data-stu-id="665ec-150">For the purpose of an object pooling extension a service behavior must be created.</span></span> <span data-ttu-id="665ec-151">服务行为是通过实现 <xref:System.ServiceModel.Description.IServiceBehavior> 接口创建的。</span><span class="sxs-lookup"><span data-stu-id="665ec-151">Service behaviors are created by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface.</span></span> <span data-ttu-id="665ec-152">可以通过多种方式使服务模型注意到自定义行为：</span><span class="sxs-lookup"><span data-stu-id="665ec-152">There are several ways to make the service model aware of the custom behaviors:</span></span>  
  
- <span data-ttu-id="665ec-153">使用自定义属性。</span><span class="sxs-lookup"><span data-stu-id="665ec-153">Using a custom attribute.</span></span>  
  
- <span data-ttu-id="665ec-154">强制将它添加到服务说明的行为集合中。</span><span class="sxs-lookup"><span data-stu-id="665ec-154">Imperatively adding it to the service description’s behaviors collection.</span></span>  
  
- <span data-ttu-id="665ec-155">扩展配置文件。</span><span class="sxs-lookup"><span data-stu-id="665ec-155">Extending the configuration file.</span></span>  
  
 <span data-ttu-id="665ec-156">本示例使用自定义属性。</span><span class="sxs-lookup"><span data-stu-id="665ec-156">This sample uses a custom attribute.</span></span> <span data-ttu-id="665ec-157">当构造 <xref:System.ServiceModel.ServiceHost> 时，本示例检查用于服务的类型定义的属性并将可用行为添加到服务说明的行为集合中。</span><span class="sxs-lookup"><span data-stu-id="665ec-157">When the <xref:System.ServiceModel.ServiceHost> is constructed it examines the attributes used in the service’s type definition and adds the available behaviors to the service description’s behaviors collection.</span></span>  
  
 <span data-ttu-id="665ec-158">接口 <xref:System.ServiceModel.Description.IServiceBehavior> 包含三个方法 -- <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>、<xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> 和 <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>。</span><span class="sxs-lookup"><span data-stu-id="665ec-158">The interface <xref:System.ServiceModel.Description.IServiceBehavior> has three methods in it -- <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>, <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>, and <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span></span> <span data-ttu-id="665ec-159"><xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> 方法用于确保该行为可以应用于服务。</span><span class="sxs-lookup"><span data-stu-id="665ec-159">The <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> method is used to ensure that the behavior can be applied to the service.</span></span> <span data-ttu-id="665ec-160">在本示例中，此实现确保不使用 <xref:System.ServiceModel.InstanceContextMode.Single> 配置服务。</span><span class="sxs-lookup"><span data-stu-id="665ec-160">In this sample, the implementation ensures that the service is not configured with <xref:System.ServiceModel.InstanceContextMode.Single>.</span></span> <span data-ttu-id="665ec-161"><xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> 方法用于配置服务的绑定。</span><span class="sxs-lookup"><span data-stu-id="665ec-161">The <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> method is used to configure the service's bindings.</span></span> <span data-ttu-id="665ec-162">它不是本方案所必需的。</span><span class="sxs-lookup"><span data-stu-id="665ec-162">It is not required in this scenario.</span></span> <span data-ttu-id="665ec-163"><xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> 用于配置服务的调度程序。</span><span class="sxs-lookup"><span data-stu-id="665ec-163">The <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> is used to configure the service's dispatchers.</span></span> <span data-ttu-id="665ec-164">初始化时，WCF 将调用此方法 <xref:System.ServiceModel.ServiceHost> 。</span><span class="sxs-lookup"><span data-stu-id="665ec-164">This method is called by WCF when the <xref:System.ServiceModel.ServiceHost> is being initialized.</span></span> <span data-ttu-id="665ec-165">下列参数将传递到此方法：</span><span class="sxs-lookup"><span data-stu-id="665ec-165">The following parameters are passed into this method:</span></span>  
  
- <span data-ttu-id="665ec-166">`Description`：此自变量提供整个服务的服务说明。</span><span class="sxs-lookup"><span data-stu-id="665ec-166">`Description`: This argument provides the service description for the entire service.</span></span> <span data-ttu-id="665ec-167">它可用于检查有关服务的终结点、协定、绑定和其他数据的说明数据。</span><span class="sxs-lookup"><span data-stu-id="665ec-167">This can be used to inspect description data about the service’s endpoints, contracts, bindings, and other data.</span></span>  
  
- <span data-ttu-id="665ec-168">`ServiceHostBase`：此自变量提供当前正在初始化的 <xref:System.ServiceModel.ServiceHostBase>。</span><span class="sxs-lookup"><span data-stu-id="665ec-168">`ServiceHostBase`: This argument provides the <xref:System.ServiceModel.ServiceHostBase> that is currently being initialized.</span></span>  
  
 <span data-ttu-id="665ec-169">在自定义 <xref:System.ServiceModel.Description.IServiceBehavior> 实现中，会实例化一个新的 `ObjectPoolingInstanceProvider` 实例，并将该实例分配到 ServiceHostBase 的每个 <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> 的 <xref:System.ServiceModel.Dispatcher.DispatchRuntime> 属性。</span><span class="sxs-lookup"><span data-stu-id="665ec-169">In the custom <xref:System.ServiceModel.Description.IServiceBehavior> implementation a new instance of `ObjectPoolingInstanceProvider` is instantiated and assigned to the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property in each <xref:System.ServiceModel.Dispatcher.DispatchRuntime> in the ServiceHostBase.</span></span>  
  
```csharp  
void IServiceBehavior.ApplyDispatchBehavior(ServiceDescription description, ServiceHostBase serviceHostBase)  
{  
    // Create an instance of the ObjectPoolInstanceProvider.  
    ObjectPoolingInstanceProvider instanceProvider = new  
           ObjectPoolingInstanceProvider(description.ServiceType,
                                                    minPoolSize);  
  
    // Forward the call if we created a ServiceThrottlingBehavior.  
    if (this.throttlingBehavior != null)  
    {  
        ((IServiceBehavior)this.throttlingBehavior).ApplyDispatchBehavior(description, serviceHostBase);  
    }  
  
    // In case there was already a ServiceThrottlingBehavior
    // (this.throttlingBehavior==null), it should have initialized
    // a single ServiceThrottle on all ChannelDispatchers.
    // As we loop through the ChannelDispatchers, we verify that
    // and modify the ServiceThrottle to guard MaxPoolSize.  
    ServiceThrottle throttle = null;  
  
    foreach (ChannelDispatcherBase cdb in
            serviceHostBase.ChannelDispatchers)  
    {  
        ChannelDispatcher cd = cdb as ChannelDispatcher;  
        if (cd != null)  
        {  
            // Make sure there is exactly one throttle used by all
            // endpoints. If there were others, we could not enforce
            // MaxPoolSize.  
            if ((this.throttlingBehavior == null) &&
                        (this.maxPoolSize != Int32.MaxValue))  
            {  
                throttle ??= cd.ServiceThrottle;
                if (cd.ServiceThrottle == null)  
                {  
                    throw new
InvalidOperationException(ResourceHelper.GetString("ExNullThrottle"));  
                }  
                if (throttle != cd.ServiceThrottle)  
                {  
                    throw new InvalidOperationException(ResourceHelper.GetString("ExDifferentThrottle"));  
                }  
             }  
  
             foreach (EndpointDispatcher ed in cd.Endpoints)  
             {  
                 // Assign it to DispatchBehavior in each endpoint.  
                 ed.DispatchRuntime.InstanceProvider =
                                      instanceProvider;  
             }  
         }  
     }  
  
     // Set the MaxConcurrentInstances to limit the number of items
     // that will ever be requested from the pool.  
     if ((throttle != null) && (throttle.MaxConcurrentInstances >
                                      this.maxPoolSize))  
     {  
         throttle.MaxConcurrentInstances = this.maxPoolSize;  
     }  
}  
```  
  
 <span data-ttu-id="665ec-170">除了 <xref:System.ServiceModel.Description.IServiceBehavior> 实现外，<xref:System.EnterpriseServices.ObjectPoolingAttribute> 类有多个可以使用属性自变量自定义对象池的成员。</span><span class="sxs-lookup"><span data-stu-id="665ec-170">In addition to an <xref:System.ServiceModel.Description.IServiceBehavior> implementation the <xref:System.EnterpriseServices.ObjectPoolingAttribute> class has several members to customize the object pool using the attribute arguments.</span></span> <span data-ttu-id="665ec-171">这些成员包括 <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>、<xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A> 和 <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>，用于匹配由 .NET 企业服务提供的对象池功能集。</span><span class="sxs-lookup"><span data-stu-id="665ec-171">These members include <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>, <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>, and <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>, to match the object pooling feature set provided by .NET Enterprise Services.</span></span>  
  
 <span data-ttu-id="665ec-172">现在可以通过使用新创建的自定义特性对服务实现进行批注，将对象池行为添加到 WCF 服务 `ObjectPooling` 。</span><span class="sxs-lookup"><span data-stu-id="665ec-172">The object pooling behavior can now be added to a WCF service by annotating the service implementation with the newly created custom `ObjectPooling` attribute.</span></span>  
  
```csharp  
[ObjectPooling(MaxPoolSize=1024, MinPoolSize=10, CreationTimeout=30000)]
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="running-the-sample"></a><span data-ttu-id="665ec-173">运行示例</span><span class="sxs-lookup"><span data-stu-id="665ec-173">Running the Sample</span></span>  

 <span data-ttu-id="665ec-174">本实例演示在某些方案中使用对象池可以获得的性能优点。</span><span class="sxs-lookup"><span data-stu-id="665ec-174">The sample demonstrates the performance benefits that can be gained by using object pooling in certain scenarios.</span></span>  
  
 <span data-ttu-id="665ec-175">服务应用程序实现两个服务 -- `WorkService` 和 `ObjectPooledWorkService`。</span><span class="sxs-lookup"><span data-stu-id="665ec-175">The service application implements two services -- `WorkService` and `ObjectPooledWorkService`.</span></span> <span data-ttu-id="665ec-176">这两个服务共享相同的实现 -- 它们都需要成本较高的初始化，再公开成本相对低廉的 `DoWork()` 方法。</span><span class="sxs-lookup"><span data-stu-id="665ec-176">Both services share the same implementation -- they both require expensive initialization and then expose a `DoWork()` method that is relatively cheap.</span></span> <span data-ttu-id="665ec-177">唯一的区别是 `ObjectPooledWorkService` 配置了对象池：</span><span class="sxs-lookup"><span data-stu-id="665ec-177">The only difference is that the `ObjectPooledWorkService` has object pooling configured:</span></span>  
  
```csharp  
[ObjectPooling(MinPoolSize = 0, MaxPoolSize = 5)]  
public class ObjectPooledWorkService : IDoWork  
{  
    public ObjectPooledWorkService()  
    {  
        Thread.Sleep(5000);  
        ColorConsole.WriteLine(ConsoleColor.Blue, "ObjectPooledWorkService instance created.");  
    }  
  
    public void DoWork()  
    {  
        ColorConsole.WriteLine(ConsoleColor.Blue, "ObjectPooledWorkService.GetData() completed.");  
    }
}  
```  
  
 <span data-ttu-id="665ec-178">当运行客户端时，它定时调用 `WorkService` 5 次。</span><span class="sxs-lookup"><span data-stu-id="665ec-178">When you run the client, it times calling the `WorkService` 5 times.</span></span> <span data-ttu-id="665ec-179">接着定时调用 `ObjectPooledWorkService` 5 次。</span><span class="sxs-lookup"><span data-stu-id="665ec-179">It then times calling the `ObjectPooledWorkService` 5 times.</span></span> <span data-ttu-id="665ec-180">然后显示时间上的区别：</span><span class="sxs-lookup"><span data-stu-id="665ec-180">The difference in time is then displayed:</span></span>  
  
```console
Press <ENTER> to start the client.  
  
Calling WorkService:  
1 - DoWork() Done  
2 - DoWork() Done  
3 - DoWork() Done  
4 - DoWork() Done  
5 - DoWork() Done  
Calling WorkService took: 26722 ms.  
Calling ObjectPooledWorkService:  
1 - DoWork() Done  
2 - DoWork() Done  
3 - DoWork() Done  
4 - DoWork() Done  
5 - DoWork() Done  
Calling ObjectPooledWorkService took: 5323 ms.  
Press <ENTER> to exit.  
```  
  
> [!NOTE]
> <span data-ttu-id="665ec-181">第一次运行客户端时，这两个服务看起来占用相等的时间。</span><span class="sxs-lookup"><span data-stu-id="665ec-181">The first time the client is run both services appear to take about the same amount of time.</span></span> <span data-ttu-id="665ec-182">如果重新运行此示例，则将看到 `ObjectPooledWorkService` 的返回速度更快，原因是池中已经存在该对象的实例了。</span><span class="sxs-lookup"><span data-stu-id="665ec-182">If you re-run the sample, you can see that the `ObjectPooledWorkService` returns much quicker because an instance of that object already exists in the pool.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="665ec-183">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="665ec-183">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="665ec-184">确保已对 [Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="665ec-184">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="665ec-185">若要生成解决方案，请按照 [生成 Windows Communication Foundation 示例](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="665ec-185">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="665ec-186">若要以单机配置或跨计算机配置来运行示例，请按照 [运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="665ec-186">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="665ec-187">如果使用 Svcutil.exe 为此示例重新生成配置，请确保在客户端配置中修改终结点名称以与客户端代码匹配。</span><span class="sxs-lookup"><span data-stu-id="665ec-187">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="665ec-188">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="665ec-188">The samples may already be installed on your machine.</span></span> <span data-ttu-id="665ec-189">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="665ec-189">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="665ec-190">如果此目录不存在，请参阅[Windows Communication Foundation (wcf) ，并 Windows Workflow Foundation (的 WF](https://www.microsoft.com/download/details.aspx?id=21459)) .NET Framework Windows Communication Foundation ([!INCLUDE[wf1](../../../../includes/wf1-md.md)]</span><span class="sxs-lookup"><span data-stu-id="665ec-190">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="665ec-191">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="665ec-191">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Pooling`  
