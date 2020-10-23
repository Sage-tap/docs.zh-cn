---
ms.openlocfilehash: edff55d540f08e8a9fd4d0687aaf6bd963ee3a84
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539446"
---
### <a name="blazor-rendertreeframe-readonly-public-fields-have-become-properties"></a><span data-ttu-id="d3d61-101">Blazor：RenderTreeFrame readonly public 字段已变为属性</span><span class="sxs-lookup"><span data-stu-id="d3d61-101">Blazor: RenderTreeFrame readonly public fields have become properties</span></span>

<span data-ttu-id="d3d61-102">在 ASP.NET Core 3.0 和 3.1 中，<xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame> 结构公开了各种 `readonly public` 字段，包括 <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame.FrameType>、<xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame.Sequence> 等。</span><span class="sxs-lookup"><span data-stu-id="d3d61-102">In ASP.NET Core 3.0 and 3.1, the <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame> struct exposed various `readonly public` fields, including <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame.FrameType>, <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame.Sequence>, and others.</span></span> <span data-ttu-id="d3d61-103">在 ASP.NET Core 5.0 RC1 及更高版本中，所有 `readonly public` 字段都更改为 `readonly public` 属性。</span><span class="sxs-lookup"><span data-stu-id="d3d61-103">In ASP.NET Core 5.0 RC1 and later versions, all the `readonly public` fields changed to `readonly public` properties.</span></span>

<span data-ttu-id="d3d61-104">此更改不会影响很多开发人员，原因如下：</span><span class="sxs-lookup"><span data-stu-id="d3d61-104">This change won't affect many developers because:</span></span>

* <span data-ttu-id="d3d61-105">只使用 `.razor` 文件（或甚至手动 <xref:Microsoft.AspNetCore.Components.Rendering.RenderTreeBuilder> 调用）来定义其组件的任何应用或库都不会直接引用此类型。</span><span class="sxs-lookup"><span data-stu-id="d3d61-105">Any app or library that simply uses `.razor` files (or even manual <xref:Microsoft.AspNetCore.Components.Rendering.RenderTreeBuilder> calls) to define its components wouldn't be referencing this type directly.</span></span>
* <span data-ttu-id="d3d61-106">`RenderTreeFrame` 类型本身被视为实现详细信息，不用于框架外部。</span><span class="sxs-lookup"><span data-stu-id="d3d61-106">The `RenderTreeFrame` type itself is regarded as an implementation detail, not intended for use outside of the framework.</span></span> <span data-ttu-id="d3d61-107">ASP.NET Core 3.0 及更高版本包括一个分析器，如果直接使用该类型，则该分析器会发出编译器警告。</span><span class="sxs-lookup"><span data-stu-id="d3d61-107">ASP.NET Core 3.0 and later includes an analyzer that issues compiler warnings if the type is being used directly.</span></span>
* <span data-ttu-id="d3d61-108">即使直接引用 `RenderTreeFrame`，此更改仍将破坏二进制文件，而不会破坏源。</span><span class="sxs-lookup"><span data-stu-id="d3d61-108">Even if you reference `RenderTreeFrame` directly, this change is binary-breaking but not source-breaking.</span></span> <span data-ttu-id="d3d61-109">也就是说，现有的源代码将正常编译并运行。</span><span class="sxs-lookup"><span data-stu-id="d3d61-109">That is, your existing source code will compile and behave properly.</span></span> <span data-ttu-id="d3d61-110">仅当针对 .NET Core 3.x 框架进行编译，然后针对 .NET 5.0 RC1 及更高版本的框架运行这些二进制文件时，才会遇到问题。</span><span class="sxs-lookup"><span data-stu-id="d3d61-110">You'll only encounter an issue if compiling against a .NET Core 3.x framework and then running those binaries against the .NET 5.0 RC1 and later framework.</span></span>

