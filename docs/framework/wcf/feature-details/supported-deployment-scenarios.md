---
description: 了解有关以下内容的详细信息：支持的部署方案
title: 支持的部署方案
ms.date: 03/30/2017
ms.assetid: 3399f208-3504-4c70-a22e-a7c02a8b94a6
ms.openlocfilehash: 090f0912660fc113bad8640afb1360b64071fa78
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793358"
---
# <a name="supported-deployment-scenarios"></a><span data-ttu-id="43f37-103">支持的部署方案</span><span class="sxs-lookup"><span data-stu-id="43f37-103">Supported deployment scenarios</span></span>

<span data-ttu-id="43f37-104">支持在部分受信任的应用程序中使用 Windows Communication Foundation (WCF) 功能的子集旨在满足使用 WCF 的某些（但不是全部）方案的要求。</span><span class="sxs-lookup"><span data-stu-id="43f37-104">The subset of Windows Communication Foundation (WCF) features supported for use in partially trusted applications is designed to meet the requirements of some, but not all, scenarios for using WCF.</span></span> <span data-ttu-id="43f37-105">在服务器上，WCF 满足 Internet 规模的共享宿主提供程序（出于安全原因，这些提供程序在 ASP.NET 2.0 Medium 信任权限集中运行第三方应用程序）的要求。</span><span class="sxs-lookup"><span data-stu-id="43f37-105">On the server, WCF meets the requirements of Internet-scale shared hosting providers who run third-party applications in the ASP.NET 2.0 Medium Trust permission set for security reasons.</span></span> <span data-ttu-id="43f37-106">在客户端上，WCF 部分信任支持旨在满足部署技术（例如 [ClickOnce 部署](/visualstudio/deployment/clickonce-security-and-deployment) 或 WPF 的 XAML 浏览器应用程序技术）的要求，这允许无缝和安全地从不受信任的站点部署桌面应用程序。</span><span class="sxs-lookup"><span data-stu-id="43f37-106">On the client, WCF partial trust support is designed to meet the requirements of deployment technologies such as [ClickOnce Deployment](/visualstudio/deployment/clickonce-security-and-deployment) or WPF's XAML Browser Application technology, which allow seamless and secure deployment of desktop applications from untrusted sites.</span></span>

## <a name="minimum-permission-requirements"></a><span data-ttu-id="43f37-107">最低权限要求</span><span class="sxs-lookup"><span data-stu-id="43f37-107">Minimum permission requirements</span></span>

<span data-ttu-id="43f37-108">WCF 支持在以下任一标准命名权限集下运行的应用程序中的功能子集：</span><span class="sxs-lookup"><span data-stu-id="43f37-108">WCF supports a subset of features in applications running under either of the following standard named permission sets:</span></span>

- <span data-ttu-id="43f37-109">“中等信任”权限</span><span class="sxs-lookup"><span data-stu-id="43f37-109">Medium Trust permissions</span></span>

- <span data-ttu-id="43f37-110">“Internet 区域”权限</span><span class="sxs-lookup"><span data-stu-id="43f37-110">Internet Zone permissions</span></span>

<span data-ttu-id="43f37-111">如果尝试在部分受信任的应用程序中使用 WCF 并且具有更严格的权限，则可能会在运行时导致安全异常。</span><span class="sxs-lookup"><span data-stu-id="43f37-111">Attempting to use WCF in partially trusted applications with more restrictive permissions may result in security exceptions at runtime.</span></span>

<span data-ttu-id="43f37-112">有关这些权限集支持的功能的详细信息，请参阅 [Partial Trust Feature Compatibility](partial-trust-feature-compatibility.md)。</span><span class="sxs-lookup"><span data-stu-id="43f37-112">For more information about the features supported in these permission sets, see [Partial Trust Feature Compatibility](partial-trust-feature-compatibility.md).</span></span>

## <a name="partial-trust-on-the-server"></a><span data-ttu-id="43f37-113">服务器上的部分信任</span><span class="sxs-lookup"><span data-stu-id="43f37-113">Partial trust on the server</span></span>

<span data-ttu-id="43f37-114">ASP.NET Web 应用程序宿主服务的许多商业提供程序要求在其服务器上运行的应用程序在 ASP.NET 2.0 中等信任权限集中运行。</span><span class="sxs-lookup"><span data-stu-id="43f37-114">Many commercial providers of ASP.NET Web application hosting services mandate that applications running on their servers run in the ASP.NET 2.0 Medium Trust permission set.</span></span> <span data-ttu-id="43f37-115">WCF 服务可以在这些环境中运行，前提是它们将 <xref:System.ServiceModel.BasicHttpBinding> 、 <xref:System.ServiceModel.WebHttpBinding> 或 <xref:System.ServiceModel.WSHttpBinding> 与传输级安全性一起使用。</span><span class="sxs-lookup"><span data-stu-id="43f37-115">WCF services can run in these environments provided they use the <xref:System.ServiceModel.BasicHttpBinding>, the <xref:System.ServiceModel.WebHttpBinding>, or the <xref:System.ServiceModel.WSHttpBinding> with transport-level security.</span></span>

<span data-ttu-id="43f37-116">在中等信任宿主环境中运行的 WCF 服务还可以通过将消息发送到其他服务器以响应客户端请求，充当中间层服务。</span><span class="sxs-lookup"><span data-stu-id="43f37-116">WCF services running in Medium Trust hosting environments can also act as middle-tier services by sending messages to other servers in response to client requests.</span></span> <span data-ttu-id="43f37-117">如果宿主环境已授予应用程序适当的 <xref:System.Net.WebPermission> 以向所需服务器发出出站请求，则支持服务器上的中间层方案。</span><span class="sxs-lookup"><span data-stu-id="43f37-117">Middle-tier scenarios on the server are supported if the hosting environment has granted the application the appropriate <xref:System.Net.WebPermission> to make outbound requests to the desired server.</span></span>

