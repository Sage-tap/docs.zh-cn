---
description: '详细了解： MustOverride (Visual Basic) '
title: New
ms.date: 07/20/2015
f1_keywords:
- vb.MustOverride
- MustOverride
helpviewer_keywords:
- virtual elements [Visual Basic], pure
- elements [Visual Basic], pure virtual
- properties [Visual Basic], redefining
- procedures [Visual Basic], overriding
- overriding, MustOverride keyword
- procedures [Visual Basic], redefining
- pure virtual elements [Visual Basic]
- MustOverride keyword [Visual Basic]
- properties [Visual Basic], overriding
ms.assetid: 6e9d9ad6-bb64-433f-b32b-3ef84293bf96
ms.openlocfilehash: df7200a7f7ec4bfda34765747d6318bc50a38dd1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774520"
---
# <a name="mustoverride-visual-basic"></a><span data-ttu-id="f2777-103">MustOverride (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2777-103">MustOverride (Visual Basic)</span></span>

<span data-ttu-id="f2777-104">指定在此类中未实现的属性或过程，并且在使用之前必须在派生类中重写该属性或过程。</span><span class="sxs-lookup"><span data-stu-id="f2777-104">Specifies that a property or procedure is not implemented in this class and must be overridden in a derived class before it can be used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2777-105">备注</span><span class="sxs-lookup"><span data-stu-id="f2777-105">Remarks</span></span>  

 <span data-ttu-id="f2777-106">`MustOverride`只能在属性或过程声明语句中使用。</span><span class="sxs-lookup"><span data-stu-id="f2777-106">You can use `MustOverride` only in a property or procedure declaration statement.</span></span> <span data-ttu-id="f2777-107">指定的属性或过程 `MustOverride` 必须是类的成员，并且该类必须标记为 [MustInherit](mustinherit.md)。</span><span class="sxs-lookup"><span data-stu-id="f2777-107">The property or procedure that specifies `MustOverride` must be a member of a class, and the class must be marked [MustInherit](mustinherit.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="f2777-108">规则</span><span class="sxs-lookup"><span data-stu-id="f2777-108">Rules</span></span>  
  
- <span data-ttu-id="f2777-109">**不完整声明。**</span><span class="sxs-lookup"><span data-stu-id="f2777-109">**Incomplete Declaration.**</span></span> <span data-ttu-id="f2777-110">如果指定 `MustOverride` ，则不会为属性或过程提供任何其他代码行，甚至不为 `End Function` 、或语句提供任何代码行 `End Property` `End Sub` 。</span><span class="sxs-lookup"><span data-stu-id="f2777-110">When you specify `MustOverride`, you do not supply any additional lines of code for the property or procedure, not even the `End Function`, `End Property`, or `End Sub` statement.</span></span>  
  
- <span data-ttu-id="f2777-111">**组合修饰符。**</span><span class="sxs-lookup"><span data-stu-id="f2777-111">**Combined Modifiers.**</span></span> <span data-ttu-id="f2777-112">不能 `MustOverride` `NotOverridable` `Overridable` `Shared` 在同一声明中同时指定、或。</span><span class="sxs-lookup"><span data-stu-id="f2777-112">You cannot specify `MustOverride` together with `NotOverridable`, `Overridable`, or `Shared` in the same declaration.</span></span>  
  
- <span data-ttu-id="f2777-113">**隐藏和重写操作。**</span><span class="sxs-lookup"><span data-stu-id="f2777-113">**Shadowing and Overriding.**</span></span> <span data-ttu-id="f2777-114">隐藏和重写操作都可重新定义继承的元素，但这两种方法之间又具有很大的差异。</span><span class="sxs-lookup"><span data-stu-id="f2777-114">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="f2777-115">有关详细信息，请参阅 [Visual Basic 中的隐藏](../../programming-guide/language-features/declared-elements/shadowing.md)。</span><span class="sxs-lookup"><span data-stu-id="f2777-115">For more information, see [Shadowing in Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
- <span data-ttu-id="f2777-116">**替代条款。**</span><span class="sxs-lookup"><span data-stu-id="f2777-116">**Alternate Terms.**</span></span> <span data-ttu-id="f2777-117">除了在重写中外，不能使用的元素有时称为 *纯虚拟* 元素。</span><span class="sxs-lookup"><span data-stu-id="f2777-117">An element that cannot be used except in an override is sometimes called a *pure virtual* element.</span></span>  
  
 <span data-ttu-id="f2777-118">`MustOverride` 修饰符可用于下面的上下文中：</span><span class="sxs-lookup"><span data-stu-id="f2777-118">The `MustOverride` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="f2777-119">Function 语句</span><span class="sxs-lookup"><span data-stu-id="f2777-119">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="f2777-120">Property Statement</span><span class="sxs-lookup"><span data-stu-id="f2777-120">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="f2777-121">Sub 语句</span><span class="sxs-lookup"><span data-stu-id="f2777-121">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="f2777-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="f2777-122">See also</span></span>

- [<span data-ttu-id="f2777-123">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="f2777-123">NotOverridable</span></span>](notoverridable.md)
- [<span data-ttu-id="f2777-124">Overrides</span><span class="sxs-lookup"><span data-stu-id="f2777-124">Overridable</span></span>](overridable.md)
- [<span data-ttu-id="f2777-125">替代</span><span class="sxs-lookup"><span data-stu-id="f2777-125">Overrides</span></span>](overrides.md)
- [<span data-ttu-id="f2777-126">MustInherit</span><span class="sxs-lookup"><span data-stu-id="f2777-126">MustInherit</span></span>](mustinherit.md)
- [<span data-ttu-id="f2777-127">关键字</span><span class="sxs-lookup"><span data-stu-id="f2777-127">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="f2777-128">Visual Basic 中的隐藏</span><span class="sxs-lookup"><span data-stu-id="f2777-128">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
