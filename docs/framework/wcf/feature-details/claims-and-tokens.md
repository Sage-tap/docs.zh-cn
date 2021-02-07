---
description: 了解详细信息：声明和标记
title: 声明和令牌
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], and tokens
ms.assetid: eff167f3-33f8-483d-a950-aa3e9f97a189
ms.openlocfilehash: d7d05fb63886ca7562ce478bcbcea73c3cbafcb8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734953"
---
# <a name="claims-and-tokens"></a><span data-ttu-id="59461-103">声明和令牌</span><span class="sxs-lookup"><span data-stu-id="59461-103">Claims and Tokens</span></span>

<span data-ttu-id="59461-104">本主题介绍 Windows Communication Foundation (WCF) 从其支持的默认令牌创建的各种声明类型。</span><span class="sxs-lookup"><span data-stu-id="59461-104">This topic describes the various claim types that Windows Communication Foundation (WCF) creates from the default tokens that it supports.</span></span>

<span data-ttu-id="59461-105">可以使用 <xref:System.IdentityModel.Claims.ClaimSet> 和 <xref:System.IdentityModel.Claims.Claim> 类来检查客户端凭据的声明。</span><span class="sxs-lookup"><span data-stu-id="59461-105">You can examine the claims of a client credential by using the <xref:System.IdentityModel.Claims.ClaimSet> and <xref:System.IdentityModel.Claims.Claim> classes.</span></span> <span data-ttu-id="59461-106">`ClaimSet` 包含 `Claim` 对象的集合。</span><span class="sxs-lookup"><span data-stu-id="59461-106">The `ClaimSet` contains a collection of `Claim` objects.</span></span> <span data-ttu-id="59461-107">每个 `Claim` 都具有以下重要成员：</span><span class="sxs-lookup"><span data-stu-id="59461-107">Each `Claim` has the following important members:</span></span>

- <span data-ttu-id="59461-108"><xref:System.IdentityModel.Claims.Claim.ClaimType%2A> 属性返回的统一资源标识符 (URI) 指定了所做声明的类型。</span><span class="sxs-lookup"><span data-stu-id="59461-108">The <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> property returns a Uniform Resource Identifier (URI) that specifies the type of claim being made.</span></span> <span data-ttu-id="59461-109">例如，声明类型可以是证书的指纹，在这种情况下，URI 是 `http://schemas.microsoft.com/ws/20005/05/identity/claims/thumprint` 。</span><span class="sxs-lookup"><span data-stu-id="59461-109">For example, a claim type may be a thumbprint of a certificate, in which case the URI is `http://schemas.microsoft.com/ws/20005/05/identity/claims/thumprint`.</span></span>

- <span data-ttu-id="59461-110"><xref:System.IdentityModel.Claims.Claim.Right%2A> 属性返回的 URI 指定了声明权限。</span><span class="sxs-lookup"><span data-stu-id="59461-110">The <xref:System.IdentityModel.Claims.Claim.Right%2A> property returns a URI that specifies the right of the claim.</span></span> <span data-ttu-id="59461-111">预定义的权限位于 <xref:System.IdentityModel.Claims.Rights> 类中（<xref:System.IdentityModel.Claims.Rights.Identity%2A>、<xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>）。</span><span class="sxs-lookup"><span data-stu-id="59461-111">Predefined rights are found in the <xref:System.IdentityModel.Claims.Rights> class (<xref:System.IdentityModel.Claims.Rights.Identity%2A>,  <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>).</span></span>

- <span data-ttu-id="59461-112"><xref:System.IdentityModel.Claims.Claim.Resource%2A> 属性返回与声明关联的资源。</span><span class="sxs-lookup"><span data-stu-id="59461-112">The <xref:System.IdentityModel.Claims.Claim.Resource%2A> property returns the resource associated with the claim.</span></span>

<span data-ttu-id="59461-113">此外，每个 <xref:System.IdentityModel.Claims.ClaimSet> 还包含一个 <xref:System.IdentityModel.Claims.ClaimSet.Issuer%2A> 属性，以表示 <xref:System.IdentityModel.Claims.ClaimSet> 的 `Issuer`。</span><span class="sxs-lookup"><span data-stu-id="59461-113">Each <xref:System.IdentityModel.Claims.ClaimSet> also has an <xref:System.IdentityModel.Claims.ClaimSet.Issuer%2A> property, which represents the <xref:System.IdentityModel.Claims.ClaimSet> of the `Issuer`.</span></span>

## <a name="windows-accounts"></a><span data-ttu-id="59461-114">Windows 帐户</span><span class="sxs-lookup"><span data-stu-id="59461-114">Windows Accounts</span></span>

