---
description: '了解详细信息：编写第一个 LINQ 查询 (Visual Basic) '
title: 编写第一个 LINQ 查询
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ queries [Visual Basic]
- LINQ [Visual Basic], writing queries
ms.assetid: 4affb732-3e9b-4479-aa31-1f9bd8183cbe
ms.openlocfilehash: cb57ae3c22b7e2ee2c3b66a8f033eda6fd72e16a
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100477510"
---
# <a name="writing-your-first-linq-query-visual-basic"></a><span data-ttu-id="3254a-103">编写第一个 LINQ 查询 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3254a-103">Writing Your First LINQ Query (Visual Basic)</span></span>

<span data-ttu-id="3254a-104">*查询* 是一种从数据源检索数据的表达式。</span><span class="sxs-lookup"><span data-stu-id="3254a-104">A *query* is an expression that retrieves data from a data source.</span></span> <span data-ttu-id="3254a-105">查询以专用查询语言表示。</span><span class="sxs-lookup"><span data-stu-id="3254a-105">Queries are expressed in a dedicated query language.</span></span> <span data-ttu-id="3254a-106">随着时间的推移，为不同类型的数据源开发了不同的语言，例如，用于关系数据库的 SQL 和用于 XML 的 XQuery。</span><span class="sxs-lookup"><span data-stu-id="3254a-106">Over time, different languages have been developed for different types of data sources, for example, SQL for relational databases and XQuery for XML.</span></span> <span data-ttu-id="3254a-107">这样，应用程序开发人员就可以为所支持的每种类型的数据源或数据格式学习一种新的查询语言。</span><span class="sxs-lookup"><span data-stu-id="3254a-107">This makes it necessary for the application developer to learn a new query language for each type of data source or data format that is supported.</span></span>  
  
 <span data-ttu-id="3254a-108">Language-Integrated 查询 (LINQ) 通过提供一种跨各种数据源和格式使用数据的一致模型，简化了这种情况。</span><span class="sxs-lookup"><span data-stu-id="3254a-108">Language-Integrated Query (LINQ) simplifies the situation by offering a consistent model for working with data across various kinds of data sources and formats.</span></span> <span data-ttu-id="3254a-109">在 LINQ 查询中，始终会用到对象。</span><span class="sxs-lookup"><span data-stu-id="3254a-109">In a LINQ query, you are always working with objects.</span></span> <span data-ttu-id="3254a-110">您可以使用相同的基本编码模式来查询和转换 XML 文档、SQL 数据库、ADO.NET 数据集和实体中的数据、.NET Framework 集合以及 LINQ 提供程序可用的任何其他源或格式。</span><span class="sxs-lookup"><span data-stu-id="3254a-110">You use the same basic coding patterns to query and transform data in XML documents, SQL databases, ADO.NET datasets and entities, .NET Framework collections, and any other source or format for which a LINQ provider is available.</span></span> <span data-ttu-id="3254a-111">本文档介绍了创建和使用基本 LINQ 查询的三个阶段。</span><span class="sxs-lookup"><span data-stu-id="3254a-111">This document describes the three phases of the creation and use of basic LINQ queries.</span></span>  
  
## <a name="three-stages-of-a-query-operation"></a><span data-ttu-id="3254a-112">查询操作的三个阶段</span><span class="sxs-lookup"><span data-stu-id="3254a-112">Three Stages of a Query Operation</span></span>  

 <span data-ttu-id="3254a-113">LINQ 查询操作包含三个操作：</span><span class="sxs-lookup"><span data-stu-id="3254a-113">LINQ query operations consist of three actions:</span></span>  
  
1. <span data-ttu-id="3254a-114">获取数据源。</span><span class="sxs-lookup"><span data-stu-id="3254a-114">Obtain the data source or sources.</span></span>  
  
2. <span data-ttu-id="3254a-115">创建查询。</span><span class="sxs-lookup"><span data-stu-id="3254a-115">Create the query.</span></span>  
  
