---
description: 了解详细信息： ADO.NET 中的数据类型映射
title: 数据类型映射
ms.date: 03/30/2017
ms.assetid: d4afab94-ada6-4c77-a73c-41f17bae6b5a
ms.openlocfilehash: c1829fdc2ebc053d1fd3a76e827a81e582572233
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786441"
---
# <a name="data-type-mappings-in-adonet"></a>ADO.NET 中的数据类型映射

.NET Framework 基于用于定义如何在运行时声明、使用和管理类型的通用类型系统。 它由值类型和引用类型组成，这两种类型均派生自 <xref:System.Object> 基类型。 使用数据源时，如果未显式指定数据类型，则从数据提供程序推断出它。 例如，<xref:System.Data.DataSet> 对象独立于任何特定的数据源。 `DataSet` 中的数据从数据源中进行检索，而更改则会使用 `DataAdapter` 持久保存回数据源。 这意味着当 `DataAdapter` <xref:System.Data.DataTable> 使用数据源中的值填充中的时 `DataSet` ，中列的结果数据类型 `DataTable` 为 .NET Framework 类型，而不是特定于用于连接到数据源的 .NET Framework 数据提供程序的类型。  
  
 同样，当 `DataReader` 从数据源返回值时，生成的值将存储在具有 .NET Framework 类型的局部变量中。 对于的 `Fill` 操作 `DataAdapter` 和的 `Get` 方法，将 `DataReader` 从 .NET Framework 数据提供程序返回的值推断 .NET Framework 类型。  
  
 当所返回值的特定类型已知时，可以使用 `DataReader` 的类型化访问器方法，而不是依靠推断出的数据类型。 类型化访问器方法无需进行额外的类型转换，即可将值作为特定的 .NET Framework 类型返回，从而提供更好的性能。  
  
> [!NOTE]
> .NET Framework 数据提供程序数据类型的 Null 值由表示 `DBNull.Value` 。  
  
## <a name="in-this-section"></a>本节内容  

 [SQL Server 数据类型映射](sql-server-data-type-mappings.md)  
 列出针对 <xref:System.Data.SqlClient> 的推断数据类型映射和数据访问器方法。  
  
 [OLE DB 数据类型映射](ole-db-data-type-mappings.md)  
 列出针对 <xref:System.Data.OleDb> 的推断数据类型映射和数据访问器方法。  
  
 [ODBC 数据类型映射](odbc-data-type-mappings.md)  
 列出针对 <xref:System.Data.Odbc> 的推断数据类型映射和数据访问器方法。  
  
 [Oracle 数据类型映射](oracle-data-type-mappings.md)  
 列出针对 <xref:System.Data.OracleClient> 的推断数据类型映射和数据访问器方法。  
  
 [浮点数](floating-point-numbers.md)  
 描述开发人员在使用浮点数时经常遇到的问题。  
  
## <a name="see-also"></a>另请参阅

- [SQL Server 数据类型和 ADO.NET](./sql/sql-server-data-types.md)
- [配置参数和参数数据类型](configuring-parameters-and-parameter-data-types.md)
- [检索数据库架构信息](retrieving-database-schema-information.md)
- [常规类型系统](../../../standard/base-types/common-type-system.md)
- [转换类型](/previous-versions/visualstudio/visual-studio-2008/t8s7t9bf(v=vs.90))
- [ADO.NET 概述](ado-net-overview.md)
