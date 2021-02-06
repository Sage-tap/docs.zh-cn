---
description: 了解详细信息：检索二进制数据
title: 检索二进制数据
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 56c5a9e3-31f1-482f-bce0-ff1c41a658d0
ms.openlocfilehash: 4304dd19b8a861baf936686edb858d7cf4da5757
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99663438"
---
# <a name="retrieving-binary-data"></a><span data-ttu-id="07ba3-103">检索二进制数据</span><span class="sxs-lookup"><span data-stu-id="07ba3-103">Retrieving Binary Data</span></span>

<span data-ttu-id="07ba3-104">默认情况下，DataReader 在整个数据行可用时立即以行的形式加载传入数据。</span><span class="sxs-lookup"><span data-stu-id="07ba3-104">By default, the **DataReader** loads incoming data as a row as soon as an entire row of data is available.</span></span> <span data-ttu-id="07ba3-105">但是，对于二进制大对象 (BLOB) 则需要进行不同的处理，因为它们可能包含数十亿字节的数据，而单个行中无法包含如此多的数据。</span><span class="sxs-lookup"><span data-stu-id="07ba3-105">Binary large objects (BLOBs) need different treatment, however, because they can contain gigabytes of data that cannot be contained in a single row.</span></span> <span data-ttu-id="07ba3-106">Command.ExecuteReader 方法具有一个重载，它将采用 <xref:System.Data.CommandBehavior> 参数来修改 DataReader 的默认行为。</span><span class="sxs-lookup"><span data-stu-id="07ba3-106">The **Command.ExecuteReader** method has an overload that will take a <xref:System.Data.CommandBehavior> argument to modify the default behavior of the **DataReader**.</span></span> <span data-ttu-id="07ba3-107">可以将 <xref:System.Data.CommandBehavior.SequentialAccess> 传递到 ExecuteReader 方法来修改 DataReader 的默认行为，使其按照顺序在接收到数据时立即将其加载，而不是加载数据行。</span><span class="sxs-lookup"><span data-stu-id="07ba3-107">You can pass <xref:System.Data.CommandBehavior.SequentialAccess> to the **ExecuteReader** method to modify the default behavior of the **DataReader** so that instead of loading rows of data, it will load data sequentially as it is received.</span></span> <span data-ttu-id="07ba3-108">这是加载 BLOB 或其他大数据结构的理想方案。</span><span class="sxs-lookup"><span data-stu-id="07ba3-108">This is ideal for loading BLOBs or other large data structures.</span></span> <span data-ttu-id="07ba3-109">请注意，该行为可能会因数据源的不同而不同。</span><span class="sxs-lookup"><span data-stu-id="07ba3-109">Note that this behavior may depend on your data source.</span></span> <span data-ttu-id="07ba3-110">例如，从 Microsoft Access 中返回 BLOB 会将整个 BLOB 加载到内存中，而不是按照顺序在接收到数据时立即将其加载。</span><span class="sxs-lookup"><span data-stu-id="07ba3-110">For example, returning a BLOB from Microsoft Access will load the entire BLOB being loaded into memory, rather than sequentially as it is received.</span></span>  
  
 <span data-ttu-id="07ba3-111">在将 DataReader 设置为使用 SequentialAccess 时，务必要注意访问所返回字段的顺序。</span><span class="sxs-lookup"><span data-stu-id="07ba3-111">When setting the **DataReader** to use **SequentialAccess**, it is important to note the sequence in which you access the fields returned.</span></span> <span data-ttu-id="07ba3-112">DataReader 的默认行为是在整个行可用时立即加载该行，这样可以在读取下一行之前按任何顺序访问所返回的字段。</span><span class="sxs-lookup"><span data-stu-id="07ba3-112">The default behavior of the **DataReader**, which loads an entire row as soon as it is available, allows you to access the fields returned in any order until the next row is read.</span></span> <span data-ttu-id="07ba3-113">但是，当使用 SequentialAccess 时，必须按顺序访问由 DataReader 返回的字段。</span><span class="sxs-lookup"><span data-stu-id="07ba3-113">When using **SequentialAccess** however, you must access the fields returned by the **DataReader** in order.</span></span> <span data-ttu-id="07ba3-114">例如，如果查询返回三个列，其中第三列是 BLOB，则必须在访问第三个字段中的 BLOB 数据之前返回第一个和第二个字段的值。</span><span class="sxs-lookup"><span data-stu-id="07ba3-114">For example, if your query returns three columns, the third of which is a BLOB, you must return the values of the first and second fields before accessing the BLOB data in the third field.</span></span> <span data-ttu-id="07ba3-115">如果在访问第一个或第二个字段之前访问第三个字段，则第一个和第二个字段值将不再可用。</span><span class="sxs-lookup"><span data-stu-id="07ba3-115">If you access the third field before the first or second fields, the first and second field values are no longer available.</span></span> <span data-ttu-id="07ba3-116">这是因为 SequentialAccess 已修改 DataReader，使其按顺序返回数据，当 DataReader 已经读取超过特定数据时，该数据将不可用。</span><span class="sxs-lookup"><span data-stu-id="07ba3-116">This is because **SequentialAccess** has modified the **DataReader** to return data in sequence and the data is not available after the **DataReader** has read past it.</span></span>  
  
 <span data-ttu-id="07ba3-117">在访问 BLOB 字段中的数据时，请使用 DataReader 的 GetBytes 或 GetChars 类型化访问器，它们将用数据来填充数组。</span><span class="sxs-lookup"><span data-stu-id="07ba3-117">When accessing the data in the BLOB field, use the **GetBytes** or **GetChars** typed accessors of the **DataReader**, which fill an array with data.</span></span> <span data-ttu-id="07ba3-118">还可以对字符数据使用 **GetString** ;尽管如此.</span><span class="sxs-lookup"><span data-stu-id="07ba3-118">You can also use **GetString** for character data; however.</span></span> <span data-ttu-id="07ba3-119">为了节省系统资源，您可能不希望将整个 BLOB 值加载到单个字符串变量中。</span><span class="sxs-lookup"><span data-stu-id="07ba3-119">to conserve system resources you might not want to load an entire BLOB value into a single string variable.</span></span> <span data-ttu-id="07ba3-120">您可以指定要返回的特定数据缓冲区大小，以及从返回的数据中读取的第一个字节或字符的起始位置。</span><span class="sxs-lookup"><span data-stu-id="07ba3-120">You can instead specify a specific buffer size of data to be returned, and a starting location for the first byte or character to be read from the returned data.</span></span> <span data-ttu-id="07ba3-121">GetBytes 和 GetChars 将返回一个 `long` 值，它表示返回的字节或字符数。</span><span class="sxs-lookup"><span data-stu-id="07ba3-121">**GetBytes** and **GetChars** will return a `long` value, which represents the number of bytes or characters returned.</span></span> <span data-ttu-id="07ba3-122">如果将一个空数组传递给 GetBytes 或 GetChars，则返回的长值将是 BLOB 中字节或字符的总数。</span><span class="sxs-lookup"><span data-stu-id="07ba3-122">If you pass a null array to **GetBytes** or **GetChars**, the long value returned will be the total number of bytes or characters in the BLOB.</span></span> <span data-ttu-id="07ba3-123">您可以选择将数组中的某个索引指定为所读取数据的起始位置。</span><span class="sxs-lookup"><span data-stu-id="07ba3-123">You can optionally specify an index in the array as a starting position for the data being read.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07ba3-124">示例</span><span class="sxs-lookup"><span data-stu-id="07ba3-124">Example</span></span>  

 <span data-ttu-id="07ba3-125">下面的示例从 Microsoft SQL Server 中的 **pubs** 示例数据库返回发行者 ID 和徽标。</span><span class="sxs-lookup"><span data-stu-id="07ba3-125">The following example returns the publisher ID and logo from the **pubs** sample database in Microsoft SQL Server.</span></span> <span data-ttu-id="07ba3-126">发行者 ID (`pub_id`) 是字符字段，而徽标则是图像，属于 BLOB。</span><span class="sxs-lookup"><span data-stu-id="07ba3-126">The publisher ID (`pub_id`) is a character field, and the logo is an image, which is a BLOB.</span></span> <span data-ttu-id="07ba3-127">由于 logo 字段是位图，因此该示例使用 GetBytes 返回二进制数据。</span><span class="sxs-lookup"><span data-stu-id="07ba3-127">Because the **logo** field is a bitmap, the example returns binary data using **GetBytes**.</span></span> <span data-ttu-id="07ba3-128">请注意，由于必须按顺序访问字段，所以将在访问徽标之前访问当前数据行的发行者 ID。</span><span class="sxs-lookup"><span data-stu-id="07ba3-128">Notice that the publisher ID is accessed for the current row of data before the logo, because the fields must be accessed sequentially.</span></span>  
  
