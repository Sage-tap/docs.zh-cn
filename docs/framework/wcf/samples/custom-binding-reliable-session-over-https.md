---
description: 了解详细信息：通过 HTTPS 自定义绑定可靠会话
title: 基于 HTTPS 的自定义绑定可靠会话
ms.date: 03/30/2017
ms.assetid: 16aaa80d-3ffe-47c4-8b16-ec65c4d25f8d
ms.openlocfilehash: ed02ce8ea199b5e7ae744fb0eacf168ea5fa85df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778290"
---
# <a name="custom-binding-reliable-session-over-https"></a><span data-ttu-id="2605a-103">基于 HTTPS 的自定义绑定可靠会话</span><span class="sxs-lookup"><span data-stu-id="2605a-103">Custom Binding Reliable Session over HTTPS</span></span>

<span data-ttu-id="2605a-104">此示例演示对可靠会话使用 SSL 传输安全。</span><span class="sxs-lookup"><span data-stu-id="2605a-104">This sample demonstrates the use of SSL transport security with Reliable Sessions.</span></span> <span data-ttu-id="2605a-105">可靠会话实现 WS-Reliable Messaging 协议。</span><span class="sxs-lookup"><span data-stu-id="2605a-105">Reliable Sessions implements the WS-Reliable Messaging protocol.</span></span> <span data-ttu-id="2605a-106">您可以通过在可靠会话上组合 WS-Security 来获得安全的可靠会话。</span><span class="sxs-lookup"><span data-stu-id="2605a-106">You can have a secure reliable session by composing WS-Security over Reliable Sessions.</span></span> <span data-ttu-id="2605a-107">但是有时候，您可以选择对 SSL 改用 HTTP 传输安全。</span><span class="sxs-lookup"><span data-stu-id="2605a-107">But sometimes, you may choose to instead use HTTP transport security with SSL.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2605a-108">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="2605a-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2605a-109">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="2605a-109">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="2605a-110">如果此目录不存在，请参阅[Windows Communication Foundation (wcf) ，并 Windows Workflow Foundation (的 WF](https://www.microsoft.com/download/details.aspx?id=21459)) .NET Framework Windows Communication Foundation ([!INCLUDE[wf1](../../../../includes/wf1-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2605a-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2605a-111">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="2605a-111">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\ReliableSessionOverHttps`  
  
## <a name="sample-details"></a><span data-ttu-id="2605a-112">示例详细信息</span><span class="sxs-lookup"><span data-stu-id="2605a-112">Sample Details</span></span>  

 <span data-ttu-id="2605a-113">SSL 可以确保数据包本身是安全的。</span><span class="sxs-lookup"><span data-stu-id="2605a-113">SSL ensures that the packets themselves are secured.</span></span> <span data-ttu-id="2605a-114">值得注意的是，这与使用 WS-Secure Conversation 确保可靠会话的安全是不同的。</span><span class="sxs-lookup"><span data-stu-id="2605a-114">It is important to note that this is different from securing the reliable session using WS-Secure Conversation.</span></span>  
  
 <span data-ttu-id="2605a-115">若要使用基于 HTTPS 的可靠会话，必须创建自定义绑定。</span><span class="sxs-lookup"><span data-stu-id="2605a-115">To use reliable session over HTTPS, you must create a custom binding.</span></span> <span data-ttu-id="2605a-116">此示例基于实现计算器服务的 [入门](getting-started-sample.md) 。</span><span class="sxs-lookup"><span data-stu-id="2605a-116">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="2605a-117">使用可靠会话绑定元素和创建自定义绑定 [\<httpsTransport>](../../configure-apps/file-schema/wcf/httpstransport.md) 。</span><span class="sxs-lookup"><span data-stu-id="2605a-117">A custom binding is created using the reliable session binding element and the [\<httpsTransport>](../../configure-apps/file-schema/wcf/httpstransport.md).</span></span> <span data-ttu-id="2605a-118">下面是自定义绑定的配置。</span><span class="sxs-lookup"><span data-stu-id="2605a-118">The following configuration is of the custom binding.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- use base address provided by host -->  
        <endpoint address=""  
                  binding="customBinding"  
                  bindingConfiguration="reliableSessionOverHttps"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is exposed as http://localhost/servicemodelsamples/service.svc/mex-->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange"/>  
      </service>  
    </services>  
  
    <bindings>  
      <customBinding>  
        <binding name="reliableSessionOverHttps">  
          <reliableSession />  
          <httpsTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="true" />  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
  
</configuration>  
```  
  
 <span data-ttu-id="2605a-119">示例中的程序代码与 [入门](getting-started-sample.md) 服务的程序代码相同。</span><span class="sxs-lookup"><span data-stu-id="2605a-119">The program code in the sample is identical to that of the [Getting Started](getting-started-sample.md) service.</span></span> <span data-ttu-id="2605a-120">必须在生成和运行示例之前使用 Web 服务器证书向导创建证书并分配此证书。</span><span class="sxs-lookup"><span data-stu-id="2605a-120">You must create a certificate and assign it by using the Web Server Certificate Wizard before building and running the sample.</span></span> <span data-ttu-id="2605a-121">配置文件设置中的终结点定义和绑定定义允许使用自定义绑定，如下面的客户端示例配置所示。</span><span class="sxs-lookup"><span data-stu-id="2605a-121">The endpoint definition and binding definition in the configuration file settings enable the use of custom binding as shown in the following sample configuration for the client.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
  
    <client>  
      <!-- this endpoint has an https: address -->  
      <endpoint name=""  
                address="https://localhost/servicemodelsamples/service.svc"
                binding="customBinding"
                bindingConfiguration="reliableSessionOverHttps"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </client>  
  
      <bindings>  
        <customBinding>  
          <binding name="reliableSessionOverHttps">  
            <reliableSession />  
            <httpsTransport />  
          </binding>  
        </customBinding>
    </bindings>  
  
  </system.serviceModel>  
  
