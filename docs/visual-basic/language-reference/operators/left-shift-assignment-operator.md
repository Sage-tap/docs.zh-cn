---
description: '了解详细信息：  <<= 运算符 (Visual Basic) '
title: <<= 运算符
ms.date: 07/20/2015
f1_keywords:
- vb.<<=
helpviewer_keywords:
- operator <<=
- assignment statements [Visual Basic], compound
- <<= operator [Visual Basic]
- statements [Visual Basic], compound assignment
- operator<<=
- compound assignment statements [Visual Basic]
ms.assetid: 8ad26613-faff-4e2f-89ee-63feee33bfda
ms.openlocfilehash: 40d0b69c3af672383230db5beadbcd3f3391db7f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665635"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="3cb98-103">\<\<= 运算符 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="3cb98-103">\<\<= Operator (Visual Basic)</span></span>

<span data-ttu-id="3cb98-104">对变量或属性的值执行算术左移位，并将结果赋回变量或属性。</span><span class="sxs-lookup"><span data-stu-id="3cb98-104">Performs an arithmetic left shift on the value of a variable or property and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cb98-105">语法</span><span class="sxs-lookup"><span data-stu-id="3cb98-105">Syntax</span></span>  
  
```vb  
variableorproperty <<= amount  
```  
  
## <a name="parts"></a><span data-ttu-id="3cb98-106">组成部分</span><span class="sxs-lookup"><span data-stu-id="3cb98-106">Parts</span></span>  

 `variableorproperty`  
 <span data-ttu-id="3cb98-107">必需。</span><span class="sxs-lookup"><span data-stu-id="3cb98-107">Required.</span></span> <span data-ttu-id="3cb98-108">整数类型的变量或属性 (`SByte` 、、、、、、 `Byte` `Short` `UShort` `Integer` `UInteger` `Long` 或 `ULong`) 。</span><span class="sxs-lookup"><span data-stu-id="3cb98-108">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="3cb98-109">必需。</span><span class="sxs-lookup"><span data-stu-id="3cb98-109">Required.</span></span> <span data-ttu-id="3cb98-110">扩大到的数据类型的数值表达式 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="3cb98-110">Numeric expression of a data type that widens to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3cb98-111">备注</span><span class="sxs-lookup"><span data-stu-id="3cb98-111">Remarks</span></span>  

 <span data-ttu-id="3cb98-112">运算符左侧的元素 `<<=` 可以是简单的标量变量、属性或数组的元素。</span><span class="sxs-lookup"><span data-stu-id="3cb98-112">The element on the left side of the `<<=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="3cb98-113">变量或属性不能是 [只读](../modifiers/readonly.md)的。</span><span class="sxs-lookup"><span data-stu-id="3cb98-113">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="3cb98-114">`<<=`运算符首先对变量或属性的值执行算术左移位运算。</span><span class="sxs-lookup"><span data-stu-id="3cb98-114">The `<<=` operator first performs an arithmetic left shift on the value of the variable or property.</span></span> <span data-ttu-id="3cb98-115">然后，运算符将该操作的结果赋给该变量或属性。</span><span class="sxs-lookup"><span data-stu-id="3cb98-115">The operator then assigns the result of that operation back to that variable or property.</span></span>  
  
 <span data-ttu-id="3cb98-116">算术移位不是循环的，这意味着，不会在另一端重新引入结果的末尾以外的位。</span><span class="sxs-lookup"><span data-stu-id="3cb98-116">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="3cb98-117">在算术左移位中，将丢弃超出结果数据类型范围的位，并将在右侧空出的位位置设置为零。</span><span class="sxs-lookup"><span data-stu-id="3cb98-117">In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="3cb98-118">重载</span><span class="sxs-lookup"><span data-stu-id="3cb98-118">Overloading</span></span>  

 <span data-ttu-id="3cb98-119">可以 *重载* [<< 运算符](left-shift-operator.md)，这意味着当操作数具有该类或结构的类型时，该类或结构可以重新定义其行为。</span><span class="sxs-lookup"><span data-stu-id="3cb98-119">The [<< Operator](left-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="3cb98-120">重载 `<<` 运算符会影响运算符的行为 `<<=` 。</span><span class="sxs-lookup"><span data-stu-id="3cb98-120">Overloading the `<<` operator affects the behavior of the `<<=` operator.</span></span> <span data-ttu-id="3cb98-121">如果你的代码 `<<=` 在重载的类或结构上使用 `<<` ，请确保你了解其重新定义的行为。</span><span class="sxs-lookup"><span data-stu-id="3cb98-121">If your code uses `<<=` on a class or structure that overloads `<<`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="3cb98-122">有关详细信息，请参阅 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="3cb98-122">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3cb98-123">示例</span><span class="sxs-lookup"><span data-stu-id="3cb98-123">Example</span></span>  

 <span data-ttu-id="3cb98-124">下面的示例使用 `<<=` 运算符将变量的位模式向左移动 `Integer` 指定的量，并将结果赋给该变量。</span><span class="sxs-lookup"><span data-stu-id="3cb98-124">The following example uses the `<<=` operator to shift the bit pattern of an `Integer` variable left by the specified amount and assign the result to the variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#13)]  
  
## <a name="see-also"></a><span data-ttu-id="3cb98-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="3cb98-125">See also</span></span>

- [<span data-ttu-id="3cb98-126"><< 运算符</span><span class="sxs-lookup"><span data-stu-id="3cb98-126"><< Operator</span></span>](left-shift-operator.md)
- [<span data-ttu-id="3cb98-127">赋值运算符</span><span class="sxs-lookup"><span data-stu-id="3cb98-127">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="3cb98-128">移位运算符</span><span class="sxs-lookup"><span data-stu-id="3cb98-128">Bit Shift Operators</span></span>](bit-shift-operators.md)
- [<span data-ttu-id="3cb98-129">Visual Basic 中的运算符优先级</span><span class="sxs-lookup"><span data-stu-id="3cb98-129">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="3cb98-130">按功能列出的运算符</span><span class="sxs-lookup"><span data-stu-id="3cb98-130">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="3cb98-131">语句</span><span class="sxs-lookup"><span data-stu-id="3cb98-131">Statements</span></span>](../../programming-guide/language-features/statements.md)
