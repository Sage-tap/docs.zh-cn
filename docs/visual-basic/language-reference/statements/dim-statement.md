---
description: '了解详细信息： Dim 语句 (Visual Basic) '
title: Dim 语句
ms.date: 05/12/2018
f1_keywords:
- vb.Dim
- Dim
helpviewer_keywords:
- Public keyword [Visual Basic], in Dim statement
- Dim statement [Visual Basic]
- fixed-length strings [Visual Basic], declaring
- variables [Visual Basic], declaring
- WithEvents keyword [Visual Basic], Dim statement
- dynamic arrays [Visual Basic], Dim statement
- variables [Visual Basic], initializing
- '{} braces'
- fields [Visual Basic], as member variables
- declarations [Visual Basic], dynamic arrays
- member variables [Visual Basic]
- default values [Visual Basic]
- data types [Visual Basic], assigning
- braces {}
- As keyword [Visual Basic], in Dim statement
- arrays [Visual Basic], declaring
- New keyword [Visual Basic], Dim statement
- To keyword [Visual Basic], in Dim statement
- storage [Visual Basic], allocating
- local variables [Visual Basic]
- declaration statements [Visual Basic]
- Dim statement [Visual Basic], syntax
- variables [Visual Basic], member and local
ms.assetid: fae3eca1-f0b2-4400-994b-7aa58a848448
ms.openlocfilehash: b950ae95af01be4e064ac9177300f144e0cc08b7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795191"
---
# <a name="dim-statement-visual-basic"></a><span data-ttu-id="f88d0-103">Dim 语句 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="f88d0-103">Dim statement (Visual Basic)</span></span>

