---
description: 了解详细信息： ICLRValidator：： FormatEventInfo 方法
title: ICLRValidator::FormatEventInfo 方法
ms.date: 03/30/2017
api_name:
- ICLRValidator.FormatEventInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRValidator::FormatEventInfo
helpviewer_keywords:
- FormatEventInfo method, ICLRValidator interface [.NET Framework hosting]
- ICLRValidator::FormatEventInfo method [.NET Framework hosting]
ms.assetid: 808e1f1d-52f4-47c4-83cc-dcf47d075219
topic_type:
- apiref
ms.openlocfilehash: 3d8d1eff8c638517e201905d0313ee824490acf4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636762"
---
# <a name="iclrvalidatorformateventinfo-method"></a><span data-ttu-id="bebc7-103">ICLRValidator::FormatEventInfo 方法</span><span class="sxs-lookup"><span data-stu-id="bebc7-103">ICLRValidator::FormatEventInfo Method</span></span>

<span data-ttu-id="bebc7-104">获取有关指定验证错误的详细消息。</span><span class="sxs-lookup"><span data-stu-id="bebc7-104">Gets a detailed message about the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bebc7-105">语法</span><span class="sxs-lookup"><span data-stu-id="bebc7-105">Syntax</span></span>  
  
```cpp  
HRESULT FormatEventInfo (  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bebc7-106">参数</span><span class="sxs-lookup"><span data-stu-id="bebc7-106">Parameters</span></span>  

 `hVECode`  
 <span data-ttu-id="bebc7-107">中传递给验证错误处理程序的 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="bebc7-107">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="bebc7-108">中一个 `VEContext` 实例，其中包含有关验证错误的上下文信息。</span><span class="sxs-lookup"><span data-stu-id="bebc7-108">[in] A `VEContext` instance that contains context information about the validation errors.</span></span>  
  
 `msg`  
 <span data-ttu-id="bebc7-109">[in，out]友好的错误消息。</span><span class="sxs-lookup"><span data-stu-id="bebc7-109">[in, out] The friendly error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="bebc7-110">中错误消息的最大长度。</span><span class="sxs-lookup"><span data-stu-id="bebc7-110">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="bebc7-111">中要在消息中使用的其他参数的安全数组。</span><span class="sxs-lookup"><span data-stu-id="bebc7-111">[in] A safe array of additional parameters to be used in the message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bebc7-112">返回值</span><span class="sxs-lookup"><span data-stu-id="bebc7-112">Return Value</span></span>  
  
|<span data-ttu-id="bebc7-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bebc7-113">HRESULT</span></span>|<span data-ttu-id="bebc7-114">说明</span><span class="sxs-lookup"><span data-stu-id="bebc7-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bebc7-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="bebc7-115">S_OK</span></span>|<span data-ttu-id="bebc7-116">`FormatEventInfo` 已成功返回。</span><span class="sxs-lookup"><span data-stu-id="bebc7-116">`FormatEventInfo` returned successfully.</span></span>|  
|<span data-ttu-id="bebc7-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bebc7-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bebc7-118"> (CLR) 的公共语言运行时未加载到进程中，或 CLR 处于无法运行托管代码或成功处理调用的状态。</span><span class="sxs-lookup"><span data-stu-id="bebc7-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bebc7-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bebc7-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bebc7-120">调用超时。</span><span class="sxs-lookup"><span data-stu-id="bebc7-120">The call timed out.</span></span>|  
|<span data-ttu-id="bebc7-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bebc7-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bebc7-122">调用方不拥有该锁。</span><span class="sxs-lookup"><span data-stu-id="bebc7-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bebc7-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bebc7-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bebc7-124">已阻止的线程或纤程正在等待某个事件时，该事件被取消。</span><span class="sxs-lookup"><span data-stu-id="bebc7-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bebc7-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bebc7-125">E_FAIL</span></span>|<span data-ttu-id="bebc7-126">发生未知的灾难性故障。</span><span class="sxs-lookup"><span data-stu-id="bebc7-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bebc7-127">当方法返回 E_FAIL 时，CLR 在该进程内将不再可用。</span><span class="sxs-lookup"><span data-stu-id="bebc7-127">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bebc7-128">对宿主方法的后续调用会返回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="bebc7-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bebc7-129">要求</span><span class="sxs-lookup"><span data-stu-id="bebc7-129">Requirements</span></span>  

 <span data-ttu-id="bebc7-130">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bebc7-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bebc7-131">**标头：** IValidator，IValidator</span><span class="sxs-lookup"><span data-stu-id="bebc7-131">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="bebc7-132">**库：** 作为中的资源包含 MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bebc7-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bebc7-133">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bebc7-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bebc7-134">请参阅</span><span class="sxs-lookup"><span data-stu-id="bebc7-134">See also</span></span>

- [<span data-ttu-id="bebc7-135">ICLRErrorReportingManager 接口</span><span class="sxs-lookup"><span data-stu-id="bebc7-135">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="bebc7-136">ICLRValidator 接口</span><span class="sxs-lookup"><span data-stu-id="bebc7-136">ICLRValidator Interface</span></span>](iclrvalidator-interface.md)
