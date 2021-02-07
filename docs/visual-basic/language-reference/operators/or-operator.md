---
description: '了解有关以下方面的详细信息：或运算符 (Visual Basic) '
title: Or 运算符
ms.date: 07/20/2015
f1_keywords:
- vb.Or
helpviewer_keywords:
- Or operator [Visual Basic]
- operators [Visual Basic], bitwise
- inclusive Or operator [Visual Basic]
- bitwise operators [Visual Basic], OR operator
- Or keyword [Visual Basic]
- operators [Visual Basic], inclusive or
- operators [Visual Basic], disjunction
- bitwise comparison [Visual Basic]
- logical disjunction
- disjunction operator [Visual Basic]
ms.assetid: 41ed6905-bf3d-468a-9e3b-03c10d461891
ms.openlocfilehash: dfc50af2298c162707976e4b2eda9e9536aa64bc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99730325"
---
# <a name="or-operator-visual-basic"></a><span data-ttu-id="dc8ec-103">Or 运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dc8ec-103">Or Operator (Visual Basic)</span></span>

<span data-ttu-id="dc8ec-104">对两个表达式执行逻辑 `Boolean` 或运算，或对两个数值表达式执行按位析取。</span><span class="sxs-lookup"><span data-stu-id="dc8ec-104">Performs a logical disjunction on two `Boolean` expressions, or a bitwise disjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc8ec-105">语法</span><span class="sxs-lookup"><span data-stu-id="dc8ec-105">Syntax</span></span>  
  
```vb  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="dc8ec-106">组成部分</span><span class="sxs-lookup"><span data-stu-id="dc8ec-106">Parts</span></span>  

 `result`  
 <span data-ttu-id="dc8ec-107">必需。</span><span class="sxs-lookup"><span data-stu-id="dc8ec-107">Required.</span></span> <span data-ttu-id="dc8ec-108">任何 `Boolean` 或数值表达式。</span><span class="sxs-lookup"><span data-stu-id="dc8ec-108">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="dc8ec-109">为了进行 `Boolean` 比较， `result` 是两个值的包含逻辑析取 `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="dc8ec-109">For `Boolean` comparison, `result` is the inclusive logical disjunction of two `Boolean` values.</span></span> <span data-ttu-id="dc8ec-110">对于按位运算， `result` 是表示两个数值位模式的包含按位析取的数值。</span><span class="sxs-lookup"><span data-stu-id="dc8ec-110">For bitwise operations, `result` is a numeric value representing the inclusive bitwise disjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="dc8ec-111">必需。</span><span class="sxs-lookup"><span data-stu-id="dc8ec-111">Required.</span></span> <span data-ttu-id="dc8ec-112">任何 `Boolean` 或数值表达式。</span><span class="sxs-lookup"><span data-stu-id="dc8ec-112">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="dc8ec-113">必需。</span><span class="sxs-lookup"><span data-stu-id="dc8ec-113">Required.</span></span> <span data-ttu-id="dc8ec-114">任何 `Boolean` 或数值表达式。</span><span class="sxs-lookup"><span data-stu-id="dc8ec-114">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc8ec-115">备注</span><span class="sxs-lookup"><span data-stu-id="dc8ec-115">Remarks</span></span>  

 <span data-ttu-id="dc8ec-116">为了进行 `Boolean` 比较 `result` ， `False` 如果和的 `expression1` `expression2` 计算结果都为，则为 `False` 。</span><span class="sxs-lookup"><span data-stu-id="dc8ec-116">For `Boolean` comparison, `result` is `False` if and only if both `expression1` and `expression2` evaluate to `False`.</span></span> <span data-ttu-id="dc8ec-117">下表说明了如何 `result` 确定。</span><span class="sxs-lookup"><span data-stu-id="dc8ec-117">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="dc8ec-118">如果 `expression1` 为 </span><span class="sxs-lookup"><span data-stu-id="dc8ec-118">If `expression1` is</span></span>|<span data-ttu-id="dc8ec-119">并且 `expression2` 为</span><span class="sxs-lookup"><span data-stu-id="dc8ec-119">And `expression2` is</span></span>|<span data-ttu-id="dc8ec-120">的值 `result` 为</span><span class="sxs-lookup"><span data-stu-id="dc8ec-120">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> <span data-ttu-id="dc8ec-121">在 `Boolean` 比较中， `Or` 运算符始终计算两个表达式，这可能包括进行过程调用。</span><span class="sxs-lookup"><span data-stu-id="dc8ec-121">In a `Boolean` comparison, the `Or` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="dc8ec-122">[OrElse 运算符](orelse-operator.md)执行 *短路*，这意味着，如果 `expression1` 为，则 `True` `expression2` 不计算。</span><span class="sxs-lookup"><span data-stu-id="dc8ec-122">The [OrElse Operator](orelse-operator.md) performs *short-circuiting*, which means that if `expression1` is `True`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="dc8ec-123">对于按位运算， `Or` 运算符对两个数值表达式中的相同位置执行按位比较，并根据下表设置中的相应位 `result` 。</span><span class="sxs-lookup"><span data-stu-id="dc8ec-123">For bitwise operations, the `Or` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="dc8ec-124">如果中的位 `expression1` 是</span><span class="sxs-lookup"><span data-stu-id="dc8ec-124">If bit in `expression1` is</span></span>|<span data-ttu-id="dc8ec-125">和中的位 `expression2` 是</span><span class="sxs-lookup"><span data-stu-id="dc8ec-125">And bit in `expression2` is</span></span>|<span data-ttu-id="dc8ec-126">中的位 `result` 是</span><span class="sxs-lookup"><span data-stu-id="dc8ec-126">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="dc8ec-127">1</span><span class="sxs-lookup"><span data-stu-id="dc8ec-127">1</span></span>|<span data-ttu-id="dc8ec-128">1</span><span class="sxs-lookup"><span data-stu-id="dc8ec-128">1</span></span>|<span data-ttu-id="dc8ec-129">1</span><span class="sxs-lookup"><span data-stu-id="dc8ec-129">1</span></span>|  
