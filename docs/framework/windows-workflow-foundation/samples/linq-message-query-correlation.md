---
description: 了解更多相关信息： LINQ 消息查询相关性
title: LINQ 消息查询相关性
ms.date: 03/30/2017
ms.assetid: b746872e-57b1-4514-b337-53398a0e0deb
ms.openlocfilehash: 7b979e3bdc2c0ede8f4f9d4595957f90581a0ecc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755273"
---
# <a name="linq-message-query-correlation"></a><span data-ttu-id="c27d1-103">LINQ 消息查询相关性</span><span class="sxs-lookup"><span data-stu-id="c27d1-103">LINQ Message Query Correlation</span></span>

<span data-ttu-id="c27d1-104">此示例演示如何使用一个与系统提供的 <xref:System.ServiceModel.Dispatcher.MessageQuery> 相对的自定义 <xref:System.ServiceModel.XPathMessageQuery> 实现，执行基于内容的相关性。</span><span class="sxs-lookup"><span data-stu-id="c27d1-104">This sample demonstrates how to do content-based correlation using a custom <xref:System.ServiceModel.Dispatcher.MessageQuery> implementation as opposed to the system-provided <xref:System.ServiceModel.XPathMessageQuery>.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="c27d1-105">演示</span><span class="sxs-lookup"><span data-stu-id="c27d1-105">Demonstrates</span></span>  

 <span data-ttu-id="c27d1-106">自定义 <xref:System.ServiceModel.Dispatcher.MessageQuery>，基于内容的相关性。</span><span class="sxs-lookup"><span data-stu-id="c27d1-106">Custom <xref:System.ServiceModel.Dispatcher.MessageQuery>, Content-Based Correlation.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="c27d1-107">讨论 (Discussion)</span><span class="sxs-lookup"><span data-stu-id="c27d1-107">Discussion</span></span>  

 <span data-ttu-id="c27d1-108">此示例演示如何出于相关性的目的从 <xref:System.ServiceModel.Dispatcher.MessageQuery> 基类进行扩展。</span><span class="sxs-lookup"><span data-stu-id="c27d1-108">This sample shows how to extend from the <xref:System.ServiceModel.Dispatcher.MessageQuery> base class for the purposes of correlation.</span></span> <span data-ttu-id="c27d1-109">自定义实现 `LinqMessageQuery` 允许用户提供一个 XName 以使用 XLinq 在消息中查找。</span><span class="sxs-lookup"><span data-stu-id="c27d1-109">The custom implementation, `LinqMessageQuery`, allows users to provide an XName to find within the message using XLinq.</span></span> <span data-ttu-id="c27d1-110">此查询检索的数据用于构成相关性键，以将消息调度到相应的工作流实例。</span><span class="sxs-lookup"><span data-stu-id="c27d1-110">The data retrieved by the query is used to form the correlation key to dispatch messages to the appropriate workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c27d1-111">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="c27d1-111">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="c27d1-112">此示例使用 HTTP 终结点公开一个工作流服务。</span><span class="sxs-lookup"><span data-stu-id="c27d1-112">This sample exposes a workflow service using HTTP endpoints.</span></span> <span data-ttu-id="c27d1-113">若要运行此示例，必须添加正确的 URL Acl (参阅 [配置 HTTP 和 HTTPS](../../wcf/feature-details/configuring-http-and-https.md) 以获取详细信息) ，方法是以管理员身份运行 Visual Studio，或在提升的提示符下执行以下命令来添加相应的 acl。</span><span class="sxs-lookup"><span data-stu-id="c27d1-113">To run this sample, proper URL ACLs must be added (see [Configuring HTTP and HTTPS](../../wcf/feature-details/configuring-http-and-https.md) for details), either by running Visual Studio as Administrator or by executing the following command at an elevated prompt to add the appropriate ACLs.</span></span> <span data-ttu-id="c27d1-114">确保替换了域和用户名。</span><span class="sxs-lookup"><span data-stu-id="c27d1-114">Ensure that your Domain and Username are substituted.</span></span>  
  
    ```console  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2. <span data-ttu-id="c27d1-115">在添加 URL ACL 后，请使用下列步骤。</span><span class="sxs-lookup"><span data-stu-id="c27d1-115">Once the URL ACLs are added, use the following steps.</span></span>  
  
    1. <span data-ttu-id="c27d1-116">生成解决方案。</span><span class="sxs-lookup"><span data-stu-id="c27d1-116">Build the solution.</span></span>  
  
    2. <span data-ttu-id="c27d1-117">通过右键单击解决方案并选择 " **设置启动项目**" 来设置多个启动项目。</span><span class="sxs-lookup"><span data-stu-id="c27d1-117">Set multiple start-up projects by right-clicking the solution and selecting **Set Startup Projects**.</span></span> <span data-ttu-id="c27d1-118">将 **服务** 和 **客户端** (按顺序添加) 为多个启动项目。</span><span class="sxs-lookup"><span data-stu-id="c27d1-118">Add **Service** and **Client** (in that order) as multiple start-up projects.</span></span>  
  
    3. <span data-ttu-id="c27d1-119">运行应用程序。</span><span class="sxs-lookup"><span data-stu-id="c27d1-119">Run the application.</span></span> <span data-ttu-id="c27d1-120">客户端控制台演示工作流如何发送订单、接收订购单 ID 以及随后确认订单。</span><span class="sxs-lookup"><span data-stu-id="c27d1-120">The client console shows a workflow  sending an order and receiving the purchase order id and then subsequently confirming the order.</span></span> <span data-ttu-id="c27d1-121">服务窗口将显示正在处理的请求。</span><span class="sxs-lookup"><span data-stu-id="c27d1-121">The Service window will show the requests being processed.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c27d1-122">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="c27d1-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c27d1-123">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="c27d1-123">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="c27d1-124">如果此目录不存在，请参阅[Windows Communication Foundation (wcf) ，并 Windows Workflow Foundation (的 WF](https://www.microsoft.com/download/details.aspx?id=21459)) .NET Framework Windows Communication Foundation ([!INCLUDE[wf1](../../../../includes/wf1-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c27d1-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c27d1-125">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="c27d1-125">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\LinqMessageQueryCorrelation`
