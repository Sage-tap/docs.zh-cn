---
description: 了解更多相关信息： BC30561： " <name1> " 不明确，从命名空间或类型 "" 导入 <name2>
title: “<name1>”不明确，从命名空间或类型“<name2>”导入
ms.date: 07/20/2015
f1_keywords:
- vbc30561
- bc30561
helpviewer_keywords:
- BC30561
ms.assetid: 761091f7-1018-4299-b481-3966a4a2c126
ms.openlocfilehash: d338d16c563be988c215dd19ac59174d79a8c7a7
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100483568"
---
# <a name="bc30561-name1-is-ambiguous-imported-from-the-namespaces-or-types-name2"></a><span data-ttu-id="bb9c5-103">BC30561： " \<name1> " 不明确，从命名空间或类型 "" 导入 \<name2></span><span class="sxs-lookup"><span data-stu-id="bb9c5-103">BC30561: '\<name1>' is ambiguous, imported from the namespaces or types '\<name2>'</span></span>

<span data-ttu-id="bb9c5-104">你提供的名称不明确，因此与另一个名称冲突。</span><span class="sxs-lookup"><span data-stu-id="bb9c5-104">You have provided a name that is ambiguous and therefore conflicts with another name.</span></span> <span data-ttu-id="bb9c5-105">Visual Basic 编译器没有任何冲突解决规则;你必须自己区分名称。</span><span class="sxs-lookup"><span data-stu-id="bb9c5-105">The Visual Basic compiler does not have any conflict resolution rules; you must disambiguate names yourself.</span></span>

 <span data-ttu-id="bb9c5-106">**错误 ID：** BC30561</span><span class="sxs-lookup"><span data-stu-id="bb9c5-106">**Error ID:** BC30561</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="bb9c5-107">更正此错误</span><span class="sxs-lookup"><span data-stu-id="bb9c5-107">To correct this error</span></span>

- <span data-ttu-id="bb9c5-108">删除命名空间导入，消除名称歧义。</span><span class="sxs-lookup"><span data-stu-id="bb9c5-108">Disambiguate the name by removing namespace imports.</span></span>

- <span data-ttu-id="bb9c5-109">完全限定名称。</span><span class="sxs-lookup"><span data-stu-id="bb9c5-109">Fully qualify the name.</span></span>

## <a name="see-also"></a><span data-ttu-id="bb9c5-110">请参阅</span><span class="sxs-lookup"><span data-stu-id="bb9c5-110">See also</span></span>

- [<span data-ttu-id="bb9c5-111">Imports 语句（.NET 命名空间和类型）</span><span class="sxs-lookup"><span data-stu-id="bb9c5-111">Imports Statement (.NET Namespace and Type)</span></span>](../statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="bb9c5-112">Visual Basic 中的命名空间</span><span class="sxs-lookup"><span data-stu-id="bb9c5-112">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="bb9c5-113">Namespace 语句</span><span class="sxs-lookup"><span data-stu-id="bb9c5-113">Namespace Statement</span></span>](../statements/namespace-statement.md)
