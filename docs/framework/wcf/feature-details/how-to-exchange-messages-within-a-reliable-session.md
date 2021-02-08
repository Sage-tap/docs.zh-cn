---
description: 了解详细信息：如何：在可靠会话内交换消息
title: 如何：在可靠会话内交换消息
ms.date: 03/30/2017
ms.assetid: 87cd0e75-dd2c-44c1-8da0-7b494bbdeaea
ms.openlocfilehash: e4a8f6a180b9c2ff9471558997034d02acc817e7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802900"
---
# <a name="how-to-exchange-messages-within-a-reliable-session"></a><span data-ttu-id="01831-103">如何：在可靠会话内交换消息</span><span class="sxs-lookup"><span data-stu-id="01831-103">How to: Exchange Messages Within a Reliable Session</span></span>

<span data-ttu-id="01831-104">本主题概述了使用系统提供的绑定之一来启用可靠会话所需的步骤。这些绑定支持可靠会话，但默认情况下不支持。</span><span class="sxs-lookup"><span data-stu-id="01831-104">This topic outlines the steps required to enable a reliable session using one of the system-provided bindings that support such a session, but not by default.</span></span> <span data-ttu-id="01831-105">可使用代码以强制方式或在配置文件中以声明方式启用可靠会话。</span><span class="sxs-lookup"><span data-stu-id="01831-105">You enable a reliable session imperatively using code or declaratively in your configuration file.</span></span> <span data-ttu-id="01831-106">此过程使用客户端和服务配置文件来启用可靠会话，并规定消息按发送顺序到达的顺序。</span><span class="sxs-lookup"><span data-stu-id="01831-106">This procedure uses the client and service configuration files to enable the reliable session and to stipulate that the messages arrive in the same order in which they were sent.</span></span>

<span data-ttu-id="01831-107">此过程的关键部分是终结点配置元素包含一个 `bindingConfiguration` 属性，该属性引用名为的绑定配置 `Binding1` 。</span><span class="sxs-lookup"><span data-stu-id="01831-107">The key part of this procedure is that the endpoint configuration element contain a `bindingConfiguration` attribute that references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="01831-108">[**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md)配置元素通过将元素的属性设置为来引用此名称以启用可靠会话 `enabled` [**\<reliableSession>**](/previous-versions/dotnet/netframework-4.0/ms731302(v=vs.100)) `true` 。</span><span class="sxs-lookup"><span data-stu-id="01831-108">The [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md) configuration element references this name to enable reliable sessions by setting the `enabled` attribute of the [**\<reliableSession>**](/previous-versions/dotnet/netframework-4.0/ms731302(v=vs.100)) element to `true`.</span></span> <span data-ttu-id="01831-109">通过将 `ordered` 属性设置为 `true`，可为可靠会话指定有序传送保证。</span><span class="sxs-lookup"><span data-stu-id="01831-109">You specify the ordered delivery assurances for the reliable session by setting the `ordered` attribute to `true`.</span></span>

<span data-ttu-id="01831-110">有关此示例的源副本，请参阅 [WS 可靠会话](../samples/ws-reliable-session.md)。</span><span class="sxs-lookup"><span data-stu-id="01831-110">For the source copy of this example, see [WS Reliable Session](../samples/ws-reliable-session.md).</span></span>

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="01831-111">使用 WSHttpBinding 配置服务以使用可靠会话</span><span class="sxs-lookup"><span data-stu-id="01831-111">Configure the service with a WSHttpBinding to use a reliable session</span></span>

