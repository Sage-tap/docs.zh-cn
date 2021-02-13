---
title: 单文件应用程序
description: 了解单文件应用程序的本质以及应考虑使用此应用程序部署模型的原因。
author: lakshanf
ms.author: lakshanf
ms.date: 12/17/2020
ms.openlocfilehash: fb768fa6fe390fbe8390e441f4eb71c3172ad395
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2021
ms.locfileid: "99505421"
---
# <a name="single-file-deployment-and-executable"></a><span data-ttu-id="ea034-103">单文件部署和可执行文件</span><span class="sxs-lookup"><span data-stu-id="ea034-103">Single file deployment and executable</span></span>

<span data-ttu-id="ea034-104">通过将所有依赖应用程序的文件捆绑到一个二进制文件中，为应用程序开发人员提供一个具有吸引力的选项，那就是将应用程序作为单个文件进行部署和分发。</span><span class="sxs-lookup"><span data-stu-id="ea034-104">Bundling all application-dependent files into a single binary provides an application developer with the attractive option to deploy and distribute the application as a single file.</span></span> <span data-ttu-id="ea034-105">此部署模型从 .NET Core 3.0 开始提供，在 .NET 5.0 中进行了增强。</span><span class="sxs-lookup"><span data-stu-id="ea034-105">This deployment model has been available since .NET Core 3.0 and has been enhanced in .NET 5.0.</span></span> <span data-ttu-id="ea034-106">之前在 .NET Core 3.0 中，当用户运行单文件应用时，.NET Core 主机先将所有文件提取到一个临时目录，然后再运行该应用程序。</span><span class="sxs-lookup"><span data-stu-id="ea034-106">Previously in .NET Core 3.0, when a user runs your single-file app, .NET Core host first extracts all files to a temporary directory before running the application.</span></span> <span data-ttu-id="ea034-107">.NET 5.0 改进了这一体验，它可直接运行代码，无需从应用中提取文件。</span><span class="sxs-lookup"><span data-stu-id="ea034-107">.NET 5.0 improves this experience by directly running the code without the need to extract the files from the app.</span></span>

