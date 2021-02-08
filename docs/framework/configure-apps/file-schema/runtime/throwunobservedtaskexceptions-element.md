---
description: 了解详细信息： <ThrowUnobservedTaskExceptions> 元素
title: <ThrowUnobservedTaskExceptions> 元素
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ThrowUnobservedTaskExceptions element
- <ThrowUnobservedTaskExceptions> element
ms.assetid: cea7e588-8b8d-48d2-9ad5-8feaf3642c18
ms.openlocfilehash: 53f3f1275ea8419bed52fd73726c043e1c49eed7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802393"
---
# <a name="throwunobservedtaskexceptions-element"></a>\<ThrowUnobservedTaskExceptions> 元素

指定未经处理的任务异常是否应终止正在运行的进程。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<ThrowUnobservedTaskExceptions>**  
  
## <a name="syntax"></a>语法  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  

 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|属性|描述|  
|---------------|-----------------|  
|`enabled`|必需的特性。<br /><br /> 指定未经处理的任务异常是否应终止正在运行的进程。|  
  
## <a name="enabled-attribute"></a>enabled 特性  
  
|值|说明|  
|-----------|-----------------|  
|`false`|对于未处理的任务异常，不会终止正在运行的进程。 这是默认设置。|  
|`true`|终止正在运行的进程的未处理任务异常。|  
  
### <a name="child-elements"></a>子元素  

 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|说明|  
|-------------|-----------------|  
|`configuration`|公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。|  
|`runtime`|包含有关运行时初始化选项的信息。|  
|||  
  
## <a name="remarks"></a>备注  

 如果未观察到与关联的异常 <xref:System.Threading.Tasks.Task> ，则不会进行任何 <xref:System.Threading.Tasks.Task.Wait%2A> 操作，也不会附加父级，并且该 <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> 属性不会被视为未观察到。  
  
 在 .NET Framework 4 中，默认情况下，如果 <xref:System.Threading.Tasks.Task> 存在未观察到异常的，则终结器将引发异常并终止进程。 进程终止由垃圾回收和终止的时间决定。  
  
 为了使开发人员可以更轻松地根据任务编写异步代码，.NET Framework 4.5 更改未观察到异常的此默认行为。 未观察到异常仍会 <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> 引发事件，但在默认情况下，进程不会终止。 相反，引发事件后将忽略此异常，而不管事件处理程序是否观察到该异常。  
  
 在 .NET Framework 4.5 中，可以使用应用程序配置文件中的[ \<ThrowUnobservedTaskExceptions> 元素](throwunobservedtaskexceptions-element.md)来启用引发异常的 .NET Framework 4 行为。  
  
 还可以通过以下方式之一指定异常行为：  
  
- 通过设置环境变量 `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`) 。  
  
- 通过在 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft中设置注册表 DWORD 值 ThrowUnobservedTaskExceptions = 1 \\ 。.Netframework 键。  
  
## <a name="example"></a>示例  

 下面的示例演示如何使用应用程序配置文件在任务中启用异常引发。  
  
```xml  
<configuration>
    <runtime>
        <ThrowUnobservedTaskExceptions enabled="true"/>
    </runtime>
</configuration>  
```  
  
## <a name="example"></a>示例  

 下面的示例演示如何从任务中引发未观察到异常。 必须以发布程序的形式运行代码，才能正常工作。  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a>请参阅

- [运行时设置架构](index.md)
- [配置文件架构](../index.md)
