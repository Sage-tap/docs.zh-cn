---
description: 了解详细信息：单次大容量复制操作
title: 单个批量复制操作
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5e7ff0be-3f23-4996-a92c-bd54d65c3836
ms.openlocfilehash: f6b046fbd73ad798f3f9f117eea0b72f46e43b37
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767474"
---
# <a name="single-bulk-copy-operations"></a>单个批量复制操作

执行 SQL Server 大容量复制操作的最简单方法是针对数据库执行单次操作。 默认情况下，大容量复制操作作为独立的操作执行：复制操作以非事务的方式执行，不可对其进行回滚。

> [!NOTE]
> 如果在发生错误时需要回滚全部或部分大容量复制，可以使用 <xref:System.Data.SqlClient.SqlBulkCopy> 托管的事务，或者在现有事务内执行大容量复制操作。 如果连接在 System.Transactions 事务中（显式或隐式）登记，SqlBulkCopy 也将适用于  <xref:System.Transactions>  。
>
> 有关详细信息，请参阅 [事务和大容量复制操作](transaction-and-bulk-copy-operations.md)。

执行大容量复制操作的常规步骤如下：

1. 连接到源服务器并获取要复制的数据。 如果可以从 <xref:System.Data.IDataReader> 或 <xref:System.Data.DataTable> 对象检索数据，那么数据也可以来自其他源。

2. 连接到目标服务器（除非希望 SqlBulkCopy 为你建立连接  ）。

3. 创建 <xref:System.Data.SqlClient.SqlBulkCopy> 对象，设置任何必要的属性。

4. 设置 DestinationTableName 属性以指示执行批量插入操作的目标表  。

5. 调用 WriteToServer 方法之一  。

6. 可以选择更新属性并根据需要再次调用 WriteToServer  。

7. 调用 <xref:System.Data.SqlClient.SqlBulkCopy.Close%2A>，或在 `Using` 语句中包装大容量复制操作。

> [!CAUTION]
> 我们建议使源列与目标列数据类型相匹配。 如果数据类型不匹配，则 SqlBulkCopy 会尝试使用由  **部署的规则将每个源值转换为目标数据类型**<xref:System.Data.SqlClient.SqlParameter.Value%2A>。 转换可能会影响性能，也可能会导致意外错误。 例如，在多数情况下，`Double` 数据类型可转换为 `Decimal` 数据类型，但并非总是如此。

## <a name="example"></a>示例

下面的控制台应用程序演示了如何使用 <xref:System.Data.SqlClient.SqlBulkCopy> 类加载数据。 在此示例中，<xref:System.Data.SqlClient.SqlDataReader> 用于将数据从 SQL Server AdventureWorks 数据库的 Production.Product 表复制到相同数据库的一个类似的表中   。

> [!IMPORTANT]
> 除非已按照 [大容量复制示例设置](bulk-copy-example-setup.md)中所述创建了工作表，否则此示例将不会运行。 提供此代码是为了演示仅使用 SqlBulkCopy 时的语法  。 如果源表和目标表位于同一 SQL Server 实例中，可以更便捷地使用 Transact-SQL `INSERT … SELECT` 语句复制数据。

[!code-csharp[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/CS/source.cs#1)]
[!code-vb[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/VB/source.vb#1)]

## <a name="performing-a-bulk-copy-operation-using-transact-sql-and-the-command-class"></a>使用 Transact-SQL 和命令类执行批量复制操作

下面的示例说明了如何使用 <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> 方法执行 BULK INSERT 语句。

> [!NOTE]
> 数据源的文件路径相对于服务器。 服务器进程必须有权访问该路径，才能成功执行大容量复制操作。

```vb
Using connection As SqlConnection = New SqlConnection(connectionString)
Dim queryString As String = _
    "BULK INSERT Northwind.dbo.[Order Details] FROM " & _
    "'f:\mydata\data.tbl' WITH (FORMATFILE='f:\mydata\data.fmt' )"
connection.Open()
SqlCommand command = New SqlCommand(queryString, connection);

command.ExecuteNonQuery()
End Using
```

```csharp
using (SqlConnection connection = New SqlConnection(connectionString))
{
string queryString =  "BULK INSERT Northwind.dbo.[Order Details] " +
    "FROM 'f:\mydata\data.tbl' " +
    "WITH ( FORMATFILE='f:\mydata\data.fmt' )";
connection.Open();
SqlCommand command = new SqlCommand(queryString, connection);

command.ExecuteNonQuery();
}
```

## <a name="see-also"></a>请参阅

- [SQL Server 中的大容量复制操作](bulk-copy-operations-in-sql-server.md)
- [ADO.NET 概述](../ado-net-overview.md)
