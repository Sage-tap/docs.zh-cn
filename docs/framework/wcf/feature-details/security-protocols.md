---
description: 了解详细信息：安全协议
title: 安全协议
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], protocols
ms.assetid: 57ffcbea-807c-4e43-a41c-44b3db8ed2af
ms.openlocfilehash: 267724f852e2402054c11fbada3ef465db4b1ca2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726801"
---
# <a name="security-protocols"></a><span data-ttu-id="d2b7d-103">安全协议</span><span class="sxs-lookup"><span data-stu-id="d2b7d-103">Security Protocols</span></span>

<span data-ttu-id="d2b7d-104">Web 服务安全协议提供 Web 服务安全机制，这些机制可满足所有现有企业的消息传递安全要求。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-104">The Web Services Security Protocols provide Web services security mechanisms that cover all existing enterprise messaging security requirements.</span></span> <span data-ttu-id="d2b7d-105">本部分介绍 (WCF) 详细信息 (在 <xref:System.ServiceModel.Channels.SecurityBindingElement>) 中为以下 Web 服务安全协议实现的 Windows Communication Foundation。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-105">This section describes the Windows Communication Foundation (WCF) details (implemented in the <xref:System.ServiceModel.Channels.SecurityBindingElement>) for the following Web services security protocols.</span></span>  
  
|<span data-ttu-id="d2b7d-106">规范/文档</span><span class="sxs-lookup"><span data-stu-id="d2b7d-106">Specification/Document</span></span>|<span data-ttu-id="d2b7d-107">链接</span><span class="sxs-lookup"><span data-stu-id="d2b7d-107">Link</span></span>|  
|-|-|  
|<span data-ttu-id="d2b7d-108">WSS：SOAP 消息安全 1.0</span><span class="sxs-lookup"><span data-stu-id="d2b7d-108">WSS: SOAP Message Security 1.0</span></span>|<http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf>|  
|<span data-ttu-id="d2b7d-109">WSS：用户名令牌配置文件 1.0</span><span class="sxs-lookup"><span data-stu-id="d2b7d-109">WSS: Username Token Profile 1.0</span></span>|<http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf>|  
|<span data-ttu-id="d2b7d-110">WSS：X509 令牌配置文件 1.0</span><span class="sxs-lookup"><span data-stu-id="d2b7d-110">WSS: X509 Token Profile 1.0</span></span>|<http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf>|  
|<span data-ttu-id="d2b7d-111">WSS：SAML 1.1 令牌配置文件 1.0</span><span class="sxs-lookup"><span data-stu-id="d2b7d-111">WSS: SAML 1.1 Token Profile 1.0</span></span>|<http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.0.pdf>|  
|<span data-ttu-id="d2b7d-112">WSS：SOAP 消息安全 1.1</span><span class="sxs-lookup"><span data-stu-id="d2b7d-112">WSS: SOAP Message Security 1.1</span></span>|<http://www.oasis-open.org/committees/download.php/16790/wss-v1.1-spec-os-SOAPMessageSecurity.pdf>|  
|<span data-ttu-id="d2b7d-113">WSS 用户名令牌配置文件 1.1</span><span class="sxs-lookup"><span data-stu-id="d2b7d-113">WSS Username Token Profile 1.1</span></span>|<http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf>|  
|<span data-ttu-id="d2b7d-114">WSS：X.509 令牌配置文件 1.1</span><span class="sxs-lookup"><span data-stu-id="d2b7d-114">WSS: X.509 Token Profile 1.1</span></span>|<http://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf>|  
|<span data-ttu-id="d2b7d-115">WSS：Kerberos 令牌配置文件 1.1</span><span class="sxs-lookup"><span data-stu-id="d2b7d-115">WSS: Kerberos Token Profile 1.1</span></span>|<http://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf>|  
|<span data-ttu-id="d2b7d-116">WSS：SAML 1.1 令牌配置文件 1.1</span><span class="sxs-lookup"><span data-stu-id="d2b7d-116">WSS: SAML 1.1 Token Profile 1.1</span></span>|<http://www.oasis-open.org/committees/download.php/16768/wss-v1.1-spec-os-SAMLTokenProfile.pdf>|  
|<span data-ttu-id="d2b7d-117">WS-Secure Conversation 1.3</span><span class="sxs-lookup"><span data-stu-id="d2b7d-117">WS-Secure Conversation 1.3</span></span>|<http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512/ws-secureconversation-1.3-os.pdf>|  
|<span data-ttu-id="d2b7d-118">WS-Trust 1.3</span><span class="sxs-lookup"><span data-stu-id="d2b7d-118">WS-Trust 1.3</span></span>|<http://docs.oasis-open.org/ws-sx/ws-trust/200512/ws-trust-1.3-os.pdf>|  
|<span data-ttu-id="d2b7d-119">应用说明：</span><span class="sxs-lookup"><span data-stu-id="d2b7d-119">Application Note:</span></span><br /><br /> <span data-ttu-id="d2b7d-120">将 WS-Trust 用于 TLS 握手</span><span class="sxs-lookup"><span data-stu-id="d2b7d-120">Using WS-Trust for TLS Handshake</span></span>|<span data-ttu-id="d2b7d-121">即将发布</span><span class="sxs-lookup"><span data-stu-id="d2b7d-121">To be published</span></span>|  
|<span data-ttu-id="d2b7d-122">应用说明：</span><span class="sxs-lookup"><span data-stu-id="d2b7d-122">Application Note:</span></span><br /><br /> <span data-ttu-id="d2b7d-123">将 WS-Trust 用于 SPNEGO</span><span class="sxs-lookup"><span data-stu-id="d2b7d-123">Using WS-Trust for SPNEGO</span></span>|<span data-ttu-id="d2b7d-124">即将发布</span><span class="sxs-lookup"><span data-stu-id="d2b7d-124">To be published</span></span>|  
|<span data-ttu-id="d2b7d-125">应用说明：</span><span class="sxs-lookup"><span data-stu-id="d2b7d-125">Application Note:</span></span><br /><br /> <span data-ttu-id="d2b7d-126">Web 服务寻址终结点引用和标识</span><span class="sxs-lookup"><span data-stu-id="d2b7d-126">Web Services Addressing Endpoint References And Identity</span></span>|<span data-ttu-id="d2b7d-127">即将发布</span><span class="sxs-lookup"><span data-stu-id="d2b7d-127">To be published</span></span>|  
|<span data-ttu-id="d2b7d-128">WS-SecurityPolicy 1.2 (2007/04)</span><span class="sxs-lookup"><span data-stu-id="d2b7d-128">WS-SecurityPolicy 1.2 (2007/04)</span></span>|<http://www.oasis-open.org/committees/download.php/23821/ws-securitypolicy-1.2-spec-cs.pdf>|  
  
 <span data-ttu-id="d2b7d-129">WCF，版本1提供17个身份验证模式，可用作 Web 服务安全配置的基础。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-129">WCF, version 1, provides 17 authentication modes that can be used as the basis for Web services security configuration.</span></span> <span data-ttu-id="d2b7d-130">每一种模式都针对一组常用部署需求进行了优化，如：</span><span class="sxs-lookup"><span data-stu-id="d2b7d-130">Each mode is optimized for a common set of deployment requirements, such as:</span></span>  
  
- <span data-ttu-id="d2b7d-131">用于对客户端和服务进行身份验证的凭据。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-131">Credentials used to authenticate client and service.</span></span>  
  
- <span data-ttu-id="d2b7d-132">消息或传输安全保护机制。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-132">Message or transport security protection mechanisms.</span></span>  
  
- <span data-ttu-id="d2b7d-133">消息交换模式。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-133">Message exchange patterns.</span></span>  
  
|<span data-ttu-id="d2b7d-134">身份验证模式</span><span class="sxs-lookup"><span data-stu-id="d2b7d-134">Authentication Mode</span></span>|<span data-ttu-id="d2b7d-135">客户端身份验证</span><span class="sxs-lookup"><span data-stu-id="d2b7d-135">Client Authentication</span></span>|<span data-ttu-id="d2b7d-136">服务器身份验证</span><span class="sxs-lookup"><span data-stu-id="d2b7d-136">Server Authentication</span></span>|<span data-ttu-id="d2b7d-137">模型</span><span class="sxs-lookup"><span data-stu-id="d2b7d-137">Mode</span></span>|  
|-------------------------|---------------------------|---------------------------|----------|  
|<span data-ttu-id="d2b7d-138">UserNameOverTransport</span><span class="sxs-lookup"><span data-stu-id="d2b7d-138">UserNameOverTransport</span></span>|<span data-ttu-id="d2b7d-139">用户名/密码</span><span class="sxs-lookup"><span data-stu-id="d2b7d-139">User name/password</span></span>|<span data-ttu-id="d2b7d-140">X509</span><span class="sxs-lookup"><span data-stu-id="d2b7d-140">X509</span></span>|<span data-ttu-id="d2b7d-141">Transport</span><span class="sxs-lookup"><span data-stu-id="d2b7d-141">Transport</span></span>|  
|<span data-ttu-id="d2b7d-142">CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="d2b7d-142">CertificateOverTransport</span></span>|<span data-ttu-id="d2b7d-143">X509</span><span class="sxs-lookup"><span data-stu-id="d2b7d-143">X509</span></span>|<span data-ttu-id="d2b7d-144">X509</span><span class="sxs-lookup"><span data-stu-id="d2b7d-144">X509</span></span>|<span data-ttu-id="d2b7d-145">Transport</span><span class="sxs-lookup"><span data-stu-id="d2b7d-145">Transport</span></span>|  
|<span data-ttu-id="d2b7d-146">KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="d2b7d-146">KerberosOverTransport</span></span>|<span data-ttu-id="d2b7d-147">Windows</span><span class="sxs-lookup"><span data-stu-id="d2b7d-147">Windows</span></span>|<span data-ttu-id="d2b7d-148">X509</span><span class="sxs-lookup"><span data-stu-id="d2b7d-148">X509</span></span>|<span data-ttu-id="d2b7d-149">Transport</span><span class="sxs-lookup"><span data-stu-id="d2b7d-149">Transport</span></span>|  
|<span data-ttu-id="d2b7d-150">IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="d2b7d-150">IssuedTokenOverTransport</span></span>|<span data-ttu-id="d2b7d-151">联合</span><span class="sxs-lookup"><span data-stu-id="d2b7d-151">Federated</span></span>|<span data-ttu-id="d2b7d-152">X509</span><span class="sxs-lookup"><span data-stu-id="d2b7d-152">X509</span></span>|<span data-ttu-id="d2b7d-153">Transport</span><span class="sxs-lookup"><span data-stu-id="d2b7d-153">Transport</span></span>|  
|<span data-ttu-id="d2b7d-154">SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="d2b7d-154">SspiNegotiatedOverTransport</span></span>|<span data-ttu-id="d2b7d-155">协商的 Windows Sspi</span><span class="sxs-lookup"><span data-stu-id="d2b7d-155">Windows Sspi Negotiated</span></span>|<span data-ttu-id="d2b7d-156">协商的 Windows Sspi</span><span class="sxs-lookup"><span data-stu-id="d2b7d-156">Windows Sspi Negotiated</span></span>|<span data-ttu-id="d2b7d-157">Transport</span><span class="sxs-lookup"><span data-stu-id="d2b7d-157">Transport</span></span>|  
|<span data-ttu-id="d2b7d-158">AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="d2b7d-158">AnonymousForCertificate</span></span>|<span data-ttu-id="d2b7d-159">无</span><span class="sxs-lookup"><span data-stu-id="d2b7d-159">None</span></span>|<span data-ttu-id="d2b7d-160">X509</span><span class="sxs-lookup"><span data-stu-id="d2b7d-160">X509</span></span>|<span data-ttu-id="d2b7d-161">消息</span><span class="sxs-lookup"><span data-stu-id="d2b7d-161">Message</span></span>|  
|<span data-ttu-id="d2b7d-162">UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="d2b7d-162">UserNameForCertificate</span></span>|<span data-ttu-id="d2b7d-163">用户名/密码</span><span class="sxs-lookup"><span data-stu-id="d2b7d-163">User name/password</span></span>|<span data-ttu-id="d2b7d-164">X509</span><span class="sxs-lookup"><span data-stu-id="d2b7d-164">X509</span></span>|<span data-ttu-id="d2b7d-165">消息</span><span class="sxs-lookup"><span data-stu-id="d2b7d-165">Message</span></span>|  
|<span data-ttu-id="d2b7d-166">MutualCertificate</span><span class="sxs-lookup"><span data-stu-id="d2b7d-166">MutualCertificate</span></span>|<span data-ttu-id="d2b7d-167">X509</span><span class="sxs-lookup"><span data-stu-id="d2b7d-167">X509</span></span>|<span data-ttu-id="d2b7d-168">X509</span><span class="sxs-lookup"><span data-stu-id="d2b7d-168">X509</span></span>|<span data-ttu-id="d2b7d-169">消息</span><span class="sxs-lookup"><span data-stu-id="d2b7d-169">Message</span></span>|  
|<span data-ttu-id="d2b7d-170">MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="d2b7d-170">MutualCertificateDuplex</span></span>|<span data-ttu-id="d2b7d-171">X509</span><span class="sxs-lookup"><span data-stu-id="d2b7d-171">X509</span></span>|<span data-ttu-id="d2b7d-172">X509</span><span class="sxs-lookup"><span data-stu-id="d2b7d-172">X509</span></span>|<span data-ttu-id="d2b7d-173">消息</span><span class="sxs-lookup"><span data-stu-id="d2b7d-173">Message</span></span>|  
|<span data-ttu-id="d2b7d-174">IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="d2b7d-174">IssuedTokenForCertificate</span></span>|<span data-ttu-id="d2b7d-175">联合</span><span class="sxs-lookup"><span data-stu-id="d2b7d-175">Federated</span></span>|<span data-ttu-id="d2b7d-176">X509</span><span class="sxs-lookup"><span data-stu-id="d2b7d-176">X509</span></span>|<span data-ttu-id="d2b7d-177">消息</span><span class="sxs-lookup"><span data-stu-id="d2b7d-177">Message</span></span>|  
|<span data-ttu-id="d2b7d-178">Kerberos</span><span class="sxs-lookup"><span data-stu-id="d2b7d-178">Kerberos</span></span>|<span data-ttu-id="d2b7d-179">Windows</span><span class="sxs-lookup"><span data-stu-id="d2b7d-179">Windows</span></span>|<span data-ttu-id="d2b7d-180">Windows</span><span class="sxs-lookup"><span data-stu-id="d2b7d-180">Windows</span></span>|<span data-ttu-id="d2b7d-181">消息</span><span class="sxs-lookup"><span data-stu-id="d2b7d-181">Message</span></span>|  
|<span data-ttu-id="d2b7d-182">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="d2b7d-182">IssuedToken</span></span>|<span data-ttu-id="d2b7d-183">联合</span><span class="sxs-lookup"><span data-stu-id="d2b7d-183">Federated</span></span>|<span data-ttu-id="d2b7d-184">联合</span><span class="sxs-lookup"><span data-stu-id="d2b7d-184">Federated</span></span>|<span data-ttu-id="d2b7d-185">消息</span><span class="sxs-lookup"><span data-stu-id="d2b7d-185">Message</span></span>|  
|<span data-ttu-id="d2b7d-186">SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="d2b7d-186">SspiNegotiated</span></span>|<span data-ttu-id="d2b7d-187">协商的 Windows Sspi</span><span class="sxs-lookup"><span data-stu-id="d2b7d-187">Windows Sspi Negotiated</span></span>|<span data-ttu-id="d2b7d-188">协商的 Windows Sspi</span><span class="sxs-lookup"><span data-stu-id="d2b7d-188">Windows Sspi Negotiated</span></span>|<span data-ttu-id="d2b7d-189">消息</span><span class="sxs-lookup"><span data-stu-id="d2b7d-189">Message</span></span>|  
|<span data-ttu-id="d2b7d-190">AnonymousForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="d2b7d-190">AnonymousForSslNegotiated</span></span>|<span data-ttu-id="d2b7d-191">无</span><span class="sxs-lookup"><span data-stu-id="d2b7d-191">None</span></span>|<span data-ttu-id="d2b7d-192">X509、TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="d2b7d-192">X509, TLS-Nego</span></span>|<span data-ttu-id="d2b7d-193">消息</span><span class="sxs-lookup"><span data-stu-id="d2b7d-193">Message</span></span>|  
|<span data-ttu-id="d2b7d-194">UserNameForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="d2b7d-194">UserNameForSslNegotiated</span></span>|<span data-ttu-id="d2b7d-195">用户名/密码</span><span class="sxs-lookup"><span data-stu-id="d2b7d-195">User name/password</span></span>|<span data-ttu-id="d2b7d-196">X509、TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="d2b7d-196">X509, TLS-Nego</span></span>|<span data-ttu-id="d2b7d-197">消息</span><span class="sxs-lookup"><span data-stu-id="d2b7d-197">Message</span></span>|  
|<span data-ttu-id="d2b7d-198">MutualSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="d2b7d-198">MutualSslNegotiated</span></span>|<span data-ttu-id="d2b7d-199">X509</span><span class="sxs-lookup"><span data-stu-id="d2b7d-199">X509</span></span>|<span data-ttu-id="d2b7d-200">X509、TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="d2b7d-200">X509, TLS-Nego</span></span>|<span data-ttu-id="d2b7d-201">消息</span><span class="sxs-lookup"><span data-stu-id="d2b7d-201">Message</span></span>|  
|<span data-ttu-id="d2b7d-202">IssuedTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="d2b7d-202">IssuedTokenForSslNegotiated</span></span>|<span data-ttu-id="d2b7d-203">联合</span><span class="sxs-lookup"><span data-stu-id="d2b7d-203">Federated</span></span>|<span data-ttu-id="d2b7d-204">X509、TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="d2b7d-204">X509, TLS-Nego</span></span>|<span data-ttu-id="d2b7d-205">消息</span><span class="sxs-lookup"><span data-stu-id="d2b7d-205">Message</span></span>|  
  
 <span data-ttu-id="d2b7d-206">使用此类身份验证模式的终结点可以使用 WS-SecurityPolicy (WS-SP) 表示其安全要求。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-206">Endpoints using such authentication modes can express their security requirements using WS-SecurityPolicy (WS-SP).</span></span> <span data-ttu-id="d2b7d-207">本文档介绍每种身份验证模式的安全标头和基础结构消息的结构，并提供策略和消息的示例。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-207">This document describes the structure of security header and infrastructure messages for each authentication mode and provides examples of policies and messages.</span></span>  
  
 <span data-ttu-id="d2b7d-208">WCF 利用 WS-SecureConversation 提供安全会话支持来保护应用程序之间的多消息交换。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-208">WCF leverages WS-SecureConversation to provide secure sessions support to protect multi-message exchanges between applications.</span></span>  <span data-ttu-id="d2b7d-209">请参见下面的“安全会话”了解实现细节。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-209">See "Secure Sessions" below for implementation details.</span></span>  
  
 <span data-ttu-id="d2b7d-210">除了身份验证模式之外，WCF 还提供一些设置，用于控制适用于大多数基于消息安全的身份验证模式的常见保护机制，例如：签名和加密操作的顺序、算法套件、密钥派生和签名确认。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-210">In addition to authentication modes, WCF provides settings to control common protection mechanisms that apply to most message security-based authentication modes, for example: order of signature versus encryption operations, algorithm suites, key derivation, and signature confirmation.</span></span>  
  
 <span data-ttu-id="d2b7d-211">本文档使用以下前缀和命名空间。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-211">The following prefixes and namespaces are used in this document.</span></span>  
  
