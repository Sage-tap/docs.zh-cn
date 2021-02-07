---
description: '了解详细信息： <defaultFtpCachePolicy> 元素 (网络设置) '
title: <defaultFtpCachePolicy> 元素（网络设置）
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultFtpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultFtpCachePolicy
helpviewer_keywords:
- <defaultFtpCachePolicy> element
- defaultFtpCachePolicy element
ms.assetid: 0eb0c5cb-dd97-484d-8614-785e88877abb
ms.openlocfilehash: 77150ce0980e96dd949df4b5ad7e4557ed1b991a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740361"
---
# <a name="defaultftpcachepolicy-element-network-settings"></a><span data-ttu-id="679ea-103">\<defaultFtpCachePolicy> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="679ea-103">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>

<span data-ttu-id="679ea-104">介绍 FTP 缓存是否处于活动状态，并描述默认缓存策略。</span><span class="sxs-lookup"><span data-stu-id="679ea-104">Describes whether FTP caching is active and describes the default caching policy.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<requestCaching>**](requestcaching-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultFtpCachePolicy>**

## <a name="syntax"></a><span data-ttu-id="679ea-105">语法</span><span class="sxs-lookup"><span data-stu-id="679ea-105">Syntax</span></span>  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="679ea-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="679ea-106">Attributes and Elements</span></span>  

 <span data-ttu-id="679ea-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="679ea-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="679ea-108">特性</span><span class="sxs-lookup"><span data-stu-id="679ea-108">Attributes</span></span>  
  
|<span data-ttu-id="679ea-109">属性</span><span class="sxs-lookup"><span data-stu-id="679ea-109">Attribute</span></span>|<span data-ttu-id="679ea-110">说明</span><span class="sxs-lookup"><span data-stu-id="679ea-110">Description</span></span>|  
|---------------|-----------------|  
|`policyLevel`|<span data-ttu-id="679ea-111">指定 FTP 缓存策略。</span><span class="sxs-lookup"><span data-stu-id="679ea-111">Specifies the FTP caching policy.</span></span> <span data-ttu-id="679ea-112">默认值是 `Default`。</span><span class="sxs-lookup"><span data-stu-id="679ea-112">The default value is `Default`.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="679ea-113">policyLevel 特性</span><span class="sxs-lookup"><span data-stu-id="679ea-113">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="679ea-114">值</span><span class="sxs-lookup"><span data-stu-id="679ea-114">Value</span></span>|<span data-ttu-id="679ea-115">说明</span><span class="sxs-lookup"><span data-stu-id="679ea-115">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="679ea-116">如果资源是最新的，则返回缓存的资源，内容长度准确，并且存在过期、修改和内容长度属性。</span><span class="sxs-lookup"><span data-stu-id="679ea-116">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="679ea-117">从服务器返回资源。</span><span class="sxs-lookup"><span data-stu-id="679ea-117">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="679ea-118">如果内容长度存在并且与条目大小匹配，则返回缓存的资源。</span><span class="sxs-lookup"><span data-stu-id="679ea-118">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="679ea-119">如果提供了内容长度并与条目大小匹配，则返回缓存的资源;否则，将从服务器下载资源，并将其返回给调用方。</span><span class="sxs-lookup"><span data-stu-id="679ea-119">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="679ea-120">如果缓存资源的时间戳与服务器上资源的时间戳相同，则返回缓存的资源;否则，将从服务器下载资源，并将其存储在缓存中，并将其返回给调用方。</span><span class="sxs-lookup"><span data-stu-id="679ea-120">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="679ea-121">从服务器下载资源，将其存储在缓存中，并将资源返回给调用方。</span><span class="sxs-lookup"><span data-stu-id="679ea-121">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="679ea-122">如果缓存的资源存在，则将其删除。</span><span class="sxs-lookup"><span data-stu-id="679ea-122">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="679ea-123">从服务器下载资源，并将其返回给调用方。</span><span class="sxs-lookup"><span data-stu-id="679ea-123">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="679ea-124">如果时间戳与服务器上的资源的时间戳相同，则使用资源的缓存副本满足请求；否则从服务器下载资源，将资源展示给调用方，然后再存储在缓存中。</span><span class="sxs-lookup"><span data-stu-id="679ea-124">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and stored in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="679ea-125">子元素</span><span class="sxs-lookup"><span data-stu-id="679ea-125">Child Elements</span></span>  

 <span data-ttu-id="679ea-126">无。</span><span class="sxs-lookup"><span data-stu-id="679ea-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="679ea-127">父元素</span><span class="sxs-lookup"><span data-stu-id="679ea-127">Parent Elements</span></span>  
  
|<span data-ttu-id="679ea-128">元素</span><span class="sxs-lookup"><span data-stu-id="679ea-128">Element</span></span>|<span data-ttu-id="679ea-129">说明</span><span class="sxs-lookup"><span data-stu-id="679ea-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="679ea-130">requestCaching</span><span class="sxs-lookup"><span data-stu-id="679ea-130">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="679ea-131">控制网络请求的缓存机制。</span><span class="sxs-lookup"><span data-stu-id="679ea-131">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="679ea-132">备注</span><span class="sxs-lookup"><span data-stu-id="679ea-132">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="679ea-133">示例</span><span class="sxs-lookup"><span data-stu-id="679ea-133">Example</span></span>  

 <span data-ttu-id="679ea-134">下面的示例演示如何指定的 FTP 缓存策略 `NoCacheNoStore` 。</span><span class="sxs-lookup"><span data-stu-id="679ea-134">The following example shows how to specify an FTP caching policy of `NoCacheNoStore`.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching>  
      <defaultFtpCachePolicy  
        policyLevel="NoCacheNoStore">  
      </defaultFtpCachePolicy>  
    </requestCaching>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="679ea-135">请参阅</span><span class="sxs-lookup"><span data-stu-id="679ea-135">See also</span></span>

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [<span data-ttu-id="679ea-136">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="679ea-136">Network Settings Schema</span></span>](index.md)
