---
description: 了解详细信息： <extensions> 节
title: <extensions> 区
ms.date: 03/30/2017
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
ms.openlocfilehash: 65b1de76155b1e3fbd8e5f14a5f4a1cb8c180ec1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664686"
---
# <a name="extensions-section"></a>\<extensions> 区

此配置节包含一个扩展集合，这些扩展使用户能够创建扩展的用户定义绑定、行为和其他方面。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<extensions>**  
  
## <a name="syntax"></a>语法  
  
```xml  
<system.serviceModel>
  <extensions>
    <bindingExtensions>
    </bindingExtensions>
    <behaviorExtensions>
    </behaviorExtensions>
    <bindingElementExtensions>
    </bindingElementExtensions>
    <endpointExtensions>
    </endpointExtensions>
  </extensions>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>特性和元素  

 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  

 无。  
  
### <a name="child-elements"></a>子元素  
  
|元素|说明|  
|-------------|-----------------|  
|[\<behaviorExtensions>](behaviorextensions.md)|本节包含子元素，这些子元素指定使用户可以自定义服务或终结点行为的行为扩展。|  
|[\<bindingElementExtensions>](bindingelementextensions.md)|本节为使用计算机或应用程序配置文件中的自定义绑定元素提供支持。|  
|[\<bindingExtensions>](bindingextensions.md)|本节包含子元素，这些子元素指定使用户可以自定义绑定的绑定扩展。|  
|[\<endpointExtensions>](endpointextensions.md)|本节包含元注册标准终结点的子元素。|  
  
### <a name="parent-elements"></a>父元素  
  
|元素|说明|  
|-------------|-----------------|  
|system.ServiceModel|所有 WCF 配置元素的根元素。|
