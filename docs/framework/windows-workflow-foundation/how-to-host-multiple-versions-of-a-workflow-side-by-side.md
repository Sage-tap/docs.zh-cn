---
description: 了解详细信息：如何：并行托管多个版本的工作流
title: 如何：并行承载多个版本的工作流
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 09c575df-e0a3-4f3b-9e01-a7ac59d65287
ms.openlocfilehash: 7662aa6375467e6bc283e1e743488439c8bf087a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99777666"
---
# <a name="how-to-host-multiple-versions-of-a-workflow-side-by-side"></a><span data-ttu-id="f5a7c-103">如何：并行承载多个版本的工作流</span><span class="sxs-lookup"><span data-stu-id="f5a7c-103">How to: Host Multiple Versions of a Workflow Side-by-Side</span></span>

<span data-ttu-id="f5a7c-104">`WorkflowIdentity` 为工作流应用程序开发人员提供了一种将名称和版本与工作流定义关联的方法，这种方法还可用于将此信息与持久化工作流实例相关联。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-104">`WorkflowIdentity` provides a way for workflow application developers to associate a name and a version with a workflow definition, and for this information to be associated with a persisted workflow instance.</span></span> <span data-ttu-id="f5a7c-105">工作流应用程序开发人员可以使用这些标识信息，为一些情景（如并行执行一个工作流定义的多个版本）提供支持，并为其他功能（如动态更新）提供基础。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-105">This identity information can be used by workflow application developers to enable scenarios such as side-by-side execution of multiple versions of a workflow definition, and provides the cornerstone for other functionality such as dynamic update.</span></span> <span data-ttu-id="f5a7c-106">该教程中的此步骤演示了如何使用 `WorkflowIdentity` 来同时承载多个版本的工作流。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-106">This step in the tutorial demonstrates how to use `WorkflowIdentity` to host multiple versions of a workflow at the same time.</span></span>

## <a name="in-this-topic"></a><span data-ttu-id="f5a7c-107">本主题内容</span><span class="sxs-lookup"><span data-stu-id="f5a7c-107">In this topic</span></span>

<span data-ttu-id="f5a7c-108">在该教程的此步骤中，工作流中的 `WriteLine` 活动已得到修改以提供其他信息，并且添加了一个新的 `WriteLine` 活动。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-108">In this step of the tutorial, the `WriteLine` activities in the workflow are modified to provide additional information, and a new `WriteLine` activity is added.</span></span> <span data-ttu-id="f5a7c-109">将存储原始工作流程序集的副本，并更新主机应用程序以便其可同时在原始工作流和更新后的工作流中运行。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-109">A copy of the original workflow assembly is stored, and the host application is updated so that it can run both the original and the updated workflows at the same time.</span></span>

- [<span data-ttu-id="f5a7c-110">制作 NumberGuessWorkflowActivities 项目的副本</span><span class="sxs-lookup"><span data-stu-id="f5a7c-110">To make a copy of the NumberGuessWorkflowActivities project</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BackupCopy)

- [<span data-ttu-id="f5a7c-111">更新工作流</span><span class="sxs-lookup"><span data-stu-id="f5a7c-111">To update the workflows</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflows)

  - [<span data-ttu-id="f5a7c-112">更新 StateMachine 工作流</span><span class="sxs-lookup"><span data-stu-id="f5a7c-112">To update the StateMachine workflow</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateStateMachine)

  - [<span data-ttu-id="f5a7c-113">更新 Flowchart 工作流</span><span class="sxs-lookup"><span data-stu-id="f5a7c-113">To update the Flowchart workflow</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateFlowchart)

  - [<span data-ttu-id="f5a7c-114">更新 Sequential 工作流</span><span class="sxs-lookup"><span data-stu-id="f5a7c-114">To update the Sequential workflow</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateSequential)

- [<span data-ttu-id="f5a7c-115">更新 WorkflowVersionMap 以包括以前的工作流版本</span><span class="sxs-lookup"><span data-stu-id="f5a7c-115">To update WorkflowVersionMap to include the previous workflow versions</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflowVersionMap)

- [<span data-ttu-id="f5a7c-116">生成并运行应用程序</span><span class="sxs-lookup"><span data-stu-id="f5a7c-116">To build and run the application</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BuildAndRun)

> [!NOTE]
> <span data-ttu-id="f5a7c-117">在执行本主题中的步骤之前，请运行该应用程序，启动每个类型的多个工作流，并针对每个工作流进行一个或两个猜测。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-117">Before following the steps in this topic, run the application, start several workflows of each type, and making one or two guesses for each one.</span></span> <span data-ttu-id="f5a7c-118">此步骤和下面的步骤中将使用这些持久工作流， [如何：更新正在运行的工作流实例的定义](how-to-update-the-definition-of-a-running-workflow-instance.md)。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-118">These persisted workflows are used in this step and the following step, [How to: Update the Definition of a Running Workflow Instance](how-to-update-the-definition-of-a-running-workflow-instance.md).</span></span>

