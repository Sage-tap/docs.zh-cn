---
description: 了解详细信息：复制数据集内容
title: 复制数据集内容
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
ms.openlocfilehash: 4b49ad367c96dd7c99363c7c4282930a6e4da37d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739685"
---
# <a name="copying-dataset-contents"></a><span data-ttu-id="ca2e7-103">复制数据集内容</span><span class="sxs-lookup"><span data-stu-id="ca2e7-103">Copying DataSet Contents</span></span>

<span data-ttu-id="ca2e7-104">您可以创建的副本， <xref:System.Data.DataSet> 以便在不影响原始数据的情况下处理数据，或使用数据 **集中** 的数据的子集。</span><span class="sxs-lookup"><span data-stu-id="ca2e7-104">You can create a copy of a <xref:System.Data.DataSet> so that you can work with data without affecting the original data, or work with a subset of the data from a **DataSet**.</span></span> <span data-ttu-id="ca2e7-105">复制 **数据集** 时，可以：</span><span class="sxs-lookup"><span data-stu-id="ca2e7-105">When copying a **DataSet**, you can:</span></span>  
  
- <span data-ttu-id="ca2e7-106">创建 **数据集** 的精确副本，包括架构、数据、行状态信息和行版本。</span><span class="sxs-lookup"><span data-stu-id="ca2e7-106">Create an exact copy of the **DataSet**, including the schema, data, row state information, and row versions.</span></span>  
  
- <span data-ttu-id="ca2e7-107">创建一个 **数据集，该数据集** 包含现有 **数据集** 的架构，而只包含已修改的行。</span><span class="sxs-lookup"><span data-stu-id="ca2e7-107">Create a **DataSet** that contains the schema of an existing **DataSet**, but only rows that have been modified.</span></span> <span data-ttu-id="ca2e7-108">可以返回所有已修改的行，也可以指定特定的 **DataRowState**。</span><span class="sxs-lookup"><span data-stu-id="ca2e7-108">You can return all rows that have been modified, or specify a specific **DataRowState**.</span></span> <span data-ttu-id="ca2e7-109">有关行状态的详细信息，请参阅 [行状态和行版本](row-states-and-row-versions.md)。</span><span class="sxs-lookup"><span data-stu-id="ca2e7-109">For more information about row states, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>  
  
- <span data-ttu-id="ca2e7-110">仅复制 **数据集** 的架构或关系结构，而不复制任何行。</span><span class="sxs-lookup"><span data-stu-id="ca2e7-110">Copy the schema, or relational structure, of the **DataSet** only, without copying any rows.</span></span> <span data-ttu-id="ca2e7-111">可以使用 <xref:System.Data.DataTable> 将行导入现有 <xref:System.Data.DataTable.ImportRow%2A>。</span><span class="sxs-lookup"><span data-stu-id="ca2e7-111">Rows can be imported into an existing <xref:System.Data.DataTable> using <xref:System.Data.DataTable.ImportRow%2A>.</span></span>  
  
 <span data-ttu-id="ca2e7-112">若要创建包含架构和数据的 **数据集** 的完全相同的副本，请使用 <xref:System.Data.DataSet.Copy%2A> **dataset** 的方法。</span><span class="sxs-lookup"><span data-stu-id="ca2e7-112">To create an exact copy of the **DataSet** that includes both schema and data, use the <xref:System.Data.DataSet.Copy%2A> method of the **DataSet**.</span></span> <span data-ttu-id="ca2e7-113">下面的代码示例演示如何创建 **数据集** 的精确副本。</span><span class="sxs-lookup"><span data-stu-id="ca2e7-113">The following code example shows how to create an exact copy of the **DataSet**.</span></span>  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 <span data-ttu-id="ca2e7-114">若要创建包含架构的数据 **集** 的副本，并且仅创建表示 **已添加**、 **已修改** 或 **已删除** 行的数据，请使用 <xref:System.Data.DataSet.GetChanges%2A> **数据集** 的方法。</span><span class="sxs-lookup"><span data-stu-id="ca2e7-114">To create a copy of a **DataSet** that includes schema and only the data representing **Added**, **Modified**, or **Deleted** rows, use the <xref:System.Data.DataSet.GetChanges%2A> method of the **DataSet**.</span></span> <span data-ttu-id="ca2e7-115">调用 **GetChanges** 时，还可以使用 **GetChanges** 来仅返回具有指定行状态的行 。</span><span class="sxs-lookup"><span data-stu-id="ca2e7-115">You can also use **GetChanges** to return only rows with a specified row state by passing a **DataRowState** value when calling **GetChanges**.</span></span> <span data-ttu-id="ca2e7-116">下面的代码示例演示如何在调用 **GetChanges** 时传递 **DataRowState** 。</span><span class="sxs-lookup"><span data-stu-id="ca2e7-116">The following code example shows how to pass a **DataRowState** when calling **GetChanges**.</span></span>  
  
