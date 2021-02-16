---
description: 详细了解：按类别列出的 Visual Basic 编译器选项
title: 按类别列出的编译器选项
ms.date: 04/12/2018
helpviewer_keywords:
- Visual Basic compiler, options
ms.assetid: fbe36f7a-7cfa-4f77-a8d4-2be5958568e3
ms.openlocfilehash: f0535e2aa94cda96610acb0edb24f6d46cc4afa0
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100474169"
---
# <a name="visual-basic-compiler-options-listed-by-category"></a><span data-ttu-id="6f526-103">按类别列出的 Visual Basic 编译器选项</span><span class="sxs-lookup"><span data-stu-id="6f526-103">Visual Basic compiler options listed by category</span></span>

<span data-ttu-id="6f526-104">Visual Basic 命令行编译器用作一种替代方法，用于在 Visual Studio 集成开发环境 (IDE) 中编译程序。</span><span class="sxs-lookup"><span data-stu-id="6f526-104">The Visual Basic command-line compiler is provided as an alternative to compiling programs from within the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="6f526-105">以下是按功能分类排序的 Visual Basic 命令行编译器选项的列表。</span><span class="sxs-lookup"><span data-stu-id="6f526-105">The following is a list of the Visual Basic command-line compiler options sorted by functional category.</span></span>  

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]
  
## <a name="compiler-output"></a><span data-ttu-id="6f526-106">编译器输出</span><span class="sxs-lookup"><span data-stu-id="6f526-106">Compiler output</span></span>  
  
|<span data-ttu-id="6f526-107">选项</span><span class="sxs-lookup"><span data-stu-id="6f526-107">Option</span></span>|<span data-ttu-id="6f526-108">目标</span><span class="sxs-lookup"><span data-stu-id="6f526-108">Purpose</span></span>|  
|---|---|  
|[<span data-ttu-id="6f526-109">-nologo</span><span class="sxs-lookup"><span data-stu-id="6f526-109">-nologo</span></span>](nologo.md)|<span data-ttu-id="6f526-110">禁止显示编译器横幅信息。</span><span class="sxs-lookup"><span data-stu-id="6f526-110">Suppresses compiler banner information.</span></span>|  
|[<span data-ttu-id="6f526-111">-utf8output</span><span class="sxs-lookup"><span data-stu-id="6f526-111">-utf8output</span></span>](utf8output.md)|<span data-ttu-id="6f526-112">显示使用 UTF-8 编码的编译器输出。</span><span class="sxs-lookup"><span data-stu-id="6f526-112">Displays compiler output using UTF-8 encoding.</span></span>|  
|[<span data-ttu-id="6f526-113">-verbose</span><span class="sxs-lookup"><span data-stu-id="6f526-113">-verbose</span></span>](verbose.md)|<span data-ttu-id="6f526-114">在编译期间输出其他信息。</span><span class="sxs-lookup"><span data-stu-id="6f526-114">Outputs extra information during compilation.</span></span>|  
|`-modulename:<string>`|<span data-ttu-id="6f526-115">指定源模块的名称</span><span class="sxs-lookup"><span data-stu-id="6f526-115">Specify the name of the source module</span></span>|  
|[<span data-ttu-id="6f526-116">/preferreduilang</span><span class="sxs-lookup"><span data-stu-id="6f526-116">-preferreduilang</span></span>](../../../csharp/language-reference/compiler-options/preferreduilang-compiler-option.md)|<span data-ttu-id="6f526-117">指定编译器输出的语言。</span><span class="sxs-lookup"><span data-stu-id="6f526-117">Specify a language for compiler output.</span></span>|
  
## <a name="optimization"></a><span data-ttu-id="6f526-118">优化</span><span class="sxs-lookup"><span data-stu-id="6f526-118">Optimization</span></span>  
  
