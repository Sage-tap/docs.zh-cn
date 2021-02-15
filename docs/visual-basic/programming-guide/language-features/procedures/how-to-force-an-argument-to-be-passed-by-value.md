---
description: '了解有关详细信息，请参阅如何：强制通过值传递参数 (Visual Basic) '
title: 如何：强制通过值传递参数
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures [Visual Basic], calling
- arguments [Visual Basic], in parentheses
- procedure arguments [Visual Basic], in parentheses
- arguments [Visual Basic], changing value
ms.assetid: 77b4f2d2-1055-4c2f-a521-874d1db86946
ms.openlocfilehash: 471ddbf8993ad671dc4285729a11f5b17a5b19dc
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475417"
---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a><span data-ttu-id="97d68-103">如何：强制通过值传递参数 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="97d68-103">How to: Force an Argument to Be Passed by Value (Visual Basic)</span></span>

<span data-ttu-id="97d68-104">过程声明确定传递机制。</span><span class="sxs-lookup"><span data-stu-id="97d68-104">The procedure declaration determines the passing mechanism.</span></span> <span data-ttu-id="97d68-105">如果参数声明为 [ByRef](../../../language-reference/modifiers/byref.md)，则 Visual Basic 要求按引用传递相应的参数。</span><span class="sxs-lookup"><span data-stu-id="97d68-105">If a parameter is declared [ByRef](../../../language-reference/modifiers/byref.md), Visual Basic expects to pass the corresponding argument by reference.</span></span> <span data-ttu-id="97d68-106">这使过程可以更改调用代码中参数的基础编程元素的值。</span><span class="sxs-lookup"><span data-stu-id="97d68-106">This allows the procedure to change the value of the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="97d68-107">如果要针对此类更改保护基础元素，则可以 `ByRef` 通过将参数名称括在括号中来覆盖过程调用中的传递机制。</span><span class="sxs-lookup"><span data-stu-id="97d68-107">If you wish to protect the underlying element against such change, you can override the `ByRef` passing mechanism in the procedure call by enclosing the argument name in parentheses.</span></span> <span data-ttu-id="97d68-108">除了在调用中包含参数列表的括号外，还需要用到这些括号。</span><span class="sxs-lookup"><span data-stu-id="97d68-108">These parentheses are in addition to the parentheses enclosing the argument list in the call.</span></span>  
  
 <span data-ttu-id="97d68-109">调用代码无法重写 [ByVal](../../../language-reference/modifiers/byval.md) 机制。</span><span class="sxs-lookup"><span data-stu-id="97d68-109">The calling code cannot override a [ByVal](../../../language-reference/modifiers/byval.md) mechanism.</span></span>  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a><span data-ttu-id="97d68-110">强制按值传递参数</span><span class="sxs-lookup"><span data-stu-id="97d68-110">To force an argument to be passed by value</span></span>  
  
- <span data-ttu-id="97d68-111">如果在过程中声明了相应的参数 `ByVal` ，则无需执行任何其他步骤。</span><span class="sxs-lookup"><span data-stu-id="97d68-111">If the corresponding parameter is declared `ByVal` in the procedure, you do not need to take any additional steps.</span></span> <span data-ttu-id="97d68-112">Visual Basic 已经要求按值传递参数。</span><span class="sxs-lookup"><span data-stu-id="97d68-112">Visual Basic already expects to pass the argument by value.</span></span>  
  
