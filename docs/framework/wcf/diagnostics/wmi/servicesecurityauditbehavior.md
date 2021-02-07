---
description: 了解详细信息： ServiceSecurityAuditBehavior
title: ServiceSecurityAuditBehavior
ms.date: 03/30/2017
ms.assetid: 2c5809e7-5364-44ce-bc71-848be4672e2a
ms.openlocfilehash: 5dfb3a70a80d5dea1ed360dcaf3a0db989bf671b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715465"
---
# <a name="servicesecurityauditbehavior"></a>ServiceSecurityAuditBehavior

ServiceSecurityAuditBehavior  
  
## <a name="syntax"></a>语法  
  
```csharp  
class ServiceSecurityAuditBehavior : Behavior  
{  
  string AuditLogLocation;  
  string MessageAuthenticationAuditLevel;  
  string ServiceAuthorizationAuditLevel;  
  boolean SuppressAuditFailure;  
};  
```  
  
## <a name="methods"></a>方法  

 ServiceSecurityAuditBehavior 类不定义任何方法。  
  
## <a name="properties"></a>属性  

 ServiceSecurityAuditBehavior 类具有下列属性：  
  
### <a name="auditloglocation"></a>AuditLogLocation  

 数据类型：字符串  
  
 访问类型：只读  
  
 审核日志的位置。  
  
### <a name="messageauthenticationauditlevel"></a>MessageAuthenticationAuditLevel  

 数据类型：字符串  
  
 访问类型：只读  
  
 用于记录审核事件的消息身份验证级别的类型。  
  
### <a name="serviceauthorizationauditlevel"></a>ServiceAuthorizationAuditLevel  

 数据类型：字符串  
  
 访问类型：只读  
  
 审核日志中记录的授权事件类型。  
  
### <a name="suppressauditfailure"></a>SuppressAuditFailure  

 数据类型：Boolean  
  
 访问类型：只读  
  
 一个 boolean 值，指定取消显示审核日志写入失败的行为。  
  
## <a name="requirements"></a>要求  
  
|MOF|已在 Servicemodel.mof 中声明。|  
|---------|-----------------------------------|  
|命名空间|已在 root\ServiceModel 中定义|  
  
## <a name="see-also"></a>请参阅

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
