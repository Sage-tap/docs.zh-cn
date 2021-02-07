---
description: 了解详细信息： CorMarkThreadInThreadPool 函数
title: CorMarkThreadInThreadPool 函数
ms.date: 03/30/2017
api_name:
- CorMarkThreadInThreadPool
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CorMarkThreadInThreadPool
helpviewer_keywords:
- CorMarkThreadInThreadPool function [.NET Framework hosting]
ms.assetid: 3f958d41-e82e-4ec3-ae6f-16c7b3b31e3e
topic_type:
- apiref
ms.openlocfilehash: 68d945870075f2f8c06fe76b7a71e2f806078694
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716927"
---
# <a name="cormarkthreadinthreadpool-function"></a>CorMarkThreadInThreadPool 函数

标记当前正在执行的线程池线程以执行托管代码。 从 .NET Framework 版本2.0 开始，此函数不起作用。 这不是必需的，并且可以从代码中删除。 此函数在 .NET Framework 4 中已弃用。  
  
## <a name="syntax"></a>语法  
  
```cpp  
void CorMarkThreadInThreadPool ();  
```  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **标头：** Mscoree.dll  
  
 **库：** MSCorEE.dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [弃用的 CLR 承载函数](deprecated-clr-hosting-functions.md)
