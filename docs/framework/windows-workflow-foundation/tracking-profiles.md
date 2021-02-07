---
description: 了解详细信息：跟踪配置文件
title: 跟踪配置文件
ms.date: 03/30/2017
ms.assetid: 22682566-1cd9-4672-9791-fb3523638e18
ms.openlocfilehash: 9748f0452a1699e08760372f826f2458d82f4b79
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755143"
---
# <a name="tracking-profiles"></a><span data-ttu-id="d9c6a-103">跟踪配置文件</span><span class="sxs-lookup"><span data-stu-id="d9c6a-103">Tracking Profiles</span></span>

<span data-ttu-id="d9c6a-104">跟踪配置文件包含跟踪查询，这些查询允许跟踪参与者订阅当工作流实例的状态在运行时发生更改时发出的工作流事件。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-104">Tracking profiles contain tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span>

## <a name="tracking-profiles"></a><span data-ttu-id="d9c6a-105">跟踪配置文件</span><span class="sxs-lookup"><span data-stu-id="d9c6a-105">Tracking Profiles</span></span>

<span data-ttu-id="d9c6a-106">跟踪配置文件用来指定为工作流实例发出的跟踪信息。 </span><span class="sxs-lookup"><span data-stu-id="d9c6a-106">Tracking profiles are used to specify which tracking information is emitted for a workflow instance.</span></span> <span data-ttu-id="d9c6a-107">如果未指定配置文件，则发出所有跟踪事件。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-107">If no profile is specified, then all tracking events are emitted.</span></span> <span data-ttu-id="d9c6a-108">如果指定了配置文件，将发出在配置文件中指定的跟踪事件。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-108">If a profile is specified, then the tracking events specified in the profile will be emitted.</span></span> <span data-ttu-id="d9c6a-109">根据您的监视需求，可以编写一个非常一般的配置文件，用来订阅对工作流进行的一小组高级状态更改。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-109">Depending on your monitoring requirements, you may write a profile that is very general, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="d9c6a-110">相反，也可以创建一个非常详细的配置文件，其生成的事件足够丰富，可在以后重新构造详细的执行流。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-110">Conversely, you may create a very detailed profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>

