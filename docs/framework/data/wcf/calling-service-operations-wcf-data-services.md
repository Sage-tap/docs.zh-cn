---
description: '了解详细信息：调用服务操作 (WCF Data Services) '
title: 调用服务操作（WCF 数据服务）
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1767f3a7-29d2-4834-a763-7d169693fa8b
ms.openlocfilehash: 49b08581e42fcd20b9d560d73379eb43ebbf2eb4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99766460"
---
# <a name="calling-service-operations-wcf-data-services"></a><span data-ttu-id="6f2c8-103">调用服务操作（WCF 数据服务）</span><span class="sxs-lookup"><span data-stu-id="6f2c8-103">Calling Service Operations (WCF Data Services)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="6f2c8-104">OData) Open Data Protocol (定义数据服务的服务操作。</span><span class="sxs-lookup"><span data-stu-id="6f2c8-104">The Open Data Protocol (OData) defines service operations for a data service.</span></span> <span data-ttu-id="6f2c8-105">WCF Data Services 使你能够将此类操作定义为数据服务中的方法。</span><span class="sxs-lookup"><span data-stu-id="6f2c8-105">WCF Data Services enables you to define such operations as methods on the data service.</span></span> <span data-ttu-id="6f2c8-106">与其他数据服务资源一样，这些服务操作也通过 URI 进行寻址。</span><span class="sxs-lookup"><span data-stu-id="6f2c8-106">Like other data service resources, these service operations are addressed by using URIs.</span></span> <span data-ttu-id="6f2c8-107">服务操作可以返回实体类型的集合、单个实体类型实例的集合和基元类型（如整数和字符串）的集合。</span><span class="sxs-lookup"><span data-stu-id="6f2c8-107">A service operation can return collections of entity types, single entity type instances, and primitive types, such as integer and string.</span></span> <span data-ttu-id="6f2c8-108">服务操作还可以返回 `null`（在 Visual Basic 中为 `Nothing`）。</span><span class="sxs-lookup"><span data-stu-id="6f2c8-108">A service operation can also return `null` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="6f2c8-109">WCF Data Services 客户端库可用于访问支持 HTTP GET 请求的服务操作。</span><span class="sxs-lookup"><span data-stu-id="6f2c8-109">The WCF Data Services client library can be used to access service operations that support HTTP GET requests.</span></span> <span data-ttu-id="6f2c8-110">这些种类的服务操作定义为应用了 <xref:System.ServiceModel.Web.WebGetAttribute> 的方法。</span><span class="sxs-lookup"><span data-stu-id="6f2c8-110">These kinds of service operations are defined as methods that have the <xref:System.ServiceModel.Web.WebGetAttribute> applied.</span></span> <span data-ttu-id="6f2c8-111">有关详细信息，请参阅 [服务操作](service-operations-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="6f2c8-111">For more information, see [Service Operations](service-operations-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="6f2c8-112">服务操作在实现 OData 的数据服务所返回的元数据中公开。</span><span class="sxs-lookup"><span data-stu-id="6f2c8-112">Service operations are exposed in the metadata returned by a data service that implements the OData.</span></span> <span data-ttu-id="6f2c8-113">在元数据中，服务操作表示为 `FunctionImport` 元素。</span><span class="sxs-lookup"><span data-stu-id="6f2c8-113">In the metadata, service operations are represented as `FunctionImport` elements.</span></span> <span data-ttu-id="6f2c8-114">生成强类型时 <xref:System.Data.Services.Client.DataServiceContext> ，添加服务引用和 DataSvcUtil.exe 工具将忽略此元素。</span><span class="sxs-lookup"><span data-stu-id="6f2c8-114">When generating the strongly typed <xref:System.Data.Services.Client.DataServiceContext>, the Add Service Reference and DataSvcUtil.exe tools ignore this element.</span></span> <span data-ttu-id="6f2c8-115">因此，无法在上下文中找到一种方法用来直接调用服务操作。</span><span class="sxs-lookup"><span data-stu-id="6f2c8-115">Because of this, you will not find a method on the context that can be used to call a service operation directly.</span></span> <span data-ttu-id="6f2c8-116">不过，仍可使用 WCF Data Services 客户端通过以下两种方式之一来调用服务操作：</span><span class="sxs-lookup"><span data-stu-id="6f2c8-116">However, you can still use the WCF Data Services client to call service operations in one of these two ways:</span></span>  
  
