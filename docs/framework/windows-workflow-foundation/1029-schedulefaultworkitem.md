---
description: 了解详细信息： 1029-ScheduleFaultWorkItem
title: 1029 - ScheduleFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 3a56b29e-f740-459d-8576-d81e58bf5a03
ms.openlocfilehash: e5f0463626882d6c8c48412326582fafa7be4670
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755442"
---
# <a name="1029---schedulefaultworkitem"></a>1029 - ScheduleFaultWorkItem

## <a name="properties"></a>属性  
  
|||  
|-|-|  
|ID|1029|  
|关键字|WFRuntime|  
|级别|“详细”|  
|通道|Microsoft-Windows-应用程序服务器-应用程序/调试|  
  
## <a name="description"></a>说明  

 指示已安排 FaultWorkItem。  
  
## <a name="message"></a>消息  

 已为 Activity "%1"、DisplayName "%2"、InstanceId "%3" 安排了 FaultWorkItem。  异常是从 Activity“%4”、DisplayName“%5”、InstanceId“%6”传播的。  
  
## <a name="details"></a>详细信息  
  
|数据项名称|数据项类型|说明|  
|--------------------|--------------------|-----------------|  
|FaultActivity|xs:string|错误活动的类型名称。|  
|FaultActivityDisplayName|xs:string|错误活动的显示名称。|  
|FaultActivityInstanceId|xs:string|错误活动的实例 ID。|  
|ExceptionActivity|xs:string|引发了异常的活动的类型名称。|  
|ExceptionActivityDisplayName|xs:string|引发了异常的活动的显示名称。|  
|ExceptionActivityInstanceId|xs:string|引发了异常的活动的实例 ID。|  
|异常|xs:string|异常的异常详细信息|  
|应用程序域|xs:string|由 AppDomain.CurrentDomain.FriendlyName 返回的字符串。|