|<span data-ttu-id="d2b7d-212">前缀</span><span class="sxs-lookup"><span data-stu-id="d2b7d-212">Prefix</span></span>|<span data-ttu-id="d2b7d-213">命名空间</span><span class="sxs-lookup"><span data-stu-id="d2b7d-213">Namespace</span></span>|  
|------------|---------------|  
|<span data-ttu-id="d2b7d-214">s</span><span class="sxs-lookup"><span data-stu-id="d2b7d-214">s</span></span>|`http://www.w3.org/2003/05/soap-envelope`|  
|<span data-ttu-id="d2b7d-215">sp</span><span class="sxs-lookup"><span data-stu-id="d2b7d-215">sp</span></span>|`http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702`|  
|<span data-ttu-id="d2b7d-216">a</span><span class="sxs-lookup"><span data-stu-id="d2b7d-216">a</span></span>|`http://www.w3.org/2005/08/addressing`|  
|<span data-ttu-id="d2b7d-217">wsse</span><span class="sxs-lookup"><span data-stu-id="d2b7d-217">wsse</span></span>|<span data-ttu-id="d2b7d-218">TBD – OASIS WSS 1.0 URI</span><span class="sxs-lookup"><span data-stu-id="d2b7d-218">TBD – OASIS WSS 1.0 URI</span></span>|  
|<span data-ttu-id="d2b7d-219">wsse11</span><span class="sxs-lookup"><span data-stu-id="d2b7d-219">wsse11</span></span>|<span data-ttu-id="d2b7d-220">TBD – OASIS WSS 1.1 URI</span><span class="sxs-lookup"><span data-stu-id="d2b7d-220">TBD – OASIS WSS 1.1 URI</span></span>|  
|<span data-ttu-id="d2b7d-221">wsu</span><span class="sxs-lookup"><span data-stu-id="d2b7d-221">wsu</span></span>|`http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd`|  
|<span data-ttu-id="d2b7d-222">ds</span><span class="sxs-lookup"><span data-stu-id="d2b7d-222">ds</span></span>|<span data-ttu-id="d2b7d-223">TBD – W3C XMLDSig URI</span><span class="sxs-lookup"><span data-stu-id="d2b7d-223">TBD – W3C XMLDSig URI</span></span>|  
|<span data-ttu-id="d2b7d-224">wst</span><span class="sxs-lookup"><span data-stu-id="d2b7d-224">wst</span></span>|<span data-ttu-id="d2b7d-225">TBD – WS-Trust 2005/02 URI</span><span class="sxs-lookup"><span data-stu-id="d2b7d-225">TBD – WS-Trust 2005/02 URI</span></span>|  
|<span data-ttu-id="d2b7d-226">wssc</span><span class="sxs-lookup"><span data-stu-id="d2b7d-226">wssc</span></span>|<span data-ttu-id="d2b7d-227">TBD – WS-SecureConversation 2005/02 URI</span><span class="sxs-lookup"><span data-stu-id="d2b7d-227">TBD – WS-SecureConversation 2005/02 URI</span></span>|  
|<span data-ttu-id="d2b7d-228">wsaw</span><span class="sxs-lookup"><span data-stu-id="d2b7d-228">wsaw</span></span>|`http://www.w3.org/2006/05/addressing/wsdl`|  
|<span data-ttu-id="d2b7d-229">wsp</span><span class="sxs-lookup"><span data-stu-id="d2b7d-229">wsp</span></span>|`http://schemas.xmlsoap.org/ws/2004/09/policy`|  
|<span data-ttu-id="d2b7d-230">mssp</span><span class="sxs-lookup"><span data-stu-id="d2b7d-230">mssp</span></span>|`http://schemas.microsoft.com/ws/2005/07/securitypolicy`|  
  
## <a name="1-token-profiles"></a><span data-ttu-id="d2b7d-231">1. 令牌配置文件</span><span class="sxs-lookup"><span data-stu-id="d2b7d-231">1. Token Profiles</span></span>  

 <span data-ttu-id="d2b7d-232">Web 服务安全规范将凭据表示为安全令牌。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-232">Web Services Security specifications represent credential as security tokens.</span></span> <span data-ttu-id="d2b7d-233">WCF 支持以下令牌类型：</span><span class="sxs-lookup"><span data-stu-id="d2b7d-233">WCF supports the following token types:</span></span>  
  
### <a name="11-usernametoken"></a><span data-ttu-id="d2b7d-234">1.1 UsernameToken</span><span class="sxs-lookup"><span data-stu-id="d2b7d-234">1.1 UsernameToken</span></span>  

 <span data-ttu-id="d2b7d-235">WCF 遵循 UsernameToken10 和 UsernameToken11 配置文件，其约束如下：</span><span class="sxs-lookup"><span data-stu-id="d2b7d-235">WCF follows UsernameToken10 and UsernameToken11 profiles with the following constraints:</span></span>  
  
 <span data-ttu-id="d2b7d-236">R1101 UsernameToken\Password 元素的 PasswordType 属性必须省略或者值为 #PasswordText（默认值）。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-236">R1101 PasswordType attribute on UsernameToken\Password element MUST be either omitted or have value #PasswordText (default).</span></span>  
  
 <span data-ttu-id="d2b7d-237">可以使用可扩展性实现 #PasswordDigest。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-237">One can implement the #PasswordDigest using extensibility.</span></span> <span data-ttu-id="d2b7d-238">人们已经发现，#PasswordDigest 经常被误认为是足够安全的密码保护机制。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-238">It has been observed that #PasswordDigest was often mistaken to be a secure enough password protection mechanism.</span></span> <span data-ttu-id="d2b7d-239">但实际上，#PasswordDigest 不可取代 UsernameToken 加密。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-239">But #PasswordDigest cannot serve as a substitute for encryption of the UsernameToken.</span></span> <span data-ttu-id="d2b7d-240">#PasswordDigest 的主要目的是防止重放攻击。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-240">The primary goal of #PasswordDigest is protection against replay attacks.</span></span> <span data-ttu-id="d2b7d-241">在 WCF 身份验证模式下，通过使用消息签名缓解重播攻击威胁。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-241">In WCF authentication modes, replay attack threats are mitigated by using message signatures.</span></span>  
  
 <span data-ttu-id="d2b7d-242">B1102 WCF 从不发出 Nonce 并创建 UsernameToken 的子元素。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-242">B1102 WCF never emits Nonce and Created sub-elements of the UsernameToken.</span></span>  
  
 <span data-ttu-id="d2b7d-243">这些子元素旨在帮助重放检测。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-243">These sub-elements are intended to help replay detection.</span></span> <span data-ttu-id="d2b7d-244">WCF 使用消息签名。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-244">WCF uses message signatures instead.</span></span>  
  
 <span data-ttu-id="d2b7d-245">OASIS WSS SOAP Message Security UsernameToken Profile 1.1 (UsernameToken11) 引入了从密码派生密钥的功能。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-245">OASIS WSS SOAP Message Security UsernameToken Profile 1.1 (UsernameToken11) introduced key derivation from password feature.</span></span>  
  
 <span data-ttu-id="d2b7d-246">B1103 UsernameToken 密码不得用于密钥派生，因此也不得用于加密操作。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-246">B1103 UsernameToken password MUST not be used for key derivation and therefore for cryptographic operations.</span></span>  
  
 <span data-ttu-id="d2b7d-247">根本原因：密码通常被视为过于脆弱，不适合用于加密操作。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-247">Rationale: passwords are generally considered too weak to be used for cryptographic operations.</span></span>  
  
