---
description: 了解详细信息： ICorDebugValue：： GetSize 方法
title: ICorDebugValue::GetSize 方法
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugValue interface [.NET Framework debugging]
- ICorDebugValue::GetSize method [.NET Framework debugging]
ms.assetid: 445a9ee3-e050-4f3a-931a-96b0efb00110
topic_type:
- apiref
ms.openlocfilehash: 3fc2582990d58fa2e42f240dfd3e563eed34e372
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690335"
---
# <a name="icordebugvaluegetsize-method"></a>ICorDebugValue::GetSize 方法

获取此 "ICorDebugValue" 对象的大小（以字节为单位）。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetSize (  
    [out] ULONG32   *pSize  
);  
```  
  
## <a name="parameters"></a>参数  

 `pSize`  
 弄此值对象的大小（以字节为单位）。  
  
## <a name="remarks"></a>备注  

 如果值的类型为引用类型，则此方法返回指针的大小，而不是对象的大小。  
  
 此 `ICorDebugValue::GetSize` 方法 `COR_E_OVERFLOW` 为64位平台上大于 4 GB 的对象返回。 使用 [ICorDebugValue3：： GetSize64](icordebugvalue3-getsize64-method.md) 方法代替大于 4 GB 的对象。  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **标头**：CorDebug.idl、CorDebug.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [GetSize64 方法](icordebugvalue3-getsize64-method.md)
