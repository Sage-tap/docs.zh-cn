---
description: 了解详细信息：如何：实现发现代理
title: 如何：实现发现代理
ms.date: 03/30/2017
ms.assetid: 78d70e0a-f6c3-4cfb-a7ca-f66ebddadde0
ms.openlocfilehash: e7bd9833ac0d449eefd5e439b442ecb0eee121ca
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793748"
---
# <a name="how-to-implement-a-discovery-proxy"></a><span data-ttu-id="a296c-103">如何：实现发现代理</span><span class="sxs-lookup"><span data-stu-id="a296c-103">How to: Implement a Discovery Proxy</span></span>

<span data-ttu-id="a296c-104">本主题介绍如何实现发现代理。</span><span class="sxs-lookup"><span data-stu-id="a296c-104">This topic explains how to implement a discovery proxy.</span></span> <span data-ttu-id="a296c-105">有关 Windows Communication Foundation (WCF) 中的发现功能的详细信息，请参阅 [Wcf 发现概述](wcf-discovery-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="a296c-105">For more information about the discovery feature in Windows Communication Foundation (WCF), see [WCF Discovery Overview](wcf-discovery-overview.md).</span></span> <span data-ttu-id="a296c-106">可以通过创建一个扩展 <xref:System.ServiceModel.Discovery.DiscoveryProxy> 抽象类的类来实现发现代理。</span><span class="sxs-lookup"><span data-stu-id="a296c-106">A discovery proxy can be implemented by creating a class that extends the <xref:System.ServiceModel.Discovery.DiscoveryProxy> abstract class.</span></span> <span data-ttu-id="a296c-107">此示例中定义并使用了多个其他支持类。</span><span class="sxs-lookup"><span data-stu-id="a296c-107">There are a number of other support classes defined and used in this sample.</span></span> <span data-ttu-id="a296c-108">`OnResolveAsyncResult`、 `OnFindAsyncResult`和 `AsyncResult`。</span><span class="sxs-lookup"><span data-stu-id="a296c-108">`OnResolveAsyncResult`, `OnFindAsyncResult`, and `AsyncResult`.</span></span> <span data-ttu-id="a296c-109">这些类实现 <xref:System.IAsyncResult> 接口。</span><span class="sxs-lookup"><span data-stu-id="a296c-109">These classes implement the <xref:System.IAsyncResult> interface.</span></span> <span data-ttu-id="a296c-110">有关详细信息， <xref:System.IAsyncResult> 请参阅 system.exception [接口](xref:System.IAsyncResult)。</span><span class="sxs-lookup"><span data-stu-id="a296c-110">For more information about <xref:System.IAsyncResult> see [System.IAsyncResult interface](xref:System.IAsyncResult).</span></span>

 <span data-ttu-id="a296c-111">本主题分三个主要部分来讨论如何实现发现代理：</span><span class="sxs-lookup"><span data-stu-id="a296c-111">Implementing a discovery proxy is broken down into three main parts in this topic:</span></span>

- <span data-ttu-id="a296c-112">定义一个包含数据存储并扩展抽象 <xref:System.ServiceModel.Discovery.DiscoveryProxy> 类的类。</span><span class="sxs-lookup"><span data-stu-id="a296c-112">Define a class that contains a data store and extends the abstract <xref:System.ServiceModel.Discovery.DiscoveryProxy> class.</span></span>

- <span data-ttu-id="a296c-113">实现帮助器 `AsyncResult` 类。</span><span class="sxs-lookup"><span data-stu-id="a296c-113">Implement the helper `AsyncResult` class.</span></span>

- <span data-ttu-id="a296c-114">承载发现代理。</span><span class="sxs-lookup"><span data-stu-id="a296c-114">Host the Discovery Proxy.</span></span>

### <a name="to-create-a-new-console-application-project"></a><span data-ttu-id="a296c-115">创建新的控制台应用程序项目</span><span class="sxs-lookup"><span data-stu-id="a296c-115">To create a new console application project</span></span>

1. <span data-ttu-id="a296c-116">启动 Visual Studio 2012。</span><span class="sxs-lookup"><span data-stu-id="a296c-116">Start Visual Studio 2012.</span></span>

2. <span data-ttu-id="a296c-117">创建新的控制台应用程序项目。</span><span class="sxs-lookup"><span data-stu-id="a296c-117">Create a new console application project.</span></span> <span data-ttu-id="a296c-118">将项目命名为 `DiscoveryProxy`，并将解决方案命名为 `DiscoveryProxyExample`。</span><span class="sxs-lookup"><span data-stu-id="a296c-118">Name the project `DiscoveryProxy` and the name the solution `DiscoveryProxyExample`.</span></span>

3. <span data-ttu-id="a296c-119">添加对项目的以下引用</span><span class="sxs-lookup"><span data-stu-id="a296c-119">Add the following references to the project</span></span>

    1. <span data-ttu-id="a296c-120">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="a296c-120">System.ServiceModel.dll</span></span>

    2. <span data-ttu-id="a296c-121">System.Servicemodel.Discovery.dll</span><span class="sxs-lookup"><span data-stu-id="a296c-121">System.Servicemodel.Discovery.dll</span></span>

    > [!CAUTION]
    > <span data-ttu-id="a296c-122">确保引用这些程序集的版本 4.0 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="a296c-122">Ensure that you reference version 4.0 or greater of these assemblies.</span></span>

### <a name="to-implement-the-proxydiscoveryservice-class"></a><span data-ttu-id="a296c-123">实现 ProxyDiscoveryService 类</span><span class="sxs-lookup"><span data-stu-id="a296c-123">To implement the ProxyDiscoveryService class</span></span>

1. <span data-ttu-id="a296c-124">向项目添加新代码文件并将其命名为 DiscoveryProxy.cs。</span><span class="sxs-lookup"><span data-stu-id="a296c-124">Add a new code file to your project and name it DiscoveryProxy.cs.</span></span>

2. <span data-ttu-id="a296c-125">将以下 `using` 语句添加到 DiscoveryProxy.cs。</span><span class="sxs-lookup"><span data-stu-id="a296c-125">Add the following `using` statements to DiscoveryProxy.cs.</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.ServiceModel;
    using System.ServiceModel.Discovery;
    using System.Xml;
    ```

3. <span data-ttu-id="a296c-126">从 `DiscoveryProxyService` 派生 <xref:System.ServiceModel.Discovery.DiscoveryProxy>。</span><span class="sxs-lookup"><span data-stu-id="a296c-126">Derive the `DiscoveryProxyService` from <xref:System.ServiceModel.Discovery.DiscoveryProxy>.</span></span> <span data-ttu-id="a296c-127">将 `ServiceBehavior` 特性应用到下面的示例所示的类。</span><span class="sxs-lookup"><span data-stu-id="a296c-127">Apply the `ServiceBehavior` attribute to the class as shown in the following example.</span></span>

    ```csharp
    // Implement DiscoveryProxy by extending the DiscoveryProxy class and overriding the abstract methods
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single, ConcurrencyMode = ConcurrencyMode.Multiple)]
    public class DiscoveryProxyService : DiscoveryProxy
    {
    }
    ```

4. <span data-ttu-id="a296c-128">在 `DiscoveryProxy` 类内，定义一个字典以保存注册的服务。</span><span class="sxs-lookup"><span data-stu-id="a296c-128">Inside the `DiscoveryProxy` class define a dictionary to hold the registered services.</span></span>

    ```csharp
    // Repository to store EndpointDiscoveryMetadata.
    Dictionary<EndpointAddress, EndpointDiscoveryMetadata> onlineServices;
    ```

5. <span data-ttu-id="a296c-129">定义一个初始化该字典的构造函数。</span><span class="sxs-lookup"><span data-stu-id="a296c-129">Define a constructor that initializes the dictionary.</span></span>

    ```csharp
    public DiscoveryProxyService()
            {
                this.onlineServices = new Dictionary<EndpointAddress, EndpointDiscoveryMetadata>();
            }
    ```

### <a name="to-define-the-methods-used-to-update-the-discovery-proxy-cache"></a><span data-ttu-id="a296c-130">定义用于更新发现代理缓存的方法</span><span class="sxs-lookup"><span data-stu-id="a296c-130">To define the methods used to update the discovery proxy cache</span></span>

1. <span data-ttu-id="a296c-131">实现 `AddOnlineservice` 方法以向缓存中添加服务。</span><span class="sxs-lookup"><span data-stu-id="a296c-131">Implement the `AddOnlineservice` method to add services to the cache.</span></span> <span data-ttu-id="a296c-132">每次代理接收到公告消息时，都会调用此方法。</span><span class="sxs-lookup"><span data-stu-id="a296c-132">This is called every time the proxy receives an announcement message.</span></span>

    ```csharp
    void AddOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)
    {
        lock (this.onlineServices)
        {
            this.onlineServices[endpointDiscoveryMetadata.Address] = endpointDiscoveryMetadata;
        }

        PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Adding");
    }
    ```

2. <span data-ttu-id="a296c-133">实现 `RemoveOnlineService` 方法，该方法用于从缓存删除服务。</span><span class="sxs-lookup"><span data-stu-id="a296c-133">Implement the `RemoveOnlineService` method that is used to remove services from the cache.</span></span>

    ```csharp
    void RemoveOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)
    {
        if (endpointDiscoveryMetadata != null)
        {
            lock (this.onlineServices)
            {
                this.onlineServices.Remove(endpointDiscoveryMetadata.Address);
            }

            PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Removing");
        }
    }
    ```

3. <span data-ttu-id="a296c-134">实现 `MatchFromOnlineService` 方法，这些方法尝试将一个服务与字典中的服务相匹配。</span><span class="sxs-lookup"><span data-stu-id="a296c-134">Implement the `MatchFromOnlineService` methods that attempt to match a service with a service in the dictionary.</span></span>

    ```csharp
    void MatchFromOnlineService(FindRequestContext findRequestContext)
    {
        lock (this.onlineServices)
        {
            foreach (EndpointDiscoveryMetadata endpointDiscoveryMetadata in this.onlineServices.Values)
            {
                if (findRequestContext.Criteria.IsMatch(endpointDiscoveryMetadata))
                {
                    findRequestContext.AddMatchingEndpoint(endpointDiscoveryMetadata);
                }
            }
        }
    }
    ```

    ```csharp
    EndpointDiscoveryMetadata MatchFromOnlineService(ResolveCriteria criteria)
    {
        EndpointDiscoveryMetadata matchingEndpoint = null;
        lock (this.onlineServices)
        {
            foreach (EndpointDiscoveryMetadata endpointDiscoveryMetadata in this.onlineServices.Values)
            {
                if (criteria.Address == endpointDiscoveryMetadata.Address)
                {
                    matchingEndpoint = endpointDiscoveryMetadata;
                }
            }
        }
        return matchingEndpoint;
    }
    ```

4. <span data-ttu-id="a296c-135">实现 `PrintDiscoveryMetadata` 方法，该方法为用户提供发现代理所执行的操作的控制台文本输出。</span><span class="sxs-lookup"><span data-stu-id="a296c-135">Implement the `PrintDiscoveryMetadata` method that provides the user with console text output of what the discovery proxy is doing.</span></span>

    ```csharp
    void PrintDiscoveryMetadata(EndpointDiscoveryMetadata endpointDiscoveryMetadata, string verb)
    {
        Console.WriteLine("\n**** " + verb + " service of the following type from cache. ");
        foreach (XmlQualifiedName contractName in endpointDiscoveryMetadata.ContractTypeNames)
        {
            Console.WriteLine("** " + contractName.ToString());
            break;
        }
        Console.WriteLine("**** Operation Completed");
    }
    ```

5. <span data-ttu-id="a296c-136">将以下 AsyncResult 类添加到 DiscoveryProxyService。</span><span class="sxs-lookup"><span data-stu-id="a296c-136">Add the following AsyncResult classes to the DiscoveryProxyService.</span></span> <span data-ttu-id="a296c-137">这些类用于区分不同的异步操作结果。</span><span class="sxs-lookup"><span data-stu-id="a296c-137">These classes are used to differentiate between the different asynchronous operation results.</span></span>

    ```csharp
    sealed class OnOnlineAnnouncementAsyncResult : AsyncResult
    {
        public OnOnlineAnnouncementAsyncResult(AsyncCallback callback, object state)
            : base(callback, state)
        {
            this.Complete(true);
        }

        public static void End(IAsyncResult result)
        {
            AsyncResult.End<OnOnlineAnnouncementAsyncResult>(result);
        }
    }

    sealed class OnOfflineAnnouncementAsyncResult : AsyncResult
    {
        public OnOfflineAnnouncementAsyncResult(AsyncCallback callback, object state)
            : base(callback, state)
        {
            this.Complete(true);
        }

        public static void End(IAsyncResult result)
        {
            AsyncResult.End<OnOfflineAnnouncementAsyncResult>(result);
        }
    }

    sealed class OnFindAsyncResult : AsyncResult
    {
        public OnFindAsyncResult(AsyncCallback callback, object state)
            : base(callback, state)
        {
            this.Complete(true);
        }

        public static void End(IAsyncResult result)
        {
            AsyncResult.End<OnFindAsyncResult>(result);
        }
    }

    sealed class OnResolveAsyncResult : AsyncResult
    {
        EndpointDiscoveryMetadata matchingEndpoint;

        public OnResolveAsyncResult(EndpointDiscoveryMetadata matchingEndpoint, AsyncCallback callback, object state)
            : base(callback, state)
        {
            this.matchingEndpoint = matchingEndpoint;
            this.Complete(true);
        }

        public static EndpointDiscoveryMetadata End(IAsyncResult result)
        {
            OnResolveAsyncResult thisPtr = AsyncResult.End<OnResolveAsyncResult>(result);
            return thisPtr.matchingEndpoint;
        }
    }
    ```

### <a name="to-define-the-methods-that-implement-the-discovery-proxy-functionality"></a><span data-ttu-id="a296c-138">定义实现发现代理功能的方法</span><span class="sxs-lookup"><span data-stu-id="a296c-138">To define the methods that implement the discovery proxy functionality</span></span>

1. <span data-ttu-id="a296c-139">重写 <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOnlineAnnouncement%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="a296c-139">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOnlineAnnouncement%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a296c-140">当发现代理接收到联机公告消息时，将调用此方法。</span><span class="sxs-lookup"><span data-stu-id="a296c-140">This method is called when the discovery proxy receives an online announcement message.</span></span>

    ```csharp
    // OnBeginOnlineAnnouncement method is called when a Hello message is received by the Proxy
    protected override IAsyncResult OnBeginOnlineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)
    {
        this.AddOnlineService(endpointDiscoveryMetadata);
        return new OnOnlineAnnouncementAsyncResult(callback, state);
    }
    ```

2. <span data-ttu-id="a296c-141">重写 <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOnlineAnnouncement%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="a296c-141">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOnlineAnnouncement%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a296c-142">当发现代理完成处理公告消息时，将调用此方法。</span><span class="sxs-lookup"><span data-stu-id="a296c-142">This method is called when the discovery proxy finishes processing an announcement message.</span></span>

    ```csharp
    protected override void OnEndOnlineAnnouncement(IAsyncResult result)
    {
        OnOnlineAnnouncementAsyncResult.End(result);
    }
    ```

3. <span data-ttu-id="a296c-143">重写 <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOfflineAnnouncement%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="a296c-143">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOfflineAnnouncement%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a296c-144">当发现代理接收到脱机公告消息时，将调用此方法。</span><span class="sxs-lookup"><span data-stu-id="a296c-144">This method is called with the discovery proxy receives an offline announcement message.</span></span>

    ```csharp
    // OnBeginOfflineAnnouncement method is called when a Bye message is received by the Proxy
    protected override IAsyncResult OnBeginOfflineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)
    {
        this.RemoveOnlineService(endpointDiscoveryMetadata);
        return new OnOfflineAnnouncementAsyncResult(callback, state);
    }
    ```

4. <span data-ttu-id="a296c-145">重写 <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOfflineAnnouncement%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="a296c-145">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOfflineAnnouncement%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a296c-146">当发现代理完成处理脱机公告消息时，将调用此方法。</span><span class="sxs-lookup"><span data-stu-id="a296c-146">This method is called when the discovery proxy finishes processing an offline announcement message.</span></span>

    ```csharp
    protected override void OnEndOfflineAnnouncement(IAsyncResult result)
    {
        OnOfflineAnnouncementAsyncResult.End(result);
    }
    ```

5. <span data-ttu-id="a296c-147">重写 <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="a296c-147">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a296c-148">当发现代理接收到查找请求时，将调用此方法。</span><span class="sxs-lookup"><span data-stu-id="a296c-148">This method is called when the discovery proxy receives a find request.</span></span>

    ```csharp
    // OnBeginFind method is called when a Probe request message is received by the Proxy
    protected override IAsyncResult OnBeginFind(FindRequestContext findRequestContext, AsyncCallback callback, object state)
    {
        this.MatchFromOnlineService(findRequestContext);
        return new OnFindAsyncResult(callback, state);
    }
    protected override IAsyncResult OnBeginFind(FindRequest findRequest, AsyncCallback callback, object state)
    {
        Collection<EndpointDiscoveryMetadata> matchingEndpoints = MatchFromCache(findRequest.Criteria);
        return new OnFindAsyncResult(
                    matchingEndpoints,
                    callback,
                    state);
    }
    ```

6. <span data-ttu-id="a296c-149">重写 <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="a296c-149">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a296c-150">当发现代理完成查找请求的处理时，将调用此方法。</span><span class="sxs-lookup"><span data-stu-id="a296c-150">This method is called when the discovery proxy finishes processing a find request.</span></span>

    ```csharp
    protected override void OnEndFind(IAsyncResult result)
    {
        OnFindAsyncResult.End(result);
    }
    ```

7. <span data-ttu-id="a296c-151">重写 <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginResolve%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="a296c-151">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginResolve%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a296c-152">当发现代理接收到解决消息时，将调用此方法。</span><span class="sxs-lookup"><span data-stu-id="a296c-152">This method is called when the discovery proxy receives a resolve message.</span></span>

    ```csharp
    // OnBeginFind method is called when a Resolve request message is received by the Proxy
    protected override IAsyncResult OnBeginResolve(ResolveCriteria resolveCriteria, AsyncCallback callback, object state)
    {
        return new OnResolveAsyncResult(this.MatchFromOnlineService(resolveCriteria), callback, state);
    }
    protected override IAsyncResult OnBeginResolve(ResolveRequest resolveRequest, AsyncCallback callback, object state)
    {
        return new OnResolveAsyncResult(
            this.proxy.MatchFromOnlineService(resolveRequest.Criteria),
            callback,
            state);
    }
    ```

8. <span data-ttu-id="a296c-153">重写 <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndResolve%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="a296c-153">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndResolve%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a296c-154">当发现代理完成处理解决消息时，将调用此方法。</span><span class="sxs-lookup"><span data-stu-id="a296c-154">This method is called when the discovery proxy finishes processing a resolve message.</span></span>

    ```csharp
    protected override EndpointDiscoveryMetadata OnEndResolve(IAsyncResult result)
    {
        return OnResolveAsyncResult.End(result);
    }
    ```

<span data-ttu-id="a296c-155">OnBegin.</span><span class="sxs-lookup"><span data-stu-id="a296c-155">The OnBegin..</span></span> <span data-ttu-id="a296c-156">/ OnEnd.</span><span class="sxs-lookup"><span data-stu-id="a296c-156">/ OnEnd..</span></span> <span data-ttu-id="a296c-157">方法提供后续发现操作的逻辑。</span><span class="sxs-lookup"><span data-stu-id="a296c-157">methods provide the logic for the subsequent discovery operations.</span></span> <span data-ttu-id="a296c-158">例如，<xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A> 和 <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A> 方法实现发现代理的查找逻辑。</span><span class="sxs-lookup"><span data-stu-id="a296c-158">For example the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A> and <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A> methods implement the find logic for discovery proxy.</span></span> <span data-ttu-id="a296c-159">当发现代理接收到探测消息时，将执行这些方法以便向客户端回发响应。</span><span class="sxs-lookup"><span data-stu-id="a296c-159">When the discovery proxy receives a probe message these methods are executed to send a response back to the client.</span></span> <span data-ttu-id="a296c-160">您可以根据需要修改查找逻辑，例如，可以将按算法实现的自定义范围匹配或应用程序特定 XML 元数据分析合并到查找操作中。</span><span class="sxs-lookup"><span data-stu-id="a296c-160">You may modify the find logic as you wish, for example you can incorporate custom scope matching by algorithms or application specific XML metadata parsing as part of your find operation.</span></span>

### <a name="to-implement-the-asyncresult-class"></a><span data-ttu-id="a296c-161">实现 AsyncResult 类</span><span class="sxs-lookup"><span data-stu-id="a296c-161">To implement the AsyncResult class</span></span>

1. <span data-ttu-id="a296c-162">定义用于派生各种异步结果类的抽象基类 AsyncResult。</span><span class="sxs-lookup"><span data-stu-id="a296c-162">Define the abstract base class AsyncResult which is used to derive the various async result classes.</span></span>

2. <span data-ttu-id="a296c-163">创建一个名为 AsyncResult.cs 的新代码文件。</span><span class="sxs-lookup"><span data-stu-id="a296c-163">Create a new code file called AsyncResult.cs.</span></span>

3. <span data-ttu-id="a296c-164">将以下 `using` 语句添加到 AsyncResult.cs。</span><span class="sxs-lookup"><span data-stu-id="a296c-164">Add the following `using` statements to AsyncResult.cs.</span></span>

    ```csharp
    using System;
    using System.Threading;
    ```

4. <span data-ttu-id="a296c-165">添加以下 AsyncResult 类。</span><span class="sxs-lookup"><span data-stu-id="a296c-165">Add the following AsyncResult class.</span></span>

    ```csharp
    abstract class AsyncResult : IAsyncResult
    {
        AsyncCallback callback;
        bool completedSynchronously;
        bool endCalled;
        Exception exception;
        bool isCompleted;
        ManualResetEvent manualResetEvent;
        object state;
        object thisLock;

        protected AsyncResult(AsyncCallback callback, object state)
        {
            this.callback = callback;
            this.state = state;
            this.thisLock = new object();
        }

        public object AsyncState
        {
            get
            {
                return state;
            }
        }

        public WaitHandle AsyncWaitHandle
        {
            get
            {
                if (manualResetEvent != null)
                {
                    return manualResetEvent;
                }
                lock (ThisLock)
                {
                    manualResetEvent ??= new ManualResetEvent(isCompleted);
                }
                return manualResetEvent;
            }
        }

        public bool CompletedSynchronously
        {
            get
            {
                return completedSynchronously;
            }
        }

        public bool IsCompleted
        {
            get
            {
                return isCompleted;
            }
        }

        object ThisLock
        {
            get
            {
                return this.thisLock;
            }
        }

        protected static TAsyncResult End<TAsyncResult>(IAsyncResult result)
            where TAsyncResult : AsyncResult
        {
            if (result == null)
            {
                throw new ArgumentNullException("result");
            }

            TAsyncResult asyncResult = result as TAsyncResult;

            if (asyncResult == null)
            {
                throw new ArgumentException("Invalid async result.", "result");
            }

            if (asyncResult.endCalled)
            {
                throw new InvalidOperationException("Async object already ended.");
            }

            asyncResult.endCalled = true;

            if (!asyncResult.isCompleted)
            {
                asyncResult.AsyncWaitHandle.WaitOne();
            }

            if (asyncResult.manualResetEvent != null)
            {
                asyncResult.manualResetEvent.Close();
            }

            if (asyncResult.exception != null)
            {
                throw asyncResult.exception;
            }

            return asyncResult;
        }

        protected void Complete(bool completedSynchronously)
        {
            if (isCompleted)
            {
                throw new InvalidOperationException("This async result is already completed.");
            }

            this.completedSynchronously = completedSynchronously;

            if (completedSynchronously)
            {
                this.isCompleted = true;
            }
            else
            {
                lock (ThisLock)
                {
                    this.isCompleted = true;
                    if (this.manualResetEvent != null)
                    {
                        this.manualResetEvent.Set();
                    }
                }
            }

            if (callback != null)
            {
                callback(this);
            }
        }

        protected void Complete(bool completedSynchronously, Exception exception)
        {
            this.exception = exception;
            Complete(completedSynchronously);
        }
    }
    ```

### <a name="to-host-the-discoveryproxy"></a><span data-ttu-id="a296c-166">承载 DiscoveryProxy</span><span class="sxs-lookup"><span data-stu-id="a296c-166">To host the DiscoveryProxy</span></span>

1. <span data-ttu-id="a296c-167">打开 DiscoveryProxyExample 项目中的 Program.cs 文件。</span><span class="sxs-lookup"><span data-stu-id="a296c-167">Open the Program.cs file in the DiscoveryProxyExample project.</span></span>

2. <span data-ttu-id="a296c-168">添加以下 `using` 语句。</span><span class="sxs-lookup"><span data-stu-id="a296c-168">Add the following `using` statements.</span></span>

    ```csharp
    using System;
    using System.ServiceModel;
    using System.ServiceModel.Discovery;
    ```

3. <span data-ttu-id="a296c-169">在 `Main()` 方法中，添加下面的代码。</span><span class="sxs-lookup"><span data-stu-id="a296c-169">Within the `Main()` method, add the following code.</span></span> <span data-ttu-id="a296c-170">这将创建 `DiscoveryProxy` 类的一个实例。</span><span class="sxs-lookup"><span data-stu-id="a296c-170">This creates an instance of the `DiscoveryProxy` class.</span></span>

    ```csharp
    Uri probeEndpointAddress = new Uri("net.tcp://localhost:8001/Probe");
    Uri announcementEndpointAddress = new Uri("net.tcp://localhost:9021/Announcement");

    // Host the DiscoveryProxy service
    ServiceHost proxyServiceHost = new ServiceHost(new DiscoveryProxyService());
    ```

4. <span data-ttu-id="a296c-171">接下来，将以下代码添加到发现终结点和公告终结点。</span><span class="sxs-lookup"><span data-stu-id="a296c-171">Next add the following code to add a discovery endpoint and an announcement endpoint.</span></span>

    ```csharp
    try
    {
        // Add DiscoveryEndpoint to receive Probe and Resolve messages
        DiscoveryEndpoint discoveryEndpoint = new DiscoveryEndpoint(new NetTcpBinding(), new EndpointAddress(probeEndpointAddress));
        discoveryEndpoint.IsSystemEndpoint = false;

        // Add AnnouncementEndpoint to receive Hello and Bye announcement messages
        AnnouncementEndpoint announcementEndpoint = new AnnouncementEndpoint(new NetTcpBinding(), new EndpointAddress(announcementEndpointAddress));

        proxyServiceHost.AddServiceEndpoint(discoveryEndpoint);
        proxyServiceHost.AddServiceEndpoint(announcementEndpoint);

        proxyServiceHost.Open();

        Console.WriteLine("Proxy Service started.");
        Console.WriteLine();
        Console.WriteLine("Press <ENTER> to terminate the service.");
        Console.WriteLine();
        Console.ReadLine();

        proxyServiceHost.Close();
    }
    catch (CommunicationException e)
    {
        Console.WriteLine(e.Message);
    }
    catch (TimeoutException e)
    {
        Console.WriteLine(e.Message);
    }

    if (proxyServiceHost.State != CommunicationState.Closed)
    {
        Console.WriteLine("Aborting the service...");
        proxyServiceHost.Abort();
    }
    ```

<span data-ttu-id="a296c-172">您已完成实现发现代理。</span><span class="sxs-lookup"><span data-stu-id="a296c-172">You have completed implementing the discovery proxy.</span></span> <span data-ttu-id="a296c-173">继续 [操作如何：实现使用发现代理注册的可发现服务](discoverable-service-that-registers-with-the-discovery-proxy.md)。</span><span class="sxs-lookup"><span data-stu-id="a296c-173">Continue on to [How to: Implement a Discoverable Service that Registers with the Discovery Proxy](discoverable-service-that-registers-with-the-discovery-proxy.md).</span></span>

## <a name="example"></a><span data-ttu-id="a296c-174">示例</span><span class="sxs-lookup"><span data-stu-id="a296c-174">Example</span></span>

<span data-ttu-id="a296c-175">下面是本主题中使用的代码的完整清单。</span><span class="sxs-lookup"><span data-stu-id="a296c-175">This is the full listing of the code used in this topic.</span></span>

```csharp
// DiscoveryProxy.cs
//----------------------------------------------------------------
// Copyright (c) Microsoft Corporation.  All rights reserved.
//----------------------------------------------------------------

