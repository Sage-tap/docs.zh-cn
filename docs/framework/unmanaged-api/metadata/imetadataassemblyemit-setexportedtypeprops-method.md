---
description: 了解详细信息： IMetaDataAssemblyEmit：： SetExportedTypeProps 方法
title: IMetaDataAssemblyEmit::SetExportedTypeProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetExportedTypeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetExportedTypeProps
helpviewer_keywords:
- SetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 1c090153-fd5f-46c7-9cff-39a78d992c8f
topic_type:
- apiref
ms.openlocfilehash: 61032abd7b049af29c583e9aee126184af3c78f2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678089"
---
# <a name="imetadataassemblyemitsetexportedtypeprops-method"></a>IMetaDataAssemblyEmit::SetExportedTypeProps 方法

修改指定的 `ExportedType` 元数据结构。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT SetExportedTypeProps (  
    [in] mdExportedType   ct,
    [in] mdToken          tkImplementation,  
    [in] mdTypeDef        tkTypeDef,  
    [in] DWORD            dwExportedTypeFlags  
);  
```  
  
## <a name="parameters"></a>参数  

 `ct`  
 中 `ExportedType` 用于指定要修改的元数据结构的元数据标记。  
  
 `tkImplementation`  
 中类型 `File` 为、或的标记， `AssemblyRef` `ExportedType` 用于指定如何实现此类型。  
  
 `tkTypeDef`  
 中 `TypeDef` 在代码文件中引用的标记。  
  
 `dwExportedTypeFlags`  
 中值的按位组合，用于指定类型的特性。  
  
## <a name="remarks"></a>备注  

 若要创建 `ExportedType` 元数据结构，请使用 [IMetaDataAssemblyEmit：:D efineexportedtype](imetadataassemblyemit-defineexportedtype-method.md) 方法。  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **标头：** Cor  
  
 **库：** 用作 MsCorEE.dll 中的资源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [IMetaDataAssemblyEmit 接口](imetadataassemblyemit-interface.md)