|<span data-ttu-id="6f526-119">选项</span><span class="sxs-lookup"><span data-stu-id="6f526-119">Option</span></span>|<span data-ttu-id="6f526-120">目标</span><span class="sxs-lookup"><span data-stu-id="6f526-120">Purpose</span></span>|  
|---|---|  
|[<span data-ttu-id="6f526-121">-filealign</span><span class="sxs-lookup"><span data-stu-id="6f526-121">-filealign</span></span>](filealign.md)|<span data-ttu-id="6f526-122">指定输出文件各节的对齐位置。</span><span class="sxs-lookup"><span data-stu-id="6f526-122">Specifies where to align the sections of the output file.</span></span>|  
|[<span data-ttu-id="6f526-123">-optimize</span><span class="sxs-lookup"><span data-stu-id="6f526-123">-optimize</span></span>](optimize.md)|<span data-ttu-id="6f526-124">启用/禁用优化。</span><span class="sxs-lookup"><span data-stu-id="6f526-124">Enables/disables optimizations.</span></span>|  
  
## <a name="output-files"></a><span data-ttu-id="6f526-125">输出文件</span><span class="sxs-lookup"><span data-stu-id="6f526-125">Output files</span></span>  
  
|<span data-ttu-id="6f526-126">选项</span><span class="sxs-lookup"><span data-stu-id="6f526-126">Option</span></span>|<span data-ttu-id="6f526-127">目标</span><span class="sxs-lookup"><span data-stu-id="6f526-127">Purpose</span></span>|  
|---|---|  
|[<span data-ttu-id="6f526-128">-doc</span><span class="sxs-lookup"><span data-stu-id="6f526-128">-doc</span></span>](doc.md)|<span data-ttu-id="6f526-129">处理 XML 文件的文档注释。</span><span class="sxs-lookup"><span data-stu-id="6f526-129">Process documentation comments to an XML file.</span></span>|  
|[<span data-ttu-id="6f526-130">-deterministic</span><span class="sxs-lookup"><span data-stu-id="6f526-130">-deterministic</span></span>](deterministic.md)|<span data-ttu-id="6f526-131">如果输入相同，则会导致编译器输出的程序集其二进制内容在整个编译中相同。</span><span class="sxs-lookup"><span data-stu-id="6f526-131">Causes the compiler to output an assembly whose binary content is identical across compilations if inputs are identical.</span></span>|
|[<span data-ttu-id="6f526-132">-netcf</span><span class="sxs-lookup"><span data-stu-id="6f526-132">-netcf</span></span>](netcf.md)|<span data-ttu-id="6f526-133">将编译器设置为以 .NET Compact Framework 为目标。</span><span class="sxs-lookup"><span data-stu-id="6f526-133">Sets the compiler to target the .NET Compact Framework.</span></span>|  
|[<span data-ttu-id="6f526-134">-out</span><span class="sxs-lookup"><span data-stu-id="6f526-134">-out</span></span>](out.md)|<span data-ttu-id="6f526-135">指定输出目录。</span><span class="sxs-lookup"><span data-stu-id="6f526-135">Specifies an output file.</span></span>|  
|[<span data-ttu-id="6f526-136">/refonly</span><span class="sxs-lookup"><span data-stu-id="6f526-136">-refonly</span></span>](refonly-compiler-option.md)|<span data-ttu-id="6f526-137">仅输出引用程序集。</span><span class="sxs-lookup"><span data-stu-id="6f526-137">Outputs only a reference assembly.</span></span>|
|[<span data-ttu-id="6f526-138">/refout</span><span class="sxs-lookup"><span data-stu-id="6f526-138">-refout</span></span>](refout-compiler-option.md)|<span data-ttu-id="6f526-139">指定引用程序集的输出路径。</span><span class="sxs-lookup"><span data-stu-id="6f526-139">Specifies the output path of a reference assembly.</span></span>|
|[<span data-ttu-id="6f526-140">-target</span><span class="sxs-lookup"><span data-stu-id="6f526-140">-target</span></span>](target.md)|<span data-ttu-id="6f526-141">指定输出的格式。</span><span class="sxs-lookup"><span data-stu-id="6f526-141">Specifies the format of the output.</span></span>|  
  
