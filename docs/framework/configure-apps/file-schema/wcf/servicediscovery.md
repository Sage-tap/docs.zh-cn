---
description: 了解详细信息： <serviceDiscovery>
title: <serviceDiscovery>
ms.date: 03/30/2017
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
ms.openlocfilehash: d6df5b8d51763429829c2ea3c2593003720b7179
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682847"
---
# \<serviceDiscovery>

<span data-ttu-id="92ddd-102">指定服务终结点的可发现性。</span><span class="sxs-lookup"><span data-stu-id="92ddd-102">Specifies the discoverability of service endpoints.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceDiscovery>**  
  
## <a name="syntax"></a><span data-ttu-id="92ddd-103">语法</span><span class="sxs-lookup"><span data-stu-id="92ddd-103">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceDiscovery>
        <announcementEndpoints>
          <endpoint name="String"
                    kind="Type" />
        </announcementEndpoints>
        <discoveryEndpoints>
          <endpoint name="String"
                    kind="Type" />
        </discoveryEndpoints>
      </serviceDiscovery>
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="92ddd-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="92ddd-104">Attributes and Elements</span></span>  

 <span data-ttu-id="92ddd-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="92ddd-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="92ddd-106">特性</span><span class="sxs-lookup"><span data-stu-id="92ddd-106">Attributes</span></span>  

 <span data-ttu-id="92ddd-107">无。</span><span class="sxs-lookup"><span data-stu-id="92ddd-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="92ddd-108">子元素</span><span class="sxs-lookup"><span data-stu-id="92ddd-108">Child Elements</span></span>  
  
|<span data-ttu-id="92ddd-109">元素</span><span class="sxs-lookup"><span data-stu-id="92ddd-109">Element</span></span>|<span data-ttu-id="92ddd-110">说明</span><span class="sxs-lookup"><span data-stu-id="92ddd-110">Description</span></span>|  
|-------------|-----------------|  
|[\<announcementEndpoint>](announcementendpoint.md)|<span data-ttu-id="92ddd-111">一个公告终结点集合。</span><span class="sxs-lookup"><span data-stu-id="92ddd-111">A collection of announcement endpoints.</span></span> <span data-ttu-id="92ddd-112">使用此节可指定用于发送公告消息的终结点。</span><span class="sxs-lookup"><span data-stu-id="92ddd-112">Use this section to specify the endpoints to use for sending announcement messages.</span></span>|  
|[\<discoveryEndpoint>](discoveryendpoint.md)|<span data-ttu-id="92ddd-113">一个发现终结点集合。</span><span class="sxs-lookup"><span data-stu-id="92ddd-113">A collection of discovery endpoints.</span></span> <span data-ttu-id="92ddd-114">使用此节可指定要在其上侦听发现消息的终结点。</span><span class="sxs-lookup"><span data-stu-id="92ddd-114">Use this section to specify the endpoints on which to listen for the discovery messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="92ddd-115">父元素</span><span class="sxs-lookup"><span data-stu-id="92ddd-115">Parent Elements</span></span>  
  
|<span data-ttu-id="92ddd-116">元素</span><span class="sxs-lookup"><span data-stu-id="92ddd-116">Element</span></span>|<span data-ttu-id="92ddd-117">说明</span><span class="sxs-lookup"><span data-stu-id="92ddd-117">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="92ddd-118">指定行为元素。</span><span class="sxs-lookup"><span data-stu-id="92ddd-118">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92ddd-119">备注</span><span class="sxs-lookup"><span data-stu-id="92ddd-119">Remarks</span></span>  

 <span data-ttu-id="92ddd-120">将此配置元素添加到服务的行为配置后，此元素可使系统检测到此服务的所有终结点。</span><span class="sxs-lookup"><span data-stu-id="92ddd-120">When added to the service’s behavior configuration, this configuration element makes all of the endpoints of that service discoverable.</span></span> <span data-ttu-id="92ddd-121">通过使用 [\<discoveryEndpoint>](discoveryendpoint.md) 或子元素，可以进一步配置此类终结点的发现功能 [\<announcementEndpoint>](announcementendpoint.md) 。</span><span class="sxs-lookup"><span data-stu-id="92ddd-121">You can further configure the discovery features of such endpoints by using the [\<discoveryEndpoint>](discoveryendpoint.md) or [\<announcementEndpoint>](announcementendpoint.md) child elements.</span></span> <span data-ttu-id="92ddd-122">使用 [\<announcementEndpoint>](announcementendpoint.md) 部分通过指定要用于将服务公告发送 (online/Hello 和 offline/再见) 来配置公告。</span><span class="sxs-lookup"><span data-stu-id="92ddd-122">Use the [\<announcementEndpoint>](announcementendpoint.md) section to configure the announcements by specifying the endpoint configuration to be use to send service announcements (online/Hello and offline/Bye).</span></span> <span data-ttu-id="92ddd-123">使用 [\<discoveryEndpoint>](discoveryendpoint.md) 部分手动指定要在其上侦听发现消息的终结点。</span><span class="sxs-lookup"><span data-stu-id="92ddd-123">Use the [\<discoveryEndpoint>](discoveryendpoint.md) section to manually specify the endpoint on which to listen for the discovery messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92ddd-124">示例</span><span class="sxs-lookup"><span data-stu-id="92ddd-124">Example</span></span>  

 <span data-ttu-id="92ddd-125">下面的配置示例指定 CalculatorService 可供检测，并选择指定要使用的公告终结点。</span><span class="sxs-lookup"><span data-stu-id="92ddd-125">The following configuration example specifies that the CalculatorService to be discoverable, and optionally specifies the announcement endpoint to be used.</span></span>  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    ...
  </service>
</services>
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <serviceDiscovery>
        <announcementEndpoints>
          <endpoint name="udpEndpoint"
                    kind="udpAnnouncementEndpoint" />
        </announcementEndpoints>
      </serviceDiscovery>
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="92ddd-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="92ddd-126">See also</span></span>

- <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>
