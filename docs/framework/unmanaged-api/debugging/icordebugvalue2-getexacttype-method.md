---
description: 了解详细信息： ICorDebugValue2：： GetExactType 方法
title: ICorDebugValue2::GetExactType 方法
ms.date: 03/30/2017
api_name:
- ICorDebugValue2.GetExactType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue2::GetExactType
helpviewer_keywords:
- ICorDebugValue2::GetExactType method [.NET Framework debugging]
- GetExactType method [.NET Framework debugging]
ms.assetid: 8e9aae1b-d1b7-4b6e-b577-6faf36dcec85
topic_type:
- apiref
ms.openlocfilehash: d0ef08b119106ced89ec2094b5bf67d0c874b6bc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690296"
---
# <a name="icordebugvalue2getexacttype-method"></a>ICorDebugValue2::GetExactType 方法

获取一个接口指针，该指针指向表示 <xref:System.Type> 此值的的 "ICorDebugType" 对象。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetExactType (  
    [out] ICorDebugType   **ppType  
);  
```  
  
## <a name="parameters"></a>参数  

 `ppType`  
 弄指向对象地址的指针，该 `ICorDebugType` 对象表示 <xref:System.Type> 此 "ICorDebugValue2" 对象表示的值的。  
  
## <a name="remarks"></a>备注  

 一般识别 `GetExactType` 方法取代了 [ICorDebugObjectValue：： GetClass](icordebugobjectvalue-getclass-method.md) 和 [ICorDebugValue：： GetType](icordebugvalue-gettype-method.md) 方法，其中每个方法都返回值类型的相关信息。  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **标头**：CorDebug.idl、CorDebug.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅
