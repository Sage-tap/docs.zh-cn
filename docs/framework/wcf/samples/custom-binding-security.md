---
description: 了解详细信息：自定义绑定安全性
title: 自定义绑定安全性
ms.date: 03/30/2017
ms.assetid: a6383dff-4308-46d2-bc6d-acd4e18b4b8d
ms.openlocfilehash: f0ed4b40fe4e0869f34a4f6016123dc9f0a57f45
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99732626"
---
# <a name="custom-binding-security"></a><span data-ttu-id="1f95d-103">自定义绑定安全性</span><span class="sxs-lookup"><span data-stu-id="1f95d-103">Custom Binding Security</span></span>

<span data-ttu-id="1f95d-104">本示例演示如何使用自定义绑定配置安全性。</span><span class="sxs-lookup"><span data-stu-id="1f95d-104">This sample demonstrates how to configure security by using a custom binding.</span></span> <span data-ttu-id="1f95d-105">并演示如何使用自定义绑定实现消息级安全性和安全传输。</span><span class="sxs-lookup"><span data-stu-id="1f95d-105">It shows how to use a custom binding to enable message-level security together with a secure transport.</span></span> <span data-ttu-id="1f95d-106">如果在客户端和服务之间传输消息时需要进行安全的传输，同时消息必须在消息级别上保持安全，这非常有用。</span><span class="sxs-lookup"><span data-stu-id="1f95d-106">This is useful when a secure transport is required to transmit the messages between client and service and simultaneously the messages must be secure on the message level.</span></span> <span data-ttu-id="1f95d-107">系统提供的绑定不支持此配置。</span><span class="sxs-lookup"><span data-stu-id="1f95d-107">This configuration is not supported by system-provided bindings.</span></span>

<span data-ttu-id="1f95d-108">本示例由客户端控制台程序 (EXE) 和服务控制台程序 (EXE) 组成。</span><span class="sxs-lookup"><span data-stu-id="1f95d-108">This sample consists of a client console program (EXE) and a service console program (EXE).</span></span> <span data-ttu-id="1f95d-109">该服务实现双工协定。</span><span class="sxs-lookup"><span data-stu-id="1f95d-109">The service implements a duplex contract.</span></span> <span data-ttu-id="1f95d-110">该协定由 `ICalculatorDuplex` 接口定义，该接口公开数学运算（加、减、乘和除）。</span><span class="sxs-lookup"><span data-stu-id="1f95d-110">The contract is defined by the `ICalculatorDuplex` interface, which exposes math operations (Add, Subtract, Multiply, and Divide).</span></span> <span data-ttu-id="1f95d-111">`ICalculatorDuplex` 接口允许客户端执行数学运算，通过会话计算运行结果。</span><span class="sxs-lookup"><span data-stu-id="1f95d-111">The `ICalculatorDuplex` interface allows the client to perform math operations, calculating a running result over a session.</span></span> <span data-ttu-id="1f95d-112">服务可以独立地在 `ICalculatorDuplexCallback` 接口上返回结果。</span><span class="sxs-lookup"><span data-stu-id="1f95d-112">Independently, the service may return results on the `ICalculatorDuplexCallback` interface.</span></span> <span data-ttu-id="1f95d-113">双工协定需要会话，因为必须建立上下文才能将客户端和服务之间发送的一组消息关联在一起。</span><span class="sxs-lookup"><span data-stu-id="1f95d-113">A duplex contract requires a session, because a context must be established to correlate the set of messages being sent between the client and the service.</span></span> <span data-ttu-id="1f95d-114">定义的自定义绑定支持双工通信并且是安全的。</span><span class="sxs-lookup"><span data-stu-id="1f95d-114">A custom binding is defined that supports duplex communication and is secure.</span></span>

> [!NOTE]
> <span data-ttu-id="1f95d-115">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="1f95d-115">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="1f95d-116">服务配置可定义支持以下内容的自定义绑定：</span><span class="sxs-lookup"><span data-stu-id="1f95d-116">The service configuration defines a custom binding that supports the following:</span></span>

