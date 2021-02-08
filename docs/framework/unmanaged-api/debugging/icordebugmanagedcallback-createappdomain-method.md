---
description: 了解详细信息： ICorDebugManagedCallback：： CreateAppDomain 方法
title: ICorDebugManagedCallback::CreateAppDomain 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.CreateAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::CreateAppDomain
helpviewer_keywords:
- CreateAppDomain method [.NET Framework debugging]
- ICorDebugManagedCallback::CreateAppDomain method [.NET Framework debugging]
ms.assetid: 48d410d7-6749-4125-a8fd-f9562c7088e9
topic_type:
- apiref
ms.openlocfilehash: 5f4aa49ce90e8ec1343794db71ae3aa911c9e09f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791060"
---
# <a name="icordebugmanagedcallbackcreateappdomain-method"></a>ICorDebugManagedCallback::CreateAppDomain 方法

通知调试器已创建应用程序域。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT CreateAppDomain (  
    [in] ICorDebugProcess   *pProcess,  
    [in] ICorDebugAppDomain *pAppDomain  
);  
```  
  
## <a name="parameters"></a>参数  

 `pProcess`  
 中指向 ICorDebugProcess 对象的指针，该对象表示在其中创建应用程序域的进程。  
  
 `pAppDomain`  
 中指向 ICorDebugAppDomain 对象的指针，该对象表示已创建的应用程序域。  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **标头**：CorDebug.idl、CorDebug.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICorDebugManagedCallback 接口](icordebugmanagedcallback-interface.md)
