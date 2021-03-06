---
title: 将中间件与模块和处理程序进行比较
description: 本部分探讨了在为其请求处理管道定义中间件的 ASP.NET Core 应用中使用处理程序和模块的 ASP.NET 应用的结构差异。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 040ae49d1307ef4dcc9dbf49b20544e9cd2bc913
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401071"
---
# <a name="compare-middleware-to-modules-and-handlers"></a><span data-ttu-id="7e996-103">将中间件与模块和处理程序进行比较</span><span class="sxs-lookup"><span data-stu-id="7e996-103">Compare middleware to modules and handlers</span></span>

<span data-ttu-id="7e996-104">如果现有的 ASP.NET MVC 或 Web API 应用使用 OWIN/Katana，则很可能已熟悉中间件的概念并将其移植到 ASP.NET Core 应该非常简单。</span><span class="sxs-lookup"><span data-stu-id="7e996-104">If your existing ASP.NET MVC or Web API app uses OWIN/Katana, you're most likely already familiar with the concept of middleware and porting it to ASP.NET Core should be fairly straightforward.</span></span> <span data-ttu-id="7e996-105">但是，大多数 ASP.NET 应用依赖于 HTTP 模块和 HTTP 处理程序而不是中间件。</span><span class="sxs-lookup"><span data-stu-id="7e996-105">However, most ASP.NET apps rely on HTTP modules and HTTP handlers instead of middleware.</span></span> <span data-ttu-id="7e996-106">将这些迁移到 ASP.NET Core 需要额外的工作。</span><span class="sxs-lookup"><span data-stu-id="7e996-106">Migrating these to ASP.NET Core requires extra effort.</span></span>

## <a name="aspnet-modules-and-handlers"></a><span data-ttu-id="7e996-107">ASP.NET 模块和处理程序</span><span class="sxs-lookup"><span data-stu-id="7e996-107">ASP.NET modules and handlers</span></span>

<span data-ttu-id="7e996-108">[Http 模块和 http 处理程序](/troubleshoot/aspnet/http-modules-handlers) 是 ASP.NET 体系结构不可或缺的一部分。</span><span class="sxs-lookup"><span data-stu-id="7e996-108">[HTTP modules and HTTP handlers](/troubleshoot/aspnet/http-modules-handlers) are an integral part of the ASP.NET architecture.</span></span> <span data-ttu-id="7e996-109">处理请求时，每个请求由多个 HTTP 模块处理 (例如，身份验证模块和会话模块) 并由单个 HTTP 处理程序进行处理。</span><span class="sxs-lookup"><span data-stu-id="7e996-109">While a request is being processed, each request is processed by multiple HTTP modules (for example, the authentication module and the session module) and is then processed by a single HTTP handler.</span></span> <span data-ttu-id="7e996-110">处理程序处理完请求后，请求会通过 HTTP 模块进行流处理。</span><span class="sxs-lookup"><span data-stu-id="7e996-110">After the handler has processed the request, the request flows back through the HTTP modules.</span></span>

<span data-ttu-id="7e996-111">如果你的应用使用的是自定义 HTTP 模块或 HTTP 处理程序，则需要计划将其迁移到 ASP.NET Core。</span><span class="sxs-lookup"><span data-stu-id="7e996-111">If your app is using custom HTTP modules or HTTP handlers, you'll need a plan to migrate them to ASP.NET Core.</span></span> <span data-ttu-id="7e996-112">ASP.NET Core 中最可能的替换为中间件。</span><span class="sxs-lookup"><span data-stu-id="7e996-112">The most likely replacement in ASP.NET Core is middleware.</span></span>

## <a name="aspnet-core-middleware"></a><span data-ttu-id="7e996-113">ASP.NET Core 中间件</span><span class="sxs-lookup"><span data-stu-id="7e996-113">ASP.NET Core middleware</span></span>

<span data-ttu-id="7e996-114">ASP.NET Core 在每个应用的方法中定义一个请求管道 `Configure` 。</span><span class="sxs-lookup"><span data-stu-id="7e996-114">ASP.NET Core defines a request pipeline in each app's `Configure` method.</span></span> <span data-ttu-id="7e996-115">此请求管道定义了应用如何处理传入的请求，以及管道中的每个方法调用下一个方法直到最终方法终止， *中间件* 的链终止并返回堆栈。</span><span class="sxs-lookup"><span data-stu-id="7e996-115">This request pipeline defines how an incoming request is handled by the app, with each method in the pipeline calling the next method until eventually a method terminates, and the chain of *middleware* terminates and returns back up the stack.</span></span> <span data-ttu-id="7e996-116">中间件可以面向所有请求，或者可以配置为仅根据请求的路径或其他因素映射到特定请求。</span><span class="sxs-lookup"><span data-stu-id="7e996-116">Middleware can target all requests, or can be configured to only map to certain requests based on the requested path or other factors.</span></span> <span data-ttu-id="7e996-117">它可以在应用的方法中完全配置 `Configure` ，也可以在单独的类中实现。</span><span class="sxs-lookup"><span data-stu-id="7e996-117">It can be configured wholly in the `Configure` method of an app, or implemented in a separate class.</span></span>

<span data-ttu-id="7e996-118">使用 HTTP 模块的 ASP.NET MVC 应用程序中的行为可能最适用于 [自定义中间件](/aspnet/core/fundamentals/middleware/?preserve-view=true&view=aspnetcore-3.1)。</span><span class="sxs-lookup"><span data-stu-id="7e996-118">Behavior in an ASP.NET MVC app that uses HTTP modules is probably best suited to [custom middleware](/aspnet/core/fundamentals/middleware/?preserve-view=true&view=aspnetcore-3.1).</span></span> <span data-ttu-id="7e996-119">自定义 HTTP 处理程序可以替换为响应同一路径的自定义路由或终结点。</span><span class="sxs-lookup"><span data-stu-id="7e996-119">Custom HTTP handlers can be replaced with custom routes or endpoints that respond to the same path.</span></span>

## <a name="references"></a><span data-ttu-id="7e996-120">参考</span><span class="sxs-lookup"><span data-stu-id="7e996-120">References</span></span>

- [<span data-ttu-id="7e996-121">ASP.NET HTTP 模块和 HTTP 处理程序</span><span class="sxs-lookup"><span data-stu-id="7e996-121">ASP.NET HTTP modules and HTTP handlers</span></span>](/troubleshoot/aspnet/http-modules-handlers)
- [<span data-ttu-id="7e996-122">ASP.NET Core 中间件</span><span class="sxs-lookup"><span data-stu-id="7e996-122">ASP.NET Core middleware</span></span>](/aspnet/core/fundamentals/middleware/?preserve-view=true&view=aspnetcore-3.1)

>[!div class="step-by-step"]
><span data-ttu-id="7e996-123">[上一页](dependency-injection-differences.md)
>[下一页](configuration-differences.md)</span><span class="sxs-lookup"><span data-stu-id="7e996-123">[Previous](dependency-injection-differences.md)
[Next](configuration-differences.md)</span></span>
