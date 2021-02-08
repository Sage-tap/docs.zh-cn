---
description: '详细了解： OrElse Operator (Visual Basic) '
title: OrElse 运算符
ms.date: 07/20/2015
f1_keywords:
- OrElse
- vb.OrElse
helpviewer_keywords:
- short-circuiting
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], disjunction
- short-circuit evaluation
- OrElse operator [Visual Basic]
ms.assetid: 253803d8-05b0-47d7-b213-abd222847779
ms.openlocfilehash: 48ccbda1e0cb4f655b28e902b22fbfe0c3e66ac8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795321"
---
# <a name="orelse-operator-visual-basic"></a><span data-ttu-id="12a62-103">OrElse 运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="12a62-103">OrElse Operator (Visual Basic)</span></span>

<span data-ttu-id="12a62-104">对两个表达式执行短路包含逻辑析取。</span><span class="sxs-lookup"><span data-stu-id="12a62-104">Performs short-circuiting inclusive logical disjunction on two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12a62-105">语法</span><span class="sxs-lookup"><span data-stu-id="12a62-105">Syntax</span></span>  
  
```vb
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="12a62-106">组成部分</span><span class="sxs-lookup"><span data-stu-id="12a62-106">Parts</span></span>  

 `result`  
 <span data-ttu-id="12a62-107">必需。</span><span class="sxs-lookup"><span data-stu-id="12a62-107">Required.</span></span> <span data-ttu-id="12a62-108">任何 `Boolean` 表达式。</span><span class="sxs-lookup"><span data-stu-id="12a62-108">Any `Boolean` expression.</span></span>  
  
 `expression1`  
 <span data-ttu-id="12a62-109">必需。</span><span class="sxs-lookup"><span data-stu-id="12a62-109">Required.</span></span> <span data-ttu-id="12a62-110">任何 `Boolean` 表达式。</span><span class="sxs-lookup"><span data-stu-id="12a62-110">Any `Boolean` expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="12a62-111">必需。</span><span class="sxs-lookup"><span data-stu-id="12a62-111">Required.</span></span> <span data-ttu-id="12a62-112">任何 `Boolean` 表达式。</span><span class="sxs-lookup"><span data-stu-id="12a62-112">Any `Boolean` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12a62-113">备注</span><span class="sxs-lookup"><span data-stu-id="12a62-113">Remarks</span></span>  

 <span data-ttu-id="12a62-114">如果编译后的代码可以根据另一个表达式的结果跳过对一个表达式的计算，则将逻辑运算称为 *短路* 。</span><span class="sxs-lookup"><span data-stu-id="12a62-114">A logical operation is said to be *short-circuiting* if the compiled code can bypass the evaluation of one expression depending on the result of another expression.</span></span> <span data-ttu-id="12a62-115">如果第一个表达式的计算结果确定了运算的最终结果，则不需要计算第二个表达式，因为它不能更改最终结果。</span><span class="sxs-lookup"><span data-stu-id="12a62-115">If the result of the first expression evaluated determines the final result of the operation, there is no need to evaluate the second expression, because it cannot change the final result.</span></span> <span data-ttu-id="12a62-116">如果绕过的表达式较复杂，或者它涉及过程调用，则短路可以提高性能。</span><span class="sxs-lookup"><span data-stu-id="12a62-116">Short-circuiting can improve performance if the bypassed expression is complex, or if it involves procedure calls.</span></span>  
  
 <span data-ttu-id="12a62-117">如果任意一个或两个表达式的计算结果为 `True` ， `result` 则为 `True` 。</span><span class="sxs-lookup"><span data-stu-id="12a62-117">If either or both expressions evaluate to `True`, `result` is `True`.</span></span> <span data-ttu-id="12a62-118">下表说明了如何 `result` 确定。</span><span class="sxs-lookup"><span data-stu-id="12a62-118">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="12a62-119">如果 `expression1` 为 </span><span class="sxs-lookup"><span data-stu-id="12a62-119">If `expression1` is</span></span>|<span data-ttu-id="12a62-120">并且 `expression2` 为</span><span class="sxs-lookup"><span data-stu-id="12a62-120">And `expression2` is</span></span>|<span data-ttu-id="12a62-121">的值 `result` 为</span><span class="sxs-lookup"><span data-stu-id="12a62-121">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|<span data-ttu-id="12a62-122">不计算 () </span><span class="sxs-lookup"><span data-stu-id="12a62-122">(not evaluated)</span></span>|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a><span data-ttu-id="12a62-123">数据类型</span><span class="sxs-lookup"><span data-stu-id="12a62-123">Data Types</span></span>  

 <span data-ttu-id="12a62-124">`OrElse`仅为[布尔数据类型](../data-types/boolean-data-type.md)定义运算符。</span><span class="sxs-lookup"><span data-stu-id="12a62-124">The `OrElse` operator is defined only for the [Boolean Data Type](../data-types/boolean-data-type.md).</span></span> <span data-ttu-id="12a62-125">Visual Basic 在计算表达式之前，根据需要将每个操作数转换为 `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="12a62-125">Visual Basic converts each operand as necessary to `Boolean` before evaluating the expression.</span></span> <span data-ttu-id="12a62-126">如果将结果赋给数值类型，Visual Basic 会将其从转换 `Boolean` 为该类型，使其 `False` 成为 `0` 并 `True` 变成 `-1` 。</span><span class="sxs-lookup"><span data-stu-id="12a62-126">If you assign the result to a numeric type, Visual Basic converts it from `Boolean` to that type such that `False` becomes `0` and `True` becomes `-1`.</span></span>
