---
description: 了解详细信息： XmlReader 示例
title: XmlReader 示例
ms.date: 03/30/2017
helpviewer_keywords:
- XML Reader
ms.assetid: 60e5848d-7d9c-4ea5-bed9-22758c9ac16c
ms.openlocfilehash: 07e54c6f8ccfe36bc378bd8c839cd7dd7f6ecb42
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668261"
---
# <a name="xmlreader-sample"></a><span data-ttu-id="03ea7-103">XmlReader 示例</span><span class="sxs-lookup"><span data-stu-id="03ea7-103">XmlReader Sample</span></span>

<span data-ttu-id="03ea7-104">XmlReader 示例演示如何使用 <xref:System.Xml.XmlReader> 处理消息正文。</span><span class="sxs-lookup"><span data-stu-id="03ea7-104">The XmlReader sample demonstrates the processing of a message body using an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="03ea7-105">该示例基于实现计算器服务的 [入门](getting-started-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="03ea7-105">The sample is based on the [Getting Started](getting-started-sample.md), which implements a calculator service.</span></span> <span data-ttu-id="03ea7-106">示例中还添加了一个服务操作 `Sum`，它接受包含要加在一起的值数组的消息。</span><span class="sxs-lookup"><span data-stu-id="03ea7-106">An additional service operation, `Sum`, has been added that accepts a message that contains an array of values to add together.</span></span> <span data-ttu-id="03ea7-107">该服务使用 <xref:System.Xml.XmlReader> 读取消息。</span><span class="sxs-lookup"><span data-stu-id="03ea7-107">The service reads the message using an <xref:System.Xml.XmlReader>.</span></span>

> [!NOTE]
> <span data-ttu-id="03ea7-108">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="03ea7-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="03ea7-109">计算器接口包括名为 `Sum` 的服务操作，它接受 <xref:System.ServiceModel.Channels.Message> 参数，如下面的示例代码所示。</span><span class="sxs-lookup"><span data-stu-id="03ea7-109">The calculator interface includes a service operation named `Sum` that accepts a <xref:System.ServiceModel.Channels.Message> parameter, as shown in the following sample code.</span></span>

```csharp
public interface ICalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    [OperationContract]
    double Subtract(double n1, double n2);
    [OperationContract]
    double Multiply(double n1, double n2);
    [OperationContract]
    double Divide(double n1, double n2);
    [OperationContract]
    Message Sum(Message message);
}
```

<span data-ttu-id="03ea7-110">客户端按如下方式访问 `Sum`，首先创建整数值数组，再创建来自该数组的消息，接着使用创建的消息调用 `Sum` 方法，如下面的示例代码所示。</span><span class="sxs-lookup"><span data-stu-id="03ea7-110">The client accesses `Sum` by first creating an array of integer values, then creating a message from the array, and then calling the `Sum` method using the created message, as shown in the following sample code.</span></span>

```csharp
CalculatorClient client = new CalculatorClient();
//...

// Call the Sum service operation.
int[] values = { 1, 2, 3, 4, 5 };
using (new OperationContextScope(client.InnerChannel))
{
    Message request = Message.CreateMessage(OperationContext.Current.OutgoingMessageHeaders.MessageVersion, "http://Microsoft.ServiceModel.Samples/ICalculator/Sum", values);
    Message reply = client.Sum(request);
    int sum = reply.GetBody<int>();

    Console.WriteLine("Sum(1,2,3,4,5) = {0}", sum);
}
```

<span data-ttu-id="03ea7-111">在服务中，服务操作 `Sum` 的实现使用 <xref:System.Xml.XmlReader> 对象访问消息正文，以便循环访问要求和的值。</span><span class="sxs-lookup"><span data-stu-id="03ea7-111">In the service, the implementation of the service operation `Sum` accesses the message body using an <xref:System.Xml.XmlReader> object to iterate through the values to sum.</span></span> <span data-ttu-id="03ea7-112">调用 <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> 方法可以访问消息正文，如下面的示例代码所示。</span><span class="sxs-lookup"><span data-stu-id="03ea7-112">The <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> method is called to access the message body, as shown in the following sample code.</span></span>

```csharp
public int Sum(Message message)
{
    int sum = 0;
    string text = "";

    //The body of the message contains a list of numbers that are read
    //directly using an XmlReader.
    XmlReader body = message.GetReaderAtBodyContents ();
    while (body.Read())
    {
        text = body.ReadString().Trim();
        if (text.Length>0)
        {
            sum += Convert.ToInt32(text);
        }
    }
    body.Close();
    Message response = Message.CreateMessage(
       "http://Microsoft.ServiceModel.Samples/ICalculator/SumResponse",
       sum);
    return response;
}
```

<span data-ttu-id="03ea7-113">运行示例时，操作的请求和响应将显示在客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="03ea7-113">When you run the sample, the requests and responses of the operation are displayed in the client console window.</span></span> <span data-ttu-id="03ea7-114">在客户端窗口中按 Enter 可以关闭客户端。</span><span class="sxs-lookup"><span data-stu-id="03ea7-114">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Sum(1,2,3,4,5) = 15

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="03ea7-115">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="03ea7-115">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="03ea7-116">确保已对 [Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="03ea7-116">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="03ea7-117">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="03ea7-117">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="03ea7-118">若要以单机配置或跨计算机配置来运行示例，请按照 [运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="03ea7-118">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="03ea7-119">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="03ea7-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="03ea7-120">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="03ea7-120">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="03ea7-121">如果此目录不存在，请参阅[Windows Communication Foundation (wcf) ，并 Windows Workflow Foundation (的 WF](https://www.microsoft.com/download/details.aspx?id=21459)) .NET Framework Windows Communication Foundation ([!INCLUDE[wf1](../../../../includes/wf1-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03ea7-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="03ea7-122">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="03ea7-122">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\XmlReader`
