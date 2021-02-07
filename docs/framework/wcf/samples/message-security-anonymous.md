---
description: 了解详细信息：匿名消息安全
title: 匿名消息安全
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: c321cbf9-8c05-4cce-b5a5-4bf7b230ee03
ms.openlocfilehash: a49b3542d2b3dd0173b31c9f7b81645ec1098afb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99703895"
---
# <a name="message-security-anonymous"></a><span data-ttu-id="6ce36-103">匿名消息安全</span><span class="sxs-lookup"><span data-stu-id="6ce36-103">Message Security Anonymous</span></span>

<span data-ttu-id="6ce36-104">消息安全匿名示例演示如何实现 Windows Communication Foundation (WCF) 应用程序，该应用程序使用不带客户端身份验证的消息级安全性，但需要使用服务器的 x.509 证书进行服务器身份验证。</span><span class="sxs-lookup"><span data-stu-id="6ce36-104">The Message Security Anonymous sample demonstrates how to implement a Windows Communication Foundation (WCF) application that uses message-level security with no client authentication but that requires server authentication using the server's X.509 certificate.</span></span> <span data-ttu-id="6ce36-105">客户端与服务器之间的所有应用程序消息均已进行签名和加密。</span><span class="sxs-lookup"><span data-stu-id="6ce36-105">All application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="6ce36-106">此示例基于 [WSHttpBinding](wshttpbinding.md) 示例。</span><span class="sxs-lookup"><span data-stu-id="6ce36-106">This sample is based on the [WSHttpBinding](wshttpbinding.md) sample.</span></span> <span data-ttu-id="6ce36-107">此示例由客户端控制台程序 (.exe) 和 Internet 信息服务 (IIS) 所承载的服务库 (.dll) 组成。</span><span class="sxs-lookup"><span data-stu-id="6ce36-107">This sample consists of a client console program (.exe) and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="6ce36-108">该服务实现定义“请求-答复”通信模式的协定。</span><span class="sxs-lookup"><span data-stu-id="6ce36-108">The service implements a contract that defines a request-reply communication pattern.</span></span>

> [!NOTE]
> <span data-ttu-id="6ce36-109">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="6ce36-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="6ce36-110">如果不对客户端进行身份验证，则本示例向返回 `True` 的计算器接口添加新运算。</span><span class="sxs-lookup"><span data-stu-id="6ce36-110">This sample adds a new operation to the calculator interface that returns `True` if the client was not authenticated.</span></span>

```csharp
public class CalculatorService : ICalculator
{
    public bool IsCallerAnonymous()
    {
        // ServiceSecurityContext.IsAnonymous returns true if the caller is not authenticated.
        return ServiceSecurityContext.Current.IsAnonymous;
    }
    ...
}
```

 <span data-ttu-id="6ce36-111">服务公开单一终结点，以便与使用配置文件 (Web.config) 定义的服务进行通信。</span><span class="sxs-lookup"><span data-stu-id="6ce36-111">The service exposes a single endpoint for communicating with the service, defined using a configuration file (Web.config).</span></span> <span data-ttu-id="6ce36-112">终结点由地址、绑定和协定组成。</span><span class="sxs-lookup"><span data-stu-id="6ce36-112">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="6ce36-113">此绑定是用 `wsHttpBinding` 绑定配置的。</span><span class="sxs-lookup"><span data-stu-id="6ce36-113">The binding is configured with a `wsHttpBinding` binding.</span></span> <span data-ttu-id="6ce36-114">`wsHttpBinding` 绑定的默认安全模式是 `Message`。</span><span class="sxs-lookup"><span data-stu-id="6ce36-114">The default security mode for the `wsHttpBinding` binding is `Message`.</span></span> <span data-ttu-id="6ce36-115">`clientCredentialType` 属性设置为 `None`。</span><span class="sxs-lookup"><span data-stu-id="6ce36-115">The `clientCredentialType` attribute is set to `None`.</span></span>

```xml
<system.serviceModel>

  <protocolMapping>
    <add scheme="http" binding="wsHttpBinding" />
  </protocolMapping>

  <bindings>
    <wsHttpBinding>
     <!-- This configuration defines the security mode as Message and -->
     <!-- the clientCredentialType as None. This mode provides -->
     <!-- server authentication only using the service certificate. -->

     <binding>
       <security mode="Message">
         <message clientCredentialType="None" />
       </security>
     </binding>
    </wsHttpBinding>
  </bindings>
  ...
</system.serviceModel>
```

 <span data-ttu-id="6ce36-116">要用于服务身份验证的凭据在中指定 [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) 。</span><span class="sxs-lookup"><span data-stu-id="6ce36-116">The credentials to be used for service authentication are specified in the [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md).</span></span> <span data-ttu-id="6ce36-117">服务器证书包含的 `SubjectName` 的值必须与为 `findValue` 属性指定的值相同，如下面的示例代码所示。</span><span class="sxs-lookup"><span data-stu-id="6ce36-117">The server certificate must contain the same value for the `SubjectName` as the value specified for the `findValue` attribute as shown in the following sample code.</span></span>

