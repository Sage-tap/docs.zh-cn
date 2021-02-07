---
description: 了解详细信息： SQL 跟踪
title: SQL 跟踪
ms.date: 03/30/2017
ms.assetid: bcaebeb1-b9e5-49e8-881b-e49af66fd341
ms.openlocfilehash: 2b336839b9c63c0b7bde8b6451add00cb353fec6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741739"
---
# <a name="sql-tracking"></a><span data-ttu-id="7bcfa-103">SQL 跟踪</span><span class="sxs-lookup"><span data-stu-id="7bcfa-103">SQL tracking</span></span>

<span data-ttu-id="7bcfa-104">此示例演示如何编写一个自定义 SQL 跟踪参与者，该参与者将跟踪记录写入 SQL 数据库。</span><span class="sxs-lookup"><span data-stu-id="7bcfa-104">This sample demonstrates how to write a custom SQL tracking participant that writes tracking records to a SQL database.</span></span> <span data-ttu-id="7bcfa-105">Windows Workflow Foundation (WF) 提供工作流跟踪，以查看工作流实例的执行情况。</span><span class="sxs-lookup"><span data-stu-id="7bcfa-105">Windows Workflow Foundation (WF) provides workflow tracking to gain visibility into the execution of a workflow instance.</span></span> <span data-ttu-id="7bcfa-106">跟踪运行时在工作流执行过程中会发出工作流跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="7bcfa-106">The tracking runtime emits workflow tracking records during the execution of the workflow.</span></span> <span data-ttu-id="7bcfa-107">有关工作流跟踪的详细信息，请参阅 [工作流跟踪和跟踪](../workflow-tracking-and-tracing.md)。</span><span class="sxs-lookup"><span data-stu-id="7bcfa-107">For more information about workflow tracking, see [Workflow Tracking and Tracing](../workflow-tracking-and-tracing.md).</span></span>

## <a name="use-the-sample"></a><span data-ttu-id="7bcfa-108">使用示例</span><span class="sxs-lookup"><span data-stu-id="7bcfa-108">Use the sample</span></span>

1. <span data-ttu-id="7bcfa-109">确认您已安装 SQL Server 2008、 SQL Server 2008 Express 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="7bcfa-109">Verify you have SQL Server 2008, SQL Server 2008 Express or newer installed.</span></span> <span data-ttu-id="7bcfa-110">与示例打包在一起的脚本假定在您的本地计算机上使用 SQL Express 实例。</span><span class="sxs-lookup"><span data-stu-id="7bcfa-110">The scripts packaged with the sample assume the use of a SQL Express instance on your local computer.</span></span> <span data-ttu-id="7bcfa-111">如果您安装了不同的实例，请在运行此示例之前修改与数据库相关的脚本。</span><span class="sxs-lookup"><span data-stu-id="7bcfa-111">If you have a different instance please modify the database-related scripts before running the sample.</span></span>

2. <span data-ttu-id="7bcfa-112">通过在脚本目录 (\WF\Basic\Tracking\SqlTracking\CS\Scripts) 中运行 Trackingsetup.cmd 来创建 SQL Server 跟踪数据库。</span><span class="sxs-lookup"><span data-stu-id="7bcfa-112">Create the SQL Server tracking database by running Trackingsetup.cmd in the scripts directory (\WF\Basic\Tracking\SqlTracking\CS\Scripts).</span></span> <span data-ttu-id="7bcfa-113">这会创建一个名为 TrackingSample 的数据库。</span><span class="sxs-lookup"><span data-stu-id="7bcfa-113">This creates a database called TrackingSample.</span></span>

   > [!NOTE]
   > <span data-ttu-id="7bcfa-114">脚本将在 SQL Express 的默认实例上创建该数据库。</span><span class="sxs-lookup"><span data-stu-id="7bcfa-114">The script creates the database on the default instance of SQL Express.</span></span> <span data-ttu-id="7bcfa-115">如果您想在不同的数据库实例上安装该数据库，请编辑 Trackingsetup.cmd 脚本。</span><span class="sxs-lookup"><span data-stu-id="7bcfa-115">If you want to install it on a different database instance, edit the Trackingsetup.cmd script.</span></span>