### <a name="12-x509-token"></a><span data-ttu-id="d2b7d-248">1.2 X509 令牌</span><span class="sxs-lookup"><span data-stu-id="d2b7d-248">1.2 X509 Token</span></span>  

 <span data-ttu-id="d2b7d-249">WCF 支持 X509v3 证书作为凭据类型，并遵循 X509tokenprofile1.1 1.0 和 X509tokenprofile1.1 1.1 的限制：</span><span class="sxs-lookup"><span data-stu-id="d2b7d-249">WCF supports X509v3 certificates as a credential type and follows X509TokenProfile1.0 and X509TokenProfile1.1 with the following constraints:</span></span>  
  
 <span data-ttu-id="d2b7d-250">R1201 在包含 X509v3 证书时，BinarySecurityToken 元素的 ValueType 属性必须值为 #X509v3。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-250">R1201 The ValueType attribute on the BinarySecurityToken element must have value #X509v3 when it contains an X509v3 certificate.</span></span>  
  
 <span data-ttu-id="d2b7d-251">WSS X509 Token Profile 1.0 和 1.1 还定义了 #X509PKIPathv1 和 #PKCS7 作为值类型。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-251">WSS X509 Token Profile 1.0 and 1.1 define also #X509PKIPathv1 and #PKCS7 as value types.</span></span> <span data-ttu-id="d2b7d-252">WCF 不支持这些类型。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-252">WCF does not support these types.</span></span>  
  
 <span data-ttu-id="d2b7d-253">R1202 如果 SubjectKeyIdentifier (SKI) 扩展在 X509 证书中存在，wsse:KeyIdentifier 应该用于对该令牌的外部引用，并且 ValueType 属性为 #X509SubjectKeyIdentifier 且其内容为证书的 SKI 扩展的 base64 编码值。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-253">R1202 If a SubjectKeyIdentifier (SKI) extension is present in an X509 certificate, wsse:KeyIdentifier should be used for external references to the token, with the ValueType attribute as #X509SubjectKeyIdentifier and its content the base64-encoded value of certificate's SKI extension.</span></span>  
  
 <span data-ttu-id="d2b7d-254">SKI 引用已广泛实现，已证明是高度可互操作的外部引用类型。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-254">SKI references are widely implemented and proven to be a highly interoperable external reference type.</span></span>  
  
 <span data-ttu-id="d2b7d-255">R1203 对 X509 安全令牌的外部引用不应使用 ds:X509IssuerSerial。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-255">R1203 An external Reference to X509 Security Token SHOULD NOT use ds:X509IssuerSerial.</span></span>  
  
 <span data-ttu-id="d2b7d-256">R1204 如果使用 X509TokenProfile1.1，则对 X509 安全令牌的外部引用应该使用 WS-Security 1.1 引入的指纹。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-256">R1204 If X509TokenProfile1.1 is in use, an external reference to X509 Security Token SHOULD use the thumbprint introduced by WS-Security 1.1.</span></span>  
  
 <span data-ttu-id="d2b7d-257">WCF 支持 X509IssuerSerial。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-257">WCF supports X509IssuerSerial.</span></span> <span data-ttu-id="d2b7d-258">但是，X509IssuerSerial 存在互操作性问题： WCF 使用字符串来比较 X509IssuerSerial 的两个值。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-258">However there are interoperability issues with X509IssuerSerial: WCF uses a string to compare two values of X509IssuerSerial.</span></span> <span data-ttu-id="d2b7d-259">因此，如果一次重命名使用者名称的组件并将其发送到 WCF 服务，则可能找不到该证书。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-259">Therefore if one reorders components of the Subject Name and sends to an WCF service a reference to a certificate, it may not be found.</span></span>  
  
### <a name="13-kerberos-token"></a><span data-ttu-id="d2b7d-260">1.3 Kerberos 令牌</span><span class="sxs-lookup"><span data-stu-id="d2b7d-260">1.3 Kerberos Token</span></span>  

 <span data-ttu-id="d2b7d-261">为了实现 Windows 身份验证，WCF 支持 KerberosTokenProfile 1.1，但具有以下限制：</span><span class="sxs-lookup"><span data-stu-id="d2b7d-261">WCF supports KerberosTokenProfile1.1 for the purpose of Windows authentication with the following constraints:</span></span>  
  
 <span data-ttu-id="d2b7d-262">R1301 Kerberos 令牌必须携带 GSS_API 和 Kerberos 规范中定义的 GSS 包装的 Kerberos v4 AP_REQ 的值，并且必须有值为 #GSS_Kerberosv5_AP_REQ 的 ValueType 属性。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-262">R1301 A Kerberos Token must carry the value of a GSS wrapped Kerberos v4 AP_REQ as defined in GSS_API and the Kerberos specification, and must have the ValueType attribute with the value #GSS_Kerberosv5_AP_REQ.</span></span>  
  
 <span data-ttu-id="d2b7d-263">WCF 使用 GSS 包装的 Kerberos AP 要求，而不是要求空的 AP 要求。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-263">WCF uses GSS wrapped Kerberos AP-REQ, not a bare AP-REQ.</span></span> <span data-ttu-id="d2b7d-264">这是一种安全最佳做法。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-264">This is a security best practice.</span></span>  
  
### <a name="14-saml-v11-token"></a><span data-ttu-id="d2b7d-265">1.4 SAML v1.1 令牌</span><span class="sxs-lookup"><span data-stu-id="d2b7d-265">1.4 SAML v1.1 Token</span></span>  

 <span data-ttu-id="d2b7d-266">对于 SAML v1.1 令牌，WCF 支持 WSS SAML 令牌配置文件1.0 和1.1。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-266">WCF supports WSS SAML Token profiles 1.0 and 1.1 for SAML v1.1 tokens.</span></span> <span data-ttu-id="d2b7d-267">可以实现其他版本的 SAML 令牌格式。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-267">It is possible to implement other versions of SAML token formats.</span></span>  
  
### <a name="15-security-context-token"></a><span data-ttu-id="d2b7d-268">1.5 安全上下文令牌</span><span class="sxs-lookup"><span data-stu-id="d2b7d-268">1.5 Security Context Token</span></span>  

 <span data-ttu-id="d2b7d-269">WCF 支持 Ws-secureconversation 中引入 (SCT) 安全上下文令牌。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-269">WCF supports the Security Context Token (SCT) introduced in WS-SecureConversation.</span></span> <span data-ttu-id="d2b7d-270">SCT 用于表示在 SecureConversation 中建立的安全上下文以及下面所述的二进制协商协议 TLS 和 SSPI。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-270">SCT is used to represent a security context established in SecureConversation as well as the binary negotiation protocols TLS and SSPI, described below.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="d2b7d-271">2. 公用消息安全参数</span><span class="sxs-lookup"><span data-stu-id="d2b7d-271">2. Common Message Security Parameters</span></span>  
  
### <a name="21-timestamp"></a><span data-ttu-id="d2b7d-272">2.1 时间戳</span><span class="sxs-lookup"><span data-stu-id="d2b7d-272">2.1 TimeStamp</span></span>  

 <span data-ttu-id="d2b7d-273">时间戳存在与否是使用 <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> 类的 <xref:System.ServiceModel.Channels.SecurityBindingElement> 属性控制的。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-273">Timestamp presence is controlled using the <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> property of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span> <span data-ttu-id="d2b7d-274">WCF 始终序列化 wsse： TimeStamp with wsse：已创建和 wsse： Expires 字段。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-274">WCF always serializes wsse:TimeStamp with wsse:Created and wsse:Expires fields.</span></span> <span data-ttu-id="d2b7d-275">使用签名时，总会对 wsse:TimeStamp 进行签名。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-275">The wsse:TimeStamp is always signed when signing is used.</span></span>  
  
### <a name="22-protection-order"></a><span data-ttu-id="d2b7d-276">2.2 保护顺序</span><span class="sxs-lookup"><span data-stu-id="d2b7d-276">2.2 Protection Order</span></span>  

 <span data-ttu-id="d2b7d-277">WCF 支持消息保护顺序 "加密前签名" 和 "签名前加密" (安全策略 1.2) 。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-277">WCF supports the message protection order "Sign Before Encrypt" and "Encrypt Before Sign" (Security Policy 1.2).</span></span> <span data-ttu-id="d2b7d-278">建议使用“加密前签名”，其原因包括：除非使用 WS-Security 1.1 SignatureConfirmation 机制，否则使用“签名前加密”进行保护的消息易受签名替换攻击，并且对加密内容进行签名使得审核更加困难。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-278">"Sign Before Encrypt" is recommended for reasons including: messages protected with Encrypt Before Sign are open to signature substitution attacks unless the WS-Security 1.1 SignatureConfirmation mechanism is used, and a signature over encrypted content makes auditing harder.</span></span>  
  
### <a name="23-signature-protection"></a><span data-ttu-id="d2b7d-279">2.3 签名保护</span><span class="sxs-lookup"><span data-stu-id="d2b7d-279">2.3 Signature Protection</span></span>  

 <span data-ttu-id="d2b7d-280">在使用“签名前加密”时，建议保护签名以防止对加密内容或签名密钥进行猜测的蛮力攻击（尤其是在自定义令牌与弱密钥材料一起使用时）。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-280">When Encrypt Before Sign is used, it is recommended to protect the signature to prevent brute force attacks for guessing the encrypted content or the signing key (especially when a custom token is used with weak key material).</span></span>  
  
### <a name="24-algorithm-suite"></a><span data-ttu-id="d2b7d-281">2.4 算法组</span><span class="sxs-lookup"><span data-stu-id="d2b7d-281">2.4 Algorithm Suite</span></span>  

 <span data-ttu-id="d2b7d-282">WCF 支持安全策略1.2 中列出的所有算法套件。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-282">WCF supports all algorithm suites listed in Security Policy 1.2.</span></span>  
  
### <a name="25-key-derivation"></a><span data-ttu-id="d2b7d-283">2.5 密钥派生</span><span class="sxs-lookup"><span data-stu-id="d2b7d-283">2.5 Key Derivation</span></span>  

 <span data-ttu-id="d2b7d-284">WCF 使用 "对称密钥的密钥派生"，如 Ws-secureconversation 中所述。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-284">WCF uses "Key Derivation for symmetric keys" as described in WS-SecureConversation.</span></span>  
  
### <a name="26-signature-confirmation"></a><span data-ttu-id="d2b7d-285">2.6 签名确认</span><span class="sxs-lookup"><span data-stu-id="d2b7d-285">2.6 Signature Confirmation</span></span>  

 <span data-ttu-id="d2b7d-286">签名确认可用于防止中间人攻击以保护签名集。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-286">Signature confirmation can be used as protection from middle man attacks to protect the set of signatures.</span></span>  
  
### <a name="27-security-header-layout"></a><span data-ttu-id="d2b7d-287">2.7 安全标头布局</span><span class="sxs-lookup"><span data-stu-id="d2b7d-287">2.7 Security Header Layout</span></span>  

 <span data-ttu-id="d2b7d-288">每种身份验证模式都描述一种特定的安全标头布局。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-288">Each authentication mode describes a certain layout for the security header.</span></span> <span data-ttu-id="d2b7d-289">安全标头内的元素为半有序。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-289">Elements within the security header are semi-ordered.</span></span> <span data-ttu-id="d2b7d-290">为了定义安全标头子元素的顺序，WS-Security Policy 定义了以下安全标头布局模式：</span><span class="sxs-lookup"><span data-stu-id="d2b7d-290">To define the order of security header child elements, WS-Security Policy defines the following security header layout modes:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d2b7d-291">严格</span><span class="sxs-lookup"><span data-stu-id="d2b7d-291">Strict</span></span>|<span data-ttu-id="d2b7d-292">根据“使用前先声明”的一般原则，各项按照 Security Policy 第 7.7.1 节中所述的编号布局规则添加到安全标头中。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-292">Items are added to the security header following the numbered layout rules described in Security Policy section 7.7.1 according to a general principle of "declare before use".</span></span>|  
|<span data-ttu-id="d2b7d-293">Lax</span><span class="sxs-lookup"><span data-stu-id="d2b7d-293">Lax</span></span>|<span data-ttu-id="d2b7d-294">各项以任何符合“WSS: SOAP 消息安全”的顺序添加到安全标头中。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-294">Items are added to the security header in any order that conforms to WSS: SOAP Message Security.</span></span>|  
|<span data-ttu-id="d2b7d-295">LaxTimestampFirst</span><span class="sxs-lookup"><span data-stu-id="d2b7d-295">LaxTimestampFirst</span></span>|<span data-ttu-id="d2b7d-296">与 Lax 相同，只是安全标头中的第一项必须为 wsse:Timestamp</span><span class="sxs-lookup"><span data-stu-id="d2b7d-296">Same as Lax except that the first item in the security header must be a wsse:Timestamp</span></span>|  
|<span data-ttu-id="d2b7d-297">LaxTimestampLast</span><span class="sxs-lookup"><span data-stu-id="d2b7d-297">LaxTimestampLast</span></span>|<span data-ttu-id="d2b7d-298">与 lax 相同，只是安全标头中的最后一项必须为 wsse:Timestamp</span><span class="sxs-lookup"><span data-stu-id="d2b7d-298">Same as lax except that the last item in the security header must be a wsse:Timestamp</span></span>|  
  
 <span data-ttu-id="d2b7d-299">WCF 支持安全标头布局的所有四种模式。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-299">WCF supports all four modes for security header layout.</span></span> <span data-ttu-id="d2b7d-300">以下针对身份验证模式的安全标头结构和消息示例遵循“Strict”模式。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-300">Security header structure and message examples for authentication modes below follow the "Strict" mode.</span></span>  
  
## <a name="3-common-message-security-parameters"></a><span data-ttu-id="d2b7d-301">3. 常见消息安全参数</span><span class="sxs-lookup"><span data-stu-id="d2b7d-301">3. Common Message Security Parameters</span></span>  

 <span data-ttu-id="d2b7d-302">本节介绍每种身份验证模式的示例策略以及演示客户端和服务所交换的消息中的安全标头结构的示例。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-302">This section provides example policies for each authentication mode along with examples showing security header structure in messages exchanged by client and service.</span></span>  
  
