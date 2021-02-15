---
description: 了解详细信息： Visual Basic 中的过程
title: 过程
ms.date: 04/28/2017
helpviewer_keywords:
- procedures [Visual Basic], structured code
- Visual Basic code, procedures
- procedures [Visual Basic], types of
- structured code [Visual Basic], procedures
- procedures
ms.assetid: 9effbcf0-80a0-4d1a-98f4-2c6920592766
ms.openlocfilehash: faff01163511d71f6dc5c6fd540b292e1dea72fb
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475144"
---
# <a name="procedures-in-visual-basic"></a><span data-ttu-id="20bcb-103">Visual Basic 中的过程</span><span class="sxs-lookup"><span data-stu-id="20bcb-103">Procedures in Visual Basic</span></span>

<span data-ttu-id="20bcb-104">*过程* 是由声明语句括起来的 Visual Basic 语句块 `Function` ， (、 `Sub` 、 `Operator` 、 `Get` 、 `Set`) 和匹配 `End` 声明。</span><span class="sxs-lookup"><span data-stu-id="20bcb-104">A *procedure* is a block of Visual Basic statements enclosed by a declaration statement (`Function`, `Sub`, `Operator`, `Get`, `Set`) and a matching `End` declaration.</span></span> <span data-ttu-id="20bcb-105">Visual Basic 中的所有可执行语句都必须在某一过程中。</span><span class="sxs-lookup"><span data-stu-id="20bcb-105">All executable statements in Visual Basic must be within some procedure.</span></span>  
  
## <a name="calling-a-procedure"></a><span data-ttu-id="20bcb-106">调用过程</span><span class="sxs-lookup"><span data-stu-id="20bcb-106">Calling a Procedure</span></span>  

 <span data-ttu-id="20bcb-107">从代码中的其他位置调用过程。</span><span class="sxs-lookup"><span data-stu-id="20bcb-107">You invoke a procedure from some other place in the code.</span></span> <span data-ttu-id="20bcb-108">这称为过程调用。</span><span class="sxs-lookup"><span data-stu-id="20bcb-108">This is known as a *procedure call*.</span></span> <span data-ttu-id="20bcb-109">过程运行完毕后，会将控件返回到调用它的代码，称为调用代码。</span><span class="sxs-lookup"><span data-stu-id="20bcb-109">When the procedure is finished running, it returns control to the code that invoked it, which is known as the *calling code*.</span></span> <span data-ttu-id="20bcb-110">调用代码是一个语句或语句中的一个表达式，它通过名称指定过程并将控件转移给该过程。</span><span class="sxs-lookup"><span data-stu-id="20bcb-110">The calling code is a statement, or an expression within a statement, that specifies the procedure by name and transfers control to it.</span></span>  
  
## <a name="returning-from-a-procedure"></a><span data-ttu-id="20bcb-111">从过程中返回</span><span class="sxs-lookup"><span data-stu-id="20bcb-111">Returning from a Procedure</span></span>  

 <span data-ttu-id="20bcb-112">过程运行完毕后，会将控件返回给调用代码。</span><span class="sxs-lookup"><span data-stu-id="20bcb-112">A procedure returns control to the calling code when it has finished running.</span></span> <span data-ttu-id="20bcb-113">为此，它可以使用 [Return 语句](../../../language-reference/statements/return-statement.md)、该过程的适当 [Exit 语句](../../../language-reference/statements/exit-statement.md) 语句或过程的 [End \<keyword> 语句](../../../language-reference/statements/end-keyword-statement.md) 语句。</span><span class="sxs-lookup"><span data-stu-id="20bcb-113">To do this, it can use a [Return Statement](../../../language-reference/statements/return-statement.md), the appropriate [Exit Statement](../../../language-reference/statements/exit-statement.md) statement for the procedure, or the procedure's [End \<keyword> Statement](../../../language-reference/statements/end-keyword-statement.md) statement.</span></span> <span data-ttu-id="20bcb-114">然后控件在过程调用之后传递给调用代码。</span><span class="sxs-lookup"><span data-stu-id="20bcb-114">Control then passes to the calling code following the point of the procedure call.</span></span>  
  
