---
description: 了解详细信息：可靠会话概述
title: 可靠会话概述
ms.date: 03/30/2017
ms.assetid: a7fc4146-ee2c-444c-82d4-ef6faffccc2d
ms.openlocfilehash: 51de6012245b4fc0a367069d02fe69ee031f2b30
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99632888"
---
# <a name="reliable-sessions-overview"></a><span data-ttu-id="6a4e9-103">可靠会话概述</span><span class="sxs-lookup"><span data-stu-id="6a4e9-103">Reliable Sessions Overview</span></span>

<span data-ttu-id="6a4e9-104">Windows Communication Foundation (WCF) SOAP 可靠消息传递提供 SOAP 终结点之间的端到端消息传输可靠性。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-104">Windows Communication Foundation (WCF) SOAP reliable messaging provides end-to-end message transfer reliability between SOAP endpoints.</span></span> <span data-ttu-id="6a4e9-105">此消息传递通过克服传输失败和 SOAP 消息级别失败，可在不可靠的网络上实现传输可靠性。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-105">It does this on networks that are unreliable by overcoming transport failures and SOAP message-level failures.</span></span> <span data-ttu-id="6a4e9-106">具体而言，它为跨 SOAP 或传输中介发送的消息提供了一种基于会话的、单一的和（可选）有序的传送。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-106">In particular, it provides session-based, single, and (optionally) ordered delivery for messages sent across SOAP or transport intermediaries.</span></span> <span data-ttu-id="6a4e9-107">基于会话的传递可用于将会话中的消息分组，并对消息进行可选排序。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-107">Session-based delivery provides for grouping messages in a session with optional ordering of the messages.</span></span>

<span data-ttu-id="6a4e9-108">本主题介绍可靠会话、使用方法和时间，以及如何对其进行保护。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-108">This topic describes reliable sessions, how and when to use them, and how to secure them.</span></span>

## <a name="wcf-reliable-sessions"></a><span data-ttu-id="6a4e9-109">WCF 可靠会话</span><span class="sxs-lookup"><span data-stu-id="6a4e9-109">WCF reliable sessions</span></span>

<span data-ttu-id="6a4e9-110">WCF 可靠会话是 WS-ReliableMessaging 协议定义的 SOAP 可靠消息的实现。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-110">WCF reliable sessions is an implementation of SOAP reliable messaging as defined by the WS-ReliableMessaging protocol.</span></span>

<span data-ttu-id="6a4e9-111">WCF SOAP 可靠消息传送提供两个终结点之间的端到端可靠会话，而不考虑分隔消息传递终结点的中介的数量或类型。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-111">WCF SOAP reliable messaging provides an end-to-end reliable session between two endpoints, regardless of the number or type of intermediaries that separate the messaging endpoints.</span></span> <span data-ttu-id="6a4e9-112">这包括任何不使用 SOAP (的传输中介（例如，使用 SOAP (的 HTTP 代理) 或中介，例如，在终结点之间传输消息所需的基于 SOAP 的路由器或桥) 。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-112">This includes any transport intermediaries that don't use SOAP (for example, HTTP proxies) or intermediaries that use SOAP (for example, SOAP-based routers or bridges) that are required for messages to flow between the endpoints.</span></span> <span data-ttu-id="6a4e9-113">可靠会话通道支持 *交互式* 通信，因此，由此类通道连接的服务可同时运行，并在低延迟的条件下（即，在相对较短的时间间隔内）交换和处理消息。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-113">A reliable session channel supports *interactive* communication so that the services connected by such a channel run concurrently and exchange and process messages under conditions of low latency, that is, within relatively short intervals of time.</span></span> <span data-ttu-id="6a4e9-114">这种耦合意味着这些组件将进度一起或故障转移，因此它们之间不会提供隔离。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-114">This coupling means that these components make progress together or fail together, so there's no isolation provided between them.</span></span>

<span data-ttu-id="6a4e9-115">可靠会话可以屏蔽两种失败情况：</span><span class="sxs-lookup"><span data-stu-id="6a4e9-115">A reliable session masks two kinds of failures:</span></span>

