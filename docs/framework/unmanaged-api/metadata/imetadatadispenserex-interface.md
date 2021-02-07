---
description: 了解详细信息： IMetaDataDispenserEx 接口
title: IMetaDataDispenserEx 接口
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx
helpviewer_keywords:
- IMetaDataDispenserEx interface [.NET Framework metadata]
ms.assetid: 78b3629e-77a2-4406-89c3-56b5cc2c4594
topic_type:
- apiref
ms.openlocfilehash: d940ac20eaad4b930ab17fb2d194d3b03bd4cf3c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753531"
---
# <a name="imetadatadispenserex-interface"></a>IMetaDataDispenserEx 接口

扩展 [IMetaDataDispenser 接口](imetadatadispenser-interface.md) 接口，以提供控制元数据 api 对当前元数据范围的操作方式的功能。  
  
## <a name="methods"></a>方法  
  
|方法|说明|  
|------------|-----------------|  
|[FindAssembly 方法](imetadatadispenserex-findassembly-method.md)|未实现此方法。 如果调用，它将返回 E_NOTIMPL。|  
|[FindAssemblyModule 方法](imetadatadispenserex-findassemblymodule-method.md)|未实现此方法。 如果调用，它将返回 E_NOTIMPL。|  
|[GetCORSystemDirectory 方法](imetadatadispenserex-getcorsystemdirectory-method.md)|获取 (CLR) 保存当前公共语言运行时的目录。 此方法仅支持在进程外调试器中使用。 如果从另一个组件调用，它将返回 E_NOTIMPL。|  
|[GetOption 方法](imetadatadispenserex-getoption-method.md)|为当前元数据范围获取指定选项的值。 选项控制如何处理对当前元数据范围的调用。|  
|[OpenScopeOnITypeInfo 方法](imetadatadispenserex-openscopeonitypeinfo-method.md)|未实现此方法。 如果调用，它将返回 E_NOTIMPL。|  
|[SetOption 方法](imetadatadispenserex-setoption-method.md)|为当前元数据范围将指定的选项设置为给定的值。 选项控制如何处理对当前元数据范围的调用。|  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **标头：** Cor  
  
 **库：** 用作 MsCorEE.dll 中的资源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [元数据接口](metadata-interfaces.md)
- [IMetaDataDispenser 接口](imetadatadispenser-interface.md)
- [IMetaDataEmit 接口](imetadataemit-interface.md)
- [IMetaDataImport 接口](imetadataimport-interface.md)
