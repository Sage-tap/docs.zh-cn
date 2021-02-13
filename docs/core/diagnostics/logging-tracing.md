---
title: 日志记录和跟踪 - .NET Core
description: .NET Core 日志记录和跟踪简介。
ms.date: 10/12/2020
ms.openlocfilehash: a8c6d82ddb7bc3f8b4cc9eae9dd7aaf65732a0b8
ms.sourcegitcommit: 4df8e005c074ceb1f978f007b222fe253be2baf3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/04/2021
ms.locfileid: "99548390"
---
# <a name="net-core-logging-and-tracing"></a><span data-ttu-id="a592c-103">.NET Core 日志记录和跟踪</span><span class="sxs-lookup"><span data-stu-id="a592c-103">.NET Core logging and tracing</span></span>

<span data-ttu-id="a592c-104">日志记录和跟踪实际上是同一技术的两个名称。</span><span class="sxs-lookup"><span data-stu-id="a592c-104">Logging and tracing are really two names for the same technique.</span></span> <span data-ttu-id="a592c-105">这种简单的技术从计算机早期就开始使用了。</span><span class="sxs-lookup"><span data-stu-id="a592c-105">The simple technique has been used since the early days of computers.</span></span> <span data-ttu-id="a592c-106">它只涉及检测应用程序以写入稍后要使用的输出。</span><span class="sxs-lookup"><span data-stu-id="a592c-106">It simply involves instrumenting an application to write output to be consumed later.</span></span>

## <a name="reasons-to-use-logging-and-tracing"></a><span data-ttu-id="a592c-107">使用日志记录和跟踪的原因</span><span class="sxs-lookup"><span data-stu-id="a592c-107">Reasons to use logging and tracing</span></span>

<span data-ttu-id="a592c-108">这一简单技术功能非常强大。</span><span class="sxs-lookup"><span data-stu-id="a592c-108">This simple technique is surprisingly powerful.</span></span> <span data-ttu-id="a592c-109">可以在调试器失败的情况下使用它：</span><span class="sxs-lookup"><span data-stu-id="a592c-109">It can be used in situations where a debugger fails:</span></span>

- <span data-ttu-id="a592c-110">很难使用传统调试器来调试在很长一段时间内发生的问题。</span><span class="sxs-lookup"><span data-stu-id="a592c-110">Issues occurring over long periods of time, can be difficult to debug with a traditional debugger.</span></span> <span data-ttu-id="a592c-111">借助日志，可以跨在较长时间进行详细的事后检查。</span><span class="sxs-lookup"><span data-stu-id="a592c-111">Logs allow for detailed post-mortem review spanning long periods of time.</span></span> <span data-ttu-id="a592c-112">与此相反，调试器限制为只能进行实时分析。</span><span class="sxs-lookup"><span data-stu-id="a592c-112">In contrast, debuggers are constrained to real-time analysis.</span></span>
- <span data-ttu-id="a592c-113">多线程应用程序和分布式应用程序通常难以调试。</span><span class="sxs-lookup"><span data-stu-id="a592c-113">Multi-threaded applications and distributed applications are often difficult to debug.</span></span>  <span data-ttu-id="a592c-114">附加调试器往往会修改行为。</span><span class="sxs-lookup"><span data-stu-id="a592c-114">Attaching a debugger tends to modify behaviors.</span></span> <span data-ttu-id="a592c-115">可以根据需要分析详细日志，以了解复杂的系统。</span><span class="sxs-lookup"><span data-stu-id="a592c-115">Detailed logs can be analyzed as needed to understand complex systems.</span></span>
- <span data-ttu-id="a592c-116">分布式应用程序中的问题可能源于许多组件之间的复杂交互，将调试器连接到系统的每个部分可能是不合理的。</span><span class="sxs-lookup"><span data-stu-id="a592c-116">Issues in distributed applications may arise from a complex interaction between many components and it may not be reasonable to connect a debugger to every part of the system.</span></span>
- <span data-ttu-id="a592c-117">许多服务不应停止。</span><span class="sxs-lookup"><span data-stu-id="a592c-117">Many services shouldn't be stalled.</span></span> <span data-ttu-id="a592c-118">附加调试器往往会导致超时失败。</span><span class="sxs-lookup"><span data-stu-id="a592c-118">Attaching a debugger often causes timeout failures.</span></span>
- <span data-ttu-id="a592c-119">问题并非总是可预见的。</span><span class="sxs-lookup"><span data-stu-id="a592c-119">Issues aren't always foreseen.</span></span> <span data-ttu-id="a592c-120">日志记录和跟踪旨在降低开销，以便在出现问题的情况下可以始终记录程序。</span><span class="sxs-lookup"><span data-stu-id="a592c-120">Logging and tracing are designed for low overhead so that programs can always be recording in case an issue occurs.</span></span>

