---
description: 了解更多相关信息：在不 ASP.NET 的情况下创建 WCF AJAX 服务
title: 创建不使用 ASP.NET 的 WCF AJAX 服务
ms.date: 03/30/2017
ms.assetid: ba4a7d1b-e277-4978-9f62-37684e6dc934
ms.openlocfilehash: 98171a67b3dd2f267edf2281396bb0da1858b0b2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705143"
---
# <a name="creating-wcf-ajax-services-without-aspnet"></a><span data-ttu-id="d6a36-103">创建不使用 ASP.NET 的 WCF AJAX 服务</span><span class="sxs-lookup"><span data-stu-id="d6a36-103">Creating WCF AJAX Services without ASP.NET</span></span>

<span data-ttu-id="d6a36-104">Windows Communication Foundation 可以从任何支持 JavaScript 的网页访问 (WCF) AJAX 服务，无需 ASP.NET AJAX。</span><span class="sxs-lookup"><span data-stu-id="d6a36-104">Windows Communication Foundation (WCF) AJAX services can be accessed from any JavaScript-enabled Web page, without requiring ASP.NET AJAX.</span></span> <span data-ttu-id="d6a36-105">本主题介绍如何创建此类 WCF 服务。</span><span class="sxs-lookup"><span data-stu-id="d6a36-105">This topic describes how to create such a WCF service.</span></span>  
  
 <span data-ttu-id="d6a36-106">有关将 WCF 与 ASP.NET AJAX 配合使用的说明，请参阅 [为 ASP.NET Ajax 创建 Wcf 服务](creating-wcf-services-for-aspnet-ajax.md)。</span><span class="sxs-lookup"><span data-stu-id="d6a36-106">For instructions on using WCF with ASP.NET AJAX, see [Creating WCF Services for ASP.NET AJAX](creating-wcf-services-for-aspnet-ajax.md).</span></span>  
  
 <span data-ttu-id="d6a36-107">创建 WCF AJAX 服务有三个部分：</span><span class="sxs-lookup"><span data-stu-id="d6a36-107">There are three parts to a creating a WCF AJAX service:</span></span>  
  
- <span data-ttu-id="d6a36-108">创建一个可以从浏览器中访问的 AJAX 终结点。</span><span class="sxs-lookup"><span data-stu-id="d6a36-108">Creating an AJAX endpoint that can be accessed from the browser.</span></span>  
  
- <span data-ttu-id="d6a36-109">创建一个与 AJAX 兼容的服务协定。</span><span class="sxs-lookup"><span data-stu-id="d6a36-109">Creating an AJAX-compatible service contract.</span></span>  
  
- <span data-ttu-id="d6a36-110">访问 WCF AJAX 服务。</span><span class="sxs-lookup"><span data-stu-id="d6a36-110">Accessing WCF AJAX services.</span></span>  
  
## <a name="creating-an-ajax-endpoint"></a><span data-ttu-id="d6a36-111">创建 AJAX 终结点</span><span class="sxs-lookup"><span data-stu-id="d6a36-111">Creating an AJAX Endpoint</span></span>  

 <span data-ttu-id="d6a36-112">在 WCF 服务中启用 AJAX 支持的最基本方法是 <xref:System.ServiceModel.Activation.WebServiceHostFactory> 在与服务关联的 .svc 文件中使用，如以下示例中所示。</span><span class="sxs-lookup"><span data-stu-id="d6a36-112">The most basic way to enable AJAX support in a WCF service is to use the <xref:System.ServiceModel.Activation.WebServiceHostFactory> in the .svc file associated with the service, as in the following example.</span></span>  
  
