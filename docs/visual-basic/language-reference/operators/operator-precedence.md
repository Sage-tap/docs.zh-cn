---
description: 详细了解：中的运算符优先级 Visual Basic
title: 运算符优先级
ms.date: 07/20/2015
helpviewer_keywords:
- arithmetic operators [Visual Basic], precedence
- operator precedence
- logical operators [Visual Basic], precedence
- operators [Visual Basic], associativity
- operators [Visual Basic], resolution
- associativity of operators [Visual Basic]
- operators [Visual Basic], precedence
- precedence [Visual Basic], of operators
- comparison operators [Visual Basic], precedence
- math operators [Visual Basic]
- order of precedence
ms.assetid: cbbdb282-f572-458e-a520-008a675f8063
ms.openlocfilehash: 7aa4677549328d450834f3a1ecb047d405893f69
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665284"
---
# <a name="operator-precedence-in-visual-basic"></a><span data-ttu-id="d3bac-103">Visual Basic 中的运算符优先级</span><span class="sxs-lookup"><span data-stu-id="d3bac-103">Operator Precedence in Visual Basic</span></span>

<span data-ttu-id="d3bac-104">当表达式中发生多个操作时，将按预先确定的顺序（称为 *运算符优先级*）来计算和解析各个部分。</span><span class="sxs-lookup"><span data-stu-id="d3bac-104">When several operations occur in an expression, each part is evaluated and resolved in a predetermined order called *operator precedence*.</span></span>

## <a name="precedence-rules"></a><span data-ttu-id="d3bac-105">优先规则</span><span class="sxs-lookup"><span data-stu-id="d3bac-105">Precedence Rules</span></span>

 <span data-ttu-id="d3bac-106">当表达式包含多个类别中的运算符时，将根据以下规则对其进行评估：</span><span class="sxs-lookup"><span data-stu-id="d3bac-106">When expressions contain operators from more than one category, they are evaluated according to the following rules:</span></span>

- <span data-ttu-id="d3bac-107">算术运算符和串联运算符具有以下部分中描述的优先级顺序，并且其优先级比比较、逻辑和按位运算符的优先级高。</span><span class="sxs-lookup"><span data-stu-id="d3bac-107">The arithmetic and concatenation operators have the order of precedence described in the following section, and all have greater precedence than the comparison, logical, and bitwise operators.</span></span>

- <span data-ttu-id="d3bac-108">所有比较运算符都具有相同的优先级，并且其优先级比逻辑 and 位运算符更高，但优先级低于算术运算符和串联运算符。</span><span class="sxs-lookup"><span data-stu-id="d3bac-108">All comparison operators have equal precedence, and all have greater precedence than the logical and bitwise operators, but lower precedence than the arithmetic and concatenation operators.</span></span>

- <span data-ttu-id="d3bac-109">逻辑运算符和位运算符具有以下部分中描述的优先级顺序，并且其优先级低于算术运算符、串联运算符和比较运算符。</span><span class="sxs-lookup"><span data-stu-id="d3bac-109">The logical and bitwise operators have the order of precedence described in the following section, and all have lower precedence than the arithmetic, concatenation, and comparison operators.</span></span>

- <span data-ttu-id="d3bac-110">具有相同优先级的运算符将按照它们在表达式中出现的顺序从左到右进行计算。</span><span class="sxs-lookup"><span data-stu-id="d3bac-110">Operators with equal precedence are evaluated left to right in the order in which they appear in the expression.</span></span>

## <a name="precedence-order"></a><span data-ttu-id="d3bac-111">优先顺序</span><span class="sxs-lookup"><span data-stu-id="d3bac-111">Precedence Order</span></span>

 <span data-ttu-id="d3bac-112">运算符的优先顺序如下：</span><span class="sxs-lookup"><span data-stu-id="d3bac-112">Operators are evaluated in the following order of precedence:</span></span>

### <a name="await-operator"></a><span data-ttu-id="d3bac-113">Await 运算符</span><span class="sxs-lookup"><span data-stu-id="d3bac-113">Await Operator</span></span>

 <span data-ttu-id="d3bac-114">Await</span><span class="sxs-lookup"><span data-stu-id="d3bac-114">Await</span></span>

