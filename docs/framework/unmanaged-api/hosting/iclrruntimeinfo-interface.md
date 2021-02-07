---
description: 了解详细信息： ICLRRuntimeInfo 接口
title: ICLRRuntimeInfo 接口
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo
helpviewer_keywords:
- ICLRRuntimeInfo interface [.NET Framework hosting]
ms.assetid: 287e5ede-b3a7-4ef8-a756-4fca3f285a82
topic_type:
- apiref
ms.openlocfilehash: d599c743e5a42801321ea487fdd9e52bfcfaf081
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753856"
---
# <a name="iclrruntimeinfo-interface"></a><span data-ttu-id="507ce-103">ICLRRuntimeInfo 接口</span><span class="sxs-lookup"><span data-stu-id="507ce-103">ICLRRuntimeInfo Interface</span></span>

<span data-ttu-id="507ce-104">提供一些方法，这些方法可返回有关特定公共语言运行时 (CLR) 的信息，包括版本、目录和加载状态。</span><span class="sxs-lookup"><span data-stu-id="507ce-104">Provides methods that return information about a specific common language runtime (CLR), including version, directory, and load status.</span></span> <span data-ttu-id="507ce-105">此接口还提供了特定于运行时的功能，而无需初始化运行时。</span><span class="sxs-lookup"><span data-stu-id="507ce-105">This interface also provides runtime-specific functionality without initializing the runtime.</span></span> <span data-ttu-id="507ce-106">它包括运行时相对 [LoadLibrary](iclrruntimeinfo-loadlibrary-method.md) 方法、运行时模块特定的 [GetProcAddress](iclrruntimeinfo-getprocaddress-method.md) 方法和通过 [GetInterface](iclrruntimeinfo-getinterface-method.md) 方法提供的运行时提供的接口。</span><span class="sxs-lookup"><span data-stu-id="507ce-106">It includes the runtime-relative [LoadLibrary](iclrruntimeinfo-loadlibrary-method.md) method, the runtime module-specific [GetProcAddress](iclrruntimeinfo-getprocaddress-method.md) method, and runtime-provided interfaces through the [GetInterface](iclrruntimeinfo-getinterface-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="507ce-107">方法</span><span class="sxs-lookup"><span data-stu-id="507ce-107">Methods</span></span>  
  
|<span data-ttu-id="507ce-108">方法</span><span class="sxs-lookup"><span data-stu-id="507ce-108">Method</span></span>|<span data-ttu-id="507ce-109">说明</span><span class="sxs-lookup"><span data-stu-id="507ce-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="507ce-110">BindAsLegacyV2Runtime 方法</span><span class="sxs-lookup"><span data-stu-id="507ce-110">BindAsLegacyV2Runtime Method</span></span>](iclrruntimeinfo-bindaslegacyv2runtime-method.md)|<span data-ttu-id="507ce-111">为所有旧版 CLR 版本2激活策略决策绑定此运行时。</span><span class="sxs-lookup"><span data-stu-id="507ce-111">Binds this runtime for all legacy CLR version 2 activation policy decisions.</span></span>|  
|[<span data-ttu-id="507ce-112">GetDefaultStartupFlags 方法</span><span class="sxs-lookup"><span data-stu-id="507ce-112">GetDefaultStartupFlags Method</span></span>](iclrruntimeinfo-getdefaultstartupflags-method.md)|<span data-ttu-id="507ce-113">获取 CLR 启动标志和主机配置文件。</span><span class="sxs-lookup"><span data-stu-id="507ce-113">Gets the CLR startup flags and host configuration file.</span></span>|  
|[<span data-ttu-id="507ce-114">GetInterface 方法</span><span class="sxs-lookup"><span data-stu-id="507ce-114">GetInterface Method</span></span>](iclrruntimeinfo-getinterface-method.md)|<span data-ttu-id="507ce-115">将 CLR 加载到当前进程并返回运行时接口指针，如 [ICLRRuntimeHost](iclrruntimehost-interface.md)、 [ICLRStrongName](iclrstrongname-interface.md) 和 [IMetaDataDispenser](../metadata/imetadatadispenser-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="507ce-115">Loads the CLR into the current process and returns runtime interface pointers, such as [ICLRRuntimeHost](iclrruntimehost-interface.md), [ICLRStrongName](iclrstrongname-interface.md) and [IMetaDataDispenser](../metadata/imetadatadispenser-interface.md).</span></span> <span data-ttu-id="507ce-116">此方法将取代所有 `CorBindTo*` 函数。</span><span class="sxs-lookup"><span data-stu-id="507ce-116">This method supersedes all the `CorBindTo*` functions.</span></span>|  
|[<span data-ttu-id="507ce-117">GetProcAddress 方法</span><span class="sxs-lookup"><span data-stu-id="507ce-117">GetProcAddress Method</span></span>](iclrruntimeinfo-getprocaddress-method.md)|<span data-ttu-id="507ce-118">获取从与此接口关联的 CLR 导出的指定函数的地址。</span><span class="sxs-lookup"><span data-stu-id="507ce-118">Gets the address of a specified function that was exported from the CLR associated with this interface.</span></span> <span data-ttu-id="507ce-119">此方法取代了 [GetRealProcAddress](getrealprocaddress-function.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="507ce-119">This method supersedes the [GetRealProcAddress](getrealprocaddress-function.md) method.</span></span>|  
|[<span data-ttu-id="507ce-120">GetRuntimeDirectory 方法</span><span class="sxs-lookup"><span data-stu-id="507ce-120">GetRuntimeDirectory Method</span></span>](iclrruntimeinfo-getruntimedirectory-method.md)|<span data-ttu-id="507ce-121">获取与此接口关联的 CLR 的安装目录。</span><span class="sxs-lookup"><span data-stu-id="507ce-121">Gets the installation directory of the CLR associated with this interface.</span></span> <span data-ttu-id="507ce-122">此方法取代了 [GetCORSystemDirectory](getcorsystemdirectory-function.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="507ce-122">This method supersedes the [GetCORSystemDirectory](getcorsystemdirectory-function.md) method.</span></span>|  
|[<span data-ttu-id="507ce-123">GetVersionString 方法</span><span class="sxs-lookup"><span data-stu-id="507ce-123">GetVersionString Method</span></span>](iclrruntimeinfo-getversionstring-method.md)|<span data-ttu-id="507ce-124">获取公共语言运行时 (CLR) 版本信息与给定的 [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) 接口相关联。</span><span class="sxs-lookup"><span data-stu-id="507ce-124">Gets common language runtime (CLR) version information associated with a given [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span> <span data-ttu-id="507ce-125">此方法取代了 [GetRequestedRuntimeInfo](getrequestedruntimeinfo-function.md) 和 [GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="507ce-125">This method supersedes the [GetRequestedRuntimeInfo](getrequestedruntimeinfo-function.md) and [GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md) methods.</span></span>|  
|[<span data-ttu-id="507ce-126">IsLoadable 方法</span><span class="sxs-lookup"><span data-stu-id="507ce-126">IsLoadable Method</span></span>](iclrruntimeinfo-isloadable-method.md)|<span data-ttu-id="507ce-127">指示是否可将与此接口关联的运行时加载到当前进程，并考虑可能已加载到进程中的其他运行时。</span><span class="sxs-lookup"><span data-stu-id="507ce-127">Indicates whether the runtime associated with this interface can be loaded into the current process, taking into account other runtimes that might already be loaded into the process.</span></span>|  
|[<span data-ttu-id="507ce-128">IsLoaded 方法</span><span class="sxs-lookup"><span data-stu-id="507ce-128">IsLoaded Method</span></span>](iclrruntimeinfo-isloaded-method.md)|<span data-ttu-id="507ce-129">指示与 [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) 接口关联的 CLR 是否已加载到进程中。</span><span class="sxs-lookup"><span data-stu-id="507ce-129">Indicates whether the CLR associated with the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface is loaded into a process.</span></span>|  
|[<span data-ttu-id="507ce-130">IsStarted 方法</span><span class="sxs-lookup"><span data-stu-id="507ce-130">IsStarted Method</span></span>](iclrruntimeinfo-isstarted-method.md)|<span data-ttu-id="507ce-131">指示与 [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) 接口关联的 CLR 是否已启动。</span><span class="sxs-lookup"><span data-stu-id="507ce-131">Indicates whether the CLR that is associated with the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface has been started.</span></span>|  
|[<span data-ttu-id="507ce-132">LoadErrorString 方法</span><span class="sxs-lookup"><span data-stu-id="507ce-132">LoadErrorString Method</span></span>](iclrruntimeinfo-loaderrorstring-method.md)|<span data-ttu-id="507ce-133">将 HRESULT 值转换为指定区域性的适当错误消息。</span><span class="sxs-lookup"><span data-stu-id="507ce-133">Translates an HRESULT value into an appropriate error message for the specified culture.</span></span> <span data-ttu-id="507ce-134">此方法取代了 [LoadStringRC](loadstringrc-function.md) 和 [LoadStringRCEx](loadstringrcex-function.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="507ce-134">This method supersedes the [LoadStringRC](loadstringrc-function.md) and [LoadStringRCEx](loadstringrcex-function.md) methods.</span></span>|  
|[<span data-ttu-id="507ce-135">LoadLibrary 方法</span><span class="sxs-lookup"><span data-stu-id="507ce-135">LoadLibrary Method</span></span>](iclrruntimeinfo-loadlibrary-method.md)|<span data-ttu-id="507ce-136">从 [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) 接口所表示的 CLR 的框架目录加载库。</span><span class="sxs-lookup"><span data-stu-id="507ce-136">Loads a library from the framework directory of the CLR represented by an [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span> <span data-ttu-id="507ce-137">此方法取代了 [LoadLibraryShim](loadlibraryshim-function.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="507ce-137">This method supersedes the [LoadLibraryShim](loadlibraryshim-function.md) method.</span></span>|  
|[<span data-ttu-id="507ce-138">SetDefaultStartupFlags 方法</span><span class="sxs-lookup"><span data-stu-id="507ce-138">SetDefaultStartupFlags Method</span></span>](iclrruntimeinfo-setdefaultstartupflags-method.md)|<span data-ttu-id="507ce-139">设置 CLR 启动标志和主机配置文件。</span><span class="sxs-lookup"><span data-stu-id="507ce-139">Sets the CLR startup flags and host configuration file.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="507ce-140">要求</span><span class="sxs-lookup"><span data-stu-id="507ce-140">Requirements</span></span>  

 <span data-ttu-id="507ce-141">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="507ce-141">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="507ce-142">**标头：** MetaHost</span><span class="sxs-lookup"><span data-stu-id="507ce-142">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="507ce-143">**库：** 作为中的资源包含 MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="507ce-143">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="507ce-144">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="507ce-144">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="507ce-145">请参阅</span><span class="sxs-lookup"><span data-stu-id="507ce-145">See also</span></span>

- [<span data-ttu-id="507ce-146">承载接口</span><span class="sxs-lookup"><span data-stu-id="507ce-146">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="507ce-147">承载</span><span class="sxs-lookup"><span data-stu-id="507ce-147">Hosting</span></span>](index.md)
