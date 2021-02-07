---
description: 了解更多： WMI 提供程序
title: WMI 提供程序
ms.date: 03/30/2017
ms.assetid: 462f0db3-f4a4-4a4b-ac26-41fc25c670a4
ms.openlocfilehash: 23d673f55781204fb4ce54d7d8ee0dab7933484f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715088"
---
# <a name="wmi-provider"></a><span data-ttu-id="f33a0-103">WMI 提供程序</span><span class="sxs-lookup"><span data-stu-id="f33a0-103">WMI Provider</span></span>

<span data-ttu-id="f33a0-104">此示例演示如何使用内置于 WCF 中的 Windows Management Instrumentation (WMI) 提供程序，在运行时从 Windows Communication Foundation (WCF) 服务收集数据。</span><span class="sxs-lookup"><span data-stu-id="f33a0-104">This sample demonstrates how to gather data from Windows Communication Foundation (WCF) services at runtime by using the Windows Management Instrumentation (WMI) provider that is built into WCF.</span></span> <span data-ttu-id="f33a0-105">另外，此示例还演示如何向服务添加用户定义的 WMI 对象。</span><span class="sxs-lookup"><span data-stu-id="f33a0-105">Also, this sample demonstrates how to add a user-defined WMI object to a service.</span></span> <span data-ttu-id="f33a0-106">该示例将激活 [入门](getting-started-sample.md) 的 WMI 提供程序，并演示如何 `ICalculator` 在运行时从服务中收集数据。</span><span class="sxs-lookup"><span data-stu-id="f33a0-106">The sample activates the WMI provider for the [Getting Started](getting-started-sample.md) and demonstrates how to gather data from the `ICalculator` service at runtime.</span></span>  
  
 <span data-ttu-id="f33a0-107">WMI 是 Microsoft 基于 Web 的企业管理 (WBEM) 标准的实现。</span><span class="sxs-lookup"><span data-stu-id="f33a0-107">WMI is Microsoft's implementation of the Web-Based Enterprise Management (WBEM) standard.</span></span> <span data-ttu-id="f33a0-108">有关 WMI SDK 的详细信息，请参阅 [Windows Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page)。</span><span class="sxs-lookup"><span data-stu-id="f33a0-108">For more information about the WMI SDK, see [Windows Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page).</span></span> <span data-ttu-id="f33a0-109">WBEM 是有关应用程序如何向外部管理工具公开管理规范的行业标准。</span><span class="sxs-lookup"><span data-stu-id="f33a0-109">WBEM is an industry standard for how applications expose management instrumentation to external management tools.</span></span>  
  
 <span data-ttu-id="f33a0-110">WCF 实现一个 WMI 提供程序，该提供程序在运行时通过与 WBEM 兼容的接口公开检测。</span><span class="sxs-lookup"><span data-stu-id="f33a0-110">WCF implements a WMI provider, a component that exposes instrumentation at runtime through a WBEM-compatible interface.</span></span> <span data-ttu-id="f33a0-111">管理工具可以在运行时通过接口连接至服务。</span><span class="sxs-lookup"><span data-stu-id="f33a0-111">Management tools can connect to the services through the interface at runtime.</span></span> <span data-ttu-id="f33a0-112">WCF 公开服务的属性，如地址、绑定、行为和侦听器。</span><span class="sxs-lookup"><span data-stu-id="f33a0-112">WCF exposes attributes of services such as addresses, bindings, behaviors, and listeners.</span></span>  
  
 <span data-ttu-id="f33a0-113">在应用程序的配置文件中激活内置 WMI 提供程序。</span><span class="sxs-lookup"><span data-stu-id="f33a0-113">The built-in WMI provider is activated in the configuration file of the application.</span></span> <span data-ttu-id="f33a0-114">此操作通过 `wmiProviderEnabled` 部分中的属性完成 [\<diagnostics>](../../configure-apps/file-schema/wcf/diagnostics.md) [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) ，如下面的示例配置所示：</span><span class="sxs-lookup"><span data-stu-id="f33a0-114">This is done through the `wmiProviderEnabled` attribute of the [\<diagnostics>](../../configure-apps/file-schema/wcf/diagnostics.md) in the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) section, as shown in the following sample configuration:</span></span>  
  
