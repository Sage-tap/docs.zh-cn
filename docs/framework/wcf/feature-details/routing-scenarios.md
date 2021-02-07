---
description: 了解详细信息：路由方案
title: 路由方案
ms.date: 03/30/2017
helpviewer_keywords:
- routing [WCF], scenarios
ms.assetid: ec22f308-665a-413e-9f94-7267cb665dab
ms.openlocfilehash: cce69ca846f5179d78b2e7321e62444fc6f6ec26
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99733276"
---
# <a name="routing-scenarios"></a><span data-ttu-id="8993a-103">路由方案</span><span class="sxs-lookup"><span data-stu-id="8993a-103">Routing Scenarios</span></span>

<span data-ttu-id="8993a-104">尽管路由服务可高度自定义，但是，如果要从头开始创建新配置，设计高效的路由逻辑很富有挑战性。</span><span class="sxs-lookup"><span data-stu-id="8993a-104">While the Routing Service is highly customizable, it can be a challenge to design efficient routing logic when creating a new configuration from scratch.</span></span>  <span data-ttu-id="8993a-105">然而，大多数路由服务配置都遵循一些常见方案。</span><span class="sxs-lookup"><span data-stu-id="8993a-105">However, there are several common scenarios that most Routing Service configurations follow.</span></span> <span data-ttu-id="8993a-106">虽然这些方案可能并不直接适用于特定配置，但是了解如何配置路由服务以处理这些方案有助于您了解路由服务。</span><span class="sxs-lookup"><span data-stu-id="8993a-106">While these scenarios may not apply directly to your specific configuration, understanding how the Routing Service can be configured to handle these scenarios will aid you in understanding the Routing Service.</span></span>  
  
## <a name="common-scenarios"></a><span data-ttu-id="8993a-107">常见方案</span><span class="sxs-lookup"><span data-stu-id="8993a-107">Common Scenarios</span></span>  

 <span data-ttu-id="8993a-108">路由服务最基本的用途是聚合多个目标终结点以减少公开给客户端应用程序的终结点数目，然后使用消息筛选器将各消息路由到正确的目标。</span><span class="sxs-lookup"><span data-stu-id="8993a-108">The most basic use of the Routing Service is to aggregate multiple destination endpoints to reduce the number of endpoints exposed to the client applications, and then use message filters to route each message to the correct destination.</span></span> <span data-ttu-id="8993a-109">可以根据逻辑或物理处理需求（如必须由特定服务处理的消息类型）或任意业务需要（如对来自特定源的消息提供优先级处理）路由消息。</span><span class="sxs-lookup"><span data-stu-id="8993a-109">Messages may be routed based on logical or physical processing requirements, such as a message type that must be processed by a specific service, or based on arbitrary business needs such as providing priority processing of messages from a specific source.</span></span> <span data-ttu-id="8993a-110">下表列出了一些常见方案及其使用时间：</span><span class="sxs-lookup"><span data-stu-id="8993a-110">The following table lists some of the common scenarios and when they are encountered:</span></span>  
  
