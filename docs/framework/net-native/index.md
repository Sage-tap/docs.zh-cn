---
description: 了解有关以下内容的详细信息：编译应用 .NET Native
title: 使用 .NET Native 编译引用
ms.date: 03/30/2017
helpviewer_keywords:
- native compilation
- .NET and native code
- compilation with .NET Native
- .NET Native
- C# and native compilation
ms.assetid: 47cd5648-9469-4b1d-804c-43cc04384045
ms.openlocfilehash: 2626daf17fda751edd7915f15fd4b68ffb623dff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747655"
---
# <a name="compiling-apps-with-net-native"></a><span data-ttu-id="e5785-103">使用 .NET Native 编译引用</span><span class="sxs-lookup"><span data-stu-id="e5785-103">Compiling Apps with .NET Native</span></span>

<span data-ttu-id="e5785-104">.NET Native 是一种用于生成和部署 Visual Studio 2015 及更高版本附带的 Windows 应用的预编译技术。</span><span class="sxs-lookup"><span data-stu-id="e5785-104">.NET Native is a precompilation technology for building and deploying Windows apps that is included with Visual Studio 2015 and later versions.</span></span> <span data-ttu-id="e5785-105">它自动将以托管代码（C# 或 Visual Basic）编写并面向 .NET Framework 和 Windows 10 的发布版本的应用编译为本机代码。</span><span class="sxs-lookup"><span data-stu-id="e5785-105">It automatically compiles the release version of apps that are written in managed code (C# or Visual Basic) and that target the .NET Framework and Windows 10 to native code.</span></span>

<span data-ttu-id="e5785-106">通常，定位于 .NET Framework 的应用会被编译到中间语言 (IL) 中。</span><span class="sxs-lookup"><span data-stu-id="e5785-106">Typically, apps that target the .NET Framework are compiled to intermediate language (IL).</span></span> <span data-ttu-id="e5785-107">在运行时间，及时生成 (JIT) 编译器将 IL 翻译为本机代码。</span><span class="sxs-lookup"><span data-stu-id="e5785-107">At run time, the just-in-time (JIT) compiler translates the IL to native code.</span></span> <span data-ttu-id="e5785-108">与此相反，.NET Native 会直接将 Windows 应用编译为本机代码。</span><span class="sxs-lookup"><span data-stu-id="e5785-108">In contrast, .NET Native compiles Windows apps directly to native code.</span></span> <span data-ttu-id="e5785-109">对于开发者，这意味着：</span><span class="sxs-lookup"><span data-stu-id="e5785-109">For developers, this means:</span></span>

- <span data-ttu-id="e5785-110">您的应用程序具有本机代码的性能。</span><span class="sxs-lookup"><span data-stu-id="e5785-110">Your apps feature the performance of native code.</span></span> <span data-ttu-id="e5785-111">通常，性能比首次编译为 IL 的代码更优越，并由 JIT 编译器编译为本机代码。</span><span class="sxs-lookup"><span data-stu-id="e5785-111">Usually, performance will be superior to code that is first compiled to IL and then compiled to native code by the JIT compiler.</span></span>

- <span data-ttu-id="e5785-112">你可以继续用 C# 或 Visual Basic 进行编程。</span><span class="sxs-lookup"><span data-stu-id="e5785-112">You can continue to program in C# or Visual Basic.</span></span>

- <span data-ttu-id="e5785-113">你可以继续使用 .NET Framework 提供的资源，包括类库、自动内存管理、垃圾回收和异常处理。</span><span class="sxs-lookup"><span data-stu-id="e5785-113">You can continue to take advantage of the resources provided by the .NET Framework, including its class library, automatic memory management and garbage collection, and exception handling.</span></span>

<span data-ttu-id="e5785-114">对于你的应用程序的用户，.NET Native 具有以下优势：</span><span class="sxs-lookup"><span data-stu-id="e5785-114">For users of your apps, .NET Native offers these advantages:</span></span>

- <span data-ttu-id="e5785-115">大多数应用和方案的执行时间更快。</span><span class="sxs-lookup"><span data-stu-id="e5785-115">Faster execution times for the majority of apps and scenarios.</span></span>

- <span data-ttu-id="e5785-116">大多数应用和方案的启动时间更快。</span><span class="sxs-lookup"><span data-stu-id="e5785-116">Faster startup times for the majority of apps and scenarios.</span></span>

- <span data-ttu-id="e5785-117">低部署和更新成本。</span><span class="sxs-lookup"><span data-stu-id="e5785-117">Low deployment and update costs.</span></span>

