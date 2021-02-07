---
description: 了解详细信息： IHostMemoryManager：： VirtualQuery 方法
title: IHostMemoryManager::VirtualQuery 方法
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualQuery
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualQuery
helpviewer_keywords:
- IHostMemoryManager::VirtualQuery method [.NET Framework hosting]
- VirtualQuery method [.NET Framework hosting]
ms.assetid: 757af1e6-b9e8-49e7-b5db-342be3aa205f
topic_type:
- apiref
ms.openlocfilehash: 8518ef71ad7d493fa04d4e2321f1f90ef8ecd18d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707489"
---
# <a name="ihostmemorymanagervirtualquery-method"></a><span data-ttu-id="fce36-103">IHostMemoryManager::VirtualQuery 方法</span><span class="sxs-lookup"><span data-stu-id="fce36-103">IHostMemoryManager::VirtualQuery Method</span></span>

<span data-ttu-id="fce36-104">用作相应 Win32 函数的逻辑包装。</span><span class="sxs-lookup"><span data-stu-id="fce36-104">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="fce36-105">的 Win32 实现 `VirtualQuery` 检索有关调用进程的虚拟地址空间中的页范围的信息。</span><span class="sxs-lookup"><span data-stu-id="fce36-105">The Win32 implementation of `VirtualQuery` retrieves information about a range of pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fce36-106">语法</span><span class="sxs-lookup"><span data-stu-id="fce36-106">Syntax</span></span>  
  
```cpp  
HRESULT VirtualQuery (  
    [in]  void*    lpAddress,  
    [out] void*    lpBuffer,  
    [in]  SIZE_T   dwLength,  
    [out] SIZE_T*  pResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fce36-107">参数</span><span class="sxs-lookup"><span data-stu-id="fce36-107">Parameters</span></span>  

 `lpAddress`  
 <span data-ttu-id="fce36-108">中指向要查询的虚拟内存中的地址的指针。</span><span class="sxs-lookup"><span data-stu-id="fce36-108">[in] A pointer to the address in virtual memory to be queried.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="fce36-109">弄指向结构的指针，该结构包含有关指定的内存区域的信息。</span><span class="sxs-lookup"><span data-stu-id="fce36-109">[out] A pointer to a structure that contains information about the specified memory region.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="fce36-110">中指向的缓冲区的大小（以字节为单位） `lpBuffer` 。</span><span class="sxs-lookup"><span data-stu-id="fce36-110">[in] The size, in bytes, of the buffer that `lpBuffer` points to.</span></span>  
  
 `pResult`  
 <span data-ttu-id="fce36-111">弄指向信息缓冲区返回的字节数的指针。</span><span class="sxs-lookup"><span data-stu-id="fce36-111">[out] A pointer to the number of bytes returned by the information buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fce36-112">返回值</span><span class="sxs-lookup"><span data-stu-id="fce36-112">Return Value</span></span>  
  
|<span data-ttu-id="fce36-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fce36-113">HRESULT</span></span>|<span data-ttu-id="fce36-114">说明</span><span class="sxs-lookup"><span data-stu-id="fce36-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fce36-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="fce36-115">S_OK</span></span>|<span data-ttu-id="fce36-116">`VirtualQuery` 已成功返回。</span><span class="sxs-lookup"><span data-stu-id="fce36-116">`VirtualQuery` returned successfully.</span></span>|  
|<span data-ttu-id="fce36-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fce36-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fce36-118"> (CLR) 的公共语言运行时未加载到进程中，或 CLR 处于无法运行托管代码或成功处理调用的状态。</span><span class="sxs-lookup"><span data-stu-id="fce36-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fce36-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fce36-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fce36-120">调用超时。</span><span class="sxs-lookup"><span data-stu-id="fce36-120">The call timed out.</span></span>|  
|<span data-ttu-id="fce36-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fce36-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fce36-122">调用方不拥有该锁。</span><span class="sxs-lookup"><span data-stu-id="fce36-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fce36-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fce36-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fce36-124">已阻止的线程或纤程正在等待某个事件时，该事件被取消。</span><span class="sxs-lookup"><span data-stu-id="fce36-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fce36-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fce36-125">E_FAIL</span></span>|<span data-ttu-id="fce36-126">发生未知的灾难性故障。</span><span class="sxs-lookup"><span data-stu-id="fce36-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fce36-127">当方法返回 E_FAIL 时，CLR 在该进程内将不再可用。</span><span class="sxs-lookup"><span data-stu-id="fce36-127">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fce36-128">对宿主方法的后续调用会返回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="fce36-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fce36-129">备注</span><span class="sxs-lookup"><span data-stu-id="fce36-129">Remarks</span></span>  

 <span data-ttu-id="fce36-130">`VirtualQuery` 提供有关调用进程的虚拟地址空间中的页范围的信息。</span><span class="sxs-lookup"><span data-stu-id="fce36-130">`VirtualQuery` provides information about a range of pages in the virtual address space of the calling process.</span></span> <span data-ttu-id="fce36-131">此实现将参数的值设置 `pResult` 为信息缓冲区中返回的字节数，并返回一个 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="fce36-131">This implementation sets the value of the `pResult` parameter to the number of bytes returned in the information buffer, and returns an HRESULT value.</span></span> <span data-ttu-id="fce36-132">在 Win32 `VirtualQuery` 函数中，返回值为缓冲区大小。</span><span class="sxs-lookup"><span data-stu-id="fce36-132">In the Win32 `VirtualQuery` function, the return value is the buffer size.</span></span> <span data-ttu-id="fce36-133">有关详细信息，请参阅 Windows 平台文档。</span><span class="sxs-lookup"><span data-stu-id="fce36-133">For more information, see the Windows Platform documentation.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="fce36-134">操作系统的实现 `VirtualQuery` 不会导致死锁，并且可以运行到完成，并在用户代码中挂起随机线程。</span><span class="sxs-lookup"><span data-stu-id="fce36-134">The operating system's implementation of `VirtualQuery` does not incur deadlock and can run to completion with random threads suspended in user code.</span></span> <span data-ttu-id="fce36-135">实现此方法的承载版本时要格外小心。</span><span class="sxs-lookup"><span data-stu-id="fce36-135">Use great caution when implementing a hosted version of this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fce36-136">要求</span><span class="sxs-lookup"><span data-stu-id="fce36-136">Requirements</span></span>  

 <span data-ttu-id="fce36-137">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fce36-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fce36-138">**标头：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="fce36-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fce36-139">**库：** 作为中的资源包含 MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fce36-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fce36-140">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fce36-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fce36-141">请参阅</span><span class="sxs-lookup"><span data-stu-id="fce36-141">See also</span></span>

- [<span data-ttu-id="fce36-142">IHostMemoryManager 接口</span><span class="sxs-lookup"><span data-stu-id="fce36-142">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
