---
description: 了解详细信息：如何：创建自定义跟踪参与者
title: 如何：创建自定义跟踪参与者
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b612c7e-2381-4a7c-b07a-77030415f2a3
ms.openlocfilehash: 8b435ac110d286d0582700289079459cca3cf979
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99777835"
---
# <a name="how-to-create-a-custom-tracking-participant"></a><span data-ttu-id="f79d4-103">如何：创建自定义跟踪参与者</span><span class="sxs-lookup"><span data-stu-id="f79d4-103">How to: Create a Custom Tracking Participant</span></span>

<span data-ttu-id="f79d4-104">工作流跟踪用于查看工作流执行的状态。</span><span class="sxs-lookup"><span data-stu-id="f79d4-104">Workflow tracking provides visibility into the status of workflow execution.</span></span> <span data-ttu-id="f79d4-105">工作流运行时发出跟踪记录，这些跟踪记录描述工作流生命周期事件、活动生命周期事件、书签摘要和故障。</span><span class="sxs-lookup"><span data-stu-id="f79d4-105">The workflow runtime emits tracking records that describe workflow lifecycle events, activity lifecycle events, bookmark resumptions, and faults.</span></span> <span data-ttu-id="f79d4-106">这些跟踪记录供跟踪参与者使用。</span><span class="sxs-lookup"><span data-stu-id="f79d4-106">These tracking records are consumed by tracking participants.</span></span> <span data-ttu-id="f79d4-107">Windows Workflow Foundation (WF) 包括一个标准跟踪参与者，该参与者将跟踪记录作为 Windows (ETW) 事件的事件跟踪来写入。</span><span class="sxs-lookup"><span data-stu-id="f79d4-107">Windows Workflow Foundation (WF) includes a standard tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span> <span data-ttu-id="f79d4-108">如果这不能满足您的需求，您还可以编写自定义跟踪参与者。</span><span class="sxs-lookup"><span data-stu-id="f79d4-108">If that does not meet your requirements, you can also write a custom tracking participant.</span></span> <span data-ttu-id="f79d4-109">本教程步骤说明如何创建自定义跟踪参与者和跟踪配置文件，该配置文件捕获 `WriteLine` 活动的输出，以便将这些活动显示给用户。</span><span class="sxs-lookup"><span data-stu-id="f79d4-109">This tutorial step describes how to create a custom tracking participant and tracking profile that capture the output of `WriteLine` activities so that they can be displayed to the user.</span></span>  
  
## <a name="to-create-the-custom-tracking-participant"></a><span data-ttu-id="f79d4-110">创建自定义跟踪参与者</span><span class="sxs-lookup"><span data-stu-id="f79d4-110">To create the custom tracking participant</span></span>  
  
1. <span data-ttu-id="f79d4-111">在 **解决方案资源管理器** 中右键单击 " **NumberGuessWorkflowHost** "，然后选择 "**添加**"、"**类**"。</span><span class="sxs-lookup"><span data-stu-id="f79d4-111">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **Class**.</span></span> <span data-ttu-id="f79d4-112">`StatusTrackingParticipant`在 "**名称**" 框中键入，然后单击 "**添加**"。</span><span class="sxs-lookup"><span data-stu-id="f79d4-112">Type `StatusTrackingParticipant` into the **Name** box, and click **Add**.</span></span>  
  
