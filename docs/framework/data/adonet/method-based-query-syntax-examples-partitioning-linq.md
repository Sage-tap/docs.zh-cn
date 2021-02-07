---
description: 了解详细信息： Method-Based 查询语法示例：分区 (LINQ
title: 基于方法的查询语法示例：分区 (LINQ)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a582c53f-f203-44ae-a797-d7f169a4fbb5
ms.openlocfilehash: 1e045fb4f0b627bdb5a926de2272bbaa59abdcee
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723772"
---
# <a name="method-based-query-syntax-examples-partitioning-linq"></a><span data-ttu-id="f10a3-103">基于方法的查询语法示例：分区 (LINQ)</span><span class="sxs-lookup"><span data-stu-id="f10a3-103">Method-Based Query Syntax Examples: Partitioning (LINQ</span></span>

<span data-ttu-id="f10a3-104">本主题中的示例演示如何使用 <xref:System.Linq.Enumerable.Skip%2A>、<xref:System.Linq.Enumerable.SkipWhile%2A>、<xref:System.Linq.Enumerable.Take%2A> 和 <xref:System.Linq.Enumerable.TakeWhile%2A> 方法以便使用查询表达式语法来查询 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="f10a3-104">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A>, <xref:System.Linq.Enumerable.Take%2A>, and <xref:System.Linq.Enumerable.TakeWhile%2A> methods to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="f10a3-105">在 `FillDataSet` 这些示例中使用的方法是在将 [数据加载到数据集](loading-data-into-a-dataset.md)时指定的。</span><span class="sxs-lookup"><span data-stu-id="f10a3-105">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="f10a3-106">本主题中的示例使用 AdventureWorks 示例数据库中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 表。</span><span class="sxs-lookup"><span data-stu-id="f10a3-106">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="f10a3-107">本主题中的示例使用以下 `using` / `Imports` 语句：</span><span class="sxs-lookup"><span data-stu-id="f10a3-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="f10a3-108">有关详细信息，请参阅 [如何：在 Visual Studio 中创建 LINQ to DataSet 项目](how-to-create-a-linq-to-dataset-project-in-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="f10a3-108">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="skip"></a><span data-ttu-id="f10a3-109">跳过</span><span class="sxs-lookup"><span data-stu-id="f10a3-109">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="f10a3-110">示例</span><span class="sxs-lookup"><span data-stu-id="f10a3-110">Example</span></span>  

 <span data-ttu-id="f10a3-111">此示例使用 <xref:System.Linq.Enumerable.Skip%2A> 方法获取 `Contact` 表中除前五个联系人以外的所有联系人。</span><span class="sxs-lookup"><span data-stu-id="f10a3-111">This example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first five contacts of the `Contact` table.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipsimple)]
 [!code-vb[DP LINQ to DataSet Examples#SkipSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipsimple)]  
  
### <a name="example"></a><span data-ttu-id="f10a3-112">示例</span><span class="sxs-lookup"><span data-stu-id="f10a3-112">Example</span></span>  

 <span data-ttu-id="f10a3-113">此示例使用 <xref:System.Linq.Enumerable.Skip%2A> 方法获取 Seattle 中除前两个地址以外的所有地址。</span><span class="sxs-lookup"><span data-stu-id="f10a3-113">This example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP LINQ to DataSet Examples#SkipNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipnested)]  
  
## <a name="skipwhile"></a><span data-ttu-id="f10a3-114">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="f10a3-114">SkipWhile</span></span>  
  
### <a name="example"></a><span data-ttu-id="f10a3-115">示例</span><span class="sxs-lookup"><span data-stu-id="f10a3-115">Example</span></span>  

 <span data-ttu-id="f10a3-116">此示例使用 <xref:System.Linq.Enumerable.OrderBy%2A> 和 <xref:System.Linq.Enumerable.SkipWhile%2A> 方法返回 `Product` 表中定价大于 300.00 的产品。</span><span class="sxs-lookup"><span data-stu-id="f10a3-116">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> and <xref:System.Linq.Enumerable.SkipWhile%2A> methods to return products from the `Product` table with a list price greater than 300.00.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipWhileSimple_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipwhilesimple_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SkipWhileSimple_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipwhilesimple_mq)]  
  
## <a name="take"></a><span data-ttu-id="f10a3-117">Take</span><span class="sxs-lookup"><span data-stu-id="f10a3-117">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="f10a3-118">示例</span><span class="sxs-lookup"><span data-stu-id="f10a3-118">Example</span></span>  

 <span data-ttu-id="f10a3-119">此示例使用 <xref:System.Linq.Enumerable.Take%2A> 方法只获取 `Contact` 表中的前五个联系人。</span><span class="sxs-lookup"><span data-stu-id="f10a3-119">This example uses the <xref:System.Linq.Enumerable.Take%2A> method to get only the first five contacts from the `Contact` table.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takesimple)]
 [!code-vb[DP LINQ to DataSet Examples#TakeSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takesimple)]  
  
### <a name="example"></a><span data-ttu-id="f10a3-120">示例</span><span class="sxs-lookup"><span data-stu-id="f10a3-120">Example</span></span>  

 <span data-ttu-id="f10a3-121">此示例使用 <xref:System.Linq.Enumerable.Take%2A> 方法获取 Seattle 中的前三个地址。</span><span class="sxs-lookup"><span data-stu-id="f10a3-121">This example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takenested)]
 [!code-vb[DP LINQ to DataSet Examples#TakeNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takenested)]  
  
## <a name="takewhile"></a><span data-ttu-id="f10a3-122">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="f10a3-122">TakeWhile</span></span>  
  
### <a name="example"></a><span data-ttu-id="f10a3-123">示例</span><span class="sxs-lookup"><span data-stu-id="f10a3-123">Example</span></span>  

 <span data-ttu-id="f10a3-124">此示例使用 <xref:System.Linq.Enumerable.OrderBy%2A> 和 <xref:System.Linq.Enumerable.TakeWhile%2A> 返回 `Product` 表中定价小于 300.00 的产品。</span><span class="sxs-lookup"><span data-stu-id="f10a3-124">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> and <xref:System.Linq.Enumerable.TakeWhile%2A> to return products from the `Product` table with a list price less than 300.00.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeWhileSimple_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takewhilesimple_mq)]
 [!code-vb[DP LINQ to DataSet Examples#TakeWhileSimple_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takewhilesimple_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="f10a3-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="f10a3-125">See also</span></span>

- [<span data-ttu-id="f10a3-126">将数据加载到数据集中</span><span class="sxs-lookup"><span data-stu-id="f10a3-126">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="f10a3-127">LINQ to DataSet 示例</span><span class="sxs-lookup"><span data-stu-id="f10a3-127">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="f10a3-128">标准查询运算符概述 (C#)</span><span class="sxs-lookup"><span data-stu-id="f10a3-128">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="f10a3-129">标准查询运算符概述 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f10a3-129">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