### <a name="31-transport-protection"></a><span data-ttu-id="d2b7d-303">3.1 传输保护</span><span class="sxs-lookup"><span data-stu-id="d2b7d-303">3.1 Transport Protection</span></span>  

 <span data-ttu-id="d2b7d-304">WCF 提供五种使用安全传输来保护消息的身份验证模式。UserNameOverTransport、CertificateOverTransport、KerberosOverTransport、IssuedTokenOverTransport 和 SspiNegotiatedOverTransport。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-304">WCF provides five authentication modes that use secure transport to protect messages; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport and SspiNegotiatedOverTransport.</span></span>  
  
 <span data-ttu-id="d2b7d-305">这些身份验证模式是使用 SecurityPolicy 中描述的传输绑定构造的。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-305">These authentication modes are constructed using the transport binding described in SecurityPolicy.</span></span> <span data-ttu-id="d2b7d-306">对于 UserNameOverTransport 身份验证模式，UsernameToken 是签名支持令牌。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-306">For the UserNameOverTransport authentication mode the UsernameToken is a signed supporting token.</span></span> <span data-ttu-id="d2b7d-307">对于其他身份验证模式，令牌作为签名认可令牌出现。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-307">For the other authentication modes the token appears as a signed endorsing token.</span></span> <span data-ttu-id="d2b7d-308">SecurityPolicy 的附录 C.1.2 和 C.1.3 详细介绍了安全标头布局。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-308">Appendix C.1.2 and C.1.3 of SecurityPolicy describe the security header layout in detail.</span></span> <span data-ttu-id="d2b7d-309">下面的示例安全标头演示给定身份验证模式的 Strict 布局。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-309">The following example security headers show the Strict layout for a given authentication mode.</span></span>  
  
 <span data-ttu-id="d2b7d-310">任何情况下，令牌的“Derived Keys”属性的值总是为“false”。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-310">The value of the "Derived Keys" property for the tokens in all cases is "false".</span></span>  
  
 <span data-ttu-id="d2b7d-311">传输绑定的各个属性的值如下：</span><span class="sxs-lookup"><span data-stu-id="d2b7d-311">The values of the various properties of the transport binding are as follows:</span></span>  
  
 <span data-ttu-id="d2b7d-312">时间戳：true</span><span class="sxs-lookup"><span data-stu-id="d2b7d-312">Timestamp: true</span></span>  
  
 <span data-ttu-id="d2b7d-313">安全标头布局：Strict</span><span class="sxs-lookup"><span data-stu-id="d2b7d-313">Security Header Layout: Strict</span></span>  
  
 <span data-ttu-id="d2b7d-314">算法组：Basic256</span><span class="sxs-lookup"><span data-stu-id="d2b7d-314">Algorithm Suite: Basic256</span></span>  
  
#### <a name="311-usernameovertransport"></a><span data-ttu-id="d2b7d-315">3.1.1 UsernameOverTransport</span><span class="sxs-lookup"><span data-stu-id="d2b7d-315">3.1.1 UsernameOverTransport</span></span>  

 <span data-ttu-id="d2b7d-316">在此身份验证模式下，客户端使用“用户名令牌”进行身份验证，该令牌作为签名支持令牌（总是从发起方发送到接收方）出现在 SOAP 层上。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-316">With this authentication mode, the client authenticates with a Username Token which appears at the SOAP layer as a signed supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="d2b7d-317">在传输层，服务是用 X.509 证书进行身份验证的。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-317">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="d2b7d-318">所用绑定为传输绑定。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-318">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="d2b7d-319">策略</span><span class="sxs-lookup"><span data-stu-id="d2b7d-319">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="UserNameOverTransport_policy"><wsp:ExactlyOne><wsp:All><sp:TransportBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:TransportToken><wsp:Policy><sp:HttpsToken/></wsp:Policy></sp:TransportToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/></wsp:Policy></sp:TransportBinding><sp:SignedEncryptedSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:UsernameToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:WssUsernameToken10/></wsp:Policy></sp:UsernameToken></wsp:Policy></sp:SignedEncryptedSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
 <span data-ttu-id="d2b7d-320">安全标头布局</span><span class="sxs-lookup"><span data-stu-id="d2b7d-320">Security Header Layout</span></span>  
  
 <span data-ttu-id="d2b7d-321">请求</span><span class="sxs-lookup"><span data-stu-id="d2b7d-321">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="_0"> ... </u:Timestamp><o:UsernameToken u:Id="uuid-b96fbb3a-e646-4403-9473-2e5ffc733ff8-1"> ... </o:UsernameToken></o:Security>  
```  
  
 <span data-ttu-id="d2b7d-322">响应</span><span class="sxs-lookup"><span data-stu-id="d2b7d-322">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="_0"> ... </u:Timestamp></o:Security>  
```  
  
#### <a name="312-certificateovertransport"></a><span data-ttu-id="d2b7d-323">3.1.2 CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="d2b7d-323">3.1.2 CertificateOverTransport</span></span>  

 <span data-ttu-id="d2b7d-324">在此身份验证模式下，客户端使用 X.509 证书进行身份验证，该证书作为认可支持令牌（总是从发起方发送到接收方）出现在 SOAP 层上。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-324">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="d2b7d-325">在传输层，服务是用 X.509 证书进行身份验证的。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-325">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="d2b7d-326">所用绑定为传输绑定。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-326">The binding used is a transport binding.</span></span> <span data-ttu-id="d2b7d-327">CertificateOverTransport 仅对 SOAP 标头而非 SOAP 正文进行签名。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-327">CertificateOverTransport only signs the SOAP headers, not the SOAP body.</span></span> <span data-ttu-id="d2b7d-328">这是由 TransportWithMessageCredentials 安全模式使用的身份验证模式。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-328">This is the authentication mode used by the TransportWithMessageCredentials security mode.</span></span> <span data-ttu-id="d2b7d-329">仅对 SOAP 标头进行签名，因为身份验证是通过使用消息凭据进行的。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-329">Only the SOAP headers are signed because authentication is done by using message credentials.</span></span>  
  
 <span data-ttu-id="d2b7d-330">策略</span><span class="sxs-lookup"><span data-stu-id="d2b7d-330">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="CertificateOverTransport_policy"><wsp:ExactlyOne><wsp:All><sp:TransportBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:TransportToken><wsp:Policy><sp:HttpsToken/></wsp:Policy></sp:TransportToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/></wsp:Policy></sp:TransportBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token><sp:SignedParts><sp:Header Name="To" Namespace="http://www.w3.org/2005/08/addressing"/></sp:SignedParts></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
 <span data-ttu-id="d2b7d-331">安全标头布局</span><span class="sxs-lookup"><span data-stu-id="d2b7d-331">Security Header Layout</span></span>  
  
 <span data-ttu-id="d2b7d-332">请求</span><span class="sxs-lookup"><span data-stu-id="d2b7d-332">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="_0"> ... </u:Timestamp><o:BinarySecurityToken> ... </o:BinarySecurityToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature></o:Security>  
```  
  
 <span data-ttu-id="d2b7d-333">响应</span><span class="sxs-lookup"><span data-stu-id="d2b7d-333">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="_0"> ... </u:Timestamp></o:Security>  
```  
  
#### <a name="313-issuedtokenovertransport"></a><span data-ttu-id="d2b7d-334">3.1.3 IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="d2b7d-334">3.1.3 IssuedTokenOverTransport</span></span>  

 <span data-ttu-id="d2b7d-335">在此身份验证模式下，客户端不向服务进行身份验证，而是出示一个由安全令牌服务 (STS) 颁发的令牌，并证明掌握了共享密钥。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-335">With this authentication mode the client does not authenticate to the service, as such, but rather presents a token issued by a Security Token Service (STS) and proves knowledge of a shared key.</span></span> <span data-ttu-id="d2b7d-336">颁发的令牌作为认可支持令牌（总是从发起方发送到接收方）出现在 SOAP 层上。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-336">The issued token appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="d2b7d-337">在传输层，服务是用 X.509 证书进行身份验证的。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-337">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="d2b7d-338">绑定为传输绑定。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-338">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="d2b7d-339">策略</span><span class="sxs-lookup"><span data-stu-id="d2b7d-339">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="IssuedTokenOverTransport_policy">
 <wsp:ExactlyOne>
  <wsp:All>
   <sp:TransportBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702">
    <wsp:Policy>
     <sp:TransportToken>
      <wsp:Policy>
       <sp:HttpsToken />
      </wsp:Policy>
     </sp:TransportToken>
     <sp:AlgorithmSuite>
      <wsp:Policy>
       <sp:Basic256 />
      </wsp:Policy>
     </sp:AlgorithmSuite>
     <sp:Layout>
      <wsp:Policy>
       <sp:Strict/>
      </wsp:Policy>
     </sp:Layout>
     <sp:IncludeTimestamp/>
    </wsp:Policy>
   </sp:TransportBinding>
   <sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702">
    <wsp:Policy>
     <sp:IssuedToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient">
      <Issuer xmlns="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702">
       <Address xmlns="http://www.w3.org/2005/08/addressing">http://www.w3.org/2005/08/addressing/anonymous</Address>
       <Metadata xmlns="http://www.w3.org/2005/08/addressing">
        <Metadata xmlns="http://schemas.xmlsoap.org/ws/2004/09/mex" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
         <wsx:MetadataSection xmlns="">
          <wsx:MetadataReference>
           <Address xmlns="http://www.w3.org/2005/08/addressing"> ... </Address>
           <Identity xmlns="http://schemas.xmlsoap.org/ws/2006/02/addressingidentity">
            <Dns> ...  </Dns>
           </Identity>
          </wsx:MetadataReference>
         </wsx:MetadataSection>
        </Metadata>
       </Metadata>
      </Issuer>
      <sp:RequestSecurityTokenTemplate>
       <trust:KeyType xmlns:trust="http://docs.oasis-open.org/ws-sx/ws-trust/200512">http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey</trust:KeyType>
      </sp:RequestSecurityTokenTemplate>
      <wsp:Policy>
       <sp:RequireInternalReference/>
      </wsp:Policy>
     </sp:IssuedToken>
     <sp:SignedParts>
      <sp:Header Name="To" Namespace="http://www.w3.org/2005/08/addressing"/>
     </sp:SignedParts>
    </wsp:Policy>
   </sp:EndorsingSupportingTokens>
   <sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702">
    <wsp:Policy>
     <sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/>
     <sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/>
    </wsp:Policy>
   </sp:Wss11>
   <sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702">
    <wsp:Policy>
     <sp:MustSupportIssuedTokens/>
     <sp:RequireClientEntropy/>
     <sp:RequireServerEntropy/>
    </wsp:Policy>
   </sp:Trust13>
   <wsaw:UsingAddressing/>
  </wsp:All>
 </wsp:ExactlyOne>
</wsp:Policy>
```  
  
 <span data-ttu-id="d2b7d-340">安全标头布局</span><span class="sxs-lookup"><span data-stu-id="d2b7d-340">Security Header Layout</span></span>  
  
 <span data-ttu-id="d2b7d-341">请求</span><span class="sxs-lookup"><span data-stu-id="d2b7d-341">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-67692bb6-85b7-4299-8587-3ce60086b0d2-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-fab7e1b2-8dc4-412b-bda9-b95a4f836815-16" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d2b7d-342">响应</span><span class="sxs-lookup"><span data-stu-id="d2b7d-342">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-fab7e1b2-8dc4-412b-bda9-b95a4f836815-21"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
#### <a name="314-kerberosovertransport"></a><span data-ttu-id="d2b7d-343">3.1.4 KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="d2b7d-343">3.1.4 KerberosOverTransport</span></span>  

 <span data-ttu-id="d2b7d-344">在此身份验证模式下，客户端使用 Kerberos 票证向服务进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-344">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="d2b7d-345">Kerberos 令牌作为认可支持令牌出现在 SOAP 层上。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-345">The Kerberos token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="d2b7d-346">在传输层，服务是用 X.509 证书进行身份验证的。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-346">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="d2b7d-347">绑定为传输绑定。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-347">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="d2b7d-348">策略</span><span class="sxs-lookup"><span data-stu-id="d2b7d-348">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="KerberosOverTransport_policy"><wsp:ExactlyOne><wsp:All><sp:TransportBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:TransportToken><wsp:Policy><sp:HttpsToken/></wsp:Policy></sp:TransportToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic128/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/></wsp:Policy></sp:TransportBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:KerberosToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Once"><wsp:Policy><sp:WssGssKerberosV5ApReqToken11/></wsp:Policy></sp:KerberosToken><sp:SignedParts><sp:Header Name="To" Namespace="http://www.w3.org/2005/08/addressing"/></sp:SignedParts></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
 <span data-ttu-id="d2b7d-349">安全标头布局</span><span class="sxs-lookup"><span data-stu-id="d2b7d-349">Security Header Layout</span></span>  
  
 <span data-ttu-id="d2b7d-350">请求</span><span class="sxs-lookup"><span data-stu-id="d2b7d-350">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="_0"> ... </u:Timestamp><o:BinarySecurityToken> ... </o:BinarySecurityToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature></o:Security>  
```  
  
 <span data-ttu-id="d2b7d-351">响应</span><span class="sxs-lookup"><span data-stu-id="d2b7d-351">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="_0"> ... </u:Timestamp></o:Security>  
