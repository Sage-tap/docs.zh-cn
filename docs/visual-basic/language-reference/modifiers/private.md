---
description: '了解详细信息：私有 (Visual Basic) '
title: 专用
ms.date: 07/20/2015
f1_keywords:
- vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
ms.openlocfilehash: 20dcd943856e20ccb1b7cb5c0603fa5f313d2421
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700944"
---
# <a name="private-visual-basic"></a><span data-ttu-id="c9fba-103">Private (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9fba-103">Private (Visual Basic)</span></span>

<span data-ttu-id="c9fba-104">指定一个或多个已声明的编程元素只能从其声明上下文中访问，包括从任何包含的类型中。</span><span class="sxs-lookup"><span data-stu-id="c9fba-104">Specifies that one or more declared programming elements are accessible only from within their declaration context, including from within any contained types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9fba-105">备注</span><span class="sxs-lookup"><span data-stu-id="c9fba-105">Remarks</span></span>  

 <span data-ttu-id="c9fba-106">如果编程元素表示专有功能，或包含机密数据，则通常需要尽可能严格地限制对其的访问。</span><span class="sxs-lookup"><span data-stu-id="c9fba-106">If a programming element represents proprietary functionality, or contains confidential data, you usually want to limit access to it as strictly as possible.</span></span> <span data-ttu-id="c9fba-107">通过只允许定义它的模块、类或结构可以实现最大限制。</span><span class="sxs-lookup"><span data-stu-id="c9fba-107">You achieve the maximum limitation by allowing only the module, class, or structure that defines it to access it.</span></span> <span data-ttu-id="c9fba-108">若要以这种方式限制对元素的访问，可使用声明 `Private` 。</span><span class="sxs-lookup"><span data-stu-id="c9fba-108">To limit access to an element in this way, you can declare it with `Private`.</span></span>  

> [!NOTE]
> <span data-ttu-id="c9fba-109">你还可以使用 [私有受保护](private-protected.md) 的访问修饰符，这使得成员可从该类内和其包含的程序集中的派生类中访问。</span><span class="sxs-lookup"><span data-stu-id="c9fba-109">You can also use the [Private Protected](private-protected.md) access modifier, which makes a member accessible from within that class and from derived classes located in its containing assembly.</span></span>

## <a name="rules"></a><span data-ttu-id="c9fba-110">规则</span><span class="sxs-lookup"><span data-stu-id="c9fba-110">Rules</span></span>  

- <span data-ttu-id="c9fba-111">**声明上下文。**</span><span class="sxs-lookup"><span data-stu-id="c9fba-111">**Declaration Context.**</span></span> <span data-ttu-id="c9fba-112">只能在模块级别使用 `Private`。</span><span class="sxs-lookup"><span data-stu-id="c9fba-112">You can use `Private` only at module level.</span></span> <span data-ttu-id="c9fba-113">这意味着元素的声明上下文 `Private` 必须是模块、类或结构，不能是源文件、命名空间、接口或过程。</span><span class="sxs-lookup"><span data-stu-id="c9fba-113">This means the declaration context for a `Private` element must be a module, class, or structure, and cannot be a source file, namespace, interface, or procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="c9fba-114">行为</span><span class="sxs-lookup"><span data-stu-id="c9fba-114">Behavior</span></span>  
  
- <span data-ttu-id="c9fba-115">**访问级别。**</span><span class="sxs-lookup"><span data-stu-id="c9fba-115">**Access Level.**</span></span> <span data-ttu-id="c9fba-116">声明上下文内的所有代码都可以访问其 `Private` 元素。</span><span class="sxs-lookup"><span data-stu-id="c9fba-116">All code within a declaration context can access its `Private` elements.</span></span> <span data-ttu-id="c9fba-117">这包括包含类型中的代码，如枚举中的嵌套类或赋值表达式。</span><span class="sxs-lookup"><span data-stu-id="c9fba-117">This includes code within a contained type, such as a nested class or an assignment expression in an enumeration.</span></span> <span data-ttu-id="c9fba-118">声明上下文外的任何代码都不能访问其 `Private` 元素。</span><span class="sxs-lookup"><span data-stu-id="c9fba-118">No code outside of the declaration context can access its `Private` elements.</span></span>  
  
