---
description: 了解详细信息： ICorDebugFrame 接口
title: ICorDebugFrame 接口
ms.date: 03/30/2017
api_name:
- ICorDebugFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame
helpviewer_keywords:
- ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 0c48f764-3c64-4602-b2f4-4ffc60eb2c65
topic_type:
- apiref
ms.openlocfilehash: d0fd629672d535f89fe78c178032937443d9dfbd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692844"
---
# <a name="icordebugframe-interface"></a>ICorDebugFrame 接口

表示当前堆栈上的帧。  
  
## <a name="methods"></a>方法  
  
|方法|说明|  
|------------|-----------------|  
|[CreateStepper 方法](icordebugframe-createstepper-method.md)|获取用于执行与此相关的单步执行操作的 ICorDebugStepper `ICorDebugFrame` 。|  
|[GetCallee 方法](icordebugframe-getcallee-method.md)|获取一个指针，该指针指向 `ICorDebugFrame` 此框架调用的当前链中的，如果这是链中的最内层帧，则返回 null。|  
|[GetCaller 方法](icordebugframe-getcaller-method.md)|获取指向 `ICorDebugFrame` 当前链中调用此帧的的指针，如果这是链中最外层的帧，则返回 null。|  
|[GetChain 方法](icordebugframe-getchain-method.md)|获取一个指针，该指针指向作为的一部分的 ICorDebugChain `ICorDebugFrame` 。|  
|[GetCode 方法](icordebugframe-getcode-method.md)|获取一个指针，该指针指向与此堆栈帧关联的 ICorDebugCode。|  
|[GetFunction 方法](icordebugframe-getfunction-method.md)|获取一个指向 ICorDebugFunction 的指针，该指针包含与此堆栈帧关联的代码。|  
|[GetFunctionToken 方法](icordebugframe-getfunctiontoken-method.md)|获取包含与此堆栈帧关联的代码的函数的元数据标记。|  
|[GetStackRange 方法](icordebugframe-getstackrange-method.md)|获取此所表示的堆栈帧的绝对地址范围 `ICorDebugFrame` 。|  
  
## <a name="remarks"></a>备注  
  
> [!NOTE]
> 此接口不支持跨计算机或跨进程远程调用。  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **标头**：CorDebug.idl、CorDebug.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [调试接口](debugging-interfaces.md)