3. <span data-ttu-id="7bcfa-116">在 Visual Studio 2010 中打开 SqlTrackingSample。</span><span class="sxs-lookup"><span data-stu-id="7bcfa-116">Open SqlTrackingSample.sln in Visual Studio 2010.</span></span>

4. <span data-ttu-id="7bcfa-117">按 **Ctrl** + **Shift** + **B** 生成解决方案。</span><span class="sxs-lookup"><span data-stu-id="7bcfa-117">Press **Ctrl**+**Shift**+**B** to build the solution.</span></span>

5. <span data-ttu-id="7bcfa-118">按 **F5** 运行该应用程序。</span><span class="sxs-lookup"><span data-stu-id="7bcfa-118">Press **F5** to run the application.</span></span>

   <span data-ttu-id="7bcfa-119">浏览器窗口打开和显示侦听应用程序的目录。</span><span class="sxs-lookup"><span data-stu-id="7bcfa-119">The browser window opens and shows the directory listing for the application.</span></span>

6. <span data-ttu-id="7bcfa-120">在浏览器中，单击 StockPriceService.xamlx。</span><span class="sxs-lookup"><span data-stu-id="7bcfa-120">In the browser, click StockPriceService.xamlx.</span></span>

7. <span data-ttu-id="7bcfa-121">浏览器显示 StockPriceService 页，其中包含本地服务 WSDL 地址。</span><span class="sxs-lookup"><span data-stu-id="7bcfa-121">The browser displays the StockPriceService page, which contains the local service WSDL address.</span></span> <span data-ttu-id="7bcfa-122">复制此地址。</span><span class="sxs-lookup"><span data-stu-id="7bcfa-122">Copy this address.</span></span>

   <span data-ttu-id="7bcfa-123">本地服务 WSDL 地址的示例为 `http://localhost:65193/StockPriceService.xamlx?wsdl` 。</span><span class="sxs-lookup"><span data-stu-id="7bcfa-123">An example of the local service WSDL address is `http://localhost:65193/StockPriceService.xamlx?wsdl`.</span></span>

