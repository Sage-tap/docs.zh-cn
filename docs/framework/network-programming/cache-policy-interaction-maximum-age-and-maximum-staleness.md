---
description: 详细了解：缓存策略交互 — 最长使用期限和最长过期时间
title: 缓存策略交互 — 最长使用期限和最长过期时间
ms.date: 03/30/2017
helpviewer_keywords:
- maximum staleness
- freshness of cached resources
- time, cached resources
- maximum age policy
- staleness of cached resources
- age of cached resources
ms.assetid: 7f775925-89a1-4956-ba90-c869c1749a94
ms.openlocfilehash: 909a7203d4c9813c90dc0dea9bae7f8a1f7336cf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791655"
---
# <a name="cache-policy-interactionmaximum-age-and-maximum-staleness"></a><span data-ttu-id="41b3b-103">缓存策略交互 — 最长使用期限和最长过期时间</span><span class="sxs-lookup"><span data-stu-id="41b3b-103">Cache Policy Interaction—Maximum Age and Maximum Staleness</span></span>

<span data-ttu-id="41b3b-104">为了帮助确保将最新鲜的内容返回给客户端应用程序，客户端缓存策略和服务器重新验证要求的交互始终会造成最保守的缓存策略。</span><span class="sxs-lookup"><span data-stu-id="41b3b-104">To help ensure that the freshest content is returned to the client application, the interaction of client cache policy and server revalidation requirements always results in the most conservative cache policy.</span></span> <span data-ttu-id="41b3b-105">本主题中的所有示例阐明针对在 1 月 1 日缓存、1 月 4 日过期的资源的缓存策略。</span><span class="sxs-lookup"><span data-stu-id="41b3b-105">All the examples in this topic illustrate the cache policy for a resource that is cached on January 1 and expires on January 4.</span></span>  
  
 <span data-ttu-id="41b3b-106">在以下示例中，结合使用了最长过期时间值 (`maxStale`) 与最长使用时间 (`maxAge`)：</span><span class="sxs-lookup"><span data-stu-id="41b3b-106">In the following examples, the maximum staleness value (`maxStale`) is used in conjunction with a maximum age (`maxAge`):</span></span>  
  
- <span data-ttu-id="41b3b-107">如果缓存策略设置 `maxAge` = 5 天，且未指定 `maxStale` 值，根据 `maxAge` 值，此内容在 1 月 6 日前可用。</span><span class="sxs-lookup"><span data-stu-id="41b3b-107">If the cache policy sets `maxAge` = 5 days and does not specify a `maxStale` value, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="41b3b-108">但是，根据服务器的重新验证要求，内容会在 1 月 4 日过期。</span><span class="sxs-lookup"><span data-stu-id="41b3b-108">However, according to the server's revalidation requirements, the content expires on January 4.</span></span> <span data-ttu-id="41b3b-109">因为内容过期日期更保守（更早），所以它优先于 `maxAge` 策略。</span><span class="sxs-lookup"><span data-stu-id="41b3b-109">Because the content expiration date is more conservative (sooner), it takes precedence over the `maxAge` policy.</span></span> <span data-ttu-id="41b3b-110">因此，即使尚未达到最长使用时间，此内容在 1 月 4 日便会过期，并且必须进行重新验证。</span><span class="sxs-lookup"><span data-stu-id="41b3b-110">Therefore, the content expires on January 4 and must be revalidated even though its maximum age has not been reached.</span></span>  
  
- <span data-ttu-id="41b3b-111">如果缓存策略设置 `maxAge` = 5 天，`maxStale` = 3 天，根据 `maxAge` 值，此内容在 1 月 6 日前可用。</span><span class="sxs-lookup"><span data-stu-id="41b3b-111">If the cache policy sets `maxAge` = 5 days and `maxStale` = 3 days, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="41b3b-112">根据 `maxStale` 值，此内容在 1 月 7 日前可用。</span><span class="sxs-lookup"><span data-stu-id="41b3b-112">According to the `maxStale` value, the content is usable until January 7.</span></span> <span data-ttu-id="41b3b-113">因此，会在 1 月 6 日重新验证此内容。</span><span class="sxs-lookup"><span data-stu-id="41b3b-113">Therefore, the content gets revalidated on January 6.</span></span>  
  
