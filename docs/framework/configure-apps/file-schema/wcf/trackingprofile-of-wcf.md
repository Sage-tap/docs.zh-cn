---
description: 了解有关 WCF 的详细信息： <trackingProfile>
title: <trackingProfile> WCF 的
ms.date: 10/08/2018
ms.assetid: 09b651c2-c0d2-4850-a101-b0e009a1dc3a
ms.openlocfilehash: d896457f45905739abd61892ac6058ddfc0f5034
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99773766"
---
# <a name="trackingprofile-of-wcf"></a><span data-ttu-id="86794-103">\<trackingProfile> WCF 的</span><span class="sxs-lookup"><span data-stu-id="86794-103">\<trackingProfile> of WCF</span></span>

<span data-ttu-id="86794-104">表示一个配置节，用于创建对跟踪参与者中的工作流跟踪记录的订阅。</span><span class="sxs-lookup"><span data-stu-id="86794-104">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="86794-105">跟踪配置文件包含跟踪查询，这些查询允许跟踪参与者订阅当工作流实例的状态在运行时发生更改时发出的工作流事件。</span><span class="sxs-lookup"><span data-stu-id="86794-105">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="86794-106">跟踪配置文件节中定义的查询用于定义订阅返回的事件类型。</span><span class="sxs-lookup"><span data-stu-id="86794-106">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>  
  
<span data-ttu-id="86794-107">有关工作流跟踪及其配置的详细信息，请参阅 [工作流跟踪和跟踪](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) 和 [跟踪配置文件](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="86794-107">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<trackingProfile>**  
  
## <a name="syntax"></a><span data-ttu-id="86794-108">语法</span><span class="sxs-lookup"><span data-stu-id="86794-108">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <tracking>
    <profiles>
      <trackingProfile name="String">
        <workflow activityDefinitionId="String">
          <activityScheduledQueries>
            <activityScheduledQuery activityName="String"
                                    childActivityName="String" />
          </activityScheduledQueries>
          <activityStateQueries>
            <activityStateQuery activityName="String">
              <arguments>
                <argument name="String" />
              </arguments>
              <states>
                <state name="String" />
              </states>
              <variables>
                <variable name="String" />
              </variables>
            </activityStateQuery>
          </activityStateQueries>
          <bookmarkResumptionQueries>
            <bookmarkResumptionQuery name="String" />
          </bookmarkResumptionQueries>
          <cancelRequestedQueries>
            <cancelRequestedQuery activityName="String"
                                  childActivityName="String" />
          </cancelRequestedQueries>
          <customTrackingQueries>
            <customTrackingQuery activityName="String"
                                 name="String" />
          </customTrackingQueries>
          <faultPropagationQueries>
            <faultPropagationQuery faultSourceActivityName="String"
                                   faultHandlerActivityName="String" />
          </faultPropagationQueries>
          <stateMachineStateQueries>
            <stateMachineStateQuery activityName="String" />
          </stateMachineStateQueries>
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="String"/>
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="86794-109">特性和元素</span><span class="sxs-lookup"><span data-stu-id="86794-109">Attributes and Elements</span></span>  

<span data-ttu-id="86794-110">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="86794-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="86794-111">特性</span><span class="sxs-lookup"><span data-stu-id="86794-111">Attributes</span></span>  
  
|<span data-ttu-id="86794-112">属性</span><span class="sxs-lookup"><span data-stu-id="86794-112">Attribute</span></span>|<span data-ttu-id="86794-113">说明</span><span class="sxs-lookup"><span data-stu-id="86794-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="86794-114">name</span><span class="sxs-lookup"><span data-stu-id="86794-114">name</span></span>|<span data-ttu-id="86794-115">一个字符串，指定跟踪配置文件的名称。</span><span class="sxs-lookup"><span data-stu-id="86794-115">A string that specifies the name of the tracking profile.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="86794-116">子元素</span><span class="sxs-lookup"><span data-stu-id="86794-116">Child Elements</span></span>  
  
|<span data-ttu-id="86794-117">元素</span><span class="sxs-lookup"><span data-stu-id="86794-117">Element</span></span>|<span data-ttu-id="86794-118">说明</span><span class="sxs-lookup"><span data-stu-id="86794-118">Description</span></span>|  
|-------------|-----------------|  
|[\<participants>](../windows-workflow-foundation/participants.md)|<span data-ttu-id="86794-119">一个配置元素，包含 <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> 属性所标识的特定工作流的所有查询。</span><span class="sxs-lookup"><span data-stu-id="86794-119">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> property.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="86794-120">父元素</span><span class="sxs-lookup"><span data-stu-id="86794-120">Parent Elements</span></span>  
  
|<span data-ttu-id="86794-121">元素</span><span class="sxs-lookup"><span data-stu-id="86794-121">Element</span></span>|<span data-ttu-id="86794-122">说明</span><span class="sxs-lookup"><span data-stu-id="86794-122">Description</span></span>|  
|-------------|-----------------|  
|[\<tracking>](../windows-workflow-foundation/tracking.md)|<span data-ttu-id="86794-123">表示一个配置节，用于定义工作流服务的跟踪设置。</span><span class="sxs-lookup"><span data-stu-id="86794-123">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86794-124">备注</span><span class="sxs-lookup"><span data-stu-id="86794-124">Remarks</span></span>  

 <span data-ttu-id="86794-125">跟踪配置文件包含跟踪查询，这些查询允许跟踪参与者订阅当工作流实例的状态在运行时发生更改时发出的工作流事件。</span><span class="sxs-lookup"><span data-stu-id="86794-125">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="86794-126">根据您的监视需求，可以编写一个非常粗陋的配置文件，用来订阅对工作流进行的一小组高级状态更改。</span><span class="sxs-lookup"><span data-stu-id="86794-126">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="86794-127">相反，也可以创建一个非常具体的配置文件，其生成的事件足够丰富，可在以后重新构造详细的执行流。</span><span class="sxs-lookup"><span data-stu-id="86794-127">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="86794-128">跟踪配置文件组织为跟踪记录的声明性订阅，利用这些订阅可以查询特定跟踪记录的工作流运行时。</span><span class="sxs-lookup"><span data-stu-id="86794-128">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="86794-129">有几种查询类型允许您订阅不同的 <xref:System.Activities.Tracking.TrackingRecord> 对象类。</span><span class="sxs-lookup"><span data-stu-id="86794-129">There are a handful of query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="86794-130">有关查询的完整列表，请参阅 [\<participants>](../windows-workflow-foundation/participants.md) 和 [跟踪配置文件](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="86794-130">For a complete list of queries, see [\<participants>](../windows-workflow-foundation/participants.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="86794-131">下面的示例演示配置文件中的跟踪配置文件，该配置文件允许跟踪参与者订阅 `Started` 和 `Completed` 工作流事件。</span><span class="sxs-lookup"><span data-stu-id="86794-131">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
```xml  
<system.serviceModel>
  <tracking>
    <profiles>
      <trackingProfile name="Sample Tracking Profile">
        <workflow activityDefinitionId="*">
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="Started" />
                <state name="Completed" />
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>
```  
  
## <a name="see-also"></a><span data-ttu-id="86794-132">请参阅</span><span class="sxs-lookup"><span data-stu-id="86794-132">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="86794-133">工作流跟踪</span><span class="sxs-lookup"><span data-stu-id="86794-133">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="86794-134">跟踪配置文件</span><span class="sxs-lookup"><span data-stu-id="86794-134">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
