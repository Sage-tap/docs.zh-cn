---
description: 了解详细信息： ICLRDebugManager：： BeginConnection 方法
title: ICLRDebugManager::BeginConnection 方法
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.BeginConnection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::BeginConnection
helpviewer_keywords:
- ICLRDebugManager::BeginConnection method [.NET Framework hosting]
- BeginConnection method [.NET Framework hosting]
ms.assetid: bdd98146-ff4d-4150-a264-a4c1a32d31f3
topic_type:
- apiref
ms.openlocfilehash: 9b4ee64ad96bddfd5d7d650b657c6691b27d8c69
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746121"
---
# <a name="iclrdebugmanagerbeginconnection-method"></a>ICLRDebugManager::BeginConnection 方法

在宿主和调试器之间建立新的连接，以将任务列表与标识符和友好名称关联起来。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT BeginConnection (  
    [in] CONNID dwConnectionId,  
    [in, string] wchar_t* szConnectionName  
);  
```  
  
## <a name="parameters"></a>参数  

 `dwConnectionId`  
 中与公共语言运行时的列表关联的标识符 (CLR) 任务。  
  
 `szConnectionName`  
 中与 CLR 任务列表关联的友好名称。  
  
## <a name="return-value"></a>返回值  
  
|HRESULT|说明|  
|-------------|-----------------|  
|S_OK|`BeginConnection` 已成功返回。|  
|HOST_E_CLRNOTAVAILABLE|CLR 未加载到进程中，或 CLR 处于无法运行托管代码或成功处理调用的状态。|  
|HOST_E_TIMEOUT|调用超时。|  
|HOST_E_NOT_OWNER|调用方不拥有该锁。|  
|HOST_E_ABANDONED|已阻止的线程或纤程正在等待某个事件时，该事件被取消。|  
|E_FAIL|发生未知的灾难性故障。 方法返回 E_FAIL 后，CLR 在该进程内将不再可用。 对宿主方法的后续调用会返回 HOST_E_CLRNOTAVAILABLE。|  
|E_INVALIDARG|`dwConnectionId` 为零，或 `BeginConnection` 已使用此值调用 `dwConnectionId` ，或为 `szConnectionName` null。|  
|E_OUTOFMEMORY|无法分配足够的内存来保存与此连接关联的任务列表。|  
  
## <a name="remarks"></a>备注  

 [ICLRDebugManager](iclrdebugmanager-interface.md) 提供了三种方法： `BeginConnection` 、 [SetConnectionTasks](iclrdebugmanager-setconnectiontasks-method.md)和 [EndConnection](iclrdebugmanager-endconnection-method.md)，用于将任务列表与标识符和友好名称关联起来。  
  
> [!IMPORTANT]
> 对于每组任务，这三种方法都必须按特定的顺序进行调用。 `BeginConnection` 首先调用以建立新连接。 `SetConnectionTasks` 在旁边调用，提供要与该连接相关联的一组任务。 `EndConnection` 最后调用，以删除任务列表与标识符和友好名称之间的关联。但是，可以嵌套不同连接的调用。  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **标头：** Mscoree.dll  
  
 **库：** 作为中的资源包含 MSCorEE.dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICLRControl 接口](iclrcontrol-interface.md)
- [ICLRDebugManager 接口](iclrdebugmanager-interface.md)
- [EndConnection 方法](iclrdebugmanager-endconnection-method.md)
- [SetConnectionTasks 方法](iclrdebugmanager-setconnectiontasks-method.md)
- [IHostControl 接口](ihostcontrol-interface.md)
