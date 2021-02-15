---
description: '了解详细信息：如何：修改表达式树 (Visual Basic) '
title: 如何：修改表达式树
ms.date: 07/20/2015
ms.assetid: d1309fff-28bd-4d8e-a2cf-75725999e8f2
ms.openlocfilehash: 13098f5588fe44be8e57c9be52a9cfe5f7cd661f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100455894"
---
# <a name="how-to-modify-expression-trees-visual-basic"></a><span data-ttu-id="ce6ea-103">如何：修改表达式树 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce6ea-103">How to: Modify Expression Trees (Visual Basic)</span></span>

<span data-ttu-id="ce6ea-104">本主题演示如何修改表达式树。</span><span class="sxs-lookup"><span data-stu-id="ce6ea-104">This topic shows you how to modify an expression tree.</span></span> <span data-ttu-id="ce6ea-105">表达式树是不可变的，这意味着不能直接对它们进行修改。</span><span class="sxs-lookup"><span data-stu-id="ce6ea-105">Expression trees are immutable, which means that they cannot be modified directly.</span></span> <span data-ttu-id="ce6ea-106">若要更改表达式树，必须创建现有表达式树的副本，创建此副本后，进行必要的更改。</span><span class="sxs-lookup"><span data-stu-id="ce6ea-106">To change an expression tree, you must create a copy of an existing expression tree and when you create the copy, make the required changes.</span></span> <span data-ttu-id="ce6ea-107">可以使用 <xref:System.Linq.Expressions.ExpressionVisitor> 类遍历现有表达式树，以及复制它访问的每个节点。</span><span class="sxs-lookup"><span data-stu-id="ce6ea-107">You can use the <xref:System.Linq.Expressions.ExpressionVisitor> class to traverse an existing expression tree and to copy each node that it visits.</span></span>

## <a name="to-modify-an-expression-tree"></a><span data-ttu-id="ce6ea-108">修改表达式树</span><span class="sxs-lookup"><span data-stu-id="ce6ea-108">To modify an expression tree</span></span>

1. <span data-ttu-id="ce6ea-109">创建新的 **控制台应用程序** 项目。</span><span class="sxs-lookup"><span data-stu-id="ce6ea-109">Create a new **Console Application** project.</span></span>

2. <span data-ttu-id="ce6ea-110">向 `Imports` 命名空间的文件添加语句 `System.Linq.Expressions` 。</span><span class="sxs-lookup"><span data-stu-id="ce6ea-110">Add an `Imports` statement to the file for the `System.Linq.Expressions` namespace.</span></span>

3. <span data-ttu-id="ce6ea-111">向项目中添加 `AndAlsoModifier` 类。</span><span class="sxs-lookup"><span data-stu-id="ce6ea-111">Add the `AndAlsoModifier` class to your project.</span></span>

    ```vb
    Public Class AndAlsoModifier
        Inherits ExpressionVisitor

        Public Function Modify(ByVal expr As Expression) As Expression
            Return Visit(expr)
        End Function

        Protected Overrides Function VisitBinary(ByVal b As BinaryExpression) As Expression
            If b.NodeType = ExpressionType.AndAlso Then
                Dim left = Me.Visit(b.Left)
                Dim right = Me.Visit(b.Right)

                ' Make this binary expression an OrElse operation instead
                ' of an AndAlso operation.
                Return Expression.MakeBinary(ExpressionType.OrElse, left, right, _
                                             b.IsLiftedToNull, b.Method)
            End If

            Return MyBase.VisitBinary(b)
        End Function
    End Class
    ```

    <span data-ttu-id="ce6ea-112">此类继承 <xref:System.Linq.Expressions.ExpressionVisitor> 类，并且专用于修改表示条件 `AND` 运算的表达式。</span><span class="sxs-lookup"><span data-stu-id="ce6ea-112">This class inherits the <xref:System.Linq.Expressions.ExpressionVisitor> class and is specialized to modify expressions that represent conditional `AND` operations.</span></span> <span data-ttu-id="ce6ea-113">它将运算从条件 `AND` 更改为条件 `OR`。</span><span class="sxs-lookup"><span data-stu-id="ce6ea-113">It changes these operations from a conditional `AND` to a conditional `OR`.</span></span> <span data-ttu-id="ce6ea-114">若要执行此操作，此类替代基类型的 <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> 方法，因为条件 `AND` 表达式表示为二进制表达式。</span><span class="sxs-lookup"><span data-stu-id="ce6ea-114">To do this, the class overrides the <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> method of the base type, because conditional `AND` expressions are represented as binary expressions.</span></span> <span data-ttu-id="ce6ea-115">在 `VisitBinary` 方法中，如果传递给它的表达式表示条件 `AND` 操作，那么代码将构造一个新的表达式，此表达式包含条件 `OR` 运算符，而不是条件 `AND` 运算符。</span><span class="sxs-lookup"><span data-stu-id="ce6ea-115">In the `VisitBinary` method, if the expression that is passed to it represents a conditional `AND` operation, the code constructs a new expression that contains the conditional `OR` operator instead of the conditional `AND` operator.</span></span> <span data-ttu-id="ce6ea-116">如果传递给 `VisitBinary` 的表达式不表示条件 `AND` 运算，那么此方法遵从基类实现。</span><span class="sxs-lookup"><span data-stu-id="ce6ea-116">If the expression that is passed to `VisitBinary` does not represent a conditional `AND` operation, the method defers to the base class implementation.</span></span> <span data-ttu-id="ce6ea-117">基类方法构造类似于所传递的表达式树的节点，但是这些节点将子树替换为访问者以递归方式生成的表达式树。</span><span class="sxs-lookup"><span data-stu-id="ce6ea-117">The base class methods construct nodes that are like the expression trees that are passed in, but the nodes have their sub trees replaced with the expression trees that are produced recursively by the visitor.</span></span>

