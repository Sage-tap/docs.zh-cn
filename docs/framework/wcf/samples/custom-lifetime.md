---
description: 了解详细信息：自定义生存期
title: 自定义生存期
ms.date: 08/20/2018
ms.assetid: 52806c07-b91c-48fe-b992-88a41924f51f
ms.openlocfilehash: 24845aaa20e60f92e2add568c81ab3d6502ebedf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99732470"
---
# <a name="custom-lifetime"></a><span data-ttu-id="e3f2b-103">自定义生存期</span><span class="sxs-lookup"><span data-stu-id="e3f2b-103">Custom lifetime</span></span>

<span data-ttu-id="e3f2b-104">此示例演示如何编写一个 Windows Communication Foundation (WCF) 扩展以为共享 WCF 服务实例提供自定义生存期服务。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-104">This sample demonstrates how to write a Windows Communication Foundation (WCF) extension to provide custom lifetime services for shared WCF service instances.</span></span>

> [!NOTE]
> <span data-ttu-id="e3f2b-105">本文的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-105">The setup procedure and build instructions for this sample are located at the end of this article.</span></span>

## <a name="shared-instancing"></a><span data-ttu-id="e3f2b-106">共享实例</span><span class="sxs-lookup"><span data-stu-id="e3f2b-106">Shared instancing</span></span>

<span data-ttu-id="e3f2b-107">WCF 为服务实例提供了多种实例化模式。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-107">WCF offers several instancing modes for your service instances.</span></span> <span data-ttu-id="e3f2b-108">本文中介绍的共享实例化模式提供了在多个通道之间共享服务实例的方法。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-108">The shared instancing mode covered in this article provides a way to share a service instance between multiple channels.</span></span> <span data-ttu-id="e3f2b-109">客户端可以联系服务中的工厂方法，并创建新的通道来开始通信。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-109">Clients can contact a factory method in the service and create a new channel to start communication.</span></span> <span data-ttu-id="e3f2b-110">以下代码段演示了客户端应用程序如何创建到现有服务实例的新通道：</span><span class="sxs-lookup"><span data-stu-id="e3f2b-110">The following code snippet shows how a client application creates a new channel to an existing service instance:</span></span>

```csharp
// Create a header for the shared instance id
MessageHeader shareableInstanceContextHeader = MessageHeader.CreateHeader(
        CustomHeader.HeaderName,
        CustomHeader.HeaderNamespace,
        Guid.NewGuid().ToString());

// Create the channel factory
ChannelFactory<IEchoService> channelFactory =
    new ChannelFactory<IEchoService>("echoservice");

// Create the first channel
IEchoService proxy = channelFactory.CreateChannel();

// Call an operation to create shared service instance
using (new OperationContextScope((IClientChannel)proxy))
{
    OperationContext.Current.OutgoingMessageHeaders.Add(shareableInstanceContextHeader);
    Console.WriteLine("Service returned: " + proxy.Echo("Apple"));
}

((IChannel)proxy).Close();

// Create the second channel
IEchoService proxy2 = channelFactory.CreateChannel();

// Call an operation using the same header that will reuse the shared service instance
using (new OperationContextScope((IClientChannel)proxy2))
{
    OperationContext.Current.OutgoingMessageHeaders.Add(shareableInstanceContextHeader);
    Console.WriteLine("Service returned: " + proxy2.Echo("Apple"));
}
```

<span data-ttu-id="e3f2b-111">与其他实例化模式不同，共享实例化模式拥有一种释放服务实例的独特方式。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-111">Unlike other instancing modes, the shared instancing mode has a unique way of releasing the service instances.</span></span> <span data-ttu-id="e3f2b-112">默认情况下，当关闭的所有通道时 <xref:System.ServiceModel.InstanceContext> ，WCF 服务运行时会检查是否将服务 <xref:System.ServiceModel.InstanceContextMode> 配置为 <xref:System.ServiceModel.InstanceContextMode.PerCall> 或，如果是， <xref:System.ServiceModel.InstanceContextMode.PerSession> 则释放实例并声明资源。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-112">By default, when all the channels are closed for an <xref:System.ServiceModel.InstanceContext>, the WCF service runtime checks to see if the service <xref:System.ServiceModel.InstanceContextMode> is configured to <xref:System.ServiceModel.InstanceContextMode.PerCall> or <xref:System.ServiceModel.InstanceContextMode.PerSession>, and if so releases the instance and claims the resources.</span></span> <span data-ttu-id="e3f2b-113">如果使用的 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 是自定义，则 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> 在释放实例之前，WCF 将调用提供程序实现的方法。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-113">If a custom <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> is being used, WCF invokes the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method of the provider implementation before releasing the instance.</span></span> <span data-ttu-id="e3f2b-114">如果 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> 返回 `true` 实例，则为; 否则 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 实现将负责 `Dispatcher` 使用回调方法通知空闲状态。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-114">If <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> returns `true` the instance is released, otherwise the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is responsible for notifying the `Dispatcher` of the idle state by using a callback method.</span></span> <span data-ttu-id="e3f2b-115">这是通过调用提供程序的方法来完成的 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> 。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-115">This is done by calling the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> method of the provider.</span></span>

