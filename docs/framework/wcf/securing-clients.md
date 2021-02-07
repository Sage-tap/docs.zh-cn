---
description: 了解详细信息：保护客户端
title: 保证客户端的安全
ms.date: 03/30/2017
helpviewer_keywords:
- clients [WCF], security considerations
ms.assetid: 44c8578c-9a5b-4acd-8168-1c30a027c4c5
ms.openlocfilehash: d78ad2fba00a0707dcf1c63681d9d76e68a31c00
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99676438"
---
# <a name="securing-clients"></a><span data-ttu-id="3dbac-103">保证客户端的安全</span><span class="sxs-lookup"><span data-stu-id="3dbac-103">Securing Clients</span></span>

<span data-ttu-id="3dbac-104">在 Windows Communication Foundation (WCF) 中，该服务决定客户端的安全要求。</span><span class="sxs-lookup"><span data-stu-id="3dbac-104">In Windows Communication Foundation (WCF), the service dictates the security requirements for clients.</span></span> <span data-ttu-id="3dbac-105">即，由服务指定要使用的安全模式以及客户端是否必须提供凭据。</span><span class="sxs-lookup"><span data-stu-id="3dbac-105">That is, the service specifies what security mode to use, and whether or not the client must provide a credential.</span></span> <span data-ttu-id="3dbac-106">因此，保证客户端安全的过程非常简单：使用从服务那里获得的元数据（如果已发布）来生成客户端。</span><span class="sxs-lookup"><span data-stu-id="3dbac-106">The process of securing a client, therefore, is simple: use the metadata obtained from the service (if it is published) and build a client.</span></span> <span data-ttu-id="3dbac-107">元数据指定如何配置客户端。</span><span class="sxs-lookup"><span data-stu-id="3dbac-107">The metadata specifies how to configure the client.</span></span> <span data-ttu-id="3dbac-108">如果服务要求客户端提供凭据，您必须获得能够满足要求的凭据。</span><span class="sxs-lookup"><span data-stu-id="3dbac-108">If the service requires that the client supply a credential, then you must obtain a credential that fits the requirement.</span></span> <span data-ttu-id="3dbac-109">本主题进一步详细讨论此过程。</span><span class="sxs-lookup"><span data-stu-id="3dbac-109">This topic discusses the process in further detail.</span></span> <span data-ttu-id="3dbac-110">有关创建安全服务的详细信息，请参阅 [保护服务](securing-services.md)。</span><span class="sxs-lookup"><span data-stu-id="3dbac-110">For more information about creating a secure service, see [Securing Services](securing-services.md).</span></span>  
  
## <a name="the-service-specifies-security"></a><span data-ttu-id="3dbac-111">服务指定安全性</span><span class="sxs-lookup"><span data-stu-id="3dbac-111">The Service Specifies Security</span></span>  

 <span data-ttu-id="3dbac-112">默认情况下，WCF 绑定启用了安全功能。</span><span class="sxs-lookup"><span data-stu-id="3dbac-112">By default, WCF bindings have security features enabled.</span></span> <span data-ttu-id="3dbac-113"> (异常是 <xref:System.ServiceModel.BasicHttpBinding> 。 ) 因此，如果服务是使用 WCF 创建的，则更有可能实现安全性以确保身份验证、保密性和完整性。</span><span class="sxs-lookup"><span data-stu-id="3dbac-113">(The exception is the <xref:System.ServiceModel.BasicHttpBinding>.) Therefore, if the service was created using WCF, there is a greater chance that it will implement security to ensure authentication, confidentiality, and integrity.</span></span> <span data-ttu-id="3dbac-114">在这种情况下，服务提供的元数据将指示建立安全通信通道需要哪些条件。</span><span class="sxs-lookup"><span data-stu-id="3dbac-114">In that case, the metadata the service provides will indicate what it requires to establish a secure communication channel.</span></span> <span data-ttu-id="3dbac-115">如果服务元数据不包含安全要求，则无法对服务强行实施安全方案，例如 Secure Sockets Layer (SSL) over HTTP。</span><span class="sxs-lookup"><span data-stu-id="3dbac-115">If the service metadata does not include any security requirements, there is no way to impose a security scheme, such as Secure Sockets Layer (SSL) over HTTP, on a service.</span></span> <span data-ttu-id="3dbac-116">但是，如果服务要求客户端提供凭据，则客户端开发人员、部署人员或管理员必须提供客户端用来向该服务证明自己身份的实际凭据。</span><span class="sxs-lookup"><span data-stu-id="3dbac-116">If, however, the service requires the client to supply a credential, then the client developer, deployer, or administrator must supply the actual credential that the client will use to authenticate itself to the service.</span></span>  
  
