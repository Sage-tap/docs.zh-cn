---
description: '详细了解：-= 运算符 (Visual Basic) '
title: -= 运算符
ms.date: 07/20/2015
f1_keywords:
- vb.-=
helpviewer_keywords:
- -= operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator -=
- compound assignment statements [Visual Basic]
ms.assetid: 5ead0c37-ae50-48f7-8435-8e341d81cae1
ms.openlocfilehash: 55574fa56d0ebe02fa5aef1a2711dfb3e5161a9e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795269"
---
# <a name="--operator-visual-basic"></a><span data-ttu-id="ed71d-103">-= 运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ed71d-103">-= Operator (Visual Basic)</span></span>

<span data-ttu-id="ed71d-104">从变量或属性的值中减去表达式的值，并将结果赋给变量或属性。</span><span class="sxs-lookup"><span data-stu-id="ed71d-104">Subtracts the value of an expression from the value of a variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed71d-105">语法</span><span class="sxs-lookup"><span data-stu-id="ed71d-105">Syntax</span></span>  
  
```vb  
variableorproperty -= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="ed71d-106">组成部分</span><span class="sxs-lookup"><span data-stu-id="ed71d-106">Parts</span></span>  

 `variableorproperty`  
 <span data-ttu-id="ed71d-107">必需。</span><span class="sxs-lookup"><span data-stu-id="ed71d-107">Required.</span></span> <span data-ttu-id="ed71d-108">任何数值变量或属性。</span><span class="sxs-lookup"><span data-stu-id="ed71d-108">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="ed71d-109">必需。</span><span class="sxs-lookup"><span data-stu-id="ed71d-109">Required.</span></span> <span data-ttu-id="ed71d-110">任何数值表达式。</span><span class="sxs-lookup"><span data-stu-id="ed71d-110">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed71d-111">备注</span><span class="sxs-lookup"><span data-stu-id="ed71d-111">Remarks</span></span>  

 <span data-ttu-id="ed71d-112">运算符左侧的元素 `-=` 可以是简单的标量变量、属性或数组的元素。</span><span class="sxs-lookup"><span data-stu-id="ed71d-112">The element on the left side of the `-=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="ed71d-113">变量或属性不能是 [只读](../modifiers/readonly.md)的。</span><span class="sxs-lookup"><span data-stu-id="ed71d-113">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="ed71d-114">`-=`运算符首先减去运算符右侧 (的表达式的值，) 从运算符) 左侧的变量或属性 (的值中的值开始。</span><span class="sxs-lookup"><span data-stu-id="ed71d-114">The `-=` operator first subtracts the value of the expression (on the right-hand side of the operator) from the value of the variable or property (on the left-hand side of the operator).</span></span> <span data-ttu-id="ed71d-115">然后，运算符将该操作的结果赋给变量或属性。</span><span class="sxs-lookup"><span data-stu-id="ed71d-115">The operator then assigns the result of that operation to the variable or property.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="ed71d-116">重载</span><span class="sxs-lookup"><span data-stu-id="ed71d-116">Overloading</span></span>  

 <span data-ttu-id="ed71d-117">[-Operator (Visual Basic)](subtraction-operator.md)可以 *重载*，这意味着当操作数具有该类或结构的类型时，该类或结构可以重新定义其行为。</span><span class="sxs-lookup"><span data-stu-id="ed71d-117">The [- Operator (Visual Basic)](subtraction-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="ed71d-118">重载 `-` 运算符会影响运算符的行为 `-=` 。</span><span class="sxs-lookup"><span data-stu-id="ed71d-118">Overloading the `-` operator affects the behavior of the `-=` operator.</span></span> <span data-ttu-id="ed71d-119">如果你的代码 `-=` 在重载的类或结构上使用 `-` ，请确保你了解其重新定义的行为。</span><span class="sxs-lookup"><span data-stu-id="ed71d-119">If your code uses `-=` on a class or structure that overloads `-`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="ed71d-120">有关详细信息，请参阅 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="ed71d-120">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed71d-121">示例</span><span class="sxs-lookup"><span data-stu-id="ed71d-121">Example</span></span>  

 <span data-ttu-id="ed71d-122">下面的示例使用 `-=` 运算符 `Integer` 从一个变量中减去另一个变量，并将结果赋给后一个变量。</span><span class="sxs-lookup"><span data-stu-id="ed71d-122">The following example uses the `-=` operator to subtract one `Integer` variable from another and assign the result to the latter variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="ed71d-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="ed71d-123">See also</span></span>

- [<span data-ttu-id="ed71d-124">-Operator (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="ed71d-124">- Operator (Visual Basic)</span></span>](subtraction-operator.md)
- [<span data-ttu-id="ed71d-125">赋值运算符</span><span class="sxs-lookup"><span data-stu-id="ed71d-125">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="ed71d-126">算术运算符</span><span class="sxs-lookup"><span data-stu-id="ed71d-126">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="ed71d-127">Visual Basic 中的运算符优先级</span><span class="sxs-lookup"><span data-stu-id="ed71d-127">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="ed71d-128">按功能列出的运算符</span><span class="sxs-lookup"><span data-stu-id="ed71d-128">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="ed71d-129">语句</span><span class="sxs-lookup"><span data-stu-id="ed71d-129">Statements</span></span>](../../programming-guide/language-features/statements.md)
