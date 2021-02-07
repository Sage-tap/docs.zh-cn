---
description: 了解详细信息： _EFN_GetManagedExcepStack 函数
title: _EFN_GetManagedExcepStack 函数
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedExcepStack
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedExcepStack
helpviewer_keywords:
- _EFN_GetManagedExcepStack function [.NET Framework debugging]
ms.assetid: 21ceed9e-62b2-4024-b027-6d095109955a
topic_type:
- apiref
ms.openlocfilehash: a3c7e30a377e10b9d4d0b1dd663a594a0e872f3c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738307"
---
# <a name="_efn_getmanagedexcepstack-function"></a><span data-ttu-id="28a74-103">\_EFN \_ GetManagedExcepStack 函数</span><span class="sxs-lookup"><span data-stu-id="28a74-103">\_EFN\_GetManagedExcepStack Function</span></span>

<span data-ttu-id="28a74-104">给定托管的异常对象地址后，将返回其中包含的堆栈跟踪的字符串版本。</span><span class="sxs-lookup"><span data-stu-id="28a74-104">Given a managed exception object address, returns a string version of the stack trace contained inside.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28a74-105">语法</span><span class="sxs-lookup"><span data-stu-id="28a74-105">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedExcepStack(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       StackObjAddr,  
    [out] __out_ecount(cbString) PSTR szStackString,  
    [out] ULONG         cbString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="28a74-106">参数</span><span class="sxs-lookup"><span data-stu-id="28a74-106">Parameters</span></span>  

 `Client`  
 <span data-ttu-id="28a74-107">中正在调试的客户端。</span><span class="sxs-lookup"><span data-stu-id="28a74-107">[in] The client being debugged.</span></span>  
  
 `StackObjAddr`  
 <span data-ttu-id="28a74-108">中托管对象指针，派生自 <xref:System.Exception> 。</span><span class="sxs-lookup"><span data-stu-id="28a74-108">[in] A managed object pointer, derived from <xref:System.Exception>.</span></span>  
  
 <span data-ttu-id="28a74-109">szStackString</span><span class="sxs-lookup"><span data-stu-id="28a74-109">szStackString</span></span>  
 <span data-ttu-id="28a74-110">弄返回的字符串。</span><span class="sxs-lookup"><span data-stu-id="28a74-110">[out] The returned string.</span></span>  
  
 `cbString`  
 <span data-ttu-id="28a74-111">弄字符串缓冲区中的可用字符数。</span><span class="sxs-lookup"><span data-stu-id="28a74-111">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28a74-112">备注</span><span class="sxs-lookup"><span data-stu-id="28a74-112">Remarks</span></span>  

 <span data-ttu-id="28a74-113">如果当前上下文中的线程上没有托管代码，则该函数将返回具有0xa0 的工具值的 HRESULT SOS_E_NOMANAGEDCODE 和错误代码0x1000。</span><span class="sxs-lookup"><span data-stu-id="28a74-113">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28a74-114">要求</span><span class="sxs-lookup"><span data-stu-id="28a74-114">Requirements</span></span>  

 <span data-ttu-id="28a74-115">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="28a74-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28a74-116">**标头：** SOS_Stacktrace。h</span><span class="sxs-lookup"><span data-stu-id="28a74-116">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="28a74-117">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28a74-117">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28a74-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="28a74-118">See also</span></span>

- [<span data-ttu-id="28a74-119">调试全局静态函数</span><span class="sxs-lookup"><span data-stu-id="28a74-119">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
