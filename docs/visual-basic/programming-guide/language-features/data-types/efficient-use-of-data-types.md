---
description: '了解更多相关信息：高效使用数据类型 (Visual Basic) '
title: 有效使用数据类型
ms.date: 07/20/2015
helpviewer_keywords:
- performance, data type efficiency
- data types [Visual Basic], weak typing
- AscW function [Visual Basic], preferred to Asc
- data types [Visual Basic], using efficiently
- optimization [Visual Basic], data types
- data types [Visual Basic], strong typing
- strong typing
- typing, strong
- data types [Visual Basic], optimizing
- ChrW function [Visual Basic], preferred to Chr
ms.assetid: 28f5e4ba-ec24-4f37-b90a-e8ee822f778a
ms.openlocfilehash: e7660bbdec530ef18d663975e314d90b64e4b055
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100476431"
---
# <a name="efficient-use-of-data-types-visual-basic"></a><span data-ttu-id="9f761-103">有效使用数据类型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f761-103">Efficient Use of Data Types (Visual Basic)</span></span>

<span data-ttu-id="9f761-104">为未声明的变量和声明的变量分配了数据 `Object` 类型。</span><span class="sxs-lookup"><span data-stu-id="9f761-104">Undeclared variables and variables declared without a data type are assigned the `Object` data type.</span></span> <span data-ttu-id="9f761-105">这样就可以轻松地快速编写程序，但这可能会导致其执行速度更慢。</span><span class="sxs-lookup"><span data-stu-id="9f761-105">This makes it easy to write programs quickly, but it can cause them to execute more slowly.</span></span>

## <a name="strong-typing"></a><span data-ttu-id="9f761-106">强类型化</span><span class="sxs-lookup"><span data-stu-id="9f761-106">Strong Typing</span></span>

 <span data-ttu-id="9f761-107">为所有变量指定数据类型称为 *强* 类型。</span><span class="sxs-lookup"><span data-stu-id="9f761-107">Specifying data types for all your variables is known as *strong typing*.</span></span> <span data-ttu-id="9f761-108">使用强类型具有以下优点：</span><span class="sxs-lookup"><span data-stu-id="9f761-108">Using strong typing has several advantages:</span></span>

- <span data-ttu-id="9f761-109">它为你的变量启用 IntelliSense 支持。</span><span class="sxs-lookup"><span data-stu-id="9f761-109">It enables IntelliSense support for your variables.</span></span> <span data-ttu-id="9f761-110">这使您可以在代码中键入时查看它们的属性和其他成员。</span><span class="sxs-lookup"><span data-stu-id="9f761-110">This allows you to see their properties and other members as you type in the code.</span></span>

- <span data-ttu-id="9f761-111">它利用编译器的类型检查。</span><span class="sxs-lookup"><span data-stu-id="9f761-111">It takes advantage of compiler type checking.</span></span> <span data-ttu-id="9f761-112">这将捕获在运行时可能会因错误（如溢出）而失败的语句。</span><span class="sxs-lookup"><span data-stu-id="9f761-112">This catches statements that can fail at run time due to errors such as overflow.</span></span> <span data-ttu-id="9f761-113">它还会捕获对不支持这些对象的方法的调用。</span><span class="sxs-lookup"><span data-stu-id="9f761-113">It also catches calls to methods on objects that do not support them.</span></span>

- <span data-ttu-id="9f761-114">这会使代码的执行速度更快。</span><span class="sxs-lookup"><span data-stu-id="9f761-114">It results in faster execution of your code.</span></span>

