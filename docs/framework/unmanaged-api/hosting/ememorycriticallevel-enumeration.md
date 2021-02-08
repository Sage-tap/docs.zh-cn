---
description: 了解详细信息： EMemoryCriticalLevel 枚举
title: EMemoryCriticalLevel 枚举
ms.date: 03/30/2017
api_name:
- EMemoryCriticalLevel
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EMemoryCriticalLevel
helpviewer_keywords:
- EMemoryCriticalLevel enumeration [.NET Framework hosting]
ms.assetid: 2ca8a7a2-7b54-4ba3-8e73-277c7df485f3
topic_type:
- apiref
ms.openlocfilehash: 88965a29164de1ec7b01c2fcc8f51415127e69fd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785427"
---
# <a name="ememorycriticallevel-enumeration"></a>EMemoryCriticalLevel 枚举

包含一些值，这些值指示在请求特定内存分配但无法满足时，失败所造成的影响。  
  
## <a name="syntax"></a>语法  
  
```cpp  
typedef enum {  
    eTaskCritical      = 0,  
    eAppDomainCritical = 1,  
    eProcessCritical   = 2  
} EMemoryCriticalLevel;  
```  
  
## <a name="members"></a>成员  
  
|成员|说明|  
|------------|-----------------|  
|`eAppDomainCritical`|指示分配对于在已请求分配的域中执行托管代码是至关重要的。 如果无法分配内存，则 CLR 无法保证域仍可用。 主机决定当无法满足分配时要执行的操作。 它可以指示 CLR `AppDomain` 自动中止，或通过在 [ICLRPolicyManager](iclrpolicymanager-interface.md)上调用方法来使其保持运行。|  
|`eProcessCritical`|指示分配对于进程中的托管代码执行至关重要。 此值在启动和运行终结器时使用。 如果无法分配内存，则 CLR 无法在进程中运行。 如果分配失败，则会有效地禁用 CLR。 对 CLR 的所有后续调用都将失败，并 HOST_E_CLRNOTAVAILABLE。|  
|`eTaskCritical`|指示分配对于运行已请求分配的任务至关重要。 如果无法分配内存，则 CLR 无法保证任务能够执行。 发生故障时，CLR 将 <xref:System.Threading.ThreadAbortException> 在物理操作系统线程上引发。|  
  
## <a name="remarks"></a>备注  

 [IHostMemoryManager](ihostmemorymanager-interface.md)和[IHostMAlloc](ihostmalloc-interface.md)接口中定义的内存分配方法采用此类型的参数。 根据故障的严重性，主机可以决定是立即对分配请求进行故障转移还是要等待，直到它得以满足。  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **标头：** Mscoree.dll  
  
 **库：** MSCorEE.dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICLRMemoryNotificationCallback 接口](iclrmemorynotificationcallback-interface.md)
- [承载枚举](hosting-enumerations.md)