- <span data-ttu-id="6a4e9-116">SOAP 消息级失败，其中包括消息丢失或重复的情况以及消息到达的顺序与消息发送的顺序不同的情况。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-116">SOAP message-level failures, which includes lost or duplicated messages and messages that arrive in a different order from the order in which they were sent.</span></span>

- <span data-ttu-id="6a4e9-117">传输失败。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-117">Transport failures.</span></span>

<span data-ttu-id="6a4e9-118">可靠会话实现 WS-ReliableMessaging 协议和内存中传输窗口以屏蔽 SOAP 消息级失败，并在传输失败的情况下重新建立连接。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-118">A reliable session implements the WS-ReliableMessaging protocol and an in-memory transfer window to mask SOAP message-level failures and re-establishes connections in the case of transport failures.</span></span>

<span data-ttu-id="6a4e9-119">可靠会话为 SOAP 消息提供 TCP 为 IP 数据包提供的内容。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-119">A reliable session provides for SOAP messages what TCP provides for IP packets.</span></span> <span data-ttu-id="6a4e9-120">TCP 套接字连接在节点之间提供单个的 IP 数据包有序传输。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-120">A TCP socket connection provides a singular, in-order transfer of IP packets between nodes.</span></span> <span data-ttu-id="6a4e9-121">可靠通道提供相同类型的可靠传输，但在以下方面与 TCP 套接字可靠性不同：</span><span class="sxs-lookup"><span data-stu-id="6a4e9-121">The reliable channel provides the same type of reliable transfer, but it differs from TCP socket reliability in the following ways:</span></span>

- <span data-ttu-id="6a4e9-122">可靠性位于 SOAP 消息级别，而不是针对一个任意大小的字节数据包。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-122">The reliability is at the SOAP message level, not for an arbitrarily sized packet of bytes.</span></span>

- <span data-ttu-id="6a4e9-123">可靠性是不特定于传输的，而不仅仅是通过 TCP 传输。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-123">The reliability is transport-neutral, not just for transfer over TCP.</span></span>

- <span data-ttu-id="6a4e9-124">可靠性与特定传输会话无关 (例如，TCP 连接提供) ，可以在可靠会话的生存期内同时或按顺序使用多个传输会话。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-124">The reliability isn't tied to a particular transport session (for example, the session a TCP connection provides) and can use multiple transport sessions concurrently or sequentially over the lifetime of the reliable session.</span></span>

- <span data-ttu-id="6a4e9-125">可靠会话是发送方和接收方的 SOAP 终结点之间的会话，与二者之间的连接所需的传输连接的数目无关。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-125">The reliable session is between the sender and receiver SOAP endpoints, regardless of the number of transport connections required for connectivity between them.</span></span> <span data-ttu-id="6a4e9-126">简而言之，TCP 可靠性结束后传输连接结束，而可靠会话提供端到端的可靠性。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-126">In short, TCP reliability ends where the transport connection ends, while a reliable session provides end-to-end reliability.</span></span>

## <a name="reliable-sessions-and-bindings"></a><span data-ttu-id="6a4e9-127">可靠会话和绑定</span><span class="sxs-lookup"><span data-stu-id="6a4e9-127">Reliable sessions and bindings</span></span>

<span data-ttu-id="6a4e9-128">如前文所述，可靠会话是无特定传输的。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-128">As mentioned earlier, a reliable session is transport neutral.</span></span> <span data-ttu-id="6a4e9-129">此外，还可以通过多种消息交换模式（例如请求-答复或双工）建立可靠会话。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-129">Also, you can establish a reliable session over many message exchange patterns, such as request-reply or duplex.</span></span> <span data-ttu-id="6a4e9-130">WCF 可靠会话公开为一组绑定的属性。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-130">A WCF reliable session is exposed as a property of a set of bindings.</span></span>

<span data-ttu-id="6a4e9-131">在使用以下的终结点上使用可靠会话：</span><span class="sxs-lookup"><span data-stu-id="6a4e9-131">Use a reliable session on endpoints that use:</span></span>