## <a name="net-core-apis"></a><span data-ttu-id="a592c-121">.NET Core API</span><span class="sxs-lookup"><span data-stu-id="a592c-121">.NET Core APIs</span></span>

### <a name="print-style-apis"></a><span data-ttu-id="a592c-122">打印样式 API</span><span class="sxs-lookup"><span data-stu-id="a592c-122">Print style APIs</span></span>

<span data-ttu-id="a592c-123">每个 <xref:System.Console?displayProperty=nameWithType>、<xref:System.Diagnostics.Trace?displayProperty=nameWithType> 和 <xref:System.Diagnostics.Debug?displayProperty=nameWithType> 类都提供类似的打印样式 API，以便于日志记录。</span><span class="sxs-lookup"><span data-stu-id="a592c-123">The <xref:System.Console?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace?displayProperty=nameWithType>, and <xref:System.Diagnostics.Debug?displayProperty=nameWithType> classes each provide similar print style APIs convenient for logging.</span></span>

<span data-ttu-id="a592c-124">选择使用哪种打印样式 API 由用户自己决定。</span><span class="sxs-lookup"><span data-stu-id="a592c-124">The choice of which print style API to use is up to you.</span></span> <span data-ttu-id="a592c-125">主要区别包括：</span><span class="sxs-lookup"><span data-stu-id="a592c-125">The key differences are:</span></span>

- <xref:System.Console?displayProperty=nameWithType>
  - <span data-ttu-id="a592c-126">始终启用，并始终写入控制台。</span><span class="sxs-lookup"><span data-stu-id="a592c-126">Always enabled and always writes to the console.</span></span>
  - <span data-ttu-id="a592c-127">这对于客户可能需要在版本中查看的信息非常有用。</span><span class="sxs-lookup"><span data-stu-id="a592c-127">Useful for information that your customer may need to see in the release.</span></span>
  - <span data-ttu-id="a592c-128">由于这是最简单的方法，所以常常用于临时调试。</span><span class="sxs-lookup"><span data-stu-id="a592c-128">Because it's the simplest approach, it's often used for ad-hoc temporary debugging.</span></span> <span data-ttu-id="a592c-129">此调试代码通常不会签入到源代码管理中。</span><span class="sxs-lookup"><span data-stu-id="a592c-129">This debug code is often never checked in to source control.</span></span>
- <xref:System.Diagnostics.Trace?displayProperty=nameWithType>
  - <span data-ttu-id="a592c-130">仅在通过向源中添加 `#define TRACE` 或在编译时指定选项 `/d:TRACE` 来定义 `TRACE` 时启用。</span><span class="sxs-lookup"><span data-stu-id="a592c-130">Only enabled when `TRACE` is defined by adding `#define TRACE` to your source or specifying the option `/d:TRACE` when compiling.</span></span>
  - <span data-ttu-id="a592c-131">写入到附加 <xref:System.Diagnostics.Trace.Listeners>，默认情况下为 <xref:System.Diagnostics.DefaultTraceListener>。</span><span class="sxs-lookup"><span data-stu-id="a592c-131">Writes to attached <xref:System.Diagnostics.Trace.Listeners>, by default the <xref:System.Diagnostics.DefaultTraceListener>.</span></span>
  - <span data-ttu-id="a592c-132">创建将在大多数生成中启用的日志时使用此 API。</span><span class="sxs-lookup"><span data-stu-id="a592c-132">Use this API when creating logs that will be enabled in most builds.</span></span>