<span data-ttu-id="f88d0-104">声明和分配一个或多个变量的存储空间。</span><span class="sxs-lookup"><span data-stu-id="f88d0-104">Declares and allocates storage space for one or more variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="f88d0-105">语法</span><span class="sxs-lookup"><span data-stu-id="f88d0-105">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ] [[ Shared ] [ Shadows ] | [ Static ]] [ ReadOnly ]
Dim [ WithEvents ] variablelist
```

## <a name="parts"></a><span data-ttu-id="f88d0-106">组成部分</span><span class="sxs-lookup"><span data-stu-id="f88d0-106">Parts</span></span>

- `attributelist`

  <span data-ttu-id="f88d0-107">可选。</span><span class="sxs-lookup"><span data-stu-id="f88d0-107">Optional.</span></span> <span data-ttu-id="f88d0-108">请参阅 [特性列表](attribute-list.md)。</span><span class="sxs-lookup"><span data-stu-id="f88d0-108">See [Attribute List](attribute-list.md).</span></span>

- `accessmodifier`

  <span data-ttu-id="f88d0-109">可选。</span><span class="sxs-lookup"><span data-stu-id="f88d0-109">Optional.</span></span> <span data-ttu-id="f88d0-110">可以是以下其中一个值：</span><span class="sxs-lookup"><span data-stu-id="f88d0-110">Can be one of the following:</span></span>

  - [<span data-ttu-id="f88d0-111">公共</span><span class="sxs-lookup"><span data-stu-id="f88d0-111">Public</span></span>](../modifiers/public.md)

  - [<span data-ttu-id="f88d0-112">Protected</span><span class="sxs-lookup"><span data-stu-id="f88d0-112">Protected</span></span>](../modifiers/protected.md)

  - [<span data-ttu-id="f88d0-113">Friend</span><span class="sxs-lookup"><span data-stu-id="f88d0-113">Friend</span></span>](../modifiers/friend.md)

  - [<span data-ttu-id="f88d0-114">专用</span><span class="sxs-lookup"><span data-stu-id="f88d0-114">Private</span></span>](../modifiers/private.md)

  - [<span data-ttu-id="f88d0-115">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="f88d0-115">Protected Friend</span></span>](../modifiers/protected-friend.md)

  - [<span data-ttu-id="f88d0-116">Private Protected</span><span class="sxs-lookup"><span data-stu-id="f88d0-116">Private Protected</span></span>](../modifiers/private-protected.md)

  <span data-ttu-id="f88d0-117">请参阅 [Visual Basic 中的访问级别](../../programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="f88d0-117">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `Shared`

  <span data-ttu-id="f88d0-118">可选。</span><span class="sxs-lookup"><span data-stu-id="f88d0-118">Optional.</span></span> <span data-ttu-id="f88d0-119">请参阅 [共享](../modifiers/shared.md)。</span><span class="sxs-lookup"><span data-stu-id="f88d0-119">See [Shared](../modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="f88d0-120">可选。</span><span class="sxs-lookup"><span data-stu-id="f88d0-120">Optional.</span></span> <span data-ttu-id="f88d0-121">请参阅 [阴影](../modifiers/shadows.md)。</span><span class="sxs-lookup"><span data-stu-id="f88d0-121">See [Shadows](../modifiers/shadows.md).</span></span>

- `Static`

  <span data-ttu-id="f88d0-122">可选。</span><span class="sxs-lookup"><span data-stu-id="f88d0-122">Optional.</span></span> <span data-ttu-id="f88d0-123">请参阅 [静态](../modifiers/static.md)。</span><span class="sxs-lookup"><span data-stu-id="f88d0-123">See [Static](../modifiers/static.md).</span></span>

- `ReadOnly`

  <span data-ttu-id="f88d0-124">可选。</span><span class="sxs-lookup"><span data-stu-id="f88d0-124">Optional.</span></span> <span data-ttu-id="f88d0-125">请参阅 [ReadOnly](../modifiers/readonly.md)。</span><span class="sxs-lookup"><span data-stu-id="f88d0-125">See [ReadOnly](../modifiers/readonly.md).</span></span>

- `WithEvents`

  <span data-ttu-id="f88d0-126">可选。</span><span class="sxs-lookup"><span data-stu-id="f88d0-126">Optional.</span></span> <span data-ttu-id="f88d0-127">指定这些对象变量引用可以引发事件的类的实例。</span><span class="sxs-lookup"><span data-stu-id="f88d0-127">Specifies that these are object variables that refer to instances of a class that can raise events.</span></span> <span data-ttu-id="f88d0-128">请参阅 [WithEvents](../modifiers/withevents.md)。</span><span class="sxs-lookup"><span data-stu-id="f88d0-128">See [WithEvents](../modifiers/withevents.md).</span></span>

- `variablelist`

  <span data-ttu-id="f88d0-129">必需。</span><span class="sxs-lookup"><span data-stu-id="f88d0-129">Required.</span></span> <span data-ttu-id="f88d0-130">在此语句中声明的变量的列表。</span><span class="sxs-lookup"><span data-stu-id="f88d0-130">List of variables being declared in this statement.</span></span>

  `variable [ , variable ... ]`

  <span data-ttu-id="f88d0-131">每个 `variable` 都具有以下语法和部件：</span><span class="sxs-lookup"><span data-stu-id="f88d0-131">Each `variable` has the following syntax and parts:</span></span>

  <span data-ttu-id="f88d0-132">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="f88d0-132">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span></span>

  |<span data-ttu-id="f88d0-133">组成部分</span><span class="sxs-lookup"><span data-stu-id="f88d0-133">Part</span></span>|<span data-ttu-id="f88d0-134">说明</span><span class="sxs-lookup"><span data-stu-id="f88d0-134">Description</span></span>|
  |---|---|
  |`variablename`|<span data-ttu-id="f88d0-135">必需。</span><span class="sxs-lookup"><span data-stu-id="f88d0-135">Required.</span></span> <span data-ttu-id="f88d0-136">变量的名称。</span><span class="sxs-lookup"><span data-stu-id="f88d0-136">Name of the variable.</span></span> <span data-ttu-id="f88d0-137">请参阅 [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="f88d0-137">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|
  |`boundslist`|<span data-ttu-id="f88d0-138">可选。</span><span class="sxs-lookup"><span data-stu-id="f88d0-138">Optional.</span></span> <span data-ttu-id="f88d0-139">数组变量的每个维度的界限列表。</span><span class="sxs-lookup"><span data-stu-id="f88d0-139">List of bounds of each dimension of an array variable.</span></span>|
  |`New`|<span data-ttu-id="f88d0-140">可选。</span><span class="sxs-lookup"><span data-stu-id="f88d0-140">Optional.</span></span> <span data-ttu-id="f88d0-141">在语句运行时创建类的新实例 `Dim` 。</span><span class="sxs-lookup"><span data-stu-id="f88d0-141">Creates a new instance of the class when the `Dim` statement runs.</span></span>|
  |`datatype`|<span data-ttu-id="f88d0-142">可选。</span><span class="sxs-lookup"><span data-stu-id="f88d0-142">Optional.</span></span> <span data-ttu-id="f88d0-143">变量的数据类型。</span><span class="sxs-lookup"><span data-stu-id="f88d0-143">Data type of the variable.</span></span>|
  |`With`|<span data-ttu-id="f88d0-144">可选。</span><span class="sxs-lookup"><span data-stu-id="f88d0-144">Optional.</span></span> <span data-ttu-id="f88d0-145">引入对象初始值设定项列表。</span><span class="sxs-lookup"><span data-stu-id="f88d0-145">Introduces the object initializer list.</span></span>|
  |`propertyname`|<span data-ttu-id="f88d0-146">可选。</span><span class="sxs-lookup"><span data-stu-id="f88d0-146">Optional.</span></span> <span data-ttu-id="f88d0-147">要生成其实例的类中的属性的名称。</span><span class="sxs-lookup"><span data-stu-id="f88d0-147">The name of a property in the class you are making an instance of.</span></span>|
  |`propinitializer`|<span data-ttu-id="f88d0-148">在 = 后必需 `propertyname` 。</span><span class="sxs-lookup"><span data-stu-id="f88d0-148">Required after `propertyname` =.</span></span> <span data-ttu-id="f88d0-149">计算并分配给属性名称的表达式。</span><span class="sxs-lookup"><span data-stu-id="f88d0-149">The expression that is evaluated and assigned to the property name.</span></span>|
  |`initializer`|<span data-ttu-id="f88d0-150">如果 `New` 未指定，则为可选。</span><span class="sxs-lookup"><span data-stu-id="f88d0-150">Optional if `New` is not specified.</span></span> <span data-ttu-id="f88d0-151">创建变量时计算并分配给该变量的表达式。</span><span class="sxs-lookup"><span data-stu-id="f88d0-151">Expression that is evaluated and assigned to the variable when it is created.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f88d0-152">备注</span><span class="sxs-lookup"><span data-stu-id="f88d0-152">Remarks</span></span>

<span data-ttu-id="f88d0-153">Visual Basic 编译器使用 `Dim` 语句来确定变量的数据类型和其他信息，例如哪些代码可以访问该变量。</span><span class="sxs-lookup"><span data-stu-id="f88d0-153">The Visual Basic compiler uses the `Dim` statement to determine the variable's data type and other information, such as what code can access the variable.</span></span> <span data-ttu-id="f88d0-154">下面的示例声明一个变量来保存 `Integer` 值。</span><span class="sxs-lookup"><span data-stu-id="f88d0-154">The following example declares a variable to hold an `Integer` value.</span></span>

```vb
Dim numberOfStudents As Integer
```

<span data-ttu-id="f88d0-155">您可以指定任何数据类型或枚举、结构、类或接口的名称。</span><span class="sxs-lookup"><span data-stu-id="f88d0-155">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>

```vb
Dim finished As Boolean
Dim monitorBox As System.Windows.Forms.Form
```

<span data-ttu-id="f88d0-156">对于引用类型，使用 `New` 关键字创建由数据类型指定的类或结构的新实例。</span><span class="sxs-lookup"><span data-stu-id="f88d0-156">For a reference type, you use the `New` keyword to create a new instance of the class or structure that is specified by the data type.</span></span> <span data-ttu-id="f88d0-157">如果使用 `New` ，则不使用初始值设定项表达式。</span><span class="sxs-lookup"><span data-stu-id="f88d0-157">If you use `New`, you do not use an initializer expression.</span></span> <span data-ttu-id="f88d0-158">相反，可以向从中创建变量的类的构造函数提供参数（如果需要）。</span><span class="sxs-lookup"><span data-stu-id="f88d0-158">Instead, you supply arguments, if they are required, to the constructor of the class from which you are creating the variable.</span></span>

```vb
Dim bottomLabel As New System.Windows.Forms.Label
```

<span data-ttu-id="f88d0-159">您可以在过程、块、类、结构或模块中声明变量。</span><span class="sxs-lookup"><span data-stu-id="f88d0-159">You can declare a variable in a procedure, block, class, structure, or module.</span></span> <span data-ttu-id="f88d0-160">不能在源文件、命名空间或接口中声明变量。</span><span class="sxs-lookup"><span data-stu-id="f88d0-160">You cannot declare a variable in a source file, namespace, or interface.</span></span> <span data-ttu-id="f88d0-161">有关详细信息，请参阅[声明上下文和默认访问级别](declaration-contexts-and-default-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="f88d0-161">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="f88d0-162">在模块级别，在任何过程外部声明的变量是 *成员变量* 或 *字段*。</span><span class="sxs-lookup"><span data-stu-id="f88d0-162">A variable that is declared at module level, outside any procedure, is a *member variable* or *field*.</span></span> <span data-ttu-id="f88d0-163">成员变量在其类、结构或模块中的作用域内。</span><span class="sxs-lookup"><span data-stu-id="f88d0-163">Member variables are in scope throughout their class, structure, or module.</span></span> <span data-ttu-id="f88d0-164">在过程级别声明的变量是 *局部变量*。</span><span class="sxs-lookup"><span data-stu-id="f88d0-164">A variable that is declared at procedure level is a *local variable*.</span></span> <span data-ttu-id="f88d0-165">局部变量仅在其过程或块范围内。</span><span class="sxs-lookup"><span data-stu-id="f88d0-165">Local variables are in scope only within their procedure or block.</span></span>

<span data-ttu-id="f88d0-166">以下访问修饰符用于在过程外声明变量： `Public` 、 `Protected` 、 `Friend` 、 `Protected Friend` 和 `Private` 。</span><span class="sxs-lookup"><span data-stu-id="f88d0-166">The following access modifiers are used to declare variables outside a procedure: `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private`.</span></span> <span data-ttu-id="f88d0-167">有关详细信息，请参阅 [Visual Basic 中的访问级别](../../programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="f88d0-167">For more information, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="f88d0-168">`Dim`关键字是可选的，如果指定以下任意修饰符，通常省略此关键字： `Public` 、 `Protected` 、 `Friend` 、 `Protected Friend` 、、、、、 `Private` `Shared` `Shadows` `Static` `ReadOnly` 或 `WithEvents` 。</span><span class="sxs-lookup"><span data-stu-id="f88d0-168">The `Dim` keyword is optional and usually omitted if you specify any of the following modifiers: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`, or `WithEvents`.</span></span>