</configuration>  
```  
  
 <span data-ttu-id="2605a-122">指定的地址使用 `https://` 方案。</span><span class="sxs-lookup"><span data-stu-id="2605a-122">The address specified uses the `https://` scheme.</span></span>  
  
 <span data-ttu-id="2605a-123">由于本示例中使用的证书是使用 Makecert.exe 创建的测试证书，因此当你尝试从浏览器访问 https：地址（如）时，将出现安全警报 `https://localhost/servicemodelsamples/service.svc` 。</span><span class="sxs-lookup"><span data-stu-id="2605a-123">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert appears when you try to access an https: address, such as `https://localhost/servicemodelsamples/service.svc`, from your browser.</span></span> <span data-ttu-id="2605a-124">为了允许 Windows Communication Foundation (WCF) 客户端使用测试证书，已向客户端添加了一些附加代码以禁止显示安全警报。</span><span class="sxs-lookup"><span data-stu-id="2605a-124">To allow the Windows Communication Foundation (WCF) client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="2605a-125">使用生产证书时，不需要此代码和随附的类。</span><span class="sxs-lookup"><span data-stu-id="2605a-125">This code, and the accompanying class, is not required when using production certificates.</span></span>  

```csharp
// This code is required only for test certificates like those created by Makecert.exe.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```

 <span data-ttu-id="2605a-126">运行示例时，操作请求和响应将显示在客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="2605a-126">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="2605a-127">在客户端窗口中按 Enter 可以关闭客户端。</span><span class="sxs-lookup"><span data-stu-id="2605a-127">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2605a-128">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="2605a-128">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="2605a-129">使用以下命令安装 ASP.NET 4.0。</span><span class="sxs-lookup"><span data-stu-id="2605a-129">Install  ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="2605a-130">确保已对 [Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="2605a-130">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="2605a-131">请确保已执行 [Internet Information Services (IIS) 服务器证书安装说明](iis-server-certificate-installation-instructions.md)。</span><span class="sxs-lookup"><span data-stu-id="2605a-131">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](iis-server-certificate-installation-instructions.md).</span></span>  
  
4. <span data-ttu-id="2605a-132">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="2605a-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
5. <span data-ttu-id="2605a-133">若要以单机配置或跨计算机配置来运行示例，请按照 [运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="2605a-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
