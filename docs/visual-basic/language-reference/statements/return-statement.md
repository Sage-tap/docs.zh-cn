---
description: '详细了解： Return 语句 (Visual Basic) '
title: Return 语句
ms.date: 07/20/2015
f1_keywords:
- vb.Return
helpviewer_keywords:
- Return statement [Visual Basic], syntax
- control flow [Visual Basic], returning control to expressions
- Return statement [Visual Basic]
- expressions [Visual Basic], returning control to
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
ms.openlocfilehash: 62086090ede7e634b09d3edc3dc42feb28d15793
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741193"
---
# <a name="return-statement-visual-basic"></a><span data-ttu-id="b0d98-103">Return 语句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b0d98-103">Return Statement (Visual Basic)</span></span>

<span data-ttu-id="b0d98-104">将控件返回到调用 `Function` 、 `Sub` 、 `Get` 、 `Set` 或 `Operator` 过程的代码。</span><span class="sxs-lookup"><span data-stu-id="b0d98-104">Returns control to the code that called a `Function`, `Sub`, `Get`, `Set`, or `Operator` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0d98-105">语法</span><span class="sxs-lookup"><span data-stu-id="b0d98-105">Syntax</span></span>  
  
```vb  
Return  
' -or-  
Return expression  
```  
  
## <a name="part"></a><span data-ttu-id="b0d98-106">组成部分</span><span class="sxs-lookup"><span data-stu-id="b0d98-106">Part</span></span>  

 `expression`  
 <span data-ttu-id="b0d98-107">在 `Function` 、或过程中是必需的 `Get` `Operator` 。</span><span class="sxs-lookup"><span data-stu-id="b0d98-107">Required in a `Function`, `Get`, or `Operator` procedure.</span></span> <span data-ttu-id="b0d98-108">表示要返回到调用代码的值的表达式。</span><span class="sxs-lookup"><span data-stu-id="b0d98-108">Expression that represents the value to be returned to the calling code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0d98-109">备注</span><span class="sxs-lookup"><span data-stu-id="b0d98-109">Remarks</span></span>  

 <span data-ttu-id="b0d98-110">在 `Sub` 或 `Set` 过程中， `Return` 语句等效于 `Exit Sub` 或 `Exit Property` 语句， `expression` 不能提供。</span><span class="sxs-lookup"><span data-stu-id="b0d98-110">In a `Sub` or `Set` procedure, the `Return` statement is equivalent to an `Exit Sub` or `Exit Property` statement, and `expression` must not be supplied.</span></span>  
  
 <span data-ttu-id="b0d98-111">在 `Function` 、 `Get` 或过程中 `Operator` ， `Return` 语句必须包含 `expression` ，并且 `expression` 必须计算为可转换为过程返回类型的数据类型。</span><span class="sxs-lookup"><span data-stu-id="b0d98-111">In a `Function`, `Get`, or `Operator` procedure, the `Return` statement must include `expression`, and `expression` must evaluate to a data type that is convertible to the return type of the procedure.</span></span> <span data-ttu-id="b0d98-112">在 `Function` 或 `Get` 过程中，您还可以选择将表达式分配给过程名称以用作返回值，然后执行 `Exit Function` 或 `Exit Property` 语句。</span><span class="sxs-lookup"><span data-stu-id="b0d98-112">In a `Function` or `Get` procedure, you also have the alternative of assigning an expression to the procedure name to serve as the return value, and then executing an `Exit Function` or `Exit Property` statement.</span></span> <span data-ttu-id="b0d98-113">在 `Operator` 过程中，必须使用 `Return expression` 。</span><span class="sxs-lookup"><span data-stu-id="b0d98-113">In an `Operator` procedure, you must use `Return expression`.</span></span>  
  
 <span data-ttu-id="b0d98-114">可以 `Return` 在同一个过程中包含任意多个语句。</span><span class="sxs-lookup"><span data-stu-id="b0d98-114">You can include as many `Return` statements as appropriate in the same procedure.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b0d98-115">块中的代码在 `Finally` `Return` 遇到或块中的语句 `Try` 之后 `Catch` 、但在执行该语句之前运行 `Return` 。</span><span class="sxs-lookup"><span data-stu-id="b0d98-115">The code in a `Finally` block runs after a `Return` statement in a `Try` or `Catch` block is encountered, but before that `Return` statement executes.</span></span> <span data-ttu-id="b0d98-116">`Return`语句不能包含在块中 `Finally` 。</span><span class="sxs-lookup"><span data-stu-id="b0d98-116">A `Return` statement cannot be included in a `Finally` block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0d98-117">示例</span><span class="sxs-lookup"><span data-stu-id="b0d98-117">Example</span></span>  

 <span data-ttu-id="b0d98-118">下面的示例多次使用 `Return` 语句，以便在过程不需要执行任何其他操作时返回到调用代码。</span><span class="sxs-lookup"><span data-stu-id="b0d98-118">The following example uses the `Return` statement several times to return to the calling code when the procedure does not have to do anything else.</span></span>  
  
 [!code-vb[VbVbalrStatements#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#53)]  
  
## <a name="see-also"></a><span data-ttu-id="b0d98-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="b0d98-119">See also</span></span>

- [<span data-ttu-id="b0d98-120">Function 语句</span><span class="sxs-lookup"><span data-stu-id="b0d98-120">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="b0d98-121">Sub 语句</span><span class="sxs-lookup"><span data-stu-id="b0d98-121">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="b0d98-122">Get 语句</span><span class="sxs-lookup"><span data-stu-id="b0d98-122">Get Statement</span></span>](get-statement.md)
- [<span data-ttu-id="b0d98-123">Set 语句</span><span class="sxs-lookup"><span data-stu-id="b0d98-123">Set Statement</span></span>](set-statement.md)
- [<span data-ttu-id="b0d98-124">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="b0d98-124">Operator Statement</span></span>](operator-statement.md)
- [<span data-ttu-id="b0d98-125">Property Statement</span><span class="sxs-lookup"><span data-stu-id="b0d98-125">Property Statement</span></span>](property-statement.md)
- [<span data-ttu-id="b0d98-126">Exit 语句</span><span class="sxs-lookup"><span data-stu-id="b0d98-126">Exit Statement</span></span>](exit-statement.md)
- [<span data-ttu-id="b0d98-127">Try...Catch...Finally 语句</span><span class="sxs-lookup"><span data-stu-id="b0d98-127">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