## <a name="obtaining-metadata"></a><span data-ttu-id="3dbac-117">获取元数据</span><span class="sxs-lookup"><span data-stu-id="3dbac-117">Obtaining Metadata</span></span>  

 <span data-ttu-id="3dbac-118">创建客户端时，第一步是获取客户端将与其通信的服务的元数据。</span><span class="sxs-lookup"><span data-stu-id="3dbac-118">When creating a client, the first step is to obtain the metadata for the service that the client will communicate with.</span></span> <span data-ttu-id="3dbac-119">有两种方法可以做到这一点。</span><span class="sxs-lookup"><span data-stu-id="3dbac-119">This can be done in two ways.</span></span> <span data-ttu-id="3dbac-120">首先，如果服务发布了元数据交换 (MEX) 终结点或使其元数据可通过 HTTP 或 HTTPS 使用，则可以使用配置的 [元数据实用工具工具（该)  ( 工具 ](servicemodel-metadata-utility-tool-svcutil-exe.md)会为客户端和配置文件生成代码文件）下载元数据。</span><span class="sxs-lookup"><span data-stu-id="3dbac-120">First, if the service publishes a metadata exchange (MEX) endpoint or makes its metadata available over HTTP or HTTPS, you can download the metadata using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md), which generates both code files for a client as well as a configuration file.</span></span> <span data-ttu-id="3dbac-121"> (有关使用该工具的详细信息，请参阅 [使用 WCF 客户端访问服务](accessing-services-using-a-wcf-client.md)) 。如果服务未发布 MEX 终结点，并且未通过 HTTP 或 HTTPS 使其元数据可用，则必须与服务创建者联系，以获取描述安全要求和元数据的文档。</span><span class="sxs-lookup"><span data-stu-id="3dbac-121">(For more information about using the tool, see [Accessing Services Using a WCF Client](accessing-services-using-a-wcf-client.md).) If the service does not publish a MEX endpoint and also does not make its metadata available over HTTP or HTTPS, you must contact the service creator for documentation that describes the security requirements and the metadata.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3dbac-122">建议使用来自受信任的源且未被篡改的元数据。</span><span class="sxs-lookup"><span data-stu-id="3dbac-122">It is recommended that the metadata come from a trusted source and that it not be tampered with.</span></span> <span data-ttu-id="3dbac-123">使用 HTTP 协议检索到的元数据是以明文形式发送的，可能被篡改。</span><span class="sxs-lookup"><span data-stu-id="3dbac-123">Metadata retrieved using the HTTP protocol is sent in clear text and can be tampered with.</span></span> <span data-ttu-id="3dbac-124">如果服务使用 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> 和 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> 属性，请根据服务创建者提供的 URL，使用 HTTPS 协议下载数据。</span><span class="sxs-lookup"><span data-stu-id="3dbac-124">If the service uses the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> and <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> properties, use the URL the service creator supplied to download the data using the HTTPS protocol.</span></span>  
  
