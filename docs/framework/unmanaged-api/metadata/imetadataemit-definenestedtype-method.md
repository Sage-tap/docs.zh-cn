---
description: 了解详细信息： IMetaDataEmit：:D efineNestedType 方法
title: IMetaDataEmit::DefineNestedType 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineNestedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineNestedType
helpviewer_keywords:
- IMetaDataEmit::DefineNestedType method [.NET Framework metadata]
- DefineNestedType method [.NET Framework metadata]
ms.assetid: 1e994de6-4628-459c-b967-b34be1e9fe4f
topic_type:
- apiref
ms.openlocfilehash: 1b0c5c8d1bffa425b2019a4434042c84a0069907
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753375"
---
# <a name="imetadataemitdefinenestedtype-method"></a>IMetaDataEmit::DefineNestedType 方法

创建类型定义的元数据签名，返回 `mdTypeDef` 该类型的标记，并指定该定义类型是参数所引用的类型的成员 `tdEncloser` 。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT DefineNestedType (
    [in]  LPCWSTR     szTypeDef,  
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[],
    [in]  mdTypeDef   tdEncloser,
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a>参数  

 `szTypeDef`  
 中Unicode 中类型的名称。  
  
 `dwTypeDefFlags`  
 [in] `TypeDef` 属性. 这是一个值的位掩码 `CorTypeAttr` 。  
  
 `tkExtends`  
 中基类的标记。 这是 `mdTypeDef` 或 `mdTypeRef` 令牌。  
  
 `rtkImplements`[]  
 中标记的数组，该数组指定此类或接口实现的接口。  
  
 `tdEncloser`  
 中封闭类型的标记。 数组的最后一个元素必须是 `mdTokenNil` 。  
  
 `ptd`  
 弄 `mdTypeDef` 分配的令牌。  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **标头：** Cor  
  
 **库：** 用作 MSCorEE.dll 中的资源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [IMetaDataEmit 接口](imetadataemit-interface.md)
- [IMetaDataEmit2 接口](imetadataemit2-interface.md)
