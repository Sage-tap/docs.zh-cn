---
description: 了解详细信息： ICorDebugThread：： EnumerateChains 方法
title: ICorDebugThread::EnumerateChains 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread.EnumerateChains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::EnumerateChains
helpviewer_keywords:
- EnumerateChains method [.NET Framework debugging]
- ICorDebugThread::EnumerateChains method [.NET Framework debugging]
ms.assetid: ec00bc21-117e-4acd-9301-2cfafd5be8d3
topic_type:
- apiref
ms.openlocfilehash: b9184a1b298e1d29970c5e56ceca76715b0ed096
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659291"
---
# <a name="icordebugthreadenumeratechains-method"></a>ICorDebugThread::EnumerateChains 方法

获取一个接口指针，该指针指向包含此 ICorDebugThread 对象中所有堆栈链的 ICorDebugChainEnum 枚举器。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT EnumerateChains (  
    [out] ICorDebugChainEnum **ppChains  
);  
```  
  
## <a name="parameters"></a>参数  

 `ppChains`  
 弄指向对象地址的指针，该 `ICorDebugChainEnum` 对象允许枚举此线程中的所有堆栈链，从活动 (开始，即最近的) 链。  
  
## <a name="remarks"></a>备注  

 堆栈链表示线程的物理调用堆栈。 以下情况会创建堆栈链边界：  
  
- 托管到非托管或非托管的转换。  
  
- 上下文切换。  
  
- 用户线程的调试器劫持。  
  
 在单个上下文中运行纯托管代码的线程的简单情况下，线程与堆栈链之间存在一对一的对应关系。  
  
 调试器可能需要将所有线程的物理调用堆栈重新排列为逻辑调用堆栈。 这涉及到通过其调用方/被调用方关系对所有线程链进行排序并 regrouping 它们。  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **标头**：CorDebug.idl、CorDebug.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
