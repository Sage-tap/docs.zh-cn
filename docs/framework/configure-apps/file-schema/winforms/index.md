---
description: 了解详细信息： Windows 窗体配置部分
title: Windows 窗体配置节
ms.date: 04/07/2017
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
ms.openlocfilehash: f1eaf2d74c7645d6cf4580d75e23d8910628cce0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697759"
---
# <a name="windows-forms-configuration-section"></a>Windows 窗体配置节

Windows 窗体配置设置允许 Windows 窗体应用存储和检索有关自定义应用程序设置的信息，如多显示器支持、高 DPI 支持和其他预定义配置设置。

Windows 窗体应用程序配置设置存储在应用程序配置文件的 `System.Windows.Forms.ApplicationConfigurationSection` 元素中。

## <a name="syntax"></a>语法

```xml
<configuration>
  <System.Windows.Forms.ApplicationConfigurationSection>
  ...
  </System.Windows.Forms.ApplicationConfigurationSection>
</configuration>
```

## <a name="attributes-and-elements"></a>特性和元素

下列各节描述了特性、子元素和父元素。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

元素  |说明 |
---------|---------|
[`<add>`](windows-forms-add-configuration-element.md) | 添加具有指定值的配置设置键 |

### <a name="parent-elements"></a>父元素

元素  |说明 |
---------|---------|
[\<configuration>](../configuration-element.md) | 公共语言运行时和 .Windows 窗体应用程序所使用的每个配置文件中的根元素 |

## <a name="remarks"></a>备注

从 .NET Framework 4.7 开始，`<System.Windows.Forms.ApplicationConfigurationSection>` 元素允许配置 Windows 窗体应用程序，以利用最新版本的 .NET Framework 中添加的功能。

`<System.Windows.Forms.ApplicationConfigurationSection>`元素可以包含一个或多个子 [`<add>`](windows-forms-add-configuration-element.md) 元素，其中每个元素都定义了一个特定的配置设置。

## <a name="see-also"></a>请参阅

- [配置文件架构](../index.md)
- [Windows 窗体中的高 DPI 支持](/dotnet/desktop/winforms/high-dpi-support-in-windows-forms)
