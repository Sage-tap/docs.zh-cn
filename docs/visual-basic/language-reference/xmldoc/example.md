---
description: 了解详细信息： <example> (Visual Basic)
title: <example>
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: 643e06fd24e38123dd2693d671b9ab33da5b413e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787482"
---
# <a name="example-visual-basic"></a><span data-ttu-id="380f3-103">\<example> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="380f3-103">\<example> (Visual Basic)</span></span>

<span data-ttu-id="380f3-104">指定成员的示例。</span><span class="sxs-lookup"><span data-stu-id="380f3-104">Specifies an example for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="380f3-105">语法</span><span class="sxs-lookup"><span data-stu-id="380f3-105">Syntax</span></span>  
  
```xml  
<example>description</example>  
```  
  
## <a name="parameters"></a><span data-ttu-id="380f3-106">参数</span><span class="sxs-lookup"><span data-stu-id="380f3-106">Parameters</span></span>  

 `description`  
 <span data-ttu-id="380f3-107">代码示例的说明。</span><span class="sxs-lookup"><span data-stu-id="380f3-107">A description of the code sample.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="380f3-108">备注</span><span class="sxs-lookup"><span data-stu-id="380f3-108">Remarks</span></span>  

 <span data-ttu-id="380f3-109">借助 `<example>` 标记，可以指定如何使用方法或其他库成员的示例。</span><span class="sxs-lookup"><span data-stu-id="380f3-109">The `<example>` tag lets you specify an example of how to use a method or other library member.</span></span> <span data-ttu-id="380f3-110">这通常涉及到使用 [\<code>](code.md) 标记。</span><span class="sxs-lookup"><span data-stu-id="380f3-110">This commonly involves using the [\<code>](code.md) tag.</span></span>  
  
 <span data-ttu-id="380f3-111">使用 [-doc](../../reference/command-line-compiler/doc.md) 进行编译以便将文档注释处理到文件中。</span><span class="sxs-lookup"><span data-stu-id="380f3-111">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="380f3-112">示例</span><span class="sxs-lookup"><span data-stu-id="380f3-112">Example</span></span>  

 <span data-ttu-id="380f3-113">此示例使用 `<example>` 标记来包含使用字段的示例 `ID` 。</span><span class="sxs-lookup"><span data-stu-id="380f3-113">This example uses the `<example>` tag to include an example for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="380f3-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="380f3-114">See also</span></span>

- [<span data-ttu-id="380f3-115">XML 注释标记</span><span class="sxs-lookup"><span data-stu-id="380f3-115">XML Comment Tags</span></span>](index.md)
