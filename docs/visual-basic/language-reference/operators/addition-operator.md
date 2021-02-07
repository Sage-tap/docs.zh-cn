---
description: '详细了解： + Operator (Visual Basic) '
title: + 操作员
ms.date: 07/20/2015
f1_keywords:
- vb.+
helpviewer_keywords:
- arithmetic operators [Visual Basic], addition
- + operator
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
- sum operator [Visual Basic]
ms.assetid: 5694778f-0a2c-4539-8009-f66f318fb46d
ms.openlocfilehash: 9a6517847945cb2edcbd97adac6a013498dde174
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700684"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="40e81-103">+ 运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="40e81-103">+ Operator (Visual Basic)</span></span>

<span data-ttu-id="40e81-104">将两个数相加或返回数值表达式的正值。</span><span class="sxs-lookup"><span data-stu-id="40e81-104">Adds two numbers or returns the positive value of a numeric expression.</span></span> <span data-ttu-id="40e81-105">还可用于连接两个字符串表达式。</span><span class="sxs-lookup"><span data-stu-id="40e81-105">Can also be used to concatenate two string expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40e81-106">语法</span><span class="sxs-lookup"><span data-stu-id="40e81-106">Syntax</span></span>  
  
```vb
expression1 + expression2
```
  
<span data-ttu-id="40e81-107">or</span><span class="sxs-lookup"><span data-stu-id="40e81-107">or</span></span>

```vb  
+expression1  
```  
  
## <a name="parts"></a><span data-ttu-id="40e81-108">组成部分</span><span class="sxs-lookup"><span data-stu-id="40e81-108">Parts</span></span>  
  
|<span data-ttu-id="40e81-109">术语</span><span class="sxs-lookup"><span data-stu-id="40e81-109">Term</span></span>|<span data-ttu-id="40e81-110">定义</span><span class="sxs-lookup"><span data-stu-id="40e81-110">Definition</span></span>|  
|---|---|  
|`expression1`|<span data-ttu-id="40e81-111">必需。</span><span class="sxs-lookup"><span data-stu-id="40e81-111">Required.</span></span> <span data-ttu-id="40e81-112">任何数值或字符串表达式。</span><span class="sxs-lookup"><span data-stu-id="40e81-112">Any numeric or string expression.</span></span>|  
|`expression2`|<span data-ttu-id="40e81-113">必需，除非 `+` 操作员计算负值。</span><span class="sxs-lookup"><span data-stu-id="40e81-113">Required unless the `+` operator is calculating a negative value.</span></span> <span data-ttu-id="40e81-114">任何数值或字符串表达式。</span><span class="sxs-lookup"><span data-stu-id="40e81-114">Any numeric or string expression.</span></span>|  
  
