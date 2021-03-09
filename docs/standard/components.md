---
title: .NET 体系结构组件
description: 描述 .NET 体系结构组件，例如 .NET Standard、.NET 实现、.NET 运行时和工具。
author: cartermp
ms.date: 10/05/2020
ms.openlocfilehash: 884deb61ab5cda5054fb54134c3338b4d05599ca
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106392"
---
# <a name="net-architectural-components"></a><span data-ttu-id="4698e-103">.NET 体系结构组件</span><span class="sxs-lookup"><span data-stu-id="4698e-103">.NET architectural components</span></span>

<span data-ttu-id="4698e-104">.NET 应用开发用于并运行于一个或多个 .NET 实现  。</span><span class="sxs-lookup"><span data-stu-id="4698e-104">A .NET app is developed for and runs in one or more *implementations of .NET*.</span></span> <span data-ttu-id="4698e-105">.NET 实现包括 .NET Framework、.NET 5（和 .NET Core）以及 Mono。</span><span class="sxs-lookup"><span data-stu-id="4698e-105">Implementations of .NET include the .NET Framework, .NET 5 (and .NET Core), and Mono.</span></span> <span data-ttu-id="4698e-106">对于多个 .NET 实现，有一个名为 .NET Standard 的通用 API 规范。</span><span class="sxs-lookup"><span data-stu-id="4698e-106">There is an API specification common to multiple implementations of .NET that's called .NET Standard.</span></span> <span data-ttu-id="4698e-107">本文简要介绍了每个概念。</span><span class="sxs-lookup"><span data-stu-id="4698e-107">This article gives a brief introduction to each of these concepts.</span></span>

## <a name="net-standard"></a><span data-ttu-id="4698e-108">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="4698e-108">.NET Standard</span></span>

<span data-ttu-id="4698e-109">.NET Standard 是一组由 .NET 实现的基类库实现的 API。</span><span class="sxs-lookup"><span data-stu-id="4698e-109">.NET Standard is a set of APIs that are implemented by the Base Class Library of a .NET implementation.</span></span> <span data-ttu-id="4698e-110">更正式地说，它是构成协定统一集（这些协定是编写代码的依据）的特定 .NET API 组。</span><span class="sxs-lookup"><span data-stu-id="4698e-110">More formally, it's a specification of .NET APIs that make up a uniform set of contracts that you compile your code against.</span></span> <span data-ttu-id="4698e-111">这些协定在多个 .NET 实现中实现。</span><span class="sxs-lookup"><span data-stu-id="4698e-111">These contracts are implemented in multiple .NET implementations.</span></span>