## <a name="net-assemblies"></a><span data-ttu-id="6f526-142">.NET 程序集</span><span class="sxs-lookup"><span data-stu-id="6f526-142">.NET assemblies</span></span>  
  
|<span data-ttu-id="6f526-143">选项</span><span class="sxs-lookup"><span data-stu-id="6f526-143">Option</span></span>|<span data-ttu-id="6f526-144">目标</span><span class="sxs-lookup"><span data-stu-id="6f526-144">Purpose</span></span>|  
|---|---|  
|[<span data-ttu-id="6f526-145">-addmodule</span><span class="sxs-lookup"><span data-stu-id="6f526-145">-addmodule</span></span>](addmodule.md)|<span data-ttu-id="6f526-146">使编译器让指定文件中的所有类型信息可供当前正在编译的项目使用。</span><span class="sxs-lookup"><span data-stu-id="6f526-146">Causes the compiler to make all type information from the specified file(s) available to the project you are currently compiling.</span></span>|  
|[<span data-ttu-id="6f526-147">-delaysign</span><span class="sxs-lookup"><span data-stu-id="6f526-147">-delaysign</span></span>](delaysign.md)|<span data-ttu-id="6f526-148">指定程序集是完全签名的还是部分签名的。</span><span class="sxs-lookup"><span data-stu-id="6f526-148">Specifies whether the assembly will be fully or partially signed.</span></span>|  
|[<span data-ttu-id="6f526-149">-imports</span><span class="sxs-lookup"><span data-stu-id="6f526-149">-imports</span></span>](imports.md)|<span data-ttu-id="6f526-150">从指定的程序集导入命名空间。</span><span class="sxs-lookup"><span data-stu-id="6f526-150">Imports a namespace from a specified assembly.</span></span>|  
|[<span data-ttu-id="6f526-151">-keycontainer</span><span class="sxs-lookup"><span data-stu-id="6f526-151">-keycontainer</span></span>](keycontainer.md)|<span data-ttu-id="6f526-152">指定密钥对的密钥容器名称从而为程序集赋予强名称。</span><span class="sxs-lookup"><span data-stu-id="6f526-152">Specifies a key container name for a key pair to give an assembly a strong name.</span></span>|  
|[<span data-ttu-id="6f526-153">-keyfile</span><span class="sxs-lookup"><span data-stu-id="6f526-153">-keyfile</span></span>](keyfile.md)|<span data-ttu-id="6f526-154">指定包含密钥或密钥对的文件从而为程序集赋予强名称。</span><span class="sxs-lookup"><span data-stu-id="6f526-154">Specifies a file containing a key or key pair to give an assembly a strong name.</span></span>|  
|[<span data-ttu-id="6f526-155">-libpath</span><span class="sxs-lookup"><span data-stu-id="6f526-155">-libpath</span></span>](libpath.md)|<span data-ttu-id="6f526-156">指定通过 [-reference](reference.md) 选项引用的程序集的位置。</span><span class="sxs-lookup"><span data-stu-id="6f526-156">Specifies the location of assemblies referenced by the [-reference](reference.md) option.</span></span>|  
|[<span data-ttu-id="6f526-157">-reference</span><span class="sxs-lookup"><span data-stu-id="6f526-157">-reference</span></span>](reference.md)|<span data-ttu-id="6f526-158">从程序集导入元数据。</span><span class="sxs-lookup"><span data-stu-id="6f526-158">Imports metadata from an assembly.</span></span>|  
|[<span data-ttu-id="6f526-159">-moduleassemblyname</span><span class="sxs-lookup"><span data-stu-id="6f526-159">-moduleassemblyname</span></span>](moduleassemblyname.md)|<span data-ttu-id="6f526-160">指定模块所属程序集的名称。</span><span class="sxs-lookup"><span data-stu-id="6f526-160">Specifies the name of the assembly that a module will be a part of.</span></span>|  
|`-analyzer`|<span data-ttu-id="6f526-161">从此程序集（缩写形式：-a）运行分析器</span><span class="sxs-lookup"><span data-stu-id="6f526-161">Run the analyzers from this assembly (Short form: -a)</span></span>|  
|`-additionalfile`|<span data-ttu-id="6f526-162">命名其他文件，这些文件不会直接影响代码生成，但可能由分析器用于生成错误或警告。</span><span class="sxs-lookup"><span data-stu-id="6f526-162">Names additional files that don't directly affect code generation but may be used by analyzers for producing errors or warnings.</span></span>|  
  
