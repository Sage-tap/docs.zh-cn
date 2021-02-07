---
description: 了解详细信息：从类导出架构
title: 从类导出架构
ms.date: 03/30/2017
helpviewer_keywords:
- WCF, schema import and export
- schemas [WCF], exporting from classes
- schemas [WCF]
- XsdDataContractExporter class
- XsdDataContractImporter class
ms.assetid: bb57b962-70c1-45a9-93d5-e721e340a13f
ms.openlocfilehash: f9ca33bb26237b3af9ff26b1ed693088c62e3b13
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756274"
---
# <a name="exporting-schemas-from-classes"></a><span data-ttu-id="7b7c9-103">从类导出架构</span><span class="sxs-lookup"><span data-stu-id="7b7c9-103">Exporting Schemas from Classes</span></span>

<span data-ttu-id="7b7c9-104">若要从数据协定模型中使用的类生成 XML 架构定义语言 (XSD) 架构，请使用 <xref:System.Runtime.Serialization.XsdDataContractExporter> 类。</span><span class="sxs-lookup"><span data-stu-id="7b7c9-104">To generate XML Schema definition language (XSD) schemas from classes that are used in the data contract model, use the <xref:System.Runtime.Serialization.XsdDataContractExporter> class.</span></span> <span data-ttu-id="7b7c9-105">本主题描述创建架构的过程。</span><span class="sxs-lookup"><span data-stu-id="7b7c9-105">This topic describes the process for creating schemas.</span></span>  
  
## <a name="the-export-process"></a><span data-ttu-id="7b7c9-106">导出过程</span><span class="sxs-lookup"><span data-stu-id="7b7c9-106">The Export Process</span></span>  

 <span data-ttu-id="7b7c9-107">架构导出过程以一个或多个类型开始，并生成一个 <xref:System.Xml.Schema.XmlSchemaSet> ，描述这些类型的 XML 投影。</span><span class="sxs-lookup"><span data-stu-id="7b7c9-107">The schema export process starts with one or more types and produces an <xref:System.Xml.Schema.XmlSchemaSet> that describes the XML projection of these types.</span></span>  
  
 <span data-ttu-id="7b7c9-108">`XmlSchemaSet`是 .NET Framework 的架构对象模型的一部分 (SOM) 表示一组 XSD 架构文档。</span><span class="sxs-lookup"><span data-stu-id="7b7c9-108">The `XmlSchemaSet` is part of the .NET Framework’s Schema Object Model (SOM) that represents a set of XSD Schema documents.</span></span> <span data-ttu-id="7b7c9-109">若要从 `XmlSchemaSet`创建 XSD 文档，请使用 <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> 类的 `XmlSchemaSet` 属性的架构集合。</span><span class="sxs-lookup"><span data-stu-id="7b7c9-109">To create XSD documents from an `XmlSchemaSet`, use the collection of schemas from the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the `XmlSchemaSet` class.</span></span> <span data-ttu-id="7b7c9-110">然后使用 <xref:System.Xml.Schema.XmlSchema> 序列化每个 <xref:System.Xml.Serialization.XmlSerializer>对象。</span><span class="sxs-lookup"><span data-stu-id="7b7c9-110">Then serialize each <xref:System.Xml.Schema.XmlSchema> object using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
#### <a name="to-export-schemas"></a><span data-ttu-id="7b7c9-111">导出架构</span><span class="sxs-lookup"><span data-stu-id="7b7c9-111">To export schemas</span></span>  
  
1. <span data-ttu-id="7b7c9-112">创建 <xref:System.Runtime.Serialization.XsdDataContractExporter> 的实例：</span><span class="sxs-lookup"><span data-stu-id="7b7c9-112">Create an instance of the <xref:System.Runtime.Serialization.XsdDataContractExporter>.</span></span>  
  
