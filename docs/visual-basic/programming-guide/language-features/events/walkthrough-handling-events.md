---
description: '了解详细信息：演练：处理事件 (Visual Basic) '
title: 处理事件
ms.date: 07/20/2015
helpviewer_keywords:
- event handling [Visual Basic], walkthroughs
- walkthroughs [Visual Basic], event handling
- variables [Visual Basic], WithEvents
- events [Visual Basic], walkthroughs
- WithEvents keyword [Visual Basic], walkthroughs
- event handlers [Visual Basic], walkthroughs
ms.assetid: f145b3fc-5ae0-4509-a2aa-1ff6934706bd
ms.openlocfilehash: 5101bd2287c81e03efb69b398d6cc961d3e6d9dc
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100436170"
---
# <a name="walkthrough-handling-events-visual-basic"></a><span data-ttu-id="f85e2-103">演练：处理事件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f85e2-103">Walkthrough: Handling Events (Visual Basic)</span></span>

<span data-ttu-id="f85e2-104">这是演示如何处理事件的两个主题中的第二个。</span><span class="sxs-lookup"><span data-stu-id="f85e2-104">This is the second of two topics that demonstrate how to work with events.</span></span> <span data-ttu-id="f85e2-105">第一主题 [演练：声明和引发事件](walkthrough-declaring-and-raising-events.md)，演示如何声明和引发事件。</span><span class="sxs-lookup"><span data-stu-id="f85e2-105">The first topic, [Walkthrough: Declaring and Raising Events](walkthrough-declaring-and-raising-events.md), shows how to declare and raise events.</span></span> <span data-ttu-id="f85e2-106">本部分使用该演练中的窗体和类来演示如何在事件发生时对其进行处理。</span><span class="sxs-lookup"><span data-stu-id="f85e2-106">This section uses the form and class from that walkthrough to show how to handle events when they take place.</span></span>  
  
 <span data-ttu-id="f85e2-107">`Widget`类示例使用传统的事件处理语句。</span><span class="sxs-lookup"><span data-stu-id="f85e2-107">The `Widget` class example uses traditional event-handling statements.</span></span> <span data-ttu-id="f85e2-108">Visual Basic 提供了用于处理事件的其他技术。</span><span class="sxs-lookup"><span data-stu-id="f85e2-108">Visual Basic provides other techniques for working with events.</span></span> <span data-ttu-id="f85e2-109">作为练习，您可以修改此示例以使用 `AddHandler` 和 `Handles` 语句。</span><span class="sxs-lookup"><span data-stu-id="f85e2-109">As an exercise, you can modify this example to use the `AddHandler` and `Handles` statements.</span></span>  
  
### <a name="to-handle-the-percentdone-event-of-the-widget-class"></a><span data-ttu-id="f85e2-110">处理小组件类的 PercentDone 事件</span><span class="sxs-lookup"><span data-stu-id="f85e2-110">To handle the PercentDone event of the Widget class</span></span>  
  
1. <span data-ttu-id="f85e2-111">将以下代码放入 `Form1` ：</span><span class="sxs-lookup"><span data-stu-id="f85e2-111">Place the following code in `Form1`:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#4)]  
  
     <span data-ttu-id="f85e2-112">`WithEvents`关键字指定该变量 `mWidget` 用于处理对象的事件。</span><span class="sxs-lookup"><span data-stu-id="f85e2-112">The `WithEvents` keyword specifies that the variable `mWidget` is used to handle an object's events.</span></span> <span data-ttu-id="f85e2-113">通过提供要从中创建对象的类的名称，指定对象的类型。</span><span class="sxs-lookup"><span data-stu-id="f85e2-113">You specify the kind of object by supplying the name of the class from which the object will be created.</span></span>  
  
     <span data-ttu-id="f85e2-114">变量 `mWidget` 在中声明， `Form1` 因为 `WithEvents` 变量必须是类级别。</span><span class="sxs-lookup"><span data-stu-id="f85e2-114">The variable `mWidget` is declared in `Form1` because `WithEvents` variables must be class-level.</span></span> <span data-ttu-id="f85e2-115">无论你将其放入哪类类型，都是如此。</span><span class="sxs-lookup"><span data-stu-id="f85e2-115">This is true regardless of the type of class you place them in.</span></span>  
  
     <span data-ttu-id="f85e2-116">变量 `mblnCancel` 用于取消 `LongTask` 方法。</span><span class="sxs-lookup"><span data-stu-id="f85e2-116">The variable `mblnCancel` is used to cancel the `LongTask` method.</span></span>  
  
