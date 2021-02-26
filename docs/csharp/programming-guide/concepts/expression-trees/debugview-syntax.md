---
title: DebugView 属性 (C#) 使用的语法
description: 描述 DebugView 属性使用的特殊语法以生成表达式数的字符串表示形式
author: zspitz
ms.author: wiwagn
ms.date: 02/14/2021
ms.topic: reference
helpviewer_keywords:
- expression trees
- debugview
ms.openlocfilehash: 278fc66f9f8cf7671b956126cec10c4464a5b81c
ms.sourcegitcommit: 456b3cd82a87b453fa737b4661295070d1b6d684
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/17/2021
ms.locfileid: "100639384"
---
# <a name="debugview-syntax"></a><span data-ttu-id="014ff-103">DebugView 语法</span><span class="sxs-lookup"><span data-stu-id="014ff-103">**DebugView** syntax</span></span>

<span data-ttu-id="014ff-104">DebugView 属性（仅在调试时可用）提供表达式树的字符串呈现。</span><span class="sxs-lookup"><span data-stu-id="014ff-104">The **DebugView** property (available only when debugging) provides a string rendering of expression trees.</span></span> <span data-ttu-id="014ff-105">大部分语法都相当容易理解；特殊情况将在以下部分中介绍。</span><span class="sxs-lookup"><span data-stu-id="014ff-105">Most of the syntax is fairly straightforward to understand; the special cases are described in the following sections.</span></span>

<span data-ttu-id="014ff-106">每个示例都后跟块注释，其中包含 DebugView。</span><span class="sxs-lookup"><span data-stu-id="014ff-106">Each example is followed by a block comment, containing the **DebugView**.</span></span>

## <a name="parameterexpression"></a><span data-ttu-id="014ff-107">ParameterExpression</span><span class="sxs-lookup"><span data-stu-id="014ff-107">ParameterExpression</span></span>

<span data-ttu-id="014ff-108"><xref:System.Linq.Expressions.ParameterExpression> 变量名称的开头显示有 `$` 符号。</span><span class="sxs-lookup"><span data-stu-id="014ff-108"><xref:System.Linq.Expressions.ParameterExpression> variable names are displayed with a `$` symbol at the beginning.</span></span>

<span data-ttu-id="014ff-109">如果参数没有名称，则会为其分配一个自动生成的名称，例如 `$var1` 或 `$var2`。</span><span class="sxs-lookup"><span data-stu-id="014ff-109">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>

### <a name="examples"></a><span data-ttu-id="014ff-110">示例</span><span class="sxs-lookup"><span data-stu-id="014ff-110">Examples</span></span>

```csharp
ParameterExpression numParam =  Expression.Parameter(typeof(int), "num");
/*
    $num
*/

ParameterExpression numParam =  Expression.Parameter(typeof(int));
/*
    $var1
*/
```

## <a name="constantexpression"></a><span data-ttu-id="014ff-111">ConstantExpression</span><span class="sxs-lookup"><span data-stu-id="014ff-111">ConstantExpression</span></span>

<span data-ttu-id="014ff-112">对于表示整数值、字符串和 `null` 的 <xref:System.Linq.Expressions.ConstantExpression> 对象，将显示常数的值。</span><span class="sxs-lookup"><span data-stu-id="014ff-112">For <xref:System.Linq.Expressions.ConstantExpression> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>

<span data-ttu-id="014ff-113">对于使用标准后缀作为 C# 原义字符的数值类型，将后缀添加到值。</span><span class="sxs-lookup"><span data-stu-id="014ff-113">For numeric types that have standard suffixes as C# literals, the suffix is added to the value.</span></span> <span data-ttu-id="014ff-114">下表显示与各种数值类型关联的后缀。</span><span class="sxs-lookup"><span data-stu-id="014ff-114">The following table shows the suffixes associated with various numeric types.</span></span>

| <span data-ttu-id="014ff-115">类型</span><span class="sxs-lookup"><span data-stu-id="014ff-115">Type</span></span> | <span data-ttu-id="014ff-116">关键字</span><span class="sxs-lookup"><span data-stu-id="014ff-116">Keyword</span></span> | <span data-ttu-id="014ff-117">Suffix</span><span class="sxs-lookup"><span data-stu-id="014ff-117">Suffix</span></span> |
|--|--|--|
| <xref:System.UInt32?displayProperty=nameWithType> | [<span data-ttu-id="014ff-118">uint</span><span class="sxs-lookup"><span data-stu-id="014ff-118">uint</span></span>](../../../language-reference/builtin-types/integral-numeric-types.md) | <span data-ttu-id="014ff-119">U</span><span class="sxs-lookup"><span data-stu-id="014ff-119">U</span></span> |
| <xref:System.Int64?displayProperty=nameWithType> | [<span data-ttu-id="014ff-120">long</span><span class="sxs-lookup"><span data-stu-id="014ff-120">long</span></span>](../../../language-reference/builtin-types/integral-numeric-types.md) | <span data-ttu-id="014ff-121">L</span><span class="sxs-lookup"><span data-stu-id="014ff-121">L</span></span> |
| <xref:System.UInt64?displayProperty=nameWithType> | [<span data-ttu-id="014ff-122">ulong</span><span class="sxs-lookup"><span data-stu-id="014ff-122">ulong</span></span>](../../../language-reference/builtin-types/integral-numeric-types.md) | <span data-ttu-id="014ff-123">UL</span><span class="sxs-lookup"><span data-stu-id="014ff-123">UL</span></span> |
| <xref:System.Double?displayProperty=nameWithType> | [<span data-ttu-id="014ff-124">double</span><span class="sxs-lookup"><span data-stu-id="014ff-124">double</span></span>](../../../language-reference/builtin-types/floating-point-numeric-types.md) | <span data-ttu-id="014ff-125">D</span><span class="sxs-lookup"><span data-stu-id="014ff-125">D</span></span> |
| <xref:System.Single?displayProperty=nameWithType> | [<span data-ttu-id="014ff-126">float</span><span class="sxs-lookup"><span data-stu-id="014ff-126">float</span></span>](../../../language-reference/builtin-types/floating-point-numeric-types.md) | <span data-ttu-id="014ff-127">F</span><span class="sxs-lookup"><span data-stu-id="014ff-127">F</span></span> |
| <xref:System.Decimal?displayProperty=nameWithType> | [<span data-ttu-id="014ff-128">decimal</span><span class="sxs-lookup"><span data-stu-id="014ff-128">decimal</span></span>](../../../language-reference/builtin-types/floating-point-numeric-types.md) | <span data-ttu-id="014ff-129">M</span><span class="sxs-lookup"><span data-stu-id="014ff-129">M</span></span> |

### <a name="examples"></a><span data-ttu-id="014ff-130">示例</span><span class="sxs-lookup"><span data-stu-id="014ff-130">Examples</span></span>

```csharp
int num = 10;
ConstantExpression expr = Expression.Constant(num);
/*
    10
*/

double num = 10;
ConstantExpression expr = Expression.Constant(num);
/*
    10D
*/
```

## <a name="blockexpression"></a><span data-ttu-id="014ff-131">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="014ff-131">BlockExpression</span></span>

<span data-ttu-id="014ff-132">如果 <xref:System.Linq.Expressions.BlockExpression> 对象的类型与块中最后一个表达式的类型不同，则该类型将显示在尖括号（`<` 和 `>`）内。</span><span class="sxs-lookup"><span data-stu-id="014ff-132">If the type of a <xref:System.Linq.Expressions.BlockExpression> object differs from the type of the last expression in the block, the type is displayed within angle brackets (`<` and `>`).</span></span> <span data-ttu-id="014ff-133">否则，将不显示 <xref:System.Linq.Expressions.BlockExpression> 对象的类型。</span><span class="sxs-lookup"><span data-stu-id="014ff-133">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>

### <a name="examples"></a><span data-ttu-id="014ff-134">示例</span><span class="sxs-lookup"><span data-stu-id="014ff-134">Examples</span></span>

```csharp
BlockExpression block = Expression.Block(Expression.Constant("test"));
/*
    .Block() {
        "test"
    }
*/

BlockExpression block =  Expression.Block(typeof(Object), Expression.Constant("test"));
/*
    .Block<System.Object>() {
        "test"
    }
*/
```

## <a name="lambdaexpression"></a><span data-ttu-id="014ff-135">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="014ff-135">LambdaExpression</span></span>

<span data-ttu-id="014ff-136">显示 <xref:System.Linq.Expressions.LambdaExpression> 对象及其委托类型。</span><span class="sxs-lookup"><span data-stu-id="014ff-136"><xref:System.Linq.Expressions.LambdaExpression> objects are displayed together with their delegate types.</span></span>

<span data-ttu-id="014ff-137">如果 lambda 表达式没有名称，则会为其分配一个自动生成的名称，例如 `#Lambda1` 或 `#Lambda2`。</span><span class="sxs-lookup"><span data-stu-id="014ff-137">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>

### <a name="examples"></a><span data-ttu-id="014ff-138">示例</span><span class="sxs-lookup"><span data-stu-id="014ff-138">Examples</span></span>

```csharp
LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1));
/*
    .Lambda #Lambda1<System.Func'1[System.Int32]>() {
        1
    }
*/

LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1), "SampleLambda", null);
/*
    .Lambda #SampleLambda<System.Func'1[System.Int32]>() {
        1
    }
*/
```

## <a name="labelexpression"></a><span data-ttu-id="014ff-139">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="014ff-139">LabelExpression</span></span>

<span data-ttu-id="014ff-140">如果指定 <xref:System.Linq.Expressions.LabelExpression> 对象的默认值，则在 <xref:System.Linq.Expressions.LabelTarget> 对象之前显示此值。</span><span class="sxs-lookup"><span data-stu-id="014ff-140">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget> object.</span></span>

<span data-ttu-id="014ff-141">`.Label` 令牌指示标签的开头。</span><span class="sxs-lookup"><span data-stu-id="014ff-141">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="014ff-142">`.LabelTarget` 令牌指示要跳转到的目标的目的地。</span><span class="sxs-lookup"><span data-stu-id="014ff-142">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>

<span data-ttu-id="014ff-143">如果标签没有名称，则会为其分配一个自动生成的名称，例如 `#Label1` 或 `#Label2`。</span><span class="sxs-lookup"><span data-stu-id="014ff-143">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>

### <a name="examples"></a><span data-ttu-id="014ff-144">示例</span><span class="sxs-lookup"><span data-stu-id="014ff-144">Examples</span></span>

```csharp
LabelTarget target = Expression.Label(typeof(int), "SampleLabel");
BlockExpression block = Expression.Block(
    Expression.Goto(target, Expression.Constant(0)),
    Expression.Label(target, Expression.Constant(-1))
);
/*
    .Block() {
        .Goto SampleLabel { 0 };
        .Label
            -1
        .LabelTarget SampleLabel:
    }
*/

LabelTarget target = Expression.Label();
BlockExpression block = Expression.Block(
    Expression.Goto(target),
    Expression.Label(target)
);
/*
    .Block() {
        .Goto #Label1 { };
        .Label
        .LabelTarget #Label1:
    }
*/
```

## <a name="checked-operators"></a><span data-ttu-id="014ff-145">Checked 运算符</span><span class="sxs-lookup"><span data-stu-id="014ff-145">Checked Operators</span></span>

<span data-ttu-id="014ff-146">Checked 运算符在运算符前面显示 `#` 符号。</span><span class="sxs-lookup"><span data-stu-id="014ff-146">Checked operators are displayed with the `#` symbol in front of the operator.</span></span> <span data-ttu-id="014ff-147">例如，checked 加号显示为 `#+`。</span><span class="sxs-lookup"><span data-stu-id="014ff-147">For example, the checked addition operator is displayed as `#+`.</span></span>

### <a name="examples"></a><span data-ttu-id="014ff-148">示例</span><span class="sxs-lookup"><span data-stu-id="014ff-148">Examples</span></span>

```csharp
Expression expr = Expression.AddChecked( Expression.Constant(1), Expression.Constant(2));
/*
    1 #+ 2
*/

Expression expr = Expression.ConvertChecked( Expression.Constant(10.0), typeof(int));
/*
    #(System.Int32)10D
*/
```