8. <span data-ttu-id="7bcfa-124">使用文件资源管理器 ( # A0) 运行 WCF 测试客户端。</span><span class="sxs-lookup"><span data-stu-id="7bcfa-124">Using File Explorer, run the WCF test client (WcfTestClient.exe).</span></span> <span data-ttu-id="7bcfa-125">它位于 *Microsoft Visual Studio 10.0 \ Common7\IDE 目录* 中。</span><span class="sxs-lookup"><span data-stu-id="7bcfa-125">It's located in the *Microsoft Visual Studio 10.0\Common7\IDE directory*.</span></span>

9. <span data-ttu-id="7bcfa-126">在 WCF 测试客户端中，单击 " **文件** " 菜单，然后选择 " **添加服务**"。</span><span class="sxs-lookup"><span data-stu-id="7bcfa-126">In the WCF test client, click the **File** menu and select **Add Service**.</span></span> <span data-ttu-id="7bcfa-127">将本地服务地址粘贴到文本框中。</span><span class="sxs-lookup"><span data-stu-id="7bcfa-127">Paste the local service address in the textbox.</span></span> <span data-ttu-id="7bcfa-128">单击 **“确定”**，关闭对话框。</span><span class="sxs-lookup"><span data-stu-id="7bcfa-128">Click **OK** to close the dialog.</span></span>

10. <span data-ttu-id="7bcfa-129">在 WCF 测试客户端中，双击 " **GetStockPrice**"。</span><span class="sxs-lookup"><span data-stu-id="7bcfa-129">In the WCF test client, double click **GetStockPrice**.</span></span> <span data-ttu-id="7bcfa-130">这会打开 `GetStockPrice` 采用一个参数的操作，键入值 `Contoso` 并单击 " **调用**"。</span><span class="sxs-lookup"><span data-stu-id="7bcfa-130">This opens the `GetStockPrice` operation that takes one parameter, type in the value `Contoso` and click **Invoke**.</span></span>

11. <span data-ttu-id="7bcfa-131">发出的跟踪记录将写入一个 SQL 数据库中。</span><span class="sxs-lookup"><span data-stu-id="7bcfa-131">The emitted tracking records are written to a SQL database.</span></span> <span data-ttu-id="7bcfa-132">若要查看跟踪记录，请在 SQL Management Studio 中打开 TrackingSample 数据库，然后导航到表。</span><span class="sxs-lookup"><span data-stu-id="7bcfa-132">To view the tracking records, open the TrackingSample database in SQL Management Studio and navigate to the tables.</span></span> <span data-ttu-id="7bcfa-133">对表运行一个选择查询，将显示存储在相关表中的跟踪记录内的数据。</span><span class="sxs-lookup"><span data-stu-id="7bcfa-133">Running a select query on the tables displays the data within the tracking records stored in the respective tables.</span></span>

   <span data-ttu-id="7bcfa-134">有关 SQL Server Management Studio 的详细信息，请参阅 [SQL Server Management Studio 简介](/sql/ssms/sql-server-management-studio-ssms)。</span><span class="sxs-lookup"><span data-stu-id="7bcfa-134">For more information about SQL Server Management Studio, see [Introducing SQL Server Management Studio](/sql/ssms/sql-server-management-studio-ssms).</span></span> <span data-ttu-id="7bcfa-135">[在此处](https://aka.ms/ssmsfullsetup)下载 SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="7bcfa-135">Download SQL Server Management Studio [here](https://aka.ms/ssmsfullsetup).</span></span>

## <a name="uninstall-the-sample"></a><span data-ttu-id="7bcfa-136">卸载示例</span><span class="sxs-lookup"><span data-stu-id="7bcfa-136">Uninstall the sample</span></span>

1. <span data-ttu-id="7bcfa-137">在示例目录中运行 theTrackingcleanup 脚本 (*\WF\Basic\Tracking\SqlTracking*) 。</span><span class="sxs-lookup"><span data-stu-id="7bcfa-137">Run theTrackingcleanup.cmd script in the sample directory (*\WF\Basic\Tracking\SqlTracking*).</span></span>

    > [!NOTE]
    > <span data-ttu-id="7bcfa-138">Trackingcleanup.cmd 将尝试删除本地计算机 SQL Express 中的数据库。</span><span class="sxs-lookup"><span data-stu-id="7bcfa-138">The Trackingcleanup.cmd attempts to delete the database in your local computer SQL Express.</span></span> <span data-ttu-id="7bcfa-139">如果您使用的是其他 SQL Server 实例，请编辑 Trackingcleanup.cmd。</span><span class="sxs-lookup"><span data-stu-id="7bcfa-139">If you are using another SQL server instance, edit Trackingcleanup.cmd.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7bcfa-140">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="7bcfa-140">The samples may already be installed on your computer.</span></span> <span data-ttu-id="7bcfa-141">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="7bcfa-141">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="7bcfa-142">如果此目录不存在，请参阅[Windows Communication Foundation (wcf) ，并 Windows Workflow Foundation (的 WF](https://www.microsoft.com/download/details.aspx?id=21459)) .NET Framework Windows Communication Foundation ([!INCLUDE[wf1](../../../../includes/wf1-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bcfa-142">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7bcfa-143">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="7bcfa-143">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\SqlTracking`

## <a name="see-also"></a><span data-ttu-id="7bcfa-144">请参阅</span><span class="sxs-lookup"><span data-stu-id="7bcfa-144">See also</span></span>

- <span data-ttu-id="7bcfa-145">[AppFabric 监视示例](/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="7bcfa-145">[AppFabric Monitoring Samples](/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
