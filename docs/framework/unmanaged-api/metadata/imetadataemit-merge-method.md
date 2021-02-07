---
description: 了解详细信息： IMetaDataEmit：： Merge 方法
title: IMetaDataEmit::Merge 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.Merge
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::Merge
helpviewer_keywords:
- IMetaDataEmit::Merge method [.NET Framework metadata]
- Merge method [.NET Framework metadata]
ms.assetid: 7596220c-f699-4b6c-8ae7-c83220610650
topic_type:
- apiref
ms.openlocfilehash: 6b78dd20555acf1eaf610ed05d8a37ab6cdeee5c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745939"
---
# <a name="imetadataemitmerge-method"></a>IMetaDataEmit::Merge 方法

将指定的导入范围添加到要合并的范围列表。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT Merge (
    [in]  IMetaDataImport  *pImport,
    [in]  IMapToken        *pHostMapToken,
    [in]  IUnknown         *pHandler
);  
```  
  
## <a name="parameters"></a>参数  

 `pImport`  
 中指向用于标识要合并的导入范围的 [IMetaDataImport](imetadataimport-interface.md) 对象的指针。  
  
 `pIMap`  
 中指向 [IMapToken](imaptoken-interface.md) 对象的指针，该对象指定标记重新映射。  
  
 `pHandler`  
 中指向指定错误的 [IUnknown](/cpp/atl/iunknown) 对象的指针。  
  
## <a name="remarks"></a>备注  

 调用 [IMetaDataEmit：： MergeEnd](imetadataemit-mergeend-method.md) 以触发将元数据合并到单个范围中。  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **标头：** Cor  
  
 **库：** 用作 MSCorEE.dll 中的资源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [IMetaDataEmit 接口](imetadataemit-interface.md)
- [IMetaDataEmit2 接口](imetadataemit2-interface.md)
