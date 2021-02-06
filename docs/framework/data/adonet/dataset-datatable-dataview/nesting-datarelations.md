---
description: 了解详细信息：嵌套 Datarelation
title: 嵌套 DataRelation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9530f9c9-dd98-4b93-8cdb-40d7f1e8d0ab
ms.openlocfilehash: d998802a11fbb2bf414aa28b4beee95cac70a819
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651751"
---
# <a name="nesting-datarelations"></a><span data-ttu-id="9391d-103">嵌套 DataRelation</span><span class="sxs-lookup"><span data-stu-id="9391d-103">Nesting DataRelations</span></span>

<span data-ttu-id="9391d-104">在数据的关系表示形式中，各个表都包含使用一个列或一组列来相互关联的行。</span><span class="sxs-lookup"><span data-stu-id="9391d-104">In a relational representation of data, individual tables contain rows that are related to one another using a column or set of columns.</span></span> <span data-ttu-id="9391d-105">在 ADO.NET <xref:System.Data.DataSet> 中，表之间的关系使用 <xref:System.Data.DataRelation> 来实现。</span><span class="sxs-lookup"><span data-stu-id="9391d-105">In the ADO.NET <xref:System.Data.DataSet>, the relationship between tables is implemented using a <xref:System.Data.DataRelation>.</span></span> <span data-ttu-id="9391d-106">创建 **DataRelation** 时，列的父子关系仅通过关系进行管理。</span><span class="sxs-lookup"><span data-stu-id="9391d-106">When you create a **DataRelation**, the parent-child relationships of the columns are managed only through the relation.</span></span> <span data-ttu-id="9391d-107">表和列是独立的实体。</span><span class="sxs-lookup"><span data-stu-id="9391d-107">The tables and columns are separate entities.</span></span> <span data-ttu-id="9391d-108">在 XML 提供的数据的分层表示形式中，父子关系通过包含嵌套子元素的父元素来表示。</span><span class="sxs-lookup"><span data-stu-id="9391d-108">In the hierarchical representation of data that XML provides, the parent-child relationships are represented by parent elements that contain nested child elements.</span></span>  
  
 <span data-ttu-id="9391d-109">若要在使用 WriteXml 将 **数据集** 与或编写为 XML 数据的情况下，使子对象嵌套更方便 <xref:System.Xml.XmlDataDocument> ，  **DataRelation** 公开了 **嵌套** 属性。</span><span class="sxs-lookup"><span data-stu-id="9391d-109">To facilitate the nesting of child objects when a **DataSet** is synchronized with an <xref:System.Xml.XmlDataDocument> or written as XML data using **WriteXml**, the **DataRelation** exposes a **Nested** property.</span></span> <span data-ttu-id="9391d-110">如果将 **DataRelation** 的 **Nested** 属性设置为 **true** ，则在写入为 XML 数据或与 **XmlDataDocument** 进行同步时，会将该关系的子行嵌套在父列中。</span><span class="sxs-lookup"><span data-stu-id="9391d-110">Setting the **Nested** property of a **DataRelation** to **true** causes the child rows of the relation to be nested within the parent column when written as XML data or synchronized with an **XmlDataDocument**.</span></span> <span data-ttu-id="9391d-111">默认情况下， **DataRelation** 的 **嵌套** 属性为 **false**。</span><span class="sxs-lookup"><span data-stu-id="9391d-111">The **Nested** property of the **DataRelation** is **false**, by default.</span></span>  
  
 <span data-ttu-id="9391d-112">例如，请考虑以下 **数据集**。</span><span class="sxs-lookup"><span data-stu-id="9391d-112">For example, consider the following **DataSet**.</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers", connection)  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT OrderID, CustomerID, OrderDate FROM Orders", connection)  
  
connection.Open()  
  
Dim dataSet As DataSet = New DataSet("CustomerOrders")  
customerAdapter.Fill(dataSet, "Customers")  
orderAdapter.Fill(dataSet, "Orders")  
  
connection.Close()  
  
Dim customerOrders As DataRelation = dataSet.Relations.Add( _  
  "CustOrders", dataSet.Tables("Customers").Columns("CustomerID"), _  
  dataSet.Tables("Orders").Columns("CustomerID"))  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers", connection);  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
  "SELECT OrderID, CustomerID, OrderDate FROM Orders", connection);  
  
connection.Open();  
  
DataSet dataSet = new DataSet("CustomerOrders");  
customerAdapter.Fill(dataSet, "Customers");  
orderAdapter.Fill(dataSet, "Orders");  
  
connection.Close();  
  
DataRelation customerOrders = dataSet.Relations.Add(  
  "CustOrders", dataSet.Tables["Customers"].Columns["CustomerID"],  
  dataSet.Tables["Orders"].Columns["CustomerID"]);  
