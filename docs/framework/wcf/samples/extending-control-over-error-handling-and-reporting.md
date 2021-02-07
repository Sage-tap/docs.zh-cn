---
description: 了解详细信息：扩展对错误处理和报告的控制
title: 扩展对错误处理和错误报告的控制
ms.date: 03/30/2017
ms.assetid: 45f996a7-fa00-45cb-9d6f-b368f5778aaa
ms.openlocfilehash: 9b9dd7761757235b2381fce575021aca2be404f2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752374"
---
# <a name="extending-control-over-error-handling-and-reporting"></a><span data-ttu-id="1d9df-103">扩展对错误处理和错误报告的控制</span><span class="sxs-lookup"><span data-stu-id="1d9df-103">Extending Control Over Error Handling and Reporting</span></span>

<span data-ttu-id="1d9df-104">此示例演示如何使用接口在 Windows Communication Foundation (WCF) 服务中扩展对错误处理和错误报告的控制 <xref:System.ServiceModel.Dispatcher.IErrorHandler> 。</span><span class="sxs-lookup"><span data-stu-id="1d9df-104">This sample demonstrates how to extend control over error handling and error reporting in a Windows Communication Foundation (WCF) service using the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface.</span></span> <span data-ttu-id="1d9df-105">该示例基于 [入门](getting-started-sample.md) ，并向服务添加了一些附加代码来处理错误。</span><span class="sxs-lookup"><span data-stu-id="1d9df-105">The sample is based on the [Getting Started](getting-started-sample.md) with some additional code added to the service to handle errors.</span></span> <span data-ttu-id="1d9df-106">客户端强制实施若干个错误条件。</span><span class="sxs-lookup"><span data-stu-id="1d9df-106">The client forces several error conditions.</span></span> <span data-ttu-id="1d9df-107">服务将截获这些错误并将其记录到某个文件中。</span><span class="sxs-lookup"><span data-stu-id="1d9df-107">The service intercepts the errors and logs them in a file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1d9df-108">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="1d9df-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="1d9df-109">服务可以截获错误、执行处理，并使用 <xref:System.ServiceModel.Dispatcher.IErrorHandler> 接口影响错误报告的方式。</span><span class="sxs-lookup"><span data-stu-id="1d9df-109">Services can intercept errors, perform processing, and affect how errors are reported using the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface.</span></span> <span data-ttu-id="1d9df-110">该接口有两个可以实现的方法：<xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> 和 <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>。</span><span class="sxs-lookup"><span data-stu-id="1d9df-110">The interface has two methods that can be implemented: <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> and <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>.</span></span> <span data-ttu-id="1d9df-111">通过 <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> 方法，您可以添加、修改或取消为响应异常而生成的错误消息。</span><span class="sxs-lookup"><span data-stu-id="1d9df-111">The <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> method allows you to add, modify, or suppress a fault message that is generated in response to an exception.</span></span> <span data-ttu-id="1d9df-112">通过 <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> 方法，您可以在发生错误时对错误进行处理，并控制是否可以运行其他错误处理。</span><span class="sxs-lookup"><span data-stu-id="1d9df-112">The <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> method allows error processing to take place in the event of an error and controls whether additional error handling can run.</span></span>  
  
 <span data-ttu-id="1d9df-113">在此示例中，`CalculatorErrorHandler` 类型实现 <xref:System.ServiceModel.Dispatcher.IErrorHandler> 接口。</span><span class="sxs-lookup"><span data-stu-id="1d9df-113">In this sample, the `CalculatorErrorHandler` type implements the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface.</span></span> <span data-ttu-id="1d9df-114">在</span><span class="sxs-lookup"><span data-stu-id="1d9df-114">In the</span></span>  
  
 <span data-ttu-id="1d9df-115"><xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> 方法中，`CalculatorErrorHandler` 将错误日志写入 c:\logs 中的 Error.txt 文本文件中。</span><span class="sxs-lookup"><span data-stu-id="1d9df-115"><xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> method, the `CalculatorErrorHandler` writes a log of the error to an Error.txt text file in c:\logs.</span></span> <span data-ttu-id="1d9df-116">请注意，该示例记录错误而不会取消错误，并允许错误报告回客户端。</span><span class="sxs-lookup"><span data-stu-id="1d9df-116">Note that the sample logs the fault and does not suppress it, allowing it to be reported back to the client.</span></span>  
  