using System;
using System.Collections.Generic;
using System.ServiceModel;
using System.ServiceModel.Discovery;
using System.Xml;

namespace Microsoft.Samples.Discovery
{
    // Implement DiscoveryProxy by extending the DiscoveryProxy class and overriding the abstract methods
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single, ConcurrencyMode = ConcurrencyMode.Multiple)]
    public class DiscoveryProxyService : DiscoveryProxy
    {
        // Repository to store EndpointDiscoveryMetadata. A database or a flat file could also be used instead.
        Dictionary<EndpointAddress, EndpointDiscoveryMetadata> onlineServices;

        public DiscoveryProxyService()
        {
            this.onlineServices = new Dictionary<EndpointAddress, EndpointDiscoveryMetadata>();
        }

        // OnBeginOnlineAnnouncement method is called when a Hello message is received by the Proxy
        protected override IAsyncResult OnBeginOnlineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)
        {
            this.AddOnlineService(endpointDiscoveryMetadata);
            return new OnOnlineAnnouncementAsyncResult(callback, state);
        }

        protected override void OnEndOnlineAnnouncement(IAsyncResult result)
        {
            OnOnlineAnnouncementAsyncResult.End(result);
        }

        // OnBeginOfflineAnnouncement method is called when a Bye message is received by the Proxy
        protected override IAsyncResult OnBeginOfflineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)
        {
            this.RemoveOnlineService(endpointDiscoveryMetadata);
            return new OnOfflineAnnouncementAsyncResult(callback, state);
        }

        protected override void OnEndOfflineAnnouncement(IAsyncResult result)
        {
            OnOfflineAnnouncementAsyncResult.End(result);
        }

        // OnBeginFind method is called when a Probe request message is received by the Proxy
        protected override IAsyncResult OnBeginFind(FindRequestContext findRequestContext, AsyncCallback callback, object state)
        {
            this.MatchFromOnlineService(findRequestContext);
            return new OnFindAsyncResult(callback, state);
        }

        protected override void OnEndFind(IAsyncResult result)
        {
            OnFindAsyncResult.End(result);
        }

        // OnBeginFind method is called when a Resolve request message is received by the Proxy
        protected override IAsyncResult OnBeginResolve(ResolveCriteria resolveCriteria, AsyncCallback callback, object state)
        {
            return new OnResolveAsyncResult(this.MatchFromOnlineService(resolveCriteria), callback, state);
        }

        protected override EndpointDiscoveryMetadata OnEndResolve(IAsyncResult result)
        {
            return OnResolveAsyncResult.End(result);
        }

        // The following are helper methods required by the Proxy implementation
        void AddOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)
        {
            lock (this.onlineServices)
            {
                this.onlineServices[endpointDiscoveryMetadata.Address] = endpointDiscoveryMetadata;
            }

            PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Adding");
        }

        void RemoveOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)
        {
            if (endpointDiscoveryMetadata != null)
            {
                lock (this.onlineServices)
                {
                    this.onlineServices.Remove(endpointDiscoveryMetadata.Address);
                }

                PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Removing");
            }
        }

        void MatchFromOnlineService(FindRequestContext findRequestContext)
        {
            lock (this.onlineServices)
            {
                foreach (EndpointDiscoveryMetadata endpointDiscoveryMetadata in this.onlineServices.Values)
                {
                    if (findRequestContext.Criteria.IsMatch(endpointDiscoveryMetadata))
                    {
                        findRequestContext.AddMatchingEndpoint(endpointDiscoveryMetadata);
                    }
                }
            }
        }

        EndpointDiscoveryMetadata MatchFromOnlineService(ResolveCriteria criteria)
        {
            EndpointDiscoveryMetadata matchingEndpoint = null;
            lock (this.onlineServices)
            {
                foreach (EndpointDiscoveryMetadata endpointDiscoveryMetadata in this.onlineServices.Values)
                {
                    if (criteria.Address == endpointDiscoveryMetadata.Address)
                    {
                        matchingEndpoint = endpointDiscoveryMetadata;
                    }
                }
            }
            return matchingEndpoint;
        }

        void PrintDiscoveryMetadata(EndpointDiscoveryMetadata endpointDiscoveryMetadata, string verb)
        {
            Console.WriteLine("\n**** " + verb + " service of the following type from cache. ");
            foreach (XmlQualifiedName contractName in endpointDiscoveryMetadata.ContractTypeNames)
            {
                Console.WriteLine("** " + contractName.ToString());
                break;
            }
            Console.WriteLine("**** Operation Completed");
        }

        sealed class OnOnlineAnnouncementAsyncResult : AsyncResult
        {
            public OnOnlineAnnouncementAsyncResult(AsyncCallback callback, object state)
                : base(callback, state)
            {
                this.Complete(true);
            }

            public static void End(IAsyncResult result)
            {
                AsyncResult.End<OnOnlineAnnouncementAsyncResult>(result);
            }
        }

        sealed class OnOfflineAnnouncementAsyncResult : AsyncResult
        {
            public OnOfflineAnnouncementAsyncResult(AsyncCallback callback, object state)
                : base(callback, state)
            {
                this.Complete(true);
            }

            public static void End(IAsyncResult result)
            {
                AsyncResult.End<OnOfflineAnnouncementAsyncResult>(result);
            }
        }

        sealed class OnFindAsyncResult : AsyncResult
        {
            public OnFindAsyncResult(AsyncCallback callback, object state)
                : base(callback, state)
            {
                this.Complete(true);
            }

            public static void End(IAsyncResult result)
            {
                AsyncResult.End<OnFindAsyncResult>(result);
            }
        }

        sealed class OnResolveAsyncResult : AsyncResult
        {
            EndpointDiscoveryMetadata matchingEndpoint;

            public OnResolveAsyncResult(EndpointDiscoveryMetadata matchingEndpoint, AsyncCallback callback, object state)
                : base(callback, state)
            {
                this.matchingEndpoint = matchingEndpoint;
                this.Complete(true);
            }

            public static EndpointDiscoveryMetadata End(IAsyncResult result)
            {
                OnResolveAsyncResult thisPtr = AsyncResult.End<OnResolveAsyncResult>(result);
                return thisPtr.matchingEndpoint;
            }
        }
    }
}
```

```csharp
// AsyncResult.cs
//----------------------------------------------------------------
// Copyright (c) Microsoft Corporation.  All rights reserved.
//----------------------------------------------------------------

