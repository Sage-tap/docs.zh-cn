---
description: 了解详细信息：映射键 XML 架构 (XSD) 约束到数据集约束
title: 将关键 XML 架构 (XSD) 约束映射到数据集约束
ms.date: 03/30/2017
ms.assetid: 22664196-f270-4ebc-a169-70e16a83dfa1
ms.openlocfilehash: 0c07b53e06dc6b80395764b2bdd76045ee80bffd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651985"
---
# <a name="map-key-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="95af7-103">将关键 XML 架构 (XSD) 约束映射到数据集约束</span><span class="sxs-lookup"><span data-stu-id="95af7-103">Map key XML Schema (XSD) Constraints to DataSet Constraints</span></span>

<span data-ttu-id="95af7-104">在架构中，可以使用 **key** 元素对元素或属性指定键约束。</span><span class="sxs-lookup"><span data-stu-id="95af7-104">In a schema, you can specify a key constraint on an element or attribute using the **key** element.</span></span> <span data-ttu-id="95af7-105">对其指定键约束的元素或属性必须在任何架构实例中都具有唯一值，并且不能具有空值。</span><span class="sxs-lookup"><span data-stu-id="95af7-105">The element or attribute on which a key constraint is specified must have unique values in any schema instance, and cannot have null values.</span></span>  
  
 <span data-ttu-id="95af7-106">除了对其定义键约束的列不能具有空值之外，键约束与唯一约束类似。</span><span class="sxs-lookup"><span data-stu-id="95af7-106">The key constraint is similar to the unique constraint, except that the column on which a key constraint is defined cannot have null values.</span></span>  
  
 <span data-ttu-id="95af7-107">下表概述了可以在 **key** 元素中指定的 **msdata** 属性。</span><span class="sxs-lookup"><span data-stu-id="95af7-107">The following table outlines the **msdata** attributes that you can specify in the **key** element.</span></span>  
  
|<span data-ttu-id="95af7-108">属性名称</span><span class="sxs-lookup"><span data-stu-id="95af7-108">Attribute name</span></span>|<span data-ttu-id="95af7-109">说明</span><span class="sxs-lookup"><span data-stu-id="95af7-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="95af7-110">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="95af7-110">**msdata:ConstraintName**</span></span>|<span data-ttu-id="95af7-111">如果指定了该属性，它的值将用作约束名。</span><span class="sxs-lookup"><span data-stu-id="95af7-111">If this attribute is specified, its value is used as the constraint name.</span></span> <span data-ttu-id="95af7-112">否则， **name** 属性提供约束名称的值。</span><span class="sxs-lookup"><span data-stu-id="95af7-112">Otherwise, the **name** attribute provides the value of the constraint name.</span></span>|  
|<span data-ttu-id="95af7-113">**msdata:PrimaryKey**</span><span class="sxs-lookup"><span data-stu-id="95af7-113">**msdata:PrimaryKey**</span></span>|<span data-ttu-id="95af7-114">如果 `PrimaryKey="true"` 存在，则 **IsPrimaryKey** 约束属性设置为 **true**，从而使其成为主键。</span><span class="sxs-lookup"><span data-stu-id="95af7-114">If `PrimaryKey="true"` is present, the **IsPrimaryKey** constraint property is set to **true**, thus making it a primary key.</span></span> <span data-ttu-id="95af7-115">**AllowDBNull** 列属性设置为 **false**，因为主键不能具有 null 值。</span><span class="sxs-lookup"><span data-stu-id="95af7-115">The **AllowDBNull** column property is set to **false**, because primary keys cannot have null values.</span></span>|  
  
 <span data-ttu-id="95af7-116">在转换指定了键约束的架构时，映射过程会对约束中的每一列将 **AllowDBNull** column 属性设置为 **false** 的表创建 unique 约束。</span><span class="sxs-lookup"><span data-stu-id="95af7-116">In converting schema in which a key constraint is specified, the mapping process creates a unique constraint on the table with the **AllowDBNull** column property set to **false** for each column in the constraint.</span></span> <span data-ttu-id="95af7-117">除非已对 key 元素指定，否则 unique 约束的 IsPrimaryKey 属性也设置为 **false** `msdata:PrimaryKey="true"` 。 </span><span class="sxs-lookup"><span data-stu-id="95af7-117">The **IsPrimaryKey** property of the unique constraint is also set to **false** unless you have specified `msdata:PrimaryKey="true"` on the **key** element.</span></span> <span data-ttu-id="95af7-118">它与 `PrimaryKey="true"` 的架构中的唯一约束相同。</span><span class="sxs-lookup"><span data-stu-id="95af7-118">This is identical to a unique constraint in the schema in which `PrimaryKey="true"`.</span></span>  
  
 <span data-ttu-id="95af7-119">在下面的架构示例中， **key** 元素指定了 **CustomerID** 元素的键约束。</span><span class="sxs-lookup"><span data-stu-id="95af7-119">In the following schema example, the **key** element specifies the key constraint on the **CustomerID** element.</span></span>  
  
