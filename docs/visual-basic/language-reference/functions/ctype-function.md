---
description: '详细了解： CType 函数 (Visual Basic) '
title: CType Function
ms.date: 07/20/2015
f1_keywords:
- vb.CType
helpviewer_keywords:
- expression conversion results
- explicit data type conversions [Visual Basic]
- CType function
- conversions [Visual Basic], expression
ms.assetid: dd4b29e7-6fa1-428c-877e-69955420bb72
ms.openlocfilehash: 9732f52b40e5f762769ba5dc340c000e7e1ba17a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701256"
---
# <a name="ctype-function-visual-basic"></a><span data-ttu-id="6bac3-103">CType 函数 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6bac3-103">CType Function (Visual Basic)</span></span>

<span data-ttu-id="6bac3-104">返回将表达式显式转换为指定的数据类型、对象、结构、类或接口的结果。</span><span class="sxs-lookup"><span data-stu-id="6bac3-104">Returns the result of explicitly converting an expression to a specified data type, object, structure, class, or interface.</span></span>

## <a name="syntax"></a><span data-ttu-id="6bac3-105">语法</span><span class="sxs-lookup"><span data-stu-id="6bac3-105">Syntax</span></span>

```vb
CType(expression, typename)
```

## <a name="parts"></a><span data-ttu-id="6bac3-106">组成部分</span><span class="sxs-lookup"><span data-stu-id="6bac3-106">Parts</span></span>

<span data-ttu-id="6bac3-107">`expression` 任何有效的表达式。</span><span class="sxs-lookup"><span data-stu-id="6bac3-107">`expression` Any valid expression.</span></span> <span data-ttu-id="6bac3-108">如果的值 `expression` 超出了所允许的范围 `typename` ，Visual Basic 会引发异常。</span><span class="sxs-lookup"><span data-stu-id="6bac3-108">If the value of `expression` is outside the range allowed by `typename`, Visual Basic throws an exception.</span></span>

<span data-ttu-id="6bac3-109">`typename` 语句中子句内合法的任何表达式，即 `As` `Dim` 任何数据类型、对象、结构、类或接口的名称。</span><span class="sxs-lookup"><span data-stu-id="6bac3-109">`typename` Any expression that is legal within an `As` clause in a `Dim` statement, that is, the name of any data type, object, structure, class, or interface.</span></span>

## <a name="remarks"></a><span data-ttu-id="6bac3-110">备注</span><span class="sxs-lookup"><span data-stu-id="6bac3-110">Remarks</span></span>

