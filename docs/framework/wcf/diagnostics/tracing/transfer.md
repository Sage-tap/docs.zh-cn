---
description: 了解详细信息：传输
title: 传输
ms.date: 03/30/2017
ms.assetid: dfcfa36c-d3bb-44b4-aa15-1c922c6f73e6
ms.openlocfilehash: ce88a71d87c7dd09f321ee58f603f7c4672a6df9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99758055"
---
# <a name="transfer"></a><span data-ttu-id="78085-103">传输</span><span class="sxs-lookup"><span data-stu-id="78085-103">Transfer</span></span>

<span data-ttu-id="78085-104">本主题介绍 Windows Communication Foundation (WCF) 活动跟踪模型中的传输。</span><span class="sxs-lookup"><span data-stu-id="78085-104">This topic describes transfer in the Windows Communication Foundation (WCF) activity tracing model.</span></span>  
  
## <a name="transfer-definition"></a><span data-ttu-id="78085-105">传输定义</span><span class="sxs-lookup"><span data-stu-id="78085-105">Transfer Definition</span></span>  

 <span data-ttu-id="78085-106">活动之间的传输表示终结点内相关活动中的事件之间的因果关系。</span><span class="sxs-lookup"><span data-stu-id="78085-106">Transfers between activities represent causal relationships between events in the related activities within endpoints.</span></span> <span data-ttu-id="78085-107">当两个活动之间存在控制流（例如方法调用跨越活动边界）时，这两个活动将与传输相关。</span><span class="sxs-lookup"><span data-stu-id="78085-107">Two activities are related with transfers when control flows between these activities, for example, a method call crossing activity boundaries.</span></span> <span data-ttu-id="78085-108">在 WCF 中，在服务上传入字节时，侦听活动会传输到接收字节活动，其中创建了消息对象。</span><span class="sxs-lookup"><span data-stu-id="78085-108">In WCF, when bytes are incoming on the service, the Listen At activity is transferred to the Receive Bytes activity where the message object is created.</span></span> <span data-ttu-id="78085-109">有关端到端跟踪方案及其各自的活动和跟踪设计的列表，请参阅 [端到端跟踪方案](end-to-end-tracing-scenarios.md)。</span><span class="sxs-lookup"><span data-stu-id="78085-109">For a list of end-to-end tracing scenarios, and their respective activity and tracing design, see [End-To-End Tracing Scenarios](end-to-end-tracing-scenarios.md).</span></span>  
  
 <span data-ttu-id="78085-110">若要发出传输跟踪，请在跟踪源中使用如下配置代码所示的 `ActivityTracing` 设置。</span><span class="sxs-lookup"><span data-stu-id="78085-110">To emit transfer traces, use the `ActivityTracing` setting on the trace source as demonstrated by the following configuration code.</span></span>  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
