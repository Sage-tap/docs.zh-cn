---
description: 了解详细信息： <forcePerformanceCounterUniqueSharedMemoryReads> 元素
title: <forcePerformanceCounterUniqueSharedMemoryReads> 元素
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
ms.openlocfilehash: 63fe695cc993faa851a9ea3196294397d2992c45
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787027"
---
# <a name="forceperformancecounteruniquesharedmemoryreads-element"></a><span data-ttu-id="87c11-103">\<forcePerformanceCounterUniqueSharedMemoryReads> 元素</span><span class="sxs-lookup"><span data-stu-id="87c11-103">\<forcePerformanceCounterUniqueSharedMemoryReads> Element</span></span>

<span data-ttu-id="87c11-104">指定 PerfCounter.dll 是否使用 .NET Framework 版本 1.1 应用程序中的 CategoryOptions 注册表设置，以确定是否加载来自特定于类别的共享内存或全局内存的性能计数器数据。</span><span class="sxs-lookup"><span data-stu-id="87c11-104">Specifies whether PerfCounter.dll uses the CategoryOptions registry setting in a .NET Framework version 1.1 application to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<forcePerformanceCounterUniqueSharedMemoryReads>**  
  
## <a name="syntax"></a><span data-ttu-id="87c11-105">语法</span><span class="sxs-lookup"><span data-stu-id="87c11-105">Syntax</span></span>  
  
