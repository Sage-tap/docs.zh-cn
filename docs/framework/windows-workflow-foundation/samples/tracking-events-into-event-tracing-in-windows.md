---
description: 了解详细信息：在 Windows 中将事件跟踪到事件跟踪
title: 在 Windows 事件跟踪中跟踪事件
ms.date: 03/30/2017
ms.assetid: f812659b-0943-45ff-9430-4defa733182b
ms.openlocfilehash: 92ad4aaee100bb3ba7f4174bbbde1dc7eaed58de
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99653740"
---
# <a name="tracking-events-into-event-tracing-in-windows"></a><span data-ttu-id="6986a-103">在 Windows 事件跟踪中跟踪事件</span><span class="sxs-lookup"><span data-stu-id="6986a-103">Tracking Events into Event Tracing in Windows</span></span>

<span data-ttu-id="6986a-104">此示例演示如何在工作流服务上启用 Windows Workflow Foundation (WF) 跟踪，并在 Windows (ETW) 的事件跟踪中发出跟踪事件。</span><span class="sxs-lookup"><span data-stu-id="6986a-104">This sample demonstrates how to enable Windows Workflow Foundation (WF) tracking on a workflow service and emit the tracking events in Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="6986a-105">为了将工作流跟踪记录发到 ETW 中，该示例使用 ETW 跟踪参与者 (<xref:System.Activities.Tracking.EtwTrackingParticipant>)。</span><span class="sxs-lookup"><span data-stu-id="6986a-105">To emit workflow tracking records into ETW, the sample uses the ETW tracking participant (<xref:System.Activities.Tracking.EtwTrackingParticipant>).</span></span>

<span data-ttu-id="6986a-106">该示例中的工作流接收请求，将输入数据的倒数分配给输入变量，并将该倒数返回到客户端。</span><span class="sxs-lookup"><span data-stu-id="6986a-106">The workflow in the sample receives a request, assigns the reciprocal of the input data to the input variable and returns the reciprocal back to the client.</span></span> <span data-ttu-id="6986a-107">当输入数据为 0 时，会发生未处理的除数为零异常，从而导致工作流中止。</span><span class="sxs-lookup"><span data-stu-id="6986a-107">When the input data is 0, a divide by zero exception occurs that is unhandled that causes the workflow to abort.</span></span> <span data-ttu-id="6986a-108">启用了跟踪后，将向 ETW 发出错误跟踪记录，以后可帮助对错误进行故障排除。</span><span class="sxs-lookup"><span data-stu-id="6986a-108">With tracking enabled, the error track record is emitted to ETW, which can help troubleshoot the error later.</span></span> <span data-ttu-id="6986a-109">ETW 跟踪参与者通过跟踪配置文件配置为订阅跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="6986a-109">The ETW tracking participant is configured with a tracking profile to subscribe to tracking records.</span></span> <span data-ttu-id="6986a-110">跟踪配置文件在 Web.config 文件中定义，作为配置参数提供给 ETW 跟踪参与者。</span><span class="sxs-lookup"><span data-stu-id="6986a-110">The tracking profile is defined in the Web.config file and provided as a configuration parameter to the ETW tracking participant.</span></span> <span data-ttu-id="6986a-111">ETW 跟踪参与者在工作流服务的 Web.config 文件中配置，作为服务行为应用于服务。</span><span class="sxs-lookup"><span data-stu-id="6986a-111">The ETW tracking participant is configured in the Web.config file of the workflow service and is applied to the service as a service behavior.</span></span> <span data-ttu-id="6986a-112">在此示例中，使用事件查看器来查看事件日志中的跟踪事件。</span><span class="sxs-lookup"><span data-stu-id="6986a-112">In this sample, you view the tracking events in the event log using Event Viewer.</span></span>

## <a name="workflow-tracking-details"></a><span data-ttu-id="6986a-113">工作流跟踪详细信息</span><span class="sxs-lookup"><span data-stu-id="6986a-113">Workflow Tracking Details</span></span>

