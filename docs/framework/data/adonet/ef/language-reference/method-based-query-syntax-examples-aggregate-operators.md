---
description: 了解详细信息： Method-Based 查询语法示例：聚合运算符
title: 基于方法的查询语法示例：聚合运算符
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0e306067-5720-4782-9719-2286570a7e47
ms.openlocfilehash: 26398af95398905f2e28c603ef90a04a4a2c56bb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99673607"
---
# <a name="method-based-query-syntax-examples-aggregate-operators"></a><span data-ttu-id="8fe37-103">基于方法的查询语法示例：聚合运算符</span><span class="sxs-lookup"><span data-stu-id="8fe37-103">Method-Based Query Syntax Examples: Aggregate Operators</span></span>

<span data-ttu-id="8fe37-104">本主题中的示例演示如何使用 <xref:System.Linq.Enumerable.Aggregate%2A> 、 <xref:System.Linq.Enumerable.Average%2A> 、、、 <xref:System.Linq.Enumerable.Count%2A> 、 <xref:System.Linq.Enumerable.LongCount%2A> <xref:System.Linq.Enumerable.Max%2A> <xref:System.Linq.Enumerable.Min%2A> 和 <xref:System.Linq.Enumerable.Sum%2A> 方法，通过基于方法的查询语法来查询 [AdventureWorks 销售模型](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) 。</span><span class="sxs-lookup"><span data-stu-id="8fe37-104">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.LongCount%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using method-based query syntax.</span></span> <span data-ttu-id="8fe37-105">这些示例中使用的 AdventureWorks 销售模型从 AdventureWorks 示例数据库中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 等表生成。</span><span class="sxs-lookup"><span data-stu-id="8fe37-105">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="8fe37-106">本主题中的示例使用以下 `using` / `Imports` 语句：</span><span class="sxs-lookup"><span data-stu-id="8fe37-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="average"></a><span data-ttu-id="8fe37-107">平均值</span><span class="sxs-lookup"><span data-stu-id="8fe37-107">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="8fe37-108">示例</span><span class="sxs-lookup"><span data-stu-id="8fe37-108">Example</span></span>  

 <span data-ttu-id="8fe37-109">以下示例使用 <xref:System.Linq.Enumerable.Average%2A> 方法以查找产品的平均标价。</span><span class="sxs-lookup"><span data-stu-id="8fe37-109">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products.</span></span>  
  
 [!code-csharp[DP L2E Examples#Average_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average_mq)]
 [!code-vb[DP L2E Examples#Average_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average_mq)]  
  
### <a name="example"></a><span data-ttu-id="8fe37-110">示例</span><span class="sxs-lookup"><span data-stu-id="8fe37-110">Example</span></span>  

 <span data-ttu-id="8fe37-111">以下示例使用 <xref:System.Linq.Enumerable.Average%2A> 方法以查找每种样式的产品的平均标价。</span><span class="sxs-lookup"><span data-stu-id="8fe37-111">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="8fe37-112">示例</span><span class="sxs-lookup"><span data-stu-id="8fe37-112">Example</span></span>  

 <span data-ttu-id="8fe37-113">以下示例使用 <xref:System.Linq.Enumerable.Average%2A> 方法以查找平均应付款总计。</span><span class="sxs-lookup"><span data-stu-id="8fe37-113">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageprojection_mq)]
 [!code-vb[DP L2E Examples#AverageProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="8fe37-114">示例</span><span class="sxs-lookup"><span data-stu-id="8fe37-114">Example</span></span>  

 <span data-ttu-id="8fe37-115">以下示例使用 <xref:System.Linq.Enumerable.Average%2A> 方法以获取每个联系人 ID 的平均应付款总计。</span><span class="sxs-lookup"><span data-stu-id="8fe37-115">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="8fe37-116">示例</span><span class="sxs-lookup"><span data-stu-id="8fe37-116">Example</span></span>  

 <span data-ttu-id="8fe37-117">以下示例使用 <xref:System.Linq.Enumerable.Average%2A> 方法以针对每个联系人获取具有平均应付款总计的订单。</span><span class="sxs-lookup"><span data-stu-id="8fe37-117">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the orders with the average total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="8fe37-118">计数</span><span class="sxs-lookup"><span data-stu-id="8fe37-118">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="8fe37-119">示例</span><span class="sxs-lookup"><span data-stu-id="8fe37-119">Example</span></span>  

 <span data-ttu-id="8fe37-120">以下示例使用 <xref:System.Linq.Enumerable.Count%2A> 方法以返回 Product 表中的产品数量。</span><span class="sxs-lookup"><span data-stu-id="8fe37-120">The following example uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in the Product table.</span></span>  
  
 [!code-csharp[DP L2E Examples#Count](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#count)]
 [!code-vb[DP L2E Examples#Count](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#count)]  
  
### <a name="example"></a><span data-ttu-id="8fe37-121">示例</span><span class="sxs-lookup"><span data-stu-id="8fe37-121">Example</span></span>  

 <span data-ttu-id="8fe37-122">以下示例使用 <xref:System.Linq.Enumerable.Count%2A> 方法以返回联系人 ID 的列表和每个联系人 ID 所具有的订单数。</span><span class="sxs-lookup"><span data-stu-id="8fe37-122">The following example uses the <xref:System.Linq.Enumerable.Count%2A> method to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countnested)]
 [!code-vb[DP L2E Examples#CountNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="8fe37-123">示例</span><span class="sxs-lookup"><span data-stu-id="8fe37-123">Example</span></span>  

 <span data-ttu-id="8fe37-124">以下示例按颜色对产品进行分组，并使用 <xref:System.Linq.Enumerable.Count%2A> 方法以返回每个颜色组中的产品数量。</span><span class="sxs-lookup"><span data-stu-id="8fe37-124">The following example groups products by color and uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="longcount"></a><span data-ttu-id="8fe37-125">LongCount</span><span class="sxs-lookup"><span data-stu-id="8fe37-125">LongCount</span></span>  
  
### <a name="example"></a><span data-ttu-id="8fe37-126">示例</span><span class="sxs-lookup"><span data-stu-id="8fe37-126">Example</span></span>  

 <span data-ttu-id="8fe37-127">以下示例以长整型获取联系人计数。</span><span class="sxs-lookup"><span data-stu-id="8fe37-127">The following example gets the contact count as a long integer.</span></span>  
  
 [!code-csharp[DP L2E Examples#LongCountSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#longcountsimple)]
 [!code-vb[DP L2E Examples#LongCountSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#longcountsimple)]  
  
## <a name="max"></a><span data-ttu-id="8fe37-128">Max</span><span class="sxs-lookup"><span data-stu-id="8fe37-128">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="8fe37-129">示例</span><span class="sxs-lookup"><span data-stu-id="8fe37-129">Example</span></span>  

 <span data-ttu-id="8fe37-130">以下示例使用 <xref:System.Linq.Enumerable.Max%2A> 方法以获取最大应付款总计。</span><span class="sxs-lookup"><span data-stu-id="8fe37-130">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxprojection_mq)]
 [!code-vb[DP L2E Examples#MaxProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="8fe37-131">示例</span><span class="sxs-lookup"><span data-stu-id="8fe37-131">Example</span></span>  

 <span data-ttu-id="8fe37-132">以下示例使用 <xref:System.Linq.Enumerable.Max%2A> 方法以获取每个联系人 ID 的最大应付款总计。</span><span class="sxs-lookup"><span data-stu-id="8fe37-132">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="8fe37-133">示例</span><span class="sxs-lookup"><span data-stu-id="8fe37-133">Example</span></span>  

 <span data-ttu-id="8fe37-134">以下示例使用 <xref:System.Linq.Enumerable.Max%2A> 方法以针对每个联系人 ID 获取具有最大应付款总计的订单。</span><span class="sxs-lookup"><span data-stu-id="8fe37-134">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="8fe37-135">Min</span><span class="sxs-lookup"><span data-stu-id="8fe37-135">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="8fe37-136">示例</span><span class="sxs-lookup"><span data-stu-id="8fe37-136">Example</span></span>  

 <span data-ttu-id="8fe37-137">以下示例使用 <xref:System.Linq.Enumerable.Min%2A> 方法以获取最小应付款总计。</span><span class="sxs-lookup"><span data-stu-id="8fe37-137">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minprojection_mq)]
 [!code-vb[DP L2E Examples#MinProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="8fe37-138">示例</span><span class="sxs-lookup"><span data-stu-id="8fe37-138">Example</span></span>  

 <span data-ttu-id="8fe37-139">以下示例使用 <xref:System.Linq.Enumerable.Min%2A> 方法以获取每个联系人 ID 的最小应付款总计。</span><span class="sxs-lookup"><span data-stu-id="8fe37-139">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="8fe37-140">示例</span><span class="sxs-lookup"><span data-stu-id="8fe37-140">Example</span></span>  

 <span data-ttu-id="8fe37-141">以下示例使用 <xref:System.Linq.Enumerable.Min%2A> 方法以针对每个联系人获取具有最小应付款总计的订单。</span><span class="sxs-lookup"><span data-stu-id="8fe37-141">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="8fe37-142">Sum</span><span class="sxs-lookup"><span data-stu-id="8fe37-142">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="8fe37-143">示例</span><span class="sxs-lookup"><span data-stu-id="8fe37-143">Example</span></span>  

 <span data-ttu-id="8fe37-144">以下示例使用 <xref:System.Linq.Enumerable.Sum%2A> 方法以获取 SalesOrderDetail 表中订单数量的总数。</span><span class="sxs-lookup"><span data-stu-id="8fe37-144">The following example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total number of order quantities in the SalesOrderDetail table.</span></span>  
  
 [!code-csharp[DP L2E Examples#SumProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumprojection_mq)]
 [!code-vb[DP L2E Examples#SumProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="8fe37-145">示例</span><span class="sxs-lookup"><span data-stu-id="8fe37-145">Example</span></span>  

 <span data-ttu-id="8fe37-146">以下示例使用 <xref:System.Linq.Enumerable.Sum%2A> 方法以获取每个联系人 ID 的应付款总计。</span><span class="sxs-lookup"><span data-stu-id="8fe37-146">The following example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="8fe37-147">请参阅</span><span class="sxs-lookup"><span data-stu-id="8fe37-147">See also</span></span>

- [<span data-ttu-id="8fe37-148">LINQ to Entities 中的查询</span><span class="sxs-lookup"><span data-stu-id="8fe37-148">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