2. <span data-ttu-id="7b7c9-113">可选。</span><span class="sxs-lookup"><span data-stu-id="7b7c9-113">Optional.</span></span> <span data-ttu-id="7b7c9-114">在构造函数中传递一个 <xref:System.Xml.Schema.XmlSchemaSet> 。</span><span class="sxs-lookup"><span data-stu-id="7b7c9-114">Pass an <xref:System.Xml.Schema.XmlSchemaSet> in the constructor.</span></span> <span data-ttu-id="7b7c9-115">在此情况下，会将架构导出期间生成的架构添加到此 <xref:System.Xml.Schema.XmlSchemaSet> 实例中，而不是以空白 <xref:System.Xml.Schema.XmlSchemaSet>开始。</span><span class="sxs-lookup"><span data-stu-id="7b7c9-115">In this case, the schema generated during the schema export is added to this <xref:System.Xml.Schema.XmlSchemaSet> instance instead of starting with a blank <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
3. <span data-ttu-id="7b7c9-116">可选。</span><span class="sxs-lookup"><span data-stu-id="7b7c9-116">Optional.</span></span> <span data-ttu-id="7b7c9-117">调用 <xref:System.Runtime.Serialization.XsdDataContractExporter.CanExport%2A> 方法之一。</span><span class="sxs-lookup"><span data-stu-id="7b7c9-117">Call one of the <xref:System.Runtime.Serialization.XsdDataContractExporter.CanExport%2A> methods.</span></span> <span data-ttu-id="7b7c9-118">该方法确定是否可以导出指定类型。</span><span class="sxs-lookup"><span data-stu-id="7b7c9-118">The method determines whether the specified type can be exported.</span></span> <span data-ttu-id="7b7c9-119">该方法与下一个步骤中的 `Export` 方法具有相同的重载。</span><span class="sxs-lookup"><span data-stu-id="7b7c9-119">The method has the same overloads as the `Export` method in the next step.</span></span>  
  
4. <span data-ttu-id="7b7c9-120">调用 <xref:System.Runtime.Serialization.XsdDataContractExporter.Export%2A> 方法之一。</span><span class="sxs-lookup"><span data-stu-id="7b7c9-120">Call one of the <xref:System.Runtime.Serialization.XsdDataContractExporter.Export%2A> methods.</span></span> <span data-ttu-id="7b7c9-121">有三个重载采用了 <xref:System.Type>、 <xref:System.Collections.Generic.List%601> 对象的 `Type` ，或 <xref:System.Collections.Generic.List%601> 对象的 <xref:System.Reflection.Assembly> 。</span><span class="sxs-lookup"><span data-stu-id="7b7c9-121">There are three overloads taking a <xref:System.Type>, a <xref:System.Collections.Generic.List%601> of `Type` objects, or a <xref:System.Collections.Generic.List%601> of <xref:System.Reflection.Assembly> objects.</span></span> <span data-ttu-id="7b7c9-122">在最后一种情况中，将导出所有给定程序集中的所有类型。</span><span class="sxs-lookup"><span data-stu-id="7b7c9-122">In the last case, all types in all the given assemblies are exported.</span></span>  
  
     <span data-ttu-id="7b7c9-123">多次调用 `Export` 方法将导致多个项被添加到同一个 `XmlSchemaSet`中。</span><span class="sxs-lookup"><span data-stu-id="7b7c9-123">Multiple calls to the `Export` method results in multiple items being added to the same `XmlSchemaSet`.</span></span> <span data-ttu-id="7b7c9-124">如果某个类型已经存在于 `XmlSchemaSet` 中，则不会再在其中生成该类型。</span><span class="sxs-lookup"><span data-stu-id="7b7c9-124">A type is not generated into the `XmlSchemaSet` if it already exists there.</span></span> <span data-ttu-id="7b7c9-125">因此，在同一 `Export` 上多次调用 `XsdDataContractExporter` 时最好创建 `XsdDataContractExporter` 类的多个实例。</span><span class="sxs-lookup"><span data-stu-id="7b7c9-125">Therefore, calling `Export` multiple times on the same `XsdDataContractExporter` is preferable to creating multiple instances of the `XsdDataContractExporter` class.</span></span> <span data-ttu-id="7b7c9-126">这可避免生成重复的架构类型。</span><span class="sxs-lookup"><span data-stu-id="7b7c9-126">This avoids duplicate schema types from being generated.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="7b7c9-127">如果导出期间出现故障，则 `XmlSchemaSet` 将处于不可预知的状态。</span><span class="sxs-lookup"><span data-stu-id="7b7c9-127">If there is a failure during export, the `XmlSchemaSet` will be in an unpredictable state.</span></span>  
  
