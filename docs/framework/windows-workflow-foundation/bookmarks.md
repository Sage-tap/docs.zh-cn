---
description: 了解详细信息：书签
title: 书签-WF
ms.date: 03/30/2017
ms.assetid: 9b51a346-09ae-455c-a70a-e2264ddeb9e2
ms.openlocfilehash: b4f0e68e0868ecd4eb97673ff6c09ee8c806cf43
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787924"
---
# <a name="bookmarks"></a><span data-ttu-id="e4c24-103">书签</span><span class="sxs-lookup"><span data-stu-id="e4c24-103">Bookmarks</span></span>

<span data-ttu-id="e4c24-104">书签是使活动能够被动等待输入而无需保持在一个工作流线程上的机制。</span><span class="sxs-lookup"><span data-stu-id="e4c24-104">Bookmarks are the mechanism that enables an activity to passively wait for input without holding onto a workflow thread.</span></span> <span data-ttu-id="e4c24-105">如果某个活动发出正在等待刺激的信号，则该活动可以创建书签。</span><span class="sxs-lookup"><span data-stu-id="e4c24-105">When an activity signals that it is waiting for stimulus, it can create a bookmark.</span></span> <span data-ttu-id="e4c24-106">这指示即使返回了当前正在执行的方法（该方法创建了 <xref:System.Activities.Bookmark>），也不应将该活动的执行视为完成。</span><span class="sxs-lookup"><span data-stu-id="e4c24-106">This indicates to the runtime that the activity’s execution should not be considered complete even when the currently executing method (which created the <xref:System.Activities.Bookmark>) returns.</span></span>  
  
## <a name="bookmark-basics"></a><span data-ttu-id="e4c24-107">书签基础知识</span><span class="sxs-lookup"><span data-stu-id="e4c24-107">Bookmark Basics</span></span>  

 <span data-ttu-id="e4c24-108"><xref:System.Activities.Bookmark> 表示工作流实例中可以在其处继续执行（以及可以通过其传递输入）的点。</span><span class="sxs-lookup"><span data-stu-id="e4c24-108">A <xref:System.Activities.Bookmark> represents a point at which execution can be resumed (and through which input can be delivered) within a workflow instance.</span></span> <span data-ttu-id="e4c24-109">通常，为 <xref:System.Activities.Bookmark> 指定一个名称并且外部（主机或扩展）代码负责使用相关数据继续书签。</span><span class="sxs-lookup"><span data-stu-id="e4c24-109">Typically, a <xref:System.Activities.Bookmark> is given a name and external (host or extension) code is responsible for resuming the bookmark with relevant data.</span></span> <span data-ttu-id="e4c24-110">继续 <xref:System.Activities.Bookmark> 后，工作流运行时会安排与其创建时的 <xref:System.Activities.BookmarkCallback> 关联的 <xref:System.Activities.Bookmark> 委托。</span><span class="sxs-lookup"><span data-stu-id="e4c24-110">When a <xref:System.Activities.Bookmark> is resumed, the workflow runtime schedules the <xref:System.Activities.BookmarkCallback> delegate that was associated with that <xref:System.Activities.Bookmark> at the time of its creation.</span></span>  
  
## <a name="bookmark-options"></a><span data-ttu-id="e4c24-111">书签选项</span><span class="sxs-lookup"><span data-stu-id="e4c24-111">Bookmark Options</span></span>  

 <span data-ttu-id="e4c24-112"><xref:System.Activities.BookmarkOptions> 类指定要创建的 <xref:System.Activities.Bookmark> 的类型。</span><span class="sxs-lookup"><span data-stu-id="e4c24-112">The <xref:System.Activities.BookmarkOptions> class specifies the type of <xref:System.Activities.Bookmark> being created.</span></span> <span data-ttu-id="e4c24-113">不互相排斥的可能值为 <xref:System.Activities.BookmarkOptions.None>、<xref:System.Activities.BookmarkOptions.MultipleResume> 和 <xref:System.Activities.BookmarkOptions.NonBlocking>。</span><span class="sxs-lookup"><span data-stu-id="e4c24-113">The possible non mutually-exclusive values are <xref:System.Activities.BookmarkOptions.None>, <xref:System.Activities.BookmarkOptions.MultipleResume>, and <xref:System.Activities.BookmarkOptions.NonBlocking>.</span></span> <span data-ttu-id="e4c24-114">创建预期只继续一次的 <xref:System.Activities.BookmarkOptions.None> 时，使用默认的 <xref:System.Activities.Bookmark>。</span><span class="sxs-lookup"><span data-stu-id="e4c24-114">Use <xref:System.Activities.BookmarkOptions.None>, the default, when creating a <xref:System.Activities.Bookmark> that is expected to be resumed exactly once.</span></span> <span data-ttu-id="e4c24-115">创建可继续多次的 <xref:System.Activities.BookmarkOptions.MultipleResume> 时，使用 <xref:System.Activities.Bookmark>。</span><span class="sxs-lookup"><span data-stu-id="e4c24-115">Use <xref:System.Activities.BookmarkOptions.MultipleResume> when creating a <xref:System.Activities.Bookmark> that can be resumed multiple times.</span></span> <span data-ttu-id="e4c24-116">创建可能永不继续的 <xref:System.Activities.BookmarkOptions.NonBlocking> 时，使用 <xref:System.Activities.Bookmark>。</span><span class="sxs-lookup"><span data-stu-id="e4c24-116">Use <xref:System.Activities.BookmarkOptions.NonBlocking> when creating a <xref:System.Activities.Bookmark> that might never be resumed.</span></span> <span data-ttu-id="e4c24-117">与使用默认的 <xref:System.Activities.BookmarkOptions> 创建的书签不同，<xref:System.Activities.BookmarkOptions.NonBlocking> 书签不会阻止某个活动完成。</span><span class="sxs-lookup"><span data-stu-id="e4c24-117">Unlike bookmarks created using the default <xref:System.Activities.BookmarkOptions>, <xref:System.Activities.BookmarkOptions.NonBlocking> bookmarks do not prevent an activity from completing.</span></span>  
  
