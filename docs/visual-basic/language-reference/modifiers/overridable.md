---
description: '了解更多：可重写 (Visual Basic) '
title: Overrides
ms.date: 07/20/2015
f1_keywords:
- Overridable
- vb.Overridable
helpviewer_keywords:
- elements [Visual Basic], concrete
- properties [Visual Basic], redefining
- overriding, Overridable keyword
- elements [Visual Basic], virtual
- virtual [elements VB]
- procedures [Visual Basic], overriding
- concrete [elements VB]
- procedures [Visual Basic], redefining
- Overridable keyword [Visual Basic]
- properties [Visual Basic], overriding
ms.assetid: 612581e7-8a4c-4a5d-beff-3402fffa6f35
ms.openlocfilehash: acbbd715113c836a3fb7f8a88bf74307c38ac682
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99730494"
---
# <a name="overridable-visual-basic"></a><span data-ttu-id="7c7ac-103">Overridable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7c7ac-103">Overridable (Visual Basic)</span></span>

<span data-ttu-id="7c7ac-104">指定属性或过程可由派生类中具有相同名称的属性或过程重写。</span><span class="sxs-lookup"><span data-stu-id="7c7ac-104">Specifies that a property or procedure can be overridden by an identically named property or procedure in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7c7ac-105">备注</span><span class="sxs-lookup"><span data-stu-id="7c7ac-105">Remarks</span></span>  

 <span data-ttu-id="7c7ac-106">`Overridable`修饰符允许在派生类中重写类中的属性或方法。</span><span class="sxs-lookup"><span data-stu-id="7c7ac-106">The `Overridable` modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="7c7ac-107">[NotOverridable](notoverridable.md)修饰符防止在派生类中重写属性或方法。</span><span class="sxs-lookup"><span data-stu-id="7c7ac-107">The [NotOverridable](notoverridable.md) modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="7c7ac-108">有关详细信息，请参阅[继承基础知识](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)。</span><span class="sxs-lookup"><span data-stu-id="7c7ac-108">For more information, see [Inheritance Basics](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="7c7ac-109">如果 `Overridable` `NotOverridable` 未指定或修饰符，则默认设置取决于属性或方法是重写基类属性还是替代方法。</span><span class="sxs-lookup"><span data-stu-id="7c7ac-109">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="7c7ac-110">如果属性或方法重写基类属性或方法，则默认设置为 `Overridable` ; 否则为 `NotOverridable` 。</span><span class="sxs-lookup"><span data-stu-id="7c7ac-110">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="7c7ac-111">您可以隐藏或重写来重新定义继承的元素，但这两种方法之间的差异很大。</span><span class="sxs-lookup"><span data-stu-id="7c7ac-111">You can shadow or override to redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="7c7ac-112">有关详细信息，请参阅 [Visual Basic 中的隐藏](../../programming-guide/language-features/declared-elements/shadowing.md)。</span><span class="sxs-lookup"><span data-stu-id="7c7ac-112">For more information, see [Shadowing in Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
 <span data-ttu-id="7c7ac-113">可以重写的元素有时称为 *虚拟* 元素。</span><span class="sxs-lookup"><span data-stu-id="7c7ac-113">An element that can be overridden is sometimes referred to as a *virtual* element.</span></span> <span data-ttu-id="7c7ac-114">如果可以重写，但不一定是，则有时也称为 *具体* 元素。</span><span class="sxs-lookup"><span data-stu-id="7c7ac-114">If it can be overridden, but does not have to be, it is sometimes also called a *concrete* element.</span></span>  
  
 <span data-ttu-id="7c7ac-115">`Overridable`只能在属性或过程声明语句中使用。</span><span class="sxs-lookup"><span data-stu-id="7c7ac-115">You can use `Overridable` only in a property or procedure declaration statement.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="7c7ac-116">组合修饰符</span><span class="sxs-lookup"><span data-stu-id="7c7ac-116">Combined Modifiers</span></span>  

 <span data-ttu-id="7c7ac-117">不能 `Overridable` `NotOverridable` 为方法指定或 `Private` 。</span><span class="sxs-lookup"><span data-stu-id="7c7ac-117">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="7c7ac-118">不能 `Overridable` `MustOverride` `NotOverridable` `Shared` 在同一声明中同时指定、或。</span><span class="sxs-lookup"><span data-stu-id="7c7ac-118">You cannot specify `Overridable` together with `MustOverride`, `NotOverridable`, or `Shared` in the same declaration.</span></span>  
  
 <span data-ttu-id="7c7ac-119">由于重写元素是隐式可重写的，因此不能将 `Overridable` 与 `Overrides` 组合到一起。</span><span class="sxs-lookup"><span data-stu-id="7c7ac-119">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="7c7ac-120">使用情况</span><span class="sxs-lookup"><span data-stu-id="7c7ac-120">Usage</span></span>  

 <span data-ttu-id="7c7ac-121">`Overridable` 修饰符可用于下面的上下文中：</span><span class="sxs-lookup"><span data-stu-id="7c7ac-121">The `Overridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="7c7ac-122">Function 语句</span><span class="sxs-lookup"><span data-stu-id="7c7ac-122">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="7c7ac-123">Property Statement</span><span class="sxs-lookup"><span data-stu-id="7c7ac-123">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="7c7ac-124">Sub 语句</span><span class="sxs-lookup"><span data-stu-id="7c7ac-124">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="7c7ac-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="7c7ac-125">See also</span></span>

- [<span data-ttu-id="7c7ac-126">修饰符</span><span class="sxs-lookup"><span data-stu-id="7c7ac-126">Modifiers</span></span>](index.md)
- [<span data-ttu-id="7c7ac-127">继承基础知识</span><span class="sxs-lookup"><span data-stu-id="7c7ac-127">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="7c7ac-128">New</span><span class="sxs-lookup"><span data-stu-id="7c7ac-128">MustOverride</span></span>](mustoverride.md)
- [<span data-ttu-id="7c7ac-129">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="7c7ac-129">NotOverridable</span></span>](notoverridable.md)
- [<span data-ttu-id="7c7ac-130">替代</span><span class="sxs-lookup"><span data-stu-id="7c7ac-130">Overrides</span></span>](overrides.md)
- [<span data-ttu-id="7c7ac-131">关键字</span><span class="sxs-lookup"><span data-stu-id="7c7ac-131">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="7c7ac-132">Visual Basic 中的隐藏</span><span class="sxs-lookup"><span data-stu-id="7c7ac-132">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
