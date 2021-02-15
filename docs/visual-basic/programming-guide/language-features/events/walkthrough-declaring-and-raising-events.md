---
description: '了解详细信息：演练：声明和引发事件 (Visual Basic) '
title: 声明和引发事件
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], events
- events [Visual Basic], walkthroughs
- declaring events [Visual Basic], walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events [Visual Basic], walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
ms.openlocfilehash: 98e9d2eabd1ace06de9f8cc7931013093d864e7a
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466375"
---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a><span data-ttu-id="b9f59-103">演练：声明和引发事件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9f59-103">Walkthrough: Declaring and Raising Events (Visual Basic)</span></span>

<span data-ttu-id="b9f59-104">本演练演示如何声明和引发名为的类的事件 `Widget` 。</span><span class="sxs-lookup"><span data-stu-id="b9f59-104">This walkthrough demonstrates how to declare and raise events for a class named `Widget`.</span></span> <span data-ttu-id="b9f59-105">完成这些步骤后，你可能需要阅读相关主题 [演练：处理事件](walkthrough-handling-events.md)，其中演示了如何使用对象中的事件 `Widget` 在应用程序中提供状态信息。</span><span class="sxs-lookup"><span data-stu-id="b9f59-105">After you complete the steps, you might want to read the companion topic, [Walkthrough: Handling Events](walkthrough-handling-events.md), which shows how to use events from `Widget` objects to provide status information in an application.</span></span>  
  
## <a name="the-widget-class"></a><span data-ttu-id="b9f59-106">小组件类</span><span class="sxs-lookup"><span data-stu-id="b9f59-106">The Widget Class</span></span>  

 <span data-ttu-id="b9f59-107">假设你有一个 `Widget` 类。</span><span class="sxs-lookup"><span data-stu-id="b9f59-107">Assume for the moment that you have a `Widget` class.</span></span> <span data-ttu-id="b9f59-108">你的 `Widget` 类有一个可能需要很长时间才能执行的方法，并且你希望你的应用程序能够提供某种类型的完成指示器。</span><span class="sxs-lookup"><span data-stu-id="b9f59-108">Your `Widget` class has a method that can take a long time to execute, and you want your application to be able to put up some kind of completion indicator.</span></span>  
  
 <span data-ttu-id="b9f59-109">当然，您可以使 `Widget` 对象显示一个完成百分比对话框，但随后在您使用该类的每个项目中都将出现该对话框 `Widget` 。</span><span class="sxs-lookup"><span data-stu-id="b9f59-109">Of course, you could make the `Widget` object show a percent-complete dialog box, but then you would be stuck with that dialog box in every project in which you used the `Widget` class.</span></span> <span data-ttu-id="b9f59-110">对象设计的一个很好的原则是让使用对象的应用程序处理用户界面，除非对象的全部用途是管理窗体或对话框。</span><span class="sxs-lookup"><span data-stu-id="b9f59-110">A good principle of object design is to let the application that uses an object handle the user interface—unless the whole purpose of the object is to manage a form or dialog box.</span></span>  
  
 <span data-ttu-id="b9f59-111">的用途 `Widget` 是执行其他任务，因此最好添加一个 `PercentDone` 事件并让调用 `Widget` 的方法的过程处理该事件并显示状态更新。</span><span class="sxs-lookup"><span data-stu-id="b9f59-111">The purpose of `Widget` is to perform other tasks, so it is better to add a `PercentDone` event and let the procedure that calls `Widget`'s methods handle that event and display status updates.</span></span> <span data-ttu-id="b9f59-112">`PercentDone`事件还可以提供取消任务的机制。</span><span class="sxs-lookup"><span data-stu-id="b9f59-112">The `PercentDone` event can also provide a mechanism for canceling the task.</span></span>  
  
#### <a name="to-build-the-code-example-for-this-topic"></a><span data-ttu-id="b9f59-113">生成本主题的代码示例</span><span class="sxs-lookup"><span data-stu-id="b9f59-113">To build the code example for this topic</span></span>  
  
1. <span data-ttu-id="b9f59-114">打开一个新的 Visual Basic Windows 应用程序项目，并创建一个名为的窗体 `Form1` 。</span><span class="sxs-lookup"><span data-stu-id="b9f59-114">Open a new Visual Basic Windows Application project and create a form named `Form1`.</span></span>  
  
2. <span data-ttu-id="b9f59-115">向添加两个按钮和一个标签 `Form1` 。</span><span class="sxs-lookup"><span data-stu-id="b9f59-115">Add two buttons and a label to `Form1`.</span></span>  
  
