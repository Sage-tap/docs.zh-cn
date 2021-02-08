---
description: '了解详细信息： #ExternalSource 指令'
title: '#ExternalSource 指令'
ms.date: 07/20/2015
f1_keywords:
- '#Externalsource'
- '#ExternalSource'
- vb.ExternalSource
- Externalsource
- vb.#ExternalSource
- ExternalSource
helpviewer_keywords:
- ExternalSource directive (#ExternalSource)
- '#ExternalSource directive'
ms.assetid: 243bc6a2-34c3-4eeb-a776-9fd2bf988149
ms.openlocfilehash: 1f2e73aa152fbe2d97edcde912626696faacd5af
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797232"
---
# <a name="externalsource-directive"></a><span data-ttu-id="44b08-103">#ExternalSource 指令</span><span class="sxs-lookup"><span data-stu-id="44b08-103">#ExternalSource Directive</span></span>

<span data-ttu-id="44b08-104">指示源代码的特定行与源外部的文本之间的映射。</span><span class="sxs-lookup"><span data-stu-id="44b08-104">Indicates a mapping between specific lines of source code and text external to the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44b08-105">语法</span><span class="sxs-lookup"><span data-stu-id="44b08-105">Syntax</span></span>  
  
```vb  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a><span data-ttu-id="44b08-106">组成部分</span><span class="sxs-lookup"><span data-stu-id="44b08-106">Parts</span></span>  

 `StringLiteral`  
 <span data-ttu-id="44b08-107">外部源的路径。</span><span class="sxs-lookup"><span data-stu-id="44b08-107">The path to the external source.</span></span>  
  
 `IntLiteral`  
 <span data-ttu-id="44b08-108">外部源的第一行的行号。</span><span class="sxs-lookup"><span data-stu-id="44b08-108">The line number of the first line of the external source.</span></span>  
  
 `LogicalLine`  
 <span data-ttu-id="44b08-109">外部源中发生错误的行。</span><span class="sxs-lookup"><span data-stu-id="44b08-109">The line where the error occurs in the external source.</span></span>  
  
 `#End ExternalSource`  
 <span data-ttu-id="44b08-110">终止 `#ExternalSource` 块。</span><span class="sxs-lookup"><span data-stu-id="44b08-110">Terminates the `#ExternalSource` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44b08-111">备注</span><span class="sxs-lookup"><span data-stu-id="44b08-111">Remarks</span></span>  

 <span data-ttu-id="44b08-112">此指令仅由编译器和调试器使用。</span><span class="sxs-lookup"><span data-stu-id="44b08-112">This directive is used only by the compiler and the debugger.</span></span>  
  
 <span data-ttu-id="44b08-113">源文件可能包含外部源指令，这表示源文件中特定代码行与源外部的文本之间的映射，如 .aspx 文件。</span><span class="sxs-lookup"><span data-stu-id="44b08-113">A source file may include external source directives, which indicate a mapping between specific lines of code in the source file and text external to the source, such as an .aspx file.</span></span> <span data-ttu-id="44b08-114">如果编译过程中在指定的源代码中遇到错误，则会将它们标识为来自外部源。</span><span class="sxs-lookup"><span data-stu-id="44b08-114">If errors are encountered in the designated source code during compilation, they are identified as coming from the external source.</span></span>  
  
 <span data-ttu-id="44b08-115">外部源指令对编译不起作用，因此不能嵌套。</span><span class="sxs-lookup"><span data-stu-id="44b08-115">External source directives have no effect on compilation and cannot be nested.</span></span> <span data-ttu-id="44b08-116">它们仅供应用程序内部使用。</span><span class="sxs-lookup"><span data-stu-id="44b08-116">They are intended for internal use by the application only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44b08-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="44b08-117">See also</span></span>

- [<span data-ttu-id="44b08-118">条件编译</span><span class="sxs-lookup"><span data-stu-id="44b08-118">Conditional Compilation</span></span>](../../programming-guide/program-structure/conditional-compilation.md)
