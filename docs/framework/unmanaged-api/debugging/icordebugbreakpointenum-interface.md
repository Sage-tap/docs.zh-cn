---
description: 了解详细信息： ICorDebugBreakpointEnum 接口
title: ICorDebugBreakpointEnum 接口
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpointEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpointEnum
helpviewer_keywords:
- ICorDebugBreakpointEnum interface [.NET Framework debugging]
ms.assetid: 4c6f4f6e-52cc-402e-881b-7b8526544c90
topic_type:
- apiref
ms.openlocfilehash: 71bd69c4fabba4a7d06f3b4cee5c0cf859d3c92b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711721"
---
# <a name="icordebugbreakpointenum-interface"></a>ICorDebugBreakpointEnum 接口

实现 ICorDebugEnum 方法，并枚举 ICorDebugBreakpoint 数组。  
  
## <a name="methods"></a>方法  
  
|方法|说明|  
|------------|-----------------|  
|[下一方法](icordebugbreakpointenum-next-method.md)|`ICorDebugBreakpoint`从当前位置开始，从枚举中获取指定数目的实例。|  
  
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
