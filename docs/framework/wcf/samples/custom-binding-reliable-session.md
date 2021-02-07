---
description: 了解详细信息：自定义绑定可靠会话
title: 自定义绑定可靠会话
ms.date: 03/30/2017
ms.assetid: c5fcd409-246f-4f3e-b3f1-629506ca4c04
ms.openlocfilehash: 0799e10c0fb86727bc21553584646031dc6f3606
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752504"
---
# <a name="custom-binding-reliable-session"></a><span data-ttu-id="eeaad-103">自定义绑定可靠会话</span><span class="sxs-lookup"><span data-stu-id="eeaad-103">Custom Binding Reliable Session</span></span>

<span data-ttu-id="eeaad-104">自定义绑定由离散绑定元素的有序列表定义。</span><span class="sxs-lookup"><span data-stu-id="eeaad-104">A custom binding is defined by an ordered list of discrete binding elements.</span></span> <span data-ttu-id="eeaad-105">本示例演示如何使用各种传输和消息编码元素配置自定义绑定，特别是启用可靠会话。</span><span class="sxs-lookup"><span data-stu-id="eeaad-105">This sample demonstrates how to configure a custom binding with various transport and message encoding elements, especially enabling reliable sessions.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="eeaad-106">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="eeaad-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="eeaad-107">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="eeaad-107">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="eeaad-108">如果此目录不存在，请参阅[Windows Communication Foundation (wcf) ，并 Windows Workflow Foundation (的 WF](https://www.microsoft.com/download/details.aspx?id=21459)) .NET Framework Windows Communication Foundation ([!INCLUDE[wf1](../../../../includes/wf1-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eeaad-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="eeaad-109">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="eeaad-109">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\ReliableSession`

## <a name="sample-details"></a><span data-ttu-id="eeaad-110">示例详细信息</span><span class="sxs-lookup"><span data-stu-id="eeaad-110">Sample Details</span></span>

<span data-ttu-id="eeaad-111">可靠会话提供可靠的消息和会话功能。</span><span class="sxs-lookup"><span data-stu-id="eeaad-111">Reliable sessions provide features for reliable messaging and sessions.</span></span> <span data-ttu-id="eeaad-112">可靠消息在失败时重新尝试通信并允许指定传递保证（如消息按顺序抵达）。</span><span class="sxs-lookup"><span data-stu-id="eeaad-112">Reliable messaging retries communication on failure and allows delivery assurances such as in-order arrival of messages to be specified.</span></span> <span data-ttu-id="eeaad-113">会话在调用之间将保持客户端的状态。</span><span class="sxs-lookup"><span data-stu-id="eeaad-113">Sessions maintain state for clients between calls.</span></span> <span data-ttu-id="eeaad-114">此示例实现了用来保持客户端状态的会话，并指定了按顺序传递保证。</span><span class="sxs-lookup"><span data-stu-id="eeaad-114">The sample implements sessions for maintaining client state and specifies in-order delivery assurances.</span></span> <span data-ttu-id="eeaad-115">该示例基于实现计算器服务的 [入门](getting-started-sample.md) 。</span><span class="sxs-lookup"><span data-stu-id="eeaad-115">The sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="eeaad-116">可靠会话功能是在客户端和服务的应用程序配置文件中启用和配置的。</span><span class="sxs-lookup"><span data-stu-id="eeaad-116">The reliable session features are enabled and configured in the application configuration files for the client and service.</span></span>

> [!NOTE]
> <span data-ttu-id="eeaad-117">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="eeaad-117">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="eeaad-118">在定义自定义绑定时，绑定元素的排序非常重要，因为每个元素都表示通道堆栈中的一个层 (请参阅 [自定义绑定](../extending/custom-bindings.md)) 。</span><span class="sxs-lookup"><span data-stu-id="eeaad-118">The ordering of binding elements is important in defining a custom binding, because each represents a layer in the channel stack (see [Custom Bindings](../extending/custom-bindings.md)).</span></span>

<span data-ttu-id="eeaad-119">示例的服务配置定义如下面的代码示例所示。</span><span class="sxs-lookup"><span data-stu-id="eeaad-119">The service configuration for the sample is defined as shown in the following code example.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"
          behaviorConfiguration="CalculatorServiceBehavior">
        <!-- This endpoint is exposed at the base address provided by host: http://localhost/servicemodelsamples/service.svc  -->
        <!-- specify customBinding binding and a binding configuration to use -->
        <endpoint address=""
                  binding="customBinding"
                  bindingConfiguration="Binding1"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- The mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>

    <!-- custom binding configuration - configures HTTP transport, reliable sessions -->
    <bindings>
      <customBinding>
        <binding name="Binding1">
          <reliableSession />
          <security authenticationMode="SecureConversation"
                     requireSecurityContextCancellation="true">
          </security>
          <compositeDuplex />
          <oneWay />
          <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8" />
          <httpTransport authenticationScheme="Anonymous" bypassProxyOnLocal="false"
                        hostNameComparisonMode="StrongWildcard"
                        proxyAuthenticationScheme="Anonymous" realm=""
                        useDefaultWebProxy="true" />
        </binding>
      </customBinding>
    </bindings>

    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata httpGetEnabled="True"/>
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>

  </system.serviceModel>

</configuration>
```

<span data-ttu-id="eeaad-120">在跨计算机方案中运行时，必须更改客户端的终结点地址以反映服务的主机名。</span><span class="sxs-lookup"><span data-stu-id="eeaad-120">When running in a cross-machine scenario, you must change client's endpoint address to reflect the host name of the service.</span></span>

<span data-ttu-id="eeaad-121">运行示例时，操作请求和响应将显示在客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="eeaad-121">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="eeaad-122">在客户端窗口中按 Enter 可以关闭客户端。</span><span class="sxs-lookup"><span data-stu-id="eeaad-122">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="eeaad-123">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="eeaad-123">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="eeaad-124">使用以下命令安装 ASP.NET 4.0：</span><span class="sxs-lookup"><span data-stu-id="eeaad-124">Install ASP.NET 4.0 using the following command:</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="eeaad-125">确保已对 [Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="eeaad-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="eeaad-126">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="eeaad-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="eeaad-127">若要以单机配置或跨计算机配置来运行示例，请按照 [运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="eeaad-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="eeaad-128">在跨计算机配置中运行客户端时，请确保 `address` [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) 使用相应计算机的名称替换元素的属性和的属性中的 "localhost" `clientBaseAddress` [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) ，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="eeaad-128">When running the client in a cross-machine configuration, be sure to replace "localhost" in both the `address` attribute of the [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) element and the `clientBaseAddress` attribute of the [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) with the name of the appropriate machine, as shown in the following example.</span></span>

    ```xml
    <endpoint name = ""
    address="http://service_machine_name/servicemodelsamples/service.svc" />
    <compositeDuplex clientBaseAddress="http://client_machine_name:8000/myClient/" />
    ```
