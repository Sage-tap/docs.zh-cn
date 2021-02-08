---
description: 了解详细信息：用存储过程修改数据
title: 使用存储过程修改数据
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7d8e9a46-1af6-4a02-bf61-969d77ae07e0
ms.openlocfilehash: 66a4aa9577c71605bde0152a142a65dfa81a31d7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786220"
---
# <a name="modifying-data-with-stored-procedures"></a><span data-ttu-id="fc6c7-103">使用存储过程修改数据</span><span class="sxs-lookup"><span data-stu-id="fc6c7-103">Modifying Data with Stored Procedures</span></span>

<span data-ttu-id="fc6c7-104">存储过程可以接受数据作为输入参数并可以返回数据作为输出参数、结果集或返回值。</span><span class="sxs-lookup"><span data-stu-id="fc6c7-104">Stored procedures can accept data as input parameters and can return data as output parameters, result sets, or return values.</span></span> <span data-ttu-id="fc6c7-105">下面的示例演示 ADO.NET 如何发送和接收输入参数、输出参数及返回值。</span><span class="sxs-lookup"><span data-stu-id="fc6c7-105">The sample below illustrates how ADO.NET sends and receives input parameters, output parameters, and return values.</span></span> <span data-ttu-id="fc6c7-106">该示例将一条新记录插入到一个表中，该表中的主键列为 SQL Server 数据库中的标识列。</span><span class="sxs-lookup"><span data-stu-id="fc6c7-106">The example inserts a new record into a table where the primary key column is an identity column in a SQL Server database.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fc6c7-107">如果您要通过 SQL Server 存储过程使用 <xref:System.Data.SqlClient.SqlDataAdapter> 来编辑或删除数据，请确保不要在存储过程定义中使用 SET NOCOUNT ON。</span><span class="sxs-lookup"><span data-stu-id="fc6c7-107">If you are using SQL Server stored procedures to edit or delete data using a <xref:System.Data.SqlClient.SqlDataAdapter>, make sure that you do not use SET NOCOUNT ON in the stored procedure definition.</span></span> <span data-ttu-id="fc6c7-108">这将使返回的受影响的行数为零，`DataAdapter` 会将其解释为并发冲突。</span><span class="sxs-lookup"><span data-stu-id="fc6c7-108">This causes the rows affected count returned to be zero, which the `DataAdapter` interprets as a concurrency conflict.</span></span> <span data-ttu-id="fc6c7-109">在这种情况下，将引发 <xref:System.Data.DBConcurrencyException>。</span><span class="sxs-lookup"><span data-stu-id="fc6c7-109">In this event, a <xref:System.Data.DBConcurrencyException> will be thrown.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc6c7-110">示例</span><span class="sxs-lookup"><span data-stu-id="fc6c7-110">Example</span></span>  

 <span data-ttu-id="fc6c7-111">此示例使用以下存储过程将一个新类别插入到 Northwind“类别”表。</span><span class="sxs-lookup"><span data-stu-id="fc6c7-111">The sample uses the following stored procedure to insert a new category into the **Northwind** **Categories** table.</span></span> <span data-ttu-id="fc6c7-112">该存储过程采用 "列 **名称** " 列中的值作为输入参数，并使用 SCOPE_IDENTITY ( # A1 函数检索标识字段的新值 " **类别 id**"，并在输出参数中将其返回。</span><span class="sxs-lookup"><span data-stu-id="fc6c7-112">The stored procedure takes the value in the **CategoryName** column as an input parameter and uses the SCOPE_IDENTITY() function to retrieve the new value of the identity field, **CategoryID**, and return it in an output parameter.</span></span> <span data-ttu-id="fc6c7-113">RETURN 语句使用 @ @ROWCOUNT 函数返回插入的行数。</span><span class="sxs-lookup"><span data-stu-id="fc6c7-113">The RETURN statement uses the @@ROWCOUNT function to return the number of rows inserted.</span></span>  
  
```sql
CREATE PROCEDURE dbo.InsertCategory  
  @CategoryName nvarchar(15),  
  @Identity int OUT  
AS  
INSERT INTO Categories (CategoryName) VALUES(@CategoryName)  
SET @Identity = SCOPE_IDENTITY()  
RETURN @@ROWCOUNT  
```  
  
 <span data-ttu-id="fc6c7-114">下面的代码示例使用上面显示的 `InsertCategory` 存储过程作为 <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> 的 <xref:System.Data.SqlClient.SqlDataAdapter> 的来源。</span><span class="sxs-lookup"><span data-stu-id="fc6c7-114">The following code example uses the `InsertCategory` stored procedure shown above as the source for the <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> of the <xref:System.Data.SqlClient.SqlDataAdapter>.</span></span> <span data-ttu-id="fc6c7-115">如果在将记录插入到数据库后调用 `@Identity` 的 <xref:System.Data.DataSet> 方法，`Update` 中将会反映出 <xref:System.Data.SqlClient.SqlDataAdapter> 输出参数。</span><span class="sxs-lookup"><span data-stu-id="fc6c7-115">The `@Identity` output parameter will be reflected in the <xref:System.Data.DataSet> after the record has been inserted into the database when the `Update` method of the <xref:System.Data.SqlClient.SqlDataAdapter> is called.</span></span> <span data-ttu-id="fc6c7-116">此代码还会检索返回值。</span><span class="sxs-lookup"><span data-stu-id="fc6c7-116">The code also retrieves the return value.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fc6c7-117">使用时 <xref:System.Data.OleDb.OleDbDataAdapter> ，必须在 <xref:System.Data.ParameterDirection> 其他参数之前指定带有 **ReturnValue** 的参数。</span><span class="sxs-lookup"><span data-stu-id="fc6c7-117">When using the <xref:System.Data.OleDb.OleDbDataAdapter>, you must specify parameters with a <xref:System.Data.ParameterDirection> of **ReturnValue** before the other parameters.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="fc6c7-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fc6c7-118">See also</span></span>

- [<span data-ttu-id="fc6c7-119">在 ADO.NET 中检索和修改数据</span><span class="sxs-lookup"><span data-stu-id="fc6c7-119">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="fc6c7-120">DataAdapter 和 DataReader</span><span class="sxs-lookup"><span data-stu-id="fc6c7-120">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="fc6c7-121">执行命令</span><span class="sxs-lookup"><span data-stu-id="fc6c7-121">Executing a Command</span></span>](executing-a-command.md)
- [<span data-ttu-id="fc6c7-122">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="fc6c7-122">ADO.NET Overview</span></span>](ado-net-overview.md)