<span data-ttu-id="4698e-112">.NET Standard 是一个[目标框架](glossary.md#target-framework)。</span><span class="sxs-lookup"><span data-stu-id="4698e-112">.NET Standard is a [target framework](glossary.md#target-framework).</span></span> <span data-ttu-id="4698e-113">如果代码面向 .NET Standard 版本，则它可在支持该 .NET Standard 版本的任何 .NET 实现上运行。</span><span class="sxs-lookup"><span data-stu-id="4698e-113">If your code targets a version of .NET Standard, it can run on any .NET implementation that supports that version of .NET Standard.</span></span>

<span data-ttu-id="4698e-114">创建 .NET Standard 是为了支持跨不同 .NET 实现的可移植性，但现在 .NET 5 提供了一种更好的方法来跨多个平台和工作负载共享代码。</span><span class="sxs-lookup"><span data-stu-id="4698e-114">.NET Standard was created to enable portability across different .NET implementations, but now .NET 5 offers a better way to share code across multiple platforms and workloads.</span></span> <span data-ttu-id="4698e-115">有关详细信息，请参阅 [.NET 5 和 .NET Standard](net-standard.md#net-5-and-net-standard)。</span><span class="sxs-lookup"><span data-stu-id="4698e-115">For more information, see [.NET 5 and .NET Standard](net-standard.md#net-5-and-net-standard).</span></span>

## <a name="net-implementations"></a><span data-ttu-id="4698e-116">.NET 实现</span><span class="sxs-lookup"><span data-stu-id="4698e-116">.NET implementations</span></span>

<span data-ttu-id="4698e-117">.NET 的每个实现都具有以下组件：</span><span class="sxs-lookup"><span data-stu-id="4698e-117">Each implementation of .NET includes the following components:</span></span>

- <span data-ttu-id="4698e-118">一个或多个运行时。</span><span class="sxs-lookup"><span data-stu-id="4698e-118">One or more runtimes.</span></span> <span data-ttu-id="4698e-119">示例：.NET Framework CLR、.NET 5 CLR。</span><span class="sxs-lookup"><span data-stu-id="4698e-119">Examples: .NET Framework CLR, .NET 5 CLR.</span></span>
- <span data-ttu-id="4698e-120">一个类库。</span><span class="sxs-lookup"><span data-stu-id="4698e-120">A class library.</span></span> <span data-ttu-id="4698e-121">示例：.NET Framework 基类库、.NET 5 基类库。</span><span class="sxs-lookup"><span data-stu-id="4698e-121">Examples: .NET Framework Base Class Library, .NET 5 Base Class Library.</span></span>
- <span data-ttu-id="4698e-122">可选择包含一个或多个应用程序框架。</span><span class="sxs-lookup"><span data-stu-id="4698e-122">Optionally, one or more application frameworks.</span></span> <span data-ttu-id="4698e-123">示例：[ASP.NET](https://www.asp.net/)、[Windows 窗体](/dotnet/desktop/winforms/windows-forms-overview)和 [Windows Presentation Foundation (WPF)](/dotnet/desktop/wpf/) 包含在 .NET Framework 和 .NET 5 中。</span><span class="sxs-lookup"><span data-stu-id="4698e-123">Examples: [ASP.NET](https://www.asp.net/), [Windows Forms](/dotnet/desktop/winforms/windows-forms-overview), and [Windows Presentation Foundation (WPF)](/dotnet/desktop/wpf/) are included in the .NET Framework and .NET 5.</span></span>
- <span data-ttu-id="4698e-124">可包含开发工具。</span><span class="sxs-lookup"><span data-stu-id="4698e-124">Optionally, development tools.</span></span> <span data-ttu-id="4698e-125">某些开发工具在多个实现之间共享。</span><span class="sxs-lookup"><span data-stu-id="4698e-125">Some development tools are shared among multiple implementations.</span></span>

<span data-ttu-id="4698e-126">Microsoft 支持以下四种 .NET 实现：</span><span class="sxs-lookup"><span data-stu-id="4698e-126">There are four .NET implementations that Microsoft supports:</span></span>

- <span data-ttu-id="4698e-127">.NET 5（和 .NET Core）及更高版本</span><span class="sxs-lookup"><span data-stu-id="4698e-127">.NET 5 (and .NET Core) and later versions</span></span>
- <span data-ttu-id="4698e-128">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="4698e-128">.NET Framework</span></span>
- <span data-ttu-id="4698e-129">Mono</span><span class="sxs-lookup"><span data-stu-id="4698e-129">Mono</span></span>
- <span data-ttu-id="4698e-130">UWP</span><span class="sxs-lookup"><span data-stu-id="4698e-130">UWP</span></span>

<span data-ttu-id="4698e-131">.NET 5 现在是主要的实现，是正在进行的开发的重点。</span><span class="sxs-lookup"><span data-stu-id="4698e-131">.NET 5 is now the primary implementation, the one that is the focus of ongoing development.</span></span> <span data-ttu-id="4698e-132">.NET 5 是基于单个代码基底进行构建的，该代码基底支持多个平台和许多工作负载，例如 Windows 桌面应用和跨平台控制台应用、云服务和网站。</span><span class="sxs-lookup"><span data-stu-id="4698e-132">.NET 5 is built on a single code base that supports multiple platforms and many workloads, such as Windows desktop apps and cross-platform console apps, cloud services, and websites.</span></span>

### <a name="net-5"></a><span data-ttu-id="4698e-133">.NET 5</span><span class="sxs-lookup"><span data-stu-id="4698e-133">.NET 5</span></span>

<span data-ttu-id="4698e-134">.NET 5 是 .NET 的跨平台实现，专门设计用于处理大规模的服务器和云工作负载。</span><span class="sxs-lookup"><span data-stu-id="4698e-134">.NET 5 is a cross-platform implementation of .NET that is designed to handle server and cloud workloads at scale.</span></span> <span data-ttu-id="4698e-135">它还支持其他工作负载，包括桌面应用。</span><span class="sxs-lookup"><span data-stu-id="4698e-135">It also supports other workloads, including desktop apps.</span></span> <span data-ttu-id="4698e-136">可在 Windows、macOS 和 Linux 上运行。</span><span class="sxs-lookup"><span data-stu-id="4698e-136">It runs on Windows, macOS, and Linux.</span></span> <span data-ttu-id="4698e-137">它可实现 .NET Standard，因此面向 .NET Standard 的代码都可在 .NET 5 上运行。</span><span class="sxs-lookup"><span data-stu-id="4698e-137">It implements .NET Standard, so code that targets .NET Standard can run on .NET 5.</span></span> <span data-ttu-id="4698e-138">[ASP.NET Core](https://dotnet.microsoft.com/learn/aspnet/what-is-aspnet-core)、[Windows 窗体](/dotnet/desktop/winforms/windows-forms-overview)和 [Windows Presentation Foundation (WPF)](/dotnet/desktop/wpf/) 都在 .NET 5 上运行。</span><span class="sxs-lookup"><span data-stu-id="4698e-138">[ASP.NET Core](https://dotnet.microsoft.com/learn/aspnet/what-is-aspnet-core), [Windows Forms](/dotnet/desktop/winforms/windows-forms-overview), and [Windows Presentation Foundation (WPF)](/dotnet/desktop/wpf/) all run on .NET 5.</span></span>

<span data-ttu-id="4698e-139">有关更多信息，请参见以下资源：</span><span class="sxs-lookup"><span data-stu-id="4698e-139">For more information, see the following resources:</span></span>

- [<span data-ttu-id="4698e-140">.NET 简介</span><span class="sxs-lookup"><span data-stu-id="4698e-140">.NET introduction</span></span>](../core/introduction.md)
- [<span data-ttu-id="4698e-141">为服务器应用选择 .NET 5 或 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4698e-141">Choosing between .NET 5 and .NET Framework for server apps</span></span>](choosing-core-framework-server.md)
- [<span data-ttu-id="4698e-142">.NET 5 和 .NET Standard</span><span class="sxs-lookup"><span data-stu-id="4698e-142">.NET 5 and .NET Standard</span></span>](net-standard.md#net-5-and-net-standard)

### <a name="net-framework"></a><span data-ttu-id="4698e-143">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="4698e-143">.NET Framework</span></span>

<span data-ttu-id="4698e-144">.Net Framework 是自 2002 年起就已存在的原始 .NET 实现。</span><span class="sxs-lookup"><span data-stu-id="4698e-144">.NET Framework is the original .NET implementation that has existed since 2002.</span></span> <span data-ttu-id="4698e-145">4\.5 版以及更高版本实现 .NET Standard，因此面向 .NET Standard 的代码都可在这些版本的 .NET Framework 上运行。</span><span class="sxs-lookup"><span data-stu-id="4698e-145">Versions 4.5 and later implement .NET Standard, so code that targets .NET Standard can run on those versions of .NET Framework.</span></span> <span data-ttu-id="4698e-146">它还包含一些特定于 Windows 的 API，如通过 Windows 窗体和 WPF 进行 Windows 桌面开发的 API。</span><span class="sxs-lookup"><span data-stu-id="4698e-146">It contains additional Windows-specific APIs, such as APIs for Windows desktop development with Windows Forms and WPF.</span></span> <span data-ttu-id="4698e-147">.NET Framework 非常适合用于生成 Windows 桌面应用程序。</span><span class="sxs-lookup"><span data-stu-id="4698e-147">.NET Framework is optimized for building Windows desktop applications.</span></span>

<span data-ttu-id="4698e-148">有关详细信息，请参阅 [.NET Framework 指南](../framework/index.yml)。</span><span class="sxs-lookup"><span data-stu-id="4698e-148">For more information, see the [.NET Framework guide](../framework/index.yml).</span></span>

### <a name="mono"></a><span data-ttu-id="4698e-149">Mono</span><span class="sxs-lookup"><span data-stu-id="4698e-149">Mono</span></span>

<span data-ttu-id="4698e-150">Mono 是主要在需要小型运行时使用的 .NET 实现。</span><span class="sxs-lookup"><span data-stu-id="4698e-150">Mono is a .NET implementation that is mainly used when a small runtime is required.</span></span> <span data-ttu-id="4698e-151">它是在 Android、macOS、iOS、tvOS 和 watchOS 上驱动 Xamarin 应用程序的运行时，且主要针对小内存占用。</span><span class="sxs-lookup"><span data-stu-id="4698e-151">It is the runtime that powers Xamarin applications on Android, macOS, iOS, tvOS, and watchOS and is focused primarily on a small footprint.</span></span> <span data-ttu-id="4698e-152">Mono 还支持使用 Unity 引擎生成的游戏。</span><span class="sxs-lookup"><span data-stu-id="4698e-152">Mono also powers games built using the Unity engine.</span></span>

<span data-ttu-id="4698e-153">它支持所有当前已发布的 .NET Standard 版本。</span><span class="sxs-lookup"><span data-stu-id="4698e-153">It supports all of the currently published .NET Standard versions.</span></span>

<span data-ttu-id="4698e-154">以前，Mono 实现更大的 .NET Framework API 并模拟一些 Unix 上最常用的功能。</span><span class="sxs-lookup"><span data-stu-id="4698e-154">Historically, Mono implemented the larger API of the .NET Framework and emulated some of the most popular capabilities on Unix.</span></span> <span data-ttu-id="4698e-155">有时使用它运行依赖 Unix 上的这些功能的 .NET 应用程序。</span><span class="sxs-lookup"><span data-stu-id="4698e-155">It is sometimes used to run .NET applications that rely on those capabilities on Unix.</span></span>

<span data-ttu-id="4698e-156">Mono 通常与实时编译器一起使用，但它也提供在 iOS 之类的平台使用的完整静态编译器（预先编译）。</span><span class="sxs-lookup"><span data-stu-id="4698e-156">Mono is typically used with a just-in-time compiler, but it also features a full static compiler (ahead-of-time compilation) that is used on platforms like iOS.</span></span>

<span data-ttu-id="4698e-157">有关详细信息，请参阅 [Mono 文档](https://www.mono-project.com/docs/)。</span><span class="sxs-lookup"><span data-stu-id="4698e-157">For more information, see the [Mono documentation](https://www.mono-project.com/docs/).</span></span>

### <a name="universal-windows-platform-uwp"></a><span data-ttu-id="4698e-158">通用 Windows 平台 (UWP)</span><span class="sxs-lookup"><span data-stu-id="4698e-158">Universal Windows Platform (UWP)</span></span>

<span data-ttu-id="4698e-159">UWP 是用于为物联网 (IoT) 生成新式触控 Windows 应用程序和软件的 .NET 实现。</span><span class="sxs-lookup"><span data-stu-id="4698e-159">UWP is an implementation of .NET that is used for building modern, touch-enabled Windows applications and software for the Internet of Things (IoT).</span></span> <span data-ttu-id="4698e-160">它旨在统一可能想要以其为目标的不同类型的设备，包括电脑、平板电脑、电话，甚至 Xbox。</span><span class="sxs-lookup"><span data-stu-id="4698e-160">It's designed to unify the different types of devices that you may want to target, including PCs, tablets, phones, and even the Xbox.</span></span> <span data-ttu-id="4698e-161">UWP 提供许多服务，如集中式应用商店、执行环境 (AppContainer) 和一组 Windows API（用于代替 Win32 (WinRT)）。</span><span class="sxs-lookup"><span data-stu-id="4698e-161">UWP provides many services, such as a centralized app store, an execution environment (AppContainer), and a set of Windows APIs to use instead of Win32 (WinRT).</span></span> <span data-ttu-id="4698e-162">应用可采用 C++、C#、Visual Basic 和 JavaScript 编写。</span><span class="sxs-lookup"><span data-stu-id="4698e-162">Apps can be written in C++, C#, Visual Basic, and JavaScript.</span></span>

<span data-ttu-id="4698e-163">有关详细信息，请参阅[通用 Windows 平台简介](/windows/uwp/get-started/universal-application-platform-guide)。</span><span class="sxs-lookup"><span data-stu-id="4698e-163">For more information, see [Introduction to the Universal Windows Platform](/windows/uwp/get-started/universal-application-platform-guide).</span></span>

## <a name="net-runtimes"></a><span data-ttu-id="4698e-164">.NET 运行时</span><span class="sxs-lookup"><span data-stu-id="4698e-164">.NET runtimes</span></span>

<span data-ttu-id="4698e-165">运行时是用于托管程序的执行环境。</span><span class="sxs-lookup"><span data-stu-id="4698e-165">A runtime is the execution environment for a managed program.</span></span> <span data-ttu-id="4698e-166">操作系统属于运行时环境，但不属于 .NET 运行时。</span><span class="sxs-lookup"><span data-stu-id="4698e-166">The OS is part of the runtime environment but is not part of the .NET runtime.</span></span> <span data-ttu-id="4698e-167">下面是 .NET 运行时的一些示例：</span><span class="sxs-lookup"><span data-stu-id="4698e-167">Here are some examples of .NET runtimes:</span></span>

- <span data-ttu-id="4698e-168">.NET Framework 公共语言运行时 (CLR)</span><span class="sxs-lookup"><span data-stu-id="4698e-168">Common Language Runtime (CLR) for .NET Framework</span></span>
- <span data-ttu-id="4698e-169">.NET 5 公共语言运行时 (CLR)</span><span class="sxs-lookup"><span data-stu-id="4698e-169">Common Language Runtime (CLR) for .NET 5</span></span>
- <span data-ttu-id="4698e-170">适用于通用 Windows 平台的 .NET Native</span><span class="sxs-lookup"><span data-stu-id="4698e-170">.NET Native for Universal Windows Platform</span></span>
- <span data-ttu-id="4698e-171">用于 Xamarin.iOS、Xamarin.Android、Xamarin.Mac 和 Mono 桌面框架的 Mono 运行时</span><span class="sxs-lookup"><span data-stu-id="4698e-171">The Mono runtime for Xamarin.iOS, Xamarin.Android, Xamarin.Mac, and the Mono desktop framework</span></span>

## <a name="net-tooling-and-common-infrastructure"></a><span data-ttu-id="4698e-172">.NET 工具和常见基础结构</span><span class="sxs-lookup"><span data-stu-id="4698e-172">.NET tooling and common infrastructure</span></span>

<span data-ttu-id="4698e-173">可访问一整套适用于每种 .NET 实现的工具和基础结构组件。</span><span class="sxs-lookup"><span data-stu-id="4698e-173">You have access to an extensive set of tools and infrastructure components that work with every implementation of .NET.</span></span> <span data-ttu-id="4698e-174">这些工具和组件包括：</span><span class="sxs-lookup"><span data-stu-id="4698e-174">These tools and components include:</span></span>

- <span data-ttu-id="4698e-175">.NET 语言及其编译器</span><span class="sxs-lookup"><span data-stu-id="4698e-175">The .NET languages and their compilers</span></span>
- <span data-ttu-id="4698e-176">.NET 项目系统（基于 .csproj  .vbproj  和 .fsproj  文件）</span><span class="sxs-lookup"><span data-stu-id="4698e-176">The .NET project system (based on *.csproj*, *.vbproj*, and *.fsproj* files)</span></span>
- <span data-ttu-id="4698e-177">[MSBuild](/visualstudio/msbuild/msbuild)（用于生成项目的生成引擎）</span><span class="sxs-lookup"><span data-stu-id="4698e-177">[MSBuild](/visualstudio/msbuild/msbuild), the build engine used to build projects</span></span>
- <span data-ttu-id="4698e-178">[NuGet](/nuget/)（适用于.NET 的 Microsoft 程序包管理器）</span><span class="sxs-lookup"><span data-stu-id="4698e-178">[NuGet](/nuget/), Microsoft's package manager for .NET</span></span>
- <span data-ttu-id="4698e-179">开放源生成业务流程工具，例如 [CAKE](https://cakebuild.net/) 和 [FAKE](https://fake.build/)</span><span class="sxs-lookup"><span data-stu-id="4698e-179">Open-source build orchestration tools, such as [CAKE](https://cakebuild.net/) and [FAKE](https://fake.build/)</span></span>

<span data-ttu-id="4698e-180">有关详细信息，请参阅[工具与工作效率](../core/introduction.md#tools-and-productivity)。</span><span class="sxs-lookup"><span data-stu-id="4698e-180">For more information, see [Tools and productivity](../core/introduction.md#tools-and-productivity).</span></span>

## <a name="applicable-standards"></a><span data-ttu-id="4698e-181">适用标准</span><span class="sxs-lookup"><span data-stu-id="4698e-181">Applicable standards</span></span>

<span data-ttu-id="4698e-182">C# 语言和公共语言基础结构 (CLI) 规范通过 [Ecma International&reg;](https://www.ecma-international.org/) 进行标准化。</span><span class="sxs-lookup"><span data-stu-id="4698e-182">The C# Language and the Common Language Infrastructure (CLI) specifications are standardized through [Ecma International&reg;](https://www.ecma-international.org/).</span></span> <span data-ttu-id="4698e-183">这些标准的第一版已于 2001 年 12 月由 Ecma 发布。</span><span class="sxs-lookup"><span data-stu-id="4698e-183">The first editions of these standards were published by Ecma in December 2001.</span></span>

<span data-ttu-id="4698e-184">这些标准的后续版本由编程委员技术委员会 ([TC49](https://www.ecma-international.org/technical-committees/tc49/)) 的 TC49-TG2 (C#) 和 TC49-TG3 (CLI) 任务组编制，被 Ecma General Assembly 采纳，随后通过 ISO 快速跟踪流程被 ISO/IEC JTC 1 采纳。</span><span class="sxs-lookup"><span data-stu-id="4698e-184">Subsequent revisions to the standards have been developed by the TC49-TG2 (C#) and TC49-TG3 (CLI) task groups within the Programming Languages Technical Committee ([TC49](https://www.ecma-international.org/technical-committees/tc49/)), and adopted by the Ecma General Assembly and subsequently by ISO/IEC JTC 1 via the ISO Fast-Track process.</span></span>

### <a name="latest-standards"></a><span data-ttu-id="4698e-185">最新标准</span><span class="sxs-lookup"><span data-stu-id="4698e-185">Latest standards</span></span>

<span data-ttu-id="4698e-186">以下官方 Ecma 文档可用于 [C#](https://www.ecma-international.org/publications-and-standards/standards/ecma-334/) 和 [CLI](https://www.ecma-international.org/publications-and-standards/standards/ecma-335/) ([TR-84](https://www.ecma-international.org/publications-and-standards/technical-reports/ecma-tr-84/))：</span><span class="sxs-lookup"><span data-stu-id="4698e-186">The following official Ecma documents are available for [C#](https://www.ecma-international.org/publications-and-standards/standards/ecma-334/) and the [CLI](https://www.ecma-international.org/publications-and-standards/standards/ecma-335/) ([TR-84](https://www.ecma-international.org/publications-and-standards/technical-reports/ecma-tr-84/)):</span></span>

- <span data-ttu-id="4698e-187">**C# 语言标准（版本 5.0）** ：[ECMA-334.pdf](https://www.ecma-international.org/wp-content/uploads/ECMA-334_5th_edition_december_2017.pdf)</span><span class="sxs-lookup"><span data-stu-id="4698e-187">**The C# Language Standard (version 5.0)**: [ECMA-334.pdf](https://www.ecma-international.org/wp-content/uploads/ECMA-334_5th_edition_december_2017.pdf)</span></span>
- <span data-ttu-id="4698e-188">**公共语言基础结构**：[ECMA-335.pdf](hhttps://www.ecma-international.org/wp-content/uploads/ECMA-335_6th_edition_june_2012.pdf)。</span><span class="sxs-lookup"><span data-stu-id="4698e-188">**The Common Language Infrastructure**: [ECMA-335.pdf](hhttps://www.ecma-international.org/wp-content/uploads/ECMA-335_6th_edition_june_2012.pdf).</span></span>
- <span data-ttu-id="4698e-189">**派生自分区 IV XML 文件的信息**：[ECMA-084.pdf](https://www.ecma-international.org/publications/files/ECMA-TR/ECMA%20TR-084.pdf) 格式。</span><span class="sxs-lookup"><span data-stu-id="4698e-189">**Information Derived from the Partition IV XML File**: [ECMA-084.pdf](https://www.ecma-international.org/publications/files/ECMA-TR/ECMA%20TR-084.pdf) format.</span></span>

<span data-ttu-id="4698e-190">官方 ISO/IEC 文档可从 ISO/IEC [公开标准](https://standards.iso.org/ittf/PubliclyAvailableStandards/)页获取。</span><span class="sxs-lookup"><span data-stu-id="4698e-190">The official ISO/IEC documents are available from the ISO/IEC [Publicly Available Standards](https://standards.iso.org/ittf/PubliclyAvailableStandards/) page.</span></span> <span data-ttu-id="4698e-191">以下链接可从该页面直接获得：</span><span class="sxs-lookup"><span data-stu-id="4698e-191">These links are direct from that page:</span></span>

- <span data-ttu-id="4698e-192">**信息技术 - 编程语言 - C#** ：[ISO/IEC 23270:2018](https://standards.iso.org/ittf/PubliclyAvailableStandards/c075178_ISO_IEC_23270_2018.zip)</span><span class="sxs-lookup"><span data-stu-id="4698e-192">**Information technology - Programming languages - C#**: [ISO/IEC 23270:2018](https://standards.iso.org/ittf/PubliclyAvailableStandards/c075178_ISO_IEC_23270_2018.zip)</span></span>
- <span data-ttu-id="4698e-193">**信息技术 - 公共语言基础结构 (CLI) 分区 I 到 VI**：[ISO/IEC 23271:2012](https://standards.iso.org/ittf/PubliclyAvailableStandards/c058046_ISO_IEC_23271_2012(E).zip)</span><span class="sxs-lookup"><span data-stu-id="4698e-193">**Information technology — Common Language Infrastructure (CLI) Partitions I to VI**: [ISO/IEC 23271:2012](https://standards.iso.org/ittf/PubliclyAvailableStandards/c058046_ISO_IEC_23271_2012(E).zip)</span></span>
- <span data-ttu-id="4698e-194">**信息技术 - 公共语言基础结构 (CLI) - 有关派生自分区 IV XML 文件的信息的技术报告**：[ISO/IEC TR 23272:2011](https://www.ecma-international.org/wp-content/uploads/ECMA_TR-84_6th_edition_june_2012.pdf)</span><span class="sxs-lookup"><span data-stu-id="4698e-194">**Information technology — Common Language Infrastructure (CLI) — Technical Report on Information Derived from Partition IV XML File**: [ISO/IEC TR 23272:2011](https://www.ecma-international.org/wp-content/uploads/ECMA_TR-84_6th_edition_june_2012.pdf)</span></span>

## <a name="see-also"></a><span data-ttu-id="4698e-195">请参阅</span><span class="sxs-lookup"><span data-stu-id="4698e-195">See also</span></span>

- [<span data-ttu-id="4698e-196">.NET 简介</span><span class="sxs-lookup"><span data-stu-id="4698e-196">.NET introduction</span></span>](../core/introduction.md)
- [<span data-ttu-id="4698e-197">.NET Standard 简介</span><span class="sxs-lookup"><span data-stu-id="4698e-197">.NET Standard introduction</span></span>](net-standard.md)
- [<span data-ttu-id="4698e-198">为服务器应用选择 .NET 5 或 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4698e-198">Choosing between .NET 5 and .NET Framework for server apps</span></span>](choosing-core-framework-server.md)
- [<span data-ttu-id="4698e-199">.NET Framework 指南</span><span class="sxs-lookup"><span data-stu-id="4698e-199">.NET Framework Guide</span></span>](../framework/index.yml)
- [<span data-ttu-id="4698e-200">C# 指南</span><span class="sxs-lookup"><span data-stu-id="4698e-200">C# Guide</span></span>](../csharp/index.yml)
- [<span data-ttu-id="4698e-201">F# 指南</span><span class="sxs-lookup"><span data-stu-id="4698e-201">F# Guide</span></span>](../fsharp/index.yml)
- [<span data-ttu-id="4698e-202">Visual Basic 指南</span><span class="sxs-lookup"><span data-stu-id="4698e-202">Visual Basic Guide</span></span>](../visual-basic/index.yml)
