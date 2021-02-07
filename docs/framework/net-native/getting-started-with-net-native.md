---
description: 了解详细信息：入门与 .NET Native
title: .NET Native 入门
ms.date: 03/30/2017
ms.assetid: fc9e04e8-2d05-4870-8cd6-5bd276814afc
ms.openlocfilehash: 6079e21764ebc39515eb9b9f217057d916da8942
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747798"
---
# <a name="getting-started-with-net-native"></a><span data-ttu-id="28f16-103">.NET Native 入门</span><span class="sxs-lookup"><span data-stu-id="28f16-103">Getting Started with .NET Native</span></span>

<span data-ttu-id="28f16-104">无论是在编写适用于 Windows 10 的新 Windows 应用，还是在迁移现有的 Windows 应用商店应用，都可以按照同一套过程操作。</span><span class="sxs-lookup"><span data-stu-id="28f16-104">Whether you are writing a new Windows app for Windows 10 or you are migrating an existing Windows Store app, you can follow the same set of procedures.</span></span> <span data-ttu-id="28f16-105">若要创建 .NET Native 应用，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="28f16-105">To create a .NET Native app, follow these steps:</span></span>

1. <span data-ttu-id="28f16-106">[开发面向 Windows 10 的通用 Windows 平台 (UWP) 应用](#Step1)，测试应用的调试版本以确保其正常工作。</span><span class="sxs-lookup"><span data-stu-id="28f16-106">[Develop a Universal Windows Platform (UWP) app that targets Windows 10](#Step1), and test the debug builds of your app to ensure that it works properly.</span></span>

2. <span data-ttu-id="28f16-107">[处理额外的反射和序列化用法](#Step2)。</span><span class="sxs-lookup"><span data-stu-id="28f16-107">[Handle additional reflection and serialization usage](#Step2).</span></span>

3. <span data-ttu-id="28f16-108">[部署和测试应用的发布版本](#Step3)。</span><span class="sxs-lookup"><span data-stu-id="28f16-108">[Deploy and test the release builds of your app](#Step3).</span></span>

4. <span data-ttu-id="28f16-109">[手动解决丢失的元数据](#Step4)，并重复[步骤 3](#Step3)，直到所有问题都得到解决为止。</span><span class="sxs-lookup"><span data-stu-id="28f16-109">[Manually resolve missing metadata](#Step4), and repeat [step 3](#Step3) until all issues are resolved.</span></span>

> [!NOTE]
> <span data-ttu-id="28f16-110">如果要将现有的 Windows 应用商店应用迁移到 .NET Native，请务必查看将 [windows 应用商店应用迁移到 .NET Native](migrating-your-windows-store-app-to-net-native.md)。</span><span class="sxs-lookup"><span data-stu-id="28f16-110">If you are migrating an existing Windows Store app to .NET Native, be sure to review [Migrating Your Windows Store App to .NET Native](migrating-your-windows-store-app-to-net-native.md).</span></span>

<a name="Step1"></a>

## <a name="step-1-develop-and-test-debug-builds-of-your-uwp-app"></a><span data-ttu-id="28f16-111">步骤 1：开发和测试 UWP 应用的调试版本</span><span class="sxs-lookup"><span data-stu-id="28f16-111">Step 1: Develop and test debug builds of your UWP app</span></span>

<span data-ttu-id="28f16-112">不管是开发新的应用还是迁移现有应用，均遵循用于任何 Windows 应用的同一流程进行操作。</span><span class="sxs-lookup"><span data-stu-id="28f16-112">Whether you are developing a new app or migrating an existing one, you follow the same process as for any Windows app.</span></span>

1. <span data-ttu-id="28f16-113">通过使用针对 Visual C# 或 Visual Basic 的通用 Windows 应用模板，在 Visual Studio 中创建新的 UWP 项目。</span><span class="sxs-lookup"><span data-stu-id="28f16-113">Create a new UWP project in Visual Studio by using the Universal Windows app template for Visual C# or Visual Basic.</span></span> <span data-ttu-id="28f16-114">默认情况下，所有 UWP 应用程序均以 CoreCLR 为目标，且其发布版本通过使用 .NET Native 工具链进行编译。</span><span class="sxs-lookup"><span data-stu-id="28f16-114">By default, all UWP applications target the CoreCLR and their release builds are compiled by using the .NET Native tool chain.</span></span>

2. <span data-ttu-id="28f16-115">请注意，使用 .NET Native 工具链和不使用它来编译 UWP 应用项目之间存在一些已知的兼容性问题。</span><span class="sxs-lookup"><span data-stu-id="28f16-115">Note that there are some known compatibility issues between compiling UWP app projects with the .NET Native tool chain and without it.</span></span> <span data-ttu-id="28f16-116">有关更多信息，请参阅 [迁移指南](migrating-your-windows-store-app-to-net-native.md) 。</span><span class="sxs-lookup"><span data-stu-id="28f16-116">Refer to the [migration guide](migrating-your-windows-store-app-to-net-native.md) for more information.</span></span>

<span data-ttu-id="28f16-117">你现在可以针对在本地系统 (或模拟器) 中运行的 .NET Native 外围应用程序，编写 c # 或 Visual Basic 代码。</span><span class="sxs-lookup"><span data-stu-id="28f16-117">You can now write C# or Visual Basic code against the .NET Native surface area that runs on the local system (or in the simulator).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="28f16-118">开发你的应用时，在代码中用任何序列化或反射时都应提起注意。</span><span class="sxs-lookup"><span data-stu-id="28f16-118">As you develop your app, note any use of serialization or reflection in your code.</span></span>

<span data-ttu-id="28f16-119">默认情况下，调试版本进行 JIT 编译以启用快速 F5 部署，而发布版本则使用 .NET Native 预编译技术进行编译。</span><span class="sxs-lookup"><span data-stu-id="28f16-119">By default, debug builds are JIT-compiled to enable rapid F5 deployment, while release builds are compiled by using the .NET Native pre-compilation technology.</span></span> <span data-ttu-id="28f16-120">这意味着在使用 .NET Native 工具链来编译应用的调试版本之前，应生成和测试它们以确保其正常工作。</span><span class="sxs-lookup"><span data-stu-id="28f16-120">This means you should build and test the debug builds of your app to ensure that they work normally before compiling them with the .NET Native tool chain.</span></span>

<a name="Step2"></a>

## <a name="step-2-handle-additional-reflection-and-serialization-usage"></a><span data-ttu-id="28f16-121">步骤 2：处理其他反射和序列化用法</span><span class="sxs-lookup"><span data-stu-id="28f16-121">Step 2: Handle additional reflection and serialization usage</span></span>

<span data-ttu-id="28f16-122">创建运行时指令文件 Default.rd.xml 时，会将其自动添加到项目中。</span><span class="sxs-lookup"><span data-stu-id="28f16-122">A runtime directives file, Default.rd.xml, is automatically added to your project when you create it.</span></span> <span data-ttu-id="28f16-123">如果在 C# 中进行开发，则该文件位于项目的 **“属性”** 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="28f16-123">If you develop in C#, it is found in your project's **Properties** folder.</span></span> <span data-ttu-id="28f16-124">如果在 Visual Basic 中进行开发，则该文件位于项目的 **“我的项目”** 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="28f16-124">If you develop in Visual Basic, it is found in your project's **My Project** folder.</span></span>

> [!NOTE]
> <span data-ttu-id="28f16-125">有关提供为何需要运行时指令文件的背景的 .NET 本机编译过程的概述，请参阅 [.NET 本机和编译](net-native-and-compilation.md)。</span><span class="sxs-lookup"><span data-stu-id="28f16-125">For an overview of the .NET Native compilation process that provides background on why a runtime directives file is needed, see [.NET Native and Compilation](net-native-and-compilation.md).</span></span>

<span data-ttu-id="28f16-126">运行时指令文件用于定义应用在运行时所需的元数据。</span><span class="sxs-lookup"><span data-stu-id="28f16-126">The runtime directives file is used to define the metadata that your app needs at run time.</span></span> <span data-ttu-id="28f16-127">某些情况下，文件的默认版本可能是够用的。</span><span class="sxs-lookup"><span data-stu-id="28f16-127">In some cases, the default version of the file may be adequate.</span></span> <span data-ttu-id="28f16-128">然而，一些依赖于序列化或反射的代码可能需要运行时指令文件中的其他条目。</span><span class="sxs-lookup"><span data-stu-id="28f16-128">However, some code that relies on serialization or reflection may require additional entries in the runtime directives file.</span></span>

<span data-ttu-id="28f16-129">**序列化**</span><span class="sxs-lookup"><span data-stu-id="28f16-129">**Serialization**</span></span>

<span data-ttu-id="28f16-130">有两类序列化程序，并且每一类可能都要求在运行时指令文件中有额外的条目：</span><span class="sxs-lookup"><span data-stu-id="28f16-130">There are two categories of serializers, and both may require additional entries in the runtime directives file:</span></span>

- <span data-ttu-id="28f16-131">非基于反射的序列化程序。</span><span class="sxs-lookup"><span data-stu-id="28f16-131">Non-reflection based serializers.</span></span> <span data-ttu-id="28f16-132">在 .NET Framework 类库中找到的序列化程序，比如 <xref:System.Runtime.Serialization.DataContractSerializer>\ <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>和 <xref:System.Xml.Serialization.XmlSerializer> 类，不依赖反射。</span><span class="sxs-lookup"><span data-stu-id="28f16-132">The serializers found in the .NET Framework class library, such as the <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer> classes, do not rely on reflection.</span></span> <span data-ttu-id="28f16-133">然而，它们需要在基于对象的基础生成的代码得到序列化或反序列化。</span><span class="sxs-lookup"><span data-stu-id="28f16-133">However, they do require that code be generated based on the object to be serialized or deserialized.</span></span>  <span data-ttu-id="28f16-134">有关更多信息，请参阅 [Serialization and Metadata](serialization-and-metadata.md)中的“Microsoft 序列化程序”部分。</span><span class="sxs-lookup"><span data-stu-id="28f16-134">For more information, see the "Microsoft Serializers" section in [Serialization and Metadata](serialization-and-metadata.md).</span></span>

- <span data-ttu-id="28f16-135">第三方序列化程序。</span><span class="sxs-lookup"><span data-stu-id="28f16-135">Third-party serializers.</span></span> <span data-ttu-id="28f16-136">第三方序列化库（最常见的是 Newtonsoft.json JSON 序列化程序）通常基于反射，并要求.rd.xml 文件中的条目 \* 支持对象序列化和反序列化。</span><span class="sxs-lookup"><span data-stu-id="28f16-136">Third-party serialization libraries, the most common of which is the Newtonsoft JSON serializer, are generally reflection-based and require entries in the \*.rd.xml file to support object serialization and deserialization.</span></span> <span data-ttu-id="28f16-137">有关更多信息，请参阅 [Serialization and Metadata](serialization-and-metadata.md)中的“第三方序列化程序”部分。</span><span class="sxs-lookup"><span data-stu-id="28f16-137">For more information, see the "Third-Party Serializers" section in [Serialization and Metadata](serialization-and-metadata.md).</span></span>

<span data-ttu-id="28f16-138">**依赖反射的方法**</span><span class="sxs-lookup"><span data-stu-id="28f16-138">**Methods that rely on reflection**</span></span>

<span data-ttu-id="28f16-139">在某些情况下，代码中对反射的使用是不明显的。</span><span class="sxs-lookup"><span data-stu-id="28f16-139">In some cases, the use of reflection in code is not obvious.</span></span> <span data-ttu-id="28f16-140">一些常见的 API 或编程模式不被视为是反射 API 的一部分，但依赖反射成功执行。</span><span class="sxs-lookup"><span data-stu-id="28f16-140">Some common APIs or programming patterns aren't considered part of the reflection API but rely on reflection to execute successfully.</span></span> <span data-ttu-id="28f16-141">这包括以下类型实例化和方法构造方法：</span><span class="sxs-lookup"><span data-stu-id="28f16-141">This includes the following type instantiation and method construction methods:</span></span>

- <span data-ttu-id="28f16-142"><xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> 方法</span><span class="sxs-lookup"><span data-stu-id="28f16-142">The <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method</span></span>

- <span data-ttu-id="28f16-143"><xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> 和 <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> 方法</span><span class="sxs-lookup"><span data-stu-id="28f16-143">The <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> and <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> methods</span></span>

- <span data-ttu-id="28f16-144"><xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="28f16-144">The <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="28f16-145">有关详细信息，请参阅 [APIs That Rely on Reflection](apis-that-rely-on-reflection.md)。</span><span class="sxs-lookup"><span data-stu-id="28f16-145">For more information, see [APIs That Rely on Reflection](apis-that-rely-on-reflection.md).</span></span>

> [!NOTE]
> <span data-ttu-id="28f16-146">运行时指令文件中使用的类型名称必须是完全限定的。</span><span class="sxs-lookup"><span data-stu-id="28f16-146">Type names used in runtime directives files must be fully qualified.</span></span> <span data-ttu-id="28f16-147">例如，该文件必须指定“System.String”而不是“String”。</span><span class="sxs-lookup"><span data-stu-id="28f16-147">For example, the file must specify "System.String" instead of "String".</span></span>

<a name="Step3"></a>

## <a name="step-3-deploy-and-test-the-release-builds-of-your-app"></a><span data-ttu-id="28f16-148">步骤 3：部署和测试应用的发布版本</span><span class="sxs-lookup"><span data-stu-id="28f16-148">Step 3: Deploy and test the release builds of your app</span></span>

<span data-ttu-id="28f16-149">在更新运行时指令文件之后，你可以重新生成和部署应用的发布版本。</span><span class="sxs-lookup"><span data-stu-id="28f16-149">After you’ve updated the runtime directives file, you can rebuild and deploy release builds of your app.</span></span> <span data-ttu-id="28f16-150">.NET Native 二进制文件放置在项目 "**属性**" 对话框的 "**生成输出路径**"**文本框中指定** 目录的 ILC 子目录中。未在此文件夹中的二进制文件尚未用 .NET Native 编译。</span><span class="sxs-lookup"><span data-stu-id="28f16-150">.NET Native binaries are placed in the ILC.out subdirectory of the directory specified in the **Build output path** text box of  the project's **Properties** dialog box, **Compile** tab. Binaries that aren't in this folder haven't been compiled with .NET Native.</span></span> <span data-ttu-id="28f16-151">彻底测试你的应用，并在其各个目标平台上测试所有方案（包括失败方案）。</span><span class="sxs-lookup"><span data-stu-id="28f16-151">Test your app thoroughly, and test all scenarios, including failure scenarios, on each of its target platforms.</span></span>

<span data-ttu-id="28f16-152">如果应用无法正常工作（尤其是在运行时引发 [MissingMetadataException](missingmetadataexception-class-net-native.md) 或 [MissingInteropDataException](missinginteropdataexception-class-net-native.md) 异常的情况下），请按照下一部分的指令进行操作，即[步骤 4：手动解决丢失的元数据](#Step4)。</span><span class="sxs-lookup"><span data-stu-id="28f16-152">If your app doesn’t work properly (particularly in cases where it throws [MissingMetadataException](missingmetadataexception-class-net-native.md) or [MissingInteropDataException](missinginteropdataexception-class-net-native.md) exceptions at run time), follow the instructions in the next section, [Step 4: Manually resolve missing metadata](#Step4).</span></span> <span data-ttu-id="28f16-153">启用最可能的异常可能会帮助发现这些 bug。</span><span class="sxs-lookup"><span data-stu-id="28f16-153">Enabling first-chance exceptions may help you find these bugs.</span></span>

<span data-ttu-id="28f16-154">如果已测试并调试了应用的调试版本，并且确信已消除 [MissingMetadataException](missingmetadataexception-class-net-native.md) 和 [MissingInteropDataException](missinginteropdataexception-class-net-native.md) 异常，则应将应用作为优化 .NET Native 应用进行测试。</span><span class="sxs-lookup"><span data-stu-id="28f16-154">When you’ve tested and debugged the debug builds of your app and you’re confident that you’ve eliminated the [MissingMetadataException](missingmetadataexception-class-net-native.md) and [MissingInteropDataException](missinginteropdataexception-class-net-native.md) exceptions, you should test your app as an optimized .NET Native app.</span></span> <span data-ttu-id="28f16-155">为此，请将活动项目配置从“调试”改为“发布”。</span><span class="sxs-lookup"><span data-stu-id="28f16-155">To do this, change your active project configuration from **Debug** to **Release**.</span></span>

<a name="Step4"></a>

## <a name="step-4-manually-resolve-missing-metadata"></a><span data-ttu-id="28f16-156">步骤 4：手动解决丢失的元数据</span><span class="sxs-lookup"><span data-stu-id="28f16-156">Step 4: Manually resolve missing metadata</span></span>

<span data-ttu-id="28f16-157">在桌面上不会遇到的 .NET Native 最常见的失败是运行时 [MissingMetadataException](missingmetadataexception-class-net-native.md)、 [MissingInteropDataException](missinginteropdataexception-class-net-native.md)或 [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) 异常。</span><span class="sxs-lookup"><span data-stu-id="28f16-157">The most common failure you'll encounter with .NET Native that you don't encounter on the desktop is a runtime [MissingMetadataException](missingmetadataexception-class-net-native.md), [MissingInteropDataException](missinginteropdataexception-class-net-native.md), or [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exception.</span></span> <span data-ttu-id="28f16-158">在某些情况下，元数据的丢失在不可预测的行为中或甚至在应用失败的情况下可以自行显露。</span><span class="sxs-lookup"><span data-stu-id="28f16-158">In some cases, the absence of metadata can manifest itself in unpredictable behavior or even in app failures.</span></span> <span data-ttu-id="28f16-159">此部分讨论了你该如何通过将指令添加到运行时指令文件来调试和解决这些异常。</span><span class="sxs-lookup"><span data-stu-id="28f16-159">This section discusses how you can debug and resolve these exceptions by adding directives to the runtime directives file.</span></span> <span data-ttu-id="28f16-160">有关运行时指令的格式信息，请参阅[运行时指令 (rd.xml) 配置文件参考](runtime-directives-rd-xml-configuration-file-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="28f16-160">For information about the format of runtime directives, see [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md).</span></span> <span data-ttu-id="28f16-161">添加运行时指令后，你应该再次 [部署并检测你的应用](#Step3) 并解决任何新的 [丢失元数据异常](missingmetadataexception-class-net-native.md)、 [丢失互操作数据异常](missinginteropdataexception-class-net-native.md)和  [丢失运行时项目异常](missingruntimeartifactexception-class-net-native.md) 异常，直到你停止遇到任何异常。</span><span class="sxs-lookup"><span data-stu-id="28f16-161">After you’ve added runtime directives, you should [deploy and test your app](#Step3) again and resolve any new [MissingMetadataException](missingmetadataexception-class-net-native.md), [MissingInteropDataException](missinginteropdataexception-class-net-native.md), and  [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exceptions until you encounter no more exceptions.</span></span>

> [!TIP]
> <span data-ttu-id="28f16-162">在更高级别上指定你的运行时指令，使你的应用能够适应代码变化。</span><span class="sxs-lookup"><span data-stu-id="28f16-162">Specify the runtime directives at a high level to enable your app to be resilient to code changes.</span></span>  <span data-ttu-id="28f16-163">我们推荐在命名空间和类型级别而不在成员级别添加运行时指令。</span><span class="sxs-lookup"><span data-stu-id="28f16-163">We recommend adding runtime directives at the namespace and type levels rather than the member level.</span></span> <span data-ttu-id="28f16-164">注意，你可能需要在弹性和编译时间较长的较大二进制代码之间做一个权衡。</span><span class="sxs-lookup"><span data-stu-id="28f16-164">Note that there may be a tradeoff between resiliency and larger binaries with longer compile times.</span></span>

<span data-ttu-id="28f16-165">当处理一个丢失元数据异常时，请考虑以下问题：</span><span class="sxs-lookup"><span data-stu-id="28f16-165">When addressing a missing metadata exception, consider these issues:</span></span>

- <span data-ttu-id="28f16-166">应用在发生异常之前正在执行什么操作？</span><span class="sxs-lookup"><span data-stu-id="28f16-166">What was the app trying to do before the exception?</span></span>

  - <span data-ttu-id="28f16-167">例如，它是正在绑定、序列化或反序列化数据？还是正在直接使用反射 API？</span><span class="sxs-lookup"><span data-stu-id="28f16-167">For example, was it data binding, serializing or deserializing data, or directly using the reflection API?</span></span>

- <span data-ttu-id="28f16-168">这是一个孤立情形吗？或者你是否认为针对其他类型时也会遇到同样的问题？</span><span class="sxs-lookup"><span data-stu-id="28f16-168">Is this an isolated case, or do you believe you'll encounter the same issue for other types?</span></span>

  - <span data-ttu-id="28f16-169">例如，当在应用的对象模型中序列化一个类型时，引发了 [丢失元数据异常](missingmetadataexception-class-net-native.md) 异常。</span><span class="sxs-lookup"><span data-stu-id="28f16-169">For example, a [MissingMetadataException](missingmetadataexception-class-net-native.md) exception is thrown when serializing a type in the app’s object model.</span></span>  <span data-ttu-id="28f16-170">如果你知道其他要得到序列化的类型，可以同时为这些类型（或者为它们包含的命名空间，这要视代码的组织情况而定）添加运行指令。</span><span class="sxs-lookup"><span data-stu-id="28f16-170">If you know other types that will be serialized, you can add runtime directives for those types (or for their containing namespaces, depending on how well the code is organized) at the same time.</span></span>

- <span data-ttu-id="28f16-171">你可以重写代码，不让它使用反射吗？</span><span class="sxs-lookup"><span data-stu-id="28f16-171">Can you rewrite the code so it doesn’t use reflection?</span></span>

  - <span data-ttu-id="28f16-172">例如，当你知道使用什么类型时代码是否使用了 `dynamic` 关键字？</span><span class="sxs-lookup"><span data-stu-id="28f16-172">For example, does the code use the `dynamic` keyword when you know what type to expect?</span></span>

  - <span data-ttu-id="28f16-173">当有更好的选择时，代码是否调用了一个依赖反射的方法？</span><span class="sxs-lookup"><span data-stu-id="28f16-173">Does the code call a method that depends on reflection when some better alternative is available?</span></span>

> [!NOTE]
> <span data-ttu-id="28f16-174">有关如何处理因反射中的差异以及桌面应用和 .NET Native 中的元数据的可用性而造成的问题的其他信息，请参阅 [依赖于反射的 api](apis-that-rely-on-reflection.md)。</span><span class="sxs-lookup"><span data-stu-id="28f16-174">For additional information about handling problems that stem from differences in reflection and the availability of metadata in desktop apps and .NET Native, see [APIs That Rely on Reflection](apis-that-rely-on-reflection.md).</span></span>

<span data-ttu-id="28f16-175">要了解处理在检测应用的过程中发生的异常和其他问题的特定实例，请参阅：</span><span class="sxs-lookup"><span data-stu-id="28f16-175">For some specific examples of handling exceptions and other issues that occur when testing your app, see:</span></span>

- [<span data-ttu-id="28f16-176">示例：处理绑定数据时出现的异常</span><span class="sxs-lookup"><span data-stu-id="28f16-176">Example: Handling Exceptions When Binding Data</span></span>](example-handling-exceptions-when-binding-data.md)

- [<span data-ttu-id="28f16-177">示例：动态编程疑难解答</span><span class="sxs-lookup"><span data-stu-id="28f16-177">Example: Troubleshooting Dynamic Programming</span></span>](example-troubleshooting-dynamic-programming.md)

- [<span data-ttu-id="28f16-178">.NET 本机应用中的运行时异常</span><span class="sxs-lookup"><span data-stu-id="28f16-178">Runtime Exceptions in .NET Native Apps</span></span>](runtime-exceptions-in-net-native-apps.md)

## <a name="see-also"></a><span data-ttu-id="28f16-179">请参阅</span><span class="sxs-lookup"><span data-stu-id="28f16-179">See also</span></span>

- [<span data-ttu-id="28f16-180">运行时指令 (rd.xml) 配置文件引用</span><span class="sxs-lookup"><span data-stu-id="28f16-180">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- <span data-ttu-id="28f16-181">[.NET Native 安装和配置](/previous-versions/dn600164(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="28f16-181">[.NET Native Setup and Configuration](/previous-versions/dn600164(v=vs.110))</span></span>
- [<span data-ttu-id="28f16-182">.NET Native 和编译</span><span class="sxs-lookup"><span data-stu-id="28f16-182">.NET Native and Compilation</span></span>](net-native-and-compilation.md)
- [<span data-ttu-id="28f16-183">反射和 .NET Native</span><span class="sxs-lookup"><span data-stu-id="28f16-183">Reflection and .NET Native</span></span>](reflection-and-net-native.md)
- [<span data-ttu-id="28f16-184">利用反射的 API</span><span class="sxs-lookup"><span data-stu-id="28f16-184">APIs That Rely on Reflection</span></span>](apis-that-rely-on-reflection.md)
- [<span data-ttu-id="28f16-185">序列化和元数据</span><span class="sxs-lookup"><span data-stu-id="28f16-185">Serialization and Metadata</span></span>](serialization-and-metadata.md)
- [<span data-ttu-id="28f16-186">将 Windows 应用商店应用迁移到 .NET Native</span><span class="sxs-lookup"><span data-stu-id="28f16-186">Migrating Your Windows Store App to .NET Native</span></span>](migrating-your-windows-store-app-to-net-native.md)
