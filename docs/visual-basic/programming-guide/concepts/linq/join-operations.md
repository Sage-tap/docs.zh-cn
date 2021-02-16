---
description: '了解详细信息：联接操作 (Visual Basic) '
title: 联接运算
ms.date: 07/20/2015
ms.assetid: 39ab4854-ac84-4738-9d0b-3cb79be84db4
ms.openlocfilehash: d5566de71bf96d2af86329929a5ab6ab34e6d154
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100426772"
---
# <a name="join-operations-visual-basic"></a><span data-ttu-id="78416-103">联接操作 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="78416-103">Join Operations (Visual Basic)</span></span>

<span data-ttu-id="78416-104">联接两个数据源就是将一个数据源中的对象与另一个数据源中具有相同公共属性的对象相关联。</span><span class="sxs-lookup"><span data-stu-id="78416-104">A *join* of two data sources is the association of objects in one data source with objects that share a common attribute in another data source.</span></span>  
  
 <span data-ttu-id="78416-105">当查询所面向的数据源相互之间具有无法直接领会的关系时，联接就成为一项重要的运算。</span><span class="sxs-lookup"><span data-stu-id="78416-105">Joining is an important operation in queries that target data sources whose relationships to each other cannot be followed directly.</span></span> <span data-ttu-id="78416-106">在面向对象的编程中，这可能意味着在未建模对象之间进行关联，例如对单向关系进行反向推理。</span><span class="sxs-lookup"><span data-stu-id="78416-106">In object-oriented programming, this could mean a correlation between objects that is not modeled, such as the backwards direction of a one-way relationship.</span></span> <span data-ttu-id="78416-107">下面是单向关系的一个示例：Customer 类有一个类型为 City 的属性，但 City 类没有作为 Customer 对象集合的属性。</span><span class="sxs-lookup"><span data-stu-id="78416-107">An example of a one-way relationship is a Customer class that has a property of type City, but the City class does not have a property that is a collection of Customer objects.</span></span> <span data-ttu-id="78416-108">如果你具有一个 City 对象列表，并且要查找每个城市中的所有客户，则可以使用联接运算完成此项查找。</span><span class="sxs-lookup"><span data-stu-id="78416-108">If you have a list of City objects and you want to find all the customers in each city, you could use a join operation to find them.</span></span>  
  
 <span data-ttu-id="78416-109">LINQ 框架中提供的 join 方法包括 <xref:System.Linq.Enumerable.Join%2A> 和 <xref:System.Linq.Enumerable.GroupJoin%2A>。</span><span class="sxs-lookup"><span data-stu-id="78416-109">The join methods provided in the LINQ framework are <xref:System.Linq.Enumerable.Join%2A> and <xref:System.Linq.Enumerable.GroupJoin%2A>.</span></span> <span data-ttu-id="78416-110">这些方法执行同等联接，即根据 2 个数据源的键是否相等来匹配这 2 个数据源的联接。</span><span class="sxs-lookup"><span data-stu-id="78416-110">These methods perform equijoins, or joins that match two data sources based on equality of their keys.</span></span> <span data-ttu-id="78416-111">（与此相较，Transact-SQL 支持除“等于”之外的联接运算符，例如“小于”运算符。）用关系数据库术语表达，就是说 <xref:System.Linq.Enumerable.Join%2A> 实现了内部联接，这种联接只返回那些在另一个数据集中具有匹配项的对象。</span><span class="sxs-lookup"><span data-stu-id="78416-111">(For comparison, Transact-SQL supports join operators other than 'equals', for example the 'less than' operator.) In relational database terms, <xref:System.Linq.Enumerable.Join%2A> implements an inner join, a type of join in which only those objects that have a match in the other data set are returned.</span></span> <span data-ttu-id="78416-112"><xref:System.Linq.Enumerable.GroupJoin%2A> 方法在关系数据库术语中没有直接等效项，但实现了内部联接和左外部联接的超集。</span><span class="sxs-lookup"><span data-stu-id="78416-112">The <xref:System.Linq.Enumerable.GroupJoin%2A> method has no direct equivalent in relational database terms, but it implements a superset of inner joins and left outer joins.</span></span> <span data-ttu-id="78416-113">左外部联接是指返回第一个（左侧）数据源的每个元素的联接，即使其他数据源中没有关联元素。</span><span class="sxs-lookup"><span data-stu-id="78416-113">A left outer join is a join that returns each element of the first (left) data source, even if it has no correlated elements in the other data source.</span></span>  
  
 <span data-ttu-id="78416-114">下图显示了一个概念性视图，其中包含两个集合以及这两个集合中的包含在内部联接或左外部联接中的元素。</span><span class="sxs-lookup"><span data-stu-id="78416-114">The following illustration shows a conceptual view of two sets and the elements within those sets that are included in either an inner join or a left outer join.</span></span>  
  
 ![显示内部/外部的两个重叠圆圈。](./media/join-operations/join-method-overlapping-circles.png)  
  
