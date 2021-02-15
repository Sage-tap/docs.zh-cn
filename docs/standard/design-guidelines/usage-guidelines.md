---
description: 详细了解：使用准则
title: 使用准则
ms.date: 10/22/2008
helpviewer_keywords:
- class library design guidelines [.NET Framework], usage guidelines
ms.assetid: 42215ffa-a099-4a26-b14e-fb2bdb6f95b7
ms.openlocfilehash: a435fab2adb00f671dfde1619a3c1f8db719d9df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641793"
---
# <a name="usage-guidelines"></a>使用准则

本部分包含有关在可公开访问的 API 中使用常见类型的准则。 其中涉及内置框架类型（如序列化特性）的直接使用和常见运算符的重载。
  
<xref:System.IDisposable?displayProperty=nameWithType> 接口在本部分未进行介绍，但在[释放模式](../garbage-collection/implementing-dispose.md)部分中进行了讨论。

> [!NOTE]
> 有关其他常见内置 .NET Framework 类型的指南和附加信息，请参阅以下各项的引用主题：<xref:System.DateTime?displayProperty=nameWithType>、<xref:System.DateTimeOffset?displayProperty=nameWithType>、<xref:System.ICloneable?displayProperty=nameWithType>、<xref:System.IComparable%601?displayProperty=nameWithType>、<xref:System.IEquatable%601?displayProperty=nameWithType>、<xref:System.Nullable%601?displayProperty=nameWithType>、<xref:System.Object?displayProperty=nameWithType>、<xref:System.Uri?displayProperty=nameWithType>。

## <a name="in-this-section"></a>本节内容

[数组](arrays.md)  
[特性](attributes.md)  
[集合](guidelines-for-collections.md)  
[序列化](serialization.md)  
[System.Xml 使用情况](system-xml-usage.md)  
[相等运算符](equality-operators.md)  

*Portions © 2005, 2009 Microsoft Corporation 版权所有。保留所有权利。*

在 Pearson Education, Inc. 授权下，由 Addison-Wesley Professional 作为 Microsoft Windows 开发系列的一部分再版自 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)（Framework 设计准则：可重用 .NET 库的约定、惯例和模式第 2 版），由 Krzysztof Cwalina 和 Brad Abrams 发布于 2008 年 10 月 22 日。
  
## <a name="see-also"></a>请参阅

- [框架设计指南](index.md)
