---
description: 了解详细信息： ICorDebugDataTarget2：： GetImageLocation 方法
title: ICorDebugDataTarget2::GetImageLocation 方法
ms.date: 03/30/2017
ms.assetid: 696afe71-5852-478d-a33f-b2d2dbc4b91f
ms.openlocfilehash: f79ba89d3ba467c2e81224d64147c2b5dd5db079
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710486"
---
# <a name="icordebugdatatarget2getimagelocation-method"></a>ICorDebugDataTarget2::GetImageLocation 方法

返回模块基址中的模块路径。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetImageLocation(    [in] CORDB_ADDRESS baseAddress,  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a>参数  

 `baseAddress`  
 中一个 [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) 值，该值表示模块的基址。  
  
 `cchName`  
 [输入] 缓冲器中将接收模块路径的字符数。  
  
 `pcchName`  
 [输出] 指针指向写入 `szName` 缓冲器的字符数。  
  
 `szName`  
 [输出] 模块路径。  
  
## <a name="remarks"></a>备注  
  
> [!NOTE]
> 此方法仅适用于 .NET Native。  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **标头**：CorDebug.idl、CorDebug.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>请参阅

- [“ICor调试数据目标2”接口](icordebugdatatarget2-interface.md)
- [调试接口](debugging-interfaces.md)
