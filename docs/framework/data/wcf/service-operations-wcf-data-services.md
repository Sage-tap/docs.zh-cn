---
description: '了解详细信息：服务操作 (WCF Data Services) '
title: 服务操作（WCF 数据服务）
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service operations [WCF Data Services]
- WCF Data Services, service operations
ms.assetid: 583a690a-e60f-4990-8991-d6efce069d76
ms.openlocfilehash: 3c811da86b1654f33675b46575d45884a6ba9b1f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99773090"
---
# <a name="service-operations-wcf-data-services"></a><span data-ttu-id="e8f07-103">服务操作（WCF 数据服务）</span><span class="sxs-lookup"><span data-stu-id="e8f07-103">Service Operations (WCF Data Services)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="e8f07-104">WCF Data Services 使你能够在数据服务上定义服务操作，以便在服务器上公开方法。</span><span class="sxs-lookup"><span data-stu-id="e8f07-104">WCF Data Services enables you to define service operations on a data service to expose methods on the server.</span></span> <span data-ttu-id="e8f07-105">与其他数据服务资源一样，服务操作也是通过 URI 进行寻址。</span><span class="sxs-lookup"><span data-stu-id="e8f07-105">Like other data service resources, service operations are addressed by URIs.</span></span> <span data-ttu-id="e8f07-106">使用服务操作可以在数据服务中公开业务逻辑；例如，实现验证逻辑，应用基于角色的安全性或公开专用查询功能。</span><span class="sxs-lookup"><span data-stu-id="e8f07-106">Service operations enable you to expose business logic in a data service, such as to implement validation logic, to apply role-based security, or to expose specialized querying capabilities.</span></span> <span data-ttu-id="e8f07-107">服务操作是添加到派生自 <xref:System.Data.Services.DataService%601> 的数据服务类的方法。</span><span class="sxs-lookup"><span data-stu-id="e8f07-107">Service operations are methods added to the data service class that derives from <xref:System.Data.Services.DataService%601>.</span></span> <span data-ttu-id="e8f07-108">与所有其他数据服务资源一样，也可以向服务操作方法提供参数。</span><span class="sxs-lookup"><span data-stu-id="e8f07-108">Like all other data service resources, you can supply parameters to the service operation method.</span></span> <span data-ttu-id="e8f07-109">例如，以下服务操作 URI 基于 [快速入门](quickstart-wcf-data-services.md) 数据服务 () 将值传递 `London` 给 `city` 参数：</span><span class="sxs-lookup"><span data-stu-id="e8f07-109">For example, the following service operation URI (based on the [quickstart](quickstart-wcf-data-services.md) data service) passes the value `London` to the `city` parameter:</span></span>

```http
http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'
```

<span data-ttu-id="e8f07-110">此服务操作的定义如下所示：</span><span class="sxs-lookup"><span data-stu-id="e8f07-110">The definition for this service operation is as follows:</span></span>

[!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationdef)]
[!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationdef)]