- <span data-ttu-id="20bcb-115">使用 `Return` 语句，控件将立即返回到调用代码。</span><span class="sxs-lookup"><span data-stu-id="20bcb-115">With a `Return` statement, control returns immediately to the calling code.</span></span> <span data-ttu-id="20bcb-116">`Return` 语句之后的语句不会运行。</span><span class="sxs-lookup"><span data-stu-id="20bcb-116">Statements following the `Return` statement do not run.</span></span> <span data-ttu-id="20bcb-117">在同一过程中可拥有多个 `Return` 语句。</span><span class="sxs-lookup"><span data-stu-id="20bcb-117">You can have more than one `Return` statement in the same procedure.</span></span>  
  
- <span data-ttu-id="20bcb-118">使用 `Exit Sub` 或 `Exit Function` 语句，控件立即返回到调用代码。</span><span class="sxs-lookup"><span data-stu-id="20bcb-118">With an `Exit Sub` or `Exit Function` statement, control returns immediately to the calling code.</span></span> <span data-ttu-id="20bcb-119">`Exit` 语句之后的语句不会运行。</span><span class="sxs-lookup"><span data-stu-id="20bcb-119">Statements following the `Exit` statement do not run.</span></span> <span data-ttu-id="20bcb-120">在同一过程中可拥有多个 `Exit` 语句，也可混合 `Return` 和 `Exit` 语句。</span><span class="sxs-lookup"><span data-stu-id="20bcb-120">You can have more than one `Exit` statement in the same procedure, and you can mix `Return` and `Exit` statements in the same procedure.</span></span>  
  
- <span data-ttu-id="20bcb-121">如果一个过程没有 `Return` 或 `Exit` 语句，则在过程主体的最后一个语句之后以 `End Sub` 或 `End Function`、`End Get` 或 `End Set` 语句结尾。</span><span class="sxs-lookup"><span data-stu-id="20bcb-121">If a procedure has no `Return` or `Exit` statements, it concludes with an `End Sub` or `End Function`, `End Get`, or `End Set` statement following the last statement of the procedure body.</span></span> <span data-ttu-id="20bcb-122">`End` 语句立即将控件返回到调用代码。</span><span class="sxs-lookup"><span data-stu-id="20bcb-122">The `End` statement returns control immediately to the calling code.</span></span> <span data-ttu-id="20bcb-123">一个过程中只能有一个 `End` 语句。</span><span class="sxs-lookup"><span data-stu-id="20bcb-123">You can have only one `End` statement in a procedure.</span></span>  
  
## <a name="parameters-and-arguments"></a><span data-ttu-id="20bcb-124">形参和实参</span><span class="sxs-lookup"><span data-stu-id="20bcb-124">Parameters and Arguments</span></span>  

 <span data-ttu-id="20bcb-125">在大多数情况下，每次调用过程时，过程都需对不同数据进行操作。</span><span class="sxs-lookup"><span data-stu-id="20bcb-125">In most cases, a procedure needs to operate on different data each time you call it.</span></span> <span data-ttu-id="20bcb-126">可将此信息作为过程调用的一部分传递给该过程。</span><span class="sxs-lookup"><span data-stu-id="20bcb-126">You can pass this information to the procedure as part of the procedure call.</span></span> <span data-ttu-id="20bcb-127">过程定义零个或多个形参，每个形参表示一个该过程希望你传递给它的值。</span><span class="sxs-lookup"><span data-stu-id="20bcb-127">The procedure defines zero or more *parameters*, each of which represents a value it expects you to pass to it.</span></span> <span data-ttu-id="20bcb-128">过程调用中，与过程定义中每个形参相对应的是的实参。</span><span class="sxs-lookup"><span data-stu-id="20bcb-128">Corresponding to each parameter in the procedure definition is an *argument* in the procedure call.</span></span> <span data-ttu-id="20bcb-129">实参表示给定过程调用中传递给相应形参的值。</span><span class="sxs-lookup"><span data-stu-id="20bcb-129">An argument represents the value you pass to the corresponding parameter in a given procedure call.</span></span>  
  