<span data-ttu-id="e3f2b-116">此示例演示如何延迟释放的 <xref:System.ServiceModel.InstanceContext> 空闲超时值为20秒。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-116">This sample demonstrates how you can delay releasing the <xref:System.ServiceModel.InstanceContext> with an idle timeout of 20 seconds.</span></span>

## <a name="extending-the-instancecontext"></a><span data-ttu-id="e3f2b-117">扩展 InstanceContext</span><span class="sxs-lookup"><span data-stu-id="e3f2b-117">Extending the InstanceContext</span></span>

<span data-ttu-id="e3f2b-118">在 WCF 中， <xref:System.ServiceModel.InstanceContext> 是服务实例和之间的链接 `Dispatcher` 。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-118">In WCF, <xref:System.ServiceModel.InstanceContext> is the link between the service instance and the `Dispatcher`.</span></span> <span data-ttu-id="e3f2b-119">WCF 允许通过使用其可扩展对象模式添加新状态或行为来扩展此运行时组件。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-119">WCF allows you to extend this runtime component by adding new state or behavior by using its extensible object pattern.</span></span> <span data-ttu-id="e3f2b-120">在 WCF 中使用可扩展对象模式，以使用新功能扩展现有的运行时类，或者向对象中添加新的状态功能。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-120">The extensible object pattern is used in WCF to either extend existing runtime classes with new functionality or to add new state features to an object.</span></span> <span data-ttu-id="e3f2b-121">可扩展对象模式中有三个接口：<xref:System.ServiceModel.IExtensibleObject%601>、<xref:System.ServiceModel.IExtension%601> 和 <xref:System.ServiceModel.IExtensionCollection%601>。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-121">There are three interfaces in the extensible object pattern: <xref:System.ServiceModel.IExtensibleObject%601>, <xref:System.ServiceModel.IExtension%601>, and <xref:System.ServiceModel.IExtensionCollection%601>.</span></span>

<span data-ttu-id="e3f2b-122"><xref:System.ServiceModel.IExtensibleObject%601>接口由对象实现，以允许自定义其功能的扩展。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-122">The <xref:System.ServiceModel.IExtensibleObject%601> interface is implemented by objects to allow extensions that customize their functionality.</span></span>

<span data-ttu-id="e3f2b-123"><xref:System.ServiceModel.IExtension%601> 接口由可作为类型为 `T` 的类扩展的对象来实现。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-123">The <xref:System.ServiceModel.IExtension%601> interface is implemented by objects that can be extensions of classes of type `T`.</span></span>

<span data-ttu-id="e3f2b-124">最后， <xref:System.ServiceModel.IExtensionCollection%601> 接口是实现的集合 <xref:System.ServiceModel.IExtension%601> ，可用于按类型检索的实现 <xref:System.ServiceModel.IExtension%601> 。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-124">And finally, the <xref:System.ServiceModel.IExtensionCollection%601> interface is a collection of <xref:System.ServiceModel.IExtension%601> implementations that allows for retrieving an implementation of <xref:System.ServiceModel.IExtension%601> by their type.</span></span>

<span data-ttu-id="e3f2b-125">因此，若要扩展 <xref:System.ServiceModel.InstanceContext> ，必须实现 <xref:System.ServiceModel.IExtension%601> 接口。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-125">Therefore, in order to extend the <xref:System.ServiceModel.InstanceContext>, you must implement the <xref:System.ServiceModel.IExtension%601> interface.</span></span> <span data-ttu-id="e3f2b-126">在此示例项目中， `CustomLeaseExtension` 类包含此实现。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-126">In this sample project, the `CustomLeaseExtension` class contains this implementation.</span></span>

```csharp
class CustomLeaseExtension : IExtension<InstanceContext>
{
}
```

