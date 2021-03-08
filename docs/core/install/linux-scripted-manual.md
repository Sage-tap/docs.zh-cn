---
title: 在 Linux 上手动安装 .NET - .NET
description: 演示如何在 Linux 上无包管理器的情况下安装 .NET SDK 和 .NET Runtime。 使用安装脚本或手动提取二进制文件。
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 414246e472c3d58a6768311bd7a4635100f3b618
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105175"
---
# <a name="install-the-net-sdk-or-the-net-runtime-manually"></a><span data-ttu-id="b290a-104">手动安装 .NET SDK 或 .NET Runtime</span><span class="sxs-lookup"><span data-stu-id="b290a-104">Install the .NET SDK or the .NET Runtime manually</span></span>

<span data-ttu-id="b290a-105">.NET 在 Linux 上受支持，本文就将介绍如何使用安装脚本或通过提取二进制文件在 Linux 上安装 .NET。</span><span class="sxs-lookup"><span data-stu-id="b290a-105">.NET is supported on Linux and this article describes how to install .NET on Linux using the install script or by extracting the binaries.</span></span> <span data-ttu-id="b290a-106">有关支持内置包管理器的发行版列表，请参阅[在 Linux 上安装 .NET](linux.md)。</span><span class="sxs-lookup"><span data-stu-id="b290a-106">For a list of distributions that support the built-in package manager, see [Install .NET on Linux](linux.md).</span></span>

<span data-ttu-id="b290a-107">还可通过 Snap 安装 .NET。</span><span class="sxs-lookup"><span data-stu-id="b290a-107">You can also install .NET with snap.</span></span> <span data-ttu-id="b290a-108">有关详细信息，请参阅[通过 Snap 安装 .NET SDK 或 .NET Runtime](linux-snap.md)。</span><span class="sxs-lookup"><span data-stu-id="b290a-108">For more information, see [Install the .NET SDK or the .NET Runtime with Snap](linux-snap.md).</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="net-releases"></a><span data-ttu-id="b290a-109">.NET 版本</span><span class="sxs-lookup"><span data-stu-id="b290a-109">.NET releases</span></span>

<span data-ttu-id="b290a-110">下表列出了 .NET（和 .NET Core）版本：</span><span class="sxs-lookup"><span data-stu-id="b290a-110">The following table lists the .NET (and .NET Core) releases:</span></span>

| <span data-ttu-id="b290a-111">✔️ 受支持</span><span class="sxs-lookup"><span data-stu-id="b290a-111">✔️ Supported</span></span> | <span data-ttu-id="b290a-112">❌ 不受支持</span><span class="sxs-lookup"><span data-stu-id="b290a-112">❌ Unsupported</span></span> |
|-------------|---------------|
| <span data-ttu-id="b290a-113">5.0</span><span class="sxs-lookup"><span data-stu-id="b290a-113">5.0</span></span>         | <span data-ttu-id="b290a-114">3.0</span><span class="sxs-lookup"><span data-stu-id="b290a-114">3.0</span></span>           |
| <span data-ttu-id="b290a-115">3.1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="b290a-115">3.1 (LTS)</span></span>   | <span data-ttu-id="b290a-116">2.2</span><span class="sxs-lookup"><span data-stu-id="b290a-116">2.2</span></span>           |
| <span data-ttu-id="b290a-117">2.1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="b290a-117">2.1 (LTS)</span></span>   | <span data-ttu-id="b290a-118">2.0</span><span class="sxs-lookup"><span data-stu-id="b290a-118">2.0</span></span>           |
|             | <span data-ttu-id="b290a-119">1.1</span><span class="sxs-lookup"><span data-stu-id="b290a-119">1.1</span></span>           |
|             | <span data-ttu-id="b290a-120">1.0</span><span class="sxs-lookup"><span data-stu-id="b290a-120">1.0</span></span>           |