- <span data-ttu-id="e5785-118">优化的应用内存使用情况。</span><span class="sxs-lookup"><span data-stu-id="e5785-118">Optimized app memory usage.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e5785-119">对于绝大多数应用和方案，与编译到 IL 或 NGEN 映像的应用相比，.NET Native 提供明显更快的启动时间和更高的性能。</span><span class="sxs-lookup"><span data-stu-id="e5785-119">For the vast majority of apps and scenarios, .NET Native offers significantly faster startup times and superior performance when compared to an app compiled to IL or to an NGEN image.</span></span> <span data-ttu-id="e5785-120">但是，您的结果可能会有所不同。</span><span class="sxs-lookup"><span data-stu-id="e5785-120">However, your results may vary.</span></span> <span data-ttu-id="e5785-121">若要确保你的应用程序已受益于 .NET Native 的性能增强，你应将其性能与应用程序的 non-.NET 本机版本的性能进行比较。</span><span class="sxs-lookup"><span data-stu-id="e5785-121">To ensure that your app has benefited from the performance enhancements of .NET Native, you should compare its performance with that of the non-.NET Native version of your app.</span></span> <span data-ttu-id="e5785-122">有关详细信息，请参阅 [性能会话概述](/visualstudio/profiling/performance-session-overview)。</span><span class="sxs-lookup"><span data-stu-id="e5785-122">For more information, see [Performance Session Overview](/visualstudio/profiling/performance-session-overview).</span></span>

<span data-ttu-id="e5785-123">但 .NET Native 只涉及到本机代码的编译。</span><span class="sxs-lookup"><span data-stu-id="e5785-123">But .NET Native involves more than a compilation to native code.</span></span> <span data-ttu-id="e5785-124">它会改变 .NET Framework 应用的创建和执行方式。</span><span class="sxs-lookup"><span data-stu-id="e5785-124">It transforms the way that .NET Framework apps are built and executed.</span></span> <span data-ttu-id="e5785-125">具体而言：</span><span class="sxs-lookup"><span data-stu-id="e5785-125">In particular:</span></span>

- <span data-ttu-id="e5785-126">在预编译期间，所需的 .NET Framework 部分会静态连接到你的应用。</span><span class="sxs-lookup"><span data-stu-id="e5785-126">During precompilation, required portions of the .NET Framework are statically linked into your app.</span></span> <span data-ttu-id="e5785-127">这允许应用同 .NET Framework 的应用本地库一起运行，并且允许编译器执行全局分析，从而提供性能优势。</span><span class="sxs-lookup"><span data-stu-id="e5785-127">This allows the app to run with app-local libraries of the .NET Framework, and the compiler to perform global analysis to deliver performance wins.</span></span> <span data-ttu-id="e5785-128">因此，应用甚至在 .NET Framework 更新后会启动得更快。</span><span class="sxs-lookup"><span data-stu-id="e5785-128">As a result, apps launch consistently faster even after .NET Framework updates.</span></span>

- <span data-ttu-id="e5785-129">.NET Native 运行时针对静态预编译进行了优化，在大多数情况下，可提供优异的性能。</span><span class="sxs-lookup"><span data-stu-id="e5785-129">The .NET Native runtime is optimized for static precompilation and in the vast majority of cases offers superior performance.</span></span> <span data-ttu-id="e5785-130">同时，它保留了开发者认为非常高效的核心反射特性。</span><span class="sxs-lookup"><span data-stu-id="e5785-130">At the same time, it retains the core reflection features that developers find so productive.</span></span>

- <span data-ttu-id="e5785-131">.NET Native 使用的后端与 c + + 编译器相同，后者针对静态预编译方案进行了优化。</span><span class="sxs-lookup"><span data-stu-id="e5785-131">.NET Native uses the same back end as the C++ compiler, which is optimized for static precompilation scenarios.</span></span>

<span data-ttu-id="e5785-132">.NET Native 可以将 c + + 的性能优势引入到托管代码开发人员，因为它使用的是与 c + + 中的 c + + 相同或类似的工具，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="e5785-132">.NET Native is able to bring the performance benefits of C++ to managed code developers because it uses the same or similar tools as C++ under the hood, as shown in this table.</span></span>

