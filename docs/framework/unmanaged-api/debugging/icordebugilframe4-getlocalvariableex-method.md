---
description: 了解详细信息： ICorDebugILFrame4：： GetLocalVariableEx 方法
title: ICorDebugILFrame4::GetLocalVariableEx 方法
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.GetCodeEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 0c8676f8-ca0d-4998-b64d-fefac7e38912
topic_type:
- apiref
ms.openlocfilehash: 4eb6b3abbaf05c0373a487d9bd9d575b58a9af49
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791213"
---
# <a name="icordebugilframe4getlocalvariableex-method"></a>ICorDebugILFrame4::GetLocalVariableEx 方法

[仅在 .NET Framework 4.5.2 及更高版本中受支持]  
  
 获取此中间语言 (IL) 堆栈帧中指定的局部变量的值，并且（可选）访问在探查器 ReJIT 检测中添加的变量。  
  
## <a name="syntax"></a>语法  
  
```cpp
HRESULT GetLocalVariableEx(  
   [in] ILCodeKind flags,
   [in] DWORD dwIndex,
   [out] ICorDebugValue **ppValue  
);  
```  
  
## <a name="parameters"></a>参数  

 `flags`  
 中一个 [ILCodeKind](ilcodekind-enumeration.md) 枚举成员，用于指定在探查器 ReJIT 检测中添加的变量是否包含在帧中。  
  
 `dwIndex`  
 [in] IL 堆栈帧中局部变量的索引。  
  
 `ppValue`  
 弄指向表示检索到的值的 "ICorDebugValue" 对象地址的指针。  
  
## <a name="remarks"></a>备注  

 此方法类似于 [GetLocalVariable](icordebugilframe-getlocalvariable-method.md) 方法，不同之处在于它还可以访问在探查器 ReJIT 检测中添加的变量。 使用的值调用此方法 `flags` `ILCODE_ORIGINAL_IL` 等效于调用 [GetLocalVariable](icordebugilframe-getlocalvariable-method.md); 如果使用附加的局部变量检测方法，则不能访问这些变量。 `ILCODE_REJIT_IL` 使调试器能够访问在探查器 ReJIT 检测中添加的局部变量。 如果未检测到 IL，则此方法将返回 `E_INVALIDARG`。  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **标头**：CorDebug.idl、CorDebug.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICorDebugILFrame4 接口](icordebugilframe4-interface.md)
- [调试接口](debugging-interfaces.md)
- [ReJIT： How-To 指南](/archive/blogs/davbr/rejit-a-how-to-guide)
