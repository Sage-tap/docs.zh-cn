---
description: 了解有关以下内容的详细信息：支持 LINQ 的 Visual Basic 功能
title: 支持 LINQ 的功能
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, LINQ features
- LINQ [Visual Basic], features supporting LINQ
ms.assetid: c821bb50-b6f6-4cf9-8aba-2717e465bd3a
ms.openlocfilehash: 58862ac4083bcd58ee08ef1afeebf95541c53e98
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100428632"
---
# <a name="visual-basic-features-that-support-linq"></a><span data-ttu-id="bb9a6-103">支持 LINQ 的 Visual Basic 功能</span><span class="sxs-lookup"><span data-stu-id="bb9a6-103">Visual Basic Features That Support LINQ</span></span>

<span data-ttu-id="bb9a6-104">LINQ) Language-Integrated (查询名称是指 Visual Basic 中的技术，该技术在语言中直接支持查询语法和其他语言构造。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-104">The name Language-Integrated Query (LINQ) refers to technology in Visual Basic that supports query syntax and other language constructs directly in the language.</span></span> <span data-ttu-id="bb9a6-105">使用 LINQ，无需学习新语言即可针对外部数据源进行查询。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-105">With LINQ, you do not have to learn a new language to query against an external data source.</span></span> <span data-ttu-id="bb9a6-106">您可以使用 Visual Basic 对关系数据库、XML 存储或对象中的数据进行查询。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-106">You can query against data in relational databases, XML stores, or objects by using Visual Basic.</span></span> <span data-ttu-id="bb9a6-107">这种将查询功能集成到语言中可实现语法错误和类型安全的编译时检查。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-107">This integration of query capabilities into the language enables compile-time checking for syntax errors and type safety.</span></span> <span data-ttu-id="bb9a6-108">此集成还确保你已了解在 Visual Basic 中编写丰富的可变查询所必须了解的大部分内容。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-108">This integration also ensures that you already know most of what you have to know to write rich, varied queries in Visual Basic.</span></span>  
  
 <span data-ttu-id="bb9a6-109">以下部分介绍支持 LINQ 的语言构造，以使你能够开始阅读介绍性文档、代码示例和示例应用程序。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-109">The following sections describe the language constructs that support LINQ in enough detail to enable you to get started in reading the introductory documentation, code examples, and sample applications.</span></span> <span data-ttu-id="bb9a6-110">您还可以单击链接以查找有关语言功能如何集成以实现语言集成查询的更详细说明。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-110">You can also click the links to find more detailed explanations of how the language features come together to enable language-integrated query.</span></span> <span data-ttu-id="bb9a6-111">[演练：在 Visual Basic 中编写查询](walkthrough-writing-queries.md)是一种很好的起点。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-111">A good place to start is [Walkthrough: Writing Queries in Visual Basic](walkthrough-writing-queries.md).</span></span>  
  
## <a name="query-expressions"></a><span data-ttu-id="bb9a6-112">查询表达式</span><span class="sxs-lookup"><span data-stu-id="bb9a6-112">Query Expressions</span></span>  

 <span data-ttu-id="bb9a6-113">Visual Basic 中的查询表达式可以用类似于 SQL 或 XQuery 的声明性语法来表示。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-113">Query expressions in Visual Basic can be expressed in a declarative syntax similar to that of SQL or XQuery.</span></span> <span data-ttu-id="bb9a6-114">在编译时，查询语法转换为对 LINQ 提供程序的标准查询运算符扩展方法实现的方法调用。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-114">At compile time, query syntax is converted into method calls to a LINQ provider's implementation of the standard query operator extension methods.</span></span> <span data-ttu-id="bb9a6-115">应用程序通过使用语句指定相应的命名空间来控制哪些标准查询运算符在范围内 `Imports` 。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-115">Applications control which standard query operators are in scope by specifying the appropriate namespace with an `Imports` statement.</span></span> <span data-ttu-id="bb9a6-116">Visual Basic 查询表达式的语法如下所示：</span><span class="sxs-lookup"><span data-stu-id="bb9a6-116">Syntax for a Visual Basic query expression looks like this:</span></span>  
  
 [!code-vb[VbLINQVbFeatures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#1)]  
  
 <span data-ttu-id="bb9a6-117">有关详细信息，请参阅[Visual Basic 中的 LINQ 简介](../../language-features/linq/introduction-to-linq.md)。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-117">For more information, see [Introduction to LINQ in Visual Basic](../../language-features/linq/introduction-to-linq.md).</span></span>  
  
## <a name="implicitly-typed-variables"></a><span data-ttu-id="bb9a6-118">隐式类型化变量</span><span class="sxs-lookup"><span data-stu-id="bb9a6-118">Implicitly Typed Variables</span></span>  

 <span data-ttu-id="bb9a6-119">在声明和初始化变量时，可以让编译器推断并分配类型，而不是在声明和初始化变量时显式指定类型。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-119">Instead of explicitly specifying a type when you declare and initialize a variable, you can enable the compiler to infer and assign the type.</span></span> <span data-ttu-id="bb9a6-120">这称为 *局部类型推理*。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-120">This is referred to as *local type inference*.</span></span>  
  
 <span data-ttu-id="bb9a6-121">推理出的类型为强类型化的变量，就像您显式指定其类型的变量一样。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-121">Variables whose types are inferred are strongly typed, just like variables whose type you specify explicitly.</span></span> <span data-ttu-id="bb9a6-122">仅当在方法体中定义本地变量时，局部类型推理才有效。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-122">Local type inference works only when you are defining a local variable inside a method body.</span></span> <span data-ttu-id="bb9a6-123">有关详细信息，请参阅 [选项推断语句](../../../language-reference/statements/option-infer-statement.md) 和 [局部类型推理](../../language-features/variables/local-type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-123">For more information, see [Option Infer Statement](../../../language-reference/statements/option-infer-statement.md) and [Local Type Inference](../../language-features/variables/local-type-inference.md).</span></span>  
  
 <span data-ttu-id="bb9a6-124">下面的示例阐释了局部类型推理。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-124">The following example illustrates local type inference.</span></span> <span data-ttu-id="bb9a6-125">若要使用此示例，必须将设置 `Option Infer` 为 `On` 。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-125">To use this example, you must set `Option Infer` to `On`.</span></span>  
  
 [!code-vb[VbLINQVbFeatures#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#2)]  
  
 <span data-ttu-id="bb9a6-126">局部类型推理还可以创建匿名类型，本节稍后将对此进行介绍，这对于 LINQ 查询是必需的。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-126">Local type inference also makes it possible to create anonymous types, which are described later in this section and are necessary for LINQ queries.</span></span>  
  
 <span data-ttu-id="bb9a6-127">在下面的 LINQ 示例中，如果为或，则会发生类型推理 `Option Infer` `On` `Off` 。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-127">In the following LINQ example, type inference occurs if `Option Infer` is either `On` or `Off`.</span></span> <span data-ttu-id="bb9a6-128">如果 `Option Infer` 为 `Off` 且为，则会发生编译时错误 `Option Strict` `On` 。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-128">A compile-time error occurs if `Option Infer` is `Off` and `Option Strict` is `On`.</span></span>  
  
 [!code-vb[VbLINQVbFeatures#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#3)]  
  
## <a name="object-initializers"></a><span data-ttu-id="bb9a6-129">对象初始值设定项</span><span class="sxs-lookup"><span data-stu-id="bb9a6-129">Object Initializers</span></span>  

 <span data-ttu-id="bb9a6-130">当必须创建匿名类型来保存查询结果时，可以在查询表达式中使用对象初始值设定项。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-130">Object initializers are used in query expressions when you have to create an anonymous type to hold the results of a query.</span></span> <span data-ttu-id="bb9a6-131">它们还可用于在查询之外初始化命名类型的对象。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-131">They also can be used to initialize objects of named types outside of queries.</span></span> <span data-ttu-id="bb9a6-132">通过使用对象初始值设定项，你可以在单个行中初始化对象，而无需显式调用构造函数。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-132">By using an object initializer, you can initialize an object in a single line without explicitly calling a constructor.</span></span> <span data-ttu-id="bb9a6-133">假设你有一个名为的类，该类 `Customer` 具有公共 `Name` 和 `Phone` 属性以及其他属性，则可以采用这种方式使用对象初始值设定项：</span><span class="sxs-lookup"><span data-stu-id="bb9a6-133">Assuming that you have a class named `Customer` that has public `Name` and `Phone` properties, along with other properties, an object initializer can be used in this manner:</span></span>  
  
 [!code-vb[VbLINQVbFeatures#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#4)]  
  
 <span data-ttu-id="bb9a6-134">有关详细信息，请参阅 [对象初始值设定项：命名类型和匿名类型](../../language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-134">For more information, see [Object Initializers: Named and Anonymous Types](../../language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).</span></span>  
  
## <a name="anonymous-types"></a><span data-ttu-id="bb9a6-135">匿名类型</span><span class="sxs-lookup"><span data-stu-id="bb9a6-135">Anonymous Types</span></span>  

 <span data-ttu-id="bb9a6-136">匿名类型提供了一种简便的方法，可将一组属性暂时分组到要包含在查询结果中的元素中。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-136">Anonymous types provide a convenient way to temporarily group a set of properties into an element that you want to include in a query result.</span></span> <span data-ttu-id="bb9a6-137">这使你可以按任意顺序在查询中选择可用字段的任意组合，而无需为元素定义命名的数据类型。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-137">This enables you to choose any combination of available fields in the query, in any order, without defining a named data type for the element.</span></span>  
  
 <span data-ttu-id="bb9a6-138">*匿名类型* 由编译器动态构造。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-138">An *anonymous type* is constructed dynamically by the compiler.</span></span> <span data-ttu-id="bb9a6-139">该类型的名称由编译器分配，并且它可能会随每个新的编译而更改。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-139">The name of the type is assigned by the compiler, and it might change with each new compilation.</span></span> <span data-ttu-id="bb9a6-140">因此，不能直接使用该名称。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-140">Therefore, the name cannot be used directly.</span></span> <span data-ttu-id="bb9a6-141">匿名类型的初始化方式如下：</span><span class="sxs-lookup"><span data-stu-id="bb9a6-141">Anonymous types are initialized in the following way:</span></span>  
  
 [!code-vb[VbLINQVbFeatures#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#5)]  
  
 <span data-ttu-id="bb9a6-142">有关详细信息，请参阅[匿名类型](../../language-features/objects-and-classes/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-142">For more information, see [Anonymous Types](../../language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
## <a name="extension-methods"></a><span data-ttu-id="bb9a6-143">扩展方法</span><span class="sxs-lookup"><span data-stu-id="bb9a6-143">Extension Methods</span></span>  

 <span data-ttu-id="bb9a6-144">使用扩展方法，可以将方法添加到定义之外的数据类型或接口。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-144">Extension methods enable you to add methods to a data type or interface from outside the definition.</span></span> <span data-ttu-id="bb9a6-145">利用此功能，您可以将新方法添加到现有类型，而无需实际修改类型。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-145">This feature enables you to, in effect, add new methods to an existing type without actually modifying the type.</span></span> <span data-ttu-id="bb9a6-146">标准查询运算符本身就是一组扩展方法，这些方法为实现的任何类型提供 LINQ 查询功能 <xref:System.Collections.Generic.IEnumerable%601> 。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-146">The standard query operators are themselves a set of extension methods that provide LINQ query functionality for any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="bb9a6-147">其他要 <xref:System.Collections.Generic.IEnumerable%601> 包括、和的扩展 <xref:System.Linq.Enumerable.Count%2A> <xref:System.Linq.Enumerable.Union%2A> <xref:System.Linq.Enumerable.Intersect%2A> 。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-147">Other extensions to <xref:System.Collections.Generic.IEnumerable%601> include <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Union%2A>, and <xref:System.Linq.Enumerable.Intersect%2A>.</span></span>  
  
 <span data-ttu-id="bb9a6-148">下面的扩展方法向类添加一个 print 方法 <xref:System.String> 。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-148">The following extension method adds a print method to the <xref:System.String> class.</span></span>  
  
 [!code-vb[VbLINQVbFeatures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#6)]  
  
 <span data-ttu-id="bb9a6-149">调用方法的方式类似于的普通实例方法 <xref:System.String> ：</span><span class="sxs-lookup"><span data-stu-id="bb9a6-149">The method is called like an ordinary instance method of <xref:System.String>:</span></span>  
  
 [!code-vb[VbLINQVbFeatures#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#7)]  
  
 <span data-ttu-id="bb9a6-150">有关详细信息，请参阅[扩展方法](../../language-features/procedures/extension-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-150">For more information, see [Extension Methods](../../language-features/procedures/extension-methods.md).</span></span>  
  
## <a name="lambda-expressions"></a><span data-ttu-id="bb9a6-151">Lambda 表达式</span><span class="sxs-lookup"><span data-stu-id="bb9a6-151">Lambda Expressions</span></span>  

 <span data-ttu-id="bb9a6-152">Lambda 表达式是没有名称的函数，用于计算并返回单个值。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-152">A lambda expression is a function without a name that calculates and returns a single value.</span></span> <span data-ttu-id="bb9a6-153">与命名函数不同，可以同时定义和执行 lambda 表达式。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-153">Unlike named functions, a lambda expression can be defined and executed at the same time.</span></span> <span data-ttu-id="bb9a6-154">下面的示例显示4。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-154">The following example displays 4.</span></span>  
  
 [!code-vb[VbLINQVbFeatures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#8)]  
  
 <span data-ttu-id="bb9a6-155">可以将 lambda 表达式定义分配给变量名，然后使用该名称调用函数。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-155">You can assign the lambda expression definition to a variable name and then use the name to call the function.</span></span> <span data-ttu-id="bb9a6-156">下面的示例还显示4。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-156">The following example also displays 4.</span></span>  
  
 [!code-vb[VbLINQVbFeatures#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#12)]  
  
 <span data-ttu-id="bb9a6-157">在 LINQ 中，lambda 表达式采用许多标准查询运算符。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-157">In LINQ, lambda expressions underlie many of the standard query operators.</span></span> <span data-ttu-id="bb9a6-158">编译器创建 lambda 表达式来捕获基本查询方法（如、、、等）中定义的计算 `Where` `Select` `Order By` `Take While` 。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-158">The compiler creates lambda expressions to capture the calculations that are defined in fundamental query methods such as `Where`, `Select`, `Order By`, `Take While`, and others.</span></span>  
  
 <span data-ttu-id="bb9a6-159">例如，以下代码定义一个查询，该查询从学生列表返回所有高级学生。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-159">For example, the following code defines a query that returns all senior students from a list of students.</span></span>  
  
 [!code-vb[VbLINQVbFeatures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#9)]  
  
 <span data-ttu-id="bb9a6-160">查询定义编译为类似于以下示例的代码，它使用两个 lambda 表达式来指定和的参数 `Where` `Select` 。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-160">The query definition is compiled into code that is similar to the following example, which uses two lambda expressions to specify the arguments for `Where` and `Select`.</span></span>  
  
 [!code-vb[VbLINQVbFeatures#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#10)]  
  
 <span data-ttu-id="bb9a6-161">任一版本都可以使用 `For Each` 循环运行：</span><span class="sxs-lookup"><span data-stu-id="bb9a6-161">Either version can be run by using a `For Each` loop:</span></span>  
  
 [!code-vb[VbLINQVbFeatures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#11)]  
  
 <span data-ttu-id="bb9a6-162">有关详细信息，请参阅 [Lambda 表达式](../../language-features/procedures/lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-162">For more information, see [Lambda Expressions](../../language-features/procedures/lambda-expressions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb9a6-163">请参阅</span><span class="sxs-lookup"><span data-stu-id="bb9a6-163">See also</span></span>

- [<span data-ttu-id="bb9a6-164">语言集成查询 (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb9a6-164">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="bb9a6-165">Visual Basic 中的 LINQ 入门</span><span class="sxs-lookup"><span data-stu-id="bb9a6-165">Getting Started with LINQ in Visual Basic</span></span>](getting-started-with-linq.md)
- [<span data-ttu-id="bb9a6-166">LINQ 和字符串 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb9a6-166">LINQ and Strings (Visual Basic)</span></span>](linq-and-strings.md)
- [<span data-ttu-id="bb9a6-167">Option Infer 语句</span><span class="sxs-lookup"><span data-stu-id="bb9a6-167">Option Infer Statement</span></span>](../../../language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="bb9a6-168">Option Strict 语句</span><span class="sxs-lookup"><span data-stu-id="bb9a6-168">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