## <a name="most-efficient-data-types"></a><span data-ttu-id="9f761-115">最有效的数据类型</span><span class="sxs-lookup"><span data-stu-id="9f761-115">Most Efficient Data Types</span></span>

 <span data-ttu-id="9f761-116">对于从不包含小数的变量，整型数据类型比非整型数据类型更有效。</span><span class="sxs-lookup"><span data-stu-id="9f761-116">For variables that never contain fractions, the integral data types are more efficient than the nonintegral types.</span></span> <span data-ttu-id="9f761-117">在 Visual Basic 中， `Integer` 和 `UInteger` 是最有效的数值类型。</span><span class="sxs-lookup"><span data-stu-id="9f761-117">In Visual Basic, `Integer` and `UInteger` are the most efficient numeric types.</span></span>

 <span data-ttu-id="9f761-118">对于小数值， `Double` 是最有效的数据类型，因为当前平台上的处理器以双精度执行浮点运算。</span><span class="sxs-lookup"><span data-stu-id="9f761-118">For fractional numbers, `Double` is the most efficient data type, because the processors on current platforms perform floating-point operations in double precision.</span></span> <span data-ttu-id="9f761-119">但是，与整数类型（例如）相比，具有的操作的 `Double` 速度并不像 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="9f761-119">However, operations with `Double` are not as fast as with the integral types such as `Integer`.</span></span>

## <a name="specifying-data-type"></a><span data-ttu-id="9f761-120">指定数据类型</span><span class="sxs-lookup"><span data-stu-id="9f761-120">Specifying Data Type</span></span>

 <span data-ttu-id="9f761-121">使用 [Dim 语句](../../../language-reference/statements/dim-statement.md) 声明特定类型的变量。</span><span class="sxs-lookup"><span data-stu-id="9f761-121">Use the [Dim Statement](../../../language-reference/statements/dim-statement.md) to declare a variable of a specific type.</span></span> <span data-ttu-id="9f761-122">可以使用 [Public](../../../language-reference/modifiers/public.md)、 [Protected](../../../language-reference/modifiers/protected.md)、 [Friend](../../../language-reference/modifiers/friend.md)或 [Private](../../../language-reference/modifiers/private.md) 关键字同时指定其访问级别，如以下示例中所示。</span><span class="sxs-lookup"><span data-stu-id="9f761-122">You can simultaneously specify its access level by using the [Public](../../../language-reference/modifiers/public.md), [Protected](../../../language-reference/modifiers/protected.md), [Friend](../../../language-reference/modifiers/friend.md), or [Private](../../../language-reference/modifiers/private.md) keyword, as in the following example.</span></span>

```vb
Private x As Double
Protected s As String
```

## <a name="character-conversion"></a><span data-ttu-id="9f761-123">字符转换</span><span class="sxs-lookup"><span data-stu-id="9f761-123">Character Conversion</span></span>

 <span data-ttu-id="9f761-124">`AscW`和 `ChrW` 函数以 Unicode 的方式运行。</span><span class="sxs-lookup"><span data-stu-id="9f761-124">The `AscW` and `ChrW` functions operate in Unicode.</span></span> <span data-ttu-id="9f761-125">应优先使用和，以使 `Asc` 它们 `Chr` 必须转换为 Unicode 和 Unicode。</span><span class="sxs-lookup"><span data-stu-id="9f761-125">You should use them in preference to `Asc` and `Chr`, which must translate into and out of Unicode.</span></span>

## <a name="see-also"></a><span data-ttu-id="9f761-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="9f761-126">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [<span data-ttu-id="9f761-127">数据类型</span><span class="sxs-lookup"><span data-stu-id="9f761-127">Data Types</span></span>](index.md)
- [<span data-ttu-id="9f761-128">数值数据类型</span><span class="sxs-lookup"><span data-stu-id="9f761-128">Numeric Data Types</span></span>](numeric-data-types.md)
- [<span data-ttu-id="9f761-129">变量声明</span><span class="sxs-lookup"><span data-stu-id="9f761-129">Variable Declaration</span></span>](../variables/variable-declaration.md)
- [<span data-ttu-id="9f761-130">使用 IntelliSense</span><span class="sxs-lookup"><span data-stu-id="9f761-130">Using IntelliSense</span></span>](/visualstudio/ide/using-intellisense)
