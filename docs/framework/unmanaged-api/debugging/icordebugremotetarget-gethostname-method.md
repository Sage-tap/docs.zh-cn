---
description: 了解详细信息： ICorDebugRemoteTarget：： GetHostName 方法
title: ICorDebugRemoteTarget::GetHostName 方法
ms.date: 03/30/2017
api_name:
- ICorDebugRemoteTarget.GetHostName
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::GetHostName
helpviewer_keywords:
- ICorDebugRemoteTarget::GetHostName method [.NET Framework debugging]
- GetHostName method, ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: 1c7276f7-7e54-470c-808c-e13745ac07a1
topic_type:
- apiref
ms.openlocfilehash: a24f34dd638c7031211c2185cd761af0aa24105e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803521"
---
# <a name="icordebugremotetargetgethostname-method"></a><span data-ttu-id="78543-103">ICorDebugRemoteTarget::GetHostName 方法</span><span class="sxs-lookup"><span data-stu-id="78543-103">ICorDebugRemoteTarget::GetHostName Method</span></span>

<span data-ttu-id="78543-104">返回远程调试目标计算机的完全限定域名或 IPv4 地址。</span><span class="sxs-lookup"><span data-stu-id="78543-104">Returns the fully qualified domain name or IPv4 address of the remote debugging target machine.</span></span> <span data-ttu-id="78543-105">此时不支持 IPV6。</span><span class="sxs-lookup"><span data-stu-id="78543-105">IPV6 is not supported at this time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78543-106">语法</span><span class="sxs-lookup"><span data-stu-id="78543-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHostName (  
    [in] ULONG32      cchHostName,  
    [out] ULONG32*    pcchHostName,  
    [out, size_is(cchHostName), length_is(*pcchHostName)]  
            WCHAR szHostName[]  
```  
  
## <a name="parameters"></a><span data-ttu-id="78543-107">参数</span><span class="sxs-lookup"><span data-stu-id="78543-107">Parameters</span></span>  

 `cchHostName`  
 <span data-ttu-id="78543-108">中缓冲区的大小（以字符为字符） `szHostName` 。</span><span class="sxs-lookup"><span data-stu-id="78543-108">[in] The size, in characters, of the `szHostName` buffer.</span></span> <span data-ttu-id="78543-109">如果此参数为 0（零），`szHostName` 必须为 null。</span><span class="sxs-lookup"><span data-stu-id="78543-109">If this parameter is 0 (zero), `szHostName` must be null.</span></span>  
  
 `pcchHostName`  
 <span data-ttu-id="78543-110">[out] 主机名或 IP 地址中的字符数，包括 null 结束符。</span><span class="sxs-lookup"><span data-stu-id="78543-110">[out] The number of characters, including a null terminator, in the host name or IP address.</span></span> <span data-ttu-id="78543-111">此参数可以为 null。</span><span class="sxs-lookup"><span data-stu-id="78543-111">This parameter can be null.</span></span>  
  
 `szHostName`  
 <span data-ttu-id="78543-112">[out] 包含主机名或 IP 地址的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="78543-112">[out] Buffer that contains the host name or IP address.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="78543-113">返回值</span><span class="sxs-lookup"><span data-stu-id="78543-113">Return Value</span></span>  

 <span data-ttu-id="78543-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="78543-114">S_OK</span></span>  
 <span data-ttu-id="78543-115">主机名或 IP 地址成功返回。</span><span class="sxs-lookup"><span data-stu-id="78543-115">The host name or IP address was successfully returned.</span></span>  
  
 <span data-ttu-id="78543-116">E_FAIL（或其他 E_ 返回代码）</span><span class="sxs-lookup"><span data-stu-id="78543-116">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="78543-117">无法返回主机名或 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="78543-117">Unable to return the host name or IP address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78543-118">备注</span><span class="sxs-lookup"><span data-stu-id="78543-118">Remarks</span></span>  

 <span data-ttu-id="78543-119">此方法由调试器编写器实现。</span><span class="sxs-lookup"><span data-stu-id="78543-119">This method is implemented by the debugger writer.</span></span> <span data-ttu-id="78543-120">它必须遵循多个调用范例：在第一次调用时，调用方将 null 传递给 `cchHostName` 和 `szHostName` ，并 `pcchHostName` 返回所需的缓冲区大小。</span><span class="sxs-lookup"><span data-stu-id="78543-120">It must follow the multiple call paradigm: On the first call, the caller passes null to both `cchHostName` and `szHostName`, and `pcchHostName` returns the size of the required buffer.</span></span> <span data-ttu-id="78543-121">第二次调用时，先前返回的大小在 `cchHostName` 中传递，相应大小的缓冲区在 `szHostName` 中传递。</span><span class="sxs-lookup"><span data-stu-id="78543-121">On the second call, the size that was previously returned is passed in `cchHostName`, and an appropriately sized buffer is passed in `szHostName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78543-122">要求</span><span class="sxs-lookup"><span data-stu-id="78543-122">Requirements</span></span>  

 <span data-ttu-id="78543-123">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="78543-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78543-124">**标头：** Cordebug.idl .idl</span><span class="sxs-lookup"><span data-stu-id="78543-124">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="78543-125">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="78543-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78543-126">**.NET Framework 版本：** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="78543-126">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78543-127">请参阅</span><span class="sxs-lookup"><span data-stu-id="78543-127">See also</span></span>

- [<span data-ttu-id="78543-128">ICorDebugRemoteTarget 接口</span><span class="sxs-lookup"><span data-stu-id="78543-128">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="78543-129">ICorDebug 接口</span><span class="sxs-lookup"><span data-stu-id="78543-129">ICorDebug Interface</span></span>](icordebug-interface.md)
