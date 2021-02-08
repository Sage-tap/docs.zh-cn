---
description: '了解详细信息： Do .。。Loop 语句 (Visual Basic) '
title: Do...Loop 语句
ms.date: 07/20/2015
f1_keywords:
- vb.Do
- vb.Loop
- vb.Until
helpviewer_keywords:
- conditional statements [Visual Basic], Do�Loop
- while statement [Visual Basic], Do...Loop
- execution [Visual Basic], conditional
- Do loops
- Until keyword [Visual Basic], Do...Loop statement
- Do...Loop statement
- instructions, repeating
- Do statement [Visual Basic]
- Exit statement [Visual Basic], in Do...Loop statements
- loop structures [Visual Basic], Do�Loop statements
- do-while statements [Visual Basic]
- loops, exiting
- Loop keyword [Visual Basic], Do...Loop statement
ms.assetid: 892f9096-b3e2-4aee-834d-83bc4e2c379d
ms.openlocfilehash: d170074c44d1692517f6b51abd4a6b3d005941c0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795178"
---
# <a name="doloop-statement-visual-basic"></a><span data-ttu-id="08eed-103">Do...Loop 语句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="08eed-103">Do...Loop Statement (Visual Basic)</span></span>

<span data-ttu-id="08eed-104">当 `Boolean` 条件为 `True` 或在条件变为之前，重复语句块 `True` 。</span><span class="sxs-lookup"><span data-stu-id="08eed-104">Repeats a block of statements while a `Boolean` condition is `True` or until the condition becomes `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08eed-105">语法</span><span class="sxs-lookup"><span data-stu-id="08eed-105">Syntax</span></span>  
  
```vb  
Do { While | Until } condition  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop  
' -or-  
Do  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop { While | Until } condition  
```  
  
## <a name="parts"></a><span data-ttu-id="08eed-106">组成部分</span><span class="sxs-lookup"><span data-stu-id="08eed-106">Parts</span></span>  
  
|<span data-ttu-id="08eed-107">术语</span><span class="sxs-lookup"><span data-stu-id="08eed-107">Term</span></span>|<span data-ttu-id="08eed-108">定义</span><span class="sxs-lookup"><span data-stu-id="08eed-108">Definition</span></span>|  
|---|---|  
|`Do`|<span data-ttu-id="08eed-109">必需。</span><span class="sxs-lookup"><span data-stu-id="08eed-109">Required.</span></span> <span data-ttu-id="08eed-110">开始循环的定义 `Do` 。</span><span class="sxs-lookup"><span data-stu-id="08eed-110">Starts the definition of the `Do` loop.</span></span>|  
|`While`|<span data-ttu-id="08eed-111">必选项（除非使用了 `Until`）。</span><span class="sxs-lookup"><span data-stu-id="08eed-111">Required unless `Until` is used.</span></span> <span data-ttu-id="08eed-112">重复循环，直到 `condition` 为为止 `False` 。</span><span class="sxs-lookup"><span data-stu-id="08eed-112">Repeat the loop until `condition` is `False`.</span></span>|  
|`Until`|<span data-ttu-id="08eed-113">必选项（除非使用了 `While`）。</span><span class="sxs-lookup"><span data-stu-id="08eed-113">Required unless `While` is used.</span></span> <span data-ttu-id="08eed-114">重复循环，直到 `condition` 为为止 `True` 。</span><span class="sxs-lookup"><span data-stu-id="08eed-114">Repeat the loop until `condition` is `True`.</span></span>|  
|`condition`|<span data-ttu-id="08eed-115">可选。</span><span class="sxs-lookup"><span data-stu-id="08eed-115">Optional.</span></span> <span data-ttu-id="08eed-116">`Boolean` 表达式。</span><span class="sxs-lookup"><span data-stu-id="08eed-116">`Boolean` expression.</span></span> <span data-ttu-id="08eed-117">如果 `condition` 为 `Nothing` ，则 Visual Basic 将其视为 `False` 。</span><span class="sxs-lookup"><span data-stu-id="08eed-117">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="08eed-118">可选。</span><span class="sxs-lookup"><span data-stu-id="08eed-118">Optional.</span></span> <span data-ttu-id="08eed-119">一个或多个重复的语句，或在之前重复 `condition` `True` 。</span><span class="sxs-lookup"><span data-stu-id="08eed-119">One or more statements that are repeated while, or until, `condition` is `True`.</span></span>|  
|`Continue Do`|<span data-ttu-id="08eed-120">可选。</span><span class="sxs-lookup"><span data-stu-id="08eed-120">Optional.</span></span> <span data-ttu-id="08eed-121">将控制转移到循环的下一次迭代 `Do` 。</span><span class="sxs-lookup"><span data-stu-id="08eed-121">Transfers control to the next iteration of the `Do` loop.</span></span>|  
|`Exit Do`|<span data-ttu-id="08eed-122">可选。</span><span class="sxs-lookup"><span data-stu-id="08eed-122">Optional.</span></span> <span data-ttu-id="08eed-123">将控制转移到 `Do` 循环外。</span><span class="sxs-lookup"><span data-stu-id="08eed-123">Transfers control out of the `Do` loop.</span></span>|  
|`Loop`|<span data-ttu-id="08eed-124">必需。</span><span class="sxs-lookup"><span data-stu-id="08eed-124">Required.</span></span> <span data-ttu-id="08eed-125">终止循环的定义 `Do` 。</span><span class="sxs-lookup"><span data-stu-id="08eed-125">Terminates the definition of the `Do` loop.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08eed-126">备注</span><span class="sxs-lookup"><span data-stu-id="08eed-126">Remarks</span></span>  

 <span data-ttu-id="08eed-127">`Do...Loop`如果希望在满足条件之前重复一组语句，请使用结构。</span><span class="sxs-lookup"><span data-stu-id="08eed-127">Use a `Do...Loop` structure when you want to repeat a set of statements an indefinite number of times, until a condition is satisfied.</span></span> <span data-ttu-id="08eed-128">如果要将语句重复一组次数 [，则下一条语句](for-next-statement.md) 通常是更好的选择。</span><span class="sxs-lookup"><span data-stu-id="08eed-128">If you want to repeat the statements a set number of times, the [For...Next Statement](for-next-statement.md) is usually a better choice.</span></span>  
  
 <span data-ttu-id="08eed-129">您可以使用 `While` 或 `Until` 来指定 `condition` ，但不能同时使用两者。</span><span class="sxs-lookup"><span data-stu-id="08eed-129">You can use either `While` or `Until` to specify `condition`, but not both.</span></span>  
  
 <span data-ttu-id="08eed-130">只能 `condition` 在循环的开头或结尾测试一次。</span><span class="sxs-lookup"><span data-stu-id="08eed-130">You can test `condition` only one time, at either the start or the end of the loop.</span></span> <span data-ttu-id="08eed-131">如果在 `condition` 语句) 中测试循环 (`Do` ，则循环可能不会运行一次。</span><span class="sxs-lookup"><span data-stu-id="08eed-131">If you test `condition` at the start of the loop (in the `Do` statement), the loop might not run even one time.</span></span> <span data-ttu-id="08eed-132">如果在语句) 中测试循环 (`Loop` ，则循环始终运行至少一次。</span><span class="sxs-lookup"><span data-stu-id="08eed-132">If you test at the end of the loop (in the `Loop` statement), the loop always runs at least one time.</span></span>  
  
 <span data-ttu-id="08eed-133">这种情况通常是由两个值比较导致的，但它可以是计算结果为 [布尔数据类型](../data-types/boolean-data-type.md) 值 (或) 的任何表达式 `True` `False` 。</span><span class="sxs-lookup"><span data-stu-id="08eed-133">The condition usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="08eed-134">这包括已转换为的其他数据类型（如数值类型）的值 `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="08eed-134">This includes values of other data types, such as numeric types, that have been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="08eed-135">可以 `Do` 通过在另一个循环中放置循环来嵌套循环。</span><span class="sxs-lookup"><span data-stu-id="08eed-135">You can nest `Do` loops by putting one loop within another.</span></span> <span data-ttu-id="08eed-136">您还可以在彼此之间嵌套不同种类的控制结构。</span><span class="sxs-lookup"><span data-stu-id="08eed-136">You can also nest different kinds of control structures within each other.</span></span> <span data-ttu-id="08eed-137">有关详细信息，请参阅 [嵌套控制结构](../../programming-guide/language-features/control-flow/nested-control-structures.md)。</span><span class="sxs-lookup"><span data-stu-id="08eed-137">For more information, see [Nested Control Structures](../../programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="08eed-138">此 `Do...Loop` 结构提供的灵活性比 [.。。End While 语句](while-end-while-statement.md) ，因为它可用于决定是在 `condition` 停止时 `True` 还是在第一次变为时结束循环 `True` 。</span><span class="sxs-lookup"><span data-stu-id="08eed-138">The `Do...Loop` structure gives you more flexibility than the [While...End While Statement](while-end-while-statement.md) because it enables you to decide whether to end the loop when `condition` stops being `True` or when it first becomes `True`.</span></span> <span data-ttu-id="08eed-139">它还使你能够 `condition` 在循环的开头或结尾进行测试。</span><span class="sxs-lookup"><span data-stu-id="08eed-139">It also enables you to test `condition` at either the start or the end of the loop.</span></span>  
  
## <a name="exit-do"></a><span data-ttu-id="08eed-140">退出 Do</span><span class="sxs-lookup"><span data-stu-id="08eed-140">Exit Do</span></span>  

 <span data-ttu-id="08eed-141">[Exit Do](exit-statement.md)语句可以提供退出的替代方法 `Do…Loop` 。</span><span class="sxs-lookup"><span data-stu-id="08eed-141">The [Exit Do](exit-statement.md) statement can provide an alternative way to exit a `Do…Loop`.</span></span> <span data-ttu-id="08eed-142">`Exit Do` 将控制立即传输到语句后面的语句 `Loop` 。</span><span class="sxs-lookup"><span data-stu-id="08eed-142">`Exit Do` transfers control immediately to the statement that follows the `Loop` statement.</span></span>  
  
 <span data-ttu-id="08eed-143">`Exit Do` 通常在计算某些条件后（例如在结构中）使用 `If...Then...Else` 。</span><span class="sxs-lookup"><span data-stu-id="08eed-143">`Exit Do` is often used after some condition is evaluated, for example in an `If...Then...Else` structure.</span></span> <span data-ttu-id="08eed-144">如果检测到可能导致不必要或无法继续迭代的条件（如错误值或终止请求），则可能需要退出循环。</span><span class="sxs-lookup"><span data-stu-id="08eed-144">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="08eed-145">的一种用途 `Exit Do` 是测试可能导致 *无限循环* 的情况，这是一个可运行很大甚至无限次数的循环。</span><span class="sxs-lookup"><span data-stu-id="08eed-145">One use of `Exit Do` is to test for a condition that could cause an *endless loop*, which is a loop that could run a large or even infinite number of times.</span></span> <span data-ttu-id="08eed-146">您可以使用 `Exit Do` 来转义循环。</span><span class="sxs-lookup"><span data-stu-id="08eed-146">You can use `Exit Do` to escape the loop.</span></span>  
  
 <span data-ttu-id="08eed-147">可以在中的任意位置包含任意数量的 `Exit Do` 语句 `Do…Loop` 。</span><span class="sxs-lookup"><span data-stu-id="08eed-147">You can include any number of `Exit Do` statements anywhere in a `Do…Loop`.</span></span>  
  
 <span data-ttu-id="08eed-148">在嵌套循环内使用时 `Do` ， `Exit Do` 将控制转移出最内层循环，并将其转移到下一个更高的嵌套级别。</span><span class="sxs-lookup"><span data-stu-id="08eed-148">When used within nested `Do` loops, `Exit Do` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08eed-149">示例</span><span class="sxs-lookup"><span data-stu-id="08eed-149">Example</span></span>  

 <span data-ttu-id="08eed-150">在下面的示例中，循环中的语句将继续运行，直到 `index` 变量大于10。</span><span class="sxs-lookup"><span data-stu-id="08eed-150">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span> <span data-ttu-id="08eed-151">`Until`子句位于循环的结尾。</span><span class="sxs-lookup"><span data-stu-id="08eed-151">The `Until` clause is at the end of the loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#131](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#131)]  
  
## <a name="example"></a><span data-ttu-id="08eed-152">示例</span><span class="sxs-lookup"><span data-stu-id="08eed-152">Example</span></span>  

 <span data-ttu-id="08eed-153">下面的示例使用 `While` 子句而不是 `Until` 子句，并 `condition` 在循环的开头而不是在结束时进行测试。</span><span class="sxs-lookup"><span data-stu-id="08eed-153">The following example uses a `While` clause instead of an `Until` clause, and `condition` is tested at the start of the loop instead of at the end.</span></span>  
  
 [!code-vb[VbVbalrStatements#132](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#132)]  
  
## <a name="example"></a><span data-ttu-id="08eed-154">示例</span><span class="sxs-lookup"><span data-stu-id="08eed-154">Example</span></span>  

 <span data-ttu-id="08eed-155">在下面的示例中， `condition` 当 `index` 变量大于100时停止循环。</span><span class="sxs-lookup"><span data-stu-id="08eed-155">In the following example, `condition` stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="08eed-156">`If`但是，循环中的语句会导致语句在 `Exit Do` 索引变量大于10时停止循环。</span><span class="sxs-lookup"><span data-stu-id="08eed-156">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a><span data-ttu-id="08eed-157">示例</span><span class="sxs-lookup"><span data-stu-id="08eed-157">Example</span></span>  

 <span data-ttu-id="08eed-158">下面的示例读取文本文件中的所有行。</span><span class="sxs-lookup"><span data-stu-id="08eed-158">The following example reads all lines in a text file.</span></span> <span data-ttu-id="08eed-159"><xref:System.IO.File.OpenText%2A>方法打开文件并返回 <xref:System.IO.StreamReader> 读取字符的。</span><span class="sxs-lookup"><span data-stu-id="08eed-159">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="08eed-160">在 `Do...Loop` 条件中，的 <xref:System.IO.StreamReader.Peek%2A> 方法 `StreamReader` 确定是否有任何其他字符。</span><span class="sxs-lookup"><span data-stu-id="08eed-160">In the `Do...Loop` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether there are any additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#134](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#134)]  
  
## <a name="see-also"></a><span data-ttu-id="08eed-161">请参阅</span><span class="sxs-lookup"><span data-stu-id="08eed-161">See also</span></span>

- [<span data-ttu-id="08eed-162">循环结构</span><span class="sxs-lookup"><span data-stu-id="08eed-162">Loop Structures</span></span>](../../programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="08eed-163">For...Next 语句</span><span class="sxs-lookup"><span data-stu-id="08eed-163">For...Next Statement</span></span>](for-next-statement.md)
- [<span data-ttu-id="08eed-164">布尔数据类型</span><span class="sxs-lookup"><span data-stu-id="08eed-164">Boolean Data Type</span></span>](../data-types/boolean-data-type.md)
- [<span data-ttu-id="08eed-165">嵌套的控件结构</span><span class="sxs-lookup"><span data-stu-id="08eed-165">Nested Control Structures</span></span>](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="08eed-166">Exit 语句</span><span class="sxs-lookup"><span data-stu-id="08eed-166">Exit Statement</span></span>](exit-statement.md)
- [<span data-ttu-id="08eed-167">While...End While 语句</span><span class="sxs-lookup"><span data-stu-id="08eed-167">While...End While Statement</span></span>](while-end-while-statement.md)