- <xref:System.Diagnostics.Debug?displayProperty=nameWithType>
  - <span data-ttu-id="a592c-133">仅在通过向源中添加 `#define DEBUG` 或在编译时指定选项 `/d:DEBUG` 来定义 `DEBUG` 时启用。</span><span class="sxs-lookup"><span data-stu-id="a592c-133">Only enabled when `DEBUG` is defined by adding `#define DEBUG` to your source or specifying the option `/d:DEBUG` when compiling.</span></span>
  - <span data-ttu-id="a592c-134">写入附加调试器。</span><span class="sxs-lookup"><span data-stu-id="a592c-134">Writes to an attached debugger.</span></span>
  - <span data-ttu-id="a592c-135">在 `*nix` 写入到 stderr 时（如果设置了 `COMPlus_DebugWriteToStdErr`）。</span><span class="sxs-lookup"><span data-stu-id="a592c-135">On `*nix` writes to stderr if `COMPlus_DebugWriteToStdErr` is set.</span></span>
  - <span data-ttu-id="a592c-136">创建将仅在调试生成中启用的日志时使用此 API。</span><span class="sxs-lookup"><span data-stu-id="a592c-136">Use this API when creating logs that will be enabled only in debug builds.</span></span>

### <a name="logging-events"></a><span data-ttu-id="a592c-137">记录事件</span><span class="sxs-lookup"><span data-stu-id="a592c-137">Logging events</span></span>

<span data-ttu-id="a592c-138">以下 API 更面向于事件。</span><span class="sxs-lookup"><span data-stu-id="a592c-138">The following APIs are more event oriented.</span></span> <span data-ttu-id="a592c-139">它们记录事件对象，而不是记录简单字符串。</span><span class="sxs-lookup"><span data-stu-id="a592c-139">Rather than logging simple strings they log event objects.</span></span>

