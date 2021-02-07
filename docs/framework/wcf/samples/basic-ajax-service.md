---
description: 了解更多：基本 AJAX 服务
title: 基本 AJAX 服务
ms.date: 03/30/2017
ms.assetid: d66d0c91-0109-45a0-a901-f3e4667c2465
ms.openlocfilehash: 08670c0e87a6f258d29288e2072cd04dd875088a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99732717"
---
# <a name="basic-ajax-service"></a><span data-ttu-id="11225-103">基本 AJAX 服务</span><span class="sxs-lookup"><span data-stu-id="11225-103">Basic AJAX Service</span></span>

<span data-ttu-id="11225-104">此示例演示如何使用 Windows Communication Foundation (WCF) 创建 ASP.NET 的基本的异步 JavaScript 和 XML (AJAX) service (可使用 Web 浏览器客户端中的 JavaScript 代码访问的服务) 。</span><span class="sxs-lookup"><span data-stu-id="11225-104">This sample demonstrates how to use Windows Communication Foundation (WCF) to create a basic ASP.NET Asynchronous JavaScript and XML (AJAX) service (a service that you can access using JavaScript code from a Web browser client).</span></span> <span data-ttu-id="11225-105">该服务使用 <xref:System.ServiceModel.Web.WebGetAttribute> 属性以确保服务响应 HTTP GET 请求并被配置为对响应使用 JavaScript 对象表示法 (JSON) 数据格式。</span><span class="sxs-lookup"><span data-stu-id="11225-105">The service uses the <xref:System.ServiceModel.Web.WebGetAttribute> attribute to ensure that the service responds to HTTP GET requests and is configured to use the JavaScript Object Notation (JSON) data format for responses.</span></span>

<span data-ttu-id="11225-106">WCF 中的 AJAX 支持经过优化，可在控件中与 ASP.NET AJAX 一起使用 `ScriptManager` 。</span><span class="sxs-lookup"><span data-stu-id="11225-106">AJAX support in WCF is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="11225-107">有关将 WCF 与 ASP.NET AJAX 一起使用的示例，请参阅 [Ajax 示例](ajax.md)。</span><span class="sxs-lookup"><span data-stu-id="11225-107">For an example of using WCF with ASP.NET AJAX, see the [AJAX Samples](ajax.md).</span></span>

> [!NOTE]
> <span data-ttu-id="11225-108">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="11225-108">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="11225-109">在下面的代码中，将 <xref:System.ServiceModel.Web.WebGetAttribute> 属性应用于 `Add` 操作以确保服务响应 HTTP GET 请求。</span><span class="sxs-lookup"><span data-stu-id="11225-109">In the following code, the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is applied to the `Add` operation to ensure that the service responds to HTTP GET requests.</span></span> <span data-ttu-id="11225-110">为了简单起见，该代码使用 GET（你可以从任何 Web 浏览器构造 HTTP GET 请求）。</span><span class="sxs-lookup"><span data-stu-id="11225-110">The code uses GET for simplicity (you can construct an HTTP GET request from any Web browser).</span></span> <span data-ttu-id="11225-111">也可以使用 GET 来启用缓存。</span><span class="sxs-lookup"><span data-stu-id="11225-111">You can also use GET to enable caching.</span></span> <span data-ttu-id="11225-112">在缺少 `WebGetAttribute` 属性时，HTTP POST 是默认属性。</span><span class="sxs-lookup"><span data-stu-id="11225-112">HTTP POST is the default in the absence of the `WebGetAttribute` attribute.</span></span>

```csharp
[ServiceContract(Namespace = "SimpleAjaxService")]
public interface ICalculator
{
    [WebGet]
    double Add(double n1, double n2);
    //Other operations omitted…
}
```

<span data-ttu-id="11225-113">示例 .svc 文件使用的是 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>，后者会将 <xref:System.ServiceModel.Description.WebScriptEndpoint> 标准终结点添加到服务。</span><span class="sxs-lookup"><span data-stu-id="11225-113">The sample .svc file uses <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, which adds a <xref:System.ServiceModel.Description.WebScriptEndpoint> standard endpoint to the service.</span></span> <span data-ttu-id="11225-114">可在相对于 .svc 文件的空地址处配置该终结点。</span><span class="sxs-lookup"><span data-stu-id="11225-114">The endpoint is configured at an empty address relative to the .svc file.</span></span> <span data-ttu-id="11225-115">这意味着服务的地址是 `http://localhost/ServiceModelSamples/service.svc` ，除操作名称外没有其他后缀。</span><span class="sxs-lookup"><span data-stu-id="11225-115">This means that the address of the service is `http://localhost/ServiceModelSamples/service.svc`, with no additional suffixes other than the operation name.</span></span>

