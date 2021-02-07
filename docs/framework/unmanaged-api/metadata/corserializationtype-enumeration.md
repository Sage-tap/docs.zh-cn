---
description: 了解详细信息： CorSerializationType 枚举
title: CorSerializationType 枚举
ms.date: 03/30/2017
api_name:
- CorSerializationType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSerializationType
helpviewer_keywords:
- CorSerializationType enumeration [.NET Framework metadata]
ms.assetid: 6b1fcd11-c7fb-4be2-8910-abc862d4caf4
topic_type:
- apiref
ms.openlocfilehash: 86df23bf03037d329a3138798725058f1d24a450
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707379"
---
# <a name="corserializationtype-enumeration"></a>CorSerializationType 枚举

指定公共语言运行时序列化对象的方式。  
  
## <a name="syntax"></a>语法  
  
```cpp  
typedef enum CorSerializationType {  
  
    SERIALIZATION_TYPE_UNDEFINED     = 0,  
    SERIALIZATION_TYPE_BOOLEAN       = ELEMENT_TYPE_BOOLEAN,  
    SERIALIZATION_TYPE_CHAR          = ELEMENT_TYPE_CHAR,  
    SERIALIZATION_TYPE_I1            = ELEMENT_TYPE_I1,  
    SERIALIZATION_TYPE_U1            = ELEMENT_TYPE_U1,  
    SERIALIZATION_TYPE_I2            = ELEMENT_TYPE_I2,  
    SERIALIZATION_TYPE_U2            = ELEMENT_TYPE_U2,  
    SERIALIZATION_TYPE_I4            = ELEMENT_TYPE_I4,  
    SERIALIZATION_TYPE_U4            = ELEMENT_TYPE_U4,  
    SERIALIZATION_TYPE_I8            = ELEMENT_TYPE_I8,  
    SERIALIZATION_TYPE_U8            = ELEMENT_TYPE_U8,  
    SERIALIZATION_TYPE_R4            = ELEMENT_TYPE_R4,  
    SERIALIZATION_TYPE_R8            = ELEMENT_TYPE_R8,  
    SERIALIZATION_TYPE_STRING        = ELEMENT_TYPE_STRING,  
    SERIALIZATION_TYPE_SZARRAY       = ELEMENT_TYPE_SZARRAY,  
    SERIALIZATION_TYPE_TYPE          = 0x50,  
    SERIALIZATION_TYPE_TAGGED_OBJECT = 0x51,  
    SERIALIZATION_TYPE_FIELD         = 0x53,  
    SERIALIZATION_TYPE_PROPERTY      = 0x54,  
    SERIALIZATION_TYPE_ENUM          = 0x55  
  
} CorSerializationType;  
```  
  
## <a name="members"></a>成员  
  
|成员|说明|  
|------------|-----------------|  
|`SERIALIZATION_TYPE_UNDEFINED`|对象的序列化未定义。|  
|`SERIALIZATION_TYPE_BOOLEAN`|将对象序列化为布尔类型|  
|`SERIALIZATION_TYPE_CHAR`|将对象序列化为字符类型。|  
|`SERIALIZATION_TYPE_I1`|将对象序列化为有符号的1字节整数。|  
|`SERIALIZATION_TYPE_U1`|将对象序列化为无符号的1字节整数。|  
|`SERIALIZATION_TYPE_I2`|将对象序列化为有符号的2字节整数。|  
|`SERIALIZATION_TYPE_U2`|将对象序列化为无符号的2字节整数。|  
|`SERIALIZATION_TYPE_I4`|将对象序列化为有符号4字节整数。|  
|`SERIALIZATION_TYPE_U4`|将对象序列化为无符号4字节整数。|  
|`SERIALIZATION_TYPE_I8`|将对象序列化为有符号的8字节整数。|  
|`SERIALIZATION_TYPE_U8`|将对象序列化为无符号的8字节整数。|  
|`SERIALIZATION_TYPE_R4`|将对象序列化为4字节浮点数。|  
|`SERIALIZATION_TYPE_R8`|将对象序列化为8字节浮点。|  
|`SERIALIZATION_TYPE_STRING`|将对象序列化为 System.string 类型。|  
|`SERIALIZATION_TYPE_SZARRAY`|将对象序列化为一个一维的、零下限的数组。|  
|`SERIALIZATION_TYPE_TYPE`|将对象序列化为泛型类型。|  
|`SERIALIZATION_TYPE_TAGGED_OBJECT`|将对象序列化为标记的对象。|  
|`SERIALIZATION_TYPE_FIELD`|将对象序列化为一个字段。|  
|`SERIALIZATION_TYPE_PROPERTY`|将对象序列化为属性。|  
|`SERIALIZATION_TYPE_ENUM`|将对象序列化为枚举。|  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **标头：** Corhdr。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [元数据枚举](metadata-enumerations.md)
