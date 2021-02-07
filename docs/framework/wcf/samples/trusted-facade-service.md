---
description: 了解详细信息：受信任的外观服务
title: 受信任的外观服务
ms.date: 03/30/2017
ms.assetid: c34d1a8f-e45e-440b-a201-d143abdbac38
ms.openlocfilehash: aebfa89c47d5e8ea37e210b2d7b19afbe204a1a1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99685473"
---
# <a name="trusted-facade-service"></a><span data-ttu-id="28e47-103">受信任的外观服务</span><span class="sxs-lookup"><span data-stu-id="28e47-103">Trusted Facade Service</span></span>

<span data-ttu-id="28e47-104">本方案示例演示如何使用 Windows Communication Foundation (WCF) 安全基础结构将调用方的标识信息从一个服务流到另一个服务。</span><span class="sxs-lookup"><span data-stu-id="28e47-104">This scenario sample demonstrates how to flow caller's identity information from one service to another using Windows Communication Foundation (WCF) security infrastructure.</span></span>  
  
 <span data-ttu-id="28e47-105">使用外观服务向公共网络公开由服务提供的功能是一种常见设计模式。</span><span class="sxs-lookup"><span data-stu-id="28e47-105">It is a common design pattern to expose the functionality provided by a service to the public network using a façade service.</span></span> <span data-ttu-id="28e47-106">外观服务通常驻留在周边网络（也称为 DMZ、外围安全区域和被筛选的子网）中，可与实现业务逻辑的后端服务通信和访问内部数据。</span><span class="sxs-lookup"><span data-stu-id="28e47-106">The façade service typically resides in the perimeter network (also known as DMZ, demilitarized zone, and screened subnet) and communicates with a backend service that implements the business logic and has access to internal data.</span></span> <span data-ttu-id="28e47-107">外观服务和后端服务之间的通信通道通过防火墙并通常仅限用于单一目的。</span><span class="sxs-lookup"><span data-stu-id="28e47-107">The communication channel between the façade service and the backend service goes through a firewall and is usually limited for a single purpose only.</span></span>  
  
 <span data-ttu-id="28e47-108">本示例包含以下组件：</span><span class="sxs-lookup"><span data-stu-id="28e47-108">This sample consists of the following components:</span></span>  
  
- <span data-ttu-id="28e47-109">计算器客户端</span><span class="sxs-lookup"><span data-stu-id="28e47-109">Calculator client</span></span>  
  
- <span data-ttu-id="28e47-110">计算器外观服务</span><span class="sxs-lookup"><span data-stu-id="28e47-110">Calculator façade service</span></span>  
  
- <span data-ttu-id="28e47-111">计算器后端服务</span><span class="sxs-lookup"><span data-stu-id="28e47-111">Calculator backend service</span></span>  
  
 <span data-ttu-id="28e47-112">外观服务负责验证请求和对调用方进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="28e47-112">The façade service is responsible for validating the request and authenticating the caller.</span></span> <span data-ttu-id="28e47-113">成功进行身份验证和验证后，服务将使用从周边网络到内部网络的受控通信通道将请求转发到后端服务。</span><span class="sxs-lookup"><span data-stu-id="28e47-113">After successful authentication and validation, it forwards the request to the backend service using the controlled communication channel from the perimeter network to the internal network.</span></span> <span data-ttu-id="28e47-114">作为所转发请求的一部分，外观服务包含有关调用方标识的信息，这样后端服务可以在其处理过程中使用此信息。</span><span class="sxs-lookup"><span data-stu-id="28e47-114">As a part of the forwarded request, the façade service includes information about the caller's identity so that the backend service can use this information in its processing.</span></span> <span data-ttu-id="28e47-115">使用消息 `Username` 标头内部的 `Security` 安全令牌传输调用方标识。</span><span class="sxs-lookup"><span data-stu-id="28e47-115">The caller's identity is transmitted using a `Username` security token inside the message `Security` header.</span></span> <span data-ttu-id="28e47-116">该示例使用 WCF 安全基础结构从标头传输和提取此信息 `Security` 。</span><span class="sxs-lookup"><span data-stu-id="28e47-116">The sample uses the WCF security infrastructure to transmit and extract this information from the `Security` header.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="28e47-117">后端服务委托外观服务对调用方进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="28e47-117">The backend service trusts the façade service to authenticate the caller.</span></span> <span data-ttu-id="28e47-118">因此，后端服务不再对调用方进行身份验证；它使用外观服务在转发的请求中提供的标识信息。</span><span class="sxs-lookup"><span data-stu-id="28e47-118">Because of this, the backend service does not authenticate the caller again; it uses the identity information provided by the façade service in the forwarded request.</span></span> <span data-ttu-id="28e47-119">由于此信任关系，后端服务必须对外观服务进行身份验证，以确保转发的消息来自受信任的源（在本例中为外观服务）。</span><span class="sxs-lookup"><span data-stu-id="28e47-119">Because of this trust relationship, the backend service must authenticate the façade service to ensure that the forwarded message comes from a trusted source - in this case, the façade service.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="28e47-120">实现</span><span class="sxs-lookup"><span data-stu-id="28e47-120">Implementation</span></span>  

 <span data-ttu-id="28e47-121">本示例中有两个通信路径：</span><span class="sxs-lookup"><span data-stu-id="28e47-121">There are two communication paths in this sample.</span></span> <span data-ttu-id="28e47-122">第一个路径是在客户端和外观服务之间，第二个路径是在外观服务和后端服务之间。</span><span class="sxs-lookup"><span data-stu-id="28e47-122">First is between the client and the façade service, the second is between the façade service and the backend service.</span></span>  
  
