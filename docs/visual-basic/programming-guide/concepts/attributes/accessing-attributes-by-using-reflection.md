---
description: '了解有关以下内容的详细信息：使用反射访问属性 (Visual Basic) '
title: 使用反射访问特性
ms.date: 07/20/2015
ms.assetid: c56e41da-5433-464f-a7bf-2a722e78bc9f
ms.openlocfilehash: e585bb427456f1187eaf8c39937eaa67651d9309
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100437860"
---
# <a name="accessing-attributes-by-using-reflection-visual-basic"></a><span data-ttu-id="58b6e-103">使用反射访问特性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58b6e-103">Accessing Attributes by Using Reflection (Visual Basic)</span></span>

<span data-ttu-id="58b6e-104">你可以定义自定义特性并将其放入源代码中这一事实，在没有检索该信息并对其进行操作的方法的情况下将没有任何价值。</span><span class="sxs-lookup"><span data-stu-id="58b6e-104">The fact that you can define custom attributes and place them in your source code would be of little value without some way of retrieving that information and acting on it.</span></span> <span data-ttu-id="58b6e-105">通过使用反射，可以检索通过自定义特性定义的信息。</span><span class="sxs-lookup"><span data-stu-id="58b6e-105">By using reflection, you can retrieve the information that was defined with custom attributes.</span></span> <span data-ttu-id="58b6e-106">主要方法是 `GetCustomAttributes`，它返回对象数组，这些对象在运行时等效于源代码特性。</span><span class="sxs-lookup"><span data-stu-id="58b6e-106">The key method is `GetCustomAttributes`, which returns an array of objects that are the run-time equivalents of the source code attributes.</span></span> <span data-ttu-id="58b6e-107">此方法有多个重载版本。</span><span class="sxs-lookup"><span data-stu-id="58b6e-107">This method has several overloaded versions.</span></span> <span data-ttu-id="58b6e-108">有关详细信息，请参阅 <xref:System.Attribute>。</span><span class="sxs-lookup"><span data-stu-id="58b6e-108">For more information, see <xref:System.Attribute>.</span></span>

<span data-ttu-id="58b6e-109">特性规范，例如：</span><span class="sxs-lookup"><span data-stu-id="58b6e-109">An attribute specification such as:</span></span>

```vb
<Author("P. Ackerman", Version:=1.1)>
Class SampleClass
    ' P. Ackerman's code goes here...
End Class
```

 <span data-ttu-id="58b6e-110">在概念上等效于此：</span><span class="sxs-lookup"><span data-stu-id="58b6e-110">is conceptually equivalent to this:</span></span>

```vb
Dim anonymousAuthorObject As Author = New Author("P. Ackerman")
anonymousAuthorObject.version = 1.1
```

<span data-ttu-id="58b6e-111">但是，在为特性查询 `SampleClass` 之前，代码将不会执行。</span><span class="sxs-lookup"><span data-stu-id="58b6e-111">However, the code is not executed until `SampleClass` is queried for attributes.</span></span> <span data-ttu-id="58b6e-112">对 `SampleClass` 调用 `GetCustomAttributes` 会导致按上述方式构造并初始化一个 `Author` 对象。</span><span class="sxs-lookup"><span data-stu-id="58b6e-112">Calling `GetCustomAttributes` on `SampleClass` causes an `Author` object to be constructed and initialized as above.</span></span> <span data-ttu-id="58b6e-113">如果该类具有其他特性，则将以类似方式构造其他特性对象。</span><span class="sxs-lookup"><span data-stu-id="58b6e-113">If the class has other attributes, other attribute objects are constructed similarly.</span></span> <span data-ttu-id="58b6e-114">然后 `GetCustomAttributes` 会以数组形式返回 `Author` 对象和任何其他特性对象。</span><span class="sxs-lookup"><span data-stu-id="58b6e-114">`GetCustomAttributes` then returns the `Author` object and any other attribute objects in an array.</span></span> <span data-ttu-id="58b6e-115">之后你便可以循环访问此数组，根据每个数组元素的类型确定所应用的特性，并从特性对象中提取信息。</span><span class="sxs-lookup"><span data-stu-id="58b6e-115">You can then iterate over this array, determine what attributes were applied based on the type of each array element, and extract information from the attribute objects.</span></span>

## <a name="example"></a><span data-ttu-id="58b6e-116">示例</span><span class="sxs-lookup"><span data-stu-id="58b6e-116">Example</span></span>

<span data-ttu-id="58b6e-117">此处是一个完整的示例。</span><span class="sxs-lookup"><span data-stu-id="58b6e-117">Here is a complete example.</span></span> <span data-ttu-id="58b6e-118">定义自定义特性、将其应用于多个实体，并通过反射对其进行检索。</span><span class="sxs-lookup"><span data-stu-id="58b6e-118">A custom attribute is defined, applied to several entities, and retrieved via reflection.</span></span>

```vb
' Multiuse attribute
<System.AttributeUsage(System.AttributeTargets.Class Or
                       System.AttributeTargets.Struct,
                       AllowMultiple:=True)>
Public Class Author
    Inherits System.Attribute
    Private name As String
    Public version As Double
    Sub New(ByVal authorName As String)
        name = authorName

        ' Default value
        version = 1.0
    End Sub

    Function GetName() As String
        Return name
    End Function
End Class

' Class with the Author attribute
<Author("P. Ackerman")>
Public Class FirstClass
End Class

' Class without the Author attribute
Public Class SecondClass
End Class

' Class with multiple Author attributes.
<Author("P. Ackerman"), Author("R. Koch", Version:=2.0)>
Public Class ThirdClass
End Class

Class TestAuthorAttribute
    Sub Main()
        PrintAuthorInfo(GetType(FirstClass))
        PrintAuthorInfo(GetType(SecondClass))
        PrintAuthorInfo(GetType(ThirdClass))
    End Sub

    Private Shared Sub PrintAuthorInfo(ByVal t As System.Type)
        System.Console.WriteLine("Author information for {0}", t)

        ' Using reflection
        Dim attrs() As System.Attribute = System.Attribute.GetCustomAttributes(t)

        ' Displaying output
        For Each attr In attrs
            Dim a As Author = CType(attr, Author)
            System.Console.WriteLine("   {0}, version {1:f}", a.GetName(), a.version)
        Next
    End Sub

    ' Output:
    '   Author information for FirstClass
    '     P. Ackerman, version 1.00
    ' Author information for SecondClass
    ' Author information for ThirdClass
    '  R. Koch, version 2.00
    '  P. Ackerman, version 1.00

End Class
```

## <a name="see-also"></a><span data-ttu-id="58b6e-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="58b6e-119">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="58b6e-120">Visual Basic 编程指南</span><span class="sxs-lookup"><span data-stu-id="58b6e-120">Visual Basic Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="58b6e-121">检索存储在特性中的信息</span><span class="sxs-lookup"><span data-stu-id="58b6e-121">Retrieving Information Stored in Attributes</span></span>](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)
- [<span data-ttu-id="58b6e-122">反射 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58b6e-122">Reflection (Visual Basic)</span></span>](../reflection.md)
- [<span data-ttu-id="58b6e-123">特性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58b6e-123">Attributes (Visual Basic)</span></span>](../../../language-reference/attributes.md)
- [<span data-ttu-id="58b6e-124">创建自定义特性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58b6e-124">Creating Custom Attributes (Visual Basic)</span></span>](creating-custom-attributes.md)
