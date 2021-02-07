---
description: 了解详细信息： ICorDebugChain：： GetReason 方法
title: ICorDebugChain::GetReason 方法
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- GetReason
helpviewer_keywords:
- GetReason method [.NET Framework debugging]
- ICorDebugChain::GetReason method [.NET Framework debugging]
ms.assetid: 9f9f62b9-113a-4a98-8f9b-b593cef27b03
topic_type:
- apiref
ms.openlocfilehash: 0952d09db6d43f7970ba9e8c46c409fb2cd4b131
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694964"
---
# <a name="icordebugchaingetreason-method"></a><span data-ttu-id="44e5e-103">ICorDebugChain::GetReason 方法</span><span class="sxs-lookup"><span data-stu-id="44e5e-103">ICorDebugChain::GetReason Method</span></span>

<span data-ttu-id="44e5e-104">获取此调用链的 genesis 的原因。</span><span class="sxs-lookup"><span data-stu-id="44e5e-104">Gets the reason for the genesis of this calling chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44e5e-105">语法</span><span class="sxs-lookup"><span data-stu-id="44e5e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetReason (  
    [out] CorDebugChainReason *pReason  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44e5e-106">参数</span><span class="sxs-lookup"><span data-stu-id="44e5e-106">Parameters</span></span>  

 `pReason`  
 <span data-ttu-id="44e5e-107">弄一个指针 (，它指向 CorDebugChainReason 枚举的按位组合) ，该枚举指示此调用链的的原因。</span><span class="sxs-lookup"><span data-stu-id="44e5e-107">[out] A pointer to a value (a bitwise combination) of the CorDebugChainReason enumeration that indicates the reason for the genesis of this calling chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44e5e-108">要求</span><span class="sxs-lookup"><span data-stu-id="44e5e-108">Requirements</span></span>  

 <span data-ttu-id="44e5e-109">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="44e5e-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44e5e-110">**标头**：CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="44e5e-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="44e5e-111">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="44e5e-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="44e5e-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44e5e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
