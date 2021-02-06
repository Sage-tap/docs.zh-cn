---
description: 了解详细信息：如何：服务数据分区
title: 如何：服务数据分区
ms.date: 03/30/2017
ms.assetid: 1ccff72e-d76b-4e36-93a2-e51f7b32dc83
ms.openlocfilehash: fd40ee37a80a8d5039231c6efe6369006022afad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643236"
---
# <a name="how-to-service-data-partitioning"></a><span data-ttu-id="9331d-103">如何：服务数据分区</span><span class="sxs-lookup"><span data-stu-id="9331d-103">How To: Service Data Partitioning</span></span>

<span data-ttu-id="9331d-104">本主题概述了在同一目标服务的多个实例之间划分消息时所需采取的基本步骤。</span><span class="sxs-lookup"><span data-stu-id="9331d-104">This topic outlines the basic steps required to partition messages across multiple instances of the same destination service.</span></span> <span data-ttu-id="9331d-105">如果需要缩放服务以提供更好的服务质量，或者需要以特定方式处理来自不同客户的请求，此时通常采用服务数据划分。</span><span class="sxs-lookup"><span data-stu-id="9331d-105">Service data partitioning is typically used when you need to scale a service in order to provide better quality of service, or when you need to handle requests from different customers in a specific way.</span></span> <span data-ttu-id="9331d-106">例如，来自高价值或 "黄金" 客户的消息可能需要比标准客户的消息处理更高的优先级。</span><span class="sxs-lookup"><span data-stu-id="9331d-106">For example, messages from high value or "Gold" customers may need to be processed at a higher priority than messages from a standard customer.</span></span>  
  
 <span data-ttu-id="9331d-107">在本示例中，将消息路由到 regularCalc 服务的两个实例之一。</span><span class="sxs-lookup"><span data-stu-id="9331d-107">In this example, messages are routed to one of two instances of the regularCalc service.</span></span> <span data-ttu-id="9331d-108">服务的两个实例相同；但是，calculator1 终结点表示的服务负责处理从高价值客户收到的消息，而 calculator 2 终结点负责处理来自其他客户的消息。</span><span class="sxs-lookup"><span data-stu-id="9331d-108">Both instances of the service are identical; however the service represented by the calculator1 endpoint processes messages received from high value customers, the calculator 2 endpoint processes messages from other customers</span></span>  
  
 <span data-ttu-id="9331d-109">客户端发送的消息不含任何独特数据可用于标识应将消息路由到哪个服务实例。</span><span class="sxs-lookup"><span data-stu-id="9331d-109">The message sent from the client does not have any unique data that can be used to identify which service instance the message should be routed to.</span></span> <span data-ttu-id="9331d-110">为了使每个客户端都将数据路由到特定目标服务，系统中将实现两个用于接收消息的服务终结点。</span><span class="sxs-lookup"><span data-stu-id="9331d-110">To allow each client to route data to a specific destination service we will implement two service endpoints that will be used to receive messages.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9331d-111">虽然此示例中使用特定终结点来划分数据，不过，也可使用消息本身中包含的信息（如标头或正文数据）来实现此操作。</span><span class="sxs-lookup"><span data-stu-id="9331d-111">While this example uses specific endpoints to partition data, this could also be accomplished using information contained within the message itself such as header or body data.</span></span>  
  
### <a name="implement-service-data-partitioning"></a><span data-ttu-id="9331d-112">实现服务数据划分</span><span class="sxs-lookup"><span data-stu-id="9331d-112">Implement Service Data Partitioning</span></span>  
  
1. <span data-ttu-id="9331d-113">通过指定由服务公开的服务终结点，创建基本路由服务配置。</span><span class="sxs-lookup"><span data-stu-id="9331d-113">Create the basic Routing Service configuration by specifying the service endpoints exposed by the service.</span></span> <span data-ttu-id="9331d-114">下面的示例定义了两个用于接收消息的终结点，</span><span class="sxs-lookup"><span data-stu-id="9331d-114">The following example defines two endpoints, which will be used to receive messages.</span></span> <span data-ttu-id="9331d-115">还定义了客户端终结点，这些客户端终结点用于将消息发送到 regularCalc 服务实例。</span><span class="sxs-lookup"><span data-stu-id="9331d-115">It also defines the client endpoints, which are used to send messages to the regularCalc service instances.</span></span>  
  
    ```xml  
    <services>  
      <service behaviorConfiguration="routingConfiguration"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost/routingservice/router" />  
          </baseAddresses>  
        </host>  
        <!--Set up the inbound endpoints for the Routing Service-->  
        <!--create the endpoints for the calculator service-->  
        <endpoint address="calculator1"  
                  binding="wsHttpBinding"  
                  name="calculator1Endpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <endpoint address="calculator2"  
                  binding="wsHttpBinding"  
                  name="calculator2Endpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
       </service>  
    </services>  
    <client>  
    <!--set up the destination endpoints-->  
        <endpoint name="CalcEndpoint1"  
                  address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                  binding="netTcpBinding"  
                  contract="*" />  
  
        <endpoint name="CalcEndpoint2"  
                  address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                  binding="netTcpBinding"  
                  contract="*" />  
     </client>  
    ```  
  
