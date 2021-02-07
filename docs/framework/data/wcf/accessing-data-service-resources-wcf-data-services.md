---
description: '了解详细信息：访问数据服务资源 (WCF Data Services) '
title: 访问数据服务资源（WCF 数据服务）
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, querying
- getting started, WCF Data Services
- querying the data service [WCF Data Service]
- WCF Data Services, getting started
- WCF Data Services, accessing data
ms.assetid: 9665ff5b-3e3a-495d-bf83-d531d5d060ed
ms.openlocfilehash: b1b4d94b020dcbb942959dfbf3fb3fc26dcbf915
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99766642"
---
# <a name="accessing-data-service-resources-wcf-data-services"></a><span data-ttu-id="006ff-103">访问数据服务资源（WCF 数据服务）</span><span class="sxs-lookup"><span data-stu-id="006ff-103">Accessing Data Service Resources (WCF Data Services)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="006ff-104">WCF Data Services 支持 Open Data Protocol (OData) 将数据公开为包含由 Uri 寻址的资源的源。</span><span class="sxs-lookup"><span data-stu-id="006ff-104">WCF Data Services supports the Open Data Protocol (OData) to expose your data as a feed with resources that are addressable by URIs.</span></span> <span data-ttu-id="006ff-105">这些资源根据 [实体数据模型](../adonet/entity-data-model.md)的实体关系约定来表示。</span><span class="sxs-lookup"><span data-stu-id="006ff-105">These resources are represented according to the entity-relationship conventions of the [Entity Data Model](../adonet/entity-data-model.md).</span></span> <span data-ttu-id="006ff-106">在此模型中，实体表示作为应用程序域中数据类型的数据操作单元，如客户、订单、项目和产品。</span><span class="sxs-lookup"><span data-stu-id="006ff-106">In this model, entities represent operational units of data that are data types in an application domain, such as customers, orders, items, and products.</span></span> <span data-ttu-id="006ff-107">可以通过使用具象状态传输 (REST) 的语义（尤其是标准 HTTP 谓词 GET、PUT、POST 和 DELETE）访问和更改实体数据。</span><span class="sxs-lookup"><span data-stu-id="006ff-107">Entity data is accessed and changed by using the semantics of representational state transfer (REST), specifically the standard HTTP verbs of GET, PUT, POST, and DELETE.</span></span>  
  
## <a name="addressing-resources"></a><span data-ttu-id="006ff-108">处理资源</span><span class="sxs-lookup"><span data-stu-id="006ff-108">Addressing Resources</span></span>  

 <span data-ttu-id="006ff-109">在 OData 中，通过使用 URI 来处理数据模型公开的任何数据。</span><span class="sxs-lookup"><span data-stu-id="006ff-109">In OData, you address any data exposed by the data model by using a URI.</span></span> <span data-ttu-id="006ff-110">例如，下面的 URI 返回一个作为 Customers 实体集的源，该实体集中包含 Customer 实体类型的所有实例的项：</span><span class="sxs-lookup"><span data-stu-id="006ff-110">For example, the following URI returns a feed that is the Customers entity set, which contains entries for all instances of the Customer entity type:</span></span>  
  
<https://services.odata.org/Northwind/Northwind.svc/Customers>
  
 <span data-ttu-id="006ff-111">实体具有称为实体键的特殊属性。</span><span class="sxs-lookup"><span data-stu-id="006ff-111">Entities have special properties called entity keys.</span></span> <span data-ttu-id="006ff-112">实体键用于在实体集中唯一标识某个实体。</span><span class="sxs-lookup"><span data-stu-id="006ff-112">An entity key is used to uniquely identify a single entity in an entity set.</span></span> <span data-ttu-id="006ff-113">这样，您可以在实体集中对某种实体类型的特定实例进行寻址。</span><span class="sxs-lookup"><span data-stu-id="006ff-113">This enables you to address a specific instance of an entity type in the entity set.</span></span> <span data-ttu-id="006ff-114">例如，下面的 URI 返回 Customer 实体类型的具有键值 `ALFKI` 的特定实例的项：</span><span class="sxs-lookup"><span data-stu-id="006ff-114">For example, the following URI returns an entry for a specific instance of the Customer entity type that has a key value of `ALFKI`:</span></span>  
  
