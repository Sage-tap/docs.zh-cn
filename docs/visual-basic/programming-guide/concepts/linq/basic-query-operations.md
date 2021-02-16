---
description: '了解详细信息：基本查询操作 (Visual Basic) '
title: 基本查询操作
ms.date: 07/20/2015
helpviewer_keywords:
- data sources [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- ordering data [LINQ in Visual Basic]
- projections [LINQ in Visual Basic]
- LINQ [Visual Basic], query operations
- Order By clause [LINQ in Visual Basic]
- joining data [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], basic operations
- selecting data [LINQ in Visual Basic]
- Group By clause [LINQ in Visual Basic]
- grouping data [LINQ in Visual Basic]
- Select clause [LINQ in Visual Basic]
ms.assetid: 1146f6d0-fcb8-4f4d-8223-c9db52620d21
ms.openlocfilehash: 1f8fbda83c21fe9032415d96ff2d7e184083a839
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100428683"
---
# <a name="basic-query-operations-visual-basic"></a><span data-ttu-id="49702-103">基本查询操作 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="49702-103">Basic Query Operations (Visual Basic)</span></span>

<span data-ttu-id="49702-104">本主题简要介绍了如何在 Visual Basic 中 Language-Integrated 查询 (LINQ) 表达式，以及在查询中执行的一些典型操作。</span><span class="sxs-lookup"><span data-stu-id="49702-104">This topic provides a brief introduction to Language-Integrated Query (LINQ) expressions in Visual Basic, and to some of the typical kinds of operations that you perform in a query.</span></span> <span data-ttu-id="49702-105">有关详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="49702-105">For more information, see the following topics:</span></span>  
  
 [<span data-ttu-id="49702-106">Visual Basic 中的 LINQ 简介</span><span class="sxs-lookup"><span data-stu-id="49702-106">Introduction to LINQ in Visual Basic</span></span>](../../language-features/linq/introduction-to-linq.md)  
  
 [<span data-ttu-id="49702-107">查询</span><span class="sxs-lookup"><span data-stu-id="49702-107">Queries</span></span>](../../../language-reference/queries/index.md)  
  
 [<span data-ttu-id="49702-108">演练：用 Visual Basic 编写查询</span><span class="sxs-lookup"><span data-stu-id="49702-108">Walkthrough: Writing Queries in Visual Basic</span></span>](walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a><span data-ttu-id="49702-109">指定 (的数据源) </span><span class="sxs-lookup"><span data-stu-id="49702-109">Specifying the Data Source (From)</span></span>  

 <span data-ttu-id="49702-110">在 LINQ 查询中，第一步是指定要查询的数据源。</span><span class="sxs-lookup"><span data-stu-id="49702-110">In a LINQ query, the first step is to specify the data source that you want to query.</span></span> <span data-ttu-id="49702-111">因此， `From` 查询中的子句始终是第一个。</span><span class="sxs-lookup"><span data-stu-id="49702-111">Therefore, the `From` clause in a query always comes first.</span></span> <span data-ttu-id="49702-112">查询运算符根据源的类型选择并生成结果。</span><span class="sxs-lookup"><span data-stu-id="49702-112">Query operators select and shape the result based on the type of the source.</span></span>  
  
 [!code-vb[VbLINQBasicOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#1)]  
  
 <span data-ttu-id="49702-113">`From`子句指定数据源、 `customers` 和 *范围变量* `cust` 。</span><span class="sxs-lookup"><span data-stu-id="49702-113">The `From` clause specifies the data source, `customers`, and a *range variable*, `cust`.</span></span> <span data-ttu-id="49702-114">范围变量类似于循环迭代变量，但在查询表达式中，不会发生实际迭代。</span><span class="sxs-lookup"><span data-stu-id="49702-114">The range variable is like a loop iteration variable, except that in a query expression, no actual iteration occurs.</span></span> <span data-ttu-id="49702-115">当执行查询时，通常使用 `For Each` 循环，范围变量充当对中每个后续元素的引用 `customers` 。</span><span class="sxs-lookup"><span data-stu-id="49702-115">When the query is executed, often by using a `For Each` loop, the range variable serves as a reference to each successive element in `customers`.</span></span> <span data-ttu-id="49702-116">由于编译器可以推断 `cust` 的类型，因此无需显式指定它。</span><span class="sxs-lookup"><span data-stu-id="49702-116">Because the compiler can infer the type of `cust`, you do not have to specify it explicitly.</span></span> <span data-ttu-id="49702-117">有关用和编写的查询的示例，但没有显式类型化，请参阅 [查询操作中的类型关系 (Visual Basic) ](type-relationships-in-query-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="49702-117">For examples of queries written with and without explicit typing, see [Type Relationships in Query Operations (Visual Basic)](type-relationships-in-query-operations.md).</span></span>  
  
 <span data-ttu-id="49702-118">有关如何 `From` 在 Visual Basic 中使用子句的详细信息，请参阅 [from 子句](../../../language-reference/queries/from-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="49702-118">For more information about how to use the `From` clause in Visual Basic, see [From Clause](../../../language-reference/queries/from-clause.md).</span></span>  
  
## <a name="filtering-data-where"></a><span data-ttu-id="49702-119">筛选数据 (位置) </span><span class="sxs-lookup"><span data-stu-id="49702-119">Filtering Data (Where)</span></span>  

 <span data-ttu-id="49702-120">可能最常见的查询操作是以布尔表达式的形式应用筛选器。</span><span class="sxs-lookup"><span data-stu-id="49702-120">Probably the most common query operation is applying a filter in the form of a Boolean expression.</span></span> <span data-ttu-id="49702-121">然后，查询仅返回表达式为 true 的元素。</span><span class="sxs-lookup"><span data-stu-id="49702-121">The query then returns only those elements for which the expression is true.</span></span> <span data-ttu-id="49702-122">`Where`子句用于执行筛选。</span><span class="sxs-lookup"><span data-stu-id="49702-122">A `Where` clause is used to perform the filtering.</span></span> <span data-ttu-id="49702-123">筛选器指定数据源中要包括在结果序列中的元素。</span><span class="sxs-lookup"><span data-stu-id="49702-123">The filter specifies which elements in the data source to include in the resulting sequence.</span></span> <span data-ttu-id="49702-124">在下面的示例中，只包括具有伦敦地址的客户。</span><span class="sxs-lookup"><span data-stu-id="49702-124">In the following example, only those customers who have an address in London are included.</span></span>  
  
 [!code-vb[VbLINQBasicOps#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#2)]  
  
 <span data-ttu-id="49702-125">可以使用逻辑运算符（如 `And` 和） `Or` 在子句中合并筛选表达式 `Where` 。</span><span class="sxs-lookup"><span data-stu-id="49702-125">You can use logical operators such as `And` and `Or` to combine filter expressions in a `Where` clause.</span></span> <span data-ttu-id="49702-126">例如，若要仅返回来自伦敦并且其名称为 Devon 的客户，请使用以下代码：</span><span class="sxs-lookup"><span data-stu-id="49702-126">For example, to return only those customers who are from London and whose name is Devon, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"
```  
  
 <span data-ttu-id="49702-127">若要返回伦敦或巴黎的客户，请使用以下代码：</span><span class="sxs-lookup"><span data-stu-id="49702-127">To return customers from London or Paris, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"
```  
  
 <span data-ttu-id="49702-128">有关如何 `Where` 在 Visual Basic 中使用子句的详细信息，请参阅 [Where 子句](../../../language-reference/queries/where-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="49702-128">For more information about how to use the `Where` clause in Visual Basic, see [Where Clause](../../../language-reference/queries/where-clause.md).</span></span>  
  
## <a name="ordering-data-order-by"></a><span data-ttu-id="49702-129">按) 对数据进行排序 (</span><span class="sxs-lookup"><span data-stu-id="49702-129">Ordering Data (Order By)</span></span>  

 <span data-ttu-id="49702-130">将返回的数据按特定顺序排序通常是非常方便的。</span><span class="sxs-lookup"><span data-stu-id="49702-130">It often is convenient to sort returned data into a particular order.</span></span> <span data-ttu-id="49702-131">`Order By`子句将导致返回的序列中的元素按指定的一个或多个字段进行排序。</span><span class="sxs-lookup"><span data-stu-id="49702-131">The `Order By` clause will cause the elements in the returned sequence to be sorted on a specified field or fields.</span></span> <span data-ttu-id="49702-132">例如，下面的查询基于属性对结果进行排序 `Name` 。</span><span class="sxs-lookup"><span data-stu-id="49702-132">For example, the following query sorts the results based on the `Name` property.</span></span> <span data-ttu-id="49702-133">由于 `Name` 是一个字符串，因此返回的数据将按字母顺序从 a 到 Z 排序。</span><span class="sxs-lookup"><span data-stu-id="49702-133">Because `Name` is a string, the returned data will be sorted alphabetically, from A to Z.</span></span>  
  
 [!code-vb[VbLINQBasicOps#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#3)]  
  
 <span data-ttu-id="49702-134">要对结果进行从 Z 到 A 的逆序排序，请使用 `Order By...Descending` 子句。</span><span class="sxs-lookup"><span data-stu-id="49702-134">To order the results in reverse order, from Z to A, use the `Order By...Descending` clause.</span></span> <span data-ttu-id="49702-135">`Ascending`如果 `Ascending` 和均未指定，则默认值为 `Descending` 。</span><span class="sxs-lookup"><span data-stu-id="49702-135">The default is `Ascending` when neither `Ascending` nor `Descending` is specified.</span></span>  
  
 <span data-ttu-id="49702-136">有关如何 `Order By` 在 Visual Basic 中使用子句的详细信息，请参阅 [Order By 子句](../../../language-reference/queries/order-by-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="49702-136">For more information about how to use the `Order By` clause in Visual Basic, see [Order By Clause](../../../language-reference/queries/order-by-clause.md).</span></span>  
  
## <a name="selecting-data-select"></a><span data-ttu-id="49702-137">选择数据 (选择) </span><span class="sxs-lookup"><span data-stu-id="49702-137">Selecting Data (Select)</span></span>  

 <span data-ttu-id="49702-138">`Select`子句指定返回元素的形式和内容。</span><span class="sxs-lookup"><span data-stu-id="49702-138">The `Select` clause specifies the form and content of returned elements.</span></span> <span data-ttu-id="49702-139">例如，您可以指定您的结果是包含完整的 `Customer` 对象、只包含一个 `Customer` 属性、一个属性子集、不同数据源的属性组合还是基于计算的某些新的结果类型。</span><span class="sxs-lookup"><span data-stu-id="49702-139">For example, you can specify whether your results will consist of complete `Customer` objects, just one `Customer` property, a subset of properties, a combination of properties from various data sources, or some new result type based on a computation.</span></span> <span data-ttu-id="49702-140">当 `Select` 子句生成除源元素副本以外的内容时，该操作称为投影。</span><span class="sxs-lookup"><span data-stu-id="49702-140">When the `Select` clause produces something other than a copy of the source element, the operation is called a *projection*.</span></span>  
  
 <span data-ttu-id="49702-141">若要检索由完整的对象组成的集合 `Customer` ，请选择范围变量本身：</span><span class="sxs-lookup"><span data-stu-id="49702-141">To retrieve a collection that consists of complete `Customer` objects, select the range variable itself:</span></span>  
  
 [!code-vb[VbLINQBasicOps#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#4)]  
  
 <span data-ttu-id="49702-142">如果 `Customer` 实例是具有多个字段的大型对象，而您要检索的只是该名称，则可以选择 `cust.Name` ，如以下示例中所示。</span><span class="sxs-lookup"><span data-stu-id="49702-142">If a `Customer` instance is a large object that has many fields, and all that you want to retrieve is the name, you can select `cust.Name`, as shown in the following example.</span></span> <span data-ttu-id="49702-143">局部类型推理可识别这会将结果类型从对象的集合更改 `Customer` 为字符串的集合。</span><span class="sxs-lookup"><span data-stu-id="49702-143">Local type inference recognizes that this changes the result type from a collection of `Customer` objects to a collection of strings.</span></span>  
  
 [!code-vb[VbLINQBasicOps#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#5)]  
  
 <span data-ttu-id="49702-144">若要从数据源中选择多个字段，您有两种选择：</span><span class="sxs-lookup"><span data-stu-id="49702-144">To select multiple fields from the data source, you have two choices:</span></span>  
  
- <span data-ttu-id="49702-145">在 `Select` 子句中，指定要包含在结果中的字段。</span><span class="sxs-lookup"><span data-stu-id="49702-145">In the `Select` clause, specify the fields you want to include in the result.</span></span> <span data-ttu-id="49702-146">编译器将定义一个匿名类型，该类型将这些字段作为其属性。</span><span class="sxs-lookup"><span data-stu-id="49702-146">The compiler will define an anonymous type that has those fields as its properties.</span></span> <span data-ttu-id="49702-147">有关详细信息，请参阅[匿名类型](../../language-features/objects-and-classes/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="49702-147">For more information, see [Anonymous Types](../../language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
     <span data-ttu-id="49702-148">由于以下示例中返回的元素是匿名类型的实例，因此不能在代码中的其他位置以名称引用该类型。</span><span class="sxs-lookup"><span data-stu-id="49702-148">Because the returned elements in the following example are instances of an anonymous type, you cannot refer to the type by name elsewhere in your code.</span></span> <span data-ttu-id="49702-149">该类型的编译器指定名称包含在正常 Visual Basic 代码中无效的字符。</span><span class="sxs-lookup"><span data-stu-id="49702-149">The compiler-designated name for the type contains characters that are not valid in normal Visual Basic code.</span></span> <span data-ttu-id="49702-150">在下面的示例中，中查询返回的集合中的元素 `londonCusts4` 是匿名类型的实例</span><span class="sxs-lookup"><span data-stu-id="49702-150">In the following example, the elements in the collection that is returned by the query in `londonCusts4` are instances of an anonymous type</span></span>  
  
     [!code-vb[VbLINQBasicOps#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#6)]  
  
     <span data-ttu-id="49702-151">- 或 -</span><span class="sxs-lookup"><span data-stu-id="49702-151">-or-</span></span>  
  
- <span data-ttu-id="49702-152">定义包含要包含在结果中的特定字段的命名类型，并在子句中创建和初始化该类型的实例 `Select` 。</span><span class="sxs-lookup"><span data-stu-id="49702-152">Define a named type that contains the particular fields that you want to include in the result, and create and initialize instances of the type in the `Select` clause.</span></span> <span data-ttu-id="49702-153">仅在以下情况下使用此选项：必须在返回的集合之外使用各个结果，或者必须在方法调用中将它们作为参数传递。</span><span class="sxs-lookup"><span data-stu-id="49702-153">Use this option only if you have to use individual results outside the collection in which they are returned, or if you have to pass them as parameters in method calls.</span></span> <span data-ttu-id="49702-154">`londonCusts5`以下示例中的类型为 NamePhone) 的 IEnumerable (。</span><span class="sxs-lookup"><span data-stu-id="49702-154">The type of `londonCusts5` in the following example is IEnumerable(Of NamePhone).</span></span>  
  
     [!code-vb[VbLINQBasicOps#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#7)]  
  
     [!code-vb[VbLINQBasicOps#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#8)]  
  
 <span data-ttu-id="49702-155">有关如何 `Select` 在 Visual Basic 中使用子句的详细信息，请参阅 [Select 子句](../../../language-reference/queries/select-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="49702-155">For more information about how to use the `Select` clause in Visual Basic, see [Select Clause](../../../language-reference/queries/select-clause.md).</span></span>  
  
## <a name="joining-data-join-and-group-join"></a><span data-ttu-id="49702-156">联接数据 (联接和分组联接) </span><span class="sxs-lookup"><span data-stu-id="49702-156">Joining Data (Join and Group Join)</span></span>  

 <span data-ttu-id="49702-157">可以通过多种方式在子句中组合多个数据源 `From` 。</span><span class="sxs-lookup"><span data-stu-id="49702-157">You can combine more than one data source in the `From` clause in several ways.</span></span> <span data-ttu-id="49702-158">例如，以下代码使用两个数据源，并在结果中隐式组合这两个数据源的属性。</span><span class="sxs-lookup"><span data-stu-id="49702-158">For example, the following code uses two data sources and implicitly combines properties from both of them in the result.</span></span> <span data-ttu-id="49702-159">查询选择姓氏以元音开头的学生。</span><span class="sxs-lookup"><span data-stu-id="49702-159">The query selects students whose last names start with a vowel.</span></span>  
  
 [!code-vb[VbLINQBasicOps#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#9)]  
  
> [!NOTE]
> <span data-ttu-id="49702-160">您可以使用在 [如何：创建项列表](how-to-create-a-list-of-items.md)中创建的学生列表运行此代码。</span><span class="sxs-lookup"><span data-stu-id="49702-160">You can run this code with the list of students created in [How to: Create a List of Items](how-to-create-a-list-of-items.md).</span></span>  
  
 <span data-ttu-id="49702-161">`Join`关键字等效于 `INNER JOIN` SQL 中的。</span><span class="sxs-lookup"><span data-stu-id="49702-161">The `Join` keyword is equivalent to an `INNER JOIN` in SQL.</span></span> <span data-ttu-id="49702-162">它基于两个集合中的元素之间的匹配键值合并两个集合。</span><span class="sxs-lookup"><span data-stu-id="49702-162">It combines two collections based on matching key values between elements in the two collections.</span></span> <span data-ttu-id="49702-163">查询返回所有或部分具有匹配键值的集合元素。</span><span class="sxs-lookup"><span data-stu-id="49702-163">The query returns all or part of the collection elements that have matching key values.</span></span> <span data-ttu-id="49702-164">例如，以下代码将复制上一个隐式联接的操作。</span><span class="sxs-lookup"><span data-stu-id="49702-164">For example, the following code duplicates the action of the previous implicit join.</span></span>  
  
 [!code-vb[VbLINQBasicOps#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#10)]  
  
 <span data-ttu-id="49702-165">`Group Join` 将集合组合为单个层次结构集合，就像 `LEFT JOIN` SQL 中的一样。</span><span class="sxs-lookup"><span data-stu-id="49702-165">`Group Join` combines collections into a single hierarchical collection, just like a `LEFT JOIN` in SQL.</span></span> <span data-ttu-id="49702-166">有关详细信息，请参阅 [Join 子句](../../../language-reference/queries/join-clause.md) 和 [Group Join 子句](../../../language-reference/queries/group-join-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="49702-166">For more information, see [Join Clause](../../../language-reference/queries/join-clause.md) and [Group Join Clause](../../../language-reference/queries/group-join-clause.md).</span></span>  
  
## <a name="grouping-data-group-by"></a><span data-ttu-id="49702-167">按) 对数据分组 (分组</span><span class="sxs-lookup"><span data-stu-id="49702-167">Grouping Data (Group By)</span></span>  

 <span data-ttu-id="49702-168">您可以添加一个 `Group By` 子句，以便根据元素的一个或多个字段对查询结果中的元素进行分组。</span><span class="sxs-lookup"><span data-stu-id="49702-168">You can add a `Group By` clause to group the elements in a query result according to one or more fields of the elements.</span></span> <span data-ttu-id="49702-169">例如，下面的代码按课程年份对学生进行分组。</span><span class="sxs-lookup"><span data-stu-id="49702-169">For example, the following code groups students by class year.</span></span>  
  
 [!code-vb[VbLINQBasicOps#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#11)]  
  
 <span data-ttu-id="49702-170">如果使用在 [如何：创建项列表](how-to-create-a-list-of-items.md)中创建的学生列表运行此代码，则语句的输出 `For Each` 为：</span><span class="sxs-lookup"><span data-stu-id="49702-170">If you run this code using the list of students created in [How to: Create a List of Items](how-to-create-a-list-of-items.md), the output from the `For Each` statement is:</span></span>  
  
 <span data-ttu-id="49702-171">Year：初级</span><span class="sxs-lookup"><span data-stu-id="49702-171">Year: Junior</span></span>  
  
 <span data-ttu-id="49702-172">Tucker、Michael</span><span class="sxs-lookup"><span data-stu-id="49702-172">Tucker, Michael</span></span>  
  
 <span data-ttu-id="49702-173">Garcia、Hugo</span><span class="sxs-lookup"><span data-stu-id="49702-173">Garcia, Hugo</span></span>  
  
 <span data-ttu-id="49702-174">Garcia、Debra</span><span class="sxs-lookup"><span data-stu-id="49702-174">Garcia, Debra</span></span>  
  
 <span data-ttu-id="49702-175">Tucker、Lance</span><span class="sxs-lookup"><span data-stu-id="49702-175">Tucker, Lance</span></span>  
  
 <span data-ttu-id="49702-176">Year：高级</span><span class="sxs-lookup"><span data-stu-id="49702-176">Year: Senior</span></span>  
  
 <span data-ttu-id="49702-177">Omelchenko, Svetlana</span><span class="sxs-lookup"><span data-stu-id="49702-177">Omelchenko, Svetlana</span></span>  
  
 <span data-ttu-id="49702-178">Osada、Michiko</span><span class="sxs-lookup"><span data-stu-id="49702-178">Osada, Michiko</span></span>  
  
 <span data-ttu-id="49702-179">Fakhouri, Fadi</span><span class="sxs-lookup"><span data-stu-id="49702-179">Fakhouri, Fadi</span></span>  
  
 <span data-ttu-id="49702-180">Feng、冯汉英 (</span><span class="sxs-lookup"><span data-stu-id="49702-180">Feng, Hanying</span></span>  
  
 <span data-ttu-id="49702-181">Adams，Terry</span><span class="sxs-lookup"><span data-stu-id="49702-181">Adams, Terry</span></span>  
  
 <span data-ttu-id="49702-182">Year： Freshman</span><span class="sxs-lookup"><span data-stu-id="49702-182">Year: Freshman</span></span>  
  
 <span data-ttu-id="49702-183">Mortensen, Sven</span><span class="sxs-lookup"><span data-stu-id="49702-183">Mortensen, Sven</span></span>  
  
 <span data-ttu-id="49702-184">Garcia、Cesar</span><span class="sxs-lookup"><span data-stu-id="49702-184">Garcia, Cesar</span></span>  
  
 <span data-ttu-id="49702-185">以下代码中显示的变体对类年进行排序，然后按姓氏对每年内的学生进行排序。</span><span class="sxs-lookup"><span data-stu-id="49702-185">The variation shown in the following code orders the class years, and then orders the students within each year by last name.</span></span>  
  
 [!code-vb[VbLINQBasicOps#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#12)]  
  
 <span data-ttu-id="49702-186">有关的详细信息 `Group By` ，请参阅 [Group by 子句](../../../language-reference/queries/group-by-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="49702-186">For more information about `Group By`, see [Group By Clause](../../../language-reference/queries/group-by-clause.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49702-187">请参阅</span><span class="sxs-lookup"><span data-stu-id="49702-187">See also</span></span>

- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="49702-188">Visual Basic 中的 LINQ 入门</span><span class="sxs-lookup"><span data-stu-id="49702-188">Getting Started with LINQ in Visual Basic</span></span>](getting-started-with-linq.md)
- [<span data-ttu-id="49702-189">查询</span><span class="sxs-lookup"><span data-stu-id="49702-189">Queries</span></span>](../../../language-reference/queries/index.md)
- [<span data-ttu-id="49702-190">标准查询运算符概述 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="49702-190">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="49702-191">LINQ</span><span class="sxs-lookup"><span data-stu-id="49702-191">LINQ</span></span>](../../language-features/linq/index.md)
