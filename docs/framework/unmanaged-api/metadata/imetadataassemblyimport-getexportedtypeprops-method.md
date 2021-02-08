---
description: 了解详细信息： IMetaDataAssemblyImport：： GetExportedTypeProps 方法
title: IMetaDataAssemblyImport::GetExportedTypeProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetExportedTypeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetExportedTypeProps
helpviewer_keywords:
- GetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 25ca7623-5a55-4f09-b44a-36b03d142278
topic_type:
- apiref
ms.openlocfilehash: 894fb65fb6de76a218489b2a85a2d3c20c572789
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784114"
---
# <a name="imetadataassemblyimportgetexportedtypeprops-method"></a>IMetaDataAssemblyImport::GetExportedTypeProps 方法

获取具有指定元数据签名的导出类型的属性集。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetExportedTypeProps (  
    [in]  mdExportedType    mdct,
    [out] LPWSTR            szName,
    [in]  ULONG             cchName,
    [out] ULONG             *pchName,
    [out] mdToken           *ptkImplementation,
    [out] mdTypeDef         *ptkTypeDef,
    [out] DWORD             *pdwExportedTypeFlags  
);  
```  
  
## <a name="parameters"></a>参数  

 `mdct`  
 中 `mdExportedType` 表示导出类型的元数据标记。  
  
 `szName`  
 弄导出的类型的名称。  
  
 `cchName`  
 中的大小（宽字符） `szName` 。  
  
 `pchName`  
 弄实际返回的宽字符数 `szName`  
  
 `ptkImplementation`  
 弄 `mdFile`、或 `mdAssemblyRef` `mdExportedType` 元数据标记，其中包含或允许访问导出的类型的属性。  
  
 `ptkTypeDef`  
 弄一个指针，指向 `mdTypeDef` 表示文件中的类型的标记。  
  
 `pdwExportedTypeFlags`  
 弄一个指针，指向用于描述应用于导出类型的元数据的标志。 Flags 值可以是一个或多个 [CorTypeAttr](cortypeattr-enumeration.md) 值。  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **标头：** Cor  
  
 **库：** 用作 MsCorEE.dll 中的资源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [IMetaDataAssemblyImport 接口](imetadataassemblyimport-interface.md)