<https://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')>
  
 <span data-ttu-id="006ff-115">也可以对实体实例的基元属性和复杂属性进行单独寻址。</span><span class="sxs-lookup"><span data-stu-id="006ff-115">Primitive and complex properties of an entity instance can also be individually addressed.</span></span> <span data-ttu-id="006ff-116">例如，下面的 URI 返回一个包含特定客户的 `ContactName` 属性值的 XML 元素：</span><span class="sxs-lookup"><span data-stu-id="006ff-116">For example, the following URI returns an XML element that contains the `ContactName` property value for a specific Customer:</span></span>  
  
<https://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/ContactName>
  
 <span data-ttu-id="006ff-117">如果在上面的 URI 中包括 `$value` 终结点，则只在响应消息中返回基元属性的值。</span><span class="sxs-lookup"><span data-stu-id="006ff-117">When you include the `$value` endpoint in the previous URI, only the value of the primitive property is returned in the response message.</span></span> <span data-ttu-id="006ff-118">下面的示例只返回字符串“Maria Anders”，而不返回 XML 元素：</span><span class="sxs-lookup"><span data-stu-id="006ff-118">The following example returns only the string "Maria Anders" without the XML element:</span></span>  
  
<https://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/ContactName/$value>
  
 <span data-ttu-id="006ff-119">实体之间的关系在数据模型中由关联定义。</span><span class="sxs-lookup"><span data-stu-id="006ff-119">Relationships between entities are defined in the data model by associations.</span></span> <span data-ttu-id="006ff-120">通过这些关联，可以使用实体实例的导航属性对相关实体进行寻址。</span><span class="sxs-lookup"><span data-stu-id="006ff-120">These associations enable you to address related entities by using navigation properties of an entity instance.</span></span> <span data-ttu-id="006ff-121">对于多对一的关系，导航属性可返回单个相关实体；对于一对多的关系，导航属性可返回一组相关实体。</span><span class="sxs-lookup"><span data-stu-id="006ff-121">A navigation property can return either a single related entity, in the case of a many-to-one relationship, or a set of related entities, in the case of a one-to-many relationship.</span></span> <span data-ttu-id="006ff-122">例如，下面的 URI 返回一个作为与特定客户相关的所有订单集的源：</span><span class="sxs-lookup"><span data-stu-id="006ff-122">For example, the following URI returns a feed that is the set of all the Orders that are related to a specific Customer:</span></span>  
  
<https://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders>
  
 <span data-ttu-id="006ff-123">通常为双向的关系由一对导航属性表示。</span><span class="sxs-lookup"><span data-stu-id="006ff-123">Relationships, which are usually bi-directional, are represented by a pair of navigation properties.</span></span> <span data-ttu-id="006ff-124">作为对前一示例中所示的关系的反转，下面的 URI 返回对特定 Order 实体所属的 Customer 实体的引用：</span><span class="sxs-lookup"><span data-stu-id="006ff-124">As the reverse of the relationship shown in the previous example, the following URI returns a reference to the Customer entity to which a specific Order entity belongs:</span></span>  
  
<https://services.odata.org/Northwind/Northwind.svc/Orders(10643)/Customer>
  
 <span data-ttu-id="006ff-125">OData 还允许您根据查询表达式的结果来对资源进行寻址。</span><span class="sxs-lookup"><span data-stu-id="006ff-125">OData also enables you to address resources based on the results of query expressions.</span></span> <span data-ttu-id="006ff-126">这样，可以基于计算的表达式对资源集进行筛选。</span><span class="sxs-lookup"><span data-stu-id="006ff-126">This makes it possible to filter sets of resources based on an evaluated expression.</span></span> <span data-ttu-id="006ff-127">例如，下面的 URI 对资源进行筛选以仅返回指定客户自 1997 年 9 月 22 日起已发货的订单：</span><span class="sxs-lookup"><span data-stu-id="006ff-127">For example, the following URI filters the resources to return only the Orders for the specified Customer that have shipped since September 22, 1997:</span></span>  
  