<span data-ttu-id="e3f2b-127"><xref:System.ServiceModel.IExtension%601> 接口具有 <xref:System.ServiceModel.IExtension%601.Attach%2A> 和 <xref:System.ServiceModel.IExtension%601.Detach%2A> 两个方法。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-127">The <xref:System.ServiceModel.IExtension%601> interface has two methods <xref:System.ServiceModel.IExtension%601.Attach%2A> and <xref:System.ServiceModel.IExtension%601.Detach%2A>.</span></span> <span data-ttu-id="e3f2b-128">顾名思义，当运行时将扩展附加到 <xref:System.ServiceModel.InstanceContext> 类的实例以及将扩展从该类的实例分离时，将会调用这两个方法。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-128">As their names imply, these two methods are called when the runtime attaches and detaches the extension to an instance of the <xref:System.ServiceModel.InstanceContext> class.</span></span> <span data-ttu-id="e3f2b-129">在此示例中，`Attach` 方法用于跟踪属于当前扩展实例的 <xref:System.ServiceModel.InstanceContext> 对象。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-129">In this sample, the `Attach` method is used to keep track of the <xref:System.ServiceModel.InstanceContext> object that belongs to the current instance of the extension.</span></span>

```csharp
InstanceContext owner;

public void Attach(InstanceContext owner)
{
    this.owner = owner;
}
```

<span data-ttu-id="e3f2b-130">此外，还必须将必要的实现添加到该扩展以提供扩展的生存期支持。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-130">In addition, you must add the necessary implementation to the extension to provide the extended lifetime support.</span></span> <span data-ttu-id="e3f2b-131">因此， `ICustomLease` 接口用所需的方法进行声明，并在类中实现 `CustomLeaseExtension` 。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-131">Therefore, the `ICustomLease` interface is declared with the desired methods and is implemented in the `CustomLeaseExtension` class.</span></span>

```csharp
interface ICustomLease
{
    bool IsIdle { get; }
    InstanceContextIdleCallback Callback { get; set; }
}

class CustomLeaseExtension : IExtension<InstanceContext>, ICustomLease
{
}
```

<span data-ttu-id="e3f2b-132">当 WCF 在 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> 实现中调用方法时 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> ，此调用将路由到的 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> 方法 `CustomLeaseExtension` 。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-132">When WCF invokes the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method in the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation, this call is routed to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method of the `CustomLeaseExtension`.</span></span> <span data-ttu-id="e3f2b-133">然后，将 `CustomLeaseExtension` 检查其私有状态以查看是否 <xref:System.ServiceModel.InstanceContext> 处于空闲状态。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-133">Then, the `CustomLeaseExtension` checks its private state to see whether the <xref:System.ServiceModel.InstanceContext> is idle.</span></span> <span data-ttu-id="e3f2b-134">如果它处于空闲状态，它将返回 `true` 。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-134">If it is idle, it returns `true`.</span></span> <span data-ttu-id="e3f2b-135">否则，它将针对指定的扩展生存期启动一个计时器。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-135">Otherwise, it starts a timer for a specified amount of extended lifetime.</span></span>

```csharp
public bool IsIdle
{
  get
  {
    lock (thisLock)
    {
      if (isIdle)
      {
        return true;
      }
      else
      {
        StartTimer();
        return false;
      }
    }
  }
}
```

<span data-ttu-id="e3f2b-136">在计时器的 `Elapsed` 事件中，将调用调度程序中的回调函数，以便启动另一个清理周期。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-136">In the timer’s `Elapsed` event, the callback function in the Dispatcher is called in order to start another clean-up cycle.</span></span>

```csharp
void idleTimer_Elapsed(object sender, ElapsedEventArgs args)
{
    lock (thisLock)
    {
        StopTimer();
        isIdle = true;
        Utility.WriteMessageToConsole(
            ResourceHelper.GetString("MsgLeaseExpired"));
        callback(owner);
    }
}
```

<span data-ttu-id="e3f2b-137">如果要将实例移动到空闲状态，则无法续订正在运行的计时器。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-137">There's no way to renew the running timer when a new message arrives for the instance being moved to the idle state.</span></span>

