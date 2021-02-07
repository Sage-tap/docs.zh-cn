---
description: 了解详细信息：更改发送活动的缓存共享级别
title: 更改发送活动的缓存共享级别
ms.date: 03/30/2017
ms.assetid: 03926a64-753d-460e-ac06-2a4ff8e1bbf5
ms.openlocfilehash: 7ced6a8a18779a0c0d5914e63fde658b6d0130ac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705208"
---
# <a name="changing-the-cache-sharing-levels-for-send-activities"></a><span data-ttu-id="e2bb0-103">更改发送活动的缓存共享级别</span><span class="sxs-lookup"><span data-stu-id="e2bb0-103">Changing the Cache Sharing Levels for Send Activities</span></span>

<span data-ttu-id="e2bb0-104">使用 <xref:System.ServiceModel.Activities.SendMessageChannelCache> 扩展可以自定义缓存共享级别、通道工厂缓存的设置，以及使用 <xref:System.ServiceModel.Activities.Send> 消息传递活动将消息发送到服务终结点的工作流的通道缓存的设置。</span><span class="sxs-lookup"><span data-stu-id="e2bb0-104">The <xref:System.ServiceModel.Activities.SendMessageChannelCache> extension enables you to customize the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using <xref:System.ServiceModel.Activities.Send> messaging activities.</span></span> <span data-ttu-id="e2bb0-105">这些工作流通常是客户端工作流，但也可以是在 <xref:System.ServiceModel.WorkflowServiceHost> 中承载的工作流服务。</span><span class="sxs-lookup"><span data-stu-id="e2bb0-105">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span> <span data-ttu-id="e2bb0-106">通道工厂缓存包含已缓存的 <xref:System.ServiceModel.ChannelFactory%601> 对象。</span><span class="sxs-lookup"><span data-stu-id="e2bb0-106">The channel factory cache contains cached <xref:System.ServiceModel.ChannelFactory%601> objects.</span></span> <span data-ttu-id="e2bb0-107">通道缓存包含已缓存的通道。</span><span class="sxs-lookup"><span data-stu-id="e2bb0-107">The channel cache contains cached channels.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e2bb0-108">工作流可以使用 <xref:System.ServiceModel.Activities.Send> 消息传递活动发送消息或参数。</span><span class="sxs-lookup"><span data-stu-id="e2bb0-108">Workflows can use <xref:System.ServiceModel.Activities.Send> messaging activities to send either messages or parameters.</span></span> <span data-ttu-id="e2bb0-109">工作流运行时将通道工厂添加到缓存，该缓存在您将 <xref:System.ServiceModel.Channels.IRequestChannel> 活动与 <xref:System.ServiceModel.Activities.ReceiveReply> 活动一起使用时会创建 <xref:System.ServiceModel.Activities.Send> 类型的通道，而在只使用 <xref:System.ServiceModel.Channels.IOutputChannel> 活动时（无 <xref:System.ServiceModel.Activities.Send>）会创建 <xref:System.ServiceModel.Activities.ReceiveReply> 类型的通道。</span><span class="sxs-lookup"><span data-stu-id="e2bb0-109">The workflow runtime adds channel factories to the cache that create channels of type <xref:System.ServiceModel.Channels.IRequestChannel> when you use a <xref:System.ServiceModel.Activities.ReceiveReply> activity with a <xref:System.ServiceModel.Activities.Send> activity, and an <xref:System.ServiceModel.Channels.IOutputChannel> when just using a <xref:System.ServiceModel.Activities.Send> activity (no <xref:System.ServiceModel.Activities.ReceiveReply>).</span></span>  
  
