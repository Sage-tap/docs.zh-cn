---
description: 了解详细信息： Visual Basic 中的逻辑运算符和位运算符
title: 逻辑运算符和位运算符
ms.date: 07/20/2015
helpviewer_keywords:
- short-circuiting
- Boolean expressions
- logical operators [Visual Basic], Boolean expressions
- operators [Visual Basic], logical
- AndAlso operator [Visual Basic]
- Not operator [Visual Basic], Boolean expressions
- Xor operator [Visual Basic], Boolean expressions
- And operator [Visual Basic], logical operators
- logical operators [Visual Basic]
- expressions [Visual Basic], Boolean
- Or operator [Visual Basic], logical operators
- Visual Basic code, operators
- short-circuiting [Visual Basic], logical operators
- logical operators [Visual Basic], short-circuiting
- Visual Basic code, expressions
- logical operators [Visual Basic], binary
- OrElse operator [Visual Basic]
- logical operators [Visual Basic], unary
ms.assetid: ca474e13-567d-4b1d-a18b-301433705e57
ms.openlocfilehash: 55d9567813a9114573e1e3f70fe181cb8621b350
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100472717"
---
# <a name="logical-and-bitwise-operators-in-visual-basic"></a><span data-ttu-id="98918-103">Visual Basic 中的逻辑运算符和位运算符</span><span class="sxs-lookup"><span data-stu-id="98918-103">Logical and Bitwise Operators in Visual Basic</span></span>

<span data-ttu-id="98918-104">逻辑运算符比较 `Boolean` 表达式并返回 `Boolean` 结果。</span><span class="sxs-lookup"><span data-stu-id="98918-104">Logical operators compare `Boolean` expressions and return a `Boolean` result.</span></span> <span data-ttu-id="98918-105">`And`、、 `Or` `AndAlso` 、 `OrElse` 和 `Xor` 运算符都是 *二进制*，因为运算符采用两个操作数，而 `Not` 运算符是 *一元*，因为它采用单个操作数。</span><span class="sxs-lookup"><span data-stu-id="98918-105">The `And`, `Or`, `AndAlso`, `OrElse`, and `Xor` operators are *binary* because they take two operands, while the `Not` operator is *unary* because it takes a single operand.</span></span> <span data-ttu-id="98918-106">其中一些运算符还可以对整数值执行按位逻辑运算。</span><span class="sxs-lookup"><span data-stu-id="98918-106">Some of these operators can also perform bitwise logical operations on integral values.</span></span>  
  