<span data-ttu-id="6986a-114">Windows Workflow Foundation 提供了跟踪基础结构，用于跟踪工作流实例的执行。</span><span class="sxs-lookup"><span data-stu-id="6986a-114">Windows Workflow Foundation provides a tracking infrastructure to track the execution of a workflow instance.</span></span> <span data-ttu-id="6986a-115">跟踪运行时会创建工作流实例以发出与工作流生命周期有关的事件、来自工作流活动的事件以及自定义事件。</span><span class="sxs-lookup"><span data-stu-id="6986a-115">The tracking runtime creates a workflow instance to emit events related to the workflow lifecycle, events from workflow activities and custom events.</span></span> <span data-ttu-id="6986a-116">下表详细介绍了跟踪基础结构的主要组件。</span><span class="sxs-lookup"><span data-stu-id="6986a-116">The following table details the primary components of the tracking infrastructure.</span></span>

|<span data-ttu-id="6986a-117">组件</span><span class="sxs-lookup"><span data-stu-id="6986a-117">Component</span></span>|<span data-ttu-id="6986a-118">说明</span><span class="sxs-lookup"><span data-stu-id="6986a-118">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="6986a-119">跟踪运行时</span><span class="sxs-lookup"><span data-stu-id="6986a-119">Tracking runtime</span></span>|<span data-ttu-id="6986a-120">提供基础结构以发出跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="6986a-120">Provides the infrastructure to emit tracking records.</span></span>|
|<span data-ttu-id="6986a-121">跟踪参与者</span><span class="sxs-lookup"><span data-stu-id="6986a-121">Tracking participants</span></span>|<span data-ttu-id="6986a-122">访问跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="6986a-122">Accesses the tracking records.</span></span> [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] <span data-ttu-id="6986a-123">附带了一个跟踪参与者，它作为 Windows 跟踪记录 (ETW) 事件写入跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="6986a-123">ships with a tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span>|
|<span data-ttu-id="6986a-124">跟踪配置文件</span><span class="sxs-lookup"><span data-stu-id="6986a-124">Tracking profile</span></span>|<span data-ttu-id="6986a-125">筛选机制，允许跟踪参与者订阅从工作流实例发出的跟踪记录的子集。</span><span class="sxs-lookup"><span data-stu-id="6986a-125">A filtering mechanism that allows a tracking participant to subscribe for a subset of the tracking records emitted from a workflow instance.</span></span>|

<span data-ttu-id="6986a-126">下表详细介绍工作流运行时发出的跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="6986a-126">The following table details the tracking records that the workflow runtime emits.</span></span>

|<span data-ttu-id="6986a-127">跟踪记录</span><span class="sxs-lookup"><span data-stu-id="6986a-127">Tracking record</span></span>|<span data-ttu-id="6986a-128">说明</span><span class="sxs-lookup"><span data-stu-id="6986a-128">Description</span></span>|
|---------------------|-----------------|
|<span data-ttu-id="6986a-129">工作流实例跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="6986a-129">Workflow instance tracking records.</span></span>|<span data-ttu-id="6986a-130">描述工作流实例的生命周期。</span><span class="sxs-lookup"><span data-stu-id="6986a-130">Describes the lifecycle of the workflow instance.</span></span> <span data-ttu-id="6986a-131">例如，当工作流启动或完成时发出一个实例记录。</span><span class="sxs-lookup"><span data-stu-id="6986a-131">For example, an instance record is emitted when the workflow starts or completes.</span></span>|
|<span data-ttu-id="6986a-132">活动状态跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="6986a-132">Activity state tracking records.</span></span>|<span data-ttu-id="6986a-133">详细说明活动执行情况。</span><span class="sxs-lookup"><span data-stu-id="6986a-133">Details activity execution.</span></span> <span data-ttu-id="6986a-134">这些记录指示工作流活动的状态，例如，当安排活动时、活动完成时或引发错误时。</span><span class="sxs-lookup"><span data-stu-id="6986a-134">These records indicate the state of a workflow activity such as when an activity is scheduled or when the activity completes or when a fault is thrown.</span></span>|
|<span data-ttu-id="6986a-135">书签恢复记录。</span><span class="sxs-lookup"><span data-stu-id="6986a-135">Bookmark resumption record.</span></span>|<span data-ttu-id="6986a-136">当恢复工作流实例中的书签时发出。</span><span class="sxs-lookup"><span data-stu-id="6986a-136">Emitted whenever a bookmark within a workflow instance is resumed.</span></span>|
|<span data-ttu-id="6986a-137">自定义跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="6986a-137">Custom tracking records.</span></span>|<span data-ttu-id="6986a-138">工作流作者可以在自定义活动中创建并发出自定义跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="6986a-138">A workflow author can create custom tracking records and emit them within the custom activity.</span></span>|
|<xref:System.Activities.Tracking.ActivityScheduledRecord>|<span data-ttu-id="6986a-139">当某个活动安排其他活动时会发出此记录。</span><span class="sxs-lookup"><span data-stu-id="6986a-139">This record is emitted when an activity schedules another activity.</span></span>|
|<xref:System.Activities.Tracking.FaultPropagationRecord>|<span data-ttu-id="6986a-140">当从某个活动传播错误时会发出此记录。</span><span class="sxs-lookup"><span data-stu-id="6986a-140">This record is emitted when a fault is propagated from an activity.</span></span>|
|<xref:System.Activities.Tracking.CancelRequestedRecord>|<span data-ttu-id="6986a-141">当某个活动由其他活动取消时会发出此记录。</span><span class="sxs-lookup"><span data-stu-id="6986a-141">This record is emitted when an activity is canceled by another activity.</span></span>|

