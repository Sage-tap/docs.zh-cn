---
description: 了解详细信息： ICorProfilerCallback4 接口
title: ICorProfilerCallback4 接口
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4
helpviewer_keywords:
- ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 665f3cfc-cd6f-4880-906c-ea65ad384783
topic_type:
- apiref
ms.openlocfilehash: 882f234cb94ccd65203b42ed213aab6355250af8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788743"
---
# <a name="icorprofilercallback4-interface"></a><span data-ttu-id="3606e-103">ICorProfilerCallback4 接口</span><span class="sxs-lookup"><span data-stu-id="3606e-103">ICorProfilerCallback4 Interface</span></span>

<span data-ttu-id="3606e-104">提供公共语言运行时 (CLR) 用于将信息传递给探查器的回调方法。</span><span class="sxs-lookup"><span data-stu-id="3606e-104">Provides callback methods that the common language runtime (CLR) uses to communicate information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3606e-105">方法</span><span class="sxs-lookup"><span data-stu-id="3606e-105">Methods</span></span>  
  
|<span data-ttu-id="3606e-106">方法</span><span class="sxs-lookup"><span data-stu-id="3606e-106">Method</span></span>|<span data-ttu-id="3606e-107">说明</span><span class="sxs-lookup"><span data-stu-id="3606e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3606e-108">GetReJITParameters 方法</span><span class="sxs-lookup"><span data-stu-id="3606e-108">GetReJITParameters Method</span></span>](icorprofilercallback4-getrejitparameters-method.md)|<span data-ttu-id="3606e-109">允许代码探查器为新的重新编译的方法体设置备用代码生成标志。</span><span class="sxs-lookup"><span data-stu-id="3606e-109">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>|  
|[<span data-ttu-id="3606e-110">MovedReferences2 方法</span><span class="sxs-lookup"><span data-stu-id="3606e-110">MovedReferences2 Method</span></span>](icorprofilercallback4-movedreferences2-method.md)|<span data-ttu-id="3606e-111">作为压缩垃圾回收的结果，报告堆中对象的新布局。</span><span class="sxs-lookup"><span data-stu-id="3606e-111">Reports the new layout of objects in the heap as a result of a compacting garbage collection.</span></span>|  
|[<span data-ttu-id="3606e-112">ReJITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="3606e-112">ReJITCompilationFinished Method</span></span>](icorprofilercallback4-rejitcompilationfinished-method.md)|<span data-ttu-id="3606e-113">通知探查器实时 (JIT) 编译器已完成函数的重新编译。</span><span class="sxs-lookup"><span data-stu-id="3606e-113">Notifies the profiler that the just-in-time (JIT) compiler has finished the recompilation of a function.</span></span>|  
|[<span data-ttu-id="3606e-114">ReJITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="3606e-114">ReJITCompilationStarted Method</span></span>](icorprofilercallback4-rejitcompilationstarted-method.md)|<span data-ttu-id="3606e-115">通知探查器实时 (JIT) 编译器已开始重新编译某个函数。</span><span class="sxs-lookup"><span data-stu-id="3606e-115">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>|  
|[<span data-ttu-id="3606e-116">ReJITError 方法</span><span class="sxs-lookup"><span data-stu-id="3606e-116">ReJITError Method</span></span>](icorprofilercallback4-rejiterror-method.md)|<span data-ttu-id="3606e-117">报告处理重新编译请求时遇到的错误。</span><span class="sxs-lookup"><span data-stu-id="3606e-117">Reports an error encountered while processing a recompile request.</span></span>|  
|[<span data-ttu-id="3606e-118">SurvivingReferences2 方法</span><span class="sxs-lookup"><span data-stu-id="3606e-118">SurvivingReferences2 Method</span></span>](icorprofilercallback4-survivingreferences2-method.md)|<span data-ttu-id="3606e-119">将堆中对象的布局报告为非压缩垃圾回收的结果。</span><span class="sxs-lookup"><span data-stu-id="3606e-119">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3606e-120">备注</span><span class="sxs-lookup"><span data-stu-id="3606e-120">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3606e-121">要求</span><span class="sxs-lookup"><span data-stu-id="3606e-121">Requirements</span></span>  

 <span data-ttu-id="3606e-122">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3606e-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3606e-123">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3606e-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3606e-124">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3606e-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3606e-125">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3606e-125">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3606e-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="3606e-126">See also</span></span>

- [<span data-ttu-id="3606e-127">ICorProfilerCallback2 接口</span><span class="sxs-lookup"><span data-stu-id="3606e-127">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
- [<span data-ttu-id="3606e-128">分析接口</span><span class="sxs-lookup"><span data-stu-id="3606e-128">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="3606e-129">ICorProfilerInfo 接口</span><span class="sxs-lookup"><span data-stu-id="3606e-129">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
