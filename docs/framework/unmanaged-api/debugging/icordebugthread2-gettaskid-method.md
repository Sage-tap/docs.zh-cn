---
description: 了解详细信息： ICorDebugThread2：： GetTaskID 方法
title: ICorDebugThread2::GetTaskID 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetTaskID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetTaskID
helpviewer_keywords:
- ICorDebugThread2::GetTaskID method [.NET Framework debugging]
- GetTaskID method [.NET Framework debugging]
ms.assetid: 6ba3c6ee-4ba1-4c98-bf1e-8531acd3da09
topic_type:
- apiref
ms.openlocfilehash: 5429daee9150d63834c747dd5ebb763dd6f0da6c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658654"
---
# <a name="icordebugthread2gettaskid-method"></a>ICorDebugThread2::GetTaskID 方法

获取此线程上运行的任务的标识符。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetTaskID (  
    [out] TASKID  *pTaskId  
);  
```  
  
## <a name="parameters"></a>参数  

 `pTaskId`  
 弄一个指针，指向在此 ICorDebugThread2 对象表示的线程上运行的任务的标识符。  
  
## <a name="remarks"></a>备注  

 任务只能在线程与连接关联时在线程上运行。 `GetTaskID` 如果线程与连接无关，则返回零 `pTaskId` 。  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **标头**：CorDebug.idl、CorDebug.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
