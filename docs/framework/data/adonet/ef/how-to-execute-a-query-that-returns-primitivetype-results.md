---
description: 了解详细信息：如何：执行返回 PrimitiveType 结果的查询
title: 如何：执行返回 PrimitiveType 结果的查询
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7139d585-4034-4dfa-916f-2120a8b72792
ms.openlocfilehash: e1493351b2c5923dc328b2ca65e784e76c5947ce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650607"
---
# <a name="how-to-execute-a-query-that-returns-primitivetype-results"></a>如何：执行返回 PrimitiveType 结果的查询

本主题演示如何使用 <xref:System.Data.EntityClient.EntityCommand> 针对概念模型执行命令，以及如何使用 <xref:System.Data.Metadata.Edm.PrimitiveType> 检索 <xref:System.Data.EntityClient.EntityDataReader> 结果。  
  
### <a name="to-run-the-code-in-this-example"></a>运行本示例中的代码  
  
1. 将 [AdventureWorks 销售模型](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) 添加到项目中，并将项目配置为使用实体框架。 有关详细信息，请参阅 [如何：使用实体数据模型向导](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))。  
  
2. 在应用程序的代码页中，添加以下 `using` 语句（在 Visual Basic 中为 `Imports`）：  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a>示例  

 本示例执行返回 <xref:System.Data.Metadata.Edm.PrimitiveType> 结果的查询。 如果将以下查询作为自变量传递给 `ExecutePrimitiveTypeQuery` 函数，则该函数将显示所有 `Products` 的平均定价：  
  
 [!code-csharp[DP EntityServices Concepts 2#EDM_AVG](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#edm_avg)]  
  
 如果传递参数化查询（如下面的查询），请将 <xref:System.Data.EntityClient.EntityParameter> 对象添加到 <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> 对象的 <xref:System.Data.EntityClient.EntityCommand> 属性。  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
 [!code-csharp[DP EntityServices Concepts#eSQLPrimitiveTypes](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#esqlprimitivetypes)]
 [!code-vb[DP EntityServices Concepts#eSQLPrimitiveTypes](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#esqlprimitivetypes)]  
  
## <a name="see-also"></a>请参阅

- [实体 SQL 引用](./language-reference/entity-sql-reference.md)
- [用于实体框架的 EntityClient 提供程序](entityclient-provider-for-the-entity-framework.md)
