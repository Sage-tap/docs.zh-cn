---
description: 了解详细信息： ICeeGen：： ComputePointer 方法
title: ICeeGen::ComputePointer 方法
ms.date: 03/30/2017
api_name:
- ICeeGen.ComputePointer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::ComputePointer
helpviewer_keywords:
- ICeeGen::ComputePointer method [.NET Framework metadata]
- ComputePointer method [.NET Framework metadata]
ms.assetid: b6b95c04-0f2c-4fcc-a8bc-3b1dcbdba731
topic_type:
- apiref
ms.openlocfilehash: 9319343cc93eae3e4c7b060239d23ad8aeb7d3e6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721167"
---
# <a name="iceegencomputepointer-method"></a>ICeeGen::ComputePointer 方法

确定指定代码节的缓冲区。  
  
 此方法已过时，不应使用。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT ComputePointer (  
    [in]  HCEESECTION  section,  
    [in]  ULONG        RVA,
    [out] UCHAR        **lpBuffer  
);  
```  
  
## <a name="parameters"></a>参数  

 `section`  
 中要为其返回缓冲区的代码部分。  
  
 `RVA`  
 中要为其获取指针的方法的相对虚拟地址。  
  
 `lpBuffer`  
 弄指向返回的缓冲区的指针。  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **标头：** Cor  
  
 **库：** 用作 MsCorEE.dll 中的资源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICeeGen 接口](iceegen-interface.md)
