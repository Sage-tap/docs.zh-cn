---
description: 了解有关 WCF 的详细信息： <workflow>
title: <workflow> WCF 的
ms.date: 03/30/2017
ms.assetid: c0443eba-d3b4-4fae-886e-9878daf77691
ms.openlocfilehash: 44391017b98bdbe76981c695c22ae68b048c3050
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682379"
---
# <a name="workflow-of-wcf"></a><span data-ttu-id="de989-103">\<workflow> WCF 的</span><span class="sxs-lookup"><span data-stu-id="de989-103">\<workflow> of WCF</span></span>

<span data-ttu-id="de989-104">配置一个跟踪参与者，它侦听直接从运行时发出的跟踪记录，并按照配置跟踪参与者的任何方式处理这些记录。</span><span class="sxs-lookup"><span data-stu-id="de989-104">Configure a tracking participant that listens to the tracking records being emitted from the runtime directly and process them in whatever way it was configured.</span></span> <span data-ttu-id="de989-105">这包括写入特定输出（例如，文件、控制台、ETW）、处理/聚合记录或可能需要的任何其他组合。</span><span class="sxs-lookup"><span data-stu-id="de989-105">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="de989-106">有关工作流跟踪和跟踪参与者的详细信息，请参阅 [工作流跟踪和](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) 跟踪和 [跟踪参与者](../../../windows-workflow-foundation/tracking-participants.md)。</span><span class="sxs-lookup"><span data-stu-id="de989-106">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../windows-workflow-foundation/tracking-participants.md).</span></span>  
  
 \<system.serviceModel>  
\<tracking>  
\<participants>  
\<add>  
  
## <a name="syntax"></a><span data-ttu-id="de989-107">语法</span><span class="sxs-lookup"><span data-stu-id="de989-107">Syntax</span></span>  
  