## <a name="debuggingerror-checking"></a><span data-ttu-id="6f526-163">调试/错误检查</span><span class="sxs-lookup"><span data-stu-id="6f526-163">Debugging/error checking</span></span>  
  
|<span data-ttu-id="6f526-164">选项</span><span class="sxs-lookup"><span data-stu-id="6f526-164">Option</span></span>|<span data-ttu-id="6f526-165">目标</span><span class="sxs-lookup"><span data-stu-id="6f526-165">Purpose</span></span>|  
|---|---|  
|[<span data-ttu-id="6f526-166">-bugreport</span><span class="sxs-lookup"><span data-stu-id="6f526-166">-bugreport</span></span>](bugreport.md)|<span data-ttu-id="6f526-167">创建一个文件，其中包含可以轻松报告 bug 的信息。</span><span class="sxs-lookup"><span data-stu-id="6f526-167">Creates a file that contains information that makes it easy to report a bug.</span></span>|  
|[<span data-ttu-id="6f526-168">-debug</span><span class="sxs-lookup"><span data-stu-id="6f526-168">-debug</span></span>](debug.md)|<span data-ttu-id="6f526-169">生成调试信息。</span><span class="sxs-lookup"><span data-stu-id="6f526-169">Produces debugging information.</span></span>|  
|[<span data-ttu-id="6f526-170">-nowarn</span><span class="sxs-lookup"><span data-stu-id="6f526-170">-nowarn</span></span>](nowarn.md)|<span data-ttu-id="6f526-171">禁止编译器生成警告的能力。</span><span class="sxs-lookup"><span data-stu-id="6f526-171">Suppresses the compiler's ability to generate warnings.</span></span>|  
|[<span data-ttu-id="6f526-172">-quiet</span><span class="sxs-lookup"><span data-stu-id="6f526-172">-quiet</span></span>](quiet.md)|<span data-ttu-id="6f526-173">阻止编译器显示与语法相关的错误和警告的代码。</span><span class="sxs-lookup"><span data-stu-id="6f526-173">Prevents the compiler from displaying code for syntax-related errors and warnings.</span></span>|  
|[<span data-ttu-id="6f526-174">-removeintchecks</span><span class="sxs-lookup"><span data-stu-id="6f526-174">-removeintchecks</span></span>](removeintchecks.md)|<span data-ttu-id="6f526-175">禁用整数溢出检查。</span><span class="sxs-lookup"><span data-stu-id="6f526-175">Disables integer overflow checking.</span></span>|  
|[<span data-ttu-id="6f526-176">-warnaserror</span><span class="sxs-lookup"><span data-stu-id="6f526-176">-warnaserror</span></span>](warnaserror.md)|<span data-ttu-id="6f526-177">将警告提升为错误。</span><span class="sxs-lookup"><span data-stu-id="6f526-177">Promotes warnings to errors.</span></span>|  
|`-ruleset:<file>`|<span data-ttu-id="6f526-178">指定可禁用特定诊断的规则集文件。</span><span class="sxs-lookup"><span data-stu-id="6f526-178">Specify a ruleset file that disables specific diagnostics.</span></span>|  
  
