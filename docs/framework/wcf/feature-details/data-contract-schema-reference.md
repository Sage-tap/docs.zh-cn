---
description: 了解详细信息：数据协定架构引用
title: 数据协定架构参考
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts [WCF], schema reference
ms.assetid: 9ebb0ebe-8166-4c93-980a-7c8f1f38f7c0
ms.openlocfilehash: 3449340600ea5c55ef46433031e53266a218bd6d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756638"
---
# <a name="data-contract-schema-reference"></a><span data-ttu-id="b4821-103">数据协定架构参考</span><span class="sxs-lookup"><span data-stu-id="b4821-103">Data Contract Schema Reference</span></span>

<span data-ttu-id="b4821-104">本主题介绍 <xref:System.Runtime.Serialization.DataContractSerializer> 用来描述 XML 序列化的公共语言运行库 (CLR) 类型的 XML 架构 (XSD) 的子集。</span><span class="sxs-lookup"><span data-stu-id="b4821-104">This topic describes the subset of the XML Schema (XSD) used by <xref:System.Runtime.Serialization.DataContractSerializer> to describe common language runtime (CLR) types for XML serialization.</span></span>

## <a name="datacontractserializer-mappings"></a><span data-ttu-id="b4821-105">DataContractSerializer 映射</span><span class="sxs-lookup"><span data-stu-id="b4821-105">DataContractSerializer Mappings</span></span>

