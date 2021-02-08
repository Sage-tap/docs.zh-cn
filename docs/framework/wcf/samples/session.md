---
description: 了解详细信息：会话
title: 会话
ms.date: 03/30/2017
helpviewer_keywords:
- Sessions
ms.assetid: 36e1db50-008c-4b32-8d09-b56e790b8417
ms.openlocfilehash: ba8d2d44d0be22243bd1562f9bd499d68a1112af
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793020"
---
# <a name="session"></a><span data-ttu-id="165f6-103">会话</span><span class="sxs-lookup"><span data-stu-id="165f6-103">Session</span></span>

<span data-ttu-id="165f6-104">“会话”示例演示如何实现需要会话的协定。</span><span class="sxs-lookup"><span data-stu-id="165f6-104">The Session sample demonstrates how to implement a contract that requires a session.</span></span> <span data-ttu-id="165f6-105">会话提供用来执行多个操作的上下文。</span><span class="sxs-lookup"><span data-stu-id="165f6-105">A session provides context for performing multiple operations.</span></span> <span data-ttu-id="165f6-106">这允许服务将某个状态与给定的会话相关联，从而使后续操作可以使用上一个操作的状态。</span><span class="sxs-lookup"><span data-stu-id="165f6-106">This allows a service to associate state with a given session, such that subsequent operations can use the state of a previous operation.</span></span> <span data-ttu-id="165f6-107">此示例基于实现计算器服务的 [入门](getting-started-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="165f6-107">This sample is based on the [Getting Started](getting-started-sample.md), which implements a calculator service.</span></span> <span data-ttu-id="165f6-108">`ICalculator` 协定已进行修改，允许在保持运行结果的同时执行一组算术运算。</span><span class="sxs-lookup"><span data-stu-id="165f6-108">The `ICalculator` contract has been modified to allow a set of arithmetic operations to be performed, while keeping a running result.</span></span> <span data-ttu-id="165f6-109">此功能由 `ICalculatorSession` 协定定义。</span><span class="sxs-lookup"><span data-stu-id="165f6-109">This functionality is defined by the `ICalculatorSession` contract.</span></span> <span data-ttu-id="165f6-110">服务在调用多个服务操作以执行一个计算时维护客户端的状态。</span><span class="sxs-lookup"><span data-stu-id="165f6-110">The service maintains the state for a client as multiple service operations are called to perform a calculation.</span></span> <span data-ttu-id="165f6-111">客户端可以通过调用 `Result()` 来检索当前结果，通过调用 `Clear()` 将结果清零。</span><span class="sxs-lookup"><span data-stu-id="165f6-111">The client can retrieve the current result by calling `Result()` and clear the result to zero by calling `Clear()`.</span></span>  
  
 <span data-ttu-id="165f6-112">在此示例中，客户端是一个控制台应用程序 (.exe)，服务是由 Internet 信息服务 (IIS) 承载的。</span><span class="sxs-lookup"><span data-stu-id="165f6-112">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="165f6-113">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="165f6-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="165f6-114">将协定的 <xref:System.ServiceModel.SessionMode> 设置为 `Required` 可以确保在通过特定的绑定公开该协定时，该绑定支持会话。</span><span class="sxs-lookup"><span data-stu-id="165f6-114">Setting the <xref:System.ServiceModel.SessionMode> of the contract to `Required` ensures that when the contract is exposed over a particular binding, the binding supports sessions.</span></span> <span data-ttu-id="165f6-115">如果绑定不支持会话，则会引发异常。</span><span class="sxs-lookup"><span data-stu-id="165f6-115">If the binding does not support sessions an exception is thrown.</span></span> <span data-ttu-id="165f6-116">定义 `ICalculatorSession` 接口使得可以调用一个或多个修改运行结果的操作，如下面的示例代码所示。</span><span class="sxs-lookup"><span data-stu-id="165f6-116">The `ICalculatorSession` interface is defined such that one or more operations can be called, which modifies a running result, as shown in the following sample code.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples", SessionMode=SessionMode.Required)]  
public interface ICalculatorSession  
{  
    [OperationContract(IsOneWay=true)]  
    void Clear();  
    [OperationContract(IsOneWay = true)]  
    void AddTo(double n);  
    [OperationContract(IsOneWay = true)]  
    void SubtractFrom(double n);  
    [OperationContract(IsOneWay = true)]  
    void MultiplyBy(double n);  
    [OperationContract(IsOneWay = true)]  
    void DivideBy(double n);  
    [OperationContract]  
    double Result();  
}  
```  
  
 <span data-ttu-id="165f6-117">服务使用 <xref:System.ServiceModel.InstanceContextMode> 的 <xref:System.ServiceModel.InstanceContextMode.PerSession> 将给定的服务实例上下文绑定到每个传入会话。</span><span class="sxs-lookup"><span data-stu-id="165f6-117">The service uses a <xref:System.ServiceModel.InstanceContextMode> of <xref:System.ServiceModel.InstanceContextMode.PerSession> to bind a given service instance context to each incoming session.</span></span> <span data-ttu-id="165f6-118">这使服务可以在本地成员变量中维护每个会话的运行结果。</span><span class="sxs-lookup"><span data-stu-id="165f6-118">This allows the service to maintain the running result for each session in a local member variable.</span></span>  
  
```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
public class CalculatorService : ICalculatorSession  
{  
    double result = 0.0D;  
  
    public void Clear()  
    {  result = 0.0D; }  
  
    public void AddTo(double n)  
    {  result += n;   }  
  
    public void SubtractFrom(double n)  
    {  result -= n;   }  
  
    public void MultiplyBy(double n)  
    {  result *= n;   }  
  
    public void DivideBy(double n)  
    {  result /= n;   }  
  
    public double Result()  
    {  return result; }  
}  
```  
  
 <span data-ttu-id="165f6-119">运行示例时，客户端会向服务器发出几个请求并请求结果，结果然后显示在客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="165f6-119">When you run the sample, the client makes several requests to the server and requests the result, which it then displays in the client console window.</span></span> <span data-ttu-id="165f6-120">在客户端窗口中按 Enter 可以关闭客户端。</span><span class="sxs-lookup"><span data-stu-id="165f6-120">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
(((0 + 100) - 50) * 17.65) / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="165f6-121">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="165f6-121">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="165f6-122">确保已对 [Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="165f6-122">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="165f6-123">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="165f6-123">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="165f6-124">若要以单机配置或跨计算机配置来运行示例，请按照 [运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="165f6-124">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="165f6-125">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="165f6-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="165f6-126">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="165f6-126">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="165f6-127">如果此目录不存在，请参阅[Windows Communication Foundation (wcf) ，并 Windows Workflow Foundation (的 WF](https://www.microsoft.com/download/details.aspx?id=21459)) .NET Framework Windows Communication Foundation ([!INCLUDE[wf1](../../../../includes/wf1-md.md)]</span><span class="sxs-lookup"><span data-stu-id="165f6-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="165f6-128">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="165f6-128">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Session`  