## <a name="writing-code-to-handle-an-event"></a><span data-ttu-id="f85e2-117">编写代码来处理事件</span><span class="sxs-lookup"><span data-stu-id="f85e2-117">Writing Code to Handle an Event</span></span>  

 <span data-ttu-id="f85e2-118">一旦使用声明变量 `WithEvents` ，变量名称就会出现在类的 **代码编辑器** 的左侧下拉列表中。</span><span class="sxs-lookup"><span data-stu-id="f85e2-118">As soon as you declare a variable using `WithEvents`, the variable name appears in the left drop-down list of the class's **Code Editor**.</span></span> <span data-ttu-id="f85e2-119">选择后 `mWidget` ， `Widget` 类的事件将出现在右侧下拉列表中。</span><span class="sxs-lookup"><span data-stu-id="f85e2-119">When you select `mWidget`, the `Widget` class's events appear in the right drop-down list.</span></span> <span data-ttu-id="f85e2-120">选择事件会显示相应的事件过程，其中包含前缀 `mWidget` 和下划线。</span><span class="sxs-lookup"><span data-stu-id="f85e2-120">Selecting an event displays the corresponding event procedure, with the prefix `mWidget` and an underscore.</span></span> <span data-ttu-id="f85e2-121">与变量关联的所有事件过程 `WithEvents` 都被赋予变量名称作为前缀。</span><span class="sxs-lookup"><span data-stu-id="f85e2-121">All the event procedures associated with a `WithEvents` variable are given the variable name as a prefix.</span></span>  
  
#### <a name="to-handle-an-event"></a><span data-ttu-id="f85e2-122">处理事件</span><span class="sxs-lookup"><span data-stu-id="f85e2-122">To handle an event</span></span>  
  
1. <span data-ttu-id="f85e2-123">`mWidget`从 **代码编辑器** 的左侧下拉列表中选择。</span><span class="sxs-lookup"><span data-stu-id="f85e2-123">Select `mWidget` from the left drop-down list in the **Code Editor**.</span></span>  
  
2. <span data-ttu-id="f85e2-124">`PercentDone`从右侧下拉列表中选择事件。</span><span class="sxs-lookup"><span data-stu-id="f85e2-124">Select the `PercentDone` event from the right drop-down list.</span></span> <span data-ttu-id="f85e2-125">" **代码编辑器** " 将打开 `mWidget_PercentDone` 事件过程。</span><span class="sxs-lookup"><span data-stu-id="f85e2-125">The **Code Editor** opens the `mWidget_PercentDone` event procedure.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="f85e2-126">**代码编辑器** 对于插入新的事件处理程序非常有用，但不是必需的。</span><span class="sxs-lookup"><span data-stu-id="f85e2-126">The **Code Editor** is useful, but not required, for inserting new event handlers.</span></span> <span data-ttu-id="f85e2-127">在本演练中，只需直接将事件处理程序复制到代码中即可。</span><span class="sxs-lookup"><span data-stu-id="f85e2-127">In this walkthrough, it is more direct to just copy the event handlers directly into your code.</span></span>  
  