using System;
using System.Threading;

namespace Microsoft.Samples.Discovery
{
    abstract class AsyncResult : IAsyncResult
    {
        AsyncCallback callback;
        bool completedSynchronously;
        bool endCalled;
        Exception exception;
        bool isCompleted;
        ManualResetEvent manualResetEvent;
        object state;
        object thisLock;

        protected AsyncResult(AsyncCallback callback, object state)
        {
            this.callback = callback;
            this.state = state;
            this.thisLock = new object();
        }

        public object AsyncState
        {
            get
            {
                return state;
            }
        }

        public WaitHandle AsyncWaitHandle
        {
            get
            {
                if (manualResetEvent != null)
                {
                    return manualResetEvent;
                }
                lock (ThisLock)
                {
                    manualResetEvent ??= new ManualResetEvent(isCompleted);
                }
                return manualResetEvent;
            }
        }

        public bool CompletedSynchronously
        {
            get
            {
                return completedSynchronously;
            }
        }

        public bool IsCompleted
        {
            get
            {
                return isCompleted;
            }
        }

        object ThisLock
        {
            get
            {
                return this.thisLock;
            }
        }

        protected static TAsyncResult End<TAsyncResult>(IAsyncResult result)
            where TAsyncResult : AsyncResult
        {
            if (result == null)
            {
                throw new ArgumentNullException("result");
            }

            TAsyncResult asyncResult = result as TAsyncResult;

            if (asyncResult == null)
            {
                throw new ArgumentException("Invalid async result.", "result");
            }

            if (asyncResult.endCalled)
            {
                throw new InvalidOperationException("Async object already ended.");
            }

            asyncResult.endCalled = true;

            if (!asyncResult.isCompleted)
            {
                asyncResult.AsyncWaitHandle.WaitOne();
            }

            if (asyncResult.manualResetEvent != null)
            {
                asyncResult.manualResetEvent.Close();
            }

            if (asyncResult.exception != null)
            {
                throw asyncResult.exception;
            }

            return asyncResult;
        }