```xml  
<xs:schema id="cod"  
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="Customers">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
        <xs:element name="CompanyName" type="xs:string" minOccurs="0" />  
       <xs:element name="Phone" type="xs:string" />  
     </xs:sequence>  
   </xs:complexType>  
 </xs:element>  
<xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element ref="Customers" />  
    </xs:choice>  
  </xs:complexType>  
   <xs:key  msdata:PrimaryKey="true"  
       msdata:ConstraintName="KeyCustID"  
          name="KeyConstCustomerID" >  
     <xs:selector xpath=".//Customers" />  
     <xs:field xpath="CustomerID" />  
    </xs:key>  
 </xs:element>  
</xs:schema>
```  
  
 <span data-ttu-id="95af7-120">**Key** 元素指定 **Customers** 元素的 **CustomerID** 子元素的值必须具有唯一值，且不能具有 null 值。</span><span class="sxs-lookup"><span data-stu-id="95af7-120">The **key** element specifies that the values of the **CustomerID** child element of the **Customers** element must have unique values and cannot have null values.</span></span> <span data-ttu-id="95af7-121">在转换 XML 架构定义语言 (XSD) 架构时，映射过程将创建下表：</span><span class="sxs-lookup"><span data-stu-id="95af7-121">In translating the XML Schema definition language (XSD) schema, the mapping process creates the following table:</span></span>  
  
```text  
Customers(CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="95af7-122">XML 架构映射还会在 **CustomerID** 列上创建 **UniqueConstraint** ，如下所示 <xref:System.Data.DataSet> 。</span><span class="sxs-lookup"><span data-stu-id="95af7-122">The XML Schema mapping also creates a **UniqueConstraint** on the **CustomerID** column, as shown in the following <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="95af7-123">（为简便起见，只显示相关属性。）</span><span class="sxs-lookup"><span data-stu-id="95af7-123">(For simplicity, only relevant properties are shown.)</span></span>  
  
```text  
      DataSetName: MyDataSet  
TableName: customers  
  ColumnName: CustomerID  
      AllowDBNull: False  
      Unique: True  
  ConstraintName: KeyCustID  
      Table: customers  
      Columns: CustomerID
      IsPrimaryKey: True  
```  
  
 <span data-ttu-id="95af7-124">在生成的 **数据集中**， **UniqueConstraint** 的 **IsPrimaryKey** 属性设置为 **true** ，因为架构指定 `msdata:PrimaryKey="true"` 了 **key** 元素中的。</span><span class="sxs-lookup"><span data-stu-id="95af7-124">In the **DataSet** that is generated, the **IsPrimaryKey** property of the **UniqueConstraint** is set to **true** because the schema specifies `msdata:PrimaryKey="true"` in the **key** element.</span></span>  
  
 <span data-ttu-id="95af7-125">**DataSet** 中 **UniqueConstraint** 的 **ConstraintName** 属性的值是在架构的 **Key** 元素中指定的 **msdata： ConstraintName** 属性的值。</span><span class="sxs-lookup"><span data-stu-id="95af7-125">The value of the **ConstraintName** property of the **UniqueConstraint** in the **DataSet** is the value of the **msdata:ConstraintName** attribute specified in the **key** element in the schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95af7-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="95af7-126">See also</span></span>

- [<span data-ttu-id="95af7-127">将关键 XML 架构 (XSD) 约束映射到数据集约束</span><span class="sxs-lookup"><span data-stu-id="95af7-127">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="95af7-128">从 XML 架构生成数据集关系 (XSD)</span><span class="sxs-lookup"><span data-stu-id="95af7-128">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="95af7-129">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="95af7-129">ADO.NET Overview</span></span>](../ado-net-overview.md)
