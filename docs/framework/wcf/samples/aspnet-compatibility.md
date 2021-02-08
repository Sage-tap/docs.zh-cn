---
description: 了解详细信息： ASP.NET 兼容性
title: ASP.NET 兼容性
ms.date: 03/30/2017
ms.assetid: c8b51f1e-c096-4c42-ad99-0519887bbbc5
ms.openlocfilehash: a5685481a16d87715d4fc9096055af5be479f459
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778849"
---
# <a name="aspnet-compatibility"></a><span data-ttu-id="20471-103">ASP.NET 兼容性</span><span class="sxs-lookup"><span data-stu-id="20471-103">ASP.NET Compatibility</span></span>

<span data-ttu-id="20471-104">此示例演示如何在 Windows Communication Foundation (WCF) 中启用 ASP.NET 兼容性模式。</span><span class="sxs-lookup"><span data-stu-id="20471-104">This sample demonstrates how to enable ASP.NET Compatibility mode in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="20471-105">在 ASP.NET 兼容模式下运行的服务完全参与 ASP.NET 应用程序管道，并可利用 ASP.NET 功能，如文件/URL 授权、会话状态和 <xref:System.Web.HttpContext> 类。</span><span class="sxs-lookup"><span data-stu-id="20471-105">Services running in ASP.NET Compatibility mode participate fully in the ASP.NET application pipeline and can make use of ASP.NET features such as file/URL authorization, session state, and the <xref:System.Web.HttpContext> class.</span></span> <span data-ttu-id="20471-106"><xref:System.Web.HttpContext>类允许访问 cookie、会话和其他 ASP.NET 功能。</span><span class="sxs-lookup"><span data-stu-id="20471-106">The <xref:System.Web.HttpContext> class allows access to cookies, sessions, and other ASP.NET features.</span></span> <span data-ttu-id="20471-107">此模式要求绑定使用 HTTP 传输，且服务本身必须承载于 IIS 中。</span><span class="sxs-lookup"><span data-stu-id="20471-107">This mode requires that the bindings use the HTTP transport and the service itself must be hosted in IIS.</span></span>

<span data-ttu-id="20471-108">在此示例中，客户端是一个控制台应用程序（一个可执行文件），服务由 Internet 信息服务 (IIS) 承载。</span><span class="sxs-lookup"><span data-stu-id="20471-108">In this sample, the client is a console application (an executable) and the service is hosted in Internet Information Services (IIS).</span></span>

> [!NOTE]
> <span data-ttu-id="20471-109">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="20471-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="20471-110">此示例需要 .NET Framework 4 应用程序池才能运行。</span><span class="sxs-lookup"><span data-stu-id="20471-110">This sample requires a .NET Framework 4 application pool in order to run.</span></span> <span data-ttu-id="20471-111">若要创建新的应用程序池或修改默认应用程序池，请按照以下步骤操作。</span><span class="sxs-lookup"><span data-stu-id="20471-111">To create a new application pool, or to modify the default application pool, follow these steps.</span></span>

1. <span data-ttu-id="20471-112">打开“控制面板”</span><span class="sxs-lookup"><span data-stu-id="20471-112">Open **Control Panel**.</span></span>  <span data-ttu-id="20471-113">打开 "**系统和安全**" 标题下的 "**管理工具**" 小程序。</span><span class="sxs-lookup"><span data-stu-id="20471-113">Open the **Administrative Tools** applet under the **System and Security** heading.</span></span> <span data-ttu-id="20471-114">**(IIS) 管理器** 小程序打开 Internet Information Services。</span><span class="sxs-lookup"><span data-stu-id="20471-114">Open the **Internet Information Services (IIS) Manager** applet.</span></span>

2. <span data-ttu-id="20471-115">展开 " **连接** " 窗格中的 treeview。</span><span class="sxs-lookup"><span data-stu-id="20471-115">Expand the treeview in the **Connections** pane.</span></span> <span data-ttu-id="20471-116">选择 " **应用程序池** " 节点。</span><span class="sxs-lookup"><span data-stu-id="20471-116">Select the **Application Pools** node.</span></span>

