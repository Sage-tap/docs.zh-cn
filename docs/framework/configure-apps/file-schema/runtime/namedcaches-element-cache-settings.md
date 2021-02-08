---
description: '了解详细信息： <namedCaches> 元素 (缓存设置) '
title: <namedCaches> 元素（缓存设置）
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
ms.openlocfilehash: 543650513270c0cee24d965b8efe98a75d7b8f9a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782320"
---
# <a name="namedcaches-element-cache-settings"></a><span data-ttu-id="35d44-103">\<namedCaches> 元素（缓存设置）</span><span class="sxs-lookup"><span data-stu-id="35d44-103">\<namedCaches> Element (Cache Settings)</span></span>

<span data-ttu-id="35d44-104">指定命名实例的配置设置的集合 <xref:System.Runtime.Caching.MemoryCache> 。</span><span class="sxs-lookup"><span data-stu-id="35d44-104">Specifies a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span> <span data-ttu-id="35d44-105"><xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A>属性从配置文件的一个或多个元素中引用配置设置的集合 `namedCaches` 。</span><span class="sxs-lookup"><span data-stu-id="35d44-105">The <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> property references the collection of configuration settings from one or more `namedCaches` elements of the configuration file.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedCaches>**  
  
## <a name="syntax"></a><span data-ttu-id="35d44-106">语法</span><span class="sxs-lookup"><span data-stu-id="35d44-106">Syntax</span></span>  
  
