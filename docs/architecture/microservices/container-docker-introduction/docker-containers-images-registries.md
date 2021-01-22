---
title: Docker 容器、映像和注册表
description: 适用于容器化 .NET 应用程序的 .NET 微服务体系结构 | Docker 容器、映像和注册表
ms.date: 01/13/2021
ms.openlocfilehash: 0dfde34cd9dab1ef47237746ca6ac2ed75379635
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189364"
---
# <a name="docker-containers-images-and-registries"></a><span data-ttu-id="c65d3-103">Docker 容器、映像和注册表</span><span class="sxs-lookup"><span data-stu-id="c65d3-103">Docker containers, images, and registries</span></span>

<span data-ttu-id="c65d3-104">使用 Docker 时，开发人员会创建一个应用或服务，并将它及其依赖项打包到一个容器映像中。</span><span class="sxs-lookup"><span data-stu-id="c65d3-104">When using Docker, a developer creates an app or service and packages it and its dependencies into a container image.</span></span> <span data-ttu-id="c65d3-105">映像是应用或服务及其配置和依赖项的静态表示形式。</span><span class="sxs-lookup"><span data-stu-id="c65d3-105">An image is a static representation of the app or service and its configuration and dependencies.</span></span>

<span data-ttu-id="c65d3-106">若要运行应用或服务，应用的映像会实例化，以创建一个在 Docker 主机上运行的容器。</span><span class="sxs-lookup"><span data-stu-id="c65d3-106">To run the app or service, the app's image is instantiated to create a container, which will be running on the Docker host.</span></span> <span data-ttu-id="c65d3-107">最初，会在开发环境或 PC 中测试容器。</span><span class="sxs-lookup"><span data-stu-id="c65d3-107">Containers are initially tested in a development environment or PC.</span></span>

<span data-ttu-id="c65d3-108">开发人员应将映像存储在注册表中，该注册表可充当映射库并在部署到生产业务流程协调程序时使用。</span><span class="sxs-lookup"><span data-stu-id="c65d3-108">Developers should store images in a registry, which acts as a library of images and is needed when deploying to production orchestrators.</span></span> <span data-ttu-id="c65d3-109">Docker 通过 [Docker 中心](https://hub.docker.com/)维护公共注册表；其他供应商为不同映像集合提供注册表，包括 [Azure 容器注册表](https://azure.microsoft.com/services/container-registry/)。</span><span class="sxs-lookup"><span data-stu-id="c65d3-109">Docker maintains a public registry via [Docker Hub](https://hub.docker.com/); other vendors provide registries for different collections of images, including [Azure Container Registry](https://azure.microsoft.com/services/container-registry/).</span></span> <span data-ttu-id="c65d3-110">或者，企业可以拥有一个本地专用注册表，用于其 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="c65d3-110">Alternatively, enterprises can have a private registry on-premises for their own Docker images.</span></span>

<span data-ttu-id="c65d3-111">图 2-4 显示了 Docker 中的映像和注册表与其他组件相关联的方式。</span><span class="sxs-lookup"><span data-stu-id="c65d3-111">Figure 2-4 shows how images and registries in Docker relate to other components.</span></span> <span data-ttu-id="c65d3-112">还显示了供应商的多个注册表产品/服务。</span><span class="sxs-lookup"><span data-stu-id="c65d3-112">It also shows the multiple registry offerings from vendors.</span></span>

![显示 Docker 中的基本分类的关系图。](./media/docker-containers-images-registries/taxonomy-of-docker-terms-and-concepts.png)

<span data-ttu-id="c65d3-114">**图 2-4**。</span><span class="sxs-lookup"><span data-stu-id="c65d3-114">**Figure 2-4**.</span></span> <span data-ttu-id="c65d3-115">Docker 术语和概念的分类</span><span class="sxs-lookup"><span data-stu-id="c65d3-115">Taxonomy of Docker terms and concepts</span></span>

<span data-ttu-id="c65d3-116">注册表如同用于存储映像的书架，可被拉取以生成容器，从而运行服务或 Web 应用。</span><span class="sxs-lookup"><span data-stu-id="c65d3-116">The registry is like a bookshelf where images are stored and available to be pulled for building containers to run services or web apps.</span></span> <span data-ttu-id="c65d3-117">本地和公有云上均有专用 Docker 注册表。</span><span class="sxs-lookup"><span data-stu-id="c65d3-117">There are private Docker registries on-premises and on the public cloud.</span></span> <span data-ttu-id="c65d3-118">Docker 中心是由 Docker 维护的公共注册表，除了 Docker 信任的注册表（企业级解决方案），Azure 还提供了 Azure 容器注册表。</span><span class="sxs-lookup"><span data-stu-id="c65d3-118">Docker Hub is a public registry maintained by Docker, along the Docker Trusted Registry an enterprise-grade solution, Azure offers the Azure Container Registry.</span></span> <span data-ttu-id="c65d3-119">AWS、Google 和其他产品也有容器注册表。</span><span class="sxs-lookup"><span data-stu-id="c65d3-119">AWS, Google, and others also have container registries.</span></span>

<span data-ttu-id="c65d3-120">将映射存储到注册表中可存储静态和不可变的应用程序，包括其在框架级别的所有依赖项。</span><span class="sxs-lookup"><span data-stu-id="c65d3-120">Putting images in a registry lets you store static and immutable application bits, including all their dependencies at a framework level.</span></span> <span data-ttu-id="c65d3-121">然后可将这些映像部署到多种环境中，并进行版本控制，从而提供一致的部署单元</span><span class="sxs-lookup"><span data-stu-id="c65d3-121">Those images can then be versioned and deployed in multiple environments and therefore provide a consistent deployment unit.</span></span>

<span data-ttu-id="c65d3-122">无论是托管在本地还是托管在云中，在下列情况下都建议使用私有映像注册表：</span><span class="sxs-lookup"><span data-stu-id="c65d3-122">Private image registries, either hosted on-premises or in the cloud, are recommended when:</span></span>

- <span data-ttu-id="c65d3-123">由于保密性，映像不能被公开分享。</span><span class="sxs-lookup"><span data-stu-id="c65d3-123">Your images must not be shared publicly due to confidentiality.</span></span>

- <span data-ttu-id="c65d3-124">在映像和所选部署环境之间，希望网络延迟保持最低。</span><span class="sxs-lookup"><span data-stu-id="c65d3-124">You want to have minimum network latency between your images and your chosen deployment environment.</span></span> <span data-ttu-id="c65d3-125">例如，如果生产环境是 Azure 云，为实现最低的网络延迟，需要将映像存储在 [Azure 容器注册表](https://azure.microsoft.com/services/container-registry/)中。</span><span class="sxs-lookup"><span data-stu-id="c65d3-125">For example, if your production environment is Azure cloud, you probably want to store your images in [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) so that network latency will be minimal.</span></span> <span data-ttu-id="c65d3-126">同样，如果生产环境是在本地，便需要使本地 Docker 信任的注册表在相同的本地网络中可用。</span><span class="sxs-lookup"><span data-stu-id="c65d3-126">In a similar way, if your production environment is on-premises, you might want to have an on-premises Docker Trusted Registry available within the same local network.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c65d3-127">[上一页](docker-terminology.md)
>[下一页](../net-core-net-framework-containers/index.md)</span><span class="sxs-lookup"><span data-stu-id="c65d3-127">[Previous](docker-terminology.md)
[Next](../net-core-net-framework-containers/index.md)</span></span>
