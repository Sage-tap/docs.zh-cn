---
description: '了解详细信息：如何：从属性获取值 (Visual Basic) '
title: 如何：从属性获取值
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
ms.openlocfilehash: 5626ad1a248c3bb51e0f80076628c8108e424186
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100427591"
---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a><span data-ttu-id="d2e23-103">如何：从属性获取值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d2e23-103">How to: Get a Value from a Property (Visual Basic)</span></span>

<span data-ttu-id="d2e23-104">通过在表达式中包含属性名称来检索属性的值。</span><span class="sxs-lookup"><span data-stu-id="d2e23-104">You retrieve a property's value by including the property name in an expression.</span></span>  
  
 <span data-ttu-id="d2e23-105">该属性的 `Get` 过程检索值，但不按名称显式调用它。</span><span class="sxs-lookup"><span data-stu-id="d2e23-105">The property's `Get` procedure retrieves the value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="d2e23-106">像使用变量一样使用属性。</span><span class="sxs-lookup"><span data-stu-id="d2e23-106">You use the property just as you would use a variable.</span></span> <span data-ttu-id="d2e23-107">Visual Basic 对属性的过程进行调用。</span><span class="sxs-lookup"><span data-stu-id="d2e23-107">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-retrieve-a-value-from-a-property"></a><span data-ttu-id="d2e23-108">从属性中检索值</span><span class="sxs-lookup"><span data-stu-id="d2e23-108">To retrieve a value from a property</span></span>  
  
1. <span data-ttu-id="d2e23-109">在表达式中使用属性名称的方式与使用变量名相同。</span><span class="sxs-lookup"><span data-stu-id="d2e23-109">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="d2e23-110">可以在可以使用变量或常量的任何位置使用属性。</span><span class="sxs-lookup"><span data-stu-id="d2e23-110">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="d2e23-111">- 或 -</span><span class="sxs-lookup"><span data-stu-id="d2e23-111">-or-</span></span>  
  
     <span data-ttu-id="d2e23-112">使用相等 (后面的属性名称 `=`) 在赋值语句中登录。</span><span class="sxs-lookup"><span data-stu-id="d2e23-112">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="d2e23-113">下面的示例读取 Visual Basic 属性的值 `Now` ，隐式调用其 `Get` 过程。</span><span class="sxs-lookup"><span data-stu-id="d2e23-113">The following example reads the value of the Visual Basic `Now` property, implicitly calling its `Get` procedure.</span></span>  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2. <span data-ttu-id="d2e23-114">如果属性采用参数，请在属性名称后面加上括号，以将参数列表括起来。</span><span class="sxs-lookup"><span data-stu-id="d2e23-114">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="d2e23-115">如果没有参数，则可以选择省略括号。</span><span class="sxs-lookup"><span data-stu-id="d2e23-115">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="d2e23-116">将参数置于括号中的参数列表内，用逗号分隔。</span><span class="sxs-lookup"><span data-stu-id="d2e23-116">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="d2e23-117">请确保以属性定义相应参数的相同顺序提供参数。</span><span class="sxs-lookup"><span data-stu-id="d2e23-117">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="d2e23-118">属性的值作为变量或常数加入表达式，或者将其存储在赋值语句左侧的变量或属性中。</span><span class="sxs-lookup"><span data-stu-id="d2e23-118">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2e23-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="d2e23-119">See also</span></span>

- [<span data-ttu-id="d2e23-120">过程</span><span class="sxs-lookup"><span data-stu-id="d2e23-120">Procedures</span></span>](./index.md)
- [<span data-ttu-id="d2e23-121">Property 过程</span><span class="sxs-lookup"><span data-stu-id="d2e23-121">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="d2e23-122">过程形参和实参</span><span class="sxs-lookup"><span data-stu-id="d2e23-122">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="d2e23-123">Property Statement</span><span class="sxs-lookup"><span data-stu-id="d2e23-123">Property Statement</span></span>](../../../language-reference/statements/property-statement.md)
- [<span data-ttu-id="d2e23-124">Visual Basic 中属性和变量的差异</span><span class="sxs-lookup"><span data-stu-id="d2e23-124">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="d2e23-125">如何：创建属性</span><span class="sxs-lookup"><span data-stu-id="d2e23-125">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="d2e23-126">如何：声明具有混合访问级别的属性</span><span class="sxs-lookup"><span data-stu-id="d2e23-126">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="d2e23-127">如何：调用 Property 过程</span><span class="sxs-lookup"><span data-stu-id="d2e23-127">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="d2e23-128">如何：在 Visual Basic 中声明和调用默认属性</span><span class="sxs-lookup"><span data-stu-id="d2e23-128">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="d2e23-129">如何：在属性中放置值</span><span class="sxs-lookup"><span data-stu-id="d2e23-129">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