3. <span data-ttu-id="f85e2-128">将以下代码添加到 `mWidget_PercentDone` 事件处理程序中：</span><span class="sxs-lookup"><span data-stu-id="f85e2-128">Add the following code to the `mWidget_PercentDone` event handler:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#5)]  
  
     <span data-ttu-id="f85e2-129">每当 `PercentDone` 引发事件时，事件过程就会在控件中显示完成百分比 `Label` 。</span><span class="sxs-lookup"><span data-stu-id="f85e2-129">Whenever the `PercentDone` event is raised, the event procedure displays the percent complete in a `Label` control.</span></span> <span data-ttu-id="f85e2-130">`DoEvents`方法允许重绘标签，并为用户提供单击 "**取消**" 按钮的机会。</span><span class="sxs-lookup"><span data-stu-id="f85e2-130">The `DoEvents` method allows the label to repaint, and also gives the user the opportunity to click the **Cancel** button.</span></span>  
  
4. <span data-ttu-id="f85e2-131">为 `Button2_Click` 事件处理程序添加以下代码：</span><span class="sxs-lookup"><span data-stu-id="f85e2-131">Add the following code for the `Button2_Click` event handler:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#6)]  
  
 <span data-ttu-id="f85e2-132">如果用户在运行时单击 " **取消** " 按钮，则只要 `LongTask` `Button2_Click` `DoEvents` 语句允许事件处理，就会立即执行该事件。</span><span class="sxs-lookup"><span data-stu-id="f85e2-132">If the user clicks the **Cancel** button while `LongTask` is running, the `Button2_Click` event is executed as soon as the `DoEvents` statement allows event processing to occur.</span></span> <span data-ttu-id="f85e2-133">类级别变量 `mblnCancel` 设置为 `True` ， `mWidget_PercentDone` 然后事件对其进行测试，并将 `ByRef Cancel` 参数设置为 `True` 。</span><span class="sxs-lookup"><span data-stu-id="f85e2-133">The class-level variable `mblnCancel` is set to `True`, and the `mWidget_PercentDone` event then tests it and sets the `ByRef Cancel` argument to `True`.</span></span>  
  
## <a name="connecting-a-withevents-variable-to-an-object"></a><span data-ttu-id="f85e2-134">将 WithEvents 变量连接到对象</span><span class="sxs-lookup"><span data-stu-id="f85e2-134">Connecting a WithEvents Variable to an Object</span></span>  

 <span data-ttu-id="f85e2-135">`Form1` 现已设置为处理 `Widget` 对象的事件。</span><span class="sxs-lookup"><span data-stu-id="f85e2-135">`Form1` is now set up to handle a `Widget` object's events.</span></span> <span data-ttu-id="f85e2-136">剩下的就是找到某个 `Widget` 地方。</span><span class="sxs-lookup"><span data-stu-id="f85e2-136">All that remains is to find a `Widget` somewhere.</span></span>  
  
 <span data-ttu-id="f85e2-137">当在设计时声明变量时 `WithEvents` ，没有与之关联的对象。</span><span class="sxs-lookup"><span data-stu-id="f85e2-137">When you declare a variable `WithEvents` at design time, no object is associated with it.</span></span> <span data-ttu-id="f85e2-138">`WithEvents`变量与任何其他对象变量一样。</span><span class="sxs-lookup"><span data-stu-id="f85e2-138">A `WithEvents` variable is just like any other object variable.</span></span> <span data-ttu-id="f85e2-139">您必须创建一个对象，并使用变量为其分配一个引用 `WithEvents` 。</span><span class="sxs-lookup"><span data-stu-id="f85e2-139">You have to create an object and assign a reference to it with the `WithEvents` variable.</span></span>  
  
#### <a name="to-create-an-object-and-assign-a-reference-to-it"></a><span data-ttu-id="f85e2-140">创建对象并为其分配引用</span><span class="sxs-lookup"><span data-stu-id="f85e2-140">To create an object and assign a reference to it</span></span>  
  
1. <span data-ttu-id="f85e2-141">从 **代码编辑器** 的左侧下拉列表中选择 " **(Form1 事件")** 。</span><span class="sxs-lookup"><span data-stu-id="f85e2-141">Select **(Form1 Events)** from the left drop-down list in the **Code Editor**.</span></span>  
  
