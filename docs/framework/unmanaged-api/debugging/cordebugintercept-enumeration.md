---
description: 了解详细信息： CorDebugIntercept 枚举
title: CorDebugIntercept 枚举
ms.date: 03/30/2017
api_name:
- CorDebugIntercept
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugIntercept
helpviewer_keywords:
- CorDebugIntercept enumeration [.NET Framework debugging]
ms.assetid: 3d5b642e-7ef2-428b-a5ae-509c35ed461a
topic_type:
- apiref
ms.openlocfilehash: ddd17aff309396fdcda37c731ff907224ee17db2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661969"
---
# <a name="cordebugintercept-enumeration"></a><span data-ttu-id="a53da-103">CorDebugIntercept 枚举</span><span class="sxs-lookup"><span data-stu-id="a53da-103">CorDebugIntercept Enumeration</span></span>

<span data-ttu-id="a53da-104">指示可截获（即可单步执行）的代码的类型。</span><span class="sxs-lookup"><span data-stu-id="a53da-104">Indicates the types of code that can be intercepted (that is, stepped into).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a53da-105">语法</span><span class="sxs-lookup"><span data-stu-id="a53da-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugIntercept {  
    INTERCEPT_NONE                = 0x0,  
    INTERCEPT_CLASS_INIT          = 0x01,  
    INTERCEPT_EXCEPTION_FILTER    = 0x02,  
    INTERCEPT_SECURITY            = 0x04,  
    INTERCEPT_CONTEXT_POLICY      = 0x08,  
    INTERCEPT_INTERCEPTION        = 0x10,  
    INTERCEPT_ALL                 = 0xffff  
} CorDebugIntercept;  
```  
  
## <a name="members"></a><span data-ttu-id="a53da-106">成员</span><span class="sxs-lookup"><span data-stu-id="a53da-106">Members</span></span>  
  
|<span data-ttu-id="a53da-107">成员</span><span class="sxs-lookup"><span data-stu-id="a53da-107">Member</span></span>|<span data-ttu-id="a53da-108">说明</span><span class="sxs-lookup"><span data-stu-id="a53da-108">Description</span></span>|  
|------------|-----------------|  
|`INTERCEPT_NONE`|<span data-ttu-id="a53da-109">未截获任何代码。</span><span class="sxs-lookup"><span data-stu-id="a53da-109">No code can be intercepted.</span></span>|  
|`INTERCEPT_CLASS_INIT`|<span data-ttu-id="a53da-110">可以截获构造函数。</span><span class="sxs-lookup"><span data-stu-id="a53da-110">A constructor can be intercepted.</span></span>|  
|`INTERCEPT_EXCEPTION_FILTER`|<span data-ttu-id="a53da-111">可以截获异常筛选器。</span><span class="sxs-lookup"><span data-stu-id="a53da-111">An exception filter can be intercepted.</span></span>|  
|`INTERCEPT_SECURITY`|<span data-ttu-id="a53da-112">可以截获强制保护的代码。</span><span class="sxs-lookup"><span data-stu-id="a53da-112">Code that enforces security can be intercepted.</span></span>|  
|`INTERCEPT_CONTEXT_POLICY`|<span data-ttu-id="a53da-113">可以截获上下文策略。</span><span class="sxs-lookup"><span data-stu-id="a53da-113">A context policy can be intercepted.</span></span>|  
|`INTERCEPT_INTERCEPTION`|<span data-ttu-id="a53da-114">未使用。</span><span class="sxs-lookup"><span data-stu-id="a53da-114">Not used.</span></span>|  
|`INTERCEPT_ALL`|<span data-ttu-id="a53da-115">可以截获所有代码。</span><span class="sxs-lookup"><span data-stu-id="a53da-115">All code can be intercepted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a53da-116">备注</span><span class="sxs-lookup"><span data-stu-id="a53da-116">Remarks</span></span>  

 <span data-ttu-id="a53da-117">使用 [ICorDebugStepper：： SetInterceptMask](icordebugstepper-setinterceptmask-method.md) 方法来建立可以截获的代码类型。</span><span class="sxs-lookup"><span data-stu-id="a53da-117">Use the [ICorDebugStepper::SetInterceptMask](icordebugstepper-setinterceptmask-method.md) method to establish the types of code that can be intercepted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a53da-118">要求</span><span class="sxs-lookup"><span data-stu-id="a53da-118">Requirements</span></span>  

 <span data-ttu-id="a53da-119">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a53da-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a53da-120">**标头**：CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a53da-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a53da-121">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a53da-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a53da-122">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a53da-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a53da-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="a53da-123">See also</span></span>

- [<span data-ttu-id="a53da-124">调试枚举</span><span class="sxs-lookup"><span data-stu-id="a53da-124">Debugging Enumerations</span></span>](debugging-enumerations.md)
