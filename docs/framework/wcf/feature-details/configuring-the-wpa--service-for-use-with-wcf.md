---
description: 了解有关以下内容的详细信息：配置 Windows 进程激活服务以用于 Windows Communication Foundation
title: 配置 Windows 进程激活服务以用于 Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 1d50712e-53cd-4773-b8bc-a1e1aad66b78
ms.openlocfilehash: b98cc776b3a0bd860b4837ba70d58d10a83827dc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780617"
---
# <a name="configuring-the-windows-process-activation-service-for-use-with-windows-communication-foundation"></a><span data-ttu-id="17952-103">配置 Windows 进程激活服务以用于 Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="17952-103">Configuring the Windows Process Activation Service for Use with Windows Communication Foundation</span></span>

<span data-ttu-id="17952-104">本主题介绍设置 Windows 进程激活服务所需的步骤， (在 Windows Vista 中也称为) ，以承载 Windows Communication Foundation (不通过 HTTP 网络协议进行通信的 WCF) 服务。</span><span class="sxs-lookup"><span data-stu-id="17952-104">This topic describes the steps required to set up Windows Process Activation Service (also known as WAS) in Windows Vista to host Windows Communication Foundation (WCF) services that do not communicate over HTTP network protocols.</span></span> <span data-ttu-id="17952-105">下面的部分略述此配置的步骤：</span><span class="sxs-lookup"><span data-stu-id="17952-105">The following sections outline the steps for this configuration:</span></span>  
  
- <span data-ttu-id="17952-106">安装 (或确认 WCF 激活组件) 的安装。</span><span class="sxs-lookup"><span data-stu-id="17952-106">Install (or confirm the installation of) the WCF activation components required.</span></span>  
  
- <span data-ttu-id="17952-107">创建一个具有要使用的网络协议绑定的 WAS 站点，或者向现有站点添加新协议绑定。</span><span class="sxs-lookup"><span data-stu-id="17952-107">Create a WAS site with the network protocol bindings you wish to use, or add a new protocol binding to an existing site.</span></span>  
  
- <span data-ttu-id="17952-108">创建一个应用程序以承载服务，并使该应用程序可以使用所需的网络协议。</span><span class="sxs-lookup"><span data-stu-id="17952-108">Create an application to host your services and enable that application to use the required network protocols.</span></span>  
  
- <span data-ttu-id="17952-109">生成公开非 HTTP 终结点的 WCF 服务。</span><span class="sxs-lookup"><span data-stu-id="17952-109">Build a WCF service that exposes a non-HTTP endpoint.</span></span>  
  