```xml  
<namedCaches>  
  <add name="default"/>
</namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="35d44-107">类型</span><span class="sxs-lookup"><span data-stu-id="35d44-107">Type</span></span>  

 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="35d44-108">特性和元素</span><span class="sxs-lookup"><span data-stu-id="35d44-108">Attributes and Elements</span></span>  

 <span data-ttu-id="35d44-109">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="35d44-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="35d44-110">特性</span><span class="sxs-lookup"><span data-stu-id="35d44-110">Attributes</span></span>  
  
|<span data-ttu-id="35d44-111">属性</span><span class="sxs-lookup"><span data-stu-id="35d44-111">Attribute</span></span>|<span data-ttu-id="35d44-112">说明</span><span class="sxs-lookup"><span data-stu-id="35d44-112">Description</span></span>|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|<span data-ttu-id="35d44-113">一个整数值，指定的实例可以增长到的最大允许大小（以 mb <xref:System.Runtime.Caching.MemoryCache> 为单位）。</span><span class="sxs-lookup"><span data-stu-id="35d44-113">An integer value that specifies the maximum allowable size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="35d44-114">默认值为0，这意味着 <xref:System.Runtime.Caching.MemoryCache> 默认情况下使用类的自动调整试探法。</span><span class="sxs-lookup"><span data-stu-id="35d44-114">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`name`|<span data-ttu-id="35d44-115">缓存的名称。</span><span class="sxs-lookup"><span data-stu-id="35d44-115">The name of the cache.</span></span>|  
|`physicalMemoryLimitPercentage`|<span data-ttu-id="35d44-116">一个介于0到100之间的整数值，用于指定缓存可使用的实际安装计算机内存的最大百分比。</span><span class="sxs-lookup"><span data-stu-id="35d44-116">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="35d44-117">默认值为0，这意味着 <xref:System.Runtime.Caching.MemoryCache> 默认情况下使用类的自动调整试探法。</span><span class="sxs-lookup"><span data-stu-id="35d44-117">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`pollingInterval`|<span data-ttu-id="35d44-118">一个时间间隔的值，在该时间间隔之后，缓存实现会将当前内存负载与为缓存实例设置的基于绝对值和百分比的内存限制进行比较。</span><span class="sxs-lookup"><span data-stu-id="35d44-118">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="35d44-119">此值以 "HH： MM： SS" 格式输入。</span><span class="sxs-lookup"><span data-stu-id="35d44-119">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="35d44-120">子元素</span><span class="sxs-lookup"><span data-stu-id="35d44-120">Child Elements</span></span>  
  
|<span data-ttu-id="35d44-121">元素</span><span class="sxs-lookup"><span data-stu-id="35d44-121">Element</span></span>|<span data-ttu-id="35d44-122">说明</span><span class="sxs-lookup"><span data-stu-id="35d44-122">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-namedcaches.md)|<span data-ttu-id="35d44-123">向内存缓存的 `namedCaches` 集合添加一个命名的缓存。</span><span class="sxs-lookup"><span data-stu-id="35d44-123">Adds a named cache to the `namedCaches` collection for a memory cache.</span></span>|  
|[\<clear>](clear-element-for-namedcaches.md)|<span data-ttu-id="35d44-124">清除内存缓存的 `namedCaches` 集合。</span><span class="sxs-lookup"><span data-stu-id="35d44-124">Clears the `namedCaches` collection for a memory cache.</span></span>|  
|[\<remove>](remove-element-for-namedcaches.md)|<span data-ttu-id="35d44-125">从内存缓存的 `namedCaches` 集合中删除一个命名的缓存条目。</span><span class="sxs-lookup"><span data-stu-id="35d44-125">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="35d44-126">父元素</span><span class="sxs-lookup"><span data-stu-id="35d44-126">Parent Elements</span></span>  
  
|<span data-ttu-id="35d44-127">元素</span><span class="sxs-lookup"><span data-stu-id="35d44-127">Element</span></span>|<span data-ttu-id="35d44-128">说明</span><span class="sxs-lookup"><span data-stu-id="35d44-128">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="35d44-129">指定公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="35d44-129">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[\<memoryCache>](memorycache-element-cache-settings.md)|<span data-ttu-id="35d44-130">定义一个用于配置基于 <xref:System.Runtime.Caching.MemoryCache> 类的缓存的元素。</span><span class="sxs-lookup"><span data-stu-id="35d44-130">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="35d44-131">包含使你可以在 .NET Framework 中内置的应用程序中实现输出缓存的类型。</span><span class="sxs-lookup"><span data-stu-id="35d44-131">Contains types that let you implement output caching in applications that are built into the .NET Framework.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35d44-132">备注</span><span class="sxs-lookup"><span data-stu-id="35d44-132">Remarks</span></span>  

 <span data-ttu-id="35d44-133">Web.config 文件的内存缓存配置部分可以包含 `add` `remove` 该集合的、和 `clear` 属性 `namedCaches` 。</span><span class="sxs-lookup"><span data-stu-id="35d44-133">The memory cache configuration section of the Web.config file can contain `add`, `remove`, and `clear` attributes for the `namedCaches` collection.</span></span> <span data-ttu-id="35d44-134">每个 `namedCaches` 项都由特性唯一标识 `name` 。</span><span class="sxs-lookup"><span data-stu-id="35d44-134">Each `namedCaches` entry is uniquely identified by the `name` attribute.</span></span>  
  
 <span data-ttu-id="35d44-135">可以通过引用应用程序配置文件中的信息来检索内存缓存项的实例。</span><span class="sxs-lookup"><span data-stu-id="35d44-135">You can retrieve instances of memory cache entries by referencing the information in the application configuration files.</span></span> <span data-ttu-id="35d44-136">默认情况下，只有默认的缓存实例在配置文件中有一个条目。</span><span class="sxs-lookup"><span data-stu-id="35d44-136">By default, only the default cache instance has an entry in the configuration file.</span></span> <span data-ttu-id="35d44-137">默认缓存实例是从属性返回的实例 <xref:System.Runtime.Caching.MemoryCache.Default%2A> 。</span><span class="sxs-lookup"><span data-stu-id="35d44-137">The default cache instance is the instance that is returned from the <xref:System.Runtime.Caching.MemoryCache.Default%2A> property.</span></span>  
  
 <span data-ttu-id="35d44-138">如果将 name 属性设置为 "default"，则元素将使用默认内存缓存实例。</span><span class="sxs-lookup"><span data-stu-id="35d44-138">If you set the name attribute to "default", the element uses the default memory cache instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35d44-139">示例</span><span class="sxs-lookup"><span data-stu-id="35d44-139">Example</span></span>  

 <span data-ttu-id="35d44-140">下面的示例演示如何通过将 `name` 属性设置为 "default"，将缓存的名称设置为默认缓存项名称。</span><span class="sxs-lookup"><span data-stu-id="35d44-140">The following example shows how to set the name of the cache to the default cache entry name by setting the `name` attribute to "default".</span></span>  
  
 <span data-ttu-id="35d44-141">将 `cacheMemoryLimitMegabytes` 属性和 `physicalMemoryPercentage` 属性设置为零。</span><span class="sxs-lookup"><span data-stu-id="35d44-141">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="35d44-142">将这些特性设置为零意味着使用类的自动调整试探法 <xref:System.Runtime.Caching.MemoryCache> 。</span><span class="sxs-lookup"><span data-stu-id="35d44-142">Setting these attributes to zero means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used.</span></span> <span data-ttu-id="35d44-143">缓存实现将当前内存负载与基于百分比的绝对内存和每两分钟的内存限制进行比较。</span><span class="sxs-lookup"><span data-stu-id="35d44-143">The cache implementation compares the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
```xml  
<configuration>  
  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="default"
               cacheMemoryLimitMegabytes="0"
               physicalMemoryLimitPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="35d44-144">请参阅</span><span class="sxs-lookup"><span data-stu-id="35d44-144">See also</span></span>

- [<span data-ttu-id="35d44-145">\<memoryCache> 元素 (缓存设置) </span><span class="sxs-lookup"><span data-stu-id="35d44-145">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
