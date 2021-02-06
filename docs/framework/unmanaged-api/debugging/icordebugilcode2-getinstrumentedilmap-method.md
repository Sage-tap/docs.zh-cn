---
description: 了解详细信息： ICorDebugILCode2：： GetInstrumentedILMap 方法
title: ICorDebugILCode2::GetInstrumentedILMap 方法
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILCode2.GetInstrumentedILMap
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 7a4e3085-8f95-40ef-a4be-7d6146f47ce2
topic_type:
- apiref
ms.openlocfilehash: 6892b059e1774d7b0a61d7a8dd7df69bc2e8c569
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660565"
---
# <a name="icordebugilcode2getinstrumentedilmap-method"></a><span data-ttu-id="5bdf4-103">ICorDebugILCode2::GetInstrumentedILMap 方法</span><span class="sxs-lookup"><span data-stu-id="5bdf4-103">ICorDebugILCode2::GetInstrumentedILMap Method</span></span>

<span data-ttu-id="5bdf4-104">[仅在 .NET Framework 4.5.2 及更高版本中受支持]</span><span class="sxs-lookup"><span data-stu-id="5bdf4-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="5bdf4-105">返回从探查器检测到的中间语言 (IL) 偏移量到此实例的原始方法的 IL 偏移量的映射。</span><span class="sxs-lookup"><span data-stu-id="5bdf4-105">Returns a map from profiler-instrumented intermediate language (IL) offsets to original method IL offsets for this instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bdf4-106">语法</span><span class="sxs-lookup"><span data-stu-id="5bdf4-106">Syntax</span></span>  
  
```cpp
HRESULT GetInstrumentedILMap(  
   [in] ULONG32 cMap,  
   [out] ULONG32 *pcMap,  
   [out, size_is(cMap), length_is(*pcMap)] COR_IL_MAP map[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5bdf4-107">参数</span><span class="sxs-lookup"><span data-stu-id="5bdf4-107">Parameters</span></span>  

 <span data-ttu-id="5bdf4-108">cMap</span><span class="sxs-lookup"><span data-stu-id="5bdf4-108">cMap</span></span>  
 <span data-ttu-id="5bdf4-109">[in] `map` 数组的存储容量。</span><span class="sxs-lookup"><span data-stu-id="5bdf4-109">[in] The storage capacity of the `map` array.</span></span> <span data-ttu-id="5bdf4-110">有关详细信息，请参阅备注部分。</span><span class="sxs-lookup"><span data-stu-id="5bdf4-110">See the Remarks section for more information.</span></span>  
  
 <span data-ttu-id="5bdf4-111">pcMap</span><span class="sxs-lookup"><span data-stu-id="5bdf4-111">pcMap</span></span>  
 <span data-ttu-id="5bdf4-112">[out] 写入映射数组的 COR_IL_MAP 值的数量。</span><span class="sxs-lookup"><span data-stu-id="5bdf4-112">[out] The number of COR_IL_MAP values written to the map array.</span></span>  
  
 <span data-ttu-id="5bdf4-113">map</span><span class="sxs-lookup"><span data-stu-id="5bdf4-113">map</span></span>  
 <span data-ttu-id="5bdf4-114">[out] 一个 COR_IL_MAP 值的数组，提供了有关从探查器检测到的 IL 到原始方法的 IL 的映射信息。</span><span class="sxs-lookup"><span data-stu-id="5bdf4-114">[out] An array of COR_IL_MAP values that provide information on mappings from profiler-instrumented IL to the IL of the original method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5bdf4-115">备注</span><span class="sxs-lookup"><span data-stu-id="5bdf4-115">Remarks</span></span>  

 <span data-ttu-id="5bdf4-116">如果探查器通过调用 [ICorProfilerInfo：： SetILInstrumentedCodeMap](../profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) 方法设置映射，则调试器可以调用此方法来检索映射，并在计算堆栈跟踪和变量生存期的 IL 偏移量时在内部使用该映射。</span><span class="sxs-lookup"><span data-stu-id="5bdf4-116">If the profiler sets the mapping by calling the [ICorProfilerInfo::SetILInstrumentedCodeMap](../profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) method, the debugger can call this method to retrieve the mapping and to use the mapping internally when calculating IL offsets for stack traces and variable lifetimes.</span></span>  
  
 <span data-ttu-id="5bdf4-117">如果 `cMap` 为0且 `pcMap` 为非 **null**， `pcMap` 则将设置为可用 COR_IL_MAP 值的数目。</span><span class="sxs-lookup"><span data-stu-id="5bdf4-117">If `cMap` is 0 and `pcMap` is non-**null**, `pcMap` is set to the number of available COR_IL_MAP values.</span></span> <span data-ttu-id="5bdf4-118">如果  为非零，则它表示  数组的存储容量。</span><span class="sxs-lookup"><span data-stu-id="5bdf4-118">If `cMap` is non-zero, it represents the storage capacity of the `map` array.</span></span> <span data-ttu-id="5bdf4-119">当该方法返回时，将 `map` 包含最多个 `cMap` 项，并且 `pcMap` 将设置为实际写入数组的 COR_IL_MAP 值的数量 `map` 。</span><span class="sxs-lookup"><span data-stu-id="5bdf4-119">When the method returns, `map` contains a maximum of `cMap` items, and `pcMap` is set to the number of COR_IL_MAP values actually written to the `map` array.</span></span>  
  
 <span data-ttu-id="5bdf4-120">如果尚未检测到 IL 或探查器没有提供映射，则此方法将返回 `S_OK` 并将 `pcMap` 设置为 0。</span><span class="sxs-lookup"><span data-stu-id="5bdf4-120">If the IL hasn't been instrumented or the mapping wasn't provided by a profiler, this method returns `S_OK` and sets `pcMap` to 0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bdf4-121">要求</span><span class="sxs-lookup"><span data-stu-id="5bdf4-121">Requirements</span></span>  

 <span data-ttu-id="5bdf4-122">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5bdf4-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bdf4-123">**标头**：CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5bdf4-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5bdf4-124">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5bdf4-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5bdf4-125">**.NET Framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5bdf4-125">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bdf4-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="5bdf4-126">See also</span></span>

- [<span data-ttu-id="5bdf4-127">ICorProfilerInfo::SetILInstrumentedCodeMap</span><span class="sxs-lookup"><span data-stu-id="5bdf4-127">ICorProfilerInfo::SetILInstrumentedCodeMap</span></span>](../profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)
- [<span data-ttu-id="5bdf4-128">ICorDebugILCode2 接口</span><span class="sxs-lookup"><span data-stu-id="5bdf4-128">ICorDebugILCode2 Interface</span></span>](icordebugilcode2-interface.md)
- [<span data-ttu-id="5bdf4-129">调试接口</span><span class="sxs-lookup"><span data-stu-id="5bdf4-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