## <a name="using-transfer-to-correlate-activities-within-endpoints"></a><span data-ttu-id="78085-111">使用传输关联终结点内的活动</span><span class="sxs-lookup"><span data-stu-id="78085-111">Using Transfer to Correlate Activities Within Endpoints</span></span>  

 <span data-ttu-id="78085-112">用户可以通过活动和传输找出错误的根本原因。</span><span class="sxs-lookup"><span data-stu-id="78085-112">Activities and transfers permit the user to probabilistically locate the root cause of an error.</span></span> <span data-ttu-id="78085-113">例如，如果分别在组件 M 和 N 的活动 M 和 N 之间来回传输，并且在传回 M 之后 N 中发生崩溃，则可以得出结论，发生错误很可能是由于 N 将数据传回了 M。</span><span class="sxs-lookup"><span data-stu-id="78085-113">For example, if we transfer back and forth between activities M and N respectively in components M and N, and a crash happens in N right after the transfer back to M, we can draw the conclusion that it is likely due to N’s passing data back to M.</span></span>  
  
 <span data-ttu-id="78085-114">活动 M 和活动 N 之间存在控制流时，会从 M 向 N 发出传输跟踪。例如，由于存在跨越活动边界的方法调用，因而 N 会为 M 执行某些工作。</span><span class="sxs-lookup"><span data-stu-id="78085-114">A transfer trace is emitted from activity M to activity N when there is a flow of control between M and N. For example, N performs some work for M because of a method call crossing the activities’ boundaries.</span></span> <span data-ttu-id="78085-115">N 可能已存在或已创建。</span><span class="sxs-lookup"><span data-stu-id="78085-115">N may already exist or has been created.</span></span> <span data-ttu-id="78085-116">N 由 M 生成，此时 N 是新活动，为 M 执行某些工作。</span><span class="sxs-lookup"><span data-stu-id="78085-116">N is spawned by M when N is a new activity that performs some work for M.</span></span>  
  
 <span data-ttu-id="78085-117">从 M 到 N 的传输之后可能不会紧跟一个从 N 到 M 的反向传输。这是因为 M 可能会在 N 中生成一些工作，并且不会跟踪何时 N 将完成这些工作。</span><span class="sxs-lookup"><span data-stu-id="78085-117">A transfer from M to N may not be followed by a transfer back from N to M. This is because M can spawn some work in N and do not track when N completes that work.</span></span> <span data-ttu-id="78085-118">实际上，M 可以在 N 完成其任务之前终止。</span><span class="sxs-lookup"><span data-stu-id="78085-118">In fact, M can terminate before N completes its task.</span></span> <span data-ttu-id="78085-119">这种情况出现在 "打开 ServiceHost" 活动 (M) 中，该活动生成侦听器活动 (N) 然后终止。</span><span class="sxs-lookup"><span data-stu-id="78085-119">This happens in the "Open ServiceHost" activity (M) that spawns Listener activities (N) and then terminates.</span></span> <span data-ttu-id="78085-120">从 N 传回 M 意味着 N 已完成与 M 相关的工作。</span><span class="sxs-lookup"><span data-stu-id="78085-120">A transfer back from N to M means that N completed the work related to M.</span></span>  
  
 <span data-ttu-id="78085-121">N 可以继续执行与 M 无关的其他处理，例如继续从不同登录活动接收登录请求 (M) 的现有身份验证器活动 (N)。</span><span class="sxs-lookup"><span data-stu-id="78085-121">N can continue performing other processing unrelated to M, for example, an existing authenticator activity (N) that keeps receiving login requests (M) from different login activities.</span></span>  
  
 <span data-ttu-id="78085-122">活动 M 与 N 之间并不一定存在嵌套关系。发生这种情况可能有两个原因。</span><span class="sxs-lookup"><span data-stu-id="78085-122">A nesting relationship does not necessarily exist between activities M and N. This can happen due to two reasons.</span></span> <span data-ttu-id="78085-123">首先，虽然活动 M 启动了 N，但 M 并不监视 N 中执行的实际处理。其次，N 可能已经存在。</span><span class="sxs-lookup"><span data-stu-id="78085-123">First, when activity M does not monitor the actual processing performed in N although M initiated N. Second, when N already exists.</span></span>  
  
## <a name="example-of-transfers"></a><span data-ttu-id="78085-124">传输示例</span><span class="sxs-lookup"><span data-stu-id="78085-124">Example of Transfers</span></span>  

 <span data-ttu-id="78085-125">下面列出了两个传输示例。</span><span class="sxs-lookup"><span data-stu-id="78085-125">The following lists two transfer examples.</span></span>  
  
- <span data-ttu-id="78085-126">在创建服务主机时，构造函数将从调用代码获得控制权，或者调用代码将控制权转移给构造函数。</span><span class="sxs-lookup"><span data-stu-id="78085-126">When you create a service host, the constructor gains control from the calling code, or the calling code transfers to the constructor.</span></span> <span data-ttu-id="78085-127">构造函数执行完时，它将控制权返回给调用代码，或者构造函数将控制权转移回调用代码。</span><span class="sxs-lookup"><span data-stu-id="78085-127">When the constructor has finished executing, it returns control to the calling code, or the constructor transfers back to the calling code.</span></span> <span data-ttu-id="78085-128">这是嵌套关系时的情况。</span><span class="sxs-lookup"><span data-stu-id="78085-128">This is the case of a nested relationship.</span></span>  
  
- <span data-ttu-id="78085-129">侦听器开始处理传输数据时，它将创建一个新线程，并将相应的上下文传递到“接收字节”活动进行处理，并且传递控制权和数据。</span><span class="sxs-lookup"><span data-stu-id="78085-129">When a listener starts processing transport data, it creates a new thread and hands to the Receive Bytes activity the appropriate context for processing, passing control and data.</span></span> <span data-ttu-id="78085-130">该线程处理完请求后，接收字节活动不向侦听器传回任何内容。</span><span class="sxs-lookup"><span data-stu-id="78085-130">When that thread has finished processing the request, the Receive Bytes activity passes nothing back to the listener.</span></span> <span data-ttu-id="78085-131">在这种情况下，有传入的新线程活动而没有传出的新线程活动。</span><span class="sxs-lookup"><span data-stu-id="78085-131">In this case, we have a transfer in but no transfer out of the new thread activity.</span></span> <span data-ttu-id="78085-132">这两个活动相关，但不是嵌套关系。</span><span class="sxs-lookup"><span data-stu-id="78085-132">The two activities are related but not nested.</span></span>  
  
## <a name="activity-transfer-sequence"></a><span data-ttu-id="78085-133">活动传输序列</span><span class="sxs-lookup"><span data-stu-id="78085-133">Activity Transfer Sequence</span></span>  

 <span data-ttu-id="78085-134">格式正确的活动传输序列包含下列步骤。</span><span class="sxs-lookup"><span data-stu-id="78085-134">A well-formed activity transfer sequence includes the following steps.</span></span>  
  