## <a name="bookmark-resumption"></a><span data-ttu-id="e4c24-118">书签继续</span><span class="sxs-lookup"><span data-stu-id="e4c24-118">Bookmark Resumption</span></span>  

 <span data-ttu-id="e4c24-119">位于工作流之外的代码可以使用其中一个 <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> 重载继续书签。</span><span class="sxs-lookup"><span data-stu-id="e4c24-119">Bookmarks can be resumed by code outside of a workflow using one of the <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> overloads.</span></span> <span data-ttu-id="e4c24-120">在本示例中，将创建一个 `ReadLine` 活动。</span><span class="sxs-lookup"><span data-stu-id="e4c24-120">In this example, a `ReadLine` activity is created.</span></span> <span data-ttu-id="e4c24-121">执行时，`ReadLine` 活动创建 <xref:System.Activities.Bookmark>，注册回调，然后等待 <xref:System.Activities.Bookmark> 继续。</span><span class="sxs-lookup"><span data-stu-id="e4c24-121">When executed, the `ReadLine` activity creates a <xref:System.Activities.Bookmark>, registers a callback, and then waits for the <xref:System.Activities.Bookmark> to be resumed.</span></span> <span data-ttu-id="e4c24-122">继续后，`ReadLine` 活动将随 <xref:System.Activities.Bookmark> 传递的数据赋给其 <xref:System.Activities.Activity%601.Result%2A> 实参。</span><span class="sxs-lookup"><span data-stu-id="e4c24-122">When it is resumed, the `ReadLine` activity assigns the data that was passed with the <xref:System.Activities.Bookmark> to its <xref:System.Activities.Activity%601.Result%2A> argument.</span></span>  
  
```csharp  
public sealed class ReadLine : NativeActivity<string>  
{  
    [RequiredArgument]  
    public  InArgument<string> BookmarkName { get; set; }  
  
    protected override void Execute(NativeActivityContext context)  
    {  
        // Create a Bookmark and wait for it to be resumed.  
        context.CreateBookmark(BookmarkName.Get(context),
            new BookmarkCallback(OnResumeBookmark));  
    }  
  
    // NativeActivity derived activities that do asynchronous operations by calling
    // one of the CreateBookmark overloads defined on System.Activities.NativeActivityContext
    // must override the CanInduceIdle property and return true.  
    protected override bool CanInduceIdle  
    {  
        get { return true; }  
    }  
  
    public void OnResumeBookmark(NativeActivityContext context, Bookmark bookmark, object obj)  
    {  
        // When the Bookmark is resumed, assign its value to  
        // the Result argument.  
        Result.Set(context, (string)obj);  
    }  
}  
```  
  
 <span data-ttu-id="e4c24-123">在本示例中，将要创建一个工作流，该工作流使用 `ReadLine` 活动来收集用户名称并将其显示在控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="e4c24-123">In this example, a workflow is created that uses the `ReadLine` activity to gather the user’s name and display it to the console window.</span></span> <span data-ttu-id="e4c24-124">宿主应用程序将执行收集输入的实际工作并通过继续 <xref:System.Activities.Bookmark> 将输入传递给该工作流。</span><span class="sxs-lookup"><span data-stu-id="e4c24-124">The host application performs the actual work of gathering the input and passes it to the workflow by resuming the <xref:System.Activities.Bookmark>.</span></span>  
  
