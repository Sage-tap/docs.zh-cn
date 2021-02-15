---
description: '了解详细信息： User-Defined 常量 (Visual Basic) '
title: 用户定义常数
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic], circular references
- Const statement [Visual Basic], user-defined constants
- user-defined constants [Visual Basic]
- scope [Visual Basic], constants
- constants [Visual Basic], user-defined
- circular references between constants [Visual Basic]
ms.assetid: a1206d5c-c45e-4ac2-970a-4a0be6a05fdd
ms.openlocfilehash: 290d4122249315ae3c6dc5e18ca4faefecb72044
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100485219"
---
# <a name="user-defined-constants-visual-basic"></a><span data-ttu-id="e9468-103">用户定义的常量 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e9468-103">User-Defined Constants (Visual Basic)</span></span>

<span data-ttu-id="e9468-104">常量是有意义的名称，用来代替不会更改的数字或字符串。</span><span class="sxs-lookup"><span data-stu-id="e9468-104">A constant is a meaningful name that takes the place of a number or string that does not change.</span></span> <span data-ttu-id="e9468-105">顾名思义，常量存储在应用程序的执行过程中保持不变的值。</span><span class="sxs-lookup"><span data-stu-id="e9468-105">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span></span> <span data-ttu-id="e9468-106">您可以使用您使用的控件或组件定义的常量，也可以创建自己的常量。</span><span class="sxs-lookup"><span data-stu-id="e9468-106">You can use constants that are defined by the controls or components you work with, or you can create your own.</span></span> <span data-ttu-id="e9468-107">您自己创建的常量被描述为 *用户定义* 的常量。</span><span class="sxs-lookup"><span data-stu-id="e9468-107">Constants you create yourself are described as *user-defined*.</span></span>  
  
 <span data-ttu-id="e9468-108">使用语句声明一个常数 `Const` ，使用与创建变量名称相同的准则。</span><span class="sxs-lookup"><span data-stu-id="e9468-108">You declare a constant with the `Const` statement, using the same guidelines you would for creating a variable name.</span></span> <span data-ttu-id="e9468-109">如果 `Option Strict` 为 `On` ，则必须显式声明常量类型。</span><span class="sxs-lookup"><span data-stu-id="e9468-109">If `Option Strict` is `On`, you must explicitly declare the constant type.</span></span>  
  
