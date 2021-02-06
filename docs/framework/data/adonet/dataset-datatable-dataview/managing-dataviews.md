---
description: 了解详细信息：管理 Dataview
title: 管理 DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b67fab5-1722-4d2b-bfc1-247a75f0f1ee
ms.openlocfilehash: cdd9da9c4f67321dba36d22610704fc2e2561930
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652089"
---
# <a name="managing-dataviews"></a><span data-ttu-id="9b98d-103">管理 DataView</span><span class="sxs-lookup"><span data-stu-id="9b98d-103">Managing DataViews</span></span>

<span data-ttu-id="9b98d-104">可以使用 <xref:System.Data.DataViewManager> 来管理 <xref:System.Data.DataView> 中所有表的视图设置。</span><span class="sxs-lookup"><span data-stu-id="9b98d-104">You can use a <xref:System.Data.DataViewManager> to manage view settings for all the tables in a <xref:System.Data.DataView>.</span></span> <span data-ttu-id="9b98d-105">如果你有一个要绑定到多个表的控件，例如导航关系的网格， **DataViewManager** 是理想的选择。</span><span class="sxs-lookup"><span data-stu-id="9b98d-105">If you have a control that you want to bind to multiple tables, such as a grid that navigates relationships, a **DataViewManager** is ideal.</span></span>  
  
 <span data-ttu-id="9b98d-106">**DataViewManager** 包含 <xref:System.Data.DataViewSetting> 对象的集合，这些对象用于设置中的表的视图设置 <xref:System.Data.DataSet> 。</span><span class="sxs-lookup"><span data-stu-id="9b98d-106">The **DataViewManager** contains a collection of <xref:System.Data.DataViewSetting> objects that are used to set the view setting of the tables in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="9b98d-107"><xref:System.Data.DataViewSettingCollection> <xref:System.Data.DataViewSetting> 对于 **数据集中** 的每个表，都包含一个对象。</span><span class="sxs-lookup"><span data-stu-id="9b98d-107">The <xref:System.Data.DataViewSettingCollection> contains one <xref:System.Data.DataViewSetting> object for each table in a **DataSet**.</span></span> <span data-ttu-id="9b98d-108">可以通过使用引用表的 **DataViewSetting** 来设置其默认的 **ApplyDefaultSort**、 **Sort**、 **RowFilter** 和 **RowStateFilter** 属性。</span><span class="sxs-lookup"><span data-stu-id="9b98d-108">You can set the default **ApplyDefaultSort**, **Sort**, **RowFilter**, and **RowStateFilter** properties of the referenced table by using its **DataViewSetting**.</span></span> <span data-ttu-id="9b98d-109">可以按名称或序号引用引用特定表的 **DataViewSetting** ，也可以通过传递对该特定表对象的引用来引用。</span><span class="sxs-lookup"><span data-stu-id="9b98d-109">You can reference the **DataViewSetting** for a particular table by name or ordinal reference, or by passing a reference to that specific table object.</span></span> <span data-ttu-id="9b98d-110">可以通过使用 **DataViewSettings** 属性来访问 **DataViewManager** 中的 **DataViewSetting** 对象集合。</span><span class="sxs-lookup"><span data-stu-id="9b98d-110">You can access the collection of **DataViewSetting** objects in a **DataViewManager** by using the **DataViewSettings** property.</span></span>  
  
 <span data-ttu-id="9b98d-111">下面 **的代码示例使用 SQL Server** **Northwind** 数据库表 **客户**、 **订单** 和 **订单详细信息**，创建表之间的关系，使用 **DataViewManager** 设置默认 **DataView** 设置，并将 **DataGrid** 绑定到 **DataViewManager**。</span><span class="sxs-lookup"><span data-stu-id="9b98d-111">The following code example fills a **DataSet** with the SQL Server **Northwind** database tables **Customers**, **Orders**, and **Order Details**, creates the relationships between the tables, uses a **DataViewManager** to set default **DataView** settings, and binds a **DataGrid** to the **DataViewManager**.</span></span> <span data-ttu-id="9b98d-112">该示例将 **数据集中** 所有表的默认 **DataView** 设置设为按表的主键进行排序， (**ApplyDefaultSort**  =  **true**) ，然后修改 **Customers** 表的排序顺序按 "**公司名称**" 排序。</span><span class="sxs-lookup"><span data-stu-id="9b98d-112">The example sets the default **DataView** settings for all tables in the **DataSet** to sort by the primary key of the table (**ApplyDefaultSort** = **true**), and then modifies the sort order of the **Customers** table to sort by **CompanyName**.</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection to Northwind.  
