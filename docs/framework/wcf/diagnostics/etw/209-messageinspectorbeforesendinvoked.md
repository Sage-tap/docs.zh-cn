---
description: 了解详细信息： 209-MessageInspectorBeforeSendInvoked
title: 209 - MessageInspectorBeforeSendInvoked
ms.date: 03/30/2017
ms.assetid: 7d710875-fb77-4463-978b-bc86d59d84cd
ms.openlocfilehash: 337ed7d4c62d41d72cb2b4710c9f98f863305aee
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99727997"
---
# <a name="209---messageinspectorbeforesendinvoked"></a>209 - MessageInspectorBeforeSendInvoked

## <a name="properties"></a>属性  
  
|||  
|-|-|  
|ID|209|  
|关键字|疑难解答，ServiceModel|  
|级别|信息|  
|通道|Microsoft-Windows-应用程序服务器-应用程序/分析|  
  
## <a name="description"></a>说明  

 服务模型对消息检查器调用 `BeforeSend` 方法之后，将发出此事件。  
  
## <a name="message"></a>消息  

 调度程序对“%1”类型的 MessageInspector 调用了“BeforeSendRequest”。  
  
## <a name="details"></a>详细信息  
  
|数据项名称|数据项类型|说明|  
|--------------------|--------------------|-----------------|  
|TypeName|`xs:string`|所调用 `MessageInspector` 的类型的 CLR FullName。|  
|HostReference|`xs:string`|对于 Web 承载的服务，此字段唯一标识 Web 层次结构中的服务。 其格式定义为 "网站名称应用程序虚拟路径&#124;服务虚拟路径&#124;ServiceName"。 示例： "Default Web Site//Calculatorapplication&#124;/CalculatorService.svc&#124;CalculatorService"。|  
|应用程序域|`xs:string`|由 AppDomain.CurrentDomain.FriendlyName 返回的字符串。|
