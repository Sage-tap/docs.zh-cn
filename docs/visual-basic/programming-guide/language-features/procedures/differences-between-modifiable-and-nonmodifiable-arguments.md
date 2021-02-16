---
description: '了解详细信息：可修改和不可修改参数之间的差异 (Visual Basic) '
title: 可修改和不可修改参数之间的差异
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedure arguments
- arguments [Visual Basic], nonmodifiable
- Visual Basic code, procedures
- arguments [Visual Basic], modifiable
ms.assetid: 87b2df69-e1f7-4657-9caf-b3f48d693428
ms.openlocfilehash: 8d83802b4b8830a17412fdef44eabd2e5b8a7f2d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100472626"
---
# <a name="differences-between-modifiable-and-nonmodifiable-arguments-visual-basic"></a><span data-ttu-id="cf046-103">可修改和不可修改自变量之间的差异 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cf046-103">Differences Between Modifiable and Nonmodifiable Arguments (Visual Basic)</span></span>

<span data-ttu-id="cf046-104">调用过程时，通常会向其传递一个或多个参数。</span><span class="sxs-lookup"><span data-stu-id="cf046-104">When you call a procedure, you typically pass one or more arguments to it.</span></span> <span data-ttu-id="cf046-105">每个参数都对应于一个基础编程元素。</span><span class="sxs-lookup"><span data-stu-id="cf046-105">Each argument corresponds to an underlying programming element.</span></span> <span data-ttu-id="cf046-106">基础元素和参数本身可以是可修改的，也可以是不可更改的。</span><span class="sxs-lookup"><span data-stu-id="cf046-106">Both the underlying elements and the arguments themselves can be either modifiable or nonmodifiable.</span></span>  
  
## <a name="modifiable-and-nonmodifiable-elements"></a><span data-ttu-id="cf046-107">可修改和不可更改元素</span><span class="sxs-lookup"><span data-stu-id="cf046-107">Modifiable and Nonmodifiable Elements</span></span>  

 <span data-ttu-id="cf046-108">编程元素可以是可修改的 *元素*（其值已更改）或 *不可更改元素*（在创建后具有固定值）。</span><span class="sxs-lookup"><span data-stu-id="cf046-108">A programming element can be either a *modifiable element*, which can have its value changed, or a *nonmodifiable element*, which has a fixed value once it has been created.</span></span>  
  
 <span data-ttu-id="cf046-109">下表列出了可修改和不可更改的编程元素。</span><span class="sxs-lookup"><span data-stu-id="cf046-109">The following table lists modifiable and nonmodifiable programming elements.</span></span>  
  
|<span data-ttu-id="cf046-110">可修改元素</span><span class="sxs-lookup"><span data-stu-id="cf046-110">Modifiable elements</span></span>|<span data-ttu-id="cf046-111">不可更改元素</span><span class="sxs-lookup"><span data-stu-id="cf046-111">Nonmodifiable elements</span></span>|  
|-------------------------|----------------------------|  
|<span data-ttu-id="cf046-112"> (在过程) 中声明的局部变量，包括对象变量（只读除外）</span><span class="sxs-lookup"><span data-stu-id="cf046-112">Local variables (declared inside procedures), including object variables, except for read-only</span></span>|<span data-ttu-id="cf046-113">只读变量、字段和属性</span><span class="sxs-lookup"><span data-stu-id="cf046-113">Read-only variables, fields, and properties</span></span>|  
|<span data-ttu-id="cf046-114">字段 (模块、类和结构的成员变量) ，只读除外</span><span class="sxs-lookup"><span data-stu-id="cf046-114">Fields (member variables of modules, classes, and structures), except for read-only</span></span>|<span data-ttu-id="cf046-115">常量和文本</span><span class="sxs-lookup"><span data-stu-id="cf046-115">Constants and literals</span></span>|  
|<span data-ttu-id="cf046-116">属性（只读除外）</span><span class="sxs-lookup"><span data-stu-id="cf046-116">Properties, except for read-only</span></span>|<span data-ttu-id="cf046-117">枚举成员</span><span class="sxs-lookup"><span data-stu-id="cf046-117">Enumeration members</span></span>|  
|<span data-ttu-id="cf046-118">数组元素</span><span class="sxs-lookup"><span data-stu-id="cf046-118">Array elements</span></span>|<span data-ttu-id="cf046-119">即使表达式的元素可修改，表达式 () </span><span class="sxs-lookup"><span data-stu-id="cf046-119">Expressions (even if their elements are modifiable)</span></span>|  
  
