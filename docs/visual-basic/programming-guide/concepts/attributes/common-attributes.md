---
description: '了解详细信息： (Visual Basic 的公共属性) '
title: 通用属性
ms.date: 07/20/2015
ms.assetid: 11fe4894-1bf9-4525-a36b-cddcd3a5d22b
ms.openlocfilehash: 875554b69a23640c2d67367c93b56c34c286df37
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100437782"
---
# <a name="common-attributes-visual-basic"></a><span data-ttu-id="02c6a-103">常见特性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="02c6a-103">Common Attributes (Visual Basic)</span></span>

<span data-ttu-id="02c6a-104">本主题介绍 Visual Basic 程序中最常用的属性。</span><span class="sxs-lookup"><span data-stu-id="02c6a-104">This topic describes the attributes that are most commonly used in Visual Basic programs.</span></span>

- [<span data-ttu-id="02c6a-105">全局属性</span><span class="sxs-lookup"><span data-stu-id="02c6a-105">Global Attributes</span></span>](#Global)

- [<span data-ttu-id="02c6a-106">过时特性</span><span class="sxs-lookup"><span data-stu-id="02c6a-106">Obsolete Attribute</span></span>](#Obsolete)

- [<span data-ttu-id="02c6a-107">条件属性</span><span class="sxs-lookup"><span data-stu-id="02c6a-107">Conditional Attribute</span></span>](#Conditional)

- [<span data-ttu-id="02c6a-108">调用方信息特性</span><span class="sxs-lookup"><span data-stu-id="02c6a-108">Caller Info Attributes</span></span>](#CallerInfo)

- [<span data-ttu-id="02c6a-109">Visual Basic 特性</span><span class="sxs-lookup"><span data-stu-id="02c6a-109">Visual Basic Attributes</span></span>](#VB)

## <a name="global-attributes"></a><a name="Global"></a> <span data-ttu-id="02c6a-110">全局属性</span><span class="sxs-lookup"><span data-stu-id="02c6a-110">Global Attributes</span></span>

<span data-ttu-id="02c6a-111">大多数特性应用于特定语言元素，如类或方法；但是，一些特性是全局特性 - 它们应用于整个程序集或模块。</span><span class="sxs-lookup"><span data-stu-id="02c6a-111">Most attributes are applied to specific language elements such as classes or methods; however, some attributes are global—they apply to an entire assembly or module.</span></span> <span data-ttu-id="02c6a-112">例如，<xref:System.Reflection.AssemblyVersionAttribute> 属性可用于将版本信息嵌入程序集，如下所示：</span><span class="sxs-lookup"><span data-stu-id="02c6a-112">For example, the <xref:System.Reflection.AssemblyVersionAttribute> attribute can be used to embed version information into an assembly, like this:</span></span>

```vb
<Assembly: AssemblyVersion("1.0.0.0")>
```

<span data-ttu-id="02c6a-113">全局特性显示在任何顶级 `Imports` 语句之后、任何类型、模块或命名空间声明之前的源代码中。</span><span class="sxs-lookup"><span data-stu-id="02c6a-113">Global attributes appear in the source code after any top-level `Imports` statements and before any type, module, or namespace declarations.</span></span> <span data-ttu-id="02c6a-114">全局特性可以出现在多个源文件中，但必须在单个编译过程中编译这些文件。</span><span class="sxs-lookup"><span data-stu-id="02c6a-114">Global attributes can appear in multiple source files, but the files must be compiled in a single compilation pass.</span></span> <span data-ttu-id="02c6a-115">对于 Visual Basic 项目，全局属性通常放在 AssemblyInfo 文件中 (在 Visual Studio 中创建项目时，将自动创建该文件) 。</span><span class="sxs-lookup"><span data-stu-id="02c6a-115">For Visual Basic projects, global attributes are generally put in the AssemblyInfo.vb file (the file is created automatically when you create a project in Visual Studio).</span></span>

<span data-ttu-id="02c6a-116">程序集特性是提供程序集相关信息的值。</span><span class="sxs-lookup"><span data-stu-id="02c6a-116">Assembly attributes are values that provide information about an assembly.</span></span> <span data-ttu-id="02c6a-117">它们分为以下几类：</span><span class="sxs-lookup"><span data-stu-id="02c6a-117">They fall into the following categories:</span></span>

- <span data-ttu-id="02c6a-118">程序集标识特性</span><span class="sxs-lookup"><span data-stu-id="02c6a-118">Assembly identity attributes</span></span>

- <span data-ttu-id="02c6a-119">信息性特性</span><span class="sxs-lookup"><span data-stu-id="02c6a-119">Informational attributes</span></span>

- <span data-ttu-id="02c6a-120">程序集清单特性</span><span class="sxs-lookup"><span data-stu-id="02c6a-120">Assembly manifest attributes</span></span>

### <a name="assembly-identity-attributes"></a><span data-ttu-id="02c6a-121">程序集标识特性。</span><span class="sxs-lookup"><span data-stu-id="02c6a-121">Assembly Identity Attributes</span></span>

<span data-ttu-id="02c6a-122">三个特性（与强名称（如果适用））组合起来可以确定程序集的标识：名称、版本和区域性。</span><span class="sxs-lookup"><span data-stu-id="02c6a-122">Three attributes (with a strong name, if applicable) determine the identity of an assembly: name, version, and culture.</span></span> <span data-ttu-id="02c6a-123">这些特性构成程序集的全名，在代码中引用程序集时必需使用。</span><span class="sxs-lookup"><span data-stu-id="02c6a-123">These attributes form the full name of the assembly and are required when you reference it in code.</span></span> <span data-ttu-id="02c6a-124">可使用特性设置程序集的版本和区域性。</span><span class="sxs-lookup"><span data-stu-id="02c6a-124">You can set an assembly's version and culture using attributes.</span></span> <span data-ttu-id="02c6a-125">但是，创建程序集时，根据包含程序集清单的文件，由编译器、[程序集信息对话框](/visualstudio/ide/reference/assembly-information-dialog-box)中的 Visual Studio IDE 或程序集链接器 (Al.exe) 设置名称值。</span><span class="sxs-lookup"><span data-stu-id="02c6a-125">However, the name value is set by the compiler, the Visual Studio IDE in the [Assembly Information Dialog Box](/visualstudio/ide/reference/assembly-information-dialog-box), or the Assembly Linker (Al.exe) when the assembly is created, based on the file that contains the assembly manifest.</span></span> <span data-ttu-id="02c6a-126"><xref:System.Reflection.AssemblyFlagsAttribute> 属性指定程序集的多个副本是否可以共存。</span><span class="sxs-lookup"><span data-stu-id="02c6a-126">The <xref:System.Reflection.AssemblyFlagsAttribute> attribute specifies whether multiple copies of the assembly can coexist.</span></span>

<span data-ttu-id="02c6a-127">下表显示标识特性。</span><span class="sxs-lookup"><span data-stu-id="02c6a-127">The following table shows the identity attributes.</span></span>

|<span data-ttu-id="02c6a-128">特性</span><span class="sxs-lookup"><span data-stu-id="02c6a-128">Attribute</span></span>|<span data-ttu-id="02c6a-129">目的</span><span class="sxs-lookup"><span data-stu-id="02c6a-129">Purpose</span></span>|
|---------------|-------------|
|<xref:System.Reflection.AssemblyName>|<span data-ttu-id="02c6a-130">详细描述程序集的标识。</span><span class="sxs-lookup"><span data-stu-id="02c6a-130">Fully describes the identity of an assembly.</span></span>|
|<xref:System.Reflection.AssemblyVersionAttribute>|<span data-ttu-id="02c6a-131">指定程序集的版本。</span><span class="sxs-lookup"><span data-stu-id="02c6a-131">Specifies the version of an assembly.</span></span>|
|<xref:System.Reflection.AssemblyCultureAttribute>|<span data-ttu-id="02c6a-132">指定程序集支持的区域性。</span><span class="sxs-lookup"><span data-stu-id="02c6a-132">Specifies which culture the assembly supports.</span></span>|
|<xref:System.Reflection.AssemblyFlagsAttribute>|<span data-ttu-id="02c6a-133">指定程序集是否支持在同一计算机上、同一进程中或同一应用程序域中并行执行。</span><span class="sxs-lookup"><span data-stu-id="02c6a-133">Specifies whether an assembly supports side-by-side execution on the same computer, in the same process, or in the same application domain.</span></span>|

### <a name="informational-attributes"></a><span data-ttu-id="02c6a-134">信息性特性</span><span class="sxs-lookup"><span data-stu-id="02c6a-134">Informational Attributes</span></span>

<span data-ttu-id="02c6a-135">信息性特性可用于提供程序集的其他公司或产品信息。</span><span class="sxs-lookup"><span data-stu-id="02c6a-135">You can use informational attributes to provide additional company or product information for an assembly.</span></span> <span data-ttu-id="02c6a-136">下表显示 <xref:System.Reflection?displayProperty=nameWithType> 命名空间中定义的信息性属性。</span><span class="sxs-lookup"><span data-stu-id="02c6a-136">The following table shows the informational attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>

|<span data-ttu-id="02c6a-137">特性</span><span class="sxs-lookup"><span data-stu-id="02c6a-137">Attribute</span></span>|<span data-ttu-id="02c6a-138">目的</span><span class="sxs-lookup"><span data-stu-id="02c6a-138">Purpose</span></span>|
|---------------|-------------|
|<xref:System.Reflection.AssemblyProductAttribute>|<span data-ttu-id="02c6a-139">定义为程序集清单指定产品名称的自定义属性。</span><span class="sxs-lookup"><span data-stu-id="02c6a-139">Defines a custom attribute that specifies a product name for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyTrademarkAttribute>|<span data-ttu-id="02c6a-140">定义为程序集清单指定商标的自定义属性。</span><span class="sxs-lookup"><span data-stu-id="02c6a-140">Defines a custom attribute that specifies a trademark for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|<span data-ttu-id="02c6a-141">定义为程序集清单指定信息性版本的自定义属性。</span><span class="sxs-lookup"><span data-stu-id="02c6a-141">Defines a custom attribute that specifies an informational version for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyCompanyAttribute>|<span data-ttu-id="02c6a-142">定义为程序集清单指定公司名称的自定义属性。</span><span class="sxs-lookup"><span data-stu-id="02c6a-142">Defines a custom attribute that specifies a company name for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyCopyrightAttribute>|<span data-ttu-id="02c6a-143">定义为程序集清单指定版权的自定义属性。</span><span class="sxs-lookup"><span data-stu-id="02c6a-143">Defines a custom attribute that specifies a copyright for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyFileVersionAttribute>|<span data-ttu-id="02c6a-144">指示编译器使用 Win32 文件版本资源的特定版本号。</span><span class="sxs-lookup"><span data-stu-id="02c6a-144">Instructs the compiler to use a specific version number for the Win32 file version resource.</span></span>|
|<xref:System.CLSCompliantAttribute>|<span data-ttu-id="02c6a-145">指示程序集是否符合公共语言规范 (CLS)。</span><span class="sxs-lookup"><span data-stu-id="02c6a-145">Indicates whether the assembly is compliant with the Common Language Specification (CLS).</span></span>|

### <a name="assembly-manifest-attributes"></a><span data-ttu-id="02c6a-146">程序集清单特性</span><span class="sxs-lookup"><span data-stu-id="02c6a-146">Assembly Manifest Attributes</span></span>

<span data-ttu-id="02c6a-147">程序集清单特性可用于提供程序集清单中的信息。</span><span class="sxs-lookup"><span data-stu-id="02c6a-147">You can use assembly manifest attributes to provide information in the assembly manifest.</span></span> <span data-ttu-id="02c6a-148">这些信息包括标题、说明、默认别名和配置。</span><span class="sxs-lookup"><span data-stu-id="02c6a-148">This includes title, description, default alias, and configuration.</span></span> <span data-ttu-id="02c6a-149">下表显示 <xref:System.Reflection?displayProperty=nameWithType> 命名空间中定义的程序集清单属性。</span><span class="sxs-lookup"><span data-stu-id="02c6a-149">The following table shows the assembly manifest attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>

|<span data-ttu-id="02c6a-150">特性</span><span class="sxs-lookup"><span data-stu-id="02c6a-150">Attribute</span></span>|<span data-ttu-id="02c6a-151">目的</span><span class="sxs-lookup"><span data-stu-id="02c6a-151">Purpose</span></span>|
|---------------|-------------|
|<xref:System.Reflection.AssemblyTitleAttribute>|<span data-ttu-id="02c6a-152">定义为程序集清单指定程序集标题的自定义属性。</span><span class="sxs-lookup"><span data-stu-id="02c6a-152">Defines a custom attribute that specifies an assembly title for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyDescriptionAttribute>|<span data-ttu-id="02c6a-153">定义为程序集清单指定程序集说明的自定义属性。</span><span class="sxs-lookup"><span data-stu-id="02c6a-153">Defines a custom attribute that specifies an assembly description for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyConfigurationAttribute>|<span data-ttu-id="02c6a-154">定义为程序集清单指定程序集配置（如零售或调试）的自定义属性。</span><span class="sxs-lookup"><span data-stu-id="02c6a-154">Defines a custom attribute that specifies an assembly configuration (such as retail or debug) for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|<span data-ttu-id="02c6a-155">定义程序集清单的友好默认别名</span><span class="sxs-lookup"><span data-stu-id="02c6a-155">Defines a friendly default alias for an assembly manifest</span></span>|

## <a name="obsolete-attribute"></a><a name="Obsolete"></a> <span data-ttu-id="02c6a-156">过时特性</span><span class="sxs-lookup"><span data-stu-id="02c6a-156">Obsolete Attribute</span></span>

<span data-ttu-id="02c6a-157">`Obsolete` 特性将程序实体标记为不再推荐使用。</span><span class="sxs-lookup"><span data-stu-id="02c6a-157">The `Obsolete` attribute marks a program entity as one that is no longer recommended for use.</span></span> <span data-ttu-id="02c6a-158">每次使用标记为过时的实体后，将生成警告或错误，具体取决于该特性的配置方式。</span><span class="sxs-lookup"><span data-stu-id="02c6a-158">Each use of an entity marked obsolete will subsequently generate a warning or an error, depending on how the attribute is configured.</span></span> <span data-ttu-id="02c6a-159">例如：</span><span class="sxs-lookup"><span data-stu-id="02c6a-159">For example:</span></span>

```vb
<System.Obsolete("use class B")>
Class A
    Sub Method()
    End Sub
End Class

Class B
    <System.Obsolete("use NewMethod", True)>
    Sub OldMethod()
    End Sub

    Sub NewMethod()
    End Sub
End Class
```

<span data-ttu-id="02c6a-160">在此示例中，`Obsolete` 特性应用于类 `A` 和方法 `B.OldMethod`。</span><span class="sxs-lookup"><span data-stu-id="02c6a-160">In this example the `Obsolete` attribute is applied to class `A` and to method `B.OldMethod`.</span></span> <span data-ttu-id="02c6a-161">因为应用于 `B.OldMethod` 的特性构造函数的第二个参数设置为 `true`，所以此方法将导致编译器错误，而使用类 `A` 只会生成警告。</span><span class="sxs-lookup"><span data-stu-id="02c6a-161">Because the second argument of the attribute constructor applied to `B.OldMethod` is set to `true`, this method will cause a compiler error, whereas using class `A` will just produce a warning.</span></span> <span data-ttu-id="02c6a-162">但是，调用 `B.NewMethod` 不会生成任何警告或错误。</span><span class="sxs-lookup"><span data-stu-id="02c6a-162">Calling `B.NewMethod`, however, produces no warning or error.</span></span>

<span data-ttu-id="02c6a-163">作为特性构造函数的第一个参数提供的字符串将作为警告或错误的一部分显示。</span><span class="sxs-lookup"><span data-stu-id="02c6a-163">The string provided as the first argument to attribute constructor will be displayed as part of the warning or error.</span></span> <span data-ttu-id="02c6a-164">例如，将其与先前的定义一起使用时，以下代码会生成两个警告和一个错误：</span><span class="sxs-lookup"><span data-stu-id="02c6a-164">For example, when you use it with the previous definitions, the following code generates two warnings and one error:</span></span>

```vb
' Generates 2 warnings:
' Dim a As New A
' Generate no errors or warnings:

Dim b As New B
b.NewMethod()

' Generates an error, terminating compilation:
' b.OldMethod()
```

<span data-ttu-id="02c6a-165">将生成类 `A` 的两个警告：一个用于声明类引用，另一个用于类构造函数。</span><span class="sxs-lookup"><span data-stu-id="02c6a-165">Two warnings for class `A` are generated: one for the declaration of the class reference, and one for the class constructor.</span></span>

<span data-ttu-id="02c6a-166">`Obsolete` 特性可以在不带参数的情况下使用，但建议包括说明项目过时的原因以及改为使用哪个项目。</span><span class="sxs-lookup"><span data-stu-id="02c6a-166">The `Obsolete` attribute can be used without arguments, but including an explanation of why the item is obsolete and what to use instead is recommended.</span></span>

<span data-ttu-id="02c6a-167">`Obsolete` 特性是一次性特性，可以应用于任何允许特性的实体。</span><span class="sxs-lookup"><span data-stu-id="02c6a-167">The `Obsolete` attribute is a single-use attribute and can be applied to any entity that allows attributes.</span></span> <span data-ttu-id="02c6a-168">`Obsolete` 是 <xref:System.ObsoleteAttribute> 的别名。</span><span class="sxs-lookup"><span data-stu-id="02c6a-168">`Obsolete` is an alias for <xref:System.ObsoleteAttribute>.</span></span>

## <a name="conditional-attribute"></a><a name="Conditional"></a> <span data-ttu-id="02c6a-169">Conditional 特性</span><span class="sxs-lookup"><span data-stu-id="02c6a-169">Conditional Attribute</span></span>

<span data-ttu-id="02c6a-170">`Conditional` 特性使得方法执行依赖于预处理标识符。</span><span class="sxs-lookup"><span data-stu-id="02c6a-170">The `Conditional` attribute makes the execution of a method dependent on a preprocessing identifier.</span></span> <span data-ttu-id="02c6a-171">`Conditional` 属性是 <xref:System.Diagnostics.ConditionalAttribute> 的别名，可以应用于方法或特性类。</span><span class="sxs-lookup"><span data-stu-id="02c6a-171">The `Conditional` attribute is an alias for <xref:System.Diagnostics.ConditionalAttribute>, and can be applied to a method or an attribute class.</span></span>

<span data-ttu-id="02c6a-172">在此示例中，`Conditional` 应用于启用或禁用显示特定于程序的诊断信息的方法：</span><span class="sxs-lookup"><span data-stu-id="02c6a-172">In this example, `Conditional` is applied to a method to enable or disable the display of program-specific diagnostic information:</span></span>

```vb
#Const TRACE_ON = True
Imports System.Diagnostics

Module TestConditionalAttribute
    Public Class Trace
        <Conditional("TRACE_ON")>
        Public Shared Sub Msg(ByVal msg As String)
            Console.WriteLine(msg)
        End Sub

    End Class

    Sub Main()
        Trace.Msg("Now in Main...")
        Console.WriteLine("Done.")
    End Sub
End Module
```

<span data-ttu-id="02c6a-173">如果未定义 `TRACE_ON` 标识符，则不会显示任何跟踪输出。</span><span class="sxs-lookup"><span data-stu-id="02c6a-173">If the `TRACE_ON` identifier is not defined, no trace output will be displayed.</span></span>

<span data-ttu-id="02c6a-174">`Conditional` 特性通常与 `DEBUG` 标识符一起使用，以启用调试生成（而非发布生成）中的跟踪和日志记录功能，如下所示：</span><span class="sxs-lookup"><span data-stu-id="02c6a-174">The `Conditional` attribute is often used with the `DEBUG` identifier to enable trace and logging features for debug builds but not in release builds, like this:</span></span>

```vb
<Conditional("DEBUG")>
Shared Sub DebugMethod()

End Sub
```

<span data-ttu-id="02c6a-175">当调用标记为 conditional 的方法时，指定的预处理符号是否存在将决定包括还是省略该调用。</span><span class="sxs-lookup"><span data-stu-id="02c6a-175">When a method marked as conditional is called, the presence or absence of the specified preprocessing symbol determines whether the call is included or omitted.</span></span> <span data-ttu-id="02c6a-176">如果定义了符号，则将包括调用；否则，将忽略该调用。</span><span class="sxs-lookup"><span data-stu-id="02c6a-176">If the symbol is defined, the call is included; otherwise, the call is omitted.</span></span> <span data-ttu-id="02c6a-177">使用 `Conditional` 是将方法封闭在 `#if…#endif` 块内的更简洁且较不容易出错的替代方法，如下所示：</span><span class="sxs-lookup"><span data-stu-id="02c6a-177">Using `Conditional` is a cleaner, more elegant, and less error-prone alternative to enclosing methods inside `#if…#endif` blocks, like this:</span></span>

```vb
#If DEBUG Then
    Sub ConditionalMethod()
    End Sub
#End If
```

<span data-ttu-id="02c6a-178">条件方法必须是类或结构声明中的方法，而且必须没有返回值。</span><span class="sxs-lookup"><span data-stu-id="02c6a-178">A conditional method must be a method in a class or struct declaration and must not have a return value.</span></span>

### <a name="using-multiple-identifiers"></a><span data-ttu-id="02c6a-179">使用多个标识符</span><span class="sxs-lookup"><span data-stu-id="02c6a-179">Using Multiple Identifiers</span></span>

<span data-ttu-id="02c6a-180">如果某个方法具有多个 `Conditional` 特性，则如果至少定义了其中一个条件符号（换言之，通过使用 OR 运算符将这些符号逻辑链接在一起），则包含对该方法的调用。</span><span class="sxs-lookup"><span data-stu-id="02c6a-180">If a method has multiple `Conditional` attributes, a call to the method is included if at least one of the conditional symbols is defined (in other words, the symbols are logically linked together by using the OR operator).</span></span> <span data-ttu-id="02c6a-181">在此示例中，存在 `A` 或 `B` 将导致方法调用：</span><span class="sxs-lookup"><span data-stu-id="02c6a-181">In this example, the presence of either `A` or `B` will result in a method call:</span></span>

```vb
<Conditional("A"), Conditional("B")>
Shared Sub DoIfAorB()

End Sub
```

<span data-ttu-id="02c6a-182">若要使用 AND 运算符实现逻辑链接符号的效果，可以定义串行条件方法。</span><span class="sxs-lookup"><span data-stu-id="02c6a-182">To achieve the effect of logically linking symbols by using the AND operator, you can define serial conditional methods.</span></span> <span data-ttu-id="02c6a-183">例如，仅当同时定义了 `A` 和 `B` 时才会执行下面的第二个方法：</span><span class="sxs-lookup"><span data-stu-id="02c6a-183">For example, the second method below will execute only if both `A` and `B` are defined:</span></span>

```vb
<Conditional("A")>
Shared Sub DoIfA()
    DoIfAandB()
End Sub

<Conditional("B")>
Shared Sub DoIfAandB()
    ' Code to execute when both A and B are defined...
End Sub
```

### <a name="using-conditional-with-attribute-classes"></a><span data-ttu-id="02c6a-184">将 Conditional 用于特性类</span><span class="sxs-lookup"><span data-stu-id="02c6a-184">Using Conditional with Attribute Classes</span></span>

<span data-ttu-id="02c6a-185">`Conditional` 特性还可应用于特性类定义。</span><span class="sxs-lookup"><span data-stu-id="02c6a-185">The `Conditional` attribute can also be applied to an attribute class definition.</span></span> <span data-ttu-id="02c6a-186">在本示例中，如果定义了 DEBUG，则自定义属性 `Documentation` 将仅向元数据添加信息。</span><span class="sxs-lookup"><span data-stu-id="02c6a-186">In this example, the custom attribute `Documentation` will only add information to the metadata if DEBUG is defined.</span></span>

```vb
<Conditional("DEBUG")>
Public Class Documentation
    Inherits System.Attribute
    Private text As String
    Sub New(ByVal doc_text As String)
        text = doc_text
    End Sub
End Class

Class SampleClass
    ' This attribute will only be included if DEBUG is defined.
    <Documentation("This method displays an integer.")>
    Shared Sub DoWork(ByVal i As Integer)
        System.Console.WriteLine(i)
    End Sub
End Class
```

## <a name="caller-info-attributes"></a><a name="CallerInfo"></a> <span data-ttu-id="02c6a-187">调用方信息特性</span><span class="sxs-lookup"><span data-stu-id="02c6a-187">Caller Info Attributes</span></span>

<span data-ttu-id="02c6a-188">通过使用调用方信息特性，可获取有关方法的调用方的信息。</span><span class="sxs-lookup"><span data-stu-id="02c6a-188">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="02c6a-189">可以获取源代码的文件路径、源代码中的行号和调用方的成员名称。</span><span class="sxs-lookup"><span data-stu-id="02c6a-189">You can obtain the file path of the source code, the line number in the source code, and the member name of the caller.</span></span>

<span data-ttu-id="02c6a-190">若要获取成员调用方信息，可以使用应用于可选参数的特性。</span><span class="sxs-lookup"><span data-stu-id="02c6a-190">To obtain member caller information, you use attributes that are applied to optional parameters.</span></span> <span data-ttu-id="02c6a-191">每个可选参数指定一个默认值。</span><span class="sxs-lookup"><span data-stu-id="02c6a-191">Each optional parameter specifies a default value.</span></span> <span data-ttu-id="02c6a-192">下表列出在 <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> 命名空间中定义的调用方信息特性：</span><span class="sxs-lookup"><span data-stu-id="02c6a-192">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>

|<span data-ttu-id="02c6a-193">特性</span><span class="sxs-lookup"><span data-stu-id="02c6a-193">Attribute</span></span>|<span data-ttu-id="02c6a-194">说明</span><span class="sxs-lookup"><span data-stu-id="02c6a-194">Description</span></span>|<span data-ttu-id="02c6a-195">类型</span><span class="sxs-lookup"><span data-stu-id="02c6a-195">Type</span></span>|
|---|---|---|
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="02c6a-196">包含调用方的源文件的完整路径。</span><span class="sxs-lookup"><span data-stu-id="02c6a-196">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="02c6a-197">这是编译时的路径。</span><span class="sxs-lookup"><span data-stu-id="02c6a-197">This is the path at compile time.</span></span>|`String`|
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="02c6a-198">源文件中调用方法的行号。</span><span class="sxs-lookup"><span data-stu-id="02c6a-198">Line number in the source file from which the method is called.</span></span>|`Integer`|
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="02c6a-199">调用方的方法名称或属性名称。</span><span class="sxs-lookup"><span data-stu-id="02c6a-199">Method name or property name of the caller.</span></span> <span data-ttu-id="02c6a-200">有关详细信息，请参阅 [ (Visual Basic) 的调用方信息 ](../caller-information.md)。</span><span class="sxs-lookup"><span data-stu-id="02c6a-200">For more information, see [Caller Information (Visual Basic)](../caller-information.md).</span></span>|`String`|

<span data-ttu-id="02c6a-201">有关调用方信息属性的详细信息，请参阅 [调用方信息 (Visual Basic) ](../caller-information.md)。</span><span class="sxs-lookup"><span data-stu-id="02c6a-201">For more information about the Caller Info attributes, see [Caller Information (Visual Basic)](../caller-information.md).</span></span>

## <a name="visual-basic-attributes"></a><a name="VB"></a> <span data-ttu-id="02c6a-202">Visual Basic 特性</span><span class="sxs-lookup"><span data-stu-id="02c6a-202">Visual Basic Attributes</span></span>

<span data-ttu-id="02c6a-203">下表列出了特定于 Visual Basic 的特性。</span><span class="sxs-lookup"><span data-stu-id="02c6a-203">The following table lists the attributes that are specific to Visual Basic.</span></span>

|<span data-ttu-id="02c6a-204">特性</span><span class="sxs-lookup"><span data-stu-id="02c6a-204">Attribute</span></span>|<span data-ttu-id="02c6a-205">目的</span><span class="sxs-lookup"><span data-stu-id="02c6a-205">Purpose</span></span>|
|---------------|-------------|
|<xref:Microsoft.VisualBasic.ComClassAttribute>|<span data-ttu-id="02c6a-206">向编译器指示应将类公开为 COM 对象。</span><span class="sxs-lookup"><span data-stu-id="02c6a-206">Indicates to the compiler that the class should be exposed as a COM object.</span></span>|
|<xref:Microsoft.VisualBasic.HideModuleNameAttribute>|<span data-ttu-id="02c6a-207">允许只使用模块所需的限定来访问模块成员。</span><span class="sxs-lookup"><span data-stu-id="02c6a-207">Allows module members to be accessed using only the qualification needed for the module.</span></span>|
|<xref:Microsoft.VisualBasic.VBFixedStringAttribute>|<span data-ttu-id="02c6a-208">指定结构中用于文件输入和输出函数的固定长度字符串的大小。</span><span class="sxs-lookup"><span data-stu-id="02c6a-208">Specifies the size of a fixed-length string in a structure for use with file input and output functions.</span></span>|
|<xref:Microsoft.VisualBasic.VBFixedArrayAttribute>|<span data-ttu-id="02c6a-209">指定结构中用于文件输入和输出函数的固定数组的大小。</span><span class="sxs-lookup"><span data-stu-id="02c6a-209">Specifies the size of a fixed array in a structure for use with file input and output functions.</span></span>|

### <a name="comclassattribute"></a><span data-ttu-id="02c6a-210">COMClassAttribute</span><span class="sxs-lookup"><span data-stu-id="02c6a-210">COMClassAttribute</span></span>

<span data-ttu-id="02c6a-211">使用 `COMClassAttribute` 可以简化从 Visual Basic 创建 COM 组件的过程。</span><span class="sxs-lookup"><span data-stu-id="02c6a-211">Use `COMClassAttribute` to simplify the process of creating COM components from Visual Basic.</span></span> <span data-ttu-id="02c6a-212">COM 对象与 .NET Framework 程序集有很大的不同，因此 `COMClassAttribute` ，您需要执行一些步骤才能从 Visual Basic 生成 com 对象。</span><span class="sxs-lookup"><span data-stu-id="02c6a-212">COM objects are considerably different from .NET Framework assemblies, and without `COMClassAttribute`, you need to follow a number of steps to generate a COM object from Visual Basic.</span></span> <span data-ttu-id="02c6a-213">对于标记为的类 `COMClassAttribute` ，编译器会自动执行这些步骤中的许多步骤。</span><span class="sxs-lookup"><span data-stu-id="02c6a-213">For classes marked with `COMClassAttribute`, the compiler performs many of these steps automatically.</span></span>

### <a name="hidemodulenameattribute"></a><span data-ttu-id="02c6a-214">HideModuleNameAttribute</span><span class="sxs-lookup"><span data-stu-id="02c6a-214">HideModuleNameAttribute</span></span>

<span data-ttu-id="02c6a-215">使用 `HideModuleNameAttribute` 可以仅使用模块所需的限定来访问模块成员。</span><span class="sxs-lookup"><span data-stu-id="02c6a-215">Use `HideModuleNameAttribute` to allow module members to be accessed by using only the qualification needed for the module.</span></span>

### <a name="vbfixedstringattribute"></a><span data-ttu-id="02c6a-216">VBFixedStringAttribute</span><span class="sxs-lookup"><span data-stu-id="02c6a-216">VBFixedStringAttribute</span></span>

<span data-ttu-id="02c6a-217">使用 `VBFixedStringAttribute` 强制 Visual Basic 创建固定长度的字符串。</span><span class="sxs-lookup"><span data-stu-id="02c6a-217">Use `VBFixedStringAttribute` to force Visual Basic to create a fixed-length string.</span></span> <span data-ttu-id="02c6a-218">字符串在默认情况下为可变长度，在将字符串存储到文件时，此属性很有用。</span><span class="sxs-lookup"><span data-stu-id="02c6a-218">Strings are of variable length by default, and this attribute is useful when storing strings to files.</span></span> <span data-ttu-id="02c6a-219">以下代码对此做了演示：</span><span class="sxs-lookup"><span data-stu-id="02c6a-219">The following code demonstrates this:</span></span>

```vb
Structure Worker
    ' The runtime uses VBFixedString to determine
    ' if the field should be written out as a fixed size.
    <VBFixedString(10)> Public LastName As String
    <VBFixedString(7)> Public Title As String
    <VBFixedString(2)> Public Rank As String
End Structure
```

### <a name="vbfixedarrayattribute"></a><span data-ttu-id="02c6a-220">VBFixedArrayAttribute</span><span class="sxs-lookup"><span data-stu-id="02c6a-220">VBFixedArrayAttribute</span></span>

<span data-ttu-id="02c6a-221">用于 `VBFixedArrayAttribute` 声明大小固定的数组。</span><span class="sxs-lookup"><span data-stu-id="02c6a-221">Use `VBFixedArrayAttribute` to declare arrays that are fixed in size.</span></span> <span data-ttu-id="02c6a-222">与 Visual Basic 字符串一样，数组在默认情况下为可变长度。</span><span class="sxs-lookup"><span data-stu-id="02c6a-222">Like Visual Basic strings, arrays are of variable length by default.</span></span> <span data-ttu-id="02c6a-223">将数据序列化或写入到文件时，此属性很有用。</span><span class="sxs-lookup"><span data-stu-id="02c6a-223">This attribute is useful when serializing or writing data to files.</span></span>

## <a name="see-also"></a><span data-ttu-id="02c6a-224">请参阅</span><span class="sxs-lookup"><span data-stu-id="02c6a-224">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="02c6a-225">Visual Basic 编程指南</span><span class="sxs-lookup"><span data-stu-id="02c6a-225">Visual Basic Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="02c6a-226">特性</span><span class="sxs-lookup"><span data-stu-id="02c6a-226">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="02c6a-227">反射 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="02c6a-227">Reflection (Visual Basic)</span></span>](../reflection.md)
- [<span data-ttu-id="02c6a-228">使用反射访问特性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="02c6a-228">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](accessing-attributes-by-using-reflection.md)
