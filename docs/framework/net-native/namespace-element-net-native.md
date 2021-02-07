---
description: '了解详细信息： <Namespace> 元素 ( .NET Native) '
title: <Namespace>元素 (.NET Native)
ms.date: 03/30/2017
ms.assetid: 57c614e5-18a9-4e87-bfd5-d0fe3396a192
ms.openlocfilehash: c24f78d8d9fd59258391e9dd5e59988675163b49
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738606"
---
# <a name="namespace-element-net-native"></a><span data-ttu-id="aa2df-103">\<Namespace>元素 (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="aa2df-103">\<Namespace> Element (.NET Native)</span></span>

<span data-ttu-id="aa2df-104">将运行时反射策略应用到一个指定的命名空间中的所有类型。</span><span class="sxs-lookup"><span data-stu-id="aa2df-104">Applies runtime reflection policy to all the types in a specified namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa2df-105">语法</span><span class="sxs-lookup"><span data-stu-id="aa2df-105">Syntax</span></span>  
  
```xml  
<Namespace Name="namespace_name"
           Activate="policy_type"
           Browse="policy_type"  
           Dynamic="policy_setting"  
           Serialize="policy_setting"  
           DataContractSerializer="policy_setting"  
           DataContractJsonSerializer="policy_setting"  
           XmlSerializer="policy_setting"  
           MarshalObject="policy_setting"  
           MarshalDelegate="policy_setting"  
           MarshalStructure="policy_setting" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aa2df-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="aa2df-106">Attributes and Elements</span></span>  

 <span data-ttu-id="aa2df-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="aa2df-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aa2df-108">特性</span><span class="sxs-lookup"><span data-stu-id="aa2df-108">Attributes</span></span>  
  
|<span data-ttu-id="aa2df-109">属性</span><span class="sxs-lookup"><span data-stu-id="aa2df-109">Attribute</span></span>|<span data-ttu-id="aa2df-110">属性类型</span><span class="sxs-lookup"><span data-stu-id="aa2df-110">Attribute type</span></span>|<span data-ttu-id="aa2df-111">说明</span><span class="sxs-lookup"><span data-stu-id="aa2df-111">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="aa2df-112">常规</span><span class="sxs-lookup"><span data-stu-id="aa2df-112">General</span></span>|<span data-ttu-id="aa2df-113">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="aa2df-113">Required attribute.</span></span> <span data-ttu-id="aa2df-114">指定命名空间的名称。</span><span class="sxs-lookup"><span data-stu-id="aa2df-114">Specifies the name of the namespace.</span></span>|  
|`Activate`|<span data-ttu-id="aa2df-115">反射</span><span class="sxs-lookup"><span data-stu-id="aa2df-115">Reflection</span></span>|<span data-ttu-id="aa2df-116">可选特性。</span><span class="sxs-lookup"><span data-stu-id="aa2df-116">Optional attribute.</span></span> <span data-ttu-id="aa2df-117">控制运行时对构造函数的访问，以启用实例激活。</span><span class="sxs-lookup"><span data-stu-id="aa2df-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="aa2df-118">反射</span><span class="sxs-lookup"><span data-stu-id="aa2df-118">Reflection</span></span>|<span data-ttu-id="aa2df-119">可选特性。</span><span class="sxs-lookup"><span data-stu-id="aa2df-119">Optional attribute.</span></span> <span data-ttu-id="aa2df-120">控制对有关程序元素信息的查询，但并不启用任何运行时访问。</span><span class="sxs-lookup"><span data-stu-id="aa2df-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="aa2df-121">反射</span><span class="sxs-lookup"><span data-stu-id="aa2df-121">Reflection</span></span>|<span data-ttu-id="aa2df-122">可选特性。</span><span class="sxs-lookup"><span data-stu-id="aa2df-122">Optional attribute.</span></span> <span data-ttu-id="aa2df-123">控制运行时对所有类型成员的访问，包括构造函数、方法、字段、属性和事件，以启用动态编程。</span><span class="sxs-lookup"><span data-stu-id="aa2df-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="aa2df-124">序列化</span><span class="sxs-lookup"><span data-stu-id="aa2df-124">Serialization</span></span>|<span data-ttu-id="aa2df-125">可选特性。</span><span class="sxs-lookup"><span data-stu-id="aa2df-125">Optional attribute.</span></span> <span data-ttu-id="aa2df-126">控制运行时对构造函数、字段和属性的访问，使类型实例得到序列化和反序列化处理，这是通过库进行的，例如 Newtonsoft JSON 序列化程序。</span><span class="sxs-lookup"><span data-stu-id="aa2df-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="aa2df-127">序列化</span><span class="sxs-lookup"><span data-stu-id="aa2df-127">Serialization</span></span>|<span data-ttu-id="aa2df-128">可选特性。</span><span class="sxs-lookup"><span data-stu-id="aa2df-128">Optional attribute.</span></span> <span data-ttu-id="aa2df-129">控制使用 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> 类的序列化策略。</span><span class="sxs-lookup"><span data-stu-id="aa2df-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="aa2df-130">序列化</span><span class="sxs-lookup"><span data-stu-id="aa2df-130">Serialization</span></span>|<span data-ttu-id="aa2df-131">可选特性。</span><span class="sxs-lookup"><span data-stu-id="aa2df-131">Optional attribute.</span></span> <span data-ttu-id="aa2df-132">控制使用 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> 类的 JSON 序列化策略。</span><span class="sxs-lookup"><span data-stu-id="aa2df-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="aa2df-133">序列化</span><span class="sxs-lookup"><span data-stu-id="aa2df-133">Serialization</span></span>|<span data-ttu-id="aa2df-134">可选特性。</span><span class="sxs-lookup"><span data-stu-id="aa2df-134">Optional attribute.</span></span> <span data-ttu-id="aa2df-135">控制使用 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> 类的 XML 序列化策略。</span><span class="sxs-lookup"><span data-stu-id="aa2df-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="aa2df-136">Interop</span><span class="sxs-lookup"><span data-stu-id="aa2df-136">Interop</span></span>|<span data-ttu-id="aa2df-137">可选特性。</span><span class="sxs-lookup"><span data-stu-id="aa2df-137">Optional attribute.</span></span> <span data-ttu-id="aa2df-138">控制封送引用类型到 Windows 运行时和 COM 的策略。</span><span class="sxs-lookup"><span data-stu-id="aa2df-138">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="aa2df-139">Interop</span><span class="sxs-lookup"><span data-stu-id="aa2df-139">Interop</span></span>|<span data-ttu-id="aa2df-140">可选特性。</span><span class="sxs-lookup"><span data-stu-id="aa2df-140">Optional attribute.</span></span> <span data-ttu-id="aa2df-141">控制将委托类型作为函数指针封送到本机代码的策略。</span><span class="sxs-lookup"><span data-stu-id="aa2df-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="aa2df-142">Interop</span><span class="sxs-lookup"><span data-stu-id="aa2df-142">Interop</span></span>|<span data-ttu-id="aa2df-143">可选特性。</span><span class="sxs-lookup"><span data-stu-id="aa2df-143">Optional attribute.</span></span> <span data-ttu-id="aa2df-144">控制封送结构到本机代码的策略。</span><span class="sxs-lookup"><span data-stu-id="aa2df-144">Controls policy for marshaling structures to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="aa2df-145">Name 特性</span><span class="sxs-lookup"><span data-stu-id="aa2df-145">Name attribute</span></span>  
  
|<span data-ttu-id="aa2df-146">值</span><span class="sxs-lookup"><span data-stu-id="aa2df-146">Value</span></span>|<span data-ttu-id="aa2df-147">说明</span><span class="sxs-lookup"><span data-stu-id="aa2df-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="aa2df-148">*namespace_name*</span><span class="sxs-lookup"><span data-stu-id="aa2df-148">*namespace_name*</span></span>|<span data-ttu-id="aa2df-149">命名空间名称。</span><span class="sxs-lookup"><span data-stu-id="aa2df-149">The namespace name.</span></span> <span data-ttu-id="aa2df-150">如果 \<Namespace> 元素是 [\<Application>](application-element-net-native.md) 、或元素的子元素 [\<Library>](library-element-net-native.md) ，则 [\<Assembly>](assembly-element-net-native.md) *namespace_name* 必须是完全限定的命名空间名称。</span><span class="sxs-lookup"><span data-stu-id="aa2df-150">If the \<Namespace> element is a child of an [\<Application>](application-element-net-native.md), [\<Library>](library-element-net-native.md), or [\<Assembly>](assembly-element-net-native.md) element, *namespace_name* must be a fully qualified namespace name.</span></span> <span data-ttu-id="aa2df-151">如果该 \<Namespace> 元素是另一个元素的子元素 \<Namespace> ，则 *namespace_name* 必须是相对的命名空间名称。</span><span class="sxs-lookup"><span data-stu-id="aa2df-151">If the \<Namespace> element is a child of another \<Namespace> element, *namespace_name* must be a relative namespace name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="aa2df-152">所有其他特性</span><span class="sxs-lookup"><span data-stu-id="aa2df-152">All other attributes</span></span>  
  
|<span data-ttu-id="aa2df-153">值</span><span class="sxs-lookup"><span data-stu-id="aa2df-153">Value</span></span>|<span data-ttu-id="aa2df-154">说明</span><span class="sxs-lookup"><span data-stu-id="aa2df-154">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="aa2df-155">*策略_设置*</span><span class="sxs-lookup"><span data-stu-id="aa2df-155">*policy_setting*</span></span>|<span data-ttu-id="aa2df-156">该设置将应用这个策略类型到该命名空间的所有类型。</span><span class="sxs-lookup"><span data-stu-id="aa2df-156">The setting to apply to this policy type for all types in the namespace.</span></span> <span data-ttu-id="aa2df-157">可能值为 `All`、`Auto`、`Excluded`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal` 以及 `Required All`。</span><span class="sxs-lookup"><span data-stu-id="aa2df-157">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="aa2df-158">有关详细信息，请参阅[运行时指令策略设置](runtime-directive-policy-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="aa2df-158">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aa2df-159">子元素</span><span class="sxs-lookup"><span data-stu-id="aa2df-159">Child Elements</span></span>  
  
|<span data-ttu-id="aa2df-160">元素</span><span class="sxs-lookup"><span data-stu-id="aa2df-160">Element</span></span>|<span data-ttu-id="aa2df-161">说明</span><span class="sxs-lookup"><span data-stu-id="aa2df-161">Description</span></span>|  
|-------------|-----------------|  
|`<Namespace>`|<span data-ttu-id="aa2df-162">将运行时反射策略应用到一个父命名空间中的所有类型。</span><span class="sxs-lookup"><span data-stu-id="aa2df-162">Applies runtime reflection policy to all types in a parent namespace.</span></span>|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="aa2df-163">将反射策略应用到一个类型。</span><span class="sxs-lookup"><span data-stu-id="aa2df-163">Applies reflection policy to a type.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="aa2df-164">将反射策略应用到一个构造泛型类型。</span><span class="sxs-lookup"><span data-stu-id="aa2df-164">Applies reflection policy to a constructed generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="aa2df-165">父元素</span><span class="sxs-lookup"><span data-stu-id="aa2df-165">Parent Elements</span></span>  
  
|<span data-ttu-id="aa2df-166">元素</span><span class="sxs-lookup"><span data-stu-id="aa2df-166">Element</span></span>|<span data-ttu-id="aa2df-167">说明</span><span class="sxs-lookup"><span data-stu-id="aa2df-167">Description</span></span>|  
|-------------|-----------------|  
|[\<Application>](application-element-net-native.md)|<span data-ttu-id="aa2df-168">作为应用程序范围内的类型和元数据可以反应在运行时间的类型成员的容器而服务。</span><span class="sxs-lookup"><span data-stu-id="aa2df-168">Serves as a container for application-wide types and type members whose metadata is available for reflection at run time.</span></span> <span data-ttu-id="aa2df-169">[\<Application>](application-element-net-native.md)元素可以包含零个、一个或多个 [\<Assembly>](assembly-element-net-native.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="aa2df-169">The [\<Application>](application-element-net-native.md) element can have zero, one, or more [\<Assembly>](assembly-element-net-native.md) elements.</span></span>|  
|[\<Assembly>](assembly-element-net-native.md)|<span data-ttu-id="aa2df-170">将运行时反射策略应用到指定程序集中的所有类型。</span><span class="sxs-lookup"><span data-stu-id="aa2df-170">Applies runtime reflection policy to all the types in a specified assembly.</span></span>|  
|[\<Library>](library-element-net-native.md)|<span data-ttu-id="aa2df-171">定义包含元数据在运行时间可以用于反射的类型和类型成员的程序集。</span><span class="sxs-lookup"><span data-stu-id="aa2df-171">Defines the assembly that contains types and type members whose metadata is available for reflection at run time.</span></span> <span data-ttu-id="aa2df-172">[\<Library>](library-element-net-native.md)元素可以有零个或一个 [\<Assembly>](assembly-element-net-native.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="aa2df-172">The [\<Library>](library-element-net-native.md) element can have zero or one [\<Assembly>](assembly-element-net-native.md) element.</span></span>|  
|`<Namespace>`|<span data-ttu-id="aa2df-173">将反射策略应用到一个父命名空间中的所有类型。</span><span class="sxs-lookup"><span data-stu-id="aa2df-173">Applies reflection policy to all types in a parent namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa2df-174">备注</span><span class="sxs-lookup"><span data-stu-id="aa2df-174">Remarks</span></span>  

 <span data-ttu-id="aa2df-175">`Activate`、`Browse`、`Dynamic` 和 `Serialize` 特性都是可选项。</span><span class="sxs-lookup"><span data-stu-id="aa2df-175">The `Activate`, `Browse`, `Dynamic`, and `Serialize` attributes are all optional.</span></span> <span data-ttu-id="aa2df-176">如果这些都不存在，`<Namespace>` 元素仅会充当子元素的容器。</span><span class="sxs-lookup"><span data-stu-id="aa2df-176">If none are present, the `<Namespace>` element serves only as a container for child elements.</span></span> <span data-ttu-id="aa2df-177">如果它们存在，`<Namespace>` 元素会将运行时反射策略应用到一个指定的命名空间中的所有类型。</span><span class="sxs-lookup"><span data-stu-id="aa2df-177">If they are present, the `<Namespace>` element applies runtime reflection policy to all the types in the specified namespace.</span></span>  
  
 <span data-ttu-id="aa2df-178">当它是元素的子元素时 [\<Assembly>](assembly-element-net-native.md) ， `<Namespace>` 元素将重写由元素定义的运行时反射策略  [\<Assembly>](assembly-element-net-native.md) 。</span><span class="sxs-lookup"><span data-stu-id="aa2df-178">When it is a child of the [\<Assembly>](assembly-element-net-native.md) element, the `<Namespace>` element overrides the runtime reflection policy defined by the  [\<Assembly>](assembly-element-net-native.md) element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa2df-179">请参阅</span><span class="sxs-lookup"><span data-stu-id="aa2df-179">See also</span></span>

- [<span data-ttu-id="aa2df-180">运行时指令策略设置</span><span class="sxs-lookup"><span data-stu-id="aa2df-180">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="aa2df-181">运行时指令 (rd.xml) 配置文件引用</span><span class="sxs-lookup"><span data-stu-id="aa2df-181">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="aa2df-182">运行时指令元素</span><span class="sxs-lookup"><span data-stu-id="aa2df-182">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
