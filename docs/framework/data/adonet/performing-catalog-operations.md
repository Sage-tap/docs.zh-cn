---
description: 了解详细信息：执行目录操作
title: 执行目录操作
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e60f542f-6271-495b-a9e4-48553481c2a3
ms.openlocfilehash: c484e3a56d846de66c6e13b374efe58430ab86b2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754337"
---
# <a name="performing-catalog-operations"></a>执行目录操作

若要执行对数据库或编录进行修改的命令（如 CREATE TABLE 或 CREATE PROCEDURE 语句），请使用相应的 SQL 语句和 Connection 对象创建一个 Command 对象。 通过 **命令** 对象的 **ExecuteNonQuery** 方法执行该命令。  
  
 以下代码示例在 Microsoft SQL Server 数据库中创建一个存储过程。  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim queryString As String = "CREATE PROCEDURE InsertCategory " & _  
    "@CategoryName nchar(15), " & _  
    "@Identity int OUT " & _  
    "AS " & _  
    "INSERT INTO Categories (CategoryName) VALUES(@CategoryName) " & _  
    "SET @Identity = @@Identity " & _  
    "RETURN @@ROWCOUNT"  
  
Dim command As SqlCommand = New SqlCommand(queryString, connection)  
command.ExecuteNonQuery()  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
string queryString = "CREATE PROCEDURE InsertCategory  " +
    "@CategoryName nchar(15), " +  
    "@Identity int OUT " +  
    "AS " +
    "INSERT INTO Categories (CategoryName) VALUES(@CategoryName) " +
    "SET @Identity = @@Identity " +  
    "RETURN @@ROWCOUNT";  
  
SqlCommand command = new SqlCommand(queryString, connection);  
command.ExecuteNonQuery();  
```  
  
## <a name="see-also"></a>请参阅

- [使用命令修改数据](using-commands-to-modify-data.md)
- [命令和参数](commands-and-parameters.md)
- [ADO.NET 概述](ado-net-overview.md)