## <a name="modifiable-and-nonmodifiable-arguments"></a><span data-ttu-id="cf046-120">可修改和不可修改参数</span><span class="sxs-lookup"><span data-stu-id="cf046-120">Modifiable and Nonmodifiable Arguments</span></span>  

 <span data-ttu-id="cf046-121">可 *修改的自变量* 是具有可修改基础元素的自变量。</span><span class="sxs-lookup"><span data-stu-id="cf046-121">A *modifiable argument* is one with a modifiable underlying element.</span></span> <span data-ttu-id="cf046-122">调用代码随时可以存储新值，并且如果传递参数 [ByRef](../../../language-reference/modifiers/byref.md)，则过程中的代码还可以修改调用代码中的基础元素。</span><span class="sxs-lookup"><span data-stu-id="cf046-122">The calling code can store a new value at any time, and if you pass the argument [ByRef](../../../language-reference/modifiers/byref.md), the code in the procedure can also modify the underlying element in the calling code.</span></span>  
  
 <span data-ttu-id="cf046-123">*不可更改的参数* 具有不可更改的基础元素，或被传递了 [ByVal](../../../language-reference/modifiers/byval.md)。</span><span class="sxs-lookup"><span data-stu-id="cf046-123">A *nonmodifiable argument* either has a nonmodifiable underlying element or is passed [ByVal](../../../language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="cf046-124">过程不能修改调用代码中的基础元素，即使它是可修改的元素。</span><span class="sxs-lookup"><span data-stu-id="cf046-124">The procedure cannot modify the underlying element in the calling code, even if it is a modifiable element.</span></span> <span data-ttu-id="cf046-125">如果它是不可更改的元素，则调用代码本身无法修改它。</span><span class="sxs-lookup"><span data-stu-id="cf046-125">If it is a nonmodifiable element, the calling code itself cannot modify it.</span></span>  
  
 <span data-ttu-id="cf046-126">被调用的过程可能会修改其不可更改参数的本地副本，但该修改不会影响调用代码中的基础元素。</span><span class="sxs-lookup"><span data-stu-id="cf046-126">The called procedure might modify its local copy of a nonmodifiable argument, but that modification does not affect the underlying element in the calling code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf046-127">请参阅</span><span class="sxs-lookup"><span data-stu-id="cf046-127">See also</span></span>

- [<span data-ttu-id="cf046-128">过程</span><span class="sxs-lookup"><span data-stu-id="cf046-128">Procedures</span></span>](./index.md)
- [<span data-ttu-id="cf046-129">过程形参和实参</span><span class="sxs-lookup"><span data-stu-id="cf046-129">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="cf046-130">如何：将参数传递给过程</span><span class="sxs-lookup"><span data-stu-id="cf046-130">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="cf046-131">按值和按引用传递参数</span><span class="sxs-lookup"><span data-stu-id="cf046-131">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="cf046-132">通过值传递参数和通过引用传递参数之间的差异</span><span class="sxs-lookup"><span data-stu-id="cf046-132">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="cf046-133">如何：更改过程参数的值</span><span class="sxs-lookup"><span data-stu-id="cf046-133">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)
- [<span data-ttu-id="cf046-134">如何：防止过程参数的值被更改</span><span class="sxs-lookup"><span data-stu-id="cf046-134">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="cf046-135">如何：强制通过值传递参数</span><span class="sxs-lookup"><span data-stu-id="cf046-135">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)
- [<span data-ttu-id="cf046-136">按位置和按名称传递自变量</span><span class="sxs-lookup"><span data-stu-id="cf046-136">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="cf046-137">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="cf046-137">Value Types and Reference Types</span></span>](../data-types/value-types-and-reference-types.md)