## <a name="const-statement-usage"></a><span data-ttu-id="e9468-110">Const 语句用法</span><span class="sxs-lookup"><span data-stu-id="e9468-110">Const Statement Usage</span></span>  

 <span data-ttu-id="e9468-111">`Const`语句可以表示数学或日期/时间数量：</span><span class="sxs-lookup"><span data-stu-id="e9468-111">A `Const` statement can represent a mathematical or date/time quantity:</span></span>  
  
 [!code-vb[VbEnumsTask#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#10)]  
  
 <span data-ttu-id="e9468-112">它还可以定义 `String` 常量：</span><span class="sxs-lookup"><span data-stu-id="e9468-112">It also can define `String` constants:</span></span>  
  
 [!code-vb[VbEnumsTask#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#13)]  
  
 <span data-ttu-id="e9468-113">相等符号 ( ) 右侧的表达式 `=` 通常是数字或文本字符串，但它也可以是导致数字或字符串的表达式 (但该表达式不能包含对函数) 的调用。</span><span class="sxs-lookup"><span data-stu-id="e9468-113">The expression on the right side of the equal sign ( `=` ) is often a number or literal string, but it also can be an expression that results in a number or string (although that expression cannot contain calls to functions).</span></span> <span data-ttu-id="e9468-114">甚至可以根据以前定义的常量来定义常量：</span><span class="sxs-lookup"><span data-stu-id="e9468-114">You can even define constants in terms of previously defined constants:</span></span>  
  
 [!code-vb[VbEnumsTask#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#15)]  
  
## <a name="scope-of-user-defined-constants"></a><span data-ttu-id="e9468-115">User-Defined 常量的作用域</span><span class="sxs-lookup"><span data-stu-id="e9468-115">Scope of User-Defined Constants</span></span>  

 <span data-ttu-id="e9468-116">`Const`语句的范围与同一位置中声明的变量的范围相同。</span><span class="sxs-lookup"><span data-stu-id="e9468-116">A `Const` statement's scope is the same as that of a variable declared in the same location.</span></span> <span data-ttu-id="e9468-117">可以通过以下任一方式指定作用域：</span><span class="sxs-lookup"><span data-stu-id="e9468-117">You can specify scope in any of the following ways:</span></span>  
  
- <span data-ttu-id="e9468-118">若要创建仅存在于一个过程中的常量，请在该过程中对其进行声明。</span><span class="sxs-lookup"><span data-stu-id="e9468-118">To create a constant that exists only within a procedure, declare it within that procedure.</span></span>  
  
- <span data-ttu-id="e9468-119">若要创建一个可用于类中的所有过程的常量，而不是该模块外的任何代码，请在类的声明部分中将其声明为。</span><span class="sxs-lookup"><span data-stu-id="e9468-119">To create a constant available to all procedures within a class, but not to any code outside that module, declare it in the declarations section of the class.</span></span>  
  
- <span data-ttu-id="e9468-120">若要创建可用于程序集的所有成员而不是程序集外部的常量，请 `Friend` 在类的声明部分使用关键字进行声明。</span><span class="sxs-lookup"><span data-stu-id="e9468-120">To create a constant that is available to all members of an assembly, but not to outside clients of the assembly, declare it using the `Friend` keyword in the declarations section of the class.</span></span>  
  
- <span data-ttu-id="e9468-121">若要创建可在整个应用程序中使用的常量，请 `Public` 在类的声明部分使用关键字进行声明。</span><span class="sxs-lookup"><span data-stu-id="e9468-121">To create a constant available throughout the application, declare it using the `Public` keyword in the declarations section the class.</span></span>  
  
 <span data-ttu-id="e9468-122">有关详细信息，请参阅 [如何：声明常量](how-to-declare-a-constant.md)。</span><span class="sxs-lookup"><span data-stu-id="e9468-122">For more information, see [How to: Declare A Constant](how-to-declare-a-constant.md).</span></span>  
  
### <a name="avoiding-circular-references"></a><span data-ttu-id="e9468-123">避免循环引用</span><span class="sxs-lookup"><span data-stu-id="e9468-123">Avoiding Circular References</span></span>  

 <span data-ttu-id="e9468-124">由于可以使用其他常量来定义常量，因此可能会在两个或多个常量之间意外创建 *循环* 或循环引用。</span><span class="sxs-lookup"><span data-stu-id="e9468-124">Because constants can be defined in terms of other constants, it is possible to inadvertently create a *cycle*, or circular reference, between two or more constants.</span></span> <span data-ttu-id="e9468-125">如果有两个或多个公共常量，则会发生循环，其中每个常量都是以其他方式定义的，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="e9468-125">A cycle occurs when you have two or more public constants, each of which is defined in terms of the other, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#16)]  
[!code-vb[VbEnumsTask#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#17)]  
  
 <span data-ttu-id="e9468-126">如果发生循环，Visual Basic 会生成编译器错误。</span><span class="sxs-lookup"><span data-stu-id="e9468-126">If a cycle occurs, Visual Basic generates a compiler error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9468-127">请参阅</span><span class="sxs-lookup"><span data-stu-id="e9468-127">See also</span></span>

- [<span data-ttu-id="e9468-128">Const 语句</span><span class="sxs-lookup"><span data-stu-id="e9468-128">Const Statement</span></span>](../../../language-reference/statements/const-statement.md)
- [<span data-ttu-id="e9468-129">常数和文本数据类型</span><span class="sxs-lookup"><span data-stu-id="e9468-129">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="e9468-130">常量和枚举</span><span class="sxs-lookup"><span data-stu-id="e9468-130">Constants and Enumerations</span></span>](index.md)
- [<span data-ttu-id="e9468-131">常量和枚举</span><span class="sxs-lookup"><span data-stu-id="e9468-131">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
- [<span data-ttu-id="e9468-132">枚举概述</span><span class="sxs-lookup"><span data-stu-id="e9468-132">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="e9468-133">常量概述</span><span class="sxs-lookup"><span data-stu-id="e9468-133">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="e9468-134">如何：声明枚举</span><span class="sxs-lookup"><span data-stu-id="e9468-134">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="e9468-135">枚举和名称限定</span><span class="sxs-lookup"><span data-stu-id="e9468-135">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="e9468-136">Option Strict 语句</span><span class="sxs-lookup"><span data-stu-id="e9468-136">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
