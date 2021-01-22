---
title: .NET 项目 SDK 概述
titleSuffix: ''
description: 了解 .NET 项目 SDK。
ms.date: 09/17/2020
ms.topic: conceptual
ms.openlocfilehash: 2adb0713fabda142d071425a2affe66cc9d4c172
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189663"
---
# <a name="net-project-sdks"></a><span data-ttu-id="0d969-103">.NET 项目 SDK</span><span class="sxs-lookup"><span data-stu-id="0d969-103">.NET project SDKs</span></span>

<span data-ttu-id="0d969-104">.NET Core 和 .NET 5.0 及更高版本项目与软件开发工具包 (SDK) 关联。</span><span class="sxs-lookup"><span data-stu-id="0d969-104">.NET Core and .NET 5.0 and later projects are associated with a software development kit (SDK).</span></span> <span data-ttu-id="0d969-105">每个项目 SDK 都是一组 MSBuild [目标](/visualstudio/msbuild/msbuild-targets)和相关的[任务](/visualstudio/msbuild/msbuild-tasks)，它们负责编译、打包和发布代码。</span><span class="sxs-lookup"><span data-stu-id="0d969-105">Each *project SDK* is a set of MSBuild [targets](/visualstudio/msbuild/msbuild-targets) and associated [tasks](/visualstudio/msbuild/msbuild-tasks) that are responsible for compiling, packing, and publishing code.</span></span> <span data-ttu-id="0d969-106">引用项目 SDK 的项目有时称为“SDK 样式的项目”。</span><span class="sxs-lookup"><span data-stu-id="0d969-106">A project that references a project SDK is sometimes referred to as an *SDK-style project*.</span></span>

## <a name="available-sdks"></a><span data-ttu-id="0d969-107">可用的 SDK</span><span class="sxs-lookup"><span data-stu-id="0d969-107">Available SDKs</span></span>

<span data-ttu-id="0d969-108">有以下 SDK 可用：</span><span class="sxs-lookup"><span data-stu-id="0d969-108">The following SDKs are available:</span></span>

| <span data-ttu-id="0d969-109">ID</span><span class="sxs-lookup"><span data-stu-id="0d969-109">ID</span></span> | <span data-ttu-id="0d969-110">描述</span><span class="sxs-lookup"><span data-stu-id="0d969-110">Description</span></span> | <span data-ttu-id="0d969-111">存储库</span><span class="sxs-lookup"><span data-stu-id="0d969-111">Repo</span></span>|
| - | - | - |
| `Microsoft.NET.Sdk` | <span data-ttu-id="0d969-112">.NET SDK</span><span class="sxs-lookup"><span data-stu-id="0d969-112">The .NET SDK</span></span> | <https://github.com/dotnet/sdk> |
| `Microsoft.NET.Sdk.Web` | <span data-ttu-id="0d969-113">.NET [Web SDK](/aspnet/core/razor-pages/web-sdk)</span><span class="sxs-lookup"><span data-stu-id="0d969-113">The .NET [Web SDK](/aspnet/core/razor-pages/web-sdk)</span></span> | <https://github.com/dotnet/sdk> |
| `Microsoft.NET.Sdk.Razor` | <span data-ttu-id="0d969-114">.NET [Razor SDK](/aspnet/core/razor-pages/sdk)</span><span class="sxs-lookup"><span data-stu-id="0d969-114">The .NET [Razor SDK](/aspnet/core/razor-pages/sdk)</span></span> |
| `Microsoft.NET.Sdk.Worker` | <span data-ttu-id="0d969-115">.NET 辅助角色服务 SDK</span><span class="sxs-lookup"><span data-stu-id="0d969-115">The .NET Worker Service SDK</span></span> |
| `Microsoft.NET.Sdk.WindowsDesktop` | <span data-ttu-id="0d969-116">WinForms 和 WPF SDK\*</span><span class="sxs-lookup"><span data-stu-id="0d969-116">The WinForms and WPF SDK\*</span></span> | <span data-ttu-id="0d969-117"><https://github.com/dotnet/winforms> 和 <https://github.com/dotnet/wpf></span><span class="sxs-lookup"><span data-stu-id="0d969-117"><https://github.com/dotnet/winforms> and <https://github.com/dotnet/wpf></span></span> |

