---
description: 了解详细信息：获取 WorkflowInstanceId
title: 获取 WorkflowInstanceId
ms.date: 03/30/2017
ms.assetid: bd7eea3b-1c28-4b84-9a67-003bc553aa81
ms.openlocfilehash: 3be6c36e6a6996a11ad1e26414fa25f1e32399e3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755312"
---
# <a name="get-workflowinstanceid"></a><span data-ttu-id="dd71f-103">获取 WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="dd71f-103">Get WorkflowInstanceId</span></span>

<span data-ttu-id="dd71f-104">此示例演示如何使用自定义活动 `GetWorkflowInstanceId` 返回工作流实例 ID。</span><span class="sxs-lookup"><span data-stu-id="dd71f-104">This sample demonstrates how to use the custom activity, `GetWorkflowInstanceId` to return the workflow instance ID.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="dd71f-105">演示</span><span class="sxs-lookup"><span data-stu-id="dd71f-105">Demonstrates</span></span>  

 <span data-ttu-id="dd71f-106">自定义活动开发，如何访问工作流实例。</span><span class="sxs-lookup"><span data-stu-id="dd71f-106">Custom activity development, how to access the workflow instance.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="dd71f-107">讨论 (Discussion)</span><span class="sxs-lookup"><span data-stu-id="dd71f-107">Discussion</span></span>  

 <span data-ttu-id="dd71f-108">若要获取某个正在运行的工作流的实例 ID，则需要编写代码。</span><span class="sxs-lookup"><span data-stu-id="dd71f-108">Getting the instance ID of a running workflow requires writing code.</span></span> <span data-ttu-id="dd71f-109">如果您想要编写一个完全声明性的工作流，则需要一个可返回工作流实例 ID 的活动，以便于可在工作流中引用该活动，以提供完全声明性的工作流创作体验。</span><span class="sxs-lookup"><span data-stu-id="dd71f-109">If you want to write a fully-declarative workflow, then you need an activity that can return the workflow instance ID so that the activity can be referenced in the workflow to provide a fully-declarative workflow authoring experience.</span></span> <span data-ttu-id="dd71f-110">许多方案需要访问实例 ID：一些示例用于记录或审核目的，或通过将实例 ID 提供回到客户端以供将来关联（例如，通过在 SendReply 活动内部使用此活动），用于执行应用程序级相关性。</span><span class="sxs-lookup"><span data-stu-id="dd71f-110">Many scenarios require access to the instance ID: a few examples are for logging or auditing purposes or for doing application-level correlation by providing the instance ID back to a client for future association (for example, by using this activity inside a SendReply activity).</span></span>  
  
 <span data-ttu-id="dd71f-111">`GetWorkflowInstanceId` 作为一个 <xref:System.Activities.CodeActivity%601> 实现，因为它必须返回 <xref:System.Guid> 类型的值，而且它必须具有对 <xref:System.Activities.CodeActivityContext> 的访问权以获取工作流的实例 ID。</span><span class="sxs-lookup"><span data-stu-id="dd71f-111">`GetWorkflowInstanceId` is implemented as a <xref:System.Activities.CodeActivity%601> because it must return a value of type <xref:System.Guid>, and it must have access to the <xref:System.Activities.CodeActivityContext> for getting the workflow’s instance ID.</span></span> <span data-ttu-id="dd71f-112">它的实现是相当基本的。</span><span class="sxs-lookup"><span data-stu-id="dd71f-112">Its implementation is fairly basic.</span></span>  
  
```csharp  
public sealed class GetWorkflowInstanceId : CodeActivity<Guid>  
{  
    protected override Guid Execute(CodeActivityContext context)  
    {  
        return context.WorkflowInstanceId;  
    }  
}
```  
  
> [!IMPORTANT]
> <span data-ttu-id="dd71f-113">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="dd71f-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="dd71f-114">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="dd71f-114">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="dd71f-115">如果此目录不存在，请参阅[Windows Communication Foundation (wcf) ，并 Windows Workflow Foundation (的 WF](https://www.microsoft.com/download/details.aspx?id=21459)) .NET Framework Windows Communication Foundation ([!INCLUDE[wf1](../../../../includes/wf1-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd71f-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="dd71f-116">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="dd71f-116">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\GetWorkflowInstanceId`