<span data-ttu-id="b4821-106">`DataContractSerializer`使用元数据终结点或 "Windows Communication Foundation (WCF) 服务从 WCF 服务" 导出元数据时，将 CLR 类型映射到 XSD， [ ( # A0) ](../servicemodel-metadata-utility-tool-svcutil-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="b4821-106">The `DataContractSerializer` maps CLR types to XSD when metadata is exported from a Windows Communication Foundation (WCF) service using a metadata endpoint or the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="b4821-107">有关详细信息，请参阅 [数据协定序列化程序](data-contract-serializer.md)。</span><span class="sxs-lookup"><span data-stu-id="b4821-107">For more information, see [Data Contract Serializer](data-contract-serializer.md).</span></span>

<span data-ttu-id="b4821-108">在使用 Svcutil.exe 访问 Web 服务描述语言 (WSDL) 或 XSD 并生成服务或客户端的数据协定时， `DataContractSerializer` 还会将 XSD 映射到 CLR 类型。</span><span class="sxs-lookup"><span data-stu-id="b4821-108">The `DataContractSerializer` also maps XSD to CLR types when Svcutil.exe is used to access Web Services Description Language (WSDL) or XSD documents and generate data contracts for services or clients.</span></span>

<span data-ttu-id="b4821-109">只有符合此文档中所述需要的 XML 架构实例才可以使用 `DataContractSerializer`映射到 CLR 类型。</span><span class="sxs-lookup"><span data-stu-id="b4821-109">Only XML Schema instances that conform to requirements stated in this document can be mapped to CLR types using `DataContractSerializer`.</span></span>

### <a name="support-levels"></a><span data-ttu-id="b4821-110">支持级别</span><span class="sxs-lookup"><span data-stu-id="b4821-110">Support Levels</span></span>

<span data-ttu-id="b4821-111">`DataContractSerializer` 提供对于给定的 XML 架构功能提供以下支持级别：</span><span class="sxs-lookup"><span data-stu-id="b4821-111">The `DataContractSerializer` provides the following levels of support for a given XML Schema feature:</span></span>

- <span data-ttu-id="b4821-112">**受支持**。</span><span class="sxs-lookup"><span data-stu-id="b4821-112">**Supported**.</span></span> <span data-ttu-id="b4821-113">从此功能到使用 `DataContractSerializer`的 CLR 类型或属性（或二者）具有显式映射。</span><span class="sxs-lookup"><span data-stu-id="b4821-113">There is explicit mapping from this feature to CLR types or attributes (or both) using `DataContractSerializer`.</span></span>

- <span data-ttu-id="b4821-114">已 **忽略**。</span><span class="sxs-lookup"><span data-stu-id="b4821-114">**Ignored**.</span></span> <span data-ttu-id="b4821-115">在 `DataContractSerializer`导入的架构中允许此功能，当对代码生成无任何影响。</span><span class="sxs-lookup"><span data-stu-id="b4821-115">The feature is allowed in schemas imported by the `DataContractSerializer`, but has no effect on code generation.</span></span>

- <span data-ttu-id="b4821-116">**禁止**。</span><span class="sxs-lookup"><span data-stu-id="b4821-116">**Forbidden**.</span></span> <span data-ttu-id="b4821-117">`DataContractSerializer` 不支持导入使用此功能的架构。</span><span class="sxs-lookup"><span data-stu-id="b4821-117">The `DataContractSerializer` does not support importing a schema using the feature.</span></span> <span data-ttu-id="b4821-118">例如，Svcutil.exe 在访问带有使用这类功能的架构的 WSDL 时会转而改用 <xref:System.Xml.Serialization.XmlSerializer> 。</span><span class="sxs-lookup"><span data-stu-id="b4821-118">For example, Svcutil.exe, when accessing a WSDL with a schema that uses such a feature, falls back to using the <xref:System.Xml.Serialization.XmlSerializer> instead.</span></span> <span data-ttu-id="b4821-119">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="b4821-119">This is by default.</span></span>

## <a name="general-information"></a><span data-ttu-id="b4821-120">常规信息</span><span class="sxs-lookup"><span data-stu-id="b4821-120">General Information</span></span>

- <span data-ttu-id="b4821-121">架构命名空间在 [XML 架构](https://www.w3.org/2001/XMLSchema)中描述。</span><span class="sxs-lookup"><span data-stu-id="b4821-121">The schema namespace is described at [XML Schema](https://www.w3.org/2001/XMLSchema).</span></span> <span data-ttu-id="b4821-122">在此文档中使用前缀“xs”。</span><span class="sxs-lookup"><span data-stu-id="b4821-122">The prefix "xs" is used in this document.</span></span>

- <span data-ttu-id="b4821-123">将忽略具有非架构命名空间的任何属性。</span><span class="sxs-lookup"><span data-stu-id="b4821-123">Any attributes with a non-schema namespace are ignored.</span></span>

- <span data-ttu-id="b4821-124">将忽略任何批注（在此文档中描述的批注除外）。</span><span class="sxs-lookup"><span data-stu-id="b4821-124">Any annotations (except for those described in this document) are ignored.</span></span>

### <a name="xsschema-attributes"></a><span data-ttu-id="b4821-125">\<xs:schema>：特性</span><span class="sxs-lookup"><span data-stu-id="b4821-125">\<xs:schema>: attributes</span></span>

|<span data-ttu-id="b4821-126">Attribute</span><span class="sxs-lookup"><span data-stu-id="b4821-126">Attribute</span></span>|<span data-ttu-id="b4821-127">DataContract</span><span class="sxs-lookup"><span data-stu-id="b4821-127">DataContract</span></span>|
|---------------|------------------|
|`attributeFormDefault`|<span data-ttu-id="b4821-128">已忽略。</span><span class="sxs-lookup"><span data-stu-id="b4821-128">Ignored.</span></span>|
|`blockDefault`|<span data-ttu-id="b4821-129">已忽略。</span><span class="sxs-lookup"><span data-stu-id="b4821-129">Ignored.</span></span>|
|`elementFormDefault`|<span data-ttu-id="b4821-130">必须进行限定。</span><span class="sxs-lookup"><span data-stu-id="b4821-130">Must be qualified.</span></span> <span data-ttu-id="b4821-131">必须对一个架构的所有元素进行限定才能得到 `DataContractSerializer`的支持。</span><span class="sxs-lookup"><span data-stu-id="b4821-131">All elements must be qualified for a schema to be supported by `DataContractSerializer`.</span></span> <span data-ttu-id="b4821-132">这可以通过将设置 xs:schema/@elementFormDefault 为 "限定" 或 xs:element/@form 在每个单个元素声明上设置为 "合格" 来实现。</span><span class="sxs-lookup"><span data-stu-id="b4821-132">This can be accomplished by either setting xs:schema/@elementFormDefault to "qualified" or by setting xs:element/@form to "qualified" on each individual element declaration.</span></span>|
|`finalDefault`|<span data-ttu-id="b4821-133">已忽略。</span><span class="sxs-lookup"><span data-stu-id="b4821-133">Ignored.</span></span>|
|`Id`|<span data-ttu-id="b4821-134">已忽略。</span><span class="sxs-lookup"><span data-stu-id="b4821-134">Ignored.</span></span>|
|`targetNamespace`|<span data-ttu-id="b4821-135">支持，并已映射到数据协定命名空间。</span><span class="sxs-lookup"><span data-stu-id="b4821-135">Supported and mapped to the data contract namespace.</span></span> <span data-ttu-id="b4821-136">如果未指定此属性，则使用空白命名空间。</span><span class="sxs-lookup"><span data-stu-id="b4821-136">If this attribute is not specified, the blank namespace is used.</span></span> <span data-ttu-id="b4821-137">不能是保留的命名空间 `http://schemas.microsoft.com/2003/10/Serialization/` 。</span><span class="sxs-lookup"><span data-stu-id="b4821-137">Cannot be the reserved namespace `http://schemas.microsoft.com/2003/10/Serialization/`.</span></span>|
|`version`|<span data-ttu-id="b4821-138">已忽略。</span><span class="sxs-lookup"><span data-stu-id="b4821-138">Ignored.</span></span>|

### <a name="xsschema-contents"></a><span data-ttu-id="b4821-139">\<xs:schema>：内容</span><span class="sxs-lookup"><span data-stu-id="b4821-139">\<xs:schema>: contents</span></span>

|<span data-ttu-id="b4821-140">目录</span><span class="sxs-lookup"><span data-stu-id="b4821-140">Contents</span></span>|<span data-ttu-id="b4821-141">架构</span><span class="sxs-lookup"><span data-stu-id="b4821-141">Schema</span></span>|
|--------------|------------|
|`include`|<span data-ttu-id="b4821-142">支持。</span><span class="sxs-lookup"><span data-stu-id="b4821-142">Supported.</span></span> <span data-ttu-id="b4821-143">`DataContractSerializer` 支持 xs:include 和 xs:import。</span><span class="sxs-lookup"><span data-stu-id="b4821-143">`DataContractSerializer` supports xs:include and xs:import.</span></span> <span data-ttu-id="b4821-144">但是，从本地文件加载元数据时，Svcutil.exe 会限制下面的 `xs:include/@schemaLocation` 和 `xs:import/@location` 引用。</span><span class="sxs-lookup"><span data-stu-id="b4821-144">However, Svcutil.exe restricts following `xs:include/@schemaLocation` and `xs:import/@location` references when metadata is loaded from a local file.</span></span> <span data-ttu-id="b4821-145">在这种情况下，必须通过带外机制而非通过 `include` 来传递架构文件的列表；将忽略 `include`架构文档。</span><span class="sxs-lookup"><span data-stu-id="b4821-145">The list of schema files must be passed through an out-of-band mechanism and not through `include` in this case; `include`d schema documents are ignored.</span></span>|
|`redefine`|<span data-ttu-id="b4821-146">已禁止。</span><span class="sxs-lookup"><span data-stu-id="b4821-146">Forbidden.</span></span> <span data-ttu-id="b4821-147">出于安全方面的原因， `xs:redefine` 禁止使用 `DataContractSerializer` ： `x:redefine` 要求后跟 `schemaLocation` 。</span><span class="sxs-lookup"><span data-stu-id="b4821-147">The use of `xs:redefine` is forbidden by `DataContractSerializer` for security reasons: `x:redefine` requires `schemaLocation` to be followed.</span></span> <span data-ttu-id="b4821-148">在某些情况下，使用 DataContract 的 Svcutil.exe 会限制 `schemaLocation`的使用。</span><span class="sxs-lookup"><span data-stu-id="b4821-148">In certain circumstances, Svcutil.exe using DataContract restricts use of `schemaLocation`.</span></span>|
|`import`|<span data-ttu-id="b4821-149">支持。</span><span class="sxs-lookup"><span data-stu-id="b4821-149">Supported.</span></span> <span data-ttu-id="b4821-150">`DataContractSerializer` 支持 `xs:include` 和 `xs:import`。</span><span class="sxs-lookup"><span data-stu-id="b4821-150">`DataContractSerializer` supports `xs:include` and `xs:import`.</span></span> <span data-ttu-id="b4821-151">但是，从本地文件加载元数据时，Svcutil.exe 会限制下面的 `xs:include/@schemaLocation` 和 `xs:import/@location` 引用。</span><span class="sxs-lookup"><span data-stu-id="b4821-151">However, Svcutil.exe restricts following `xs:include/@schemaLocation` and `xs:import/@location` references when metadata is loaded from a local file.</span></span> <span data-ttu-id="b4821-152">在这种情况下，必须通过带外机制而非通过 `include` 来传递架构文件的列表；将忽略 `include`架构文档。</span><span class="sxs-lookup"><span data-stu-id="b4821-152">The list of schema files must be passed through an out-of-band mechanism and not through `include` in this case; `include`d schema documents are ignored.</span></span>|
|`simpleType`|<span data-ttu-id="b4821-153">支持。</span><span class="sxs-lookup"><span data-stu-id="b4821-153">Supported.</span></span> <span data-ttu-id="b4821-154">请参见“ `xs:simpleType` ”一节。</span><span class="sxs-lookup"><span data-stu-id="b4821-154">See the `xs:simpleType` section.</span></span>|
|`complexType`|<span data-ttu-id="b4821-155">支持，将映射到数据协定。</span><span class="sxs-lookup"><span data-stu-id="b4821-155">Supported, maps to data contracts.</span></span> <span data-ttu-id="b4821-156">请参见“ `xs:complexType` ”一节。</span><span class="sxs-lookup"><span data-stu-id="b4821-156">See the `xs:complexType` section.</span></span>|
|`group`|<span data-ttu-id="b4821-157">已忽略。</span><span class="sxs-lookup"><span data-stu-id="b4821-157">Ignored.</span></span> <span data-ttu-id="b4821-158">`DataContractSerializer` 不支持使用 `xs:group`、 `xs:attributeGroup`和 `xs:attribute`。</span><span class="sxs-lookup"><span data-stu-id="b4821-158">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="b4821-159">这些声明将作为 `xs:schema`子级被忽略，但无法从 `complexType` 或其他支持的结构内引用。</span><span class="sxs-lookup"><span data-stu-id="b4821-159">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|
|`attributeGroup`|<span data-ttu-id="b4821-160">已忽略。</span><span class="sxs-lookup"><span data-stu-id="b4821-160">Ignored.</span></span> <span data-ttu-id="b4821-161">`DataContractSerializer` 不支持使用 `xs:group`、 `xs:attributeGroup`和 `xs:attribute`。</span><span class="sxs-lookup"><span data-stu-id="b4821-161">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="b4821-162">这些声明将作为 `xs:schema`子级被忽略，但无法从 `complexType` 或其他支持的结构内引用。</span><span class="sxs-lookup"><span data-stu-id="b4821-162">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|
|`element`|<span data-ttu-id="b4821-163">支持。</span><span class="sxs-lookup"><span data-stu-id="b4821-163">Supported.</span></span> <span data-ttu-id="b4821-164">请参见“全局元素声明 (GED)”。</span><span class="sxs-lookup"><span data-stu-id="b4821-164">See Global Element Declaration (GED).</span></span>|
|`attribute`|<span data-ttu-id="b4821-165">已忽略。</span><span class="sxs-lookup"><span data-stu-id="b4821-165">Ignored.</span></span> <span data-ttu-id="b4821-166">`DataContractSerializer` 不支持使用 `xs:group`、 `xs:attributeGroup`和 `xs:attribute`。</span><span class="sxs-lookup"><span data-stu-id="b4821-166">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="b4821-167">这些声明将作为 `xs:schema`子级被忽略，但无法从 `complexType` 或其他支持的结构内引用。</span><span class="sxs-lookup"><span data-stu-id="b4821-167">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|
|`notation`|<span data-ttu-id="b4821-168">已忽略。</span><span class="sxs-lookup"><span data-stu-id="b4821-168">Ignored.</span></span>|

## <a name="complex-types--xscomplextype"></a><span data-ttu-id="b4821-169">复杂类型– \<xs:complexType></span><span class="sxs-lookup"><span data-stu-id="b4821-169">Complex Types – \<xs:complexType></span></span>

### <a name="general-information"></a><span data-ttu-id="b4821-170">常规信息</span><span class="sxs-lookup"><span data-stu-id="b4821-170">General Information</span></span>

<span data-ttu-id="b4821-171">每个复杂类型 \<xs:complexType> 映射到一个数据协定。</span><span class="sxs-lookup"><span data-stu-id="b4821-171">Each complex type \<xs:complexType> maps to a data contract.</span></span>

### <a name="xscomplextype-attributes"></a><span data-ttu-id="b4821-172">\<xs:complexType>：特性</span><span class="sxs-lookup"><span data-stu-id="b4821-172">\<xs:complexType>: attributes</span></span>

|<span data-ttu-id="b4821-173">Attribute</span><span class="sxs-lookup"><span data-stu-id="b4821-173">Attribute</span></span>|<span data-ttu-id="b4821-174">架构</span><span class="sxs-lookup"><span data-stu-id="b4821-174">Schema</span></span>|
|---------------|------------|
|`abstract`|<span data-ttu-id="b4821-175">必须是 false（默认值）。</span><span class="sxs-lookup"><span data-stu-id="b4821-175">Must be false (default).</span></span>|
|`block`|<span data-ttu-id="b4821-176">已禁止。</span><span class="sxs-lookup"><span data-stu-id="b4821-176">Forbidden.</span></span>|
|`final`|<span data-ttu-id="b4821-177">已忽略。</span><span class="sxs-lookup"><span data-stu-id="b4821-177">Ignored.</span></span>|
|`id`|<span data-ttu-id="b4821-178">已忽略。</span><span class="sxs-lookup"><span data-stu-id="b4821-178">Ignored.</span></span>|
|`mixed`|<span data-ttu-id="b4821-179">必须是 false（默认值）。</span><span class="sxs-lookup"><span data-stu-id="b4821-179">Must be false (default).</span></span>|
|`name`|<span data-ttu-id="b4821-180">支持，并已映射到数据协定名称。</span><span class="sxs-lookup"><span data-stu-id="b4821-180">Supported and mapped to the data contract name.</span></span> <span data-ttu-id="b4821-181">如果名称中有句点，则尝试将类型映射到内部类型。</span><span class="sxs-lookup"><span data-stu-id="b4821-181">If there are periods in the name, an attempt is made to map the type to an inner type.</span></span> <span data-ttu-id="b4821-182">例如，名为 `A.B` 的复杂类型将映射到一个数据协定类型，该数据协定类型是具有数据协定名称 `A`的类型的内部类型，但前提是这种数据协定类型存在。</span><span class="sxs-lookup"><span data-stu-id="b4821-182">For example, a complex type named `A.B` maps to a data contract type that is an inner type of a type with the data contract name `A`, but only if such a data contract type exists.</span></span> <span data-ttu-id="b4821-183">嵌套可能有多个级别：例如， `A.B.C` 可以是内部类型，但前提是 `A` 和 `A.B` 两者都存在。</span><span class="sxs-lookup"><span data-stu-id="b4821-183">More than one level of nesting is possible: for example, `A.B.C` can be an inner type, but only if `A` and `A.B` both exist.</span></span>|

### <a name="xscomplextype-contents"></a><span data-ttu-id="b4821-184">\<xs:complexType>：内容</span><span class="sxs-lookup"><span data-stu-id="b4821-184">\<xs:complexType>: contents</span></span>

|<span data-ttu-id="b4821-185">目录</span><span class="sxs-lookup"><span data-stu-id="b4821-185">Contents</span></span>|<span data-ttu-id="b4821-186">架构</span><span class="sxs-lookup"><span data-stu-id="b4821-186">Schema</span></span>|
|--------------|------------|
|`simpleContent`|<span data-ttu-id="b4821-187">禁止扩展。</span><span class="sxs-lookup"><span data-stu-id="b4821-187">Extensions are forbidden.</span></span><br /><br /> <span data-ttu-id="b4821-188">仅允许从 `anySimpleType`进行限制。</span><span class="sxs-lookup"><span data-stu-id="b4821-188">Restriction is allowed only from `anySimpleType`.</span></span>|
|`complexContent`|<span data-ttu-id="b4821-189">支持。</span><span class="sxs-lookup"><span data-stu-id="b4821-189">Supported.</span></span> <span data-ttu-id="b4821-190">请参见“继承”。</span><span class="sxs-lookup"><span data-stu-id="b4821-190">See "Inheritance".</span></span>|
|`group`|<span data-ttu-id="b4821-191">已禁止。</span><span class="sxs-lookup"><span data-stu-id="b4821-191">Forbidden.</span></span>|
|`all`|<span data-ttu-id="b4821-192">已禁止。</span><span class="sxs-lookup"><span data-stu-id="b4821-192">Forbidden.</span></span>|
|`choice`|<span data-ttu-id="b4821-193">禁止</span><span class="sxs-lookup"><span data-stu-id="b4821-193">Forbidden</span></span>|
|`sequence`|<span data-ttu-id="b4821-194">支持，将映射到数据协定的数据成员。</span><span class="sxs-lookup"><span data-stu-id="b4821-194">Supported, maps to data members of a data contract.</span></span>|
|`attribute`|<span data-ttu-id="b4821-195">已禁止，即使 use="prohibited"（但有一个例外）。</span><span class="sxs-lookup"><span data-stu-id="b4821-195">Forbidden, even if use="prohibited" (with one exception).</span></span> <span data-ttu-id="b4821-196">只支持标准序列化架构命名空间中的可选属性。</span><span class="sxs-lookup"><span data-stu-id="b4821-196">Only optional attributes from the Standard Serialization Schema namespace are supported.</span></span> <span data-ttu-id="b4821-197">这些属性不映射到数据协定编程模型中的数据成员。</span><span class="sxs-lookup"><span data-stu-id="b4821-197">They do not map to data members in the data contract programming model.</span></span> <span data-ttu-id="b4821-198">当前，仅有一个这样的属性有意义，将在“ISerializable”一节讨论。</span><span class="sxs-lookup"><span data-stu-id="b4821-198">Currently, only one such attribute has meaning and is discussed in the ISerializable section.</span></span> <span data-ttu-id="b4821-199">将忽略所有其他成员。</span><span class="sxs-lookup"><span data-stu-id="b4821-199">All others are ignored.</span></span>|
|`attributeGroup`|<span data-ttu-id="b4821-200">已禁止。</span><span class="sxs-lookup"><span data-stu-id="b4821-200">Forbidden.</span></span> <span data-ttu-id="b4821-201">在 WCF v1 版本中， `DataContractSerializer` 将忽略内部的 `attributeGroup` 存在 `xs:complexType` 。</span><span class="sxs-lookup"><span data-stu-id="b4821-201">In the WCF v1 release, `DataContractSerializer` ignores the presence of `attributeGroup` inside `xs:complexType`.</span></span>|
|`anyAttribute`|<span data-ttu-id="b4821-202">已禁止。</span><span class="sxs-lookup"><span data-stu-id="b4821-202">Forbidden.</span></span>|
|<span data-ttu-id="b4821-203">(empty)</span><span class="sxs-lookup"><span data-stu-id="b4821-203">(empty)</span></span>|<span data-ttu-id="b4821-204">映射到没有数据成员的数据协定。</span><span class="sxs-lookup"><span data-stu-id="b4821-204">Maps to a data contract with no data members.</span></span>|

### <a name="xssequence-in-a-complex-type-attributes"></a><span data-ttu-id="b4821-205">\<xs:sequence> 在复杂类型中：特性</span><span class="sxs-lookup"><span data-stu-id="b4821-205">\<xs:sequence> in a complex type: attributes</span></span>

|<span data-ttu-id="b4821-206">Attribute</span><span class="sxs-lookup"><span data-stu-id="b4821-206">Attribute</span></span>|<span data-ttu-id="b4821-207">架构</span><span class="sxs-lookup"><span data-stu-id="b4821-207">Schema</span></span>|
|---------------|------------|
|`id`|<span data-ttu-id="b4821-208">已忽略。</span><span class="sxs-lookup"><span data-stu-id="b4821-208">Ignored.</span></span>|
|`maxOccurs`|<span data-ttu-id="b4821-209">必须是 1（默认值）。</span><span class="sxs-lookup"><span data-stu-id="b4821-209">Must be 1 (default).</span></span>|
|`minOccurs`|<span data-ttu-id="b4821-210">必须是 1（默认值）。</span><span class="sxs-lookup"><span data-stu-id="b4821-210">Must be 1 (default).</span></span>|

### <a name="xssequence-in-a-complex-type-contents"></a><span data-ttu-id="b4821-211">\<xs:sequence> 在复杂类型中：内容</span><span class="sxs-lookup"><span data-stu-id="b4821-211">\<xs:sequence> in a complex type: contents</span></span>

|<span data-ttu-id="b4821-212">目录</span><span class="sxs-lookup"><span data-stu-id="b4821-212">Contents</span></span>|<span data-ttu-id="b4821-213">架构</span><span class="sxs-lookup"><span data-stu-id="b4821-213">Schema</span></span>|
|--------------|------------|
|`element`|<span data-ttu-id="b4821-214">每个实例都映射到一个数据成员。</span><span class="sxs-lookup"><span data-stu-id="b4821-214">Each instance maps to a data member.</span></span>|
|`group`|<span data-ttu-id="b4821-215">已禁止。</span><span class="sxs-lookup"><span data-stu-id="b4821-215">Forbidden.</span></span>|
|`choice`|<span data-ttu-id="b4821-216">已禁止。</span><span class="sxs-lookup"><span data-stu-id="b4821-216">Forbidden.</span></span>|
|`sequence`|<span data-ttu-id="b4821-217">已禁止。</span><span class="sxs-lookup"><span data-stu-id="b4821-217">Forbidden.</span></span>|
|`any`|<span data-ttu-id="b4821-218">已禁止。</span><span class="sxs-lookup"><span data-stu-id="b4821-218">Forbidden.</span></span>|
|<span data-ttu-id="b4821-219">(empty)</span><span class="sxs-lookup"><span data-stu-id="b4821-219">(empty)</span></span>|<span data-ttu-id="b4821-220">映射到没有数据成员的数据协定。</span><span class="sxs-lookup"><span data-stu-id="b4821-220">Maps to a data contract with no data members.</span></span>|

## <a name="elements--xselement"></a><span data-ttu-id="b4821-221">单元 \<xs:element></span><span class="sxs-lookup"><span data-stu-id="b4821-221">Elements – \<xs:element></span></span>

### <a name="general-information"></a><span data-ttu-id="b4821-222">常规信息</span><span class="sxs-lookup"><span data-stu-id="b4821-222">General Information</span></span>

<span data-ttu-id="b4821-223">`<xs:element>` 会在以下上下文中发生：</span><span class="sxs-lookup"><span data-stu-id="b4821-223">`<xs:element>` can occur in the following contexts:</span></span>

- <span data-ttu-id="b4821-224">在描述常规（非集合）数据协定的数据成员的 `<xs:sequence>`内发生。</span><span class="sxs-lookup"><span data-stu-id="b4821-224">It can occur within an `<xs:sequence>`, which describes a data member of a regular (non-collection) data contract.</span></span> <span data-ttu-id="b4821-225">在这种情况下， `maxOccurs` 属性必须为 1。</span><span class="sxs-lookup"><span data-stu-id="b4821-225">In this case, the `maxOccurs` attribute must be 1.</span></span> <span data-ttu-id="b4821-226">（不允许值为 0。）</span><span class="sxs-lookup"><span data-stu-id="b4821-226">(A value of 0 is not allowed).</span></span>

- <span data-ttu-id="b4821-227">在描述集合数据协定的数据成员的 `<xs:sequence>`内发生。</span><span class="sxs-lookup"><span data-stu-id="b4821-227">It can occur within an `<xs:sequence>`, which describes a data member of a collection data contract.</span></span> <span data-ttu-id="b4821-228">在这种情况下， `maxOccurs` 属性必须大于 1 或为“unbounded”。</span><span class="sxs-lookup"><span data-stu-id="b4821-228">In this case, the `maxOccurs` attribute must be greater than 1 or "unbounded".</span></span>

- <span data-ttu-id="b4821-229">在作为全局元素声明 (GED) 的 `<xs:schema>` 内发生。</span><span class="sxs-lookup"><span data-stu-id="b4821-229">It can occur within an `<xs:schema>` as a Global Element Declaration (GED).</span></span>

### <a name="xselement-with-maxoccurs1-within-an-xssequence-data-members"></a><span data-ttu-id="b4821-230">\<xs:element> 在 (的数据成员内使用 maxOccurs = 1 \<xs:sequence>) </span><span class="sxs-lookup"><span data-stu-id="b4821-230">\<xs:element> with maxOccurs=1 within an \<xs:sequence> (Data Members)</span></span>

|<span data-ttu-id="b4821-231">Attribute</span><span class="sxs-lookup"><span data-stu-id="b4821-231">Attribute</span></span>|<span data-ttu-id="b4821-232">架构</span><span class="sxs-lookup"><span data-stu-id="b4821-232">Schema</span></span>|
|---------------|------------|
|`ref`|<span data-ttu-id="b4821-233">已禁止。</span><span class="sxs-lookup"><span data-stu-id="b4821-233">Forbidden.</span></span>|
|`name`|<span data-ttu-id="b4821-234">支持，映射到数据成员名称。</span><span class="sxs-lookup"><span data-stu-id="b4821-234">Supported, maps to the data member name.</span></span>|
|`type`|<span data-ttu-id="b4821-235">支持，映射到数据成员类型。</span><span class="sxs-lookup"><span data-stu-id="b4821-235">Supported, maps to the data member type.</span></span> <span data-ttu-id="b4821-236">有关更多信息，请参见“类型/基元映射”。</span><span class="sxs-lookup"><span data-stu-id="b4821-236">For more information, see Type/primitive mapping.</span></span> <span data-ttu-id="b4821-237">如果未指定（并且元素不包含匿名类型），则假定 `xs:anyType` 。</span><span class="sxs-lookup"><span data-stu-id="b4821-237">If not specified (and the element does not contain an anonymous type), `xs:anyType` is assumed.</span></span>|
|`block`|<span data-ttu-id="b4821-238">已忽略。</span><span class="sxs-lookup"><span data-stu-id="b4821-238">Ignored.</span></span>|
|`default`|<span data-ttu-id="b4821-239">已禁止。</span><span class="sxs-lookup"><span data-stu-id="b4821-239">Forbidden.</span></span>|
|`fixed`|<span data-ttu-id="b4821-240">已禁止。</span><span class="sxs-lookup"><span data-stu-id="b4821-240">Forbidden.</span></span>|
|`form`|<span data-ttu-id="b4821-241">必须进行限定。</span><span class="sxs-lookup"><span data-stu-id="b4821-241">Must be qualified.</span></span> <span data-ttu-id="b4821-242">可以通过 `elementFormDefault` 上的 `xs:schema`来设置此特性。</span><span class="sxs-lookup"><span data-stu-id="b4821-242">This attribute can be set through `elementFormDefault` on `xs:schema`.</span></span>|
|`id`|<span data-ttu-id="b4821-243">已忽略。</span><span class="sxs-lookup"><span data-stu-id="b4821-243">Ignored.</span></span>|
|`maxOccurs`|<span data-ttu-id="b4821-244">1</span><span class="sxs-lookup"><span data-stu-id="b4821-244">1</span></span>|
|`minOccurs`|<span data-ttu-id="b4821-245">映射到数据成员的 <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> 属性（当`IsRequired` 为 1 时， `minOccurs` 为 true）。</span><span class="sxs-lookup"><span data-stu-id="b4821-245">Maps to the <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property of a data member (`IsRequired` is true when `minOccurs` is 1).</span></span>|
|`nillable`|<span data-ttu-id="b4821-246">影响类型映射。</span><span class="sxs-lookup"><span data-stu-id="b4821-246">Affects type mapping.</span></span> <span data-ttu-id="b4821-247">请参见“类型/基元映射”。</span><span class="sxs-lookup"><span data-stu-id="b4821-247">See Type/primitive mapping.</span></span>|

### <a name="xselement-with-maxoccurs1-within-an-xssequence-collections"></a><span data-ttu-id="b4821-248">\<xs:element> 在 (集合内使用 maxOccurs>1 \<xs:sequence>) </span><span class="sxs-lookup"><span data-stu-id="b4821-248">\<xs:element> with maxOccurs>1 within an \<xs:sequence> (Collections)</span></span>

- <span data-ttu-id="b4821-249">映射到 <xref:System.Runtime.Serialization.CollectionDataContractAttribute>。</span><span class="sxs-lookup"><span data-stu-id="b4821-249">Maps to a <xref:System.Runtime.Serialization.CollectionDataContractAttribute>.</span></span>

- <span data-ttu-id="b4821-250">在集合类型中，在 xs:sequence 内只允许一个 xs:element。</span><span class="sxs-lookup"><span data-stu-id="b4821-250">In collection types, only one xs:element is allowed within an xs:sequence.</span></span>

 <span data-ttu-id="b4821-251">集合可以是以下类型之一：</span><span class="sxs-lookup"><span data-stu-id="b4821-251">Collections can be of the following types:</span></span>

- <span data-ttu-id="b4821-252">常规集合（例如，数组）。</span><span class="sxs-lookup"><span data-stu-id="b4821-252">Regular collections (for example, arrays).</span></span>

- <span data-ttu-id="b4821-253">字典集合（将一个值映射到另一个值，例如 <xref:System.Collections.Hashtable>）。</span><span class="sxs-lookup"><span data-stu-id="b4821-253">Dictionary collections (mapping one value to another; for example, a <xref:System.Collections.Hashtable>).</span></span>

- <span data-ttu-id="b4821-254">字典和密钥/值对类型的数组之间仅有的差别在于生成的编程模型。</span><span class="sxs-lookup"><span data-stu-id="b4821-254">The only difference between a dictionary and an array of a key/value pair type is in the generated programming model.</span></span> <span data-ttu-id="b4821-255">有一种架构批注机制可用来指示给定的类型是一个字典集合。</span><span class="sxs-lookup"><span data-stu-id="b4821-255">There is a schema annotation mechanism that can be used to indicate that a given type is a dictionary collection.</span></span>

<span data-ttu-id="b4821-256">`ref`、 `block`、 `default`、 `fixed`, `form`和 `id` 属性的规则与非集合情况下的规则相同。</span><span class="sxs-lookup"><span data-stu-id="b4821-256">The rules for the `ref`, `block`, `default`, `fixed`, `form`, and `id` attributes are the same as for the non-collection case.</span></span> <span data-ttu-id="b4821-257">其他属性包含下表中的规则。</span><span class="sxs-lookup"><span data-stu-id="b4821-257">Other attributes include those in the following table.</span></span>

|<span data-ttu-id="b4821-258">Attribute</span><span class="sxs-lookup"><span data-stu-id="b4821-258">Attribute</span></span>|<span data-ttu-id="b4821-259">架构</span><span class="sxs-lookup"><span data-stu-id="b4821-259">Schema</span></span>|
|---------------|------------|
|`name`|<span data-ttu-id="b4821-260">支持，映射到 <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> 属性 (Attribute) 中的 `CollectionDataContractAttribute` 属性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="b4821-260">Supported, maps to the <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> property in the `CollectionDataContractAttribute` attribute.</span></span>|
|`type`|<span data-ttu-id="b4821-261">支持，映射到集合中存储的类型。</span><span class="sxs-lookup"><span data-stu-id="b4821-261">Supported, maps to the type stored in the collection.</span></span>|
|`maxOccurs`|<span data-ttu-id="b4821-262">大于 1 或为“unbounded”。</span><span class="sxs-lookup"><span data-stu-id="b4821-262">Greater than 1 or "unbounded".</span></span> <span data-ttu-id="b4821-263">DC 架构应使用“unbounded”。</span><span class="sxs-lookup"><span data-stu-id="b4821-263">The DC schema should use "unbounded".</span></span>|
|`minOccurs`|<span data-ttu-id="b4821-264">已忽略。</span><span class="sxs-lookup"><span data-stu-id="b4821-264">Ignored.</span></span>|
|`nillable`|<span data-ttu-id="b4821-265">影响类型映射。</span><span class="sxs-lookup"><span data-stu-id="b4821-265">Affects type mapping.</span></span> <span data-ttu-id="b4821-266">对于字典集合，忽略此属性。</span><span class="sxs-lookup"><span data-stu-id="b4821-266">This attribute is ignored for dictionary collections.</span></span>|

### <a name="xselement-within-an-xsschema-global-element-declaration"></a><span data-ttu-id="b4821-267">\<xs:element> 在 \<xs:schema> 全局元素声明中</span><span class="sxs-lookup"><span data-stu-id="b4821-267">\<xs:element> within an \<xs:schema> Global Element Declaration</span></span>

- <span data-ttu-id="b4821-268">在架构中的某个类型时具有相同的名称和命名空间的全局元素声明 (GED) 或在其内部指定匿名类型的全局元素声明 (GED) 可认为是与该类型相关联。</span><span class="sxs-lookup"><span data-stu-id="b4821-268">A Global Element Declaration (GED) that has the same name and namespace as a type in schema, or that defines an anonymous type inside itself, is said to be associated with the type.</span></span>

- <span data-ttu-id="b4821-269">架构导出：将为每个生成的（简单的和复杂的）类型生成相关联的 GED。</span><span class="sxs-lookup"><span data-stu-id="b4821-269">Schema export: associated GEDs are generated for every generated type, both simple and complex.</span></span>

- <span data-ttu-id="b4821-270">反序列化/序列化：将关联的 GED 用作类型的根元素。</span><span class="sxs-lookup"><span data-stu-id="b4821-270">Deserialization/serialization: associated GEDs are used as root elements for the type.</span></span>

- <span data-ttu-id="b4821-271">架构导入：当关联的 GED 遵循以下规则时，将不是必需的并可忽略（除非它们定义了类型）。</span><span class="sxs-lookup"><span data-stu-id="b4821-271">Schema import: associated GEDs are not required and are ignored if they follow the following rules (unless they define types).</span></span>

|<span data-ttu-id="b4821-272">Attribute</span><span class="sxs-lookup"><span data-stu-id="b4821-272">Attribute</span></span>|<span data-ttu-id="b4821-273">架构</span><span class="sxs-lookup"><span data-stu-id="b4821-273">Schema</span></span>|
|---------------|------------|
|`abstract`|<span data-ttu-id="b4821-274">对于关联的 GED 必须是 false。</span><span class="sxs-lookup"><span data-stu-id="b4821-274">Must be false for associated GEDs.</span></span>|
|`block`|<span data-ttu-id="b4821-275">在关联的 GED 中禁止。</span><span class="sxs-lookup"><span data-stu-id="b4821-275">Forbidden in associated GEDs.</span></span>|
|`default`|<span data-ttu-id="b4821-276">在关联的 GED 中禁止。</span><span class="sxs-lookup"><span data-stu-id="b4821-276">Forbidden in associated GEDs.</span></span>|
|`final`|<span data-ttu-id="b4821-277">对于关联的 GED 必须是 false。</span><span class="sxs-lookup"><span data-stu-id="b4821-277">Must be false for associated GEDs.</span></span>|
|`fixed`|<span data-ttu-id="b4821-278">在关联的 GED 中禁止。</span><span class="sxs-lookup"><span data-stu-id="b4821-278">Forbidden in associated GEDs.</span></span>|
|`id`|<span data-ttu-id="b4821-279">已忽略。</span><span class="sxs-lookup"><span data-stu-id="b4821-279">Ignored.</span></span>|
|`name`|<span data-ttu-id="b4821-280">支持。</span><span class="sxs-lookup"><span data-stu-id="b4821-280">Supported.</span></span> <span data-ttu-id="b4821-281">请参见关联的 GED 的定义。</span><span class="sxs-lookup"><span data-stu-id="b4821-281">See the definition of associated GEDs.</span></span>|
|`nillable`|<span data-ttu-id="b4821-282">对于关联的 GED 必须是 true。</span><span class="sxs-lookup"><span data-stu-id="b4821-282">Must be true for associated GEDs.</span></span>|
|`substitutionGroup`|<span data-ttu-id="b4821-283">在关联的 GED 中禁止。</span><span class="sxs-lookup"><span data-stu-id="b4821-283">Forbidden in associated GEDs.</span></span>|
|`type`|<span data-ttu-id="b4821-284">支持，必须与关联的 GED 的关联类型相匹配（除非该元素包含一个匿名类型）。</span><span class="sxs-lookup"><span data-stu-id="b4821-284">Supported, and must match the associated type for associated GEDs (unless the element contains an anonymous type).</span></span>|

### <a name="xselement-contents"></a><span data-ttu-id="b4821-285">\<xs:element>：内容</span><span class="sxs-lookup"><span data-stu-id="b4821-285">\<xs:element>: contents</span></span>

|<span data-ttu-id="b4821-286">目录</span><span class="sxs-lookup"><span data-stu-id="b4821-286">Contents</span></span>|<span data-ttu-id="b4821-287">架构</span><span class="sxs-lookup"><span data-stu-id="b4821-287">Schema</span></span>|
|--------------|------------|
|`simpleType`|<span data-ttu-id="b4821-288">支持。\*</span><span class="sxs-lookup"><span data-stu-id="b4821-288">Supported.\*</span></span>|
|`complexType`|<span data-ttu-id="b4821-289">支持。\*</span><span class="sxs-lookup"><span data-stu-id="b4821-289">Supported.\*</span></span>|
|`unique`|<span data-ttu-id="b4821-290">已忽略。</span><span class="sxs-lookup"><span data-stu-id="b4821-290">Ignored.</span></span>|
|`key`|<span data-ttu-id="b4821-291">已忽略。</span><span class="sxs-lookup"><span data-stu-id="b4821-291">Ignored.</span></span>|
|`keyref`|<span data-ttu-id="b4821-292">已忽略。</span><span class="sxs-lookup"><span data-stu-id="b4821-292">Ignored.</span></span>|
|<span data-ttu-id="b4821-293">(空白)</span><span class="sxs-lookup"><span data-stu-id="b4821-293">(blank)</span></span>|<span data-ttu-id="b4821-294">支持。</span><span class="sxs-lookup"><span data-stu-id="b4821-294">Supported.</span></span>|

<span data-ttu-id="b4821-295">\* 对 `simpleType` `complexType,` 匿名类型使用和映射与非匿名类型的映射相同，不同之处在于不存在匿名数据协定，因此创建命名的数据协定，并使用从元素名称派生的生成名称。</span><span class="sxs-lookup"><span data-stu-id="b4821-295">\* When using the `simpleType` and `complexType,` mapping for anonymous types is the same as for non-anonymous types, except that there is no anonymous data contracts, and so a named data contract is created, with a generated name derived from the element name.</span></span> <span data-ttu-id="b4821-296">下面的列表中是匿名类型的规则：</span><span class="sxs-lookup"><span data-stu-id="b4821-296">The rules for anonymous types are in the following list:</span></span>

- <span data-ttu-id="b4821-297">WCF 实现详细信息：如果 `xs:element` 名称不包含句点，则匿名类型映射到外部数据协定类型的内部类型。</span><span class="sxs-lookup"><span data-stu-id="b4821-297">WCF implementation detail: If the `xs:element` name does not contain periods, the anonymous type maps to an inner type of the outer data contract type.</span></span> <span data-ttu-id="b4821-298">如果名称包含句点，则结果数据协定类型是独立的（不是内部类型）。</span><span class="sxs-lookup"><span data-stu-id="b4821-298">If the name contains periods, the resulting data contract type is independent (not an inner type).</span></span>

- <span data-ttu-id="b4821-299">内部类型的生成数据协定名称是由外部类型的数据协定名称后跟一个句点、元素名称和字符串“Type”构成。</span><span class="sxs-lookup"><span data-stu-id="b4821-299">The generated data contract name of the inner type is the data contract name of the outer type followed by a period, the name of the element, and the string "Type".</span></span>

- <span data-ttu-id="b4821-300">如果已存在具有这个名称的数据协定，则通过在该名称后追加“1”、“2”、“3”等以使名称具有唯一性，从而创建一个唯一的名称。</span><span class="sxs-lookup"><span data-stu-id="b4821-300">If a data contract with such a name already exists, the name is made unique by appending "1", "2", "3", and so on until a unique name is created.</span></span>

## <a name="simple-types---xssimpletype"></a><span data-ttu-id="b4821-301">简单类型- \<xs:simpleType></span><span class="sxs-lookup"><span data-stu-id="b4821-301">Simple Types - \<xs:simpleType></span></span>

### <a name="xssimpletype-attributes"></a><span data-ttu-id="b4821-302">\<xs:simpleType>：特性</span><span class="sxs-lookup"><span data-stu-id="b4821-302">\<xs:simpleType>: attributes</span></span>

|<span data-ttu-id="b4821-303">Attribute</span><span class="sxs-lookup"><span data-stu-id="b4821-303">Attribute</span></span>|<span data-ttu-id="b4821-304">架构</span><span class="sxs-lookup"><span data-stu-id="b4821-304">Schema</span></span>|
|---------------|------------|
|`final`|<span data-ttu-id="b4821-305">已忽略。</span><span class="sxs-lookup"><span data-stu-id="b4821-305">Ignored.</span></span>|
|`id`|<span data-ttu-id="b4821-306">已忽略。</span><span class="sxs-lookup"><span data-stu-id="b4821-306">Ignored.</span></span>|
|`name`|<span data-ttu-id="b4821-307">支持，映射到数据协定名称。</span><span class="sxs-lookup"><span data-stu-id="b4821-307">Supported, maps to the data contract name.</span></span>|

### <a name="xssimpletype-contents"></a><span data-ttu-id="b4821-308">\<xs:simpleType>：内容</span><span class="sxs-lookup"><span data-stu-id="b4821-308">\<xs:simpleType>: contents</span></span>

|<span data-ttu-id="b4821-309">目录</span><span class="sxs-lookup"><span data-stu-id="b4821-309">Contents</span></span>|<span data-ttu-id="b4821-310">架构</span><span class="sxs-lookup"><span data-stu-id="b4821-310">Schema</span></span>|
|--------------|------------|
|`restriction`|<span data-ttu-id="b4821-311">支持。</span><span class="sxs-lookup"><span data-stu-id="b4821-311">Supported.</span></span> <span data-ttu-id="b4821-312">映射到枚举数据协定。</span><span class="sxs-lookup"><span data-stu-id="b4821-312">Maps to enumeration data contracts.</span></span> <span data-ttu-id="b4821-313">如果与枚举模式不匹配，则忽略此属性。</span><span class="sxs-lookup"><span data-stu-id="b4821-313">This attribute is ignored if it does not match the enumeration pattern.</span></span> <span data-ttu-id="b4821-314">请参见“ `xs:simpleType` 限制”一节。</span><span class="sxs-lookup"><span data-stu-id="b4821-314">See the `xs:simpleType` restrictions section.</span></span>|
|`list`|<span data-ttu-id="b4821-315">支持。</span><span class="sxs-lookup"><span data-stu-id="b4821-315">Supported.</span></span> <span data-ttu-id="b4821-316">映射到标志枚举数据协定。</span><span class="sxs-lookup"><span data-stu-id="b4821-316">Maps to flag enumeration data contracts.</span></span> <span data-ttu-id="b4821-317">请参见“ `xs:simpleType` 列表”一节。</span><span class="sxs-lookup"><span data-stu-id="b4821-317">See the `xs:simpleType` lists section.</span></span>|
|`union`|<span data-ttu-id="b4821-318">已禁止。</span><span class="sxs-lookup"><span data-stu-id="b4821-318">Forbidden.</span></span>|

### \<xs:restriction>

- <span data-ttu-id="b4821-319">仅 base="`xs:anyType`" 支持复杂类型限制。</span><span class="sxs-lookup"><span data-stu-id="b4821-319">Complex type restrictions are supported only for base="`xs:anyType`".</span></span>

- <span data-ttu-id="b4821-320">除 `xs:string` 之外没有任何限制方面的 `xs:enumeration` 的简单类型限制映射到枚举数据协定。</span><span class="sxs-lookup"><span data-stu-id="b4821-320">Simple type restrictions of `xs:string` that do not have any restriction facets other than `xs:enumeration` are mapped to enumeration data contracts.</span></span>

- <span data-ttu-id="b4821-321">将所有其他简单类型限制映射到它们限制的类型。</span><span class="sxs-lookup"><span data-stu-id="b4821-321">All other simple type restrictions are mapped to the types they restrict.</span></span> <span data-ttu-id="b4821-322">例如， `xs:int` 的限制将映射到一个整数，就像 `xs:int` 自身一样。</span><span class="sxs-lookup"><span data-stu-id="b4821-322">For example, a restriction of `xs:int` maps to an integer, just as `xs:int` itself does.</span></span> <span data-ttu-id="b4821-323">有关基元类型映射的详细信息，请参阅类型/基元映射。</span><span class="sxs-lookup"><span data-stu-id="b4821-323">For more information about primitive type mapping, see Type/primitive mapping.</span></span>

### <a name="xsrestriction-attributes"></a><span data-ttu-id="b4821-324">\<xs:restriction>：特性</span><span class="sxs-lookup"><span data-stu-id="b4821-324">\<xs:restriction>: attributes</span></span>

|<span data-ttu-id="b4821-325">Attribute</span><span class="sxs-lookup"><span data-stu-id="b4821-325">Attribute</span></span>|<span data-ttu-id="b4821-326">架构</span><span class="sxs-lookup"><span data-stu-id="b4821-326">Schema</span></span>|
|---------------|------------|
|`base`|<span data-ttu-id="b4821-327">必须是一个支持的简单类型或 `xs:anyType`。</span><span class="sxs-lookup"><span data-stu-id="b4821-327">Must be a supported simple type or `xs:anyType`.</span></span>|
|`id`|<span data-ttu-id="b4821-328">已忽略。</span><span class="sxs-lookup"><span data-stu-id="b4821-328">Ignored.</span></span>|

### <a name="xsrestriction-for-all-other-cases-contents"></a><span data-ttu-id="b4821-329">\<xs:restriction> 对于所有其他情况：内容</span><span class="sxs-lookup"><span data-stu-id="b4821-329">\<xs:restriction> for all other cases: contents</span></span>

|<span data-ttu-id="b4821-330">目录</span><span class="sxs-lookup"><span data-stu-id="b4821-330">Contents</span></span>|<span data-ttu-id="b4821-331">架构</span><span class="sxs-lookup"><span data-stu-id="b4821-331">Schema</span></span>|
|--------------|------------|
|`simpleType`|<span data-ttu-id="b4821-332">如果存在，必须派生自支持的基元类型。</span><span class="sxs-lookup"><span data-stu-id="b4821-332">If present, must be derived from a supported primitive type.</span></span>|
|`minExclusive`|<span data-ttu-id="b4821-333">已忽略。</span><span class="sxs-lookup"><span data-stu-id="b4821-333">Ignored.</span></span>|
|`minInclusive`|<span data-ttu-id="b4821-334">已忽略。</span><span class="sxs-lookup"><span data-stu-id="b4821-334">Ignored.</span></span>|
|`maxExclusive`|<span data-ttu-id="b4821-335">已忽略。</span><span class="sxs-lookup"><span data-stu-id="b4821-335">Ignored.</span></span>|
|`maxInclusive`|<span data-ttu-id="b4821-336">已忽略。</span><span class="sxs-lookup"><span data-stu-id="b4821-336">Ignored.</span></span>|
|`totalDigits`|<span data-ttu-id="b4821-337">已忽略。</span><span class="sxs-lookup"><span data-stu-id="b4821-337">Ignored.</span></span>|
|`fractionDigits`|<span data-ttu-id="b4821-338">已忽略。</span><span class="sxs-lookup"><span data-stu-id="b4821-338">Ignored.</span></span>|
|`length`|<span data-ttu-id="b4821-339">已忽略。</span><span class="sxs-lookup"><span data-stu-id="b4821-339">Ignored.</span></span>|
|`minLength`|<span data-ttu-id="b4821-340">已忽略。</span><span class="sxs-lookup"><span data-stu-id="b4821-340">Ignored.</span></span>|
|`maxLength`|<span data-ttu-id="b4821-341">已忽略。</span><span class="sxs-lookup"><span data-stu-id="b4821-341">Ignored.</span></span>|
|`enumeration`|<span data-ttu-id="b4821-342">已忽略。</span><span class="sxs-lookup"><span data-stu-id="b4821-342">Ignored.</span></span>|
|`whiteSpace`|<span data-ttu-id="b4821-343">已忽略。</span><span class="sxs-lookup"><span data-stu-id="b4821-343">Ignored.</span></span>|
|`pattern`|<span data-ttu-id="b4821-344">已忽略。</span><span class="sxs-lookup"><span data-stu-id="b4821-344">Ignored.</span></span>|
|<span data-ttu-id="b4821-345">(空白)</span><span class="sxs-lookup"><span data-stu-id="b4821-345">(blank)</span></span>|<span data-ttu-id="b4821-346">支持。</span><span class="sxs-lookup"><span data-stu-id="b4821-346">Supported.</span></span>|

## <a name="enumeration"></a><span data-ttu-id="b4821-347">枚举</span><span class="sxs-lookup"><span data-stu-id="b4821-347">Enumeration</span></span>

### <a name="xsrestriction-for-enumerations-attributes"></a><span data-ttu-id="b4821-348">\<xs:restriction> 对于枚举：特性</span><span class="sxs-lookup"><span data-stu-id="b4821-348">\<xs:restriction> for enumerations: attributes</span></span>

|<span data-ttu-id="b4821-349">Attribute</span><span class="sxs-lookup"><span data-stu-id="b4821-349">Attribute</span></span>|<span data-ttu-id="b4821-350">架构</span><span class="sxs-lookup"><span data-stu-id="b4821-350">Schema</span></span>|
|---------------|------------|
|`base`|<span data-ttu-id="b4821-351">如果存在，必须是 `xs:string`。</span><span class="sxs-lookup"><span data-stu-id="b4821-351">If present, must be `xs:string`.</span></span>|
|`id`|<span data-ttu-id="b4821-352">已忽略。</span><span class="sxs-lookup"><span data-stu-id="b4821-352">Ignored.</span></span>|

### <a name="xsrestriction-for-enumerations-contents"></a><span data-ttu-id="b4821-353">\<xs:restriction> 对于枚举：内容</span><span class="sxs-lookup"><span data-stu-id="b4821-353">\<xs:restriction> for enumerations: contents</span></span>

|<span data-ttu-id="b4821-354">目录</span><span class="sxs-lookup"><span data-stu-id="b4821-354">Contents</span></span>|<span data-ttu-id="b4821-355">架构</span><span class="sxs-lookup"><span data-stu-id="b4821-355">Schema</span></span>|
|--------------|------------|
|`simpleType`|<span data-ttu-id="b4821-356">如果存在，必须是数据协定支持的枚举限制（本节）。</span><span class="sxs-lookup"><span data-stu-id="b4821-356">If present, must be an enumeration restriction supported by the data contract (this section).</span></span>|
|`minExclusive`|<span data-ttu-id="b4821-357">已忽略。</span><span class="sxs-lookup"><span data-stu-id="b4821-357">Ignored.</span></span>|
|`minInclusive`|<span data-ttu-id="b4821-358">已忽略。</span><span class="sxs-lookup"><span data-stu-id="b4821-358">Ignored.</span></span>|
|`maxExclusive`|<span data-ttu-id="b4821-359">已忽略。</span><span class="sxs-lookup"><span data-stu-id="b4821-359">Ignored.</span></span>|
|`maxInclusive`|<span data-ttu-id="b4821-360">已忽略。</span><span class="sxs-lookup"><span data-stu-id="b4821-360">Ignored.</span></span>|
|`totalDigits`|<span data-ttu-id="b4821-361">已忽略。</span><span class="sxs-lookup"><span data-stu-id="b4821-361">Ignored.</span></span>|
|`fractionDigits`|<span data-ttu-id="b4821-362">已忽略。</span><span class="sxs-lookup"><span data-stu-id="b4821-362">Ignored.</span></span>|
|`length`|<span data-ttu-id="b4821-363">已禁止。</span><span class="sxs-lookup"><span data-stu-id="b4821-363">Forbidden.</span></span>|
|`minLength`|<span data-ttu-id="b4821-364">已禁止。</span><span class="sxs-lookup"><span data-stu-id="b4821-364">Forbidden.</span></span>|
|`maxLength`|<span data-ttu-id="b4821-365">已禁止。</span><span class="sxs-lookup"><span data-stu-id="b4821-365">Forbidden.</span></span>|
|`enumeration`|<span data-ttu-id="b4821-366">支持。</span><span class="sxs-lookup"><span data-stu-id="b4821-366">Supported.</span></span> <span data-ttu-id="b4821-367">忽略枚举“id”，并且“值”映射到枚举数据协定上的值名称。</span><span class="sxs-lookup"><span data-stu-id="b4821-367">Enumeration "id" is ignored, and "value" maps to the value name in the enumeration data contract.</span></span>|
|`whiteSpace`|<span data-ttu-id="b4821-368">已禁止。</span><span class="sxs-lookup"><span data-stu-id="b4821-368">Forbidden.</span></span>|
|`pattern`|<span data-ttu-id="b4821-369">已禁止。</span><span class="sxs-lookup"><span data-stu-id="b4821-369">Forbidden.</span></span>|
|<span data-ttu-id="b4821-370">(empty)</span><span class="sxs-lookup"><span data-stu-id="b4821-370">(empty)</span></span>|<span data-ttu-id="b4821-371">支持，映射到空枚举类型。</span><span class="sxs-lookup"><span data-stu-id="b4821-371">Supported, maps to empty enumeration type.</span></span>|

 <span data-ttu-id="b4821-372">下面的代码演示 C# 枚举类。</span><span class="sxs-lookup"><span data-stu-id="b4821-372">The following code shows a C# enumeration class.</span></span>

```csharp
public enum MyEnum
{
  first = 3,
  second = 4,
  third =5
}
```

<span data-ttu-id="b4821-373">此类通过 `DataContractSerializer`映射到下面的架构。</span><span class="sxs-lookup"><span data-stu-id="b4821-373">This class maps to the following schema by the `DataContractSerializer`.</span></span> <span data-ttu-id="b4821-374">如果枚举值从 1 开始，则不生成 `xs:annotation` 块。</span><span class="sxs-lookup"><span data-stu-id="b4821-374">If enumeration values start from 1, `xs:annotation` blocks are not generated.</span></span>

```xml
<xs:simpleType name="MyEnum">
  <xs:restriction base="xs:string">
    <xs:enumeration value="first">
      <xs:annotation>
        <xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">
          3
          </EnumerationValue>
        </xs:appinfo>
      </xs:annotation>
    </xs:enumeration>
    <xs:enumeration value="second">
      <xs:annotation>
        <xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">
          4
          </EnumerationValue>
        </xs:appinfo>
      </xs:annotation>
    </xs:enumeration>
  </xs:restriction>
</xs:simpleType>
```

### \<xs:list>

<span data-ttu-id="b4821-375">`DataContractSerializer` 将用 `System.FlagsAttribute` 标记的枚举类型映射到从 `xs:list` 派生的 `xs:string`。</span><span class="sxs-lookup"><span data-stu-id="b4821-375">`DataContractSerializer` maps enumeration types marked with `System.FlagsAttribute` to `xs:list` derived from `xs:string`.</span></span> <span data-ttu-id="b4821-376">不支持其他 `xs:list` 变体。</span><span class="sxs-lookup"><span data-stu-id="b4821-376">No other `xs:list` variations are supported.</span></span>

### <a name="xslist-attributes"></a><span data-ttu-id="b4821-377">\<xs:list>：特性</span><span class="sxs-lookup"><span data-stu-id="b4821-377">\<xs:list>: attributes</span></span>

|<span data-ttu-id="b4821-378">Attribute</span><span class="sxs-lookup"><span data-stu-id="b4821-378">Attribute</span></span>|<span data-ttu-id="b4821-379">架构</span><span class="sxs-lookup"><span data-stu-id="b4821-379">Schema</span></span>|
|---------------|------------|
|`itemType`|<span data-ttu-id="b4821-380">已禁止。</span><span class="sxs-lookup"><span data-stu-id="b4821-380">Forbidden.</span></span>|
|`id`|<span data-ttu-id="b4821-381">已忽略。</span><span class="sxs-lookup"><span data-stu-id="b4821-381">Ignored.</span></span>|

### <a name="xslist-contents"></a><span data-ttu-id="b4821-382">\<xs:list>：内容</span><span class="sxs-lookup"><span data-stu-id="b4821-382">\<xs:list>: contents</span></span>

|<span data-ttu-id="b4821-383">目录</span><span class="sxs-lookup"><span data-stu-id="b4821-383">Contents</span></span>|<span data-ttu-id="b4821-384">架构</span><span class="sxs-lookup"><span data-stu-id="b4821-384">Schema</span></span>|
|--------------|------------|
|`simpleType`|<span data-ttu-id="b4821-385">必须是来自使用 `xs:string` 方面的 `xs:enumeration` 的限制。</span><span class="sxs-lookup"><span data-stu-id="b4821-385">Must be restriction from `xs:string` using `xs:enumeration` facet.</span></span>|

<span data-ttu-id="b4821-386">如果枚举值后面没有 2 的幂级数（标志的默认值），则在 `xs:annotation/xs:appInfo/ser:EnumerationValue` 元素中存储值。</span><span class="sxs-lookup"><span data-stu-id="b4821-386">If enumeration value does not follow a power of 2 progression (default for Flags), the value is stored in the `xs:annotation/xs:appInfo/ser:EnumerationValue` element.</span></span>

<span data-ttu-id="b4821-387">例如，下面的代码标志一个枚举类型。</span><span class="sxs-lookup"><span data-stu-id="b4821-387">For example, the following code flags an enumeration type.</span></span>

```csharp
[Flags]
public enum AuthFlags
{
  AuthAnonymous = 1,
  AuthBasic = 2,
  AuthNTLM = 4,
  AuthMD5 = 16,
  AuthWindowsLiveID = 64,
}
```

<span data-ttu-id="b4821-388">此类型映射到下面的架构。</span><span class="sxs-lookup"><span data-stu-id="b4821-388">This type maps to the following schema.</span></span>

```xml
<xs:simpleType name="AuthFlags">
    <xs:list>
      <xs:simpleType>
        <xs:restriction base="xs:string">
          <xs:enumeration value="AuthAnonymous" />
          <xs:enumeration value="AuthBasic" />
          <xs:enumeration value="AuthNTLM" />
          <xs:enumeration value="AuthMD5">
            <xs:annotation>
              <xs:appinfo>
                <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">16</EnumerationValue>
              </xs:appinfo>
            </xs:annotation>
          </xs:enumeration>
          <xs:enumeration value="AuthWindowsLiveID">
            <xs:annotation>
              <xs:appinfo>
                <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">64</EnumerationValue>
              </xs:appinfo>
            </xs:annotation>
          </xs:enumeration>
        </xs:restriction>
      </xs:simpleType>
    </xs:list>
  </xs:simpleType>
```

## <a name="inheritance"></a><span data-ttu-id="b4821-389">继承</span><span class="sxs-lookup"><span data-stu-id="b4821-389">Inheritance</span></span>

### <a name="general-rules"></a><span data-ttu-id="b4821-390">一般规则</span><span class="sxs-lookup"><span data-stu-id="b4821-390">General rules</span></span>

<span data-ttu-id="b4821-391">数据协定可以继承自另一个数据协定。</span><span class="sxs-lookup"><span data-stu-id="b4821-391">A data contract can inherit from another data contract.</span></span> <span data-ttu-id="b4821-392">这类数据协定映射到一个基协定，并由扩展类型使用 `<xs:extension>` XML 架构协定进行派生。</span><span class="sxs-lookup"><span data-stu-id="b4821-392">Such data contracts map to a base and are derived by extension types using the `<xs:extension>` XML Schema construct.</span></span>

<span data-ttu-id="b4821-393">数据协定不能继承自集合数据协定。</span><span class="sxs-lookup"><span data-stu-id="b4821-393">A data contract cannot inherit from a collection data contract.</span></span>

<span data-ttu-id="b4821-394">例如，下面的代码是数据协定。</span><span class="sxs-lookup"><span data-stu-id="b4821-394">For example, the following code is a data contract.</span></span>

```csharp
[DataContract]
public class Person
{
  [DataMember]
  public string Name;
}
[DataContract]
public class Employee : Person
{
  [DataMember]
  public int ID;
}
```

<span data-ttu-id="b4821-395">此数据协定映射到下面的 XML 架构类型声明。</span><span class="sxs-lookup"><span data-stu-id="b4821-395">This data contract maps to the following XML Schema type declaration.</span></span>

```xml
<xs:complexType name="Employee">
 <xs:complexContent mixed="false">
  <xs:extension base="tns:Person">
   <xs:sequence>
    <xs:element minOccurs="0" name="ID" type="xs:int"/>
   </xs:sequence>
  </xs:extension>
 </xs:complexContent>
</xs:complexType>
<xs:complexType name="Person">
 <xs:sequence>
  <xs:element minOccurs="0" name="Name"
    nillable="true" type="xs:string"/>
 </xs:sequence>
</xs:complexType>
```

### <a name="xscomplexcontent-attributes"></a><span data-ttu-id="b4821-396">\<xs:complexContent>：特性</span><span class="sxs-lookup"><span data-stu-id="b4821-396">\<xs:complexContent>: attributes</span></span>

|<span data-ttu-id="b4821-397">Attribute</span><span class="sxs-lookup"><span data-stu-id="b4821-397">Attribute</span></span>|<span data-ttu-id="b4821-398">架构</span><span class="sxs-lookup"><span data-stu-id="b4821-398">Schema</span></span>|
|---------------|------------|
|`id`|<span data-ttu-id="b4821-399">已忽略。</span><span class="sxs-lookup"><span data-stu-id="b4821-399">Ignored.</span></span>|
|`mixed`|<span data-ttu-id="b4821-400">必须是 false。</span><span class="sxs-lookup"><span data-stu-id="b4821-400">Must be false.</span></span>|

### <a name="xscomplexcontent-contents"></a><span data-ttu-id="b4821-401">\<xs:complexContent>：内容</span><span class="sxs-lookup"><span data-stu-id="b4821-401">\<xs:complexContent>: contents</span></span>

|<span data-ttu-id="b4821-402">目录</span><span class="sxs-lookup"><span data-stu-id="b4821-402">Contents</span></span>|<span data-ttu-id="b4821-403">架构</span><span class="sxs-lookup"><span data-stu-id="b4821-403">Schema</span></span>|
|--------------|------------|
|`restriction`|<span data-ttu-id="b4821-404">已禁止，除了 base="`xs:anyType`"。</span><span class="sxs-lookup"><span data-stu-id="b4821-404">Forbidden, except when base="`xs:anyType`".</span></span> <span data-ttu-id="b4821-405">后者等效于将 `xs:restriction` 的内容直接放到 `xs:complexContent`的容器下。</span><span class="sxs-lookup"><span data-stu-id="b4821-405">The latter is equivalent to placing the content of the `xs:restriction` directly under the container of the `xs:complexContent`.</span></span>|
|`extension`|<span data-ttu-id="b4821-406">支持。</span><span class="sxs-lookup"><span data-stu-id="b4821-406">Supported.</span></span> <span data-ttu-id="b4821-407">映射到数据协定继承。</span><span class="sxs-lookup"><span data-stu-id="b4821-407">Maps to data contract inheritance.</span></span>|

### <a name="xsextension-in-xscomplexcontent-attributes"></a><span data-ttu-id="b4821-408">\<xs:extension> in \<xs:complexContent> ：特性</span><span class="sxs-lookup"><span data-stu-id="b4821-408">\<xs:extension> in \<xs:complexContent>: attributes</span></span>

|<span data-ttu-id="b4821-409">Attribute</span><span class="sxs-lookup"><span data-stu-id="b4821-409">Attribute</span></span>|<span data-ttu-id="b4821-410">架构</span><span class="sxs-lookup"><span data-stu-id="b4821-410">Schema</span></span>|
|---------------|------------|
|`id`|<span data-ttu-id="b4821-411">已忽略。</span><span class="sxs-lookup"><span data-stu-id="b4821-411">Ignored.</span></span>|
|`base`|<span data-ttu-id="b4821-412">支持。</span><span class="sxs-lookup"><span data-stu-id="b4821-412">Supported.</span></span> <span data-ttu-id="b4821-413">映射到此类型继承自的基数据协定类型。</span><span class="sxs-lookup"><span data-stu-id="b4821-413">Maps to the base data contract type that this type inherits from.</span></span>|

### <a name="xsextension-in-xscomplexcontent-contents"></a><span data-ttu-id="b4821-414">\<xs:extension> 在中 \<xs:complexContent> ：内容</span><span class="sxs-lookup"><span data-stu-id="b4821-414">\<xs:extension> in \<xs:complexContent>: contents</span></span>

<span data-ttu-id="b4821-415">规则与 `<xs:complexType>` 内容的规则相同。</span><span class="sxs-lookup"><span data-stu-id="b4821-415">The rules are the same as for `<xs:complexType>` contents.</span></span>

<span data-ttu-id="b4821-416">如果提供 `<xs:sequence>` ，则其成员元素将映射到存在于派生的数据协定中的附加数据成员。</span><span class="sxs-lookup"><span data-stu-id="b4821-416">If an `<xs:sequence>` is provided, its member elements map to additional data members that are present in the derived data contract.</span></span>

<span data-ttu-id="b4821-417">如果派生的类型包含与基类型中的元素有相同名称的元素，则重复元素声明映射到一个具有生成的唯一名称的数据成员。</span><span class="sxs-lookup"><span data-stu-id="b4821-417">If a derived type contains an element with the same name as an element in a base type, the duplicate element declaration maps to a data member with a name that is generated to be unique.</span></span> <span data-ttu-id="b4821-418">将向数据成员名称添加正整数数字（“member1”、“member2”等）直至查找到唯一的名称。</span><span class="sxs-lookup"><span data-stu-id="b4821-418">Positive integer numbers are added to the data member name ("member1", "member2", and so on) until a unique name is found.</span></span> <span data-ttu-id="b4821-419">相反：</span><span class="sxs-lookup"><span data-stu-id="b4821-419">Conversely:</span></span>

- <span data-ttu-id="b4821-420">如果派生的数据协定有一个数据成员与基数据协定中的数据成员具有相同的名称和类型，则 `DataContractSerializer` 在派生的类型中生成此对应的元素。</span><span class="sxs-lookup"><span data-stu-id="b4821-420">If a derived data contract has a data member with the same name and type as a data member in a base data contract, `DataContractSerializer` generates this corresponding element in the derived type.</span></span>

- <span data-ttu-id="b4821-421">如果派生的数据协定有一个数据成员与基数据协定中的数据成员具有相同的名称，但类型不同，则 `DataContractSerializer` 使用基类型和派生的类型声明中的 `xs:anyType` 类型的元素导入架构。</span><span class="sxs-lookup"><span data-stu-id="b4821-421">If a derived data contract has a data member with the same name as a data member in a base data contract but a different type, the `DataContractSerializer` imports a schema with an element of the type `xs:anyType` in both base type and derived type declarations.</span></span> <span data-ttu-id="b4821-422">在 `xs:annotations/xs:appInfo/ser:ActualType/@Name`中保留原始类型名称。</span><span class="sxs-lookup"><span data-stu-id="b4821-422">The original type name is preserved in `xs:annotations/xs:appInfo/ser:ActualType/@Name`.</span></span>

<span data-ttu-id="b4821-423">两个变体可能会导致一个使用有歧义的内容模型的架构，此内容模型取决于各自数据成员的顺序。</span><span class="sxs-lookup"><span data-stu-id="b4821-423">Both variations may lead to a schema with an ambiguous content model, which depends on the order of the respective data members.</span></span>

## <a name="typeprimitive-mapping"></a><span data-ttu-id="b4821-424">类型/基元映射</span><span class="sxs-lookup"><span data-stu-id="b4821-424">Type/primitive mapping</span></span>

<span data-ttu-id="b4821-425">`DataContractSerializer` 使用下面的 XML 架构基元类型映射。</span><span class="sxs-lookup"><span data-stu-id="b4821-425">The `DataContractSerializer` uses the following mapping for XML Schema primitive types.</span></span>

|<span data-ttu-id="b4821-426">XSD 类型</span><span class="sxs-lookup"><span data-stu-id="b4821-426">XSD type</span></span>|<span data-ttu-id="b4821-427">.NET 类型</span><span class="sxs-lookup"><span data-stu-id="b4821-427">.NET type</span></span>|
|--------------|---------------|
|`anyType`|<span data-ttu-id="b4821-428"><xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="b4821-428"><xref:System.Object>.</span></span>|
|`anySimpleType`|<span data-ttu-id="b4821-429"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b4821-429"><xref:System.String>.</span></span>|
|`duration`|<span data-ttu-id="b4821-430"><xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="b4821-430"><xref:System.TimeSpan>.</span></span>|
|`dateTime`|<span data-ttu-id="b4821-431"><xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="b4821-431"><xref:System.DateTime>.</span></span>|
|`dateTimeOffset`|<span data-ttu-id="b4821-432">表示偏移量的<xref:System.DateTime> 和 <xref:System.TimeSpan> 。</span><span class="sxs-lookup"><span data-stu-id="b4821-432"><xref:System.DateTime> and <xref:System.TimeSpan> for the offset.</span></span> <span data-ttu-id="b4821-433">请参见下面的“DateTimeOffset 序列化”。</span><span class="sxs-lookup"><span data-stu-id="b4821-433">See DateTimeOffset Serialization below.</span></span>|
|`time`|<span data-ttu-id="b4821-434"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b4821-434"><xref:System.String>.</span></span>|
|`date`|<span data-ttu-id="b4821-435"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b4821-435"><xref:System.String>.</span></span>|
|`gYearMonth`|<span data-ttu-id="b4821-436"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b4821-436"><xref:System.String>.</span></span>|
|`gYear`|<span data-ttu-id="b4821-437"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b4821-437"><xref:System.String>.</span></span>|
|`gMonthDay`|<span data-ttu-id="b4821-438"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b4821-438"><xref:System.String>.</span></span>|
|`gDay`|<span data-ttu-id="b4821-439"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b4821-439"><xref:System.String>.</span></span>|
|`gMonth`|<span data-ttu-id="b4821-440"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b4821-440"><xref:System.String>.</span></span>|
|`boolean`|<xref:System.Boolean>|
|`base64Binary`|<span data-ttu-id="b4821-441"><xref:System.Byte> 数组。</span><span class="sxs-lookup"><span data-stu-id="b4821-441"><xref:System.Byte> array.</span></span>|
|`hexBinary`|<span data-ttu-id="b4821-442"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b4821-442"><xref:System.String>.</span></span>|
|`float`|<span data-ttu-id="b4821-443"><xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="b4821-443"><xref:System.Single>.</span></span>|
|`double`|<span data-ttu-id="b4821-444"><xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="b4821-444"><xref:System.Double>.</span></span>|
|`anyURI`|<span data-ttu-id="b4821-445"><xref:System.Uri>.</span><span class="sxs-lookup"><span data-stu-id="b4821-445"><xref:System.Uri>.</span></span>|
|`QName`|<span data-ttu-id="b4821-446"><xref:System.Xml.XmlQualifiedName>.</span><span class="sxs-lookup"><span data-stu-id="b4821-446"><xref:System.Xml.XmlQualifiedName>.</span></span>|
|`string`|<span data-ttu-id="b4821-447"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b4821-447"><xref:System.String>.</span></span>|
|`normalizedString`|<span data-ttu-id="b4821-448"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b4821-448"><xref:System.String>.</span></span>|
|`token`|<span data-ttu-id="b4821-449"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b4821-449"><xref:System.String>.</span></span>|
|`language`|<span data-ttu-id="b4821-450"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b4821-450"><xref:System.String>.</span></span>|
|`Name`|<span data-ttu-id="b4821-451"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b4821-451"><xref:System.String>.</span></span>|
|`NCName`|<span data-ttu-id="b4821-452"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b4821-452"><xref:System.String>.</span></span>|
|`ID`|<span data-ttu-id="b4821-453"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b4821-453"><xref:System.String>.</span></span>|
|`IDREF`|<span data-ttu-id="b4821-454"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b4821-454"><xref:System.String>.</span></span>|
|`IDREFS`|<span data-ttu-id="b4821-455"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b4821-455"><xref:System.String>.</span></span>|
|`ENTITY`|<span data-ttu-id="b4821-456"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b4821-456"><xref:System.String>.</span></span>|
|`ENTITIES`|<span data-ttu-id="b4821-457"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b4821-457"><xref:System.String>.</span></span>|
|`NMTOKEN`|<span data-ttu-id="b4821-458"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b4821-458"><xref:System.String>.</span></span>|
|`NMTOKENS`|<span data-ttu-id="b4821-459"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b4821-459"><xref:System.String>.</span></span>|
|`decimal`|<span data-ttu-id="b4821-460"><xref:System.Decimal>.</span><span class="sxs-lookup"><span data-stu-id="b4821-460"><xref:System.Decimal>.</span></span>|
|`integer`|<span data-ttu-id="b4821-461"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="b4821-461"><xref:System.Int64>.</span></span>|
|`nonPositiveInteger`|<span data-ttu-id="b4821-462"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="b4821-462"><xref:System.Int64>.</span></span>|
|`negativeInteger`|<span data-ttu-id="b4821-463"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="b4821-463"><xref:System.Int64>.</span></span>|
|`long`|<span data-ttu-id="b4821-464"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="b4821-464"><xref:System.Int64>.</span></span>|
|`int`|<span data-ttu-id="b4821-465"><xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="b4821-465"><xref:System.Int32>.</span></span>|
|`short`|<span data-ttu-id="b4821-466"><xref:System.Int16>.</span><span class="sxs-lookup"><span data-stu-id="b4821-466"><xref:System.Int16>.</span></span>|
|`Byte`|<span data-ttu-id="b4821-467"><xref:System.SByte>.</span><span class="sxs-lookup"><span data-stu-id="b4821-467"><xref:System.SByte>.</span></span>|
|`nonNegativeInteger`|<span data-ttu-id="b4821-468"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="b4821-468"><xref:System.Int64>.</span></span>|
|`unsignedLong`|<span data-ttu-id="b4821-469"><xref:System.UInt64>.</span><span class="sxs-lookup"><span data-stu-id="b4821-469"><xref:System.UInt64>.</span></span>|
|`unsignedInt`|<span data-ttu-id="b4821-470"><xref:System.UInt32>.</span><span class="sxs-lookup"><span data-stu-id="b4821-470"><xref:System.UInt32>.</span></span>|
|`unsignedShort`|<span data-ttu-id="b4821-471"><xref:System.UInt16>.</span><span class="sxs-lookup"><span data-stu-id="b4821-471"><xref:System.UInt16>.</span></span>|
|`unsignedByte`|<span data-ttu-id="b4821-472"><xref:System.Byte>.</span><span class="sxs-lookup"><span data-stu-id="b4821-472"><xref:System.Byte>.</span></span>|
|`positiveInteger`|<span data-ttu-id="b4821-473"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="b4821-473"><xref:System.Int64>.</span></span>|

## <a name="iserializable-types-mapping"></a><span data-ttu-id="b4821-474">ISerializable 类型映射</span><span class="sxs-lookup"><span data-stu-id="b4821-474">ISerializable types mapping</span></span>

<span data-ttu-id="b4821-475">在 .NET Framework 版本1.0 中， <xref:System.Runtime.Serialization.ISerializable> 是作为一种用于序列化对象以实现持久性或数据传输的常规机制。</span><span class="sxs-lookup"><span data-stu-id="b4821-475">In .NET Framework version 1.0, <xref:System.Runtime.Serialization.ISerializable> was introduced as a general mechanism to serialize objects for persistence or data transfer.</span></span> <span data-ttu-id="b4821-476">可以实现许多 .NET Framework 类型，这些类型 `ISerializable` 可以在应用程序之间传递。</span><span class="sxs-lookup"><span data-stu-id="b4821-476">There are many .NET Framework types that implement `ISerializable` and that can be passed between applications.</span></span> <span data-ttu-id="b4821-477"><xref:System.Runtime.Serialization.DataContractSerializer> 自然支持 `ISerializable` 类。</span><span class="sxs-lookup"><span data-stu-id="b4821-477"><xref:System.Runtime.Serialization.DataContractSerializer> naturally provides support for `ISerializable` classes.</span></span> <span data-ttu-id="b4821-478">`DataContractSerializer` 映射到 `ISerializable` 实现架构类型，这些类型仅在类型的 QName（限定名）上存在不同，并且实际上是属性集合。</span><span class="sxs-lookup"><span data-stu-id="b4821-478">The `DataContractSerializer` maps `ISerializable` implementation schema types that differ only by the QName (qualified name) of the type and are effectively property collections.</span></span> <span data-ttu-id="b4821-479">例如， `DataContractSerializer` 映射 <xref:System.Exception> 到命名空间中的以下 XSD 类型 `http://schemas.datacontract.org/2004/07/System` 。</span><span class="sxs-lookup"><span data-stu-id="b4821-479">For example, the `DataContractSerializer` maps <xref:System.Exception> to the following XSD type in the `http://schemas.datacontract.org/2004/07/System` namespace.</span></span>

```xml
<xs:complexType name="Exception">
 <xs:sequence>
  <xs:any minOccurs="0" maxOccurs="unbounded"
      namespace="##local" processContents="skip"/>
 </xs:sequence>
 <xs:attribute ref="ser:FactoryType"/>
</xs:complexType>
```

<span data-ttu-id="b4821-480">数据协定序列化架构中声明的可选属性 `ser:FactoryType` 引用可以反序列化类型的工厂类。</span><span class="sxs-lookup"><span data-stu-id="b4821-480">The optional attribute `ser:FactoryType` declared in the Data Contract Serialization schema references a factory class that can deserialize the type.</span></span> <span data-ttu-id="b4821-481">工厂类必须是正在使用的 `DataContractSerializer` 实例的已知类型集合的一部分。</span><span class="sxs-lookup"><span data-stu-id="b4821-481">The factory class must be part of the known types collection of the `DataContractSerializer` instance being used.</span></span> <span data-ttu-id="b4821-482">有关已知类型的详细信息，请参阅 [数据协定已知类型](data-contract-known-types.md)。</span><span class="sxs-lookup"><span data-stu-id="b4821-482">For more information about known types, see [Data Contract Known Types](data-contract-known-types.md).</span></span>

## <a name="datacontract-serialization-schema"></a><span data-ttu-id="b4821-483">DataContract 序列化架构</span><span class="sxs-lookup"><span data-stu-id="b4821-483">DataContract Serialization Schema</span></span>

<span data-ttu-id="b4821-484">许多由 `DataContractSerializer` 导出的架构都使用一个特殊数据协定序列化命名空间中的类型、元素和属性：</span><span class="sxs-lookup"><span data-stu-id="b4821-484">A number of schemas exported by the `DataContractSerializer` use types, elements, and attributes from a special Data Contract Serialization namespace:</span></span>

`http://schemas.microsoft.com/2003/10/Serialization`

<span data-ttu-id="b4821-485">下面是一个完整的数据协定序列化架构声明。</span><span class="sxs-lookup"><span data-stu-id="b4821-485">The following is a complete Data Contract Serialization schema declaration.</span></span>

```xml
<xs:schema attributeFormDefault="qualified"
   elementFormDefault="qualified"
   targetNamespace =
    "http://schemas.microsoft.com/2003/10/Serialization/"
   xmlns:xs="http://www.w3.org/2001/XMLSchema"
   xmlns:tns="http://schemas.microsoft.com/2003/10/Serialization/">

 <!-- Top-level elements for primitive types. -->
 <xs:element name="anyType" nillable="true" type="xs:anyType"/>
 <xs:element name="anyURI" nillable="true" type="xs:anyURI"/>
 <xs:element name="base64Binary"
       nillable="true" type="xs:base64Binary"/>
 <xs:element name="boolean" nillable="true" type="xs:boolean"/>
 <xs:element name="byte" nillable="true" type="xs:byte"/>
 <xs:element name="dateTime" nillable="true" type="xs:dateTime"/>
 <xs:element name="decimal" nillable="true" type="xs:decimal"/>
 <xs:element name="double" nillable="true" type="xs:double"/>
 <xs:element name="float" nillable="true" type="xs:float"/>
 <xs:element name="int" nillable="true" type="xs:int"/>
 <xs:element name="long" nillable="true" type="xs:long"/>
 <xs:element name="QName" nillable="true" type="xs:QName"/>
 <xs:element name="short" nillable="true" type="xs:short"/>
 <xs:element name="string" nillable="true" type="xs:string"/>
 <xs:element name="unsignedByte"
       nillable="true" type="xs:unsignedByte"/>
 <xs:element name="unsignedInt"
       nillable="true" type="xs:unsignedInt"/>
 <xs:element name="unsignedLong"
       nillable="true" type="xs:unsignedLong"/>
 <xs:element name="unsignedShort"
       nillable="true" type="xs:unsignedShort"/>

 <!-- Primitive types introduced for certain .NET simple types. -->
 <xs:element name="char" nillable="true" type="tns:char"/>
 <xs:simpleType name="char">
  <xs:restriction base="xs:int"/>
 </xs:simpleType>

 <!-- xs:duration is restricted to an ordered value space,
    to map to System.TimeSpan -->
 <xs:element name="duration" nillable="true" type="tns:duration"/>
 <xs:simpleType name="duration">
  <xs:restriction base="xs:duration">
   <xs:pattern
     value="\-?P(\d*D)?(T(\d*H)?(\d*M)?(\d*(\.\d*)?S)?)?"/>
   <xs:minInclusive value="-P10675199DT2H48M5.4775808S"/>
   <xs:maxInclusive value="P10675199DT2H48M5.4775807S"/>
  </xs:restriction>
 </xs:simpleType>

 <xs:element name="guid" nillable="true" type="tns:guid"/>
 <xs:simpleType name="guid">
  <xs:restriction base="xs:string">
   <xs:pattern value="[\da-fA-F]{8}-[\da-fA-F]{4}-[\da-fA-F]{4}-[\da-fA-F]{4}-[\da-fA-F]{12}"/>
  </xs:restriction>
 </xs:simpleType>

 <!-- This is used for schemas exported from ISerializable type. -->
 <xs:attribute name="FactoryType" type="xs:QName"/>
</xs:schema>
```

<span data-ttu-id="b4821-486">应注意以下事项：</span><span class="sxs-lookup"><span data-stu-id="b4821-486">The following should be noted:</span></span>

- <span data-ttu-id="b4821-487">已引入`ser:char` 来表示 <xref:System.Char>类型的 Unicode 字符。</span><span class="sxs-lookup"><span data-stu-id="b4821-487">`ser:char` is introduced to represent Unicode characters of type <xref:System.Char>.</span></span>

- <span data-ttu-id="b4821-488">`valuespace` 的 `xs:duration` 已简化为一个有序集，因此可以将其映射到 <xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="b4821-488">The `valuespace` of `xs:duration` is reduced to an ordered set so that it can be mapped to a <xref:System.TimeSpan>.</span></span>

- <span data-ttu-id="b4821-489">在从派生自`FactoryType` 的类型中导出的架构中使用 <xref:System.Runtime.Serialization.ISerializable>。</span><span class="sxs-lookup"><span data-stu-id="b4821-489">`FactoryType` is used in schemas exported from types that are derived from <xref:System.Runtime.Serialization.ISerializable>.</span></span>

## <a name="importing-non-datacontract-schemas"></a><span data-ttu-id="b4821-490">导入非 DataContract 架构</span><span class="sxs-lookup"><span data-stu-id="b4821-490">Importing non-DataContract schemas</span></span>

<span data-ttu-id="b4821-491">`DataContractSerializer` 具有 `ImportXmlTypes` 选项，可允许导入不符合 `DataContractSerializer` XSD 配置文件的架构（请参见 <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> 属性）。</span><span class="sxs-lookup"><span data-stu-id="b4821-491">`DataContractSerializer` has the `ImportXmlTypes` option to allow import of schemas that do not conform to the `DataContractSerializer` XSD profile (see the <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> property).</span></span> <span data-ttu-id="b4821-492">将此选项设置为 `true` 可接受不符合要求的架构类型，并将其映射到下面的实现，即包装 <xref:System.Xml.Serialization.IXmlSerializable> 数组的 <xref:System.Xml.XmlNode> （仅类名称不同）。</span><span class="sxs-lookup"><span data-stu-id="b4821-492">Setting this option to `true` enables acceptance of non-conforming schema types and mapping them to the following implementation, <xref:System.Xml.Serialization.IXmlSerializable> wrapping an array of <xref:System.Xml.XmlNode> (only the class name differs).</span></span>

```csharp
[GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]
[System.Xml.Serialization.XmlSchemaProviderAttribute("ExportSchema")]
[System.Xml.Serialization.XmlRootAttribute(IsNullable=false)]
public partial class Person : object, IXmlSerializable
{
  private XmlNode[] nodesField;
  private static XmlQualifiedName typeName =
new XmlQualifiedName("Person","http://Microsoft.ServiceModel.Samples");
  public XmlNode[] Nodes
  {
    get {return this.nodesField;}
    set {this.nodesField = value;}
  }
  public void ReadXml(XmlReader reader)
  {
    this.nodesField = XmlSerializableServices.ReadNodes(reader);
  }
  public void WriteXml(XmlWriter writer)
  {
    XmlSerializableServices.WriteNodes(writer, this.Nodes);
  }
  public System.Xml.Schema.XmlSchema GetSchema()
  {
    return null;
  }
  public static XmlQualifiedName ExportSchema(XmlSchemaSet schemas)
  {
    XmlSerializableServices.AddDefaultSchema(schemas, typeName);
    return typeName;
  }
}
```

## <a name="datetimeoffset-serialization"></a><span data-ttu-id="b4821-493">DateTimeOffset 序列化</span><span class="sxs-lookup"><span data-stu-id="b4821-493">DateTimeOffset Serialization</span></span>

<span data-ttu-id="b4821-494">未将 <xref:System.DateTimeOffset> 视为基元类型，</span><span class="sxs-lookup"><span data-stu-id="b4821-494">The <xref:System.DateTimeOffset> is not treated as a primitive type.</span></span> <span data-ttu-id="b4821-495">而是将其序列化为具有两部分的复杂元素。</span><span class="sxs-lookup"><span data-stu-id="b4821-495">Instead, it is serialized as a complex element with two parts.</span></span> <span data-ttu-id="b4821-496">第一部分表示日期时间，第二部分表示日期时间的偏移量。</span><span class="sxs-lookup"><span data-stu-id="b4821-496">The first part represents the date time, and the second part represents the offset from the date time.</span></span> <span data-ttu-id="b4821-497">在下面的代码中演示已序列化的 DateTimeOffset 值的示例。</span><span class="sxs-lookup"><span data-stu-id="b4821-497">An example of a serialized DateTimeOffset value is shown in the following code.</span></span>

```xml
<OffSet xmlns:a="http://schemas.datacontract.org/2004/07/System">
  <DateTime i:type="b:dateTime" xmlns=""
    xmlns:b="http://www.w3.org/2001/XMLSchema">2008-08-28T08:00:00
  </DateTime>
  <OffsetMinutes i:type="b:short" xmlns=""
   xmlns:b="http://www.w3.org/2001/XMLSchema">-480
   </OffsetMinutes>
</OffSet>
```

<span data-ttu-id="b4821-498">相应的架构如下所示。</span><span class="sxs-lookup"><span data-stu-id="b4821-498">The schema is as follows.</span></span>

```xml
<xs:schema targetNamespace="http://schemas.datacontract.org/2004/07/System">
   <xs:complexType name="DateTimeOffset">
      <xs:sequence minOccurs="1" maxOccurs="1">
         <xs:element name="DateTime" type="xs:dateTime"
         minOccurs="1" maxOccurs="1" />
         <xs:element name="OffsetMinutes" type="xs:short"
         minOccurs="1" maxOccurs="1" />
      </xs:sequence>
   </xs:complexType>
</xs:schema>
```

## <a name="see-also"></a><span data-ttu-id="b4821-499">请参阅</span><span class="sxs-lookup"><span data-stu-id="b4821-499">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- [<span data-ttu-id="b4821-500">使用数据协定</span><span class="sxs-lookup"><span data-stu-id="b4821-500">Using Data Contracts</span></span>](using-data-contracts.md)
