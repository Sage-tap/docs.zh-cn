---
description: '了解详细信息： Method-Based 查询语法示例：转换运算符 (LINQ to DataSet) '
title: 基于方法的查询语法示例：转换运算符 (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a084c16b-9b55-4690-aefd-f8e0810a92c3
ms.openlocfilehash: 958e5c0ac1d1d8a98e6099ffcad055e78f07b23e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99672733"
---
# <a name="method-based-query-syntax-examples-conversion-operators-linq-to-dataset"></a><span data-ttu-id="712d4-103">基于方法的查询语法示例：转换运算符 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="712d4-103">Method-Based Query Syntax Examples: Conversion Operators (LINQ to DataSet)</span></span>

<span data-ttu-id="712d4-104">本主题中的示例演示如何使用 <xref:System.Linq.Enumerable.ToArray%2A>、<xref:System.Linq.Enumerable.ToDictionary%2A> 和 <xref:System.Linq.Enumerable.ToList%2A> 方法立即执行查询表达式。</span><span class="sxs-lookup"><span data-stu-id="712d4-104">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A>, and <xref:System.Linq.Enumerable.ToList%2A> methods to immediately execute a query expression.</span></span>  
  
 <span data-ttu-id="712d4-105">在 `FillDataSet` 这些示例中使用的方法是在将 [数据加载到数据集](loading-data-into-a-dataset.md)时指定的。</span><span class="sxs-lookup"><span data-stu-id="712d4-105">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="712d4-106">本主题中的示例使用 AdventureWorks 示例数据库中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 表。</span><span class="sxs-lookup"><span data-stu-id="712d4-106">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="712d4-107">本主题中的示例使用以下 `using` / `Imports` 语句：</span><span class="sxs-lookup"><span data-stu-id="712d4-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="712d4-108">有关详细信息，请参阅 [如何：在 Visual Studio 中创建 LINQ to DataSet 项目](how-to-create-a-linq-to-dataset-project-in-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="712d4-108">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="toarray"></a><span data-ttu-id="712d4-109">ToArray</span><span class="sxs-lookup"><span data-stu-id="712d4-109">ToArray</span></span>  
  
### <a name="example"></a><span data-ttu-id="712d4-110">示例</span><span class="sxs-lookup"><span data-stu-id="712d4-110">Example</span></span>  

 <span data-ttu-id="712d4-111">此示例使用 <xref:System.Linq.Enumerable.ToArray%2A> 方法立即将序列计算为数组。</span><span class="sxs-lookup"><span data-stu-id="712d4-111">This example uses the <xref:System.Linq.Enumerable.ToArray%2A> method to immediately evaluate a sequence into an array.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToArray](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#toarray)]
 [!code-vb[DP LINQ to DataSet Examples#ToArray](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#toarray)]  
  
## <a name="todictionary"></a><span data-ttu-id="712d4-112">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="712d4-112">ToDictionary</span></span>  
  
### <a name="example"></a><span data-ttu-id="712d4-113">示例</span><span class="sxs-lookup"><span data-stu-id="712d4-113">Example</span></span>  

 <span data-ttu-id="712d4-114">此示例使用 <xref:System.Linq.Enumerable.ToDictionary%2A> 方法立即将序列和相关键表达式计算为字典。</span><span class="sxs-lookup"><span data-stu-id="712d4-114">This example uses the <xref:System.Linq.Enumerable.ToDictionary%2A> method to immediately evaluate a sequence and a related key expression into a dictionary.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToDictionary](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#todictionary)]
 [!code-vb[DP LINQ to DataSet Examples#ToDictionary](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#todictionary)]  
  
## <a name="tolist"></a><span data-ttu-id="712d4-115">ToList</span><span class="sxs-lookup"><span data-stu-id="712d4-115">ToList</span></span>  
  
### <a name="example"></a><span data-ttu-id="712d4-116">示例</span><span class="sxs-lookup"><span data-stu-id="712d4-116">Example</span></span>  

 <span data-ttu-id="712d4-117">此示例使用 <xref:System.Linq.Enumerable.ToList%2A> 方法立即将序列计算为 <xref:System.Collections.Generic.List%601>，其中 `T` 的类型为 <xref:System.Data.DataRow>。</span><span class="sxs-lookup"><span data-stu-id="712d4-117">This example uses the <xref:System.Linq.Enumerable.ToList%2A> method to immediately evaluate a sequence into a <xref:System.Collections.Generic.List%601>, where `T` is of type <xref:System.Data.DataRow>.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToList](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#tolist)]
 [!code-vb[DP LINQ to DataSet Examples#ToList](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#tolist)]  
  
## <a name="see-also"></a><span data-ttu-id="712d4-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="712d4-118">See also</span></span>

- [<span data-ttu-id="712d4-119">将数据加载到数据集中</span><span class="sxs-lookup"><span data-stu-id="712d4-119">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="712d4-120">LINQ to DataSet 示例</span><span class="sxs-lookup"><span data-stu-id="712d4-120">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="712d4-121">标准查询运算符概述 (C#)</span><span class="sxs-lookup"><span data-stu-id="712d4-121">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="712d4-122">标准查询运算符概述 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="712d4-122">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
