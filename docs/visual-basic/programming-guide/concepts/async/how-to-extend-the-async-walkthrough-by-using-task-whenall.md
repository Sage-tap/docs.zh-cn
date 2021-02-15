---
description: '了解详细信息：如何：使用 System.threading.tasks.task.whenall (Visual Basic 扩展 Async 演练) '
title: 如何：使用 Task.WhenAll 扩展异步演练
ms.date: 07/20/2015
ms.assetid: c06d386d-e996-4da9-bf3d-05a3b6c0a258
ms.openlocfilehash: fc303d6b2ed64cb2003c06724fcd21000d0b3abf
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100474377"
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-visual-basic"></a><span data-ttu-id="ede20-103">如何：使用 Task.WhenAll 扩展异步演练 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ede20-103">How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)</span></span>

<span data-ttu-id="ede20-104">可以通过使用 [async 和 Await (Visual Basic) ](walkthrough-accessing-the-web-by-using-async-and-await.md) 通过使用方法来提高异步解决方案的性能 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="ede20-104">You can improve the performance of the async solution in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md) by using the <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ede20-105">此方法以异步方式等待多个异步操作（它们表示为任务的集合）。</span><span class="sxs-lookup"><span data-stu-id="ede20-105">This method asynchronously awaits multiple asynchronous operations, which are represented as a collection of tasks.</span></span>

<span data-ttu-id="ede20-106">你可能已在演练中注意到网站以不同速率进行下载。</span><span class="sxs-lookup"><span data-stu-id="ede20-106">You might have noticed in the walkthrough that the websites download at different rates.</span></span> <span data-ttu-id="ede20-107">有时一个网站非常慢，这会延迟所有其余下载。</span><span class="sxs-lookup"><span data-stu-id="ede20-107">Sometimes one of the websites is very slow, which delays all the remaining downloads.</span></span> <span data-ttu-id="ede20-108">运行在演练中生成的异步解决方案时，如果不想等待，则可以方便地结束程序，但更好的选项是同时启动所有下载，并让较快的下载继续进行而不等待延迟的下载。</span><span class="sxs-lookup"><span data-stu-id="ede20-108">When you run the asynchronous solutions that you build in the walkthrough, you can end the program easily if you don't want to wait, but a better option would be to start all the downloads at the same time and let faster downloads continue without waiting for the one that’s delayed.</span></span>

<span data-ttu-id="ede20-109">可将 `Task.WhenAll` 方法应用于任务的集合。</span><span class="sxs-lookup"><span data-stu-id="ede20-109">You apply the `Task.WhenAll` method to a collection of tasks.</span></span> <span data-ttu-id="ede20-110">`WhenAll` 的应用程序返回单个任务，直到集合中的每个任务都已完成之后，该任务才会完成。</span><span class="sxs-lookup"><span data-stu-id="ede20-110">The application of `WhenAll` returns a single task that isn’t complete until every task in the collection is completed.</span></span> <span data-ttu-id="ede20-111">任务会表现为并行运行，但不会创建其他线程。</span><span class="sxs-lookup"><span data-stu-id="ede20-111">The tasks appear to run in parallel, but no additional threads are created.</span></span> <span data-ttu-id="ede20-112">任务可以按任何顺序完成。</span><span class="sxs-lookup"><span data-stu-id="ede20-112">The tasks can complete in any order.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ede20-113">以下过程介绍了演练中开发的异步应用程序的扩展 [：使用 async 和 Await 访问 Web (Visual Basic) ](walkthrough-accessing-the-web-by-using-async-and-await.md)。</span><span class="sxs-lookup"><span data-stu-id="ede20-113">The following procedures describe extensions to the async applications that are developed in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="ede20-114">可以通过完成演练或从[开发人员代码示例](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)下载代码来开发应用程序。</span><span class="sxs-lookup"><span data-stu-id="ede20-114">You can develop the applications by either completing the walkthrough or downloading the code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>
>
> <span data-ttu-id="ede20-115">若要运行示例，必须在计算机上安装 Visual Studio 2012 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="ede20-115">To run the example, you must have Visual Studio 2012 or later installed on your computer.</span></span>

### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a><span data-ttu-id="ede20-116">向你的 GetURLContentsAsync 解决方案中添加 Task.WhenAll</span><span class="sxs-lookup"><span data-stu-id="ede20-116">To add Task.WhenAll to your GetURLContentsAsync solution</span></span>

1. <span data-ttu-id="ede20-117">将 `ProcessURLAsync` 方法添加到在演练中开发的第一个应用程序 [：使用 Async 和 Await 访问 Web (Visual Basic) ](walkthrough-accessing-the-web-by-using-async-and-await.md)。</span><span class="sxs-lookup"><span data-stu-id="ede20-117">Add the `ProcessURLAsync` method to the first application that's developed in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>

    - <span data-ttu-id="ede20-118">如果从  [开发人员代码示例](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)下载代码，请打开 AsyncWalkthrough 项目，然后将添加 `ProcessURLAsync` 到 mainwindow.xaml 文件中。</span><span class="sxs-lookup"><span data-stu-id="ede20-118">If you downloaded the code from  [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), open the AsyncWalkthrough project, and then add `ProcessURLAsync` to the MainWindow.xaml.vb file.</span></span>

    - <span data-ttu-id="ede20-119">如果是通过完成演练开发的代码，请向包含 `GetURLContentsAsync` 方法的应用程序添加 `ProcessURLAsync`。</span><span class="sxs-lookup"><span data-stu-id="ede20-119">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that includes the `GetURLContentsAsync` method.</span></span> <span data-ttu-id="ede20-120">此应用程序的 Mainwindow.xaml 文件是 "完成演练中的代码示例" 部分中的第一个示例。</span><span class="sxs-lookup"><span data-stu-id="ede20-120">The MainWindow.xaml.vb file for this application is the first example in the "Complete Code Examples from the Walkthrough" section.</span></span>

     <span data-ttu-id="ede20-121">`ProcessURLAsync` 方法整合了原始演练的 `SumPageSizesAsync` 中的 `For Each` 循环体中的操作。</span><span class="sxs-lookup"><span data-stu-id="ede20-121">The `ProcessURLAsync` method consolidates the actions in the body of the `For Each` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="ede20-122">该方法以异步方式将指定网站的内容作为字节数组进行下载，然后显示并返回字节数组的长度。</span><span class="sxs-lookup"><span data-stu-id="ede20-122">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>

    ```vb
    Private Async Function ProcessURLAsync(url As String) As Task(Of Integer)

        Dim byteArray = Await GetURLContentsAsync(url)
        DisplayResults(url, byteArray)
        Return byteArray.Length
    End Function
    ```

2. <span data-ttu-id="ede20-123">注释禁止或删除 `SumPageSizesAsync` 中的 `For Each` 循环，如以下代码所示。</span><span class="sxs-lookup"><span data-stu-id="ede20-123">Comment out or delete the `For Each` loop in `SumPageSizesAsync`, as the following code shows.</span></span>

    ```vb
    'Dim total = 0
    'For Each url In urlList

    '    Dim urlContents As Byte() = Await GetURLContentsAsync(url)

    '    ' The previous line abbreviates the following two assignment statements.

    '    ' GetURLContentsAsync returns a task. At completion, the task
    '    ' produces a byte array.
    '    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)
    '    'Dim urlContents As Byte() = Await getContentsTask

    '    DisplayResults(url, urlContents)

    '    ' Update the total.
    '    total += urlContents.Length
    'Next
    ```