<span data-ttu-id="59461-115">在客户端凭据映射到 Windows 用户帐户的情况下，生成的 <xref:System.IdentityModel.Claims.ClaimSet> 具有以下值：</span><span class="sxs-lookup"><span data-stu-id="59461-115">Where a client credential maps to a Windows user account, the resulting <xref:System.IdentityModel.Claims.ClaimSet> has the following values:</span></span>

- <span data-ttu-id="59461-116">`Issuer` 是 <xref:System.IdentityModel.Claims.ClaimSet> 类的静态 Windows 属性返回的值。</span><span class="sxs-lookup"><span data-stu-id="59461-116">The `Issuer` is the value returned by the static Windows property of the <xref:System.IdentityModel.Claims.ClaimSet> class.</span></span>

- <span data-ttu-id="59461-117">集合中的声明包括：</span><span class="sxs-lookup"><span data-stu-id="59461-117">The claims in the collection are:</span></span>

  - <span data-ttu-id="59461-118"><xref:System.IdentityModel.Claims.Claim> 值为安全标识符 (SID)、<xref:System.IdentityModel.Claims.Claim.ClaimType%2A> 属性值为 <xref:System.IdentityModel.Claims.Claim.Right%2A> 以及返回实际 SID 值的 `Identity` 的 <xref:System.IdentityModel.Claims.Claim.Resource%2A>。</span><span class="sxs-lookup"><span data-stu-id="59461-118">A <xref:System.IdentityModel.Claims.Claim> with a <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> value of security identifier (SID), a <xref:System.IdentityModel.Claims.Claim.Right%2A> property value of `Identity`, and a <xref:System.IdentityModel.Claims.Claim.Resource%2A> that returns the actual SID value.</span></span> <span data-ttu-id="59461-119">SID 是域控制器颁发给每个用户的一个唯一值。</span><span class="sxs-lookup"><span data-stu-id="59461-119">A SID is a unique value the domain controller issues to every user.</span></span> <span data-ttu-id="59461-120">SID 用于在与 Windows 安全交互时标识用户。</span><span class="sxs-lookup"><span data-stu-id="59461-120">The SID is used to identify the user in interactions with Windows security.</span></span>

  - <span data-ttu-id="59461-121"><xref:System.IdentityModel.Claims.Claim> 值为 SID、<xref:System.IdentityModel.Claims.Claim.ClaimType%2A> 为 <xref:System.IdentityModel.Claims.Claim.Right%2A> 以及 `PossessProperty` 为 SID 值的 <xref:System.IdentityModel.Claims.Claim.Resource%2A>。</span><span class="sxs-lookup"><span data-stu-id="59461-121">A <xref:System.IdentityModel.Claims.Claim> with a <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> value of SID, a <xref:System.IdentityModel.Claims.Claim.Right%2A> of `PossessProperty`, and a <xref:System.IdentityModel.Claims.Claim.Resource%2A> of the SID value.</span></span>

  - <span data-ttu-id="59461-122"><xref:System.IdentityModel.Claims.Claim> 为 <xref:System.IdentityModel.Claims.Claim.ClaimType%2A>、<xref:System.IdentityModel.Claims.ClaimTypes.Name%2A> 为 <xref:System.IdentityModel.Claims.Claim.Right%2A> 以及 `PossessProperty` 为包含用户名的字符串（如“MYMACHINE\Bob”）的 <xref:System.IdentityModel.Claims.Claim.Resource%2A>。</span><span class="sxs-lookup"><span data-stu-id="59461-122">A <xref:System.IdentityModel.Claims.Claim> with a <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> of <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, a <xref:System.IdentityModel.Claims.Claim.Right%2A> of `PossessProperty` and a <xref:System.IdentityModel.Claims.Claim.Resource%2A> of string containing the user name (for example, "MYMACHINE\Bob").</span></span>

  - <span data-ttu-id="59461-123">用户所属的各个组的 <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> 的附加 SID 声明。</span><span class="sxs-lookup"><span data-stu-id="59461-123">Additional SID claims with <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> for the various groups the user belongs to.</span></span>

## <a name="certificates"></a><span data-ttu-id="59461-124">证书</span><span class="sxs-lookup"><span data-stu-id="59461-124">Certificates</span></span>

<span data-ttu-id="59461-125">在客户端凭据为证书的情况下，生成的 <xref:System.IdentityModel.Claims.ClaimSet> 具有以下各值：</span><span class="sxs-lookup"><span data-stu-id="59461-125">Where the client credential is a certificate, the resulting <xref:System.IdentityModel.Claims.ClaimSet> has the following values:</span></span>