```vb  
' Assumes that connection is a valid SqlConnection object.  
Dim command As SqlCommand = New SqlCommand( _  
  "SELECT pub_id, logo FROM pub_info", connection)  
  
' Writes the BLOB to a file (*.bmp).  
Dim stream As FileStream
' Streams the binary data to the FileStream object.  
Dim writer As BinaryWriter
' The size of the BLOB buffer.  
Dim bufferSize As Integer = 100
' The BLOB byte() buffer to be filled by GetBytes.  
Dim outByte(bufferSize - 1) As Byte
' The bytes returned from GetBytes.  
Dim retval As Long
' The starting position in the BLOB output.  
Dim startIndex As Long = 0
  
' The publisher id to use in the file name.  
Dim pubID As String = ""
  
' Open the connection and read data into the DataReader.  
connection.Open()  
Dim reader As SqlDataReader = command.ExecuteReader(CommandBehavior.SequentialAccess)  
  
Do While reader.Read()  
  ' Get the publisher id, which must occur before getting the logo.  
  pubID = reader.GetString(0)  
  
  ' Create a file to hold the output.  
  stream = New FileStream( _  
    "logo" & pubID & ".bmp", FileMode.OpenOrCreate, FileAccess.Write)  
  writer = New BinaryWriter(stream)  
  
  ' Reset the starting byte for a new BLOB.  
  startIndex = 0  
  
  ' Read bytes into outByte() and retain the number of bytes returned.  
  retval = reader.GetBytes(1, startIndex, outByte, 0, bufferSize)  
  
  ' Continue while there are bytes beyond the size of the buffer.  
  Do While retval = bufferSize  
    writer.Write(outByte)  
    writer.Flush()  
  
    ' Reposition start index to end of the last buffer and fill buffer.  
    startIndex += bufferSize  
    retval = reader.GetBytes(1, startIndex, outByte, 0, bufferSize)  
  Loop  
  
  ' Write the remaining buffer.  
  writer.Write(outByte, 0 , retval - 1)  
  writer.Flush()  
  
  ' Close the output file.  
  writer.Close()  
  stream.Close()  
Loop  
  
' Close the reader and the connection.  
reader.Close()  
connection.Close()  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection object.  
SqlCommand command = new SqlCommand(  
  "SELECT pub_id, logo FROM pub_info", connection);  
  
// Writes the BLOB to a file (*.bmp).  
FileStream stream;
// Streams the BLOB to the FileStream object.  
BinaryWriter writer;
  
// Size of the BLOB buffer.  
int bufferSize = 100;
// The BLOB byte[] buffer to be filled by GetBytes.  
byte[] outByte = new byte[bufferSize];
// The bytes returned from GetBytes.  
long retval;
// The starting position in the BLOB output.  
long startIndex = 0;
  
// The publisher id to use in the file name.  
string pubID = "";
  
// Open the connection and read data into the DataReader.  
connection.Open();  
SqlDataReader reader = command.ExecuteReader(CommandBehavior.SequentialAccess);  
  
while (reader.Read())  
{  
  // Get the publisher id, which must occur before getting the logo.  
  pubID = reader.GetString(0);
  
  // Create a file to hold the output.  
  stream = new FileStream(  
    "logo" + pubID + ".bmp", FileMode.OpenOrCreate, FileAccess.Write);  
  writer = new BinaryWriter(stream);  
  
  // Reset the starting byte for the new BLOB.  
  startIndex = 0;  
  
  // Read bytes into outByte[] and retain the number of bytes returned.  
  retval = reader.GetBytes(1, startIndex, outByte, 0, bufferSize);  
  
  // Continue while there are bytes beyond the size of the buffer.  
  while (retval == bufferSize)  
  {  
    writer.Write(outByte);  
    writer.Flush();  
  
    // Reposition start index to end of last buffer and fill buffer.  
    startIndex += bufferSize;  
    retval = reader.GetBytes(1, startIndex, outByte, 0, bufferSize);  
  }  
  
  // Write the remaining buffer.  
  writer.Write(outByte, 0, (int)retval);  
  writer.Flush();  
  
  // Close the output file.  
  writer.Close();  
  stream.Close();  
}  
  
// Close the reader and the connection.  
reader.Close();  
connection.Close();  
```  
  
## <a name="see-also"></a><span data-ttu-id="07ba3-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="07ba3-129">See also</span></span>

- [<span data-ttu-id="07ba3-130">SQL Server 二进制和大值数据</span><span class="sxs-lookup"><span data-stu-id="07ba3-130">SQL Server Binary and Large-Value Data</span></span>](./sql/sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="07ba3-131">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="07ba3-131">ADO.NET Overview</span></span>](ado-net-overview.md)
