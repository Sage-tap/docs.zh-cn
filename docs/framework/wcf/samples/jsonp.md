---
description: 了解详细信息： JSONP
title: JSONP
ms.date: 03/30/2017
ms.assetid: c13b4d7b-dac7-4ffd-9f84-765c903511e1
ms.openlocfilehash: 83236f3d40a9dfeaf2ab0e521a227fb6dfc461f6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726333"
---
# <a name="jsonp"></a><span data-ttu-id="b7b13-103">JSONP</span><span class="sxs-lookup"><span data-stu-id="b7b13-103">JSONP</span></span>

<span data-ttu-id="b7b13-104">本示例演示在 WCF REST 服务中如何支持 JSON with Padding (JSONP)。</span><span class="sxs-lookup"><span data-stu-id="b7b13-104">This sample demonstrates how to support JSON with Padding (JSONP) in WCF REST services.</span></span> <span data-ttu-id="b7b13-105">JSONP 是通过在当前文档中生成脚本标记来调用跨域脚本时使用的约定。</span><span class="sxs-lookup"><span data-stu-id="b7b13-105">JSONP is a convention used to invoke cross-domain scripts by generating script tags in the current document.</span></span> <span data-ttu-id="b7b13-106">结果在指定的回调函数中返回。</span><span class="sxs-lookup"><span data-stu-id="b7b13-106">The result is returned in a specified callback function.</span></span> <span data-ttu-id="b7b13-107">JSONP 基于这一构想，如 `<script src="http://..." >` 可以从任何域评估脚本，而这些标记检索的脚本在可能已经定义了其他函数的范围内进行评估。</span><span class="sxs-lookup"><span data-stu-id="b7b13-107">JSONP is based on the idea that tags such as `<script src="http://..." >` can evaluate scripts from any domain and the script retrieved by those tags is evaluated within a scope in which other functions may already be defined.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="b7b13-108">演示</span><span class="sxs-lookup"><span data-stu-id="b7b13-108">Demonstrates</span></span>

 <span data-ttu-id="b7b13-109">使用 JSONP 进行跨域脚本编写。</span><span class="sxs-lookup"><span data-stu-id="b7b13-109">Cross-domain scripting with JSONP.</span></span>

## <a name="discussion"></a><span data-ttu-id="b7b13-110">讨论 (Discussion)</span><span class="sxs-lookup"><span data-stu-id="b7b13-110">Discussion</span></span>

 <span data-ttu-id="b7b13-111">本示例包含一个网页，该网页在页面呈现在浏览器中后动态添加脚本块。</span><span class="sxs-lookup"><span data-stu-id="b7b13-111">The sample includes a Web page that dynamically adds a script block after the page has been rendered in the browser.</span></span> <span data-ttu-id="b7b13-112">此脚本块调用一个 WCF REST 服务，该服务有一个 `GetCustomer` 操作。</span><span class="sxs-lookup"><span data-stu-id="b7b13-112">This script block calls a WCF REST service that has a single operation, `GetCustomer`.</span></span> <span data-ttu-id="b7b13-113">WCF REST 服务返回包装在回调函数名内的客户名称和地址。</span><span class="sxs-lookup"><span data-stu-id="b7b13-113">The WCF REST service returns a customer’s name and address wrapped in a callback function name.</span></span> <span data-ttu-id="b7b13-114">当 WCF REST 服务响应时，会使用客户数据调用网页上的回调函数，该回调函数会在网页上显示数据。</span><span class="sxs-lookup"><span data-stu-id="b7b13-114">When the WCF REST service responds, the callback function on the Web page is invoked with the customer data and the callback function displays the data on the Web page.</span></span> <span data-ttu-id="b7b13-115">脚本标记的注入和回调函数的执行由 ASP.NET AJAX ScriptManager 控件自动处理。</span><span class="sxs-lookup"><span data-stu-id="b7b13-115">The injection of the script tag and the execution of the callback function is automatically handled by the ASP.NET AJAX ScriptManager control.</span></span> <span data-ttu-id="b7b13-116">使用模式与所有 ASP.NET AJAX 代理相同，只是多了一行用于启用 JSONP 的代码，如下面的代码所示：</span><span class="sxs-lookup"><span data-stu-id="b7b13-116">The usage pattern is the same as with all ASP.NET AJAX proxies, with the addition of one line to enable JSONP, as shown in the following code:</span></span>

```csharp
var proxy = new JsonpAjaxService.CustomerService();
proxy.set_enableJsonp(true);
proxy.GetCustomer(onSuccess, onFail, null);
```

 <span data-ttu-id="b7b13-117">网页可以调用 WCF REST 服务，因为该服务使用 <xref:System.ServiceModel.Description.WebScriptEndpoint> 且 `crossDomainScriptAccessEnabled` 设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="b7b13-117">The Web page can call the WCF REST service because the service is using the <xref:System.ServiceModel.Description.WebScriptEndpoint> with `crossDomainScriptAccessEnabled` set to `true`.</span></span> <span data-ttu-id="b7b13-118">这两个配置都在元素下的 Web.config 文件中完成 \<system.serviceModel> 。</span><span class="sxs-lookup"><span data-stu-id="b7b13-118">Both of these configurations are done in the Web.config file under the \<system.serviceModel> element.</span></span>

