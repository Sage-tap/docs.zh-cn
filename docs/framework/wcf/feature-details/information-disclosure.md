---
description: 了解详细信息：信息泄漏
title: 信息泄露
ms.date: 03/30/2017
ms.assetid: 4064c89f-afa6-444a-aa7e-807ef072131c
ms.openlocfilehash: 420437703fab883698cdd7217efb14c214a1f529
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802848"
---
# <a name="information-disclosure"></a><span data-ttu-id="374ba-103">信息泄露</span><span class="sxs-lookup"><span data-stu-id="374ba-103">Information Disclosure</span></span>

<span data-ttu-id="374ba-104">信息泄露会使攻击者获得有价值的系统相关信息。</span><span class="sxs-lookup"><span data-stu-id="374ba-104">Information disclosure enables an attacker to gain valuable information about a system.</span></span> <span data-ttu-id="374ba-105">因此，应始终考虑到您正在泄露何种信息以及恶意用户是否可能使用这些信息。</span><span class="sxs-lookup"><span data-stu-id="374ba-105">Therefore, always consider what information you are revealing and whether it can be used by a malicious user.</span></span> <span data-ttu-id="374ba-106">下面列出了可能的信息泄露攻击并针对每种攻击提供了缓解措施。</span><span class="sxs-lookup"><span data-stu-id="374ba-106">The following lists possible information disclosure attacks and provides mitigations for each.</span></span>

## <a name="message-security-and-http"></a><span data-ttu-id="374ba-107">消息安全性和 HTTP</span><span class="sxs-lookup"><span data-stu-id="374ba-107">Message Security and HTTP</span></span>

<span data-ttu-id="374ba-108">如果正在 HTTP 传输层上使用消息级安全性，请注意消息级安全性不保护 HTTP 头。</span><span class="sxs-lookup"><span data-stu-id="374ba-108">If you are using message-level security over an HTTP transport layer, be aware that message-level security does not protect HTTP headers.</span></span> <span data-ttu-id="374ba-109">保护 HTTP 头的唯一方式是使用 HTTPS 传输协议而不是 HTTP 传输协议。</span><span class="sxs-lookup"><span data-stu-id="374ba-109">The only way to protect HTTP headers is to use HTTPS transport instead of HTTP.</span></span> <span data-ttu-id="374ba-110">HTTPS 传输协议会导致使用安全套接字层 (SSL) 协议对整个消息（包括 HTTP 头）进行加密。</span><span class="sxs-lookup"><span data-stu-id="374ba-110">HTTPS transport causes the entire message, including the HTTP headers, to be encrypted using the Secure Sockets Layer (SSL) protocol.</span></span>

## <a name="policy-information"></a><span data-ttu-id="374ba-111">策略信息</span><span class="sxs-lookup"><span data-stu-id="374ba-111">Policy Information</span></span>

<span data-ttu-id="374ba-112">保持策略安全是十分重要的，在联合方案中尤其如此 — 在这些方案中，会在策略中公开敏感的已颁发令牌要求或令牌颁发者信息。</span><span class="sxs-lookup"><span data-stu-id="374ba-112">Keeping policy secure is important, especially in federation scenarios where sensitive issued-token requirements or token-issuer information is exposed in policy.</span></span> <span data-ttu-id="374ba-113">在这些情况下，建议保护联合服务的策略终结点，以防止攻击者获取服务的有关信息（如要放置在已颁发令牌中的声明的类型）或是将客户端重定向到恶意的令牌颁发者。</span><span class="sxs-lookup"><span data-stu-id="374ba-113">In these cases, the recommendation is to secure the federated service's policy endpoint to prevent attackers from obtaining information about the service, such as the type of claims to put in the issued token, or redirecting clients to malicious token issuers.</span></span> <span data-ttu-id="374ba-114">例如，攻击者可能通过将联合信任链重新配置为终止于执行中间人攻击的颁发者处，来发现用户名/密码对。</span><span class="sxs-lookup"><span data-stu-id="374ba-114">For example, an attacker could discover user name/password pairs by reconfiguring the federated trust chain to terminate in an issuer that executed a man-in-the-middle attack.</span></span> <span data-ttu-id="374ba-115">此外，还建议通过策略检索来获取绑定的联合客户端验证是否信任所获得的联合信任链中的颁发者。</span><span class="sxs-lookup"><span data-stu-id="374ba-115">It is also recommended that federated clients who obtain their bindings through policy retrieval verify that they trust the issuers in the obtained federated trust chain.</span></span> <span data-ttu-id="374ba-116">有关联合方案的详细信息，请参阅 [联合](federation.md)。</span><span class="sxs-lookup"><span data-stu-id="374ba-116">For more information about federation scenarios, see [Federation](federation.md).</span></span>

