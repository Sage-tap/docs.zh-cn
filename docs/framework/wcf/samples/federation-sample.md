---
description: 了解详细信息：联合示例
title: 联合示例
ms.date: 03/30/2017
ms.assetid: 7e9da0ca-e925-4644-aa96-8bfaf649d4bb
ms.openlocfilehash: a85a290988b6cbb4b30a1098f3558ec34ead1d50
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704077"
---
# <a name="federation-sample"></a><span data-ttu-id="2fbb6-103">联合示例</span><span class="sxs-lookup"><span data-stu-id="2fbb6-103">Federation Sample</span></span>

<span data-ttu-id="2fbb6-104">本示例演示联合安全。</span><span class="sxs-lookup"><span data-stu-id="2fbb6-104">This sample demonstrates federated security.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="2fbb6-105">示例详细信息</span><span class="sxs-lookup"><span data-stu-id="2fbb6-105">Sample Details</span></span>  

 <span data-ttu-id="2fbb6-106">Windows Communication Foundation (WCF) 提供对通过部署联合安全体系结构的支持 `wsFederationHttpBinding` 。</span><span class="sxs-lookup"><span data-stu-id="2fbb6-106">Windows Communication Foundation (WCF) provides support for deploying federated security architectures through the `wsFederationHttpBinding`.</span></span> <span data-ttu-id="2fbb6-107">`wsFederationHttpBinding` 提供安全可靠并且可互操作的绑定，该绑定中使用 HTTP 作为请求/回复通信的基础传输机制，并使用文本/XML 作为编码的联网格式。</span><span class="sxs-lookup"><span data-stu-id="2fbb6-107">The `wsFederationHttpBinding` provides a secure, reliable, and interoperable binding that involves the use of HTTP as the underlying transport mechanism for request/reply communication, and Text/XML as the wire format for encoding.</span></span> <span data-ttu-id="2fbb6-108">有关 WCF 中的联合的详细信息，请参阅 [联合](../feature-details/federation.md)。</span><span class="sxs-lookup"><span data-stu-id="2fbb6-108">For more information about Federation in WCF, see [Federation](../feature-details/federation.md).</span></span>  
  
 <span data-ttu-id="2fbb6-109">此方案包括 4 个部分：</span><span class="sxs-lookup"><span data-stu-id="2fbb6-109">The scenario is made up of 4 pieces:</span></span>  
  
- <span data-ttu-id="2fbb6-110">BookStore 服务</span><span class="sxs-lookup"><span data-stu-id="2fbb6-110">BookStore service</span></span>  
  
- <span data-ttu-id="2fbb6-111">BookStore STS</span><span class="sxs-lookup"><span data-stu-id="2fbb6-111">BookStore STS</span></span>  
  
- <span data-ttu-id="2fbb6-112">HomeRealm STS</span><span class="sxs-lookup"><span data-stu-id="2fbb6-112">HomeRealm STS</span></span>  
  
- <span data-ttu-id="2fbb6-113">BookStore 客户端</span><span class="sxs-lookup"><span data-stu-id="2fbb6-113">BookStore Client</span></span>  
  
 <span data-ttu-id="2fbb6-114">BookStore 服务支持两个操作：`BrowseBooks` 和 `BuyBook`。</span><span class="sxs-lookup"><span data-stu-id="2fbb6-114">The BookStore service supports two operations, `BrowseBooks` and `BuyBook`.</span></span> <span data-ttu-id="2fbb6-115">它允许匿名访问 `BrowseBooks` 操作，但需要经过身份验证才能访问 `BuyBooks` 操作。</span><span class="sxs-lookup"><span data-stu-id="2fbb6-115">It allows anonymous access to the `BrowseBooks` operation, but requires authenticated access to access the `BuyBooks` operation.</span></span> <span data-ttu-id="2fbb6-116">身份验证采用由 BookStore STS 颁发的令牌的形式。</span><span class="sxs-lookup"><span data-stu-id="2fbb6-116">The authentication takes the form of a token issued by the BookStore STS.</span></span> <span data-ttu-id="2fbb6-117">BookStore 服务的配置文件使用 `wsFederationHttpBinding` 将客户端指向 BookStore STS。</span><span class="sxs-lookup"><span data-stu-id="2fbb6-117">The configuration file for the BookStore Service points clients to the BookStore STS using the `wsFederationHttpBinding`.</span></span>  
  
