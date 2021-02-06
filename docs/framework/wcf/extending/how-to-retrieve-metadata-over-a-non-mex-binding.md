---
description: 了解详细信息：如何：通过非 MEX 绑定检索元数据
title: 如何：通过非 MEX 绑定检索元数据
ms.date: 03/30/2017
ms.assetid: 2292e124-81b2-4317-b881-ce9c1ec66ecb
ms.openlocfilehash: 521e48d90e9dbed2e0ded61c60af59d063d2b3dc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99644211"
---
# <a name="how-to-retrieve-metadata-over-a-non-mex-binding"></a><span data-ttu-id="c69b8-103">如何：通过非 MEX 绑定检索元数据</span><span class="sxs-lookup"><span data-stu-id="c69b8-103">How to: Retrieve Metadata Over a non-MEX Binding</span></span>

<span data-ttu-id="c69b8-104">本主题介绍如何通过非 MEX 绑定从 MEX 终结点检索元数据。</span><span class="sxs-lookup"><span data-stu-id="c69b8-104">This topic describes how to retrieve metadata from a MEX endpoint over a non-MEX binding.</span></span> <span data-ttu-id="c69b8-105">此示例中的代码基于 [自定义安全元数据终结点](../samples/custom-secure-metadata-endpoint.md) 示例。</span><span class="sxs-lookup"><span data-stu-id="c69b8-105">The code in this sample is based on the [Custom Secure Metadata Endpoint](../samples/custom-secure-metadata-endpoint.md) sample.</span></span>  
  
### <a name="to-retrieve-metadata-over-a-non-mex-binding"></a><span data-ttu-id="c69b8-106">通过非 MEX 绑定检索元数据</span><span class="sxs-lookup"><span data-stu-id="c69b8-106">To retrieve metadata over a non-MEX binding</span></span>  
  
1. <span data-ttu-id="c69b8-107">确定由 MEX 终结点使用的绑定。</span><span class="sxs-lookup"><span data-stu-id="c69b8-107">Determine the binding used by the MEX endpoint.</span></span> <span data-ttu-id="c69b8-108">对于 Windows Communication Foundation (WCF) 服务，可以通过访问服务的配置文件来确定 MEX 绑定。</span><span class="sxs-lookup"><span data-stu-id="c69b8-108">For Windows Communication Foundation (WCF) services, you can determine the MEX binding by accessing the service's configuration file.</span></span> <span data-ttu-id="c69b8-109">在本例中，MEX 绑定在以下服务配置中定义。</span><span class="sxs-lookup"><span data-stu-id="c69b8-109">In this case, the MEX binding is defined in the following service configuration.</span></span>  
  
    ```xml  
    <services>  
        <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
                behaviorConfiguration="CalculatorServiceBehavior">  
         <!-- Use the base address provided by the host. -->  
         <endpoint address=""  
           binding="wsHttpBinding"  
           bindingConfiguration="Binding2"  
           contract="Microsoft.ServiceModel.Samples.ICalculator" />  
         <endpoint address="mex"  
           binding="wsHttpBinding"  
           bindingConfiguration="Binding1"  
           contract="IMetadataExchange" />  
         </service>  
     </services>  
     <bindings>  
       <wsHttpBinding>  
         <binding name="Binding1">  
           <security mode="Message">  
             <message clientCredentialType="Certificate" />  
           </security>  
         </binding>  
         <binding name="Binding2">  
           <reliableSession inactivityTimeout="00:01:00" enabled="true" />  
           <security mode="Message">  
             <message clientCredentialType="Certificate" />  
           </security>  
         </binding>  
       </wsHttpBinding>  
     </bindings>  
    ```  
  
