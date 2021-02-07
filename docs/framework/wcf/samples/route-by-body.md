---
description: 了解详细信息：按正文路由
title: 按正文路由
ms.date: 03/30/2017
ms.assetid: 07a6fc3b-c360-42e0-b663-3d0f22cf4502
ms.openlocfilehash: 1c9505484c4af34c5e1f2f98524c01fb378c005f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99703778"
---
# <a name="route-by-body"></a><span data-ttu-id="fbb37-103">按正文路由</span><span class="sxs-lookup"><span data-stu-id="fbb37-103">Route by Body</span></span>

<span data-ttu-id="fbb37-104">此示例演示如何实现一种使用任何 SOAP 操作接受消息对象的服务。</span><span class="sxs-lookup"><span data-stu-id="fbb37-104">This sample demonstrates how to implement a service that accepts message objects with any SOAP action.</span></span> <span data-ttu-id="fbb37-105">此示例基于实现计算器服务的 [入门](getting-started-sample.md) 。</span><span class="sxs-lookup"><span data-stu-id="fbb37-105">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="fbb37-106">该服务实现一个 `Calculate` 操作，此操作接受一个 <xref:System.ServiceModel.Channels.Message> 请求参数并返回一个 <xref:System.ServiceModel.Channels.Message> 响应。</span><span class="sxs-lookup"><span data-stu-id="fbb37-106">The service implements a single `Calculate` operation that accepts a <xref:System.ServiceModel.Channels.Message> request parameter and returns a <xref:System.ServiceModel.Channels.Message> response.</span></span>  
  
 <span data-ttu-id="fbb37-107">在此示例中，客户端是一个控制台应用程序 (.exe)，并且服务承载在 IIS 中。</span><span class="sxs-lookup"><span data-stu-id="fbb37-107">In this sample, the client is a console application (.exe) and the service is hosted in IIS.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fbb37-108">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="fbb37-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="fbb37-109">此示例演示基于正文内容的消息调度。</span><span class="sxs-lookup"><span data-stu-id="fbb37-109">The sample demonstrates message dispatch based on the body content.</span></span> <span data-ttu-id="fbb37-110">内置 Windows Communication Foundation (WCF) 服务模型消息调度机制基于消息操作。</span><span class="sxs-lookup"><span data-stu-id="fbb37-110">The built-in Windows Communication Foundation (WCF) service model message dispatch mechanism is based on message Actions.</span></span> <span data-ttu-id="fbb37-111">不过，有许多现有的 Web 服务使用 Action="" 来定义其所有操作。</span><span class="sxs-lookup"><span data-stu-id="fbb37-111">However, there are many existing Web services that define all of their operations with Action="".</span></span> <span data-ttu-id="fbb37-112">不可能基于 WSDL 生成基于 Action 信息调度请求消息的服务。</span><span class="sxs-lookup"><span data-stu-id="fbb37-112">It is impossible to build a service based on WSDL that keeps dispatching request messages based on Action information.</span></span> <span data-ttu-id="fbb37-113">此示例演示一个基于 WSDL 的服务协定，此 WSDL 包含在该示例包括的 Service.wsdl 中。</span><span class="sxs-lookup"><span data-stu-id="fbb37-113">This sample demonstrates a service contract that is based on WSDL (the WSDL is contained in Service.wsdl that is included with the sample).</span></span> <span data-ttu-id="fbb37-114">服务协定是计算器，类似于 [入门](getting-started-sample.md)中使用的协定。</span><span class="sxs-lookup"><span data-stu-id="fbb37-114">The service contract is Calculator, similar to the one used in [Getting Started](getting-started-sample.md).</span></span> <span data-ttu-id="fbb37-115">但是，`[OperationContract]` 指定所有操作的 `Action=""`。</span><span class="sxs-lookup"><span data-stu-id="fbb37-115">However the `[OperationContract]` specifies `Action=""` for all operations.</span></span>  
  
```csharp  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples"),
                 XmlSerializerFormat, DispatchByBodyBehavior]  
    public interface ICalculator  
    {  
        [OperationContract(Action="")]  
        double Add(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Subtract(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Multiply(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Divide(double n1, double n2);  
    }  
```  
  
 <span data-ttu-id="fbb37-116">给定协定之后，服务需要自定义调度行为 `DispatchByBodyBehavior` 以便允许在操作之间调度消息。</span><span class="sxs-lookup"><span data-stu-id="fbb37-116">Given a contract, a service requires custom dispatch behavior `DispatchByBodyBehavior` to allow messages to be dispatched between operations.</span></span> <span data-ttu-id="fbb37-117">此调度行为 `DispatchByBodyElementOperationSelector` 使用由各自包装元素的 QName 进行键控的操作名称表初始化自定义操作选择器。</span><span class="sxs-lookup"><span data-stu-id="fbb37-117">This dispatch behavior initializes the `DispatchByBodyElementOperationSelector` custom operation selector with a table of the operation names keyed by QName of respective wrapper elements.</span></span> <span data-ttu-id="fbb37-118">`DispatchByBodyElementOperationSelector` 在正文第一个子级的开始标记中查找，并使用前面提到的表选择操作。</span><span class="sxs-lookup"><span data-stu-id="fbb37-118">`DispatchByBodyElementOperationSelector` looks at the start tag of the first child of the Body and selects the operation using the table previously mentioned.</span></span>  
  
 <span data-ttu-id="fbb37-119">客户端使用由服务导出的 WSDL 自动生成的代理，使用 " [)  ( ](../servicemodel-metadata-utility-tool-svcutil-exe.md)</span><span class="sxs-lookup"><span data-stu-id="fbb37-119">The client uses a proxy auto-generated from the WSDL exported by the service using [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
```console  
svcutil.exe  /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples /uxs http://localhost/servicemodelsamples/service.svc?wsdl /out:generatedProxy.cs  
```  
  
 <span data-ttu-id="fbb37-120">所有操作的此 Action 均为空，这一事实对客户端节点没有影响，但自动生成的代理中的 Action 参数除外。</span><span class="sxs-lookup"><span data-stu-id="fbb37-120">The fact that actions of all operations are empty has no impact on the client code, except for the Action parameters in the auto-generated proxy.</span></span>  
  
 <span data-ttu-id="fbb37-121">客户端代码执行若干计算。</span><span class="sxs-lookup"><span data-stu-id="fbb37-121">The client code performs several calculations.</span></span> <span data-ttu-id="fbb37-122">运行示例时，操作请求和响应将显示在客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="fbb37-122">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="fbb37-123">在客户端窗口中按 Enter 可以关闭客户端。</span><span class="sxs-lookup"><span data-stu-id="fbb37-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```console
Add(100, 15.99) = 115.99  
Subtract(145, 76.54) = 68.46  
Multiply(9, 81.25) = 731.25  
Divide(22, 7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="fbb37-124">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="fbb37-124">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="fbb37-125">确保已对 [Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="fbb37-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="fbb37-126">若要生成解决方案，请按照 [生成 Windows Communication Foundation 示例](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="fbb37-126">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="fbb37-127">若要以单机配置或跨计算机配置来运行示例，请按照 [运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="fbb37-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="fbb37-128">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="fbb37-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fbb37-129">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="fbb37-129">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="fbb37-130">如果此目录不存在，请参阅[Windows Communication Foundation (wcf) ，并 Windows Workflow Foundation (的 WF](https://www.microsoft.com/download/details.aspx?id=21459)) .NET Framework Windows Communication Foundation ([!INCLUDE[wf1](../../../../includes/wf1-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbb37-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fbb37-131">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="fbb37-131">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\RouteByBody`  