- <span data-ttu-id="6a4e9-132">基于 HTTP 的传输协议标准绑定：</span><span class="sxs-lookup"><span data-stu-id="6a4e9-132">HTTP-based transport standard bindings:</span></span>

  - <span data-ttu-id="6a4e9-133">`WsHttpBinding` 并公开请求-答复或单向协定。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-133">`WsHttpBinding` and expose request-reply or one-way contracts.</span></span>

  - <span data-ttu-id="6a4e9-134">通过请求-答复或简单单向服务约定使用可靠会话时。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-134">When using reliable session over a request-reply or simple one-way service contract.</span></span>

  - <span data-ttu-id="6a4e9-135">`WsDualHttpBinding` 并公开双工、请求-答复或单向协定。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-135">`WsDualHttpBinding` and expose duplex, request-reply, or one-way contracts.</span></span>

  - <span data-ttu-id="6a4e9-136">`WsFederationHttpBinding` 并公开请求-答复或单向协定。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-136">`WsFederationHttpBinding` and expose request-reply or one-way contracts.</span></span>

- <span data-ttu-id="6a4e9-137">基于 TCP 的传输协议标准绑定：</span><span class="sxs-lookup"><span data-stu-id="6a4e9-137">TCP-based transport standard bindings:</span></span>

  - <span data-ttu-id="6a4e9-138">`NetTcpBinding` 并公开双工、请求答复或单向协定。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-138">`NetTcpBinding` and expose duplex, request reply, or one-way contracts.</span></span>

<span data-ttu-id="6a4e9-139">通过创建自定义绑定（如 HTTPS (），在任何其他绑定上使用可靠会话。有关问题的详细信息，请参阅 <a href="#reliable-sessions-and-security">可靠会话和安全</a>) 或命名管道绑定。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-139">Use a reliable session on any other bindings by creating a custom binding, such as HTTPS (for more information about issues, see <a href="#reliable-sessions-and-security">Reliable sessions and security</a>) or a named pipe binding.</span></span>

<span data-ttu-id="6a4e9-140">可以在不同的基础通道类型上堆叠可靠会话，并且生成的可靠会话通道形状会变化。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-140">You can stack a reliable session on different underlying channel types, and the resulting reliable session channel shape varies.</span></span> <span data-ttu-id="6a4e9-141">在客户端和服务器上，受支持的可靠会话通道的类型取决于所使用的基础通道的类型。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-141">On both the client and the server, the type of reliable session channel supported depends on the type of underlying channel used.</span></span> <span data-ttu-id="6a4e9-142">下表列出了在客户端上作为基础通道的一项功能支持的会话通道的类型。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-142">The following table lists the types of session channels supported on the client as a function of the underlying channel type.</span></span>

| <span data-ttu-id="6a4e9-143">支持的可靠会话通道类型&#8224;</span><span class="sxs-lookup"><span data-stu-id="6a4e9-143">Supported reliable session channel types&#8224;</span></span> | `IRequestChannel` | `IRequestSessionChannel` | `IDuplexChannel` | `IDuplexSessionChannel` |
| ----------------------------------------------- | :---------------: | :----------------------: | :--------------: | :---------------------: |
| `IOutputSessionChannel`                         | <span data-ttu-id="6a4e9-144">是</span><span class="sxs-lookup"><span data-stu-id="6a4e9-144">Yes</span></span>               | <span data-ttu-id="6a4e9-145">是</span><span class="sxs-lookup"><span data-stu-id="6a4e9-145">Yes</span></span>                      | <span data-ttu-id="6a4e9-146">是</span><span class="sxs-lookup"><span data-stu-id="6a4e9-146">Yes</span></span>              | <span data-ttu-id="6a4e9-147">是</span><span class="sxs-lookup"><span data-stu-id="6a4e9-147">Yes</span></span>                     |
| `IRequestSessionChannel`                        | <span data-ttu-id="6a4e9-148">是</span><span class="sxs-lookup"><span data-stu-id="6a4e9-148">Yes</span></span>               | <span data-ttu-id="6a4e9-149">是</span><span class="sxs-lookup"><span data-stu-id="6a4e9-149">Yes</span></span>                      | <span data-ttu-id="6a4e9-150">否</span><span class="sxs-lookup"><span data-stu-id="6a4e9-150">No</span></span>               | <span data-ttu-id="6a4e9-151">否</span><span class="sxs-lookup"><span data-stu-id="6a4e9-151">No</span></span>                      |
| `IDuplexSessionChannel`                         | <span data-ttu-id="6a4e9-152">否</span><span class="sxs-lookup"><span data-stu-id="6a4e9-152">No</span></span>                | <span data-ttu-id="6a4e9-153">否</span><span class="sxs-lookup"><span data-stu-id="6a4e9-153">No</span></span>                       | <span data-ttu-id="6a4e9-154">是</span><span class="sxs-lookup"><span data-stu-id="6a4e9-154">Yes</span></span>              | <span data-ttu-id="6a4e9-155">是</span><span class="sxs-lookup"><span data-stu-id="6a4e9-155">Yes</span></span>                     |

