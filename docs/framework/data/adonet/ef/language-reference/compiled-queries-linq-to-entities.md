---
description: '了解详细信息： LINQ to Entities (的编译查询) '
title: 编译的查询 (LINQ to Entities)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8025ba1d-29c7-4407-841b-d5a3bed40b7a
ms.openlocfilehash: bed14f21b6f2b46bfa229dbca0aa7c31d9763af3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696914"
---
# <a name="compiled-queries--linq-to-entities"></a><span data-ttu-id="0b5f7-103">已编译查询 (LINQ to Entities) </span><span class="sxs-lookup"><span data-stu-id="0b5f7-103">Compiled queries  (LINQ to Entities)</span></span>

<span data-ttu-id="0b5f7-104">如果应用程序需要在实体框架中多次执行结构类似的查询，通常可以通过仅编译查询一次并在每次执行时使用不同参数的方法来提高性能。</span><span class="sxs-lookup"><span data-stu-id="0b5f7-104">When you have an application that executes structurally similar queries many times in the Entity Framework, you can frequently increase performance by compiling the query one time and executing it several times with different parameters.</span></span> <span data-ttu-id="0b5f7-105">例如，某应用程序要检索特定城市的所有客户，而该城市是运行时由用户在窗体中指定的。</span><span class="sxs-lookup"><span data-stu-id="0b5f7-105">For example, an application might have to retrieve all the customers in a particular city; the city is specified at runtime by the user in a form.</span></span> <span data-ttu-id="0b5f7-106">LINQ to Entities 支持将已编译的查询用于此目的。</span><span class="sxs-lookup"><span data-stu-id="0b5f7-106">LINQ to Entities supports using compiled queries for this purpose.</span></span>  
  
 <span data-ttu-id="0b5f7-107">从 .NET Framework 4.5 开始，将自动缓存 LINQ 查询。</span><span class="sxs-lookup"><span data-stu-id="0b5f7-107">Starting with .NET Framework 4.5, LINQ queries are cached automatically.</span></span> <span data-ttu-id="0b5f7-108">但是，您仍可以使用已编译的 LINQ 查询来降低后续执行中的这一开销，编译的查询比自动缓存的 LINQ 查询效率更高。</span><span class="sxs-lookup"><span data-stu-id="0b5f7-108">However, you can still use compiled LINQ queries to reduce this cost in later executions and compiled queries can be more efficient than LINQ queries that are automatically cached.</span></span> <span data-ttu-id="0b5f7-109">`Enumerable.Contains`不自动缓存将运算符应用于内存中集合的 LINQ to Entities 查询。</span><span class="sxs-lookup"><span data-stu-id="0b5f7-109">LINQ to Entities queries that apply the `Enumerable.Contains` operator to in-memory collections are not automatically cached.</span></span> <span data-ttu-id="0b5f7-110">此外，不允许在已编译的 LINQ 查询中参数化内存中集合。</span><span class="sxs-lookup"><span data-stu-id="0b5f7-110">Also, parameterizing in-memory collections in compiled LINQ queries is not allowed.</span></span>  
  
 <span data-ttu-id="0b5f7-111"><xref:System.Data.Objects.CompiledQuery> 类提供查询的编译和缓存以供重复使用。</span><span class="sxs-lookup"><span data-stu-id="0b5f7-111">The <xref:System.Data.Objects.CompiledQuery> class provides compilation and caching of queries for reuse.</span></span> <span data-ttu-id="0b5f7-112">从概念上讲，此类包含 <xref:System.Data.Objects.CompiledQuery> 的 `Compile` 方法以及若干重载。</span><span class="sxs-lookup"><span data-stu-id="0b5f7-112">Conceptually, this class contains a <xref:System.Data.Objects.CompiledQuery>'s `Compile` method with several overloads.</span></span> <span data-ttu-id="0b5f7-113">调用 `Compile` 方法可以创建新的委托来表示已编译的查询。</span><span class="sxs-lookup"><span data-stu-id="0b5f7-113">Call the `Compile` method to create a new delegate to represent the compiled query.</span></span> <span data-ttu-id="0b5f7-114">给定 `Compile` 及其参数值，<xref:System.Data.Objects.ObjectContext> 方法将返回生成某个结果的委托（例如 <xref:System.Linq.IQueryable%601> 实例）。</span><span class="sxs-lookup"><span data-stu-id="0b5f7-114">The `Compile` methods, provided with a <xref:System.Data.Objects.ObjectContext> and parameter values, return a delegate that produces some result (such as an <xref:System.Linq.IQueryable%601> instance).</span></span> <span data-ttu-id="0b5f7-115">只在第一次执行的过程中查询才编译一次。</span><span class="sxs-lookup"><span data-stu-id="0b5f7-115">The query compiles once during only the first execution.</span></span> <span data-ttu-id="0b5f7-116">编译时为查询设置的合并选项在以后无法更改。</span><span class="sxs-lookup"><span data-stu-id="0b5f7-116">The merge options set for the query at the time of the compilation cannot be changed later.</span></span> <span data-ttu-id="0b5f7-117">编译查询后，只能提供基元类型的参数，但不能替换将更改生成的 SQL 的查询部分。</span><span class="sxs-lookup"><span data-stu-id="0b5f7-117">Once the query is compiled, you can only supply parameters of primitive type but you cannot replace parts of the query that would change the generated SQL.</span></span> <span data-ttu-id="0b5f7-118">有关详细信息，请参阅 [EF 合并选项和已编译的查询](/archive/blogs/dsimmons/ef-merge-options-and-compiled-queries)。</span><span class="sxs-lookup"><span data-stu-id="0b5f7-118">For more information, see [EF Merge Options and Compiled Queries](/archive/blogs/dsimmons/ef-merge-options-and-compiled-queries).</span></span>
  
 <span data-ttu-id="0b5f7-119">用于编译的方法的 LINQ to Entities 查询表达式由 <xref:System.Data.Objects.CompiledQuery> `Compile` 一个泛型委托（如）表示 `Func` <xref:System.Func%605> 。</span><span class="sxs-lookup"><span data-stu-id="0b5f7-119">The LINQ to Entities query expression that the <xref:System.Data.Objects.CompiledQuery>'s `Compile` method compiles is represented by one of the generic `Func` delegates, such as <xref:System.Func%605>.</span></span> <span data-ttu-id="0b5f7-120">查询表达式最多可以包装一个 `ObjectContext` 参数、一个返回参数和 16 个查询参数。</span><span class="sxs-lookup"><span data-stu-id="0b5f7-120">At most, the query expression can encapsulate an `ObjectContext` parameter, a return parameter, and 16 query parameters.</span></span> <span data-ttu-id="0b5f7-121">如果需要的查询参数不止 16 个，则可以创建一个结构并用其属性表示查询参数。</span><span class="sxs-lookup"><span data-stu-id="0b5f7-121">If more than 16 query parameters are required, you can create a structure whose properties represent query parameters.</span></span> <span data-ttu-id="0b5f7-122">然后，该结构上的这些属性在经过设置之后就可以用于查询表达式中。</span><span class="sxs-lookup"><span data-stu-id="0b5f7-122">You can then use the properties on the structure in the query expression after you set the properties.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="0b5f7-123">示例 1</span><span class="sxs-lookup"><span data-stu-id="0b5f7-123">Example 1</span></span>  

 <span data-ttu-id="0b5f7-124">下面的示例将编译并调用一个查询，该查询接受 <xref:System.Decimal> 输入参数，并返回一个应付款总额大于或等于 200.00 美元的订单序列：</span><span class="sxs-lookup"><span data-stu-id="0b5f7-124">The following example compiles and then invokes a query that accepts a <xref:System.Decimal> input parameter and returns a sequence of orders where the total due is greater than or equal to $200.00:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples - compiled query 2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery2)]
 [!code-vb[DP L2E Conceptual Examples - compiled query2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery2)]  
  
