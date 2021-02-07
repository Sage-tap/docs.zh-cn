---
description: 了解详细信息： ICorDebugProcess5：： GetTypeForTypeID 方法
title: ICorDebugProcess5::GetTypeForTypeID 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeForTypeID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeForTypeID
helpviewer_keywords:
- GetTypeForTypeID method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetTypeForTypeID method [.NET Framework debugging]
ms.assetid: e0eed5a8-fa6d-4818-bd00-7babcea30325
topic_type:
- apiref
ms.openlocfilehash: a18543b0afc867dc3796264ac1d08a775c73ca59
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746368"
---
# <a name="icordebugprocess5gettypefortypeid-method"></a>ICorDebugProcess5::GetTypeForTypeID 方法

将类型标识符转换为 ICorDebugType 值。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetTypeForTypeID(  
    [in] COR_TYPEID id, [  
    out] ICorDebugType **ppType  
);  
```  
  
## <a name="parameters"></a>参数  

 `id`  
 中类型标识符。  
  
 `ppType`  
 弄指向 ICorDebugType 对象地址的指针。  
  
## <a name="remarks"></a>备注  

 在某些情况下，返回类型标识符的方法可能返回 null `COR_TYPEID` 值。 如果此值作为 `id` 参数传递，则 `GetTypeForTypeID` 方法将失败，并返回 `E_FAIL` 。  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **标头**：CorDebug.idl、CorDebug.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICorDebugProcess5 接口](icordebugprocess5-interface.md)
- [调试接口](debugging-interfaces.md)
