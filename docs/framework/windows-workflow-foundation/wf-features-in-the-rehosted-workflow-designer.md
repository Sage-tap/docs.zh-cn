---
description: 了解详细信息：重新承载中的新 Workflow Foundation 4.5 功能的支持工作流设计器
title: 重新承载的工作流设计器中新 Workflow Foundation 4.5 功能的支持
ms.date: 03/30/2017
ms.assetid: 1a4a4038-d8e6-41dd-99ea-93bd76286772
ms.openlocfilehash: 948519265383e9fd3850c44304f7c02283b3f579
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755000"
---
# <a name="support-for-new-workflow-foundation-45-features-in-the-rehosted-workflow-designer"></a><span data-ttu-id="64063-103">重新承载的工作流设计器中新 Workflow Foundation 4.5 功能的支持</span><span class="sxs-lookup"><span data-stu-id="64063-103">Support for New Workflow Foundation 4.5 Features in the Rehosted Workflow Designer</span></span>

<span data-ttu-id="64063-104">.NET Framework 4.5 (WF) Windows Workflow Foundation 引入了许多新功能，包括工作流设计器体验的多项增强功能。</span><span class="sxs-lookup"><span data-stu-id="64063-104">Windows Workflow Foundation (WF) in .NET Framework 4.5 introduced many new features, including several enhancements to the workflow designer experience.</span></span> <span data-ttu-id="64063-105">本主题详细介绍重新承载的设计器中支持哪些功能以及当前不支持哪些功能。</span><span class="sxs-lookup"><span data-stu-id="64063-105">This topic details which of these features are supported in the rehosted designer, and which ones are currently not supported.</span></span>