## <a name="unary-logical-operator"></a><span data-ttu-id="98918-107">一元逻辑运算符</span><span class="sxs-lookup"><span data-stu-id="98918-107">Unary Logical Operator</span></span>  

 <span data-ttu-id="98918-108">[Not 运算符](../../../language-reference/operators/not-operator.md)对表达式执行逻辑非运算 `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="98918-108">The [Not Operator](../../../language-reference/operators/not-operator.md) performs logical *negation* on a `Boolean` expression.</span></span> <span data-ttu-id="98918-109">它生成其操作数的逻辑相反。</span><span class="sxs-lookup"><span data-stu-id="98918-109">It yields the logical opposite of its operand.</span></span> <span data-ttu-id="98918-110">如果表达式的计算结果为 `True` ，则 `Not` 返回 `False` ; 如果表达式的计算结果为， `False` `Not` `True` 则返回。</span><span class="sxs-lookup"><span data-stu-id="98918-110">If the expression evaluates to `True`, then `Not` returns `False`; if the expression evaluates to `False`, then `Not` returns `True`.</span></span> <span data-ttu-id="98918-111">下面的示例对此进行了演示。</span><span class="sxs-lookup"><span data-stu-id="98918-111">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#77)]  
  
## <a name="binary-logical-operators"></a><span data-ttu-id="98918-112">二元逻辑运算符</span><span class="sxs-lookup"><span data-stu-id="98918-112">Binary Logical Operators</span></span>  

 <span data-ttu-id="98918-113">[And 运算符](../../../language-reference/operators/and-operator.md)对两个表达式执行逻辑与 *运算* `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="98918-113">The [And Operator](../../../language-reference/operators/and-operator.md) performs logical *conjunction* on two `Boolean` expressions.</span></span> <span data-ttu-id="98918-114">如果两个表达式的计算结果都为 `True` ，则 `And` 返回 `True` 。</span><span class="sxs-lookup"><span data-stu-id="98918-114">If both expressions evaluate to `True`, then `And` returns `True`.</span></span> <span data-ttu-id="98918-115">如果至少有一个表达式的计算结果为 `False` ，则 `And` 返回 `False` 。</span><span class="sxs-lookup"><span data-stu-id="98918-115">If at least one of the expressions evaluates to `False`, then `And` returns `False`.</span></span>  
  
 <span data-ttu-id="98918-116">[Or 运算符](../../../language-reference/operators/or-operator.md)对两个表达式执行 *逻辑或\*\*运算* `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="98918-116">The [Or Operator](../../../language-reference/operators/or-operator.md) performs logical *disjunction* or *inclusion* on two `Boolean` expressions.</span></span> <span data-ttu-id="98918-117">如果两个表达式的计算结果为 `True` ，或均为计算结果 `True` ，则 `Or` 返回 `True` 。</span><span class="sxs-lookup"><span data-stu-id="98918-117">If either expression evaluates to `True`, or both evaluate to `True`, then `Or` returns `True`.</span></span> <span data-ttu-id="98918-118">如果两个表达式的计算结果均为 `True` ，则 `Or` 返回 `False` 。</span><span class="sxs-lookup"><span data-stu-id="98918-118">If neither expression evaluates to `True`, `Or` returns `False`.</span></span>  
  
 <span data-ttu-id="98918-119">[Xor 运算符](../../../language-reference/operators/xor-operator.md)对两个表达式执行逻辑 *异* 运算 `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="98918-119">The [Xor Operator](../../../language-reference/operators/xor-operator.md) performs logical *exclusion* on two `Boolean` expressions.</span></span> <span data-ttu-id="98918-120">如果恰好一个表达式的计算结果为 `True` ，而不是同时返回，则 `Xor` 返回 `True` 。</span><span class="sxs-lookup"><span data-stu-id="98918-120">If exactly one expression evaluates to `True`, but not both, `Xor` returns `True`.</span></span> <span data-ttu-id="98918-121">如果两个表达式的计算结果都为 `True` ，或者都为 `False` ，则 `Xor` 返回 `False` 。</span><span class="sxs-lookup"><span data-stu-id="98918-121">If both expressions evaluate to `True` or both evaluate to `False`, `Xor` returns `False`.</span></span>  
  
 <span data-ttu-id="98918-122">下面的示例演示了 `And` 、 `Or` 和 `Xor` 运算符。</span><span class="sxs-lookup"><span data-stu-id="98918-122">The following example illustrates the `And`, `Or`, and `Xor` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#78)]  
  
