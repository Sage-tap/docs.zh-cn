---
description: '详细了解： Visual Basic 的错误语句 () '
title: On Error 语句
ms.date: 07/20/2015
f1_keywords:
- vb.OnError
helpviewer_keywords:
- Visual Basic code, control flow
- Resume Next statement [Visual Basic]
- errors [Visual Basic], trapping
- error handling, On Error statement
- Next statement [Visual Basic], On Error
- control flow [Visual Basic], branching
- Error keyword [Visual Basic]
- execution [Visual Basic], conditional
- Resume statement [Visual Basic], and On Error statement
- Error statement [Visual Basic], and On Error statement
- GoTo statement [Visual Basic], and On Error statement
- branching [Visual Basic], on error
- conditional statements [Visual Basic], On Error
- On Error statement [Visual Basic], syntax
- On keyword [Visual Basic]
- run-time errors [Visual Basic], handling
- On Error statement [Visual Basic]
ms.assetid: ff947930-fb84-40cf-bd66-1ea219561d5c
ms.openlocfilehash: 593e90b07101d08d18a0db127bcb74cf6509f317
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768826"
---
# <a name="on-error-statement-visual-basic"></a><span data-ttu-id="b575c-103">On Error 语句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b575c-103">On Error Statement (Visual Basic)</span></span>

<span data-ttu-id="b575c-104">启用错误处理例程，并指定例程在过程中的位置;还可用于禁用错误处理例程。</span><span class="sxs-lookup"><span data-stu-id="b575c-104">Enables an error-handling routine and specifies the location of the routine within a procedure; can also be used to disable an error-handling routine.</span></span> <span data-ttu-id="b575c-105">`On Error`语句用在非结构化错误处理中，可以使用而不是结构化异常处理。</span><span class="sxs-lookup"><span data-stu-id="b575c-105">The `On Error` statement is used in unstructured error handling and can be used instead of structured exception handling.</span></span> <span data-ttu-id="b575c-106">[结构化异常处理](../../../standard/exceptions/index.md) 内置于 .net 中，通常更高效，因此在处理应用程序中的运行时错误时建议使用。</span><span class="sxs-lookup"><span data-stu-id="b575c-106">[Structured exception handling](../../../standard/exceptions/index.md) is built into .NET, is generally more efficient, and so is recommended when handling runtime errors in your application.</span></span>

 <span data-ttu-id="b575c-107">如果没有错误处理或异常处理，则发生的任何运行时错误都是致命的：将显示一条错误消息，并停止执行。</span><span class="sxs-lookup"><span data-stu-id="b575c-107">Without error handling or exception handling, any run-time error that occurs is fatal: an error message is displayed, and execution stops.</span></span>

> [!NOTE]
> <span data-ttu-id="b575c-108">`Error`关键字还用于[Error 语句](error-statement.md)，该语句支持向后兼容性。</span><span class="sxs-lookup"><span data-stu-id="b575c-108">The `Error` keyword is also used in the [Error Statement](error-statement.md), which is supported for backward compatibility.</span></span>

## <a name="syntax"></a><span data-ttu-id="b575c-109">语法</span><span class="sxs-lookup"><span data-stu-id="b575c-109">Syntax</span></span>

```vb
On Error { GoTo [ line | 0 | -1 ] | Resume Next }
```

## <a name="parts"></a><span data-ttu-id="b575c-110">组成部分</span><span class="sxs-lookup"><span data-stu-id="b575c-110">Parts</span></span>

