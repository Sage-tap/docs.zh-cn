---
description: 了解详细信息： StrongNameCompareAssemblies 函数
title: StrongNameCompareAssemblies 函数
ms.date: 03/30/2017
api_name:
- StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameCompareAssemblies
helpviewer_keywords:
- StrongNameCompareAssemblies function [.NET Framework strong naming]
ms.assetid: 763f2375-efc6-4219-8806-a3b0567ef72b
topic_type:
- apiref
ms.openlocfilehash: e59bb96a89dc1e1cf8b809c3e0d538aaffe83b8e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736485"
---
# <a name="strongnamecompareassemblies-function"></a>StrongNameCompareAssemblies 函数

确定两个程序集是否仅是强名称签名不同。  
  
 此函数已弃用。 改为使用 [ICLRStrongName：： StrongNameCompareAssemblies](../hosting/iclrstrongname-strongnamecompareassemblies-method.md) 方法。  
  
## <a name="syntax"></a>语法  
  
```cpp  
BOOLEAN StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a>参数  

 `wszAssembly1`  
 中第一个程序集的路径。  
  
 `wszAssembly2`  
 中第二个程序集的路径。  
  
 `pdwResult`  
 弄以下值之一：  
  
- `SN_CMP_DIFFERENT` (0) -指定程序集包含不同的数据。  
  
- `SN_CMP_IDENTICAL` (1) -指定程序集完全相同，包括它们的签名和校验和。  
  
- `SN_CMP_SIGONLY` (2) -指定程序集不同于签名和校验和。  
  
## <a name="return-value"></a>返回值  

 `true` 成功完成时;否则为 `false` 。  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **标头：** Stackexchange.redis.strongname  
  
 **库：** 作为中的资源包含 MsCorEE.dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="remarks"></a>备注  

 程序集的强名称签名由程序集的文本名称、版本、区域性和公钥标记组成。  
  
 如果 `StrongNameCompareAssemblies` 函数未成功完成，请调用 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 函数来检索上次生成的错误。  
  
## <a name="see-also"></a>请参阅

- [StrongNameCompareAssemblies 方法](../hosting/iclrstrongname-strongnamecompareassemblies-method.md)
- [ICLRStrongName 接口](../hosting/iclrstrongname-interface.md)
