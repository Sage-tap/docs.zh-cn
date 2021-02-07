---
description: 了解详细信息： IMetaDataAssemblyImport：： GetManifestResourceProps 方法
title: IMetaDataAssemblyImport::GetManifestResourceProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetManifestResourceProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetManifestResourceProps
helpviewer_keywords:
- GetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetManifestResourceProps method [.NET Framework metadata]
ms.assetid: 00be4789-ac63-4397-b2ec-1629a5c5a585
topic_type:
- apiref
ms.openlocfilehash: d8f390f8eede5153df282cc30479ceff22fb552d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728252"
---
# <a name="imetadataassemblyimportgetmanifestresourceprops-method"></a>IMetaDataAssemblyImport::GetManifestResourceProps 方法

获取具有指定元数据签名的清单资源的属性集。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetManifestResourceProps (  
    [in]  mdManifestResource   mdmr,
    [out] LPWSTR               szName,
    [in]  ULONG                cchName,
    [out] ULONG                *pchName,
    [out] mdToken              *ptkImplementation,
    [out] DWORD                *pdwOffset,
    [out] DWORD                *pdwResourceFlags  
);  
```  
  
## <a name="parameters"></a>参数  

 `mdmr`  
 中一个 `mdManifestResource` 标记，表示要获取其属性的资源。  
  
 `szName`  
 弄资源的名称。  
  
 `cchName`  
 中的大小（宽字符） `szName` 。  
  
 `pchName`  
 弄一个指针，指向在中实际返回的宽字符数 `szName` 。  
  
 `ptkImplementation`  
 弄一个指针，该指针指向 `mdFile` 包含资源的标记或 `mdAssemblyRef` 表示文件或程序集的标记。  
  
 `pdwOffset`  
 弄一个指向值的指针，该值指定文件中资源开始处的偏移量。  
  
 `pdwResourceFlags`  
 弄一个指针，指向用于描述应用于资源的元数据的标志。 Flags 值是一个或多个 [CorManifestResourceFlags](cormanifestresourceflags-enumeration.md) 值的组合。  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **标头：** Cor  
  
 **库：** 用作 MsCorEE.dll 中的资源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [IMetaDataAssemblyImport 接口](imetadataassemblyimport-interface.md)