||<span data-ttu-id="e5785-133">.NET Native</span><span class="sxs-lookup"><span data-stu-id="e5785-133">.NET Native</span></span>|<span data-ttu-id="e5785-134">C++</span><span class="sxs-lookup"><span data-stu-id="e5785-134">C++</span></span>|
|-|----------------------------------------------------------------|-----------|
|<span data-ttu-id="e5785-135">库</span><span class="sxs-lookup"><span data-stu-id="e5785-135">Libraries</span></span>|<span data-ttu-id="e5785-136">.NET Framework + Windows 运行时</span><span class="sxs-lookup"><span data-stu-id="e5785-136">The .NET Framework + Windows Runtime</span></span>|<span data-ttu-id="e5785-137">Win32 + Windows 运行时</span><span class="sxs-lookup"><span data-stu-id="e5785-137">Win32 + Windows Runtime</span></span>|
|<span data-ttu-id="e5785-138">编译器</span><span class="sxs-lookup"><span data-stu-id="e5785-138">Compiler</span></span>|<span data-ttu-id="e5785-139">UTC 优化编译器</span><span class="sxs-lookup"><span data-stu-id="e5785-139">UTC optimizing compiler</span></span>|<span data-ttu-id="e5785-140">UTC 优化编译器</span><span class="sxs-lookup"><span data-stu-id="e5785-140">UTC optimizing compiler</span></span>|
|<span data-ttu-id="e5785-141">已部署</span><span class="sxs-lookup"><span data-stu-id="e5785-141">Deployed</span></span>|<span data-ttu-id="e5785-142">随时可以运行的二进制代码</span><span class="sxs-lookup"><span data-stu-id="e5785-142">Ready-to-run binaries</span></span>|<span data-ttu-id="e5785-143">随时可以运行的二进制代码 (ASM)</span><span class="sxs-lookup"><span data-stu-id="e5785-143">Ready-to-run binaries (ASM)</span></span>|
|<span data-ttu-id="e5785-144">运行时</span><span class="sxs-lookup"><span data-stu-id="e5785-144">Runtime</span></span>|<span data-ttu-id="e5785-145">MRT.dll（最短 CLR 运行时）</span><span class="sxs-lookup"><span data-stu-id="e5785-145">MRT.dll (Minimal CLR Runtime)</span></span>|<span data-ttu-id="e5785-146">CRT.dll（C 运行时）</span><span class="sxs-lookup"><span data-stu-id="e5785-146">CRT.dll (C Runtime)</span></span>|

<span data-ttu-id="e5785-147">对于适用于 Windows 10 的 Windows 应用，可将应用程序包（.appx 文件）中的 .NET 本机代码编译二进制文件上载到 Windows 应用商店。</span><span class="sxs-lookup"><span data-stu-id="e5785-147">For Windows apps for Windows 10, you upload .NET Native Code Compilation binaries in app packages (.appx files) to the Windows Store.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="e5785-148">本节内容</span><span class="sxs-lookup"><span data-stu-id="e5785-148">In This Section</span></span>

<span data-ttu-id="e5785-149">要查看有关带有 .NET Native 代码编译的应用开发的信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="e5785-149">For more information about developing apps with .NET Native Code Compilation, see these topics:</span></span>

- [<span data-ttu-id="e5785-150">.NET Native 代码编译入门：开发者经验介绍</span><span class="sxs-lookup"><span data-stu-id="e5785-150">Getting Started with .NET Native Code Compilation: The Developer Experience Walkthrough</span></span>](getting-started-with-net-native.md)

- <span data-ttu-id="e5785-151">[.NET 本机和编译：](net-native-and-compilation.md) .NET 本机如何将你的项目编译为本机代码。</span><span class="sxs-lookup"><span data-stu-id="e5785-151">[.NET Native and Compilation:](net-native-and-compilation.md) How .NET Native compiles your project to native code.</span></span>

- [<span data-ttu-id="e5785-152">反射和 .NET Native</span><span class="sxs-lookup"><span data-stu-id="e5785-152">Reflection and .NET Native</span></span>](reflection-and-net-native.md)

  - [<span data-ttu-id="e5785-153">利用反射的 API</span><span class="sxs-lookup"><span data-stu-id="e5785-153">APIs That Rely on Reflection</span></span>](apis-that-rely-on-reflection.md)

  - [<span data-ttu-id="e5785-154">反射 API 引用</span><span class="sxs-lookup"><span data-stu-id="e5785-154">Reflection API Reference</span></span>](net-native-reflection-api-reference.md)

  - [<span data-ttu-id="e5785-155">运行时指令 (rd.xml) 配置文件引用</span><span class="sxs-lookup"><span data-stu-id="e5785-155">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)

- [<span data-ttu-id="e5785-156">序列化和元数据</span><span class="sxs-lookup"><span data-stu-id="e5785-156">Serialization and Metadata</span></span>](serialization-and-metadata.md)

- [<span data-ttu-id="e5785-157">将 Windows 应用商店应用迁移到 .NET Native</span><span class="sxs-lookup"><span data-stu-id="e5785-157">Migrating Your Windows Store App to .NET Native</span></span>](migrating-your-windows-store-app-to-net-native.md)

- [<span data-ttu-id="e5785-158">.NET Native 一般疑难解答</span><span class="sxs-lookup"><span data-stu-id="e5785-158">.NET Native General Troubleshooting</span></span>](net-native-general-troubleshooting.md)