```csharp
public class CalculatorErrorHandler : IErrorHandler
{
    // Provide a fault. The Message fault parameter can be replaced, or set to
    // null to suppress reporting a fault.

    public void ProvideFault(Exception error, MessageVersion version, ref Message fault)
    {
    }

    // HandleError. Log an error, then allow the error to be handled as usual.
    // Return true if the error is considered as already handled

    public bool HandleError(Exception error)
    {
        using (TextWriter tw = File.AppendText(@"c:\logs\error.txt"))
        {
            if (error != null)
            {
                tw.WriteLine("Exception: " + error.GetType().Name + " - " + error.Message);
            }
            tw.Close();
        }
        return true;
    }
}  
```  
  
 <span data-ttu-id="1d9df-117">`ErrorBehaviorAttribute` 作为一种向服务注册错误处理程序的机制存在。</span><span class="sxs-lookup"><span data-stu-id="1d9df-117">The `ErrorBehaviorAttribute` exists as a mechanism to register an error handler with a service.</span></span> <span data-ttu-id="1d9df-118">此属性采取单一类型的参数。</span><span class="sxs-lookup"><span data-stu-id="1d9df-118">This attribute takes a single type parameter.</span></span> <span data-ttu-id="1d9df-119">该类型应实现 <xref:System.ServiceModel.Dispatcher.IErrorHandler> 接口，还应具有一个公用的空构造函数。</span><span class="sxs-lookup"><span data-stu-id="1d9df-119">That type should implement the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface and should have a public, empty constructor.</span></span> <span data-ttu-id="1d9df-120">该属性随后实例化该错误处理程序类型的实例，并将其安装到该服务中。</span><span class="sxs-lookup"><span data-stu-id="1d9df-120">The attribute then instantiates an instance of that error handler type and installs it into the service.</span></span> <span data-ttu-id="1d9df-121">实现此操作的方法是，实现 <xref:System.ServiceModel.Description.IServiceBehavior> 接口，然后使用 <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> 方法将错误处理程序的实例添加到该服务。</span><span class="sxs-lookup"><span data-stu-id="1d9df-121">It does this by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface and then using the <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> method to add instances of the error handler to the service.</span></span>  
  
```csharp
// This attribute can be used to install a custom error handler for a service.  
public class ErrorBehaviorAttribute : Attribute, IServiceBehavior  
{  
    Type errorHandlerType;  
  
    public ErrorBehaviorAttribute(Type errorHandlerType)  
    {  
        this.errorHandlerType = errorHandlerType;  
    }  
  
    void IServiceBehavior.Validate(ServiceDescription description, ServiceHostBase serviceHostBase)  
    {  
    }  
  
    void IServiceBehavior.AddBindingParameters(ServiceDescription description, ServiceHostBase serviceHostBase, System.Collections.ObjectModel.Collection<ServiceEndpoint> endpoints, BindingParameterCollection parameters)  
    {  
    }  
  
    void IServiceBehavior.ApplyDispatchBehavior(ServiceDescription description, ServiceHostBase serviceHostBase)  
    {  
        IErrorHandler errorHandler;  
  
        try  
        {  
            errorHandler = (IErrorHandler)Activator.CreateInstance(errorHandlerType);  
        }  
        catch (MissingMethodException e)  
        {  
            throw new ArgumentException("The errorHandlerType specified in the ErrorBehaviorAttribute constructor must have a public empty constructor.", e);  
        }  
        catch (InvalidCastException e)  
        {  
            throw new ArgumentException("The errorHandlerType specified in the ErrorBehaviorAttribute constructor must implement System.ServiceModel.Dispatcher.IErrorHandler.", e);  
        }  
  
        foreach (ChannelDispatcherBase channelDispatcherBase in serviceHostBase.ChannelDispatchers)  
        {  
            ChannelDispatcher channelDispatcher = channelDispatcherBase as ChannelDispatcher;  
            channelDispatcher.ErrorHandlers.Add(errorHandler);  
        }
    }  
}  
```  
  
 <span data-ttu-id="1d9df-122">该示例实现计算器服务。</span><span class="sxs-lookup"><span data-stu-id="1d9df-122">The sample implements a calculator service.</span></span> <span data-ttu-id="1d9df-123">客户端通过提供具有非法值的参数，使该服务故意出现两个错误。</span><span class="sxs-lookup"><span data-stu-id="1d9df-123">The client deliberately causes two errors to occur on the service by providing parameters with illegal values.</span></span> <span data-ttu-id="1d9df-124">`CalculatorErrorHandler` 使用 <xref:System.ServiceModel.Dispatcher.IErrorHandler> 接口将这些错误记录到某个本地文件，然后允许将这些错误报告回客户端。</span><span class="sxs-lookup"><span data-stu-id="1d9df-124">The `CalculatorErrorHandler` uses the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface to log the errors to a local file and then allows them to be reported back to the client.</span></span> <span data-ttu-id="1d9df-125">客户端强制执行除以零的除法运算和自变量超出范围的情况。</span><span class="sxs-lookup"><span data-stu-id="1d9df-125">The client forces a divide by zero and an argument-out-of-range condition.</span></span>  
  
