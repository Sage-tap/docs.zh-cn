---
description: 了解详细信息： IXCLRDataMethodDefinition：： StartEnumInstances 方法
title: IXCLRDataMethodDefinition：： StartEnumInstances 方法
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition::StartEnumInstances Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition::StartEnumInstances Method
helpviewer.keywords:
- IXCLRDataMethodDefinition::StartEnumInstances Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 74de6360c90766cfec17e6b88a495fe2a70858b4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800820"
---
# <a name="ixclrdatamethoddefinitionstartenuminstances-method"></a>IXCLRDataMethodDefinition：： StartEnumInstances 方法

为给定的的方法实例枚举提供句柄 `IXCLRDataAppDomain` 。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>语法

```cpp
HRESULT StartEnumInstances(
    [in] IXCLRDataAppDomain* appDomain,
    [out] CLRDATA_ENUM *handle
);
```

## <a name="parameters"></a>参数

`appDomain`\
中枚举的 AppDomain。

`handle`\
弄用于枚举实例的句柄。

## <a name="remarks"></a>备注

提供的方法是接口的一部分 `IXCLRDataMethodDefinition` ，并且对应于虚拟方法表的第5个槽。

## <a name="requirements"></a>要求

**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
**标头：** 内容  
**库：** 内容  
**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>请参阅

- [CLRDataSourceType 枚举](clrdatasourcetype-enumeration.md)
- [调试](index.md)
- [IXCLRDataMethodDefinition 接口](ixclrdatamethoddefinition-interface.md)
