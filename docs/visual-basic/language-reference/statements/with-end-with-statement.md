---
description: '了解有关以下内容的详细信息： .。。End With 语句 (Visual Basic) '
title: With...End With 语句
ms.date: 07/20/2015
f1_keywords:
- vb.With
helpviewer_keywords:
- With keyword [Visual Basic]
- loop structures [Visual Basic], and With...End With statements
- execution [Visual Basic], on object
- instructions, repeating
- With...End With statements [Visual Basic]
- With statement [Visual Basic]
- With statement [Visual Basic], nesting
- objects [Visual Basic], accessing
- With block
- End keyword [Visual Basic], With...End With statements
ms.assetid: 340d5fbb-4f43-48ec-a024-80843c137817
ms.openlocfilehash: 86393d5dee7a03b2b8396b34b31326d1b0ea3c28
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787560"
---
# <a name="withend-with-statement-visual-basic"></a><span data-ttu-id="08892-103">With...End With 语句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="08892-103">With...End With Statement (Visual Basic)</span></span>

<span data-ttu-id="08892-104">执行一系列反复引用单个对象或结构的语句，以便这些语句可在访问对象或结构的成员时使用简化语法。</span><span class="sxs-lookup"><span data-stu-id="08892-104">Executes a series of statements that repeatedly refer to a single object or structure so that the statements can use a simplified syntax when accessing members of the object or structure.</span></span>  <span data-ttu-id="08892-105">使用结构时，你只能读取成员或调用的方法的值，如果你尝试为 `With...End With` 语句中使用的结构的成员赋值，则将收到错误。</span><span class="sxs-lookup"><span data-stu-id="08892-105">When using a structure, you can only read the values of members or invoke methods, and you get an error if you try to assign values to members of a structure used in a `With...End With` statement.</span></span>

## <a name="syntax"></a><span data-ttu-id="08892-106">语法</span><span class="sxs-lookup"><span data-stu-id="08892-106">Syntax</span></span>

```vb
With objectExpression
    [ statements ]
End With
```

## <a name="parts"></a><span data-ttu-id="08892-107">组成部分</span><span class="sxs-lookup"><span data-stu-id="08892-107">Parts</span></span>

|<span data-ttu-id="08892-108">术语</span><span class="sxs-lookup"><span data-stu-id="08892-108">Term</span></span>|<span data-ttu-id="08892-109">定义</span><span class="sxs-lookup"><span data-stu-id="08892-109">Definition</span></span>|
|---|---|
|`objectExpression`|<span data-ttu-id="08892-110">必需。</span><span class="sxs-lookup"><span data-stu-id="08892-110">Required.</span></span> <span data-ttu-id="08892-111">计算结果为对象的表达式。</span><span class="sxs-lookup"><span data-stu-id="08892-111">An expression that evaluates to an object.</span></span> <span data-ttu-id="08892-112">表达式可能是任意复杂的，并且只能计算一次。</span><span class="sxs-lookup"><span data-stu-id="08892-112">The expression may be arbitrarily complex and is evaluated only once.</span></span> <span data-ttu-id="08892-113">表达式可以计算为任何数据类型，包括基本类型。</span><span class="sxs-lookup"><span data-stu-id="08892-113">The expression can evaluate to any data type, including elementary types.</span></span>|
|`statements`|<span data-ttu-id="08892-114">可选。</span><span class="sxs-lookup"><span data-stu-id="08892-114">Optional.</span></span> <span data-ttu-id="08892-115">`With` 和 `End With` 之间的一个或多个语句，这些语句可能引用通过计算 `objectExpression` 生成的对象的成员。</span><span class="sxs-lookup"><span data-stu-id="08892-115">One or more statements between `With` and `End With` that may refer to members of an object that's produced by the evaluation of `objectExpression`.</span></span>|
|`End With`|<span data-ttu-id="08892-116">必需。</span><span class="sxs-lookup"><span data-stu-id="08892-116">Required.</span></span> <span data-ttu-id="08892-117">终止 `With` 块的定义。</span><span class="sxs-lookup"><span data-stu-id="08892-117">Terminates the definition of the `With` block.</span></span>|

## <a name="remarks"></a><span data-ttu-id="08892-118">备注</span><span class="sxs-lookup"><span data-stu-id="08892-118">Remarks</span></span>

<span data-ttu-id="08892-119">通过使用 `With...End With`，你可对指定对象执行一系列语句，而无需多次指定对象名称。</span><span class="sxs-lookup"><span data-stu-id="08892-119">By using `With...End With`, you can perform a series of statements on a specified object without specifying the name of the object multiple times.</span></span> <span data-ttu-id="08892-120">在 `With` 语句块内，你可指定以句点开头的对象的成员，就像它前面有 `With` 语句对象一样。</span><span class="sxs-lookup"><span data-stu-id="08892-120">Within a `With` statement block, you can specify a member of the object starting with a period, as if the `With` statement object preceded it.</span></span>

<span data-ttu-id="08892-121">例如，若要更改单个对象的多个属性，请将属性分配语句放在 `With...End With` 块中，这样只需引用一次对象，而不是为每个属性分配都引用一次对象。</span><span class="sxs-lookup"><span data-stu-id="08892-121">For example, to change multiple properties on a single object, place the property assignment statements inside the `With...End With` block, referring to the object only once instead of once for each property assignment.</span></span>

<span data-ttu-id="08892-122">如果代码访问多个语句中的同一个对象，则使用 `With` 语句将获得下列好处：</span><span class="sxs-lookup"><span data-stu-id="08892-122">If your code accesses the same object in multiple statements, you gain the following benefits by using the `With` statement:</span></span>

- <span data-ttu-id="08892-123">你不必多次计算复杂的表达式，或者多次将结果分配给临时变量来引用其成员。</span><span class="sxs-lookup"><span data-stu-id="08892-123">You don't need to evaluate a complex expression multiple times or assign the result to a temporary variable to refer to its members multiple times.</span></span>

- <span data-ttu-id="08892-124">通过消除反复限定表达式，你提高了代码的可读取性。</span><span class="sxs-lookup"><span data-stu-id="08892-124">You make your code more readable by eliminating repetitive qualifying expressions.</span></span>

<span data-ttu-id="08892-125">`objectExpression` 的数据类型可以是任何类或结构类型，甚至可以是 Visual Basic 基础类型（如 `Integer`）。</span><span class="sxs-lookup"><span data-stu-id="08892-125">The data type of `objectExpression` can be any class or structure type or even a Visual Basic elementary type such as `Integer`.</span></span>  <span data-ttu-id="08892-126">如果 `objectExpression` 生成对象之外的任何内容，则你只能读取其成员或调用的方法的值，如果你尝试为 `With...End With` 语句中使用的结构的成员赋值，则将收到错误。</span><span class="sxs-lookup"><span data-stu-id="08892-126">If `objectExpression` results in anything other than an object, you can only read the values of its members or invoke methods, and you get an error if you try to assign values to members of a structure used in a `With...End With` statement.</span></span>  <span data-ttu-id="08892-127">此错误与你在调用返回一个结构的方法并立即访问函数结果（如 `GetAPoint().x = 1`）的成员并为其赋值时收到的错误一样。</span><span class="sxs-lookup"><span data-stu-id="08892-127">This is the same error you would get if you invoked a method that returned a structure and immediately accessed and assigned a value to a member of the function’s result, such as `GetAPoint().x = 1`.</span></span>  <span data-ttu-id="08892-128">这两种情况的问题是，结构仅存在于调用堆栈上，并且已修改的结构成员在这些情况下无法写入到一个位置以使程序中的所有其他代码可以观察到更改。</span><span class="sxs-lookup"><span data-stu-id="08892-128">The problem in both cases is that the structure exists only on the call stack, and there is no way a modified structure member in these situations can write to  a location such that any other code in the program can observe the change.</span></span>

<span data-ttu-id="08892-129">在进入块时仅计算 `objectExpression` 一次。</span><span class="sxs-lookup"><span data-stu-id="08892-129">The `objectExpression` is evaluated once, upon entry into the block.</span></span> <span data-ttu-id="08892-130">你无法从 `objectExpression` 块中重新分配 `With`。</span><span class="sxs-lookup"><span data-stu-id="08892-130">You can't reassign the `objectExpression` from within the `With` block.</span></span>

<span data-ttu-id="08892-131">在 `With` 块中，你可访问仅指定对象的方法和属性，而不必限定它们。</span><span class="sxs-lookup"><span data-stu-id="08892-131">Within a `With` block, you can access the methods and properties of only the specified object without qualifying them.</span></span> <span data-ttu-id="08892-132">你可以使用其他对象的方法和属性，但是必须用其对象名限定它们。</span><span class="sxs-lookup"><span data-stu-id="08892-132">You can use methods and properties of other objects, but you must qualify them with their object names.</span></span>