```xml
<behaviors>
  <serviceBehaviors>
    <behavior>
      <!--
    The serviceCredentials behavior allows you to define a service certificate.
    A service certificate is used by a client to authenticate the service and provide message protection.
    This configuration references the "localhost" certificate installed during the setup instructions.
    -->
      <serviceCredentials>
        <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
      </serviceCredentials>
      <serviceMetadata httpGetEnabled="True"/>
      <serviceDebug includeExceptionDetailInFaults="False" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```

 <span data-ttu-id="6ce36-118">客户端终结点配置由服务终结点的绝对地址、绑定和协定组成。</span><span class="sxs-lookup"><span data-stu-id="6ce36-118">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="6ce36-119">`wsHttpBinding` 绑定的客户端安全模式为 `Message`。</span><span class="sxs-lookup"><span data-stu-id="6ce36-119">The client security mode for the `wsHttpBinding` binding is `Message`.</span></span> <span data-ttu-id="6ce36-120">`clientCredentialType` 属性设置为 `None`。</span><span class="sxs-lookup"><span data-stu-id="6ce36-120">The `clientCredentialType` attribute is set to `None`.</span></span>

```xml
<system.serviceModel>
  <client>
    <endpoint name=""
             address="http://localhost/servicemodelsamples/service.svc"
             binding="wsHttpBinding"
             behaviorConfiguration="ClientCredentialsBehavior"
             bindingConfiguration="Binding1"
             contract="Microsoft.ServiceModel.Samples.ICalculator" />
  </client>

  <bindings>
    <wsHttpBinding>
      <!--This configuration defines the security mode as -->
      <!--Message and the clientCredentialType as None. -->
      <binding name="Binding1">
        <security mode = "Message">
          <message clientCredentialType="None"/>
        </security>
      </binding>
    </wsHttpBinding>
  </bindings>
  ...
</system.serviceModel>
```

 <span data-ttu-id="6ce36-121">本示例将 <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> 设置为 <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust> 以便对服务的证书进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="6ce36-121">The sample sets the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> to <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust> for authenticating the service's certificate.</span></span> <span data-ttu-id="6ce36-122">这是在`behaviors`一节中的客户端的 App.config 文件中实现的。</span><span class="sxs-lookup"><span data-stu-id="6ce36-122">This is done in the client's App.config file in the `behaviors` section.</span></span> <span data-ttu-id="6ce36-123">这意味着如果证书在用户的“受信任人”存储中，则信任此证书，而不对证书的颁发者链执行身份验证。</span><span class="sxs-lookup"><span data-stu-id="6ce36-123">This means that if the certificate is in the user's Trusted People store, then it is trusted without performing a validation of the certificate's issuer chain.</span></span> <span data-ttu-id="6ce36-124">此处使用的设置是为了方便起见，使示例可以不需要证书颁发机构 (CA) 颁发的证书就能运行。</span><span class="sxs-lookup"><span data-stu-id="6ce36-124">This setting is used here for convenience so that the sample can be run without requiring certificates issued by a certification authority (CA).</span></span> <span data-ttu-id="6ce36-125">此设置没有默认设置 ChainTrust 安全。</span><span class="sxs-lookup"><span data-stu-id="6ce36-125">This setting is less secure than the default, ChainTrust.</span></span> <span data-ttu-id="6ce36-126">在生产代码中使用 `PeerOrChainTrust` 之前，应仔细考虑此设置的安全含义。</span><span class="sxs-lookup"><span data-stu-id="6ce36-126">The security implications of this setting should be carefully considered before using `PeerOrChainTrust` in production code.</span></span>

 <span data-ttu-id="6ce36-127">客户端实现添加对方法的调用 `IsCallerAnonymous` ，否则不同于 [WSHttpBinding](wshttpbinding.md) 示例。</span><span class="sxs-lookup"><span data-stu-id="6ce36-127">The client implementation adds a call to the `IsCallerAnonymous` method and otherwise does not differ from the [WSHttpBinding](wshttpbinding.md) sample.</span></span>

