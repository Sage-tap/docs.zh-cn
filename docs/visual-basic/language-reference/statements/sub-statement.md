---
description: '了解详细信息： (Visual Basic 的 Sub 语句) '
title: Sub 语句
ms.date: 05/12/2018
f1_keywords:
- vb.Sub
helpviewer_keywords:
- Public keyword [Visual Basic], Sub statements
- procedures [Visual Basic], creating
- declaring procedures [Visual Basic], Sub statement
- arguments [Visual Basic], Sub procedures
- As keyword [Visual Basic], Sub statements
- Optional keyword [Visual Basic], Sub statements
- declarations [Visual Basic], procedures
- Sub keyword [Visual Basic]
- Handles keyword [Visual Basic], Sub statements
- Protected Friend keyword [Visual Basic]
- ParamArray keyword [Visual Basic], Sub statements
- Implements keyword [Visual Basic], Sub statements
- Sub statement [Visual Basic]
- subroutines
- ByRef keyword [Visual Basic], Sub statements
- Sub procedures [Visual Basic], Sub statement
- recursive procedures
- Private keyword [Visual Basic], Sub statements
- Friend keyword [Visual Basic], Sub statements
- Exit statement [Visual Basic], Sub statements
- procedures [Visual Basic], Sub
- End keyword [Visual Basic], Sub statements
- ByVal keyword [Visual Basic], Sub statements
- Visual Basic code, Sub procedures
ms.assetid: e347d700-d06c-405b-b302-e9b1edb57dfc
ms.openlocfilehash: 9be40c8284c677a151e4b1665f0b49e5f852bf00
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740985"
---
# <a name="sub-statement-visual-basic"></a><span data-ttu-id="282af-103">Sub 语句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="282af-103">Sub Statement (Visual Basic)</span></span>

<span data-ttu-id="282af-104">声明定义过程的名称、参数和代码 `Sub` 。</span><span class="sxs-lookup"><span data-stu-id="282af-104">Declares the name, parameters, and code that define a `Sub` procedure.</span></span>

## <a name="syntax"></a><span data-ttu-id="282af-105">语法</span><span class="sxs-lookup"><span data-stu-id="282af-105">Syntax</span></span>

```vb
[ <attributelist> ] [ Partial ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async ]
Sub name [ (Of typeparamlist) ] [ (parameterlist) ] [ Implements implementslist | Handles eventlist ]
    [ statements ]
    [ Exit Sub ]
    [ statements ]
End Sub
```

## <a name="parts"></a><span data-ttu-id="282af-106">组成部分</span><span class="sxs-lookup"><span data-stu-id="282af-106">Parts</span></span>

- `attributelist`

  <span data-ttu-id="282af-107">可选。</span><span class="sxs-lookup"><span data-stu-id="282af-107">Optional.</span></span> <span data-ttu-id="282af-108">请参阅 [特性列表](attribute-list.md)。</span><span class="sxs-lookup"><span data-stu-id="282af-108">See [Attribute List](attribute-list.md).</span></span>