2. <span data-ttu-id="9331d-116">定义用于将消息路由到目标终结点的筛选器。</span><span class="sxs-lookup"><span data-stu-id="9331d-116">Define the filters used to route messages to the destination endpoints.</span></span>  <span data-ttu-id="9331d-117">对于本示例，EndpointName 筛选器用于确定哪个服务终结点接收消息。</span><span class="sxs-lookup"><span data-stu-id="9331d-117">For this example, the EndpointName filter is used to determine which service endpoint received the message.</span></span> <span data-ttu-id="9331d-118">下面的示例定义所需的路由节和筛选器。</span><span class="sxs-lookup"><span data-stu-id="9331d-118">The following example defines the necessary routing section and filters.</span></span>  
  
    ```xml  
    <filters>  
      <!--define the different message filters-->  
      <!--define endpoint name filters looking for messages that show up on the virtual endpoints-->  
      <filter name="HighPriority" filterType="EndpointName"  
              filterData="calculator1Endpoint"/>  
      <filter name="NormalPriority" filterType="EndpointName"  
              filterData="calculator2Endpoint"/>  
    </filters>  
    ```  
  
3. <span data-ttu-id="9331d-119">定义筛选器表，该表将各个筛选器与客户端终结点相关联。</span><span class="sxs-lookup"><span data-stu-id="9331d-119">Define the filter table, which associates each filter with a client endpoint.</span></span> <span data-ttu-id="9331d-120">在本示例中，将根据通过其接收消息的特定终结点路由消息。</span><span class="sxs-lookup"><span data-stu-id="9331d-120">In this example, the message will be routed based on the specific endpoint it was received over.</span></span> <span data-ttu-id="9331d-121">由于消息只能与两个可能的过滤器之一匹配，因此无需使用筛选器优先级控制筛选器的求值顺序。</span><span class="sxs-lookup"><span data-stu-id="9331d-121">Since the message can only match one of the two possible filters, there is no need for using filter priority to control to the order in which filters are evaluated.</span></span>  
  
     <span data-ttu-id="9331d-122">以下代码定义筛选器表并添加前面定义的筛选器。</span><span class="sxs-lookup"><span data-stu-id="9331d-122">The following defines the filter table and adds the filters defined earlier.</span></span>  
  
    ```xml  
    <filterTables>  
       <filterTable name="filterTable1">  
         <!--add the filters to the message filter table-->  
         <add filterName="HighPriority" endpointName="CalcEndpoint1"/>  
         <add filterName="NormalPriority" endpointName="CalcEndpoint2"/>  
       </filterTable>  
    </filterTables>  
    ```  
  
4. <span data-ttu-id="9331d-123">若要根据表中包含的筛选器对传入消息求值，必须使用路由行为将筛选器表与服务终结点关联。</span><span class="sxs-lookup"><span data-stu-id="9331d-123">To evaluate incoming messages against the filters contained in the table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span> <span data-ttu-id="9331d-124">下面的示例演示如何将 "filterTable1" 与服务终结点相关联：</span><span class="sxs-lookup"><span data-stu-id="9331d-124">The following example demonstrates associating "filterTable1" with the service endpoints:</span></span>  
  
    ```xml  
    <behaviors>  
      <!--default routing service behavior definition-->  
      <serviceBehaviors>  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
## <a name="example"></a><span data-ttu-id="9331d-125">示例</span><span class="sxs-lookup"><span data-stu-id="9331d-125">Example</span></span>  

 <span data-ttu-id="9331d-126">下面是配置文件的完整代码清单。</span><span class="sxs-lookup"><span data-stu-id="9331d-126">The following is a complete listing of the configuration file.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright (c) Microsoft Corporation. All rights reserved -->  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service behaviorConfiguration="routingConfiguration"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost/routingservice/router" />  
          </baseAddresses>  
        </host>  
        <!--Set up the inbound endpoints for the Routing Service-->  
        <!--create the endpoints for the calculator service-->  
        <endpoint address="calculator1"  
                  binding="wsHttpBinding"  
                  name="calculator1Endpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <endpoint address="calculator2"  
                  binding="wsHttpBinding"  
                  name="calculator2Endpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
  
      </service>  
    </services>  
    <behaviors>  
      <!--default routing service behavior definition-->  
      <serviceBehaviors>  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
    <client>  
<!--set up the destination endpoints-->  
      <endpoint name="CalcEndpoint1"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
  
      <endpoint name="CalcEndpoint2"  
                address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
    </client>  
    <routing>  
      <!-- use the namespace table element to define a prefix for our custom namespace-->  
  
      <filters>  
        <!--define the different message filters-->  
        <!--define endpoint name filters looking for messages that show up on the virtual endpoints-->  
        <filter name="HighPriority" filterType="EndpointName"  
                filterData="calculator1Endpoint"/>  
        <filter name="NormalPriority" filterType="EndpointName"  
                filterData="calculator2Endpoint"/>  
      </filters>  
  
      <filterTables>  
        <filterTable name="filterTable1">  
          <!--add the filters to the message filter table-->  
          <add filterName="HighPriority" endpointName="CalcEndpoint1"/>  
          <add filterName="NormalPriority" endpointName="CalcEndpoint2"/>  
        </filterTable>  
      </filterTables>  
  
    </routing>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9331d-127">请参阅</span><span class="sxs-lookup"><span data-stu-id="9331d-127">See also</span></span>

- [<span data-ttu-id="9331d-128">路由服务</span><span class="sxs-lookup"><span data-stu-id="9331d-128">Routing Services</span></span>](../samples/routing-services.md)
