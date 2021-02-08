---
description: '了解详细信息：反射提供程序 (WCF Data Services) '
title: 反射提供程序（WCF 数据服务）
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: ef5ba300-6d7c-455e-a7bd-d0cc6d211ad4
ms.openlocfilehash: e09c9a86bb940681d8de24f5082919aea897795d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794918"
---
# <a name="reflection-provider-wcf-data-services"></a><span data-ttu-id="24c1e-103">反射提供程序（WCF 数据服务）</span><span class="sxs-lookup"><span data-stu-id="24c1e-103">Reflection Provider (WCF Data Services)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="24c1e-104">除了通过实体框架公开数据模型中的数据以外，WCF Data Services 可以公开未在基于实体的模型中严格定义的数据。</span><span class="sxs-lookup"><span data-stu-id="24c1e-104">In addition to exposing data from a data model through the Entity Framework, WCF Data Services can expose data that is not strictly defined in an entity-based model.</span></span> <span data-ttu-id="24c1e-105">反射提供程序公开类中的数据，这些类返回实现 <xref:System.Linq.IQueryable%601> 接口的类型。</span><span class="sxs-lookup"><span data-stu-id="24c1e-105">The reflection provider exposes data in classes that return types that implement the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="24c1e-106">WCF Data Services 使用反射推断这些类的数据模型，并且可以将针对资源的基于地址的查询转换为针对已公开类型的基于 LINQ) 的查询的语言集成 (查询 <xref:System.Linq.IQueryable%601> 。</span><span class="sxs-lookup"><span data-stu-id="24c1e-106">WCF Data Services uses reflection to infer a data model for these classes and can translate address-based queries against resources into language integrated query (LINQ)-based queries against the exposed <xref:System.Linq.IQueryable%601> types.</span></span>

> [!NOTE]
> <span data-ttu-id="24c1e-107">可使用 <xref:System.Linq.Queryable.AsQueryable%2A> 方法从实现 <xref:System.Linq.IQueryable%601> 接口的任何类返回 <xref:System.Collections.Generic.IEnumerable%601> 接口。</span><span class="sxs-lookup"><span data-stu-id="24c1e-107">You can use the <xref:System.Linq.Queryable.AsQueryable%2A> method to return an <xref:System.Linq.IQueryable%601> interface from any class that implements the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="24c1e-108">这允许将大多数泛型集合类型用作数据服务的数据源。</span><span class="sxs-lookup"><span data-stu-id="24c1e-108">This enables most generic collection types to be used as a data source for your data service.</span></span>