<span data-ttu-id="43f37-118">除了使用支持的 SOAP 绑定之一的 SOAP 消息传递之外，WCF 还支持在 <xref:System.ServiceModel.WebHttpBinding> 部分受信任的应用程序中生成 Web 样式服务。</span><span class="sxs-lookup"><span data-stu-id="43f37-118">In addition to SOAP messaging using one of the supported SOAP bindings, WCF supports the <xref:System.ServiceModel.WebHttpBinding> for building Web-style services in partially trusted applications.</span></span> <span data-ttu-id="43f37-119">在部分信任环境中，wcf [WEB HTTP 编程模型](wcf-web-http-programming-model.md)、 [Wcf 联合](wcf-syndication.md)以及 [AJAX 集成和 JSON 支持](ajax-integration-and-json-support.md) 功能都受支持。</span><span class="sxs-lookup"><span data-stu-id="43f37-119">The [WCF Web HTTP Programming Model](wcf-web-http-programming-model.md), [WCF Syndication](wcf-syndication.md), and [AJAX Integration and JSON Support](ajax-integration-and-json-support.md) features of WCF are all supported in partial trust.</span></span>

<span data-ttu-id="43f37-120">工作流服务需要完全信任权限并且不能在部分受信任的应用程序中使用。</span><span class="sxs-lookup"><span data-stu-id="43f37-120">Workflow Services require Full Trust permissions and cannot be used in partially trusted applications.</span></span>

<span data-ttu-id="43f37-121">有关详细信息，请参阅 [如何：在 ASP.NET 2.0 中使用中等信任](/previous-versions/msp-n-p/ff648344(v=pandp.10))。</span><span class="sxs-lookup"><span data-stu-id="43f37-121">For more information, see [How to: Use Medium Trust in ASP.NET 2.0](/previous-versions/msp-n-p/ff648344(v=pandp.10)).</span></span>

## <a name="partial-trust-on-the-client"></a><span data-ttu-id="43f37-122">客户端上的部分信任</span><span class="sxs-lookup"><span data-stu-id="43f37-122">Partial trust on the client</span></span>

<span data-ttu-id="43f37-123">在从不受信任的 Internet 网站上下载和运行代码时必须采用某些安全预防措施。</span><span class="sxs-lookup"><span data-stu-id="43f37-123">Certain security precautions must be taken when downloading and running code from untrusted Internet sites.</span></span> <span data-ttu-id="43f37-124">[ClickOnce 部署](/visualstudio/deployment/clickonce-security-and-deployment)和 WPF 的 XAML 浏览器应用程序 (XBAP) 技术均使用部分信任， (Internet 区域) 向不受信任的代码授予有限权限。</span><span class="sxs-lookup"><span data-stu-id="43f37-124">Both [ClickOnce Deployment](/visualstudio/deployment/clickonce-security-and-deployment) and WPF's XAML Browser Application (XBAP) technology make use of partial trust to grant limited permissions (Internet Zone) to untrusted code.</span></span>

<span data-ttu-id="43f37-125">WCF 可用于与远程服务器进行通信，这些应用程序由 [ClickOnce 部署](/visualstudio/deployment/clickonce-security-and-deployment) 或 XBAP 部署的部分受信任的应用程序内部。</span><span class="sxs-lookup"><span data-stu-id="43f37-125">WCF can be used to communicate with remote servers from within partially trusted applications deployed by either [ClickOnce Deployment](/visualstudio/deployment/clickonce-security-and-deployment) or XBAP.</span></span> <span data-ttu-id="43f37-126">Internet 区域权限集包括 <xref:System.Net.WebPermission> 发起主机的，此权限允许这些应用程序使用 [部分信任功能兼容性](partial-trust-feature-compatibility.md)中所述的任何受支持的 WCF 绑定来与其源服务器进行通信。</span><span class="sxs-lookup"><span data-stu-id="43f37-126">The Internet Zone permission set includes <xref:System.Net.WebPermission> for the originating host, which allows these applications to communicate with their origin server using any of the supported WCF bindings described in [Partial Trust Feature Compatibility](partial-trust-feature-compatibility.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="43f37-127">请参阅</span><span class="sxs-lookup"><span data-stu-id="43f37-127">See also</span></span>

- [<span data-ttu-id="43f37-128">代码访问安全性</span><span class="sxs-lookup"><span data-stu-id="43f37-128">Code Access Security</span></span>](../../misc/code-access-security.md)
- [<span data-ttu-id="43f37-129">Windows Presentation Foundation 浏览器托管的应用程序概述</span><span class="sxs-lookup"><span data-stu-id="43f37-129">Windows Presentation Foundation Browser-Hosted Applications Overview</span></span>](/dotnet/desktop/wpf/app-development/wpf-xaml-browser-applications-overview)
- [<span data-ttu-id="43f37-130">部分信任</span><span class="sxs-lookup"><span data-stu-id="43f37-130">Partial Trust</span></span>](partial-trust.md)
- <span data-ttu-id="43f37-131">[ASP.NET Trust Levels and Policy Files](/previous-versions/wyts434y(v=vs.140))</span><span class="sxs-lookup"><span data-stu-id="43f37-131">[ASP.NET Trust Levels and Policy Files](/previous-versions/wyts434y(v=vs.140))</span></span>
