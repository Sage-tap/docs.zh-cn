---
description: 了解详细信息：将 XSLT 转换应用于数据集
title: 将 XSLT 转换应用于 DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 09f2e4ee-1d08-4ba8-8936-83394fee319d
ms.openlocfilehash: c7fc25441091112f7fbb7e4c1f8dd210d8cd0c5d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725111"
---
# <a name="applying-an-xslt-transform-to-a-dataset"></a><span data-ttu-id="2d49e-103">将 XSLT 转换应用于 DataSet</span><span class="sxs-lookup"><span data-stu-id="2d49e-103">Applying an XSLT Transform to a DataSet</span></span>

<span data-ttu-id="2d49e-104">使用的 **WriteXml** 方法， <xref:System.Data.DataSet> 可以将 **数据集** 的内容作为 XML 数据写入。</span><span class="sxs-lookup"><span data-stu-id="2d49e-104">The **WriteXml** method of the <xref:System.Data.DataSet> enables you to write the contents of a **DataSet** as XML data.</span></span> <span data-ttu-id="2d49e-105">随后的一项常见任务是使用 XSL 转换 (XSLT) 将该 XML 转换为另一种格式。</span><span class="sxs-lookup"><span data-stu-id="2d49e-105">A common task is to then transform that XML to another format using XSL transformations (XSLT).</span></span> <span data-ttu-id="2d49e-106">但是，通过将 **数据集** 与同步，可以 <xref:System.Xml.XmlDataDocument> 将 XSLT 样式表应用于 **数据集** 的内容，而不必首先使用 **WriteXml** 以 XML 数据的形式编写 **数据集** 的内容。</span><span class="sxs-lookup"><span data-stu-id="2d49e-106">However, synchronizing a **DataSet** with an <xref:System.Xml.XmlDataDocument> enables you to apply an XSLT stylesheet to the contents of a **DataSet** without having to first write the contents of the **DataSet** as XML data using **WriteXml**.</span></span>  
  
 <span data-ttu-id="2d49e-107">下面的示例使用数据表和关系填充 **数据集** ，并将 **数据** 集与 **XMLDATADOCUMENT** 同步，并使用 XSLT 样式表将部分 **数据集** 作为 HTML 文件写入。</span><span class="sxs-lookup"><span data-stu-id="2d49e-107">The following example populates a **DataSet** with tables and relationships, synchronizes the **DataSet** with an **XmlDataDocument**, and writes a portion of the **DataSet** as an HTML file using an XSLT stylesheet.</span></span> <span data-ttu-id="2d49e-108">下面是 XSLT 样式表的内容：</span><span class="sxs-lookup"><span data-stu-id="2d49e-108">The following are the contents of the XSLT stylesheet:</span></span>
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">  
  
<xsl:template match="CustomerOrders">  
  <HTML>  
  <STYLE>  
  BODY {font-family:verdana;font-size:9pt}  
  TD   {font-size:8pt}  
  </STYLE>  
    <BODY>  
    <TABLE BORDER="1">  
      <xsl:apply-templates select="Customers"/>  
    </TABLE>  
    </BODY>  
  </HTML>  
</xsl:template>  
  
<xsl:template match="Customers">  
    <TR><TD>  
      <xsl:value-of select="ContactName"/>, <xsl:value-of select="Phone"/><BR/>  
    </TD></TR>  
      <xsl:apply-templates select="Orders"/>  
</xsl:template>  
  
<xsl:template match="Orders">  
  <TABLE BORDER="1">  
    <TR><TD valign="top"><B>Order:</B></TD><TD valign="top"><xsl:value-of select="OrderID"/></TD></TR>  
    <TR><TD valign="top"><B>Date:</B></TD><TD valign="top"><xsl:value-of select="OrderDate"/></TD></TR>  
    <TR><TD valign="top"><B>Ship To:</B></TD>  
        <TD valign="top"><xsl:value-of select="ShipName"/><BR/>  
        <xsl:value-of select="ShipAddress"/><BR/>  
        <xsl:value-of select="ShipCity"/>, <xsl:value-of select="ShipRegion"/>  <xsl:value-of select="ShipPostalCode"/><BR/>  
        <xsl:value-of select="ShipCountry"/></TD></TR>  
  </TABLE>  
