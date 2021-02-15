---
description: '了解详细信息：如何：创建 Lambda 表达式 (Visual Basic) '
title: 如何：创建 lambda 表达式
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
ms.openlocfilehash: 386d40c1e2021c9b02b2f785300c4e978b4da87d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100472561"
---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a><span data-ttu-id="6ba30-103">如何：创建 Lambda 表达式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6ba30-103">How to: Create a Lambda Expression (Visual Basic)</span></span>

<span data-ttu-id="6ba30-104">*Lambda 表达式* 是没有名称的函数或子例程。</span><span class="sxs-lookup"><span data-stu-id="6ba30-104">A *lambda expression* is a function or subroutine that does not have a name.</span></span> <span data-ttu-id="6ba30-105">如果委托类型有效，可以使用 lambda 表达式。</span><span class="sxs-lookup"><span data-stu-id="6ba30-105">A lambda expression can be used wherever a delegate type is valid.</span></span>  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a><span data-ttu-id="6ba30-106">创建单行 lambda 表达式函数</span><span class="sxs-lookup"><span data-stu-id="6ba30-106">To create a single-line lambda expression function</span></span>  
  
1. <span data-ttu-id="6ba30-107">在可以使用委托类型的任何情况下，键入关键字 `Function` ，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="6ba30-107">In any situation where a delegate type could be used, type the keyword `Function`, as in the following example:</span></span>  
  
     <span data-ttu-id="6ba30-108">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="6ba30-108">`Dim add1 =`   `Function`</span></span>  
  
2. <span data-ttu-id="6ba30-109">在括号中，直接 `Function` 键入函数的参数。</span><span class="sxs-lookup"><span data-stu-id="6ba30-109">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="6ba30-110">请注意，不能在之后指定名称 `Function` 。</span><span class="sxs-lookup"><span data-stu-id="6ba30-110">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="6ba30-111">`Dim add1 = Function`   `(num As Integer)`</span><span class="sxs-lookup"><span data-stu-id="6ba30-111">`Dim add1 = Function`   `(num As Integer)`</span></span>  
  
3. <span data-ttu-id="6ba30-112">在参数列表的后面键入一个表达式作为函数的主体。</span><span class="sxs-lookup"><span data-stu-id="6ba30-112">Following the parameter list, type a single expression as the body of the function.</span></span> <span data-ttu-id="6ba30-113">表达式计算结果的值是函数返回的值。</span><span class="sxs-lookup"><span data-stu-id="6ba30-113">The value that the expression evaluates to is the value returned by the function.</span></span> <span data-ttu-id="6ba30-114">不要使用 `As` 子句来指定返回类型。</span><span class="sxs-lookup"><span data-stu-id="6ba30-114">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
     <span data-ttu-id="6ba30-115">通过传入整数参数来调用 lambda 表达式。</span><span class="sxs-lookup"><span data-stu-id="6ba30-115">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
