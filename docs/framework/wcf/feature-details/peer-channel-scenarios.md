---
description: 详细了解：对等通道方案
title: 对等通道方案
ms.date: 03/30/2017
ms.assetid: dae6e0f7-900c-45ee-8be9-3647698382fb
ms.openlocfilehash: ae21cdb5452864ce3852f2c10892fd082a79fa29
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99733471"
---
# <a name="peer-channel-scenarios"></a><span data-ttu-id="a96ce-103">对等通道方案</span><span class="sxs-lookup"><span data-stu-id="a96ce-103">Peer Channel Scenarios</span></span>

<span data-ttu-id="a96ce-104">对等通道 API 支持下列开发方案。</span><span class="sxs-lookup"><span data-stu-id="a96ce-104">The Peer Channel APIs support the following development scenarios.</span></span>  
  
## <a name="publicationsubscription-messaging"></a><span data-ttu-id="a96ce-105">发布/订阅消息传递</span><span class="sxs-lookup"><span data-stu-id="a96ce-105">Publication/Subscription Messaging</span></span>  

 <span data-ttu-id="a96ce-106">生成发布/订阅应用程序（例如，证券报价程序以及新闻标题、运动成绩和天气预报发布程序）的公司可以使用对等通道来生成无服务器应用程序。</span><span class="sxs-lookup"><span data-stu-id="a96ce-106">Companies that build publication/subscription applications (for example, stock tickers, and publishers of news headlines, sports scores, and weather reports) can use Peer Channel to server-less applications.</span></span> <span data-ttu-id="a96ce-107">例如，用户可以通过加入一个公用网格（客户端组）来获取最新的运动成绩，并在不增加服务器负载的情况下传播大量的最新比赛数据。</span><span class="sxs-lookup"><span data-stu-id="a96ce-107">For example, users can obtain the latest sports scores by joining a common mesh (or group of clients) and propagate the large amount of up-to-date game data without increasing the server load.</span></span> <span data-ttu-id="a96ce-108">这有助于数据提供商提供更高的服务质量，而不会显著增加在基于服务器的技术方面的投资。</span><span class="sxs-lookup"><span data-stu-id="a96ce-108">This helps the data provider to give higher quality of service without substantially increasing the investment in server-based technologies.</span></span>  
  
## <a name="collaboration"></a><span data-ttu-id="a96ce-109">协作</span><span class="sxs-lookup"><span data-stu-id="a96ce-109">Collaboration</span></span>  

 <span data-ttu-id="a96ce-110">使用独立软件供应商 (ISV) 创建的应用程序，用户可以形成紧密协作的团队来参与对等活动。</span><span class="sxs-lookup"><span data-stu-id="a96ce-110">Independent software vendors (ISVs) can create applications that let people create tight groups for participation in peer-to-peer activities.</span></span> <span data-ttu-id="a96ce-111">例如，这可能包括围绕协作项目的团队合作、在朋友之间共享图片、筹备聚会活动等。</span><span class="sxs-lookup"><span data-stu-id="a96ce-111">For example, this can include teams working on collaborative projects, picture-sharing between friends, party-planning activities, and more.</span></span> <span data-ttu-id="a96ce-112">传统上，这些活动总是涉及到服务器；但是，对等通道通过实现脱机访问方案提供了一种以更经济的方式执行这些活动的方法，而这些方案在传统的服务器-客户端模型中不易实现。</span><span class="sxs-lookup"><span data-stu-id="a96ce-112">Traditionally, these activities always involve servers; however, Peer Channel provides a way of doing this in a more cost-efficient way by enabling offline access scenarios that are not as easily implemented under a traditional server-client model.</span></span>  
  
