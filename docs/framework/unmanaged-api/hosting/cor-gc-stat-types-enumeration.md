---
description: 了解详细信息： COR_GC_STAT_TYPES 枚举
title: COR_GC_STAT_TYPES 枚举
ms.date: 03/30/2017
api_name:
- COR_GC_STAT_TYPES
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_STAT_TYPES
helpviewer_keywords:
- COR_GC_STAT_TYPES enumeration [.NET Framework hosting]
ms.assetid: fc51d6db-f7f8-408b-b93d-c166fc712c99
topic_type:
- apiref
ms.openlocfilehash: c4ea3175c777d49a5d6cffdf506f42e479784971
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799795"
---
# <a name="cor_gc_stat_types-enumeration"></a>COR_GC_STAT_TYPES 枚举

指定要为垃圾回收记录的统计信息。  
  
## <a name="syntax"></a>语法  
  
```cpp  
typedef enum {  
    COR_GC_COUNTS                 = 0x00000001  
    COR_GC_MEMORYUSAGE            = 0x00000002  
} COR_GC_STAT_TYPES;  
```  
  
## <a name="remarks"></a>备注  

 此枚举指定 [COR_GC_STATS](cor-gc-stats-structure.md) 结构中的哪些统计信息由 [ICLRGCManager：： GetStats](iclrgcmanager-getstats-method.md) 方法设置。  
  
## <a name="members"></a>成员  
  
|成员|说明|  
|------------|-----------------|  
|`COR_GC_COUNTS`|记录为每个代执行的垃圾回收数。|  
|`COR_GC_MEMORYUSAGE`|记录内存使用情况和垃圾回收大小统计信息。|  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **标头：** GCHost，GCHost  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [COR_GC_STATS 结构](cor-gc-stats-structure.md)
- [承载枚举](hosting-enumerations.md)
