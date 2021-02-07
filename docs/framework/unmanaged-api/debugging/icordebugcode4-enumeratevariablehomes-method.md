---
description: 了解详细信息： ICorDebugCode4：： EnumerateVariableHomes 方法
title: ICorDebugCode4：： EnumerateVariableHomes 方法
ms.date: 03/30/2017
api_name:
- ICorDebugCode4.EnumerateVariableHomes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode4::EnumerateVariableHomes
helpviewer_keywords:
- EnumerateVariableHomes method [.NET Framework debugging]
- ICorDebugCode4::EnumerateVariableHomes method [.NET Framework debugging]
ms.assetid: 802c01ff-8b80-4733-b6dd-03ab6ff7fa11
topic_type:
- apiref
ms.openlocfilehash: 58f5f9063cd22356efd3a77ece9fb43b6b4c1062
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710954"
---
# <a name="icordebugcode4enumeratevariablehomes-method"></a><span data-ttu-id="53096-103">ICorDebugCode4：： EnumerateVariableHomes 方法</span><span class="sxs-lookup"><span data-stu-id="53096-103">ICorDebugCode4::EnumerateVariableHomes Method</span></span>

<span data-ttu-id="53096-104">获取函数中局部变量和参数的枚举器。</span><span class="sxs-lookup"><span data-stu-id="53096-104">Gets an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53096-105">语法</span><span class="sxs-lookup"><span data-stu-id="53096-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateVariableHomes(  
    [out] ICorDebugVariableHomeEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53096-106">参数</span><span class="sxs-lookup"><span data-stu-id="53096-106">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="53096-107">指向 [ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md) 接口对象地址的指针，该对象是函数中局部变量和参数的枚举器。</span><span class="sxs-lookup"><span data-stu-id="53096-107">A pointer to the address of an [ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md) interface object that is an enumerator for the local variables and arguments in a function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53096-108">备注</span><span class="sxs-lookup"><span data-stu-id="53096-108">Remarks</span></span>  

 <span data-ttu-id="53096-109">[ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md)接口对象是从 "ICorDebugEnum" 接口派生的标准枚举器，该枚举器可用于枚举[ICorDebugVariableHome](icordebugvariablehome-interface.md)对象。</span><span class="sxs-lookup"><span data-stu-id="53096-109">The [ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md) interface object is a standard enumerator derived from the "ICorDebugEnum" interface that allows you to enumerate [ICorDebugVariableHome](icordebugvariablehome-interface.md) objects.</span></span> <span data-ttu-id="53096-110">如果同一槽或参数索引的多个 [ICorDebugVariableHome](icordebugvariablehome-interface.md) 对象在函数不同的点具有不同的主对象，则该集合可能包含多个这些对象。</span><span class="sxs-lookup"><span data-stu-id="53096-110">The collection may include multiple [ICorDebugVariableHome](icordebugvariablehome-interface.md) objects for the same slot or      argument index if they have different homes at different points in the      function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53096-111">要求</span><span class="sxs-lookup"><span data-stu-id="53096-111">Requirements</span></span>  

 <span data-ttu-id="53096-112">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="53096-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53096-113">**标头**：CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="53096-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="53096-114">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="53096-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53096-115">**.NET Framework 版本：**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53096-115">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53096-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="53096-116">See also</span></span>

- [<span data-ttu-id="53096-117">ICorDebugCode4 接口</span><span class="sxs-lookup"><span data-stu-id="53096-117">ICorDebugCode4 Interface</span></span>](icordebugcode4-interface.md)
- [<span data-ttu-id="53096-118">调试接口</span><span class="sxs-lookup"><span data-stu-id="53096-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
