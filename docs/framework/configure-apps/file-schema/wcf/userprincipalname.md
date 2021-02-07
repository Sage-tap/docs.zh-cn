---
description: 了解详细信息： <userPrincipalName>
title: <userPrincipalName>
ms.date: 03/30/2017
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
ms.openlocfilehash: 73ace3d6f3d5cb88f2630a4a2ae319decf420021
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664413"
---
# \<userPrincipalName>

<span data-ttu-id="f0cf3-102">指定要由客户端进行身份验证的服务的用户主体名称 (UPN)。</span><span class="sxs-lookup"><span data-stu-id="f0cf3-102">Specifies the User Principal Name (UPN) of a service to be authenticated by the client.</span></span>  
  
<span data-ttu-id="f0cf3-103">有关设置 UPN 的详细信息，请参阅 [服务标识和身份验证](../../../wcf/feature-details/service-identity-and-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="f0cf3-103">For more information about setting the UPN, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userPrincipalName>**  
  
## <a name="syntax"></a><span data-ttu-id="f0cf3-104">语法</span><span class="sxs-lookup"><span data-stu-id="f0cf3-104">Syntax</span></span>  
  
```xml  
<userPrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f0cf3-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="f0cf3-105">Attributes and Elements</span></span>  

 <span data-ttu-id="f0cf3-106">以下几节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f0cf3-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f0cf3-107">特性</span><span class="sxs-lookup"><span data-stu-id="f0cf3-107">Attributes</span></span>  
  
|<span data-ttu-id="f0cf3-108">属性</span><span class="sxs-lookup"><span data-stu-id="f0cf3-108">Attribute</span></span>|<span data-ttu-id="f0cf3-109">说明</span><span class="sxs-lookup"><span data-stu-id="f0cf3-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f0cf3-110">value</span><span class="sxs-lookup"><span data-stu-id="f0cf3-110">value</span></span>|<span data-ttu-id="f0cf3-111">一个用户帐户名（有时称为“用户登录名”）和一个域名（标识用户帐户所在的域）。</span><span class="sxs-lookup"><span data-stu-id="f0cf3-111">A user account name (sometimes referred to as the user logon name) and a domain name identifying the domain in which the user account is located.</span></span> <span data-ttu-id="f0cf3-112">这是登录到 Windows 域的标准用法。</span><span class="sxs-lookup"><span data-stu-id="f0cf3-112">This is the standard usage for logging on to a Windows domain.</span></span> <span data-ttu-id="f0cf3-113">格式为： someone@example.com () 电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="f0cf3-113">The format is: someone@example.com (as for an email address).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f0cf3-114">子元素</span><span class="sxs-lookup"><span data-stu-id="f0cf3-114">Child Elements</span></span>  

 <span data-ttu-id="f0cf3-115">无。</span><span class="sxs-lookup"><span data-stu-id="f0cf3-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f0cf3-116">父元素</span><span class="sxs-lookup"><span data-stu-id="f0cf3-116">Parent Elements</span></span>  
  
|<span data-ttu-id="f0cf3-117">元素</span><span class="sxs-lookup"><span data-stu-id="f0cf3-117">Element</span></span>|<span data-ttu-id="f0cf3-118">说明</span><span class="sxs-lookup"><span data-stu-id="f0cf3-118">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="f0cf3-119">指定要由客户端进行身份验证的服务的标识。</span><span class="sxs-lookup"><span data-stu-id="f0cf3-119">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0cf3-120">备注</span><span class="sxs-lookup"><span data-stu-id="f0cf3-120">Remarks</span></span>  

 <span data-ttu-id="f0cf3-121">使用此标识连接到终结点的安全 Windows Communication Foundation (WCF) 客户端使用 UPN 在对终结点进行 SSPI 身份验证时使用 UPN。</span><span class="sxs-lookup"><span data-stu-id="f0cf3-121">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the UPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0cf3-122">示例</span><span class="sxs-lookup"><span data-stu-id="f0cf3-122">Example</span></span>  

 <span data-ttu-id="f0cf3-123">下面的配置代码指定要由客户端进行身份验证的服务的 UPN。</span><span class="sxs-lookup"><span data-stu-id="f0cf3-123">The following configuration code specifies the UPN of the service to be authenticated by the client.</span></span>  
  
```xml  
<identity>
  <userPrincipalName value="someone@cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="f0cf3-124">请参阅</span><span class="sxs-lookup"><span data-stu-id="f0cf3-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.UpnEndpointIdentity>
- [<span data-ttu-id="f0cf3-125">服务标识和身份验证</span><span class="sxs-lookup"><span data-stu-id="f0cf3-125">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
