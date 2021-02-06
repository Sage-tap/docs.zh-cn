---
description: 了解详细信息：保护对等通道应用程序
title: 保护对等通道应用程序
ms.date: 03/30/2017
ms.assetid: d4a0311d-3f78-4525-9c4b-5c93c4492f28
ms.openlocfilehash: cff94fe618ca25a6810d68efe8cb99b4316d95b7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99632654"
---
# <a name="securing-peer-channel-applications"></a><span data-ttu-id="7a7cd-103">保护对等通道应用程序</span><span class="sxs-lookup"><span data-stu-id="7a7cd-103">Securing Peer Channel Applications</span></span>

<span data-ttu-id="7a7cd-104">与 WinFX 下的其他绑定一样， `NetPeerTcpBinding` 默认情况下已启用安全性，并提供基于传输和消息的安全 (或两者) 。</span><span class="sxs-lookup"><span data-stu-id="7a7cd-104">Like other bindings under the WinFX, `NetPeerTcpBinding` has security enabled by default and offers both transport- and message-based security (or both).</span></span> <span data-ttu-id="7a7cd-105">本主题讨论这两种类型的安全。</span><span class="sxs-lookup"><span data-stu-id="7a7cd-105">This topic discusses these two types of security.</span></span> <span data-ttu-id="7a7cd-106">安全类型由绑定规范中的安全模式标记指定 (<xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>`Mode`)。</span><span class="sxs-lookup"><span data-stu-id="7a7cd-106">The type of security is specified by the security mode tag in the binding specification (<xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>`Mode`).</span></span>  
  
## <a name="transport-based-security"></a><span data-ttu-id="7a7cd-107">基于传输的安全</span><span class="sxs-lookup"><span data-stu-id="7a7cd-107">Transport-Based Security</span></span>  

 <span data-ttu-id="7a7cd-108">对等通道支持两种类型的用于保护传输安全的身份验证凭据，这两种类型都要求设置关联 `ClientCredentialSettings.Peer` 上的 `ChannelFactory` 属性：</span><span class="sxs-lookup"><span data-stu-id="7a7cd-108">Peer Channel supports two types of authentication credentials for securing transport, both of which require setting out the `ClientCredentialSettings.Peer` property on the associated `ChannelFactory`:</span></span>  
  
- <span data-ttu-id="7a7cd-109">Password。</span><span class="sxs-lookup"><span data-stu-id="7a7cd-109">Password.</span></span> <span data-ttu-id="7a7cd-110">客户端使用有关一个机密密码的信息对连接进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="7a7cd-110">Clients use knowledge of a secret password to authenticate connections.</span></span> <span data-ttu-id="7a7cd-111">如果使用此凭据类型，则 `ClientCredentialSettings.Peer.MeshPassword` 必须携带一个有效的密码，另外还可以携带一个 `X509Certificate2` 实例。</span><span class="sxs-lookup"><span data-stu-id="7a7cd-111">When this credential type is used, `ClientCredentialSettings.Peer.MeshPassword` must carry a valid password and optionally an `X509Certificate2` instance.</span></span>  
  
- <span data-ttu-id="7a7cd-112">证书。</span><span class="sxs-lookup"><span data-stu-id="7a7cd-112">Certificate.</span></span> <span data-ttu-id="7a7cd-113">使用特定的应用程序身份验证。</span><span class="sxs-lookup"><span data-stu-id="7a7cd-113">Specific application authentication is used.</span></span> <span data-ttu-id="7a7cd-114">如果使用此凭据类型，则必须在 <xref:System.IdentityModel.Selectors.X509CertificateValidator> 中使用 `ClientCredentialSettings.Peer.PeerAuthentication` 的一个具体实现。</span><span class="sxs-lookup"><span data-stu-id="7a7cd-114">When this credential type is used, you must use a concrete implementation of <xref:System.IdentityModel.Selectors.X509CertificateValidator> in `ClientCredentialSettings.Peer.PeerAuthentication`.</span></span>  
  
## <a name="message-based-security"></a><span data-ttu-id="7a7cd-115">基于消息的安全</span><span class="sxs-lookup"><span data-stu-id="7a7cd-115">Message-Based Security</span></span>  

 <span data-ttu-id="7a7cd-116">使用消息安全时，应用程序可以对传出的消息进行签名，以便所有接收方都可以验证此消息是由受信任方发送的并且此消息没有被篡改。</span><span class="sxs-lookup"><span data-stu-id="7a7cd-116">Using message security, an application can sign outgoing messages so that all receiving parties can verify the message is sent by a trusted party and that the message was not tampered with.</span></span> <span data-ttu-id="7a7cd-117">目前，对等通道仅支持 X.509 凭据消息签名。</span><span class="sxs-lookup"><span data-stu-id="7a7cd-117">Currently, Peer Channel supports only X.509 credential message signing.</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="7a7cd-118">最佳方案</span><span class="sxs-lookup"><span data-stu-id="7a7cd-118">Best Practices</span></span>  
  
- <span data-ttu-id="7a7cd-119">本节讨论保护对等通道应用程序安全的最佳做法。</span><span class="sxs-lookup"><span data-stu-id="7a7cd-119">This section discusses the best practices for securing Peer Channel applications.</span></span>  
  
