---
description: 了解详细信息： ICLRTaskManager：： CreateTask 方法
title: ICLRTaskManager::CreateTask 方法
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.CreateTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::CreateTask
helpviewer_keywords:
- ICLRTaskManager::CreateTask method [.NET Framework hosting]
- CreateTask method, ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: eea570d9-2e53-4320-9ea0-eb777bf9dcf3
topic_type:
- apiref
ms.openlocfilehash: 98a287f10a84b18579ebf2a4294cbb8a67cabc9c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728608"
---
# <a name="iclrtaskmanagercreatetask-method"></a><span data-ttu-id="d3cd5-103">ICLRTaskManager::CreateTask 方法</span><span class="sxs-lookup"><span data-stu-id="d3cd5-103">ICLRTaskManager::CreateTask Method</span></span>

<span data-ttu-id="d3cd5-104">显式请求公共语言运行时 (CLR) 创建新任务。</span><span class="sxs-lookup"><span data-stu-id="d3cd5-104">Requests explicitly that the common language runtime (CLR) create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3cd5-105">语法</span><span class="sxs-lookup"><span data-stu-id="d3cd5-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateTask (  
    [out] ICLRTask **pTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3cd5-106">参数</span><span class="sxs-lookup"><span data-stu-id="d3cd5-106">Parameters</span></span>  

 `pTask`  
 <span data-ttu-id="d3cd5-107">弄指向新创建的 [ICLRTask](iclrtask-interface.md)的地址的指针; 如果无法创建任务，则为 null。</span><span class="sxs-lookup"><span data-stu-id="d3cd5-107">[out] A pointer to the address of a newly created [ICLRTask](iclrtask-interface.md), or null, if the task could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d3cd5-108">返回值</span><span class="sxs-lookup"><span data-stu-id="d3cd5-108">Return Value</span></span>  
  
|<span data-ttu-id="d3cd5-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d3cd5-109">HRESULT</span></span>|<span data-ttu-id="d3cd5-110">说明</span><span class="sxs-lookup"><span data-stu-id="d3cd5-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d3cd5-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d3cd5-111">S_OK</span></span>|<span data-ttu-id="d3cd5-112">该方法已成功返回。</span><span class="sxs-lookup"><span data-stu-id="d3cd5-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="d3cd5-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d3cd5-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d3cd5-114">CLR 未加载到进程中，或 CLR 处于无法运行托管代码或成功处理调用的状态。</span><span class="sxs-lookup"><span data-stu-id="d3cd5-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d3cd5-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d3cd5-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d3cd5-116">调用超时。</span><span class="sxs-lookup"><span data-stu-id="d3cd5-116">The call timed out.</span></span>|  
|<span data-ttu-id="d3cd5-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d3cd5-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d3cd5-118">调用方不拥有该锁。</span><span class="sxs-lookup"><span data-stu-id="d3cd5-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d3cd5-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d3cd5-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d3cd5-120">已阻止的线程或纤程正在等待某个事件时，该事件被取消。</span><span class="sxs-lookup"><span data-stu-id="d3cd5-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d3cd5-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d3cd5-121">E_FAIL</span></span>|<span data-ttu-id="d3cd5-122">发生未知的灾难性故障。</span><span class="sxs-lookup"><span data-stu-id="d3cd5-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d3cd5-123">当方法返回 E_FAIL 时，CLR 在该进程内将不再可用。</span><span class="sxs-lookup"><span data-stu-id="d3cd5-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d3cd5-124">对宿主方法的后续调用会返回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="d3cd5-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d3cd5-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="d3cd5-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="d3cd5-126">没有足够的内存可用于分配请求的资源。</span><span class="sxs-lookup"><span data-stu-id="d3cd5-126">Not enough memory is available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3cd5-127">备注</span><span class="sxs-lookup"><span data-stu-id="d3cd5-127">Remarks</span></span>  

 <span data-ttu-id="d3cd5-128">当用户代码通过使用命名空间中的类型创建线程时 <xref:System.Threading> ，或者当线程池的大小增加时，CLR 将自动创建一个新任务。</span><span class="sxs-lookup"><span data-stu-id="d3cd5-128">The CLR creates a new task automatically upon initialization, when user code creates a thread by using types in the <xref:System.Threading> namespace, or when the size of the thread pool is increased.</span></span> <span data-ttu-id="d3cd5-129">当非托管代码调用托管函数时，它还会创建任务。</span><span class="sxs-lookup"><span data-stu-id="d3cd5-129">It also creates tasks when unmanaged code makes a call to a managed function.</span></span>  
  
 <span data-ttu-id="d3cd5-130">`CreateTask` 允许宿主发出显式请求，指示 CLR 创建了一个新的任务。</span><span class="sxs-lookup"><span data-stu-id="d3cd5-130">`CreateTask` allows the host to make an explicit request that the CLR create a new task.</span></span> <span data-ttu-id="d3cd5-131">例如，宿主可以调用此方法来预先初始化数据结构。</span><span class="sxs-lookup"><span data-stu-id="d3cd5-131">For example, the host can invoke this method to preinitialize data structures.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d3cd5-132">新任务在挂起状态返回，并保持挂起状态，直到主机显式调用 [IHostTask：： Start](ihosttask-start-method.md)。</span><span class="sxs-lookup"><span data-stu-id="d3cd5-132">The new task is returned in a suspended state and remains suspended until the host explicitly calls [IHostTask::Start](ihosttask-start-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3cd5-133">要求</span><span class="sxs-lookup"><span data-stu-id="d3cd5-133">Requirements</span></span>  

 <span data-ttu-id="d3cd5-134">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d3cd5-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3cd5-135">**标头：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="d3cd5-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d3cd5-136">**库：** 作为中的资源包含 MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d3cd5-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d3cd5-137">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3cd5-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3cd5-138">请参阅</span><span class="sxs-lookup"><span data-stu-id="d3cd5-138">See also</span></span>

- [<span data-ttu-id="d3cd5-139">ICLRTask 接口</span><span class="sxs-lookup"><span data-stu-id="d3cd5-139">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="d3cd5-140">ICLRTaskManager 接口</span><span class="sxs-lookup"><span data-stu-id="d3cd5-140">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="d3cd5-141">IHostTask 接口</span><span class="sxs-lookup"><span data-stu-id="d3cd5-141">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="d3cd5-142">IHostTaskManager 接口</span><span class="sxs-lookup"><span data-stu-id="d3cd5-142">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
