---
description: 了解详细信息： ICLRHostProtectionManager 接口
title: ICLRHostProtectionManager 接口
ms.date: 03/30/2017
api_name:
- ICLRHostProtectionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostProtectionManager
helpviewer_keywords:
- ICLRHostProtectionManager interface [.NET Framework hosting]
ms.assetid: ce2770ae-23d0-45d9-8bcf-46504ac5020e
topic_type:
- apiref
ms.openlocfilehash: 60d27a8c1a24720bbfdcde52a5495425279d5ac4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689223"
---
# <a name="iclrhostprotectionmanager-interface"></a>ICLRHostProtectionManager 接口

允许宿主阻止在部分受信任的代码中运行特定的托管类、方法、属性和字段。  
  
## <a name="methods"></a>方法  
  
|方法|说明|  
|------------|-----------------|  
|[SetEagerSerializeGrantSets](iclrhostprotectionmanager-seteagerserializegrantsets-method.md)|确保某些极少数争用条件可能会导致严重的公共语言运行时 (CLR) 错误。|  
|[SetProtectedCategories 方法](iclrhostprotectionmanager-setprotectedcategories-method.md)|指定应阻止在部分受信任代码中运行的托管类型和成员的类别。|  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **标头：** Mscoree.dll  
  
 **库：** 作为中的资源包含 MSCorEE.dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [EApiCategories 枚举](eapicategories-enumeration.md)
- [ICLRControl 接口](iclrcontrol-interface.md)