<span data-ttu-id="6a4e9-156">&#8224;支持的通道类型是 `TChannel` 传递给方法的泛型参数值可用的值 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelFactory%60%601%28System.ServiceModel.Channels.BindingContext%29> 。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-156">&#8224;The supported channel types are the values available for the generic `TChannel` parameter value that is passed into the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelFactory%60%601%28System.ServiceModel.Channels.BindingContext%29> method.</span></span>

<span data-ttu-id="6a4e9-157">下表列出了在服务器上作为基础通道的一项功能支持的会话通道的类型。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-157">The following table lists the types of session channels supported on the server as a function of the underlying channel type.</span></span>

| <span data-ttu-id="6a4e9-158">支持的可靠会话通道类型&#8225;</span><span class="sxs-lookup"><span data-stu-id="6a4e9-158">Supported reliable session channel types&#8225;</span></span> | `IReplyChannel` | `IReplySessionChannel` | `IDuplexChannel` | `IDuplexSessionChannel` |
| ----------------------------------------------- | :-------------: | :--------------------: | :--------------: | :---------------------: |
| `IInputSessionChannel`                          | <span data-ttu-id="6a4e9-159">是</span><span class="sxs-lookup"><span data-stu-id="6a4e9-159">Yes</span></span>             | <span data-ttu-id="6a4e9-160">是</span><span class="sxs-lookup"><span data-stu-id="6a4e9-160">Yes</span></span>                    | <span data-ttu-id="6a4e9-161">是</span><span class="sxs-lookup"><span data-stu-id="6a4e9-161">Yes</span></span>              | <span data-ttu-id="6a4e9-162">是</span><span class="sxs-lookup"><span data-stu-id="6a4e9-162">Yes</span></span>                     |
| `IReplySessionChannel`                          | <span data-ttu-id="6a4e9-163">是</span><span class="sxs-lookup"><span data-stu-id="6a4e9-163">Yes</span></span>             | <span data-ttu-id="6a4e9-164">是</span><span class="sxs-lookup"><span data-stu-id="6a4e9-164">Yes</span></span>                    | <span data-ttu-id="6a4e9-165">否</span><span class="sxs-lookup"><span data-stu-id="6a4e9-165">No</span></span>               | <span data-ttu-id="6a4e9-166">否</span><span class="sxs-lookup"><span data-stu-id="6a4e9-166">No</span></span>                      |
| `IDuplexSessionChannel`                         | <span data-ttu-id="6a4e9-167">否</span><span class="sxs-lookup"><span data-stu-id="6a4e9-167">No</span></span>              | <span data-ttu-id="6a4e9-168">否</span><span class="sxs-lookup"><span data-stu-id="6a4e9-168">No</span></span>                     | <span data-ttu-id="6a4e9-169">是</span><span class="sxs-lookup"><span data-stu-id="6a4e9-169">Yes</span></span>              | <span data-ttu-id="6a4e9-170">是</span><span class="sxs-lookup"><span data-stu-id="6a4e9-170">Yes</span></span>                     |

