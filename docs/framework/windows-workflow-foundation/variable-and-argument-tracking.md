---
description: 了解详细信息：变量和参数跟踪
title: 变量和自变量跟踪
ms.date: 03/30/2017
ms.assetid: 8f3d9d30-d899-49aa-b7ce-a8d0d32c4ff0
ms.openlocfilehash: f2663e585ca280739f9c4ec176c31cf1d7c30657
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754974"
---
# <a name="variable-and-argument-tracking"></a><span data-ttu-id="1b74c-103">变量和自变量跟踪</span><span class="sxs-lookup"><span data-stu-id="1b74c-103">Variable and Argument Tracking</span></span>

<span data-ttu-id="1b74c-104">当跟踪工作流的执行时，提取数据往往很有用。</span><span class="sxs-lookup"><span data-stu-id="1b74c-104">When tracking the execution of a workflow, it is often useful to extract data.</span></span> <span data-ttu-id="1b74c-105">这在访问跟踪记录后续执行时可提供其他上下文。</span><span class="sxs-lookup"><span data-stu-id="1b74c-105">This provides additional context when accessing a tracking record post execution.</span></span> <span data-ttu-id="1b74c-106">在 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 中，你可以使用跟踪在工作流的任意活动范围内提取所有可见变量或自变量。</span><span class="sxs-lookup"><span data-stu-id="1b74c-106">In [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], you can extract any visible variable or argument within the scope of any activity in a workflow using tracking.</span></span> <span data-ttu-id="1b74c-107">跟踪配置文件简化了对数据的提取。</span><span class="sxs-lookup"><span data-stu-id="1b74c-107">Tracking profiles make it easy to extract data.</span></span>  
  
## <a name="variables-and-arguments"></a><span data-ttu-id="1b74c-108">变量和自变量</span><span class="sxs-lookup"><span data-stu-id="1b74c-108">Variables and Arguments</span></span>  

 <span data-ttu-id="1b74c-109">变量和参数在活动发出 ActivityStateRecord 时提取。</span><span class="sxs-lookup"><span data-stu-id="1b74c-109">Variables and arguments are extracted when an activity emits an ActivityStateRecord.</span></span>  <span data-ttu-id="1b74c-110">仅当变量位于活动范围中时，才能提取该变量。</span><span class="sxs-lookup"><span data-stu-id="1b74c-110">A variable is available for extraction only if it is within the scope of the activity.</span></span> <span data-ttu-id="1b74c-111">按如下方式指定将在活动中提取的变量：</span><span class="sxs-lookup"><span data-stu-id="1b74c-111">A variable to be extracted within an activity is specified in the following manner:</span></span>  
  
- <span data-ttu-id="1b74c-112">如果变量用变量名称指定，跟踪则在正跟踪的当前活动和父活动中查找变量。</span><span class="sxs-lookup"><span data-stu-id="1b74c-112">If a variable is specified by the variable name, then tracking looks for the variable within the current activity being tracked and in parent activities.</span></span> <span data-ttu-id="1b74c-113">系统将在当前活动范围和父范围中搜索变量。</span><span class="sxs-lookup"><span data-stu-id="1b74c-113">The variable is searched in current activity scope and in parent scope.</span></span>  
  