`https://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders?$filter=ShippedDate gt datetime'1997-09-22T00:00:00'`
  
 <span data-ttu-id="006ff-128">有关详细信息，请参阅 [OData： URI 约定](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/)。</span><span class="sxs-lookup"><span data-stu-id="006ff-128">For more information, see [OData: URI Conventions](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/).</span></span>
  
## <a name="system-query-options"></a><span data-ttu-id="006ff-129">系统查询选项</span><span class="sxs-lookup"><span data-stu-id="006ff-129">System Query Options</span></span>  

 <span data-ttu-id="006ff-130">OData 定义一组系统查询选项，这些选项可用于对资源执行传统的查询操作，如筛选、排序和分页。</span><span class="sxs-lookup"><span data-stu-id="006ff-130">OData defines a set of system query options that you can use to perform traditional query operations against resources, such as filtering, sorting, and paging.</span></span> <span data-ttu-id="006ff-131">例如，下面的 URI 返回所有实体的集 `Order` ，以及相关 `Order_Detail` 实体（不是以结尾的邮政编码） `100` ：</span><span class="sxs-lookup"><span data-stu-id="006ff-131">For example, the following URI returns the set of all the `Order` entities, along with related `Order_Detail` entities, the postal codes of which do not end in `100`:</span></span>  
  
`https://services.odata.org/Northwind/Northwind.svc/Orders?$filter=not endswith(ShipPostalCode,'100')&$expand=Order_Details&$orderby=ShipCity`
  
 <span data-ttu-id="006ff-132">返回源中的各项还按订单的 ShipCity 属性值进行排序。</span><span class="sxs-lookup"><span data-stu-id="006ff-132">The entries in the returned feed are also ordered by the value of the ShipCity property of the orders.</span></span>  
  
 <span data-ttu-id="006ff-133">WCF Data Services 支持以下 OData 系统查询选项：</span><span class="sxs-lookup"><span data-stu-id="006ff-133">WCF Data Services supports the following OData system query options:</span></span>  
  