### <a name="arithmetic-and-concatenation-operators"></a><span data-ttu-id="d3bac-115">算术和串联运算符</span><span class="sxs-lookup"><span data-stu-id="d3bac-115">Arithmetic and Concatenation Operators</span></span>

 <span data-ttu-id="d3bac-116">求幂 (`^`) </span><span class="sxs-lookup"><span data-stu-id="d3bac-116">Exponentiation (`^`)</span></span>

 <span data-ttu-id="d3bac-117">一元恒等 (`+` ， `–`) </span><span class="sxs-lookup"><span data-stu-id="d3bac-117">Unary identity and negation (`+`, `–`)</span></span>

 <span data-ttu-id="d3bac-118">乘法和浮点除法 (`*` ， `/`) </span><span class="sxs-lookup"><span data-stu-id="d3bac-118">Multiplication and floating-point division (`*`, `/`)</span></span>

 <span data-ttu-id="d3bac-119">整数除法 (`\`) </span><span class="sxs-lookup"><span data-stu-id="d3bac-119">Integer division (`\`)</span></span>

 <span data-ttu-id="d3bac-120">模块化算法 (`Mod`) </span><span class="sxs-lookup"><span data-stu-id="d3bac-120">Modular arithmetic (`Mod`)</span></span>

 <span data-ttu-id="d3bac-121">加法和减法 (`+` ， `–`) </span><span class="sxs-lookup"><span data-stu-id="d3bac-121">Addition and subtraction (`+`, `–`)</span></span>

 <span data-ttu-id="d3bac-122">字符串串联 (`&`) </span><span class="sxs-lookup"><span data-stu-id="d3bac-122">String concatenation (`&`)</span></span>

 <span data-ttu-id="d3bac-123">算术移位 (`<<` ， `>>`) </span><span class="sxs-lookup"><span data-stu-id="d3bac-123">Arithmetic bit shift (`<<`, `>>`)</span></span>

### <a name="comparison-operators"></a><span data-ttu-id="d3bac-124">比较运算符</span><span class="sxs-lookup"><span data-stu-id="d3bac-124">Comparison Operators</span></span>

 <span data-ttu-id="d3bac-125">所有比较运算符都 (`=` 、 `<>` 、、 `<` `<=` 、 `>` 、 `>=` 、、、 `Is` `IsNot` `Like` `TypeOf` `Is`) </span><span class="sxs-lookup"><span data-stu-id="d3bac-125">All comparison operators (`=`, `<>`, `<`, `<=`, `>`, `>=`, `Is`, `IsNot`, `Like`, `TypeOf`...`Is`)</span></span>

### <a name="logical-and-bitwise-operators"></a><span data-ttu-id="d3bac-126">逻辑运算符和位运算符</span><span class="sxs-lookup"><span data-stu-id="d3bac-126">Logical and Bitwise Operators</span></span>

 <span data-ttu-id="d3bac-127">求反 (`Not`) </span><span class="sxs-lookup"><span data-stu-id="d3bac-127">Negation (`Not`)</span></span>

 <span data-ttu-id="d3bac-128"> (`And` ， `AndAlso`) </span><span class="sxs-lookup"><span data-stu-id="d3bac-128">Conjunction (`And`, `AndAlso`)</span></span>

 <span data-ttu-id="d3bac-129">包含析取 (`Or` ， `OrElse`) </span><span class="sxs-lookup"><span data-stu-id="d3bac-129">Inclusive disjunction (`Or`, `OrElse`)</span></span>

 <span data-ttu-id="d3bac-130">独占析取 (`Xor`) </span><span class="sxs-lookup"><span data-stu-id="d3bac-130">Exclusive disjunction (`Xor`)</span></span>

### <a name="comments"></a><span data-ttu-id="d3bac-131">注释</span><span class="sxs-lookup"><span data-stu-id="d3bac-131">Comments</span></span>

 <span data-ttu-id="d3bac-132">`=`运算符只是相等比较运算符，而不是赋值运算符。</span><span class="sxs-lookup"><span data-stu-id="d3bac-132">The `=` operator is only the equality comparison operator, not the assignment operator.</span></span>

 <span data-ttu-id="d3bac-133">字符串串联运算符 (`&`) 不是算术运算符，但在优先级上，它是与算术运算符组合在一起的。</span><span class="sxs-lookup"><span data-stu-id="d3bac-133">The string concatenation operator (`&`) is not an arithmetic operator, but in precedence it is grouped with the arithmetic operators.</span></span>

 <span data-ttu-id="d3bac-134">`Is`和 `IsNot` 运算符是对象引用比较运算符。</span><span class="sxs-lookup"><span data-stu-id="d3bac-134">The `Is` and `IsNot` operators are object reference comparison operators.</span></span> <span data-ttu-id="d3bac-135">它们不会比较两个对象的值;它们仅检查以确定两个对象变量是否引用同一对象实例。</span><span class="sxs-lookup"><span data-stu-id="d3bac-135">They do not compare the values of two objects; they check only to determine whether two object variables refer to the same object instance.</span></span>

## <a name="associativity"></a><span data-ttu-id="d3bac-136">结合性</span><span class="sxs-lookup"><span data-stu-id="d3bac-136">Associativity</span></span>

 <span data-ttu-id="d3bac-137">当相同优先级的运算符同时出现在表达式中时（例如，乘法和除法），编译器将按从左至右的顺序计算每个运算。</span><span class="sxs-lookup"><span data-stu-id="d3bac-137">When operators of equal precedence appear together in an expression, for example multiplication and division, the compiler evaluates each operation as it encounters it from left to right.</span></span> <span data-ttu-id="d3bac-138">下面的示例阐释了这一点。</span><span class="sxs-lookup"><span data-stu-id="d3bac-138">The following example illustrates this.</span></span>

```vb
Dim n1 As Integer = 96 / 8 / 4
Dim n2 As Integer = (96 / 8) / 4
Dim n3 As Integer = 96 / (8 / 4)
```

 <span data-ttu-id="d3bac-139">第一个表达式计算除法 96/8 (，这将导致 12) ，然后是除法 12/4，这会产生三个结果。</span><span class="sxs-lookup"><span data-stu-id="d3bac-139">The first expression evaluates the division 96 / 8 (which results in 12) and then the division 12 / 4, which results in three.</span></span> <span data-ttu-id="d3bac-140">由于编译器 `n1` 会按从左至右的顺序计算运算，因此当显式指示该顺序时，计算是相同的 `n2` 。</span><span class="sxs-lookup"><span data-stu-id="d3bac-140">Because the compiler evaluates the operations for `n1` from left to right, the evaluation is the same when that order is explicitly indicated for `n2`.</span></span> <span data-ttu-id="d3bac-141">`n1`和都 `n2` 具有三个结果。</span><span class="sxs-lookup"><span data-stu-id="d3bac-141">Both `n1` and `n2` have a result of three.</span></span> <span data-ttu-id="d3bac-142">相反， `n3` 结果为48，因为括号强制编译器首先计算 8/4。</span><span class="sxs-lookup"><span data-stu-id="d3bac-142">By contrast, `n3` has a result of 48, because the parentheses force the compiler to evaluate 8 / 4 first.</span></span>

 <span data-ttu-id="d3bac-143">由于此行为，在 Visual Basic 中，运算符被称为 *左结合* 。</span><span class="sxs-lookup"><span data-stu-id="d3bac-143">Because of this behavior, operators are said to be *left associative* in Visual Basic.</span></span>

## <a name="overriding-precedence-and-associativity"></a><span data-ttu-id="d3bac-144">重写优先级和关联性</span><span class="sxs-lookup"><span data-stu-id="d3bac-144">Overriding Precedence and Associativity</span></span>

 <span data-ttu-id="d3bac-145">您可以使用括号来强制在其他部分中计算表达式。</span><span class="sxs-lookup"><span data-stu-id="d3bac-145">You can use parentheses to force some parts of an expression to be evaluated before others.</span></span> <span data-ttu-id="d3bac-146">这可以覆盖优先级顺序和左侧相关性。</span><span class="sxs-lookup"><span data-stu-id="d3bac-146">This can override both the order of precedence and the left associativity.</span></span> <span data-ttu-id="d3bac-147">Visual Basic 始终执行括在括号内的操作。</span><span class="sxs-lookup"><span data-stu-id="d3bac-147">Visual Basic always performs operations that are enclosed in parentheses before those outside.</span></span> <span data-ttu-id="d3bac-148">但在括号中，它将保持普通的优先级和关联性，除非在括号内使用括号。</span><span class="sxs-lookup"><span data-stu-id="d3bac-148">However, within parentheses, it maintains ordinary precedence and associativity, unless you use parentheses within the parentheses.</span></span> <span data-ttu-id="d3bac-149">下面的示例阐释了这一点。</span><span class="sxs-lookup"><span data-stu-id="d3bac-149">The following example illustrates this.</span></span>

```vb
Dim a, b, c, d, e, f, g As Double
a = 8.0
b = 3.0
c = 4.0
d = 2.0
e = 1.0
f = a - b + c / d * e
' The preceding line sets f to 7.0. Because of natural operator
' precedence and associativity, it is exactly equivalent to the
' following line.
f = (a - b) + ((c / d) * e)
' The following line overrides the natural operator precedence
' and left associativity.
g = (a - (b + c)) / (d * e)
' The preceding line sets g to 0.5.
```

## <a name="see-also"></a><span data-ttu-id="d3bac-150">请参阅</span><span class="sxs-lookup"><span data-stu-id="d3bac-150">See also</span></span>

- [<span data-ttu-id="d3bac-151">= 运算符</span><span class="sxs-lookup"><span data-stu-id="d3bac-151">= Operator</span></span>](assignment-operator.md)
- [<span data-ttu-id="d3bac-152">Is 运算符</span><span class="sxs-lookup"><span data-stu-id="d3bac-152">Is Operator</span></span>](is-operator.md)
- [<span data-ttu-id="d3bac-153">IsNot 运算符</span><span class="sxs-lookup"><span data-stu-id="d3bac-153">IsNot Operator</span></span>](isnot-operator.md)
- [<span data-ttu-id="d3bac-154">Like 运算符</span><span class="sxs-lookup"><span data-stu-id="d3bac-154">Like Operator</span></span>](like-operator.md)
- [<span data-ttu-id="d3bac-155">TypeOf 运算符</span><span class="sxs-lookup"><span data-stu-id="d3bac-155">TypeOf Operator</span></span>](typeof-operator.md)
- [<span data-ttu-id="d3bac-156">Await 运算符</span><span class="sxs-lookup"><span data-stu-id="d3bac-156">Await Operator</span></span>](await-operator.md)
- [<span data-ttu-id="d3bac-157">按功能列出的运算符</span><span class="sxs-lookup"><span data-stu-id="d3bac-157">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="d3bac-158">运算符和表达式</span><span class="sxs-lookup"><span data-stu-id="d3bac-158">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
