---
description: 了解详细信息： Oracle Bfile
title: Oracle BFILE
ms.date: 03/30/2017
ms.assetid: 341bbf84-4734-4d44-8723-ccedee954e21
ms.openlocfilehash: e1fda4ad4acb225dc9a70c92b2c4f2b1d61ab1d7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99672486"
---
# <a name="oracle-bfiles"></a><span data-ttu-id="83081-103">Oracle BFILE</span><span class="sxs-lookup"><span data-stu-id="83081-103">Oracle BFILEs</span></span>

<span data-ttu-id="83081-104">Oracle .NET Framework 数据提供程序包括 <xref:System.Data.OracleClient.OracleBFile> 类，该类用于使用 Oracle <xref:System.Data.OracleClient.OracleType.BFile> 数据类型。</span><span class="sxs-lookup"><span data-stu-id="83081-104">The .NET Framework Data Provider for Oracle includes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle <xref:System.Data.OracleClient.OracleType.BFile> data type.</span></span>  
  
 <span data-ttu-id="83081-105">Oracle **BFILE** 数据类型是一种 oracle **LOB** 数据类型，包含对二进制数据的引用，其最大大小为 4 gb。</span><span class="sxs-lookup"><span data-stu-id="83081-105">The Oracle **BFILE** data type is an Oracle **LOB** data type that contains a reference to binary data with a maximum size of 4 gigabytes.</span></span> <span data-ttu-id="83081-106">Oracle **BFILE** 不同于其他 oracle **LOB** 数据类型，因为它的数据存储在操作系统而不是服务器上的物理文件中。</span><span class="sxs-lookup"><span data-stu-id="83081-106">An Oracle **BFILE** differs from other Oracle **LOB** data types in that its data is stored in a physical file in the operating system instead of on the server.</span></span> <span data-ttu-id="83081-107">请注意， **BFILE** 数据类型提供对数据的只读访问。</span><span class="sxs-lookup"><span data-stu-id="83081-107">Note that the **BFILE** data type provides read-only access to data.</span></span>  
  
 <span data-ttu-id="83081-108">**BFILE** 数据类型的其他特性可以将其与 **LOB** 数据类型区分开来：</span><span class="sxs-lookup"><span data-stu-id="83081-108">Other characteristics of a **BFILE** data type that distinguish it from a **LOB** data type are that it:</span></span>  
  
- <span data-ttu-id="83081-109">包含非结构化数据。</span><span class="sxs-lookup"><span data-stu-id="83081-109">Contains unstructured data.</span></span>  
  
- <span data-ttu-id="83081-110">支持服务器端分块。</span><span class="sxs-lookup"><span data-stu-id="83081-110">Supports server-side chunking.</span></span>  
  
- <span data-ttu-id="83081-111">使用引用复制语义。</span><span class="sxs-lookup"><span data-stu-id="83081-111">Uses reference copy semantics.</span></span> <span data-ttu-id="83081-112">例如，如果您在 **bfile** 上执行复制操作，则只会复制 (为对文件) 的引用的 **BFILE** 定位符。</span><span class="sxs-lookup"><span data-stu-id="83081-112">For example, if you perform a copy operation on a **BFILE**, only the **BFILE** locator (which is a reference to the file) is copied.</span></span> <span data-ttu-id="83081-113">而不会复制文件中的数据。</span><span class="sxs-lookup"><span data-stu-id="83081-113">The data in the file is not copied.</span></span>  
  
 <span data-ttu-id="83081-114">**BFILE** 数据类型应用于引用大小较大的 lob，因此，不能在数据库中存储。</span><span class="sxs-lookup"><span data-stu-id="83081-114">The **BFILE** data type should be used for referencing LOBs that are large in size, and therefore, not practical to store in the database.</span></span> <span data-ttu-id="83081-115">与 **LOB** 数据类型相比，使用 **BFILE** 数据类型时，会涉及更多的客户端、服务器和通信开销。</span><span class="sxs-lookup"><span data-stu-id="83081-115">More client, server, and communication overhead is involved when using a **BFILE** data type compared with the **LOB** data type.</span></span> <span data-ttu-id="83081-116">如果只需获取少量的数据，则访问 **BFILE** 会更有效。</span><span class="sxs-lookup"><span data-stu-id="83081-116">It is more efficient to access a **BFILE** if you only need to obtain a small amount of data.</span></span> <span data-ttu-id="83081-117">如果需要获取整个对象，访问数据库驻留的 LOB 会更加有效。</span><span class="sxs-lookup"><span data-stu-id="83081-117">It is more efficient to access database-resident LOBs if you need to obtain the entire object.</span></span>  
  
 <span data-ttu-id="83081-118">每个非 NULL **OracleBFile** 对象都与定义基础物理文件位置的两个实体相关联：</span><span class="sxs-lookup"><span data-stu-id="83081-118">Each non-NULL **OracleBFile** object is associated with two entities that define the location of the underlying physical file:</span></span>  
  