```csharp
// Create a client with a client endpoint configuration.
CalculatorClient client = new CalculatorClient();

// Call the GetCallerIdentity operation.
Console.WriteLine("IsCallerAnonymous returned: {0}", client.IsCallerAnonymous());

// Call the Add service operation.
double value1 = 100.00D;
double value2 = 15.99D;
double result = client.Add(value1, value2);
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

...

//Closing the client gracefully closes the connection and cleans up resources.
client.Close();

Console.WriteLine();
Console.WriteLine("Press <ENTER> to terminate client.");
Console.ReadLine();
```

 <span data-ttu-id="6ce36-128">运行示例时，操作请求和响应将显示在客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="6ce36-128">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="6ce36-129">在客户端窗口中按 Enter 可以关闭客户端。</span><span class="sxs-lookup"><span data-stu-id="6ce36-129">Press ENTER in the client window to shut down the client.</span></span>

```console
IsCallerAnonymous returned: True
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Press <ENTER> to terminate client.
```

 <span data-ttu-id="6ce36-130">“匿名消息安全”示例随附的 Setup.bat 批处理文件使您可以用相关的证书来配置服务器，以运行所承载的需要基于证书的安全的应用程序。</span><span class="sxs-lookup"><span data-stu-id="6ce36-130">The Setup.bat batch file included with the Message Security Anonymous sample enables you to configure the server with a relevant certificate to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="6ce36-131">可以在两种模式中运行此批处理文件。</span><span class="sxs-lookup"><span data-stu-id="6ce36-131">The batch file can be run in two modes.</span></span> <span data-ttu-id="6ce36-132">若要在单一计算机模式下运行该批处理文件，请在命令行键入 `setup.bat`。</span><span class="sxs-lookup"><span data-stu-id="6ce36-132">To run the batch file in the single-computer mode, type `setup.bat` at the command line.</span></span> <span data-ttu-id="6ce36-133">若要在服务模式中运行此文件，请键入 `setup.bat service`。</span><span class="sxs-lookup"><span data-stu-id="6ce36-133">To run it in service mode, type `setup.bat service`.</span></span> <span data-ttu-id="6ce36-134">跨计算机运行示例时，请使用此模式。</span><span class="sxs-lookup"><span data-stu-id="6ce36-134">Use this mode when running the sample across computers.</span></span> <span data-ttu-id="6ce36-135">有关详细信息，请参见本主题末尾的设置过程。</span><span class="sxs-lookup"><span data-stu-id="6ce36-135">See the setup procedure at the end of this topic for details.</span></span>

 <span data-ttu-id="6ce36-136">下面提供了有关此批处理文件的不同部分的简要概述：</span><span class="sxs-lookup"><span data-stu-id="6ce36-136">The following provides a brief overview of the different sections of the batch files:</span></span>

- <span data-ttu-id="6ce36-137">创建服务器证书。</span><span class="sxs-lookup"><span data-stu-id="6ce36-137">Creating the server certificate.</span></span>

     <span data-ttu-id="6ce36-138">Setup.bat 批处理文件中的以下行创建将要使用的服务器证书。</span><span class="sxs-lookup"><span data-stu-id="6ce36-138">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

     <span data-ttu-id="6ce36-139">%SERVER_NAME% 变量指定服务器名称。</span><span class="sxs-lookup"><span data-stu-id="6ce36-139">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="6ce36-140">该证书存储在 LocalMachine 存储区中。</span><span class="sxs-lookup"><span data-stu-id="6ce36-140">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="6ce36-141">如果用服务参数（如 `setup.bat service`）运行 setup 批处理文件，则 %SERVER_NAME% 包含计算机的完全限定域名。</span><span class="sxs-lookup"><span data-stu-id="6ce36-141">If the setup batch file is run with an argument of service (such as `setup.bat service`) the %SERVER_NAME% contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="6ce36-142">否则，它默认为 localhost。</span><span class="sxs-lookup"><span data-stu-id="6ce36-142">Otherwise it defaults to localhost.</span></span>

