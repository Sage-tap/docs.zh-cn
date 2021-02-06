---
description: 了解更多：传播
title: 传播
ms.date: 03/30/2017
ms.assetid: f8181e75-d693-48d1-b333-a776ad3b382a
ms.openlocfilehash: 43ecbf7b8db66f26accc058501730300a2891284
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99635592"
---
# <a name="propagation"></a><span data-ttu-id="69512-103">传播</span><span class="sxs-lookup"><span data-stu-id="69512-103">Propagation</span></span>

<span data-ttu-id="69512-104">本主题介绍 Windows Communication Foundation (WCF) 跟踪模型中的活动传播。</span><span class="sxs-lookup"><span data-stu-id="69512-104">This topic describes activity propagation in the Windows Communication Foundation (WCF) tracing model.</span></span>  
  
## <a name="using-propagation-to-correlate-activities-across-endpoints"></a><span data-ttu-id="69512-105">使用传播关联终结点之间的活动</span><span class="sxs-lookup"><span data-stu-id="69512-105">Using Propagation to Correlate Activities Across Endpoints</span></span>  

 <span data-ttu-id="69512-106">传播可向用户提供应用程序终结点之间相同处理单元的错误跟踪的直接关联，如请求。</span><span class="sxs-lookup"><span data-stu-id="69512-106">Propagation provides the user with direct correlation of error traces for the same unit of processing across application endpoints, for example, a request.</span></span> <span data-ttu-id="69512-107">在不同终结点为相同处理单元发出的错误将被分组到相同的活动中，甚至跨应用程序域。</span><span class="sxs-lookup"><span data-stu-id="69512-107">Errors emitted at different endpoints for the same unit of processing are grouped in the same activity, even across application domains.</span></span> <span data-ttu-id="69512-108">这是通过活动 ID 在消息头中的传播实现的。</span><span class="sxs-lookup"><span data-stu-id="69512-108">This is done through propagation of the activity ID in the message headers.</span></span> <span data-ttu-id="69512-109">因此，如果客户端由于服务器内部错误而超时，则这两个错误都会显示在同一活动中以便直接关联。</span><span class="sxs-lookup"><span data-stu-id="69512-109">Therefore, if a client times out because of an internal error in the server, both errors appear in the same activity for direct correlation.</span></span>  
  
 <span data-ttu-id="69512-110">为此，可以按前面示例所示使用 `ActivityTracing` 设置。</span><span class="sxs-lookup"><span data-stu-id="69512-110">To do this, use the `ActivityTracing` setting as demonstrated in the previous example.</span></span> <span data-ttu-id="69512-111">此外，在所有终结点处设置 `propagateActivity` 跟踪源的 `System.ServiceModel` 属性。</span><span class="sxs-lookup"><span data-stu-id="69512-111">In addition, set the `propagateActivity` attribute for the `System.ServiceModel` trace source at all endpoints.</span></span>  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing" propagateActivity="true" >  
```  
  
 <span data-ttu-id="69512-112">活动传播是一种可配置的功能，可使 WCF 向出站消息添加标头，其中包括 TLS 上的活动 ID。</span><span class="sxs-lookup"><span data-stu-id="69512-112">Activity propagation is a configurable capability that causes WCF to add a header to outbound messages, which includes the activity ID on the TLS.</span></span> <span data-ttu-id="69512-113">通过在服务器端的后续跟踪上包括此 ID，可以关联客户端和服务器活动。</span><span class="sxs-lookup"><span data-stu-id="69512-113">By including this on subsequent traces on the server side, we can correlate client and server activities.</span></span>  
  
## <a name="propagation-definition"></a><span data-ttu-id="69512-114">传播定义</span><span class="sxs-lookup"><span data-stu-id="69512-114">Propagation Definition</span></span>  

 <span data-ttu-id="69512-115">如果下列所有条件都适用，则活动 M 的 gAId 会传播到活动 N。</span><span class="sxs-lookup"><span data-stu-id="69512-115">Activity M’s gAId is propagated to activity N if all of the following conditions apply.</span></span>  
  
- <span data-ttu-id="69512-116">N 是为 M 创建的</span><span class="sxs-lookup"><span data-stu-id="69512-116">N is created because of M</span></span>  
  
- <span data-ttu-id="69512-117">N 已知 M 的 gAId</span><span class="sxs-lookup"><span data-stu-id="69512-117">M’s gAId is known to N</span></span>  
  
- <span data-ttu-id="69512-118">N 的 gAId 与 M 的 gAId 相同。</span><span class="sxs-lookup"><span data-stu-id="69512-118">N's gAId is equal to M’s gAId.</span></span>  
  
 <span data-ttu-id="69512-119">gAId 通过 ActivityId 消息头传播，如下面的 XML 架构所示。</span><span class="sxs-lookup"><span data-stu-id="69512-119">The gAId is propagated through the ActivityId message header, as illustrated in the following XML schema.</span></span>  
  
```xml  
<xsd:element name="ActivityId" type="integer" minOccurs="0">  
  <xsd:attribute name="CorrelationId" type="integer" minOccurs="0"/>  
