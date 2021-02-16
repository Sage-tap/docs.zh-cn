---
description: '了解详细信息：委托 (Visual Basic) '
title: 委托
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [Visual Basic]
- Visual Basic code, delegates
ms.assetid: 410b60dc-5e60-4ec0-bfae-426755a2ee28
ms.openlocfilehash: aba3c1483f2875600d925ec3edb0167ddfb18125
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100434428"
---
# <a name="delegates-visual-basic"></a><span data-ttu-id="7898b-103">委托 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7898b-103">Delegates (Visual Basic)</span></span>

<span data-ttu-id="7898b-104">委托是引用方法的对象。</span><span class="sxs-lookup"><span data-stu-id="7898b-104">Delegates are objects that refer to methods.</span></span> <span data-ttu-id="7898b-105">有时亦称为 *类型安全函数指针*，因为它们与其他编程语言中使用的函数指针类似。</span><span class="sxs-lookup"><span data-stu-id="7898b-105">They are sometimes described as *type-safe function pointers* because they are similar to function pointers used in other programming languages.</span></span> <span data-ttu-id="7898b-106">但与函数指针不同的是，Visual Basic 委托是基于类的引用类型 <xref:System.Delegate?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="7898b-106">But unlike function pointers, Visual Basic delegates are a reference type based on the class <xref:System.Delegate?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7898b-107">委托既可以引用共享方法（无需特定类实例即可调用的方法），也可以引用实例方法。</span><span class="sxs-lookup"><span data-stu-id="7898b-107">Delegates can reference both shared methods — methods that can be called without a specific instance of a class — and instance methods.</span></span>

## <a name="delegates-and-events"></a><span data-ttu-id="7898b-108">委托和事件</span><span class="sxs-lookup"><span data-stu-id="7898b-108">Delegates and Events</span></span>

<span data-ttu-id="7898b-109">在过程调用方和被调用的过程之间需要中介的情况下，委托非常有用。</span><span class="sxs-lookup"><span data-stu-id="7898b-109">Delegates are useful in situations where you need an intermediary between a calling procedure and the procedure being called.</span></span> <span data-ttu-id="7898b-110">例如，你希望引发事件的对象能够在不同的情况下调用不同的事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="7898b-110">For example, you might want an object that raises events to be able to call different event handlers under different circumstances.</span></span> <span data-ttu-id="7898b-111">遗憾的是，引发事件的对象无法提前确定用于处理特定事件的事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="7898b-111">Unfortunately, the object raising the events cannot know ahead of time which event handler is handling a specific event.</span></span> <span data-ttu-id="7898b-112">使用 Visual Basic，可以在使用语句时，通过创建委托，动态地将事件处理程序与事件关联 `AddHandler` 。</span><span class="sxs-lookup"><span data-stu-id="7898b-112">Visual Basic lets you dynamically associate event handlers with events by creating a delegate for you when you use the `AddHandler` statement.</span></span> <span data-ttu-id="7898b-113">在运行时，委托会将调用转接到相应的事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="7898b-113">At run time, the delegate forwards calls to the appropriate event handler.</span></span>

<span data-ttu-id="7898b-114">虽然您可以创建自己的委托，但在大多数情况下 Visual Basic 会创建委托并处理详细信息。</span><span class="sxs-lookup"><span data-stu-id="7898b-114">Although you can create your own delegates, in most cases Visual Basic creates the delegate and takes care of the details for you.</span></span> <span data-ttu-id="7898b-115">例如，`Event` 语句将 `<EventName>EventHandler` 委托类隐式定义为包含 `Event` 语句的类的嵌套类，并且具有与事件相同的签名。</span><span class="sxs-lookup"><span data-stu-id="7898b-115">For example, an `Event` statement implicitly defines a delegate class named `<EventName>EventHandler` as a nested class of the class containing the `Event` statement, and with the same signature as the event.</span></span> <span data-ttu-id="7898b-116">`AddressOf` 语句隐式创建引用特定过程的委托的实例。</span><span class="sxs-lookup"><span data-stu-id="7898b-116">The `AddressOf` statement implicitly creates an instance of a delegate that refers to a specific procedure.</span></span> <span data-ttu-id="7898b-117">下面两行代码是等同的。</span><span class="sxs-lookup"><span data-stu-id="7898b-117">The following two lines of code are equivalent.</span></span> <span data-ttu-id="7898b-118">第一行代码显式创建 `EventHandler` 的实例，将对方法 `Button1_Click` 的引用作为自变量发送。</span><span class="sxs-lookup"><span data-stu-id="7898b-118">In the first line, you see the explicit creation of an instance of `EventHandler`, with a reference to method `Button1_Click` sent as the argument.</span></span> <span data-ttu-id="7898b-119">第二行代码是执行相同操作的更简便方式。</span><span class="sxs-lookup"><span data-stu-id="7898b-119">The second line is a more convenient way to do the same thing.</span></span>

