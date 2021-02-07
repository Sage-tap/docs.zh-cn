---
description: 了解详细信息： ICorDebugFunction：： GetCurrentVersionNumber 方法
title: ICorDebugFunction::GetCurrentVersionNumber 方法
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetCurrentVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetCurrentVersionNumber
helpviewer_keywords:
- GetCurrentVersionNumber method [.NET Framework debugging]
- ICorDebugFunction::GetCurrentVersionNumber method [.NET Framework debugging]
ms.assetid: c3af1575-cbe6-457a-bc08-c53460edcbc8
topic_type:
- apiref
ms.openlocfilehash: ccc96755ac74624a00b806e3f569f39f2d6059f5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692532"
---
# <a name="icordebugfunctiongetcurrentversionnumber-method"></a>ICorDebugFunction::GetCurrentVersionNumber 方法

获取对此 ICorDebugFunction 对象所表示的函数进行的最新编辑的版本号。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetCurrentVersionNumber (  
    [out] ULONG32 *pnCurrentVersion  
);  
```  
  
## <a name="parameters"></a>参数  

 `pnCurrentVersion`  
 弄指向整数值的指针，该整数值是对此函数进行的最新编辑的版本号。  
  
## <a name="remarks"></a>备注  

 对此函数进行的最新编辑的版本号可能大于函数本身的版本号。 使用 [ICorDebugFunction2：： GetVersionNumber](icordebugfunction2-getversionnumber-method.md) 方法或 [ICorDebugCode：： GetVersionNumber](icordebugcode-getversionnumber-method.md) 方法检索函数的版本号。  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **标头**：CorDebug.idl、CorDebug.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
