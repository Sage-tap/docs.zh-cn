---
description: -doc（C# 编译器选项）
title: -doc（C# 编译器选项）
ms.date: 07/20/2015
f1_keywords:
- FileProperties.BuildAction
- /doc
helpviewer_keywords:
- comments, C# code
- XML documentation [C#], comments in source files
- doc compiler option [C#]
- Visual C#, XML documentation for
- -doc compiler option [C#]
- /doc compiler option [C#]
ms.assetid: 849eea59-c936-4311-bad8-d07404480f2a
ms.openlocfilehash: e55b86e5b028fb871f309d80217477cfd164c106
ms.sourcegitcommit: f0eb7eeedf3ceec726499fa678786d03083214ea
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/21/2021
ms.locfileid: "98629249"
---
# <a name="-doc-c-compiler-options"></a><span data-ttu-id="eaf23-103">-doc（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="eaf23-103">-doc (C# Compiler Options)</span></span>

<span data-ttu-id="eaf23-104">-doc 选项可让你在 XML 文件中放置文档注释。</span><span class="sxs-lookup"><span data-stu-id="eaf23-104">The **-doc** option allows you to place documentation comments in an XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eaf23-105">语法</span><span class="sxs-lookup"><span data-stu-id="eaf23-105">Syntax</span></span>  
  
```console  
-doc:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="eaf23-106">自变量</span><span class="sxs-lookup"><span data-stu-id="eaf23-106">Arguments</span></span>  

 `file`  
 <span data-ttu-id="eaf23-107">XML 的输出文件（由编译的源代码文件中的注释填充）。</span><span class="sxs-lookup"><span data-stu-id="eaf23-107">The output file for XML, which is populated with the comments in the source code files of the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eaf23-108">备注</span><span class="sxs-lookup"><span data-stu-id="eaf23-108">Remarks</span></span>  

 <span data-ttu-id="eaf23-109">在源代码文件中，可以处理以下内容之前的文档注释，并将其添加到 XML 文件中：</span><span class="sxs-lookup"><span data-stu-id="eaf23-109">In source code files, documentation comments that precede the following can be processed and added to the XML file:</span></span>  
  
- <span data-ttu-id="eaf23-110">作为[类](../keywords/class.md)、[委托](../builtin-types/reference-types.md#the-delegate-type)或[接口](../keywords/interface.md)的用户定义类型</span><span class="sxs-lookup"><span data-stu-id="eaf23-110">Such user-defined types as a [class](../keywords/class.md), [delegate](../builtin-types/reference-types.md#the-delegate-type), or [interface](../keywords/interface.md)</span></span>  
  
- <span data-ttu-id="eaf23-111">作为字段、[事件](../keywords/event.md)、[属性](../../programming-guide/classes-and-structs/using-properties.md)或方法的成员</span><span class="sxs-lookup"><span data-stu-id="eaf23-111">Such members as a field, [event](../keywords/event.md), [property](../../programming-guide/classes-and-structs/using-properties.md), or method</span></span>  
  
 <span data-ttu-id="eaf23-112">包含 Main 的源代码文件首先输出到 XML 中。</span><span class="sxs-lookup"><span data-stu-id="eaf23-112">The source code file that contains Main is output first into the XML.</span></span>  
  
 <span data-ttu-id="eaf23-113">若要将生成的 xml 文件与 [IntelliSense](/visualstudio/ide/using-intellisense) 功能配合使用，请将 .xml 文件的文件名设为与要支持的程序集相同的名称，然后确保 .xml 文件与程序集位于同一目录中。</span><span class="sxs-lookup"><span data-stu-id="eaf23-113">To use the generated .xml file for use with the [IntelliSense](/visualstudio/ide/using-intellisense) feature, let the file name of the .xml file be the same as the assembly you want to support and then make sure the .xml file is in the same directory as the assembly.</span></span> <span data-ttu-id="eaf23-114">这样，在 Visual Studio 项目中引用程序集时，也会找到 .xml 文件。</span><span class="sxs-lookup"><span data-stu-id="eaf23-114">Thus, when the assembly is referenced in the Visual Studio project, the .xml file is found as well.</span></span> <span data-ttu-id="eaf23-115">有关详细信息，请参阅[提供代码注释](/visualstudio/ide/reference/generate-xml-documentation-comments)。</span><span class="sxs-lookup"><span data-stu-id="eaf23-115">See [Supplying Code Comments](/visualstudio/ide/reference/generate-xml-documentation-comments) and for more information.</span></span>  
  
 <span data-ttu-id="eaf23-116">除非用 [-target:module](./target-module-compiler-option.md) 进行编译，否则 `file` 将包含 \<assembly>\</assembly> 标记，指定包含编译输出文件的程序集清单的文件名。</span><span class="sxs-lookup"><span data-stu-id="eaf23-116">Unless you compile with [-target:module](./target-module-compiler-option.md), `file` will contain \<assembly>\</assembly> tags specifying the name of the file containing the assembly manifest for the output file of the compilation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eaf23-117">-doc 选项适用于所有输入文件；或者，如果在项目设置中进行设置，则适用于项目中的所有文件。</span><span class="sxs-lookup"><span data-stu-id="eaf23-117">The -doc option applies to all input files; or, if set in the Project Settings, all files in the project.</span></span> <span data-ttu-id="eaf23-118">若要禁用与特定文件或一段代码的文档注释相关的警告，请使用 [#pragma 警告](../preprocessor-directives/preprocessor-pragma-warning.md)。</span><span class="sxs-lookup"><span data-stu-id="eaf23-118">To disable warnings related to documentation comments for a specific file or section of code, use [#pragma warning](../preprocessor-directives/preprocessor-pragma-warning.md).</span></span>  
  
 <span data-ttu-id="eaf23-119">有关从代码中的注释生成文档的方法，请参阅[建议的文档注释标记](../../programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)。</span><span class="sxs-lookup"><span data-stu-id="eaf23-119">See [Recommended Tags for Documentation Comments](../../programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) for ways to generate documentation from comments in your code.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-2019-development-environment"></a><span data-ttu-id="eaf23-120">在 Visual Studio 2019 开发环境中设置此编译器选项</span><span class="sxs-lookup"><span data-stu-id="eaf23-120">To set this compiler option in the Visual Studio 2019 development environment</span></span>  

1. <span data-ttu-id="eaf23-121">打开项目的“属性”页。</span><span class="sxs-lookup"><span data-stu-id="eaf23-121">Open the project's **Properties** page.</span></span>  
2. <span data-ttu-id="eaf23-122">单击“生成”选项卡。</span><span class="sxs-lookup"><span data-stu-id="eaf23-122">Click the **Build** tab.</span></span>
3. <span data-ttu-id="eaf23-123">修改“XML 文档文件”属性。</span><span class="sxs-lookup"><span data-stu-id="eaf23-123">Modify the **XML documentation file** property.</span></span>
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-for-mac-development-environment"></a><span data-ttu-id="eaf23-124">在 Visual Studio for Mac 开发环境中设置此编译器选项</span><span class="sxs-lookup"><span data-stu-id="eaf23-124">To set this compiler option in the Visual Studio for Mac development environment</span></span>  
  
1. <span data-ttu-id="eaf23-125">打开项目的“选项”页。</span><span class="sxs-lookup"><span data-stu-id="eaf23-125">Open the project's **Options** page.</span></span>
2. <span data-ttu-id="eaf23-126">选择“编译器”选项卡。</span><span class="sxs-lookup"><span data-stu-id="eaf23-126">Select the **Compiler** tab.</span></span>
3. <span data-ttu-id="eaf23-127">选择“生成 xml 文档”并在文本框中输入文件名。</span><span class="sxs-lookup"><span data-stu-id="eaf23-127">Select **Generate xml documentation** and enter the file name in the text box.</span></span>

<span data-ttu-id="eaf23-128">有关如何以编程方式设置此编译器选项的信息，请参阅 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>。</span><span class="sxs-lookup"><span data-stu-id="eaf23-128">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaf23-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="eaf23-129">See also</span></span>

- [<span data-ttu-id="eaf23-130">C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="eaf23-130">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="eaf23-131">管理项目和解决方案属性</span><span class="sxs-lookup"><span data-stu-id="eaf23-131">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