<span data-ttu-id="b290a-121">有关 .NET 版本的生命周期的详细信息，请参阅 [.NET Core 和 .NET 5 支持策略](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="b290a-121">For more information about the life cycle of .NET releases, see [.NET Core and .NET 5 Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span>

## <a name="dependencies"></a><span data-ttu-id="b290a-122">依赖项</span><span class="sxs-lookup"><span data-stu-id="b290a-122">Dependencies</span></span>

<span data-ttu-id="b290a-123">安装 .NET 时，例如[手动安装](#manual-install)时，可能不会安装特定依赖项。</span><span class="sxs-lookup"><span data-stu-id="b290a-123">It's possible that when you install .NET, specific dependencies may not be installed, such as when [manually installing](#manual-install).</span></span> <span data-ttu-id="b290a-124">下面的列表详细列出了 Microsoft 支持的 Linux 发行版以及可能需要安装的依赖项。</span><span class="sxs-lookup"><span data-stu-id="b290a-124">The following list details Linux distributions that are supported by Microsoft and have dependencies you may need to install.</span></span> <span data-ttu-id="b290a-125">更多信息，请查看发行版页面：</span><span class="sxs-lookup"><span data-stu-id="b290a-125">Check the distribution page for more information:</span></span>

- [<span data-ttu-id="b290a-126">Alpine</span><span class="sxs-lookup"><span data-stu-id="b290a-126">Alpine</span></span>](linux-alpine.md#dependencies)
- [<span data-ttu-id="b290a-127">Debian</span><span class="sxs-lookup"><span data-stu-id="b290a-127">Debian</span></span>](linux-debian.md#dependencies)
- [<span data-ttu-id="b290a-128">CentOS</span><span class="sxs-lookup"><span data-stu-id="b290a-128">CentOS</span></span>](linux-centos.md#dependencies)
- [<span data-ttu-id="b290a-129">Fedora</span><span class="sxs-lookup"><span data-stu-id="b290a-129">Fedora</span></span>](linux-fedora.md#dependencies)
- [<span data-ttu-id="b290a-130">RHEL</span><span class="sxs-lookup"><span data-stu-id="b290a-130">RHEL</span></span>](linux-rhel.md#dependencies)
- [<span data-ttu-id="b290a-131">SLES</span><span class="sxs-lookup"><span data-stu-id="b290a-131">SLES</span></span>](linux-sles.md#dependencies)
- [<span data-ttu-id="b290a-132">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="b290a-132">Ubuntu</span></span>](linux-ubuntu.md#dependencies)

<span data-ttu-id="b290a-133">有关依赖项的一般信息，请参阅[独立式 Linux 应用](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md)。</span><span class="sxs-lookup"><span data-stu-id="b290a-133">For generic information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

### <a name="rpm-dependencies"></a><span data-ttu-id="b290a-134">RPM 依赖项</span><span class="sxs-lookup"><span data-stu-id="b290a-134">RPM dependencies</span></span>

<span data-ttu-id="b290a-135">如果之前未列出发行版，并且该版本基于 RPM，则可能需要以下依赖项：</span><span class="sxs-lookup"><span data-stu-id="b290a-135">If your distribution wasn't previously listed, and is RPM-based, you may need the following dependencies:</span></span>

- <span data-ttu-id="b290a-136">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="b290a-136">krb5-libs</span></span>
- <span data-ttu-id="b290a-137">libicu</span><span class="sxs-lookup"><span data-stu-id="b290a-137">libicu</span></span>
- <span data-ttu-id="b290a-138">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="b290a-138">openssl-libs</span></span>

<span data-ttu-id="b290a-139">如果目标运行时环境的 OpenSSL 版本为1.1 或更高版本，则需要安装 compat-openssl10。</span><span class="sxs-lookup"><span data-stu-id="b290a-139">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

### <a name="deb-dependencies"></a><span data-ttu-id="b290a-140">DEB 依赖项</span><span class="sxs-lookup"><span data-stu-id="b290a-140">DEB dependencies</span></span>

<span data-ttu-id="b290a-141">如果之前未列出发行版，并且该版本基于 debian，则可能需要以下依赖项：</span><span class="sxs-lookup"><span data-stu-id="b290a-141">If your distribution wasn't previously listed, and is debian-based, you may need the following dependencies:</span></span>

- <span data-ttu-id="b290a-142">libc6</span><span class="sxs-lookup"><span data-stu-id="b290a-142">libc6</span></span>
- <span data-ttu-id="b290a-143">libgcc1</span><span class="sxs-lookup"><span data-stu-id="b290a-143">libgcc1</span></span>
- <span data-ttu-id="b290a-144">libgssapi-krb5-2</span><span class="sxs-lookup"><span data-stu-id="b290a-144">libgssapi-krb5-2</span></span>
- <span data-ttu-id="b290a-145">libicu67</span><span class="sxs-lookup"><span data-stu-id="b290a-145">libicu67</span></span>
- <span data-ttu-id="b290a-146">libssl1.1</span><span class="sxs-lookup"><span data-stu-id="b290a-146">libssl1.1</span></span>
- <span data-ttu-id="b290a-147">libstdc++6</span><span class="sxs-lookup"><span data-stu-id="b290a-147">libstdc++6</span></span>
- <span data-ttu-id="b290a-148">zlib1g</span><span class="sxs-lookup"><span data-stu-id="b290a-148">zlib1g</span></span>

### <a name="common-dependencies"></a><span data-ttu-id="b290a-149">通用依赖项</span><span class="sxs-lookup"><span data-stu-id="b290a-149">Common dependencies</span></span>

<span data-ttu-id="b290a-150">对于使用 System.Drawing.Common 程序集的 .NET 应用，还需要以下依赖项：</span><span class="sxs-lookup"><span data-stu-id="b290a-150">For .NET apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="b290a-151">libgdiplus（版本 6.0.1 或更高版本）</span><span class="sxs-lookup"><span data-stu-id="b290a-151">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="b290a-152">可以通过将 Mono 存储库添加到系统来安装最新版 libgdiplus。</span><span class="sxs-lookup"><span data-stu-id="b290a-152">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="b290a-153">有关详细信息，请参阅 <https://www.mono-project.com/download/stable/>。</span><span class="sxs-lookup"><span data-stu-id="b290a-153">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="b290a-154">脚本安装</span><span class="sxs-lookup"><span data-stu-id="b290a-154">Scripted install</span></span>

<span data-ttu-id="b290a-155">[dotnet-install 脚本](../tools/dotnet-install-script.md)用于 **SDK** 和 **运行时** 的自动化和非管理员安装。</span><span class="sxs-lookup"><span data-stu-id="b290a-155">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the **SDK** and **Runtime**.</span></span> <span data-ttu-id="b290a-156">可通过 <https://dot.net/v1/dotnet-install.sh> 下载脚本。</span><span class="sxs-lookup"><span data-stu-id="b290a-156">You can download the script from <https://dot.net/v1/dotnet-install.sh>.</span></span>

<span data-ttu-id="b290a-157">此脚本默认安装最新的 SDK [长期支持 (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 版本，即 .NET Core 3.1。</span><span class="sxs-lookup"><span data-stu-id="b290a-157">The script defaults to installing the latest SDK [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="b290a-158">若要安装当前版本（可能不是 (LTS) 版本），请使用 `-c Current` 参数。</span><span class="sxs-lookup"><span data-stu-id="b290a-158">To install the current release, which may not be an (LTS) version, use the `-c Current` parameter.</span></span>

```bash
./dotnet-install.sh -c Current
```

<span data-ttu-id="b290a-159">若要安装 .NET 运行时而非 SDK，请使用 `--runtime` 参数。</span><span class="sxs-lookup"><span data-stu-id="b290a-159">To install .NET Runtime instead of the SDK, use the `--runtime` parameter.</span></span>

```bash
./dotnet-install.sh -c Current --runtime aspnetcore
```

<span data-ttu-id="b290a-160">可以通过更改 `-c` 参数以指示特定版本来安装特定版本。</span><span class="sxs-lookup"><span data-stu-id="b290a-160">You can install a specific version by altering the `-c` parameter to indicate the specific version.</span></span> <span data-ttu-id="b290a-161">以下命令将安装 .NET SDK 5.0。</span><span class="sxs-lookup"><span data-stu-id="b290a-161">The following command installs .NET SDK 5.0.</span></span>

```bash
./dotnet-install.sh -c 5.0
```

<span data-ttu-id="b290a-162">有关详细信息，请参阅 [dotnet-install 脚本参考](../tools/dotnet-install-script.md)。</span><span class="sxs-lookup"><span data-stu-id="b290a-162">For more information, see [dotnet-install scripts reference](../tools/dotnet-install-script.md).</span></span>

## <a name="manual-install"></a><span data-ttu-id="b290a-163">手动安装</span><span class="sxs-lookup"><span data-stu-id="b290a-163">Manual install</span></span>

<!-- Note, this content is copied in macos.md. Any fixes should be applied there too, though content may be different -->

<span data-ttu-id="b290a-164">除了使用包管理器，还可以下载并手动安装 SDK 和运行时。</span><span class="sxs-lookup"><span data-stu-id="b290a-164">As an alternative to the package managers, you can download and manually install the SDK and runtime.</span></span> <span data-ttu-id="b290a-165">手动安装通常作为持续集成测试的一部分执行，或在不支持的 Linux 发行版上执行。</span><span class="sxs-lookup"><span data-stu-id="b290a-165">Manual install is commonly used as part of continuous integration testing or on an unsupported Linux distribution.</span></span> <span data-ttu-id="b290a-166">对于开发人员或用户，使用包管理器会更好。</span><span class="sxs-lookup"><span data-stu-id="b290a-166">For a developer or user, it's better to use a package manager.</span></span>

<span data-ttu-id="b290a-167">如果安装 .NET SDK，则无需安装相应的运行时。</span><span class="sxs-lookup"><span data-stu-id="b290a-167">If you install .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="b290a-168">首先，从以下站点之一下载 SDK 或运行时的二进制版本：</span><span class="sxs-lookup"><span data-stu-id="b290a-168">First, download a **binary** release for either the SDK or the runtime from one of the following sites:</span></span>

- <span data-ttu-id="b290a-169">✔️ [.NET 5.0 下载](https://dotnet.microsoft.com/download/dotnet/5.0)</span><span class="sxs-lookup"><span data-stu-id="b290a-169">✔️ [.NET 5.0 downloads](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>
- <span data-ttu-id="b290a-170">✔️ [.NET Core 3.1 下载](https://dotnet.microsoft.com/download/dotnet/3.1)</span><span class="sxs-lookup"><span data-stu-id="b290a-170">✔️ [.NET Core 3.1 downloads](https://dotnet.microsoft.com/download/dotnet/3.1)</span></span>
- <span data-ttu-id="b290a-171">✔️ [.NET Core 2.1 下载](https://dotnet.microsoft.com/download/dotnet/2.1)</span><span class="sxs-lookup"><span data-stu-id="b290a-171">✔️ [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet/2.1)</span></span>
- [<span data-ttu-id="b290a-172">所有 .NET Core 下载项</span><span class="sxs-lookup"><span data-stu-id="b290a-172">All .NET Core downloads</span></span>](https://dotnet.microsoft.com/download/dotnet)

<span data-ttu-id="b290a-173">接下来，提取已下载的文件并使用 `export` 命令设置 .NET 使用的变量，然后确保 .NET 在 PATH 中。</span><span class="sxs-lookup"><span data-stu-id="b290a-173">Next, extract the downloaded file and use the `export` command to set variables used by .NET and then ensure .NET is in PATH.</span></span>

<span data-ttu-id="b290a-174">若要提取运行时并使 .NET CLI 命令可用于终端，请先下载 .NET 二进制版本。</span><span class="sxs-lookup"><span data-stu-id="b290a-174">To extract the runtime and make the .NET CLI commands available at the terminal, first download a .NET binary release.</span></span> <span data-ttu-id="b290a-175">然后，打开终端并从保存文件的目录运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="b290a-175">Then, open a terminal and run the following commands from the directory where the file was saved.</span></span> <span data-ttu-id="b290a-176">根据下载内容，存档文件名称可能不同。</span><span class="sxs-lookup"><span data-stu-id="b290a-176">The archive file name may be different depending on what you downloaded.</span></span>

<span data-ttu-id="b290a-177">使用以下命令提取已下载的运行时或 SDK。</span><span class="sxs-lookup"><span data-stu-id="b290a-177">**Use the following commands to extract the runtime or SDK that you downloaded.**</span></span> <span data-ttu-id="b290a-178">请记得将 `DOTNET_FILE` 值更改为你的文件名：</span><span class="sxs-lookup"><span data-stu-id="b290a-178">Remember to change the `DOTNET_FILE` value to your file name:</span></span>

```bash
DOTNET_FILE=dotnet-sdk-5.0.102-linux-x64.tar.gz
export DOTNET_ROOT=$HOME/dotnet

mkdir -p "$DOTNET_ROOT" && tar zxf "$DOTNET_FILE" -C "$DOTNET_ROOT"

export PATH=$PATH:$DOTNET_ROOT
```

> [!TIP]
> <span data-ttu-id="b290a-179">前面的 `export` 命令只会使 .NET CLI 命令对运行它的终端会话可用。</span><span class="sxs-lookup"><span data-stu-id="b290a-179">The preceding `export` commands only make the .NET CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="b290a-180">你可以编辑 shell 配置文件，永久地添加这些命令。</span><span class="sxs-lookup"><span data-stu-id="b290a-180">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="b290a-181">Linux 提供了许多不同的 shell，每个都有不同的配置文件。</span><span class="sxs-lookup"><span data-stu-id="b290a-181">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="b290a-182">例如：</span><span class="sxs-lookup"><span data-stu-id="b290a-182">For example:</span></span>
>
> - <span data-ttu-id="b290a-183">**Bash Shell**：~/.bash_profile、~/.bashrc</span><span class="sxs-lookup"><span data-stu-id="b290a-183">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="b290a-184">**Korn Shell**：~/.kshrc 或 .profile</span><span class="sxs-lookup"><span data-stu-id="b290a-184">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="b290a-185">**Z Shell**：~/.zshrc 或 .zprofile</span><span class="sxs-lookup"><span data-stu-id="b290a-185">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="b290a-186">为 shell 编辑相应的源文件，并将 `:$HOME/dotnet` 添加到现有 `PATH` 语句的末尾。</span><span class="sxs-lookup"><span data-stu-id="b290a-186">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="b290a-187">如果不包含 `PATH` 语句，则使用 `export PATH=$PATH:$HOME/dotnet` 添加新行。</span><span class="sxs-lookup"><span data-stu-id="b290a-187">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="b290a-188">另外，将 `export DOTNET_ROOT=$HOME/dotnet` 添加至文件的末尾。</span><span class="sxs-lookup"><span data-stu-id="b290a-188">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

<span data-ttu-id="b290a-189">使用此方法可以将不同的版本安装到不同的位置，并明确选择应用程序要使用的对应版本。</span><span class="sxs-lookup"><span data-stu-id="b290a-189">This approach lets you install different versions into separate locations and choose explicitly which one to use by which application.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b290a-190">后续步骤</span><span class="sxs-lookup"><span data-stu-id="b290a-190">Next steps</span></span>

- [<span data-ttu-id="b290a-191">如何为 .NET CLI 启用 Tab 自动补全</span><span class="sxs-lookup"><span data-stu-id="b290a-191">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="b290a-192">教程：使用 Visual Studio Code 通过 .NET SDK 创建控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="b290a-192">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
