---
description: 了解详细信息： ICorDebugNativeFrame 接口
title: ICorDebugNativeFrame 接口
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame
helpviewer_keywords:
- ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 04819c58-7246-4b32-befb-680cf1dbc436
topic_type:
- apiref
ms.openlocfilehash: e417184c9f1ca5136e1b4dba07820fd8242ae932
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729128"
---
# <a name="icordebugnativeframe-interface"></a><span data-ttu-id="a8faf-103">ICorDebugNativeFrame 接口</span><span class="sxs-lookup"><span data-stu-id="a8faf-103">ICorDebugNativeFrame Interface</span></span>

<span data-ttu-id="a8faf-104">用于本机帧的 ICorDebugFrame 的专用实现。</span><span class="sxs-lookup"><span data-stu-id="a8faf-104">A specialized implementation of ICorDebugFrame used for native frames.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a8faf-105">方法</span><span class="sxs-lookup"><span data-stu-id="a8faf-105">Methods</span></span>  
  
|<span data-ttu-id="a8faf-106">方法</span><span class="sxs-lookup"><span data-stu-id="a8faf-106">Method</span></span>|<span data-ttu-id="a8faf-107">说明</span><span class="sxs-lookup"><span data-stu-id="a8faf-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a8faf-108">CanSetIP 方法</span><span class="sxs-lookup"><span data-stu-id="a8faf-108">CanSetIP Method</span></span>](icordebugnativeframe-cansetip-method.md)|<span data-ttu-id="a8faf-109">获取一个值，该值指示是否可以安全地将指令指针设置为本机代码中的指定偏移位置。</span><span class="sxs-lookup"><span data-stu-id="a8faf-109">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location in native code.</span></span>|  
|[<span data-ttu-id="a8faf-110">GetIP 方法</span><span class="sxs-lookup"><span data-stu-id="a8faf-110">GetIP Method</span></span>](icordebugnativeframe-getip-method.md)|<span data-ttu-id="a8faf-111">获取堆栈帧到本机代码的偏移量。</span><span class="sxs-lookup"><span data-stu-id="a8faf-111">Gets the stack frame's offset into native code.</span></span>|  
|[<span data-ttu-id="a8faf-112">GetLocalDoubleRegisterValue 方法</span><span class="sxs-lookup"><span data-stu-id="a8faf-112">GetLocalDoubleRegisterValue Method</span></span>](icordebugnativeframe-getlocaldoubleregistervalue-method.md)|<span data-ttu-id="a8faf-113">获取一个指向 ICorDebugValue 的指针，该指针表示存储在本机帧的两个内存寄存器中的参数或局部变量的值。</span><span class="sxs-lookup"><span data-stu-id="a8faf-113">Gets a pointer to an ICorDebugValue that represents the value of an argument or local variable stored in two memory registers of a native frame.</span></span>|  
|[<span data-ttu-id="a8faf-114">GetLocalMemoryRegisterValue 方法</span><span class="sxs-lookup"><span data-stu-id="a8faf-114">GetLocalMemoryRegisterValue Method</span></span>](icordebugnativeframe-getlocalmemoryregistervalue-method.md)|<span data-ttu-id="a8faf-115">获取一个指向的指针， `ICorDebugValue` 该指针表示本地变量的值，其中低位存储在指定的寄存器中，高位存储于指定的内存地址。</span><span class="sxs-lookup"><span data-stu-id="a8faf-115">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the low bits are stored in the specified register and the high bits are stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="a8faf-116">GetLocalMemoryValue 方法</span><span class="sxs-lookup"><span data-stu-id="a8faf-116">GetLocalMemoryValue Method</span></span>](icordebugnativeframe-getlocalmemoryvalue-method.md)|<span data-ttu-id="a8faf-117">获取一个指向的指针 `ICorDebugValue` ，该指针表示存储在指定内存地址中的局部变量的值。</span><span class="sxs-lookup"><span data-stu-id="a8faf-117">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="a8faf-118">GetLocalRegisterMemoryValue 方法</span><span class="sxs-lookup"><span data-stu-id="a8faf-118">GetLocalRegisterMemoryValue Method</span></span>](icordebugnativeframe-getlocalregistermemoryvalue-method.md)|<span data-ttu-id="a8faf-119">获取一个指向的指针， `ICorDebugValue` 该指针表示本地变量的值，其中高位存储在指定的寄存器中，低位存储在指定的内存地址</span><span class="sxs-lookup"><span data-stu-id="a8faf-119">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the high bits are stored in the specified register and the low bits are stored at the specified memory address</span></span>|  
|[<span data-ttu-id="a8faf-120">GetLocalRegisterValue 方法</span><span class="sxs-lookup"><span data-stu-id="a8faf-120">GetLocalRegisterValue Method</span></span>](icordebugnativeframe-getlocalregistervalue-method.md)|<span data-ttu-id="a8faf-121">获取一个指向的指针 `ICorDebugValue` ，该指针表示存储在指定本机寄存器中的参数或局部变量的值。</span><span class="sxs-lookup"><span data-stu-id="a8faf-121">Gets a pointer to an `ICorDebugValue` that represents the value of an argument or a local variable stored in the specified native register.</span></span>|  
|[<span data-ttu-id="a8faf-122">GetRegisterSet 方法</span><span class="sxs-lookup"><span data-stu-id="a8faf-122">GetRegisterSet Method</span></span>](icordebugnativeframe-getregisterset-method.md)|<span data-ttu-id="a8faf-123">获取一个指针，该指针指向表示此的注册集的 [ICorDebugRegisterSet](icordebugregisterset-interface.md) `ICorDebugNativeFrame` 。</span><span class="sxs-lookup"><span data-stu-id="a8faf-123">Gets a pointer to an [ICorDebugRegisterSet](icordebugregisterset-interface.md) that represents the register set for this `ICorDebugNativeFrame`.</span></span>|  
|[<span data-ttu-id="a8faf-124">SetIP 方法</span><span class="sxs-lookup"><span data-stu-id="a8faf-124">SetIP Method</span></span>](icordebugnativeframe-setip-method.md)|<span data-ttu-id="a8faf-125">将指令指针设置为本机代码中的指定偏移位置。</span><span class="sxs-lookup"><span data-stu-id="a8faf-125">Sets the instruction pointer to the specified offset location in native code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8faf-126">备注</span><span class="sxs-lookup"><span data-stu-id="a8faf-126">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a8faf-127">此接口不支持跨计算机或跨进程远程调用。</span><span class="sxs-lookup"><span data-stu-id="a8faf-127">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8faf-128">要求</span><span class="sxs-lookup"><span data-stu-id="a8faf-128">Requirements</span></span>  

 <span data-ttu-id="a8faf-129">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a8faf-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8faf-130">**标头**：CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a8faf-130">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a8faf-131">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a8faf-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8faf-132">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8faf-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8faf-133">请参阅</span><span class="sxs-lookup"><span data-stu-id="a8faf-133">See also</span></span>

- [<span data-ttu-id="a8faf-134">调试接口</span><span class="sxs-lookup"><span data-stu-id="a8faf-134">Debugging Interfaces</span></span>](debugging-interfaces.md)