- <span data-ttu-id="41b3b-114">如果缓存策略设置 `maxAge` = 5 天，`maxStale` = 1 天，根据 `maxAge` 值，此内容在 1 月 6 日前可用。</span><span class="sxs-lookup"><span data-stu-id="41b3b-114">If the cache policy sets `maxAge` = 5 days and `maxStale` = 1 day, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="41b3b-115">根据 `maxStale` 值，此内容在 1 月 5 日前可用。</span><span class="sxs-lookup"><span data-stu-id="41b3b-115">According to the `maxStale` value, the content is usable until January 5.</span></span> <span data-ttu-id="41b3b-116">因此，会在 1 月 5 日重新验证此内容。</span><span class="sxs-lookup"><span data-stu-id="41b3b-116">Therefore, the content gets revalidated on January 5.</span></span>  
  
 <span data-ttu-id="41b3b-117">当内容的最长使用时间小于过期日期时，更保守的缓存行为占据优先级，且最长过期时间值不会有任何效果。</span><span class="sxs-lookup"><span data-stu-id="41b3b-117">When the maximum age is less than the content expiration date, the more conservative caching behavior always prevails and the maximum staleness value has no effect.</span></span> <span data-ttu-id="41b3b-118">以下示例阐明了在内容过期之前到达最长使用时间 (`maxAge`) 时设置最长过期时间 (`maxStale`) 值的效果：</span><span class="sxs-lookup"><span data-stu-id="41b3b-118">The following examples illustrate the effect of setting a maximum staleness (`maxStale`) value when the maximum age (`maxAge`) is reached before the content expires:</span></span>  
  
- <span data-ttu-id="41b3b-119">如果缓存策略设置 `maxAge` = 1 天，且未指定 `maxStale` 值，即使内容尚未过期，也会在 1 月 2 日重新验证此内容。</span><span class="sxs-lookup"><span data-stu-id="41b3b-119">If the cache policy sets `maxAge` = 1 day and does not specify a value for `maxStale` value, the content is revalidated on January 2 even though it has not expired.</span></span>  
  
- <span data-ttu-id="41b3b-120">如果设缓存策略设置 `maxAge` = 1 天，`maxStale` = 3 天，会在 1 月 2 日重新验证此内容以强制实施更保守的策略设置。</span><span class="sxs-lookup"><span data-stu-id="41b3b-120">If the cache policy sets `maxAge` = 1 day and `maxStale` = 3 days, the content is revalidated on January 2 to enforce the more conservative policy setting.</span></span>  
  
- <span data-ttu-id="41b3b-121">如果缓存策略设置 `maxAge` = 1 天，`maxStale` = 1 天，会在 1 月 2 日重新验证此内容。</span><span class="sxs-lookup"><span data-stu-id="41b3b-121">If the cache policy sets `maxAge` = 1 day and `maxStale` = 1 day, the content is revalidated on January 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41b3b-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="41b3b-122">See also</span></span>

- [<span data-ttu-id="41b3b-123">网络应用程序的缓存管理</span><span class="sxs-lookup"><span data-stu-id="41b3b-123">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="41b3b-124">缓存策略</span><span class="sxs-lookup"><span data-stu-id="41b3b-124">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="41b3b-125">基于位置的缓存策略</span><span class="sxs-lookup"><span data-stu-id="41b3b-125">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="41b3b-126">基于时间的缓存策略</span><span class="sxs-lookup"><span data-stu-id="41b3b-126">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="41b3b-127">在网络应用程序中配置缓存</span><span class="sxs-lookup"><span data-stu-id="41b3b-127">Configuring Caching in Network Applications</span></span>](configuring-caching-in-network-applications.md)
- [<span data-ttu-id="41b3b-128">缓存策略交互 — 最长使用期限和最低新鲜度</span><span class="sxs-lookup"><span data-stu-id="41b3b-128">Cache Policy Interaction—Maximum Age and Minimum Freshness</span></span>](cache-policy-interaction-maximum-age-and-minimum-freshness.md)
