---
description: 了解详细信息： IMetaDataEmit：:D efineMethodImpl 方法
title: IMetaDataEmit::DefineMethodImpl 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMethodImpl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMethodImpl
helpviewer_keywords:
- DefineMethodImpl method [.NET Framework metadata]
- IMetaDataEmit::DefineMethodImpl method [.NET Framework metadata]
ms.assetid: 9dcc8b3d-33ee-4c7c-8d6f-322c57b94a0f
topic_type:
- apiref
ms.openlocfilehash: 9c79d713e61bfcc7b3191e570ed727b128422bf1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753401"
---
# <a name="imetadataemitdefinemethodimpl-method"></a>IMetaDataEmit::DefineMethodImpl 方法

创建一个定义，用于实现从接口继承的方法，并返回该方法实现定义的标记。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT DefineMethodImpl (
    [in]  mdTypeDef         td,
    [in]  mdToken           tkBody,
    [in]  mdToken           tkDecl  
);  
```  
  
## <a name="parameters"></a>参数  

 `td`  
 中 `mdTypedef` 实现类的标记。  
  
 `tkBody`  
 中 `mdMethodDef` `mdMemberRef` 代码主体的或标记。  
  
 `tkDecl`  
 中 `mdMethodDef` `mdMemberRef` 要实现的接口方法的或标记。  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **标头：** Cor  
  
 **库：** 用作 MSCorEE.dll 中的资源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [IMetaDataEmit 接口](imetadataemit-interface.md)
- [IMetaDataEmit2 接口](imetadataemit2-interface.md)
