---
description: '了解详细信息： Method-Based 查询语法示例：元素运算符 (LINQ to DataSet) '
title: 基于方法的查询语法示例：元素运算符 (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eedf2fbd-f407-4f62-bb1a-c00eb001b1dd
ms.openlocfilehash: b6e9832832198927f7913b0f93b1347ae353461b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99672720"
---
# <a name="method-based-query-syntax-examples-element-operators-linq-to-dataset"></a><span data-ttu-id="e85a8-103">基于方法的查询语法示例：元素运算符 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="e85a8-103">Method-Based Query Syntax Examples: Element Operators (LINQ to DataSet)</span></span>

<span data-ttu-id="e85a8-104">本主题中的示例演示如何使用 <xref:System.Linq.Enumerable.First%2A> 和 <xref:System.Linq.Enumerable.ElementAt%2A> 方法以便使用查询表达式语法从 <xref:System.Data.DataRow> 中获取 <xref:System.Data.DataSet> 元素。</span><span class="sxs-lookup"><span data-stu-id="e85a8-104">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> and <xref:System.Linq.Enumerable.ElementAt%2A> methods to get <xref:System.Data.DataRow> elements from a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="e85a8-105">在 `FillDataSet` 这些示例中使用的方法是在将 [数据加载到数据集](loading-data-into-a-dataset.md)时指定的。</span><span class="sxs-lookup"><span data-stu-id="e85a8-105">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="e85a8-106">本主题中的示例使用 AdventureWorks 示例数据库中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 表。</span><span class="sxs-lookup"><span data-stu-id="e85a8-106">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="e85a8-107">本主题中的示例使用以下 `using` / `Imports` 语句：</span><span class="sxs-lookup"><span data-stu-id="e85a8-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
[!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
[!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]

 <span data-ttu-id="e85a8-108">有关详细信息，请参阅 [如何：在 Visual Studio 中创建 LINQ to DataSet 项目](how-to-create-a-linq-to-dataset-project-in-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="e85a8-108">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="elementat"></a><span data-ttu-id="e85a8-109">ElementAt</span><span class="sxs-lookup"><span data-stu-id="e85a8-109">ElementAt</span></span>  
  
### <a name="example"></a><span data-ttu-id="e85a8-110">示例</span><span class="sxs-lookup"><span data-stu-id="e85a8-110">Example</span></span>  

 <span data-ttu-id="e85a8-111">此示例使用 <xref:System.Linq.Enumerable.ElementAt%2A> 方法检索 `PostalCode` == "M4B 1V7" 的第五个地址。</span><span class="sxs-lookup"><span data-stu-id="e85a8-111">This example uses the <xref:System.Linq.Enumerable.ElementAt%2A> method to retrieve the fifth address where `PostalCode` == "M4B 1V7".</span></span>  
  
[!code-csharp[DP LINQ to DataSet Examples#ElementAt](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#elementat)]
[!code-vb[DP LINQ to DataSet Examples#ElementAt](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#elementat)]
  
## <a name="first"></a><span data-ttu-id="e85a8-112">First</span><span class="sxs-lookup"><span data-stu-id="e85a8-112">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="e85a8-113">示例</span><span class="sxs-lookup"><span data-stu-id="e85a8-113">Example</span></span>  

 <span data-ttu-id="e85a8-114">此示例使用 <xref:System.Linq.Enumerable.First%2A> 方法返回名字为“Brooke”的第一个联系人。</span><span class="sxs-lookup"><span data-stu-id="e85a8-114">This example uses the <xref:System.Linq.Enumerable.First%2A> method to return the first contact whose first name is 'Brooke'.</span></span>  
  
[!code-csharp[DP LINQ to DataSet Examples#FirstSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#firstsimple)]
[!code-vb[DP LINQ to DataSet Examples#FirstSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#firstsimple)]
  
## <a name="see-also"></a><span data-ttu-id="e85a8-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="e85a8-115">See also</span></span>

- [<span data-ttu-id="e85a8-116">将数据加载到数据集中</span><span class="sxs-lookup"><span data-stu-id="e85a8-116">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="e85a8-117">LINQ to DataSet 示例</span><span class="sxs-lookup"><span data-stu-id="e85a8-117">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="e85a8-118">标准查询运算符概述 (C#)</span><span class="sxs-lookup"><span data-stu-id="e85a8-118">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="e85a8-119">标准查询运算符概述 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e85a8-119">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