```text
<%ServiceHost
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CityService"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory  
%>  
```  
  
 <span data-ttu-id="d6a36-113">另外，也可以使用配置来添加 AJAX 终结点。</span><span class="sxs-lookup"><span data-stu-id="d6a36-113">Alternatively, you can also use configuration to add an AJAX endpoint.</span></span> <span data-ttu-id="d6a36-114">在服务终结点上使用 <xref:System.ServiceModel.WebHttpBinding>，并使用 <xref:System.ServiceModel.Description.WebHttpBehavior> 配置该终结点，如下面的代码段所示。</span><span class="sxs-lookup"><span data-stu-id="d6a36-114">Use the <xref:System.ServiceModel.WebHttpBinding> on the service endpoint and configure that endpoint with the <xref:System.ServiceModel.Description.WebHttpBehavior> as shown in the following code snippet.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="AjaxBehavior">  
          <webHttp/>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <services>  
      <service name="Microsoft.Ajax.Samples.CityService">  
        <endpoint
          address="ajaxEndpoint"  
          behaviorConfiguration="AjaxBehavior"  
          binding="webHttpBinding"  
          contract="Microsoft.Ajax.Samples.ICityService" />  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="d6a36-115">有关工作示例，请参阅 [具有 JSON 和 XML 的 AJAX 服务](../samples/ajax-service-with-json-and-xml-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="d6a36-115">For a working example, see the [AJAX Service with JSON and XML](../samples/ajax-service-with-json-and-xml-sample.md).</span></span>  
  
## <a name="creating-an-ajax-compatible-service-contract"></a><span data-ttu-id="d6a36-116">创建与 AJAX 兼容的服务协定</span><span class="sxs-lookup"><span data-stu-id="d6a36-116">Creating an AJAX-Compatible Service Contract</span></span>  

 <span data-ttu-id="d6a36-117">默认情况下，通过 AJAX 终结点公开的服务协定将以 XML 格式返回数据。</span><span class="sxs-lookup"><span data-stu-id="d6a36-117">By default, service contracts exposed over an AJAX endpoint return data in the XML format.</span></span> <span data-ttu-id="d6a36-118">而且，默认情况下，通过对包含跟有操作名称的终结点地址的 URL 发出 HTTP POST 请求，将可以访问服务操作，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="d6a36-118">Also, by default service operations are accessible through HTTP POST requests to URLs that include the endpoint address followed by the operation name, as shown in the following example.</span></span>  
  
```csharp
[OperationContract]  
string[] GetCities(string firstLetters);  
```  
  
 <span data-ttu-id="d6a36-119">可以使用 HTTP POST `http://serviceaddress/endpointaddress/GetCities` 和返回 XML 消息来访问此操作。</span><span class="sxs-lookup"><span data-stu-id="d6a36-119">This operation is accessible using an HTTP POST to `http://serviceaddress/endpointaddress/GetCities` and return an XML message.</span></span>  
  
 <span data-ttu-id="d6a36-120">可以使用完整的 Web 编程模型来自定义这些基本方面。</span><span class="sxs-lookup"><span data-stu-id="d6a36-120">You can use the full Web Programming Model to customize these basic aspects.</span></span> <span data-ttu-id="d6a36-121">例如，可以使用 <xref:System.ServiceModel.Web.WebGetAttribute> 或 <xref:System.ServiceModel.Web.WebInvokeAttribute> 特性来控制操作响应的 HTTP 谓词，或使用各个特性的 `UriTemplate` 属性来指定自定义 URI。</span><span class="sxs-lookup"><span data-stu-id="d6a36-121">For example, you can use the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes to control the HTTP verb to which the operation responds or use the `UriTemplate` property of these respective attributes to specify custom URIs.</span></span> <span data-ttu-id="d6a36-122">有关详细信息，请参阅 [WCF WEB HTTP 编程模型](wcf-web-http-programming-model.md) 主题。</span><span class="sxs-lookup"><span data-stu-id="d6a36-122">For more information, see the [WCF Web HTTP Programming Model](wcf-web-http-programming-model.md) topic.</span></span>  
  
 <span data-ttu-id="d6a36-123">AJAX 服务中经常使用 JSON 数据格式。</span><span class="sxs-lookup"><span data-stu-id="d6a36-123">The JSON data format is often used in AJAX services.</span></span> <span data-ttu-id="d6a36-124">若要创建返回 JSON 而非 XML 的操作，请将 <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A>（或 <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>）属性设置为 <xref:System.ServiceModel.Web.WebMessageFormat.Json>。</span><span class="sxs-lookup"><span data-stu-id="d6a36-124">To create an operation that returns JSON instead of XML, set the <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> (or the <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>) property to <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span> <span data-ttu-id="d6a36-125">[独立 JSON 序列化](stand-alone-json-serialization.md)主题显示内置 .net 类型和数据协定类型映射到 JSON 的方式。</span><span class="sxs-lookup"><span data-stu-id="d6a36-125">The [Stand-Alone JSON Serialization](stand-alone-json-serialization.md) topic shows how built-in .NET types and data contract types map to JSON.</span></span>  
  
 <span data-ttu-id="d6a36-126">通常，JSON 的请求和响应只包括一项。</span><span class="sxs-lookup"><span data-stu-id="d6a36-126">Normally, JSON requests and responses consist of just one item.</span></span> <span data-ttu-id="d6a36-127">对于上面的 `GetCities` 操作，该请求将类似于以下语句。</span><span class="sxs-lookup"><span data-stu-id="d6a36-127">For the preceding `GetCities` operation, the request resembles the following statement.</span></span>  
  
```json
"na"  
```  
  
 <span data-ttu-id="d6a36-128">该请求的响应类似于以下语句。</span><span class="sxs-lookup"><span data-stu-id="d6a36-128">The response to that request resembles the following statement.</span></span>  
  
```json
["Nairobi", "Naples", "Nashville"]  
```  
  
 <span data-ttu-id="d6a36-129">如果该操作使用了额外的参数，则请求样式必须是“包装的”，以便将两个参数都包装在一个 JSON 对象中。</span><span class="sxs-lookup"><span data-stu-id="d6a36-129">If the operation takes an extra parameter, the request style must be wrapped to wrap both parameters in a single JSON object.</span></span> <span data-ttu-id="d6a36-130">下面的示例显示了这种样式的 JSON 消息。</span><span class="sxs-lookup"><span data-stu-id="d6a36-130">An example of this style JSON message is in the following example.</span></span>  
  
```json  
{"firstLetters": "na", "maxNumber": 2}  
```  
  
 <span data-ttu-id="d6a36-131">下面的协定会接受此消息。</span><span class="sxs-lookup"><span data-stu-id="d6a36-131">The following contract accepts this message.</span></span>  
  
```csharp
[WebInvoke(BodyStyle=WebMessageBodyStyle.WrappedRequest, ResponseFormat=WebMessageFormat.Json)]  
[OperationContract]  
string[] GetCities(string firstLetters, int maxNumber);  
```  
  
## <a name="accessing-ajax-services"></a><span data-ttu-id="d6a36-132">访问 AJAX 服务</span><span class="sxs-lookup"><span data-stu-id="d6a36-132">Accessing AJAX Services</span></span>  

 <span data-ttu-id="d6a36-133">WCF AJAX 终结点始终接受 JSON 和 XML 请求。</span><span class="sxs-lookup"><span data-stu-id="d6a36-133">WCF AJAX endpoints always accept both JSON and XML requests.</span></span>  
  
 <span data-ttu-id="d6a36-134">内容类型为 "application/json" 的 HTTP POST 请求被视为 JSON，其内容类型指示 XML (的 HTTP POST 请求例如，"text/XML" ) 被视为 XML。</span><span class="sxs-lookup"><span data-stu-id="d6a36-134">HTTP POST requests with a content-type of "application/json" are treated as JSON, and those with content-type that indicate XML (for example, "text/xml") are treated as XML.</span></span>  
  
 <span data-ttu-id="d6a36-135">HTTP GET 请求的所有请求参数都包含在 URL 本身中。</span><span class="sxs-lookup"><span data-stu-id="d6a36-135">HTTP GET requests contain all the request parameters in the URL itself.</span></span>  
  
 <span data-ttu-id="d6a36-136">用户将负责决定如何创建对终结点的 HTTP 请求。</span><span class="sxs-lookup"><span data-stu-id="d6a36-136">It is up to the user to decide how to create the HTTP request to the endpoint.</span></span> <span data-ttu-id="d6a36-137">另外，用户还可以完全控制如何构造构成请求主体的 JSON。</span><span class="sxs-lookup"><span data-stu-id="d6a36-137">Also, the user has full control over constructing the JSON that forms the body of the request.</span></span> <span data-ttu-id="d6a36-138">有关从 JavaScript 创建请求的示例，请参阅 [具有 JSON 和 XML 的 AJAX 服务](../samples/ajax-service-with-json-and-xml-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="d6a36-138">For an example of creating a request from JavaScript, see the [AJAX Service with JSON and XML](../samples/ajax-service-with-json-and-xml-sample.md).</span></span>
