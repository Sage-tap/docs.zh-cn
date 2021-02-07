---
description: 了解详细信息：查询表达式语法示例：元素运算符
title: 查询表达式语法示例：元素运算符
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 32268fe2-de18-4065-8060-f250def83837
ms.openlocfilehash: 0dc6d49959abba712cef572eaa549138af646bd5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696238"
---
# <a name="query-expression-syntax-examples-element-operators"></a><span data-ttu-id="44638-103">查询表达式语法示例：元素运算符</span><span class="sxs-lookup"><span data-stu-id="44638-103">Query Expression Syntax Examples: Element Operators</span></span>

<span data-ttu-id="44638-104">本主题中的示例演示如何使用 <xref:System.Linq.Enumerable.First%2A> 方法通过使用查询表达式语法来查询 [AdventureWorks 销售模型](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) 。</span><span class="sxs-lookup"><span data-stu-id="44638-104">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> method to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using the query expression syntax.</span></span> <span data-ttu-id="44638-105">这些示例中使用的 AdventureWorks 销售模型从 AdventureWorks 示例数据库中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 等表生成。</span><span class="sxs-lookup"><span data-stu-id="44638-105">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="44638-106">本主题中的示例使用以下 `using` / `Imports` 语句：</span><span class="sxs-lookup"><span data-stu-id="44638-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="first"></a><span data-ttu-id="44638-107">First</span><span class="sxs-lookup"><span data-stu-id="44638-107">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="44638-108">示例</span><span class="sxs-lookup"><span data-stu-id="44638-108">Example</span></span>  

 <span data-ttu-id="44638-109">以下示例使用 <xref:System.Linq.Enumerable.First%2A> 方法以返回其名字为“Brooke”的第一个联系人。</span><span class="sxs-lookup"><span data-stu-id="44638-109">The following example uses the <xref:System.Linq.Enumerable.First%2A> method to return the first contact whose first name is "Brooke".</span></span>  
  
 [!code-csharp[DP L2E Examples#FirstSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#firstsimple)]
 [!code-vb[DP L2E Examples#FirstSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#firstsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="44638-110">请参阅</span><span class="sxs-lookup"><span data-stu-id="44638-110">See also</span></span>

- [<span data-ttu-id="44638-111">LINQ to Entities 中的查询</span><span class="sxs-lookup"><span data-stu-id="44638-111">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
