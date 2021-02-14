---
description: '了解有关详细信息，请参阅如何：将参数传递给过程 (Visual Basic) '
title: 如何：将参数传递给过程
ms.date: 07/20/2015
helpviewer_keywords:
- arguments [Visual Basic], passing to procedures
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], calling
- argument passing [Visual Basic], procedures
ms.assetid: 08723588-3890-4ddc-8249-79e049e0f241
ms.openlocfilehash: e4dcdac19699c4b4b1f88327034a9e9d4364f040
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100434324"
---
# <a name="how-to-pass-arguments-to-a-procedure-visual-basic"></a><span data-ttu-id="2c16a-103">如何：将参数传递给过程 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2c16a-103">How to: Pass Arguments to a Procedure (Visual Basic)</span></span>

<span data-ttu-id="2c16a-104">调用过程时，请在括号中使用参数列表的过程名称。</span><span class="sxs-lookup"><span data-stu-id="2c16a-104">When you call a procedure, you follow the procedure name with an argument list in parentheses.</span></span> <span data-ttu-id="2c16a-105">提供与过程定义的每个必需参数相对应的参数，可选择为参数提供参数 `Optional` 。</span><span class="sxs-lookup"><span data-stu-id="2c16a-105">You supply an argument corresponding to every required parameter the procedure defines, and you can optionally supply arguments to the `Optional` parameters.</span></span> <span data-ttu-id="2c16a-106">如果未 `Optional` 在调用中提供参数，则必须包含一个逗号，以便在提供任何后续参数时将其位置标记到参数列表中。</span><span class="sxs-lookup"><span data-stu-id="2c16a-106">If you do not supply an `Optional` parameter in the call, you must include a comma to mark its place in the argument list if you are supplying any subsequent arguments.</span></span>  
  
 <span data-ttu-id="2c16a-107">如果要传递的参数的数据类型不同于其对应参数的参数（例如 `Byte` `String` ），则可以将类型检查开关 ([Option Strict 语句](../../../language-reference/statements/option-strict-statement.md)) 设置为 `Off` 。</span><span class="sxs-lookup"><span data-stu-id="2c16a-107">If you intend to pass an argument of a data type different from that of its corresponding parameter, such as `Byte` to `String`, you can set the type-checking switch ([Option Strict Statement](../../../language-reference/statements/option-strict-statement.md)) to `Off`.</span></span> <span data-ttu-id="2c16a-108">如果 `Option Strict` 为 `On` ，则必须使用扩大转换或显式转换关键字。</span><span class="sxs-lookup"><span data-stu-id="2c16a-108">If `Option Strict` is `On`, you must use either widening conversions or explicit conversion keywords.</span></span> <span data-ttu-id="2c16a-109">有关详细信息，请参阅 [扩大和收缩转换](../data-types/widening-and-narrowing-conversions.md) 和 [类型转换函数](../../../language-reference/functions/type-conversion-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="2c16a-109">For more information, see [Widening and Narrowing Conversions](../data-types/widening-and-narrowing-conversions.md) and [Type Conversion Functions](../../../language-reference/functions/type-conversion-functions.md).</span></span>  
  
 <span data-ttu-id="2c16a-110">有关详细信息，请参阅 [过程参数和参数](./procedure-parameters-and-arguments.md)。</span><span class="sxs-lookup"><span data-stu-id="2c16a-110">For more information, see [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md).</span></span>  
  
### <a name="to-pass-one-or-more-arguments-to-a-procedure"></a><span data-ttu-id="2c16a-111">将一个或多个自变量传递给过程</span><span class="sxs-lookup"><span data-stu-id="2c16a-111">To pass one or more arguments to a procedure</span></span>  
  
1. <span data-ttu-id="2c16a-112">在调用语句中，在过程名称后面加上括号。</span><span class="sxs-lookup"><span data-stu-id="2c16a-112">In the calling statement, follow the procedure name with parentheses.</span></span>  
  
2. <span data-ttu-id="2c16a-113">在括号内，放入参数列表。</span><span class="sxs-lookup"><span data-stu-id="2c16a-113">Inside the parentheses, put an argument list.</span></span> <span data-ttu-id="2c16a-114">为过程定义的每个必需参数包含一个参数，并使用逗号分隔参数。</span><span class="sxs-lookup"><span data-stu-id="2c16a-114">Include an argument for each required parameter the procedure defines, and separate the arguments with commas.</span></span>  
  
3. <span data-ttu-id="2c16a-115">请确保每个参数都是一个有效的表达式，该表达式的计算结果为可转换为相应参数的过程定义的类型的数据类型。</span><span class="sxs-lookup"><span data-stu-id="2c16a-115">Make sure each argument is a valid expression that evaluates to a data type convertible to the type the procedure defines for the corresponding parameter.</span></span>  
  
4. <span data-ttu-id="2c16a-116">如果将某个参数定义为 [可选](../../../language-reference/modifiers/optional.md)参数，则可以将其包含在自变量列表中，或将其省略。</span><span class="sxs-lookup"><span data-stu-id="2c16a-116">If a parameter is defined as [Optional](../../../language-reference/modifiers/optional.md), you can either include it in the argument list or omit it.</span></span> <span data-ttu-id="2c16a-117">如果省略该参数，则该过程将使用为该参数定义的默认值。</span><span class="sxs-lookup"><span data-stu-id="2c16a-117">If you omit it, the procedure uses the default value defined for that parameter.</span></span>  
  
5. <span data-ttu-id="2c16a-118">如果省略参数的自变量， `Optional` 并且参数列表中后面有另一个参数，则可以在参数列表中用额外的逗号标记省略参数的位置。</span><span class="sxs-lookup"><span data-stu-id="2c16a-118">If you omit an argument for an `Optional` parameter and there is another parameter after it in the parameter list, you can mark the place of the omitted argument by an extra comma in the argument list.</span></span>  
  
     <span data-ttu-id="2c16a-119">下面的示例调用 Visual Basic <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> 函数。</span><span class="sxs-lookup"><span data-stu-id="2c16a-119">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function.</span></span>  
  
     [!code-vb[VbVbcnProcedures#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#34)]  
  
     <span data-ttu-id="2c16a-120">前面的示例提供了必需的第一个参数，即要显示的消息字符串。</span><span class="sxs-lookup"><span data-stu-id="2c16a-120">The preceding example supplies the required first argument, which is the message string to be displayed.</span></span> <span data-ttu-id="2c16a-121">它省略了可选的第二个参数的参数，该参数指定要在消息框中显示的按钮。</span><span class="sxs-lookup"><span data-stu-id="2c16a-121">It omits an argument for the optional second parameter, which specifies the buttons to be displayed on the message box.</span></span> <span data-ttu-id="2c16a-122">由于调用不提供值，因此 `MsgBox` 将使用默认值，该默认值 `MsgBoxStyle.OKOnly` 仅显示 **"确定"** 按钮。</span><span class="sxs-lookup"><span data-stu-id="2c16a-122">Because the call does not supply a value, `MsgBox` uses the default value, `MsgBoxStyle.OKOnly`, which displays only an **OK** button.</span></span>  
  
     <span data-ttu-id="2c16a-123">自变量列表中的第二个逗号标记省略的第二个参数的位置，最后一个字符串传递给的可选第三个参数 `MsgBox` ，即要在标题栏中显示的文本。</span><span class="sxs-lookup"><span data-stu-id="2c16a-123">The second comma in the argument list marks the place of the omitted second argument, and the last string is passed to the optional third parameter of `MsgBox`, which is the text to be displayed in the title bar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c16a-124">请参阅</span><span class="sxs-lookup"><span data-stu-id="2c16a-124">See also</span></span>

- [<span data-ttu-id="2c16a-125">Sub 过程</span><span class="sxs-lookup"><span data-stu-id="2c16a-125">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="2c16a-126">Function 过程</span><span class="sxs-lookup"><span data-stu-id="2c16a-126">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="2c16a-127">Property 过程</span><span class="sxs-lookup"><span data-stu-id="2c16a-127">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="2c16a-128">运算符过程</span><span class="sxs-lookup"><span data-stu-id="2c16a-128">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="2c16a-129">如何：为过程定义参数</span><span class="sxs-lookup"><span data-stu-id="2c16a-129">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="2c16a-130">按值和按引用传递参数</span><span class="sxs-lookup"><span data-stu-id="2c16a-130">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="2c16a-131">递归过程</span><span class="sxs-lookup"><span data-stu-id="2c16a-131">Recursive Procedures</span></span>](./recursive-procedures.md)
- [<span data-ttu-id="2c16a-132">过程重载</span><span class="sxs-lookup"><span data-stu-id="2c16a-132">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="2c16a-133">对象和类</span><span class="sxs-lookup"><span data-stu-id="2c16a-133">Objects and Classes</span></span>](../objects-and-classes/index.md)
- [<span data-ttu-id="2c16a-134">面向对象的编程 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2c16a-134">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)
