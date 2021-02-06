---
description: 了解详细信息：默认消息协定
title: 默认消息协定
ms.date: 03/30/2017
helpviewer_keywords:
- Message Contract
ms.assetid: 5a200b78-1a46-4104-b7fb-da6dbab33893
ms.openlocfilehash: 3587f6ce81e085a4915af8162f8d76aed30bf8df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99632082"
---
# <a name="default-message-contract"></a><span data-ttu-id="17b13-103">默认消息协定</span><span class="sxs-lookup"><span data-stu-id="17b13-103">Default Message Contract</span></span>

<span data-ttu-id="17b13-104">默认消息协定示例演示了一个服务，在该服务中，用户定义的自定义消息会在服务操作来回传递。</span><span class="sxs-lookup"><span data-stu-id="17b13-104">The Default Message Contract sample demonstrates a service where a custom user-defined message is passed to and from service operations.</span></span> <span data-ttu-id="17b13-105">此示例基于将计算器接口实现为类型化服务的 [入门](getting-started-sample.md) 。</span><span class="sxs-lookup"><span data-stu-id="17b13-105">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator interface as a typed service.</span></span> <span data-ttu-id="17b13-106">此示例不是 [入门](getting-started-sample.md)中使用的加法、减法、乘法和除法的单个服务操作，而是传递包含操作数和运算符的自定义消息，并返回算术计算的结果。</span><span class="sxs-lookup"><span data-stu-id="17b13-106">Instead of the individual service operations for addition, subtraction, multiplication, and division used in the [Getting Started](getting-started-sample.md), this sample passes a custom message that contains both the operands and the operator, and returns the result of the arithmetic calculation.</span></span>  
  
 <span data-ttu-id="17b13-107">客户端是一种控制台程序 (.exe)，服务库 (.dll) 是由 Internet 信息服务 (IIS) 承载的。</span><span class="sxs-lookup"><span data-stu-id="17b13-107">The client is a console program (.exe) and the service library (.dll) is hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="17b13-108">客户端活动显示在控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="17b13-108">Client activity is visible in the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="17b13-109">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="17b13-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="17b13-110">在服务中，定义了单个服务操作，该操作接受和返回 `MyMessage` 类型的自定义消息。</span><span class="sxs-lookup"><span data-stu-id="17b13-110">In the service, a single service operation is defined that accepts and returns custom messages of type `MyMessage`.</span></span> <span data-ttu-id="17b13-111">在该示例中，尽管请求消息和响应消息属于同一种类型，但必要时当然也可以属于不同的消息协定。</span><span class="sxs-lookup"><span data-stu-id="17b13-111">Although in this sample the request and response messages are of the same type, they could of course be different message contracts if necessary.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract(Action="http://test/MyMessage_action",  
                  ReplyAction="http://test/MyMessage_action")]  
    MyMessage Calculate(MyMessage request);  
}  
```  
  
 <span data-ttu-id="17b13-112">自定义消息 `MyMessage` 是在用 <xref:System.ServiceModel.MessageContractAttribute>、<xref:System.ServiceModel.MessageHeaderAttribute> 和 <xref:System.ServiceModel.MessageBodyMemberAttribute> 属性进行批注的类中定义的。</span><span class="sxs-lookup"><span data-stu-id="17b13-112">The custom message `MyMessage` is defined in a class annotated with <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes.</span></span> <span data-ttu-id="17b13-113">本示例中只使用第三个构造函数。</span><span class="sxs-lookup"><span data-stu-id="17b13-113">Only the third constructor is used in this sample.</span></span> <span data-ttu-id="17b13-114">使用消息协定，您可以对 SOAP 消息进行完全控制。</span><span class="sxs-lookup"><span data-stu-id="17b13-114">Using message contracts allows you to exercise full control over the SOAP message.</span></span> <span data-ttu-id="17b13-115">在本示例中，<xref:System.ServiceModel.MessageHeaderAttribute> 属性用来将 `Operation` 放在 SOAP 头中。</span><span class="sxs-lookup"><span data-stu-id="17b13-115">In this sample, the <xref:System.ServiceModel.MessageHeaderAttribute> attribute is used to put `Operation` in a SOAP header.</span></span> <span data-ttu-id="17b13-116">操作数 `N1` 和 `N2` 以及 `Result` 出现在 SOAP 正文中，因为它们应用了 <xref:System.ServiceModel.MessageBodyMemberAttribute> 属性。</span><span class="sxs-lookup"><span data-stu-id="17b13-116">The operands `N1`, `N2` and the `Result` appear within the SOAP body because they have the <xref:System.ServiceModel.MessageBodyMemberAttribute> attribute applied.</span></span>  
  
```csharp
[MessageContract]  
public class MyMessage  
{  
    private string operation;  
    private double n1;  
    private double n2;  
    private double result;  
  
    //Constructor - create an empty message.  
  
    public MyMessage() {}  
  
    //Constructor - create a message and populate its members.  
  
    public MyMessage(double n1, double n2, string operation,
                     double result)  
    {  
        this.n1 = n1;  
        this.n2 = n2;  
        this.operation = operation;  
        this.result = result;  
    }  
  
    //Constructor - create a message from another message.  
  
