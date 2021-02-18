---
description: 详细了解：-optimize
title: -optimize
ms.date: 07/20/2015
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
ms.openlocfilehash: 812eaa544dd874fd3871e58f366a34ee8176273a
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100426694"
---
# <a name="-optimize"></a><span data-ttu-id="f4340-103">-optimize</span><span class="sxs-lookup"><span data-stu-id="f4340-103">-optimize</span></span>

<span data-ttu-id="f4340-104">启用或禁用编译器优化。</span><span class="sxs-lookup"><span data-stu-id="f4340-104">Enables or disables compiler optimizations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4340-105">语法</span><span class="sxs-lookup"><span data-stu-id="f4340-105">Syntax</span></span>  
  
```console  
-optimize[ + | - ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="f4340-106">自变量</span><span class="sxs-lookup"><span data-stu-id="f4340-106">Arguments</span></span>  
  
|<span data-ttu-id="f4340-107">术语</span><span class="sxs-lookup"><span data-stu-id="f4340-107">Term</span></span>|<span data-ttu-id="f4340-108">定义</span><span class="sxs-lookup"><span data-stu-id="f4340-108">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="f4340-109">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="f4340-109">`+` &#124; `-`</span></span>|<span data-ttu-id="f4340-110">可选。</span><span class="sxs-lookup"><span data-stu-id="f4340-110">Optional.</span></span> <span data-ttu-id="f4340-111">`-optimize-` 选项启用或禁用编译器优化。</span><span class="sxs-lookup"><span data-stu-id="f4340-111">The `-optimize-` option disables compiler optimizations.</span></span> <span data-ttu-id="f4340-112">`-optimize+` 选项启用优化。</span><span class="sxs-lookup"><span data-stu-id="f4340-112">The `-optimize+` option enables optimizations.</span></span> <span data-ttu-id="f4340-113">默认情况下，禁用优化。</span><span class="sxs-lookup"><span data-stu-id="f4340-113">By default, optimizations are disabled.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f4340-114">备注</span><span class="sxs-lookup"><span data-stu-id="f4340-114">Remarks</span></span>  

 <span data-ttu-id="f4340-115">编译器优化会使输出文件更智能、更快并且更有效。</span><span class="sxs-lookup"><span data-stu-id="f4340-115">Compiler optimizations make your output file smaller, faster, and more efficient.</span></span> <span data-ttu-id="f4340-116">但是，由于优化会导致输出文件中的代码重排，因此 `-optimize+` 可能会增加调试的难度。</span><span class="sxs-lookup"><span data-stu-id="f4340-116">However, because optimizations result in code rearrangement in the output file, `-optimize+` can make debugging difficult.</span></span>  
  
 <span data-ttu-id="f4340-117">使用 `-target:module` 为程序集生成的所有模块都必须使用与程序集相同的 `-optimize` 设置。</span><span class="sxs-lookup"><span data-stu-id="f4340-117">All modules generated with `-target:module` for an assembly must use the same `-optimize` settings as the assembly.</span></span> <span data-ttu-id="f4340-118">有关详细信息，请参阅 [-target (Visual Basic)](target.md)。</span><span class="sxs-lookup"><span data-stu-id="f4340-118">For more information, see [-target (Visual Basic)](target.md).</span></span>  
  
 <span data-ttu-id="f4340-119">可以组合 `-optimize` 和 `-debug` 选项。</span><span class="sxs-lookup"><span data-stu-id="f4340-119">You can combine the `-optimize` and `-debug` options.</span></span>  
  
|<span data-ttu-id="f4340-120">在 Visual Studio 集成开发环境中设置 -optimize</span><span class="sxs-lookup"><span data-stu-id="f4340-120">To set -optimize in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="f4340-121">1.在 **“解决方案资源管理器”** 中选择一个项目。</span><span class="sxs-lookup"><span data-stu-id="f4340-121">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="f4340-122">在“项目”菜单上，单击“属性”   。</span><span class="sxs-lookup"><span data-stu-id="f4340-122">On the **Project** menu, click **Properties**.</span></span><br />     <br /><span data-ttu-id="f4340-123">2.单击“编译”  选项卡。</span><span class="sxs-lookup"><span data-stu-id="f4340-123">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="f4340-124">3.单击“高级”  按钮。</span><span class="sxs-lookup"><span data-stu-id="f4340-124">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="f4340-125">4.修改“启用优化”  复选框。</span><span class="sxs-lookup"><span data-stu-id="f4340-125">4.  Modify the **Enable optimizations** check box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f4340-126">示例</span><span class="sxs-lookup"><span data-stu-id="f4340-126">Example</span></span>  

 <span data-ttu-id="f4340-127">下面的代码编译 `T2.vb`，并启用编译器优化。</span><span class="sxs-lookup"><span data-stu-id="f4340-127">The following code compiles `T2.vb` and enables compiler optimizations.</span></span>  
  
```console
vbc t2.vb -optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="f4340-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="f4340-128">See also</span></span>

- [<span data-ttu-id="f4340-129">Visual Basic 命令行编译器</span><span class="sxs-lookup"><span data-stu-id="f4340-129">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="f4340-130">-debug (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f4340-130">-debug (Visual Basic)</span></span>](debug.md)
- [<span data-ttu-id="f4340-131">示例编译命令行</span><span class="sxs-lookup"><span data-stu-id="f4340-131">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="f4340-132">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f4340-132">-target (Visual Basic)</span></span>](target.md)
