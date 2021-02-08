---
description: 了解详细信息：与 COM + 应用程序集成概述
title: 与 COM+ 应用程序集成的概述
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM+ integration
- WCF, COM+ integration
ms.assetid: e481e48f-7096-40eb-9f20-7f0098412941
ms.openlocfilehash: c24ce95651aff222b8374243143afc7166406fcf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802783"
---
# <a name="integrating-with-com-applications-overview"></a><span data-ttu-id="73e9c-103">与 COM+ 应用程序集成的概述</span><span class="sxs-lookup"><span data-stu-id="73e9c-103">Integrating with COM+ Applications Overview</span></span>

<span data-ttu-id="73e9c-104">Windows Communication Foundation (WCF) 提供了一个用于创建分布式应用程序的丰富环境。</span><span class="sxs-lookup"><span data-stu-id="73e9c-104">Windows Communication Foundation (WCF) provides a rich environment for creating distributed applications.</span></span> <span data-ttu-id="73e9c-105">如果已在使用 COM + 中承载的基于组件的应用程序逻辑，则可以使用 WCF 来扩展现有的逻辑，而不必重写它。</span><span class="sxs-lookup"><span data-stu-id="73e9c-105">If you are already using component-based application logic hosted in COM+, you can use WCF to extend your existing logic rather than having to rewrite it.</span></span> <span data-ttu-id="73e9c-106">最常见的情形是通过 Web 服务来公开现有 COM+ 或企业服务业务逻辑。</span><span class="sxs-lookup"><span data-stu-id="73e9c-106">A common scenario is when you want to expose existing COM+ or Enterprise Services business logic through Web Services.</span></span>  
  
 <span data-ttu-id="73e9c-107">在 COM+ 组件上的接口作为 Web 服务公开时，这些服务的规范和协定取决于在应用程序初始化时执行的自动映射。</span><span class="sxs-lookup"><span data-stu-id="73e9c-107">When an interface on a COM+ component is exposed as a Web service, the specification and contract of these services are determined by an automatic mapping that is performed at application initialization time.</span></span> <span data-ttu-id="73e9c-108">下面的列表演示此映射的概念模型：</span><span class="sxs-lookup"><span data-stu-id="73e9c-108">The following list shows the conceptual model for this mapping:</span></span>  
  
- <span data-ttu-id="73e9c-109">为每个公开的 COM 类定义一个服务。</span><span class="sxs-lookup"><span data-stu-id="73e9c-109">One service is defined for each exposed COM class.</span></span>  
  
- <span data-ttu-id="73e9c-110">服务的协定直接派生自选定组件的接口定义，并可能在配置中定义方法排除。</span><span class="sxs-lookup"><span data-stu-id="73e9c-110">The contract for the service is derived directly from the selected component's interface definition with the possibility of method exclusion defined in configuration.</span></span>  
  
- <span data-ttu-id="73e9c-111">该协定中的操作直接派生自组件接口定义中的方法。</span><span class="sxs-lookup"><span data-stu-id="73e9c-111">The operations in that contract are derived directly from the methods on the component's interface definition.</span></span>  
  
