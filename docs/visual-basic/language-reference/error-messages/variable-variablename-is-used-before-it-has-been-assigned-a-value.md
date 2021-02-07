---
description: 了解更多相关信息： BC42104：变量 " <variablename> " 在赋值前已被使用
title: 变量“<variablename>”在赋值前被使用
ms.date: 07/20/2015
f1_keywords:
- vbc42104
- BC42104
helpviewer_keywords:
- BC42104
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
ms.openlocfilehash: 501c3e3971c5ca0ebdba6981134f5029b77d0075
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701490"
---
# <a name="bc42104-variable-variablename-is-used-before-it-has-been-assigned-a-value"></a>BC42104：变量 " \<variablename> " 在赋值前被使用

变量 " \<variablename> " 在赋值前被使用。 可能在运行时导致 null 引用异常。

 应用程序在其代码上至少有一个可能的路径，该路径将在分配任何值之前读取该变量。

 如果从未为变量赋值，则它保持其数据类型的默认值。 对于引用数据类型，默认值是 [Nothing](../nothing.md)。 在某些情况下，读取具有 `Nothing` 值的引用变量可能导致 <xref:System.NullReferenceException> 。

 默认情况下，此消息是一个警告。 有关隐藏警告或将警告视为错误的详细信息，请参见 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。

 **错误 ID：** BC42104

## <a name="to-correct-this-error"></a>更正此错误

- 检查控制流逻辑，并确保在控制传递到读取它的任何语句之前，该变量具有一个有效的值。

- 保证变量始终具有有效值的一种方法是将其初始化为其声明的一部分。 请参阅 [Dim 语句](../statements/dim-statement.md)中的 "初始化"。

## <a name="see-also"></a>请参阅

- [Dim 语句](../statements/dim-statement.md)
- [变量声明](../../programming-guide/language-features/variables/variable-declaration.md)
- [变量疑难解答](../../programming-guide/language-features/variables/troubleshooting-variables.md)
