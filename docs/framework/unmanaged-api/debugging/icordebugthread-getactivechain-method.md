---
description: 了解详细信息： ICorDebugThread：： GetActiveChain 方法
title: ICorDebugThread::GetActiveChain 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetActiveChain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetActiveChain
helpviewer_keywords:
- ICorDebugThread::GetActiveChain method [.NET Framework debugging]
- GetActiveChain method [.NET Framework debugging]
ms.assetid: f50de1f7-40ef-4949-b542-1d9a61f7bfef
topic_type:
- apiref
ms.openlocfilehash: d9aff80801fa72a227a84b3b5216e3ffa72b0e24
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659262"
---
# <a name="icordebugthreadgetactivechain-method"></a><span data-ttu-id="46565-103">ICorDebugThread::GetActiveChain 方法</span><span class="sxs-lookup"><span data-stu-id="46565-103">ICorDebugThread::GetActiveChain Method</span></span>

<span data-ttu-id="46565-104">获取一个接口指针，该指针指向此 ICorDebugThread 对象上的活动 (最新) 堆栈链。</span><span class="sxs-lookup"><span data-stu-id="46565-104">Gets an interface pointer to the active (most recent) stack chain on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46565-105">语法</span><span class="sxs-lookup"><span data-stu-id="46565-105">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveChain (  
    [out] ICorDebugChain **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="46565-106">参数</span><span class="sxs-lookup"><span data-stu-id="46565-106">Parameters</span></span>  

 `ppChain`  
 <span data-ttu-id="46565-107">弄指向表示堆栈链的 ICorDebugChain 对象地址的指针。</span><span class="sxs-lookup"><span data-stu-id="46565-107">[out] A pointer to the address of an ICorDebugChain object that represents the stack chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46565-108">备注</span><span class="sxs-lookup"><span data-stu-id="46565-108">Remarks</span></span>  

 <span data-ttu-id="46565-109">`ppChain`如果当前没有堆栈链处于活动状态，则参数为 null。</span><span class="sxs-lookup"><span data-stu-id="46565-109">The `ppChain` parameter is null if no stack chain is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46565-110">要求</span><span class="sxs-lookup"><span data-stu-id="46565-110">Requirements</span></span>  

 <span data-ttu-id="46565-111">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="46565-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46565-112">**标头**：CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="46565-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="46565-113">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="46565-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46565-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46565-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
