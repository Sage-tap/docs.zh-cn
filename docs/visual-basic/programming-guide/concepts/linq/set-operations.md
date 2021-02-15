---
description: '了解详细信息：设置操作 (Visual Basic) '
title: Set 运算
ms.date: 07/20/2015
ms.assetid: 2b06e822-e030-438f-9db7-ee402bd3a706
ms.openlocfilehash: 9c75c9e029ba260917f59c7d2ea0341c157bf406
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100471664"
---
# <a name="set-operations-visual-basic"></a><span data-ttu-id="35b1c-103">设置操作 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="35b1c-103">Set Operations (Visual Basic)</span></span>

<span data-ttu-id="35b1c-104">LINQ 中的集运算是指根据相同或不同集合（或集）中是否存在等效元素来生成结果集的查询运算。</span><span class="sxs-lookup"><span data-stu-id="35b1c-104">Set operations in LINQ refer to query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate collections (or sets).</span></span>

<span data-ttu-id="35b1c-105">下节列出了执行集运算的标准查询运算符方法。</span><span class="sxs-lookup"><span data-stu-id="35b1c-105">The standard query operator methods that perform set operations are listed in the following section.</span></span>

## <a name="methods"></a><span data-ttu-id="35b1c-106">方法</span><span class="sxs-lookup"><span data-stu-id="35b1c-106">Methods</span></span>

|<span data-ttu-id="35b1c-107">方法名</span><span class="sxs-lookup"><span data-stu-id="35b1c-107">Method Name</span></span>|<span data-ttu-id="35b1c-108">描述</span><span class="sxs-lookup"><span data-stu-id="35b1c-108">Description</span></span>|<span data-ttu-id="35b1c-109">Visual Basic 查询表达式语法</span><span class="sxs-lookup"><span data-stu-id="35b1c-109">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="35b1c-110">更多信息</span><span class="sxs-lookup"><span data-stu-id="35b1c-110">More Information</span></span>|
|-----------------|-----------------|------------------------------------------|----------------------|
|<span data-ttu-id="35b1c-111">Distinct</span><span class="sxs-lookup"><span data-stu-id="35b1c-111">Distinct</span></span>|<span data-ttu-id="35b1c-112">删除集合中的重复值。</span><span class="sxs-lookup"><span data-stu-id="35b1c-112">Removes duplicate values from a collection.</span></span>|`Distinct`|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|
|<span data-ttu-id="35b1c-113">Except</span><span class="sxs-lookup"><span data-stu-id="35b1c-113">Except</span></span>|<span data-ttu-id="35b1c-114">返回差集，差集指位于一个集合但不位于另一个集合的元素。</span><span class="sxs-lookup"><span data-stu-id="35b1c-114">Returns the set difference, which means the elements of one collection that do not appear in a second collection.</span></span>|<span data-ttu-id="35b1c-115">不适用。</span><span class="sxs-lookup"><span data-stu-id="35b1c-115">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|
|<span data-ttu-id="35b1c-116">相交</span><span class="sxs-lookup"><span data-stu-id="35b1c-116">Intersect</span></span>|<span data-ttu-id="35b1c-117">返回交集，交集指同时出现在两个集合中的元素。</span><span class="sxs-lookup"><span data-stu-id="35b1c-117">Returns the set intersection, which means elements that appear in each of two collections.</span></span>|<span data-ttu-id="35b1c-118">不适用。</span><span class="sxs-lookup"><span data-stu-id="35b1c-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|
|<span data-ttu-id="35b1c-119">联合</span><span class="sxs-lookup"><span data-stu-id="35b1c-119">Union</span></span>|<span data-ttu-id="35b1c-120">返回并集，并集指位于两个集合中任一集合的唯一的元素。</span><span class="sxs-lookup"><span data-stu-id="35b1c-120">Returns the set union, which means unique elements that appear in either of two collections.</span></span>|<span data-ttu-id="35b1c-121">不适用。</span><span class="sxs-lookup"><span data-stu-id="35b1c-121">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|

## <a name="comparison-of-set-operations"></a><span data-ttu-id="35b1c-122">比较集运算</span><span class="sxs-lookup"><span data-stu-id="35b1c-122">Comparison of Set Operations</span></span>

### <a name="distinct"></a><span data-ttu-id="35b1c-123">Distinct</span><span class="sxs-lookup"><span data-stu-id="35b1c-123">Distinct</span></span>