- <span data-ttu-id="6f2c8-117">通过调用 <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> 的 <xref:System.Data.Services.Client.DataServiceContext> 方法，同时提供服务操作的 URI 以及任何参数。</span><span class="sxs-lookup"><span data-stu-id="6f2c8-117">By calling the <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> method on the <xref:System.Data.Services.Client.DataServiceContext>, supplying the URI of the service operation, along with any parameters.</span></span> <span data-ttu-id="6f2c8-118">此方法用于调用任意 GET 服务操作。</span><span class="sxs-lookup"><span data-stu-id="6f2c8-118">This method is used to call any GET service operation.</span></span>  
  
- <span data-ttu-id="6f2c8-119">通过对 <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> 使用 <xref:System.Data.Services.Client.DataServiceContext> 方法来创建 <xref:System.Data.Services.Client.DataServiceQuery%601> 对象。</span><span class="sxs-lookup"><span data-stu-id="6f2c8-119">By using the <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> method on the <xref:System.Data.Services.Client.DataServiceContext> to create a <xref:System.Data.Services.Client.DataServiceQuery%601> object.</span></span> <span data-ttu-id="6f2c8-120">在调用 <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> 时，该服务操作的名称将提供给 `entitySetName` 参数。</span><span class="sxs-lookup"><span data-stu-id="6f2c8-120">When calling <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>, the name of the service operation is supplied to the `entitySetName` parameter.</span></span> <span data-ttu-id="6f2c8-121">此方法返回一个 <xref:System.Data.Services.Client.DataServiceQuery%601> 对象，该对象在枚举时或在调用 <xref:System.Data.Services.Client.DataServiceQuery%601.Execute%2A> 方法时调用该服务操作。</span><span class="sxs-lookup"><span data-stu-id="6f2c8-121">This method returns a <xref:System.Data.Services.Client.DataServiceQuery%601> object that calls the service operation when enumerated or when the <xref:System.Data.Services.Client.DataServiceQuery%601.Execute%2A> method is called.</span></span> <span data-ttu-id="6f2c8-122">此方法用于调用返回集合的 GET 服务操作。</span><span class="sxs-lookup"><span data-stu-id="6f2c8-122">This method is used to call GET service operations that return a collection.</span></span> <span data-ttu-id="6f2c8-123">可通过使用 <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> 方法来提供单个参数。</span><span class="sxs-lookup"><span data-stu-id="6f2c8-123">A single parameter can be supplied by using the <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> method.</span></span> <span data-ttu-id="6f2c8-124">可以进一步编辑此方法返回的 <xref:System.Data.Services.Client.DataServiceQuery%601> 对象，就像对待任何查询对象一样。</span><span class="sxs-lookup"><span data-stu-id="6f2c8-124">The <xref:System.Data.Services.Client.DataServiceQuery%601> object returned by this method can be further composed against like any query object.</span></span> <span data-ttu-id="6f2c8-125">有关详细信息，请参阅 [查询数据服务](querying-the-data-service-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="6f2c8-125">For more information, see [Querying the Data Service](querying-the-data-service-wcf-data-services.md).</span></span>  
  
## <a name="considerations-for-calling-service-operations"></a><span data-ttu-id="6f2c8-126">调用服务操作的注意事项</span><span class="sxs-lookup"><span data-stu-id="6f2c8-126">Considerations for Calling Service Operations</span></span>  

 <span data-ttu-id="6f2c8-127">使用 WCF Data Services 客户端调用服务操作时，请注意以下事项。</span><span class="sxs-lookup"><span data-stu-id="6f2c8-127">The following considerations apply when using the WCF Data Services client to call service operations.</span></span>  
  
- <span data-ttu-id="6f2c8-128">异步访问数据服务时，必须在 <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A> / <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A> 上 <xref:System.Data.Services.Client.DataServiceContext> 或 <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> / <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> 方法上 <xref:System.Data.Services.Client.DataServiceQuery%601> 使用等效的异步方法。</span><span class="sxs-lookup"><span data-stu-id="6f2c8-128">When accessing the data service asynchronously, you must use the equivalent asynchronous <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A>/<xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A> methods on <xref:System.Data.Services.Client.DataServiceContext> or the <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A>/<xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> methods on <xref:System.Data.Services.Client.DataServiceQuery%601>.</span></span>  
  
- <span data-ttu-id="6f2c8-129">WCF Data Services 客户端库无法具体化返回基元类型集合的服务操作的结果。</span><span class="sxs-lookup"><span data-stu-id="6f2c8-129">The WCF Data Services client library cannot materialize the results from a service operation that returns a collection of primitive types.</span></span>  
  
- <span data-ttu-id="6f2c8-130">WCF Data Services 客户端库不支持调用后服务操作。</span><span class="sxs-lookup"><span data-stu-id="6f2c8-130">The WCF Data Services client library does not support calling POST service operations.</span></span> <span data-ttu-id="6f2c8-131">服务操作由 HTTP POST 调用，后者通过使用 <xref:System.ServiceModel.Web.WebInvokeAttribute> 配合 `Method="POST"` 参数定义。</span><span class="sxs-lookup"><span data-stu-id="6f2c8-131">Service operations that are called by an HTTP POST are defined by using the <xref:System.ServiceModel.Web.WebInvokeAttribute> with the `Method="POST"` parameter.</span></span> <span data-ttu-id="6f2c8-132">要通过使用 HTTP POST 请求调用服务操作，必须使用 <xref:System.Net.HttpWebRequest>。</span><span class="sxs-lookup"><span data-stu-id="6f2c8-132">To call a service operation by using an HTTP POST request, you must instead use an <xref:System.Net.HttpWebRequest>.</span></span>  
  
- <span data-ttu-id="6f2c8-133">您不能使用 <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> 调用这样的 GET 服务操作：它返回实体或基元类型的单个结果，或需要多个输入参数。</span><span class="sxs-lookup"><span data-stu-id="6f2c8-133">You cannot use <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> to call a GET service operation that returns a single result, of either entity or primitive type, or that requires more than one input parameter.</span></span> <span data-ttu-id="6f2c8-134">必须调用 <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="6f2c8-134">You must instead call the <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> method.</span></span>  
  
- <span data-ttu-id="6f2c8-135">请考虑在强类型化分部类（由工具生成）上创建扩展方法，该 <xref:System.Data.Services.Client.DataServiceContext> 分部类使用 <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> 或 <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> 方法来调用服务操作。</span><span class="sxs-lookup"><span data-stu-id="6f2c8-135">Consider creating an extension method on the strongly typed <xref:System.Data.Services.Client.DataServiceContext> partial class, which is generated by the tools, that uses either the <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> or the <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> method to call a service operation.</span></span> <span data-ttu-id="6f2c8-136">这样您就可以直接从上下文调用服务操作。</span><span class="sxs-lookup"><span data-stu-id="6f2c8-136">This enables you to call service operations directly from the context.</span></span> <span data-ttu-id="6f2c8-137">有关详细信息，请参阅博客文章 [服务操作和 WCF Data Services 客户端](/archive/blogs/astoriateam/service-operations-and-the-wcf-data-services-client)。</span><span class="sxs-lookup"><span data-stu-id="6f2c8-137">For more information, see the blog post [Service Operations and the WCF Data Services Client](/archive/blogs/astoriateam/service-operations-and-the-wcf-data-services-client).</span></span>  
  
- <span data-ttu-id="6f2c8-138">使用 <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> 调用服务操作时，客户端库会 <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> 通过对保留字符执行百分号编码（如与号 ( # A0) ），并对字符串中的单引号进行转义来自动转义提供给的字符。</span><span class="sxs-lookup"><span data-stu-id="6f2c8-138">When you use <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> to call a service operation, the client library automatically escapes characters supplied to the <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> by performing percent-encoding of reserved characters, such as ampersand (&), and escaping of single-quotes in strings.</span></span> <span data-ttu-id="6f2c8-139">但是，当您调用某一 *Execute* 方法来调用服务操作时，您必须记得对任何用户提供的字符串值执行这种转义。</span><span class="sxs-lookup"><span data-stu-id="6f2c8-139">However, when you call one of the *Execute* methods to call a service operation, you must remember to perform this escaping of any user-supplied string values.</span></span> <span data-ttu-id="6f2c8-140">URI 中的单引号转义为单引号对。</span><span class="sxs-lookup"><span data-stu-id="6f2c8-140">Single-quotes in URIs are escaped as pairs of single-quotes.</span></span>  
  
## <a name="examples-of-calling-service-operations"></a><span data-ttu-id="6f2c8-141">调用服务操作示例</span><span class="sxs-lookup"><span data-stu-id="6f2c8-141">Examples of Calling Service Operations</span></span>  

 <span data-ttu-id="6f2c8-142">本部分包含以下示例，说明如何使用 WCF Data Services 客户端库调用服务操作：</span><span class="sxs-lookup"><span data-stu-id="6f2c8-142">This section contains the following examples of how to call service operations by using the WCF Data Services client library:</span></span>  
  
- [<span data-ttu-id="6f2c8-143">调用 Execute &lt; T &gt; 以返回实体集合</span><span class="sxs-lookup"><span data-stu-id="6f2c8-143">Calling Execute&lt;T&gt; to Return a Collection of Entities</span></span>](calling-service-operations-wcf-data-services.md#ExecuteIQueryable)  
  
- [<span data-ttu-id="6f2c8-144">使用 Servicecontext.createquery &lt; T &gt; 返回实体集合</span><span class="sxs-lookup"><span data-stu-id="6f2c8-144">Using CreateQuery&lt;T&gt; to Return a Collection of Entities</span></span>](calling-service-operations-wcf-data-services.md#CreateQueryIQueryable)  
  
- [<span data-ttu-id="6f2c8-145">调用 Execute &lt; T &gt; 以返回单个实体</span><span class="sxs-lookup"><span data-stu-id="6f2c8-145">Calling Execute&lt;T&gt; to Return a Single Entity</span></span>](calling-service-operations-wcf-data-services.md#ExecuteSingleEntity)  
  
- [<span data-ttu-id="6f2c8-146">调用 Execute &lt; T &gt; 以返回基元值集合</span><span class="sxs-lookup"><span data-stu-id="6f2c8-146">Calling Execute&lt;T&gt; to Return a Collection of Primitive Values</span></span>](calling-service-operations-wcf-data-services.md#ExecutePrimitiveCollection)  
  
- [<span data-ttu-id="6f2c8-147">调用 Execute &lt; T &gt; 以返回单个基元值</span><span class="sxs-lookup"><span data-stu-id="6f2c8-147">Calling Execute&lt;T&gt; to Return a Single Primitive Value</span></span>](calling-service-operations-wcf-data-services.md#ExecutePrimitiveValue)  
  
- [<span data-ttu-id="6f2c8-148">调用不返回数据的服务操作</span><span class="sxs-lookup"><span data-stu-id="6f2c8-148">Calling a Service Operation that Returns No Data</span></span>](calling-service-operations-wcf-data-services.md#ExecuteVoid)  
  
- [<span data-ttu-id="6f2c8-149">异步调用服务操作</span><span class="sxs-lookup"><span data-stu-id="6f2c8-149">Calling a Service Operation Asynchronously</span></span>](calling-service-operations-wcf-data-services.md#ExecuteAsync)  
  
<a name="ExecuteIQueryable"></a>

### <a name="calling-executet-to-return-a-collection-of-entities"></a><span data-ttu-id="6f2c8-150">调用 Execute \<T> 以返回实体集合</span><span class="sxs-lookup"><span data-stu-id="6f2c8-150">Calling Execute\<T> to Return a Collection of Entities</span></span>  

 <span data-ttu-id="6f2c8-151">下面的示例调用名为 GetOrdersByCity 的服务操作，该操作采用字符串参数 `city`，并返回 <xref:System.Linq.IQueryable%601>：</span><span class="sxs-lookup"><span data-stu-id="6f2c8-151">The following example calls a service operation named GetOrdersByCity, which takes a string parameter of `city` and returns an <xref:System.Linq.IQueryable%601>:</span></span>  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationiqueryable)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationiqueryable)]  
  
 <span data-ttu-id="6f2c8-152">在此示例中，该服务操作返回 `Order` 对象的集合，其中含有相关的 `Order_Detail` 对象。</span><span class="sxs-lookup"><span data-stu-id="6f2c8-152">In this example, the service operation returns a collection of `Order` objects with related `Order_Detail` objects.</span></span>  
  
<a name="CreateQueryIQueryable"></a>

### <a name="using-createqueryt-to-return-a-collection-of-entities"></a><span data-ttu-id="6f2c8-153">使用 Servicecontext.createquery \<T> 返回实体集合</span><span class="sxs-lookup"><span data-stu-id="6f2c8-153">Using CreateQuery\<T> to Return a Collection of Entities</span></span>  

 <span data-ttu-id="6f2c8-154">下面的示例使用 <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> 来返回用于调用同一 GetOrdersByCity 服务操作的 <xref:System.Data.Services.Client.DataServiceQuery%601>：</span><span class="sxs-lookup"><span data-stu-id="6f2c8-154">The following example uses the <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> to return a <xref:System.Data.Services.Client.DataServiceQuery%601> that is used to call the same GetOrdersByCity service operation:</span></span>  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationcreatequery)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationcreatequery)]  
  
 <span data-ttu-id="6f2c8-155">在此示例中，<xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> 方法用于向查询中添加参数，而 <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> 方法用于在结果中包括相关 Order_Details 对象。</span><span class="sxs-lookup"><span data-stu-id="6f2c8-155">In this example, the <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> method is used to add the parameter to the query, and the <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> method is used to include related Order_Details objects in the results.</span></span>  
  
<a name="ExecuteSingleEntity"></a>

### <a name="calling-executet-to-return-a-single-entity"></a><span data-ttu-id="6f2c8-156">调用 Execute \<T> 以返回单个实体</span><span class="sxs-lookup"><span data-stu-id="6f2c8-156">Calling Execute\<T> to Return a Single Entity</span></span>  

 <span data-ttu-id="6f2c8-157">下面的示例调用名为 GetNewestOrder 的服务操作，该操作仅返回单个 Order 实体：</span><span class="sxs-lookup"><span data-stu-id="6f2c8-157">The following example calls a service operation named GetNewestOrder that returns only a single Order entity:</span></span>  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationsingleentity)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationsingleentity)]  
  
 <span data-ttu-id="6f2c8-158">在此示例中，<xref:System.Linq.Enumerable.FirstOrDefault%2A> 方法用于在执行时仅请求单个 Order 实体。</span><span class="sxs-lookup"><span data-stu-id="6f2c8-158">In this example, the <xref:System.Linq.Enumerable.FirstOrDefault%2A> method is used to request only a single Order entity on execution.</span></span>  
  