|<span data-ttu-id="8993a-111">方案</span><span class="sxs-lookup"><span data-stu-id="8993a-111">Scenario</span></span>|<span data-ttu-id="8993a-112">何时使用</span><span class="sxs-lookup"><span data-stu-id="8993a-112">Use when</span></span>|  
|--------------|--------------|  
|<span data-ttu-id="8993a-113">服务版本控制</span><span class="sxs-lookup"><span data-stu-id="8993a-113">Service versioning</span></span>|<span data-ttu-id="8993a-114">需要支持服务的多个版本，或者可能会在将来部署更新服务</span><span class="sxs-lookup"><span data-stu-id="8993a-114">You need to support multiple versions of a service or may deploy an updated service in the future</span></span>|  
|<span data-ttu-id="8993a-115">服务数据分区</span><span class="sxs-lookup"><span data-stu-id="8993a-115">Service data partitioning</span></span>|<span data-ttu-id="8993a-116">必须跨多个主机对服务进行分区</span><span class="sxs-lookup"><span data-stu-id="8993a-116">You must partition a service across multiple hosts</span></span>|  
|<span data-ttu-id="8993a-117">动态更新</span><span class="sxs-lookup"><span data-stu-id="8993a-117">Dynamic update</span></span>|<span data-ttu-id="8993a-118">必须在运行时动态重新配置路由逻辑以处理不断变化的服务部署</span><span class="sxs-lookup"><span data-stu-id="8993a-118">You must dynamically reconfigure routing logic at runtime to handle changing service deployments</span></span>|  
|<span data-ttu-id="8993a-119">多播</span><span class="sxs-lookup"><span data-stu-id="8993a-119">Multicast</span></span>|<span data-ttu-id="8993a-120">必须将一条消息发送到多个终结点</span><span class="sxs-lookup"><span data-stu-id="8993a-120">You must send one message to multiple endpoints</span></span>|  
|<span data-ttu-id="8993a-121">协议桥接</span><span class="sxs-lookup"><span data-stu-id="8993a-121">Protocol bridging</span></span>|<span data-ttu-id="8993a-122">通过一个传输协议接收消息，且目标终结点使用不同协议</span><span class="sxs-lookup"><span data-stu-id="8993a-122">You receive messages over one transport protocol, and the destination endpoint uses a different protocol</span></span>|  
|<span data-ttu-id="8993a-123">错误处理</span><span class="sxs-lookup"><span data-stu-id="8993a-123">Error Handling</span></span>|<span data-ttu-id="8993a-124">需要为网络中断和通信故障提供弹性</span><span class="sxs-lookup"><span data-stu-id="8993a-124">You need to provide resilience to network outages and communication failures</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="8993a-125">虽然提供的多种方案都特定于某些业务需求或处理要求，但计划支持动态更新和利用错误处理通常可认为是最佳做法，因为它们允许在运行时修改路由逻辑并从暂时的网络和通信故障恢复。</span><span class="sxs-lookup"><span data-stu-id="8993a-125">While many of the scenarios presented are specific to certain business needs or processing requirements, planning to support dynamic updates and utilizing error handling can often be considered as best practices as they allow you to modify routing logic at runtime and recover from transient network and communication failures.</span></span>  
  
### <a name="service-versioning"></a><span data-ttu-id="8993a-126">服务版本控制</span><span class="sxs-lookup"><span data-stu-id="8993a-126">Service Versioning</span></span>  

 <span data-ttu-id="8993a-127">引入新的服务版本时，您通常需要维护以前的版本，直到所有客户端都已转换到新服务为止。</span><span class="sxs-lookup"><span data-stu-id="8993a-127">When introducing a new version of a service, you must often maintain the previous version until all clients have transitioned to the new service.</span></span> <span data-ttu-id="8993a-128">如果服务是需要数天、数周甚至数月才能完成的长时间运行的进程，这一点尤为重要。</span><span class="sxs-lookup"><span data-stu-id="8993a-128">This is especially critical if the service is a long-running process that takes days, weeks, or even months to complete.</span></span> <span data-ttu-id="8993a-129">通常，这要求为新服务实现一个新终结点地址，同时维护以前版本的原始终结点。</span><span class="sxs-lookup"><span data-stu-id="8993a-129">Usually this requires implementing a new endpoint address for the new service while maintaining the original endpoint for the previous version.</span></span>  
  
 <span data-ttu-id="8993a-130">使用路由服务，您可以公开一个终结点以接收来自客户端应用程序的消息，然后基于消息内容将各消息路由到正确的服务版本。</span><span class="sxs-lookup"><span data-stu-id="8993a-130">By using the Routing Service, you can expose one endpoint to receive messages from client applications and then route each message to the correct service version based on the message content.</span></span> <span data-ttu-id="8993a-131">最基本的实现涉及在消息中添加自定义标头，用于指示将对消息进行处理的服务版本。</span><span class="sxs-lookup"><span data-stu-id="8993a-131">The most basic implementation involves adding a custom header to the message that indicates the version of the service that the message is to be processed by.</span></span> <span data-ttu-id="8993a-132">路由服务可以使用 XPathMessageFilter 检查各消息中是否存在自定义标头，并将消息路由到适当的目标终结点。</span><span class="sxs-lookup"><span data-stu-id="8993a-132">The Routing Service can use the XPathMessageFilter to inspect each message for the presence of the custom header and route the message to the appropriate destination endpoint.</span></span>  
  
 <span data-ttu-id="8993a-133">有关用于创建服务版本管理配置的步骤，请参阅 [如何：服务版本控制](how-to-service-versioning.md)。</span><span class="sxs-lookup"><span data-stu-id="8993a-133">For the steps used to create a service versioning configuration, see [How To: Service Versioning](how-to-service-versioning.md).</span></span>
  
