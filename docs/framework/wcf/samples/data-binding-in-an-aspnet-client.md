---
description: 了解详细信息： ASP.NET 客户端中的数据绑定
title: ASP.NET 客户端中的数据绑定
ms.date: 03/30/2017
ms.assetid: 68b49fa6-94e7-4d4c-a34e-902a2b3770b6
ms.openlocfilehash: 9615c34805d406bb382ab252f317156e1750bed1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755858"
---
# <a name="data-binding-in-an-aspnet-client"></a><span data-ttu-id="69bd8-103">ASP.NET 客户端中的数据绑定</span><span class="sxs-lookup"><span data-stu-id="69bd8-103">Data Binding in an ASP.NET Client</span></span>

<span data-ttu-id="69bd8-104">此示例演示如何在 Web 窗体应用程序中绑定由典型 Windows Communication Foundation (WCF) 服务返回的数据。</span><span class="sxs-lookup"><span data-stu-id="69bd8-104">This sample demonstrates how to bind data returned by a typical Windows Communication Foundation (WCF) service in a Web Forms application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="69bd8-105">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="69bd8-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="69bd8-106">本示例演示一个服务，该服务可实现定义“请求-答复”通信模式的协定。</span><span class="sxs-lookup"><span data-stu-id="69bd8-106">This sample demonstrates a service that implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="69bd8-107">该示例包含一个客户端 Web 窗体应用程序，该应用程序可从浏览器和通过 Internet Information Services (IIS) 承载的 WCF 服务进行访问。</span><span class="sxs-lookup"><span data-stu-id="69bd8-107">The sample consists of a client Web Forms application accessible from a browser and a WCF service hosted by Internet Information Services (IIS).</span></span>  
  
 <span data-ttu-id="69bd8-108">该服务实现定义“请求-答复”通信模式的协定。</span><span class="sxs-lookup"><span data-stu-id="69bd8-108">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="69bd8-109">协定由 `IWeatherService` 接口定义，该接口公开一个名为 `GetWeatherData` 的操作。</span><span class="sxs-lookup"><span data-stu-id="69bd8-109">The contract is defined by the `IWeatherService` interface, which exposes an operation named `GetWeatherData`.</span></span> <span data-ttu-id="69bd8-110">此操作接受一个城市数组并返回一个 `WeatherData` 对象数组，这些对象表示城市的预报高温和预报低温。</span><span class="sxs-lookup"><span data-stu-id="69bd8-110">This operation accepts an array of cities and returns an array of `WeatherData` objects that represent the high and low forecasted temperature for a city.</span></span>  
  
 <span data-ttu-id="69bd8-111">在 ASP.NET client .aspx 页上，定义了一个 DataGrid Web 控件，其中包含服务返回的数据的图形表示形式。</span><span class="sxs-lookup"><span data-stu-id="69bd8-111">On the ASP.NET client .aspx page, a DataGrid Web control is defined, which contains the graphical representation of the data returned by the service.</span></span> <span data-ttu-id="69bd8-112">.Aspx 页上的代码为天气数据调用 WCF 服务，并将数据返回到对象的数组 `WeatherData` 。</span><span class="sxs-lookup"><span data-stu-id="69bd8-112">Code on the .aspx page calls the WCF service for weather data and returns the data to an array of `WeatherData` objects.</span></span> <span data-ttu-id="69bd8-113">DataGrid 通过将它的 `DataSource` 属性设置为该数组来指定从何处获取数据。</span><span class="sxs-lookup"><span data-stu-id="69bd8-113">The DataGrid specifies where to get its data from by setting its `DataSource` property to that array.</span></span> <span data-ttu-id="69bd8-114">数据绑定通过调用 DataGrid 的 `DataBind` 方法发生。</span><span class="sxs-lookup"><span data-stu-id="69bd8-114">The data binding occurs with a call to the DataGrid's `DataBind` method.</span></span> <span data-ttu-id="69bd8-115">所有此代码都包含在中。`aspx`</span><span class="sxs-lookup"><span data-stu-id="69bd8-115">All of this code is contained inside the .`aspx`</span></span> <span data-ttu-id="69bd8-116">页的 `Page_Load` 方法，因此，每次用户刷新浏览器页时，数据都会在 DataGrid 中更新。</span><span class="sxs-lookup"><span data-stu-id="69bd8-116">page's `Page_Load` method, so every time the user refreshes the browser page, the data is updated in the DataGrid.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="69bd8-117">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="69bd8-117">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="69bd8-118">确保已对 [Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="69bd8-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="69bd8-119">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="69bd8-119">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="69bd8-120">本示例的客户端是运行在开发 Web 服务器下的网站。</span><span class="sxs-lookup"><span data-stu-id="69bd8-120">This sample's client is a Web site that runs under a development Web server.</span></span> <span data-ttu-id="69bd8-121">若要启动开发 Web 服务器，请在命令提示符下键入以下命令： `%SystemDrive%\Program Files\Common Files\Microsoft Shared\DevServer\9.0\WebDev.WebServer.EXE" /port:8000 /path:<WebFormsSamplePath>\CS\client /vpath:/client` 。</span><span class="sxs-lookup"><span data-stu-id="69bd8-121">To launch the development Web server, type the following at the command prompt: `%SystemDrive%\Program Files\Common Files\Microsoft Shared\DevServer\9.0\WebDev.WebServer.EXE" /port:8000 /path:<WebFormsSamplePath>\CS\client /vpath:/client`.</span></span> <span data-ttu-id="69bd8-122">然后浏览到 `http://localhost:8000/client` 。</span><span class="sxs-lookup"><span data-stu-id="69bd8-122">Then browse to `http://localhost:8000/client`.</span></span> <span data-ttu-id="69bd8-123">若要跨计算机运行此示例，请在客户端的 Web.config 文件中将所有对 `localhost` 的引用替换为服务器的计算机名称。</span><span class="sxs-lookup"><span data-stu-id="69bd8-123">To run this sample across computers, replace all references to `localhost` in the client's Web.config file with the computer name of the server.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="69bd8-124">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="69bd8-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="69bd8-125">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="69bd8-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="69bd8-126">如果此目录不存在，请参阅[Windows Communication Foundation (wcf) ，并 Windows Workflow Foundation (的 WF](https://www.microsoft.com/download/details.aspx?id=21459)) .NET Framework Windows Communication Foundation ([!INCLUDE[wf1](../../../../includes/wf1-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69bd8-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="69bd8-127">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="69bd8-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WebForms`