3. <span data-ttu-id="ede20-124">创建任务集合。</span><span class="sxs-lookup"><span data-stu-id="ede20-124">Create a collection of tasks.</span></span> <span data-ttu-id="ede20-125">以下代码定义一个[查询](../linq/index.md)，由 <xref:System.Linq.Enumerable.ToArray%2A> 方法执行该查询时，它会创建下载每个网站内容的任务集合。</span><span class="sxs-lookup"><span data-stu-id="ede20-125">The following code defines a [query](../linq/index.md) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="ede20-126">计算该查询时，会启动任务。</span><span class="sxs-lookup"><span data-stu-id="ede20-126">The tasks are started when the query is evaluated.</span></span>

     <span data-ttu-id="ede20-127">在 `urlList` 的声明后，将以下代码添加到方法 `SumPageSizesAsync` 中。</span><span class="sxs-lookup"><span data-stu-id="ede20-127">Add the following code to method `SumPageSizesAsync` after the declaration of `urlList`.</span></span>

    ```vb
    ' Create a query.
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
        From url In urlList Select ProcessURLAsync(url)

    ' Use ToArray to execute the query and start the download tasks.
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()
    ```

4. <span data-ttu-id="ede20-128">将 `Task.WhenAll` 应用于任务集合 `downloadTasks`。</span><span class="sxs-lookup"><span data-stu-id="ede20-128">Apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="ede20-129">`Task.WhenAll` 返回单个任务，它在任务集合中的所有任务都已完成时完成。</span><span class="sxs-lookup"><span data-stu-id="ede20-129">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>

     <span data-ttu-id="ede20-130">在以下示例中，`Await` 表达式等待 `WhenAll` 返回的单个任务完成。</span><span class="sxs-lookup"><span data-stu-id="ede20-130">In the following example, the `Await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="ede20-131">该表达式的计算结果为整数数组，其中每个整数都是一个下载的网站的长度。</span><span class="sxs-lookup"><span data-stu-id="ede20-131">The expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="ede20-132">就在上一步添加的代码后，将以下代码添加到 `SumPageSizesAsync` 中。</span><span class="sxs-lookup"><span data-stu-id="ede20-132">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>

    ```vb
    ' Await the completion of all the running tasks.
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)

    '' The previous line is equivalent to the following two statements.
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)
    'Dim lengths As Integer() = Await whenAllTask
    ```

5. <span data-ttu-id="ede20-133">最后，使用 <xref:System.Linq.Enumerable.Sum%2A> 方法计算所有网站的长度总和。</span><span class="sxs-lookup"><span data-stu-id="ede20-133">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to calculate the sum of the lengths of all the websites.</span></span> <span data-ttu-id="ede20-134">将以下行添加到 `SumPageSizesAsync` 中。</span><span class="sxs-lookup"><span data-stu-id="ede20-134">Add the following line to `SumPageSizesAsync`.</span></span>

    ```vb
    Dim total = lengths.Sum()
    ```

### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a><span data-ttu-id="ede20-135">向 HttpClient.GetByteArrayAsync 解决方案中添加 Task.WhenAll</span><span class="sxs-lookup"><span data-stu-id="ede20-135">To add Task.WhenAll to the HttpClient.GetByteArrayAsync solution</span></span>

1. <span data-ttu-id="ede20-136">将以下版本的添加 `ProcessURLAsync` 到演练中开发的第二个应用程序 [：使用 Async 和 Await 访问 Web (Visual Basic) ](walkthrough-accessing-the-web-by-using-async-and-await.md)。</span><span class="sxs-lookup"><span data-stu-id="ede20-136">Add the following version of `ProcessURLAsync` to the second application that's developed in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>

    - <span data-ttu-id="ede20-137">如果从 [开发人员代码示例](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)下载代码，请打开 AsyncWalkthrough_HttpClient 项目，然后将添加 `ProcessURLAsync` 到 mainwindow.xaml 文件。</span><span class="sxs-lookup"><span data-stu-id="ede20-137">If you downloaded the code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), open the AsyncWalkthrough_HttpClient project, and then add `ProcessURLAsync` to the MainWindow.xaml.vb file.</span></span>

    - <span data-ttu-id="ede20-138">如果是通过完成演练开发的代码，请向使用 `HttpClient.GetByteArrayAsync` 方法的应用程序添加 `ProcessURLAsync`。</span><span class="sxs-lookup"><span data-stu-id="ede20-138">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that uses the `HttpClient.GetByteArrayAsync` method.</span></span> <span data-ttu-id="ede20-139">此应用程序的 Mainwindow.xaml 文件是 "完成演练中的代码示例" 部分中的第二个示例。</span><span class="sxs-lookup"><span data-stu-id="ede20-139">The MainWindow.xaml.vb file for this application is the second example in the "Complete Code Examples from the Walkthrough" section.</span></span>

     <span data-ttu-id="ede20-140">`ProcessURLAsync` 方法整合了原始演练的 `SumPageSizesAsync` 中的 `For Each` 循环体中的操作。</span><span class="sxs-lookup"><span data-stu-id="ede20-140">The `ProcessURLAsync` method consolidates the actions in the body of the `For Each` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="ede20-141">该方法以异步方式将指定网站的内容作为字节数组进行下载，然后显示并返回字节数组的长度。</span><span class="sxs-lookup"><span data-stu-id="ede20-141">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>

     <span data-ttu-id="ede20-142">与上面过程中的 `ProcessURLAsync` 方法的唯一区别是使用 <xref:System.Net.Http.HttpClient> 实例 `client`。</span><span class="sxs-lookup"><span data-stu-id="ede20-142">The only difference from the `ProcessURLAsync` method in the previous procedure is the use of the <xref:System.Net.Http.HttpClient> instance, `client`.</span></span>

    ```vb
    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)

        Dim byteArray = Await client.GetByteArrayAsync(url)
        DisplayResults(url, byteArray)
        Return byteArray.Length
    End Function
    ```

2. <span data-ttu-id="ede20-143">注释禁止或删除 `SumPageSizesAsync` 中的 `For Each` 循环，如以下代码所示。</span><span class="sxs-lookup"><span data-stu-id="ede20-143">Comment out or delete the `For Each` loop in `SumPageSizesAsync`, as the following code shows.</span></span>

    ```vb
    'Dim total = 0
    'For Each url In urlList
    '    ' GetByteArrayAsync returns a task. At completion, the task
    '    ' produces a byte array.
    '    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)

    '    ' The following two lines can replace the previous assignment statement.
    '    'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)
    '    'Dim urlContents As Byte() = Await getContentsTask

    '    DisplayResults(url, urlContents)

    '    ' Update the total.
    '    total += urlContents.Length
    'Next
    ```

3. <span data-ttu-id="ede20-144">定义一个[查询](../linq/index.md)，由 <xref:System.Linq.Enumerable.ToArray%2A> 方法执行该查询时，它会创建下载每个网站内容的任务集合。</span><span class="sxs-lookup"><span data-stu-id="ede20-144">Define a [query](../linq/index.md) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="ede20-145">计算该查询时，会启动任务。</span><span class="sxs-lookup"><span data-stu-id="ede20-145">The tasks are started when the query is evaluated.</span></span>

     <span data-ttu-id="ede20-146">在 `client` 和 `urlList` 的声明后，将以下代码添加到方法 `SumPageSizesAsync` 中。</span><span class="sxs-lookup"><span data-stu-id="ede20-146">Add the following code to method `SumPageSizesAsync` after the declaration of `client` and `urlList`.</span></span>

    ```vb
    ' Create a query.
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
        From url In urlList Select ProcessURLAsync(url, client)

    ' Use ToArray to execute the query and start the download tasks.
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()
    ```

4. <span data-ttu-id="ede20-147">接下来，将 `Task.WhenAll` 应用于任务集合 `downloadTasks`。</span><span class="sxs-lookup"><span data-stu-id="ede20-147">Next, apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="ede20-148">`Task.WhenAll` 返回单个任务，它在任务集合中的所有任务都已完成时完成。</span><span class="sxs-lookup"><span data-stu-id="ede20-148">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>

     <span data-ttu-id="ede20-149">在以下示例中，`Await` 表达式等待 `WhenAll` 返回的单个任务完成。</span><span class="sxs-lookup"><span data-stu-id="ede20-149">In the following example, the `Await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="ede20-150">完成后，`Await` 表达式的计算结果为整数数组，其中每个整数都是一个下载的网站的长度。</span><span class="sxs-lookup"><span data-stu-id="ede20-150">When complete, the `Await` expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="ede20-151">就在上一步添加的代码后，将以下代码添加到 `SumPageSizesAsync` 中。</span><span class="sxs-lookup"><span data-stu-id="ede20-151">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>

    ```vb
    ' Await the completion of all the running tasks.
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)

    '' The previous line is equivalent to the following two statements.
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)
    'Dim lengths As Integer() = Await whenAllTask
    ```

