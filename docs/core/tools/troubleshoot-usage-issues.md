---
title: 排查 .NET 工具使用问题
description: 了解运行 .NET 工具出现的常见问题以及可能的解决方案。
author: kdollard
ms.topic: troubleshooting
ms.date: 02/14/2020
ms.openlocfilehash: 9cf0320ec5b5d6f317a4ef7f9052c0068b3ad8e5
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2021
ms.locfileid: "102104084"
---
# <a name="troubleshoot-net-tool-usage-issues"></a><span data-ttu-id="cc6e0-103">排查 .NET 工具使用问题</span><span class="sxs-lookup"><span data-stu-id="cc6e0-103">Troubleshoot .NET tool usage issues</span></span>

<span data-ttu-id="cc6e0-104">在尝试安装或运行 .NET 工具（可能是全局工具，也可能是本地工具）时，可能会遇到问题。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-104">You might come across issues when trying to install or run a .NET tool, which can be a global tool or a local tool.</span></span> <span data-ttu-id="cc6e0-105">本文介绍了常见的根本原因及一些可能的解决方案。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-105">This article describes the common root causes and some possible solutions.</span></span>

## <a name="installed-net-tool-fails-to-run"></a><span data-ttu-id="cc6e0-106">安装的 .NET 工具无法运行</span><span class="sxs-lookup"><span data-stu-id="cc6e0-106">Installed .NET tool fails to run</span></span>

<span data-ttu-id="cc6e0-107">当 .NET 工具无法运行时，你最可能遇到下述问题之一：</span><span class="sxs-lookup"><span data-stu-id="cc6e0-107">When a .NET tool fails to run, most likely you ran into one of the following issues:</span></span>

* <span data-ttu-id="cc6e0-108">找不到工具的可执行文件。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-108">The executable file for the tool wasn't found.</span></span>
* <span data-ttu-id="cc6e0-109">找不到 .NET 运行时的正确版本。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-109">The correct version of the .NET runtime wasn't found.</span></span>

### <a name="executable-file-not-found"></a><span data-ttu-id="cc6e0-110">找不到可执行文件</span><span class="sxs-lookup"><span data-stu-id="cc6e0-110">Executable file not found</span></span>

<span data-ttu-id="cc6e0-111">如果找不到可执行文件，则将看到如下所示的消息：</span><span class="sxs-lookup"><span data-stu-id="cc6e0-111">If the executable file isn't found, you'll see a message similar to the following:</span></span>

```console
Could not execute because the specified command or file was not found.
Possible reasons for this include:
  * You misspelled a built-in dotnet command.
  * You intended to execute a .NET program, but dotnet-xyz does not exist.
  * You intended to run a global tool, but a dotnet-prefixed executable with this name could not be found on the PATH.
```

<span data-ttu-id="cc6e0-112">可执行文件的名称决定了调用工具的方式。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-112">The name of the executable determines how you invoke the tool.</span></span> <span data-ttu-id="cc6e0-113">相关格式请参见下表：</span><span class="sxs-lookup"><span data-stu-id="cc6e0-113">The following table describes the format:</span></span>

| <span data-ttu-id="cc6e0-114">可执行文件名称的格式</span><span class="sxs-lookup"><span data-stu-id="cc6e0-114">Executable name format</span></span>  | <span data-ttu-id="cc6e0-115">调用格式</span><span class="sxs-lookup"><span data-stu-id="cc6e0-115">Invocation format</span></span>   |
|-------------------------|---------------------|
| `dotnet-<toolName>.exe` | `dotnet <toolName>` |
| `<toolName>.exe`        | `<toolName>`        |

