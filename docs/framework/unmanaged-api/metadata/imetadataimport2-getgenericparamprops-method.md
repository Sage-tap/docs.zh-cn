---
description: 了解详细信息： IMetaDataImport2：： GetGenericParamProps 方法
title: IMetaDataImport2::GetGenericParamProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetGenericParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetGenericParamProps
helpviewer_keywords:
- IMetaDataImport2::GetGenericParamProps method [.NET Framework metadata]
- GetGenericParamProps method [.NET Framework metadata]
ms.assetid: dbb21e67-712b-49e7-a27c-a1e73ffd46c5
topic_type:
- apiref
ms.openlocfilehash: 06b522531282b4a30cdc8ebf001c16438e8612ce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688723"
---
# <a name="imetadataimport2getgenericparamprops-method"></a>IMetaDataImport2::GetGenericParamProps 方法

获取与指定标记表示的泛型参数关联的元数据。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetGenericParamProps (  
   [in]  mdGenericParam  gp,  
   [out] ULONG           *pulParamSeq,  
   [out] DWORD           *pdwParamFlags,  
   [out] mdToken         *ptOwner,  
   [out] DWORD           *reserved,  
   [out] LPWSTR          wzName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName  
);  
```  
  
## <a name="parameters"></a>参数  

 `gp`  
 中表示要为其返回元数据的泛型参数的标记。  
  
 `pulParamSeq`  
 弄 `Type` 参数在父构造函数或方法中的序号位置。  
  
 `pdwParamFlags`  
 弄用于描述泛型参数的的 [CorGenericParamAttr](corgenericparamattr-enumeration.md) 枚举的值 `Type` 。  
  
 `ptOwner`  
 弄一个 TypeDef 或 MethodDef 标记，它表示参数的所有者。  
  
 `reserved`  
 弄保留以供将来进行扩展。  
  
 `wzName`  
 弄泛型参数的名称。  
  
 `cchName`  
 中缓冲区的大小 `wzName` 。  
  
 `pchName`  
 弄以宽字符返回的名称的大小。  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **标头：** Cor  
  
 **库：** 用作 MsCorEE.dll 中的资源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [IMetaDataImport2 接口](imetadataimport2-interface.md)
- [IMetaDataImport 接口](imetadataimport-interface.md)