1. <span data-ttu-id="78085-135">开始一个新活动（包括选择新的 gAId）。</span><span class="sxs-lookup"><span data-stu-id="78085-135">Begin a new activity, which consists of selecting a new gAId.</span></span>  
  
2. <span data-ttu-id="78085-136">发出从当前活动 ID 到该新 gAId 的传输跟踪</span><span class="sxs-lookup"><span data-stu-id="78085-136">Emit a transfer trace to that new gAId from the current activity ID</span></span>  
  
3. <span data-ttu-id="78085-137">在 TLS 中设置新 ID</span><span class="sxs-lookup"><span data-stu-id="78085-137">Set the new ID in TLS</span></span>  
  
4. <span data-ttu-id="78085-138">发出开始跟踪以指示新活动的开始。</span><span class="sxs-lookup"><span data-stu-id="78085-138">Emit a start trace to indicate the beginning of the new activity by.</span></span>  
  
5. <span data-ttu-id="78085-139">返回到原始活动包括下列步骤：</span><span class="sxs-lookup"><span data-stu-id="78085-139">Return to the original activity consists of the following:</span></span>  
  
6. <span data-ttu-id="78085-140">发出到原始 gAId 的传输跟踪</span><span class="sxs-lookup"><span data-stu-id="78085-140">Emit a transfer trace to the original gAId</span></span>  
  
7. <span data-ttu-id="78085-141">发出停止跟踪以指示新活动的结束</span><span class="sxs-lookup"><span data-stu-id="78085-141">Emit a Stop trace to indicate the end of the new activity</span></span>  
  
8. <span data-ttu-id="78085-142">将 TLS 设置为旧的 gAId。</span><span class="sxs-lookup"><span data-stu-id="78085-142">Set TLS to the old gAId.</span></span>  
  
 <span data-ttu-id="78085-143">下面的代码示例演示如何执行此操作。</span><span class="sxs-lookup"><span data-stu-id="78085-143">The following code example demonstrates how to do this.</span></span> <span data-ttu-id="78085-144">此示例假定，在传输到新活动时将进行阻止调用，该调用包括挂起/继续跟踪。</span><span class="sxs-lookup"><span data-stu-id="78085-144">This sample assumes a blocking call is made when transferring to the new activity, and includes suspend/resume traces.</span></span>  
  
```csharp
// 0. Create a trace source  
TraceSource ts = new TraceSource("myTS");  

// 1. remember existing ("ambient") activity for clean up  
Guid oldGuid = Trace.CorrelationManager.ActivityId;  
// this will be our new activity  
Guid newGuid = Guid.NewGuid();

// 2. call transfer, indicating that we are switching to the new AID  
ts.TraceTransfer(667, "Transferring.", newGuid);  

// 3. Suspend the current activity.  
ts.TraceEvent(TraceEventType.Suspend, 667, "Suspend: Activity " + i-1);  

// 4. set the new AID in TLS  
Trace.CorrelationManager.ActivityId = newGuid;  

// 5. Emit the start trace  
ts.TraceEvent(TraceEventType.Start, 667, "Boundary: Activity " + i);  

// trace something  
ts.TraceEvent(TraceEventType.Information, 667, "Hello from activity " + i);  

// Perform Work  
// some work.  
// Return  
ts.TraceEvent(TraceEventType.Information, 667, "Work complete on activity " + i);

// 6. Emit the transfer returning to the original activity  
ts.TraceTransfer(667, "Transferring Back.", oldGuid);  

// 7. Emit the End trace  
ts.TraceEvent(TraceEventType.Stop, 667, "Boundary: Activity " + i);  

// 8. Change the tls variable to the original AID  
Trace.CorrelationManager.ActivityId = oldGuid;

// 9. Resume the old activity  
ts.TraceEvent(TraceEventType.Resume, 667, "Resume: Activity " + i-1);  
```  
  
## <a name="see-also"></a><span data-ttu-id="78085-145">请参阅</span><span class="sxs-lookup"><span data-stu-id="78085-145">See also</span></span>

- [<span data-ttu-id="78085-146">配置跟踪</span><span class="sxs-lookup"><span data-stu-id="78085-146">Configuring Tracing</span></span>](configuring-tracing.md)
- [<span data-ttu-id="78085-147">使用服务跟踪查看器查看相关跟踪和进行故障诊断</span><span class="sxs-lookup"><span data-stu-id="78085-147">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [<span data-ttu-id="78085-148">端到端跟踪方案</span><span class="sxs-lookup"><span data-stu-id="78085-148">End-To-End Tracing Scenarios</span></span>](end-to-end-tracing-scenarios.md)
- [<span data-ttu-id="78085-149">服务跟踪查看器工具 (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="78085-149">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../service-trace-viewer-tool-svctraceviewer-exe.md)