> [!NOTE]
> <span data-ttu-id="64063-106">若要查看 .NET Framework 4.5 中引入的所有新 Windows Workflow Foundation (WF) 功能的列表，包括与设计器重新承载无关的功能，请参阅 [Windows Workflow Foundation 4.5 中 .NET Framework 的新增](whats-new-in-wf-in-dotnet.md)功能。</span><span class="sxs-lookup"><span data-stu-id="64063-106">For a list of all of the new Windows Workflow Foundation (WF) features introduced in .NET Framework 4.5, including those that are unrelated to designer rehosting, see [What's New in Windows Workflow Foundation in .NET Framework 4.5](whats-new-in-wf-in-dotnet.md).</span></span>

## <a name="activities"></a><span data-ttu-id="64063-107">活动</span><span class="sxs-lookup"><span data-stu-id="64063-107">Activities</span></span>

 <span data-ttu-id="64063-108">内置活动库包含新活动和现有活动的新功能。</span><span class="sxs-lookup"><span data-stu-id="64063-108">The built-in activity library contains new activities and new features for existing activities.</span></span> <span data-ttu-id="64063-109">重新承载的设计器支持所有这些新活动。</span><span class="sxs-lookup"><span data-stu-id="64063-109">All of these new activities are supported in the rehosted designer.</span></span> <span data-ttu-id="64063-110">有关这些新活动的详细信息，请参阅[.NET Framework 4.5 中 Windows Workflow Foundation 的新增功能](whats-new-in-wf-in-dotnet.md)的[活动](whats-new-in-wf-in-dotnet.md#BKMK_NewActivities)部分。</span><span class="sxs-lookup"><span data-stu-id="64063-110">For more information on these new activities, see the [Activities](whats-new-in-wf-in-dotnet.md#BKMK_NewActivities) section of [What's New in Windows Workflow Foundation in .NET Framework 4.5](whats-new-in-wf-in-dotnet.md).</span></span>

## <a name="c-expressions"></a><span data-ttu-id="64063-111">C# 表达式</span><span class="sxs-lookup"><span data-stu-id="64063-111">C# Expressions</span></span>

 <span data-ttu-id="64063-112">在 .NET Framework 4.5 之前，工作流中的所有表达式只能用 Visual Basic 编写。</span><span class="sxs-lookup"><span data-stu-id="64063-112">Prior to .NET Framework 4.5, all expressions in workflows could only be written in Visual Basic.</span></span> <span data-ttu-id="64063-113">在 .NET Framework 4.5 中，Visual Basic 表达式仅用于使用 Visual Basic 创建的项目。</span><span class="sxs-lookup"><span data-stu-id="64063-113">In .NET Framework 4.5, Visual Basic expressions are only used for projects created using Visual Basic.</span></span> <span data-ttu-id="64063-114">Visual C# 项目现在将 C# 用于表达式。</span><span class="sxs-lookup"><span data-stu-id="64063-114">Visual C# projects now use C# for expressions.</span></span> <span data-ttu-id="64063-115">在 Visual Studio 2012 中创作工作流时，将提供一个功能齐全的 c # 表达式编辑器，其中包括语法突出显示和 intellisense 等功能。</span><span class="sxs-lookup"><span data-stu-id="64063-115">When authoring workflows in Visual Studio 2012, a fully functional C# expression editor is provided which capabilities such as grammar highlighting and intellisense.</span></span> <span data-ttu-id="64063-116">在使用 Visual Basic 表达式的以前版本中创建的 C# 工作流项目仍可继续使用。</span><span class="sxs-lookup"><span data-stu-id="64063-116">C# workflow projects created in previous versions that use Visual Basic expressions will continue to work.</span></span>

> [!WARNING]
> <span data-ttu-id="64063-117">重新承载的设计器不支持 C# 表达式。</span><span class="sxs-lookup"><span data-stu-id="64063-117">C# expressions are not supported in the rehosted designer.</span></span>

## <a name="new-designer-capabilities"></a><span data-ttu-id="64063-118">新设计器功能</span><span class="sxs-lookup"><span data-stu-id="64063-118">New Designer Capabilities</span></span>

### <a name="designer-search"></a><span data-ttu-id="64063-119">设计器搜索</span><span class="sxs-lookup"><span data-stu-id="64063-119">Designer Search</span></span>

 <span data-ttu-id="64063-120">重新承载设计器不支持 .NET Framework 4.5 引入的 " [快速查找](whats-new-in-wf-in-dotnet.md#BKMK_QuickFind) " 和 " [在文件中查找](whats-new-in-wf-in-dotnet.md#BKMK_FindInFiles) " 功能。</span><span class="sxs-lookup"><span data-stu-id="64063-120">The [Quick Find](whats-new-in-wf-in-dotnet.md#BKMK_QuickFind) and [Find in Files](whats-new-in-wf-in-dotnet.md#BKMK_FindInFiles) features introduced with .NET Framework 4.5 are not supported in the rehosted designer.</span></span> <span data-ttu-id="64063-121">重新承载的设计器不支持 `Toolbox` 搜索。</span><span class="sxs-lookup"><span data-stu-id="64063-121">The `Toolbox` search is supported in the rehosted designer.</span></span> <span data-ttu-id="64063-122">有关这些功能的详细信息，请参阅 [设计器搜索](whats-new-in-wf-in-dotnet.md#BKMK_DesignerSearch)。</span><span class="sxs-lookup"><span data-stu-id="64063-122">For more information on these features, see [Designer Search](whats-new-in-wf-in-dotnet.md#BKMK_DesignerSearch).</span></span>

> [!WARNING]
> <span data-ttu-id="64063-123">重新承载设计器不支持[快速查找](whats-new-in-wf-in-dotnet.md#BKMK_QuickFind)和[在文件中查找](whats-new-in-wf-in-dotnet.md#BKMK_FindInFiles)。</span><span class="sxs-lookup"><span data-stu-id="64063-123">[Quick Find](whats-new-in-wf-in-dotnet.md#BKMK_QuickFind) and [Find in Files](whats-new-in-wf-in-dotnet.md#BKMK_FindInFiles) are not supported in the rehosted designer.</span></span>

### <a name="delete-context-menu-item-in-variable-and-argument-designer"></a><span data-ttu-id="64063-124">删除变量和自变量设计器中的上下文菜单项</span><span class="sxs-lookup"><span data-stu-id="64063-124">Delete context menu item in variable and argument designer</span></span>

 <span data-ttu-id="64063-125">在 .NET Framework 4 中，只能使用键盘在设计器中删除变量和参数。</span><span class="sxs-lookup"><span data-stu-id="64063-125">In .NET Framework 4, variables and arguments could only be deleted in the designer using the keyboard.</span></span> <span data-ttu-id="64063-126">从 .NET Framework 4.5 开始，可以使用上下文菜单来删除变量和参数。</span><span class="sxs-lookup"><span data-stu-id="64063-126">Starting with .NET Framework 4.5, variables and arguments can be deleted using the context menu.</span></span> <span data-ttu-id="64063-127">重新承载的编辑器支持此功能。</span><span class="sxs-lookup"><span data-stu-id="64063-127">This feature is supported in the rehosted designer.</span></span>

 <span data-ttu-id="64063-128">以下屏幕快照显示了变量和自变量设计器的上下文菜单。</span><span class="sxs-lookup"><span data-stu-id="64063-128">The following screenshot shows the variable and argument designer context menu.</span></span>

 ![变量和参数设计器上下文菜单](./media/wf-features-in-the-rehosted-workflow-designer/designer-context-menu.png)

### <a name="auto-surround-with-sequence"></a><span data-ttu-id="64063-130">使用顺序进行自动环绕</span><span class="sxs-lookup"><span data-stu-id="64063-130">Auto-surround with Sequence</span></span>

 <span data-ttu-id="64063-131">由于工作流或特定容器活动（如 <xref:System.Activities.Statements.NoPersistScope>）只能包含单个主体活动，因此添加第二个活动需要开发人员删除第一个活动，请添加一个 <xref:System.Activities.Statements.Sequence> 活动，然后将两个活动都添加到该顺序活动中。</span><span class="sxs-lookup"><span data-stu-id="64063-131">Since a workflow or certain container activities (such as <xref:System.Activities.Statements.NoPersistScope>) can only contain a single body activity, adding a second activity required the developer to delete the first activity, add a <xref:System.Activities.Statements.Sequence> activity, and then add both activities to the sequence activity.</span></span> <span data-ttu-id="64063-132">从 .NET Framework 4.5 开始，在将第二个活动添加到设计器图面时， `Sequence` 将自动创建一个活动来包装这两个活动。</span><span class="sxs-lookup"><span data-stu-id="64063-132">Starting with .NET Framework 4.5, when adding a second activity to the designer surface, a `Sequence` activity will be automatically created to wrap both activities.</span></span> <span data-ttu-id="64063-133">重新承载的编辑器支持此功能。</span><span class="sxs-lookup"><span data-stu-id="64063-133">This feature is supported in the rehosted designer.</span></span>

 <span data-ttu-id="64063-134">以下屏幕快照显示了 `WriteLine` 的 `Body` 中的 `NoPersistScope` 活动。</span><span class="sxs-lookup"><span data-stu-id="64063-134">The following screenshot shows a `WriteLine` activity in the `Body` of a `NoPersistScope`.</span></span>

 ![NoPersistScope 活动正文中的 WriteLine 活动。](./media/wf-features-in-the-rehosted-workflow-designer/auto-surround-write-line-activity.png)

 <span data-ttu-id="64063-136">以下屏幕快照显示了在第一个 `Sequence` 下面丢弃第二个时在 `Body` 中自动创建的 `WriteLine` 活动。</span><span class="sxs-lookup"><span data-stu-id="64063-136">The following screenshot shows the automatically created `Sequence` activity in the `Body` when a second `WriteLine` is dropped below the first.</span></span>

 ![在 NoPersistScope 的正文中自动创建的序列。](./media/wf-features-in-the-rehosted-workflow-designer/auto-surround-sequence-activity.png)

### <a name="pan-mode"></a><span data-ttu-id="64063-138">平移模式</span><span class="sxs-lookup"><span data-stu-id="64063-138">Pan Mode</span></span>

 <span data-ttu-id="64063-139">若要更轻松地在设计器中浏览大型工作流，可以启用平移模式；通过此模式，开发人员可以单击并拖动工作流的可见部分将其移动，而无需使用滚动条。</span><span class="sxs-lookup"><span data-stu-id="64063-139">To more easily navigate a large workflow in the designer, pan mode can be enabled, allowing the developer to click and drag to move the visible portion of the workflow, rather than needing to use the scroll bars.</span></span> <span data-ttu-id="64063-140">用于激活平移模式的按钮位于设计器的右下角。</span><span class="sxs-lookup"><span data-stu-id="64063-140">The button to activate pan mode is in the lower right corner of the designer.</span></span> <span data-ttu-id="64063-141">重新承载的编辑器支持此功能。</span><span class="sxs-lookup"><span data-stu-id="64063-141">This feature is supported in the rehosted designer.</span></span>

 <span data-ttu-id="64063-142">下面的屏幕快照显示了位于工作流设计器右下角的平移按钮。</span><span class="sxs-lookup"><span data-stu-id="64063-142">The following screenshot shows the pan button which is located at the bottom right corner of the workflow designer.</span></span>

 ![工作流设计器中突出显示的 "平移" 按钮。](./media/wf-features-in-the-rehosted-workflow-designer/pan-button-workflow-designer.png)

 <span data-ttu-id="64063-144">也可以使用鼠标中键或空格键来平移工作流设计器。</span><span class="sxs-lookup"><span data-stu-id="64063-144">The middle mouse button or space bar can also be used to pan the workflow designer.</span></span>

### <a name="multi-select"></a><span data-ttu-id="64063-145">多选</span><span class="sxs-lookup"><span data-stu-id="64063-145">Multi-select</span></span>

 <span data-ttu-id="64063-146">通过拖动围绕活动的矩形（未启用平移模式时）或通过按住 Ctrl 键并逐一单击所需的活动，可以一次选择多个活动。</span><span class="sxs-lookup"><span data-stu-id="64063-146">Multiple activities can be selected at one time, either by dragging a rectangle around them (when pan mode is not enabled), or by holding down Ctrl and click on the desired activities one by one.</span></span> <span data-ttu-id="64063-147">重新承载的编辑器支持此功能。</span><span class="sxs-lookup"><span data-stu-id="64063-147">This feature is supported in the rehosted designer.</span></span>

 <span data-ttu-id="64063-148">也可以在设计器中拖动并放置多个选择的活动，并使用上下文菜单与这些活动交互。</span><span class="sxs-lookup"><span data-stu-id="64063-148">Multiple activity selections can also be dragged and dropped within the designer, and can also be interacted with using the context menu.</span></span>

### <a name="outline-view-of-workflow-items"></a><span data-ttu-id="64063-149">工作流项的大纲视图</span><span class="sxs-lookup"><span data-stu-id="64063-149">Outline view of workflow items</span></span>

 <span data-ttu-id="64063-150">为了更加方便地浏览分层工作流，工作流的组件显示在树样式的大纲视图中。</span><span class="sxs-lookup"><span data-stu-id="64063-150">In order to make hierarchical workflows easier to navigate, components of a workflow are shown in a tree-style outline view.</span></span> <span data-ttu-id="64063-151">大纲视图显示在 " **文档大纲** " 视图中。</span><span class="sxs-lookup"><span data-stu-id="64063-151">The outline view is displayed in the **Document Outline** view.</span></span> <span data-ttu-id="64063-152">若要在 Visual Studio 中打开此视图，请从顶部菜单中选择 " **视图**"、" **其他窗口**"、" **文档大纲**"，或按 Ctrl W、U。</span><span class="sxs-lookup"><span data-stu-id="64063-152">To open this view in Visual Studio, from the top menu, select **View**, **Other Windows**, **Document Outline**, or press Ctrl W,U.</span></span> <span data-ttu-id="64063-153">单击大纲视图中的节点将会定位到工作流设计器中的相应活动，并且该大纲视图将会更新以显示在设计器中选择的活动。</span><span class="sxs-lookup"><span data-stu-id="64063-153">Clicking on a node in outline view will navigate to the corresponding activity in the workflow designer, and the outline view will be updated to show activities that are selected in the designer.</span></span> <span data-ttu-id="64063-154">重新承载的编辑器支持此功能。</span><span class="sxs-lookup"><span data-stu-id="64063-154">This feature is supported in the rehosted designer.</span></span>

 <span data-ttu-id="64063-155">[入门教程](getting-started-tutorial.md)中的已完成工作流的以下屏幕截图显示了包含顺序工作流的大纲视图。</span><span class="sxs-lookup"><span data-stu-id="64063-155">The following screenshot of the completed workflow from the [Getting Started Tutorial](getting-started-tutorial.md) shows the outline view with a sequential workflow.</span></span>

 ![使用 Visual Studio 中的顺序工作流显示大纲视图的屏幕截图](./media/wf-features-in-the-rehosted-workflow-designer/outline-view-in-workflow-designer.jpg)

### <a name="more-control-of-visibility-of-shell-bar-and-header-items"></a><span data-ttu-id="64063-157">shell 栏和标头项的更多可见性控制</span><span class="sxs-lookup"><span data-stu-id="64063-157">More control of visibility of shell bar and header items</span></span>

 <span data-ttu-id="64063-158">在重新承载的设计器中，某些标准 UI 控件可能对于给定的工作流没有意义，并可能已关闭。</span><span class="sxs-lookup"><span data-stu-id="64063-158">In a rehosted designer, some of the standard UI controls may not have meaning for a given workflow, and may be turned off.</span></span> <span data-ttu-id="64063-159">在 .NET Framework 4 中，仅在设计器底部的 shell 栏支持此自定义项。</span><span class="sxs-lookup"><span data-stu-id="64063-159">In .NET Framework 4, this customization is only supported by the shell bar at the bottom of the designer.</span></span> <span data-ttu-id="64063-160">在 .NET Framework 4.5 中，可以通过设置适当的值来调整设计器顶部 shell 标头项的可见性 <xref:System.Activities.Presentation.View.DesignerView.WorkflowShellHeaderItemsVisibility%2A> <xref:System.Activities.Presentation.View.ShellHeaderItemsVisibility> 。</span><span class="sxs-lookup"><span data-stu-id="64063-160">In .NET Framework 4.5, the visibility of shell header items at the top of the designer can be adjusted by setting <xref:System.Activities.Presentation.View.DesignerView.WorkflowShellHeaderItemsVisibility%2A> with the appropriate <xref:System.Activities.Presentation.View.ShellHeaderItemsVisibility> value.</span></span>

### <a name="auto-connect-and-auto-insert-in-flowchart-and-state-machine-workflows"></a><span data-ttu-id="64063-161">在流程图和状态机工作流中自动连接和自动插入</span><span class="sxs-lookup"><span data-stu-id="64063-161">Auto-connect and auto-insert in Flowchart and State Machine workflows</span></span>

 <span data-ttu-id="64063-162">在 .NET Framework 4 中，必须手动添加流程图工作流中节点之间的连接。</span><span class="sxs-lookup"><span data-stu-id="64063-162">In .NET Framework 4, connections between nodes in a Flowchart workflow had to be added manually.</span></span> <span data-ttu-id="64063-163">在 .NET Framework 4.5 中，流程图和状态机节点具有在将活动从工具箱拖到设计器图面时变为可见的自动连接点。</span><span class="sxs-lookup"><span data-stu-id="64063-163">In .NET Framework 4.5, Flowchart and State Machine nodes have auto-connect points that become visible when an activity is dragged from the toolbox onto the designer surface.</span></span> <span data-ttu-id="64063-164">将活动放置在这些点中的一个点上会自动添加该活动以及必要的连接。</span><span class="sxs-lookup"><span data-stu-id="64063-164">Dropping an activity on one of these points automatically adds the activity along with the necessary connection.</span></span>

 <span data-ttu-id="64063-165">下面的屏幕快照显示了从工具箱中拖动活动时变为可见的附属点。</span><span class="sxs-lookup"><span data-stu-id="64063-165">The following screenshot shows the attachment points that become visible when an activity is dragged from the toolbox.</span></span>

 ![显示自动连接点的流程图开始节点](./media/wf-features-in-the-rehosted-workflow-designer/auto-connect-points-start-node.png)

 <span data-ttu-id="64063-167">也可以将活动拖动到流程图节点和状态之间的连接上，以在两个其他节点之间自动插入该节点。</span><span class="sxs-lookup"><span data-stu-id="64063-167">Activities can also be dragged onto connections between flowchart nodes and states to auto-insert the node between two other nodes.</span></span> <span data-ttu-id="64063-168">以下屏幕快照显示了突出显示的连接线，可在此连接线处从工具箱拖动并放置活动。</span><span class="sxs-lookup"><span data-stu-id="64063-168">The following screenshot shows the highlighted connecting line where activities can be dragged from the toolbox and dropped.</span></span>

 ![放置活动的自动插入处理](./media/wf-features-in-the-rehosted-workflow-designer/auto-insert-connecting-line.png)

 <span data-ttu-id="64063-170">重新承载的设计器支持自动连接和自动插入。</span><span class="sxs-lookup"><span data-stu-id="64063-170">Auto-connect and auto-insert are supported in the rehosted designer.</span></span>

### <a name="designer-annotations"></a><span data-ttu-id="64063-171">设计器批注</span><span class="sxs-lookup"><span data-stu-id="64063-171">Designer Annotations</span></span>

 <span data-ttu-id="64063-172">为促进开发较大型的工作流，设计器现在支持添加批注以帮助跟踪设计过程。</span><span class="sxs-lookup"><span data-stu-id="64063-172">To facilitate developing larger workflows, the designer now supports adding annotations to help keep track of the design process.</span></span> <span data-ttu-id="64063-173">可以向活动、状态、流程图节点、变量和自变量添加批注。</span><span class="sxs-lookup"><span data-stu-id="64063-173">Annotation can be added to activities, states, flowchart nodes, variables and arguments.</span></span> <span data-ttu-id="64063-174">以下屏幕快照显示了用于将批注添加到设计器的上下文菜单。</span><span class="sxs-lookup"><span data-stu-id="64063-174">The following screenshot shows the context menu used to add annotations to the designer.</span></span>

 ![显示用于添加表示法的菜单的屏幕截图。](./media/wf-features-in-the-rehosted-workflow-designer/designer-annotations-context-menu.png)

 <span data-ttu-id="64063-176">重新承载的设计器支持设计器批注。</span><span class="sxs-lookup"><span data-stu-id="64063-176">Designer annotations are supported in the rehosted designer.</span></span>

### <a name="define-and-consume-activitydelegate-objects-in-the-designer"></a><span data-ttu-id="64063-177">在设计器中定义和使用 ActivityDelegate 对象</span><span class="sxs-lookup"><span data-stu-id="64063-177">Define and consume ActivityDelegate objects in the designer</span></span>

 <span data-ttu-id="64063-178">.NET Framework 4 中的活动使用 <xref:System.Activities.ActivityDelegate> 对象公开工作流的其他部分可与工作流的执行交互的执行点，但使用这些执行点通常需要大量的代码。</span><span class="sxs-lookup"><span data-stu-id="64063-178">Activities in .NET Framework 4 used <xref:System.Activities.ActivityDelegate> objects to expose execution points where other parts of the workflow could interact with a workflow's execution, but using these execution points usually required a fair amount of code.</span></span> <span data-ttu-id="64063-179">在此版本中，开发人员可以使用工作流设计器来定义和使用活动委托。</span><span class="sxs-lookup"><span data-stu-id="64063-179">In this release, developers can define and consume activity delegates using the workflow designer.</span></span> <span data-ttu-id="64063-180">有关详细信息，请参阅 [如何：在工作流设计器中定义和使用活动委托](/visualstudio/workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer)。</span><span class="sxs-lookup"><span data-stu-id="64063-180">For more information, see [How to: Define and consume activity delegates in the Workflow Designer](/visualstudio/workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer).</span></span>

 <span data-ttu-id="64063-181">重新承载的设计器支持活动委托。</span><span class="sxs-lookup"><span data-stu-id="64063-181">Activity delegates are supported in the rehosted designer.</span></span>

### <a name="build-time-validation"></a><span data-ttu-id="64063-182">生成时验证</span><span class="sxs-lookup"><span data-stu-id="64063-182">Build-time validation</span></span>

 <span data-ttu-id="64063-183">在 .NET Framework 4 中，工作流验证错误在工作流项目的生成过程中不计为生成错误。</span><span class="sxs-lookup"><span data-stu-id="64063-183">In .NET Framework 4, workflow validation errors weren’t counted as build errors during the build of a workflow project.</span></span> <span data-ttu-id="64063-184">这意味着即使存在工作流验证错误，工作流项目的生成也可能成功。</span><span class="sxs-lookup"><span data-stu-id="64063-184">This meant that building a workflow project could succeed even when there were workflow validation errors.</span></span> <span data-ttu-id="64063-185">在 .NET Framework 4.5 中，工作流验证错误将导致生成失败。</span><span class="sxs-lookup"><span data-stu-id="64063-185">In .NET Framework 4.5, workflow validation errors cause the build to fail.</span></span>

> [!WARNING]
> <span data-ttu-id="64063-186">重新承载的设计器不支持生成时验证。</span><span class="sxs-lookup"><span data-stu-id="64063-186">Build-time validation is not supported in the rehosted designer.</span></span>

### <a name="design-time-background-validation"></a><span data-ttu-id="64063-187">设计时后台验证</span><span class="sxs-lookup"><span data-stu-id="64063-187">Design-time background validation</span></span>

 <span data-ttu-id="64063-188">在 .NET Framework 4 中，工作流被验证为前台进程，这可能会在复杂或耗时的验证过程中阻止 UI。</span><span class="sxs-lookup"><span data-stu-id="64063-188">In .NET Framework 4, workflows were validated as a foreground process, which could potentially block the UI during complex or time-consuming validation processes.</span></span> <span data-ttu-id="64063-189">工作流验证现在发生在后台线程上，因此不会阻止 UI。</span><span class="sxs-lookup"><span data-stu-id="64063-189">Workflow validation now takes place on a background thread, so that the UI is not blocked.</span></span>

 <span data-ttu-id="64063-190">重新承载的设计器支持设计时后台验证。</span><span class="sxs-lookup"><span data-stu-id="64063-190">Design-time background validation is supported in the rehosted designer.</span></span>

### <a name="view-state-located-in-a-separate-location-in-xaml-files"></a><span data-ttu-id="64063-191">位于 XAML 文件中的单独位置处的视图状态</span><span class="sxs-lookup"><span data-stu-id="64063-191">View state located in a separate location in XAML files</span></span>

 <span data-ttu-id="64063-192">在 .NET Framework 4 中，工作流的视图状态信息存储在多个不同位置的 XAML 文件中。</span><span class="sxs-lookup"><span data-stu-id="64063-192">In .NET Framework 4, the view state information for a workflow is stored across the XAML file in many different locations.</span></span> <span data-ttu-id="64063-193">这对于想直接读取 XAML 或编写用于删除视图状态信息的代码的开发人员来说很不方便。</span><span class="sxs-lookup"><span data-stu-id="64063-193">This is inconvenient for developers who want to read XAML directly, or write code to remove the view state information.</span></span> <span data-ttu-id="64063-194">在 .NET Framework 4.5 中，XAML 文件中的视图状态信息序列化为 XAML 文件中的单独元素。</span><span class="sxs-lookup"><span data-stu-id="64063-194">In .NET Framework 4.5, the view state information in the XAML file is serialized as a separate element in the XAML file.</span></span>  <span data-ttu-id="64063-195">开发人员可以轻松地查找和编辑活动的视图状态信息，或者完全删除视图状态。</span><span class="sxs-lookup"><span data-stu-id="64063-195">Developers can easily locate and edit the view state information of an activity, or remove the view state altogether.</span></span>

 <span data-ttu-id="64063-196">重新承载的工作流编辑器支持此功能。</span><span class="sxs-lookup"><span data-stu-id="64063-196">This feature is supported in the rehosted workflow designer.</span></span>

### <a name="opt-in-for-workflow-45-features-in-rehosted-designer"></a><span data-ttu-id="64063-197">重新承载的设计器中 Workflow 4.5 功能的选择性加入</span><span class="sxs-lookup"><span data-stu-id="64063-197">Opt-in for Workflow 4.5 features in rehosted designer</span></span>

 <span data-ttu-id="64063-198">为了保持向后兼容性，默认情况下，重新承载设计器中不会启用 .NET Framework 4.5 中包含的一些新功能。</span><span class="sxs-lookup"><span data-stu-id="64063-198">To preserve backward compatibility, some new features included in .NET Framework 4.5 are not enabled by default in the rehosted designer.</span></span> <span data-ttu-id="64063-199">这是为了确保使用重新承载的设计器的现有应用程序不会由于更新至最新版本而中断。</span><span class="sxs-lookup"><span data-stu-id="64063-199">This is to ensure that existing applications that use the rehosted designer are not broken by updating to the latest version.</span></span> <span data-ttu-id="64063-200">若要启用重新承载的设计器中的新功能，可将 <xref:System.Activities.Presentation.DesignerConfigurationService.TargetFrameworkName%2A> 设置为“.Net Framework 4.5”，或设置 <xref:System.Activities.Presentation.DesignerConfigurationService> 的各成员以启用各个功能。</span><span class="sxs-lookup"><span data-stu-id="64063-200">To enable new features in the rehosted designer, either set <xref:System.Activities.Presentation.DesignerConfigurationService.TargetFrameworkName%2A> to ".Net Framework 4.5", or set individual members of <xref:System.Activities.Presentation.DesignerConfigurationService> to enable individual features.</span></span>

## <a name="new-workflow-development-models"></a><span data-ttu-id="64063-201">新工作流开发模型</span><span class="sxs-lookup"><span data-stu-id="64063-201">New Workflow Development Models</span></span>

 <span data-ttu-id="64063-202">除流程图和顺序工作流开发模型外，此版本还包括状态机工作流和协定优先工作流服务。</span><span class="sxs-lookup"><span data-stu-id="64063-202">In addition to flowchart and sequential workflow development models, this release includes State Machine workflows, and contract-first workflow services.</span></span>

### <a name="state-machine-workflows"></a><span data-ttu-id="64063-203">状态机工作流</span><span class="sxs-lookup"><span data-stu-id="64063-203">State machine workflows</span></span>

 <span data-ttu-id="64063-204">状态机工作流作为 [Microsoft .NET Framework 4 平台更新 1](/archive/blogs/endpoint/microsoft-net-framework-4-platform-update-1)中 .NET Framework 4.0.1 的一部分引入。</span><span class="sxs-lookup"><span data-stu-id="64063-204">State machine workflows were introduced as part of the .NET Framework 4.0.1 in the [Microsoft .NET Framework 4 Platform Update 1](/archive/blogs/endpoint/microsoft-net-framework-4-platform-update-1).</span></span> <span data-ttu-id="64063-205">此更新包括多个新类和活动，允许开发人员创建状态机工作流。</span><span class="sxs-lookup"><span data-stu-id="64063-205">This update included several new classes and activities which allowed developers to create state machine workflows.</span></span> <span data-ttu-id="64063-206">这些类和活动已针对 .NET Framework 4.5 进行了更新。</span><span class="sxs-lookup"><span data-stu-id="64063-206">These classes and activities have been updated for .NET Framework 4.5.</span></span> <span data-ttu-id="64063-207">更新包括：</span><span class="sxs-lookup"><span data-stu-id="64063-207">Updates include:</span></span>

1. <span data-ttu-id="64063-208">能够对状态设置断点</span><span class="sxs-lookup"><span data-stu-id="64063-208">The ability to set breakpoints on states</span></span>

2. <span data-ttu-id="64063-209">能够在工作流设计器中复制和粘贴转换</span><span class="sxs-lookup"><span data-stu-id="64063-209">The ability to copy and paste transitions in the workflow designer</span></span>

3. <span data-ttu-id="64063-210">设计器支持共享触发器转换创建</span><span class="sxs-lookup"><span data-stu-id="64063-210">Designer support for shared trigger transition creation</span></span>

4. <span data-ttu-id="64063-211">用于创建状态机工作流的活动，包括：<xref:System.Activities.Statements.StateMachine>、<xref:System.Activities.Statements.State> 和 <xref:System.Activities.Statements.Transition></span><span class="sxs-lookup"><span data-stu-id="64063-211">Activities used to create State Machine workflows, including: <xref:System.Activities.Statements.StateMachine>, <xref:System.Activities.Statements.State>, and <xref:System.Activities.Statements.Transition></span></span>

 <span data-ttu-id="64063-212">以下屏幕截图显示了 [入门教程](getting-started-tutorial.md) 步骤 [如何：创建状态机工作流](how-to-create-a-state-machine-workflow.md)中的已完成状态机工作流。</span><span class="sxs-lookup"><span data-stu-id="64063-212">The following screenshot shows the completed state machine workflow from the [Getting Started Tutorial](getting-started-tutorial.md) step [How to: Create a State Machine Workflow](how-to-create-a-state-machine-workflow.md).</span></span>

 ![显示已完成状态机工作流的插图。](./media/wf-features-in-the-rehosted-workflow-designer/complete-state-machine-workflow.jpg)

 <span data-ttu-id="64063-214">有关创建状态机工作流的详细信息，请参阅 [状态机工作流](state-machine-workflows.md)。</span><span class="sxs-lookup"><span data-stu-id="64063-214">For more information on creating state machine workflows, see [State Machine Workflows](state-machine-workflows.md).</span></span> <span data-ttu-id="64063-215">重新承载的工作流编辑器状态机工作流。</span><span class="sxs-lookup"><span data-stu-id="64063-215">State machine workflows are supported in the rehosted designer.</span></span>

### <a name="contract-first-workflow-development"></a><span data-ttu-id="64063-216">协定优先工作流开发</span><span class="sxs-lookup"><span data-stu-id="64063-216">Contract-first workflow development</span></span>

 <span data-ttu-id="64063-217">协定优先工作流开发工具允许开发人员首先在代码中设计协定，然后，只需在 Visual Studio 中单击几下鼠标，就会在工具箱中自动生成表示每个操作的活动模板。</span><span class="sxs-lookup"><span data-stu-id="64063-217">The contract-first workflow development tool allows the developer to design a contract in code first, then, with a few clicks in Visual Studio, automatically generate an activity template in the toolbox representing each operation.</span></span> <span data-ttu-id="64063-218">这些活动随后用于创建实现由该协定定义的操作的工作流。</span><span class="sxs-lookup"><span data-stu-id="64063-218">These activities are then used to create a workflow that implements the operations defined by the contract.</span></span> <span data-ttu-id="64063-219">工作流设计器将对该工作流服务进行验证，以确保实现这些操作并且工作流的签名与协定签名匹配。</span><span class="sxs-lookup"><span data-stu-id="64063-219">The workflow designer will validate the workflow service to ensure that these operations are implemented and the signature of the workflow matches the contract signature.</span></span> <span data-ttu-id="64063-220">开发人员还可以将工作流服务与所实现的协定的集合进行关联。</span><span class="sxs-lookup"><span data-stu-id="64063-220">The developer can also associate a workflow service with a collection of implemented contracts.</span></span> <span data-ttu-id="64063-221">有关协定优先工作流服务开发的详细信息，请参阅 [如何：创建使用现有服务协定的工作流服务](how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)。</span><span class="sxs-lookup"><span data-stu-id="64063-221">For more information on contract-first workflow service development, see [How to: Create a workflow service that consumes an existing service contract](how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md).</span></span>

> [!WARNING]
> <span data-ttu-id="64063-222">工作流设计器不支持协定优先工作流开发。</span><span class="sxs-lookup"><span data-stu-id="64063-222">Contract-first workflow development is not supported in the workflow designer.</span></span>
