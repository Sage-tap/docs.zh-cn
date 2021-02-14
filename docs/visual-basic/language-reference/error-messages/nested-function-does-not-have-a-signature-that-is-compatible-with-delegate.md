---
description: 了解详细信息： BC36532：嵌套函数没有与委托 "" 兼容的签名 <delegatename>
title: 嵌套函数没有与委托“<delegatename>”兼容的签名。
ms.date: 07/20/2015
f1_keywords:
- vbc36532
- bc36532
helpviewer_keywords:
- BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
ms.openlocfilehash: ff6abda015187d0d7d0690f2f1fd00772e63c61b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100483542"
---
# <a name="bc36532-nested-function-does-not-have-a-signature-that-is-compatible-with-delegate-delegatename"></a><span data-ttu-id="0cf07-103">BC36532：嵌套函数没有与委托 "" 兼容的签名 \<delegatename></span><span class="sxs-lookup"><span data-stu-id="0cf07-103">BC36532: Nested function does not have a signature that is compatible with delegate '\<delegatename>'</span></span>

<span data-ttu-id="0cf07-104">已将 lambda 表达式分配给具有不兼容签名的委托。</span><span class="sxs-lookup"><span data-stu-id="0cf07-104">A lambda expression has been assigned to a delegate that has an incompatible signature.</span></span> <span data-ttu-id="0cf07-105">例如，在下面的代码中，委托 `Del` 具有两个整数参数。</span><span class="sxs-lookup"><span data-stu-id="0cf07-105">For example, in the following code, delegate `Del` has two integer parameters.</span></span>

```vb
Delegate Function Del(ByVal p As Integer, ByVal q As Integer) As Integer
```

<span data-ttu-id="0cf07-106">如果将带一个自变量的 lambda 表达式声明为类型，则会引发此错误 `Del` ：</span><span class="sxs-lookup"><span data-stu-id="0cf07-106">The error is raised if a lambda expression with one argument is declared as type `Del`:</span></span>

```vb
' Neither of these is valid.
' Dim lambda1 As Del = Function(n As Integer) n + 1
' Dim lambda2 As Del = Function(n) n + 1
```

<span data-ttu-id="0cf07-107">**错误 ID：** BC36532</span><span class="sxs-lookup"><span data-stu-id="0cf07-107">**Error ID:** BC36532</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="0cf07-108">更正此错误</span><span class="sxs-lookup"><span data-stu-id="0cf07-108">To correct this error</span></span>

<span data-ttu-id="0cf07-109">调整委托定义或指定的 lambda 表达式，使签名兼容。</span><span class="sxs-lookup"><span data-stu-id="0cf07-109">Adjust either the delegate definition or the assigned lambda expression so that the signatures are compatible.</span></span>

## <a name="see-also"></a><span data-ttu-id="0cf07-110">请参阅</span><span class="sxs-lookup"><span data-stu-id="0cf07-110">See also</span></span>

- [<span data-ttu-id="0cf07-111">宽松委托转换</span><span class="sxs-lookup"><span data-stu-id="0cf07-111">Relaxed Delegate Conversion</span></span>](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [<span data-ttu-id="0cf07-112">Lambda 表达式</span><span class="sxs-lookup"><span data-stu-id="0cf07-112">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