### <a name="service-data-partitioning"></a><span data-ttu-id="8993a-134">服务数据分区</span><span class="sxs-lookup"><span data-stu-id="8993a-134">Service Data Partitioning</span></span>  

 <span data-ttu-id="8993a-135">设计分布式环境时，通常需要在多台计算机之间分布处理负载以提供高可用性，降低各计算机上的处理负载，或为特定消息子集提供专用资源。</span><span class="sxs-lookup"><span data-stu-id="8993a-135">When designing a distributed environment, it is often desirable to spread processing load across multiple computers in order to provide high availability, decrease processing load on individual computers, or to provide dedicated resources for a specific subset of messages.</span></span> <span data-ttu-id="8993a-136">虽然路由服务无法取代专用负载平衡解决方案，但是它具有执行基于内容的路由的功能，可以利用这一功能将其他类似的消息路由到特定目标。</span><span class="sxs-lookup"><span data-stu-id="8993a-136">While the Routing Service does not replace a dedicated load balancing solution, its ability to perform content based routing can be used to route otherwise similar messages to specific destinations.</span></span> <span data-ttu-id="8993a-137">例如，您可能需要单独处理从特定客户端接收的消息和从其他客户端接收的消息。</span><span class="sxs-lookup"><span data-stu-id="8993a-137">For example, you may have a requirement to process messages from a specific client separately from messages received from other clients.</span></span>  
  
 <span data-ttu-id="8993a-138">有关用于创建服务数据分区配置的步骤，请参阅 [如何：服务数据分区](how-to-service-data-partitioning.md)。</span><span class="sxs-lookup"><span data-stu-id="8993a-138">For the steps used to create a service data partitioning configuration, see [How To: Service Data Partitioning](how-to-service-data-partitioning.md).</span></span>  
  
### <a name="dynamic-routing"></a><span data-ttu-id="8993a-139">动态路由</span><span class="sxs-lookup"><span data-stu-id="8993a-139">Dynamic Routing</span></span>  

 <span data-ttu-id="8993a-140">通常需要修改路由配置以满足不断变化的业务需求，例如，在服务的较新版本中添加一个路由，更改路由条件或更改筛选器将特定消息路由到的目标终结点。</span><span class="sxs-lookup"><span data-stu-id="8993a-140">Often it is desirable to modify the routing configuration to satisfy changing business needs, such as adding a route to a newer version of a service, changing routing criteria, or changing the destination endpoint a specific message that the filter routes to.</span></span> <span data-ttu-id="8993a-141">路由服务允许您通过 <xref:System.ServiceModel.Routing.RoutingExtension>（用于在运行时提供新 RoutingConfiguration）实现此操作。</span><span class="sxs-lookup"><span data-stu-id="8993a-141">The Routing Service allows you to do this through the <xref:System.ServiceModel.Routing.RoutingExtension>, which allows you to provide a new RoutingConfiguration during run time.</span></span> <span data-ttu-id="8993a-142">新配置将立即生效，但只影响路由服务处理的任何新会话。</span><span class="sxs-lookup"><span data-stu-id="8993a-142">The new configuration takes effect immediately, but only affects any new sessions processed by the Routing Service.</span></span>  
  
 <span data-ttu-id="8993a-143">有关用于实现动态路由的步骤，请参阅 [如何：动态更新](how-to-dynamic-update.md)。</span><span class="sxs-lookup"><span data-stu-id="8993a-143">For the steps used to implement dynamic routing, see [How To: Dynamic Update](how-to-dynamic-update.md).</span></span>
  