2. <span data-ttu-id="c69b8-110">在客户端配置文件中，配置同样的自定义绑定。</span><span class="sxs-lookup"><span data-stu-id="c69b8-110">In the client configuration file, configure the same custom binding.</span></span> <span data-ttu-id="c69b8-111">在该配置文件中，客户端还定义了一个 `clientCredentials` 行为以提供证书，用于在请求 MEX 终结点中的元数据时对服务进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="c69b8-111">Here the client also defines a `clientCredentials` behavior to provide a certificate to use to authenticate to the service when requesting metadata from the MEX endpoint.</span></span> <span data-ttu-id="c69b8-112">在使用 Svcutil.exe 通过自定义绑定请求元数据时，应向 Svcutil.exe 的配置文件 (Svcutil.exe.config) 中添加 MEX 终结点配置，并且终结点配置的名称应与 MEX 终结点地址的 URI 架构匹配，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="c69b8-112">When using Svcutil.exe to request metadata over a custom binding, you should add the MEX endpoint configuration to the configuration file for Svcutil.exe (Svcutil.exe.config), and the name of the endpoint configuration should match the URI scheme of the address of the MEX endpoint, as shown in the following code.</span></span>  
  
    ```xml  
    <system.serviceModel>  
      <client>  
        <endpoint name="http"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="Binding1"  
                  behaviorConfiguration="ClientCertificateBehavior"  
                  contract="IMetadataExchange" />  
      </client>  
      <bindings>  
        <wsHttpBinding>  
          <binding name="Binding1">  
            <security mode="Message">  
              <message clientCredentialType="Certificate"/>  
            </security>  
          </binding>  
        </wsHttpBinding>  
      </bindings>  
      <behaviors>  
        <endpointBehaviors>  
          <behavior name="ClientCertificateBehavior">  
            <clientCredentials>  
              <clientCertificate findValue="client.com" storeLocation="CurrentUser" storeName="My" x509FindType="FindBySubjectName" />  
              <serviceCertificate>  
                <authentication certificateValidationMode="PeerOrChainTrust" />  
              </serviceCertificate>  
            </clientCredentials>  
          </behavior>  
        </endpointBehaviors>  
      </behaviors>
    </system.serviceModel>  
    ```  
  
3. <span data-ttu-id="c69b8-113">创建一个 `MetadataExchangeClient` 并调用 `GetMetadata`。</span><span class="sxs-lookup"><span data-stu-id="c69b8-113">Create a `MetadataExchangeClient` and call `GetMetadata`.</span></span> <span data-ttu-id="c69b8-114">有两种方法可以完成此操作：在配置中指定自定义绑定，或在代码中指定自定义绑定，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="c69b8-114">There are two ways to do this: you can specify the custom binding in configuration, or you can specify the custom binding in code, as shown in the following example.</span></span>  
  
    ```csharp
    // The custom binding is specified in configuration.  
    EndpointAddress mexAddress = new EndpointAddress("http://localhost:8000/ServiceModelSamples/Service/mex");  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("http");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mexSet = mexClient.GetMetadata(mexAddress);  
  
    // The custom binding is specified in code.  
    // Specify the Metadata Exchange binding and its security mode.  
    WSHttpBinding mexBinding = new WSHttpBinding(SecurityMode.Message);  
    mexBinding.Security.Message.ClientCredentialType = MessageCredentialType.Certificate;  
  
    // Create a MetadataExchangeClient and set the certificate details.  
    MetadataExchangeClient mexClient = new MetadataExchangeClient(mexBinding);  
    mexClient.SoapCredentials.ClientCertificate.SetCertificate(  
        StoreLocation.CurrentUser, StoreName.My,  
        X509FindType.FindBySubjectName, "client.com");  
    mexClient.SoapCredentials.ServiceCertificate.Authentication.  
        CertificateValidationMode =  
        X509CertificateValidationMode.PeerOrChainTrust;  
    mexClient.SoapCredentials.ServiceCertificate.SetDefaultCertificate(  
        StoreLocation.CurrentUser, StoreName.TrustedPeople,  
        X509FindType.FindBySubjectName, "localhost");  
    MetadataExchangeClient mexClient2 = new MetadataExchangeClient(customBinding);  
    mexClient2.ResolveMetadataReferences = true;  
    MetadataSet mexSet2 = mexClient2.GetMetadata(mexAddress);  
    ```  
  
4. <span data-ttu-id="c69b8-115">创建 `WsdlImporter` 并调用 `ImportAllEndpoints`，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="c69b8-115">Create a `WsdlImporter` and call `ImportAllEndpoints`, as shown in the following code.</span></span>  
  
    ```csharp
    WsdlImporter importer = new WsdlImporter(mexSet);  
    ServiceEndpointCollection endpoints = importer.ImportAllEndpoints();  
    ```  
  
5. <span data-ttu-id="c69b8-116">此时，您拥有服务终结点的集合。</span><span class="sxs-lookup"><span data-stu-id="c69b8-116">At this point, you have a collection of service endpoints.</span></span> <span data-ttu-id="c69b8-117">有关导入元数据的详细信息，请参阅 [如何：将元数据导入服务终结点](../feature-details/how-to-import-metadata-into-service-endpoints.md)。</span><span class="sxs-lookup"><span data-stu-id="c69b8-117">For more information about importing metadata, see [How to: Import Metadata into Service Endpoints](../feature-details/how-to-import-metadata-into-service-endpoints.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c69b8-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="c69b8-118">See also</span></span>

- <span data-ttu-id="c69b8-119">Metadata </span><span class="sxs-lookup"><span data-stu-id="c69b8-119">[Metadata](../feature-details/metadata.md)</span></span>
