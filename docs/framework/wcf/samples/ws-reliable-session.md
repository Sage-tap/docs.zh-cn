---
description: 了解有关以下内容的详细信息： WS 可靠会话
title: WS 可靠会话
ms.date: 03/30/2017
helpviewer_keywords:
- Reliable session
ms.assetid: 86e914f2-060b-432b-bd17-333695317745
ms.openlocfilehash: a8ccdefd3ef585e3ae164246d69e5cc004390728
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99714945"
---
# <a name="ws-reliable-session"></a><span data-ttu-id="a8226-103">WS 可靠会话</span><span class="sxs-lookup"><span data-stu-id="a8226-103">WS Reliable Session</span></span>

<span data-ttu-id="a8226-104">此示例演示可靠会话的用法。</span><span class="sxs-lookup"><span data-stu-id="a8226-104">This sample demonstrates the use of reliable sessions.</span></span> <span data-ttu-id="a8226-105">可靠会话为可靠消息传递和会话提供支持。</span><span class="sxs-lookup"><span data-stu-id="a8226-105">Reliable sessions provide support for reliable messaging and sessions.</span></span> <span data-ttu-id="a8226-106">可靠消息传递在失败时会重新尝试通信，并允许指定传递保证（如消息按顺序抵达）。</span><span class="sxs-lookup"><span data-stu-id="a8226-106">Reliable messaging retries communication on failure and allows delivery assurances to be specified, such as in-order arrival of messages.</span></span> <span data-ttu-id="a8226-107">会话在调用之间将保持客户端的状态。</span><span class="sxs-lookup"><span data-stu-id="a8226-107">Sessions maintain state for clients between calls.</span></span> <span data-ttu-id="a8226-108">此示例实现了用来保持客户端状态的会话，并指定了按顺序传递保证。</span><span class="sxs-lookup"><span data-stu-id="a8226-108">The sample implements sessions for maintaining client state and specifies in-order delivery assurances.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a8226-109">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="a8226-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a8226-110">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="a8226-110">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="a8226-111">如果此目录不存在，请参阅[Windows Communication Foundation (wcf) ，并 Windows Workflow Foundation (的 WF](https://www.microsoft.com/download/details.aspx?id=21459)) .NET Framework Windows Communication Foundation ([!INCLUDE[wf1](../../../../includes/wf1-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8226-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a8226-112">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="a8226-112">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsReliableSession`  
  
 <span data-ttu-id="a8226-113">此示例基于实现计算器服务的 [入门](getting-started-sample.md) 。</span><span class="sxs-lookup"><span data-stu-id="a8226-113">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="a8226-114">可靠会话功能是在客户端和服务的应用程序配置文件中启用和配置的。</span><span class="sxs-lookup"><span data-stu-id="a8226-114">The reliable session features are enabled and configured in the application configuration files for the client and service.</span></span>  
  
 <span data-ttu-id="a8226-115">在此示例中，服务由 Internet 信息服务 (IIS) 承载，客户端是一个控制台应用程序 (.exe)。</span><span class="sxs-lookup"><span data-stu-id="a8226-115">In this sample, the service is hosted in Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a8226-116">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="a8226-116">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="a8226-117">此示例使用 `wsHttpBinding`。</span><span class="sxs-lookup"><span data-stu-id="a8226-117">The sample uses the `wsHttpBinding`.</span></span> <span data-ttu-id="a8226-118">绑定是在客户端和服务的配置文件中指定的。</span><span class="sxs-lookup"><span data-stu-id="a8226-118">The binding is specified in the configuration files for both the client and service.</span></span> <span data-ttu-id="a8226-119">绑定类型是在终结点元素的 `binding` 属性中指定的，如下面的示例配置中所示。</span><span class="sxs-lookup"><span data-stu-id="a8226-119">The binding type is specified in the endpoint element’s `binding` attribute as shown in the following sample configuration.</span></span>  
  
```xml  
<endpoint address=""  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="a8226-120">终结点包含一个 `bindingConfiguration` 属性，该属性引用一个名为“Binding1”的绑定配置。</span><span class="sxs-lookup"><span data-stu-id="a8226-120">The endpoint contains a `bindingConfiguration` attribute that references a binding configuration named "Binding1."</span></span> <span data-ttu-id="a8226-121">绑定配置通过将 `enabled` 的属性设置为来启用可靠会话 [\<reliableSession>](../../configure-apps/file-schema/wcf/reliablesession.md) `true` 。</span><span class="sxs-lookup"><span data-stu-id="a8226-121">The binding configuration enables reliable sessions by setting the `enabled` attribute of the [\<reliableSession>](../../configure-apps/file-schema/wcf/reliablesession.md) to `true`.</span></span> <span data-ttu-id="a8226-122">有序会话的传递保证是通过将有序属性设置为 `true` 或 `false` 来控制的。</span><span class="sxs-lookup"><span data-stu-id="a8226-122">Delivery assurances for ordered sessions are controlled by setting the ordered attribute to `true` or `false`.</span></span> <span data-ttu-id="a8226-123">默认值为 `true`。</span><span class="sxs-lookup"><span data-stu-id="a8226-123">The default is `true`.</span></span>  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding name="Binding1">  
            <reliableSession enabled="true" />  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="a8226-124">服务实现类将实现 <xref:System.ServiceModel.InstanceContextMode.PerSession> 实例化，以便针对每个客户端维护一个单独的类实例，如下面的示例代码中所示。</span><span class="sxs-lookup"><span data-stu-id="a8226-124">The service implementation class implements <xref:System.ServiceModel.InstanceContextMode.PerSession> instancing to maintain a separate class instance for each client, as shown in the following sample code.</span></span>  

```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)] public class CalculatorService : ICalculator  
{  
    ...  
}  
```
  
 <span data-ttu-id="a8226-125">运行示例时，操作请求和响应将显示在客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="a8226-125">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="a8226-126">在客户端窗口中按 Enter 可以关闭客户端。</span><span class="sxs-lookup"><span data-stu-id="a8226-126">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a8226-127">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="a8226-127">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="a8226-128">使用以下命令安装 ASP.NET 4.0。</span><span class="sxs-lookup"><span data-stu-id="a8226-128">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="a8226-129">确保已对 [Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="a8226-129">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="a8226-130">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="a8226-130">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="a8226-131">若要以单机配置或跨计算机配置来运行示例，请按照 [运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="a8226-131">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
