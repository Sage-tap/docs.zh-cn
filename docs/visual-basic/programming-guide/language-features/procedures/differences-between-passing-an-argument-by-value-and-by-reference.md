---
description: '了解详细信息：按值传递自变量和通过引用传递参数 (Visual Basic 的差异) '
title: 通过值传递参数和通过引用传递参数之间的差异
ms.date: 07/20/2015
helpviewer_keywords:
- ByRef keyword [Visual Basic], passing arguments by reference
- Visual Basic code, procedures
- procedures [Visual Basic], passing arguments
- ByVal keyword [Visual Basic], passing arguments by value
- arguments [Visual Basic], passing by value or by reference
ms.assetid: 5f5c38fe-3e2d-494c-8fff-f4025b55ec93
ms.openlocfilehash: 632895eae82a20c9bcd773da71f88ebef26d786c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100464724"
---
# <a name="differences-between-passing-an-argument-by-value-and-by-reference-visual-basic"></a><span data-ttu-id="01b4e-103">通过值传递参数和通过引用传递参数之间的差异 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01b4e-103">Differences Between Passing an Argument By Value and By Reference (Visual Basic)</span></span>

<span data-ttu-id="01b4e-104">将一个或多个自变量传递给过程时，每个参数都对应于调用代码中的基础编程元素。</span><span class="sxs-lookup"><span data-stu-id="01b4e-104">When you pass one or more arguments to a procedure, each argument corresponds to an underlying programming element in the calling code.</span></span> <span data-ttu-id="01b4e-105">可以传递此基础元素的值或对其的引用。</span><span class="sxs-lookup"><span data-stu-id="01b4e-105">You can pass either the value of this underlying element, or a reference to it.</span></span> <span data-ttu-id="01b4e-106">这称为 *传递机制*。</span><span class="sxs-lookup"><span data-stu-id="01b4e-106">This is known as the *passing mechanism*.</span></span>  
  
## <a name="passing-by-value"></a><span data-ttu-id="01b4e-107">按值传递</span><span class="sxs-lookup"><span data-stu-id="01b4e-107">Passing by Value</span></span>  

 <span data-ttu-id="01b4e-108">通过 *值* 传递自变量，方法是在过程定义中为相应的参数指定 [ByVal](../../../language-reference/modifiers/byval.md) 关键字。</span><span class="sxs-lookup"><span data-stu-id="01b4e-108">You pass an argument *by value* by specifying the [ByVal](../../../language-reference/modifiers/byval.md) keyword for the corresponding parameter in the procedure definition.</span></span> <span data-ttu-id="01b4e-109">使用此传递机制时，Visual Basic 会将基础编程元素的值复制到过程中的局部变量中。</span><span class="sxs-lookup"><span data-stu-id="01b4e-109">When you use this passing mechanism, Visual Basic copies the value of the underlying programming element into a local variable in the procedure.</span></span> <span data-ttu-id="01b4e-110">过程代码对调用代码中的基础元素没有任何访问权限。</span><span class="sxs-lookup"><span data-stu-id="01b4e-110">The procedure code does not have any access to the underlying element in the calling code.</span></span>  
  
## <a name="passing-by-reference"></a><span data-ttu-id="01b4e-111">按引用传递</span><span class="sxs-lookup"><span data-stu-id="01b4e-111">Passing by Reference</span></span>  

 <span data-ttu-id="01b4e-112">通过在过程定义中为相应的参数指定 [ByRef](../../../language-reference/modifiers/byref.md)关键字，可以通过 *引用* 传递自变量。</span><span class="sxs-lookup"><span data-stu-id="01b4e-112">You pass an argument *by reference* by specifying the [ByRef](../../../language-reference/modifiers/byref.md) keyword for the corresponding parameter in the procedure definition.</span></span> <span data-ttu-id="01b4e-113">使用此传递机制时，Visual Basic 为过程提供对调用代码中的基础编程元素的直接引用。</span><span class="sxs-lookup"><span data-stu-id="01b4e-113">When you use this passing mechanism, Visual Basic gives the procedure a direct reference to the underlying programming element in the calling code.</span></span>  
  
## <a name="passing-mechanism-and-element-type"></a><span data-ttu-id="01b4e-114">传递机制和元素类型</span><span class="sxs-lookup"><span data-stu-id="01b4e-114">Passing Mechanism and Element Type</span></span>  

 <span data-ttu-id="01b4e-115">选择的传递机制与基础元素类型的分类不同。</span><span class="sxs-lookup"><span data-stu-id="01b4e-115">The choice of passing mechanism is not the same as the classification of the underlying element type.</span></span> <span data-ttu-id="01b4e-116">按值或按引用传递是指 Visual Basic 向过程代码提供的内容。</span><span class="sxs-lookup"><span data-stu-id="01b4e-116">Passing by value or by reference refers to what Visual Basic supplies to the procedure code.</span></span> <span data-ttu-id="01b4e-117">值类型或引用类型是指编程元素在内存中的存储方式。</span><span class="sxs-lookup"><span data-stu-id="01b4e-117">A value type or reference type refers to how a programming element is stored in memory.</span></span>  
  
 <span data-ttu-id="01b4e-118">不过，传递机制和元素类型是相互关联的。</span><span class="sxs-lookup"><span data-stu-id="01b4e-118">However, the passing mechanism and element type are interrelated.</span></span> <span data-ttu-id="01b4e-119">引用类型的值是指向内存中其他位置的数据的指针。</span><span class="sxs-lookup"><span data-stu-id="01b4e-119">The value of a reference type is a pointer to the data elsewhere in memory.</span></span> <span data-ttu-id="01b4e-120">这意味着，当你按值传递引用类型时，过程代码将具有指向基础元素数据的指针，即使它无法访问基础元素本身。</span><span class="sxs-lookup"><span data-stu-id="01b4e-120">This means that when you pass a reference type by value, the procedure code has a pointer to the underlying element's data, even though it cannot access the underlying element itself.</span></span> <span data-ttu-id="01b4e-121">例如，如果元素是一个数组变量，则过程代码不能访问变量本身，但它可以访问数组成员。</span><span class="sxs-lookup"><span data-stu-id="01b4e-121">For example, if the element is an array variable, the procedure code does not have access to the variable itself, but it can access the array members.</span></span>  
  