## <a name="distributed-processing-and-compute-clusters"></a><span data-ttu-id="a96ce-113">分布式处理和计算群集</span><span class="sxs-lookup"><span data-stu-id="a96ce-113">Distributed Processing and Compute Clusters</span></span>  

 <span data-ttu-id="a96ce-114">计算群集和分布式处理通常用于大规模计算，如对金融/天气建模和对人类 DNA 的解码。</span><span class="sxs-lookup"><span data-stu-id="a96ce-114">Compute clusters and distributed processing are typically used for large-scale computations, such as financial/weather modeling and decoding human DNA.</span></span> <span data-ttu-id="a96ce-115">这通常是让服务器向参与计算群集的所有客户端逐个分配任务来完成的。</span><span class="sxs-lookup"><span data-stu-id="a96ce-115">Typically, this is done by having servers individually assign tasks to all clients participating in the computation cluster.</span></span> <span data-ttu-id="a96ce-116">这些服务器可能还有额外需求；例如，可能需要在某段持续时间内完成所有任务，这会要求针对每项任务使用多台计算机。</span><span class="sxs-lookup"><span data-stu-id="a96ce-116">These servers may also have additional demands; for example, all tasks may need to be completed within a certain duration, requiring more than one machine for each task.</span></span> <span data-ttu-id="a96ce-117">另外，如果运行某项任务的任何客户端已关闭，则另一个客户端必须能够接管和执行该任务。</span><span class="sxs-lookup"><span data-stu-id="a96ce-117">Additionally, if any client running a task goes down, another client must be able to take over that task and perform work on it.</span></span> <span data-ttu-id="a96ce-118">同样，多个客户端可能必须运行同一项任务才能确保得到一致的结果。</span><span class="sxs-lookup"><span data-stu-id="a96ce-118">Likewise, more than one client may have to run the same task to ensure consistent results.</span></span> <span data-ttu-id="a96ce-119">尽管服务器可以运行这种类型的客户端协调，但是你可以创建一个对等解决方案，以便让接收某项任务的客户端独立确定该任务对服务器的需求，并使用计算网格来确定如何完成该任务。</span><span class="sxs-lookup"><span data-stu-id="a96ce-119">Although servers can run this type of client coordination, you can create a peer-to-peer solution where the clients receiving a task independently determine the server requirements around the task and use a compute mesh to determine how to complete that task.</span></span>  
  
## <a name="gaming"></a><span data-ttu-id="a96ce-120">游戏</span><span class="sxs-lookup"><span data-stu-id="a96ce-120">Gaming</span></span>  

 <span data-ttu-id="a96ce-121">使用对等通道，应用程序开发人员可以创建无服务器版本的游戏，在这样的游戏中，游戏动作可以通过对等机制（而非中央服务器）传输到其他玩家并与他们同步。</span><span class="sxs-lookup"><span data-stu-id="a96ce-121">Using Peer Channel, application developers can create server-less versions of their games where game moves get transmitted to and synchronized with other players by a peer-to-peer mechanism rather than through a central server.</span></span> <span data-ttu-id="a96ce-122">对于小型 ISV，这会帮助其消除与部署、维护和维修中央服务器相关联的运营成本。</span><span class="sxs-lookup"><span data-stu-id="a96ce-122">For small ISVs, this helps remove operational costs associated with deploying, maintaining, and servicing central servers.</span></span> <span data-ttu-id="a96ce-123">可以通过 Internet、有线或无线本地网络来参与使用对等体系结构编写的游戏。</span><span class="sxs-lookup"><span data-stu-id="a96ce-123">Games written using a peer-to-peer architecture can be played across the Internet, or in wired or wireless local networks.</span></span> <span data-ttu-id="a96ce-124">辅助游戏活动（如大厅和游戏中的聊天）可以使用对等网络来开发。</span><span class="sxs-lookup"><span data-stu-id="a96ce-124">Secondary gaming activities, such as lobby and in-game chat can be developed using a peer-to-peer network.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a96ce-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="a96ce-125">See also</span></span>

- [<span data-ttu-id="a96ce-126">对等通道概念</span><span class="sxs-lookup"><span data-stu-id="a96ce-126">Peer Channel Concepts</span></span>](peer-channel-concepts.md)