5. <span data-ttu-id="ede20-152">最后，使用 <xref:System.Linq.Enumerable.Sum%2A> 方法获取所有网站的长度总和。</span><span class="sxs-lookup"><span data-stu-id="ede20-152">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to get the sum of the lengths of all the websites.</span></span> <span data-ttu-id="ede20-153">将以下行添加到 `SumPageSizesAsync` 中。</span><span class="sxs-lookup"><span data-stu-id="ede20-153">Add the following line to `SumPageSizesAsync`.</span></span>

    ```vb
    Dim total = lengths.Sum()
    ```

### <a name="to-test-the-taskwhenall-solutions"></a><span data-ttu-id="ede20-154">测试 Task.WhenAll 解决方案</span><span class="sxs-lookup"><span data-stu-id="ede20-154">To test the Task.WhenAll solutions</span></span>

<span data-ttu-id="ede20-155">对于任一解决方案，按 F5 键以运行程序，然后选择“启动”按钮。</span><span class="sxs-lookup"><span data-stu-id="ede20-155">For either solution, choose the F5 key to run the program, and then choose the **Start** button.</span></span> <span data-ttu-id="ede20-156">输出应类似于以下演练中异步解决方案的输出 [：使用 async 和 Await 访问 Web (Visual Basic) ](walkthrough-accessing-the-web-by-using-async-and-await.md)。</span><span class="sxs-lookup"><span data-stu-id="ede20-156">The output should resemble the output from the async solutions in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="ede20-157">但请注意，网站每次会以不同顺序出现。</span><span class="sxs-lookup"><span data-stu-id="ede20-157">However, notice that the websites appear in a different order each time.</span></span>

