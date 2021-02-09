---
description: 详细了解：PNRP 云
title: PNRP 云
ms.date: 03/30/2017
ms.assetid: a82e2bf1-62ab-4c2d-83f3-3217a6aead2e
ms.openlocfilehash: 82e9fe85e019d1ef53fa35ed49d55cd2759b4335
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794892"
---
# <a name="pnrp-clouds"></a><span data-ttu-id="df018-103">PNRP 云</span><span class="sxs-lookup"><span data-stu-id="df018-103">PNRP Clouds</span></span>

<span data-ttu-id="df018-104">PNRP“云”表示通过网络相互通信的一组节点。</span><span class="sxs-lookup"><span data-stu-id="df018-104">A PNRP "cloud" represents a set of nodes that can communicate with each other through the network.</span></span> <span data-ttu-id="df018-105">术语“云”与“对等网格”和“对等图”同义。</span><span class="sxs-lookup"><span data-stu-id="df018-105">The term "cloud" is synonymous with "peer mesh" and "peer-to-peer graph".</span></span>  
  
 <span data-ttu-id="df018-106">节点之间的通信绝不能从一个云跨越至另一个云。</span><span class="sxs-lookup"><span data-stu-id="df018-106">Communication between nodes should never cross from one cloud to another.</span></span> <span data-ttu-id="df018-107"><xref:System.Net.PeerToPeer.Cloud> 实例由其名称（区分大小写）唯一标识。</span><span class="sxs-lookup"><span data-stu-id="df018-107">A <xref:System.Net.PeerToPeer.Cloud> instance is uniquely identified by its name, which is case-sensitive.</span></span> <span data-ttu-id="df018-108">单个对等机或节点可以连接到多个云。</span><span class="sxs-lookup"><span data-stu-id="df018-108">A single peer or node may be connected to more than one cloud.</span></span>  
  
 <span data-ttu-id="df018-109">云与网络接口紧密相关。</span><span class="sxs-lookup"><span data-stu-id="df018-109">Clouds are tied very closely to network interfaces.</span></span>  <span data-ttu-id="df018-110">在有两个网卡附加到不同子网的一个多宿主计算机上，将返回三个云：每个接口的每个链接本地地址有一个云，还有一个全局范围云。</span><span class="sxs-lookup"><span data-stu-id="df018-110">On a multi-homed machine with two network cards attached to different subnets, three clouds will be returned: one for each of the link local addresses per interface, and a single global scope cloud.</span></span>  
  
 <span data-ttu-id="df018-111">PNRP 使用三个云“范围”，其中范围指一组可互相找到的计算机：</span><span class="sxs-lookup"><span data-stu-id="df018-111">PNRP uses three cloud "scopes", in which a scope is a grouping of computers that are able to find each other:</span></span>  
  
- <span data-ttu-id="df018-112">全局云对应于全局 IPv6 地址范围和全局地址，表示整个 IPv6 Internet 上的所有计算机。</span><span class="sxs-lookup"><span data-stu-id="df018-112">The global cloud corresponds to the global IPv6 address scope and global addresses and represents all the computers on the entire IPv6 Internet.</span></span> <span data-ttu-id="df018-113">全局云只有一个。</span><span class="sxs-lookup"><span data-stu-id="df018-113">There is only a single global cloud.</span></span>  
  
- <span data-ttu-id="df018-114">链接-本地云对应于链接-本地 IPv6 地址范围和链接-本地地址。</span><span class="sxs-lookup"><span data-stu-id="df018-114">The link-local cloud corresponds to the link-local IPv6 address scope and link-local addresses.</span></span> <span data-ttu-id="df018-115">链接-本地云针对特定链接，通常与本地附加的子网相同。</span><span class="sxs-lookup"><span data-stu-id="df018-115">A link-local cloud is for a specific link, which is typically the same as the locally attached subnet.</span></span> <span data-ttu-id="df018-116">链接-本地云可以有多个。</span><span class="sxs-lookup"><span data-stu-id="df018-116">There can be multiple link-local clouds.</span></span>  
  
 <span data-ttu-id="df018-117">第三种云是站点特定的云，对应于站点 IPv6 地址范围和站点-本地地址。</span><span class="sxs-lookup"><span data-stu-id="df018-117">A third cloud, the site-specific cloud, corresponds to the site IPv6 address scope and site-local addresses.</span></span> <span data-ttu-id="df018-118">这类云已被弃用，尽管它仍受 PNRP 支持。</span><span class="sxs-lookup"><span data-stu-id="df018-118">This cloud has been deprecated, although it is still supported in PNRP.</span></span>  
  
## <a name="clouds"></a><span data-ttu-id="df018-119">云</span><span class="sxs-lookup"><span data-stu-id="df018-119">Clouds</span></span>  

 <span data-ttu-id="df018-120">PNRP 云由 <xref:System.Net.PeerToPeer.Cloud> 类的实例表示。</span><span class="sxs-lookup"><span data-stu-id="df018-120">PNRP clouds are represented by instances of the <xref:System.Net.PeerToPeer.Cloud> class.</span></span> <span data-ttu-id="df018-121">对等机使用的多组云由可枚举的 <xref:System.Net.PeerToPeer.CloudCollection> 类的实例表示。</span><span class="sxs-lookup"><span data-stu-id="df018-121">Groups of clouds used a peer are represented by instances of the enumerable <xref:System.Net.PeerToPeer.CloudCollection> class.</span></span> <span data-ttu-id="df018-122">通过调用静态 <xref:System.Net.PeerToPeer.Cloud.GetAvailableClouds%2A> 方法，可以获取当前对等机已知的 PNRP 云的集合。</span><span class="sxs-lookup"><span data-stu-id="df018-122">Collections of PNRP clouds known to the current peer can be obtained by calling the static <xref:System.Net.PeerToPeer.Cloud.GetAvailableClouds%2A> method.</span></span>  
  
 <span data-ttu-id="df018-123">各个云具有唯一的名称，表示为 256 个字符的 Unicode 字符串。</span><span class="sxs-lookup"><span data-stu-id="df018-123">Individual clouds have unique names, represented as a 256 character Unicode string.</span></span> <span data-ttu-id="df018-124">这些名称以及上面提到的范围共同用于构造 Cloud 类的唯一实例。</span><span class="sxs-lookup"><span data-stu-id="df018-124">These names, along with the above-mentioned scope, are used to construct unique instances of the Cloud class.</span></span> <span data-ttu-id="df018-125">可以将这些实例进行序列化和重新构造，以便永久使用。</span><span class="sxs-lookup"><span data-stu-id="df018-125">These instances can be serialized and reconstructed for persistent usage.</span></span>  
  
 <span data-ttu-id="df018-126">创建或获取 Cloud 实例后，便可为其注册对等名称以创建已知对等网格。</span><span class="sxs-lookup"><span data-stu-id="df018-126">Once a Cloud instance is created or obtained, peer names can be registered with it to create a mesh of known peers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df018-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="df018-127">See also</span></span>

- <xref:System.Net.PeerToPeer.Cloud>
- [<span data-ttu-id="df018-128">对等名称解析协议</span><span class="sxs-lookup"><span data-stu-id="df018-128">Peer Name Resolution Protocol</span></span>](peer-name-resolution-protocol.md)
