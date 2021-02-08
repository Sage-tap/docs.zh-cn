---
description: '了解详细信息：使用 (实体 SQL) '
title: USING (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
ms.openlocfilehash: 084ab56f25041377dd6a0a35dd743122f482eeba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795048"
---
# <a name="using-entity-sql"></a>USING (Entity SQL)

指定查询表达式中使用的命名空间。  
  
## <a name="syntax"></a>语法  
  
```sql  
USING [ alias = ] namespace  
```  
  
## <a name="arguments"></a>参数  

 `alias`  
 指定用于限定命名空间的较短别名。  
  
 `namespace`  
 任何有效的命名空间。  
  
## <a name="example"></a>示例  

 以下 Entity SQL 查询使用 USING 运算符以指定查询表达式中使用的命名空间。 若要编译并运行此查询，请执行下列步骤：  
  
1. 按照 [如何：执行返回 PrimitiveType 结果的查询](../how-to-execute-a-query-that-returns-primitivetype-results.md)中的过程进行操作。  
  
2. 将以下查询作为参数传递给 `ExecutePrimitiveTypeQuery` 方法：  
  
```csharp
using SqlServer; RAND()  
```  
  
## <a name="see-also"></a>请参阅

- [命名空间](namespaces-entity-sql.md)
- [实体 SQL 引用](entity-sql-reference.md)
