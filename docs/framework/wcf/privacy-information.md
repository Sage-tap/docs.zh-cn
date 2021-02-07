---
description: 了解详细信息： Windows Communication Foundation 隐私信息
title: Windows Communication Foundation 隐私信息
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, privacy information
- WCF, privacy information
- privacy information [WCF]
ms.assetid: c9553724-f3e7-45cb-9ea5-450a22d309d9
ms.openlocfilehash: 4f942e84a072d15a12b6db7cc2c310d629a59f6b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726684"
---
# <a name="windows-communication-foundation-privacy-information"></a><span data-ttu-id="b4053-103">Windows Communication Foundation 隐私信息</span><span class="sxs-lookup"><span data-stu-id="b4053-103">Windows Communication Foundation Privacy Information</span></span>

<span data-ttu-id="b4053-104">Microsoft 承诺保护最终用户的隐私。</span><span class="sxs-lookup"><span data-stu-id="b4053-104">Microsoft is committed to protecting end user privacy.</span></span> <span data-ttu-id="b4053-105">使用 Windows Communication Foundation (WCF) 版本3.0 生成应用程序时，应用程序可能会影响最终用户的隐私。</span><span class="sxs-lookup"><span data-stu-id="b4053-105">When you build an application using Windows Communication Foundation (WCF), version 3.0, your application may impact your end users' privacy.</span></span> <span data-ttu-id="b4053-106">例如，应用程序可能显式收集用户联系信息，或者通过 Internet 向您的网站请求或发送信息。</span><span class="sxs-lookup"><span data-stu-id="b4053-106">For example, your application may explicitly collect user contact information, or it may request or send information over the Internet to your Web site.</span></span> <span data-ttu-id="b4053-107">如果您在应用程序中嵌入了 Microsoft 技术，则该技术可能具有可能会影响隐私的自己的行为。</span><span class="sxs-lookup"><span data-stu-id="b4053-107">If you embed Microsoft technology in your application, that technology may have its own behavior that might affect privacy.</span></span> <span data-ttu-id="b4053-108">WCF 不会从你的应用程序向 Microsoft 发送任何信息，除非你或最终用户选择将其发送给我们。</span><span class="sxs-lookup"><span data-stu-id="b4053-108">WCF does not send any information to Microsoft from your application unless you or the end user choose to send it to us.</span></span>  
  
## <a name="wcf-in-brief"></a><span data-ttu-id="b4053-109">WCF 概述</span><span class="sxs-lookup"><span data-stu-id="b4053-109">WCF in Brief</span></span>  

 <span data-ttu-id="b4053-110">WCF 是使用 Microsoft .NET 框架的分布式消息框架，允许开发人员生成分布式应用程序。</span><span class="sxs-lookup"><span data-stu-id="b4053-110">WCF is a distributed messaging framework using the Microsoft .NET Framework that allows developers to build distributed applications.</span></span> <span data-ttu-id="b4053-111">在两个应用程序之间交换的消息包含标头和正文信息。</span><span class="sxs-lookup"><span data-stu-id="b4053-111">Messages communicated between two applications contain header and body information.</span></span>  
  
 <span data-ttu-id="b4053-112">标头可能包含消息路由、安全信息、事务和其他信息，具体取决于应用程序所使用的服务。</span><span class="sxs-lookup"><span data-stu-id="b4053-112">Headers may contain message routing, security information, transactions, and more depending on the services used by the application.</span></span> <span data-ttu-id="b4053-113">默认情况下，消息通常要进行加密。</span><span class="sxs-lookup"><span data-stu-id="b4053-113">Messages are typically encrypted by default.</span></span> <span data-ttu-id="b4053-114">一个例外的情况是使用 `BasicHttpBinding`（它适用于不受保护的旧式 Web 服务）。</span><span class="sxs-lookup"><span data-stu-id="b4053-114">The one exception is when using the `BasicHttpBinding`, which was designed for use with non-secured, legacy Web services.</span></span> <span data-ttu-id="b4053-115">作为应用程序设计人员，您负责进行最终设计。</span><span class="sxs-lookup"><span data-stu-id="b4053-115">As the application designer, you are responsible for the final design.</span></span> <span data-ttu-id="b4053-116">SOAP 正文中的消息包含特定于应用程序的数据;不过，这些数据（如应用程序定义的个人信息）可以通过使用 WCF 加密或机密性功能来保护。</span><span class="sxs-lookup"><span data-stu-id="b4053-116">Messages in the SOAP body contain application-specific data; however, this data, such as application-defined personal information, can be secured by using WCF encryption or confidentiality features.</span></span> <span data-ttu-id="b4053-117">以下几节将描述可能对隐私造成影响的功能。</span><span class="sxs-lookup"><span data-stu-id="b4053-117">The following sections describe the features that potentially impact privacy.</span></span>  
  
## <a name="messaging"></a><span data-ttu-id="b4053-118">Messaging</span><span class="sxs-lookup"><span data-stu-id="b4053-118">Messaging</span></span>  

 <span data-ttu-id="b4053-119">每个 WCF 消息都有一个地址标头，该标头指定消息目标和答复的目标位置。</span><span class="sxs-lookup"><span data-stu-id="b4053-119">Each WCF message has an address header that specifies the message destination and where the reply should go.</span></span>  
  
 <span data-ttu-id="b4053-120">终结点地址的地址部分是一个标识该终结点的统一资源标识符 (URI)。</span><span class="sxs-lookup"><span data-stu-id="b4053-120">The address component of an endpoint address is a Uniform Resource Identifier (URI) that identifies the endpoint.</span></span> <span data-ttu-id="b4053-121">该地址可以是网络地址，也可以是逻辑地址。</span><span class="sxs-lookup"><span data-stu-id="b4053-121">The address can be a network address or a logical address.</span></span> <span data-ttu-id="b4053-122">该地址可能包含计算机名称（主机名、完全限定域名）和一个 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="b4053-122">The address may include machine name (hostname, fully qualified domain name) and an IP address.</span></span> <span data-ttu-id="b4053-123">终结点地址还可能包含一个用于进行临时寻址的全局唯一标识符 (GUID) 或 GUID 集合，以便辨别每个地址。</span><span class="sxs-lookup"><span data-stu-id="b4053-123">The endpoint address may also contain a globally unique identifier (GUID), or a collection of GUIDs for temporary addressing used to discern each address.</span></span> <span data-ttu-id="b4053-124">每个消息都包含一个消息 ID，该消息 ID 是 GUID。</span><span class="sxs-lookup"><span data-stu-id="b4053-124">Each message contains a message ID that is a GUID.</span></span> <span data-ttu-id="b4053-125">此功能遵循 WS-Addressing 引用标准。</span><span class="sxs-lookup"><span data-stu-id="b4053-125">This feature follows the WS-Addressing reference standard.</span></span>  
  
 <span data-ttu-id="b4053-126">WCF 消息传递层不会向本地计算机写入任何个人信息。</span><span class="sxs-lookup"><span data-stu-id="b4053-126">The WCF messaging layer does not write any personal information to the local machine.</span></span> <span data-ttu-id="b4053-127">但是，如果服务开发人员创建了公开此类信息的服务（例如，通过在终结点名称中使用个人姓名，或者将个人信息包含在终结点的 Web 服务描述语言中，但不要求客户端使用 https 来访问 WSDL），则消息传递层可能会在网络级传播个人信息。</span><span class="sxs-lookup"><span data-stu-id="b4053-127">However, it might propagate personal information at the network level if a service developer has created a service that exposes such information (for example, by using a person's name in an endpoint name, or including personal information in the endpoint's Web Services Description Language but not requiring clients to use https to access the WSDL).</span></span> <span data-ttu-id="b4053-128">此外，如果开发人员对公开个人信息的终结点运行 " [)  ( 的元数据实用工具" 工具 ](servicemodel-metadata-utility-tool-svcutil-exe.md) ，则该工具的输出可能包含该信息，并且输出文件将写入本地硬盘。</span><span class="sxs-lookup"><span data-stu-id="b4053-128">Also, if a developer runs the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) tool against an endpoint that exposes personal information, the tool's output could contain that information, and the output file is written to the local hard disk.</span></span>  
  