<a name="ExecutePrimitiveCollection"></a>

### <a name="calling-executet-to-return-a-collection-of-primitive-values"></a><span data-ttu-id="6f2c8-159">调用 Execute \<T> 以返回基元值集合</span><span class="sxs-lookup"><span data-stu-id="6f2c8-159">Calling Execute\<T> to Return a Collection of Primitive Values</span></span>  

 <span data-ttu-id="6f2c8-160">下面的示例调用返回字符串值集合的服务操作：</span><span class="sxs-lookup"><span data-stu-id="6f2c8-160">The following example calls a service operation that returns a collection of string values:</span></span>  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationEnumString](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationenumstring)]  
  
<a name="ExecutePrimitiveValue"></a>

### <a name="calling-executet-to-return-a-single-primitive-value"></a><span data-ttu-id="6f2c8-161">调用 Execute \<T> 以返回单个基元值</span><span class="sxs-lookup"><span data-stu-id="6f2c8-161">Calling Execute\<T> to Return a Single Primitive Value</span></span>  

 <span data-ttu-id="6f2c8-162">下面的示例调用返回单个字符串值的服务操作：</span><span class="sxs-lookup"><span data-stu-id="6f2c8-162">The following example calls a service operation that returns a single string value:</span></span>  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationsingleint)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationsingleint)]  
  
 <span data-ttu-id="6f2c8-163">同样，在此示例中，<xref:System.Linq.Enumerable.FirstOrDefault%2A> 方法用于在执行时仅请求单个整数值。</span><span class="sxs-lookup"><span data-stu-id="6f2c8-163">Again in this example, the <xref:System.Linq.Enumerable.FirstOrDefault%2A> method is used to request only a single integer value on execution.</span></span>  
  