```  
  
#### <a name="315-sspinegotiatedovertransport"></a><span data-ttu-id="d2b7d-352">3.1.5 SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="d2b7d-352">3.1.5 SspiNegotiatedOverTransport</span></span>  

 <span data-ttu-id="d2b7d-353">在此模式下，将使用协商协议来执行客户端和服务器身份验证。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-353">With this mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="d2b7d-354">如果可能，就使用 Kerberos，否则使用 NTLM。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-354">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="d2b7d-355">产生的 SCT 作为认可支持令牌（总是从发起方发送到接收方）出现在 SOAP 层上。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-355">The resulting SCT appears at the SOAP layer as an endorsing supporting token that is always sent from initiator to recipient.</span></span> <span data-ttu-id="d2b7d-356">在传输层，服务还是由 X.509 证书另外进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-356">The service is additionally authenticated at the transport layer by an X.509 certificate.</span></span> <span data-ttu-id="d2b7d-357">所用绑定为传输绑定。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-357">The binding used is a transport binding.</span></span> <span data-ttu-id="d2b7d-358">"SPNEGO" (协商) 介绍 WCF 如何将 SSPI 二进制协商协议用于 WS-TRUST。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-358">"SPNEGO" (negotiation) describes how WCF uses SSPI binary negotiation protocol with WS-Trust.</span></span> <span data-ttu-id="d2b7d-359">在通过 SPNEGO 握手建立 SCT 之后，本节将介绍安全标头示例。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-359">Security header examples in this section are after the SCT has been established through the SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="d2b7d-360">策略</span><span class="sxs-lookup"><span data-stu-id="d2b7d-360">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="SspiNegotiatedOverTransport_policy"><wsp:ExactlyOne><wsp:All><sp:TransportBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:TransportToken><wsp:Policy><sp:HttpsToken/></wsp:Policy></sp:TransportToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/></wsp:Policy></sp:TransportBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:SpnegoContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></sp:SpnegoContextToken><sp:SignedParts><sp:Header Name="To" Namespace="http://www.w3.org/2005/08/addressing"/></sp:SignedParts></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples"></a><span data-ttu-id="d2b7d-361">安全标头示例</span><span class="sxs-lookup"><span data-stu-id="d2b7d-361">Security Header Examples</span></span>  

 <span data-ttu-id="d2b7d-362">在使用 WS-Trust 二进制协商通过 SPNEGO 握手建立安全上下文令牌之后，应用程序消息将具有如下结构的安全标头。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-362">Once the Security Context Token is established through SPNEGO handshake using WS-Trust Binary Negotiation, the application messages have security headers with the following structure.</span></span>  
  
 <span data-ttu-id="d2b7d-363">请求</span><span class="sxs-lookup"><span data-stu-id="d2b7d-363">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="_0"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-9a29d087-5dae-4d40-bf86-5746d9d30eca-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature></o:Security>  
```  
  
 <span data-ttu-id="d2b7d-364">响应</span><span class="sxs-lookup"><span data-stu-id="d2b7d-364">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="_0"> ... </u:Timestamp></o:Security>  