`<%@ServiceHost language="C#" Debug="true" Service="Microsoft.Samples.SimpleAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory" %>`

<span data-ttu-id="11225-116">将对 <xref:System.ServiceModel.Description.WebScriptEndpoint> 进行预配置，以便能从 ASP.NET AJAX 客户端页访问服务。</span><span class="sxs-lookup"><span data-stu-id="11225-116">The <xref:System.ServiceModel.Description.WebScriptEndpoint> is pre-configured to make the service accessible from an ASP.NET AJAX client page.</span></span> <span data-ttu-id="11225-117">可以使用 Web.config 中的以下节对终结点进行其他配置更改。</span><span class="sxs-lookup"><span data-stu-id="11225-117">The following section in Web.config can be used to make additional configuration changes to the endpoint.</span></span> <span data-ttu-id="11225-118">如果不需要额外更改，则可以移除该节。</span><span class="sxs-lookup"><span data-stu-id="11225-118">It can be removed if no extra changes are required.</span></span>

```xml
<system.serviceModel>
  <standardEndpoints>
    <webScriptEndpoint>
      <!-- Use this element to configure the endpoint -->
      <standardEndpoint name=""  />
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```

<span data-ttu-id="11225-119"><xref:System.ServiceModel.Description.WebScriptEndpoint> 将服务的默认数据格式设置为 JSON 而不是 XML。</span><span class="sxs-lookup"><span data-stu-id="11225-119">The <xref:System.ServiceModel.Description.WebScriptEndpoint> sets the default data format for the service to JSON instead of XML.</span></span> <span data-ttu-id="11225-120">若要调用服务，请在 `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` 完成本主题后面的设置和生成步骤后导航到。</span><span class="sxs-lookup"><span data-stu-id="11225-120">To invoke the service, navigate to `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` after completing the set up and build steps shown later in this topic.</span></span> <span data-ttu-id="11225-121">这个测试功能是通过使用 HTTP GET 请求实现的。</span><span class="sxs-lookup"><span data-stu-id="11225-121">This testing functionality is enabled by the use of a HTTP GET request.</span></span>

<span data-ttu-id="11225-122">客户端 Web 页 SimpleAjaxClientPage.aspx 包含 ASP.NET 代码，无论何时用户单击该页面上的操作按钮之一，就能调用服务。</span><span class="sxs-lookup"><span data-stu-id="11225-122">The client Web page SimpleAjaxClientPage.aspx contains ASP.NET code to invoke the service whenever the user clicks one of the operation buttons on the page.</span></span> <span data-ttu-id="11225-123">`ScriptManager` 控件用于使服务的代理可以通过 JavaScript 访问。</span><span class="sxs-lookup"><span data-stu-id="11225-123">The `ScriptManager` control is used to make a proxy to the service accessible through JavaScript.</span></span>

```aspx-csharp
<asp:ScriptManager ID="ScriptManager" runat="server">
    <Services>
        <asp:ServiceReference Path="service.svc" />
    </Services>
</asp:ScriptManager>
```

<span data-ttu-id="11225-124">使用以下 JavaScript 代码实例化本地代理和调用操作。</span><span class="sxs-lookup"><span data-stu-id="11225-124">The local proxy is instantiated and operations are invoked using the following JavaScript code.</span></span>

```javascript
// Code for extracting arguments n1 and n2 omitted…
// Instantiate a service proxy
var proxy = new SimpleAjaxService.ICalculator();
// Code for selecting operation omitted…
proxy.Add(parseFloat(n1), parseFloat(n2), onSuccess, onFail, null);
```

<span data-ttu-id="11225-125">如果服务调用成功，则代码调用 `onSuccess` 处理程序并在文本框中显示操作结果。</span><span class="sxs-lookup"><span data-stu-id="11225-125">If the service call succeeds, the code invokes the `onSuccess` handler and the result of the operation is displayed in a text box.</span></span>

```javascript
function onSuccess(mathResult){
     document.getElementById("result").value = mathResult;
}
```

> [!IMPORTANT]
> <span data-ttu-id="11225-126">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="11225-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="11225-127">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="11225-127">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="11225-128">如果此目录不存在，请参阅[Windows Communication Foundation (wcf) ，并 Windows Workflow Foundation (的 WF](https://www.microsoft.com/download/details.aspx?id=21459)) .NET Framework Windows Communication Foundation ([!INCLUDE[wf1](../../../../includes/wf1-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11225-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="11225-129">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="11225-129">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\SimpleAjaxService`