<a name="ExecuteVoid"></a>

### <a name="calling-a-service-operation-that-returns-no-data"></a><span data-ttu-id="6f2c8-164">调用不返回数据的服务操作</span><span class="sxs-lookup"><span data-stu-id="6f2c8-164">Calling a Service Operation that Returns No Data</span></span>  

 <span data-ttu-id="6f2c8-165">下面的示例调用不返回任何数据的服务操作：</span><span class="sxs-lookup"><span data-stu-id="6f2c8-165">The following example calls a service operation that returns no data:</span></span>  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationvoid)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationvoid)]  
  
 <span data-ttu-id="6f2c8-166">由于不返回数据，因此不分配执行的值。</span><span class="sxs-lookup"><span data-stu-id="6f2c8-166">Because not data is returned, the value of the execution is not assigned.</span></span> <span data-ttu-id="6f2c8-167">请求已成功的唯一指示是未引发 <xref:System.Data.Services.Client.DataServiceQueryException>。</span><span class="sxs-lookup"><span data-stu-id="6f2c8-167">The only indication that the request has succeeded is that no <xref:System.Data.Services.Client.DataServiceQueryException> is raised.</span></span>  
  
<a name="ExecuteAsync"></a>

### <a name="calling-a-service-operation-asynchronously"></a><span data-ttu-id="6f2c8-168">异步调用服务操作</span><span class="sxs-lookup"><span data-stu-id="6f2c8-168">Calling a Service Operation Asynchronously</span></span>  

 <span data-ttu-id="6f2c8-169">下面的示例通过调用 <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A> 和 <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A> 来异步调用服务操作：</span><span class="sxs-lookup"><span data-stu-id="6f2c8-169">The following example calls a service operation asynchronously by calling <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A> and <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>:</span></span>  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onasyncexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onasyncexecutioncomplete)]  
  
 <span data-ttu-id="6f2c8-170">由于不返回数据，因此不分配由该执行返回的值。</span><span class="sxs-lookup"><span data-stu-id="6f2c8-170">Because no data is returned, the value returned by the execution is not assigned.</span></span> <span data-ttu-id="6f2c8-171">请求已成功的唯一指示是未引发 <xref:System.Data.Services.Client.DataServiceQueryException>。</span><span class="sxs-lookup"><span data-stu-id="6f2c8-171">The only indication that the request has succeeded is that no <xref:System.Data.Services.Client.DataServiceQueryException> is raised.</span></span>  
  
 <span data-ttu-id="6f2c8-172">下面的示例通过使用 <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> 来异步调用同一服务操作：</span><span class="sxs-lookup"><span data-stu-id="6f2c8-172">The following example calls the same service operation asynchronously by using <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>:</span></span>  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationqueryasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationqueryasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onasyncqueryexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onasyncqueryexecutioncomplete)]  
  
## <a name="see-also"></a><span data-ttu-id="6f2c8-173">请参阅</span><span class="sxs-lookup"><span data-stu-id="6f2c8-173">See also</span></span>

- [<span data-ttu-id="6f2c8-174">WCF 数据服务客户端库</span><span class="sxs-lookup"><span data-stu-id="6f2c8-174">WCF Data Services Client Library</span></span>](wcf-data-services-client-library.md)
