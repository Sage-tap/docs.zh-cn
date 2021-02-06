---
description: '了解有关以下方面的详细信息：模块 <keyword> (Visual Basic) '
title: 模块 <keyword>
ms.date: 07/20/2015
f1_keywords:
- vb.ModuleAttribute
helpviewer_keywords:
- Module keyword [Visual Basic]
- Module modifier
- attribute blocks, Module keyword
ms.assetid: d971b940-05ab-4d56-8485-e3b8a661906b
ms.openlocfilehash: 1bd25b00b41f5da4fca535220fe4e1694c81baca
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640688"
---
# <a name="module-keyword-visual-basic"></a><span data-ttu-id="736ac-103">Module \<keyword> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="736ac-103">Module \<keyword> (Visual Basic)</span></span>

<span data-ttu-id="736ac-104">指定源文件开头的属性应用于当前程序集模块。</span><span class="sxs-lookup"><span data-stu-id="736ac-104">Specifies that an attribute at the beginning of a source file applies to the current assembly module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="736ac-105">备注</span><span class="sxs-lookup"><span data-stu-id="736ac-105">Remarks</span></span>  

 <span data-ttu-id="736ac-106">许多属性都属于单个编程元素，如类或属性。</span><span class="sxs-lookup"><span data-stu-id="736ac-106">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="736ac-107">可以通过将特性块附加到尖括号 (在) 中，将此类特性直接应用于 `< >` 声明语句。</span><span class="sxs-lookup"><span data-stu-id="736ac-107">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="736ac-108">如果特性不仅与以下元素有关，而与当前程序集模块有关，请将特性块放在源文件的开头，并使用关键字标识特性 `Module` 。</span><span class="sxs-lookup"><span data-stu-id="736ac-108">If an attribute pertains not only to the following element but to the current assembly module, you place the attribute block at the beginning of the source file and identify the attribute with the `Module` keyword.</span></span> <span data-ttu-id="736ac-109">如果它适用于整个程序集，则可以使用 [assembly](assembly.md) 关键字。</span><span class="sxs-lookup"><span data-stu-id="736ac-109">If it applies to the entire assembly, you use the [Assembly](assembly.md) keyword.</span></span>  
  
 <span data-ttu-id="736ac-110">`Module`修饰符与[Module 语句](../statements/module-statement.md)不同。</span><span class="sxs-lookup"><span data-stu-id="736ac-110">The `Module` modifier is not the same as the [Module Statement](../statements/module-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="736ac-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="736ac-111">See also</span></span>

- [<span data-ttu-id="736ac-112">程序集</span><span class="sxs-lookup"><span data-stu-id="736ac-112">Assembly</span></span>](assembly.md)
- [<span data-ttu-id="736ac-113">Module 语句</span><span class="sxs-lookup"><span data-stu-id="736ac-113">Module Statement</span></span>](../statements/module-statement.md)
- [<span data-ttu-id="736ac-114">属性概述</span><span class="sxs-lookup"><span data-stu-id="736ac-114">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