- <span data-ttu-id="1b74c-114">如果要提取的变量使用 name = " \* " 指定，则提取正在跟踪的当前活动中的所有变量。</span><span class="sxs-lookup"><span data-stu-id="1b74c-114">If variables to be extracted are specified by using name="\*", then all variables within the current activity being tracked are extracted.</span></span> <span data-ttu-id="1b74c-115">此种情况下，将不会提取范围中在父活动中定义的变量。</span><span class="sxs-lookup"><span data-stu-id="1b74c-115">In this case variables that are in scope but defined in parent activities are not extracted.</span></span>  
  
 <span data-ttu-id="1b74c-116">当提取自变量时，提取的自变量依赖于活动状态。</span><span class="sxs-lookup"><span data-stu-id="1b74c-116">When extracting arguments, the arguments extracted depend on the state of the activity.</span></span> <span data-ttu-id="1b74c-117">当活动状态为 Executing 时，只能提取 `InArguments`。</span><span class="sxs-lookup"><span data-stu-id="1b74c-117">When the state of an activity is Executing, then only the `InArguments` are available for extraction.</span></span> <span data-ttu-id="1b74c-118">对于任何其他活动状态（Closed、Faulted、Canceled），则可以提取所有自变量，即 InArguments 和 OutArguments。</span><span class="sxs-lookup"><span data-stu-id="1b74c-118">For any other activity state (Closed, Faulted, Canceled), all arguments, both InArguments and OutArguments, are available for extraction.</span></span>  
  
 <span data-ttu-id="1b74c-119">下面的示例演示用于在发出活动的 `Closed` 跟踪记录时提取变量和自变量的活动状态查询。</span><span class="sxs-lookup"><span data-stu-id="1b74c-119">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="1b74c-120">变量和自变量只能使用 <xref:System.Activities.Tracking.ActivityStateRecord> 来提取，因此使用 <xref:System.Activities.Tracking.ActivityStateQuery> 在跟踪配置文件内进行订阅。</span><span class="sxs-lookup"><span data-stu-id="1b74c-120">Variables and arguments can be extracted only with an <xref:System.Activities.Tracking.ActivityStateRecord> and thus are subscribed to within a tracking profile using <xref:System.Activities.Tracking.ActivityStateQuery>.</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <variables>  
    <variable name="FromAddress"/>  
  </variables>  
  <arguments>  
    <argument name="Result"/>  
  </arguments>  
</activityStateQuery>  
```  
  
## <a name="protecting-information-stored-within-variables-and-arguments"></a><span data-ttu-id="1b74c-121">保护存储在变量和参数中的信息</span><span class="sxs-lookup"><span data-stu-id="1b74c-121">Protecting Information Stored Within Variables and Arguments</span></span>  

 <span data-ttu-id="1b74c-122">默认情况下，跟踪变量或自变量对 WF 运行时可见。</span><span class="sxs-lookup"><span data-stu-id="1b74c-122">A tracked variable or argument is by default made visible by the WF runtime.</span></span> <span data-ttu-id="1b74c-123">工作流开发人员可以采取以下步骤，阻止访问这些变量或参数：</span><span class="sxs-lookup"><span data-stu-id="1b74c-123">A workflow developer can protect it from being accessed by taking the following steps:</span></span>  
  
1. <span data-ttu-id="1b74c-124">对变量的值进行加密。</span><span class="sxs-lookup"><span data-stu-id="1b74c-124">Encrypt the value of a variable.</span></span>  
  
2. <span data-ttu-id="1b74c-125">控制跟踪配置文件的创作，以阻止提取变量或参数。</span><span class="sxs-lookup"><span data-stu-id="1b74c-125">Control the authoring of a tracking profile to prevent the extraction of a variable or argument.</span></span>  
  
3. <span data-ttu-id="1b74c-126">对于自定义跟踪参与者，请确保 WF 代码不会泄露存储在变量或参数中的敏感信息。</span><span class="sxs-lookup"><span data-stu-id="1b74c-126">For custom tracking participants ensure that the WF code does not disclose sensitive information that is stored in variables or arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b74c-127">请参阅</span><span class="sxs-lookup"><span data-stu-id="1b74c-127">See also</span></span>

- <span data-ttu-id="1b74c-128">[Windows Server App Fabric 监视](/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="1b74c-128">[Windows Server App Fabric Monitoring](/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="1b74c-129">[用 App Fabric 监视应用程序](/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="1b74c-129">[Monitoring Applications with App Fabric](/previous-versions/appfabric/ee677276(v=azure.10))</span></span>