|<span data-ttu-id="006ff-134">查询选项</span><span class="sxs-lookup"><span data-stu-id="006ff-134">Query Option</span></span>|<span data-ttu-id="006ff-135">说明</span><span class="sxs-lookup"><span data-stu-id="006ff-135">Description</span></span>|  
|------------------|-----------------|  
|`$orderby`|<span data-ttu-id="006ff-136">定义用于返回的源中的实体的默认排序顺序。</span><span class="sxs-lookup"><span data-stu-id="006ff-136">Defines a default sort order for entities in the returned feed.</span></span> <span data-ttu-id="006ff-137">下面的查询按市/县对返回的客户源进行排序：</span><span class="sxs-lookup"><span data-stu-id="006ff-137">The following query orders the returned customers feed by county and city:</span></span><br /><br /> `https://services.odata.org/Northwind/Northwind.svc/Customers?$orderby=Country,City>`|  
|`$top`|<span data-ttu-id="006ff-138">指定要包括在返回的源中的实体数。</span><span class="sxs-lookup"><span data-stu-id="006ff-138">Specifies the number of entities to include in the returned feed.</span></span> <span data-ttu-id="006ff-139">下面的示例跳过前 10 个客户，然后返回接下来的 10 个客户：</span><span class="sxs-lookup"><span data-stu-id="006ff-139">The following example skips the first 10 customers and then returns the next 10:</span></span><br /><br /> `https://services.odata.org/Northwind/Northwind.svc/Customers?$skip=10&$top=10`|  
|`$skip`|<span data-ttu-id="006ff-140">指定开始在源中返回实体前要跳过的实体数。</span><span class="sxs-lookup"><span data-stu-id="006ff-140">Specifies the number of entities to skip before starting to return entities in the feed.</span></span> <span data-ttu-id="006ff-141">下面的示例跳过前 10 个客户，然后返回接下来的 10 个客户：</span><span class="sxs-lookup"><span data-stu-id="006ff-141">The following example skips the first 10 customers and then returns the next 10:</span></span><br /><br /> `https://services.odata.org/Northwind/Northwind.svc/Customers?$skip=10&$top=10`|  
|`$filter`|<span data-ttu-id="006ff-142">定义一个基于特定条件对源中返回的实体进行筛选的表达式。</span><span class="sxs-lookup"><span data-stu-id="006ff-142">Defines an expression that filters the entities returned in the feed based on specific criteria.</span></span> <span data-ttu-id="006ff-143">此查询选项支持一组用于计算筛选表达式的逻辑比较运算符、算术运算符和预定义查询函数。</span><span class="sxs-lookup"><span data-stu-id="006ff-143">This query option supports a set of logical comparison operators, arithmetic operators, and predefined query functions that are used to evaluate the filter expression.</span></span> <span data-ttu-id="006ff-144">下面示例返回邮政编码尾号不是 100 的所有订单：</span><span class="sxs-lookup"><span data-stu-id="006ff-144">The following example returns all orders the postal codes of which do not end in 100:</span></span><br /><br /> `https://services.odata.org/Northwind/Northwind.svc/Orders?$filter=not endswith(ShipPostalCode,'100')`|  
|`$expand`|<span data-ttu-id="006ff-145">指定由查询返回哪些相关实体。</span><span class="sxs-lookup"><span data-stu-id="006ff-145">Specifies which related entities are returned by the query.</span></span> <span data-ttu-id="006ff-146">相关实体将作为源或内联项与查询返回的实体包含在一起。</span><span class="sxs-lookup"><span data-stu-id="006ff-146">Related entities are included as either a feed or an entry inline with the entity returned by the query.</span></span> <span data-ttu-id="006ff-147">下面的示例返回客户“ALFKI”的订单以及每个订单的项目详细信息：</span><span class="sxs-lookup"><span data-stu-id="006ff-147">The following example returns the order for the customer 'ALFKI' along with the item details for each order:</span></span><br /><br /> `https://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders?$expand=Order_Details`|  
|`$select`|<span data-ttu-id="006ff-148">指定一个投影，用于定义在投影中返回的实体的属性。</span><span class="sxs-lookup"><span data-stu-id="006ff-148">Specifies a projection that defines the properties of the entity are returned in the projection.</span></span> <span data-ttu-id="006ff-149">默认情况下，在源中返回实体的所有属性。</span><span class="sxs-lookup"><span data-stu-id="006ff-149">By default, all properties of an entity are returned in a feed.</span></span> <span data-ttu-id="006ff-150">下面的查询仅返回 `Customer` 实体的三个属性：</span><span class="sxs-lookup"><span data-stu-id="006ff-150">The following query returns only three properties of the `Customer` entity:</span></span><br /><br /> `https://services.odata.org/Northwind/Northwind.svc/Customers?$select=CustomerID,CompanyName,City`|  
|`$inlinecount`|<span data-ttu-id="006ff-151">请求在源中包括源中返回的实体数的计数。</span><span class="sxs-lookup"><span data-stu-id="006ff-151">Requests that a count of the number of entities returned in the feed be included with the feed.</span></span>|  
  