### <a name="to-make-a-copy-of-the-numberguessworkflowactivities-project"></a><a name="BKMK_BackupCopy"></a> <span data-ttu-id="f5a7c-119">创建 NumberGuessWorkflowActivities 项目的副本</span><span class="sxs-lookup"><span data-stu-id="f5a7c-119">To make a copy of the NumberGuessWorkflowActivities project</span></span>

1. <span data-ttu-id="f5a7c-120">如果未打开，则在 Visual Studio 2012 中打开 **WF45GettingStartedTutorial** 解决方案。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-120">Open the **WF45GettingStartedTutorial** solution in Visual Studio 2012 if it is not open.</span></span>

2. <span data-ttu-id="f5a7c-121">按 CTRL+SHIFT+B 生成解决方案。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-121">Press CTRL+SHIFT+B to build the solution.</span></span>

3. <span data-ttu-id="f5a7c-122">关闭 **WF45GettingStartedTutorial** 解决方案。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-122">Close the **WF45GettingStartedTutorial** solution.</span></span>

4. <span data-ttu-id="f5a7c-123">打开 Windows 资源管理器并定位到该教程解决方案文件和项目文件夹所在的文件夹。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-123">Open Windows Explorer and navigate to the folder where the tutorial solution file and the project folders are located.</span></span>

5. <span data-ttu-id="f5a7c-124">在与 **NumberGuessWorkflowHost** 和 **NumberGuessWorkflowActivities** 相同的文件夹中创建名为 **PreviousVersions** 的新文件夹。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-124">Create a new folder named **PreviousVersions** in the same folder as **NumberGuessWorkflowHost** and **NumberGuessWorkflowActivities**.</span></span> <span data-ttu-id="f5a7c-125">此文件夹用于放置包含在后续教程步骤中使用的不同版本工作流的程序集。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-125">This folder is used to contain the assemblies that contain the different versions of the workflows used in the subsequent tutorial steps.</span></span>

6. <span data-ttu-id="f5a7c-126">导航到 **NumberGuessWorkflowActivities\bin\debug** 文件夹 (或 **bin\release** ，具体取决于项目设置) 。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-126">Navigate to the **NumberGuessWorkflowActivities\bin\debug** folder (or **bin\release** depending on your project settings).</span></span> <span data-ttu-id="f5a7c-127">将 **NumberGuessWorkflowActivities.dll** 复制并粘贴到 **PreviousVersions** 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-127">Copy **NumberGuessWorkflowActivities.dll** and paste it into the **PreviousVersions** folder.</span></span>

7. <span data-ttu-id="f5a7c-128">将 **PreviousVersions** 文件夹中 **NumberGuessWorkflowActivities.dll** 重命名为 **NumberGuessWorkflowActivities_v1.dll**。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-128">Rename **NumberGuessWorkflowActivities.dll** in the **PreviousVersions** folder to **NumberGuessWorkflowActivities_v1.dll**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f5a7c-129">本主题中的步骤演示了一种对用于包含多个版本的工作流的程序集进行管理的方法。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-129">The steps in this topic demonstrate one way to manage the assemblies used to contain multiple versions of the workflows.</span></span> <span data-ttu-id="f5a7c-130">也可以使用其他方法，例如，对程序集进行强命名，并在全局程序集缓冲中注册这些程序集。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-130">Other methods such as strong naming the assemblies and registering them in the global assembly cache could also be used.</span></span>

8. <span data-ttu-id="f5a7c-131">在 **NumberGuessWorkflowHost**、 **NumberGuessWorkflowActivities** 和新添加 **PreviousVersions** 文件夹所在的文件夹中创建一个名为 **NumberGuessWorkflowActivities_du** 的新文件夹，并将 **NumberGuessWorkflowActivities** 文件夹中的所有文件和子文件夹复制到新的 **NumberGuessWorkflowActivities_du** 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-131">Create a new folder named **NumberGuessWorkflowActivities_du** in the same folder as **NumberGuessWorkflowHost**, **NumberGuessWorkflowActivities**, and the newly added **PreviousVersions** folder, and copy all of the files and subfolders from the **NumberGuessWorkflowActivities** folder into the new **NumberGuessWorkflowActivities_du** folder.</span></span> <span data-ttu-id="f5a7c-132">此项目的备份副本将在 [如何：更新正在运行的工作流实例的定义](how-to-update-the-definition-of-a-running-workflow-instance.md)中使用。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-132">This backup copy of the project for the initial version of the activities is used in [How to: Update the Definition of a Running Workflow Instance](how-to-update-the-definition-of-a-running-workflow-instance.md).</span></span>

