---
description: '了解详细信息： Method-Based 查询语法示例： LINQ to DataSet 排序 () '
title: 基于方法的查询语法示例：排序 (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8f9ce4fd-e84f-48c0-bb64-89e217236d3e
ms.openlocfilehash: d655ff52fe30a9af15245a4c9989062107bb6842
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99672655"
---
# <a name="method-based-query-syntax-examples-ordering-linq-to-dataset"></a>基于方法的查询语法示例：排序 (LINQ to DataSet)

本主题中的示例演示如何使用 <xref:System.Linq.Enumerable.OrderBy%2A>、<xref:System.Linq.Enumerable.Reverse%2A> 和 <xref:System.Linq.Enumerable.ThenBy%2A> 方法来查询 <xref:System.Data.DataSet> 并使用方法查询语法对结果排序。  
  
 在 `FillDataSet` 这些示例中使用的方法是在将 [数据加载到数据集](loading-data-into-a-dataset.md)时指定的。  
  
 本主题中的示例使用 AdventureWorks 示例数据库中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 表。  
  
 本主题中的示例使用以下 `using` / `Imports` 语句：  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 有关详细信息，请参阅 [如何：在 Visual Studio 中创建 LINQ to DataSet 项目](how-to-create-a-linq-to-dataset-project-in-vs.md)。  
  
## <a name="orderby"></a>OrderBy  
  
### <a name="example"></a>示例  

 此示例使用具有自定义比较器的 <xref:System.Linq.Enumerable.OrderBy%2A> 方法对姓氏执行不区分大小写的排序。  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderByComparer_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbycomparer_mq)]
 [!code-vb[DP LINQ to DataSet Examples#OrderByComparer_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbycomparer_mq)]  
  
## <a name="reverse"></a>Reverse  
  
### <a name="example"></a>示例  

 此示例使用 <xref:System.Linq.Enumerable.Reverse%2A> 方法创建 `OrderDate` 早于 2002 年 2 月 20 日的订单的列表。  
  
 [!code-csharp[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#reverse)]
 [!code-vb[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#reverse)]  
  
## <a name="thenby"></a>ThenBy  
  
### <a name="example"></a>示例  

 此示例使用具有自定义比较器的 <xref:System.Linq.Enumerable.OrderBy%2A> 和 <xref:System.Linq.Enumerable.ThenBy%2A> 方法对产品名称先按定价排序，然后执行不区分大小写的降序排序。  
  
 [!code-csharp[DP LINQ to DataSet Examples#ThenByDescendingComparer_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#thenbydescendingcomparer_mq)]
 [!code-vb[DP LINQ to DataSet Examples#ThenByDescendingComparer_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#thenbydescendingcomparer_mq)]  
  
## <a name="see-also"></a>请参阅

- [将数据加载到数据集中](loading-data-into-a-dataset.md)
- [LINQ to DataSet 示例](linq-to-dataset-examples.md)
- [标准查询运算符概述 (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [标准查询运算符概述 (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