```csharp
try
{  
    Console.WriteLine("Forcing an error in Divide");  
    // Call the Divide service operation - trigger a divide by 0 error.  
    value1 = 22;  
    value2 = 0;  
    result = proxy.Divide(value1, value2);  
    Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
}  
catch (FaultException e)  
{  
    Console.WriteLine("FaultException: " + e.GetType().Name + " - " + e.Message);  
}  
catch (Exception e)  
{  
    Console.WriteLine("Exception: " + e.GetType().Name + " - " + e.Message);  
}  
```  
  
 <span data-ttu-id="1d9df-126">运行示例时，操作请求和响应将显示在客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="1d9df-126">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="1d9df-127">你将看到除以零的除法运算和自变量超出范围的情况被报告为错误。</span><span class="sxs-lookup"><span data-stu-id="1d9df-127">You see the division by zero and the argument-out-of-range conditions being reported as faults.</span></span> <span data-ttu-id="1d9df-128">在客户端窗口中按 Enter 可以关闭客户端。</span><span class="sxs-lookup"><span data-stu-id="1d9df-128">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
Forcing an error in Divide  
FaultException: FaultException - Invalid Argument: The second argument must not be zero.  
Forcing an error in Factorial  
FaultException: FaultException - Invalid Argument: The argument must be greater than zero.  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="1d9df-129">文件 c:\logs\errors.txt 包含服务记录的有关错误的信息。</span><span class="sxs-lookup"><span data-stu-id="1d9df-129">The file c:\logs\errors.txt contains the information logged about the errors by the service.</span></span> <span data-ttu-id="1d9df-130">请注意，为了使服务能够写入目录，必须确保运行服务的进程 (通常 ASP.NET 或网络服务) 有权写入该目录。</span><span class="sxs-lookup"><span data-stu-id="1d9df-130">Note that for the service to write to the directory you must make sure that the process under which the service is running (typically ASP.NET or Network Service) has permission to write to the directory.</span></span>  
  
```txt
Fault: Reason = Invalid Argument: The second argument must not be zero.  
Fault: Reason = Invalid Argument: The argument must be greater than zero.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1d9df-131">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="1d9df-131">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="1d9df-132">确保已对 [Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="1d9df-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="1d9df-133">若要生成解决方案，请按照 [生成 Windows Communication Foundation 示例](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="1d9df-133">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="1d9df-134">确保您已经为 error.txt 文件创建了 c:\logs 目录，</span><span class="sxs-lookup"><span data-stu-id="1d9df-134">Ensure you have created the c:\logs directory for the error.txt file.</span></span> <span data-ttu-id="1d9df-135">或者修改 `CalculatorErrorHandler.HandleError` 中使用的文件名。</span><span class="sxs-lookup"><span data-stu-id="1d9df-135">Or modify the file name used in `CalculatorErrorHandler.HandleError`.</span></span>  
  
4. <span data-ttu-id="1d9df-136">若要以单机配置或跨计算机配置来运行示例，请按照 [运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="1d9df-136">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1d9df-137">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="1d9df-137">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1d9df-138">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="1d9df-138">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="1d9df-139">如果此目录不存在，请参阅[Windows Communication Foundation (wcf) ，并 Windows Workflow Foundation (的 WF](https://www.microsoft.com/download/details.aspx?id=21459)) .NET Framework Windows Communication Foundation ([!INCLUDE[wf1](../../../../includes/wf1-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d9df-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1d9df-140">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="1d9df-140">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\ErrorHandling`  
