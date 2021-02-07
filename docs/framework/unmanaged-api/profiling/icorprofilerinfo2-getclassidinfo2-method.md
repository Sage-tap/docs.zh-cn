---
description: 了解详细信息： ICorProfilerInfo2：： GetClassIDInfo2 方法
title: ICorProfilerInfo2::GetClassIDInfo2 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassIDInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassIDInfo2
helpviewer_keywords:
- GetClassIDInfo2 method [.NET Framework profiling]
- ICorProfilerInfo2::GetClassIDInfo2 method [.NET Framework profiling]
ms.assetid: 0141d582-d066-4d49-8d1f-ae82129a1960
topic_type:
- apiref
ms.openlocfilehash: 44ef38b5f50da0f0aea045bd755614e00dae8c22
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760472"
---
# <a name="icorprofilerinfo2getclassidinfo2-method"></a><span data-ttu-id="1063b-103">ICorProfilerInfo2::GetClassIDInfo2 方法</span><span class="sxs-lookup"><span data-stu-id="1063b-103">ICorProfilerInfo2::GetClassIDInfo2 Method</span></span>

<span data-ttu-id="1063b-104">获取指定类的开放式泛型定义的父模块和元数据标记、 `ClassID` 其父类的，以及 `ClassID` 每个类型参数（如果存在）的。</span><span class="sxs-lookup"><span data-stu-id="1063b-104">Gets the parent module and metadata token for the open generic definition of the specified class, the `ClassID` of its parent class, and the `ClassID` for each type argument, if present, of the class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1063b-105">语法</span><span class="sxs-lookup"><span data-stu-id="1063b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetClassIDInfo2(  
    [in]  ClassID classId,  
    [out] ModuleID *pModuleId,  
    [out] mdTypeDef *pTypeDefToken,  
    [out] ClassID *pParentClassId,  
    [in]  ULONG32 cNumTypeArgs,  
    [out] ULONG32 *pcNumTypeArgs,  
    [out] ClassID typeArgs[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1063b-106">参数</span><span class="sxs-lookup"><span data-stu-id="1063b-106">Parameters</span></span>  

 `classId`  
 <span data-ttu-id="1063b-107">[in] 将为其检索信息的类的 ID。</span><span class="sxs-lookup"><span data-stu-id="1063b-107">[in] The ID of the class for which information will be retrieved.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="1063b-108">弄指向指定类的开放式泛型定义的父模块 ID 的指针。</span><span class="sxs-lookup"><span data-stu-id="1063b-108">[out] Pointer to the ID of the parent module for the open generic definition of the specified class.</span></span>  
  
 `pTypeDefToken`  
 <span data-ttu-id="1063b-109">弄指向指定类的开放式泛型定义的元数据标记的指针。</span><span class="sxs-lookup"><span data-stu-id="1063b-109">[out] Pointer to the metadata token for the open generic definition of the specified class.</span></span>  
  
 `pParentClassId`  
 <span data-ttu-id="1063b-110">[out] 指向父类 ID 的指针。</span><span class="sxs-lookup"><span data-stu-id="1063b-110">[out] Pointer to the ID of the parent class.</span></span>  
  
 `cNumTypeArgs`  
 <span data-ttu-id="1063b-111">[in] `typeArgs` 数组的大小。</span><span class="sxs-lookup"><span data-stu-id="1063b-111">[in] The size of the `typeArgs` array.</span></span>  
  
 `pcNumTypeArgs`  
 <span data-ttu-id="1063b-112">[out] 指向可用元素总数的指针。</span><span class="sxs-lookup"><span data-stu-id="1063b-112">[out] Pointer to the total number of available elements.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="1063b-113">[out] `ClassID` 值的数组，其中每个值表示类的类型参数 ID。</span><span class="sxs-lookup"><span data-stu-id="1063b-113">[out] An array of `ClassID` values, each of which represents the ID of a type argument of the class.</span></span> <span data-ttu-id="1063b-114">方法返回时，`typeArgs` 将包含部分或全部可用 `ClassID` 值。</span><span class="sxs-lookup"><span data-stu-id="1063b-114">When the method returns, `typeArgs` will contain some or all the available `ClassID` values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1063b-115">备注</span><span class="sxs-lookup"><span data-stu-id="1063b-115">Remarks</span></span>  

 <span data-ttu-id="1063b-116">`GetClassIDInfo2`方法类似于[ICorProfilerInfo：： GetClassIDInfo](icorprofilerinfo-getclassidinfo-method.md)方法，但 `GetClassIDInfo2` 获取有关泛型类型的其他信息。</span><span class="sxs-lookup"><span data-stu-id="1063b-116">The `GetClassIDInfo2` method is similar to the [ICorProfilerInfo::GetClassIDInfo](icorprofilerinfo-getclassidinfo-method.md) method, but `GetClassIDInfo2` obtains additional information about a generic type.</span></span>  
  
 <span data-ttu-id="1063b-117">探查器代码可调用 [ICorProfilerInfo：： GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) 以获取给定模块的 [元数据](../metadata/index.md) 接口。</span><span class="sxs-lookup"><span data-stu-id="1063b-117">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) to obtain a [metadata](../metadata/index.md) interface for a given module.</span></span> <span data-ttu-id="1063b-118">返回至 `pTypeDefToken` 所引用的位置的元数据标记可用于访问类的元数据。</span><span class="sxs-lookup"><span data-stu-id="1063b-118">The metadata token that is returned to the location referenced by `pTypeDefToken` can then be used to access the metadata for the class.</span></span>  
  
 <span data-ttu-id="1063b-119">`GetClassIDInfo2` 返回后，必须验证 `typeArgs` 缓冲区是否足够大，可包含所有 `ClassID` 值。</span><span class="sxs-lookup"><span data-stu-id="1063b-119">After `GetClassIDInfo2` returns, you must verify that the `typeArgs` buffer was large enough to contain all the `ClassID` values.</span></span> <span data-ttu-id="1063b-120">为此，请比较 `pcNumTypeArgs` 指向的值和 `cNumTypeArgs` 参数的值。</span><span class="sxs-lookup"><span data-stu-id="1063b-120">To do this, compare the value that `pcNumTypeArgs` points to with the value of the `cNumTypeArgs` parameter.</span></span> <span data-ttu-id="1063b-121">如果 `pcNumTypeArgs` 指向的值大于 `cNumTypeArgs`，请分配更大的 `typeArgs` 缓冲区，并用新的、更大的大小更新 `cNumTypeArgs`，然后再次调用 `GetClassIDInfo2`。</span><span class="sxs-lookup"><span data-stu-id="1063b-121">If `pcNumTypeArgs` points to a value that is larger than `cNumTypeArgs`, allocate a larger `typeArgs` buffer, update `cNumTypeArgs` with the new, larger size, and call `GetClassIDInfo2` again.</span></span>  
  
 <span data-ttu-id="1063b-122">或者，可以先用长度为零的 `typeArgs` 缓冲区调用 `GetClassIDInfo2` 以获取正确的缓冲区大小。</span><span class="sxs-lookup"><span data-stu-id="1063b-122">Alternatively, you can first call `GetClassIDInfo2` with a zero-length `typeArgs` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="1063b-123">然后，可将 `typeArgs` 缓冲区大小设置为 `pcNumTypeArgs` 中返回的值，并再次调用 `GetClassIDInfo2`。</span><span class="sxs-lookup"><span data-stu-id="1063b-123">You can then set the `typeArgs` buffer size to the value returned in `pcNumTypeArgs` and call `GetClassIDInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1063b-124">要求</span><span class="sxs-lookup"><span data-stu-id="1063b-124">Requirements</span></span>  

 <span data-ttu-id="1063b-125">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1063b-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1063b-126">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1063b-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1063b-127">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1063b-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1063b-128">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1063b-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1063b-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="1063b-129">See also</span></span>

- [<span data-ttu-id="1063b-130">ICorProfilerInfo 接口</span><span class="sxs-lookup"><span data-stu-id="1063b-130">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="1063b-131">ICorProfilerInfo2 接口</span><span class="sxs-lookup"><span data-stu-id="1063b-131">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
- [<span data-ttu-id="1063b-132">分析接口</span><span class="sxs-lookup"><span data-stu-id="1063b-132">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="1063b-133">分析</span><span class="sxs-lookup"><span data-stu-id="1063b-133">Profiling</span></span>](index.md)
