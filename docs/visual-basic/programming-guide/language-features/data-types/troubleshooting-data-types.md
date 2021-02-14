---
description: '了解详细信息：排除数据类型 (Visual Basic) '
title: 数据类型疑难解答
ms.date: 07/20/2015
helpviewer_keywords:
- Char data type [Visual Basic], converting
- Decimal data type [Visual Basic], conversions
- data types [Visual Basic], troubleshooting
- literals [Visual Basic], default types
- type characters [Visual Basic], literal
- Mod operator [Visual Basic], in floating-point operations
- troubleshooting Visual Basic, data types
- troubleshooting data types [Visual Basic]
- floating-point numbers [Visual Basic], precision
- Boolean data type [Visual Basic], converting
- literal types [Visual Basic]
- literal type characters [Visual Basic]
- floating-point numbers [Visual Basic], imprecision
- String data type [Visual Basic], converting
- floating-point numbers [Visual Basic], comparison
- floating-point numbers
ms.assetid: 90040d67-b630-4125-a6ae-37195b079042
ms.openlocfilehash: 417a71e88dcd0bfb0c6582ee6304a64871640255
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100463840"
---
# <a name="troubleshooting-data-types-visual-basic"></a><span data-ttu-id="043e0-103">数据类型疑难解答 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="043e0-103">Troubleshooting Data Types (Visual Basic)</span></span>

<span data-ttu-id="043e0-104">此页列出了对内部数据类型执行操作时可能出现的一些常见问题。</span><span class="sxs-lookup"><span data-stu-id="043e0-104">This page lists some common problems that can occur when you perform operations on intrinsic data types.</span></span>

## <a name="floating-point-expressions-do-not-compare-as-equal"></a><span data-ttu-id="043e0-105">Floating-Point 表达式的比较结果不相等</span><span class="sxs-lookup"><span data-stu-id="043e0-105">Floating-Point Expressions Do Not Compare as Equal</span></span>

<span data-ttu-id="043e0-106">使用浮点数字 ([单数据类型](../../../language-reference/data-types/single-data-type.md) 和 [Double 数据类型](../../../language-reference/data-types/double-data-type.md)) 时，请记住，它们存储为二进制小数。</span><span class="sxs-lookup"><span data-stu-id="043e0-106">When you work with floating-point numbers ([Single Data Type](../../../language-reference/data-types/single-data-type.md) and [Double Data Type](../../../language-reference/data-types/double-data-type.md)), remember that they are stored as binary fractions.</span></span> <span data-ttu-id="043e0-107">这意味着，它们不能将不是二进制小数的任何数量的精确表示形式 (k/ (2 ^ n) ，其中 k 和 n 是) 整数。</span><span class="sxs-lookup"><span data-stu-id="043e0-107">This means they cannot hold an exact representation of any quantity that is not a binary fraction (of the form k / (2 ^ n) where k and n are integers).</span></span> <span data-ttu-id="043e0-108">例如，0.5 (= 1/2) 并且 0.3125 (= 5/16) 可以作为精确值保留，而 0.2 (= 1/5) 和 0.3 (= 3/10) 只能是近似值。</span><span class="sxs-lookup"><span data-stu-id="043e0-108">For example, 0.5 (= 1/2) and 0.3125 (= 5/16) can be held as precise values, whereas 0.2 (= 1/5) and 0.3 (= 3/10) can be only approximations.</span></span>

<span data-ttu-id="043e0-109">由于此不精确性，在对浮点值进行操作时，不能依赖于准确的结果。</span><span class="sxs-lookup"><span data-stu-id="043e0-109">Because of this imprecision, you cannot rely on exact results when you operate on floating-point values.</span></span> <span data-ttu-id="043e0-110">具体而言，理论上相等的两个值可能具有略微不同的表示形式。</span><span class="sxs-lookup"><span data-stu-id="043e0-110">In particular, two values that are theoretically equal might have slightly different representations.</span></span>

