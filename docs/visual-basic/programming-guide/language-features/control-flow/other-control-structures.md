---
description: '了解详细信息：其他控制结构 (Visual Basic) '
title: 其他控件结构
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
ms.openlocfilehash: 39654b8c780369eeea043087c8a04e2ba1f928c2
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100473571"
---
# <a name="other-control-structures-visual-basic"></a>其他控件结构 (Visual Basic)

Visual Basic 提供了控制结构，可帮助您释放资源或减少必须重复对象引用的次数。  
  
## <a name="usingend-using-construction"></a>使用 .。。使用构造结束  

 `Using...End Using`构造建立了一个语句块，其中使用了诸如 SQL 连接等资源。 您可以选择获取带有语句的资源 `Using` 。 退出 `Using` 块时，Visual Basic 会自动释放资源，以便其他代码可以使用该资源。 资源必须是本地的，并且是可释放的。 有关详细信息，请参阅 [Using 语句](../../../language-reference/statements/using-statement.md)。  
  
## <a name="withend-with-construction"></a>用 .。。以构造结尾  

 `With...End With`构造使你可以指定一个对象引用一次，并运行一系列访问其成员的语句。 这可以简化代码和提高性能，因为 Visual Basic 不必为访问它的每个语句重新建立引用。 有关详细信息，请参阅 [With .。。End With 语句](../../../language-reference/statements/with-end-with-statement.md)。  
  
## <a name="see-also"></a>请参阅

- [控制流](index.md)
- [决策结构](decision-structures.md)
- [循环结构](loop-structures.md)
- [嵌套的控件结构](nested-control-structures.md)
- [Using 语句](../../../language-reference/statements/using-statement.md)
- [With...End With 语句](../../../language-reference/statements/with-end-with-statement.md)
