---
description: 了解详细信息： SecurityBindingElement
title: SecurityBindingElement
ms.date: 03/30/2017
ms.assetid: ef93b6e6-3524-48a8-94d3-c8837f1872f9
ms.openlocfilehash: bc9a519978a9cccccd80a58abb8d109fa9bc9337
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743806"
---
# <a name="securitybindingelement"></a>SecurityBindingElement

SecurityBindingElement  
  
## <a name="syntax"></a>语法  
  
```csharp
class SecurityBindingElement : BindingElement  
{  
  string DefaultAlgorithmSuite;  
  boolean IncludeTimestamp;  
  string KeyEntropyMode;  
  LocalServiceSecuritySettings LocalServiceSecuritySettings;  
  string MessageSecurityVersion;  
  string SecurityHeaderLayout;  
};  
```  
  
## <a name="methods"></a>方法  

 SecurityBindingElement 类未定义任何方法。  
  
## <a name="properties"></a>属性  

 SecurityBindingElement 类具有下列属性：  
  
### <a name="defaultalgorithmsuite"></a>DefaultAlgorithmSuite  

 数据类型：字符串  
  
 访问类型：只读  
  
 指定要用于绑定的算法。  
  
### <a name="includetimestamp"></a>IncludeTimestamp  

 数据类型：Boolean  
  
 访问类型：只读  
  
 一个布尔值，指定是否每个消息都包含时间戳。  
  
### <a name="keyentropymode"></a>KeyEntropyMode  

 数据类型：字符串  
  
 访问类型：只读  
  
 用于创建密钥的熵的来源。  
  
### <a name="localservicesecuritysettings"></a>LocalServiceSecuritySettings  

 数据类型：LocalServiceSecuritySettings  
  
 访问类型：只读  
  
 本地服务的特定于绑定的安全属性。  
  
### <a name="messagesecurityversion"></a>MessageSecurityVersion  

 数据类型：字符串  
  
 访问类型：只读  
  
 消息安全使用的版本。  
  
### <a name="securityheaderlayout"></a>SecurityHeaderLayout  

 数据类型：字符串  
  
 访问类型：只读  
  
 此绑定的安全标头中的元素顺序。  
  
## <a name="requirements"></a>要求  
  
|MOF|已在 Servicemodel.mof 中声明。|  
|---------|-----------------------------------|  
|命名空间|已在 root\ServiceModel 中定义|  
  
## <a name="see-also"></a>请参阅

- <xref:System.ServiceModel.Channels.SecurityBindingElement>
