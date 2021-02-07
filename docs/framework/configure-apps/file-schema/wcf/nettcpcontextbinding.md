---
description: 了解详细信息： <netTcpContextBinding>
title: <netTcpContextBinding>
ms.date: 03/30/2017
ms.assetid: 1d4715e1-5fff-4c3d-a226-18f21d0b30c4
ms.openlocfilehash: 2a5eea664c4287f8da45e8d286621bb7aa358d0f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683861"
---
# \<netTcpContextBinding>

<span data-ttu-id="57a2a-102">为要求对保护级别进行签名的 <xref:System.ServiceModel.NetTcpBinding> 指定上下文。</span><span class="sxs-lookup"><span data-stu-id="57a2a-102">Specifies a context for the <xref:System.ServiceModel.NetTcpBinding> that requires that the protection level be signed.</span></span> <span data-ttu-id="57a2a-103">NetTcpContextBinding 的 contextExchangeMechanism 是 SOAPHeader。</span><span class="sxs-lookup"><span data-stu-id="57a2a-103">The contextExchangeMechanism for NetTcpContextBinding is SOAPHeader.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netTcpContextBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="57a2a-104">语法</span><span class="sxs-lookup"><span data-stu-id="57a2a-104">Syntax</span></span>  
  
```xml  
<netTcpContextBinding>
  <binding closeTimeout="TimeSpan"
           contextProtectionLevel="EncryptAndSign/None/Sign"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           listenBacklog="Integer"
           maxBufferPoolSize="integer"
           maxBufferSize="Integer"
           maxConnections="Integer"
           maxReceivedMessageSize="Integer"
           name="string"
           openTimeout="TimeSpan"
           portSharingEnabled="Boolean"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           transactionFlow="Boolean"
           transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004"
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan"
                     enabled="Boolean" />
    <security mode="Message/None/Transport/TransportWithCredential">
      <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
                 proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
                 realm="String"
                 defaultClientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
                 defaultProxyCredentialType="Basic/Digest/None/Ntlm/Windows"
                 defaultRealm="String" />
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
</netTcpContextBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="57a2a-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="57a2a-105">Attributes and Elements</span></span>  

 <span data-ttu-id="57a2a-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="57a2a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="57a2a-107">特性</span><span class="sxs-lookup"><span data-stu-id="57a2a-107">Attributes</span></span>  
  
|<span data-ttu-id="57a2a-108">属性</span><span class="sxs-lookup"><span data-stu-id="57a2a-108">Attribute</span></span>|<span data-ttu-id="57a2a-109">说明</span><span class="sxs-lookup"><span data-stu-id="57a2a-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="57a2a-110">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="57a2a-110">closeTimeout</span></span>|<span data-ttu-id="57a2a-111">一个 <xref:System.TimeSpan> 值，指定为完成关闭操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="57a2a-111">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="57a2a-112">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="57a2a-112">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="57a2a-113">默认值为 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="57a2a-113">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="57a2a-114">contextProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="57a2a-114">contextProtectionLevel</span></span>|<span data-ttu-id="57a2a-115">一个有效的 <xref:System.Net.Security.ProtectionLevel> 值，指定用于传播上下文信息的 SOAP 标头的所需保护级别。</span><span class="sxs-lookup"><span data-stu-id="57a2a-115">A valid <xref:System.Net.Security.ProtectionLevel> value that specifies the desired protection level of the SOAP header used to propagate the context information.</span></span>  <span data-ttu-id="57a2a-116">默认值是 <xref:System.Net.Security.ProtectionLevel.Sign>。</span><span class="sxs-lookup"><span data-stu-id="57a2a-116">The default value is <xref:System.Net.Security.ProtectionLevel.Sign>.</span></span>|  
|<span data-ttu-id="57a2a-117">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="57a2a-117">hostnameComparisonMode</span></span>|<span data-ttu-id="57a2a-118">指定用于分析 URI 的 HTTP 主机名比较模式。</span><span class="sxs-lookup"><span data-stu-id="57a2a-118">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="57a2a-119">此属性的类型为 <xref:System.ServiceModel.HostNameComparisonMode>，指示在对 URI 进行匹配时，是否使用主机名来访问服务。</span><span class="sxs-lookup"><span data-stu-id="57a2a-119">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="57a2a-120">默认值为 <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>，表示忽略匹配项中的主机名。</span><span class="sxs-lookup"><span data-stu-id="57a2a-120">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="57a2a-121">listenBacklog</span><span class="sxs-lookup"><span data-stu-id="57a2a-121">listenBacklog</span></span>|<span data-ttu-id="57a2a-122">一个正整数，指定侦听器上等待接受的最大通道数。</span><span class="sxs-lookup"><span data-stu-id="57a2a-122">A positive integer that specifies the maximum number of channels waiting to be accepted on the listener.</span></span> <span data-ttu-id="57a2a-123">超出此限制的连接会被排队，直到连接数低于限制值。</span><span class="sxs-lookup"><span data-stu-id="57a2a-123">Connections in excess of this limit are queued until space below the limit becomes available.</span></span> <span data-ttu-id="57a2a-124">`connectionTimeout` 属性限制客户端在引发连接异常之前将等待连接的时间。</span><span class="sxs-lookup"><span data-stu-id="57a2a-124">The `connectionTimeout` attribute limits the time a client will wait to be connected before throwing a connection exception.</span></span> <span data-ttu-id="57a2a-125">默认值为 10。</span><span class="sxs-lookup"><span data-stu-id="57a2a-125">The default is 10.</span></span>|  
|<span data-ttu-id="57a2a-126">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="57a2a-126">maxBufferPoolSize</span></span>|<span data-ttu-id="57a2a-127">一个整数，指定此绑定的最大缓冲池大小。</span><span class="sxs-lookup"><span data-stu-id="57a2a-127">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="57a2a-128">默认值为 512 \* 1024 字节。</span><span class="sxs-lookup"><span data-stu-id="57a2a-128">The default is 512 \* 1024 bytes.</span></span> <span data-ttu-id="57a2a-129">Windows Communication Foundation (WCF) 的许多部件使用缓冲区。</span><span class="sxs-lookup"><span data-stu-id="57a2a-129">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="57a2a-130">每次使用缓冲区时，创建和销毁它们都将占用大量资源，而缓冲区的垃圾回收过程也是如此。</span><span class="sxs-lookup"><span data-stu-id="57a2a-130">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="57a2a-131">利用缓冲池，可以从缓冲池中获得缓冲区，使用缓冲区，然后在完成工作后将其返回给缓冲池。</span><span class="sxs-lookup"><span data-stu-id="57a2a-131">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="57a2a-132">这样就避免了创建和销毁缓冲区的系统开销。</span><span class="sxs-lookup"><span data-stu-id="57a2a-132">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="57a2a-133">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="57a2a-133">maxBufferSize</span></span>|<span data-ttu-id="57a2a-134">一个正整数，指定内存中用于存储消息的缓冲区的最大大小（字节）。</span><span class="sxs-lookup"><span data-stu-id="57a2a-134">A positive integer that specifies the maximum size, in bytes, of the buffer used to store messages in memory.</span></span> <span data-ttu-id="57a2a-135">如果缓冲区已满，则多余的数据会保留在基础套接字中，直到缓冲区重新具有可用空间。</span><span class="sxs-lookup"><span data-stu-id="57a2a-135">If the buffer is full, excess data remains in the underlying socket until the buffer has room again.</span></span> <span data-ttu-id="57a2a-136">该值不能小于 `maxReceivedMessageSize` 属性。</span><span class="sxs-lookup"><span data-stu-id="57a2a-136">This value cannot be less than `maxReceivedMessageSize` attribute.</span></span> <span data-ttu-id="57a2a-137">默认值为 65536。</span><span class="sxs-lookup"><span data-stu-id="57a2a-137">The default is 65536.</span></span> <span data-ttu-id="57a2a-138">有关详细信息，请参阅 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>。</span><span class="sxs-lookup"><span data-stu-id="57a2a-138">For more information, see <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span></span>|  
|<span data-ttu-id="57a2a-139">maxConnections</span><span class="sxs-lookup"><span data-stu-id="57a2a-139">maxConnections</span></span>|<span data-ttu-id="57a2a-140">一个整数，指定服务将创建/接受的最大出站和入站连接数。</span><span class="sxs-lookup"><span data-stu-id="57a2a-140">An integer that specifies the maximum number of outbound and inbound connections the service will create/accept.</span></span> <span data-ttu-id="57a2a-141">传入和传出连接分别根据此属性指定的限制进行计数。</span><span class="sxs-lookup"><span data-stu-id="57a2a-141">Incoming and outgoing connections are counted against a separate limit specified by this attribute.</span></span><br /><br /> <span data-ttu-id="57a2a-142">超出此限制的入站连接需要排队，直到连接数低于限制值。</span><span class="sxs-lookup"><span data-stu-id="57a2a-142">Inbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="57a2a-143">超出此限制的出站连接需要排队，直到连接数低于限制值。</span><span class="sxs-lookup"><span data-stu-id="57a2a-143">Outbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="57a2a-144">默认值为 10。</span><span class="sxs-lookup"><span data-stu-id="57a2a-144">The default is 10.</span></span>|  
|<span data-ttu-id="57a2a-145">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="57a2a-145">maxReceivedMessageSize</span></span>|<span data-ttu-id="57a2a-146">一个正整数，指定采用此绑定配置的通道上可以接收的最大消息大小（字节），包括消息头。</span><span class="sxs-lookup"><span data-stu-id="57a2a-146">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="57a2a-147">如果消息超出此限制，则发送方将收到 SOAP 错误。</span><span class="sxs-lookup"><span data-stu-id="57a2a-147">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="57a2a-148">接收方将删除该消息，并在跟踪日志中创建事件项。</span><span class="sxs-lookup"><span data-stu-id="57a2a-148">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="57a2a-149">默认值为 65536。</span><span class="sxs-lookup"><span data-stu-id="57a2a-149">The default is 65536.</span></span>|  
|<span data-ttu-id="57a2a-150">name</span><span class="sxs-lookup"><span data-stu-id="57a2a-150">name</span></span>|<span data-ttu-id="57a2a-151">一个包含绑定的配置名称的字符串。</span><span class="sxs-lookup"><span data-stu-id="57a2a-151">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="57a2a-152">因为此值用作绑定的标识，所以它应该是唯一的。</span><span class="sxs-lookup"><span data-stu-id="57a2a-152">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="57a2a-153">从 .NET Framework 4 开始，绑定和行为不需要具有名称。</span><span class="sxs-lookup"><span data-stu-id="57a2a-153">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="57a2a-154">有关默认配置和无值绑定和行为的详细信息，请参阅[WCF 服务的](../../../wcf/samples/simplified-configuration-for-wcf-services.md)[简化配置](../../../wcf/simplified-configuration.md)和简化配置。</span><span class="sxs-lookup"><span data-stu-id="57a2a-154">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="57a2a-155">openTimeout</span><span class="sxs-lookup"><span data-stu-id="57a2a-155">openTimeout</span></span>|<span data-ttu-id="57a2a-156">一个 <xref:System.TimeSpan> 值，指定为完成打开操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="57a2a-156">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="57a2a-157">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="57a2a-157">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="57a2a-158">默认值为 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="57a2a-158">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="57a2a-159">portSharingEnabled</span><span class="sxs-lookup"><span data-stu-id="57a2a-159">portSharingEnabled</span></span>|<span data-ttu-id="57a2a-160">一个布尔值，指定是否为此连接启用 TCP 端口共享。</span><span class="sxs-lookup"><span data-stu-id="57a2a-160">A Boolean value that specifies whether TCP port sharing is enabled for this connection.</span></span> <span data-ttu-id="57a2a-161">如果此值为 `false`，则每个绑定都使用自己的独占端口。</span><span class="sxs-lookup"><span data-stu-id="57a2a-161">If this is `false`, each binding uses its own exclusive port.</span></span> <span data-ttu-id="57a2a-162">此设置只与服务相关，因为客户端不受影响。</span><span class="sxs-lookup"><span data-stu-id="57a2a-162">This setting is relevant only to services, because clients are not affected.</span></span>|  
|<span data-ttu-id="57a2a-163">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="57a2a-163">receiveTimeout</span></span>|<span data-ttu-id="57a2a-164">一个 <xref:System.TimeSpan> 值，指定为完成接收操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="57a2a-164">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="57a2a-165">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="57a2a-165">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="57a2a-166">默认值为 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="57a2a-166">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="57a2a-167">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="57a2a-167">sendTimeout</span></span>|<span data-ttu-id="57a2a-168">一个 <xref:System.TimeSpan> 值，指定为完成发送操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="57a2a-168">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="57a2a-169">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="57a2a-169">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="57a2a-170">默认值为 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="57a2a-170">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="57a2a-171">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="57a2a-171">transactionFlow</span></span>|<span data-ttu-id="57a2a-172">一个布尔值，指定绑定是否支持流动 WS-Transactions。</span><span class="sxs-lookup"><span data-stu-id="57a2a-172">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="57a2a-173">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="57a2a-173">The default is `false`.</span></span>|  
|<span data-ttu-id="57a2a-174">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="57a2a-174">transactionProtocol</span></span>|<span data-ttu-id="57a2a-175">指定与此绑定一起使用的事务处理协议。</span><span class="sxs-lookup"><span data-stu-id="57a2a-175">Specifies the transaction protocol to be used with this binding.</span></span> <span data-ttu-id="57a2a-176">有效值为</span><span class="sxs-lookup"><span data-stu-id="57a2a-176">Valid values are</span></span><br /><br /> <span data-ttu-id="57a2a-177">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="57a2a-177">-   OleTransactions</span></span><br /><span data-ttu-id="57a2a-178">-WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="57a2a-178">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="57a2a-179">默认值为 OleTransactions。</span><span class="sxs-lookup"><span data-stu-id="57a2a-179">The default is OleTransactions.</span></span> <span data-ttu-id="57a2a-180">此属性的类型为 <xref:System.ServiceModel.TransactionProtocol>。</span><span class="sxs-lookup"><span data-stu-id="57a2a-180">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
|<span data-ttu-id="57a2a-181">transferMode</span><span class="sxs-lookup"><span data-stu-id="57a2a-181">transferMode</span></span>|<span data-ttu-id="57a2a-182">一个 <xref:System.ServiceModel.TransferMode> 值，指定为请求或响应对消息进行缓冲处理还是流式处理。</span><span class="sxs-lookup"><span data-stu-id="57a2a-182">A <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed or a request or response.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="57a2a-183">子元素</span><span class="sxs-lookup"><span data-stu-id="57a2a-183">Child Elements</span></span>  
  
|<span data-ttu-id="57a2a-184">元素</span><span class="sxs-lookup"><span data-stu-id="57a2a-184">Element</span></span>|<span data-ttu-id="57a2a-185">说明</span><span class="sxs-lookup"><span data-stu-id="57a2a-185">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-nettcpbinding.md)|<span data-ttu-id="57a2a-186">定义绑定的安全设置。</span><span class="sxs-lookup"><span data-stu-id="57a2a-186">Defines the security settings for the binding.</span></span> <span data-ttu-id="57a2a-187">此元素的类型为 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="57a2a-187">This element is of type <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>.</span></span>|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="57a2a-188">定义可由采用此绑定配置的终结点进行处理的 SOAP 消息的复杂性约束。</span><span class="sxs-lookup"><span data-stu-id="57a2a-188">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="57a2a-189">此元素的类型为 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="57a2a-189">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[\<reliableSession>](/previous-versions/ms731375(v=vs.90))|<span data-ttu-id="57a2a-190">指定是否在通道终结点之间建立可靠会话。</span><span class="sxs-lookup"><span data-stu-id="57a2a-190">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="57a2a-191">父元素</span><span class="sxs-lookup"><span data-stu-id="57a2a-191">Parent Elements</span></span>  
  
|<span data-ttu-id="57a2a-192">元素</span><span class="sxs-lookup"><span data-stu-id="57a2a-192">Element</span></span>|<span data-ttu-id="57a2a-193">说明</span><span class="sxs-lookup"><span data-stu-id="57a2a-193">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="57a2a-194">此元素包含标准绑定和自定义绑定的集合。</span><span class="sxs-lookup"><span data-stu-id="57a2a-194">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="57a2a-195">请参阅</span><span class="sxs-lookup"><span data-stu-id="57a2a-195">See also</span></span>

- <xref:System.ServiceModel.NetTcpBinding>
- <xref:System.ServiceModel.NetTcpContextBinding>
- <xref:System.ServiceModel.Configuration.NetTcpContextBindingElement>
- <xref:System.ServiceModel.Channels.ContextBindingElement>
- [\<netTcpBinding>](nettcpbinding.md)
- [<span data-ttu-id="57a2a-196">绑定</span><span class="sxs-lookup"><span data-stu-id="57a2a-196">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="57a2a-197">配置系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="57a2a-197">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="57a2a-198">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="57a2a-198">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
