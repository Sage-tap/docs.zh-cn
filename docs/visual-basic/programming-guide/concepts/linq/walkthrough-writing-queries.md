---
description: 了解详细信息：演练：在 Visual Basic 中编写查询
title: 编写查询
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ [Visual Basic], walkthroughs
- LINQ [Visual Basic], writing queries
- writing LINQ queries [Visual Basic]
ms.assetid: f0045808-b9fe-4d31-88d1-473d9957211e
ms.openlocfilehash: 55a1b3382d587b7982b79448334c4688895fa6e6
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466804"
---
# <a name="walkthrough-writing-queries-in-visual-basic"></a><span data-ttu-id="5110b-103">演练：用 Visual Basic 编写查询</span><span class="sxs-lookup"><span data-stu-id="5110b-103">Walkthrough: Writing Queries in Visual Basic</span></span>

<span data-ttu-id="5110b-104">本演练演示如何使用 Visual Basic 语言功能编写 Language-Integrated Query (LINQ) 查询表达式。</span><span class="sxs-lookup"><span data-stu-id="5110b-104">This walkthrough demonstrates how you can use Visual Basic language features to write Language-Integrated Query (LINQ) query expressions.</span></span> <span data-ttu-id="5110b-105">本演练演示如何对学生对象列表创建查询，如何运行查询，以及如何修改查询。</span><span class="sxs-lookup"><span data-stu-id="5110b-105">The walkthrough demonstrates how to create queries on a list of Student objects, how to run the queries, and how to modify them.</span></span> <span data-ttu-id="5110b-106">查询包含多个功能，包括对象初始值设定项、本地类型推理和匿名类型。</span><span class="sxs-lookup"><span data-stu-id="5110b-106">The queries incorporate several features including object initializers, local type inference, and anonymous types.</span></span>

<span data-ttu-id="5110b-107">完成本演练后，你将准备好进入你感兴趣的特定 LINQ 提供程序的示例和文档。</span><span class="sxs-lookup"><span data-stu-id="5110b-107">After completing this walkthrough, you will be ready to move on to the samples and documentation for the specific LINQ provider you are interested in.</span></span> <span data-ttu-id="5110b-108">LINQ 提供程序包括 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 、LINQ to DataSet 和 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="5110b-108">LINQ providers include [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], LINQ to DataSet, and [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>

## <a name="create-a-project"></a><span data-ttu-id="5110b-109">创建项目</span><span class="sxs-lookup"><span data-stu-id="5110b-109">Create a Project</span></span>

### <a name="to-create-a-console-application-project"></a><span data-ttu-id="5110b-110">创建控制台应用程序项目</span><span class="sxs-lookup"><span data-stu-id="5110b-110">To create a console application project</span></span>

1. <span data-ttu-id="5110b-111">启动 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="5110b-111">Start Visual Studio.</span></span>

2. <span data-ttu-id="5110b-112">在 **“文件”** 菜单上，指向 **“新建”** ，然后单击 **“项目”** 。</span><span class="sxs-lookup"><span data-stu-id="5110b-112">On the **File** menu, point to **New**, and then click **Project**.</span></span>

3. <span data-ttu-id="5110b-113">在 " **已安装的模板** " 列表中，单击 **Visual Basic**。</span><span class="sxs-lookup"><span data-stu-id="5110b-113">In the **Installed Templates** list, click **Visual Basic**.</span></span>

4. <span data-ttu-id="5110b-114">在项目类型列表中，单击 " **控制台应用程序**"。</span><span class="sxs-lookup"><span data-stu-id="5110b-114">In the list of project types, click **Console Application**.</span></span> <span data-ttu-id="5110b-115">在 " **名称** " 框中，键入项目的名称，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="5110b-115">In the **Name** box, type a name for the project, and then click **OK**.</span></span>

    <span data-ttu-id="5110b-116">创建一个项目。</span><span class="sxs-lookup"><span data-stu-id="5110b-116">A project is created.</span></span> <span data-ttu-id="5110b-117">默认情况下，它包含对 System.Core.dll 的引用。</span><span class="sxs-lookup"><span data-stu-id="5110b-117">By default, it contains a reference to System.Core.dll.</span></span> <span data-ttu-id="5110b-118">此外，"引用" 页上的 "[项目设计器" (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)的 "已 **导入命名空间**" 列表包括 <xref:System.Linq?displayProperty=nameWithType> 命名空间。</span><span class="sxs-lookup"><span data-stu-id="5110b-118">Also, the **Imported namespaces** list on the [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic) includes the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>

5. <span data-ttu-id="5110b-119">在 "编译" 页上的 " [项目设计器" (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)上，确保 " **选项推断** " 设置为 **"开"**。</span><span class="sxs-lookup"><span data-stu-id="5110b-119">On the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), ensure that **Option infer** is set to **On**.</span></span>