2. <span data-ttu-id="f85e2-142">`Load`从右侧下拉列表中选择事件。</span><span class="sxs-lookup"><span data-stu-id="f85e2-142">Select the `Load` event from the right drop-down list.</span></span> <span data-ttu-id="f85e2-143">" **代码编辑器** " 将打开 `Form1_Load` 事件过程。</span><span class="sxs-lookup"><span data-stu-id="f85e2-143">The **Code Editor** opens the `Form1_Load` event procedure.</span></span>  
  
3. <span data-ttu-id="f85e2-144">为事件过程添加以下代码 `Form1_Load` 以创建 `Widget` ：</span><span class="sxs-lookup"><span data-stu-id="f85e2-144">Add the following code for the `Form1_Load` event procedure to create the `Widget`:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#7)]  
  
 <span data-ttu-id="f85e2-145">执行此代码时，Visual Basic 将创建一个 `Widget` 对象，并将其事件连接到与关联的事件过程 `mWidget` 。</span><span class="sxs-lookup"><span data-stu-id="f85e2-145">When this code executes, Visual Basic creates a `Widget` object and connects its events to the event procedures associated with `mWidget`.</span></span> <span data-ttu-id="f85e2-146">从该点开始，无论何时 `Widget` 引发 `PercentDone` 事件，都将 `mWidget_PercentDone` 执行事件过程。</span><span class="sxs-lookup"><span data-stu-id="f85e2-146">From that point on, whenever the `Widget` raises its `PercentDone` event, the `mWidget_PercentDone` event procedure is executed.</span></span>  
  
#### <a name="to-call-the-longtask-method"></a><span data-ttu-id="f85e2-147">调用 LongTask 方法</span><span class="sxs-lookup"><span data-stu-id="f85e2-147">To call the LongTask method</span></span>  
  
- <span data-ttu-id="f85e2-148">将以下代码添加到 `Button1_Click` 事件处理程序中：</span><span class="sxs-lookup"><span data-stu-id="f85e2-148">Add the following code to the `Button1_Click` event handler:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#8)]  
  
 <span data-ttu-id="f85e2-149">在 `LongTask` 调用方法之前，必须初始化显示完成百分比的标签，并且 `Boolean` 用于取消方法的类级别标志必须设置为 `False` 。</span><span class="sxs-lookup"><span data-stu-id="f85e2-149">Before the `LongTask` method is called, the label that displays the percent complete must be initialized, and the class-level `Boolean` flag for canceling the method must be set to `False`.</span></span>  
  
 <span data-ttu-id="f85e2-150">`LongTask` 调用时，任务持续时间为12.2 秒。</span><span class="sxs-lookup"><span data-stu-id="f85e2-150">`LongTask` is called with a task duration of 12.2 seconds.</span></span> <span data-ttu-id="f85e2-151">`PercentDone`每隔一秒引发一次事件。</span><span class="sxs-lookup"><span data-stu-id="f85e2-151">The `PercentDone` event is raised once every one-third of a second.</span></span> <span data-ttu-id="f85e2-152">每次引发事件时， `mWidget_PercentDone` 都会执行事件过程。</span><span class="sxs-lookup"><span data-stu-id="f85e2-152">Each time the event is raised, the `mWidget_PercentDone` event procedure is executed.</span></span>  
  
 <span data-ttu-id="f85e2-153">`LongTask`完成后， `mblnCancel` 将测试，以查看是否 `LongTask` 正常结束，或是否由于 `mblnCancel` 设置为而停止 `True` 。</span><span class="sxs-lookup"><span data-stu-id="f85e2-153">When `LongTask` is done, `mblnCancel` is tested to see if `LongTask` ended normally, or if it stopped because `mblnCancel` was set to `True`.</span></span> <span data-ttu-id="f85e2-154">只有在前一种情况下才会更新完成百分比。</span><span class="sxs-lookup"><span data-stu-id="f85e2-154">The percent complete is updated only in the former case.</span></span>  
  
#### <a name="to-run-the-program"></a><span data-ttu-id="f85e2-155">运行程序</span><span class="sxs-lookup"><span data-stu-id="f85e2-155">To run the program</span></span>  
  