## <a name="example"></a><span data-ttu-id="ede20-158">示例</span><span class="sxs-lookup"><span data-stu-id="ede20-158">Example</span></span>

<span data-ttu-id="ede20-159">以下代码演示使用 `GetURLContentsAsync` 方法从 Web 下载内容的项目的扩展。</span><span class="sxs-lookup"><span data-stu-id="ede20-159">The following code shows the extensions to the project that uses the `GetURLContentsAsync` method to download content from the web.</span></span>

```vb
' Add the following Imports statements, and add a reference for System.Net.Http.
Imports System.Net.Http
Imports System.Net
Imports System.IO

Class MainWindow

    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click

        resultsTextBox.Clear()

        ' One-step async call.
        Await SumPageSizesAsync()

        '' Two-step async call.
        'Dim sumTask As Task = SumPageSizesAsync()
        'Await sumTask

        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."
    End Sub

    Private Async Function SumPageSizesAsync() As Task

        ' Make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        ' Create a query.
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
            From url In urlList Select ProcessURLAsync(url)

        ' Use ToArray to execute the query and start the download tasks.
        Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()

        ' You can do other work here before awaiting.

        ' Await the completion of all the running tasks.
        Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)

        '' The previous line is equivalent to the following two statements.
        'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)
        'Dim lengths As Integer() = Await whenAllTask

        Dim total = lengths.Sum()

        'Dim total = 0
        'For Each url In urlList

        '    Dim urlContents As Byte() = Await GetURLContentsAsync(url)

        '    ' The previous line abbreviates the following two assignment statements.

        '    ' GetURLContentsAsync returns a task. At completion, the task
        '    ' produces a byte array.
        '    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)
        '    'Dim urlContents As Byte() = Await getContentsTask

        '    DisplayResults(url, urlContents)

        '    ' Update the total.
        '    total += urlContents.Length
        'NextNext

        ' Display the total count for all of the web addresses.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function

    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
    End Function

    ' The actions from the foreach loop are moved to this async method.
    Private Async Function ProcessURLAsync(url As String) As Task(Of Integer)

        Dim byteArray = Await GetURLContentsAsync(url)
        DisplayResults(url, byteArray)
        Return byteArray.Length
    End Function

    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())

        ' The downloaded resource ends up in the variable named content.
        Dim content = New MemoryStream()

        ' Initialize an HttpWebRequest for the current URL.
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)

        ' Send the request to the Internet resource and wait for
        ' the response.
        Using response As WebResponse = Await webReq.GetResponseAsync()
            ' Get the data stream that is associated with the specified URL.
            Using responseStream As Stream = response.GetResponseStream()
                ' Read the bytes in responseStream and copy them to content.
                ' CopyToAsync returns a Task, not a Task<T>.
                Await responseStream.CopyToAsync(content)
            End Using
        End Using

        ' Return the result as a byte array.
        Return content.ToArray()
    End Function

    Private Sub DisplayResults(url As String, content As Byte())

        ' Display the length of each website. The string format
        ' is designed to be used with a monospaced font, such as
        ' Lucida Console or Global Monospace.
        Dim bytes = content.Length
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub

End Class
```