1. <span data-ttu-id="83081-119">一个 Oracle DIRECTORY 对象，它是文件系统中一个目录的数据库别名，以及</span><span class="sxs-lookup"><span data-stu-id="83081-119">An Oracle DIRECTORY object, which is a database alias for a directory in the file system, and</span></span>  
  
2. <span data-ttu-id="83081-120">基础物理文件的文件名，它位于与 DIRECTORY 对象关联的目录中。</span><span class="sxs-lookup"><span data-stu-id="83081-120">The file name of the underlying physical file, which is located in the directory associated with the DIRECTORY object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83081-121">示例</span><span class="sxs-lookup"><span data-stu-id="83081-121">Example</span></span>  

 <span data-ttu-id="83081-122">下面的 c # 示例演示如何在 Oracle 表中创建 **BFILE** ，然后以 **OracleBFile** 对象的形式检索它。</span><span class="sxs-lookup"><span data-stu-id="83081-122">The following C# example demonstrates how you can create a **BFILE** in an Oracle table and then retrieve it in the form of an **OracleBFile** object.</span></span> <span data-ttu-id="83081-123">该示例演示如何使用 <xref:System.Data.OracleClient.OracleDataReader> 对象以及 **OracleBFile** **Seek** 和 **Read** 方法。</span><span class="sxs-lookup"><span data-stu-id="83081-123">The example demonstrates using the <xref:System.Data.OracleClient.OracleDataReader> object and the **OracleBFile** **Seek** and **Read** methods.</span></span> <span data-ttu-id="83081-124">请注意，若要使用此示例，必须先在 Oracle 服务器上创建一个名为 "c： \\ \bfiles" 的目录和一个名为 "MyFile.jpg" 的文件。</span><span class="sxs-lookup"><span data-stu-id="83081-124">Note that in order to use this sample, you must first create a directory named "c:\\\bfiles" and file named "MyFile.jpg" on the Oracle server.</span></span>  
  
```csharp  
using System;  
using System.IO;  
using System.Data;  
using System.Data.OracleClient;  
  
public class Sample  
{  
   public static void Main(string[] args)  
   {  
      OracleConnection connection = new OracleConnection(  
        "Data Source=Oracle8i;Integrated Security=yes");  
      connection.Open();  
  
      OracleCommand command = connection.CreateCommand();  
      command.CommandText =
        "CREATE or REPLACE DIRECTORY MyDir as 'c:\\bfiles'";  
      command.ExecuteNonQuery();  
      command.CommandText =
        "DROP TABLE MyBFileTable";  
      try {  
        command.ExecuteNonQuery();  
      }  
      catch {  
      }  
      command.CommandText =
        "CREATE TABLE MyBFileTable(col1 number, col2 BFILE)";  
      command.ExecuteNonQuery();  
      command.CommandText =
        "INSERT INTO MyBFileTable values ('2', BFILENAME('MyDir', " +  
        "'MyFile.jpg'))";  
      command.ExecuteNonQuery();  
      command.CommandText = "SELECT * FROM MyBFileTable";  
  
        byte[] buffer = new byte[100];  
  
      OracleDataReader reader = command.ExecuteReader();  
      using (reader) {  
          if (reader.Read()) {  
                OracleBFile bFile = reader.GetOracleBFile(1);  
                using (bFile) {  
                  bFile.Seek(0, SeekOrigin.Begin);  
                  bFile.Read(buffer, 0, 100);  
              }  
          }  
      }  
  
      connection.Close();  
   }  
  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="83081-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="83081-125">See also</span></span>

- [<span data-ttu-id="83081-126">Oracle 和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="83081-126">Oracle and ADO.NET</span></span>](oracle-and-adonet.md)
- [<span data-ttu-id="83081-127">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="83081-127">ADO.NET Overview</span></span>](ado-net-overview.md)