- <span data-ttu-id="6ce36-143">将服务器证书安装到客户端的受信任证书存储区中。</span><span class="sxs-lookup"><span data-stu-id="6ce36-143">Installing the server certificate into the client's trusted certificate store.</span></span>

     <span data-ttu-id="6ce36-144">以下行将服务器证书复制到客户端的受信任人存储中。</span><span class="sxs-lookup"><span data-stu-id="6ce36-144">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="6ce36-145">因为客户端系统不隐式信任 Makecert.exe 生成的证书，所以需要执行此步骤。</span><span class="sxs-lookup"><span data-stu-id="6ce36-145">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="6ce36-146">如果已经拥有一个证书，该证书来源于客户端的受信任根证书（例如由 Microsoft 颁发的证书），则不需要执行使用服务器证书填充客户端证书存储区这一步骤。</span><span class="sxs-lookup"><span data-stu-id="6ce36-146">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- <span data-ttu-id="6ce36-147">授予对证书私钥的权限。</span><span class="sxs-lookup"><span data-stu-id="6ce36-147">Granting permissions on the certificate's private key.</span></span>

     <span data-ttu-id="6ce36-148">Setup.bat 批处理文件中的以下行使 ASP.NET 工作进程帐户可以访问存储在 LocalMachine 存储区中的服务器证书。</span><span class="sxs-lookup"><span data-stu-id="6ce36-148">The following lines in the Setup.bat batch file make the server certificate stored in the LocalMachine store accessible to the ASP.NET worker process account.</span></span>

    ```bat
    echo ************
    echo setting privileges on server certificates
    echo ************
    for /F "delims=" %%i in ('"%MSSDK%\bin\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE
    (ver | findstr "5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET
    echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R
    iisreset
    ```

> [!NOTE]
> <span data-ttu-id="6ce36-149">如果你使用的是非美国Windows 英文版你必须编辑 Setup.bat 文件，并将 `NT AUTHORITY\NETWORK SERVICE` 帐户名称替换为你的区域性等效项。</span><span class="sxs-lookup"><span data-stu-id="6ce36-149">If you are using a non-U.S. English edition of Windows you must edit the Setup.bat file and replace the `NT AUTHORITY\NETWORK SERVICE` account name with your regional equivalent.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6ce36-150">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="6ce36-150">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="6ce36-151">确保已对 [Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="6ce36-151">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="6ce36-152">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="6ce36-152">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="6ce36-153">在同一计算机上运行示例</span><span class="sxs-lookup"><span data-stu-id="6ce36-153">To run the sample on the same computer</span></span>

1. <span data-ttu-id="6ce36-154">请确保路径包括 Makecert.exe 和 FindPrivateKey.exe 所在的文件夹。</span><span class="sxs-lookup"><span data-stu-id="6ce36-154">Ensure that the path includes the folder where Makecert.exe and FindPrivateKey.exe are located.</span></span>

2. <span data-ttu-id="6ce36-155">从 Visual Studio 的开发人员命令提示中的示例安装文件夹运行 Setup.bat，并使用管理员权限运行。</span><span class="sxs-lookup"><span data-stu-id="6ce36-155">Run Setup.bat from the sample install folder in a Developer Command Prompt for Visual Studio run with administrator privileges.</span></span> <span data-ttu-id="6ce36-156">这将安装运行示例所需的所有证书。</span><span class="sxs-lookup"><span data-stu-id="6ce36-156">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="6ce36-157">安装批处理文件设计为从 Visual Studio 的开发人员命令提示中运行。</span><span class="sxs-lookup"><span data-stu-id="6ce36-157">The setup batch file is designed to be run from a  Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="6ce36-158">这要求路径环境变量指向 SDK 的安装目录。</span><span class="sxs-lookup"><span data-stu-id="6ce36-158">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="6ce36-159">在 Visual Studio 开发人员命令提示中自动设置此环境变量。</span><span class="sxs-lookup"><span data-stu-id="6ce36-159">This environment variable is automatically set within a Developer Command Prompt for Visual Studio.</span></span>  
  
3. <span data-ttu-id="6ce36-160">通过输入地址来验证使用浏览器访问服务 `http://localhost/servicemodelsamples/service.svc` 。</span><span class="sxs-lookup"><span data-stu-id="6ce36-160">Verify access to the service using a browser by entering the address `http://localhost/servicemodelsamples/service.svc`.</span></span>  
  
4. <span data-ttu-id="6ce36-161">启动 \client\bin 中的 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="6ce36-161">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="6ce36-162">客户端活动将显示在客户端控制台应用程序上。</span><span class="sxs-lookup"><span data-stu-id="6ce36-162">Client activity is displayed on the client console application.</span></span>  
  