<span data-ttu-id="ea034-108">单文件部署可用于[依赖框架的部署模型](index.md#publish-framework-dependent)和[独立应用程序](index.md#publish-self-contained)。</span><span class="sxs-lookup"><span data-stu-id="ea034-108">Single File deployment is available for both the [framework-dependent deployment model](index.md#publish-framework-dependent) and [self-contained applications](index.md#publish-self-contained).</span></span> <span data-ttu-id="ea034-109">独立应用程序中单个文件的大小很大，因为它包含运行时和框架库。</span><span class="sxs-lookup"><span data-stu-id="ea034-109">The size of the single file in a self-contained application will be large since it will include the runtime and the framework libraries.</span></span> <span data-ttu-id="ea034-110">单文件部署选项可与 [ReadyToRun](ready-to-run.md) 和 [Trim（.NET 5.0 中的一项试验功能）](trim-self-contained.md)发布选项结合使用。</span><span class="sxs-lookup"><span data-stu-id="ea034-110">The single file deployment option can be combined with [ReadyToRun](ready-to-run.md) and [Trim (an experimental feature in .NET 5.0)](trim-self-contained.md) publish options.</span></span>

## <a name="api-incompatibility"></a><span data-ttu-id="ea034-111">API 不兼容</span><span class="sxs-lookup"><span data-stu-id="ea034-111">API incompatibility</span></span>

<span data-ttu-id="ea034-112">某些 API 与单文件部署不兼容，如果应用程序使用这些 API，可能需要进行修改。</span><span class="sxs-lookup"><span data-stu-id="ea034-112">Some APIs are not compatible with single-file deployment and applications may require modification if they use these APIs.</span></span> <span data-ttu-id="ea034-113">如果使用第三方框架或包，则它们也可能使用了这样的 API 并需要修改。</span><span class="sxs-lookup"><span data-stu-id="ea034-113">If you use a third-party framework or package, it's possible that they may also use one of these APIs and need modification.</span></span> <span data-ttu-id="ea034-114">出现问题的最常见原因是依赖于应用程序附带的文件或 DLL 的文件路径。</span><span class="sxs-lookup"><span data-stu-id="ea034-114">The most common cause of problems is dependence on file paths for files or DLLs shipped with the application.</span></span>

<span data-ttu-id="ea034-115">下表提供了用于单文件的相关运行时库 API 详细信息。</span><span class="sxs-lookup"><span data-stu-id="ea034-115">The table below has the relevant runtime library API details for single-file use.</span></span>

| <span data-ttu-id="ea034-116">API</span><span class="sxs-lookup"><span data-stu-id="ea034-116">API</span></span>                            | <span data-ttu-id="ea034-117">注意</span><span class="sxs-lookup"><span data-stu-id="ea034-117">Note</span></span>                                                                   |
|--------------------------------|------------------------------------------------------------------------|
| `Assembly.Location`            | <span data-ttu-id="ea034-118">返回空字符串。</span><span class="sxs-lookup"><span data-stu-id="ea034-118">Returns an empty string.</span></span>                                               |
| `Module.FullyQualifiedName`    | <span data-ttu-id="ea034-119">返回值为 `<Unknown>` 的字符串，或引发异常。</span><span class="sxs-lookup"><span data-stu-id="ea034-119">Returns a string with the value of `<Unknown>` or throws an exception.</span></span> |
| `Module.Name`                  | <span data-ttu-id="ea034-120">返回值为 `<Unknown>` 的字符串。</span><span class="sxs-lookup"><span data-stu-id="ea034-120">Returns a string with the value of `<Unknown>`.</span></span>                        |
| `Assembly.GetFile`             | <span data-ttu-id="ea034-121">引发 <xref:System.IO.IOException>。</span><span class="sxs-lookup"><span data-stu-id="ea034-121">Throws <xref:System.IO.IOException>.</span></span>                                   |
| `Assembly.GetFiles`            | <span data-ttu-id="ea034-122">引发 <xref:System.IO.IOException>。</span><span class="sxs-lookup"><span data-stu-id="ea034-122">Throws <xref:System.IO.IOException>.</span></span>                                   |
| `Assembly.CodeBase`            | <span data-ttu-id="ea034-123">引发 <xref:System.PlatformNotSupportedException>。</span><span class="sxs-lookup"><span data-stu-id="ea034-123">Throws <xref:System.PlatformNotSupportedException>.</span></span>                    |
| `Assembly.EscapedCodeBase`     | <span data-ttu-id="ea034-124">引发 <xref:System.PlatformNotSupportedException>。</span><span class="sxs-lookup"><span data-stu-id="ea034-124">Throws <xref:System.PlatformNotSupportedException>.</span></span>                    |
| `AssemblyName.CodeBase`        | <span data-ttu-id="ea034-125">返回 `null`。</span><span class="sxs-lookup"><span data-stu-id="ea034-125">Returns `null`.</span></span>                                                        |
| `AssemblyName.EscapedCodeBase` | <span data-ttu-id="ea034-126">返回 `null`。</span><span class="sxs-lookup"><span data-stu-id="ea034-126">Returns `null`.</span></span>                                                        |

<span data-ttu-id="ea034-127">我们提供了关于修复常见问题的一些建议：</span><span class="sxs-lookup"><span data-stu-id="ea034-127">We have some recommendations for fixing common scenarios:</span></span>

* <span data-ttu-id="ea034-128">若要访问可执行文件旁边的文件，请使用 <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="ea034-128">To access files next to the executable, use <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType>.</span></span>

* <span data-ttu-id="ea034-129">若要查找可执行文件的文件名，请使用 <xref:System.Environment.GetCommandLineArgs?displayProperty=nameWithType> 的第一个元素。</span><span class="sxs-lookup"><span data-stu-id="ea034-129">To find the file name of the executable, use the first element of <xref:System.Environment.GetCommandLineArgs?displayProperty=nameWithType>.</span></span>

* <span data-ttu-id="ea034-130">若要避免完全发送松散文件，请考虑使用[嵌入的资源](../../framework/resources/creating-resource-files-for-desktop-apps.md)。</span><span class="sxs-lookup"><span data-stu-id="ea034-130">To avoid shipping loose files entirely, consider using [embedded resources](../../framework/resources/creating-resource-files-for-desktop-apps.md).</span></span>

## <a name="attaching-a-debugger"></a><span data-ttu-id="ea034-131">附加调试器</span><span class="sxs-lookup"><span data-stu-id="ea034-131">Attaching a debugger</span></span>

<span data-ttu-id="ea034-132">在 Linux 上，可以附加到自包含单文件进程或调试故障转储的唯一调试器是[有 LLDB 的 SOS](../diagnostics/dotnet-sos.md)。</span><span class="sxs-lookup"><span data-stu-id="ea034-132">On Linux, the only debugger which can attach to self-contained single-file processes or debug crash dumps is [SOS with LLDB](../diagnostics/dotnet-sos.md).</span></span>

<span data-ttu-id="ea034-133">在 Windows 和 Mac 上，可以使用 Visual Studio 和 VS Code 调试故障转储。</span><span class="sxs-lookup"><span data-stu-id="ea034-133">On Windows and Mac, Visual Studio and VS Code can be used to debug crash dumps.</span></span> <span data-ttu-id="ea034-134">要附加到运行自包含单文件可执行文件，需要额外的文件：_mscordbi.{dll,so}_</span><span class="sxs-lookup"><span data-stu-id="ea034-134">Attaching to a running self-contained single-file executable requires an extra file: _mscordbi.{dll,so}_.</span></span>

<span data-ttu-id="ea034-135">如果没有此文件，Visual Studio 可能会生成错误“无法附加到进程。</span><span class="sxs-lookup"><span data-stu-id="ea034-135">Without this file Visual Studio may produce the error "Unable to attach to the process.</span></span> <span data-ttu-id="ea034-136">未安装调试组件。”</span><span class="sxs-lookup"><span data-stu-id="ea034-136">A debug component is not installed."</span></span> <span data-ttu-id="ea034-137">而 VS Code 可能生成错误“未能附加到进程:未知错误:0x80131c3c。”</span><span class="sxs-lookup"><span data-stu-id="ea034-137">and VS Code may produce the error "Failed to attach to process: Unknown Error: 0x80131c3c."</span></span>

<span data-ttu-id="ea034-138">若要修复这些错误，需要将 mscordbi 复制到可执行文件旁边。</span><span class="sxs-lookup"><span data-stu-id="ea034-138">To fix these errors, _mscordbi_ needs to be copied next to the executable.</span></span> <span data-ttu-id="ea034-139">mscordbi 默认 `publish` 到具有应用程序运行时 ID 的子目录中。</span><span class="sxs-lookup"><span data-stu-id="ea034-139">_mscordbi_ is `publish`ed by default in the subdirectory with the application's runtime ID.</span></span> <span data-ttu-id="ea034-140">例如，如果使用适用于 Windows 的 `dotnet` CLI 并使用 `-r win-x64` 参数发布自包含单文件可执行文件，则可执行文件将置于 bin/Debug/net5.0/win-x64/publish 中。</span><span class="sxs-lookup"><span data-stu-id="ea034-140">So, for example, if one were to publish a self-contained single-file executable using the `dotnet` CLI for Windows using the parameters `-r win-x64`, the executable would be placed in _bin/Debug/net5.0/win-x64/publish_.</span></span> <span data-ttu-id="ea034-141">mscordbi.dll 的副本将存在于 bin/Debug/net5.0/win-x64 中。 </span><span class="sxs-lookup"><span data-stu-id="ea034-141">A copy of _mscordbi.dll_ would be present in _bin/Debug/net5.0/win-x64_.</span></span>

## <a name="other-considerations"></a><span data-ttu-id="ea034-142">其他注意事项</span><span class="sxs-lookup"><span data-stu-id="ea034-142">Other considerations</span></span>

<span data-ttu-id="ea034-143">默认情况下，单文件不捆绑本机库。</span><span class="sxs-lookup"><span data-stu-id="ea034-143">Single-file doesn't bundle native libraries by default.</span></span> <span data-ttu-id="ea034-144">在 Linux 上，我们将运行时预链接到捆绑包中，并且仅将应用程序本机库部署到单文件应用所在的目录中。</span><span class="sxs-lookup"><span data-stu-id="ea034-144">On Linux, we prelink the runtime into the bundle and only application native libraries are deployed to the same directory as the single-file app.</span></span> <span data-ttu-id="ea034-145">在 Windows 上，我们仅预链接托管代码，而且运行时库和应用程序本机库都部署到单文件应用所在的目录中。</span><span class="sxs-lookup"><span data-stu-id="ea034-145">On Windows, we prelink only the hosting code and both the runtime and application native libraries are deployed to the same directory as the single-file app.</span></span> <span data-ttu-id="ea034-146">目的是确保提供良好的调试体验，这要求将本机文件从单文件中排除。</span><span class="sxs-lookup"><span data-stu-id="ea034-146">This is to ensure a good debugging experience, which requires native files to be excluded from the single file.</span></span> <span data-ttu-id="ea034-147">可选择设置标志 `IncludeNativeLibrariesForSelfExtract`，从而在单文件捆绑包中包含本机库，但在运行单文件应用程序时，这些文件将被提取到客户端计算机上的临时目录中。</span><span class="sxs-lookup"><span data-stu-id="ea034-147">There is an option to set a flag, `IncludeNativeLibrariesForSelfExtract`, to include native libraries in the single file bundle, but these files will be extracted to a temporary directory in the client machine when the single file application is run.</span></span>

<span data-ttu-id="ea034-148">指定 `IncludeAllContentForSelfExtract` 将在运行可执行文件之前提取所有文件。</span><span class="sxs-lookup"><span data-stu-id="ea034-148">Specifying `IncludeAllContentForSelfExtract` will extract all files before running the executable.</span></span> <span data-ttu-id="ea034-149">这将保留原始 .NET Core 单文件部署行为。</span><span class="sxs-lookup"><span data-stu-id="ea034-149">This preserves the original .NET Core single-file deployment behavior.</span></span>

<span data-ttu-id="ea034-150">单文件应用程序旁边将具有所有相关的 PDB 文件，并且默认情况下不会绑定。</span><span class="sxs-lookup"><span data-stu-id="ea034-150">Single-file application will have all related PDB files alongside it and will not be bundled by default.</span></span> <span data-ttu-id="ea034-151">如果要在生成的项目的程序集内包含 PDB，请将 `DebugType` 设置为 `embedded`，如[下方](#include-pdb-files-inside-the-bundle)所详述。</span><span class="sxs-lookup"><span data-stu-id="ea034-151">If you want to include PDBs inside the assembly for projects you build, set the `DebugType` to `embedded` as described [below](#include-pdb-files-inside-the-bundle) in detail.</span></span>

<span data-ttu-id="ea034-152">托管的 C++ 应组件不太适合进行单文件部署，建议使用 C# 或其他非托管 C++ 语言编写应用程序来实现单文件兼容。</span><span class="sxs-lookup"><span data-stu-id="ea034-152">Managed C++ components aren't well suited for single-file deployment and we recommend that you write applications in C# or another non-managed C++ language to be single-file compatible.</span></span>

## <a name="exclude-files-from-being-embedded"></a><span data-ttu-id="ea034-153">将文件排除在嵌入之外</span><span class="sxs-lookup"><span data-stu-id="ea034-153">Exclude files from being embedded</span></span>

<span data-ttu-id="ea034-154">通过设置以下元数据，可明确指定不在单文件中嵌入某些文件：</span><span class="sxs-lookup"><span data-stu-id="ea034-154">Certain files can be explicitly excluded from being embedded in the single-file by setting following metadata:</span></span>

```xml
<ExcludeFromSingleFile>true</ExcludeFromSingleFile>
```

<span data-ttu-id="ea034-155">例如，若要将某些文件放置在发布目录中，但不将它们捆绑到单文件中：</span><span class="sxs-lookup"><span data-stu-id="ea034-155">For example, to place some files in the publish directory but not bundle them in the single-file:</span></span>

```xml
<ItemGroup>
  <Content Update="Plugin.dll">
    <CopyToPublishDirectory>PreserveNewest</CopyToPublishDirectory>
    <ExcludeFromSingleFile>true</ExcludeFromSingleFile>
  </Content>
</ItemGroup>
```

## <a name="include-pdb-files-inside-the-bundle"></a><span data-ttu-id="ea034-156">在绑定内包括 PDB 文件</span><span class="sxs-lookup"><span data-stu-id="ea034-156">Include PDB files inside the bundle</span></span>

<span data-ttu-id="ea034-157">可以使用下面的设置将程序集的 PDB 文件嵌入到程序集本身 (`.dll`)。</span><span class="sxs-lookup"><span data-stu-id="ea034-157">The PDB file for an assembly can be embedded into the assembly itself (the `.dll`) using the setting below.</span></span> <span data-ttu-id="ea034-158">由于符号是程序集的一部分，因此，它们也会是单文件应用程序的一部分：</span><span class="sxs-lookup"><span data-stu-id="ea034-158">Since the symbols are part of the assembly, they will be part of the single-file application as well:</span></span>

```xml
<DebugType>embedded</DebugType>
```

<span data-ttu-id="ea034-159">例如，将以下属性添加到程序集的项目文件，以将 PDB 文件嵌入到该程序集：</span><span class="sxs-lookup"><span data-stu-id="ea034-159">For example, add the following property to the project file of an assembly to embed the PDB file to that assembly:</span></span>

```xml
<PropertyGroup>
  <DebugType>embedded</DebugType>
</PropertyGroup>
```

## <a name="publish-a-single-file-app---sample-project-file"></a><span data-ttu-id="ea034-160">发布单文件应用 - 示例项目文件</span><span class="sxs-lookup"><span data-stu-id="ea034-160">Publish a single file app - sample project file</span></span>

<span data-ttu-id="ea034-161">下面是指定单文件发布的示例项目文件：</span><span class="sxs-lookup"><span data-stu-id="ea034-161">Here's a sample project file that specifies single-file publishing:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>
    <PublishSingleFile>true</PublishSingleFile>
    <SelfContained>true</SelfContained>
    <RuntimeIdentifier>win-x64</RuntimeIdentifier>
    <PublishTrimmed>true</PublishTrimmed>
    <PublishReadyToRun>true</PublishReadyToRun>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="ea034-162">这些属性具有下列函数：</span><span class="sxs-lookup"><span data-stu-id="ea034-162">These properties have the following functions:</span></span>

* <span data-ttu-id="ea034-163">`PublishSingleFile` - 启用单文件发布。</span><span class="sxs-lookup"><span data-stu-id="ea034-163">`PublishSingleFile` - Enables single-file publishing.</span></span>
* <span data-ttu-id="ea034-164">`SelfContained` - 确定应用是独立的还是依赖于框架的。</span><span class="sxs-lookup"><span data-stu-id="ea034-164">`SelfContained` - Determines whether the app will be self-contained or framework-dependent.</span></span>
* <span data-ttu-id="ea034-165">`RuntimeIdentifier` - 指定目标 [OS 和 CPU 类型](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="ea034-165">`RuntimeIdentifier` - Specifies the [OS and CPU type](../rid-catalog.md) you are targeting.</span></span>
* <span data-ttu-id="ea034-166">`PublishTrimmed` - 启用[程序集剪裁](trim-self-contained.md)（只有独立应用才支持）。</span><span class="sxs-lookup"><span data-stu-id="ea034-166">`PublishTrimmed` - Enables use of [assembly trimming](trim-self-contained.md), which is only supported for self-contained apps.</span></span>
* <span data-ttu-id="ea034-167">`PublishReadyToRun` - 启用[预先 (AOT) 编译](ready-to-run.md)。</span><span class="sxs-lookup"><span data-stu-id="ea034-167">`PublishReadyToRun` - Enables [ahead-of-time (AOT) compilation](ready-to-run.md).</span></span>

<span data-ttu-id="ea034-168">**注意：**</span><span class="sxs-lookup"><span data-stu-id="ea034-168">**Notes:**</span></span>

* <span data-ttu-id="ea034-169">应用特定于 OS 和体系结构。</span><span class="sxs-lookup"><span data-stu-id="ea034-169">Apps are OS and architecture-specific.</span></span> <span data-ttu-id="ea034-170">需要为每个配置发布，例如 Linux x64、Linux ARM64、Windows x64 等。</span><span class="sxs-lookup"><span data-stu-id="ea034-170">You need to publish for each configuration, such as Linux x64, Linux ARM64, Windows x64, and so forth.</span></span>
* <span data-ttu-id="ea034-171">单个文件中包含配置文件，例如 \*.runtimeconfig.json。</span><span class="sxs-lookup"><span data-stu-id="ea034-171">Configuration files, such as *\*.runtimeconfig.json*, are included in the single file.</span></span> <span data-ttu-id="ea034-172">如果需要其他配置文件，可将其放在单个文件旁边。</span><span class="sxs-lookup"><span data-stu-id="ea034-172">If an additional configuration file is needed, you can place it beside the single file.</span></span>

## <a name="publish-a-single-file-app---cli"></a><span data-ttu-id="ea034-173">发布单文件应用 - CLI</span><span class="sxs-lookup"><span data-stu-id="ea034-173">Publish a single file app - CLI</span></span>

<span data-ttu-id="ea034-174">使用 [dotnet publish](../tools/dotnet-publish.md) 命令发布单文件应用程序。</span><span class="sxs-lookup"><span data-stu-id="ea034-174">Publish a single file application using the [dotnet publish](../tools/dotnet-publish.md) command.</span></span> <span data-ttu-id="ea034-175">发布应用时，请设置以下属性：</span><span class="sxs-lookup"><span data-stu-id="ea034-175">When you publish your app, set the following properties:</span></span>

- <span data-ttu-id="ea034-176">针对特定运行时进行发布：`-r win-x64`</span><span class="sxs-lookup"><span data-stu-id="ea034-176">Publish for a specific runtime: `-r win-x64`</span></span>
- <span data-ttu-id="ea034-177">作为单个文件进行发布：`-p:PublishSingleFile=true`</span><span class="sxs-lookup"><span data-stu-id="ea034-177">Publish as a single-file: `-p:PublishSingleFile=true`</span></span>

<span data-ttu-id="ea034-178">以下示例将 Windows 应用作为独立的单文件应用程序发布。</span><span class="sxs-lookup"><span data-stu-id="ea034-178">The following example publishes an app for Windows as a self-contained single file application.</span></span>

```dotnetcli
dotnet publish -r win-x64 -p:PublishSingleFile=true --self-contained true
```

<span data-ttu-id="ea034-179">以下示例将 Linux 应用作为依赖框架的单文件应用程序发布。</span><span class="sxs-lookup"><span data-stu-id="ea034-179">The following example publishes an app for Linux as a framework dependent single file application.</span></span>

```dotnetcli
dotnet publish -r linux-x64 -p:PublishSingleFile=true --self-contained false
```

<span data-ttu-id="ea034-180">有关详细信息，请参阅[使用 .NET Core CLI 发布 .NET Core 应用](deploy-with-cli.md)。</span><span class="sxs-lookup"><span data-stu-id="ea034-180">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="publish-a-single-file-app---visual-studio"></a><span data-ttu-id="ea034-181">发布单文件应用 - Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ea034-181">Publish a single file app - Visual Studio</span></span>

<span data-ttu-id="ea034-182">Visual Studio 创建可重用的发布配置文件，用于控制应用程序的发布方式。</span><span class="sxs-lookup"><span data-stu-id="ea034-182">Visual Studio creates reusable publishing profiles that control how your application is published.</span></span>

01. <span data-ttu-id="ea034-183">在“解决方案资源管理器”窗格中，右键单击要发布的项目  。</span><span class="sxs-lookup"><span data-stu-id="ea034-183">On the **Solution Explorer** pane, right-click on the project you want to publish.</span></span> <span data-ttu-id="ea034-184">选择“发布”。</span><span class="sxs-lookup"><span data-stu-id="ea034-184">Select **Publish**.</span></span>

    :::image type="content" source="media/single-file/visual-studio-solution-explorer.png" alt-text="解决方案资源管理器，其中右键单击菜单突出显示了“发布”选项。":::

    <span data-ttu-id="ea034-186">如果还没有发布配置文件，请按照说明创建一个并选择“文件夹”目标类型  。</span><span class="sxs-lookup"><span data-stu-id="ea034-186">If you don't already have a publishing profile, follow the instructions to create one and choose the **Folder** target-type.</span></span>

01. <span data-ttu-id="ea034-187">选择“编辑”  。</span><span class="sxs-lookup"><span data-stu-id="ea034-187">Choose **Edit**.</span></span>

    :::image type="content" source="media/single-file/visual-studio-publish-edit-settings.png" alt-text="带有“编辑”按钮的 Visual Studio 发布配置文件。":::

01. <span data-ttu-id="ea034-189">在“配置文件设置”对话框中，设置以下选项  ：</span><span class="sxs-lookup"><span data-stu-id="ea034-189">In the **Profile settings** dialog, set the following options:</span></span>

    - <span data-ttu-id="ea034-190">将“部署模式”设置为“独立式”或“依赖于框架”。</span><span class="sxs-lookup"><span data-stu-id="ea034-190">Set **Deployment mode** to **Self-contained** or **Framework-dependent**.</span></span>
    - <span data-ttu-id="ea034-191">将“目标运行时”设置为要发布到的平台  。</span><span class="sxs-lookup"><span data-stu-id="ea034-191">Set **Target runtime** to the platform you want to publish to.</span></span> <span data-ttu-id="ea034-192">（必须是除“可移植”以外的设置。）</span><span class="sxs-lookup"><span data-stu-id="ea034-192">(Must be something other than **Portable**.)</span></span>
    - <span data-ttu-id="ea034-193">选择“生成单个文件”。</span><span class="sxs-lookup"><span data-stu-id="ea034-193">Select **Produce single file**.</span></span>

    <span data-ttu-id="ea034-194">选择“保存”保存设置并返回到“发布”对话框   。</span><span class="sxs-lookup"><span data-stu-id="ea034-194">Choose **Save** to save the settings and return to the **Publish** dialog.</span></span>

    :::image type="content" source="media/single-file/visual-studio-publish-single-file-properties.png" alt-text="“配置文件设置”对话框，其中突出显示了“部署模式”、“目标运行时”和“单个文件”选项。":::

01. <span data-ttu-id="ea034-196">选择“发布”，将应用作为单个文件发布。</span><span class="sxs-lookup"><span data-stu-id="ea034-196">Choose **Publish** to publish your app as a single file.</span></span>

<span data-ttu-id="ea034-197">有关详细信息，请参阅[使用 Visual Studio 发布 .NET Core 应用](deploy-with-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="ea034-197">For more information, see [Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>

## <a name="publish-a-single-file-app---visual-studio-for-mac"></a><span data-ttu-id="ea034-198">发布单文件应用 - Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="ea034-198">Publish a single file app - Visual Studio for Mac</span></span>

<span data-ttu-id="ea034-199">Visual Studio for Mac 不提供将应用作为单个文件发布的选项。</span><span class="sxs-lookup"><span data-stu-id="ea034-199">Visual Studio for Mac doesn't provide options to publish your app as a single file.</span></span> <span data-ttu-id="ea034-200">你需要按照[发布单文件应用 - CLI](#publish-a-single-file-app---cli) 部分中的说明手动发布。</span><span class="sxs-lookup"><span data-stu-id="ea034-200">You'll need to publish manually by following the instructions from the [Publish a single file app - CLI](#publish-a-single-file-app---cli) section.</span></span> <span data-ttu-id="ea034-201">有关详细信息，请参阅[使用 .NET Core CLI 发布 .NET Core 应用](deploy-with-cli.md)。</span><span class="sxs-lookup"><span data-stu-id="ea034-201">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ea034-202">请参阅</span><span class="sxs-lookup"><span data-stu-id="ea034-202">See also</span></span>

- <span data-ttu-id="ea034-203">[.NET Core 应用程序部署](index.md)。</span><span class="sxs-lookup"><span data-stu-id="ea034-203">[.NET Core application deployment](index.md).</span></span>
- <span data-ttu-id="ea034-204">[使用 .NET Core CLI 发布 .NET Core 应用](deploy-with-cli.md)。</span><span class="sxs-lookup"><span data-stu-id="ea034-204">[Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>
- <span data-ttu-id="ea034-205">[使用 Visual Studio 发布 .NET Core 应用](deploy-with-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="ea034-205">[Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>
- <span data-ttu-id="ea034-206">[`dotnet publish` 命令](../tools/dotnet-publish.md)。</span><span class="sxs-lookup"><span data-stu-id="ea034-206">[`dotnet publish` command](../tools/dotnet-publish.md).</span></span>
