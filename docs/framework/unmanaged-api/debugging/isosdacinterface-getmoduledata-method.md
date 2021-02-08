---
description: 了解详细信息： ISOSDacInterface：： GetModuleData 方法
title: ISOSDacInterface：： GetModuleData 方法
ms.date: 02/01/2019
api.name:
- ISOSDacInterface::GetModuleData Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetModuleData Method
helpviewer.keywords:
- ISOSDacInterface::GetModuleData Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: c01f55d55d5ee9082dee4b3adb3022bb17807aa2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790381"
---
# <a name="isosdacinterfacegetmoduledata-method"></a>ISOSDacInterface：： GetModuleData 方法

提取与在给定地址加载的模块对应的数据。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>语法

```cpp
HRESULT GetModuleData(
    CLRDATA_ADDRESS moduleAddr,
    DacpModuleData *data
);
```

## <a name="parameters"></a>参数

`moduleAddr`\
中要为其检索信息的模块的地址。

`data`\
弄用于保存已加载模块的信息的 [DacpModuleData 结构](dacpmoduledata-structure.md) 。

## <a name="remarks"></a>备注

提供的方法是接口的一部分 `ISOSDacInterface` ，并且对应于虚拟方法表的第14个槽。

## <a name="requirements"></a>要求

**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
**标头：** 内容  
**库：** 内容  
**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>请参阅

- [调试](index.md)
- [ISOSDacInterface 接口](isosdacinterface-interface.md)