|<span data-ttu-id="dc8ec-130">1</span><span class="sxs-lookup"><span data-stu-id="dc8ec-130">1</span></span>|<span data-ttu-id="dc8ec-131">0</span><span class="sxs-lookup"><span data-stu-id="dc8ec-131">0</span></span>|<span data-ttu-id="dc8ec-132">1</span><span class="sxs-lookup"><span data-stu-id="dc8ec-132">1</span></span>|  
|<span data-ttu-id="dc8ec-133">0</span><span class="sxs-lookup"><span data-stu-id="dc8ec-133">0</span></span>|<span data-ttu-id="dc8ec-134">1</span><span class="sxs-lookup"><span data-stu-id="dc8ec-134">1</span></span>|<span data-ttu-id="dc8ec-135">1</span><span class="sxs-lookup"><span data-stu-id="dc8ec-135">1</span></span>|  
|<span data-ttu-id="dc8ec-136">0</span><span class="sxs-lookup"><span data-stu-id="dc8ec-136">0</span></span>|<span data-ttu-id="dc8ec-137">0</span><span class="sxs-lookup"><span data-stu-id="dc8ec-137">0</span></span>|<span data-ttu-id="dc8ec-138">0</span><span class="sxs-lookup"><span data-stu-id="dc8ec-138">0</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="dc8ec-139">由于逻辑 and 位运算符的优先级低于其他算术运算符和关系运算符，因此应将任何按位运算括在括号中，以确保准确执行。</span><span class="sxs-lookup"><span data-stu-id="dc8ec-139">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="dc8ec-140">数据类型</span><span class="sxs-lookup"><span data-stu-id="dc8ec-140">Data Types</span></span>  

 <span data-ttu-id="dc8ec-141">如果操作数由一个 `Boolean` 表达式和一个数值表达式组成，则 Visual Basic 会将 `Boolean` 表达式转换为数值， ( 为– 1; 对于) ，则将 `True` `False` 执行按位运算。</span><span class="sxs-lookup"><span data-stu-id="dc8ec-141">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="dc8ec-142">对于 `Boolean` 比较，结果的数据类型为 `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="dc8ec-142">For a `Boolean` comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="dc8ec-143">对于按位比较，结果数据类型是适用于和的数据类型的数值类型 `expression1` `expression2` 。</span><span class="sxs-lookup"><span data-stu-id="dc8ec-143">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="dc8ec-144">请参阅 [运算符结果的数据类型](data-types-of-operator-results.md)中的 "关系和按位比较" 表。</span><span class="sxs-lookup"><span data-stu-id="dc8ec-144">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](data-types-of-operator-results.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="dc8ec-145">重载</span><span class="sxs-lookup"><span data-stu-id="dc8ec-145">Overloading</span></span>  

 <span data-ttu-id="dc8ec-146">`Or`运算符可以 *重载*，这意味着当操作数具有该类或结构的类型时，该类或结构可以重新定义其行为。</span><span class="sxs-lookup"><span data-stu-id="dc8ec-146">The `Or` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="dc8ec-147">如果你的代码在该类或结构上使用此运算符，请确保了解其重新定义的行为。</span><span class="sxs-lookup"><span data-stu-id="dc8ec-147">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="dc8ec-148">有关详细信息，请参阅 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="dc8ec-148">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc8ec-149">示例</span><span class="sxs-lookup"><span data-stu-id="dc8ec-149">Example</span></span>  

 <span data-ttu-id="dc8ec-150">下面的示例使用 `Or` 运算符对两个表达式执行包含逻辑析取。</span><span class="sxs-lookup"><span data-stu-id="dc8ec-150">The following example uses the `Or` operator to perform an inclusive logical disjunction on two expressions.</span></span> <span data-ttu-id="dc8ec-151">结果是一个 `Boolean` 值，该值表示两个表达式中的一个是否为 `True` 。</span><span class="sxs-lookup"><span data-stu-id="dc8ec-151">The result is a `Boolean` value that represents whether either of the two expressions is `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#35)]  
  
 <span data-ttu-id="dc8ec-152">前面的示例 `True` 分别生成、 `True` 和的结果 `False` 。</span><span class="sxs-lookup"><span data-stu-id="dc8ec-152">The preceding example produces results of `True`, `True`, and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc8ec-153">示例</span><span class="sxs-lookup"><span data-stu-id="dc8ec-153">Example</span></span>  

 <span data-ttu-id="dc8ec-154">下面的示例使用 `Or` 运算符对两个数值表达式的各个位执行包含逻辑析取。</span><span class="sxs-lookup"><span data-stu-id="dc8ec-154">The following example uses the `Or` operator to perform inclusive logical disjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="dc8ec-155">如果操作数中的相应位均设置为1，则结果模式中的位将设置为1。</span><span class="sxs-lookup"><span data-stu-id="dc8ec-155">The bit in the result pattern is set if either of the corresponding bits in the operands is set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#36)]  
  
 <span data-ttu-id="dc8ec-156">前面的示例分别生成10、14和14的结果。</span><span class="sxs-lookup"><span data-stu-id="dc8ec-156">The preceding example produces results of 10, 14, and 14, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc8ec-157">请参阅</span><span class="sxs-lookup"><span data-stu-id="dc8ec-157">See also</span></span>

- [<span data-ttu-id="dc8ec-158">逻辑/按位运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dc8ec-158">Logical/Bitwise Operators (Visual Basic)</span></span>](logical-bitwise-operators.md)
- [<span data-ttu-id="dc8ec-159">Visual Basic 中的运算符优先级</span><span class="sxs-lookup"><span data-stu-id="dc8ec-159">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="dc8ec-160">按功能列出的运算符</span><span class="sxs-lookup"><span data-stu-id="dc8ec-160">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="dc8ec-161">OrElse 运算符</span><span class="sxs-lookup"><span data-stu-id="dc8ec-161">OrElse Operator</span></span>](orelse-operator.md)
- [<span data-ttu-id="dc8ec-162">Visual Basic 中的逻辑运算符和位运算符</span><span class="sxs-lookup"><span data-stu-id="dc8ec-162">Logical and Bitwise Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
