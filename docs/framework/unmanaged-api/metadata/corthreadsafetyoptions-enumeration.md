---
description: 了解详细信息： CorThreadSafetyOptions 枚举
title: CorThreadSafetyOptions 枚举
ms.date: 03/30/2017
api_name:
- CorThreadSafetyOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorThreadSafetyOptions
helpviewer_keywords:
- CorThreadSafetyOptions enumeration [.NET Framework metadata]
ms.assetid: dae07d9b-df51-488c-b17e-52d6e48217bd
topic_type:
- apiref
ms.openlocfilehash: 7915bcf5e7b71fa84ea83642467c1600cd38712d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707314"
---
# <a name="corthreadsafetyoptions-enumeration"></a>CorThreadSafetyOptions 枚举

指定用于选择线程安全性选项的标志。

## <a name="syntax"></a>语法

```cpp
typedef enum CorThreadSafetyOptions {
    MDThreadSafetyDefault       = 0x00000000,
    MDThreadSafetyOff           = 0x00000000,
    MDThreadSafetyOn            = 0x00000001,
} CorThreadSafetyOptions;
```

## <a name="members"></a>成员

|成员|说明|
|------------|-----------------|
|`MDThreadSafetyDefault`|默认值。 与 `MDThreadSafetyOff` 相同。|
|`MDThreadSafetyOff`|指示无法设置读取器/写入器锁。|
|`MDThreadSafetyOn`|指示可以设置读取器/写入器锁。|

## <a name="requirements"></a>要求

**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。

**标头：** Corhdr。h

**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>请参阅

- [元数据枚举](metadata-enumerations.md)
