---
description: 了解详细信息：如何：将 ASP.NET 授权管理器角色提供程序与服务一起使用
title: 如何：将 ASP.NET 授权管理器角色提供程序与服务一起使用
ms.date: 03/30/2017
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
ms.openlocfilehash: 24d6bbbf2181189104fb0df0068130c402fd2f68
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734121"
---
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a><span data-ttu-id="31955-103">如何：将 ASP.NET 授权管理器角色提供程序与服务一起使用</span><span class="sxs-lookup"><span data-stu-id="31955-103">How to: Use the ASP.NET Authorization Manager Role Provider with a Service</span></span>

<span data-ttu-id="31955-104">当 ASP.NET 托管 Web 服务时，可以将授权管理器集成到应用程序中，以向服务提供授权。</span><span class="sxs-lookup"><span data-stu-id="31955-104">When ASP.NET hosts a Web service, you can integrate Authorization Manager into the application to provide authorization to the service.</span></span> <span data-ttu-id="31955-105">授权管理器允许应用程序开发人员定义各个操作，这些操作可组织在一起形成任务。</span><span class="sxs-lookup"><span data-stu-id="31955-105">Authorization Manager enables an application developer to define individual operations, which can be grouped together to form tasks.</span></span> <span data-ttu-id="31955-106">然后管理员可以授权角色执行特定任务或各个操作。</span><span class="sxs-lookup"><span data-stu-id="31955-106">An administrator can then authorize roles to perform specific tasks or individual operations.</span></span> <span data-ttu-id="31955-107">授权管理器提供管理工具，并将其作为 Microsoft 管理控制台 (MMC) 管理单元来管理角色、任务、操作和用户。</span><span class="sxs-lookup"><span data-stu-id="31955-107">Authorization Manager provides an administration tool as a Microsoft Management Console (MMC) snap-in to manage roles, tasks, operations, and users.</span></span> <span data-ttu-id="31955-108">管理员在 XML 文件、Active Directory 或 Active Directory 应用程序模式 (ADAM) 存储区中配置授权管理器策略存储区。</span><span class="sxs-lookup"><span data-stu-id="31955-108">Administrators configure an Authorization Manager policy store in an XML file, Active Directory, or in an Active Directory Application Mode (ADAM) store.</span></span>  
  
 <span data-ttu-id="31955-109">授权管理器集成到应用程序中，方法是为托管 Web 服务的 ASP.NET 应用程序配置授权管理器 ASP.NET 角色提供程序。</span><span class="sxs-lookup"><span data-stu-id="31955-109">Authorization Manager is Integrated into the application by configuring the Authorization Manager ASP.NET role provider for the ASP.NET application that is hosting the Web service.</span></span> <span data-ttu-id="31955-110">与其他 ASP.NET 角色提供程序一样，授权管理器 ASP.NET 角色提供程序使用 <`providers`> 元素进行配置。</span><span class="sxs-lookup"><span data-stu-id="31955-110">Like other ASP.NET role providers, the Authorization Manager ASP.NET role provider is configured using the <`providers`> element.</span></span>  
  
 <span data-ttu-id="31955-111">下面的代码示例是 Web 服务配置文件的一部分，该 Web 服务将授权管理器集成到应用程序中。</span><span class="sxs-lookup"><span data-stu-id="31955-111">The following code example is a portion of a configuration file for a Web service that is integrating Authorization Manager into the application.</span></span>  
  
```xml  
<system.web>  
    <roleManager enabled="true" defaultProvider="AzManRoleProvider">  
      <providers>  
        <add name="AzManRoleProvider"  
             type="System.Web.Security.AuthorizationStoreRoleProvider, System.Web, Version=2.0.0.0, Culture=neutral, publicKeyToken=b03f5f7f11d50a3a"  
             connectionStringName="AzManPolicyStoreConnectionString"
             applicationName="SecureService"/>  
      </providers>  
    </roleManager>  
</system.web>  
```  
  
 <span data-ttu-id="31955-112">有关将 ASP.NET 角色提供程序与 WCF 应用程序集成的详细信息，请参阅 [如何：将 ASP.NET 角色提供程序用于服务](how-to-use-the-aspnet-role-provider-with-a-service.md)。</span><span class="sxs-lookup"><span data-stu-id="31955-112">For more information about integrating an ASP.NET role provider with a WCF application, see [How to: Use the ASP.NET Role Provider with a Service](how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span> <span data-ttu-id="31955-113">有关将授权管理器与 ASP.NET 配合使用的详细信息，请参阅 [如何：将授权管理器 (AzMan) 与 ASP.NET 2.0 一起](/previous-versions/msp-n-p/ff649313(v=pandp.10))使用。</span><span class="sxs-lookup"><span data-stu-id="31955-113">For more information about using Authorization Manager with ASP.NET, see [How to: Use Authorization Manager (AzMan) with ASP.NET 2.0](/previous-versions/msp-n-p/ff649313(v=pandp.10)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31955-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="31955-114">See also</span></span>

- [<span data-ttu-id="31955-115">如何：将 ASP.NET 角色提供程序与服务一起使用</span><span class="sxs-lookup"><span data-stu-id="31955-115">How to: Use the ASP.NET Role Provider with a Service</span></span>](how-to-use-the-aspnet-role-provider-with-a-service.md)