## <a name="the-cache-sharing-levels"></a><span data-ttu-id="e2bb0-110">缓存共享级别</span><span class="sxs-lookup"><span data-stu-id="e2bb0-110">The Cache Sharing Levels</span></span>  

 <span data-ttu-id="e2bb0-111">默认情况下，在 <xref:System.ServiceModel.WorkflowServiceHost> 所承载的工作流中，由 <xref:System.ServiceModel.Activities.Send> 消息传递活动使用的缓存可在 <xref:System.ServiceModel.WorkflowServiceHost> 中的所有工作流实例之间共享（宿主级缓存）。</span><span class="sxs-lookup"><span data-stu-id="e2bb0-111">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost> the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="e2bb0-112">对于未由 <xref:System.ServiceModel.WorkflowServiceHost> 承载的客户端工作流，缓存仅对该工作流实例可用（实例级缓存）。</span><span class="sxs-lookup"><span data-stu-id="e2bb0-112">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="e2bb0-113">除非启用了不安全缓存，否则缓存只对未使用配置中定义的终结点的 <xref:System.ServiceModel.Activities.Send> 活动可用。</span><span class="sxs-lookup"><span data-stu-id="e2bb0-113">The cache is only available for <xref:System.ServiceModel.Activities.Send> activities that do not use endpoints defined in configuration unless unsafe caching is enabled.</span></span>  
  
 <span data-ttu-id="e2bb0-114">下面介绍了可供工作流中的 <xref:System.ServiceModel.Activities.Send> 活动使用的各种缓存共享级别及其建议用法：</span><span class="sxs-lookup"><span data-stu-id="e2bb0-114">The following are the different cache sharing levels available for <xref:System.ServiceModel.Activities.Send> activities in a workflow and their recommended use:</span></span>  
  
- <span data-ttu-id="e2bb0-115">**主机级别**：在宿主共享级别，缓存仅对工作流服务主机中承载的工作流实例可用。</span><span class="sxs-lookup"><span data-stu-id="e2bb0-115">**Host Level**: In the host sharing level, the cache is available only to the workflow instances hosted in the workflow service host.</span></span> <span data-ttu-id="e2bb0-116">缓存还可在进程范围的缓存中的工作流服务主机之间共享。</span><span class="sxs-lookup"><span data-stu-id="e2bb0-116">A cache can also be shared between workflow service hosts in a process-wide cache.</span></span>  
  
- <span data-ttu-id="e2bb0-117">**实例级**：在实例共享级别，缓存在其整个生存期内可用于特定工作流实例，但该缓存不适用于其他工作流实例。</span><span class="sxs-lookup"><span data-stu-id="e2bb0-117">**Instance Level**: In the instance sharing level, the cache is available to a particular workflow instance throughout its lifetime but the cache is not available to other workflow instances.</span></span>  
  
- <span data-ttu-id="e2bb0-118">**无缓存**：默认情况下，如果你有使用配置中定义的终结点的工作流，则缓存处于关闭状态。</span><span class="sxs-lookup"><span data-stu-id="e2bb0-118">**No Cache**: The cache is turned off by default if you have a workflow that uses endpoints defined in configuration.</span></span> <span data-ttu-id="e2bb0-119">在这种情况下，由于打开缓存可能会造成不安全的情况，因此也建议关闭缓存。</span><span class="sxs-lookup"><span data-stu-id="e2bb0-119">It is also recommended to keep the cache turned off in this case because turning it on could be unsecure.</span></span> <span data-ttu-id="e2bb0-120">例如，在针对每次发送都需要使用不同的标识（不同的凭据或使用模拟）时。</span><span class="sxs-lookup"><span data-stu-id="e2bb0-120">For example, if a different identity (different credentials or using impersonation) is required for each send.</span></span>  
  
## <a name="changing-the-cache-sharing-level-for-a-client-workflow"></a><span data-ttu-id="e2bb0-121">更改客户端工作流的缓存共享级别</span><span class="sxs-lookup"><span data-stu-id="e2bb0-121">Changing the Cache Sharing Level for a Client Workflow</span></span>  

 <span data-ttu-id="e2bb0-122">若要在客户端工作流中设置缓存共享，请将 <xref:System.ServiceModel.Activities.SendMessageChannelCache> 类的实例作为扩展添加到所需的工作流实例集。</span><span class="sxs-lookup"><span data-stu-id="e2bb0-122">To set the cache sharing in a client workflow, add an instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class as an extension to the desired set of workflow instances.</span></span> <span data-ttu-id="e2bb0-123">这样可在所有工作流实例之间共享缓存。</span><span class="sxs-lookup"><span data-stu-id="e2bb0-123">This results in sharing the cache across all the workflow instances.</span></span> <span data-ttu-id="e2bb0-124">下面的代码示例演示如何执行这些步骤。</span><span class="sxs-lookup"><span data-stu-id="e2bb0-124">The following code examples show how to perform these steps.</span></span>  
  
 <span data-ttu-id="e2bb0-125">首先，声明一个 <xref:System.ServiceModel.Activities.SendMessageChannelCache> 类型的实例。</span><span class="sxs-lookup"><span data-stu-id="e2bb0-125">First, declare an instance of type <xref:System.ServiceModel.Activities.SendMessageChannelCache>.</span></span>  
  
