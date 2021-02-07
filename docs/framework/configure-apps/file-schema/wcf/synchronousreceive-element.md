---
description: 了解详细信息： <synchronousReceive> 元素
title: <synchronousReceive> 元素
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: afcd10b4ad41bd6ff12dbf246f66ef7fac4e759a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682613"
---
# <a name="synchronousreceive-element"></a>\<synchronousReceive> 元素

此配置元素用于指定服务或客户端应用程序中用来接收消息的运行时行为。 它不具有任何属性或子元素。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<synchronousReceive>**  
  
## <a name="syntax"></a>语法  
  
```xml  
<synchronousReceive />
```  
  
## <a name="attributes-and-elements"></a>特性和元素  

 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  

 无。  
  
### <a name="child-elements"></a>子元素  

 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|说明|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|指定终结点行为。|  
  
## <a name="remarks"></a>备注  

 使用此行为可指示通道侦听器使用同步接收，而非默认的异步接受。 Windows Communication Foundation (WCF) 发出一个新线程，以便为每个接受的通道抽取。 如果有许多通道，则可能出现线程溢出的情况。  
  
## <a name="see-also"></a>请参阅

- <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>
- <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
