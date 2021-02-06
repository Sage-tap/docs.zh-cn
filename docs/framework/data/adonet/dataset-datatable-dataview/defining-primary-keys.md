---
description: 了解详细信息：定义主键
title: 定义主键
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2ea85959-e763-4669-8bd9-46a9dab894bd
ms.openlocfilehash: 2becfbd124af723f55edb39666352fc501044045
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652544"
---
# <a name="defining-primary-keys"></a>定义主键

数据库表通常都有一列或一组列，用于唯一地标识表中的每一行。 这种具有标识作用的列或列组称为主键。  
  
 当你将单个指定 <xref:System.Data.DataColumn> 为的时 <xref:System.Data.DataTable.PrimaryKey%2A> <xref:System.Data.DataTable> ，该表会自动将列的 <xref:System.Data.DataColumn.AllowDBNull%2A> 属性设置为 **false** ，并将 <xref:System.Data.DataColumn.Unique%2A> 属性设置为 **true**。 对于多列主键，仅 **AllowDBNull** 属性自动设置为 **false**。  
  
 接收的 **PrimaryKey** 属性的 <xref:System.Data.DataTable> 值是一个或多个 **DataColumn** 对象的数组，如下面的示例中所示。 第一个示例将单独一列定义为主键。  
  
```vb  
workTable.PrimaryKey = New DataColumn() {workTable.Columns("CustID")}  
  
' Or  
  
Dim columns(1) As DataColumn  
columns(0) = workTable.Columns("CustID")  
workTable.PrimaryKey = columns  
```  
  
```csharp  
workTable.PrimaryKey = new DataColumn[] {workTable.Columns["CustID"]};  
  
// Or  
  
DataColumn[] columns = new DataColumn[1];  
columns[0] = workTable.Columns["CustID"];  
workTable.PrimaryKey = columns;  
```  
  
 下面的示例将两列定义为主键。  
  
```vb  
workTable.PrimaryKey = New DataColumn() {workTable.Columns("CustLName"), _  
                                         workTable.Columns("CustFName")}  
  
' Or  
  
Dim keyColumn(2) As DataColumn  
keyColumn(0) = workTable.Columns("CustLName")  
keyColumn(1) = workTable.Columns("CustFName")  
workTable.PrimaryKey = keyColumn  
```  
  
```csharp  
workTable.PrimaryKey = new DataColumn[] {workTable.Columns["CustLName"],
                                         workTable.Columns["CustFName"]};  
  
// Or  
  
DataColumn[] keyColumn = new DataColumn[2];  
keyColumn[0] = workTable.Columns["CustLName"];  
keyColumn[1] = workTable.Columns["CustFName"];  
workTable.PrimaryKey = keyColumn;  
```  
  
## <a name="see-also"></a>请参阅

- <xref:System.Data.DataTable>
- [数据表架构定义](datatable-schema-definition.md)
- [DataTables](datatables.md)
- [ADO.NET 概述](../ado-net-overview.md)