## <a name="memory-dumps-can-reveal-claim-information"></a><span data-ttu-id="374ba-117">内存转储可能泄露声明信息</span><span class="sxs-lookup"><span data-stu-id="374ba-117">Memory Dumps Can Reveal Claim Information</span></span>

<span data-ttu-id="374ba-118">当应用程序失败时，日志文件（如由 Dr. Watson 生成的那些日志文件）可能包含声明信息。</span><span class="sxs-lookup"><span data-stu-id="374ba-118">When an application fails, log files, such as those produced by Dr. Watson, can contain the claim information.</span></span> <span data-ttu-id="374ba-119">不应该将这些信息导出到其他实体，如支持团队；否则，包含私有数据的声明信息也会导出。</span><span class="sxs-lookup"><span data-stu-id="374ba-119">This information should not be exported to other entities, such as support teams; otherwise, the claim information that contains private data is also exported.</span></span> <span data-ttu-id="374ba-120">通过避免将日志文件发送到未知实体，可以减轻这一问题带来的威胁。</span><span class="sxs-lookup"><span data-stu-id="374ba-120">You can mitigate this by not sending the log files to unknown entities.</span></span>

## <a name="endpoint-addresses"></a><span data-ttu-id="374ba-121">终结点地址</span><span class="sxs-lookup"><span data-stu-id="374ba-121">Endpoint Addresses</span></span>

<span data-ttu-id="374ba-122">终结点地址包含与终结点通信所需的信息。</span><span class="sxs-lookup"><span data-stu-id="374ba-122">An endpoint address contains the information needed to communicate with an endpoint.</span></span> <span data-ttu-id="374ba-123">SOAP 安全必须在安全协商消息中包含完整地址，这些消息会被交换以便在客户端与服务器之间协商一个对称密钥。</span><span class="sxs-lookup"><span data-stu-id="374ba-123">SOAP security must include the address in full in the security negotiation messages that are exchanged in order to negotiate a symmetric key between a client and a server.</span></span> <span data-ttu-id="374ba-124">因为安全协商是一个引导过程，所以在此过程中无法对地址头进行加密。</span><span class="sxs-lookup"><span data-stu-id="374ba-124">Because security negotiation is a bootstrap process, the address headers cannot be encrypted during this process.</span></span> <span data-ttu-id="374ba-125">因此，地址不应包含任何机密数据；否则，会导致信息泄露攻击。</span><span class="sxs-lookup"><span data-stu-id="374ba-125">Therefore, the address should not contain any confidential data; otherwise, it leads to information disclosure attacks.</span></span>

## <a name="certificates-transferred-unencrypted"></a><span data-ttu-id="374ba-126">未加密传输的证书</span><span class="sxs-lookup"><span data-stu-id="374ba-126">Certificates Transferred Unencrypted</span></span>

<span data-ttu-id="374ba-127">在使用 X.509 证书对客户端进行身份验证时，该证书会以明文形式在 SOAP 标头内传输。</span><span class="sxs-lookup"><span data-stu-id="374ba-127">When you use an X.509 certificate to authenticate a client, the certificate is transferred in the clear, inside the SOAP header.</span></span> <span data-ttu-id="374ba-128">请注意，这可能会泄露个人身份信息 (PII)。</span><span class="sxs-lookup"><span data-stu-id="374ba-128">Be aware of this as a potential personally identifiable information (PII) disclosure.</span></span> <span data-ttu-id="374ba-129">对于 `TransportWithMessageCredential` 模式而言，这不是问题，因为在该模式中使用传输级安全对整个消息进行加密。</span><span class="sxs-lookup"><span data-stu-id="374ba-129">This is not an issue for `TransportWithMessageCredential` mode, where the entire message is encrypted with transport-level security.</span></span>

## <a name="service-references"></a><span data-ttu-id="374ba-130">服务引用</span><span class="sxs-lookup"><span data-stu-id="374ba-130">Service References</span></span>

