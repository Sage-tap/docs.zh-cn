---
description: 了解详细信息： ICorDebugNativeFrame：： CanSetIP 方法
title: ICorDebugNativeFrame::CanSetIP 方法
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.CanSetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::CanSetIP
helpviewer_keywords:
- ICorDebugNativeFrame::CanSetIP method [.NET Framework debugging]
- CanSetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 13258ac6-f4e4-4f66-8fc3-f1244417a3c3
topic_type:
- apiref
ms.openlocfilehash: ec8f257b44143332063d7579b62dcc2afe0fccdd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637835"
---
# <a name="icordebugnativeframecansetip-method"></a><span data-ttu-id="6b0b9-103">ICorDebugNativeFrame::CanSetIP 方法</span><span class="sxs-lookup"><span data-stu-id="6b0b9-103">ICorDebugNativeFrame::CanSetIP Method</span></span>

<span data-ttu-id="6b0b9-104">获取 HRESULT，它指示是否可以安全地将指令指针 (IP) 设置为本机代码中的指定偏移位置。</span><span class="sxs-lookup"><span data-stu-id="6b0b9-104">Gets an HRESULT that indicates whether it is safe to set the instruction pointer (IP) to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b0b9-105">语法</span><span class="sxs-lookup"><span data-stu-id="6b0b9-105">Syntax</span></span>  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32            nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b0b9-106">参数</span><span class="sxs-lookup"><span data-stu-id="6b0b9-106">Parameters</span></span>  

 `nOffset`  
 <span data-ttu-id="6b0b9-107">中指令指针所需的设置。</span><span class="sxs-lookup"><span data-stu-id="6b0b9-107">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b0b9-108">备注</span><span class="sxs-lookup"><span data-stu-id="6b0b9-108">Remarks</span></span>  

 <span data-ttu-id="6b0b9-109">在 `CanSetIP` 调用 [ICorDebugNativeFrame：： SetIP](icordebugnativeframe-setip-method.md) 方法之前，请使用方法。</span><span class="sxs-lookup"><span data-stu-id="6b0b9-109">Use the `CanSetIP` method prior to calling the [ICorDebugNativeFrame::SetIP](icordebugnativeframe-setip-method.md) method.</span></span> <span data-ttu-id="6b0b9-110">如果 `CanSetIP` 返回除 S_OK 以外的任何 HRESULT，则仍可调用 `ICorDebugNativeFrame::SetIP` ，但是无法保证调试器将继续安全且正确地执行正在调试的代码。</span><span class="sxs-lookup"><span data-stu-id="6b0b9-110">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugNativeFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b0b9-111">要求</span><span class="sxs-lookup"><span data-stu-id="6b0b9-111">Requirements</span></span>  

 <span data-ttu-id="6b0b9-112">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6b0b9-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b0b9-113">**标头**：CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6b0b9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6b0b9-114">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b0b9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b0b9-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b0b9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b0b9-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="6b0b9-116">See also</span></span>