<span data-ttu-id="e8f07-111">使用 <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> 的 <xref:System.Data.Services.DataService%601> 可以直接访问数据服务正在使用的数据源。</span><span class="sxs-lookup"><span data-stu-id="e8f07-111">You can use the <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> of the <xref:System.Data.Services.DataService%601> to directly access the data source that the data service is using.</span></span> <span data-ttu-id="e8f07-112">有关详细信息，请参阅 [如何：定义服务操作](how-to-define-a-service-operation-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="e8f07-112">For more information, see [How to: Define a Service Operation](how-to-define-a-service-operation-wcf-data-services.md).</span></span>

<span data-ttu-id="e8f07-113">有关如何从 .NET Framework 客户端应用程序调用服务操作的信息，请参阅 [调用服务操作](calling-service-operations-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="e8f07-113">For information on how to call a service operation from a .NET Framework client application, see [Calling Service Operations](calling-service-operations-wcf-data-services.md).</span></span>

## <a name="service-operation-requirements"></a><span data-ttu-id="e8f07-114">服务操作要求</span><span class="sxs-lookup"><span data-stu-id="e8f07-114">Service Operation Requirements</span></span>

<span data-ttu-id="e8f07-115">在数据服务中定义服务操作需满足下列要求。</span><span class="sxs-lookup"><span data-stu-id="e8f07-115">The following requirements apply when defining service operations on the data service.</span></span> <span data-ttu-id="e8f07-116">如果某一方法不符合这些要求，则不会将该方法公开为数据服务的服务操作。</span><span class="sxs-lookup"><span data-stu-id="e8f07-116">If a method does not meet these requirements, it will not be exposed as a service operation for the data service.</span></span>

- <span data-ttu-id="e8f07-117">操作必须是作为数据服务类成员的公共实例方法。</span><span class="sxs-lookup"><span data-stu-id="e8f07-117">The operation must be a public instance method that is a member of the data service class.</span></span>

- <span data-ttu-id="e8f07-118">操作方法只能接受输入参数。</span><span class="sxs-lookup"><span data-stu-id="e8f07-118">The operation method may only accept input parameters.</span></span> <span data-ttu-id="e8f07-119">数据服务无法访问在消息正文中发送的数据。</span><span class="sxs-lookup"><span data-stu-id="e8f07-119">Data sent in the message body cannot be accessed by the data service.</span></span>

- <span data-ttu-id="e8f07-120">如果定义了参数，则每个参数的类型必须为基元类型。</span><span class="sxs-lookup"><span data-stu-id="e8f07-120">If parameters are defined, the type of each parameter must be a primitive type.</span></span> <span data-ttu-id="e8f07-121">任何非基元类型的数据必须序列化并传递到一个字符串参数。</span><span class="sxs-lookup"><span data-stu-id="e8f07-121">Any data of a non-primitive type must be serialized and passed into a string parameter.</span></span>

- <span data-ttu-id="e8f07-122">方法必须返回下列值之一：</span><span class="sxs-lookup"><span data-stu-id="e8f07-122">The method must return one of the following:</span></span>

  - <span data-ttu-id="e8f07-123">`void`（在 Visual Basic 中为 `Nothing`）</span><span class="sxs-lookup"><span data-stu-id="e8f07-123">`void` (`Nothing` in Visual Basic)</span></span>

  - <xref:System.Collections.Generic.IEnumerable%601>

  - <xref:System.Linq.IQueryable%601>

  - <span data-ttu-id="e8f07-124">数据服务所公开的数据模型中的实体类型。</span><span class="sxs-lookup"><span data-stu-id="e8f07-124">An entity type in the data model that the data service exposes.</span></span>

  - <span data-ttu-id="e8f07-125">整数或字符串等基元类。</span><span class="sxs-lookup"><span data-stu-id="e8f07-125">A primitive class such as integer or string.</span></span>

- <span data-ttu-id="e8f07-126">若要支持查询选项（如排序、分页和筛选），服务操作方法应返回 <xref:System.Linq.IQueryable%601>。</span><span class="sxs-lookup"><span data-stu-id="e8f07-126">In order to support query options such as sorting, paging, and filtering, service operation methods should return <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="e8f07-127">只返回 <xref:System.Collections.Generic.IEnumerable%601> 的操作拒绝对包含查询选项的服务操作的请求。</span><span class="sxs-lookup"><span data-stu-id="e8f07-127">Requests to service operations that include query options are rejected for operations that only return <xref:System.Collections.Generic.IEnumerable%601>.</span></span>

- <span data-ttu-id="e8f07-128">若要支持使用导航属性访问相关实体，服务操作必须返回 <xref:System.Linq.IQueryable%601>。</span><span class="sxs-lookup"><span data-stu-id="e8f07-128">In order to support accessing related entities by using navigation properties, the service operation must return <xref:System.Linq.IQueryable%601>.</span></span>

- <span data-ttu-id="e8f07-129">必须用 `[WebGet]` 或 `[WebInvoke]` 属性为此方法添加批注。</span><span class="sxs-lookup"><span data-stu-id="e8f07-129">The method must be annotated with the `[WebGet]` or `[WebInvoke]` attribute.</span></span>

  - <span data-ttu-id="e8f07-130">`[WebGet]` 使您能够通过使用 GET 请求调用方法。</span><span class="sxs-lookup"><span data-stu-id="e8f07-130">`[WebGet]` enables the method to be invoked by using a GET request.</span></span>

  - <span data-ttu-id="e8f07-131">`[WebInvoke(Method = "POST")]` 使您能够通过使用 POST 请求调用方法。</span><span class="sxs-lookup"><span data-stu-id="e8f07-131">`[WebInvoke(Method = "POST")]` enables the method to be invoked by using a POST request.</span></span> <span data-ttu-id="e8f07-132">其他 <xref:System.ServiceModel.Web.WebInvokeAttribute> 方法不受支持。</span><span class="sxs-lookup"><span data-stu-id="e8f07-132">Other <xref:System.ServiceModel.Web.WebInvokeAttribute> methods are not supported.</span></span>

- <span data-ttu-id="e8f07-133">可以用 <xref:System.Data.Services.SingleResultAttribute> 为服务操作添加批注，指定方法的返回值是一个实体而不是一个实体集。</span><span class="sxs-lookup"><span data-stu-id="e8f07-133">A service operation may be annotated with the <xref:System.Data.Services.SingleResultAttribute> that specifies that the return value from the method is a single entity rather than a collection of entities.</span></span> <span data-ttu-id="e8f07-134">这一区别确定了生成的响应结果串行化以及用 URI 表示其他导航属性遍历的方式。</span><span class="sxs-lookup"><span data-stu-id="e8f07-134">This distinction dictates the resulting serialization of the response and the manner in which additional navigation property traversals are represented in the URI.</span></span> <span data-ttu-id="e8f07-135">例如，当使用 AtomPub 序列化时，单个资源类型实例将表示为一个 entry 元素，而单个实例集将表示为一个 feed 元素。</span><span class="sxs-lookup"><span data-stu-id="e8f07-135">For example, when using AtomPub serialization, a single resource type instance is represented as an entry element and a set of instances as a feed element.</span></span>

## <a name="addressing-service-operations"></a><span data-ttu-id="e8f07-136">对服务操作进行寻址</span><span class="sxs-lookup"><span data-stu-id="e8f07-136">Addressing Service Operations</span></span>

<span data-ttu-id="e8f07-137">通过将方法名称放在 URI 的第一个路径段中，可以对服务操作进行寻址。</span><span class="sxs-lookup"><span data-stu-id="e8f07-137">You can address service operations by placing the name of the method in the first path segment of a URI.</span></span> <span data-ttu-id="e8f07-138">例如，下面的 URI 访问一个 `GetOrdersByState` 操作，其返回 <xref:System.Linq.IQueryable%601> 对象的 `Orders` 集合。</span><span class="sxs-lookup"><span data-stu-id="e8f07-138">As an example, the following URI accesses a `GetOrdersByState` operation that returns an <xref:System.Linq.IQueryable%601> collection of `Orders` objects.</span></span>

```http
http://localhost:12345/Northwind.svc/GetOrdersByState?state='CA'&includeItems=true
```

<span data-ttu-id="e8f07-139">当调用服务操作时，参数作为查询选项提供。</span><span class="sxs-lookup"><span data-stu-id="e8f07-139">When calling a service operation, parameters are supplied as query options.</span></span> <span data-ttu-id="e8f07-140">以前的服务操作接受字符串参数 `state` 和布尔值参数 `includeItems`，后者指示在响应中是否包括相关的 `Order_Detail` 对象。</span><span class="sxs-lookup"><span data-stu-id="e8f07-140">The previous service operation accepts both a string parameter `state` and a Boolean parameter `includeItems` that indicates whether to include related `Order_Detail` objects in the response.</span></span>

<span data-ttu-id="e8f07-141">以下是有效的服务操作的返回类型：</span><span class="sxs-lookup"><span data-stu-id="e8f07-141">The following are valid return types for a service operation:</span></span>

|<span data-ttu-id="e8f07-142">有效的返回类型</span><span class="sxs-lookup"><span data-stu-id="e8f07-142">Valid Return Types</span></span>|<span data-ttu-id="e8f07-143">URI 规则</span><span class="sxs-lookup"><span data-stu-id="e8f07-143">URI Rules</span></span>|
|------------------------|---------------|
|<span data-ttu-id="e8f07-144">`void`（在 Visual Basic 中为 `Nothing`）</span><span class="sxs-lookup"><span data-stu-id="e8f07-144">`void` (`Nothing` in Visual Basic)</span></span><br /><br /> <span data-ttu-id="e8f07-145">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="e8f07-145">-or-</span></span><br /><br /> <span data-ttu-id="e8f07-146">实体类型</span><span class="sxs-lookup"><span data-stu-id="e8f07-146">Entity types</span></span><br /><br /> <span data-ttu-id="e8f07-147">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="e8f07-147">-or-</span></span><br /><br /> <span data-ttu-id="e8f07-148">基元类型</span><span class="sxs-lookup"><span data-stu-id="e8f07-148">Primitive types</span></span>|<span data-ttu-id="e8f07-149">URI 必须是作为服务操作名称的单个路径段。</span><span class="sxs-lookup"><span data-stu-id="e8f07-149">The URI must be a single path segment that is the name of the service operation.</span></span> <span data-ttu-id="e8f07-150">不允许使用查询选项。</span><span class="sxs-lookup"><span data-stu-id="e8f07-150">Query options are not allowed.</span></span>|
|<xref:System.Collections.Generic.IEnumerable%601>|<span data-ttu-id="e8f07-151">URI 必须是作为服务操作名称的单个路径段。</span><span class="sxs-lookup"><span data-stu-id="e8f07-151">The URI must be a single path segment that is the name of the service operation.</span></span> <span data-ttu-id="e8f07-152">由于结果类型不是 <xref:System.Linq.IQueryable%601> 类型，因此不允许使用查询选项。</span><span class="sxs-lookup"><span data-stu-id="e8f07-152">Because the result type is not an <xref:System.Linq.IQueryable%601> type, query options are not allowed.</span></span>|
|<xref:System.Linq.IQueryable%601>|<span data-ttu-id="e8f07-153">除了作为服务操作名称的路径之外，还允许使用查询路径段。</span><span class="sxs-lookup"><span data-stu-id="e8f07-153">Query path segments in addition to the path that is the name of the service operation are allowed.</span></span> <span data-ttu-id="e8f07-154">也允许使用查询选项。</span><span class="sxs-lookup"><span data-stu-id="e8f07-154">Query options are also allowed.</span></span>|

<span data-ttu-id="e8f07-155">可以将其他路径段或查询选项添加到该 URI，具体取决于服务操作的返回类型。</span><span class="sxs-lookup"><span data-stu-id="e8f07-155">Additional path segments or query options may be added to the URI depending on the return type of the service operation.</span></span> <span data-ttu-id="e8f07-156">例如，以下 URI 访问 `GetOrdersByCity` 操作，该操作返回 <xref:System.Linq.IQueryable%601> 对象的 `Orders` 集合（按 `RequiredDate` 的降序顺序排序）以及相关的 `Order_Details` 对象：</span><span class="sxs-lookup"><span data-stu-id="e8f07-156">For example, the following URI accesses a `GetOrdersByCity` operation that returns an <xref:System.Linq.IQueryable%601> collection of `Orders` objects, ordered by `RequiredDate` in descending order, along with the related `Order_Details` objects:</span></span>

```http
http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc
```

## <a name="service-operations-access-control"></a><span data-ttu-id="e8f07-157">服务操作访问控制</span><span class="sxs-lookup"><span data-stu-id="e8f07-157">Service Operations Access Control</span></span>

<span data-ttu-id="e8f07-158">服务操作的服务范围可见性由 <xref:System.Data.Services.IDataServiceConfiguration.SetServiceOperationAccessRule%2A> 类的 <xref:System.Data.Services.IDataServiceConfiguration> 方法控制，其方式与使用 <xref:System.Data.Services.IDataServiceConfiguration.SetEntitySetAccessRule%2A> 方法控制实体集可见性的方式大致相同。</span><span class="sxs-lookup"><span data-stu-id="e8f07-158">Service-wide visibility of service operations is controlled by the <xref:System.Data.Services.IDataServiceConfiguration.SetServiceOperationAccessRule%2A> method on the <xref:System.Data.Services.IDataServiceConfiguration> class in much the same way that entity set visibility is controlled by using the <xref:System.Data.Services.IDataServiceConfiguration.SetEntitySetAccessRule%2A> method.</span></span> <span data-ttu-id="e8f07-159">例如，数据服务定义中的以下代码行用于访问 `CustomersByCity` 服务操作。</span><span class="sxs-lookup"><span data-stu-id="e8f07-159">For example, the following line of code in the data service definition enables access to the `CustomersByCity` service operation.</span></span>

[!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationconfig)]
[!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationconfig)]

