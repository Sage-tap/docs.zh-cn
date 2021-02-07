---
description: 了解详细信息： <workflowIdle>
title: <workflowIdle>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: c1707ab5c633a358846a8ddf529bbfab90d3012d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697954"
---
# \<workflowIdle>

<span data-ttu-id="e17a4-102">一种服务行为，可以控制何时卸载和持久保存空闲工作流实例。</span><span class="sxs-lookup"><span data-stu-id="e17a4-102">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowIdle>**  
  
## <a name="syntax"></a><span data-ttu-id="e17a4-103">语法</span><span class="sxs-lookup"><span data-stu-id="e17a4-103">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowIdle timeToPersist="TimeSpan"
                    timeToUnload="TimeSpan" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e17a4-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="e17a4-104">Attributes and Elements</span></span>  

 <span data-ttu-id="e17a4-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e17a4-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e17a4-106">特性</span><span class="sxs-lookup"><span data-stu-id="e17a4-106">Attributes</span></span>  
  
|<span data-ttu-id="e17a4-107">属性</span><span class="sxs-lookup"><span data-stu-id="e17a4-107">Attribute</span></span>|<span data-ttu-id="e17a4-108">说明</span><span class="sxs-lookup"><span data-stu-id="e17a4-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e17a4-109">timeToPersist</span><span class="sxs-lookup"><span data-stu-id="e17a4-109">timeToPersist</span></span>|<span data-ttu-id="e17a4-110">一个 Timespan 值，该值指定工作流进入空闲状态与持久保存工作流之间的持续时间。</span><span class="sxs-lookup"><span data-stu-id="e17a4-110">A Timespan value that specifies the duration between the time the workflow becomes idle and is persisted.</span></span> <span data-ttu-id="e17a4-111">默认值为 TimeSpan.MaxValue。</span><span class="sxs-lookup"><span data-stu-id="e17a4-111">The default value is TimeSpan.MaxValue.</span></span><br /><br /> <span data-ttu-id="e17a4-112">该持续时间从工作流实例进入空闲状态时算起。</span><span class="sxs-lookup"><span data-stu-id="e17a4-112">The duration begins to elapse when the workflow instance becomes idle.</span></span> <span data-ttu-id="e17a4-113">如果您想要更积极地持久保存工作流实例，同时还要尽可能长久地在内存中保留该实例，此特性会非常有用。</span><span class="sxs-lookup"><span data-stu-id="e17a4-113">This attribute  is useful if you want to persist a workflow instance more aggressively while still keeping the instance in memory for as long as possible.</span></span> <span data-ttu-id="e17a4-114">仅当此属性的值小于 **timeToUnload** 属性时，此属性才有效。</span><span class="sxs-lookup"><span data-stu-id="e17a4-114">This attribute  is only valid if its value is less than the **timeToUnload** attribute.</span></span> <span data-ttu-id="e17a4-115">如果大于该特性，将忽略此项。</span><span class="sxs-lookup"><span data-stu-id="e17a4-115">If it is greater, it is ignored.</span></span> <span data-ttu-id="e17a4-116">如果此属性在 **timeToUnload** 属性指定的值之前过期，则必须在卸载工作流之前完成暂留。</span><span class="sxs-lookup"><span data-stu-id="e17a4-116">If this attribute elapses before the value specified by the **timeToUnload** attribute, persistence must complete before the workflow is unloaded.</span></span> <span data-ttu-id="e17a4-117">这意味着卸载操作可能要等到工作流永久保留完毕才能进行。</span><span class="sxs-lookup"><span data-stu-id="e17a4-117">This implies that the unload operation may be delayed until the workflow is persisted.</span></span> <span data-ttu-id="e17a4-118">永久层负责处理暂时性错误的任何重试操作，并仅在发生不可恢复的错误时引发异常。</span><span class="sxs-lookup"><span data-stu-id="e17a4-118">The persistence layer is responsible for handling any retries for transient errors and only throws exceptions on non-recoverable errors.</span></span> <span data-ttu-id="e17a4-119">因此，任何在持久性操作期间引发的异常都将被视为是致命的，并导致该工作流实例中止。</span><span class="sxs-lookup"><span data-stu-id="e17a4-119">Therefore, any exceptions thrown during persistence are treated as fatal and the workflow instance is aborted.</span></span>|  
|<span data-ttu-id="e17a4-120">timeToUnload</span><span class="sxs-lookup"><span data-stu-id="e17a4-120">timeToUnload</span></span>|<span data-ttu-id="e17a4-121">一个 Timespan 值，该值指定工作流进入空闲状态与卸载工作流之间的持续时间。</span><span class="sxs-lookup"><span data-stu-id="e17a4-121">A Timespan value that specifies the duration between the time the workflow becomes idle and is unloaded.</span></span> <span data-ttu-id="e17a4-122">默认值为 1 分钟。</span><span class="sxs-lookup"><span data-stu-id="e17a4-122">The default value is 1 minute.</span></span><br /><br /> <span data-ttu-id="e17a4-123">卸载一个工作流意味着该工作流已持久保存。</span><span class="sxs-lookup"><span data-stu-id="e17a4-123">Unloading a workflow implies that it is also persisted.</span></span> <span data-ttu-id="e17a4-124">如果此特性设置为零，则在工作流进入空闲状态后会立即持久保存并卸载该工作流实例。</span><span class="sxs-lookup"><span data-stu-id="e17a4-124">If this attribute is set to zero the workflow instance is persisted and unloaded immediately after the workflow becomes idle.</span></span> <span data-ttu-id="e17a4-125">将此特性设置为 TimeSpan.MaxValue 可以有效地禁用卸载操作。</span><span class="sxs-lookup"><span data-stu-id="e17a4-125">Setting this attribute to TimeSpan.MaxValue effectively disables the unload operation.</span></span> <span data-ttu-id="e17a4-126">处于空闲状态的工作流实例永远不会被卸载。</span><span class="sxs-lookup"><span data-stu-id="e17a4-126">Idle workflow instances are never unloaded.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e17a4-127">子元素</span><span class="sxs-lookup"><span data-stu-id="e17a4-127">Child Elements</span></span>  

 <span data-ttu-id="e17a4-128">无。</span><span class="sxs-lookup"><span data-stu-id="e17a4-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e17a4-129">父元素</span><span class="sxs-lookup"><span data-stu-id="e17a4-129">Parent Elements</span></span>  
  
|<span data-ttu-id="e17a4-130">元素</span><span class="sxs-lookup"><span data-stu-id="e17a4-130">Element</span></span>|<span data-ttu-id="e17a4-131">说明</span><span class="sxs-lookup"><span data-stu-id="e17a4-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e17a4-132">\<serviceBehaviors> 的 \<behavior></span><span class="sxs-lookup"><span data-stu-id="e17a4-132">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="e17a4-133">指定行为元素。</span><span class="sxs-lookup"><span data-stu-id="e17a4-133">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e17a4-134">请参阅</span><span class="sxs-lookup"><span data-stu-id="e17a4-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
