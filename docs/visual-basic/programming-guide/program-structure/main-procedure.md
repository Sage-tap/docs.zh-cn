---
description: 了解详细信息： Visual Basic 中的 Main 过程
title: 主要过程
ms.date: 07/20/2015
f1_keywords:
- vb.Main
helpviewer_keywords:
- Main procedure
- Main method [Visual Basic]
- main function
ms.assetid: f0db283e-f283-4464-b521-b90858cc1b44
ms.openlocfilehash: b25190ef216fe4219923a27d6bbe0acff4536685
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100432801"
---
# <a name="main-procedure-in-visual-basic"></a><span data-ttu-id="9281c-103">Visual Basic 中的 Main 过程</span><span class="sxs-lookup"><span data-stu-id="9281c-103">Main Procedure in Visual Basic</span></span>

<span data-ttu-id="9281c-104">每个 Visual Basic 应用程序都必须包含一个名为的过程 `Main` 。</span><span class="sxs-lookup"><span data-stu-id="9281c-104">Every Visual Basic application must contain a procedure called `Main`.</span></span> <span data-ttu-id="9281c-105">此过程可用作应用程序的起点和总体控制。</span><span class="sxs-lookup"><span data-stu-id="9281c-105">This procedure serves as the starting point and overall control for your application.</span></span> <span data-ttu-id="9281c-106">当你的 `Main` 应用程序已加载并准备好将控制传递给你的应用程序时，.NET Framework 将调用你的过程。</span><span class="sxs-lookup"><span data-stu-id="9281c-106">The .NET Framework calls your `Main` procedure when it has loaded your application and is ready to pass control to it.</span></span> <span data-ttu-id="9281c-107">除非要创建 Windows 窗体应用程序，否则必须 `Main` 为自己运行的应用程序编写过程。</span><span class="sxs-lookup"><span data-stu-id="9281c-107">Unless you are creating a Windows Forms application, you must write the `Main` procedure for applications that run on their own.</span></span>

 <span data-ttu-id="9281c-108">`Main` 包含首先运行的代码。</span><span class="sxs-lookup"><span data-stu-id="9281c-108">`Main` contains the code that runs first.</span></span> <span data-ttu-id="9281c-109">在中 `Main` ，您可以在程序启动时确定要加载的窗体，查明您的应用程序的副本是否已在系统上运行，为您的应用程序建立一组变量，或者打开应用程序所需的数据库。</span><span class="sxs-lookup"><span data-stu-id="9281c-109">In `Main`, you can determine which form is to be loaded first when the program starts, find out if a copy of your application is already running on the system, establish a set of variables for your application, or open a database that the application requires.</span></span>

## <a name="requirements-for-the-main-procedure"></a><span data-ttu-id="9281c-110">Main 过程的要求</span><span class="sxs-lookup"><span data-stu-id="9281c-110">Requirements for the Main Procedure</span></span>

 <span data-ttu-id="9281c-111">在其自身 (上运行的文件通常具有扩展名 .exe) 必须包含 `Main` 过程。</span><span class="sxs-lookup"><span data-stu-id="9281c-111">A file that runs on its own (usually with extension .exe) must contain a `Main` procedure.</span></span> <span data-ttu-id="9281c-112">库 (例如，扩展名为 .dll) 不会自行运行，也不需要 `Main` 过程。</span><span class="sxs-lookup"><span data-stu-id="9281c-112">A library (for example with extension .dll) does not run on its own and does not require a `Main` procedure.</span></span> <span data-ttu-id="9281c-113">可以创建的不同类型的项目的要求如下：</span><span class="sxs-lookup"><span data-stu-id="9281c-113">The requirements for the different types of projects you can create are as follows:</span></span>

- <span data-ttu-id="9281c-114">控制台应用程序会自行运行，你必须至少提供一个 `Main` 过程。</span><span class="sxs-lookup"><span data-stu-id="9281c-114">Console applications run on their own, and you must supply at least one `Main` procedure.</span></span>

