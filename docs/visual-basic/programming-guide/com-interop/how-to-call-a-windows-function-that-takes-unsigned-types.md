---
description: '了解有关详细信息，请参阅如何：调用采用无符号类型的 Windows 函数 (Visual Basic) '
title: 如何：调用需要使用无符号类型的 Windows 函数
ms.date: 07/20/2015
helpviewer_keywords:
- Windows functions [Visual Basic], calling
- unsigned data types [Visual Basic]
- UShort data type [Visual Basic], using
- functions [Visual Basic], calling Windows functions
- ULong data type [Visual Basic], using
- UInteger data type [Visual Basic], using
- data types [Visual Basic], using
- unsigned types [Visual Basic]
- data types [Visual Basic], unsigned
- data types [Visual Basic], numeric
- unsigned types [Visual Basic], using
ms.assetid: c2c0e712-8dc2-43b9-b4c6-345fbb02e7ce
ms.openlocfilehash: 45851e22db88b9d35e5315398fb4cdbc2a7b920c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475638"
---
# <a name="how-to-call-a-windows-function-that-takes-unsigned-types-visual-basic"></a><span data-ttu-id="15055-103">如何：调用采用无符号类型的 Windows 函数 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="15055-103">How to: Call a Windows Function that Takes Unsigned Types (Visual Basic)</span></span>

<span data-ttu-id="15055-104">如果你使用的类、模块或结构具有无符号整数类型的成员，则可以使用 Visual Basic 访问这些成员。</span><span class="sxs-lookup"><span data-stu-id="15055-104">If you are consuming a class, module, or structure that has members of unsigned integer types, you can access these members with Visual Basic.</span></span>

## <a name="to-call-a-windows-function-that-takes-an-unsigned-type"></a><span data-ttu-id="15055-105">调用采用无符号类型的 Windows 函数</span><span class="sxs-lookup"><span data-stu-id="15055-105">To call a Windows function that takes an unsigned type</span></span>

1. <span data-ttu-id="15055-106">使用 [Declare 语句](../../language-reference/statements/declare-statement.md) 来告知 Visual Basic 哪个库包含函数、其在库中的名称、调用顺序，以及如何在调用字符串时转换字符串。</span><span class="sxs-lookup"><span data-stu-id="15055-106">Use a [Declare Statement](../../language-reference/statements/declare-statement.md) to tell Visual Basic which library holds the function, what its name is in that library, what its calling sequence is, and how to convert strings when calling it.</span></span>

2. <span data-ttu-id="15055-107">在 `Declare` 语句中，将 `UInteger` 、 `ULong` 、 `UShort` 或 `Byte` 适当地用于具有无符号类型的每个参数。</span><span class="sxs-lookup"><span data-stu-id="15055-107">In the `Declare` statement, use `UInteger`, `ULong`, `UShort`, or `Byte` as appropriate for each parameter with an unsigned type.</span></span>

3. <span data-ttu-id="15055-108">请参阅你要调用的 Windows 函数的文档，以查找它所使用的常量的名称和值。</span><span class="sxs-lookup"><span data-stu-id="15055-108">Consult the documentation for the Windows function you are calling to find the names and values of the constants it uses.</span></span> <span data-ttu-id="15055-109">其中许多是在 Winuser.h 文件中定义的。</span><span class="sxs-lookup"><span data-stu-id="15055-109">Many of these are defined in the WinUser.h file.</span></span>

4. <span data-ttu-id="15055-110">在代码中声明必要的常量。</span><span class="sxs-lookup"><span data-stu-id="15055-110">Declare the necessary constants in your code.</span></span> <span data-ttu-id="15055-111">许多 Windows 常量为32位无符号值，你应将其声明为 `As UInteger` 。</span><span class="sxs-lookup"><span data-stu-id="15055-111">Many Windows constants are 32-bit unsigned values, and you should declare these `As UInteger`.</span></span>