3. <span data-ttu-id="20471-117">若要将默认应用程序池设置为使用 .NET Framework 4 (这可能会导致) 的现有站点出现不兼容问题，请右键单击 " **DefaultAppPool** " 列表项并选择 " **基本设置 ...**"。</span><span class="sxs-lookup"><span data-stu-id="20471-117">To set the default application pool to use .NET Framework 4 (which may cause incompatibility problems with existing sites), right-click the **DefaultAppPool** list item and select **Basic Settings…**.</span></span> <span data-ttu-id="20471-118">将 **.Net Framework 版本** 下拉菜单 **设置 (或** 更高版本) 。</span><span class="sxs-lookup"><span data-stu-id="20471-118">Set the **.Net Framework Version** pull-down to **.Net Framework v4.0.30128** (or later).</span></span>

4. <span data-ttu-id="20471-119">若要创建一个新的应用程序池，该应用程序池使用 .NET Framework 4 (来保留其他应用程序的兼容性) ，右键单击 " **应用程序** 池" 节点，然后选择 " **添加应用程序池 ...**"。</span><span class="sxs-lookup"><span data-stu-id="20471-119">To create a new application pool that uses .NET Framework 4 (to preserve compatibility for other applications), right-click the **Application Pools** node and select **Add Application Pool…**.</span></span> <span data-ttu-id="20471-120">命名新的应用程序池，并将 **.Net Framework 版本** 下拉菜单设置为 **.net framework v v4.0.30128** (或更高版本) 。</span><span class="sxs-lookup"><span data-stu-id="20471-120">Name the new application pool, and set the **.Net Framework Version** pull-down to **.Net Framework v4.0.30128** (or later).</span></span> <span data-ttu-id="20471-121">运行以下安装步骤后，右键单击 **ServiceModelSamples** 应用程序，然后选择 " **管理应用程序**、 **高级设置 ...**"。</span><span class="sxs-lookup"><span data-stu-id="20471-121">After running the setup steps below, right-click the **ServiceModelSamples** application and select **Manage Application**, **Advanced Settings…**.</span></span> <span data-ttu-id="20471-122">将 **应用程序池** 设置为新的应用程序池。</span><span class="sxs-lookup"><span data-stu-id="20471-122">Set the **Application Pool** to the new application pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="20471-123">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="20471-123">The samples may already be installed on your computer.</span></span> <span data-ttu-id="20471-124">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="20471-124">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="20471-125">如果此目录不存在，请参阅[Windows Communication Foundation (wcf) ，并 Windows Workflow Foundation (的 WF](https://www.microsoft.com/download/details.aspx?id=21459)) .NET Framework Windows Communication Foundation ([!INCLUDE[wf1](../../../../includes/wf1-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20471-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="20471-126">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="20471-126">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\ASPNetCompatibility`

<span data-ttu-id="20471-127">此示例基于实现计算器服务的 [入门](getting-started-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="20471-127">This sample is based on the [Getting Started](getting-started-sample.md), which implements a calculator service.</span></span> <span data-ttu-id="20471-128">`ICalculator` 协定已根据 `ICalculatorSession` 协定进行修改，允许在保持运行结果的同时执行一组运算。</span><span class="sxs-lookup"><span data-stu-id="20471-128">The `ICalculator` contract has been modified as the `ICalculatorSession` contract to allow a set of operations to be performed, while keeping a running result.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface ICalculatorSession
{
    [OperationContract]
    void Clear();
    [OperationContract]
    void AddTo(double n);
    [OperationContract]
    void SubtractFrom(double n);
    [OperationContract]
    void MultiplyBy(double n);
    [OperationContract]
    void DivideBy(double n);
    [OperationContract]
    double Result();
}
```

<span data-ttu-id="20471-129">在调用多个服务操作来执行计算时，服务将使用该功能保持每个客户端的状态。</span><span class="sxs-lookup"><span data-stu-id="20471-129">The service maintains state, using the feature, for each client as multiple service operations are called to perform a calculation.</span></span> <span data-ttu-id="20471-130">客户端可以通过调用 `Result` 来检索当前结果，通过调用 `Clear` 将结果清零。</span><span class="sxs-lookup"><span data-stu-id="20471-130">The client can retrieve the current result by calling `Result` and can clear the result to zero by calling `Clear`.</span></span>

<span data-ttu-id="20471-131">服务使用 ASP.NET 会话存储每个客户端会话的结果。</span><span class="sxs-lookup"><span data-stu-id="20471-131">The service uses the ASP.NET session to store the result for each client session.</span></span> <span data-ttu-id="20471-132">这使服务可以为跨多个服务调用的每个客户端保持运行结果。</span><span class="sxs-lookup"><span data-stu-id="20471-132">This allows the service to maintain the running result for each client across multiple calls to the service.</span></span>

> [!NOTE]
> <span data-ttu-id="20471-133">ASP.NET 会话状态和 WCF 会话的用途非常不同。</span><span class="sxs-lookup"><span data-stu-id="20471-133">ASP.NET session state and WCF sessions are very different things.</span></span> <span data-ttu-id="20471-134">有关 WCF 会话的详细信息，请参阅 [会话](session.md) 。</span><span class="sxs-lookup"><span data-stu-id="20471-134">See [Session](session.md) for details on WCF sessions.</span></span>

<span data-ttu-id="20471-135">该服务对 ASP.NET 会话状态的依赖非常熟悉，需要 ASP.NET 兼容模式才能正常运行。</span><span class="sxs-lookup"><span data-stu-id="20471-135">The service has an intimate dependency on ASP.NET session state and requires ASP.NET compatibility mode to function correctly.</span></span> <span data-ttu-id="20471-136">这些需求是通过应用 `AspNetCompatibilityRequirements` 属性以声明性方式表示的。</span><span class="sxs-lookup"><span data-stu-id="20471-136">These requirements are expressed declaratively by applying the `AspNetCompatibilityRequirements` attribute.</span></span>

```csharp
[AspNetCompatibilityRequirements(RequirementsMode =
                       AspNetCompatibilityRequirementsMode.Required)]
public class CalculatorService : ICalculatorSession
{
    double Result
    {  // store result in AspNet Session
       get {
          if (HttpContext.Current.Session["Result"] != null)
             return (double)HttpContext.Current.Session["Result"];
          return 0.0D;
       }
       set
       {
          HttpContext.Current.Session["Result"] = value;
       }
    }
    public void Clear()
    {
        Result = 0.0D;
    }
    public void AddTo(double n)
    {
        Result += n;
    }
    public void SubtractFrom(double n)
    {
        Result -= n;
    }
    public void MultiplyBy(double n)
    {
        Result *= n;
    }
    public void DivideBy(double n)
    {
        Result /= n;
    }
    public double Result()
    {
        return Result;
    }
}
```

<span data-ttu-id="20471-137">运行示例时，操作请求和响应将显示在客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="20471-137">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="20471-138">在客户端窗口中按 Enter 可以关闭客户端。</span><span class="sxs-lookup"><span data-stu-id="20471-138">Press ENTER in the client window to shut down the client.</span></span>

```console
0, + 100, - 50, * 17.65, / 2 = 441.25
Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="20471-139">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="20471-139">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="20471-140">请确保已 [为 Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="20471-140">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="20471-141">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="20471-141">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="20471-142">构建解决方案后，运行 Setup.bat 在 IIS 7.0 中设置 ServiceModelSamples 应用程序。</span><span class="sxs-lookup"><span data-stu-id="20471-142">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in IIS 7.0.</span></span> <span data-ttu-id="20471-143">现在，ServiceModelSamples 目录应显示为 IIS 7.0 应用程序。</span><span class="sxs-lookup"><span data-stu-id="20471-143">The ServiceModelSamples directory should now appear as an IIS 7.0 Application.</span></span>

4. <span data-ttu-id="20471-144">若要以单机配置或跨计算机配置来运行示例，请按照 [运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="20471-144">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="20471-145">请参阅</span><span class="sxs-lookup"><span data-stu-id="20471-145">See also</span></span>

- <span data-ttu-id="20471-146">[AppFabric 承载和持久性示例](/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="20471-146">[AppFabric Hosting and Persistence Samples](/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