3. <span data-ttu-id="b9f59-116">按下表所示命名对象。</span><span class="sxs-lookup"><span data-stu-id="b9f59-116">Name the objects as shown in the following table.</span></span>  
  
    |<span data-ttu-id="b9f59-117">Object</span><span class="sxs-lookup"><span data-stu-id="b9f59-117">Object</span></span>|<span data-ttu-id="b9f59-118">属性</span><span class="sxs-lookup"><span data-stu-id="b9f59-118">Property</span></span>|<span data-ttu-id="b9f59-119">设置</span><span class="sxs-lookup"><span data-stu-id="b9f59-119">Setting</span></span>|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|<span data-ttu-id="b9f59-120">启动任务</span><span class="sxs-lookup"><span data-stu-id="b9f59-120">Start Task</span></span>|  
    |`Button2`|`Text`|<span data-ttu-id="b9f59-121">取消</span><span class="sxs-lookup"><span data-stu-id="b9f59-121">Cancel</span></span>|  
    |`Label`|<span data-ttu-id="b9f59-122">`(Name)`, `Text`</span><span class="sxs-lookup"><span data-stu-id="b9f59-122">`(Name)`, `Text`</span></span>|<span data-ttu-id="b9f59-123">lblPercentDone，0</span><span class="sxs-lookup"><span data-stu-id="b9f59-123">lblPercentDone, 0</span></span>|  
  
4. <span data-ttu-id="b9f59-124">在 " **项目** " 菜单上，选择 " **添加类** "，将名为的类添加 `Widget.vb` 到项目。</span><span class="sxs-lookup"><span data-stu-id="b9f59-124">On the **Project** menu, choose **Add Class** to add a class named `Widget.vb` to the project.</span></span>  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a><span data-ttu-id="b9f59-125">为小组件类声明事件</span><span class="sxs-lookup"><span data-stu-id="b9f59-125">To declare an event for the Widget class</span></span>  
  
- <span data-ttu-id="b9f59-126">使用 `Event` 关键字声明类中的事件 `Widget` 。</span><span class="sxs-lookup"><span data-stu-id="b9f59-126">Use the `Event` keyword to declare an event in the `Widget` class.</span></span> <span data-ttu-id="b9f59-127">请注意，事件可以具有 `ByVal` 和 `ByRef` 参数，如 `Widget` 事件所示 `PercentDone` ：</span><span class="sxs-lookup"><span data-stu-id="b9f59-127">Note that an event can have `ByVal` and `ByRef` arguments, as `Widget`'s `PercentDone` event demonstrates:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#1)]  
  
 <span data-ttu-id="b9f59-128">调用对象收到 `PercentDone` 事件时，该 `Percent` 参数包含已完成的任务的百分比。</span><span class="sxs-lookup"><span data-stu-id="b9f59-128">When the calling object receives a `PercentDone` event, the `Percent` argument contains the percentage of the task that is complete.</span></span> <span data-ttu-id="b9f59-129">`Cancel`参数可以设置为 `True` ，以取消引发事件的方法。</span><span class="sxs-lookup"><span data-stu-id="b9f59-129">The `Cancel` argument can be set to `True` to cancel the method that raised the event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b9f59-130">可以声明事件自变量，就像处理过程的参数一样，但有以下例外：事件不能包含 `Optional` 或 `ParamArray` 参数，并且事件没有返回值。</span><span class="sxs-lookup"><span data-stu-id="b9f59-130">You can declare event arguments just as you do arguments of procedures, with the following exceptions: Events cannot have `Optional` or `ParamArray` arguments, and events do not have return values.</span></span>  
  
 <span data-ttu-id="b9f59-131">此 `PercentDone` 事件由 `LongTask` 类的方法引发 `Widget` 。</span><span class="sxs-lookup"><span data-stu-id="b9f59-131">The `PercentDone` event is raised by the `LongTask` method of the `Widget` class.</span></span> <span data-ttu-id="b9f59-132">`LongTask` 采用两个参数：方法在经过一段时间后进行工作，并在暂停之前的最小时间间隔内 `LongTask` 引发 `PercentDone` 事件。</span><span class="sxs-lookup"><span data-stu-id="b9f59-132">`LongTask` takes two arguments: the length of time the method pretends to be doing work, and the minimum time interval before `LongTask` pauses to raise the `PercentDone` event.</span></span>  
  
#### <a name="to-raise-the-percentdone-event"></a><span data-ttu-id="b9f59-133">引发 PercentDone 事件</span><span class="sxs-lookup"><span data-stu-id="b9f59-133">To raise the PercentDone event</span></span>  
  
