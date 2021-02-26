---
description: try-finally - C# 参考
title: try-finally - C# 参考
ms.date: 07/20/2015
f1_keywords:
- finally
- finally_CSharpKeyword
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
ms.openlocfilehash: 03e5fa46cef6b30a0af15c113ec6b141a61bee47
ms.sourcegitcommit: 456b3cd82a87b453fa737b4661295070d1b6d684
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/17/2021
ms.locfileid: "100639411"
---
# <a name="try-finally-c-reference"></a><span data-ttu-id="1e72a-103">try-finally（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="1e72a-103">try-finally (C# Reference)</span></span>

<span data-ttu-id="1e72a-104">通过使用 `finally` 块，可以清除 [try](try-catch.md) 块中分配的任何资源，即使在 `try` 块中发生异常，也可以运行代码。</span><span class="sxs-lookup"><span data-stu-id="1e72a-104">By using a `finally` block, you can clean up any resources that are allocated in a [try](try-catch.md) block, and you can run code even if an exception occurs in the `try` block.</span></span> <span data-ttu-id="1e72a-105">通常情况下，`finally` 块的语句会在控件离开 `try` 语句时运行。</span><span class="sxs-lookup"><span data-stu-id="1e72a-105">Typically, the statements of a `finally` block run when control leaves a `try` statement.</span></span> <span data-ttu-id="1e72a-106">正常执行中，执行 `break`、`continue`、`goto` 或 `return` 语句，或者从 `try` 语句外传播异常都可能会导致发生控件转换。</span><span class="sxs-lookup"><span data-stu-id="1e72a-106">The transfer of control can occur as a result of normal execution, of execution of a `break`, `continue`, `goto`, or `return` statement, or of propagation of an exception out of the `try` statement.</span></span>

<span data-ttu-id="1e72a-107">已处理的异常中会保证运行相关联的 `finally` 块。</span><span class="sxs-lookup"><span data-stu-id="1e72a-107">Within a handled exception, the associated `finally` block is guaranteed to be run.</span></span> <span data-ttu-id="1e72a-108">但是，如果异常未经处理，则 `finally` 块的执行将取决于异常解除操作的触发方式。</span><span class="sxs-lookup"><span data-stu-id="1e72a-108">However, if the exception is unhandled, execution of the `finally` block is dependent on how the exception unwind operation is triggered.</span></span> <span data-ttu-id="1e72a-109">反过来，这又取决于你计算机的设置方式。</span><span class="sxs-lookup"><span data-stu-id="1e72a-109">That, in turn, is dependent on how your computer is set up.</span></span> <span data-ttu-id="1e72a-110">只有在 `finally` 子句不运行的情况下，才会涉及程序被立即停止的情况。</span><span class="sxs-lookup"><span data-stu-id="1e72a-110">The only cases where `finally` clauses don't run involve a program being immediately stopped.</span></span> <span data-ttu-id="1e72a-111">例如，由于 IL 语句损坏而引发 <xref:System.InvalidProgramException>。</span><span class="sxs-lookup"><span data-stu-id="1e72a-111">An example of this would be when <xref:System.InvalidProgramException> gets thrown because of the IL statements being corrupt.</span></span> <span data-ttu-id="1e72a-112">在大多数操作系统上，会在停止和卸载进程时进行合理的资源清理。</span><span class="sxs-lookup"><span data-stu-id="1e72a-112">On most operating systems, reasonable resource cleanup will take place as part of stopping and unloading the process.</span></span>

