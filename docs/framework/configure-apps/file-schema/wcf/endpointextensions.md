---
description: 了解详细信息： <endpointExtensions>
title: <endpointExtensions>
ms.date: 03/30/2017
ms.assetid: 33396e0a-1fae-4616-b822-923584eebfd1
ms.openlocfilehash: d9684ccfab868b1b0d5fe9e054a3a97912712324
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664751"
---
# \<endpointExtensions>

<span data-ttu-id="681fc-102">此节在计算机或应用程序配置文件的扩展节中注册新的标准终结点。</span><span class="sxs-lookup"><span data-stu-id="681fc-102">This section registers a new standard endpoint in the extensions section in a machine or application configuration file.</span></span> <span data-ttu-id="681fc-103">您可以向此集合添加标准终结点，具体方法为：使用 `add` 关键字，然后将元素的 `type` 特性设置为终结点类型，并将 `name` 特性设置为标准终结点的名称。</span><span class="sxs-lookup"><span data-stu-id="681fc-103">You can add a standard endpoint to this collection by using the `add` keyword, and setting the `type` attribute of the element to the endpoint type, as well as the `name` attribute to the name of the standard endpoint.</span></span>  
  
 <span data-ttu-id="681fc-104">下面的示例使用 `add` 元素以及 `name` 特性将标准终结点添加到配置文件的 `<endpointExtensions>` 节。</span><span class="sxs-lookup"><span data-stu-id="681fc-104">The following example uses the `add` element, as well as the `name` attribute to add a standard endpoint to the `<endpointExtensions>` section of the configuration file.</span></span>  
  
```xml  
<system.serviceModel>
  <extensions>
    <endpointExtensions>
      <add name="udpDiscoveryEndpoint"
           type="System.Discovery.UdpEndpointCollectionElement, System.Discovery.dll, Version=1.0.0.0, Culture=neutral, PublicKeyToken=ffffffffffffffff"/>
    </endpointExtensions>
  </extensions>
</system.serviceModel>
```  
  
 <span data-ttu-id="681fc-105">在注册标准终结点之后，您可以按下例所示使用此终结点。</span><span class="sxs-lookup"><span data-stu-id="681fc-105">After the standard endpoint has been registered, you can use it as shown in the following example.</span></span> <span data-ttu-id="681fc-106">在 [\<endpoint>](endpoint-element.md) 元素中， `kind` 特性指定已在节中注册的标准终结点类型 `<endpointExtensions>` 。</span><span class="sxs-lookup"><span data-stu-id="681fc-106">In the [\<endpoint>](endpoint-element.md) element, the `kind` attribute specifies the standard endpoint type that has been registered in the `<endpointExtensions>` section.</span></span> <span data-ttu-id="681fc-107">`endpointConfiguration`特性将与 `name` 节中的标准终结点的配置元素的特性相同 `<standardEndpoints>` 。</span><span class="sxs-lookup"><span data-stu-id="681fc-107">The `endpointConfiguration` attribute will be identical to the `name` attribute of the configuration element of the standard endpoint in the `<standardEndpoints>` section.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service name="Service1">
      <endpoint kind="udpDiscoveryEndpoint"
                endpointConfiguration="udpConfig" />
    </service>
  </services>
  <standardEndpoints>
    <udpDiscoveryEndpoint>
      <standardEndpoint name="udpConfig"
                        multicastAddress="soap.udp://239.255.255.250:3703"
                        ... />
    </udpDiscoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
