---
description: 了解详细信息： CLRCreateInstance 函数
title: CLRCreateInstance 函数
ms.date: 03/30/2017
api_name:
- CLRCreateInstance
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- COM
f1_keywords:
- CLRCreateInstance
helpviewer_keywords:
- CLRCreateInstance function [.NET Framework hosting]
ms.assetid: 5de13327-96c6-4697-a89e-b8bf40717855
topic_type:
- apiref
ms.openlocfilehash: 3b4dd9f07444f3e7ca68af3b85a7a053fc72b772
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799934"
---
# <a name="clrcreateinstance-function"></a><span data-ttu-id="5f427-103">CLRCreateInstance 函数</span><span class="sxs-lookup"><span data-stu-id="5f427-103">CLRCreateInstance Function</span></span>

<span data-ttu-id="5f427-104">提供以下三个接口之一： [ICLRMetaHost](iclrmetahost-interface.md)、 [ICLRMetaHostPolicy](iclrmetahostpolicy-interface.md)或 [ICLRDebugging](../debugging/iclrdebugging-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="5f427-104">Provides one of three interfaces: [ICLRMetaHost](iclrmetahost-interface.md), [ICLRMetaHostPolicy](iclrmetahostpolicy-interface.md), or [ICLRDebugging](../debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f427-105">语法</span><span class="sxs-lookup"><span data-stu-id="5f427-105">Syntax</span></span>  
  
```cpp  
HRESULT CLRCreateInstance(  
    [in]  REFCLSID  clsid,  
    [in]  REFIID     riid,  
    [out] LPVOID  * ppInterface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f427-106">参数</span><span class="sxs-lookup"><span data-stu-id="5f427-106">Parameters</span></span>  

 `clsid`  
 <span data-ttu-id="5f427-107">中三个类标识符之一： CLSID_CLRMetaHost、CLSID_CLRMetaHostPolicy 或 CLSID_CLRDebugging。</span><span class="sxs-lookup"><span data-stu-id="5f427-107">[in] One of three class identifiers: CLSID_CLRMetaHost, CLSID_CLRMetaHostPolicy, or CLSID_CLRDebugging.</span></span>  
  
 `riid`  
 <span data-ttu-id="5f427-108">中三个接口标识符中的一个 (Iid) ： IID_ICLRMetaHost、IID_ICLRMetaHostPolicy 或 IID_ICLRDebugging。</span><span class="sxs-lookup"><span data-stu-id="5f427-108">[in] One of three interface identifiers (IIDs): IID_ICLRMetaHost, IID_ICLRMetaHostPolicy, or IID_ICLRDebugging.</span></span>  
  
 `ppInterface`  
 <span data-ttu-id="5f427-109">弄以下三个接口之一： [ICLRMetaHost](iclrmetahost-interface.md)、 [ICLRMetaHostPolicy](iclrmetahostpolicy-interface.md)或 [ICLRDebugging](../debugging/iclrdebugging-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="5f427-109">[out] One of three interfaces: [ICLRMetaHost](iclrmetahost-interface.md), [ICLRMetaHostPolicy](iclrmetahostpolicy-interface.md), or [ICLRDebugging](../debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5f427-110">返回值</span><span class="sxs-lookup"><span data-stu-id="5f427-110">Return Value</span></span>  

 <span data-ttu-id="5f427-111">此方法返回以下特定 HRESULT 以及表示方法失败的 HRESULT 错误。</span><span class="sxs-lookup"><span data-stu-id="5f427-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="5f427-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5f427-112">HRESULT</span></span>|<span data-ttu-id="5f427-113">说明</span><span class="sxs-lookup"><span data-stu-id="5f427-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5f427-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="5f427-114">S_OK</span></span>|<span data-ttu-id="5f427-115">该方法已成功完成。</span><span class="sxs-lookup"><span data-stu-id="5f427-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="5f427-116">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="5f427-116">E_POINTER</span></span>|<span data-ttu-id="5f427-117">`ppInterface` 为 null。</span><span class="sxs-lookup"><span data-stu-id="5f427-117">`ppInterface` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f427-118">备注</span><span class="sxs-lookup"><span data-stu-id="5f427-118">Remarks</span></span>  

 <span data-ttu-id="5f427-119">下表显示了和支持的组合 `clsid` `riid` 。</span><span class="sxs-lookup"><span data-stu-id="5f427-119">The following table shows the supported combinations for `clsid` and `riid`.</span></span>  
  
|`clsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="5f427-120">CLSID_CLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="5f427-120">CLSID_CLRMetaHost</span></span>|<span data-ttu-id="5f427-121">IID_ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="5f427-121">IID_ICLRMetaHost</span></span>|  
|<span data-ttu-id="5f427-122">CLSID_CLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="5f427-122">CLSID_CLRMetaHostPolicy</span></span>|<span data-ttu-id="5f427-123">IID_ICLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="5f427-123">IID_ICLRMetaHostPolicy</span></span>|  
|<span data-ttu-id="5f427-124">CLSID_CLRDebugging</span><span class="sxs-lookup"><span data-stu-id="5f427-124">CLSID_CLRDebugging</span></span>|<span data-ttu-id="5f427-125">IID_ICLRDebugging</span><span class="sxs-lookup"><span data-stu-id="5f427-125">IID_ICLRDebugging</span></span>|  
  
 <span data-ttu-id="5f427-126">下面的代码演示如何使用 `CLRCreateInstance` 获取所有三个接口：</span><span class="sxs-lookup"><span data-stu-id="5f427-126">The following code shows how to use `CLRCreateInstance` to get all three interfaces:</span></span>  
  
```cpp  
#include <metahost.h>  
#pragma comment(lib, "mscoree.lib")  
  
ICLRMetaHost       *pMetaHost       = NULL;  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
ICLRDebugging      *pCLRDebugging   = NULL;  
HRESULT hr;  
hr = CLRCreateInstance(CLSID_CLRMetaHost, IID_ICLRMetaHost,  
                    (LPVOID*)&pMetaHost);  
hr = CLRCreateInstance (CLSID_CLRMetaHostPolicy, IID_ICLRMetaHostPolicy,  
                    (LPVOID*)&pMetaHostPolicy);  
hr = CLRCreateInstance (CLSID_CLRDebugging, IID_ICLRDebugging,  
                    (LPVOID*)&pCLRDebugging);  
```  
  
## <a name="requirements"></a><span data-ttu-id="5f427-127">要求</span><span class="sxs-lookup"><span data-stu-id="5f427-127">Requirements</span></span>  

 <span data-ttu-id="5f427-128">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5f427-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f427-129">**标头：** MetaHost</span><span class="sxs-lookup"><span data-stu-id="5f427-129">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="5f427-130">**库：** 作为中的资源包含 MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5f427-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5f427-131">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f427-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f427-132">请参阅</span><span class="sxs-lookup"><span data-stu-id="5f427-132">See also</span></span>

- [<span data-ttu-id="5f427-133">承载</span><span class="sxs-lookup"><span data-stu-id="5f427-133">Hosting</span></span>](index.md)