## <a name="hosting"></a><span data-ttu-id="b4053-129">Hosting</span><span class="sxs-lookup"><span data-stu-id="b4053-129">Hosting</span></span>  

 <span data-ttu-id="b4053-130">WCF 中的托管功能使应用程序可以按需启动，或者允许在多个应用程序之间共享端口。</span><span class="sxs-lookup"><span data-stu-id="b4053-130">The hosting feature in WCF allows applications to start on demand or to enable port sharing between multiple applications.</span></span> <span data-ttu-id="b4053-131">WCF 应用程序可以在 Internet Information Services (IIS) 中承载，类似于 ASP.NET。</span><span class="sxs-lookup"><span data-stu-id="b4053-131">A WCF application can be hosted in Internet Information Services (IIS), similar to ASP.NET.</span></span>  
  
 <span data-ttu-id="b4053-132">承载功能不会在网路上公开任何特定信息，也不会在计算机上保留数据。</span><span class="sxs-lookup"><span data-stu-id="b4053-132">Hosting does not expose any specific information on the network and it does not keep data on the machine.</span></span>  
  
## <a name="message-security"></a><span data-ttu-id="b4053-133">消息安全</span><span class="sxs-lookup"><span data-stu-id="b4053-133">Message Security</span></span>  

 <span data-ttu-id="b4053-134">WCF 安全性为消息传递应用程序提供安全功能。</span><span class="sxs-lookup"><span data-stu-id="b4053-134">WCF security provides the security capabilities for messaging applications.</span></span> <span data-ttu-id="b4053-135">所提供的安全功能包括身份验证和授权。</span><span class="sxs-lookup"><span data-stu-id="b4053-135">The security functions provided include authentication and authorization.</span></span>  
  
 <span data-ttu-id="b4053-136">身份验证通过在客户端和服务之间传递凭据来执行。</span><span class="sxs-lookup"><span data-stu-id="b4053-136">Authentication is performed by passing credentials between the clients and services.</span></span> <span data-ttu-id="b4053-137">身份验证可以通过传输级安全实现，也可以通过 SOAP 消息级安全实现，如下所述：</span><span class="sxs-lookup"><span data-stu-id="b4053-137">Authentication can be either through transport-level security or through SOAP message-level security, as follows:</span></span>  
  
- <span data-ttu-id="b4053-138">在 SOAP 消息安全中，身份验证通过诸如用户名/密码、X.509 证书、Kerberos 票证以及 SAML 令牌等凭据来执行，所有这些凭据都可能包含个人信息（根据颁发机构的情况而定）。</span><span class="sxs-lookup"><span data-stu-id="b4053-138">In SOAP message security, authentication is performed through credentials like username/passwords, X.509 certificates, Kerberos tickets, and SAML tokens, all of which might contain personal information, depending on the issuer.</span></span>  
  
- <span data-ttu-id="b4053-139">使用传输安全时，身份验证通过传统的传输身份验证机制来实现，如 HTTP 身份验证方案（基本、摘要式、协商、集成 Windows 身份验证、NTLM、无身份验证和匿名）和窗体身份验证。</span><span class="sxs-lookup"><span data-stu-id="b4053-139">Using transport security, authentication is done through traditional transport authentication mechanisms like HTTP authentication schemes (Basic, Digest, Negotiate, Integrated Windows Authorization, NTLM, None, and Anonymous), and form authentication.</span></span>  
  
 <span data-ttu-id="b4053-140">身份验证可以导致在相互通信的终结点之间建立安全会话。</span><span class="sxs-lookup"><span data-stu-id="b4053-140">Authentication can result in a secure session established between the communicating endpoints.</span></span> <span data-ttu-id="b4053-141">会话由 GUID 标识，而 GUID 能够在安全会话的整个生存期保持有效。</span><span class="sxs-lookup"><span data-stu-id="b4053-141">The session is identified by a GUID that lasts the lifetime of the security session.</span></span> <span data-ttu-id="b4053-142">下表显示保留的内容和保留位置。</span><span class="sxs-lookup"><span data-stu-id="b4053-142">The following table shows what is kept and where.</span></span>  
  
|<span data-ttu-id="b4053-143">数据</span><span class="sxs-lookup"><span data-stu-id="b4053-143">Data</span></span>|<span data-ttu-id="b4053-144">存储</span><span class="sxs-lookup"><span data-stu-id="b4053-144">Storage</span></span>|  
|----------|-------------|  
|<span data-ttu-id="b4053-145">表示凭据，例如用户名、X.509 证书、Kerberos 令牌和对凭据的引用。</span><span class="sxs-lookup"><span data-stu-id="b4053-145">Presentation credentials, such as username, X.509 certificates, Kerberos tokens, and references to credentials.</span></span>|<span data-ttu-id="b4053-146">标准 Windows 凭据管理机制，例如 Windows 证书存储区。</span><span class="sxs-lookup"><span data-stu-id="b4053-146">Standard Windows credential management mechanisms such as the Windows certificate store.</span></span>|  
|<span data-ttu-id="b4053-147">用户成员资格信息，例如用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="b4053-147">User membership information, such as usernames and passwords.</span></span>|<span data-ttu-id="b4053-148">ASP.NET 成员资格提供程序。</span><span class="sxs-lookup"><span data-stu-id="b4053-148">ASP.NET membership providers.</span></span>|  
|<span data-ttu-id="b4053-149">用于向客户端证明服务身份的有关服务的标识信息。</span><span class="sxs-lookup"><span data-stu-id="b4053-149">Identity information about the service used to authenticate the service to clients.</span></span>|<span data-ttu-id="b4053-150">服务的终结点地址。</span><span class="sxs-lookup"><span data-stu-id="b4053-150">Endpoint address of the service.</span></span>|  
|<span data-ttu-id="b4053-151">调用方信息。</span><span class="sxs-lookup"><span data-stu-id="b4053-151">Caller information.</span></span>|<span data-ttu-id="b4053-152">审核日志。</span><span class="sxs-lookup"><span data-stu-id="b4053-152">Auditing logs.</span></span>|  
  
## <a name="auditing"></a><span data-ttu-id="b4053-153">审核</span><span class="sxs-lookup"><span data-stu-id="b4053-153">Auditing</span></span>  

 <span data-ttu-id="b4053-154">审核功能用于记录身份验证和授权事件的成功和失败。</span><span class="sxs-lookup"><span data-stu-id="b4053-154">Auditing records the success and failure of authentication and authorization events.</span></span> <span data-ttu-id="b4053-155">审核记录包含以下数据：服务 URI、操作 URI 和调用方的标识。</span><span class="sxs-lookup"><span data-stu-id="b4053-155">Auditing records contain the following data: service URI, action URI, and the caller's identification.</span></span>  
  
 <span data-ttu-id="b4053-156">审核功能还记录管理员修改消息日志记录的配置（启用或禁用）的时间，因为消息日志记录可能记录标头或正文中特定于应用程序的数据。</span><span class="sxs-lookup"><span data-stu-id="b4053-156">Auditing also records when the administrator modifies the configuration of message logging (turning it on or off), because message logging may log application-specific data in headers and bodies.</span></span> <span data-ttu-id="b4053-157">对于 Windows XP，记录记录在应用程序事件日志中。</span><span class="sxs-lookup"><span data-stu-id="b4053-157">For Windows XP, a record is logged in the application event log.</span></span> <span data-ttu-id="b4053-158">对于 Windows Vista 和 Windows Server 2003，会在安全事件日志中记录一条记录。</span><span class="sxs-lookup"><span data-stu-id="b4053-158">For Windows Vista and Windows Server 2003, a record is logged in the security event log.</span></span>  
  