```  
  
### <a name="32-using-x509-certificates-for-service-authentication"></a><span data-ttu-id="d2b7d-365">3.2 使用 x.509 证书进行服务身份验证</span><span class="sxs-lookup"><span data-stu-id="d2b7d-365">3.2 Using X.509 Certificates for Service Authentication</span></span>  

 <span data-ttu-id="d2b7d-366">本节介绍以下身份验证模式：MutualCertificate WSS1.0、Mutual CertificateDuplex、MutualCertificate WSS1.1、AnonymousForCertificate、UserNameForCertificate 和 IssuedTokenForCertificate。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-366">This section describes the following authentication modes: MutualCertificate WSS1.0, Mutual CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate and IssuedTokenForCertificate.</span></span>  
  
#### <a name="321-mutualcertificate-wss10"></a><span data-ttu-id="d2b7d-367">3.2.1 MutualCertificate WSS1.0</span><span class="sxs-lookup"><span data-stu-id="d2b7d-367">3.2.1 MutualCertificate WSS1.0</span></span>  

 <span data-ttu-id="d2b7d-368">在此身份验证模式下，客户端使用 X.509 证书进行身份验证，该证书作为发起方令牌出现在 SOAP 层上。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-368">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="d2b7d-369">同样使用 X.509 证书对服务进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-369">The service is also authenticated using an X.509 certificate.</span></span> <span data-ttu-id="d2b7d-370">同时对 SOAP 标头和 SOAP 正文进行签名。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-370">Both the SOAP headers and the SOAP body are signed.</span></span> <span data-ttu-id="d2b7d-371">创建对称密钥并使用收件人的传输证书对该密钥进行加密。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-371">A symmetric key is created and is encrypted with the transport certificate for the recipient.</span></span>  
  
 <span data-ttu-id="d2b7d-372">所用绑定为带有以下属性值的非对称绑定：</span><span class="sxs-lookup"><span data-stu-id="d2b7d-372">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="d2b7d-373">发起方令牌：客户端的 X.509 证书，包含模式设置为 .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="d2b7d-373">Initiator Token: the client’s X.509 certificate, with inclusion mode set to .../IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="d2b7d-374">接收方令牌：服务器的 X.509 证书，包含模式设置为 .../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="d2b7d-374">Recipient Token: Server’s X.509 Certificate, with inclusion mode is set .../IncludeToken/Never</span></span>  
  
 <span data-ttu-id="d2b7d-375">令牌保护：False</span><span class="sxs-lookup"><span data-stu-id="d2b7d-375">Token Protection: False</span></span>  
  
 <span data-ttu-id="d2b7d-376">整个标头和正文签名：True</span><span class="sxs-lookup"><span data-stu-id="d2b7d-376">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="d2b7d-377">保护顺序：SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="d2b7d-377">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="d2b7d-378">加密签名：True</span><span class="sxs-lookup"><span data-stu-id="d2b7d-378">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="d2b7d-379">策略</span><span class="sxs-lookup"><span data-stu-id="d2b7d-379">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="MutualCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:AsymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:InitiatorToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:InitiatorToken><sp:RecipientToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:RecipientToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:AsymmetricBinding><sp:Wss10 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/></wsp:Policy></sp:Wss10><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="d2b7d-380">安全标头示例：SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="d2b7d-380">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="d2b7d-381">请求</span><span class="sxs-lookup"><span data-stu-id="d2b7d-381">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-39cb393e-9da8-4d5d-b273-540ef614569b-1"> ... </u:Timestamp><o:BinarySecurityToken> ... </o:BinarySecurityToken><e:EncryptedKey Id="_0" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><e:EncryptedData Id="_7" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d2b7d-382">响应</span><span class="sxs-lookup"><span data-stu-id="d2b7d-382">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"> <u:Timestamp u:Id="uuid-3d742930-70d3-4d7e-aa0a-8721128dc115-8"> ... </u:Timestamp><e:EncryptedKey Id="_0" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><e:EncryptedData Id="_5" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d2b7d-383">策略</span><span class="sxs-lookup"><span data-stu-id="d2b7d-383">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="MutualCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:AsymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:InitiatorToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:InitiatorToken><sp:RecipientToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:RecipientToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:AsymmetricBinding><sp:Wss10 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/></wsp:Policy></sp:Wss10><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="d2b7d-384">安全标头示例：EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="d2b7d-384">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="d2b7d-385">请求</span><span class="sxs-lookup"><span data-stu-id="d2b7d-385">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-73da3e21-abff-4294-a910-e75303d280cc-1"> ... </u:Timestamp><o:BinarySecurityToken> ... </o:BinarySecurityToken><e:EncryptedKey Id="_0" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 <span data-ttu-id="d2b7d-386">响应</span><span class="sxs-lookup"><span data-stu-id="d2b7d-386">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-02f276b6-804f-480d-99e9-2e90fc76ab27-3"> ... </u:Timestamp><e:EncryptedKey Id="_0" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
#### <a name="322-mutualcertificateduplex"></a><span data-ttu-id="d2b7d-387">3.2.2 MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="d2b7d-387">3.2.2 MutualCertificateDuplex</span></span>  

 <span data-ttu-id="d2b7d-388">在此身份验证模式下，客户端使用 X.509 证书进行身份验证，该证书作为发起方令牌出现在 SOAP 层上。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-388">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="d2b7d-389">同样使用 X.509 证书对服务进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-389">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="d2b7d-390">所用绑定为带有以下属性值的非对称绑定：</span><span class="sxs-lookup"><span data-stu-id="d2b7d-390">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="d2b7d-391">发起方令牌：客户端的 X509 证书，包含模式设置为 .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="d2b7d-391">Initiator Token: Client’s X509 Certificate, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="d2b7d-392">接收方令牌：服务器的 X509 证书，包含模式设置为 .../IncludeToken/AlwaysToInitiator</span><span class="sxs-lookup"><span data-stu-id="d2b7d-392">Recipient Token: Server’s X509 Certificate, inclusion mode is set to .../IncludeToken/AlwaysToInitiator</span></span>  
  
 <span data-ttu-id="d2b7d-393">令牌保护：False</span><span class="sxs-lookup"><span data-stu-id="d2b7d-393">Token Protection: False</span></span>  
  
 <span data-ttu-id="d2b7d-394">整个标头和正文签名：True</span><span class="sxs-lookup"><span data-stu-id="d2b7d-394">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="d2b7d-395">保护顺序：SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="d2b7d-395">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="d2b7d-396">加密签名：True</span><span class="sxs-lookup"><span data-stu-id="d2b7d-396">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="d2b7d-397">策略</span><span class="sxs-lookup"><span data-stu-id="d2b7d-397">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="MutualCertificateDuplex_policy"><wsp:ExactlyOne><wsp:All><sp:AsymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:InitiatorToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:InitiatorToken><sp:RecipientToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToInitiator"><wsp:Policy><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:RecipientToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:AsymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><cdp:CompositeDuplex xmlns:cdp="http://schemas.microsoft.com/net/2006/06/duplex"/><ow:OneWay xmlns:ow="http://schemas.microsoft.com/ws/2005/05/routing/policy"/><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="d2b7d-398">安全标头示例：SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="d2b7d-398">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="d2b7d-399">请求和响应</span><span class="sxs-lookup"><span data-stu-id="d2b7d-399">Request and Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-4dec3da4-b572-4654-ba4d-4a2f84a87510-1"> ... </u:Timestamp><o:BinarySecurityToken> ... </o:BinarySecurityToken><e:EncryptedKey Id="_0" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><e:EncryptedData Id="_7" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d2b7d-400">策略</span><span class="sxs-lookup"><span data-stu-id="d2b7d-400">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="MutualCertificateDuplex_policy"><wsp:ExactlyOne><wsp:All><sp:AsymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:InitiatorToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:InitiatorToken><sp:RecipientToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToInitiator"><wsp:Policy><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:RecipientToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:AsymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><cdp:CompositeDuplex xmlns:cdp="http://schemas.microsoft.com/net/2006/06/duplex"/><ow:OneWay xmlns:ow="http://schemas.microsoft.com/ws/2005/05/routing/policy"/><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="d2b7d-401">安全标头示例：EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="d2b7d-401">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="d2b7d-402">请求和响应</span><span class="sxs-lookup"><span data-stu-id="d2b7d-402">Request and Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-b0e23feb-cd2d-4dc1-bad9-284bc45f3be3-1"> ... </u:Timestamp><o:BinarySecurityToken> ... </o:BinarySecurityToken><e:EncryptedKey Id="_0" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
#### <a name="323-using-symmetricbinding-with-x509-service-authentication"></a><span data-ttu-id="d2b7d-403">3.2.3 将 SymmetricBinding 用于 X.509 服务身份验证</span><span class="sxs-lookup"><span data-stu-id="d2b7d-403">3.2.3 Using SymmetricBinding with X.509 Service Authentication</span></span>  

 <span data-ttu-id="d2b7d-404">“WSS10”对 X509 令牌方案提供有限支持。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-404">"WSS10" provided limited support for scenarios with X509 tokens.</span></span> <span data-ttu-id="d2b7d-405">例如，如果消息仅使用服务 X509 令牌，则无法为其提供签名和加密保护。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-405">For example, there was no way to provide signature and encryption protection for messages using only service X509 token.</span></span> <span data-ttu-id="d2b7d-406">“WSS11”将 EncryptedKey 用作对称令牌。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-406">"WSS11" introduced the usage of EncryptedKey as a symmetric token.</span></span> <span data-ttu-id="d2b7d-407">现在，为服务的 X.509 证书加密的临时密钥可同时用于请求和响应消息保护。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-407">Now a temporary key encrypted for the service's X.509 certificate could be used for both request and response messages protection.</span></span> <span data-ttu-id="d2b7d-408">下面3.4 部分中描述的身份验证模式使用此模式。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-408">The authentication modes described in the section 3.4 below use this pattern.</span></span>  
  
 <span data-ttu-id="d2b7d-409">WS-SecurityPolicy 描述了此模式，即将 SymmetricBinding 用于服务 X509 令牌作为保护令牌。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-409">WS-SecurityPolicy describes this pattern using SymmetricBinding with Service X509 token as the protection token.</span></span>  
  
 <span data-ttu-id="d2b7d-410">身份验证模式 AnonymousForCertificate、UsernameForCertificate、MutualCertificate WSS11 和 IssuedTokenForCertificate 都使用具有以下属性值的类似的 sp:SymmetricBinding 实例：</span><span class="sxs-lookup"><span data-stu-id="d2b7d-410">Authentication modes AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 and IssuedTokenForCertificate all use a similar instance of sp:SymmetricBinding with the following property values:</span></span>  
  
 <span data-ttu-id="d2b7d-411">保护令牌：服务器的 X509 证书，包含模式设置为 …/IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="d2b7d-411">Protection Token: Server’s X509 Certificate, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="d2b7d-412">令牌保护：False</span><span class="sxs-lookup"><span data-stu-id="d2b7d-412">Token Protection: False</span></span>  
  
 <span data-ttu-id="d2b7d-413">整个标头和正文签名：True</span><span class="sxs-lookup"><span data-stu-id="d2b7d-413">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="d2b7d-414">保护顺序：SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="d2b7d-414">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="d2b7d-415">加密签名：True</span><span class="sxs-lookup"><span data-stu-id="d2b7d-415">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="d2b7d-416">上述身份验证模式的区别仅在于它们所使用的支持令牌。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-416">The above authentication modes only differ by the supporting tokens they use.</span></span> <span data-ttu-id="d2b7d-417">AnonymousForCertificate 没有任何支持令牌，MutualCertificate WSS 1.1 将客户端的 X509 证书作为认可支持令牌，UserNameForCertificate 将“用户名令牌”作为签名支持令牌，而 IssuedTokenForCertificate 将颁发的令牌作为认可支持令牌。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-417">AnonymousForCertificate does not have any supporting tokens, MutualCertificate WSS 1.1 has the client’s X509 certificate as an endorsing supporting tokens, UserNameForCertificate has a UserName Token as a signed supporting token and IssuedTokenForCertificate has the issued token as an endorsing supporting token.</span></span>  
  
#### <a name="324-anonymousforcertificate"></a><span data-ttu-id="d2b7d-418">3.2.4 AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="d2b7d-418">3.2.4 AnonymousForCertificate</span></span>  

 <span data-ttu-id="d2b7d-419">在此身份验证模式下，客户端是匿名的，而使用 X.509 证书对服务进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-419">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="d2b7d-420">所用绑定是对称绑定的一个实例，如上面 3.4.2 中所述。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-420">The binding used is an instance of symmetric binding as described in 3.4.2.</span></span>  
  
 <span data-ttu-id="d2b7d-421">策略</span><span class="sxs-lookup"><span data-stu-id="d2b7d-421">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="AnonymousforCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/><sp:RequireSignatureConfirmation/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="d2b7d-422">安全标头示例：SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="d2b7d-422">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="d2b7d-423">请求</span><span class="sxs-lookup"><span data-stu-id="d2b7d-423">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-4de2d2a1-6266-4a02-93e6-242a1ac2aeb3-2"> ... </u:Timestamp><e:EncryptedKey Id="uuid-4de2d2a1-6266-4a02-93e6-242a1ac2aeb3-1" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d2b7d-424">响应</span><span class="sxs-lookup"><span data-stu-id="d2b7d-424">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-b06cb481-3176-4c56-af35-c38252bb6c78-4"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_2" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData><e:EncryptedData Id="_7" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d2b7d-425">策略</span><span class="sxs-lookup"><span data-stu-id="d2b7d-425">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="AnonymousforCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/><sp:RequireSignatureConfirmation/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="d2b7d-426">安全标头示例：EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="d2b7d-426">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="d2b7d-427">请求</span><span class="sxs-lookup"><span data-stu-id="d2b7d-427">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-562aac68-8cdd-45d5-bc03-df662e6ed048-2"> ... </u:Timestamp><e:EncryptedKey Id="uuid-562aac68-8cdd-45d5-bc03-df662e6ed048-1" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 <span data-ttu-id="d2b7d-428">响应</span><span class="sxs-lookup"><span data-stu-id="d2b7d-428">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-15b48260-23da-424d-8dc4-8f4e150fb8cf-3"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><k:SignatureConfirmation u:Id="_2" Value="ALF+QNGmWn2k3LpWEDIzSBgTkvo=" xmlns:k="http://docs.oasis-open.org/wss/oasis-wss-wssecurity-secext-1.1.xsd"></k:SignatureConfirmation><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
#### <a name="325-usernameforcertificate"></a><span data-ttu-id="d2b7d-429">3.2.5 UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="d2b7d-429">3.2.5 UserNameForCertificate</span></span>  

 <span data-ttu-id="d2b7d-430">在此身份验证模式下，客户端使用“用户名令牌”向服务进行身份验证，该令牌作为签名支持令牌出现在 SOAP 层上。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-430">With this authentication mode the client authenticates to the service using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="d2b7d-431">服务使用 X.509 证书对客户端进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-431">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="d2b7d-432">所用绑定为对称绑定，其保护令牌是由客户端生成的密钥，用服务的公钥进行加密。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-432">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="d2b7d-433">策略</span><span class="sxs-lookup"><span data-stu-id="d2b7d-433">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="UserNameForCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:SignedEncryptedSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:UsernameToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:WssUsernameToken10/></wsp:Policy></sp:UsernameToken></wsp:Policy></sp:SignedEncryptedSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><http:BasicAuthentication xmlns:http="http://schemas.microsoft.com/ws/06/2004/policy/http"/><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="d2b7d-434">安全标头示例：SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="d2b7d-434">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="d2b7d-435">请求</span><span class="sxs-lookup"><span data-stu-id="d2b7d-435">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-27196139-acb9-410f-a2c6-51d20d24278b-2"> ... </u:Timestamp><e:EncryptedKey Id="uuid-27196139-acb9-410f-a2c6-51d20d24278b-1" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_9" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d2b7d-436">响应</span><span class="sxs-lookup"><span data-stu-id="d2b7d-436">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-681226f7-126a-4806-b732-fcca097cd7a8-5"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d2b7d-437">策略</span><span class="sxs-lookup"><span data-stu-id="d2b7d-437">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="UserNameForCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:SignedEncryptedSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:UsernameToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:WssUsernameToken10/></wsp:Policy></sp:UsernameToken></wsp:Policy></sp:SignedEncryptedSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><http:BasicAuthentication xmlns:http="http://schemas.microsoft.com/ws/06/2004/policy/http"/><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="d2b7d-438">安全标头示例：EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="d2b7d-438">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="d2b7d-439">请求</span><span class="sxs-lookup"><span data-stu-id="d2b7d-439">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-8276d8b7-74a0-4257-b8a5-e25350e7c2d4-2"> ... </u:Timestamp><e:EncryptedKey Id="uuid-8276d8b7-74a0-4257-b8a5-e25350e7c2d4-1" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 <span data-ttu-id="d2b7d-440">响应</span><span class="sxs-lookup"><span data-stu-id="d2b7d-440">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-8a7ad353-f071-49dc-90dd-5ad2e9abd40a-4"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
#### <a name="326-mutualcertificate-wss-11"></a><span data-ttu-id="d2b7d-441">3.2.6 MutualCertificate (WSS 1.1)</span><span class="sxs-lookup"><span data-stu-id="d2b7d-441">3.2.6 MutualCertificate (WSS 1.1)</span></span>  

 <span data-ttu-id="d2b7d-442">在此身份验证模式下，客户端使用 X.509 证书进行身份验证，该证书作为认可支持令牌出现在 SOAP 层上。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-442">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="d2b7d-443">同样使用 X.509 证书对服务进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-443">The service is also authenticated using an X.509 certificate.</span></span> <span data-ttu-id="d2b7d-444">所用绑定为对称绑定，其保护令牌是由客户端生成的密钥，用服务的公钥进行加密。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-444">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="d2b7d-445">策略</span><span class="sxs-lookup"><span data-stu-id="d2b7d-445">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="MutualCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/><sp:RequireSignatureConfirmation/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="d2b7d-446">安全标头示例：SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="d2b7d-446">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="d2b7d-447">请求</span><span class="sxs-lookup"><span data-stu-id="d2b7d-447">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-75305d4e-f54f-4e36-9de9-45b6d2053c80-2"> ... </u:Timestamp><e:EncryptedKey Id="uuid-75305d4e-f54f-4e36-9de9-45b6d2053c80-1" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_2" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><o:BinarySecurityToken> ...</o:BinarySecurityToken><e:EncryptedData Id="_9" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData><e:EncryptedData Id="_10" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d2b7d-448">响应</span><span class="sxs-lookup"><span data-stu-id="d2b7d-448">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-8c73fa91-f95b-40ff-b088-48118e6fadcf-5"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_3" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_9" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData><e:EncryptedData Id="_10" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d2b7d-449">策略</span><span class="sxs-lookup"><span data-stu-id="d2b7d-449">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="MutualCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/><sp:RequireSignatureConfirmation/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="d2b7d-450">安全标头示例：EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="d2b7d-450">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="d2b7d-451">请求</span><span class="sxs-lookup"><span data-stu-id="d2b7d-451">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-0b940a9e-606f-43b9-b05d-a162043529bc-2"> ... </u:Timestamp><e:EncryptedKey Id="uuid-0b940a9e-606f-43b9-b05d-a162043529bc-1" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><o:BinarySecurityToken> ... </o:BinarySecurityToken><Signature Id="_2" xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 <span data-ttu-id="d2b7d-452">响应</span><span class="sxs-lookup"><span data-stu-id="d2b7d-452">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-67dacc31-4a50-4866-b673-ccc03e156337-3"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><k:SignatureConfirmation u:Id="_2" Value="mYyksUQKkK27Fd6hmgOiqFwvudk=" xmlns:k="http://docs.oasis-open.org/wss/oasis-wss-wssecurity-secext-1.1.xsd"></k:SignatureConfirmation><k:SignatureConfirmation u:Id="_3" Value="SreOZ4Rr2BcXjFQFvgN55ERypI/1/86hdWThE5lav0eYIxF1OCzQgZF+y7cQ82t+g3CRnLbE3c52DqMpY/HXlrdMct3m3rnpDH+fqdhNY4fE+M2v4zUMFR7uxDKWcEm9zZpmUvJCDfJRfKRaKjy5cTbccRKqSxw7HAqOYnqibA4=" xmlns:k="http://docs.oasis-open.org/wss/oasis-wss-wssecurity-secext-1.1.xsd"></k:SignatureConfirmation><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
#### <a name="327-issuedtokenforcertificate"></a><span data-ttu-id="d2b7d-453">3.2.7 IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="d2b7d-453">3.2.7 IssuedTokenForCertificate</span></span>  

 <span data-ttu-id="d2b7d-454">在此身份验证模式下，客户端不向服务进行身份验证，而是出示一个由 STS 颁发的令牌，并证明掌握了共享密钥。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-454">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by a STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="d2b7d-455">颁发的令牌作为认可支持令牌出现在 SOAP 层上。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-455">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="d2b7d-456">服务使用 X.509 证书对客户端进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-456">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="d2b7d-457">所用绑定为对称绑定，其保护令牌是由客户端生成的密钥，用服务的公钥进行加密。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-457">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="d2b7d-458">策略</span><span class="sxs-lookup"><span data-stu-id="d2b7d-458">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="IssuedTokenForCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:IssuedToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><Issuer xmlns="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><Address xmlns="http://www.w3.org/2005/08/addressing">http://www.w3.org/2005/08/addressing/anonymous</Address><Metadata xmlns="http://www.w3.org/2005/08/addressing"><Metadata xmlns="http://schemas.xmlsoap.org/ws/2004/09/mex" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><wsx:MetadataSection xmlns=""><wsx:MetadataReference><Address xmlns="http://www.w3.org/2005/08/addressing"> ... </Address><Identity xmlns="http://schemas.xmlsoap.org/ws/2006/02/addressingidentity"><Dns> ...  </Dns></Identity></wsx:MetadataReference></wsx:MetadataSection></Metadata></Metadata></Issuer><sp:RequestSecurityTokenTemplate><trust:KeyType xmlns:trust="http://docs.oasis-open.org/ws-sx/ws-trust/200512">http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey</trust:KeyType></sp:RequestSecurityTokenTemplate><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireInternalReference/></wsp:Policy></sp:IssuedToken></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/><sp:RequireSignatureConfirmation/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="d2b7d-459">安全标头示例：SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="d2b7d-459">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="d2b7d-460">请求</span><span class="sxs-lookup"><span data-stu-id="d2b7d-460">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-1d2c03e6-0b69-4483-903a-6ef9b9d286ed-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-3f0f57fa-046d-40c0-919f-d0d7aa640b9f-1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d2b7d-461">响应</span><span class="sxs-lookup"><span data-stu-id="d2b7d-461">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-3f0f57fa-046d-40c0-919f-d0d7aa640b9f-6"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="d2b7d-462">安全标头示例：EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="d2b7d-462">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="d2b7d-463">策略</span><span class="sxs-lookup"><span data-stu-id="d2b7d-463">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="IssuedTokenForCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:IssuedToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><Issuer xmlns="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><Address xmlns="http://www.w3.org/2005/08/addressing">http://www.w3.org/2005/08/addressing/anonymous</Address><Metadata xmlns="http://www.w3.org/2005/08/addressing"><Metadata xmlns="http://schemas.xmlsoap.org/ws/2004/09/mex" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><wsx:MetadataSection xmlns=""><wsx:MetadataReference><Address xmlns="http://www.w3.org/2005/08/addressing"> ... </Address><Identity xmlns="http://schemas.xmlsoap.org/ws/2006/02/addressingidentity"><Dns> ...  </Dns></Identity></wsx:MetadataReference></wsx:MetadataSection></Metadata></Metadata></Issuer><sp:RequestSecurityTokenTemplate><trust:KeyType xmlns:trust="http://docs.oasis-open.org/ws-sx/ws-trust/200512">http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey</trust:KeyType></sp:RequestSecurityTokenTemplate><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireInternalReference/></wsp:Policy></sp:IssuedToken></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/><sp:RequireSignatureConfirmation/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
 <span data-ttu-id="d2b7d-464">请求</span><span class="sxs-lookup"><span data-stu-id="d2b7d-464">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-de1c51aa-2ecc-4e70-b6bd-9dca58331fa7-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-96c5e80a-9b87-4c6f-af77-752ca65cf607-16" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d2b7d-465">响应</span><span class="sxs-lookup"><span data-stu-id="d2b7d-465">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-96c5e80a-9b87-4c6f-af77-752ca65cf607-21"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
## <a name="33-kerberos"></a><span data-ttu-id="d2b7d-466">3.3 Kerberos</span><span class="sxs-lookup"><span data-stu-id="d2b7d-466">3.3 Kerberos</span></span>  

 <span data-ttu-id="d2b7d-467">在此身份验证模式下，客户端使用 Kerberos 票证向服务进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-467">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="d2b7d-468">该票证还提供服务器身份验证。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-468">That same ticket also provides server authentication.</span></span> <span data-ttu-id="d2b7d-469">所用绑定为对称绑定，具有以下属性：</span><span class="sxs-lookup"><span data-stu-id="d2b7d-469">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="d2b7d-470">保护令牌：Kerberos 票证，包含模式设置为 .../IncludeToken/Once</span><span class="sxs-lookup"><span data-stu-id="d2b7d-470">Protection Token: Kerberos Ticket, inclusion mode is set to .../IncludeToken/Once</span></span>  
<span data-ttu-id="d2b7d-471">令牌保护：False</span><span class="sxs-lookup"><span data-stu-id="d2b7d-471">Token Protection: False</span></span>  
  
 <span data-ttu-id="d2b7d-472">整个标头和正文签名：True</span><span class="sxs-lookup"><span data-stu-id="d2b7d-472">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="d2b7d-473">保护顺序：SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="d2b7d-473">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="d2b7d-474">加密签名：True</span><span class="sxs-lookup"><span data-stu-id="d2b7d-474">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="d2b7d-475">策略</span><span class="sxs-lookup"><span data-stu-id="d2b7d-475">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="Kerberos_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:KerberosToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Once"><wsp:Policy><sp:RequireDerivedKeys/><sp:WssGssKerberosV5ApReqToken11/></wsp:Policy></sp:KerberosToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic128/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="d2b7d-476">安全标头示例：SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="d2b7d-476">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="d2b7d-477">请求</span><span class="sxs-lookup"><span data-stu-id="d2b7d-477">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-e8f6dc3b-407d-4387-bd33-97aedfd8bf13-2"> ... </u:Timestamp><o:BinarySecurityToken> ... </o:BinarySecurityToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d2b7d-478">响应</span><span class="sxs-lookup"><span data-stu-id="d2b7d-478">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-7b03568e-66ae-49da-82ee-5d12d372876e-3"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d2b7d-479">策略</span><span class="sxs-lookup"><span data-stu-id="d2b7d-479">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="Kerberos_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:KerberosToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Once"><wsp:Policy><sp:RequireDerivedKeys/><sp:WssGssKerberosV5ApReqToken11/></wsp:Policy></sp:KerberosToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic128/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="d2b7d-480">安全标头示例：EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="d2b7d-480">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="d2b7d-481">请求</span><span class="sxs-lookup"><span data-stu-id="d2b7d-481">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-d29247f0-f220-4e81-9a8d-a15f5ac31072-2"> ... </u:Timestamp><o:BinarySecurityToken> ... </o:BinarySecurityToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 <span data-ttu-id="d2b7d-482">响应</span><span class="sxs-lookup"><span data-stu-id="d2b7d-482">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-9025b930-4f15-42fe-8e78-35d3a3480177-2"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
#### <a name="34-issuedtoken"></a><span data-ttu-id="d2b7d-483">3.4 IssuedToken</span><span class="sxs-lookup"><span data-stu-id="d2b7d-483">3.4 IssuedToken</span></span>  

 <span data-ttu-id="d2b7d-484">在此身份验证模式下，客户端不向服务进行身份验证，而是提供一个由 STS 颁发的令牌，并证明掌握了共享密钥。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-484">With this authentication mode the client does not authenticate to the service, as such, rather the client presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="d2b7d-485">服务也不向客户端进行身份验证，而是由 STS 将共享密钥作为颁发的令牌的一部分进行加密，这样，只有服务才能解密该密钥。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-485">The service is not authenticated to the client, as such, instead the STS encrypts the shared key as part of the issued token such that only the service can decrypt the key.</span></span> <span data-ttu-id="d2b7d-486">所用绑定为对称绑定，具有以下属性：</span><span class="sxs-lookup"><span data-stu-id="d2b7d-486">The binding used is as symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="d2b7d-487">保护令牌：颁发的令牌，包含模式设置为 .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="d2b7d-487">Protection Token: Issued Token, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="d2b7d-488">令牌保护：False</span><span class="sxs-lookup"><span data-stu-id="d2b7d-488">Token Protection: False</span></span>  
  
 <span data-ttu-id="d2b7d-489">整个标头和正文签名：True</span><span class="sxs-lookup"><span data-stu-id="d2b7d-489">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="d2b7d-490">保护顺序：SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="d2b7d-490">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="d2b7d-491">加密签名：True</span><span class="sxs-lookup"><span data-stu-id="d2b7d-491">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="d2b7d-492">策略</span><span class="sxs-lookup"><span data-stu-id="d2b7d-492">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="IssuedToken_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:IssuedToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><Issuer xmlns="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><Address xmlns="http://www.w3.org/2005/08/addressing">http://www.w3.org/2005/08/addressing/anonymous</Address><Metadata xmlns="http://www.w3.org/2005/08/addressing"><Metadata xmlns="http://schemas.xmlsoap.org/ws/2004/09/mex" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><wsx:MetadataSection xmlns=""><wsx:MetadataReference><Address xmlns="http://www.w3.org/2005/08/addressing"> ... </Address><Identity xmlns="http://schemas.xmlsoap.org/ws/2006/02/addressingidentity"><Dns> ...  </Dns></Identity></wsx:MetadataReference></wsx:MetadataSection></Metadata></Metadata></Issuer><sp:RequestSecurityTokenTemplate><trust:KeyType xmlns:trust="http://docs.oasis-open.org/ws-sx/ws-trust/200512">http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey</trust:KeyType></sp:RequestSecurityTokenTemplate><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireInternalReference/></wsp:Policy></sp:IssuedToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="d2b7d-493">安全标头示例：SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="d2b7d-493">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="d2b7d-494">请求</span><span class="sxs-lookup"><span data-stu-id="d2b7d-494">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-61ce3989-bc38-4d67-8262-6232c9d49a26-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-7e2d2617-1c28-465a-be30-de4a78cfc0e2-1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d2b7d-495">响应</span><span class="sxs-lookup"><span data-stu-id="d2b7d-495">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-7e2d2617-1c28-465a-be30-de4a78cfc0e2-6"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>
```  
  
 <span data-ttu-id="d2b7d-496">策略</span><span class="sxs-lookup"><span data-stu-id="d2b7d-496">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="IssuedToken_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:IssuedToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><Issuer xmlns="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><Address xmlns="http://www.w3.org/2005/08/addressing">http://www.w3.org/2005/08/addressing/anonymous</Address><Metadata xmlns="http://www.w3.org/2005/08/addressing"><Metadata xmlns="http://schemas.xmlsoap.org/ws/2004/09/mex" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><wsx:MetadataSection xmlns=""><wsx:MetadataReference><Address xmlns="http://www.w3.org/2005/08/addressing"> ... </Address><Identity xmlns="http://schemas.xmlsoap.org/ws/2006/02/addressingidentity"><Dns> ...  </Dns></Identity></wsx:MetadataReference></wsx:MetadataSection></Metadata></Metadata></Issuer><sp:RequestSecurityTokenTemplate><trust:KeyType xmlns:trust="http://docs.oasis-open.org/ws-sx/ws-trust/200512">http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey</trust:KeyType></sp:RequestSecurityTokenTemplate><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireInternalReference/></wsp:Policy></sp:IssuedToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="d2b7d-497">安全标头示例：EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="d2b7d-497">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="d2b7d-498">请求</span><span class="sxs-lookup"><span data-stu-id="d2b7d-498">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-1dc8bdef-4202-4e08-8a5e-ab94da579dec-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-7e004f51-63a3-4069-9b03-6a1a311a3181-1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d2b7d-499">响应</span><span class="sxs-lookup"><span data-stu-id="d2b7d-499">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-7e004f51-63a3-4069-9b03-6a1a311a3181-6"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> </c:DerivedKeyToken> ... <c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