- <xref:System.Diagnostics.Tracing.EventSource?displayProperty=nameWithType>
  - <span data-ttu-id="a592c-140">EventSource 是主根 .NET Core 跟踪 API。</span><span class="sxs-lookup"><span data-stu-id="a592c-140">EventSource is the primary root .NET Core tracing API.</span></span>
  - <span data-ttu-id="a592c-141">在所有 .NET Standard 版本中提供。</span><span class="sxs-lookup"><span data-stu-id="a592c-141">Available in all .NET Standard versions.</span></span>
  - <span data-ttu-id="a592c-142">仅允许跟踪可序列化的对象。</span><span class="sxs-lookup"><span data-stu-id="a592c-142">Only allows tracing serializable objects.</span></span>
  - <span data-ttu-id="a592c-143">可以通过配置为使用 EventSource 的任何 [EventListener](xref:System.Diagnostics.Tracing.EventListener) 实例在进程中使用。</span><span class="sxs-lookup"><span data-stu-id="a592c-143">Can be consumed in-process via any [EventListener](xref:System.Diagnostics.Tracing.EventListener) instances configured to consume the EventSource.</span></span>
  - <span data-ttu-id="a592c-144">可通过以下方式在进程外使用：</span><span class="sxs-lookup"><span data-stu-id="a592c-144">Can be consumed out-of-process via:</span></span>
    - <span data-ttu-id="a592c-145">所有平台上的 [.NET Core EventPipe](./eventpipe.md)</span><span class="sxs-lookup"><span data-stu-id="a592c-145">[.NET Core's EventPipe](./eventpipe.md) on all platforms</span></span>
    - [<span data-ttu-id="a592c-146">Windows 事件跟踪 (ETW)</span><span class="sxs-lookup"><span data-stu-id="a592c-146">Event Tracing for Windows (ETW)</span></span>](/windows/win32/etw/event-tracing-portal)
    - [<span data-ttu-id="a592c-147">适用于 Linux 的 LTTng 跟踪框架</span><span class="sxs-lookup"><span data-stu-id="a592c-147">LTTng tracing framework for Linux</span></span>](https://lttng.org/)
      - <span data-ttu-id="a592c-148">演练：[使用 PerfCollect 收集 LTTng 跟踪](trace-perfcollect-lttng.md)。</span><span class="sxs-lookup"><span data-stu-id="a592c-148">Walkthrough: [Collect an LTTng trace using PerfCollect](trace-perfcollect-lttng.md).</span></span>

- <xref:System.Diagnostics.DiagnosticSource?displayProperty=nameWithType>
  - <span data-ttu-id="a592c-149">包含在 .NET Core 中，用作 .NET Framework 的 [NuGet 包](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource)。</span><span class="sxs-lookup"><span data-stu-id="a592c-149">Included in .NET Core and as a [NuGet package](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource) for .NET Framework.</span></span>
  - <span data-ttu-id="a592c-150">允许对非序列化对象进行进程内跟踪。</span><span class="sxs-lookup"><span data-stu-id="a592c-150">Allows in-process tracing of non-serializable objects.</span></span>
  - <span data-ttu-id="a592c-151">包括一个桥，以允许将已记录对象的所选字段写入 <xref:System.Diagnostics.Tracing.EventSource>。</span><span class="sxs-lookup"><span data-stu-id="a592c-151">Includes a bridge to allow selected fields of logged objects to be written to an <xref:System.Diagnostics.Tracing.EventSource>.</span></span>

- <xref:System.Diagnostics.Activity?displayProperty=nameWithType>
  - <span data-ttu-id="a592c-152">提供了一种明确的方法来标识由特定活动或事务生成的日志消息。</span><span class="sxs-lookup"><span data-stu-id="a592c-152">Provides a definitive way to identify log messages resulting from a specific activity or transaction.</span></span> <span data-ttu-id="a592c-153">此对象可用于关联不同服务中的日志。</span><span class="sxs-lookup"><span data-stu-id="a592c-153">This object can be used to correlate logs across different services.</span></span>

- <xref:System.Diagnostics.EventLog?displayProperty=nameWithType>
  - <span data-ttu-id="a592c-154">仅限 Windows。</span><span class="sxs-lookup"><span data-stu-id="a592c-154">Windows only.</span></span>
  - <span data-ttu-id="a592c-155">将消息写入 Windows 事件日志。</span><span class="sxs-lookup"><span data-stu-id="a592c-155">Writes messages to the Windows Event Log.</span></span>
  - <span data-ttu-id="a592c-156">系统管理员希望严重的应用程序错误消息会在 Windows 事件日志中出现。</span><span class="sxs-lookup"><span data-stu-id="a592c-156">System administrators expect fatal application error messages to appear in the Windows Event Log.</span></span>

## <a name="distributed-tracing"></a><span data-ttu-id="a592c-157">分布式跟踪</span><span class="sxs-lookup"><span data-stu-id="a592c-157">Distributed Tracing</span></span>

<span data-ttu-id="a592c-158">[分布式跟踪](./distributed-tracing.md)是在分布式系统中发布和观察跟踪数据的方法。</span><span class="sxs-lookup"><span data-stu-id="a592c-158">[Distributed Tracing](./distributed-tracing.md) is the way to publish and observe the tracing data in a distributed system.</span></span>

## <a name="ilogger-and-logging-frameworks"></a><span data-ttu-id="a592c-159">ILogger 和日志记录框架</span><span class="sxs-lookup"><span data-stu-id="a592c-159">ILogger and logging frameworks</span></span>

<span data-ttu-id="a592c-160">低级别 API 可能不符合你的日志记录需求。</span><span class="sxs-lookup"><span data-stu-id="a592c-160">The low-level APIs may not be the right choice for your logging needs.</span></span> <span data-ttu-id="a592c-161">可能需要考虑使用日志记录框架。</span><span class="sxs-lookup"><span data-stu-id="a592c-161">You may want to consider a logging framework.</span></span>

<span data-ttu-id="a592c-162"><xref:Microsoft.Extensions.Logging.ILogger> 接口已用于创建一个公共日志记录接口，可在其中通过依赖项注入插入记录器。</span><span class="sxs-lookup"><span data-stu-id="a592c-162">The <xref:Microsoft.Extensions.Logging.ILogger> interface has been used to create a common logging interface where the loggers can be inserted through dependency injection.</span></span>

<span data-ttu-id="a592c-163">例如，为了使你能够为应用程序做出最佳选择，.NET 提供了对选择的内置和第三方框架的支持：</span><span class="sxs-lookup"><span data-stu-id="a592c-163">For instance, to allow you to make the best choice for your application .NET offers support for a selection of built-in and third-party frameworks:</span></span>

- [<span data-ttu-id="a592c-164">.NET 内置日志记录提供程序</span><span class="sxs-lookup"><span data-stu-id="a592c-164">.NET Built-in logging providers</span></span>](../extensions/logging-providers.md#built-in-logging-providers)
- [<span data-ttu-id="a592c-165">.NET 第三方日志记录提供程序</span><span class="sxs-lookup"><span data-stu-id="a592c-165">.NET Third-party logging providers</span></span>](../extensions/logging-providers.md#third-party-logging-providers)

## <a name="logging-related-references"></a><span data-ttu-id="a592c-166">与日志记录相关的引用</span><span class="sxs-lookup"><span data-stu-id="a592c-166">Logging related references</span></span>

- [<span data-ttu-id="a592c-167">如何：使用跟踪和调试进行条件编译</span><span class="sxs-lookup"><span data-stu-id="a592c-167">How to: Compile Conditionally with Trace and Debug</span></span>](../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)

- [<span data-ttu-id="a592c-168">如何：向应用程序代码添加跟踪语句</span><span class="sxs-lookup"><span data-stu-id="a592c-168">How to: Add Trace Statements to Application Code</span></span>](../../framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)

- <span data-ttu-id="a592c-169">[.NET 中的日志记录](../extensions/logging.md)提供它所支持的日志记录技术的概述。</span><span class="sxs-lookup"><span data-stu-id="a592c-169">[Logging in .NET](../extensions/logging.md) provides an overview of the logging techniques it supports.</span></span>

- <span data-ttu-id="a592c-170">[C# 字符串内插](../../csharp/language-reference/tokens/interpolated.md)可以简化日志记录代码的编写。</span><span class="sxs-lookup"><span data-stu-id="a592c-170">[C# string interpolation](../../csharp/language-reference/tokens/interpolated.md) can simplify writing logging code.</span></span>

- [<span data-ttu-id="a592c-171">运行时提供程序事件列表</span><span class="sxs-lookup"><span data-stu-id="a592c-171">Runtime Provider Event List</span></span>](../../fundamentals/diagnostics/runtime-events.md)

- [<span data-ttu-id="a592c-172">.NET 中的已知事件提供程序</span><span class="sxs-lookup"><span data-stu-id="a592c-172">Well-known Event Providers in .NET</span></span>](well-known-event-providers.md)

- <span data-ttu-id="a592c-173"><xref:System.Exception.Message?displayProperty=nameWithType> 属性对日志记录异常很有用。</span><span class="sxs-lookup"><span data-stu-id="a592c-173">The <xref:System.Exception.Message?displayProperty=nameWithType> property is useful for logging exceptions.</span></span>

- <span data-ttu-id="a592c-174"><xref:System.Diagnostics.StackTrace?displayProperty=nameWithType> 类可用于在日志中提供堆栈信息。</span><span class="sxs-lookup"><span data-stu-id="a592c-174">The <xref:System.Diagnostics.StackTrace?displayProperty=nameWithType> class can be useful to provide stack info in your logs.</span></span>

## <a name="performance-considerations"></a><span data-ttu-id="a592c-175">性能注意事项</span><span class="sxs-lookup"><span data-stu-id="a592c-175">Performance considerations</span></span>

<span data-ttu-id="a592c-176">字符串格式设置可能会占用大量的 CPU 处理时间。</span><span class="sxs-lookup"><span data-stu-id="a592c-176">String formatting can take noticeable CPU processing time.</span></span>

<span data-ttu-id="a592c-177">在性能关键应用程序中，建议执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="a592c-177">In performance critical applications, it's recommended that you:</span></span>

- <span data-ttu-id="a592c-178">如果未侦听，则避免进行大量日志记录。</span><span class="sxs-lookup"><span data-stu-id="a592c-178">Avoid lots of logging when no one is listening.</span></span> <span data-ttu-id="a592c-179">通过检查是否首先启用了日志记录，避免构造开销较大的日志记录消息。</span><span class="sxs-lookup"><span data-stu-id="a592c-179">Avoid constructing costly logging messages by checking if logging is enabled first.</span></span>
- <span data-ttu-id="a592c-180">仅记录有用的内容。</span><span class="sxs-lookup"><span data-stu-id="a592c-180">Only log what's useful.</span></span>
- <span data-ttu-id="a592c-181">将复杂的格式设置推迟到分析阶段。</span><span class="sxs-lookup"><span data-stu-id="a592c-181">Defer fancy formatting to the analysis stage.</span></span>
