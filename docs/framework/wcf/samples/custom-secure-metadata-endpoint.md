---
description: 了解详细信息：自定义安全元数据终结点
title: 自定义安全元数据终结点
ms.date: 03/30/2017
ms.assetid: 9e369e99-ea4a-49ff-aed2-9fdf61091a48
ms.openlocfilehash: 11b8439fda74924ff17a101d3aa0b0db948ff8dd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752452"
---
# <a name="custom-secure-metadata-endpoint"></a><span data-ttu-id="b6c74-103">自定义安全元数据终结点</span><span class="sxs-lookup"><span data-stu-id="b6c74-103">Custom Secure Metadata Endpoint</span></span>

<span data-ttu-id="b6c74-104">此示例演示如何实现一个具有安全元数据终结点（该终结点使用一个非元数据交换绑定）的服务，以及如何配置 [ ( # A0) ](../servicemodel-metadata-utility-tool-svcutil-exe.md) 或客户端从这类元数据终结点获取元数据的安全元数据终结点。</span><span class="sxs-lookup"><span data-stu-id="b6c74-104">This sample demonstrates how to implement a service with a secure metadata endpoint that uses one of the non-metadata exchange bindings, and how to configure [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) or clients to fetch the metadata from such a metadata endpoint.</span></span> <span data-ttu-id="b6c74-105">有两个系统提供的绑定可供公开元数据终结点：mexHttpBinding 和 mexHttpsBinding。</span><span class="sxs-lookup"><span data-stu-id="b6c74-105">There are two system-provided bindings available for exposing metadata endpoints: mexHttpBinding and mexHttpsBinding.</span></span> <span data-ttu-id="b6c74-106">mexHttpBinding 用于以非安全的方式，通过 HTTP 公开元数据终结点。</span><span class="sxs-lookup"><span data-stu-id="b6c74-106">mexHttpBinding is used to expose a metadata endpoint over HTTP in a non-secure manner.</span></span> <span data-ttu-id="b6c74-107">mexHttpsBinding 用于以安全的方式，通过 HTTP 公开元数据终结点。</span><span class="sxs-lookup"><span data-stu-id="b6c74-107">mexHttpsBinding is used to expose a metadata endpoint over HTTPS in a secure manner.</span></span> <span data-ttu-id="b6c74-108">本示例演示如何使用 <xref:System.ServiceModel.WSHttpBinding> 公开安全元数据终结点。</span><span class="sxs-lookup"><span data-stu-id="b6c74-108">This sample illustrates how to expose a secure metadata endpoint using the <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="b6c74-109">要更改绑定的安全设置但不想使用 HTTPS 时需要这样做。</span><span class="sxs-lookup"><span data-stu-id="b6c74-109">You would want to do this when you want to change the security settings on the binding, but you do not want to use HTTPS.</span></span> <span data-ttu-id="b6c74-110">如果使用 mexHttpsBinding，则元数据终结点是安全的，但无法修改绑定设置。</span><span class="sxs-lookup"><span data-stu-id="b6c74-110">If you use the mexHttpsBinding your metadata endpoint will be secure, but there is no way to modify the binding settings.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b6c74-111">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="b6c74-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="service"></a><span data-ttu-id="b6c74-112">服务</span><span class="sxs-lookup"><span data-stu-id="b6c74-112">Service</span></span>  

 <span data-ttu-id="b6c74-113">本示例中的服务有两个终结点。</span><span class="sxs-lookup"><span data-stu-id="b6c74-113">The service in this sample has two endpoints.</span></span> <span data-ttu-id="b6c74-114">应用程序终结点可用于 `ICalculator` 上的 `WSHttpBinding` 协定，其中启用了 `ReliableSession` 并且 `Message` 安全性为使用证书。</span><span class="sxs-lookup"><span data-stu-id="b6c74-114">The application endpoint serves the `ICalculator` contract on a `WSHttpBinding` with `ReliableSession` enabled and `Message` security using certificates.</span></span> <span data-ttu-id="b6c74-115">元数据终结点还使用具有相同安全设置但没有 `WSHttpBinding` 的 `ReliableSession`。</span><span class="sxs-lookup"><span data-stu-id="b6c74-115">The metadata endpoint also uses `WSHttpBinding`, with the same security settings but with no `ReliableSession`.</span></span> <span data-ttu-id="b6c74-116">下面是相关的配置：</span><span class="sxs-lookup"><span data-stu-id="b6c74-116">Here is the relevant configuration:</span></span>  
  
```xml  
<services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
     <!-- use base address provided by host -->  
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
  
 <span data-ttu-id="b6c74-117">在很多其他示例中，元数据终结点使用默认 `mexHttpBinding`，这样会不安全。</span><span class="sxs-lookup"><span data-stu-id="b6c74-117">In many of the other samples, the metadata endpoint uses the default `mexHttpBinding`, which is not secure.</span></span> <span data-ttu-id="b6c74-118">下面是使用具有 `WSHttpBinding` 安全性的 `Message` 来保护的元数据。</span><span class="sxs-lookup"><span data-stu-id="b6c74-118">Here the metadata is secured using `WSHttpBinding` with `Message` security.</span></span> <span data-ttu-id="b6c74-119">为了使元数据客户端能够检索此元数据，必须用匹配的绑定来配置这些客户端。</span><span class="sxs-lookup"><span data-stu-id="b6c74-119">In order for metadata clients to retrieve this metadata, they must be configured with a matching binding.</span></span> <span data-ttu-id="b6c74-120">本示例演示两个此类客户端。</span><span class="sxs-lookup"><span data-stu-id="b6c74-120">This sample demonstrates two such clients.</span></span>  
  
 <span data-ttu-id="b6c74-121">第一个客户端使用 Svcutil.exe 提取元数据并在设计时生成客户端代码和配置。</span><span class="sxs-lookup"><span data-stu-id="b6c74-121">The first client uses Svcutil.exe to fetch the metadata and generate client code and configuration at design time.</span></span> <span data-ttu-id="b6c74-122">由于服务针对元数据使用非默认绑定，因此必须专门配置 Svcutil.exe 工具，以便此工具能够使用该绑定从服务中获取元数据。</span><span class="sxs-lookup"><span data-stu-id="b6c74-122">Because the service uses a non-default binding for the metadata, the Svcutil.exe tool must be specifically configured so that it can get the metadata from the service using that binding.</span></span>  
  
 <span data-ttu-id="b6c74-123">第二个客户端使用 `MetadataResolver` 动态提取已知协定的元数据，然后在动态生成的客户端上调用操作。</span><span class="sxs-lookup"><span data-stu-id="b6c74-123">The second client uses the `MetadataResolver` to dynamically fetch the metadata for a known contract and then invoke operations on the dynamically generated client.</span></span>  
  
## <a name="svcutil-client"></a><span data-ttu-id="b6c74-124">Svcutil 客户端</span><span class="sxs-lookup"><span data-stu-id="b6c74-124">Svcutil client</span></span>  

 <span data-ttu-id="b6c74-125">当使用默认绑定承载您的 `IMetadataExchange` 终结点时，可以使用该终结点的地址运行 Svcutil.exe：</span><span class="sxs-lookup"><span data-stu-id="b6c74-125">When using the default binding to host your `IMetadataExchange` endpoint, you can run Svcutil.exe with the address of that endpoint:</span></span>  
  
```console  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="b6c74-126">它正常工作。</span><span class="sxs-lookup"><span data-stu-id="b6c74-126">and it works.</span></span> <span data-ttu-id="b6c74-127">但在本示例中，服务器使用非默认终结点承载元数据。</span><span class="sxs-lookup"><span data-stu-id="b6c74-127">But in this sample, the server uses a non-default endpoint to host the metadata.</span></span> <span data-ttu-id="b6c74-128">因此，必须指示 Svcutil.exe 使用正确的绑定。</span><span class="sxs-lookup"><span data-stu-id="b6c74-128">So Svcutil.exe must be instructed to use the correct binding.</span></span> <span data-ttu-id="b6c74-129">使用 Svcutil.exe.config 文件可以实现此目标。</span><span class="sxs-lookup"><span data-stu-id="b6c74-129">This can be done using a Svcutil.exe.config file.</span></span>  
  
 <span data-ttu-id="b6c74-130">Svcutil.exe.config 文件类似于普通的客户端配置文件。</span><span class="sxs-lookup"><span data-stu-id="b6c74-130">The Svcutil.exe.config file looks like a normal client configuration file.</span></span> <span data-ttu-id="b6c74-131">唯一不同之处是客户端终结点名称和协定：</span><span class="sxs-lookup"><span data-stu-id="b6c74-131">The only unusual aspects are the client endpoint name and contract:</span></span>  
  
```xml  
<endpoint name="http"  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"  
          behaviorConfiguration="ClientCertificateBehavior"  
          contract="IMetadataExchange" />  
```  
  
 <span data-ttu-id="b6c74-132">终结点名称必须是承载该元数据的地址的方案名称，终结点协定必须为 `IMetadataExchange`。</span><span class="sxs-lookup"><span data-stu-id="b6c74-132">The endpoint name must be the name of the scheme of the address where the metadata is hosted and the endpoint contract must be `IMetadataExchange`.</span></span> <span data-ttu-id="b6c74-133">因此，当使用如下所示的命令行运行 Svcutil.exe 时：</span><span class="sxs-lookup"><span data-stu-id="b6c74-133">Thus, when Svcutil.exe is run with a command-line such as the following:</span></span>  
  
```console  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="b6c74-134">它查找名为“http”的终结点和 `IMetadataExchange` 协定，以使用元数据终结点配置通信交换的绑定和行为。</span><span class="sxs-lookup"><span data-stu-id="b6c74-134">it looks for the endpoint named "http" and contract `IMetadataExchange` to configure the binding and behavior of the communication exchange with the metadata endpoint.</span></span> <span data-ttu-id="b6c74-135">示例中的 Svcutil.exe.config 文件的其余部分指定绑定配置和行为凭据以与元数据终结点的服务器配置相匹配。</span><span class="sxs-lookup"><span data-stu-id="b6c74-135">The rest of the Svcutil.exe.config file in the sample specifies the binding configuration and behavior credentials to match the server's configuration of the metadata endpoint.</span></span>  
  
 <span data-ttu-id="b6c74-136">为了使 Svcutil.exe 能够在 Svcutil.exe.config 中选取配置，Svcutil.exe 必须与该配置文件位于同一目录中。</span><span class="sxs-lookup"><span data-stu-id="b6c74-136">In order for Svcutil.exe to pick up the configuration in Svcutil.exe.config, Svcutil.exe must be in the same directory as the configuration file.</span></span> <span data-ttu-id="b6c74-137">因此，您必须将 Svcutil.exe 从其安装位置复制到包含 Svcutil.exe.config 文件的目录中。</span><span class="sxs-lookup"><span data-stu-id="b6c74-137">As a result, you must copy Svcutil.exe from its install location to the directory that contains the Svcutil.exe.config file.</span></span> <span data-ttu-id="b6c74-138">然后，从该目录中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="b6c74-138">Then from that directory, run the following command:</span></span>  
  
```console  
.\svcutil.exe http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="b6c74-139">前导 ". \\ "确保在此目录中 Svcutil.exe 的副本 (具有相应 Svcutil.exe.config) 运行的副本。</span><span class="sxs-lookup"><span data-stu-id="b6c74-139">The leading ".\\" ensures that the copy of Svcutil.exe in this directory (the one which has a corresponding Svcutil.exe.config) is run.</span></span>  
  
## <a name="metadataresolver-client"></a><span data-ttu-id="b6c74-140">MetadataResolver 客户端</span><span class="sxs-lookup"><span data-stu-id="b6c74-140">MetadataResolver client</span></span>  

 <span data-ttu-id="b6c74-141">如果客户端在设计时知道协定和如何与元数据交谈，客户端就可以使用 `MetadataResolver` 动态找到应用程序终结点的绑定和地址。</span><span class="sxs-lookup"><span data-stu-id="b6c74-141">If the client knows the contract and how to talk to the metadata at design time, the client can dynamically find out the binding and address of application endpoints using the `MetadataResolver`.</span></span> <span data-ttu-id="b6c74-142">本示例客户端对此进行了演示，显示如何通过创建和配置 `MetadataResolver` 来配置 `MetadataExchangeClient` 使用的绑定和凭据。</span><span class="sxs-lookup"><span data-stu-id="b6c74-142">This sample client demonstrates this, showing how to configure the binding and credentials used by `MetadataResolver` by creating and configuring a `MetadataExchangeClient`.</span></span>  
  
 <span data-ttu-id="b6c74-143">可以在 `MetadataExchangeClient` 上强制指定 Svcutil.exe.config 中出现的相同绑定和证书信息：</span><span class="sxs-lookup"><span data-stu-id="b6c74-143">The same binding and certificate information that appeared in Svcutil.exe.config can be specified imperatively on the `MetadataExchangeClient`:</span></span>  
  
```csharp  
// Specify the Metadata Exchange binding and its security mode  
WSHttpBinding mexBinding = new WSHttpBinding(SecurityMode.Message);  
mexBinding.Security.Message.ClientCredentialType = MessageCredentialType.Certificate;  
  
// Create a MetadataExchangeClient for retrieving metadata, and set the // certificate details  
MetadataExchangeClient mexClient = new MetadataExchangeClient(mexBinding);  
mexClient.SoapCredentials.ClientCertificate.SetCertificate(    StoreLocation.CurrentUser, StoreName.My,  
    X509FindType.FindBySubjectName, "client.com");  
mexClient.SoapCredentials.ServiceCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
mexClient.SoapCredentials.ServiceCertificate.SetDefaultCertificate(    StoreLocation.CurrentUser, StoreName.TrustedPeople,  
    X509FindType.FindBySubjectName, "localhost");  
```  
  
 <span data-ttu-id="b6c74-144">配置完 `mexClient`，我们可以枚举感兴趣的协定并使用 `MetadataResolver` 提取使用这些协定的终结点的列表：</span><span class="sxs-lookup"><span data-stu-id="b6c74-144">With the `mexClient` configured, we can enumerate the contracts we are interested in, and use `MetadataResolver` to fetch a list of endpoints with those contracts:</span></span>  
  
```csharp  
// The contract we want to fetch metadata for  
Collection<ContractDescription> contracts = new Collection<ContractDescription>();  
ContractDescription contract = ContractDescription.GetContract(typeof(ICalculator));  
contracts.Add(contract);  
// Find endpoints for that contract  
EndpointAddress mexAddress = new EndpointAddress(ConfigurationManager.AppSettings["mexAddress"]);  
ServiceEndpointCollection endpoints = MetadataResolver.Resolve(contracts, mexAddress, mexClient);  
```  
  
 <span data-ttu-id="b6c74-145">最后，我们可以使用这些终结点中的信息初始化 `ChannelFactory`（用于创建与应用程序终结点通信的通道）的绑定和地址。</span><span class="sxs-lookup"><span data-stu-id="b6c74-145">Finally we can use the information from those endpoints to initialize the binding and address of a `ChannelFactory` used to create channels to communicate with the application endpoints.</span></span>  
  
```csharp  
ChannelFactory<ICalculator> cf = new ChannelFactory<ICalculator>(endpoint.Binding, endpoint.Address);  
```  
  
 <span data-ttu-id="b6c74-146">本示例的关键之处在于演示：如果你要使用 `MetadataResolver`，则必须指定用于元数据交换通信的自定义绑定或行为，你可以使用 `MetadataExchangeClient` 指定这些自定义设置。</span><span class="sxs-lookup"><span data-stu-id="b6c74-146">The key point of this sample client is to demonstrate that, if you are using `MetadataResolver`, and you must specify custom bindings or behaviors for the metadata exchange communication, you can use a `MetadataExchangeClient` to specify those custom settings.</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="b6c74-147">设置和生成示例</span><span class="sxs-lookup"><span data-stu-id="b6c74-147">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="b6c74-148">确保已对 [Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="b6c74-148">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="b6c74-149">若要生成解决方案，请按照 [生成 Windows Communication Foundation 示例](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="b6c74-149">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="b6c74-150">在同一计算机上运行示例</span><span class="sxs-lookup"><span data-stu-id="b6c74-150">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="b6c74-151">运行示例安装文件夹中的 Setup.bat。</span><span class="sxs-lookup"><span data-stu-id="b6c74-151">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="b6c74-152">这将安装运行示例所需的所有证书。</span><span class="sxs-lookup"><span data-stu-id="b6c74-152">This installs all the certificates required for running the sample.</span></span> <span data-ttu-id="b6c74-153">请注意，Setup.bat 使用 FindPrivateKey.exe 工具，该工具是通过 [在 Windows Communication Foundation 示例的一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)中运行 setupCertTool.bat 而安装的。</span><span class="sxs-lookup"><span data-stu-id="b6c74-153">Note that Setup.bat uses the FindPrivateKey.exe tool, which is installed by running setupCertTool.bat from [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="b6c74-154">运行 \MetadataResolverClient\bin 或 \SvcutilClient\bin 中的客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="b6c74-154">Run the client application from \MetadataResolverClient\bin or \SvcutilClient\bin.</span></span> <span data-ttu-id="b6c74-155">客户端活动将显示在客户端控制台应用程序上。</span><span class="sxs-lookup"><span data-stu-id="b6c74-155">Client activity is displayed on the client console application.</span></span>  
  
3. <span data-ttu-id="b6c74-156">如果客户端和服务无法进行通信，请参阅 [WCF 示例的故障排除提示](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="b6c74-156">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
4. <span data-ttu-id="b6c74-157">在运行完该示例后运行 Cleanup.bat 移除证书。</span><span class="sxs-lookup"><span data-stu-id="b6c74-157">Remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="b6c74-158">其他安全示例使用相同的证书。</span><span class="sxs-lookup"><span data-stu-id="b6c74-158">Other security samples use the same certificates.</span></span>  
  
#### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="b6c74-159">跨计算机运行示例</span><span class="sxs-lookup"><span data-stu-id="b6c74-159">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="b6c74-160">在服务器上运行 `setup.bat service`。</span><span class="sxs-lookup"><span data-stu-id="b6c74-160">On the server, run `setup.bat service`.</span></span> <span data-ttu-id="b6c74-161">`setup.bat`使用参数运行将 `service` 使用计算机的完全限定的域名创建一个服务证书，并将服务证书导出到名为 .cer 的文件中。</span><span class="sxs-lookup"><span data-stu-id="b6c74-161">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the machine and exports the service certificate to a file named Service.cer.</span></span>  
  
2. <span data-ttu-id="b6c74-162">在服务器上，编辑 Web.config 以反映新证书名称。</span><span class="sxs-lookup"><span data-stu-id="b6c74-162">On the server, edit Web.config to reflect the new certificate name.</span></span> <span data-ttu-id="b6c74-163">也就是说，将 `findValue` 元素中的属性更改 [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) 为计算机的完全限定域名。</span><span class="sxs-lookup"><span data-stu-id="b6c74-163">That is, change the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) element to the fully-qualified domain name of the machine.</span></span>  
  
3. <span data-ttu-id="b6c74-164">将服务目录中的 Service.cer 文件复制到客户端计算机上的客户端目录中。</span><span class="sxs-lookup"><span data-stu-id="b6c74-164">Copy the Service.cer file from the service directory to the client directory on the client machine.</span></span>  
  
4. <span data-ttu-id="b6c74-165">在客户端上，运行 `setup.bat client`。</span><span class="sxs-lookup"><span data-stu-id="b6c74-165">On the client, run `setup.bat client`.</span></span> <span data-ttu-id="b6c74-166">`setup.bat`使用参数运行将 `client` 创建一个名为 Client.com 的客户端证书，并将客户端证书导出到名为的文件。</span><span class="sxs-lookup"><span data-stu-id="b6c74-166">Running `setup.bat` with the `client` argument creates a client certificate named Client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
5. <span data-ttu-id="b6c74-167">在客户端计算机上的 `MetadataResolverClient` 的 App.config 文件中，更改 Mex 终结点的地址值以与服务的新地址相匹配。</span><span class="sxs-lookup"><span data-stu-id="b6c74-167">In the App.config file of the `MetadataResolverClient` on the client machine, change the address value of the mex endpoint to match the new address of your service.</span></span> <span data-ttu-id="b6c74-168">通过使用服务器的完全限定域名替换 localhost 来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="b6c74-168">You do this by replacing localhost with the fully-qualified domain name of the server.</span></span> <span data-ttu-id="b6c74-169">还要将 metadataResolverClient.cs 文件中出现的“localhost”更改为新的服务证书名称（服务器的完全限定域名）。</span><span class="sxs-lookup"><span data-stu-id="b6c74-169">Also change the occurrence of "localhost" in the metadataResolverClient.cs file to the new service certificate name (the fully-qualified domain name of the server).</span></span> <span data-ttu-id="b6c74-170">对 SvcutilClient 项目的 App.config 执行相同的操作。</span><span class="sxs-lookup"><span data-stu-id="b6c74-170">Do the same thing for the App.config of the SvcutilClient project.</span></span>  
  
6. <span data-ttu-id="b6c74-171">将客户端目录中的 Client.cer 文件复制到服务器上的服务目录中。</span><span class="sxs-lookup"><span data-stu-id="b6c74-171">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
7. <span data-ttu-id="b6c74-172">在客户端上，运行 `ImportServiceCert.bat`。</span><span class="sxs-lookup"><span data-stu-id="b6c74-172">On the client, run `ImportServiceCert.bat`.</span></span> <span data-ttu-id="b6c74-173">这会将 Service.cer 文件中的服务证书导入 CurrentUser – TrustedPeople 存储区。</span><span class="sxs-lookup"><span data-stu-id="b6c74-173">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
8. <span data-ttu-id="b6c74-174">在服务器上，运行 `ImportClientCert.bat`，这会将 Client.cer 文件中的客户端证书导入 LocalMachine - TrustedPeople 存储区。</span><span class="sxs-lookup"><span data-stu-id="b6c74-174">On the server, run `ImportClientCert.bat`, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
9. <span data-ttu-id="b6c74-175">在服务计算机上，在 Visual Studio 中生成服务项目，在 Web 浏览器中选择帮助页可验证该项目是否在运行。</span><span class="sxs-lookup"><span data-stu-id="b6c74-175">On the service machine, build the service project in Visual Studio and select the help page in a web browser to verify that it is running.</span></span>  
  
10. <span data-ttu-id="b6c74-176">在客户端计算机上，运行 VS 中的 MetadataResolverClient 或 SvcutilClient。</span><span class="sxs-lookup"><span data-stu-id="b6c74-176">On the client machine, run the MetadataResolverClient or the SvcutilClient from VS.</span></span>  
  
    1. <span data-ttu-id="b6c74-177">如果客户端和服务无法进行通信，请参阅 [WCF 示例的故障排除提示](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="b6c74-177">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="b6c74-178">运行示例后进行清理</span><span class="sxs-lookup"><span data-stu-id="b6c74-178">To clean up after the sample</span></span>  
  
- <span data-ttu-id="b6c74-179">运行完示例后运行示例文件夹中的 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="b6c74-179">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="b6c74-180">此脚本不会在跨计算机运行此示例时移除客户端上的服务证书。</span><span class="sxs-lookup"><span data-stu-id="b6c74-180">This script does not remove service certificates on a client when running this sample across machines.</span></span> <span data-ttu-id="b6c74-181">如果已运行 Windows Communication Foundation 跨计算机使用证书 (WCF) 示例，请确保清除已安装在 CurrentUser-TrustedPeople 存储中的服务证书。</span><span class="sxs-lookup"><span data-stu-id="b6c74-181">If you have run Windows Communication Foundation (WCF) samples that use certificates across machines, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="b6c74-182">为此，请使用以下命令：`certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`。</span><span class="sxs-lookup"><span data-stu-id="b6c74-182">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`.</span></span> <span data-ttu-id="b6c74-183">例如：`certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`。</span><span class="sxs-lookup"><span data-stu-id="b6c74-183">For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b6c74-184">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="b6c74-184">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b6c74-185">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="b6c74-185">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="b6c74-186">如果此目录不存在，请参阅[Windows Communication Foundation (wcf) ，并 Windows Workflow Foundation (的 WF](https://www.microsoft.com/download/details.aspx?id=21459)) .NET Framework Windows Communication Foundation ([!INCLUDE[wf1](../../../../includes/wf1-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6c74-186">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b6c74-187">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="b6c74-187">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\CustomMexEndpoint`