2. <span data-ttu-id="f79d4-113">在包含其他 `using`（或 `Imports`）语句的文件的顶部添加以下 `using`（或 `Imports`）语句。</span><span class="sxs-lookup"><span data-stu-id="f79d4-113">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Activities.Tracking  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    using System.IO;  
    ```  
  
3. <span data-ttu-id="f79d4-114">修改 `StatusTrackingParticipant` 类，使它从 `TrackingParticipant` 继承。</span><span class="sxs-lookup"><span data-stu-id="f79d4-114">Modify the `StatusTrackingParticipant` class so that it inherits from `TrackingParticipant`.</span></span>  
  
    ```vb  
    Public Class StatusTrackingParticipant  
        Inherits TrackingParticipant  
  
    End Class  
    ```  
  
    ```csharp  
    class StatusTrackingParticipant : TrackingParticipant  
    {  
    }  
    ```  
  
4. <span data-ttu-id="f79d4-115">添加以下 `Track` 方法重写。</span><span class="sxs-lookup"><span data-stu-id="f79d4-115">Add the following `Track` method override.</span></span> <span data-ttu-id="f79d4-116">有多种不同类型的跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="f79d4-116">There are several different types of tracking records.</span></span> <span data-ttu-id="f79d4-117">我们对 `WriteLine` 活动的输出十分感兴趣，这些活动包含在活动跟踪记录中。</span><span class="sxs-lookup"><span data-stu-id="f79d4-117">We are interested in the output of `WriteLine` activities, which are contained in activity tracking records.</span></span> <span data-ttu-id="f79d4-118">如果 `TrackingRecord` 为 `ActivityTrackingRecord` 活动的 `WriteLine`，则 `Text` 的 `WriteLine` 将附加到工作流 `InstanceId` 后面的指定文件。</span><span class="sxs-lookup"><span data-stu-id="f79d4-118">If the `TrackingRecord` is an `ActivityTrackingRecord` for a `WriteLine` activity, the `Text` of the `WriteLine` is appended to a file named after the `InstanceId` of the workflow.</span></span> <span data-ttu-id="f79d4-119">在本教程中，该文件将保存到宿主应用程序的当前文件夹中。</span><span class="sxs-lookup"><span data-stu-id="f79d4-119">In this tutorial, the file is saved to the current folder of the host application.</span></span>  
  
    ```vb  
    Protected Overrides Sub Track(record As TrackingRecord, timeout As TimeSpan)  
        Dim asr As ActivityStateRecord = TryCast(record, ActivityStateRecord)  
  
        If Not asr Is Nothing Then  
            If asr.State = ActivityStates.Executing And _  
            asr.Activity.TypeName = "System.Activities.Statements.WriteLine" Then  
  
                'Append the WriteLine output to the tracking  
                'file for this instance.  
                Using writer As StreamWriter = File.AppendText(record.InstanceId.ToString())  
                    writer.WriteLine(asr.Arguments("Text"))  
                    writer.Close()  
                End Using  
            End If  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    protected override void Track(TrackingRecord record, TimeSpan timeout)  
    {  
        ActivityStateRecord asr = record as ActivityStateRecord;  
  
        if (asr != null)  
        {  
            if (asr.State == ActivityStates.Executing &&  
                asr.Activity.TypeName == "System.Activities.Statements.WriteLine")  
            {  
                // Append the WriteLine output to the tracking  
                // file for this instance  
                using (StreamWriter writer = File.AppendText(record.InstanceId.ToString()))  
                {  
                    writer.WriteLine(asr.Arguments["Text"]);  
                    writer.Close();  
                }  
            }  
        }  
    }  
    ```  
  
     <span data-ttu-id="f79d4-120">未指定跟踪配置文件时，使用默认跟踪配置文件。</span><span class="sxs-lookup"><span data-stu-id="f79d4-120">When no tracking profile is specified, the default tracking profile is used.</span></span> <span data-ttu-id="f79d4-121">使用默认跟踪配置文件时，将为所有 `ActivityStates` 发出跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="f79d4-121">When the default tracking profile is used, tracking records are emitted for all `ActivityStates`.</span></span> <span data-ttu-id="f79d4-122">因为我们只需在 `WriteLine` 活动的生命周期内捕获一次文本，所以我们仅从 `ActivityStates.Executing` 状态捕获文本。</span><span class="sxs-lookup"><span data-stu-id="f79d4-122">Because we only need to capture the text one time during the lifecycle of the `WriteLine` activity, we only extract the text from the `ActivityStates.Executing` state.</span></span> <span data-ttu-id="f79d4-123">在中， [创建跟踪配置文件并注册跟踪参与者](#to-create-the-tracking-profile-and-register-the-tracking-participant)，将创建一个跟踪配置文件，该配置文件指定仅 `WriteLine` `ActivityStates.Executing` 发出跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="f79d4-123">In [To create the tracking profile and register the tracking participant](#to-create-the-tracking-profile-and-register-the-tracking-participant), a tracking profile is created that specifies that only `WriteLine` `ActivityStates.Executing` tracking records are emitted.</span></span>  
  
## <a name="to-create-the-tracking-profile-and-register-the-tracking-participant"></a><span data-ttu-id="f79d4-124">创建跟踪配置文件并注册跟踪参与者</span><span class="sxs-lookup"><span data-stu-id="f79d4-124">To create the tracking profile and register the tracking participant</span></span>  
  
1. <span data-ttu-id="f79d4-125">在 **解决方案资源管理器** 中右键单击 " **WorkflowHostForm** "，然后选择 "**查看代码**"。</span><span class="sxs-lookup"><span data-stu-id="f79d4-125">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>  
  
2. <span data-ttu-id="f79d4-126">在包含其他 `using`（或 `Imports`）语句的文件的顶部添加以下 `using`（或 `Imports`）语句。</span><span class="sxs-lookup"><span data-stu-id="f79d4-126">Add the following `using` (or `Imports`) statement at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Activities.Tracking  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    ```  
  
