---
description: 了解详细信息：在 Visual Basic 中从零开始与从1开始的字符串访问
title: 以零起始的字符串访问与以一起始的字符串访问
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
ms.openlocfilehash: adab6954c4329ae0a547d136f26f6c3115dc5890
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100463827"
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a>从 0 开始与从 1 开始的字符串访问 (Visual Basic)

本主题比较 Visual Basic 和 .NET Framework 如何提供对字符串中的字符的访问。 .NET Framework 始终提供对字符串中的字符的从零开始的访问，而 Visual Basic 提供从零开始的和基于的访问（具体取决于函数）。  
  
## <a name="one-based"></a>One-Based  

 有关基于一个 Visual Basic 函数的示例，请考虑 `Mid` 函数。 它采用一个参数，该参数指示子字符串的起始字符位置（从位置1开始）。 .NET Framework <xref:System.String.Substring%2A?displayProperty=nameWithType> 方法采用字符串中的字符的索引，子字符串将从位置0开始。 因此，如果您有字符串 "ABCDE...Z"，则每个字符的编号为1、2、3、4、5和函数一起使用 `Mid` ，但0、1、2、3、4用于 <xref:System.String.Substring%2A?displayProperty=nameWithType> 方法。  
  
## <a name="zero-based"></a>Zero-Based  

 有关从零开始的 Visual Basic 函数的示例，请考虑 `Split` 函数。 它拆分字符串并返回包含子字符串的数组。 .NET Framework <xref:System.String.Split%2A?displayProperty=nameWithType> 方法还拆分字符串并返回包含子字符串的数组。 由于 `Split` 函数和 <xref:System.String.Split%2A> 方法返回 .NET Framework 数组，因此它们必须是从零开始的。  
  
## <a name="see-also"></a>请参阅

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:System.String.Substring%2A>
- <xref:System.String.Split%2A>
- [字符串介绍 (Visual Basic)](introduction-to-strings.md)