- <span data-ttu-id="9281c-115">Windows 窗体应用程序独立运行。</span><span class="sxs-lookup"><span data-stu-id="9281c-115">Windows Forms applications run on their own.</span></span> <span data-ttu-id="9281c-116">不过，Visual Basic 编译器会自动 `Main` 在此类应用程序中生成过程，而不需要编写一个过程。</span><span class="sxs-lookup"><span data-stu-id="9281c-116">However, the Visual Basic compiler automatically generates a `Main` procedure in such an application, and you do not need to write one.</span></span>

- <span data-ttu-id="9281c-117">类库不需要 `Main` 过程。</span><span class="sxs-lookup"><span data-stu-id="9281c-117">Class libraries do not require a `Main` procedure.</span></span> <span data-ttu-id="9281c-118">其中包括 Windows 控件库和 Web 控件库。</span><span class="sxs-lookup"><span data-stu-id="9281c-118">These include Windows Control Libraries and Web Control Libraries.</span></span> <span data-ttu-id="9281c-119">Web 应用程序部署为类库。</span><span class="sxs-lookup"><span data-stu-id="9281c-119">Web applications are deployed as class libraries.</span></span>

## <a name="declaring-the-main-procedure"></a><span data-ttu-id="9281c-120">声明 Main 过程</span><span class="sxs-lookup"><span data-stu-id="9281c-120">Declaring the Main Procedure</span></span>

 <span data-ttu-id="9281c-121">有四种方法可以声明 `Main` 过程。</span><span class="sxs-lookup"><span data-stu-id="9281c-121">There are four ways to declare the `Main` procedure.</span></span> <span data-ttu-id="9281c-122">它可以接受参数，也可以返回值。</span><span class="sxs-lookup"><span data-stu-id="9281c-122">It can take arguments or not, and it can return a value or not.</span></span>

> [!NOTE]
> <span data-ttu-id="9281c-123">如果 `Main` 在类中声明，则必须使用 `Shared` 关键字。</span><span class="sxs-lookup"><span data-stu-id="9281c-123">If you declare `Main` in a class, you must use the `Shared` keyword.</span></span> <span data-ttu-id="9281c-124">在模块中， `Main` 无需为 `Shared` 。</span><span class="sxs-lookup"><span data-stu-id="9281c-124">In a module, `Main` does not need to be `Shared`.</span></span>

- <span data-ttu-id="9281c-125">最简单的方法是声明 `Sub` 不采用参数或返回值的过程。</span><span class="sxs-lookup"><span data-stu-id="9281c-125">The simplest way is to declare a `Sub` procedure that does not take arguments or return a value.</span></span>

    ```vb
    Module mainModule
        Sub Main()
            MsgBox("The Main procedure is starting the application.")
            ' Insert call to appropriate starting place in your code.
            MsgBox("The application is terminating.")
        End Sub
    End Module
    ```

- <span data-ttu-id="9281c-126">`Main` 还可以返回一个 `Integer` 值，操作系统使用该值作为程序的退出代码。</span><span class="sxs-lookup"><span data-stu-id="9281c-126">`Main` can also return an `Integer` value, which the operating system uses as the exit code for your program.</span></span> <span data-ttu-id="9281c-127">其他程序可以通过检查 Windows ERRORLEVEL 值来测试此代码。</span><span class="sxs-lookup"><span data-stu-id="9281c-127">Other programs can test this code by examining the Windows ERRORLEVEL value.</span></span> <span data-ttu-id="9281c-128">若要返回退出代码，必须将声明 `Main` 为 `Function` 过程而不是 `Sub` 过程。</span><span class="sxs-lookup"><span data-stu-id="9281c-128">To return an exit code, you must declare `Main` as a `Function` procedure instead of a `Sub` procedure.</span></span>

    ```vb
    Module mainModule
        Function Main() As Integer
            MsgBox("The Main procedure is starting the application.")
            Dim returnValue As Integer = 0
            ' Insert call to appropriate starting place in your code.
            ' On return, assign appropriate value to returnValue.
            ' 0 usually means successful completion.
            MsgBox("The application is terminating with error level " &
                 CStr(returnValue) & ".")
            Return returnValue
        End Function
    End Module
    ```

