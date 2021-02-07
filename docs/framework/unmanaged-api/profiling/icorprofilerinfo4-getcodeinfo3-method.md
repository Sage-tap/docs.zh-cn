---
description: 了解详细信息： ICorProfilerInfo4：： GetCodeInfo3 方法
title: ICorProfilerInfo4::GetCodeInfo3 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetCodeInfo3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetCodeInfo3
helpviewer_keywords:
- GetCodeInfo3 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetCodeInfo3 method [.NET Framework profiling]
ms.assetid: bb8c105e-4d9a-4684-8c05-ed6909cc1b8c
topic_type:
- apiref
ms.openlocfilehash: 6bc2beb291101257448ab58ac9a93362005fecbe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99686821"
---
# <a name="icorprofilerinfo4getcodeinfo3-method"></a><span data-ttu-id="ad33e-103">ICorProfilerInfo4::GetCodeInfo3 方法</span><span class="sxs-lookup"><span data-stu-id="ad33e-103">ICorProfilerInfo4::GetCodeInfo3 Method</span></span>

<span data-ttu-id="ad33e-104">获取本机代码的范围，该代码与指定函数的 JIT 重新编译版本相关联。</span><span class="sxs-lookup"><span data-stu-id="ad33e-104">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad33e-105">语法</span><span class="sxs-lookup"><span data-stu-id="ad33e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeInfo3(  
    [in]  FunctionID functionID,  
    [in]  ReJITID reJitId,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad33e-106">参数</span><span class="sxs-lookup"><span data-stu-id="ad33e-106">Parameters</span></span>  

 `functionID`  
 <span data-ttu-id="ad33e-107">[in] 与本机代码关联的函数的 ID。</span><span class="sxs-lookup"><span data-stu-id="ad33e-107">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `reJitId`  
 <span data-ttu-id="ad33e-108">[in] JIT 重新编译的函数的标识。</span><span class="sxs-lookup"><span data-stu-id="ad33e-108">[in] The identity of the JIT-recompiled function.</span></span>  
  
 `cCodeInfos`  
 <span data-ttu-id="ad33e-109">[in] `codeInfos` 数组的大小。</span><span class="sxs-lookup"><span data-stu-id="ad33e-109">[in] The size of the `codeInfos` array.</span></span>  
  
 `pcCodeInfos`  
 <span data-ttu-id="ad33e-110">弄指向可用 [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) 结构总数的指针。</span><span class="sxs-lookup"><span data-stu-id="ad33e-110">[out] A pointer to the total number of [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures available.</span></span>  
  
 `codeInfos`  
 <span data-ttu-id="ad33e-111">[out] 调用方提供的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="ad33e-111">[out] A caller-provided buffer.</span></span> <span data-ttu-id="ad33e-112">返回此方法后，它包含一个 `COR_PRF_CODE_INFO` 结构数组，每个结构描述一个本机代码块。</span><span class="sxs-lookup"><span data-stu-id="ad33e-112">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad33e-113">备注</span><span class="sxs-lookup"><span data-stu-id="ad33e-113">Remarks</span></span>  

 <span data-ttu-id="ad33e-114">`GetCodeInfo3`方法类似于[GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md)，只不过它将获取包含指定 IP 地址的函数的 JIT 重新编译的 ID。</span><span class="sxs-lookup"><span data-stu-id="ad33e-114">The `GetCodeInfo3` method is similar to [GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md), except that it will get the JIT-recompiled ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ad33e-115">`GetCodeInfo3` 可以触发垃圾回收，而 [GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md) 将不会触发垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="ad33e-115">`GetCodeInfo3` can trigger a garbage collection, whereas [GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md) will not.</span></span> <span data-ttu-id="ad33e-116">有关详细信息，请参阅 [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](corprof-e-unsupported-call-sequence-hresult.md) HRESULT。</span><span class="sxs-lookup"><span data-stu-id="ad33e-116">For more information, see the [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](corprof-e-unsupported-call-sequence-hresult.md) HRESULT.</span></span>  
  
 <span data-ttu-id="ad33e-117">范围按公共中间语言 (CIL) 偏移递增的顺序进行排序。</span><span class="sxs-lookup"><span data-stu-id="ad33e-117">The extents are sorted in order of increasing Common Intermediate Language (CIL) offset.</span></span>  
  
 <span data-ttu-id="ad33e-118">`GetCodeInfo3`返回后，必须验证 `codeInfos` 缓冲区大小是否足以包含所有[COR_PRF_CODE_INFO](cor-prf-code-info-structure.md)的结构。</span><span class="sxs-lookup"><span data-stu-id="ad33e-118">After `GetCodeInfo3` returns, you must verify that the `codeInfos` buffer was large enough to contain all the [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures.</span></span> <span data-ttu-id="ad33e-119">为此，请将 `cCodeInfos` 的值和 `cchName` 参数的值进行比较。</span><span class="sxs-lookup"><span data-stu-id="ad33e-119">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="ad33e-120">如果 `cCodeInfos` 除以 [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) 结构的大小小于 `pcCodeInfos` ，则分配更大的 `codeInfos` 缓冲区， `cCodeInfos` 用新的、更大的大小更新，然后再次调用 `GetCodeInfo3` 。</span><span class="sxs-lookup"><span data-stu-id="ad33e-120">If `cCodeInfos` divided by the size of a [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo3` again.</span></span>  
  
 <span data-ttu-id="ad33e-121">或者，可以先用长度为零的 `codeInfos` 缓冲区调用 `GetCodeInfo3` 以获取正确的缓冲区大小。</span><span class="sxs-lookup"><span data-stu-id="ad33e-121">Alternatively, you can first call `GetCodeInfo3` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="ad33e-122">然后，可以将 `codeInfos` 缓冲区大小设置为中返回的值 `pcCodeInfos` ，再乘以 [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) 结构的大小，然后 `GetCodeInfo3` 再次调用。</span><span class="sxs-lookup"><span data-stu-id="ad33e-122">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structure, and call `GetCodeInfo3` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad33e-123">要求</span><span class="sxs-lookup"><span data-stu-id="ad33e-123">Requirements</span></span>  

 <span data-ttu-id="ad33e-124">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ad33e-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad33e-125">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ad33e-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ad33e-126">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad33e-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad33e-127">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad33e-127">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad33e-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="ad33e-128">See also</span></span>

- [<span data-ttu-id="ad33e-129">GetCodeInfo2 方法</span><span class="sxs-lookup"><span data-stu-id="ad33e-129">GetCodeInfo2 Method</span></span>](icorprofilerinfo2-getcodeinfo2-method.md)
- [<span data-ttu-id="ad33e-130">ICorProfilerInfo4 接口</span><span class="sxs-lookup"><span data-stu-id="ad33e-130">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="ad33e-131">分析接口</span><span class="sxs-lookup"><span data-stu-id="ad33e-131">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="ad33e-132">分析</span><span class="sxs-lookup"><span data-stu-id="ad33e-132">Profiling</span></span>](index.md)