<span data-ttu-id="1e72a-113">通常情况下，当未经处理的异常终止应用程序时，`finally` 块是否运行已不重要。</span><span class="sxs-lookup"><span data-stu-id="1e72a-113">Usually, when an unhandled exception ends an application, whether or not the `finally` block is run is not important.</span></span> <span data-ttu-id="1e72a-114">但是，如果 `finally` 块中的语句必须在这种情况下运行，则可以将 `catch` 块添加到 `try`-`finally` 语句，这是其中一种解决方法。</span><span class="sxs-lookup"><span data-stu-id="1e72a-114">However, if you have statements in a `finally` block that must be run even in that situation, one solution is to add a `catch` block to the `try`-`finally` statement.</span></span> <span data-ttu-id="1e72a-115">另一种解决方法是，可以捕获可能在调用堆栈上方的 `try`-`finally` 语句的 `try` 块中引发的异常。</span><span class="sxs-lookup"><span data-stu-id="1e72a-115">Alternatively, you can catch the exception that might be thrown in the `try` block of a `try`-`finally` statement higher up the call stack.</span></span> <span data-ttu-id="1e72a-116">也就是说，可以通过以下几种方法来捕获异常：调用包含 `try`-`finally` 语句的方法、调用该方法或调用堆栈中的任何方法。</span><span class="sxs-lookup"><span data-stu-id="1e72a-116">That is, you can catch the exception in the method that calls the method that contains the `try`-`finally` statement, or in the method that calls that method, or in any method in the call stack.</span></span> <span data-ttu-id="1e72a-117">如果未捕获异常，则 `finally` 块的执行取决于操作系统是否选择触发异常解除操作。</span><span class="sxs-lookup"><span data-stu-id="1e72a-117">If the exception is not caught, execution of the `finally` block depends on whether the operating system chooses to trigger an exception unwind operation.</span></span>

## <a name="example"></a><span data-ttu-id="1e72a-118">示例</span><span class="sxs-lookup"><span data-stu-id="1e72a-118">Example</span></span>

<span data-ttu-id="1e72a-119">在以下示例中，无效的转换语句会导致 `System.InvalidCastException` 异常。</span><span class="sxs-lookup"><span data-stu-id="1e72a-119">In the following example, an invalid conversion statement causes a `System.InvalidCastException` exception.</span></span> <span data-ttu-id="1e72a-120">异常未经处理。</span><span class="sxs-lookup"><span data-stu-id="1e72a-120">The exception is unhandled.</span></span>

[!code-csharp[csrefKeywordsExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#4)]

<span data-ttu-id="1e72a-121">在以下示例中，`TryCast` 方法导致的异常会在比调用堆栈更远的方法中被捕获。</span><span class="sxs-lookup"><span data-stu-id="1e72a-121">In the following example, an exception from the `TryCast` method is caught in a method farther up the call stack.</span></span>

[!code-csharp[csrefKeywordsExceptions#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#6)]

<span data-ttu-id="1e72a-122">有关 `finally` 的详细信息，请参阅 [try-catch-finally](try-catch-finally.md)。</span><span class="sxs-lookup"><span data-stu-id="1e72a-122">For more information about `finally`, see [try-catch-finally](try-catch-finally.md).</span></span>

<span data-ttu-id="1e72a-123">C# 还包含 [using 语句](using-statement.md)，它以简便语法为 <xref:System.IDisposable> 对象提供类似的功能。</span><span class="sxs-lookup"><span data-stu-id="1e72a-123">C# also contains the [using statement](using-statement.md), which provides similar functionality for <xref:System.IDisposable> objects in a convenient syntax.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1e72a-124">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="1e72a-124">C# language specification</span></span>

<span data-ttu-id="1e72a-125">有关详细信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)中的 [try 语句](~/_csharplang/spec/statements.md#the-try-statement)部分。</span><span class="sxs-lookup"><span data-stu-id="1e72a-125">For more information, see [The try statement](~/_csharplang/spec/statements.md#the-try-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1e72a-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1e72a-126">See also</span></span>

- [<span data-ttu-id="1e72a-127">C# 参考</span><span class="sxs-lookup"><span data-stu-id="1e72a-127">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1e72a-128">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="1e72a-128">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1e72a-129">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="1e72a-129">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="1e72a-130">try、throw 和 catch 语句 (C++)</span><span class="sxs-lookup"><span data-stu-id="1e72a-130">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="1e72a-131">throw</span><span class="sxs-lookup"><span data-stu-id="1e72a-131">throw</span></span>](throw.md)
- [<span data-ttu-id="1e72a-132">try-catch</span><span class="sxs-lookup"><span data-stu-id="1e72a-132">try-catch</span></span>](try-catch.md)
- [<span data-ttu-id="1e72a-133">如何：显式引发异常</span><span class="sxs-lookup"><span data-stu-id="1e72a-133">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