3. <span data-ttu-id="f79d4-127">将以下代码添加到 `ConfigureWorkflowApplication`，紧接在将 `StringWriter` 添加到工作流扩展的代码之后和工作流生命周期处理程序之前。</span><span class="sxs-lookup"><span data-stu-id="f79d4-127">Add the following code to `ConfigureWorkflowApplication` just after the code that adds the `StringWriter` to the workflow extensions and before the workflow lifecycle handlers.</span></span>  
  
    ```vb  
    'Add the custom tracking participant with a tracking profile  
    'that only emits tracking records for WriteLine activities.  
    Dim query As New ActivityStateQuery()  
    query.ActivityName = "WriteLine"  
    query.States.Add(ActivityStates.Executing)  
    query.Arguments.Add("Text")  
  
    Dim profile As New TrackingProfile()  
    profile.Queries.Add(query)  
  
    Dim stp As New StatusTrackingParticipant()  
    stp.TrackingProfile = profile  
  
    wfApp.Extensions.Add(stp)  
    ```  
  
    ```csharp  
    // Add the custom tracking participant with a tracking profile  
    // that only emits tracking records for WriteLine activities.  
    StatusTrackingParticipant stp = new StatusTrackingParticipant  
    {  
        TrackingProfile = new TrackingProfile  
        {  
            Queries =
            {  
                new ActivityStateQuery  
                {  
                    ActivityName = "WriteLine",  
                    States = { ActivityStates.Executing },  
                    Arguments = { "Text" }  
                }  
            }  
        }  
    };  
  
    wfApp.Extensions.Add(stp);  
    ```  
  
     <span data-ttu-id="f79d4-128">此跟踪配置文件指定仅向自定义跟踪参与者发出处于 `WriteLine` 状态的 `Executing` 活动的活动状态记录。</span><span class="sxs-lookup"><span data-stu-id="f79d4-128">This tracking profile specifies that only activity state records for `WriteLine` activities in the `Executing` state are emitted to the custom tracking participant.</span></span>  
  
     <span data-ttu-id="f79d4-129">在添加代码后，`ConfigureWorkflowApplication` 的开头将类似于以下示例。</span><span class="sxs-lookup"><span data-stu-id="f79d4-129">After adding the code, the start of `ConfigureWorkflowApplication` will look like the following example.</span></span>  
  
    ```vb  
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)  
        'Configure the persistence store.  
        wfApp.InstanceStore = store  
  
        'Add a StringWriter to the extensions. This captures the output  
        'from the WriteLine activities so we can display it in the form.  
        Dim sw As New StringWriter()  
        wfApp.Extensions.Add(sw)  
  
        'Add the custom tracking participant with a tracking profile  
        'that only emits tracking records for WriteLine activities.  
        Dim query As New ActivityStateQuery()  
        query.ActivityName = "WriteLine"  
        query.States.Add(ActivityStates.Executing)  
        query.Arguments.Add("Text")  
  
        Dim profile As New TrackingProfile()  
        profile.Queries.Add(query)  
  
        Dim stp As New StatusTrackingParticipant()  
        stp.TrackingProfile = profile  
  
        wfApp.Extensions.Add(stp)  
  
        'Workflow lifecycle handlers...  
    ```  
  
    ```csharp  
    private void ConfigureWorkflowApplication(WorkflowApplication wfApp)  
    {  
        // Configure the persistence store.  
        wfApp.InstanceStore = store;  
  
        // Add a StringWriter to the extensions. This captures the output  
        // from the WriteLine activities so we can display it in the form.  
        StringWriter sw = new StringWriter();  
        wfApp.Extensions.Add(sw);  
  
        // Add the custom tracking participant with a tracking profile  
        // that only emits tracking records for WriteLine activities.  
        StatusTrackingParticipant stp = new StatusTrackingParticipant  
        {  
            TrackingProfile = new TrackingProfile  
            {  
                Queries =
                {  
                    new ActivityStateQuery  
                    {  
                        ActivityName = "WriteLine",  
                        States = { ActivityStates.Executing },  
                        Arguments = { "Text" }  
                    }  
                }  
            }  
        };  
  
        wfApp.Extensions.Add(stp);  
  
        // Workflow lifecycle handlers...  
    ```  
  
