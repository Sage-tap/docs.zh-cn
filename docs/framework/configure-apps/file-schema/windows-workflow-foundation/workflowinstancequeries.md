---
description: 了解详细信息： <workflowInstanceQueries>
title: <workflowInstanceQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fe7ce85-cf9a-4dbf-a8f7-bc9b1fc2fe35
ms.openlocfilehash: 7672bcd574c15f130b8553881e53994afe9cda93
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697837"
---
# \<workflowInstanceQueries>

<span data-ttu-id="e7e56-102">表示配置元素的集合，这些配置元素跟踪工作流实例生命周期的更改，例如已开始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="e7e56-102">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="e7e56-103">有关跟踪配置文件查询的详细信息，请参阅 [跟踪配置文件](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="e7e56-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="e7e56-104">语法</span><span class="sxs-lookup"><span data-stu-id="e7e56-104">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <workflowInstanceQueries>
        <workflowInstanceQuery>
          <states>
            <state name="Name"/>
          </states>
        </workflowInstanceQuery>
      </workflowInstanceQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e7e56-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="e7e56-105">Attributes and Elements</span></span>  

<span data-ttu-id="e7e56-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e7e56-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e7e56-107">特性</span><span class="sxs-lookup"><span data-stu-id="e7e56-107">Attributes</span></span>  

<span data-ttu-id="e7e56-108">无。</span><span class="sxs-lookup"><span data-stu-id="e7e56-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e7e56-109">子元素</span><span class="sxs-lookup"><span data-stu-id="e7e56-109">Child Elements</span></span>  
  
|<span data-ttu-id="e7e56-110">元素</span><span class="sxs-lookup"><span data-stu-id="e7e56-110">Element</span></span>|<span data-ttu-id="e7e56-111">说明</span><span class="sxs-lookup"><span data-stu-id="e7e56-111">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowInstanceQuery>](workflowinstancequery.md)|<span data-ttu-id="e7e56-112">一个查询，用于跟踪工作流实例生命周期的更改。</span><span class="sxs-lookup"><span data-stu-id="e7e56-112">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e7e56-113">父元素</span><span class="sxs-lookup"><span data-stu-id="e7e56-113">Parent Elements</span></span>  
  
|<span data-ttu-id="e7e56-114">元素</span><span class="sxs-lookup"><span data-stu-id="e7e56-114">Element</span></span>|<span data-ttu-id="e7e56-115">说明</span><span class="sxs-lookup"><span data-stu-id="e7e56-115">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="e7e56-116">一个配置元素，该元素包含由 **activityDefinitionId** 属性标识的特定工作流的所有查询。</span><span class="sxs-lookup"><span data-stu-id="e7e56-116">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7e56-117">备注</span><span class="sxs-lookup"><span data-stu-id="e7e56-117">Remarks</span></span>  

<span data-ttu-id="e7e56-118"><xref:System.Activities.Tracking.WorkflowInstanceQuery> 用于订阅以下 <xref:System.Activities.Tracking.TrackingRecord> 对象：</span><span class="sxs-lookup"><span data-stu-id="e7e56-118">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="e7e56-119">示例</span><span class="sxs-lookup"><span data-stu-id="e7e56-119">Example</span></span>  

<span data-ttu-id="e7e56-120">下面的配置使用此查询订阅 `Started` 实例状态的工作流实例级跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="e7e56-120">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e7e56-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="e7e56-121">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="e7e56-122">工作流跟踪</span><span class="sxs-lookup"><span data-stu-id="e7e56-122">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e7e56-123">跟踪配置文件</span><span class="sxs-lookup"><span data-stu-id="e7e56-123">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