## <a name="example-2"></a><span data-ttu-id="0b5f7-125">示例 2</span><span class="sxs-lookup"><span data-stu-id="0b5f7-125">Example 2</span></span>  

 <span data-ttu-id="0b5f7-126">下面的示例将编译并调用一个返回 <xref:System.Data.Objects.ObjectQuery%601> 实例的查询：</span><span class="sxs-lookup"><span data-stu-id="0b5f7-126">The following example compiles and then invokes a query that returns an <xref:System.Data.Objects.ObjectQuery%601> instance:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples - compiled query1_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery1_mq)]
 [!code-vb[DP L2E Conceptual Examples - compiled query1_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery1_mq)]  
  
## <a name="example-3"></a><span data-ttu-id="0b5f7-127">示例 3</span><span class="sxs-lookup"><span data-stu-id="0b5f7-127">Example 3</span></span>  

 <span data-ttu-id="0b5f7-128">下面的示例将编译并调用一个返回 <xref:System.Decimal> 形式产品标价平均值的查询：</span><span class="sxs-lookup"><span data-stu-id="0b5f7-128">The following example compiles and then invokes a query that returns the average of the product list prices as a <xref:System.Decimal> value:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples - compiled query3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery3_mq)]
 [!code-vb[DP L2E Conceptual Examples - compiled query3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery3_mq)]  
  
## <a name="example-4"></a><span data-ttu-id="0b5f7-129">示例 4</span><span class="sxs-lookup"><span data-stu-id="0b5f7-129">Example 4</span></span>  

 <span data-ttu-id="0b5f7-130">下面的示例将编译并调用一个查询，该查询接受 <xref:System.String> 输入参数，然后返回一个 `Contact` 其电子邮件地址以指定的字符串开头的：</span><span class="sxs-lookup"><span data-stu-id="0b5f7-130">The following example compiles and then invokes a query that accepts a <xref:System.String> input parameter and then returns a `Contact` whose email address starts with the specified string:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples - compiled query4_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery4_mq)]
 [!code-vb[DP L2E Conceptual Examples - compiled query4_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery4_mq)]  
  