- <span data-ttu-id="1f95d-117">使用 TLS/SSL 协议保护的 TCP 通信。</span><span class="sxs-lookup"><span data-stu-id="1f95d-117">TCP communication protected by using the TLS/SSL protocol.</span></span>

- <span data-ttu-id="1f95d-118">Windows 消息安全。</span><span class="sxs-lookup"><span data-stu-id="1f95d-118">Windows message security.</span></span>

<span data-ttu-id="1f95d-119">自定义绑定配置通过同时启用消息级安全性来启用安全传输。</span><span class="sxs-lookup"><span data-stu-id="1f95d-119">The custom binding configuration enables secure transport by simultaneously enabling the message-level security.</span></span> <span data-ttu-id="1f95d-120">在定义自定义绑定时，绑定元素的排序非常重要，因为每个元素都表示通道堆栈中的一个层 (请参阅 [自定义绑定](../extending/custom-bindings.md)) 。</span><span class="sxs-lookup"><span data-stu-id="1f95d-120">The ordering of binding elements is important in defining a custom binding, because each represents a layer in the channel stack (see [Custom Bindings](../extending/custom-bindings.md)).</span></span> <span data-ttu-id="1f95d-121">自定义绑定在服务和客户端配置文件中进行定义，如下面的示例配置所示。</span><span class="sxs-lookup"><span data-stu-id="1f95d-121">The custom binding is defined in the service and client configuration files, as shown in the following sample configuration.</span></span>

```xml
<bindings>
  <!-- Configure a custom binding. -->
  <customBinding>
    <binding name="Binding1">
      <security authenticationMode="SecureConversation"
                 requireSecurityContextCancellation="true">
      </security>
      <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8"/>
      <sslStreamSecurity requireClientCertificate="false"/>
      <tcpTransport/>
    </binding>
  </customBinding>
</bindings>
```

<span data-ttu-id="1f95d-122">此自定义绑定使用服务证书在传输级别对服务进行身份验证，并且在客户端与服务之间传输消息时保护消息。</span><span class="sxs-lookup"><span data-stu-id="1f95d-122">The custom binding uses a service certificate to authenticate the service on the transport level and to protect the messages during the transmission between client and service.</span></span> <span data-ttu-id="1f95d-123">这是通过 `sslStreamSecurity` 绑定元素实现的。</span><span class="sxs-lookup"><span data-stu-id="1f95d-123">This is accomplished by the `sslStreamSecurity` binding element.</span></span> <span data-ttu-id="1f95d-124">服务证书使用服务行为进行配置，如下面的示例配置所示。</span><span class="sxs-lookup"><span data-stu-id="1f95d-124">The service's certificate is configured using a service behavior as shown in the following sample configuration.</span></span>

```xml
<behaviors>
    <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
        <serviceMetadata />
        <serviceDebug includeExceptionDetailInFaults="False" />
        <serviceCredentials>
        <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName"/>
        </serviceCredentials>
    </behavior>
    </serviceBehaviors>
</behaviors>
```

<span data-ttu-id="1f95d-125">此外，此自定义绑定将消息安全性与 Windows 凭据类型（默认凭据类型）一起使用。</span><span class="sxs-lookup"><span data-stu-id="1f95d-125">Additionally, the custom binding uses message security with Windows credential type - this is the default credential type.</span></span> <span data-ttu-id="1f95d-126">这是通过 `security` 绑定元素实现的。</span><span class="sxs-lookup"><span data-stu-id="1f95d-126">This is accomplished by the `security` binding element.</span></span> <span data-ttu-id="1f95d-127">如果 Kerberos 身份验证机制可用，则使用消息级安全性对客户端和服务进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="1f95d-127">Both client and service are authenticated using message-level security if the Kerberos authentication mechanism is available.</span></span> <span data-ttu-id="1f95d-128">如果在 Active Directory 环境中运行示例，则会发生这种情况。</span><span class="sxs-lookup"><span data-stu-id="1f95d-128">This happens if the sample is run in the Active Directory environment.</span></span> <span data-ttu-id="1f95d-129">如果 Kerberos 身份验证机制不可用，则使用 NTLM 身份验证。</span><span class="sxs-lookup"><span data-stu-id="1f95d-129">If the Kerberos authentication mechanism is not available, NTLM authentication is used.</span></span> <span data-ttu-id="1f95d-130">NTLM 向服务对客户端进行身份验证，但不向客户端对服务进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="1f95d-130">NTLM authenticates the client to the service but does not authenticate the service to the client.</span></span> <span data-ttu-id="1f95d-131">`security`绑定元素配置为使用 `SecureConversation` `authenticationType` ，这将导致在客户端和服务上创建安全会话。</span><span class="sxs-lookup"><span data-stu-id="1f95d-131">The `security` binding element is configured to use `SecureConversation` `authenticationType`, which results in the creation of a security session on both the client and the service.</span></span> <span data-ttu-id="1f95d-132">为了使服务的双工协定起作用，需要这么做。</span><span class="sxs-lookup"><span data-stu-id="1f95d-132">This is required to enable the service's duplex contract to work.</span></span>

