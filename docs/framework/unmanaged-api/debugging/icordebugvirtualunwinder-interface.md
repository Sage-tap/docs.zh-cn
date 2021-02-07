---
description: 了解详细信息： ICorDebugVirtualUnwinder 接口
title: ICorDebugVirtualUnwinder 接口
ms.date: 03/30/2017
ms.assetid: a09e9ccc-0b37-43e3-95c1-bc5fa7ee5f42
ms.openlocfilehash: e941ace2e7f72c9f7956c03bae19f9b92094b338
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738073"
---
# <a name="icordebugvirtualunwinder-interface"></a><span data-ttu-id="80785-103">ICorDebugVirtualUnwinder 接口</span><span class="sxs-lookup"><span data-stu-id="80785-103">ICorDebugVirtualUnwinder Interface</span></span>

<span data-ttu-id="80785-104">提供帮助堆栈展开的方法。</span><span class="sxs-lookup"><span data-stu-id="80785-104">Provides methods to help in stack unwinding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="80785-105">方法</span><span class="sxs-lookup"><span data-stu-id="80785-105">Methods</span></span>  
  
|<span data-ttu-id="80785-106">方法</span><span class="sxs-lookup"><span data-stu-id="80785-106">Method</span></span>|<span data-ttu-id="80785-107">名称</span><span class="sxs-lookup"><span data-stu-id="80785-107">Name</span></span>|  
|------------|----------|  
|[<span data-ttu-id="80785-108">GetContext 方法</span><span class="sxs-lookup"><span data-stu-id="80785-108">GetContext Method</span></span>](icordebugvirtualunwinder-getcontext-method.md)|<span data-ttu-id="80785-109">获取此展开器的当前上下文。</span><span class="sxs-lookup"><span data-stu-id="80785-109">Gets the current context of this unwinder.</span></span>|  
|[<span data-ttu-id="80785-110">下一方法</span><span class="sxs-lookup"><span data-stu-id="80785-110">Next Method</span></span>](icordebugvirtualunwinder-next-method.md)|<span data-ttu-id="80785-111">前进到调用方的上下文。</span><span class="sxs-lookup"><span data-stu-id="80785-111">Advances to the caller's context.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80785-112">备注</span><span class="sxs-lookup"><span data-stu-id="80785-112">Remarks</span></span>  

 <span data-ttu-id="80785-113">`ICorDebugVirtualUnwinder` 接口的成员由调试器来实现，从而在堆栈展开中提供帮助。</span><span class="sxs-lookup"><span data-stu-id="80785-113">The members of the `ICorDebugVirtualUnwinder` interface are implemented by the debugger to help in stack unwinding.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="80785-114">此接口仅适用于 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="80785-114">This interface is available with .NET Native only.</span></span> <span data-ttu-id="80785-115">如果在 .NET Native 外为 ICorDebug 方案实现此接口，则公共语言运行时将忽略此接口。</span><span class="sxs-lookup"><span data-stu-id="80785-115">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80785-116">要求</span><span class="sxs-lookup"><span data-stu-id="80785-116">Requirements</span></span>  

 <span data-ttu-id="80785-117">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="80785-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80785-118">**标头**：CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="80785-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="80785-119">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="80785-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="80785-120">**.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80785-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80785-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="80785-121">See also</span></span>

- [<span data-ttu-id="80785-122">调试接口</span><span class="sxs-lookup"><span data-stu-id="80785-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="80785-123">调试</span><span class="sxs-lookup"><span data-stu-id="80785-123">Debugging</span></span>](index.md)