1. <span data-ttu-id="f85e2-156">按 F5 将项目置于运行模式。</span><span class="sxs-lookup"><span data-stu-id="f85e2-156">Press F5 to put the project in run mode.</span></span>  
  
2. <span data-ttu-id="f85e2-157">单击 " **启动任务** " 按钮。</span><span class="sxs-lookup"><span data-stu-id="f85e2-157">Click the **Start Task** button.</span></span> <span data-ttu-id="f85e2-158">每次 `PercentDone` 引发事件时，都会将标签更新为已完成的任务的百分比。</span><span class="sxs-lookup"><span data-stu-id="f85e2-158">Each time the `PercentDone` event is raised, the label is updated with the percentage of the task that is complete.</span></span>  
  
3. <span data-ttu-id="f85e2-159">单击 " **取消** " 按钮停止任务。</span><span class="sxs-lookup"><span data-stu-id="f85e2-159">Click the **Cancel** button to stop the task.</span></span> <span data-ttu-id="f85e2-160">请注意，当你单击 " **取消** " 按钮时，该按钮的外观不会立即更改。</span><span class="sxs-lookup"><span data-stu-id="f85e2-160">Notice that the appearance of the **Cancel** button does not change immediately when you click it.</span></span> <span data-ttu-id="f85e2-161">`Click`只有 `My.Application.DoEvents` 语句允许事件处理后，才能发生事件。</span><span class="sxs-lookup"><span data-stu-id="f85e2-161">The `Click` event cannot happen until the `My.Application.DoEvents` statement allows event processing.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="f85e2-162">`My.Application.DoEvents`方法不以与窗体相同的方式处理事件。</span><span class="sxs-lookup"><span data-stu-id="f85e2-162">The `My.Application.DoEvents` method does not process events in exactly the same way as the form does.</span></span> <span data-ttu-id="f85e2-163">例如，在本演练中，必须单击 " **取消** " 按钮两次。</span><span class="sxs-lookup"><span data-stu-id="f85e2-163">For example, in this walkthrough, you must click the **Cancel** button twice.</span></span> <span data-ttu-id="f85e2-164">若要允许窗体直接处理事件，可以使用多线程处理。</span><span class="sxs-lookup"><span data-stu-id="f85e2-164">To allow the form to handle the events directly, you can use multithreading.</span></span> <span data-ttu-id="f85e2-165">有关详细信息，请参阅 [托管线程处理](../../../../standard/threading/index.md)。</span><span class="sxs-lookup"><span data-stu-id="f85e2-165">For more information, see [Managed Threading](../../../../standard/threading/index.md).</span></span>
  
 <span data-ttu-id="f85e2-166">你可能会发现，通过 F11 运行程序并单步执行代码行来单步执行代码是有益的。</span><span class="sxs-lookup"><span data-stu-id="f85e2-166">You may find it instructive to run the program with F11 and step through the code a line at a time.</span></span> <span data-ttu-id="f85e2-167">您可以清楚地了解执行的输入方式 `LongTask` ，然后在 `Form1` 每次引发事件时短暂重新进入 `PercentDone` 。</span><span class="sxs-lookup"><span data-stu-id="f85e2-167">You can clearly see how execution enters `LongTask`, and then briefly re-enters `Form1` each time the `PercentDone` event is raised.</span></span>  
  
 <span data-ttu-id="f85e2-168">如果在的代码中返回执行时，会发生什么情况， `Form1` `LongTask` 再次调用该方法呢？</span><span class="sxs-lookup"><span data-stu-id="f85e2-168">What would happen if, while execution was back in the code of `Form1`, the `LongTask` method were called again?</span></span> <span data-ttu-id="f85e2-169">在最糟糕的情况下，如果 `LongTask` 每次引发事件时调用，则可能会发生堆栈溢出。</span><span class="sxs-lookup"><span data-stu-id="f85e2-169">At worst, a stack overflow might occur if `LongTask` were called every time the event was raised.</span></span>  
  
 <span data-ttu-id="f85e2-170">您可以通过将对新的引用分配给，使变量 `mWidget` 处理不同对象的事件 `Widget` `Widget` `mWidget` 。</span><span class="sxs-lookup"><span data-stu-id="f85e2-170">You can cause the variable `mWidget` to handle events for a different `Widget` object by assigning a reference to the new `Widget` to `mWidget`.</span></span> <span data-ttu-id="f85e2-171">事实上， `Button1_Click` 每次单击按钮时，都可以使代码执行此操作。</span><span class="sxs-lookup"><span data-stu-id="f85e2-171">In fact, you can make the code in `Button1_Click` do this every time you click the button.</span></span>  
  