[!code-vb[VbVbalrDelegates#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#6)]

<span data-ttu-id="7898b-120">只要编译器可通过上下文确定委托类型，就可以采用更简便的方式来创建委托。</span><span class="sxs-lookup"><span data-stu-id="7898b-120">You can use the shorthand way of creating delegates anywhere the compiler can determine the delegate's type by the context.</span></span>

## <a name="declaring-events-that-use-an-existing-delegate-type"></a><span data-ttu-id="7898b-121">声明使用现有委托类型的事件</span><span class="sxs-lookup"><span data-stu-id="7898b-121">Declaring Events that Use an Existing Delegate Type</span></span>

<span data-ttu-id="7898b-122">在某些情况下，你可能希望将事件声明为使用现有委托类型作为其基础委托。</span><span class="sxs-lookup"><span data-stu-id="7898b-122">In some situations, you may want to declare an event to use an existing delegate type as its underlying delegate.</span></span> <span data-ttu-id="7898b-123">下面的语法展示了具体做法：</span><span class="sxs-lookup"><span data-stu-id="7898b-123">The following syntax demonstrates how:</span></span>

[!code-vb[VbVbalrDelegates#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#7)]

<span data-ttu-id="7898b-124">如果要将多个事件路由到同一处理程序，就会发现这非常有用。</span><span class="sxs-lookup"><span data-stu-id="7898b-124">This is useful when you want to route multiple events to the same handler.</span></span>

## <a name="delegate-variables-and-parameters"></a><span data-ttu-id="7898b-125">委托变量和参数</span><span class="sxs-lookup"><span data-stu-id="7898b-125">Delegate Variables and Parameters</span></span>

<span data-ttu-id="7898b-126">可以将委托用于与事件无关的其他任务（如自由线程），或将委托与需要在运行时调用不同版本函数的过程结合使用。</span><span class="sxs-lookup"><span data-stu-id="7898b-126">You can use delegates for other, non-event related tasks, such as free threading or with procedures that need to call different versions of functions at run time.</span></span>

<span data-ttu-id="7898b-127">例如，假设你有一个分类广告应用程序，其中包含一个显示汽车名称的列表框。</span><span class="sxs-lookup"><span data-stu-id="7898b-127">For example, suppose you have a classified-ad application that includes a list box with the names of cars.</span></span> <span data-ttu-id="7898b-128">广告按标题（通常是汽车品牌）进行排序。</span><span class="sxs-lookup"><span data-stu-id="7898b-128">The ads are sorted by title, which is normally the make of the car.</span></span> <span data-ttu-id="7898b-129">如果一些汽车品牌前有汽车出厂年份，可能就会遇到问题。</span><span class="sxs-lookup"><span data-stu-id="7898b-129">A problem you may face occurs when some cars include the year of the car before the make.</span></span> <span data-ttu-id="7898b-130">即列表框的内置排序功能只能按字符代码排序；它会先列出标题以日期开头的所有广告，然后列出标题以品牌开头的广告。</span><span class="sxs-lookup"><span data-stu-id="7898b-130">The problem is that the built-in sort functionality of the list box sorts only by character codes; it places all the ads starting with dates first, followed by the ads starting with the make.</span></span>

<span data-ttu-id="7898b-131">若要解决此问题，可以在类中创建以下排序过程：对大多数列表框使用标准的按字母顺序排序，但可在运行时为汽车广告切换到自定义排序过程。</span><span class="sxs-lookup"><span data-stu-id="7898b-131">To fix this, you can create a sort procedure in a class that uses the standard alphabetic sort on most list boxes, but is able to switch at run time to the custom sort procedure for car ads.</span></span> <span data-ttu-id="7898b-132">为此，可以使用委托在运行时将自定义排序过程传递给排序类。</span><span class="sxs-lookup"><span data-stu-id="7898b-132">To do this, you pass the custom sort procedure to the sort class at run time, using delegates.</span></span>

## <a name="addressof-and-lambda-expressions"></a><span data-ttu-id="7898b-133">AddressOf 和 Lambda 表达式</span><span class="sxs-lookup"><span data-stu-id="7898b-133">AddressOf and Lambda Expressions</span></span>

<span data-ttu-id="7898b-134">每个委托类均可定义将对象方法指定传递到的构造函数。</span><span class="sxs-lookup"><span data-stu-id="7898b-134">Each delegate class defines a constructor that is passed the specification of an object method.</span></span> <span data-ttu-id="7898b-135">委托构造函数的自变量必须是对方法的引用或 lambda 表达式。</span><span class="sxs-lookup"><span data-stu-id="7898b-135">An argument to a delegate constructor must be a reference to a method, or a lambda expression.</span></span>

<span data-ttu-id="7898b-136">若要指定对方法的引用，请使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="7898b-136">To specify a reference to a method, use the following syntax:</span></span>

<span data-ttu-id="7898b-137">`AddressOf` [`expression`.]`methodName`</span><span class="sxs-lookup"><span data-stu-id="7898b-137">`AddressOf` [`expression`.]`methodName`</span></span>

<span data-ttu-id="7898b-138">`expression` 的编译时类型必须是类或接口的名称，此类或接口包含指定名称的方法，其签名与委托类的签名一致。</span><span class="sxs-lookup"><span data-stu-id="7898b-138">The compile-time type of the `expression` must be the name of a class or an interface that contains a method of the specified name whose signature matches the signature of the delegate class.</span></span> <span data-ttu-id="7898b-139">`methodName` 可以是共享方法，也可以是实例方法。</span><span class="sxs-lookup"><span data-stu-id="7898b-139">The `methodName` can be either a shared method or an instance method.</span></span> <span data-ttu-id="7898b-140">即使为类的默认方法创建委托，`methodName` 也不是可选的。</span><span class="sxs-lookup"><span data-stu-id="7898b-140">The `methodName` is not optional, even if you create a delegate for the default method of the class.</span></span>

<span data-ttu-id="7898b-141">若要指定 lambda 表达式，请使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="7898b-141">To specify a lambda expression, use the following syntax:</span></span>

<span data-ttu-id="7898b-142">`Function` ([`parm` As `type`, `parm2` As `type2`, ...]) `expression`</span><span class="sxs-lookup"><span data-stu-id="7898b-142">`Function` ([`parm` As `type`, `parm2` As `type2`, ...]) `expression`</span></span>

<span data-ttu-id="7898b-143">下面的示例展示了用于为委托指定引用的 `AddressOf` 和 lambda 表达式。</span><span class="sxs-lookup"><span data-stu-id="7898b-143">The following example shows both `AddressOf` and lambda expressions used to specify the reference for a delegate.</span></span>

[!code-vb[VbVbalrDelegates#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class2.vb#15)]

<span data-ttu-id="7898b-144">函数的签名必须与委托类型的签名一致。</span><span class="sxs-lookup"><span data-stu-id="7898b-144">The signature of the function must match that of the delegate type.</span></span> <span data-ttu-id="7898b-145">有关 lambda 表达式的详细信息，请参阅 [Lambda 表达式](../procedures/lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="7898b-145">For more information about lambda expressions, see [Lambda Expressions](../procedures/lambda-expressions.md).</span></span> <span data-ttu-id="7898b-146">有关委托的 lambda 表达式和 `AddressOf` 赋值的更多示例，请参阅[宽松委托转换](relaxed-delegate-conversion.md)。</span><span class="sxs-lookup"><span data-stu-id="7898b-146">For more examples of lambda expression and `AddressOf` assignments to delegates, see [Relaxed Delegate Conversion](relaxed-delegate-conversion.md).</span></span>

## <a name="related-topics"></a><span data-ttu-id="7898b-147">相关主题</span><span class="sxs-lookup"><span data-stu-id="7898b-147">Related Topics</span></span>

|<span data-ttu-id="7898b-148">Title</span><span class="sxs-lookup"><span data-stu-id="7898b-148">Title</span></span>|<span data-ttu-id="7898b-149">说明</span><span class="sxs-lookup"><span data-stu-id="7898b-149">Description</span></span>|
|-----------|-----------------|
|[<span data-ttu-id="7898b-150">如何：调用委托方法</span><span class="sxs-lookup"><span data-stu-id="7898b-150">How to: Invoke a Delegate Method</span></span>](how-to-invoke-a-delegate-method.md)|<span data-ttu-id="7898b-151">通过示例展示了如何将方法与委托相关联，然后通过委托调用相应的方法。</span><span class="sxs-lookup"><span data-stu-id="7898b-151">Provides an example that shows how to associate a method with a delegate and then invoke that method through the delegate.</span></span>|
|[<span data-ttu-id="7898b-152">如何：在 Visual Basic 中将过程传递给另一过程</span><span class="sxs-lookup"><span data-stu-id="7898b-152">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](how-to-pass-procedures-to-another-procedure.md)|<span data-ttu-id="7898b-153">介绍了如何使用委托将一个过程传递给另一个过程。</span><span class="sxs-lookup"><span data-stu-id="7898b-153">Demonstrates how to use delegates to pass one procedure to another procedure.</span></span>|
|[<span data-ttu-id="7898b-154">宽松委托转换</span><span class="sxs-lookup"><span data-stu-id="7898b-154">Relaxed Delegate Conversion</span></span>](relaxed-delegate-conversion.md)|<span data-ttu-id="7898b-155">介绍了如何向委托或处理程序分配 Sub 和函数，即使是在它们的签名不一致时</span><span class="sxs-lookup"><span data-stu-id="7898b-155">Describes how you can assign subs and functions to delegates or handlers even when their signatures are not identical</span></span>|
|[<span data-ttu-id="7898b-156">事件</span><span class="sxs-lookup"><span data-stu-id="7898b-156">Events</span></span>](../events/index.md)|<span data-ttu-id="7898b-157">概述了 Visual Basic 中的事件。</span><span class="sxs-lookup"><span data-stu-id="7898b-157">Provides an overview of events in Visual Basic.</span></span>|
