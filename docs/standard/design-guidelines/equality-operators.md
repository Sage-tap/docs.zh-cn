---
description: 详细了解：相等运算符
title: 相等运算符
ms.date: 10/22/2008
helpviewer_keywords:
- class library design guidelines [.NET Framework], Equals method
- class library design guidelines [.NET Framework], equality operator
- equality operator (==) [.NET Framework]
- Equals method
- == operator (equality) [.NET Framework]
ms.assetid: bc496a91-fefb-4ce0-ab4c-61f09964119a
ms.openlocfilehash: 8678ed1b4bc320f685cf7ae172f064b3dededd04
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642235"
---
# <a name="equality-operators"></a>相等运算符

本部分讨论重载相等运算符，并将 `operator==` 和 `operator!=` 视为相等运算符。

 ❌ 请勿重载其中一个相等运算符而不重载另一个。

 ✔️ 请务必确保 <xref:System.Object.Equals%2A?displayProperty=nameWithType> 和相等运算符具有完全相同的语义和相似的性能特征。

 这通常意味着在重载相等运算符时，需要重写 `Object.Equals`。

 ❌ 请避免从相等运算符引发异常。

 例如，如果其中一个参数为 null，则返回 false，而不是引发 `NullReferenceException`。

## <a name="equality-operators-on-value-types"></a>针对值类型的相等运算符

 ✔️ 如果相等性是有意义的，请务必对值类型重载相等运算符。

 在大多数编程语言中，值类型没有默认的 `operator==` 实现。

## <a name="equality-operators-on-reference-types"></a>针对引用类型的相等运算符

 ❌ 请避免对可变引用类型重载相等运算符。

 许多语言都具有用于引用类型的内置相等运算符。 内置运算符通常实现引用相等性，当默认行为更改为值相等性时，很多开发人员都感到很惊讶。

 对于不可变的引用类型，此问题得到了缓解，因为不可变性使发现引用相等性和值相等性之间的差异变得更加困难。

 ❌ 请避免对引用类型重载相等运算符（如果实现的速度远远低于引用相等性的实现速度）。

 *Portions © 2005, 2009 Microsoft Corporation 版权所有。保留所有权利。*

 在 Pearson Education, Inc. 授权下，由 Addison-Wesley Professional 作为 Microsoft Windows 开发系列的一部分再版自 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)（Framework 设计准则：可重用 .NET 库的约定、惯例和模式第 2 版），由 Krzysztof Cwalina 和 Brad Abrams 发布于 2008 年 10 月 22 日。

## <a name="see-also"></a>请参阅

- [框架设计指南](index.md)
- [使用准则](usage-guidelines.md)
