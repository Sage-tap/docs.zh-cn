---
description: 了解详细信息： ICorRuntimeHost：： GetDefaultDomain 方法
title: ICorRuntimeHost::GetDefaultDomain 方法
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.GetDefaultDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::GetDefaultDomain
helpviewer_keywords:
- ICorRuntimeHost::GetDefaultDomain method [.NET Framework hosting]
- GetDefaultDomain method [.NET Framework hosting]
ms.assetid: 5e17a6fc-f335-4aae-9bb0-c3e1271a9426
topic_type:
- apiref
ms.openlocfilehash: 53be5e3db7bec396743edc728942ad54efc0ec16
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753817"
---
# <a name="icorruntimehostgetdefaultdomain-method"></a><span data-ttu-id="cb7e3-103">ICorRuntimeHost::GetDefaultDomain 方法</span><span class="sxs-lookup"><span data-stu-id="cb7e3-103">ICorRuntimeHost::GetDefaultDomain Method</span></span>

<span data-ttu-id="cb7e3-104">获取类型的接口指针 <xref:System._AppDomain?displayProperty=nameWithType> ，该指针表示当前进程的默认域。</span><span class="sxs-lookup"><span data-stu-id="cb7e3-104">Gets an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the default domain for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb7e3-105">语法</span><span class="sxs-lookup"><span data-stu-id="cb7e3-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDefaultDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb7e3-106">参数</span><span class="sxs-lookup"><span data-stu-id="cb7e3-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="cb7e3-107">弄类型为的接口指针， <xref:System._AppDomain?displayProperty=nameWithType> 用于 <xref:System.AppDomain> 表示进程的默认应用程序域的实例。</span><span class="sxs-lookup"><span data-stu-id="cb7e3-107">[out] An interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> to the <xref:System.AppDomain> instance that represents the default application domain for the process.</span></span>  
  
 <span data-ttu-id="cb7e3-108">此指针已类型化 `IUnknown` ，因此调用方通常应调用 `QueryInterface` 以获取类型的接口指针 <xref:System._AppDomain?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="cb7e3-108">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cb7e3-109">返回值</span><span class="sxs-lookup"><span data-stu-id="cb7e3-109">Return Value</span></span>  
  
|<span data-ttu-id="cb7e3-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cb7e3-110">HRESULT</span></span>|<span data-ttu-id="cb7e3-111">说明</span><span class="sxs-lookup"><span data-stu-id="cb7e3-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cb7e3-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="cb7e3-112">S_OK</span></span>|<span data-ttu-id="cb7e3-113">操作成功。</span><span class="sxs-lookup"><span data-stu-id="cb7e3-113">The operation was successful.</span></span>|  
|<span data-ttu-id="cb7e3-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="cb7e3-114">S_FALSE</span></span>|<span data-ttu-id="cb7e3-115">操作未能完成。</span><span class="sxs-lookup"><span data-stu-id="cb7e3-115">The operation failed to complete.</span></span>|  
|<span data-ttu-id="cb7e3-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cb7e3-116">E_FAIL</span></span>|<span data-ttu-id="cb7e3-117">发生了未知的灾难性故障。</span><span class="sxs-lookup"><span data-stu-id="cb7e3-117">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="cb7e3-118">如果某个方法返回 E_FAIL，则公共语言运行时 (CLR) 在该进程中不再可用。</span><span class="sxs-lookup"><span data-stu-id="cb7e3-118">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="cb7e3-119">对任何宿主 Api 的后续调用都会返回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="cb7e3-119">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="cb7e3-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cb7e3-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cb7e3-121">CLR 未加载到进程中，或 CLR 处于无法运行托管代码或成功处理调用的状态。</span><span class="sxs-lookup"><span data-stu-id="cb7e3-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cb7e3-122">要求</span><span class="sxs-lookup"><span data-stu-id="cb7e3-122">Requirements</span></span>  

 <span data-ttu-id="cb7e3-123">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cb7e3-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb7e3-124">**标头：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="cb7e3-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cb7e3-125">**库：** 作为中的资源包含 MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cb7e3-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cb7e3-126">**.NET Framework 版本：** 1.0、1。1</span><span class="sxs-lookup"><span data-stu-id="cb7e3-126">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb7e3-127">请参阅</span><span class="sxs-lookup"><span data-stu-id="cb7e3-127">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="cb7e3-128">ICorRuntimeHost 接口</span><span class="sxs-lookup"><span data-stu-id="cb7e3-128">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