' Create a Connection, DataAdapters, and a DataSet.  
Dim custDA As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers", connection)  
Dim orderDA As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT OrderID, CustomerID FROM Orders", connection)  
Dim ordDetDA As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT OrderID, ProductID, Quantity FROM [Order Details]", connection)  
  
Dim custDS As DataSet = New DataSet()  
  
' Open the Connection.  
connection.Open()  
  
    ' Fill the DataSet with schema information and data.  
    custDA.MissingSchemaAction = MissingSchemaAction.AddWithKey  
    orderDA.MissingSchemaAction = MissingSchemaAction.AddWithKey  
    ordDetDA.MissingSchemaAction = MissingSchemaAction.AddWithKey  
  
    custDA.Fill(custDS, "Customers")  
    orderDA.Fill(custDS, "Orders")  
    ordDetDA.Fill(custDS, "OrderDetails")  
  
    ' Close the Connection.  
    connection.Close()  
  
    ' Create relationships.  
    custDS.Relations.Add("CustomerOrders", _  
          custDS.Tables("Customers").Columns("CustomerID"), _  
          custDS.Tables("Orders").Columns("CustomerID"))  
  
    custDS.Relations.Add("OrderDetails", _  
          custDS.Tables("Orders").Columns("OrderID"), _  
          custDS.Tables("OrderDetails").Columns("OrderID"))  
  
' Create default DataView settings.  
Dim viewManager As DataViewManager = New DataViewManager(custDS)  
  
Dim viewSetting As DataViewSetting  
For Each viewSetting In viewManager.DataViewSettings  
  viewSetting.ApplyDefaultSort = True  
Next  
  
viewManager.DataViewSettings("Customers").Sort = "CompanyName"  
  
' Bind to a DataGrid.  
Dim grid As System.Windows.Forms.DataGrid = New System.Windows.Forms.DataGrid()  
grid.SetDataBinding(viewManager, "Customers")  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection to Northwind.  
// Create a Connection, DataAdapters, and a DataSet.  
SqlDataAdapter custDA = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers", connection);  
SqlDataAdapter orderDA = new SqlDataAdapter(  
  "SELECT OrderID, CustomerID FROM Orders", connection);  
SqlDataAdapter ordDetDA = new SqlDataAdapter(  
  "SELECT OrderID, ProductID, Quantity FROM [Order Details]", connection);  
  
DataSet custDS = new DataSet();  
  
// Open the Connection.  
connection.Open();  
  
    // Fill the DataSet with schema information and data.  
    custDA.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
    orderDA.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
    ordDetDA.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
  
    custDA.Fill(custDS, "Customers");  
    orderDA.Fill(custDS, "Orders");  
    ordDetDA.Fill(custDS, "OrderDetails");  
  
    // Close the Connection.  
    connection.Close();  
  
    // Create relationships.  
    custDS.Relations.Add("CustomerOrders",  
          custDS.Tables["Customers"].Columns["CustomerID"],  
          custDS.Tables["Orders"].Columns["CustomerID"]);  
  
    custDS.Relations.Add("OrderDetails",  
          custDS.Tables["Orders"].Columns["OrderID"],  
          custDS.Tables["OrderDetails"].Columns["OrderID"]);  
  
// Create default DataView settings.  
DataViewManager viewManager = new DataViewManager(custDS);  
  
foreach (DataViewSetting viewSetting in viewManager.DataViewSettings)  
  viewSetting.ApplyDefaultSort = true;  
  
viewManager.DataViewSettings["Customers"].Sort = "CompanyName";  
  
// Bind to a DataGrid.  
System.Windows.Forms.DataGrid grid = new System.Windows.Forms.DataGrid();  
grid.SetDataBinding(viewManager, "Customers");  
```  
  
## <a name="see-also"></a><span data-ttu-id="9b98d-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="9b98d-113">See also</span></span>

- <xref:System.Data.DataSet>
- <xref:System.Data.DataViewManager>
- <xref:System.Data.DataViewSetting>
- <xref:System.Data.DataViewSettingCollection>
- [<span data-ttu-id="9b98d-114">DataView</span><span class="sxs-lookup"><span data-stu-id="9b98d-114">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="9b98d-115">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="9b98d-115">ADO.NET Overview</span></span>](../ado-net-overview.md)