#### <a name="to-handle-events-for-a-different-widget"></a><span data-ttu-id="f85e2-172">处理不同小组件的事件</span><span class="sxs-lookup"><span data-stu-id="f85e2-172">To handle events for a different widget</span></span>  
  
- <span data-ttu-id="f85e2-173">将以下代码行添加到 `Button1_Click` 过程中，紧靠在读取的行之前 `mWidget.LongTask(12.2, 0.33)` ：</span><span class="sxs-lookup"><span data-stu-id="f85e2-173">Add the following line of code to the `Button1_Click` procedure, immediately preceding the line that reads `mWidget.LongTask(12.2, 0.33)`:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#9)]  
  
 <span data-ttu-id="f85e2-174">每次单击按钮时，上面的代码都会创建一个新的 `Widget` 。</span><span class="sxs-lookup"><span data-stu-id="f85e2-174">The code above creates a new `Widget` each time the button is clicked.</span></span> <span data-ttu-id="f85e2-175">`LongTask`方法完成后，将立即释放对的引用 `Widget` 并 `Widget` 销毁。</span><span class="sxs-lookup"><span data-stu-id="f85e2-175">As soon as the `LongTask` method completes, the reference to the `Widget` is released, and the `Widget` is destroyed.</span></span>  
  
 <span data-ttu-id="f85e2-176">一个 `WithEvents` 变量一次只能包含一个对象引用，因此，如果您向分配不同的 `Widget` 对象 `mWidget` ，则不会 `Widget` 再处理上一个对象的事件。</span><span class="sxs-lookup"><span data-stu-id="f85e2-176">A `WithEvents` variable can contain only one object reference at a time, so if you assign a different `Widget` object to `mWidget`, the previous `Widget` object's events will no longer be handled.</span></span> <span data-ttu-id="f85e2-177">如果 `mWidget` 是唯一包含对旧对象的引用的对象变量 `Widget` ，则销毁该对象。</span><span class="sxs-lookup"><span data-stu-id="f85e2-177">If `mWidget` is the only object variable containing a reference to the old `Widget`, the object is destroyed.</span></span> <span data-ttu-id="f85e2-178">如果要处理来自多个对象的事件 `Widget` ，请使用 `AddHandler` 语句分别处理每个对象中的事件。</span><span class="sxs-lookup"><span data-stu-id="f85e2-178">If you want to handle events from several `Widget` objects, use the `AddHandler` statement to process events from each object separately.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f85e2-179">您可以根据需要声明多个 `WithEvents` 变量，但 `WithEvents` 不支持变量的数组。</span><span class="sxs-lookup"><span data-stu-id="f85e2-179">You can declare as many `WithEvents` variables as you need, but arrays of `WithEvents` variables are not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f85e2-180">请参阅</span><span class="sxs-lookup"><span data-stu-id="f85e2-180">See also</span></span>

- [<span data-ttu-id="f85e2-181">演练：声明和引发事件</span><span class="sxs-lookup"><span data-stu-id="f85e2-181">Walkthrough: Declaring and Raising Events</span></span>](walkthrough-declaring-and-raising-events.md)
- [<span data-ttu-id="f85e2-182">事件</span><span class="sxs-lookup"><span data-stu-id="f85e2-182">Events</span></span>](index.md)
