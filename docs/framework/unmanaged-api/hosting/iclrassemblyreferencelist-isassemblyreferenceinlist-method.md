---
description: 了解详细信息： ICLRAssemblyReferenceList：： IsAssemblyReferenceInList 方法
title: ICLRAssemblyReferenceList::IsAssemblyReferenceInList 方法
ms.date: 03/30/2017
api_name:
- ICLRAssemblyReferenceList.IsAssemblyReferenceInList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyReferenceList::IsAssemblyReferenceInList
helpviewer_keywords:
- ICLRAssemblyReferenceList::IsAssemblyReferenceInList method [.NET Framework hosting]
- IsAssemblyReferenceInList method [.NET Framework hosting]
ms.assetid: 8a570813-21be-407e-92a6-7ae8de3bc728
topic_type:
- apiref
ms.openlocfilehash: ce90423715d6cbe07c1112cb2136c11fd58c982a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716765"
---
# <a name="iclrassemblyreferencelistisassemblyreferenceinlist-method"></a><span data-ttu-id="00882-103">ICLRAssemblyReferenceList::IsAssemblyReferenceInList 方法</span><span class="sxs-lookup"><span data-stu-id="00882-103">ICLRAssemblyReferenceList::IsAssemblyReferenceInList Method</span></span>

<span data-ttu-id="00882-104">获取一个值，该值指示提供的指针是否引用列表中的程序集。</span><span class="sxs-lookup"><span data-stu-id="00882-104">Gets a value that indicates whether the supplied pointer refers to an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00882-105">语法</span><span class="sxs-lookup"><span data-stu-id="00882-105">Syntax</span></span>  
  
```cpp  
HRESULT IsAssemblyReferenceInList (  
    [in] IUnknown *pName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00882-106">参数</span><span class="sxs-lookup"><span data-stu-id="00882-106">Parameters</span></span>  

 `pName`  
 <span data-ttu-id="00882-107">中一个接口指针，指向要搜索的程序集。</span><span class="sxs-lookup"><span data-stu-id="00882-107">[in] An interface pointer to the assembly for which to search.</span></span> <span data-ttu-id="00882-108">有效值的类型为 `IAssemblyName` 或 `IReferenceIdentity` 。</span><span class="sxs-lookup"><span data-stu-id="00882-108">Valid values are of type `IAssemblyName` or `IReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="00882-109">返回值</span><span class="sxs-lookup"><span data-stu-id="00882-109">Return Value</span></span>  
  
|<span data-ttu-id="00882-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="00882-110">HRESULT</span></span>|<span data-ttu-id="00882-111">说明</span><span class="sxs-lookup"><span data-stu-id="00882-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="00882-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="00882-112">S_OK</span></span>|<span data-ttu-id="00882-113">此字符串将显示在列表中。</span><span class="sxs-lookup"><span data-stu-id="00882-113">The string appears in the list.</span></span>|  
|<span data-ttu-id="00882-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="00882-114">S_FALSE</span></span>|<span data-ttu-id="00882-115">该字符串未出现在列表中。</span><span class="sxs-lookup"><span data-stu-id="00882-115">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="00882-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="00882-116">E_FAIL</span></span>|<span data-ttu-id="00882-117">发生未知的灾难性故障。</span><span class="sxs-lookup"><span data-stu-id="00882-117">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="00882-118">方法返回 E_FAIL 后，公共语言运行时在进程中将不再可用。</span><span class="sxs-lookup"><span data-stu-id="00882-118">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="00882-119">对宿主方法的后续调用会返回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="00882-119">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="00882-120">要求</span><span class="sxs-lookup"><span data-stu-id="00882-120">Requirements</span></span>  

 <span data-ttu-id="00882-121">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="00882-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00882-122">**标头：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="00882-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="00882-123">**库：** 作为中的资源包含 MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="00882-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="00882-124">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00882-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00882-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="00882-125">See also</span></span>

- [<span data-ttu-id="00882-126">ICLRAssemblyIdentityManager 接口</span><span class="sxs-lookup"><span data-stu-id="00882-126">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="00882-127">ICLRAssemblyReferenceList 接口</span><span class="sxs-lookup"><span data-stu-id="00882-127">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="00882-128">IHostAssemblyManager 接口</span><span class="sxs-lookup"><span data-stu-id="00882-128">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="00882-129">IHostAssemblyStore 接口</span><span class="sxs-lookup"><span data-stu-id="00882-129">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