## <a name="to-display-the-tracking-information"></a><span data-ttu-id="f79d4-130">显示跟踪信息</span><span class="sxs-lookup"><span data-stu-id="f79d4-130">To display the tracking information</span></span>  
  
1. <span data-ttu-id="f79d4-131">在 **解决方案资源管理器** 中右键单击 " **WorkflowHostForm** "，然后选择 "**查看代码**"。</span><span class="sxs-lookup"><span data-stu-id="f79d4-131">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>  
  
2. <span data-ttu-id="f79d4-132">在 `InstanceId_SelectedIndexChanged` 处理程序中，添加以下代码，紧接在清除状态窗口的代码之后。</span><span class="sxs-lookup"><span data-stu-id="f79d4-132">In the `InstanceId_SelectedIndexChanged` handler, add the following code immediately after the code that clears the status window.</span></span>  
  
    ```vb  
    'If there is tracking data for this workflow, display it  
    'in the status window.  
    If File.Exists(WorkflowInstanceId.ToString()) Then  
        Dim status As String = File.ReadAllText(WorkflowInstanceId.ToString())  
        UpdateStatus(status)  
    End If  
    ```  
  
    ```csharp  
    // If there is tracking data for this workflow, display it  
    // in the status window.  
    if (File.Exists(WorkflowInstanceId.ToString()))  
    {  
        string status = File.ReadAllText(WorkflowInstanceId.ToString());  
        UpdateStatus(status);  
    }  
    ```  
  
     <span data-ttu-id="f79d4-133">在工作流列表中选择新工作流后，将加载该工作流的跟踪记录并将其显示在状态窗口中。</span><span class="sxs-lookup"><span data-stu-id="f79d4-133">When a new workflow is selected in the workflow list, the tracking records for that workflow are loaded and displayed in the status window.</span></span> <span data-ttu-id="f79d4-134">以下示例是完成的 `InstanceId_SelectedIndexChanged` 处理程序。</span><span class="sxs-lookup"><span data-stu-id="f79d4-134">The following example is the completed `InstanceId_SelectedIndexChanged` handler.</span></span>  
  
    ```vb  
    Private Sub InstanceId_SelectedIndexChanged(sender As Object, e As EventArgs) Handles InstanceId.SelectedIndexChanged  
        If InstanceId.SelectedIndex = -1 Then  
            Return  
        End If  
  
        'Clear the status window.  
        WorkflowStatus.Clear()  
  
        'If there is tracking data for this workflow, display it  
        'in the status window.  
        If File.Exists(WorkflowInstanceId.ToString()) Then  
            Dim status As String = File.ReadAllText(WorkflowInstanceId.ToString())  
            UpdateStatus(status)  
        End If  
  
        'Get the workflow version and display it.  
        'If the workflow is just starting then this info will not  
        'be available in the persistence store so do not try and retrieve it.  
        If Not WorkflowStarting Then  
            Dim instance As WorkflowApplicationInstance = _  
                WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
            WorkflowVersion.Text = _  
                WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity)  
  
            'Unload the instance.  
            instance.Abandon()  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private void InstanceId_SelectedIndexChanged(object sender, EventArgs e)  
    {  
        if (InstanceId.SelectedIndex == -1)  
        {  
            return;  
        }  
  
        // Clear the status window.  
        WorkflowStatus.Clear();  
  
        // If there is tracking data for this workflow, display it  
        // in the status window.  
        if (File.Exists(WorkflowInstanceId.ToString()))  
        {  
            string status = File.ReadAllText(WorkflowInstanceId.ToString());  
            UpdateStatus(status);  
        }  
  
        // Get the workflow version and display it.  
        // If the workflow is just starting then this info will not  
        // be available in the persistence store so do not try and retrieve it.  
        if (!WorkflowStarting)  
        {  
            WorkflowApplicationInstance instance =  
                WorkflowApplication.GetInstance(this.WorkflowInstanceId, store);  
  
            WorkflowVersion.Text =  
                WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity);  
  
            // Unload the instance.  
            instance.Abandon();  
        }  
    }  
    ```  
  