9. <span data-ttu-id="f5a7c-133">重新打开 Visual Studio 2012 中的 **WF45GettingStartedTutorial** 解决方案。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-133">Re-open the **WF45GettingStartedTutorial** solution in Visual Studio 2012.</span></span>

### <a name="to-update-the-workflows"></a><a name="BKMK_UpdateWorkflows"></a> <span data-ttu-id="f5a7c-134">更新工作流</span><span class="sxs-lookup"><span data-stu-id="f5a7c-134">To update the workflows</span></span>

<span data-ttu-id="f5a7c-135">在本节中，将会更新工作流定义。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-135">In this section, the workflow definitions are updated.</span></span> <span data-ttu-id="f5a7c-136">将会更新针对用户猜测提供反馈的两个 `WriteLine` 活动，并添加一个新的 `WriteLine` 活动，此活动提供猜测了数字之后有关该游戏的其他信息。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-136">The two `WriteLine` activities that give feedback on the user's guess are updated, and a new `WriteLine` activity is added that provides additional information about the game once the number is guessed.</span></span>

#### <a name="to-update-the-statemachine-workflow"></a><a name="BKMK_UpdateStateMachine"></a> <span data-ttu-id="f5a7c-137">更新 StateMachine 工作流</span><span class="sxs-lookup"><span data-stu-id="f5a7c-137">To update the StateMachine workflow</span></span>

1. <span data-ttu-id="f5a7c-138">在 **解决方案资源管理器** 的 **NumberGuessWorkflowActivities** 项目下，双击 **statemachinenumberguessworkflow.xaml**。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-138">In **Solution Explorer**, under the **NumberGuessWorkflowActivities** project, double-click **StateMachineNumberGuessWorkflow.xaml**.</span></span>

2. <span data-ttu-id="f5a7c-139">双击状态机上的 **推测错误** 转换。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-139">Double-click the **Guess Incorrect** transition on the state machine.</span></span>

3. <span data-ttu-id="f5a7c-140">更新 `Text` 活动中最左侧 `WriteLine` 的 `If`。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-140">Update the `Text` of the left-most `WriteLine` in the `If` activity.</span></span>

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

4. <span data-ttu-id="f5a7c-141">更新 `Text` 活动中最右侧 `WriteLine` 的 `If`。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-141">Update the `Text` of the right-most `WriteLine` in the `If` activity.</span></span>

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

5. <span data-ttu-id="f5a7c-142">通过单击工作流设计器顶部显示的痕迹导航中的 "状态机"，返回到工作流设计 **器中的** "总体状态机" 视图。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-142">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>

6. <span data-ttu-id="f5a7c-143">双击状态机上的 " **猜测正确** 转换"。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-143">Double-click the **Guess Correct** transition on the state machine.</span></span>

7. <span data-ttu-id="f5a7c-144">将 " **WriteLine** " 活动从 "**工具箱**" 的 "**基元**" 部分拖放到转换的 "在 **此处放置操作活动**" 标签上。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-144">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it on the **Drop Action activity here** label of the transition.</span></span>

8. <span data-ttu-id="f5a7c-145">在 `Text` 属性框中键入以下表达式。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-145">Type the following expression into the `Text` property box.</span></span>

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

#### <a name="to-update-the-flowchart-workflow"></a><a name="BKMK_UpdateFlowchart"></a> <span data-ttu-id="f5a7c-146">更新流程图工作流</span><span class="sxs-lookup"><span data-stu-id="f5a7c-146">To update the Flowchart workflow</span></span>

1. <span data-ttu-id="f5a7c-147">在 **解决方案资源管理器** 的 **NumberGuessWorkflowActivities** 项目下，双击 **flowchartnumberguessworkflow.xaml**。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-147">In **Solution Explorer**, under the **NumberGuessWorkflowActivities** project, double-click **FlowchartNumberGuessWorkflow.xaml**.</span></span>

2. <span data-ttu-id="f5a7c-148">更新最左侧 `Text` 活动的 `WriteLine`。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-148">Update the `Text` of the left-most `WriteLine` activity.</span></span>

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

3. <span data-ttu-id="f5a7c-149">更新最右侧 `Text` 活动的 `WriteLine`。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-149">Update the `Text` of the right-most `WriteLine` activity.</span></span>

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