```xml  
<system.serviceModel>  
    ...  
    <diagnostics wmiProviderEnabled="true" />  
    ...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="f33a0-115">此配置项公开 WMI 接口。</span><span class="sxs-lookup"><span data-stu-id="f33a0-115">This configuration entry exposes a WMI interface.</span></span> <span data-ttu-id="f33a0-116">现在，您可以通过此接口连接管理应用程序并访问应用程序的管理规范。</span><span class="sxs-lookup"><span data-stu-id="f33a0-116">Management applications can now connect through this interface and access the management instrumentation of the application.</span></span>  
  
## <a name="custom-wmi-object"></a><span data-ttu-id="f33a0-117">自定义 WMI 对象</span><span class="sxs-lookup"><span data-stu-id="f33a0-117">Custom WMI Object</span></span>  

 <span data-ttu-id="f33a0-118">将 WMI 对象添加到服务，可以显示用户定义的信息以及内置的 WMI 提供程序信息。</span><span class="sxs-lookup"><span data-stu-id="f33a0-118">Adding WMI objects to a service makes it possible to reveal user-defined information along with the built-in WMI provider information.</span></span> <span data-ttu-id="f33a0-119">这可以通过使用 Installutil.exe 应用程序将服务方案发布到 WMI 来实现。</span><span class="sxs-lookup"><span data-stu-id="f33a0-119">This is accomplished by publishing the schema of the service to WMI by using the Installutil.exe application.</span></span> <span data-ttu-id="f33a0-120">本主题末尾的安装说明介绍了如何实现上述操作的说明以及更详细的信息。</span><span class="sxs-lookup"><span data-stu-id="f33a0-120">Instructions to accomplish this, along with more details can be found in the setup instructions at the end of the topic.</span></span>  
  
## <a name="accessing-wmi-information"></a><span data-ttu-id="f33a0-121">访问 WMI 信息</span><span class="sxs-lookup"><span data-stu-id="f33a0-121">Accessing WMI Information</span></span>  

<span data-ttu-id="f33a0-122">可以采用多种不同方式访问 WMI 数据。</span><span class="sxs-lookup"><span data-stu-id="f33a0-122">WMI data can be accessed in many different ways.</span></span> <span data-ttu-id="f33a0-123">Microsoft 为脚本、Visual Basic 应用程序、c + + 应用程序和 .NET Framework 提供 WMI Api。</span><span class="sxs-lookup"><span data-stu-id="f33a0-123">Microsoft provides WMI APIs for scripts, Visual Basic applications, C++ applications, and the .NET Framework.</span></span> <span data-ttu-id="f33a0-124">有关详细信息，请参阅 [使用 WMI](/windows/desktop/wmisdk/using-wmi)。</span><span class="sxs-lookup"><span data-stu-id="f33a0-124">For more information, see [Using WMI](/windows/desktop/wmisdk/using-wmi).</span></span>
  
 <span data-ttu-id="f33a0-125">此示例使用两个 Java 脚本：一个脚本用于枚举在计算机上运行的服务及其某些属性，另一个脚本用于查看用户定义的 WMI 数据。</span><span class="sxs-lookup"><span data-stu-id="f33a0-125">This sample uses two Java scripts: one to enumerate services running on the computer along with some of their properties and the second to view user-defined WMI data.</span></span> <span data-ttu-id="f33a0-126">该脚本打开与 WMI 提供程序的连接、分析数据并显示所收集的数据。</span><span class="sxs-lookup"><span data-stu-id="f33a0-126">The script opens a connection to the WMI provider, parses data, and displays the data gathered.</span></span>  
  
 <span data-ttu-id="f33a0-127">启动示例以创建 WCF 服务的运行实例。</span><span class="sxs-lookup"><span data-stu-id="f33a0-127">Start the sample to create a running instance of a WCF service.</span></span> <span data-ttu-id="f33a0-128">在该服务运行的同时，在命令提示符处使用以下命令运行每个 Java 脚本：</span><span class="sxs-lookup"><span data-stu-id="f33a0-128">While the service is running, run each Java script by using the following command at the command prompt:</span></span>  
  
```console  
cscript EnumerateServices.js  
```  
  
 <span data-ttu-id="f33a0-129">该脚本访问服务中包含的规范，并生成下面的输出：</span><span class="sxs-lookup"><span data-stu-id="f33a0-129">The script accesses the instrumentation contained in the service and produces the following output:</span></span>  
  
```console  
Microsoft (R) Windows Script Host Version 5.6  
Copyright © Microsoft Corporation 1996-2001. All rights reserved.  
  
