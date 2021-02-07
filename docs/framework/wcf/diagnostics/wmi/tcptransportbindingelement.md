---
description: 了解详细信息： TcpTransportBindingElement
title: TcpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 33bbc1e5-44e4-4ee3-b7b5-801dc78956e4
ms.openlocfilehash: b52bb2eb4b40648808459f76e068a6f72f9476a4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715140"
---
# <a name="tcptransportbindingelement"></a>TcpTransportBindingElement

TcpTransportBindingElement  
  
## <a name="syntax"></a>语法  
  
```csharp
class TcpTransportBindingElement : ConnectionOrientedTransportBindingElement  
{  
  TcpConnectionPoolSettings ConnectionPoolSettings;  
  sint32 ListenBacklog;  
  boolean PortSharingEnabled;  
  boolean TeredoEnabled;  
};  
```  
  
## <a name="methods"></a>方法  

 TcpTransportBindingElement 类不定义任何方法。  
  
## <a name="properties"></a>属性  

 TcpTransportBindingElement 类具有以下属性：  
  
### <a name="connectionpoolsettings"></a>ConnectionPoolSettings  

 数据类型：TcpConnectionPoolSettings  
  
 访问类型：只读  
  
 连接池设置。  
  
### <a name="listenbacklog"></a>ListenBacklog  

 数据类型：sint32  
  
 访问类型：只读  
  
 可挂起的最大排队连接请求数。  
  
### <a name="portsharingenabled"></a>PortSharingEnabled  

 数据类型：Boolean  
  
 访问类型：只读  
  
 一个布尔值，指定是否为此连接启用 TCP 端口共享。  
  
### <a name="teredoenabled"></a>TeredoEnabled  

 数据类型：Boolean  
  
 访问类型：只读  
  
 一个布尔值，指定是否启用 Teredo（一种用于对防火墙后的客户端进行寻址的技术）。  
  
## <a name="requirements"></a>要求  
  
|MOF|已在 Servicemodel.mof 中声明。|  
|---------|-----------------------------------|  
|命名空间|已在 root\ServiceModel 中定义|  
  
## <a name="see-also"></a>请参阅

- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
