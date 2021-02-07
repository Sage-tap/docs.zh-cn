---
description: 了解详细信息： ICorProfilerCallback：： ExceptionUnwindFinallyLeave 方法
title: ICorProfilerCallback::ExceptionUnwindFinallyLeave 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFinallyLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyLeave method [.NET Framework profiling]
- ExceptionUnwindFinallyLeave method [.NET Framework profiling]
ms.assetid: 2350351e-f253-4c0c-a191-f952bc5700e6
topic_type:
- apiref
ms.openlocfilehash: dd3916d1e250344dbbc707a2ba3ef21a4877415f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706105"
---
# <a name="icorprofilercallbackexceptionunwindfinallyleave-method"></a><span data-ttu-id="d2bd2-103">ICorProfilerCallback::ExceptionUnwindFinallyLeave 方法</span><span class="sxs-lookup"><span data-stu-id="d2bd2-103">ICorProfilerCallback::ExceptionUnwindFinallyLeave Method</span></span>

<span data-ttu-id="d2bd2-104">通知探查器异常处理的展开阶段已离开 `finally` 子句。</span><span class="sxs-lookup"><span data-stu-id="d2bd2-104">Notifies the profiler that the unwind phase of exception handling has left a `finally` clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2bd2-105">语法</span><span class="sxs-lookup"><span data-stu-id="d2bd2-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwindFinallyLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="d2bd2-106">备注</span><span class="sxs-lookup"><span data-stu-id="d2bd2-106">Remarks</span></span>  

 <span data-ttu-id="d2bd2-107">探查器不应在此调用期间被阻止，因为堆栈可能不处于允许垃圾回收的状态，因此无法启用抢先垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="d2bd2-107">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="d2bd2-108">如果探查器在此处阻止并且试图进行垃圾回收，则运行时将被阻止，直到此回调返回。</span><span class="sxs-lookup"><span data-stu-id="d2bd2-108">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="d2bd2-109">此外，在此调用期间，探查器不得调入托管代码或以任何方式导致托管内存分配。</span><span class="sxs-lookup"><span data-stu-id="d2bd2-109">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2bd2-110">要求</span><span class="sxs-lookup"><span data-stu-id="d2bd2-110">Requirements</span></span>  

 <span data-ttu-id="d2bd2-111">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d2bd2-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2bd2-112">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d2bd2-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d2bd2-113">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d2bd2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d2bd2-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2bd2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2bd2-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="d2bd2-115">See also</span></span>

- [<span data-ttu-id="d2bd2-116">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="d2bd2-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="d2bd2-117">ExceptionUnwindFinallyEnter 方法</span><span class="sxs-lookup"><span data-stu-id="d2bd2-117">ExceptionUnwindFinallyEnter Method</span></span>](icorprofilercallback-exceptionunwindfinallyenter-method.md)