* <span data-ttu-id="cc6e0-116">全局工具</span><span class="sxs-lookup"><span data-stu-id="cc6e0-116">Global tools</span></span>

  <span data-ttu-id="cc6e0-117">全局工具可安装在默认目录中，也可安装在特定位置中。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-117">Global tools can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="cc6e0-118">默认目录为：</span><span class="sxs-lookup"><span data-stu-id="cc6e0-118">The default directories are:</span></span>

  | <span data-ttu-id="cc6e0-119">(OS)</span><span class="sxs-lookup"><span data-stu-id="cc6e0-119">OS</span></span>          | <span data-ttu-id="cc6e0-120">路径</span><span class="sxs-lookup"><span data-stu-id="cc6e0-120">Path</span></span>                          |
  |-------------|-------------------------------|
  | <span data-ttu-id="cc6e0-121">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="cc6e0-121">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
  | <span data-ttu-id="cc6e0-122">Windows</span><span class="sxs-lookup"><span data-stu-id="cc6e0-122">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

  <span data-ttu-id="cc6e0-123">如果要尝试运行全局工具，请检查计算机上的 `PATH` 环境变量是否包含安装该全局工具的路径且可执行文件是否位于该路径中。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-123">If you're trying to run a global tool, check that the `PATH` environment variable on your machine contains the path where you installed the global tool and that the executable is in that path.</span></span>

  <span data-ttu-id="cc6e0-124">.NET CLI 在首次使用时尝试将默认位置添加到 PATH 环境变量。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-124">The .NET CLI tries to add the default location to the PATH environment variable on its first usage.</span></span> <span data-ttu-id="cc6e0-125">但是，在某些情况下，位置不会自动添加至 PATH：</span><span class="sxs-lookup"><span data-stu-id="cc6e0-125">However, there are some scenarios where the location might not be added to PATH automatically:</span></span>

  * <span data-ttu-id="cc6e0-126">如果使用的 Linux，并且已使用 .tar.gz 文件（而非 apt-get 或 rpm）安装 .NET SDK。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-126">If you're using Linux and you've installed the .NET SDK using *.tar.gz* files and not apt-get or rpm.</span></span>
  * <span data-ttu-id="cc6e0-127">如果使用的是 macOS 10.15“Catalina”或更高版本。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-127">If you're using macOS 10.15 "Catalina" or later versions.</span></span>
  * <span data-ttu-id="cc6e0-128">如果使用的是 macOS 10.14“Mojave”或更低版本，并且已使用 .tar.gz 文件（而非 .pkg）安装 .NET SDK 。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-128">If you're using macOS 10.14 "Mojave" or earlier versions, and you've installed the .NET SDK using *.tar.gz* files and not *.pkg*.</span></span>
  * <span data-ttu-id="cc6e0-129">如果已安装 .NET Core 3.0 SDK，并且已将 `DOTNET_ADD_GLOBAL_TOOLS_TO_PATH` 环境变量设置为 `false`。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-129">If you've installed the .NET Core 3.0 SDK and you've set the `DOTNET_ADD_GLOBAL_TOOLS_TO_PATH` environment variable to `false`.</span></span>
  * <span data-ttu-id="cc6e0-130">如果已安装 .NET Core 2.2 SDK 或更低版本，并且已将 `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` 环境变量设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-130">If you've installed .NET Core 2.2 SDK or earlier versions, and you've set the `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` environment variable to `true`.</span></span>

  <span data-ttu-id="cc6e0-131">在这些情况下，或者如果指定了 `--tool-path` 选项，则计算机上的 `PATH` 环境变量不会自动包含安装全局工具的路径。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-131">In these scenarios or if you specified the `--tool-path` option, the `PATH` environment variable on your machine doesn't automatically contain the path where you installed the global tool.</span></span> <span data-ttu-id="cc6e0-132">在这种情况下，使用 shell 提供的用于更新环境变量的任何方法，将工具位置（例如 `$HOME/.dotnet/tools`）追加到 `PATH` 环境变量。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-132">In that case, append the tool location (for example, `$HOME/.dotnet/tools`) to the `PATH` environment variable by using whatever method your shell provides for updating environment variables.</span></span> <span data-ttu-id="cc6e0-133">有关详细信息，请参阅 [.NET 工具](global-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-133">For more information, see [.NET tools](global-tools.md).</span></span>

* <span data-ttu-id="cc6e0-134">本地工具</span><span class="sxs-lookup"><span data-stu-id="cc6e0-134">Local tools</span></span>

  <span data-ttu-id="cc6e0-135">如果要尝试运行本地工具，请验证当前目录或其任何父目录中是否存在一个名为 dotnet-tools.json 的清单文件。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-135">If you're trying to run a local tool, verify that there's a manifest file called *dotnet-tools.json* in the current directory or any of its parent directories.</span></span> <span data-ttu-id="cc6e0-136">此文件还可位于项目文件夹层次结构中任意位置的 .config 文件夹下，而不是位于根文件夹中。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-136">This file can also live under a folder named *.config* anywhere in the project folder hierarchy, instead of the root folder.</span></span> <span data-ttu-id="cc6e0-137">如果存在 dotnet-tools.json，请将其打开，检查是否存在你要尝试运行的工具。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-137">If *dotnet-tools.json* exists, open it and check for the tool you're trying to run.</span></span> <span data-ttu-id="cc6e0-138">如果该文件不包含 `"isRoot": true` 的条目，则还要进一步检查文件层次结构中是否存在其他工具清单文件。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-138">If the file doesn't contain an entry for `"isRoot": true`, then also check further up the file hierarchy for additional tool manifest files.</span></span>

  <span data-ttu-id="cc6e0-139">如果要尝试运行已通过指定的路径安装的 .NET 工具，则需要在使用该工具时包含该路径。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-139">If you're trying to run a .NET tool that was installed with a specified path, you need to include that path when using the tool.</span></span> <span data-ttu-id="cc6e0-140">下面是使用安装了工具路径的工具的示例：</span><span class="sxs-lookup"><span data-stu-id="cc6e0-140">An example of using a tool-path installed tool is:</span></span>

  ```console
  ..\<toolDirectory>\dotnet-<toolName>
  ```

### <a name="runtime-not-found"></a><span data-ttu-id="cc6e0-141">找不到运行时</span><span class="sxs-lookup"><span data-stu-id="cc6e0-141">Runtime not found</span></span>

<span data-ttu-id="cc6e0-142">.NET 工具是[依赖框架的应用程序](../deploying/index.md#publish-framework-dependent)，也就是说它们依赖于计算机上安装的 .NET 运行时。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-142">.NET tools are [framework-dependent applications](../deploying/index.md#publish-framework-dependent), which means they rely on a .NET runtime installed on your machine.</span></span> <span data-ttu-id="cc6e0-143">如果找不到所需的运行时，则遵循常规的 .NET 运行时前滚规则，例如：</span><span class="sxs-lookup"><span data-stu-id="cc6e0-143">If the expected runtime isn't found, they follow normal .NET runtime roll-forward rules such as:</span></span>

* <span data-ttu-id="cc6e0-144">应用程序前滚至指定的主要版本和次要版本的最高修补程序版本。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-144">An application rolls forward to the highest patch release of the specified major and minor version.</span></span>
* <span data-ttu-id="cc6e0-145">如果主要版本号和次要版本号没有匹配的运行时，则使用下一个较高的次要版本。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-145">If there's no matching runtime with a matching major and minor version number, the next higher minor version is used.</span></span>
* <span data-ttu-id="cc6e0-146">前滚不会发生在运行时的预览版之间，也不会发生在预览版和发行版之间。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-146">Roll forward doesn't occur between preview versions of the runtime or between preview versions and release versions.</span></span> <span data-ttu-id="cc6e0-147">因此，使用预览版创建的 .NET 工具必须由作者重新生成和重新发布，再重新安装。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-147">So, .NET tools created using preview versions must be rebuilt and republished by the author and reinstalled.</span></span>

<span data-ttu-id="cc6e0-148">在下面两种常见场景中，默认不进行前滚：</span><span class="sxs-lookup"><span data-stu-id="cc6e0-148">Roll-forward won't occur by default in two common scenarios:</span></span>

* <span data-ttu-id="cc6e0-149">只有运行时的较低版本可用。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-149">Only lower versions of the runtime are available.</span></span> <span data-ttu-id="cc6e0-150">前滚仅选择运行时的较高版本。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-150">Roll-forward only selects later versions of the runtime.</span></span>
* <span data-ttu-id="cc6e0-151">只有运行时的较高版本可用。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-151">Only higher major versions of the runtime are available.</span></span> <span data-ttu-id="cc6e0-152">前滚不跨越主要版本边界。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-152">Roll-forward doesn't cross major version boundaries.</span></span>

<span data-ttu-id="cc6e0-153">如果应用程序找不到合适的运行时，则它无法运行并报告错误。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-153">If an application can't find an appropriate runtime, it fails to run and reports an error.</span></span>

<span data-ttu-id="cc6e0-154">若要查看计算机上安装了哪些 .NET 运行时，可使用以下命令之一：</span><span class="sxs-lookup"><span data-stu-id="cc6e0-154">You can find out which .NET runtimes are installed on your machine using one of the following commands:</span></span>

```dotnetcli
dotnet --list-runtimes
dotnet --info
```

<span data-ttu-id="cc6e0-155">如果你认为此工具应支持你当前安装的运行时版本，可联系工具作者，询问他们是否可更新版本号或实现多目标。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-155">If you think the tool should support the runtime version you currently have installed, you can contact the tool author and see if they can update the version number or multi-target.</span></span> <span data-ttu-id="cc6e0-156">在工具作者编译其工具包并使用更新后的版本号将其重新发布到 NuGet 之后，你可更新你的副本。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-156">Once they've recompiled and republished their tool package to NuGet with an updated version number, you can update your copy.</span></span> <span data-ttu-id="cc6e0-157">虽然这种情况不会发生，但最快捷的解决方案是安装适合你要尝试运行的工具的运行时版本。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-157">While that doesn't happen, the quickest solution for you is to install a version of the runtime that would work with the tool you're trying to run.</span></span> <span data-ttu-id="cc6e0-158">若要下载特定的 .NET 运行时版本，请访问 [.NET 下载页](https://dotnet.microsoft.com/download/dotnet)。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-158">To download a specific .NET runtime version, visit the [.NET download page](https://dotnet.microsoft.com/download/dotnet).</span></span>

<span data-ttu-id="cc6e0-159">如果将 .NET SDK 安装到非默认位置，则需要将环境变量 `DOTNET_ROOT` 设置到包含 `dotnet` 可执行文件的目录。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-159">If you install the .NET SDK to a non-default location, you need to set the environment variable `DOTNET_ROOT` to the directory that contains the `dotnet` executable.</span></span>

## <a name="net-tool-installation-fails"></a><span data-ttu-id="cc6e0-160">.NET 工具安装失败</span><span class="sxs-lookup"><span data-stu-id="cc6e0-160">.NET tool installation fails</span></span>

<span data-ttu-id="cc6e0-161">.NET 全局或本地工具安装失败的原因有很多。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-161">There are a number of reasons the installation of a .NET global or local tool may fail.</span></span> <span data-ttu-id="cc6e0-162">当工具安装失败时，你将看到如下所示的消息：</span><span class="sxs-lookup"><span data-stu-id="cc6e0-162">When the tool installation fails, you'll see a message similar to the following one:</span></span>

```console
Tool '{0}' failed to install. This failure may have been caused by:

* You are attempting to install a preview release and did not use the --version option to specify the version.
* A package by this name was found, but it was not a .NET tool.
* The required NuGet feed cannot be accessed, perhaps because of an Internet connection problem.
* You mistyped the name of the tool.

For more reasons, including package naming enforcement, visit https://aka.ms/failure-installing-tool
```

<span data-ttu-id="cc6e0-163">为帮助诊断这些失败情况，会随同之前的消息直接向用户显示 NuGet 消息。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-163">To help diagnose these failures, NuGet messages are shown directly to the user, along with the previous message.</span></span> <span data-ttu-id="cc6e0-164">NuGet 消息可帮助你确定问题。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-164">The NuGet message may help you identify the problem.</span></span>

### <a name="package-naming-enforcement"></a><span data-ttu-id="cc6e0-165">包命名强制</span><span class="sxs-lookup"><span data-stu-id="cc6e0-165">Package naming enforcement</span></span>

<span data-ttu-id="cc6e0-166">Microsoft 针对工具的包 ID 更改了相关指导，导致没法用预测出的名称找到很多工具。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-166">Microsoft has changed its guidance on the Package ID for tools, resulting in a number of tools not being found with the predicted name.</span></span> <span data-ttu-id="cc6e0-167">新的指导是所有 Microsoft 工具均附上“Microsoft”这一前缀。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-167">The new guidance is that all Microsoft tools be prefixed with "Microsoft."</span></span> <span data-ttu-id="cc6e0-168">此前缀已预留，仅用于使用 Microsoft 授权证书签名的包。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-168">This prefix is reserved and can only be used for packages signed with a Microsoft authorized certificate.</span></span>

<span data-ttu-id="cc6e0-169">在过渡期间，一些 Microsoft 工具将采用包 ID 的旧格式，而另外一些将采用新格式：</span><span class="sxs-lookup"><span data-stu-id="cc6e0-169">During the transition, some Microsoft tools will have the old form of the package ID, while others will have the new form:</span></span>

```dotnetcli
dotnet tool install -g Microsoft.<toolName>
dotnet tool install -g <toolName>
```

<span data-ttu-id="cc6e0-170">更新包 ID 后，你将需要更改到新的包 ID 以获取最新更新。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-170">As package IDs are updated, you'll need to change to the new package ID to get the latest updates.</span></span> <span data-ttu-id="cc6e0-171">带简化工具名称的包将遭到弃用。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-171">Packages with the simplified tool name will be deprecated.</span></span>

### <a name="preview-releases"></a><span data-ttu-id="cc6e0-172">预览版本</span><span class="sxs-lookup"><span data-stu-id="cc6e0-172">Preview releases</span></span>

* <span data-ttu-id="cc6e0-173">你正在尝试安装预览版本，但未使用 `--version` 选项来指定该版本。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-173">You're attempting to install a preview release and didn't use the `--version` option to specify the version.</span></span>

<span data-ttu-id="cc6e0-174">必须用名称的一部分指定处于预览状态的 .NET 工具，这样才能指示它们现为预览版。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-174">.NET tools that are in preview must be specified with a portion of the name to indicate that they are in preview.</span></span> <span data-ttu-id="cc6e0-175">不需要包含整个预览版。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-175">You don't need to include the entire preview.</span></span> <span data-ttu-id="cc6e0-176">假定版本号都采用预期的格式，则你可使用与下例类似的内容：</span><span class="sxs-lookup"><span data-stu-id="cc6e0-176">Assuming the version numbers are in the expected format, you can use something like the following example:</span></span>

```dotnetcli
dotnet tool install -g --version 1.1.0-pre <toolName>
```

### <a name="package-isnt-a-net-tool"></a><span data-ttu-id="cc6e0-177">包不是 .NET 工具</span><span class="sxs-lookup"><span data-stu-id="cc6e0-177">Package isn't a .NET tool</span></span>

* <span data-ttu-id="cc6e0-178">已按此名称找到 NuGet 包，但它不是 .NET 工具。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-178">A NuGet package by this name was found, but it wasn't a .NET tool.</span></span>

<span data-ttu-id="cc6e0-179">如果尝试安装的 NuGet 包是常规 NuGet 包而非 .NET 工具，你将看到如下所示的错误：</span><span class="sxs-lookup"><span data-stu-id="cc6e0-179">If you try to install a NuGet package that is a regular NuGet package and not a .NET tool, you'll see an error similar to the following:</span></span>

> <span data-ttu-id="cc6e0-180">NU1212：`<ToolName>` 的项目包组合无效。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-180">NU1212: Invalid project-package combination for `<ToolName>`.</span></span> <span data-ttu-id="cc6e0-181">DotnetToolReference 项目类型仅可包含 DotnetTool 类型的引用。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-181">DotnetToolReference project style can only contain references of the DotnetTool type.</span></span>

### <a name="nuget-feed-cant-be-accessed"></a><span data-ttu-id="cc6e0-182">无法访问 NuGet 源</span><span class="sxs-lookup"><span data-stu-id="cc6e0-182">NuGet feed can't be accessed</span></span>

* <span data-ttu-id="cc6e0-183">无法访问必需的 NuGet 源，这可能是由 Internet 连接问题造成的。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-183">The required NuGet feed can't be accessed, perhaps because of an Internet connection problem.</span></span>

<span data-ttu-id="cc6e0-184">需要访问包含工具包的 NuGet 源才能安装工具。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-184">Tool installation requires access to the NuGet feed that contains the tool package.</span></span> <span data-ttu-id="cc6e0-185">如果源不可用，则安装将失败。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-185">It fails if the feed isn't available.</span></span> <span data-ttu-id="cc6e0-186">可使用 `nuget.config` 修改源、请求特定的 `nuget.config` 文件，也可使用 `--add-source` 开关指定其他源。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-186">You can alter feeds with `nuget.config`, request a specific `nuget.config` file, or specify additional feeds with the `--add-source` switch.</span></span> <span data-ttu-id="cc6e0-187">默认情况下，对于无法连接的任何源，NuGet 都将引发错误。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-187">By default, NuGet throws an error for any feed that can't connect.</span></span> <span data-ttu-id="cc6e0-188">标志 `--ignore-failed-sources` 可跳过这些不可访问的源。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-188">The flag `--ignore-failed-sources` can skip these non-reachable sources.</span></span>

### <a name="package-id-incorrect"></a><span data-ttu-id="cc6e0-189">包 ID 错误</span><span class="sxs-lookup"><span data-stu-id="cc6e0-189">Package ID incorrect</span></span>

* <span data-ttu-id="cc6e0-190">工具的名称拼写错误。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-190">You mistyped the name of the tool.</span></span>

<span data-ttu-id="cc6e0-191">常见的失败原因是工具名称不正确。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-191">A common reason for failure is that the tool name isn't correct.</span></span> <span data-ttu-id="cc6e0-192">原因可能是拼写错误，或者工具已移动或已被弃用。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-192">This can happen because of mistyping, or because the tool has moved or been deprecated.</span></span> <span data-ttu-id="cc6e0-193">对于 NuGet.org 上的工具，确保名称正确的一种方式是在 NuGet.org 处搜索该工具并复制安装命令。</span><span class="sxs-lookup"><span data-stu-id="cc6e0-193">For tools on NuGet.org, one way to ensure you have the name correct is to search for the tool at NuGet.org and copy the installation command.</span></span>

## <a name="see-also"></a><span data-ttu-id="cc6e0-194">请参阅</span><span class="sxs-lookup"><span data-stu-id="cc6e0-194">See also</span></span>

* [<span data-ttu-id="cc6e0-195">.NET 工具</span><span class="sxs-lookup"><span data-stu-id="cc6e0-195">.NET tools</span></span>](global-tools.md)
