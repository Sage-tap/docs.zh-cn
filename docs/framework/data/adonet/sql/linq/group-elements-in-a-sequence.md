---
description: 了解详细信息：按顺序对元素进行分组
title: 对序列中的元素进行分组
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1d50c8b4-f550-4775-bbb6-eab6e874cb43
ms.openlocfilehash: bc9a4d042ed0edb090f0530ebb24d99a5390c882
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786064"
---
# <a name="group-elements-in-a-sequence"></a>对序列中的元素进行分组

<xref:System.Linq.Enumerable.GroupBy%2A> 运算符用于对序列中的元素进行分组。 下面的示例使用 Northwind 数据库。  
  
> [!NOTE]
> <xref:System.Linq.Enumerable.GroupBy%2A> 查询中的 Null 列值有时可能引发 <xref:System.InvalidOperationException>。 有关详细信息，请参阅 [疑难解答](troubleshooting.md)的 "GroupBy InvalidOperationException" 部分。  
  
## <a name="example"></a>示例  

 下面的示例按照 `Products` 对 `CategoryID` 进行分区。  
  
 [!code-csharp[DLinqQueryExamples#27](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#27)]
 [!code-vb[DLinqQueryExamples#27](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#27)]  
  
## <a name="example"></a>示例  

 下面的示例使用 <xref:System.Linq.Enumerable.Max%2A> 来查找每个 `CategoryID` 的最高单价。  
  
 [!code-csharp[DLinqQueryExamples#28](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#28)]
 [!code-vb[DLinqQueryExamples#28](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#28)]  
  
## <a name="example"></a>示例  

 下面的示例使用 Average 来查找每个 `UnitPrice` 的平均 `CategoryID`。  
  
 [!code-csharp[DLinqQueryExamples#29](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#29)]
 [!code-vb[DLinqQueryExamples#29](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#29)]  
  
## <a name="example"></a>示例  

 下面的示例使用 <xref:System.Linq.Queryable.Sum%2A> 来查找每个 `UnitPrice` 的总 `CategoryID`。  
  
 [!code-csharp[DLinqQueryExamples#30](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#30)]
 [!code-vb[DLinqQueryExamples#30](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#30)]  
  
## <a name="example"></a>示例  

 下面的示例使用 <xref:System.Linq.Queryable.Count%2A> 来查找每个 `Products` 中已停产 `CategoryID` 的数量。  
  
 [!code-csharp[DLinqQueryExamples#31](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#31)]
 [!code-vb[DLinqQueryExamples#31](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#31)]  
  
## <a name="example"></a>示例  

 下面的示例使用后跟的 `where` 子句来查找至少包含 10 种产品的所有类别。  
  
 [!code-csharp[DLinqQueryExamples#32](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#32)]
 [!code-vb[DLinqQueryExamples#32](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#32)]  
  
## <a name="example"></a>示例  

 下面的示例按 `CategoryID` 和 `SupplierID` 对产品进行分组。  
  
 [!code-csharp[DLinqQueryExamples#33](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#33)]
 [!code-vb[DLinqQueryExamples#33](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#33)]  
  
## <a name="example"></a>示例  

 下面的示例返回两个产品序列。 第一个序列包含单价小于或等于 10 的产品。 第二个序列包含单价大于 10 的产品。  
  
 [!code-csharp[DLinqQueryExamples#34](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#34)]
 [!code-vb[DLinqQueryExamples#34](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#34)]  
  
## <a name="example"></a>示例  

 <xref:System.Linq.Queryable.GroupBy%2A> 运算符只能采用单个键自变量。 如果您需要按多个键进行分组，则必须创建匿名类型，如下例所示：  
  
 [!code-csharp[DLinqQueryExamples#35](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#35)]
 [!code-vb[DLinqQueryExamples#35](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#35)]  
  
## <a name="see-also"></a>请参阅

- [查询示例](query-examples.md)
- [下载示例数据库](downloading-sample-databases.md)
