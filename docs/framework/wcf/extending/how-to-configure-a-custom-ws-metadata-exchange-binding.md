---
description: 了解详细信息：如何：配置自定义 WS-Metadata Exchange 绑定
title: 如何：配置自定义 WS-Metadata Exchange 绑定
ms.date: 03/30/2017
helpviewer_keywords:
- WS-Metadata Exchange [WCF]
- WS-Metadata Exchange [WCF], configuring a custom binding
ms.assetid: cdba4d73-da64-4805-bc56-9822becfd1e4
ms.openlocfilehash: ae9d1932e7539d25c117a98bd130d1def8e691fe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743728"
---
# <a name="how-to-configure-a-custom-ws-metadata-exchange-binding"></a>如何：配置自定义 WS-Metadata Exchange 绑定

本文介绍如何配置自定义 WS-Metadata exchange 绑定。 Windows Communication Foundation (WCF) 包括四个系统定义的元数据绑定，但您可以使用所需的任何绑定来发布元数据。 本文说明如何使用发布元数据 `wsHttpBinding` 。 此绑定提供了以安全方式公开元数据的选择。 本文中的代码基于 [入门](../samples/getting-started-sample.md)。  
  
### <a name="using-a-configuration-file"></a>使用配置文件  
  
1. 在服务的配置文件中，添加一个包含 `serviceMetadata` 标记的服务行为：  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
           <serviceMetadata httpGetEnabled="True"/>  
         </behavior>  
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
2. 将一个 `behaviorConfiguration` 属性添加到该服务标记，该属性引用这一新行为：  
  
    ```xml  
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior" />
    ```  
  
3. 添加一个元数据终结点，该终结点将 mex 指定为地址，将 `wsHttpBinding` 指定为绑定，并将 <xref:System.ServiceModel.Description.IMetadataExchange> 指定为协定：  
  
    ```xml  
    <endpoint address="mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange" />  
    ```  
  
4. 若要验证元数据交换终结点是否正常工作，请在客户端配置文件中添加一个终结点标记：  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
5. 在客户端的 Main() 方法中，创建一个新的 <xref:System.ServiceModel.Description.MetadataExchangeClient> 实例，将该实例的 <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> 属性设置为 `true`，调用 <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>，然后循环访问返回的元数据集合：  
  
    ```csharp
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
### <a name="configuring-by-code"></a>通过代码进行配置  
  
1. 创建一个 <xref:System.ServiceModel.WSHttpBinding> 绑定实例：  
  
    ```csharp  
    WSHttpBinding binding = new WSHttpBinding();  
    ```  
  
2. 创建一个 <xref:System.ServiceModel.ServiceHost> 实例：  
  
    ```csharp  
    ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
    ```  
  
3. 添加一个服务终结点，并添加一个 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 实例：  
  
    ```csharp  
    serviceHost.AddServiceEndpoint(typeof(ICalculator), binding, baseAddress);  
    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
    smb.HttpGetEnabled = true;  
    serviceHost.Description.Behaviors.Add(smb);  
    ```  
  
4. 添加一个元数据交换终结点，并且指定先前创建的 <xref:System.ServiceModel.WSHttpBinding>：  
  
    ```csharp  
    serviceHost.AddServiceEndpoint(typeof(IMetadataExchange), binding, mexAddress);  
    ```  
  
5. 若要验证元数据交换终结点是否能够正常工作，请在客户端配置文件中添加一个终结点标记：  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
6. 在客户端的 Main() 方法中，创建一个新的 <xref:System.ServiceModel.Description.MetadataExchangeClient> 实例，将该实例的 <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> 属性设置为 `true`，调用 <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>，然后循环访问返回的元数据集合：  
  
    ```csharp  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
## <a name="see-also"></a>请参阅

- [元数据发布行为](../samples/metadata-publishing-behavior.md)
- [检索元数据](../samples/retrieve-metadata.md)
- Metadata 
- [发布元数据](../feature-details/publishing-metadata.md)
- [发布元数据终结点](../publishing-metadata-endpoints.md)
