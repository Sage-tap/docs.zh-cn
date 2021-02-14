---
description: '了解详细信息：如何：编写扩展方法 (Visual Basic) '
title: 如何：编写扩展方法
ms.date: 07/20/2015
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
ms.openlocfilehash: 4c5d88976e55288ccb350ab82d459db0a23f468e
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100476184"
---
# <a name="how-to-write-an-extension-method-visual-basic"></a><span data-ttu-id="8033c-103">如何：编写扩展方法 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8033c-103">How to: Write an Extension Method (Visual Basic)</span></span>

<span data-ttu-id="8033c-104">扩展方法使你能够向现有类添加方法。</span><span class="sxs-lookup"><span data-stu-id="8033c-104">Extension methods enable you to add methods to an existing class.</span></span> <span data-ttu-id="8033c-105">可以调用扩展方法，就像它是该类的实例一样。</span><span class="sxs-lookup"><span data-stu-id="8033c-105">The extension method can be called as if it were an instance of that class.</span></span>

### <a name="to-define-an-extension-method"></a><span data-ttu-id="8033c-106">定义扩展方法</span><span class="sxs-lookup"><span data-stu-id="8033c-106">To define an extension method</span></span>

1. <span data-ttu-id="8033c-107">在 Visual Studio 中打开新的或现有的 Visual Basic 应用程序。</span><span class="sxs-lookup"><span data-stu-id="8033c-107">Open a new or existing Visual Basic application in Visual Studio.</span></span>

2. <span data-ttu-id="8033c-108">在要在其中定义扩展方法的文件的顶部，请包含以下 import 语句：</span><span class="sxs-lookup"><span data-stu-id="8033c-108">At the top of the file in which you want to define an extension method, include the following import statement:</span></span>

    ```vb
    Imports System.Runtime.CompilerServices
    ```

3. <span data-ttu-id="8033c-109">在新应用程序或现有应用程序的模块中，使用属性开始方法定义 [`<Extension>`](xref:System.Runtime.CompilerServices.ExtensionAttribute) ：</span><span class="sxs-lookup"><span data-stu-id="8033c-109">Within a module in your new or existing application, begin the method definition with the [`<Extension>`](xref:System.Runtime.CompilerServices.ExtensionAttribute) attribute:</span></span>

    ```vb
    <Extension()>
    ```

    <span data-ttu-id="8033c-110">请注意， `Extension` 属性只能应用于 `Sub` `Function` Visual Basic [模块](../../../language-reference/statements/module-statement.md)中 (或过程) 的方法。</span><span class="sxs-lookup"><span data-stu-id="8033c-110">Note that the `Extension` attribute can only be applied to a method (a `Sub` or `Function` procedure) in a Visual Basic [Module](../../../language-reference/statements/module-statement.md).</span></span> <span data-ttu-id="8033c-111">如果将它应用于或中的方法 `Class` `Structure` ，则 Visual Basic 编译器会生成错误 [BC36551](../../../misc/bc36551.md)，"只能在模块中定义扩展方法。"</span><span class="sxs-lookup"><span data-stu-id="8033c-111">If you apply it to a method in a `Class` or a `Structure`, the Visual Basic compiler generates error [BC36551](../../../misc/bc36551.md), "Extension methods can be defined only in modules."</span></span>

4. <span data-ttu-id="8033c-112">用普通方法声明方法，但第一个参数的类型必须是要扩展的数据类型。</span><span class="sxs-lookup"><span data-stu-id="8033c-112">Declare your method in the ordinary way, except that the type of the first parameter must be the data type you want to extend.</span></span>

    ```vb
    <Extension()>
    Public Sub SubName(para1 As ExtendedType, <other parameters>)
         ' < Body of the method >
    End Sub
    ```

## <a name="example"></a><span data-ttu-id="8033c-113">示例</span><span class="sxs-lookup"><span data-stu-id="8033c-113">Example</span></span>

<span data-ttu-id="8033c-114">下面的示例声明了模块中的扩展方法 `StringExtensions` 。</span><span class="sxs-lookup"><span data-stu-id="8033c-114">The following example declares an extension method in module `StringExtensions`.</span></span> <span data-ttu-id="8033c-115">第二个模块 `Module1` 导入 `StringExtensions` 并调用方法。</span><span class="sxs-lookup"><span data-stu-id="8033c-115">A second module, `Module1`, imports `StringExtensions` and calls the method.</span></span> <span data-ttu-id="8033c-116">在调用扩展方法时，该方法必须在范围内。</span><span class="sxs-lookup"><span data-stu-id="8033c-116">The extension method must be in scope when it is called.</span></span> <span data-ttu-id="8033c-117">扩展方法 `PrintAndPunctuate` <xref:System.String> 使用一个方法来扩展类，该方法将后跟以参数形式发送的标点符号字符串作为参数。</span><span class="sxs-lookup"><span data-stu-id="8033c-117">Extension method `PrintAndPunctuate` extends the <xref:System.String> class with a method that displays the string instance followed by a string of punctuation symbols sent in as a parameter.</span></span>

```vb
' Declarations will typically be in a separate module.
Imports System.Runtime.CompilerServices

Module StringExtensions
    <Extension()>
    Public Sub PrintAndPunctuate(aString As String, punc As String)
        Console.WriteLine(aString & punc)
    End Sub

End Module
```

```vb
' Import the module that holds the extension method you want to use,
' and call it.

Imports ConsoleApplication2.StringExtensions

Module Module1

    Sub Main()
        Dim example = "Hello"
        example.PrintAndPunctuate("?")
        example.PrintAndPunctuate("!!!!")
    End Sub

End Module
```

<span data-ttu-id="8033c-118">请注意，方法是用两个参数定义的，并且只能用一个参数调用。</span><span class="sxs-lookup"><span data-stu-id="8033c-118">Notice that the method is defined with two parameters and called with only one.</span></span> <span data-ttu-id="8033c-119">方法定义中的第一个参数 `aString` 绑定到 `example` `String` 调用方法的实例。</span><span class="sxs-lookup"><span data-stu-id="8033c-119">The first parameter, `aString`, in the method definition is bound to `example`, the instance of `String` that calls the method.</span></span> <span data-ttu-id="8033c-120">示例的输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="8033c-120">The output of the example is as follows:</span></span>

```console
Hello?
Hello!!!!
```

## <a name="see-also"></a><span data-ttu-id="8033c-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="8033c-121">See also</span></span>

- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [<span data-ttu-id="8033c-122">扩展方法</span><span class="sxs-lookup"><span data-stu-id="8033c-122">Extension Methods</span></span>](extension-methods.md)
- [<span data-ttu-id="8033c-123">Module 语句</span><span class="sxs-lookup"><span data-stu-id="8033c-123">Module Statement</span></span>](../../../language-reference/statements/module-statement.md)
- [<span data-ttu-id="8033c-124">过程形参和实参</span><span class="sxs-lookup"><span data-stu-id="8033c-124">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="8033c-125">Visual Basic 中的范围</span><span class="sxs-lookup"><span data-stu-id="8033c-125">Scope in Visual Basic</span></span>](../declared-elements/scope.md)
