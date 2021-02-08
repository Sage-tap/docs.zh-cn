---
description: 了解详细信息： NamedPipeConnectionPoolSettings
title: NamedPipeConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 079bccb8-54b5-4436-a43d-5567763f72ce
ms.openlocfilehash: 8d724c7a24f62a8d48797125528eb8a194ece660
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803108"
---
# <a name="namedpipeconnectionpoolsettings"></a>NamedPipeConnectionPoolSettings

NamedPipeConnectionPoolSettings  
  
## <a name="syntax"></a>语法  
  
```csharp
class NamedPipeConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a>方法  

 NamedPipeConnectionPoolSettings 类不定义任何方法。  
  
## <a name="properties"></a>属性  

 NamedPipeConnectionPoolSettings 类具有以下属性：  
  
### <a name="groupname"></a>GroupName  

 数据类型：字符串  
  
 访问类型：只读  
  
 绑定元素使用的连接池的组名。  
  
### <a name="idletimeout"></a>IdleTimeout  

 数据类型：DateTime  
  
 访问类型：只读  
  
 连接在断开前可以空闲的最长时间。  
  
### <a name="maxoutboundconnectionsperendpoint"></a>MaxOutboundConnectionsPerEndpoint  

 数据类型：sint32  
  
 访问类型：只读  
  
 客户端上每个终结点的最大出站连接数。  
  
## <a name="requirements"></a>要求  
  
|MOF|已在 Servicemodel.mof 中声明。|  
|---------|-----------------------------------|  
|命名空间|已在 root\ServiceModel 中定义|  
  
## <a name="see-also"></a>请参阅

- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
