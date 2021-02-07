---
description: 了解详细信息：终结点地址
title: 终结点地址
ms.date: 03/30/2017
helpviewer_keywords:
- addresses [WCF]
- Windows Communication Foundation [WCF], addresses
- WCF [WCF], addresses
ms.assetid: 13f269e3-ebb1-433c-86cf-54fbd866a627
ms.openlocfilehash: 009b34a3931bda3b16c9079316b97ea2f1680ffb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704779"
---
# <a name="endpoint-addresses"></a><span data-ttu-id="8ccf3-103">终结点地址</span><span class="sxs-lookup"><span data-stu-id="8ccf3-103">Endpoint Addresses</span></span>

<span data-ttu-id="8ccf3-104">每个终结点都具有与其关联的地址，该地址用于查找和标识终结点。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-104">Every endpoint has an address associated with it, which is used to locate and identify the endpoint.</span></span> <span data-ttu-id="8ccf3-105">此地址主要包括指定终结点位置的统一资源标识符 (URI)。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-105">This address consists primarily of a Uniform Resource Identifier (URI), which specifies the location of the endpoint.</span></span> <span data-ttu-id="8ccf3-106">终结点地址在 Windows Communication Foundation (WCF) 编程模型中表示 <xref:System.ServiceModel.EndpointAddress> ，该类包含一个可选的属性，该 <xref:System.ServiceModel.EndpointAddress.Identity%2A> 属性允许终结点的其他终结点与交换消息的其他终结点进行身份验证，并提供一组可选 <xref:System.ServiceModel.EndpointAddress.Headers%2A> 属性，用于定义访问服务时所需的任何其他 SOAP 标头。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-106">The endpoint address is represented in the Windows Communication Foundation (WCF) programming model by the <xref:System.ServiceModel.EndpointAddress> class, which contains an optional <xref:System.ServiceModel.EndpointAddress.Identity%2A> property that enables the authentication of the endpoint by other endpoints that exchange messages with it, and a set of optional <xref:System.ServiceModel.EndpointAddress.Headers%2A> properties, which define any other SOAP headers required to reach the service.</span></span> <span data-ttu-id="8ccf3-107">可选头提供其他的更详细寻址信息以标识服务终结点或与之交互。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-107">The optional headers provide additional and more detailed addressing information to identify or interact with the service endpoint.</span></span> <span data-ttu-id="8ccf3-108">终结点的地址在网络上表示为 WS-Addressing 终结点引用 (EPR)。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-108">The address of an endpoint is represented on the wire as a WS-Addressing endpoint reference (EPR).</span></span>  
  
## <a name="uri-structure-of-an-address"></a><span data-ttu-id="8ccf3-109">地址的 URI 结构</span><span class="sxs-lookup"><span data-stu-id="8ccf3-109">URI Structure of an Address</span></span>  

 <span data-ttu-id="8ccf3-110">大多数传输的地址 URI 包含四个部分。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-110">The address URI for most transports has four parts.</span></span> <span data-ttu-id="8ccf3-111">例如，URI 的四个部分 `http://www.fabrikam.com:322/mathservice.svc/secureEndpoint` 可以按如下方式进行细化：</span><span class="sxs-lookup"><span data-stu-id="8ccf3-111">For example, the four parts of the URI `http://www.fabrikam.com:322/mathservice.svc/secureEndpoint` can be itemized as follows:</span></span>  
  
- <span data-ttu-id="8ccf3-112">方案：`http:`</span><span class="sxs-lookup"><span data-stu-id="8ccf3-112">Scheme: `http:`</span></span>
  
- <span data-ttu-id="8ccf3-113">设备 `www.fabrikam.com`</span><span class="sxs-lookup"><span data-stu-id="8ccf3-113">Machine: `www.fabrikam.com`</span></span>  
  
- <span data-ttu-id="8ccf3-114">（可选）端口：322</span><span class="sxs-lookup"><span data-stu-id="8ccf3-114">(optional) Port: 322</span></span>  
  
- <span data-ttu-id="8ccf3-115">路径：/mathservice.svc/secureEndpoint</span><span class="sxs-lookup"><span data-stu-id="8ccf3-115">Path: /mathservice.svc/secureEndpoint</span></span>  
  
