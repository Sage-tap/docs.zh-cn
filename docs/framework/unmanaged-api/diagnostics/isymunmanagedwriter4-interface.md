---
description: 了解详细信息： ISymUnmanagedWriter4 接口
title: ISymUnmanagedWriter4 接口
ms.date: 03/30/2017
ms.assetid: 4af5e8c0-987d-405e-b934-8b9e70fcae6e
ms.openlocfilehash: 3814d7e2728f28d224a4e9a6d99f699f220e8a4d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761676"
---
# <a name="isymunmanagedwriter4-interface"></a>ISymUnmanagedWriter4 接口

ISymUnmanagedWriter4 接口。  
  
## <a name="syntax"></a>语法  
  
```idl  
[object,uuid(BC7E3F53-F458-4C23-9DBD-A189E6E96594),pointer_default(unique)]interface ISymUnmanagedWriter4 : ISymUnmanagedWriter3  
```  
  
## <a name="methods"></a>方法  

 此接口包含下列方法：  
  
|方法|说明|  
|------------|-----------------|  
|[GetDebugInfoWithPadding 方法](isymunmanagedwriter4-getdebuginfowithpadding-method.md)|与 [GetDebugInfo 方法](isymunmanagedwriter-getdebuginfo-method.md) 相同，不同之处在于，在终止 null 字符后使用零填充路径字符串，使字符串数据成为固定大小的字符串数据 `MAX_PATH` 。 仅当路径字符串长度本身小于时才会提供填充 `MAX_PATH` 。<br /><br /> 这样可以更轻松地编写不同 PE 文件的工具。|  
  
## <a name="requirements"></a>要求  

 **标头：** CorSym，CorSym  
  
## <a name="see-also"></a>请参阅

- [诊断符号存储区接口](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter3 接口](isymunmanagedwriter3-interface.md)
