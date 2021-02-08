---
description: 了解详细信息： ISymUnmanagedENCUpdate：： UpdateSymbolStore2 方法
title: ISymUnmanagedENCUpdate::UpdateSymbolStore2 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.UpdateSymbolStore2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::UpdateSymbolStore2
helpviewer_keywords:
- ISymUnmanagedENCUpdate::UpdateSymbolStore2 method [.NET Framework debugging]
- UpdateSymbolStore2 method [.NET Framework debugging]
ms.assetid: 35588317-6184-485c-ab41-4b15fc1765d9
topic_type:
- apiref
ms.openlocfilehash: f2e5cbf51c1bab3a538fbf5a3e5824739fa3b250
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790134"
---
# <a name="isymunmanagedencupdateupdatesymbolstore2-method"></a>ISymUnmanagedENCUpdate::UpdateSymbolStore2 方法

如果行信息满足要求，则允许编译器省略未从程序数据库 (PDB) 流中修改的函数。 可以通过旧的 PDB 行信息和函数中所有行的一个增量来确定正确的行信息。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT UpdateSymbolStore2(  
    [in]  IStream      *pIStream,  
    [in]  SYMLINEDELTA* pDeltaLines,  
    [in]  ULONG         cDeltaLines);  
```  
  
## <a name="parameters"></a>参数  

 `pIStream`  
 中一个指针，指向包含行信息的 [IStream](/windows/desktop/api/objidl/nn-objidl-istream) 。  
  
 `pDeltaLines`  
 中指向 [SYMLINEDELTA](symlinedelta-structure.md) 结构的指针，该结构包含已更改的行。  
  
 `cDeltaLines`  
 中 `ULONG` ，它表示已更改的行数。  
  
## <a name="return-value"></a>返回值  

 如果该方法成功，则 S_OK;否则，E_FAIL 或其他一些错误代码。  
  
## <a name="requirements"></a>要求  

 **标头：** CorSym，CorSym  
  
## <a name="see-also"></a>请参阅

- [ISymUnmanagedENCUpdate 接口](isymunmanagedencupdate-interface.md)
