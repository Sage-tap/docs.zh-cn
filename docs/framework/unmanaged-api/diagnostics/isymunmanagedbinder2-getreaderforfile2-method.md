---
description: 了解详细信息： ISymUnmanagedBinder2：： GetReaderForFile2 方法
title: ISymUnmanagedBinder2::GetReaderForFile2 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder2.GetReaderForFile2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder2::GetReaderForFile2
helpviewer_keywords:
- ISymUnmanagedBinder2::GetReaderForFile2 method [.NET Framework debugging]
- GetReaderForFile2 method [.NET Framework debugging]
ms.assetid: dd92dcaf-403c-464d-a254-21594985dddd
topic_type:
- apiref
ms.openlocfilehash: c1a180ceec07c3087150613365acfce646adc34e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689932"
---
# <a name="isymunmanagedbinder2getreaderforfile2-method"></a>ISymUnmanagedBinder2::GetReaderForFile2 方法

给定元数据接口和文件名后，将返回正确的 [ISymUnmanagedReader](isymunmanagedreader-interface.md) 接口，该接口将读取与模块关联的调试符号。  
  
 与 [ISymUnmanagedBinder：： GetReaderForFile](isymunmanagedbinder-getreaderforfile-method.md) 方法相比，此方法可更广泛地搜索程序数据库 (PDB) 文件。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetReaderForFile2(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a>参数  

 `importer`  
 中指向元数据导入接口的指针。  
  
 `fileName`  
 中指向文件名的指针。  
  
 `searchPath`  
 中指向搜索路径的指针。  
  
 `searchPolicy`  
 中 [CorSymSearchPolicyAttributes](corsymsearchpolicyattributes-enumeration.md) 枚举的一个值，该值指定在搜索符号读取器时要使用的策略。  
  
 `pRetVal`  
 弄设置为返回的 [ISymUnmanagedReader](isymunmanagedreader-interface.md) 接口的指针。  
  
## <a name="return-value"></a>返回值  

 如果该方法成功，则 S_OK;否则，E_FAIL 或其他一些错误代码。  
  
## <a name="requirements"></a>要求  

 **标头：** CorSym，CorSym  
  
## <a name="remarks"></a>备注  

 此版本的方法可在模块旁的其他区域中搜索 PDB 文件。 可以通过组合 [CorSymSearchPolicyAttributes](corsymsearchpolicyattributes-enumeration.md)来控制搜索策略。 例如，将在 `AllowReferencePathAccess | AllowSymbolServerAccess` 可执行文件和符号服务器上查找 PDB，但不查询注册表或使用可执行文件中的路径。 如果 `searchPath` 提供了参数，将始终搜索这些目录。  
  
## <a name="see-also"></a>请参阅

- [ISymUnmanagedBinder2 接口](isymunmanagedbinder2-interface.md)
- [GetReaderForFile 方法](isymunmanagedbinder-getreaderforfile-method.md)
