---
description: 了解详细信息： Windows Communication Foundation 终结点
title: Windows Communication Foundation 终结点
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
ms.assetid: bd0c310f-dd9f-4081-9be2-3db5909850b6
ms.openlocfilehash: caa918f2dd7ca7b0289cc1faf6d189270596808b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756768"
---
# <a name="windows-communication-foundation-endpoints"></a>Windows Communication Foundation 终结点

与 Windows Communication Foundation (WCF) 服务的所有通信都通过服务 *终结点* 进行。 终结点为客户端提供对 WCF 服务所提供的功能的访问权限。  
  
 有关如何创建终结点的概述，请参阅 [终结点创建概述](endpoint-creation-overview.md)。 每个终结点包含：  
  
- 一个指示要查找终结点位置的地址。  
  
- 一个指定客户端如何与终结点进行通信的绑定。  
  
- 一个标识可用方法的协定。  
  
 有关如何指定终结点的上述各个部分的说明，请参见：  
  
- [指定终结点地址](specifying-an-endpoint-address.md)  
  
- [使用绑定配置服务和客户端](using-bindings-to-configure-services-and-clients.md)  
  
- [设计和实现服务](designing-and-implementing-services.md)  
  
## <a name="in-this-section"></a>本节内容  

 [终结点创建概述](endpoint-creation-overview.md)  
 描述终结点的结构，并概述如何在配置和代码中定义终结点，以及如何使用运行时提供的默认终结点、绑定和行为。  
  
 [指定终结点地址](specifying-an-endpoint-address.md)  
 介绍如何通过终结点与 WCF 服务进行通信。  
  
 [如何：在配置中创建服务终结点](./feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 演示如何在配置中创建服务终结点。  
  
 [如何：在代码中创建服务终结点](./feature-details/how-to-create-a-service-endpoint-in-code.md)  
 演示如何在代码中创建服务终结点。  
  
 [发布元数据终结点](publishing-metadata-endpoints.md)  
 演示如何通过在配置和代码中发布元数据终结点来发布元数据。  
  
## <a name="reference"></a>参考  

 <xref:System.ServiceModel.EndpointAddress>  
  
## <a name="related-sections"></a>相关章节  

 [基本编程生命周期](basic-programming-lifecycle.md)