## <a name="validating-security"></a><span data-ttu-id="3dbac-125">验证安全性</span><span class="sxs-lookup"><span data-stu-id="3dbac-125">Validating Security</span></span>  

 <span data-ttu-id="3dbac-126">元数据源可以分为两大类：受信任的源和不受信任的源。</span><span class="sxs-lookup"><span data-stu-id="3dbac-126">Metadata sources can be divided into two broad categories: trust sources and untrusted sources.</span></span> <span data-ttu-id="3dbac-127">如果信任某个源，并且已从该源的安全 MEX 终结点下载客户端代码和其他元数据，则可以生成客户端，为其提供正确的凭据，然后无所顾忌地运行该客户端。</span><span class="sxs-lookup"><span data-stu-id="3dbac-127">If you trust a source and have downloaded the client code and other metadata from that source's secure MEX endpoint, then you can build the client, supply it with the right credentials, and run it with no other concerns.</span></span>  
  
 <span data-ttu-id="3dbac-128">但是，如果您选择从一个知之甚少的源下载客户端和元数据，请务必验证代码所使用的安全措施。</span><span class="sxs-lookup"><span data-stu-id="3dbac-128">However, if you elect to download a client and metadata from a source that you know little about, be sure to validate the security measures the code uses.</span></span> <span data-ttu-id="3dbac-129">例如，一定不要简单地创建一个向服务发送个人或财务信息的客户端，除非该服务要求保密性和完整性（这是最基本的要求）。</span><span class="sxs-lookup"><span data-stu-id="3dbac-129">For example, you must not simply create a client that sends your personal or financial information to a service unless the service demands confidentiality and integrity (at the very least).</span></span> <span data-ttu-id="3dbac-130">你应信任该服务的所有者，使其能够公开此类信息，因为这些信息将对这些信息可见。</span><span class="sxs-lookup"><span data-stu-id="3dbac-130">You should trust the owner of the service to the extent that you are willing to disclose such information, because such information will be visible to them.</span></span>  
  
 <span data-ttu-id="3dbac-131">因此，请记住如下规则：在使用来自不受信任的源的代码和元数据时，应检查这些代码和元数据，以确保它们满足你所要求的安全级别。</span><span class="sxs-lookup"><span data-stu-id="3dbac-131">As a rule, therefore, when using code and metadata from an untrusted source, check the code and metadata to ensure that it meets the security level that you require.</span></span>  
  
## <a name="setting-a-client-credential"></a><span data-ttu-id="3dbac-132">设置客户端凭据</span><span class="sxs-lookup"><span data-stu-id="3dbac-132">Setting a Client Credential</span></span>  

 <span data-ttu-id="3dbac-133">在客户端上设置客户端凭据的过程包含两个步骤：</span><span class="sxs-lookup"><span data-stu-id="3dbac-133">Setting a client credential on a client consists of two steps:</span></span>  
  
1. <span data-ttu-id="3dbac-134">确定服务所需的 *客户端凭据类型* 。</span><span class="sxs-lookup"><span data-stu-id="3dbac-134">Determine the *client credential type* the service requires.</span></span> <span data-ttu-id="3dbac-135">这是通过两种方法之一完成的。</span><span class="sxs-lookup"><span data-stu-id="3dbac-135">This is accomplished by one of two methods.</span></span> <span data-ttu-id="3dbac-136">首先，如果您拥有来自服务创建者的文档，则其中应指定了服务所要求的客户端凭据类型（如果有要求的话）。</span><span class="sxs-lookup"><span data-stu-id="3dbac-136">First, if you have documentation from the service creator, it should specify the client credential type (if any) the service requires.</span></span> <span data-ttu-id="3dbac-137">其次，如果您仅拥有由 Svcutil.exe 工具生成的配置文件，则可以检查各个绑定，以确定要求何种凭据类型。</span><span class="sxs-lookup"><span data-stu-id="3dbac-137">Second, if you have only a configuration file generated by the Svcutil.exe tool, you can examine the individual bindings to determine what credential type is required.</span></span>  
  
2. <span data-ttu-id="3dbac-138">指定一个实际客户端凭据。</span><span class="sxs-lookup"><span data-stu-id="3dbac-138">Specify an actual client credential.</span></span> <span data-ttu-id="3dbac-139">实际的客户端凭据称为 *客户端凭据值* ，以便将其与类型区分开来。</span><span class="sxs-lookup"><span data-stu-id="3dbac-139">The actual client credential is called a *client credential value* to distinguish it from the type.</span></span> <span data-ttu-id="3dbac-140">例如，如果客户端凭据类型指定了证书，您必须提供由该服务所信任的证书颁发机构颁发的 X.509 证书。</span><span class="sxs-lookup"><span data-stu-id="3dbac-140">For example, if the client credential type specifies a certificate, you must supply an X.509 certificate that is issued by a certification authority the service trusts.</span></span>  
  
