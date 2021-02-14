---
description: '了解有关详细信息，请参阅如何：在代码中中断和组合语句 (Visual Basic) '
title: 如何：在代码中拆分和合并语句
ms.date: 07/20/2015
f1_keywords:
- vb._
helpviewer_keywords:
- colons (:)
- line continuation
- _ line-continuation character
- ': line separator character'
- Visual Basic code, line breaks in
- Visual Basic code, line breaks
- Visual Basic code, line continuation
- long lines of code
- line terminator
- line-continuation sequence
- underscores [Visual Basic], in code
- statements [Visual Basic], line continuation in
- line breaks [Visual Basic], in code
- line-continuation character [Visual Basic]
- Visual Basic code, line continuation in
- statements [Visual Basic], line breaks in
ms.assetid: dea01dad-a8ac-484a-bb3a-8c45a1b1eccc
ms.openlocfilehash: 33a8b87171c4ee14e73ada564cff406637e96783
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475989"
---
# <a name="how-to-break-and-combine-statements-in-code-visual-basic"></a><span data-ttu-id="6f6ec-103">如何：在代码中拆分和合并语句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f6ec-103">How to: Break and Combine Statements in Code (Visual Basic)</span></span>

<span data-ttu-id="6f6ec-104">编写代码时，有时可能会创建需要在代码编辑器中水平滚动的冗长语句。</span><span class="sxs-lookup"><span data-stu-id="6f6ec-104">When writing your code, you might at times create lengthy statements that necessitate horizontal scrolling in the Code Editor.</span></span> <span data-ttu-id="6f6ec-105">尽管这不会影响你的代码的运行方式，但当你或其他人在监视器上显示的代码时，这会很难。</span><span class="sxs-lookup"><span data-stu-id="6f6ec-105">Although this doesn't affect the way your code runs, it makes it difficult for you or anyone else to read the code as it appears on the monitor.</span></span> <span data-ttu-id="6f6ec-106">在这种情况下，应考虑将单个长语句分解为多行。</span><span class="sxs-lookup"><span data-stu-id="6f6ec-106">In such cases, you should consider breaking the single long statement into several lines.</span></span>

## <a name="to-break-a-single-statement-into-multiple-lines"></a><span data-ttu-id="6f6ec-107">将单个语句分解为多行</span><span class="sxs-lookup"><span data-stu-id="6f6ec-107">To break a single statement into multiple lines</span></span>