<span data-ttu-id="6a4e9-171">&#8225;支持的通道类型是 `TChannel` 传递给方法的泛型参数值可用的值 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelListener%60%601%28System.ServiceModel.Channels.BindingContext%29> 。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-171">&#8225;The supported channel types are the values available for the generic `TChannel` parameter value that is passed into the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelListener%60%601%28System.ServiceModel.Channels.BindingContext%29> method.</span></span>

## <a name="reliable-sessions-and-security"></a><span data-ttu-id="6a4e9-172">可靠会话和安全</span><span class="sxs-lookup"><span data-stu-id="6a4e9-172">Reliable sessions and security</span></span>

<span data-ttu-id="6a4e9-173">保护可靠会话对于确保通信方 (服务和客户端) 进行身份验证，并且会话中交换的消息不会被篡改，这一点非常重要。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-173">Securing a reliable session is important to ensure that the communicating parties (service and client) are authenticated and that the messages exchanged in the session aren't tampered with.</span></span> <span data-ttu-id="6a4e9-174">而且，确保每个可靠会话的完整性是很重要的。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-174">Furthermore, it's important to ensure the integrity of each individual reliable session.</span></span> <span data-ttu-id="6a4e9-175">通过将可靠会话绑定到由安全会话通道表示和管理的安全上下文，可对其进行保护。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-175">A reliable session is secured by binding it to a security context that's represented and managed by a security session channel.</span></span> <span data-ttu-id="6a4e9-176">安全通道提供安全会话。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-176">The security channel provides a security session.</span></span> <span data-ttu-id="6a4e9-177">然后，使用在会话建立的过程中交换的安全令牌保护可靠会话中的消息。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-177">Security tokens exchanged during the session establishment are then used to secure the messages in the reliable session.</span></span>

<span data-ttu-id="6a4e9-178">当可靠会话通过 TCP 时，TCP 会话与可靠会话相关联。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-178">When a reliable session is over TCP-S, the TCP session is tied to the reliable session.</span></span> <span data-ttu-id="6a4e9-179">因此，传输安全机制可确保安全会话与可靠会话相关联。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-179">Therefore, transport security ensures that security is also tied to the reliable session.</span></span> <span data-ttu-id="6a4e9-180">在此情况下，将关闭重新建立连接的操作。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-180">In this case, connection re-establishment is turned off.</span></span>

<span data-ttu-id="6a4e9-181">唯一的例外是在使用 HTTPS 时。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-181">The only exception is when using HTTPS.</span></span> <span data-ttu-id="6a4e9-182"> (SSL) 会话安全套接字层未绑定到可靠会话。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-182">The Secure Sockets Layer (SSL) session isn't bound to the reliable session.</span></span> <span data-ttu-id="6a4e9-183">这会导致威胁，因为在 SSL 会话 (共享安全上下文的会话) 不会受到保护;这可能会也可能不是真正的威胁，具体取决于应用程序。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-183">This imposes a threat because sessions that are sharing a security context (the SSL session) aren't protected from each other; this might or might not be a real threat depending on the application.</span></span>

## <a name="using-reliable-sessions"></a><span data-ttu-id="6a4e9-184">使用可靠会话</span><span class="sxs-lookup"><span data-stu-id="6a4e9-184">Using reliable sessions</span></span>

<span data-ttu-id="6a4e9-185">若要使用 WCF 可靠会话，请使用支持可靠会话的绑定创建一个终结点。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-185">To use WCF reliable sessions, create an endpoint with a binding that supports a reliable session.</span></span> <span data-ttu-id="6a4e9-186">使用启用了可靠会话的 WCF 提供的系统提供的绑定之一，或者创建自己的自定义绑定来执行此项。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-186">Use one of the system-provided bindings that WCF provides with the reliable session enabled or create your own custom binding that does this.</span></span>

<span data-ttu-id="6a4e9-187">默认情况下支持并启用可靠会话的系统定义的绑定包括：</span><span class="sxs-lookup"><span data-stu-id="6a4e9-187">The system-defined bindings that support and enable a reliable session by default include:</span></span>

- <xref:System.ServiceModel.WSDualHttpBinding>

