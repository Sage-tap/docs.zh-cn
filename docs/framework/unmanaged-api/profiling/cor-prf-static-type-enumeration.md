---
description: 了解详细信息： COR_PRF_STATIC_TYPE 枚举
title: COR_PRF_STATIC_TYPE 枚举
ms.date: 03/30/2017
api_name:
- COR_PRF_STATIC_TYPE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_STATIC_TYPE
helpviewer_keywords:
- COR_PRF_STATIC_TYPE enumeration [.NET Framework profiling]
ms.assetid: 441d7809-5b65-41a5-ba64-2910a8008315
topic_type:
- apiref
ms.openlocfilehash: b7171fe4e9c536d94109d46ae6cad9201a15bab9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789029"
---
# <a name="cor_prf_static_type-enumeration"></a>COR_PRF_STATIC_TYPE 枚举

指示字段是否为静态的，并在字段为静态字段时指示应用于该字段的静态质量。 可以使用按位 "或" 运算组合这些值，以指示该字段具有多个不同的静态质量。  
  
## <a name="syntax"></a>语法  
  
```cpp  
typedef enum {  
    COR_PRF_FIELD_NOT_A_STATIC = 0x0,  
    COR_PRF_FIELD_APP_DOMAIN_STATIC = 0x1,  
    COR_PRF_FIELD_THREAD_STATIC = 0x2,  
    COR_PRF_FIELD_CONTEXT_STATIC = 0x4,  
    COR_PRF_FIELD_RVA_STATIC = 0x8  
} COR_PRF_STATIC_TYPE;  
```  
  
## <a name="members"></a>成员  
  
|成员|说明|  
|------------|-----------------|  
|`COR_PRF_FIELD_NOT_A_STATIC`|此字段不是静态的。|  
|`COR_PRF_FIELD_APP_DOMAIN_STATIC`|此字段为应用程序域静态。|  
|`COR_PRF_FIELD_THREAD_STATIC`|此字段是线程静态的。|  
|`COR_PRF_FIELD_CONTEXT_STATIC`|此字段是上下文静态的。|  
|`COR_PRF_FIELD_RVA_STATIC`|此字段是相对虚拟地址 (RVA) 静态。|  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **头文件：** CorProf.idl、CorProf.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [分析枚举](profiling-enumerations.md)