<span data-ttu-id="1f95d-133">运行示例时，操作请求和响应将显示在客户端的控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="1f95d-133">When you run the sample, the operation requests and responses are displayed in the client's console window.</span></span> <span data-ttu-id="1f95d-134">在客户端窗口中按 Enter 可以关闭客户端。</span><span class="sxs-lookup"><span data-stu-id="1f95d-134">Press ENTER in the client window to shut down the client.</span></span>

```console
Press <ENTER> to terminate client.
Result(100)
Result(50)
Result(882.5)
Result(441.25)
Equation(0 + 100 - 50 * 17.65 / 2 = 441.25)
```

<span data-ttu-id="1f95d-135">当运行示例时，在回调接口上可以看到从服务发送的、返回到客户端的消息。</span><span class="sxs-lookup"><span data-stu-id="1f95d-135">When you run the sample, you see the messages returned to the client on the callback interface sent from the service.</span></span> <span data-ttu-id="1f95d-136">显示每个中间结果，最后在所有操作完成时显示整个公式。</span><span class="sxs-lookup"><span data-stu-id="1f95d-136">Each intermediate result is displayed, followed by the entire equation upon completion of all operations.</span></span> <span data-ttu-id="1f95d-137">按 Enter 可关闭客户端。</span><span class="sxs-lookup"><span data-stu-id="1f95d-137">Press ENTER to shut down the client.</span></span>

<span data-ttu-id="1f95d-138">通过运行所包含的 Setup.bat 文件，可以用相关的服务证书配置客户端和服务器，使其可以运行需要基于证书的安全性的承载应用程序。</span><span class="sxs-lookup"><span data-stu-id="1f95d-138">The included Setup.bat file enables you to configure the client and server with the relevant service certificate to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="1f95d-139">必须修改此批处理文件，以便跨计算机或在非承载情况下工作。</span><span class="sxs-lookup"><span data-stu-id="1f95d-139">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

<span data-ttu-id="1f95d-140">下面提供了批处理文件中适用于本示例的各个节的简要概述，以便可以修改批处理文件从而在相应的配置下运行：</span><span class="sxs-lookup"><span data-stu-id="1f95d-140">The following provides a brief overview of the different sections of the batch files that apply to this sample so that they can be modified to run in the appropriate configuration:</span></span>

- <span data-ttu-id="1f95d-141">创建服务器证书。</span><span class="sxs-lookup"><span data-stu-id="1f95d-141">Creating the server certificate.</span></span>

  <span data-ttu-id="1f95d-142">Setup.bat 文件中的以下行创建将要使用的服务器证书。</span><span class="sxs-lookup"><span data-stu-id="1f95d-142">The following lines from the Setup.bat file create the server certificate to be used.</span></span> <span data-ttu-id="1f95d-143">`%SERVER_NAME%`变量指定服务器名称。</span><span class="sxs-lookup"><span data-stu-id="1f95d-143">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="1f95d-144">更改此变量可以指定您自己的服务器名称。</span><span class="sxs-lookup"><span data-stu-id="1f95d-144">Change this variable to specify your own server name.</span></span> <span data-ttu-id="1f95d-145">此批处理文件将服务器名默认为 localhost。</span><span class="sxs-lookup"><span data-stu-id="1f95d-145">This batch file defaults the server name to localhost.</span></span>

  <span data-ttu-id="1f95d-146">证书存储在 Web 承载的服务的 CurrentUser 存储中。</span><span class="sxs-lookup"><span data-stu-id="1f95d-146">The certificate is stored in the CurrentUser store for the Web-hosted services.</span></span>

  ```bat
  echo ************
  echo Server cert setup starting
  echo %SERVER_NAME%
  echo ************
  echo making server cert
  echo ************
  makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
  ```

