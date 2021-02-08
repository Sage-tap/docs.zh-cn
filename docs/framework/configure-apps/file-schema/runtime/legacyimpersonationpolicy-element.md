---
description: 了解详细信息： <legacyImpersonationPolicy> 元素
title: <legacyImpersonationPolicy> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#legacyImpersonationPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/legacyImpersonationPolicy
helpviewer_keywords:
- <legacyImpersonationPolicy> element
- legacyImpersonationPolicy element
ms.assetid: 6e00af10-42f3-4235-8415-1bb2db78394e
ms.openlocfilehash: 36cc3336e8e3c0196ae20fc749fc2239c35c8584
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782359"
---
# <a name="legacyimpersonationpolicy-element"></a><span data-ttu-id="2a5ad-103">\<legacyImpersonationPolicy> 元素</span><span class="sxs-lookup"><span data-stu-id="2a5ad-103">\<legacyImpersonationPolicy> Element</span></span>

<span data-ttu-id="2a5ad-104">指定 Windows 标识不流经异步点，而不考虑当前线程上执行上下文的流设置。</span><span class="sxs-lookup"><span data-stu-id="2a5ad-104">Specifies that the Windows identity does not flow across asynchronous points, regardless of the flow settings for the execution context on the current thread.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<legacyImpersonationPolicy>**  
  
## <a name="syntax"></a><span data-ttu-id="2a5ad-105">语法</span><span class="sxs-lookup"><span data-stu-id="2a5ad-105">Syntax</span></span>  
  