4. <span data-ttu-id="f5a7c-150">将 " **WriteLine** " 活动从 "**工具箱**" 的 "**基元**" 部分拖放到 `True` 最顶部操作的下拉点上 `FlowDecision` 。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-150">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it on the drop point of the `True` action of the topmost `FlowDecision`.</span></span> <span data-ttu-id="f5a7c-151">`WriteLine` 活动将添加到流程图并链接到 `True` 的 `FlowDecision` 操作。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-151">The `WriteLine` activity is added to the flowchart and linked to the `True` action of the `FlowDecision`.</span></span>

5. <span data-ttu-id="f5a7c-152">在 `Text` 属性框中键入以下表达式。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-152">Type the following expression into the `Text` property box.</span></span>

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

#### <a name="to-update-the-sequential-workflow"></a><a name="BKMK_UpdateSequential"></a> <span data-ttu-id="f5a7c-153">更新顺序工作流</span><span class="sxs-lookup"><span data-stu-id="f5a7c-153">To update the Sequential workflow</span></span>

1. <span data-ttu-id="f5a7c-154">在 **解决方案资源管理器** 的 **NumberGuessWorkflowActivities** 项目下，双击 **sequentialnumberguessworkflow.xaml**。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-154">In **Solution Explorer**, under the **NumberGuessWorkflowActivities** project, double-click **SequentialNumberGuessWorkflow.xaml**.</span></span>

2. <span data-ttu-id="f5a7c-155">更新 `Text` 活动中最左侧 `WriteLine` 的 `If`。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-155">Update the `Text` of the left-most `WriteLine` in the `If` activity.</span></span>

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

3. <span data-ttu-id="f5a7c-156">更新 `Text` 活动中最右侧 `WriteLine` 活动的 `If`。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-156">Update the `Text` of the right-most `WriteLine` activity in the `If` activity.</span></span>

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

4. <span data-ttu-id="f5a7c-157">将 " **writeline** " 活动从 "**工具箱**" 的 "**基元**" 部分拖放到 " **DoWhile** " 活动后面，使 **WriteLine** 成为根活动中的最后一个活动 `Sequence` 。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-157">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it after the **DoWhile** activity so that the **WriteLine** is the final activity in the root `Sequence` activity.</span></span>

5. <span data-ttu-id="f5a7c-158">在 `Text` 属性框中键入以下表达式。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-158">Type the following expression into the `Text` property box.</span></span>

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

### <a name="to-update-workflowversionmap-to-include-the-previous-workflow-versions"></a><a name="BKMK_UpdateWorkflowVersionMap"></a> <span data-ttu-id="f5a7c-159">更新 WorkflowVersionMap 以包含以前的工作流版本</span><span class="sxs-lookup"><span data-stu-id="f5a7c-159">To update WorkflowVersionMap to include the previous workflow versions</span></span>

1. <span data-ttu-id="f5a7c-160">双击 **NumberGuessWorkflowHost** 项目下的 " **WorkflowVersionMap.cs** (" 或 " **WorkflowVersionMap** ") 将其打开。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-160">Double-click **WorkflowVersionMap.cs** (or **WorkflowVersionMap.vb**) under the **NumberGuessWorkflowHost** project to open it.</span></span>

2. <span data-ttu-id="f5a7c-161">向包含其他 `using`（或 `Imports`）语句的文件的顶部添加以下 `using`（或 `Imports`）语句。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-161">Add the following `using` (or `Imports`) statements to the top of the file with the other `using` (or `Imports`) statements.</span></span>

    ```vb
    Imports System.Reflection
    Imports System.IO
    ```

    ```csharp
    using System.Reflection;
    using System.IO;
    ```

3. <span data-ttu-id="f5a7c-162">紧接在现有的三个工作流标识声明下面添加三个新工作流标识。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-162">Add three new workflow identities just below the three existing workflow identity declarations.</span></span> <span data-ttu-id="f5a7c-163">这些新的 `v1` 工作流标识用于为在进行更新前启动的工作流提供正确的工作流定义。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-163">These new `v1` workflow identities will be used provide the correct workflow definition to workflows started before the updates were made.</span></span>

    ```vb
    'Current version identities.
    Public StateMachineNumberGuessIdentity As WorkflowIdentity
    Public FlowchartNumberGuessIdentity As WorkflowIdentity
    Public SequentialNumberGuessIdentity As WorkflowIdentity

    'v1 Identities.
    Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity
    Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity
    Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity
    ```

    ```csharp
    // Current version identities.
    static public WorkflowIdentity StateMachineNumberGuessIdentity;
    static public WorkflowIdentity FlowchartNumberGuessIdentity;
    static public WorkflowIdentity SequentialNumberGuessIdentity;

    // v1 identities.
    static public WorkflowIdentity StateMachineNumberGuessIdentity_v1;
    static public WorkflowIdentity FlowchartNumberGuessIdentity_v1;
    static public WorkflowIdentity SequentialNumberGuessIdentity_v1;
    ```

