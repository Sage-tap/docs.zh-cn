---
description: 了解详细信息： ICorProfilerCallback4：： ReJITCompilationStarted 方法
title: ICorProfilerCallback4::ReJITCompilationStarted 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITCompilationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITCompilationStarted
helpviewer_keywords:
- ReJITCompilationStarted method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITCompilationStarted method [.NET Framework profiling]
ms.assetid: 512fdd00-262a-4456-a075-365ef4133c4d
topic_type:
- apiref
ms.openlocfilehash: 7656f68ff6b10dcd58e48df212a036a590d0c3b3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788704"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a><span data-ttu-id="8de30-103">ICorProfilerCallback4::ReJITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="8de30-103">ICorProfilerCallback4::ReJITCompilationStarted Method</span></span>

<span data-ttu-id="8de30-104">通知探查器实时 (JIT) 编译器已开始重新编译某个函数。</span><span class="sxs-lookup"><span data-stu-id="8de30-104">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8de30-105">语法</span><span class="sxs-lookup"><span data-stu-id="8de30-105">Syntax</span></span>  
  
```cpp  
HRESULT ReJITCompilationStarted(
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8de30-106">参数</span><span class="sxs-lookup"><span data-stu-id="8de30-106">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="8de30-107">中JIT 编译器已开始重新编译的函数的 ID。</span><span class="sxs-lookup"><span data-stu-id="8de30-107">[in] The ID of the function that the JIT compiler has started to recompile.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="8de30-108">中新版本的函数的重新编译 ID。</span><span class="sxs-lookup"><span data-stu-id="8de30-108">[in] The recompilation ID of the new version of the function.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="8de30-109">[in] `true` 指示阻止可能会导致运行时等待调用线程从该回调返回; `false` 指示阻止操作不会影响运行时的操作。</span><span class="sxs-lookup"><span data-stu-id="8de30-109">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span> <span data-ttu-id="8de30-110">的值 `true` 不会损害运行时，但会影响分析结果。</span><span class="sxs-lookup"><span data-stu-id="8de30-110">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8de30-111">备注</span><span class="sxs-lookup"><span data-stu-id="8de30-111">Remarks</span></span>  

 <span data-ttu-id="8de30-112">`ReJITCompilationStarted`由于运行时处理类构造函数的方式，每个函数可以接收多对和[ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md)方法调用。</span><span class="sxs-lookup"><span data-stu-id="8de30-112">It is possible to receive more than one pair of `ReJITCompilationStarted` and [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) method calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="8de30-113">例如，运行时开始重新编译方法 A，但类 B 的类构造函数需要运行。</span><span class="sxs-lookup"><span data-stu-id="8de30-113">For example, the runtime starts to recompile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="8de30-114">因此，运行时将为类 B 重新编译构造函数并运行它。</span><span class="sxs-lookup"><span data-stu-id="8de30-114">Therefore, the runtime recompiles the constructor for class B and runs it.</span></span> <span data-ttu-id="8de30-115">当构造函数正在运行时，它会调用方法 A，这将导致重新编译方法 A。</span><span class="sxs-lookup"><span data-stu-id="8de30-115">While the constructor is running, it makes a call to method A, which causes method A to be recompiled again.</span></span> <span data-ttu-id="8de30-116">在此方案中，方法 A 的第一次重新编译将暂停。</span><span class="sxs-lookup"><span data-stu-id="8de30-116">In this scenario, the first recompilation of method A is halted.</span></span> <span data-ttu-id="8de30-117">但是，将使用 JIT 重新编译事件来报告对方法 A 的重新编译。</span><span class="sxs-lookup"><span data-stu-id="8de30-117">However, both attempts to recompile method A are reported with JIT recompilation events.</span></span>  
  
 <span data-ttu-id="8de30-118">当两个线程同时进行回调时，探查器必须支持 JIT 重新编译回调的顺序。</span><span class="sxs-lookup"><span data-stu-id="8de30-118">Profilers must support the sequence of JIT recompilation callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="8de30-119">例如，线程 A 调用 `ReJITCompilationStarted` ; 但是，在线程 a 调用 [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md)之前，线程 B 使用线程 a 的回调中的函数 ID 调用 [ICorProfilerCallback：： ExceptionSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) `ReJITCompilationStarted` 。由于探查器尚未收到对 [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) 的调用，因此函数 ID 似乎不应有效。</span><span class="sxs-lookup"><span data-stu-id="8de30-119">For example, thread A calls `ReJITCompilationStarted`; however, before thread A calls [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md), thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from the `ReJITCompilationStarted` callback for thread A. It might appear that the function ID should not yet be valid because a call to [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) had not yet been received by the profiler.</span></span> <span data-ttu-id="8de30-120">但在这种情况下，函数 ID 有效。</span><span class="sxs-lookup"><span data-stu-id="8de30-120">However, in this case, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8de30-121">要求</span><span class="sxs-lookup"><span data-stu-id="8de30-121">Requirements</span></span>  

 <span data-ttu-id="8de30-122">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8de30-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8de30-123">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8de30-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8de30-124">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8de30-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8de30-125">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8de30-125">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8de30-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="8de30-126">See also</span></span>

- [<span data-ttu-id="8de30-127">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="8de30-127">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="8de30-128">ICorProfilerCallback4 接口</span><span class="sxs-lookup"><span data-stu-id="8de30-128">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
- [<span data-ttu-id="8de30-129">JITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="8de30-129">JITCompilationFinished Method</span></span>](icorprofilercallback-jitcompilationfinished-method.md)
- [<span data-ttu-id="8de30-130">ReJITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="8de30-130">ReJITCompilationFinished Method</span></span>](icorprofilercallback4-rejitcompilationfinished-method.md)