| <span data-ttu-id="043e0-111">比较浮点数量</span><span class="sxs-lookup"><span data-stu-id="043e0-111">To compare floating-point quantities</span></span> |
|---|
|<span data-ttu-id="043e0-112">1. 通过使用 <xref:System.Math.Abs%2A> <xref:System.Math> 命名空间中类的方法来计算其差异的绝对值 <xref:System> 。</span><span class="sxs-lookup"><span data-stu-id="043e0-112">1.  Calculate the absolute value of their difference by using the <xref:System.Math.Abs%2A> method of the <xref:System.Math> class in the <xref:System> namespace.</span></span><br /><span data-ttu-id="043e0-113">2. 确定可接受的最大值，以便在其差异不大时，可以将两个数量视为适用于实用目的。</span><span class="sxs-lookup"><span data-stu-id="043e0-113">2.  Determine an acceptable maximum difference, such that you can consider the two quantities to be equal for practical purposes if their difference is no larger.</span></span><br /><span data-ttu-id="043e0-114">3. 将差异的绝对值与可接受的差异进行比较。</span><span class="sxs-lookup"><span data-stu-id="043e0-114">3.  Compare the absolute value of the difference to the acceptable difference.</span></span>|

<span data-ttu-id="043e0-115">下面的示例演示了两个值的错误和正确比较 `Double` 。</span><span class="sxs-lookup"><span data-stu-id="043e0-115">The following example demonstrates both incorrect and correct comparison of two `Double` values.</span></span>

