---
description: 了解详细信息： GetStartupNotificationEvent 函数
title: GetStartupNotificationEvent 函数
ms.date: 03/30/2017
api_name:
- GetStartupNotificationEvent
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- GetStartupNotificationEvent
helpviewer_keywords:
- GetStartupNotificationEvent function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: c94b1b61-045a-4695-bacd-0f18c5acc246
topic_type:
- apiref
ms.openlocfilehash: 49b0e3f9b2acec87e419bae03086a7e437f45f98
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801379"
---
# <a name="getstartupnotificationevent-function"></a>GetStartupNotificationEvent 函数

创建或打开一个事件句柄，由在指定目标进程中加载的公共语言运行时 (CLR) 对其发出信号。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetStartupNotificationEvent  
    (  
    [in]  DWORD     debuggeePID,  
    [out]  HANDLE*  phStartupEvent  
    );  
```  
  
## <a name="parameters"></a>参数  

 `debuggeePID`  
 [in] 从其中接收 CLR 启动通知的目标进程的进程标识符。  
  
 `phStartupEvent`  
 [out] 指向在启动时由 CLR 发出信号通知的句柄的指针。  
  
## <a name="return-value"></a>返回值  

 S_OK  
 成功获取启动通知事件的句柄。  
  
 E_INVALIDARG  
 `phStartupEvent` 为 null 或 `debuggeePID` 不引用当前正在运行的进程。  
  
 E_FAIL（或其他 E_ 返回代码）  
 无法获取启动通知事件的句柄。  
  
## <a name="remarks"></a>备注  

 在 Windows 操作系统上，`debuggeePID` 映射到 OS 进程标识符。  
  
 在发出信号通知事件的 CLR 执行任何托管代码之前，对该事件发出了信号。  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **标头：** dbgshim.dll  
  
 **库：** dbgshim.dll  
  
 **.NET Framework 版本：** 3.5 SP1