```xml  
<wsFederationHttpBinding>  
<!-- This is the Service binding for the BuyBooks endpoint. It redirects clients to the BookStore STS -->  
    <binding name='BuyBookBinding'>  
        <security mode="Message">  
            <message>  
                <issuerMetadata  
  address='http://localhost/FederationSample/BookStoreSTS/STS.svc/mex' >  
                    <identity>  
                        <dns value ='BookStoreSTS.com'/>  
                    </identity>  
                </issuerMetadata>  
            </message>  
        </security>  
    </binding>  
</wsFederationHttpBinding>  
```  
  
 <span data-ttu-id="2fbb6-118">BookStore STS 然后要求客户端使用 HomeRealm STS 颁发的令牌进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="2fbb6-118">The BookStore STS then requires that clients authenticate using a token issued by the HomeRealm STS.</span></span> <span data-ttu-id="2fbb6-119">同样，BookStore STS 的配置文件使用 `wsFederationHttpBinding` 将客户端指向 HomeRealm STS。</span><span class="sxs-lookup"><span data-stu-id="2fbb6-119">Again, the configuration file for the BookStore STS points clients to the HomeRealm STS using the `wsFederationHttpBinding`.</span></span>  
  
```xml  
<wsFederationHttpBinding>  
 <!-- This is the binding for the clients requesting tokens from this STS. It redirects clients to the HomeRealm STS -->  
    <binding name='BookStoreSTSBinding'>  
        <security mode='Message'>  
            <message>  
                <issuerMetadata  
 address='http://localhost/FederationSample/HomeRealmSTS/STS.svc/mex' >  
                    <identity>  
                        <dns value ='HomeRealmSTS.com' />  
                    </identity>  
                </issuerMetadata>  
            </message>  
        </security>  
    </binding>  
</wsFederationHttpBinding>  
```  
  
 <span data-ttu-id="2fbb6-120">访问 `BuyBook` 操作时的事件序列如下：</span><span class="sxs-lookup"><span data-stu-id="2fbb6-120">The sequence of events when accessing the `BuyBook` operation is as follows:</span></span>  
  
1. <span data-ttu-id="2fbb6-121">客户端使用 Windows 凭据向 HomeRealm STS 进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="2fbb6-121">The client authenticates to the HomeRealm STS using Windows credentials.</span></span>  
  
2. <span data-ttu-id="2fbb6-122">HomeRealm STS 颁发一个令牌，该令牌可用于向 BookStore STS 进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="2fbb6-122">The HomeRealm STS issues a token that can be used to authenticate to the BookStore STS.</span></span>  
  
3. <span data-ttu-id="2fbb6-123">客户端使用 HomeRealm STS 颁发的令牌向 BookStore STS 进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="2fbb6-123">The client authenticates to the BookStore STS using the token issued by the HomeRealm STS.</span></span>  
  
4. <span data-ttu-id="2fbb6-124">BookStore STS 颁发一个令牌，该令牌可用于向 BookStore 服务进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="2fbb6-124">The BookStore STS issues a token that can be used to authenticate to the BookStore Service.</span></span>  
  
5. <span data-ttu-id="2fbb6-125">客户端使用 BookStore STS 颁发的令牌向 BookStore 服务进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="2fbb6-125">The client authenticates to the BookStore service using the token issued by the BookStore STS.</span></span>  
  
6. <span data-ttu-id="2fbb6-126">客户端访问 `BuyBook` 操作。</span><span class="sxs-lookup"><span data-stu-id="2fbb6-126">The client accesses the `BuyBook` operation.</span></span>  
  
 <span data-ttu-id="2fbb6-127">有关如何设置和运行此示例的信息，请参见以下说明。</span><span class="sxs-lookup"><span data-stu-id="2fbb6-127">See the following instructions about how to set up and run this sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2fbb6-128">若要运行此示例，您必须具有 **wwwroot** 目录的写入权限。</span><span class="sxs-lookup"><span data-stu-id="2fbb6-128">You must have Write permissions to the **wwwroot** directory to run this sample.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2fbb6-129">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="2fbb6-129">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="2fbb6-130">打开 SDK 命令窗口。</span><span class="sxs-lookup"><span data-stu-id="2fbb6-130">Open the SDK command window.</span></span> <span data-ttu-id="2fbb6-131">在示例路径中运行 Setup.bat。</span><span class="sxs-lookup"><span data-stu-id="2fbb6-131">In the sample path, run Setup.bat.</span></span> <span data-ttu-id="2fbb6-132">这将创建示例所需的虚拟目录，并使用相应的权限安装所需的证书。</span><span class="sxs-lookup"><span data-stu-id="2fbb6-132">This creates the virtual directories required for the sample and installs the required certificates with appropriate permissions.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="2fbb6-133">Setup.bat 批处理文件设计为通过 Windows SDK 命令提示运行。</span><span class="sxs-lookup"><span data-stu-id="2fbb6-133">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="2fbb6-134">这要求 MSSDK 环境变量指向 SDK 的安装目录。</span><span class="sxs-lookup"><span data-stu-id="2fbb6-134">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="2fbb6-135">将在 Windows SDK 命令提示中自动设置此环境变量。</span><span class="sxs-lookup"><span data-stu-id="2fbb6-135">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span> <span data-ttu-id="2fbb6-136">在 Windows Vista 上，必须确保已安装 IIS 6.0 管理兼容性，因为安装程序将使用 IIS 管理员脚本。</span><span class="sxs-lookup"><span data-stu-id="2fbb6-136">On Windows Vista, you must ensure that IIS 6.0 Management Compatibility is installed because the set up uses IIS administrator scripts.</span></span> <span data-ttu-id="2fbb6-137">在 Windows Vista 上运行安装脚本需要管理员权限。</span><span class="sxs-lookup"><span data-stu-id="2fbb6-137">Running the set-up script on Windows Vista requires administrator privileges.</span></span>  
  
