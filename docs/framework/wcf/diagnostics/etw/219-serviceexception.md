---
description: 了解详细信息： 219-ServiceException
title: 219 - ServiceException
ms.date: 03/30/2017
ms.assetid: 81e2efac-39aa-4ed2-85a9-97eb8793b844
ms.openlocfilehash: b2ac12d6c5c68517b085b39dd7d0f81c39db9ebd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794320"
---
# <a name="219---serviceexception"></a>219 - ServiceException

## <a name="properties"></a>属性  
  
|||  
|-|-|  
|ID|219|  
|关键字|EndToEndMonitoring、HealthMonitoring、疑难解答、ServiceModel|  
|级别|错误|  
|通道|Microsoft-Windows-应用程序服务器-应用程序/分析|  
  
## <a name="description"></a>说明  

 当 WCF 服务遇到未经处理的异常时会发出此事件。 这包括在激活和消息处理期间以及在用户代码中出现的未经处理的异常。  
  
## <a name="message"></a>消息  

 消息处理过程中出现了“%2”类型的未经处理的异常。 完整异常 ToString: %1。  
  
## <a name="details"></a>详细信息  
  
|数据项名称|数据项类型|说明|  
|--------------------|--------------------|-----------------|  
|ExceptionToString|`xs:string`|对 CLR 异常调用 `ToString`() 的结果。|  
|ExceptionTypeName|`xs:string`|异常的类型的 CLR FullName。|  
|HostReference|`xs:string`|对于 Web 承载的服务，此字段唯一标识 Web 层次结构中的服务。 其格式定义为 "网站名称应用程序虚拟路径&#124;服务虚拟路径&#124;ServiceName"。 示例： "Default Web Site//Calculatorapplication&#124;/CalculatorService.svc&#124;CalculatorService"。|  
|应用程序域|`xs:string`|由 AppDomain.CurrentDomain.FriendlyName 返回的字符串。|
