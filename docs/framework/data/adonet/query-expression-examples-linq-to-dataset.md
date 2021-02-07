---
description: '了解详细信息：查询表达式示例 (LINQ to DataSet) '
title: 查询表达式示例 (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: f743fbc7-faff-45e5-af1e-61577d87f0cc
ms.openlocfilehash: 1d1571a851fae685942cbdbd557b275e86e8b0d2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99663685"
---
# <a name="query-expression-examples-linq-to-dataset"></a><span data-ttu-id="b9a69-103">查询表达式示例 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="b9a69-103">Query Expression Examples (LINQ to DataSet)</span></span>

<span data-ttu-id="b9a69-104">本节提供使用标准查询运算符的查询表达式语法中 LINQ to DataSet 的编程示例。</span><span class="sxs-lookup"><span data-stu-id="b9a69-104">This section provides LINQ to DataSet programming examples in query expression syntax that use the standard query operators.</span></span> <span data-ttu-id="b9a69-105"><xref:System.Data.DataSet>这些示例中使用的是使用方法填充的 `FillDataSet` ，该方法是在将[数据加载到数据集](loading-data-into-a-dataset.md)时指定的。</span><span class="sxs-lookup"><span data-stu-id="b9a69-105">The <xref:System.Data.DataSet> used in these examples is populated by using the `FillDataSet` method, which is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span> <span data-ttu-id="b9a69-106">有关详细信息，请参阅 [标准查询运算符概述 (c # ) ](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) 或 [标准查询运算符概述 (Visual Basic) ](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="b9a69-106">For more information, see [Standard Query Operators Overview (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) or [Standard Query Operators Overview (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b9a69-107">本节内容</span><span class="sxs-lookup"><span data-stu-id="b9a69-107">In This Section</span></span>  

 [<span data-ttu-id="b9a69-108">投影</span><span class="sxs-lookup"><span data-stu-id="b9a69-108">Projection</span></span>](query-expression-syntax-examples-projection-linq-to-dataset.md)  
 <span data-ttu-id="b9a69-109">本主题中的示例演示如何使用 <xref:System.Linq.Enumerable.Select%2A> 和 <xref:System.Linq.Enumerable.SelectMany%2A> 方法来查询 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="b9a69-109">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="b9a69-110">限制</span><span class="sxs-lookup"><span data-stu-id="b9a69-110">Restriction</span></span>](query-expression-syntax-examples-restriction-linq-to-dataset.md)  
 <span data-ttu-id="b9a69-111">本主题中的示例演示如何使用 <xref:System.Linq.Enumerable.Where%2A> 方法来查询 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="b9a69-111">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Where%2A> method to query a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="b9a69-112">分区</span><span class="sxs-lookup"><span data-stu-id="b9a69-112">Partitioning</span></span>](query-expression-syntax-examples-partitioning.md)  
 <span data-ttu-id="b9a69-113">本主题中的示例演示如何使用 <xref:System.Linq.Enumerable.Skip%2A> 和 <xref:System.Linq.Enumerable.Take%2A> 方法来查询 <xref:System.Data.DataSet> 并分隔结果。</span><span class="sxs-lookup"><span data-stu-id="b9a69-113">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods to query a <xref:System.Data.DataSet> and partition the results.</span></span>  
  
 [<span data-ttu-id="b9a69-114">中间件排序</span><span class="sxs-lookup"><span data-stu-id="b9a69-114">Ordering</span></span>](query-expression-syntax-examples-ordering-linq-to-dataset.md)  
 <span data-ttu-id="b9a69-115">本主题中的示例演示如何使用 <xref:System.Linq.Enumerable.OrderBy%2A>、<xref:System.Linq.Enumerable.OrderByDescending%2A>、<xref:System.Linq.Enumerable.Reverse%2A> 和 <xref:System.Linq.Enumerable.ThenByDescending%2A> 方法来查询 <xref:System.Data.DataSet> 并排序结果。</span><span class="sxs-lookup"><span data-stu-id="b9a69-115">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, and <xref:System.Linq.Enumerable.ThenByDescending%2A> methods to query a <xref:System.Data.DataSet> and order the results.</span></span>  
  
 [<span data-ttu-id="b9a69-116">元素运算符</span><span class="sxs-lookup"><span data-stu-id="b9a69-116">Element Operators</span></span>](query-expression-syntax-examples-element-operators.md)  
 <span data-ttu-id="b9a69-117">本主题中的示例演示如何使用 <xref:System.Linq.Enumerable.First%2A> 和 <xref:System.Linq.Enumerable.ElementAt%2A> 方法来获取 <xref:System.Data.DataRow> 中的 <xref:System.Data.DataSet> 元素。</span><span class="sxs-lookup"><span data-stu-id="b9a69-117">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> and <xref:System.Linq.Enumerable.ElementAt%2A> methods to get <xref:System.Data.DataRow> elements from a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="b9a69-118">聚合运算符</span><span class="sxs-lookup"><span data-stu-id="b9a69-118">Aggregate Operators</span></span>](query-expression-syntax-examples-aggregate-operators.md)  
 <span data-ttu-id="b9a69-119">本主题中的示例演示如何使用 <xref:System.Linq.Enumerable.Average%2A>、<xref:System.Linq.Enumerable.Count%2A>、<xref:System.Linq.Enumerable.Max%2A>、<xref:System.Linq.Enumerable.Min%2A> 和 <xref:System.Linq.Enumerable.Sum%2A> 方法来查询 <xref:System.Data.DataSet> 并聚合数据。</span><span class="sxs-lookup"><span data-stu-id="b9a69-119">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query a <xref:System.Data.DataSet> and aggregate data.</span></span>  
  
 [<span data-ttu-id="b9a69-120">联接运算符</span><span class="sxs-lookup"><span data-stu-id="b9a69-120">Join Operators</span></span>](query-expression-syntax-examples-join-operators.md)  
 <span data-ttu-id="b9a69-121">本主题中的示例演示如何使用 <xref:System.Linq.Enumerable.GroupJoin%2A> 和 <xref:System.Linq.Enumerable.Join%2A> 方法来查询 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="b9a69-121">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.GroupJoin%2A> and <xref:System.Linq.Enumerable.Join%2A> methods to query a <xref:System.Data.DataSet>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9a69-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="b9a69-122">See also</span></span>

- [<span data-ttu-id="b9a69-123">基于方法的查询示例</span><span class="sxs-lookup"><span data-stu-id="b9a69-123">Method-Based Query Examples</span></span>](method-based-query-examples-linq-to-dataset.md)
- [<span data-ttu-id="b9a69-124">数据集特定的运算符示例</span><span class="sxs-lookup"><span data-stu-id="b9a69-124">DataSet-Specific Operator Examples</span></span>](dataset-specific-operator-examples-linq-to-dataset.md)
- [<span data-ttu-id="b9a69-125">LINQ to DataSet 示例</span><span class="sxs-lookup"><span data-stu-id="b9a69-125">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