        protected void Complete(bool completedSynchronously)
        {
            if (isCompleted)
            {
                throw new InvalidOperationException("This async result is already completed.");
            }

            this.completedSynchronously = completedSynchronously;

            if (completedSynchronously)
            {
                this.isCompleted = true;
            }
            else
            {
                lock (ThisLock)
                {
                    this.isCompleted = true;
                    if (this.manualResetEvent != null)
                    {
                        this.manualResetEvent.Set();
                    }
                }
            }

            if (callback != null)
            {
                callback(this);
            }
        }

        protected void Complete(bool completedSynchronously, Exception exception)
        {
            this.exception = exception;
            Complete(completedSynchronously);
        }
    }
}
```

```csharp
// program.cs
//----------------------------------------------------------------
// Copyright (c) Microsoft Corporation.  All rights reserved.
//----------------------------------------------------------------

using System;
using System.ServiceModel;
using System.ServiceModel.Discovery;

namespace Microsoft.Samples.Discovery
{
    class Program
    {
        public static void Main()
        {
            Uri probeEndpointAddress = new Uri("net.tcp://localhost:8001/Probe");
            Uri announcementEndpointAddress = new Uri("net.tcp://localhost:9021/Announcement");

            // Host the DiscoveryProxy service
            ServiceHost proxyServiceHost = new ServiceHost(new DiscoveryProxyService());

            try
            {
                // Add DiscoveryEndpoint to receive Probe and Resolve messages
                DiscoveryEndpoint discoveryEndpoint = new DiscoveryEndpoint(new NetTcpBinding(), new EndpointAddress(probeEndpointAddress));
                discoveryEndpoint.IsSystemEndpoint = false;

                // Add AnnouncementEndpoint to receive Hello and Bye announcement messages
                AnnouncementEndpoint announcementEndpoint = new AnnouncementEndpoint(new NetTcpBinding(), new EndpointAddress(announcementEndpointAddress));

                proxyServiceHost.AddServiceEndpoint(discoveryEndpoint);
                proxyServiceHost.AddServiceEndpoint(announcementEndpoint);

                proxyServiceHost.Open();

                Console.WriteLine("Proxy Service started.");
                Console.WriteLine();
                Console.WriteLine("Press <ENTER> to terminate the service.");
                Console.WriteLine();
                Console.ReadLine();

                proxyServiceHost.Close();
            }
            catch (CommunicationException e)
            {
                Console.WriteLine(e.Message);
            }
            catch (TimeoutException e)
            {
                Console.WriteLine(e.Message);
            }

            if (proxyServiceHost.State != CommunicationState.Closed)
            {
                Console.WriteLine("Aborting the service...");
                proxyServiceHost.Abort();
            }
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="a296c-176">请参阅</span><span class="sxs-lookup"><span data-stu-id="a296c-176">See also</span></span>

- [<span data-ttu-id="a296c-177">WCF Discovery 概述</span><span class="sxs-lookup"><span data-stu-id="a296c-177">WCF Discovery Overview</span></span>](wcf-discovery-overview.md)
- [<span data-ttu-id="a296c-178">如何：实现向发现代理注册的可发现的服务</span><span class="sxs-lookup"><span data-stu-id="a296c-178">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](discoverable-service-that-registers-with-the-discovery-proxy.md)
- [<span data-ttu-id="a296c-179">如何：实现使用发现代理查找服务的客户端应用程序</span><span class="sxs-lookup"><span data-stu-id="a296c-179">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](client-app-discovery-proxy-to-find-a-service.md)
- [<span data-ttu-id="a296c-180">如何：测试发现代理</span><span class="sxs-lookup"><span data-stu-id="a296c-180">How to: Test the Discovery Proxy</span></span>](how-to-test-the-discovery-proxy.md)
