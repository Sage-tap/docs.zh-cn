---
description: '了解详细信息：运算符的有效组合 (Visual Basic) '
title: 运算符的有效组合
ms.date: 07/20/2015
helpviewer_keywords:
- expressions [Visual Basic], parentheses
- operators [Visual Basic], associativity
- expressions [Visual Basic], operators
- operators [Visual Basic], precedence
- Visual Basic code, operators
- Visual Basic code, expressions
- operators [Visual Basic], complex expressions
- expressions [Visual Basic], complex
- parentheses [Visual Basic], complex expressions
- numeric expressions
ms.assetid: bd22340e-b5be-458b-8772-3916c02309a4
ms.openlocfilehash: a4d2d0c1caeea95dd8d34b2033a398d26bcf63ef
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100476262"
---
# <a name="efficient-combination-of-operators-visual-basic"></a><span data-ttu-id="261b9-103">运算符的有效组合 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="261b9-103">Efficient Combination of Operators (Visual Basic)</span></span>

<span data-ttu-id="261b9-104">复杂表达式可以包含多个不同的运算符。</span><span class="sxs-lookup"><span data-stu-id="261b9-104">Complex expressions can contain many different operators.</span></span> <span data-ttu-id="261b9-105">下面的示例对此进行了演示。</span><span class="sxs-lookup"><span data-stu-id="261b9-105">The following example illustrates this.</span></span>  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 <span data-ttu-id="261b9-106">如前面的示例所示，创建复杂表达式需要透彻地理解运算符优先级的规则。</span><span class="sxs-lookup"><span data-stu-id="261b9-106">Creating complex expressions such as the one in the preceding example requires a thorough understanding of the rules of operator precedence.</span></span> <span data-ttu-id="261b9-107">有关详细信息，请参阅 [Visual Basic 中的运算符优先级](../../../language-reference/operators/operator-precedence.md)。</span><span class="sxs-lookup"><span data-stu-id="261b9-107">For more information, see [Operator Precedence in Visual Basic](../../../language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="parenthetical-expressions"></a><span data-ttu-id="261b9-108">括号中的表达式</span><span class="sxs-lookup"><span data-stu-id="261b9-108">Parenthetical Expressions</span></span>  

 <span data-ttu-id="261b9-109">通常，你希望以不同于运算符优先级确定的顺序执行操作。</span><span class="sxs-lookup"><span data-stu-id="261b9-109">Often you want operations to proceed in a different order from that determined by operator precedence.</span></span> <span data-ttu-id="261b9-110">请看下面的示例。</span><span class="sxs-lookup"><span data-stu-id="261b9-110">Consider the following example.</span></span>  
  
 `x = z * y + 4`  
  
 <span data-ttu-id="261b9-111">前面的示例 `z` 将乘以 `y` ，然后将结果添加到 `4` 。</span><span class="sxs-lookup"><span data-stu-id="261b9-111">The preceding example multiplies `z` by `y`, then adds the result to `4`.</span></span> <span data-ttu-id="261b9-112">但是，如果想要在 `y` 将 `4` 结果与相乘之前添加 and `z` ，则可以通过使用括号覆盖普通运算符优先级。</span><span class="sxs-lookup"><span data-stu-id="261b9-112">But if you want to add `y` and `4` before multiplying the result by `z`, you can override normal operator precedence by using parentheses.</span></span> <span data-ttu-id="261b9-113">通过将表达式括在括号中，可以强制首先计算表达式，而不考虑运算符优先级。</span><span class="sxs-lookup"><span data-stu-id="261b9-113">By enclosing an expression in parentheses, you force that expression to be evaluated first, regardless of operator precedence.</span></span> <span data-ttu-id="261b9-114">若要强制前面的示例先执行加法操作，可以重写它，如以下示例中所示。</span><span class="sxs-lookup"><span data-stu-id="261b9-114">To force the preceding example to do the addition first, you could rewrite it as in the following example.</span></span>  
  
 `x = z * (y + 4)`  
  
 <span data-ttu-id="261b9-115">前面的示例添加 `y` and `4` ，然后将 sum 相乘 `z` 。</span><span class="sxs-lookup"><span data-stu-id="261b9-115">The preceding example adds `y` and `4`, then multiplies that sum by `z`.</span></span>  
  
### <a name="nested-parenthetical-expressions"></a><span data-ttu-id="261b9-116">嵌套的括号表达式</span><span class="sxs-lookup"><span data-stu-id="261b9-116">Nested Parenthetical Expressions</span></span>  

 <span data-ttu-id="261b9-117">可以将表达式嵌套在多个级别的括号中，以便进一步覆盖优先级。</span><span class="sxs-lookup"><span data-stu-id="261b9-117">You can nest expressions in multiple levels of parentheses to override precedence even further.</span></span> <span data-ttu-id="261b9-118">首先计算最深层嵌套在括号中的表达式，然后计算下一个最深层嵌套的表达式，依此类推到最深层嵌套的表达式，最后将表达式括在括号内。</span><span class="sxs-lookup"><span data-stu-id="261b9-118">The expressions most deeply nested in parentheses are evaluated first, followed by the next most deeply nested, and so on to the least deeply nested, and finally the expressions outside parentheses.</span></span> <span data-ttu-id="261b9-119">下面的示例对此进行了演示。</span><span class="sxs-lookup"><span data-stu-id="261b9-119">The following example illustrates this.</span></span>  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 <span data-ttu-id="261b9-120">在前面的示例中， `z + 2` 首先计算，然后是其他括号表达式。</span><span class="sxs-lookup"><span data-stu-id="261b9-120">In the preceding example, `z + 2` is evaluated first, then the other parenthetical expressions.</span></span> <span data-ttu-id="261b9-121">在此示例中，求幂的优先级通常高于加法或乘法，因为其他表达式括在括号中。</span><span class="sxs-lookup"><span data-stu-id="261b9-121">Exponentiation, which normally has higher precedence than addition or multiplication, is evaluated last in this example because the other expressions are enclosed in parentheses.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="261b9-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="261b9-122">See also</span></span>

- [<span data-ttu-id="261b9-123">算术运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="261b9-123">Arithmetic Operators in Visual Basic</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="261b9-124">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="261b9-124">Comparison Operators in Visual Basic</span></span>](comparison-operators.md)
- [<span data-ttu-id="261b9-125">Visual Basic 中的逻辑运算符和位运算符</span><span class="sxs-lookup"><span data-stu-id="261b9-125">Logical and Bitwise Operators in Visual Basic</span></span>](logical-and-bitwise-operators.md)
- [<span data-ttu-id="261b9-126">逻辑/按位运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="261b9-126">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="261b9-127">布尔表达式</span><span class="sxs-lookup"><span data-stu-id="261b9-127">Boolean Expressions</span></span>](boolean-expressions.md)
- [<span data-ttu-id="261b9-128">值的比较</span><span class="sxs-lookup"><span data-stu-id="261b9-128">Value Comparisons</span></span>](value-comparisons.md)
- [<span data-ttu-id="261b9-129">如何：计算数值</span><span class="sxs-lookup"><span data-stu-id="261b9-129">How to: Calculate Numeric Values</span></span>](how-to-calculate-numeric-values.md)
- [<span data-ttu-id="261b9-130">Visual Basic 中的运算符优先级</span><span class="sxs-lookup"><span data-stu-id="261b9-130">Operator Precedence in Visual Basic</span></span>](../../../language-reference/operators/operator-precedence.md)
