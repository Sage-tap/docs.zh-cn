---
description: 了解详细信息：跟踪和调试设置架构
title: 跟踪和调试设置架构
ms.date: 03/30/2017
helpviewer_keywords:
- tracing [.NET Framework], trace and debug settings schema
- configuration schema [.NET Framework], trace and debug settings
- configuration settings [.NET Framework], tracing
- schema configuration settings
- configuration settings [.NET Framework], debugging
- trace listeners, trace and debug settings schema
- configuration sections [.NET Framework]
- elements [.NET Framework], trace and debug settings
ms.assetid: 277ca5f6-e1c4-41b6-a47f-3a67ce5b94ac
ms.openlocfilehash: 2429585c44952d2ee12547dab8f51662295bf02f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639645"
---
# <a name="trace-and-debug-settings-schema"></a><span data-ttu-id="5d01b-103">跟踪和调试设置架构</span><span class="sxs-lookup"><span data-stu-id="5d01b-103">Trace and Debug Settings Schema</span></span>

<span data-ttu-id="5d01b-104">跟踪和调试设置指定用于收集、存储和路由消息的跟踪侦听器以及对跟踪开关设置的级别。</span><span class="sxs-lookup"><span data-stu-id="5d01b-104">Trace and debug settings specify trace listeners that collect, store, and route messages, and the level where a trace switch is set.</span></span>  
  
 <span data-ttu-id="5d01b-105">下表介绍每个跟踪和调试设置元素的功能。</span><span class="sxs-lookup"><span data-stu-id="5d01b-105">The following table describes the function of each trace and debug settings element.</span></span>  
  