```xml
<system.serviceModel>
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint name="" crossDomainScriptAccessEnabled="true"/>
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```

 <span data-ttu-id="b7b13-119">ScriptManager 管理与服务的交互并隐藏手动实现 JSONP 访问的复杂性。</span><span class="sxs-lookup"><span data-stu-id="b7b13-119">ScriptManager manages the interaction with the service and hides away the complexity of manually implementing JSONP access.</span></span> <span data-ttu-id="b7b13-120">当 `crossDomainScriptAccessEnabled` 设置为 `true` 并且操作的响应格式为 JSON 时，WCF 基础结构将检查回调查询字符串参数的请求 URI，并使用回调查询字符串参数的值包装 JSON 响应。</span><span class="sxs-lookup"><span data-stu-id="b7b13-120">When `crossDomainScriptAccessEnabled` is set to `true` and the response format for an operation is JSON, the WCF infrastructure inspects the URI of the request for a callback query string parameter and wraps the JSON response with the value of the callback query string parameter.</span></span> <span data-ttu-id="b7b13-121">在本示例中，网页使用以下 URI 调用 WCF REST 服务。</span><span class="sxs-lookup"><span data-stu-id="b7b13-121">In the sample, the Web page calls the WCF REST service with the following URI.</span></span>

```http
http://localhost:33695/CustomerService/GetCustomer?callback=Sys._json0
```

 <span data-ttu-id="b7b13-122">因为回调查询字符串参数的值为 `JsonPCallback`，所以 WCF 服务返回如下面的示例所示的 JSONP 响应。</span><span class="sxs-lookup"><span data-stu-id="b7b13-122">Because the callback query string parameter has a value of `JsonPCallback`, the WCF service returns a JSONP response shown in the following example.</span></span>

```json
Sys._json0({"__type":"Customer:#Microsoft.Samples.Jsonp","Address":"1 Example Way","Name":"Bob"});
```

 <span data-ttu-id="b7b13-123">此 JSONP 响应包含 JSON 格式的客户数据（使用网页请求的回调函数名进行包装）。</span><span class="sxs-lookup"><span data-stu-id="b7b13-123">This JSONP response includes the customer data formatted as JSON, wrapped with the callback function name that the Web page requested.</span></span> <span data-ttu-id="b7b13-124">ScriptManager 将使用脚本标记执行此回调以完成跨域请求，然后将结果传递给 onSuccess 处理程序，该处理程序会传递给 ASP.NET AJAX 代理的 GetCustomer 操作。</span><span class="sxs-lookup"><span data-stu-id="b7b13-124">ScriptManager will execute this callback using a script tag to accomplish the cross-domain request, and then pass the result to the onSuccess handler that was passed to the GetCustomer operation of the ASP.NET AJAX proxy.</span></span>

 <span data-ttu-id="b7b13-125">此示例由两个 ASP.NET web 应用程序组成：一个只包含一个 WCF 服务，另一个包含调用该服务的 .aspx 网页。</span><span class="sxs-lookup"><span data-stu-id="b7b13-125">The sample consists of two ASP.NET web applications: one contains just a WCF service, and another one contains the .aspx webpage, which calls the service.</span></span> <span data-ttu-id="b7b13-126">运行解决方案时，Visual Studio 2012 将在不同的端口上托管两个网站，这将创建一个环境，其中的服务和客户端位于不同的域。</span><span class="sxs-lookup"><span data-stu-id="b7b13-126">When running the solution, Visual Studio 2012 will host the two websites on different ports, which creates an environment where the service and client live on different domains.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b7b13-127">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="b7b13-127">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b7b13-128">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="b7b13-128">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="b7b13-129">如果此目录不存在，请参阅[Windows Communication Foundation (wcf) ，并 Windows Workflow Foundation (的 WF](https://www.microsoft.com/download/details.aspx?id=21459)) .NET Framework Windows Communication Foundation ([!INCLUDE[wf1](../../../../includes/wf1-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7b13-129">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b7b13-130">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="b7b13-130">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\JSONP`  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="b7b13-131">运行示例</span><span class="sxs-lookup"><span data-stu-id="b7b13-131">To run the sample</span></span>  
  
1. <span data-ttu-id="b7b13-132">打开 JSONP 示例的解决方案。</span><span class="sxs-lookup"><span data-stu-id="b7b13-132">Open the solution for the JSONP Sample.</span></span>  
  
2. <span data-ttu-id="b7b13-133">按 F5 `http://localhost:26648/JSONPClientPage.aspx` 在浏览器中启动。</span><span class="sxs-lookup"><span data-stu-id="b7b13-133">Press F5 to launch `http://localhost:26648/JSONPClientPage.aspx` in the browser.</span></span>  
  
3. <span data-ttu-id="b7b13-134">请注意，加载页面后，"Name" 和 "Address" 的文本输入由值填充。</span><span class="sxs-lookup"><span data-stu-id="b7b13-134">Notice that after the page loads, the text inputs for "Name" and "Address" are populated by values.</span></span>  <span data-ttu-id="b7b13-135">在浏览器完成页面的呈现后，从对 WCF 服务的调用中提供这些值。</span><span class="sxs-lookup"><span data-stu-id="b7b13-135">These values were supplied from a call to the WCF service after the browser finished rendering the page.</span></span>