|<span data-ttu-id="b575c-111">术语</span><span class="sxs-lookup"><span data-stu-id="b575c-111">Term</span></span>|<span data-ttu-id="b575c-112">定义</span><span class="sxs-lookup"><span data-stu-id="b575c-112">Definition</span></span>|
|---|---|
|<span data-ttu-id="b575c-113">`GoTo`*行*</span><span class="sxs-lookup"><span data-stu-id="b575c-113">`GoTo` *line*</span></span>|<span data-ttu-id="b575c-114">启用从必需 *line* 参数所指定的行开始的错误处理例程。</span><span class="sxs-lookup"><span data-stu-id="b575c-114">Enables the error-handling routine that starts at the line specified in the required *line* argument.</span></span> <span data-ttu-id="b575c-115">*Line* 参数是任意行标签或行号。</span><span class="sxs-lookup"><span data-stu-id="b575c-115">The *line* argument is any line label or line number.</span></span> <span data-ttu-id="b575c-116">如果出现运行时错误，控制将分支到指定的行，使错误处理程序处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="b575c-116">If a run-time error occurs, control branches to the specified line, making the error handler active.</span></span> <span data-ttu-id="b575c-117">指定的行必须与语句位于同一过程中， `On Error` 否则将发生编译时错误。</span><span class="sxs-lookup"><span data-stu-id="b575c-117">The specified line must be in the same procedure as the `On Error` statement or a compile-time error will occur.</span></span>|
|`GoTo 0`|<span data-ttu-id="b575c-118">禁用当前过程中启用的错误处理程序，并将其重置为 `Nothing` 。</span><span class="sxs-lookup"><span data-stu-id="b575c-118">Disables enabled error handler in the current procedure and resets it to `Nothing`.</span></span>|
|`GoTo -1`|<span data-ttu-id="b575c-119">在当前过程中禁用已启用的异常并将其重置为 `Nothing` 。</span><span class="sxs-lookup"><span data-stu-id="b575c-119">Disables enabled exception in the current procedure and resets it to `Nothing`.</span></span>|
|`Resume Next`|<span data-ttu-id="b575c-120">指定在发生运行时错误时，控制转到紧随发生错误的语句之后的语句，然后从该点继续执行。</span><span class="sxs-lookup"><span data-stu-id="b575c-120">Specifies that when a run-time error occurs, control goes to the statement immediately following the statement where the error occurred, and execution continues from that point.</span></span> <span data-ttu-id="b575c-121">在访问对象时，请使用此窗体而不是 `On Error GoTo` 。</span><span class="sxs-lookup"><span data-stu-id="b575c-121">Use this form rather than `On Error GoTo` when accessing objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b575c-122">备注</span><span class="sxs-lookup"><span data-stu-id="b575c-122">Remarks</span></span>

