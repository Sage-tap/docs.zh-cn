---
description: 了解详细信息： ICorProfilerInfo3：： GetRuntimeInformation 方法
title: ICorProfilerInfo3::GetRuntimeInformation 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetRuntimeInformation Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetRuntimeInformation
helpviewer_keywords:
- GetRuntimeInformation method [.NET Framework profiling]
- ICorProfilerInfo3::GetRuntimeInformation method [.NET Framework profiling]
ms.assetid: 4400fb8c-0407-4791-8557-f011fd2aee51
topic_type:
- apiref
ms.openlocfilehash: f615cc54e12b6f2f6eaa7335353f2f5f6a8ecfce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646707"
---
# <a name="icorprofilerinfo3getruntimeinformation-method"></a><span data-ttu-id="1709f-103">ICorProfilerInfo3::GetRuntimeInformation 方法</span><span class="sxs-lookup"><span data-stu-id="1709f-103">ICorProfilerInfo3::GetRuntimeInformation Method</span></span>

<span data-ttu-id="1709f-104">提供有关正在分析的 (CLR) 的公共语言运行时的版本信息。</span><span class="sxs-lookup"><span data-stu-id="1709f-104">Provides version information about the common language runtime (CLR) that is being profiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1709f-105">语法</span><span class="sxs-lookup"><span data-stu-id="1709f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRuntimeInformation(  
       [out] USHORT *pClrInstanceId,  
       [out] COR_PRF_RUNTIME_TYPE *pRuntimeType,  
       [out] USHORT *pMajorVersion,  
       [out] USHORT *pMinorVersion,  
       [out] USHORT *pBuildNumber,  
       [out] USHORT *pQFEVersion,  
       [in]  ULONG  cchVersionString,  
       [out] ULONG  *pcchVersionString,  
       [out, size_is(cchVersionString), length_is(*pcchVersionString)]  
                   WCHAR  szVersionString[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1709f-106">参数</span><span class="sxs-lookup"><span data-stu-id="1709f-106">Parameters</span></span>  

 `pClrInstanceId`  
 <span data-ttu-id="1709f-107">弄进程中正在运行的 CLR 实例的代表 ID。</span><span class="sxs-lookup"><span data-stu-id="1709f-107">[out] The representative ID of a running CLR instance in a process.</span></span> <span data-ttu-id="1709f-108">这与 `ClrInstanceID` Windows 事件跟踪 (ETW) 启动事件报告相同。</span><span class="sxs-lookup"><span data-stu-id="1709f-108">This is the same as the `ClrInstanceID` that the event tracing for Windows (ETW) startup event reports.</span></span>  
  
 `pRuntimeType`  
 <span data-ttu-id="1709f-109">弄运行时类型。</span><span class="sxs-lookup"><span data-stu-id="1709f-109">[out] The runtime type.</span></span> <span data-ttu-id="1709f-110">此参数 `COR_PRF_DESKTOP_CLR` 为 clr 的桌面版本或 `COR_PRF_CORE_CLR` Silverlight 中使用的 clr 的核心版本返回。</span><span class="sxs-lookup"><span data-stu-id="1709f-110">This parameter returns `COR_PRF_DESKTOP_CLR` for the desktop version of the CLR, or `COR_PRF_CORE_CLR` for the core version of the CLR used in Silverlight.</span></span>  
  
 `pMajorVersion`  
 <span data-ttu-id="1709f-111">弄CLR 的主版本号。</span><span class="sxs-lookup"><span data-stu-id="1709f-111">[out] The major version number of the CLR.</span></span>  
  
 `pMinorVersion`  
 <span data-ttu-id="1709f-112">弄CLR 的次版本号。</span><span class="sxs-lookup"><span data-stu-id="1709f-112">[out] The minor version number of the CLR.</span></span>  
  
 `pBuildVersion`  
 <span data-ttu-id="1709f-113">弄CLR 的内部版本号。</span><span class="sxs-lookup"><span data-stu-id="1709f-113">[out] The build version number of the CLR.</span></span>  
  
 `pQFEVersion`  
 <span data-ttu-id="1709f-114">弄与软件更新关联的 CLR 的版本号。</span><span class="sxs-lookup"><span data-stu-id="1709f-114">[out] The version number of the CLR that is associated with a software update.</span></span>  
  
 `cchVersionString`  
 <span data-ttu-id="1709f-115">中指向的缓冲区的长度（以字符为单位） `szVersionString` 。</span><span class="sxs-lookup"><span data-stu-id="1709f-115">[in] The length, in characters, of the buffer that `szVersionString` points to.</span></span>  
  
 `pcchVersionString`  
 <span data-ttu-id="1709f-116">弄的长度，以字符为字符 `szVersionString` 。</span><span class="sxs-lookup"><span data-stu-id="1709f-116">[out] The length, in characters, of `szVersionString`.</span></span>  
  
 `szVersionString`  
 <span data-ttu-id="1709f-117">弄CLR 版本字符串。</span><span class="sxs-lookup"><span data-stu-id="1709f-117">[out] The CLR version string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1709f-118">备注</span><span class="sxs-lookup"><span data-stu-id="1709f-118">Remarks</span></span>  

 <span data-ttu-id="1709f-119">可以为任何参数传递 null。</span><span class="sxs-lookup"><span data-stu-id="1709f-119">You may pass null for any parameter.</span></span> <span data-ttu-id="1709f-120">但是， `pcchVersionString` 除非也为 null，否则不能为 null `szVersionString` 。</span><span class="sxs-lookup"><span data-stu-id="1709f-120">However, `pcchVersionString` cannot be null unless `szVersionString` is also null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1709f-121">要求</span><span class="sxs-lookup"><span data-stu-id="1709f-121">Requirements</span></span>  

 <span data-ttu-id="1709f-122">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1709f-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1709f-123">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1709f-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1709f-124">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1709f-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1709f-125">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1709f-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1709f-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="1709f-126">See also</span></span>

- [<span data-ttu-id="1709f-127">ICorProfilerInfo3 接口</span><span class="sxs-lookup"><span data-stu-id="1709f-127">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="1709f-128">分析接口</span><span class="sxs-lookup"><span data-stu-id="1709f-128">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="1709f-129">分析</span><span class="sxs-lookup"><span data-stu-id="1709f-129">Profiling</span></span>](index.md)