```xml  
<tracking>
  <participants>
    <add name="String"
         profileName="String"
         type="String" />
  </participants>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de989-108">特性和元素</span><span class="sxs-lookup"><span data-stu-id="de989-108">Attributes and Elements</span></span>  

 <span data-ttu-id="de989-109">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="de989-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de989-110">特性</span><span class="sxs-lookup"><span data-stu-id="de989-110">Attributes</span></span>  
  
|<span data-ttu-id="de989-111">元素</span><span class="sxs-lookup"><span data-stu-id="de989-111">Element</span></span>|<span data-ttu-id="de989-112">说明</span><span class="sxs-lookup"><span data-stu-id="de989-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="de989-113">name</span><span class="sxs-lookup"><span data-stu-id="de989-113">name</span></span>|<span data-ttu-id="de989-114">一个字符串，指定跟踪参与者的名称。</span><span class="sxs-lookup"><span data-stu-id="de989-114">A string that specifies the name of a tracking participant.</span></span>|  
|<span data-ttu-id="de989-115">profileName</span><span class="sxs-lookup"><span data-stu-id="de989-115">profileName</span></span>|<span data-ttu-id="de989-116">一个字符串，指定跟踪配置文件的名称，该跟踪配置文件定义跟踪参与者已订阅的跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="de989-116">A string that specifies the name of the tracking profile which defines the tracking records the tracking participant has subscribed to.</span></span>|  
|<span data-ttu-id="de989-117">type</span><span class="sxs-lookup"><span data-stu-id="de989-117">type</span></span>|<span data-ttu-id="de989-118">一个字符串，指定跟踪参与者的类型。</span><span class="sxs-lookup"><span data-stu-id="de989-118">A string that specifies the type of a tracking participant.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="de989-119">子元素</span><span class="sxs-lookup"><span data-stu-id="de989-119">Child Elements</span></span>  

 <span data-ttu-id="de989-120">无。</span><span class="sxs-lookup"><span data-stu-id="de989-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="de989-121">父元素</span><span class="sxs-lookup"><span data-stu-id="de989-121">Parent Elements</span></span>  
  
|<span data-ttu-id="de989-122">元素</span><span class="sxs-lookup"><span data-stu-id="de989-122">Element</span></span>|<span data-ttu-id="de989-123">说明</span><span class="sxs-lookup"><span data-stu-id="de989-123">Description</span></span>|  
|-------------|-----------------|  
|[\<participants>](../windows-workflow-foundation/participants.md)|<span data-ttu-id="de989-124">跟踪参与者的列表</span><span class="sxs-lookup"><span data-stu-id="de989-124">A list of tracking participants</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de989-125">备注</span><span class="sxs-lookup"><span data-stu-id="de989-125">Remarks</span></span>  

 <span data-ttu-id="de989-126">跟踪参与者用于获取从工作流发出的跟踪数据并将其存储在不同的媒体中。</span><span class="sxs-lookup"><span data-stu-id="de989-126">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="de989-127">同样，也可以在跟踪参与者中执行对跟踪记录的任何后续处理。</span><span class="sxs-lookup"><span data-stu-id="de989-127">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="de989-128">多个跟踪参与者可同时使用跟踪事件。</span><span class="sxs-lookup"><span data-stu-id="de989-128">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="de989-129">每个跟踪参与者都可与不同的跟踪配置文件关联。</span><span class="sxs-lookup"><span data-stu-id="de989-129">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="de989-130">提供了将跟踪记录写入 ETW 会话的标准跟踪参与者。</span><span class="sxs-lookup"><span data-stu-id="de989-130">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="de989-131">通过在配置文件中添加特定于跟踪的行为，可以对工作流服务配置参与者。</span><span class="sxs-lookup"><span data-stu-id="de989-131">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="de989-132">通过启用 ETW 跟踪参与者，可以在事件查看器中查看跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="de989-132">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="de989-133">如果这不能满足您的需求，您还可以编写自定义跟踪参与者。</span><span class="sxs-lookup"><span data-stu-id="de989-133">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de989-134">示例</span><span class="sxs-lookup"><span data-stu-id="de989-134">Example</span></span>  

 <span data-ttu-id="de989-135">下面的配置示例演示在 Web.config 文件中配置的标准 ETW 跟踪参与者。</span><span class="sxs-lookup"><span data-stu-id="de989-135">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="de989-136">ETW 跟踪参与者用于将跟踪记录写入 ETW 的提供程序 ID 在 `<diagnostics>` 节中定义。</span><span class="sxs-lookup"><span data-stu-id="de989-136">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the `<diagnostics>` section.</span></span> <span data-ttu-id="de989-137">跟踪参与者具有一个与其关联的配置文件，用来指定跟踪参与者已订阅的跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="de989-137">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="de989-138">它由 `profileName` 元素的 `<add>` 特性进行定义。</span><span class="sxs-lookup"><span data-stu-id="de989-138">This is defined by the `profileName` attribute of the `<add>` element.</span></span> <span data-ttu-id="de989-139">定义这些内容后，跟踪参与者将被添加到 `<etwTracking>` 服务行为中。</span><span class="sxs-lookup"><span data-stu-id="de989-139">Once these are defined, the Tracking Participant is added to the `<etwTracking>` service behavior.</span></span> <span data-ttu-id="de989-140">这会将所选跟踪参与者添加到工作流实例的扩展中，以便它们开始接收跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="de989-140">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
```xml  
<configuration>
  <system.web>
    <compilation targetFrameworkMoniker=".NETFramework,Version=v4.0" />
  </system.web>
  <system.serviceModel>
    <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />
    <tracking>
      <participants>
        <add name="EtwTrackingParticipant"
             type="System.Activities.Tracking.EtwTrackingParticipant, System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
             profileName="HealthMonitoring_Tracking_Profile" />
      </participants>
    </tracking>
    <behaviors>
      <serviceBehaviors>
        <behavior>
          <etwTracking profileName="Sample Tracking Profile" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="de989-141">请参阅</span><span class="sxs-lookup"><span data-stu-id="de989-141">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="de989-142">工作流跟踪</span><span class="sxs-lookup"><span data-stu-id="de989-142">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="de989-143">跟踪参与者</span><span class="sxs-lookup"><span data-stu-id="de989-143">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