### <a name="determining-the-client-credential-type"></a><span data-ttu-id="3dbac-141">确定客户端凭据类型</span><span class="sxs-lookup"><span data-stu-id="3dbac-141">Determining the Client Credential Type</span></span>  

 <span data-ttu-id="3dbac-142">如果已生成 Svcutil.exe 工具的配置文件，请检查 [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) 部分以确定所需的客户端凭据类型。</span><span class="sxs-lookup"><span data-stu-id="3dbac-142">If you have the configuration file the Svcutil.exe tool generated, examine the [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) section to determine what client credential type is required.</span></span> <span data-ttu-id="3dbac-143">该节包含指定安全需求的绑定元素。</span><span class="sxs-lookup"><span data-stu-id="3dbac-143">Within the section are binding elements that specify the security requirements.</span></span> <span data-ttu-id="3dbac-144">具体而言，检查 \<security> 每个绑定的元素。</span><span class="sxs-lookup"><span data-stu-id="3dbac-144">Specifically, examine the \<security> Element of each binding.</span></span> <span data-ttu-id="3dbac-145">该元素包含 `mode` 属性，该属性可设置为以下三个可能的值之一：`Message`、`Transport` 或 `TransportWithMessageCredential`。</span><span class="sxs-lookup"><span data-stu-id="3dbac-145">That element includes the `mode` attribute, which you can set to one of three possible values (`Message`, `Transport`, or `TransportWithMessageCredential`).</span></span> <span data-ttu-id="3dbac-146">该属性的值确定模式，而模式则确定哪个子元素有效。</span><span class="sxs-lookup"><span data-stu-id="3dbac-146">The value of the attribute determines the mode, and the mode determines which of the child elements is significant.</span></span>  
  
 <span data-ttu-id="3dbac-147">`<security>`元素可以包含 `<transport>` 或 `<message>` 元素，或同时包含两者。</span><span class="sxs-lookup"><span data-stu-id="3dbac-147">The `<security>` element can contain either a `<transport>` or `<message>` element, or both.</span></span> <span data-ttu-id="3dbac-148">有效元素是指与安全模式匹配的那个元素。</span><span class="sxs-lookup"><span data-stu-id="3dbac-148">The significant element is the one that matches the security mode.</span></span> <span data-ttu-id="3dbac-149">例如，下面的代码指定安全模式为 `"Message"`，`<message>` 元素的客户端凭据类型为 `"Certificate"`。</span><span class="sxs-lookup"><span data-stu-id="3dbac-149">For example, the following code specifies that the security mode is `"Message"`, and the client credential type for the `<message>` element is `"Certificate"`.</span></span> <span data-ttu-id="3dbac-150">在这种情况下，`<transport>` 元素可以忽略。</span><span class="sxs-lookup"><span data-stu-id="3dbac-150">In this case, the `<transport>` element can be ignored.</span></span> <span data-ttu-id="3dbac-151">但是，`<message>` 元素指定必须提供 X.509 证书。</span><span class="sxs-lookup"><span data-stu-id="3dbac-151">However, the `<message>` element specifies that an X.509 certificate must be supplied.</span></span>  

```xml  
<wsHttpBinding>  
    <binding name="WSHttpBinding_ICalculator">  
       <security mode="Message">  
           <transport clientCredentialType="Windows"
                      realm="" />  
           <message clientCredentialType="Certificate"
                    negotiateServiceCredential="true"  
                    algorithmSuite="Default"
                    establishSecurityContext="true" />  
       </security>  
    </binding>  
</wsHttpBinding>  
```  

 <span data-ttu-id="3dbac-152">请注意，如果按照下面的示例所示，将 `clientCredentialType` 属性设置为 `"Windows"`，则无需提供实际凭据值。</span><span class="sxs-lookup"><span data-stu-id="3dbac-152">Note that if the `clientCredentialType` attribute is set to `"Windows"`, as shown in the following example, you do not need to supply an actual credential value.</span></span> <span data-ttu-id="3dbac-153">这是因为，Windows 集成安全性提供了正在运行客户端的用户的实际凭据（一个 Kerberos 令牌）。</span><span class="sxs-lookup"><span data-stu-id="3dbac-153">This is because the Windows integrated security provides the actual credential (a Kerberos token) of the person who is running the client.</span></span>  
  
```xml  
<security mode="Message">  
    <transport clientCredentialType="Windows "
        realm="" />  
</security>  
```  
  
