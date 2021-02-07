---
description: '了解详细信息：迭代器 (Visual Basic) '
title: 迭代器
ms.date: 07/20/2015
f1_keywords:
- vb.Iterator
helpviewer_keywords:
- Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
ms.openlocfilehash: 7a3329ba23a3f2487343b332f3bb9c4b19c36496
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99730520"
---
# <a name="iterator-visual-basic"></a><span data-ttu-id="5576c-103">迭代器 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5576c-103">Iterator (Visual Basic)</span></span>

<span data-ttu-id="5576c-104">指定函数或 `Get` 访问器是迭代器。</span><span class="sxs-lookup"><span data-stu-id="5576c-104">Specifies that a function or `Get` accessor is an iterator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5576c-105">备注</span><span class="sxs-lookup"><span data-stu-id="5576c-105">Remarks</span></span>  

 <span data-ttu-id="5576c-106">*迭代器* 对集合执行自定义迭代。</span><span class="sxs-lookup"><span data-stu-id="5576c-106">An *iterator* performs a custom iteration over a collection.</span></span> <span data-ttu-id="5576c-107">迭代器使用 [Yield](../statements/yield-statement.md) 语句每次返回集合中的每个元素。</span><span class="sxs-lookup"><span data-stu-id="5576c-107">An iterator uses the [Yield](../statements/yield-statement.md) statement to return each element in the collection one at a time.</span></span> <span data-ttu-id="5576c-108">当 `Yield` 到达语句时，会保留代码中的当前位置。</span><span class="sxs-lookup"><span data-stu-id="5576c-108">When a `Yield` statement is reached, the current location in code is retained.</span></span> <span data-ttu-id="5576c-109">下次调用迭代器函数时，将从该位置重新开始执行。</span><span class="sxs-lookup"><span data-stu-id="5576c-109">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="5576c-110">迭代器可作为函数实现或作为 `Get` 属性定义的访问器。</span><span class="sxs-lookup"><span data-stu-id="5576c-110">An iterator can be implemented as a function or as a `Get` accessor of a property definition.</span></span> <span data-ttu-id="5576c-111">`Iterator`修饰符出现在迭代器函数或访问器的声明中 `Get` 。</span><span class="sxs-lookup"><span data-stu-id="5576c-111">The `Iterator` modifier appears in the declaration of the iterator function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="5576c-112">使用 For Each ... 将从客户端代码调用迭代器 [下一语句](../statements/for-each-next-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="5576c-112">You call an iterator from client code by using a [For Each...Next Statement](../statements/for-each-next-statement.md).</span></span>  
  
 <span data-ttu-id="5576c-113">迭代器函数或访问器的返回类型 `Get` 可以是 <xref:System.Collections.IEnumerable> 、 <xref:System.Collections.Generic.IEnumerable%601> 、 <xref:System.Collections.IEnumerator> 或 <xref:System.Collections.Generic.IEnumerator%601> 。</span><span class="sxs-lookup"><span data-stu-id="5576c-113">The return type of an iterator function or `Get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="5576c-114">迭代器不能具有任何 `ByRef` 参数。</span><span class="sxs-lookup"><span data-stu-id="5576c-114">An iterator cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="5576c-115">不能在事件、实例构造函数、静态构造函数或静态析构函数中使用迭代器。</span><span class="sxs-lookup"><span data-stu-id="5576c-115">An iterator cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="5576c-116">迭代器可以是匿名函数。</span><span class="sxs-lookup"><span data-stu-id="5576c-116">An iterator can be an anonymous function.</span></span> <span data-ttu-id="5576c-117">有关更多信息，请参见 [迭代器](../../programming-guide/concepts/iterators.md)。</span><span class="sxs-lookup"><span data-stu-id="5576c-117">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="usage"></a><span data-ttu-id="5576c-118">使用情况</span><span class="sxs-lookup"><span data-stu-id="5576c-118">Usage</span></span>  

 <span data-ttu-id="5576c-119">`Iterator` 修饰符可用于下面的上下文中：</span><span class="sxs-lookup"><span data-stu-id="5576c-119">The `Iterator` modifier can be used in these contexts:</span></span>  
  
- [<span data-ttu-id="5576c-120">Function 语句</span><span class="sxs-lookup"><span data-stu-id="5576c-120">Function Statement</span></span>](../statements/function-statement.md)  
  
- [<span data-ttu-id="5576c-121">Property Statement</span><span class="sxs-lookup"><span data-stu-id="5576c-121">Property Statement</span></span>](../statements/property-statement.md)  
  
## <a name="example"></a><span data-ttu-id="5576c-122">示例</span><span class="sxs-lookup"><span data-stu-id="5576c-122">Example</span></span>  

 <span data-ttu-id="5576c-123">下面的示例演示迭代器函数。</span><span class="sxs-lookup"><span data-stu-id="5576c-123">The following example demonstrates an iterator function.</span></span> <span data-ttu-id="5576c-124">迭代器函数具有 `Yield` 位于 [For .。。下一个](../statements/for-next-statement.md) 循环。</span><span class="sxs-lookup"><span data-stu-id="5576c-124">The iterator function has a `Yield` statement that is inside a [For…Next](../statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="5576c-125">中 [每](../statements/for-each-next-statement.md) 个语句体的每次迭代 `Main` 都会创建对 `Power` 迭代器函数的调用。</span><span class="sxs-lookup"><span data-stu-id="5576c-125">Each iteration of the [For Each](../statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="5576c-126">对迭代器函数的每个调用将继续到 `Yield` 语句的下一次执行（在 `For…Next` 循环的下一次迭代期间发生）。</span><span class="sxs-lookup"><span data-stu-id="5576c-126">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a><span data-ttu-id="5576c-127">示例</span><span class="sxs-lookup"><span data-stu-id="5576c-127">Example</span></span>  

 <span data-ttu-id="5576c-128">下面的示例演示一个作为迭代器的 `Get` 访问器。</span><span class="sxs-lookup"><span data-stu-id="5576c-128">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="5576c-129">`Iterator`修饰符在属性声明中。</span><span class="sxs-lookup"><span data-stu-id="5576c-129">The `Iterator` modifier is in the property declaration.</span></span>  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 <span data-ttu-id="5576c-130">有关其他示例，请参阅 [迭代](../../programming-guide/concepts/iterators.md)器。</span><span class="sxs-lookup"><span data-stu-id="5576c-130">For additional examples, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5576c-131">请参阅</span><span class="sxs-lookup"><span data-stu-id="5576c-131">See also</span></span>

- <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>
- [<span data-ttu-id="5576c-132">迭代器</span><span class="sxs-lookup"><span data-stu-id="5576c-132">Iterators</span></span>](../../programming-guide/concepts/iterators.md)
- [<span data-ttu-id="5576c-133">Yield 语句</span><span class="sxs-lookup"><span data-stu-id="5576c-133">Yield Statement</span></span>](../statements/yield-statement.md)
