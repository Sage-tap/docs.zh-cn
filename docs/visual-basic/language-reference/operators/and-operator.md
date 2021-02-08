---
description: '详细了解：和运算符 (Visual Basic) '
title: And 运算符
ms.date: 07/20/2015
f1_keywords:
- vb.And
helpviewer_keywords:
- operators [Visual Basic], bitwise
- logical conjunction
- bitwise AND operator [Visual Basic]
- conjunction operator [Visual Basic]
- And operator [Visual Basic]
- bitwise operators [Visual Basic], AND operator
- operators [Visual Basic], conjunction
- bitwise comparison [Visual Basic]
ms.assetid: 2ea711f3-439a-4c7c-9e3a-1ffe3b0d6046
ms.openlocfilehash: 238ef0b2f14f2014da6e65684bfac183e03d963e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774273"
---
# <a name="and-operator-visual-basic"></a><span data-ttu-id="58c4c-103">And 运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58c4c-103">And Operator (Visual Basic)</span></span>

<span data-ttu-id="58c4c-104">对两个表达式执行逻辑与运算 `Boolean` ，或对两个数值表达式执行位与运算。</span><span class="sxs-lookup"><span data-stu-id="58c4c-104">Performs a logical conjunction on two `Boolean` expressions, or a bitwise conjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58c4c-105">语法</span><span class="sxs-lookup"><span data-stu-id="58c4c-105">Syntax</span></span>  
  
```vb  
result = expression1 And expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="58c4c-106">组成部分</span><span class="sxs-lookup"><span data-stu-id="58c4c-106">Parts</span></span>  

 `result`  
 <span data-ttu-id="58c4c-107">必需。</span><span class="sxs-lookup"><span data-stu-id="58c4c-107">Required.</span></span> <span data-ttu-id="58c4c-108">任何 `Boolean` 或数值表达式。</span><span class="sxs-lookup"><span data-stu-id="58c4c-108">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="58c4c-109">对于布尔值比较， `result` 是两个值的逻辑与 `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="58c4c-109">For Boolean comparison, `result` is the logical conjunction of two `Boolean` values.</span></span> <span data-ttu-id="58c4c-110">对于按位运算， `result` 是表示两个数值位模式的按位 "与" 的数值。</span><span class="sxs-lookup"><span data-stu-id="58c4c-110">For bitwise operations, `result` is a numeric value representing the bitwise conjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="58c4c-111">必需。</span><span class="sxs-lookup"><span data-stu-id="58c4c-111">Required.</span></span> <span data-ttu-id="58c4c-112">任何 `Boolean` 或数值表达式。</span><span class="sxs-lookup"><span data-stu-id="58c4c-112">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="58c4c-113">必需。</span><span class="sxs-lookup"><span data-stu-id="58c4c-113">Required.</span></span> <span data-ttu-id="58c4c-114">任何 `Boolean` 或数值表达式。</span><span class="sxs-lookup"><span data-stu-id="58c4c-114">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58c4c-115">备注</span><span class="sxs-lookup"><span data-stu-id="58c4c-115">Remarks</span></span>  

 <span data-ttu-id="58c4c-116">对于布尔值比较 `result` ， `True` 如果和均为，则为 `expression1` `expression2` `True` 。</span><span class="sxs-lookup"><span data-stu-id="58c4c-116">For Boolean comparison, `result` is `True` if and only if both `expression1` and `expression2` evaluate to `True`.</span></span> <span data-ttu-id="58c4c-117">下表说明了如何 `result` 确定。</span><span class="sxs-lookup"><span data-stu-id="58c4c-117">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="58c4c-118">如果 `expression1` 为 </span><span class="sxs-lookup"><span data-stu-id="58c4c-118">If `expression1` is</span></span>|<span data-ttu-id="58c4c-119">并且 `expression2` 为</span><span class="sxs-lookup"><span data-stu-id="58c4c-119">And `expression2` is</span></span>|<span data-ttu-id="58c4c-120">的值 `result` 为</span><span class="sxs-lookup"><span data-stu-id="58c4c-120">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> <span data-ttu-id="58c4c-121">在布尔比较中， `And` 运算符始终计算两个表达式，这可能包括进行过程调用。</span><span class="sxs-lookup"><span data-stu-id="58c4c-121">In a Boolean comparison, the `And` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="58c4c-122">[AndAlso 运算符](andalso-operator.md)执行 *短路*，这意味着，如果 `expression1` 为，则 `False` `expression2` 不计算。</span><span class="sxs-lookup"><span data-stu-id="58c4c-122">The [AndAlso Operator](andalso-operator.md) performs *short-circuiting*, which means that if `expression1` is `False`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="58c4c-123">当应用于数值时，运算符将对 `And` 两个数值表达式中的相同位置执行按位比较，并根据下表设置中的相应位 `result` 。</span><span class="sxs-lookup"><span data-stu-id="58c4c-123">When applied to numeric values, the `And` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="58c4c-124">如果中的位 `expression1` 是</span><span class="sxs-lookup"><span data-stu-id="58c4c-124">If bit in `expression1` is</span></span>|<span data-ttu-id="58c4c-125">和中的位 `expression2` 是</span><span class="sxs-lookup"><span data-stu-id="58c4c-125">And bit in `expression2` is</span></span>|<span data-ttu-id="58c4c-126">中的位 `result` 是</span><span class="sxs-lookup"><span data-stu-id="58c4c-126">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="58c4c-127">1</span><span class="sxs-lookup"><span data-stu-id="58c4c-127">1</span></span>|<span data-ttu-id="58c4c-128">1</span><span class="sxs-lookup"><span data-stu-id="58c4c-128">1</span></span>|<span data-ttu-id="58c4c-129">1</span><span class="sxs-lookup"><span data-stu-id="58c4c-129">1</span></span>|  
