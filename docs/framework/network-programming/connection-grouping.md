---
description: 详细了解：连接分组
title: 连接分组
ms.date: 03/30/2017
helpviewer_keywords:
- Internet, connections
- connections [.NET Framework], grouping
- WebRequest class, connection grouping
- network resources, connections
- connection pooling
ms.assetid: 2ec502e8-4ba0-4c22-9410-f28eaf4eee63
ms.openlocfilehash: 08e917b555da918ad4386a77938aeb57bc4e4ced
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791564"
---
# <a name="connection-grouping"></a><span data-ttu-id="6a811-103">连接分组</span><span class="sxs-lookup"><span data-stu-id="6a811-103">Connection Grouping</span></span>

<span data-ttu-id="6a811-104">连接分组将单个应用程序内的特定请求与已定义连接池相联系。</span><span class="sxs-lookup"><span data-stu-id="6a811-104">Connection grouping associates specific requests within a single application to a defined connection pool.</span></span> <span data-ttu-id="6a811-105">代表用户连接到后端服务器并使用支持委托的身份验证协议（如 Kerberos）的中间层应用程序，或提供其自身凭据的中间层应用程序可要求连接分组，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="6a811-105">This can be required by a middle-tier application that connects to a back-end server on behalf of a user and uses an authentication protocol that supports delegation, such as Kerberos, or by a middle-tier application that supplies its own credentials, as in the example below.</span></span> <span data-ttu-id="6a811-106">例如，假设用户 Joe 访问显示其工资信息的内部网站。</span><span class="sxs-lookup"><span data-stu-id="6a811-106">For example, suppose a user, Joe, visits an internal Web site that displays his payroll information.</span></span> <span data-ttu-id="6a811-107">对 Joe 进行身份验证之后，中间层应用程序服务器使用 Joe 的凭据连接到后端服务器来检索他的工资信息。</span><span class="sxs-lookup"><span data-stu-id="6a811-107">After authenticating Joe, the middle-tier application server uses Joe's credentials to connect to the back-end server to retrieve his payroll information.</span></span> <span data-ttu-id="6a811-108">接下来 Susan 访问该站点，并请求她的工资信息。</span><span class="sxs-lookup"><span data-stu-id="6a811-108">Next, Susan visits the site and requests her payroll information.</span></span> <span data-ttu-id="6a811-109">因为中间层应用程序已使用 Joe 的凭据完成了连接，所以后端服务器会使用 Joe 的信息进行响应。</span><span class="sxs-lookup"><span data-stu-id="6a811-109">Because the middle-tier application has already made a connection using Joe's credentials, the back-end server responds with Joe's information.</span></span> <span data-ttu-id="6a811-110">但是，如果应用程序将发送到后端服务器的每个请求分配给由用户名形成的连接组，那么每个用户将属于单独的连接池，并且不会意外地与其他用户分享身份验证信息。</span><span class="sxs-lookup"><span data-stu-id="6a811-110">However, if the application assigns each request sent to the back-end server to a connection group formed from the user name, then each user belongs to a separate connection pool and cannot accidentally share authentication information with another user.</span></span>  
  
 <span data-ttu-id="6a811-111">若要将请求分配到特定的连接组，必须在进行请求之前分为 <xref:System.Net.WebRequest> 的 <xref:System.Net.WebRequest.ConnectionGroupName%2A> 属性分配名称。</span><span class="sxs-lookup"><span data-stu-id="6a811-111">To assign a request to a specific connection group, you must assign a name to the <xref:System.Net.WebRequest.ConnectionGroupName%2A> property of your <xref:System.Net.WebRequest> before making the request.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a811-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6a811-112">See also</span></span>

- [<span data-ttu-id="6a811-113">管理连接</span><span class="sxs-lookup"><span data-stu-id="6a811-113">Managing Connections</span></span>](managing-connections.md)
- [<span data-ttu-id="6a811-114">如何：将用户信息分配给组连接</span><span class="sxs-lookup"><span data-stu-id="6a811-114">How to: Assign User Information to Group Connections</span></span>](how-to-assign-user-information-to-group-connections.md)
