---
description: 了解详细信息： ICoreClrDebugTarget：： FreeMemory 方法
title: ICoreClrDebugTarget::FreeMemory 方法
ms.date: 03/30/2017
api_name:
- ICoreDebugTarget.FreeMemory
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget::FreeMemory
helpviewer_keywords:
- remote debugging API [Silverlight]
- FreeMemory method, ICoreClrDebugTarget interface [Silverlight debugging]
- ICorClrDebugTarget::FreeMemory method [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: 98f2a0db-a6ec-4f9b-861d-f82485237d08
topic_type:
- apiref
ms.openlocfilehash: 9572e0c3df1fdd064e78ba170d39c1415c68dc85
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689997"
---
# <a name="icoreclrdebugtargetfreememory-method"></a><span data-ttu-id="94daa-103">ICoreClrDebugTarget::FreeMemory 方法</span><span class="sxs-lookup"><span data-stu-id="94daa-103">ICoreClrDebugTarget::FreeMemory Method</span></span>

<span data-ttu-id="94daa-104">释放由 [ICoreClrDebugTarget：： EnumProcesses](icoreclrdebugtarget-enumprocesses-method.md) 和 [ICoreClrDebugTarget：： EnumRuntimes](icoreclrdebugtarget-enumruntimes-method.md) 方法分配的内存。</span><span class="sxs-lookup"><span data-stu-id="94daa-104">Frees the memory allocated by the [ICoreClrDebugTarget::EnumProcesses](icoreclrdebugtarget-enumprocesses-method.md) and [ICoreClrDebugTarget::EnumRuntimes](icoreclrdebugtarget-enumruntimes-method.md) methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94daa-105">语法</span><span class="sxs-lookup"><span data-stu-id="94daa-105">Syntax</span></span>  
  
```cpp  
void FreeMemory (  
     [in] void*pMemory);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94daa-106">参数</span><span class="sxs-lookup"><span data-stu-id="94daa-106">Parameters</span></span>  

 `pMemory`  
 <span data-ttu-id="94daa-107">中指向由 [ICoreClrDebugTarget：： EnumProcesses](icoreclrdebugtarget-enumprocesses-method.md) 或 [ICoreClrDebugTarget：： EnumRuntimes](icoreclrdebugtarget-enumruntimes-method.md) 方法返回的数组的指针。</span><span class="sxs-lookup"><span data-stu-id="94daa-107">[in] A pointer to the array that is returned by either the [ICoreClrDebugTarget::EnumProcesses](icoreclrdebugtarget-enumprocesses-method.md) or the [ICoreClrDebugTarget::EnumRuntimes](icoreclrdebugtarget-enumruntimes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94daa-108">要求</span><span class="sxs-lookup"><span data-stu-id="94daa-108">Requirements</span></span>  

 <span data-ttu-id="94daa-109">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="94daa-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94daa-110">**标头：** CoreClrRemoteDebuggingInterfaces</span><span class="sxs-lookup"><span data-stu-id="94daa-110">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="94daa-111">**库：** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="94daa-111">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="94daa-112">**.NET Framework 版本：** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="94daa-112">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94daa-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="94daa-113">See also</span></span>

- [<span data-ttu-id="94daa-114">ICoreClrDebugTarget 接口</span><span class="sxs-lookup"><span data-stu-id="94daa-114">ICoreClrDebugTarget Interface</span></span>](icoreclrdebugtarget-interface.md)
