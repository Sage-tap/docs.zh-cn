---
description: 了解详细信息：将 keyref XML 架构 (XSD) 约束映射到数据集约束
title: 将 keyref XML 架构 (XSD) 约束映射到数据集约束
ms.date: 03/30/2017
ms.assetid: 5b634fea-cc1e-4f6b-9454-10858105b1c8
ms.openlocfilehash: f9925cf68e0c8fd1258eeeb509664e0527e58526
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651972"
---
# <a name="map-keyref-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="023dc-103">将 keyref XML 架构 (XSD) 约束映射到数据集约束</span><span class="sxs-lookup"><span data-stu-id="023dc-103">Map keyref XML Schema (XSD) Constraints to DataSet Constraints</span></span>

<span data-ttu-id="023dc-104">**Keyref** 元素使你可以在文档中的元素之间建立链接。</span><span class="sxs-lookup"><span data-stu-id="023dc-104">The **keyref** element allows you to establish links between elements within a document.</span></span> <span data-ttu-id="023dc-105">它类似于关系数据库中的外键关系。</span><span class="sxs-lookup"><span data-stu-id="023dc-105">This is similar to a foreign key relationship in a relational database.</span></span> <span data-ttu-id="023dc-106">如果架构指定了 **keyref** 元素，则在架构映射过程中将元素转换为的表中的列的相应外键约束 <xref:System.Data.DataSet> 。</span><span class="sxs-lookup"><span data-stu-id="023dc-106">If a schema specifies the **keyref** element, the element is converted during the schema mapping process to a corresponding foreign key constraint on the columns in the tables of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="023dc-107">默认情况下， **keyref** 元素还会生成一个关系，并在关系上指定 **ParentTable**、 **ChildTable**、 **ParentColumn** 和 **ChildColumn** 属性。</span><span class="sxs-lookup"><span data-stu-id="023dc-107">By default, the **keyref** element also generates a relation, with the **ParentTable**, **ChildTable**, **ParentColumn**, and **ChildColumn** properties specified on the relation.</span></span>  
  
 <span data-ttu-id="023dc-108">下表概述了可在 **keyref** 元素中指定的 **msdata** 属性。</span><span class="sxs-lookup"><span data-stu-id="023dc-108">The following table outlines the **msdata** attributes you can specify in the **keyref** element.</span></span>  
  
|<span data-ttu-id="023dc-109">属性名称</span><span class="sxs-lookup"><span data-stu-id="023dc-109">Attribute name</span></span>|<span data-ttu-id="023dc-110">说明</span><span class="sxs-lookup"><span data-stu-id="023dc-110">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="023dc-111">**msdata:ConstraintOnly**</span><span class="sxs-lookup"><span data-stu-id="023dc-111">**msdata:ConstraintOnly**</span></span>|<span data-ttu-id="023dc-112">如果在架构的 **keyref** 元素中指定了 **ConstraintOnly = "true"** ，则会创建一个约束，但不会创建任何关系。</span><span class="sxs-lookup"><span data-stu-id="023dc-112">If **ConstraintOnly="true"** is specified on the **keyref** element in the schema, a constraint is created, but no relation is created.</span></span> <span data-ttu-id="023dc-113">如果未指定此特性 (或设置为 **False**) ，则在 **数据集中** 创建约束和关系。</span><span class="sxs-lookup"><span data-stu-id="023dc-113">If this attribute is not specified (or is set to **False**), both the constraint and the relation are created in the **DataSet**.</span></span>|  
|<span data-ttu-id="023dc-114">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="023dc-114">**msdata:ConstraintName**</span></span>|<span data-ttu-id="023dc-115">如果指定了 **ConstraintName** 属性，则将其值用作约束的名称。</span><span class="sxs-lookup"><span data-stu-id="023dc-115">If the **ConstraintName** attribute is specified, its value is used as the name of the constraint.</span></span> <span data-ttu-id="023dc-116">否则，架构中 **keyref** 元素的 **Name** 属性提供 **数据集中** 的约束名称。</span><span class="sxs-lookup"><span data-stu-id="023dc-116">Otherwise, the **name** attribute of the **keyref** element in the schema provides the constraint name in the **DataSet**.</span></span>|  
|<span data-ttu-id="023dc-117">**msdata:UpdateRule**</span><span class="sxs-lookup"><span data-stu-id="023dc-117">**msdata:UpdateRule**</span></span>|<span data-ttu-id="023dc-118">如果在架构的 **keyref** 元素中指定了 **UpdateRule** 属性，则其值将分配给 **数据集中** 的 **UpdateRule** 约束属性。</span><span class="sxs-lookup"><span data-stu-id="023dc-118">If the **UpdateRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **UpdateRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="023dc-119">否则， **UpdateRule** 属性将设置为 **Cascade**。</span><span class="sxs-lookup"><span data-stu-id="023dc-119">Otherwise the **UpdateRule** property is set to **Cascade**.</span></span>|  
|<span data-ttu-id="023dc-120">**msdata:DeleteRule**</span><span class="sxs-lookup"><span data-stu-id="023dc-120">**msdata:DeleteRule**</span></span>|<span data-ttu-id="023dc-121">如果在架构的 **keyref** 元素中指定了 **DeleteRule** 属性，则其值将分配给 **数据集中** 的 **DeleteRule** 约束属性。</span><span class="sxs-lookup"><span data-stu-id="023dc-121">If the **DeleteRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **DeleteRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="023dc-122">否则， **DeleteRule** 属性将设置为 **Cascade**。</span><span class="sxs-lookup"><span data-stu-id="023dc-122">Otherwise the **DeleteRule** property is set to **Cascade**.</span></span>|  
|<span data-ttu-id="023dc-123">**msdata:AcceptRejectRule**</span><span class="sxs-lookup"><span data-stu-id="023dc-123">**msdata:AcceptRejectRule**</span></span>|<span data-ttu-id="023dc-124">如果在架构的 **keyref** 元素中指定了 **AcceptRejectRule** 属性，则其值将分配给 **数据集中** 的 **AcceptRejectRule** 约束属性。</span><span class="sxs-lookup"><span data-stu-id="023dc-124">If the **AcceptRejectRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **AcceptRejectRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="023dc-125">否则， **AcceptRejectRule** 属性设置为 **None**。</span><span class="sxs-lookup"><span data-stu-id="023dc-125">Otherwise the **AcceptRejectRule** property is set to **None**.</span></span>|  
  
 <span data-ttu-id="023dc-126">下面的示例包含一个架构，该架构指定 **Order** 元素的 **OrderNumber** 子元素和 **OrderDetail** 元素的 **OrderNo** 子元素之间的 **key** 和 **keyref** 关系。</span><span class="sxs-lookup"><span data-stu-id="023dc-126">The following example contains a schema that specifies the **key** and **keyref** relationships between the **OrderNumber** child element of the **Order** element and the **OrderNo** child element of the **OrderDetail** element.</span></span>  
  
 <span data-ttu-id="023dc-127">在此示例中， **OrderDetail** 元素的 **OrderNumber** 子元素引用 **Order** 元素的 **OrderNo** key 子元素。</span><span class="sxs-lookup"><span data-stu-id="023dc-127">In the example, the **OrderNumber** child element of the **OrderDetail** element refers to the **OrderNo** key child element of the **Order** element.</span></span>  
  