1. <span data-ttu-id="b9f59-134">若要简化对 `Timer` 此类使用的属性的访问，请将 `Imports` 语句添加到类模块的 "声明" 部分的顶部、语句的上方 `Class Widget` 。</span><span class="sxs-lookup"><span data-stu-id="b9f59-134">To simplify access to the `Timer` property used by this class, add an `Imports` statement to the top of the declarations section of your class module, above the `Class Widget` statement.</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#2)]  
  
2. <span data-ttu-id="b9f59-135">将以下代码添加到 `Widget` 类：</span><span class="sxs-lookup"><span data-stu-id="b9f59-135">Add the following code to the `Widget` class:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#3)]  
  
 <span data-ttu-id="b9f59-136">当应用程序调用 `LongTask` 方法时， `Widget` 类 `PercentDone` 每秒引发一次事件 `MinimumInterval` 。</span><span class="sxs-lookup"><span data-stu-id="b9f59-136">When your application calls the `LongTask` method, the `Widget` class raises the `PercentDone` event every `MinimumInterval` seconds.</span></span> <span data-ttu-id="b9f59-137">当事件返回时，将 `LongTask` 检查 `Cancel` 参数是否设置为 `True` 。</span><span class="sxs-lookup"><span data-stu-id="b9f59-137">When the event returns, `LongTask` checks to see if the `Cancel` argument was set to `True`.</span></span>  
  
 <span data-ttu-id="b9f59-138">此处有一些免责声明是必需的。</span><span class="sxs-lookup"><span data-stu-id="b9f59-138">A few disclaimers are necessary here.</span></span> <span data-ttu-id="b9f59-139">为简单起见，该 `LongTask` 过程假定您事先知道任务将花多长时间。</span><span class="sxs-lookup"><span data-stu-id="b9f59-139">For simplicity, the `LongTask` procedure assumes you know in advance how long the task will take.</span></span> <span data-ttu-id="b9f59-140">几乎不会出现这种情况。</span><span class="sxs-lookup"><span data-stu-id="b9f59-140">This is almost never the case.</span></span> <span data-ttu-id="b9f59-141">将任务划分为偶大的块可能比较困难，通常，用户最重要的是，用户只需经过一段时间，就能看出发生了什么情况。</span><span class="sxs-lookup"><span data-stu-id="b9f59-141">Dividing tasks into chunks of even size can be difficult, and often what matters most to users is simply the amount of time that passes before they get an indication that something is happening.</span></span>  
  
 <span data-ttu-id="b9f59-142">在此示例中，可能已发现另一个缺陷。</span><span class="sxs-lookup"><span data-stu-id="b9f59-142">You may have spotted another flaw in this sample.</span></span> <span data-ttu-id="b9f59-143">`Timer`属性返回从午夜开始经过的秒数; 因此，如果该应用程序在午夜之前启动，则会停滞。</span><span class="sxs-lookup"><span data-stu-id="b9f59-143">The `Timer` property returns the number of seconds that have passed since midnight; therefore, the application gets stuck if it is started just before midnight.</span></span> <span data-ttu-id="b9f59-144">更仔细地测量时间的方法会将这类边界情况（例如这种情况）考虑在内，或使用属性（例如）来避免这种情况 `Now` 。</span><span class="sxs-lookup"><span data-stu-id="b9f59-144">A more careful approach to measuring time would take boundary conditions such as this into consideration, or avoid them altogether, using properties such as `Now`.</span></span>  
  
 <span data-ttu-id="b9f59-145">由于 `Widget` 该类可以引发事件，因此你可以转到下一个演练。</span><span class="sxs-lookup"><span data-stu-id="b9f59-145">Now that the `Widget` class can raise events, you can move to the next walkthrough.</span></span> <span data-ttu-id="b9f59-146">[演练：处理事件](walkthrough-handling-events.md) 演示如何使用将 `WithEvents` 事件处理程序与 `PercentDone` 事件关联。</span><span class="sxs-lookup"><span data-stu-id="b9f59-146">[Walkthrough: Handling Events](walkthrough-handling-events.md) demonstrates how to use `WithEvents` to associate an event handler with the `PercentDone` event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9f59-147">请参阅</span><span class="sxs-lookup"><span data-stu-id="b9f59-147">See also</span></span>

- <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>
- <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>
- [<span data-ttu-id="b9f59-148">演练：处理事件</span><span class="sxs-lookup"><span data-stu-id="b9f59-148">Walkthrough: Handling Events</span></span>](walkthrough-handling-events.md)
- [<span data-ttu-id="b9f59-149">事件</span><span class="sxs-lookup"><span data-stu-id="b9f59-149">Events</span></span>](index.md)