## <a name="example"></a><span data-ttu-id="ede20-160">示例</span><span class="sxs-lookup"><span data-stu-id="ede20-160">Example</span></span>

<span data-ttu-id="ede20-161">以下代码演示使用 `HttpClient.GetByteArrayAsync` 方法从 Web 下载内容的项目的扩展。</span><span class="sxs-lookup"><span data-stu-id="ede20-161">The following code shows the extensions to the project that uses method `HttpClient.GetByteArrayAsync` to download content from the web.</span></span>

```vb
' Add the following Imports statements, and add a reference for System.Net.Http.
Imports System.Net.Http
Imports System.Net
Imports System.IO

Class MainWindow

    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click

        resultsTextBox.Clear()

        '' One-step async call.
        Await SumPageSizesAsync()

        '' Two-step async call.
        'Dim sumTask As Task = SumPageSizesAsync()
        'Await sumTask

        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."
    End Sub

    Private Async Function SumPageSizesAsync() As Task

        ' Declare an HttpClient object and increase the buffer size. The
        ' default buffer size is 65,536.
        Dim client As HttpClient =
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}

        ' Make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        ' Create a query.
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
            From url In urlList Select ProcessURLAsync(url, client)

        ' Use ToArray to execute the query and start the download tasks.
        Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()

        ' You can do other work here before awaiting.

        ' Await the completion of all the running tasks.
        Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)

        '' The previous line is equivalent to the following two statements.
        'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)
        'Dim lengths As Integer() = Await whenAllTask

        Dim total = lengths.Sum()

        ''<snippet7>
        'Dim total = 0
        'For Each url In urlList
        '    ' GetByteArrayAsync returns a task. At completion, the task
        '    ' produces a byte array.
        '    '<snippet31>
        '    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)
        '    '</snippet31>

        '    ' The following two lines can replace the previous assignment statement.
        '    'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)
        '    'Dim urlContents As Byte() = Await getContentsTask

        '    DisplayResults(url, urlContents)

        '    ' Update the total.
        '    total += urlContents.Length
        'NextNext

        ' Display the total count for all of the web addresses.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function

    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://www.msdn.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
    End Function

    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)

        Dim byteArray = Await client.GetByteArrayAsync(url)
        DisplayResults(url, byteArray)
        Return byteArray.Length
    End Function

    Private Sub DisplayResults(url As String, content As Byte())

        ' Display the length of each website. The string format
        ' is designed to be used with a monospaced font, such as
        ' Lucida Console or Global Monospace.
        Dim bytes = content.Length
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub

End Class
```

## <a name="see-also"></a><span data-ttu-id="ede20-162">请参阅</span><span class="sxs-lookup"><span data-stu-id="ede20-162">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>
- [<span data-ttu-id="ede20-163">演练：使用 Async 和 Await 访问 Web (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ede20-163">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](walkthrough-accessing-the-web-by-using-async-and-await.md)