## <a name="help"></a><span data-ttu-id="6f526-179">帮助</span><span class="sxs-lookup"><span data-stu-id="6f526-179">Help</span></span>  
  
|<span data-ttu-id="6f526-180">选项</span><span class="sxs-lookup"><span data-stu-id="6f526-180">Option</span></span>|<span data-ttu-id="6f526-181">目标</span><span class="sxs-lookup"><span data-stu-id="6f526-181">Purpose</span></span>|  
|---|---|  
|[<span data-ttu-id="6f526-182">-?</span><span class="sxs-lookup"><span data-stu-id="6f526-182">-?</span></span>](help.md)|<span data-ttu-id="6f526-183">显示编译器选项。</span><span class="sxs-lookup"><span data-stu-id="6f526-183">Displays the compiler options.</span></span> <span data-ttu-id="6f526-184">此命令等同于指定 `-help` 选项。</span><span class="sxs-lookup"><span data-stu-id="6f526-184">This command is the same as specifying the `-help` option.</span></span> <span data-ttu-id="6f526-185">未进行编译。</span><span class="sxs-lookup"><span data-stu-id="6f526-185">No compilation occurs.</span></span>|  
|[<span data-ttu-id="6f526-186">-help</span><span class="sxs-lookup"><span data-stu-id="6f526-186">-help</span></span>](help.md)|<span data-ttu-id="6f526-187">显示编译器选项。</span><span class="sxs-lookup"><span data-stu-id="6f526-187">Displays the compiler options.</span></span> <span data-ttu-id="6f526-188">此命令等同于指定 `-?` 选项。</span><span class="sxs-lookup"><span data-stu-id="6f526-188">This command is the same as specifying the `-?` option.</span></span> <span data-ttu-id="6f526-189">未进行编译。</span><span class="sxs-lookup"><span data-stu-id="6f526-189">No compilation occurs.</span></span>|  
  
## <a name="language"></a><span data-ttu-id="6f526-190">语言</span><span class="sxs-lookup"><span data-stu-id="6f526-190">Language</span></span>  
  
|<span data-ttu-id="6f526-191">选项</span><span class="sxs-lookup"><span data-stu-id="6f526-191">Option</span></span>|<span data-ttu-id="6f526-192">目标</span><span class="sxs-lookup"><span data-stu-id="6f526-192">Purpose</span></span>|  
|---|---|  
|[<span data-ttu-id="6f526-193">-langversion</span><span class="sxs-lookup"><span data-stu-id="6f526-193">-langversion</span></span>](langversion.md)|<span data-ttu-id="6f526-194">指定语言版本：9&#124;9.0&#124;10&#124;10.0&#124;11&#124;11.0。</span><span class="sxs-lookup"><span data-stu-id="6f526-194">Specify language version: 9&#124;9.0&#124;10&#124;10.0&#124;11&#124;11.0.</span></span>|  
|[<span data-ttu-id="6f526-195">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="6f526-195">-optionexplicit</span></span>](optionexplicit.md)|<span data-ttu-id="6f526-196">强制执行显式声明变量。</span><span class="sxs-lookup"><span data-stu-id="6f526-196">Enforces explicit declaration of variables.</span></span>|  
|[<span data-ttu-id="6f526-197">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="6f526-197">-optionstrict</span></span>](optionstrict.md)|<span data-ttu-id="6f526-198">执行严格的类语义。</span><span class="sxs-lookup"><span data-stu-id="6f526-198">Enforces strict type semantics.</span></span>|  
|[<span data-ttu-id="6f526-199">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="6f526-199">-optioncompare</span></span>](optioncompare.md)|<span data-ttu-id="6f526-200">指定字符串比较是否应为二进制，或是否应使用特定于区域设置的文本语义。</span><span class="sxs-lookup"><span data-stu-id="6f526-200">Specifies whether string comparisons should be binary or use locale-specific text semantics.</span></span>|  
|[<span data-ttu-id="6f526-201">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="6f526-201">-optioninfer</span></span>](optioninfer.md)|<span data-ttu-id="6f526-202">允许在变量声明中使用局部类型推理。</span><span class="sxs-lookup"><span data-stu-id="6f526-202">Enables the use of local type inference in variable declarations.</span></span>|  
  
