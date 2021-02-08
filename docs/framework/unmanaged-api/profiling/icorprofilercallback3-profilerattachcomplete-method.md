---
description: 了解详细信息： ICorProfilerCallback3：:P rofilerAttachComplete 方法
title: ICorProfilerCallback3::ProfilerAttachComplete 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.ProfilerAttachComplete Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::ProfilerAttachComplete
helpviewer_keywords:
- ProfilerAttachComplete method [.NET Framework profiling]
- ICorProfilerCallback3::ProfilerAttachComplete method [.NET Framework profiling]
ms.assetid: 257d6076-06e0-4d93-bb33-651fbb2b92d7
topic_type:
- apiref
ms.openlocfilehash: dcd8ab9fed402593fc955050b0d3be6f8a46730a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788782"
---
# <a name="icorprofilercallback3profilerattachcomplete-method"></a>ICorProfilerCallback3::ProfilerAttachComplete 方法

由公共语言运行时 (CLR) 调用，以指示探查器现在可以调用 [ICorProfilerInfo3：： EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) 和 [ICorProfilerInfo3：： EnumModules](icorprofilerinfo3-enummodules-method.md) 追赶方法。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT ProfilerAttachComplete ();  
```  
  
## <a name="remarks"></a>备注  

 `ProfilerAttachComplete`调用[ICorProfilerCallback3：： InitializeForAttach](icorprofilercallback3-initializeforattach-method.md)方法后发出回调。 指示如下内容：  
  
- 已激活 `InitializeForAttach` 中的探测器请求的回调。  
  
- 探查器现在可以对关联的 ID 执行追赶操作，而不必担心丢失通知。  
  
 CLR 将忽略从此回调返回的值。  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **头文件：** CorProf.idl、CorProf.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICorProfilerCallback 接口](icorprofilercallback-interface.md)
- [ICorProfilerInfo3 接口](icorprofilerinfo3-interface.md)
- [分析接口](profiling-interfaces.md)
- [分析](index.md)