## <a name="types-of-procedures"></a><span data-ttu-id="20bcb-130">过程类型</span><span class="sxs-lookup"><span data-stu-id="20bcb-130">Types of Procedures</span></span>  

 <span data-ttu-id="20bcb-131">Visual Basic 使用几种类型的过程：</span><span class="sxs-lookup"><span data-stu-id="20bcb-131">Visual Basic uses several types of procedures:</span></span>  
  
- <span data-ttu-id="20bcb-132">[Sub 过程](./sub-procedures.md)执行操作，但不向调用代码返回值。</span><span class="sxs-lookup"><span data-stu-id="20bcb-132">[Sub Procedures](./sub-procedures.md) perform actions but do not return a value to the calling code.</span></span>  
  
- <span data-ttu-id="20bcb-133">事件处理过程是为响应由用户操作所引发的事件或由程序中的发生所引发的事件而执行的 `Sub` 过程。</span><span class="sxs-lookup"><span data-stu-id="20bcb-133">Event-handling procedures are `Sub` procedures that execute in response to an event raised by user action or by an occurrence in a program.</span></span>  
  
- <span data-ttu-id="20bcb-134">[Function 过程](./function-procedures.md)向调用代码返回值。</span><span class="sxs-lookup"><span data-stu-id="20bcb-134">[Function Procedures](./function-procedures.md) return a value to the calling code.</span></span> <span data-ttu-id="20bcb-135">其可在返回前执行其他操作。</span><span class="sxs-lookup"><span data-stu-id="20bcb-135">They can perform other actions before returning.</span></span>

    <span data-ttu-id="20bcb-136">某些用 C# 编写的函数会返回引用返回值。</span><span class="sxs-lookup"><span data-stu-id="20bcb-136">Some functions written in C# return a *reference return value*.</span></span> <span data-ttu-id="20bcb-137">函数调用方可修改返回值，这种修改反映在被调用对象的状态中。</span><span class="sxs-lookup"><span data-stu-id="20bcb-137">Function callers can modify the return value, and this modification is reflected in the state of the called object.</span></span> <span data-ttu-id="20bcb-138">从 Visual Basic 2017 开始，Visual Basic 代码可以使用引用返回值，但不能返回引用的值。</span><span class="sxs-lookup"><span data-stu-id="20bcb-138">Starting with Visual Basic 2017, Visual Basic code can consume reference return values, although it cannot return a value by reference.</span></span> <span data-ttu-id="20bcb-139">有关详细信息，请参阅[引用返回值](ref-return-values.md)。</span><span class="sxs-lookup"><span data-stu-id="20bcb-139">For more information, see [Reference return values](ref-return-values.md).</span></span>
  
- <span data-ttu-id="20bcb-140">[属性过程](./property-procedures.md)返回并分配对象或模块上的属性值。</span><span class="sxs-lookup"><span data-stu-id="20bcb-140">[Property Procedures](./property-procedures.md) return and assign values of properties on objects or modules.</span></span>  
  
- <span data-ttu-id="20bcb-141">如果一个或两个操作数是新定义的类或结构，则[运算符过程](./operator-procedures.md)定义标准运算符的行为。</span><span class="sxs-lookup"><span data-stu-id="20bcb-141">[Operator Procedures](./operator-procedures.md) define the behavior of a standard operator when one or both of the operands is a newly-defined class or structure.</span></span>  
  
- <span data-ttu-id="20bcb-142">[Visual Basic 中的泛型过程](../data-types/generic-procedures.md)除定义其正常参数外，还定义一个或多个类型参数，因此调用代码可在每次调用时传递特定的数据类型。</span><span class="sxs-lookup"><span data-stu-id="20bcb-142">[Generic Procedures in Visual Basic](../data-types/generic-procedures.md) define one or more *type parameters* in addition to their normal parameters, so the calling code can pass specific data types each time it makes a call.</span></span>  
  
