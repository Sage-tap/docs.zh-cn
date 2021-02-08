---
description: 了解详细信息： EClrOperation 枚举
title: EClrOperation 枚举
ms.date: 03/30/2017
api_name:
- EClrOperation
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrOperation
helpviewer_keywords:
- EClrOperation enumeration [.NET Framework hosting]
ms.assetid: 5aef6808-5aac-4b2f-a2c7-fee1575c55ed
topic_type:
- apiref
ms.openlocfilehash: 9f75762a400955b5f36fb2a337f283e36a32658c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785557"
---
# <a name="eclroperation-enumeration"></a><span data-ttu-id="309e7-103">EClrOperation 枚举</span><span class="sxs-lookup"><span data-stu-id="309e7-103">EClrOperation Enumeration</span></span>

<span data-ttu-id="309e7-104">描述主机可对其应用策略操作的一组操作。</span><span class="sxs-lookup"><span data-stu-id="309e7-104">Describes the set of operations for which a host can apply policy actions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="309e7-105">语法</span><span class="sxs-lookup"><span data-stu-id="309e7-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    OPR_ThreadAbort,  
    OPR_ThreadRudeAbortInNonCriticalRegion,  
    OPR_ThreadRudeAbortInCriticalRegion,  
    OPR_AppDomainUnload,  
    OPR_AppDomainRudeUnload,  
    OPR_ProcessExit,  
    OPR_FinalizerRun  
} EClrOperation;  
```  
  
## <a name="members"></a><span data-ttu-id="309e7-106">成员</span><span class="sxs-lookup"><span data-stu-id="309e7-106">Members</span></span>  
  
|<span data-ttu-id="309e7-107">成员</span><span class="sxs-lookup"><span data-stu-id="309e7-107">Member</span></span>|<span data-ttu-id="309e7-108">说明</span><span class="sxs-lookup"><span data-stu-id="309e7-108">Description</span></span>|  
|------------|-----------------|  
|`OPR_AppDomainRudeUnload`|<span data-ttu-id="309e7-109">当 <xref:System.AppDomain> 以非正常 (强制) 方式卸载时，主机可以指定要执行的策略操作。</span><span class="sxs-lookup"><span data-stu-id="309e7-109">The host can specify policy actions to be taken when an <xref:System.AppDomain> is unloaded in a non-graceful (rude) manner.</span></span>|  
|`OPR_AppDomainUnload`|<span data-ttu-id="309e7-110">宿主可以指定卸载时要执行的策略操作 <xref:System.AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="309e7-110">The host can specify policy actions to be taken when an <xref:System.AppDomain> is unloaded.</span></span>|  
|`OPR_FinalizerRun`|<span data-ttu-id="309e7-111">主机可以指定在终结器运行时执行的策略操作。</span><span class="sxs-lookup"><span data-stu-id="309e7-111">The host can specify policy actions to be taken when finalizers run.</span></span>|  
|`OPR_ProcessExit`|<span data-ttu-id="309e7-112">宿主可以指定在进程退出时要执行的策略操作。</span><span class="sxs-lookup"><span data-stu-id="309e7-112">The host can specify policy actions to be taken when the process exits.</span></span>|  
|`OPR_ThreadAbort`|<span data-ttu-id="309e7-113">宿主可以指定在线程中止时要执行的策略操作。</span><span class="sxs-lookup"><span data-stu-id="309e7-113">The host can specify policy actions to be taken when a thread is aborted.</span></span>|  
|`OPR_ThreadRudeAbortInCriticalRegion`|<span data-ttu-id="309e7-114">宿主可以指定在关键代码区域发生强制线程中止时要执行的策略操作。</span><span class="sxs-lookup"><span data-stu-id="309e7-114">The host can specify policy actions to be taken when a rude thread abort occurs in a critical region of code.</span></span>|  
|`OPR_ThreadRudeAbortInNonCriticalRegion`|<span data-ttu-id="309e7-115">宿主可以指定在非关键代码区域发生强制线程中止时要执行的策略操作。</span><span class="sxs-lookup"><span data-stu-id="309e7-115">The host can specify policy actions to be take when a rude thread abort occurs in a non-critical region of code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="309e7-116">备注</span><span class="sxs-lookup"><span data-stu-id="309e7-116">Remarks</span></span>  

 <span data-ttu-id="309e7-117">公共语言运行时 (CLR) 可靠性基础结构区分关键代码区域发生的中止和资源分配失败，以及在非关键代码区域发生的失败。</span><span class="sxs-lookup"><span data-stu-id="309e7-117">The common language runtime (CLR) reliability infrastructure distinguishes between aborts and resource allocation failures that occur in critical regions of code and those that occur in non-critical regions of code.</span></span> <span data-ttu-id="309e7-118">这种区别旨在允许主机根据代码中发生故障的位置设置不同的策略。</span><span class="sxs-lookup"><span data-stu-id="309e7-118">This distinction is designed to allow hosts to set different policies depending on where a failure occurs in the code.</span></span>  
  
 <span data-ttu-id="309e7-119">*关键代码区域* 是指 CLR 无法保证中止任务或未能完成资源请求的任何空间都将只影响当前任务。</span><span class="sxs-lookup"><span data-stu-id="309e7-119">A *critical region of code* is any space where the CLR cannot guarantee that aborting a task or failing to complete a request for resources will affect only the current task.</span></span> <span data-ttu-id="309e7-120">例如，如果某个任务持有锁，并且收到一个 HRESULT，指示在发出内存分配请求时失败，则只需中止该任务以确保的稳定性 <xref:System.AppDomain> ，因为 <xref:System.AppDomain> 可能包含其他等待同一锁的任务。</span><span class="sxs-lookup"><span data-stu-id="309e7-120">For example, if a task is holding a lock and receives an HRESULT that indicates failure upon making a memory allocation request, it is insufficient simply to abort that task to ensure the stability of the <xref:System.AppDomain>, because the <xref:System.AppDomain> might contain other tasks waiting for the same lock.</span></span> <span data-ttu-id="309e7-121">放弃当前任务可能会导致其他任务停止响应。</span><span class="sxs-lookup"><span data-stu-id="309e7-121">To abandon the current task might cause those other tasks to stop responding.</span></span> <span data-ttu-id="309e7-122">在这种情况下，主机需要能够卸载整个 <xref:System.AppDomain> 而不是风险潜在的不稳定。</span><span class="sxs-lookup"><span data-stu-id="309e7-122">In such a case, the host needs the ability to unload the entire <xref:System.AppDomain> rather than risk potential instability.</span></span>  
  
 <span data-ttu-id="309e7-123">另一方面， *非关键的代码区域* 是一个区域，在此区域中，CLR 可以保证中止或失败只会影响发生错误的任务。</span><span class="sxs-lookup"><span data-stu-id="309e7-123">A *non-critical region of code*, on the other hand, is a region where the CLR can guarantee that an abort or a failure will affect only the task upon which the error occurs.</span></span>  
  
 <span data-ttu-id="309e7-124">CLR 还可以区分正常和不正常 (强制) 中止。</span><span class="sxs-lookup"><span data-stu-id="309e7-124">The CLR also distinguishes between graceful and non-graceful (rude) aborts.</span></span> <span data-ttu-id="309e7-125">通常情况下，正常或正常中止会使每个工作在中止任务之前运行异常处理例程和终结器，而强制中止则不会有这样的保证。</span><span class="sxs-lookup"><span data-stu-id="309e7-125">In general, a normal or graceful abort makes every effort to run exception-handling routines and finalizers before aborting a task, while a rude abort makes no such guarantees.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="309e7-126">要求</span><span class="sxs-lookup"><span data-stu-id="309e7-126">Requirements</span></span>  

 <span data-ttu-id="309e7-127">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="309e7-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="309e7-128">**标头：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="309e7-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="309e7-129">**库：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="309e7-129">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="309e7-130">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="309e7-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="309e7-131">请参阅</span><span class="sxs-lookup"><span data-stu-id="309e7-131">See also</span></span>

- [<span data-ttu-id="309e7-132">EClrFailure 枚举</span><span class="sxs-lookup"><span data-stu-id="309e7-132">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="309e7-133">EPolicyAction 枚举</span><span class="sxs-lookup"><span data-stu-id="309e7-133">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="309e7-134">ICLRPolicyManager 接口</span><span class="sxs-lookup"><span data-stu-id="309e7-134">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="309e7-135">IHostPolicyManager 接口</span><span class="sxs-lookup"><span data-stu-id="309e7-135">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
- [<span data-ttu-id="309e7-136">承载枚举</span><span class="sxs-lookup"><span data-stu-id="309e7-136">Hosting Enumerations</span></span>](hosting-enumerations.md)
