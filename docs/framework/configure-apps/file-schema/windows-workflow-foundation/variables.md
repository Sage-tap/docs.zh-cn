---
description: 了解详细信息： <variables>
title: <variables>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: da0fd144-dda9-4613-b650-fe6325076513
ms.openlocfilehash: e77c4fb1d4d16a655cd1918bb9460177b7ff3266
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698006"
---
# \<variables>

<span data-ttu-id="f83bc-102">表示与此活动查询关联的变量的集合。</span><span class="sxs-lookup"><span data-stu-id="f83bc-102">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="f83bc-103">有关跟踪配置文件查询的详细信息，请参阅 [跟踪配置文件](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="f83bc-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<variables>**  
  
## <a name="syntax"></a><span data-ttu-id="f83bc-104">语法</span><span class="sxs-lookup"><span data-stu-id="f83bc-104">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <variables>
          <variable name="String" />
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f83bc-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="f83bc-105">Attributes and Elements</span></span>  

 <span data-ttu-id="f83bc-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f83bc-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f83bc-107">特性</span><span class="sxs-lookup"><span data-stu-id="f83bc-107">Attributes</span></span>  

 <span data-ttu-id="f83bc-108">无。</span><span class="sxs-lookup"><span data-stu-id="f83bc-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f83bc-109">子元素</span><span class="sxs-lookup"><span data-stu-id="f83bc-109">Child Elements</span></span>  
  
|<span data-ttu-id="f83bc-110">元素</span><span class="sxs-lookup"><span data-stu-id="f83bc-110">Element</span></span>|<span data-ttu-id="f83bc-111">说明</span><span class="sxs-lookup"><span data-stu-id="f83bc-111">Description</span></span>|  
|-------------|-----------------|  
|[\<variable>](variable.md)|<span data-ttu-id="f83bc-112">与活动状态查询相关联的变量。</span><span class="sxs-lookup"><span data-stu-id="f83bc-112">A variable associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f83bc-113">父元素</span><span class="sxs-lookup"><span data-stu-id="f83bc-113">Parent Elements</span></span>  
  
|<span data-ttu-id="f83bc-114">元素</span><span class="sxs-lookup"><span data-stu-id="f83bc-114">Element</span></span>|<span data-ttu-id="f83bc-115">说明</span><span class="sxs-lookup"><span data-stu-id="f83bc-115">Description</span></span>|  
|-------------|-----------------|  
|[\<activityStateQuery>](activitystatequery.md)|<span data-ttu-id="f83bc-116">表示一个配置元素，该元素用于跟踪父活动取消子活动的请求。</span><span class="sxs-lookup"><span data-stu-id="f83bc-116">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="f83bc-117">跟踪参与者需要用此查询来订阅取消请求记录对象。</span><span class="sxs-lookup"><span data-stu-id="f83bc-117">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f83bc-118">备注</span><span class="sxs-lookup"><span data-stu-id="f83bc-118">Remarks</span></span>  

 <span data-ttu-id="f83bc-119">ActivityStateQuery 的一项独特功能是能够在跟踪工作流的执行时提取数据。</span><span class="sxs-lookup"><span data-stu-id="f83bc-119">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="f83bc-120">这在访问跟踪记录后续执行时可提供其他上下文。</span><span class="sxs-lookup"><span data-stu-id="f83bc-120">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="f83bc-121">您可以使用 [\<arguments>](arguments.md) 、 [\<states>](states.md) 和 [\<states>](states.md) 元素从工作流中的任何活动提取任何变量或参数。</span><span class="sxs-lookup"><span data-stu-id="f83bc-121">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="f83bc-122">下面的示例演示用于在发出活动的 `Closed` 跟踪记录时提取变量和自变量的活动状态查询。</span><span class="sxs-lookup"><span data-stu-id="f83bc-122">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="f83bc-123">变量和参数只能通过 ActivityStateRecord 提取，因此使用在跟踪配置文件内进行订阅 [\<activityStateQuery>](activitystatequery.md) 。</span><span class="sxs-lookup"><span data-stu-id="f83bc-123">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <variables>  
    <variable name="FromAddress"/>  
  </variables>  
  <arguments>  
    <argument name="Result"/>  
  </arguments>  
</activityStateQuery>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f83bc-124">请参阅</span><span class="sxs-lookup"><span data-stu-id="f83bc-124">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="f83bc-125">工作流跟踪</span><span class="sxs-lookup"><span data-stu-id="f83bc-125">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="f83bc-126">跟踪配置文件</span><span class="sxs-lookup"><span data-stu-id="f83bc-126">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