## <a name="short-circuiting-logical-operations"></a><span data-ttu-id="98918-123">Short-Circuiting 逻辑操作</span><span class="sxs-lookup"><span data-stu-id="98918-123">Short-Circuiting Logical Operations</span></span>  

 <span data-ttu-id="98918-124">[AndAlso 运算符](../../../language-reference/operators/andalso-operator.md)与运算符非常类似 `And` ，因为它还对两个表达式执行逻辑与运算 `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="98918-124">The [AndAlso Operator](../../../language-reference/operators/andalso-operator.md) is very similar to the `And` operator, in that it also performs logical conjunction on two `Boolean` expressions.</span></span> <span data-ttu-id="98918-125">这两者之间的主要区别在于 `AndAlso` 表现 *短路* 行为。</span><span class="sxs-lookup"><span data-stu-id="98918-125">The key difference between the two is that `AndAlso` exhibits *short-circuiting* behavior.</span></span> <span data-ttu-id="98918-126">如果表达式中的第一个表达式的 `AndAlso` 计算结果为 `False` ，则不会计算第二个表达式，因为它不能更改最终结果，并 `AndAlso` 返回 `False` 。</span><span class="sxs-lookup"><span data-stu-id="98918-126">If the first expression in an `AndAlso` expression evaluates to `False`, then the second expression is not evaluated because it cannot alter the final result, and `AndAlso` returns `False`.</span></span>  
  
 <span data-ttu-id="98918-127">同样， [OrElse 运算符](../../../language-reference/operators/orelse-operator.md) 对两个表达式执行短路逻辑析取 `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="98918-127">Similarly, the [OrElse Operator](../../../language-reference/operators/orelse-operator.md) performs short-circuiting logical disjunction on two `Boolean` expressions.</span></span> <span data-ttu-id="98918-128">如果表达式中的第一个表达式的 `OrElse` 计算结果为 `True` ，则不会计算第二个表达式，因为它不能更改最终结果，并 `OrElse` 返回 `True` 。</span><span class="sxs-lookup"><span data-stu-id="98918-128">If the first expression in an `OrElse` expression evaluates to `True`, then the second expression is not evaluated because it cannot alter the final result, and `OrElse` returns `True`.</span></span>  
  