### <a name="multicast"></a><span data-ttu-id="8993a-144">多播</span><span class="sxs-lookup"><span data-stu-id="8993a-144">Multicast</span></span>  

 <span data-ttu-id="8993a-145">路由消息时，您通常需要将各消息路由到一个特定的目标终结点。</span><span class="sxs-lookup"><span data-stu-id="8993a-145">When routing messages, usually you routing each message to one specific destination endpoint.</span></span>  <span data-ttu-id="8993a-146">但是，有时您可能需要将消息副本路由到多个目标终结点。</span><span class="sxs-lookup"><span data-stu-id="8993a-146">However, you may occasionally need to route a copy of the message to multiple destination endpoints.</span></span> <span data-ttu-id="8993a-147">若要执行多播路由，必须满足以下条件：</span><span class="sxs-lookup"><span data-stu-id="8993a-147">To perform multicast routing, the following conditions must be true:</span></span>  
  
- <span data-ttu-id="8993a-148">通道形状不能为请求-答复（但可以为单向或双工），因为请求-答复要求客户端应用程序在响应请求时只能接收一个答复。</span><span class="sxs-lookup"><span data-stu-id="8993a-148">The channel shape must not be request-reply (though it may be one-way or duplex,) because request-reply mandates that only one reply can be received by the client application in response to the request.</span></span>  
  
- <span data-ttu-id="8993a-149">计算消息时，多个筛选器必须返回 **true** 。</span><span class="sxs-lookup"><span data-stu-id="8993a-149">Multiple filters must return **true** when evaluating the message.</span></span>  
  
 <span data-ttu-id="8993a-150">如果满足这些条件，则与返回 true 的筛选器关联的每个目标终结点都将收到消息的一个副本。</span><span class="sxs-lookup"><span data-stu-id="8993a-150">If these conditions are met, each destination endpoint that is associated with a filter that returns true will receive a copy of the message.</span></span>  
  
### <a name="protocol-bridging"></a><span data-ttu-id="8993a-151">协议桥接</span><span class="sxs-lookup"><span data-stu-id="8993a-151">Protocol Bridging</span></span>  

 <span data-ttu-id="8993a-152">在不同 SOAP 协议之间路由消息时，路由服务使用 WCF API 将消息从一个协议转换为另一个协议。</span><span class="sxs-lookup"><span data-stu-id="8993a-152">When routing messages between dissimilar SOAP protocols, the Routing Service uses WCF APIs to convert the message from one protocol to the other.</span></span> <span data-ttu-id="8993a-153">如果路由服务公开的服务终结点与消息路由到的客户端终结点使用不同的协议，则会自动执行上述转换。</span><span class="sxs-lookup"><span data-stu-id="8993a-153">This occurs automatically when the service endpoint(s) exposed by the Routing Service use a different protocol than the client endpoint(s) that messages are routed to.</span></span> <span data-ttu-id="8993a-154">如果使用的协议不是标准协议，则可以禁用此行为；但是您必须提供您自己的桥接代码。</span><span class="sxs-lookup"><span data-stu-id="8993a-154">It is possible to disable this behavior if the protocols in use are not standard; however, you must then provide your own bridging code.</span></span>
  
