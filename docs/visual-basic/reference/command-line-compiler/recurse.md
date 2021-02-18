---
description: 详细了解：-recurse
title: -recurse
ms.date: 03/13/2018
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
ms.openlocfilehash: 2c0f1788c3811e24e2d51ff30e4cb2842aa0bd7a
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475872"
---
# <a name="-recurse"></a><span data-ttu-id="49fa3-103">-recurse</span><span class="sxs-lookup"><span data-stu-id="49fa3-103">-recurse</span></span>

<span data-ttu-id="49fa3-104">在指定目录或项目目录的所有子目录中编译源代码文件。</span><span class="sxs-lookup"><span data-stu-id="49fa3-104">Compiles source-code files in all child directories of either the specified directory or the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49fa3-105">语法</span><span class="sxs-lookup"><span data-stu-id="49fa3-105">Syntax</span></span>  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="49fa3-106">自变量</span><span class="sxs-lookup"><span data-stu-id="49fa3-106">Arguments</span></span>  

 `dir`  
 <span data-ttu-id="49fa3-107">可选。</span><span class="sxs-lookup"><span data-stu-id="49fa3-107">Optional.</span></span> <span data-ttu-id="49fa3-108">希望从中开始搜索的目录。</span><span class="sxs-lookup"><span data-stu-id="49fa3-108">The directory in which you want the search to begin.</span></span> <span data-ttu-id="49fa3-109">如未指定目录，搜索将从项目目录开始。</span><span class="sxs-lookup"><span data-stu-id="49fa3-109">If not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="49fa3-110">必需。</span><span class="sxs-lookup"><span data-stu-id="49fa3-110">Required.</span></span> <span data-ttu-id="49fa3-111">要搜索的文件。</span><span class="sxs-lookup"><span data-stu-id="49fa3-111">The file(s) to search for.</span></span> <span data-ttu-id="49fa3-112">允许通配符。</span><span class="sxs-lookup"><span data-stu-id="49fa3-112">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="49fa3-113">备注</span><span class="sxs-lookup"><span data-stu-id="49fa3-113">Remarks</span></span>  

 <span data-ttu-id="49fa3-114">可在文件名中使用通配符，对项目目录中的所有匹配文件进行编译，而无需使用 `-recurse`。</span><span class="sxs-lookup"><span data-stu-id="49fa3-114">You can use wildcards in a file name to compile all matching files in the project directory without using `-recurse`.</span></span> <span data-ttu-id="49fa3-115">如果未指定输出文件名，编译器会将输出文件名建立在处理的第一个输入文件的基础上。</span><span class="sxs-lookup"><span data-stu-id="49fa3-115">If no output file name is specified, the compiler bases the output file name on the first input file processed.</span></span> <span data-ttu-id="49fa3-116">这通常是按字母顺序查看时所编译文件列表中的第一个文件。</span><span class="sxs-lookup"><span data-stu-id="49fa3-116">This is generally the first file in the list of files compiled when viewed alphabetically.</span></span> <span data-ttu-id="49fa3-117">因此，最好使用 `-out` 选项来指定输出文件。</span><span class="sxs-lookup"><span data-stu-id="49fa3-117">For this reason, it is best to specify an output file using the `-out` option.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="49fa3-118">`-recurse` 选项在 Visual Studio 开发环境内无法使用；仅当从命令行编译时才可用。</span><span class="sxs-lookup"><span data-stu-id="49fa3-118">The `-recurse` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49fa3-119">示例</span><span class="sxs-lookup"><span data-stu-id="49fa3-119">Example</span></span>  

 <span data-ttu-id="49fa3-120">以下命令编译当前目录中的所有 Visual Basic 文件。</span><span class="sxs-lookup"><span data-stu-id="49fa3-120">The following command compiles all Visual Basic files in the current directory.</span></span>  
  
```console
vbc *.vb  
```  
  
 <span data-ttu-id="49fa3-121">以下命令编译 `Test\ABC` 目录及其下任何目录中的所有 Visual Basic 文件，然后生成 `Test.ABC.dll`。</span><span class="sxs-lookup"><span data-stu-id="49fa3-121">The following command compiles all Visual Basic files in the `Test\ABC` directory and any directories below it, and then generates `Test.ABC.dll`.</span></span>  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="49fa3-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="49fa3-122">See also</span></span>

- [<span data-ttu-id="49fa3-123">Visual Basic 命令行编译器</span><span class="sxs-lookup"><span data-stu-id="49fa3-123">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="49fa3-124">-out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="49fa3-124">-out (Visual Basic)</span></span>](out.md)
- [<span data-ttu-id="49fa3-125">示例编译命令行</span><span class="sxs-lookup"><span data-stu-id="49fa3-125">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
