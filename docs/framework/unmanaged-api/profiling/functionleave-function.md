---
description: 了解详细信息： FunctionLeave 函数
title: FunctionLeave 函数
ms.date: 03/30/2017
api_name:
- FunctionLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave
helpviewer_keywords:
- FunctionLeave function [.NET Framework profiling]
ms.assetid: 18e89f45-e068-426a-be16-9f53a4346860
topic_type:
- apiref
ms.openlocfilehash: cc0db68df8976ce86197cc9b7570b00c6f662cb5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648475"
---
# <a name="functionleave-function"></a><span data-ttu-id="87b99-103">FunctionLeave 函数</span><span class="sxs-lookup"><span data-stu-id="87b99-103">FunctionLeave Function</span></span>

<span data-ttu-id="87b99-104">通知探查器某个函数将要返回到调用方。</span><span class="sxs-lookup"><span data-stu-id="87b99-104">Notifies the profiler that a function is about to return to the caller.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="87b99-105">`FunctionLeave`.NET Framework 2.0 中不推荐使用该函数。</span><span class="sxs-lookup"><span data-stu-id="87b99-105">The `FunctionLeave` function is deprecated in the .NET Framework 2.0.</span></span> <span data-ttu-id="87b99-106">它将继续运行，但会导致性能下降。</span><span class="sxs-lookup"><span data-stu-id="87b99-106">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="87b99-107">改为使用 [FunctionLeave2](functionleave2-function.md) 函数。</span><span class="sxs-lookup"><span data-stu-id="87b99-107">Use the [FunctionLeave2](functionleave2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87b99-108">语法</span><span class="sxs-lookup"><span data-stu-id="87b99-108">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87b99-109">参数</span><span class="sxs-lookup"><span data-stu-id="87b99-109">Parameters</span></span>

- `funcID`

  <span data-ttu-id="87b99-110">\[in] 返回的函数的标识符。</span><span class="sxs-lookup"><span data-stu-id="87b99-110">\[in] The identifier of the function that is returning.</span></span>

## <a name="remarks"></a><span data-ttu-id="87b99-111">备注</span><span class="sxs-lookup"><span data-stu-id="87b99-111">Remarks</span></span>  

 <span data-ttu-id="87b99-112">`FunctionLeave`函数是回调; 必须实现它。</span><span class="sxs-lookup"><span data-stu-id="87b99-112">The `FunctionLeave` function is a callback; you must implement it.</span></span> <span data-ttu-id="87b99-113">实现必须使用 `__declspec` `naked`) 存储类特性的 (。</span><span class="sxs-lookup"><span data-stu-id="87b99-113">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="87b99-114">在调用此函数之前，执行引擎不会保存任何注册。</span><span class="sxs-lookup"><span data-stu-id="87b99-114">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="87b99-115">进入时，必须保存使用的所有寄存器，包括 (FPU) 的浮点单元中的寄存器。</span><span class="sxs-lookup"><span data-stu-id="87b99-115">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="87b99-116">退出时，必须通过弹出由其调用方推送的所有参数来还原堆栈。</span><span class="sxs-lookup"><span data-stu-id="87b99-116">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="87b99-117">的实现 `FunctionLeave` 不应被阻止，因为它将延迟垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="87b99-117">The implementation of `FunctionLeave` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="87b99-118">实现不应尝试垃圾回收，因为堆栈可能不处于垃圾回收友好状态。</span><span class="sxs-lookup"><span data-stu-id="87b99-118">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="87b99-119">如果尝试垃圾回收，则运行时将被阻止，直到 `FunctionLeave` 返回。</span><span class="sxs-lookup"><span data-stu-id="87b99-119">If a garbage collection is attempted, the runtime will block until `FunctionLeave` returns.</span></span>  
  
 <span data-ttu-id="87b99-120">此外，该 `FunctionLeave` 函数不得调入托管代码或以任何方式导致托管的内存分配。</span><span class="sxs-lookup"><span data-stu-id="87b99-120">Also, the `FunctionLeave` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87b99-121">要求</span><span class="sxs-lookup"><span data-stu-id="87b99-121">Requirements</span></span>  

 <span data-ttu-id="87b99-122">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="87b99-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87b99-123">**标头：** Corprof.idl .idl</span><span class="sxs-lookup"><span data-stu-id="87b99-123">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="87b99-124">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="87b99-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87b99-125">**.NET Framework 版本：** 1.1、1。0</span><span class="sxs-lookup"><span data-stu-id="87b99-125">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87b99-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="87b99-126">See also</span></span>

- [<span data-ttu-id="87b99-127">FunctionEnter2 函数</span><span class="sxs-lookup"><span data-stu-id="87b99-127">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="87b99-128">FunctionLeave2 函数</span><span class="sxs-lookup"><span data-stu-id="87b99-128">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="87b99-129">FunctionTailcall2 函数</span><span class="sxs-lookup"><span data-stu-id="87b99-129">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="87b99-130">SetEnterLeaveFunctionHooks2 方法</span><span class="sxs-lookup"><span data-stu-id="87b99-130">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="87b99-131">分析全局静态函数</span><span class="sxs-lookup"><span data-stu-id="87b99-131">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