### <a name="setting-the-client-credential-value"></a><span data-ttu-id="3dbac-154">设置客户端凭据值</span><span class="sxs-lookup"><span data-stu-id="3dbac-154">Setting the Client Credential Value</span></span>  

 <span data-ttu-id="3dbac-155">如果确定客户端必须提供凭据，请使用适当的方法来配置客户端。</span><span class="sxs-lookup"><span data-stu-id="3dbac-155">If it is determined that the client must supply a credential, use the appropriate method to configure the client.</span></span> <span data-ttu-id="3dbac-156">例如，若要设置客户端证书，请使用 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="3dbac-156">For example, to set a client certificate, use the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> method.</span></span>  
  
 <span data-ttu-id="3dbac-157">一种常见的证书形式是 X.509 证书。</span><span class="sxs-lookup"><span data-stu-id="3dbac-157">A common form of credential is the X.509 certificate.</span></span> <span data-ttu-id="3dbac-158">可以通过两种方式来提供凭据：</span><span class="sxs-lookup"><span data-stu-id="3dbac-158">You can supply the credential in two ways:</span></span>  
  
- <span data-ttu-id="3dbac-159">在客户端代码中对其进行编程（使用 `SetCertificate` 方法）。</span><span class="sxs-lookup"><span data-stu-id="3dbac-159">By programming it in your client code (using the `SetCertificate` method).</span></span>  
  
 <span data-ttu-id="3dbac-160">通过添加 [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md) 客户端的配置文件的部分，并使用 `clientCredentials` 如下所示的元素 () 。</span><span class="sxs-lookup"><span data-stu-id="3dbac-160">By adding a [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md) section of the configuration file for the client and using the `clientCredentials` element (shown below).</span></span>  
  
#### <a name="setting-a-clientcredentials-value-in-code"></a><span data-ttu-id="3dbac-161">\<clientCredentials>在代码中设置值</span><span class="sxs-lookup"><span data-stu-id="3dbac-161">Setting a \<clientCredentials> Value in Code</span></span>  

 <span data-ttu-id="3dbac-162">若要 [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) 在代码中设置值，你必须访问 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> 类的属性 <xref:System.ServiceModel.ClientBase%601> 。</span><span class="sxs-lookup"><span data-stu-id="3dbac-162">To set a [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) value in code, you must access the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the <xref:System.ServiceModel.ClientBase%601> class.</span></span> <span data-ttu-id="3dbac-163">该属性返回一个 <xref:System.ServiceModel.Description.ClientCredentials> 对象，使用该对象可以访问各种凭据类型，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="3dbac-163">The property returns a <xref:System.ServiceModel.Description.ClientCredentials> object that allows access to various credential types, as shown in the following table.</span></span>  
  