### <a name="error-handling"></a><span data-ttu-id="8993a-155">错误处理</span><span class="sxs-lookup"><span data-stu-id="8993a-155">Error Handling</span></span>  

 <span data-ttu-id="8993a-156">在分布式环境中，通常会遇到暂时的网络或通信故障。</span><span class="sxs-lookup"><span data-stu-id="8993a-156">In a distributed environment, it is not uncommon to encounter transient network or communication failures.</span></span> <span data-ttu-id="8993a-157">如果不采用中介服务（如路由服务），则处理此类故障的重担将落在客户端应用程序上。</span><span class="sxs-lookup"><span data-stu-id="8993a-157">Without an intermediary service such as the Routing Service, the burden of handling such failures falls on the client application.</span></span> <span data-ttu-id="8993a-158">如果客户端应用程序不包含发生网络或通信故障时进行重试的特定逻辑且不知道备用位置，用户可能会遇到这样的情况：必须多次提交某条消息才能使目标服务成功处理该消息。</span><span class="sxs-lookup"><span data-stu-id="8993a-158">If the client application does not include specific logic to retry in the event of network or communication failures and knowledge of alternate locations, the user may encounter scenarios where a message must be submitted multiple times before it is successfully processed by the destination service.</span></span> <span data-ttu-id="8993a-159">客户可能会将该应用程序视为不可靠的应用程序，进而可能影响客户对该应用程序的满意度。</span><span class="sxs-lookup"><span data-stu-id="8993a-159">This can lead to customer dissatisfaction with the application, as it may be perceived as unreliable.</span></span>  
  
 <span data-ttu-id="8993a-160">路由服务将为遇到网络或通信相关故障的消息提供可靠的错误处理功能，从而纠正此状况。</span><span class="sxs-lookup"><span data-stu-id="8993a-160">The Routing Service attempts to remedy this scenario by providing robust error handling capabilities for messages that encounter network or communication-related failures.</span></span> <span data-ttu-id="8993a-161">通过创建可能的目标终结点列表并将此列表与各消息筛选器相关联，可以避免由于只有一个可能的终结点而导致的单点故障。</span><span class="sxs-lookup"><span data-stu-id="8993a-161">By creating a list of possible destination endpoints and associating this list with each message filter, you remove the single point of failure incurred by having only one possible destination.</span></span> <span data-ttu-id="8993a-162">出现故障时，路由服务会尝试将消息传递到列表中的下一个终结点，直到已传递此消息、出现非通信故障或所有终结点已耗尽。</span><span class="sxs-lookup"><span data-stu-id="8993a-162">In the event of a failure, the Routing Service will attempt to deliver the message to the next endpoint in the list until the message has been delivered, a non-communication failure occurs, or all endpoints have been exhausted.</span></span>  
  
 <span data-ttu-id="8993a-163">有关用于配置错误处理的步骤，请参阅 [如何：错误处理](how-to-error-handling.md)。</span><span class="sxs-lookup"><span data-stu-id="8993a-163">For the steps used to configure error handling, see [How To: Error Handling](how-to-error-handling.md).</span></span>
  
### <a name="in-this-section"></a><span data-ttu-id="8993a-164">本节内容</span><span class="sxs-lookup"><span data-stu-id="8993a-164">In This Section</span></span>  

 [<span data-ttu-id="8993a-165">如何：服务版本控制</span><span class="sxs-lookup"><span data-stu-id="8993a-165">How To: Service Versioning</span></span>](how-to-service-versioning.md)  
  
 [<span data-ttu-id="8993a-166">如何：服务数据分区</span><span class="sxs-lookup"><span data-stu-id="8993a-166">How To: Service Data Partitioning</span></span>](how-to-service-data-partitioning.md)  
  
 [<span data-ttu-id="8993a-167">如何：动态更新</span><span class="sxs-lookup"><span data-stu-id="8993a-167">How To: Dynamic Update</span></span>](how-to-dynamic-update.md)  
  
 [<span data-ttu-id="8993a-168">如何：错误处理</span><span class="sxs-lookup"><span data-stu-id="8993a-168">How To: Error Handling</span></span>](how-to-error-handling.md)  
  
## <a name="see-also"></a><span data-ttu-id="8993a-169">请参阅</span><span class="sxs-lookup"><span data-stu-id="8993a-169">See also</span></span>

- [<span data-ttu-id="8993a-170">路由简介</span><span class="sxs-lookup"><span data-stu-id="8993a-170">Routing Introduction</span></span>](routing-introduction.md)