<span data-ttu-id="d3d61-111">有关讨论，请参阅 GitHub 问题 [dotnet/aspnetcore#25727](https://github.com/dotnet/aspnetcore/issues/25727)。</span><span class="sxs-lookup"><span data-stu-id="d3d61-111">For discussion, see GitHub issue [dotnet/aspnetcore#25727](https://github.com/dotnet/aspnetcore/issues/25727).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d3d61-112">引入的版本</span><span class="sxs-lookup"><span data-stu-id="d3d61-112">Version introduced</span></span>

<span data-ttu-id="d3d61-113">5.0 RC1</span><span class="sxs-lookup"><span data-stu-id="d3d61-113">5.0 RC1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="d3d61-114">旧行为</span><span class="sxs-lookup"><span data-stu-id="d3d61-114">Old behavior</span></span>

<span data-ttu-id="d3d61-115">`RenderTreeFrame` 上的公共成员被定义为字段。</span><span class="sxs-lookup"><span data-stu-id="d3d61-115">Public members on `RenderTreeFrame` are defined as fields.</span></span> <span data-ttu-id="d3d61-116">例如，`renderTreeFrame.Sequence` 和 `renderTreeFrame.ElementName`。</span><span class="sxs-lookup"><span data-stu-id="d3d61-116">For example, `renderTreeFrame.Sequence` and `renderTreeFrame.ElementName`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="d3d61-117">新行为</span><span class="sxs-lookup"><span data-stu-id="d3d61-117">New behavior</span></span>

<span data-ttu-id="d3d61-118">`RenderTreeFrame` 上的公共成员被定义名称与以前相同的属性。</span><span class="sxs-lookup"><span data-stu-id="d3d61-118">Public members on `RenderTreeFrame` are defined as properties with the same names as before.</span></span> <span data-ttu-id="d3d61-119">例如，`renderTreeFrame.Sequence` 和 `renderTreeFrame.ElementName`。</span><span class="sxs-lookup"><span data-stu-id="d3d61-119">For example, `renderTreeFrame.Sequence` and `renderTreeFrame.ElementName`.</span></span>

<span data-ttu-id="d3d61-120">如果在此更改后，尚未重新编译旧的预编译代码，它可能会引发与此类似的异常：*MissingFieldException:找不到字段:"Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame.FrameType"* 。</span><span class="sxs-lookup"><span data-stu-id="d3d61-120">If older precompiled code hasn't been recompiled since this change, it may throw an exception similar to *MissingFieldException: Field not found: 'Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame.FrameType'*.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d3d61-121">更改原因</span><span class="sxs-lookup"><span data-stu-id="d3d61-121">Reason for change</span></span>

<span data-ttu-id="d3d61-122">若要在 ASP.NET Core 5.0 中的 Blazor 组件呈现方面实现强影响力的性能改进，此更改是必需的。</span><span class="sxs-lookup"><span data-stu-id="d3d61-122">This change was necessary to implement high-impact performance improvements in Blazor component rendering in ASP.NET Core 5.0.</span></span> <span data-ttu-id="d3d61-123">保持相同级别的安全和封装。</span><span class="sxs-lookup"><span data-stu-id="d3d61-123">The same levels of safety and encapsulation are maintained.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d3d61-124">建议操作</span><span class="sxs-lookup"><span data-stu-id="d3d61-124">Recommended action</span></span>

<span data-ttu-id="d3d61-125">大多数 Blazor 开发人员不受此更改的影响。</span><span class="sxs-lookup"><span data-stu-id="d3d61-125">Most Blazor developers are unaffected by this change.</span></span> <span data-ttu-id="d3d61-126">此更改更有可能影响库和包作者，但仅在极少数情况下会造成影响。</span><span class="sxs-lookup"><span data-stu-id="d3d61-126">The change is more likely to affect library and package authors, but only in rare cases.</span></span> <span data-ttu-id="d3d61-127">具体来说，如果你要执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="d3d61-127">Specifically, if you're developing:</span></span>

* <span data-ttu-id="d3d61-128">开发一款应用，并使用 ASP.NET Core 3.x 或者升级到 5.0 RC1 或更高版本，则无需更改自己的代码。</span><span class="sxs-lookup"><span data-stu-id="d3d61-128">An app and using ASP.NET Core 3.x or upgrading to 5.0 RC1 or later, you don't need to change your own code.</span></span> <span data-ttu-id="d3d61-129">但是，如果依赖于已升级的库来进行此更改，则需要更新到该库的更新版本。</span><span class="sxs-lookup"><span data-stu-id="d3d61-129">However, if you depend on a library that upgraded to account for this change, then you need to update to a newer version of that library.</span></span>
* <span data-ttu-id="d3d61-130">开发一个库，并希望仅支持 ASP.NET Core 5.0 RC1 或更高版本，则无需执行任何操作。</span><span class="sxs-lookup"><span data-stu-id="d3d61-130">A library and want to support only ASP.NET Core 5.0 RC1 or later, no action is needed.</span></span> <span data-ttu-id="d3d61-131">只需确保项目文件声明 `net5.0` 或更高版本的 `<TargetFramework>` 值。</span><span class="sxs-lookup"><span data-stu-id="d3d61-131">Just ensure that your project file declares a `<TargetFramework>` value of `net5.0` or a later version.</span></span>
* <span data-ttu-id="d3d61-132">开发一个库，并希望支持 ASP.NET Core 3.x 和 5.0，则需要确定代码是否读取任何 `RenderTreeFrame` 成员。</span><span class="sxs-lookup"><span data-stu-id="d3d61-132">A library and want to support both ASP.NET Core 3.x *and* 5.0, determine whether your code reads any `RenderTreeFrame` members.</span></span> <span data-ttu-id="d3d61-133">例如，计算 `someRenderTreeFrame.FrameType`。</span><span class="sxs-lookup"><span data-stu-id="d3d61-133">For example, evaluating `someRenderTreeFrame.FrameType`.</span></span>
  * <span data-ttu-id="d3d61-134">大多数库不会读取 `RenderTreeFrame` 成员，包括包含 `.razor` 组件的库。</span><span class="sxs-lookup"><span data-stu-id="d3d61-134">Most libraries won't read `RenderTreeFrame` members, including libraries that contain `.razor` components.</span></span> <span data-ttu-id="d3d61-135">在这种情况下，无需执行任何操作。</span><span class="sxs-lookup"><span data-stu-id="d3d61-135">In this case, no action is needed.</span></span>
  * <span data-ttu-id="d3d61-136">但是，如果你的库执行此操作，则你需要进行多目标操作以同时支持 `netstandard2.1` 和 `net5.0`。</span><span class="sxs-lookup"><span data-stu-id="d3d61-136">However, if your library does that, you'll need to multi-target to support both `netstandard2.1` and `net5.0`.</span></span> <span data-ttu-id="d3d61-137">在项目文件中应用以下更改：</span><span class="sxs-lookup"><span data-stu-id="d3d61-137">Apply the following changes in your project file:</span></span>
    * <span data-ttu-id="d3d61-138">将现有 `<TargetFramework>` 元素替换为 `<TargetFrameworks>netstandard2.0;net5.0</TargetFrameworks>`。</span><span class="sxs-lookup"><span data-stu-id="d3d61-138">Replace the existing `<TargetFramework>` element with `<TargetFrameworks>netstandard2.0;net5.0</TargetFrameworks>`.</span></span>
    * <span data-ttu-id="d3d61-139">使用条件 `Microsoft.AspNetCore.Components` 包引用来说明希望支持的两个版本。</span><span class="sxs-lookup"><span data-stu-id="d3d61-139">Use a conditional `Microsoft.AspNetCore.Components` package reference to account for both versions you wish to support.</span></span> <span data-ttu-id="d3d61-140">例如：</span><span class="sxs-lookup"><span data-stu-id="d3d61-140">For example:</span></span>

        ```xml
        <PackageReference Include="Microsoft.AspNetCore.Components" Version="3.0.0" Condition="'$(TargetFramework)' == 'netstandard2.0'" />
        <PackageReference Include="Microsoft.AspNetCore.Components" Version="5.0.0-rc.1.*" Condition="'$(TargetFramework)' != 'netstandard2.0'" />
        ```

<span data-ttu-id="d3d61-141">有关进一步说明，请参阅此[显示 @jsakamoto 如何已升级 `Toolbelt.Blazor.HeadElement` 库的差异](https://github.com/jsakamoto/Toolbelt.Blazor.HeadElement/commit/090df430ba725f9420d412753db8104e8c32bf51)。</span><span class="sxs-lookup"><span data-stu-id="d3d61-141">For further clarification, see this [diff showing how @jsakamoto already upgraded the `Toolbelt.Blazor.HeadElement` library](https://github.com/jsakamoto/Toolbelt.Blazor.HeadElement/commit/090df430ba725f9420d412753db8104e8c32bf51).</span></span>

#### <a name="category"></a><span data-ttu-id="d3d61-142">类别</span><span class="sxs-lookup"><span data-stu-id="d3d61-142">Category</span></span>

<span data-ttu-id="d3d61-143">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d3d61-143">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d3d61-144">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="d3d61-144">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame`

-->