## <a name="preprocessor"></a><span data-ttu-id="6f526-203">预处理器</span><span class="sxs-lookup"><span data-stu-id="6f526-203">Preprocessor</span></span>  
  
|<span data-ttu-id="6f526-204">选项</span><span class="sxs-lookup"><span data-stu-id="6f526-204">Option</span></span>|<span data-ttu-id="6f526-205">目标</span><span class="sxs-lookup"><span data-stu-id="6f526-205">Purpose</span></span>|  
|---|---|  
|[<span data-ttu-id="6f526-206">-define</span><span class="sxs-lookup"><span data-stu-id="6f526-206">-define</span></span>](define.md)|<span data-ttu-id="6f526-207">定义条件编译的符号。</span><span class="sxs-lookup"><span data-stu-id="6f526-207">Defines symbols for conditional compilation.</span></span>|  
  
## <a name="resources"></a><span data-ttu-id="6f526-208">资源</span><span class="sxs-lookup"><span data-stu-id="6f526-208">Resources</span></span>  
  
|<span data-ttu-id="6f526-209">选项</span><span class="sxs-lookup"><span data-stu-id="6f526-209">Option</span></span>|<span data-ttu-id="6f526-210">目标</span><span class="sxs-lookup"><span data-stu-id="6f526-210">Purpose</span></span>|  
|---|---|  
|[<span data-ttu-id="6f526-211">-linkresource</span><span class="sxs-lookup"><span data-stu-id="6f526-211">-linkresource</span></span>](linkresource.md)|<span data-ttu-id="6f526-212">创建指向托管资源的链接。</span><span class="sxs-lookup"><span data-stu-id="6f526-212">Creates a link to a managed resource.</span></span>|  
|[<span data-ttu-id="6f526-213">-resource</span><span class="sxs-lookup"><span data-stu-id="6f526-213">-resource</span></span>](resource.md)|<span data-ttu-id="6f526-214">将托管资源嵌入程序集。</span><span class="sxs-lookup"><span data-stu-id="6f526-214">Embeds a managed resource in an assembly.</span></span>|  
|[<span data-ttu-id="6f526-215">-win32icon</span><span class="sxs-lookup"><span data-stu-id="6f526-215">-win32icon</span></span>](win32icon.md)|<span data-ttu-id="6f526-216">将 .ico 文件插入到输出文件。</span><span class="sxs-lookup"><span data-stu-id="6f526-216">Inserts an .ico file into the output file.</span></span>|  
|[<span data-ttu-id="6f526-217">-win32resource</span><span class="sxs-lookup"><span data-stu-id="6f526-217">-win32resource</span></span>](win32resource.md)|<span data-ttu-id="6f526-218">将 Win32 资源插入到输出文件。</span><span class="sxs-lookup"><span data-stu-id="6f526-218">Inserts a Win32 resource into the output file.</span></span>|  
  
## <a name="miscellaneous"></a><span data-ttu-id="6f526-219">杂项</span><span class="sxs-lookup"><span data-stu-id="6f526-219">Miscellaneous</span></span>  
  
