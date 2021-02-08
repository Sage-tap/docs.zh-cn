---
description: 了解详细信息：活动库
title: 活动库
ms.date: 03/30/2017
ms.assetid: 5323e9d4-71d6-47eb-bfa6-31feac62044d
ms.openlocfilehash: 7e59846d34b63683266fed2c4ec1ad4ed5cb9566
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792604"
---
# <a name="activity-library"></a><span data-ttu-id="fad48-103">活动库</span><span class="sxs-lookup"><span data-stu-id="fad48-103">Activity Library</span></span>

<span data-ttu-id="fad48-104">本部分包含的示例演示了 Windows Workflow Foundation (WF) 中的高级自定义活动。</span><span class="sxs-lookup"><span data-stu-id="fad48-104">This section contains samples that demonstrate advanced custom activities in Windows Workflow Foundation (WF).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fad48-105">本节内容</span><span class="sxs-lookup"><span data-stu-id="fad48-105">In This Section</span></span>

 [<span data-ttu-id="fad48-106">SendMail 自定义活动</span><span class="sxs-lookup"><span data-stu-id="fad48-106">SendMail Custom Activity</span></span>](sendmail-custom-activity.md)  
 <span data-ttu-id="fad48-107">演示如何创建派生自 <xref:System.Activities.AsyncCodeActivity> 的自定义活动，以使用 SMTP 发送邮件供在工作流应用程序内使用。</span><span class="sxs-lookup"><span data-stu-id="fad48-107">Demonstrates how to create a custom activity that derives from <xref:System.Activities.AsyncCodeActivity> to send mail using SMTP for use within a workflow application.</span></span>  
  
 [<span data-ttu-id="fad48-108">限制并行 ForEach</span><span class="sxs-lookup"><span data-stu-id="fad48-108">Throttled Parallel ForEach</span></span>](throttled-parallel-foreach.md)  
 <span data-ttu-id="fad48-109">演示 `ThrottleParallelForEach` 活动与 <xref:System.Activities.Statements.ParallelForEach%601> 活动的相似之处，二者的不同之处在于，前者允许设置一个并发因子来限制要同时执行的分支的数量。</span><span class="sxs-lookup"><span data-stu-id="fad48-109">Demonstrates how the `ThrottleParallelForEach` activity is similar to the <xref:System.Activities.Statements.ParallelForEach%601> activity with the one exception that it allows setting a concurrency factor to restrict the number of simultaneous branches to execute.</span></span>
  
 [<span data-ttu-id="fad48-110">数据库访问活动</span><span class="sxs-lookup"><span data-stu-id="fad48-110">Database Access Activities</span></span>](database-access-activities.md)  
 <span data-ttu-id="fad48-111">演示如何创建活动，以允许访问数据库以检索或修改信息，并使用 [ADO.NET](../../data/adonet/index.md) 来访问数据库。</span><span class="sxs-lookup"><span data-stu-id="fad48-111">Demonstrates how to create activities that allow accessing databases to retrieve or modify information and use [ADO.NET](../../data/adonet/index.md) to access the database.</span></span>  
  
 [<span data-ttu-id="fad48-112">.NET Framework 4.5 中的外部化策略活动</span><span class="sxs-lookup"><span data-stu-id="fad48-112">Externalized Policy Activity in .NET Framework 4.5</span></span>](externalized-policy-activity-in-net-framework-4-5.md)  
 <span data-ttu-id="fad48-113">演示 ExternalizedPolicy4 活动如何 <xref:System.Workflow.Activities.Rules.RuleSet> [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] 通过使用在 wf 3.5 中随附的规则引擎，在 Windows Workflow Foundation wf 4.5 (中，通过) 中的 wf 直接执行 .NET Framework 3.5 (WF) 3.5 中的现有 Windows Workflow Foundation。</span><span class="sxs-lookup"><span data-stu-id="fad48-113">Demonstrates how the ExternalizedPolicy4 activity allows executing existing Windows Workflow Foundation in .NET Framework 3.5 (WF 3.5) <xref:System.Workflow.Activities.Rules.RuleSet> objects in Windows Workflow Foundation in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF 4.5) directly by using the rules engine that is shipped in WF 3.5.</span></span>
  
 [<span data-ttu-id="fad48-114">非泛型 ForEach</span><span class="sxs-lookup"><span data-stu-id="fad48-114">Non-Generic ForEach</span></span>](non-generic-foreach.md)  
 <span data-ttu-id="fad48-115">演示了如何创建非泛型版本的 <xref:System.Activities.Statements.ForEach%601> 活动。</span><span class="sxs-lookup"><span data-stu-id="fad48-115">Demonstrates how to create a non-generic version of the <xref:System.Activities.Statements.ForEach%601> activity.</span></span>  
  
 [<span data-ttu-id="fad48-116">非泛型 ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="fad48-116">Non-Generic ParallelForEach</span></span>](non-generic-parallelforeach.md)  
 <span data-ttu-id="fad48-117">演示了如何创建非泛型版本的 <xref:System.Activities.Statements.ParallelForEach%601> 活动。</span><span class="sxs-lookup"><span data-stu-id="fad48-117">Demonstrates how to create a non-generic version of the <xref:System.Activities.Statements.ParallelForEach%601> activity.</span></span>  
  
 [<span data-ttu-id="fad48-118">获取 WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="fad48-118">Get WorkflowInstanceId</span></span>](get-workflowinstanceid.md)  
 <span data-ttu-id="fad48-119">演示如何使用自定义活动 `GetWorkflowInstanceId` 返回工作流实例 ID。</span><span class="sxs-lookup"><span data-stu-id="fad48-119">Demonstrates how to use the custom activity, `GetWorkflowInstanceId`, to return the workflow instance ID.</span></span>