|<span data-ttu-id="3dbac-164">ClientCredential 属性</span><span class="sxs-lookup"><span data-stu-id="3dbac-164">ClientCredential Property</span></span>|<span data-ttu-id="3dbac-165">说明</span><span class="sxs-lookup"><span data-stu-id="3dbac-165">Description</span></span>|<span data-ttu-id="3dbac-166">说明</span><span class="sxs-lookup"><span data-stu-id="3dbac-166">Notes</span></span>|  
|-------------------------------|-----------------|-----------|  
|<xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A>|<span data-ttu-id="3dbac-167">返回一个 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential></span><span class="sxs-lookup"><span data-stu-id="3dbac-167">Returns an <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential></span></span>|<span data-ttu-id="3dbac-168">表示客户端提供的 X.509 证书，客户端使用该证书向服务器证明自己的身份。</span><span class="sxs-lookup"><span data-stu-id="3dbac-168">Represents an X.509 certificate provided by the client to authenticate itself to the service.</span></span>|  
|<xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>|<span data-ttu-id="3dbac-169">返回一个 <xref:System.ServiceModel.Security.HttpDigestClientCredential></span><span class="sxs-lookup"><span data-stu-id="3dbac-169">Returns an <xref:System.ServiceModel.Security.HttpDigestClientCredential></span></span>|<span data-ttu-id="3dbac-170">表示 HTTP 摘要式凭据。</span><span class="sxs-lookup"><span data-stu-id="3dbac-170">Represents an HTTP digest credential.</span></span> <span data-ttu-id="3dbac-171">该凭据是用户名和密码的哈希。</span><span class="sxs-lookup"><span data-stu-id="3dbac-171">The credential is a hash of the user name and password.</span></span>|  
|<xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>|<span data-ttu-id="3dbac-172">返回一个 <xref:System.ServiceModel.Security.IssuedTokenClientCredential></span><span class="sxs-lookup"><span data-stu-id="3dbac-172">Returns an <xref:System.ServiceModel.Security.IssuedTokenClientCredential></span></span>|<span data-ttu-id="3dbac-173">表示由安全令牌服务颁发的一个自定义安全令牌，通常用在联合方案中。</span><span class="sxs-lookup"><span data-stu-id="3dbac-173">Represents a custom security token issued by a Security Token Service, commonly used in federation scenarios.</span></span>|  
|<xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>|<span data-ttu-id="3dbac-174">返回一个 <xref:System.ServiceModel.Security.PeerCredential></span><span class="sxs-lookup"><span data-stu-id="3dbac-174">Returns a <xref:System.ServiceModel.Security.PeerCredential></span></span>|<span data-ttu-id="3dbac-175">表示一个用于参与 Windows 域上的对等网格的对等凭据。</span><span class="sxs-lookup"><span data-stu-id="3dbac-175">Represents a Peer credential for participation in a Peer mesh on a Windows domain.</span></span>|  
|<xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>|<span data-ttu-id="3dbac-176">返回一个 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential></span><span class="sxs-lookup"><span data-stu-id="3dbac-176">Returns an <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential></span></span>|<span data-ttu-id="3dbac-177">表示服务在带外协商中提供的 X.509 证书。</span><span class="sxs-lookup"><span data-stu-id="3dbac-177">Represents an X.509 certificate provided by the service in an out-of-band negotiation.</span></span>|  
|<xref:System.ServiceModel.Description.ClientCredentials.UserName%2A>|<span data-ttu-id="3dbac-178">返回一个 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential></span><span class="sxs-lookup"><span data-stu-id="3dbac-178">Returns a <xref:System.ServiceModel.Security.UserNamePasswordClientCredential></span></span>|<span data-ttu-id="3dbac-179">表示一个用户名和密码对。</span><span class="sxs-lookup"><span data-stu-id="3dbac-179">Represents a user name and password pair.</span></span>|  
|<xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>|<span data-ttu-id="3dbac-180">返回一个 <xref:System.ServiceModel.Security.WindowsClientCredential></span><span class="sxs-lookup"><span data-stu-id="3dbac-180">Returns a <xref:System.ServiceModel.Security.WindowsClientCredential></span></span>|<span data-ttu-id="3dbac-181">表示 Windows 客户端凭据（Kerberos 凭据）。</span><span class="sxs-lookup"><span data-stu-id="3dbac-181">Represents a Windows client credential (a Kerberos credential).</span></span> <span data-ttu-id="3dbac-182">该类的属性是只读的。</span><span class="sxs-lookup"><span data-stu-id="3dbac-182">The properties of the class are read-only.</span></span>|  
  
