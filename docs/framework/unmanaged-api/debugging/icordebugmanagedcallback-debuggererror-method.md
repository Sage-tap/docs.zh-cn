---
description: 了解详细信息： ICorDebugManagedCallback：:D ebuggerError 方法
title: ICorDebugManagedCallback::DebuggerError 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.DebuggerError
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::DebuggerError
helpviewer_keywords:
- DebuggerError method [.NET Framework debugging]
- ICorDebugManagedCallback::DebuggerError method [.NET Framework debugging]
ms.assetid: 9e983d11-eaf3-4741-b936-29ec456384a3
topic_type:
- apiref
ms.openlocfilehash: 2f73e07711f7d2ce865aab8f90862563e767fd16
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790993"
---
# <a name="icordebugmanagedcallbackdebuggererror-method"></a>ICorDebugManagedCallback::DebuggerError 方法

通知调试器在尝试处理来自公共语言运行时 (CLR) 的事件时出错。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT DebuggerError (  
    [in] ICorDebugProcess *pProcess,  
    [in] HRESULT           errorHR,  
    [in] DWORD             errorCode  
);  
```  
  
## <a name="parameters"></a>参数  

 `pProcess`  
 中一个指向 "ICorDebugProcess" 对象的指针，该对象表示发生事件的进程。  
  
 `errorHR`  
 中从事件处理程序返回的 HRESULT 值。  
  
 `errorCode`  
 中一个整数，指定 CLR 错误。  
  
## <a name="remarks"></a>备注  

 根据错误的性质，此过程可能会置于直通模式下。  
  
 `DebugError`回调指示调试服务由于错误而被禁用，因此调试器应向用户提供错误消息。 [ICorDebugProcess：： GetID](icordebugprocess-getid-method.md) 可以安全调用，但所有其他方法（包括 [ICorDebug：： Terminate](icordebug-terminate-method.md)）都不应调用。 调试器应使用操作系统工具来终止进程。  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **标头**：CorDebug.idl、CorDebug.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICorDebugManagedCallback 接口](icordebugmanagedcallback-interface.md)
