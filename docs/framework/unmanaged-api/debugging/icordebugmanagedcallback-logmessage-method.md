---
description: 了解详细信息： ICorDebugManagedCallback：： LogMessage 方法
title: ICorDebugManagedCallback::LogMessage 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LogMessage
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LogMessage
helpviewer_keywords:
- ICorDebugManagedCallback::LogMessage method [.NET Framework debugging]
- LogMessage method [.NET Framework debugging]
ms.assetid: d218554a-bf42-4d88-833d-ede30de67a53
topic_type:
- apiref
ms.openlocfilehash: 199f1f5dca7889a62ef351b4a2731fdb360768d3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660513"
---
# <a name="icordebugmanagedcallbacklogmessage-method"></a>ICorDebugManagedCallback::LogMessage 方法

通知调试器公共语言运行时 (CLR) 托管线程在类中调用了方法 <xref:System.Diagnostics.EventLog> 来记录事件。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT LogMessage (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pMessage  
);  
```  
  
## <a name="parameters"></a>参数  

 `pAppDomain`  
 中指向 ICorDebugAppDomain 对象的指针，该对象表示包含记录事件的托管线程的应用程序域。  
  
 `pThread`  
 中指向 ICorDebugThread 对象的指针，该对象表示托管线程。  
  
 `lLevel`  
 中 [LoggingLevelEnum](logginglevelenum-enumeration.md) 枚举的一个值，该值指示写入事件日志的描述性消息的严重性级别。  
  
 `pLogSwitchName`  
 中指向跟踪开关名称的指针。  
  
 `pMessage`  
 中指向写入事件日志的消息的指针。  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **标头**：CorDebug.idl、CorDebug.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICorDebugManagedCallback 接口](icordebugmanagedcallback-interface.md)
