---
description: 了解详细信息： CorManifestResourceFlags 枚举
title: CorManifestResourceFlags 枚举
ms.date: 03/30/2017
api_name:
- CorManifestResourceFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorManifestResourceFlags
helpviewer_keywords:
- CorManifestResourceFlags enumeration [.NET Framework metadata]
ms.assetid: 1b0306b7-622b-4b57-8edc-3c713bb147ae
topic_type:
- apiref
ms.openlocfilehash: a863e1248bf5274e12fc16d2edea6b28dd493963
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784400"
---
# <a name="cormanifestresourceflags-enumeration"></a>CorManifestResourceFlags 枚举

指示程序集清单中编码的资源的可见性。  
  
## <a name="syntax"></a>语法  
  
```cpp  
typedef enum CorManifestResourceFlags {  
  
    mrVisibilityMask        =   0x0007,  
    mrPublic                =   0x0001,  
    mrPrivate               =   0x0002  
  
} CorManifestResourceFlags;  
```  
  
## <a name="members"></a>成员  
  
|成员|说明|  
|------------|-----------------|  
|`mrVisibilityMask`|保留。|  
|`mrPublic`|资源是公共的。|  
|`mrPrivate`|资源是专用的。|  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **标头：** Corhdr。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [元数据枚举](metadata-enumerations.md)
