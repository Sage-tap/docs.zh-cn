---
description: 了解有关 <peer> 元素的详细 <clientCredentials> 信息
title: <peer> of <clientCredentials> 元素
ms.date: 03/30/2017
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
ms.openlocfilehash: 1ff9386ba51dcf6bab6df71bd345cdaa59f18e3a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683783"
---
# <a name="peer-of-clientcredentials-element"></a>\<peer> of \<clientCredentials> 元素

指定在向对等客户端进行身份验证时使用的凭据。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peer>**  
  
## <a name="syntax"></a>语法  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a>特性和元素  

 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  

 无。  
  
### <a name="child-elements"></a>子元素  
  
|元素|说明|  
|-------------|-----------------|  
|[\<certificate>](certificate-element.md)|指定要用于为对等客户端的消息进行签名和加密的 X.509 证书。 .|  
|[\<peerAuthentication>](peerauthentication-element.md)|指定用于对等客户端的身份验证选项。|  
|[\<messageSenderAuthentication>](messagesenderauthentication-element.md)|指定用于消息发送方的身份验证选项。|  
  
### <a name="parent-elements"></a>父元素  
  
|元素|说明|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|指定用于向服务验证客户端身份的凭据。|  
  
## <a name="remarks"></a>备注  

 此配置元素指定对等节点用于向网格中的其他节点证明它自己的身份的凭据，以及对等节点用于验证其他对等节点的身份的身份验证设置。 有关详细信息，请参阅 [对等通道消息身份验证](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) 和 [保护对等通道应用程序](../../../wcf/feature-details/securing-peer-channel-applications.md)。  
  
## <a name="see-also"></a>请参阅

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [对等网络](../../../wcf/feature-details/peer-to-peer-networking.md)
- [保证客户端的安全](../../../wcf/securing-clients.md)
- [对等通道消息身份验证](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))
- [对等通道自定义身份验证](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))
- [保护对等通道应用程序](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [保护服务和客户端的安全](../../../wcf/feature-details/securing-services-and-clients.md)
