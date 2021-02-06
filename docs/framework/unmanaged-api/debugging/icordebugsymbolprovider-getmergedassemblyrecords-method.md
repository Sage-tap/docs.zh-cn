---
description: 了解详细信息： ICorDebugSymbolProvider：： GetMergedAssemblyRecords 方法
title: ICorDebugSymbolProvider::GetMergedAssemblyRecords 方法
ms.date: 03/30/2017
ms.assetid: cc4c510d-550d-4941-af34-81987caf3425
ms.openlocfilehash: f12bb3a49d7b49f9f8916c9d04417340502d44ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659876"
---
# <a name="icordebugsymbolprovidergetmergedassemblyrecords-method"></a><span data-ttu-id="cba6c-103">ICorDebugSymbolProvider::GetMergedAssemblyRecords 方法</span><span class="sxs-lookup"><span data-stu-id="cba6c-103">ICorDebugSymbolProvider::GetMergedAssemblyRecords Method</span></span>

<span data-ttu-id="cba6c-104">获取所有合并程序集的符号记录。</span><span class="sxs-lookup"><span data-stu-id="cba6c-104">Gets the symbol records for all the merged assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cba6c-105">语法</span><span class="sxs-lookup"><span data-stu-id="cba6c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMergedAssemblyRecords(  
   [in] ULONG32 cRequestedRecords,  
   [out] ULONG32 *pcFetchedRecords,  
   [out, size_is(cRequestedRecords), length_is(*pcFetchedRecords)] ICorDebugMergedAssemblyRecord *pRecords[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cba6c-106">参数</span><span class="sxs-lookup"><span data-stu-id="cba6c-106">Parameters</span></span>  

 `cRequestedRecords`  
 <span data-ttu-id="cba6c-107">[in] 请求的符号记录数。</span><span class="sxs-lookup"><span data-stu-id="cba6c-107">[in] The number of symbol records requested.</span></span>  
  
 `pcFetchedRecords`  
 <span data-ttu-id="cba6c-108">[out] 指向由方法检索的符号记录数的指针。</span><span class="sxs-lookup"><span data-stu-id="cba6c-108">[out] A pointer to the number of symbol records retrieved by the method.</span></span>  
  
 `pRecords`  
 <span data-ttu-id="cba6c-109">指向 [ICorDebugMergedAssemblyRecord](icordebugmergedassemblyrecord-interface.md) 对象数组的指针。</span><span class="sxs-lookup"><span data-stu-id="cba6c-109">A pointer to an array of [ICorDebugMergedAssemblyRecord](icordebugmergedassemblyrecord-interface.md) objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cba6c-110">备注</span><span class="sxs-lookup"><span data-stu-id="cba6c-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cba6c-111">此方法仅适用于 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="cba6c-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cba6c-112">要求</span><span class="sxs-lookup"><span data-stu-id="cba6c-112">Requirements</span></span>  

 <span data-ttu-id="cba6c-113">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cba6c-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cba6c-114">**标头**：CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cba6c-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cba6c-115">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cba6c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cba6c-116">**.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cba6c-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cba6c-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="cba6c-117">See also</span></span>

- [<span data-ttu-id="cba6c-118">ICorDebugSymbolProvider 接口</span><span class="sxs-lookup"><span data-stu-id="cba6c-118">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="cba6c-119">调试接口</span><span class="sxs-lookup"><span data-stu-id="cba6c-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
