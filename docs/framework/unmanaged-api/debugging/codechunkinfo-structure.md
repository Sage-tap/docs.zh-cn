---
description: 了解详细信息： CodeChunkInfo 结构
title: CodeChunkInfo 结构
ms.date: 03/30/2017
api_name:
- CodeChunkInfo
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CodeChunkInfo
helpviewer_keywords:
- CodeChunkInfo structure [.NET Framework debugging]
ms.assetid: 0f482454-8517-48de-ba7a-d7aedab13bb5
topic_type:
- apiref
ms.openlocfilehash: 017a9ee8c608d4efae98eb0a342a3371ef8ec310
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712345"
---
# <a name="codechunkinfo-structure"></a>CodeChunkInfo 结构

表示内存中的单一代码块。  
  
## <a name="syntax"></a>语法  
  
```cpp  
typedef struct _CodeChunkInfo {  
    CORDB_ADDRESS startAddr;  
    ULONG32       length;  
} CodeChunkInfo;  
```  
  
## <a name="members"></a>成员  
  
|成员|说明|  
|------------|-----------------|  
|`startAddr`|一个 `CORDB_ADDRESS` 值，该值指定块区的起始地址。|  
|`length`|块区的大小（以字节为单位）。|  
  
## <a name="remarks"></a>备注  

 单个代码块是本机代码区域，它是代码对象（例如函数）的一部分。  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **标头：** Cordebug.idl .idl  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [GetCodeChunks 方法](icordebugcode2-getcodechunks-method.md)
- [调试结构](debugging-structures.md)
- [调试](index.md)