|<span data-ttu-id="5d01b-106">元素</span><span class="sxs-lookup"><span data-stu-id="5d01b-106">Element</span></span>|<span data-ttu-id="5d01b-107">说明</span><span class="sxs-lookup"><span data-stu-id="5d01b-107">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-listeners-for-source.md)|<span data-ttu-id="5d01b-108">将侦听器添加到跟踪源的 `Listeners` 集合中。</span><span class="sxs-lookup"><span data-stu-id="5d01b-108">Adds a listener to the `Listeners` collection for a trace source.</span></span>|  
|[\<add>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="5d01b-109">将侦听器添加到 `Listeners` 集合中。</span><span class="sxs-lookup"><span data-stu-id="5d01b-109">Adds a listener to the `Listeners` collection.</span></span>|  
|[\<add>](add-element-for-sharedlisteners.md)|<span data-ttu-id="5d01b-110">将侦听器添加到 `sharedListeners` 集合中。</span><span class="sxs-lookup"><span data-stu-id="5d01b-110">Adds a listener to the `sharedListeners` collection.</span></span>|  
|[\<add>](add-element-for-switches.md)|<span data-ttu-id="5d01b-111">指定对跟踪开关设置的级别。</span><span class="sxs-lookup"><span data-stu-id="5d01b-111">Specifies the level where a trace switch is set.</span></span>|  
|[\<assert>](assert-element.md)|<span data-ttu-id="5d01b-112">指定调用 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> 方法时是否显示消息框；另外指定要写入消息的文件的名称。</span><span class="sxs-lookup"><span data-stu-id="5d01b-112">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>|  
|[\<clear>](clear-element-for-listeners-for-source.md)|<span data-ttu-id="5d01b-113">清除跟踪源的 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="5d01b-113">Clears the `Listeners` collection for a trace source.</span></span>|  
|[\<clear>](clear-element-for-listeners-for-trace.md)|<span data-ttu-id="5d01b-114">清除跟踪的 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="5d01b-114">Clears the `Listeners` collection for trace.</span></span>|  
|[\<filter>](filter-element-for-add-for-listeners-for-source.md)|<span data-ttu-id="5d01b-115">将筛选器添加到跟踪源的 `Listeners` 集合中的侦听器。</span><span class="sxs-lookup"><span data-stu-id="5d01b-115">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>|  
|[\<filter>](filter-element-for-add-for-listeners-for-trace.md)|<span data-ttu-id="5d01b-116">将筛选器添加到跟踪的 `Listeners` 集合中的侦听器。</span><span class="sxs-lookup"><span data-stu-id="5d01b-116">Adds a filter to a listener in the `Listeners` collection for trace.</span></span>|  
|[\<filter>](filter-element-for-add-for-sharedlisteners.md)|<span data-ttu-id="5d01b-117">将筛选器添加到 `sharedListeners` 集合中的侦听器。</span><span class="sxs-lookup"><span data-stu-id="5d01b-117">Adds a filter to a listener in the `sharedListeners` collection.</span></span>|  
|[\<listeners>](listeners-element-for-source.md)|<span data-ttu-id="5d01b-118">指定跟踪源的 `Listeners` 集合中的侦听器。</span><span class="sxs-lookup"><span data-stu-id="5d01b-118">Specifies listeners for the `Listeners` collection for a trace source.</span></span>|  
|[\<listeners>](listeners-element-for-trace.md)|<span data-ttu-id="5d01b-119">指定跟踪的 `Listeners` 集合中的侦听器。</span><span class="sxs-lookup"><span data-stu-id="5d01b-119">Specifies listeners for the `Listeners` collection for trace.</span></span>|  
|[\<performanceCounters>](performancecounters-element.md)|<span data-ttu-id="5d01b-120">指定由性能计数器共享的全局内存的大小。</span><span class="sxs-lookup"><span data-stu-id="5d01b-120">Specifies the size of the global memory shared by performance counters.</span></span>|  
|[\<remove>](remove-element-for-listeners-for-trace.md)|<span data-ttu-id="5d01b-121">从跟踪的 `Listeners` 集合中删除侦听器。</span><span class="sxs-lookup"><span data-stu-id="5d01b-121">Removes a listener from the `Listeners` collection for trace.</span></span>|  
|[\<remove>](remove-element-for-listeners-for-source.md)|<span data-ttu-id="5d01b-122">从跟踪源的 `Listeners` 集合中删除侦听器。</span><span class="sxs-lookup"><span data-stu-id="5d01b-122">Removes a listener from the `Listeners` collection for a trace source.</span></span>|  
|[\<sharedListeners>](sharedlisteners-element.md)|<span data-ttu-id="5d01b-123">包含任何源或跟踪元素可以引用的侦听器。</span><span class="sxs-lookup"><span data-stu-id="5d01b-123">Contains listeners that any source or trace element can reference.</span></span>|  
|[\<sources>](sources-element.md)|<span data-ttu-id="5d01b-124">包含用于启动跟踪消息的跟踪源。</span><span class="sxs-lookup"><span data-stu-id="5d01b-124">Contains trace sources that initiate tracing messages.</span></span>|  
|[\<source>](source-element.md)|<span data-ttu-id="5d01b-125">指定用于启动跟踪消息的跟踪源。</span><span class="sxs-lookup"><span data-stu-id="5d01b-125">Specifies a trace source that initiates tracing messages.</span></span>|  
|[\<switches>](switches-element.md)|<span data-ttu-id="5d01b-126">包含跟踪开关和对该跟踪开关设置的级别。</span><span class="sxs-lookup"><span data-stu-id="5d01b-126">Contains trace switches and the level where the trace switches are set.</span></span>|  
|[\<system.diagnostics>](system-diagnostics-element.md)|<span data-ttu-id="5d01b-127">指定用于收集、存储和路由消息的跟踪侦听器以及对跟踪开关设置的级别。</span><span class="sxs-lookup"><span data-stu-id="5d01b-127">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|[\<trace>](trace-element.md)|<span data-ttu-id="5d01b-128">包含用于收集、存储和路由跟踪消息的侦听器。</span><span class="sxs-lookup"><span data-stu-id="5d01b-128">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5d01b-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="5d01b-129">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.Debug>
- [<span data-ttu-id="5d01b-130">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="5d01b-130">Configuration File Schema</span></span>](../index.md)