## <a name="to-build-and-run-the-application"></a><span data-ttu-id="f79d4-135">生成并运行应用程序</span><span class="sxs-lookup"><span data-stu-id="f79d4-135">To build and run the application</span></span>  
  
1. <span data-ttu-id="f79d4-136">按 Ctrl+Shift+B 生成应用程序。</span><span class="sxs-lookup"><span data-stu-id="f79d4-136">Press Ctrl+Shift+B to build the application.</span></span>  
  
2. <span data-ttu-id="f79d4-137">按 Ctrl+F5 启动应用程序。</span><span class="sxs-lookup"><span data-stu-id="f79d4-137">Press Ctrl+F5 to start the application.</span></span>  
  
3. <span data-ttu-id="f79d4-138">为推测游戏选择一个范围，并选择要启动的工作流类型，然后单击 " **新建游戏**"。</span><span class="sxs-lookup"><span data-stu-id="f79d4-138">Select a range for the guessing game and the type of workflow to start, and click **New Game**.</span></span> <span data-ttu-id="f79d4-139">在 **推测** 框中输入推测，然后单击 " **开始** " 以提交推测。</span><span class="sxs-lookup"><span data-stu-id="f79d4-139">Enter a guess in the **Guess** box and click **Go** to submit your guess.</span></span> <span data-ttu-id="f79d4-140">可以看到，工作流的状态显示在状态窗口中。</span><span class="sxs-lookup"><span data-stu-id="f79d4-140">Note that the status of the workflow is displayed in the status window.</span></span> <span data-ttu-id="f79d4-141">此输出是从 `WriteLine` 活动捕获的。</span><span class="sxs-lookup"><span data-stu-id="f79d4-141">This output is captured from the `WriteLine` activities.</span></span> <span data-ttu-id="f79d4-142">通过从 " **工作流实例 Id** " 组合框中选择一个工作流来切换到该工作流，并注意当前工作流的状态为 "已删除"。</span><span class="sxs-lookup"><span data-stu-id="f79d4-142">Switch to a different workflow by selecting one from the **Workflow Instance Id** combo box and note that the status of the current workflow is removed.</span></span> <span data-ttu-id="f79d4-143">切换回上一个工作流，可以看到其状态已恢复，与以下示例类似。</span><span class="sxs-lookup"><span data-stu-id="f79d4-143">Switch back to the previous workflow and note that the status is restored, similar to the following example.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="f79d4-144">如果切换到启用跟踪之前启动的工作流，则不会显示状态。</span><span class="sxs-lookup"><span data-stu-id="f79d4-144">If you switch to a workflow that was started before tracking was enabled no status is displayed.</span></span> <span data-ttu-id="f79d4-145">但是，如果如果进行了其他猜数，则将保存其状态，因为现在启用了跟踪。</span><span class="sxs-lookup"><span data-stu-id="f79d4-145">However if you make additional guesses, their status is saved because tracking is now enabled.</span></span>  
  
    ```output
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    ```

    > [!NOTE]
    > <span data-ttu-id="f79d4-146">此信息对于确定随机数的范围十分有用，但它并不包含有关先前进行的猜数的任何信息。</span><span class="sxs-lookup"><span data-stu-id="f79d4-146">This information is useful for determining the range of the random number, but it does not contain any information about what guesses have been previously made.</span></span> <span data-ttu-id="f79d4-147">此信息将在下一步中， [如何：并行承载多个版本的工作流](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)。</span><span class="sxs-lookup"><span data-stu-id="f79d4-147">This information is in the next step, [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>

    <span data-ttu-id="f79d4-148">记下工作流实例 ID，然后播放游戏，直到播完。</span><span class="sxs-lookup"><span data-stu-id="f79d4-148">Make a note of the workflow instance id, and play the game through to its completion.</span></span>
  
4. <span data-ttu-id="f79d4-149">打开 Windows 资源管理器并导航到 **NumberGuessWorkflowHost\bin\debug** 文件夹 (或 **bin\release** ，具体取决于项目设置) 。</span><span class="sxs-lookup"><span data-stu-id="f79d4-149">Open Windows Explorer and navigate to the **NumberGuessWorkflowHost\bin\debug** folder (or **bin\release** depending on your project settings).</span></span> <span data-ttu-id="f79d4-150">可以看到，除了项目可执行文件之外，还有包含 guid 文件名的文件。</span><span class="sxs-lookup"><span data-stu-id="f79d4-150">Note that in addition to the project executable files there are files with guid filenames.</span></span> <span data-ttu-id="f79d4-151">确定与上一步中已完成工作流的工作流实例 ID 对应的工作流，然后用记事本打开它。</span><span class="sxs-lookup"><span data-stu-id="f79d4-151">Identify the one that corresponds to the workflow instance id from the completed workflow in the previous step and open it in Notepad.</span></span> <span data-ttu-id="f79d4-152">跟踪信息所包含的内容类似于以下内容。</span><span class="sxs-lookup"><span data-stu-id="f79d4-152">The tracking information contains information similar to the following.</span></span>  
  
    ```output
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    ```

    <span data-ttu-id="f79d4-153">除了缺少用户的猜数之外，此跟踪数据不包含有关工作流的最终猜数的信息。</span><span class="sxs-lookup"><span data-stu-id="f79d4-153">In addition to the absence of the user's guesses, this tracking data does not contain information about the final guess of the workflow.</span></span> <span data-ttu-id="f79d4-154">这是因为，跟踪信息仅包含工作流的 `WriteLine` 输出，而在工作流完成后从 `Completed` 显示的最终消息也是这样的。</span><span class="sxs-lookup"><span data-stu-id="f79d4-154">That is because the tracking information consists only of the `WriteLine` output from the workflow, and the final message that is displayed is done so from the `Completed` handler after the workflow completes.</span></span> <span data-ttu-id="f79d4-155">在本教程的后续步骤中， [如何：并行承载多个版本的工作流](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)，将 `WriteLine` 修改现有活动以显示用户的猜测，并 `WriteLine` 添加一个显示最终结果的附加活动。</span><span class="sxs-lookup"><span data-stu-id="f79d4-155">In next step of the tutorial, [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md), the existing `WriteLine` activities are modified to display the user's guesses, and an additional `WriteLine` activity is added that displays the final results.</span></span> <span data-ttu-id="f79d4-156">集成这些更改后， [如何：并行承载多个版本的工作流](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) 演示如何同时承载多个版本的工作流。</span><span class="sxs-lookup"><span data-stu-id="f79d4-156">After these changes are integrated, [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) demonstrates how to host multiple versions of a workflow at the same time.</span></span>
