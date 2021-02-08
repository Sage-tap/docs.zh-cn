---
description: 了解详细信息： <discoveryEndpoint>
title: <discoveryEndpoint>
ms.date: 03/30/2017
ms.assetid: fae2f48b-a635-4e4b-859d-a1432ac37e1c
ms.openlocfilehash: 32be673aac9604d8285d002640f11a29b9545afb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802302"
---
# \<discoveryEndpoint>

<span data-ttu-id="b997f-102">此配置元素定义具有固定发现协定的标准终结点。</span><span class="sxs-lookup"><span data-stu-id="b997f-102">This configuration element defines a standard endpoint with a fixed discovery contract.</span></span> <span data-ttu-id="b997f-103">将此元素添加到服务配置后，该元素将指定侦听发现消息的位置。</span><span class="sxs-lookup"><span data-stu-id="b997f-103">When added to the service configuration, it specifies where to listen for the discovery messages.</span></span> <span data-ttu-id="b997f-104">将此元素添加到客户端配置后，该元素将指定发送发现查询的位置。</span><span class="sxs-lookup"><span data-stu-id="b997f-104">When added to the client configuration it specifies where to send the discovery queries.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="b997f-105">语法</span><span class="sxs-lookup"><span data-stu-id="b997f-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <discoveryEndpoint>
      <standardEndpoint discoveryMode="Adhoc/Managed"
                        discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxResponseDelay="Timespan"
                        name="String" />
    </discoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b997f-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="b997f-106">Attributes and elements</span></span>

<span data-ttu-id="b997f-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="b997f-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b997f-108">特性</span><span class="sxs-lookup"><span data-stu-id="b997f-108">Attributes</span></span>

| <span data-ttu-id="b997f-109">属性</span><span class="sxs-lookup"><span data-stu-id="b997f-109">Attribute</span></span>        | <span data-ttu-id="b997f-110">说明</span><span class="sxs-lookup"><span data-stu-id="b997f-110">Description</span></span> |  
| ---------------- | ----------- |  
| <span data-ttu-id="b997f-111">discoveryMode</span><span class="sxs-lookup"><span data-stu-id="b997f-111">discoveryMode</span></span>    | <span data-ttu-id="b997f-112">一个字符串，指定发现协议的模式。</span><span class="sxs-lookup"><span data-stu-id="b997f-112">A string that specifies the mode of discovery protocol.</span></span> <span data-ttu-id="b997f-113">有效值为 "即席" 和 "Managed"。</span><span class="sxs-lookup"><span data-stu-id="b997f-113">Valid values are "Adhoc" and "Managed".</span></span> <span data-ttu-id="b997f-114">在托管模式下，协议依靠发现代理，此代理用作可检测服务的存储库。</span><span class="sxs-lookup"><span data-stu-id="b997f-114">In managed mode the protocol relies on a Discovery Proxy, which acts as a repository of Discoverable services.</span></span> <span data-ttu-id="b997f-115">即席模式要求协议使用 UDP 多播机制查找可用的服务。</span><span class="sxs-lookup"><span data-stu-id="b997f-115">Adhoc mode requires the protocol to use UDP multicast mechanism to find available services.</span></span> <span data-ttu-id="b997f-116">有关属性的详细信息，请参阅 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A> 。</span><span class="sxs-lookup"><span data-stu-id="b997f-116">For more information on the property, see <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>.</span></span> |  
| <span data-ttu-id="b997f-117">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="b997f-117">discoveryVersion</span></span> | <span data-ttu-id="b997f-118">一个字符串，指定两个 WS-Discovery 协议版本中的其中一个版本。</span><span class="sxs-lookup"><span data-stu-id="b997f-118">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="b997f-119">有效值为 WSDiscovery11 和 WSDiscoveryApril2005。</span><span class="sxs-lookup"><span data-stu-id="b997f-119">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="b997f-120">此值的类型为 <xref:System.ServiceModel.Discovery.DiscoveryVersion>。</span><span class="sxs-lookup"><span data-stu-id="b997f-120">This value is of type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span></span> |  
| <span data-ttu-id="b997f-121">maxResponseDelay</span><span class="sxs-lookup"><span data-stu-id="b997f-121">maxResponseDelay</span></span> | <span data-ttu-id="b997f-122">一个 Timespan 值，指定 Discovery 协议在发送 Probe Match、Resolve Match 这类消息之前等待的最大延迟值。</span><span class="sxs-lookup"><span data-stu-id="b997f-122">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending certain messages such as Probe Match or Resolve Match.</span></span><br /><br /> <span data-ttu-id="b997f-123">如果同时发送所有 ProbeMatch，则可能发生网络风暴。</span><span class="sxs-lookup"><span data-stu-id="b997f-123">If all ProbeMatches are sent at the same time, a network storm may result.</span></span> <span data-ttu-id="b997f-124">若要防止发生这种情况，可在发送 ProbeMatch 时在各 ProbeMatch 之间应用随机延迟。</span><span class="sxs-lookup"><span data-stu-id="b997f-124">To prevent this from occurring, ProbeMatches are sent with a random delay between each ProbeMatch.</span></span> <span data-ttu-id="b997f-125">随机延迟的范围是从 0 到此特性所设置的值之间。</span><span class="sxs-lookup"><span data-stu-id="b997f-125">The random delay is in the range of 0 to the value set by this attribute.</span></span> <span data-ttu-id="b997f-126">如果将此特性设置为 0，则在不使用任何延迟的紧凑循环中发送 ProbeMatch 消息。</span><span class="sxs-lookup"><span data-stu-id="b997f-126">If this attribute is set to 0, then the ProbeMatches messages are sent in a tight loop without any delay.</span></span> <span data-ttu-id="b997f-127">否则，在发送 ProbeMatch 消息时将应用一定的随机延迟，以使发送所有 ProbeMatch 消息所用的总时间不会超过 maxResponseDelay。</span><span class="sxs-lookup"><span data-stu-id="b997f-127">Otherwise, the ProbeMatches messages are sent with some random delay such that the total time taken to send all ProbeMatches messages does not exceed the maxResponseDelay.</span></span> <span data-ttu-id="b997f-128">此值只与服务相关，不可用于客户端。</span><span class="sxs-lookup"><span data-stu-id="b997f-128">This value is only relevant for services, it is not used by clients.</span></span> |  
| `name`           | <span data-ttu-id="b997f-129">一个字符串，指定标准终结点的配置的名称。</span><span class="sxs-lookup"><span data-stu-id="b997f-129">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="b997f-130">此名称在服务终结点的 `endpointConfiguration` 特性中用于将标准终结点链接到其配置。</span><span class="sxs-lookup"><span data-stu-id="b997f-130">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span> |  
  