- <span data-ttu-id="97d68-113">如果在过程中声明了相应的参数 `ByRef` ，请在过程调用中将参数括在括号中。</span><span class="sxs-lookup"><span data-stu-id="97d68-113">If the corresponding parameter is declared `ByRef` in the procedure, enclose the argument in parentheses in the procedure call.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97d68-114">示例</span><span class="sxs-lookup"><span data-stu-id="97d68-114">Example</span></span>  

 <span data-ttu-id="97d68-115">下面的示例重写 `ByRef` 参数声明。</span><span class="sxs-lookup"><span data-stu-id="97d68-115">The following example overrides a `ByRef` parameter declaration.</span></span> <span data-ttu-id="97d68-116">在强制的调用中 `ByVal` ，请注意两个级别的括号。</span><span class="sxs-lookup"><span data-stu-id="97d68-116">In the call that forces `ByVal`, note the two levels of parentheses.</span></span>  
  
 [!code-vb[VbVbcnProcedures#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#39)]  
  
 [!code-vb[VbVbcnProcedures#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#40)]  
  
 <span data-ttu-id="97d68-117">如果 `str` 将括在参数列表内的额外括号中，则该 `setNewString` 过程将无法在调用代码中更改其值，并 `MsgBox` 显示 "如果传递了 ByVal，则无法替换"。</span><span class="sxs-lookup"><span data-stu-id="97d68-117">When `str` is enclosed in extra parentheses within the argument list, the `setNewString` procedure cannot change its value in the calling code, and `MsgBox` displays "Cannot be replaced if passed ByVal".</span></span> <span data-ttu-id="97d68-118">当不 `str` 用多余的括号括起来时，该过程可以更改它并 `MsgBox` 显示 "这是 inString 参数的新值"。</span><span class="sxs-lookup"><span data-stu-id="97d68-118">When `str` is not enclosed in extra parentheses, the procedure can change it, and `MsgBox` displays "This is a new value for the inString argument."</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="97d68-119">编译代码</span><span class="sxs-lookup"><span data-stu-id="97d68-119">Compile the code</span></span>  

 <span data-ttu-id="97d68-120">通过引用传递变量时，必须使用 `ByRef` 关键字来指定此机制。</span><span class="sxs-lookup"><span data-stu-id="97d68-120">When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.</span></span>  
  
 <span data-ttu-id="97d68-121">Visual Basic 中的默认值是按值传递参数。</span><span class="sxs-lookup"><span data-stu-id="97d68-121">The default in Visual Basic is to pass arguments by value.</span></span> <span data-ttu-id="97d68-122">但是，将 [ByVal](../../../language-reference/modifiers/byval.md) 或 [ByRef](../../../language-reference/modifiers/byref.md) 关键字用于每个声明的参数是一种好的编程做法。</span><span class="sxs-lookup"><span data-stu-id="97d68-122">However, it is good programming practice to include either the [ByVal](../../../language-reference/modifiers/byval.md) or [ByRef](../../../language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="97d68-123">这使代码更易于阅读。</span><span class="sxs-lookup"><span data-stu-id="97d68-123">This makes your code easier to read.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="97d68-124">可靠编程</span><span class="sxs-lookup"><span data-stu-id="97d68-124">Robust Programming</span></span>  

 <span data-ttu-id="97d68-125">如果过程声明了参数 [ByRef](../../../language-reference/modifiers/byref.md)，代码的正确执行可能取决于是否能够更改调用代码中的基础元素。</span><span class="sxs-lookup"><span data-stu-id="97d68-125">If a procedure declares a parameter [ByRef](../../../language-reference/modifiers/byref.md), the correct execution of the code might depend on being able to change the underlying element in the calling code.</span></span> <span data-ttu-id="97d68-126">如果调用代码通过将参数括在括号中来重写此调用机制，或者如果传递了不可修改参数，则该过程不能更改基础元素。</span><span class="sxs-lookup"><span data-stu-id="97d68-126">If the calling code overrides this calling mechanism by enclosing the argument in parentheses, or if it passes a nonmodifiable argument, the procedure cannot change the underlying element.</span></span> <span data-ttu-id="97d68-127">这可能会在调用代码中产生意外结果。</span><span class="sxs-lookup"><span data-stu-id="97d68-127">This might produce unexpected results in the calling code.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="97d68-128">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="97d68-128">.NET Framework Security</span></span>  

 <span data-ttu-id="97d68-129">允许过程更改调用代码中参数的基础值始终存在潜在风险。</span><span class="sxs-lookup"><span data-stu-id="97d68-129">There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="97d68-130">请确保此值已更改，并在使用之前对其进行检查以确保其有效性。</span><span class="sxs-lookup"><span data-stu-id="97d68-130">Make sure you expect this value to be changed, and be prepared to check it for validity before using it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97d68-131">请参阅</span><span class="sxs-lookup"><span data-stu-id="97d68-131">See also</span></span>

- [<span data-ttu-id="97d68-132">过程</span><span class="sxs-lookup"><span data-stu-id="97d68-132">Procedures</span></span>](./index.md)
- [<span data-ttu-id="97d68-133">过程形参和实参</span><span class="sxs-lookup"><span data-stu-id="97d68-133">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="97d68-134">如何：将参数传递给过程</span><span class="sxs-lookup"><span data-stu-id="97d68-134">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="97d68-135">按值和按引用传递参数</span><span class="sxs-lookup"><span data-stu-id="97d68-135">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="97d68-136">可修改和不可修改参数之间的差异</span><span class="sxs-lookup"><span data-stu-id="97d68-136">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [<span data-ttu-id="97d68-137">通过值传递参数和通过引用传递参数之间的差异</span><span class="sxs-lookup"><span data-stu-id="97d68-137">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="97d68-138">如何：更改过程参数的值</span><span class="sxs-lookup"><span data-stu-id="97d68-138">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)
- [<span data-ttu-id="97d68-139">如何：防止过程参数的值被更改</span><span class="sxs-lookup"><span data-stu-id="97d68-139">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="97d68-140">按位置和按名称传递自变量</span><span class="sxs-lookup"><span data-stu-id="97d68-140">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="97d68-141">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="97d68-141">Value Types and Reference Types</span></span>](../data-types/value-types-and-reference-types.md)