<span data-ttu-id="12a62-127">有关详细信息，请参阅 [布尔类型转换](../data-types/boolean-data-type.md#type-conversions)。</span><span class="sxs-lookup"><span data-stu-id="12a62-127">For more information, see [Boolean Type Conversions](../data-types/boolean-data-type.md#type-conversions).</span></span>
  
## <a name="overloading"></a><span data-ttu-id="12a62-128">重载</span><span class="sxs-lookup"><span data-stu-id="12a62-128">Overloading</span></span>  

 <span data-ttu-id="12a62-129">可以 *重载* [Or 运算符](or-operator.md)和 [IsTrue 运算符](istrue-operator.md)，这意味着当操作数具有该类或结构的类型时，该类或结构可以重新定义其行为。</span><span class="sxs-lookup"><span data-stu-id="12a62-129">The [Or Operator](or-operator.md) and the [IsTrue Operator](istrue-operator.md) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="12a62-130">重载 `Or` 和 `IsTrue` 运算符会影响运算符的行为 `OrElse` 。</span><span class="sxs-lookup"><span data-stu-id="12a62-130">Overloading the `Or` and `IsTrue` operators affects the behavior of the `OrElse` operator.</span></span> <span data-ttu-id="12a62-131">如果你的代码 `OrElse` 在重载和的类或结构上使用 `Or` `IsTrue` ，请确保你了解其重新定义的行为。</span><span class="sxs-lookup"><span data-stu-id="12a62-131">If your code uses `OrElse` on a class or structure that overloads `Or` and `IsTrue`, be sure you understand their redefined behavior.</span></span> <span data-ttu-id="12a62-132">有关详细信息，请参阅 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="12a62-132">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="12a62-133">示例</span><span class="sxs-lookup"><span data-stu-id="12a62-133">Example</span></span>  

 <span data-ttu-id="12a62-134">下面的示例使用 `OrElse` 运算符对两个表达式执行逻辑析取。</span><span class="sxs-lookup"><span data-stu-id="12a62-134">The following example uses the `OrElse` operator to perform logical disjunction on two expressions.</span></span> <span data-ttu-id="12a62-135">结果是一个 `Boolean` 值，该值表示两个表达式之一是否为 true。</span><span class="sxs-lookup"><span data-stu-id="12a62-135">The result is a `Boolean` value that represents whether either of the two expressions is true.</span></span> <span data-ttu-id="12a62-136">如果第一个表达式为 `True` ，则不计算第二个表达式。</span><span class="sxs-lookup"><span data-stu-id="12a62-136">If the first expression is `True`, the second is not evaluated.</span></span>  
  
 [!code-vb[VbVbalrOperators#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#37)]  
  
 <span data-ttu-id="12a62-137">前面的示例 `True` 分别生成、 `True` 和的结果 `False` 。</span><span class="sxs-lookup"><span data-stu-id="12a62-137">The preceding example produces results of `True`, `True`, and `False` respectively.</span></span> <span data-ttu-id="12a62-138">在的计算中 `firstCheck` ，不计算第二个表达式，因为第一个表达式已经存在 `True` 。</span><span class="sxs-lookup"><span data-stu-id="12a62-138">In the calculation of `firstCheck`, the second expression is not evaluated because the first is already `True`.</span></span> <span data-ttu-id="12a62-139">但是，在的计算中计算第二个表达式 `secondCheck` 。</span><span class="sxs-lookup"><span data-stu-id="12a62-139">However, the second expression is evaluated in the calculation of `secondCheck`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="12a62-140">示例</span><span class="sxs-lookup"><span data-stu-id="12a62-140">Example</span></span>  

 <span data-ttu-id="12a62-141">下面的示例显示了 `If` `Then` 包含两个过程调用的 ... 语句。</span><span class="sxs-lookup"><span data-stu-id="12a62-141">The following example shows an `If`...`Then` statement containing two procedure calls.</span></span> <span data-ttu-id="12a62-142">如果第一次调用返回 `True` ，则不会调用第二个过程。</span><span class="sxs-lookup"><span data-stu-id="12a62-142">If the first call returns `True`, the second procedure is not called.</span></span> <span data-ttu-id="12a62-143">如果第二个过程执行的重要任务应始终在此部分代码运行时执行，这可能会产生意外的结果。</span><span class="sxs-lookup"><span data-stu-id="12a62-143">This could produce unexpected results if the second procedure performs important tasks that should always be performed when this section of the code runs.</span></span>  
  
 [!code-vb[VbVbalrOperators#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#38)]  
  
## <a name="see-also"></a><span data-ttu-id="12a62-144">请参阅</span><span class="sxs-lookup"><span data-stu-id="12a62-144">See also</span></span>

- [<span data-ttu-id="12a62-145">逻辑/按位运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="12a62-145">Logical/Bitwise Operators (Visual Basic)</span></span>](logical-bitwise-operators.md)
- [<span data-ttu-id="12a62-146">Visual Basic 中的运算符优先级</span><span class="sxs-lookup"><span data-stu-id="12a62-146">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="12a62-147">按功能列出的运算符</span><span class="sxs-lookup"><span data-stu-id="12a62-147">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="12a62-148">Or 运算符</span><span class="sxs-lookup"><span data-stu-id="12a62-148">Or Operator</span></span>](or-operator.md)
- [<span data-ttu-id="12a62-149">IsTrue 运算符</span><span class="sxs-lookup"><span data-stu-id="12a62-149">IsTrue Operator</span></span>](istrue-operator.md)
- [<span data-ttu-id="12a62-150">Visual Basic 中的逻辑运算符和位运算符</span><span class="sxs-lookup"><span data-stu-id="12a62-150">Logical and Bitwise Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