[!code-vb[VbVbalrDataTypes#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#10)]

<span data-ttu-id="043e0-116">上面的示例使用 <xref:System.Double.ToString%2A> 结构的方法， <xref:System.Double> 以便它可以指定比关键字使用更好的精度 `CStr` 。</span><span class="sxs-lookup"><span data-stu-id="043e0-116">The previous example uses the <xref:System.Double.ToString%2A> method of the <xref:System.Double> structure so that it can specify better  precision than the `CStr` keyword uses.</span></span> <span data-ttu-id="043e0-117">默认值为15个数字，但 "G17" 格式将其扩展为17位数字。</span><span class="sxs-lookup"><span data-stu-id="043e0-117">The default is 15 digits, but the "G17" format extends it to 17 digits.</span></span>

## <a name="mod-operator-does-not-return-accurate-result"></a><span data-ttu-id="043e0-118">Mod 运算符未返回准确的结果</span><span class="sxs-lookup"><span data-stu-id="043e0-118">Mod Operator Does Not Return Accurate Result</span></span>

<span data-ttu-id="043e0-119">由于浮点存储的不精确性，如果至少有一个操作数为浮点，则 [Mod 运算符](../../../language-reference/operators/mod-operator.md) 可能会返回意外的结果。</span><span class="sxs-lookup"><span data-stu-id="043e0-119">Because of the imprecision of floating-point storage, the [Mod Operator](../../../language-reference/operators/mod-operator.md) can return an unexpected result when at least one of the operands is floating-point.</span></span>

<span data-ttu-id="043e0-120">[Decimal 数据类型](../../../language-reference/data-types/decimal-data-type.md)不使用浮点表示形式。</span><span class="sxs-lookup"><span data-stu-id="043e0-120">The [Decimal Data Type](../../../language-reference/data-types/decimal-data-type.md) does not use floating-point representation.</span></span> <span data-ttu-id="043e0-121">许多在和中不精确的数字 `Single` `Double` `Decimal` (例如0.2 和 0.3) 。</span><span class="sxs-lookup"><span data-stu-id="043e0-121">Many numbers that are inexact in `Single` and `Double` are exact in `Decimal` (for example 0.2 and 0.3).</span></span> <span data-ttu-id="043e0-122">尽管算术 `Decimal` 比浮点时间慢，但其性能可能会降低，从而获得更好的精度。</span><span class="sxs-lookup"><span data-stu-id="043e0-122">Although arithmetic is slower in `Decimal` than in floating-point, it might be worth the performance decrease to achieve better precision.</span></span>

|<span data-ttu-id="043e0-123">查找浮点数量的整数余数</span><span class="sxs-lookup"><span data-stu-id="043e0-123">To find the integer remainder of floating-point quantities</span></span>|
|---|
|<span data-ttu-id="043e0-124">1. 将变量声明为 `Decimal` 。</span><span class="sxs-lookup"><span data-stu-id="043e0-124">1.  Declare variables as `Decimal`.</span></span><br /><span data-ttu-id="043e0-125">2. 使用文本类型字符将 `D` 文本强制 `Decimal` 置于，以防其值对于数据类型来说太大 `Long` 。</span><span class="sxs-lookup"><span data-stu-id="043e0-125">2.  Use the literal type character `D` to force literals to `Decimal`, in case their values are too large for the `Long` data type.</span></span>|

<span data-ttu-id="043e0-126">下面的示例演示了浮点操作数的潜在不精确性。</span><span class="sxs-lookup"><span data-stu-id="043e0-126">The following example demonstrates the potential imprecision of floating-point operands.</span></span>

[!code-vb[VbVbalrDataTypes#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#11)]

<span data-ttu-id="043e0-127">上面的示例使用 <xref:System.Double.ToString%2A> 结构的方法， <xref:System.Double> 以便它可以指定比关键字使用更好的精度 `CStr` 。</span><span class="sxs-lookup"><span data-stu-id="043e0-127">The previous example uses the <xref:System.Double.ToString%2A> method of the <xref:System.Double> structure so that it can specify better precision than the `CStr` keyword uses.</span></span> <span data-ttu-id="043e0-128">默认值为15个数字，但 "G17" 格式将其扩展为17位数字。</span><span class="sxs-lookup"><span data-stu-id="043e0-128">The default is 15 digits, but the "G17" format extends it to 17 digits.</span></span>

<span data-ttu-id="043e0-129">因为 `zeroPointTwo` 为 `Double` ，所以，0.2 的值是0.20000000000000001 的存储值的无限重复二进制小数。</span><span class="sxs-lookup"><span data-stu-id="043e0-129">Because `zeroPointTwo` is `Double`, its value for 0.2 is an infinitely repeating binary fraction with a stored value of 0.20000000000000001.</span></span> <span data-ttu-id="043e0-130">此数量相除2.0 将产生9.9999999999999995，剩余0.19999999999999991。</span><span class="sxs-lookup"><span data-stu-id="043e0-130">Dividing 2.0 by this quantity yields 9.9999999999999995 with a remainder of 0.19999999999999991.</span></span>

<span data-ttu-id="043e0-131">在的表达式中 `decimalRemainder` ，文本类型字符 `D` 强制两个操作数为 `Decimal` ，0.2 具有精确的表示形式。</span><span class="sxs-lookup"><span data-stu-id="043e0-131">In the expression for `decimalRemainder`, the literal type character `D` forces both operands to `Decimal`, and 0.2 has a precise representation.</span></span> <span data-ttu-id="043e0-132">因此， `Mod` 运算符产生了预计的0.0 余数。</span><span class="sxs-lookup"><span data-stu-id="043e0-132">Therefore the `Mod` operator yields the expected remainder of 0.0.</span></span>

<span data-ttu-id="043e0-133">请注意，声明为是不够的 `decimalRemainder` `Decimal` 。</span><span class="sxs-lookup"><span data-stu-id="043e0-133">Note that it is not sufficient to declare `decimalRemainder` as `Decimal`.</span></span> <span data-ttu-id="043e0-134">您还必须强制文本 `Decimal` ，或者默认使用， `Double` 并 `decimalRemainder` 接收与相同的不准确值 `doubleRemainder` 。</span><span class="sxs-lookup"><span data-stu-id="043e0-134">You must also force the literals to `Decimal`, or they use `Double` by default and `decimalRemainder` receives the same inaccurate value as `doubleRemainder`.</span></span>

## <a name="boolean-type-does-not-convert-to-numeric-type-accurately"></a><span data-ttu-id="043e0-135">布尔类型不会准确地转换为数值类型</span><span class="sxs-lookup"><span data-stu-id="043e0-135">Boolean Type Does Not Convert to Numeric Type Accurately</span></span>

<span data-ttu-id="043e0-136">[布尔数据类型](../../../language-reference/data-types/boolean-data-type.md) 值不会存储为数字，并且存储的值不应与数字等效。</span><span class="sxs-lookup"><span data-stu-id="043e0-136">[Boolean Data Type](../../../language-reference/data-types/boolean-data-type.md) values are not stored as numbers, and the stored values are not intended to be equivalent to numbers.</span></span> <span data-ttu-id="043e0-137">为了与早期版本兼容，Visual Basic 提供 ([CType 函数](../../../language-reference/functions/ctype-function.md)、、等的转换关键字， `CBool` `CInt`) 在 `Boolean` 和数值类型之间进行转换。</span><span class="sxs-lookup"><span data-stu-id="043e0-137">For compatibility with earlier versions, Visual Basic provides conversion keywords ([CType Function](../../../language-reference/functions/ctype-function.md), `CBool`, `CInt`, and so on) to convert between `Boolean` and numeric types.</span></span> <span data-ttu-id="043e0-138">但是，其他语言有时会以不同的方式执行这些转换，这与 .NET Framework 方法相同。</span><span class="sxs-lookup"><span data-stu-id="043e0-138">However, other languages sometimes perform these conversions differently, as do the .NET Framework methods.</span></span>

<span data-ttu-id="043e0-139">永远不应编写依赖于和的等效数值的代码 `True` `False` 。</span><span class="sxs-lookup"><span data-stu-id="043e0-139">You should never write code that relies on equivalent numeric values for `True` and `False`.</span></span> <span data-ttu-id="043e0-140">应尽可能将变量的使用限制 `Boolean` 为它们的设计逻辑值。</span><span class="sxs-lookup"><span data-stu-id="043e0-140">Whenever possible, you should restrict usage of `Boolean` variables to the logical values for which they are designed.</span></span> <span data-ttu-id="043e0-141">如果必须混合 `Boolean` 和数值，请确保了解所选的转换方法。</span><span class="sxs-lookup"><span data-stu-id="043e0-141">If you must mix `Boolean` and numeric values, make sure that you understand the conversion method that you select.</span></span>

### <a name="conversion-in-visual-basic"></a><span data-ttu-id="043e0-142">Visual Basic 中的转换</span><span class="sxs-lookup"><span data-stu-id="043e0-142">Conversion in Visual Basic</span></span>

<span data-ttu-id="043e0-143">如果使用 `CType` 或 `CBool` 转换关键字将数值数据类型转换为，则 `Boolean` 0 变为， `False` 所有其他值将变为 `True` 。</span><span class="sxs-lookup"><span data-stu-id="043e0-143">When you use the `CType` or `CBool` conversion keywords to convert numeric data types to `Boolean`, 0 becomes `False` and all other values become `True`.</span></span> <span data-ttu-id="043e0-144">`Boolean`使用转换关键字将值转换为数值类型时，将 `False` 变为0，并 `True` 变为-1。</span><span class="sxs-lookup"><span data-stu-id="043e0-144">When you convert `Boolean` values to numeric types by using the conversion keywords, `False` becomes 0 and `True` becomes -1.</span></span>

### <a name="conversion-in-the-framework"></a><span data-ttu-id="043e0-145">框架中的转换</span><span class="sxs-lookup"><span data-stu-id="043e0-145">Conversion in the Framework</span></span>

<span data-ttu-id="043e0-146"><xref:System.Convert.ToInt32%2A> <xref:System.Convert> 命名空间中的类的方法 <xref:System> 将转换 `True` 为 + 1。</span><span class="sxs-lookup"><span data-stu-id="043e0-146">The <xref:System.Convert.ToInt32%2A> method of the <xref:System.Convert> class in the <xref:System> namespace converts `True` to +1.</span></span>

<span data-ttu-id="043e0-147">如果必须将值转换 `Boolean` 为数值数据类型，请注意使用哪种转换方法。</span><span class="sxs-lookup"><span data-stu-id="043e0-147">If you must convert a `Boolean` value to a numeric data type, be careful about which conversion method you use.</span></span>

## <a name="character-literal-generates-compiler-error"></a><span data-ttu-id="043e0-148">字符文本生成编译器错误</span><span class="sxs-lookup"><span data-stu-id="043e0-148">Character Literal Generates Compiler Error</span></span>

<span data-ttu-id="043e0-149">如果没有任何类型的字符，Visual Basic 会假设文本的默认数据类型。</span><span class="sxs-lookup"><span data-stu-id="043e0-149">In the absence of any type characters, Visual Basic assumes default data types for literals.</span></span> <span data-ttu-id="043e0-150">字符文本的默认类型（用引号引起来 `" "`)  (）为 `String` 。</span><span class="sxs-lookup"><span data-stu-id="043e0-150">The default type for a character literal — enclosed in quotation marks (`" "`) — is `String`.</span></span>

<span data-ttu-id="043e0-151">`String`数据类型不会扩大到[Char 数据类型](../../../language-reference/data-types/char-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="043e0-151">The `String` data type does not widen to the [Char Data Type](../../../language-reference/data-types/char-data-type.md).</span></span> <span data-ttu-id="043e0-152">这意味着，如果要将文本分配给 `Char` 变量，则必须进行收缩转换或将文本强制转换为 `Char` 类型。</span><span class="sxs-lookup"><span data-stu-id="043e0-152">This means that if you want to assign a literal to a `Char` variable, you must either make a narrowing conversion or force the literal to the `Char` type.</span></span>

|<span data-ttu-id="043e0-153">创建要分配给变量或常量的 Char 文本</span><span class="sxs-lookup"><span data-stu-id="043e0-153">To create a Char literal to assign to a variable or constant</span></span>|
|---|
|<span data-ttu-id="043e0-154">1. 将变量或常数声明为 `Char` 。</span><span class="sxs-lookup"><span data-stu-id="043e0-154">1.  Declare the variable or constant as `Char`.</span></span><br /><span data-ttu-id="043e0-155">2. 将字符值用引号引起来 (`" "`) 。</span><span class="sxs-lookup"><span data-stu-id="043e0-155">2.  Enclose the character value in quotation marks (`" "`).</span></span><br /><span data-ttu-id="043e0-156">3. 在右双引号后跟文本类型字符 `C` ，以强制实施文本 `Char` 。</span><span class="sxs-lookup"><span data-stu-id="043e0-156">3.  Follow the closing double quotation mark with the literal type character `C` to force the literal to `Char`.</span></span> <span data-ttu-id="043e0-157">如果类型检查开关 ([Option Strict 语句](../../../language-reference/statements/option-strict-statement.md)) 为，则这是必需的 `On` ，在任何情况下都是必需的。</span><span class="sxs-lookup"><span data-stu-id="043e0-157">This is necessary if the type checking switch ([Option Strict Statement](../../../language-reference/statements/option-strict-statement.md)) is `On`, and it is desirable in any case.</span></span>|

<span data-ttu-id="043e0-158">下面的示例演示了将文本成功和成功分配给变量的情况 `Char` 。</span><span class="sxs-lookup"><span data-stu-id="043e0-158">The following example demonstrates both unsuccessful and successful assignments of a literal to a `Char` variable.</span></span>

[!code-vb[VbVbalrDataTypes#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#12)]

<span data-ttu-id="043e0-159">使用收缩转换始终存在风险，因为它们可能会在运行时失败。</span><span class="sxs-lookup"><span data-stu-id="043e0-159">There is always a risk in using narrowing conversions, because they can fail at run time.</span></span> <span data-ttu-id="043e0-160">例如， `String` 如果值包含多个字符，则从到的转换 `Char` 可能会失败 `String` 。</span><span class="sxs-lookup"><span data-stu-id="043e0-160">For example, a conversion from `String` to `Char` can fail if the `String` value contains more than one character.</span></span> <span data-ttu-id="043e0-161">因此，更好的编程方法是使用 `C` 类型字符。</span><span class="sxs-lookup"><span data-stu-id="043e0-161">Therefore, it is better programming to use the `C` type character.</span></span>

## <a name="string-conversion-fails-at-run-time"></a><span data-ttu-id="043e0-162">字符串转换在运行时失败</span><span class="sxs-lookup"><span data-stu-id="043e0-162">String Conversion Fails at Run Time</span></span>

<span data-ttu-id="043e0-163">[字符串数据类型](../../../language-reference/data-types/string-data-type.md)参与极少的扩大转换。</span><span class="sxs-lookup"><span data-stu-id="043e0-163">The [String Data Type](../../../language-reference/data-types/string-data-type.md) participates in very few widening conversions.</span></span> <span data-ttu-id="043e0-164">`String` 仅扩大到其自身和 `Object` ，并且只有 `Char` 并 `Char()` (`Char`) 扩大到的数组 `String` 。</span><span class="sxs-lookup"><span data-stu-id="043e0-164">`String` widens only to itself and `Object`, and only `Char` and `Char()` (a `Char` array) widen to `String`.</span></span> <span data-ttu-id="043e0-165">这是因为 `String` 变量和常量可以包含其他数据类型不能包含的值。</span><span class="sxs-lookup"><span data-stu-id="043e0-165">This is because `String` variables and constants can contain values that other data types cannot contain.</span></span>

<span data-ttu-id="043e0-166">如果类型检查开关 ([Option Strict 语句](../../../language-reference/statements/option-strict-statement.md)) 为 `On` ，则编译器不允许所有隐式收缩转换。</span><span class="sxs-lookup"><span data-stu-id="043e0-166">When the type checking switch ([Option Strict Statement](../../../language-reference/statements/option-strict-statement.md)) is `On`, the compiler disallows all implicit narrowing conversions.</span></span> <span data-ttu-id="043e0-167">这包括涉及的内容 `String` 。</span><span class="sxs-lookup"><span data-stu-id="043e0-167">This includes those involving `String`.</span></span> <span data-ttu-id="043e0-168">你的代码仍可使用转换关键字（如 `CStr` 和 [CType 函数](../../../language-reference/functions/ctype-function.md)）来指示 .NET Framework 尝试转换。</span><span class="sxs-lookup"><span data-stu-id="043e0-168">Your code can still use conversion keywords such as `CStr` and [CType Function](../../../language-reference/functions/ctype-function.md), which direct the .NET Framework to attempt the conversion.</span></span>

> [!NOTE]
> <span data-ttu-id="043e0-169">禁止将从集合中的元素转换 `For Each…Next` 为循环控制变量的收缩转换错误。</span><span class="sxs-lookup"><span data-stu-id="043e0-169">The narrowing-conversion error is suppressed for conversions from the elements in a `For Each…Next` collection to the loop control variable.</span></span> <span data-ttu-id="043e0-170">有关详细信息和示例，请参阅中的 "收缩转换" 一节 [。下一语句](../../../language-reference/statements/for-each-next-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="043e0-170">For more information and examples, see the "Narrowing Conversions" section in [For Each...Next Statement](../../../language-reference/statements/for-each-next-statement.md).</span></span>

### <a name="narrowing-conversion-protection"></a><span data-ttu-id="043e0-171">收缩转换保护</span><span class="sxs-lookup"><span data-stu-id="043e0-171">Narrowing Conversion Protection</span></span>

<span data-ttu-id="043e0-172">收缩转换的缺点是它们可能会在运行时失败。</span><span class="sxs-lookup"><span data-stu-id="043e0-172">The disadvantage of narrowing conversions is that they can fail at run time.</span></span> <span data-ttu-id="043e0-173">例如，如果 `String` 变量包含除 "True" 或 "False" 之外的任何值，则不能将其转换为 `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="043e0-173">For example, if a `String` variable contains anything other than "True" or "False," it cannot be converted to `Boolean`.</span></span> <span data-ttu-id="043e0-174">如果包含标点字符，则转换为任意数值类型的操作都将失败。</span><span class="sxs-lookup"><span data-stu-id="043e0-174">If it contains punctuation characters, conversion to any numeric type fails.</span></span> <span data-ttu-id="043e0-175">除非您知道 `String` 变量始终包含目标类型可以接受的值，否则不应尝试转换。</span><span class="sxs-lookup"><span data-stu-id="043e0-175">Unless you know that your `String` variable always holds values that the destination type can accept, you should not try a conversion.</span></span>

<span data-ttu-id="043e0-176">如果必须从转换 `String` 为另一种数据类型，最安全的过程是将尝试的转换包含在 [Try .。。Catch .。。Finally 语句](../../../language-reference/statements/try-catch-finally-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="043e0-176">If you must convert from `String` to another data type, the safest procedure is to enclose the attempted conversion in the [Try...Catch...Finally Statement](../../../language-reference/statements/try-catch-finally-statement.md).</span></span> <span data-ttu-id="043e0-177">这使你可以处理运行时失败。</span><span class="sxs-lookup"><span data-stu-id="043e0-177">This lets you deal with a run-time failure.</span></span>

### <a name="character-arrays"></a><span data-ttu-id="043e0-178">字符数组</span><span class="sxs-lookup"><span data-stu-id="043e0-178">Character Arrays</span></span>

<span data-ttu-id="043e0-179">一个 `Char` 元素和一个数组， `Char` 它们都扩大到 `String` 。</span><span class="sxs-lookup"><span data-stu-id="043e0-179">A single `Char` and an array of `Char` elements both widen to `String`.</span></span> <span data-ttu-id="043e0-180">但是，不 `String` 会扩大到 `Char()` 。</span><span class="sxs-lookup"><span data-stu-id="043e0-180">However, `String` does not widen to `Char()`.</span></span> <span data-ttu-id="043e0-181">若要将 `String` 值转换为 `Char` 数组，可以使用类的 <xref:System.String.ToCharArray%2A> 方法 <xref:System.String?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="043e0-181">To convert a `String` value to a `Char` array, you can use the <xref:System.String.ToCharArray%2A> method of the <xref:System.String?displayProperty=nameWithType> class.</span></span>

### <a name="meaningless-values"></a><span data-ttu-id="043e0-182">无意义值</span><span class="sxs-lookup"><span data-stu-id="043e0-182">Meaningless Values</span></span>

<span data-ttu-id="043e0-183">通常情况下， `String` 值在其他数据类型中没有意义，转换非常有意义。</span><span class="sxs-lookup"><span data-stu-id="043e0-183">In general, `String` values are not meaningful in other data types, and conversion is highly artificial and dangerous.</span></span> <span data-ttu-id="043e0-184">应尽可能将变量的使用限制 `String` 为为其设计的字符序列。</span><span class="sxs-lookup"><span data-stu-id="043e0-184">Whenever possible, you should restrict usage of `String` variables to the character sequences for which they are designed.</span></span> <span data-ttu-id="043e0-185">永远不应编写依赖于其他类型中的等效值的代码。</span><span class="sxs-lookup"><span data-stu-id="043e0-185">You should never write code that relies on equivalent values in other types.</span></span>

## <a name="see-also"></a><span data-ttu-id="043e0-186">请参阅</span><span class="sxs-lookup"><span data-stu-id="043e0-186">See also</span></span>

- [<span data-ttu-id="043e0-187">数据类型</span><span class="sxs-lookup"><span data-stu-id="043e0-187">Data Types</span></span>](index.md)
- [<span data-ttu-id="043e0-188">类型字符</span><span class="sxs-lookup"><span data-stu-id="043e0-188">Type Characters</span></span>](type-characters.md)
- [<span data-ttu-id="043e0-189">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="043e0-189">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="043e0-190">Visual Basic 中的类型转换</span><span class="sxs-lookup"><span data-stu-id="043e0-190">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="043e0-191">数据类型</span><span class="sxs-lookup"><span data-stu-id="043e0-191">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="043e0-192">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="043e0-192">Type Conversion Functions</span></span>](../../../language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="043e0-193">有效使用数据类型</span><span class="sxs-lookup"><span data-stu-id="043e0-193">Efficient Use of Data Types</span></span>](efficient-use-of-data-types.md)