- <span data-ttu-id="1f95d-147">将服务器证书安装到客户端的受信任证书存储区中。</span><span class="sxs-lookup"><span data-stu-id="1f95d-147">Installing the server certificate into the client's trusted certificate store.</span></span>

  <span data-ttu-id="1f95d-148">Setup.bat 文件中的以下行将服务器证书复制到客户端的受信任人存储中。</span><span class="sxs-lookup"><span data-stu-id="1f95d-148">The following lines in the Setup.bat file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="1f95d-149">因为客户端系统不隐式信任 Makecert.exe 生成的证书，所以需要执行此步骤。</span><span class="sxs-lookup"><span data-stu-id="1f95d-149">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="1f95d-150">如果已经拥有一个证书，该证书来源于客户端的受信任根证书（例如由 Microsoft 颁发的证书），则不需要执行使用服务器证书填充客户端证书存储区这一步骤。</span><span class="sxs-lookup"><span data-stu-id="1f95d-150">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

  ```console
  certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
  ```

  > [!NOTE]
  > <span data-ttu-id="1f95d-151">Setup.bat 批处理文件设计为通过 Visual Studio 2010 命令提示运行。</span><span class="sxs-lookup"><span data-stu-id="1f95d-151">The Setup.bat batch file is designed to be run from a Visual Studio 2010 Command Prompt.</span></span> <span data-ttu-id="1f95d-152">这要求 MSSDK 环境变量指向 SDK 的安装目录。</span><span class="sxs-lookup"><span data-stu-id="1f95d-152">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="1f95d-153">将在 Visual Studio 2010 命令提示中自动设置此环境变量。</span><span class="sxs-lookup"><span data-stu-id="1f95d-153">This environment variable is automatically set within a Visual Studio 2010 Command Prompt.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1f95d-154">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="1f95d-154">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="1f95d-155">确保已对 [Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="1f95d-155">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="1f95d-156">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="1f95d-156">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="1f95d-157">若要以单机配置或跨计算机配置来运行示例，请按照 [运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="1f95d-157">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="1f95d-158">在同一计算机上运行示例</span><span class="sxs-lookup"><span data-stu-id="1f95d-158">To run the sample on the same computer</span></span>

1. <span data-ttu-id="1f95d-159">使用管理员权限打开 Visual Studio 窗口的开发人员命令提示，并从示例安装文件夹中运行 Setup.bat。</span><span class="sxs-lookup"><span data-stu-id="1f95d-159">Open a Developer Command Prompt for Visual Studio window with administrator privileges and run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="1f95d-160">这将安装运行示例所需的所有证书。</span><span class="sxs-lookup"><span data-stu-id="1f95d-160">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="1f95d-161">Setup.bat 批处理文件设计为在 Visual Studio 2012 命令提示符下运行。</span><span class="sxs-lookup"><span data-stu-id="1f95d-161">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="1f95d-162">在 Visual Studio 2012 命令提示符下设置的 PATH 环境变量指向包含 Setup.bat 脚本所需的可执行文件的目录。</span><span class="sxs-lookup"><span data-stu-id="1f95d-162">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>

2. <span data-ttu-id="1f95d-163">启动 \service\bin 中的 Service.exe。</span><span class="sxs-lookup"><span data-stu-id="1f95d-163">Launch Service.exe from \service\bin.</span></span>

3. <span data-ttu-id="1f95d-164">启动 \client\bin 中的 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="1f95d-164">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="1f95d-165">客户端活动将显示在客户端控制台应用程序上。</span><span class="sxs-lookup"><span data-stu-id="1f95d-165">Client activity is displayed on the client console application.</span></span>