<span data-ttu-id="08892-133">你可以将一个 `With...End With` 语句放置在另一个语句中。</span><span class="sxs-lookup"><span data-stu-id="08892-133">You can place one `With...End With` statement within another.</span></span> <span data-ttu-id="08892-134">如果未从上下文中清除引用的对象，则嵌套的 `With...End With` 语句可能产生混乱。</span><span class="sxs-lookup"><span data-stu-id="08892-134">Nested `With...End With` statements may be confusing if the objects that are being referred to aren't clear from context.</span></span> <span data-ttu-id="08892-135">从内部的 `With` 块内引用外部的 `With` 块中的某个对象时，你必须提供对该对象的完全限定的引用。</span><span class="sxs-lookup"><span data-stu-id="08892-135">You must provide a fully qualified reference to an object that's in an outer `With` block when the object is referenced from within an inner `With` block.</span></span>

<span data-ttu-id="08892-136">你不能从 `With` 语句块的外部分支到此语句块。</span><span class="sxs-lookup"><span data-stu-id="08892-136">You can't branch into a `With` statement block from outside the block.</span></span>

<span data-ttu-id="08892-137">除非此语句块包含循环，否则这些语句只运行一次。</span><span class="sxs-lookup"><span data-stu-id="08892-137">Unless the block contains a loop, the statements run only once.</span></span> <span data-ttu-id="08892-138">你可嵌套不同类型的控制结构。</span><span class="sxs-lookup"><span data-stu-id="08892-138">You can nest different kinds of control structures.</span></span> <span data-ttu-id="08892-139">有关详细信息，请参阅 [嵌套控制结构](../../programming-guide/language-features/control-flow/nested-control-structures.md)。</span><span class="sxs-lookup"><span data-stu-id="08892-139">For more information, see [Nested Control Structures](../../programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>

> [!NOTE]
> <span data-ttu-id="08892-140">你还可在对象初始值设定项中使用 `With` 关键字。</span><span class="sxs-lookup"><span data-stu-id="08892-140">You can use the `With` keyword in object initializers also.</span></span> <span data-ttu-id="08892-141">有关详细信息和示例，请参阅 [对象初始值设定项：命名类型和匿名](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) 类型和 [匿名类型](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="08892-141">For more information and examples, see [Object Initializers: Named and Anonymous Types](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) and [Anonymous Types](../../programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>
>
> <span data-ttu-id="08892-142">如果你使用 `With` 块只是为了初始化已实例化的对象的属性或字段，请考虑改用对象初始值设定项。</span><span class="sxs-lookup"><span data-stu-id="08892-142">If you're using a `With` block only to initialize the properties or fields of an object that you've just instantiated, consider using an object initializer instead.</span></span>

## <a name="example"></a><span data-ttu-id="08892-143">示例</span><span class="sxs-lookup"><span data-stu-id="08892-143">Example</span></span>

<span data-ttu-id="08892-144">在下面的示例中，每个 `With` 块将对单个对象执行一系列语句。</span><span class="sxs-lookup"><span data-stu-id="08892-144">In the following example, each `With` block executes a series of statements on a single object.</span></span>

[!code-vb[VbVbalrWithStatement#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrwithstatement/vb/mainwindow.xaml.vb#2)]

## <a name="example"></a><span data-ttu-id="08892-145">示例</span><span class="sxs-lookup"><span data-stu-id="08892-145">Example</span></span>

<span data-ttu-id="08892-146">下面的示例嵌套 `With…End With` 语句。</span><span class="sxs-lookup"><span data-stu-id="08892-146">The following example nests `With…End With` statements.</span></span> <span data-ttu-id="08892-147">在嵌套的 `With` 语句中，语法引用内部对象。</span><span class="sxs-lookup"><span data-stu-id="08892-147">Within the nested `With` statement, the syntax refers to the inner object.</span></span>

[!code-vb[VbVbalrWithStatement#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrwithstatement/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a><span data-ttu-id="08892-148">请参阅</span><span class="sxs-lookup"><span data-stu-id="08892-148">See also</span></span>

- <xref:System.Collections.Generic.List%601>
- [<span data-ttu-id="08892-149">嵌套的控件结构</span><span class="sxs-lookup"><span data-stu-id="08892-149">Nested Control Structures</span></span>](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="08892-150">对象初始值设定项：命名和匿名类型</span><span class="sxs-lookup"><span data-stu-id="08892-150">Object Initializers: Named and Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="08892-151">匿名类型</span><span class="sxs-lookup"><span data-stu-id="08892-151">Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)
