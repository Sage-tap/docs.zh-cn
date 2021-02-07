---
description: 了解详细信息： ICorDebugProcess：： WriteMemory 方法
title: ICorDebugProcess::WriteMemory 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.WriteMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::WriteMemory
helpviewer_keywords:
- ICorDebugProcess::WriteMemory method [.NET Framework debugging]
- WriteMemory method [.NET Framework debugging]
ms.assetid: d5c07d86-045d-4391-893b-0bcd2959f90e
topic_type:
- apiref
ms.openlocfilehash: 6ea48aff2e1ea812d851a228976b458f58a60e14
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746615"
---
# <a name="icordebugprocesswritememory-method"></a><span data-ttu-id="a997d-103">ICorDebugProcess::WriteMemory 方法</span><span class="sxs-lookup"><span data-stu-id="a997d-103">ICorDebugProcess::WriteMemory Method</span></span>

<span data-ttu-id="a997d-104">将数据写入到此进程中的内存区域。</span><span class="sxs-lookup"><span data-stu-id="a997d-104">Writes data to an area of memory in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a997d-105">语法</span><span class="sxs-lookup"><span data-stu-id="a997d-105">Syntax</span></span>  
  
```cpp  
HRESULT WriteMemory(  
    [in]  CORDB_ADDRESS address,  
    [in]  DWORD size,  
    [in, size_is(size)] BYTE buffer[],  
    [out] SIZE_T *written);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a997d-106">参数</span><span class="sxs-lookup"><span data-stu-id="a997d-106">Parameters</span></span>  

 `address`  
 <span data-ttu-id="a997d-107">中一个 `CORDB_ADDRESS` 值，该值是写入数据的内存区域的基址。</span><span class="sxs-lookup"><span data-stu-id="a997d-107">[in] A `CORDB_ADDRESS` value that is the base address of the memory area to which data is written.</span></span> <span data-ttu-id="a997d-108">在进行数据传输之前，系统将验证指定大小（从基址开始）的内存区域是否可供写入。</span><span class="sxs-lookup"><span data-stu-id="a997d-108">Before data transfer occurs, the system verifies that the memory area of the specified size, beginning at the base address, is accessible for writing.</span></span> <span data-ttu-id="a997d-109">如果不可访问，则该方法将失败。</span><span class="sxs-lookup"><span data-stu-id="a997d-109">If it is not accessible, the method fails.</span></span>  
  
 `size`  
 <span data-ttu-id="a997d-110">中要写入内存区域的字节数。</span><span class="sxs-lookup"><span data-stu-id="a997d-110">[in] The number of bytes to be written to the memory area.</span></span>  
  
 `buffer`  
 <span data-ttu-id="a997d-111">中包含要写入的数据的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="a997d-111">[in] A buffer that contains data to be written.</span></span>  
  
 `written`  
 <span data-ttu-id="a997d-112">弄指向一个变量的指针，该变量接收写入到此进程中的内存区域的字节数。</span><span class="sxs-lookup"><span data-stu-id="a997d-112">[out] A pointer to a variable that receives the number of bytes written to the memory area in this process.</span></span> <span data-ttu-id="a997d-113">如果 `written` 为 NULL，则忽略此参数。</span><span class="sxs-lookup"><span data-stu-id="a997d-113">If `written` is NULL, this parameter is ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a997d-114">备注</span><span class="sxs-lookup"><span data-stu-id="a997d-114">Remarks</span></span>  

 <span data-ttu-id="a997d-115">数据将在任何断点后面自动写入。</span><span class="sxs-lookup"><span data-stu-id="a997d-115">Data is automatically written behind any breakpoints.</span></span> <span data-ttu-id="a997d-116">在 .NET Framework 版本2.0 中，本机调试器不应使用此方法将断点注入到指令流中。</span><span class="sxs-lookup"><span data-stu-id="a997d-116">In the .NET Framework version 2.0, native debuggers should not use this method to inject breakpoints into the instruction stream.</span></span> <span data-ttu-id="a997d-117">改 [为使用 ICorDebugProcess2：： SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md) 。</span><span class="sxs-lookup"><span data-stu-id="a997d-117">Use [ICorDebugProcess2::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md) instead.</span></span>  
  
 <span data-ttu-id="a997d-118">`WriteMemory`方法只应在托管代码之外使用。</span><span class="sxs-lookup"><span data-stu-id="a997d-118">The `WriteMemory` method should be used only outside of managed code.</span></span> <span data-ttu-id="a997d-119">如果使用不当，此方法可能会损坏运行时。</span><span class="sxs-lookup"><span data-stu-id="a997d-119">This method can corrupt the runtime if used improperly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a997d-120">要求</span><span class="sxs-lookup"><span data-stu-id="a997d-120">Requirements</span></span>  

 <span data-ttu-id="a997d-121">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a997d-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a997d-122">**标头**：CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a997d-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a997d-123">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a997d-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a997d-124">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a997d-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
