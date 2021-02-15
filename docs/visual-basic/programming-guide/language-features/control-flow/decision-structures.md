---
description: '了解详细信息：决策结构 (Visual Basic) '
title: 决策结构
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- If statement [Visual Basic], decision structures
- If statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], decision structures
- decision structures [Visual Basic]
- conditional statements [Visual Basic], decision structures
ms.assetid: 2e2e0895-4483-442a-b17c-26aead751ec2
ms.openlocfilehash: 76b63d2cdc238ec5590d11a6a802f55866990a3a
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100480682"
---
# <a name="decision-structures-visual-basic"></a><span data-ttu-id="f0e46-103">决策结构 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f0e46-103">Decision Structures (Visual Basic)</span></span>

<span data-ttu-id="f0e46-104">Visual Basic 允许您测试条件并根据该测试的结果执行不同的操作。</span><span class="sxs-lookup"><span data-stu-id="f0e46-104">Visual Basic lets you test conditions and perform different operations depending on the results of that test.</span></span> <span data-ttu-id="f0e46-105">对于表达式的各个值，或者在执行一系列语句时生成的各种异常，可以测试条件是 true 还是 false。</span><span class="sxs-lookup"><span data-stu-id="f0e46-105">You can test for a condition being true or false, for various values of an expression, or for various exceptions generated when you execute a series of statements.</span></span>  
  
 <span data-ttu-id="f0e46-106">下图显示了一个决策结构，该结构用于测试条件是否为 true，并执行不同的操作，具体取决于它是 true 还是 false。</span><span class="sxs-lookup"><span data-stu-id="f0e46-106">The following illustration shows a decision structure that tests for a condition being true and takes different actions depending on whether it is true or false.</span></span>  
  
 ![If ... 的流程图Then .。。Else 构造。](./media/decision-structures/if-then-else-construction.gif)  
  
## <a name="ifthenelse-construction"></a><span data-ttu-id="f0e46-108">If .。。Then .。。Else 构造</span><span class="sxs-lookup"><span data-stu-id="f0e46-108">If...Then...Else Construction</span></span>  

 <span data-ttu-id="f0e46-109">`If...Then...Else` 构造使你可以测试一个或多个条件并根据每个条件运行一个或多个语句。</span><span class="sxs-lookup"><span data-stu-id="f0e46-109">`If...Then...Else` constructions let you test for one or more conditions and run one or more statements depending on each condition.</span></span> <span data-ttu-id="f0e46-110">可以通过以下方式测试条件并采取措施：</span><span class="sxs-lookup"><span data-stu-id="f0e46-110">You can test conditions and take actions in the following ways:</span></span>  
  
- <span data-ttu-id="f0e46-111">如果条件为，则运行一个或多个语句 `True`</span><span class="sxs-lookup"><span data-stu-id="f0e46-111">Run one or more statements if a condition is `True`</span></span>  
  
- <span data-ttu-id="f0e46-112">如果条件为，则运行一个或多个语句 `False`</span><span class="sxs-lookup"><span data-stu-id="f0e46-112">Run one or more statements if a condition is `False`</span></span>  
  
- <span data-ttu-id="f0e46-113">如果条件为，则运行某些语句; 如果条件为，则运行 `True` 其他语句 `False`</span><span class="sxs-lookup"><span data-stu-id="f0e46-113">Run some statements if a condition is `True` and others if it is `False`</span></span>  
  
