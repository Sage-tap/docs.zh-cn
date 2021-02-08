---
description: 了解详细信息： IMetaDataImport：： GetScopeProps 方法
title: IMetaDataImport::GetScopeProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetScopeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetScopeProps
helpviewer_keywords:
- IMetaDataImport::GetScopeProps method [.NET Framework metadata]
- GetScopeProps method [.NET Framework metadata]
ms.assetid: c8ba42d2-d9fa-43cb-bbc0-f33e1e592cb6
topic_type:
- apiref
ms.openlocfilehash: 2ed7c08cc876f467a46fe38c7c27719e5608e623
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789146"
---
# <a name="imetadataimportgetscopeprops-method"></a>IMetaDataImport::GetScopeProps 方法

获取当前元数据范围内的程序集或模块的名称和版本标识符（可选）。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetScopeProps (  
   [out] LPWSTR           szName,  
   [in]  ULONG            cchName,  
   [out] ULONG            *pchName,  
   [out, optional] GUID   *pmvid  
);  
```  
  
## <a name="parameters"></a>参数  

 `szName`  
 弄程序集或模块名称的缓冲区。  
  
 `cchName`  
 中的大小（以宽字符为大小） `szName` 。  
  
 `pchName`  
 弄返回的宽字符数 `szName` 。  
  
 `pmvid`  
 [out，optional]一个指向 GUID 的指针，该 GUID 用于唯一标识程序集或模块的版本。  
  
## <a name="remarks"></a>备注  

 使用 [IMetaDataEmit：： SetModuleProps](imetadataemit-setmoduleprops-method.md) 方法设置这些属性。  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **标头：** Cor  
  
 **库：** 作为中的资源包含 MsCorEE.dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [IMetaDataImport 接口](imetadataimport-interface.md)
- [IMetaDataImport2 接口](imetadataimport2-interface.md)
