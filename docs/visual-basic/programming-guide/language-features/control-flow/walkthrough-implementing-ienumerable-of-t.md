---
description: 了解详细信息：演练：在 Visual Basic 中实现 T) 的 IEnumerable (
title: 实现 IEnumerable
ms.date: 07/31/2018
helpviewer_keywords:
- control flow [Visual Basic]
- enumerable interfaces
- loop structures [Visual Basic], optimizing performance
- control flow [Visual Basic]
ms.assetid: c60d7589-51f2-4463-a2d5-22506bbc1554
ms.openlocfilehash: 87905e4f110d3a9d95b1cad642296ea8105f32f4
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100428137"
---
# <a name="walkthrough-implementing-ienumerableof-t-in-visual-basic"></a><span data-ttu-id="be5b7-103">演练：在 Visual Basic 中实现 IEnumerable(Of T)</span><span class="sxs-lookup"><span data-stu-id="be5b7-103">Walkthrough: Implementing IEnumerable(Of T) in Visual Basic</span></span>

<span data-ttu-id="be5b7-104"><xref:System.Collections.Generic.IEnumerable%601>接口由每次可以返回一项值序列的类实现。</span><span class="sxs-lookup"><span data-stu-id="be5b7-104">The <xref:System.Collections.Generic.IEnumerable%601> interface is implemented by classes that can return a sequence of values one item at a time.</span></span> <span data-ttu-id="be5b7-105">一次返回一项数据的优点是，无需将完整的数据集加载到内存中即可使用它。</span><span class="sxs-lookup"><span data-stu-id="be5b7-105">The advantage of returning data one item at a time is that you do not have to load the complete set of data into memory to work with it.</span></span> <span data-ttu-id="be5b7-106">只需使用足够的内存来加载数据中的单个项。</span><span class="sxs-lookup"><span data-stu-id="be5b7-106">You only have to use sufficient memory to load a single item from the data.</span></span> <span data-ttu-id="be5b7-107">实现接口的类 `IEnumerable(T)` 可用于 `For Each` 循环或 LINQ 查询。</span><span class="sxs-lookup"><span data-stu-id="be5b7-107">Classes that implement the `IEnumerable(T)` interface can be used with `For Each` loops or LINQ queries.</span></span>  
  
 <span data-ttu-id="be5b7-108">例如，假设某个应用程序必须读取一个大型文本文件，并从该文件中返回与特定搜索条件相匹配的每一行。</span><span class="sxs-lookup"><span data-stu-id="be5b7-108">For example, consider an application that must read a large text file and return each line from the file that matches particular search criteria.</span></span> <span data-ttu-id="be5b7-109">应用程序使用 LINQ 查询从文件返回与指定条件相匹配的行。</span><span class="sxs-lookup"><span data-stu-id="be5b7-109">The application uses a LINQ query to return lines from the file that match the specified criteria.</span></span> <span data-ttu-id="be5b7-110">若要通过使用 LINQ 查询来查询文件的内容，应用程序可以将文件的内容加载到数组或集合中。</span><span class="sxs-lookup"><span data-stu-id="be5b7-110">To query the contents of the file by using a LINQ query, the application could load the contents of the file into an array or a collection.</span></span> <span data-ttu-id="be5b7-111">但是，将整个文件加载到数组或集合会占用比所需的更多的内存。</span><span class="sxs-lookup"><span data-stu-id="be5b7-111">However, loading the whole file into an array or collection would consume far more memory than is required.</span></span> <span data-ttu-id="be5b7-112">LINQ 查询可以使用可枚举的类（仅返回与搜索条件匹配的值）来查询文件内容。</span><span class="sxs-lookup"><span data-stu-id="be5b7-112">The LINQ query could instead query the file contents by using an enumerable class, returning only values that match the search criteria.</span></span> <span data-ttu-id="be5b7-113">仅返回几个匹配值的查询将消耗更少的内存。</span><span class="sxs-lookup"><span data-stu-id="be5b7-113">Queries that return only a few matching values would consume far less memory.</span></span>  
  
 <span data-ttu-id="be5b7-114">你可以创建一个实现接口的类， <xref:System.Collections.Generic.IEnumerable%601> 以将源数据作为可枚举数据公开。</span><span class="sxs-lookup"><span data-stu-id="be5b7-114">You can create a class that implements the <xref:System.Collections.Generic.IEnumerable%601> interface to expose source data as enumerable data.</span></span> <span data-ttu-id="be5b7-115">实现接口的类 `IEnumerable(T)` 将需要另一个实现接口的类 <xref:System.Collections.Generic.IEnumerator%601> 来循环访问源数据。</span><span class="sxs-lookup"><span data-stu-id="be5b7-115">Your class that implements the `IEnumerable(T)` interface will require another class that implements the <xref:System.Collections.Generic.IEnumerator%601> interface to iterate through the source data.</span></span> <span data-ttu-id="be5b7-116">这两个类使你能够按特定类型按顺序返回数据项。</span><span class="sxs-lookup"><span data-stu-id="be5b7-116">These two classes enable you to return items of data sequentially as a specific type.</span></span>  
  
 <span data-ttu-id="be5b7-117">在本演练中，您将创建一个实现接口的类 `IEnumerable(Of String)` 和一个实现 `IEnumerator(Of String)` 接口的类，以便一次一行地读取一个文本文件。</span><span class="sxs-lookup"><span data-stu-id="be5b7-117">In this walkthrough, you will create a class that implements the `IEnumerable(Of String)` interface and a class that implements the `IEnumerator(Of String)` interface to read a text file one line at a time.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-enumerable-class"></a><span data-ttu-id="be5b7-118">创建可枚举类</span><span class="sxs-lookup"><span data-stu-id="be5b7-118">Creating the Enumerable Class</span></span>  
  
<span data-ttu-id="be5b7-119">**创建可枚举类项目**</span><span class="sxs-lookup"><span data-stu-id="be5b7-119">**Create the enumerable class project**</span></span>

1. <span data-ttu-id="be5b7-120">在 Visual Basic 的 " **文件** " 菜单上，指向 " **新建** "，然后单击 " **项目**"。</span><span class="sxs-lookup"><span data-stu-id="be5b7-120">In Visual Basic, on the **File** menu, point to **New** and then click **Project**.</span></span>

1. <span data-ttu-id="be5b7-121">在“新建项目”对话框的“项目类型”窗格中，确保选中“Windows”。</span><span class="sxs-lookup"><span data-stu-id="be5b7-121">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="be5b7-122">在“模板”窗格中，选择“类库”。</span><span class="sxs-lookup"><span data-stu-id="be5b7-122">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="be5b7-123">在“名称”框中，键入 `StreamReaderEnumerable`，然后单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="be5b7-123">In the **Name** box, type `StreamReaderEnumerable`, and then click **OK**.</span></span> <span data-ttu-id="be5b7-124">将显示新项目。</span><span class="sxs-lookup"><span data-stu-id="be5b7-124">The new project is displayed.</span></span>

1. <span data-ttu-id="be5b7-125">在 **解决方案资源管理器** 中，右键单击 Class1 文件，然后单击 " **重命名**"。</span><span class="sxs-lookup"><span data-stu-id="be5b7-125">In **Solution Explorer**, right-click the Class1.vb file and click **Rename**.</span></span> <span data-ttu-id="be5b7-126">将文件重命名为 `StreamReaderEnumerable.vb`，然后按 Enter。</span><span class="sxs-lookup"><span data-stu-id="be5b7-126">Rename the file to `StreamReaderEnumerable.vb` and press ENTER.</span></span> <span data-ttu-id="be5b7-127">重命名文件也会将类重命名为 `StreamReaderEnumerable`。</span><span class="sxs-lookup"><span data-stu-id="be5b7-127">Renaming the file will also rename the class to `StreamReaderEnumerable`.</span></span> <span data-ttu-id="be5b7-128">此类将实现 `IEnumerable(Of String)` 接口。</span><span class="sxs-lookup"><span data-stu-id="be5b7-128">This class will implement the `IEnumerable(Of String)` interface.</span></span>

1. <span data-ttu-id="be5b7-129">右键单击 "StreamReaderEnumerable" 项目，指向 " **添加**"，然后单击 " **新建项**"。</span><span class="sxs-lookup"><span data-stu-id="be5b7-129">Right-click the StreamReaderEnumerable project, point to **Add**, and then click **New Item**.</span></span> <span data-ttu-id="be5b7-130">选择 " **类** " 模板。</span><span class="sxs-lookup"><span data-stu-id="be5b7-130">Select the **Class** template.</span></span> <span data-ttu-id="be5b7-131">在 " **名称** " 框中，键入 `StreamReaderEnumerator.vb` 并单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="be5b7-131">In the **Name** box, type `StreamReaderEnumerator.vb` and click **OK**.</span></span>

 <span data-ttu-id="be5b7-132">此项目中的第一个类是可枚举类并将实现 `IEnumerable(Of String)` 接口。</span><span class="sxs-lookup"><span data-stu-id="be5b7-132">The first class in this project is the enumerable class and will implement the `IEnumerable(Of String)` interface.</span></span> <span data-ttu-id="be5b7-133">此泛型接口实现 <xref:System.Collections.IEnumerable> 接口，并保证此类的使用者可以访问类型为 `String` 的值。</span><span class="sxs-lookup"><span data-stu-id="be5b7-133">This generic interface implements the <xref:System.Collections.IEnumerable> interface and guarantees that consumers of this class can access values typed as `String`.</span></span>  
  
<span data-ttu-id="be5b7-134">**添加代码以实现 IEnumerable**</span><span class="sxs-lookup"><span data-stu-id="be5b7-134">**Add the code to implement IEnumerable**</span></span>

1. <span data-ttu-id="be5b7-135">打开 StreamReaderEnumerable 文件。</span><span class="sxs-lookup"><span data-stu-id="be5b7-135">Open the StreamReaderEnumerable.vb file.</span></span>

2. <span data-ttu-id="be5b7-136">在 "之后的行" `Public Class StreamReaderEnumerable` 中，键入以下各项，然后按 enter。</span><span class="sxs-lookup"><span data-stu-id="be5b7-136">On the line after `Public Class StreamReaderEnumerable`, type the following and press ENTER.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#1)]

   <span data-ttu-id="be5b7-137">Visual Basic 使用接口所需的成员自动填充类 `IEnumerable(Of String)` 。</span><span class="sxs-lookup"><span data-stu-id="be5b7-137">Visual Basic automatically populates the class with the members that are required by the `IEnumerable(Of String)` interface.</span></span>
  
3. <span data-ttu-id="be5b7-138">此可枚举类将一次一行地读取文本文件中的行。</span><span class="sxs-lookup"><span data-stu-id="be5b7-138">This enumerable class will read lines from a text file one line at a time.</span></span> <span data-ttu-id="be5b7-139">将下面的代码添加到类以公开公共构造函数，该构造函数采用文件路径作为输入参数。</span><span class="sxs-lookup"><span data-stu-id="be5b7-139">Add the following code to the class to expose a public constructor that takes a file path as an input parameter.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#2)]

4. <span data-ttu-id="be5b7-140">接口方法的实现 <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> `IEnumerable(Of String)` 将返回类的新实例 `StreamReaderEnumerator` 。</span><span class="sxs-lookup"><span data-stu-id="be5b7-140">Your implementation of the <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method of the `IEnumerable(Of String)` interface will return a new instance of the `StreamReaderEnumerator` class.</span></span> <span data-ttu-id="be5b7-141">`GetEnumerator` `IEnumerable` 可以执行接口的方法 `Private` ，因为必须仅公开接口的成员 `IEnumerable(Of String)` 。</span><span class="sxs-lookup"><span data-stu-id="be5b7-141">The implementation of the `GetEnumerator` method of the `IEnumerable` interface can be made `Private`, because you have to expose only members of the `IEnumerable(Of String)` interface.</span></span> <span data-ttu-id="be5b7-142">将 Visual Basic 为方法生成的代码替换为 `GetEnumerator` 以下代码。</span><span class="sxs-lookup"><span data-stu-id="be5b7-142">Replace the code that Visual Basic generated for the `GetEnumerator` methods with the following code.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#3)]  
  
<span data-ttu-id="be5b7-143">**添加代码以实现 IEnumerator**</span><span class="sxs-lookup"><span data-stu-id="be5b7-143">**Add the code to implement IEnumerator**</span></span>

1. <span data-ttu-id="be5b7-144">打开 StreamReaderEnumerator 文件。</span><span class="sxs-lookup"><span data-stu-id="be5b7-144">Open the StreamReaderEnumerator.vb file.</span></span>

2. <span data-ttu-id="be5b7-145">在 "之后的行" `Public Class StreamReaderEnumerator` 中，键入以下各项，然后按 enter。</span><span class="sxs-lookup"><span data-stu-id="be5b7-145">On the line after `Public Class StreamReaderEnumerator`, type the following and press ENTER.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#4)]

   <span data-ttu-id="be5b7-146">Visual Basic 使用接口所需的成员自动填充类 `IEnumerator(Of String)` 。</span><span class="sxs-lookup"><span data-stu-id="be5b7-146">Visual Basic automatically populates the class with the members that are required by the `IEnumerator(Of String)` interface.</span></span>

3. <span data-ttu-id="be5b7-147">枚举器类打开文本文件，并执行文件 i/o 以读取文件中的行。</span><span class="sxs-lookup"><span data-stu-id="be5b7-147">The enumerator class opens the text file and performs the file I/O to read the lines from the file.</span></span> <span data-ttu-id="be5b7-148">将下面的代码添加到类，以公开公共构造函数，该构造函数采用文件路径作为输入参数并打开文本文件进行读取。</span><span class="sxs-lookup"><span data-stu-id="be5b7-148">Add the following code to the class to expose a public constructor that takes a file path as an input parameter and open the text file for reading.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#5)]

4. <span data-ttu-id="be5b7-149">`Current`和接口的属性均 `IEnumerator(Of String)` 以 `IEnumerator` 形式返回文本文件中的当前项 `String` 。</span><span class="sxs-lookup"><span data-stu-id="be5b7-149">The `Current` properties for both the `IEnumerator(Of String)` and `IEnumerator` interfaces return the current item from the text file as a `String`.</span></span> <span data-ttu-id="be5b7-150">`Current` `IEnumerator` 可以执行接口的属性 `Private` ，因为必须仅公开接口的成员 `IEnumerator(Of String)` 。</span><span class="sxs-lookup"><span data-stu-id="be5b7-150">The implementation of the `Current` property of the `IEnumerator` interface can be made `Private`, because you have to expose only members of the `IEnumerator(Of String)` interface.</span></span> <span data-ttu-id="be5b7-151">将为属性生成的代码替换为 `Current` 以下代码 Visual Basic。</span><span class="sxs-lookup"><span data-stu-id="be5b7-151">Replace the code that Visual Basic generated for the `Current` properties with the following code.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#6)]

5. <span data-ttu-id="be5b7-152">`MoveNext`接口的方法 `IEnumerator` 导航到文本文件中的下一项并更新属性返回的值 `Current` 。</span><span class="sxs-lookup"><span data-stu-id="be5b7-152">The `MoveNext` method of the `IEnumerator` interface navigates to the next item in the text file and updates the value that is returned by the `Current` property.</span></span> <span data-ttu-id="be5b7-153">如果没有更多要读取的项，则此 `MoveNext` 方法将返回 `False` ; 否则，该 `MoveNext` 方法将返回 `True` 。</span><span class="sxs-lookup"><span data-stu-id="be5b7-153">If there are no more items to read, the `MoveNext` method returns `False`; otherwise the `MoveNext` method returns `True`.</span></span> <span data-ttu-id="be5b7-154">将以下代码添加到 `MoveNext` 方法中。</span><span class="sxs-lookup"><span data-stu-id="be5b7-154">Add the following code to the `MoveNext` method.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#7)]

6. <span data-ttu-id="be5b7-155">`Reset`接口的方法 `IEnumerator` 指示迭代器指向文本文件的开头，并清除当前项值。</span><span class="sxs-lookup"><span data-stu-id="be5b7-155">The `Reset` method of the `IEnumerator` interface directs the iterator to point to the start of the text file and clears the current item value.</span></span> <span data-ttu-id="be5b7-156">将以下代码添加到 `Reset` 方法中。</span><span class="sxs-lookup"><span data-stu-id="be5b7-156">Add the following code to the `Reset` method.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#8)]

7. <span data-ttu-id="be5b7-157">`Dispose`接口的方法 `IEnumerator` 保证在迭代器销毁之前释放所有非托管资源。</span><span class="sxs-lookup"><span data-stu-id="be5b7-157">The `Dispose` method of the `IEnumerator` interface guarantees that all unmanaged resources are released before the iterator is destroyed.</span></span> <span data-ttu-id="be5b7-158">对象使用的文件句柄 `StreamReader` 是非托管资源，必须在销毁迭代器实例之前关闭。</span><span class="sxs-lookup"><span data-stu-id="be5b7-158">The file handle that is used by the `StreamReader` object is an unmanaged resource and must be closed before the iterator instance is destroyed.</span></span> <span data-ttu-id="be5b7-159">将 Visual Basic 为方法生成的代码替换为 `Dispose` 以下代码。</span><span class="sxs-lookup"><span data-stu-id="be5b7-159">Replace the code that Visual Basic generated for the `Dispose` method with the following code.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#9)]
  
## <a name="using-the-sample-iterator"></a><span data-ttu-id="be5b7-160">使用示例迭代器</span><span class="sxs-lookup"><span data-stu-id="be5b7-160">Using the Sample Iterator</span></span>

 <span data-ttu-id="be5b7-161">你可以在代码中将可枚举的类与需要实现的对象 `IEnumerable` （如 `For Next` 循环或 LINQ 查询）的控制结构一起使用。</span><span class="sxs-lookup"><span data-stu-id="be5b7-161">You can use an enumerable class in your code together with control structures that require an object that implements `IEnumerable`, such as a `For Next` loop or a LINQ query.</span></span> <span data-ttu-id="be5b7-162">下面的示例显示了 `StreamReaderEnumerable` LINQ 查询中的。</span><span class="sxs-lookup"><span data-stu-id="be5b7-162">The following example shows the `StreamReaderEnumerable` in a LINQ query.</span></span>  
  
 [!code-vb[VbVbalrIteratorWalkthrough#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/Module1.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="be5b7-163">请参阅</span><span class="sxs-lookup"><span data-stu-id="be5b7-163">See also</span></span>

- [<span data-ttu-id="be5b7-164">Visual Basic 中的 LINQ 简介</span><span class="sxs-lookup"><span data-stu-id="be5b7-164">Introduction to LINQ in Visual Basic</span></span>](../linq/introduction-to-linq.md)
- [<span data-ttu-id="be5b7-165">控制流</span><span class="sxs-lookup"><span data-stu-id="be5b7-165">Control Flow</span></span>](index.md)
- [<span data-ttu-id="be5b7-166">循环结构</span><span class="sxs-lookup"><span data-stu-id="be5b7-166">Loop Structures</span></span>](loop-structures.md)
- [<span data-ttu-id="be5b7-167">For Each...Next 语句</span><span class="sxs-lookup"><span data-stu-id="be5b7-167">For Each...Next Statement</span></span>](../../../language-reference/statements/for-each-next-statement.md)