## <a name="ability-to-modify"></a><span data-ttu-id="01b4e-122">修改能力</span><span class="sxs-lookup"><span data-stu-id="01b4e-122">Ability to Modify</span></span>  

 <span data-ttu-id="01b4e-123">当你将不可更改元素作为参数传递时，此过程将永远不能在调用代码中修改它，无论该元素是通过还是传递的 `ByVal` `ByRef` 。</span><span class="sxs-lookup"><span data-stu-id="01b4e-123">When you pass a nonmodifiable element as an argument, the procedure can never modify it in the calling code, whether it is passed `ByVal` or `ByRef`.</span></span>  
  
 <span data-ttu-id="01b4e-124">对于可修改元素，下表总结了元素类型和传递机制之间的交互。</span><span class="sxs-lookup"><span data-stu-id="01b4e-124">For a modifiable element, the following table summarizes the interaction between the element type and the passing mechanism.</span></span>  
  
|<span data-ttu-id="01b4e-125">元素类型</span><span class="sxs-lookup"><span data-stu-id="01b4e-125">Element type</span></span>|<span data-ttu-id="01b4e-126">过来 `ByVal`</span><span class="sxs-lookup"><span data-stu-id="01b4e-126">Passed `ByVal`</span></span>|<span data-ttu-id="01b4e-127">过来 `ByRef`</span><span class="sxs-lookup"><span data-stu-id="01b4e-127">Passed `ByRef`</span></span>|  
|------------------|--------------------|--------------------|  
|<span data-ttu-id="01b4e-128">值类型 (仅包含一个值) </span><span class="sxs-lookup"><span data-stu-id="01b4e-128">Value type (contains only a value)</span></span>|<span data-ttu-id="01b4e-129">此过程无法更改变量或其任何成员。</span><span class="sxs-lookup"><span data-stu-id="01b4e-129">The procedure cannot change the variable or any of its members.</span></span>|<span data-ttu-id="01b4e-130">该过程可以更改变量及其成员。</span><span class="sxs-lookup"><span data-stu-id="01b4e-130">The procedure can change the variable and its members.</span></span>|  
|<span data-ttu-id="01b4e-131">引用类型 (包含指向类或结构实例的指针) </span><span class="sxs-lookup"><span data-stu-id="01b4e-131">Reference type (contains a pointer to a class or structure instance)</span></span>|<span data-ttu-id="01b4e-132">此过程无法更改变量，但可以更改它所指向的实例的成员。</span><span class="sxs-lookup"><span data-stu-id="01b4e-132">The procedure cannot change the variable but can change members of the instance to which it points.</span></span>|<span data-ttu-id="01b4e-133">该过程可以更改变量以及它所指向的实例的成员。</span><span class="sxs-lookup"><span data-stu-id="01b4e-133">The procedure can change the variable and members of the instance to which it points.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="01b4e-134">请参阅</span><span class="sxs-lookup"><span data-stu-id="01b4e-134">See also</span></span>

- [<span data-ttu-id="01b4e-135">过程</span><span class="sxs-lookup"><span data-stu-id="01b4e-135">Procedures</span></span>](./index.md)
- [<span data-ttu-id="01b4e-136">过程形参和实参</span><span class="sxs-lookup"><span data-stu-id="01b4e-136">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="01b4e-137">如何：将参数传递给过程</span><span class="sxs-lookup"><span data-stu-id="01b4e-137">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="01b4e-138">按值和按引用传递参数</span><span class="sxs-lookup"><span data-stu-id="01b4e-138">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="01b4e-139">可修改和不可修改参数之间的差异</span><span class="sxs-lookup"><span data-stu-id="01b4e-139">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [<span data-ttu-id="01b4e-140">如何：更改过程参数的值</span><span class="sxs-lookup"><span data-stu-id="01b4e-140">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)
- [<span data-ttu-id="01b4e-141">如何：防止过程参数的值被更改</span><span class="sxs-lookup"><span data-stu-id="01b4e-141">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="01b4e-142">如何：强制通过值传递参数</span><span class="sxs-lookup"><span data-stu-id="01b4e-142">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)
- [<span data-ttu-id="01b4e-143">按位置和按名称传递自变量</span><span class="sxs-lookup"><span data-stu-id="01b4e-143">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="01b4e-144">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="01b4e-144">Value Types and Reference Types</span></span>](../data-types/value-types-and-reference-types.md)