## <a name="addressing-relationships"></a><span data-ttu-id="006ff-152">对关系进行寻址</span><span class="sxs-lookup"><span data-stu-id="006ff-152">Addressing Relationships</span></span>  

 <span data-ttu-id="006ff-153">除了对实体集和实体实例进行寻址以外，OData 还允许对表示实体之间的关系的关联进行寻址。</span><span class="sxs-lookup"><span data-stu-id="006ff-153">In addition to addressing entity sets and entity instances, OData also enables you to address the associations that represent relationships between entities.</span></span> <span data-ttu-id="006ff-154">若要创建或更改两个实体实例（例如与 Northwind 示例数据库中指定订单相关的发货方）之间的关系，必须使用此功能。</span><span class="sxs-lookup"><span data-stu-id="006ff-154">This functionality is required to be able to create or change a relationship between two entity instances, such as the shipper that is related to a given order in the Northwind sample database.</span></span> <span data-ttu-id="006ff-155">OData 支持 `$link` 操作员专门对实体间的关联进行寻址。</span><span class="sxs-lookup"><span data-stu-id="006ff-155">OData supports a `$link` operator to specifically address the associations between entities.</span></span> <span data-ttu-id="006ff-156">例如，在 HTTP PUT 请求消息中指定下面的 URI 可将指定订单的发货方更改为新发货方。</span><span class="sxs-lookup"><span data-stu-id="006ff-156">For example, the following URI is specified in an HTTP PUT request message to change the shipper for the specified order to a new shipper.</span></span>  
  
`https://services.odata.org/Northwind/Northwind.svc/Orders(10643)/$links/Shipper`
  
 <span data-ttu-id="006ff-157">有关详细信息，请参阅 `3.2. Addressing Links between Entries` [ODATA： URI 约定](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/)部分。</span><span class="sxs-lookup"><span data-stu-id="006ff-157">For more information, see section `3.2. Addressing Links between Entries` at [OData: URI Conventions](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/).</span></span>
  
## <a name="consuming-the-returned-feed"></a><span data-ttu-id="006ff-158">使用返回的源</span><span class="sxs-lookup"><span data-stu-id="006ff-158">Consuming the Returned Feed</span></span>  

 <span data-ttu-id="006ff-159">OData 资源的 URI 使你可以对服务公开的实体数据进行寻址。</span><span class="sxs-lookup"><span data-stu-id="006ff-159">The URI of an OData resource enables you to address entity data exposed by the service.</span></span> <span data-ttu-id="006ff-160">在 Web 浏览器的 "地址" 字段中输入 URI 时，将返回所请求资源的 OData 源表示形式。</span><span class="sxs-lookup"><span data-stu-id="006ff-160">When you enter a URI into the address field of a Web browser, a OData feed representation of the requested resource is returned.</span></span> <span data-ttu-id="006ff-161">有关详细信息，请参阅 [WCF Data Services 快速入门](quickstart-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="006ff-161">For more information, see the [WCF Data Services Quickstart](quickstart-wcf-data-services.md).</span></span> <span data-ttu-id="006ff-162">尽管可以使用 Web 浏览器测试某个数据服务资源能否返回预期的数据，但是生产数据服务（这些服务也可创建、更新和删除数据）通常由应用程序代码或网页中的脚本编写语言访问。</span><span class="sxs-lookup"><span data-stu-id="006ff-162">Although a Web browser may be useful for testing that a data service resource returns the expected data, production data services that can also create, update, and delete data are generally accessed by application code or scripting languages in a Web page.</span></span> <span data-ttu-id="006ff-163">有关详细信息，请参阅 [在客户端应用程序中使用数据服务](using-a-data-service-in-a-client-application-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="006ff-163">For more information, see [Using a Data Service in a Client Application](using-a-data-service-in-a-client-application-wcf-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="006ff-164">请参阅</span><span class="sxs-lookup"><span data-stu-id="006ff-164">See also</span></span>

- [<span data-ttu-id="006ff-165">Open Data Protocol 网站</span><span class="sxs-lookup"><span data-stu-id="006ff-165">Open Data Protocol Web site</span></span>](https://www.odata.org/)
