---
description: '了解详细信息：嵌套控制结构 (Visual Basic) '
title: 嵌套的控件结构
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, control flow
- control structures [Visual Basic], nested
- conditional statements [Visual Basic], nested
- statements [Visual Basic], control flow
- control flow [Visual Basic], nested control statements
- structures [Visual Basic], nested control
- nested control statements [Visual Basic]
ms.assetid: cf60b061-65d9-44a8-81f2-b0bdccd23a05
ms.openlocfilehash: 086e1201cab3ea133b01a003de58f8d3e67bfc44
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100473597"
---
# <a name="nested-control-structures-visual-basic"></a><span data-ttu-id="8dbaa-103">嵌套的控件结构 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8dbaa-103">Nested Control Structures (Visual Basic)</span></span>

<span data-ttu-id="8dbaa-104">可以将控制语句置于其他控制语句中，例如 `If...Then...Else` 循环内的块 `For...Next` 。</span><span class="sxs-lookup"><span data-stu-id="8dbaa-104">You can place control statements inside other control statements, for example an `If...Then...Else` block within a `For...Next` loop.</span></span> <span data-ttu-id="8dbaa-105">放置在另一控制语句内部的控制语句称为 " *嵌套*"。</span><span class="sxs-lookup"><span data-stu-id="8dbaa-105">A control statement placed inside another control statement is said to be *nested*.</span></span>  
  
## <a name="nesting-levels"></a><span data-ttu-id="8dbaa-106">嵌套级别</span><span class="sxs-lookup"><span data-stu-id="8dbaa-106">Nesting Levels</span></span>  

 <span data-ttu-id="8dbaa-107">Visual Basic 中的控制结构可以嵌套给所需的多个级别。</span><span class="sxs-lookup"><span data-stu-id="8dbaa-107">Control structures in Visual Basic can be nested to as many levels as you want.</span></span> <span data-ttu-id="8dbaa-108">常见的做法是通过缩进每个结构的主体，使嵌套结构更具可读性。</span><span class="sxs-lookup"><span data-stu-id="8dbaa-108">It is common practice to make nested structures more readable by indenting the body of each one.</span></span> <span data-ttu-id="8dbaa-109">集成开发环境 (IDE) 编辑器会自动执行此功能。</span><span class="sxs-lookup"><span data-stu-id="8dbaa-109">The integrated development environment (IDE) editor automatically does this.</span></span>  
  
 <span data-ttu-id="8dbaa-110">在下面的示例中，过程 `sumRows` 将矩阵中每行的正面元素相加。</span><span class="sxs-lookup"><span data-stu-id="8dbaa-110">In the following example, the procedure `sumRows` adds together the positive elements of each row of the matrix.</span></span>  
  
