---
title: 依赖项加载 - .NET Core
description: .NET Core 中的托管和非托管依赖项加载概述
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.topic: overview
ms.openlocfilehash: 2eaa01fad3913272dc90891592d0e35cd89ad2ab
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2021
ms.locfileid: "99506313"
---
# <a name="dependency-loading-in-net-core"></a><span data-ttu-id="f0684-103">.NET Core 中的依赖项加载</span><span class="sxs-lookup"><span data-stu-id="f0684-103">Dependency loading in .NET Core</span></span>

<span data-ttu-id="f0684-104">每个 .NET Core 应用程序都有依赖项。</span><span class="sxs-lookup"><span data-stu-id="f0684-104">Every .NET Core application has dependencies.</span></span> <span data-ttu-id="f0684-105">即使是简单的 `hello world` 应用程序也在 .NET Core 类库的各个部分中有依赖项。</span><span class="sxs-lookup"><span data-stu-id="f0684-105">Even the simple `hello world` app has dependencies on portions of the .NET Core class libraries.</span></span>

<span data-ttu-id="f0684-106">了解 .NET Core 默认程序集加载逻辑有助于理解和调试典型的部署问题。</span><span class="sxs-lookup"><span data-stu-id="f0684-106">Understanding .NET Core default assembly loading logic can help understanding and debugging typical deployment issues.</span></span>

<span data-ttu-id="f0684-107">在某些应用程序中，在运行时动态确定依赖项。</span><span class="sxs-lookup"><span data-stu-id="f0684-107">In some applications, dependencies are dynamically determined at run time.</span></span> <span data-ttu-id="f0684-108">在这些情况下，了解托管程序集和非托管依赖项的加载方式至关重要。</span><span class="sxs-lookup"><span data-stu-id="f0684-108">In these situations, it's critical to understand how managed assemblies and unmanaged dependencies are loaded.</span></span>

## <a name="understanding-assemblyloadcontext"></a><span data-ttu-id="f0684-109">了解 AssemblyLoadContext</span><span class="sxs-lookup"><span data-stu-id="f0684-109">Understanding AssemblyLoadContext</span></span>

<span data-ttu-id="f0684-110"><xref:System.Runtime.Loader.AssemblyLoadContext> API 是 .NET Core 加载设计的核心。</span><span class="sxs-lookup"><span data-stu-id="f0684-110">The <xref:System.Runtime.Loader.AssemblyLoadContext> API is central to the .NET Core loading design.</span></span> <span data-ttu-id="f0684-111">[了解 AssemblyLoadContext ](understanding-assemblyloadcontext.md) 一文提供了有关设计的概念性概述。</span><span class="sxs-lookup"><span data-stu-id="f0684-111">The [Understanding AssemblyLoadContext](understanding-assemblyloadcontext.md) article provides a conceptual overview to the design.</span></span>

## <a name="loading-details"></a><span data-ttu-id="f0684-112">加载详细信息</span><span class="sxs-lookup"><span data-stu-id="f0684-112">Loading details</span></span>

<span data-ttu-id="f0684-113">以下几篇文章简要介绍了加载算法的详细信息：</span><span class="sxs-lookup"><span data-stu-id="f0684-113">The loading algorithm details are covered briefly in several articles:</span></span>

- [<span data-ttu-id="f0684-114">托管程序集加载算法</span><span class="sxs-lookup"><span data-stu-id="f0684-114">Managed assembly loading algorithm</span></span>](loading-managed.md)
- [<span data-ttu-id="f0684-115">附属程序集加载算法</span><span class="sxs-lookup"><span data-stu-id="f0684-115">Satellite assembly loading algorithm</span></span>](loading-resources.md)
- [<span data-ttu-id="f0684-116">非托管（本机）库加载算法</span><span class="sxs-lookup"><span data-stu-id="f0684-116">Unmanaged (native) library loading algorithm</span></span>](loading-unmanaged.md)
- [<span data-ttu-id="f0684-117">默认探测</span><span class="sxs-lookup"><span data-stu-id="f0684-117">Default probing</span></span>](default-probing.md)

## <a name="create-a-net-core-application-with-plugins"></a><span data-ttu-id="f0684-118">使用插件创建 .NET Core 应用程序</span><span class="sxs-lookup"><span data-stu-id="f0684-118">Create a .NET Core application with plugins</span></span>

<span data-ttu-id="f0684-119">[创建包含插件的 .NET Core 应用程序](../tutorials/creating-app-with-plugin-support.md)教程介绍了如何创建自定义 AssemblyLoadContext。</span><span class="sxs-lookup"><span data-stu-id="f0684-119">The tutorial [Create a .NET Core application with plugins](../tutorials/creating-app-with-plugin-support.md) describes how to create a custom AssemblyLoadContext.</span></span> <span data-ttu-id="f0684-120">它使用 <xref:System.Runtime.Loader.AssemblyDependencyResolver> 来解析插件的依赖项。</span><span class="sxs-lookup"><span data-stu-id="f0684-120">It uses an <xref:System.Runtime.Loader.AssemblyDependencyResolver> to resolve the dependencies of the plugin.</span></span> <span data-ttu-id="f0684-121">该教程正确地将插件依赖项与主机应用程序隔离开来。</span><span class="sxs-lookup"><span data-stu-id="f0684-121">The tutorial correctly isolates the plugin's dependencies from the hosting application.</span></span>

## <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a><span data-ttu-id="f0684-122">如何在 .NET Core 中使用和调试程序集可卸载性</span><span class="sxs-lookup"><span data-stu-id="f0684-122">How to use and debug assembly unloadability in .NET Core</span></span>

<span data-ttu-id="f0684-123">[如何在 .NET Core 中使用和调试程序集可卸载性](../../standard/assembly/unloadability.md)一文是逐步骤教程。</span><span class="sxs-lookup"><span data-stu-id="f0684-123">The [How to use and debug assembly unloadability in .NET Core](../../standard/assembly/unloadability.md) article is a step-by-step tutorial.</span></span> <span data-ttu-id="f0684-124">其中显示了如何加载 .NET Core 应用程序、执行以及将其卸载。</span><span class="sxs-lookup"><span data-stu-id="f0684-124">It shows how to load a .NET Core application, execute, and then unload it.</span></span> <span data-ttu-id="f0684-125">该文章还提供了调试提示。</span><span class="sxs-lookup"><span data-stu-id="f0684-125">The article also provides debugging tips.</span></span>

## <a name="collect-detailed-assembly-loading-information"></a><span data-ttu-id="f0684-126">收集详细的程序集加载信息</span><span class="sxs-lookup"><span data-stu-id="f0684-126">Collect detailed assembly loading information</span></span>

<span data-ttu-id="f0684-127">[收集详细的程序集加载信息](collect-details.md)一文介绍了如何收集运行时中托管程序集加载的详细信息。</span><span class="sxs-lookup"><span data-stu-id="f0684-127">The [Collect detailed assembly loading information](collect-details.md) article describes how to collect detailed information about managed assembly loading in the runtime.</span></span> <span data-ttu-id="f0684-128">它使用 [dotnet-trace](../diagnostics/dotnet-trace.md) 工具在正在运行的进程的跟踪中捕获程序集加载程序事件。</span><span class="sxs-lookup"><span data-stu-id="f0684-128">It uses the [dotnet-trace](../diagnostics/dotnet-trace.md) tool to capture assembly loader events in a trace of a running process.</span></span>