<span data-ttu-id="6a4e9-188">默认情况下，系统提供的绑定支持可靠会话，但默认情况下不启用一个的绑定包括：</span><span class="sxs-lookup"><span data-stu-id="6a4e9-188">The system-provided bindings that support a reliable session as an option but don't enable one by default include:</span></span>

- <xref:System.ServiceModel.WSHttpBinding>

- <xref:System.ServiceModel.WSFederationHttpBinding>

- <xref:System.ServiceModel.NetTcpBinding>

<span data-ttu-id="6a4e9-189">有关如何创建自定义绑定的示例，请参阅 [如何：使用 HTTPS 创建自定义可靠会话绑定](how-to-create-a-custom-reliable-session-binding-with-https.md)。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-189">For an example of how to create a custom binding, see [How to: Create a Custom Reliable Session Binding with HTTPS](how-to-create-a-custom-reliable-session-binding-with-https.md).</span></span>

<span data-ttu-id="6a4e9-190">有关支持可靠会话的 WCF 绑定的讨论，请参阅 [系统提供的绑定](../system-provided-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-190">For a discussion of WCF bindings that support reliable sessions, see [System-Provided Bindings](../system-provided-bindings.md).</span></span>

## <a name="when-to-use-reliable-sessions"></a><span data-ttu-id="6a4e9-191">何时使用可靠会话</span><span class="sxs-lookup"><span data-stu-id="6a4e9-191">When to use reliable sessions</span></span>

<span data-ttu-id="6a4e9-192">了解何时在应用程序中使用可靠会话是很重要的。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-192">It's important to understand when to use reliable sessions in your application.</span></span> <span data-ttu-id="6a4e9-193">WCF 支持同时处于活动状态和活动状态的终结点之间的可靠会话。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-193">WCF supports reliable sessions between endpoints that are active and alive at the same time.</span></span> <span data-ttu-id="6a4e9-194">如果你的应用程序要求其中一个终结点不可用，则使用队列来实现可靠性。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-194">If your application requires one of the endpoints be unavailable for a duration of time, then use queues to achieve reliability.</span></span>

<span data-ttu-id="6a4e9-195">如果方案要求通过 TCP 连接两个终结点，则 TCP 可能足以提供可靠的消息交换。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-195">If the scenario requires two endpoints connected over TCP, then TCP may be sufficient to provide reliable message exchanges.</span></span> <span data-ttu-id="6a4e9-196">尽管不需要使用可靠会话，但由于 TCP 可以确保数据包按顺序到达，而且只会出现一次。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-196">Although, it isn't necessary to use a reliable session, since TCP ensures that the packets arrive in order and only once.</span></span>

<span data-ttu-id="6a4e9-197">如果你的方案具有以下任何特征，则必须认真考虑使用可靠会话。</span><span class="sxs-lookup"><span data-stu-id="6a4e9-197">If your scenario has any of the following characteristics, then you must seriously consider using a reliable session.</span></span>

- <span data-ttu-id="6a4e9-198">SOAP 中介，如 SOAP 路由器</span><span class="sxs-lookup"><span data-stu-id="6a4e9-198">SOAP intermediaries, such as SOAP routers</span></span>

- <span data-ttu-id="6a4e9-199">代理中介或传输桥</span><span class="sxs-lookup"><span data-stu-id="6a4e9-199">Proxy intermediaries or transport bridges</span></span>

- <span data-ttu-id="6a4e9-200">间歇性连接</span><span class="sxs-lookup"><span data-stu-id="6a4e9-200">Intermittent connectivity</span></span>

- <span data-ttu-id="6a4e9-201">HTTP 会话</span><span class="sxs-lookup"><span data-stu-id="6a4e9-201">Sessions over HTTP</span></span>

## <a name="see-also"></a><span data-ttu-id="6a4e9-202">请参阅</span><span class="sxs-lookup"><span data-stu-id="6a4e9-202">See also</span></span>

- [<span data-ttu-id="6a4e9-203">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="6a4e9-203">Using Bindings to Configure Services and Clients</span></span>](../using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="6a4e9-204">WS 可靠会话</span><span class="sxs-lookup"><span data-stu-id="6a4e9-204">WS Reliable Session</span></span>](../samples/ws-reliable-session.md)