- <span data-ttu-id="c9fba-119">**访问修饰符。**</span><span class="sxs-lookup"><span data-stu-id="c9fba-119">**Access Modifiers.**</span></span> <span data-ttu-id="c9fba-120">指定访问级别的关键字称为 *访问修饰符*。</span><span class="sxs-lookup"><span data-stu-id="c9fba-120">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="c9fba-121">有关访问修饰符的比较，请参阅 [Visual Basic 中的访问级别](../../programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="c9fba-121">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="c9fba-122">`Private` 修饰符可用于下面的上下文中：</span><span class="sxs-lookup"><span data-stu-id="c9fba-122">The `Private` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="c9fba-123">Class 语句</span><span class="sxs-lookup"><span data-stu-id="c9fba-123">Class Statement</span></span>](../statements/class-statement.md)  
  
 [<span data-ttu-id="c9fba-124">Const 语句</span><span class="sxs-lookup"><span data-stu-id="c9fba-124">Const Statement</span></span>](../statements/const-statement.md)  
  
 [<span data-ttu-id="c9fba-125">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="c9fba-125">Declare Statement</span></span>](../statements/declare-statement.md)  
  
 [<span data-ttu-id="c9fba-126">Delegate 语句</span><span class="sxs-lookup"><span data-stu-id="c9fba-126">Delegate Statement</span></span>](../statements/delegate-statement.md)  
  
 [<span data-ttu-id="c9fba-127">Dim 语句</span><span class="sxs-lookup"><span data-stu-id="c9fba-127">Dim Statement</span></span>](../statements/dim-statement.md)  
  
 [<span data-ttu-id="c9fba-128">Enum 语句</span><span class="sxs-lookup"><span data-stu-id="c9fba-128">Enum Statement</span></span>](../statements/enum-statement.md)  
  
 [<span data-ttu-id="c9fba-129">Event 语句</span><span class="sxs-lookup"><span data-stu-id="c9fba-129">Event Statement</span></span>](../statements/event-statement.md)  
  
 [<span data-ttu-id="c9fba-130">Function 语句</span><span class="sxs-lookup"><span data-stu-id="c9fba-130">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="c9fba-131">Interface 语句</span><span class="sxs-lookup"><span data-stu-id="c9fba-131">Interface Statement</span></span>](../statements/interface-statement.md)  
  
 [<span data-ttu-id="c9fba-132">Property Statement</span><span class="sxs-lookup"><span data-stu-id="c9fba-132">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="c9fba-133">Structure 语句</span><span class="sxs-lookup"><span data-stu-id="c9fba-133">Structure Statement</span></span>](../statements/structure-statement.md)  
  
 [<span data-ttu-id="c9fba-134">Sub 语句</span><span class="sxs-lookup"><span data-stu-id="c9fba-134">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="c9fba-135">请参阅</span><span class="sxs-lookup"><span data-stu-id="c9fba-135">See also</span></span>

- [<span data-ttu-id="c9fba-136">公共</span><span class="sxs-lookup"><span data-stu-id="c9fba-136">Public</span></span>](public.md)
- [<span data-ttu-id="c9fba-137">Protected</span><span class="sxs-lookup"><span data-stu-id="c9fba-137">Protected</span></span>](protected.md)
- [<span data-ttu-id="c9fba-138">Friend</span><span class="sxs-lookup"><span data-stu-id="c9fba-138">Friend</span></span>](friend.md)
- [<span data-ttu-id="c9fba-139">Private Protected</span><span class="sxs-lookup"><span data-stu-id="c9fba-139">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="c9fba-140">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="c9fba-140">Protected Friend</span></span>](./protected-friend.md)
- [<span data-ttu-id="c9fba-141">Visual Basic 中的访问级别</span><span class="sxs-lookup"><span data-stu-id="c9fba-141">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="c9fba-142">过程</span><span class="sxs-lookup"><span data-stu-id="c9fba-142">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="c9fba-143">结构</span><span class="sxs-lookup"><span data-stu-id="c9fba-143">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="c9fba-144">对象和类</span><span class="sxs-lookup"><span data-stu-id="c9fba-144">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
