---
description: '了解详细信息：错误类型 (Visual Basic) '
title: 错误类型
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions, types
- errors [Visual Basic], types
- errors [Visual Basic], logic
- errors [Visual Basic], syntax
- logic errors [Visual Basic], Visual Basic
- run-time errors [Visual Basic], types of errors
- syntax errors [Visual Basic], Visual Basic
ms.assetid: 3048aabf-8c97-4e13-9150-853769cb5f6f
ms.openlocfilehash: cc4fce5e0ce77a4e402ba832fd6f4e36e6feed07
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100423766"
---
# <a name="error-types-visual-basic"></a><span data-ttu-id="86d91-103">错误类型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="86d91-103">Error Types (Visual Basic)</span></span>

<span data-ttu-id="86d91-104">在 Visual Basic 中，错误分为三个类别之一：语法错误、运行时错误和逻辑错误。</span><span class="sxs-lookup"><span data-stu-id="86d91-104">In Visual Basic, errors fall into one of three categories: syntax errors, run-time errors, and logic errors.</span></span>

## <a name="syntax-errors"></a><span data-ttu-id="86d91-105">语法错误</span><span class="sxs-lookup"><span data-stu-id="86d91-105">Syntax Errors</span></span>

 <span data-ttu-id="86d91-106">*语法错误* 是在编写代码时显示的错误。</span><span class="sxs-lookup"><span data-stu-id="86d91-106">*Syntax errors* are those that appear while you write code.</span></span> <span data-ttu-id="86d91-107">如果使用的是 Visual Studio，则 Visual Basic 在 **代码编辑器** 窗口中键入代码时检查代码，并在出现错误时发出警报，如错误拼写错误或错误地使用语言元素。</span><span class="sxs-lookup"><span data-stu-id="86d91-107">If you're using Visual Studio, Visual Basic checks your code as you type it in the **Code Editor** window and alerts you if you make a mistake, such as misspelling a word or using a language element improperly.</span></span> <span data-ttu-id="86d91-108">如果从命令行进行编译，Visual Basic 将显示编译器错误，其中包含有关语法错误的信息。</span><span class="sxs-lookup"><span data-stu-id="86d91-108">If you compile from the command line, Visual Basic displays a compiler error with information about the syntax error.</span></span> <span data-ttu-id="86d91-109">语法错误是最常见的错误类型。</span><span class="sxs-lookup"><span data-stu-id="86d91-109">Syntax errors are the most common type of errors.</span></span> <span data-ttu-id="86d91-110">一旦出现，就可以在编码环境中轻松地对其进行修复。</span><span class="sxs-lookup"><span data-stu-id="86d91-110">You can fix them easily in the coding environment as soon as they occur.</span></span>

> [!NOTE]
> <span data-ttu-id="86d91-111">`Option Explicit`语句是避免语法错误的一种方法。</span><span class="sxs-lookup"><span data-stu-id="86d91-111">The `Option Explicit` statement is one means of avoiding syntax errors.</span></span> <span data-ttu-id="86d91-112">它强制您事先声明要在应用程序中使用的所有变量。</span><span class="sxs-lookup"><span data-stu-id="86d91-112">It forces you to declare, in advance, all the variables to be used in the application.</span></span> <span data-ttu-id="86d91-113">因此，当在代码中使用这些变量时，会立即捕获任何排字错误，并可修复这些错误。</span><span class="sxs-lookup"><span data-stu-id="86d91-113">Therefore, when those variables are used in the code, any typographic errors are caught immediately and can be fixed.</span></span>

## <a name="run-time-errors"></a><span data-ttu-id="86d91-114">Run-Time 错误</span><span class="sxs-lookup"><span data-stu-id="86d91-114">Run-Time Errors</span></span>

 <span data-ttu-id="86d91-115">*运行时错误* 是指仅在编译和运行代码后显示的错误。</span><span class="sxs-lookup"><span data-stu-id="86d91-115">*Run-time errors* are those that appear only after you compile and run your code.</span></span> <span data-ttu-id="86d91-116">它们涉及的代码可能看起来是正确的，因为它没有语法错误，但不会执行。</span><span class="sxs-lookup"><span data-stu-id="86d91-116">These involve code that may appear to be correct in that it has no syntax errors, but that will not execute.</span></span> <span data-ttu-id="86d91-117">例如，你可能会正确编写一行代码来打开文件。</span><span class="sxs-lookup"><span data-stu-id="86d91-117">For example, you might correctly write a line of code to open a file.</span></span> <span data-ttu-id="86d91-118">但是，如果该文件不存在，应用程序将无法打开该文件，并将引发异常。</span><span class="sxs-lookup"><span data-stu-id="86d91-118">But if the file does not exist, the application cannot open the file, and it throws an exception.</span></span> <span data-ttu-id="86d91-119">您可以通过重写错误的代码或使用 [异常处理](../../language-reference/statements/try-catch-finally-statement.md)来修复大多数运行时错误，然后重新编译并重新运行它。</span><span class="sxs-lookup"><span data-stu-id="86d91-119">You can fix most run-time errors by rewriting the faulty code or by using [exception handling](../../language-reference/statements/try-catch-finally-statement.md), and then recompiling and rerunning it.</span></span>
  
## <a name="logic-errors"></a><span data-ttu-id="86d91-120">逻辑错误</span><span class="sxs-lookup"><span data-stu-id="86d91-120">Logic Errors</span></span>

 <span data-ttu-id="86d91-121">*逻辑错误* 是指在应用程序使用后出现的错误。</span><span class="sxs-lookup"><span data-stu-id="86d91-121">*Logic errors* are those that appear once the application is in use.</span></span> <span data-ttu-id="86d91-122">它们最常见的是开发人员作出的假设，或者是不需要或意外的结果来响应用户操作。</span><span class="sxs-lookup"><span data-stu-id="86d91-122">They are most often faulty assumptions made by the developer, or unwanted or unexpected results in response to user actions.</span></span> <span data-ttu-id="86d91-123">例如，键入错误的键可能会为方法提供错误的信息，或者，如果不是这样，则您可能会假设始终向方法提供有效的值。</span><span class="sxs-lookup"><span data-stu-id="86d91-123">For example, a mistyped key might provide incorrect information to a method, or you may assume that a valid value is always supplied to a method when that is not the case.</span></span> <span data-ttu-id="86d91-124">尽管可以使用 [异常处理](../../language-reference/statements/try-catch-finally-statement.md) 来处理逻辑错误 (例如，通过测试参数是否为 `Nothing` 并引发 <xref:System.ArgumentNullException>) ，最常见的解决方法是更正逻辑中的错误并重新编译应用程序。</span><span class="sxs-lookup"><span data-stu-id="86d91-124">Although logic errors can be handled by using [exception handling](../../language-reference/statements/try-catch-finally-statement.md) (for example, by testing whether an argument is `Nothing` and throwing an <xref:System.ArgumentNullException>), most commonly they should be addressed by correcting the error in logic and recompiling the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="86d91-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="86d91-125">See also</span></span>

- [<span data-ttu-id="86d91-126">Try...Catch...Finally 语句</span><span class="sxs-lookup"><span data-stu-id="86d91-126">Try...Catch...Finally Statement</span></span>](../../language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="86d91-127">调试器基础知识</span><span class="sxs-lookup"><span data-stu-id="86d91-127">Debugger Basics</span></span>](/visualstudio/debugger/debugger-feature-tour)
