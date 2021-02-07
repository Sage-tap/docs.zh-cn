---
description: 了解详细信息： <dispatcherSynchronization>
title: <dispatcherSynchronization>
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: 93664dec3648ed58df7e3e5c0760f1694c60ba7e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749597"
---
# \<dispatcherSynchronization>
  
指定允许服务进行异步答复的终结点行为。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dispatcherSynchronization>**  
  
## <a name="syntax"></a>语法  
  
```xml  
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean"
                                   maxPendingReceives="Integer" />
```  
  
## <a name="type"></a>类型  
  
`Type`  
  
## <a name="attributes-and-elements"></a>特性和元素  
  
下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性

| 属性               | 说明       |
| ----------------------- | ----------------- |
| asynchronousSendEnabled | 一个布尔值，指定是否启用异步发送行为。 |
| `maxPendingReceives`    | 一个整数，指定可在每个通道上执行的并发接收数。<br /><br /> 仅当已正确配置服务限制行为之后，才能配置此值。 |

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

| 元素 | 说明 |  
| ------- | ----------- |  
| [\<behavior>](behavior-of-endpointbehaviors.md)|指定终结点行为。 |

## <a name="see-also"></a>请参阅

- <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement>
- <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>
