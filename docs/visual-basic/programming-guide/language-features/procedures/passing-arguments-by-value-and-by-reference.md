---
description: '了解详细信息：按值和按引用传递自变量 (Visual Basic) '
title: 按值和按引用传递参数
ms.date: 07/20/2015
helpviewer_keywords:
- ByRef keyword [Visual Basic], passing arguments by reference
- Visual Basic code, procedures
- passing arguments [Visual Basic], by value or by reference
- ByVal keyword [Visual Basic], passing arguments by value
- arguments [Visual Basic], passing by value or by reference
- argument passing [Visual Basic], by value or by reference
ms.assetid: fd8a9de6-7178-44d5-a9bf-458d4ad907c2
ms.openlocfilehash: dbe020a7fffd48c14d377fff740f57e4bcc43ed2
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466674"
---
# <a name="passing-arguments-by-value-and-by-reference-visual-basic"></a><span data-ttu-id="68378-103">通过值和通过引用传递参数 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="68378-103">Passing Arguments by Value and by Reference (Visual Basic)</span></span>

<span data-ttu-id="68378-104">在 Visual Basic 中，可以 *通过值* 或 *引用* 将参数传递给过程。</span><span class="sxs-lookup"><span data-stu-id="68378-104">In Visual Basic, you can pass an argument to a procedure *by value* or *by reference*.</span></span> <span data-ttu-id="68378-105">这称为 *传递机制*，它确定过程是否可以修改调用代码中参数的基础编程元素。</span><span class="sxs-lookup"><span data-stu-id="68378-105">This is known as the *passing mechanism*, and it determines whether the procedure can modify the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="68378-106">过程声明通过指定 [ByVal](../../../language-reference/modifiers/byval.md) 或 [ByRef](../../../language-reference/modifiers/byref.md) 关键字来确定每个参数的传递机制。</span><span class="sxs-lookup"><span data-stu-id="68378-106">The procedure declaration determines the passing mechanism for each parameter by specifying the [ByVal](../../../language-reference/modifiers/byval.md) or [ByRef](../../../language-reference/modifiers/byref.md) keyword.</span></span>  
  
## <a name="distinctions"></a><span data-ttu-id="68378-107">区别</span><span class="sxs-lookup"><span data-stu-id="68378-107">Distinctions</span></span>  

 <span data-ttu-id="68378-108">将参数传递给过程时，请注意彼此交互的几个不同的区别：</span><span class="sxs-lookup"><span data-stu-id="68378-108">When passing an argument to a procedure, be aware of several different distinctions that interact with each other:</span></span>  
  
- <span data-ttu-id="68378-109">基础编程元素是否可修改或不可更改</span><span class="sxs-lookup"><span data-stu-id="68378-109">Whether the underlying programming element is modifiable or nonmodifiable</span></span>  
  
- <span data-ttu-id="68378-110">参数本身是否可修改或不可更改</span><span class="sxs-lookup"><span data-stu-id="68378-110">Whether the argument itself is modifiable or nonmodifiable</span></span>  
  
- <span data-ttu-id="68378-111">参数是通过值还是通过引用传递</span><span class="sxs-lookup"><span data-stu-id="68378-111">Whether the argument is being passed by value or by reference</span></span>  
  
- <span data-ttu-id="68378-112">参数数据类型是值类型还是引用类型</span><span class="sxs-lookup"><span data-stu-id="68378-112">Whether the argument data type is a value type or a reference type</span></span>  
  
 <span data-ttu-id="68378-113">有关详细信息，请参阅可 [修改和不可修改参数](./differences-between-modifiable-and-nonmodifiable-arguments.md) 与通过 [值传递参数和通过引用传递参数](./differences-between-passing-an-argument-by-value-and-by-reference.md)之间的差异。</span><span class="sxs-lookup"><span data-stu-id="68378-113">For more information, see [Differences Between Modifiable and Nonmodifiable Arguments](./differences-between-modifiable-and-nonmodifiable-arguments.md) and [Differences Between Passing an Argument By Value and By Reference](./differences-between-passing-an-argument-by-value-and-by-reference.md).</span></span>  
  
## <a name="choice-of-passing-mechanism"></a><span data-ttu-id="68378-114">选择传递机制</span><span class="sxs-lookup"><span data-stu-id="68378-114">Choice of Passing Mechanism</span></span>  

 <span data-ttu-id="68378-115">应为每个参数仔细选择传递机制。</span><span class="sxs-lookup"><span data-stu-id="68378-115">You should choose the passing mechanism carefully for each argument.</span></span>  
  
- <span data-ttu-id="68378-116">**保护**。</span><span class="sxs-lookup"><span data-stu-id="68378-116">**Protection**.</span></span> <span data-ttu-id="68378-117">在两个传递机制之间进行选择时，最重要的条件是公开调用变量以进行更改。</span><span class="sxs-lookup"><span data-stu-id="68378-117">In choosing between the two passing mechanisms, the most important criterion is the exposure of calling variables to change.</span></span> <span data-ttu-id="68378-118">传递参数的优点 `ByRef` 是过程可以通过该参数将值返回给调用代码。</span><span class="sxs-lookup"><span data-stu-id="68378-118">The advantage of passing an argument `ByRef` is that the procedure can return a value to the calling code through that argument.</span></span> <span data-ttu-id="68378-119">传递参数的优点在于 `ByVal` ，它可以防止变量被过程更改。</span><span class="sxs-lookup"><span data-stu-id="68378-119">The advantage of passing an argument `ByVal` is that it protects a variable from being changed by the procedure.</span></span>  
  
