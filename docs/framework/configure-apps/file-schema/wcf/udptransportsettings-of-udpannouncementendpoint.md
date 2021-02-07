---
description: 了解详细 <udpTransportSettings> 信息： <udpAnnouncementEndpoint>
title: <udpTransportSettings> 的 <udpAnnouncementEndpoint>
ms.date: 03/30/2017
ms.assetid: a7ddff1a-5eed-4bbc-8580-b95ef8890e1f
ms.openlocfilehash: 2997004e162728b20daa4f137e1edf132cd33d52
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749202"
---
# <a name="udptransportsettings-of-udpannouncementendpoint"></a><span data-ttu-id="6ce45-103">\<udpTransportSettings> 的 \<udpAnnouncementEndpoint></span><span class="sxs-lookup"><span data-stu-id="6ce45-103">\<udpTransportSettings> of \<udpAnnouncementEndpoint></span></span>

<span data-ttu-id="6ce45-104">此配置元素公开的 UDP 传输设置 [\<udpAnnouncementEndpoint>](udpannouncementendpoint.md) 。</span><span class="sxs-lookup"><span data-stu-id="6ce45-104">This configuration element exposes UDP transport settings for [\<udpAnnouncementEndpoint>](udpannouncementendpoint.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<udpAnnouncementEndpoint>**](udpannouncementendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<updTransportSettings>**  

## <a name="syntax"></a><span data-ttu-id="6ce45-105">语法</span><span class="sxs-lookup"><span data-stu-id="6ce45-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <udpAnnouncementEndpoint>
      <standardEndpoint>
        <updTransportSettings duplicateMessageHistoryLength="Integer"
                              maxBufferPoolSize="Integer"
                              maxMulticastRetransmitCount="Integer"
                              maxPendingMessageCount="Integer"
                              maxReceivedMessageSize="Integer"
                              maxUnicastRetransmitCount="Integer"
                              multicastInterfaceId="String"
                              socketReceiveBufferSize="Integer"
                              timeToLive="Integer" />
      </standardEndpoint>
    </udpAnnouncementEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6ce45-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="6ce45-106">Attributes and Elements</span></span>  

 <span data-ttu-id="6ce45-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6ce45-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6ce45-108">特性</span><span class="sxs-lookup"><span data-stu-id="6ce45-108">Attributes</span></span>  
  
|<span data-ttu-id="6ce45-109">属性</span><span class="sxs-lookup"><span data-stu-id="6ce45-109">Attribute</span></span>|<span data-ttu-id="6ce45-110">说明</span><span class="sxs-lookup"><span data-stu-id="6ce45-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6ce45-111">duplicateMessageHistoryLength</span><span class="sxs-lookup"><span data-stu-id="6ce45-111">duplicateMessageHistoryLength</span></span>|<span data-ttu-id="6ce45-112">一个整数，指定传输用于标识重复消息的最大消息哈希数。</span><span class="sxs-lookup"><span data-stu-id="6ce45-112">An integer that specifies the maximum number of message hashes used by the transport for identifying duplicate messages.</span></span>  <span data-ttu-id="6ce45-113">将在 TransportManager 级别进行重复检测。</span><span class="sxs-lookup"><span data-stu-id="6ce45-113">Duplicate detection will be done at the TransportManager level.</span></span> <span data-ttu-id="6ce45-114">将此属性设置为 0 即可禁用重复检测。</span><span class="sxs-lookup"><span data-stu-id="6ce45-114">Setting this property to 0 disables duplicate detection.</span></span><br /><br /> <span data-ttu-id="6ce45-115">系统管理员或开发人员可以使用此特性关闭重复消息检测算法。</span><span class="sxs-lookup"><span data-stu-id="6ce45-115">This attribute allows system administrators or developers to turn off duplicate message detection algorithms.</span></span> <span data-ttu-id="6ce45-116">如果您希望实现自己的重复检测算法，可能需要这一功能。</span><span class="sxs-lookup"><span data-stu-id="6ce45-116">This may be desirable if you want to implement your own duplicate detection algorithm.</span></span><br /><br /> <span data-ttu-id="6ce45-117">默认值为 4112。</span><span class="sxs-lookup"><span data-stu-id="6ce45-117">The default is 4112.</span></span>|  
|<span data-ttu-id="6ce45-118">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="6ce45-118">maxBufferPoolSize</span></span>|<span data-ttu-id="6ce45-119">一个整数，指定传输使用的任何缓冲池的最大大小。</span><span class="sxs-lookup"><span data-stu-id="6ce45-119">An integer that specifies the maximum size of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="6ce45-120">maxMulticastRetransmitCount</span><span class="sxs-lookup"><span data-stu-id="6ce45-120">maxMulticastRetransmitCount</span></span>|<span data-ttu-id="6ce45-121">一个整数，指定应重新传输消息的最大次数（包括第一次发送）。</span><span class="sxs-lookup"><span data-stu-id="6ce45-121">An integer that specifies the maximum number of times the message should be retransmitted (in addition to the first send).</span></span><br /><br /> <span data-ttu-id="6ce45-122">默认值为 2。</span><span class="sxs-lookup"><span data-stu-id="6ce45-122">The default is 2.</span></span>|  
|<span data-ttu-id="6ce45-123">maxPendingMessageCount</span><span class="sxs-lookup"><span data-stu-id="6ce45-123">maxPendingMessageCount</span></span>|<span data-ttu-id="6ce45-124">一个整数，指定已经接收但尚未从单个通道实例的 InputQueue 中移除的最大消息数。</span><span class="sxs-lookup"><span data-stu-id="6ce45-124">An integer that specifies the maximum number of messages that have been received but not yet removed from the InputQueue for an individual channel instance.</span></span>  <span data-ttu-id="6ce45-125">如果 InputQueue 已达到挂起消息计数上限，则将丢弃消息。</span><span class="sxs-lookup"><span data-stu-id="6ce45-125">If the InputQueue has hit its pending message count limit, the message will be dropped.</span></span><br /><br /> <span data-ttu-id="6ce45-126">默认值为 32。</span><span class="sxs-lookup"><span data-stu-id="6ce45-126">The default is 32.</span></span>|  
|<span data-ttu-id="6ce45-127">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="6ce45-127">maxReceivedMessageSize</span></span>|<span data-ttu-id="6ce45-128">一个整数，指定绑定可处理的消息的最大大小。</span><span class="sxs-lookup"><span data-stu-id="6ce45-128">An integer that specifies the maximum size for a message that can be processed by the binding.</span></span><br /><br /> <span data-ttu-id="6ce45-129">默认值为 65507。</span><span class="sxs-lookup"><span data-stu-id="6ce45-129">The default value is 65507.</span></span>|  
|<span data-ttu-id="6ce45-130">maxUnicastRetransmitCount</span><span class="sxs-lookup"><span data-stu-id="6ce45-130">maxUnicastRetransmitCount</span></span>|<span data-ttu-id="6ce45-131">一个整数，指定应重新传输消息的最大次数（包括第一次发送）。</span><span class="sxs-lookup"><span data-stu-id="6ce45-131">An integer that specifies the maximum number of times the message should be retransmitted (in addition to the first send).</span></span>  <span data-ttu-id="6ce45-132">如果将消息发送到单播地址，并且收到的响应消息中带有相应的 RelatesTo 标头，重新传输可能会提前终止（在达到配置的重新传输次数之前）。</span><span class="sxs-lookup"><span data-stu-id="6ce45-132">If the message is sent to a unicast address and a response message is received with a corresponding RelatesTo header, then retransmission may terminate early (before retransmitting the configured number of times).</span></span><br /><br /> <span data-ttu-id="6ce45-133">默认值为 1。</span><span class="sxs-lookup"><span data-stu-id="6ce45-133">The default value is 1.</span></span>|  
|<span data-ttu-id="6ce45-134">multicastInterfaceId</span><span class="sxs-lookup"><span data-stu-id="6ce45-134">multicastInterfaceId</span></span>|<span data-ttu-id="6ce45-135">一个字符串，唯一标识在多宿主计算机上发送和接收多播流量时应使用的网络适配器。</span><span class="sxs-lookup"><span data-stu-id="6ce45-135">A string that uniquely identifies the network adapter that should be used when sending and receiving multicast traffic on multi-homed machines.</span></span> <span data-ttu-id="6ce45-136">在运行时，传输将使用此特性值来查找接口索引，然后使用该索引设置 `IP_MULTICAST_IF` 和 `IPV6_MULTICAST_IF` 套接字选项。</span><span class="sxs-lookup"><span data-stu-id="6ce45-136">At runtime, the transport will use this attribute value to lookup the interface index, which is then used to set the `IP_MULTICAST_IF` and `IPV6_MULTICAST_IF` socket options.</span></span>  <span data-ttu-id="6ce45-137">加入多播组时将使用相同的接口索引（如果适用）。</span><span class="sxs-lookup"><span data-stu-id="6ce45-137">The same interface index will be used when joining a multicast group, if applicable.</span></span><br /><br /> <span data-ttu-id="6ce45-138">默认值是 `null`。</span><span class="sxs-lookup"><span data-stu-id="6ce45-138">The default value is `null`.</span></span>|  
|<span data-ttu-id="6ce45-139">socketReceiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="6ce45-139">socketReceiveBufferSize</span></span>|<span data-ttu-id="6ce45-140">一个整数，指定基础 WinSock 套接字上接收缓冲区的大小。</span><span class="sxs-lookup"><span data-stu-id="6ce45-140">An integer that specifies the receive buffer size on the underlying WinSock socket.</span></span><br /><br /> <span data-ttu-id="6ce45-141">接收通道的用户可以对绑定使用此特性，以控制系统在接收数据时的行为。</span><span class="sxs-lookup"><span data-stu-id="6ce45-141">A user of a receiving channel can use this attribute on the Binding to control how the system behaves when it receives data.</span></span>  <span data-ttu-id="6ce45-142">例如，假定应用程序使用入站 WCF 消息时达到了最大阈值，对此特性使用较高的值将允许消息在等待应用程序处理时在 WinSock 缓冲区中堆叠。</span><span class="sxs-lookup"><span data-stu-id="6ce45-142">For example, given an application that is consuming inbound WCF messages at the maximum threshold, using a higher value for this attribute would allow messages to stack up in the WinSock buffer while waiting for the application to be able to process them.</span></span>  <span data-ttu-id="6ce45-143">在相同情况下使用较低的值将导致丢弃这些消息。此特性公开基础 WinSock `SO_RCVBUF` 套接字选项。此特性值必须至少为 `maxReceivedMessageSize` 的大小。</span><span class="sxs-lookup"><span data-stu-id="6ce45-143">Using a lower value in the same situation would result in messages getting dropped.This attribute exposes the underlying WinSock `SO_RCVBUF` socket option.This attribute value must be at least the size of `maxReceivedMessageSize`.</span></span>   <span data-ttu-id="6ce45-144">如果将此特性值设置为小于 `maxReceivedMessageSize` 的值，会导致运行时异常。</span><span class="sxs-lookup"><span data-stu-id="6ce45-144">Setting it to a value smaller than the `maxReceivedMessageSize` will result in runtime exception.</span></span><br /><br /> <span data-ttu-id="6ce45-145">默认值为 65536。</span><span class="sxs-lookup"><span data-stu-id="6ce45-145">The default value is 65536.</span></span>|  
|<span data-ttu-id="6ce45-146">timeToLive</span><span class="sxs-lookup"><span data-stu-id="6ce45-146">timeToLive</span></span>|<span data-ttu-id="6ce45-147">一个整数，指定多播数据包可以遍历的网络段跃点数。</span><span class="sxs-lookup"><span data-stu-id="6ce45-147">An integer that specifies the number of network segment hops that a multicast packet can traverse.</span></span>  <span data-ttu-id="6ce45-148">此特性公开与 `IP_MULTICAST_TTL` 和 `IP_TTL` 套接字选项关联的功能。</span><span class="sxs-lookup"><span data-stu-id="6ce45-148">This attribute exposes the functionality associated with the `IP_MULTICAST_TTL` and `IP_TTL` socket options.</span></span><br /><br /> <span data-ttu-id="6ce45-149">默认值为 1。</span><span class="sxs-lookup"><span data-stu-id="6ce45-149">The default value is 1.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6ce45-150">子元素</span><span class="sxs-lookup"><span data-stu-id="6ce45-150">Child Elements</span></span>  

 <span data-ttu-id="6ce45-151">无。</span><span class="sxs-lookup"><span data-stu-id="6ce45-151">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6ce45-152">父元素</span><span class="sxs-lookup"><span data-stu-id="6ce45-152">Parent Elements</span></span>  
  
|<span data-ttu-id="6ce45-153">元素</span><span class="sxs-lookup"><span data-stu-id="6ce45-153">Element</span></span>|<span data-ttu-id="6ce45-154">说明</span><span class="sxs-lookup"><span data-stu-id="6ce45-154">Description</span></span>|  
|-------------|-----------------|  
|[\<udpAnnouncementEndpoint>](udpannouncementendpoint.md)|<span data-ttu-id="6ce45-155">具有固定公告协定和 UDP 传输绑定的标准终结点。</span><span class="sxs-lookup"><span data-stu-id="6ce45-155">A standard endpoint that has fixed announcement contract and UDP transport binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6ce45-156">请参阅</span><span class="sxs-lookup"><span data-stu-id="6ce45-156">See also</span></span>

- <xref:System.ServiceModel.Discovery.UdpTransportSettings>