- `Partial`

  <span data-ttu-id="282af-109">可选。</span><span class="sxs-lookup"><span data-stu-id="282af-109">Optional.</span></span> <span data-ttu-id="282af-110">指示分部方法的定义。</span><span class="sxs-lookup"><span data-stu-id="282af-110">Indicates definition of a partial method.</span></span> <span data-ttu-id="282af-111">请参阅 [分部方法](../../programming-guide/language-features/procedures/partial-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="282af-111">See [Partial Methods](../../programming-guide/language-features/procedures/partial-methods.md).</span></span>

- `accessmodifier`

  <span data-ttu-id="282af-112">可选。</span><span class="sxs-lookup"><span data-stu-id="282af-112">Optional.</span></span> <span data-ttu-id="282af-113">可以是以下其中一个值：</span><span class="sxs-lookup"><span data-stu-id="282af-113">Can be one of the following:</span></span>

  - [<span data-ttu-id="282af-114">公共</span><span class="sxs-lookup"><span data-stu-id="282af-114">Public</span></span>](../modifiers/public.md)

  - [<span data-ttu-id="282af-115">Protected</span><span class="sxs-lookup"><span data-stu-id="282af-115">Protected</span></span>](../modifiers/protected.md)

  - [<span data-ttu-id="282af-116">Friend</span><span class="sxs-lookup"><span data-stu-id="282af-116">Friend</span></span>](../modifiers/friend.md)

  - [<span data-ttu-id="282af-117">专用</span><span class="sxs-lookup"><span data-stu-id="282af-117">Private</span></span>](../modifiers/private.md)

  - [<span data-ttu-id="282af-118">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="282af-118">Protected Friend</span></span>](../modifiers/protected-friend.md)

  - [<span data-ttu-id="282af-119">Private Protected</span><span class="sxs-lookup"><span data-stu-id="282af-119">Private Protected</span></span>](../modifiers/private-protected.md)

  <span data-ttu-id="282af-120">请参阅 [Visual Basic 中的访问级别](../../programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="282af-120">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `proceduremodifiers`

  <span data-ttu-id="282af-121">可选。</span><span class="sxs-lookup"><span data-stu-id="282af-121">Optional.</span></span> <span data-ttu-id="282af-122">可以是以下其中一个值：</span><span class="sxs-lookup"><span data-stu-id="282af-122">Can be one of the following:</span></span>

  - [<span data-ttu-id="282af-123">重载</span><span class="sxs-lookup"><span data-stu-id="282af-123">Overloads</span></span>](../modifiers/overloads.md)

  - [<span data-ttu-id="282af-124">替代</span><span class="sxs-lookup"><span data-stu-id="282af-124">Overrides</span></span>](../modifiers/overrides.md)

  - [<span data-ttu-id="282af-125">Overrides</span><span class="sxs-lookup"><span data-stu-id="282af-125">Overridable</span></span>](../modifiers/overridable.md)

  - [<span data-ttu-id="282af-126">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="282af-126">NotOverridable</span></span>](../modifiers/notoverridable.md)

  - [<span data-ttu-id="282af-127">New</span><span class="sxs-lookup"><span data-stu-id="282af-127">MustOverride</span></span>](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  <span data-ttu-id="282af-128">可选。</span><span class="sxs-lookup"><span data-stu-id="282af-128">Optional.</span></span> <span data-ttu-id="282af-129">请参阅 [共享](../modifiers/shared.md)。</span><span class="sxs-lookup"><span data-stu-id="282af-129">See [Shared](../modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="282af-130">可选。</span><span class="sxs-lookup"><span data-stu-id="282af-130">Optional.</span></span> <span data-ttu-id="282af-131">请参阅 [阴影](../modifiers/shadows.md)。</span><span class="sxs-lookup"><span data-stu-id="282af-131">See [Shadows](../modifiers/shadows.md).</span></span>

- `Async`

  <span data-ttu-id="282af-132">可选。</span><span class="sxs-lookup"><span data-stu-id="282af-132">Optional.</span></span> <span data-ttu-id="282af-133">请参阅 [Async](../modifiers/async.md)。</span><span class="sxs-lookup"><span data-stu-id="282af-133">See [Async](../modifiers/async.md).</span></span>

- `name`

  <span data-ttu-id="282af-134">必需。</span><span class="sxs-lookup"><span data-stu-id="282af-134">Required.</span></span> <span data-ttu-id="282af-135">过程的名称。</span><span class="sxs-lookup"><span data-stu-id="282af-135">Name of the procedure.</span></span> <span data-ttu-id="282af-136">请参阅 [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="282af-136">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span> <span data-ttu-id="282af-137">若要为类创建构造函数过程，请将过程的名称设置 `Sub` 为 `New` 关键字。</span><span class="sxs-lookup"><span data-stu-id="282af-137">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="282af-138">有关详细信息，请参阅 [对象生存期：如何创建和销毁对象](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)。</span><span class="sxs-lookup"><span data-stu-id="282af-138">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>

- `typeparamlist`

  <span data-ttu-id="282af-139">可选。</span><span class="sxs-lookup"><span data-stu-id="282af-139">Optional.</span></span> <span data-ttu-id="282af-140">泛型过程的类型参数的列表。</span><span class="sxs-lookup"><span data-stu-id="282af-140">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="282af-141">请参阅 [类型列表](type-list.md)。</span><span class="sxs-lookup"><span data-stu-id="282af-141">See [Type List](type-list.md).</span></span>

- `parameterlist`

  <span data-ttu-id="282af-142">可选。</span><span class="sxs-lookup"><span data-stu-id="282af-142">Optional.</span></span> <span data-ttu-id="282af-143">表示此过程参数的本地变量名称列表。</span><span class="sxs-lookup"><span data-stu-id="282af-143">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="282af-144">请参阅 [参数列表](parameter-list.md)。</span><span class="sxs-lookup"><span data-stu-id="282af-144">See [Parameter List](parameter-list.md).</span></span>

- `Implements`

  <span data-ttu-id="282af-145">可选。</span><span class="sxs-lookup"><span data-stu-id="282af-145">Optional.</span></span> <span data-ttu-id="282af-146">指示此过程实现了一个或多个 `Sub` 过程，每个过程都在此过程的包含类或结构实现的接口中定义。</span><span class="sxs-lookup"><span data-stu-id="282af-146">Indicates that this procedure implements one or more `Sub` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="282af-147">请参阅 [Implements 语句](implements-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="282af-147">See [Implements Statement](implements-statement.md).</span></span>

- `implementslist`

  <span data-ttu-id="282af-148">如果提供 `Implements`，则是必需的。</span><span class="sxs-lookup"><span data-stu-id="282af-148">Required if `Implements` is supplied.</span></span> <span data-ttu-id="282af-149">所实现的 `Sub` 过程的列表。</span><span class="sxs-lookup"><span data-stu-id="282af-149">List of `Sub` procedures being implemented.</span></span>

  `implementedprocedure [ , implementedprocedure ... ]`

  <span data-ttu-id="282af-150">每个 `implementedprocedure` 都具有以下语法和部件：</span><span class="sxs-lookup"><span data-stu-id="282af-150">Each `implementedprocedure` has the following syntax and parts:</span></span>

  `interface.definedname`

  |<span data-ttu-id="282af-151">组成部分</span><span class="sxs-lookup"><span data-stu-id="282af-151">Part</span></span>|<span data-ttu-id="282af-152">说明</span><span class="sxs-lookup"><span data-stu-id="282af-152">Description</span></span>|
  |---|---|
  |`interface`|<span data-ttu-id="282af-153">必需。</span><span class="sxs-lookup"><span data-stu-id="282af-153">Required.</span></span> <span data-ttu-id="282af-154">此过程的包含类或结构实现的接口的名称。</span><span class="sxs-lookup"><span data-stu-id="282af-154">Name of an interface implemented by this procedure's containing class or structure.</span></span>|
  |`definedname`|<span data-ttu-id="282af-155">必需。</span><span class="sxs-lookup"><span data-stu-id="282af-155">Required.</span></span> <span data-ttu-id="282af-156">在 `interface` 中用于定义过程的名称。</span><span class="sxs-lookup"><span data-stu-id="282af-156">Name by which the procedure is defined in `interface`.</span></span>|

- `Handles`

  <span data-ttu-id="282af-157">可选。</span><span class="sxs-lookup"><span data-stu-id="282af-157">Optional.</span></span> <span data-ttu-id="282af-158">指示此过程可以处理一个或多个特定事件。</span><span class="sxs-lookup"><span data-stu-id="282af-158">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="282af-159">请参阅 [句柄](handles-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="282af-159">See [Handles](handles-clause.md).</span></span>

- `eventlist`

  <span data-ttu-id="282af-160">如果提供 `Handles`，则是必需的。</span><span class="sxs-lookup"><span data-stu-id="282af-160">Required if `Handles` is supplied.</span></span> <span data-ttu-id="282af-161">此过程处理的事件列表。</span><span class="sxs-lookup"><span data-stu-id="282af-161">List of events this procedure handles.</span></span>

  `eventspecifier [ , eventspecifier ... ]`

  <span data-ttu-id="282af-162">每个 `eventspecifier` 都具有以下语法和部件：</span><span class="sxs-lookup"><span data-stu-id="282af-162">Each `eventspecifier` has the following syntax and parts:</span></span>

  `eventvariable.event`

  |<span data-ttu-id="282af-163">组成部分</span><span class="sxs-lookup"><span data-stu-id="282af-163">Part</span></span>|<span data-ttu-id="282af-164">说明</span><span class="sxs-lookup"><span data-stu-id="282af-164">Description</span></span>|
  |---|---|
  |`eventvariable`|<span data-ttu-id="282af-165">必需。</span><span class="sxs-lookup"><span data-stu-id="282af-165">Required.</span></span> <span data-ttu-id="282af-166">用引发事件的类或结构的数据类型声明的对象变量。</span><span class="sxs-lookup"><span data-stu-id="282af-166">Object variable declared with the data type of the class or structure that raises the event.</span></span>|
  |`event`|<span data-ttu-id="282af-167">必需。</span><span class="sxs-lookup"><span data-stu-id="282af-167">Required.</span></span> <span data-ttu-id="282af-168">此过程处理的事件的名称。</span><span class="sxs-lookup"><span data-stu-id="282af-168">Name of the event this procedure handles.</span></span>|

- `statements`

  <span data-ttu-id="282af-169">可选。</span><span class="sxs-lookup"><span data-stu-id="282af-169">Optional.</span></span> <span data-ttu-id="282af-170">要在此过程中运行的语句块。</span><span class="sxs-lookup"><span data-stu-id="282af-170">Block of statements to run within this procedure.</span></span>

- `End Sub`

  <span data-ttu-id="282af-171">终止此过程的定义。</span><span class="sxs-lookup"><span data-stu-id="282af-171">Terminates the definition of this procedure.</span></span>

## <a name="remarks"></a><span data-ttu-id="282af-172">备注</span><span class="sxs-lookup"><span data-stu-id="282af-172">Remarks</span></span>

<span data-ttu-id="282af-173">所有可执行代码都必须在过程内。</span><span class="sxs-lookup"><span data-stu-id="282af-173">All executable code must be inside a procedure.</span></span> <span data-ttu-id="282af-174">`Sub`如果不想将值返回到调用代码，请使用过程。</span><span class="sxs-lookup"><span data-stu-id="282af-174">Use a `Sub` procedure when you don't want to return a value to the calling code.</span></span> <span data-ttu-id="282af-175">`Function`如果要返回值，请使用过程。</span><span class="sxs-lookup"><span data-stu-id="282af-175">Use a `Function` procedure when you want to return a value.</span></span>

## <a name="defining-a-sub-procedure"></a><span data-ttu-id="282af-176">定义 Sub 过程</span><span class="sxs-lookup"><span data-stu-id="282af-176">Defining a Sub Procedure</span></span>

<span data-ttu-id="282af-177">只能 `Sub` 在模块级别定义过程。</span><span class="sxs-lookup"><span data-stu-id="282af-177">You can define a `Sub` procedure only at the module level.</span></span> <span data-ttu-id="282af-178">因此，sub 过程的声明上下文必须是类、结构、模块或接口，不能是源文件、命名空间、过程或块。</span><span class="sxs-lookup"><span data-stu-id="282af-178">The declaration context for a sub procedure must, therefore, be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="282af-179">有关详细信息，请参阅[声明上下文和默认访问级别](declaration-contexts-and-default-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="282af-179">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="282af-180">`Sub` 过程默认为公共访问。</span><span class="sxs-lookup"><span data-stu-id="282af-180">`Sub` procedures default to public access.</span></span> <span data-ttu-id="282af-181">您可以使用访问修饰符调整其访问级别。</span><span class="sxs-lookup"><span data-stu-id="282af-181">You can adjust their access levels by using the access modifiers.</span></span>

<span data-ttu-id="282af-182">如果过程使用 `Implements` 关键字，则包含类或结构必须具有 `Implements` 紧跟在其或语句后面的语句 `Class` `Structure` 。</span><span class="sxs-lookup"><span data-stu-id="282af-182">If the procedure uses the `Implements` keyword, the containing class or structure must have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="282af-183">`Implements`语句必须包括在中指定的每个接口 `implementslist` 。</span><span class="sxs-lookup"><span data-stu-id="282af-183">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="282af-184">但是，接口用于定义 `Sub`) 中的 (的名称不必 `definedname` 与此过程在) 中 (的名称相匹配 `name` 。</span><span class="sxs-lookup"><span data-stu-id="282af-184">However, the name by which an interface defines the `Sub` (in `definedname`) doesn't have to match the name of this procedure (in `name`).</span></span>

## <a name="returning-from-a-sub-procedure"></a><span data-ttu-id="282af-185">从 Sub 过程返回</span><span class="sxs-lookup"><span data-stu-id="282af-185">Returning from a Sub Procedure</span></span>

<span data-ttu-id="282af-186">当 `Sub` 过程返回到调用代码时，执行将继续执行调用它的语句之后的语句。</span><span class="sxs-lookup"><span data-stu-id="282af-186">When a `Sub` procedure returns to the calling code, execution continues with the statement after the statement that called it.</span></span>

<span data-ttu-id="282af-187">下面的示例演示如何从过程返回 `Sub` 。</span><span class="sxs-lookup"><span data-stu-id="282af-187">The following example shows a return from a `Sub` procedure.</span></span>

```vb
Sub mySub(ByVal q As String)
    Return
End Sub
```

<span data-ttu-id="282af-188">`Exit Sub`和 `Return` 语句导致直接从 `Sub` 过程退出。</span><span class="sxs-lookup"><span data-stu-id="282af-188">The `Exit Sub` and `Return` statements cause an immediate exit from a `Sub` procedure.</span></span> <span data-ttu-id="282af-189">任意数量的 `Exit Sub` 和 `Return` 语句可以出现在过程中的任何位置，并且可以混合使用 `Exit Sub` 和 `Return` 语句。</span><span class="sxs-lookup"><span data-stu-id="282af-189">Any number of `Exit Sub` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Sub` and `Return` statements.</span></span>

## <a name="calling-a-sub-procedure"></a><span data-ttu-id="282af-190">调用 Sub 过程</span><span class="sxs-lookup"><span data-stu-id="282af-190">Calling a Sub Procedure</span></span>

<span data-ttu-id="282af-191">`Sub`通过在语句中使用过程名称，然后将该名称跟在括号中的参数列表后面来调用过程。</span><span class="sxs-lookup"><span data-stu-id="282af-191">You call a `Sub` procedure by using the procedure name in a statement and then following that name with its argument list in parentheses.</span></span> <span data-ttu-id="282af-192">仅当未提供任何参数时，才可以省略括号。</span><span class="sxs-lookup"><span data-stu-id="282af-192">You can omit the parentheses only if you don't supply any arguments.</span></span> <span data-ttu-id="282af-193">但是，如果你始终包含括号，你的代码将更具可读性。</span><span class="sxs-lookup"><span data-stu-id="282af-193">However, your code is more readable if you always include the parentheses.</span></span>

<span data-ttu-id="282af-194">`Sub`过程和 `Function` 过程可以具有参数并执行一系列语句。</span><span class="sxs-lookup"><span data-stu-id="282af-194">A `Sub` procedure and a `Function` procedure  can have parameters and perform a series of statements.</span></span> <span data-ttu-id="282af-195">但 `Function` 过程返回值，并且 `Sub` 过程不会。</span><span class="sxs-lookup"><span data-stu-id="282af-195">However, a `Function` procedure returns a value, and a `Sub` procedure doesn't.</span></span> <span data-ttu-id="282af-196">因此，不能 `Sub` 在表达式中使用过程。</span><span class="sxs-lookup"><span data-stu-id="282af-196">Therefore, you can't use a `Sub` procedure in an expression.</span></span>

<span data-ttu-id="282af-197">您可以在 `Call` 调用过程时使用关键字 `Sub` ，但对于大多数用途，不建议使用该关键字。</span><span class="sxs-lookup"><span data-stu-id="282af-197">You can use the `Call` keyword when you call a `Sub` procedure, but that keyword isn't recommended for most uses.</span></span> <span data-ttu-id="282af-198">有关详细信息，请参阅 [Call 语句](call-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="282af-198">For more information, see [Call Statement](call-statement.md).</span></span>

<span data-ttu-id="282af-199">Visual Basic 有时会重新排列算术表达式以提高内部效率。</span><span class="sxs-lookup"><span data-stu-id="282af-199">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="282af-200">出于此原因，如果参数列表包含调用其他过程的表达式，则不应假定将按特定顺序调用这些表达式。</span><span class="sxs-lookup"><span data-stu-id="282af-200">For that reason, if your argument list includes expressions that call other procedures, you shouldn't assume that those expressions will be called in a particular order.</span></span>

## <a name="async-sub-procedures"></a><span data-ttu-id="282af-201">Async Sub 过程</span><span class="sxs-lookup"><span data-stu-id="282af-201">Async Sub Procedures</span></span>

<span data-ttu-id="282af-202">通过使用异步功能，你可以调用异步函数而无需使用显式回调或在多个函数或 lambda 表达式中手动拆分你的代码。</span><span class="sxs-lookup"><span data-stu-id="282af-202">By using the Async feature, you can invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>

<span data-ttu-id="282af-203">如果使用 [Async](../modifiers/async.md) 修饰符标记过程，则可以在过程中使用 [Await](../operators/await-operator.md) 运算符。</span><span class="sxs-lookup"><span data-stu-id="282af-203">If you mark a procedure with the [Async](../modifiers/async.md) modifier, you can use the [Await](../operators/await-operator.md) operator in the procedure.</span></span> <span data-ttu-id="282af-204">当控件 `Await` 在过程中到达表达式时 `Async` ，控件将返回到调用方，并且在等待的任务完成之前，会挂起过程中的进度。</span><span class="sxs-lookup"><span data-stu-id="282af-204">When control reaches an `Await` expression in the `Async` procedure, control returns to the caller, and progress in the procedure is suspended until the awaited task completes.</span></span> <span data-ttu-id="282af-205">任务完成后，可以在过程中继续执行。</span><span class="sxs-lookup"><span data-stu-id="282af-205">When the task is complete, execution can resume in the procedure.</span></span>

> [!NOTE]
> <span data-ttu-id="282af-206">`Async`如果遇到了第一个尚未完成的对象或过程结束时 `Async` （以先发生者为准），则过程返回到调用方。</span><span class="sxs-lookup"><span data-stu-id="282af-206">An `Async` procedure returns to the caller when either the first awaited object that’s not yet complete is encountered or the end of the `Async` procedure is reached, whichever occurs first.</span></span>

<span data-ttu-id="282af-207">还可以使用修饰符标记 [函数语句](function-statement.md) `Async` 。</span><span class="sxs-lookup"><span data-stu-id="282af-207">You can also mark a [Function Statement](function-statement.md) with the `Async` modifier.</span></span> <span data-ttu-id="282af-208">`Async`函数的返回类型可以是 <xref:System.Threading.Tasks.Task%601> 或 <xref:System.Threading.Tasks.Task> 。</span><span class="sxs-lookup"><span data-stu-id="282af-208">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="282af-209">本主题后面的示例演示了 `Async` 返回类型为的函数 <xref:System.Threading.Tasks.Task%601> 。</span><span class="sxs-lookup"><span data-stu-id="282af-209">An example later in this topic shows an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span>

<span data-ttu-id="282af-210">`Async``Sub`过程主要用于事件处理程序，其中不能返回值。</span><span class="sxs-lookup"><span data-stu-id="282af-210">`Async` `Sub` procedures are primarily used for event handlers, where a value can't be returned.</span></span> <span data-ttu-id="282af-211">`Async` `Sub` 无法等待过程，并且过程的调用方 `Async` `Sub` 无法捕获该 `Sub` 过程引发的异常。</span><span class="sxs-lookup"><span data-stu-id="282af-211">An `Async` `Sub` procedure can't be awaited, and the caller of an `Async` `Sub` procedure can't catch exceptions that the `Sub` procedure throws.</span></span>

<span data-ttu-id="282af-212">`Async`过程不能声明任何[ByRef](../modifiers/byref.md)参数。</span><span class="sxs-lookup"><span data-stu-id="282af-212">An `Async` procedure can't declare any [ByRef](../modifiers/byref.md) parameters.</span></span>

<span data-ttu-id="282af-213">有关过程的详细信息 `Async` ，请参阅 [采用 Async 和 Await 的异步编程](../../programming-guide/concepts/async/index.md)、 [异步程序中的控制流](../../programming-guide/concepts/async/control-flow-in-async-programs.md)和 [异步返回类型](../../programming-guide/concepts/async/async-return-types.md)。</span><span class="sxs-lookup"><span data-stu-id="282af-213">For more information about `Async` procedures, see [Asynchronous Programming with Async and Await](../../programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../programming-guide/concepts/async/async-return-types.md).</span></span>

## <a name="example"></a><span data-ttu-id="282af-214">示例</span><span class="sxs-lookup"><span data-stu-id="282af-214">Example</span></span>

<span data-ttu-id="282af-215">下面的示例使用 `Sub` 语句来定义构成过程正文的名称、参数和代码 `Sub` 。</span><span class="sxs-lookup"><span data-stu-id="282af-215">The following example uses the `Sub` statement to define the name, parameters, and code that form the body of a `Sub` procedure.</span></span>

[!code-vb[VbVbalrStatements#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#58)]

## <a name="example"></a><span data-ttu-id="282af-216">示例</span><span class="sxs-lookup"><span data-stu-id="282af-216">Example</span></span>

<span data-ttu-id="282af-217">在下面的示例中， `DelayAsync` 是 `Async` `Function` 具有返回类型的 <xref:System.Threading.Tasks.Task%601> 。</span><span class="sxs-lookup"><span data-stu-id="282af-217">In the following example, `DelayAsync` is an `Async` `Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="282af-218">`DelayAsync` 具有返回整数的 `Return` 语句。</span><span class="sxs-lookup"><span data-stu-id="282af-218">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="282af-219">因此，的函数声明 `DelayAsync` 必须具有返回类型 `Task(Of Integer)` 。</span><span class="sxs-lookup"><span data-stu-id="282af-219">Therefore, the function declaration of `DelayAsync` must have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="282af-220">由于返回类型是 `Task(Of Integer)` ，中表达式的计算会 `Await` `DoSomethingAsync` 生成一个整数，如以下语句所示： `Dim result As Integer = Await delayTask` 。</span><span class="sxs-lookup"><span data-stu-id="282af-220">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer, as the following statement shows: `Dim result As Integer = Await delayTask`.</span></span>

<span data-ttu-id="282af-221">此 `startButton_Click` 过程是过程的示例 `Async Sub` 。</span><span class="sxs-lookup"><span data-stu-id="282af-221">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="282af-222">由于 `DoSomethingAsync` 是一个 `Async` 函数，因此对的调用的任务 `DoSomethingAsync` 必须等待，如以下语句所示： `Await DoSomethingAsync()` 。</span><span class="sxs-lookup"><span data-stu-id="282af-222">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement shows: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="282af-223">此 `startButton_Click` `Sub` 过程必须使用修饰符进行定义， `Async` 因为它具有 `Await` 表达式。</span><span class="sxs-lookup"><span data-stu-id="282af-223">The `startButton_Click` `Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a><span data-ttu-id="282af-224">请参阅</span><span class="sxs-lookup"><span data-stu-id="282af-224">See also</span></span>

- [<span data-ttu-id="282af-225">Implements 语句</span><span class="sxs-lookup"><span data-stu-id="282af-225">Implements Statement</span></span>](implements-statement.md)
- [<span data-ttu-id="282af-226">Function 语句</span><span class="sxs-lookup"><span data-stu-id="282af-226">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="282af-227">参数列表</span><span class="sxs-lookup"><span data-stu-id="282af-227">Parameter List</span></span>](parameter-list.md)
- [<span data-ttu-id="282af-228">Dim 语句</span><span class="sxs-lookup"><span data-stu-id="282af-228">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="282af-229">Call 语句</span><span class="sxs-lookup"><span data-stu-id="282af-229">Call Statement</span></span>](call-statement.md)
- [<span data-ttu-id="282af-230">个</span><span class="sxs-lookup"><span data-stu-id="282af-230">Of</span></span>](of-clause.md)
- [<span data-ttu-id="282af-231">参数数组</span><span class="sxs-lookup"><span data-stu-id="282af-231">Parameter Arrays</span></span>](../../programming-guide/language-features/procedures/parameter-arrays.md)
- [<span data-ttu-id="282af-232">如何：使用泛型类</span><span class="sxs-lookup"><span data-stu-id="282af-232">How to: Use a Generic Class</span></span>](../../programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="282af-233">过程疑难解答</span><span class="sxs-lookup"><span data-stu-id="282af-233">Troubleshooting Procedures</span></span>](../../programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [<span data-ttu-id="282af-234">分部方法</span><span class="sxs-lookup"><span data-stu-id="282af-234">Partial Methods</span></span>](../../programming-guide/language-features/procedures/partial-methods.md)
