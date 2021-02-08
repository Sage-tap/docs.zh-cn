---
description: 了解详细信息： <rsa>
title: <rsa>
ms.date: 03/30/2017
ms.assetid: ae1f2267-e40d-42ff-8abf-06ab7067bdb9
ms.openlocfilehash: 5e558e608ec1196081166d01415e12fb2c3083b0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786871"
---
# \<rsa>

<span data-ttu-id="26756-102">通过此标识连接到终结点的安全 WCF 客户端将验证在服务器提供的众多声明中是否具有一个包含用于构建此标识的 RSA 公钥的声明。</span><span class="sxs-lookup"><span data-stu-id="26756-102">A secure WCF client that connects to an endpoint with this identity verifies that the claims presented by the server contain a claim that contains the RSA public key used to construct this identity.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<rsa>**  
  
## <a name="syntax"></a><span data-ttu-id="26756-103">语法</span><span class="sxs-lookup"><span data-stu-id="26756-103">Syntax</span></span>  
  
```xml  
<rsa value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="26756-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="26756-104">Attributes and Elements</span></span>  

 <span data-ttu-id="26756-105">以下几节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="26756-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="26756-106">特性</span><span class="sxs-lookup"><span data-stu-id="26756-106">Attributes</span></span>  
  
|<span data-ttu-id="26756-107">属性</span><span class="sxs-lookup"><span data-stu-id="26756-107">Attribute</span></span>|<span data-ttu-id="26756-108">说明</span><span class="sxs-lookup"><span data-stu-id="26756-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="26756-109">value</span><span class="sxs-lookup"><span data-stu-id="26756-109">value</span></span>|<span data-ttu-id="26756-110">可选的字符串。</span><span class="sxs-lookup"><span data-stu-id="26756-110">Optional String.</span></span> <span data-ttu-id="26756-111">客户端上要进行比较的 RSA 公钥值。</span><span class="sxs-lookup"><span data-stu-id="26756-111">The RSA public key value to be compared with on the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="26756-112">子元素</span><span class="sxs-lookup"><span data-stu-id="26756-112">Child Elements</span></span>  

 <span data-ttu-id="26756-113">无</span><span class="sxs-lookup"><span data-stu-id="26756-113">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="26756-114">父元素</span><span class="sxs-lookup"><span data-stu-id="26756-114">Parent Elements</span></span>  
  
|<span data-ttu-id="26756-115">元素</span><span class="sxs-lookup"><span data-stu-id="26756-115">Element</span></span>|<span data-ttu-id="26756-116">说明</span><span class="sxs-lookup"><span data-stu-id="26756-116">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="26756-117">指定要由客户端进行身份验证的服务的标识。</span><span class="sxs-lookup"><span data-stu-id="26756-117">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26756-118">备注</span><span class="sxs-lookup"><span data-stu-id="26756-118">Remarks</span></span>  

 <span data-ttu-id="26756-119">您可以通过 RSA 检查将身份验证明确限制为单个基于其 RSA 密钥或生成的个人的 RSA 密钥值的证书。</span><span class="sxs-lookup"><span data-stu-id="26756-119">A RSA check enables you to specifically restrict authentication to a single certificate based upon its RSA key or generated your own RSA key value.</span></span> <span data-ttu-id="26756-120">这样将启用更为严格的特定 RSA 密钥身份验证，不过与此对应的代价是，如果更改 RSA 密钥值，则该服务不可再用于现有客户端。</span><span class="sxs-lookup"><span data-stu-id="26756-120">This enables stricter authentication of a specific RSA key at the expense of the service no longer working with existing clients if the RSA key value is changed.</span></span>  
  
 <span data-ttu-id="26756-121">有关使用标识向客户端验证服务的详细信息，请参阅 [服务标识和身份验证](../../../wcf/feature-details/service-identity-and-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="26756-121">For more information about using identity to validate a service to a client, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="26756-122">示例</span><span class="sxs-lookup"><span data-stu-id="26756-122">Example</span></span>  

 <span data-ttu-id="26756-123">下面的配置代码指定用于对服务器进行身份验证的 X.509 证书的公钥值。</span><span class="sxs-lookup"><span data-stu-id="26756-123">The following configuration code specifies the public key value of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <rsa value="0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="26756-124">请参阅</span><span class="sxs-lookup"><span data-stu-id="26756-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.RsaEndpointIdentity>
- [<span data-ttu-id="26756-125">服务标识和身份验证</span><span class="sxs-lookup"><span data-stu-id="26756-125">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