## <a name="add-an-in-memory-data-source"></a><span data-ttu-id="5110b-120">添加 In-Memory 数据源</span><span class="sxs-lookup"><span data-stu-id="5110b-120">Add an In-Memory Data Source</span></span>

<span data-ttu-id="5110b-121">此演练中的查询的数据源是对象的列表 `Student` 。</span><span class="sxs-lookup"><span data-stu-id="5110b-121">The data source for the queries in this walkthrough is a list of `Student` objects.</span></span> <span data-ttu-id="5110b-122">每个 `Student` 对象都包含学生正文中的名字、姓氏、课程年份和学术排名。</span><span class="sxs-lookup"><span data-stu-id="5110b-122">Each `Student` object contains a first name, a last name, a class year, and an academic rank in the student body.</span></span>

### <a name="to-add-the-data-source"></a><span data-ttu-id="5110b-123">添加数据源</span><span class="sxs-lookup"><span data-stu-id="5110b-123">To add the data source</span></span>

- <span data-ttu-id="5110b-124">定义 `Student` 类，并创建类的实例的列表。</span><span class="sxs-lookup"><span data-stu-id="5110b-124">Define a `Student` class, and create a list of instances of the class.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="5110b-125">`Student`[如何：创建项列表](how-to-create-a-list-of-items.md)中提供了定义类并创建在演练示例中使用的列表所需的代码。</span><span class="sxs-lookup"><span data-stu-id="5110b-125">The code needed to define the `Student` class and create the list used in the walkthrough examples is provided in [How to: Create a List of Items](how-to-create-a-list-of-items.md).</span></span> <span data-ttu-id="5110b-126">可以将其复制到项目中，并将其粘贴到你的项目中。</span><span class="sxs-lookup"><span data-stu-id="5110b-126">You can copy it from there and paste it into your project.</span></span> <span data-ttu-id="5110b-127">新代码将替换在创建项目时显示的代码。</span><span class="sxs-lookup"><span data-stu-id="5110b-127">The new code replaces the code that appeared when you created the project.</span></span>

### <a name="to-add-a-new-student-to-the-students-list"></a><span data-ttu-id="5110b-128">向学生列表中添加新的学生</span><span class="sxs-lookup"><span data-stu-id="5110b-128">To add a new student to the students list</span></span>