1 service(s) found.  
|-PID:           5776  
|-DistinguishedName:  CalculatorService@http://localhost/ServiceModelSamples/service.svc  
|-Endpoints:     1 endpoints  
  |-CalculatorService.ICalculator@http://localhost/ServiceModelSamples/service.svc  
    |-Address:                        http://localhost/ServiceModelSamples/service.svc  
    |-CounterInstanceName:  
    |-AddressHeaders:                 0  
    |-ContractType:                   Contract.Name='ICalculator'  
    |-BindingElements:                4 bindings  
      |-BindingElements[0]  
        |-Type:                       TransactionFlowBindingElement  
      |-BindingElements[1]  
        |-Type:                       SymmetricSecurityBindingElement  
      |-BindingElements[2]  
        |-Type:                       TextMessageEncodingBindingElement  
        |-MaxReadPoolSize:            64  
        |-MaxWritePoolSize:           16  
      |-BindingElements[3]  
        |-Type:                       HttpTransportBindingElement  
        |-ManualAddressing:           false  
        |-MaxBufferSize:              65536  
        |-AllowCookies:               false  
        |-AuthenticationScheme:       Anonymous  
        |-BypassProxyOnLocal:         false  
        |-HostNameComparisonMode:     StrongWildcard  
        |-ProxyAddress:               null  
        |-ProxyAuthenticationScheme:  Anonymous  
        |-Realm:  
        |-TransferMode:               Buffered  
        |-UseDefaultWebProxy:         true  
|-Behaviors:     5 behaviors  
      |-Behavior[0]  
      |-Type:                       ServiceBehaviorAttribute  
        |-AddressFilterMode:               Exact  
        |-AutomaticSessionShutdown:        true  
        |-ConcurrencyMode:                 Single  
        |-IncludeExceptionDetailInFaults:  false  
        |-InstanceContextMode:             PerSession  
        |-TransactionIsolationLevel:       Unspecified  
        |-TransactionTimeout:              null  
        |-ValidateMustUnderstand:          true  
      |-Behavior[1]  
      |-Type:                       AspNetCompatibilityRequirementsAttribute  
      |-Behavior[2]  
      |-Type:                       ServiceDebugBehavior  
      |-Behavior[3]  
      |-Type:                       ServiceAuthorizationBehavior  
      |-Behavior[4]  
      |-Type:                       Behavior  