```xml  
<xs:schema id="MyDataSet" xmlns=""
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element name="OrderDetail">  
       <xs:complexType>  
         <xs:sequence>  
           <xs:element name="OrderNo" type="xs:integer" />  
           <xs:element name="ItemNo" type="xs:string" />  
         </xs:sequence>  
       </xs:complexType>  
      </xs:element>  
      <xs:element name="Order">  
        <xs:complexType>  
          <xs:sequence>  
            <xs:element name="OrderNumber" type="xs:integer" />  
            <xs:element name="EmpNumber" type="xs:integer" />  
          </xs:sequence>  
        </xs:complexType>  
      </xs:element>  
    </xs:choice>  
  </xs:complexType>  
  
  <xs:key name="OrderNumberKey"  >  
    <xs:selector xpath=".//Order" />  
    <xs:field xpath="OrderNumber" />  
  </xs:key>  
  
  <xs:keyref name="OrderNoRef" refer="OrderNumberKey">  
    <xs:selector xpath=".//OrderDetail" />  
    <xs:field xpath="OrderNo" />  
  </xs:keyref>  
 </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="023dc-128">XML 架构定义语言 (XSD) 架构映射过程生成包含两个表的以下 **数据集** ：</span><span class="sxs-lookup"><span data-stu-id="023dc-128">The XML Schema definition language (XSD) schema mapping process produces the following **DataSet** with two tables:</span></span>  
  
```text  
OrderDetail(OrderNo, ItemNo) and  
Order(OrderNumber, EmpNumber)  
```  
  
 <span data-ttu-id="023dc-129">此外， **数据集** 还定义以下约束：</span><span class="sxs-lookup"><span data-stu-id="023dc-129">In addition, the **DataSet** defines the following constraints:</span></span>  
  
- <span data-ttu-id="023dc-130">**Order** 表的唯一约束。</span><span class="sxs-lookup"><span data-stu-id="023dc-130">A unique constraint on the **Order** table.</span></span>  
  
    ```text
              Table: Order  
    Columns: OrderNumber
    ConstraintName: OrderNumberKey  
    Type: UniqueConstraint  
    IsPrimaryKey: False  
    ```  
  
- <span data-ttu-id="023dc-131">**Order** 表和 **OrderDetail** 表之间的关系。</span><span class="sxs-lookup"><span data-stu-id="023dc-131">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="023dc-132">**嵌套** 的属性设置为 **False** ，因为这两个元素不嵌套在架构中。</span><span class="sxs-lookup"><span data-stu-id="023dc-132">The **Nested** property is set to **False** because the two elements are not nested in the schema.</span></span>  
  
    ```text
              ParentTable: Order  
    ParentColumns: OrderNumber
    ChildTable: OrderDetail  
    ChildColumns: OrderNo
    ParentKeyConstraint: OrderNumberKey  
    ChildKeyConstraint: OrderNoRef  
    RelationName: OrderNoRef  
    Nested: False  
    ```  
  
- <span data-ttu-id="023dc-133">**OrderDetail** 表的外键约束。</span><span class="sxs-lookup"><span data-stu-id="023dc-133">A foreign key constraint on the **OrderDetail** table.</span></span>  
  
    ```text  
              ConstraintName: OrderNoRef  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: OrderNo
    RelatedTable: Order  
    RelatedColumns: OrderNumber
    ```  
  
## <a name="see-also"></a><span data-ttu-id="023dc-134">请参阅</span><span class="sxs-lookup"><span data-stu-id="023dc-134">See also</span></span>

- [<span data-ttu-id="023dc-135">将关键 XML 架构 (XSD) 约束映射到数据集约束</span><span class="sxs-lookup"><span data-stu-id="023dc-135">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="023dc-136">从 XML 架构生成数据集关系 (XSD)</span><span class="sxs-lookup"><span data-stu-id="023dc-136">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="023dc-137">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="023dc-137">ADO.NET Overview</span></span>](../ado-net-overview.md)