<span data-ttu-id="374ba-131">服务引用是对另一个服务的引用。</span><span class="sxs-lookup"><span data-stu-id="374ba-131">A service reference is a reference to another service.</span></span> <span data-ttu-id="374ba-132">例如，服务可能会在操作过程中将服务引用传递给客户端。</span><span class="sxs-lookup"><span data-stu-id="374ba-132">For example, a service may pass a service reference to a client in the course of an operation.</span></span> <span data-ttu-id="374ba-133">服务引用还用于 *信任标识验证* 程序，这是一个内部组件，它在向目标公开应用程序数据或凭据等信息之前确保目标主体的标识。</span><span class="sxs-lookup"><span data-stu-id="374ba-133">The service reference is also used with a *trust identity verifier*, an internal component that ensures the identity of the target principal before disclosing information such as application data or credentials to the target.</span></span> <span data-ttu-id="374ba-134">如果远程信任标识无法验证或不正确，则发送方应确保没有泄露任何可能危及自身、应用程序或用户的数据。</span><span class="sxs-lookup"><span data-stu-id="374ba-134">If the remote trust identity cannot be verified or is incorrect, the sender should ensure that no data was disclosed that could compromise itself, the application, or the user.</span></span>

<span data-ttu-id="374ba-135">缓解措施包括：</span><span class="sxs-lookup"><span data-stu-id="374ba-135">Mitigations include the following:</span></span>

- <span data-ttu-id="374ba-136">假定服务引用是值得信任的。</span><span class="sxs-lookup"><span data-stu-id="374ba-136">Service references are assumed to be trustworthy.</span></span> <span data-ttu-id="374ba-137">无论何时传输服务引用实例时都应小心处理，以确保它们没有被篡改。</span><span class="sxs-lookup"><span data-stu-id="374ba-137">Take care whenever transferring service reference instances to ensure that they have not been tampered with.</span></span>

- <span data-ttu-id="374ba-138">某些应用程序可以提供这样一种用户体验，即允许基于服务引用中的数据和经过远程主机证明的信任数据来交互地建立信任。</span><span class="sxs-lookup"><span data-stu-id="374ba-138">Some applications can present a user experience that allows interactive establishment of trust based on data in the service reference and trust data proven by the remote host.</span></span> <span data-ttu-id="374ba-139">WCF 为这样一种功能提供了扩展点，但用户必须实现这些扩展点。</span><span class="sxs-lookup"><span data-stu-id="374ba-139">WCF provides extensibility points for such a facility, but the user must implemented them.</span></span>

## <a name="ntlm"></a><span data-ttu-id="374ba-140">NTLM</span><span class="sxs-lookup"><span data-stu-id="374ba-140">NTLM</span></span>

<span data-ttu-id="374ba-141">默认情况下，在 Windows 域环境中，Windows 身份验证使用 Kerberos 协议对用户进行身份验证和授权。</span><span class="sxs-lookup"><span data-stu-id="374ba-141">By default, in the Windows domain environment, Windows authentication uses the Kerberos protocol to authenticate and authorize users.</span></span> <span data-ttu-id="374ba-142">如果出于某种原因而无法使用 Kerberos 协议，则使用 NT LAN Manager (NTLM) 作为后备方式。</span><span class="sxs-lookup"><span data-stu-id="374ba-142">If the Kerberos protocol cannot be used for some reason, NT LAN Manager (NTLM) is used as a fallback.</span></span> <span data-ttu-id="374ba-143">通过将 <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> 属性设置为 `false`，可以禁用此行为。</span><span class="sxs-lookup"><span data-stu-id="374ba-143">You can disable this behavior by setting the <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> property to `false`.</span></span> <span data-ttu-id="374ba-144">在允许使用 NTLM 时应注意的问题包括：</span><span class="sxs-lookup"><span data-stu-id="374ba-144">Issues to be aware of when allowing NTLM include:</span></span>

- <span data-ttu-id="374ba-145">NTLM 会公开客户端用户名。</span><span class="sxs-lookup"><span data-stu-id="374ba-145">NTLM exposes the client user name.</span></span> <span data-ttu-id="374ba-146">如果用户名需要保密，请将绑定上的 `AllowNTLM` 属性设置为 `false`。</span><span class="sxs-lookup"><span data-stu-id="374ba-146">If the user name needs to be kept confidential, then set the `AllowNTLM` property on the binding to `false`.</span></span>

