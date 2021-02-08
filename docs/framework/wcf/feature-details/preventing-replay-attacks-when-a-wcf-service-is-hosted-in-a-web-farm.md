---
description: 了解详细信息：在 Web 场中承载 WCF 服务时防止重播攻击
title: 当 Web 场中承载 WCF 服务时防止重放攻击
ms.date: 03/30/2017
ms.assetid: 1c2ed695-7a31-4257-92bd-9e9731b886a5
ms.openlocfilehash: 015059ef650b3ec213c54b89763bac7d46dd218f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793605"
---
# <a name="preventing-replay-attacks-when-a-wcf-service-is-hosted-in-a-web-farm"></a><span data-ttu-id="a532e-103">当 Web 场中承载 WCF 服务时防止重放攻击</span><span class="sxs-lookup"><span data-stu-id="a532e-103">Preventing Replay Attacks When a WCF Service is Hosted in a Web Farm</span></span>

<span data-ttu-id="a532e-104">当使用消息安全性时，WCF 通过从传入的消息创建 NONCE 并检查内部 `InMemoryNonceCache` 以查看是否存在生成的 NONCE，从而防止重播攻击。</span><span class="sxs-lookup"><span data-stu-id="a532e-104">When using message security WCF prevents replay attacks by creating a NONCE out of the incoming message and checking the internal `InMemoryNonceCache` to see if the generated NONCE is present.</span></span> <span data-ttu-id="a532e-105">如果存在，则该消息作为重播被丢弃。</span><span class="sxs-lookup"><span data-stu-id="a532e-105">If it is, the message is discarded as a replay.</span></span> <span data-ttu-id="a532e-106">当 WCF 服务承载在 Web 场中时，因为不跨 Web 场中的节点共享 `InMemoryNonceCache`，所以服务易于受重播攻击。</span><span class="sxs-lookup"><span data-stu-id="a532e-106">When a WCF service is hosted in a web farm, since the `InMemoryNonceCache` is not shared across the nodes in the web farm, the service is vulnerable to replay attacks.</span></span>  <span data-ttu-id="a532e-107">为了缓解这种情况，WCF 4.5 提供了一个可扩展点，使您能够通过从抽象类 <xref:System.ServiceModel.Security.NonceCache> 中派生类来实现您自己的共享 NONCE 缓存。</span><span class="sxs-lookup"><span data-stu-id="a532e-107">To mitigate this scenario WCF 4.5 provides an extensibility point that allows you to implement your own shared NONCE cache by deriving a class from the abstract class <xref:System.ServiceModel.Security.NonceCache>.</span></span>  
  
## <a name="noncecache-implementation"></a><span data-ttu-id="a532e-108">NonceCache 实现</span><span class="sxs-lookup"><span data-stu-id="a532e-108">NonceCache Implementation</span></span>  

 <span data-ttu-id="a532e-109">若要实现您自己的共享 NONCE 缓存，请从 <xref:System.ServiceModel.Security.NonceCache> 派生类并重写 <xref:System.ServiceModel.Security.NonceCache.CheckNonce%2A> 和 <xref:System.ServiceModel.Security.NonceCache.TryAddNonce%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="a532e-109">To implement your own shared NONCE cache, derive a class from <xref:System.ServiceModel.Security.NonceCache> and override the <xref:System.ServiceModel.Security.NonceCache.CheckNonce%2A> and <xref:System.ServiceModel.Security.NonceCache.TryAddNonce%2A> methods.</span></span> <span data-ttu-id="a532e-110"><xref:System.ServiceModel.Security.NonceCache.CheckNonce%2A> 将检查缓存中是否存在指定的 NONCE。</span><span class="sxs-lookup"><span data-stu-id="a532e-110"><xref:System.ServiceModel.Security.NonceCache.CheckNonce%2A> will check to see if the specified NONCE exists in the cache.</span></span> <span data-ttu-id="a532e-111"><xref:System.ServiceModel.Security.NonceCache.TryAddNonce%2A> 将尝试向缓存添加 NONCE。</span><span class="sxs-lookup"><span data-stu-id="a532e-111"><xref:System.ServiceModel.Security.NonceCache.TryAddNonce%2A> will attempt to add a NONCE to the cache.</span></span> <span data-ttu-id="a532e-112">一旦实现类，您就可以通过对实例进行实例化并将其分配给 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.NonceCache%2A> 来进行客户端重播检测，并分配给  <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NonceCache%2A> 以进行服务器端重播检测，从而将其挂钩。</span><span class="sxs-lookup"><span data-stu-id="a532e-112">Once the class is implemented, you hook it up by instantiating an instance and assigning it to <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.NonceCache%2A> for client-side replay detection and <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NonceCache%2A> for server-side replay detection.</span></span> <span data-ttu-id="a532e-113">没有支持此功能的现成配置。</span><span class="sxs-lookup"><span data-stu-id="a532e-113">There is no out of the box configuration support for this feature.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a532e-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="a532e-114">See also</span></span>

- [<span data-ttu-id="a532e-115">消息安全</span><span class="sxs-lookup"><span data-stu-id="a532e-115">Message Security</span></span>](message-security-in-wcf.md)
- [<span data-ttu-id="a532e-116">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="a532e-116">SymmetricSecurityBindingElement</span></span>](../diagnostics/wmi/symmetricsecuritybindingelement.md)
