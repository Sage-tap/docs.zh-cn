---
description: 了解详细信息： ICorDebugStaticFieldSymbol：： GetSize 方法
title: ICorDebugStaticFieldSymbol::GetSize 方法
ms.date: 03/30/2017
ms.assetid: 72389860-7e37-4656-ba46-b6aeee1860f8
ms.openlocfilehash: f6fd2fe60d7cb8a77dcff5ca259d05ae1ef195ed
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794684"
---
# <a name="icordebugstaticfieldsymbolgetsize-method"></a><span data-ttu-id="1c84c-103">ICorDebugStaticFieldSymbol::GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="1c84c-103">ICorDebugStaticFieldSymbol::GetSize Method</span></span>

<span data-ttu-id="1c84c-104">获取静态字段的大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="1c84c-104">Gets the size in bytes of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c84c-105">语法</span><span class="sxs-lookup"><span data-stu-id="1c84c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c84c-106">参数</span><span class="sxs-lookup"><span data-stu-id="1c84c-106">Parameters</span></span>  

 `pcbSize`  
 <span data-ttu-id="1c84c-107">[out] 指向字段长度的指针。</span><span class="sxs-lookup"><span data-stu-id="1c84c-107">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c84c-108">备注</span><span class="sxs-lookup"><span data-stu-id="1c84c-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1c84c-109">此方法仅适用于 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="1c84c-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c84c-110">要求</span><span class="sxs-lookup"><span data-stu-id="1c84c-110">Requirements</span></span>  

 <span data-ttu-id="1c84c-111">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1c84c-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c84c-112">**标头**：CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1c84c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1c84c-113">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c84c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c84c-114">**.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c84c-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c84c-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="1c84c-115">See also</span></span>

- [<span data-ttu-id="1c84c-116">ICorDebugStaticFieldSymbol 接口</span><span class="sxs-lookup"><span data-stu-id="1c84c-116">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="1c84c-117">调试接口</span><span class="sxs-lookup"><span data-stu-id="1c84c-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