<span data-ttu-id="6986a-142">跟踪参与者使用跟踪配置文件来订阅发出的跟踪记录的子集。</span><span class="sxs-lookup"><span data-stu-id="6986a-142">The tracking participant subscribes for a subset of the emitted tracking records using tracking profiles.</span></span> <span data-ttu-id="6986a-143">跟踪配置文件包含允许订阅特定跟踪记录类型的跟踪查询。</span><span class="sxs-lookup"><span data-stu-id="6986a-143">A tracking profile contains tracking queries that allow subscribing for a particular tracking record type.</span></span> <span data-ttu-id="6986a-144">可以在代码或配置中指定跟踪配置文件。</span><span class="sxs-lookup"><span data-stu-id="6986a-144">Tracking profiles can be specified in code or in configuration.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="6986a-145">使用此示例</span><span class="sxs-lookup"><span data-stu-id="6986a-145">To use this sample</span></span>

1. <span data-ttu-id="6986a-146">使用 Visual Studio 2010 打开 EtwTrackingParticipantSample 解决方案文件。</span><span class="sxs-lookup"><span data-stu-id="6986a-146">Using Visual Studio 2010, open the EtwTrackingParticipantSample.sln solution file.</span></span>

2. <span data-ttu-id="6986a-147">要生成解决方案，按 Ctrl+Shift+B。</span><span class="sxs-lookup"><span data-stu-id="6986a-147">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="6986a-148">若要运行解决方案，请按 F5。</span><span class="sxs-lookup"><span data-stu-id="6986a-148">To run the solution, press F5.</span></span>

    <span data-ttu-id="6986a-149">默认情况下，该服务正在侦听端口 53797 (`http://localhost:53797/SampleWorkflowService.xamlx`) 。</span><span class="sxs-lookup"><span data-stu-id="6986a-149">By default, the service is listening on port 53797 (`http://localhost:53797/SampleWorkflowService.xamlx`).</span></span>