3. <span data-ttu-id="3254a-116">执行查询。</span><span class="sxs-lookup"><span data-stu-id="3254a-116">Execute the query.</span></span>  
  
 <span data-ttu-id="3254a-117">在 LINQ 中，查询的执行与查询的创建不同。</span><span class="sxs-lookup"><span data-stu-id="3254a-117">In LINQ, the execution of a query is distinct from the creation of the query.</span></span> <span data-ttu-id="3254a-118">不只是通过创建查询来检索任何数据。</span><span class="sxs-lookup"><span data-stu-id="3254a-118">You do not retrieve any data just by creating a query.</span></span> <span data-ttu-id="3254a-119">这一点将在本主题后面部分进行更详细的讨论。</span><span class="sxs-lookup"><span data-stu-id="3254a-119">This point is discussed in more detail later in this topic.</span></span>  
  
 <span data-ttu-id="3254a-120">下面的示例演示了查询操作的三个部分。</span><span class="sxs-lookup"><span data-stu-id="3254a-120">The following example illustrates the three parts of a query operation.</span></span> <span data-ttu-id="3254a-121">为了便于演示，该示例使用一个整数数组作为方便的数据源。</span><span class="sxs-lookup"><span data-stu-id="3254a-121">The example uses an array of integers as a convenient data source for demonstration purposes.</span></span> <span data-ttu-id="3254a-122">不过，相同的概念也适用于其他数据源。</span><span class="sxs-lookup"><span data-stu-id="3254a-122">However, the same concepts also apply to other data sources.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3254a-123">在 "编译" 页上的 " [项目设计器" (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)上，确保 " **选项推断** " 设置为 **"开"**。</span><span class="sxs-lookup"><span data-stu-id="3254a-123">On the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), ensure that **Option infer** is set to **On**.</span></span>  
  
 [!code-vb[VbLINQFirstQuery#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#1)]  
  
 <span data-ttu-id="3254a-124">输出：</span><span class="sxs-lookup"><span data-stu-id="3254a-124">Output:</span></span>  
  
 `0 2 4 6`  
  
## <a name="the-data-source"></a><span data-ttu-id="3254a-125">数据源</span><span class="sxs-lookup"><span data-stu-id="3254a-125">The Data Source</span></span>  

 <span data-ttu-id="3254a-126">由于上一个示例中的数据源是一个数组，因此它隐式支持泛型 <xref:System.Collections.Generic.IEnumerable%601> 接口。</span><span class="sxs-lookup"><span data-stu-id="3254a-126">Because the data source in the previous example is an array, it implicitly supports the generic <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="3254a-127">这种情况下，您可以使用数组作为 LINQ 查询的数据源。</span><span class="sxs-lookup"><span data-stu-id="3254a-127">It is this fact that enables you to use an array as a data source for a LINQ query.</span></span> <span data-ttu-id="3254a-128">支持 <xref:System.Collections.Generic.IEnumerable%601> 或派生接口（如泛型 <xref:System.Linq.IQueryable%601>）的类型称为可查询类型  。</span><span class="sxs-lookup"><span data-stu-id="3254a-128">Types that support <xref:System.Collections.Generic.IEnumerable%601> or a derived interface such as the generic <xref:System.Linq.IQueryable%601> are called *queryable types*.</span></span>  
  
 <span data-ttu-id="3254a-129">作为隐式查询类型，数组不需要修改或特殊处理就可以用作 LINQ 数据源。</span><span class="sxs-lookup"><span data-stu-id="3254a-129">As an implicitly queryable type, the array requires no modification or special treatment to serve as a LINQ data source.</span></span> <span data-ttu-id="3254a-130">对于支持的任何集合类型也是如此 <xref:System.Collections.Generic.IEnumerable%601> ，包括泛型 <xref:System.Collections.Generic.List%601> 、 <xref:System.Collections.Generic.Dictionary%602> 和 .NET Framework 类库中的其他类。</span><span class="sxs-lookup"><span data-stu-id="3254a-130">The same is true for any collection type that supports <xref:System.Collections.Generic.IEnumerable%601>, including the generic <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.Dictionary%602>, and other classes in the .NET Framework class library.</span></span>  
  
 <span data-ttu-id="3254a-131">如果尚未实现源数据 <xref:System.Collections.Generic.IEnumerable%601> ，则需要 LINQ 提供程序来实现该数据源的 *标准查询运算符* 的功能。</span><span class="sxs-lookup"><span data-stu-id="3254a-131">If the source data does not already implement <xref:System.Collections.Generic.IEnumerable%601>, a LINQ provider is needed to implement the functionality of the *standard query operators* for that data source.</span></span> <span data-ttu-id="3254a-132">例如， [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 处理将 XML 文档加载到可查询类型的工作 <xref:System.Xml.Linq.XElement> ，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="3254a-132">For example, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] handles the work of loading an XML document into a queryable <xref:System.Xml.Linq.XElement> type, as shown in the following example.</span></span> <span data-ttu-id="3254a-133">有关标准查询运算符的详细信息，请参阅 [标准查询运算符概述 (Visual Basic) ](standard-query-operators-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="3254a-133">For more information about standard query operators, see [Standard Query Operators Overview (Visual Basic)](standard-query-operators-overview.md).</span></span>  
  
 [!code-vb[VbLINQFirstQuery#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#2)]  
  
 <span data-ttu-id="3254a-134">使用 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] ，你可以在设计时先使用 Visual studio 中的 [visual studio 中的 LINQ to SQL 工具](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2) 来创建对象关系映射。</span><span class="sxs-lookup"><span data-stu-id="3254a-134">With [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], you first create an object-relational mapping at design time, either manually or by using the [LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2) in Visual Studio.</span></span> <span data-ttu-id="3254a-135">针对这些对象编写查询，然后由 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 在运行时处理与数据库的通信。</span><span class="sxs-lookup"><span data-stu-id="3254a-135">You write your queries against the objects, and at run-time [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] handles the communication with the database.</span></span> <span data-ttu-id="3254a-136">在下面的示例中， `customers` 表示数据库中的特定表，并 <xref:System.Data.Linq.Table%601> 支持泛型 <xref:System.Linq.IQueryable%601> 。</span><span class="sxs-lookup"><span data-stu-id="3254a-136">In the following example, `customers` represents a specific table in the database, and <xref:System.Data.Linq.Table%601> supports generic <xref:System.Linq.IQueryable%601>.</span></span>  
  
```vb  
' Create a data source from a SQL table.  
Dim db As New DataContext("C:\Northwind\Northwnd.mdf")  
Dim customers As Table(Of Customer) = db.GetTable(Of Customer)  
```  
  
 <span data-ttu-id="3254a-137">有关如何创建特定类型的数据源的详细信息，请参阅各种 LINQ 提供程序的文档。</span><span class="sxs-lookup"><span data-stu-id="3254a-137">For more information about how to create specific types of data sources, see the documentation for the various LINQ providers.</span></span> <span data-ttu-id="3254a-138"> (获取这些提供程序的列表，请参阅 [LINQ (语言集成查询) ](index.md)。 ) 基本规则非常简单： LINQ 数据源是支持泛型接口的任何对象 <xref:System.Collections.Generic.IEnumerable%601> ，或者是从该接口继承的接口。</span><span class="sxs-lookup"><span data-stu-id="3254a-138">(For a list of these providers, see [LINQ (Language-Integrated Query)](index.md).) The basic rule is simple: a LINQ data source is any object that supports the generic <xref:System.Collections.Generic.IEnumerable%601> interface, or an interface that inherits from it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3254a-139"><xref:System.Collections.ArrayList>支持非泛型接口的类型（如） <xref:System.Collections.IEnumerable> 也可用作 LINQ 数据源。</span><span class="sxs-lookup"><span data-stu-id="3254a-139">Types such as <xref:System.Collections.ArrayList> that support the non-generic <xref:System.Collections.IEnumerable> interface can also be used as LINQ data sources.</span></span> <span data-ttu-id="3254a-140">有关使用的示例 <xref:System.Collections.ArrayList> ，请参阅 [如何：使用 LINQ (查询 ArrayList Visual Basic) ](how-to-query-an-arraylist-with-linq.md)。</span><span class="sxs-lookup"><span data-stu-id="3254a-140">For an example that uses an <xref:System.Collections.ArrayList>, see [How to: Query an ArrayList with LINQ (Visual Basic)](how-to-query-an-arraylist-with-linq.md).</span></span>  
  
## <a name="the-query"></a><span data-ttu-id="3254a-141">查询</span><span class="sxs-lookup"><span data-stu-id="3254a-141">The Query</span></span>  

 <span data-ttu-id="3254a-142">在查询中，可以指定要从数据源中检索的信息。</span><span class="sxs-lookup"><span data-stu-id="3254a-142">In the query, you specify what information you want to retrieve from the data source or sources.</span></span> <span data-ttu-id="3254a-143">您还可以选择在返回信息之前如何对其进行排序、分组或结构化。</span><span class="sxs-lookup"><span data-stu-id="3254a-143">You also have the option of specifying how that information should be sorted, grouped, or structured before it is returned.</span></span> <span data-ttu-id="3254a-144">若要启用查询创建，Visual Basic 已将新的查询语法合并到语言中。</span><span class="sxs-lookup"><span data-stu-id="3254a-144">To enable query creation, Visual Basic has incorporated new query syntax into the language.</span></span>  
  
 <span data-ttu-id="3254a-145">执行时，以下示例中的查询将从整数数组中返回所有偶数 `numbers` 。</span><span class="sxs-lookup"><span data-stu-id="3254a-145">When it is executed, the query in the following example returns all the even numbers from an integer array, `numbers`.</span></span>  
  
 [!code-vb[VbLINQFirstQuery#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#1)]  
  
 <span data-ttu-id="3254a-146">查询表达式包含三个子句： `From` 、 `Where` 和 `Select` 。</span><span class="sxs-lookup"><span data-stu-id="3254a-146">The query expression contains three clauses: `From`, `Where`, and `Select`.</span></span> <span data-ttu-id="3254a-147">[基本查询操作 (Visual Basic) ](basic-query-operations.md)中讨论了每个查询表达式子句的特定函数和目的。</span><span class="sxs-lookup"><span data-stu-id="3254a-147">The specific function and purpose of each query expression clause is discussed in [Basic Query Operations (Visual Basic)](basic-query-operations.md).</span></span> <span data-ttu-id="3254a-148">有关详细信息，请参阅 [查询](../../../language-reference/queries/index.md)。</span><span class="sxs-lookup"><span data-stu-id="3254a-148">For more information, see [Queries](../../../language-reference/queries/index.md).</span></span> <span data-ttu-id="3254a-149">请注意，在 LINQ 中，查询定义通常存储在变量中，并在以后执行。</span><span class="sxs-lookup"><span data-stu-id="3254a-149">Note that in LINQ, a query definition often is stored in a variable and executed later.</span></span> <span data-ttu-id="3254a-150">查询变量（如 `evensQuery` 前面的示例中的）必须是可查询的类型。</span><span class="sxs-lookup"><span data-stu-id="3254a-150">The query variable, such as `evensQuery` in the previous example, must be a queryable type.</span></span> <span data-ttu-id="3254a-151">的类型 `evensQuery` 为 `IEnumerable(Of Integer)` ，由编译器使用局部类型推理分配。</span><span class="sxs-lookup"><span data-stu-id="3254a-151">The type of `evensQuery` is `IEnumerable(Of Integer)`, assigned by the compiler using local type inference.</span></span>  
  
 <span data-ttu-id="3254a-152">请记住，查询变量本身不会执行任何操作，也不会返回任何数据。</span><span class="sxs-lookup"><span data-stu-id="3254a-152">It is important to remember that the query variable itself takes no action and returns no data.</span></span> <span data-ttu-id="3254a-153">它仅存储查询定义。</span><span class="sxs-lookup"><span data-stu-id="3254a-153">It only stores the query definition.</span></span> <span data-ttu-id="3254a-154">在上面的示例中，它是 `For Each` 执行查询的循环。</span><span class="sxs-lookup"><span data-stu-id="3254a-154">In the previous example, it is the `For Each` loop that executes the query.</span></span>  
  
## <a name="query-execution"></a><span data-ttu-id="3254a-155">查询执行</span><span class="sxs-lookup"><span data-stu-id="3254a-155">Query Execution</span></span>  

 <span data-ttu-id="3254a-156">查询执行与查询创建分离。</span><span class="sxs-lookup"><span data-stu-id="3254a-156">Query execution is separate from query creation.</span></span> <span data-ttu-id="3254a-157">查询创建定义查询，但执行由不同的机制触发。</span><span class="sxs-lookup"><span data-stu-id="3254a-157">Query creation defines the query, but execution is triggered by a different mechanism.</span></span> <span data-ttu-id="3254a-158">可以在定义查询 *后立即执行查询 ()* ，或者可以存储定义，稍后 (*延迟执行*) 执行查询。</span><span class="sxs-lookup"><span data-stu-id="3254a-158">A query can be executed as soon as it is defined (*immediate execution*), or the definition can be stored and the query can be executed later (*deferred execution*).</span></span>  
  
### <a name="deferred-execution"></a><span data-ttu-id="3254a-159">延迟执行</span><span class="sxs-lookup"><span data-stu-id="3254a-159">Deferred Execution</span></span>  

 <span data-ttu-id="3254a-160">典型 LINQ 查询类似于上一示例中定义的查询 `evensQuery` 。</span><span class="sxs-lookup"><span data-stu-id="3254a-160">A typical LINQ query resembles the one in the previous example, in which `evensQuery` is defined.</span></span> <span data-ttu-id="3254a-161">它将创建查询，但不会立即执行。</span><span class="sxs-lookup"><span data-stu-id="3254a-161">It creates the query but does not execute it immediately.</span></span> <span data-ttu-id="3254a-162">相反，查询定义存储在查询变量中 `evensQuery` 。</span><span class="sxs-lookup"><span data-stu-id="3254a-162">Instead, the query definition is stored in the query variable `evensQuery`.</span></span> <span data-ttu-id="3254a-163">稍后，您将执行查询（通常通过使用 `For Each` 返回值序列的循环）或应用标准查询运算符（如 `Count` 或） `Max` 。</span><span class="sxs-lookup"><span data-stu-id="3254a-163">You execute the query later, typically by using a `For Each` loop, which returns a sequence of values, or by applying a standard query operator, such as `Count` or `Max`.</span></span> <span data-ttu-id="3254a-164">此过程称为 " *延迟执行*"。</span><span class="sxs-lookup"><span data-stu-id="3254a-164">This process is referred to as *deferred execution*.</span></span>  
  
 [!code-vb[VbLINQFirstQuery#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#7)]  
  
 <span data-ttu-id="3254a-165">对于值序列，可以通过在 `For Each` 前面的示例中使用循环 (来访问检索到的数据 `number`) 。</span><span class="sxs-lookup"><span data-stu-id="3254a-165">For a sequence of values, you access the retrieved data by using the iteration variable in the `For Each` loop (`number` in the previous example).</span></span> <span data-ttu-id="3254a-166">由于查询变量 `evensQuery` 包含查询定义，而不是查询结果，因此可以多次使用查询变量，按所需频率执行查询。</span><span class="sxs-lookup"><span data-stu-id="3254a-166">Because the query variable, `evensQuery`, holds the query definition rather than the query results, you can execute a query as often as you want by using the query variable more than one time.</span></span> <span data-ttu-id="3254a-167">例如，你的应用程序中可能存在由单独的应用程序持续更新的数据库。</span><span class="sxs-lookup"><span data-stu-id="3254a-167">For example, you might have a database in your application that is being updated continually by a separate application.</span></span> <span data-ttu-id="3254a-168">创建了从该数据库中检索数据的查询后，可以使用 `For Each` 循环重复执行该查询，每次检索最新的数据。</span><span class="sxs-lookup"><span data-stu-id="3254a-168">After you have created a query that retrieves data from that database, you can use a `For Each` loop to execute the query repeatedly, retrieving the most recent data every time.</span></span>  
  
 <span data-ttu-id="3254a-169">下面的示例演示延迟执行的工作方式。</span><span class="sxs-lookup"><span data-stu-id="3254a-169">The following example demonstrates how deferred execution works.</span></span> <span data-ttu-id="3254a-170">`evensQuery2`使用循环定义并执行后 `For Each` ，如前面的示例中所示，数据源中的某些元素 `numbers` 将发生更改。</span><span class="sxs-lookup"><span data-stu-id="3254a-170">After `evensQuery2` is defined and executed with a `For Each` loop, as in the previous examples, some elements in the data source `numbers` are changed.</span></span> <span data-ttu-id="3254a-171">然后 `For Each` 再次运行另一个循环 `evensQuery2` 。</span><span class="sxs-lookup"><span data-stu-id="3254a-171">Then a second `For Each` loop runs `evensQuery2` again.</span></span> <span data-ttu-id="3254a-172">由于 `For Each` 循环再次执行查询（使用中的新值），因此结果是不同的 `numbers` 。</span><span class="sxs-lookup"><span data-stu-id="3254a-172">The results are different the second time, because the `For Each` loop executes the query again, using the new values in `numbers`.</span></span>  
  
 [!code-vb[VbLINQFirstQuery#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#3)]  
  
 <span data-ttu-id="3254a-173">输出：</span><span class="sxs-lookup"><span data-stu-id="3254a-173">Output:</span></span>  
  
 `Evens in original array:`  
  
 `0  2  4  6`  
  
 `Evens in changed array:`  
  
 `0  10  2  22  8`  
  
### <a name="immediate-execution"></a><span data-ttu-id="3254a-174">立即执行</span><span class="sxs-lookup"><span data-stu-id="3254a-174">Immediate Execution</span></span>  

 <span data-ttu-id="3254a-175">在延迟的查询执行中，查询定义存储在查询变量中以供以后执行。</span><span class="sxs-lookup"><span data-stu-id="3254a-175">In deferred execution of queries, the query definition is stored in a query variable for later execution.</span></span> <span data-ttu-id="3254a-176">在 "立即执行" 中，将在定义时执行查询。</span><span class="sxs-lookup"><span data-stu-id="3254a-176">In immediate execution, the query is executed at the time of its definition.</span></span> <span data-ttu-id="3254a-177">当应用需要访问查询结果的单个元素的方法时，将触发执行。</span><span class="sxs-lookup"><span data-stu-id="3254a-177">Execution is triggered when you apply a method that requires access to individual elements of the query result.</span></span> <span data-ttu-id="3254a-178">通常，使用返回单个值的标准查询运算符之一来强制立即执行。</span><span class="sxs-lookup"><span data-stu-id="3254a-178">Immediate execution often is forced by using one of the standard query operators that return single values.</span></span> <span data-ttu-id="3254a-179">例如， `Count` 、 `Max` `Average` 和 `First` 。</span><span class="sxs-lookup"><span data-stu-id="3254a-179">Examples are `Count`, `Max`, `Average`, and `First`.</span></span> <span data-ttu-id="3254a-180">这些标准查询运算符会在应用查询后立即执行查询，以便计算并返回单一实例结果。</span><span class="sxs-lookup"><span data-stu-id="3254a-180">These standard query operators execute the query as soon as they are applied in order to calculate and return a singleton result.</span></span> <span data-ttu-id="3254a-181">有关返回单个值的标准查询运算符的详细信息，请参阅 [聚合运算](aggregation-operations.md)、 [元素操作](element-operations.md)和 [限定符运算](quantifier-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="3254a-181">For more information about standard query operators that return single values, see [Aggregation Operations](aggregation-operations.md), [Element Operations](element-operations.md), and [Quantifier Operations](quantifier-operations.md).</span></span>  
  
 <span data-ttu-id="3254a-182">下面的查询返回整数数组中偶数的计数。</span><span class="sxs-lookup"><span data-stu-id="3254a-182">The following query returns a count of the even numbers in an array of integers.</span></span> <span data-ttu-id="3254a-183">查询定义不会保存， `numEvens` 这是一个简单的 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="3254a-183">The query definition is not saved, and `numEvens` is a simple `Integer`.</span></span>  
  
 [!code-vb[VbLINQFirstQuery#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#4)]  
  
 <span data-ttu-id="3254a-184">您可以通过使用方法获得相同的结果 `Aggregate` 。</span><span class="sxs-lookup"><span data-stu-id="3254a-184">You can achieve the same result by using the `Aggregate` method.</span></span>  
  
 [!code-vb[VbLINQFirstQuery#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#5)]  
  
 <span data-ttu-id="3254a-185">还可以通过 `ToList` `ToArray` 对查询调用或方法 (立即) 或查询变量 (延迟) ，来强制执行查询，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="3254a-185">You can also force execution of a query by calling the `ToList` or `ToArray` method on a query (immediate) or query variable (deferred), as shown in the following code.</span></span>  
  
 [!code-vb[VbLINQFirstQuery#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#6)]  
  
 <span data-ttu-id="3254a-186">在前面的示例中， `evensQuery3` 是一个查询变量，但 `evensList` 是一个列表， `evensArray` 是一个数组。</span><span class="sxs-lookup"><span data-stu-id="3254a-186">In the previous examples, `evensQuery3` is a query variable, but `evensList` is a list and `evensArray` is an array.</span></span>  
  
 <span data-ttu-id="3254a-187">`ToList` `ToArray` 如果希望立即执行查询并将结果缓存在单个集合对象中，则使用或强制立即执行将特别有用。</span><span class="sxs-lookup"><span data-stu-id="3254a-187">Using `ToList` or `ToArray` to force immediate execution is especially useful in scenarios in which you want to execute the query immediately and cache the results in a single collection object.</span></span> <span data-ttu-id="3254a-188">有关这些方法的详细信息，请参阅 [转换数据类型](converting-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="3254a-188">For more information about these methods, see [Converting Data Types](converting-data-types.md).</span></span>  
  
 <span data-ttu-id="3254a-189">您还可以使用 `IEnumerable` 方法（如方法）来执行查询 <xref:Microsoft.VisualBasic.Collection.System%23Collections%23IEnumerable%23GetEnumerator%2A> 。</span><span class="sxs-lookup"><span data-stu-id="3254a-189">You can also cause a query to be executed by using an `IEnumerable` method such as the <xref:Microsoft.VisualBasic.Collection.System%23Collections%23IEnumerable%23GetEnumerator%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3254a-190">请参阅</span><span class="sxs-lookup"><span data-stu-id="3254a-190">See also</span></span>

- [<span data-ttu-id="3254a-191">Visual Basic 中的 LINQ 入门</span><span class="sxs-lookup"><span data-stu-id="3254a-191">Getting Started with LINQ in Visual Basic</span></span>](getting-started-with-linq.md)
- [<span data-ttu-id="3254a-192">局部类型推理</span><span class="sxs-lookup"><span data-stu-id="3254a-192">Local Type Inference</span></span>](../../language-features/variables/local-type-inference.md)
- [<span data-ttu-id="3254a-193">标准查询运算符概述 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3254a-193">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="3254a-194">Visual Basic 中的 LINQ 简介</span><span class="sxs-lookup"><span data-stu-id="3254a-194">Introduction to LINQ in Visual Basic</span></span>](../../language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="3254a-195">LINQ</span><span class="sxs-lookup"><span data-stu-id="3254a-195">LINQ</span></span>](../../language-features/linq/index.md)
- [<span data-ttu-id="3254a-196">查询</span><span class="sxs-lookup"><span data-stu-id="3254a-196">Queries</span></span>](../../../language-reference/queries/index.md)