4. <span data-ttu-id="6ba30-116">或者，通过以下示例实现相同的结果：</span><span class="sxs-lookup"><span data-stu-id="6ba30-116">Alternatively, the same result is accomplished by the following example:</span></span>  
  
     [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a><span data-ttu-id="6ba30-117">创建单行 lambda 表达式子例程</span><span class="sxs-lookup"><span data-stu-id="6ba30-117">To create a single-line lambda expression subroutine</span></span>  
  
1. <span data-ttu-id="6ba30-118">在可以使用委托类型的任何情况下，键入关键字 `Sub` ，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="6ba30-118">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="6ba30-119">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="6ba30-119">`Dim add1 =`   `Sub`</span></span>  
  
2. <span data-ttu-id="6ba30-120">在括号中，直接 `Sub` 键入子例程的参数。</span><span class="sxs-lookup"><span data-stu-id="6ba30-120">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="6ba30-121">请注意，不能在之后指定名称 `Sub` 。</span><span class="sxs-lookup"><span data-stu-id="6ba30-121">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="6ba30-122">`Dim add1 = Sub`   `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="6ba30-122">`Dim add1 = Sub`   `(msg As String)`</span></span>  
  
3. <span data-ttu-id="6ba30-123">在参数列表的后面键入单个语句作为子例程的主体。</span><span class="sxs-lookup"><span data-stu-id="6ba30-123">Following the parameter list, type a single statement as the body of the subroutine.</span></span>  
  
     [!code-vb[VbVbalrLambdas#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#17)]  
  
     <span data-ttu-id="6ba30-124">通过传入字符串参数来调用 lambda 表达式。</span><span class="sxs-lookup"><span data-stu-id="6ba30-124">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#18)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a><span data-ttu-id="6ba30-125">创建多行 lambda 表达式函数</span><span class="sxs-lookup"><span data-stu-id="6ba30-125">To create a multiline lambda expression function</span></span>  
  
1. <span data-ttu-id="6ba30-126">在可以使用委托类型的任何情况下，键入关键字 `Function` ，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="6ba30-126">In any situation where a delegate type could be used, type the keyword `Function`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="6ba30-127">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="6ba30-127">`Dim add1 =`   `Function`</span></span>  
  
2. <span data-ttu-id="6ba30-128">在括号中，直接 `Function` 键入函数的参数。</span><span class="sxs-lookup"><span data-stu-id="6ba30-128">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="6ba30-129">请注意，不能在之后指定名称 `Function` 。</span><span class="sxs-lookup"><span data-stu-id="6ba30-129">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="6ba30-130">`Dim add1 = Function`   `(index As Integer)`</span><span class="sxs-lookup"><span data-stu-id="6ba30-130">`Dim add1 = Function`   `(index As Integer)`</span></span>  
  
3. <span data-ttu-id="6ba30-131">按 Enter。</span><span class="sxs-lookup"><span data-stu-id="6ba30-131">Press ENTER.</span></span> <span data-ttu-id="6ba30-132">`End Function`语句会自动添加。</span><span class="sxs-lookup"><span data-stu-id="6ba30-132">The `End Function` statement is automatically added.</span></span>  
  
4. <span data-ttu-id="6ba30-133">在函数的主体中，添加以下代码以创建表达式并返回值。</span><span class="sxs-lookup"><span data-stu-id="6ba30-133">Within the body of the function, add the following code to create an expression and return the value.</span></span> <span data-ttu-id="6ba30-134">不要使用 `As` 子句来指定返回类型。</span><span class="sxs-lookup"><span data-stu-id="6ba30-134">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#19)]  
  
     <span data-ttu-id="6ba30-135">通过传入整数参数来调用 lambda 表达式。</span><span class="sxs-lookup"><span data-stu-id="6ba30-135">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#20)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a><span data-ttu-id="6ba30-136">创建多行 lambda 表达式子例程</span><span class="sxs-lookup"><span data-stu-id="6ba30-136">To create a multiline lambda expression subroutine</span></span>  
  
1. <span data-ttu-id="6ba30-137">在可以使用委托类型的任何情况下，键入关键字 `Sub` ，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="6ba30-137">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example:</span></span>  
  
     <span data-ttu-id="6ba30-138">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="6ba30-138">`Dim add1 =`   `Sub`</span></span>  
  
2. <span data-ttu-id="6ba30-139">在括号中，直接 `Sub` 键入子例程的参数。</span><span class="sxs-lookup"><span data-stu-id="6ba30-139">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="6ba30-140">请注意，不能在之后指定名称 `Sub` 。</span><span class="sxs-lookup"><span data-stu-id="6ba30-140">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="6ba30-141">`Dim add1 = Sub`  `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="6ba30-141">`Dim add1 = Sub`  `(msg As String)`</span></span>  
  
3. <span data-ttu-id="6ba30-142">按 Enter。</span><span class="sxs-lookup"><span data-stu-id="6ba30-142">Press ENTER.</span></span> <span data-ttu-id="6ba30-143">`End Sub`语句会自动添加。</span><span class="sxs-lookup"><span data-stu-id="6ba30-143">The `End Sub` statement is automatically added.</span></span>  
  
4. <span data-ttu-id="6ba30-144">在函数的主体中，添加以下代码，以便在调用子例程时执行。</span><span class="sxs-lookup"><span data-stu-id="6ba30-144">Within the body of the function, add the following code to execute when the subroutine is invoked.</span></span>  
  
     [!code-vb[VbVbalrLambdas#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#21)]  
  
     <span data-ttu-id="6ba30-145">通过传入字符串参数来调用 lambda 表达式。</span><span class="sxs-lookup"><span data-stu-id="6ba30-145">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#22)]  
  
## <a name="example"></a><span data-ttu-id="6ba30-146">示例</span><span class="sxs-lookup"><span data-stu-id="6ba30-146">Example</span></span>  

 <span data-ttu-id="6ba30-147">Lambda 表达式的一个常见用途是定义一个函数，该函数可作为参数（其类型为）作为参数传入 `Delegate` 。</span><span class="sxs-lookup"><span data-stu-id="6ba30-147">A common use of lambda expressions is to define a function that can be passed in as the argument for a parameter whose type is `Delegate`.</span></span> <span data-ttu-id="6ba30-148">在下面的示例中， <xref:System.Diagnostics.Process.GetProcesses%2A> 方法返回在本地计算机上运行的进程的数组。</span><span class="sxs-lookup"><span data-stu-id="6ba30-148">In the following example, the <xref:System.Diagnostics.Process.GetProcesses%2A> method returns an array of the processes running on the local computer.</span></span> <span data-ttu-id="6ba30-149"><xref:System.Linq.Enumerable.Where%2A>类中的方法 <xref:System.Linq.Enumerable> 要求 `Boolean` 委托作为其参数。</span><span class="sxs-lookup"><span data-stu-id="6ba30-149">The <xref:System.Linq.Enumerable.Where%2A> method from the <xref:System.Linq.Enumerable> class requires a `Boolean` delegate as its argument.</span></span> <span data-ttu-id="6ba30-150">示例中的 lambda 表达式用于此目的。</span><span class="sxs-lookup"><span data-stu-id="6ba30-150">The lambda expression in the example is used for that purpose.</span></span> <span data-ttu-id="6ba30-151">它 `True` 为每个只有一个线程的进程返回，在中选择这些进程 `filteredList` 。</span><span class="sxs-lookup"><span data-stu-id="6ba30-151">It returns `True` for each process that has only one thread, and those are selected in `filteredList`.</span></span>  
  
 [!code-vb[VbVbalrLambdas#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class4.vb#10)]  
  
 <span data-ttu-id="6ba30-152">前面的示例等效于以下代码，该代码以 Language-Integrated 查询编写 (LINQ) 语法：</span><span class="sxs-lookup"><span data-stu-id="6ba30-152">The previous example is equivalent to the following code, which is written in Language-Integrated Query (LINQ) syntax:</span></span>  
  
 [!code-vb[VbVbalrLambdas#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class5.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="6ba30-153">请参阅</span><span class="sxs-lookup"><span data-stu-id="6ba30-153">See also</span></span>

- <xref:System.Linq.Enumerable>
- [<span data-ttu-id="6ba30-154">Lambda 表达式</span><span class="sxs-lookup"><span data-stu-id="6ba30-154">Lambda Expressions</span></span>](./lambda-expressions.md)
- [<span data-ttu-id="6ba30-155">Function 语句</span><span class="sxs-lookup"><span data-stu-id="6ba30-155">Function Statement</span></span>](../../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="6ba30-156">Sub 语句</span><span class="sxs-lookup"><span data-stu-id="6ba30-156">Sub Statement</span></span>](../../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="6ba30-157">委托</span><span class="sxs-lookup"><span data-stu-id="6ba30-157">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="6ba30-158">如何：在 Visual Basic 中将过程传递给另一过程</span><span class="sxs-lookup"><span data-stu-id="6ba30-158">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="6ba30-159">Delegate 语句</span><span class="sxs-lookup"><span data-stu-id="6ba30-159">Delegate Statement</span></span>](../../../language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="6ba30-160">Visual Basic 中的 LINQ 简介</span><span class="sxs-lookup"><span data-stu-id="6ba30-160">Introduction to LINQ in Visual Basic</span></span>](../linq/introduction-to-linq.md)