2. <span data-ttu-id="2fbb6-138">在 Visual Studio 中打开 FederationSample，并从 "**生成**" 菜单中选择 "**生成解决方案**"。</span><span class="sxs-lookup"><span data-stu-id="2fbb6-138">Open FederationSample.sln in Visual Studio and select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="2fbb6-139">这将生成通用项目文件、Bookstore 服务、Bookstore STS、HomeRealm STS 并将它们部署到 IIS 中。</span><span class="sxs-lookup"><span data-stu-id="2fbb6-139">This builds the common project files, Bookstore service, Bookstore STS, HomeRealm STS, and deploys them in IIS.</span></span> <span data-ttu-id="2fbb6-140">还将生成 Bookstore 客户端应用程序，并将可执行文件 BookStoreClient.exe 放入 FederationSample\BookStoreClient\bin\Debug 文件夹。</span><span class="sxs-lookup"><span data-stu-id="2fbb6-140">This also builds the Bookstore client application and places the executable BookStoreClient.exe in the FederationSample\BookStoreClient\bin\Debug folder.</span></span>  
  
3. <span data-ttu-id="2fbb6-141">双击 BookStoreClient.exe。</span><span class="sxs-lookup"><span data-stu-id="2fbb6-141">Double-click BookStoreClient.exe.</span></span> <span data-ttu-id="2fbb6-142">将显示 BookStoreClient 窗口。</span><span class="sxs-lookup"><span data-stu-id="2fbb6-142">The BookStoreClient window is displayed.</span></span>  
  
4. <span data-ttu-id="2fbb6-143">可以通过单击 " **浏览书籍**" 浏览书店中提供的书籍。</span><span class="sxs-lookup"><span data-stu-id="2fbb6-143">You can browse the books available in the bookstore by clicking **Browse Books**.</span></span>  
  
5. <span data-ttu-id="2fbb6-144">若要购买特定书籍，请在列表中选择该书籍，然后单击 " **购买书籍**"。</span><span class="sxs-lookup"><span data-stu-id="2fbb6-144">To purchase a particular book, select the book in the list and click **Buy Book**.</span></span> <span data-ttu-id="2fbb6-145">该应用程序将启动，并使用 Windows 身份验证和 HomeRealm 安全令牌服务进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="2fbb6-145">The application starts up and authenticates using Windows authentication with the HomeRealm Security Token Service.</span></span>  
  
     <span data-ttu-id="2fbb6-146">此示例配置为允许用户购买价格等于或低于 15 美元的图书。</span><span class="sxs-lookup"><span data-stu-id="2fbb6-146">The sample is configured to allow users to purchase books that cost $15 or less.</span></span> <span data-ttu-id="2fbb6-147">尝试购买价格超过 15 美元的图书将导致客户端从 BookStore 服务获得“拒绝访问”消息。</span><span class="sxs-lookup"><span data-stu-id="2fbb6-147">Attempting to buy books that cost more than $15 results in the client getting an Access Denied message from the Book Store Service.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="2fbb6-148">此示例不会在用户购买图书后更新其信用限额。</span><span class="sxs-lookup"><span data-stu-id="2fbb6-148">The sample does not update the user’s credit limit after a purchase.</span></span> <span data-ttu-id="2fbb6-149">您可以在用户的（固定）信用限额内反复购买图书。</span><span class="sxs-lookup"><span data-stu-id="2fbb6-149">You can repeatedly purchase books within the user’s (fixed) credit limit.</span></span>  
  
#### <a name="to-clean-up"></a><span data-ttu-id="2fbb6-150">清理</span><span class="sxs-lookup"><span data-stu-id="2fbb6-150">To clean up</span></span>  
  
1. <span data-ttu-id="2fbb6-151">运行 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="2fbb6-151">Run Cleanup.bat.</span></span> <span data-ttu-id="2fbb6-152">这将删除安装过程中创建的虚拟目录，并移除安装过程中安装的证书。</span><span class="sxs-lookup"><span data-stu-id="2fbb6-152">This deletes the virtual directories that were created during set up and also removes the certificates installed during setup.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2fbb6-153">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="2fbb6-153">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2fbb6-154">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="2fbb6-154">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="2fbb6-155">如果此目录不存在，请参阅[Windows Communication Foundation (wcf) ，并 Windows Workflow Foundation (的 WF](https://www.microsoft.com/download/details.aspx?id=21459)) .NET Framework Windows Communication Foundation ([!INCLUDE[wf1](../../../../includes/wf1-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2fbb6-155">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2fbb6-156">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="2fbb6-156">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Federation`  