> [!NOTE]
> <span data-ttu-id="e8f07-160">如果服务操作的返回类型已通过限制访问基础实体集的方式被隐藏，则该服务操作将不能用于客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="e8f07-160">If a service operation has a return type that has been hidden by restricting access on the underlying entity sets, then the service operation will not be available to client applications.</span></span>

<span data-ttu-id="e8f07-161">有关详细信息，请参阅 [如何：定义服务操作](how-to-define-a-service-operation-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="e8f07-161">For more information, see [How to: Define a Service Operation](how-to-define-a-service-operation-wcf-data-services.md).</span></span>

## <a name="raising-exceptions"></a><span data-ttu-id="e8f07-162">引发异常</span><span class="sxs-lookup"><span data-stu-id="e8f07-162">Raising Exceptions</span></span>

<span data-ttu-id="e8f07-163">在数据服务执行中引发异常时，我们建议您始终使用 <xref:System.Data.Services.DataServiceException> 类。</span><span class="sxs-lookup"><span data-stu-id="e8f07-163">We recommend that you use the <xref:System.Data.Services.DataServiceException> class whenever you raise an exception in the data service execution.</span></span> <span data-ttu-id="e8f07-164">这是因为数据服务运行时知道如何正确地将此异常对象的属性映射到 HTTP 响应消息。</span><span class="sxs-lookup"><span data-stu-id="e8f07-164">This is because the data service runtime knows how to map properties of this exception object correctly to the HTTP response message.</span></span> <span data-ttu-id="e8f07-165">在服务操作中引发 <xref:System.Data.Services.DataServiceException> 时，返回的异常包装在 <xref:System.Reflection.TargetInvocationException> 中。</span><span class="sxs-lookup"><span data-stu-id="e8f07-165">When you raise a <xref:System.Data.Services.DataServiceException> in a service operation, the returned exception is wrapped in a <xref:System.Reflection.TargetInvocationException>.</span></span> <span data-ttu-id="e8f07-166">若要返回基 <xref:System.Data.Services.DataServiceException> 而不包含 <xref:System.Reflection.TargetInvocationException>，您必须重写 <xref:System.Data.Services.DataService%601.HandleException%2A> 中的 <xref:System.Data.Services.DataService%601> 方法，从 <xref:System.Data.Services.DataServiceException> 中提取 <xref:System.Reflection.TargetInvocationException>，并将其作为顶级错误返回，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="e8f07-166">To return the base <xref:System.Data.Services.DataServiceException> without the enclosing <xref:System.Reflection.TargetInvocationException>, you must override the <xref:System.Data.Services.DataService%601.HandleException%2A> method in the <xref:System.Data.Services.DataService%601>, extract the <xref:System.Data.Services.DataServiceException> from the <xref:System.Reflection.TargetInvocationException>, and return it as the top-level error, as in the following example:</span></span>

[!code-csharp[Astoria Northwind Service#HandleExceptions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#handleexceptions)]
[!code-vb[Astoria Northwind Service#HandleExceptions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#handleexceptions)]

## <a name="see-also"></a><span data-ttu-id="e8f07-167">请参阅</span><span class="sxs-lookup"><span data-stu-id="e8f07-167">See also</span></span>

- [<span data-ttu-id="e8f07-168">侦听器</span><span class="sxs-lookup"><span data-stu-id="e8f07-168">Interceptors</span></span>](interceptors-wcf-data-services.md)
