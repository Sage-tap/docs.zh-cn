---
description: '详细了解： Visual Basic 的表达式树 () '
title: 表达式树
ms.date: 07/20/2015
ms.assetid: 8bbbb02d-7ffc-476b-8c25-118d82bf5d46
ms.openlocfilehash: 7fa4f36334a5a951cbe86c6db80af77db40e245a
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100462251"
---
# <a name="expression-trees-visual-basic"></a><span data-ttu-id="21e35-103">表达式树 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21e35-103">Expression Trees (Visual Basic)</span></span>

<span data-ttu-id="21e35-104">表达式树以树形数据结构表示代码，其中每一个节点都是一种表达式，比如方法调用和 `x < y` 这样的二元运算等。</span><span class="sxs-lookup"><span data-stu-id="21e35-104">Expression trees represent code in a tree-like data structure, where each node is an expression, for example, a method call or a binary operation such as `x < y`.</span></span>  
  
 <span data-ttu-id="21e35-105">你可以对表达式树中的代码进行编辑和运算。</span><span class="sxs-lookup"><span data-stu-id="21e35-105">You can compile and run code represented by expression trees.</span></span> <span data-ttu-id="21e35-106">这样能够动态修改可执行代码、在不同数据库中执行 LINQ 查询以及创建动态查询。</span><span class="sxs-lookup"><span data-stu-id="21e35-106">This enables dynamic modification of executable code, the execution of LINQ queries in various databases, and the creation of dynamic queries.</span></span> <span data-ttu-id="21e35-107">有关 LINQ 中表达式树的详细信息，请参阅[如何：使用表达式树生成动态查询 (Visual Basic)](how-to-use-expression-trees-to-build-dynamic-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="21e35-107">For more information about expression trees in LINQ, see [How to: Use Expression Trees to Build Dynamic Queries (Visual Basic)](how-to-use-expression-trees-to-build-dynamic-queries.md).</span></span>  
  
 <span data-ttu-id="21e35-108">表达式树还能用于动态语言运行时 (DLR) 以提供动态语言和 .NET Framework 之间的互操作性，同时保证编译器编写员能够发射表达式树而非 Microsoft 中间语言 (MSIL)。</span><span class="sxs-lookup"><span data-stu-id="21e35-108">Expression trees are also used in the dynamic language runtime (DLR) to provide interoperability between dynamic languages and the .NET Framework and to enable compiler writers to emit expression trees instead of Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="21e35-109">有关 DLR 的详细信息，请参阅[动态语言运行时概述](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="21e35-109">For more information about the DLR, see [Dynamic Language Runtime Overview](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).</span></span>  
  
 <span data-ttu-id="21e35-110">你可以基于匿名 lambda 表达式通过 C# 或者 Visual Basic 编译器创建表达式树，或者通过 <xref:System.Linq.Expressions> 名称空间手动创建。</span><span class="sxs-lookup"><span data-stu-id="21e35-110">You can have the C# or Visual Basic compiler create an expression tree for you based on an anonymous lambda expression, or you can create expression trees manually by using the <xref:System.Linq.Expressions> namespace.</span></span>  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a><span data-ttu-id="21e35-111">根据 Lambda 表达式创建表达式树</span><span class="sxs-lookup"><span data-stu-id="21e35-111">Creating Expression Trees from Lambda Expressions</span></span>  

 <span data-ttu-id="21e35-112">若 lambda 表达式被分配给 <xref:System.Linq.Expressions.Expression%601> 类型的变量，则编译器可以发射代码以创建表示该 lambda 表达式的表达式树。</span><span class="sxs-lookup"><span data-stu-id="21e35-112">When a lambda expression is assigned to a variable of type <xref:System.Linq.Expressions.Expression%601>, the compiler emits code to build an expression tree that represents the lambda expression.</span></span>  
  
 <span data-ttu-id="21e35-113">Visual Basic 编译器只能从表达式 Lambda（或单行 Lambda）生成表达式树。</span><span class="sxs-lookup"><span data-stu-id="21e35-113">The Visual Basic compiler can generate expression trees only from expression lambdas (or single-line lambdas).</span></span> <span data-ttu-id="21e35-114">它无法解析语句 lambda （或多行 lambda）。</span><span class="sxs-lookup"><span data-stu-id="21e35-114">It cannot parse statement lambdas (or multi-line lambdas).</span></span> <span data-ttu-id="21e35-115">有关 Visual Basic 中 Lambda 表达式的详细信息，请参阅 [Lambda 表达式](../../language-features/procedures/lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="21e35-115">For more information about lambda expressions in Visual Basic, see [Lambda Expressions](../../language-features/procedures/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="21e35-116">下列代码示例展示如何通过 Visual Basic 编译器创建表示 Lambda 表达式 `Function(num) num < 5` 的表达式树。</span><span class="sxs-lookup"><span data-stu-id="21e35-116">The following code examples demonstrate how to have the Visual Basic compiler create an expression tree that represents the lambda expression `Function(num) num < 5`.</span></span>  
  
```vb  
Dim lambda As Expression(Of Func(Of Integer, Boolean)) =  
    Function(num) num < 5  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a><span data-ttu-id="21e35-117">通过 API 创建表达式树</span><span class="sxs-lookup"><span data-stu-id="21e35-117">Creating Expression Trees by Using the API</span></span>  

 <span data-ttu-id="21e35-118">通过 API 创建表达式树需要使用 <xref:System.Linq.Expressions.Expression> 类。</span><span class="sxs-lookup"><span data-stu-id="21e35-118">To create expression trees by using the API, use the <xref:System.Linq.Expressions.Expression> class.</span></span> <span data-ttu-id="21e35-119">类包含创建特定类型表达式树节点的静态工厂方法，比如表示参数变量的 <xref:System.Linq.Expressions.ParameterExpression>，或者是表示方法调用的 <xref:System.Linq.Expressions.MethodCallExpression>。</span><span class="sxs-lookup"><span data-stu-id="21e35-119">This class contains static factory methods that create expression tree nodes of specific types, for example, <xref:System.Linq.Expressions.ParameterExpression>, which represents a variable or parameter, or <xref:System.Linq.Expressions.MethodCallExpression>, which represents a method call.</span></span> <span data-ttu-id="21e35-120"><xref:System.Linq.Expressions.ParameterExpression> 名称空间还解释了 <xref:System.Linq.Expressions.MethodCallExpression>、<xref:System.Linq.Expressions>和另一种具体表达式类型。</span><span class="sxs-lookup"><span data-stu-id="21e35-120"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, and the other expression-specific types are also defined in the <xref:System.Linq.Expressions> namespace.</span></span> <span data-ttu-id="21e35-121">这些类型来源于抽象类型 <xref:System.Linq.Expressions.Expression>。</span><span class="sxs-lookup"><span data-stu-id="21e35-121">These types derive from the abstract type <xref:System.Linq.Expressions.Expression>.</span></span>  
  
 <span data-ttu-id="21e35-122">下列代码示例展示如何使用 API 创建表示 Lambda 表达式 `Function(num) num < 5` 的表达式树。</span><span class="sxs-lookup"><span data-stu-id="21e35-122">The following code example demonstrates how to create an expression tree that represents the lambda expression `Function(num) num < 5` by using the API.</span></span>  
  
```vb  
' Import the following namespace to your project: System.Linq.Expressions  
  
' Manually build the expression tree for the lambda expression num => num < 5.  
Dim numParam As ParameterExpression = Expression.Parameter(GetType(Integer), "num")  
Dim five As ConstantExpression = Expression.Constant(5, GetType(Integer))  
Dim numLessThanFive As BinaryExpression = Expression.LessThan(numParam, five)  
Dim lambda1 As Expression(Of Func(Of Integer, Boolean)) =  
  Expression.Lambda(Of Func(Of Integer, Boolean))(  
        numLessThanFive,  
        New ParameterExpression() {numParam})  
```  
  
 <span data-ttu-id="21e35-123">在 .NET Framework 4 或更高版本中，表达式树 API 还支持赋值表达式和控制流表达式，例如循环、条件块和 `try-catch` 块等。</span><span class="sxs-lookup"><span data-stu-id="21e35-123">In .NET Framework 4 or later, the expression trees API also supports assignments and control flow expressions such as loops, conditional blocks, and `try-catch` blocks.</span></span> <span data-ttu-id="21e35-124">相对于通过 Visual Basic 编译器和 Lambda 表达式创建表达式树，还可利用 API 创建更加复杂的表达式树。</span><span class="sxs-lookup"><span data-stu-id="21e35-124">By using the API, you can create expression trees that are more complex than those that can be created from lambda expressions by the Visual Basic compiler.</span></span> <span data-ttu-id="21e35-125">下列示例展示如何创建计算数字阶乘的表达式树。</span><span class="sxs-lookup"><span data-stu-id="21e35-125">The following example demonstrates how to create an expression tree that calculates the factorial of a number.</span></span>  
  
```vb  
' Creating a parameter expression.  
Dim value As ParameterExpression =  
    Expression.Parameter(GetType(Integer), "value")  
  
' Creating an expression to hold a local variable.
Dim result As ParameterExpression =  
    Expression.Parameter(GetType(Integer), "result")  
  
' Creating a label to jump to from a loop.  
Dim label As LabelTarget = Expression.Label(GetType(Integer))  
  
' Creating a method body.  
Dim block As BlockExpression = Expression.Block(  
    New ParameterExpression() {result},  
    Expression.Assign(result, Expression.Constant(1)),  
    Expression.Loop(  
        Expression.IfThenElse(  
            Expression.GreaterThan(value, Expression.Constant(1)),  
            Expression.MultiplyAssign(result,  
                Expression.PostDecrementAssign(value)),  
            Expression.Break(label, result)  
        ),  
        label  
    )  
)  
  
' Compile an expression tree and return a delegate.  
Dim factorial As Integer =  
    Expression.Lambda(Of Func(Of Integer, Integer))(block, value).Compile()(5)  
  
Console.WriteLine(factorial)  
' Prints 120.  
```

<span data-ttu-id="21e35-126">有关详细信息，请参阅[在 Visual Studio 2010 中使用表达式树生成动态方法](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/)，该方法也适用于 Visual Studio 的更高版本。</span><span class="sxs-lookup"><span data-stu-id="21e35-126">For more information, see [Generating Dynamic Methods with Expression Trees in Visual Studio 2010](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), which also applies to later versions of Visual Studio.</span></span>
  
## <a name="parsing-expression-trees"></a><span data-ttu-id="21e35-127">解析表达式树</span><span class="sxs-lookup"><span data-stu-id="21e35-127">Parsing Expression Trees</span></span>  

 <span data-ttu-id="21e35-128">下列代码示例展示如何分解表示 Lambda 表达式 `Function(num) num < 5` 的表达式树。</span><span class="sxs-lookup"><span data-stu-id="21e35-128">The following code example demonstrates how the expression tree that represents the lambda expression `Function(num) num < 5` can be decomposed into its parts.</span></span>  
  
```vb  
' Import the following namespace to your project: System.Linq.Expressions  
  
' Create an expression tree.  
Dim exprTree As Expression(Of Func(Of Integer, Boolean)) = Function(num) num < 5  
  
' Decompose the expression tree.  
Dim param As ParameterExpression = exprTree.Parameters(0)  
Dim operation As BinaryExpression = exprTree.Body  
Dim left As ParameterExpression = operation.Left  
Dim right As ConstantExpression = operation.Right  
  
Console.WriteLine(String.Format("Decomposed expression: {0} => {1} {2} {3}",  
                  param.Name, left.Name, operation.NodeType, right.Value))  
  
' This code produces the following output:  
'  
' Decomposed expression: num => num LessThan 5  
```  
  
## <a name="immutability-of-expression-trees"></a><span data-ttu-id="21e35-129">表达式树永久性</span><span class="sxs-lookup"><span data-stu-id="21e35-129">Immutability of Expression Trees</span></span>  

 <span data-ttu-id="21e35-130">表达式树应具有永久性。</span><span class="sxs-lookup"><span data-stu-id="21e35-130">Expression trees should be immutable.</span></span> <span data-ttu-id="21e35-131">这意味着如果你想修改某个表达式树，则必须复制该表达式树然后替换其中的节点来创建一个新的表达式树。</span><span class="sxs-lookup"><span data-stu-id="21e35-131">This means that if you want to modify an expression tree, you must construct a new expression tree by copying the existing one and replacing nodes in it.</span></span> <span data-ttu-id="21e35-132">你可以使用表达式树访问者遍历现有表达式树。</span><span class="sxs-lookup"><span data-stu-id="21e35-132">You can use an expression tree visitor to traverse the existing expression tree.</span></span> <span data-ttu-id="21e35-133">有关详细信息，请参阅[如何：修改表达式树 (Visual Basic)](how-to-modify-expression-trees.md)。</span><span class="sxs-lookup"><span data-stu-id="21e35-133">For more information, see [How to: Modify Expression Trees (Visual Basic)](how-to-modify-expression-trees.md).</span></span>  
  
## <a name="compiling-expression-trees"></a><span data-ttu-id="21e35-134">编译表达式树</span><span class="sxs-lookup"><span data-stu-id="21e35-134">Compiling Expression Trees</span></span>  

 <span data-ttu-id="21e35-135"><xref:System.Linq.Expressions.Expression%601> 类型提供了 <xref:System.Linq.Expressions.Expression%601.Compile%2A> 方法以将表达式树表示的代码编译成可执行委托。</span><span class="sxs-lookup"><span data-stu-id="21e35-135">The <xref:System.Linq.Expressions.Expression%601> type provides the <xref:System.Linq.Expressions.Expression%601.Compile%2A> method that compiles the code represented by an expression tree into an executable delegate.</span></span>  
  
 <span data-ttu-id="21e35-136">下列代码示例展示如何编译表达式树并运行结果代码。</span><span class="sxs-lookup"><span data-stu-id="21e35-136">The following code example demonstrates how to compile an expression tree and run the resulting code.</span></span>  
  
```vb  
' Creating an expression tree.  
Dim expr As Expression(Of Func(Of Integer, Boolean)) =  
    Function(num) num < 5  
  
' Compiling the expression tree into a delegate.  
Dim result As Func(Of Integer, Boolean) = expr.Compile()  
  
' Invoking the delegate and writing the result to the console.  
Console.WriteLine(result(4))  
  
' Prints True.  
  
' You can also use simplified syntax  
' to compile and run an expression tree.  
' The following line can replace two previous statements.  
Console.WriteLine(expr.Compile()(4))  
  
' Also prints True.  
```  
  
 <span data-ttu-id="21e35-137">有关详细信息，请参阅[如何：执行表达式树 (Visual Basic)](how-to-execute-expression-trees.md)。</span><span class="sxs-lookup"><span data-stu-id="21e35-137">For more information, see [How to: Execute Expression Trees (Visual Basic)](how-to-execute-expression-trees.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21e35-138">请参阅</span><span class="sxs-lookup"><span data-stu-id="21e35-138">See also</span></span>

- <xref:System.Linq.Expressions>
- [<span data-ttu-id="21e35-139">如何：执行表达式树 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21e35-139">How to: Execute Expression Trees (Visual Basic)</span></span>](how-to-execute-expression-trees.md)
- [<span data-ttu-id="21e35-140">如何：修改表达式树 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21e35-140">How to: Modify Expression Trees (Visual Basic)</span></span>](how-to-modify-expression-trees.md)
- [<span data-ttu-id="21e35-141">Lambda 表达式</span><span class="sxs-lookup"><span data-stu-id="21e35-141">Lambda Expressions</span></span>](../../language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="21e35-142">动态语言运行时概述</span><span class="sxs-lookup"><span data-stu-id="21e35-142">Dynamic Language Runtime Overview</span></span>](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)
- [<span data-ttu-id="21e35-143">Visual Basic 的编程概念 () </span><span class="sxs-lookup"><span data-stu-id="21e35-143">Programming Concepts (Visual Basic)</span></span>](../index.md)