<span data-ttu-id="d9c6a-111">在标准 .NET Framework 配置文件中或在代码中指定，将配置文件清单本身作为 XML 元素进行跟踪。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-111">Tracking profiles manifest themselves as XML elements within a standard .NET Framework configuration file or specified in code.</span></span> <span data-ttu-id="d9c6a-112">下面的示例摘自配置文件中的 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]跟踪配置文件，跟踪参与者可利用它订阅 `Started` 和 `Completed` 工作流事件。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-112">The following example is of a [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>

```xml
<system.serviceModel>
    ...
    <tracking>
     <profiles>
      <trackingProfile name="Sample Tracking Profile">
        <workflow activityDefinitionId="*">
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="Started"/>
                <state name="Completed"/>
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
    ...
</system.serviceModel>
```

<span data-ttu-id="d9c6a-113">下面的示例演示使用代码创建的等效跟踪配置文件。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-113">The following example shows the equivalent tracking profile created using code.</span></span>

```csharp
TrackingProfile profile = new TrackingProfile()
{
    Name = "CustomTrackingProfile",
    Queries =
    {
        new WorkflowInstanceQuery()
        {
            // Limit workflow instance tracking records for started and
            // completed workflow states.
            States = { WorkflowInstanceStates.Started, WorkflowInstanceStates.Completed },
        }
    }
};
```

<span data-ttu-id="d9c6a-114">利用 <xref:System.Activities.Tracking.ImplementationVisibility> 特性，可以通过跟踪配置文件中的可见性模式筛选跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-114">Tracking records are filtered through the visibility mode within a tracking profile by using the <xref:System.Activities.Tracking.ImplementationVisibility> attribute.</span></span> <span data-ttu-id="d9c6a-115">复合活动是顶级活动，包含构成其实现的其他活动。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-115">A composite activity is a top-level activity that contains other activities that form its implementation.</span></span> <span data-ttu-id="d9c6a-116">可见性模式指定工作流活动中的复合活动发出的跟踪记录，这些跟踪记录用于指定是否跟踪构成实现的活动。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-116">The visibility mode specifies the tracking records emitted from composite activities within a workflow activity, to specify if activities that form the implementation are being tracked.</span></span> <span data-ttu-id="d9c6a-117">可见性模式在跟踪配置文件级别应用。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-117">The visibility mode applies at the tracking profile level.</span></span> <span data-ttu-id="d9c6a-118">对工作流中单个活动的跟踪记录的筛选由跟踪配置文件中的查询控制。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-118">The filtering of tracking records for individual activities within a workflow is controlled by the queries within the tracking profile.</span></span> <span data-ttu-id="d9c6a-119">有关详细信息，请参阅本文档中的 **跟踪配置文件查询类型** 部分。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-119">For more information, see the **Tracking Profile Query Types** section in this document.</span></span>

<span data-ttu-id="d9c6a-120">跟踪配置文件中的 `implementationVisibility` 特性指定的两种可见性模式包括 `RootScope` 和 `All`。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-120">The two visibility modes specified by the `implementationVisibility` attribute in the tracking profile are `RootScope` and `All`.</span></span> <span data-ttu-id="d9c6a-121">如果复合活动不是工作流的根，则使用 `RootScope` 模式会禁止构成活动实现的活动的跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-121">Using the `RootScope` mode suppresses the tracking records for activities that form the implementation of an activity in the case where a composite activity is not the root of a workflow.</span></span> <span data-ttu-id="d9c6a-122">这意味着，如果将使用其他活动实现的某一活动添加到工作流中，并将 `implementationVisibility` 设置为 RootScope，则仅跟踪该复合活动中的顶级活动。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-122">This implies that, when an activity that is implemented using other activities is added to a workflow, and the `implementationVisibility` set to RootScope, only the top-level activity within that composite activity is tracked.</span></span> <span data-ttu-id="d9c6a-123">如果活动是工作流的根，该活动的实现即为工作流自身，因此将发出构成实现的活动的跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-123">If an activity is the root of the workflow, then the implementation of the activity is the workflow itself and tracking records are emitted for activities that form the implementation.</span></span> <span data-ttu-id="d9c6a-124">使用 All 模式允许发出根活动及其所有复合活动的所有跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-124">Using the All mode permits all tracking records to be emitted for the root activity and all its composite activities.</span></span>

<span data-ttu-id="d9c6a-125">例如，假设 *MyActivity* 是一个复合活动，其实现包含两个活动： *Activity1* 和 *Activity2*。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-125">For example, suppose *MyActivity* is a composite activity whose implementation contains two activities, *Activity1* and *Activity2*.</span></span> <span data-ttu-id="d9c6a-126">如果将此活动添加到工作流，并使用设置为的跟踪配置文件启用跟踪 `implementationVisibility` `RootScope` ，则只会为 *MyActivity* 发出跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-126">When this activity is added to a workflow and tracking is enabled with a tracking profile with `implementationVisibility` set to `RootScope`, tracking records are emitted only for *MyActivity*.</span></span> <span data-ttu-id="d9c6a-127">但是，对于 activity *Activity1* 和 *Activity2*，不会发出任何记录。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-127">However, no records are emitted for activities *Activity1* and *Activity2*.</span></span>

<span data-ttu-id="d9c6a-128">但是，如果将 `implementationVisibility` 跟踪配置文件的属性设置为 `All` ，则会同时为 *MyActivity* 和活动 *Activity1* 和 *Activity2* 发出跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-128">However, if the `implementationVisibility` attribute for the tracking profile is  set to `All`, then tracking records are emitted not only for *MyActivity*, but also for activities *Activity1* and *Activity2*.</span></span>

<span data-ttu-id="d9c6a-129">`implementationVisibility` 标志适用于以下跟踪记录类型：</span><span class="sxs-lookup"><span data-stu-id="d9c6a-129">The `implementationVisibility` flag applies to following tracking record types:</span></span>

- <span data-ttu-id="d9c6a-130">ActivityStateRecord</span><span class="sxs-lookup"><span data-stu-id="d9c6a-130">ActivityStateRecord</span></span>

- <span data-ttu-id="d9c6a-131">FaultPropagationRecord</span><span class="sxs-lookup"><span data-stu-id="d9c6a-131">FaultPropagationRecord</span></span>

- <span data-ttu-id="d9c6a-132">CancelRequestedRecord</span><span class="sxs-lookup"><span data-stu-id="d9c6a-132">CancelRequestedRecord</span></span>

- <span data-ttu-id="d9c6a-133">ActivityScheduledRecord</span><span class="sxs-lookup"><span data-stu-id="d9c6a-133">ActivityScheduledRecord</span></span>

> [!NOTE]
> <span data-ttu-id="d9c6a-134">implementationVisibility 设置无法筛选出活动实现发出的 CustomTrackingRecord。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-134">CustomTrackingRecords emitted from activity implementation are not filtered out by the implementationVisibility setting.</span></span>

<span data-ttu-id="d9c6a-135">在代码中，按如下所示在跟踪配置文件中将 `implementationVisibility` 功能指定为 <xref:System.Activities.Tracking.ImplementationVisibility.RootScope>：</span><span class="sxs-lookup"><span data-stu-id="d9c6a-135">The `implementationVisibility` functionality is specified as <xref:System.Activities.Tracking.ImplementationVisibility.RootScope> on the tracking profile in code as follows:</span></span>

```csharp
TrackingProfile sampleTrackingProfile = new TrackingProfile()
{
    Name = "Sample Tracking Profile",
    ImplementationVisibility = ImplementationVisibility.RootScope
};
```

<span data-ttu-id="d9c6a-136">在配置文件中，按如下所示在跟踪配置文件中将 `implementationVisibility` 功能指定为 <xref:System.Activities.Tracking.ImplementationVisibility.All>：</span><span class="sxs-lookup"><span data-stu-id="d9c6a-136">The `implementationVisibility` functionality is specified as <xref:System.Activities.Tracking.ImplementationVisibility.All> on the tracking profile in a configuration file as follows:</span></span>

```xml
<tracking>
      <profiles>
        <trackingProfile name="Shipping Monitoring" implementationVisibility="All">
          <workflow activityDefinitionId="*">
...
         </workflow>
        </trackingProfile>
      </profiles>
</tracking>
```

<span data-ttu-id="d9c6a-137">跟踪配置文件中的 `ImplementationVisibility` 设置是可选的。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-137">The `ImplementationVisibility` setting on the tracking profile is optional.</span></span> <span data-ttu-id="d9c6a-138">默认情况下，其值设置为 `RootScope`。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-138">By default, its value is set to `RootScope`.</span></span> <span data-ttu-id="d9c6a-139">此外，该特性的值还区分大小写。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-139">The values for this attribute are also case-sensitive.</span></span>

### <a name="tracking-profile-query-types"></a><span data-ttu-id="d9c6a-140">跟踪配置文件查询类型</span><span class="sxs-lookup"><span data-stu-id="d9c6a-140">Tracking Profile Query Types</span></span>

<span data-ttu-id="d9c6a-141">跟踪配置文件组织为跟踪记录的声明性订阅，利用这些订阅可以查询特定跟踪记录的工作流运行时。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-141">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="d9c6a-142">查询类型有多种，可用于订阅 <xref:System.Activities.Tracking.TrackingRecord> 对象的不同类。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-142">There are several query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="d9c6a-143">可以通过配置或代码指定跟踪配置文件。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-143">Tracking profiles can be specified in configuration or through code.</span></span> <span data-ttu-id="d9c6a-144">以下是最常见的查询类型：</span><span class="sxs-lookup"><span data-stu-id="d9c6a-144">Here are the most common query types:</span></span>

- <span data-ttu-id="d9c6a-145"><xref:System.Activities.Tracking.WorkflowInstanceQuery> - 用于跟踪工作流实例生命周期更改，例如，上面演示的 `Started` 和 `Completed`。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-145"><xref:System.Activities.Tracking.WorkflowInstanceQuery> - Use this to track workflow instance life cycle changes like the previously-demonstrated `Started` and `Completed`.</span></span> <span data-ttu-id="d9c6a-146"><xref:System.Activities.Tracking.WorkflowInstanceQuery> 用于订阅以下 <xref:System.Activities.Tracking.TrackingRecord> 对象：</span><span class="sxs-lookup"><span data-stu-id="d9c6a-146">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>

  - <xref:System.Activities.Tracking.WorkflowInstanceRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>

  <span data-ttu-id="d9c6a-147">在 <xref:System.Activities.Tracking.WorkflowInstanceStates> 类中指定了可订阅的状态。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-147">The states that can be subscribed to are specified in the <xref:System.Activities.Tracking.WorkflowInstanceStates> class.</span></span>

  <span data-ttu-id="d9c6a-148">下面的示例演示使用 `Started` 订阅 <xref:System.Activities.Tracking.WorkflowInstanceQuery> 实例状态的工作流实例级跟踪记录所使用的配置或代码。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-148">The configuration or code used to subscribe to workflow instance-level tracking records for the `Started` instance state using the <xref:System.Activities.Tracking.WorkflowInstanceQuery> is shown in the following example.</span></span>

  ```xml
  <workflowInstanceQueries>
      <workflowInstanceQuery>
        <states>
          <state name="Started"/>
        </states>
      </workflowInstanceQuery>
  </workflowInstanceQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new WorkflowInstanceQuery()
          {
              States = { WorkflowInstanceStates.Started}
          }
      }
  };
  ```

- <span data-ttu-id="d9c6a-149"><xref:System.Activities.Tracking.ActivityStateQuery> - 用于跟踪组成工作流实例的活动的生命周期更改。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-149"><xref:System.Activities.Tracking.ActivityStateQuery> - Use this to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="d9c6a-150">例如，你可能想要跟踪每次在工作流实例中完成 "发送电子邮件" 活动的时间。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-150">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="d9c6a-151"><xref:System.Activities.Tracking.TrackingParticipant> 需要用该查询来订阅 <xref:System.Activities.Tracking.ActivityStateRecord> 对象。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-151">This query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.ActivityStateRecord> objects.</span></span> <span data-ttu-id="d9c6a-152">在 <xref:System.Activities.Tracking.ActivityStates> 中指定了要订阅的可用状态。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-152">The available states to subscribe to are specified in <xref:System.Activities.Tracking.ActivityStates>.</span></span>

  <span data-ttu-id="d9c6a-153">下面的示例演示使用 <xref:System.Activities.Tracking.ActivityStateQuery> 订阅 `SendEmailActivity` 活动的活动状态跟踪记录所使用的配置和代码。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-153">The configuration and code used to subscribe activity state tracking records that use the <xref:System.Activities.Tracking.ActivityStateQuery> for the `SendEmailActivity` activity is shown in the following example.</span></span>

  ```xml
  <activityStateQueries>
    <activityStateQuery activityName="SendEmailActivity">
      <states>
        <state name="Closed"/>
      </states>
    </activityStateQuery>
  </activityStateQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new ActivityStateQuery()
          {
              ActivityName = "SendEmailActivity",
              States = { ActivityStates.Closed }
          }
      }
  };
  ```

  > [!NOTE]
  > <span data-ttu-id="d9c6a-154">如果多个 activityStateQuery 元素具有相同名称，则只有最后一个元素中的状态用于跟踪配置文件。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-154">If multiple activityStateQuery elements have the same name, only the states in the last element are used in the tracking profile.</span></span>

- <span data-ttu-id="d9c6a-155"><xref:System.Activities.Tracking.ActivityScheduledQuery> - 该查询用于跟踪安排给父活动来执行的活动。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-155"><xref:System.Activities.Tracking.ActivityScheduledQuery> - This query allows you to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="d9c6a-156"><xref:System.Activities.Tracking.TrackingParticipant> 需要用该查询来订阅 <xref:System.Activities.Tracking.ActivityScheduledRecord> 对象。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-156">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.ActivityScheduledRecord> objects.</span></span>

  <span data-ttu-id="d9c6a-157">下面的示例演示使用 `SendEmailActivity` 订阅与安排执行的 <xref:System.Activities.Tracking.ActivityScheduledQuery> 子活动相关的记录所使用的配置和代码。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-157">The configuration and code used to subscribe to records related to the `SendEmailActivity` child activity being scheduled using the <xref:System.Activities.Tracking.ActivityScheduledQuery> is shown in the following example.</span></span>

  ```xml
  <activityScheduledQueries>
    <activityScheduledQuery activityName="ProcessNotificationsActivity" childActivityName="SendEmailActivity" />
  </activityScheduledQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new ActivityScheduledQuery()
          {
              ActivityName = "ProcessNotificationsActivity",
              ChildActivityName = "SendEmailActivity"
          }
      }
  };
  ```

- <span data-ttu-id="d9c6a-158"><xref:System.Activities.Tracking.FaultPropagationQuery> - 用于跟踪对在活动中出现的错误进行的处理。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-158"><xref:System.Activities.Tracking.FaultPropagationQuery> - Use this to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="d9c6a-159"><xref:System.Activities.Tracking.TrackingParticipant> 需要用该查询来订阅 <xref:System.Activities.Tracking.FaultPropagationRecord> 对象。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-159">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.FaultPropagationRecord> objects.</span></span>

  <span data-ttu-id="d9c6a-160">下面的示例演示使用 <xref:System.Activities.Tracking.FaultPropagationQuery> 订阅与错误传播相关的记录所使用的配置和代码。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-160">The configuration and code used to subscribe to records related to fault propagation using <xref:System.Activities.Tracking.FaultPropagationQuery> is shown in the following example.</span></span>

  ```xml
  <faultPropagationQueries>
    <faultPropagationQuery faultSourceActivityName="SendEmailActivity" faultHandlerActivityName="NotificationsFaultHandler" />
  </faultPropagationQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new FaultPropagationQuery()
          {
              FaultSourceActivityName = "SendEmailActivity",
              FaultHandlerActivityName = "NotificationsFaultHandler"
          }
      }
  };
  ```

- <span data-ttu-id="d9c6a-161"><xref:System.Activities.Tracking.CancelRequestedQuery> - 用于跟踪父活动取消子活动的请求。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-161"><xref:System.Activities.Tracking.CancelRequestedQuery> - Use this to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="d9c6a-162"><xref:System.Activities.Tracking.TrackingParticipant> 需要用该查询来订阅 <xref:System.Activities.Tracking.CancelRequestedRecord> 对象。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-162">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.CancelRequestedRecord> objects.</span></span>

  <span data-ttu-id="d9c6a-163">下面的示例演示了使用订阅与活动取消相关的记录所使用的配置和代码 <xref:System.Activities.Tracking.CancelRequestedQuery> 。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-163">The configuration and code used to subscribe to records related to activity cancellation using <xref:System.Activities.Tracking.CancelRequestedQuery> is shown in the following example.</span></span>

  ```xml
  <cancelRequestedQueries>
    <cancelRequestedQuery activityName="ProcessNotificationsActivity" childActivityName="SendEmailActivity" />
  </cancelRequestedQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new CancelRequestedQuery()
          {
              ActivityName = "ProcessNotificationsActivity",
              ChildActivityName = "SendEmailActivity"
          }
      }
  };
  ```

- <span data-ttu-id="d9c6a-164"><xref:System.Activities.Tracking.CustomTrackingQuery> - 用于跟踪您在代码活动中定义的事件。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-164"><xref:System.Activities.Tracking.CustomTrackingQuery> - Use this to track events that you define in your code activities.</span></span> <span data-ttu-id="d9c6a-165"><xref:System.Activities.Tracking.TrackingParticipant> 需要用该查询来订阅 <xref:System.Activities.Tracking.CustomTrackingRecord> 对象。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-165">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.CustomTrackingRecord> objects.</span></span>

  <span data-ttu-id="d9c6a-166">下面的示例演示使用 <xref:System.Activities.Tracking.CustomTrackingQuery> 订阅与自定义跟踪记录相关的记录所使用的配置和代码。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-166">The configuration and code used to subscribe to records related to custom tracking records using <xref:System.Activities.Tracking.CustomTrackingQuery> is shown in the following example.</span></span>

  ```xml
  <customTrackingQueries>
    <customTrackingQuery name="EmailAddress" activityName="SendEmailActivity" />
  </customTrackingQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new CustomTrackingQuery()
          {
              Name = "EmailAddress",
              ActivityName = "SendEmailActivity"
          }
      }
  };
  ```

- <span data-ttu-id="d9c6a-167"><xref:System.Activities.Tracking.BookmarkResumptionQuery> - 用于跟踪工作流实例中的书签恢复。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-167"><xref:System.Activities.Tracking.BookmarkResumptionQuery> - Use this to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="d9c6a-168"><xref:System.Activities.Tracking.TrackingParticipant> 需要用该查询来订阅 <xref:System.Activities.Tracking.BookmarkResumptionRecord> 对象。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-168">This query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.BookmarkResumptionRecord> objects.</span></span>

  <span data-ttu-id="d9c6a-169">下面的示例演示使用 <xref:System.Activities.Tracking.BookmarkResumptionQuery> 订阅与书签恢复相关的记录所使用的配置和代码。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-169">The configuration and code used to subscribe to records related to bookmark resumption using <xref:System.Activities.Tracking.BookmarkResumptionQuery> is shown in the following example.</span></span>

  ```xml
  <bookmarkResumptionQueries>
    <bookmarkResumptionQuery name="SentEmailBookmark" />
  </bookmarkResumptionQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new BookmarkResumptionQuery()
          {
              Name = "sentEmailBookmark"
          }
      }
  };
  ```

### <a name="annotations"></a><span data-ttu-id="d9c6a-170">批注</span><span class="sxs-lookup"><span data-stu-id="d9c6a-170">Annotations</span></span>

<span data-ttu-id="d9c6a-171">通过批注，可以使用可在生成时后配置的某个值任意标记跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-171">Annotations allow you to arbitrarily tag tracking records with a value that can be configured after build time.</span></span> <span data-ttu-id="d9c6a-172">例如，您可能希望多个工作流的多个跟踪记录都用 "Mail Server" = = "Mail Server1" 标记。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-172">For example, you might want several tracking records across several workflows to be tagged with "Mail Server" == "Mail Server1".</span></span> <span data-ttu-id="d9c6a-173">这样便于在以后查询跟踪记录时查找带有此标记的所有记录。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-173">This makes it easy to find all records with this tag when querying tracking records later.</span></span>

<span data-ttu-id="d9c6a-174">为此，可以在跟踪查询中添加一个批注，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-174">To accomplish this, an annotation is added to a tracking query as shown in the following example.</span></span>

```xml
<activityStateQuery activityName="SendEmailActivity">
  <states>
    <state name="Closed"/>
  </states>
  <annotations>
    <annotation name="MailServer" value="Mail Server1"/>
  </annotations>
</activityStateQuery>
```

### <a name="how-to-create-a-tracking-profile"></a><span data-ttu-id="d9c6a-175">如何创建跟踪配置文件</span><span class="sxs-lookup"><span data-stu-id="d9c6a-175">How to Create a Tracking Profile</span></span>

<span data-ttu-id="d9c6a-176">跟踪查询元素用于通过 XML 配置文件或代码创建跟踪配置文件 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-176">Tracking query elements are used to create a tracking profile using either an XML configuration file or [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] code.</span></span> <span data-ttu-id="d9c6a-177">以下是使用配置文件创建跟踪配置文件的示例。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-177">Here is an example of a tracking profile created using a configuration file.</span></span>

```xml
<system.serviceModel>
  <tracking>
    <profiles>
      <trackingProfile name="Sample Tracking Profile ">
        <workflow activityDefinitionId="*">
          <!--Specify the tracking profile query elements to subscribe for tracking records-->
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>
```

> [!WARNING]
> <span data-ttu-id="d9c6a-178">对于使用工作流服务主机的 WF，跟踪配置文件通常是使用配置文件创建的。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-178">For a WF using the Workflow service host, the tracking profile is typically created using a configuration file.</span></span> <span data-ttu-id="d9c6a-179">也可以通过代码使用跟踪配置文件和跟踪查询 API 来创建跟踪配置文件。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-179">It is also possible to create a tracking profile with code using the tracking profile and tracking query API.</span></span>

<span data-ttu-id="d9c6a-180">配置为 XML 配置文件的配置文件适用于使用行为扩展的跟踪参与者。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-180">A profile configured as an XML configuration file is applied to a tracking participant using a behavior extension.</span></span> <span data-ttu-id="d9c6a-181">这将添加到 WorkflowServiceHost，如后面的为 [工作流配置跟踪](configuring-tracking-for-a-workflow.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-181">This is added to a WorkflowServiceHost as described in the later section [Configuring Tracking for a Workflow](configuring-tracking-for-a-workflow.md).</span></span>

<span data-ttu-id="d9c6a-182">主机发出的跟踪记录的详细信息由跟踪配置文件中的配置设置确定。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-182">The verbosity of the tracking records emitted by the host is determined by configuration settings within the tracking profile.</span></span> <span data-ttu-id="d9c6a-183">跟踪参与者通过向跟踪配置文件添加查询来订阅跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-183">A tracking participant subscribes to tracking records by adding queries to a tracking profile.</span></span> <span data-ttu-id="d9c6a-184">若要订阅所有跟踪记录，跟踪配置文件需要 \* 在每个查询的名称字段中使用 "" 指定所有跟踪查询。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-184">To subscribe to all tracking records, the tracking profile needs to specify all tracking queries using "\*" in the name fields in each of the queries.</span></span>

<span data-ttu-id="d9c6a-185">下面是跟踪配置文件的一些常见示例。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-185">Here are some of the common examples of tracking profiles.</span></span>

- <span data-ttu-id="d9c6a-186">用于获取工作流实例记录和错误的跟踪配置文件。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-186">A tracking profile to obtain workflow instance records and faults.</span></span>

  ```xml
  <trackingProfile name="Instance and Fault Records">
    <workflow activityDefinitionId="*">
      <workflowInstanceQueries>
        <workflowInstanceQuery>
          <states>
            <state name="*" />
          </states>
        </workflowInstanceQuery>
      </workflowInstanceQueries>
      <activityStateQueries>
        <activityStateQuery activityName="*">
          <states>
            <state name="Faulted"/>
          </states>
        </activityStateQuery>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
  ```

- <span data-ttu-id="d9c6a-187">用于获取所有自定义跟踪记录的跟踪配置文件。</span><span class="sxs-lookup"><span data-stu-id="d9c6a-187">A tracking profile to obtain all custom tracking records.</span></span>

  ```xml
  <trackingProfile name="Instance_And_Custom_Records">
    <workflow activityDefinitionId="*">
      <customTrackingQueries>
        <customTrackingQuery name="*" activityName="*" />
      </customTrackingQueries>
    </workflow>
  </trackingProfile>
  ```

## <a name="see-also"></a><span data-ttu-id="d9c6a-188">请参阅</span><span class="sxs-lookup"><span data-stu-id="d9c6a-188">See also</span></span>

- [<span data-ttu-id="d9c6a-189">SQL 跟踪</span><span class="sxs-lookup"><span data-stu-id="d9c6a-189">SQL Tracking</span></span>](./samples/sql-tracking.md)
- <span data-ttu-id="d9c6a-190">[Windows Server App Fabric 监视](/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="d9c6a-190">[Windows Server App Fabric Monitoring](/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="d9c6a-191">[用 App Fabric 监视应用程序](/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="d9c6a-191">[Monitoring Applications with App Fabric](/previous-versions/appfabric/ee677276(v=azure.10))</span></span>
