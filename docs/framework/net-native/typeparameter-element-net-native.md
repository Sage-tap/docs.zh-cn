---
description: '了解详细信息： <TypeParameter> 元素 ( .NET Native) '
title: <TypeParameter>元素 (.NET Native)
ms.date: 03/30/2017
ms.assetid: d37bb1b7-1ddc-4c6d-8ecf-583f804a2479
ms.openlocfilehash: 182cd62dc0584991b8ef0f5757d6005173d6d7a7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803641"
---
# <a name="typeparameter-element-net-native"></a><span data-ttu-id="edc2e-103">\<TypeParameter>元素 (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="edc2e-103">\<TypeParameter> Element (.NET Native)</span></span>

<span data-ttu-id="edc2e-104">将策略应用到以传递到方法为代表的类型参数类型。</span><span class="sxs-lookup"><span data-stu-id="edc2e-104">Applies policy to the type represented by a Type argument passed to a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edc2e-105">语法</span><span class="sxs-lookup"><span data-stu-id="edc2e-105">Syntax</span></span>  
  
```xml  
<Parameter Name="parameter_name"  
           Activate="policy_type"  
           Browse="policy_type"  
           Dynamic="policy_type"  
           Serialize="policy_type"  
           DataContractSerializer="policy_type"  
           DataContractJsonSerializer="policy_type"  
           XmlSerializer="policy_type"  
           MarshalObject="policy_type"  
           MarshalDelegate="policy_type"  
           MarshalStructure="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="edc2e-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="edc2e-106">Attributes and Elements</span></span>  

 <span data-ttu-id="edc2e-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="edc2e-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="edc2e-108">特性</span><span class="sxs-lookup"><span data-stu-id="edc2e-108">Attributes</span></span>  
  
|<span data-ttu-id="edc2e-109">属性</span><span class="sxs-lookup"><span data-stu-id="edc2e-109">Attribute</span></span>|<span data-ttu-id="edc2e-110">属性类型</span><span class="sxs-lookup"><span data-stu-id="edc2e-110">Attribute type</span></span>|<span data-ttu-id="edc2e-111">说明</span><span class="sxs-lookup"><span data-stu-id="edc2e-111">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="edc2e-112">常规</span><span class="sxs-lookup"><span data-stu-id="edc2e-112">General</span></span>|<span data-ttu-id="edc2e-113">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="edc2e-113">Required attribute.</span></span> <span data-ttu-id="edc2e-114">类型 <xref:System.Type> 的参数名称。</span><span class="sxs-lookup"><span data-stu-id="edc2e-114">The name of the parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="edc2e-115">例如，对于方法签名 `Type.GetInterfaceMap(Type interfaceType)`，`Name` 特性的值为“接口类型”。</span><span class="sxs-lookup"><span data-stu-id="edc2e-115">For example, for the method signature `Type.GetInterfaceMap(Type interfaceType)`, the value of the `Name` attribute is "interfaceType".</span></span>|  
|`Activate`|<span data-ttu-id="edc2e-116">反射</span><span class="sxs-lookup"><span data-stu-id="edc2e-116">Reflection</span></span>|<span data-ttu-id="edc2e-117">可选特性。</span><span class="sxs-lookup"><span data-stu-id="edc2e-117">Optional attribute.</span></span> <span data-ttu-id="edc2e-118">控制运行时对构造函数的访问，以启用实例激活。</span><span class="sxs-lookup"><span data-stu-id="edc2e-118">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="edc2e-119">反射</span><span class="sxs-lookup"><span data-stu-id="edc2e-119">Reflection</span></span>|<span data-ttu-id="edc2e-120">可选特性。</span><span class="sxs-lookup"><span data-stu-id="edc2e-120">Optional attribute.</span></span> <span data-ttu-id="edc2e-121">控制对有关程序元素信息的查询，但并不启用任何运行时访问。</span><span class="sxs-lookup"><span data-stu-id="edc2e-121">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="edc2e-122">反射</span><span class="sxs-lookup"><span data-stu-id="edc2e-122">Reflection</span></span>|<span data-ttu-id="edc2e-123">可选特性。</span><span class="sxs-lookup"><span data-stu-id="edc2e-123">Optional attribute.</span></span> <span data-ttu-id="edc2e-124">控制运行时对所有类型成员的访问，包括构造函数、方法、字段、属性和事件，以启用动态编程。</span><span class="sxs-lookup"><span data-stu-id="edc2e-124">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="edc2e-125">序列化</span><span class="sxs-lookup"><span data-stu-id="edc2e-125">Serialization</span></span>|<span data-ttu-id="edc2e-126">可选特性。</span><span class="sxs-lookup"><span data-stu-id="edc2e-126">Optional attribute.</span></span> <span data-ttu-id="edc2e-127">控制运行时对构造函数、字段和属性的访问，使类型实例得到序列化和反序列化处理，这是通过库进行的，例如 Newtonsoft JSON 序列化程序。</span><span class="sxs-lookup"><span data-stu-id="edc2e-127">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="edc2e-128">序列化</span><span class="sxs-lookup"><span data-stu-id="edc2e-128">Serialization</span></span>|<span data-ttu-id="edc2e-129">可选特性。</span><span class="sxs-lookup"><span data-stu-id="edc2e-129">Optional attribute.</span></span> <span data-ttu-id="edc2e-130">控制使用 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> 类的序列化策略。</span><span class="sxs-lookup"><span data-stu-id="edc2e-130">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="edc2e-131">序列化</span><span class="sxs-lookup"><span data-stu-id="edc2e-131">Serialization</span></span>|<span data-ttu-id="edc2e-132">可选特性。</span><span class="sxs-lookup"><span data-stu-id="edc2e-132">Optional attribute.</span></span> <span data-ttu-id="edc2e-133">控制使用 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> 类的 JSON 序列化策略。</span><span class="sxs-lookup"><span data-stu-id="edc2e-133">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="edc2e-134">序列化</span><span class="sxs-lookup"><span data-stu-id="edc2e-134">Serialization</span></span>|<span data-ttu-id="edc2e-135">可选特性。</span><span class="sxs-lookup"><span data-stu-id="edc2e-135">Optional attribute.</span></span> <span data-ttu-id="edc2e-136">控制使用 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> 类的 XML 序列化策略。</span><span class="sxs-lookup"><span data-stu-id="edc2e-136">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="edc2e-137">Interop</span><span class="sxs-lookup"><span data-stu-id="edc2e-137">Interop</span></span>|<span data-ttu-id="edc2e-138">可选特性。</span><span class="sxs-lookup"><span data-stu-id="edc2e-138">Optional attribute.</span></span> <span data-ttu-id="edc2e-139">控制封送引用类型到 Windows 运行时和 COM 的策略。</span><span class="sxs-lookup"><span data-stu-id="edc2e-139">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="edc2e-140">Interop</span><span class="sxs-lookup"><span data-stu-id="edc2e-140">Interop</span></span>|<span data-ttu-id="edc2e-141">可选特性。</span><span class="sxs-lookup"><span data-stu-id="edc2e-141">Optional attribute.</span></span> <span data-ttu-id="edc2e-142">控制将委托类型作为函数指针封送到本机代码的策略。</span><span class="sxs-lookup"><span data-stu-id="edc2e-142">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="edc2e-143">Interop</span><span class="sxs-lookup"><span data-stu-id="edc2e-143">Interop</span></span>|<span data-ttu-id="edc2e-144">可选特性。</span><span class="sxs-lookup"><span data-stu-id="edc2e-144">Optional attribute.</span></span> <span data-ttu-id="edc2e-145">控制封送处理值类型到本机代码的策略。</span><span class="sxs-lookup"><span data-stu-id="edc2e-145">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="edc2e-146">Name 特性</span><span class="sxs-lookup"><span data-stu-id="edc2e-146">Name attribute</span></span>  
  
|<span data-ttu-id="edc2e-147">值</span><span class="sxs-lookup"><span data-stu-id="edc2e-147">Value</span></span>|<span data-ttu-id="edc2e-148">说明</span><span class="sxs-lookup"><span data-stu-id="edc2e-148">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="edc2e-149">*parameter_name*</span><span class="sxs-lookup"><span data-stu-id="edc2e-149">*parameter_name*</span></span>|<span data-ttu-id="edc2e-150">类型 <xref:System.Type> 的参数名称。</span><span class="sxs-lookup"><span data-stu-id="edc2e-150">The name of the parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="edc2e-151">例如，对于方法签名 `Type.GetInterfaceMap(Type interfaceType)`，`Name` 特性的值为“接口类型”。</span><span class="sxs-lookup"><span data-stu-id="edc2e-151">For example, for the method signature `Type.GetInterfaceMap(Type interfaceType)`, the value of the `Name` attribute is "interfaceType".</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="edc2e-152">所有其他特性</span><span class="sxs-lookup"><span data-stu-id="edc2e-152">All other attributes</span></span>  
  
|<span data-ttu-id="edc2e-153">值</span><span class="sxs-lookup"><span data-stu-id="edc2e-153">Value</span></span>|<span data-ttu-id="edc2e-154">说明</span><span class="sxs-lookup"><span data-stu-id="edc2e-154">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="edc2e-155">*策略_设置*</span><span class="sxs-lookup"><span data-stu-id="edc2e-155">*policy_setting*</span></span>|<span data-ttu-id="edc2e-156">该设置将应用到这种策略类型。</span><span class="sxs-lookup"><span data-stu-id="edc2e-156">The setting to apply to this policy type.</span></span> <span data-ttu-id="edc2e-157">可能值为 `All`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal` 以及 `Required All`。</span><span class="sxs-lookup"><span data-stu-id="edc2e-157">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="edc2e-158">有关详细信息，请参阅[运行时指令策略设置](runtime-directive-policy-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="edc2e-158">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="edc2e-159">子元素</span><span class="sxs-lookup"><span data-stu-id="edc2e-159">Child Elements</span></span>  

 <span data-ttu-id="edc2e-160">无。</span><span class="sxs-lookup"><span data-stu-id="edc2e-160">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="edc2e-161">父元素</span><span class="sxs-lookup"><span data-stu-id="edc2e-161">Parent Elements</span></span>  
  
|<span data-ttu-id="edc2e-162">元素</span><span class="sxs-lookup"><span data-stu-id="edc2e-162">Element</span></span>|<span data-ttu-id="edc2e-163">说明</span><span class="sxs-lookup"><span data-stu-id="edc2e-163">Description</span></span>|  
|-------------|-----------------|  
|[\<Method>](method-element-net-native.md)|<span data-ttu-id="edc2e-164">将运行时反射策略应用到一个构造函数或方法。</span><span class="sxs-lookup"><span data-stu-id="edc2e-164">Applies runtime reflection policy to a constructor or method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="edc2e-165">备注</span><span class="sxs-lookup"><span data-stu-id="edc2e-165">Remarks</span></span>  

 <span data-ttu-id="edc2e-166">`<TypeParameter>`元素类似于 [\<Parameter>](parameter-element-net-native.md) 元素，只不过它只能应用于类型的参数 <xref:System.Type> 。</span><span class="sxs-lookup"><span data-stu-id="edc2e-166">The `<TypeParameter>` element is similar to the [\<Parameter>](parameter-element-net-native.md) element, except that it can be applied only to parameters of type <xref:System.Type>.</span></span> <span data-ttu-id="edc2e-167">它将策略应用到任何在运行时间由 `Name` 特性指定的以类型参数为代表的类型。</span><span class="sxs-lookup"><span data-stu-id="edc2e-167">It applies policy to whatever type is represented at run time by the type argument specified by the `Name` attribute.</span></span>  
  
 <span data-ttu-id="edc2e-168">例如，NewtonSoft JSON 序列化程序包含一个静态 `JsonConvert.DeserializeObject(String value, Type type)` 方法。</span><span class="sxs-lookup"><span data-stu-id="edc2e-168">For example, the NewtonSoft JSON serializer includes a static `JsonConvert.DeserializeObject(String value, Type type)` method.</span></span> <span data-ttu-id="edc2e-169">以下是反射指令：</span><span class="sxs-lookup"><span data-stu-id="edc2e-169">The following reflection directives:</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject">  
         <GenericParameter Name="type" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
 <span data-ttu-id="edc2e-170">指定 `type` 参数所代表的运行时类型的元数据应可用于序列化。</span><span class="sxs-lookup"><span data-stu-id="edc2e-170">specify that metadata for the runtime type represented by the `type` argument should be made available for serialization.</span></span> <span data-ttu-id="edc2e-171">如果这些运行时指令适用于一个包含以下源代码的项目：</span><span class="sxs-lookup"><span data-stu-id="edc2e-171">If these runtime directives apply to a project that includes the following source code:</span></span>  
  
```csharp  
Type t = typeof(StockQuote);  
Object obj = JsonConvert.DeserializeObject(data, t);  
```  
  
 <span data-ttu-id="edc2e-172">反射指令使 `StockQuote` 类型的元数据在运行时间可由 NewtonSoft JSON 序列化程序使用。</span><span class="sxs-lookup"><span data-stu-id="edc2e-172">the reflection directives make metadata for the `StockQuote` type available for the NewtonSoft JSON serializer at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edc2e-173">请参阅</span><span class="sxs-lookup"><span data-stu-id="edc2e-173">See also</span></span>

- [<span data-ttu-id="edc2e-174">\<Method> 元素</span><span class="sxs-lookup"><span data-stu-id="edc2e-174">\<Method> Element</span></span>](method-element-net-native.md)
- [<span data-ttu-id="edc2e-175">运行时指令 (rd.xml) 配置文件引用</span><span class="sxs-lookup"><span data-stu-id="edc2e-175">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="edc2e-176">运行时指令策略设置</span><span class="sxs-lookup"><span data-stu-id="edc2e-176">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="edc2e-177">运行时指令元素</span><span class="sxs-lookup"><span data-stu-id="edc2e-177">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
