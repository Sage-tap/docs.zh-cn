---
description: 了解详细信息： <disableFusionUpdatesFromADManager> 元素
title: <disableFusionUpdatesFromADManager> 元素
ms.date: 03/30/2017
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
ms.openlocfilehash: c3b5758a12fc78c67ec0a4a9631361808724e72a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787079"
---
# <a name="disablefusionupdatesfromadmanager-element"></a><span data-ttu-id="e6a7f-103">\<disableFusionUpdatesFromADManager> 元素</span><span class="sxs-lookup"><span data-stu-id="e6a7f-103">\<disableFusionUpdatesFromADManager> Element</span></span>

<span data-ttu-id="e6a7f-104">指定是否禁用允许运行时主机为应用程序域重写配置设置的默认行为。</span><span class="sxs-lookup"><span data-stu-id="e6a7f-104">Specifies whether the default behavior, which is to allow the runtime host to override configuration settings for an application domain, is disabled.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<disableFusionUpdatesFromADManager>**  
  
## <a name="syntax"></a><span data-ttu-id="e6a7f-105">语法</span><span class="sxs-lookup"><span data-stu-id="e6a7f-105">Syntax</span></span>  
  
```xml  
<disableFusionUpdatesFromADManager enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6a7f-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="e6a7f-106">Attributes and Elements</span></span>  

 <span data-ttu-id="e6a7f-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e6a7f-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6a7f-108">特性</span><span class="sxs-lookup"><span data-stu-id="e6a7f-108">Attributes</span></span>  
  
|<span data-ttu-id="e6a7f-109">属性</span><span class="sxs-lookup"><span data-stu-id="e6a7f-109">Attribute</span></span>|<span data-ttu-id="e6a7f-110">说明</span><span class="sxs-lookup"><span data-stu-id="e6a7f-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e6a7f-111">enabled</span><span class="sxs-lookup"><span data-stu-id="e6a7f-111">enabled</span></span>|<span data-ttu-id="e6a7f-112">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="e6a7f-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="e6a7f-113">指定是否禁用用于重写合成设置的默认功能。</span><span class="sxs-lookup"><span data-stu-id="e6a7f-113">Specifies whether the default ability to override Fusion settings is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="e6a7f-114">enabled 特性</span><span class="sxs-lookup"><span data-stu-id="e6a7f-114">enabled Attribute</span></span>  
  
|<span data-ttu-id="e6a7f-115">值</span><span class="sxs-lookup"><span data-stu-id="e6a7f-115">Value</span></span>|<span data-ttu-id="e6a7f-116">说明</span><span class="sxs-lookup"><span data-stu-id="e6a7f-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e6a7f-117">0</span><span class="sxs-lookup"><span data-stu-id="e6a7f-117">0</span></span>|<span data-ttu-id="e6a7f-118">不要禁用替代合成设置的功能。</span><span class="sxs-lookup"><span data-stu-id="e6a7f-118">Do not disable the ability to override Fusion settings.</span></span> <span data-ttu-id="e6a7f-119">这是默认行为，从 .NET Framework 4 开始。</span><span class="sxs-lookup"><span data-stu-id="e6a7f-119">This is the default behavior, starting with the .NET Framework 4.</span></span>|  
|<span data-ttu-id="e6a7f-120">1</span><span class="sxs-lookup"><span data-stu-id="e6a7f-120">1</span></span>|<span data-ttu-id="e6a7f-121">禁用重写合成设置的功能。</span><span class="sxs-lookup"><span data-stu-id="e6a7f-121">Disable the ability to override Fusion settings.</span></span> <span data-ttu-id="e6a7f-122">这会恢复到 .NET Framework 早期版本的行为。</span><span class="sxs-lookup"><span data-stu-id="e6a7f-122">This reverts to the behavior of earlier versions of the .NET Framework.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e6a7f-123">子元素</span><span class="sxs-lookup"><span data-stu-id="e6a7f-123">Child Elements</span></span>  

 <span data-ttu-id="e6a7f-124">无。</span><span class="sxs-lookup"><span data-stu-id="e6a7f-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e6a7f-125">父元素</span><span class="sxs-lookup"><span data-stu-id="e6a7f-125">Parent Elements</span></span>  
  
|<span data-ttu-id="e6a7f-126">元素</span><span class="sxs-lookup"><span data-stu-id="e6a7f-126">Element</span></span>|<span data-ttu-id="e6a7f-127">说明</span><span class="sxs-lookup"><span data-stu-id="e6a7f-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e6a7f-128">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="e6a7f-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="e6a7f-129">包含有关程序集绑定和垃圾回收的信息。</span><span class="sxs-lookup"><span data-stu-id="e6a7f-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6a7f-130">备注</span><span class="sxs-lookup"><span data-stu-id="e6a7f-130">Remarks</span></span>  

 <span data-ttu-id="e6a7f-131">从 .NET Framework 4 开始，默认行为是允许 <xref:System.AppDomainManager> 对象 <xref:System.AppDomainSetup.ConfigurationFile%2A> <xref:System.AppDomainSetup.SetConfigurationBytes%2A> <xref:System.AppDomainSetup> <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> 在的子类中使用传递给方法实现的属性或对象的方法来重写配置设置 <xref:System.AppDomainManager> 。</span><span class="sxs-lookup"><span data-stu-id="e6a7f-131">Starting with the .NET Framework 4, the default behavior is to allow the <xref:System.AppDomainManager> object to override configuration settings by using the <xref:System.AppDomainSetup.ConfigurationFile%2A> property or the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method of the <xref:System.AppDomainSetup> object that is passed to your implementation of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method, in your subclass of <xref:System.AppDomainManager>.</span></span> <span data-ttu-id="e6a7f-132">对于默认应用程序域，所更改的设置将覆盖由应用程序配置文件指定的设置。</span><span class="sxs-lookup"><span data-stu-id="e6a7f-132">For the default application domain, the settings you change override the settings that were specified by the application configuration file.</span></span> <span data-ttu-id="e6a7f-133">对于其他应用程序域，它们会重写传递给或方法的配置设置 <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="e6a7f-133">For other application domains, they override the configuration settings that were passed to the <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="e6a7f-134">可以传递新的配置信息，也可以将 null (传递 `Nothing` 到 Visual Basic) ，以消除传入的配置信息。</span><span class="sxs-lookup"><span data-stu-id="e6a7f-134">You can either pass new configuration information, or pass null (`Nothing` in Visual Basic) to eliminate configuration information that was passed in.</span></span>  
  
 <span data-ttu-id="e6a7f-135">不要将配置信息传递给 <xref:System.AppDomainSetup.ConfigurationFile%2A> 属性和 <xref:System.AppDomainSetup.SetConfigurationBytes%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="e6a7f-135">Do not pass configuration information to both the <xref:System.AppDomainSetup.ConfigurationFile%2A> property and the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method.</span></span> <span data-ttu-id="e6a7f-136">如果将配置信息传递到这两个文件，则会忽略传递给属性的信息 <xref:System.AppDomainSetup.ConfigurationFile%2A> ，因为 <xref:System.AppDomainSetup.SetConfigurationBytes%2A> 方法会重写应用程序配置文件中的配置信息。</span><span class="sxs-lookup"><span data-stu-id="e6a7f-136">If you pass configuration information to both, the information you pass to the <xref:System.AppDomainSetup.ConfigurationFile%2A> property is ignored, because the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method overrides configuration information from the application configuration file.</span></span> <span data-ttu-id="e6a7f-137">如果使用 <xref:System.AppDomainSetup.ConfigurationFile%2A> 属性，则可以将 `Nothing` Visual Basic) 中的 null (传递给方法， <xref:System.AppDomainSetup.SetConfigurationBytes%2A> 以消除对或方法的调用中指定的任何配置字节 <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="e6a7f-137">If you use the <xref:System.AppDomainSetup.ConfigurationFile%2A> property, you can pass null (`Nothing` in Visual Basic) to the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method to eliminate any configuration bytes that were specified in the call to the <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="e6a7f-138">除了配置信息之外，你还可以在 <xref:System.AppDomainSetup> 传递给方法的实现的对象上更改以下设置 <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> ： <xref:System.AppDomainSetup.ApplicationBase%2A> 、 <xref:System.AppDomainSetup.ApplicationName%2A> 、 <xref:System.AppDomainSetup.CachePath%2A> 、 <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A> 、、 <xref:System.AppDomainSetup.DisallowBindingRedirects%2A> <xref:System.AppDomainSetup.DisallowCodeDownload%2A> <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A> <xref:System.AppDomainSetup.DynamicBase%2A> <xref:System.AppDomainSetup.LoaderOptimization%2A> <xref:System.AppDomainSetup.PrivateBinPath%2A> <xref:System.AppDomainSetup.PrivateBinPathProbe%2A> <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> <xref:System.AppDomainSetup.ShadowCopyFiles%2A> 、、、、、、和。</span><span class="sxs-lookup"><span data-stu-id="e6a7f-138">In addition to configuration information, you can change the following settings on the <xref:System.AppDomainSetup> object that is passed to your implementation of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method: <xref:System.AppDomainSetup.ApplicationBase%2A>, <xref:System.AppDomainSetup.ApplicationName%2A>, <xref:System.AppDomainSetup.CachePath%2A>, <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>, <xref:System.AppDomainSetup.DisallowBindingRedirects%2A>, <xref:System.AppDomainSetup.DisallowCodeDownload%2A>, <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>, <xref:System.AppDomainSetup.DynamicBase%2A>, <xref:System.AppDomainSetup.LoaderOptimization%2A>, <xref:System.AppDomainSetup.PrivateBinPath%2A>, <xref:System.AppDomainSetup.PrivateBinPathProbe%2A>, <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>, and <xref:System.AppDomainSetup.ShadowCopyFiles%2A>.</span></span>  
  
 <span data-ttu-id="e6a7f-139">作为使用元素的替代方法 `<disableFusionUpdatesFromADManager>` ，你可以通过创建注册表设置或通过设置环境变量来禁用默认行为。</span><span class="sxs-lookup"><span data-stu-id="e6a7f-139">As an alternative to using the `<disableFusionUpdatesFromADManager>` element, you can disable the default behavior by creating a registry setting or by setting an environment variable.</span></span> <span data-ttu-id="e6a7f-140">在注册表中，创建一个名为或的 DWORD 值 `COMPLUS_disableFusionUpdatesFromADManager` `HKCU\Software\Microsoft\.NETFramework` `HKLM\Software\Microsoft\.NETFramework` ，并将该值设置为1。</span><span class="sxs-lookup"><span data-stu-id="e6a7f-140">In the registry, create a DWORD value named `COMPLUS_disableFusionUpdatesFromADManager` under `HKCU\Software\Microsoft\.NETFramework` or `HKLM\Software\Microsoft\.NETFramework`, and set the value to 1.</span></span> <span data-ttu-id="e6a7f-141">在命令行中，将环境变量设置 `COMPLUS_disableFusionUpdatesFromADManager` 为1。</span><span class="sxs-lookup"><span data-stu-id="e6a7f-141">At the command line, set the environment variable `COMPLUS_disableFusionUpdatesFromADManager` to 1.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6a7f-142">示例</span><span class="sxs-lookup"><span data-stu-id="e6a7f-142">Example</span></span>  

 <span data-ttu-id="e6a7f-143">下面的示例演示如何使用元素禁用重写合成设置的功能 `<disableFusionUpdatesFromADManager>` 。</span><span class="sxs-lookup"><span data-stu-id="e6a7f-143">The following example shows how to disable the ability to override Fusion settings by using the `<disableFusionUpdatesFromADManager>` element.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e6a7f-144">请参阅</span><span class="sxs-lookup"><span data-stu-id="e6a7f-144">See also</span></span>

- [<span data-ttu-id="e6a7f-145">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="e6a7f-145">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e6a7f-146">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="e6a7f-146">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="e6a7f-147">运行时如何定位程序集</span><span class="sxs-lookup"><span data-stu-id="e6a7f-147">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