#### <a name="setting-a-clientcredentials-value-in-configuration"></a><span data-ttu-id="3dbac-183">\<clientCredentials>在配置中设置值</span><span class="sxs-lookup"><span data-stu-id="3dbac-183">Setting a \<clientCredentials> Value in Configuration</span></span>  

 <span data-ttu-id="3dbac-184">通过使用终结点行为作为元素的子元素来指定凭据值 [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) 。</span><span class="sxs-lookup"><span data-stu-id="3dbac-184">Credential values are specified by using an endpoint behavior as child elements of the [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) element.</span></span> <span data-ttu-id="3dbac-185">所使用的元素取决于客户端凭据类型。</span><span class="sxs-lookup"><span data-stu-id="3dbac-185">The element used depends on the client credential type.</span></span> <span data-ttu-id="3dbac-186">例如，下面的示例演示使用 <设置 x.509 证书的配置 [\<clientCertificate>](../configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md) 。</span><span class="sxs-lookup"><span data-stu-id="3dbac-186">For example, the following example shows the configuration to set an X.509 certificate using the <[\<clientCertificate>](../configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>
        <behavior name="myEndpointBehavior">  
          <clientCredentials>  
            <clientCertificate findvalue="myMachineName"
            storeLocation="Current" X509FindType="FindBySubjectName" />  
          </clientCredentials>  
        </behavior>
      </endpointBehaviors>
    </behaviors>
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="3dbac-187">若要在配置中设置客户端凭据，请将 [\<endpointBehaviors>](../configure-apps/file-schema/wcf/endpointbehaviors.md) 元素添加到配置文件中。</span><span class="sxs-lookup"><span data-stu-id="3dbac-187">To set the client credential in configuration, add an [\<endpointBehaviors>](../configure-apps/file-schema/wcf/endpointbehaviors.md) element to the configuration file.</span></span> <span data-ttu-id="3dbac-188">此外，必须使用元素的的 `behaviorConfiguration` 属性[ \<endpoint> \<client> ](../configure-apps/file-schema/wcf/endpoint-of-client.md)将添加的行为元素链接到服务的终结点，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="3dbac-188">Additionally, the added behavior element must be linked to the service's endpoint using the `behaviorConfiguration` attribute of the [\<endpoint> of \<client>](../configure-apps/file-schema/wcf/endpoint-of-client.md) element as shown in the following example.</span></span> <span data-ttu-id="3dbac-189">`behaviorConfiguration` 属性的值必须与行为 `name` 属性的值相匹配。</span><span class="sxs-lookup"><span data-stu-id="3dbac-189">The value of the `behaviorConfiguration` attribute must match the value of the behavior `name` attribute.</span></span>  

```xml
<configuration>
  <system.serviceModel>
    <client>
      <endpoint address="http://localhost/servicemodelsamples/service.svc"
                binding="wsHttpBinding"
                bindingConfiguration="Binding1"
                behaviorConfiguration="myEndpointBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </client>
  </system.serviceModel>
</configuration>
```
  
> [!NOTE]
> <span data-ttu-id="3dbac-190">有些客户端凭据值无法使用应用程序配置文件来设置，例如，用户名和密码值或 Windows 用户和密码值。</span><span class="sxs-lookup"><span data-stu-id="3dbac-190">Some of the client credential values cannot be set using application configuration files, for example, user name and password, or Windows user and password values.</span></span> <span data-ttu-id="3dbac-191">这种凭据值只能在代码中指定。</span><span class="sxs-lookup"><span data-stu-id="3dbac-191">Such credential values can be specified only in code.</span></span>  
  
 <span data-ttu-id="3dbac-192">有关设置客户端凭据的详细信息，请参阅 [如何：指定客户端凭据值](how-to-specify-client-credential-values.md)。</span><span class="sxs-lookup"><span data-stu-id="3dbac-192">For more information about setting the client credential, see [How to: Specify Client Credential Values](how-to-specify-client-credential-values.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3dbac-193">当 `ClientCredentialType` 设置为 `SecurityMode` 时，`"TransportWithMessageCredential",` 将被忽略，如下面的示例配置所示。</span><span class="sxs-lookup"><span data-stu-id="3dbac-193">`ClientCredentialType` is ignored when `SecurityMode` is set to `"TransportWithMessageCredential",` as shown in the following sample configuration.</span></span>  
  
```xml  
<wsHttpBinding>  
    <binding name="PingBinding">  
        <security mode="TransportWithMessageCredential"  >  
           <message  clientCredentialType="UserName"
               establishSecurityContext="false"
               negotiateServiceCredential="false" />  
           <transport clientCredentialType="Certificate"  />  
         </security>  
    </binding>  
</wsHttpBinding>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3dbac-194">请参阅</span><span class="sxs-lookup"><span data-stu-id="3dbac-194">See also</span></span>

- <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>
- <xref:System.ServiceModel.ClientBase%601>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>
- [\<bindings>](../configure-apps/file-schema/wcf/bindings.md)
- [<span data-ttu-id="3dbac-195">配置编辑器工具 (SvcConfigEditor.exe)</span><span class="sxs-lookup"><span data-stu-id="3dbac-195">Configuration Editor Tool (SvcConfigEditor.exe)</span></span>](configuration-editor-tool-svcconfigeditor-exe.md)
- [<span data-ttu-id="3dbac-196">保证服务的安全</span><span class="sxs-lookup"><span data-stu-id="3dbac-196">Securing Services</span></span>](securing-services.md)
- [<span data-ttu-id="3dbac-197">使用 WCF 客户端访问服务</span><span class="sxs-lookup"><span data-stu-id="3dbac-197">Accessing Services Using a WCF Client</span></span>](accessing-services-using-a-wcf-client.md)
- [<span data-ttu-id="3dbac-198">如何：指定客户端凭据值</span><span class="sxs-lookup"><span data-stu-id="3dbac-198">How to: Specify Client Credential Values</span></span>](how-to-specify-client-credential-values.md)
- [<span data-ttu-id="3dbac-199">ServiceModel 元数据实用工具 (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="3dbac-199">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="3dbac-200">如何：指定客户端凭据类型</span><span class="sxs-lookup"><span data-stu-id="3dbac-200">How to: Specify the Client Credential Type</span></span>](how-to-specify-the-client-credential-type.md)
