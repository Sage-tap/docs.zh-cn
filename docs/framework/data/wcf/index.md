---
title: WCF 数据服务 4.5
description: 了解 WCF Data Services，它是一个 .NET Framework 组件，它支持使用 REST 语义公开和使用数据的服务。
ms.date: 03/30/2017
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
ms.openlocfilehash: 2d3da2ca9cd958fc70d3b91362dde71d68dc9d8a
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/27/2021
ms.locfileid: "98898746"
---
# <a name="wcf-data-services-45"></a><span data-ttu-id="ad385-103">WCF 数据服务 4.5</span><span class="sxs-lookup"><span data-stu-id="ad385-103">WCF Data Services 4.5</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

## <a name="overview"></a><span data-ttu-id="ad385-104">概述</span><span class="sxs-lookup"><span data-stu-id="ad385-104">Overview</span></span>

<span data-ttu-id="ad385-105">WCF Data Services (以前称为 "ADO.NET Data Services" ) 是 .NET Framework 的一个组件，它使你能够通过使用 [具象状态传输 OPEN DATA PROTOCOL REST (](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm)的语义，来创建使用)  (OData) 在 Web 或 intranet 上公开和使用数据的服务。</span><span class="sxs-lookup"><span data-stu-id="ad385-105">WCF Data Services (formerly known as "ADO.NET Data Services") is a component of the .NET Framework that enables you to create services that use the Open Data Protocol (OData) to expose and consume data over the Web or intranet by using the semantics of [representational state transfer (REST)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm).</span></span> <span data-ttu-id="ad385-106">OData 将数据公开为可通过 URI 进行寻址的资源。</span><span class="sxs-lookup"><span data-stu-id="ad385-106">OData exposes data as resources that are addressable by URIs.</span></span> <span data-ttu-id="ad385-107">通过使用标准 HTTP 谓词 GET、PUT、POST 和 DELETE 访问和更改数据。</span><span class="sxs-lookup"><span data-stu-id="ad385-107">Data is accessed and changed by using standard HTTP verbs of GET, PUT, POST, and DELETE.</span></span> <span data-ttu-id="ad385-108">OData 使用 [实体数据模型](../adonet/entity-data-model.md) 的实体关系约定将资源公开为通过关联相关的实体集。</span><span class="sxs-lookup"><span data-stu-id="ad385-108">OData uses the entity-relationship conventions of the [Entity Data Model](../adonet/entity-data-model.md) to expose resources as sets of entities that are related by associations.</span></span>

<span data-ttu-id="ad385-109">WCF Data Services 使用 OData 协议对资源进行寻址和更新。</span><span class="sxs-lookup"><span data-stu-id="ad385-109">WCF Data Services uses the OData protocol for addressing and updating resources.</span></span> <span data-ttu-id="ad385-110">通过这种方式，你可以从支持 OData 的任何客户端访问这些服务。</span><span class="sxs-lookup"><span data-stu-id="ad385-110">In this way, you can access these services from any client that supports OData.</span></span> <span data-ttu-id="ad385-111">OData 使你可以通过使用众所周知的传输格式请求数据并将数据写入资源： Atom，一组用于以 XML 格式交换和更新数据的标准，并 JavaScript 对象表示法 (JSON) ，这是在 AJAX 应用程序中广泛使用的基于文本的数据交换格式。</span><span class="sxs-lookup"><span data-stu-id="ad385-111">OData enables you to request and write data to resources by using well-known transfer formats: Atom, a set of standards for exchanging and updating data as XML, and JavaScript Object Notation (JSON), a text-based data exchange format used extensively in AJAX applications.</span></span>

<span data-ttu-id="ad385-112">WCF Data Services 可以将源自各种源的数据作为 OData 源公开。</span><span class="sxs-lookup"><span data-stu-id="ad385-112">WCF Data Services can expose data that originates from various sources as OData feeds.</span></span> <span data-ttu-id="ad385-113">Visual Studio 工具通过使用 ADO.NET 实体框架数据模型，使你可以更轻松地创建基于 OData 的服务。</span><span class="sxs-lookup"><span data-stu-id="ad385-113">Visual Studio tools make it easier for you to create an OData-based service by using an ADO.NET Entity Framework data model.</span></span> <span data-ttu-id="ad385-114">还可以基于公共语言运行时 (CLR) 类，甚至是后期绑定或未类型化的数据来创建 OData 源。</span><span class="sxs-lookup"><span data-stu-id="ad385-114">You can also create OData feeds based on common language runtime (CLR) classes and even late-bound or un-typed data.</span></span>

<span data-ttu-id="ad385-115">WCF Data Services 还包括一组客户端库，一个用于一般 .NET Framework 客户端应用程序，另一个专用于基于 Silverlight 的应用程序。</span><span class="sxs-lookup"><span data-stu-id="ad385-115">WCF Data Services also includes a set of client libraries, one for general .NET Framework client applications and another specifically for Silverlight-based applications.</span></span> <span data-ttu-id="ad385-116">在从 .NET Framework 和 Silverlight 之类的环境访问 OData 源时，这些客户端库提供了基于对象的编程模型。</span><span class="sxs-lookup"><span data-stu-id="ad385-116">These client libraries provide an object-based programming model when you access an OData feed from environments such as the .NET Framework and Silverlight.</span></span>

## <a name="where-should-i-start"></a><span data-ttu-id="ad385-117">从何处开始？</span><span class="sxs-lookup"><span data-stu-id="ad385-117">Where Should I Start?</span></span>

<span data-ttu-id="ad385-118">根据你的兴趣，请考虑以下主题之一中的 WCF Data Services 入门。</span><span class="sxs-lookup"><span data-stu-id="ad385-118">Depending on your interests, consider getting started with WCF Data Services in one of the following topics.</span></span>

<span data-ttu-id="ad385-119">我希望直接开始使用...</span><span class="sxs-lookup"><span data-stu-id="ad385-119">I want to jump right in...</span></span>

- [<span data-ttu-id="ad385-120">快速入门</span><span class="sxs-lookup"><span data-stu-id="ad385-120">Quickstart</span></span>](quickstart-wcf-data-services.md)

- [<span data-ttu-id="ad385-121">入门</span><span class="sxs-lookup"><span data-stu-id="ad385-121">Getting Started</span></span>](getting-started-with-wcf-data-services.md)

<span data-ttu-id="ad385-122">只显示一些代码 .。。</span><span class="sxs-lookup"><span data-stu-id="ad385-122">Just show me some code...</span></span>

- [<span data-ttu-id="ad385-123">快速入门</span><span class="sxs-lookup"><span data-stu-id="ad385-123">Quickstart</span></span>](quickstart-wcf-data-services.md)

- [<span data-ttu-id="ad385-124">如何：执行数据服务查询</span><span class="sxs-lookup"><span data-stu-id="ad385-124">How to: Execute Data Service Queries</span></span>](how-to-execute-data-service-queries-wcf-data-services.md)

- [<span data-ttu-id="ad385-125">如何：将数据绑定到 Windows Presentation Foundation 元素</span><span class="sxs-lookup"><span data-stu-id="ad385-125">How to: Bind Data to Windows Presentation Foundation Elements</span></span>](bind-data-to-wpf-elements-wcf-data-services.md)

<span data-ttu-id="ad385-126">我想了解有关 OData 的详细信息 .。。</span><span class="sxs-lookup"><span data-stu-id="ad385-126">I want to know more about OData...</span></span>

