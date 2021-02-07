---
description: '了解详细信息： ReadOnly (Visual Basic) '
title: ReadOnly
ms.date: 07/20/2015
f1_keywords:
- vb.ReadOnly
helpviewer_keywords:
- ReadOnly keyword [Visual Basic]
- variables [Visual Basic], read-only
- ReadOnly property
- properties [Visual Basic], read-only
- read-only variables
ms.assetid: e868185d-6142-4359-a2fd-a7965cadfce8
ms.openlocfilehash: f510271531f6e6604f2b542d8331d1a1d7f64d58
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700905"
---
# <a name="readonly-visual-basic"></a><span data-ttu-id="fed9a-103">ReadOnly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fed9a-103">ReadOnly (Visual Basic)</span></span>

<span data-ttu-id="fed9a-104">指定可以读取但不能写入变量或属性。</span><span class="sxs-lookup"><span data-stu-id="fed9a-104">Specifies that a variable or property can be read but not written.</span></span>

## <a name="remarks"></a><span data-ttu-id="fed9a-105">备注</span><span class="sxs-lookup"><span data-stu-id="fed9a-105">Remarks</span></span>

## <a name="rules"></a><span data-ttu-id="fed9a-106">规则</span><span class="sxs-lookup"><span data-stu-id="fed9a-106">Rules</span></span>

- <span data-ttu-id="fed9a-107">**声明上下文。**</span><span class="sxs-lookup"><span data-stu-id="fed9a-107">**Declaration Context.**</span></span> <span data-ttu-id="fed9a-108">只能在模块级别使用 `ReadOnly`。</span><span class="sxs-lookup"><span data-stu-id="fed9a-108">You can use `ReadOnly` only at module level.</span></span> <span data-ttu-id="fed9a-109">这意味着元素的声明上下文 `ReadOnly` 必须是类、结构或模块，不能是源文件、命名空间或过程。</span><span class="sxs-lookup"><span data-stu-id="fed9a-109">This means the declaration context for a `ReadOnly` element must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span></span>

- <span data-ttu-id="fed9a-110">**组合修饰符。**</span><span class="sxs-lookup"><span data-stu-id="fed9a-110">**Combined Modifiers.**</span></span> <span data-ttu-id="fed9a-111">不能 `ReadOnly` `Static` 在同一声明中同时指定和。</span><span class="sxs-lookup"><span data-stu-id="fed9a-111">You cannot specify `ReadOnly` together with `Static` in the same declaration.</span></span>

- <span data-ttu-id="fed9a-112">**赋值。**</span><span class="sxs-lookup"><span data-stu-id="fed9a-112">**Assigning a Value.**</span></span> <span data-ttu-id="fed9a-113">使用属性的代码 `ReadOnly` 不能设置其值。</span><span class="sxs-lookup"><span data-stu-id="fed9a-113">Code consuming a `ReadOnly` property cannot set its value.</span></span> <span data-ttu-id="fed9a-114">但有权访问基础存储的代码可以随时分配或更改值。</span><span class="sxs-lookup"><span data-stu-id="fed9a-114">But code that has access to the underlying storage can assign or change the value at any time.</span></span>

     <span data-ttu-id="fed9a-115">只能 `ReadOnly` 在其声明中或在定义它的类或结构的构造函数中为变量赋值。</span><span class="sxs-lookup"><span data-stu-id="fed9a-115">You can assign a value to a `ReadOnly` variable only in its declaration or in the constructor of a class or structure in which it is defined.</span></span>

## <a name="when-to-use-a-readonly-variable"></a><span data-ttu-id="fed9a-116">何时使用 ReadOnly 变量</span><span class="sxs-lookup"><span data-stu-id="fed9a-116">When to Use a ReadOnly Variable</span></span>

<span data-ttu-id="fed9a-117">在某些情况下，不能使用 [Const 语句](../statements/const-statement.md) 来声明和分配常量值。</span><span class="sxs-lookup"><span data-stu-id="fed9a-117">There are situations in which you cannot use a [Const Statement](../statements/const-statement.md) to declare and assign a constant value.</span></span> <span data-ttu-id="fed9a-118">例如， `Const` 语句可能不接受您要分配的数据类型，或者您可能无法在编译时使用常量表达式来计算值。</span><span class="sxs-lookup"><span data-stu-id="fed9a-118">For example, the `Const` statement might not accept the data type you want to assign, or you might not be able to compute the value at compile time with a constant expression.</span></span> <span data-ttu-id="fed9a-119">在编译时，您甚至不知道值。</span><span class="sxs-lookup"><span data-stu-id="fed9a-119">You might not even know the value at compile time.</span></span> <span data-ttu-id="fed9a-120">在这些情况下，可以使用 `ReadOnly` 变量来保存常量值。</span><span class="sxs-lookup"><span data-stu-id="fed9a-120">In these cases, you can use a `ReadOnly` variable to hold a constant value.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fed9a-121">如果该变量的数据类型是引用类型（如数组或类实例），则即使该变量本身为，也可以更改其成员 `ReadOnly` 。</span><span class="sxs-lookup"><span data-stu-id="fed9a-121">If the data type of the variable is a reference type, such as an array or a class instance, its members can be changed even if the variable itself is `ReadOnly`.</span></span> <span data-ttu-id="fed9a-122">下面的示例阐释了这一点。</span><span class="sxs-lookup"><span data-stu-id="fed9a-122">The following example illustrates this.</span></span>

