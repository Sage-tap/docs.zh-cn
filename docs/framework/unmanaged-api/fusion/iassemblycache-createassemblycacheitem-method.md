---
description: 了解详细信息： IAssemblyCache：： CreateAssemblyCacheItem 方法
title: IAssemblyCache::CreateAssemblyCacheItem 方法
ms.date: 03/30/2017
api_name:
- IAssemblyCache.CreateAssemblyCacheItem
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::CreateAssemblyCacheItem
helpviewer_keywords:
- IAssemblyCache::CreateAssemblyCacheItem method [.NET Framework fusion]
- CreateAssemblyCacheItem method [.NET Framework fusion]
ms.assetid: 017a7ba5-aaaf-44e2-9cbe-ceebef259df0
topic_type:
- apiref
ms.openlocfilehash: 3377901d358bcf643ce0d30336c1c0cd8089e50c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760974"
---
# <a name="iassemblycachecreateassemblycacheitem-method"></a><span data-ttu-id="d1189-103">IAssemblyCache::CreateAssemblyCacheItem 方法</span><span class="sxs-lookup"><span data-stu-id="d1189-103">IAssemblyCache::CreateAssemblyCacheItem Method</span></span>

<span data-ttu-id="d1189-104">获取对新的 [IAssemblyCacheItem](iassemblycacheitem-interface.md) 对象的引用。</span><span class="sxs-lookup"><span data-stu-id="d1189-104">Gets a reference to a new [IAssemblyCacheItem](iassemblycacheitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1189-105">语法</span><span class="sxs-lookup"><span data-stu-id="d1189-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyCacheItem (  
    [in]  DWORD dwFlags,  
    [in]  PVOID pvReserved,  
    [out] IAssemblyCacheItem **ppAsmItem,  
    [in, optional] LPCWSTR pszAssemblyName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1189-106">参数</span><span class="sxs-lookup"><span data-stu-id="d1189-106">Parameters</span></span>  

 `dwFlags`  
 <span data-ttu-id="d1189-107">中在合成 .idl 中定义的标志。</span><span class="sxs-lookup"><span data-stu-id="d1189-107">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="d1189-108">支持以下值：</span><span class="sxs-lookup"><span data-stu-id="d1189-108">The following values are supported:</span></span>  
  
- <span data-ttu-id="d1189-109"> (0x00000001) IASSEMBLYCACHE_INSTALL_FLAG_REFRESH</span><span class="sxs-lookup"><span data-stu-id="d1189-109">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span></span>  
  
- <span data-ttu-id="d1189-110">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002) </span><span class="sxs-lookup"><span data-stu-id="d1189-110">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="d1189-111">中保留以供将来进行扩展。</span><span class="sxs-lookup"><span data-stu-id="d1189-111">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="d1189-112">`pvReserved` 必须为空引用。</span><span class="sxs-lookup"><span data-stu-id="d1189-112">`pvReserved` must be a null reference.</span></span>  
  
 `ppAsmItem`  
 <span data-ttu-id="d1189-113">弄返回的 `IAssemblyCacheItem` 指针。</span><span class="sxs-lookup"><span data-stu-id="d1189-113">[out] The returned `IAssemblyCacheItem` pointer.</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="d1189-114">[in，可选]Uncanonicalized，以逗号分隔的 `name=value` 对。</span><span class="sxs-lookup"><span data-stu-id="d1189-114">[in, optional] Uncanonicalized, comma-separated `name=value` pairs.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1189-115">要求</span><span class="sxs-lookup"><span data-stu-id="d1189-115">Requirements</span></span>  

 <span data-ttu-id="d1189-116">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d1189-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1189-117">**标头：** 合成。h</span><span class="sxs-lookup"><span data-stu-id="d1189-117">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="d1189-118">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1189-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1189-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="d1189-119">See also</span></span>

- [<span data-ttu-id="d1189-120">IAssemblyCache 接口</span><span class="sxs-lookup"><span data-stu-id="d1189-120">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
- [<span data-ttu-id="d1189-121">IAssemblyCacheItem 接口</span><span class="sxs-lookup"><span data-stu-id="d1189-121">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
