---
description: 了解详细信息：如何：控制检索的相关数据量
title: 如何：控制检索的相关数据量
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: efdc203e-3da9-4477-815e-54f10c3d7c6c
ms.openlocfilehash: becf1282d18d5c630da3e3be27c62ebae404d940
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786038"
---
# <a name="how-to-control-how-much-related-data-is-retrieved"></a><span data-ttu-id="d8055-103">如何：控制检索的相关数据量</span><span class="sxs-lookup"><span data-stu-id="d8055-103">How to: Control How Much Related Data Is Retrieved</span></span>

<span data-ttu-id="d8055-104">使用 <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> 方法可指定应同时检索与主目标相关的哪些数据。</span><span class="sxs-lookup"><span data-stu-id="d8055-104">Use the <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> method to specify which data related to your main target should be retrieved at the same time.</span></span> <span data-ttu-id="d8055-105">例如，如果您了解将需要有关客户订单的信息，则可以使用 <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> 来确保在检索客户信息时会检索订单信息。</span><span class="sxs-lookup"><span data-stu-id="d8055-105">For example, if you know you will need information about customers' orders, you can use <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> to make sure that the order information is retrieved at the same time as the customer information.</span></span> <span data-ttu-id="d8055-106">这种方法的结果是只检索一次数据库即可获取这两组信息。</span><span class="sxs-lookup"><span data-stu-id="d8055-106">This approach results in only one trip to the database for both sets of information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d8055-107">通过将叉积作为一个大型投影检索，可以检索与您的查询主目标相关的数据，例如在以客户为目标时检索订单。</span><span class="sxs-lookup"><span data-stu-id="d8055-107">You can retrieve data related to the main target of your query by retrieving a cross-product as one large projection, such as retrieving orders when you target customers.</span></span> <span data-ttu-id="d8055-108">但这种方法往往存在弊端。</span><span class="sxs-lookup"><span data-stu-id="d8055-108">But this approach often has disadvantages.</span></span> <span data-ttu-id="d8055-109">例如，所得结果仅仅为投影，而不是可以由 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 更改和持久化的实体。</span><span class="sxs-lookup"><span data-stu-id="d8055-109">For example, the results are just projections and not entities that can be changed and persisted by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="d8055-110">此外，您可能会检索到您并不需要的大量数据。</span><span class="sxs-lookup"><span data-stu-id="d8055-110">And you can be retrieving lots of data that you do not need.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8055-111">示例</span><span class="sxs-lookup"><span data-stu-id="d8055-111">Example</span></span>  

 <span data-ttu-id="d8055-112">在下面的示例中，在执行查询时会检索到位于伦敦的所有 `Orders` 所下的所有 `Customers`。</span><span class="sxs-lookup"><span data-stu-id="d8055-112">In the following example, all the `Orders` for all the `Customers` who are located in London are retrieved when the query is executed.</span></span> <span data-ttu-id="d8055-113">这样一来，连续访问 `Orders` 对象的 `Customer` 属性不会触发新的数据库查询。</span><span class="sxs-lookup"><span data-stu-id="d8055-113">As a result, successive access to the `Orders` property on a `Customer` object does not trigger a new database query.</span></span>  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="d8055-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="d8055-114">See also</span></span>

- [<span data-ttu-id="d8055-115">查询数据库</span><span class="sxs-lookup"><span data-stu-id="d8055-115">Querying the Database</span></span>](querying-the-database.md)