## <a name="defining-an-address-for-a-service"></a><span data-ttu-id="8ccf3-116">定义服务地址</span><span class="sxs-lookup"><span data-stu-id="8ccf3-116">Defining an Address for a Service</span></span>  

 <span data-ttu-id="8ccf3-117">您可以通过使用代码以强制方式或通过配置以声明方式指定服务的终结点地址。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-117">The endpoint address for a service can be specified either imperatively using code or declaratively through configuration.</span></span> <span data-ttu-id="8ccf3-118">在代码中定义终结点通常是不可行的，因为已部署服务的绑定和地址通常与在部署服务时所用的绑定和地址不同。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-118">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="8ccf3-119">一般而言，使用配置定义服务终结点比使用代码更为可行。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-119">Generally, it is more practical to define service endpoints using configuration rather than code.</span></span> <span data-ttu-id="8ccf3-120">通过在代码之外保存绑定和寻址信息，无须重新编译或重新部署应用程序即可更改它们。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-120">Keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
### <a name="defining-an-address-in-configuration"></a><span data-ttu-id="8ccf3-121">在配置中定义地址</span><span class="sxs-lookup"><span data-stu-id="8ccf3-121">Defining an Address in Configuration</span></span>  

 <span data-ttu-id="8ccf3-122">若要在配置文件中定义终结点，请使用 [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-122">To define an endpoint in a configuration file, use the [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="8ccf3-123">有关详细信息和示例，请参阅 [指定终结点地址](../specifying-an-endpoint-address.md)。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-123">For details and an example, see [Specifying an Endpoint Address](../specifying-an-endpoint-address.md).</span></span>  
  
### <a name="defining-an-address-in-code"></a><span data-ttu-id="8ccf3-124">在代码中定义地址</span><span class="sxs-lookup"><span data-stu-id="8ccf3-124">Defining an Address in Code</span></span>  

 <span data-ttu-id="8ccf3-125">在代码中可以使用 <xref:System.ServiceModel.EndpointAddress> 类创建终结点地址。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-125">An endpoint address can be created in code with the <xref:System.ServiceModel.EndpointAddress> class.</span></span> <span data-ttu-id="8ccf3-126">有关详细信息和示例，请参阅 [指定终结点地址](../specifying-an-endpoint-address.md)。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-126">For details and an example, see [Specifying an Endpoint Address](../specifying-an-endpoint-address.md).</span></span>  
  
### <a name="endpoints-in-wsdl"></a><span data-ttu-id="8ccf3-127">WSDL 中的终结点</span><span class="sxs-lookup"><span data-stu-id="8ccf3-127">Endpoints in WSDL</span></span>  

 <span data-ttu-id="8ccf3-128">在 WSDL 中终结点地址也可以表示为对应终结点的 `wsdl:port` 元素内的 WS-Addressing EPR 元素。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-128">An endpoint address can also be represented in WSDL as a WS-Addressing EPR element inside the corresponding endpoint's `wsdl:port` element.</span></span> <span data-ttu-id="8ccf3-129">EPR 包含终结点的地址以及所有的地址属性。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-129">The EPR contains the endpoint's address as well as any address properties.</span></span> <span data-ttu-id="8ccf3-130">有关详细信息和示例，请参阅 [指定终结点地址](../specifying-an-endpoint-address.md)。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-130">For details and an example, see [Specifying an Endpoint Address](../specifying-an-endpoint-address.md).</span></span>  
  
## <a name="multiple-iis-binding-support-in-net-framework-35"></a><span data-ttu-id="8ccf3-131">.NET Framework 3.5 中提供多个 IIS 绑定支持</span><span class="sxs-lookup"><span data-stu-id="8ccf3-131">Multiple IIS Binding Support in .NET Framework 3.5</span></span>  

 <span data-ttu-id="8ccf3-132">Internet 服务提供商通常在同一服务器和站点上承载许多应用程序，以增加站点密度和降低总拥有成本。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-132">Internet service providers often host many applications on the same server and site to increase the site density and lower total cost of ownership.</span></span> <span data-ttu-id="8ccf3-133">这些应用程序通常绑定到不同的基址。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-133">These applications are typically bound to different base addresses.</span></span> <span data-ttu-id="8ccf3-134">Internet 信息服务 (IIS) 网站可以包含多个应用程序。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-134">An Internet Information Services (IIS) Web site can contain multiple applications.</span></span> <span data-ttu-id="8ccf3-135">可以通过一个或多个 IIS 绑定访问站点中的应用程序。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-135">The applications in a site can be accessed through one or more IIS bindings.</span></span>  
  
 <span data-ttu-id="8ccf3-136">IIS 绑定提供了两则信息：绑定协议和绑定信息。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-136">IIS bindings provide two pieces of information: a binding protocol, and binding information.</span></span> <span data-ttu-id="8ccf3-137">绑定协议定义发生通信所依据的方案，而绑定信息是用于访问站点的信息。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-137">The binding protocol defines the scheme over which communication occurs, and binding information is the information used to access the site.</span></span>  
  
 <span data-ttu-id="8ccf3-138">下面的示例演示可以存在于 IIS 绑定中的组件：</span><span class="sxs-lookup"><span data-stu-id="8ccf3-138">The following example shows the components that can be present in an IIS binding:</span></span>  
  
- <span data-ttu-id="8ccf3-139">绑定协议：HTTP</span><span class="sxs-lookup"><span data-stu-id="8ccf3-139">Binding protocol: HTTP</span></span>  
  
- <span data-ttu-id="8ccf3-140">绑定信息：IP 地址、端口、主机头</span><span class="sxs-lookup"><span data-stu-id="8ccf3-140">Binding Information: IP Address, Port, Host header</span></span>  
  
 <span data-ttu-id="8ccf3-141">IIS 可以为每个站点指定多个绑定，这会导致每个方案有多个基址。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-141">IIS can specify multiple bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="8ccf3-142">在 .NET Framework 3.5 之前，WCF 不支持架构的多个地址，如果已指定，则 <xref:System.ArgumentException> 在激活过程中引发。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-142">Prior to .NET Framework 3.5, WCF did not support multiple addresses for a schema and, if they were specified, threw a <xref:System.ArgumentException> during activation.</span></span>  
  
 <span data-ttu-id="8ccf3-143">.NET Framework 3.5 使 Internet 服务提供商能够为同一站点上的同一方案托管多个具有不同基址的应用程序。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-143">The .NET Framework 3.5 enables Internet service providers to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="8ccf3-144">例如，一个站点可能包含以下基址：</span><span class="sxs-lookup"><span data-stu-id="8ccf3-144">For example, a site could contain the following base addresses:</span></span>  
  
- `http://payroll.myorg.com/Service.svc`
  
- `http://shipping.myorg.com/Service.svc`
  
 <span data-ttu-id="8ccf3-145">使用 .NET Framework 3.5，可以在配置文件的 AppDomain 级别指定前缀筛选器。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-145">With .NET Framework 3.5, you specify a prefix filter at the AppDomain level in the configuration file.</span></span> <span data-ttu-id="8ccf3-146">为此 [\<baseAddressPrefixFilters>](../../configure-apps/file-schema/wcf/baseaddressprefixfilters.md) ，请使用包含前缀列表的元素。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-146">You do this with the [\<baseAddressPrefixFilters>](../../configure-apps/file-schema/wcf/baseaddressprefixfilters.md) element, which contains a list of prefixes.</span></span> <span data-ttu-id="8ccf3-147">基于可选前缀列表筛选由 IIS 提供的传入基址。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-147">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list.</span></span> <span data-ttu-id="8ccf3-148">默认情况下，如果未指定前缀，则使所有地址通过。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-148">By default, when a prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="8ccf3-149">指定前缀导致仅使该方案的匹配基址通过。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-149">Specifying the prefix results in only the matching base address for that scheme to be passed through.</span></span>  
  
 <span data-ttu-id="8ccf3-150">下面的配置代码示例使用前缀筛选器。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-150">The following is an example of configuration code that uses the prefix filters.</span></span>  
  
```xml  
<system.serviceModel>  
  <serviceHostingEnvironment>  
     <baseAddressPrefixFilters>  
        <add prefix="net.tcp://payroll.myorg.com:8000"/>  
        <add prefix="http://shipping.myorg.com:8000"/>  
    </baseAddressPrefixFilters>  
  </serviceHostingEnvironment>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="8ccf3-151">在前面的示例中， `net.tcp://payroll.myorg.com:8000` 和 `http://shipping.myorg.com:8000` 是唯一的基址，它们适用于其各自的方案，它们会通过。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-151">In the preceding example, `net.tcp://payroll.myorg.com:8000` and `http://shipping.myorg.com:8000` are the only base addresses, for their respective schemes, which are passed through.</span></span>  
  
 <span data-ttu-id="8ccf3-152">`baseAddressPrefixFilter` 不支持通配符。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-152">The `baseAddressPrefixFilter` does not support wildcards.</span></span>  
  
 <span data-ttu-id="8ccf3-153">IIS 提供的基址可能具有绑定到 `baseAddressPrefixFilters` 列表中不存在的其他方案的地址。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-153">The base addresses supplied by IIS may have addresses bound to other schemes not present in `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="8ccf3-154">不会筛选出这些地址。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-154">These addresses are not filtered out.</span></span>  
  
## <a name="multiple-iis-binding-support-in-net-framework-4-and-later"></a><span data-ttu-id="8ccf3-155">.NET Framework 4 以及更高版本中的多个 IIS 绑定支持</span><span class="sxs-lookup"><span data-stu-id="8ccf3-155">Multiple IIS Binding Support in .NET Framework 4 and later</span></span>  

 <span data-ttu-id="8ccf3-156">从 .NET 4 开始，通过将 <xref:System.ServiceModel.ServiceHostingEnvironment> 的 <xref:System.ServiceModel.ServiceHostingEnvironment.MultipleSiteBindingsEnabled%2A> 设置为 True，你无需选取单个基址便可实现对 IIS 中多个绑定的支持。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-156">Starting in .NET 4, you can enable support for multiple bindings in IIS without having to pick a single base address, by setting <xref:System.ServiceModel.ServiceHostingEnvironment>’s <xref:System.ServiceModel.ServiceHostingEnvironment.MultipleSiteBindingsEnabled%2A> setting to true.</span></span> <span data-ttu-id="8ccf3-157">此支持限于 HTTP 协议方案。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-157">This support is limited to HTTP protocol schemes.</span></span>  
  
 <span data-ttu-id="8ccf3-158">下面是在上使用 multipleSiteBindingsEnabled 的配置代码示例 [\<serviceHostingEnvironment>](../../configure-apps/file-schema/wcf/servicehostingenvironment.md) 。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-158">The following is an example of configuration code that uses multipleSiteBindingsEnabled on [\<serviceHostingEnvironment>](../../configure-apps/file-schema/wcf/servicehostingenvironment.md).</span></span>  
  
```xml  
<system.serviceModel>  
  <serviceHostingEnvironment multipleSiteBindingsEnabled="true" >  
  </serviceHostingEnvironment>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="8ccf3-159">对于 HTTP 和非 HTTP 协议，当使用此设置启用多个网站绑定时，忽略任何 baseAddressPrefixFilter 设置。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-159">Any baseAddressPrefixFilters settings are ignored, for both HTTP and non-HTTP protocols, when multiple site bindings are enabled using this setting.</span></span>  
  
 <span data-ttu-id="8ccf3-160">有关详细信息和示例，请参阅 [支持多个 IIS 站点绑定](supporting-multiple-iis-site-bindings.md) 和 <xref:System.ServiceModel.ServiceHostingEnvironment.MultipleSiteBindingsEnabled%2A> 。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-160">For details and examples, see [Supporting Multiple IIS Site Bindings](supporting-multiple-iis-site-bindings.md) and <xref:System.ServiceModel.ServiceHostingEnvironment.MultipleSiteBindingsEnabled%2A>.</span></span>  
  
## <a name="extending-addressing-in-wcf-services"></a><span data-ttu-id="8ccf3-161">在 WCF 服务中扩展寻址</span><span class="sxs-lookup"><span data-stu-id="8ccf3-161">Extending Addressing in WCF Services</span></span>  

 <span data-ttu-id="8ccf3-162">WCF 服务的默认寻址模型使用终结点地址 URI 来实现以下目的：</span><span class="sxs-lookup"><span data-stu-id="8ccf3-162">The default addressing model of WCF services uses the endpoint address URI for the following purposes:</span></span>  
  
- <span data-ttu-id="8ccf3-163">指定服务侦听地址，即终结点侦听消息的位置，</span><span class="sxs-lookup"><span data-stu-id="8ccf3-163">To specify the service listening address, the location at which the endpoint listens for messages,</span></span>  
  
- <span data-ttu-id="8ccf3-164">指定 SOAP 地址筛选器，即终结点期望作为 SOAP 头的地址。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-164">To specify the SOAP address filter, the address an endpoint expects as a SOAP header.</span></span>  
  
 <span data-ttu-id="8ccf3-165">可以单独指定用于其中每个目的的值，从而允许涉及有用方案的若干寻址扩展：</span><span class="sxs-lookup"><span data-stu-id="8ccf3-165">The values for each of these purposes can be specified separately, allowing several extensions of addressing that cover useful scenarios:</span></span>  
  
- <span data-ttu-id="8ccf3-166">SOAP 媒介：客户端发送的消息在到达其最终目的地之前遍历一个或多个处理消息的其他服务。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-166">SOAP intermediaries: a message sent by a client traverses one or more additional services that process the message before it reaches its final destination.</span></span> <span data-ttu-id="8ccf3-167">SOAP 媒介可以执行各种任务，如对消息进行缓存、路由、负载平衡或架构验证。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-167">SOAP intermediaries can perform various tasks, such as caching, routing, load-balancing, or schema validation on the messages.</span></span> <span data-ttu-id="8ccf3-168">此方案是通过将消息发送到单独的物理地址（`via`，以媒介为目标），而不是仅发送到逻辑地址（`wsa:To`，以最终目的地为目标）完成的。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-168">This scenario is accomplished by sending messages to a separate physical address (`via`) that targets the intermediary rather than just to a logical address (`wsa:To`) that targets the ultimate destination.</span></span>  
  
- <span data-ttu-id="8ccf3-169">终结点的侦听地址是专用 URI，它设置为与其 `listenURI` 属性不同的值。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-169">The listening address of the endpoint is a private URI and is set to a different value than its `listenURI` property.</span></span>  
  
 <span data-ttu-id="8ccf3-170">`via` 指定的传输地址是将消息发往 `to` 参数指定的、服务所在的某个其他远程地址途中应该最初发送到的地址。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-170">The transport address that the `via` specifies is the location to which a message should initially be sent on its way to some other remote address specified by the `to` parameter at which the service is located.</span></span> <span data-ttu-id="8ccf3-171">在大多数 Internet 方案中，`via` URI 与服务的最终 <xref:System.ServiceModel.EndpointAddress.Uri%2A> 地址的 `to` 属性相同。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-171">In most Internet scenarios, the `via` URI is the same as the <xref:System.ServiceModel.EndpointAddress.Uri%2A> property of the final `to` address of the service.</span></span> <span data-ttu-id="8ccf3-172">仅当必须执行手动路由时，才区分这两个地址。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-172">You only distinguish between these two addresses when you must do manual routing.</span></span>  
  
### <a name="addressing-headers"></a><span data-ttu-id="8ccf3-173">寻址头</span><span class="sxs-lookup"><span data-stu-id="8ccf3-173">Addressing Headers</span></span>  

 <span data-ttu-id="8ccf3-174">除了其基本 URI 外，终结点可以按一个或多个 SOAP 标头寻址。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-174">An endpoint can be addressed by one or more SOAP headers in addition to its basic URI.</span></span> <span data-ttu-id="8ccf3-175">这一点在其中很有用的一组方案是一组 SOAP 媒介方案，其中终结点要求该终结点的客户端包括以媒介为目标的 SOAP 头。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-175">One set of scenarios where this is useful is a set of SOAP intermediary scenarios where an endpoint requires clients of that endpoint to include SOAP headers targeted at intermediaries.</span></span>  
  
 <span data-ttu-id="8ccf3-176">可以通过两种方法定义自定义地址头 - 使用代码或使用配置：</span><span class="sxs-lookup"><span data-stu-id="8ccf3-176">You can define custom address headers in two ways—by using either code or configuration:</span></span>  
  
- <span data-ttu-id="8ccf3-177">在代码中，通过使用 <xref:System.ServiceModel.Channels.AddressHeader> 类创建自定义地址头，然后在构造 <xref:System.ServiceModel.EndpointAddress> 时使用它。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-177">In code, create custom address headers by using the <xref:System.ServiceModel.Channels.AddressHeader> class, and then used in the construction of an <xref:System.ServiceModel.EndpointAddress>.</span></span>  
  
- <span data-ttu-id="8ccf3-178">在配置中， [\<headers>](../../configure-apps/file-schema/wcf/headers.md) 将自定义指定为元素的子 [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-178">In configuration, custom [\<headers>](../../configure-apps/file-schema/wcf/headers.md) are specified as children of the [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) element.</span></span>  
  
 <span data-ttu-id="8ccf3-179">配置通常比代码更可取，因为它允许你在部署后更改头。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-179">Configuration is generally preferable to code, as it allows you to change the headers after deployment.</span></span>  
  
### <a name="custom-listening-addresses"></a><span data-ttu-id="8ccf3-180">自定义侦听地址</span><span class="sxs-lookup"><span data-stu-id="8ccf3-180">Custom Listening Addresses</span></span>  

 <span data-ttu-id="8ccf3-181">可以将侦听地址设置为与终结点的 URI 不同的值。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-181">You can set the listening address to a different value than the endpoint’s URI.</span></span> <span data-ttu-id="8ccf3-182">在要公开的 SOAP 地址为公共 SOAP 媒介的地址，而终结点实际侦听的地址是专用网络地址的媒介方案中，这是很有用的。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-182">This is useful in intermediary scenarios where the SOAP address to be exposed is that of a public SOAP intermediary, whereas the address where the endpoint actually listens is a private network address.</span></span>  
  
 <span data-ttu-id="8ccf3-183">可以通过使用代码或配置指定自定义侦听地址：</span><span class="sxs-lookup"><span data-stu-id="8ccf3-183">You can specify a custom listening address by using either code or configuration:</span></span>  
  
- <span data-ttu-id="8ccf3-184">在代码中，通过将 <xref:System.ServiceModel.Description.ClientViaBehavior> 类添加到终结点的行为集合指定自定义侦听地址。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-184">In code, specify a custom listening address by adding a <xref:System.ServiceModel.Description.ClientViaBehavior> class to the endpoint’s behavior collection.</span></span>  
  
- <span data-ttu-id="8ccf3-185">在 "配置" 中，使用服务元素的属性指定自定义侦听地址 `ListenUri` [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) 。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-185">In configuration, specify a custom listening address with the `ListenUri` attribute of the service [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) element.</span></span>  
  
### <a name="custom-soap-address-filter"></a><span data-ttu-id="8ccf3-186">自定义 SOAP 地址筛选器</span><span class="sxs-lookup"><span data-stu-id="8ccf3-186">Custom SOAP Address Filter</span></span>  

 <span data-ttu-id="8ccf3-187"><xref:System.ServiceModel.EndpointAddress.Uri%2A> 与任何 <xref:System.ServiceModel.EndpointAddress.Headers%2A> 属性联合使用，以定义终结点的 SOAP 地址筛选器 (<xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A>)。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-187">The <xref:System.ServiceModel.EndpointAddress.Uri%2A> is used in conjunction with any <xref:System.ServiceModel.EndpointAddress.Headers%2A> property to define an endpoint’s SOAP address filter (<xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A>).</span></span> <span data-ttu-id="8ccf3-188">默认情况下，此筛选器验证传入消息是否具有与终结点的 URI 匹配的 `To` 消息头，以及所有必需的终结点头是否存在于消息中。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-188">By default, this filter verifies that an incoming message has a `To` message header that matches the endpoint’s URI and that all of the required endpoint headers are present in the message.</span></span>  
  
 <span data-ttu-id="8ccf3-189">在某些方案中，终结点接收抵达基础传输的所有消息，而不仅仅是具有相应 `To` 头的消息。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-189">In some scenarios, an endpoint receives all messages that arrive on the underlying transport, and not just those with the appropriate `To` header.</span></span> <span data-ttu-id="8ccf3-190">若要启用这一点，用户可以使用 <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> 类。</span><span class="sxs-lookup"><span data-stu-id="8ccf3-190">To enable this, the user can use the <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ccf3-191">请参阅</span><span class="sxs-lookup"><span data-stu-id="8ccf3-191">See also</span></span>

- [<span data-ttu-id="8ccf3-192">指定终结点地址</span><span class="sxs-lookup"><span data-stu-id="8ccf3-192">Specifying an Endpoint Address</span></span>](../specifying-an-endpoint-address.md)
- [<span data-ttu-id="8ccf3-193">服务标识和身份验证</span><span class="sxs-lookup"><span data-stu-id="8ccf3-193">Service Identity and Authentication</span></span>](service-identity-and-authentication.md)
