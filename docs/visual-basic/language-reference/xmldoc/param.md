---
description: 了解详细信息： <param> (Visual Basic)
title: <param>
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: 94fe5e11d5846f7fa00eb73c1c4363990ae23b2f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700287"
---
# <a name="param-visual-basic"></a><span data-ttu-id="60ee4-103">\<param> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="60ee4-103">\<param> (Visual Basic)</span></span>

<span data-ttu-id="60ee4-104">定义参数名称和说明。</span><span class="sxs-lookup"><span data-stu-id="60ee4-104">Defines a parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60ee4-105">语法</span><span class="sxs-lookup"><span data-stu-id="60ee4-105">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
## <a name="parameters"></a><span data-ttu-id="60ee4-106">参数</span><span class="sxs-lookup"><span data-stu-id="60ee4-106">Parameters</span></span>  

 `name`  
 <span data-ttu-id="60ee4-107">方法参数的名称。</span><span class="sxs-lookup"><span data-stu-id="60ee4-107">The name of a method parameter.</span></span> <span data-ttu-id="60ee4-108">用双引号 (" ") 将名称引起来。</span><span class="sxs-lookup"><span data-stu-id="60ee4-108">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="60ee4-109">参数的说明。</span><span class="sxs-lookup"><span data-stu-id="60ee4-109">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="60ee4-110">备注</span><span class="sxs-lookup"><span data-stu-id="60ee4-110">Remarks</span></span>  

 <span data-ttu-id="60ee4-111">在方法声明的注释中，应使用 `<param>` 标记来描述方法参数之一。</span><span class="sxs-lookup"><span data-stu-id="60ee4-111">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span>  
  
 <span data-ttu-id="60ee4-112">标记的文本 `<param>` 将出现在以下位置：</span><span class="sxs-lookup"><span data-stu-id="60ee4-112">The text for the `<param>` tag will appear in the following locations:</span></span>  
  
- <span data-ttu-id="60ee4-113">IntelliSense 的参数信息。</span><span class="sxs-lookup"><span data-stu-id="60ee4-113">Parameter Info of IntelliSense.</span></span> <span data-ttu-id="60ee4-114">有关详细信息，请参阅[使用 IntelliSense](/visualstudio/ide/using-intellisense)。</span><span class="sxs-lookup"><span data-stu-id="60ee4-114">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>  
  
- <span data-ttu-id="60ee4-115">对象浏览器。</span><span class="sxs-lookup"><span data-stu-id="60ee4-115">Object Browser.</span></span> <span data-ttu-id="60ee4-116">有关详细信息，请参阅 [查看代码的结构](/visualstudio/ide/viewing-the-structure-of-code)。</span><span class="sxs-lookup"><span data-stu-id="60ee4-116">For more information, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="60ee4-117">使用 [-doc](../../reference/command-line-compiler/doc.md) 进行编译以便将文档注释处理到文件中。</span><span class="sxs-lookup"><span data-stu-id="60ee4-117">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60ee4-118">示例</span><span class="sxs-lookup"><span data-stu-id="60ee4-118">Example</span></span>  

 <span data-ttu-id="60ee4-119">此示例使用 `<param>` 标记来描述 `id` 参数。</span><span class="sxs-lookup"><span data-stu-id="60ee4-119">This example uses the `<param>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="60ee4-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="60ee4-120">See also</span></span>

- [<span data-ttu-id="60ee4-121">XML 注释标记</span><span class="sxs-lookup"><span data-stu-id="60ee4-121">XML Comment Tags</span></span>](index.md)
