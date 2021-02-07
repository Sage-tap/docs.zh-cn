---
description: '了解详细信息：查询表达式语法示例：分区 (LINQ to DataSet) '
title: 查询表达式语法示例：分区 (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: beb5f361-1ac8-44fb-afa1-2aacea15f166
ms.openlocfilehash: 01ce41e2281632cf30692656c70c0610971aaa06
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681547"
---
# <a name="query-expression-syntax-examples-partitioning-linq-to-dataset"></a><span data-ttu-id="51e60-103">查询表达式语法示例：分区 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="51e60-103">Query Expression Syntax Examples: Partitioning (LINQ to DataSet)</span></span>

<span data-ttu-id="51e60-104">本主题中的示例演示如何使用 <xref:System.Linq.Enumerable.Skip%2A> 和 <xref:System.Linq.Enumerable.Take%2A> 方法以便使用查询表达式语法来查询 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="51e60-104">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="51e60-105">在 `FillDataSet` 这些示例中使用的方法是在将 [数据加载到数据集](loading-data-into-a-dataset.md)时指定的。</span><span class="sxs-lookup"><span data-stu-id="51e60-105">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="51e60-106">本主题中的示例使用 AdventureWorks 示例数据库中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 表。</span><span class="sxs-lookup"><span data-stu-id="51e60-106">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="51e60-107">本主题中的示例使用以下 `using` / `Imports` 语句：</span><span class="sxs-lookup"><span data-stu-id="51e60-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="51e60-108">有关详细信息，请参阅 [如何：在 Visual Studio 中创建 LINQ to DataSet 项目](how-to-create-a-linq-to-dataset-project-in-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="51e60-108">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="skip"></a><span data-ttu-id="51e60-109">跳过</span><span class="sxs-lookup"><span data-stu-id="51e60-109">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="51e60-110">示例</span><span class="sxs-lookup"><span data-stu-id="51e60-110">Example</span></span>  

 <span data-ttu-id="51e60-111">此示例使用 <xref:System.Linq.Enumerable.Skip%2A> 方法获取 Seattle 中除前两个地址以外的所有地址。</span><span class="sxs-lookup"><span data-stu-id="51e60-111">This example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP LINQ to DataSet Examples#SkipNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipnested)]  
  
## <a name="take"></a><span data-ttu-id="51e60-112">Take</span><span class="sxs-lookup"><span data-stu-id="51e60-112">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="51e60-113">示例</span><span class="sxs-lookup"><span data-stu-id="51e60-113">Example</span></span>  

 <span data-ttu-id="51e60-114">此示例使用 <xref:System.Linq.Enumerable.Take%2A> 方法获取 Seattle 中的前三个地址。</span><span class="sxs-lookup"><span data-stu-id="51e60-114">This example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takenested)]
 [!code-vb[DP LINQ to DataSet Examples#TakeNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takenested)]  
  
## <a name="see-also"></a><span data-ttu-id="51e60-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="51e60-115">See also</span></span>

- [<span data-ttu-id="51e60-116">将数据加载到数据集中</span><span class="sxs-lookup"><span data-stu-id="51e60-116">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="51e60-117">LINQ to DataSet 示例</span><span class="sxs-lookup"><span data-stu-id="51e60-117">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="51e60-118">标准查询运算符概述 (C#)</span><span class="sxs-lookup"><span data-stu-id="51e60-118">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="51e60-119">标准查询运算符概述 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="51e60-119">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
