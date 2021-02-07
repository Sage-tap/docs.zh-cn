---
description: 了解详细信息： IMetaDataEmit：:D efineImportType 方法
title: IMetaDataEmit::DefineImportType 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineImportType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineImportType
helpviewer_keywords:
- DefineImportType method [.NET Framework metadata]
- IMetaDataEmit::DefineImportType method [.NET Framework metadata]
ms.assetid: 37fd27af-8062-4904-ace4-51bb78ec600a
topic_type:
- apiref
ms.openlocfilehash: 7afe0fe400e4eb6e177a06e00b2d69202820804c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753427"
---
# <a name="imetadataemitdefineimporttype-method"></a>IMetaDataEmit::DefineImportType 方法

创建对在当前范围外定义的指定类型的引用，并定义该引用的标记。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT DefineImportType (
    [in]  IMetaDataAssemblyImport  *pAssemImport,
    [in]  const void               *pbHashValue,
    [in]  ULONG                    cbHashValue,
    [in]  IMetaDataImport          *pImport,
    [in]  mdTypeDef                tdImport,
    [in]  IMetaDataAssemblyEmit    *pAssemEmit,
    [out] mdTypeRef                *ptr  
);  
```  
  
## <a name="parameters"></a>参数  

 `pAssemImport`  
 中一个 [IMetaDataAssemblyImport](imetadataassemblyimport-interface.md) 接口，它表示从其导入目标类型的程序集。  
  
 `pbHashValue`  
 中一个数组，其中包含由指定的程序集的哈希 `pAssemImport` 。  
  
 `cbHashValue`  
 [in] `pbHashValue` 数组中的字节数。  
  
 `pImport`  
 中表示要从其导入目标类型的元数据范围的 [IMetaDataImport](imetadataimport-interface.md) 接口。  
  
 `tdImport`  
 中 `mdTypeDef` 指定目标类型的标记。  
  
 `pAssemEmit`  
 中一个 [IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md) 接口，该接口表示要将目标类型导入到其中的程序集。  
  
 `ptr`  
 弄 `mdTypeRef` 在类型引用的当前范围中定义的标记。  
  
## <a name="remarks"></a>备注  

 在调用 [IMetaDataEmit：:D efineimportmember](imetadataemit-defineimportmember-method.md) 方法之前，可以使用 `DefineImportType` 方法在当前作用域中为成员的父类或父接口创建类型引用。  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **标头：** Cor  
  
 **库：** 用作 MSCorEE.dll 中的资源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [IMetaDataEmit 接口](imetadataemit-interface.md)
- [IMetaDataEmit2 接口](imetadataemit2-interface.md)
