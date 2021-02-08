---
description: '详细了解： Handles 子句 (Visual Basic) '
title: Handles 子句
ms.date: 07/20/2015
f1_keywords:
- Handles
- vb.Handles
helpviewer_keywords:
- Handles keyword [Visual Basic]
ms.assetid: 1b051c0e-f499-42f6-acb5-6f4f27824b40
ms.openlocfilehash: 2bddfdecc163feacaaf042a7928ab16af324b0a3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99769021"
---
# <a name="handles-clause-visual-basic"></a><span data-ttu-id="40655-103">Handles 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="40655-103">Handles Clause (Visual Basic)</span></span>

<span data-ttu-id="40655-104">声明某一过程可处理指定的事件。</span><span class="sxs-lookup"><span data-stu-id="40655-104">Declares that a procedure handles a specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40655-105">语法</span><span class="sxs-lookup"><span data-stu-id="40655-105">Syntax</span></span>  
  
```vb  
proceduredeclaration Handles eventlist  
```  
  
## <a name="parts"></a><span data-ttu-id="40655-106">组成部分</span><span class="sxs-lookup"><span data-stu-id="40655-106">Parts</span></span>  

 `proceduredeclaration`  
 <span data-ttu-id="40655-107">将处理事件的过程的 `Sub` 过程声明。</span><span class="sxs-lookup"><span data-stu-id="40655-107">The `Sub` procedure declaration for the procedure that will handle the event.</span></span>  
  
 `eventlist`  
 <span data-ttu-id="40655-108">`proceduredeclaration` 要处理的事件的列表，以逗号分隔。</span><span class="sxs-lookup"><span data-stu-id="40655-108">List of the events for `proceduredeclaration` to handle, separated by commas.</span></span> <span data-ttu-id="40655-109">事件必须由当前类的基类引发，或由使用 `WithEvents` 关键字声明的对象引发。</span><span class="sxs-lookup"><span data-stu-id="40655-109">The events must be raised by either the base class for the current class, or by an object declared using the `WithEvents` keyword.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40655-110">备注</span><span class="sxs-lookup"><span data-stu-id="40655-110">Remarks</span></span>  

 <span data-ttu-id="40655-111">在过程声明的结尾使用 `Handles` 关键字，以使其处理由使用 `WithEvents` 关键字声明的对象变量引发的事件。</span><span class="sxs-lookup"><span data-stu-id="40655-111">Use the `Handles` keyword at the end of a procedure declaration to cause it to handle events raised by an object variable declared using the `WithEvents` keyword.</span></span> <span data-ttu-id="40655-112">`Handles` 关键字还可在派生类中用于处理来自基类的事件。</span><span class="sxs-lookup"><span data-stu-id="40655-112">The `Handles` keyword can also be used in a derived class to handle events from a base class.</span></span>  
  
 <span data-ttu-id="40655-113">`Handles` 关键字和 `AddHandler` 语句都允许你指定特定过程处理特定事件，但存在差异。</span><span class="sxs-lookup"><span data-stu-id="40655-113">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="40655-114">定义过程时使用 `Handles` 关键字，以指定它处理特定事件。</span><span class="sxs-lookup"><span data-stu-id="40655-114">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="40655-115">`AddHandler` 语句在运行时将过程连接到事件。</span><span class="sxs-lookup"><span data-stu-id="40655-115">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="40655-116">有关详细信息，请参阅 [AddHandler 语句](addhandler-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="40655-116">For more information, see [AddHandler Statement](addhandler-statement.md).</span></span>  
  
 <span data-ttu-id="40655-117">对于自定义事件，应用程序会在添加过程作为事件处理程序时，调用事件的 `AddHandler` 访问器。</span><span class="sxs-lookup"><span data-stu-id="40655-117">For custom events, the application invokes the event's `AddHandler` accessor when it adds the procedure as an event handler.</span></span> <span data-ttu-id="40655-118">有关自定义事件的详细信息，请参阅 [Event 语句](event-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="40655-118">For more information on custom events, see [Event Statement](event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="40655-119">示例</span><span class="sxs-lookup"><span data-stu-id="40655-119">Example</span></span>  

 [!code-vb[VbVbalrEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#2)]  
  
 <span data-ttu-id="40655-120">下面的示例演示派生类可以如何使用 `Handles` 语句处理来自基类的事件。</span><span class="sxs-lookup"><span data-stu-id="40655-120">The following example demonstrates how a derived class can use the `Handles` statement to handle an event from a base class.</span></span>  
  
 [!code-vb[VbVbalrEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="40655-121">示例</span><span class="sxs-lookup"><span data-stu-id="40655-121">Example</span></span>  

 <span data-ttu-id="40655-122">下面的示例包含 **WPF 应用程序** 项目的两个按钮事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="40655-122">The following example contains two button event handlers for a **WPF Application** project.</span></span>  
  
 [!code-vb[VbVbalrEvents#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#41)]  
  
## <a name="example"></a><span data-ttu-id="40655-123">示例</span><span class="sxs-lookup"><span data-stu-id="40655-123">Example</span></span>  

 <span data-ttu-id="40655-124">下面的示例与前面的示例等效。</span><span class="sxs-lookup"><span data-stu-id="40655-124">The following example is equivalent to the previous example.</span></span> <span data-ttu-id="40655-125">`Handles` 子句中的 `eventlist` 包含两个按钮的事件。</span><span class="sxs-lookup"><span data-stu-id="40655-125">The `eventlist` in the `Handles` clause contains the events for both buttons.</span></span>  
  
 [!code-vb[VbVbalrEvents#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#42)]  
  
## <a name="see-also"></a><span data-ttu-id="40655-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="40655-126">See also</span></span>

- [<span data-ttu-id="40655-127">WithEvents</span><span class="sxs-lookup"><span data-stu-id="40655-127">WithEvents</span></span>](../modifiers/withevents.md)
- [<span data-ttu-id="40655-128">AddHandler 语句</span><span class="sxs-lookup"><span data-stu-id="40655-128">AddHandler Statement</span></span>](addhandler-statement.md)
- [<span data-ttu-id="40655-129">RemoveHandler 语句</span><span class="sxs-lookup"><span data-stu-id="40655-129">RemoveHandler Statement</span></span>](removehandler-statement.md)
- [<span data-ttu-id="40655-130">Event 语句</span><span class="sxs-lookup"><span data-stu-id="40655-130">Event Statement</span></span>](event-statement.md)
- [<span data-ttu-id="40655-131">RaiseEvent 语句</span><span class="sxs-lookup"><span data-stu-id="40655-131">RaiseEvent Statement</span></span>](raiseevent-statement.md)
- [<span data-ttu-id="40655-132">事件</span><span class="sxs-lookup"><span data-stu-id="40655-132">Events</span></span>](../../programming-guide/language-features/events/index.md)