## <a name="transactions"></a><span data-ttu-id="b4053-159">事务</span><span class="sxs-lookup"><span data-stu-id="b4053-159">Transactions</span></span>  

 <span data-ttu-id="b4053-160">事务功能为 WCF 应用程序提供事务性服务。</span><span class="sxs-lookup"><span data-stu-id="b4053-160">The transactions feature provides transactional services to a WCF application.</span></span>  
  
 <span data-ttu-id="b4053-161">事务传播中使用的事物标头可能包含事务 ID 或登记 ID（这些 ID 都是 GUID）。</span><span class="sxs-lookup"><span data-stu-id="b4053-161">Transaction headers used in transaction propagation may contain Transaction IDs or Enlistment IDs, which are GUIDs.</span></span>  
  
 <span data-ttu-id="b4053-162">事务功能使用 Microsoft 分布式事务协调器 (MSDTC) 事务管理器（一个 Windows 组件）来管理事务状态。</span><span class="sxs-lookup"><span data-stu-id="b4053-162">The Transactions feature uses the Microsoft Distributed Transaction Coordinator (MSDTC) Transaction Manager (a Windows component) to manage transaction state.</span></span> <span data-ttu-id="b4053-163">默认情况下，事务管理器之间的通信进行加密。</span><span class="sxs-lookup"><span data-stu-id="b4053-163">By default, communications between Transactions Managers are encrypted.</span></span> <span data-ttu-id="b4053-164">事务管理器会将终结点引用、事务 ID 和登记 ID 作为其持久状态的一部分进行记录。</span><span class="sxs-lookup"><span data-stu-id="b4053-164">Transaction Managers may log endpoint references, Transaction IDs, and Enlistment IDs as part of their durable state.</span></span> <span data-ttu-id="b4053-165">此状态的生存期由事务管理器的日志文件的生存期确定。</span><span class="sxs-lookup"><span data-stu-id="b4053-165">The lifetime of this state is determined by the lifetime of the Transaction Manager’s log file.</span></span> <span data-ttu-id="b4053-166">MSDTC 服务拥有并维护此日志。</span><span class="sxs-lookup"><span data-stu-id="b4053-166">The MSDTC service owns and maintains this log.</span></span>  
  
 <span data-ttu-id="b4053-167">事务功能实现了 WS-Coordination 和 WS-Atomic 事务标准。</span><span class="sxs-lookup"><span data-stu-id="b4053-167">The Transactions feature implements the WS-Coordination and WS-Atomic Transaction standards.</span></span>  
  
## <a name="reliable-sessions"></a><span data-ttu-id="b4053-168">可靠会话</span><span class="sxs-lookup"><span data-stu-id="b4053-168">Reliable Sessions</span></span>  

 <span data-ttu-id="b4053-169">WCF 中的可靠会话在发生传输或中介故障时提供消息传输。</span><span class="sxs-lookup"><span data-stu-id="b4053-169">Reliable sessions in WCF provide the transfer of messages when transport or intermediary failures occur.</span></span> <span data-ttu-id="b4053-170">甚至在基础传输断开（例如，无线网络上的 TCP 连接断开）或丢失消息（HTTP 代理丢弃传出消息或传入消息）时，它们也会提供“一次性”消息传送。</span><span class="sxs-lookup"><span data-stu-id="b4053-170">They provide an exactly-once transfer of messages even when the underlying transport disconnects (for example, a TCP connection on a wireless network) or loses a message (an HTTP proxy dropping an outgoing or incoming message).</span></span> <span data-ttu-id="b4053-171">可靠会话还可以恢复消息重新排序（这可能在多路径路由的情况下发生），从而保留消息的发送顺序。</span><span class="sxs-lookup"><span data-stu-id="b4053-171">Reliable sessions also recover message reordering (as may happen in the case of multipath routing), preserving the order in which the messages were sent.</span></span>  
  
 <span data-ttu-id="b4053-172">可靠会话是使用 WS-ReliableMessaging (WS-RM) 协议来实现的。</span><span class="sxs-lookup"><span data-stu-id="b4053-172">Reliable sessions are implemented using the WS-ReliableMessaging (WS-RM) protocol.</span></span> <span data-ttu-id="b4053-173">可靠会话添加包含会话信息的 WS-RM 标头，这些会话信息用于标识与特定可靠会话关联的所有消息。</span><span class="sxs-lookup"><span data-stu-id="b4053-173">They add WS-RM headers that contain session information, which is used to identify all messages associated with a particular reliable session.</span></span> <span data-ttu-id="b4053-174">每个 WS-RM 会话都有一个 GUID 标识符。</span><span class="sxs-lookup"><span data-stu-id="b4053-174">Each WS-RM session has an identifier, which is a GUID.</span></span>  
  
 <span data-ttu-id="b4053-175">最终用户的计算机上不会保留任何个人信息。</span><span class="sxs-lookup"><span data-stu-id="b4053-175">No personal information is retained on the end user's machine.</span></span>  
  
## <a name="queued-channels"></a><span data-ttu-id="b4053-176">排队通道</span><span class="sxs-lookup"><span data-stu-id="b4053-176">Queued Channels</span></span>  

 <span data-ttu-id="b4053-177">队列代表接收应用程序存储来自发送应用程序的消息，之后再将这些消息转发给接收应用程序。</span><span class="sxs-lookup"><span data-stu-id="b4053-177">Queues store messages from a sending application on behalf of a receiving application and later forward these messages to the receiving application.</span></span> <span data-ttu-id="b4053-178">队列有助于在某些情况下（例如，接收应用程序是瞬态应用程序）确保消息从发送应用程序传送到接收应用程序。</span><span class="sxs-lookup"><span data-stu-id="b4053-178">They help ensure the transfer of messages from sending applications to receiving applications when, for example, the receiving application is transient.</span></span> <span data-ttu-id="b4053-179">WCF 通过使用 Microsoft 消息队列 (MSMQ) 作为传输来提供对队列的支持。</span><span class="sxs-lookup"><span data-stu-id="b4053-179">WCF provides support for queuing by using Microsoft Message Queuing (MSMQ) as a transport.</span></span>  
  
 <span data-ttu-id="b4053-180">排队通道功能不会向消息中添加标头。</span><span class="sxs-lookup"><span data-stu-id="b4053-180">The queued channels feature does not add headers to a message.</span></span> <span data-ttu-id="b4053-181">相反，它会创建一个具有适当的消息队列消息属性集的消息队列消息，并调用消息队列方法来将消息放入“消息队列”队列中。</span><span class="sxs-lookup"><span data-stu-id="b4053-181">Instead it creates a Message Queuing message with appropriate Message Queuing message properties set, and invokes Message Queuing methods to put the message in the Message Queuing queue.</span></span> <span data-ttu-id="b4053-182">消息队列是一个可选组件，它随 Windows 一起提供。</span><span class="sxs-lookup"><span data-stu-id="b4053-182">Message Queuing is an optional component that ships with Windows.</span></span>  
  
 <span data-ttu-id="b4053-183">排队通道功能不会将任何信息保留在最终用户的计算机上，因为它使用消息队列作为队列基础结构。</span><span class="sxs-lookup"><span data-stu-id="b4053-183">No information is retained on the end user's machine by the queued channels feature, because it uses Message Queuing as the queuing infrastructure.</span></span>  
  
## <a name="com-integration"></a><span data-ttu-id="b4053-184">COM+ 集成</span><span class="sxs-lookup"><span data-stu-id="b4053-184">COM+ Integration</span></span>  

 <span data-ttu-id="b4053-185">此功能包装现有的 COM 和 COM + 功能，以创建与 WCF 服务兼容的服务。</span><span class="sxs-lookup"><span data-stu-id="b4053-185">This feature wraps existing COM and COM+ functionality to create services that are compatible with WCF services.</span></span> <span data-ttu-id="b4053-186">此功能不使用特定的标头，并且不会在最终用户的计算机上保留数据。</span><span class="sxs-lookup"><span data-stu-id="b4053-186">This feature does not use specific headers and it does not retain data on the end user's machine.</span></span>  
  
## <a name="com-service-moniker"></a><span data-ttu-id="b4053-187">COM 服务标记</span><span class="sxs-lookup"><span data-stu-id="b4053-187">COM Service Moniker</span></span>  

 <span data-ttu-id="b4053-188">这为标准 WCF 客户端提供非托管包装。</span><span class="sxs-lookup"><span data-stu-id="b4053-188">This provides an unmanaged wrapper to a standard WCF client.</span></span> <span data-ttu-id="b4053-189">此功能在网络上没有特定的标头，也不会在计算机上持久保留数据。</span><span class="sxs-lookup"><span data-stu-id="b4053-189">This feature does not have specific headers on the wire nor does it persist data on the machine.</span></span>  
  
