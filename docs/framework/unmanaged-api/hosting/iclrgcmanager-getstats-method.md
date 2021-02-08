---
description: 了解详细信息： ICLRGCManager：： GetStats 方法
title: ICLRGCManager::GetStats 方法
ms.date: 03/30/2017
api_name:
- ICLRGCManager.GetStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager::GetStats
helpviewer_keywords:
- GetStats method, ICLRGCManager interface [.NET Framework hosting]
- ICLRGCManager::GetStats method [.NET Framework hosting]
ms.assetid: ce259d1d-cd81-4490-a7a1-0d0ea0804872
topic_type:
- apiref
ms.openlocfilehash: 94b20fb313f06d73f1e7fafd1f46fefb0da3fe95
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790017"
---
# <a name="iclrgcmanagergetstats-method"></a>ICLRGCManager::GetStats 方法

获取有关公共语言运行时的垃圾回收系统的当前统计信息集。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a>参数  

 `pStats`  
 [in，out]一个 [COR_GC_STATS](cor-gc-stats-structure.md) 实例，其中包含请求的统计信息。  
  
## <a name="return-value"></a>返回值  
  
|HRESULT|说明|  
|-------------|-----------------|  
|S_OK|`GetStats` 已成功返回。|  
|HOST_E_CLRNOTAVAILABLE| (CLR) 的公共语言运行时未加载到进程中，或 CLR 处于无法运行托管代码或成功处理调用的状态。|  
|HOST_E_TIMEOUT|调用超时。|  
|HOST_E_NOT_OWNER|调用方不拥有该锁。|  
|HOST_E_ABANDONED|已阻止的线程或纤程正在等待某个事件时，该事件被取消。|  
|E_FAIL|发生未知的灾难性故障。 方法返回 E_FAIL 后，CLR 在该进程内将不再可用。 对宿主方法的后续调用会返回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>备注  

 CLR 只计算和返回由的字段指定的统计信息 `Flags` `pStats` 。  
  
 将 `Flags` 字段设置为一个或多个 [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) 枚举的值，以指定要设置 [COR_GC_STATS](cor-gc-stats-structure.md) 结构中的哪些统计信息。  
  
 用法的示例如下所示：  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **标头：** Mscoree.dll  
  
 **库：** 作为中的资源包含 MSCorEE.dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [自动内存管理](../../../standard/automatic-memory-management.md)
- [COR_GC_STATS 结构](cor-gc-stats-structure.md)
- [COR_GC_STAT_TYPES 枚举](cor-gc-stat-types-enumeration.md)
- [垃圾回收](../../../standard/garbage-collection/index.md)
- [ICLRControl 接口](iclrcontrol-interface.md)
- [ICLRGCManager 接口](iclrgcmanager-interface.md)
- [CLR 承载接口](clr-hosting-interfaces.md)
- [承载接口](hosting-interfaces.md)
- [承载](index.md)
