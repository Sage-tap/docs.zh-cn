---
description: '了解详细信息：收缩 (Visual Basic) '
title: Narrowing
ms.date: 07/20/2015
f1_keywords:
- vb.narrowing
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Narrowing keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: a207ee91-aca4-4771-b4e2-713f029bf2bb
ms.openlocfilehash: 1dd9185ccf30fb6f9dc9360f75450c2533ab90e5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795346"
---
# <a name="narrowing-visual-basic"></a>Narrowing (Visual Basic)

指示转换运算符 (`CType`) 将类或结构转换为可能无法保存原始类或结构的某些可能值的类型。  
  
## <a name="converting-with-the-narrowing-keyword"></a>用收缩关键字转换  

 除了之外，转换过程必须指定 `Public Shared` `Narrowing` 。  
  
 收缩转换在运行时并不总是成功，可能会失败或导致数据丢失。 示例包括 `Long` 对 `Integer` `String` 派生类型的、到 `Date` 和基类型。 此上一转换是收缩的，因为基类型可能不包含派生类型的所有成员，因此不是派生类型的实例。  
  
 如果 `Option Strict` 为 `On` ，则使用的代码必须用于 `CType` 所有收缩转换。  
  
 `Narrowing`关键字可以在此上下文中使用：  
  
 [Operator Statement](../statements/operator-statement.md)  
  
## <a name="see-also"></a>请参阅

- [Operator Statement](../statements/operator-statement.md)
- [Widening](widening.md)
- [Widening and Narrowing Conversions](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [如何：定义运算符](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [CType Function](../functions/ctype-function.md)
- [Option Strict 语句](../statements/option-strict-statement.md)