- <span data-ttu-id="68378-120">性能。</span><span class="sxs-lookup"><span data-stu-id="68378-120">**Performance**.</span></span> <span data-ttu-id="68378-121">尽管传递机制可能会影响你的代码的性能，但差别通常是不重要的。</span><span class="sxs-lookup"><span data-stu-id="68378-121">Although the passing mechanism can affect the performance of your code, the difference is usually insignificant.</span></span> <span data-ttu-id="68378-122">这种情况的一个例外是传递了一个值类型 `ByVal` 。</span><span class="sxs-lookup"><span data-stu-id="68378-122">One exception to this is a value type passed `ByVal`.</span></span> <span data-ttu-id="68378-123">在这种情况下，Visual Basic 会复制参数的所有数据内容。</span><span class="sxs-lookup"><span data-stu-id="68378-123">In this case, Visual Basic copies the entire data contents of the argument.</span></span> <span data-ttu-id="68378-124">因此，对于大值类型（如结构），传递它会更有效 `ByRef` 。</span><span class="sxs-lookup"><span data-stu-id="68378-124">Therefore, for a large value type such as a structure, it can be more efficient to pass it `ByRef`.</span></span>  
  
     <span data-ttu-id="68378-125">对于引用类型，仅将指向数据的指针复制 (32 位平台上的四个字节，64位平台上的8个字节) 。</span><span class="sxs-lookup"><span data-stu-id="68378-125">For reference types, only the pointer to the data is copied (four bytes on 32-bit platforms, eight bytes on 64-bit platforms).</span></span> <span data-ttu-id="68378-126">因此，可以传递类型的参数或通过值传递的参数， `String` `Object` 而不会对性能有损害。</span><span class="sxs-lookup"><span data-stu-id="68378-126">Therefore, you can pass arguments of type `String` or `Object` by value without harming performance.</span></span>  
  
## <a name="determination-of-the-passing-mechanism"></a><span data-ttu-id="68378-127">确定传递机制</span><span class="sxs-lookup"><span data-stu-id="68378-127">Determination of the Passing Mechanism</span></span>  

 <span data-ttu-id="68378-128">过程声明指定每个参数的传递机制。</span><span class="sxs-lookup"><span data-stu-id="68378-128">The procedure declaration specifies the passing mechanism for each parameter.</span></span> <span data-ttu-id="68378-129">调用代码无法重写 `ByVal` 机制。</span><span class="sxs-lookup"><span data-stu-id="68378-129">The calling code can't override a `ByVal` mechanism.</span></span>  
  
 <span data-ttu-id="68378-130">如果使用声明参数 `ByRef` ，则调用代码可以 `ByVal` 通过在调用中将参数名称括在括号中来强制机制。</span><span class="sxs-lookup"><span data-stu-id="68378-130">If a parameter is declared with `ByRef`, the calling code can force the mechanism to `ByVal` by enclosing the argument name in parentheses in the call.</span></span> <span data-ttu-id="68378-131">有关详细信息，请参阅 [如何：强制通过值传递参数](./how-to-force-an-argument-to-be-passed-by-value.md)。</span><span class="sxs-lookup"><span data-stu-id="68378-131">For more information, see [How to: Force an Argument to Be Passed by Value](./how-to-force-an-argument-to-be-passed-by-value.md).</span></span>  
  
 <span data-ttu-id="68378-132">Visual Basic 中的默认值是按值传递参数。</span><span class="sxs-lookup"><span data-stu-id="68378-132">The default in Visual Basic is to pass arguments by value.</span></span>  
  
## <a name="when-to-pass-an-argument-by-value"></a><span data-ttu-id="68378-133">何时按值传递参数</span><span class="sxs-lookup"><span data-stu-id="68378-133">When to Pass an Argument by Value</span></span>  
  