4. <span data-ttu-id="1f95d-166">如果客户端和服务无法进行通信，请参阅 [WCF 示例的故障排除提示](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="1f95d-166">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>

### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="1f95d-167">跨计算机运行示例</span><span class="sxs-lookup"><span data-stu-id="1f95d-167">To run the sample across computers</span></span>

1. <span data-ttu-id="1f95d-168">在服务计算机上：</span><span class="sxs-lookup"><span data-stu-id="1f95d-168">On the service computer:</span></span>

    1. <span data-ttu-id="1f95d-169">在服务计算机上创建一个名为 servicemodelsamples 的虚拟目录。</span><span class="sxs-lookup"><span data-stu-id="1f95d-169">Create a virtual directory named servicemodelsamples on the service computer.</span></span>

    2. <span data-ttu-id="1f95d-170">将服务程序文件从 \inetpub\wwwroot\servicemodelsamples 复制到服务计算机上的虚拟目录中。</span><span class="sxs-lookup"><span data-stu-id="1f95d-170">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="1f95d-171">确保复制 \bin 子目录中的文件。</span><span class="sxs-lookup"><span data-stu-id="1f95d-171">Ensure that you copy the files in the \bin subdirectory.</span></span>

    3. <span data-ttu-id="1f95d-172">将 Setup.bat 和 Cleanup.bat 文件复制到服务计算机上。</span><span class="sxs-lookup"><span data-stu-id="1f95d-172">Copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>

    4. <span data-ttu-id="1f95d-173">在使用管理员权限打开的 Visual Studio 开发人员命令提示中运行以下命令： `Setup.bat service` 。</span><span class="sxs-lookup"><span data-stu-id="1f95d-173">Run the following command in a Developer Command Prompt for Visual Studio opened with administrator privileges: `Setup.bat service`.</span></span> <span data-ttu-id="1f95d-174">这会用与运行批处理文件的计算机的名称匹配的主题名称创建服务证书。</span><span class="sxs-lookup"><span data-stu-id="1f95d-174">This creates the service certificate with the subject name matching the name of the computer the batch file was run on.</span></span>

        > [!NOTE]
        > <span data-ttu-id="1f95d-175">Setup.bat 批处理文件设计为通过 Visual Studio 2010 命令提示运行。</span><span class="sxs-lookup"><span data-stu-id="1f95d-175">The Setup.bat batch file is designed to be run from a Visual Studio 2010 Command Prompt.</span></span> <span data-ttu-id="1f95d-176">这要求路径环境变量指向 SDK 的安装目录。</span><span class="sxs-lookup"><span data-stu-id="1f95d-176">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="1f95d-177">将在 Visual Studio 2010 命令提示中自动设置此环境变量。</span><span class="sxs-lookup"><span data-stu-id="1f95d-177">This environment variable is automatically set within a Visual Studio 2010 Command Prompt.</span></span>

    5. <span data-ttu-id="1f95d-178">更改 [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) Service.exe.config 文件中的，以反映在上一步中生成的证书的使用者名称。</span><span class="sxs-lookup"><span data-stu-id="1f95d-178">Change the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) inside the Service.exe.config file to reflect the subject name of the certificate generated in the previous step.</span></span>

    6. <span data-ttu-id="1f95d-179">在命令提示符下运行 Service.exe。</span><span class="sxs-lookup"><span data-stu-id="1f95d-179">Run Service.exe from a command prompt.</span></span>

