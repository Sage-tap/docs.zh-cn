---
title: 字段 - C# 编程指南
description: C# 中的字段是在类或结构中直接声明的任意类型的变量。 字段是其包含类型的成员。
ms.date: 07/20/2015
helpviewer_keywords:
- fields [C#]
ms.assetid: 3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7
ms.openlocfilehash: 3210500719529f8bb7f2627abf634cc7b9dcb772
ms.sourcegitcommit: b924ade6426cf61a4604c4e2ee54cb3592c29317
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/18/2021
ms.locfileid: "101096832"
---
# <a name="fields-c-programming-guide"></a><span data-ttu-id="0e4f4-104">字段（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="0e4f4-104">Fields (C# Programming Guide)</span></span>

<span data-ttu-id="0e4f4-105">字段是在[类](../../language-reference/keywords/class.md)或[结构](../../language-reference/builtin-types/struct.md)中直接声明的任意类型的变量。</span><span class="sxs-lookup"><span data-stu-id="0e4f4-105">A *field* is a variable of any type that is declared directly in a [class](../../language-reference/keywords/class.md) or [struct](../../language-reference/builtin-types/struct.md).</span></span> <span data-ttu-id="0e4f4-106">字段是其包含类型的成员。</span><span class="sxs-lookup"><span data-stu-id="0e4f4-106">Fields are *members* of their containing type.</span></span>

<span data-ttu-id="0e4f4-107">类或结构可能具有实例字段和/或静态字段。</span><span class="sxs-lookup"><span data-stu-id="0e4f4-107">A class or struct may have instance fields, static fields, or both.</span></span> <span data-ttu-id="0e4f4-108">实例字段特定于类型的实例。</span><span class="sxs-lookup"><span data-stu-id="0e4f4-108">Instance fields are specific to an instance of a type.</span></span> <span data-ttu-id="0e4f4-109">如果你有包含实例字段 F 的类 T，则可以创建两个类型为 T 的对象并修改每个对象中 F 的值，而不会影响另一个对象中的值。</span><span class="sxs-lookup"><span data-stu-id="0e4f4-109">If you have a class T, with an instance field F, you can create two objects of type T, and modify the value of F in each object without affecting the value in the other object.</span></span> <span data-ttu-id="0e4f4-110">与此相比，静态字段属于类本身，并在该类的所有实例之间共享。</span><span class="sxs-lookup"><span data-stu-id="0e4f4-110">By contrast, a static field belongs to the class itself, and is shared among all instances of that class.</span></span> <span data-ttu-id="0e4f4-111">只能使用类名称访问静态字段。</span><span class="sxs-lookup"><span data-stu-id="0e4f4-111">You can access the static field only by using the class name.</span></span> <span data-ttu-id="0e4f4-112">如果按实例名称访问静态字段，将出现 [CS0176](../../misc/cs0176.md) 编译时错误。</span><span class="sxs-lookup"><span data-stu-id="0e4f4-112">If you access the static field by an instance name, you get [CS0176](../../misc/cs0176.md) compile-time error.</span></span>

<span data-ttu-id="0e4f4-113">通常情况下，应仅对具有 private 或 protected 可访问性的变量使用字段。</span><span class="sxs-lookup"><span data-stu-id="0e4f4-113">Generally, you should use fields only for variables that have private or protected accessibility.</span></span> <span data-ttu-id="0e4f4-114">类向客户端代码公开的数据应通过[方法](./methods.md)、[属性](./properties.md)和[索引器](../indexers/index.md)提供。</span><span class="sxs-lookup"><span data-stu-id="0e4f4-114">Data that your class exposes to client code should be provided through [methods](./methods.md), [properties](./properties.md), and [indexers](../indexers/index.md).</span></span> <span data-ttu-id="0e4f4-115">通过使用这些构造间接访问内部字段，可以防止出现无效的输入值。</span><span class="sxs-lookup"><span data-stu-id="0e4f4-115">By using these constructs for indirect access to internal fields, you can guard against invalid input values.</span></span> <span data-ttu-id="0e4f4-116">存储由公共属性公开的数据的私有字段称为后备存储或支持字段。</span><span class="sxs-lookup"><span data-stu-id="0e4f4-116">A private field that stores the data exposed by a public property is called a *backing store* or *backing field*.</span></span>

<span data-ttu-id="0e4f4-117">字段通常存储必须对多个类方法可访问且存储时间必须长于任何单个方法的生存期的数据。</span><span class="sxs-lookup"><span data-stu-id="0e4f4-117">Fields typically store the data that must be accessible to more than one class method and must be stored for longer than the lifetime of any single method.</span></span> <span data-ttu-id="0e4f4-118">例如，表示日历日期的类可能具有三个整数字段：一个用于月、一个用于日、一个用于年。</span><span class="sxs-lookup"><span data-stu-id="0e4f4-118">For example, a class that represents a calendar date might have three integer fields: one for the month, one for the day, and one for the year.</span></span> <span data-ttu-id="0e4f4-119">不在单个方法作用域外使用的变量应声明为方法主体本身中的局部变量。</span><span class="sxs-lookup"><span data-stu-id="0e4f4-119">Variables that are not used outside the scope of a single method should be declared as *local variables* within the method body itself.</span></span>

<span data-ttu-id="0e4f4-120">字段是通过指定该字段的访问级别在类块中声明的，其后跟字段的类型，再跟字段的名称。</span><span class="sxs-lookup"><span data-stu-id="0e4f4-120">Fields are declared in the class block by specifying the access level of the field, followed by the type of the field, followed by the name of the field.</span></span> <span data-ttu-id="0e4f4-121">例如:</span><span class="sxs-lookup"><span data-stu-id="0e4f4-121">For example:</span></span>

[!code-csharp[fields#1](snippets/fields/Program.cs#1)]

<span data-ttu-id="0e4f4-122">若要访问对象中的字段，请在对象名称后添加一个句点，后跟字段的名称，如 `objectname._fieldName` 中所示。</span><span class="sxs-lookup"><span data-stu-id="0e4f4-122">To access a field in an object, add a period after the object name, followed by the name of the field, as in `objectname._fieldName`.</span></span> <span data-ttu-id="0e4f4-123">例如：</span><span class="sxs-lookup"><span data-stu-id="0e4f4-123">For example:</span></span>

[!code-csharp[fields#2](snippets/fields/Program.cs#2)]

<span data-ttu-id="0e4f4-124">声明字段时，可以使用赋值运算符为字段指定一个初始值。</span><span class="sxs-lookup"><span data-stu-id="0e4f4-124">A field can be given an initial value by using the assignment operator when the field is declared.</span></span> <span data-ttu-id="0e4f4-125">例如，若要为 `Day` 字段自动赋值 `"Monday"`，则需要声明 `Day`，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="0e4f4-125">To automatically assign the `Day` field to `"Monday"`, for example, you would declare `Day` as in the following example:</span></span>

[!code-csharp[fields#3](snippets/fields/Program.cs#3)]

<span data-ttu-id="0e4f4-126">字段会在对象实例的构造函数被调用之前即刻初始化。</span><span class="sxs-lookup"><span data-stu-id="0e4f4-126">Fields are initialized immediately before the constructor for the object instance is called.</span></span> <span data-ttu-id="0e4f4-127">如果构造函数分配了字段的值，则它将覆盖在字段声明期间给定的任何值。</span><span class="sxs-lookup"><span data-stu-id="0e4f4-127">If the constructor assigns the value of a field, it will overwrite any value given during field declaration.</span></span> <span data-ttu-id="0e4f4-128">有关详细信息，请参阅[使用构造函数](./using-constructors.md)。</span><span class="sxs-lookup"><span data-stu-id="0e4f4-128">For more information, see [Using Constructors](./using-constructors.md).</span></span>

> [!NOTE]
> <span data-ttu-id="0e4f4-129">字段初始化表达式不能引用其他实例字段。</span><span class="sxs-lookup"><span data-stu-id="0e4f4-129">A field initializer cannot refer to other instance fields.</span></span>

<span data-ttu-id="0e4f4-130">可以将字段标记为 [public](../../language-reference/keywords/public.md)、[private](../../language-reference/keywords/private.md)、[protected](../../language-reference/keywords/protected.md)、[internal](../../language-reference/keywords/internal.md)、[protected internal](../../language-reference/keywords/protected-internal.md) 或 [private protected](../../language-reference/keywords/private-protected.md)。</span><span class="sxs-lookup"><span data-stu-id="0e4f4-130">Fields can be marked as [public](../../language-reference/keywords/public.md), [private](../../language-reference/keywords/private.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md), or [private protected](../../language-reference/keywords/private-protected.md).</span></span> <span data-ttu-id="0e4f4-131">这些访问修饰符定义该类的用户访问该字段的方式。</span><span class="sxs-lookup"><span data-stu-id="0e4f4-131">These access modifiers define how users of the class can access the fields.</span></span> <span data-ttu-id="0e4f4-132">有关详细信息，请参阅[访问修饰符](./access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="0e4f4-132">For more information, see [Access Modifiers](./access-modifiers.md).</span></span>

<span data-ttu-id="0e4f4-133">可以选择性地将字段声明为[静态](../../language-reference/keywords/static.md)。</span><span class="sxs-lookup"><span data-stu-id="0e4f4-133">A field can optionally be declared [static](../../language-reference/keywords/static.md).</span></span> <span data-ttu-id="0e4f4-134">这可使字段可供调用方在任何时候进行调用，即使不存在任何类的实例。</span><span class="sxs-lookup"><span data-stu-id="0e4f4-134">This makes the field available to callers at any time, even if no instance of the class exists.</span></span> <span data-ttu-id="0e4f4-135">有关详细信息，请参阅[静态类和静态类成员](./static-classes-and-static-class-members.md)。</span><span class="sxs-lookup"><span data-stu-id="0e4f4-135">For more information, see [Static Classes and Static Class Members](./static-classes-and-static-class-members.md).</span></span>

<span data-ttu-id="0e4f4-136">可以将字段声明为[只读](../../language-reference/keywords/readonly.md)。</span><span class="sxs-lookup"><span data-stu-id="0e4f4-136">A field can be declared [readonly](../../language-reference/keywords/readonly.md).</span></span> <span data-ttu-id="0e4f4-137">只能在初始化期间或在构造函数中为只读字段赋值。</span><span class="sxs-lookup"><span data-stu-id="0e4f4-137">A read-only field can only be assigned a value during initialization or in a constructor.</span></span> <span data-ttu-id="0e4f4-138">`static readonly` 字段非常类似于常量，只不过 C# 编译器在编译时不具有对静态只读字段的值的访问权限，而只有在运行时才具有访问权限。</span><span class="sxs-lookup"><span data-stu-id="0e4f4-138">A `static readonly` field is very similar to a constant, except that the C# compiler does not have access to the value of a static read-only field at compile time, only at run time.</span></span> <span data-ttu-id="0e4f4-139">有关详细信息，请参阅[常量](./constants.md)。</span><span class="sxs-lookup"><span data-stu-id="0e4f4-139">For more information, see [Constants](./constants.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="0e4f4-140">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="0e4f4-140">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="0e4f4-141">请参阅</span><span class="sxs-lookup"><span data-stu-id="0e4f4-141">See also</span></span>

- [<span data-ttu-id="0e4f4-142">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="0e4f4-142">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="0e4f4-143">类和结构</span><span class="sxs-lookup"><span data-stu-id="0e4f4-143">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="0e4f4-144">使用构造函数</span><span class="sxs-lookup"><span data-stu-id="0e4f4-144">Using Constructors</span></span>](./using-constructors.md)
- [<span data-ttu-id="0e4f4-145">继承</span><span class="sxs-lookup"><span data-stu-id="0e4f4-145">Inheritance</span></span>](./inheritance.md)
- [<span data-ttu-id="0e4f4-146">访问修饰符</span><span class="sxs-lookup"><span data-stu-id="0e4f4-146">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="0e4f4-147">抽象类、密封类及类成员</span><span class="sxs-lookup"><span data-stu-id="0e4f4-147">Abstract and Sealed Classes and Class Members</span></span>](./abstract-and-sealed-classes-and-class-members.md)
