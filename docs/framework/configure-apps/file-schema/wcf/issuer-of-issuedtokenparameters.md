---
description: 了解详细 <issuer> 信息： <issuedTokenParameters>
title: <issuer> 的 <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
ms.openlocfilehash: 7d67583eda22414750631b6dff40f6e6ea8831e4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725644"
---
# <a name="issuer-of-issuedtokenparameters"></a>\<issuer> 的 \<issuedTokenParameters>

指定颁发安全令牌的安全令牌服务 (STS)。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuer>**  
  
## <a name="syntax"></a>语法  
  
```xml  
<issuer address="Uri" />
```  
  
## <a name="attributes-and-elements"></a>特性和元素  

 以下几节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|属性|说明|  
|---------------|-----------------|  
|address|必选字符串。 STS 的 URL。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|说明|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|生成器可以创建的终结点的地址标头的集合。|  
|[\<identity>](identity.md)|在使用颁发的令牌时，指定能够使客户端对服务器进行身份验证的设置。|  
  
### <a name="parent-elements"></a>父元素  
  
|元素|说明|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|指定当前颁发的令牌。|  
  
## <a name="see-also"></a>请参阅

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [服务标识和身份验证](../../../wcf/feature-details/service-identity-and-authentication.md)
- [联合令牌与颁发的令牌](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [使用自定义绑定的安全功能](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [联合令牌与颁发的令牌](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [绑定](../../../wcf/bindings.md)
- [扩展绑定](../../../wcf/extending/extending-bindings.md)
- [自定义绑定](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [如何：使用 SecurityBindingElement 创建自定义绑定](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [自定义绑定安全性](../../../wcf/samples/custom-binding-security.md)