- <span data-ttu-id="73e9c-112">这些操作的参数直接派生自与组件的方法参数对应的 COM 互操作性类型。</span><span class="sxs-lookup"><span data-stu-id="73e9c-112">The parameters for those operations are derived directly from the COM interoperability type that corresponds to the component's method parameters.</span></span>  
  
 <span data-ttu-id="73e9c-113">服务的默认地址和传输绑定是在服务配置文件中提供的，但可以根据需要重新配置。</span><span class="sxs-lookup"><span data-stu-id="73e9c-113">Default addresses and transport bindings for the service are provided in a service configuration file, but these can be reconfigured as required.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="73e9c-114">只要 COM+ 接口和配置保持不变，公开的 Web 服务的协定就会保持不变。</span><span class="sxs-lookup"><span data-stu-id="73e9c-114">The contracts for the exposed Web services remain constant as long as the COM+ interfaces and configuration remain unchanged.</span></span> <span data-ttu-id="73e9c-115">如果修改多个接口，将不会自动更新可用服务，并且需要重新运行 COM+ 服务模块配置工具 (ComSvcConfig.exe)。</span><span class="sxs-lookup"><span data-stu-id="73e9c-115">A modification to several interfaces does not automatically update the available services and requires re-running the COM+ Service Model Configuration tool (ComSvcConfig.exe).</span></span>  
  
 <span data-ttu-id="73e9c-116">用作 Web 服务时，会继续强制施加 COM+ 应用程序及其组件的身份验证和授权要求。</span><span class="sxs-lookup"><span data-stu-id="73e9c-116">The authentication and authorization requirements of the COM+ application and its components continue to be enforced when used as a Web service.</span></span>  
  
 <span data-ttu-id="73e9c-117">如果调用方启动 Web 服务事务，则标记为事务性的组件将在该事务范围内登记。</span><span class="sxs-lookup"><span data-stu-id="73e9c-117">If the caller initiates a Web service transaction, components marked as transactional enlist within that transaction scope.</span></span>  
  
 <span data-ttu-id="73e9c-118">在不修改 COM+ 组件的情况下将该组件的接口作为 Web 服务公开时，需要执行下列步骤：</span><span class="sxs-lookup"><span data-stu-id="73e9c-118">The following steps are required to expose a COM+ component's interface as a Web service without modifying the component:</span></span>  
  
1. <span data-ttu-id="73e9c-119">确定是否可将 COM+ 组件的接口作为 Web 服务公开。</span><span class="sxs-lookup"><span data-stu-id="73e9c-119">Determine whether the COM+ component's interface can be exposed as a Web service.</span></span>  
  
2. <span data-ttu-id="73e9c-120">选择相应的宿主模式。</span><span class="sxs-lookup"><span data-stu-id="73e9c-120">Select an appropriate hosting mode.</span></span>  
  
