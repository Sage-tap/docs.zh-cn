---
description: 详细了解：基于时间的缓存策略
title: 基于时间的缓存策略
ms.date: 03/30/2017
helpviewer_keywords:
- time-based cache policies
- cache synchronization date policy
- cache [.NET Framework], time-based policies
- freshness of cached resources
- time, cached resources
- maximum age policy
- synchronization, cache
- staleness of cached resources
- default time-based cache policy
- maximum staleness policy
- content cache policies
- expired content
- minimum freshness policy
- age of cached resources
ms.assetid: 74f0bcaf-5c95-40c1-9967-f3bbf1d2360a
ms.openlocfilehash: 42a76be0da664899295a583d72477de0698cc39e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712293"
---
# <a name="time-based-cache-policies"></a><span data-ttu-id="8e4d3-103">基于时间的缓存策略</span><span class="sxs-lookup"><span data-stu-id="8e4d3-103">Time-Based Cache Policies</span></span>

<span data-ttu-id="8e4d3-104">基于时间的缓存策略使用检索资源的时间、随资源返回的标头和当前时间来定义缓存条目的新鲜度。</span><span class="sxs-lookup"><span data-stu-id="8e4d3-104">A time-based cache policy defines the freshness of cached entries using the time the resource was retrieved, the headers returned with the resource, and the current time.</span></span> <span data-ttu-id="8e4d3-105">设置基于时间的缓存策略时，可使用 <xref:System.Net.Cache.HttpRequestCacheLevel.Default> 基于时间的策略，也可创建自定义的基于时间的策略。</span><span class="sxs-lookup"><span data-stu-id="8e4d3-105">When setting a time-based cache policy, you can either use the <xref:System.Net.Cache.HttpRequestCacheLevel.Default> time-based policy or create a customized time-based policy.</span></span> <span data-ttu-id="8e4d3-106">当对使用超文本传输协议 (HTTP) 获得的资源使用默认的基于时间的策略时，由缓存响应中包含的标头以及 RFC 2616 第 13 和 14 节（可在 [Internet 工程任务组 (IETF)](https://www.ietf.org/) 网站上找到）中指定的行为来确定精确的缓存行为。</span><span class="sxs-lookup"><span data-stu-id="8e4d3-106">When using the default time-based policy for resources obtained using Hypertext Transfer Protocol (HTTP), the exact cache behavior is determined by the headers included in the cached response and by the behaviors specified in sections 13 and 14 of RFC 2616, available at [Internet Engineering Task Force (IETF)](https://www.ietf.org/) website.</span></span> <span data-ttu-id="8e4d3-107">有关演示如何为 HTTP 资源设置默认的基于时间策略的代码示例，请参阅[如何：为应用程序设置默认基于时间的缓存策略](how-to-set-the-default-time-based-cache-policy-for-an-application.md)。</span><span class="sxs-lookup"><span data-stu-id="8e4d3-107">For a code example that demonstrates setting the default time-based policy for HTTP resources, see [How to: Set the Default Time-Based Cache Policy for an Application](how-to-set-the-default-time-based-cache-policy-for-an-application.md).</span></span> <span data-ttu-id="8e4d3-108">有关演示如何创建和使用缓存策略的代码示例，请参阅[在网络应用程序中配置缓存](configuring-caching-in-network-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="8e4d3-108">For code examples that demonstrate creating and using cache policies, see [Configuring Caching in Network Applications](configuring-caching-in-network-applications.md).</span></span>  
  
## <a name="criteria-to-determine-freshness-of-cached-entries"></a><span data-ttu-id="8e4d3-109">用于确定已缓存条目新鲜度的条件</span><span class="sxs-lookup"><span data-stu-id="8e4d3-109">Criteria to Determine Freshness of Cached Entries</span></span>  

 <span data-ttu-id="8e4d3-110">要自定义基于时间的缓存策略，可指定使用以下一个或多个条件来确定已缓存条目的新鲜度：</span><span class="sxs-lookup"><span data-stu-id="8e4d3-110">To customize a time-based cache policy, you can specify that one or more of the following criteria be used to determine the freshness of cached entries:</span></span>  
  
- <span data-ttu-id="8e4d3-111">最长使用时间</span><span class="sxs-lookup"><span data-stu-id="8e4d3-111">Maximum age</span></span>  
  
- <span data-ttu-id="8e4d3-112">最长过期时间</span><span class="sxs-lookup"><span data-stu-id="8e4d3-112">Maximum staleness</span></span>  
  
- <span data-ttu-id="8e4d3-113">最低新鲜度</span><span class="sxs-lookup"><span data-stu-id="8e4d3-113">Minimum freshness</span></span>  
  
- <span data-ttu-id="8e4d3-114">缓存同步日期</span><span class="sxs-lookup"><span data-stu-id="8e4d3-114">Cache synchronization date</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8e4d3-115">使用默认的基于时间的缓存策略不应与设置应用程序的默认缓存策略混淆。</span><span class="sxs-lookup"><span data-stu-id="8e4d3-115">Using the default time-based cache policy should not be confused with setting a default cache policy for your application.</span></span> <span data-ttu-id="8e4d3-116">默认的基于时间的策略是可在请求级别或应用程序级别使用的特定策略。</span><span class="sxs-lookup"><span data-stu-id="8e4d3-116">The default time-based policy is a specific policy that can be used at the request or application level.</span></span> <span data-ttu-id="8e4d3-117">应用程序的默认缓存策略是当未在请求中设置任何策略时生效的策略（基于位置或基于时间）。</span><span class="sxs-lookup"><span data-stu-id="8e4d3-117">The default cache policy for your application is a policy (location-based or time-based) that takes effect when no policy is set on a request.</span></span> <span data-ttu-id="8e4d3-118">有关为应用程序设置默认缓存策略的详细信息，请参阅 <xref:System.Net.WebRequest.DefaultCachePolicy%2A>。</span><span class="sxs-lookup"><span data-stu-id="8e4d3-118">For details on setting a default cache policy for your application, see <xref:System.Net.WebRequest.DefaultCachePolicy%2A>.</span></span>  
  
### <a name="maximum-age"></a><span data-ttu-id="8e4d3-119">Maximum Age</span><span class="sxs-lookup"><span data-stu-id="8e4d3-119">Maximum Age</span></span>  

 <span data-ttu-id="8e4d3-120">最长使用时间策略条件指定资源的缓存副本可使用的时间。</span><span class="sxs-lookup"><span data-stu-id="8e4d3-120">The maximum age policy criterion specifies the amount of time a cached copy of a resource can be used.</span></span> <span data-ttu-id="8e4d3-121">如果资源的缓存副本超过指定的时间，则必须根据服务器上的内容进行检查，重新验证该资源。</span><span class="sxs-lookup"><span data-stu-id="8e4d3-121">If the cached copy of the resource is older than the amount of time specified, the resource must be revalidated by checking it against the content on the server.</span></span> <span data-ttu-id="8e4d3-122">如果最长使用时间允许在资源过期后使用资源，则不符合此条件，除非还指定了最长过期时间值。</span><span class="sxs-lookup"><span data-stu-id="8e4d3-122">If the maximum age would allow the resource to be used after it expires, this criteria is not honored unless a maximum staleness value is also specified.</span></span>  
  
### <a name="maximum-staleness"></a><span data-ttu-id="8e4d3-123">最长过期时间</span><span class="sxs-lookup"><span data-stu-id="8e4d3-123">Maximum Staleness</span></span>  

 <span data-ttu-id="8e4d3-124">最长过期时间策略条件指定资源的缓存副本内容过期后可使用的时间。</span><span class="sxs-lookup"><span data-stu-id="8e4d3-124">The maximum staleness policy criterion specifies the length of time after content expiration that the cached copy of the resource can be used.</span></span> <span data-ttu-id="8e4d3-125">这是允许在资源过期后使用资源的唯一缓存策略条件。</span><span class="sxs-lookup"><span data-stu-id="8e4d3-125">This is the only cache policy criterion that permits resources to be used after they have expired.</span></span>  
  
### <a name="minimum-freshness"></a><span data-ttu-id="8e4d3-126">最低新鲜度</span><span class="sxs-lookup"><span data-stu-id="8e4d3-126">Minimum Freshness</span></span>  

 <span data-ttu-id="8e4d3-127">最低新鲜度策略条件指定资源的缓存副本内容过期前可使用的时间。</span><span class="sxs-lookup"><span data-stu-id="8e4d3-127">The minimum freshness policy criterion specifies the length of time before content expiration that the cached copy of the resource can be used.</span></span> <span data-ttu-id="8e4d3-128">此策略的作用是使缓存条目在过期日之前过期，因此，最低新鲜度和最长过期时间设置是相互排斥的。</span><span class="sxs-lookup"><span data-stu-id="8e4d3-128">This policy has the effect of causing a cache entry to expire before its expiration date; therefore, the minimum freshness and maximum staleness settings are mutually exclusive.</span></span>  
  
## <a name="cache-synchronization-date"></a><span data-ttu-id="8e4d3-129">缓存同步日期</span><span class="sxs-lookup"><span data-stu-id="8e4d3-129">Cache Synchronization Date</span></span>  

 <span data-ttu-id="8e4d3-130">缓存同步日期策略条件确定必须根据服务器上的内容进行检查以重新验证资源的缓存副本的时间。</span><span class="sxs-lookup"><span data-stu-id="8e4d3-130">The cache synchronization date policy criterion determines when a cached copy of a resource must be revalidated by checking it against the content on the server.</span></span> <span data-ttu-id="8e4d3-131">如果缓存项目后内容发生更改，则将从服务器检索内容并存储在缓存中，然后返回到应用程序。</span><span class="sxs-lookup"><span data-stu-id="8e4d3-131">If the content has changed since the item was cached, it is retrieved from the server, stored in the cache, and returned to the application.</span></span> <span data-ttu-id="8e4d3-132">如果内容未更改，则会更新其时间戳，并且应用程序将获取缓存内容。</span><span class="sxs-lookup"><span data-stu-id="8e4d3-132">If the content has not changed, its timestamp is updated and the application gets the cached content.</span></span>  
  
 <span data-ttu-id="8e4d3-133">缓存同步日期允许指定必须重新验证缓存内容的绝对日期。</span><span class="sxs-lookup"><span data-stu-id="8e4d3-133">The cache synchronization date allows you to specify an absolute date when cached contents must be revalidated.</span></span> <span data-ttu-id="8e4d3-134">如果上一次重新验证新缓存条目是在缓存同步日期之前，则仍将根据服务器重新验证。</span><span class="sxs-lookup"><span data-stu-id="8e4d3-134">If a fresh cache entry was last revalidated prior to the cache synchronization date, revalidation with the server still occurs.</span></span> <span data-ttu-id="8e4d3-135">如果在缓存同步日期后重新验证缓存条目，且无其他新鲜度或服务器重新验证要求使缓存条目无效，则使用缓存中的条目。</span><span class="sxs-lookup"><span data-stu-id="8e4d3-135">If the cache entry was revalidated after the cache synchronization date and there are no additional freshness or server revalidation requirements that invalidate the cached entry, the entry from the cache is used.</span></span> <span data-ttu-id="8e4d3-136">如果缓存同步日期设置为未来某个日期，则每次请求时都会重新验证该条目，直到缓存同步日期过去。</span><span class="sxs-lookup"><span data-stu-id="8e4d3-136">If the cache synchronization date is set to a future date, the entry is revalidated every time it is requested, until the cache synchronization date passes.</span></span>  
  
 <span data-ttu-id="8e4d3-137">以下主题介绍组合基于时间的缓存策略条件的影响：</span><span class="sxs-lookup"><span data-stu-id="8e4d3-137">The following topics provide information about the effects of combining time-based cache policy criteria:</span></span>  
  
- [<span data-ttu-id="8e4d3-138">缓存策略交互 — 最长使用期限和最长过期时间</span><span class="sxs-lookup"><span data-stu-id="8e4d3-138">Cache Policy Interaction—Maximum Age and Maximum Staleness</span></span>](cache-policy-interaction-maximum-age-and-maximum-staleness.md)  
  
- [<span data-ttu-id="8e4d3-139">缓存策略交互 — 最长使用期限和最低新鲜度</span><span class="sxs-lookup"><span data-stu-id="8e4d3-139">Cache Policy Interaction—Maximum Age and Minimum Freshness</span></span>](cache-policy-interaction-maximum-age-and-minimum-freshness.md)  
  
## <a name="see-also"></a><span data-ttu-id="8e4d3-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8e4d3-140">See also</span></span>

- [<span data-ttu-id="8e4d3-141">网络应用程序的缓存管理</span><span class="sxs-lookup"><span data-stu-id="8e4d3-141">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="8e4d3-142">缓存策略</span><span class="sxs-lookup"><span data-stu-id="8e4d3-142">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="8e4d3-143">基于位置的缓存策略</span><span class="sxs-lookup"><span data-stu-id="8e4d3-143">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="8e4d3-144">在网络应用程序中配置缓存</span><span class="sxs-lookup"><span data-stu-id="8e4d3-144">Configuring Caching in Network Applications</span></span>](configuring-caching-in-network-applications.md)
- [<span data-ttu-id="8e4d3-145">\<requestCaching> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="8e4d3-145">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
