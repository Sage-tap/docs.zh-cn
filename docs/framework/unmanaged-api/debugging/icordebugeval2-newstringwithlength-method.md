---
description: 了解详细信息： ICorDebugEval2：： NewStringWithLength 方法
title: ICorDebugEval2::NewStringWithLength 方法
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewStringWithLength
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewStringWithLength
helpviewer_keywords:
- NewStringWithLength method [.NET Framework debugging]
- ICorDebugEval2::NewStringWithLength method [.NET Framework debugging]
ms.assetid: d5f54a34-6335-4708-b407-a756ec70fab4
topic_type:
- apiref
ms.openlocfilehash: 23864dabefcb4fc12f73c66bc2d19a6cca1aacf0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693520"
---
# <a name="icordebugeval2newstringwithlength-method"></a>ICorDebugEval2::NewStringWithLength 方法

使用指定的内容创建指定长度的字符串。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT NewStringWithLength (  
    [in] LPCWSTR               string,  
    [in] UINT                  uiLength  
);  
```  
  
## <a name="parameters"></a>参数  

 `string`  
 中指向字符串值的指针。  
  
 `uiLength`  
 中字符串的长度。  
  
## <a name="remarks"></a>备注  

 如果字符串的尾随空字符应在托管字符串中，则该方法的调用方 `NewStringWithLength` 必须确保字符串长度包含结尾的 null 字符。  
  
 始终在当前执行线程的应用程序域中创建字符串。  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **标头**：CorDebug.idl、CorDebug.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