- <span data-ttu-id="f0e46-114">如果先前的条件为，则测试其他条件 `False`</span><span class="sxs-lookup"><span data-stu-id="f0e46-114">Test an additional condition if a prior condition is `False`</span></span>  
  
 <span data-ttu-id="f0e46-115">提供所有这些可能的控制结构是 [If .。。Then .。。Else 语句](../../../language-reference/statements/if-then-else-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="f0e46-115">The control structure that offers all these possibilities is the [If...Then...Else Statement](../../../language-reference/statements/if-then-else-statement.md).</span></span> <span data-ttu-id="f0e46-116">如果仅有一个测试和一个语句要运行，则可以使用单行版本。</span><span class="sxs-lookup"><span data-stu-id="f0e46-116">You can use a single-line version if you have just one test and one statement to run.</span></span> <span data-ttu-id="f0e46-117">如果有更复杂的条件和操作集，则可以使用多行版本。</span><span class="sxs-lookup"><span data-stu-id="f0e46-117">If you have a more complex set of conditions and actions, you can use the multiple-line version.</span></span>  
  
## <a name="selectcase-construction"></a><span data-ttu-id="f0e46-118">选择 .。。案例构造</span><span class="sxs-lookup"><span data-stu-id="f0e46-118">Select...Case Construction</span></span>  

 <span data-ttu-id="f0e46-119">使用 `Select...Case` 构造，可以计算一次表达式，并基于不同的可能值运行不同的语句集。</span><span class="sxs-lookup"><span data-stu-id="f0e46-119">The `Select...Case` construction lets you evaluate an expression one time and run different sets of statements based on different possible values.</span></span> <span data-ttu-id="f0e46-120">有关详细信息，请参阅 [Select .。。Case 语句](../../../language-reference/statements/select-case-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="f0e46-120">For more information, see [Select...Case Statement](../../../language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="trycatchfinally-construction"></a><span data-ttu-id="f0e46-121">尝试 .。。Catch .。。最终构造</span><span class="sxs-lookup"><span data-stu-id="f0e46-121">Try...Catch...Finally Construction</span></span>  

 <span data-ttu-id="f0e46-122">`Try...Catch...Finally` 构造使你可以在某个环境下运行一组语句，如果你的任何一个语句导致异常，该环境将保留控制权。</span><span class="sxs-lookup"><span data-stu-id="f0e46-122">`Try...Catch...Finally` constructions let you run a set of statements under an environment that retains control if any one of your statements causes an exception.</span></span> <span data-ttu-id="f0e46-123">对于不同的异常，可以执行不同的操作。</span><span class="sxs-lookup"><span data-stu-id="f0e46-123">You can take different actions for different exceptions.</span></span> <span data-ttu-id="f0e46-124">您可以选择指定在退出整个构造之前运行的代码块 `Try...Catch...Finally` ，而不管发生了什么情况。</span><span class="sxs-lookup"><span data-stu-id="f0e46-124">You can optionally specify a block of code that runs before you exit the whole `Try...Catch...Finally` construction, regardless of what occurs.</span></span> <span data-ttu-id="f0e46-125">有关详细信息，请参阅 [Try...Catch...Finally 语句](../../../language-reference/statements/try-catch-finally-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="f0e46-125">For more information, see [Try...Catch...Finally Statement](../../../language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f0e46-126">对于许多控制结构，当您单击某个关键字时，将突出显示该结构中的所有关键字。</span><span class="sxs-lookup"><span data-stu-id="f0e46-126">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="f0e46-127">例如，单击构造时，将 `If` `If...Then...Else` `If` `Then` `ElseIf` `Else` `End If` 突出显示构造中的、、、和的所有实例。</span><span class="sxs-lookup"><span data-stu-id="f0e46-127">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="f0e46-128">若要移动到下一个或上一个突出显示的关键字，请按 CTRL + SHIFT + 向下键或 CTRL + SHIFT + 向上键。</span><span class="sxs-lookup"><span data-stu-id="f0e46-128">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0e46-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="f0e46-129">See also</span></span>

- [<span data-ttu-id="f0e46-130">控制流</span><span class="sxs-lookup"><span data-stu-id="f0e46-130">Control Flow</span></span>](index.md)
- [<span data-ttu-id="f0e46-131">循环结构</span><span class="sxs-lookup"><span data-stu-id="f0e46-131">Loop Structures</span></span>](loop-structures.md)
- [<span data-ttu-id="f0e46-132">其他控件结构</span><span class="sxs-lookup"><span data-stu-id="f0e46-132">Other Control Structures</span></span>](other-control-structures.md)
- [<span data-ttu-id="f0e46-133">嵌套的控件结构</span><span class="sxs-lookup"><span data-stu-id="f0e46-133">Nested Control Structures</span></span>](nested-control-structures.md)
- [<span data-ttu-id="f0e46-134">If 运算符</span><span class="sxs-lookup"><span data-stu-id="f0e46-134">If Operator</span></span>](../../../language-reference/operators/if-operator.md)