- <span data-ttu-id="9281c-129">`Main` 还可以采用 `String` 数组作为参数。</span><span class="sxs-lookup"><span data-stu-id="9281c-129">`Main` can also take a `String` array as an argument.</span></span> <span data-ttu-id="9281c-130">数组中的每个字符串都包含一个用于调用程序的命令行参数。</span><span class="sxs-lookup"><span data-stu-id="9281c-130">Each string in the array contains one of the command-line arguments used to invoke your program.</span></span> <span data-ttu-id="9281c-131">您可以根据它们的值执行不同的操作。</span><span class="sxs-lookup"><span data-stu-id="9281c-131">You can take different actions depending on their values.</span></span>

    ```vb
    Module mainModule
        Function Main(ByVal cmdArgs() As String) As Integer
            MsgBox("The Main procedure is starting the application.")
            Dim returnValue As Integer = 0
            ' See if there are any arguments.
            If cmdArgs.Length > 0 Then
                For argNum As Integer = 0 To UBound(cmdArgs, 1)
                    ' Insert code to examine cmdArgs(argNum) and take
                    ' appropriate action based on its value.
                Next
            End If
            ' Insert call to appropriate starting place in your code.
            ' On return, assign appropriate value to returnValue.
            ' 0 usually means successful completion.
            MsgBox("The application is terminating with error level " &
                 CStr(returnValue) & ".")
            Return returnValue
        End Function
    End Module
    ```

- <span data-ttu-id="9281c-132">可以声明 `Main` 检查命令行参数，但不会返回退出代码，如下所示。</span><span class="sxs-lookup"><span data-stu-id="9281c-132">You can declare `Main` to examine the command-line arguments but not return an exit code, as follows.</span></span>

    ```vb
    Module mainModule
        Sub Main(ByVal cmdArgs() As String)
            MsgBox("The Main procedure is starting the application.")
            Dim returnValue As Integer = 0
            ' See if there are any arguments.
            If cmdArgs.Length > 0 Then
                For argNum As Integer = 0 To UBound(cmdArgs, 1)
                    ' Insert code to examine cmdArgs(argNum) and take
                    ' appropriate action based on its value.
                Next
            End If
            ' Insert call to appropriate starting place in your code.
            MsgBox("The application is terminating.")
        End Sub
    End Module
    ```
  
## <a name="see-also"></a><span data-ttu-id="9281c-133">请参阅</span><span class="sxs-lookup"><span data-stu-id="9281c-133">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>
- <xref:System.Array.Length%2A>
- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [<span data-ttu-id="9281c-134">Visual Basic 程序的结构</span><span class="sxs-lookup"><span data-stu-id="9281c-134">Structure of a Visual Basic Program</span></span>](structure-of-a-visual-basic-program.md)
- [<span data-ttu-id="9281c-135">-main</span><span class="sxs-lookup"><span data-stu-id="9281c-135">-main</span></span>](../../reference/command-line-compiler/main.md)
- [<span data-ttu-id="9281c-136">共享</span><span class="sxs-lookup"><span data-stu-id="9281c-136">Shared</span></span>](../../language-reference/modifiers/shared.md)
- [<span data-ttu-id="9281c-137">Sub 语句</span><span class="sxs-lookup"><span data-stu-id="9281c-137">Sub Statement</span></span>](../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="9281c-138">Function 语句</span><span class="sxs-lookup"><span data-stu-id="9281c-138">Function Statement</span></span>](../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="9281c-139">Integer 数据类型</span><span class="sxs-lookup"><span data-stu-id="9281c-139">Integer Data Type</span></span>](../../language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="9281c-140">String 数据类型</span><span class="sxs-lookup"><span data-stu-id="9281c-140">String Data Type</span></span>](../../language-reference/data-types/string-data-type.md)