## <a name="peer-channel"></a><span data-ttu-id="b4053-190">对等通道</span><span class="sxs-lookup"><span data-stu-id="b4053-190">Peer Channel</span></span>  

 <span data-ttu-id="b4053-191">对等通道允许使用 WCF 开发多方应用程序。</span><span class="sxs-lookup"><span data-stu-id="b4053-191">A peer channel enables development of multiparty applications using WCF.</span></span> <span data-ttu-id="b4053-192">多方消息传递发生在网格环境中。</span><span class="sxs-lookup"><span data-stu-id="b4053-192">Multiparty messaging occurs in the context of a mesh.</span></span> <span data-ttu-id="b4053-193">网格由节点可以加入的名称来标识。</span><span class="sxs-lookup"><span data-stu-id="b4053-193">Meshes are identified by a name that nodes can join.</span></span> <span data-ttu-id="b4053-194">对等通道中的每个节点都在用户指定的端口创建一个 TCP 侦听器，并与网格中的其他节点建立连接以确保连接的弹性。</span><span class="sxs-lookup"><span data-stu-id="b4053-194">Each node in the peer channel creates a TCP listener at a user-specified port and establishes connections with other nodes in the mesh to ensure resiliency.</span></span> <span data-ttu-id="b4053-195">为了与网格中的其他节点进行连接，节点还会与网格中的其他节点交换一些数据，包括侦听器地址和计算机的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="b4053-195">To connect to other nodes in the mesh, nodes also exchange some data, including the listener address and the machine's IP addresses, with other nodes in the mesh.</span></span> <span data-ttu-id="b4053-196">在网格中四处发送的消息可能包含与发送方相关的安全信息，以防止发生消息欺骗和篡改。</span><span class="sxs-lookup"><span data-stu-id="b4053-196">Messages sent around in the mesh can contain security information that pertains to the sender to prevent message spoofing and tampering.</span></span>  
  
 <span data-ttu-id="b4053-197">最终用户的计算机上不存储任何个人信息。</span><span class="sxs-lookup"><span data-stu-id="b4053-197">No personal information is stored on the end user's machine.</span></span>  
  
## <a name="it-professional-experience"></a><span data-ttu-id="b4053-198">IT 专业经验</span><span class="sxs-lookup"><span data-stu-id="b4053-198">IT Professional Experience</span></span>  
  
### <a name="tracing"></a><span data-ttu-id="b4053-199">跟踪</span><span class="sxs-lookup"><span data-stu-id="b4053-199">Tracing</span></span>  

 <span data-ttu-id="b4053-200">WCF 基础结构的诊断功能记录传递到传输和服务模型层的消息，以及与这些消息关联的活动和事件。</span><span class="sxs-lookup"><span data-stu-id="b4053-200">The diagnostics feature of the WCF infrastructure logs messages that pass through the transport and service model layers, and the activities and events associated with these messages.</span></span> <span data-ttu-id="b4053-201">默认情况下，此功能处于禁用状态。</span><span class="sxs-lookup"><span data-stu-id="b4053-201">This feature is turned off by default.</span></span> <span data-ttu-id="b4053-202">使用应用程序的配置文件启用此功能，并且可以在运行时使用 WCF WMI 提供程序修改跟踪行为。</span><span class="sxs-lookup"><span data-stu-id="b4053-202">It is enabled using the application’s configuration file and the tracing behavior may be modified using the WCF WMI provider at run time.</span></span> <span data-ttu-id="b4053-203">在启用此功能后，跟踪基础结构会向已配置的侦听器发出包含消息、活动和处理事件的诊断跟踪。</span><span class="sxs-lookup"><span data-stu-id="b4053-203">When enabled, the tracing infrastructure emits a diagnostic trace that contains messages, activities, and processing events to configured listeners.</span></span> <span data-ttu-id="b4053-204">输出的格式和位置由管理员的侦听器配置选择确定，但通常是 XML 格式化文件。</span><span class="sxs-lookup"><span data-stu-id="b4053-204">The format and location of the output are determined by the administrator’s listener configuration choices, but is typically an XML formatted file.</span></span> <span data-ttu-id="b4053-205">管理员负责设置跟踪文件上的访问控制列表 (ACL)。</span><span class="sxs-lookup"><span data-stu-id="b4053-205">The administrator is responsible for setting the access control list (ACL) on the trace files.</span></span> <span data-ttu-id="b4053-206">具体而言，在由 Windows 激活系统 (WAS) 进行承载时，管理员应确保不是从公共虚拟根目录提供这些文件（如果不需要）。</span><span class="sxs-lookup"><span data-stu-id="b4053-206">In particular, when hosted by Windows Activation System (WAS), the administrator should make sure the files are not served from the public virtual root directory if that is not desired.</span></span>  
  
 <span data-ttu-id="b4053-207">有两种类型的跟踪：消息日志记录和服务模型诊断跟踪，下一节将对其进行介绍。</span><span class="sxs-lookup"><span data-stu-id="b4053-207">There are two types of tracing: Message logging and Service Model diagnostic tracing, described in the following section.</span></span> <span data-ttu-id="b4053-208">每种类型都通过其自身的跟踪源进行配置，它们分别是 <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> 和 <xref:System.ServiceModel>。</span><span class="sxs-lookup"><span data-stu-id="b4053-208">Each type is configured through its own trace source: <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> and <xref:System.ServiceModel>.</span></span> <span data-ttu-id="b4053-209">这两种日志记录跟踪源都捕获应用程序本地的数据。</span><span class="sxs-lookup"><span data-stu-id="b4053-209">Both of these logging trace sources capture data that is local to the application.</span></span>  
  
### <a name="message-logging"></a><span data-ttu-id="b4053-210">消息日志记录</span><span class="sxs-lookup"><span data-stu-id="b4053-210">Message Logging</span></span>  

 <span data-ttu-id="b4053-211">消息日志记录跟踪源（<xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>）使管理员可以记录流经系统的消息。</span><span class="sxs-lookup"><span data-stu-id="b4053-211">The message logging trace source (<xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>) allows an administrator to log the messages that flow through the system.</span></span> <span data-ttu-id="b4053-212">通过配置，用户可以决定是记录完整的消息还是仅记录消息头、是否在传输和/或服务模型层记录以及是否包括格式不正确的消息。</span><span class="sxs-lookup"><span data-stu-id="b4053-212">Through configuration, the user may decide to log entire messages or message headers only, whether to log at the transport and/or service model layers, and whether to include malformed messages.</span></span> <span data-ttu-id="b4053-213">另外，用户可以配置筛选来限制要记录的消息范围。</span><span class="sxs-lookup"><span data-stu-id="b4053-213">Also, the user may configure filtering to restrict which messages are logged.</span></span>  
  
 <span data-ttu-id="b4053-214">默认情况下，消息日志记录被禁用。</span><span class="sxs-lookup"><span data-stu-id="b4053-214">By default, message logging is disabled.</span></span> <span data-ttu-id="b4053-215">本地计算机管理员可以阻止应用程序级管理员启用消息日志记录。</span><span class="sxs-lookup"><span data-stu-id="b4053-215">The local machine administrator can prevent the application-level administrator from turning message logging on.</span></span>  
  
