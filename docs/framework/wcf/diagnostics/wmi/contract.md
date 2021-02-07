---
description: 了解详细信息：协定
title: 协定
ms.date: 03/30/2017
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
ms.openlocfilehash: 3443a7d2eed1a34f07495bd3ceb98c1ba997fabf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757548"
---
# <a name="contract"></a>协定

协定  
  
## <a name="syntax"></a>语法  
  
```csharp
class Contract  
{  
  sint32 AppDomainId;  
  Behavior Behaviors[];  
  string Name;  
  string Namespace;  
  Operation Operations[];  
  sint32 ProcessId;  
  Contract ref;  
  string SessionMode;  
  string Type;  
};  
```  
  
## <a name="methods"></a>方法  

 Contract 类不定义任何方法。  
  
## <a name="properties"></a>属性  

 Contract 类具有下列属性：  
  
### <a name="appdomainid"></a>AppDomainId  

 数据类型：sint32  
  
 访问类型：只读  
  
 承载协定的 appdomain 的 appdomain ID。  
  
### <a name="behaviors"></a>行为  

 数据类型：Behavior array  
  
 访问类型：只读  
  
 与此协定关联的行为。  
  
### <a name="name"></a>名称  

 数据类型：字符串  
  
 访问类型：只读  
  
 WSDL 中协定的名称。  
  
### <a name="namespace"></a>命名空间  

 数据类型：字符串  
  
 访问类型：只读  
  
 WSDL 中 `portType` 元素的命名空间。  
  
### <a name="operations"></a>操作  

 数据类型：操作数组  
  
 访问类型：只读  
  
 此协定的操作。  
  
### <a name="processid"></a>ProcessId  

 数据类型：sint32  
  
 访问类型：只读  
  
 承载此协定的进程的进程 ID。  
  
### <a name="ref"></a>ref  

 数据类型：Contract  
  
 访问类型：只读  
  
 协定为双工协定时的回调类型。  
  
### <a name="sessionmode"></a>SessionMode  

 数据类型：字符串  
  
 访问类型：只读  
  
 指示协定是否要求与此协定关联的绑定来使用通道会话。  
  
### <a name="type"></a>类型  

 数据类型：字符串  
  
 访问类型：只读  
  
 协定的类型。  
  
## <a name="requirements"></a>要求  
  
|MOF|已在 Servicemodel.mof 中声明。|  
|---------|-----------------------------------|  
|命名空间|已在 root\ServiceModel 中定义|  
  
## <a name="see-also"></a>请参阅

- <xref:System.ServiceModel.Description.ContractDescription>