4. <span data-ttu-id="f5a7c-164">在 `WorkflowVersionMap` 构造函数中，将三个当前工作流标识的 `Version` 属性更新为 `2.0.0.0`。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-164">In the `WorkflowVersionMap` constructor, update the `Version` property of the three current workflow identities to `2.0.0.0`.</span></span>

    ```vb
    'Add the current workflow version identities.
    StateMachineNumberGuessIdentity = New WorkflowIdentity With
    {
        .Name = "StateMachineNumberGuessWorkflow",
        .Version = New Version(2, 0, 0, 0)
    }

    FlowchartNumberGuessIdentity = New WorkflowIdentity With
    {
        .Name = "FlowchartNumberGuessWorkflow",
        .Version = New Version(2, 0, 0, 0)
    }

    SequentialNumberGuessIdentity = New WorkflowIdentity With
    {
        .Name = "SequentialNumberGuessWorkflow",
        .Version = New Version(2, 0, 0, 0)
    }

    map.Add(StateMachineNumberGuessIdentity, New StateMachineNumberGuessWorkflow())
    map.Add(FlowchartNumberGuessIdentity, New FlowchartNumberGuessWorkflow())
    map.Add(SequentialNumberGuessIdentity, New SequentialNumberGuessWorkflow())
    ```

    ```csharp
    // Add the current workflow version identities.
    StateMachineNumberGuessIdentity = new WorkflowIdentity
    {
        Name = "StateMachineNumberGuessWorkflow",
        // Version = new Version(1, 0, 0, 0),
        Version = new Version(2, 0, 0, 0)
    };

    FlowchartNumberGuessIdentity = new WorkflowIdentity
    {
        Name = "FlowchartNumberGuessWorkflow",
        // Version = new Version(1, 0, 0, 0),
        Version = new Version(2, 0, 0, 0)
    };

    SequentialNumberGuessIdentity = new WorkflowIdentity
    {
        Name = "SequentialNumberGuessWorkflow",
        // Version = new Version(1, 0, 0, 0),
        Version = new Version(2, 0, 0, 0)
    };

    map.Add(StateMachineNumberGuessIdentity, new StateMachineNumberGuessWorkflow());
    map.Add(FlowchartNumberGuessIdentity, new FlowchartNumberGuessWorkflow());
    map.Add(SequentialNumberGuessIdentity, new SequentialNumberGuessWorkflow());
    ```

    <span data-ttu-id="f5a7c-165">向字典添加当前版本的工作流的代码使用项目中引用的当前版本，因此，无需对初始化工作流定义的代码进行更新。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-165">The code in that adds the current versions of the workflows to the dictionary uses the current versions that are referenced in the project, so the code that initializes the workflow definitions does not need to be updated.</span></span>

5. <span data-ttu-id="f5a7c-166">紧接在向字典添加当前版本的代码的后面添加以下代码。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-166">Add the following code in the constructor just after the code that adds the current versions to the dictionary.</span></span>

    ```vb
    'Initialize the previous workflow version identities.
    StateMachineNumberGuessIdentity_v1 = New WorkflowIdentity With
    {
        .Name = "StateMachineNumberGuessWorkflow",
        .Version = New Version(1, 0, 0, 0)
    }

    FlowchartNumberGuessIdentity_v1 = New WorkflowIdentity With
    {
        .Name = "FlowchartNumberGuessWorkflow",
        .Version = New Version(1, 0, 0, 0)
    }

    SequentialNumberGuessIdentity_v1 = New WorkflowIdentity With
    {
        .Name = "SequentialNumberGuessWorkflow",
        .Version = New Version(1, 0, 0, 0)
    }
    ```

    ```csharp
    // Initialize the previous workflow version identities.
    StateMachineNumberGuessIdentity_v1 = new WorkflowIdentity
    {
        Name = "StateMachineNumberGuessWorkflow",
        Version = new Version(1, 0, 0, 0)
    };

    FlowchartNumberGuessIdentity_v1 = new WorkflowIdentity
    {
        Name = "FlowchartNumberGuessWorkflow",
        Version = new Version(1, 0, 0, 0)
    };

    SequentialNumberGuessIdentity_v1 = new WorkflowIdentity
    {
        Name = "SequentialNumberGuessWorkflow",
        Version = new Version(1, 0, 0, 0)
    };
    ```

    <span data-ttu-id="f5a7c-167">这些工作流标识与相应工作流定义的初始版本相关联。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-167">These workflow identities are associated with the initial versions of the corresponding workflow definitions.</span></span>

