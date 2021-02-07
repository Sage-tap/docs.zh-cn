---
description: 了解详细信息：远程执行与本地执行
title: 远程查询执行与本地执行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ee50e943-9349-4c84-ab1c-c35d3ada1a9c
ms.openlocfilehash: ea4d85faedd4a299da292029e64d77132e1a65a9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695172"
---
# <a name="remote-vs-local-execution"></a><span data-ttu-id="6452b-103">远程查询执行与本地执行</span><span class="sxs-lookup"><span data-stu-id="6452b-103">Remote vs. Local Execution</span></span>

<span data-ttu-id="6452b-104">您可以决定以远程方式（即数据库引擎对数据库执行查询）或在本地（[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 对本地缓存执行查询）执行您的查询。</span><span class="sxs-lookup"><span data-stu-id="6452b-104">You can decide to execute your queries either remotely (that is, the database engine executes the query against the database) or locally ([!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] executes the query against a local cache).</span></span>  
  
## <a name="remote-execution"></a><span data-ttu-id="6452b-105">远程执行</span><span class="sxs-lookup"><span data-stu-id="6452b-105">Remote Execution</span></span>  

 <span data-ttu-id="6452b-106">请考虑下列查询：</span><span class="sxs-lookup"><span data-stu-id="6452b-106">Consider the following query:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#7)]
 [!code-vb[DLinqQueryConcepts#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#7)]  
  
 <span data-ttu-id="6452b-107">如果数据库有数千行订单，则在处理其中很小一部分时您不需要将它们全都检索出来。</span><span class="sxs-lookup"><span data-stu-id="6452b-107">If your database has thousands of rows of orders, you do not want to retrieve them all to process a small subset.</span></span> <span data-ttu-id="6452b-108">在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中，<xref:System.Data.Linq.EntitySet%601> 类实现了 <xref:System.Linq.IQueryable> 接口。</span><span class="sxs-lookup"><span data-stu-id="6452b-108">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Data.Linq.EntitySet%601> class implements the <xref:System.Linq.IQueryable> interface.</span></span> <span data-ttu-id="6452b-109">这种方式确保了可以以远程方式执行此类查询。</span><span class="sxs-lookup"><span data-stu-id="6452b-109">This approach makes sure that such queries can be executed remotely.</span></span> <span data-ttu-id="6452b-110">利用此技术有两大优点：</span><span class="sxs-lookup"><span data-stu-id="6452b-110">Two major benefits flow from this technique:</span></span>  
  
- <span data-ttu-id="6452b-111">不会检索到不需要的数据。</span><span class="sxs-lookup"><span data-stu-id="6452b-111">Unnecessary data is not retrieved.</span></span>  
  
- <span data-ttu-id="6452b-112">由于利用了数据库索引，由数据库引擎执行的查询通常更为高效。</span><span class="sxs-lookup"><span data-stu-id="6452b-112">A query executed by the database engine is often more efficient because of the database indexes.</span></span>  
  
## <a name="local-execution"></a><span data-ttu-id="6452b-113">本地执行</span><span class="sxs-lookup"><span data-stu-id="6452b-113">Local Execution</span></span>  

 <span data-ttu-id="6452b-114">在其他一些情况下，您可能需要在本地缓存中保留完整的相关实体集。</span><span class="sxs-lookup"><span data-stu-id="6452b-114">In other situations, you might want to have the complete set of related entities in the local cache.</span></span> <span data-ttu-id="6452b-115">为此，<xref:System.Data.Linq.EntitySet%601> 提供了 <xref:System.Data.Linq.EntitySet%601.Load%2A> 方法，用于显式加载 <xref:System.Data.Linq.EntitySet%601> 的所有成员。</span><span class="sxs-lookup"><span data-stu-id="6452b-115">For this purpose, <xref:System.Data.Linq.EntitySet%601> provides the <xref:System.Data.Linq.EntitySet%601.Load%2A> method to explicitly load all the members of the <xref:System.Data.Linq.EntitySet%601>.</span></span>  
  
 <span data-ttu-id="6452b-116">如果 <xref:System.Data.Linq.EntitySet%601> 已经加载，则后续查询将在本地执行。</span><span class="sxs-lookup"><span data-stu-id="6452b-116">If an <xref:System.Data.Linq.EntitySet%601> is already loaded, subsequent queries are executed locally.</span></span> <span data-ttu-id="6452b-117">这种方式在两个方面起到帮助作用：</span><span class="sxs-lookup"><span data-stu-id="6452b-117">This approach helps in two ways:</span></span>  
  
- <span data-ttu-id="6452b-118">如果此完整集必须在本地使用或使用多次，则您可以避免远程查询和与之相关的延迟。</span><span class="sxs-lookup"><span data-stu-id="6452b-118">If the complete set must be used locally or multiple times, you can avoid remote queries and associated latencies.</span></span>  
  
- <span data-ttu-id="6452b-119">实体可以序列化为完整的实体。</span><span class="sxs-lookup"><span data-stu-id="6452b-119">The entity can be serialized as a complete entity.</span></span>  
  
 <span data-ttu-id="6452b-120">下面的代码段演示了如何实现本地执行：</span><span class="sxs-lookup"><span data-stu-id="6452b-120">The following code fragment illustrates how local execution can be obtained:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#8)]
 [!code-vb[DLinqQueryConcepts#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#8)]  
  
## <a name="comparison"></a><span data-ttu-id="6452b-121">比较</span><span class="sxs-lookup"><span data-stu-id="6452b-121">Comparison</span></span>  

 <span data-ttu-id="6452b-122">这两项功能提供了强大的选项组合：大型集合采用以远程方式执行，小型集合或在需要完整集的情况下在本地执行。</span><span class="sxs-lookup"><span data-stu-id="6452b-122">These two capabilities provide a powerful combination of options: remote execution for large collections and local execution for small collections or where the complete collection is needed.</span></span> <span data-ttu-id="6452b-123">您需要通过 <xref:System.Linq.IQueryable> 进行远程执行，对于本地执行，则需要对内存中的 <xref:System.Collections.Generic.IEnumerable%601> 集合执行。</span><span class="sxs-lookup"><span data-stu-id="6452b-123">You implement remote execution through <xref:System.Linq.IQueryable>, and local execution against an in-memory <xref:System.Collections.Generic.IEnumerable%601> collection.</span></span> <span data-ttu-id="6452b-124">若要强制执行本地执行 (即 <xref:System.Collections.Generic.IEnumerable%601>) ，请参阅 [将类型转换为泛型 IEnumerable](convert-a-type-to-a-generic-ienumerable.md)。</span><span class="sxs-lookup"><span data-stu-id="6452b-124">To force local execution (that is, <xref:System.Collections.Generic.IEnumerable%601>), see [Convert a Type to a Generic IEnumerable](convert-a-type-to-a-generic-ienumerable.md).</span></span>  
  
### <a name="queries-against-unordered-sets"></a><span data-ttu-id="6452b-125">针对无序集的查询</span><span class="sxs-lookup"><span data-stu-id="6452b-125">Queries Against Unordered Sets</span></span>  

 <span data-ttu-id="6452b-126">请注意实现的本地集合 <xref:System.Collections.Generic.List%601> 与提供对关系数据库中 *无序集* 执行的远程查询的集合之间的重要区别。</span><span class="sxs-lookup"><span data-stu-id="6452b-126">Note the important difference between a local collection that implements <xref:System.Collections.Generic.List%601> and a collection that provides remote queries executed against *unordered sets* in a relational database.</span></span> <span data-ttu-id="6452b-127"><xref:System.Collections.Generic.List%601> 方法（如使用索引值的那些方法）需要列表语义，列表语义通常无法通过针对无序集的远程查询获得。</span><span class="sxs-lookup"><span data-stu-id="6452b-127"><xref:System.Collections.Generic.List%601> methods such as those that use index values require list semantics, which typically cannot be obtained through a remote query against an unordered set.</span></span> <span data-ttu-id="6452b-128">因此，此类方法隐式加载 <xref:System.Data.Linq.EntitySet%601>，以允许本地执行。</span><span class="sxs-lookup"><span data-stu-id="6452b-128">For this reason, such methods implicitly load the <xref:System.Data.Linq.EntitySet%601> to allow local execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6452b-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="6452b-129">See also</span></span>

- [<span data-ttu-id="6452b-130">查询概念</span><span class="sxs-lookup"><span data-stu-id="6452b-130">Query Concepts</span></span>](query-concepts.md)