```  
  
 <span data-ttu-id="9391d-113">由于此 **数据集** 的 **DataRelation** 对象的 **嵌套** 属性未设置为 **true** ，因此当此 **数据集** 表示为 XML 数据时，子对象不会嵌套在父元素内。</span><span class="sxs-lookup"><span data-stu-id="9391d-113">Because the **Nested** property of the **DataRelation** object is not set to **true** for this **DataSet**, the child objects are not nested within the parent elements when this **DataSet** is represented as XML data.</span></span> <span data-ttu-id="9391d-114">转换包含相关 **数据** 集以及非嵌套数据关系的 **数据集** 的 XML 表示形式可能会导致性能下降。</span><span class="sxs-lookup"><span data-stu-id="9391d-114">Transforming the XML representation of a **DataSet** that contains related **DataSet** s with non-nested data relations can cause slow performance.</span></span> <span data-ttu-id="9391d-115">建议您嵌套数据关系。</span><span class="sxs-lookup"><span data-stu-id="9391d-115">We recommend that you nest the data relations.</span></span> <span data-ttu-id="9391d-116">为此，请将 **Nested** 属性设置为 **true**。</span><span class="sxs-lookup"><span data-stu-id="9391d-116">To do this, set the **Nested** property to **true**.</span></span> <span data-ttu-id="9391d-117">然后在使用上下分层 XPath 查询表达式的 XSLT 样式表中编写代码以定位和转换数据。</span><span class="sxs-lookup"><span data-stu-id="9391d-117">Then write code in the XSLT style sheet that uses top-down hierarchical XPath query expressions to locate and transform the data.</span></span>  
  
 <span data-ttu-id="9391d-118">下面的代码示例演示了对 **数据集** 调用 **WriteXml** 的结果。</span><span class="sxs-lookup"><span data-stu-id="9391d-118">The following code example shows the result from calling **WriteXml** on the **DataSet**.</span></span>  
  
```xml  
<CustomerOrders>  
  <Customers>  
    <CustomerID>ALFKI</CustomerID>  
    <CompanyName>Alfreds Futterkiste</CompanyName>  
  </Customers>  
  <Customers>  
    <CustomerID>ANATR</CustomerID>  
    <CompanyName>Ana Trujillo Emparedados y helados</CompanyName>  
  </Customers>  
  <Orders>  
    <OrderID>10643</OrderID>  
    <CustomerID>ALFKI</CustomerID>  
    <OrderDate>1997-08-25T00:00:00</OrderDate>  
  </Orders>  
  <Orders>  
    <OrderID>10692</OrderID>  
    <CustomerID>ALFKI</CustomerID>  
    <OrderDate>1997-10-03T00:00:00</OrderDate>  
  </Orders>  
  <Orders>  
    <OrderID>10308</OrderID>  
    <CustomerID>ANATR</CustomerID>  
    <OrderDate>1996-09-18T00:00:00</OrderDate>  
  </Orders>  
</CustomerOrders>  
```  
  
 <span data-ttu-id="9391d-119">请注意， **Customers** 元素和 **Orders** 元素显示为同级元素。</span><span class="sxs-lookup"><span data-stu-id="9391d-119">Note that the **Customers** element and the **Orders** elements are shown as sibling elements.</span></span> <span data-ttu-id="9391d-120">如果希望 **Orders** 元素显示为其各自父元素的子级，则必须将 **DataRelation** 的 **嵌套** 属性设置为 **true** ，并添加以下内容：</span><span class="sxs-lookup"><span data-stu-id="9391d-120">If you wanted the **Orders** elements to show up as children of their respective parent elements, the **Nested** property of the **DataRelation** would need to be set to **true** and you would add the following:</span></span>  
  
```vb  
customerOrders.Nested = True  
```  
  
```csharp  
customerOrders.Nested = true;  
```  
  
 <span data-ttu-id="9391d-121">下面的代码演示生成的输出的外观，其中的 **Orders** 元素嵌套在其各自的父元素中。</span><span class="sxs-lookup"><span data-stu-id="9391d-121">The following code shows what the resulting output would look like, with the **Orders** elements nested within their respective parent elements.</span></span>  
  
```xml  
<CustomerOrders>  
  <Customers>  
    <CustomerID>ALFKI</CustomerID>  
    <Orders>  
      <OrderID>10643</OrderID>  
      <CustomerID>ALFKI</CustomerID>  
      <OrderDate>1997-08-25T00:00:00</OrderDate>  
    </Orders>  
    <Orders>  
      <OrderID>10692</OrderID>  
      <CustomerID>ALFKI</CustomerID>  
      <OrderDate>1997-10-03T00:00:00</OrderDate>  
    </Orders>  
    <CompanyName>Alfreds Futterkiste</CompanyName>  
  </Customers>  
  <Customers>  
    <CustomerID>ANATR</CustomerID>  
    <Orders>  
      <OrderID>10308</OrderID>  
      <CustomerID>ANATR</CustomerID>  
      <OrderDate>1996-09-18T00:00:00</OrderDate>  
    </Orders>  
    <CompanyName>Ana Trujillo Emparedados y helados</CompanyName>  
  </Customers>  
</CustomerOrders>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9391d-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="9391d-122">See also</span></span>

- [<span data-ttu-id="9391d-123">在数据集中使用 XML</span><span class="sxs-lookup"><span data-stu-id="9391d-123">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="9391d-124">添加 DataRelation</span><span class="sxs-lookup"><span data-stu-id="9391d-124">Adding DataRelations</span></span>](adding-datarelations.md)
- [<span data-ttu-id="9391d-125">数据集、数据表和数据视图</span><span class="sxs-lookup"><span data-stu-id="9391d-125">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="9391d-126">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="9391d-126">ADO.NET Overview</span></span>](../ado-net-overview.md)
