---
title: dotnet-gcdump 诊断工具 - .NET CLI
description: 了解如何安装和使用 dotnet-gcdump CLI 工具，以使用 .NET EventPipe 收集实时 .NET 进程的 GC（垃圾回收器）转储。
ms.date: 11/17/2020
ms.openlocfilehash: fe7772eed642daadbd1754627751f58d0ab57b8e
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188564"
---
# <a name="heap-analysis-tool-dotnet-gcdump"></a><span data-ttu-id="de4f4-103">堆分析工具 (dotnet-gcdump)</span><span class="sxs-lookup"><span data-stu-id="de4f4-103">Heap analysis tool (dotnet-gcdump)</span></span>

<span data-ttu-id="de4f4-104">**本文适用于：** ✔️ .NET Core 3.1 SDK 及更高版本</span><span class="sxs-lookup"><span data-stu-id="de4f4-104">**This article applies to:** ✔️ .NET Core 3.1 SDK and later versions</span></span>

## <a name="install"></a><span data-ttu-id="de4f4-105">安装</span><span class="sxs-lookup"><span data-stu-id="de4f4-105">Install</span></span>

<span data-ttu-id="de4f4-106">可采用两种方法来下载和安装 `dotnet-gcdump`：</span><span class="sxs-lookup"><span data-stu-id="de4f4-106">There are two ways to download and install `dotnet-gcdump`:</span></span>