## <a name="configuring-a-site-with-non-http-bindings"></a><span data-ttu-id="17952-110">使用非 HTTP 绑定配置站点</span><span class="sxs-lookup"><span data-stu-id="17952-110">Configuring a Site with Non-HTTP bindings</span></span>  

 <span data-ttu-id="17952-111">若要将非 HTTP 绑定与 WAS 一起使用，必须将站点绑定添加到 WAS 配置。</span><span class="sxs-lookup"><span data-stu-id="17952-111">To use a non-HTTP binding with WAS, the site binding must be added to the WAS configuration.</span></span> <span data-ttu-id="17952-112">WAS 的配置存储是 applicationHost.config 文件，该文件位于 %windir%\system32\inetsrv\config 目录中。</span><span class="sxs-lookup"><span data-stu-id="17952-112">The configuration store for WAS is the applicationHost.config file, located in the %windir%\system32\inetsrv\config directory.</span></span> <span data-ttu-id="17952-113">此配置存储由 WAS 和 IIS 7.0 共享。</span><span class="sxs-lookup"><span data-stu-id="17952-113">This configuration store is shared by both WAS and IIS 7.0.</span></span>  
  
 <span data-ttu-id="17952-114">applicationHost.config 是一个 XML 文本文件，可以使用任何标准文本编辑器（如记事本）打开。</span><span class="sxs-lookup"><span data-stu-id="17952-114">applicationHost.config is an XML text file that can be opened with any standard text editor (such as Notepad).</span></span> <span data-ttu-id="17952-115">但是，IIS 7.0 命令行配置工具 ( # A0) 是添加非 HTTP 网站绑定的首选方法。</span><span class="sxs-lookup"><span data-stu-id="17952-115">However, the IIS 7.0 command-line configuration tool (appcmd.exe) is the preferred way to add non-HTTP site bindings.</span></span>  
  
 <span data-ttu-id="17952-116">下面的命令使用 appcmd.exe 将 net.tcp 站点绑定添加到默认网站（将此命令作为单独的一行输入）。</span><span class="sxs-lookup"><span data-stu-id="17952-116">The following command adds a net.tcp site binding to the default Web site using appcmd.exe (this command is entered as a single line).</span></span>  
  
```console  
appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
```  
  
 <span data-ttu-id="17952-117">通过将下面指示的行添加到 applicationHost.config 文件，此命令将新 net.tcp 绑定添加到默认网站。</span><span class="sxs-lookup"><span data-stu-id="17952-117">This command adds the new net.tcp binding to the default Web site by adding the line indicated below to the applicationHost.config file.</span></span>  
  
```xml  
<sites>  
    <site name="Default Web Site" id="1">  
        <bindings>  
            <binding protocol="HTTP" bindingInformation="*:80:" />  
            //The following line is added by the command.  
            <binding protocol="net.tcp" bindingInformation="808:*" />  
        </bindings>  
    </site>  
</sites>  
```  
  
## <a name="enabling-an-application-to-use-non-http-protocols"></a><span data-ttu-id="17952-118">使应用程序可以使用非 HTTP 协议</span><span class="sxs-lookup"><span data-stu-id="17952-118">Enabling an Application to Use Non-HTTP Protocols</span></span>  

 <span data-ttu-id="17952-119">可以启用或禁用单个网络 protocolsat 应用程序级别。</span><span class="sxs-lookup"><span data-stu-id="17952-119">You can enable or disable individual network protocolsat the application level.</span></span> <span data-ttu-id="17952-120">下面的命令说明如何为在 `Default Web Site` 中运行的应用程序同时启用 HTTP 和 net.tcp 协议。</span><span class="sxs-lookup"><span data-stu-id="17952-120">The following command illustrates how to enable both the HTTP and net.tcp protocols for an application that runs in the `Default Web Site`.</span></span>  
  
```console  
appcmd.exe set app "Default Web Site/appOne" /enabledProtocols:net.tcp  
```  
  
 <span data-ttu-id="17952-121">还可以在 \<applicationDefaults> 存储在 ApplicationHost.config 中的站点 XML 配置的元素中设置启用的协议的列表。</span><span class="sxs-lookup"><span data-stu-id="17952-121">The list of enabled protocols can also be set in the \<applicationDefaults> element of the site’s XML configuration stored in ApplicationHost.config.</span></span>  
  
 <span data-ttu-id="17952-122">摘自 applicationHost.config 的以下 XML 代码说明一个已同时绑定到 HTTP 协议和非 HTTP 协议的站点。</span><span class="sxs-lookup"><span data-stu-id="17952-122">The following XML code from applicationHost.config illustrates a site bound to both HTTP and non-HTTP protocols.</span></span> <span data-ttu-id="17952-123">支持非 HTTP 协议所需的其他配置通过注释进行了突出。</span><span class="sxs-lookup"><span data-stu-id="17952-123">The additional configuration required to support non-HTTP protocols is called out with comments.</span></span>  
  
```xml  
<sites>  
    <site name="Default Web Site" id="1">  
      <application path="/">  
        <virtualDirectory path="/" physicalPath="D:\inetpub\wwwroot" />  
      </application>  
      <bindings>  
            <!-- The following two lines are added by the command. -->
            <binding protocol="HTTP" bindingInformation="*:80:" />  
            <binding protocol="net.tcp" bindingInformation="808:*" />  
       </bindings>  
    </site>  
    <siteDefaults>  
        <logFile
        customLogPluginClsid="{FF160663-DE82-11CF-BC0A-00AA006111E0}"  
          directory="D:\inetpub\logs\LogFiles" />  
        <traceFailedRequestsLogging
          directory="D:\inetpub\logs\FailedReqLogFiles" />  
    </siteDefaults>  
    <applicationDefaults
      applicationPool="DefaultAppPool"
      <!-- The following line is inserted by the command. -->
      enabledProtocols="http, net.tcp" />  
    <virtualDirectoryDefaults allowSubDirConfig="true" />  
</sites>  
```  
  
 <span data-ttu-id="17952-124">如果您尝试通过用于非 HTTP 激活的 WAS 来激活服务，并且您未安装和配置 WAS，您可能会看到以下错误：</span><span class="sxs-lookup"><span data-stu-id="17952-124">If you attempt to activate a service using WAS for Non-HTTP activation and you have not installed and configured WAS you may see the following error:</span></span>  
  
```output  
[InvalidOperationException: The protocol 'net.tcp' does not have an implementation of HostedTransportConfiguration type registered.]   System.ServiceModel.AsyncResult.End(IAsyncResult result) +15778592   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.End(IAsyncResult result) +15698937   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.ExecuteSynchronous(HttpApplication context, Boolean flowContext) +265   System.ServiceModel.Activation.HttpModule.ProcessRequest(Object sender, EventArgs e) +227   System.Web.SyncEventExecutionStep.System.Web.HttpApplication.IExecutionStep.Execute() +80   System.Web.HttpApplication.ExecuteStep(IExecutionStep step, Boolean& completedSynchronously) +171  
```  
  
 <span data-ttu-id="17952-125">如果您看到此错误，确保已安装并正确配置了用于非 HTTP 激活的 WAS。</span><span class="sxs-lookup"><span data-stu-id="17952-125">If you see this error ensure WAS for Non-HTTP Activation is installed and configured properly.</span></span> <span data-ttu-id="17952-126">有关详细信息，请参阅 [如何：安装和配置 WCF 激活组件](how-to-install-and-configure-wcf-activation-components.md)。</span><span class="sxs-lookup"><span data-stu-id="17952-126">For more information, see [How to: Install and Configure WCF Activation Components](how-to-install-and-configure-wcf-activation-components.md).</span></span>  
  
## <a name="building-a-wcf-service-that-uses-was-for-non-http-activation"></a><span data-ttu-id="17952-127">生成一个将 WAS 用于非 HTTP 激活的 WCF 服务</span><span class="sxs-lookup"><span data-stu-id="17952-127">Building a WCF Service That Uses WAS for Non-HTTP activation</span></span>  

 <span data-ttu-id="17952-128">执行安装和配置 WAS 的步骤后 (参阅 [如何：安装和配置 WCF 激活组件](how-to-install-and-configure-wcf-activation-components.md)) ，将服务配置为使用 WAS 用于激活类似于配置在 IIS 中托管的服务。</span><span class="sxs-lookup"><span data-stu-id="17952-128">Once you perform the steps to install and configure WAS (see [How to: Install and Configure WCF Activation Components](how-to-install-and-configure-wcf-activation-components.md)), configuring a service to use WAS for activation is similar to configuring a service that is hosted in IIS.</span></span>  
  
 <span data-ttu-id="17952-129">有关生成已激活的 WCF 服务的详细说明，请参阅 [如何：在 was 中承载 WCF 服务](how-to-host-a-wcf-service-in-was.md)。</span><span class="sxs-lookup"><span data-stu-id="17952-129">For detailed instructions about building a WAS-activated WCF service, see [How to: Host a WCF Service in WAS](how-to-host-a-wcf-service-in-was.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17952-130">请参阅</span><span class="sxs-lookup"><span data-stu-id="17952-130">See also</span></span>

- [<span data-ttu-id="17952-131">在 Windows 进程激活服务中承载</span><span class="sxs-lookup"><span data-stu-id="17952-131">Hosting in Windows Process Activation Service</span></span>](hosting-in-windows-process-activation-service.md)
- <span data-ttu-id="17952-132">[Windows Server App Fabric 承载功能](/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="17952-132">[Windows Server App Fabric Hosting Features](/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