<span data-ttu-id="0d969-118">.NET SDK 是 .NET 的基本 SDK。</span><span class="sxs-lookup"><span data-stu-id="0d969-118">The .NET SDK is the base SDK for .NET.</span></span> <span data-ttu-id="0d969-119">其他 SDK 引用 .NET SDK，与其他 SDK 关联的项目具有所有可用的 .NET SDK 属性。</span><span class="sxs-lookup"><span data-stu-id="0d969-119">The other SDKs reference the .NET SDK, and projects that are associated with the other SDKs have all the .NET SDK properties available to them.</span></span> <span data-ttu-id="0d969-120">例如，Web SDK 依赖于 .NET SDK 和 Razor SDK。</span><span class="sxs-lookup"><span data-stu-id="0d969-120">The Web SDK, for example, depends on both the .NET SDK and the Razor SDK.</span></span>

<span data-ttu-id="0d969-121">你还可以创建自己的 SDK，并通过 NuGet 进行分发。</span><span class="sxs-lookup"><span data-stu-id="0d969-121">You can also author your own SDK that can be distributed via NuGet.</span></span>

<span data-ttu-id="0d969-122">\* 从 .NET 5.0 开始，Windows 窗体和 Windows Presentation Foundation (WPF) 项目应指定 .NET SDK (`Microsoft.NET.Sdk`)，而不是 `Microsoft.NET.Sdk.WindowsDesktop`。</span><span class="sxs-lookup"><span data-stu-id="0d969-122">\* Starting in .NET 5.0, Windows Forms and Windows Presentation Foundation (WPF) projects should specify the .NET SDK (`Microsoft.NET.Sdk`) instead of `Microsoft.NET.Sdk.WindowsDesktop`.</span></span> <span data-ttu-id="0d969-123">对于这些项目，将 `TargetFramework` 设置为 `net5.0-windows` 并将 `UseWPF` 或 `UseWindowsForms` 设置为 `true` 的操作会自动导入 Windows 桌面 SDK。</span><span class="sxs-lookup"><span data-stu-id="0d969-123">For these projects, setting `TargetFramework` to `net5.0-windows` and `UseWPF` or `UseWindowsForms` to `true` will automatically import the Windows desktop SDK.</span></span> <span data-ttu-id="0d969-124">如果你的项目面向 .NET 5.0 或更高版本，并指定 `Microsoft.NET.Sdk.WindowsDesktop` SDK，则会收到生成警告 NETSDK1137。</span><span class="sxs-lookup"><span data-stu-id="0d969-124">If your project targets .NET 5.0 or later and specifies the `Microsoft.NET.Sdk.WindowsDesktop` SDK, you'll get build warning NETSDK1137.</span></span>

## <a name="project-files"></a><span data-ttu-id="0d969-125">项目文件</span><span class="sxs-lookup"><span data-stu-id="0d969-125">Project files</span></span>

<span data-ttu-id="0d969-126">.NET 项目基于 [MSBuild](/visualstudio/msbuild/msbuild) 格式。</span><span class="sxs-lookup"><span data-stu-id="0d969-126">.NET projects are based on the [MSBuild](/visualstudio/msbuild/msbuild) format.</span></span> <span data-ttu-id="0d969-127">具有扩展名（如用于 C# 项目的 .csproj 和用于 F# 项目的 .fsproj）的项目文件都是 XML 格式的 。</span><span class="sxs-lookup"><span data-stu-id="0d969-127">Project files, which have extensions like *.csproj* for C# projects and *.fsproj* for F# projects, are in XML format.</span></span> <span data-ttu-id="0d969-128">MSBuild 项目文件的根元素是 [Project](/visualstudio/msbuild/project-element-msbuild) 元素。</span><span class="sxs-lookup"><span data-stu-id="0d969-128">The root element of an MSBuild project file is the [Project](/visualstudio/msbuild/project-element-msbuild) element.</span></span> <span data-ttu-id="0d969-129">`Project` 元素有一个可选的 `Sdk` 属性，该属性指定要使用的 SDK（和版本）。</span><span class="sxs-lookup"><span data-stu-id="0d969-129">The `Project` element has an optional `Sdk` attribute that specifies which SDK (and version) to use.</span></span> <span data-ttu-id="0d969-130">若要使用 .NET 工具并构建你的代码，请将 `Sdk` 属性设置为[可用 SDK](#available-sdks) 表中的其中一个 ID。</span><span class="sxs-lookup"><span data-stu-id="0d969-130">To use the .NET tools and build your code, set the `Sdk` attribute to one of the IDs in the [Available SDKs](#available-sdks) table.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
</Project>
```

<span data-ttu-id="0d969-131">若要指定来自 NuGet 的 SDK，请在名称末尾包含版本，或者在 global.json 文件中指定名称和版本。</span><span class="sxs-lookup"><span data-stu-id="0d969-131">To specify an SDK that comes from NuGet, include the version at the end of the name, or specify the name and version in the *global.json* file.</span></span>

```xml
<Project Sdk="MSBuild.Sdk.Extras/2.0.54">
  ...