<span data-ttu-id="e3f2b-138">此示例实现 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 以截获对 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> 方法的调用，并将这些调用路由到 `CustomLeaseExtension`。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-138">The sample implements <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> to intercept the calls to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method and route them to the `CustomLeaseExtension`.</span></span> <span data-ttu-id="e3f2b-139"><xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 实现包含在 `CustomLifetimeLease` 类中。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-139">The <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is contained in `CustomLifetimeLease` class.</span></span> <span data-ttu-id="e3f2b-140"><xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>当 WCF 即将发布服务实例时，将调用方法。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-140">The <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method is invoked when WCF is about to release the service instance.</span></span> <span data-ttu-id="e3f2b-141">但是，在 ServiceBehavior 的 `ISharedSessionInstance` 集合中，只有特定 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 实现的一个实例。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-141">However, there is only one instance of a particular `ISharedSessionInstance` implementation in the ServiceBehavior’s <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> collection.</span></span> <span data-ttu-id="e3f2b-142">这意味着，在 WCF 检查方法时，无法知道 <xref:System.ServiceModel.InstanceContext> 是否关闭了 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> 。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-142">This means there's no way of knowing if the <xref:System.ServiceModel.InstanceContext> is closed at the time WCF checks the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span> <span data-ttu-id="e3f2b-143">因此，此示例使用线程锁定将请求序列化到 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-143">Therefore, this sample uses thread locking to serialize requests to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e3f2b-144">由于序列化可能会严重影响应用程序的性能，因此不推荐使用线程锁定方法。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-144">Using thread locking is not a recommended approach because serialization can severely affect the performance of your application.</span></span>

<span data-ttu-id="e3f2b-145">私有成员字段在类中用于 `CustomLifetimeLease` 跟踪空闲状态，并由 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> 方法返回。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-145">A private member field is used in the `CustomLifetimeLease` class to track the idle state and is returned by the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span> <span data-ttu-id="e3f2b-146">每次 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> 调用方法时， `isIdle` 都会返回字段并将其重置为 `false` 。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-146">Each time the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method is called, the `isIdle` field is returned and reset to `false`.</span></span>  <span data-ttu-id="e3f2b-147">必须将此值设置为 `false`，以确保调度程序调用 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-147">It is essential to set this value to `false` in order to make sure the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> method.</span></span>

```csharp
public bool IsIdle(InstanceContext instanceContext)
{
    get
    {
        lock (thisLock)
        {
            //...
            bool idleCopy = isIdle;
            isIdle = false;
            return idleCopy;
        }
    }
}
```

<span data-ttu-id="e3f2b-148">如果该 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType> 方法返回 `false` ，则调度程序使用方法注册一个回调函数 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> 。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-148">If the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType> method returns `false`, the Dispatcher registers a callback function by using the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> method.</span></span> <span data-ttu-id="e3f2b-149">此方法将接收对所释放的 <xref:System.ServiceModel.InstanceContext> 的引用。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-149">This method receives a reference to the <xref:System.ServiceModel.InstanceContext> being released.</span></span> <span data-ttu-id="e3f2b-150">因此，示例代码可查询 `ICustomLease` 类型扩展并检查 `ICustomLease.IsIdle` 属性是否处于扩展状态。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-150">Therefore, the sample code can query the `ICustomLease` type extension and check the `ICustomLease.IsIdle` property in the extended state.</span></span>

```csharp
public void NotifyIdle(InstanceContextIdleCallback callback,
            InstanceContext instanceContext)
{
    lock (thisLock)
    {
       ICustomLease customLease =
           instanceContext.Extensions.Find<ICustomLease>();
       customLease.Callback = callback;
       isIdle = customLease.IsIdle;
       if (isIdle)
       {
             callback(instanceContext);
       }
    }
}
```

<span data-ttu-id="e3f2b-151">在 `ICustomLease.IsIdle` 检查属性之前，需要设置回调属性，因为这对于在调度程序处于 `CustomLeaseExtension` 空闲状态时通知调度程序是必需的。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-151">Before the `ICustomLease.IsIdle` property is checked, the Callback property needs to be set as this is essential for `CustomLeaseExtension` to notify the Dispatcher when it becomes idle.</span></span> <span data-ttu-id="e3f2b-152">如果 `ICustomLease.IsIdle` 返回 `true`，则 `isIdle` 私有成员仅在 `CustomLifetimeLease` 中设置为 `true`，并调用该回调方法。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-152">If `ICustomLease.IsIdle` returns `true`, the `isIdle` private member is simply set in `CustomLifetimeLease` to `true` and calls the callback method.</span></span> <span data-ttu-id="e3f2b-153">由于代码持有锁，其他线程无法更改此私有成员的值。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-153">Because the code holds a lock, other threads can't change the value of this private member.</span></span> <span data-ttu-id="e3f2b-154">然后，当调度程序下次调用时 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType> ，它将返回， `true` 并让调度程序释放该实例。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-154">And the next time Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType>, it returns `true` and lets Dispatcher release the instance.</span></span>

