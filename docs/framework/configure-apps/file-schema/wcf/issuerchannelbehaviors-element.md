---
description: 了解详细信息： <issuerChannelBehaviors> 元素
title: <issuerChannelBehaviors> 元素
ms.date: 03/30/2017
ms.assetid: f7378673-8e9b-45b2-98d1-cf5dccdd8c40
no-loc:
- <system.serviceModel>
- <behaviors>
- <endpointBehaviors>
- <behavior>
- <clientCredentials>
- <issuedToken>
- <issuerChannelBehaviors>
- <dataContractSerializer>
ms.openlocfilehash: 6be79f2ee6afb442a7a399ce49df4ad59dff2db5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725540"
---
# <a name="issuerchannelbehaviors-element"></a>\:：： no (<issuerChannelBehaviors>) ：：：元素

包含 Windows Communication Foundation (WCF) 客户端终结点行为的集合， (在与指定的服务令牌服务通信时要使用的配置) 中定义。 定义的行为不能包含任何[ \: ：： no (<clientCredentials>) ：：](clientcredentials.md) ：元素。

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\:：： no ( # B0>) ：：：](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\:：： no (<behaviors>) ：：：](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\:：： no (<endpointBehaviors>) ：：：](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\:：： no (<behavior>) ：：：](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\:：： no (<clientCredentials>) ：：：](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\:：： no (<issuedToken>) ：：：](issuedtoken.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\:：： no (<issuerChannelBehaviors>) ：：：

## <a name="syntax"></a>语法

```xml
<issuerChannelBehaviors>
  <add behaviorConfiguration="string"
       issuerAddress="string" />
</issuerChannelBehaviors>
```

## <a name="attributes-and-elements"></a>特性和元素

下列各节描述了特性、子元素和父元素。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

|元素|说明|
|-------------|-----------------|
|[\<add>](add-of-issuerchannelbehaviors.md)|向集合中添加行为。|

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[\:：： no (<issuedToken>) ：：：](issuedtoken.md)|指定用于向服务验证客户端身份的自定义令牌。|

## <a name="remarks"></a>备注

当必须使用任何行为（包含 `<clientCredentials>` 元素的行为除外）与某个服务进行通信时，应使用此元素。 例如，如果必须包含[ \: ：： no (<dataContractSerializer>) ：：](datacontractserializer-element.md) ：行为元素。

## <a name="see-also"></a>请参阅

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [服务标识和身份验证](../../../wcf/feature-details/service-identity-and-authentication.md)
- [安全行为](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [联合令牌与颁发的令牌](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [保护服务和客户端的安全](../../../wcf/feature-details/securing-services-and-clients.md)
- [保证客户端的安全](../../../wcf/securing-clients.md)
- [如何：创建联合客户端](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [如何：配置本地颁发者](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [联合令牌与颁发的令牌](../../../wcf/feature-details/federation-and-issued-tokens.md)