#### <a name="encrypted-and-decrypted-message-logging"></a><span data-ttu-id="b4053-216">加密和解密消息日志记录</span><span class="sxs-lookup"><span data-stu-id="b4053-216">Encrypted and Decrypted Message Logging</span></span>  

 <span data-ttu-id="b4053-217">消息按下列术语所描述的方式进行记录、加密或解密。</span><span class="sxs-lookup"><span data-stu-id="b4053-217">Messages are logged, encrypted, or decrypted, as described in the following terms.</span></span>  
  
 <span data-ttu-id="b4053-218">传输日志记录</span><span class="sxs-lookup"><span data-stu-id="b4053-218">Transport Logging</span></span>  
 <span data-ttu-id="b4053-219">记录在传输级接收和发送的消息。</span><span class="sxs-lookup"><span data-stu-id="b4053-219">Logs messages received and sent at the transport level.</span></span> <span data-ttu-id="b4053-220">这些消息包含所有标头，并且在网络上发送之前以及在接收时可能进行加密。</span><span class="sxs-lookup"><span data-stu-id="b4053-220">These messages contain all headers, and may be encrypted before being sent on the wire and when being received.</span></span>  
  
 <span data-ttu-id="b4053-221">如果消息在网络上发送之前以及在接收时进行加密，那么还会记录加密后的消息。</span><span class="sxs-lookup"><span data-stu-id="b4053-221">If messages are encrypted before being sent on the wire and when they are received, they are logged encrypted as well.</span></span> <span data-ttu-id="b4053-222">一个例外的情况是使用安全协议 (https)：尽管消息在网络上进行了加密，但是在发送之前以及接收之后会记录解密的消息。</span><span class="sxs-lookup"><span data-stu-id="b4053-222">An exception is when a security protocol is used (https): they are then logged decrypted before being sent and after being received even if they are encrypted on the wire.</span></span>  
  
 <span data-ttu-id="b4053-223">服务日志记录</span><span class="sxs-lookup"><span data-stu-id="b4053-223">Service Logging</span></span>  
 <span data-ttu-id="b4053-224">在通道标头处理已经发生后，刚好在进入用户代码之前和之后记录在服务模型层接收或发送的消息。</span><span class="sxs-lookup"><span data-stu-id="b4053-224">Logs messages received or sent at the service model level, after channel header processing has occurred, just before and after entering user code.</span></span>  
  
 <span data-ttu-id="b4053-225">即使消息在网络上进行了保护和加密，在此层记录的消息也是解密消息。</span><span class="sxs-lookup"><span data-stu-id="b4053-225">Messages logged at this level are decrypted even if they were secured and encrypted on the wire.</span></span>  
  
 <span data-ttu-id="b4053-226">格式不正确的消息日志记录</span><span class="sxs-lookup"><span data-stu-id="b4053-226">Malformed Message Logging</span></span>  
 <span data-ttu-id="b4053-227">记录 WCF 基础结构无法理解或处理的消息。</span><span class="sxs-lookup"><span data-stu-id="b4053-227">Logs messages that the WCF infrastructure cannot understand or process.</span></span>  
  
 <span data-ttu-id="b4053-228">消息按原样（即，加密或不加密）进行记录。</span><span class="sxs-lookup"><span data-stu-id="b4053-228">Messages are logged as-is, that is, encrypted or not</span></span>  
  
 <span data-ttu-id="b4053-229">如果以解密或未加密形式记录消息，则默认情况下，WCF 将在记录消息之前从消息中删除安全密钥和潜在的个人信息。</span><span class="sxs-lookup"><span data-stu-id="b4053-229">When messages are logged in decrypted or unencrypted form, by default WCF removes security keys and potentially personal information from the messages before logging them.</span></span> <span data-ttu-id="b4053-230">下面几节将描述要删除的消息以及删除时间。</span><span class="sxs-lookup"><span data-stu-id="b4053-230">The next sections describe what information is removed, and when.</span></span> <span data-ttu-id="b4053-231">计算机管理员和应用程序部署人员都必须执行一定的配置操作来更改默认行为，以便记录密钥和潜在的个人信息。</span><span class="sxs-lookup"><span data-stu-id="b4053-231">The machine administrator and application deployer must both take certain configuration actions to change the default behavior to log keys and potentially personal information.</span></span>  
  