6. <span data-ttu-id="f5a7c-168">接下来，加载包含初始版本的工作流定义的程序集，然后创建相应工作流定义，并将这些定义添加到字典。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-168">Next, load the assembly that contains the initial version of the workflow definitions, and create and add the corresponding workflow definitions to the dictionary.</span></span>

    ```vb
    'Add the previous version workflow identities to the dictionary along with
    'the corresponding workflow definitions loaded from the v1 assembly.
    'Assembly.LoadFile requires an absolute path so convert this relative path
    'to an absolute path.
    Dim v1AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll"
    v1AssemblyPath = Path.GetFullPath(v1AssemblyPath)
    Dim v1Assembly As Assembly = Assembly.LoadFile(v1AssemblyPath)

    map.Add(StateMachineNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))

    map.Add(SequentialNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))

    map.Add(FlowchartNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))
    ```

    ```csharp
    // Add the previous version workflow identities to the dictionary along with
    // the corresponding workflow definitions loaded from the v1 assembly.
    // Assembly.LoadFile requires an absolute path so convert this relative path
    // to an absolute path.
    string v1AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll";
    v1AssemblyPath = Path.GetFullPath(v1AssemblyPath);
    Assembly v1Assembly = Assembly.LoadFile(v1AssemblyPath);

    map.Add(StateMachineNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);

    map.Add(SequentialNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);

    map.Add(FlowchartNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);
    ```

    <span data-ttu-id="f5a7c-169">下面的示例完整列出了已更新的 `WorkflowVersionMap` 类。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-169">The following example is the complete listing for the updated `WorkflowVersionMap` class.</span></span>

    ```vb
    Public Module WorkflowVersionMap
        Dim map As Dictionary(Of WorkflowIdentity, Activity)

        'Current version identities.
        Public StateMachineNumberGuessIdentity As WorkflowIdentity
        Public FlowchartNumberGuessIdentity As WorkflowIdentity
        Public SequentialNumberGuessIdentity As WorkflowIdentity

        'v1 Identities.
        Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity
        Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity
        Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity

        Sub New()
            map = New Dictionary(Of WorkflowIdentity, Activity)

            'Add the current workflow version identities.
            StateMachineNumberGuessIdentity = New WorkflowIdentity With
            {
                .Name = "StateMachineNumberGuessWorkflow",
                .Version = New Version(2, 0, 0, 0)
            }

            FlowchartNumberGuessIdentity = New WorkflowIdentity With
            {
                .Name = "FlowchartNumberGuessWorkflow",
                .Version = New Version(2, 0, 0, 0)
            }

            SequentialNumberGuessIdentity = New WorkflowIdentity With
            {
                .Name = "SequentialNumberGuessWorkflow",
                .Version = New Version(2, 0, 0, 0)
            }

            map.Add(StateMachineNumberGuessIdentity, New StateMachineNumberGuessWorkflow())
            map.Add(FlowchartNumberGuessIdentity, New FlowchartNumberGuessWorkflow())
            map.Add(SequentialNumberGuessIdentity, New SequentialNumberGuessWorkflow())

            'Initialize the previous workflow version identities.
            StateMachineNumberGuessIdentity_v1 = New WorkflowIdentity With
            {
                .Name = "StateMachineNumberGuessWorkflow",
                .Version = New Version(1, 0, 0, 0)
            }

            FlowchartNumberGuessIdentity_v1 = New WorkflowIdentity With
            {
                .Name = "FlowchartNumberGuessWorkflow",
                .Version = New Version(1, 0, 0, 0)
            }

            SequentialNumberGuessIdentity_v1 = New WorkflowIdentity With
            {
                .Name = "SequentialNumberGuessWorkflow",
                .Version = New Version(1, 0, 0, 0)
            }

            'Add the previous version workflow identities to the dictionary along with
            'the corresponding workflow definitions loaded from the v1 assembly.
            'Assembly.LoadFile requires an absolute path so convert this relative path
            'to an absolute path.
            Dim v1AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll"
            v1AssemblyPath = Path.GetFullPath(v1AssemblyPath)
            Dim v1Assembly As Assembly = Assembly.LoadFile(v1AssemblyPath)

            map.Add(StateMachineNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))

            map.Add(SequentialNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))

            map.Add(FlowchartNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))
        End Sub

        Public Function GetWorkflowDefinition(identity As WorkflowIdentity) As Activity
            Return map(identity)
        End Function

        Public Function GetIdentityDescription(identity As WorkflowIdentity) As String
            Return identity.ToString()
        End Function
    End Module
    ```

    ```csharp
    public static class WorkflowVersionMap
    {
        static Dictionary<WorkflowIdentity, Activity> map;

        // Current version identities.
        static public WorkflowIdentity StateMachineNumberGuessIdentity;
        static public WorkflowIdentity FlowchartNumberGuessIdentity;
        static public WorkflowIdentity SequentialNumberGuessIdentity;

        // v1 identities.
        static public WorkflowIdentity StateMachineNumberGuessIdentity_v1;
        static public WorkflowIdentity FlowchartNumberGuessIdentity_v1;
        static public WorkflowIdentity SequentialNumberGuessIdentity_v1;

        static WorkflowVersionMap()
        {
            map = new Dictionary<WorkflowIdentity, Activity>();

            // Add the current workflow version identities.
            StateMachineNumberGuessIdentity = new WorkflowIdentity
            {
                Name = "StateMachineNumberGuessWorkflow",
                // Version = new Version(1, 0, 0, 0),
                Version = new Version(2, 0, 0, 0)
            };

            FlowchartNumberGuessIdentity = new WorkflowIdentity
            {
                Name = "FlowchartNumberGuessWorkflow",
                // Version = new Version(1, 0, 0, 0),
                Version = new Version(2, 0, 0, 0)
            };

            SequentialNumberGuessIdentity = new WorkflowIdentity
            {
                Name = "SequentialNumberGuessWorkflow",
                // Version = new Version(1, 0, 0, 0),
                Version = new Version(2, 0, 0, 0)
            };

            map.Add(StateMachineNumberGuessIdentity, new StateMachineNumberGuessWorkflow());
            map.Add(FlowchartNumberGuessIdentity, new FlowchartNumberGuessWorkflow());
            map.Add(SequentialNumberGuessIdentity, new SequentialNumberGuessWorkflow());

            // Initialize the previous workflow version identities.
            StateMachineNumberGuessIdentity_v1 = new WorkflowIdentity
            {
                Name = "StateMachineNumberGuessWorkflow",
                Version = new Version(1, 0, 0, 0)
            };

            FlowchartNumberGuessIdentity_v1 = new WorkflowIdentity
            {
                Name = "FlowchartNumberGuessWorkflow",
                Version = new Version(1, 0, 0, 0)
            };

            SequentialNumberGuessIdentity_v1 = new WorkflowIdentity
            {
                Name = "SequentialNumberGuessWorkflow",
                Version = new Version(1, 0, 0, 0)
            };

            // Add the previous version workflow identities to the dictionary along with
            // the corresponding workflow definitions loaded from the v1 assembly.
            // Assembly.LoadFile requires an absolute path so convert this relative path
            // to an absolute path.
            string v1AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll";
            v1AssemblyPath = Path.GetFullPath(v1AssemblyPath);
            Assembly v1Assembly = Assembly.LoadFile(v1AssemblyPath);

            map.Add(StateMachineNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);

            map.Add(SequentialNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);

            map.Add(FlowchartNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);
        }

        public static Activity GetWorkflowDefinition(WorkflowIdentity identity)
        {
            return map[identity];
        }

        public static string GetIdentityDescription(WorkflowIdentity identity)
        {
            return identity.ToString();
        }
    }
    ```

