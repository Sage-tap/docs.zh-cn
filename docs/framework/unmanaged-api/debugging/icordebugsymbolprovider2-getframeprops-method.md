---
description: 了解详细信息： ICorDebugSymbolProvider2：： GetFrameProps 方法
title: ICorDebugSymbolProvider2::GetFrameProps 方法
ms.date: 03/30/2017
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
ms.openlocfilehash: c0286e423f8f395568ad4df94fac38a7ef91c6bd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659551"
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a>ICorDebugSymbolProvider2::GetFrameProps 方法

返回启动方法相对虚拟地址的方法和具有代码相对虚拟地址的父框架。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
## <a name="parameters"></a>参数  

 `codeRva`  
 [in] 代码相对虚拟地址。  
  
 `pCodeStartRva`  
 [out] 指向方法的启动相对虚拟地址的指针。  
  
 `pParentFrameStartRva`  
 [out] 指向框架的启动相对虚拟地址的指针。  
  
## <a name="remarks"></a>备注  
  
> [!NOTE]
> 此方法仅适用于 .NET Native。  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **标头**：CorDebug.idl、CorDebug.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICorDebugSymbolProvider2 接口](icordebugsymbolprovider2-interface.md)
- [调试接口](debugging-interfaces.md)
