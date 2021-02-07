---
description: 了解详细信息：查询表达式语法示例：排序
title: 查询表达式语法示例：中间件排序
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: bcbc9625-7cf7-476e-85d2-058f12682f54
ms.openlocfilehash: 931225344311e8dde6318564ddeba6eae0e2411d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696095"
---
# <a name="query-expression-syntax-examples-ordering"></a><span data-ttu-id="46632-103">查询表达式语法示例：中间件排序</span><span class="sxs-lookup"><span data-stu-id="46632-103">Query Expression Syntax Examples: Ordering</span></span>

<span data-ttu-id="46632-104">本主题中的示例演示如何使用 `OrderBy` 和 `OrderByDescending` 方法通过使用查询表达式语法来查询 [AdventureWorks 销售模型](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) 。</span><span class="sxs-lookup"><span data-stu-id="46632-104">The examples in this topic demonstrate how to use the `OrderBy` and `OrderByDescending` methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using query expression syntax.</span></span> <span data-ttu-id="46632-105">这些示例中使用的 AdventureWorks 销售模型从 AdventureWorks 示例数据库中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 等表生成。</span><span class="sxs-lookup"><span data-stu-id="46632-105">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="46632-106">本主题中的示例使用以下 `using` / `Imports` 语句：</span><span class="sxs-lookup"><span data-stu-id="46632-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="orderby"></a><span data-ttu-id="46632-107">OrderBy</span><span class="sxs-lookup"><span data-stu-id="46632-107">OrderBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="46632-108">示例</span><span class="sxs-lookup"><span data-stu-id="46632-108">Example</span></span>  

 <span data-ttu-id="46632-109">以下示例使用 <xref:System.Linq.Enumerable.OrderBy%2A> 以返回按姓氏排序的联系人列表。</span><span class="sxs-lookup"><span data-stu-id="46632-109">The following example uses <xref:System.Linq.Enumerable.OrderBy%2A> to return a list of contacts ordered by last name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderBySimple1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbysimple1)]
 [!code-vb[DP L2E Examples#OrderBySimple1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbysimple1)]  
  
### <a name="example"></a><span data-ttu-id="46632-110">示例</span><span class="sxs-lookup"><span data-stu-id="46632-110">Example</span></span>  

 <span data-ttu-id="46632-111">以下示例使用 <xref:System.Linq.Enumerable.OrderBy%2A> 以按姓氏的长度对联系人列表排序。</span><span class="sxs-lookup"><span data-stu-id="46632-111">The following example uses <xref:System.Linq.Enumerable.OrderBy%2A> to sort a list of contacts by length of last name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderBySimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbysimple2)]
 [!code-vb[DP L2E Examples#OrderBySimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbysimple2)]  
  
## <a name="orderbydescending"></a><span data-ttu-id="46632-112">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="46632-112">OrderByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="46632-113">示例</span><span class="sxs-lookup"><span data-stu-id="46632-113">Example</span></span>  

 <span data-ttu-id="46632-114">以下示例使用 `orderby… descending`（等效于 `Order By … Descending` 方法，但在 Visual Basic 中为 <xref:System.Linq.Enumerable.OrderByDescending%2A>），以按照从高到低的顺序对价目表排序。</span><span class="sxs-lookup"><span data-stu-id="46632-114">The following example uses `orderby… descending` (`Order By … Descending` in Visual Basic), which is equivalent to the <xref:System.Linq.Enumerable.OrderByDescending%2A> method, to sort the price list from highest to lowest.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderByDescendingSimple1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbydescendingsimple1)]
 [!code-vb[DP L2E Examples#OrderByDescendingSimple1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbydescendingsimple1)]  
  
## <a name="thenby"></a><span data-ttu-id="46632-115">ThenBy</span><span class="sxs-lookup"><span data-stu-id="46632-115">ThenBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="46632-116">示例</span><span class="sxs-lookup"><span data-stu-id="46632-116">Example</span></span>  

 <span data-ttu-id="46632-117">以下示例使用 <xref:System.Linq.Queryable.OrderBy%2A> 和 <xref:System.Linq.Queryable.ThenBy%2A> 以返回先按姓氏后按名字排序的联系人列表。</span><span class="sxs-lookup"><span data-stu-id="46632-117">The following example uses <xref:System.Linq.Queryable.OrderBy%2A> and <xref:System.Linq.Queryable.ThenBy%2A> to return a list of contacts ordered by last name and then by first name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderByThenBy](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbythenby)]
 [!code-vb[DP L2E Examples#OrderByThenBy](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbythenby)]  
  
## <a name="thenbydescending"></a><span data-ttu-id="46632-118">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="46632-118">ThenByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="46632-119">示例</span><span class="sxs-lookup"><span data-stu-id="46632-119">Example</span></span>  

 <span data-ttu-id="46632-120">以下示例使用 `OrderBy… Descending`（等效于 <xref:System.Linq.Enumerable.ThenByDescending%2A> 方法），以先按名称后按标价（从高到低）对产品列表排序。</span><span class="sxs-lookup"><span data-stu-id="46632-120">The following example uses `OrderBy… Descending`, which is equivalent to the <xref:System.Linq.Enumerable.ThenByDescending%2A> method, to sort a list of products, first by name and then by list price from highest to lowest.</span></span>  
  
 [!code-csharp[DP L2E Examples#ThenByDescendingSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#thenbydescendingsimple)]
 [!code-vb[DP L2E Examples#ThenByDescendingSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#thenbydescendingsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="46632-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="46632-121">See also</span></span>

- [<span data-ttu-id="46632-122">LINQ to Entities 中的查询</span><span class="sxs-lookup"><span data-stu-id="46632-122">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