### <a name="communication-path-between-client-and-faade-service"></a><span data-ttu-id="28e47-123">客户端和外观服务之间的通信路径</span><span class="sxs-lookup"><span data-stu-id="28e47-123">Communication Path between Client and Façade Service</span></span>  

 <span data-ttu-id="28e47-124">客户端到外观服务这一通信路径使用具有 `wsHttpBinding` 客户端凭据类型的 `UserName` 。</span><span class="sxs-lookup"><span data-stu-id="28e47-124">The client to the façade service communication path uses `wsHttpBinding` with a `UserName` client credential type.</span></span> <span data-ttu-id="28e47-125">这意味着客户端使用用户名和密码对外观服务进行身份验证，而外观服务使用 X.509 证书对客户端进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="28e47-125">This means that the client uses username and password to authenticate to the façade service and the façade service uses X.509 certificate to authenticate to the client.</span></span> <span data-ttu-id="28e47-126">绑定配置如下例所示：</span><span class="sxs-lookup"><span data-stu-id="28e47-126">The binding configuration looks like the following example.</span></span>  
  
```xml  
<bindings>  
  <wsHttpBinding>  
    <binding name="Binding1">  
      <security mode="Message">  
        <message clientCredentialType="UserName"/>  
      </security>  
    </binding>  
  </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="28e47-127">外观服务使用自定义 `UserNamePasswordValidator` 实现对调用方进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="28e47-127">The façade service authenticates the caller using custom `UserNamePasswordValidator` implementation.</span></span> <span data-ttu-id="28e47-128">出于演示目的，该身份验证只确保调用方的用户名与所提供的密码相匹配。</span><span class="sxs-lookup"><span data-stu-id="28e47-128">For demonstration purposes, the authentication only ensures that the caller's username matches the presented password.</span></span> <span data-ttu-id="28e47-129">在现实情况中，可能会使用 Active Directory 或自定义 ASP.NET 成员资格提供程序对用户进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="28e47-129">In the real world situation, the user is probably authenticated using Active Directory or custom ASP.NET Membership provider.</span></span> <span data-ttu-id="28e47-130">验证程序实现位于 `FacadeService.cs` 文件中。</span><span class="sxs-lookup"><span data-stu-id="28e47-130">The validator implementation resides in `FacadeService.cs` file.</span></span>  
  
```csharp  
public class MyUserNamePasswordValidator : UserNamePasswordValidator  
{  
    public override void Validate(string userName, string password)  
    {  
        // check that username matches password  
        if (null == userName || userName != password)  
        {  
            Console.WriteLine("Invalid username or password");  
            throw new SecurityTokenValidationException(  
                       "Invalid username or password");  
        }  
    }  
}  
```  
  
 <span data-ttu-id="28e47-131">自定义验证程序配置为在外观服务配置文件的 `serviceCredentials` 行为内部使用。</span><span class="sxs-lookup"><span data-stu-id="28e47-131">The custom validator is configured to be used inside the `serviceCredentials` behavior in the façade service configuration file.</span></span> <span data-ttu-id="28e47-132">此行为还可用于配置服务的 X.509 证书。</span><span class="sxs-lookup"><span data-stu-id="28e47-132">This behavior is also used to configure the service's X.509 certificate.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="FacadeServiceBehavior">  
      <!--The serviceCredentials behavior allows you to define -->  
      <!--a service certificate. -->  
      <!--A service certificate is used by the service to  -->  
      <!--authenticate itself to its clients and to provide  -->  
      <!--message protection. -->  
      <!--This configuration references the "localhost"  -->  
      <!--certificate installed during the setup instructions. -->  
      <serviceCredentials>  
        <serviceCertificate
               findValue="localhost"
               storeLocation="LocalMachine"
               storeName="My"
               x509FindType="FindBySubjectName" />  
        <userNameAuthentication userNamePasswordValidationMode="Custom"  
            customUserNamePasswordValidatorType=  
           "Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator,  
            FacadeService"/>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
### <a name="communication-path-between-faade-service-and-backend-service"></a><span data-ttu-id="28e47-133">外观服务和后端服务之间的通信路径</span><span class="sxs-lookup"><span data-stu-id="28e47-133">Communication Path between Façade Service and Backend Service</span></span>  

 <span data-ttu-id="28e47-134">外观服务到后端服务这一通信路径使用包含多个绑定元素的 `customBinding` 。</span><span class="sxs-lookup"><span data-stu-id="28e47-134">The façade service to the backend service communication path uses a `customBinding` that consists of several binding elements.</span></span> <span data-ttu-id="28e47-135">此绑定可实现两个目的。</span><span class="sxs-lookup"><span data-stu-id="28e47-135">This binding accomplishes two things.</span></span> <span data-ttu-id="28e47-136">它对外观服务和后端服务进行身份验证，以确保通信的安全并确保通信来自受信任的源。</span><span class="sxs-lookup"><span data-stu-id="28e47-136">It authenticates the façade service and backend service to ensure that the communication is secure and is coming from a trusted source.</span></span> <span data-ttu-id="28e47-137">另外，它还可在 `Username` 安全令牌中传输初始调用方的标识。</span><span class="sxs-lookup"><span data-stu-id="28e47-137">Additionally, it also transmits the initial caller's identity inside the `Username` security token.</span></span> <span data-ttu-id="28e47-138">在这种情况下，只将初始调用方的用户名传输到后端服务，密码不包括在消息中。</span><span class="sxs-lookup"><span data-stu-id="28e47-138">In this case, only the initial caller's username is transmitted to the backend service, the password is not included in the message.</span></span> <span data-ttu-id="28e47-139">这是因为在将请求转发给调用方之前，后端服务会委托外观服务对调用方进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="28e47-139">This is because the backend service trusts the façade service to authenticate the caller before forwarding the request to it.</span></span> <span data-ttu-id="28e47-140">由于外观服务会向后端服务对其自身进行身份验证，因此后端服务可以信任所转发请求中包含的信息。</span><span class="sxs-lookup"><span data-stu-id="28e47-140">Because the façade service authenticates itself to the backend service, the backend service can trust the information contained in the forwarded request.</span></span>  
  
 <span data-ttu-id="28e47-141">下面是此通信路径的绑定配置。</span><span class="sxs-lookup"><span data-stu-id="28e47-141">The following is the binding configuration for this communication path.</span></span>  
  
```xml  
<bindings>  
  <customBinding>  
    <binding name="ClientBinding">  
      <security authenticationMode="UserNameOverTransport"/>  
      <windowsStreamSecurity/>  
      <tcpTransport/>  
    </binding>  
  </customBinding>  
