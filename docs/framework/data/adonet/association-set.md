---
description: 了解详细信息：关联集
title: Association Set — 关联集
ms.date: 03/30/2017
ms.assetid: a65247b6-ce59-44ea-974c-14ae20a7995f
ms.openlocfilehash: aeddf3e898aecc2b283a941e844a6dbe810357f5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697577"
---
# <a name="association-set"></a><span data-ttu-id="26157-103">Association Set — 关联集</span><span class="sxs-lookup"><span data-stu-id="26157-103">association set</span></span>

<span data-ttu-id="26157-104">*关联集* 是同一类型的 [关联](association-type.md)实例的逻辑容器。</span><span class="sxs-lookup"><span data-stu-id="26157-104">An *association set* is a logical container for [association](association-type.md) instances of the same type.</span></span> <span data-ttu-id="26157-105">关联集不是一种数据建模构造，也就是说，它没有描述数据结构或关系。</span><span class="sxs-lookup"><span data-stu-id="26157-105">An association set is not a data modeling construct; that is, it does not describe the structure of data or relationships.</span></span> <span data-ttu-id="26157-106">相反，关联集提供了一种承载或存储环境构造（例如公共语言运行库或 SQL Server 数据库）来分组关联实例，以便可以将它们映射到某个数据存储区。</span><span class="sxs-lookup"><span data-stu-id="26157-106">Instead, an association set provides a construct for a hosting or storage environment (such as the common language runtime or a SQL Server database) to group association instances so that they can be mapped to a data store.</span></span>  
  
 <span data-ttu-id="26157-107">关联集是在实体容器中定义的， [实体容器](entity-container.md)是 [实体集](entity-set.md) 和关联集的逻辑分组。</span><span class="sxs-lookup"><span data-stu-id="26157-107">An association set is defined within an [entity container](entity-container.md), which is a logical grouping of [entity sets](entity-set.md) and association sets.</span></span>  
  
 <span data-ttu-id="26157-108">关联集的定义包含以下信息：</span><span class="sxs-lookup"><span data-stu-id="26157-108">A definition for an association set contains the following information:</span></span>  
  
- <span data-ttu-id="26157-109">关联集名称。</span><span class="sxs-lookup"><span data-stu-id="26157-109">The association set name.</span></span> <span data-ttu-id="26157-110">（必需）</span><span class="sxs-lookup"><span data-stu-id="26157-110">(Required)</span></span>  
  
- <span data-ttu-id="26157-111">要包含其实例的关联。</span><span class="sxs-lookup"><span data-stu-id="26157-111">The association of which it will contain instances.</span></span> <span data-ttu-id="26157-112">（必需）</span><span class="sxs-lookup"><span data-stu-id="26157-112">(Required)</span></span>  
  
- <span data-ttu-id="26157-113">两个 [关联集结束](association-set-end.md)。</span><span class="sxs-lookup"><span data-stu-id="26157-113">Two [association set ends](association-set-end.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="26157-114">示例</span><span class="sxs-lookup"><span data-stu-id="26157-114">Example</span></span>  

 <span data-ttu-id="26157-115">下图显示了一个具有两个关联的概念模型：`PublishedBy` 和 `WrittenBy`。</span><span class="sxs-lookup"><span data-stu-id="26157-115">The diagram below shows a conceptual model with two associations: `PublishedBy`, and `WrittenBy`.</span></span> <span data-ttu-id="26157-116">上图没有传达有关关联集的信息，但下图显示了一个基于此模型的关联集和实体集的示例。</span><span class="sxs-lookup"><span data-stu-id="26157-116">Although information about association sets is not conveyed in the diagram, the next diagram shows an example of association sets and entity sets based on this model.</span></span>  
  
 ![具有三个实体类型的示例模型](./media/association-set/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="26157-118">下面的示例显示了基于上面所示的概念模型的一个关联集 (`PublishedBy`) 和两个实体集（`Books` 和 `Publishers`）。</span><span class="sxs-lookup"><span data-stu-id="26157-118">The following example shows an association set (`PublishedBy`) and two entity sets (`Books` and `Publishers`) based on the conceptual model shown above.</span></span> <span data-ttu-id="26157-119">`Books`实体集中的 Bi 表示 `Book` 运行时实体类型的实例。</span><span class="sxs-lookup"><span data-stu-id="26157-119">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="26157-120">同样，Pj 表示 `Publisher` 实体集中的实例 `Publishers` 。</span><span class="sxs-lookup"><span data-stu-id="26157-120">Similarly, Pj represents a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="26157-121">BiPj 表示 `PublishedBy` 关联集中关联的实例 `PublishedBy` 。</span><span class="sxs-lookup"><span data-stu-id="26157-121">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 ![显示集合示例的屏幕截图。](./media/association-set/sets-example-association.gif)  
  
 <span data-ttu-id="26157-123">[ADO.NET 实体框架](./ef/index.md)使用一种特定于域的语言 (DSL) 称为概念架构定义语言 ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) 来定义概念模型。</span><span class="sxs-lookup"><span data-stu-id="26157-123">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="26157-124">下面的 CSDL 定义了一个实体容器，其中对于上图所示的每个关联都有一个关联集。</span><span class="sxs-lookup"><span data-stu-id="26157-124">The following CSDL defines an entity container with one association set for each association in the diagram above.</span></span> <span data-ttu-id="26157-125">请注意，每个关联集的名称和关联都是使用 XML 特性定义的。</span><span class="sxs-lookup"><span data-stu-id="26157-125">Note that the name and association for each association set are defined using XML attributes.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 <span data-ttu-id="26157-126">只要没有两个关联集共享一个 [关联集端](association-set-end.md)，就可以为每个关联定义多个关联集。</span><span class="sxs-lookup"><span data-stu-id="26157-126">It is possible to define multiple association sets per association, as long as no two association sets share an [association set end](association-set-end.md).</span></span> <span data-ttu-id="26157-127">下面的 CSDL 定义了一个实体容器，其中包含 `WrittenBy` 关联的两个关联集。</span><span class="sxs-lookup"><span data-stu-id="26157-127">The following CSDL defines an entity container with two association sets for the `WrittenBy` association.</span></span> <span data-ttu-id="26157-128">请注意，为 `Book` 和 `Author` 实体类型定义了多个实体集，并且没有关联集共享关联集端。</span><span class="sxs-lookup"><span data-stu-id="26157-128">Notice that multiple entity sets have been defined for the `Book` and `Author` entity types and that no association set shares an association set end.</span></span>  
  
 [!code-xml[EDM_Example_Model#MultipleAssociationSets](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#multipleassociationsets)]  
  
## <a name="see-also"></a><span data-ttu-id="26157-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="26157-129">See also</span></span>

- [<span data-ttu-id="26157-130">实体数据模型关键概念</span><span class="sxs-lookup"><span data-stu-id="26157-130">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="26157-131">实体数据模型</span><span class="sxs-lookup"><span data-stu-id="26157-131">Entity Data Model</span></span>](entity-data-model.md)
- [<span data-ttu-id="26157-132">外键属性</span><span class="sxs-lookup"><span data-stu-id="26157-132">foreign key property</span></span>](foreign-key-property.md)