</Project>
```

<span data-ttu-id="0d969-132">另一种指定 SDK 的方法是使用顶层 [Sdk](/visualstudio/msbuild/sdk-element-msbuild) 元素：</span><span class="sxs-lookup"><span data-stu-id="0d969-132">Another way to specify the SDK is with the top-level [Sdk](/visualstudio/msbuild/sdk-element-msbuild) element:</span></span>

```xml
<Project>
  <Sdk Name="Microsoft.NET.Sdk" />
  ...
</Project>
```

<span data-ttu-id="0d969-133">以这些方式之一引用 SDK 可以极大地简化 .NET 的项目文件。</span><span class="sxs-lookup"><span data-stu-id="0d969-133">Referencing an SDK in one of these ways greatly simplifies project files for .NET.</span></span> <span data-ttu-id="0d969-134">在评估项目时，MSBuild 在项目文件的顶部和底部分别为 `Sdk.props` 和 `Sdk.targets` 添加隐式导入。</span><span class="sxs-lookup"><span data-stu-id="0d969-134">While evaluating the project, MSBuild adds implicit imports for `Sdk.props` at the top of the project file and `Sdk.targets` at the bottom.</span></span>

```xml
<Project>
  <!-- Implicit top import -->
  <Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk" />
  ...
  <!-- Implicit bottom import -->
  <Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk" />