4. <span data-ttu-id="6986a-150">使用文件资源管理器打开 WCF 测试客户端。</span><span class="sxs-lookup"><span data-stu-id="6986a-150">Using File Explorer, open the WCF test client.</span></span>

    <span data-ttu-id="6986a-151"> ( # A0) 的 WCF 测试客户端位于 \<Visual Studio 2010 installation folder> \Common7\IDE\ 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="6986a-151">The WCF test client (WcfTestClient.exe) is located in the \<Visual Studio 2010 installation folder>\Common7\IDE\ folder.</span></span>

    <span data-ttu-id="6986a-152">默认 Visual Studio 2010 安装文件夹为 C:\Program Files\Microsoft Visual Studio 10.0。</span><span class="sxs-lookup"><span data-stu-id="6986a-152">The default Visual Studio 2010 installation folder is C:\Program Files\Microsoft Visual Studio 10.0.</span></span>

5. <span data-ttu-id="6986a-153">在 WCF 测试客户端中，从 "**文件**" 菜单中选择 "**添加服务**"。</span><span class="sxs-lookup"><span data-stu-id="6986a-153">In WCF test client, select **Add Service** from the **File** menu.</span></span>

    <span data-ttu-id="6986a-154">在输入框中添加终结点地址。</span><span class="sxs-lookup"><span data-stu-id="6986a-154">Add the endpoint address in the input box.</span></span> <span data-ttu-id="6986a-155">默认值为 `http://localhost:53797/SampleWorkflowService.xamlx`。</span><span class="sxs-lookup"><span data-stu-id="6986a-155">The default is `http://localhost:53797/SampleWorkflowService.xamlx`.</span></span>

6. <span data-ttu-id="6986a-156">打开事件查看器应用程序。</span><span class="sxs-lookup"><span data-stu-id="6986a-156">Open the Event Viewer application.</span></span>

    <span data-ttu-id="6986a-157">在调用服务之前事件查看器，从 " **开始** " 菜单中选择 " **运行** "，然后键入 `eventvwr.exe` 。</span><span class="sxs-lookup"><span data-stu-id="6986a-157">Before invoking the service, start Event Viewer from the **Start** menu, select **Run** and type in `eventvwr.exe`.</span></span> <span data-ttu-id="6986a-158">确保事件日志正在侦听从工作流服务发出的跟踪事件。</span><span class="sxs-lookup"><span data-stu-id="6986a-158">Ensure that the event log is listening for tracking events emitted from the workflow service.</span></span>

7. <span data-ttu-id="6986a-159">在事件查看器的树视图中，导航到 " **事件查看器**"、" **应用程序和服务日志**" 和 " **Microsoft**"。</span><span class="sxs-lookup"><span data-stu-id="6986a-159">In the tree view of the Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, and **Microsoft**.</span></span> <span data-ttu-id="6986a-160">右键单击 " **Microsoft** " 并选择 "查看"，然后选择 " **查看** 和 **调试日志** " 以启用分析日志和调试日志</span><span class="sxs-lookup"><span data-stu-id="6986a-160">Right-click **Microsoft** and select **View** and then **Show Analytic and Debug Logs** to enable the analytic and debug logs</span></span>

    <span data-ttu-id="6986a-161">确保选中 " **显示分析和调试日志** " 选项。</span><span class="sxs-lookup"><span data-stu-id="6986a-161">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>

8. <span data-ttu-id="6986a-162">在事件查看器中的树视图中，导航到 " **事件查看器**"、" **应用程序和服务日志**"、" **Microsoft**"、" **Windows**"、" **应用程序服务器**"</span><span class="sxs-lookup"><span data-stu-id="6986a-162">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="6986a-163">右键单击 " **分析** "，然后选择 " **启用日志** " 以启用 **分析** 日志。</span><span class="sxs-lookup"><span data-stu-id="6986a-163">Right-click **Analytic** and select **Enable Log** to enable the **Analytic** log.</span></span>

9. <span data-ttu-id="6986a-164">通过双击 `GetData`，使用 WCF 测试客户端测试服务。</span><span class="sxs-lookup"><span data-stu-id="6986a-164">Test the service using the WCF test client by double-clicking `GetData`.</span></span>

    <span data-ttu-id="6986a-165">这会打开 `GetData` 方法。</span><span class="sxs-lookup"><span data-stu-id="6986a-165">This opens the `GetData` method.</span></span> <span data-ttu-id="6986a-166">请求接受一个参数，并确保值为 0（默认值）。</span><span class="sxs-lookup"><span data-stu-id="6986a-166">The request accepts one parameter and ensures that the value is 0, which is the default.</span></span>

     <span data-ttu-id="6986a-167">单击 " **调用**"。</span><span class="sxs-lookup"><span data-stu-id="6986a-167">Click **Invoke**.</span></span>

10. <span data-ttu-id="6986a-168">观察从工作流发出的事件。</span><span class="sxs-lookup"><span data-stu-id="6986a-168">Observe the events emitted from the workflow.</span></span>

    <span data-ttu-id="6986a-169">切换回事件查看器，导航到 **事件查看器**、 **应用程序和服务日志**、 **Microsoft**、 **Windows**、 **应用程序服务器应用程序**。</span><span class="sxs-lookup"><span data-stu-id="6986a-169">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="6986a-170">右键单击 " **分析** "，然后选择 " **刷新**"。</span><span class="sxs-lookup"><span data-stu-id="6986a-170">Right-click **Analytic** and select **Refresh**.</span></span>

    <span data-ttu-id="6986a-171">事件查看器中会显示工作流事件。</span><span class="sxs-lookup"><span data-stu-id="6986a-171">The workflow events are displayed in the event viewer.</span></span> <span data-ttu-id="6986a-172">请注意，会显示工作流执行事件，并且其中一个事件是对应于工作流中的错误的未处理异常。</span><span class="sxs-lookup"><span data-stu-id="6986a-172">Notice that workflow execution events are displayed and that one of them is an unhandled exception that corresponds to the error in workflow.</span></span> <span data-ttu-id="6986a-173">此外，还会从工作流活动发出一个警告事件，指示活动正引发错误。</span><span class="sxs-lookup"><span data-stu-id="6986a-173">Also, a warning event is emitted from the workflow activity, which indicates that the activity is throwing a fault.</span></span>

11. <span data-ttu-id="6986a-174">通过输入不为 0 的数据来重复步骤 9 和 10，以便不会引发错误。</span><span class="sxs-lookup"><span data-stu-id="6986a-174">Repeat steps 9 and 10 with an input of data other than 0, so that no error is thrown.</span></span>

<span data-ttu-id="6986a-175">通过跟踪配置文件，可以订阅运行时在工作流实例的状态发生更改时发出的事件。</span><span class="sxs-lookup"><span data-stu-id="6986a-175">Tracking profiles allow you to subscribe to events that are emitted by the runtime when the state of a workflow instance changes.</span></span> <span data-ttu-id="6986a-176">根据监视需求，可以创建一个非常粗陋的配置文件，用于订阅对工作流进行的一小组高级状态更改。</span><span class="sxs-lookup"><span data-stu-id="6986a-176">Depending on your monitoring requirements, you can create a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="6986a-177">另一方面，可以创建一个非常精确的配置文件，其输出足够丰富，可在以后重新构造执行。</span><span class="sxs-lookup"><span data-stu-id="6986a-177">On the other hand, you can create a very precise profile whose output is rich enough to reconstruct the execution later.</span></span> <span data-ttu-id="6986a-178">该示例使用发出一小组事件的 `HealthMonitoring Tracking Profile`，演示从工作流运行时向 ETW 发出的事件。</span><span class="sxs-lookup"><span data-stu-id="6986a-178">The sample demonstrates the events emitted from the workflow runtime to ETW using the `HealthMonitoring Tracking Profile`, which emits a small set of events.</span></span> <span data-ttu-id="6986a-179">Web.config 中还提供了另一个发出更多工作流跟踪事件的配置文件，该文件名为 `Troubleshooting Tracking Profile`。</span><span class="sxs-lookup"><span data-stu-id="6986a-179">A different profile that emits more workflow tracking events is also provided in the Web.config that is named `Troubleshooting Tracking Profile`.</span></span> <span data-ttu-id="6986a-180">安装 [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] 时，会在 Machine.config 文件中配置一个具有空名称的默认配置文件。</span><span class="sxs-lookup"><span data-stu-id="6986a-180">When the [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] is installed, a default profile with an empty name is configured in the Machine.config file.</span></span> <span data-ttu-id="6986a-181">当未指定配置文件名称或指定了空配置文件名称时，此配置文件由 ETW 跟踪行为配置使用。</span><span class="sxs-lookup"><span data-stu-id="6986a-181">This profile is used by the ETW tracking behavior configuration when no profile name or an empty profile name is specified.</span></span>

<span data-ttu-id="6986a-182">运行状况监视跟踪配置文件发出工作流实例记录和活动错误传播记录。</span><span class="sxs-lookup"><span data-stu-id="6986a-182">The health monitoring tracking profile emits workflow instance records and activity fault propagation records.</span></span> <span data-ttu-id="6986a-183">通过将以下跟踪配置文件添加到 Web.config 配置文件来创建此配置文件。</span><span class="sxs-lookup"><span data-stu-id="6986a-183">This profile is created by adding the following tracking profile to a Web.config configuration file.</span></span>

```xml
<tracking>
  <profiles>
    <trackingProfile name="HealthMonitoring Tracking Profile">
      <workflow activityDefinitionId="*">
        <workflowInstanceQueries>
          <workflowInstanceQuery>
            <states>
              <state name="Started"/>
              <state name="Completed"/>
              <state name="Aborted"/>
              <state name="UnhandledException"/>
            </states>
          </workflowInstanceQuery>
        </workflowInstanceQueries>
        <faultPropagationQueries>
          <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>
        </faultPropagationQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```

 <span data-ttu-id="6986a-184">可以通过将 `EtwTrackingParticipant` 配置更改为以下内容来更改该配置文件。</span><span class="sxs-lookup"><span data-stu-id="6986a-184">The profile can be changed by changing the `EtwTrackingParticipant` configuration to the following.</span></span>

```xml
<behaviors>
  <serviceBehaviors>
    <behavior>
      <etwTracking profileName="HealthMonitoring Tracking Profile"/>
    </behavior>
  </serviceBehaviors>
</behaviors>
```

#### <a name="to-clean-up-optional"></a><span data-ttu-id="6986a-185">清理（可选）</span><span class="sxs-lookup"><span data-stu-id="6986a-185">To clean up (Optional)</span></span>

1. <span data-ttu-id="6986a-186">打开事件查看器。</span><span class="sxs-lookup"><span data-stu-id="6986a-186">Open Event Viewer.</span></span>

2. <span data-ttu-id="6986a-187">导航到 **事件查看器**、 **应用程序和服务日志**、 **Microsoft**、 **Windows**、 **应用程序服务器应用程序**。</span><span class="sxs-lookup"><span data-stu-id="6986a-187">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="6986a-188">右键单击 " **分析** "，然后选择 " **禁用日志**"。</span><span class="sxs-lookup"><span data-stu-id="6986a-188">Right-click **Analytic** and select **Disable Log**.</span></span>

3. <span data-ttu-id="6986a-189">导航到 **事件查看器**、 **应用程序和服务日志**、 **Microsoft**、 **Windows**、 **应用程序服务器应用程序**。</span><span class="sxs-lookup"><span data-stu-id="6986a-189">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="6986a-190">右键单击 " **分析** "，然后选择 " **清除日志**"。</span><span class="sxs-lookup"><span data-stu-id="6986a-190">Right-click **Analytic** and select **Clear Log**.</span></span>

4. <span data-ttu-id="6986a-191">选择 " **清除** " 选项可清除事件。</span><span class="sxs-lookup"><span data-stu-id="6986a-191">Choose the **Clear** option to clear the events.</span></span>

## <a name="known-issue"></a><span data-ttu-id="6986a-192">已知问题</span><span class="sxs-lookup"><span data-stu-id="6986a-192">Known Issue</span></span>

> [!NOTE]
> <span data-ttu-id="6986a-193">事件查看器中存在一个已知问题，即可能无法解码 ETW 事件。</span><span class="sxs-lookup"><span data-stu-id="6986a-193">There is a known issue in the Event Viewer where it may fail to decode ETW events.</span></span> <span data-ttu-id="6986a-194">您可能会看到与下面类似的错误消息。</span><span class="sxs-lookup"><span data-stu-id="6986a-194">You may see an error message that looks like the following.</span></span>
>
> <span data-ttu-id="6986a-195">\<id>找不到来自源 Microsoft-Windows-应用程序 Server-Applications 的事件 ID 的描述。</span><span class="sxs-lookup"><span data-stu-id="6986a-195">The description for Event ID \<id> from source Microsoft-Windows-Application Server-Applications cannot be found.</span></span> <span data-ttu-id="6986a-196">未在本地计算机上安装引发此事件的组件，或者安装已损坏。</span><span class="sxs-lookup"><span data-stu-id="6986a-196">Either the component that raises this event is not installed on your local computer or the installation is corrupted.</span></span> <span data-ttu-id="6986a-197">可在本地计算机上安装或修复该组件。</span><span class="sxs-lookup"><span data-stu-id="6986a-197">You can install or repair the component on the local computer.</span></span>
>
> <span data-ttu-id="6986a-198">如果遇到此错误，请在操作窗格中单击“刷新”。</span><span class="sxs-lookup"><span data-stu-id="6986a-198">If you encounter this error, click refresh in the actions pane.</span></span> <span data-ttu-id="6986a-199">事件现在应能正确解码。</span><span class="sxs-lookup"><span data-stu-id="6986a-199">The event should now decode properly.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6986a-200">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="6986a-200">The samples may already be installed on your computer.</span></span> <span data-ttu-id="6986a-201">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="6986a-201">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="6986a-202">如果此目录不存在，请参阅[Windows Communication Foundation (wcf) ，并 Windows Workflow Foundation (的 WF](https://www.microsoft.com/download/details.aspx?id=21459)) .NET Framework Windows Communication Foundation ([!INCLUDE[wf1](../../../../includes/wf1-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6986a-202">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6986a-203">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="6986a-203">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\EtwTracking`

## <a name="see-also"></a><span data-ttu-id="6986a-204">请参阅</span><span class="sxs-lookup"><span data-stu-id="6986a-204">See also</span></span>

- <span data-ttu-id="6986a-205">[AppFabric 监视示例](/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="6986a-205">[AppFabric Monitoring Samples](/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