### <a name="short-circuiting-trade-offs"></a><span data-ttu-id="98918-129">Short-Circuiting Trade-Offs</span><span class="sxs-lookup"><span data-stu-id="98918-129">Short-Circuiting Trade-Offs</span></span>  

 <span data-ttu-id="98918-130">短路可以通过不计算无法更改逻辑操作结果的表达式来提高性能。</span><span class="sxs-lookup"><span data-stu-id="98918-130">Short-circuiting can improve performance by not evaluating an expression that cannot alter the result of the logical operation.</span></span> <span data-ttu-id="98918-131">但是，如果该表达式执行其他操作，则短路将跳过这些操作。</span><span class="sxs-lookup"><span data-stu-id="98918-131">However, if that expression performs additional actions, short-circuiting skips those actions.</span></span> <span data-ttu-id="98918-132">例如，如果表达式包含对过程的调用，则在 `Function` 表达式为短路时不会调用该过程，并且中包含的任何其他代码都不 `Function` 会运行。</span><span class="sxs-lookup"><span data-stu-id="98918-132">For example, if the expression includes a call to a `Function` procedure, that procedure is not called if the expression is short-circuited, and any additional code contained in the `Function` does not run.</span></span> <span data-ttu-id="98918-133">因此，该函数可能会偶尔运行，并且可能无法正确测试。</span><span class="sxs-lookup"><span data-stu-id="98918-133">Therefore, the function might run only occasionally, and might not be tested correctly.</span></span> <span data-ttu-id="98918-134">或程序逻辑可能依赖于中的代码 `Function` 。</span><span class="sxs-lookup"><span data-stu-id="98918-134">Or the program logic might depend on the code in the `Function`.</span></span>  
  
 <span data-ttu-id="98918-135">下面的示例演示了 `And` 、 `Or` 和其短路对应项之间的差异。</span><span class="sxs-lookup"><span data-stu-id="98918-135">The following example illustrates the difference between `And`, `Or`, and their short-circuiting counterparts.</span></span>  
  
 [!code-vb[VbVbalrOperators#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#81)]  
  
 [!code-vb[VbVbalrOperators#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#80)]  
  
 [!code-vb[VbVbalrOperators#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#79)]  
  
 <span data-ttu-id="98918-136">在前面的示例中，请注意，当调用短路时，中的一些重要代码 `checkIfValid()` 不会运行。</span><span class="sxs-lookup"><span data-stu-id="98918-136">In the preceding example, note that some important code inside `checkIfValid()` does not run when the call is short-circuited.</span></span> <span data-ttu-id="98918-137">`If`即使返回，第一条语句 `checkIfValid()` 也 `12 > 45` 会调用 `False` ，因为 `And` 不会进行短路。</span><span class="sxs-lookup"><span data-stu-id="98918-137">The first `If` statement calls `checkIfValid()` even though `12 > 45` returns `False`, because `And` does not short-circuit.</span></span> <span data-ttu-id="98918-138">第二个 `If` 语句不调用 `checkIfValid()` ，因为当 `12 > 45` 返回时 `False` ，会 `AndAlso` 将第二个表达式短路。</span><span class="sxs-lookup"><span data-stu-id="98918-138">The second `If` statement does not call `checkIfValid()`, because when `12 > 45` returns `False`, `AndAlso` short-circuits the second expression.</span></span> <span data-ttu-id="98918-139">`If`即使返回，第三条语句 `checkIfValid()` 也 `12 < 45` 会调用 `True` ，因为 `Or` 不会进行短路。</span><span class="sxs-lookup"><span data-stu-id="98918-139">The third `If` statement calls `checkIfValid()` even though `12 < 45` returns `True`, because `Or` does not short-circuit.</span></span> <span data-ttu-id="98918-140">第四个 `If` 语句不调用 `checkIfValid()` ，因为当 `12 < 45` 返回时 `True` ，会 `OrElse` 将第二个表达式短路。</span><span class="sxs-lookup"><span data-stu-id="98918-140">The fourth `If` statement does not call `checkIfValid()`, because when `12 < 45` returns `True`, `OrElse` short-circuits the second expression.</span></span>  
  
## <a name="bitwise-operations"></a><span data-ttu-id="98918-141">按位运算</span><span class="sxs-lookup"><span data-stu-id="98918-141">Bitwise Operations</span></span>  

 <span data-ttu-id="98918-142">按位运算以 binary (第 2) 形式计算两个整数值。</span><span class="sxs-lookup"><span data-stu-id="98918-142">Bitwise operations evaluate two integral values in binary (base 2) form.</span></span> <span data-ttu-id="98918-143">它们比较相应位置上的位，然后基于比较分配值。</span><span class="sxs-lookup"><span data-stu-id="98918-143">They compare the bits at corresponding positions and then assign values based on the comparison.</span></span> <span data-ttu-id="98918-144">下面的示例阐释 `And` 运算符。</span><span class="sxs-lookup"><span data-stu-id="98918-144">The following example illustrates the `And` operator.</span></span>  
  
 [!code-vb[VbVbalrConcepts#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConcepts/VB/Class1.vb#2)]  
  
 <span data-ttu-id="98918-145">前面的示例将的值设置 `x` 为1。</span><span class="sxs-lookup"><span data-stu-id="98918-145">The preceding example sets the value of `x` to 1.</span></span> <span data-ttu-id="98918-146">出现这种情况的原因如下：</span><span class="sxs-lookup"><span data-stu-id="98918-146">This happens for the following reasons:</span></span>  
  
- <span data-ttu-id="98918-147">值被视为 binary：</span><span class="sxs-lookup"><span data-stu-id="98918-147">The values are treated as binary:</span></span>  
  
     <span data-ttu-id="98918-148">二进制格式的 3 = 011</span><span class="sxs-lookup"><span data-stu-id="98918-148">3 in binary form = 011</span></span>  
  
     <span data-ttu-id="98918-149">二进制格式的 5 = 101</span><span class="sxs-lookup"><span data-stu-id="98918-149">5 in binary form = 101</span></span>  
  
- <span data-ttu-id="98918-150">`And`运算符比较二进制表示形式，一次 (位) 一个二进制位置。</span><span class="sxs-lookup"><span data-stu-id="98918-150">The `And` operator compares the binary representations, one binary position (bit) at a time.</span></span> <span data-ttu-id="98918-151">如果给定位置处的两个位均为1，则将1置于结果中的该位置。</span><span class="sxs-lookup"><span data-stu-id="98918-151">If both bits at a given position are 1, then a 1 is placed in that position in the result.</span></span> <span data-ttu-id="98918-152">如果任一位为0，则将0放入结果中的该位置。</span><span class="sxs-lookup"><span data-stu-id="98918-152">If either bit is 0, then a 0 is placed in that position in the result.</span></span> <span data-ttu-id="98918-153">在前面的示例中，此过程如下所示：</span><span class="sxs-lookup"><span data-stu-id="98918-153">In the preceding example this works out as follows:</span></span>  
  
     <span data-ttu-id="98918-154">011 (3 二进制格式) </span><span class="sxs-lookup"><span data-stu-id="98918-154">011 (3 in binary form)</span></span>  
  
     <span data-ttu-id="98918-155">101 (二进制格式的 5) </span><span class="sxs-lookup"><span data-stu-id="98918-155">101 (5 in binary form)</span></span>  
  
     <span data-ttu-id="98918-156">001以二进制格式 (结果) </span><span class="sxs-lookup"><span data-stu-id="98918-156">001 (The result, in binary form)</span></span>  
  
- <span data-ttu-id="98918-157">结果被视为 decimal。</span><span class="sxs-lookup"><span data-stu-id="98918-157">The result is treated as decimal.</span></span> <span data-ttu-id="98918-158">值001是1的二进制表示形式，因此 `x` = 1。</span><span class="sxs-lookup"><span data-stu-id="98918-158">The value 001 is the binary representation of 1, so `x` = 1.</span></span>  
  
 <span data-ttu-id="98918-159">按位 `Or` 运算类似，不同之处在于，如果两个比较位中有一个或两个均为1，则将1分配给结果位。</span><span class="sxs-lookup"><span data-stu-id="98918-159">The bitwise `Or` operation is similar, except that a 1 is assigned to the result bit if either or both of the compared bits is 1.</span></span> <span data-ttu-id="98918-160">`Xor` 如果两个比较位 (都不) 为1，则将1指定给结果位。</span><span class="sxs-lookup"><span data-stu-id="98918-160">`Xor` assigns a 1 to the result bit if exactly one of the compared bits (not both) is 1.</span></span> <span data-ttu-id="98918-161">`Not` 采用单个操作数并反转所有位（包括符号位），并将该值分配给结果。</span><span class="sxs-lookup"><span data-stu-id="98918-161">`Not` takes a single operand and inverts all the bits, including the sign bit, and assigns that value to the result.</span></span> <span data-ttu-id="98918-162">这意味着，对于有符号正数， `Not` 始终返回负值，对于负数， `Not` 始终返回正值或零值。</span><span class="sxs-lookup"><span data-stu-id="98918-162">This means that for signed positive numbers, `Not` always returns a negative value, and for negative numbers, `Not` always returns a positive or zero value.</span></span>  
  
 <span data-ttu-id="98918-163">`AndAlso`和 `OrElse` 运算符不支持按位运算。</span><span class="sxs-lookup"><span data-stu-id="98918-163">The `AndAlso` and `OrElse` operators do not support bitwise operations.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="98918-164">只能对整数类型执行按位运算。</span><span class="sxs-lookup"><span data-stu-id="98918-164">Bitwise operations can be performed on integral types only.</span></span> <span data-ttu-id="98918-165">必须先将浮点值转换为整数类型，然后才能继续执行位运算。</span><span class="sxs-lookup"><span data-stu-id="98918-165">Floating-point values must be converted to integral types before bitwise operation can proceed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98918-166">请参阅</span><span class="sxs-lookup"><span data-stu-id="98918-166">See also</span></span>

- [<span data-ttu-id="98918-167">逻辑/按位运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="98918-167">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="98918-168">布尔表达式</span><span class="sxs-lookup"><span data-stu-id="98918-168">Boolean Expressions</span></span>](boolean-expressions.md)
- [<span data-ttu-id="98918-169">算术运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="98918-169">Arithmetic Operators in Visual Basic</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="98918-170">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="98918-170">Comparison Operators in Visual Basic</span></span>](comparison-operators.md)
- [<span data-ttu-id="98918-171">串联运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="98918-171">Concatenation Operators in Visual Basic</span></span>](concatenation-operators.md)
- [<span data-ttu-id="98918-172">运算符的有效组合</span><span class="sxs-lookup"><span data-stu-id="98918-172">Efficient Combination of Operators</span></span>](efficient-combination-of-operators.md)