### <a name="enable-security-with-peer-channel-applications"></a><span data-ttu-id="7a7cd-120">为对等通道应用程序启用安全性</span><span class="sxs-lookup"><span data-stu-id="7a7cd-120">Enable Security with Peer Channel Applications</span></span>  

 <span data-ttu-id="7a7cd-121">由于对等通道协议的分布式性质，很难在未受保护的网格中实施网格成员资格审查以及确保保密性和私密性。</span><span class="sxs-lookup"><span data-stu-id="7a7cd-121">Due to the distributed nature of the Peer Channel protocols, it is hard to enforce mesh membership, confidentiality, and privacy in an unsecured mesh.</span></span> <span data-ttu-id="7a7cd-122">另外，还需要记住保护客户端和解析程序服务之间的通信安全。</span><span class="sxs-lookup"><span data-stu-id="7a7cd-122">It is also important to remember to secure communication between clients and the resolver service.</span></span> <span data-ttu-id="7a7cd-123">按照对等名称解析协议 (PNRP) 的要求，应使用安全的名称来避免欺骗和其他常见的攻击。</span><span class="sxs-lookup"><span data-stu-id="7a7cd-123">Under Peer Name Resolution Protocol (PNRP), use secure names to avoid spoofing and other common attacks.</span></span> <span data-ttu-id="7a7cd-124">通过在客户端用来联系解析程序服务的连接上启用安全（包括基于消息的安全和基于传输的安全），可以保护自定义解析程序服务的安全。</span><span class="sxs-lookup"><span data-stu-id="7a7cd-124">Secure a custom resolver service by enabling security on the connection clients use to contact the resolver service, including both message- and transport-based security.</span></span>  
  
### <a name="use-the-strongest-possible-security-model"></a><span data-ttu-id="7a7cd-125">尽可能使用最强大的安全模型</span><span class="sxs-lookup"><span data-stu-id="7a7cd-125">Use the Strongest Possible Security Model</span></span>  

 <span data-ttu-id="7a7cd-126">例如，如果需要对网格中的每个成员单独进行标识，请使用基于证书的身份验证模型。</span><span class="sxs-lookup"><span data-stu-id="7a7cd-126">For example, if each member of the mesh needs to be individually identified, use certificate-based authentication model.</span></span> <span data-ttu-id="7a7cd-127">如果不能这样做，请按照当前建议，使用基于密码的身份验证来保证网格成员的安全。</span><span class="sxs-lookup"><span data-stu-id="7a7cd-127">If that is not possible, use password-based authentication following current recommendations to keep them secure.</span></span> <span data-ttu-id="7a7cd-128">这包括只与受信任方共享密码、使用安全媒体传输密码、经常更改密码以及确保密码为强密码（长度至少为 8 个字符，其中至少包括一个大写字母和一个小写字母、一个数字和一个特殊字符）。</span><span class="sxs-lookup"><span data-stu-id="7a7cd-128">This includes sharing passwords only with trusted parties, transmitting passwords using a secure medium, changing passwords frequently, and ensuring that passwords are strong (at least eight characters long, include at least one letter from both cases, a digit, and a special character).</span></span>  
  
### <a name="never-accept-self-signed-certificates"></a><span data-ttu-id="7a7cd-129">切勿接受自签名证书</span><span class="sxs-lookup"><span data-stu-id="7a7cd-129">Never Accept Self-Signed Certificates</span></span>  

 <span data-ttu-id="7a7cd-130">切勿接受基于主题名称的证书凭据。</span><span class="sxs-lookup"><span data-stu-id="7a7cd-130">Never accept a certificate credential based on subject names.</span></span> <span data-ttu-id="7a7cd-131">请注意，任何人都可以创建证书，并且任何人都可以选择您正在验证的名称。</span><span class="sxs-lookup"><span data-stu-id="7a7cd-131">Note that anyone can create a certificate, and anyone can choose a name that you are validating.</span></span> <span data-ttu-id="7a7cd-132">若要避免发生欺骗的可能性，请基于证书颁发机构凭据（一个受信任的颁发机构或一个根证书颁发机构）验证证书。</span><span class="sxs-lookup"><span data-stu-id="7a7cd-132">To avoid the possibility of spoofing, validate certificates based on issuing authority credentials (either a trusted issuer or a root certification authority).</span></span>  
  
### <a name="use-message-authentication"></a><span data-ttu-id="7a7cd-133">使用消息身份验证</span><span class="sxs-lookup"><span data-stu-id="7a7cd-133">Use Message Authentication</span></span>  

 <span data-ttu-id="7a7cd-134">使用消息身份验证来验证消息来自受信任的源，并且消息在传输期间没有被篡改。</span><span class="sxs-lookup"><span data-stu-id="7a7cd-134">Use message authentication to verify that a message originated from a trusted source and that no one has tampered with the message during transmission.</span></span> <span data-ttu-id="7a7cd-135">如果不使用消息身份验证，则恶意客户端很容易实施欺骗或篡改网格中的消息。</span><span class="sxs-lookup"><span data-stu-id="7a7cd-135">Without message authentication, it is easy for a malicious client to spoof or tamper with messages in the mesh.</span></span>  
  
## <a name="peer-channel-code-examples"></a><span data-ttu-id="7a7cd-136">对等通道代码示例</span><span class="sxs-lookup"><span data-stu-id="7a7cd-136">Peer Channel Code Examples</span></span>  

 [<span data-ttu-id="7a7cd-137">对等通道方案</span><span class="sxs-lookup"><span data-stu-id="7a7cd-137">Peer Channel Scenarios</span></span>](peer-channel-scenarios.md)  
  
## <a name="see-also"></a><span data-ttu-id="7a7cd-138">请参阅</span><span class="sxs-lookup"><span data-stu-id="7a7cd-138">See also</span></span>

- [<span data-ttu-id="7a7cd-139">对等通道安全性</span><span class="sxs-lookup"><span data-stu-id="7a7cd-139">Peer Channel Security</span></span>](peer-channel-security.md)
- [<span data-ttu-id="7a7cd-140">生成对等通道应用程序</span><span class="sxs-lookup"><span data-stu-id="7a7cd-140">Building a Peer Channel Application</span></span>](building-a-peer-channel-application.md)