```xml  
<legacyImpersonationPolicy
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2a5ad-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="2a5ad-106">Attributes and Elements</span></span>  

 <span data-ttu-id="2a5ad-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="2a5ad-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2a5ad-108">特性</span><span class="sxs-lookup"><span data-stu-id="2a5ad-108">Attributes</span></span>  
  
|<span data-ttu-id="2a5ad-109">属性</span><span class="sxs-lookup"><span data-stu-id="2a5ad-109">Attribute</span></span>|<span data-ttu-id="2a5ad-110">描述</span><span class="sxs-lookup"><span data-stu-id="2a5ad-110">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="2a5ad-111">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="2a5ad-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="2a5ad-112">指定不 <xref:System.Security.Principal.WindowsIdentity> 流经异步点，无论 <xref:System.Threading.ExecutionContext> 当前线程上的流设置如何。</span><span class="sxs-lookup"><span data-stu-id="2a5ad-112">Specifies that the <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="2a5ad-113">enabled 特性</span><span class="sxs-lookup"><span data-stu-id="2a5ad-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="2a5ad-114">值</span><span class="sxs-lookup"><span data-stu-id="2a5ad-114">Value</span></span>|<span data-ttu-id="2a5ad-115">说明</span><span class="sxs-lookup"><span data-stu-id="2a5ad-115">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="2a5ad-116"><xref:System.Security.Principal.WindowsIdentity> 根据当前线程的流设置，跨异步点流动 <xref:System.Threading.ExecutionContext> 。</span><span class="sxs-lookup"><span data-stu-id="2a5ad-116"><xref:System.Security.Principal.WindowsIdentity> flows across asynchronous points depending upon the <xref:System.Threading.ExecutionContext> flow settings for the current thread.</span></span> <span data-ttu-id="2a5ad-117">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="2a5ad-117">This is the default.</span></span>|  
|`true`|<span data-ttu-id="2a5ad-118"><xref:System.Security.Principal.WindowsIdentity> 不流经异步点，无论 <xref:System.Threading.ExecutionContext> 当前线程上的流设置如何。</span><span class="sxs-lookup"><span data-stu-id="2a5ad-118"><xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2a5ad-119">子元素</span><span class="sxs-lookup"><span data-stu-id="2a5ad-119">Child Elements</span></span>  

 <span data-ttu-id="2a5ad-120">无。</span><span class="sxs-lookup"><span data-stu-id="2a5ad-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2a5ad-121">父元素</span><span class="sxs-lookup"><span data-stu-id="2a5ad-121">Parent Elements</span></span>  
  
|<span data-ttu-id="2a5ad-122">元素</span><span class="sxs-lookup"><span data-stu-id="2a5ad-122">Element</span></span>|<span data-ttu-id="2a5ad-123">说明</span><span class="sxs-lookup"><span data-stu-id="2a5ad-123">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="2a5ad-124">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="2a5ad-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="2a5ad-125">包含有关程序集绑定和垃圾回收的信息。</span><span class="sxs-lookup"><span data-stu-id="2a5ad-125">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a5ad-126">备注</span><span class="sxs-lookup"><span data-stu-id="2a5ad-126">Remarks</span></span>  

 <span data-ttu-id="2a5ad-127">在 .NET Framework 版本1.0 和1.1 中，不在 <xref:System.Security.Principal.WindowsIdentity> 任何用户定义的异步点上流动。</span><span class="sxs-lookup"><span data-stu-id="2a5ad-127">In the .NET Framework versions 1.0 and 1.1, the <xref:System.Security.Principal.WindowsIdentity> does not flow across any user-defined asynchronous points.</span></span> <span data-ttu-id="2a5ad-128">从 .NET Framework 版本2.0 开始，有一个对象， <xref:System.Threading.ExecutionContext> 该对象包含当前正在执行的线程的相关信息，并在应用程序域中的异步点之间流动。</span><span class="sxs-lookup"><span data-stu-id="2a5ad-128">Starting with the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and it flows across asynchronous points within an application domain.</span></span> <span data-ttu-id="2a5ad-129"><xref:System.Security.Principal.WindowsIdentity>包含在此执行上下文中，因此也会流过异步点，这意味着，如果存在模拟上下文，它也会流动。</span><span class="sxs-lookup"><span data-stu-id="2a5ad-129">The <xref:System.Security.Principal.WindowsIdentity> is included in this execution context and therefore also flows across the asynchronous points, which means that if an impersonation context exists, it will flow as well.</span></span>  
  
 <span data-ttu-id="2a5ad-130">从 .NET Framework 2.0 开始，可以使用 `<legacyImpersonationPolicy>` 元素指定不  <xref:System.Security.Principal.WindowsIdentity> 流经异步点。</span><span class="sxs-lookup"><span data-stu-id="2a5ad-130">Starting with the .NET Framework 2.0, you can use the `<legacyImpersonationPolicy>` element to specify that  <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2a5ad-131">公共语言运行时 (CLR) 知道仅使用托管代码执行的模拟操作，而不是在托管代码之外执行的模拟，例如通过平台调用到非托管代码或通过直接调用 Win32 函数。</span><span class="sxs-lookup"><span data-stu-id="2a5ad-131">The common language runtime (CLR) is aware of impersonation operations performed using only managed code, not of impersonation performed outside of managed code, such as through platform invoke to unmanaged code or through direct calls to Win32 functions.</span></span> <span data-ttu-id="2a5ad-132">只有托管 <xref:System.Security.Principal.WindowsIdentity> 对象才能流经异步点，除非该 `alwaysFlowImpersonationPolicy` 元素已设置为 true (`<alwaysFlowImpersonationPolicy enabled="true"/>`) 。</span><span class="sxs-lookup"><span data-stu-id="2a5ad-132">Only managed <xref:System.Security.Principal.WindowsIdentity> objects can flow across asynchronous points, unless the `alwaysFlowImpersonationPolicy` element has been set to true (`<alwaysFlowImpersonationPolicy enabled="true"/>`).</span></span> <span data-ttu-id="2a5ad-133">将 `alwaysFlowImpersonationPolicy` 元素设置为 true 可指定无论模拟的执行方式如何，Windows 标识总是流经异步点。</span><span class="sxs-lookup"><span data-stu-id="2a5ad-133">Setting the `alwaysFlowImpersonationPolicy` element to true specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span> <span data-ttu-id="2a5ad-134">有关跨异步点流动非托管模拟的详细信息，请参阅[ \<alwaysFlowImpersonationPolicy> 元素](alwaysflowimpersonationpolicy-element.md)。</span><span class="sxs-lookup"><span data-stu-id="2a5ad-134">For more information on flowing unmanaged impersonation across asynchronous points, see [\<alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md).</span></span>  
  
 <span data-ttu-id="2a5ad-135">可以通过两种其他方式更改此默认行为：</span><span class="sxs-lookup"><span data-stu-id="2a5ad-135">You can alter this default behavior in two other ways:</span></span>  
  
1. <span data-ttu-id="2a5ad-136">在托管代码中，在每个线程的基础上。</span><span class="sxs-lookup"><span data-stu-id="2a5ad-136">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="2a5ad-137">通过 <xref:System.Threading.ExecutionContext> <xref:System.Security.SecurityContext> 使用 <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType> 、 <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> 或方法修改和设置，可以按线程禁止显示流 <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="2a5ad-137">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="2a5ad-138">在调用非托管承载接口时， (CLR) 加载公共语言运行时。</span><span class="sxs-lookup"><span data-stu-id="2a5ad-138">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="2a5ad-139">如果使用非托管宿主 (接口而不是简单的托管可执行) 文件来加载 CLR，则可以在 [CorBindToRuntimeEx 函数](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) 函数的调用中指定特殊标志。</span><span class="sxs-lookup"><span data-stu-id="2a5ad-139">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="2a5ad-140">若要为整个进程启用兼容模式，请将 `flags` [CorBindToRuntimeEx 函数](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) 的参数设置为 STARTUP_LEGACY_IMPERSONATION。</span><span class="sxs-lookup"><span data-stu-id="2a5ad-140">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) to STARTUP_LEGACY_IMPERSONATION.</span></span>  
  
 <span data-ttu-id="2a5ad-141">有关详细信息，请参阅[ \<alwaysFlowImpersonationPolicy> 元素](alwaysflowimpersonationpolicy-element.md)。</span><span class="sxs-lookup"><span data-stu-id="2a5ad-141">For more information, see the [\<alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md).</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="2a5ad-142">配置文件</span><span class="sxs-lookup"><span data-stu-id="2a5ad-142">Configuration File</span></span>  

 <span data-ttu-id="2a5ad-143">在 .NET Framework 应用程序中，此元素只能在应用程序配置文件中使用。</span><span class="sxs-lookup"><span data-stu-id="2a5ad-143">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="2a5ad-144">对于 ASP.NET 应用程序，可以在 \Microsoft.NET\Framework\vx.x.xxxx 目录中找到的 aspnet.config 文件中配置模拟流 \<Windows Folder> 。</span><span class="sxs-lookup"><span data-stu-id="2a5ad-144">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="2a5ad-145">默认情况下，ASP.NET 使用以下配置设置禁用 aspnet.config 文件中的模拟流：</span><span class="sxs-lookup"><span data-stu-id="2a5ad-145">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
``` xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="2a5ad-146">在 ASP.NET 中，如果要改为允许模拟流，则必须显式使用以下配置设置：</span><span class="sxs-lookup"><span data-stu-id="2a5ad-146">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="2a5ad-147">示例</span><span class="sxs-lookup"><span data-stu-id="2a5ad-147">Example</span></span>  

 <span data-ttu-id="2a5ad-148">下面的示例演示如何指定不跨异步点流式传输 Windows 标识的旧行为。</span><span class="sxs-lookup"><span data-stu-id="2a5ad-148">The following example shows how to specify the legacy behavior that does not flow the Windows identity across asynchronous points.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2a5ad-149">请参阅</span><span class="sxs-lookup"><span data-stu-id="2a5ad-149">See also</span></span>

- [<span data-ttu-id="2a5ad-150">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="2a5ad-150">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="2a5ad-151">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="2a5ad-151">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="2a5ad-152">\<alwaysFlowImpersonationPolicy> 元素</span><span class="sxs-lookup"><span data-stu-id="2a5ad-152">\<alwaysFlowImpersonationPolicy> Element</span></span>](alwaysflowimpersonationpolicy-element.md)