<span data-ttu-id="e3f2b-155">由于自定义扩展的基础工作已完成，因此必须将其挂钩到服务模型。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-155">Now that the groundwork for the custom extension is completed, it has to be hooked up to the service model.</span></span> <span data-ttu-id="e3f2b-156">为了将实现挂钩 `CustomLeaseExtension` 到 <xref:System.ServiceModel.InstanceContext> ，WCF 提供了执行的 <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> 引导的接口 <xref:System.ServiceModel.InstanceContext> 。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-156">To hook up the `CustomLeaseExtension` implementation to the <xref:System.ServiceModel.InstanceContext>, WCF provides the <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> interface to perform the bootstrapping of <xref:System.ServiceModel.InstanceContext>.</span></span> <span data-ttu-id="e3f2b-157">在此示例中，`CustomLeaseInitializer` 类实现此接口，并将 `CustomLeaseExtension` 的一个实例从仅方法初始化添加到 <xref:System.ServiceModel.InstanceContext.Extensions%2A> 集合。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-157">In the sample, the `CustomLeaseInitializer` class implements this interface and adds an instance of `CustomLeaseExtension` to the <xref:System.ServiceModel.InstanceContext.Extensions%2A> collection from the only method initialization.</span></span> <span data-ttu-id="e3f2b-158">此方法在初始化 <xref:System.ServiceModel.InstanceContext> 时由调度程序调用。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-158">This method is called by Dispatcher while initializing the <xref:System.ServiceModel.InstanceContext>.</span></span>

```csharp
public void InitializeInstanceContext(InstanceContext instanceContext,
    System.ServiceModel.Channels.Message message, IContextChannel channel)

    //...

    IExtension<InstanceContext> customLeaseExtension =
        new CustomLeaseExtension(timeout, headerId);
    instanceContext.Extensions.Add(customLeaseExtension);
}
```

 <span data-ttu-id="e3f2b-159">最后， <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 通过使用实现将实现挂钩到服务模型 <xref:System.ServiceModel.Description.IServiceBehavior> 。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-159">Finally the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is hooked up to the service model by using the <xref:System.ServiceModel.Description.IServiceBehavior> implementation.</span></span> <span data-ttu-id="e3f2b-160">此实现将放置在 `CustomLeaseTimeAttribute` 类中，它还派生自 <xref:System.Attribute> 基类，以将此行为作为特性公开。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-160">This implementation is placed in the `CustomLeaseTimeAttribute` class and it also derives from the <xref:System.Attribute> base class to expose this behavior as an attribute.</span></span>

```csharp
public void ApplyDispatchBehavior(ServiceDescription description,
           ServiceHostBase serviceHostBase)
{
    CustomLifetimeLease customLease = new CustomLifetimeLease(timeout);

    foreach (ChannelDispatcherBase cdb in serviceHostBase.ChannelDispatchers)
    {
        ChannelDispatcher cd = cdb as ChannelDispatcher;

        if (cd != null)
        {
            foreach (EndpointDispatcher ed in cd.Endpoints)
            {
                ed.DispatchRuntime.InstanceContextProvider = customLease;
            }
        }
    }
}
```

<span data-ttu-id="e3f2b-161">可使用 `CustomLeaseTime` 特性对此行为进行批注，以将其添加到示例服务类中。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-161">This behavior can be added to a sample service class by annotating it with the `CustomLeaseTime` attribute.</span></span>

```csharp
[CustomLeaseTime(Timeout = 20000)]
public class EchoService : IEchoService
{
  //…
}
```

<span data-ttu-id="e3f2b-162">运行示例时，操作请求和响应将显示在服务和客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-162">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="e3f2b-163">在每个控制台窗口中按 Enter 可以关闭服务和客户端。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-163">Press ENTER in each console window to shut down the service and client.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e3f2b-164">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="e3f2b-164">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="e3f2b-165">确保已 [为 Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-165">Ensure that you've performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="e3f2b-166">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-166">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="e3f2b-167">若要以单机配置或跨计算机配置来运行示例，请按照 [运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-167">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e3f2b-168">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="e3f2b-168">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e3f2b-169">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="e3f2b-169">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="e3f2b-170">如果此目录不存在，请参阅[Windows Communication Foundation (wcf) ，并 Windows Workflow Foundation (的 WF](https://www.microsoft.com/download/details.aspx?id=21459)) .NET Framework Windows Communication Foundation ([!INCLUDE[wf1](../../../../includes/wf1-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3f2b-170">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e3f2b-171">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="e3f2b-171">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Lifetime`
