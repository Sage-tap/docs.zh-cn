---
description: 了解详细信息： DacpModuleData 结构
title: DacpModuleData 结构
ms.date: 02/01/2019
api.name:
- DacpModuleData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpModuleData Structure
helpviewer.keywords:
- DacpModuleData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 376a49ab78db08e5906e8d33389cdc45fe76e81e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661566"
---
# <a name="dacpmoduledata-structure"></a>DacpModuleData 结构

定义模块的运行时信息的传输缓冲区。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>语法

```cpp
struct DacpModuleData
{
    CLRDATA_ADDRESS Address;
    CLRDATA_ADDRESS File;
    CLRDATA_ADDRESS  ilBase;
    char payLoad[132];
};
```

## <a name="members"></a>成员

| 成员    | 说明                                                             |
| --------- | ----------------------------------------------------------------------- |
| `Address` | Module 对象的地址。                                           |
| `File`    | 指向可移植可执行文件 (PE) 文件的指针。                       |
| `ilBase`  | 加载的映像的基址。                                 |
| `payLoad` | 运行时使用的其他模块信息的负载缓冲区。 |

## <a name="remarks"></a>备注

此结构存在于运行时中，并且不会通过任何标头或库文件公开。 若要使用它，请定义上面指定的结构。

## <a name="requirements"></a>要求

**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
**标头：** 内容  
**库：** 内容  
**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>请参阅

- [调试](index.md)
- [调试结构](debugging-structures.md)