4. <span data-ttu-id="ce6ea-118">向 `Imports` 命名空间的文件添加语句 `System.Linq.Expressions` 。</span><span class="sxs-lookup"><span data-stu-id="ce6ea-118">Add an `Imports` statement to the file for the `System.Linq.Expressions` namespace.</span></span>

5. <span data-ttu-id="ce6ea-119">向 `Main` Module1 文件中的方法添加代码以创建表达式树，并将其传递给将修改它的方法。</span><span class="sxs-lookup"><span data-stu-id="ce6ea-119">Add code to the `Main` method in the Module1.vb file to create an expression tree and pass it to the method that will modify it.</span></span>

    ```vb
    Dim expr As Expression(Of Func(Of String, Boolean)) = _
        Function(name) name.Length > 10 AndAlso name.StartsWith("G")

    Console.WriteLine(expr)

    Dim modifier As New AndAlsoModifier()
    Dim modifiedExpr = modifier.Modify(CType(expr, Expression))

    Console.WriteLine(modifiedExpr)

    ' This code produces the following output:
    ' name => ((name.Length > 10) && name.StartsWith("G"))
    ' name => ((name.Length > 10) || name.StartsWith("G"))
    ```

    <span data-ttu-id="ce6ea-120">此代码创建的表达式中包含条件 `AND` 运算。</span><span class="sxs-lookup"><span data-stu-id="ce6ea-120">The code creates an expression that contains a conditional `AND` operation.</span></span> <span data-ttu-id="ce6ea-121">然后，此代码创建 `AndAlsoModifier` 类的实例，并将表达式传递给此类的 `Modify` 方法。</span><span class="sxs-lookup"><span data-stu-id="ce6ea-121">It then creates an instance of the `AndAlsoModifier` class and passes the expression to the `Modify` method of this class.</span></span> <span data-ttu-id="ce6ea-122">输出原始以及修改后的表达式树以显示更改。</span><span class="sxs-lookup"><span data-stu-id="ce6ea-122">Both the original and the modified expression trees are outputted to show the change.</span></span>

6. <span data-ttu-id="ce6ea-123">编译并运行该应用程序。</span><span class="sxs-lookup"><span data-stu-id="ce6ea-123">Compile and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="ce6ea-124">请参阅</span><span class="sxs-lookup"><span data-stu-id="ce6ea-124">See also</span></span>

- [<span data-ttu-id="ce6ea-125">如何：执行表达式树 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce6ea-125">How to: Execute Expression Trees (Visual Basic)</span></span>](how-to-execute-expression-trees.md)
- [<span data-ttu-id="ce6ea-126">表达式树 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce6ea-126">Expression Trees (Visual Basic)</span></span>](index.md)
