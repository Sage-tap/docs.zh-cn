---
description: '详细了解： IsTrue Operator (Visual Basic) '
title: IsTrue 运算符
ms.date: 07/20/2015
f1_keywords:
- vb.istrue
helpviewer_keywords:
- IsTrue operator [Visual Basic]
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
ms.openlocfilehash: 50b618c888ce988da5241041fb2f728e0a581c70
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665648"
---
# <a name="istrue-operator-visual-basic"></a><span data-ttu-id="dbd3b-103">IsTrue 运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dbd3b-103">IsTrue Operator (Visual Basic)</span></span>

<span data-ttu-id="dbd3b-104">确定表达式是否为 `True` 。</span><span class="sxs-lookup"><span data-stu-id="dbd3b-104">Determines whether an expression is `True`.</span></span>  
  
 <span data-ttu-id="dbd3b-105">你不能 `IsTrue` 在代码中显式调用，但是 Visual Basic 编译器可以使用它来生成代码 from `OrElse` 子句。</span><span class="sxs-lookup"><span data-stu-id="dbd3b-105">You cannot call `IsTrue` explicitly in your code, but the Visual Basic compiler can use it to generate code from `OrElse` clauses.</span></span> <span data-ttu-id="dbd3b-106">如果定义类或结构，然后在子句中使用该类型的变量 `OrElse` ，则必须 `IsTrue` 在该类或结构上进行定义。</span><span class="sxs-lookup"><span data-stu-id="dbd3b-106">If you define a class or structure and then use a variable of that type in an `OrElse` clause, you must define `IsTrue` on that class or structure.</span></span>  
  
 <span data-ttu-id="dbd3b-107">编译器将 `IsTrue` 和运算符视为 `IsFalse` *匹配的对*。</span><span class="sxs-lookup"><span data-stu-id="dbd3b-107">The compiler considers the `IsTrue` and `IsFalse` operators as a *matched pair*.</span></span> <span data-ttu-id="dbd3b-108">这意味着，如果定义其中一个类型，则还必须定义另一个。</span><span class="sxs-lookup"><span data-stu-id="dbd3b-108">This means that if you define one of them, you must also define the other one.</span></span>  
  
## <a name="compiler-use-of-istrue"></a><span data-ttu-id="dbd3b-109">IsTrue 的编译器使用</span><span class="sxs-lookup"><span data-stu-id="dbd3b-109">Compiler Use of IsTrue</span></span>  

 <span data-ttu-id="dbd3b-110">定义了类或结构后，可以在 `For` 、 `If` 、 `Else If` 或 `While` 语句或 `When` 子句中使用该类型的变量。</span><span class="sxs-lookup"><span data-stu-id="dbd3b-110">When you have defined a class or structure, you can use a variable of that type in a `For`, `If`, `Else If`, or `While` statement, or in a `When` clause.</span></span> <span data-ttu-id="dbd3b-111">如果执行此操作，则编译器需要一个运算符，该运算符将您的类型转换为 `Boolean` 值，以便可以测试条件。</span><span class="sxs-lookup"><span data-stu-id="dbd3b-111">If you do this, the compiler requires an operator that converts your type into a `Boolean` value so it can test a condition.</span></span> <span data-ttu-id="dbd3b-112">它按以下顺序搜索合适的运算符：</span><span class="sxs-lookup"><span data-stu-id="dbd3b-112">It searches for a suitable operator in the following order:</span></span>  
  
1. <span data-ttu-id="dbd3b-113">从你的类或结构到的扩大转换运算符 `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="dbd3b-113">A widening conversion operator from your class or structure to `Boolean`.</span></span>  
  
2. <span data-ttu-id="dbd3b-114">从你的类或结构到的扩大转换运算符 `Boolean?` 。</span><span class="sxs-lookup"><span data-stu-id="dbd3b-114">A widening conversion operator from your class or structure to `Boolean?`.</span></span>  
  
3. <span data-ttu-id="dbd3b-115">`IsTrue`类或结构中的运算符。</span><span class="sxs-lookup"><span data-stu-id="dbd3b-115">The `IsTrue` operator on your class or structure.</span></span>  
  
4. <span data-ttu-id="dbd3b-116">到的收缩转换 `Boolean?` 不涉及从到的转换 `Boolean` `Boolean?` 。</span><span class="sxs-lookup"><span data-stu-id="dbd3b-116">A narrowing conversion to `Boolean?` that does not involve a conversion from `Boolean` to `Boolean?`.</span></span>  
  
5. <span data-ttu-id="dbd3b-117">类或结构中的收缩转换运算符 `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="dbd3b-117">A narrowing conversion operator from your class or structure to `Boolean`.</span></span>  
  
 <span data-ttu-id="dbd3b-118">如果未定义任何到 `Boolean` 或运算符的转换 `IsTrue` ，则编译器会发出错误消息。</span><span class="sxs-lookup"><span data-stu-id="dbd3b-118">If you have not defined any conversion to `Boolean` or an `IsTrue` operator, the compiler signals an error.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dbd3b-119">`IsTrue`运算符可以 *重载*，这意味着当类或结构的操作数具有该类或结构的类型时，该类或结构可以重新定义它的行为。</span><span class="sxs-lookup"><span data-stu-id="dbd3b-119">The `IsTrue` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="dbd3b-120">如果你的代码在该类或结构上使用此运算符，请确保了解其重新定义的行为。</span><span class="sxs-lookup"><span data-stu-id="dbd3b-120">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="dbd3b-121">有关详细信息，请参阅 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="dbd3b-121">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dbd3b-122">示例</span><span class="sxs-lookup"><span data-stu-id="dbd3b-122">Example</span></span>  

 <span data-ttu-id="dbd3b-123">下面的代码示例定义了包含和运算符定义的结构的轮廓 `IsFalse` `IsTrue` 。</span><span class="sxs-lookup"><span data-stu-id="dbd3b-123">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="dbd3b-124">请参阅</span><span class="sxs-lookup"><span data-stu-id="dbd3b-124">See also</span></span>

- [<span data-ttu-id="dbd3b-125">IsFalse 运算符</span><span class="sxs-lookup"><span data-stu-id="dbd3b-125">IsFalse Operator</span></span>](isfalse-operator.md)
- [<span data-ttu-id="dbd3b-126">如何：定义运算符</span><span class="sxs-lookup"><span data-stu-id="dbd3b-126">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="dbd3b-127">OrElse 运算符</span><span class="sxs-lookup"><span data-stu-id="dbd3b-127">OrElse Operator</span></span>](orelse-operator.md)