### <a name="child-elements"></a><span data-ttu-id="b997f-131">子元素</span><span class="sxs-lookup"><span data-stu-id="b997f-131">Child elements</span></span>

<span data-ttu-id="b997f-132">无。</span><span class="sxs-lookup"><span data-stu-id="b997f-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b997f-133">父元素</span><span class="sxs-lookup"><span data-stu-id="b997f-133">Parent elements</span></span>

| <span data-ttu-id="b997f-134">元素</span><span class="sxs-lookup"><span data-stu-id="b997f-134">Element</span></span> | <span data-ttu-id="b997f-135">说明</span><span class="sxs-lookup"><span data-stu-id="b997f-135">Description</span></span> |  
| ------- | ----------- |  
| [\<standardEndpoints>](standardendpoints.md) | <span data-ttu-id="b997f-136">具有一个或多个固定属性（地址、绑定和协定）的预定义终结点的标准终结点集合。</span><span class="sxs-lookup"><span data-stu-id="b997f-136">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span> |  
  
## <a name="example"></a><span data-ttu-id="b997f-137">示例</span><span class="sxs-lookup"><span data-stu-id="b997f-137">Example</span></span>

<span data-ttu-id="b997f-138">下面的示例演示通过对等网多播传输侦听发现消息的服务。</span><span class="sxs-lookup"><span data-stu-id="b997f-138">The following example demonstrates a service listening on the discovery messages over a peer net multicast transport.</span></span> <span data-ttu-id="b997f-139">此示例明确指定 WS-Discovery 2005 年 4 月版。</span><span class="sxs-lookup"><span data-stu-id="b997f-139">The example explicitly specifies WS-Discovery April 2005 version.</span></span>  
  
<span data-ttu-id="b997f-140">标准终结点配置基于服务定义，无法在服务之间共享。</span><span class="sxs-lookup"><span data-stu-id="b997f-140">The standard endpoint configuration is defined per service and cannot be shared across the service.</span></span> <span data-ttu-id="b997f-141">如果其他服务希望采用相同的发现终结点，则需要将相同配置添加到该服务的节中。</span><span class="sxs-lookup"><span data-stu-id="b997f-141">If another service would like to have the same discovery endpoint, the same configuration needs to be added to that service’s section.</span></span>  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    <endpoint binding="basicHttpBinding"
              address="calculator"
              contract="ICalculatorService" />
    <endpoint name="peerNetDiscovery"
              binding="peerTcpBinding"
              address="net.p2p://discoveryMesh/multicast"
              kind="discoveryEndpoint"
              endpointConfiguration="peerTcpDiscoveryEndpointConfiguration"
              bindingConfiguration="discoveryPeerTcpBindingConfig" />
  </service>
</services>
<standardEndpoints>
  <discoveryEndpoint>
    <standardEndpoint name="peerTcpDiscoveryEndpointConfiguration"
                      version="WSDiscoveryApril2005" />
  </discoveryEndpoint>
</standardEndpoints>
```  
  
## <a name="see-also"></a><span data-ttu-id="b997f-142">请参阅</span><span class="sxs-lookup"><span data-stu-id="b997f-142">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