</Project>
```

> [!TIP]
> <span data-ttu-id="0d969-135">在 Windows 计算机上，Sdk.props 和 Sdk.targets 文件位于 %ProgramFiles%\dotnet\sdk\\[version]\Sdks\Microsoft.NET.Sdk\Sdk 文件夹中  。</span><span class="sxs-lookup"><span data-stu-id="0d969-135">On a Windows machine, the *Sdk.props* and *Sdk.targets* files can be found in the *%ProgramFiles%\dotnet\sdk\\[version]\Sdks\Microsoft.NET.Sdk\Sdk* folder.</span></span>

### <a name="preprocess-the-project-file"></a><span data-ttu-id="0d969-136">预处理项目文件</span><span class="sxs-lookup"><span data-stu-id="0d969-136">Preprocess the project file</span></span>

<span data-ttu-id="0d969-137">使用 `dotnet msbuild -preprocess` 命令，可以看到 MSBuild 在包含 SDK 及其目标之后所显示的完全扩展的项目。</span><span class="sxs-lookup"><span data-stu-id="0d969-137">You can see the fully expanded project as MSBuild sees it after the SDK and its targets are included by using the `dotnet msbuild -preprocess` command.</span></span> <span data-ttu-id="0d969-138">[`dotnet msbuild`](../tools/dotnet-msbuild.md) 命令的[预处理](/visualstudio/msbuild/msbuild-command-line-reference#preprocess)开关显示导入的文件、文件源及其在生成中的参与情况，而无需实际生成项目。</span><span class="sxs-lookup"><span data-stu-id="0d969-138">The [preprocess](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) switch of the [`dotnet msbuild`](../tools/dotnet-msbuild.md) command shows which files are imported, their sources, and their contributions to the build without actually building the project.</span></span>

<span data-ttu-id="0d969-139">如果项目有多个目标框架，请将命令的结果指定为 MSBuild 属性，使其仅侧重于框架之一。</span><span class="sxs-lookup"><span data-stu-id="0d969-139">If the project has multiple target frameworks, focus the results of the command on only one framework by specifying it as an MSBuild property.</span></span> <span data-ttu-id="0d969-140">例如：</span><span class="sxs-lookup"><span data-stu-id="0d969-140">For example:</span></span>

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

## <a name="default-includes-and-excludes"></a><span data-ttu-id="0d969-141">默认包含和排除的内容</span><span class="sxs-lookup"><span data-stu-id="0d969-141">Default includes and excludes</span></span>

<span data-ttu-id="0d969-142">SDK 中定义了 [`Compile` 项](/visualstudio/msbuild/common-msbuild-project-items#compile)、[嵌入的资源](/visualstudio/msbuild/common-msbuild-project-items#embeddedresource)和 [`None` 项](/visualstudio/msbuild/common-msbuild-project-items#none)默认包含和排除的内容。</span><span class="sxs-lookup"><span data-stu-id="0d969-142">The default includes and excludes for [`Compile` items](/visualstudio/msbuild/common-msbuild-project-items#compile), [embedded resources](/visualstudio/msbuild/common-msbuild-project-items#embeddedresource), and [`None` items](/visualstudio/msbuild/common-msbuild-project-items#none) are defined in the SDK.</span></span> <span data-ttu-id="0d969-143">与非 SDK .NET 框架项目不同，你无需在项目文件中指定这些项，因为默认设置涵盖了最常见的用例。</span><span class="sxs-lookup"><span data-stu-id="0d969-143">Unlike non-SDK .NET Framework projects, you don't need to specify these items in your project file, because the defaults cover most common use cases.</span></span> <span data-ttu-id="0d969-144">此行为使得项目文件更小、更易于理解和手动编辑（如需要）。</span><span class="sxs-lookup"><span data-stu-id="0d969-144">This behavior makes the project file smaller and easier to understand and edit by hand, if needed.</span></span>

<span data-ttu-id="0d969-145">下表显示在 .NET SDK 中包含和排除的元素和 [glob](https://en.wikipedia.org/wiki/Glob_(programming))：</span><span class="sxs-lookup"><span data-stu-id="0d969-145">The following table shows which elements and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are included and excluded in the .NET SDK:</span></span>

| <span data-ttu-id="0d969-146">元素</span><span class="sxs-lookup"><span data-stu-id="0d969-146">Element</span></span>           | <span data-ttu-id="0d969-147">包含 glob</span><span class="sxs-lookup"><span data-stu-id="0d969-147">Include glob</span></span>                              | <span data-ttu-id="0d969-148">排除 glob</span><span class="sxs-lookup"><span data-stu-id="0d969-148">Exclude glob</span></span>                                                  | <span data-ttu-id="0d969-149">删除 glob</span><span class="sxs-lookup"><span data-stu-id="0d969-149">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| <span data-ttu-id="0d969-150">Compile</span><span class="sxs-lookup"><span data-stu-id="0d969-150">Compile</span></span>           | <span data-ttu-id="0d969-151">\*\*/\*.cs（或其他语言扩展名）</span><span class="sxs-lookup"><span data-stu-id="0d969-151">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="0d969-152">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="0d969-152">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="0d969-153">不可用</span><span class="sxs-lookup"><span data-stu-id="0d969-153">N/A</span></span>                      |
| <span data-ttu-id="0d969-154">EmbeddedResource</span><span class="sxs-lookup"><span data-stu-id="0d969-154">EmbeddedResource</span></span>  | <span data-ttu-id="0d969-155">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="0d969-155">\*\*/\*.resx</span></span>                              | <span data-ttu-id="0d969-156">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="0d969-156">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="0d969-157">不可用</span><span class="sxs-lookup"><span data-stu-id="0d969-157">N/A</span></span>                      |
| <span data-ttu-id="0d969-158">None</span><span class="sxs-lookup"><span data-stu-id="0d969-158">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="0d969-159">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="0d969-159">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="0d969-160">\*\*/\*.cs; \*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="0d969-160">\*\*/\*.cs; \*\*/\*.resx</span></span> |

> [!NOTE]
> <span data-ttu-id="0d969-161">默认情况下，由 `$(BaseOutputPath)` 和 `$(BaseIntermediateOutputPath)` MSBuild 属性表示的 `./bin` 和 `./obj` 文件夹不包含在 glob 中。</span><span class="sxs-lookup"><span data-stu-id="0d969-161">The `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, are excluded from the globs by default.</span></span> <span data-ttu-id="0d969-162">排除由 [DefaultItemExcludes 属性](msbuild-props.md#defaultitemexcludes)表示。</span><span class="sxs-lookup"><span data-stu-id="0d969-162">Excludes are represented by the [DefaultItemExcludes property](msbuild-props.md#defaultitemexcludes).</span></span>

### <a name="build-errors"></a><span data-ttu-id="0d969-163">生成错误</span><span class="sxs-lookup"><span data-stu-id="0d969-163">Build errors</span></span>

<span data-ttu-id="0d969-164">如果在项目文件中显式定义这些项中的任何项，可能会出现类似于以下内容的“NETSDK1022”生成错误：</span><span class="sxs-lookup"><span data-stu-id="0d969-164">If you explicitly define any of these items in your project file, you're likely to get a "NETSDK1022" build error similar to the following:</span></span>

  > <span data-ttu-id="0d969-165">包含重复的“编译”项。</span><span class="sxs-lookup"><span data-stu-id="0d969-165">Duplicate 'Compile' items were included.</span></span> <span data-ttu-id="0d969-166">默认情况下，.NET SDK 包括项目目录中的“编译”项。</span><span class="sxs-lookup"><span data-stu-id="0d969-166">The .NET SDK includes 'Compile' items from your project directory by default.</span></span> <span data-ttu-id="0d969-167">可从项目文件中删除这些项，或如果想要在项目文件中显式包括它们，则将“EnableDefaultCompileItems”属性设为“false”。</span><span class="sxs-lookup"><span data-stu-id="0d969-167">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

  > <span data-ttu-id="0d969-168">包含重复的“EmbeddedResource”项。</span><span class="sxs-lookup"><span data-stu-id="0d969-168">Duplicate 'EmbeddedResource' items were included.</span></span> <span data-ttu-id="0d969-169">默认情况下，.NET SDK 包括项目目录中的“EmbeddedResource”项。</span><span class="sxs-lookup"><span data-stu-id="0d969-169">The .NET SDK includes 'EmbeddedResource' items from your project directory by default.</span></span> <span data-ttu-id="0d969-170">可从项目文件中删除这些项，或如果想要在项目文件中显式包括它们，则将“EnableDefaultEmbeddedResourceItems”属性设为“false”。</span><span class="sxs-lookup"><span data-stu-id="0d969-170">You can either remove these items from your project file, or set the 'EnableDefaultEmbeddedResourceItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

<span data-ttu-id="0d969-171">若要解决此错误，请执行以下操作之一：</span><span class="sxs-lookup"><span data-stu-id="0d969-171">To resolve the errors, do one of the following:</span></span>

- <span data-ttu-id="0d969-172">删除与上表中列出的隐式项匹配的显式 `Compile`、`EmbeddedResource` 或 `None` 项。</span><span class="sxs-lookup"><span data-stu-id="0d969-172">Remove the explicit `Compile`, `EmbeddedResource`, or `None` items that match the implicit ones listed on the previous table.</span></span>

- <span data-ttu-id="0d969-173">若要禁用所有隐式文件包含，请将 [EnableDefaultItems 属性](msbuild-props.md#enabledefaultitems)设置为 `false`：</span><span class="sxs-lookup"><span data-stu-id="0d969-173">Set the [EnableDefaultItems property](msbuild-props.md#enabledefaultitems) to `false` to disable all implicit file inclusion:</span></span>

  ```xml
  <PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
  </PropertyGroup>
  ```

  <span data-ttu-id="0d969-174">若要指定某些文件通过应用发布，仍可以使用相应的已知 MSBuild 机制来实现（例如 `Content` 元素）。</span><span class="sxs-lookup"><span data-stu-id="0d969-174">If you want to specify files to be published with your app, you can still use the known MSBuild mechanisms for that, for example, the `Content` element.</span></span>

- <span data-ttu-id="0d969-175">可选择仅禁用 `Compile`、`EmbeddedResource` 或 `None` glob，方法是将 [EnableDefaultCompileItems](msbuild-props.md#enabledefaultcompileitems)、[EnableDefaultEmbeddedResourceItems](msbuild-props.md#enabledefaultembeddedresourceitems) 或 [EnableDefaultNoneItems](msbuild-props.md#enabledefaultnoneitems) 属性设置为 `false`：</span><span class="sxs-lookup"><span data-stu-id="0d969-175">Selectively disable only `Compile`, `EmbeddedResource`, or `None` globs by setting the [EnableDefaultCompileItems](msbuild-props.md#enabledefaultcompileitems), [EnableDefaultEmbeddedResourceItems](msbuild-props.md#enabledefaultembeddedresourceitems), or [EnableDefaultNoneItems](msbuild-props.md#enabledefaultnoneitems) property to `false`:</span></span>

  ```xml
  <PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
    <EnableDefaultEmbeddedResourceItems>false</EnableDefaultEmbeddedResourceItems>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
  </PropertyGroup>
  ```

  <span data-ttu-id="0d969-176">如果仅禁用 `Compile` glob，则 Visual Studio 中的解决方案资源管理器仍将 \*.cs 项显示为项目的一部分，并作为 `None` 项包含在内。</span><span class="sxs-lookup"><span data-stu-id="0d969-176">If you only disable `Compile` globs, Solution Explorer in Visual Studio still shows \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="0d969-177">若要禁用隐式 `None` glob，请将 `EnableDefaultNoneItems` 也设置为 `false`。</span><span class="sxs-lookup"><span data-stu-id="0d969-177">To disable the implicit `None` glob, set `EnableDefaultNoneItems` to `false` too.</span></span>

## <a name="build-events"></a><span data-ttu-id="0d969-178">生成事件</span><span class="sxs-lookup"><span data-stu-id="0d969-178">Build events</span></span>

<span data-ttu-id="0d969-179">在 SDK 样式的项目中，请使用名为 `PreBuild` 或 `PostBuild` 的 MSBuild 目标，并设置 `PreBuild` 的 `BeforeTargets` 属性或 `PostBuild` 的 `AfterTargets` 属性。</span><span class="sxs-lookup"><span data-stu-id="0d969-179">In SDK-style projects, use an MSBuild target named `PreBuild` or `PostBuild` and set the `BeforeTargets` property for `PreBuild` or the `AfterTargets` property for `PostBuild`.</span></span>

```xml
<Target Name="PreBuild" BeforeTargets="PreBuildEvent">
    <Exec Command="&quot;$(ProjectDir)PreBuildEvent.bat&quot; &quot;$(ProjectDir)..\&quot; &quot;$(ProjectDir)&quot; &quot;$(TargetDir)&quot;" />
</Target>

<Target Name="PostBuild" AfterTargets="PostBuildEvent">
   <Exec Command="echo Output written to $(TargetDir)" />
</Target>
```

> [!NOTE]
>
> - <span data-ttu-id="0d969-180">可以为 MSBuild 目标使用任何名称。</span><span class="sxs-lookup"><span data-stu-id="0d969-180">You can use any name for the MSBuild targets.</span></span> <span data-ttu-id="0d969-181">但是，Visual Studio IDE 会识别 `PreBuild` 和 `PostBuild` 目标，因此通过使用这些名称，可以在 IDE 中编辑命令。</span><span class="sxs-lookup"><span data-stu-id="0d969-181">However, the Visual Studio IDE recognizes `PreBuild` and `PostBuild` targets, so by using those names, you can edit the commands in the IDE.</span></span>
> - <span data-ttu-id="0d969-182">不建议在 SDK 样式的项目中使用属性 `PreBuildEvent` 和 `PostBuildEvent`，因为无法解析 `$(ProjectDir)` 这样的宏。</span><span class="sxs-lookup"><span data-stu-id="0d969-182">The properties `PreBuildEvent` and `PostBuildEvent` are not recommended in SDK-style projects, because macros such as `$(ProjectDir)` aren't resolved.</span></span> <span data-ttu-id="0d969-183">例如，以下代码是不受支持的：</span><span class="sxs-lookup"><span data-stu-id="0d969-183">For example, the following code is not supported:</span></span>
>
> ```xml
> <PropertyGroup>
>   <PreBuildEvent>"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)"</PreBuildEvent>
> </PropertyGroup>
> ```

## <a name="customize-the-build"></a><span data-ttu-id="0d969-184">自定义生成</span><span class="sxs-lookup"><span data-stu-id="0d969-184">Customize the build</span></span>

<span data-ttu-id="0d969-185">可以通过多种方式[自定义生成](/visualstudio/msbuild/customize-your-build)。</span><span class="sxs-lookup"><span data-stu-id="0d969-185">There are various ways to [customize a build](/visualstudio/msbuild/customize-your-build).</span></span> <span data-ttu-id="0d969-186">建议通过将属性作为参数传递给 [msbuild](/visualstudio/msbuild/msbuild-command-line-reference) 或 [dotnet](../tools/index.md) 命令来重写该属性。</span><span class="sxs-lookup"><span data-stu-id="0d969-186">You may want to override a property by passing it as an argument to an [msbuild](/visualstudio/msbuild/msbuild-command-line-reference) or [dotnet](../tools/index.md) command.</span></span> <span data-ttu-id="0d969-187">还可以将属性添加到项目文件或 Directory.Build.props 文件中。</span><span class="sxs-lookup"><span data-stu-id="0d969-187">You can also add the property to the project file or to a *Directory.Build.props* file.</span></span> <span data-ttu-id="0d969-188">有关 .NET 项目的有用属性列表，请参见 [.NET SDK 项目的 MSBuild 参考](msbuild-props.md)。</span><span class="sxs-lookup"><span data-stu-id="0d969-188">For a list of useful properties for .NET projects, see [MSBuild reference for .NET SDK projects](msbuild-props.md).</span></span>

### <a name="custom-targets"></a><span data-ttu-id="0d969-189">自定义目标</span><span class="sxs-lookup"><span data-stu-id="0d969-189">Custom targets</span></span>

<span data-ttu-id="0d969-190">.NET 项目可以打包自定义的 MSBuild 目标和属性，以供使用该包的项目使用。</span><span class="sxs-lookup"><span data-stu-id="0d969-190">.NET projects can package custom MSBuild targets and properties for use by projects that consume the package.</span></span> <span data-ttu-id="0d969-191">如果要执行以下操作，请使用此类型的可扩展性：</span><span class="sxs-lookup"><span data-stu-id="0d969-191">Use this type of extensibility when you want to:</span></span>

- <span data-ttu-id="0d969-192">扩展生成过程。</span><span class="sxs-lookup"><span data-stu-id="0d969-192">Extend the build process.</span></span>
- <span data-ttu-id="0d969-193">访问生成过程的工件，如生成的文件。</span><span class="sxs-lookup"><span data-stu-id="0d969-193">Access artifacts of the build process, such as generated files.</span></span>
- <span data-ttu-id="0d969-194">检查调用生成的配置。</span><span class="sxs-lookup"><span data-stu-id="0d969-194">Inspect the configuration under which the build is invoked.</span></span>

<span data-ttu-id="0d969-195">通过在项目的生成文件夹中以 `<package_id>.targets` 或 `<package_id>.props`（例如 `Contoso.Utility.UsefulStuff.targets`）的形式放置文件，可以添加自定义生成目标或属性。</span><span class="sxs-lookup"><span data-stu-id="0d969-195">You add custom build targets or properties by placing files in the form `<package_id>.targets` or `<package_id>.props` (for example, `Contoso.Utility.UsefulStuff.targets`) in the *build* folder of the project.</span></span>

<span data-ttu-id="0d969-196">以下 XML 是 .csproj 文件中的一个片段，该文件指示 [`dotnet pack`](../tools/dotnet-pack.md) 命令打包的内容。</span><span class="sxs-lookup"><span data-stu-id="0d969-196">The following XML is a snippet from a *.csproj* file that instructs the [`dotnet pack`](../tools/dotnet-pack.md) command what to package.</span></span> <span data-ttu-id="0d969-197">`<ItemGroup Label="dotnet pack instructions">` 元素将目标文件放入包内的生成文件夹中。</span><span class="sxs-lookup"><span data-stu-id="0d969-197">The `<ItemGroup Label="dotnet pack instructions">` element places the targets files into the *build* folder inside the package.</span></span> <span data-ttu-id="0d969-198">`<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` 元素将程序集和 .json 文件放入生成文件夹 。</span><span class="sxs-lookup"><span data-stu-id="0d969-198">The `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` element places the assemblies and *.json* files into the *build* folder.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  ...
  <ItemGroup Label="dotnet pack instructions">
    <Content Include="build\*.targets">
      <Pack>true</Pack>
      <PackagePath>build\</PackagePath>
    </Content>
  </ItemGroup>
  <Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">
    <!-- Collect these items inside a target that runs after build but before packaging. -->
    <ItemGroup>
      <Content Include="$(OutputPath)\*.dll;$(OutputPath)\*.json">
        <Pack>true</Pack>
        <PackagePath>build\</PackagePath>
      </Content>
    </ItemGroup>
  </Target>
  ...

</Project>
```

<span data-ttu-id="0d969-199">若要在项目中使用自定义目标，请添加指向包及其版本的 `PackageReference` 元素。</span><span class="sxs-lookup"><span data-stu-id="0d969-199">To consume a custom target in your project, add a `PackageReference` element that points to the package and its version.</span></span> <span data-ttu-id="0d969-200">与工具不同，自定义目标包包含在消费项目的依赖项闭包中。</span><span class="sxs-lookup"><span data-stu-id="0d969-200">Unlike the tools, the custom targets package is included in the consuming project's dependency closure.</span></span>

<span data-ttu-id="0d969-201">你可以配置自定义目标的使用方式。</span><span class="sxs-lookup"><span data-stu-id="0d969-201">You can configure how to use the custom target.</span></span> <span data-ttu-id="0d969-202">由于它是 MSBuild 目标，因此会依赖于给定的目标并在另一个目标后运行，也可使用 `dotnet msbuild -t:<target-name>` 命令手动调用。</span><span class="sxs-lookup"><span data-stu-id="0d969-202">Since it's an MSBuild target, it can depend on a given target, run after another target, or be manually invoked by using the `dotnet msbuild -t:<target-name>` command.</span></span> <span data-ttu-id="0d969-203">若要提供更好的用户体验，可以合并基于项目的工具和自定义目标。</span><span class="sxs-lookup"><span data-stu-id="0d969-203">However, to provide a better user experience, you can combine per-project tools and custom targets.</span></span> <span data-ttu-id="0d969-204">在此方案中，每个项目工具接受所需的任何参数，并将其转换为执行目标所需的 [`dotnet msbuild`](../tools/dotnet-msbuild.md) 调用。</span><span class="sxs-lookup"><span data-stu-id="0d969-204">In this scenario, the per-project tool accepts whatever parameters are needed and translates that into the required [`dotnet msbuild`](../tools/dotnet-msbuild.md) invocation that executes the target.</span></span> <span data-ttu-id="0d969-205">有关此类协同作用的示例，请访问 [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) 项目中的 [2016 年编程马拉松 MVP 峰会示例](https://github.com/dotnet/MVPSummitHackathon2016)存储库。</span><span class="sxs-lookup"><span data-stu-id="0d969-205">You can see a sample of this kind of synergy on the [MVP Summit 2016 Hackathon samples](https://github.com/dotnet/MVPSummitHackathon2016) repo in the [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) project.</span></span>

## <a name="see-also"></a><span data-ttu-id="0d969-206">请参阅</span><span class="sxs-lookup"><span data-stu-id="0d969-206">See also</span></span>

- [<span data-ttu-id="0d969-207">安装 .NET Core</span><span class="sxs-lookup"><span data-stu-id="0d969-207">Install .NET Core</span></span>](../install/index.yml)
- [<span data-ttu-id="0d969-208">如何使用 MSBuild 项目 SDK</span><span class="sxs-lookup"><span data-stu-id="0d969-208">How to use MSBuild project SDKs</span></span>](/visualstudio/msbuild/how-to-use-project-sdk)
- [<span data-ttu-id="0d969-209">使用 NuGet 打包自定义 MSBuild 目标和属性</span><span class="sxs-lookup"><span data-stu-id="0d969-209">Package custom MSBuild targets and props with NuGet</span></span>](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package)