<span data-ttu-id="24c1e-109">反射提供程序支持类型层次结构。</span><span class="sxs-lookup"><span data-stu-id="24c1e-109">The reflection provider supports type hierarchies.</span></span> <span data-ttu-id="24c1e-110">有关详细信息，请参阅 [如何：使用反射提供程序创建数据服务](create-a-data-service-using-rp-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="24c1e-110">For more information, see [How to: Create a Data Service Using the Reflection Provider](create-a-data-service-using-rp-wcf-data-services.md).</span></span>

## <a name="inferring-the-data-model"></a><span data-ttu-id="24c1e-111">推断数据模型</span><span class="sxs-lookup"><span data-stu-id="24c1e-111">Inferring the Data Model</span></span>

<span data-ttu-id="24c1e-112">创建数据服务时，提供程序通过使用反射来推断数据模型。</span><span class="sxs-lookup"><span data-stu-id="24c1e-112">When you create the data service, the provider infers the data model by using reflection.</span></span> <span data-ttu-id="24c1e-113">以下列表显示了反射提供程序如何推断数据模型：</span><span class="sxs-lookup"><span data-stu-id="24c1e-113">The following list shows how the reflection provider infers the data model:</span></span>

- <span data-ttu-id="24c1e-114">实体容器 – 将数据作为可返回 <xref:System.Linq.IQueryable%601> 实例的属性公开的类。</span><span class="sxs-lookup"><span data-stu-id="24c1e-114">Entity container - the class that exposes the data as properties that return an <xref:System.Linq.IQueryable%601> instance.</span></span> <span data-ttu-id="24c1e-115">对基于反射的数据模型进行寻址时，实体容器表示服务的根。</span><span class="sxs-lookup"><span data-stu-id="24c1e-115">When you address a reflection-based data model, the entity container represents the root of the service.</span></span> <span data-ttu-id="24c1e-116">对给定命名空间仅支持一个实体容器类。</span><span class="sxs-lookup"><span data-stu-id="24c1e-116">Only one entity container class is supported for a given namespace.</span></span>

- <span data-ttu-id="24c1e-117">实体集 – 返回 <xref:System.Linq.IQueryable%601> 实例的属性视为实体集。</span><span class="sxs-lookup"><span data-stu-id="24c1e-117">Entity sets - properties that return <xref:System.Linq.IQueryable%601> instances are treated as entity sets.</span></span> <span data-ttu-id="24c1e-118">在查询中，将把实体集作为资源直接进行寻址。</span><span class="sxs-lookup"><span data-stu-id="24c1e-118">Entity sets are addressed directly as resources in the query.</span></span> <span data-ttu-id="24c1e-119">实体容器中只有一个属性才能返回给定类型的 <xref:System.Linq.IQueryable%601> 实例。</span><span class="sxs-lookup"><span data-stu-id="24c1e-119">Only one property on the entity container can return an <xref:System.Linq.IQueryable%601> instance of a given type.</span></span>

- <span data-ttu-id="24c1e-120">实体类型 – 实体集返回的 `T` 的类型 <xref:System.Linq.IQueryable%601>。</span><span class="sxs-lookup"><span data-stu-id="24c1e-120">Entity types - the type `T` of the <xref:System.Linq.IQueryable%601> that the entity set returns.</span></span> <span data-ttu-id="24c1e-121">反射提供程序将作为继承层次结构一部分的类转换为等效的实体类型层次结构。</span><span class="sxs-lookup"><span data-stu-id="24c1e-121">Classes that are part of an inheritance hierarchy are translated by the reflection provider into an equivalent entity type hierarchy.</span></span>

- <span data-ttu-id="24c1e-122">实体键 – 作为实体类型的每个数据类必须具有一个键属性。</span><span class="sxs-lookup"><span data-stu-id="24c1e-122">Entity keys - each data class that is an entity type must have a key property.</span></span> <span data-ttu-id="24c1e-123">该属性具有 <xref:System.Data.Services.Common.DataServiceKeyAttribute> 特性 (`[DataServiceKeyAttribute]`)。</span><span class="sxs-lookup"><span data-stu-id="24c1e-123">This property is attributed with the <xref:System.Data.Services.Common.DataServiceKeyAttribute> attribute (`[DataServiceKeyAttribute]`).</span></span>

    > [!NOTE]
    > <span data-ttu-id="24c1e-124">您应将 <xref:System.Data.Services.Common.DataServiceKeyAttribute> 特性仅应用于可以用来唯一标识实体类型的实例的属性。</span><span class="sxs-lookup"><span data-stu-id="24c1e-124">You should only apply the <xref:System.Data.Services.Common.DataServiceKeyAttribute> attribute to a property that can be used to uniquely identify an instance of the entity type.</span></span> <span data-ttu-id="24c1e-125">当应用于导航属性时忽略此特性。</span><span class="sxs-lookup"><span data-stu-id="24c1e-125">This attribute is ignored when applied to a navigation property.</span></span>

- <span data-ttu-id="24c1e-126">实体类型属性 – 与实体键不同的是，反射提供程序按如下方式处理作为实体类型的类的可访问非索引器属性：</span><span class="sxs-lookup"><span data-stu-id="24c1e-126">Entity type properties - other than the entity key, the reflection provider treats the accessible, non-indexer properties of a class that is an entity type as follows:</span></span>

  - <span data-ttu-id="24c1e-127">如果属性返回基元类型，则假定该属性为实体类型的属性。</span><span class="sxs-lookup"><span data-stu-id="24c1e-127">If the property returns a primitive type, then the property is assumed to be a property of an entity type.</span></span>

  - <span data-ttu-id="24c1e-128">如果属性返回的类型同时也是实体类型，则假定该属性为导航属性，表示多对一或一对一关系的“一”端。</span><span class="sxs-lookup"><span data-stu-id="24c1e-128">If the property returns a type that is also an entity type, then the property is assumed to be a navigation property that represents the "one" end of a many-to-one or one-to-one relationship.</span></span>

  - <span data-ttu-id="24c1e-129">如果属性返回实体类型的 <xref:System.Collections.Generic.IEnumerable%601>，则假定该属性为导航属性，表示一对多或多对多关系的“多”端。</span><span class="sxs-lookup"><span data-stu-id="24c1e-129">If the property returns an <xref:System.Collections.Generic.IEnumerable%601> of an entity type, then the property is assumed to be a navigation property that represents the "many" end of a one-to-many or many-to-many relationship.</span></span>

  - <span data-ttu-id="24c1e-130">如果属性的返回类型为一个值类型，则该属性表示一个复杂类型。</span><span class="sxs-lookup"><span data-stu-id="24c1e-130">If the return type of the property is a value type, then the property represents a complex type.</span></span>

> [!NOTE]
> <span data-ttu-id="24c1e-131">与基于实体关系模型的数据模型不同，基于反射提供程序的模型不了解关系数据。</span><span class="sxs-lookup"><span data-stu-id="24c1e-131">Unlike a data model that is based on the entity-relational model, models that are based on the reflection provider do not understand relational data.</span></span> <span data-ttu-id="24c1e-132">应使用实体框架通过 WCF Data Services 公开关系数据。</span><span class="sxs-lookup"><span data-stu-id="24c1e-132">You should use the Entity Framework to expose relational data through WCF Data Services.</span></span>

## <a name="data-type-mapping"></a><span data-ttu-id="24c1e-133">数据类型映射</span><span class="sxs-lookup"><span data-stu-id="24c1e-133">Data Type Mapping</span></span>

<span data-ttu-id="24c1e-134">根据 .NET Framework 类推断数据模型时，数据模型中的基元类型按如下方式映射到 .NET Framework 数据类型：</span><span class="sxs-lookup"><span data-stu-id="24c1e-134">When a data model is inferred from .NET Framework classes, the primitive types in the data model are mapped to .NET Framework data types as follows:</span></span>

|<span data-ttu-id="24c1e-135">.NET framework 数据类型</span><span class="sxs-lookup"><span data-stu-id="24c1e-135">.NET Framework data type</span></span>|<span data-ttu-id="24c1e-136">数据模型类型</span><span class="sxs-lookup"><span data-stu-id="24c1e-136">Data model type</span></span>|
|------------------------------|---------------------|
|<span data-ttu-id="24c1e-137"><xref:System.Byte> `[]`</span><span class="sxs-lookup"><span data-stu-id="24c1e-137"><xref:System.Byte> `[]`</span></span>|`Edm.Binary`|
|<xref:System.Boolean>|`Edm.Boolean`|
|<xref:System.Byte>|`Edm.Byte`|
|<xref:System.DateTime>|`Edm.DateTime`|
|<xref:System.Decimal>|`Edm.Decimal`|
|<xref:System.Double>|`Edm.Double`|
|<xref:System.Guid>|`Edm.Guid`|
|<xref:System.Int16>|`Edm.Int16`|
|<xref:System.Int32>|`Edm.Int32`|
|<xref:System.Int64>|`Edm.Int64`|
|<xref:System.SByte>|`Edm.SByte`|
|<xref:System.Single>|`Edm.Single`|
|<xref:System.String>|`Edm.String`|

> [!NOTE]
> <span data-ttu-id="24c1e-138">.NET Framework 可以为 null 的值类型会映射到与不能分配 null 的相应值类型相同的数据模型类型。</span><span class="sxs-lookup"><span data-stu-id="24c1e-138">.NET Framework nullable value types are mapped to the same data model types as the corresponding value types that cannot be assigned a null.</span></span>

## <a name="enabling-updates-in-the-data-model"></a><span data-ttu-id="24c1e-139">在数据模型中启用更新</span><span class="sxs-lookup"><span data-stu-id="24c1e-139">Enabling Updates in the Data Model</span></span>

<span data-ttu-id="24c1e-140">为了对通过此类数据模型公开的数据进行更新，反射提供程序定义了一个 <xref:System.Data.Services.IUpdatable> 接口。</span><span class="sxs-lookup"><span data-stu-id="24c1e-140">To allow updates to data that is exposed through this kind of data model, the reflection provider defines an <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="24c1e-141">该接口指示数据服务如何保持对公开类型的更新。</span><span class="sxs-lookup"><span data-stu-id="24c1e-141">This interface instructs the data service on how to persist updates to the exposed types.</span></span> <span data-ttu-id="24c1e-142">若要启用对数据模型定义的资源的更新，实体容器类必须实现 <xref:System.Data.Services.IUpdatable> 接口。</span><span class="sxs-lookup"><span data-stu-id="24c1e-142">To enable updates to resources that are defined by the data model, the entity container class must implement the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="24c1e-143">有关接口实现的示例 <xref:System.Data.Services.IUpdatable> ，请参阅 [如何：使用 LINQ to SQL 数据源创建数据服务](create-a-data-service-using-linq-to-sql-wcf.md)。</span><span class="sxs-lookup"><span data-stu-id="24c1e-143">For an example of an implementation of the <xref:System.Data.Services.IUpdatable> interface, see [How to: Create a Data Service Using a LINQ to SQL Data Source](create-a-data-service-using-linq-to-sql-wcf.md).</span></span>

<span data-ttu-id="24c1e-144"><xref:System.Data.Services.IUpdatable> 接口要求实现以下成员，以便可使用反射提供程序将更新传播到数据源：</span><span class="sxs-lookup"><span data-stu-id="24c1e-144">The <xref:System.Data.Services.IUpdatable> interface requires that the following members be implemented so that updates can be propagated to the data source by using the reflection provider:</span></span>

|<span data-ttu-id="24c1e-145">成员</span><span class="sxs-lookup"><span data-stu-id="24c1e-145">Member</span></span>|<span data-ttu-id="24c1e-146">说明</span><span class="sxs-lookup"><span data-stu-id="24c1e-146">Description</span></span>|
|------------|-----------------|
|<xref:System.Data.Services.IUpdatable.AddReferenceToCollection%2A>|<span data-ttu-id="24c1e-147">提供将对象添加到从导航属性访问的相关对象集合的功能。</span><span class="sxs-lookup"><span data-stu-id="24c1e-147">Provides the functionality to add an object to a collection of related objects that are accessed from a navigation property.</span></span>|
|<xref:System.Data.Services.IUpdatable.ClearChanges%2A>|<span data-ttu-id="24c1e-148">提供取消挂起的数据更改的功能。</span><span class="sxs-lookup"><span data-stu-id="24c1e-148">Provides the functionality that cancels pending changes to the data.</span></span>|
|<xref:System.Data.Services.IUpdatable.CreateResource%2A>|<span data-ttu-id="24c1e-149">提供在指定容器中创建新资源的功能。</span><span class="sxs-lookup"><span data-stu-id="24c1e-149">Provides the functionality to create a new resource in the specified container.</span></span>|
|<xref:System.Data.Services.IUpdatable.DeleteResource%2A>|<span data-ttu-id="24c1e-150">提供删除资源的功能。</span><span class="sxs-lookup"><span data-stu-id="24c1e-150">Provides the functionality to delete a resource.</span></span>|
|<xref:System.Data.Services.IUpdatable.GetResource%2A>|<span data-ttu-id="24c1e-151">提供检索由特定查询和类型名称标识的资源的功能。</span><span class="sxs-lookup"><span data-stu-id="24c1e-151">Provides the functionality to retrieve a resource that is identified by a specific query and type name.</span></span>|
|<xref:System.Data.Services.IUpdatable.GetValue%2A>|<span data-ttu-id="24c1e-152">提供返回资源的属性值的功能。</span><span class="sxs-lookup"><span data-stu-id="24c1e-152">Provides the functionality to return the value of a property of a resource.</span></span>|
|<xref:System.Data.Services.IUpdatable.RemoveReferenceFromCollection%2A>|<span data-ttu-id="24c1e-153">提供从通过导航属性访问的相关对象集合中移除某一对象的功能。</span><span class="sxs-lookup"><span data-stu-id="24c1e-153">Provides the functionality to remove an object to a collection of related objects accessed from a navigation property.</span></span>|
|<xref:System.Data.Services.IUpdatable.ResetResource%2A>|<span data-ttu-id="24c1e-154">提供更新指定资源的功能。</span><span class="sxs-lookup"><span data-stu-id="24c1e-154">Provides the functionality to update a specified resource.</span></span>|
|<xref:System.Data.Services.IUpdatable.ResolveResource%2A>|<span data-ttu-id="24c1e-155">提供返回由特定对象实例表示的资源的功能。</span><span class="sxs-lookup"><span data-stu-id="24c1e-155">Provides the functionality to return the resource that is represented by a specific object instance.</span></span>|
|<xref:System.Data.Services.IUpdatable.SaveChanges%2A>|<span data-ttu-id="24c1e-156">提供保存挂起的所有更改的功能。</span><span class="sxs-lookup"><span data-stu-id="24c1e-156">Provides the functionality to save all pending changes.</span></span>|
|<xref:System.Data.Services.IUpdatable.SetReference%2A>|<span data-ttu-id="24c1e-157">提供通过使用导航属性来设置相关对象引用的功能。</span><span class="sxs-lookup"><span data-stu-id="24c1e-157">Provides the functionality to set a related object reference by using a navigation property.</span></span>|
|<xref:System.Data.Services.IUpdatable.SetValue%2A>|<span data-ttu-id="24c1e-158">提供设置资源的属性值的功能。</span><span class="sxs-lookup"><span data-stu-id="24c1e-158">Provides the functionality to set the value of the property of a resource.</span></span>|

## <a name="handling-concurrency"></a><span data-ttu-id="24c1e-159">处理并发</span><span class="sxs-lookup"><span data-stu-id="24c1e-159">Handling Concurrency</span></span>

<span data-ttu-id="24c1e-160">通过使你能够为实体定义并发标记，WCF Data Services 支持开放式并发模型。</span><span class="sxs-lookup"><span data-stu-id="24c1e-160">WCF Data Services supports an optimistic concurrency model by enabling you to define a concurrency token for an entity.</span></span> <span data-ttu-id="24c1e-161">这样一个包含一个或多个实体属性的并发标记由数据服务用来确定，正在请求、更新或删除的数据中是否发生了更改。</span><span class="sxs-lookup"><span data-stu-id="24c1e-161">This concurrency token, which includes one or more properties of the entity, is used by the data service to determine whether a change has occurred in the data that is being requested, updated, or deleted.</span></span> <span data-ttu-id="24c1e-162">如果从请求的 eTag 中获取的标记值与实体的当前值不相同，则数据服务将引发异常。</span><span class="sxs-lookup"><span data-stu-id="24c1e-162">When token values obtained from the eTag in the request differ from the current values of the entity, an exception is raised by the data service.</span></span> <span data-ttu-id="24c1e-163">将 <xref:System.Data.Services.ETagAttribute> 应用于某个实体类型可在反射提供程序中定义并发标记。</span><span class="sxs-lookup"><span data-stu-id="24c1e-163">The <xref:System.Data.Services.ETagAttribute> is applied to an entity type to define a concurrency token in the reflection provider.</span></span> <span data-ttu-id="24c1e-164">并发标记不能包含键属性或导航属性。</span><span class="sxs-lookup"><span data-stu-id="24c1e-164">The concurrency token cannot include a key property or a navigation property.</span></span> <span data-ttu-id="24c1e-165">有关详细信息，请参阅 [更新数据服务](updating-the-data-service-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="24c1e-165">For more information, see [Updating the Data Service](updating-the-data-service-wcf-data-services.md).</span></span>

## <a name="using-linq-to-sql-with-the-reflection-provider"></a><span data-ttu-id="24c1e-166">配合使用 LINQ to SQL 和反射提供程序</span><span class="sxs-lookup"><span data-stu-id="24c1e-166">Using LINQ to SQL with the Reflection Provider</span></span>

<span data-ttu-id="24c1e-167">由于默认情况下支持实体框架，因此它是建议用于将关系数据与 WCF Data Services 结合使用的数据提供程序。</span><span class="sxs-lookup"><span data-stu-id="24c1e-167">Because the Entity Framework is natively supported by default, it is the recommended data provider for using relational data with WCF Data Services.</span></span> <span data-ttu-id="24c1e-168">但是，可以使用反射提供程序来配合使用 LINQ to SQL 类和数据服务。</span><span class="sxs-lookup"><span data-stu-id="24c1e-168">However, you can use the reflection provider to use LINQ to SQL classes with a data service.</span></span> <span data-ttu-id="24c1e-169"><xref:System.Data.Linq.Table%601> <xref:System.Data.Linq.DataContext> LINQ to SQL 对象关系设计器 (O/R 设计器生成的方法返回的结果集) 实现 <xref:System.Linq.IQueryable%601> 接口。</span><span class="sxs-lookup"><span data-stu-id="24c1e-169">The <xref:System.Data.Linq.Table%601> result sets that are returned by methods on the <xref:System.Data.Linq.DataContext> generated by the LINQ to SQL Object Relational Designer (O/R Designer) implement the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="24c1e-170">这样，反射提供程序便可以通过使用生成的 LINQ to SQL 类从 SQL Server 访问这些方法和返回实体数据。</span><span class="sxs-lookup"><span data-stu-id="24c1e-170">This enables the reflection provider to access these methods and return entity data from SQL Server by using the generated LINQ to SQL classes.</span></span> <span data-ttu-id="24c1e-171">但是，由于 LINQ to SQL 不会实现 <xref:System.Data.Services.IUpdatable> 接口，因此需要添加一个可扩展现有 <xref:System.Data.Linq.DataContext> 分部类的分部类才能添加 <xref:System.Data.Services.IUpdatable> 实现。</span><span class="sxs-lookup"><span data-stu-id="24c1e-171">However, because LINQ to SQL does not implement the <xref:System.Data.Services.IUpdatable> interface, you need to add a partial class that extends the existing <xref:System.Data.Linq.DataContext> partial class to add the <xref:System.Data.Services.IUpdatable> implementation.</span></span> <span data-ttu-id="24c1e-172">有关详细信息，请参阅 [如何：使用 LINQ to SQL 数据源创建数据服务](create-a-data-service-using-linq-to-sql-wcf.md)。</span><span class="sxs-lookup"><span data-stu-id="24c1e-172">For more information, see [How to: Create a Data Service Using a LINQ to SQL Data Source](create-a-data-service-using-linq-to-sql-wcf.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="24c1e-173">请参阅</span><span class="sxs-lookup"><span data-stu-id="24c1e-173">See also</span></span>

- [<span data-ttu-id="24c1e-174">数据服务提供程序</span><span class="sxs-lookup"><span data-stu-id="24c1e-174">Data Services Providers</span></span>](data-services-providers-wcf-data-services.md)
