---
description: 了解详细信息： ICorDebugStepper：： Step 方法
title: ICorDebugStepper::Step 方法
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.Step
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::Step
helpviewer_keywords:
- Step method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::Step method [.NET Framework debugging]
ms.assetid: 38c1940b-ada1-40ba-8295-4c0833744e1e
topic_type:
- apiref
ms.openlocfilehash: cb45575f7818784addf67eacda35442764e706af
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717623"
---
# <a name="icordebugstepperstep-method"></a><span data-ttu-id="a6433-103">ICorDebugStepper::Step 方法</span><span class="sxs-lookup"><span data-stu-id="a6433-103">ICorDebugStepper::Step Method</span></span>

<span data-ttu-id="a6433-104">使此 ICorDebugStepper 单步执行其包含线程，并根据需要继续单步执行线程中调用的函数。</span><span class="sxs-lookup"><span data-stu-id="a6433-104">Causes this ICorDebugStepper to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6433-105">语法</span><span class="sxs-lookup"><span data-stu-id="a6433-105">Syntax</span></span>  
  
```cpp  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6433-106">参数</span><span class="sxs-lookup"><span data-stu-id="a6433-106">Parameters</span></span>  

 `bStepIn`  
 <span data-ttu-id="a6433-107">中设置为 `true` 可单步执行在线程中调用的函数。</span><span class="sxs-lookup"><span data-stu-id="a6433-107">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="a6433-108">设置为 `false` 以逐过程执行函数。</span><span class="sxs-lookup"><span data-stu-id="a6433-108">Set to `false` to step over the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6433-109">备注</span><span class="sxs-lookup"><span data-stu-id="a6433-109">Remarks</span></span>  

 <span data-ttu-id="a6433-110">当公共语言运行时执行此分档器帧中的下一个托管指令时，此步骤即告完成。</span><span class="sxs-lookup"><span data-stu-id="a6433-110">The step completes when the common language runtime performs the next managed instruction in this stepper's frame.</span></span> <span data-ttu-id="a6433-111">如果 `Step` 在不在托管代码中的分档器上调用，则在线程执行下一个托管代码指令时，步骤将完成。</span><span class="sxs-lookup"><span data-stu-id="a6433-111">If `Step` is called on a stepper, which is not in managed code, the step will complete when the next managed code instruction is executed by the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6433-112">要求</span><span class="sxs-lookup"><span data-stu-id="a6433-112">Requirements</span></span>  

 <span data-ttu-id="a6433-113">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a6433-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6433-114">**标头**：CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a6433-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a6433-115">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a6433-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6433-116">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6433-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
