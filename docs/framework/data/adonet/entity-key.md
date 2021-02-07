---
description: 了解详细信息：实体键
title: 实体键
ms.date: 03/30/2017
ms.assetid: 0d447a6d-fa7a-4db0-8e7a-fd45e385fca0
ms.openlocfilehash: 588f18a2f76ca11c797b9b2aaab00b090c99e345
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724435"
---
# <a name="entity-key"></a><span data-ttu-id="a1e7c-103">实体键</span><span class="sxs-lookup"><span data-stu-id="a1e7c-103">entity key</span></span>

<span data-ttu-id="a1e7c-104">"*实体键*" 是用于确定标识的 [实体类型](entity-type.md)的 [一个或一组属性。](property.md)</span><span class="sxs-lookup"><span data-stu-id="a1e7c-104">An *entity key* is a [property](property.md) or a set of properties of an [entity type](entity-type.md) that are used to determine identity.</span></span> <span data-ttu-id="a1e7c-105">构成实体键的属性是在设计时选择的。</span><span class="sxs-lookup"><span data-stu-id="a1e7c-105">The properties that make up an entity key are chosen at design time.</span></span> <span data-ttu-id="a1e7c-106">实体键属性的值必须在运行时唯一标识 [实体集中](entity-set.md) 的实体类型实例。</span><span class="sxs-lookup"><span data-stu-id="a1e7c-106">The values of entity key properties must uniquely identify an entity type instance within an [entity set](entity-set.md) at run time.</span></span> <span data-ttu-id="a1e7c-107">在选择构成实体键的属性时应确保实例在实体集中的唯一性。</span><span class="sxs-lookup"><span data-stu-id="a1e7c-107">The properties that make up an entity key should be chosen to guarantee uniqueness of instances in an entity set.</span></span>  
  
 <span data-ttu-id="a1e7c-108">下面是将一组属性用作实体键的要求：</span><span class="sxs-lookup"><span data-stu-id="a1e7c-108">The following are the requirements for a set of properties to be an entity key:</span></span>  
  
- <span data-ttu-id="a1e7c-109">实体集中不能存在两个相同的实体键。</span><span class="sxs-lookup"><span data-stu-id="a1e7c-109">No two entity keys within an entity set can be identical.</span></span> <span data-ttu-id="a1e7c-110">也就是说，对于实体集中的任意两个实体，构成一个键的所有属性的值不能全部相同。</span><span class="sxs-lookup"><span data-stu-id="a1e7c-110">That is, for any two entities within an entity set, the values for all of the properties that constitute a key cannot be the same.</span></span> <span data-ttu-id="a1e7c-111">但是，构成实体键的部分（而不是全部）值可以相同。</span><span class="sxs-lookup"><span data-stu-id="a1e7c-111">However, some (but not all) of the values that make up an entity key can be the same.</span></span>  
  