- <span data-ttu-id="374ba-147">NTLM 不提供服务器身份验证。</span><span class="sxs-lookup"><span data-stu-id="374ba-147">NTLM does not provide server authentication.</span></span> <span data-ttu-id="374ba-148">因此，当您使用 NTLM 作为身份验证协议时，客户端无法确保其正在与正确的服务进行通信。</span><span class="sxs-lookup"><span data-stu-id="374ba-148">Therefore, the client cannot ensure that it is communicating with the right service when you use NTLM as an authentication protocol.</span></span>

### <a name="specifying-client-credentials-or-invalid-identity-forces-ntlm-usage"></a><span data-ttu-id="374ba-149">指定客户端凭据或无效标识会强制使用 NTLM</span><span class="sxs-lookup"><span data-stu-id="374ba-149">Specifying Client Credentials or Invalid Identity Forces NTLM Usage</span></span>

<span data-ttu-id="374ba-150">在创建客户端时，如果指定不带域名的客户端凭据或指定无效的服务器标识，则会导致使用 NTLM 而不是 Kerberos 协议（如果 `AllowNtlm` 属性设置为 `true`）。</span><span class="sxs-lookup"><span data-stu-id="374ba-150">When creating a client, specifying client credentials without a domain name, or specifying an invalid server identity, causes NTLM to be used instead of the Kerberos protocol (if the `AllowNtlm` property is set to `true`).</span></span> <span data-ttu-id="374ba-151">因为 NTLM 不进行服务器身份验证，所以信息可能会泄露。</span><span class="sxs-lookup"><span data-stu-id="374ba-151">Because  NTLM does not do server authentication, information can potentially be disclosed.</span></span>

<span data-ttu-id="374ba-152">例如，可以指定不带域名的 Windows 客户端凭据，如以下 Visual c # 代码中所示。</span><span class="sxs-lookup"><span data-stu-id="374ba-152">For example, it is possible to specify Windows client credentials without a domain name, as shown in the following Visual C# code.</span></span>

```csharp
MyChannelFactory.Credentials.Windows.ClientCredential = new System.Net.NetworkCredential("username", "password");
```

<span data-ttu-id="374ba-153">这段代码未指定域名，因而将使用 NTLM。</span><span class="sxs-lookup"><span data-stu-id="374ba-153">The code does not specify a domain name, and therefore NTLM will be used.</span></span>

<span data-ttu-id="374ba-154">如果指定了域，但使用终结点标识功能指定了无效的服务主体名称，则会使用 NTLM。</span><span class="sxs-lookup"><span data-stu-id="374ba-154">If the domain is specified, but an invalid service principal name is specified using the endpoint identity feature, then NTLM is used.</span></span> <span data-ttu-id="374ba-155">有关如何指定终结点标识的详细信息，请参阅 [服务标识和身份验证](service-identity-and-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="374ba-155">For more information about how endpoint identity is specified, see [Service Identity and Authentication](service-identity-and-authentication.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="374ba-156">请参阅</span><span class="sxs-lookup"><span data-stu-id="374ba-156">See also</span></span>

- [<span data-ttu-id="374ba-157">安全注意事项</span><span class="sxs-lookup"><span data-stu-id="374ba-157">Security Considerations</span></span>](security-considerations-in-wcf.md)
- [<span data-ttu-id="374ba-158">权限提升</span><span class="sxs-lookup"><span data-stu-id="374ba-158">Elevation of Privilege</span></span>](elevation-of-privilege.md)
- [<span data-ttu-id="374ba-159">拒绝服务</span><span class="sxs-lookup"><span data-stu-id="374ba-159">Denial of Service</span></span>](denial-of-service.md)
- [<span data-ttu-id="374ba-160">篡改</span><span class="sxs-lookup"><span data-stu-id="374ba-160">Tampering</span></span>](tampering.md)
- [<span data-ttu-id="374ba-161">不受支持的方案</span><span class="sxs-lookup"><span data-stu-id="374ba-161">Unsupported Scenarios</span></span>](unsupported-scenarios.md)
- [<span data-ttu-id="374ba-162">重播攻击</span><span class="sxs-lookup"><span data-stu-id="374ba-162">Replay Attacks</span></span>](replay-attacks.md)
