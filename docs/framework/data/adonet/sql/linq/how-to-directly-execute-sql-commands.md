---
description: 了解详细信息：如何：直接执行 SQL 命令
title: 如何：直接执行 SQL 命令
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 04671bb0-40c0-4465-86e5-77986f454661
ms.openlocfilehash: 9dd53b3582b6099bae51dc008debd8cb3142e386
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786025"
---
# <a name="how-to-directly-execute-sql-commands"></a>如何：直接执行 SQL 命令

采用 <xref:System.Data.Linq.DataContext> 连接时，可以使用 <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> 来执行不返回对象的 SQL 命令。  
  
## <a name="example"></a>示例  

 下面的示例会导致 SQL Server 将 UnitPrice 增加 1.00。  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#3)]
 [!code-vb[DLinqCommunicatingWithDatabase#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>请参阅

- [如何：直接执行 SQL 查询](how-to-directly-execute-sql-queries.md)
- [与数据库通信](communicating-with-the-database.md)