### <a name="35-using-sslnegotiated-for-service-authentication"></a><span data-ttu-id="d2b7d-500">3.5 使用 SslNegotiated 进行服务身份验证</span><span class="sxs-lookup"><span data-stu-id="d2b7d-500">3.5 Using SslNegotiated for Service Authentication</span></span>  

 <span data-ttu-id="d2b7d-501">本节介绍的一组身份验证模式将对称绑定用于保护令牌，作为安全上下文令牌（符合 WS-SecureConversation (WS-SC)），其键值是通过对 WS-Trust (WS-T) RST/RSTR 消息执行 TLS 协议进行协商的。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-501">This section describes a group of authentication modes that use a symmetric binding with the protection token being a Security Context Token per WS-SecureConversation (WS-SC) whose key value is negotiated by executing the TLS protocol over WS-Trust (WS-T) RST/RSTR messages.</span></span> <span data-ttu-id="d2b7d-502">有关使用 WS-Trust 实现 TLS 握手的详细信息，请参见 TLSNEGO 中的内容。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-502">Details of the TLS handshake implementation using WS-Trust are described in TLSNEGO.</span></span> <span data-ttu-id="d2b7d-503">此处的消息示例中，我们假设已通过握手建立了带有关联安全上下文的 SCT。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-503">Here in the message examples we will assume that SCT with an associated security context is already established through a handshake.</span></span>  
  
 <span data-ttu-id="d2b7d-504">所用绑定为对称绑定，具有以下属性：</span><span class="sxs-lookup"><span data-stu-id="d2b7d-504">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="d2b7d-505">保护令牌：SslContextToken，包含模式设置为 .../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="d2b7d-505">Protection Token: SslContextToken, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="d2b7d-506">令牌保护：False</span><span class="sxs-lookup"><span data-stu-id="d2b7d-506">Token Protection: False</span></span>  
  
 <span data-ttu-id="d2b7d-507">整个标头和正文签名：True</span><span class="sxs-lookup"><span data-stu-id="d2b7d-507">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="d2b7d-508">保护顺序：SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="d2b7d-508">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="d2b7d-509">加密签名：True</span><span class="sxs-lookup"><span data-stu-id="d2b7d-509">Encrypt Signature: True</span></span>  
  
#### <a name="351-policy-for-sslnegotiated-service-authentication"></a><span data-ttu-id="d2b7d-510">3.5.1 SslNegotiated 服务身份验证的策略</span><span class="sxs-lookup"><span data-stu-id="d2b7d-510">3.5.1 Policy for SslNegotiated service authentication</span></span>  

 <span data-ttu-id="d2b7d-511">本节介绍的所有身份验证模式的策略都相似，唯一的区别在于，所用的特定签名支持令牌或认可令牌不相同。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-511">Policy for all authentication modes in this section are similar and differ only by specific signed supporting or endorsing tokens used.</span></span>  
  
#### <a name="352-anonymousforsslnegotiated"></a><span data-ttu-id="d2b7d-512">3.5.2 AnonymousForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="d2b7d-512">3.5.2 AnonymousForSslNegotiated</span></span>  

 <span data-ttu-id="d2b7d-513">在此身份验证模式下，客户端是匿名的，而使用 X.509 证书对服务进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-513">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="d2b7d-514">所用绑定是对称绑定的一个实例，如上面 3.5.1 中所述。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-514">The binding used is an instance of symmetric binding as described in 3.5.1 above.</span></span>  
  
 <span data-ttu-id="d2b7d-515">策略</span><span class="sxs-lookup"><span data-stu-id="d2b7d-515">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="AnonymousForSslNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><mssp:SslContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient" xmlns:mssp="http://schemas.microsoft.com/ws/2005/07/securitypolicy"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></mssp:SslContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="d2b7d-516">安全标头示例：SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="d2b7d-516">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="d2b7d-517">请求</span><span class="sxs-lookup"><span data-stu-id="d2b7d-517">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-f4b86ce2-4ba6-4c55-bac1-2e920fc6d5db-4"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-d21ec2b8-99f5-443c-a4c6-a4d40619187e-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d2b7d-518">响应</span><span class="sxs-lookup"><span data-stu-id="d2b7d-518">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-d21ec2b8-99f5-443c-a4c6-a4d40619187e-4"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d2b7d-519">策略</span><span class="sxs-lookup"><span data-stu-id="d2b7d-519">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="AnonymousForSslNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><mssp:SslContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient" xmlns:mssp="http://schemas.microsoft.com/ws/2005/07/securitypolicy"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></mssp:SslContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="d2b7d-520">安全标头示例：EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="d2b7d-520">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="d2b7d-521">请求</span><span class="sxs-lookup"><span data-stu-id="d2b7d-521">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-c84b24b9-39e0-4cc3-99e2-cec088f1b9eb-4"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-df206ad9-1ee2-46d7-9fb4-6e4631c9762f-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 <span data-ttu-id="d2b7d-522">响应</span><span class="sxs-lookup"><span data-stu-id="d2b7d-522">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-df206ad9-1ee2-46d7-9fb4-6e4631c9762f-3"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
#### <a name="353-usernameforsslnegotiated"></a><span data-ttu-id="d2b7d-523">3.5.3 UserNameForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="d2b7d-523">3.5.3 UserNameForSslNegotiated</span></span>  

 <span data-ttu-id="d2b7d-524">在此身份验证模式下，客户端使用“用户名令牌”进行身份验证，该令牌作为签名支持令牌出现在 SOAP 层上。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-524">With this authentication mode the client is authenticates using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="d2b7d-525">使用 X.509 证书对服务进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-525">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="d2b7d-526">所用绑定是对称绑定的一个实例，如上面 3.5.1 中所述。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-526">The binding used is an instance of symmetric binding as described in 3.5.1.</span></span>  
  
 <span data-ttu-id="d2b7d-527">策略</span><span class="sxs-lookup"><span data-stu-id="d2b7d-527">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="UserNameForSslNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><mssp:SslContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient" xmlns:mssp="http://schemas.microsoft.com/ws/2005/07/securitypolicy"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></mssp:SslContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:SignedEncryptedSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:UsernameToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:WssUsernameToken10/></wsp:Policy></sp:UsernameToken></wsp:Policy></sp:SignedEncryptedSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="d2b7d-528">安全标头示例：SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="d2b7d-528">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="d2b7d-529">请求</span><span class="sxs-lookup"><span data-stu-id="d2b7d-529">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-3d1a12c3-e690-474a-a223-a346fc0329a9-4"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-137ea768-7d49-404b-87eb-f11d9c7154aa-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_9" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d2b7d-530">响应</span><span class="sxs-lookup"><span data-stu-id="d2b7d-530">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-137ea768-7d49-404b-87eb-f11d9c7154aa-5"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d2b7d-531">策略</span><span class="sxs-lookup"><span data-stu-id="d2b7d-531">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="UserNameForSslNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><mssp:SslContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient" xmlns:mssp="http://schemas.microsoft.com/ws/2005/07/securitypolicy"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></mssp:SslContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:SignedEncryptedSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:UsernameToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:WssUsernameToken10/></wsp:Policy></sp:UsernameToken></wsp:Policy></sp:SignedEncryptedSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="d2b7d-532">安全标头示例：EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="d2b7d-532">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="d2b7d-533">请求</span><span class="sxs-lookup"><span data-stu-id="d2b7d-533">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-56e931e8-20c2-457f-a83e-8fcd6b92c258-4"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-83d053cb-03a0-4461-9616-86475cf083c4-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 <span data-ttu-id="d2b7d-534">响应</span><span class="sxs-lookup"><span data-stu-id="d2b7d-534">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-83d053cb-03a0-4461-9616-86475cf083c4-4"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
