---
ms.openlocfilehash: 73bf0ba78e2986da3e0aa66d492f1765df563b27
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2021
ms.locfileid: "102109265"
---
### <a name="target-framework-net-framework-support-dropped"></a><span data-ttu-id="41b38-101">目标框架：删除了 .NET Framework 支持</span><span class="sxs-lookup"><span data-stu-id="41b38-101">Target framework: .NET Framework support dropped</span></span>

<span data-ttu-id="41b38-102">从 ASP.NET Core 3.0 开始，.NET Framework 不再是受支持的目标框架。</span><span class="sxs-lookup"><span data-stu-id="41b38-102">Starting with ASP.NET Core 3.0, .NET Framework is an unsupported target framework.</span></span>

#### <a name="change-description"></a><span data-ttu-id="41b38-103">更改描述</span><span class="sxs-lookup"><span data-stu-id="41b38-103">Change description</span></span>

<span data-ttu-id="41b38-104">.NET Framework 4.8 是 .NET Framework 的上一个主要版本。</span><span class="sxs-lookup"><span data-stu-id="41b38-104">.NET Framework 4.8 is the last major version of .NET Framework.</span></span> <span data-ttu-id="41b38-105">新的 ASP.NET Core 应用应基于 .NET Core 构建。</span><span class="sxs-lookup"><span data-stu-id="41b38-105">New ASP.NET Core apps should be built on .NET Core.</span></span> <span data-ttu-id="41b38-106">从 .NET Core 3.0 版开始，可将 ASP.NET Core 3.0 视为 .NET Core 的一部分。</span><span class="sxs-lookup"><span data-stu-id="41b38-106">Starting with the .NET Core 3.0 release, you can think of ASP.NET Core 3.0 as being part of .NET Core.</span></span>

<span data-ttu-id="41b38-107">将 .NET Framework 和 ASP.NET Core 结合使用的客户可以使用 [2.1 LTS 版本](https://dotnet.microsoft.com/download/dotnet/2.1)以完全受支持的方式继续。</span><span class="sxs-lookup"><span data-stu-id="41b38-107">Customers using ASP.NET Core with .NET Framework can continue in a fully supported fashion using the [2.1 LTS release](https://dotnet.microsoft.com/download/dotnet/2.1).</span></span> <span data-ttu-id="41b38-108">至少在 2021 年 8 月 21 日之前，将继续提供对 2.1 的支持和服务。</span><span class="sxs-lookup"><span data-stu-id="41b38-108">Support and servicing for 2.1 continues until at least August 21, 2021.</span></span> <span data-ttu-id="41b38-109">根据 [.NET 支持策略](https://dotnet.microsoft.com/platform/support-policy)，此日期为声明 LTS 版本后三年。</span><span class="sxs-lookup"><span data-stu-id="41b38-109">This date is three years after declaration of the LTS release per the [.NET Support Policy](https://dotnet.microsoft.com/platform/support-policy).</span></span> <span data-ttu-id="41b38-110">.NET Framework 对 ASP.NET Core 2.1 包的支持将无限延期，类似于[其他基于包的 ASP.NET 框架的服务策略](https://dotnet.microsoft.com/platform/support/policy/aspnet)。</span><span class="sxs-lookup"><span data-stu-id="41b38-110">Support for ASP.NET Core 2.1 packages **on .NET Framework** will extend indefinitely, similar to the [servicing policy for other package-based ASP.NET frameworks](https://dotnet.microsoft.com/platform/support/policy/aspnet).</span></span>

<span data-ttu-id="41b38-111">有关从 .NET Framework 移植到 .NET Core 的详细信息，请参阅[移植到 .NET Core](~/docs/core/porting/index.md)。</span><span class="sxs-lookup"><span data-stu-id="41b38-111">For more information about porting from .NET Framework to .NET Core, see [Porting to .NET Core](~/docs/core/porting/index.md).</span></span>

<span data-ttu-id="41b38-112">`Microsoft.Extensions` 包（如日志记录、依赖项注入和配置）和 Entity Framework Core 不受影响。</span><span class="sxs-lookup"><span data-stu-id="41b38-112">`Microsoft.Extensions` packages (such as logging, dependency injection, and configuration) and Entity Framework Core aren't affected.</span></span> <span data-ttu-id="41b38-113">它们将继续支持 .NET Standard。</span><span class="sxs-lookup"><span data-stu-id="41b38-113">They'll continue to support .NET Standard.</span></span>

<span data-ttu-id="41b38-114">有关此更改动机的详细信息，请参阅[原始博客文章](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/)。</span><span class="sxs-lookup"><span data-stu-id="41b38-114">For more information on the motivation for this change, see [the original blog post](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="41b38-115">引入的版本</span><span class="sxs-lookup"><span data-stu-id="41b38-115">Version introduced</span></span>

<span data-ttu-id="41b38-116">3.0</span><span class="sxs-lookup"><span data-stu-id="41b38-116">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="41b38-117">旧行为</span><span class="sxs-lookup"><span data-stu-id="41b38-117">Old behavior</span></span>

<span data-ttu-id="41b38-118">ASP.NET Core 应用可在 .NET Core 或 .NET Framework 上运行。</span><span class="sxs-lookup"><span data-stu-id="41b38-118">ASP.NET Core apps could run on either .NET Core or .NET Framework.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="41b38-119">新行为</span><span class="sxs-lookup"><span data-stu-id="41b38-119">New behavior</span></span>

<span data-ttu-id="41b38-120">ASP.NET Core 应用只能在 .NET Core 上运行。</span><span class="sxs-lookup"><span data-stu-id="41b38-120">ASP.NET Core apps can only be run on .NET Core.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="41b38-121">建议的操作</span><span class="sxs-lookup"><span data-stu-id="41b38-121">Recommended action</span></span>

<span data-ttu-id="41b38-122">请执行以下一项操作：</span><span class="sxs-lookup"><span data-stu-id="41b38-122">Take one of the following actions:</span></span>

- <span data-ttu-id="41b38-123">将应用保留在 ASP.NET Core 2.1 上。</span><span class="sxs-lookup"><span data-stu-id="41b38-123">Keep your app on ASP.NET Core 2.1.</span></span>
- <span data-ttu-id="41b38-124">将应用和依赖项迁移到 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="41b38-124">Migrate your app and dependencies to .NET Core.</span></span>

#### <a name="category"></a><span data-ttu-id="41b38-125">类别</span><span class="sxs-lookup"><span data-stu-id="41b38-125">Category</span></span>

<span data-ttu-id="41b38-126">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="41b38-126">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="41b38-127">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="41b38-127">Affected APIs</span></span>

<span data-ttu-id="41b38-128">无</span><span class="sxs-lookup"><span data-stu-id="41b38-128">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