```vb
ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}
Sub ChangeArrayElement()
    characterArray(1) = "M"c
End Sub
```

<span data-ttu-id="fed9a-123">初始化后，由指向的数组 `characterArray()` 包含 "x"、"y" 和 "z"。</span><span class="sxs-lookup"><span data-stu-id="fed9a-123">When initialized, the array pointed to by `characterArray()` holds "x", "y", and "z".</span></span> <span data-ttu-id="fed9a-124">由于变量 `characterArray` 为 `ReadOnly` ，因此在初始化后无法更改其值; 也就是说，您不能为其分配新数组。</span><span class="sxs-lookup"><span data-stu-id="fed9a-124">Because the variable `characterArray` is `ReadOnly`, you cannot change its value once it is initialized; that is, you cannot assign a new array to it.</span></span> <span data-ttu-id="fed9a-125">但是，您可以更改一个或多个数组成员的值。</span><span class="sxs-lookup"><span data-stu-id="fed9a-125">However, you can change the values of one or more of the array members.</span></span> <span data-ttu-id="fed9a-126">调用过程后 `ChangeArrayElement` ，由指向的数组 `characterArray()` 包含 "x"、"M" 和 "z"。</span><span class="sxs-lookup"><span data-stu-id="fed9a-126">Following a call to the procedure `ChangeArrayElement`, the array pointed to by `characterArray()` holds "x", "M", and "z".</span></span>

<span data-ttu-id="fed9a-127">请注意，这类似于将过程参数声明为 [ByVal](byval.md)，这会阻止过程更改调用自变量本身，但允许该过程更改其成员。</span><span class="sxs-lookup"><span data-stu-id="fed9a-127">Note that this is similar to declaring a procedure parameter to be [ByVal](byval.md), which prevents the procedure from changing the calling argument itself but allows it to change its members.</span></span>

## <a name="example"></a><span data-ttu-id="fed9a-128">示例</span><span class="sxs-lookup"><span data-stu-id="fed9a-128">Example</span></span>

<span data-ttu-id="fed9a-129">下面的示例定义了 `ReadOnly` 雇员雇用日期的属性。</span><span class="sxs-lookup"><span data-stu-id="fed9a-129">The following example defines a `ReadOnly` property for the date on which an employee was hired.</span></span> <span data-ttu-id="fed9a-130">类在内部将属性值存储为 `Private` 变量，并且只有类中的代码可以更改该值。</span><span class="sxs-lookup"><span data-stu-id="fed9a-130">The class stores the property value internally as a `Private` variable, and only code inside the class can change that value.</span></span> <span data-ttu-id="fed9a-131">但是，属性为 `Public` ，并且任何可以访问类的代码都可以读取属性。</span><span class="sxs-lookup"><span data-stu-id="fed9a-131">However, the property is `Public`, and any code that can access the class can read the property.</span></span>

[!code-vb[VbVbalrKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#4)]

<span data-ttu-id="fed9a-132">`ReadOnly` 修饰符可用于下面的上下文中：</span><span class="sxs-lookup"><span data-stu-id="fed9a-132">The `ReadOnly` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="fed9a-133">Dim 语句</span><span class="sxs-lookup"><span data-stu-id="fed9a-133">Dim Statement</span></span>](../statements/dim-statement.md)
- [<span data-ttu-id="fed9a-134">Property Statement</span><span class="sxs-lookup"><span data-stu-id="fed9a-134">Property Statement</span></span>](../statements/property-statement.md)

## <a name="see-also"></a><span data-ttu-id="fed9a-135">请参阅</span><span class="sxs-lookup"><span data-stu-id="fed9a-135">See also</span></span>

- [<span data-ttu-id="fed9a-136">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="fed9a-136">WriteOnly</span></span>](writeonly.md)
- [<span data-ttu-id="fed9a-137">关键字</span><span class="sxs-lookup"><span data-stu-id="fed9a-137">Keywords</span></span>](../keywords/index.md)