#### <a name="354-issuedtokenforsslnegotiated"></a><span data-ttu-id="d2b7d-535">3.5.4 IssuedTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="d2b7d-535">3.5.4 IssuedTokenForSslNegotiated</span></span>  

 <span data-ttu-id="d2b7d-536">在此身份验证模式下，客户端不向服务进行身份验证，而是出示一个由 STS 颁发的令牌，并证明掌握了共享密钥。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-536">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="d2b7d-537">颁发的令牌作为认可支持令牌出现在 SOAP 层上。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-537">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="d2b7d-538">使用 X.509 证书对服务进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-538">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="d2b7d-539">所用绑定是对称绑定的一个实例，如上面 3.5.1 中所述。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-539">The binding used is an instance of symmetric binding as described in 3.5.1 above.</span></span>  
  
 <span data-ttu-id="d2b7d-540">策略</span><span class="sxs-lookup"><span data-stu-id="d2b7d-540">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="IssuedTokenForSslNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><mssp:SslContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient" xmlns:mssp="http://schemas.microsoft.com/ws/2005/07/securitypolicy"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></mssp:SslContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:IssuedToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><Issuer xmlns="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><Address xmlns="http://www.w3.org/2005/08/addressing">http://www.w3.org/2005/08/addressing/anonymous</Address><Metadata xmlns="http://www.w3.org/2005/08/addressing"><Metadata xmlns="http://schemas.xmlsoap.org/ws/2004/09/mex" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><wsx:MetadataSection xmlns=""><wsx:MetadataReference><Address xmlns="http://www.w3.org/2005/08/addressing"> ... </Address><Identity xmlns="http://schemas.xmlsoap.org/ws/2006/02/addressingidentity"><Dns> ... </Dns></Identity></wsx:MetadataReference></wsx:MetadataSection></Metadata></Metadata></Issuer><sp:RequestSecurityTokenTemplate><trust:KeyType xmlns:trust="http://docs.oasis-open.org/ws-sx/ws-trust/200512">http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey</trust:KeyType></sp:RequestSecurityTokenTemplate><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireInternalReference/></wsp:Policy></sp:IssuedToken></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/><sp:RequireSignatureConfirmation/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="d2b7d-541">安全标头示例：SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="d2b7d-541">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="d2b7d-542">请求</span><span class="sxs-lookup"><span data-stu-id="d2b7d-542">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-b19fb2e7-8f0c-45c1-b62c-45d6ff6d57e7-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-199509f9-7963-42b7-b340-7598ee261d5a-1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d2b7d-543">响应</span><span class="sxs-lookup"><span data-stu-id="d2b7d-543">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-199509f9-7963-42b7-b340-7598ee261d5a-6"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d2b7d-544">策略</span><span class="sxs-lookup"><span data-stu-id="d2b7d-544">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="IssuedTokenForSslNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><mssp:SslContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient" xmlns:mssp="http://schemas.microsoft.com/ws/2005/07/securitypolicy"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></mssp:SslContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:IssuedToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><Issuer xmlns="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><Address xmlns="http://www.w3.org/2005/08/addressing">http://www.w3.org/2005/08/addressing/anonymous</Address><Metadata xmlns="http://www.w3.org/2005/08/addressing"><Metadata xmlns="http://schemas.xmlsoap.org/ws/2004/09/mex" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><wsx:MetadataSection xmlns=""><wsx:MetadataReference><Address xmlns="http://www.w3.org/2005/08/addressing"> ... </Address><Identity xmlns="http://schemas.xmlsoap.org/ws/2006/02/addressingidentity"><Dns> ... </Dns></Identity></wsx:MetadataReference></wsx:MetadataSection></Metadata></Metadata></Issuer><sp:RequestSecurityTokenTemplate><trust:KeyType xmlns:trust="http://docs.oasis-open.org/ws-sx/ws-trust/200512">http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey</trust:KeyType></sp:RequestSecurityTokenTemplate><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireInternalReference/></wsp:Policy></sp:IssuedToken></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/><sp:RequireSignatureConfirmation/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="d2b7d-545">安全标头示例：EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="d2b7d-545">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="d2b7d-546">请求</span><span class="sxs-lookup"><span data-stu-id="d2b7d-546">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-d75104d5-313e-440f-b112-db8aff57a5fe-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-e668caab-b7e4-4056-ac42-4015ae2a67a6-1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d2b7d-547">响应</span><span class="sxs-lookup"><span data-stu-id="d2b7d-547">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-e668caab-b7e4-4056-ac42-4015ae2a67a6-6"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
#### <a name="355-mutualsslnegotiated"></a><span data-ttu-id="d2b7d-548">3.5.5 MutualSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="d2b7d-548">3.5.5 MutualSslNegotiated</span></span>  

 <span data-ttu-id="d2b7d-549">在此身份验证模式下，客户端和服务都使用 X.509 证书进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-549">With this authentication mode the client and the service authenticate using X.509 certificates.</span></span> <span data-ttu-id="d2b7d-550">所用绑定是对称绑定的一个实例，如上面 3.5.1 中所述。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-550">The binding used is an instance of symmetric binding as described in 3.5.1 above.</span></span>  
  
 <span data-ttu-id="d2b7d-551">策略</span><span class="sxs-lookup"><span data-stu-id="d2b7d-551">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="MutualSslNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><mssp:SslContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient" xmlns:mssp="http://schemas.microsoft.com/ws/2005/07/securitypolicy"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><mssp:RequireClientCertificate/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></mssp:SslContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="d2b7d-552">安全标头示例：SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="d2b7d-552">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="d2b7d-553">请求</span><span class="sxs-lookup"><span data-stu-id="d2b7d-553">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-d1e6037e-8a64-494f-9447-07d3125b81b5-4"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-e4b73625-3011-4f6d-a6f9-4d682e860801-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d2b7d-554">响应</span><span class="sxs-lookup"><span data-stu-id="d2b7d-554">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-e4b73625-3011-4f6d-a6f9-4d682e860801-4"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d2b7d-555">策略</span><span class="sxs-lookup"><span data-stu-id="d2b7d-555">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="MutualSslNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><mssp:SslContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient" xmlns:mssp="http://schemas.microsoft.com/ws/2005/07/securitypolicy"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><mssp:RequireClientCertificate/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></mssp:SslContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="d2b7d-556">安全标头示例：EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="d2b7d-556">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="d2b7d-557">请求</span><span class="sxs-lookup"><span data-stu-id="d2b7d-557">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-c2a6ab10-889a-4ee1-871d-05410c90fc10-4"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-ede0bd89-1f7e-4453-96ed-13e58c7ba8fe-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 <span data-ttu-id="d2b7d-558">响应</span><span class="sxs-lookup"><span data-stu-id="d2b7d-558">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-ede0bd89-1f7e-4453-96ed-13e58c7ba8fe-3"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
### <a name="36-sspinegotiated"></a><span data-ttu-id="d2b7d-559">3.6 SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="d2b7d-559">3.6 SspiNegotiated</span></span>  

 <span data-ttu-id="d2b7d-560">在此身份验证模式下，将使用协商协议来执行客户端和服务器身份验证。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-560">With this authentication mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="d2b7d-561">如果可能，就使用 Kerberos，否则使用 NTLM。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-561">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="d2b7d-562">所用绑定为对称绑定，具有以下属性：</span><span class="sxs-lookup"><span data-stu-id="d2b7d-562">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="d2b7d-563">保护令牌：SpnegoContextToken，包含模式设置为 .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="d2b7d-563">Protection Token: SpnegoContextToken, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="d2b7d-564">令牌保护：False</span><span class="sxs-lookup"><span data-stu-id="d2b7d-564">Token Protection: False</span></span>  
  
 <span data-ttu-id="d2b7d-565">整个标头和正文签名：True</span><span class="sxs-lookup"><span data-stu-id="d2b7d-565">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="d2b7d-566">保护顺序：SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="d2b7d-566">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="d2b7d-567">加密签名：True</span><span class="sxs-lookup"><span data-stu-id="d2b7d-567">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="d2b7d-568">策略</span><span class="sxs-lookup"><span data-stu-id="d2b7d-568">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="SspiNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:SpnegoContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></sp:SpnegoContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="d2b7d-569">安全标头示例：SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="d2b7d-569">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="d2b7d-570">请求</span><span class="sxs-lookup"><span data-stu-id="d2b7d-570">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-9a954fcb-4df2-4610-9800-f542f2b5130a-4"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-554d8cfc-e956-43db-9abb-afcafd024347-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d2b7d-571">响应</span><span class="sxs-lookup"><span data-stu-id="d2b7d-571">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-554d8cfc-e956-43db-9abb-afcafd024347-4"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>
```  
  
 <span data-ttu-id="d2b7d-572">策略</span><span class="sxs-lookup"><span data-stu-id="d2b7d-572">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="SspiNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:SpnegoContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></sp:SpnegoContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="d2b7d-573">安全标头示例：EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="d2b7d-573">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="d2b7d-574">请求</span><span class="sxs-lookup"><span data-stu-id="d2b7d-574">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-f1673773-f9a7-4b43-b13b-405e7dd4a6e3-4"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-e0aabc81-6942-4fe6-81bc-9def184565ea-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 <span data-ttu-id="d2b7d-575">响应</span><span class="sxs-lookup"><span data-stu-id="d2b7d-575">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-e0aabc81-6942-4fe6-81bc-9def184565ea-3"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
### <a name="37-secureconversation"></a><span data-ttu-id="d2b7d-576">3.7 Ws-secureconversation</span><span class="sxs-lookup"><span data-stu-id="d2b7d-576">3.7 SecureConversation</span></span>  

 <span data-ttu-id="d2b7d-577">所用绑定为对称绑定，保护令牌为符合 WS-SecureConversation (WS-SC) 的 SCT。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-577">The binding used is a symmetric binding with the protection token being a SCT per WS-SecureConversation (WS-SC).</span></span> <span data-ttu-id="d2b7d-578">该 SCT 是根据嵌套的绑定使用 WS-Trust (WS-Trust) 或 WS-SecureConversation (WS-SC) 协商的，该嵌套绑定本身是使用协商协议的对称绑定。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-578">The SCT is negotiated using WS-Trust (WS-Trust) or WS-SecureConversation (WS-SC) according to a nested binding, which is itself a symmetric binding that uses a negotiation protocol.</span></span> <span data-ttu-id="d2b7d-579">如果可能，协商协议将使用 Kerberos 来执行客户端和服务器身份验证。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-579">The negotiation protocol will use Kerberos to perform client and server authentication if possible.</span></span> <span data-ttu-id="d2b7d-580">如果无法使用 Kerberos，则退而使用 NTLM。</span><span class="sxs-lookup"><span data-stu-id="d2b7d-580">If Kerberos cannot be used, it will fall back to NTLM.</span></span>  
  
 <span data-ttu-id="d2b7d-581">策略</span><span class="sxs-lookup"><span data-stu-id="d2b7d-581">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="SecureConversation_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:SecureConversationToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireDerivedKeys/><sp:BootstrapPolicy><wsp:Policy><sp:SignedParts xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><sp:Body/><sp:Header Name="To" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="From" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="FaultTo" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="ReplyTo" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="MessageID" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="RelatesTo" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="Action" Namespace="http://www.w3.org/2005/08/addressing"/></sp:SignedParts><sp:EncryptedParts xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><sp:Body/></sp:EncryptedParts><sp:SymmetricBinding xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:SpnegoContextToken sp:IncludeToken="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireDerivedKeys/></wsp:Policy></sp:SpnegoContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust10 xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust10></wsp:Policy></sp:BootstrapPolicy><sp:MustNotSendAmend/></wsp:Policy></sp:SecureConversationToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="d2b7d-582">安全标头示例：SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="d2b7d-582">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="d2b7d-583">请求</span><span class="sxs-lookup"><span data-stu-id="d2b7d-583">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-f01c6159-f159-454d-bd97-bbcc9b8e25d3-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-582920d7-14a7-4adc-8091-e1f92d7d8055-1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d2b7d-584">响应</span><span class="sxs-lookup"><span data-stu-id="d2b7d-584">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-582920d7-14a7-4adc-8091-e1f92d7d8055-6"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d2b7d-585">策略</span><span class="sxs-lookup"><span data-stu-id="d2b7d-585">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="SecureConversation_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:SecureConversationToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireDerivedKeys/><sp:BootstrapPolicy><wsp:Policy><sp:SignedParts xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><sp:Body/><sp:Header Name="To" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="From" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="FaultTo" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="ReplyTo" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="MessageID" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="RelatesTo" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="Action" Namespace="http://www.w3.org/2005/08/addressing"/></sp:SignedParts><sp:EncryptedParts xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><sp:Body/></sp:EncryptedParts><sp:SymmetricBinding xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:SpnegoContextToken sp:IncludeToken="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireDerivedKeys/></wsp:Policy></sp:SpnegoContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust10 xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust10></wsp:Policy></sp:BootstrapPolicy><sp:MustNotSendAmend/></wsp:Policy></sp:SecureConversationToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="d2b7d-586">安全标头示例：EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="d2b7d-586">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="d2b7d-587">请求</span><span class="sxs-lookup"><span data-stu-id="d2b7d-587">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-d57e6342-1c68-4095-a0c1-41979088a944-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-9b22407d-b914-4c41-9105-1cf8cf7c3fe5-1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d2b7d-588">响应</span><span class="sxs-lookup"><span data-stu-id="d2b7d-588">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-9b22407d-b914-4c41-9105-1cf8cf7c3fe5-6"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```
