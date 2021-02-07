---
description: '了解有关以下内容的详细信息：受保护的 Friend (Visual Basic) '
title: Protected Friend
ms.date: 05/10/2018
f1_keywords:
- vb.ProtectedFriend
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: dcc8fd2b1aa99f910f002ac05178d379532fb73d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700970"
---
# <a name="protected-friend-visual-basic"></a><span data-ttu-id="93f94-103">受保护的 Friend (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="93f94-103">Protected Friend (Visual Basic)</span></span>

<span data-ttu-id="93f94-104">`Protected Friend` 关键字组合是一种成员访问修饰符。</span><span class="sxs-lookup"><span data-stu-id="93f94-104">The `Protected Friend` keyword combination is a member access modifier.</span></span> <span data-ttu-id="93f94-105">它在已声明的元素上授予 [朋友](friend.md) 访问和 [受保护](protected.md) 的访问，因此可以从同一程序集中的任何位置、从其自己的类和派生类中访问它们。</span><span class="sxs-lookup"><span data-stu-id="93f94-105">It confers both [Friend](friend.md) access and [Protected](protected.md) access on the declared elements, so they are accessible from anywhere in the same assembly, from their own class, and from derived classes.</span></span> <span data-ttu-id="93f94-106">只能 `Protected Friend` 在类的成员上指定; 无法应用 `Protected Friend` 于结构的成员，因为结构不能继承。</span><span class="sxs-lookup"><span data-stu-id="93f94-106">You can specify `Protected Friend` only on members of classes; you cannot apply `Protected Friend` to members of a structure because structures cannot be inherited.</span></span>

> [!NOTE]
> <span data-ttu-id="93f94-107">在 Visual Studio 中，选择 "F1 帮助" `protected friend` 可为 [受保护](protected.md) 的或 [朋友](friend.md)提供帮助。</span><span class="sxs-lookup"><span data-stu-id="93f94-107">In Visual Studio, selecting F1 help on `protected friend` provides help for either [protected](protected.md) or [friend](friend.md).</span></span> <span data-ttu-id="93f94-108">IDE 将选取光标下的单个标记，而不是组合词。</span><span class="sxs-lookup"><span data-stu-id="93f94-108">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="93f94-109">规则</span><span class="sxs-lookup"><span data-stu-id="93f94-109">Rules</span></span>

<span data-ttu-id="93f94-110">**声明上下文。**</span><span class="sxs-lookup"><span data-stu-id="93f94-110">**Declaration Context.**</span></span> <span data-ttu-id="93f94-111">`Protected Friend`只能在类级别使用。</span><span class="sxs-lookup"><span data-stu-id="93f94-111">You can use `Protected Friend` only at the class level.</span></span> <span data-ttu-id="93f94-112">这意味着元素的声明上下文 `Protected` 必须是类，且不能是源文件、命名空间、接口、模块、结构或过程。</span><span class="sxs-lookup"><span data-stu-id="93f94-112">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="see-also"></a><span data-ttu-id="93f94-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="93f94-113">See also</span></span>

- [<span data-ttu-id="93f94-114">公共</span><span class="sxs-lookup"><span data-stu-id="93f94-114">Public</span></span>](public.md)
- [<span data-ttu-id="93f94-115">Protected</span><span class="sxs-lookup"><span data-stu-id="93f94-115">Protected</span></span>](protected.md)
- [<span data-ttu-id="93f94-116">Friend</span><span class="sxs-lookup"><span data-stu-id="93f94-116">Friend</span></span>](friend.md)
- [<span data-ttu-id="93f94-117">专用</span><span class="sxs-lookup"><span data-stu-id="93f94-117">Private</span></span>](private.md)
- [<span data-ttu-id="93f94-118">Private Protected</span><span class="sxs-lookup"><span data-stu-id="93f94-118">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="93f94-119">Visual Basic 中的访问级别</span><span class="sxs-lookup"><span data-stu-id="93f94-119">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="93f94-120">过程</span><span class="sxs-lookup"><span data-stu-id="93f94-120">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="93f94-121">结构</span><span class="sxs-lookup"><span data-stu-id="93f94-121">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="93f94-122">对象和类</span><span class="sxs-lookup"><span data-stu-id="93f94-122">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
