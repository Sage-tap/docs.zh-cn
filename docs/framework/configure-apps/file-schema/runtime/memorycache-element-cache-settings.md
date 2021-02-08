---
description: '了解详细信息： <memoryCache> 元素 (缓存设置) '
title: <memoryCache> 元素（缓存设置）
ms.date: 03/30/2017
helpviewer_keywords:
- <memoryCache> element
- caching [.NET Framework], configuration
- memoryCache element
ms.assetid: 182a622f-f7cf-472d-9d0b-451d2fd94525
ms.openlocfilehash: 1d46a156a222a0dc54e27cf56a5eb06cb1a908be
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782333"
---
# <a name="memorycache-element-cache-settings"></a><span data-ttu-id="66484-103">\<memoryCache> 元素（缓存设置）</span><span class="sxs-lookup"><span data-stu-id="66484-103">\<memoryCache> Element (Cache Settings)</span></span>

<span data-ttu-id="66484-104">定义一个用于配置基于 <xref:System.Runtime.Caching.MemoryCache> 类的缓存的元素。</span><span class="sxs-lookup"><span data-stu-id="66484-104">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="66484-105"><xref:System.Runtime.Caching.Configuration.MemoryCacheElement> 类定义可以用于配置缓存的 [memoryCache](memorycache-element-cache-settings.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="66484-105">The <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> class defines a [memoryCache](memorycache-element-cache-settings.md) element that you can use to configure the cache.</span></span> <span data-ttu-id="66484-106">可以在单个应用程序中使用 <xref:System.Runtime.Caching.MemoryCache> 类的多个实例。</span><span class="sxs-lookup"><span data-stu-id="66484-106">Multiple instances of the <xref:System.Runtime.Caching.MemoryCache> class can be used in a single application.</span></span> <span data-ttu-id="66484-107">配置文件中的每个 `memoryCache` 元素可以包含一个命名 <xref:System.Runtime.Caching.MemoryCache> 实例的设置。</span><span class="sxs-lookup"><span data-stu-id="66484-107">Each `memoryCache` element in the configuration file can contain settings for a named <xref:System.Runtime.Caching.MemoryCache> instance.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<memoryCache>**  
  
## <a name="syntax"></a><span data-ttu-id="66484-108">语法</span><span class="sxs-lookup"><span data-stu-id="66484-108">Syntax</span></span>  
  
```xml  
<memoryCache>
    <namedCaches>  
        <!-- child elements -->  
    </namedCaches>
</memoryCache>  
```  
  
## <a name="type"></a><span data-ttu-id="66484-109">类型</span><span class="sxs-lookup"><span data-stu-id="66484-109">Type</span></span>  

 <span data-ttu-id="66484-110"><xref:System.Runtime.Caching.MemoryCache> 类。</span><span class="sxs-lookup"><span data-stu-id="66484-110"><xref:System.Runtime.Caching.MemoryCache> class.</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="66484-111">特性和元素</span><span class="sxs-lookup"><span data-stu-id="66484-111">Attributes and Elements</span></span>  

 <span data-ttu-id="66484-112">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="66484-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="66484-113">特性</span><span class="sxs-lookup"><span data-stu-id="66484-113">Attributes</span></span>  
  
|<span data-ttu-id="66484-114">属性</span><span class="sxs-lookup"><span data-stu-id="66484-114">Attribute</span></span>|<span data-ttu-id="66484-115">说明</span><span class="sxs-lookup"><span data-stu-id="66484-115">Description</span></span>|  
|---------------|-----------------|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="66484-116"><xref:System.Runtime.Caching.MemoryCache> 对象的实例可以增长到的最大内存大小（以兆字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="66484-116">The maximum memory size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> object can grow to.</span></span> <span data-ttu-id="66484-117">默认值为 0，这意味着默认情况下使用 <xref:System.Runtime.Caching.MemoryCache> 类的自动调整大小启发。</span><span class="sxs-lookup"><span data-stu-id="66484-117">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosize heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="66484-118">缓存配置的名称。</span><span class="sxs-lookup"><span data-stu-id="66484-118">The name of the cache configuration.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="66484-119">缓存可以使用的物理内存的百分比。</span><span class="sxs-lookup"><span data-stu-id="66484-119">The percentage of physical memory that can be used by the cache.</span></span> <span data-ttu-id="66484-120">默认值为 0，这意味着默认情况下使用 <xref:System.Runtime.Caching.MemoryCache> 类的自动调整大小启发。</span><span class="sxs-lookup"><span data-stu-id="66484-120">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosize heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="66484-121">一个时间间隔的值，在该时间间隔之后，缓存实现会将当前内存负载与为缓存实例设置的基于绝对值和百分比的内存限制进行比较。</span><span class="sxs-lookup"><span data-stu-id="66484-121">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="66484-122">该值以“HH:MM:SS”格式输入。</span><span class="sxs-lookup"><span data-stu-id="66484-122">The value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="66484-123">子元素</span><span class="sxs-lookup"><span data-stu-id="66484-123">Child Elements</span></span>  
  
|<span data-ttu-id="66484-124">元素</span><span class="sxs-lookup"><span data-stu-id="66484-124">Element</span></span>|<span data-ttu-id="66484-125">说明</span><span class="sxs-lookup"><span data-stu-id="66484-125">Description</span></span>|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|<span data-ttu-id="66484-126">包含 `namedCache` 实例的配置设置的集合。</span><span class="sxs-lookup"><span data-stu-id="66484-126">Contains a collection of configuration settings for the `namedCache` instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="66484-127">父元素</span><span class="sxs-lookup"><span data-stu-id="66484-127">Parent Elements</span></span>  
  
|<span data-ttu-id="66484-128">元素</span><span class="sxs-lookup"><span data-stu-id="66484-128">Element</span></span>|<span data-ttu-id="66484-129">说明</span><span class="sxs-lookup"><span data-stu-id="66484-129">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="66484-130">指定公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="66484-130">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="66484-131">包含使你可以在 .NET Framework 中内置的应用程序中实现输出缓存的类型。</span><span class="sxs-lookup"><span data-stu-id="66484-131">Contains types that let you implement output caching in applications that are built into the .NET Framework.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="66484-132">备注</span><span class="sxs-lookup"><span data-stu-id="66484-132">Remarks</span></span>  

 <span data-ttu-id="66484-133"><xref:System.Runtime.Caching.MemoryCache> 类是抽象 <xref:System.Runtime.Caching.ObjectCache> 类的具体实现。</span><span class="sxs-lookup"><span data-stu-id="66484-133">The <xref:System.Runtime.Caching.MemoryCache> class is a concrete implementation of the abstract <xref:System.Runtime.Caching.ObjectCache> class.</span></span> <span data-ttu-id="66484-134"><xref:System.Runtime.Caching.MemoryCache> 类的实例可以随来自应用程序配置文件的配置信息一起提供。</span><span class="sxs-lookup"><span data-stu-id="66484-134">Instances of the <xref:System.Runtime.Caching.MemoryCache> class can be supplied with configuration information from application configuration files.</span></span> <span data-ttu-id="66484-135">[memoryCache](memorycache-element-cache-settings.md) 配置节包含 `namedCaches` 配置集合。</span><span class="sxs-lookup"><span data-stu-id="66484-135">The [memoryCache](memorycache-element-cache-settings.md) configuration section contains a `namedCaches` configuration collection.</span></span>  
  
 <span data-ttu-id="66484-136">基于内存的缓存对象进行初始化时，它首先尝试查找与传递给内存缓存构造函数的参数中的名称进行匹配的 `namedCaches` 项。</span><span class="sxs-lookup"><span data-stu-id="66484-136">When a memory-based cache object is initialized, it first tries to find a `namedCaches` entry that matches the name in the parameter that is passed to the memory cache constructor.</span></span> <span data-ttu-id="66484-137">如果找到 `namedCaches` 项，则从配置文件检索轮询和内存管理信息。</span><span class="sxs-lookup"><span data-stu-id="66484-137">If a `namedCaches` entry is found, the polling and memory-management information are retrieved from the configuration file.</span></span>  
  
 <span data-ttu-id="66484-138">初始化过程随后使用构造函数中配置信息的名称/值对的可选集合来确定是否重写了任何配置项。</span><span class="sxs-lookup"><span data-stu-id="66484-138">The initialization process then determines whether any configuration entries were overridden, by using the optional collection of name/value pairs of configuration information in the constructor.</span></span> <span data-ttu-id="66484-139">如果在名称/值对集合中传递以下值之一，则这些值会重写从配置文件获取的信息：</span><span class="sxs-lookup"><span data-stu-id="66484-139">If you pass any one of the following values in the name/value pair collection, these values override information obtained from the configuration file:</span></span>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.CacheMemoryLimitMegabytes%2A>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.PhysicalMemoryLimitPercentage%2A>  
  
- <xref:System.Runtime.Caching.MemoryCache.PollingInterval%2A>  
  
## <a name="example"></a><span data-ttu-id="66484-140">示例</span><span class="sxs-lookup"><span data-stu-id="66484-140">Example</span></span>  

 <span data-ttu-id="66484-141">下面的示例演示如何 <xref:System.Runtime.Caching.MemoryCache> 通过将 `name` 属性设置为 "default"，将对象的名称设置为默认缓存对象名称。</span><span class="sxs-lookup"><span data-stu-id="66484-141">The following example shows how to set the name of the <xref:System.Runtime.Caching.MemoryCache> object to the default cache object name by setting the `name` attribute to "Default".</span></span>  
  
 <span data-ttu-id="66484-142">将 `cacheMemoryLimitMegabytes` 属性和 `physicalMemoryLimitPercentage` 属性设置为零。</span><span class="sxs-lookup"><span data-stu-id="66484-142">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryLimitPercentage` attribute are set to zero.</span></span> <span data-ttu-id="66484-143">将这些特性设置为零意味着默认情况下使用 <xref:System.Runtime.Caching.MemoryCache> 自动调整大小试探法。</span><span class="sxs-lookup"><span data-stu-id="66484-143">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="66484-144">每隔两分钟，缓存实现应对当前内存负载和基于百分比的绝对内存限制进行比较。</span><span class="sxs-lookup"><span data-stu-id="66484-144">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
```xml  
<configuration>  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="Default"
               cacheMemoryLimitMegabytes="0"
               physicalMemoryLimitPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="66484-145">请参阅</span><span class="sxs-lookup"><span data-stu-id="66484-145">See also</span></span>

- <xref:System.Runtime.Caching.MemoryCache>
- [<span data-ttu-id="66484-146">\<system.runtime.caching> 元素 (缓存设置) </span><span class="sxs-lookup"><span data-stu-id="66484-146">\<system.runtime.caching> Element (Cache Settings)</span></span>](system-runtime-caching-element-cache-settings.md)
- [<span data-ttu-id="66484-147">\<namedCaches> 元素 (缓存设置) </span><span class="sxs-lookup"><span data-stu-id="66484-147">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
