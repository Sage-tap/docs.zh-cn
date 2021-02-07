---
description: 了解详细信息： LPOVERLAPPED_COMPLETION_ROUTINE 函数指针
title: LPOVERLAPPED_COMPLETION_ROUTINE 函数指针
ms.date: 03/30/2017
api_name:
- LPOVERLAPPED_COMPLETION_ROUTINE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- LPOVERLAPPED_COMPLETION_ROUTINE
helpviewer_keywords:
- LPOVERLAPPED_COMPLETION_ROUTINE function pointer [.NET Framework hosting]
ms.assetid: 5fb645d9-b818-401c-8c2c-c30d86de58ba
topic_type:
- apiref
ms.openlocfilehash: 6645e6a9746404a4ae355a22cf16e6d164c63bed
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679818"
---
# <a name="lpoverlapped_completion_routine-function-pointer"></a>LPOVERLAPPED_COMPLETION_ROUTINE 函数指针

指向一个函数，该函数在重叠 (即设备的异步) i/o 完成时通知宿主。  
  
 此函数指针在 .NET Framework 4 中已弃用。  
  
## <a name="syntax"></a>语法  
  
```cpp  
typedef VOID (*LPOVERLAPPED_COMPLETION_ROUTINE) (  
    [in] DWORD  dwErrorCode,  
    [in] DWORD  dwNumberOfBytesTransfered,  
    [in] LPVOID lpOverlapped  
);  
```  
  
## <a name="parameters"></a>参数  

 `dwErrorCode`  
 中如果设备已关闭，则为错误代码的值;否则，此值为零。  
  
 关闭设备会导致设备的所有挂起的 i/o 立即完成。  
  
 `dwNumberOfBytesTransfered`  
 中I/o 操作传输的字节数。  
  
 `lpOverlapped`  
 中指向结构的指针，该结构包含用于完成 i/o 请求的信息。  
  
## <a name="remarks"></a>备注  

 指向该函数的 `LPOVERLAPPED_COMPLETION_ROUTINE` 点是回调函数，并且必须由宿主应用程序的编写器实现。 回调函数允许主机处理已完成的 i/o 请求。  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **标头：** Mscoree.dll  
  
 **库：** MSCorWks.dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [弃用的 CLR 承载函数](deprecated-clr-hosting-functions.md)
