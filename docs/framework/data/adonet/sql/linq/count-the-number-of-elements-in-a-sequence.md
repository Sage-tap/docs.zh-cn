---
description: 了解详细信息：计算序列中的元素数
title: 对序列中元素的数目进行计数
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccbe5d54-c9eb-4b14-b0ab-f628483c5f99
ms.openlocfilehash: 91030516098e900229a1e131ea0c9a7d8bef4034
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99663074"
---
# <a name="count-the-number-of-elements-in-a-sequence"></a><span data-ttu-id="d769e-103">对序列中元素的数目进行计数</span><span class="sxs-lookup"><span data-stu-id="d769e-103">Count the Number of Elements in a Sequence</span></span>

<span data-ttu-id="d769e-104">使用 <xref:System.Linq.Enumerable.Count%2A> 运算符可计算序列中的元素数目。</span><span class="sxs-lookup"><span data-stu-id="d769e-104">Use the <xref:System.Linq.Enumerable.Count%2A> operator to count the number of elements in a sequence.</span></span>  
  
 <span data-ttu-id="d769e-105">对 Northwind 示例数据库运行此查询产生的输出为 `91`。</span><span class="sxs-lookup"><span data-stu-id="d769e-105">Running this query against the Northwind sample database produces an output of `91`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d769e-106">示例</span><span class="sxs-lookup"><span data-stu-id="d769e-106">Example</span></span>  

 <span data-ttu-id="d769e-107">下面的示例计算数据库中的 `Customers` 数目。</span><span class="sxs-lookup"><span data-stu-id="d769e-107">The following example counts the number of `Customers` in the database.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#4)]
 [!code-vb[DLinqQueryExamples#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="d769e-108">示例</span><span class="sxs-lookup"><span data-stu-id="d769e-108">Example</span></span>  

 <span data-ttu-id="d769e-109">下面的示例计算数据库中尚未停产的产品数目。</span><span class="sxs-lookup"><span data-stu-id="d769e-109">The following example counts the number of products in the database that have not been discontinued.</span></span>  
  
 <span data-ttu-id="d769e-110">对 Northwind 示例数据库运行此示例产生的输出为 `69`。</span><span class="sxs-lookup"><span data-stu-id="d769e-110">Running this example against the Northwind sample database produces an output of `69`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#5)]
 [!code-vb[DLinqQueryExamples#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="d769e-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="d769e-111">See also</span></span>

- [<span data-ttu-id="d769e-112">聚合查询</span><span class="sxs-lookup"><span data-stu-id="d769e-112">Aggregate Queries</span></span>](aggregate-queries.md)
- [<span data-ttu-id="d769e-113">下载示例数据库</span><span class="sxs-lookup"><span data-stu-id="d769e-113">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