|<span data-ttu-id="6f526-220">选项</span><span class="sxs-lookup"><span data-stu-id="6f526-220">Option</span></span>|<span data-ttu-id="6f526-221">目标</span><span class="sxs-lookup"><span data-stu-id="6f526-221">Purpose</span></span>|  
|---|---|  
|[<span data-ttu-id="6f526-222">@（指定响应文件）</span><span class="sxs-lookup"><span data-stu-id="6f526-222">@ (Specify Response File)</span></span>](specify-response-file.md)|<span data-ttu-id="6f526-223">指定响应文件。</span><span class="sxs-lookup"><span data-stu-id="6f526-223">Specifies a response file.</span></span>|  
|[<span data-ttu-id="6f526-224">-baseaddress</span><span class="sxs-lookup"><span data-stu-id="6f526-224">-baseaddress</span></span>](baseaddress.md)|<span data-ttu-id="6f526-225">指定的 DLL 的基址。</span><span class="sxs-lookup"><span data-stu-id="6f526-225">Specifies the base address of a DLL.</span></span>|  
|[<span data-ttu-id="6f526-226">-codepage</span><span class="sxs-lookup"><span data-stu-id="6f526-226">-codepage</span></span>](codepage.md)|<span data-ttu-id="6f526-227">指定要用于编译中所有源代码文件的代码页。</span><span class="sxs-lookup"><span data-stu-id="6f526-227">Specifies the code page to use for all source code files in the compilation.</span></span>|  
|[<span data-ttu-id="6f526-228">-errorreport</span><span class="sxs-lookup"><span data-stu-id="6f526-228">-errorreport</span></span>](errorreport.md)|<span data-ttu-id="6f526-229">指定 Visual Basic 编译器应报告内部编译器错误的方式。</span><span class="sxs-lookup"><span data-stu-id="6f526-229">Specifies how the Visual Basic compiler should report internal compiler errors.</span></span>|  
|[<span data-ttu-id="6f526-230">-highentropyva</span><span class="sxs-lookup"><span data-stu-id="6f526-230">-highentropyva</span></span>](highentropyva.md)|<span data-ttu-id="6f526-231">向 Windows 内核提供下列信息：特定的可执行文件是否支持高熵地址空间布局随机化 (ASLR)。</span><span class="sxs-lookup"><span data-stu-id="6f526-231">Tells the Windows kernel whether a particular executable supports high entropy Address Space Layout Randomization (ASLR).</span></span>|  
|[<span data-ttu-id="6f526-232">-main</span><span class="sxs-lookup"><span data-stu-id="6f526-232">-main</span></span>](main.md)|<span data-ttu-id="6f526-233">指定包含启动时要使用的 `Sub Main` 过程的类。</span><span class="sxs-lookup"><span data-stu-id="6f526-233">Specifies the class that contains the `Sub Main` procedure to use at startup.</span></span>|  
|[<span data-ttu-id="6f526-234">-noconfig</span><span class="sxs-lookup"><span data-stu-id="6f526-234">-noconfig</span></span>](noconfig.md)|<span data-ttu-id="6f526-235">不要使用 Vbc.rsp 进行编译</span><span class="sxs-lookup"><span data-stu-id="6f526-235">Do not compile with Vbc.rsp</span></span>|  
|[<span data-ttu-id="6f526-236">-nostdlib</span><span class="sxs-lookup"><span data-stu-id="6f526-236">-nostdlib</span></span>](nostdlib.md)|<span data-ttu-id="6f526-237">导致编译器不引用标准库。</span><span class="sxs-lookup"><span data-stu-id="6f526-237">Causes the compiler not to reference the standard libraries.</span></span>|  
|[<span data-ttu-id="6f526-238">-nowin32manifest</span><span class="sxs-lookup"><span data-stu-id="6f526-238">-nowin32manifest</span></span>](nowin32manifest.md)|<span data-ttu-id="6f526-239">指示编译器不在可执行文件中嵌入任何应用程序清单。</span><span class="sxs-lookup"><span data-stu-id="6f526-239">Instructs the compiler not to embed any application manifest into the executable file.</span></span>|  
|[<span data-ttu-id="6f526-240">-platform</span><span class="sxs-lookup"><span data-stu-id="6f526-240">-platform</span></span>](platform.md)|<span data-ttu-id="6f526-241">为输出文件指定编译器面向的处理器平台。</span><span class="sxs-lookup"><span data-stu-id="6f526-241">Specifies the processor platform the compiler targets for the output file.</span></span>|  
|[<span data-ttu-id="6f526-242">-recurse</span><span class="sxs-lookup"><span data-stu-id="6f526-242">-recurse</span></span>](recurse.md)|<span data-ttu-id="6f526-243">搜索要编译的源文件的子目录。</span><span class="sxs-lookup"><span data-stu-id="6f526-243">Searches subdirectories for source files to compile.</span></span>|  
|[<span data-ttu-id="6f526-244">-rootnamespace</span><span class="sxs-lookup"><span data-stu-id="6f526-244">-rootnamespace</span></span>](rootnamespace.md)|<span data-ttu-id="6f526-245">指定所有类型声明的命名空间。</span><span class="sxs-lookup"><span data-stu-id="6f526-245">Specifies a namespace for all type declarations.</span></span>|  
|[<span data-ttu-id="6f526-246">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="6f526-246">-sdkpath</span></span>](sdkpath.md)|<span data-ttu-id="6f526-247">指定 Mscorlib.dll 和 Microsoft.VisualBasic.dll 的位置。</span><span class="sxs-lookup"><span data-stu-id="6f526-247">Specifies the location of Mscorlib.dll and Microsoft.VisualBasic.dll.</span></span>|  
|[<span data-ttu-id="6f526-248">-vbruntime</span><span class="sxs-lookup"><span data-stu-id="6f526-248">-vbruntime</span></span>](vbruntime.md)|<span data-ttu-id="6f526-249">指定编译器应在不引用 Visual Basic 运行库的情况下进行编译，或在引用特定运行库的情况下进行编译。</span><span class="sxs-lookup"><span data-stu-id="6f526-249">Specifies that the compiler should compile without a reference to the Visual Basic Runtime Library, or with a reference to a specific runtime library.</span></span>|  
|[<span data-ttu-id="6f526-250">-win32manifest</span><span class="sxs-lookup"><span data-stu-id="6f526-250">-win32manifest</span></span>](win32manifest.md)|<span data-ttu-id="6f526-251">标识用户定义的 Win32 应用程序清单文件要嵌入到项目的可移植可执行 (PE) 文件。</span><span class="sxs-lookup"><span data-stu-id="6f526-251">Identifies a user-defined Win32 application manifest file to be embedded into a project's portable executable (PE) file.</span></span>|  
|`-parallel[+&#124;-]`|<span data-ttu-id="6f526-252">指定是否使用并发生成 (+)。</span><span class="sxs-lookup"><span data-stu-id="6f526-252">Specifies whether to use concurrent build (+).</span></span>|  
|`-checksumalgorithm:<alg>`|<span data-ttu-id="6f526-253">指定用于计算 PDB 中存储的源文件校验和的算法。</span><span class="sxs-lookup"><span data-stu-id="6f526-253">Specify the algorithm for calculating the source file checksum stored in PDB.</span></span>  <span data-ttu-id="6f526-254">受支持的值为:SHA1（默认值）或 SHA256。</span><span class="sxs-lookup"><span data-stu-id="6f526-254">Supported values are: SHA1 (default) or SHA256.</span></span> <br><span data-ttu-id="6f526-255">由于与 SHA1 冲突，Microsoft 建议使用 SHA256 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="6f526-255">Due to collision problems with SHA1, Microsoft recommends SHA256 or better.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6f526-256">请参阅</span><span class="sxs-lookup"><span data-stu-id="6f526-256">See also</span></span>

- [<span data-ttu-id="6f526-257">按字母顺序列出的 Visual Basic 编译器选项</span><span class="sxs-lookup"><span data-stu-id="6f526-257">Visual Basic Compiler Options Listed Alphabetically</span></span>](compiler-options-listed-alphabetically.md)
- [<span data-ttu-id="6f526-258">管理项目和解决方案属性</span><span class="sxs-lookup"><span data-stu-id="6f526-258">Manage project and solution properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
