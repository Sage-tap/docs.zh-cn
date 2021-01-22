---
title: 微服务可寻址性和服务注册表
description: 了解容器映像注册表在微服务体系结构中的角色。
ms.date: 01/13/2021
ms.openlocfilehash: 363a307d44d30125563863bbe3ebeb5f5b9ad2bc
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188408"
---
# <a name="microservices-addressability-and-the-service-registry"></a><span data-ttu-id="b5da4-103">微服务可寻址性和服务注册表</span><span class="sxs-lookup"><span data-stu-id="b5da4-103">Microservices addressability and the service registry</span></span>

<span data-ttu-id="b5da4-104">每个微服务都有一个唯一名称 (URL)，用于解析其位置。</span><span class="sxs-lookup"><span data-stu-id="b5da4-104">Each microservice has a unique name (URL) that's used to resolve its location.</span></span> <span data-ttu-id="b5da4-105">无论微服务在哪里运行，都需是可寻址的。</span><span class="sxs-lookup"><span data-stu-id="b5da4-105">Your microservice needs to be addressable wherever it's running.</span></span> <span data-ttu-id="b5da4-106">如果必须考虑哪一台计算机正在运行某个特定微服务，事情可能很快就不那么好办了。</span><span class="sxs-lookup"><span data-stu-id="b5da4-106">If you have to think about which computer is running a particular microservice, things can go bad quickly.</span></span> <span data-ttu-id="b5da4-107">按照 DNS 解析特定计算机 URL 的相同方式，微服务需要有唯一名称，以便可发现其当前位置。</span><span class="sxs-lookup"><span data-stu-id="b5da4-107">In the same way that DNS resolves a URL to a particular computer, your microservice needs to have a unique name so that its current location is discoverable.</span></span> <span data-ttu-id="b5da4-108">微服务需要可寻址的名称，使其独立于运行于其中的基础结构。</span><span class="sxs-lookup"><span data-stu-id="b5da4-108">Microservices need addressable names that make them independent from the infrastructure that they're running on.</span></span> <span data-ttu-id="b5da4-109">此方法意味着服务部署方式与服务发现方式之间存在交互，因为此处需要一个[服务注册表](https://microservices.io/patterns/service-registry.html)。</span><span class="sxs-lookup"><span data-stu-id="b5da4-109">This approach implies that there's an interaction between how your service is deployed and how it's discovered, because there needs to be a [service registry](https://microservices.io/patterns/service-registry.html).</span></span> <span data-ttu-id="b5da4-110">同样，如果计算机出现故障，注册表服务须能够指出服务的运行位置。</span><span class="sxs-lookup"><span data-stu-id="b5da4-110">In the same vein, when a computer fails, the registry service must be able to indicate where the service is now running.</span></span>

<span data-ttu-id="b5da4-111">[服务注册表模式](https://microservices.io/patterns/service-registry.html)是发现服务的一个关键部分。</span><span class="sxs-lookup"><span data-stu-id="b5da4-111">The [service registry pattern](https://microservices.io/patterns/service-registry.html) is a key part of service discovery.</span></span> <span data-ttu-id="b5da4-112">注册表是包含服务实例的网络位置的数据库。</span><span class="sxs-lookup"><span data-stu-id="b5da4-112">The registry is a database containing the network locations of service instances.</span></span> <span data-ttu-id="b5da4-113">服务注册表需保持高度可用且是最新状态。</span><span class="sxs-lookup"><span data-stu-id="b5da4-113">A service registry needs to be highly available and up-to-date.</span></span> <span data-ttu-id="b5da4-114">客户端可缓存从服务注册表获得的网络位置。</span><span class="sxs-lookup"><span data-stu-id="b5da4-114">Clients could cache network locations obtained from the service registry.</span></span> <span data-ttu-id="b5da4-115">但是，该信息最终也会过时，客户端便无法再发现服务实例。</span><span class="sxs-lookup"><span data-stu-id="b5da4-115">However, that information eventually goes out of date and clients can no longer discover service instances.</span></span> <span data-ttu-id="b5da4-116">因此，服务注册表包含了一个服务器群集，使用复制协议来维护一致性。</span><span class="sxs-lookup"><span data-stu-id="b5da4-116">So, a service registry consists of a cluster of servers that use a replication protocol to maintain consistency.</span></span>

<span data-ttu-id="b5da4-117">在某些微服务部署环境中（称为集群，将在后面章节中介绍），服务发现是内置的。</span><span class="sxs-lookup"><span data-stu-id="b5da4-117">In some microservice deployment environments (called clusters, to be covered in a later section), service discovery is built in.</span></span> <span data-ttu-id="b5da4-118">例如，具有 Kubernetes (AKS) 环境的 Azure 容器服务可以处理服务实例注册和注销。</span><span class="sxs-lookup"><span data-stu-id="b5da4-118">For example, an Azure Container Service with Kubernetes (AKS) environment can handle service instance registration and deregistration.</span></span> <span data-ttu-id="b5da4-119">它还可在每个群集主机（充当服务器端发现路由器角色）上运行一个代理。</span><span class="sxs-lookup"><span data-stu-id="b5da4-119">It also runs a proxy on each cluster host that plays the role of server-side discovery router.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="b5da4-120">其他资源</span><span class="sxs-lookup"><span data-stu-id="b5da4-120">Additional resources</span></span>

- <span data-ttu-id="b5da4-121">**Chris Richardson.模式：Service Registry（服务注册表）**  </span><span class="sxs-lookup"><span data-stu-id="b5da4-121">**Chris Richardson. Pattern: Service registry** </span></span>\
  <https://microservices.io/patterns/service-registry.html>

- <span data-ttu-id="b5da4-122">**Auth0.The Service Registry**（服务注册表） </span><span class="sxs-lookup"><span data-stu-id="b5da4-122">**Auth0. The Service Registry** </span></span>\
  <https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/>

- <span data-ttu-id="b5da4-123">**Gabriel Schenker.Service discovery**（服务发现） </span><span class="sxs-lookup"><span data-stu-id="b5da4-123">**Gabriel Schenker. Service discovery** </span></span>\
  <https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/>

>[!div class="step-by-step"]
><span data-ttu-id="b5da4-124">[上一页](maintain-microservice-apis.md)
>[下一页](microservice-based-composite-ui-shape-layout.md)</span><span class="sxs-lookup"><span data-stu-id="b5da4-124">[Previous](maintain-microservice-apis.md)
[Next](microservice-based-composite-ui-shape-layout.md)</span></span>