- <span data-ttu-id="59461-126">对于自行颁发的证书，`Issuer` 为 <xref:System.IdentityModel.Claims.ClaimSet> 本身。</span><span class="sxs-lookup"><span data-stu-id="59461-126">For self-issued certificates, the `Issuer` is the <xref:System.IdentityModel.Claims.ClaimSet> itself.</span></span> <span data-ttu-id="59461-127"><xref:System.IdentityModel.Claims.ClaimSet> 返回 <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> 的 <xref:System.IdentityModel.Claims.ClaimTypes.Thumbprint%2A>、<xref:System.IdentityModel.Claims.Claim.Right%2A> 的 `Identity` 以及 <xref:System.IdentityModel.Claims.Claim.Resource%2A> 值，该值是一个包含证书指纹的 <xref:System.Byte> 数组。</span><span class="sxs-lookup"><span data-stu-id="59461-127">The <xref:System.IdentityModel.Claims.ClaimSet> returns a <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> of <xref:System.IdentityModel.Claims.ClaimTypes.Thumbprint%2A>, a <xref:System.IdentityModel.Claims.Claim.Right%2A> of `Identity`, and a <xref:System.IdentityModel.Claims.Claim.Resource%2A> value that is a <xref:System.Byte> array containing the thumbprint of the certificate.</span></span>

- <span data-ttu-id="59461-128">对于证书颁发机构颁发的证书，颁发者为表示证书颁发机构的证书的 `ClaimSet`。</span><span class="sxs-lookup"><span data-stu-id="59461-128">For a certificate issued by a certification authority, the issuer is the `ClaimSet` representing the certification authority’s certificate.</span></span>

- <span data-ttu-id="59461-129">集合中的 `Claims` 包括：</span><span class="sxs-lookup"><span data-stu-id="59461-129">The `Claims` in the collection include:</span></span>

  - <span data-ttu-id="59461-130">`Claim` 为 Thumbprint、`ClaimType` 为 PossessProperty 以及 `Right` 为包含证书指纹的字节数组的 `Resource`</span><span class="sxs-lookup"><span data-stu-id="59461-130">A `Claim` with a `ClaimType` of Thumbprint, a `Right` of PossessProperty, and a `Resource` that is a byte array containing the thumbprint of the certificate</span></span>

  - <span data-ttu-id="59461-131">各种类型的其他 PossessProperty 声明，包括表示各种证书属性的 X500DistinguishedName、Dns、Name、Upn 和 Rsa。</span><span class="sxs-lookup"><span data-stu-id="59461-131">Additional PossessProperty claims of various types, including X500DistinguishedName, Dns, Name, Upn, and Rsa, represent various properties of the certificate.</span></span> <span data-ttu-id="59461-132">Rsa 声明的资源是与证书关联的公钥。**注意** 如果客户端凭据类型是服务将映射到 Windows 帐户的证书，则 `ClaimSet` 会生成两个对象。</span><span class="sxs-lookup"><span data-stu-id="59461-132">The resource for the Rsa claim is the public key associated with the certificate.**Note** Where the client credential type is a certificate that the service maps to a Windows account, two `ClaimSet` objects are generated.</span></span> <span data-ttu-id="59461-133">第一个对象包含与 Windows 帐户相关的所有声明，第二个对象包含与证书相关的所有声明。</span><span class="sxs-lookup"><span data-stu-id="59461-133">The first contains all the claims related to the Windows account and the second contains all the claims related to the certificate.</span></span>

## <a name="user-namepassword"></a><span data-ttu-id="59461-134">用户名/密码</span><span class="sxs-lookup"><span data-stu-id="59461-134">User Name/Password</span></span>

<span data-ttu-id="59461-135">在客户端凭据是未映射到 Windows 帐户的用户名/密码（或等效项）的情况下，生成的 `ClaimSet` 由 <xref:System.IdentityModel.Claims.ClaimSet.System%2A> 类的静态 `ClaimSet` 属性颁发。</span><span class="sxs-lookup"><span data-stu-id="59461-135">Where the client credential is a user name/password (or equivalent) that does not map to a Windows account, the resulting `ClaimSet` is issued by the static <xref:System.IdentityModel.Claims.ClaimSet.System%2A> property of the `ClaimSet` class.</span></span> <span data-ttu-id="59461-136">`ClaimSet`包含类型的 `Identity` 声明， <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A> 其资源是客户端提供的用户名。</span><span class="sxs-lookup"><span data-stu-id="59461-136">The `ClaimSet` contains an `Identity` claim of type <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A> whose resource is the user name the client provides.</span></span> <span data-ttu-id="59461-137">对应声明的 `Right` 为 `PossessProperty`。</span><span class="sxs-lookup"><span data-stu-id="59461-137">A corresponding claim has a `Right` of `PossessProperty`.</span></span>