## <a name="methods"></a><span data-ttu-id="78416-116">方法</span><span class="sxs-lookup"><span data-stu-id="78416-116">Methods</span></span>  
  
|<span data-ttu-id="78416-117">方法名</span><span class="sxs-lookup"><span data-stu-id="78416-117">Method Name</span></span>|<span data-ttu-id="78416-118">描述</span><span class="sxs-lookup"><span data-stu-id="78416-118">Description</span></span>|<span data-ttu-id="78416-119">Visual Basic 查询表达式语法</span><span class="sxs-lookup"><span data-stu-id="78416-119">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="78416-120">更多信息</span><span class="sxs-lookup"><span data-stu-id="78416-120">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="78416-121">联接</span><span class="sxs-lookup"><span data-stu-id="78416-121">Join</span></span>|<span data-ttu-id="78416-122">根据键选择器函数联接两个序列并提取值对。</span><span class="sxs-lookup"><span data-stu-id="78416-122">Joins two sequences based on key selector functions and extracts pairs of values.</span></span>|`From x In …, y In … Where x.a = y.a`<br /><br /> <span data-ttu-id="78416-123">- 或 -</span><span class="sxs-lookup"><span data-stu-id="78416-123">-or-</span></span><br /><br /> `Join … [As …]In … On …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="78416-124">GroupJoin</span><span class="sxs-lookup"><span data-stu-id="78416-124">GroupJoin</span></span>|<span data-ttu-id="78416-125">根据键选择器函数联接两个序列，并对每个元素的结果匹配项进行分组。</span><span class="sxs-lookup"><span data-stu-id="78416-125">Joins two sequences based on key selector functions and groups the resulting matches for each element.</span></span>|`Group Join … In … On …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="78416-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="78416-126">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="78416-127">标准查询运算符概述 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="78416-127">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="78416-128">匿名类型</span><span class="sxs-lookup"><span data-stu-id="78416-128">Anonymous Types</span></span>](../../language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="78416-129">构建联接和跨产品查询</span><span class="sxs-lookup"><span data-stu-id="78416-129">Formulate Joins and Cross-Product Queries</span></span>](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)
- [<span data-ttu-id="78416-130">Join 子句</span><span class="sxs-lookup"><span data-stu-id="78416-130">Join Clause</span></span>](../../../language-reference/queries/join-clause.md)
- [<span data-ttu-id="78416-131">如何： (LINQ)  (Visual Basic 联接不同文件的内容) </span><span class="sxs-lookup"><span data-stu-id="78416-131">How to: Join Content from Dissimilar Files (LINQ) (Visual Basic)</span></span>](how-to-join-content-from-dissimilar-files-linq.md)
- [<span data-ttu-id="78416-132">如何：从多个源 (LINQ)  (Visual Basic 填充对象集合) </span><span class="sxs-lookup"><span data-stu-id="78416-132">How to: Populate Object Collections from Multiple Sources (LINQ) (Visual Basic)</span></span>](how-to-populate-object-collections-from-multiple-sources-linq.md)