## <a name="example-5"></a><span data-ttu-id="0b5f7-131">示例 5</span><span class="sxs-lookup"><span data-stu-id="0b5f7-131">Example 5</span></span>  

 <span data-ttu-id="0b5f7-132">下面的示例将编译并调用一个查询，该查询接受 <xref:System.DateTime> 和 <xref:System.Decimal> 输入参数，并返回一个订单日期晚于 2003 年 3 月 8 日且应付款总额少于 300.00 美元的订单序列：</span><span class="sxs-lookup"><span data-stu-id="0b5f7-132">The following example compiles and then invokes a query that accepts <xref:System.DateTime> and <xref:System.Decimal> input parameters and returns a sequence of orders where the order date is later than March 8, 2003, and the total due is less than $300.00:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples - compiled query5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery5)]
 [!code-vb[DP L2E Conceptual Examples - compiled query5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery5)]  
  
## <a name="example-6"></a><span data-ttu-id="0b5f7-133">示例 6</span><span class="sxs-lookup"><span data-stu-id="0b5f7-133">Example 6</span></span>  

 <span data-ttu-id="0b5f7-134">下面的示例将编译并调用一个查询，该查询接受 <xref:System.DateTime> 输入参数，并返回一个订单日期迟于 2004 年 3 月 8 日的订单序列：</span><span class="sxs-lookup"><span data-stu-id="0b5f7-134">The following example compiles and then invokes a query that accepts a <xref:System.DateTime> input parameter and returns a sequence of orders where the order date is later than March 8, 2004.</span></span> <span data-ttu-id="0b5f7-135">此查询将订单信息返回为匿名类型序列。</span><span class="sxs-lookup"><span data-stu-id="0b5f7-135">This query returns the order information as a sequence of anonymous types.</span></span> <span data-ttu-id="0b5f7-136">匿名类型由编译器推断，因此不能在 <xref:System.Data.Objects.CompiledQuery> 的 `Compile` 方法中指定类型参数，该类型只能在查询本身中定义。</span><span class="sxs-lookup"><span data-stu-id="0b5f7-136">Anonymous types are inferred by the compiler, so you cannot specify type parameters in the <xref:System.Data.Objects.CompiledQuery>'s `Compile` method and the type is defined in the query itself.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples - compiled query6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery6)]
 [!code-vb[DP L2E Conceptual Examples - compiled query6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery6)]  
  
## <a name="example-7"></a><span data-ttu-id="0b5f7-137">示例 7</span><span class="sxs-lookup"><span data-stu-id="0b5f7-137">Example 7</span></span>  

 <span data-ttu-id="0b5f7-138">下面的示例编译并调用一个查询，该查询接受用户定义的结构输入参数并返回一个订单序列。</span><span class="sxs-lookup"><span data-stu-id="0b5f7-138">The following example compiles and then invokes a query that accepts a user-defined structure input parameter and returns a sequence of orders.</span></span> <span data-ttu-id="0b5f7-139">该结构定义开始日期、结束日期和应付款总额查询参数，该查询返回在 2003 年 3 月 3 日到 3 月 8 日之间发货的应付款总额超过 700.00 美元的订单。</span><span class="sxs-lookup"><span data-stu-id="0b5f7-139">The structure defines start date, end date, and total due query parameters, and the query returns orders shipped between March 3 and March 8, 2003 with a total due greater than $700.00.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples - compiled query7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery7)]
 [!code-vb[DP L2E Conceptual Examples - compiled query7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery7)]  
  
 <span data-ttu-id="0b5f7-140">定义查询参数的结构：</span><span class="sxs-lookup"><span data-stu-id="0b5f7-140">The structure that defines the query parameters:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples - MyParamsStruct](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myparamsstruct)]
 [!code-vb[DP L2E Conceptual Examples - MyParamsStruct](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myparamsstruct)]  
  
## <a name="see-also"></a><span data-ttu-id="0b5f7-141">请参阅</span><span class="sxs-lookup"><span data-stu-id="0b5f7-141">See also</span></span>

- [<span data-ttu-id="0b5f7-142">ADO.NET 实体框架</span><span class="sxs-lookup"><span data-stu-id="0b5f7-142">ADO.NET Entity Framework</span></span>](../index.md)
- [<span data-ttu-id="0b5f7-143">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="0b5f7-143">LINQ to Entities</span></span>](linq-to-entities.md)
- [<span data-ttu-id="0b5f7-144">EF 合并选项和已编译的查询</span><span class="sxs-lookup"><span data-stu-id="0b5f7-144">EF Merge Options and Compiled Queries</span></span>](/archive/blogs/dsimmons/ef-merge-options-and-compiled-queries)
