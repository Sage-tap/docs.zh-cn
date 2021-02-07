---
description: 了解详细信息：更新数据源中的数据
title: 更新数据源中的数据
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 55c545e5-dcd5-4323-a5b9-3825c2157462
ms.openlocfilehash: a55d6a53f4607908fa279474419803eac3963909
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99766564"
---
# <a name="updating-data-in-a-data-source"></a><span data-ttu-id="287ae-103">更新数据源中的数据</span><span class="sxs-lookup"><span data-stu-id="287ae-103">Updating Data in a Data Source</span></span>

<span data-ttu-id="287ae-104">修改数据的 SQL 语句（如 INSERT、UPDATE 或 DELETE）不返回行。</span><span class="sxs-lookup"><span data-stu-id="287ae-104">SQL statements that modify data (such as INSERT, UPDATE, or DELETE) do not return rows.</span></span> <span data-ttu-id="287ae-105">同样，许多存储过程执行操作但不返回行。</span><span class="sxs-lookup"><span data-stu-id="287ae-105">Similarly, many stored procedures perform an action but do not return rows.</span></span> <span data-ttu-id="287ae-106">要执行不返回行的命令，使用相应 SQL 命令创建一个 Command 对象，并创建一个 Connection，包括所有必需的 Parameters。</span><span class="sxs-lookup"><span data-stu-id="287ae-106">To execute commands that do not return rows, create a **Command** object with the appropriate SQL command and a **Connection**, including any required **Parameters**.</span></span> <span data-ttu-id="287ae-107">通过 **命令** 对象的 **ExecuteNonQuery** 方法执行该命令。</span><span class="sxs-lookup"><span data-stu-id="287ae-107">Execute the command with the **ExecuteNonQuery** method of the **Command** object.</span></span>  
  
 <span data-ttu-id="287ae-108">ExecuteNonQuery 方法返回一个整数，表示受已执行的语句或存储过程影响的行数。</span><span class="sxs-lookup"><span data-stu-id="287ae-108">The **ExecuteNonQuery** method returns an integer that represents the number of rows affected by the statement or stored procedure that was executed.</span></span> <span data-ttu-id="287ae-109">如果执行了多个语句，则返回的值为受所有已执行语句影响的记录的总数。</span><span class="sxs-lookup"><span data-stu-id="287ae-109">If multiple statements are executed, the value returned is the sum of the records affected by all of the statements executed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="287ae-110">示例</span><span class="sxs-lookup"><span data-stu-id="287ae-110">Example</span></span>  

 <span data-ttu-id="287ae-111">以下代码示例执行一个 INSERT 语句，以使用 ExecuteNonQuery 将一个记录插入数据库中。</span><span class="sxs-lookup"><span data-stu-id="287ae-111">The following code example executes an INSERT statement to insert a record into a database using **ExecuteNonQuery**.</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
connection.Open()  
  
Dim queryString As String = "INSERT INTO Customers " & _  
  "(CustomerID, CompanyName) Values('NWIND', 'Northwind Traders')"  
  
Dim command As SqlCommand = New SqlCommand(queryString, connection)  
Dim recordsAffected As Int32 = command.ExecuteNonQuery()  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
connection.Open();  
  
string queryString = "INSERT INTO Customers " +  
  "(CustomerID, CompanyName) Values('NWIND', 'Northwind Traders')";  
  
SqlCommand command = new SqlCommand(queryString, connection);  
Int32 recordsAffected = command.ExecuteNonQuery();  
```  
  
 <span data-ttu-id="287ae-112">以下代码示例执行由[执行编录操作](performing-catalog-operations.md)中的示例代码创建的存储过程。</span><span class="sxs-lookup"><span data-stu-id="287ae-112">The following code example executes the stored procedure created by the sample code in [Performing Catalog Operations](performing-catalog-operations.md).</span></span> <span data-ttu-id="287ae-113">该存储过程没有返回任何行，因此将使用 ExecuteNonQuery 方法，但该存储过程会接收输入参数并返回输出参数和返回值。</span><span class="sxs-lookup"><span data-stu-id="287ae-113">No rows are returned by the stored procedure, so the **ExecuteNonQuery** method is used, but the stored procedure does receive an input parameter and returns an output parameter and a return value.</span></span>  
  
 <span data-ttu-id="287ae-114">对于 <xref:System.Data.OleDb.OleDbCommand> 对象，必须先将 **ReturnValue** 参数添加到 **Parameters** 集合。</span><span class="sxs-lookup"><span data-stu-id="287ae-114">For the <xref:System.Data.OleDb.OleDbCommand> object, the **ReturnValue** parameter must be added to the **Parameters** collection first.</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim command As SqlCommand = _  
   New SqlCommand("InsertCategory" , connection)  
command.CommandType = CommandType.StoredProcedure  
  
Dim parameter As SqlParameter = _  
 command.Parameters.Add("@RowCount", SqlDbType.Int)  
parameter.Direction = ParameterDirection.ReturnValue  
  
parameter = command.Parameters.Add( _  
  "@CategoryName", SqlDbType.NChar, 15)  
  
parameter = command.Parameters.Add("@Identity", SqlDbType.Int)  
parameter.Direction = ParameterDirection.Output  
  
command.Parameters("@CategoryName").Value = "New Category"  
command.ExecuteNonQuery()  
  
Dim categoryID As Int32 = CInt(command.Parameters("@Identity").Value)  
Dim rowCount As Int32 = CInt(command.Parameters("@RowCount").Value)
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
SqlCommand command = new SqlCommand("InsertCategory" , connection);  
command.CommandType = CommandType.StoredProcedure;  
  
SqlParameter parameter = command.Parameters.Add(  
  "@RowCount", SqlDbType.Int);  
parameter.Direction = ParameterDirection.ReturnValue;  
  
parameter = command.Parameters.Add(  
  "@CategoryName", SqlDbType.NChar, 15);  
  
parameter = command.Parameters.Add("@Identity", SqlDbType.Int);  
parameter.Direction = ParameterDirection.Output;  
  
command.Parameters["@CategoryName"].Value = "New Category";  
command.ExecuteNonQuery();  
  
Int32 categoryID = (Int32) command.Parameters["@Identity"].Value;  
Int32 rowCount = (Int32) command.Parameters["@RowCount"].Value;  
```  
  
## <a name="see-also"></a><span data-ttu-id="287ae-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="287ae-115">See also</span></span>

- [<span data-ttu-id="287ae-116">使用命令修改数据</span><span class="sxs-lookup"><span data-stu-id="287ae-116">Using Commands to Modify Data</span></span>](using-commands-to-modify-data.md)
- [<span data-ttu-id="287ae-117">使用 DataAdapter 更新数据源</span><span class="sxs-lookup"><span data-stu-id="287ae-117">Updating Data Sources with DataAdapters</span></span>](updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="287ae-118">命令和参数</span><span class="sxs-lookup"><span data-stu-id="287ae-118">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="287ae-119">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="287ae-119">ADO.NET Overview</span></span>](ado-net-overview.md)
