---
description: '了解详细信息：-- (注释)  (实体 SQL) '
title: --（注释）(Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5d9de735-2099-47f1-b7e7-60856f494924
ms.openlocfilehash: 793649177d9e64bead7b8755f35bdb51f53f4dd8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724968"
---
# <a name="---comment-entity-sql"></a>--（注释）(Entity SQL)

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查询可以包含注释。 注释行以两个短划线 (`--`) 开头。  
  
## <a name="syntax"></a>语法  
  
```csharp  
-- text_of_comment  
```  
  
## <a name="arguments"></a>参数  

 `text_of_comment`  
 包含注释文本的字符串。  
  
## <a name="example"></a>示例  

 下面的 Entity SQL 查询演示如何使用注释。 此查询基于 AdventureWorks 销售模型。 若要编译并运行此查询，请执行下列步骤：  
  
1. 执行 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的过程。  
  
2. 将以下查询作为参数传递给 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#COMMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#comment)]  
  
## <a name="see-also"></a>请参阅

- [Entity SQL 概述](entity-sql-overview.md)
- [实体 SQL 引用](entity-sql-reference.md)