### <a name="to-build-and-run-the-application"></a><a name="BKMK_BuildAndRun"></a> <span data-ttu-id="f5a7c-170">生成并运行应用程序</span><span class="sxs-lookup"><span data-stu-id="f5a7c-170">To build and run the application</span></span>

1. <span data-ttu-id="f5a7c-171">按 Ctrl+Shift+B 以生成应用程序，然后按 Ctrl+F5 启动该应用程序。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-171">Press CTRL+SHIFT+B to build the application, and then CTRL+F5 to start.</span></span>

2. <span data-ttu-id="f5a7c-172">通过单击 " **新游戏**" 启动新工作流。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-172">Start a new workflow by clicking **New Game**.</span></span> <span data-ttu-id="f5a7c-173">工作流的版本显示在状态窗口下面，它反映了关联 `WorkflowIdentity` 的更新版本。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-173">The version of the workflow is displayed under the status window and reflects the updated version from the associated `WorkflowIdentity`.</span></span> <span data-ttu-id="f5a7c-174">请记下 `InstanceId`，这样您就可以在工作流完成时查看该工作流的跟踪文件，然后在游戏完成之前输入猜测。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-174">Make a note of the `InstanceId` so you can view the tracking file for the workflow when it completes, and then enter guesses until the game is complete.</span></span> <span data-ttu-id="f5a7c-175">请注意用户猜测基于 `WriteLine` 活动的更新在状态窗口中的信息中显示的方式。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-175">Note how the user's guess is displayed in the information displayed in the status window based on the updates to the `WriteLine` activities.</span></span>

    ```console
    Please enter a number between 1 and 10
    5 is too high.
    Please enter a number between 1 and 10
    3 is too high.
    Please enter a number between 1 and 10
    1 is too low.
    Please enter a number between 1 and 10
    Congratulations, you guessed the number in 4 turns.
    ```

    > [!NOTE]
    > <span data-ttu-id="f5a7c-176">将显示 `WriteLine` 活动的更新文本，但不显示已在本主题中添加的最终 `WriteLine` 活动的输出。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-176">The updated text from the `WriteLine` activities is displayed, but the output of the final `WriteLine` activity that was added in this topic is not.</span></span> <span data-ttu-id="f5a7c-177">这是因为，此状态窗口将由 `PersistableIdle` 处理程序进行更新。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-177">That is because the status window is updated by the `PersistableIdle` handler.</span></span> <span data-ttu-id="f5a7c-178">由于该工作流在最终活动之后完成且不会转为空闲状态，因此不会调用 `PersistableIdle` 处理程序。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-178">Because the workflow completes and does not go idle after the final activity, the `PersistableIdle` handler is not called.</span></span> <span data-ttu-id="f5a7c-179">但是，`Completed` 处理程序会在状态窗口中显示类似的消息。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-179">However, a similar message is displayed in the status window by the `Completed` handler.</span></span> <span data-ttu-id="f5a7c-180">如果需要，可以向 `Completed` 处理程序添加代码，以便从 `StringWriter` 提取文本并在状态窗口中显示。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-180">If desired, code could be added to the `Completed` handler to extract the text from the `StringWriter` and display it to the status window.</span></span>