</xsd:element>  
```  
  
 <span data-ttu-id="69512-120">下面是一个消息头示例。</span><span class="sxs-lookup"><span data-stu-id="69512-120">The following is an example of the message header.</span></span>  
  
```xml  
<MessageLogTraceRecord>  
  <s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope"
                      xmlns:a="http://www.w3.org/2005/08/addressing">  
    <s:Header>  
      <a:Action s:mustUnderstand="1">http://Microsoft.ServiceModel.Samples/ICalculator/Subtract  
      </a:Action>  
      <a:MessageID>urn:uuid:f0091eae-d339-4c7e-9408-ece34602f1ce  
      </a:MessageID>  
      <ActivityId CorrelationId="f94c6af1-7d5d-4295-b693-4670a8a0ce34"
               xmlns="http://schemas.microsoft.com/2004/09/ServiceModel/Diagnostics">  
        17f59a29-b435-4a15-bf7b-642ffc40eac8  
      </ActivityId>  
      <a:ReplyTo>  
          <a:Address>http://www.w3.org/2005/08/addressing/anonymous</a:Address>  
      </a:ReplyTo>  
      <a:To s:mustUnderstand="1">net.tcp://localhost/servicemodelsamples/service</a:To>  
   </s:Header>  
   <s:Body>  
     <Subtract xmlns="http://Microsoft.ServiceModel.Samples">  
       <n1>145</n1>  
       <n2>76.54</n2>  
     </Subtract>  
   </s:Body>  
  </s:Envelope>  
</MessageLogTraceRecord>  
```  
  
## <a name="propagation-and-activity-boundaries"></a><span data-ttu-id="69512-121">传播和活动边界</span><span class="sxs-lookup"><span data-stu-id="69512-121">Propagation and Activity Boundaries</span></span>  

 <span data-ttu-id="69512-122">当活动 ID 在终结点之间传播时，消息接收方使用该（传播的）活动 ID 发出开始跟踪和停止跟踪。</span><span class="sxs-lookup"><span data-stu-id="69512-122">When the activity ID is propagated across endpoints, the message receiver emits a Start and Stop traces with that (propagated) activity ID.</span></span> <span data-ttu-id="69512-123">因此，每个跟踪源的 gAId 都具有开始和停止跟踪。</span><span class="sxs-lookup"><span data-stu-id="69512-123">Therefore, there is a Start and Stop trace with that gAId from each trace source.</span></span> <span data-ttu-id="69512-124">如果终结点位于同一个进程中，且使用相同的跟踪源名称，则会创建多个具有相同 lAId（相同 gAId、相同跟踪源和相同进程）的开始和停止跟踪。</span><span class="sxs-lookup"><span data-stu-id="69512-124">If the endpoints are in the same process and use the same trace source name, multiple Start and Stop with the same lAId (same gAId, same trace source, same process) are created.</span></span>  
  
## <a name="synchronization"></a><span data-ttu-id="69512-125">同步</span><span class="sxs-lookup"><span data-stu-id="69512-125">Synchronization</span></span>  

 <span data-ttu-id="69512-126">为了同步不同计算机上运行的各终结点之间的事件，向在消息中传播的 ActivityId 标头中添加了一个 CorrelationId。</span><span class="sxs-lookup"><span data-stu-id="69512-126">To synchronize events across endpoints that run on different machines, a CorrelationId is added to the ActivityId header that is propagated in messages.</span></span> <span data-ttu-id="69512-127">工具可使用此 ID 来同步计算机之间具有时钟差的事件。</span><span class="sxs-lookup"><span data-stu-id="69512-127">Tools can use this ID to synchronize events across machines with clock discrepancy.</span></span> <span data-ttu-id="69512-128">具体地说，服务跟踪查看器工具可使用此 ID 显示终结点之间的消息流。</span><span class="sxs-lookup"><span data-stu-id="69512-128">Specifically, the Service Trace Viewer tool uses this ID for showing message flows between endpoints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69512-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="69512-129">See also</span></span>

- [<span data-ttu-id="69512-130">配置跟踪</span><span class="sxs-lookup"><span data-stu-id="69512-130">Configuring Tracing</span></span>](configuring-tracing.md)
- [<span data-ttu-id="69512-131">使用服务跟踪查看器查看相关跟踪和进行故障诊断</span><span class="sxs-lookup"><span data-stu-id="69512-131">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [<span data-ttu-id="69512-132">端到端跟踪方案</span><span class="sxs-lookup"><span data-stu-id="69512-132">End-To-End Tracing Scenarios</span></span>](end-to-end-tracing-scenarios.md)
- [<span data-ttu-id="69512-133">服务跟踪查看器工具 (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="69512-133">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../service-trace-viewer-tool-svctraceviewer-exe.md)
