---
description: 了解详细信息： .NET Native 反射 API 参考
title: .NET Native 本机反射 API 参考
ms.date: 03/30/2017
ms.assetid: 0429c049-22a3-4ba1-9cc8-f6ee91e31d9c
ms.openlocfilehash: 44786812b5bf8c7bd470a588730b7b03ee91f00c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738515"
---
# <a name="net-native-reflection-api-reference"></a><span data-ttu-id="f9c3c-103">.NET Native 本机反射 API 参考</span><span class="sxs-lookup"><span data-stu-id="f9c3c-103">.NET Native Reflection API Reference</span></span>

<span data-ttu-id="f9c3c-104">.NET Native 包括三个新的异常类型： MissingInteropDataException、MissingMetadataException 和 MissingRuntimeArtifactException。 [system.runtime.compilerservices.](missinginteropdataexception-class-net-native.md)、 [](missingmetadataexception-class-net-native.md)和[](missingruntimeartifactexception-class-net-native.md)。</span><span class="sxs-lookup"><span data-stu-id="f9c3c-104">.NET Native includes three new exception types: [System.Runtime.CompilerServices.MissingInteropDataException](missinginteropdataexception-class-net-native.md), [System.Reflection.MissingMetadataException](missingmetadataexception-class-net-native.md), and [System.Reflection.MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md).</span></span> <span data-ttu-id="f9c3c-105">请注意有关所有三种异常类型的以下内容：</span><span class="sxs-lookup"><span data-stu-id="f9c3c-105">Note the following about all three exception types:</span></span>  
  
 <span data-ttu-id="f9c3c-106">这些类型仅供内部使用。</span><span class="sxs-lookup"><span data-stu-id="f9c3c-106">These types are for internal use only.</span></span>  
 <span data-ttu-id="f9c3c-107">这三种异常类型仅用于 .NET Native 工具链。</span><span class="sxs-lookup"><span data-stu-id="f9c3c-107">These three exception types are for the use of the .NET Native tool chain only.</span></span> <span data-ttu-id="f9c3c-108">当 .NET Native 工具链检测到不允许程序继续执行的缺失数据时，将引发异常。</span><span class="sxs-lookup"><span data-stu-id="f9c3c-108">The exceptions are thrown when the .NET Native tool chain detects missing data that does not allow program execution to continue.</span></span>  
  
 <span data-ttu-id="f9c3c-109">不在代码中处理这些异常。</span><span class="sxs-lookup"><span data-stu-id="f9c3c-109">Do not handle these exceptions in your code.</span></span>  
 <span data-ttu-id="f9c3c-110">这些异常指示缺少应用程序所需的元数据（ [MissingInteropDataException](missinginteropdataexception-class-net-native.md) 和 [MissingMetadataException](missingmetadataexception-class-net-native.md) 异常）或缺少应用程序所需的实现代码（ [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) 异常）。</span><span class="sxs-lookup"><span data-stu-id="f9c3c-110">These exceptions indicate either that metadata needed by your application is absent (the [MissingInteropDataException](missinginteropdataexception-class-net-native.md) and [MissingMetadataException](missingmetadataexception-class-net-native.md) exceptions) or that implementation code needed by your application is missing (the [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exception).</span></span> <span data-ttu-id="f9c3c-111">可以通过修改运行时指令 (.rd.xml) 文件，使所需的元数据或实现代码在运行时可用，从而更正这些异常条件。</span><span class="sxs-lookup"><span data-stu-id="f9c3c-111">You correct these exception conditions by modifying a runtime directives (.rd.xml) file to make the required metadata or implementation code available at runtime.</span></span> <span data-ttu-id="f9c3c-112">有关更多信息，请参见 [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="f9c3c-112">For more information, see [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md).</span></span> <span data-ttu-id="f9c3c-113">有两个故障排除程序可用于为运行时指令文件提供合适的条目，指令文件将消除 [MissingMetadataException](missingmetadataexception-class-net-native.md) 和 [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) 异常：</span><span class="sxs-lookup"><span data-stu-id="f9c3c-113">Two troubleshooters are available that supply the appropriate entries for your runtime directives file that will eliminate [MissingMetadataException](missingmetadataexception-class-net-native.md) and [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exceptions:</span></span>  
  
- <span data-ttu-id="f9c3c-114">类型的 [MissingMetadataException 故障排除程序](https://dotnet.github.io/native/troubleshooter/type.html) 。</span><span class="sxs-lookup"><span data-stu-id="f9c3c-114">The [MissingMetadataException troubleshooter](https://dotnet.github.io/native/troubleshooter/type.html) for types.</span></span>  
  
- <span data-ttu-id="f9c3c-115">方法的 [MissingMetadataException 故障排除程序](https://dotnet.github.io/native/troubleshooter/method.html) 。</span><span class="sxs-lookup"><span data-stu-id="f9c3c-115">The [MissingMetadataException troubleshooter](https://dotnet.github.io/native/troubleshooter/method.html) for methods.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f9c3c-116">此引用记录了三种对 .NET Native 唯一的异常类型。</span><span class="sxs-lookup"><span data-stu-id="f9c3c-116">This reference documents three exception types that are unique to .NET Native.</span></span> <span data-ttu-id="f9c3c-117">有关 .NET Framework 核心反射 API 的参考文档，请参阅 <xref:System.Reflection> <xref:System.Reflection.Context> 和 <xref:System.Reflection.Emit> 命名空间。</span><span class="sxs-lookup"><span data-stu-id="f9c3c-117">For reference documentation for the .NET Framework core reflection API, see the <xref:System.Reflection>, <xref:System.Reflection.Context> and <xref:System.Reflection.Emit> namespaces.</span></span> <span data-ttu-id="f9c3c-118">要查看 .NET Framework 核心互操作 API 的应用文档，请参阅 <xref:System.Runtime.InteropServices>。</span><span class="sxs-lookup"><span data-stu-id="f9c3c-118">For reference documentation for the .NET Framework core interop API, see <xref:System.Runtime.InteropServices>.</span></span>  
  
## <a name="systemreflection-namespace"></a><span data-ttu-id="f9c3c-119">System.Reflection 命名空间</span><span class="sxs-lookup"><span data-stu-id="f9c3c-119">System.Reflection namespace</span></span>  

 <span data-ttu-id="f9c3c-120"><xref:System.Reflection> 命名空间包含用于 .NET Framework 中的反射的核心类型。</span><span class="sxs-lookup"><span data-stu-id="f9c3c-120">The <xref:System.Reflection> namespace contains the core types used for reflection in the .NET Framework.</span></span> <span data-ttu-id="f9c3c-121">对于 .NET Native，它还包括两个新的异常类型：</span><span class="sxs-lookup"><span data-stu-id="f9c3c-121">For .NET Native, it also includes two new exception types:</span></span>  
  
|<span data-ttu-id="f9c3c-122">实例</span><span class="sxs-lookup"><span data-stu-id="f9c3c-122">Class</span></span>|<span data-ttu-id="f9c3c-123">说明</span><span class="sxs-lookup"><span data-stu-id="f9c3c-123">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="f9c3c-124">MissingMetadataException</span><span class="sxs-lookup"><span data-stu-id="f9c3c-124">MissingMetadataException</span></span>](missingmetadataexception-class-net-native.md)|<span data-ttu-id="f9c3c-125">当反射用于检索不存在的元数据时会引起此异常。</span><span class="sxs-lookup"><span data-stu-id="f9c3c-125">The exception that is thrown when reflection is used to retrieve metadata that isn't present.</span></span>|  
|[<span data-ttu-id="f9c3c-126">MissingRuntimeArtifactException</span><span class="sxs-lookup"><span data-stu-id="f9c3c-126">MissingRuntimeArtifactException</span></span>](missingruntimeartifactexception-class-net-native.md)|<span data-ttu-id="f9c3c-127">当一个类型或类型成员的元数据可用但其实现已遭到删除时会引发此异常。</span><span class="sxs-lookup"><span data-stu-id="f9c3c-127">The exception that is thrown when metadata for a type or type member is available but its implementation has been removed.</span></span>|  
  
 <span data-ttu-id="f9c3c-128">要查看有关此命名空间中其他类型的文档，请参阅 .NET Framework 文档集中的 <xref:System.Reflection> 引用页面。</span><span class="sxs-lookup"><span data-stu-id="f9c3c-128">For documentation about the other types in this namespace, see the <xref:System.Reflection> reference pages in the .NET Framework documentation set.</span></span>  
  
## <a name="systemruntimecompilerservices-namespace"></a><span data-ttu-id="f9c3c-129">System.Runtime.CompilerServices 命名空间</span><span class="sxs-lookup"><span data-stu-id="f9c3c-129">System.Runtime.CompilerServices namespace</span></span>  

 <span data-ttu-id="f9c3c-130"><xref:System.Runtime.CompilerServices> 命名空间包括通过语言编译器为用户设计的类型。</span><span class="sxs-lookup"><span data-stu-id="f9c3c-130">The <xref:System.Runtime.CompilerServices> namespace includes types designed for user by language compilers.</span></span> <span data-ttu-id="f9c3c-131">对于 .NET Native，它还包含一个新的异常类型：</span><span class="sxs-lookup"><span data-stu-id="f9c3c-131">For .NET Native, it also includes a new exception type:</span></span>  
  
|<span data-ttu-id="f9c3c-132">实例</span><span class="sxs-lookup"><span data-stu-id="f9c3c-132">Class</span></span>|<span data-ttu-id="f9c3c-133">说明</span><span class="sxs-lookup"><span data-stu-id="f9c3c-133">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="f9c3c-134">MissingInteropDataException</span><span class="sxs-lookup"><span data-stu-id="f9c3c-134">MissingInteropDataException</span></span>](missinginteropdataexception-class-net-native.md)|<span data-ttu-id="f9c3c-135">当手动封送方法被调用但一个类型的元数据无法通过动态分析找到或无法在运行时指令文件中找到时，会引发该异常。</span><span class="sxs-lookup"><span data-stu-id="f9c3c-135">The exception that is thrown when a manual marshaling method is called, but metadata for a type isn't found by static analysis or in a runtime directives file.</span></span>|  
  
 <span data-ttu-id="f9c3c-136">要查看有关此命名空间中其他类型的文档，请参阅 .NET Framework 文档集中的 <xref:System.Runtime.CompilerServices> 引用页面。</span><span class="sxs-lookup"><span data-stu-id="f9c3c-136">For documentation about the other types in this namespace, see the <xref:System.Runtime.CompilerServices> reference pages in the .NET Framework documentation set.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9c3c-137">请参阅</span><span class="sxs-lookup"><span data-stu-id="f9c3c-137">See also</span></span>

- [<span data-ttu-id="f9c3c-138">MissingInteropDataException 类</span><span class="sxs-lookup"><span data-stu-id="f9c3c-138">MissingInteropDataException Class</span></span>](missinginteropdataexception-class-net-native.md)
- [<span data-ttu-id="f9c3c-139">MissingMetadataException 类</span><span class="sxs-lookup"><span data-stu-id="f9c3c-139">MissingMetadataException Class</span></span>](missingmetadataexception-class-net-native.md)
- [<span data-ttu-id="f9c3c-140">MissingRuntimeArtifactException 类</span><span class="sxs-lookup"><span data-stu-id="f9c3c-140">MissingRuntimeArtifactException Class</span></span>](missingruntimeartifactexception-class-net-native.md)
- [<span data-ttu-id="f9c3c-141">入门</span><span class="sxs-lookup"><span data-stu-id="f9c3c-141">Getting Started</span></span>](getting-started-with-net-native.md)