|<span data-ttu-id="58c4c-130">1</span><span class="sxs-lookup"><span data-stu-id="58c4c-130">1</span></span>|<span data-ttu-id="58c4c-131">0</span><span class="sxs-lookup"><span data-stu-id="58c4c-131">0</span></span>|<span data-ttu-id="58c4c-132">0</span><span class="sxs-lookup"><span data-stu-id="58c4c-132">0</span></span>|  
|<span data-ttu-id="58c4c-133">0</span><span class="sxs-lookup"><span data-stu-id="58c4c-133">0</span></span>|<span data-ttu-id="58c4c-134">1</span><span class="sxs-lookup"><span data-stu-id="58c4c-134">1</span></span>|<span data-ttu-id="58c4c-135">0</span><span class="sxs-lookup"><span data-stu-id="58c4c-135">0</span></span>|  
|<span data-ttu-id="58c4c-136">0</span><span class="sxs-lookup"><span data-stu-id="58c4c-136">0</span></span>|<span data-ttu-id="58c4c-137">0</span><span class="sxs-lookup"><span data-stu-id="58c4c-137">0</span></span>|<span data-ttu-id="58c4c-138">0</span><span class="sxs-lookup"><span data-stu-id="58c4c-138">0</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="58c4c-139">由于逻辑运算符和位运算符的优先级低于其他算术运算符和关系运算符，因此应将任何按位运算括在括号中，以确保准确的结果。</span><span class="sxs-lookup"><span data-stu-id="58c4c-139">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate results.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="58c4c-140">数据类型</span><span class="sxs-lookup"><span data-stu-id="58c4c-140">Data Types</span></span>  

 <span data-ttu-id="58c4c-141">如果操作数由一个 `Boolean` 表达式和一个数值表达式组成，则 Visual Basic 会将 `Boolean` 表达式转换为数值， ( 为– 1; 对于) ，则将 `True` `False` 执行按位运算。</span><span class="sxs-lookup"><span data-stu-id="58c4c-141">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="58c4c-142">对于布尔值比较，结果的数据类型为 `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="58c4c-142">For a Boolean comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="58c4c-143">对于按位比较，结果数据类型是适用于和的数据类型的数值类型 `expression1` `expression2` 。</span><span class="sxs-lookup"><span data-stu-id="58c4c-143">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="58c4c-144">请参阅 [运算符结果的数据类型](data-types-of-operator-results.md)中的 "关系和按位比较" 表。</span><span class="sxs-lookup"><span data-stu-id="58c4c-144">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](data-types-of-operator-results.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="58c4c-145">`And`运算符可以 *重载*，这意味着当操作数具有该类或结构的类型时，该类或结构可以重新定义其行为。</span><span class="sxs-lookup"><span data-stu-id="58c4c-145">The `And` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="58c4c-146">如果你的代码在该类或结构上使用此运算符，请确保了解其重新定义的行为。</span><span class="sxs-lookup"><span data-stu-id="58c4c-146">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="58c4c-147">有关详细信息，请参阅 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="58c4c-147">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="58c4c-148">示例</span><span class="sxs-lookup"><span data-stu-id="58c4c-148">Example</span></span>  

 <span data-ttu-id="58c4c-149">下面的示例使用 `And` 运算符对两个表达式执行逻辑与运算。</span><span class="sxs-lookup"><span data-stu-id="58c4c-149">The following example uses the `And` operator to perform a logical conjunction on two expressions.</span></span> <span data-ttu-id="58c4c-150">结果是一个 `Boolean` 表示两个表达式是否都为的值 `True` 。</span><span class="sxs-lookup"><span data-stu-id="58c4c-150">The result is a `Boolean` value that represents whether both of the expressions are `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#22)]  
  
 <span data-ttu-id="58c4c-151">前面的示例分别生成和的结果 `True` `False` 。</span><span class="sxs-lookup"><span data-stu-id="58c4c-151">The preceding example produces results of `True` and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58c4c-152">示例</span><span class="sxs-lookup"><span data-stu-id="58c4c-152">Example</span></span>  

 <span data-ttu-id="58c4c-153">下面的示例使用 `And` 运算符对两个数值表达式的单个位执行逻辑与运算。</span><span class="sxs-lookup"><span data-stu-id="58c4c-153">The following example uses the `And` operator to perform logical conjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="58c4c-154">如果操作数中的相应位均设置为1，则结果模式中的位将设置为1。</span><span class="sxs-lookup"><span data-stu-id="58c4c-154">The bit in the result pattern is set if the corresponding bits in the operands are both set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#23)]  
  
 <span data-ttu-id="58c4c-155">前面的示例分别生成8、2和0的结果。</span><span class="sxs-lookup"><span data-stu-id="58c4c-155">The preceding example produces results of 8, 2, and 0, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58c4c-156">请参阅</span><span class="sxs-lookup"><span data-stu-id="58c4c-156">See also</span></span>

- [<span data-ttu-id="58c4c-157">逻辑/按位运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58c4c-157">Logical/Bitwise Operators (Visual Basic)</span></span>](logical-bitwise-operators.md)
- [<span data-ttu-id="58c4c-158">Visual Basic 中的运算符优先级</span><span class="sxs-lookup"><span data-stu-id="58c4c-158">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="58c4c-159">按功能列出的运算符</span><span class="sxs-lookup"><span data-stu-id="58c4c-159">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="58c4c-160">AndAlso 运算符</span><span class="sxs-lookup"><span data-stu-id="58c4c-160">AndAlso Operator</span></span>](andalso-operator.md)
- [<span data-ttu-id="58c4c-161">Visual Basic 中的逻辑运算符和位运算符</span><span class="sxs-lookup"><span data-stu-id="58c4c-161">Logical and Bitwise Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