> [!TIP]
> <span data-ttu-id="6bac3-111">你还可以使用以下函数来执行类型转换：</span><span class="sxs-lookup"><span data-stu-id="6bac3-111">You can also use the following functions to perform a type conversion:</span></span>
>
> - <span data-ttu-id="6bac3-112">类型转换函数，例如 `CByte` 、 `CDbl` 和， `CInt` 它们执行到特定数据类型的转换。</span><span class="sxs-lookup"><span data-stu-id="6bac3-112">Type conversion functions such as `CByte`, `CDbl`, and `CInt` that perform a conversion to a specific data type.</span></span> <span data-ttu-id="6bac3-113">有关详细信息，请参阅 [Type Conversion Functions](type-conversion-functions.md)（类型转换函数）。</span><span class="sxs-lookup"><span data-stu-id="6bac3-113">For more information, see [Type Conversion Functions](type-conversion-functions.md).</span></span>
> - <span data-ttu-id="6bac3-114">[DirectCast 运算符](../operators/directcast-operator.md) 或 [TryCast 运算符](../operators/trycast-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="6bac3-114">[DirectCast Operator](../operators/directcast-operator.md) or [TryCast Operator](../operators/trycast-operator.md).</span></span> <span data-ttu-id="6bac3-115">这些运算符要求一个类型继承自或实现另一个类型。</span><span class="sxs-lookup"><span data-stu-id="6bac3-115">These operators require that one type inherit from or implement the other type.</span></span> <span data-ttu-id="6bac3-116">与在 `CType` 数据类型之间进行转换相比，它们可以提供更好的性能 `Object` 。</span><span class="sxs-lookup"><span data-stu-id="6bac3-116">They can provide somewhat better performance than `CType` when converting to and from the `Object` data type.</span></span>

<span data-ttu-id="6bac3-117">`CType` 是内联编译的，这意味着转换代码是计算表达式的代码的一部分。</span><span class="sxs-lookup"><span data-stu-id="6bac3-117">`CType` is compiled inline, which means that the conversion code is part of the code that evaluates the expression.</span></span> <span data-ttu-id="6bac3-118">在某些情况下，代码运行速度更快，因为没有调用任何过程来执行转换。</span><span class="sxs-lookup"><span data-stu-id="6bac3-118">In some cases, the code runs faster because no procedures are called to perform the conversion.</span></span>

<span data-ttu-id="6bac3-119">如果未定义从到的 `expression` 转换 `typename` (例如，从 `Integer` 到 `Date`) ，Visual Basic 将显示编译时错误消息。</span><span class="sxs-lookup"><span data-stu-id="6bac3-119">If no conversion is defined from `expression` to `typename` (for example, from `Integer` to `Date`), Visual Basic displays a compile-time error message.</span></span>

<span data-ttu-id="6bac3-120">如果转换在运行时失败，则会引发相应的异常。</span><span class="sxs-lookup"><span data-stu-id="6bac3-120">If a conversion fails at run time, the appropriate exception is thrown.</span></span> <span data-ttu-id="6bac3-121">如果收缩转换失败， <xref:System.OverflowException> 最常见的结果是。</span><span class="sxs-lookup"><span data-stu-id="6bac3-121">If a narrowing conversion fails, an <xref:System.OverflowException> is the most common result.</span></span> <span data-ttu-id="6bac3-122">如果未定义转换，则会 <xref:System.InvalidCastException> 引发。</span><span class="sxs-lookup"><span data-stu-id="6bac3-122">If the conversion is undefined, an <xref:System.InvalidCastException> in thrown.</span></span> <span data-ttu-id="6bac3-123">例如，如果 `expression` 的类型为 `Object` 且其运行时类型没有转换为，则可能会发生这种情况 `typename` 。</span><span class="sxs-lookup"><span data-stu-id="6bac3-123">For example, this can happen  if `expression` is of type `Object` and its run-time type has no conversion to `typename`.</span></span>

<span data-ttu-id="6bac3-124">如果或的数据类型 `expression` `typename` 是你定义的类或结构，则可以 `CType` 将该类或结构的定义为转换运算符。</span><span class="sxs-lookup"><span data-stu-id="6bac3-124">If the data type of `expression` or `typename` is a class or structure you've defined, you can define `CType` on that class or structure as a conversion operator.</span></span> <span data-ttu-id="6bac3-125">这会使作为 `CType` *重载运算符*。</span><span class="sxs-lookup"><span data-stu-id="6bac3-125">This makes `CType` act as an *overloaded operator*.</span></span> <span data-ttu-id="6bac3-126">如果执行此操作，则可以控制与类或结构的转换的行为，包括可能引发的异常。</span><span class="sxs-lookup"><span data-stu-id="6bac3-126">If you do this, you can control the behavior of conversions to and from your class or structure, including the exceptions that can be thrown.</span></span>

## <a name="overloading"></a><span data-ttu-id="6bac3-127">重载</span><span class="sxs-lookup"><span data-stu-id="6bac3-127">Overloading</span></span>

<span data-ttu-id="6bac3-128">`CType`还可以在代码外部定义的类或结构上重载运算符。</span><span class="sxs-lookup"><span data-stu-id="6bac3-128">The `CType` operator can also be overloaded on a class or structure defined outside your code.</span></span> <span data-ttu-id="6bac3-129">如果你的代码在此类或结构之间进行转换，请确保了解其运算符的行为 `CType` 。</span><span class="sxs-lookup"><span data-stu-id="6bac3-129">If your code converts to or from such a class or structure, be sure you understand the behavior of its `CType` operator.</span></span> <span data-ttu-id="6bac3-130">有关详细信息，请参阅 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="6bac3-130">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>

## <a name="converting-dynamic-objects"></a><span data-ttu-id="6bac3-131">转换动态对象</span><span class="sxs-lookup"><span data-stu-id="6bac3-131">Converting Dynamic Objects</span></span>

<span data-ttu-id="6bac3-132">动态对象的类型转换由使用或方法的用户定义的动态转换执行 <xref:System.Dynamic.DynamicObject.TryConvert%2A> <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> 。</span><span class="sxs-lookup"><span data-stu-id="6bac3-132">Type conversions of dynamic objects are performed by user-defined dynamic conversions that use the <xref:System.Dynamic.DynamicObject.TryConvert%2A> or <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> methods.</span></span> <span data-ttu-id="6bac3-133">如果使用的是动态对象，请使用 <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> 方法转换动态对象。</span><span class="sxs-lookup"><span data-stu-id="6bac3-133">If you're working with dynamic objects, use the <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> method to convert the dynamic object.</span></span>

## <a name="example"></a><span data-ttu-id="6bac3-134">示例</span><span class="sxs-lookup"><span data-stu-id="6bac3-134">Example</span></span>

<span data-ttu-id="6bac3-135">下面的示例使用 `CType` 函数将表达式转换为 `Single` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="6bac3-135">The following example uses the `CType` function to convert an expression to the `Single` data type.</span></span>

[!code-vb[VbVbalrFunctions#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#24)]

<span data-ttu-id="6bac3-136">有关其他示例，请参阅 [隐式和显式转换](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="6bac3-136">For additional examples, see [Implicit and Explicit Conversions](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6bac3-137">请参阅</span><span class="sxs-lookup"><span data-stu-id="6bac3-137">See also</span></span>

- <xref:System.OverflowException>
- <xref:System.InvalidCastException>
- [<span data-ttu-id="6bac3-138">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="6bac3-138">Type Conversion Functions</span></span>](type-conversion-functions.md)
- [<span data-ttu-id="6bac3-139">转换函数</span><span class="sxs-lookup"><span data-stu-id="6bac3-139">Conversion Functions</span></span>](conversion-functions.md)
- [<span data-ttu-id="6bac3-140">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="6bac3-140">Operator Statement</span></span>](../statements/operator-statement.md)
- [<span data-ttu-id="6bac3-141">如何：定义转换运算符</span><span class="sxs-lookup"><span data-stu-id="6bac3-141">How to: Define a Conversion Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="6bac3-142">.NET Framework 中的类型转换</span><span class="sxs-lookup"><span data-stu-id="6bac3-142">Type Conversion in the .NET Framework</span></span>](../../../standard/base-types/type-conversion.md)