3. <span data-ttu-id="f5a7c-181">打开 Windows 资源管理器并导航到 **NumberGuessWorkflowHost\bin\debug** 文件夹 (或 **bin\release** ，具体取决于你的项目设置) 并使用与已完成的工作流相对应的 Notepad 打开跟踪文件。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-181">Open Windows Explorer and navigate to the **NumberGuessWorkflowHost\bin\debug** folder (or **bin\release** depending on your project settings) and open the tracking file using Notepad that corresponds to the completed workflow.</span></span> <span data-ttu-id="f5a7c-182">如果未记下 `InstanceId` ，可以使用 Windows 资源管理器中的 " **修改日期** " 信息来识别正确的跟踪文件。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-182">If you did not make a note of the `InstanceId`, you can identify the correct tracking file by using the **Date modified** information in Windows Explorer.</span></span>

    ```console
    Please enter a number between 1 and 10
    5 is too high.
    Please enter a number between 1 and 10
    3 is too high.
    Please enter a number between 1 and 10
    1 is too low.
    Please enter a number between 1 and 10
    2 is correct. You guessed it in 4 turns.
    ```

    <span data-ttu-id="f5a7c-183">该跟踪文件中包含已更新的 `WriteLine` 输出，包括在本主题中添加的 `WriteLine` 的输出。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-183">The updated `WriteLine` output is contained within the tracking file, including the output of the `WriteLine` that was added in this topic.</span></span>

4. <span data-ttu-id="f5a7c-184">切换回数字猜测应用程序，然后选择在进行更新前启动的一个工作流。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-184">Switch back to the number guessing application and select one of the workflows that was started before the updates were made.</span></span> <span data-ttu-id="f5a7c-185">您可通过查看在状态窗口下面显示的版本信息来识别当前选择的工作流的版本。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-185">You can identify the version of the currently selected workflow by looking at the version information that is displayed below the status window.</span></span> <span data-ttu-id="f5a7c-186">输入一些猜测，并注意状态更新与前一个版本的 `WriteLine` 活动输出相符，并且不包括用户猜测。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-186">Enter some guesses and note that the status updates match the `WriteLine` activity output from the previous version, and do not include the user's guess.</span></span> <span data-ttu-id="f5a7c-187">这是因为，这些工作流使用的是不具有 `WriteLine` 更新的前一个工作流定义。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-187">That is because these workflows are using the previous workflow definition that does not have the `WriteLine` updates.</span></span>

    <span data-ttu-id="f5a7c-188">在下一步中， [如何：更新正在运行的工作流实例的定义](how-to-update-the-definition-of-a-running-workflow-instance.md)，将更新正在运行的 `v1` 工作流实例，使其包含作为实例的新功能 `v2` 。</span><span class="sxs-lookup"><span data-stu-id="f5a7c-188">In the next step, [How to: Update the Definition of a Running Workflow Instance](how-to-update-the-definition-of-a-running-workflow-instance.md), the running `v1` workflow instances are updated so they contain the new functionality as the `v2` instances.</span></span>