1. <span data-ttu-id="01831-112">为该类型的服务定义服务协定。</span><span class="sxs-lookup"><span data-stu-id="01831-112">Define a service contract for the type of service.</span></span>

   [!code-csharp[c_HowTo_UseReliableSession#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1121)]

1. <span data-ttu-id="01831-113">在服务类中实现该服务协定。</span><span class="sxs-lookup"><span data-stu-id="01831-113">Implement the service contract in a service class.</span></span> <span data-ttu-id="01831-114">请注意，在服务的实现内未指定地址或绑定信息。</span><span class="sxs-lookup"><span data-stu-id="01831-114">Note that the address or binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="01831-115">无需编写代码即可从配置文件中检索地址或绑定信息。</span><span class="sxs-lookup"><span data-stu-id="01831-115">You aren't required to write code to retrieve the address or binding information from the configuration file.</span></span>

   [!code-csharp[c_HowTo_UseReliableSession#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1122)]

1. <span data-ttu-id="01831-116">创建一个 *Web.config* 文件，以便为 `CalculatorService` 使用 <xref:System.ServiceModel.WSHttpBinding> 启用了可靠会话并按序传递所需的消息的终结点。</span><span class="sxs-lookup"><span data-stu-id="01831-116">Create a *Web.config* file to configure an endpoint for the `CalculatorService` that uses the <xref:System.ServiceModel.WSHttpBinding> with reliable session enabled and ordered delivery of messages required.</span></span>

   [!code-xml[c_HowTo_UseReliableSession#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/web.config#2111)]

1. <span data-ttu-id="01831-117">创建包含以下行的 *服务 .svc* 文件：</span><span class="sxs-lookup"><span data-stu-id="01831-117">Create a *Service.svc* file that contains the line:</span></span>

   ```aspx-csharp
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1. <span data-ttu-id="01831-118">将 *服务 .svc* 文件放入 INTERNET INFORMATION SERVICES (IIS) 虚拟目录。</span><span class="sxs-lookup"><span data-stu-id="01831-118">Place the *Service.svc* file in your Internet Information Services (IIS) virtual directory.</span></span>

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="01831-119">使用 WSHttpBinding 配置客户端以使用可靠会话</span><span class="sxs-lookup"><span data-stu-id="01831-119">Configure the client with a WSHttpBinding to use a reliable session</span></span>

1. <span data-ttu-id="01831-120">使用 " ("，从命令行 [ *Svcutil.exe*)](../servicemodel-metadata-utility-tool-svcutil-exe.md) ，从服务元数据生成代码：</span><span class="sxs-lookup"><span data-stu-id="01831-120">Use the [ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata:</span></span>

   ```console
   Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. <span data-ttu-id="01831-121">生成的客户端包含 `ICalculator` 定义客户端实现必须满足的服务协定的接口。</span><span class="sxs-lookup"><span data-stu-id="01831-121">The generated client contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1221)]

1. <span data-ttu-id="01831-122">生成的客户端应用程序还包含 `ClientCalculator` 的实现。</span><span class="sxs-lookup"><span data-stu-id="01831-122">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="01831-123">请注意，在服务的实现内部，未指定地址和绑定信息。</span><span class="sxs-lookup"><span data-stu-id="01831-123">Note that the address and binding information isn't specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="01831-124">无需编写代码即可从配置文件中检索地址或绑定信息。</span><span class="sxs-lookup"><span data-stu-id="01831-124">You aren't required to write code to retrieve the address or binding information from the configuration file.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1222)]

1. <span data-ttu-id="01831-125">*Svcutil.exe* 还会生成使用类的客户端的配置 <xref:System.ServiceModel.WSHttpBinding> 。</span><span class="sxs-lookup"><span data-stu-id="01831-125">*Svcutil.exe* also generates the configuration for the client that uses the <xref:System.ServiceModel.WSHttpBinding> class.</span></span> <span data-ttu-id="01831-126">使用 Visual Studio 时，将配置文件命名 *App.config* 。</span><span class="sxs-lookup"><span data-stu-id="01831-126">Name the configuration file *App.config* when using Visual Studio.</span></span>

   [!code-xml[C_HowTo_UseReliableSession#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/app.config#2211)]

1. <span data-ttu-id="01831-127">`ClientCalculator`在应用程序中创建的实例，然后调用服务操作。</span><span class="sxs-lookup"><span data-stu-id="01831-127">Create an instance of the `ClientCalculator` in an application and call the service operations.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1223)]

1. <span data-ttu-id="01831-128">编译并运行客户端。</span><span class="sxs-lookup"><span data-stu-id="01831-128">Compile and run the client.</span></span>

## <a name="example"></a><span data-ttu-id="01831-129">示例</span><span class="sxs-lookup"><span data-stu-id="01831-129">Example</span></span>

<span data-ttu-id="01831-130">默认情况下，有多种系统提供的绑定支持可靠会话。</span><span class="sxs-lookup"><span data-stu-id="01831-130">Several of the system-provided bindings support reliable sessions by default.</span></span> <span data-ttu-id="01831-131">其中包括：</span><span class="sxs-lookup"><span data-stu-id="01831-131">These include:</span></span>

- <xref:System.ServiceModel.WSDualHttpBinding>

- <xref:System.ServiceModel.NetNamedPipeBinding>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>

<span data-ttu-id="01831-132">有关如何创建支持可靠会话的自定义绑定的示例，请参阅 [如何：使用 HTTPS 创建自定义可靠会话绑定](how-to-create-a-custom-reliable-session-binding-with-https.md)。</span><span class="sxs-lookup"><span data-stu-id="01831-132">For an example of how to create a custom binding that supports reliable sessions, see [How to: Create a Custom Reliable Session Binding with HTTPS](how-to-create-a-custom-reliable-session-binding-with-https.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="01831-133">请参阅</span><span class="sxs-lookup"><span data-stu-id="01831-133">See also</span></span>

- [<span data-ttu-id="01831-134">可靠会话</span><span class="sxs-lookup"><span data-stu-id="01831-134">Reliable Sessions</span></span>](reliable-sessions.md)
