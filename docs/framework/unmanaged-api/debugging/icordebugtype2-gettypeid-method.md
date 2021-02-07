---
description: 了解详细信息： ICorDebugType2：： GetTypeID 方法
title: ICorDebugType2：： GetTypeID 方法
ms.date: 03/30/2017
api_name:
- ICorDebugType2.GetTypeID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetTypeID
helpviewer_keywords:
- GetTypeID method, ICorDebugType2 interface [.NET Framework debugging]
- ICorDebugType2.GetTypeID method [.NET Framework debugging]
ms.assetid: 0b933686-226e-4373-92b7-fac579ee7b1a
topic_type:
- apiref
ms.openlocfilehash: 8143ede1a11ee5f73c49fc723920f53430339ed0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738099"
---
# <a name="icordebugtype2gettypeid-method"></a>ICorDebugType2：： GetTypeID 方法

获取此类型的 [COR_TYPEID](cor-typeid-structure.md) 。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetTypeID(  
    ([out] COR_TYPEID *id  
);  
```  
  
## <a name="parameters"></a>参数  

 `id`  
 弄指向此 ICorDebugType 的 [COR_TYPEID](cor-typeid-structure.md) 的指针。  
  
## <a name="return-value"></a>返回值  

 如果成功，则返回值是 `S_OK`；如果失败，则返回失败 `HRESULT` 代码。 这些 `HRESULT` 代码包括：  
  
|返回代码|描述|  
|-----------------|-----------------|  
|`S_OK`|方法成功。 方法已检索到有效 [COR_TYPEID](cor-typeid-structure.md)。|  
|`CORDBG_E_CLASS_NOT_LOADED`|尚未加载类型。|  
|`CORDBG_E_UNSUPPORTED`|不支持该类型。|  
  
## <a name="remarks"></a>备注  

 此方法提供了一个从 ICorDebugType 的映射，该映射表示可能尚未加载到运行时中的类型，也称为一个 [COR_TYPEID](cor-typeid-structure.md)，它用作标识加载到运行时中的类型的不透明句柄。  
  
 如果尚未加载 ICorDebugType 表示的类型，则此方法返回 `CORDBG_E_CLASS_NOT_LOADED` 。  如果该类型不受支持，则返回 `CORDBG_E_UNSUPPORTED` 。  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **标头**：CorDebug.idl、CorDebug.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICorDebugType2 接口](icordebugtype2-interface.md)
