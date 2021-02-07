---
description: 了解详细信息： IDebuggerThreadControl 接口
title: IDebuggerThreadControl 接口
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IDebuggerThreadControl
helpviewer_keywords:
- IDebuggerThreadControl interface [.NET Framework hosting]
ms.assetid: 0a270c42-a7d1-45f1-a64d-fa3e84d14532
topic_type:
- apiref
ms.openlocfilehash: 293a120d44b9b04d7e367546c477fb273f535310
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709734"
---
# <a name="idebuggerthreadcontrol-interface"></a>IDebuggerThreadControl 接口

提供一些方法，用于通知宿主调试服务阻止和取消阻止线程。  
  
## <a name="methods"></a>方法  
  
|方法|说明|  
|------------|-----------------|  
|[ThreadIsBlockingForDebugger 方法](idebuggerthreadcontrol-threadisblockingfordebugger-method.md)|向宿主通知发送此回调的线程即将在调试服务中阻止。|  
|[ReleaseAllRuntimeThreads 方法](idebuggerthreadcontrol-releaseallruntimethreads-method.md)|向宿主通知调试服务将要释放被阻止的所有线程。|  
|[StartBlockingForDebugger 方法](idebuggerthreadcontrol-startblockingfordebugger-method.md)|通知宿主调试服务即将开始阻塞所有线程。|  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **标头：** Mscoree.dll  
  
 **库：** 作为中的资源包含 MSCorEE.dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [承载接口](hosting-interfaces.md)