5. <span data-ttu-id="15055-112">以正常方式调用函数。</span><span class="sxs-lookup"><span data-stu-id="15055-112">Call the function in the normal way.</span></span> <span data-ttu-id="15055-113">下面的示例调用 Windows 函数 `MessageBox` ，该函数采用无符号整数参数。</span><span class="sxs-lookup"><span data-stu-id="15055-113">The following example calls the Windows function `MessageBox`, which takes an unsigned integer argument.</span></span>

    ```vb
    Public Class windowsMessage
        Private Declare Auto Function mb Lib "user32.dll" Alias "MessageBox" (
            ByVal hWnd As Integer,
            ByVal lpText As String,
            ByVal lpCaption As String,
            ByVal uType As UInteger) As Integer
        Private Const MB_OK As UInteger = 0
        Private Const MB_ICONEXCLAMATION As UInteger = &H30
        Private Const IDOK As UInteger = 1
        Private Const IDCLOSE As UInteger = 8
        Private Const c As UInteger = MB_OK Or MB_ICONEXCLAMATION
        Public Function messageThroughWindows() As String
            Dim r As Integer = mb(0, "Click OK if you see this!",
                "Windows API call", c)
            Dim s As String = "Windows API MessageBox returned " &
                 CStr(r)& vbCrLf & "(IDOK = " & CStr(IDOK) &
                 ", IDCLOSE = " & CStr(IDCLOSE) & ")"
            Return s
        End Function
    End Class
    ```

     <span data-ttu-id="15055-114">可以 `messageThroughWindows` 通过以下代码测试该函数。</span><span class="sxs-lookup"><span data-stu-id="15055-114">You can test the function `messageThroughWindows` with the following code.</span></span>

    ```vb
    Public Sub consumeWindowsMessage()
        Dim w As New windowsMessage
        w.messageThroughWindows()
    End Sub
    ```

    > [!CAUTION]
    > <span data-ttu-id="15055-115">`UInteger`、 `ULong` 、 `UShort` 和 `SByte` 数据类型不是语言独立性的一部分，[并且 Language-Independent 组件](../../../standard/language-independence-and-language-independent-components.md) (cls) ，因此符合 cls 的代码无法使用使用它们的组件。</span><span class="sxs-lookup"><span data-stu-id="15055-115">The `UInteger`, `ULong`, `UShort`, and `SByte` data types are not part of the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), so CLS-compliant code cannot consume a component that uses them.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="15055-116">调用非托管代码（如 (API) 的 Windows 应用程序编程接口）会使代码面临潜在的安全风险。</span><span class="sxs-lookup"><span data-stu-id="15055-116">Making a call to unmanaged code, such as the Windows application programming interface (API), exposes your code to potential security risks.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="15055-117">调用 Windows API 需要非托管代码权限，这可能会影响在部分信任情况下的执行。</span><span class="sxs-lookup"><span data-stu-id="15055-117">Calling the Windows API requires unmanaged code permission, which might affect its execution in partial-trust situations.</span></span> <span data-ttu-id="15055-118">有关详细信息，请参阅 <xref:System.Security.Permissions.SecurityPermission> 和 [代码访问权限](/previous-versions/dotnet/netframework-4.0/h846e9b3(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="15055-118">For more information, see <xref:System.Security.Permissions.SecurityPermission> and [Code Access Permissions](/previous-versions/dotnet/netframework-4.0/h846e9b3(v=vs.100)).</span></span>

## <a name="see-also"></a><span data-ttu-id="15055-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="15055-119">See also</span></span>

- [<span data-ttu-id="15055-120">数据类型</span><span class="sxs-lookup"><span data-stu-id="15055-120">Data Types</span></span>](../../language-reference/data-types/index.md)
- [<span data-ttu-id="15055-121">Integer 数据类型</span><span class="sxs-lookup"><span data-stu-id="15055-121">Integer Data Type</span></span>](../../language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="15055-122">UInteger 数据类型</span><span class="sxs-lookup"><span data-stu-id="15055-122">UInteger Data Type</span></span>](../../language-reference/data-types/uinteger-data-type.md)
- [<span data-ttu-id="15055-123">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="15055-123">Declare Statement</span></span>](../../language-reference/statements/declare-statement.md)
- [<span data-ttu-id="15055-124">演练：调用 Windows API</span><span class="sxs-lookup"><span data-stu-id="15055-124">Walkthrough: Calling Windows APIs</span></span>](walkthrough-calling-windows-apis.md)
