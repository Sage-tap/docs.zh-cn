---
description: 了解详细信息： ICorDebugAssembly3 接口
title: “ICor调试程序集3”接口
ms.date: 03/30/2017
ms.assetid: 17fc5d76-75a9-4933-83f0-594de7f973f3
ms.openlocfilehash: 3a8cabf41dffa75d82c2b6fde53dff2ede4838e7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791499"
---
# <a name="icordebugassembly3-interface"></a>“ICor调试程序集3”接口

对 ICorDebugAssembly 接口进行逻辑扩展，从而为容器程序集及其包含的程序集提供支持。  
  
## <a name="methods"></a>方法  
  
|方法|说明|  
|------------|-----------------|  
|[EnumerateContainedAssemblies 方法](icordebugassembly3-enumeratecontainedassemblies-method.md)|获取该程序集中所包含的程序集的枚举器。|  
|[GetContainerAssembly 方法](icordebugassembly3-getcontainerassembly-method.md)|返回该 `ICorDebugAssembly3` 对象的容器程序集。|  
  
## <a name="remarks"></a>备注  
  
> [!NOTE]
> 此接口仅适用于 .NET Native。 尝试调用 `QueryInterface` 来检索接口指针会为 .NET Native 外部的 ICorDebug 方案返回 `E_NOINTERFACE`。  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **标头**：CorDebug.idl、CorDebug.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>请参阅

- [调试接口](debugging-interfaces.md)
- [调试](index.md)
