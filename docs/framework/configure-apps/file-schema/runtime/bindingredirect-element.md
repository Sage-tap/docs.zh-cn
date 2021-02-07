---
description: 了解详细信息： <bindingRedirect> 元素
title: <bindingRedirect> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/bindingRedirect
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bindingRedirect
helpviewer_keywords:
- <bindingRedirect> element
- container tags, <bindingRedirect> element
- bindingRedirect element
ms.assetid: 67784ecd-9663-434e-bd6a-26975e447ac0
ms.openlocfilehash: 833ee73fa11d179ac855f3ac4d2bca8d7a2226ac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99719170"
---
# <a name="bindingredirect-element"></a><span data-ttu-id="2736b-103">\<bindingRedirect> 元素</span><span class="sxs-lookup"><span data-stu-id="2736b-103">\<bindingRedirect> Element</span></span>

<span data-ttu-id="2736b-104">将一个程序集版本重定向到另一个版本。</span><span class="sxs-lookup"><span data-stu-id="2736b-104">Redirects one assembly version to another.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bindingRedirect>**  
  
## <a name="syntax"></a><span data-ttu-id="2736b-105">语法</span><span class="sxs-lookup"><span data-stu-id="2736b-105">Syntax</span></span>  
  
```xml  
   <bindingRedirect
oldVersion="existing assembly version"  
newVersion="new assembly version"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2736b-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="2736b-106">Attributes and Elements</span></span>  

 <span data-ttu-id="2736b-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="2736b-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2736b-108">特性</span><span class="sxs-lookup"><span data-stu-id="2736b-108">Attributes</span></span>  
  
|<span data-ttu-id="2736b-109">属性</span><span class="sxs-lookup"><span data-stu-id="2736b-109">Attribute</span></span>|<span data-ttu-id="2736b-110">描述</span><span class="sxs-lookup"><span data-stu-id="2736b-110">Description</span></span>|  
|---------------|-----------------|  
|`oldVersion`|<span data-ttu-id="2736b-111">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="2736b-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="2736b-112">指定最初请求的程序集的版本。</span><span class="sxs-lookup"><span data-stu-id="2736b-112">Specifies the version of the assembly that was originally requested.</span></span> <span data-ttu-id="2736b-113">程序集版本号的格式为 "主要版本. 次要版本. 内部版本. *修订* 版本"。</span><span class="sxs-lookup"><span data-stu-id="2736b-113">The format of an assembly version number is *major.minor.build.revision*.</span></span> <span data-ttu-id="2736b-114">该版本号的每个部分的有效值介于 0 和 65535 之间。</span><span class="sxs-lookup"><span data-stu-id="2736b-114">Valid values for each part of this version number are 0 to 65535.</span></span><br /><br /> <span data-ttu-id="2736b-115">你还可以按下列格式指定版本范围：</span><span class="sxs-lookup"><span data-stu-id="2736b-115">You can also specify a range of versions in the following format:</span></span><br /><br /> <span data-ttu-id="2736b-116">*n. n。 n n n n n n n n n n n n n n n n n n n n*</span><span class="sxs-lookup"><span data-stu-id="2736b-116">*n.n.n.n - n.n.n.n*</span></span>|  
|`newVersion`|<span data-ttu-id="2736b-117">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="2736b-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="2736b-118">用以下格式指定要使用的程序集的版本，而不是最初请求的 *版本：*</span><span class="sxs-lookup"><span data-stu-id="2736b-118">Specifies the version of the assembly to use instead of the originally requested version in the format: *n.n.n.n*</span></span><br /><br /> <span data-ttu-id="2736b-119">此值可以指定 `oldVersion` 之前的版本。</span><span class="sxs-lookup"><span data-stu-id="2736b-119">This value can specify an earlier version than `oldVersion`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2736b-120">子元素</span><span class="sxs-lookup"><span data-stu-id="2736b-120">Child Elements</span></span>  
  
|<span data-ttu-id="2736b-121">元素</span><span class="sxs-lookup"><span data-stu-id="2736b-121">Element</span></span>|<span data-ttu-id="2736b-122">说明</span><span class="sxs-lookup"><span data-stu-id="2736b-122">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2736b-123">无</span><span class="sxs-lookup"><span data-stu-id="2736b-123">None</span></span>||  
  
### <a name="parent-elements"></a><span data-ttu-id="2736b-124">父元素</span><span class="sxs-lookup"><span data-stu-id="2736b-124">Parent Elements</span></span>  
  
|<span data-ttu-id="2736b-125">元素</span><span class="sxs-lookup"><span data-stu-id="2736b-125">Element</span></span>|<span data-ttu-id="2736b-126">说明</span><span class="sxs-lookup"><span data-stu-id="2736b-126">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="2736b-127">包含有关程序集版本重定向和程序集位置的信息。</span><span class="sxs-lookup"><span data-stu-id="2736b-127">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="2736b-128">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="2736b-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="2736b-129">封装每个程序集的绑定策略和程序集位置。</span><span class="sxs-lookup"><span data-stu-id="2736b-129">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="2736b-130">为每个程序集使用一个 dependentAssembly 元素。</span><span class="sxs-lookup"><span data-stu-id="2736b-130">Use one dependentAssembly element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="2736b-131">包含有关程序集绑定和垃圾回收的信息。</span><span class="sxs-lookup"><span data-stu-id="2736b-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2736b-132">备注</span><span class="sxs-lookup"><span data-stu-id="2736b-132">Remarks</span></span>  

 <span data-ttu-id="2736b-133">在针对具有强名称的程序集生成 .NET Framework 应用程序时，默认情况下，应用程序在运行时使用该版本的程序集，即使提供了新版本也是如此。</span><span class="sxs-lookup"><span data-stu-id="2736b-133">When you build a .NET Framework application against a strong-named assembly, the application uses that version of the assembly at run time by default, even if a new version is available.</span></span> <span data-ttu-id="2736b-134">但是，你可以将应用程序配置为针对更新版本的程序集运行。</span><span class="sxs-lookup"><span data-stu-id="2736b-134">However, you can configure the application to run against a newer version of the assembly.</span></span> <span data-ttu-id="2736b-135">有关运行时如何使用这些文件来确定要使用的程序集版本的详细信息，请参阅 [运行时如何定位程序集](../../../deployment/how-the-runtime-locates-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="2736b-135">For details on how the runtime uses these files to determine which assembly version to use, see [How the Runtime Locates Assemblies](../../../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="2736b-136">通过在一个 `bindingRedirect` 元素中包含多个 `dependentAssembly` 元素，你可以重定向多个程序集版本。</span><span class="sxs-lookup"><span data-stu-id="2736b-136">You can redirect more than one assembly version by including multiple `bindingRedirect` elements in a `dependentAssembly` element.</span></span> <span data-ttu-id="2736b-137">你还可从程序集的更新版本重定向到较旧版本。</span><span class="sxs-lookup"><span data-stu-id="2736b-137">You can also redirect from a newer version to an older version of the assembly.</span></span>  
  
 <span data-ttu-id="2736b-138">应用程序配置文件中的显式程序集绑定重定向需要安全权限。</span><span class="sxs-lookup"><span data-stu-id="2736b-138">Explicit assembly binding redirection in an application configuration file requires a security permission.</span></span> <span data-ttu-id="2736b-139">这适用于对 .NET Framework 程序集和来自第三方的程序集的重定向。</span><span class="sxs-lookup"><span data-stu-id="2736b-139">This applies to redirection of .NET Framework assemblies and assemblies from third parties.</span></span> <span data-ttu-id="2736b-140">通过在上设置标志来授予权限 <xref:System.Security.Permissions.SecurityPermissionFlag> <xref:System.Security.Permissions.SecurityPermission> 。</span><span class="sxs-lookup"><span data-stu-id="2736b-140">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="2736b-141">有关详细信息，请参阅 [程序集绑定重定向安全权限](../../assembly-binding-redirection-security-permission.md)。</span><span class="sxs-lookup"><span data-stu-id="2736b-141">For more information, see [Assembly Binding Redirection Security Permission](../../assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2736b-142">示例</span><span class="sxs-lookup"><span data-stu-id="2736b-142">Example</span></span>  

 <span data-ttu-id="2736b-143">下面的示例演示如何将一个程序集版本重定向到另一个版本。</span><span class="sxs-lookup"><span data-stu-id="2736b-143">The following example shows how to redirect one assembly version to another.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <bindingRedirect oldVersion="1.0.0.0"  
                             newVersion="2.0.0.0"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2736b-144">请参阅</span><span class="sxs-lookup"><span data-stu-id="2736b-144">See also</span></span>

- [<span data-ttu-id="2736b-145">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="2736b-145">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="2736b-146">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="2736b-146">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="2736b-147">重定向程序集版本</span><span class="sxs-lookup"><span data-stu-id="2736b-147">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