- <span data-ttu-id="a1e7c-112">实体键必须包含一组不可为 null 的不可变的 [基元类型属性](entity-data-model-primitive-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="a1e7c-112">An entity key must consist of a set of non-nullable, immutable, [primitive type properties](entity-data-model-primitive-data-types.md).</span></span>  
  
- <span data-ttu-id="a1e7c-113">构成给定实体类型的实体键的属性不可更改。</span><span class="sxs-lookup"><span data-stu-id="a1e7c-113">The properties that make up an entity key for a given entity type cannot change.</span></span> <span data-ttu-id="a1e7c-114">对于某个给定实体类型，不能允许存在多个可能的实体键；不支持代理键。</span><span class="sxs-lookup"><span data-stu-id="a1e7c-114">You cannot allow more than one possible entity key for a given entity type; surrogate keys are not supported.</span></span>  
  
- <span data-ttu-id="a1e7c-115">当实体位于继承层次结构中时，根实体必须包含构成实体键的所有属性，并且必须在根实体类型上定义实体键。</span><span class="sxs-lookup"><span data-stu-id="a1e7c-115">When an entity is involved in an inheritance hierarchy, the root entity must contain all the properties that make up the entity key, and the entity key must be defined on the root entity type.</span></span> <span data-ttu-id="a1e7c-116">有关详细信息，请参阅 [实体数据模型：继承](entity-data-model-inheritance.md)。</span><span class="sxs-lookup"><span data-stu-id="a1e7c-116">For more information, see [Entity Data Model: Inheritance](entity-data-model-inheritance.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1e7c-117">示例</span><span class="sxs-lookup"><span data-stu-id="a1e7c-117">Example</span></span>  

 <span data-ttu-id="a1e7c-118">下图显示了一个具有三个实体类型的概念模型：`Book`、`Publisher` 和 `Author`。</span><span class="sxs-lookup"><span data-stu-id="a1e7c-118">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="a1e7c-119">构成其实体键的每个实体类型的属性均用“(Key)”标示出来。</span><span class="sxs-lookup"><span data-stu-id="a1e7c-119">The properties of each entity type that make up its entity key are denoted with "(Key)".</span></span> <span data-ttu-id="a1e7c-120">请注意，`Author` 实体类型有一个包含两个属性（`Name` 和 `Address`）的实体键。</span><span class="sxs-lookup"><span data-stu-id="a1e7c-120">Note that the `Author` entity type has an entity key that consists of two properties, `Name` and `Address`.</span></span>  
  
 ![具有三个实体类型的示例模型](./media/entity-key/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="a1e7c-122">[ADO.NET 实体框架](./ef/index.md)使用一种特定于域的语言 (DSL) 称为概念架构定义语言 ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) 来定义概念模型。</span><span class="sxs-lookup"><span data-stu-id="a1e7c-122">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="a1e7c-123">下面的 CSDL 定义了上图中显示的 `Book` 实体类型。</span><span class="sxs-lookup"><span data-stu-id="a1e7c-123">The CSDL below defines the `Book` entity type shown in the diagram above.</span></span> <span data-ttu-id="a1e7c-124">请注意，实体键通过引用实体类型的 `ISBN` 属性来定义。</span><span class="sxs-lookup"><span data-stu-id="a1e7c-124">Note that the entity key is defined by referencing the `ISBN` property of the entity type.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 <span data-ttu-id="a1e7c-125">对实体键使用 `ISBN` 属性是一个不错的选择，因为国际标准书号 (ISBN) 可以唯一地标识一本书。</span><span class="sxs-lookup"><span data-stu-id="a1e7c-125">The `ISBN` property is a good choice for the entity key because an International Standard Book Number (ISBN) uniquely identifies a book.</span></span>  
  
 <span data-ttu-id="a1e7c-126">下面的 CSDL 定义了上图中显示的 `Author` 实体类型。</span><span class="sxs-lookup"><span data-stu-id="a1e7c-126">The CSDL below defines the `Author` entity type shown in the diagram above.</span></span> <span data-ttu-id="a1e7c-127">请注意，该实体键包含两个属性，`Name` 和 `Address`。</span><span class="sxs-lookup"><span data-stu-id="a1e7c-127">Note that the entity key consists of two properties, `Name` and `Address`.</span></span>  
  
 [!code-xml[EDM_Example_Model#CompositeKeyExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#compositekeyexample)]  
  
 <span data-ttu-id="a1e7c-128">对实体键使用 `Name` 和 `Address` 是一个合理的选择，因为两个同名作者住址相同的可能性很小。</span><span class="sxs-lookup"><span data-stu-id="a1e7c-128">Using `Name` and `Address` for the entity key is a reasonable choice, because two authors of the same name are unlikely to live at the same address.</span></span> <span data-ttu-id="a1e7c-129">但是，针对实体键的这种选择并不能绝对确保实体键在实体集中的唯一性。</span><span class="sxs-lookup"><span data-stu-id="a1e7c-129">However, this choice for an entity key does not absolutely guarantee unique entity keys in an entity set.</span></span> <span data-ttu-id="a1e7c-130">在这种情况下，建议添加一个可用来唯一标识作者的属性，例如 `AuthorId`。</span><span class="sxs-lookup"><span data-stu-id="a1e7c-130">Adding a property, such as `AuthorId`, that could be used to uniquely identify an author would be recommended in this case.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1e7c-131">请参阅</span><span class="sxs-lookup"><span data-stu-id="a1e7c-131">See also</span></span>

- [<span data-ttu-id="a1e7c-132">实体数据模型关键概念</span><span class="sxs-lookup"><span data-stu-id="a1e7c-132">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="a1e7c-133">实体数据模型</span><span class="sxs-lookup"><span data-stu-id="a1e7c-133">Entity Data Model</span></span>](entity-data-model.md)