```csharp  
// Create an instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension =  
    new SendMessageChannelCache();  
```  
  
 <span data-ttu-id="e2bb0-126">接下来，将缓存扩展添加到各个客户端工作流实例。</span><span class="sxs-lookup"><span data-stu-id="e2bb0-126">Next, add the cache extension to each client workflow instance.</span></span>  
  
```csharp
WorkflowApplication clientInstance1 = new WorkflowApplication(new clientWorkflow1());  
WorkflowApplication clientInstance2 = new WorkflowApplication(new clientWorkflow2());  
  
// Share the cache extension object
  
clientInstance1.Extensions.Add(sharedChannelCacheExtension);  
clientInstance2.Extensions.Add(sharedChannelCacheExtension);  
```  
  
## <a name="changing-the-cache-sharing-level-for-a-hosted-workflow-service"></a><span data-ttu-id="e2bb0-127">更改所承载的工作流服务的缓存共享级别</span><span class="sxs-lookup"><span data-stu-id="e2bb0-127">Changing the Cache Sharing Level for a Hosted Workflow Service</span></span>  

 <span data-ttu-id="e2bb0-128">若要在所承载的工作流服务中设置缓存共享，请将 <xref:System.ServiceModel.Activities.SendMessageChannelCache> 类的实例作为扩展添加到所有工作流服务主机。</span><span class="sxs-lookup"><span data-stu-id="e2bb0-128">To set the cache sharing in a hosted workflow service, add an instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class as an extension to all the workflow service hosts.</span></span> <span data-ttu-id="e2bb0-129">这样可在所有工作流服务主机之间共享缓存。</span><span class="sxs-lookup"><span data-stu-id="e2bb0-129">This results in sharing the cache across all the workflow service hosts.</span></span> <span data-ttu-id="e2bb0-130">下面的代码示例演示如何执行这些步骤。</span><span class="sxs-lookup"><span data-stu-id="e2bb0-130">The following code examples show to perform these steps.</span></span>  
  
 <span data-ttu-id="e2bb0-131">首先，在类级别声明一个 <xref:System.ServiceModel.Activities.SendMessageChannelCache> 类型的实例。</span><span class="sxs-lookup"><span data-stu-id="e2bb0-131">First, declare an instance  of type <xref:System.ServiceModel.Activities.SendMessageChannelCache> at the class level.</span></span>  
  
```csharp  
// Create static instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension = new  
    SendMessageChannelCache();  
```  
  
 <span data-ttu-id="e2bb0-132">接下来，将静态缓存扩展添加到各个工作流服务主机。</span><span class="sxs-lookup"><span data-stu-id="e2bb0-132">Next, add the static cache extension to each workflow service host.</span></span>  
  
