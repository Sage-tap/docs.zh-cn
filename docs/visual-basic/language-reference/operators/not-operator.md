---
description: '详细了解： Not Operator (Visual Basic) '
title: Not 运算符
ms.date: 07/20/2015
f1_keywords:
- vb.Not
helpviewer_keywords:
- Boolean expressions, negating
- operators [Visual Basic], bitwise
- negation operator [Visual Basic]
- inverse bit values in variables [Visual Basic]
- bitwise operators [Visual Basic], NOT operator
- bitwise comparison [Visual Basic]
- Not operator [Visual Basic]
- logical negation
- operators [Visual Basic], negation
ms.assetid: 8f2ea83c-d2ed-480a-a474-3042a1cad9b5
ms.openlocfilehash: 91f3525b52d6f38081b8e5ba208c193f714a4045
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665349"
---
# <a name="not-operator-visual-basic"></a><span data-ttu-id="f3539-103">Not 运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f3539-103">Not Operator (Visual Basic)</span></span>

<span data-ttu-id="f3539-104">对表达式执行逻辑非运算 `Boolean` ，或对数值表达式执行位求反运算。</span><span class="sxs-lookup"><span data-stu-id="f3539-104">Performs logical negation on a `Boolean` expression, or bitwise negation on a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3539-105">语法</span><span class="sxs-lookup"><span data-stu-id="f3539-105">Syntax</span></span>  
  
```vb  
result = Not expression  
```  
  
## <a name="parts"></a><span data-ttu-id="f3539-106">组成部分</span><span class="sxs-lookup"><span data-stu-id="f3539-106">Parts</span></span>  

 `result`  
 <span data-ttu-id="f3539-107">必需。</span><span class="sxs-lookup"><span data-stu-id="f3539-107">Required.</span></span> <span data-ttu-id="f3539-108">任何 `Boolean` 或数值表达式。</span><span class="sxs-lookup"><span data-stu-id="f3539-108">Any `Boolean` or numeric expression.</span></span>  
  
 `expression`  
 <span data-ttu-id="f3539-109">必需。</span><span class="sxs-lookup"><span data-stu-id="f3539-109">Required.</span></span> <span data-ttu-id="f3539-110">任何 `Boolean` 或数值表达式。</span><span class="sxs-lookup"><span data-stu-id="f3539-110">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3539-111">备注</span><span class="sxs-lookup"><span data-stu-id="f3539-111">Remarks</span></span>  

 <span data-ttu-id="f3539-112">对于 `Boolean` 表达式，下表说明了如何 `result` 确定。</span><span class="sxs-lookup"><span data-stu-id="f3539-112">For `Boolean` expressions, the following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="f3539-113">如果 `expression` 为 </span><span class="sxs-lookup"><span data-stu-id="f3539-113">If `expression` is</span></span>|<span data-ttu-id="f3539-114">的值 `result` 为</span><span class="sxs-lookup"><span data-stu-id="f3539-114">The value of `result` is</span></span>|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 <span data-ttu-id="f3539-115">对于数值表达式， `Not` 运算符反转任何数值表达式的位值，并根据下表设置中的相应位 `result` 。</span><span class="sxs-lookup"><span data-stu-id="f3539-115">For numeric expressions, the `Not` operator inverts the bit values of any numeric expression and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="f3539-116">如果中的位 `expression` 是</span><span class="sxs-lookup"><span data-stu-id="f3539-116">If bit in `expression` is</span></span>|<span data-ttu-id="f3539-117">中的位 `result` 是</span><span class="sxs-lookup"><span data-stu-id="f3539-117">The bit in `result` is</span></span>|  