5. <span data-ttu-id="7b7c9-128">通过 <xref:System.Xml.Schema.XmlSchemaSet> 属性访问 <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas%2A> 。</span><span class="sxs-lookup"><span data-stu-id="7b7c9-128">Access the <xref:System.Xml.Schema.XmlSchemaSet> through the <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas%2A> property.</span></span>  
  
## <a name="export-options"></a><span data-ttu-id="7b7c9-129">导出选项</span><span class="sxs-lookup"><span data-stu-id="7b7c9-129">Export Options</span></span>  

 <span data-ttu-id="7b7c9-130">您可以将 <xref:System.Runtime.Serialization.XsdDataContractExporter.Options%2A> 的 <xref:System.Runtime.Serialization.XsdDataContractExporter> 属性设置为 <xref:System.Runtime.Serialization.ExportOptions> 类的实例以控制导出过程的各个方面。</span><span class="sxs-lookup"><span data-stu-id="7b7c9-130">You can set the <xref:System.Runtime.Serialization.XsdDataContractExporter.Options%2A> property of the <xref:System.Runtime.Serialization.XsdDataContractExporter> to an instance of the <xref:System.Runtime.Serialization.ExportOptions> class to control various aspects of the export process.</span></span> <span data-ttu-id="7b7c9-131">您可以具体设置以下选项：</span><span class="sxs-lookup"><span data-stu-id="7b7c9-131">Specifically, you can set the following options:</span></span>  
  
- <span data-ttu-id="7b7c9-132"><xref:System.Runtime.Serialization.ExportOptions.KnownTypes%2A>.</span><span class="sxs-lookup"><span data-stu-id="7b7c9-132"><xref:System.Runtime.Serialization.ExportOptions.KnownTypes%2A>.</span></span> <span data-ttu-id="7b7c9-133">这一 `Type` 集合表示要导出的类型的已知类型。</span><span class="sxs-lookup"><span data-stu-id="7b7c9-133">This collection of `Type` represents the known types for the types being exported.</span></span> <span data-ttu-id="7b7c9-134"> (有关详细信息，请参阅[数据协定已知类型](data-contract-known-types.md)。 `Export` 除了传递到方法的类型外，还会在每次调用时导出这些已知类型 ) 。 `Export`</span><span class="sxs-lookup"><span data-stu-id="7b7c9-134">(For more information, see [Data Contract Known Types](data-contract-known-types.md).) These known types are exported on every `Export` call in addition to the types passed to the `Export` method.</span></span>  
  
- <span data-ttu-id="7b7c9-135"><xref:System.Runtime.Serialization.ExportOptions.DataContractSurrogate%2A>.</span><span class="sxs-lookup"><span data-stu-id="7b7c9-135"><xref:System.Runtime.Serialization.ExportOptions.DataContractSurrogate%2A>.</span></span> <span data-ttu-id="7b7c9-136">通过此属性可以提供 <xref:System.Runtime.Serialization.IDataContractSurrogate> ，该属性将自定义导出过程。</span><span class="sxs-lookup"><span data-stu-id="7b7c9-136">An <xref:System.Runtime.Serialization.IDataContractSurrogate> can be supplied through this property that will customize the export process.</span></span> <span data-ttu-id="7b7c9-137">有关详细信息，请参阅 [数据协定代理](../extending/data-contract-surrogates.md)项。</span><span class="sxs-lookup"><span data-stu-id="7b7c9-137">For more information, see [Data Contract Surrogates](../extending/data-contract-surrogates.md).</span></span> <span data-ttu-id="7b7c9-138">默认情况下，不使用代理项。</span><span class="sxs-lookup"><span data-stu-id="7b7c9-138">By default, no surrogate is used.</span></span>  
  
## <a name="helper-methods"></a><span data-ttu-id="7b7c9-139">帮助器方法</span><span class="sxs-lookup"><span data-stu-id="7b7c9-139">Helper Methods</span></span>  

 <span data-ttu-id="7b7c9-140">除了具有导出架构的主要作用， `XsdDataContractExporter` 还具有几个有用的帮助器方法，它们可提供有关类型的信息。</span><span class="sxs-lookup"><span data-stu-id="7b7c9-140">In addition to its primary role of exporting schema, the `XsdDataContractExporter` provides several useful helper methods that provide information about types.</span></span> <span data-ttu-id="7b7c9-141">其中包括：</span><span class="sxs-lookup"><span data-stu-id="7b7c9-141">These include:</span></span>  
  
