---
description: 了解详细信息： IValidator：： FormatEventInfo 方法
title: IValidator::FormatEventInfo 方法
ms.date: 03/30/2017
api_name:
- IValidator.FormatEventInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FormatEventInfo
helpviewer_keywords:
- IValidator::FormatEventInfo method [.NET Framework hosting]
- FormatEventInfo method, IValidator interface [.NET Framework hosting]
ms.assetid: 4c0c7477-05ba-461b-b21b-cbfba95f1db1
topic_type:
- apiref
ms.openlocfilehash: 28ecf9ab2b14cd2fdd178a4ad9d8e218f7038a9d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99680156"
---
# <a name="ivalidatorformateventinfo-method"></a>IValidator::FormatEventInfo 方法

获取与指定的验证错误相对应的错误消息。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT FormatEventInfo(  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
## <a name="parameters"></a>参数  

 `hVECode`  
 中传递给验证错误处理程序的 HRESULT 值。  
  
 `Context`  
 中一个 `VEContext` 实例，其中包含有关验证错误的上下文信息。  
  
 `msg`  
 [in，out]包含返回的错误消息的字符串。  
  
 `ulMaxLength`  
 中错误消息的最大长度。  
  
 `psa`  
 中一个安全数组，其中包含描述错误的其他参数。  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **标头：** IValidator，IValidator  
  
 **库：** 作为中的资源包含 MSCorEE.dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