- <span data-ttu-id="de4f4-107">**dotnet 全局工具：**</span><span class="sxs-lookup"><span data-stu-id="de4f4-107">**dotnet global tool:**</span></span>

  <span data-ttu-id="de4f4-108">若要安装最新版 `dotnet-gcdump` [NuGet 包](https://www.nuget.org/packages/dotnet-gcdump)，请使用 [dotnet tool install](../tools/dotnet-tool-install.md) 命令：</span><span class="sxs-lookup"><span data-stu-id="de4f4-108">To install the latest release version of the `dotnet-gcdump` [NuGet package](https://www.nuget.org/packages/dotnet-gcdump), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

  ```dotnetcli
  dotnet tool install --global dotnet-gcdump
  ```

- <span data-ttu-id="de4f4-109">**直接下载：**</span><span class="sxs-lookup"><span data-stu-id="de4f4-109">**Direct download:**</span></span>

  <span data-ttu-id="de4f4-110">下载与平台相匹配的工具可执行文件：</span><span class="sxs-lookup"><span data-stu-id="de4f4-110">Download the tool executable that matches your platform:</span></span>

  | <span data-ttu-id="de4f4-111">(OS)</span><span class="sxs-lookup"><span data-stu-id="de4f4-111">OS</span></span>  | <span data-ttu-id="de4f4-112">平台</span><span class="sxs-lookup"><span data-stu-id="de4f4-112">Platform</span></span> |
  | --- | -------- |
  | <span data-ttu-id="de4f4-113">Windows</span><span class="sxs-lookup"><span data-stu-id="de4f4-113">Windows</span></span> | <span data-ttu-id="de4f4-114">[x86](https://aka.ms/dotnet-gcdump/win-x86) \| [x64](https://aka.ms/dotnet-gcdump/win-x64) \| [arm](https://aka.ms/dotnet-gcdump/win-arm) \| [arm-x64](https://aka.ms/dotnet-gcdump/win-arm64)</span><span class="sxs-lookup"><span data-stu-id="de4f4-114">[x86](https://aka.ms/dotnet-gcdump/win-x86) \| [x64](https://aka.ms/dotnet-gcdump/win-x64) \| [arm](https://aka.ms/dotnet-gcdump/win-arm) \| [arm-x64](https://aka.ms/dotnet-gcdump/win-arm64)</span></span> |
  | <span data-ttu-id="de4f4-115">macOS</span><span class="sxs-lookup"><span data-stu-id="de4f4-115">macOS</span></span>   | [<span data-ttu-id="de4f4-116">x64</span><span class="sxs-lookup"><span data-stu-id="de4f4-116">x64</span></span>](https://aka.ms/dotnet-gcdump/osx-x64) |
  | <span data-ttu-id="de4f4-117">Linux</span><span class="sxs-lookup"><span data-stu-id="de4f4-117">Linux</span></span>   | <span data-ttu-id="de4f4-118">[x64](https://aka.ms/dotnet-gcdump/linux-x64) \| [arm](https://aka.ms/dotnet-gcdump/linux-arm) \| [arm64](https://aka.ms/dotnet-gcdump/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-gcdump/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-gcdump/linux-musl-arm64)</span><span class="sxs-lookup"><span data-stu-id="de4f4-118">[x64](https://aka.ms/dotnet-gcdump/linux-x64) \| [arm](https://aka.ms/dotnet-gcdump/linux-arm) \| [arm64](https://aka.ms/dotnet-gcdump/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-gcdump/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-gcdump/linux-musl-arm64)</span></span> |

> [!NOTE]
> <span data-ttu-id="de4f4-119">若要在 x86 应用上使用 `dotnet-gcdump`，需要使用相应的 x86 版本的工具。</span><span class="sxs-lookup"><span data-stu-id="de4f4-119">To use `dotnet-gcdump` on an x86 app, you need a corresponding x86 version of the tool.</span></span>

## <a name="synopsis"></a><span data-ttu-id="de4f4-120">摘要</span><span class="sxs-lookup"><span data-stu-id="de4f4-120">Synopsis</span></span>

```console
dotnet-gcdump [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="de4f4-121">说明</span><span class="sxs-lookup"><span data-stu-id="de4f4-121">Description</span></span>

<span data-ttu-id="de4f4-122">`dotnet-gcdump` 全局工具使用 [EventPipe](./eventpipe.md) 收集实时 .NET 进程的 GC（垃圾回收器）转储。</span><span class="sxs-lookup"><span data-stu-id="de4f4-122">The `dotnet-gcdump` global tool collects GC (Garbage Collector) dumps of live .NET processes using [EventPipe](./eventpipe.md).</span></span> <span data-ttu-id="de4f4-123">创建 GC 转储时需要在目标进程中触发 GC、开启特殊事件并从事件流中重新生成对象根图。</span><span class="sxs-lookup"><span data-stu-id="de4f4-123">GC dumps are created by triggering a GC in the target process, turning on special events, and regenerating the graph of object roots from the event stream.</span></span> <span data-ttu-id="de4f4-124">此过程允许在进程运行时以最小的开销收集 GC 转储。</span><span class="sxs-lookup"><span data-stu-id="de4f4-124">This process allows for GC dumps to be collected while the process is running and with minimal overhead.</span></span> <span data-ttu-id="de4f4-125">这些转储对于以下几种情况非常有用：</span><span class="sxs-lookup"><span data-stu-id="de4f4-125">These dumps are useful for several scenarios:</span></span>

- <span data-ttu-id="de4f4-126">比较多个时间点堆上的对象数。</span><span class="sxs-lookup"><span data-stu-id="de4f4-126">Comparing the number of objects on the heap at several points in time.</span></span>
- <span data-ttu-id="de4f4-127">分析对象的根（回答诸如“还有哪些引用此类型的内容？”等问题）。</span><span class="sxs-lookup"><span data-stu-id="de4f4-127">Analyzing roots of objects (answering questions like, "what still has a reference to this type?").</span></span>
- <span data-ttu-id="de4f4-128">收集有关堆上的对象计数的常规统计信息。</span><span class="sxs-lookup"><span data-stu-id="de4f4-128">Collecting general statistics about the counts of objects on the heap.</span></span>

### <a name="view-the-gc-dump-captured-from-dotnet-gcdump"></a><span data-ttu-id="de4f4-129">查看从 dotnet-gcdump 捕获的 GC 转储</span><span class="sxs-lookup"><span data-stu-id="de4f4-129">View the GC dump captured from dotnet-gcdump</span></span>

<span data-ttu-id="de4f4-130">在 Windows 上，可以在 [PerfView](https://github.com/microsoft/perfview) 中查看 `.gcdump` 文件，以便进行分析，也可在 Visual Studio 中查看该文件。</span><span class="sxs-lookup"><span data-stu-id="de4f4-130">On Windows, `.gcdump` files can be viewed in [PerfView](https://github.com/microsoft/perfview) for analysis or in Visual Studio.</span></span> <span data-ttu-id="de4f4-131">目前，无法在非 Windows 平台上打开 `.gcdump`。</span><span class="sxs-lookup"><span data-stu-id="de4f4-131">Currently, There is no way of opening a `.gcdump` on non-Windows platforms.</span></span>

<span data-ttu-id="de4f4-132">可以收集多个 `.gcdump`，并在 Visual Studio 中同时打开它们以获取比较体验。</span><span class="sxs-lookup"><span data-stu-id="de4f4-132">You can collect multiple `.gcdump`s and open them simultaneously in Visual Studio to get a comparison experience.</span></span>

## <a name="options"></a><span data-ttu-id="de4f4-133">选项</span><span class="sxs-lookup"><span data-stu-id="de4f4-133">Options</span></span>

- **`--version`**

  <span data-ttu-id="de4f4-134">显示 `dotnet-gcdump` 实用工具的版本。</span><span class="sxs-lookup"><span data-stu-id="de4f4-134">Displays the version of the `dotnet-gcdump` utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="de4f4-135">显示命令行帮助。</span><span class="sxs-lookup"><span data-stu-id="de4f4-135">Shows command-line help.</span></span>

## `dotnet-gcdump collect`

<span data-ttu-id="de4f4-136">从当前正在运行的进程中收集 GC 转储。</span><span class="sxs-lookup"><span data-stu-id="de4f4-136">Collects a GC dump from a currently running process.</span></span>

> [!WARNING]
> <span data-ttu-id="de4f4-137">为了遍历 GC 堆，此命令将触发第 2 代（完整）垃圾回收，这可能会使运行时长时间挂起，尤其是在 GC 堆很大的情况下。</span><span class="sxs-lookup"><span data-stu-id="de4f4-137">To walk the GC heap, this command triggers a generation 2 (full) garbage collection, which can suspend the runtime for a long time, especially when the GC heap is large.</span></span> <span data-ttu-id="de4f4-138">如果 GC 堆很大，请不要在对性能要求高的环境中使用此命令。</span><span class="sxs-lookup"><span data-stu-id="de4f4-138">Don't use this command in performance-sensitive environments when the GC heap is large.</span></span>

### <a name="synopsis"></a><span data-ttu-id="de4f4-139">摘要</span><span class="sxs-lookup"><span data-stu-id="de4f4-139">Synopsis</span></span>

```console
dotnet-gcdump collect [-h|--help] [-p|--process-id <pid>] [-o|--output <gcdump-file-path>] [-v|--verbose] [-t|--timeout <timeout>] [-n|--name <name>]
```

### <a name="options"></a><span data-ttu-id="de4f4-140">选项</span><span class="sxs-lookup"><span data-stu-id="de4f4-140">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="de4f4-141">显示命令行帮助。</span><span class="sxs-lookup"><span data-stu-id="de4f4-141">Shows command-line help.</span></span>

- **`-p|--process-id <pid>`**

  <span data-ttu-id="de4f4-142">可从中收集 GC 转储的进程 ID。</span><span class="sxs-lookup"><span data-stu-id="de4f4-142">The process ID to collect the GC dump from.</span></span>

- **`-o|--output <gcdump-file-path>`**

  <span data-ttu-id="de4f4-143">应写入收集 GC 转储的路径。</span><span class="sxs-lookup"><span data-stu-id="de4f4-143">The path where collected GC dumps should be written.</span></span> <span data-ttu-id="de4f4-144">默认为 .\\YYYYMMDD\_HHMMSS\_\<pid>.gcdump。</span><span class="sxs-lookup"><span data-stu-id="de4f4-144">Defaults to *.\\YYYYMMDD\_HHMMSS\_\<pid>.gcdump*.</span></span>

- **`-v|--verbose`**

  <span data-ttu-id="de4f4-145">收集 GC 转储时输出日志。</span><span class="sxs-lookup"><span data-stu-id="de4f4-145">Output the log while collecting the GC dump.</span></span>

- **`-t|--timeout <timeout>`**

  <span data-ttu-id="de4f4-146">如果收集 GC 转储的时间超过了此秒数，则放弃收集。</span><span class="sxs-lookup"><span data-stu-id="de4f4-146">Give up on collecting the GC dump if it takes longer than this many seconds.</span></span> <span data-ttu-id="de4f4-147">默认值为 30。</span><span class="sxs-lookup"><span data-stu-id="de4f4-147">The default value is 30.</span></span>

- **`-n|--name <name>`**

  <span data-ttu-id="de4f4-148">可从中收集 GC 转储的进程的名称。</span><span class="sxs-lookup"><span data-stu-id="de4f4-148">The name of the process to collect the GC dump from.</span></span>

> [!NOTE]
> <span data-ttu-id="de4f4-149">在 Linux 和 macOS 上，此命令需要目标应用程序和 `dotnet-gcdump` 使用同一 `TMPDIR` 环境变量。</span><span class="sxs-lookup"><span data-stu-id="de4f4-149">On Linux and macOS, this command expects the target application and `dotnet-gcdump` to share the same `TMPDIR` environment variable.</span></span> <span data-ttu-id="de4f4-150">否则，该命令将超时。</span><span class="sxs-lookup"><span data-stu-id="de4f4-150">Otherwise, the command will time out.</span></span>

> [!NOTE]
> <span data-ttu-id="de4f4-151">若要使用 `dotnet-gcdump` 收集 GC 转储，需要以与运行目标进程的用户相同的用户身份或以根身份运行。</span><span class="sxs-lookup"><span data-stu-id="de4f4-151">To collect a GC dump using `dotnet-gcdump`, it needs to be run as the same user as the user running target process or as root.</span></span> <span data-ttu-id="de4f4-152">否则，该工具将无法与目标进程建立连接。</span><span class="sxs-lookup"><span data-stu-id="de4f4-152">Otherwise, the tool will fail to establish a connection with the target process.</span></span>

## `dotnet-gcdump ps`

<span data-ttu-id="de4f4-153">列出可为其收集 GC 转储的 dotnet 进程。</span><span class="sxs-lookup"><span data-stu-id="de4f4-153">Lists the dotnet processes that GC dumps can be collected for.</span></span>

### <a name="synopsis"></a><span data-ttu-id="de4f4-154">摘要</span><span class="sxs-lookup"><span data-stu-id="de4f4-154">Synopsis</span></span>

```console
dotnet-gcdump ps
```

## `dotnet-gcdump report <gcdump_filename>`

<span data-ttu-id="de4f4-155">从以前生成的 GC 转储或从正在运行的进程生成报表，并将其写入 `stdout`。</span><span class="sxs-lookup"><span data-stu-id="de4f4-155">Generate a report from a previously generated GC dump or from a running process, and write to `stdout`.</span></span>

### <a name="synopsis"></a><span data-ttu-id="de4f4-156">摘要</span><span class="sxs-lookup"><span data-stu-id="de4f4-156">Synopsis</span></span>

```console
dotnet-gcdump report [-h|--help] [-p|--process-id <pid>] [-t|--report-type <HeapStat>]
```

### <a name="options"></a><span data-ttu-id="de4f4-157">选项</span><span class="sxs-lookup"><span data-stu-id="de4f4-157">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="de4f4-158">显示命令行帮助。</span><span class="sxs-lookup"><span data-stu-id="de4f4-158">Shows command-line help.</span></span>

- **`-p|--process-id <pid>`**

  <span data-ttu-id="de4f4-159">可从中收集 GC 转储的进程 ID。</span><span class="sxs-lookup"><span data-stu-id="de4f4-159">The process ID to collect the GC dump from.</span></span>

- **`-t|--report-type <HeapStat>`**

  <span data-ttu-id="de4f4-160">可生成报表的类型。</span><span class="sxs-lookup"><span data-stu-id="de4f4-160">The type of report to generate.</span></span> <span data-ttu-id="de4f4-161">可用选项：heapstat（默认）。</span><span class="sxs-lookup"><span data-stu-id="de4f4-161">Available options: heapstat (default).</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="de4f4-162">疑难解答</span><span class="sxs-lookup"><span data-stu-id="de4f4-162">Troubleshoot</span></span>

- <span data-ttu-id="de4f4-163">gcdump 中没有类型信息。</span><span class="sxs-lookup"><span data-stu-id="de4f4-163">There is no type information in the gcdump.</span></span>

   <span data-ttu-id="de4f4-164">在 .NET Core 3.1 之前，存在一个问题，即使用 EventPipe 调用 gcdump 时，gcdump 之间的类型缓存没有清除。</span><span class="sxs-lookup"><span data-stu-id="de4f4-164">Prior to .NET Core 3.1, there was an issue where a type cache was not cleared between gcdumps when they were invoked with EventPipe.</span></span> <span data-ttu-id="de4f4-165">这导致确定类型信息所需的事件未发送给第二个和后续 gcdump。</span><span class="sxs-lookup"><span data-stu-id="de4f4-165">This resulted in the events needed for determining type information not being sent for the second and subsequent gcdumps.</span></span> <span data-ttu-id="de4f4-166">此问题已在 .NET Core 3.1-preview2 中得以修复。</span><span class="sxs-lookup"><span data-stu-id="de4f4-166">This was fixed in .NET Core 3.1-preview2.</span></span>

- <span data-ttu-id="de4f4-167">COM 和静态类型不在 GC 转储中。</span><span class="sxs-lookup"><span data-stu-id="de4f4-167">COM and static types aren't in the GC dump.</span></span>

   <span data-ttu-id="de4f4-168">在 .NET Core 3.1-preview2 之前，存在一个问题，即通过 EventPipe 调用 GC 转储时，不会发送静态和 COM 类型。</span><span class="sxs-lookup"><span data-stu-id="de4f4-168">Prior to .NET Core 3.1-preview2, there was an issue where static and COM types weren't sent when the GC dump was invoked via EventPipe.</span></span> <span data-ttu-id="de4f4-169">此问题已在 .NET Core 3.1-preview2 中得以修复。</span><span class="sxs-lookup"><span data-stu-id="de4f4-169">This has been fixed in .NET Core 3.1-preview2.</span></span>
