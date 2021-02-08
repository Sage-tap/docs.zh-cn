---
description: 了解详细信息： ICorProfilerModuleEnum：： Next 方法
title: ICorProfilerModuleEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.Next Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::Next
helpviewer_keywords:
- ICorProfilerModuleEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: a3cea59d-7622-4323-897a-0a464c40f77f
topic_type:
- apiref
ms.openlocfilehash: 06c9528d5468847a905e84fe38591c9b5ef3ee44
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798987"
---
# <a name="icorprofilermoduleenumnext-method"></a><span data-ttu-id="84e86-103">ICorProfilerModuleEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="84e86-103">ICorProfilerModuleEnum::Next Method</span></span>

<span data-ttu-id="84e86-104">从模块的序列集合中获取指定的连续模块数，从枚举器在该序列的当前位置开始。</span><span class="sxs-lookup"><span data-stu-id="84e86-104">Gets the specified number of contiguous modules from a sequential collection of modules, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84e86-105">语法</span><span class="sxs-lookup"><span data-stu-id="84e86-105">Syntax</span></span>  
  
```cpp  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    ModuleID ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84e86-106">参数</span><span class="sxs-lookup"><span data-stu-id="84e86-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="84e86-107">[in] 要检索的模块的数量。</span><span class="sxs-lookup"><span data-stu-id="84e86-107">[in] The number of modules to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="84e86-108">[out] `ModuleID` 值的数组，其中每个表示检索的模块。</span><span class="sxs-lookup"><span data-stu-id="84e86-108">[out] An array of `ModuleID` values, each of which represents a retrieved module.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="84e86-109">[out] 指向 `ids` 数组中实际返回的元素数目的指针。</span><span class="sxs-lookup"><span data-stu-id="84e86-109">[out] A pointer to the number of elements actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="84e86-110">返回值</span><span class="sxs-lookup"><span data-stu-id="84e86-110">Return Value</span></span>  

 <span data-ttu-id="84e86-111">此方法返回以下特定 HRESULT 以及表示方法失败的 HRESULT 错误。</span><span class="sxs-lookup"><span data-stu-id="84e86-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="84e86-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="84e86-112">HRESULT</span></span>|<span data-ttu-id="84e86-113">说明</span><span class="sxs-lookup"><span data-stu-id="84e86-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="84e86-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="84e86-114">S_OK</span></span>|<span data-ttu-id="84e86-115">已返回 `celt` 元素。</span><span class="sxs-lookup"><span data-stu-id="84e86-115">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="84e86-116">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="84e86-116">S_FALSE</span></span>|<span data-ttu-id="84e86-117">返回的元素少于 `celt` 个，表示枚举已完成。</span><span class="sxs-lookup"><span data-stu-id="84e86-117">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="84e86-118">要求</span><span class="sxs-lookup"><span data-stu-id="84e86-118">Requirements</span></span>  

 <span data-ttu-id="84e86-119">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="84e86-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84e86-120">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="84e86-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="84e86-121">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="84e86-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84e86-122">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84e86-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84e86-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="84e86-123">See also</span></span>

- [<span data-ttu-id="84e86-124">ICorProfilerModuleEnum 接口</span><span class="sxs-lookup"><span data-stu-id="84e86-124">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="84e86-125">分析接口</span><span class="sxs-lookup"><span data-stu-id="84e86-125">Profiling Interfaces</span></span>](profiling-interfaces.md)
