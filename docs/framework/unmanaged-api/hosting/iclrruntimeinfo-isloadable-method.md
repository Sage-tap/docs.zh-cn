---
description: 了解详细信息： ICLRRuntimeInfo：： IsLoadable 方法
title: ICLRRuntimeInfo::IsLoadable 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsLoadable
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsLoadable
helpviewer_keywords:
- IsLoadable method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoadable method [.NET Framework hosting]
ms.assetid: 205ca53b-e78e-49b2-9a46-2a7823e96b8c
topic_type:
- apiref
ms.openlocfilehash: cf63212350bfbd18e2a312add72818b163c32d0c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789783"
---
# <a name="iclrruntimeinfoisloadable-method"></a>ICLRRuntimeInfo::IsLoadable 方法

指示是否可将与此接口关联的运行时加载到当前进程，并考虑可能已加载到进程中的其他运行时。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT IsLoadable(  
        [out, retval] BOOL *pbLoadable);  
```  
  
## <a name="parameters"></a>参数  

 `pbLoadable`  
 [out] `true` 如果可以将此运行时加载到当前进程，则为;否则为 `false` 。  
  
## <a name="return-value"></a>返回值  

 此方法返回以下特定 HRESULT 以及表示方法失败的 HRESULT 错误。  
  
|HRESULT|说明|  
|-------------|-----------------|  
|S_OK|该方法已成功完成。|  
|E_POINTER|`pbLoadable` 为 null。|  
  
## <a name="remarks"></a>备注  

 如果已将另一个运行时加载到进程中，并且可以为进程内并行执行加载与此接口关联的运行时，则 `pbLoadable` 返回 `true` 。 如果两个运行时不能并行运行，则 `pbLoadable` 返回 `false` 。 例如，公共语言运行时 (CLR) 版本4可在 CLR 版本2.0 或 CLR 版本1.1 的同一进程中并行运行。 但是，CLR 版本1.1 和 CLR 版本2.0 无法在进程中并行运行。  
  
 如果没有任何运行时加载到进程中，此方法将始终返回 `true` 。  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **标头：** MetaHost  
  
 **库：** 作为中的资源包含 MSCorEE.dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICLRRuntimeInfo 接口](iclrruntimeinfo-interface.md)
- [承载接口](hosting-interfaces.md)
- [承载](index.md)