#### <a name="information-removed-from-message-headers-when-logging-decryptedunencrypted-messages"></a><span data-ttu-id="b4053-232">在记录解密/未加密消息时从消息头中删除的信息</span><span class="sxs-lookup"><span data-stu-id="b4053-232">Information Removed from Message Headers When Logging Decrypted/Unencrypted Messages</span></span>  

 <span data-ttu-id="b4053-233">在以解密/未加密形式记录消息时，默认情况下，将在记录消息之前从消息头和消息正文中删除安全密钥和潜在的个人信息。</span><span class="sxs-lookup"><span data-stu-id="b4053-233">When messages are logged in decrypted/unencrypted form, security keys and potentially personal information are removed by default from message headers and message bodies before they are logged.</span></span> <span data-ttu-id="b4053-234">下面的列表显示 WCF 如何考虑密钥和潜在的个人信息。</span><span class="sxs-lookup"><span data-stu-id="b4053-234">The following list shows what WCF considers keys and potentially personal information.</span></span>  
  
 <span data-ttu-id="b4053-235">被删除的密钥：</span><span class="sxs-lookup"><span data-stu-id="b4053-235">Keys that are removed:</span></span>  
  
 <span data-ttu-id="b4053-236">\- 对于 xmlns： wst = " http://schemas.xmlsoap.org/ws/2004/04/trust " 和 xmlns： wst = " http://schemas.xmlsoap.org/ws/2005/02/trust "</span><span class="sxs-lookup"><span data-stu-id="b4053-236">\- For xmlns:wst="http://schemas.xmlsoap.org/ws/2004/04/trust" and xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust"</span></span>  
  
 <span data-ttu-id="b4053-237">wst:BinarySecret</span><span class="sxs-lookup"><span data-stu-id="b4053-237">wst:BinarySecret</span></span>  
  
 <span data-ttu-id="b4053-238">wst:Entropy</span><span class="sxs-lookup"><span data-stu-id="b4053-238">wst:Entropy</span></span>  
  
 <span data-ttu-id="b4053-239">\- 对于 xmlns： wsse = " http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd " 和 xmlns： wsse = " http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd "</span><span class="sxs-lookup"><span data-stu-id="b4053-239">\- For xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" and xmlns:wsse="http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span></span>  
  
 <span data-ttu-id="b4053-240">wsse:Password</span><span class="sxs-lookup"><span data-stu-id="b4053-240">wsse:Password</span></span>  
  
 <span data-ttu-id="b4053-241">wsse:Nonce</span><span class="sxs-lookup"><span data-stu-id="b4053-241">wsse:Nonce</span></span>  
  
 <span data-ttu-id="b4053-242">被删除的潜在个人信息：</span><span class="sxs-lookup"><span data-stu-id="b4053-242">Potentially personal information that is removed:</span></span>  
  
 <span data-ttu-id="b4053-243">\- 对于 xmlns： wsse = " http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd " 和 xmlns： wsse = " http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd "</span><span class="sxs-lookup"><span data-stu-id="b4053-243">\- For xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" and xmlns:wsse="http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span></span>  
  
 <span data-ttu-id="b4053-244">wsse:Username</span><span class="sxs-lookup"><span data-stu-id="b4053-244">wsse:Username</span></span>  
  
 <span data-ttu-id="b4053-245">wsse:BinarySecurityToken</span><span class="sxs-lookup"><span data-stu-id="b4053-245">wsse:BinarySecurityToken</span></span>  
  
 <span data-ttu-id="b4053-246">\- 对于 xmlns： saml = "urn： oasis： names： tc： SAML：1.0： assertion"，以下)  (中的项将被删除：</span><span class="sxs-lookup"><span data-stu-id="b4053-246">\- For xmlns:saml="urn:oasis:names:tc:SAML:1.0:assertion" the items in bold (below) are removed:</span></span>  
  
 <span data-ttu-id="b4053-247">\<断言</span><span class="sxs-lookup"><span data-stu-id="b4053-247">\<Assertion</span></span>  
  
 <span data-ttu-id="b4053-248">MajorVersion="1"</span><span class="sxs-lookup"><span data-stu-id="b4053-248">MajorVersion="1"</span></span>  
  
 <span data-ttu-id="b4053-249">MinorVersion="1"</span><span class="sxs-lookup"><span data-stu-id="b4053-249">MinorVersion="1"</span></span>  
  
 <span data-ttu-id="b4053-250">AssertionId="[ID]"</span><span class="sxs-lookup"><span data-stu-id="b4053-250">AssertionId="[ID]"</span></span>  
  
 <span data-ttu-id="b4053-251">Issuer="[string]"</span><span class="sxs-lookup"><span data-stu-id="b4053-251">Issuer="[string]"</span></span>  
  
 <span data-ttu-id="b4053-252">IssueInstant="[dateTime]"</span><span class="sxs-lookup"><span data-stu-id="b4053-252">IssueInstant="[dateTime]"</span></span>  
  
 >  
  
 \<Conditions NotBefore="[dateTime]" NotOnOrAfter="[dateTime]">  
  
 \<AudienceRestrictionCondition>  
  
 <span data-ttu-id="b4053-253">\<Audience>oma-uri\</Audience>+</span><span class="sxs-lookup"><span data-stu-id="b4053-253">\<Audience>[uri]\</Audience>+</span></span>  
  
 \</AudienceRestrictionCondition>*  
  
 \<DoNotCacheCondition />*  
  
 <span data-ttu-id="b4053-254"><\!--抽象基类型</span><span class="sxs-lookup"><span data-stu-id="b4053-254"><\!-- abstract base type</span></span>  
  
 \<Condition />*  
  
 -->  
  
 <span data-ttu-id="b4053-255">\</Conditions>?</span><span class="sxs-lookup"><span data-stu-id="b4053-255">\</Conditions>?</span></span>  
  
 \<Advice>  
  
 <span data-ttu-id="b4053-256">\<AssertionIDReference>识别\</AssertionIDReference>\*</span><span class="sxs-lookup"><span data-stu-id="b4053-256">\<AssertionIDReference>[ID]\</AssertionIDReference>\*</span></span>  
  
 <span data-ttu-id="b4053-257">\<Assertion>断言\</Assertion>\*</span><span class="sxs-lookup"><span data-stu-id="b4053-257">\<Assertion>[assertion]\</Assertion>\*</span></span>  
  
 <span data-ttu-id="b4053-258">[any]\*</span><span class="sxs-lookup"><span data-stu-id="b4053-258">[any]\*</span></span>  
  
 <span data-ttu-id="b4053-259">\</Advice>?</span><span class="sxs-lookup"><span data-stu-id="b4053-259">\</Advice>?</span></span>  
  
 <span data-ttu-id="b4053-260"><\!--抽象基类型</span><span class="sxs-lookup"><span data-stu-id="b4053-260"><\!-- Abstract base types</span></span>  
  
 \<Statement />*  
  
 \<SubjectStatement>  
  
 \<Subject>  
  
 `<NameIdentifier`  
  
 `NameQualifier="[string]"?`  
  
 `Format="[uri]"?`  
  
 `>`  
  
 `[string]`  
  
 `</NameIdentifier>?`  
  
 \<SubjectConfirmation>  
  
 <span data-ttu-id="b4053-261">\<ConfirmationMethod>AnyUri\</ConfirmationMethod>+</span><span class="sxs-lookup"><span data-stu-id="b4053-261">\<ConfirmationMethod>[anyUri]\</ConfirmationMethod>+</span></span>  
  
 <span data-ttu-id="b4053-262">\<SubjectConfirmationData>[任何] \</SubjectConfirmationData> ？</span><span class="sxs-lookup"><span data-stu-id="b4053-262">\<SubjectConfirmationData>[any]\</SubjectConfirmationData>?</span></span>  
  
 <span data-ttu-id="b4053-263">\<ds:KeyInfo>...\</ds:KeyInfo>?</span><span class="sxs-lookup"><span data-stu-id="b4053-263">\<ds:KeyInfo>...\</ds:KeyInfo>?</span></span>  
  
 <span data-ttu-id="b4053-264">\</SubjectConfirmation>?</span><span class="sxs-lookup"><span data-stu-id="b4053-264">\</SubjectConfirmation>?</span></span>  
  
 \</Subject>  
  
 \</SubjectStatement>*  
  
 -->  
  
 <span data-ttu-id="b4053-265">\<AuthenticationStatement</span><span class="sxs-lookup"><span data-stu-id="b4053-265">\<AuthenticationStatement</span></span>  
  
 <span data-ttu-id="b4053-266">AuthenticationMethod="[uri]"</span><span class="sxs-lookup"><span data-stu-id="b4053-266">AuthenticationMethod="[uri]"</span></span>  
  
 <span data-ttu-id="b4053-267">AuthenticationInstant="[dateTime]"</span><span class="sxs-lookup"><span data-stu-id="b4053-267">AuthenticationInstant="[dateTime]"</span></span>  
  
 >  
  
 <span data-ttu-id="b4053-268">[Subject]</span><span class="sxs-lookup"><span data-stu-id="b4053-268">[Subject]</span></span>  
  
 `<SubjectLocality`  
  
 `IPAddress="[string]"?`  
  
 `DNSAddress="[string]"?`  
  
 `/>?`  
  
 <span data-ttu-id="b4053-269"><AuthorityBinding</span><span class="sxs-lookup"><span data-stu-id="b4053-269"><AuthorityBinding</span></span>  
  
 <span data-ttu-id="b4053-270">AuthorityKind="[QName]"</span><span class="sxs-lookup"><span data-stu-id="b4053-270">AuthorityKind="[QName]"</span></span>  
  
 <span data-ttu-id="b4053-271">Location="[uri]"</span><span class="sxs-lookup"><span data-stu-id="b4053-271">Location="[uri]"</span></span>  
  
 <span data-ttu-id="b4053-272">Binding="[uri]"</span><span class="sxs-lookup"><span data-stu-id="b4053-272">Binding="[uri]"</span></span>  
  
 />*  
  
 \</AuthenticationStatement>*  
  
 \<AttributeStatement>  
  
 <span data-ttu-id="b4053-273">[Subject]</span><span class="sxs-lookup"><span data-stu-id="b4053-273">[Subject]</span></span>  
  
 <span data-ttu-id="b4053-274">\<Attribute</span><span class="sxs-lookup"><span data-stu-id="b4053-274">\<Attribute</span></span>  
  
 <span data-ttu-id="b4053-275">AttributeName="[string]"</span><span class="sxs-lookup"><span data-stu-id="b4053-275">AttributeName="[string]"</span></span>  
  
 <span data-ttu-id="b4053-276">AttributeNamespace="[uri]"</span><span class="sxs-lookup"><span data-stu-id="b4053-276">AttributeNamespace="[uri]"</span></span>  
  
 >  
  
 `<AttributeValue>[any]</AttributeValue>+`  
  
 \</Attribute>+  
  
 \</AttributeStatement>*  
  
 <span data-ttu-id="b4053-277">\<AuthorizationDecisionStatement</span><span class="sxs-lookup"><span data-stu-id="b4053-277">\<AuthorizationDecisionStatement</span></span>  
  
 <span data-ttu-id="b4053-278">Resource="[uri]"</span><span class="sxs-lookup"><span data-stu-id="b4053-278">Resource="[uri]"</span></span>  
  
 <span data-ttu-id="b4053-279">决策 = "[允许&#124;拒绝&#124;不确定]"</span><span class="sxs-lookup"><span data-stu-id="b4053-279">Decision="[Permit&#124;Deny&#124;Indeterminate]"</span></span>  
  
 >  
  
 <span data-ttu-id="b4053-280">[Subject]</span><span class="sxs-lookup"><span data-stu-id="b4053-280">[Subject]</span></span>  
  
 <span data-ttu-id="b4053-281">\<Action Namespace="[uri]">类似\</Action>+</span><span class="sxs-lookup"><span data-stu-id="b4053-281">\<Action Namespace="[uri]">[string]\</Action>+</span></span>  
  
 \<Evidence>  
  
 <span data-ttu-id="b4053-282">\<AssertionIDReference>识别\</AssertionIDReference>+</span><span class="sxs-lookup"><span data-stu-id="b4053-282">\<AssertionIDReference>[ID]\</AssertionIDReference>+</span></span>  
  
 <span data-ttu-id="b4053-283">\<Assertion>断言\</Assertion>+</span><span class="sxs-lookup"><span data-stu-id="b4053-283">\<Assertion>[assertion]\</Assertion>+</span></span>  
  
 <span data-ttu-id="b4053-284">\</Evidence>?</span><span class="sxs-lookup"><span data-stu-id="b4053-284">\</Evidence>?</span></span>  
  
 \</AuthorizationDecisionStatement>*  
  
 \</Assertion>  
  
#### <a name="information-removed-from-message-bodies-when-logging-decryptedunencrypted-messages"></a><span data-ttu-id="b4053-285">在记录解密/未加密消息时从消息正文中删除的信息</span><span class="sxs-lookup"><span data-stu-id="b4053-285">Information Removed from Message Bodies When Logging Decrypted/Unencrypted Messages</span></span>  

 <span data-ttu-id="b4053-286">如前所述，WCF 从消息头中删除已记录的解密/未加密消息的密钥和已知的潜在个人信息。</span><span class="sxs-lookup"><span data-stu-id="b4053-286">As previously described, WCF removes keys and known potentially personal information from message headers for logged decrypted/unencrypted messages.</span></span> <span data-ttu-id="b4053-287">另外，WCF 将从以下列表中的正文元素和操作的消息正文中删除密钥和已知的潜在个人信息，其中描述了密钥交换中涉及的安全消息。</span><span class="sxs-lookup"><span data-stu-id="b4053-287">In addition, WCF removes keys and known potentially personal information from message bodies for the body elements and actions in the following list, which describe security messages involved in key exchange.</span></span>  
  
 <span data-ttu-id="b4053-288">对于下列命名空间：</span><span class="sxs-lookup"><span data-stu-id="b4053-288">For the following namespaces:</span></span>  
  
 <span data-ttu-id="b4053-289">xmlns： wst = " http://schemas.xmlsoap.org/ws/2004/04/trust " 和 xmlns： wst = " http://schemas.xmlsoap.org/ws/2005/02/trust " (例如，如果没有可用的操作) </span><span class="sxs-lookup"><span data-stu-id="b4053-289">xmlns:wst="http://schemas.xmlsoap.org/ws/2004/04/trust" and xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust" (for example, if no action available)</span></span>  
  
 <span data-ttu-id="b4053-290">删除那些涉及密钥交换的正文元素的信息：</span><span class="sxs-lookup"><span data-stu-id="b4053-290">Information is removed for these body elements, which involve key exchange:</span></span>  
  
 <span data-ttu-id="b4053-291">wst:RequestSecurityToken</span><span class="sxs-lookup"><span data-stu-id="b4053-291">wst:RequestSecurityToken</span></span>  
  
 <span data-ttu-id="b4053-292">wst:RequestSecurityTokenResponse</span><span class="sxs-lookup"><span data-stu-id="b4053-292">wst:RequestSecurityTokenResponse</span></span>  
  
 <span data-ttu-id="b4053-293">wst:RequestSecurityTokenResponseCollection</span><span class="sxs-lookup"><span data-stu-id="b4053-293">wst:RequestSecurityTokenResponseCollection</span></span>  
  
 <span data-ttu-id="b4053-294">还要删除下列每个操作的信息：</span><span class="sxs-lookup"><span data-stu-id="b4053-294">Information is also removed for each of the following Actions:</span></span>  
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Validate`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Validate`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Amend`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Amend`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RST/SCT`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RSTR/SCT`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RST/SCT-Amend`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RSTR/SCT-Amend`
  
#### <a name="no-information-is-removed-from-application-specific-headers-and-body-data"></a><span data-ttu-id="b4053-295">不会从特定于应用程序的标头和正文数据中删除任何信息</span><span class="sxs-lookup"><span data-stu-id="b4053-295">No Information Is Removed from Application-specific Headers and Body Data</span></span>  

 <span data-ttu-id="b4053-296">WCF 不跟踪特定于应用程序的标头中的个人信息 (例如，查询字符串) 或正文数据 (例如，信用卡号码) 。</span><span class="sxs-lookup"><span data-stu-id="b4053-296">WCF does not track personal information in application-specific headers (for example, query strings) or body data (for example, credit card number).</span></span>  
  
 <span data-ttu-id="b4053-297">启用消息日志记录后，特定于应用程序的标头中的个人信息和正文信息在日志中可见。</span><span class="sxs-lookup"><span data-stu-id="b4053-297">When message logging is on, personal information in application-specific headers and body information may be visible in the logs.</span></span> <span data-ttu-id="b4053-298">同样，应用程序部署人员负责设置配置和日志文件上的 ACL。</span><span class="sxs-lookup"><span data-stu-id="b4053-298">Again, the application deployer is responsible for setting the ACLs on the configuration and log files.</span></span> <span data-ttu-id="b4053-299">如果不希望此信息可见，还可以关闭日志记录，或者在记录日志文件后从日志文件中筛选出此信息。</span><span class="sxs-lookup"><span data-stu-id="b4053-299">They also can turn off logging if they don't want this information to be visible, or filter out this information from the log files after it is logged.</span></span>  
  
### <a name="service-model-tracing"></a><span data-ttu-id="b4053-300">服务模型跟踪</span><span class="sxs-lookup"><span data-stu-id="b4053-300">Service Model Tracing</span></span>  

 <span data-ttu-id="b4053-301">使用服务模型跟踪源（<xref:System.ServiceModel>）可以对与消息处理相关的活动和事件进行跟踪。</span><span class="sxs-lookup"><span data-stu-id="b4053-301">The Service Model trace source (<xref:System.ServiceModel>) enables tracing of activities and events related to message processing.</span></span> <span data-ttu-id="b4053-302">此功能使用 <xref:System.Diagnostics> 中的 .NET Framework 诊断功能。</span><span class="sxs-lookup"><span data-stu-id="b4053-302">This feature uses the .NET Framework diagnostic functionality from <xref:System.Diagnostics>.</span></span> <span data-ttu-id="b4053-303">就像 <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> 属性一样，用户可以使用 .NET Framework 应用程序配置文件对其位置和 ACL 进行配置。</span><span class="sxs-lookup"><span data-stu-id="b4053-303">As with the <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> property, the location and its ACL are user-configurable using .NET Framework application configuration files.</span></span> <span data-ttu-id="b4053-304">与消息日志记录一样，文件位置总是在管理员启用跟踪时进行配置，这样，管理员便可以控制 ACL。</span><span class="sxs-lookup"><span data-stu-id="b4053-304">As with message logging, the file location is always configured when the administrator enables tracing; thus, the administrator controls the ACL.</span></span>  
  
 <span data-ttu-id="b4053-305">当消息在范围内时，跟踪包含消息头。</span><span class="sxs-lookup"><span data-stu-id="b4053-305">Traces contain message headers when a message is in scope.</span></span> <span data-ttu-id="b4053-306">上一节中描述的有关隐藏消息头中的潜在个人信息的相同规则同样适用：默认情况下，将先前标识的个人信息从跟踪中包含的标头中删除。</span><span class="sxs-lookup"><span data-stu-id="b4053-306">The same rules for hiding potentially personal information in message headers in the previous section apply: the personal information previously identified is removed by default from the headers in traces.</span></span> <span data-ttu-id="b4053-307">计算机管理员和应用程序部署人员都必须修改配置，以便记录潜在的个人信息。</span><span class="sxs-lookup"><span data-stu-id="b4053-307">Both the machine administrator and the application deployer must modify the configuration in order to log potentially personal information.</span></span> <span data-ttu-id="b4053-308">但是，跟踪中会记录特定于应用程序的标头中包含的个人信息。</span><span class="sxs-lookup"><span data-stu-id="b4053-308">However, personal information contained in application-specific headers is logged in traces.</span></span> <span data-ttu-id="b4053-309">应用程序部署人员负责设置配置和跟踪文件上的 ACL。</span><span class="sxs-lookup"><span data-stu-id="b4053-309">The application deployer is responsible for setting the ACLs on the configuration and trace files.</span></span> <span data-ttu-id="b4053-310">它们还可以禁用跟踪来隐藏此信息，或在记录后从跟踪文件中筛选出此信息。</span><span class="sxs-lookup"><span data-stu-id="b4053-310">They can also turn off tracing to hide this information or filter out this information from the trace files after it's logged.</span></span>  
  
 <span data-ttu-id="b4053-311">作为服务模型跟踪的一部分，当消息流经基础结构的不同部分时，由唯一的 ID（称为活动 ID，通常是 GUID）将不同的活动链接到一起。</span><span class="sxs-lookup"><span data-stu-id="b4053-311">As part of ServiceModel Tracing, Unique IDs (called Activity IDs, and typically a GUID) link different activities together as a message flows through different parts of the infrastructure.</span></span>  
  
#### <a name="custom-trace-listeners"></a><span data-ttu-id="b4053-312">自定义跟踪侦听器</span><span class="sxs-lookup"><span data-stu-id="b4053-312">Custom Trace Listeners</span></span>  

 <span data-ttu-id="b4053-313">对于消息日志记录和跟踪记录，可以配置一个自定义跟踪侦听器，该侦听器可以在网络上发送跟踪和消息（例如，向远程数据库发送）。</span><span class="sxs-lookup"><span data-stu-id="b4053-313">For both message logging and tracing, a custom trace listener can be configured, which can send traces and messages on the wire (for example, to a remote database).</span></span> <span data-ttu-id="b4053-314">应用程序部署人员负责配置自定义侦听器或授权用户执行这一操作。</span><span class="sxs-lookup"><span data-stu-id="b4053-314">The application deployer is responsible for configuring custom listeners or enabling users to do so.</span></span> <span data-ttu-id="b4053-315">它们还负责在远程位置公开的任何个人信息，并将 Acl 正确地应用到此位置。</span><span class="sxs-lookup"><span data-stu-id="b4053-315">They are also responsible for any personal information exposed at the remote location and for properly applying ACLs to this location.</span></span>  
  
### <a name="other-features-for-it-professionals"></a><span data-ttu-id="b4053-316">IT 专业人员的其他作用</span><span class="sxs-lookup"><span data-stu-id="b4053-316">Other features for IT Professionals</span></span>  

 <span data-ttu-id="b4053-317">WCF 有一个 WMI 提供程序，该提供程序通过随 Windows) 提供的 WMI (公开 WCF 基础结构配置信息。</span><span class="sxs-lookup"><span data-stu-id="b4053-317">WCF has a WMI provider that exposes the WCF infrastructure configuration information through WMI (shipped with Windows).</span></span> <span data-ttu-id="b4053-318">默认情况下，WMI 接口可供管理员使用。</span><span class="sxs-lookup"><span data-stu-id="b4053-318">By default, the WMI interface is available to administrators.</span></span>  
  
 <span data-ttu-id="b4053-319">WCF 配置使用 .NET Framework 配置机制。</span><span class="sxs-lookup"><span data-stu-id="b4053-319">WCF configuration uses the .NET Framework configuration mechanism.</span></span> <span data-ttu-id="b4053-320">配置文件存储在计算机上。</span><span class="sxs-lookup"><span data-stu-id="b4053-320">The configuration files are stored on the machine.</span></span> <span data-ttu-id="b4053-321">应用程序开发人员和管理员为应用程序的每个需求创建配置文件和 ACL。</span><span class="sxs-lookup"><span data-stu-id="b4053-321">The application developer and the administrator create the configuration files and ACL for each of the application's requirements.</span></span> <span data-ttu-id="b4053-322">配置文件可以包含终结点地址和指向证书存储区中的证书的链接。</span><span class="sxs-lookup"><span data-stu-id="b4053-322">A configuration file can contain endpoint addresses and links to certificates in the certificate store.</span></span> <span data-ttu-id="b4053-323">证书可用于提供应用程序数据，以配置应用程序所使用的功能的各种属性。</span><span class="sxs-lookup"><span data-stu-id="b4053-323">The certificates can be used to provide application data to configure various properties of the features used by the application.</span></span>  
  
 <span data-ttu-id="b4053-324">WCF 还通过调用方法使用 .NET Framework 进程转储功能 <xref:System.Environment.FailFast%2A> 。</span><span class="sxs-lookup"><span data-stu-id="b4053-324">WCF also uses the .NET Framework process dump functionality by calling the <xref:System.Environment.FailFast%2A> method.</span></span>  
  
### <a name="it-pro-tools"></a><span data-ttu-id="b4053-325">IT 专业工具</span><span class="sxs-lookup"><span data-stu-id="b4053-325">IT Pro Tools</span></span>  

 <span data-ttu-id="b4053-326">WCF 还提供了以下 Windows SDK 附带的 IT 专业工具。</span><span class="sxs-lookup"><span data-stu-id="b4053-326">WCF also provides the following IT professional tools, which ship in the Windows SDK.</span></span>  
  
#### <a name="svctraceviewerexe"></a><span data-ttu-id="b4053-327">SvcTraceViewer.exe</span><span class="sxs-lookup"><span data-stu-id="b4053-327">SvcTraceViewer.exe</span></span>  

 <span data-ttu-id="b4053-328">查看器将显示 WCF 跟踪文件。</span><span class="sxs-lookup"><span data-stu-id="b4053-328">The viewer displays WCF trace files.</span></span> <span data-ttu-id="b4053-329">该查看器显示跟踪中包含的所有信息。</span><span class="sxs-lookup"><span data-stu-id="b4053-329">The viewer shows whatever information is contained in the traces.</span></span>  
  
#### <a name="svcconfigeditorexe"></a><span data-ttu-id="b4053-330">SvcConfigEditor.exe</span><span class="sxs-lookup"><span data-stu-id="b4053-330">SvcConfigEditor.exe</span></span>  

 <span data-ttu-id="b4053-331">编辑器允许用户创建和编辑 WCF 配置文件。</span><span class="sxs-lookup"><span data-stu-id="b4053-331">The editor allows the user to create and edit WCF configuration files.</span></span> <span data-ttu-id="b4053-332">该编辑器显示配置文件中包含的所有信息。</span><span class="sxs-lookup"><span data-stu-id="b4053-332">The editor shows whatever information is contained in the configuration files.</span></span> <span data-ttu-id="b4053-333">使用文本编辑器可以完成同样的任务。</span><span class="sxs-lookup"><span data-stu-id="b4053-333">The same task can be accomplished with a text editor.</span></span>  
  
#### <a name="servicemodel_reg"></a><span data-ttu-id="b4053-334">ServiceModel_Reg</span><span class="sxs-lookup"><span data-stu-id="b4053-334">ServiceModel_Reg</span></span>  

 <span data-ttu-id="b4053-335">此工具使用户可以管理计算机上的 ServiceModel 安装。</span><span class="sxs-lookup"><span data-stu-id="b4053-335">This tool allows the user to manage ServiceModel installs on a machine.</span></span> <span data-ttu-id="b4053-336">该工具在运行时在控制台窗口中显示状态消息，在此过程中，可能会显示有关 WCF 安装的配置的信息。</span><span class="sxs-lookup"><span data-stu-id="b4053-336">The tool displays status messages in a console window when it runs and, in the process, may display information about the configuration of the WCF installation.</span></span>  
  
#### <a name="wsatconfigexe-and-wsatuidll"></a><span data-ttu-id="b4053-337">WSATConfig.exe 和 WSATUI.dll</span><span class="sxs-lookup"><span data-stu-id="b4053-337">WSATConfig.exe and WSATUI.dll</span></span>  

 <span data-ttu-id="b4053-338">这些工具使 IT 专业人员能够在 WCF 中配置互操作 WS-AtomicTransaction 网络支持。</span><span class="sxs-lookup"><span data-stu-id="b4053-338">These tools allow IT Professionals to configure interoperable WS-AtomicTransaction network support in WCF.</span></span> <span data-ttu-id="b4053-339">这两种工具显示并使用户可以更改存储在注册表中的最常用 WS-AtomicTransaction 设置的值。</span><span class="sxs-lookup"><span data-stu-id="b4053-339">The tools display and allow the user to change the values of the most commonly used WS-AtomicTransaction settings stored in the registry.</span></span>  
  
## <a name="cross-cutting-features"></a><span data-ttu-id="b4053-340">横切功能</span><span class="sxs-lookup"><span data-stu-id="b4053-340">Cross-cutting Features</span></span>  

 <span data-ttu-id="b4053-341">下列功能是横切功能。</span><span class="sxs-lookup"><span data-stu-id="b4053-341">The following features are cross-cutting.</span></span> <span data-ttu-id="b4053-342">即，它们可以用前面的任何功能构成。</span><span class="sxs-lookup"><span data-stu-id="b4053-342">That is, they can be composed with any of the preceding features.</span></span>  
  
### <a name="service-framework"></a><span data-ttu-id="b4053-343">服务框架</span><span class="sxs-lookup"><span data-stu-id="b4053-343">Service Framework</span></span>  

 <span data-ttu-id="b4053-344">标头可以包含一个实例 ID，该 ID 是一个将消息与 CLR 类的一个实例相关联的 GUID。</span><span class="sxs-lookup"><span data-stu-id="b4053-344">Headers can contain an instance ID, which is a GUID that associates a message with an instance of a CLR class.</span></span>  
  
 <span data-ttu-id="b4053-345">Web 服务描述语言 (WSDL) 包含端口的定义。</span><span class="sxs-lookup"><span data-stu-id="b4053-345">The Web Services Description Language (WSDL) contains a definition of the port.</span></span> <span data-ttu-id="b4053-346">每个端口都具有一个终结点地址和一个表示应用程序所使用的服务的绑定。</span><span class="sxs-lookup"><span data-stu-id="b4053-346">Each port has an endpoint address and a binding that represents the services used by the application.</span></span> <span data-ttu-id="b4053-347">可以使用配置禁用公开 WSDL。</span><span class="sxs-lookup"><span data-stu-id="b4053-347">Exposing WSDL can be turned off using configuration.</span></span> <span data-ttu-id="b4053-348">计算机上不会保留任何信息。</span><span class="sxs-lookup"><span data-stu-id="b4053-348">No information is retained on the machine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4053-349">请参阅</span><span class="sxs-lookup"><span data-stu-id="b4053-349">See also</span></span>

- [<span data-ttu-id="b4053-350">Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="b4053-350">Windows Communication Foundation</span></span>](index.md)
- [<span data-ttu-id="b4053-351">安全性</span><span class="sxs-lookup"><span data-stu-id="b4053-351">Security</span></span>](./feature-details/security.md)
