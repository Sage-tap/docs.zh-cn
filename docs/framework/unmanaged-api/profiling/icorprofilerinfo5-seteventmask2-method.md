---
description: 了解详细信息： ICorProfilerInfo5：： SetEventMask2 方法
title: ICorProfilerInfo5::SetEventMask2 方法
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- IcorProfilerInfo5.SetEventMask2
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 05dbbe2b-049c-4a60-be69-2ad7a949405e
topic_type:
- apiref
ms.openlocfilehash: 2928ec408f2fdeb363164530258a3bf5c9719e2b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799000"
---
# <a name="icorprofilerinfo5seteventmask2-method"></a><span data-ttu-id="62470-103">ICorProfilerInfo5::SetEventMask2 方法</span><span class="sxs-lookup"><span data-stu-id="62470-103">ICorProfilerInfo5::SetEventMask2 Method</span></span>

<span data-ttu-id="62470-104">[仅在 .NET Framework 4.5.2 及更高版本中受支持]</span><span class="sxs-lookup"><span data-stu-id="62470-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="62470-105">设置一个值，用于指定探查器需要从公共语言运行时 (CLR) 接收其事件通知的事件的类型。</span><span class="sxs-lookup"><span data-stu-id="62470-105">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the common language runtime (CLR).</span></span> <span data-ttu-id="62470-106">它提供的功能比 [ICorProfilerInfo：： SetEventMask](icorprofilerinfo-seteventmask-method.md) 方法更多。</span><span class="sxs-lookup"><span data-stu-id="62470-106">It provides more functionality than the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62470-107">语法</span><span class="sxs-lookup"><span data-stu-id="62470-107">Syntax</span></span>  
  
```cpp
HRESULT SetEventMask2(        [in] DWORD dwEventsLow,        [in] DWORD dwEventsHigh  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="62470-108">参数</span><span class="sxs-lookup"><span data-stu-id="62470-108">Parameters</span></span>  

 `dwEventsLow`  
 <span data-ttu-id="62470-109">[in] 一个指定事件类别的 4 字节的值。</span><span class="sxs-lookup"><span data-stu-id="62470-109">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="62470-110">每个位都可控制不同的功能、行为或事件类型。</span><span class="sxs-lookup"><span data-stu-id="62470-110">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="62470-111">[COR_PRF_MONITOR](cor-prf-monitor-enumeration.md)枚举中描述了这些位。</span><span class="sxs-lookup"><span data-stu-id="62470-111">The bits are described in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 `dwEventsHigh`  
 <span data-ttu-id="62470-112">[in] 一个指定事件类别的 4 字节的值。</span><span class="sxs-lookup"><span data-stu-id="62470-112">[in] A 4-byte value that specifies the categories of events.</span></span>  <span data-ttu-id="62470-113">每个位都可控制不同的功能、行为或事件类型。</span><span class="sxs-lookup"><span data-stu-id="62470-113">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="62470-114">[COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md)枚举中描述了这些位。</span><span class="sxs-lookup"><span data-stu-id="62470-114">The bits are described in the [COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62470-115">备注</span><span class="sxs-lookup"><span data-stu-id="62470-115">Remarks</span></span>  

 <span data-ttu-id="62470-116">`SetEventMask2` 方法用于设置探查器订阅的回调。</span><span class="sxs-lookup"><span data-stu-id="62470-116">The `SetEventMask2` method is used to set the callbacks to which the profiler subscribes.</span></span> <span data-ttu-id="62470-117">通常，你可以调用 [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) 方法来确定设置了哪些位，对其 `pdwEventsLow` 和 `pdwEventsHigh` 值以及要设置的任何新位执行逻辑 "或"，然后调用 `SetEventMask2` 方法。</span><span class="sxs-lookup"><span data-stu-id="62470-117">Typically, you call the [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) method to determine which bits are set, perform a logical OR of its `pdwEventsLow` and `pdwEventsHigh` values and any new bits you want to set, and then call the `SetEventMask2` method.</span></span>  
  
 <span data-ttu-id="62470-118">此方法是 [SetEventMask](icorprofilerinfo-seteventmask-method.md) 方法的建议替代方法。</span><span class="sxs-lookup"><span data-stu-id="62470-118">This method is the recommended alternative to the [SetEventMask](icorprofilerinfo-seteventmask-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62470-119">要求</span><span class="sxs-lookup"><span data-stu-id="62470-119">Requirements</span></span>  

 <span data-ttu-id="62470-120">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="62470-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62470-121">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="62470-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="62470-122">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="62470-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62470-123">**.NET Framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62470-123">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62470-124">请参阅</span><span class="sxs-lookup"><span data-stu-id="62470-124">See also</span></span>

- [<span data-ttu-id="62470-125">ICorProfilerInfo5 接口</span><span class="sxs-lookup"><span data-stu-id="62470-125">ICorProfilerInfo5 Interface</span></span>](icorprofilerinfo5-interface.md)
- [<span data-ttu-id="62470-126">GetEventMask2 方法</span><span class="sxs-lookup"><span data-stu-id="62470-126">GetEventMask2 Method</span></span>](icorprofilerinfo5-geteventmask2-method.md)