> [!NOTE]
> <span data-ttu-id="b575c-123">建议尽可能地在代码中使用结构化异常处理，而不是使用非结构化异常处理和 `On Error` 语句。</span><span class="sxs-lookup"><span data-stu-id="b575c-123">We recommend that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` statement.</span></span> <span data-ttu-id="b575c-124">有关详细信息，请参阅 [Try...Catch...Finally 语句](try-catch-finally-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="b575c-124">For more information, see [Try...Catch...Finally Statement](try-catch-finally-statement.md).</span></span>

 <span data-ttu-id="b575c-125">"Enabled" 错误处理程序是指由语句打开的错误处理程序 `On Error` 。</span><span class="sxs-lookup"><span data-stu-id="b575c-125">An "enabled" error handler is one that is turned on by an `On Error` statement.</span></span> <span data-ttu-id="b575c-126">"活动" 错误处理程序是在处理错误的过程中的已启用处理程序。</span><span class="sxs-lookup"><span data-stu-id="b575c-126">An "active" error handler is an enabled handler that is in the process of handling an error.</span></span>

 <span data-ttu-id="b575c-127">如果错误处理程序处于活动状态时发生错误， (在发生错误的情况下出现错误 `Resume` ， `Exit Sub` `Exit Function`) ， `Exit Property` 则当前过程的错误处理程序将无法处理此错误。</span><span class="sxs-lookup"><span data-stu-id="b575c-127">If an error occurs while an error handler is active (between the occurrence of the error and a `Resume`, `Exit Sub`, `Exit Function`, or `Exit Property` statement), the current procedure's error handler cannot handle the error.</span></span> <span data-ttu-id="b575c-128">控件返回到调用过程。</span><span class="sxs-lookup"><span data-stu-id="b575c-128">Control returns to the calling procedure.</span></span>
  
 <span data-ttu-id="b575c-129">如果调用过程具有已启用的错误处理程序，则会激活该处理程序来处理错误。</span><span class="sxs-lookup"><span data-stu-id="b575c-129">If the calling procedure has an enabled error handler, it is activated to handle the error.</span></span> <span data-ttu-id="b575c-130">如果调用过程的错误处理程序也处于活动状态，控制将通过以前的调用过程返回，直到找到已启用但不活动的错误处理程序。</span><span class="sxs-lookup"><span data-stu-id="b575c-130">If the calling procedure's error handler is also active, control passes back through previous calling procedures until an enabled, but inactive, error handler is found.</span></span> <span data-ttu-id="b575c-131">如果找不到这样的错误处理程序，则该错误在实际发生时是致命的。</span><span class="sxs-lookup"><span data-stu-id="b575c-131">If no such error handler is found, the error is fatal at the point at which it actually occurred.</span></span>
  
 <span data-ttu-id="b575c-132">每次错误处理程序将控制权返回给调用过程时，该过程将成为当前过程。</span><span class="sxs-lookup"><span data-stu-id="b575c-132">Each time the error handler passes control back to a calling procedure, that procedure becomes the current procedure.</span></span> <span data-ttu-id="b575c-133">一旦任何过程中的错误处理程序处理错误，就会在当前过程中的语句指定的点继续执行 `Resume` 。</span><span class="sxs-lookup"><span data-stu-id="b575c-133">Once an error is handled by an error handler in any procedure, execution resumes in the current procedure at the point designated by the `Resume` statement.</span></span>
  
> [!NOTE]
> <span data-ttu-id="b575c-134">错误处理例程不是 `Sub` 过程或 `Function` 过程。</span><span class="sxs-lookup"><span data-stu-id="b575c-134">An error-handling routine is not a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="b575c-135">它是由行标签或行号标记的代码部分。</span><span class="sxs-lookup"><span data-stu-id="b575c-135">It is a section of code marked by a line label or a line number.</span></span>
  
## <a name="number-property"></a><span data-ttu-id="b575c-136">Number 属性</span><span class="sxs-lookup"><span data-stu-id="b575c-136">Number Property</span></span>

 <span data-ttu-id="b575c-137">错误处理例程依赖于对象的属性中的值 `Number` `Err` 来确定错误的原因。</span><span class="sxs-lookup"><span data-stu-id="b575c-137">Error-handling routines rely on the value in the `Number` property of the `Err` object to determine the cause of the error.</span></span> <span data-ttu-id="b575c-138">在 `Err` 发生任何其他错误之前，或在调用可能导致错误的过程之前，例程应测试或保存对象中的相关属性值。</span><span class="sxs-lookup"><span data-stu-id="b575c-138">The routine should test or save relevant property values in the `Err` object before any other error can occur or before a procedure that might cause an error is called.</span></span> <span data-ttu-id="b575c-139">对象中的属性值 `Err` 仅反映最近的错误。</span><span class="sxs-lookup"><span data-stu-id="b575c-139">The property values in the `Err` object reflect only the most recent error.</span></span> <span data-ttu-id="b575c-140">与关联的错误消息 `Err.Number` 包含在中 `Err.Description` 。</span><span class="sxs-lookup"><span data-stu-id="b575c-140">The error message associated with `Err.Number` is contained in `Err.Description`.</span></span>  
  
## <a name="throw-statement"></a><span data-ttu-id="b575c-141">Throw 语句</span><span class="sxs-lookup"><span data-stu-id="b575c-141">Throw Statement</span></span>  

 <span data-ttu-id="b575c-142">使用方法引发的错误会 `Err.Raise` 将 `Exception` 属性设置为类的新创建实例 <xref:System.Exception> 。</span><span class="sxs-lookup"><span data-stu-id="b575c-142">An error that is raised with the `Err.Raise` method sets the `Exception` property to a newly created instance of the <xref:System.Exception> class.</span></span> <span data-ttu-id="b575c-143">为了支持引发派生异常类型的异常， `Throw` 语言支持语句。</span><span class="sxs-lookup"><span data-stu-id="b575c-143">In order to support the raising of exceptions of derived exception types, a `Throw` statement is supported in the language.</span></span> <span data-ttu-id="b575c-144">这需要一个参数，该参数是要引发的异常实例。</span><span class="sxs-lookup"><span data-stu-id="b575c-144">This takes a single parameter that is the exception instance to be thrown.</span></span> <span data-ttu-id="b575c-145">下面的示例演示如何将这些功能与现有的异常处理支持结合使用：</span><span class="sxs-lookup"><span data-stu-id="b575c-145">The following example shows how these features can be used with the existing exception handling support:</span></span>

 [!code-vb[VbVbalrErrorHandling#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#17)]  
  
 <span data-ttu-id="b575c-146">请注意， `On Error GoTo` 语句捕获所有错误，而不考虑异常类。</span><span class="sxs-lookup"><span data-stu-id="b575c-146">Notice that the `On Error GoTo` statement traps all errors, regardless of the exception class.</span></span>
  
## <a name="on-error-resume-next"></a><span data-ttu-id="b575c-147">On Error Resume Next</span><span class="sxs-lookup"><span data-stu-id="b575c-147">On Error Resume Next</span></span>

 <span data-ttu-id="b575c-148">`On Error Resume Next` 使执行继续使用紧随导致运行时错误的语句之后的语句，或紧随包含语句的过程的最近调用之后的语句 `On Error Resume Next` 。</span><span class="sxs-lookup"><span data-stu-id="b575c-148">`On Error Resume Next` causes execution to continue with the statement immediately following the statement that caused the run-time error, or with the statement immediately following the most recent call out of the procedure containing the `On Error Resume Next` statement.</span></span> <span data-ttu-id="b575c-149">此语句允许在运行时错误的情况下继续执行。</span><span class="sxs-lookup"><span data-stu-id="b575c-149">This statement allows execution to continue despite a run-time error.</span></span> <span data-ttu-id="b575c-150">可以放置错误处理例程，其中发生错误，而不是将控制转移到过程内的另一个位置。</span><span class="sxs-lookup"><span data-stu-id="b575c-150">You can place the error-handling routine where the error would occur rather than transferring control to another location within the procedure.</span></span> <span data-ttu-id="b575c-151">`On Error Resume Next`当调用另一个过程时，语句变为非活动状态，因此， `On Error Resume Next` 如果您希望在该例程中进行内联错误处理，则应在每个调用的例程中执行语句。</span><span class="sxs-lookup"><span data-stu-id="b575c-151">An `On Error Resume Next` statement becomes inactive when another procedure is called, so you should execute an `On Error Resume Next` statement in each called routine if you want inline error handling within that routine.</span></span>
  
> [!NOTE]
> <span data-ttu-id="b575c-152">在 `On Error Resume Next` `On Error GoTo` 处理访问其他对象的过程中生成的错误时，构造可能更好。</span><span class="sxs-lookup"><span data-stu-id="b575c-152">The `On Error Resume Next` construct may be preferable to `On Error GoTo` when handling errors generated during access to other objects.</span></span> <span data-ttu-id="b575c-153">`Err`在每次与对象交互后进行检查将消除代码所访问的对象的歧义。</span><span class="sxs-lookup"><span data-stu-id="b575c-153">Checking `Err` after each interaction with an object removes ambiguity about which object was accessed by the code.</span></span> <span data-ttu-id="b575c-154">您可以确定哪个对象放置了错误代码，以及 `Err.Number` 哪个对象最初生成了错误 (在) 中指定的对象 `Err.Source` 。</span><span class="sxs-lookup"><span data-stu-id="b575c-154">You can be sure which object placed the error code in `Err.Number`, as well as which object originally generated the error (the object specified in `Err.Source`).</span></span>

## <a name="on-error-goto-0"></a><span data-ttu-id="b575c-155">On Error GoTo 0</span><span class="sxs-lookup"><span data-stu-id="b575c-155">On Error GoTo 0</span></span>

 <span data-ttu-id="b575c-156">`On Error GoTo 0` 禁用当前过程中的错误处理。</span><span class="sxs-lookup"><span data-stu-id="b575c-156">`On Error GoTo 0` disables error handling in the current procedure.</span></span> <span data-ttu-id="b575c-157">即使过程包含编号为0的行，它也不会将第0行指定为错误处理代码的开头。</span><span class="sxs-lookup"><span data-stu-id="b575c-157">It doesn't specify line 0 as the start of the error-handling code, even if the procedure contains a line numbered 0.</span></span> <span data-ttu-id="b575c-158">如果没有 `On Error GoTo 0` 语句，则在退出过程时，将自动禁用错误处理程序。</span><span class="sxs-lookup"><span data-stu-id="b575c-158">Without an `On Error GoTo 0` statement, an error handler is automatically disabled when a procedure is exited.</span></span>

## <a name="on-error-goto--1"></a><span data-ttu-id="b575c-159">Error GoTo 时-1</span><span class="sxs-lookup"><span data-stu-id="b575c-159">On Error GoTo -1</span></span>

 <span data-ttu-id="b575c-160">`On Error GoTo -1` 禁用当前过程中的异常。</span><span class="sxs-lookup"><span data-stu-id="b575c-160">`On Error GoTo -1` disables the exception in the current procedure.</span></span> <span data-ttu-id="b575c-161">即使过程包含编号为-1 的行，它也不会将第1行指定为错误处理代码的开头。</span><span class="sxs-lookup"><span data-stu-id="b575c-161">It does not specify line -1 as the start of the error-handling code, even if the procedure contains a line numbered -1.</span></span> <span data-ttu-id="b575c-162">如果不使用 `On Error GoTo -1` 语句，则在退出过程时，将自动禁用异常。</span><span class="sxs-lookup"><span data-stu-id="b575c-162">Without an `On Error GoTo -1` statement, an exception is automatically disabled when a procedure is exited.</span></span>

 <span data-ttu-id="b575c-163">若要防止错误处理代码在未发生错误时运行，请将 `Exit Sub` 、 `Exit Function` 或 `Exit Property` 语句紧靠在错误处理例程之前，如以下代码片段所示：</span><span class="sxs-lookup"><span data-stu-id="b575c-163">To prevent error-handling code from running when no error has occurred, place an `Exit Sub`, `Exit Function`, or `Exit Property` statement immediately before the error-handling routine, as in the following fragment:</span></span>

 [!code-vb[VbVbalrErrorHandling#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#18)]

 <span data-ttu-id="b575c-164">此处，错误处理代码将遵循 `Exit Sub` 语句，并在语句之前执行， `End Sub` 以将其与过程流区分开来。</span><span class="sxs-lookup"><span data-stu-id="b575c-164">Here, the error-handling code follows the `Exit Sub` statement and precedes the `End Sub` statement to separate it from the procedure flow.</span></span> <span data-ttu-id="b575c-165">可以在过程中的任何位置放置错误处理代码。</span><span class="sxs-lookup"><span data-stu-id="b575c-165">You can place error-handling code anywhere in a procedure.</span></span>

## <a name="untrapped-errors"></a><span data-ttu-id="b575c-166">未捕获错误</span><span class="sxs-lookup"><span data-stu-id="b575c-166">Untrapped Errors</span></span>

 <span data-ttu-id="b575c-167">当对象作为可执行文件运行时，对象中的未捕获错误将返回给控制应用程序。</span><span class="sxs-lookup"><span data-stu-id="b575c-167">Untrapped errors in objects are returned to the controlling application when the object is running as an executable file.</span></span> <span data-ttu-id="b575c-168">在开发环境中，仅当设置了正确的选项时，未捕获错误才能返回给控制应用程序。</span><span class="sxs-lookup"><span data-stu-id="b575c-168">Within the development environment, untrapped errors are returned to the controlling application only if the proper options are set.</span></span> <span data-ttu-id="b575c-169">请参阅宿主应用程序的文档，以了解在调试期间应设置哪些选项、如何设置这些选项以及宿主是否可以创建类。</span><span class="sxs-lookup"><span data-stu-id="b575c-169">See your host application's documentation for a description of which options should be set during debugging, how to set them, and whether the host can create classes.</span></span>

 <span data-ttu-id="b575c-170">如果创建的对象访问其他对象，则应尝试处理它们传回的任何未处理的错误。</span><span class="sxs-lookup"><span data-stu-id="b575c-170">If you create an object that accesses other objects, you should try to handle any unhandled errors they pass back.</span></span> <span data-ttu-id="b575c-171">如果无法做到这一点，请将中的错误代码映射 `Err.Number` 到你自己的错误之一，然后将它们传递回你的对象的调用方。</span><span class="sxs-lookup"><span data-stu-id="b575c-171">If you cannot, map the error codes in `Err.Number` to one of your own errors and then pass them back to the caller of your object.</span></span> <span data-ttu-id="b575c-172">应通过将错误代码添加到常量来指定错误 `VbObjectError` 。</span><span class="sxs-lookup"><span data-stu-id="b575c-172">You should specify your error by adding your error code to the `VbObjectError` constant.</span></span> <span data-ttu-id="b575c-173">例如，如果错误代码为1052，请按如下所示分配：</span><span class="sxs-lookup"><span data-stu-id="b575c-173">For example, if your error code is 1052, assign it as follows:</span></span>

 [!code-vb[VbVbalrErrorHandling#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#19)]

> [!CAUTION]
> <span data-ttu-id="b575c-174">调用 Windows 动态链接库 (Dll 时出现系统错误) 不会引发异常，并且在 Visual Basic 错误捕获时无法进行捕获。</span><span class="sxs-lookup"><span data-stu-id="b575c-174">System errors during calls to Windows dynamic-link libraries (DLLs) do not raise exceptions and cannot be trapped with Visual Basic error trapping.</span></span> <span data-ttu-id="b575c-175">调用 DLL 函数时，应根据 API 规范) 检查每个返回值的成功或失败 (，并在发生故障时检查 `Err` 对象的属性中的值 `LastDLLError` 。</span><span class="sxs-lookup"><span data-stu-id="b575c-175">When calling DLL functions, you should check each return value for success or failure (according to the API specifications), and in the event of a failure, check the value in the `Err` object's `LastDLLError` property.</span></span>

## <a name="example"></a><span data-ttu-id="b575c-176">示例</span><span class="sxs-lookup"><span data-stu-id="b575c-176">Example</span></span>

 <span data-ttu-id="b575c-177">此示例首先使用 `On Error GoTo` 语句在过程中指定错误处理例程的位置。</span><span class="sxs-lookup"><span data-stu-id="b575c-177">This example first uses the `On Error GoTo` statement to specify the location of an error-handling routine within a procedure.</span></span> <span data-ttu-id="b575c-178">在此示例中，被零除的尝试将生成错误编号6。</span><span class="sxs-lookup"><span data-stu-id="b575c-178">In the example, an attempt to divide by zero generates error number 6.</span></span> <span data-ttu-id="b575c-179">错误在错误处理例程中进行处理，然后将控件返回给导致错误的语句。</span><span class="sxs-lookup"><span data-stu-id="b575c-179">The error is handled in the error-handling routine, and control is then returned to the statement that caused the error.</span></span> <span data-ttu-id="b575c-180">`On Error GoTo 0`语句会关闭错误捕获。</span><span class="sxs-lookup"><span data-stu-id="b575c-180">The `On Error GoTo 0` statement turns off error trapping.</span></span> <span data-ttu-id="b575c-181">然后， `On Error Resume Next` 使用语句将错误捕获延迟，以便对下一条语句所生成的错误上下文具有特定的已知上下文。</span><span class="sxs-lookup"><span data-stu-id="b575c-181">Then the `On Error Resume Next` statement is used to defer error trapping so that the context for the error generated by the next statement can be known for certain.</span></span> <span data-ttu-id="b575c-182">请注意，在 `Err.Clear` `Err` 处理错误后，用于清除对象的属性。</span><span class="sxs-lookup"><span data-stu-id="b575c-182">Note that `Err.Clear` is used to clear the `Err` object's properties after the error is handled.</span></span>

 [!code-vb[VbVbalrErrorHandling#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#20)]

## <a name="requirements"></a><span data-ttu-id="b575c-183">要求</span><span class="sxs-lookup"><span data-stu-id="b575c-183">Requirements</span></span>

 <span data-ttu-id="b575c-184">**命名空间：** [Microsoft](../runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="b575c-184">**Namespace:** [Microsoft.VisualBasic](../runtime-library-members.md)</span></span>

 <span data-ttu-id="b575c-185">**程序集：** Microsoft.VisualBasic.dll) 中的 Visual Basic 运行时库 (</span><span class="sxs-lookup"><span data-stu-id="b575c-185">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>

## <a name="see-also"></a><span data-ttu-id="b575c-186">请参阅</span><span class="sxs-lookup"><span data-stu-id="b575c-186">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Number%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Description%2A>
- <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>
- [<span data-ttu-id="b575c-187">End 语句</span><span class="sxs-lookup"><span data-stu-id="b575c-187">End Statement</span></span>](end-statement.md)
- [<span data-ttu-id="b575c-188">Exit 语句</span><span class="sxs-lookup"><span data-stu-id="b575c-188">Exit Statement</span></span>](exit-statement.md)
- [<span data-ttu-id="b575c-189">Resume 语句</span><span class="sxs-lookup"><span data-stu-id="b575c-189">Resume Statement</span></span>](resume-statement.md)
- [<span data-ttu-id="b575c-190">错误消息</span><span class="sxs-lookup"><span data-stu-id="b575c-190">Error Messages</span></span>](../error-messages/index.md)
- [<span data-ttu-id="b575c-191">Try...Catch...Finally 语句</span><span class="sxs-lookup"><span data-stu-id="b575c-191">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
