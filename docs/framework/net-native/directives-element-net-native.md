---
description: '了解详细信息： <Directives> 元素 ( .NET Native) '
title: <Directives>元素 (.NET Native)
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
ms.openlocfilehash: 7aa3bf3718f32d55ba8189c65705868c6fb399ae
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662905"
---
# <a name="directives-element-net-native"></a>\<Directives>元素 (.NET Native)

.NET Native 的每个运行时指令文件中的根元素。  
  
 `<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">`
  
## <a name="syntax"></a>语法  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->
</Directives>  
```  
  
## <a name="attributes"></a>特性  
  
|属性|说明|  
|---------------|-----------------|  
|`xmlns`|XML 命名空间。 其值始终为 `http://schemas.microsoft.com/netfx/2013/01/metadata` 。|  
  
## <a name="child-elements"></a>子元素  
  
|元素|说明|  
|-------------|-----------------|  
|[\<Application>](application-element-net-native.md)|作为应用程序范围内的类型和其元数据可以用于反射的类型成员的容器而服务。|  
|[\<Library>](library-element-net-native.md)|定义那些子类型和类型成员在运行时间要求元数据的程序集。|  
  
## <a name="remarks"></a>备注  

 每个运行时指令文件都可以只包含一个 `<Directives>` 元素。  
  
 `<Directives>`元素可以包含零个或一个 [\<Application>](application-element-net-native.md) 元素，以及零个、一个或多个元素 [\<Library>](library-element-net-native.md) 。  
  
## <a name="see-also"></a>请参阅

- [运行时指令 (rd.xml) 配置文件引用](runtime-directives-rd-xml-configuration-file-reference.md)
- [运行时指令元素](runtime-directive-elements.md)
