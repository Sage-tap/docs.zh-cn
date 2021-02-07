---
description: 了解详细信息： ICorProfilerInfo2：： GetAppDomainStaticAddress 方法
title: ICorProfilerInfo2::GetAppDomainStaticAddress 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetAppDomainStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetAppDomainStaticAddress
helpviewer_keywords:
- ICorProfilerInfo2::GetAppDomainStaticAddress method [.NET Framework profiling]
- GetAppDomainStaticAddress method [.NET Framework profiling]
ms.assetid: 2a9e0ea7-a9e2-4817-b1c4-fcf15b215ea9
topic_type:
- apiref
ms.openlocfilehash: 4ef8511e75a18f7626fa7a30ea194140de051bb2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753228"
---
# <a name="icorprofilerinfo2getappdomainstaticaddress-method"></a>ICorProfilerInfo2::GetAppDomainStaticAddress 方法

获取指定应用程序域静态字段在指定应用程序域范围内的地址。  
  
## <a name="syntax"></a>语法  
  
```cpp  
RESULT GetAppDomainStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] AppDomainID appDomainId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a>参数  

 `classId`  
 中包含请求的应用程序域静态字段的类的类 ID。  
  
 `fieldToken`  
 中请求的应用程序域静态字段的元数据标记。  
  
 `appDomainId`  
 中作为所请求的静态字段的作用域的应用程序域的 ID。  
  
 `ppAddress`  
 弄指向指定应用程序域中的静态字段的地址的指针。  
  
## <a name="remarks"></a>备注  

 此 `GetAppDomainStaticAddress` 方法可能会返回以下内容之一：  
  
- 如果未在指定的上下文中为给定的静态字段分配地址，则 CORPROF_E_DATAINCOMPLETE HRESULT。  
  
- 可能位于垃圾回收堆中的对象的地址。 这些地址可能会在垃圾回收后失效，因此，在垃圾回收后，探查器不应假定它们是有效的。  
  
 在类的类构造函数完成之前， `GetAppDomainStaticAddress` 将为其所有静态字段返回 CORPROF_E_DATAINCOMPLETE，不过，某些静态字段可能已经初始化并为垃圾回收对象提供了根。  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **头文件：** CorProf.idl、CorProf.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICorProfilerInfo 接口](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 接口](icorprofilerinfo2-interface.md)
