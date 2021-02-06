---
description: 了解详细信息： ICorProfilerCallback：： RuntimeSuspendStarted 方法
title: ICorProfilerCallback::RuntimeSuspendStarted 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeSuspendStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendStarted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendStarted method [.NET Framework profiling]
- RuntimeSuspendStarted method [.NET Framework profiling]
ms.assetid: c8461cac-e31b-4efa-ad2c-26598173eb96
topic_type:
- apiref
ms.openlocfilehash: 7f7ba6a2a8523589b025d98ea925b77d05d8a59d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657406"
---
# <a name="icorprofilercallbackruntimesuspendstarted-method"></a><span data-ttu-id="11c72-103">ICorProfilerCallback::RuntimeSuspendStarted 方法</span><span class="sxs-lookup"><span data-stu-id="11c72-103">ICorProfilerCallback::RuntimeSuspendStarted Method</span></span>

<span data-ttu-id="11c72-104">通知探查器运行时将要挂起所有运行时线程。</span><span class="sxs-lookup"><span data-stu-id="11c72-104">Notifies the profiler that the runtime is about to suspend all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11c72-105">语法</span><span class="sxs-lookup"><span data-stu-id="11c72-105">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendStarted(  
    [in] COR_PRF_SUSPEND_REASON suspendReason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11c72-106">参数</span><span class="sxs-lookup"><span data-stu-id="11c72-106">Parameters</span></span>  

 `suspendReason`  
 <span data-ttu-id="11c72-107">中一个 [COR_PRF_SUSPEND_REASON](cor-prf-suspend-reason-enumeration.md) 枚举的值，该值指示挂起的原因。</span><span class="sxs-lookup"><span data-stu-id="11c72-107">[in] A value of the [COR_PRF_SUSPEND_REASON](cor-prf-suspend-reason-enumeration.md) enumeration that indicates the reason for the suspension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11c72-108">备注</span><span class="sxs-lookup"><span data-stu-id="11c72-108">Remarks</span></span>  

 <span data-ttu-id="11c72-109">允许非托管代码中的所有运行时线程继续运行，直到它们尝试重新进入运行时。</span><span class="sxs-lookup"><span data-stu-id="11c72-109">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="11c72-110">此时，它们也将被挂起，直到运行时恢复。</span><span class="sxs-lookup"><span data-stu-id="11c72-110">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="11c72-111">这也适用于输入运行时的新线程。</span><span class="sxs-lookup"><span data-stu-id="11c72-111">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="11c72-112">如果运行时中的所有线程已处于中断的代码中，则会立即将其挂起，或者当它们到达中断的代码时要求它们挂起。</span><span class="sxs-lookup"><span data-stu-id="11c72-112">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11c72-113">要求</span><span class="sxs-lookup"><span data-stu-id="11c72-113">Requirements</span></span>  

 <span data-ttu-id="11c72-114">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="11c72-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11c72-115">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="11c72-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="11c72-116">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11c72-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11c72-117">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11c72-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11c72-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="11c72-118">See also</span></span>

- [<span data-ttu-id="11c72-119">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="11c72-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="11c72-120">RuntimeSuspendAborted 方法</span><span class="sxs-lookup"><span data-stu-id="11c72-120">RuntimeSuspendAborted Method</span></span>](icorprofilercallback-runtimesuspendaborted-method.md)
- [<span data-ttu-id="11c72-121">RuntimeSuspendFinished 方法</span><span class="sxs-lookup"><span data-stu-id="11c72-121">RuntimeSuspendFinished Method</span></span>](icorprofilercallback-runtimesuspendfinished-method.md)
