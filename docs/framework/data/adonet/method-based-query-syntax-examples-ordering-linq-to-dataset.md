---
description: '了解详细信息： Method-Based 查询语法示例： LINQ to DataSet 排序 () '
title: 基于方法的查询语法示例：排序 (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8f9ce4fd-e84f-48c0-bb64-89e217236d3e
ms.openlocfilehash: d655ff52fe30a9af15245a4c9989062107bb6842
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99672655"
---
# <a name="method-based-query-syntax-examples-ordering-linq-to-dataset"></a><span data-ttu-id="0abb2-103">基于方法的查询语法示例：排序 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="0abb2-103">Method-Based Query Syntax Examples: Ordering (LINQ to DataSet)</span></span>

<span data-ttu-id="0abb2-104">本主题中的示例演示如何使用 <xref:System.Linq.Enumerable.OrderBy%2A>、<xref:System.Linq.Enumerable.Reverse%2A> 和 <xref:System.Linq.Enumerable.ThenBy%2A> 方法来查询 <xref:System.Data.DataSet> 并使用方法查询语法对结果排序。</span><span class="sxs-lookup"><span data-stu-id="0abb2-104">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.OrderBy%2A>,  <xref:System.Linq.Enumerable.Reverse%2A>, and <xref:System.Linq.Enumerable.ThenBy%2A> methods to query a <xref:System.Data.DataSet> and order the results using the method query syntax.</span></span>  
  
 <span data-ttu-id="0abb2-105">在 `FillDataSet` 这些示例中使用的方法是在将 [数据加载到数据集](loading-data-into-a-dataset.md)时指定的。</span><span class="sxs-lookup"><span data-stu-id="0abb2-105">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="0abb2-106">本主题中的示例使用 AdventureWorks 示例数据库中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 表。</span><span class="sxs-lookup"><span data-stu-id="0abb2-106">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="0abb2-107">本主题中的示例使用以下 `using` / `Imports` 语句：</span><span class="sxs-lookup"><span data-stu-id="0abb2-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="0abb2-108">有关详细信息，请参阅 [如何：在 Visual Studio 中创建 LINQ to DataSet 项目](how-to-create-a-linq-to-dataset-project-in-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="0abb2-108">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="orderby"></a><span data-ttu-id="0abb2-109">OrderBy</span><span class="sxs-lookup"><span data-stu-id="0abb2-109">OrderBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="0abb2-110">示例</span><span class="sxs-lookup"><span data-stu-id="0abb2-110">Example</span></span>  

 <span data-ttu-id="0abb2-111">此示例使用具有自定义比较器的 <xref:System.Linq.Enumerable.OrderBy%2A> 方法对姓氏执行不区分大小写的排序。</span><span class="sxs-lookup"><span data-stu-id="0abb2-111">This example uses the <xref:System.Linq.Enumerable.OrderBy%2A> method with a custom comparer to do a case-insensitive sort of last names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderByComparer_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbycomparer_mq)]
 [!code-vb[DP LINQ to DataSet Examples#OrderByComparer_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbycomparer_mq)]  
  
## <a name="reverse"></a><span data-ttu-id="0abb2-112">Reverse</span><span class="sxs-lookup"><span data-stu-id="0abb2-112">Reverse</span></span>  
  
### <a name="example"></a><span data-ttu-id="0abb2-113">示例</span><span class="sxs-lookup"><span data-stu-id="0abb2-113">Example</span></span>  

 <span data-ttu-id="0abb2-114">此示例使用 <xref:System.Linq.Enumerable.Reverse%2A> 方法创建 `OrderDate` 早于 2002 年 2 月 20 日的订单的列表。</span><span class="sxs-lookup"><span data-stu-id="0abb2-114">This example uses the <xref:System.Linq.Enumerable.Reverse%2A> method to create a list of orders where `OrderDate` is earlier than Feb 20, 2002.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#reverse)]
 [!code-vb[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#reverse)]  
  
## <a name="thenby"></a><span data-ttu-id="0abb2-115">ThenBy</span><span class="sxs-lookup"><span data-stu-id="0abb2-115">ThenBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="0abb2-116">示例</span><span class="sxs-lookup"><span data-stu-id="0abb2-116">Example</span></span>  

 <span data-ttu-id="0abb2-117">此示例使用具有自定义比较器的 <xref:System.Linq.Enumerable.OrderBy%2A> 和 <xref:System.Linq.Enumerable.ThenBy%2A> 方法对产品名称先按定价排序，然后执行不区分大小写的降序排序。</span><span class="sxs-lookup"><span data-stu-id="0abb2-117">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> and <xref:System.Linq.Enumerable.ThenBy%2A> methods with a custom comparer to first sort by list price, and then perform a case-insensitive descending sort of the product names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ThenByDescendingComparer_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#thenbydescendingcomparer_mq)]
 [!code-vb[DP LINQ to DataSet Examples#ThenByDescendingComparer_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#thenbydescendingcomparer_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="0abb2-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="0abb2-118">See also</span></span>

- [<span data-ttu-id="0abb2-119">将数据加载到数据集中</span><span class="sxs-lookup"><span data-stu-id="0abb2-119">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="0abb2-120">LINQ to DataSet 示例</span><span class="sxs-lookup"><span data-stu-id="0abb2-120">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="0abb2-121">标准查询运算符概述 (C#)</span><span class="sxs-lookup"><span data-stu-id="0abb2-121">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="0abb2-122">标准查询运算符概述 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0abb2-122">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
