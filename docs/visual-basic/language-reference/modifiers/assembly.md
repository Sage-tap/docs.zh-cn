---
description: '了解有关以下方面的详细信息：程序集 (Visual Basic) '
title: 程序集
ms.date: 07/20/2015
f1_keywords:
- vb.Assembly
- vb.AssemblyAttribute
- Assembly
helpviewer_keywords:
- Assembly modifier
- Assembly keyword [Visual Basic]
- attribute blocks, Assembly keyword
ms.assetid: 925e7471-3bdf-4b51-bb93-cbcfc6efc52f
ms.openlocfilehash: 60b8ce4ed2b8b5cb7deeabb702c33d1e561d765f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701178"
---
# <a name="assembly-visual-basic"></a><span data-ttu-id="34398-103">程序集 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34398-103">Assembly (Visual Basic)</span></span>

<span data-ttu-id="34398-104">指定源文件开头的属性应用于整个程序集。</span><span class="sxs-lookup"><span data-stu-id="34398-104">Specifies that an attribute at the beginning of a source file applies to the entire assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34398-105">备注</span><span class="sxs-lookup"><span data-stu-id="34398-105">Remarks</span></span>  

 <span data-ttu-id="34398-106">许多属性都属于单个编程元素，如类或属性。</span><span class="sxs-lookup"><span data-stu-id="34398-106">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="34398-107">可以通过将特性块附加到尖括号 (在) 中，将此类特性直接应用于 `< >` 声明语句。</span><span class="sxs-lookup"><span data-stu-id="34398-107">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="34398-108">如果某个特性不仅与以下元素有关，而不属于整个程序集，则可以将特性块放在源文件的开头，并使用关键字标识该特性 `Assembly` 。</span><span class="sxs-lookup"><span data-stu-id="34398-108">If an attribute pertains not only to the following element but to the entire assembly, you place the attribute block at the beginning of the source file and identify the attribute with the `Assembly` keyword.</span></span> <span data-ttu-id="34398-109">如果它适用于当前程序集模块，则使用 [module](module-keyword.md) 关键字。</span><span class="sxs-lookup"><span data-stu-id="34398-109">If it applies to the current assembly module, you use the [Module](module-keyword.md) keyword.</span></span>  
  
 <span data-ttu-id="34398-110">你还可以在 AssemblyInfo 文件中将属性应用于程序集，在这种情况下，你不必在主源代码文件中使用属性块。</span><span class="sxs-lookup"><span data-stu-id="34398-110">You can also apply an attribute to an assembly in the AssemblyInfo.vb file, in which case you do not have to use an attribute block in your main source-code file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34398-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="34398-111">See also</span></span>

- [<span data-ttu-id="34398-112">模块 \<keyword></span><span class="sxs-lookup"><span data-stu-id="34398-112">Module \<keyword></span></span>](module-keyword.md)
- [<span data-ttu-id="34398-113">属性概述</span><span class="sxs-lookup"><span data-stu-id="34398-113">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
