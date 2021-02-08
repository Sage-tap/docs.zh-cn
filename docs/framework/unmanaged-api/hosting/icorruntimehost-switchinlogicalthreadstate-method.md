---
description: 了解详细信息： ICorRuntimeHost：： SwitchInLogicalThreadState 方法
title: ICorRuntimeHost::SwitchInLogicalThreadState 方法
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.SwitchInLogicalThreadState
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::SwitchInLogicalThreadState
helpviewer_keywords:
- ICorRuntimeHost::SwitchInLogicalThreadState method [.NET Framework hosting]
- SwitchInLogicalThreadState method [.NET Framework hosting]
ms.assetid: 7df1e492-8014-43ea-80d1-a4743e9b1c17
topic_type:
- apiref
ms.openlocfilehash: 3e375379cc5d6af7c3a8fb8d64a40a389e0f9dcc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789562"
---
# <a name="icorruntimehostswitchinlogicalthreadstate-method"></a><span data-ttu-id="64cc7-103">ICorRuntimeHost::SwitchInLogicalThreadState 方法</span><span class="sxs-lookup"><span data-stu-id="64cc7-103">ICorRuntimeHost::SwitchInLogicalThreadState Method</span></span>

<span data-ttu-id="64cc7-104">此方法支持 .NET Framework 基础结构，但不适合直接在代码中使用。</span><span class="sxs-lookup"><span data-stu-id="64cc7-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64cc7-105">语法</span><span class="sxs-lookup"><span data-stu-id="64cc7-105">Syntax</span></span>  
  
```cpp  
HRESULT SwitchInLogicalThreadState(  
    [in] DWORD *pFiberCookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64cc7-106">参数</span><span class="sxs-lookup"><span data-stu-id="64cc7-106">Parameters</span></span>  

 `pFiberCookie`  
 <span data-ttu-id="64cc7-107">中指示要使用的纤程的 Cookie。</span><span class="sxs-lookup"><span data-stu-id="64cc7-107">[in] Cookie that indicates the fiber to use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64cc7-108">要求</span><span class="sxs-lookup"><span data-stu-id="64cc7-108">Requirements</span></span>  

 <span data-ttu-id="64cc7-109">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="64cc7-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64cc7-110">**标头：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="64cc7-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="64cc7-111">**库：** 作为中的资源包含 MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="64cc7-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="64cc7-112">**.NET Framework 版本：** 1.0、1。1</span><span class="sxs-lookup"><span data-stu-id="64cc7-112">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64cc7-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="64cc7-113">See also</span></span>

- [<span data-ttu-id="64cc7-114">ICorRuntimeHost 接口</span><span class="sxs-lookup"><span data-stu-id="64cc7-114">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
