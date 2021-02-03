---
title: EShopOnContainers 参考应用简介
description: 介绍适用于 ASP.NET Core 和 Azure 的 eShopOnContainers Cloud 本机微服务 Reference 应用。
ms.date: 01/19/2021
ms.openlocfilehash: 35aa92794d8488c3de60f42af52654c4c26aad82
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2021
ms.locfileid: "99505669"
---
# <a name="introducing-eshoponcontainers-reference-app"></a><span data-ttu-id="1daf4-103">EShopOnContainers 参考应用简介</span><span class="sxs-lookup"><span data-stu-id="1daf4-103">Introducing eShopOnContainers reference app</span></span>

<span data-ttu-id="1daf4-104">Microsoft 与领先社区专家合作，已生成了一个功能完备的云本机微服务参考应用程序 eShopOnContainers。</span><span class="sxs-lookup"><span data-stu-id="1daf4-104">Microsoft, in partnership with leading community experts, has produced a full-featured cloud-native microservices reference application, eShopOnContainers.</span></span> <span data-ttu-id="1daf4-105">构建此应用程序时，可以使用 .NET 和 Docker，还可以选择使用 Azure、Kubernetes 和 Visual Studio 来构建在线店面。</span><span class="sxs-lookup"><span data-stu-id="1daf4-105">This application is built to showcase using .NET and Docker, and optionally Azure, Kubernetes, and Visual Studio, to build an online storefront.</span></span>

![eShopOnContainers 示例应用屏幕快照。](./media/eshoponcontainers-sample-app-screenshot.png)

<span data-ttu-id="1daf4-107">**图 2-1**.</span><span class="sxs-lookup"><span data-stu-id="1daf4-107">**Figure 2-1**.</span></span> <span data-ttu-id="1daf4-108">eShopOnContainers 示例应用屏幕快照。</span><span class="sxs-lookup"><span data-stu-id="1daf4-108">eShopOnContainers Sample App Screenshot.</span></span>

<span data-ttu-id="1daf4-109">在开始本章之前，我们建议下载 [eShopOnContainers 引用应用程序](https://github.com/dotnet-architecture/eShopOnContainers)。</span><span class="sxs-lookup"><span data-stu-id="1daf4-109">Before starting this chapter, we recommend that you download the [eShopOnContainers reference application](https://github.com/dotnet-architecture/eShopOnContainers).</span></span> <span data-ttu-id="1daf4-110">如果执行此操作，则应更轻松地遵循所显示的信息。</span><span class="sxs-lookup"><span data-stu-id="1daf4-110">If you do so, it should be easier for you to follow along with the information presented.</span></span>

## <a name="features-and-requirements"></a><span data-ttu-id="1daf4-111">功能和要求</span><span class="sxs-lookup"><span data-stu-id="1daf4-111">Features and requirements</span></span>

<span data-ttu-id="1daf4-112">让我们先来回顾一下应用程序的功能和要求。</span><span class="sxs-lookup"><span data-stu-id="1daf4-112">Let's start with a review of the application's features and requirements.</span></span> <span data-ttu-id="1daf4-113">EShopOnContainers 应用程序代表了一款在线商店，其中销售各种实物产品，如 t 恤衫和咖啡杯子。</span><span class="sxs-lookup"><span data-stu-id="1daf4-113">The eShopOnContainers application represents an online store that sells various physical products like t-shirts and coffee mugs.</span></span> <span data-ttu-id="1daf4-114">如果你之前已购买过任何内容，则使用该商店的体验应该比较熟悉。</span><span class="sxs-lookup"><span data-stu-id="1daf4-114">If you've bought anything online before, the experience of using the store should be relatively familiar.</span></span> <span data-ttu-id="1daf4-115">下面是应用商店实现的一些基本功能：</span><span class="sxs-lookup"><span data-stu-id="1daf4-115">Here are some of the basic features the store implements:</span></span>

- <span data-ttu-id="1daf4-116">列出目录项</span><span class="sxs-lookup"><span data-stu-id="1daf4-116">List catalog items</span></span>
- <span data-ttu-id="1daf4-117">按类型筛选项目</span><span class="sxs-lookup"><span data-stu-id="1daf4-117">Filter items by type</span></span>
- <span data-ttu-id="1daf4-118">按品牌筛选项目</span><span class="sxs-lookup"><span data-stu-id="1daf4-118">Filter items by brand</span></span>
- <span data-ttu-id="1daf4-119">将商品添加到购物篮</span><span class="sxs-lookup"><span data-stu-id="1daf4-119">Add items to the shopping basket</span></span>
- <span data-ttu-id="1daf4-120">编辑或删除购物篮中的项</span><span class="sxs-lookup"><span data-stu-id="1daf4-120">Edit or remove items from the basket</span></span>
- <span data-ttu-id="1daf4-121">签出</span><span class="sxs-lookup"><span data-stu-id="1daf4-121">Checkout</span></span>
- <span data-ttu-id="1daf4-122">注册帐户</span><span class="sxs-lookup"><span data-stu-id="1daf4-122">Register an account</span></span>
- <span data-ttu-id="1daf4-123">登录</span><span class="sxs-lookup"><span data-stu-id="1daf4-123">Sign in</span></span>
- <span data-ttu-id="1daf4-124">注销</span><span class="sxs-lookup"><span data-stu-id="1daf4-124">Sign out</span></span>
- <span data-ttu-id="1daf4-125">查看订单</span><span class="sxs-lookup"><span data-stu-id="1daf4-125">Review orders</span></span>

<span data-ttu-id="1daf4-126">该应用程序还具有以下非功能性要求：</span><span class="sxs-lookup"><span data-stu-id="1daf4-126">The application also has the following non-functional requirements:</span></span>

- <span data-ttu-id="1daf4-127">它必须具有高可用性，并且必须自动缩放以满足增加的流量 (并在流量下降) 后向下缩放。</span><span class="sxs-lookup"><span data-stu-id="1daf4-127">It needs to be highly available and it must scale automatically to meet increased traffic (and scale back down once traffic subsides).</span></span>
- <span data-ttu-id="1daf4-128">它应该为其运行状况和诊断日志提供易于使用的监视，以帮助解决所遇到的任何问题。</span><span class="sxs-lookup"><span data-stu-id="1daf4-128">It should provide easy-to-use monitoring of its health and diagnostic logs to help troubleshoot any issues it encounters.</span></span>
- <span data-ttu-id="1daf4-129">它应支持 agile 开发过程，其中包括支持持续集成和部署 (CI/CD) 。</span><span class="sxs-lookup"><span data-stu-id="1daf4-129">It should support an agile development process, including support for continuous integration and deployment (CI/CD).</span></span>
- <span data-ttu-id="1daf4-130">除两个 web 前端外 (传统的单页应用程序) ，应用程序还必须支持运行不同种类的操作系统的移动客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="1daf4-130">In addition to the two web front ends (traditional and Single Page Application), the application must also support mobile client apps running different kinds of operating systems.</span></span>
- <span data-ttu-id="1daf4-131">它应该支持跨平台托管和跨平台开发。</span><span class="sxs-lookup"><span data-stu-id="1daf4-131">It should support cross-platform hosting and cross-platform development.</span></span>

![eShopOnContainers 参考应用程序开发体系结构。](./media/eshoponcontainers-development-architecture.png)

<span data-ttu-id="1daf4-133">**图 2-2**。</span><span class="sxs-lookup"><span data-stu-id="1daf4-133">**Figure 2-2**.</span></span> <span data-ttu-id="1daf4-134">eShopOnContainers 参考应用程序开发体系结构。</span><span class="sxs-lookup"><span data-stu-id="1daf4-134">eShopOnContainers reference application development architecture.</span></span>

<span data-ttu-id="1daf4-135">可以从通过 HTTPS 访问应用程序的 web 或移动客户端访问 eShopOnContainers 应用程序，该应用程序针对的是 ASP.NET Core MVC 服务器应用程序或相应的 API 网关。</span><span class="sxs-lookup"><span data-stu-id="1daf4-135">The eShopOnContainers application is accessible from web or mobile clients that access the application over HTTPS targeting either the ASP.NET Core MVC server application or an appropriate API Gateway.</span></span> <span data-ttu-id="1daf4-136">API 网关提供多种优势，例如将后端服务与单个前端客户端分离并提供更好的安全性。</span><span class="sxs-lookup"><span data-stu-id="1daf4-136">API Gateways offer several advantages, such as decoupling back-end services from individual front-end clients and providing better security.</span></span> <span data-ttu-id="1daf4-137">应用程序还使用称为后端的相关模式 (BFF) ，这建议为每个前端客户端创建单独的 API 网关。</span><span class="sxs-lookup"><span data-stu-id="1daf4-137">The application also makes use of a related pattern known as Backends-for-Frontends (BFF), which recommends creating separate API gateways for each front-end client.</span></span> <span data-ttu-id="1daf4-138">参考体系结构演示了如何根据请求是来自 web 客户端还是移动客户端来细分 API 网关。</span><span class="sxs-lookup"><span data-stu-id="1daf4-138">The reference architecture demonstrates breaking up the API gateways based on whether the request is coming from a web or mobile client.</span></span>

<span data-ttu-id="1daf4-139">应用程序的功能分为多个不同的微服务。</span><span class="sxs-lookup"><span data-stu-id="1daf4-139">The application's functionality is broken up into many distinct microservices.</span></span> <span data-ttu-id="1daf4-140">有一些服务负责身份验证和标识、列出产品目录中的项目、管理用户的购物篮和订购订单。</span><span class="sxs-lookup"><span data-stu-id="1daf4-140">There are services responsible for authentication and identity, listing items from the product catalog, managing users' shopping baskets, and  placing orders.</span></span> <span data-ttu-id="1daf4-141">每个单独的服务都有自己的持久存储。</span><span class="sxs-lookup"><span data-stu-id="1daf4-141">Each of these separate services has its own persistent storage.</span></span> <span data-ttu-id="1daf4-142">不存在所有服务都与之进行交互的单个主数据存储。</span><span class="sxs-lookup"><span data-stu-id="1daf4-142">There's no single master data store with which all services interact.</span></span> <span data-ttu-id="1daf4-143">相反，服务之间的协调和通信是按需执行的，而是通过使用消息总线来完成的。</span><span class="sxs-lookup"><span data-stu-id="1daf4-143">Instead, coordination and communication between the services is done on an as-needed basis and by using a message bus.</span></span>

<span data-ttu-id="1daf4-144">每个不同的微服务根据其各自的需求进行了不同的设计。</span><span class="sxs-lookup"><span data-stu-id="1daf4-144">Each of the different microservices is designed differently, based on their individual requirements.</span></span> <span data-ttu-id="1daf4-145">此方面意味着它们的技术堆栈可能会有所不同，不过它们都是使用 .NET 构建的，并且是针对云设计的。</span><span class="sxs-lookup"><span data-stu-id="1daf4-145">This aspect means their technology stack may differ, although they're all built using .NET and designed for the cloud.</span></span> <span data-ttu-id="1daf4-146">更简单的服务提供基本的创建-读取-更新-删除 (CRUD) 对基础数据存储区的访问，而更高级的服务则使用 Domain-Driven 设计方法和模式来管理业务复杂性。</span><span class="sxs-lookup"><span data-stu-id="1daf4-146">Simpler services provide basic Create-Read-Update-Delete (CRUD) access to the underlying data stores, while more advanced services use Domain-Driven Design approaches and patterns to manage business complexity.</span></span>

![不同类型的微服务](./media/different-kinds-of-microservices.png)

<span data-ttu-id="1daf4-148">**图 2-3**。</span><span class="sxs-lookup"><span data-stu-id="1daf4-148">**Figure 2-3**.</span></span> <span data-ttu-id="1daf4-149">不同类型的微服务。</span><span class="sxs-lookup"><span data-stu-id="1daf4-149">Different kinds of microservices.</span></span>

## <a name="overview-of-the-code"></a><span data-ttu-id="1daf4-150">代码概述</span><span class="sxs-lookup"><span data-stu-id="1daf4-150">Overview of the code</span></span>

<span data-ttu-id="1daf4-151">由于它使用微服务，eShopOnContainers 应用在其 GitHub 存储库中包含非常多的单独项目和解决方案。</span><span class="sxs-lookup"><span data-stu-id="1daf4-151">Because it uses microservices, the eShopOnContainers app includes quite a few separate projects and solutions in its GitHub repository.</span></span> <span data-ttu-id="1daf4-152">除了单独的解决方案和可执行文件，各种服务还设计为在本地开发期间和在生产环境中运行时，在其自己的容器中运行。</span><span class="sxs-lookup"><span data-stu-id="1daf4-152">In addition to separate solutions and executable files, the various services are designed to run inside their own containers, both during local development and at runtime in production.</span></span> <span data-ttu-id="1daf4-153">图2-4 显示了完整的 Visual Studio 解决方案，其中组织了各种不同的项目。</span><span class="sxs-lookup"><span data-stu-id="1daf4-153">Figure 2-4 shows the full Visual Studio solution, in which the various different projects are organized.</span></span>

![Visual Studio 解决方案中的项目。](./media/projects-in-visual-studio-solution.png)

<span data-ttu-id="1daf4-155">**图 2-4**。</span><span class="sxs-lookup"><span data-stu-id="1daf4-155">**Figure 2-4**.</span></span> <span data-ttu-id="1daf4-156">Visual Studio 解决方案中的项目。</span><span class="sxs-lookup"><span data-stu-id="1daf4-156">Projects in Visual Studio solution.</span></span>

<span data-ttu-id="1daf4-157">对代码进行组织以支持不同的微服务，并在每个微服务中将代码分解为域逻辑、基础结构问题、用户界面或服务终结点。</span><span class="sxs-lookup"><span data-stu-id="1daf4-157">The code is organized to support the different microservices, and within each microservice, the code is broken up into domain logic, infrastructure concerns, and user interface or service endpoint.</span></span> <span data-ttu-id="1daf4-158">在许多情况下，每个服务的依赖项可由 Azure 服务在生产环境中实现，而备用选项用于本地开发。</span><span class="sxs-lookup"><span data-stu-id="1daf4-158">In many cases, each service's dependencies can be fulfilled by Azure services in production, and alternative options for local development.</span></span> <span data-ttu-id="1daf4-159">让我们看看应用程序的需求如何映射到 Azure 服务。</span><span class="sxs-lookup"><span data-stu-id="1daf4-159">Let's examine how the application's requirements map to Azure services.</span></span>

## <a name="understanding-microservices"></a><span data-ttu-id="1daf4-160">了解微服务</span><span class="sxs-lookup"><span data-stu-id="1daf4-160">Understanding microservices</span></span>

<span data-ttu-id="1daf4-161">本书重点介绍使用 Azure 技术构建的云本机应用程序。</span><span class="sxs-lookup"><span data-stu-id="1daf4-161">This book focuses on cloud-native applications built using Azure technology.</span></span> <span data-ttu-id="1daf4-162">若要详细了解微服务最佳实践和如何构建基于微服务的应用程序，请阅读 [适用于容器化 .Net 应用程序的 .Net 微服务：架构](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)。</span><span class="sxs-lookup"><span data-stu-id="1daf4-162">To learn more about microservices best practices and how to architect microservice-based applications, read the companion book, [.NET Microservices: Architecture for Containerized .NET Applications](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="1daf4-163">[上一页](candidate-apps.md)
>[下一页](map-eshoponcontainers-azure-services.md)</span><span class="sxs-lookup"><span data-stu-id="1daf4-163">[Previous](candidate-apps.md)
[Next](map-eshoponcontainers-azure-services.md)</span></span>
