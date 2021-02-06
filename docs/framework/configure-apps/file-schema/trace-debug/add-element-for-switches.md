---
description: 详细了解： <add> 的元素 <switches>
title: <switches> 的 <add> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
ms.openlocfilehash: fc47a8518aca1e4e6390d9d7eba97d5fb7a7664e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639713"
---
# <a name="add-element-for-switches"></a>\<switches> 的 \<add> 元素

指定对跟踪开关设置的级别。  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<switches>**](switches-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a>语法  
  
```xml  
<add name="switch name"  
     value="value"/>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  

 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|属性|说明|  
|---------------|-----------------|  
|**name**|必需的特性。<br /><br /> 指定开关的名称。 此属性的值对应于传递给 switch 构造函数的 *displayName* 参数。|  
|**value**|必需的特性。<br /><br /> 指定开关的级别。|  
  
### <a name="child-elements"></a>子元素  

 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|说明|  
|-------------|-----------------|  
|`configuration`|公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。|  
|`switches`|包含跟踪开关和对该跟踪开关设置的级别。|  
|`system.diagnostics`|指定用于收集、存储和路由消息的跟踪侦听器以及对跟踪开关设置的级别。|  
  
## <a name="remarks"></a>备注  

 可以通过将跟踪开关置于配置文件中来更改其级别。 如果开关是 <xref:System.Diagnostics.BooleanSwitch> ，则可以将其打开或关闭。 如果开关是 <xref:System.Diagnostics.TraceSwitch> ，则可以为其分配不同的级别，以指定应用程序输出的跟踪或调试消息的类型。  
  
## <a name="example"></a>示例  

 下面的示例演示如何使用 **\<add>** 元素将 `General` 跟踪开关设置为 <xref:System.Diagnostics.TraceLevel> 级别，并启用 `Data` 布尔型跟踪开关。  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="General" value="4" />  
         <add name="Data" value="1" />  
      </switches>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>请参阅

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [跟踪和调试设置架构](index.md)
