---
description: 了解详细信息：将唯一 XML 架构 (XSD) 约束映射到数据集约束
title: 将唯一 XML 架构 (XSD) 约束映射到数据集约束
ms.date: 03/30/2017
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
ms.openlocfilehash: 41a6e5424d67b092e57ac61d6e34a1f285fb8d0c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651920"
---
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="bc65c-103">将唯一 XML 架构 (XSD) 约束映射到数据集约束</span><span class="sxs-lookup"><span data-stu-id="bc65c-103">Map unique XML Schema (XSD) Constraints to DataSet Constraints</span></span>

<span data-ttu-id="bc65c-104">在 XML 架构定义语言中 (XSD) 架构， **unique** 元素指定元素或属性的唯一性约束。</span><span class="sxs-lookup"><span data-stu-id="bc65c-104">In an XML Schema definition language (XSD) schema, the **unique** element specifies the uniqueness constraint on an element or attribute.</span></span> <span data-ttu-id="bc65c-105">在将 XML 架构转换为关系架构的过程中，对 XML 架构中的元素或属性指定的唯一约束将映射到所生成的相应 <xref:System.Data.DataTable> 中的 <xref:System.Data.DataSet> 中的唯一约束。</span><span class="sxs-lookup"><span data-stu-id="bc65c-105">In the process of translating an XML Schema into a relational schema, the unique constraint specified on an element or attribute in the XML Schema is mapped to a unique constraint in the <xref:System.Data.DataTable> in the corresponding <xref:System.Data.DataSet> that is generated.</span></span>  
  
 <span data-ttu-id="bc65c-106">下表概述了可在 **unique** 元素中指定的 **msdata** 属性。</span><span class="sxs-lookup"><span data-stu-id="bc65c-106">The following table outlines the **msdata** attributes that you can specify in the **unique** element.</span></span>  
  
|<span data-ttu-id="bc65c-107">属性名称</span><span class="sxs-lookup"><span data-stu-id="bc65c-107">Attribute name</span></span>|<span data-ttu-id="bc65c-108">说明</span><span class="sxs-lookup"><span data-stu-id="bc65c-108">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="bc65c-109">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="bc65c-109">**msdata:ConstraintName**</span></span>|<span data-ttu-id="bc65c-110">如果指定了该属性，它的值将用作约束名。</span><span class="sxs-lookup"><span data-stu-id="bc65c-110">If this attribute is specified, its value is used as the constraint name.</span></span> <span data-ttu-id="bc65c-111">否则， **name** 属性提供约束名称的值。</span><span class="sxs-lookup"><span data-stu-id="bc65c-111">Otherwise, the **name** attribute provides the value of the constraint name.</span></span>|  
|<span data-ttu-id="bc65c-112">**msdata:PrimaryKey**</span><span class="sxs-lookup"><span data-stu-id="bc65c-112">**msdata:PrimaryKey**</span></span>|<span data-ttu-id="bc65c-113">如果在 `PrimaryKey="true"` **unique** 元素中存在，则将创建一个唯一约束，并将 **IsPrimaryKey** 属性设置为 **true**。</span><span class="sxs-lookup"><span data-stu-id="bc65c-113">If `PrimaryKey="true"` is present in the **unique** element, a unique constraint is created with the **IsPrimaryKey** property set to **true**.</span></span>|  
  
 <span data-ttu-id="bc65c-114">下面的示例演示一个使用 **unique** 元素指定唯一性约束的 XML 架构。</span><span class="sxs-lookup"><span data-stu-id="bc65c-114">The following example shows an XML Schema that uses the **unique** element to specify a uniqueness constraint.</span></span>  
  
```xml  
<xs:schema id="SampleDataSet"
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="Customers">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="CustomerID" type="xs:integer"
           minOccurs="0"/>  
        <xs:element name="CompanyName" type="xs:string"
           minOccurs="0"/>  
       <xs:element name="Phone" type="xs:string" />  
     </xs:sequence>  
   </xs:complexType>  
 </xs:element>  
  
 <xs:element name="SampleDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element ref="Customers" />  
    </xs:choice>  
  </xs:complexType>  
   <xs:unique     msdata:ConstraintName="UCustID"     name="UniqueCustIDConstr" >       <xs:selector xpath=".//Customers" />       <xs:field xpath="CustomerID" />     </xs:unique>  
</xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="bc65c-115">架构中的 **unique** 元素指定对于文档实例中的所有 **Customers** 元素， **CustomerID** 子元素的值必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="bc65c-115">The **unique** element in the schema specifies that for all **Customers** elements in a document instance, the value of the **CustomerID** child element must be unique.</span></span> <span data-ttu-id="bc65c-116">在生成 **数据集** 时，映射过程将读取此架构并生成下表：</span><span class="sxs-lookup"><span data-stu-id="bc65c-116">In building the **DataSet**, the mapping process reads this schema and generates the following table:</span></span>  
  
```text  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="bc65c-117">映射过程还会在 **CustomerID** 列上创建唯一约束，如下面的 **数据集** 中所示。</span><span class="sxs-lookup"><span data-stu-id="bc65c-117">The mapping process also creates a unique constraint on the **CustomerID** column, as shown in the following **DataSet**.</span></span> <span data-ttu-id="bc65c-118">（为简便起见，只显示相关属性。）</span><span class="sxs-lookup"><span data-stu-id="bc65c-118">(For simplicity, only relevant properties are shown.)</span></span>  
  