- <span data-ttu-id="5110b-129">按照方法中的模式 `getStudents` 将类的另一个实例添加 `Student` 到列表。</span><span class="sxs-lookup"><span data-stu-id="5110b-129">Follow the pattern in the `getStudents` method to add another instance of the `Student` class to the list.</span></span> <span data-ttu-id="5110b-130">添加学生将向你介绍对象初始值设定项。</span><span class="sxs-lookup"><span data-stu-id="5110b-130">Adding the student will introduce you to object initializers.</span></span> <span data-ttu-id="5110b-131">有关详细信息，请参阅 [对象初始值设定项：命名类型和匿名类型](../../language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="5110b-131">For more information, see [Object Initializers: Named and Anonymous Types](../../language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).</span></span>

## <a name="create-a-query"></a><span data-ttu-id="5110b-132">创建查询</span><span class="sxs-lookup"><span data-stu-id="5110b-132">Create a Query</span></span>

<span data-ttu-id="5110b-133">执行时，此部分中添加的查询将生成一个学生列表，其中的学生排名将其放在前十位。</span><span class="sxs-lookup"><span data-stu-id="5110b-133">When executed, the query added in this section produces a list of the students whose academic rank puts them in the top ten.</span></span> <span data-ttu-id="5110b-134">由于查询 `Student` 每次都选择完整的对象，因此查询结果的类型为 `IEnumerable(Of Student)` 。</span><span class="sxs-lookup"><span data-stu-id="5110b-134">Because the query selects the complete `Student` object each time, the type of the query result is `IEnumerable(Of Student)`.</span></span> <span data-ttu-id="5110b-135">但是，查询的类型通常不在查询定义中指定。</span><span class="sxs-lookup"><span data-stu-id="5110b-135">However, the type of the query typically is not specified in query definitions.</span></span> <span data-ttu-id="5110b-136">相反，编译器将使用局部类型推理来确定类型。</span><span class="sxs-lookup"><span data-stu-id="5110b-136">Instead, the compiler uses local type inference to determine the type.</span></span> <span data-ttu-id="5110b-137">有关详细信息，请参阅 [局部类型推理](../../language-features/variables/local-type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="5110b-137">For more information, see [Local Type Inference](../../language-features/variables/local-type-inference.md).</span></span> <span data-ttu-id="5110b-138">查询的范围变量用作对 `currentStudent` 源中每个实例的引用 `Student` `students` ，提供对中每个对象的属性的访问 `students` 。</span><span class="sxs-lookup"><span data-stu-id="5110b-138">The query's range variable, `currentStudent`, serves as a reference to each `Student` instance in the source, `students`, providing access to the properties of each object in `students`.</span></span>

### <a name="to-create-a-simple-query"></a><span data-ttu-id="5110b-139">创建简单查询</span><span class="sxs-lookup"><span data-stu-id="5110b-139">To create a simple query</span></span>

1. <span data-ttu-id="5110b-140">查找 `Main` 项目的方法中标记为以下内容的位置：</span><span class="sxs-lookup"><span data-stu-id="5110b-140">Find the place in the `Main` method of the project that is marked as follows:</span></span>

    [!code-vb[VbLINQWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#1)]

    <span data-ttu-id="5110b-141">复制以下代码并将其粘贴到中。</span><span class="sxs-lookup"><span data-stu-id="5110b-141">Copy the following code and paste it in.</span></span>

    [!code-vb[VbLINQWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#2)]

2. <span data-ttu-id="5110b-142">将鼠标指针停留 `studentQuery` 在代码中，以验证编译器分配的类型是否为 `IEnumerable(Of Student)` 。</span><span class="sxs-lookup"><span data-stu-id="5110b-142">Rest the mouse pointer over `studentQuery` in your code to verify that the compiler-assigned type is `IEnumerable(Of Student)`.</span></span>

## <a name="run-the-query"></a><span data-ttu-id="5110b-143">运行查询</span><span class="sxs-lookup"><span data-stu-id="5110b-143">Run the Query</span></span>

<span data-ttu-id="5110b-144">变量 `studentQuery` 包含查询的定义，而不是运行查询的结果。</span><span class="sxs-lookup"><span data-stu-id="5110b-144">The variable `studentQuery` contains the definition of the query, not the results of running the query.</span></span> <span data-ttu-id="5110b-145">用于运行查询的一种典型机制是 `For Each` 循环。</span><span class="sxs-lookup"><span data-stu-id="5110b-145">A typical mechanism for running a query is a `For Each` loop.</span></span> <span data-ttu-id="5110b-146">返回序列中的每个元素都通过循环迭代变量来访问。</span><span class="sxs-lookup"><span data-stu-id="5110b-146">Each element in the returned sequence is accessed through the loop iteration variable.</span></span> <span data-ttu-id="5110b-147">有关查询执行的详细信息，请参阅 [编写第一个 LINQ 查询](writing-your-first-linq-query.md)。</span><span class="sxs-lookup"><span data-stu-id="5110b-147">For more information about query execution, see [Writing Your First LINQ Query](writing-your-first-linq-query.md).</span></span>

### <a name="to-run-the-query"></a><span data-ttu-id="5110b-148">运行查询</span><span class="sxs-lookup"><span data-stu-id="5110b-148">To run the query</span></span>

1. <span data-ttu-id="5110b-149">`For Each`在项目中的查询下添加以下循环。</span><span class="sxs-lookup"><span data-stu-id="5110b-149">Add the following `For Each` loop below the query in your project.</span></span>

    [!code-vb[VbLINQWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#3)]

2. <span data-ttu-id="5110b-150">将鼠标指针停留在循环控制变量上 `studentRecord` ，以查看其数据类型。</span><span class="sxs-lookup"><span data-stu-id="5110b-150">Rest the mouse pointer over the loop control variable `studentRecord` to see its data type.</span></span> <span data-ttu-id="5110b-151">的类型 `studentRecord` 被推断为 `Student` ，因为 `studentQuery` 返回实例的集合 `Student` 。</span><span class="sxs-lookup"><span data-stu-id="5110b-151">The type of `studentRecord` is inferred to be `Student`, because `studentQuery` returns a collection of `Student` instances.</span></span>

3. <span data-ttu-id="5110b-152">按 CTRL + F5 生成并运行应用程序。</span><span class="sxs-lookup"><span data-stu-id="5110b-152">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="5110b-153">请注意控制台窗口中的结果。</span><span class="sxs-lookup"><span data-stu-id="5110b-153">Note the results in the console window.</span></span>

## <a name="modify-the-query"></a><span data-ttu-id="5110b-154">修改查询</span><span class="sxs-lookup"><span data-stu-id="5110b-154">Modify the Query</span></span>

<span data-ttu-id="5110b-155">如果查询结果按指定顺序进行扫描，则会更容易。</span><span class="sxs-lookup"><span data-stu-id="5110b-155">It is easier to scan query results if they are in a specified order.</span></span> <span data-ttu-id="5110b-156">您可以基于任何可用字段对返回的序列进行排序。</span><span class="sxs-lookup"><span data-stu-id="5110b-156">You can sort the returned sequence based on any available field.</span></span>

### <a name="to-order-the-results"></a><span data-ttu-id="5110b-157">对结果进行排序</span><span class="sxs-lookup"><span data-stu-id="5110b-157">To order the results</span></span>

1. <span data-ttu-id="5110b-158">在 `Order By` `Where` 语句和查询的语句之间添加以下子句 `Select` 。</span><span class="sxs-lookup"><span data-stu-id="5110b-158">Add the following `Order By` clause between the `Where` statement and the `Select` statement of the query.</span></span> <span data-ttu-id="5110b-159">`Order By`子句根据每个学生的姓氏从 A 到 Z 的顺序对结果进行排序。</span><span class="sxs-lookup"><span data-stu-id="5110b-159">The `Order By` clause will order the results alphabetically from A to Z, according to the last name of each student.</span></span>

    ```vb
    Order By currentStudent.Last Ascending
    ```

2. <span data-ttu-id="5110b-160">若要按姓氏再按名字排序，请将这两个字段添加到查询中：</span><span class="sxs-lookup"><span data-stu-id="5110b-160">To order by last name and then first name, add both fields to the query:</span></span>

    ```vb
    Order By currentStudent.Last Ascending, currentStudent.First Ascending
    ```

    <span data-ttu-id="5110b-161">您还可以指定 `Descending` 从 Z 到 A 的顺序。</span><span class="sxs-lookup"><span data-stu-id="5110b-161">You can also specify `Descending` to order from Z to A.</span></span>

3. <span data-ttu-id="5110b-162">按 CTRL + F5 生成并运行应用程序。</span><span class="sxs-lookup"><span data-stu-id="5110b-162">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="5110b-163">请注意控制台窗口中的结果。</span><span class="sxs-lookup"><span data-stu-id="5110b-163">Note the results in the console window.</span></span>

### <a name="to-introduce-a-local-identifier"></a><span data-ttu-id="5110b-164">引入本地标识符</span><span class="sxs-lookup"><span data-stu-id="5110b-164">To introduce a local identifier</span></span>

1. <span data-ttu-id="5110b-165">添加此部分中的代码，以在查询表达式中引入本地标识符。</span><span class="sxs-lookup"><span data-stu-id="5110b-165">Add the code in this section to introduce a local identifier in the query expression.</span></span> <span data-ttu-id="5110b-166">本地标识符将保存中间结果。</span><span class="sxs-lookup"><span data-stu-id="5110b-166">The local identifier will hold an intermediate result.</span></span> <span data-ttu-id="5110b-167">在下面的示例中， `name` 是一个标识符，该标识符保存学生的名字和姓氏的连接。</span><span class="sxs-lookup"><span data-stu-id="5110b-167">In the following example, `name` is an identifier that holds a concatenation of the student's first and last names.</span></span> <span data-ttu-id="5110b-168">本地标识符可用于方便起见，也可通过存储表达式的结果来提高性能，此表达式的计算结果将为多次。</span><span class="sxs-lookup"><span data-stu-id="5110b-168">A local identifier can be used for convenience, or it can enhance performance by storing the results of an expression that would otherwise be calculated multiple times.</span></span>

    [!code-vb[VbLINQWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#4)]

2. <span data-ttu-id="5110b-169">按 CTRL + F5 生成并运行应用程序。</span><span class="sxs-lookup"><span data-stu-id="5110b-169">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="5110b-170">请注意控制台窗口中的结果。</span><span class="sxs-lookup"><span data-stu-id="5110b-170">Note the results in the console window.</span></span>

### <a name="to-project-one-field-in-the-select-clause"></a><span data-ttu-id="5110b-171">在 Select 子句中投影一个字段</span><span class="sxs-lookup"><span data-stu-id="5110b-171">To project one field in the Select clause</span></span>

1. <span data-ttu-id="5110b-172">添加 `For Each` 此部分中的查询和循环，以创建一个查询，该查询将生成一个其元素不同于源中的元素的序列。</span><span class="sxs-lookup"><span data-stu-id="5110b-172">Add the query and `For Each` loop from this section to create a query that produces a sequence whose elements differ from the elements in the source.</span></span> <span data-ttu-id="5110b-173">在下面的示例中，源是对象的集合 `Student` ，但只返回每个对象的一个成员：姓氏为 Garcia 的学生名字。</span><span class="sxs-lookup"><span data-stu-id="5110b-173">In the following example, the source is a collection of `Student` objects, but only one member of each object is returned: the first name of students whose last name is Garcia.</span></span> <span data-ttu-id="5110b-174">由于 `currentStudent.First` 是一个字符串，返回的序列的数据类型 `studentQuery3` 是 `IEnumerable(Of String)` 一个字符串序列。</span><span class="sxs-lookup"><span data-stu-id="5110b-174">Because `currentStudent.First` is a string, the data type of the sequence returned by `studentQuery3` is `IEnumerable(Of String)`, a sequence of strings.</span></span> <span data-ttu-id="5110b-175">如前面的示例所示，的数据类型的分配 `studentQuery3` 留给编译器通过使用局部类型推理来确定。</span><span class="sxs-lookup"><span data-stu-id="5110b-175">As in earlier examples, the assignment of a data type for `studentQuery3` is left for the compiler to determine by using local type inference.</span></span>

    [!code-vb[VbLINQWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#5)]

2. <span data-ttu-id="5110b-176">将鼠标指针停留 `studentQuery3` 在代码中，以验证分配的类型是否为 `IEnumerable(Of String)` 。</span><span class="sxs-lookup"><span data-stu-id="5110b-176">Rest the mouse pointer over `studentQuery3` in your code to verify that the assigned type is `IEnumerable(Of String)`.</span></span>

3. <span data-ttu-id="5110b-177">按 CTRL + F5 生成并运行应用程序。</span><span class="sxs-lookup"><span data-stu-id="5110b-177">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="5110b-178">请注意控制台窗口中的结果。</span><span class="sxs-lookup"><span data-stu-id="5110b-178">Note the results in the console window.</span></span>

### <a name="to-create-an-anonymous-type-in-the-select-clause"></a><span data-ttu-id="5110b-179">在 Select 子句中创建匿名类型</span><span class="sxs-lookup"><span data-stu-id="5110b-179">To create an anonymous type in the Select clause</span></span>

1. <span data-ttu-id="5110b-180">添加此部分中的代码，以了解如何在查询中使用匿名类型。</span><span class="sxs-lookup"><span data-stu-id="5110b-180">Add the code from this section to see how anonymous types are used in queries.</span></span> <span data-ttu-id="5110b-181">如果要从数据源返回多个字段，而不是 (前面 `currentStudent` 的示例中的记录) 或 (`First` 前面部分) 中的单个字段）返回多个字段，则可以在查询中使用这些字段。</span><span class="sxs-lookup"><span data-stu-id="5110b-181">You use them in queries when you want to return several fields from the data source rather than complete records (`currentStudent` records in previous examples) or single fields (`First` in the preceding section).</span></span> <span data-ttu-id="5110b-182">您可以在子句中指定字段，而不是定义一个新的命名类型（其中包含您想要包括在结果中的字段），而 `Select` 编译器会创建一个匿名类型，并将这些字段作为其属性。</span><span class="sxs-lookup"><span data-stu-id="5110b-182">Instead of defining a new named type that contains the fields you want to include in the result, you specify the fields in the `Select` clause and the compiler creates an anonymous type with those fields as its properties.</span></span> <span data-ttu-id="5110b-183">有关详细信息，请参阅[匿名类型](../../language-features/objects-and-classes/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="5110b-183">For more information, see [Anonymous Types](../../language-features/objects-and-classes/anonymous-types.md).</span></span>

    <span data-ttu-id="5110b-184">下面的示例创建一个查询，该查询返回学术排名介于1到10之间的发言的名称和排名，按学术排名排序。</span><span class="sxs-lookup"><span data-stu-id="5110b-184">The following example creates a query that returns the name and rank of seniors whose academic rank is between 1 and 10, in order of academic rank.</span></span> <span data-ttu-id="5110b-185">在此示例中， `studentQuery4` 必须推断的类型 `Select` ，因为子句返回匿名类型的实例，而匿名类型没有可使用的名称。</span><span class="sxs-lookup"><span data-stu-id="5110b-185">In this example, the type of `studentQuery4` must be inferred because the `Select` clause returns an instance of an anonymous type, and an anonymous type has no usable name.</span></span>

    [!code-vb[VbLINQWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#6)]

2. <span data-ttu-id="5110b-186">按 CTRL + F5 生成并运行应用程序。</span><span class="sxs-lookup"><span data-stu-id="5110b-186">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="5110b-187">请注意控制台窗口中的结果。</span><span class="sxs-lookup"><span data-stu-id="5110b-187">Note the results in the console window.</span></span>

## <a name="additional-examples"></a><span data-ttu-id="5110b-188">其他示例</span><span class="sxs-lookup"><span data-stu-id="5110b-188">Additional Examples</span></span>

<span data-ttu-id="5110b-189">现在，你已了解基础知识，以下是说明 LINQ 查询的灵活性和强大功能的其他示例列表。</span><span class="sxs-lookup"><span data-stu-id="5110b-189">Now that you understand the basics, the following is a list of additional examples to illustrate the flexibility and power of LINQ queries.</span></span> <span data-ttu-id="5110b-190">每个示例前面都有其作用的简短说明。</span><span class="sxs-lookup"><span data-stu-id="5110b-190">Each example is preceded by a brief description of what it does.</span></span> <span data-ttu-id="5110b-191">将鼠标指针停留在每个查询的查询结果变量上，以查看推断出的类型。</span><span class="sxs-lookup"><span data-stu-id="5110b-191">Rest the mouse pointer over the query result variable for each query to see the inferred type.</span></span> <span data-ttu-id="5110b-192">使用 `For Each` 循环来生成结果。</span><span class="sxs-lookup"><span data-stu-id="5110b-192">Use a `For Each` loop to produce the results.</span></span>

[!code-vb[VbLINQWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#7)]

## <a name="additional-information"></a><span data-ttu-id="5110b-193">其他信息</span><span class="sxs-lookup"><span data-stu-id="5110b-193">Additional Information</span></span>

<span data-ttu-id="5110b-194">熟悉使用查询的基本概念后，便可以阅读感兴趣的特定类型 LINQ 提供程序的文档和示例：</span><span class="sxs-lookup"><span data-stu-id="5110b-194">After you are familiar with the basic concepts of working with queries, you are ready to read the documentation and samples for the specific type of LINQ provider that you are interested in:</span></span>

- [<span data-ttu-id="5110b-195">LINQ to Objects</span><span class="sxs-lookup"><span data-stu-id="5110b-195">LINQ to Objects</span></span>](linq-to-objects.md)

- [<span data-ttu-id="5110b-196">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="5110b-196">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)

- [<span data-ttu-id="5110b-197">LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="5110b-197">LINQ to XML</span></span>](../../../../standard/linq/linq-xml-overview.md)

- [<span data-ttu-id="5110b-198">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="5110b-198">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)

## <a name="see-also"></a><span data-ttu-id="5110b-199">请参阅</span><span class="sxs-lookup"><span data-stu-id="5110b-199">See also</span></span>

- [<span data-ttu-id="5110b-200">语言集成查询 (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5110b-200">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="5110b-201">Visual Basic 中的 LINQ 入门</span><span class="sxs-lookup"><span data-stu-id="5110b-201">Getting Started with LINQ in Visual Basic</span></span>](getting-started-with-linq.md)
- [<span data-ttu-id="5110b-202">局部类型推理</span><span class="sxs-lookup"><span data-stu-id="5110b-202">Local Type Inference</span></span>](../../language-features/variables/local-type-inference.md)
- [<span data-ttu-id="5110b-203">对象初始值设定项：命名和匿名类型</span><span class="sxs-lookup"><span data-stu-id="5110b-203">Object Initializers: Named and Anonymous Types</span></span>](../../language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="5110b-204">匿名类型</span><span class="sxs-lookup"><span data-stu-id="5110b-204">Anonymous Types</span></span>](../../language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="5110b-205">Visual Basic 中的 LINQ 简介</span><span class="sxs-lookup"><span data-stu-id="5110b-205">Introduction to LINQ in Visual Basic</span></span>](../../language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="5110b-206">LINQ</span><span class="sxs-lookup"><span data-stu-id="5110b-206">LINQ</span></span>](../../language-features/linq/index.md)
- [<span data-ttu-id="5110b-207">查询</span><span class="sxs-lookup"><span data-stu-id="5110b-207">Queries</span></span>](../../../language-reference/queries/index.md)
