---
description: 了解详细信息： USER_THREAD 结构
title: USER_THREAD 结构
ms.date: 03/30/2017
api_name:
- USER_THREAD
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- USER_THREAD
helpviewer_keywords:
- USER_THREAD structure [.NET Framework debugging]
ms.assetid: a57c7d71-c4b0-41f9-a964-0c5ee84a3124
topic_type:
- apiref
ms.openlocfilehash: a4bd22073b7610307e67107781bdb68a15ef795f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761263"
---
# <a name="user_thread-structure"></a>USER_THREAD 结构

向调试器提供有关线程的信息。 有关详细信息，请参阅 [INotifySource2：： SetNotifyFilter](inotifysource2-setnotifyfilter-method.md) 方法。  
  
## <a name="syntax"></a>语法  
  
```cpp  
typedef struct tagUSER_THREAD  
{  
    BYTE    *pSidBuffer;  
    DWORD   dwSidLen;  
    DWORD   dwTid;  
} USER_THREAD;  
```  
  
## <a name="members"></a>成员  
  
|成员|说明|  
|------------|-----------------|  
|`pSidBuffer`|线程缓冲区的地址。|  
|`dwSidLen`|线程缓冲区的长度（以字节为单位）。|  
|`dwTid`|线程 ID。|  
  
## <a name="requirements"></a>要求  

 **标头：** ProtocolNotify2 .idl  
  
## <a name="see-also"></a>请参阅

- [SetNotifyFilter 方法](inotifysource2-setnotifyfilter-method.md)
- [诊断符号存储区结构](diagnostics-symbol-store-structures.md)
