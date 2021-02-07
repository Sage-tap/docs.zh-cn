---
description: 了解详细信息：在工作流解决方案中添加服务引用
title: 在工作流解决方案中添加服务引用
ms.date: 03/30/2017
ms.assetid: 83574cf3-9803-49bc-837f-432936dc9c76
ms.openlocfilehash: ff54235ce2925bd2596bae68333ce98dc7a2f009
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705312"
---
# <a name="add-a-service-reference-in-a-workflow-solution"></a><span data-ttu-id="8bd4a-103">在工作流解决方案中添加服务引用</span><span class="sxs-lookup"><span data-stu-id="8bd4a-103">Add a Service Reference in a Workflow Solution</span></span>

<span data-ttu-id="8bd4a-104">在工作流应用程序中添加服务引用后，其工作方式与常规 WCF 应用程序略有不同。</span><span class="sxs-lookup"><span data-stu-id="8bd4a-104">Adding a service reference in a workflow application works a little differently than a regular WCF application.</span></span> <span data-ttu-id="8bd4a-105">当你选择 "**添加**  >  **服务引用**" 并指定服务的 URL 时，将下载元数据，并生成自定义活动，以允许你调用该 wcf 服务或 wcf 工作流服务。</span><span class="sxs-lookup"><span data-stu-id="8bd4a-105">When you select **Add** > **Service Reference** and specify the URL to the service, the metadata is downloaded and custom activities are generated that allow you to call that WCF service or WCF workflow service.</span></span> <span data-ttu-id="8bd4a-106">添加服务引用后，重新生成解决方案，以便构建生成的活动。</span><span class="sxs-lookup"><span data-stu-id="8bd4a-106">After adding a service reference, rebuild the solution so the generated activities are built.</span></span> <span data-ttu-id="8bd4a-107">之后它们将出现在工作流设计器工具箱中。</span><span class="sxs-lookup"><span data-stu-id="8bd4a-107">They will then appear in the workflow designer toolbox.</span></span> <span data-ttu-id="8bd4a-108">仅当在工作流解决方案中添加服务引用时，此操作才有效。</span><span class="sxs-lookup"><span data-stu-id="8bd4a-108">This will only work if you are adding a service reference within a workflow solution.</span></span> <span data-ttu-id="8bd4a-109">以下 web 转换显示了如何在其他类型的项目中添加服务引用： [从 Web 项目的工作流中调用 WCF 服务](/archive/blogs/endpoint/how-to-consume-a-wcf-service-from-a-wf4-workflow)。</span><span class="sxs-lookup"><span data-stu-id="8bd4a-109">The following web cast shows how to add a service reference in other types of projects: [Calling a WCF Service from a Workflow in a Web Project](/archive/blogs/endpoint/how-to-consume-a-wcf-service-from-a-wf4-workflow).</span></span>

<span data-ttu-id="8bd4a-110">添加对包含相同操作名称的服务的两个或多个服务引用会导致出现问题。</span><span class="sxs-lookup"><span data-stu-id="8bd4a-110">Adding two or more service references to services that contain the same operation name will cause a problem.</span></span> <span data-ttu-id="8bd4a-111">生成的活动将仅调用第一个服务操作。</span><span class="sxs-lookup"><span data-stu-id="8bd4a-111">The generated activities will call only the first service operation.</span></span> <span data-ttu-id="8bd4a-112">若要解决此问题，请重命名服务操作，使其不同，或在每个生成的活动中更改终结点配置名称。</span><span class="sxs-lookup"><span data-stu-id="8bd4a-112">To work around this issue, rename the service operations so they are different, or change the endpoint configuration name within each generated activity.</span></span>

## <a name="see-also"></a><span data-ttu-id="8bd4a-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="8bd4a-113">See also</span></span>

- [<span data-ttu-id="8bd4a-114">工作流服务</span><span class="sxs-lookup"><span data-stu-id="8bd4a-114">Workflow Services</span></span>](workflow-services.md)
- [<span data-ttu-id="8bd4a-115">从 Web 项目的工作流中调用 WCF 服务</span><span class="sxs-lookup"><span data-stu-id="8bd4a-115">Calling a WCF Service from a Workflow in a Web Project</span></span>](/archive/blogs/endpoint/how-to-consume-a-wcf-service-from-a-wf4-workflow)