```csharp  
WorkflowServiceHost host1 = new WorkflowServiceHost(new serviceWorkflow1(), new Uri(baseAddress1));  
WorkflowServiceHost host2 = new WorkflowServiceHost(new serviceWorkflow2(), new Uri(baseAddress2));  
  
// Share the static cache to get an AppDomain level cache.  
host1.WorkflowExtensions.Add(sharedChannelCacheExtension);  
host2.WorkflowExtensions.Add(sharedChannelCacheExtension);  
```  
  
 <span data-ttu-id="e2bb0-133">若要将所承载的工作流服务的缓存共享设置为实例级缓存，请将 `Func<SendMessageChannelCache>` 委托作为扩展添加到工作流服务主机，并将此委托分配到实例化 <xref:System.ServiceModel.Activities.SendMessageChannelCache> 类的新实例的代码中。</span><span class="sxs-lookup"><span data-stu-id="e2bb0-133">To set the cache sharing in a hosted workflow service to the instance level, add a `Func<SendMessageChannelCache>` delegate as an extension to the workflow service host and assign this delegate to the code that instantiates a new instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class.</span></span> <span data-ttu-id="e2bb0-134">这将为各个工作流实例使用不同的缓存，而不是在工作流服务主机中的所有工作流实例之间共享单个缓存。</span><span class="sxs-lookup"><span data-stu-id="e2bb0-134">This results in a different cache for each individual workflow instance, instead of a single cache shared by all workflow instances in the workflow service host.</span></span> <span data-ttu-id="e2bb0-135">下面的代码示例演示如何使用 lambda 表达式直接定义委托所指向的 <xref:System.ServiceModel.Activities.SendMessageChannelCache> 扩展来实现这一结果。</span><span class="sxs-lookup"><span data-stu-id="e2bb0-135">The following code example shows how to achieve this by using a lambda expression to directly define the <xref:System.ServiceModel.Activities.SendMessageChannelCache> extension that the delegate points to.</span></span>  
  
```csharp
serviceHost.WorkflowExtensions.Add(() => new SendMessageChannelCache  
{  
    // Use FactorySettings property to add custom factory cache settings.  
    FactorySettings = new ChannelCacheSettings
    { MaxItemsInCache = 5, },  
    // Use ChannelSettings property to add custom channel cache settings.  
    ChannelSettings = new ChannelCacheSettings
    { MaxItemsInCache = 10 },  
});  
```  
  
## <a name="customizing-cache-settings"></a><span data-ttu-id="e2bb0-136">自定义缓存设置</span><span class="sxs-lookup"><span data-stu-id="e2bb0-136">Customizing Cache Settings</span></span>  

 <span data-ttu-id="e2bb0-137">您可以为通道工厂缓存和通道缓存自定义缓存设置。</span><span class="sxs-lookup"><span data-stu-id="e2bb0-137">You can customize the cache settings for the channel factory cache and the channel cache.</span></span> <span data-ttu-id="e2bb0-138">缓存设置在 <xref:System.ServiceModel.Activities.ChannelCacheSettings> 类中定义。</span><span class="sxs-lookup"><span data-stu-id="e2bb0-138">The cache settings are defined in the <xref:System.ServiceModel.Activities.ChannelCacheSettings> class.</span></span> <span data-ttu-id="e2bb0-139"><xref:System.ServiceModel.Activities.SendMessageChannelCache>类在其无参数构造函数中为通道工厂缓存和通道缓存定义默认缓存设置。</span><span class="sxs-lookup"><span data-stu-id="e2bb0-139">The <xref:System.ServiceModel.Activities.SendMessageChannelCache> class defines default cache settings for the channel factory cache and the channel cache in its parameterless constructor.</span></span> <span data-ttu-id="e2bb0-140">下表针对各种缓存类型列出了这些缓存设置的默认值。</span><span class="sxs-lookup"><span data-stu-id="e2bb0-140">The following table lists the default values of these cache settings for each type of cache.</span></span>  
  
