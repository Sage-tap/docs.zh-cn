---
description: 了解详细信息： <basicHttpContextBinding>
title: <basicHttpContextBinding>
ms.date: 03/30/2017
ms.assetid: 39b16b82-4ec6-4eff-8031-67e026870961
ms.openlocfilehash: d77d57325417a2aa7c49fb8893f4512dad71563b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782191"
---
# \<basicHttpContextBinding>

<span data-ttu-id="9000d-102">指定一个绑定，该绑定为将通过启用 HTTP Cookie 作为交换机制来进行交换的 <xref:System.ServiceModel.BasicHttpBinding> 提供上下文。</span><span class="sxs-lookup"><span data-stu-id="9000d-102">Specifying a binding that provides context for the <xref:System.ServiceModel.BasicHttpBinding> to be exchanged by enabling HTTP cookies as the exchange mechanism.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<basicHttpContextBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="9000d-103">语法</span><span class="sxs-lookup"><span data-stu-id="9000d-103">Syntax</span></span>  
  
```xml  
<basicHttpContextBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxReceivedMessageSize="Integer"
           messageEncoding="Text/Mtom"
           name="String"
           openTimeout="TimeSpan"
           proxyAddress="URI"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"
           useDefaultWebProxy="Boolean">
    <security mode="None/Transport/Message/TransportWithMessageCredential/TransportCredentialOnly">
      <transport clientCredentialType="None/Basic/Digest/Ntlm/Windows/Certificate"
                 proxyCredentialType="None/Basic/Digest/Ntlm/Windows"
                 realm="String" />
      <message algorithmSuite="Aes128/Aes192/Aes256/Rsa15Aes128/ Rsa15Aes256/TripleDes"
               clientCredentialType="UserName/Certificate" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</basicHttpContextBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9000d-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="9000d-104">Attributes and Elements</span></span>  

 <span data-ttu-id="9000d-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="9000d-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9000d-106">特性</span><span class="sxs-lookup"><span data-stu-id="9000d-106">Attributes</span></span>  
  
|<span data-ttu-id="9000d-107">属性</span><span class="sxs-lookup"><span data-stu-id="9000d-107">Attribute</span></span>|<span data-ttu-id="9000d-108">说明</span><span class="sxs-lookup"><span data-stu-id="9000d-108">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="9000d-109">一个布尔值，指示客户端是否接受 Cookie 并在今后的请求中传播这些 Cookie。</span><span class="sxs-lookup"><span data-stu-id="9000d-109">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="9000d-110">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="9000d-110">The default is `false`.</span></span><br /><br /> <span data-ttu-id="9000d-111">在与使用 Cookie 的 ASMX Web 服务进行交互时，可以使用此属性。</span><span class="sxs-lookup"><span data-stu-id="9000d-111">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="9000d-112">通过这种方式，可以确保从服务器返回的 Cookie 自动复制到客户端今后对该服务的所有请求。</span><span class="sxs-lookup"><span data-stu-id="9000d-112">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="9000d-113">一个布尔值，指示是否对本地地址不使用代理服务器。</span><span class="sxs-lookup"><span data-stu-id="9000d-113">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="9000d-114">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="9000d-114">The default is `false`.</span></span><br /><br /> <span data-ttu-id="9000d-115">如果 Internet 资源具有本地地址，则该资源是本地资源。</span><span class="sxs-lookup"><span data-stu-id="9000d-115">An Internet resource is local if it has a local address.</span></span> <span data-ttu-id="9000d-116">本地地址是在同一台计算机上，本地 LAN 或 intranet 上的地址，在语法上，在 ) 缺少句点 `http://webserver/` (。 `http://localhost/`</span><span class="sxs-lookup"><span data-stu-id="9000d-116">A local address is one that is on same computer, the local LAN or intranet and is identified, syntactically, by the lack of a period (.) as in the URIs `http://webserver/` and `http://localhost/`.</span></span><br /><br /> <span data-ttu-id="9000d-117">通过设置此属性，可以确定在访问本地资源时，采用 BasicHttpBinding 配置的终结点是否使用代理服务器。</span><span class="sxs-lookup"><span data-stu-id="9000d-117">Setting this attribute determines whether endpoints configured with the BasicHttpBinding use the proxy server when accessing local resources.</span></span> <span data-ttu-id="9000d-118">如果此属性为 `true`，则对本地 Internet 资源的请求不使用代理服务器。</span><span class="sxs-lookup"><span data-stu-id="9000d-118">If this attribute is `true`, requests to local Internet resources do not use the proxy server.</span></span> <span data-ttu-id="9000d-119">当此属性设置为 `true` 时，如果希望客户端在与同一台计算机上的服务通话时使用代理，请使用主机名称（而非 localhost）。</span><span class="sxs-lookup"><span data-stu-id="9000d-119">Use the host name (rather than localhost) if you want clients to go through a proxy when talking to services on the same machine when this attribute is set to `true`.</span></span><br /><br /> <span data-ttu-id="9000d-120">当此属性为 `false` 时，所有 Internet 请求都通过代理服务器发出。</span><span class="sxs-lookup"><span data-stu-id="9000d-120">When this attribute is `false`, all Internet requests are made through the proxy server.</span></span>|  
|`closeTimeout`|<span data-ttu-id="9000d-121">一个 <xref:System.TimeSpan> 值，指定为完成关闭操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="9000d-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="9000d-122">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="9000d-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9000d-123">默认值为 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="9000d-123">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="9000d-124">指定用于分析 URI 的 HTTP 主机名比较模式。</span><span class="sxs-lookup"><span data-stu-id="9000d-124">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="9000d-125">此属性的类型为 <xref:System.ServiceModel.HostNameComparisonMode>，指示在对 URI 进行匹配时，是否使用主机名来访问服务。</span><span class="sxs-lookup"><span data-stu-id="9000d-125">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="9000d-126">默认值为 <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>，表示忽略匹配项中的主机名。</span><span class="sxs-lookup"><span data-stu-id="9000d-126">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="9000d-127">一个整数值，指定为从通道接收消息的消息缓冲区管理器分配并供其使用的最大内存量。</span><span class="sxs-lookup"><span data-stu-id="9000d-127">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="9000d-128">默认值为 524288 (0x80000) 字节。</span><span class="sxs-lookup"><span data-stu-id="9000d-128">The default value is 524288 (0x80000) bytes.</span></span><br /><br /> <span data-ttu-id="9000d-129">通过使用缓冲池，缓冲区管理器可将使用缓冲区的开销降到最低。</span><span class="sxs-lookup"><span data-stu-id="9000d-129">The Buffer Manager minimizes the cost of using buffers by using a buffer pool.</span></span> <span data-ttu-id="9000d-130">当消息离开通道时，服务需要使用缓冲区来处理这些消息。</span><span class="sxs-lookup"><span data-stu-id="9000d-130">Buffers are required to process messages by the service when they come out of the channel.</span></span> <span data-ttu-id="9000d-131">如果缓冲池中的内存不够用来处理消息负载，则缓冲区管理器必须从 CLR 堆分配更多内存，而这会增加垃圾回收的系统开销。</span><span class="sxs-lookup"><span data-stu-id="9000d-131">If there is not sufficient memory in the buffer pool to process the message load, the Buffer Manager must allocate additional memory from the CLR heap, which increases the garbage collection overhead.</span></span> <span data-ttu-id="9000d-132">从 CLR 垃圾堆进行大量分配表明缓冲池太小，可以通过提高此属性指定的限制来实现更大的内存分配，从而提高性能。</span><span class="sxs-lookup"><span data-stu-id="9000d-132">Extensive allocation from the CLR garbage heap is an indication that the buffer pool size is too small and that performance can be improved with a larger allocation by increasing the limit specified by this attribute.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="9000d-133">一个整数值，指定为采用此绑定配置的终结点处理消息时存储消息的缓冲区的最大大小（字节）。</span><span class="sxs-lookup"><span data-stu-id="9000d-133">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="9000d-134">默认值为 65,536 字节。</span><span class="sxs-lookup"><span data-stu-id="9000d-134">The default value is 65,536 bytes.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="9000d-135">一个正整数，定义在采用此绑定配置的通道上可以接收的消息的最大消息大小（字节），包括消息头。</span><span class="sxs-lookup"><span data-stu-id="9000d-135">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="9000d-136">如果消息对于接收方而言太大，则发送方将收到 SOAP 错误。</span><span class="sxs-lookup"><span data-stu-id="9000d-136">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="9000d-137">接收方将删除该消息，并在跟踪日志中创建事件项。</span><span class="sxs-lookup"><span data-stu-id="9000d-137">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="9000d-138">默认值为 65,536 字节。</span><span class="sxs-lookup"><span data-stu-id="9000d-138">The default is 65,536 bytes.</span></span>|  
|`messageEncoding`|<span data-ttu-id="9000d-139">定义用于对 SOAP 消息进行编码的编码器。</span><span class="sxs-lookup"><span data-stu-id="9000d-139">Defines the encoder used to encode the SOAP message.</span></span> <span data-ttu-id="9000d-140">有效值包括以下值：</span><span class="sxs-lookup"><span data-stu-id="9000d-140">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="9000d-141">-Text：使用文本消息编码器。</span><span class="sxs-lookup"><span data-stu-id="9000d-141">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="9000d-142">-Mtom：使用消息传输组织机制 1.0 (MTOM) 编码器。</span><span class="sxs-lookup"><span data-stu-id="9000d-142">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="9000d-143">默认值为 Text。</span><span class="sxs-lookup"><span data-stu-id="9000d-143">The default is Text.</span></span> <span data-ttu-id="9000d-144">此属性的类型为 <xref:System.ServiceModel.WSMessageEncoding>。</span><span class="sxs-lookup"><span data-stu-id="9000d-144">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`messageVersion`|<span data-ttu-id="9000d-145">指定采用绑定配置的客户端和服务使用的消息版本。</span><span class="sxs-lookup"><span data-stu-id="9000d-145">Specifies the message version used by clients and services configured with the binding.</span></span> <span data-ttu-id="9000d-146">此属性的类型为 <xref:System.ServiceModel.Channels.MessageVersion>。</span><span class="sxs-lookup"><span data-stu-id="9000d-146">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|`name`|<span data-ttu-id="9000d-147">一个包含绑定的配置名称的字符串。</span><span class="sxs-lookup"><span data-stu-id="9000d-147">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="9000d-148">因为此值用作绑定的标识，所以它应该是唯一的。</span><span class="sxs-lookup"><span data-stu-id="9000d-148">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="9000d-149">从 .NET Framework 4 开始，绑定和行为不需要具有名称。</span><span class="sxs-lookup"><span data-stu-id="9000d-149">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="9000d-150">有关默认配置和无值绑定和行为的详细信息，请参阅[WCF 服务的](../../../wcf/samples/simplified-configuration-for-wcf-services.md)[简化配置](../../../wcf/simplified-configuration.md)和简化配置。</span><span class="sxs-lookup"><span data-stu-id="9000d-150">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="9000d-151">一个 <xref:System.TimeSpan> 值，指定为完成打开操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="9000d-151">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="9000d-152">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="9000d-152">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9000d-153">默认值为 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="9000d-153">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="9000d-154">一个包含 HTTP 代理地址的 URI。</span><span class="sxs-lookup"><span data-stu-id="9000d-154">A URI that contains the address of the HTTP proxy.</span></span> <span data-ttu-id="9000d-155">如果 `useSystemWebProxy` 设置为 `true`，则此设置必须为 `null`。</span><span class="sxs-lookup"><span data-stu-id="9000d-155">If `useSystemWebProxy` is set to `true`, this setting must be `null`.</span></span> <span data-ttu-id="9000d-156">默认值为 `null`。</span><span class="sxs-lookup"><span data-stu-id="9000d-156">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="9000d-157">一个 <xref:System.TimeSpan> 值，指定为完成接收操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="9000d-157">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="9000d-158">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="9000d-158">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9000d-159">默认值为 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="9000d-159">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="9000d-160">一个 <xref:System.TimeSpan> 值，指定为完成发送操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="9000d-160">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="9000d-161">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="9000d-161">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9000d-162">默认值为 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="9000d-162">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="9000d-163">设置要用来在绑定上发出消息的字符集编码。</span><span class="sxs-lookup"><span data-stu-id="9000d-163">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="9000d-164">有效值包括以下值：</span><span class="sxs-lookup"><span data-stu-id="9000d-164">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="9000d-165">-BigEndianUnicode： Unicode BigEndian 编码。</span><span class="sxs-lookup"><span data-stu-id="9000d-165">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="9000d-166">-Unicode：16位编码。</span><span class="sxs-lookup"><span data-stu-id="9000d-166">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="9000d-167">-UTF8：8位编码</span><span class="sxs-lookup"><span data-stu-id="9000d-167">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="9000d-168">默认编码为 UTF8。</span><span class="sxs-lookup"><span data-stu-id="9000d-168">The default is UTF8.</span></span> <span data-ttu-id="9000d-169">此属性的类型为 <xref:System.Text.Encoding>。</span><span class="sxs-lookup"><span data-stu-id="9000d-169">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transferMode`|<span data-ttu-id="9000d-170">一个有效的 <xref:System.ServiceModel.TransferMode> 值，指定为请求或响应对消息进行缓冲处理还是流式处理。</span><span class="sxs-lookup"><span data-stu-id="9000d-170">A valid <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed on a request or response.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="9000d-171">一个布尔值，指定是否应在可用时使用系统的自动配置 HTTP 代理。</span><span class="sxs-lookup"><span data-stu-id="9000d-171">A Boolean value that specifies whether the auto-configured HTTP proxy of the system should be used, if available.</span></span> <span data-ttu-id="9000d-172">默认值为 `true`。</span><span class="sxs-lookup"><span data-stu-id="9000d-172">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9000d-173">子元素</span><span class="sxs-lookup"><span data-stu-id="9000d-173">Child Elements</span></span>  
  
