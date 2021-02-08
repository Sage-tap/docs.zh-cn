---
description: '了解详细信息： Yield 语句 (Visual Basic) '
title: Yield 语句
ms.date: 07/20/2015
f1_keywords:
- vb.Yield
helpviewer_keywords:
- iterators, Yield statement [Visual Basic]
- iterators [Visual Basic]
- Yield statement [Visual Basic]
ms.assetid: f33126c5-d7c4-43e2-8e36-4ae3f0703d97
ms.openlocfilehash: cd07c271722a715beeddfddf660cec3e05127db8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787547"
---
# <a name="yield-statement-visual-basic"></a><span data-ttu-id="36060-103">Yield 语句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36060-103">Yield Statement (Visual Basic)</span></span>

<span data-ttu-id="36060-104">将集合的下一个元素发送到 `For Each...Next` 语句。</span><span class="sxs-lookup"><span data-stu-id="36060-104">Sends the next element of a collection to a `For Each...Next` statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36060-105">语法</span><span class="sxs-lookup"><span data-stu-id="36060-105">Syntax</span></span>  
  
```vb  
Yield expression  
```  
  
## <a name="parameters"></a><span data-ttu-id="36060-106">参数</span><span class="sxs-lookup"><span data-stu-id="36060-106">Parameters</span></span>  
  
|<span data-ttu-id="36060-107">术语</span><span class="sxs-lookup"><span data-stu-id="36060-107">Term</span></span>|<span data-ttu-id="36060-108">定义</span><span class="sxs-lookup"><span data-stu-id="36060-108">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="36060-109">必需。</span><span class="sxs-lookup"><span data-stu-id="36060-109">Required.</span></span> <span data-ttu-id="36060-110">可隐式转换为迭代器函数或包含该语句的访问器的类型的表达式 `Get` `Yield` 。</span><span class="sxs-lookup"><span data-stu-id="36060-110">An expression that is implicitly convertible to the type of the iterator function or `Get` accessor that contains the `Yield` statement.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36060-111">备注</span><span class="sxs-lookup"><span data-stu-id="36060-111">Remarks</span></span>  

 <span data-ttu-id="36060-112">`Yield`语句一次返回集合中的一个元素。</span><span class="sxs-lookup"><span data-stu-id="36060-112">The `Yield` statement returns one element of a collection at a time.</span></span> <span data-ttu-id="36060-113">`Yield`语句包含在迭代器函数或 `Get` 访问器中，后者对集合执行自定义迭代。</span><span class="sxs-lookup"><span data-stu-id="36060-113">The `Yield` statement is included in an iterator function or `Get` accessor, which perform custom iterations over a collection.</span></span>  
  
 <span data-ttu-id="36060-114">使用 For Each ... 的方法使用迭代器函数 [Next 语句](for-each-next-statement.md) 或 LINQ 查询。</span><span class="sxs-lookup"><span data-stu-id="36060-114">You consume an iterator function by using a [For Each...Next Statement](for-each-next-statement.md) or a LINQ query.</span></span> <span data-ttu-id="36060-115">循环的每次迭代都会 `For Each` 调用迭代器函数。</span><span class="sxs-lookup"><span data-stu-id="36060-115">Each iteration of the `For Each` loop calls the iterator function.</span></span> <span data-ttu-id="36060-116">当 `Yield` 在迭代器函数中到达语句时， `expression` 将返回，并且保留代码中的当前位置。</span><span class="sxs-lookup"><span data-stu-id="36060-116">When a `Yield` statement is reached in the iterator function, `expression` is returned, and the current location in code is retained.</span></span> <span data-ttu-id="36060-117">下次调用迭代器函数时，将从该位置重新开始执行。</span><span class="sxs-lookup"><span data-stu-id="36060-117">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="36060-118">隐式转换必须从语句中的类型 `expression` `Yield` 到迭代器的返回类型存在。</span><span class="sxs-lookup"><span data-stu-id="36060-118">An implicit conversion must exist from the type of `expression` in the `Yield` statement to the return type of the iterator.</span></span>  
  
 <span data-ttu-id="36060-119">您可以使用 `Exit Function` 或 `Return` 语句结束迭代。</span><span class="sxs-lookup"><span data-stu-id="36060-119">You can use an `Exit Function` or `Return` statement to end the iteration.</span></span>  
  
 <span data-ttu-id="36060-120">"Yield" 不是保留字，只在 `Iterator` 函数或访问器中使用时具有特殊意义 `Get` 。</span><span class="sxs-lookup"><span data-stu-id="36060-120">"Yield" is not a reserved word and has special meaning only when it is used in an `Iterator` function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="36060-121">有关迭代器函数和访问器的详细信息 `Get` ，请参阅 [迭代](../../programming-guide/concepts/iterators.md)器。</span><span class="sxs-lookup"><span data-stu-id="36060-121">For more information about iterator functions and `Get` accessors, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="iterator-functions-and-get-accessors"></a><span data-ttu-id="36060-122">迭代器函数和 Get 访问器</span><span class="sxs-lookup"><span data-stu-id="36060-122">Iterator Functions and Get Accessors</span></span>  

 <span data-ttu-id="36060-123">迭代器函数或 `Get` 访问器的声明必须满足以下要求：</span><span class="sxs-lookup"><span data-stu-id="36060-123">The declaration of an iterator function or `Get` accessor must meet the following requirements:</span></span>  
  