|<span data-ttu-id="e2bb0-141">设置</span><span class="sxs-lookup"><span data-stu-id="e2bb0-141">Settings</span></span>|<span data-ttu-id="e2bb0-142">LeaseTimeout（分钟）</span><span class="sxs-lookup"><span data-stu-id="e2bb0-142">LeaseTimeout (min)</span></span>|<span data-ttu-id="e2bb0-143">IdleTimeout（分钟）</span><span class="sxs-lookup"><span data-stu-id="e2bb0-143">IdleTimeout (min)</span></span>|<span data-ttu-id="e2bb0-144">MaxItemsInCache</span><span class="sxs-lookup"><span data-stu-id="e2bb0-144">MaxItemsInCache</span></span>|  
|-|-|-|-|  
|<span data-ttu-id="e2bb0-145">工厂缓存默认值</span><span class="sxs-lookup"><span data-stu-id="e2bb0-145">Factory Cache Default</span></span>|<span data-ttu-id="e2bb0-146">TimeSpan.MaxValue</span><span class="sxs-lookup"><span data-stu-id="e2bb0-146">TimeSpan.MaxValue</span></span>|<span data-ttu-id="e2bb0-147">2</span><span class="sxs-lookup"><span data-stu-id="e2bb0-147">2</span></span>|<span data-ttu-id="e2bb0-148">16</span><span class="sxs-lookup"><span data-stu-id="e2bb0-148">16</span></span>|  
|<span data-ttu-id="e2bb0-149">通道缓存默认值</span><span class="sxs-lookup"><span data-stu-id="e2bb0-149">Channel Cache Default</span></span>|<span data-ttu-id="e2bb0-150">5</span><span class="sxs-lookup"><span data-stu-id="e2bb0-150">5</span></span>|<span data-ttu-id="e2bb0-151">2</span><span class="sxs-lookup"><span data-stu-id="e2bb0-151">2</span></span>|<span data-ttu-id="e2bb0-152">16</span><span class="sxs-lookup"><span data-stu-id="e2bb0-152">16</span></span>|  
  
 <span data-ttu-id="e2bb0-153">若要自定义工厂缓存和通道缓存设置，请使用参数化构造函数 <xref:System.ServiceModel.Activities.SendMessageChannelCache> 实例化 <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> 类，并将 <xref:System.ServiceModel.Activities.ChannelCacheSettings> 的新实例以及自定义值传递到各个 `factorySettings` 和 `channelSettings` 参数。</span><span class="sxs-lookup"><span data-stu-id="e2bb0-153">To customize the factory cache and channel cache settings, instantiate the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class using the parameterized constructor <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> and pass a new instance of the <xref:System.ServiceModel.Activities.ChannelCacheSettings> with custom values to each of the `factorySettings` and `channelSettings` parameters.</span></span> <span data-ttu-id="e2bb0-154">接下来，将此类的新实例作为扩展添加到工作流服务主机或工作流实例。</span><span class="sxs-lookup"><span data-stu-id="e2bb0-154">Next, add the new instance of this class as an extension to a workflow service host or a workflow instance.</span></span> <span data-ttu-id="e2bb0-155">下面的代码示例演示如何对工作流实例执行这些步骤。</span><span class="sxs-lookup"><span data-stu-id="e2bb0-155">The following code example shows how to perform these steps for a workflow instance.</span></span>  
  
```csharp  
ChannelCacheSettings factorySettings = new ChannelCacheSettings{  
                        MaxItemsInCache = 5,
                        IdleTimeout = TimeSpan.FromMinutes(5),
                        LeaseTimeout = TimeSpan.FromMinutes(20)};  
  
ChannelCacheSettings channelSettings = new ChannelCacheSettings{  
                        MaxItemsInCache = 5,
                        IdleTimeout = TimeSpan.FromMinutes(2),  
                        LeaseTimeout = TimeSpan.FromMinutes(10) };  
  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache(factorySettings, channelSettings);  
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="e2bb0-156">当工作流服务的配置中定义了终结点时，如果要启用缓存，请使用参数化构造函数 <xref:System.ServiceModel.Activities.SendMessageChannelCache> 实例化 <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> 类，并将 `allowUnsafeCaching` 参数设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="e2bb0-156">To enable caching when your workflow service has endpoints defined in configuration, instantiate the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class using the parameterized constructor <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> with the `allowUnsafeCaching` parameter set to `true`.</span></span> <span data-ttu-id="e2bb0-157">接下来，将此类的新实例作为扩展添加到工作流服务主机或工作流实例。</span><span class="sxs-lookup"><span data-stu-id="e2bb0-157">Next, add the new instance of this class as an extension to a workflow service host or a workflow instance.</span></span> <span data-ttu-id="e2bb0-158">下面的代码示例演示如何为工作流实例启用缓存。</span><span class="sxs-lookup"><span data-stu-id="e2bb0-158">The following code example shows how to enable caching for a workflow instance.</span></span>  
  
```csharp  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache{ AllowUnsafeCaching = true };  
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="e2bb0-159">若要完全禁用通道工厂和通道的缓存，请禁用通道工厂缓存。</span><span class="sxs-lookup"><span data-stu-id="e2bb0-159">To disable the cache completely for the channel factories and the channels, disable the channel factory cache.</span></span> <span data-ttu-id="e2bb0-160">这样还将关闭通道缓存，因为通道由其对应的通道工厂所拥有。</span><span class="sxs-lookup"><span data-stu-id="e2bb0-160">Doing so also turns off the channel cache as the channels are owned by their corresponding channel factories.</span></span> <span data-ttu-id="e2bb0-161">若要禁用通道工厂缓存，请将 `factorySettings` 参数传递到 <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> 构造函数，该参数使用 <xref:System.ServiceModel.Activities.ChannelCacheSettings> 值 0 初始化为 <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> 实例。</span><span class="sxs-lookup"><span data-stu-id="e2bb0-161">To disable the channel factory cache, pass the `factorySettings` parameter to the <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> constructor initialized to a <xref:System.ServiceModel.Activities.ChannelCacheSettings> instance with a <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> value of 0.</span></span> <span data-ttu-id="e2bb0-162">下面的代码示例演示了此过程。</span><span class="sxs-lookup"><span data-stu-id="e2bb0-162">The following code example shows this.</span></span>  
  