|<span data-ttu-id="9000d-174">元素</span><span class="sxs-lookup"><span data-stu-id="9000d-174">Element</span></span>|<span data-ttu-id="9000d-175">说明</span><span class="sxs-lookup"><span data-stu-id="9000d-175">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-basichttpbinding.md)|<span data-ttu-id="9000d-176">定义绑定的安全设置。</span><span class="sxs-lookup"><span data-stu-id="9000d-176">Defines the security settings for the binding.</span></span> <span data-ttu-id="9000d-177">此元素的类型为 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="9000d-177">This element is of type <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.</span></span>|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="9000d-178">定义可由采用此绑定配置的终结点进行处理的 SOAP 消息的复杂性约束。</span><span class="sxs-lookup"><span data-stu-id="9000d-178">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="9000d-179">此元素的类型为 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="9000d-179">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9000d-180">父元素</span><span class="sxs-lookup"><span data-stu-id="9000d-180">Parent Elements</span></span>  
  
|<span data-ttu-id="9000d-181">元素</span><span class="sxs-lookup"><span data-stu-id="9000d-181">Element</span></span>|<span data-ttu-id="9000d-182">说明</span><span class="sxs-lookup"><span data-stu-id="9000d-182">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="9000d-183">此元素包含标准绑定和自定义绑定的集合。</span><span class="sxs-lookup"><span data-stu-id="9000d-183">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9000d-184">备注</span><span class="sxs-lookup"><span data-stu-id="9000d-184">Remarks</span></span>  

 <span data-ttu-id="9000d-185">此绑定元素提供一个保护级别和一种交换机制，作为 `BasicHttpBinding` 的上下文的一部分。</span><span class="sxs-lookup"><span data-stu-id="9000d-185">This binding element provides a protection level and an exchange mechanism as part of the context for a `BasicHttpBinding`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9000d-186">请参阅</span><span class="sxs-lookup"><span data-stu-id="9000d-186">See also</span></span>

- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.BasicHttpContextBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpContextBindingElement>
- <xref:System.ServiceModel.Channels.ContextBindingElement>
- [<span data-ttu-id="9000d-187">绑定</span><span class="sxs-lookup"><span data-stu-id="9000d-187">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="9000d-188">配置系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="9000d-188">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="9000d-189">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="9000d-189">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [\<basicHttpBinding>](basichttpbinding.md)