```vb  
' Copy all changes.  
Dim changeDataSet As DataSet = customerDataSet.GetChanges()  
' Copy only new rows.  
Dim addedDataSetAs DataSet = _  
    customerDataSet.GetChanges(DataRowState.Added)  
```  
  
```csharp  
// Copy all changes.  
DataSet changeDataSet = customerDataSet.GetChanges();  
// Copy only new rows.  
DataSet addedDataSet= customerDataSet.GetChanges(DataRowState.Added);  
```  
  
 <span data-ttu-id="ca2e7-117">若要创建仅包含架构的 **数据集** 的副本，请使用 <xref:System.Data.DataSet.Clone%2A> **dataset** 的方法。</span><span class="sxs-lookup"><span data-stu-id="ca2e7-117">To create a copy of a **DataSet** that only includes schema, use the <xref:System.Data.DataSet.Clone%2A> method of the **DataSet**.</span></span> <span data-ttu-id="ca2e7-118">还可以使用 **DataTable** 的 **ImportRow** 方法将现有行添加到克隆的 **数据集**。</span><span class="sxs-lookup"><span data-stu-id="ca2e7-118">You can also add existing rows to the cloned **DataSet** using the **ImportRow** method of the **DataTable**.</span></span> <span data-ttu-id="ca2e7-119">**ImportRow** 将数据、行状态和行版本信息添加到指定的表中。</span><span class="sxs-lookup"><span data-stu-id="ca2e7-119">**ImportRow** adds data, row state, and row version information to the specified table.</span></span> <span data-ttu-id="ca2e7-120">只有当列名称匹配且数据类型兼容时，才会添加列值。</span><span class="sxs-lookup"><span data-stu-id="ca2e7-120">Column values are added only where the column name matches and the data type is compatible.</span></span>  
  
 <span data-ttu-id="ca2e7-121">下面的代码示例创建一个 **数据集** 的克隆，然后将原始 **数据集中** 的行添加到 "国家/地区"**克隆的**"**客户**" 表中的 "**国家/地区**" 列值为 "德国" 的客户。</span><span class="sxs-lookup"><span data-stu-id="ca2e7-121">The following code example creates a clone of a **DataSet** and then adds the rows from the original **DataSet** to the **Customers** table in the **DataSet** clone for customers where the **CountryRegion** column has the value "Germany".</span></span>  
  
```vb  
Dim customerDataSet As New DataSet  
        customerDataSet.Tables.Add(New DataTable("Customers"))  
        customerDataSet.Tables("Customers").Columns.Add("Name", GetType(String))  
        customerDataSet.Tables("Customers").Columns.Add("CountryRegion", GetType(String))  
        customerDataSet.Tables("Customers").Rows.Add("Juan", "Spain")  
        customerDataSet.Tables("Customers").Rows.Add("Johann", "Germany")  
        customerDataSet.Tables("Customers").Rows.Add("John", "UK")  
  
Dim germanyCustomers As DataSet = customerDataSet.Clone()  
  
Dim copyRows() As DataRow = _  
  customerDataSet.Tables("Customers").Select("CountryRegion = 'Germany'")  
  
Dim customerTable As DataTable = germanyCustomers.Tables("Customers")  
Dim copyRow As DataRow  
  
For Each copyRow In copyRows  
  customerTable.ImportRow(copyRow)  
Next  
```  
  
```csharp  
DataSet customerDataSet = new DataSet();  
customerDataSet.Tables.Add(new DataTable("Customers"));  
customerDataSet.Tables["Customers"].Columns.Add("Name", typeof(string));  
customerDataSet.Tables["Customers"].Columns.Add("CountryRegion", typeof(string));  
customerDataSet.Tables["Customers"].Rows.Add("Juan", "Spain");  
customerDataSet.Tables["Customers"].Rows.Add("Johann", "Germany");  
customerDataSet.Tables["Customers"].Rows.Add("John", "UK");  
  
DataSet germanyCustomers = customerDataSet.Clone();  
  
DataRow[] copyRows =
  customerDataSet.Tables["Customers"].Select("CountryRegion = 'Germany'");  
  
DataTable customerTable = germanyCustomers.Tables["Customers"];  
  
foreach (DataRow copyRow in copyRows)  
  customerTable.ImportRow(copyRow);  
```  
  
## <a name="see-also"></a><span data-ttu-id="ca2e7-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="ca2e7-122">See also</span></span>

- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="ca2e7-123">数据集、数据表和数据视图</span><span class="sxs-lookup"><span data-stu-id="ca2e7-123">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="ca2e7-124">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="ca2e7-124">ADO.NET Overview</span></span>](../ado-net-overview.md)
