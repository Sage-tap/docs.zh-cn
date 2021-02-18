---
description: 详细了解：-keycontainer
title: -keycontainer
ms.date: 03/10/2018
helpviewer_keywords:
- -keycontainer compiler option [Visual Basic]
- keycontainer compiler option [Visual Basic]
- /keycontainer compiler option [Visual Basic]
ms.assetid: 6a9bc861-1752-4db1-9f64-b5252f0482cc
ms.openlocfilehash: d8b83162d9404eb2ce80e5e531457360b040f27d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100436807"
---
# <a name="-keycontainer"></a><span data-ttu-id="acfcf-103">-keycontainer</span><span class="sxs-lookup"><span data-stu-id="acfcf-103">-keycontainer</span></span>

<span data-ttu-id="acfcf-104">指定密钥对的密钥容器名称从而为程序集赋予强名称。</span><span class="sxs-lookup"><span data-stu-id="acfcf-104">Specifies a key container name for a key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acfcf-105">语法</span><span class="sxs-lookup"><span data-stu-id="acfcf-105">Syntax</span></span>  
  
```console  
-keycontainer:container  
```  
  
## <a name="arguments"></a><span data-ttu-id="acfcf-106">自变量</span><span class="sxs-lookup"><span data-stu-id="acfcf-106">Arguments</span></span>  
  
|<span data-ttu-id="acfcf-107">术语</span><span class="sxs-lookup"><span data-stu-id="acfcf-107">Term</span></span>|<span data-ttu-id="acfcf-108">定义</span><span class="sxs-lookup"><span data-stu-id="acfcf-108">Definition</span></span>|  
|---|---|  
|`container`|<span data-ttu-id="acfcf-109">必需。</span><span class="sxs-lookup"><span data-stu-id="acfcf-109">Required.</span></span> <span data-ttu-id="acfcf-110">包含密钥的容器文件。</span><span class="sxs-lookup"><span data-stu-id="acfcf-110">Container file that contains the key.</span></span> <span data-ttu-id="acfcf-111">如果文件名包含空格，则将它括在引号 ("") 内。</span><span class="sxs-lookup"><span data-stu-id="acfcf-111">Enclose the file name in quotation marks ("") if the name contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="acfcf-112">备注</span><span class="sxs-lookup"><span data-stu-id="acfcf-112">Remarks</span></span>  

 <span data-ttu-id="acfcf-113">通过将公钥插入到程序集清单并且用私钥签名最终程序集，编译器可创建可共享的组件。</span><span class="sxs-lookup"><span data-stu-id="acfcf-113">The compiler creates the sharable component by inserting a public key into the assembly manifest and by signing the final assembly with the private key.</span></span> <span data-ttu-id="acfcf-114">若要生成密钥文件，请在命令行键入 `sn -k file`。</span><span class="sxs-lookup"><span data-stu-id="acfcf-114">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="acfcf-115">`-i` 选项将密钥对安装到容器中。</span><span class="sxs-lookup"><span data-stu-id="acfcf-115">The `-i` option installs the key pair into a container.</span></span> <span data-ttu-id="acfcf-116">有关详细信息，请参阅 [Sn.exe（强名称工具）](../../../framework/tools/sn-exe-strong-name-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="acfcf-116">For more information, see [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span></span>  
  
 <span data-ttu-id="acfcf-117">如果使用 `-target:module` 进行编译，密钥文件的名称将保存在模块中，并在使用 [-addmodule](addmodule.md) 编译程序集时包含到创建的程序集中。</span><span class="sxs-lookup"><span data-stu-id="acfcf-117">If you compile with `-target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](addmodule.md).</span></span>  
  
 <span data-ttu-id="acfcf-118">还可以将此选项指定为任何 Microsoft 中间语言 (MSIL) 模块的源代码中的自定义特性 (<xref:System.Reflection.AssemblyKeyNameAttribute>)。</span><span class="sxs-lookup"><span data-stu-id="acfcf-118">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyNameAttribute>) in the source code for any Microsoft intermediate language (MSIL) module.</span></span>  
  
 <span data-ttu-id="acfcf-119">此外，可使用 [-keyfile](keyfile.md) 将加密信息传递给编译器。</span><span class="sxs-lookup"><span data-stu-id="acfcf-119">You can also pass your encryption information to the compiler with [-keyfile](keyfile.md).</span></span> <span data-ttu-id="acfcf-120">如果需要部分签名的程序集，请使用 [-delaysign](delaysign.md)。</span><span class="sxs-lookup"><span data-stu-id="acfcf-120">Use [-delaysign](delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="acfcf-121">有关对程序集签名的详细信息，请参阅[创建和使用具有强名称的程序集](../../../standard/assembly/create-use-strong-named.md)。</span><span class="sxs-lookup"><span data-stu-id="acfcf-121">See [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="acfcf-122">Visual Studio 开发环境内无法使用 `-keycontainer` 选项；仅当从命令行编译时才可用。</span><span class="sxs-lookup"><span data-stu-id="acfcf-122">The `-keycontainer` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="acfcf-123">示例</span><span class="sxs-lookup"><span data-stu-id="acfcf-123">Example</span></span>  

 <span data-ttu-id="acfcf-124">下面的代码编译源文件 `Input.vb`，并指定一个密钥容器。</span><span class="sxs-lookup"><span data-stu-id="acfcf-124">The following code compiles source file `Input.vb` and specifies a key container.</span></span>  
  
```console  
vbc -keycontainer:key1 input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="acfcf-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="acfcf-125">See also</span></span>

- [<span data-ttu-id="acfcf-126">.NET 中的程序集</span><span class="sxs-lookup"><span data-stu-id="acfcf-126">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="acfcf-127">Visual Basic 命令行编译器</span><span class="sxs-lookup"><span data-stu-id="acfcf-127">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="acfcf-128">-keyfile</span><span class="sxs-lookup"><span data-stu-id="acfcf-128">-keyfile</span></span>](keyfile.md)
- [<span data-ttu-id="acfcf-129">示例编译命令行</span><span class="sxs-lookup"><span data-stu-id="acfcf-129">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