```text  
      DataSetName: MyDataSet  
TableName: Customers  
  ColumnName: CustomerID  
      AllowDBNull: True  
      Unique: True  
  ConstraintName: UcustID       Type: UniqueConstraint  
      Table: Customers  
      Columns: CustomerID
      IsPrimaryKey: False  
```  
  
 <span data-ttu-id="bc65c-119">在生成的 **数据集中** ，unique 约束的 **IsPrimaryKey** 属性设置为 **False** 。</span><span class="sxs-lookup"><span data-stu-id="bc65c-119">In the **DataSet** that is generated, the **IsPrimaryKey** property is set to **False** for the unique constraint.</span></span> <span data-ttu-id="bc65c-120">列的 **unique** 属性指示 **CustomerID** 列值必须唯一 (但可以是空引用，如) 的列的 **AllowDBNull** 属性所指定。</span><span class="sxs-lookup"><span data-stu-id="bc65c-120">The **unique** property on the column indicates that the **CustomerID** column values must be unique (but they can be a null reference, as specified by the **AllowDBNull** property of the column).</span></span>  
  
 <span data-ttu-id="bc65c-121">如果修改架构并将可选的 **msdata： PrimaryKey** 特性值设置为 **True**，则会在表中创建 unique 约束。</span><span class="sxs-lookup"><span data-stu-id="bc65c-121">If you modify the schema and set the optional **msdata:PrimaryKey** attribute value to **True**, the unique constraint is created on the table.</span></span> <span data-ttu-id="bc65c-122">**AllowDBNull** 列属性设置为 **False**，并且约束的 **IsPrimaryKey** 属性设置为 **True**，从而使 **CustomerID** 列成为主键列。</span><span class="sxs-lookup"><span data-stu-id="bc65c-122">The **AllowDBNull** column property is set to **False**, and the **IsPrimaryKey** property of the constraint set to **True**, thus making the **CustomerID** column a primary key column.</span></span>  
  
 <span data-ttu-id="bc65c-123">您可以对 XML 架构中元素或属性的组合指定唯一约束。</span><span class="sxs-lookup"><span data-stu-id="bc65c-123">You can specify a unique constraint on a combination of elements or attributes in the XML Schema.</span></span> <span data-ttu-id="bc65c-124">下面的示例演示了如何通过在架构中添加另一个 **xs： field** 元素，为任何实例中的所有 **客户** 指定 **CustomerID** **和值** 的组合必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="bc65c-124">The following example demonstrates how to specify that a combination of **CustomerID** and **CompanyName** values must be unique for all **Customers** in any instance, by adding another **xs:field** element in the schema.</span></span>  
  
```xml  
      <xs:unique
         msdata:ConstraintName="SomeName"
         name="UniqueCustIDConstr" >
  <xs:selector xpath=".//Customers" />
  <xs:field xpath="CustomerID" />
  <xs:field xpath="CompanyName" />
</xs:unique>  
```  
  
 <span data-ttu-id="bc65c-125">这是在生成的 **数据集中** 创建的约束。</span><span class="sxs-lookup"><span data-stu-id="bc65c-125">This is the constraint that is created in the resulting **DataSet**.</span></span>  
  
```text  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName
  IsPrimaryKey: False  
```  
  
## <a name="see-also"></a><span data-ttu-id="bc65c-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="bc65c-126">See also</span></span>

- [<span data-ttu-id="bc65c-127">将关键 XML 架构 (XSD) 约束映射到数据集约束</span><span class="sxs-lookup"><span data-stu-id="bc65c-127">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="bc65c-128">从 XML 架构生成数据集关系 (XSD)</span><span class="sxs-lookup"><span data-stu-id="bc65c-128">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="bc65c-129">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="bc65c-129">ADO.NET Overview</span></span>](../ado-net-overview.md)
