---
title: 浮点数值类型 - C# 引用
description: 了解内置 C# 浮点类型：float、double 和 decimal
ms.date: 02/04/2021
f1_keywords:
- float
- float_CSharpKeyword
- double
- double_CSharpKeyword
- decimal_CSharpKeyword
- decimal
helpviewer_keywords:
- floating-point numbers [C#]
- ranges of floating-point types [C#]
- size of floating-point types [C#]
- types [C#], floating-point types
- float keyword [C#]
- floating-point numbers [C#], float keyword
- double data type [C#]
- decimal keyword [C#]
ms.openlocfilehash: a086e8de60bbb63408c3f2cd557feb36c4baa0f8
ms.sourcegitcommit: 65af0f0ad316858882845391d60ef7e303b756e8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/05/2021
ms.locfileid: "99585749"
---
# <a name="floating-point-numeric-types-c-reference"></a><span data-ttu-id="2ca8d-103">浮点数值类型（C# 引用）</span><span class="sxs-lookup"><span data-stu-id="2ca8d-103">Floating-point numeric types (C# reference)</span></span>

<span data-ttu-id="2ca8d-104">浮点数值类型表示实数。</span><span class="sxs-lookup"><span data-stu-id="2ca8d-104">The *floating-point numeric types* represent real numbers.</span></span> <span data-ttu-id="2ca8d-105">所有浮点型数值类型均为[值类型](value-types.md)。</span><span class="sxs-lookup"><span data-stu-id="2ca8d-105">All floating-point numeric types are [value types](value-types.md).</span></span> <span data-ttu-id="2ca8d-106">它们还是[简单类型](value-types.md#built-in-value-types)，可以使用[文本](#real-literals)进行初始化。</span><span class="sxs-lookup"><span data-stu-id="2ca8d-106">They are also [simple types](value-types.md#built-in-value-types) and can be initialized with [literals](#real-literals).</span></span> <span data-ttu-id="2ca8d-107">所有浮点数值类型都支持[算术](../operators/arithmetic-operators.md)、[比较](../operators/comparison-operators.md)和[相等](../operators/equality-operators.md)运算符。</span><span class="sxs-lookup"><span data-stu-id="2ca8d-107">All floating-point numeric types support [arithmetic](../operators/arithmetic-operators.md), [comparison](../operators/comparison-operators.md), and [equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-floating-point-types"></a><span data-ttu-id="2ca8d-108">浮点类型的特征</span><span class="sxs-lookup"><span data-stu-id="2ca8d-108">Characteristics of the floating-point types</span></span>

<span data-ttu-id="2ca8d-109">C# 支持以下预定义浮点类型：</span><span class="sxs-lookup"><span data-stu-id="2ca8d-109">C# supports the following predefined floating-point types:</span></span>
  
|<span data-ttu-id="2ca8d-110">C# 类型/关键字</span><span class="sxs-lookup"><span data-stu-id="2ca8d-110">C# type/keyword</span></span>|<span data-ttu-id="2ca8d-111">大致范围</span><span class="sxs-lookup"><span data-stu-id="2ca8d-111">Approximate range</span></span>|<span data-ttu-id="2ca8d-112">精度</span><span class="sxs-lookup"><span data-stu-id="2ca8d-112">Precision</span></span>|<span data-ttu-id="2ca8d-113">大小</span><span class="sxs-lookup"><span data-stu-id="2ca8d-113">Size</span></span>|<span data-ttu-id="2ca8d-114">.NET 类型</span><span class="sxs-lookup"><span data-stu-id="2ca8d-114">.NET type</span></span>|
|----------|-----------------------|---------------|--------------|--------------|
|`float`|<span data-ttu-id="2ca8d-115">±1.5 x 10<sup>−45</sup> 至 ±3.4 x 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="2ca8d-115">±1.5 x 10<sup>−45</sup> to ±3.4 x 10<sup>38</sup></span></span>|<span data-ttu-id="2ca8d-116">大约 6-9 位数字</span><span class="sxs-lookup"><span data-stu-id="2ca8d-116">~6-9 digits</span></span>|<span data-ttu-id="2ca8d-117">4 个字节</span><span class="sxs-lookup"><span data-stu-id="2ca8d-117">4 bytes</span></span>|<xref:System.Single?displayProperty=nameWithType>|
|`double`|<span data-ttu-id="2ca8d-118">±5.0 × 10<sup>−324</sup> 到 ±1.7 × 10<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="2ca8d-118">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="2ca8d-119">大约 15-17 位数字</span><span class="sxs-lookup"><span data-stu-id="2ca8d-119">~15-17 digits</span></span>|<span data-ttu-id="2ca8d-120">8 个字节</span><span class="sxs-lookup"><span data-stu-id="2ca8d-120">8 bytes</span></span>|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|<span data-ttu-id="2ca8d-121">±1.0 x 10<sup>-28</sup> 至 ±7.9228 x 10<sup>28</sup></span><span class="sxs-lookup"><span data-stu-id="2ca8d-121">±1.0 x 10<sup>-28</sup> to ±7.9228 x 10<sup>28</sup></span></span>|<span data-ttu-id="2ca8d-122">28-29 位</span><span class="sxs-lookup"><span data-stu-id="2ca8d-122">28-29 digits</span></span>|<span data-ttu-id="2ca8d-123">16 个字节</span><span class="sxs-lookup"><span data-stu-id="2ca8d-123">16 bytes</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|

<span data-ttu-id="2ca8d-124">在上表中，最左侧列中的每个 C# 类型关键字都是相应 .NET 类型的别名。</span><span class="sxs-lookup"><span data-stu-id="2ca8d-124">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="2ca8d-125">它们是可互换的。</span><span class="sxs-lookup"><span data-stu-id="2ca8d-125">They are interchangeable.</span></span> <span data-ttu-id="2ca8d-126">例如，以下声明声明了相同类型的变量：</span><span class="sxs-lookup"><span data-stu-id="2ca8d-126">For example, the following declarations declare variables of the same type:</span></span>

```csharp
double a = 12.3;
System.Double b = 12.3;
```

<span data-ttu-id="2ca8d-127">每个浮点类型的默认值都为零，`0`。</span><span class="sxs-lookup"><span data-stu-id="2ca8d-127">The default value of each floating-point type is zero, `0`.</span></span> <span data-ttu-id="2ca8d-128">每个浮点类型都有 `MinValue` 和 `MaxValue` 常量，提供该类型的最小值和最大有限值。</span><span class="sxs-lookup"><span data-stu-id="2ca8d-128">Each of the floating-point types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum finite value of that type.</span></span> <span data-ttu-id="2ca8d-129">`float` and `double` 类型还提供可表示非数字和无穷大值的常量。</span><span class="sxs-lookup"><span data-stu-id="2ca8d-129">The `float` and `double` types also provide constants that represent not-a-number and infinity values.</span></span> <span data-ttu-id="2ca8d-130">例如，`double` 类型提供以下常量：<xref:System.Double.NaN?displayProperty=nameWithType>、<xref:System.Double.NegativeInfinity?displayProperty=nameWithType> 和 <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="2ca8d-130">For example, the `double` type provides the following constants: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, and <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="2ca8d-131">当所需的精度由小数点右侧的位数决定时，`decimal` 类型是合适的。</span><span class="sxs-lookup"><span data-stu-id="2ca8d-131">The `decimal` type is appropriate when the required degree of precision is determined by the number of digits to the right of the decimal point.</span></span> <span data-ttu-id="2ca8d-132">此类数字通常用于财务应用程序、货币金额（例如 $1.00）、利率（例如 2.625%）等。</span><span class="sxs-lookup"><span data-stu-id="2ca8d-132">Such numbers are commonly used in financial applications, for currency amounts (for example, $1.00), interest rates (for example, 2.625%), and so forth.</span></span> <span data-ttu-id="2ca8d-133">精确到只有一个小数的偶数用 `decimal` 类型处理会更准确：例如，0.1 可以由 `decimal` 实例精确表示，而没有精确表示 0.1 的 `double` 或 `float` 实例。</span><span class="sxs-lookup"><span data-stu-id="2ca8d-133">Even numbers that are precise to only one decimal digit are handled more accurately by the `decimal` type: 0.1, for example, can be exactly represented by a `decimal` instance, while there's no `double` or `float` instance that exactly represents 0.1.</span></span> <span data-ttu-id="2ca8d-134">由于数值类型存在这种差异，因此当你对十进制数据使用 `double` 或 `float` 时，算术计算可能会出现意外的舍入错误。</span><span class="sxs-lookup"><span data-stu-id="2ca8d-134">Because of this difference in numeric types, unexpected rounding errors can occur in arithmetic calculations when you use `double` or `float` for decimal data.</span></span> <span data-ttu-id="2ca8d-135">当优化性能比确保准确度更重要时，可以使用 `double` 代替 `decimal`。</span><span class="sxs-lookup"><span data-stu-id="2ca8d-135">You can use `double` instead of `decimal` when optimizing performance is more important than ensuring accuracy.</span></span> <span data-ttu-id="2ca8d-136">然而，除了大多数计算密集型应用程序之外，所有应用程序都不会注意到性能上的任何差异。</span><span class="sxs-lookup"><span data-stu-id="2ca8d-136">However, any difference in performance would go unnoticed by all but the most calculation-intensive applications.</span></span> <span data-ttu-id="2ca8d-137">避免使用 `decimal` 的另一个可能原因是为了最大限度地降低存储需求。</span><span class="sxs-lookup"><span data-stu-id="2ca8d-137">Another possible reason to avoid `decimal` is to minimize storage requirements.</span></span> <span data-ttu-id="2ca8d-138">例如，[ML.NET](../../../machine-learning/how-does-mldotnet-work.md) 使用 `float`，因为对于非常大的数据集，4 个字节与 16 个字节之间的差异合乎情理。</span><span class="sxs-lookup"><span data-stu-id="2ca8d-138">For example, [ML.NET](../../../machine-learning/how-does-mldotnet-work.md) uses `float` because the difference between 4 bytes and 16 bytes adds up for very large data sets.</span></span> <span data-ttu-id="2ca8d-139">有关详细信息，请参阅 <xref:System.Decimal?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="2ca8d-139">For more information, see <xref:System.Decimal?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="2ca8d-140">可在表达式中将[整型](integral-numeric-types.md)类型与 `float` 和 `double` 类型混合使用功能。</span><span class="sxs-lookup"><span data-stu-id="2ca8d-140">You can mix [integral](integral-numeric-types.md) types and the `float` and `double` types in an expression.</span></span> <span data-ttu-id="2ca8d-141">在这种情况下，整型类型隐式转换为其中一种浮点类型，且必要时，`float` 类型隐式转换为 `double`。</span><span class="sxs-lookup"><span data-stu-id="2ca8d-141">In this case, integral types are implicitly converted to one of the floating-point types and, if necessary, the `float` type is implicitly converted to `double`.</span></span> <span data-ttu-id="2ca8d-142">此表达式的计算方式如下：</span><span class="sxs-lookup"><span data-stu-id="2ca8d-142">The expression is evaluated as follows:</span></span>

- <span data-ttu-id="2ca8d-143">如果表达式中有 `double` 类型，则表达式在关系比较和相等比较中求值得到 `double` 或 [`bool`](bool.md)。</span><span class="sxs-lookup"><span data-stu-id="2ca8d-143">If there is `double` type in the expression, the expression evaluates to `double`, or to [`bool`](bool.md) in relational and equality comparisons.</span></span>
- <span data-ttu-id="2ca8d-144">如果表达式中没有 `double` 类型，则表达式在关系比较和相等比较中求值得到 `float` 或 `bool`。</span><span class="sxs-lookup"><span data-stu-id="2ca8d-144">If there is no `double` type in the expression, the expression evaluates to `float`, or to `bool` in relational and equality comparisons.</span></span>

<span data-ttu-id="2ca8d-145">你还可在表达式中混合使用整型类型和 `decimal` 类型。</span><span class="sxs-lookup"><span data-stu-id="2ca8d-145">You can also mix integral types and the `decimal` type in an expression.</span></span> <span data-ttu-id="2ca8d-146">在这种情况下，整型类型隐式转换为 `decimal` 类型，并且表达式在关系比较和相等比较中求值得到 `decimal` 或 `bool`。</span><span class="sxs-lookup"><span data-stu-id="2ca8d-146">In this case, integral types are implicitly converted to the `decimal` type and the expression evaluates to `decimal`, or to `bool` in relational and equality comparisons.</span></span>

<span data-ttu-id="2ca8d-147">不能在表达式中将 `decimal` 类型与 `float` 和 `double` 类型混合使用。</span><span class="sxs-lookup"><span data-stu-id="2ca8d-147">You cannot mix the `decimal` type with the `float` and `double` types in an expression.</span></span> <span data-ttu-id="2ca8d-148">在这种情况下，如果你想要执行算术运算、比较运算或相等运算，则必须将操作数显式转换为 `decimal` 或反向转换，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="2ca8d-148">In this case, if you want to perform arithmetic, comparison, or equality operations, you must explicitly convert the operands either from or to the `decimal` type, as the following example shows:</span></span>

```csharp-interactive
double a = 1.0;
decimal b = 2.1m;
Console.WriteLine(a + (double)b);
Console.WriteLine((decimal)a + b);
```

<span data-ttu-id="2ca8d-149">可以使用[标准数字格式字符串](../../../standard/base-types/standard-numeric-format-strings.md)或[自定义数字格式字符串](../../../standard/base-types/custom-numeric-format-strings.md)设置浮点值的格式。</span><span class="sxs-lookup"><span data-stu-id="2ca8d-149">You can use either [standard numeric format strings](../../../standard/base-types/standard-numeric-format-strings.md) or [custom numeric format strings](../../../standard/base-types/custom-numeric-format-strings.md) to format a floating-point value.</span></span>

## <a name="real-literals"></a><span data-ttu-id="2ca8d-150">真实文本</span><span class="sxs-lookup"><span data-stu-id="2ca8d-150">Real literals</span></span>

<span data-ttu-id="2ca8d-151">真实文本的类型由其后缀确定，如下所示：</span><span class="sxs-lookup"><span data-stu-id="2ca8d-151">The type of a real literal is determined by its suffix as follows:</span></span>

- <span data-ttu-id="2ca8d-152">不带后缀的文本或带有 `d` 或 `D` 后缀的文本的类型为 `double`</span><span class="sxs-lookup"><span data-stu-id="2ca8d-152">The literal without suffix or with the `d` or `D` suffix is of type `double`</span></span>
- <span data-ttu-id="2ca8d-153">带有 `f` 或 `F` 后缀的文本的类型为 `float`</span><span class="sxs-lookup"><span data-stu-id="2ca8d-153">The literal with the `f` or `F` suffix is of type `float`</span></span>
- <span data-ttu-id="2ca8d-154">带有 `m` 或 `M` 后缀的文本的类型为 `decimal`</span><span class="sxs-lookup"><span data-stu-id="2ca8d-154">The literal with the `m` or `M` suffix is of type `decimal`</span></span>

<span data-ttu-id="2ca8d-155">下面的代码演示每种类型的示例：</span><span class="sxs-lookup"><span data-stu-id="2ca8d-155">The following code demonstrates an example of each:</span></span>

```csharp
double d = 3D;
d = 4d;
d = 3.934_001;

float f = 3_000.5F;
f = 5.4f;

decimal myMoney = 3_000.5m;
myMoney = 400.75M;
```

<span data-ttu-id="2ca8d-156">前面的示例还演示了如何将 `_` 用作数字分隔符（从 C# 7.0 开始提供支持）。</span><span class="sxs-lookup"><span data-stu-id="2ca8d-156">The preceding example also shows the use of `_` as a *digit separator*, which is supported starting with C# 7.0.</span></span> <span data-ttu-id="2ca8d-157">可以将数字分隔符用于所有类型的数字文本。</span><span class="sxs-lookup"><span data-stu-id="2ca8d-157">You can use the digit separator with all kinds of numeric literals.</span></span>

<span data-ttu-id="2ca8d-158">还可以使用科学记数法，即指定真实文本的指数部分，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="2ca8d-158">You can also use scientific notation, that is, specify an exponent part of a real literal, as the following example shows:</span></span>

```csharp-interactive
double d = 0.42e2;
Console.WriteLine(d);  // output 42

float f = 134.45E-2f;
Console.WriteLine(f);  // output: 1.3445

decimal m = 1.5E6m;
Console.WriteLine(m);  // output: 1500000
```

## <a name="conversions"></a><span data-ttu-id="2ca8d-159">转换</span><span class="sxs-lookup"><span data-stu-id="2ca8d-159">Conversions</span></span>

<span data-ttu-id="2ca8d-160">浮点数值类型之间只有一种隐式转换：从 `float` 到 `double`。</span><span class="sxs-lookup"><span data-stu-id="2ca8d-160">There is only one implicit conversion between floating-point numeric types: from `float` to `double`.</span></span> <span data-ttu-id="2ca8d-161">但是，可以使用[显式强制转换](../operators/type-testing-and-cast.md#cast-expression)将任何浮点类型转换为任何其他浮点类型。</span><span class="sxs-lookup"><span data-stu-id="2ca8d-161">However, you can convert any floating-point type to any other floating-point type with the [explicit cast](../operators/type-testing-and-cast.md#cast-expression).</span></span> <span data-ttu-id="2ca8d-162">有关详细信息，请参阅[内置数值转换](numeric-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="2ca8d-162">For more information, see [Built-in numeric conversions](numeric-conversions.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="2ca8d-163">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="2ca8d-163">C# language specification</span></span>

<span data-ttu-id="2ca8d-164">有关更多信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)的以下部分：</span><span class="sxs-lookup"><span data-stu-id="2ca8d-164">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="2ca8d-165">浮点类型</span><span class="sxs-lookup"><span data-stu-id="2ca8d-165">Floating-point types</span></span>](~/_csharplang/spec/types.md#floating-point-types)
- [<span data-ttu-id="2ca8d-166">十进制类型</span><span class="sxs-lookup"><span data-stu-id="2ca8d-166">The decimal type</span></span>](~/_csharplang/spec/types.md#the-decimal-type)
- [<span data-ttu-id="2ca8d-167">真实文本</span><span class="sxs-lookup"><span data-stu-id="2ca8d-167">Real literals</span></span>](~/_csharplang/spec/lexical-structure.md#real-literals)

## <a name="see-also"></a><span data-ttu-id="2ca8d-168">请参阅</span><span class="sxs-lookup"><span data-stu-id="2ca8d-168">See also</span></span>

- [<span data-ttu-id="2ca8d-169">C# 参考</span><span class="sxs-lookup"><span data-stu-id="2ca8d-169">C# reference</span></span>](../index.md)
- [<span data-ttu-id="2ca8d-170">值类型</span><span class="sxs-lookup"><span data-stu-id="2ca8d-170">Value types</span></span>](value-types.md)
- [<span data-ttu-id="2ca8d-171">整型类型</span><span class="sxs-lookup"><span data-stu-id="2ca8d-171">Integral types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="2ca8d-172">标准数字格式字符串</span><span class="sxs-lookup"><span data-stu-id="2ca8d-172">Standard numeric format strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="2ca8d-173">.NET 中的数字</span><span class="sxs-lookup"><span data-stu-id="2ca8d-173">Numerics in .NET</span></span>](../../../standard/numerics.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