```vb
Public Sub sumRows(ByVal a(,) As Double, ByRef r() As Double)  
    Dim i, j As Integer  
    For i = 0 To UBound(a, 1)  
        r(i) = 0  
        For j = 0 To UBound(a, 2)  
            If a(i, j) > 0 Then  
                r(i) = r(i) + a(i, j)  
            End If  
        Next j  
    Next i  
End Sub  
```  
  
 <span data-ttu-id="8dbaa-111">在前面的示例中，第一个 `Next` 语句关闭内层 `For` 循环，最后一个 `Next` 语句关闭外部 `For` 循环。</span><span class="sxs-lookup"><span data-stu-id="8dbaa-111">In the preceding example, the first `Next` statement closes the inner `For` loop and the last `Next` statement closes the outer `For` loop.</span></span>  
  
 <span data-ttu-id="8dbaa-112">同样，在嵌套 `If` 语句中， `End If` 语句会自动应用到最近的前一 `If` 语句。</span><span class="sxs-lookup"><span data-stu-id="8dbaa-112">Likewise, in nested `If` statements, the `End If` statements automatically apply to the nearest prior `If` statement.</span></span> <span data-ttu-id="8dbaa-113">嵌套 `Do` 循环的工作方式类似，最内层的 `Loop` 语句与最内层的 `Do` 语句匹配。</span><span class="sxs-lookup"><span data-stu-id="8dbaa-113">Nested `Do` loops work in a similar fashion, with the innermost `Loop` statement matching the innermost `Do` statement.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8dbaa-114">对于许多控制结构，当您单击某个关键字时，将突出显示该结构中的所有关键字。</span><span class="sxs-lookup"><span data-stu-id="8dbaa-114">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="8dbaa-115">例如，单击构造时，将 `If` `If...Then...Else` `If` `Then` `ElseIf` `Else` `End If` 突出显示构造中的、、、和的所有实例。</span><span class="sxs-lookup"><span data-stu-id="8dbaa-115">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="8dbaa-116">若要移动到下一个或上一个突出显示的关键字，请按 CTRL + SHIFT + 向下键或 CTRL + SHIFT + 向上键。</span><span class="sxs-lookup"><span data-stu-id="8dbaa-116">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="nesting-different-kinds-of-control-structures"></a><span data-ttu-id="8dbaa-117">嵌套不同种类的控制结构</span><span class="sxs-lookup"><span data-stu-id="8dbaa-117">Nesting Different Kinds of Control Structures</span></span>  

 <span data-ttu-id="8dbaa-118">您可以在另一种类型中嵌套一种控件结构。</span><span class="sxs-lookup"><span data-stu-id="8dbaa-118">You can nest one kind of control structure within another kind.</span></span> <span data-ttu-id="8dbaa-119">下面的示例在 `With` 循环内使用块 `For Each` ，并在 `If` 块内使用嵌套块 `With` 。</span><span class="sxs-lookup"><span data-stu-id="8dbaa-119">The following example uses a `With` block inside a `For Each` loop and nested `If` blocks inside the `With` block.</span></span>  
  
```vb
For Each ctl As System.Windows.Forms.Control In Me.Controls  
    With ctl  
        .BackColor = System.Drawing.Color.Yellow  
        .ForeColor = System.Drawing.Color.Black  
        If .CanFocus Then  
            .Text = "Colors changed"  
            If Not .Focus() Then  
                ' Insert code to process failed focus.  
            End If  
        End If  
    End With  
Next ctl  
```  
  
## <a name="overlapping-control-structures"></a><span data-ttu-id="8dbaa-120">重叠控制结构</span><span class="sxs-lookup"><span data-stu-id="8dbaa-120">Overlapping Control Structures</span></span>  

 <span data-ttu-id="8dbaa-121">不能重叠控制结构。</span><span class="sxs-lookup"><span data-stu-id="8dbaa-121">You cannot overlap control structures.</span></span> <span data-ttu-id="8dbaa-122">这意味着，任何嵌套结构都必须完全包含在下一个最内层的结构中。</span><span class="sxs-lookup"><span data-stu-id="8dbaa-122">This means that any nested structure must be completely contained within the next innermost structure.</span></span> <span data-ttu-id="8dbaa-123">例如，下面的排列无效，因为循环在 `For` 内部块终止之前终止 `With` 。</span><span class="sxs-lookup"><span data-stu-id="8dbaa-123">For example, the following arrangement is invalid because the `For` loop terminates before the inner `With` block terminates.</span></span>  
  
 ![显示无效嵌套示例的关系图。](./media/nested-control-structures/example-invalid-nesting.gif)
  
 <span data-ttu-id="8dbaa-125">Visual Basic 编译器检测到这样的重叠控制结构并发出编译时错误。</span><span class="sxs-lookup"><span data-stu-id="8dbaa-125">The Visual Basic compiler detects such overlapping control structures and signals a compile-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dbaa-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="8dbaa-126">See also</span></span>

- [<span data-ttu-id="8dbaa-127">控制流</span><span class="sxs-lookup"><span data-stu-id="8dbaa-127">Control Flow</span></span>](index.md)
- [<span data-ttu-id="8dbaa-128">决策结构</span><span class="sxs-lookup"><span data-stu-id="8dbaa-128">Decision Structures</span></span>](decision-structures.md)
- [<span data-ttu-id="8dbaa-129">循环结构</span><span class="sxs-lookup"><span data-stu-id="8dbaa-129">Loop Structures</span></span>](loop-structures.md)
- [<span data-ttu-id="8dbaa-130">其他控件结构</span><span class="sxs-lookup"><span data-stu-id="8dbaa-130">Other Control Structures</span></span>](other-control-structures.md)