|-------------------------------|----------------------------|  
|<span data-ttu-id="f3539-118">1</span><span class="sxs-lookup"><span data-stu-id="f3539-118">1</span></span>|<span data-ttu-id="f3539-119">0</span><span class="sxs-lookup"><span data-stu-id="f3539-119">0</span></span>|  
|<span data-ttu-id="f3539-120">0</span><span class="sxs-lookup"><span data-stu-id="f3539-120">0</span></span>|<span data-ttu-id="f3539-121">1</span><span class="sxs-lookup"><span data-stu-id="f3539-121">1</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="f3539-122">由于逻辑 and 位运算符的优先级低于其他算术运算符和关系运算符，因此应将任何按位运算括在括号中，以确保准确执行。</span><span class="sxs-lookup"><span data-stu-id="f3539-122">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="f3539-123">数据类型</span><span class="sxs-lookup"><span data-stu-id="f3539-123">Data Types</span></span>  

 <span data-ttu-id="f3539-124">对于布尔求反，结果的数据类型为 `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="f3539-124">For a Boolean negation, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="f3539-125">对于按位求反，结果数据类型与的数据类型相同 `expression` 。</span><span class="sxs-lookup"><span data-stu-id="f3539-125">For a bitwise negation, the result data type is the same as that of `expression`.</span></span> <span data-ttu-id="f3539-126">但是，如果 expression 为 `Decimal` ，则结果为 `Long` 。</span><span class="sxs-lookup"><span data-stu-id="f3539-126">However, if expression is `Decimal`, the result is `Long`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="f3539-127">重载</span><span class="sxs-lookup"><span data-stu-id="f3539-127">Overloading</span></span>  

 <span data-ttu-id="f3539-128">`Not`运算符可以 *重载*，这意味着当类或结构的操作数具有该类或结构的类型时，该类或结构可以重新定义它的行为。</span><span class="sxs-lookup"><span data-stu-id="f3539-128">The `Not` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="f3539-129">如果你的代码在该类或结构上使用此运算符，请确保了解其重新定义的行为。</span><span class="sxs-lookup"><span data-stu-id="f3539-129">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="f3539-130">有关详细信息，请参阅 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="f3539-130">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3539-131">示例</span><span class="sxs-lookup"><span data-stu-id="f3539-131">Example</span></span>  

 <span data-ttu-id="f3539-132">下面的示例使用 `Not` 运算符对表达式执行逻辑非运算 `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="f3539-132">The following example uses the `Not` operator to perform logical negation on a `Boolean` expression.</span></span> <span data-ttu-id="f3539-133">结果是一个 `Boolean` 值，该值表示表达式的值的逆值。</span><span class="sxs-lookup"><span data-stu-id="f3539-133">The result is a `Boolean` value that represents the reverse of the value of the expression.</span></span>  
  
 [!code-vb[VbVbalrOperators#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#33)]  
  
 <span data-ttu-id="f3539-134">前面的示例分别生成和的结果 `False` `True` 。</span><span class="sxs-lookup"><span data-stu-id="f3539-134">The preceding example produces results of `False` and `True`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3539-135">示例</span><span class="sxs-lookup"><span data-stu-id="f3539-135">Example</span></span>  

 <span data-ttu-id="f3539-136">下面的示例使用 `Not` 运算符对数值表达式的各个位执行逻辑求反运算。</span><span class="sxs-lookup"><span data-stu-id="f3539-136">The following example uses the `Not` operator to perform logical negation of the individual bits of a numeric expression.</span></span> <span data-ttu-id="f3539-137">结果模式中的位设置为操作数模式中相应位的反向，其中包括符号位。</span><span class="sxs-lookup"><span data-stu-id="f3539-137">The bit in the result pattern is set to the reverse of the corresponding bit in the operand pattern, including the sign bit.</span></span>  
  
 [!code-vb[VbVbalrOperators#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#34)]  
  
 <span data-ttu-id="f3539-138">前面的示例分别产生–11、–9和–7的结果。</span><span class="sxs-lookup"><span data-stu-id="f3539-138">The preceding example produces results of –11, –9, and –7, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3539-139">请参阅</span><span class="sxs-lookup"><span data-stu-id="f3539-139">See also</span></span>

- [<span data-ttu-id="f3539-140">逻辑/按位运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f3539-140">Logical/Bitwise Operators (Visual Basic)</span></span>](logical-bitwise-operators.md)
- [<span data-ttu-id="f3539-141">Visual Basic 中的运算符优先级</span><span class="sxs-lookup"><span data-stu-id="f3539-141">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="f3539-142">按功能列出的运算符</span><span class="sxs-lookup"><span data-stu-id="f3539-142">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="f3539-143">Visual Basic 中的逻辑运算符和位运算符</span><span class="sxs-lookup"><span data-stu-id="f3539-143">Logical and Bitwise Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