</bindings>  
```  
  
 <span data-ttu-id="28e47-142">[\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md)绑定元素负责发送和提取初始调用方的用户名。</span><span class="sxs-lookup"><span data-stu-id="28e47-142">The [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) binding element takes care of the initial caller's username transmission and extraction.</span></span> <span data-ttu-id="28e47-143">[\<windowsStreamSecurity>](../../configure-apps/file-schema/wcf/windowsstreamsecurity.md)和 [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) 负责对外观和后端服务和消息保护进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="28e47-143">The [\<windowsStreamSecurity>](../../configure-apps/file-schema/wcf/windowsstreamsecurity.md) and [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) take care of authenticating façade and backend services and message protection.</span></span>  
  
 <span data-ttu-id="28e47-144">若要转发请求，外观服务实现必须提供初始调用方的用户名，以便 WCF 安全基础结构能够将其放入转发的消息中。</span><span class="sxs-lookup"><span data-stu-id="28e47-144">To forward the request, the façade service implementation must provide the initial caller's username so that WCF security infrastructure can place this into the forwarded message.</span></span> <span data-ttu-id="28e47-145">初始调用方的用户名是在外观服务实现中提供的，具体方式为在外观服务用于与后端服务进行通信的客户端代理实例的 `ClientCredentials` 属性中设置该用户名。</span><span class="sxs-lookup"><span data-stu-id="28e47-145">The initial caller's username is provided in the façade service implementation by setting it in the `ClientCredentials` property on the client proxy instance that façade service uses to communicate with the backend service.</span></span>  
  
 <span data-ttu-id="28e47-146">下面的代码演示如何在外观服务上实现 `GetCallerIdentity` 方法。</span><span class="sxs-lookup"><span data-stu-id="28e47-146">The following code shows how `GetCallerIdentity` method is implemented on the façade service.</span></span> <span data-ttu-id="28e47-147">其他方法使用相同的模式。</span><span class="sxs-lookup"><span data-stu-id="28e47-147">Other methods use the same pattern.</span></span>  
  
```csharp  
public string GetCallerIdentity()  
{  
    CalculatorClient client = new CalculatorClient();  
    client.ClientCredentials.UserName.UserName = ServiceSecurityContext.Current.PrimaryIdentity.Name;  
    string result = client.GetCallerIdentity();  
    client.Close();  
    return result;  
}  
```  
  
 <span data-ttu-id="28e47-148">如前面的代码中所示，未针对 `ClientCredentials` 属性设置密码，只设置用户名。</span><span class="sxs-lookup"><span data-stu-id="28e47-148">As shown in the previous code, the password is not set on the `ClientCredentials` property, only the username is set.</span></span> <span data-ttu-id="28e47-149">在这种情况下，WCF 安全基础结构创建不含密码的用户名安全令牌，这正是这种情况下所要求的。</span><span class="sxs-lookup"><span data-stu-id="28e47-149">WCF security infrastructure creates a username security token without a password in this case, which is exactly what is required in this scenario.</span></span>  
  
 <span data-ttu-id="28e47-150">在后端服务上，必须对用户名安全令牌中包含的信息进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="28e47-150">On the backend service, the information contained in the username security token must be authenticated.</span></span> <span data-ttu-id="28e47-151">默认情况下，WCF 安全尝试使用提供的密码将用户映射到 Windows 帐户。</span><span class="sxs-lookup"><span data-stu-id="28e47-151">By default, WCF security attempts to map the user to a Windows account using the provided password.</span></span> <span data-ttu-id="28e47-152">在这种情况下，不提供密码且不需要后端服务对用户名进行身份验证，因为外观服务已经执行了身份验证。</span><span class="sxs-lookup"><span data-stu-id="28e47-152">In this case, there is no password provided and the backend service is not required to authenticate the username because the authentication was already performed by the façade service.</span></span> <span data-ttu-id="28e47-153">若要在 WCF 中实现此功能，提供了一个自定义， `UserNamePasswordValidator` 它只强制在令牌中指定用户名，不执行任何其他身份验证。</span><span class="sxs-lookup"><span data-stu-id="28e47-153">To implement this functionality in WCF, a custom `UserNamePasswordValidator` is provided that only enforces that a username is specified in the token and does not perform any additional authentication.</span></span>  
  
```csharp  
public class MyUserNamePasswordValidator : UserNamePasswordValidator  
{  
    public override void Validate(string userName, string password)  
    {  
        // Ignore the password because it is empty,
        // we trust the facade service to authenticate the client.  
        // Accept the username information here so that the
        // application gets access to it.  
        if (null == userName)  
        {  
            Console.WriteLine("Invalid username");  
            throw new
             SecurityTokenValidationException("Invalid username");  
        }  
    }  
}  
```  
  
 <span data-ttu-id="28e47-154">自定义验证程序配置为在外观服务配置文件的 `serviceCredentials` 行为内部使用。</span><span class="sxs-lookup"><span data-stu-id="28e47-154">The custom validator is configured to be used inside the `serviceCredentials` behavior in the façade service configuration file.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="BackendServiceBehavior">  
      <serviceCredentials>  
        <userNameAuthentication userNamePasswordValidationMode="Custom"  
           customUserNamePasswordValidatorType=  
          "Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator,
           BackendService"/>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="28e47-155">为提取用户名信息和有关受信任外观服务帐户的信息，后端服务实现使用 `ServiceSecurityContext` 类。</span><span class="sxs-lookup"><span data-stu-id="28e47-155">To extract the username information and information about the trusted façade service account, the backend service implementation uses the `ServiceSecurityContext` class.</span></span> <span data-ttu-id="28e47-156">下面的代码演示如何实现 `GetCallerIdentity` 方法。</span><span class="sxs-lookup"><span data-stu-id="28e47-156">The following code shows how the `GetCallerIdentity` method is implemented.</span></span>  
  
```csharp  
public string GetCallerIdentity()  
{  
    // Facade service is authenticated using Windows authentication.  
    //Its identity is accessible.  
    // On ServiceSecurityContext.Current.WindowsIdentity.  
    string facadeServiceIdentityName =
          ServiceSecurityContext.Current.WindowsIdentity.Name;  
  
    // The client name is transmitted using Username authentication on
    //the message level without the password  
    // using a supporting encrypted UserNameToken.  
    // Claims extracted from this supporting token are available in
    // ServiceSecurityContext.Current.AuthorizationContext.ClaimSets
    // collection.  
    string clientName = null;  
    foreach (ClaimSet claimSet in
        ServiceSecurityContext.Current.AuthorizationContext.ClaimSets)  
    {  
        foreach (Claim claim in claimSet)  
        {  
            if (claim.ClaimType == ClaimTypes.Name &&
                                   claim.Right == Rights.Identity)  
            {  
                clientName = (string)claim.Resource;  
                break;  
            }  
        }  
    }  
    if (clientName == null)  
    {  
        // In case there was no UserNameToken attached to the request.  
        // In the real world implementation the service should reject
        // this request.  
        return "Anonymous caller via " + facadeServiceIdentityName;  
    }  
  
    return clientName + " via " + facadeServiceIdentityName;  
}  
```  
  
 <span data-ttu-id="28e47-157">使用 `ServiceSecurityContext.Current.WindowsIdentity` 属性提取外观服务帐户信息。</span><span class="sxs-lookup"><span data-stu-id="28e47-157">The façade service account information is extracted using the `ServiceSecurityContext.Current.WindowsIdentity` property.</span></span> <span data-ttu-id="28e47-158">为访问有关初始调用方的信息，后端服务使用 `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` 属性。</span><span class="sxs-lookup"><span data-stu-id="28e47-158">To access the information about the initial caller the backend service uses the `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` property.</span></span> <span data-ttu-id="28e47-159">该属性查找类型为 `Identity` 的 `Name`声明。</span><span class="sxs-lookup"><span data-stu-id="28e47-159">It looks for an `Identity` claim with a type `Name`.</span></span> <span data-ttu-id="28e47-160">此声明是由 WCF 安全基础结构根据安全令牌中包含的信息自动生成的 `Username` 。</span><span class="sxs-lookup"><span data-stu-id="28e47-160">This claim is automatically generated by WCF security infrastructure from the information contained in the `Username` security token.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="28e47-161">运行示例</span><span class="sxs-lookup"><span data-stu-id="28e47-161">Running the sample</span></span>  

 <span data-ttu-id="28e47-162">运行示例时，操作请求和响应将显示在客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="28e47-162">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="28e47-163">在客户端窗口中按 Enter 可以关闭客户端。</span><span class="sxs-lookup"><span data-stu-id="28e47-163">Press ENTER in the client window to shut down the client.</span></span> <span data-ttu-id="28e47-164">在外观服务和后端服务控制台窗口中按 Enter 可以关闭服务。</span><span class="sxs-lookup"><span data-stu-id="28e47-164">You can press ENTER in the façade and backend service console windows to shut down the services.</span></span>  
  
```console  
Username authentication required.  
Provide a valid machine or domain ac  
   Enter username:  