</xsl:template>  
  
</xsl:stylesheet>  
```  
  
 <span data-ttu-id="2d49e-109">下面的代码填充 **数据集** 并应用 XSLT 样式表。</span><span class="sxs-lookup"><span data-stu-id="2d49e-109">The following code fills the **DataSet** and applies the XSLT style sheet.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2d49e-110">如果要将 XSLT 样式表应用于包含关系的 **数据集** ，如果将每个嵌套关系的的 **嵌套** 属性设置 <xref:System.Data.DataRelation> 为 **true** ，则会获得最佳性能。</span><span class="sxs-lookup"><span data-stu-id="2d49e-110">If you are applying an XSLT style sheet to a **DataSet** that contains relations, you achieve best performance if you set the **Nested** property of the <xref:System.Data.DataRelation> to **true** for each nested relation.</span></span> <span data-ttu-id="2d49e-111">此设置使你可以使用 XSLT 样式表，执行正常的由上而下处理以遍历层次结构和转换数据，而不是使用对性能要求较高的 XPath 定位轴（例如，样式表节点测试表达式中前面的同级和后面的同级）来遍历层次结构。</span><span class="sxs-lookup"><span data-stu-id="2d49e-111">This allows you to use XSLT style sheets that implement natural top-down processing to navigate the hierarchy and transform the data, as opposed to using performance-intensive XPath location axes (for example, preceding-sibling and following-sibling in style sheet node test expressions) to navigate it.</span></span> <span data-ttu-id="2d49e-112">有关嵌套关系的详细信息，请参阅 [嵌套 datarelation](nesting-datarelations.md)。</span><span class="sxs-lookup"><span data-stu-id="2d49e-112">For more information on nested relations, see [Nesting DataRelations](nesting-datarelations.md).</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim dataSet As DataSet = New DataSet("CustomerOrders")  
  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM Customers", connection)  
customerAdapter.Fill(dataSet, "Customers")  
  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM Orders", connection)  
orderAdapter.Fill(dataSet, "Orders")  
  
connection.Close()  
  
dataSet.Relations.Add("CustOrders", _  
dataSet.Tables("Customers").Columns("CustomerID"), _  
dataSet.Tables("Orders").Columns("CustomerID")).Nested = true  
  
Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)
  
Dim xslTran As XslTransform = New XslTransform  
xslTran.Load("transform.xsl")  
  
Dim writer As XmlTextWriter = New XmlTextWriter( _  
  "xslt_output.html", System.Text.Encoding.UTF8)  
  
xslTran.Transform(xmlDoc, Nothing, writer)  
writer.Close()  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
connection.Open();  
  
DataSet custDS = new DataSet("CustomerDataSet");  
  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
  "SELECT * FROM Customers", connection);  
customerAdapter.Fill(custDS, "Customers");  
  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
  "SELECT * FROM Orders", connection);  
orderAdapter.Fill(custDS, "Orders");  
  
connection.Close();  
  
custDS.Relations.Add("CustOrders",  
  custDS.Tables["Customers"].Columns["CustomerID"],  
                     custDS.Tables["Orders"].Columns["CustomerID"]).Nested = true;  
  
XmlDataDocument xmlDoc = new XmlDataDocument(custDS);
  
XslTransform xslTran = new XslTransform();  
xslTran.Load("transform.xsl");  
  
XmlTextWriter writer = new XmlTextWriter("xslt_output.html",
  System.Text.Encoding.UTF8);  
  
xslTran.Transform(xmlDoc, null, writer);  
writer.Close();  
```  
  
## <a name="see-also"></a><span data-ttu-id="2d49e-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="2d49e-113">See also</span></span>

- [<span data-ttu-id="2d49e-114">数据集和 XmlDataDocument 同步</span><span class="sxs-lookup"><span data-stu-id="2d49e-114">DataSet and XmlDataDocument Synchronization</span></span>](dataset-and-xmldatadocument-synchronization.md)
- [<span data-ttu-id="2d49e-115">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="2d49e-115">ADO.NET Overview</span></span>](../ado-net-overview.md)