```  
  
 <span data-ttu-id="f33a0-130">接下来，运行第二个 Java 脚本可以显示用户定义的 WMI 数据：</span><span class="sxs-lookup"><span data-stu-id="f33a0-130">Next, run the second Java Script to display the user-defined WMI data:</span></span>  
  
```console  
cscript EnumerateCustomObjects.js  
```  
  
 <span data-ttu-id="f33a0-131">该脚本访问服务中包含的用户定义的规范，并生成下面的输出：</span><span class="sxs-lookup"><span data-stu-id="f33a0-131">The script accesses the user-defined instrumentation contained in the services and produces the following output:</span></span>  
  
```console
1 WMIObject(s) found.  
|-PID:           30285bfd-9d66-4c4e-9be2-310499c5cef5  
|-InstanceId:    3839  
|-WMIInfo:       User Defined WMI Information.  
```  
  
 <span data-ttu-id="f33a0-132">该输出显示计算机上正在运行一个单一服务。</span><span class="sxs-lookup"><span data-stu-id="f33a0-132">The output shows that there is a single service running on the computer.</span></span> <span data-ttu-id="f33a0-133">该服务公开一个实现 `ICalculator` 协定的终结点。</span><span class="sxs-lookup"><span data-stu-id="f33a0-133">The service exposes one endpoint that implements the `ICalculator` contract.</span></span> <span data-ttu-id="f33a0-134">该终结点实现的行为和绑定的设置列作消息堆栈的各个元素的总和。</span><span class="sxs-lookup"><span data-stu-id="f33a0-134">The settings of the behavior and binding that are implemented by the endpoint are listed as the sum of individual elements of the messaging stack.</span></span>  
  
 <span data-ttu-id="f33a0-135">WMI 并不局限于公开 WCF 基础结构的管理规范。</span><span class="sxs-lookup"><span data-stu-id="f33a0-135">WMI is not limited to exposing the management instrumentation of the WCF infrastructure.</span></span> <span data-ttu-id="f33a0-136">该应用程序可以通过相同机制公开它自己的特定域数据项。</span><span class="sxs-lookup"><span data-stu-id="f33a0-136">The application can expose its own domain-specific data items through the same mechanism.</span></span> <span data-ttu-id="f33a0-137">WMI 是用于检查和控制 Web 服务的统一机制。</span><span class="sxs-lookup"><span data-stu-id="f33a0-137">WMI is a unified mechanism for inspection and control of a Web service.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f33a0-138">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="f33a0-138">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="f33a0-139">确保已对 [Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="f33a0-139">Ensure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="f33a0-140">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="f33a0-140">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="f33a0-141">通过在宿主目录中的 service.dll 文件上运行 InstallUtil.exe（InstallUtil.exe 的默认位置是“%WINDIR%\Microsoft.NET\Framework\v4.0.30319”），可以将服务方案发布到 WMI。</span><span class="sxs-lookup"><span data-stu-id="f33a0-141">Publish the services schema to WMI by running the InstallUtil.exe (the default locations for InstallUtil.exe is "%WINDIR%\Microsoft.NET\Framework\v4.0.30319") on the service.dll file in the hosting directory.</span></span> <span data-ttu-id="f33a0-142">只有在对 service.dll 文件进行了更改的情况下才需要执行此步骤。</span><span class="sxs-lookup"><span data-stu-id="f33a0-142">This step only needs to be executed when changes have been made to the service.dll file.</span></span>
  
4. <span data-ttu-id="f33a0-143">若要以单机配置或跨计算机配置来运行示例，请按照 [运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="f33a0-143">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="f33a0-144">如果在安装 ASP.NET 之后安装了 WCF，则可能需要运行 "% WINDIR% \Net\Framework\v3.0\Windows 通信 Foundation\servicemodelreg.exe "-r-x，为 ASPNET 帐户授予发布 WMI 对象的权限。</span><span class="sxs-lookup"><span data-stu-id="f33a0-144">If you installed WCF after installing ASP.NET, you may need to run "%WINDIR%\ Microsoft.Net\Framework\v3.0\Windows Communication Foundation\servicemodelreg.exe " -r -x to give the ASPNET account permission to publish WMI objects.</span></span>  
  
5. <span data-ttu-id="f33a0-145">使用下面的命令可以查看通过 WMI 显示的示例：`cscript EnumerateServices.js` 或 `cscript EnumerateCustomObjects.js`。</span><span class="sxs-lookup"><span data-stu-id="f33a0-145">View data from the sample surfaced through WMI by using the commands: `cscript EnumerateServices.js` or `cscript EnumerateCustomObjects.js`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f33a0-146">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="f33a0-146">The samples may already be installed on your computer.</span></span> <span data-ttu-id="f33a0-147">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="f33a0-147">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="f33a0-148">如果此目录不存在，请参阅[Windows Communication Foundation (wcf) ，并 Windows Workflow Foundation (的 WF](https://www.microsoft.com/download/details.aspx?id=21459)) .NET Framework Windows Communication Foundation ([!INCLUDE[wf1](../../../../includes/wf1-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f33a0-148">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f33a0-149">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="f33a0-149">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\WMIProvider`  
  
## <a name="see-also"></a><span data-ttu-id="f33a0-150">请参阅</span><span class="sxs-lookup"><span data-stu-id="f33a0-150">See also</span></span>

- <span data-ttu-id="f33a0-151">[AppFabric 监视示例](/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="f33a0-151">[AppFabric Monitoring Samples](/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