## <a name="procedures-and-structured-code"></a><span data-ttu-id="20bcb-143">过程和结构化代码</span><span class="sxs-lookup"><span data-stu-id="20bcb-143">Procedures and Structured Code</span></span>  

 <span data-ttu-id="20bcb-144">应用程序中的每行可执行代码都必须位于某个过程内，例如 `Main`、`calculate` 或 `Button1_Click`。</span><span class="sxs-lookup"><span data-stu-id="20bcb-144">Every line of executable code in your application must be inside some procedure, such as `Main`, `calculate`, or `Button1_Click`.</span></span> <span data-ttu-id="20bcb-145">如果将较大的过程细分为较小的过程，则应用程序将更易读取。</span><span class="sxs-lookup"><span data-stu-id="20bcb-145">If you subdivide large procedures into smaller ones, your application is more readable.</span></span>  
  
 <span data-ttu-id="20bcb-146">过程对于执行重复或共享任务（如常用的计算、文本和控制处理以及数据库操作）非常有用。</span><span class="sxs-lookup"><span data-stu-id="20bcb-146">Procedures are useful for performing repeated or shared tasks, such as frequently used calculations, text and control manipulation, and database operations.</span></span> <span data-ttu-id="20bcb-147">可从代码中的众多不同位置调用过程，因此可将过程用作应用程序的构建基块。</span><span class="sxs-lookup"><span data-stu-id="20bcb-147">You can call a procedure from many different places in your code, so you can use procedures as building blocks for your application.</span></span>  
  
 <span data-ttu-id="20bcb-148">使用过程来构建代码具有以下好处：</span><span class="sxs-lookup"><span data-stu-id="20bcb-148">Structuring your code with procedures gives you the following benefits:</span></span>  
  
- <span data-ttu-id="20bcb-149">过程允许将程序分解成离散的逻辑单元。</span><span class="sxs-lookup"><span data-stu-id="20bcb-149">Procedures allow you to break your programs into discrete logical units.</span></span> <span data-ttu-id="20bcb-150">调试独立的单元比在没有过程时调试整个程序更容易。</span><span class="sxs-lookup"><span data-stu-id="20bcb-150">You can debug separate units more easily than you can debug an entire program without procedures.</span></span>  
  
- <span data-ttu-id="20bcb-151">开发可供某一程序使用的过程后，也可在其他程序中使用它们，通常只需很少修改或无需修改。</span><span class="sxs-lookup"><span data-stu-id="20bcb-151">After you develop procedures for use in one program, you can use them in other programs, often with little or no modification.</span></span> <span data-ttu-id="20bcb-152">这有助于避免代码重复。</span><span class="sxs-lookup"><span data-stu-id="20bcb-152">This helps you avoid code duplication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20bcb-153">请参阅</span><span class="sxs-lookup"><span data-stu-id="20bcb-153">See also</span></span>

- [<span data-ttu-id="20bcb-154">如何：创建过程</span><span class="sxs-lookup"><span data-stu-id="20bcb-154">How to: Create a Procedure</span></span>](./how-to-create-a-procedure.md)
- [<span data-ttu-id="20bcb-155">Sub 过程</span><span class="sxs-lookup"><span data-stu-id="20bcb-155">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="20bcb-156">Function 过程</span><span class="sxs-lookup"><span data-stu-id="20bcb-156">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="20bcb-157">Property 过程</span><span class="sxs-lookup"><span data-stu-id="20bcb-157">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="20bcb-158">运算符过程</span><span class="sxs-lookup"><span data-stu-id="20bcb-158">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="20bcb-159">过程形参和实参</span><span class="sxs-lookup"><span data-stu-id="20bcb-159">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="20bcb-160">递归过程</span><span class="sxs-lookup"><span data-stu-id="20bcb-160">Recursive Procedures</span></span>](./recursive-procedures.md)
- [<span data-ttu-id="20bcb-161">过程重载</span><span class="sxs-lookup"><span data-stu-id="20bcb-161">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="20bcb-162">Generic Procedures in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="20bcb-162">Generic Procedures in Visual Basic</span></span>](../data-types/generic-procedures.md)
- [<span data-ttu-id="20bcb-163">对象和类</span><span class="sxs-lookup"><span data-stu-id="20bcb-163">Objects and Classes</span></span>](../objects-and-classes/index.md)