```xml  
<forcePerformanceCounterUniqueSharedMemoryReads
enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="87c11-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="87c11-106">Attributes and Elements</span></span>  

 <span data-ttu-id="87c11-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="87c11-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="87c11-108">特性</span><span class="sxs-lookup"><span data-stu-id="87c11-108">Attributes</span></span>  
  
|<span data-ttu-id="87c11-109">属性</span><span class="sxs-lookup"><span data-stu-id="87c11-109">Attribute</span></span>|<span data-ttu-id="87c11-110">描述</span><span class="sxs-lookup"><span data-stu-id="87c11-110">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="87c11-111">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="87c11-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="87c11-112">指示 PerfCounter.dll 是否使用 CategoryOptions 注册表设置来确定是否从特定于类别的共享内存或全局内存加载性能计数器数据。</span><span class="sxs-lookup"><span data-stu-id="87c11-112">Indicates whether PerfCounter.dll uses the CategoryOptions registry setting to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="87c11-113">enabled 特性</span><span class="sxs-lookup"><span data-stu-id="87c11-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="87c11-114">值</span><span class="sxs-lookup"><span data-stu-id="87c11-114">Value</span></span>|<span data-ttu-id="87c11-115">说明</span><span class="sxs-lookup"><span data-stu-id="87c11-115">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="87c11-116">PerfCounter.dll 不使用 CategoryOptions 注册表设置，这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="87c11-116">PerfCounter.dll does not use the CategoryOptions registry setting This is the default.</span></span>|  
|`true`|<span data-ttu-id="87c11-117">PerfCounter.dll 使用 CategoryOptions 注册表设置。</span><span class="sxs-lookup"><span data-stu-id="87c11-117">PerfCounter.dll does use the CategoryOptions registry setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="87c11-118">子元素</span><span class="sxs-lookup"><span data-stu-id="87c11-118">Child Elements</span></span>  

 <span data-ttu-id="87c11-119">无。</span><span class="sxs-lookup"><span data-stu-id="87c11-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="87c11-120">父元素</span><span class="sxs-lookup"><span data-stu-id="87c11-120">Parent Elements</span></span>  
  
|<span data-ttu-id="87c11-121">元素</span><span class="sxs-lookup"><span data-stu-id="87c11-121">Element</span></span>|<span data-ttu-id="87c11-122">说明</span><span class="sxs-lookup"><span data-stu-id="87c11-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="87c11-123">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="87c11-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="87c11-124">包含有关程序集绑定和垃圾回收的信息。</span><span class="sxs-lookup"><span data-stu-id="87c11-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87c11-125">备注</span><span class="sxs-lookup"><span data-stu-id="87c11-125">Remarks</span></span>  

 <span data-ttu-id="87c11-126">在 .NET Framework 4 之前的 .NET Framework 版本中，已加载到进程中加载的运行时的 PerfCounter.dll 版本对应。</span><span class="sxs-lookup"><span data-stu-id="87c11-126">In versions of the .NET Framework before the .NET Framework 4, the version of PerfCounter.dll that was loaded corresponded to the runtime that was loaded in the process.</span></span> <span data-ttu-id="87c11-127">如果计算机已安装 .NET Framework 版本1.1 和 .NET Framework 2.0，.NET Framework 1.1 应用程序会加载 PerfCounter.dll 的 .NET Framework 1.1 版本。</span><span class="sxs-lookup"><span data-stu-id="87c11-127">If a computer had both the .NET Framework version 1.1 and the .NET Framework 2.0 installed, a .NET Framework 1.1 application would load the .NET Framework 1.1 version of PerfCounter.dll.</span></span> <span data-ttu-id="87c11-128">从 .NET Framework 4 开始，将加载 PerfCounter.dll 的最新安装版本。</span><span class="sxs-lookup"><span data-stu-id="87c11-128">Starting with the .NET Framework 4, the newest installed version of PerfCounter.dll is loaded.</span></span> <span data-ttu-id="87c11-129">这意味着，如果计算机上安装了 .NET Framework 4 版本，.NET Framework 1.1 应用程序将加载 PerfCounter.dll 的 .NET Framework 4 版本。</span><span class="sxs-lookup"><span data-stu-id="87c11-129">This means that a .NET Framework 1.1 application will load the .NET Framework 4 version of PerfCounter.dll if the .NET Framework 4 is installed on the computer.</span></span>  
  
 <span data-ttu-id="87c11-130">从 .NET Framework 4 开始，使用性能计数器时，PerfCounter.dll 检查每个提供程序的 CategoryOptions 注册表项，以确定是否应从特定于类别的共享内存或全局共享内存中读取。</span><span class="sxs-lookup"><span data-stu-id="87c11-130">Starting with the .NET Framework 4, when consuming performance counters, PerfCounter.dll checks the CategoryOptions registry entry for each provider to determine whether it should read from category-specific shared memory or global shared memory.</span></span> <span data-ttu-id="87c11-131">.NET Framework 1.1 PerfCounter.dll 未读取该注册表项，因为它不知道特定于类别的共享内存;它始终从全局共享内存进行读取。</span><span class="sxs-lookup"><span data-stu-id="87c11-131">The .NET Framework 1.1 PerfCounter.dll does not read that registry entry, because it is not aware of category-specific shared memory; it always reads from global shared memory.</span></span>  
  
 <span data-ttu-id="87c11-132">为了向后兼容，.NET Framework 4 PerfCounter.dll 在 .NET Framework 1.1 应用程序中运行时，不会检查 CategoryOptions 注册表项。</span><span class="sxs-lookup"><span data-stu-id="87c11-132">For backward compatibility, the .NET Framework 4 PerfCounter.dll does not check the CategoryOptions registry entry when running in a .NET Framework 1.1 application.</span></span> <span data-ttu-id="87c11-133">它只使用全局共享内存，就像 .NET Framework 1.1 PerfCounter.dll 一样。</span><span class="sxs-lookup"><span data-stu-id="87c11-133">It simply uses global shared memory, just like the .NET Framework 1.1 PerfCounter.dll.</span></span> <span data-ttu-id="87c11-134">不过，你可以通过启用元素指示 .NET Framework 4 PerfCounter.dll 检查注册表设置 `<forcePerformanceCounterUniqueSharedMemoryReads>` 。</span><span class="sxs-lookup"><span data-stu-id="87c11-134">However, you can instruct the .NET Framework 4 PerfCounter.dll to check the registry setting by enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="87c11-135">启用 `<forcePerformanceCounterUniqueSharedMemoryReads>` 元素并不保证将使用特定于类别的共享内存。</span><span class="sxs-lookup"><span data-stu-id="87c11-135">Enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element does not guarantee that category-specific shared memory will be used.</span></span> <span data-ttu-id="87c11-136">设置为 `true` 仅导致 PerfCounter.dll 引用 CategoryOptions 注册表设置。</span><span class="sxs-lookup"><span data-stu-id="87c11-136">Setting enabled to `true` only causes PerfCounter.dll to reference the CategoryOptions registry setting.</span></span> <span data-ttu-id="87c11-137">CategoryOptions 的默认设置是使用特定于类别的共享内存;但是，您可以更改 CategoryOptions 以指示应使用全局共享内存。</span><span class="sxs-lookup"><span data-stu-id="87c11-137">The default setting for CategoryOptions is to use category-specific shared memory; however, you can change CategoryOptions to indicate that global shared memory should be used.</span></span>  
  
 <span data-ttu-id="87c11-138">包含 CategoryOptions 设置的注册表项是 HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\<类别名称 \> \Performance。</span><span class="sxs-lookup"><span data-stu-id="87c11-138">The registry key that contains the CategoryOptions setting is HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\<categoryName\>\Performance.</span></span> <span data-ttu-id="87c11-139">默认情况下，CategoryOptions 设置为3，指示 PerfCounter.dll 使用特定于类别的共享内存。</span><span class="sxs-lookup"><span data-stu-id="87c11-139">By default, CategoryOptions is set to 3, which instructs PerfCounter.dll to use category-specific shared memory.</span></span> <span data-ttu-id="87c11-140">如果将 CategoryOptions 设置为0，则 PerfCounter.dll 使用全局共享内存。</span><span class="sxs-lookup"><span data-stu-id="87c11-140">If CategoryOptions is set to 0, PerfCounter.dll uses global shared memory.</span></span> <span data-ttu-id="87c11-141">仅当正在创建的实例的名称与重复使用的实例相同时，才会重新使用实例数据。</span><span class="sxs-lookup"><span data-stu-id="87c11-141">Instance data will be reused only if the name of the instance being created is identical to the instance being reused.</span></span> <span data-ttu-id="87c11-142">所有版本都可以写入该类别。</span><span class="sxs-lookup"><span data-stu-id="87c11-142">All versions will be able to write to the category.</span></span> <span data-ttu-id="87c11-143">如果 CategoryOptions 设置为1，则使用全局共享内存，但如果类别名称与要重用的类别的长度相同，则可以重用实例数据。</span><span class="sxs-lookup"><span data-stu-id="87c11-143">If CategoryOptions is set to 1, global shared memory is used, but instance data can be reused if the category name is the same length as the category being reused.</span></span>  
  
 <span data-ttu-id="87c11-144">设置0和1可能会导致内存泄漏和填充性能计数器内存。</span><span class="sxs-lookup"><span data-stu-id="87c11-144">The settings 0 and 1 can lead to memory leaks and the filling up of performance counter memory.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87c11-145">示例</span><span class="sxs-lookup"><span data-stu-id="87c11-145">Example</span></span>  

 <span data-ttu-id="87c11-146">下面的示例演示如何指定 PerfCounter.dll 应引用 CategoryOptions 注册表项，以确定它是否应使用特定于类别的共享内存。</span><span class="sxs-lookup"><span data-stu-id="87c11-146">The following example shows how to specify that PerfCounter.dll should reference the CategoryOptions registry entry to determine whether it should use category-specific shared memory.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="87c11-147">请参阅</span><span class="sxs-lookup"><span data-stu-id="87c11-147">See also</span></span>

- [<span data-ttu-id="87c11-148">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="87c11-148">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="87c11-149">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="87c11-149">Configuration File Schema</span></span>](../index.md)