- <span data-ttu-id="36060-124">它必须包含 [迭代器](../modifiers/iterator.md) 修饰符。</span><span class="sxs-lookup"><span data-stu-id="36060-124">It must include an [Iterator](../modifiers/iterator.md) modifier.</span></span>  
  
- <span data-ttu-id="36060-125">返回类型必须为 <xref:System.Collections.IEnumerable>、<xref:System.Collections.Generic.IEnumerable%601>、<xref:System.Collections.IEnumerator> 或 <xref:System.Collections.Generic.IEnumerator%601>。</span><span class="sxs-lookup"><span data-stu-id="36060-125">The return type must be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
- <span data-ttu-id="36060-126">它不能具有任何 `ByRef` 参数。</span><span class="sxs-lookup"><span data-stu-id="36060-126">It cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="36060-127">迭代器函数不能出现在事件、实例构造函数、静态构造函数或静态析构函数中。</span><span class="sxs-lookup"><span data-stu-id="36060-127">An iterator function cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="36060-128">迭代器函数可以是匿名函数。</span><span class="sxs-lookup"><span data-stu-id="36060-128">An iterator function can be an anonymous function.</span></span> <span data-ttu-id="36060-129">有关更多信息，请参见 [迭代器](../../programming-guide/concepts/iterators.md)。</span><span class="sxs-lookup"><span data-stu-id="36060-129">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="36060-130">异常处理</span><span class="sxs-lookup"><span data-stu-id="36060-130">Exception Handling</span></span>  

 <span data-ttu-id="36060-131">`Yield`语句可以在 `Try` [Try ... 的块内Catch .。。Finally 语句](try-catch-finally-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="36060-131">A `Yield` statement can be inside a `Try` block of a [Try...Catch...Finally Statement](try-catch-finally-statement.md).</span></span> <span data-ttu-id="36060-132">`Try`带有语句的块 `Yield` 可以有 `Catch` 块，并且可以有 `Finally` 块。</span><span class="sxs-lookup"><span data-stu-id="36060-132">A `Try` block that has a `Yield` statement can have `Catch` blocks, and can have a `Finally` block.</span></span>  
  
 <span data-ttu-id="36060-133">`Yield`语句不能位于 `Catch` 块或 `Finally` 块中。</span><span class="sxs-lookup"><span data-stu-id="36060-133">A `Yield` statement cannot be inside a `Catch` block or a `Finally` block.</span></span>  
  
 <span data-ttu-id="36060-134">如果在 `For Each` 迭代器函数外 (主体) 引发异常，则 `Catch` 不会执行迭代器函数中的块，但 `Finally` 会执行迭代器函数中的块。</span><span class="sxs-lookup"><span data-stu-id="36060-134">If the `For Each` body (outside of the iterator function) throws an exception, a `Catch` block in the iterator function is not executed, but a `Finally` block in the iterator function is executed.</span></span> <span data-ttu-id="36060-135">`Catch`Iterator 函数内的块仅捕获 iterator 函数内发生的异常。</span><span class="sxs-lookup"><span data-stu-id="36060-135">A `Catch` block inside an iterator function catches only exceptions that occur inside the iterator function.</span></span>  
  
## <a name="technical-implementation"></a><span data-ttu-id="36060-136">技术实现</span><span class="sxs-lookup"><span data-stu-id="36060-136">Technical Implementation</span></span>  

 <span data-ttu-id="36060-137">下面的代码 `IEnumerable (Of String)` 从迭代器函数返回，然后循环访问的元素 `IEnumerable (Of String)` 。</span><span class="sxs-lookup"><span data-stu-id="36060-137">The following code returns an `IEnumerable (Of String)` from an iterator function and then iterates through the elements of the `IEnumerable (Of String)`.</span></span>  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 <span data-ttu-id="36060-138">对的调用 `MyIteratorFunction` 不会执行函数的主体。</span><span class="sxs-lookup"><span data-stu-id="36060-138">The call to `MyIteratorFunction` doesn't execute the body of the function.</span></span> <span data-ttu-id="36060-139">相反，该调用会将 `IEnumerable(Of String)` 返回到 `elements` 变量中。</span><span class="sxs-lookup"><span data-stu-id="36060-139">Instead the call returns an `IEnumerable(Of String)` into the `elements` variable.</span></span>  
  
 <span data-ttu-id="36060-140">在 `For Each` 循环迭代时，将为 <xref:System.Collections.IEnumerator.MoveNext%2A> 调用 `elements` 方法。</span><span class="sxs-lookup"><span data-stu-id="36060-140">On an iteration of the `For Each` loop, the <xref:System.Collections.IEnumerator.MoveNext%2A> method is called for `elements`.</span></span> <span data-ttu-id="36060-141">此调用将执行 `MyIteratorFunction` 的主体，直至到达下一个 `Yield` 语句。</span><span class="sxs-lookup"><span data-stu-id="36060-141">This call executes the body of `MyIteratorFunction` until the next `Yield` statement is reached.</span></span> <span data-ttu-id="36060-142">`Yield`语句返回的表达式不仅确定了循环体的使用的变量值 `element` ，还确定了元素的 <xref:System.Collections.Generic.IEnumerator%601.Current%2A> 属性，这是 `IEnumerable (Of String)` 。</span><span class="sxs-lookup"><span data-stu-id="36060-142">The `Yield` statement returns an expression that determines not only the value of the `element` variable for consumption by the loop body but also the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property of elements, which is an `IEnumerable (Of String)`.</span></span>  
  
 <span data-ttu-id="36060-143">在 `For Each` 循环的每个后续迭代中，迭代器主体的执行将从它暂停的位置继续，直至到达 `Yield` 语句后才会停止。</span><span class="sxs-lookup"><span data-stu-id="36060-143">On each subsequent iteration of the `For Each` loop, the execution of the iterator body continues from where it left off, again stopping when it reaches a `Yield` statement.</span></span> <span data-ttu-id="36060-144">`For Each`当达到 iterator 函数或或语句的末尾时，循环 `Return` `Exit Function` 就会完成。</span><span class="sxs-lookup"><span data-stu-id="36060-144">The `For Each` loop completes when the end of the iterator function or a `Return` or `Exit Function` statement is reached.</span></span>  
  
## <a name="example"></a><span data-ttu-id="36060-145">示例</span><span class="sxs-lookup"><span data-stu-id="36060-145">Example</span></span>  

 <span data-ttu-id="36060-146">下面的示例包含一个 `Yield` 位于 [For .。。下一个](for-next-statement.md) 循环。</span><span class="sxs-lookup"><span data-stu-id="36060-146">The following example has a `Yield` statement that is inside a [For…Next](for-next-statement.md) loop.</span></span> <span data-ttu-id="36060-147">中 [每](for-each-next-statement.md) 个语句体的每次迭代 `Main` 都会创建对 `Power` 迭代器函数的调用。</span><span class="sxs-lookup"><span data-stu-id="36060-147">Each iteration of the [For Each](for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="36060-148">对迭代器函数的每个调用将继续到 `Yield` 语句的下一次执行（在 `For…Next` 循环的下一次迭代期间发生）。</span><span class="sxs-lookup"><span data-stu-id="36060-148">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 <span data-ttu-id="36060-149">迭代器方法的返回类型是 <xref:System.Collections.Generic.IEnumerable%601> ，迭代器接口类型。</span><span class="sxs-lookup"><span data-stu-id="36060-149">The return type of the iterator method is <xref:System.Collections.Generic.IEnumerable%601>, an iterator interface type.</span></span> <span data-ttu-id="36060-150">当调用迭代器方法时，它将返回一个包含数字幂的可枚举对象。</span><span class="sxs-lookup"><span data-stu-id="36060-150">When the iterator method is called, it returns an enumerable object that contains the powers of a number.</span></span>  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a><span data-ttu-id="36060-151">示例</span><span class="sxs-lookup"><span data-stu-id="36060-151">Example</span></span>  

 <span data-ttu-id="36060-152">下面的示例演示一个作为迭代器的 `Get` 访问器。</span><span class="sxs-lookup"><span data-stu-id="36060-152">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="36060-153">属性声明包含 `Iterator` 修饰符。</span><span class="sxs-lookup"><span data-stu-id="36060-153">The property declaration includes an `Iterator` modifier.</span></span>  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 <span data-ttu-id="36060-154">有关其他示例，请参阅 [迭代](../../programming-guide/concepts/iterators.md)器。</span><span class="sxs-lookup"><span data-stu-id="36060-154">For additional examples, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36060-155">请参阅</span><span class="sxs-lookup"><span data-stu-id="36060-155">See also</span></span>

- [<span data-ttu-id="36060-156">语句</span><span class="sxs-lookup"><span data-stu-id="36060-156">Statements</span></span>](index.md)