3. <span data-ttu-id="73e9c-121">使用 COM+ 服务模块配置工具 (ComSvcConfig.exe) 为该接口添加 Web 服务。</span><span class="sxs-lookup"><span data-stu-id="73e9c-121">Use the COM+ Service Model Configuration tool (ComSvcConfig.exe) to add a Web service for the interface.</span></span> <span data-ttu-id="73e9c-122">有关如何使用 ComSvcConfig.exe 的详细信息，请参阅 [如何：使用 COM + 服务模型配置工具](how-to-use-the-com-service-model-configuration-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="73e9c-122">For more information about how to use ComSvcConfig.exe, see [How to: Use the COM+ Service Model Configuration Tool](how-to-use-the-com-service-model-configuration-tool.md).</span></span>  
  
4. <span data-ttu-id="73e9c-123">在应用程序配置文件中配置任何其他服务设置。</span><span class="sxs-lookup"><span data-stu-id="73e9c-123">Configure any additional service settings in the application configuration file.</span></span> <span data-ttu-id="73e9c-124">有关如何配置组件的详细信息，请参阅 [如何：配置 COM + 服务设置](how-to-configure-com-service-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="73e9c-124">For more information about how to configure a component, see [How to: Configure COM+ Service Settings](how-to-configure-com-service-settings.md).</span></span>  
  
## <a name="supported-interfaces"></a><span data-ttu-id="73e9c-125">支持的接口</span><span class="sxs-lookup"><span data-stu-id="73e9c-125">Supported Interfaces</span></span>  

 <span data-ttu-id="73e9c-126">对可作为 Web 服务公开的接口的类型有一些限制。</span><span class="sxs-lookup"><span data-stu-id="73e9c-126">There are some restrictions on the type of interfaces that can be exposed as a Web service.</span></span> <span data-ttu-id="73e9c-127">不支持以下类型的接口：</span><span class="sxs-lookup"><span data-stu-id="73e9c-127">The following types of interfaces are not supported:</span></span>  
  
- <span data-ttu-id="73e9c-128">将对象引用作为参数传递的接口 –“受限对象引用支持”一节中介绍了以下受限对象引用方法。</span><span class="sxs-lookup"><span data-stu-id="73e9c-128">Interfaces that pass object references as parameters - the following limited object reference approach is described in the Limited Object Reference Support section.</span></span>  
  
- <span data-ttu-id="73e9c-129">传递与 .NET Framework COM 互操作性转换不兼容的类型的接口。</span><span class="sxs-lookup"><span data-stu-id="73e9c-129">Interfaces that pass types that are not compatible with the .NET Framework COM interoperability conversions.</span></span>  
  
- <span data-ttu-id="73e9c-130">由 COM+ 承载时启用应用程序池的应用程序的接口。</span><span class="sxs-lookup"><span data-stu-id="73e9c-130">Interfaces for applications that have application pooling enabled when hosted by COM+.</span></span>  
  
- <span data-ttu-id="73e9c-131">标记为应用程序专用的组件的接口。</span><span class="sxs-lookup"><span data-stu-id="73e9c-131">Interfaces of components that are marked as private to the application.</span></span>  
  
- <span data-ttu-id="73e9c-132">COM+ 基础结构接口。</span><span class="sxs-lookup"><span data-stu-id="73e9c-132">COM+ infrastructure interfaces.</span></span>  
  
- <span data-ttu-id="73e9c-133">系统应用程序的接口。</span><span class="sxs-lookup"><span data-stu-id="73e9c-133">Interfaces from the system application.</span></span>  
  
- <span data-ttu-id="73e9c-134">尚未添加到全局程序集缓存中的企业服务组件的接口。</span><span class="sxs-lookup"><span data-stu-id="73e9c-134">Interfaces from Enterprise Services components that have not been added to the global assembly cache.</span></span>  
  
### <a name="limited-object-reference-support"></a><span data-ttu-id="73e9c-135">受限对象引用支持</span><span class="sxs-lookup"><span data-stu-id="73e9c-135">Limited Object Reference Support</span></span>  

 <span data-ttu-id="73e9c-136">由于许多已部署的 COM+ 组件需要根据引用参数来使用对象（如返回 ADO Recordset 对象），因此 COM+ 集成为对象引用参数提供了有限支持。</span><span class="sxs-lookup"><span data-stu-id="73e9c-136">Because a number of deployed COM+ components do use objects by reference parameters, such as returning an ADO Recordset object, COM+ integration includes limited support for object reference parameters.</span></span> <span data-ttu-id="73e9c-137">该支持仅限于实现 `IPersistStream` COM 接口的对象。</span><span class="sxs-lookup"><span data-stu-id="73e9c-137">The support is limited to objects that implement the `IPersistStream` COM interface.</span></span> <span data-ttu-id="73e9c-138">其中包括 ADO Recordset 对象，并且可针对应用程序特定的 COM 对象实现。</span><span class="sxs-lookup"><span data-stu-id="73e9c-138">This includes ADO Recordset objects and can be implemented for application specific COM objects.</span></span>  
  
 <span data-ttu-id="73e9c-139">为了实现此支持，ComSvcConfig.exe 工具提供了 **allowreferences** 开关，该开关可禁用常规方法签名参数并检查该工具是否运行以确保不使用对象引用参数。</span><span class="sxs-lookup"><span data-stu-id="73e9c-139">To enable this support, the ComSvcConfig.exe tool provides the **allowreferences** switch that disables the regular method signature parameter and checks that the tool runs to ensure that object reference parameters are not being used.</span></span> <span data-ttu-id="73e9c-140">此外，你作为参数传递的对象类型必须在 <> 配置元素内进行命名和标识， `persistableTypes` 该元素是 <> 元素的子元素 `comContract` 。</span><span class="sxs-lookup"><span data-stu-id="73e9c-140">In addition, the object types that you pass as parameters must be named and identified within the <`persistableTypes`> configuration element that is a child of the <`comContract`> element.</span></span>  
  
 <span data-ttu-id="73e9c-141">使用此功能时，COM+ 集成服务使用 `IPersistStream` 接口来序列化或反序列化对象实例。</span><span class="sxs-lookup"><span data-stu-id="73e9c-141">When this feature is used, the COM+ integration service uses the `IPersistStream` interface to serialize or deserialize the object instance.</span></span> <span data-ttu-id="73e9c-142">如果对象实例不支持 `IPersistStream`，则会引发异常。</span><span class="sxs-lookup"><span data-stu-id="73e9c-142">If the object instance does not support `IPersistStream`, an exception is thrown.</span></span>  
  
 <span data-ttu-id="73e9c-143">在客户端应用程序内，可以使用 <xref:System.ServiceModel.ComIntegration.PersistStreamTypeWrapper> 对象上的方法将对象传入服务，同样也可以用于检索对象。</span><span class="sxs-lookup"><span data-stu-id="73e9c-143">Within a client application, the methods on the <xref:System.ServiceModel.ComIntegration.PersistStreamTypeWrapper> object can be used to pass an object in to a service and similarly to retrieve an object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="73e9c-144">由于序列化方法的自定义和平台特定性质，这最适用于 WCF 客户端和 WCF 服务之间的使用。</span><span class="sxs-lookup"><span data-stu-id="73e9c-144">Due to the custom and platform-specific nature of the serialization approach, this is best suited for use between WCF clients and WCF services.</span></span>  
  
## <a name="selecting-the-hosting-mode"></a><span data-ttu-id="73e9c-145">选择宿主模式</span><span class="sxs-lookup"><span data-stu-id="73e9c-145">Selecting the Hosting Mode</span></span>  

 <span data-ttu-id="73e9c-146">COM+ 可以通过以下宿主模式之一来公开 Web 服务：</span><span class="sxs-lookup"><span data-stu-id="73e9c-146">COM+ exposes Web services in one of the following hosting modes:</span></span>  
  
- <span data-ttu-id="73e9c-147">COM+ 承载</span><span class="sxs-lookup"><span data-stu-id="73e9c-147">COM+-hosted</span></span>  
  
     <span data-ttu-id="73e9c-148">Web 服务承载于应用程序的专用 COM+ 服务器进程 (Dllhost.exe) 中。</span><span class="sxs-lookup"><span data-stu-id="73e9c-148">The Web service is hosted within the application's dedicated COM+ server process (Dllhost.exe).</span></span> <span data-ttu-id="73e9c-149">此模式要求显式启动应用程序才能接收 Web 服务请求。</span><span class="sxs-lookup"><span data-stu-id="73e9c-149">This mode requires the application to be explicitly started before it can receive Web service requests.</span></span> <span data-ttu-id="73e9c-150">可以使用 COM+ 选项“Run as an NT Service”[作为 NT 服务运行]或“Leave running when idle”[空闲时保持运行]来防止在空闲时关闭应用程序及其服务。</span><span class="sxs-lookup"><span data-stu-id="73e9c-150">The COM+ options "Run as an NT Service" or "Leave running when idle" can be used to prevent idle shutdown of the application and its services.</span></span> <span data-ttu-id="73e9c-151">此模式对服务器应用程序同时提供 Web 服务和 DCOM 访问。</span><span class="sxs-lookup"><span data-stu-id="73e9c-151">This mode provides both Web service and DCOM access to the server application.</span></span>  
  
- <span data-ttu-id="73e9c-152">Web 承载</span><span class="sxs-lookup"><span data-stu-id="73e9c-152">Web-hosted</span></span>  
  
     <span data-ttu-id="73e9c-153">Web 服务承载于 Web 服务器工作进程中。</span><span class="sxs-lookup"><span data-stu-id="73e9c-153">The Web service is hosted within a Web server worker process.</span></span> <span data-ttu-id="73e9c-154">此模式不要求 COM+ 在接收初始请求时处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="73e9c-154">This mode does not require COM+ to be active when the initial request is received.</span></span> <span data-ttu-id="73e9c-155">如果在接收该请求时应用程序处于非活动状态，则在处理该请求之前会自动激活它。</span><span class="sxs-lookup"><span data-stu-id="73e9c-155">If the application is not active when this request is received, it is automatically activated prior to processing the request.</span></span> <span data-ttu-id="73e9c-156">此模式也对服务器应用程序同时提供 Web 服务和 DCOM 访问，但会导致 Web 服务请求产生进程跃点。</span><span class="sxs-lookup"><span data-stu-id="73e9c-156">This mode also provides both Web service and DCOM access to the server application, but causes a process hop for Web service requests.</span></span> <span data-ttu-id="73e9c-157">这通常要求客户端启用模拟。</span><span class="sxs-lookup"><span data-stu-id="73e9c-157">This typically requires the client to enable impersonation.</span></span> <span data-ttu-id="73e9c-158">在 WCF 中，可以使用类的属性来完成此操作 <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> <xref:System.ServiceModel.Security.WindowsClientCredential> ，该类可作为泛型类的属性进行访问 <xref:System.ServiceModel.ChannelFactory%601> ，也可用于 <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> 枚举值。</span><span class="sxs-lookup"><span data-stu-id="73e9c-158">In WCF, this can be done with the <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> property of the <xref:System.ServiceModel.Security.WindowsClientCredential> class, which is accessed as a property of the generic <xref:System.ServiceModel.ChannelFactory%601> class, as well as the <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> enumeration value.</span></span>  
  
- <span data-ttu-id="73e9c-159">进程内 Web 承载</span><span class="sxs-lookup"><span data-stu-id="73e9c-159">Web-hosted in-process</span></span>  
  
     <span data-ttu-id="73e9c-160">Web 服务和 COM+ 应用程序逻辑承载于 Web 服务器工作进程中。</span><span class="sxs-lookup"><span data-stu-id="73e9c-160">The Web service and the COM+ application logic are hosted within the Web server worker process.</span></span> <span data-ttu-id="73e9c-161">这样可以自动激活 Web 承载模式，而不会导致 Web 服务请求产生进程跃点。</span><span class="sxs-lookup"><span data-stu-id="73e9c-161">This provides automatic activation of the Web-hosted mode without causing a process hop for Web service requests.</span></span> <span data-ttu-id="73e9c-162">其缺点在于无法通过 DCOM 访问服务器应用程序。</span><span class="sxs-lookup"><span data-stu-id="73e9c-162">The disadvantage is that the server application cannot be accessed through DCOM.</span></span>  
  
### <a name="security-considerations"></a><span data-ttu-id="73e9c-163">安全注意事项</span><span class="sxs-lookup"><span data-stu-id="73e9c-163">Security Considerations</span></span>  

 <span data-ttu-id="73e9c-164">与其他 WCF 服务类似，公开服务的安全设置通过 WCF 通道的配置设置进行管理。</span><span class="sxs-lookup"><span data-stu-id="73e9c-164">Like other WCF services, the security settings for the exposed service are administered through configuration settings for the WCF channel.</span></span> <span data-ttu-id="73e9c-165">不会强制执行传统的 DCOM 安全设置，如 DCOM 计算机范围内的权限设置。</span><span class="sxs-lookup"><span data-stu-id="73e9c-165">Traditional DCOM security settings such as the DCOM machine-wide permissions settings are not enforced.</span></span> <span data-ttu-id="73e9c-166">若要强制执行 COM+ 应用程序角色，必须为组件启用“组件级别访问检查”授权。</span><span class="sxs-lookup"><span data-stu-id="73e9c-166">To enforce COM+ application roles, "component-level access checks" authorization must be enabled for the component.</span></span>  
  
 <span data-ttu-id="73e9c-167">使用非安全绑定可能会致使通信被篡改或信息泄漏。</span><span class="sxs-lookup"><span data-stu-id="73e9c-167">The use of a non-secured binding can leave communication open to tampering or information disclosure.</span></span> <span data-ttu-id="73e9c-168">为防止发生此类情况，建议您使用安全绑定。</span><span class="sxs-lookup"><span data-stu-id="73e9c-168">To prevent this, it is recommended that you use a secured binding.</span></span>  
  
 <span data-ttu-id="73e9c-169">对于 COM+ 承载模式和 Web 承载模式，客户端应用程序必须允许服务器进程模拟客户端用户。</span><span class="sxs-lookup"><span data-stu-id="73e9c-169">For the COM+-hosted and Web-hosted modes, client applications must permit the server process to impersonate the client user.</span></span> <span data-ttu-id="73e9c-170">可以通过将模拟级别设置为来在 WCF 客户端中完成此操作 <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> 。</span><span class="sxs-lookup"><span data-stu-id="73e9c-170">This can be done in WCF clients by setting the impersonation level to <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>.</span></span>  
  
 <span data-ttu-id="73e9c-171">通过 Internet 信息服务 (IIS) 或使用 HTTP 传输的 Windows 进程激活服务 (WAS)，Httpcfg.exe 工具可用于保留传输终结点地址。</span><span class="sxs-lookup"><span data-stu-id="73e9c-171">With Internet Information Services (IIS) or Windows Process Activation Service (WAS) using the HTTP transport, the Httpcfg.exe tool can be used to reserve a transport endpoint address.</span></span> <span data-ttu-id="73e9c-172">在其他配置中，务必防止非法服务充当既定的服务，这一点相当重要。</span><span class="sxs-lookup"><span data-stu-id="73e9c-172">In other configurations, it is important to protect against rogue services that act as the intended service.</span></span> <span data-ttu-id="73e9c-173">若要防止非法服务在所需终结点启动，可以将合法服务配置为作为 NT 服务来运行。</span><span class="sxs-lookup"><span data-stu-id="73e9c-173">To prevent a rogue service from starting at the desired endpoint, the legitimate service can be configured to run as an NT service.</span></span> <span data-ttu-id="73e9c-174">这样，合法服务就可以先于任何非法服务来声明终结点地址。</span><span class="sxs-lookup"><span data-stu-id="73e9c-174">This enables the legitimate service to claim the endpoint address prior to any rogue services.</span></span>  
  
 <span data-ttu-id="73e9c-175">当使用配置的 COM + 角色作为 Web 承载的服务公开 COM + 应用程序时，必须将 "启动 IIS 进程帐户" 添加到该应用程序的其中一个角色。</span><span class="sxs-lookup"><span data-stu-id="73e9c-175">When exposing a COM+ application with configured COM+ roles as a Web-hosted service, the "Launch IIS Process Account" must be added to one of the application’s roles.</span></span> <span data-ttu-id="73e9c-176">必须先添加此帐户（名称通常为 IWAM_machinename）才能在使用之后完全关闭对象。</span><span class="sxs-lookup"><span data-stu-id="73e9c-176">This account, typically with the name IWAM_machinename, must be added to enable clean shutdown of objects after use.</span></span> <span data-ttu-id="73e9c-177">不应授予此帐户任何附加权限。</span><span class="sxs-lookup"><span data-stu-id="73e9c-177">The account should not be granted any additional permissions.</span></span>  
  
 <span data-ttu-id="73e9c-178">COM+ 进程回收功能不能在集成应用程序上使用。</span><span class="sxs-lookup"><span data-stu-id="73e9c-178">The COM+ process recycling features cannot be used on integrated applications.</span></span> <span data-ttu-id="73e9c-179">如果该应用程序配置为使用进程回收功能，并且组件正在 COM+ 承载的进程中运行，则服务将无法启动。</span><span class="sxs-lookup"><span data-stu-id="73e9c-179">If the application is configured to use process recycling and the components are running in a COM+ hosted process, the service fails to start.</span></span> <span data-ttu-id="73e9c-180">此需求不包括使用进程内 Web 承载模式的服务，这是因为没有应用进程回收设置。</span><span class="sxs-lookup"><span data-stu-id="73e9c-180">This requirement does not include services using the Web-hosted in-process mode because the process recycling settings are not applied.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73e9c-181">请参阅</span><span class="sxs-lookup"><span data-stu-id="73e9c-181">See also</span></span>

- [<span data-ttu-id="73e9c-182">COM 应用程序集成概述</span><span class="sxs-lookup"><span data-stu-id="73e9c-182">Integrating with COM Applications Overview</span></span>](integrating-with-com-applications-overview.md)