2. <span data-ttu-id="1f95d-180">在客户端计算机上执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="1f95d-180">On the client computer:</span></span>

    1. <span data-ttu-id="1f95d-181">将 \client\bin\ 文件夹中的客户端程序文件复制到客户端计算机上。</span><span class="sxs-lookup"><span data-stu-id="1f95d-181">Copy the client program files from the \client\bin\ folder to the client computer.</span></span> <span data-ttu-id="1f95d-182">还要复制 Cleanup.bat 文件。</span><span class="sxs-lookup"><span data-stu-id="1f95d-182">Also copy the Cleanup.bat file.</span></span>

    2. <span data-ttu-id="1f95d-183">运行 Cleanup.bat 以移除先前示例中使用的所有旧证书。</span><span class="sxs-lookup"><span data-stu-id="1f95d-183">Run Cleanup.bat to remove any old certificates from previous samples.</span></span>

    3. <span data-ttu-id="1f95d-184">通过使用管理特权打开 Visual Studio 的开发人员命令提示，并在服务计算机上运行以下命令来导出服务的证书 (替换 `%SERVER_NAME%` 为运行服务的计算机的完全限定名称) ：</span><span class="sxs-lookup"><span data-stu-id="1f95d-184">Export the service's certificate by opening a Developer Command Prompt for Visual Studio with administrative privileges, and running the following command on the service computer (substitute `%SERVER_NAME%` with the fully-qualified name of the computer where the service is running):</span></span>

        ```console
        certmgr -put -r LocalMachine -s My -c -n %SERVER_NAME% %SERVER_NAME%.cer
        ```

    4. <span data-ttu-id="1f95d-185">将 %SERVER_NAME%.cer 复制到客户端计算机（用运行服务的计算机的完全限定名称替换 %SERVER_NAME%）。</span><span class="sxs-lookup"><span data-stu-id="1f95d-185">Copy %SERVER_NAME%.cer to the client computer (substitute %SERVER_NAME% with the fully-qualified name of the computer where the service is running).</span></span>

    5. <span data-ttu-id="1f95d-186">通过使用管理特权打开 Visual Studio 的开发人员命令提示，然后在客户端计算机上运行以下命令来导入服务的证书 (使用运行该服务的计算机的完全限定名称替换% SERVER_NAME%) ：</span><span class="sxs-lookup"><span data-stu-id="1f95d-186">Import the service's certificate by opening a Developer Command Prompt for Visual Studio with administrative privileges, and running the following command on the client computer (substitute %SERVER_NAME% with the fully-qualified name of the computer where the service is running):</span></span>

        ```console
        certmgr.exe -add -c %SERVER_NAME%.cer -s -r CurrentUser TrustedPeople
        ```

        <span data-ttu-id="1f95d-187">如果证书是由可信颁发者颁发的，则不需要执行步骤 c、d 和 e。</span><span class="sxs-lookup"><span data-stu-id="1f95d-187">Steps c, d, and e are not necessary if the certificate is issued by a Trusted Issuer.</span></span>

    6. <span data-ttu-id="1f95d-188">按如下所示修改客户端的 App.config 文件：</span><span class="sxs-lookup"><span data-stu-id="1f95d-188">Modify the client’s App.config file as follows:</span></span>

        ```xml
        <client>
            <endpoint name="default"
                address="net.tcp://ReplaceThisWithServiceMachineName:8000/ServiceModelSamples/Service"
                binding="customBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex"
                behaviorConfiguration="CalculatorClientBehavior" />
        </client>
        ```

    7. <span data-ttu-id="1f95d-189">如果在域环境中 NetworkService 或 LocalSystem 以外的帐户下运行服务，则可能需要修改客户端的 App.config 文件中服务终结点的终结点标识，以便基于用于运行服务的帐户来设置相应的 UPN 或 SPN。</span><span class="sxs-lookup"><span data-stu-id="1f95d-189">If the service is running under an account other than the NetworkService or LocalSystem account in a domain environment, you might need to modify the endpoint identity for the service endpoint inside the client's App.config file to set the appropriate UPN or SPN based on the account that is used to run the service.</span></span> <span data-ttu-id="1f95d-190">有关终结点标识的详细信息，请参阅 [服务标识和身份验证](../feature-details/service-identity-and-authentication.md) 主题。</span><span class="sxs-lookup"><span data-stu-id="1f95d-190">For more information about endpoint identity, see the [Service Identity and Authentication](../feature-details/service-identity-and-authentication.md) topic.</span></span>

    8. <span data-ttu-id="1f95d-191">在命令提示符下运行 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="1f95d-191">Run Client.exe from a command prompt.</span></span>

### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="1f95d-192">运行示例后进行清理</span><span class="sxs-lookup"><span data-stu-id="1f95d-192">To clean up after the sample</span></span>

- <span data-ttu-id="1f95d-193">运行完示例后运行示例文件夹中的 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="1f95d-193">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>
