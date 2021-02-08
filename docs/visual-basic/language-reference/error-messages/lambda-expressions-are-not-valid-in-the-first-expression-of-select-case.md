---
description: 了解详细信息： BC36635： Lambda 表达式在 "Select Case" 语句的第一个表达式中无效
title: Lambda 表达式在“Select Case”语句的第一个表达式中无效
ms.date: 07/20/2015
f1_keywords:
- bc36635
- vbc36635
helpviewer_keywords:
- BC36635
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
ms.openlocfilehash: e0c388db7164f6c9f99ba917109593a796f7b23b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795932"
---
# <a name="bc36635-lambda-expressions-are-not-valid-in-the-first-expression-of-a-select-case-statement"></a><span data-ttu-id="47070-103">BC36635： Lambda 表达式在 "Select Case" 语句的第一个表达式中无效</span><span class="sxs-lookup"><span data-stu-id="47070-103">BC36635: Lambda expressions are not valid in the first expression of a 'Select Case' statement</span></span>

<span data-ttu-id="47070-104">不能对语句中的测试表达式使用 lambda 表达式 `Select Case` 。</span><span class="sxs-lookup"><span data-stu-id="47070-104">You cannot use a lambda expression for the test expression in a `Select Case` statement.</span></span> <span data-ttu-id="47070-105">Lambda 表达式定义返回函数，语句的测试表达式 `Select Case` 必须是基本数据类型。</span><span class="sxs-lookup"><span data-stu-id="47070-105">Lambda expression definitions return functions, and the test expression of a `Select Case` statement must be an elementary data type.</span></span>

 <span data-ttu-id="47070-106">下面的代码会导致此错误：</span><span class="sxs-lookup"><span data-stu-id="47070-106">The following code causes this error:</span></span>

```vb
' Select Case (Function(arg) arg Is Nothing)
    ' List of the cases.
' End Select
```

 <span data-ttu-id="47070-107">**错误 ID：** BC36635</span><span class="sxs-lookup"><span data-stu-id="47070-107">**Error ID:** BC36635</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="47070-108">更正此错误</span><span class="sxs-lookup"><span data-stu-id="47070-108">To correct this error</span></span>

- <span data-ttu-id="47070-109">检查你的代码以确定是否可以使用其他条件构造，例如 `If...Then...Else` 语句。</span><span class="sxs-lookup"><span data-stu-id="47070-109">Examine your code to determine whether a different conditional construction, such as an `If...Then...Else` statement, would work for you.</span></span>

- <span data-ttu-id="47070-110">你可能打算调用函数，如以下代码所示：</span><span class="sxs-lookup"><span data-stu-id="47070-110">You may have intended to call the function, as shown in the following code:</span></span>

```vb
Dim num? As Integer
Select Case ((Function(arg? As Integer) arg Is Nothing)(num))
    ' List of the cases
End Select
```

## <a name="see-also"></a><span data-ttu-id="47070-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="47070-111">See also</span></span>

- [<span data-ttu-id="47070-112">Lambda 表达式</span><span class="sxs-lookup"><span data-stu-id="47070-112">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="47070-113">If...Then...Else 语句</span><span class="sxs-lookup"><span data-stu-id="47070-113">If...Then...Else Statement</span></span>](../statements/if-then-else-statement.md)
- [<span data-ttu-id="47070-114">Select...Case 语句</span><span class="sxs-lookup"><span data-stu-id="47070-114">Select...Case Statement</span></span>](../statements/select-case-statement.md)