<span data-ttu-id="35b1c-124">下图演示字符序列上 <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> 方法的行为。</span><span class="sxs-lookup"><span data-stu-id="35b1c-124">The following illustration depicts the behavior of the <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> method on a sequence of characters.</span></span> <span data-ttu-id="35b1c-125">返回的序列包含输入序列的唯一元素。</span><span class="sxs-lookup"><span data-stu-id="35b1c-125">The returned sequence contains the unique elements from the input sequence.</span></span>

![显示 Distinct() 的行为的图。](./media/set-operations/distinct-method-behavior.png)

### <a name="except"></a><span data-ttu-id="35b1c-127">Except</span><span class="sxs-lookup"><span data-stu-id="35b1c-127">Except</span></span>

<span data-ttu-id="35b1c-128">下图演示 <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType> 的行为。</span><span class="sxs-lookup"><span data-stu-id="35b1c-128">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="35b1c-129">返回的序列只包含位于第一个输入序列但不位于第二个输入序列的元素。</span><span class="sxs-lookup"><span data-stu-id="35b1c-129">The returned sequence contains only the elements from the first input sequence that are not in the second input sequence.</span></span>

<span data-ttu-id="35b1c-130">![显示 Except() 的操作的图](./media/set-operations/except-behavior-graphic.png "显示 Except 的行为。")</span><span class="sxs-lookup"><span data-stu-id="35b1c-130">![Graphic showing the action of Except&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Shows the behavior of Except.")</span></span>

### <a name="intersect"></a><span data-ttu-id="35b1c-131">相交</span><span class="sxs-lookup"><span data-stu-id="35b1c-131">Intersect</span></span>

<span data-ttu-id="35b1c-132">下图演示 <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType> 的行为。</span><span class="sxs-lookup"><span data-stu-id="35b1c-132">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="35b1c-133">返回的序列包含两个输入序列共有的元素。</span><span class="sxs-lookup"><span data-stu-id="35b1c-133">The returned sequence contains the elements that are common to both of the input sequences.</span></span>

![显示两个序列的交集的图。](./media/set-operations/intersection-two-sequences.png)

### <a name="union"></a><span data-ttu-id="35b1c-135">联合</span><span class="sxs-lookup"><span data-stu-id="35b1c-135">Union</span></span>

<span data-ttu-id="35b1c-136">下图演示对两个字符序列执行的联合操作。</span><span class="sxs-lookup"><span data-stu-id="35b1c-136">The following illustration depicts a union operation on two sequences of characters.</span></span> <span data-ttu-id="35b1c-137">返回的序列包含两个输入序列的唯一元素。</span><span class="sxs-lookup"><span data-stu-id="35b1c-137">The returned sequence contains the unique elements from both input sequences.</span></span>

![显示两个序列的并集的图。](./media/set-operations/union-operation-two-sequences.png)

## <a name="query-expression-syntax-example"></a><span data-ttu-id="35b1c-139">查询表达式语法示例</span><span class="sxs-lookup"><span data-stu-id="35b1c-139">Query Expression Syntax Example</span></span>

<span data-ttu-id="35b1c-140">下面的示例 `Distinct` 在 LINQ 查询中使用子句从整数列表返回唯一的数字。</span><span class="sxs-lookup"><span data-stu-id="35b1c-140">The following example uses the `Distinct` clause in a LINQ query to return the unique numbers from a list of integers.</span></span>

[!code-vb[CsLINQSetOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQSetOps/VB/setops.vb#1)]

## <a name="see-also"></a><span data-ttu-id="35b1c-141">请参阅</span><span class="sxs-lookup"><span data-stu-id="35b1c-141">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="35b1c-142">标准查询运算符概述 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="35b1c-142">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="35b1c-143">Distinct 子句</span><span class="sxs-lookup"><span data-stu-id="35b1c-143">Distinct Clause</span></span>](../../../language-reference/queries/distinct-clause.md)
- [<span data-ttu-id="35b1c-144">如何：合并和比较字符串集合 (LINQ)  (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="35b1c-144">How to: Combine and Compare String Collections (LINQ) (Visual Basic)</span></span>](how-to-combine-and-compare-string-collections-linq.md)
- [<span data-ttu-id="35b1c-145">如何：查找两个列表之间的差集 (LINQ)  (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="35b1c-145">How to: Find the Set Difference Between Two Lists (LINQ) (Visual Basic)</span></span>](how-to-find-the-set-difference-between-two-lists-linq.md)
