---
description: 了解详细信息： <wsHttpContextBinding>
title: <wsHttpContextBinding>
ms.date: 03/30/2017
ms.assetid: 1e40b5c9-0df2-4d66-afc5-a99d0e4ae7a4
ms.openlocfilehash: b020bbcaaa8d7680aeda8dc1a72cbc70fb4f9ada
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682054"
---
# \<wsHttpContextBinding>

<span data-ttu-id="e5964-102">为要求对保护级别进行签名的 <xref:System.ServiceModel.WSHttpBinding> 提供上下文。</span><span class="sxs-lookup"><span data-stu-id="e5964-102">Provides a context for the <xref:System.ServiceModel.WSHttpBinding> that requires that the protection level be signed.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsHttpContextBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="e5964-103">语法</span><span class="sxs-lookup"><span data-stu-id="e5964-103">Syntax</span></span>  
  
```xml  
<wsHttpContextBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           contextProtectionLevel="EncryptAndSign/None/Sign"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="integer"
           maxReceivedMessageSize="Integer"
           messageEncoding="Text/Mtom"
           name="string"
           openTimeout="TimeSpan"
           proxyAddress="URI"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           transactionFlow="Boolean"
           useDefaultWebProxy="Boolean">
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan"
                     enabled="Boolean" />
    <security mode="Message/None/Transport/TransportWithCredential">
      <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
                 proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
                 realm="string"
                 defaultClientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
                 defaultProxyCredentialType="Basic/Digest/None/Ntlm/Windows"
                 defaultRealm="string" />
      <message clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               establishSecurityContext="Boolean"
               negotiateServiceCredential="Boolean" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</wsHttpContextBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e5964-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="e5964-104">Attributes and Elements</span></span>  

 <span data-ttu-id="e5964-105">以下几节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e5964-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e5964-106">特性</span><span class="sxs-lookup"><span data-stu-id="e5964-106">Attributes</span></span>  
  
|<span data-ttu-id="e5964-107">属性</span><span class="sxs-lookup"><span data-stu-id="e5964-107">Attribute</span></span>|<span data-ttu-id="e5964-108">说明</span><span class="sxs-lookup"><span data-stu-id="e5964-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e5964-109">allowCookies</span><span class="sxs-lookup"><span data-stu-id="e5964-109">allowCookies</span></span>|<span data-ttu-id="e5964-110">一个布尔值，指示客户端是否接受 Cookie 并在今后的请求中传播这些 Cookie。</span><span class="sxs-lookup"><span data-stu-id="e5964-110">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="e5964-111">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="e5964-111">The default is `false`.</span></span><br /><br /> <span data-ttu-id="e5964-112">当 `allowCookies` 设置为 `true` 时，contextChannel 将使用 httpCookies 作为交换上下文的模式。</span><span class="sxs-lookup"><span data-stu-id="e5964-112">When `allowCookies` is set to `true`, contextChannel will use httpCookies as the mode of exchanging context.</span></span> <span data-ttu-id="e5964-113">当此属性设置为 `false` 时，将上下文作为 soap 标头进行交换。</span><span class="sxs-lookup"><span data-stu-id="e5964-113">When this attribute is set to `false`, context is exchanged as soap headers.</span></span><br /><br /> <span data-ttu-id="e5964-114">默认值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="e5964-114">The default value is `false`.</span></span><br /><br /> <span data-ttu-id="e5964-115">在与使用 Cookie 的 ASMX Web 服务进行交互时，可以使用此属性。</span><span class="sxs-lookup"><span data-stu-id="e5964-115">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="e5964-116">通过这种方式，可以确保从服务器返回的 Cookie 自动复制到客户端今后对该服务的所有请求。</span><span class="sxs-lookup"><span data-stu-id="e5964-116">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|<span data-ttu-id="e5964-117">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="e5964-117">bypassProxyOnLocal</span></span>|<span data-ttu-id="e5964-118">一个布尔值，指示是否对本地地址不使用代理服务器。</span><span class="sxs-lookup"><span data-stu-id="e5964-118">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="e5964-119">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="e5964-119">The default is `false`.</span></span>|  
|<span data-ttu-id="e5964-120">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="e5964-120">closeTimeout</span></span>|<span data-ttu-id="e5964-121">一个 <xref:System.TimeSpan> 值，指定为完成关闭操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="e5964-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="e5964-122">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="e5964-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e5964-123">默认值为 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="e5964-123">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="e5964-124">contextProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="e5964-124">contextProtectionLevel</span></span>|<span data-ttu-id="e5964-125">一个有效的 <xref:System.Net.Security.ProtectionLevel> 值，指定用于传播上下文信息的 SOAP 标头的所需保护级别。</span><span class="sxs-lookup"><span data-stu-id="e5964-125">A valid <xref:System.Net.Security.ProtectionLevel> value that specifies the desired protection level of the SOAP header used to propagate the context information.</span></span>  <span data-ttu-id="e5964-126">默认值是 `Sign`。</span><span class="sxs-lookup"><span data-stu-id="e5964-126">The default value is `Sign`.</span></span>|  
|<span data-ttu-id="e5964-127">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="e5964-127">hostnameComparisonMode</span></span>|<span data-ttu-id="e5964-128">指定用于分析 URI 的 HTTP 主机名比较模式。</span><span class="sxs-lookup"><span data-stu-id="e5964-128">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="e5964-129">此属性的类型为 <xref:System.ServiceModel.HostNameComparisonMode>，指示在对 URI 进行匹配时，是否使用主机名来访问服务。</span><span class="sxs-lookup"><span data-stu-id="e5964-129">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="e5964-130">默认值为 <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>，表示忽略匹配项中的主机名。</span><span class="sxs-lookup"><span data-stu-id="e5964-130">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="e5964-131">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="e5964-131">maxBufferPoolSize</span></span>|<span data-ttu-id="e5964-132">一个整数，指定此绑定的最大缓冲池大小。</span><span class="sxs-lookup"><span data-stu-id="e5964-132">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="e5964-133">默认值为 524,288 字节 (512 \* 1024)。</span><span class="sxs-lookup"><span data-stu-id="e5964-133">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="e5964-134">Windows Communication Foundation (WCF) 的许多部件使用缓冲区。</span><span class="sxs-lookup"><span data-stu-id="e5964-134">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="e5964-135">每次使用缓冲区时，创建和销毁它们都将占用大量资源，而缓冲区的垃圾回收过程也是如此。</span><span class="sxs-lookup"><span data-stu-id="e5964-135">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="e5964-136">利用缓冲池，可以从缓冲池中获得缓冲区，使用缓冲区，然后在完成工作后将其返回给缓冲池。</span><span class="sxs-lookup"><span data-stu-id="e5964-136">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="e5964-137">这样就避免了创建和销毁缓冲区的系统开销。</span><span class="sxs-lookup"><span data-stu-id="e5964-137">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="e5964-138">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="e5964-138">maxReceivedMessageSize</span></span>|<span data-ttu-id="e5964-139">一个正整数，指定采用此绑定配置的通道上可以接收的最大消息大小（字节），包括消息头。</span><span class="sxs-lookup"><span data-stu-id="e5964-139">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="e5964-140">如果消息超出此限制，则发送方将收到 SOAP 错误。</span><span class="sxs-lookup"><span data-stu-id="e5964-140">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="e5964-141">接收方将删除该消息，并在跟踪日志中创建事件项。</span><span class="sxs-lookup"><span data-stu-id="e5964-141">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="e5964-142">默认值为 65536。</span><span class="sxs-lookup"><span data-stu-id="e5964-142">The default is 65536.</span></span>|  
|<span data-ttu-id="e5964-143">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="e5964-143">messageEncoding</span></span>|<span data-ttu-id="e5964-144">定义用于对消息进行编码的编码器。</span><span class="sxs-lookup"><span data-stu-id="e5964-144">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="e5964-145">有效值包括以下值：</span><span class="sxs-lookup"><span data-stu-id="e5964-145">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e5964-146">-Text：使用文本消息编码器。</span><span class="sxs-lookup"><span data-stu-id="e5964-146">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="e5964-147">-Mtom：使用消息传输组织机制 1.0 (MTOM) 编码器。</span><span class="sxs-lookup"><span data-stu-id="e5964-147">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><span data-ttu-id="e5964-148">-默认值为 Text。</span><span class="sxs-lookup"><span data-stu-id="e5964-148">-   The default is Text.</span></span><br /><br /> <span data-ttu-id="e5964-149">此属性的类型为 <xref:System.ServiceModel.WSMessageEncoding>。</span><span class="sxs-lookup"><span data-stu-id="e5964-149">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|<span data-ttu-id="e5964-150">name</span><span class="sxs-lookup"><span data-stu-id="e5964-150">name</span></span>|<span data-ttu-id="e5964-151">一个包含绑定的配置名称的字符串。</span><span class="sxs-lookup"><span data-stu-id="e5964-151">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="e5964-152">因为此值用作绑定的标识，所以它应该是唯一的。</span><span class="sxs-lookup"><span data-stu-id="e5964-152">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="e5964-153">从 .NET Framework 4 开始，绑定和行为不需要具有名称。</span><span class="sxs-lookup"><span data-stu-id="e5964-153">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="e5964-154">有关默认配置和无值绑定和行为的详细信息，请参阅[WCF 服务的](../../../wcf/samples/simplified-configuration-for-wcf-services.md)[简化配置](../../../wcf/simplified-configuration.md)和简化配置。</span><span class="sxs-lookup"><span data-stu-id="e5964-154">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="e5964-155">openTimeout</span><span class="sxs-lookup"><span data-stu-id="e5964-155">openTimeout</span></span>|<span data-ttu-id="e5964-156">一个 <xref:System.TimeSpan> 值，指定为完成打开操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="e5964-156">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="e5964-157">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="e5964-157">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e5964-158">默认值为 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="e5964-158">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="e5964-159">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="e5964-159">proxyAddress</span></span>|<span data-ttu-id="e5964-160">一个指定 HTTP 代理的地址的 URI。</span><span class="sxs-lookup"><span data-stu-id="e5964-160">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="e5964-161">如果 `useSystemWebProxy` 为 `true`，则此设置必须为 `null`。</span><span class="sxs-lookup"><span data-stu-id="e5964-161">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="e5964-162">默认值为 `null`。</span><span class="sxs-lookup"><span data-stu-id="e5964-162">The default is `null`.</span></span>|  
|<span data-ttu-id="e5964-163">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="e5964-163">receiveTimeout</span></span>|<span data-ttu-id="e5964-164">一个 <xref:System.TimeSpan> 值，指定为完成接收操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="e5964-164">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="e5964-165">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="e5964-165">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e5964-166">默认值为 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="e5964-166">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="e5964-167">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="e5964-167">sendTimeout</span></span>|<span data-ttu-id="e5964-168">一个 <xref:System.TimeSpan> 值，指定为完成发送操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="e5964-168">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="e5964-169">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="e5964-169">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e5964-170">默认值为 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="e5964-170">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="e5964-171">textEncoding</span><span class="sxs-lookup"><span data-stu-id="e5964-171">textEncoding</span></span>|<span data-ttu-id="e5964-172">指定要用来在绑定上发出消息的字符集编码。</span><span class="sxs-lookup"><span data-stu-id="e5964-172">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="e5964-173">有效值包括以下值：</span><span class="sxs-lookup"><span data-stu-id="e5964-173">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e5964-174">-UnicodeFffeTextEncoding： Unicode BigEndian 编码。</span><span class="sxs-lookup"><span data-stu-id="e5964-174">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="e5964-175">-Utf16TextEncoding：16位编码。</span><span class="sxs-lookup"><span data-stu-id="e5964-175">-   Utf16TextEncoding: 16-bit encoding.</span></span><br /><span data-ttu-id="e5964-176">-Utf8TextEncoding：8位编码。</span><span class="sxs-lookup"><span data-stu-id="e5964-176">-   Utf8TextEncoding: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="e5964-177">默认值为 Utf8TextEncoding。</span><span class="sxs-lookup"><span data-stu-id="e5964-177">The default is Utf8TextEncoding.</span></span><br /><br /> <span data-ttu-id="e5964-178">此属性的类型为 <xref:System.Text.Encoding>。</span><span class="sxs-lookup"><span data-stu-id="e5964-178">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|<span data-ttu-id="e5964-179">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="e5964-179">transactionFlow</span></span>|<span data-ttu-id="e5964-180">一个布尔值，指定绑定是否支持流动 WS-Transactions。</span><span class="sxs-lookup"><span data-stu-id="e5964-180">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="e5964-181">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="e5964-181">The default is `false`.</span></span>|  
|<span data-ttu-id="e5964-182">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="e5964-182">useDefaultWebProxy</span></span>|<span data-ttu-id="e5964-183">一个布尔值，指定是否使用系统的自动配置 HTTP 代理。</span><span class="sxs-lookup"><span data-stu-id="e5964-183">A Boolean value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="e5964-184">默认值为 `true`。</span><span class="sxs-lookup"><span data-stu-id="e5964-184">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e5964-185">子元素</span><span class="sxs-lookup"><span data-stu-id="e5964-185">Child Elements</span></span>  
  
|<span data-ttu-id="e5964-186">元素</span><span class="sxs-lookup"><span data-stu-id="e5964-186">Element</span></span>|<span data-ttu-id="e5964-187">说明</span><span class="sxs-lookup"><span data-stu-id="e5964-187">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-wshttpbinding.md)|<span data-ttu-id="e5964-188">定义绑定的安全设置。</span><span class="sxs-lookup"><span data-stu-id="e5964-188">Defines the security settings for the binding.</span></span> <span data-ttu-id="e5964-189">此元素的类型为 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="e5964-189">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="e5964-190">定义可由采用此绑定配置的终结点进行处理的 SOAP 消息的复杂性约束。</span><span class="sxs-lookup"><span data-stu-id="e5964-190">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="e5964-191">此元素的类型为 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="e5964-191">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[\<reliableSession>](/previous-versions/ms731375(v=vs.90))|<span data-ttu-id="e5964-192">指定是否在通道终结点之间建立可靠会话。</span><span class="sxs-lookup"><span data-stu-id="e5964-192">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e5964-193">父元素</span><span class="sxs-lookup"><span data-stu-id="e5964-193">Parent Elements</span></span>  
  
|<span data-ttu-id="e5964-194">元素</span><span class="sxs-lookup"><span data-stu-id="e5964-194">Element</span></span>|<span data-ttu-id="e5964-195">说明</span><span class="sxs-lookup"><span data-stu-id="e5964-195">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="e5964-196">此元素包含标准绑定和自定义绑定的集合。</span><span class="sxs-lookup"><span data-stu-id="e5964-196">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e5964-197">请参阅</span><span class="sxs-lookup"><span data-stu-id="e5964-197">See also</span></span>

- <xref:System.ServiceModel.WSHttpBinding>
- <xref:System.ServiceModel.WSHttpContextBinding>
- <xref:System.ServiceModel.Configuration.WSHttpContextBindingElement>
- <xref:System.ServiceModel.Channels.ContextBindingElement>
- [<span data-ttu-id="e5964-198">绑定</span><span class="sxs-lookup"><span data-stu-id="e5964-198">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e5964-199">配置系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="e5964-199">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="e5964-200">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="e5964-200">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [\<wsHttpBinding>](wshttpbinding.md)