- <span data-ttu-id="7b7c9-142"><xref:System.Runtime.Serialization.XsdDataContractExporter.GetRootElementName%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="7b7c9-142"><xref:System.Runtime.Serialization.XsdDataContractExporter.GetRootElementName%2A> method.</span></span> <span data-ttu-id="7b7c9-143">此方法采用 `Type` 并返回表示根元素名称和命名空间的 <xref:System.Xml.XmlQualifiedName> ，此名称和命名空间可在此类型被序列化为根对象时使用。</span><span class="sxs-lookup"><span data-stu-id="7b7c9-143">This method takes a `Type` and returns an <xref:System.Xml.XmlQualifiedName> that represents the root element name and namespace that would be used if this type were serialized as the root object.</span></span>  
  
- <span data-ttu-id="7b7c9-144"><xref:System.Runtime.Serialization.XsdDataContractExporter.GetSchemaTypeName%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="7b7c9-144"><xref:System.Runtime.Serialization.XsdDataContractExporter.GetSchemaTypeName%2A> method.</span></span> <span data-ttu-id="7b7c9-145">此方法采用 `Type` 并返回表示 XSD 架构类型名称的 <xref:System.Xml.XmlQualifiedName> ，此名称可在此类型导出到架构中时使用。</span><span class="sxs-lookup"><span data-stu-id="7b7c9-145">This method takes a `Type` and returns an <xref:System.Xml.XmlQualifiedName> that represents the name of the XSD schema type that would be used if this type were exported to the schema.</span></span> <span data-ttu-id="7b7c9-146">对于表示架构中匿名类型的 <xref:System.Xml.Serialization.IXmlSerializable> 类型，此方法返回 `null`。</span><span class="sxs-lookup"><span data-stu-id="7b7c9-146">For <xref:System.Xml.Serialization.IXmlSerializable> types represented as anonymous types in the schema, this method returns `null`.</span></span>  
  
- <span data-ttu-id="7b7c9-147"><xref:System.Runtime.Serialization.XsdDataContractExporter.GetSchemaType%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="7b7c9-147"><xref:System.Runtime.Serialization.XsdDataContractExporter.GetSchemaType%2A> method.</span></span> <span data-ttu-id="7b7c9-148">此方法只能与表示架构中匿名类型的 <xref:System.Xml.Serialization.IXmlSerializable> 类型一起使用，并为所有其他类型返回 `null` 。</span><span class="sxs-lookup"><span data-stu-id="7b7c9-148">This method works only with <xref:System.Xml.Serialization.IXmlSerializable> types that are represented as anonymous types in the schema, and returns `null` for all other types.</span></span> <span data-ttu-id="7b7c9-149">对于匿名类型，此方法返回表示给定 <xref:System.Xml.Schema.XmlSchemaType> 的 `Type`。</span><span class="sxs-lookup"><span data-stu-id="7b7c9-149">For anonymous types, this method returns an <xref:System.Xml.Schema.XmlSchemaType> that represents a given `Type`.</span></span>  
  
 <span data-ttu-id="7b7c9-150">导出选项会影响所有这些方法。</span><span class="sxs-lookup"><span data-stu-id="7b7c9-150">Export options affect all of these methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b7c9-151">请参阅</span><span class="sxs-lookup"><span data-stu-id="7b7c9-151">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- <xref:System.Runtime.Serialization.XsdDataContractExporter>
- [<span data-ttu-id="7b7c9-152">架构导入和导出</span><span class="sxs-lookup"><span data-stu-id="7b7c9-152">Schema Import and Export</span></span>](schema-import-and-export.md)
- [<span data-ttu-id="7b7c9-153">导入架构以生成类</span><span class="sxs-lookup"><span data-stu-id="7b7c9-153">Importing Schema to Generate Classes</span></span>](importing-schema-to-generate-classes.md)
