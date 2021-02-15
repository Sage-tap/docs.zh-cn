---
description: 了解更多：延迟与立即加载
title: 推迟加载与即时加载
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d1d7247f-a3b7-460b-b342-5c1a2365aa1a
ms.openlocfilehash: 8c2237bd726ca79c7c168040e2a701f51ec3d238
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100464750"
---
# <a name="deferred-versus-immediate-loading"></a><span data-ttu-id="03b92-103">推迟加载与即时加载</span><span class="sxs-lookup"><span data-stu-id="03b92-103">Deferred versus Immediate Loading</span></span>

<span data-ttu-id="03b92-104">查询某对象时，实际上您只检索请求的对象。</span><span class="sxs-lookup"><span data-stu-id="03b92-104">When you query for an object, you actually retrieve only the object you requested.</span></span> <span data-ttu-id="03b92-105">不会同时自动提取 *相关* 的对象。</span><span class="sxs-lookup"><span data-stu-id="03b92-105">The *related* objects are not automatically fetched at the same time.</span></span> <span data-ttu-id="03b92-106"> (有关详细信息，请参阅 [跨关系进行查询](querying-across-relationships.md)。 ) 找不到相关对象尚未加载的事实，因为尝试访问它们会生成检索它们的请求。</span><span class="sxs-lookup"><span data-stu-id="03b92-106">(For more information, see [Querying Across Relationships](querying-across-relationships.md).) You cannot see the fact that the related objects are not already loaded, because an attempt to access them produces a request that retrieves them.</span></span>  
  
 <span data-ttu-id="03b92-107">例如，你可能需要查询一组特定的订单，然后仅偶尔向特定客户发送电子邮件通知。</span><span class="sxs-lookup"><span data-stu-id="03b92-107">For example, you might want to query for a particular set of orders and then only occasionally send an email notification to particular customers.</span></span> <span data-ttu-id="03b92-108">您最初不一定需要检索与每个订单有关的所有客户数据。</span><span class="sxs-lookup"><span data-stu-id="03b92-108">You would not necessarily need initially to retrieve all customer data with every order.</span></span> <span data-ttu-id="03b92-109">您可以使用延迟加载将额外信息的检索操作延迟到您确实需要检索它们时再进行。</span><span class="sxs-lookup"><span data-stu-id="03b92-109">You can use deferred loading to defer retrieval of extra information until you absolutely have to.</span></span> <span data-ttu-id="03b92-110">请看下面的示例：</span><span class="sxs-lookup"><span data-stu-id="03b92-110">Consider the following example:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#1)]
 [!code-vb[DLinqQueryConcepts#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#1)]  
  
 <span data-ttu-id="03b92-111">反过来也可能是可行的。</span><span class="sxs-lookup"><span data-stu-id="03b92-111">The opposite might also be true.</span></span> <span data-ttu-id="03b92-112">您的应用程序可能必须同时查看客户数据和订单数据。</span><span class="sxs-lookup"><span data-stu-id="03b92-112">You might have an application that has to view customer and order data at the same time.</span></span> <span data-ttu-id="03b92-113">您了解同时需要这两组数据。</span><span class="sxs-lookup"><span data-stu-id="03b92-113">You know you need both sets of data.</span></span> <span data-ttu-id="03b92-114">您了解一旦获得结果，您的应用程序就需要每个客户的订单信息。</span><span class="sxs-lookup"><span data-stu-id="03b92-114">You know your application needs order information for each customer as soon as you get the results.</span></span> <span data-ttu-id="03b92-115">您不希望一个一个地提交对每个客户的订单的查询。</span><span class="sxs-lookup"><span data-stu-id="03b92-115">You would not want to submit individual queries for orders for every customer.</span></span> <span data-ttu-id="03b92-116">您真正想要的是将订单数据与客户信息一起检索出来。</span><span class="sxs-lookup"><span data-stu-id="03b92-116">What you really want is to retrieve the order data together with the customers.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#2)]
 [!code-vb[DLinqQueryConcepts#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#2)]  
  
 <span data-ttu-id="03b92-117">您还可以在查询中联接客户和订单，方法是构建叉积并将所有相关数据位作为一个大型投影检索出来。</span><span class="sxs-lookup"><span data-stu-id="03b92-117">You can also join customers and orders in a query by forming the cross-product and retrieving all the relative bits of data as one large projection.</span></span> <span data-ttu-id="03b92-118">但这些结果并非实体。</span><span class="sxs-lookup"><span data-stu-id="03b92-118">But these results are not entities.</span></span> <span data-ttu-id="03b92-119">有关详细信息，请参阅 [LINQ to SQL 对象模型) 的](the-linq-to-sql-object-model.md) (。</span><span class="sxs-lookup"><span data-stu-id="03b92-119">(For more information, see [The LINQ to SQL Object Model](the-linq-to-sql-object-model.md)).</span></span> <span data-ttu-id="03b92-120">实体是具有标识且您可以修改的对象，而这些结果将是无法更改和持久化的投影。</span><span class="sxs-lookup"><span data-stu-id="03b92-120">Entities are objects that have identity and that you can modify, whereas these results would be projections that cannot be changed and persisted.</span></span> <span data-ttu-id="03b92-121">更糟的是，您将检索到大量的冗余数据，因为在平展联接输出中，对于每个订单，每个客户将重复出现。</span><span class="sxs-lookup"><span data-stu-id="03b92-121">Even worse, you would be retrieving lots of redundant data as each customer repeats for each order in the flattened join output.</span></span>  
  
 <span data-ttu-id="03b92-122">您真正需要的是同时检索相关对象的集合的方法。</span><span class="sxs-lookup"><span data-stu-id="03b92-122">What you really need is a way to retrieve a set of related objects at the same time.</span></span> <span data-ttu-id="03b92-123">此集合是关系图的精确剖面，因此您检索到的数据绝不会比您所需要的数据多或少。</span><span class="sxs-lookup"><span data-stu-id="03b92-123">The set is a delineated section of a graph so that you would never be retrieving more or less than was necessary for your intended use.</span></span> <span data-ttu-id="03b92-124">为此，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 提供了 <xref:System.Data.Linq.DataLoadOptions>，用以立即加载对象模型的某一区域。</span><span class="sxs-lookup"><span data-stu-id="03b92-124">For this purpose, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides <xref:System.Data.Linq.DataLoadOptions> for immediate loading of a region of your object model.</span></span> <span data-ttu-id="03b92-125">方法包括：</span><span class="sxs-lookup"><span data-stu-id="03b92-125">Methods include:</span></span>  
  
- <span data-ttu-id="03b92-126"><xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> 方法，用于立即加载与主目标相关的数据。</span><span class="sxs-lookup"><span data-stu-id="03b92-126">The  <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> method, to immediately load data related to the main target.</span></span>  
  
- <span data-ttu-id="03b92-127"><xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> 方法，用于筛选为特定关系检索到的对象。</span><span class="sxs-lookup"><span data-stu-id="03b92-127">The <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> method, to filter objects retrieved for a particular relationship.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03b92-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="03b92-128">See also</span></span>

- [<span data-ttu-id="03b92-129">查询概念</span><span class="sxs-lookup"><span data-stu-id="03b92-129">Query Concepts</span></span>](query-concepts.md)
