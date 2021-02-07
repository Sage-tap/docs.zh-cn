---
description: 了解详细信息： IMetaDataTables：： GetStringHeapSize 方法
title: IMetaDataTables::GetStringHeapSize 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetStringHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetStringHeapSize
helpviewer_keywords:
- IMetaDataTables::GetStringHeapSize method [.NET Framework metadata]
- GetStringHeapSize method [.NET Framework metadata]
ms.assetid: ed8f6335-81f5-4c09-81a9-2a909fc530c9
topic_type:
- apiref
ms.openlocfilehash: 0ec9f4e2768cc78163db67bc9099fc9cafae8c8c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687774"
---
# <a name="imetadatatablesgetstringheapsize-method"></a><span data-ttu-id="6664f-103">IMetaDataTables::GetStringHeapSize 方法</span><span class="sxs-lookup"><span data-stu-id="6664f-103">IMetaDataTables::GetStringHeapSize Method</span></span>

<span data-ttu-id="6664f-104">获取字符串堆的大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="6664f-104">Gets the size, in bytes, of the string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6664f-105">语法</span><span class="sxs-lookup"><span data-stu-id="6664f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStringHeapSize (  
    [out] ULONG   *pcbStrings  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6664f-106">参数</span><span class="sxs-lookup"><span data-stu-id="6664f-106">Parameters</span></span>  

 `pcbStrings`  
 <span data-ttu-id="6664f-107">弄一个指针，指向字符串堆的大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="6664f-107">[out] A pointer to the size, in bytes, of the string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6664f-108">要求</span><span class="sxs-lookup"><span data-stu-id="6664f-108">Requirements</span></span>  

 <span data-ttu-id="6664f-109">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6664f-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6664f-110">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="6664f-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6664f-111">**库：** 用作 MsCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="6664f-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6664f-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6664f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6664f-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="6664f-113">See also</span></span>

- [<span data-ttu-id="6664f-114">IMetaDataTables 接口</span><span class="sxs-lookup"><span data-stu-id="6664f-114">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="6664f-115">IMetaDataTables2 接口</span><span class="sxs-lookup"><span data-stu-id="6664f-115">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
