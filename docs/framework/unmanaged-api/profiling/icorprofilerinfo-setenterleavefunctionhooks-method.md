---
description: 了解详细信息： ICorProfilerInfo：： SetEnterLeaveFunctionHooks 方法
title: ICorProfilerInfo::SetEnterLeaveFunctionHooks 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetEnterLeaveFunctionHooks
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetEnterLeaveFunctionHooks
helpviewer_keywords:
- SetEnterLeaveFunctionHooks method [.NET Framework profiling]
- ICorProfilerInfo::SetEnterLeaveFunctionHooks method [.NET Framework profiling]
ms.assetid: 72399636-c219-4ffd-8ac8-39432c9d4641
topic_type:
- apiref
ms.openlocfilehash: 45c161a76f3ae568da6a83a2c45acb214a327ff1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687202"
---
# <a name="icorprofilerinfosetenterleavefunctionhooks-method"></a>ICorProfilerInfo::SetEnterLeaveFunctionHooks 方法

指定在托管函数的 "enter"、"leave" 和 "tailcall" 挂钩上调用的探查器实现函数。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks(  
    [in] FunctionEnter    *pFuncEnter,  
    [in] FunctionLeave    *pFuncLeave,  
    [in] FunctionTailcall *pFuncTailcall);  
```  
  
## <a name="parameters"></a>参数  

 `pFuncEnter`  
 中指向要用作 [FunctionEnter](functionenter-function.md) 回调的实现的指针。  
  
 `pFuncLeave`  
 中指向要用作 [FunctionLeave](functionleave-function.md) 回调的实现的指针。  
  
 `pFuncTailcall`  
 中指向要用作 [FunctionTailcall](functiontailcall-function.md) 回调的实现的指针。  
  
## <a name="remarks"></a>备注  

 在 .NET Framework 版本1.0 中，每个函数指针均可为 null，以禁用相应的回调。  
  
 一次只能有一个回调集处于活动状态。 因此，如果探查器同时调用 `SetEnterLeaveFunctionHooks` 和 [ICorProfilerInfo2：： SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)，则 `SetEnterLeaveFunctionHooks2` 优先使用。  
  
 只能 `SetEnterLeaveFunctionHooks` 从探查器的 [ICorProfilerCallback：： Initialize](icorprofilercallback-initialize-method.md) 回调调用此方法。  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **头文件：** CorProf.idl、CorProf.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICorProfilerInfo 接口](icorprofilerinfo-interface.md)
