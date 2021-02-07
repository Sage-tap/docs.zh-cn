---
description: 了解详细信息： BC30145：无法发出程序集： <error message>
title: 无法发出程序集：<error message>
ms.date: 08/14/2018
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
ms.openlocfilehash: 015ab6e1d186495d72bddd65678ab15088c0f1b2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99674878"
---
# <a name="bc30145-unable-to-emit-assembly-error-message"></a><span data-ttu-id="9dca4-103">BC30145：无法发出程序集： \<error message></span><span class="sxs-lookup"><span data-stu-id="9dca4-103">BC30145: Unable to emit assembly: \<error message></span></span>

<span data-ttu-id="9dca4-104">Visual Basic 编译器调用程序集链接器 (*Al.exe*（也称为 Alink) ）以生成包含清单的程序集，并且链接器在创建该程序集的辐射阶段报告错误。</span><span class="sxs-lookup"><span data-stu-id="9dca4-104">The Visual Basic compiler calls the Assembly Linker (*Al.exe*, also known as Alink) to generate an assembly with a manifest, and the linker reports an error in the emission stage of creating the assembly.</span></span>

<span data-ttu-id="9dca4-105">**错误 ID：** BC30145</span><span class="sxs-lookup"><span data-stu-id="9dca4-105">**Error ID:** BC30145</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="9dca4-106">更正此错误</span><span class="sxs-lookup"><span data-stu-id="9dca4-106">To correct this error</span></span>

1. <span data-ttu-id="9dca4-107">检查引用的错误消息并参考主题 [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) 以获取进一步的说明和建议。</span><span class="sxs-lookup"><span data-stu-id="9dca4-107">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) for further explanation and advice.</span></span>

2. <span data-ttu-id="9dca4-108">尝试使用 [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) 或 [Sn.exe (强名称工具) ](../../../framework/tools/sn-exe-strong-name-tool.md)，手动对程序集进行签名。</span><span class="sxs-lookup"><span data-stu-id="9dca4-108">Try signing the assembly manually, using either the [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) or the [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md).</span></span>

3. <span data-ttu-id="9dca4-109">如果仍然出现错误，则收集有关该情况的信息并通知 Microsoft 产品支持服务。</span><span class="sxs-lookup"><span data-stu-id="9dca4-109">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>

### <a name="to-sign-the-assembly-manually"></a><span data-ttu-id="9dca4-110">手动对程序集进行签名</span><span class="sxs-lookup"><span data-stu-id="9dca4-110">To sign the assembly manually</span></span>

1. <span data-ttu-id="9dca4-111">使用 [Sn.exe (强名称工具) ](../../../framework/tools/sn-exe-strong-name-tool.md)) 来创建公钥/私钥对文件。</span><span class="sxs-lookup"><span data-stu-id="9dca4-111">Use the [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)) to create a public/private key pair file.</span></span>

   <span data-ttu-id="9dca4-112">此文件的扩展名为 *.snk* 。</span><span class="sxs-lookup"><span data-stu-id="9dca4-112">This file has an *.snk* extension.</span></span>

2. <span data-ttu-id="9dca4-113">从项目中删除生成错误的 COM 引用。</span><span class="sxs-lookup"><span data-stu-id="9dca4-113">Delete the COM reference that is generating the error from your project.</span></span>

3. <span data-ttu-id="9dca4-114">打开 [Visual Studio 的开发人员命令提示](../../../framework/tools/developer-command-prompt-for-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="9dca4-114">Open the [Developer Command Prompt for Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md).</span></span>

   <span data-ttu-id="9dca4-115">在 Windows 10 中，在任务栏上的搜索框中输入 " **开发人员命令提示** "。</span><span class="sxs-lookup"><span data-stu-id="9dca4-115">In Windows 10, enter **Developer command prompt** into the search box on the task bar.</span></span> <span data-ttu-id="9dca4-116">然后，从结果列表中选择 **VS 2017 开发人员命令提示** 。</span><span class="sxs-lookup"><span data-stu-id="9dca4-116">Then, select **Developer Command Prompt for VS 2017** from the results list.</span></span>

4. <span data-ttu-id="9dca4-117">将目录更改为要在其中放置程序集包装的目录。</span><span class="sxs-lookup"><span data-stu-id="9dca4-117">Change the directory to the directory where you want to place your assembly wrapper.</span></span>

5. <span data-ttu-id="9dca4-118">输入以下命令：</span><span class="sxs-lookup"><span data-stu-id="9dca4-118">Enter the following command:</span></span>

    ```cmd
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>
    ```

   <span data-ttu-id="9dca4-119">你可能会输入的实际命令的示例如下：</span><span class="sxs-lookup"><span data-stu-id="9dca4-119">An example of the actual command you might enter is:</span></span>

    ```cmd
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"
    ```

   > [!TIP]
   > <span data-ttu-id="9dca4-120">如果路径或文件包含空格，请使用双引号。</span><span class="sxs-lookup"><span data-stu-id="9dca4-120">Use double quotation marks if a path or file contains spaces.</span></span>

6. <span data-ttu-id="9dca4-121">在 Visual Studio 中，将 .NET 程序集引用添加到刚创建的文件。</span><span class="sxs-lookup"><span data-stu-id="9dca4-121">In Visual Studio, add a .NET Assembly reference to the file you just created.</span></span>

## <a name="see-also"></a><span data-ttu-id="9dca4-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="9dca4-122">See also</span></span>

- [<span data-ttu-id="9dca4-123">Al.exe</span><span class="sxs-lookup"><span data-stu-id="9dca4-123">Al.exe</span></span>](../../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="9dca4-124">Sn.exe（强名称工具）</span><span class="sxs-lookup"><span data-stu-id="9dca4-124">Sn.exe (Strong Name Tool)</span></span>](../../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="9dca4-125">如何：创建公钥/私钥对</span><span class="sxs-lookup"><span data-stu-id="9dca4-125">How to: Create a Public-Private Key Pair</span></span>](../../../standard/assembly/create-public-private-key-pair.md)
- [<span data-ttu-id="9dca4-126">与我们交流</span><span class="sxs-lookup"><span data-stu-id="9dca4-126">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