    public MyMessage(MyMessage message)  
    {  
        this.n1 = message.n1;  
        this.n2 = message.n2;  
        this.operation = message.operation;  
        this.result = message.result;  
    }  
  
    [MessageHeader]  
    public string Operation  
    {  
        get { return operation; }  
        set { operation = value; }  
    }  
  
    [MessageBodyMember]  
    public double N1  
    {  
        get { return n1; }  
        set { n1 = value; }  
    }  
  
    [MessageBodyMember]  
    public double N2  
    {  
        get { return n2; }  
        set { n2 = value; }  
    }  
  
    [MessageBodyMember]  
    public double Result  
    {  
        get { return result; }  
        set { result = value; }  
    }  
}  
```  
  
 <span data-ttu-id="17b13-117">实现类包含 `Calculate` 服务操作的代码。</span><span class="sxs-lookup"><span data-stu-id="17b13-117">The implementation class contains the code for the `Calculate` service operation.</span></span> <span data-ttu-id="17b13-118">`CalculateService` 类从请求消息获取操作数和运算符，并创建一条包含所请求的计算的结果的响应消息，如下面的示例代码所示。</span><span class="sxs-lookup"><span data-stu-id="17b13-118">The `CalculateService` class obtains the operands and operator from the request message and creates a response message that contains the result of the requested calculation, as shown in the following sample code.</span></span>  
  
```csharp
// Service class which implements the service contract.  
public class CalculatorService : ICalculator  
{  
    // Perform a calculation.  
  
    public MyMessage Calculate(MyMessage request)  
    {  
        MyMessage response = new MyMessage(request);  
        switch (request.Operation)  
        {  
            case "+":  
                response.Result = request.N1 + request.N2;  
                break;  
            case "-":  
                response.Result = request.N1 - request.N2;  
                break;  
            case "*":  
                response.Result = request.N1 * request.N2;  
                break;  
            case "/":  
                response.Result = request.N1 / request.N2;  
                break;  
            default:  
                response.Result = 0.0D;  
                break;  
        }  
        return response;  
    }  
}  
```  
  
 <span data-ttu-id="17b13-119">为客户端生成的客户端代码是通过 [ ( # A0) ](../servicemodel-metadata-utility-tool-svcutil-exe.md) 工具创建的。</span><span class="sxs-lookup"><span data-stu-id="17b13-119">The generated client code for the client was created with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) tool.</span></span> <span data-ttu-id="17b13-120">在必要时，该工具会自动在所生成的客户端代码中创建消息协定类型。</span><span class="sxs-lookup"><span data-stu-id="17b13-120">The tool automatically creates message contract types in the generated client code if necessary.</span></span> <span data-ttu-id="17b13-121">可以指定 `/messageContract` 命令选项来强制生成消息协定。</span><span class="sxs-lookup"><span data-stu-id="17b13-121">The `/messageContract` command option may be specified to force the generation of message contracts.</span></span>  
  
```console  
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" /o:client\generatedClient.cs http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="17b13-122">下面的示例代码演示使用 `MyMessage` 消息的客户端。</span><span class="sxs-lookup"><span data-stu-id="17b13-122">The following sample code demonstrates the client using the `MyMessage` message.</span></span>  
  
```csharp
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
// Perform addition using a typed message.  
  
MyMessage request = new MyMessage()
                    {  
                        N1 = 100D,  
                        N2 = 15.99D,  
                        Operation = "+"  
                    };
MyMessage response = ((ICalculator)client).Calculate(request);  
Console.WriteLine("Add({0},{1}) = {2}", request.N1, request.N2, response.Result);  
```  
  
 <span data-ttu-id="17b13-123">运行示例时，计算结果将显示在客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="17b13-123">When you run the sample, the calculations are displayed in the client console window.</span></span> <span data-ttu-id="17b13-124">在客户端窗口中按 Enter 可以关闭客户端。</span><span class="sxs-lookup"><span data-stu-id="17b13-124">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="17b13-125">此时，用户定义的自定义消息已经在客户端和服务操作之间传递。</span><span class="sxs-lookup"><span data-stu-id="17b13-125">At this point, custom user-defined messages have passed between the client and the service operation.</span></span> <span data-ttu-id="17b13-126">消息协定进行了如下定义：操作数和结果位于消息正文中，运算符位于消息头中。</span><span class="sxs-lookup"><span data-stu-id="17b13-126">The message contract defined that the operands and results were in the message body and that the operator was in a message header.</span></span> <span data-ttu-id="17b13-127">消息日志记录可以配置为遵守这个消息结构。</span><span class="sxs-lookup"><span data-stu-id="17b13-127">Message logging can be configured to observe this message structure.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="17b13-128">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="17b13-128">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="17b13-129">确保已对 [Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="17b13-129">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="17b13-130">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="17b13-130">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="17b13-131">若要以单机配置或跨计算机配置来运行示例，请按照 [运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="17b13-131">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="17b13-132">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="17b13-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="17b13-133">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="17b13-133">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="17b13-134">如果此目录不存在，请参阅[Windows Communication Foundation (wcf) ，并 Windows Workflow Foundation (的 WF](https://www.microsoft.com/download/details.aspx?id=21459)) .NET Framework Windows Communication Foundation ([!INCLUDE[wf1](../../../../includes/wf1-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17b13-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="17b13-135">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="17b13-135">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Default`  