- <span data-ttu-id="68378-134">如果作为参数的基础的调用代码元素是不可更改的元素，则声明相应的参数 [ByVal](../../../language-reference/modifiers/byval.md)。</span><span class="sxs-lookup"><span data-stu-id="68378-134">If the calling code element underlying the argument is a nonmodifiable element, declare the corresponding parameter [ByVal](../../../language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="68378-135">任何代码都不能更改不可更改元素的值。</span><span class="sxs-lookup"><span data-stu-id="68378-135">No code can change the value of a nonmodifiable element.</span></span>  
  
- <span data-ttu-id="68378-136">如果基础元素可修改，但您不希望该过程更改其值，则声明参数 `ByVal` 。</span><span class="sxs-lookup"><span data-stu-id="68378-136">If the underlying element is modifiable, but you do not want the procedure to be able to change its value, declare the parameter `ByVal`.</span></span> <span data-ttu-id="68378-137">只有调用代码可以更改通过值传递的可修改元素的值。</span><span class="sxs-lookup"><span data-stu-id="68378-137">Only the calling code can change the value of a modifiable element passed by value.</span></span>  
  
## <a name="when-to-pass-an-argument-by-reference"></a><span data-ttu-id="68378-138">何时通过引用传递自变量</span><span class="sxs-lookup"><span data-stu-id="68378-138">When to Pass an Argument by Reference</span></span>  
  
- <span data-ttu-id="68378-139">如果过程确实需要更改调用代码中的基础元素，请声明相应的参数 [ByRef](../../../language-reference/modifiers/byref.md)。</span><span class="sxs-lookup"><span data-stu-id="68378-139">If the procedure has a genuine need to change the underlying element in the calling code, declare the corresponding parameter [ByRef](../../../language-reference/modifiers/byref.md).</span></span>  
  
- <span data-ttu-id="68378-140">如果正确执行代码取决于更改调用代码中基础元素的过程，请声明参数 `ByRef` 。</span><span class="sxs-lookup"><span data-stu-id="68378-140">If the correct execution of the code depends on the procedure changing the underlying element in the calling code, declare the parameter `ByRef`.</span></span> <span data-ttu-id="68378-141">如果按值传递它，或者调用代码 `ByRef` 通过将参数括在括号中来覆盖传递机制，则过程调用可能会产生意外的结果。</span><span class="sxs-lookup"><span data-stu-id="68378-141">If you pass it by value, or if the calling code overrides the `ByRef` passing mechanism by enclosing the argument in parentheses, the procedure call might produce unexpected results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="68378-142">示例</span><span class="sxs-lookup"><span data-stu-id="68378-142">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="68378-143">说明</span><span class="sxs-lookup"><span data-stu-id="68378-143">Description</span></span>  

 <span data-ttu-id="68378-144">下面的示例说明何时按值传递参数，以及何时通过引用传递参数。</span><span class="sxs-lookup"><span data-stu-id="68378-144">The following example illustrates when to pass arguments by value and when to pass them by reference.</span></span> <span data-ttu-id="68378-145">过程 `Calculate` 具有 `ByVal` 和 `ByRef` 参数。</span><span class="sxs-lookup"><span data-stu-id="68378-145">Procedure `Calculate` has both a `ByVal` and a `ByRef` parameter.</span></span> <span data-ttu-id="68378-146">对于利率、 `rate` 和金钱的总和， `debt` 此过程的任务是为计算一个新值 `debt` ，这是将利率应用于原始值的结果 `debt` 。</span><span class="sxs-lookup"><span data-stu-id="68378-146">Given an interest rate, `rate`, and a sum of money, `debt`, the task of the procedure is to calculate a new value for `debt` that is the result of applying the interest rate to the original value of `debt`.</span></span> <span data-ttu-id="68378-147">由于 `debt` 是一个 `ByRef` 参数，因此新的总计将反映在与对应的调用代码中的参数值中 `debt` 。</span><span class="sxs-lookup"><span data-stu-id="68378-147">Because `debt` is a `ByRef` parameter, the new total is reflected in the value of the argument in the calling code that corresponds to `debt`.</span></span> <span data-ttu-id="68378-148">参数 `rate` 是一个 `ByVal` 参数，因为 `Calculate` 不应更改其值。</span><span class="sxs-lookup"><span data-stu-id="68378-148">Parameter `rate` is a `ByVal` parameter because `Calculate` should not change its value.</span></span>  
  
### <a name="code"></a><span data-ttu-id="68378-149">代码</span><span class="sxs-lookup"><span data-stu-id="68378-149">Code</span></span>  

 [!code-vb[VbVbcnProcedures#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class2.vb#74)]  
  
## <a name="see-also"></a><span data-ttu-id="68378-150">请参阅</span><span class="sxs-lookup"><span data-stu-id="68378-150">See also</span></span>

- [<span data-ttu-id="68378-151">过程</span><span class="sxs-lookup"><span data-stu-id="68378-151">Procedures</span></span>](./index.md)
- [<span data-ttu-id="68378-152">过程形参和实参</span><span class="sxs-lookup"><span data-stu-id="68378-152">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="68378-153">如何：将参数传递给过程</span><span class="sxs-lookup"><span data-stu-id="68378-153">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="68378-154">如何：更改过程参数的值</span><span class="sxs-lookup"><span data-stu-id="68378-154">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)
- [<span data-ttu-id="68378-155">如何：防止过程参数的值被更改</span><span class="sxs-lookup"><span data-stu-id="68378-155">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="68378-156">如何：强制通过值传递参数</span><span class="sxs-lookup"><span data-stu-id="68378-156">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)
- [<span data-ttu-id="68378-157">按位置和按名称传递自变量</span><span class="sxs-lookup"><span data-stu-id="68378-157">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="68378-158">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="68378-158">Value Types and Reference Types</span></span>](../data-types/value-types-and-reference-types.md)