<span data-ttu-id="6f6ec-108">在您想要换行的点使用行继续符（下划线 (`_`) ）。</span><span class="sxs-lookup"><span data-stu-id="6f6ec-108">Use the line-continuation character, which is an underscore (`_`), at the point at which you want the line to break.</span></span> <span data-ttu-id="6f6ec-109">下划线必须紧跟在空格后面，后面紧跟行终止符 (回车) 或从版本16.0 开始的 () 注释后跟回车符。</span><span class="sxs-lookup"><span data-stu-id="6f6ec-109">The underscore must be immediately preceded by a space and immediately followed by a line terminator (carriage return) or (starting with version 16.0) a comment followed by a carriage return.</span></span>

  > [!NOTE]
  > <span data-ttu-id="6f6ec-110">在某些情况下，如果省略行继续符，则 Visual Basic 编译器将在下一行代码中隐式地继续执行该语句。</span><span class="sxs-lookup"><span data-stu-id="6f6ec-110">In some cases, if you omit the line-continuation character, the Visual Basic compiler will implicitly continue the statement on the next line of code.</span></span> <span data-ttu-id="6f6ec-111">有关可以省略行继续符的语法元素的列表，请参阅 [语句](../language-features/statements.md)中的 "隐式行继续符"。</span><span class="sxs-lookup"><span data-stu-id="6f6ec-111">For a list of syntax elements for which you can omit the line-continuation character, see "Implicit Line Continuation" in [Statements](../language-features/statements.md).</span></span>

  <span data-ttu-id="6f6ec-112">在下面的示例中，语句分为四行，其中的行继续符用于终止除最后一行以外的所有行。</span><span class="sxs-lookup"><span data-stu-id="6f6ec-112">In the following example, the statement is broken into four lines with line-continuation characters terminating all but the last line.</span></span>

  [!code-vb[VbVbcnConventions#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#20)]

  <span data-ttu-id="6f6ec-113">使用此序列可以使代码更易于阅读，无论是联机还是打印。</span><span class="sxs-lookup"><span data-stu-id="6f6ec-113">Using this sequence makes your code easier to read, both online and when printed.</span></span>

  <span data-ttu-id="6f6ec-114">行继续符必须是行中的最后一个字符。</span><span class="sxs-lookup"><span data-stu-id="6f6ec-114">The line-continuation character must be the last character on a line.</span></span> <span data-ttu-id="6f6ec-115">你不能在同一行上将它与其他任何内容一起跟随。</span><span class="sxs-lookup"><span data-stu-id="6f6ec-115">You can't follow it with anything else on the same line.</span></span>

  <span data-ttu-id="6f6ec-116">存在一些限制，以使你可以使用行继续符;例如，不能在参数名中间使用。</span><span class="sxs-lookup"><span data-stu-id="6f6ec-116">Some limitations exist as to where you can use the line-continuation character; for example, you can't use it in the middle of an argument name.</span></span> <span data-ttu-id="6f6ec-117">您可以使用行继续符来破坏参数列表，但参数的各个名称必须保持不变。</span><span class="sxs-lookup"><span data-stu-id="6f6ec-117">You can break an argument list with the line-continuation character, but the individual names of the arguments must remain intact.</span></span>

  <span data-ttu-id="6f6ec-118">不能使用行继续符继续注释。</span><span class="sxs-lookup"><span data-stu-id="6f6ec-118">You can't continue a comment by using a line-continuation character.</span></span> <span data-ttu-id="6f6ec-119">编译器不会检查注释中的字符是否有特殊意义。</span><span class="sxs-lookup"><span data-stu-id="6f6ec-119">The compiler doesn't examine the characters in a comment for special meaning.</span></span> <span data-ttu-id="6f6ec-120">对于多行注释，请 `'` 在每行 () 重复注释符号。</span><span class="sxs-lookup"><span data-stu-id="6f6ec-120">For a multiple-line comment, repeat the comment symbol (`'`) on each line.</span></span>

 <span data-ttu-id="6f6ec-121">尽管建议方法将每个语句置于单独的行上，但 Visual Basic 也允许在同一行上放置多个语句。</span><span class="sxs-lookup"><span data-stu-id="6f6ec-121">Although placing each statement on a separate line is the recommended method, Visual Basic also allows you to place multiple statements on the same line.</span></span>

## <a name="to-place-multiple-statements-on-the-same-line"></a><span data-ttu-id="6f6ec-122">在同一行上放置多个语句</span><span class="sxs-lookup"><span data-stu-id="6f6ec-122">To place multiple statements on the same line</span></span>

<span data-ttu-id="6f6ec-123">使用冒号 () 分隔语句 `:` ，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="6f6ec-123">Separate the statements with a colon (`:`), as in the following example:</span></span>

  [!code-vb[VbVbcnConventions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#10)]

## <a name="see-also"></a><span data-ttu-id="6f6ec-124">请参阅</span><span class="sxs-lookup"><span data-stu-id="6f6ec-124">See also</span></span>

- [<span data-ttu-id="6f6ec-125">程序结构和代码约定</span><span class="sxs-lookup"><span data-stu-id="6f6ec-125">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)
- [<span data-ttu-id="6f6ec-126">语句</span><span class="sxs-lookup"><span data-stu-id="6f6ec-126">Statements</span></span>](../language-features/statements.md)