```vb
Public maximumAllowed As Double
Protected Friend currentUserName As String
Private salary As Decimal
Static runningTotal As Integer
```

<span data-ttu-id="f88d0-169">如果 `Option Explicit` (默认) 上，则编译器要求使用每个变量的声明。</span><span class="sxs-lookup"><span data-stu-id="f88d0-169">If `Option Explicit` is on (the default), the compiler requires a declaration for every variable you use.</span></span> <span data-ttu-id="f88d0-170">有关详细信息，请参阅 [Option Explicit 语句](option-explicit-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="f88d0-170">For more information, see [Option Explicit Statement](option-explicit-statement.md).</span></span>

## <a name="specifying-an-initial-value"></a><span data-ttu-id="f88d0-171">指定初始值</span><span class="sxs-lookup"><span data-stu-id="f88d0-171">Specifying an initial value</span></span>

<span data-ttu-id="f88d0-172">可以在创建变量时为该变量分配值。</span><span class="sxs-lookup"><span data-stu-id="f88d0-172">You can assign a value to a variable when it is created.</span></span> <span data-ttu-id="f88d0-173">对于值类型，使用 *初始值设定项* 提供要分配给变量的表达式。</span><span class="sxs-lookup"><span data-stu-id="f88d0-173">For a value type, you use an *initializer* to supply an expression to be assigned to the variable.</span></span> <span data-ttu-id="f88d0-174">表达式的计算结果必须为可在编译时计算的常数。</span><span class="sxs-lookup"><span data-stu-id="f88d0-174">The expression must evaluate to a constant that can be calculated at compile time.</span></span>

```vb
Dim quantity As Integer = 10
Dim message As String = "Just started"
```

<span data-ttu-id="f88d0-175">如果指定了初始值设定项并且子句中未指定数据类型 `As` ，则 *类型推理* 用于从初始值设定项推断数据类型。</span><span class="sxs-lookup"><span data-stu-id="f88d0-175">If an initializer is specified and a data type is not specified in an `As` clause, *type inference* is used to infer the data type from the initializer.</span></span> <span data-ttu-id="f88d0-176">在下面的示例中， `num1` 和 `num2` 均强类型化为整数。</span><span class="sxs-lookup"><span data-stu-id="f88d0-176">In the following example, both `num1` and `num2` are strongly typed as integers.</span></span> <span data-ttu-id="f88d0-177">在第二个声明中，类型推理从值3推断类型。</span><span class="sxs-lookup"><span data-stu-id="f88d0-177">In the second declaration, type inference infers the type from the value 3.</span></span>

```vb
' Use explicit typing.
Dim num1 As Integer = 3

' Use local type inference.
Dim num2 = 3
```

<span data-ttu-id="f88d0-178">类型推理适用于过程级别。</span><span class="sxs-lookup"><span data-stu-id="f88d0-178">Type inference applies at the procedure level.</span></span> <span data-ttu-id="f88d0-179">它不会应用于类、结构、模块或接口中的过程外部。</span><span class="sxs-lookup"><span data-stu-id="f88d0-179">It does not apply outside a procedure in a class, structure, module, or interface.</span></span> <span data-ttu-id="f88d0-180">有关类型推理的详细信息，请参阅 [选项推断语句](option-infer-statement.md) 和 [局部类型推理](../../programming-guide/language-features/variables/local-type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="f88d0-180">For more information about type inference, see [Option Infer Statement](option-infer-statement.md) and [Local Type Inference](../../programming-guide/language-features/variables/local-type-inference.md).</span></span>

<span data-ttu-id="f88d0-181">有关未指定数据类型或初始值设定项时所发生情况的信息，请参阅本主题后面的 [默认数据类型和值](dim-statement.md#default) 。</span><span class="sxs-lookup"><span data-stu-id="f88d0-181">For information about what happens when a data type or initializer is not specified, see [Default Data Types and Values](dim-statement.md#default) later in this topic.</span></span>

<span data-ttu-id="f88d0-182">可以使用 *对象初始值设定项* 声明命名类型和匿名类型的实例。</span><span class="sxs-lookup"><span data-stu-id="f88d0-182">You can use an *object initializer* to declare instances of named and anonymous types.</span></span> <span data-ttu-id="f88d0-183">下面的代码创建类的一个实例 `Student` ，并使用对象初始值设定项来初始化属性。</span><span class="sxs-lookup"><span data-stu-id="f88d0-183">The following code creates an instance of a `Student` class and uses an object initializer to initialize properties.</span></span>

```vb
Dim student1 As New Student With {.First = "Michael",
                                  .Last = "Tucker"}
```

<span data-ttu-id="f88d0-184">有关对象初始值设定项的详细信息，请参阅 [如何：使用对象初始值设定项声明对象](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)、 [对象初始值设定项：命名类型和匿名](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)类型和 [匿名类型](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="f88d0-184">For more information about object initializers, see [How to: Declare an Object by Using an Object Initializer](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [Object Initializers: Named and Anonymous Types](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md), and [Anonymous Types](../../programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>

## <a name="declaring-multiple-variables"></a><span data-ttu-id="f88d0-185">声明多个变量</span><span class="sxs-lookup"><span data-stu-id="f88d0-185">Declaring multiple variables</span></span>

<span data-ttu-id="f88d0-186">可以在一个声明语句中声明多个变量，并为每个变量指定变量名称，并在每个数组名称后面加上括号。</span><span class="sxs-lookup"><span data-stu-id="f88d0-186">You can declare several variables in one declaration statement, specifying the variable name for each one, and following each array name with parentheses.</span></span> <span data-ttu-id="f88d0-187">以逗号分隔多个变量。</span><span class="sxs-lookup"><span data-stu-id="f88d0-187">Multiple variables are separated by commas.</span></span>

```vb
Dim lastTime, nextTime, allTimes() As Date
```

<span data-ttu-id="f88d0-188">如果使用一个子句声明多个变量 `As` ，则不能为该变量组提供初始值设定项。</span><span class="sxs-lookup"><span data-stu-id="f88d0-188">If you declare more than one variable with one `As` clause, you cannot supply an initializer for that group of variables.</span></span>

<span data-ttu-id="f88d0-189">您可以为不同的变量指定不同的数据类型，方法是 `As` 为每个声明的变量使用单独的子句。</span><span class="sxs-lookup"><span data-stu-id="f88d0-189">You can specify different data types for different variables by using a separate `As` clause for each variable you declare.</span></span> <span data-ttu-id="f88d0-190">每个变量都采用在 `As` 其部分后遇到的第一个子句中指定的数据类型 `variablename` 。</span><span class="sxs-lookup"><span data-stu-id="f88d0-190">Each variable takes the data type specified in the first `As` clause encountered after its `variablename` part.</span></span>

```vb
Dim a, b, c As Single, x, y As Double, i As Integer
' a, b, and c are all Single; x and y are both Double
```

## <a name="arrays"></a><span data-ttu-id="f88d0-191">数组</span><span class="sxs-lookup"><span data-stu-id="f88d0-191">Arrays</span></span>

<span data-ttu-id="f88d0-192">您可以声明一个变量来保存一个 *数组*，该数组可以包含多个值。</span><span class="sxs-lookup"><span data-stu-id="f88d0-192">You can declare a variable to hold an *array*, which can hold multiple values.</span></span> <span data-ttu-id="f88d0-193">若要指定某个变量包含数组，请在其 `variablename` 前面加上括号。</span><span class="sxs-lookup"><span data-stu-id="f88d0-193">To specify that a variable holds an array, follow its `variablename` immediately with parentheses.</span></span> <span data-ttu-id="f88d0-194">有关数组的详细信息，请参阅[数组](../../programming-guide/language-features/arrays/index.md)。</span><span class="sxs-lookup"><span data-stu-id="f88d0-194">For more information about arrays, see [Arrays](../../programming-guide/language-features/arrays/index.md).</span></span>

<span data-ttu-id="f88d0-195">您可以指定数组的每个维度的下限和上限。</span><span class="sxs-lookup"><span data-stu-id="f88d0-195">You can specify the lower and upper bound of each dimension of an array.</span></span> <span data-ttu-id="f88d0-196">为此，请在 `boundslist` 括号内添加一个。</span><span class="sxs-lookup"><span data-stu-id="f88d0-196">To do this, include a `boundslist` inside the parentheses.</span></span> <span data-ttu-id="f88d0-197">对于每个维度， `boundslist` 指定上限和下限（可选）。</span><span class="sxs-lookup"><span data-stu-id="f88d0-197">For each dimension, the `boundslist` specifies the upper bound and optionally the lower bound.</span></span> <span data-ttu-id="f88d0-198">无论是否指定，下限始终为零。</span><span class="sxs-lookup"><span data-stu-id="f88d0-198">The lower bound is always zero, whether you specify it or not.</span></span> <span data-ttu-id="f88d0-199">每个索引的大小均为0到其上限值。</span><span class="sxs-lookup"><span data-stu-id="f88d0-199">Each index can vary from zero through its upper bound value.</span></span>

<span data-ttu-id="f88d0-200">下面两个语句是等效的。</span><span class="sxs-lookup"><span data-stu-id="f88d0-200">The following two statements are equivalent.</span></span> <span data-ttu-id="f88d0-201">每个语句声明21个元素的数组 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="f88d0-201">Each statement declares an array of 21 `Integer` elements.</span></span> <span data-ttu-id="f88d0-202">访问数组时，索引的取值可能为0到20。</span><span class="sxs-lookup"><span data-stu-id="f88d0-202">When you access the array, the index can vary from 0 through 20.</span></span>

```vb
Dim totals(20) As Integer
Dim totals(0 To 20) As Integer
```

<span data-ttu-id="f88d0-203">下面的语句声明一个类型为的二维数组 `Double` 。</span><span class="sxs-lookup"><span data-stu-id="f88d0-203">The following statement declares a two-dimensional array of type `Double`.</span></span> <span data-ttu-id="f88d0-204">数组有4行 (3 列，每) 6 列 (5 + 1) 每个列。</span><span class="sxs-lookup"><span data-stu-id="f88d0-204">The array has 4 rows (3 + 1) of 6 columns (5 + 1) each.</span></span> <span data-ttu-id="f88d0-205">请注意，上限表示索引的可能的最大值，而不是维度的长度。</span><span class="sxs-lookup"><span data-stu-id="f88d0-205">Note that an upper bound represents the highest possible value for the index, not the length of the dimension.</span></span> <span data-ttu-id="f88d0-206">维度的长度为上限加1。</span><span class="sxs-lookup"><span data-stu-id="f88d0-206">The length of the dimension is the upper bound plus one.</span></span>

```vb
Dim matrix2(3, 5) As Double
```

<span data-ttu-id="f88d0-207">数组的维数可以是1到32。</span><span class="sxs-lookup"><span data-stu-id="f88d0-207">An array can have from 1 to 32 dimensions.</span></span>

<span data-ttu-id="f88d0-208">可以在数组声明中保留所有界限为空。</span><span class="sxs-lookup"><span data-stu-id="f88d0-208">You can leave all the bounds blank in an array declaration.</span></span> <span data-ttu-id="f88d0-209">如果执行此操作，数组将具有指定的维度数，但未初始化。</span><span class="sxs-lookup"><span data-stu-id="f88d0-209">If you do this, the array has the number of dimensions you specify, but it is uninitialized.</span></span> <span data-ttu-id="f88d0-210">它的值为， `Nothing` 直到至少初始化其部分元素。</span><span class="sxs-lookup"><span data-stu-id="f88d0-210">It has a value of `Nothing` until you initialize at least some of its elements.</span></span> <span data-ttu-id="f88d0-211">`Dim`语句必须为所有维度或无维度指定界限。</span><span class="sxs-lookup"><span data-stu-id="f88d0-211">The `Dim` statement must specify bounds either for all dimensions or for no dimensions.</span></span>

```vb
' Declare an array with blank array bounds.
Dim messages() As String
' Initialize the array.
ReDim messages(4)
```

<span data-ttu-id="f88d0-212">如果数组具有多个维度，则必须在括号之间包含逗号以指示维数。</span><span class="sxs-lookup"><span data-stu-id="f88d0-212">If the array has more than one dimension, you must include commas between the parentheses to indicate the number of dimensions.</span></span>

```vb
Dim oneDimension(), twoDimensions(,), threeDimensions(,,) As Byte
```

<span data-ttu-id="f88d0-213">可以通过将数组的一个维度声明为-1，来声明 *长度为零的数组* 。</span><span class="sxs-lookup"><span data-stu-id="f88d0-213">You can declare a *zero-length array* by declaring one of the array's dimensions to be -1.</span></span> <span data-ttu-id="f88d0-214">保存零长度数组的变量不具有值 `Nothing` 。</span><span class="sxs-lookup"><span data-stu-id="f88d0-214">A variable that holds a zero-length array does not have the value `Nothing`.</span></span> <span data-ttu-id="f88d0-215">某些公共语言运行时函数需要零长度数组。</span><span class="sxs-lookup"><span data-stu-id="f88d0-215">Zero-length arrays are required by certain common language runtime functions.</span></span> <span data-ttu-id="f88d0-216">如果尝试访问此类数组，则会发生运行时异常。</span><span class="sxs-lookup"><span data-stu-id="f88d0-216">If you try to access such an array, a runtime exception occurs.</span></span> <span data-ttu-id="f88d0-217">有关详细信息，请参阅 [array](../../programming-guide/language-features/arrays/index.md)。</span><span class="sxs-lookup"><span data-stu-id="f88d0-217">For more information, see [Arrays](../../programming-guide/language-features/arrays/index.md).</span></span>

<span data-ttu-id="f88d0-218">可以通过使用数组文本初始化数组的值。</span><span class="sxs-lookup"><span data-stu-id="f88d0-218">You can initialize the values of an array by using an array literal.</span></span> <span data-ttu-id="f88d0-219">为此，请将初始化值括在大括号中， (`{}`) 。</span><span class="sxs-lookup"><span data-stu-id="f88d0-219">To do this, surround the initialization values with braces (`{}`).</span></span>

```vb
Dim longArray() As Long = {0, 1, 2, 3}
```

<span data-ttu-id="f88d0-220">对于多维数组，每个单独维度的初始化都括在外部维度中的大括号内。</span><span class="sxs-lookup"><span data-stu-id="f88d0-220">For multidimensional arrays, the initialization for each separate dimension is enclosed in braces in the outer dimension.</span></span> <span data-ttu-id="f88d0-221">元素按行主顺序指定。</span><span class="sxs-lookup"><span data-stu-id="f88d0-221">The elements are specified in row-major order.</span></span>

```vb
Dim twoDimensions(,) As Integer = {{0, 1, 2}, {10, 11, 12}}
```

<span data-ttu-id="f88d0-222">有关数组文本的详细信息，请参阅 [数组](../../programming-guide/language-features/arrays/index.md)。</span><span class="sxs-lookup"><span data-stu-id="f88d0-222">For more information about array literals, see [Arrays](../../programming-guide/language-features/arrays/index.md).</span></span>

## <a name="default-data-types-and-values"></a><a name="default"></a> <span data-ttu-id="f88d0-223">默认数据类型和值</span><span class="sxs-lookup"><span data-stu-id="f88d0-223">Default data types and values</span></span>

<span data-ttu-id="f88d0-224">下表描述了指定 `Dim` 语句中数据类型和初始值设定项的各种组合的结果。</span><span class="sxs-lookup"><span data-stu-id="f88d0-224">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>

|<span data-ttu-id="f88d0-225">是否指定数据类型？</span><span class="sxs-lookup"><span data-stu-id="f88d0-225">Data type specified?</span></span>|<span data-ttu-id="f88d0-226">是否指定初始值设定项？</span><span class="sxs-lookup"><span data-stu-id="f88d0-226">Initializer specified?</span></span>|<span data-ttu-id="f88d0-227">示例</span><span class="sxs-lookup"><span data-stu-id="f88d0-227">Example</span></span>|<span data-ttu-id="f88d0-228">结果</span><span class="sxs-lookup"><span data-stu-id="f88d0-228">Result</span></span>|
|---|---|---|---|
|<span data-ttu-id="f88d0-229">否</span><span class="sxs-lookup"><span data-stu-id="f88d0-229">No</span></span>|<span data-ttu-id="f88d0-230">否</span><span class="sxs-lookup"><span data-stu-id="f88d0-230">No</span></span>|`Dim qty`|<span data-ttu-id="f88d0-231">如果 [选项 Strict](option-strict-statement.md) 在默认)  (关闭，则将变量设置为 `Nothing` 。</span><span class="sxs-lookup"><span data-stu-id="f88d0-231">If [Option Strict](option-strict-statement.md) is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="f88d0-232">如果 `Option Strict` 处于打开状态，则发生编译时错误。</span><span class="sxs-lookup"><span data-stu-id="f88d0-232">If `Option Strict` is on, a compile-time error occurs.</span></span>|
|<span data-ttu-id="f88d0-233">否</span><span class="sxs-lookup"><span data-stu-id="f88d0-233">No</span></span>|<span data-ttu-id="f88d0-234">是</span><span class="sxs-lookup"><span data-stu-id="f88d0-234">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="f88d0-235">如果 [选项推断](option-infer-statement.md) (默认) 上，则该变量将采用初始值设定项的数据类型。</span><span class="sxs-lookup"><span data-stu-id="f88d0-235">If [Option Infer](option-infer-statement.md) is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="f88d0-236">请参阅 [局部类型推理](../../programming-guide/language-features/variables/local-type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="f88d0-236">See [Local Type Inference](../../programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="f88d0-237">如果 `Option Infer` 和 `Option Strict` 均处于关闭状态，则变量采用 `Object` 的数据类型。</span><span class="sxs-lookup"><span data-stu-id="f88d0-237">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="f88d0-238">如果 `Option Infer` 处于关闭状态但 `Option Strict` 处于打开状态，则发生编译时错误。</span><span class="sxs-lookup"><span data-stu-id="f88d0-238">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|
|<span data-ttu-id="f88d0-239">是</span><span class="sxs-lookup"><span data-stu-id="f88d0-239">Yes</span></span>|<span data-ttu-id="f88d0-240">否</span><span class="sxs-lookup"><span data-stu-id="f88d0-240">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="f88d0-241">将变量初始化为数据类型的默认值。</span><span class="sxs-lookup"><span data-stu-id="f88d0-241">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="f88d0-242">请参阅本部分后面的表。</span><span class="sxs-lookup"><span data-stu-id="f88d0-242">See the table later in this section.</span></span>|
|<span data-ttu-id="f88d0-243">是</span><span class="sxs-lookup"><span data-stu-id="f88d0-243">Yes</span></span>|<span data-ttu-id="f88d0-244">是</span><span class="sxs-lookup"><span data-stu-id="f88d0-244">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="f88d0-245">如果初始值设定项的数据类型不可转换为指定数据类型，则会发生编译时错误。</span><span class="sxs-lookup"><span data-stu-id="f88d0-245">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|

<span data-ttu-id="f88d0-246">如果指定数据类型但未指定初始值设定项，Visual Basic 会将变量初始化为其数据类型的默认值。</span><span class="sxs-lookup"><span data-stu-id="f88d0-246">If you specify a data type but do not specify an initializer, Visual Basic initializes the variable to the default value for its data type.</span></span> <span data-ttu-id="f88d0-247">下表显示了默认的初始化值。</span><span class="sxs-lookup"><span data-stu-id="f88d0-247">The following table shows the default initialization values.</span></span>

|<span data-ttu-id="f88d0-248">数据类型</span><span class="sxs-lookup"><span data-stu-id="f88d0-248">Data type</span></span>|<span data-ttu-id="f88d0-249">默认值</span><span class="sxs-lookup"><span data-stu-id="f88d0-249">Default value</span></span>|
|---|---|
|<span data-ttu-id="f88d0-250">所有数值类型 (包括 `Byte` 和 `SByte`) </span><span class="sxs-lookup"><span data-stu-id="f88d0-250">All numeric types (including `Byte` and `SByte`)</span></span>|<span data-ttu-id="f88d0-251">0</span><span class="sxs-lookup"><span data-stu-id="f88d0-251">0</span></span>|
|`Char`|<span data-ttu-id="f88d0-252">二进制0</span><span class="sxs-lookup"><span data-stu-id="f88d0-252">Binary 0</span></span>|
|<span data-ttu-id="f88d0-253">所有引用类型 (包括 `Object` 、 `String` 和所有数组) </span><span class="sxs-lookup"><span data-stu-id="f88d0-253">All reference types (including `Object`, `String`, and all arrays)</span></span>|`Nothing`|
|`Boolean`|`False`|
|`Date`|<span data-ttu-id="f88d0-254">12:00 年1月1日上午 (01/01/0001 12:00:00 AM) </span><span class="sxs-lookup"><span data-stu-id="f88d0-254">12:00 AM of January 1 of the year 1 (01/01/0001 12:00:00 AM)</span></span>|

<span data-ttu-id="f88d0-255">将结构的每个元素初始化为一个单独的变量。</span><span class="sxs-lookup"><span data-stu-id="f88d0-255">Each element of a structure is initialized as if it were a separate variable.</span></span> <span data-ttu-id="f88d0-256">如果声明数组的长度，但不初始化其元素，则会将每个元素初始化为单独的变量。</span><span class="sxs-lookup"><span data-stu-id="f88d0-256">If you declare the length of an array but do not initialize its elements, each element is initialized as if it were a separate variable.</span></span>

## <a name="static-local-variable-lifetime"></a><span data-ttu-id="f88d0-257">静态局部变量生存期</span><span class="sxs-lookup"><span data-stu-id="f88d0-257">Static local variable lifetime</span></span>

<span data-ttu-id="f88d0-258">`Static`局部变量的生存期比声明它的过程长。</span><span class="sxs-lookup"><span data-stu-id="f88d0-258">A `Static` local variable has a longer lifetime than that of the procedure in which it is declared.</span></span> <span data-ttu-id="f88d0-259">变量生存期的边界取决于声明过程的位置以及是否为 `Shared` 。</span><span class="sxs-lookup"><span data-stu-id="f88d0-259">The boundaries of the variable's lifetime depend on where the procedure is declared and whether it is `Shared`.</span></span>

|<span data-ttu-id="f88d0-260">过程声明</span><span class="sxs-lookup"><span data-stu-id="f88d0-260">Procedure declaration</span></span>|<span data-ttu-id="f88d0-261">变量已初始化</span><span class="sxs-lookup"><span data-stu-id="f88d0-261">Variable initialized</span></span>|<span data-ttu-id="f88d0-262">变量停止了现有</span><span class="sxs-lookup"><span data-stu-id="f88d0-262">Variable stops existing</span></span>|
|---|---|---|
|<span data-ttu-id="f88d0-263">在模块中</span><span class="sxs-lookup"><span data-stu-id="f88d0-263">In a module</span></span>|<span data-ttu-id="f88d0-264">第一次调用该过程时</span><span class="sxs-lookup"><span data-stu-id="f88d0-264">The first time the procedure is called</span></span>|<span data-ttu-id="f88d0-265">当程序停止执行时</span><span class="sxs-lookup"><span data-stu-id="f88d0-265">When your program stops execution</span></span>|
|<span data-ttu-id="f88d0-266">在类或结构中，过程是 `Shared`</span><span class="sxs-lookup"><span data-stu-id="f88d0-266">In a class or structure, procedure is `Shared`</span></span>|<span data-ttu-id="f88d0-267">第一次在特定实例或类或结构自身上调用该过程时</span><span class="sxs-lookup"><span data-stu-id="f88d0-267">The first time the procedure is called either on a specific instance or on the class or structure itself</span></span>|<span data-ttu-id="f88d0-268">当程序停止执行时</span><span class="sxs-lookup"><span data-stu-id="f88d0-268">When your program stops execution</span></span>|
|<span data-ttu-id="f88d0-269">在类或结构中，过程不是 `Shared`</span><span class="sxs-lookup"><span data-stu-id="f88d0-269">In a class or structure, procedure isn't `Shared`</span></span>|<span data-ttu-id="f88d0-270">第一次在特定实例上调用该过程时</span><span class="sxs-lookup"><span data-stu-id="f88d0-270">The first time the procedure is called on a specific instance</span></span>|<span data-ttu-id="f88d0-271">在释放实例以进行垃圾回收 (GC) </span><span class="sxs-lookup"><span data-stu-id="f88d0-271">When the instance is released for garbage collection (GC)</span></span>|

## <a name="attributes-and-modifiers"></a><span data-ttu-id="f88d0-272">特性和修饰符</span><span class="sxs-lookup"><span data-stu-id="f88d0-272">Attributes and modifiers</span></span>

<span data-ttu-id="f88d0-273">仅可将属性应用于成员变量，而不能应用于局部变量。</span><span class="sxs-lookup"><span data-stu-id="f88d0-273">You can apply attributes only to member variables, not to local variables.</span></span> <span data-ttu-id="f88d0-274">特性向程序集的元数据提供信息，这对于临时存储（如局部变量）没有意义。</span><span class="sxs-lookup"><span data-stu-id="f88d0-274">An attribute contributes information to the assembly's metadata, which is not meaningful for temporary storage such as local variables.</span></span>

<span data-ttu-id="f88d0-275">在模块级别，不能使用 `Static` 修饰符来声明成员变量。</span><span class="sxs-lookup"><span data-stu-id="f88d0-275">At module level, you cannot use the `Static` modifier to declare member variables.</span></span> <span data-ttu-id="f88d0-276">在过程级别，不能使用 `Shared` 、 `Shadows` 、 `ReadOnly` 、 `WithEvents` 或任何访问修饰符来声明局部变量。</span><span class="sxs-lookup"><span data-stu-id="f88d0-276">At procedure level, you cannot use `Shared`, `Shadows`, `ReadOnly`, `WithEvents`, or any access modifiers to declare local variables.</span></span>

<span data-ttu-id="f88d0-277">可以通过提供来指定哪些代码可以访问变量 `accessmodifier` 。</span><span class="sxs-lookup"><span data-stu-id="f88d0-277">You can specify what code can access a variable by supplying an `accessmodifier`.</span></span> <span data-ttu-id="f88d0-278">类和模块成员变量 (于任何过程之外) 默认为私有访问，而结构成员变量默认为公共访问。</span><span class="sxs-lookup"><span data-stu-id="f88d0-278">Class and module member variables (outside any procedure) default to private access, and structure member variables default to public access.</span></span> <span data-ttu-id="f88d0-279">您可以使用访问修饰符调整其访问级别。</span><span class="sxs-lookup"><span data-stu-id="f88d0-279">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="f88d0-280">不能在过程)  (中使用对本地变量的访问修饰符。</span><span class="sxs-lookup"><span data-stu-id="f88d0-280">You cannot use access modifiers on local variables (inside a procedure).</span></span>

<span data-ttu-id="f88d0-281">只能 `WithEvents` 在成员变量上指定，而不能指定过程内的局部变量。</span><span class="sxs-lookup"><span data-stu-id="f88d0-281">You can specify `WithEvents` only on member variables, not on local variables inside a procedure.</span></span> <span data-ttu-id="f88d0-282">如果指定 `WithEvents` ，则变量的数据类型必须是特定的类类型，而不是 `Object` 。</span><span class="sxs-lookup"><span data-stu-id="f88d0-282">If you specify `WithEvents`, the data type of the variable must be a specific class type, not `Object`.</span></span> <span data-ttu-id="f88d0-283">不能使用声明数组 `WithEvents` 。</span><span class="sxs-lookup"><span data-stu-id="f88d0-283">You cannot declare an array with `WithEvents`.</span></span> <span data-ttu-id="f88d0-284">有关事件的详细信息，请参阅 [事件](../../programming-guide/language-features/events/index.md)。</span><span class="sxs-lookup"><span data-stu-id="f88d0-284">For more information about events, see [Events](../../programming-guide/language-features/events/index.md).</span></span>

> [!NOTE]
> <span data-ttu-id="f88d0-285">类、结构或模块外的代码必须使用该类、结构或模块的名称来限定成员变量的名称。</span><span class="sxs-lookup"><span data-stu-id="f88d0-285">Code outside a class, structure, or module must qualify a member variable's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="f88d0-286">过程或块外的代码不能引用该过程或块中的任何局部变量。</span><span class="sxs-lookup"><span data-stu-id="f88d0-286">Code outside a procedure or block cannot refer to any local variables within that procedure or block.</span></span>

## <a name="releasing-managed-resources"></a><span data-ttu-id="f88d0-287">释放托管资源</span><span class="sxs-lookup"><span data-stu-id="f88d0-287">Releasing managed resources</span></span>

<span data-ttu-id="f88d0-288">.NET Framework 垃圾回收器会释放托管资源，而不会对你的部分进行任何额外编码。</span><span class="sxs-lookup"><span data-stu-id="f88d0-288">The .NET Framework garbage collector disposes of managed resources without any extra coding on your part.</span></span> <span data-ttu-id="f88d0-289">但是，您可以强制处置托管资源，而不是等待垃圾回收器。</span><span class="sxs-lookup"><span data-stu-id="f88d0-289">However, you can force the disposal of a managed resource instead of waiting for the garbage collector.</span></span>

<span data-ttu-id="f88d0-290">如果某个类保存在特别宝贵的资源上 (例如数据库连接或) 的文件句柄），则可能不希望等到下一次垃圾回收，以清理不再使用的类实例。</span><span class="sxs-lookup"><span data-stu-id="f88d0-290">If a class holds onto a particularly valuable and scarce resource (such as a database connection or file handle), you might not want to wait until the next garbage collection to clean up a class instance that's no longer in use.</span></span> <span data-ttu-id="f88d0-291">类可以实现 <xref:System.IDisposable> 接口，以提供一种在垃圾回收之前释放资源的方法。</span><span class="sxs-lookup"><span data-stu-id="f88d0-291">A class may implement the <xref:System.IDisposable> interface to provide a way to release resources before a garbage collection.</span></span> <span data-ttu-id="f88d0-292">实现该接口的类公开了一个 `Dispose` 方法，可以调用该方法来强制立即释放有价值的资源。</span><span class="sxs-lookup"><span data-stu-id="f88d0-292">A class that implements that interface exposes a `Dispose` method that can be called to force valuable resources to be released immediately.</span></span>

<span data-ttu-id="f88d0-293">`Using`语句会自动执行获取资源的过程、执行一组语句，然后释放资源。</span><span class="sxs-lookup"><span data-stu-id="f88d0-293">The `Using` statement automates the process of acquiring a resource, executing a set of statements, and then disposing of the resource.</span></span> <span data-ttu-id="f88d0-294">但是，资源必须实现 <xref:System.IDisposable> 接口。</span><span class="sxs-lookup"><span data-stu-id="f88d0-294">However, the resource must implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="f88d0-295">有关详细信息，请参阅 [Using 语句](using-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="f88d0-295">For more information, see [Using Statement](using-statement.md).</span></span>

## <a name="example"></a><span data-ttu-id="f88d0-296">示例</span><span class="sxs-lookup"><span data-stu-id="f88d0-296">Example</span></span>

<span data-ttu-id="f88d0-297">下面的示例通过使用 `Dim` 带有各种选项的语句来声明变量。</span><span class="sxs-lookup"><span data-stu-id="f88d0-297">The following example declares variables by using the `Dim` statement with various options.</span></span>

[!code-vb[VbVbalrStatements#141](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#141)]

## <a name="example"></a><span data-ttu-id="f88d0-298">示例</span><span class="sxs-lookup"><span data-stu-id="f88d0-298">Example</span></span>

<span data-ttu-id="f88d0-299">下面的示例列出了介于1和30之间的质数。</span><span class="sxs-lookup"><span data-stu-id="f88d0-299">The following example lists the prime numbers between 1 and 30.</span></span> <span data-ttu-id="f88d0-300">在代码注释中介绍了局部变量的作用域。</span><span class="sxs-lookup"><span data-stu-id="f88d0-300">The scope of local variables is described in code comments.</span></span>

[!code-vb[VbVbalrStatements#142](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#142)]

## <a name="example"></a><span data-ttu-id="f88d0-301">示例</span><span class="sxs-lookup"><span data-stu-id="f88d0-301">Example</span></span>

<span data-ttu-id="f88d0-302">在下面的示例中，在 `speedValue` 类级别声明变量。</span><span class="sxs-lookup"><span data-stu-id="f88d0-302">In the following example, the `speedValue` variable is declared at the class level.</span></span> <span data-ttu-id="f88d0-303">`Private`关键字用于声明变量。</span><span class="sxs-lookup"><span data-stu-id="f88d0-303">The `Private` keyword is used to declare the variable.</span></span> <span data-ttu-id="f88d0-304">类中的任何过程都可以访问该变量 `Car` 。</span><span class="sxs-lookup"><span data-stu-id="f88d0-304">The variable can be accessed by any procedure in the `Car` class.</span></span>

[!code-vb[VbVbalrStatements#144](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#144)]

[!code-vb[VbVbalrStatements#145](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#145)]

## <a name="see-also"></a><span data-ttu-id="f88d0-305">请参阅</span><span class="sxs-lookup"><span data-stu-id="f88d0-305">See also</span></span>

- [<span data-ttu-id="f88d0-306">Const 语句</span><span class="sxs-lookup"><span data-stu-id="f88d0-306">Const Statement</span></span>](const-statement.md)
- [<span data-ttu-id="f88d0-307">ReDim 语句</span><span class="sxs-lookup"><span data-stu-id="f88d0-307">ReDim Statement</span></span>](redim-statement.md)
- [<span data-ttu-id="f88d0-308">Option Explicit 语句</span><span class="sxs-lookup"><span data-stu-id="f88d0-308">Option Explicit Statement</span></span>](option-explicit-statement.md)
- [<span data-ttu-id="f88d0-309">Option Infer 语句</span><span class="sxs-lookup"><span data-stu-id="f88d0-309">Option Infer Statement</span></span>](option-infer-statement.md)
- [<span data-ttu-id="f88d0-310">Option Strict 语句</span><span class="sxs-lookup"><span data-stu-id="f88d0-310">Option Strict Statement</span></span>](option-strict-statement.md)
- [<span data-ttu-id="f88d0-311">“项目设计器”->“编译”页 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f88d0-311">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [<span data-ttu-id="f88d0-312">变量声明</span><span class="sxs-lookup"><span data-stu-id="f88d0-312">Variable Declaration</span></span>](../../programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="f88d0-313">数组</span><span class="sxs-lookup"><span data-stu-id="f88d0-313">Arrays</span></span>](../../programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="f88d0-314">对象初始值设定项：命名和匿名类型</span><span class="sxs-lookup"><span data-stu-id="f88d0-314">Object Initializers: Named and Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="f88d0-315">匿名类型</span><span class="sxs-lookup"><span data-stu-id="f88d0-315">Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="f88d0-316">对象初始值设定项：命名和匿名类型</span><span class="sxs-lookup"><span data-stu-id="f88d0-316">Object Initializers: Named and Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="f88d0-317">如何：使用对象初始值设定项声明对象</span><span class="sxs-lookup"><span data-stu-id="f88d0-317">How to: Declare an Object by Using an Object Initializer</span></span>](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
- [<span data-ttu-id="f88d0-318">局部类型推理</span><span class="sxs-lookup"><span data-stu-id="f88d0-318">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