user  
   Enter password:  
****  
user via MyMachine\testaccount  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="28e47-165">使用“受信任外观”方案示例中包括的 Setup.bat 批处理文件可以用相关证书配置服务器，以便运行需要基于证书的安全向客户端对其自身进行身份验证的外观服务。</span><span class="sxs-lookup"><span data-stu-id="28e47-165">The Setup.bat batch file included with the Trusted Facade scenario sample enables you to configure the server with a relevant certificate to run the façade service that requires certificate-based security to authenticate itself to the client.</span></span> <span data-ttu-id="28e47-166">有关详细信息，请参见本主题末尾的设置过程。</span><span class="sxs-lookup"><span data-stu-id="28e47-166">See the setup procedure at the end of this topic for details.</span></span>  
  
 <span data-ttu-id="28e47-167">下面提供该批处理文件不同部分的简要概述。</span><span class="sxs-lookup"><span data-stu-id="28e47-167">The following provides a brief overview of the different sections of the batch files.</span></span>  
  
- <span data-ttu-id="28e47-168">创建服务器证书。</span><span class="sxs-lookup"><span data-stu-id="28e47-168">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="28e47-169">Setup.bat 批处理文件中的以下行创建将要使用的服务器证书。</span><span class="sxs-lookup"><span data-stu-id="28e47-169">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```console  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="28e47-170">`%SERVER_NAME%` 变量指定服务器名，默认值为 localhost。</span><span class="sxs-lookup"><span data-stu-id="28e47-170">The `%SERVER_NAME%` variable specifies the server name - the default value is localhost.</span></span> <span data-ttu-id="28e47-171">该证书存储在 LocalMachine 存储区中。</span><span class="sxs-lookup"><span data-stu-id="28e47-171">The certificate is stored in the LocalMachine store.</span></span>  
  
- <span data-ttu-id="28e47-172">将外观服务的证书安装到客户端的受信任证书存储区中。</span><span class="sxs-lookup"><span data-stu-id="28e47-172">Installing the façade service's certificate into the client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="28e47-173">下面的行将外观服务的证书复制到客户端的受信任人存储中。</span><span class="sxs-lookup"><span data-stu-id="28e47-173">The following line copies the façade service's certificate into the client trusted people store.</span></span> <span data-ttu-id="28e47-174">因为客户端系统不隐式信任 Makecert.exe 生成的证书，所以需要执行此步骤。</span><span class="sxs-lookup"><span data-stu-id="28e47-174">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="28e47-175">如果已经拥有一个证书，该证书来源于客户端的受信任根证书（例如由 Microsoft 颁发的证书），则不需要执行使用服务器证书填充客户端证书存储区这一步骤。</span><span class="sxs-lookup"><span data-stu-id="28e47-175">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```console  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="28e47-176">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="28e47-176">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="28e47-177">确保已对 [Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="28e47-177">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="28e47-178">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="28e47-178">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="28e47-179">在同一计算机上运行示例</span><span class="sxs-lookup"><span data-stu-id="28e47-179">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="28e47-180">确保路径包含 Makecert.exe 所在的文件夹。</span><span class="sxs-lookup"><span data-stu-id="28e47-180">Ensure that the path includes the folder where Makecert.exe is located.</span></span>  
  
2. <span data-ttu-id="28e47-181">运行示例安装文件夹中的 Setup.bat。</span><span class="sxs-lookup"><span data-stu-id="28e47-181">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="28e47-182">这将安装运行示例所需的所有证书。</span><span class="sxs-lookup"><span data-stu-id="28e47-182">This installs all the certificates required for running the sample.</span></span>  
  
3. <span data-ttu-id="28e47-183">在单独的控制台窗口中启动 \BackendService\bin 目录中的 BackendService.exe</span><span class="sxs-lookup"><span data-stu-id="28e47-183">Launch the BackendService.exe from \BackendService\bin directory in a separate console window</span></span>  
  
4. <span data-ttu-id="28e47-184">在单独的控制台窗口中启动 \FacadeService\bin 目录中的 FacadeService.exe</span><span class="sxs-lookup"><span data-stu-id="28e47-184">Launch the FacadeService.exe from \FacadeService\bin directory in a separate console window</span></span>  
  
5. <span data-ttu-id="28e47-185">启动 \client\bin 中的 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="28e47-185">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="28e47-186">客户端活动将显示在客户端控制台应用程序上。</span><span class="sxs-lookup"><span data-stu-id="28e47-186">Client activity is displayed on the client console application.</span></span>  
  
6. <span data-ttu-id="28e47-187">如果客户端和服务无法进行通信，请参阅 [WCF 示例的故障排除提示](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="28e47-187">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="28e47-188">运行示例后进行清理</span><span class="sxs-lookup"><span data-stu-id="28e47-188">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="28e47-189">运行完示例后运行示例文件夹中的 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="28e47-189">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="28e47-190">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="28e47-190">The samples may already be installed on your machine.</span></span> <span data-ttu-id="28e47-191">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="28e47-191">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="28e47-192">如果此目录不存在，请参阅[Windows Communication Foundation (wcf) ，并 Windows Workflow Foundation (的 WF](https://www.microsoft.com/download/details.aspx?id=21459)) .NET Framework Windows Communication Foundation ([!INCLUDE[wf1](../../../../includes/wf1-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28e47-192">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="28e47-193">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="28e47-193">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\TrustedFacade`
