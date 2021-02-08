---
description: '详细了解： &amp; = 运算符 (Visual Basic) '
title: '&amp;= 运算符'
ms.date: 07/20/2015
f1_keywords:
- vb.&=
helpviewer_keywords:
- operator &=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '&= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 0cf262fc-1a05-419a-a503-60013f111c8a
ms.openlocfilehash: ffc4de352ee29f4c7d18a257dd3699b37c668db7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774312"
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="ea07c-103">&amp;= 运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ea07c-103">&amp;= Operator (Visual Basic)</span></span>

<span data-ttu-id="ea07c-104">将 `String` 表达式连接到 `String` 变量或属性，并将结果赋给变量或属性。</span><span class="sxs-lookup"><span data-stu-id="ea07c-104">Concatenates a `String` expression to a `String` variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea07c-105">语法</span><span class="sxs-lookup"><span data-stu-id="ea07c-105">Syntax</span></span>  
  
```vb  
variableorproperty &= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="ea07c-106">组成部分</span><span class="sxs-lookup"><span data-stu-id="ea07c-106">Parts</span></span>  

 `variableorproperty`  
 <span data-ttu-id="ea07c-107">必需。</span><span class="sxs-lookup"><span data-stu-id="ea07c-107">Required.</span></span> <span data-ttu-id="ea07c-108">任何 `String` 变量或属性。</span><span class="sxs-lookup"><span data-stu-id="ea07c-108">Any `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="ea07c-109">必需。</span><span class="sxs-lookup"><span data-stu-id="ea07c-109">Required.</span></span> <span data-ttu-id="ea07c-110">任何 `String` 表达式。</span><span class="sxs-lookup"><span data-stu-id="ea07c-110">Any `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea07c-111">备注</span><span class="sxs-lookup"><span data-stu-id="ea07c-111">Remarks</span></span>  

 <span data-ttu-id="ea07c-112">运算符左侧的元素 `&=` 可以是简单的标量变量、属性或数组的元素。</span><span class="sxs-lookup"><span data-stu-id="ea07c-112">The element on the left side of the `&=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="ea07c-113">变量或属性不能是 [只读](../modifiers/readonly.md)的。</span><span class="sxs-lookup"><span data-stu-id="ea07c-113">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span> <span data-ttu-id="ea07c-114">`&=`运算符将 `String` 其右侧的表达式连接到左侧的 `String` 变量或属性，并将结果赋给其左侧的变量或属性。</span><span class="sxs-lookup"><span data-stu-id="ea07c-114">The `&=` operator concatenates the `String` expression on its right to the `String` variable or property on its left, and assigns the result to the variable or property on its left.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="ea07c-115">重载</span><span class="sxs-lookup"><span data-stu-id="ea07c-115">Overloading</span></span>  

 <span data-ttu-id="ea07c-116">可以 *重载* [& 运算符](concatenation-operator.md)，这意味着当操作数具有该类或结构的类型时，该类或结构可以重新定义其行为。</span><span class="sxs-lookup"><span data-stu-id="ea07c-116">The [& Operator](concatenation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="ea07c-117">重载 `&` 运算符会影响运算符的行为 `&=` 。</span><span class="sxs-lookup"><span data-stu-id="ea07c-117">Overloading the `&` operator affects the behavior of the `&=` operator.</span></span> <span data-ttu-id="ea07c-118">如果你的代码 `&=` 在重载的类或结构上使用 `&` ，请确保你了解其重新定义的行为。</span><span class="sxs-lookup"><span data-stu-id="ea07c-118">If your code uses `&=` on a class or structure that overloads `&`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="ea07c-119">有关详细信息，请参阅 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="ea07c-119">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea07c-120">示例</span><span class="sxs-lookup"><span data-stu-id="ea07c-120">Example</span></span>  

 <span data-ttu-id="ea07c-121">下面的示例使用 `&=` 运算符将两个变量连接起来 `String` ，并将结果赋给第一个变量。</span><span class="sxs-lookup"><span data-stu-id="ea07c-121">The following example uses the `&=` operator to concatenate two `String` variables and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="ea07c-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="ea07c-122">See also</span></span>

- [<span data-ttu-id="ea07c-123">& 运算符</span><span class="sxs-lookup"><span data-stu-id="ea07c-123">& Operator</span></span>](concatenation-operator.md)
- [<span data-ttu-id="ea07c-124">+ = 运算符</span><span class="sxs-lookup"><span data-stu-id="ea07c-124">+= Operator</span></span>](addition-assignment-operator.md)
- [<span data-ttu-id="ea07c-125">赋值运算符</span><span class="sxs-lookup"><span data-stu-id="ea07c-125">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="ea07c-126">串联运算符</span><span class="sxs-lookup"><span data-stu-id="ea07c-126">Concatenation Operators</span></span>](concatenation-operators.md)
- [<span data-ttu-id="ea07c-127">Visual Basic 中的运算符优先级</span><span class="sxs-lookup"><span data-stu-id="ea07c-127">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="ea07c-128">按功能列出的运算符</span><span class="sxs-lookup"><span data-stu-id="ea07c-128">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="ea07c-129">语句</span><span class="sxs-lookup"><span data-stu-id="ea07c-129">Statements</span></span>](../../programming-guide/language-features/statements.md)
