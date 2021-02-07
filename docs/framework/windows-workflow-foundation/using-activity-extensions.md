---
description: 了解详细信息：使用活动扩展
title: 使用活动扩展
ms.date: 03/30/2017
ms.assetid: 500eb96a-c009-4247-b6b5-b36faffdf715
ms.openlocfilehash: d0286850bf685497d3a2471a3b4e0db4630070b1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755065"
---
# <a name="using-activity-extensions"></a><span data-ttu-id="e8cd1-103">使用活动扩展</span><span class="sxs-lookup"><span data-stu-id="e8cd1-103">Using Activity Extensions</span></span>

<span data-ttu-id="e8cd1-104">活动可与工作流应用程序扩展进行交互，这些扩展允许主机提供未在工作流中显式建模的其他功能。</span><span class="sxs-lookup"><span data-stu-id="e8cd1-104">Activities can interact with workflow application extensions that allow the host to provide additional functionality that is not explicitly modeled in the workflow.</span></span>  <span data-ttu-id="e8cd1-105">本主题描述如何创建和使用扩展以计算活动的执行次数。</span><span class="sxs-lookup"><span data-stu-id="e8cd1-105">This topic describes how to create and use an extension to count the number of times the activity executes.</span></span>

### <a name="to-use-an-activity-extension-to-count-executions"></a><span data-ttu-id="e8cd1-106">使用活动扩展来计算执行次数</span><span class="sxs-lookup"><span data-stu-id="e8cd1-106">To use an activity extension to count executions</span></span>

1. <span data-ttu-id="e8cd1-107">打开 Visual Studio 2010。</span><span class="sxs-lookup"><span data-stu-id="e8cd1-107">Open Visual Studio 2010.</span></span> <span data-ttu-id="e8cd1-108">选择 " **新建**"、" **项目**"。</span><span class="sxs-lookup"><span data-stu-id="e8cd1-108">Select **New**, **Project**.</span></span> <span data-ttu-id="e8cd1-109">在 **Visual c #** 节点下，选择 " **工作流**"。</span><span class="sxs-lookup"><span data-stu-id="e8cd1-109">Under the **Visual C#** node, select **Workflow**.</span></span>  <span data-ttu-id="e8cd1-110">从模板列表中选择 " **工作流控制台应用程序** "。</span><span class="sxs-lookup"><span data-stu-id="e8cd1-110">Select **Workflow Console Application** from the list of templates.</span></span> <span data-ttu-id="e8cd1-111">将项目命名为 `Extensions`。</span><span class="sxs-lookup"><span data-stu-id="e8cd1-111">Name the project `Extensions`.</span></span> <span data-ttu-id="e8cd1-112">单击“确定”以创建该项目  。</span><span class="sxs-lookup"><span data-stu-id="e8cd1-112">Click **OK** to create the project.</span></span>

2. <span data-ttu-id="e8cd1-113">`using`在 Program.cs 文件中为 **system.object** 命名空间添加语句。</span><span class="sxs-lookup"><span data-stu-id="e8cd1-113">Add a `using` statement in the Program.cs file for the **System.Collections.Generic** namespace.</span></span>

    ```csharp
    using System.Collections.Generic;
    ```

3. <span data-ttu-id="e8cd1-114">在 Program.cs 文件中，创建一个名为 **ExecutionCountExtension** 的新类。</span><span class="sxs-lookup"><span data-stu-id="e8cd1-114">In the Program.cs file, create a new class named **ExecutionCountExtension**.</span></span> <span data-ttu-id="e8cd1-115">下面的代码创建一个在调用其 **Register** 方法时跟踪实例 id 的工作流扩展。</span><span class="sxs-lookup"><span data-stu-id="e8cd1-115">The following code creates a workflow extension that tracks instance IDs when its **Register** method is called.</span></span>

    ```csharp
    // This extension collects a list of workflow Ids
    public class ExecutionCountExtension
    {
        IList<Guid> instances = new List<Guid>();

        public int ExecutionCount
        {
            get
            {
                return this.instances.Count;
            }
        }

        public IEnumerable<Guid> InstanceIds
        {
            get
            {
                return this.instances;
            }
        }

        public void Register(Guid activityInstanceId)
        {
            if (!this.instances.Contains<Guid>(activityInstanceId))
            {
                instances.Add(activityInstanceId);
            }
        }
    }
    ```

4. <span data-ttu-id="e8cd1-116">创建使用 **ExecutionCountExtension** 的活动。</span><span class="sxs-lookup"><span data-stu-id="e8cd1-116">Create an activity that consumes the **ExecutionCountExtension**.</span></span> <span data-ttu-id="e8cd1-117">下面的代码定义一个活动，该活动从运行时检索 **ExecutionCountExtension** 对象，并在执行活动时调用其 **Register** 方法。</span><span class="sxs-lookup"><span data-stu-id="e8cd1-117">The following code defines an activity that retrieves the **ExecutionCountExtension** object from the runtime and calls its **Register** method when the activity executes.</span></span>

    ```csharp
    // Activity that consumes an extension provided by the host. If the extension is available
    // in the context, it will invoke (in this case, registers the Id of the executing workflow)
    public class MyActivity: CodeActivity
    {
        protected override void Execute(CodeActivityContext context)
        {
            ExecutionCountExtension ext = context.GetExtension<ExecutionCountExtension>();
            if (ext != null)
            {
                ext.Register(context.WorkflowInstanceId);
            }

        }
    }
    ```

5. <span data-ttu-id="e8cd1-118">在 program.cs 文件的 **Main** 方法中实现活动。</span><span class="sxs-lookup"><span data-stu-id="e8cd1-118">Implement the activity in the **Main** method of the program.cs file.</span></span> <span data-ttu-id="e8cd1-119">以下代码包含用于生成两个不同的工作流、将每个工作流执行多次以及显示扩展中包含的结果数据的方法。</span><span class="sxs-lookup"><span data-stu-id="e8cd1-119">The following code contains methods to generate two different workflows, execute each workflow several times, and display the resulting data that is contained in the extension.</span></span>

    ```csharp
    class Program
    {
        // Creates a workflow that uses the activity that consumes the extension
        static Activity CreateWorkflow1()
        {
            return new Sequence
            {
                Activities =
                {
                    new MyActivity()
                }
            };
        }

        // Creates a workflow that uses two instances of the activity that consumes the extension
        static Activity CreateWorkflow2()
        {
            return new Sequence
            {
                Activities =
                {
                    new MyActivity(),
                    new MyActivity()
                }
            };
        }

        static void Main(string[] args)
        {
            // create the extension
            ExecutionCountExtension executionCountExt = new ExecutionCountExtension();

            // configure the first invoker and execute 3 times
            WorkflowInvoker invoker = new WorkflowInvoker(CreateWorkflow1());
            invoker.Extensions.Add(executionCountExt);
            invoker.Invoke();
            invoker.Invoke();
            invoker.Invoke();

            // configure the second invoker and execute 2 times
            WorkflowInvoker invoker2 = new WorkflowInvoker(CreateWorkflow2());
            invoker2.Extensions.Add(executionCountExt);
            invoker2.Invoke();
            invoker2.Invoke();

            // show the data in the extension
            Console.WriteLine("Executed {0} times", executionCountExt.ExecutionCount);
            executionCountExt.InstanceIds.ToList().ForEach(i => Console.WriteLine("...{0}", i));
        }
    }
    ```