5. <span data-ttu-id="6ce36-163">如果客户端和服务无法进行通信，请参阅 [WCF 示例的故障排除提示](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="6ce36-163">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="6ce36-164">跨计算机运行示例</span><span class="sxs-lookup"><span data-stu-id="6ce36-164">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="6ce36-165">在服务计算机上创建目录。</span><span class="sxs-lookup"><span data-stu-id="6ce36-165">Create a directory on the service computer.</span></span> <span data-ttu-id="6ce36-166">使用 Internet Information Services (IIS) 管理工具为此目录创建名为 servicemodelsamples 的虚拟应用程序。</span><span class="sxs-lookup"><span data-stu-id="6ce36-166">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services (IIS) management tool.</span></span>  
  
2. <span data-ttu-id="6ce36-167">将服务程序文件从 \inetpub\wwwroot\servicemodelsamples 复制到服务计算机上的虚拟目录中。</span><span class="sxs-lookup"><span data-stu-id="6ce36-167">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="6ce36-168">确保复制 \bin 子目录中的文件。</span><span class="sxs-lookup"><span data-stu-id="6ce36-168">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="6ce36-169">另外，将 Setup.bat 和 Cleanup.bat 文件复制到服务计算机上。</span><span class="sxs-lookup"><span data-stu-id="6ce36-169">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="6ce36-170">在客户端计算机上为这些客户端二进制文件创建一个目录。</span><span class="sxs-lookup"><span data-stu-id="6ce36-170">Create a directory on the client computer for the client binaries.</span></span>  
  
4. <span data-ttu-id="6ce36-171">将客户端程序文件复制到客户端计算机上的客户端目录中。</span><span class="sxs-lookup"><span data-stu-id="6ce36-171">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="6ce36-172">另外，将 Setup.bat、Cleanup.bat 和 ImportServiceCert.bat 文件复制到客户端上。</span><span class="sxs-lookup"><span data-stu-id="6ce36-172">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="6ce36-173">在服务器上， `setup.bat service` 在使用管理员特权打开的 Visual Studio 开发人员命令提示中运行。</span><span class="sxs-lookup"><span data-stu-id="6ce36-173">On the server, run `setup.bat service` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="6ce36-174">使用参数运行将使用 `setup.bat` `service` 计算机的完全限定的域名创建一个服务证书，并将服务证书导出到名为的文件。</span><span class="sxs-lookup"><span data-stu-id="6ce36-174">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="6ce36-175">编辑 Web.config，以反映) 的属性中 (新的证书名称，该名称与 `findValue` [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) 计算机的完全限定域名相同。</span><span class="sxs-lookup"><span data-stu-id="6ce36-175">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), which is the same as the fully-qualified domain name of the computer.</span></span>  
  
7. <span data-ttu-id="6ce36-176">将服务目录中的 Service.cer 文件复制到客户端计算机上的客户端目录中。</span><span class="sxs-lookup"><span data-stu-id="6ce36-176">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8. <span data-ttu-id="6ce36-177">在客户端计算机上的 Client.exe.config 文件中，更改终结点的地址值，使其与服务的新地址相匹配。</span><span class="sxs-lookup"><span data-stu-id="6ce36-177">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="6ce36-178">在客户端上，在使用管理员特权打开的 Visual Studio 开发人员命令提示中运行 ImportServiceCert.bat。</span><span class="sxs-lookup"><span data-stu-id="6ce36-178">On the client, run ImportServiceCert.bat in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="6ce36-179">这会将 Service.cer 文件中的服务证书导入 CurrentUser – TrustedPeople 存储区。</span><span class="sxs-lookup"><span data-stu-id="6ce36-179">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="6ce36-180">在客户端计算机上，在命令提示符下启动 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="6ce36-180">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="6ce36-181">如果客户端和服务无法进行通信，请参阅 [WCF 示例的故障排除提示](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="6ce36-181">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="6ce36-182">运行示例后进行清理</span><span class="sxs-lookup"><span data-stu-id="6ce36-182">To clean up after the sample</span></span>  
  
- <span data-ttu-id="6ce36-183">运行完示例后运行示例文件夹中的 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="6ce36-183">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6ce36-184">此脚本不会在跨计算机运行此示例时移除客户端上的服务证书。</span><span class="sxs-lookup"><span data-stu-id="6ce36-184">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="6ce36-185">如果你已运行 Windows Communication Foundation 跨计算机使用证书 (WCF) 示例，请确保清除已安装在 CurrentUser-TrustedPeople 存储中的服务证书。</span><span class="sxs-lookup"><span data-stu-id="6ce36-185">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="6ce36-186">为此，请使用以下命令：`certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`，例如：`certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com.`。</span><span class="sxs-lookup"><span data-stu-id="6ce36-186">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com.`</span></span>