```csharp  
Variable<string> name = new Variable<string>  
{  
    Name = "name"  
};  
  
Activity wf = new Sequence  
{  
    Variables =  
    {  
        name  
    },  
    Activities =  
    {  
        new WriteLine()  
        {  
            Text = "What is your name?"  
        },  
        new ReadLine()  
        {  
            BookmarkName = "UserName",  
            Result = name  
        },  
        new WriteLine()  
        {  
            Text = new InArgument<string>((env) => "Hello, " + name.Get(env))  
        }  
    }  
};  
  
AutoResetEvent syncEvent = new AutoResetEvent(false);  
  
// Create the WorkflowApplication using the desired  
// workflow definition.  
WorkflowApplication wfApp = new WorkflowApplication(wf);  
  
// Handle the desired lifecycle events.  
wfApp.Completed = delegate(WorkflowApplicationCompletedEventArgs e)  
{  
    // Signal the host that the workflow is complete.  
    syncEvent.Set();  
};  
  
// Start the workflow.  
wfApp.Run();  
  
// Collect the user's name and resume the bookmark.  
// Bookmark resumption only occurs when the workflow  
// is idle. If a call to ResumeBookmark is made and the workflow  
// is not idle, ResumeBookmark blocks until the workflow becomes  
// idle before resuming the bookmark.  
wfApp.ResumeBookmark("UserName", Console.ReadLine());  
  
// Wait for Completed to arrive and signal that  
// the workflow is complete.  
syncEvent.WaitOne();  
```  
  
 <span data-ttu-id="e4c24-125">执行 `ReadLine` 活动时，该活动创建一个名为 <xref:System.Activities.Bookmark> 的 `UserName`，然后等待书签继续。</span><span class="sxs-lookup"><span data-stu-id="e4c24-125">When the `ReadLine` activity is executed, it creates a <xref:System.Activities.Bookmark> named `UserName` and then waits for the bookmark to be resumed.</span></span> <span data-ttu-id="e4c24-126">宿主收集所需的数据，然后继续 <xref:System.Activities.Bookmark>。</span><span class="sxs-lookup"><span data-stu-id="e4c24-126">The host collects the desired data and then resumes the <xref:System.Activities.Bookmark>.</span></span> <span data-ttu-id="e4c24-127">工作流继续，显示该名称，然后完成。</span><span class="sxs-lookup"><span data-stu-id="e4c24-127">The workflow resumes, displays the name, and then completes.</span></span> <span data-ttu-id="e4c24-128">请注意，不需要与继续书签有关的任何同步代码。</span><span class="sxs-lookup"><span data-stu-id="e4c24-128">Note that no synchronization code is required with regard to resuming the bookmark.</span></span> <span data-ttu-id="e4c24-129"><xref:System.Activities.Bookmark> 只能在工作流空闲时继续，如果工作流不空闲，则会调用 <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> 块，直到工作流空闲。</span><span class="sxs-lookup"><span data-stu-id="e4c24-129">A <xref:System.Activities.Bookmark> can only be resumed when the workflow is idle, and if the workflow is not idle, the call to <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> blocks until the workflow becomes idle.</span></span>  
  
## <a name="bookmark-resumption-result"></a><span data-ttu-id="e4c24-130">书签继续结果</span><span class="sxs-lookup"><span data-stu-id="e4c24-130">Bookmark Resumption Result</span></span>  

 <span data-ttu-id="e4c24-131"><xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> 返回一个 <xref:System.Activities.BookmarkResumptionResult> 枚举值，以指示书签继续请求的结果。</span><span class="sxs-lookup"><span data-stu-id="e4c24-131"><xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> returns a <xref:System.Activities.BookmarkResumptionResult> enumeration value to indicate the results of the bookmark resumption request.</span></span> <span data-ttu-id="e4c24-132">可能的返回值为 <xref:System.Activities.BookmarkResumptionResult.Success>、<xref:System.Activities.BookmarkResumptionResult.NotReady> 和 <xref:System.Activities.BookmarkResumptionResult.NotFound>。</span><span class="sxs-lookup"><span data-stu-id="e4c24-132">The possible return values are <xref:System.Activities.BookmarkResumptionResult.Success>, <xref:System.Activities.BookmarkResumptionResult.NotReady>, and <xref:System.Activities.BookmarkResumptionResult.NotFound>.</span></span> <span data-ttu-id="e4c24-133">宿主和扩展可以使用此值来确定如何继续执行。</span><span class="sxs-lookup"><span data-stu-id="e4c24-133">Hosts and extensions can use this value to determine how to proceed.</span></span>