## <a name="result"></a><span data-ttu-id="40e81-115">结果</span><span class="sxs-lookup"><span data-stu-id="40e81-115">Result</span></span>  

 <span data-ttu-id="40e81-116">如果 `expression1` 和 `expression2` 均为数值，则结果为其算术和。</span><span class="sxs-lookup"><span data-stu-id="40e81-116">If `expression1` and `expression2` are both numeric, the result is their arithmetic sum.</span></span>  
  
 <span data-ttu-id="40e81-117">如果 `expression2` 不存在，则 `+` 运算符为表达式的未更改值的 *一元* 标识运算符。</span><span class="sxs-lookup"><span data-stu-id="40e81-117">If `expression2` is absent, the `+` operator is the *unary* identity operator for the unchanged value of an expression.</span></span> <span data-ttu-id="40e81-118">从这种意义上讲，操作包括保留的符号 `expression1` ，因此如果为负，则结果为负 `expression1` 。</span><span class="sxs-lookup"><span data-stu-id="40e81-118">In this sense, the operation consists of retaining the sign of `expression1`, so the result is negative if `expression1` is negative.</span></span>  
  
 <span data-ttu-id="40e81-119">如果 `expression1` 和 `expression2` 都是字符串，则结果是其值的串联。</span><span class="sxs-lookup"><span data-stu-id="40e81-119">If `expression1` and `expression2` are both strings, the result is the concatenation of their values.</span></span>  
  
 <span data-ttu-id="40e81-120">如果 `expression1` 和 `expression2` 属于混合类型，则执行的操作取决于它们的类型、内容和 [Option Strict 语句](../statements/option-strict-statement.md)的设置。</span><span class="sxs-lookup"><span data-stu-id="40e81-120">If `expression1` and `expression2` are of mixed types, the action taken depends on their types, their contents, and the setting of the [Option Strict Statement](../statements/option-strict-statement.md).</span></span> <span data-ttu-id="40e81-121">有关详细信息，请参阅 "备注" 中的表。</span><span class="sxs-lookup"><span data-stu-id="40e81-121">For more information, see the tables in "Remarks."</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="40e81-122">支持的类型</span><span class="sxs-lookup"><span data-stu-id="40e81-122">Supported Types</span></span>  

 <span data-ttu-id="40e81-123">所有数值类型，包括无符号和浮点类型以及和 `Decimal` `String` 。</span><span class="sxs-lookup"><span data-stu-id="40e81-123">All numeric types, including the unsigned and floating-point types and `Decimal`, and `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40e81-124">备注</span><span class="sxs-lookup"><span data-stu-id="40e81-124">Remarks</span></span>  

 <span data-ttu-id="40e81-125">通常， `+` 如果可能，将执行算术加法运算，并且仅当两个表达式都是字符串时才会进行连接。</span><span class="sxs-lookup"><span data-stu-id="40e81-125">In general, `+` performs arithmetic addition when possible, and concatenates only when both expressions are strings.</span></span>  
  
 <span data-ttu-id="40e81-126">如果两个表达式均为 `Object` ，则 Visual Basic 执行以下操作。</span><span class="sxs-lookup"><span data-stu-id="40e81-126">If neither expression is an `Object`, Visual Basic takes the following actions.</span></span>  
  
|<span data-ttu-id="40e81-127">表达式的数据类型</span><span class="sxs-lookup"><span data-stu-id="40e81-127">Data types of expressions</span></span>|<span data-ttu-id="40e81-128">编译器操作</span><span class="sxs-lookup"><span data-stu-id="40e81-128">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="40e81-129">这两个表达式都是数值数据类型 (、、、、、、、、、 `SByte` `Byte` `Short` `UShort` `Integer` `UInteger` `Long` `ULong` `Decimal` `Single` 或 `Double`) </span><span class="sxs-lookup"><span data-stu-id="40e81-129">Both expressions are numeric data types (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, or `Double`)</span></span>|<span data-ttu-id="40e81-130">添加。</span><span class="sxs-lookup"><span data-stu-id="40e81-130">Add.</span></span> <span data-ttu-id="40e81-131">Result 数据类型是适用于和的数据类型的数值类型 `expression1` `expression2` 。</span><span class="sxs-lookup"><span data-stu-id="40e81-131">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="40e81-132">请参阅 [运算符结果的数据类型](data-types-of-operator-results.md)中的 "整数算法" 表。</span><span class="sxs-lookup"><span data-stu-id="40e81-132">See the "Integer Arithmetic" tables in [Data Types of Operator Results](data-types-of-operator-results.md).</span></span>|  
|<span data-ttu-id="40e81-133">这两个表达式的类型为 `String`</span><span class="sxs-lookup"><span data-stu-id="40e81-133">Both expressions are of type `String`</span></span>|<span data-ttu-id="40e81-134">起来.</span><span class="sxs-lookup"><span data-stu-id="40e81-134">Concatenate.</span></span>|  
|<span data-ttu-id="40e81-135">一个表达式为数值数据类型，另一个表达式为字符串</span><span class="sxs-lookup"><span data-stu-id="40e81-135">One expression is a numeric data type and the other is a string</span></span>|<span data-ttu-id="40e81-136">如果 `Option Strict` 为 `On` ，则生成编译器错误。</span><span class="sxs-lookup"><span data-stu-id="40e81-136">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="40e81-137">如果 `Option Strict` 为 `Off` ，则将隐式转换 `String` 为 `Double` 并添加。</span><span class="sxs-lookup"><span data-stu-id="40e81-137">If `Option Strict` is `Off`, then implicitly convert the `String` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="40e81-138">如果 `String` 无法转换为 `Double` ，则引发 <xref:System.InvalidCastException> 异常。</span><span class="sxs-lookup"><span data-stu-id="40e81-138">If the `String` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="40e81-139">一个表达式为数值数据类型，另一个表达式为 [Nothing](../nothing.md)</span><span class="sxs-lookup"><span data-stu-id="40e81-139">One expression is a numeric data type, and the other is [Nothing](../nothing.md)</span></span>|<span data-ttu-id="40e81-140">添加，其 `Nothing` 值为零。</span><span class="sxs-lookup"><span data-stu-id="40e81-140">Add, with `Nothing` valued as zero.</span></span>|  
|<span data-ttu-id="40e81-141">一个表达式是字符串，另一个表达式是 `Nothing`</span><span class="sxs-lookup"><span data-stu-id="40e81-141">One expression is a string, and the other is `Nothing`</span></span>|<span data-ttu-id="40e81-142">串联，其 `Nothing` 值为 ""。</span><span class="sxs-lookup"><span data-stu-id="40e81-142">Concatenate, with `Nothing` valued as "".</span></span>|  
  
 <span data-ttu-id="40e81-143">如果一个表达式是 `Object` 表达式，Visual Basic 会执行以下操作。</span><span class="sxs-lookup"><span data-stu-id="40e81-143">If one expression is an `Object` expression, Visual Basic takes the following actions.</span></span>  
  
|<span data-ttu-id="40e81-144">表达式的数据类型</span><span class="sxs-lookup"><span data-stu-id="40e81-144">Data types of expressions</span></span>|<span data-ttu-id="40e81-145">编译器操作</span><span class="sxs-lookup"><span data-stu-id="40e81-145">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="40e81-146">`Object` 表达式保存数字值，另一种是数值数据类型</span><span class="sxs-lookup"><span data-stu-id="40e81-146">`Object` expression holds a numeric value and the other is a numeric data type</span></span>|<span data-ttu-id="40e81-147">如果 `Option Strict` 为 `On` ，则生成编译器错误。</span><span class="sxs-lookup"><span data-stu-id="40e81-147">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="40e81-148">如果 `Option Strict` 为 `Off` ，则添加。</span><span class="sxs-lookup"><span data-stu-id="40e81-148">If `Option Strict` is `Off`, then add.</span></span>|  
|<span data-ttu-id="40e81-149">`Object` 表达式保存一个数字值，另一个的类型为 `String`</span><span class="sxs-lookup"><span data-stu-id="40e81-149">`Object` expression holds a numeric value and the other is of type `String`</span></span>|<span data-ttu-id="40e81-150">如果 `Option Strict` 为 `On` ，则生成编译器错误。</span><span class="sxs-lookup"><span data-stu-id="40e81-150">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="40e81-151">如果 `Option Strict` 为 `Off` ，则将隐式转换 `String` 为 `Double` 并添加。</span><span class="sxs-lookup"><span data-stu-id="40e81-151">If `Option Strict` is `Off`, then implicitly convert the `String` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="40e81-152">如果 `String` 无法转换为 `Double` ，则引发 <xref:System.InvalidCastException> 异常。</span><span class="sxs-lookup"><span data-stu-id="40e81-152">If the `String` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="40e81-153">`Object` 表达式保存一个字符串，另一个表达式为数值数据类型</span><span class="sxs-lookup"><span data-stu-id="40e81-153">`Object` expression holds a string and the other is a numeric data type</span></span>|<span data-ttu-id="40e81-154">如果 `Option Strict` 为 `On` ，则生成编译器错误。</span><span class="sxs-lookup"><span data-stu-id="40e81-154">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="40e81-155">如果 `Option Strict` 为 `Off` ，则将字符串隐式转换 `Object` 为 `Double` 并添加。</span><span class="sxs-lookup"><span data-stu-id="40e81-155">If `Option Strict` is `Off`, then implicitly convert the string `Object` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="40e81-156">如果字符串 `Object` 无法转换为 `Double` ，则引发 <xref:System.InvalidCastException> 异常。</span><span class="sxs-lookup"><span data-stu-id="40e81-156">If the string `Object` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="40e81-157">`Object` 表达式保存了一个字符串，另一个的类型为 `String`</span><span class="sxs-lookup"><span data-stu-id="40e81-157">`Object` expression holds a string and the other is of type `String`</span></span>|<span data-ttu-id="40e81-158">如果 `Option Strict` 为 `On` ，则生成编译器错误。</span><span class="sxs-lookup"><span data-stu-id="40e81-158">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="40e81-159">如果 `Option Strict` 为 `Off` ，则隐式转换 `Object` 到 `String` 并连接。</span><span class="sxs-lookup"><span data-stu-id="40e81-159">If `Option Strict` is `Off`, then implicitly convert `Object` to `String` and concatenate.</span></span>|  
  
 <span data-ttu-id="40e81-160">如果两个表达式都是 `Object` 表达式，则 Visual Basic 仅 () 执行以下操作 `Option Strict Off` 。</span><span class="sxs-lookup"><span data-stu-id="40e81-160">If both expressions are `Object` expressions, Visual Basic takes the following actions (`Option Strict Off` only).</span></span>  
  
|<span data-ttu-id="40e81-161">表达式的数据类型</span><span class="sxs-lookup"><span data-stu-id="40e81-161">Data types of expressions</span></span>|<span data-ttu-id="40e81-162">编译器操作</span><span class="sxs-lookup"><span data-stu-id="40e81-162">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="40e81-163">两个 `Object` 表达式都保存数字值</span><span class="sxs-lookup"><span data-stu-id="40e81-163">Both `Object` expressions hold numeric values</span></span>|<span data-ttu-id="40e81-164">添加。</span><span class="sxs-lookup"><span data-stu-id="40e81-164">Add.</span></span>|  
|<span data-ttu-id="40e81-165">这两个 `Object` 表达式的类型为 `String`</span><span class="sxs-lookup"><span data-stu-id="40e81-165">Both `Object` expressions are of type `String`</span></span>|<span data-ttu-id="40e81-166">起来.</span><span class="sxs-lookup"><span data-stu-id="40e81-166">Concatenate.</span></span>|  
|<span data-ttu-id="40e81-167">一个 `Object` 表达式保存一个数字值，另一个表达式保存一个字符串</span><span class="sxs-lookup"><span data-stu-id="40e81-167">One `Object` expression holds a numeric value and the other holds a string</span></span>|<span data-ttu-id="40e81-168">将字符串隐式转换 `Object` 为 `Double` 并添加。</span><span class="sxs-lookup"><span data-stu-id="40e81-168">Implicitly convert the string `Object` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="40e81-169">如果字符串 `Object` 不能转换为数字值，则引发 <xref:System.InvalidCastException> 异常。</span><span class="sxs-lookup"><span data-stu-id="40e81-169">If the string `Object` cannot be converted to a numeric value, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
  
 <span data-ttu-id="40e81-170">如果其中一个 `Object` 表达式的计算结果为 [Nothing](../nothing.md) 或 <xref:System.DBNull> ，则 `+` 运算符将其视为 `String` 值为 "" 的。</span><span class="sxs-lookup"><span data-stu-id="40e81-170">If either `Object` expression evaluates to [Nothing](../nothing.md) or <xref:System.DBNull>, the `+` operator treats it as a `String` with a value of "".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="40e81-171">使用 `+` 运算符时，可能无法确定是进行加法还是字符串串联。</span><span class="sxs-lookup"><span data-stu-id="40e81-171">When you use the `+` operator, you might not be able to determine whether addition or string concatenation will occur.</span></span> <span data-ttu-id="40e81-172">使用 `&` 运算符进行串联以消除多义性，并提供自文档代码。</span><span class="sxs-lookup"><span data-stu-id="40e81-172">Use the `&` operator for concatenation to eliminate ambiguity and to provide self-documenting code.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="40e81-173">重载</span><span class="sxs-lookup"><span data-stu-id="40e81-173">Overloading</span></span>  

 <span data-ttu-id="40e81-174">`+`运算符可以 *重载*，这意味着当操作数具有该类或结构的类型时，该类或结构可以重新定义其行为。</span><span class="sxs-lookup"><span data-stu-id="40e81-174">The `+` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="40e81-175">如果你的代码在该类或结构上使用此运算符，请确保了解其重新定义的行为。</span><span class="sxs-lookup"><span data-stu-id="40e81-175">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="40e81-176">有关详细信息，请参阅 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="40e81-176">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="40e81-177">示例</span><span class="sxs-lookup"><span data-stu-id="40e81-177">Example</span></span>  

 <span data-ttu-id="40e81-178">下面的示例使用 `+` 运算符来添加数字。</span><span class="sxs-lookup"><span data-stu-id="40e81-178">The following example uses the `+` operator to add numbers.</span></span> <span data-ttu-id="40e81-179">如果操作数均为数值，则 Visual Basic 计算算术结果。</span><span class="sxs-lookup"><span data-stu-id="40e81-179">If the operands are both numeric, Visual Basic computes the arithmetic result.</span></span> <span data-ttu-id="40e81-180">算术结果表示两个操作数之和。</span><span class="sxs-lookup"><span data-stu-id="40e81-180">The arithmetic result represents the sum of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#6)]  
  
 <span data-ttu-id="40e81-181">还可以使用 `+` 运算符来串联字符串。</span><span class="sxs-lookup"><span data-stu-id="40e81-181">You can also use the `+` operator to concatenate strings.</span></span> <span data-ttu-id="40e81-182">如果两个操作数都是字符串，Visual Basic 将它们连接起来。</span><span class="sxs-lookup"><span data-stu-id="40e81-182">If the operands are both strings, Visual Basic concatenates them.</span></span> <span data-ttu-id="40e81-183">连接结果表示一个字符串，该字符串包含两个操作数的内容。</span><span class="sxs-lookup"><span data-stu-id="40e81-183">The concatenation result represents a single string consisting of the contents of the two operands one after the other.</span></span>  
  
 <span data-ttu-id="40e81-184">如果操作数属于混合类型，则结果取决于 [Option Strict 语句](../statements/option-strict-statement.md)的设置。</span><span class="sxs-lookup"><span data-stu-id="40e81-184">If the operands are of mixed types, the result depends on the setting of the [Option Strict Statement](../statements/option-strict-statement.md).</span></span> <span data-ttu-id="40e81-185">下面的示例演示了在为时的结果 `Option Strict` `On` 。</span><span class="sxs-lookup"><span data-stu-id="40e81-185">The following example illustrates the result when `Option Strict` is `On`.</span></span>  
  
 [!code-vb[VbVbalrOperators#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class3.vb#53)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#51)]  
  
 <span data-ttu-id="40e81-186">下面的示例演示了在为时的结果 `Option Strict` `Off` 。</span><span class="sxs-lookup"><span data-stu-id="40e81-186">The following example illustrates the result when `Option Strict` is `Off`.</span></span>  
  
 [!code-vb[VbVbalrOperators#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#54)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#52)]  
  
 <span data-ttu-id="40e81-187">为了消除多义性，应使用 `&` 运算符而不是 `+` 串联。</span><span class="sxs-lookup"><span data-stu-id="40e81-187">To eliminate ambiguity, you should use the `&` operator instead of `+` for concatenation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40e81-188">请参阅</span><span class="sxs-lookup"><span data-stu-id="40e81-188">See also</span></span>

- [<span data-ttu-id="40e81-189">& 运算符</span><span class="sxs-lookup"><span data-stu-id="40e81-189">& Operator</span></span>](concatenation-operator.md)
- [<span data-ttu-id="40e81-190">串联运算符</span><span class="sxs-lookup"><span data-stu-id="40e81-190">Concatenation Operators</span></span>](concatenation-operators.md)
- [<span data-ttu-id="40e81-191">算术运算符</span><span class="sxs-lookup"><span data-stu-id="40e81-191">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="40e81-192">按功能列出的运算符</span><span class="sxs-lookup"><span data-stu-id="40e81-192">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="40e81-193">Visual Basic 中的运算符优先级</span><span class="sxs-lookup"><span data-stu-id="40e81-193">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="40e81-194">算术运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="40e81-194">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [<span data-ttu-id="40e81-195">Option Strict 语句</span><span class="sxs-lookup"><span data-stu-id="40e81-195">Option Strict Statement</span></span>](../statements/option-strict-statement.md)