## <a name="rsa-keys"></a><span data-ttu-id="59461-138">RSA 密钥</span><span class="sxs-lookup"><span data-stu-id="59461-138">RSA Keys</span></span>

<span data-ttu-id="59461-139">如果使用不与证书关联的 RSA 密钥，则生成的 `ClaimSet` 是自行颁发的，并且包含 `Identity` 类型的声明， <xref:System.IdentityModel.Claims.ClaimTypes.Rsa%2A> 其资源为 RSA 密钥。</span><span class="sxs-lookup"><span data-stu-id="59461-139">Where an RSA key not associated with a certificate is used, the resulting `ClaimSet` is self-issued and contains an `Identity` claim of type <xref:System.IdentityModel.Claims.ClaimTypes.Rsa%2A> whose resource is the RSA key.</span></span> <span data-ttu-id="59461-140">对应声明的 `Right` 为 `PossessProperty`。</span><span class="sxs-lookup"><span data-stu-id="59461-140">A corresponding claim has a `Right` of `PossessProperty`.</span></span>

## <a name="saml"></a><span data-ttu-id="59461-141">SAML</span><span class="sxs-lookup"><span data-stu-id="59461-141">SAML</span></span>

<span data-ttu-id="59461-142">在客户端使用安全断言标记语言 (SAML) 令牌进行身份验证的情况下，生成的 `ClaimSet` 由已对 SAML 令牌进行签名的实体来颁发，通常为颁发了 SAML 令牌的安全令牌服务 (STS) 的证书。</span><span class="sxs-lookup"><span data-stu-id="59461-142">Where the client authenticates with a Security Assertions Markup Language (SAML) token, the resulting `ClaimSet` is issued by the entity that signed the SAML token, often the certificate of the security token service (STS) that issued the SAML token.</span></span> <span data-ttu-id="59461-143">`ClaimSet` 中包含 SAML 令牌中的各种声明。</span><span class="sxs-lookup"><span data-stu-id="59461-143">The `ClaimSet` contains various claims as found in the SAML token.</span></span> <span data-ttu-id="59461-144">如果 SAML 令牌包含非 `SamlSubject` 名称的 `null`，则会创建一个类型为 `Identity`、资源类型为 <xref:System.IdentityModel.Claims.ClaimTypes.NameIdentifier%2A> 的 <xref:System.IdentityModel.Tokens.SamlNameIdentifierClaimResource> 声明。</span><span class="sxs-lookup"><span data-stu-id="59461-144">If the SAML token contains a `SamlSubject` with a non-`null` name, then an `Identity` claim with a type of <xref:System.IdentityModel.Claims.ClaimTypes.NameIdentifier%2A> and a resource type of <xref:System.IdentityModel.Tokens.SamlNameIdentifierClaimResource> are created.</span></span>

## <a name="identity-claims-and-servicesecuritycontextisanonymous"></a><span data-ttu-id="59461-145">标识声明和 ServiceSecurityContext.IsAnonymous</span><span class="sxs-lookup"><span data-stu-id="59461-145">Identity Claims and ServiceSecurityContext.IsAnonymous</span></span>

<span data-ttu-id="59461-146">如果 `ClaimSet` 客户端凭据生成的任何对象都不包含包含的声明， `Right` `Identity,` 则属性将 <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> 返回 `true` 。</span><span class="sxs-lookup"><span data-stu-id="59461-146">If none of the `ClaimSet` objects resulting from the client credentials contain a claim with a `Right` of `Identity,` then the <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> property returns `true`.</span></span> <span data-ttu-id="59461-147">如果存在一个或多个此类声明，则 `IsAnonymous` 属性将返回 `false`。</span><span class="sxs-lookup"><span data-stu-id="59461-147">If one or more such claims are present, the `IsAnonymous` property returns `false`.</span></span>

## <a name="see-also"></a><span data-ttu-id="59461-148">请参阅</span><span class="sxs-lookup"><span data-stu-id="59461-148">See also</span></span>

- <xref:System.IdentityModel.Claims.ClaimSet>
- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.Rights>
- <xref:System.IdentityModel.Claims.ClaimTypes>
- [<span data-ttu-id="59461-149">使用标识模型管理声明和授权</span><span class="sxs-lookup"><span data-stu-id="59461-149">Managing Claims and Authorization with the Identity Model</span></span>](managing-claims-and-authorization-with-the-identity-model.md)
