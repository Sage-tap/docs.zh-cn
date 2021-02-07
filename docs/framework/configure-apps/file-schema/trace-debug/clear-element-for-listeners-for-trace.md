---
description: 详细了解： <clear> <listeners> 的元素 <trace>
title: <clear>的元素 <listeners><trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 3c1b3816f4ccd0ceb9e9bc0fc6acfd9b6e8ade85
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725969"
---
# <a name="clear-element-for-listeners-for-trace"></a><span data-ttu-id="0bcf1-103">\<clear>的元素 \<listeners>\<trace></span><span class="sxs-lookup"><span data-stu-id="0bcf1-103">\<clear> Element for \<listeners> for \<trace></span></span>

<span data-ttu-id="0bcf1-104">清除跟踪的 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="0bcf1-104">Clears the `Listeners` collection for trace.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="0bcf1-105">语法</span><span class="sxs-lookup"><span data-stu-id="0bcf1-105">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0bcf1-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="0bcf1-106">Attributes and Elements</span></span>  

 <span data-ttu-id="0bcf1-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="0bcf1-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0bcf1-108">特性</span><span class="sxs-lookup"><span data-stu-id="0bcf1-108">Attributes</span></span>  

 <span data-ttu-id="0bcf1-109">无。</span><span class="sxs-lookup"><span data-stu-id="0bcf1-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0bcf1-110">子元素</span><span class="sxs-lookup"><span data-stu-id="0bcf1-110">Child Elements</span></span>  

 <span data-ttu-id="0bcf1-111">无。</span><span class="sxs-lookup"><span data-stu-id="0bcf1-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0bcf1-112">父元素</span><span class="sxs-lookup"><span data-stu-id="0bcf1-112">Parent Elements</span></span>  
  
|<span data-ttu-id="0bcf1-113">元素</span><span class="sxs-lookup"><span data-stu-id="0bcf1-113">Element</span></span>|<span data-ttu-id="0bcf1-114">说明</span><span class="sxs-lookup"><span data-stu-id="0bcf1-114">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0bcf1-115">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="0bcf1-115">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="0bcf1-116">指定用于收集、存储和路由消息的跟踪侦听器以及对跟踪开关设置的级别。</span><span class="sxs-lookup"><span data-stu-id="0bcf1-116">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="0bcf1-117">包含用于收集、存储和路由跟踪消息的侦听器。</span><span class="sxs-lookup"><span data-stu-id="0bcf1-117">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="0bcf1-118">包含收集、存储和路由消息的侦听器。</span><span class="sxs-lookup"><span data-stu-id="0bcf1-118">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="0bcf1-119">侦听器将跟踪输出定向到适当的目标。</span><span class="sxs-lookup"><span data-stu-id="0bcf1-119">Listeners direct the tracing output to an appropriate target.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0bcf1-120">备注</span><span class="sxs-lookup"><span data-stu-id="0bcf1-120">Remarks</span></span>  

 <span data-ttu-id="0bcf1-121">`<clear>`元素从跟踪的集合中移除所有侦听器 `Listeners` 。</span><span class="sxs-lookup"><span data-stu-id="0bcf1-121">The `<clear>` element removes all listeners from the `Listeners` collection for trace.</span></span> <span data-ttu-id="0bcf1-122">可以在使用元素 `<clear>` 之前使用元素 `<add>` ，以确定集合中没有其他活动的侦听器。</span><span class="sxs-lookup"><span data-stu-id="0bcf1-122">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
 <span data-ttu-id="0bcf1-123">您可以 `Listeners` 通过 <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> 对 <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> 属性 () 调用方法，以编程方式清除该集合 `System.Diagnostics.Trace.Listeners.Clear()` 。</span><span class="sxs-lookup"><span data-stu-id="0bcf1-123">You can clear the `Listeners` collection programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> method on the <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> property (`System.Diagnostics.Trace.Listeners.Clear()`).</span></span>  
  
 <span data-ttu-id="0bcf1-124">此元素可在计算机配置文件中使用 ( # A0) 和应用程序配置文件。</span><span class="sxs-lookup"><span data-stu-id="0bcf1-124">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0bcf1-125">`<clear>`元素 <xref:System.Diagnostics.DefaultTraceListener> 从集合中移除， `Listeners` 并更改 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> 、 <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType> 、 <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType> 和 <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> 方法的行为。</span><span class="sxs-lookup"><span data-stu-id="0bcf1-125">The `<clear>` element removes the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection, altering the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="0bcf1-126">通常调用 `Assert` 或 `Fail` 方法会导致显示消息框。</span><span class="sxs-lookup"><span data-stu-id="0bcf1-126">Calling an `Assert` or `Fail` method normally results in the display of a message box.</span></span> <span data-ttu-id="0bcf1-127">但是，如果不在集合中，则不会显示消息框 <xref:System.Diagnostics.DefaultTraceListener> `Listeners` 。</span><span class="sxs-lookup"><span data-stu-id="0bcf1-127">However, the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0bcf1-128">示例</span><span class="sxs-lookup"><span data-stu-id="0bcf1-128">Example</span></span>  

 <span data-ttu-id="0bcf1-129">下面的示例演示如何 `<clear>` 在使用 `<add>` 元素将侦听器添加 `console` 到用于 trace 的集合之前使用元素 `Listeners` 。</span><span class="sxs-lookup"><span data-stu-id="0bcf1-129">The following example shows how to use the `<clear>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for trace.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <clear/>  
        <add name="console"
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"
            initializeData="Error" />  
        </add>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="0bcf1-130">请参阅</span><span class="sxs-lookup"><span data-stu-id="0bcf1-130">See also</span></span>

- <xref:System.Diagnostics.Trace.Listeners%2A>
- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="0bcf1-131">跟踪和调试设置架构</span><span class="sxs-lookup"><span data-stu-id="0bcf1-131">Trace and Debug Settings Schema</span></span>](index.md)
- [\<remove>](remove-element-for-listeners-for-trace.md)
- [<span data-ttu-id="0bcf1-132">跟踪侦听器</span><span class="sxs-lookup"><span data-stu-id="0bcf1-132">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