- [<span data-ttu-id="ad385-127">白皮书： OData 简介</span><span class="sxs-lookup"><span data-stu-id="ad385-127">White paper: Introducing OData</span></span>](https://download.microsoft.com/download/E/5/A/E5A59052-EE48-4D64-897B-5F7C608165B8/IntroducingOData.pdf)
- [<span data-ttu-id="ad385-128">Open Data Protocol 网站</span><span class="sxs-lookup"><span data-stu-id="ad385-128">Open Data Protocol website</span></span>](https://www.odata.org/)
- [<span data-ttu-id="ad385-129">OData：SDK</span><span class="sxs-lookup"><span data-stu-id="ad385-129">OData: SDK</span></span>](https://www.odata.org/ecosystem/)

<span data-ttu-id="ad385-130">我想要查看端到端示例 .。。</span><span class="sxs-lookup"><span data-stu-id="ad385-130">I want to see end-to-end samples...</span></span>

- <span data-ttu-id="ad385-131">[WCF Data Services 快速入门](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client))</span><span class="sxs-lookup"><span data-stu-id="ad385-131">[WCF Data Services Quickstart](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client))</span></span>
- [<span data-ttu-id="ad385-132">OData SDK-示例代码</span><span class="sxs-lookup"><span data-stu-id="ad385-132">OData SDK - Sample Code</span></span>](https://www.odata.org/ecosystem/#sdk)

<span data-ttu-id="ad385-133">它如何与 Visual Studio 集成？</span><span class="sxs-lookup"><span data-stu-id="ad385-133">How does it integrate with Visual Studio?</span></span>

- [<span data-ttu-id="ad385-134">生成数据服务客户端库</span><span class="sxs-lookup"><span data-stu-id="ad385-134">Generating the Data Service Client Library</span></span>](generating-the-data-service-client-library-wcf-data-services.md)

- [<span data-ttu-id="ad385-135">创建数据服务</span><span class="sxs-lookup"><span data-stu-id="ad385-135">Creating the Data Service</span></span>](creating-the-data-service.md)

- [<span data-ttu-id="ad385-136">实体框架提供程序</span><span class="sxs-lookup"><span data-stu-id="ad385-136">Entity Framework Provider</span></span>](entity-framework-provider-wcf-data-services.md)

<span data-ttu-id="ad385-137">它的作用是什么？</span><span class="sxs-lookup"><span data-stu-id="ad385-137">What can I do with it?</span></span>

- <span data-ttu-id="ad385-138">概述</span><span class="sxs-lookup"><span data-stu-id="ad385-138">[Overview](wcf-data-services-overview.md)</span></span>

- [<span data-ttu-id="ad385-139">应用程序方案</span><span class="sxs-lookup"><span data-stu-id="ad385-139">Application Scenarios</span></span>](application-scenarios-wcf-data-services.md)

<span data-ttu-id="ad385-140">我想要使用 LINQ .。。</span><span class="sxs-lookup"><span data-stu-id="ad385-140">I want to use LINQ...</span></span>

- [<span data-ttu-id="ad385-141">查询数据服务</span><span class="sxs-lookup"><span data-stu-id="ad385-141">Querying the Data Service</span></span>](querying-the-data-service-wcf-data-services.md)

- [<span data-ttu-id="ad385-142">LINQ 注意事项</span><span class="sxs-lookup"><span data-stu-id="ad385-142">LINQ Considerations</span></span>](linq-considerations-wcf-data-services.md)

- [<span data-ttu-id="ad385-143">如何：执行数据服务查询</span><span class="sxs-lookup"><span data-stu-id="ad385-143">How to: Execute Data Service Queries</span></span>](how-to-execute-data-service-queries-wcf-data-services.md)

<span data-ttu-id="ad385-144">我仍然需要了解更多信息 .。。</span><span class="sxs-lookup"><span data-stu-id="ad385-144">I still need some more information...</span></span>

- <span data-ttu-id="ad385-145">[WCF Data Services Team Blog](/archive/blogs/astoriateam/)（WCF Data Services 团队博客）</span><span class="sxs-lookup"><span data-stu-id="ad385-145">[WCF Data Services Team Blog](/archive/blogs/astoriateam/)</span></span>

- [<span data-ttu-id="ad385-146">资源</span><span class="sxs-lookup"><span data-stu-id="ad385-146">Resources</span></span>](wcf-data-services-resources.md)

## <a name="in-this-section"></a><span data-ttu-id="ad385-147">本节内容</span><span class="sxs-lookup"><span data-stu-id="ad385-147">In This Section</span></span>

<span data-ttu-id="ad385-148">概述</span><span class="sxs-lookup"><span data-stu-id="ad385-148">[Overview](wcf-data-services-overview.md)</span></span>

<span data-ttu-id="ad385-149">概述 WCF Data Services 中可用的特性和功能。</span><span class="sxs-lookup"><span data-stu-id="ad385-149">Provides an overview of the features and functionality available in WCF Data Services.</span></span>

<span data-ttu-id="ad385-150">[WCF Data Services 5.0 的新增功能](/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))</span><span class="sxs-lookup"><span data-stu-id="ad385-150">[What's New in WCF Data Services 5.0](/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))</span></span>

<span data-ttu-id="ad385-151">介绍 WCF Data Services 的新功能，并支持新的 OData 功能。</span><span class="sxs-lookup"><span data-stu-id="ad385-151">Describes new functionality in WCF Data Services and support for new OData features.</span></span>

[<span data-ttu-id="ad385-152">入门</span><span class="sxs-lookup"><span data-stu-id="ad385-152">Getting Started</span></span>](getting-started-with-wcf-data-services.md)

<span data-ttu-id="ad385-153">介绍如何使用 WCF Data Services 公开和使用 OData 源。</span><span class="sxs-lookup"><span data-stu-id="ad385-153">Describes how to expose and consume OData feeds by using WCF Data Services.</span></span>

[<span data-ttu-id="ad385-154">定义 WCF 数据服务</span><span class="sxs-lookup"><span data-stu-id="ad385-154">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)

<span data-ttu-id="ad385-155">介绍如何创建和配置公开 OData 源的数据服务。</span><span class="sxs-lookup"><span data-stu-id="ad385-155">Describes how to create and configure a data service that exposes OData feeds.</span></span>

[<span data-ttu-id="ad385-156">WCF 数据服务客户端库</span><span class="sxs-lookup"><span data-stu-id="ad385-156">WCF Data Services Client Library</span></span>](wcf-data-services-client-library.md)

<span data-ttu-id="ad385-157">介绍如何使用客户端库从 .NET Framework 客户端应用程序中使用 OData 源。</span><span class="sxs-lookup"><span data-stu-id="ad385-157">Describes how to use client libraries to consume OData feeds from a .NET Framework client application.</span></span>

## <a name="see-also"></a><span data-ttu-id="ad385-158">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ad385-158">See also</span></span>

- <span data-ttu-id="ad385-159">[Representational State Transfer (REST)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm)（表述性状态转移 (REST)）</span><span class="sxs-lookup"><span data-stu-id="ad385-159">[Representational State Transfer (REST)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm)</span></span>