```csharp  
// Disable the factory cache. This results in the channel cache to be turned off as well.  
ChannelCacheSettings factorySettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0 };  
  
ChannelCacheSettings channelSettings = new ChannelCacheSettings();  
  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache(factorySettings, channelSettings);
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="e2bb0-163">通过以下方法，可以选择仅使用通道工厂缓存并禁用通道缓存：将 `channelSettings` 参数 <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> 传递到构造函数，该参数使用 <xref:System.ServiceModel.Activities.ChannelCacheSettings> 值 0 初始化为 <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> 实例。</span><span class="sxs-lookup"><span data-stu-id="e2bb0-163">You can choose to use only the channel factory cache and disable the channel cache by passing the `channelSettings` parameter to the <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> constructor initialized to a <xref:System.ServiceModel.Activities.ChannelCacheSettings> instance with a <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> value of 0.</span></span> <span data-ttu-id="e2bb0-164">下面的代码示例演示了此过程。</span><span class="sxs-lookup"><span data-stu-id="e2bb0-164">The following code example shows this.</span></span>  
  
```csharp  
ChannelCacheSettings factorySettings = new ChannelCacheSettings();  
// Disable only the channel cache.  
ChannelCacheSettings channelSettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0};  
  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache(factorySettings, channelSettings);
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="e2bb0-165">在承载的工作流服务中，可以在应用程序配置文件中指定工厂缓存和通道缓存设置。</span><span class="sxs-lookup"><span data-stu-id="e2bb0-165">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="e2bb0-166">为此，应添加一个包含工厂和通道缓存的缓存设置的服务行为，并将此服务行为添加到您的服务中。</span><span class="sxs-lookup"><span data-stu-id="e2bb0-166">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="e2bb0-167">下面的示例显示了配置文件的内容，其中包含 `MyChannelCacheBehavior` 具有自定义工厂缓存和通道缓存设置的服务行为。</span><span class="sxs-lookup"><span data-stu-id="e2bb0-167">The following example shows the contents of a configuration file that contains the `MyChannelCacheBehavior` service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="e2bb0-168">此服务行为通过属性添加到服务 `behaviorConfiguration` 。</span><span class="sxs-lookup"><span data-stu-id="e2bb0-168">This service behavior is added to the service through the `behaviorConfiguration` attribute.</span></span>  
  
```xml  
<configuration>
  <system.serviceModel>  
    <!-- List of other config sections here -->
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="MyChannelCacheBehavior">  
          <sendMessageChannelCache allowUnsafeCaching ="false" >  
            <!-- Control only the host level settings -->
            <factorySettings maxItemsInCache = "8" idleTimeout = "00:05:00" leaseTimeout="10:00:00" />  
            <channelSettings maxItemsInCache = "32" idleTimeout = "00:05:00" leaseTimeout="00:06:00" />  
          </sendMessageChannelCache>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service name="MyService" behaviorConfiguration="MyChannelCacheBehavior" />  
    </services>  
  </system.serviceModel>  
</configuration>  
```
