---
description: 了解详细信息：多个终结点
title: 多终结点
ms.date: 03/30/2017
helpviewer_keywords:
- Multiple EndPoints
ms.assetid: 8f0c2e1f-9aee-41c2-8301-c72b7f664412
ms.openlocfilehash: f11110cdc53c6e9a8abc876f0304b144a2d82964
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752197"
---
# <a name="multiple-endpoints"></a><span data-ttu-id="b1f8b-103">多终结点</span><span class="sxs-lookup"><span data-stu-id="b1f8b-103">Multiple Endpoints</span></span>

<span data-ttu-id="b1f8b-104">此多终结点示例演示如何在服务上配置多个终结点，以及如何从客户端与每个终结点通信。</span><span class="sxs-lookup"><span data-stu-id="b1f8b-104">The Multiple Endpoints sample demonstrates how to configure multiple endpoints on a service and how to communicate with each endpoint from a client.</span></span> <span data-ttu-id="b1f8b-105">此示例基于 [入门](getting-started-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="b1f8b-105">This sample is based on the [Getting Started](getting-started-sample.md).</span></span> <span data-ttu-id="b1f8b-106">已经对服务配置进行了修改以定义两个支持 `ICalculator` 协定的终结点，但是这两个终结点位于使用不同绑定的不同地址。</span><span class="sxs-lookup"><span data-stu-id="b1f8b-106">The service configuration has been modified to define two endpoints that support the `ICalculator` contract, but each at a different address using a different binding.</span></span> <span data-ttu-id="b1f8b-107">已经对客户端配置和代码进行了修改，以便与这两个服务终结点均进行通信。</span><span class="sxs-lookup"><span data-stu-id="b1f8b-107">The client configuration and code have been modified to communicate with both of the service endpoints.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b1f8b-108">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="b1f8b-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="b1f8b-109">已经对服务的 Web.config 文件进行了修改以定义两个终结点，这两个终结点支持同一个 `ICalculator` 协定，但是位于使用不同绑定的不同地址。</span><span class="sxs-lookup"><span data-stu-id="b1f8b-109">The service Web.config file has been modified to define two endpoints, each supporting the same `ICalculator` contract, but at different addresses using different bindings.</span></span> <span data-ttu-id="b1f8b-110">第一个终结点是在基址中使用 `basicHttpBinding` 绑定定义的，该绑定未启用安全性。</span><span class="sxs-lookup"><span data-stu-id="b1f8b-110">The first endpoint is defined at the base address using a `basicHttpBinding` binding, which does not have security enabled.</span></span> <span data-ttu-id="b1f8b-111">第二个终结点是在 {baseaddress}/secure 中使用 `wsHttpBinding` 绑定定义的，默认情况下结合使用 WS-Security 和 Windows 身份验证来确保该绑定的安全。</span><span class="sxs-lookup"><span data-stu-id="b1f8b-111">The second endpoint is defined at {baseaddress}/secure using a `wsHttpBinding` binding, which is secure by default, using WS-Security with Windows authentication.</span></span>  
  
```xml  
<service
    name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">  
  <!-- This endpoint is exposed at the base address provided by host:  
       http://localhost/servicemodelsamples/service.svc  -->  
  <endpoint address=""  
            binding="basicHttpBinding"  
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  <!-- secure endpoint exposed at {base address}/secure:  
       http://localhost/servicemodelsamples/service.svc/secure -->  
  <endpoint address="secure"  
            binding="wsHttpBinding"  
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  ...  
</service>  
```  
  
 <span data-ttu-id="b1f8b-112">这两个终结点也都在客户端上进行了配置。</span><span class="sxs-lookup"><span data-stu-id="b1f8b-112">Both endpoints are also configured on the client.</span></span> <span data-ttu-id="b1f8b-113">这些终结点的命名方法允许调用方将所需的终结点名称传递到客户端的构造函数。</span><span class="sxs-lookup"><span data-stu-id="b1f8b-113">These endpoints are given names so that the caller can pass the desired endpoint name into the constructor of the client.</span></span>  
  
```xml  
<client>  
  <!-- Passing "basic" into the constructor of the CalculatorClient  
       class selects this endpoint.-->  
  <endpoint name="basic"  
            address="http://localhost/servicemodelsamples/service.svc"
            binding="basicHttpBinding"
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  <!-- Passing "secure" into the constructor of the CalculatorClient  
       class selects this endpoint.-->  
  <endpoint name="secure"  
            address="http://localhost/servicemodelsamples/service.svc/secure"
            binding="wsHttpBinding"
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
</client>  
```  
  
 <span data-ttu-id="b1f8b-114">客户端同时使用这两个终结点，如下面的代码中所示。</span><span class="sxs-lookup"><span data-stu-id="b1f8b-114">The client uses both endpoints as shown in the following code.</span></span>  
  
```csharp  
static void Main()  
{  
    // Create a client to the basic endpoint configuration.  
    CalculatorClient client = new CalculatorClient("basic");  
    Console.WriteLine("Communicate with basic endpoint.");  
    // call operations  
    DoCalculations(client);  
  
    // Close the client and release resources.  
    client.Close();  
  
    // Create a client to the secure endpoint configuration.  
    client = new CalculatorClient("secure");  
    Console.WriteLine("Communicate with secure endpoint.");  
    // Call operations.  
    DoCalculations(client);  
  
    // Close the client and release resources.  
    client.Close();  
  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
}  
```  
  
 <span data-ttu-id="b1f8b-115">运行客户端时，将显示与这两个终结点的交互结果。</span><span class="sxs-lookup"><span data-stu-id="b1f8b-115">When you run the client, interactions with both endpoints are displayed.</span></span>  
  
```console
Communicate with basic endpoint.  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Communicate with secure endpoint.  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b1f8b-116">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="b1f8b-116">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="b1f8b-117">确保已对 [Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="b1f8b-117">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="b1f8b-118">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="b1f8b-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="b1f8b-119">若要以单机配置或跨计算机配置来运行示例，请按照 [运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="b1f8b-119">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b1f8b-120">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="b1f8b-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b1f8b-121">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="b1f8b-121">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="b1f8b-122">如果此目录不存在，请参阅[Windows Communication Foundation (wcf) ，并 Windows Workflow Foundation (的 WF](https://www.microsoft.com/download/details.aspx?id=21459)) .NET Framework Windows Communication Foundation ([!INCLUDE[wf1](../../../../includes/wf1-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1f8b-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b1f8b-123">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="b1f8b-123">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleEndpoints`  
