---
title: 静态类和静态类成员 - C# 编程指南
description: 使用 C# 不可实例化静态类。 可以使用类名本身访问静态类的成员。
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, static members
- static members [C#]
- static classes [C#]
- C# language, static classes
- static class members [C#]
ms.assetid: 235614b5-1371-4dbd-9abd-b406a8b0298b
ms.openlocfilehash: 31de2a7d58d610213bfa4fc0377e1ab7283e111e
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899004"
---
# <a name="static-classes-and-static-class-members-c-programming-guide"></a><span data-ttu-id="9acff-104">静态类和静态类成员（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="9acff-104">Static Classes and Static Class Members (C# Programming Guide)</span></span>

<span data-ttu-id="9acff-105">[静态](../../language-reference/keywords/static.md)类基本上与非静态类相同，但存在一个差异：静态类无法实例化。</span><span class="sxs-lookup"><span data-stu-id="9acff-105">A [static](../../language-reference/keywords/static.md) class is basically the same as a non-static class, but there is one difference: a static class cannot be instantiated.</span></span> <span data-ttu-id="9acff-106">换句话说，无法使用 [new](../../language-reference/operators/new-operator.md) 运算符创建类类型的变量。</span><span class="sxs-lookup"><span data-stu-id="9acff-106">In other words, you cannot use the [new](../../language-reference/operators/new-operator.md) operator to create a variable of the class type.</span></span> <span data-ttu-id="9acff-107">由于不存在任何实例变量，因此可以使用类名本身访问静态类的成员。</span><span class="sxs-lookup"><span data-stu-id="9acff-107">Because there is no instance variable, you access the members of a static class by using the class name itself.</span></span> <span data-ttu-id="9acff-108">例如，如果你具有一个静态类，该类名为 `UtilityClass`，并且具有一个名为 `MethodA` 的公共静态方法，如下面的示例所示：</span><span class="sxs-lookup"><span data-stu-id="9acff-108">For example, if you have a static class that is named `UtilityClass` that has a public static method named `MethodA`, you call the method as shown in the following example:</span></span>  
  
```csharp  
UtilityClass.MethodA();  
```  
  
 <span data-ttu-id="9acff-109">静态类可以用作只对输入参数进行操作并且不必获取或设置任何内部实例字段的方法集的方便容器。</span><span class="sxs-lookup"><span data-stu-id="9acff-109">A static class can be used as a convenient container for sets of methods that just operate on input parameters and do not have to get or set any internal instance fields.</span></span> <span data-ttu-id="9acff-110">例如，在 .NET 类库中，静态 <xref:System.Math?displayProperty=nameWithType> 类包含执行数学运算，而无需存储或检索对 <xref:System.Math> 类特定实例唯一的数据的方法。</span><span class="sxs-lookup"><span data-stu-id="9acff-110">For example, in the .NET Class Library, the static <xref:System.Math?displayProperty=nameWithType> class contains methods that perform mathematical operations, without any requirement to store or retrieve data that is unique to a particular instance of the <xref:System.Math> class.</span></span> <span data-ttu-id="9acff-111">即，通过指定类名和方法名称来应用类的成员，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="9acff-111">That is, you apply the members of the class by specifying the class name and the method name, as shown in the following example.</span></span>  
  
```csharp  
double dub = -3.14;  
Console.WriteLine(Math.Abs(dub));  
Console.WriteLine(Math.Floor(dub));  
Console.WriteLine(Math.Round(Math.Abs(dub)));  
  
// Output:  
// 3.14  
// -4  
// 3  
```  
  
 <span data-ttu-id="9acff-112">与所有类类型的情况一样，加载引用该类的程序时，.NET 运行时会加载静态类的类型信息。</span><span class="sxs-lookup"><span data-stu-id="9acff-112">As is the case with all class types, the type information for a static class is loaded by the .NET runtime when the program that references the class is loaded.</span></span> <span data-ttu-id="9acff-113">程序无法确切指定类加载的时间。</span><span class="sxs-lookup"><span data-stu-id="9acff-113">The program cannot specify exactly when the class is loaded.</span></span> <span data-ttu-id="9acff-114">但是，可保证进行加载，以及在程序中首次引用类之前初始化其字段并调用其静态构造函数。</span><span class="sxs-lookup"><span data-stu-id="9acff-114">However, it is guaranteed to be loaded and to have its fields initialized and its static constructor called before the class is referenced for the first time in your program.</span></span> <span data-ttu-id="9acff-115">静态构造函数只调用一次，在程序所驻留的应用程序域的生存期内，静态类会保留在内存中。</span><span class="sxs-lookup"><span data-stu-id="9acff-115">A static constructor is only called one time, and a static class remains in memory for the lifetime of the application domain in which your program resides.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9acff-116">若要创建仅允许创建本身的一个实例的非静态类，请参阅[在 C# 中实现单一实例](/previous-versions/msp-n-p/ff650316(v=pandp.10))。</span><span class="sxs-lookup"><span data-stu-id="9acff-116">To create a non-static class that allows only one instance of itself to be created, see [Implementing Singleton in C#](/previous-versions/msp-n-p/ff650316(v=pandp.10)).</span></span>  
  
 <span data-ttu-id="9acff-117">以下列表提供静态类的主要功能：</span><span class="sxs-lookup"><span data-stu-id="9acff-117">The following list provides the main features of a static class:</span></span>  
  
- <span data-ttu-id="9acff-118">只包含静态成员。</span><span class="sxs-lookup"><span data-stu-id="9acff-118">Contains only static members.</span></span>  
  
- <span data-ttu-id="9acff-119">无法进行实例化。</span><span class="sxs-lookup"><span data-stu-id="9acff-119">Cannot be instantiated.</span></span>  
  
- <span data-ttu-id="9acff-120">会进行密封。</span><span class="sxs-lookup"><span data-stu-id="9acff-120">Is sealed.</span></span>  
  
- <span data-ttu-id="9acff-121">不能包含[实例构造函数](./instance-constructors.md)。</span><span class="sxs-lookup"><span data-stu-id="9acff-121">Cannot contain [Instance Constructors](./instance-constructors.md).</span></span>  
  
 <span data-ttu-id="9acff-122">因此，创建静态类基本上与创建只包含静态成员和私有构造函数的类相同。</span><span class="sxs-lookup"><span data-stu-id="9acff-122">Creating a static class is therefore basically the same as creating a class that contains only static members and a private constructor.</span></span> <span data-ttu-id="9acff-123">私有构造函数可防止类进行实例化。</span><span class="sxs-lookup"><span data-stu-id="9acff-123">A private constructor prevents the class from being instantiated.</span></span> <span data-ttu-id="9acff-124">使用静态类的优点是编译器可以进行检查，以确保不会意外地添加任何实例成员。</span><span class="sxs-lookup"><span data-stu-id="9acff-124">The advantage of using a static class is that the compiler can check to make sure that no instance members are accidentally added.</span></span> <span data-ttu-id="9acff-125">编译器可保证无法创建此类的实例。</span><span class="sxs-lookup"><span data-stu-id="9acff-125">The compiler will guarantee that instances of this class cannot be created.</span></span>  
  
 <span data-ttu-id="9acff-126">静态类会进行密封，因此不能继承。</span><span class="sxs-lookup"><span data-stu-id="9acff-126">Static classes are sealed and therefore cannot be inherited.</span></span> <span data-ttu-id="9acff-127">它们不能继承自任何类（除了 <xref:System.Object>）。</span><span class="sxs-lookup"><span data-stu-id="9acff-127">They cannot inherit from any class except <xref:System.Object>.</span></span> <span data-ttu-id="9acff-128">静态类不能包含实例构造函数。</span><span class="sxs-lookup"><span data-stu-id="9acff-128">Static classes cannot contain an instance constructor.</span></span> <span data-ttu-id="9acff-129">但是，它们可以包含静态构造函数。</span><span class="sxs-lookup"><span data-stu-id="9acff-129">However, they can contain a static constructor.</span></span> <span data-ttu-id="9acff-130">如果非静态类包含了需要进行有意义的初始化的静态成员，则它也应该定义一个静态构造器。</span><span class="sxs-lookup"><span data-stu-id="9acff-130">Non-static classes should also define a static constructor if the class contains static members that require non-trivial initialization.</span></span> <span data-ttu-id="9acff-131">有关详细信息，请参阅[静态构造函数](./static-constructors.md)。</span><span class="sxs-lookup"><span data-stu-id="9acff-131">For more information, see [Static Constructors](./static-constructors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9acff-132">示例</span><span class="sxs-lookup"><span data-stu-id="9acff-132">Example</span></span>  

 <span data-ttu-id="9acff-133">下面是静态类的示例，该类包含将温度从摄氏度从华氏度以及从华氏度转换为摄氏度的两个方法：</span><span class="sxs-lookup"><span data-stu-id="9acff-133">Here is an example of a static class that contains two methods that convert temperature from Celsius to Fahrenheit and from Fahrenheit to Celsius:</span></span>  
  
 [!code-csharp[TemperatureConverter#1](snippets/static-classes-and-static-class-members/Program.cs#1)]  
  
## <a name="static-members"></a><span data-ttu-id="9acff-134">静态成员</span><span class="sxs-lookup"><span data-stu-id="9acff-134">Static Members</span></span>  

 <span data-ttu-id="9acff-135">非静态类可以包含静态方法、字段、属性或事件。</span><span class="sxs-lookup"><span data-stu-id="9acff-135">A non-static class can contain static methods, fields, properties, or events.</span></span> <span data-ttu-id="9acff-136">即使未创建类的任何实例，也可对类调用静态成员。</span><span class="sxs-lookup"><span data-stu-id="9acff-136">The static member is callable on a class even when no instance of the class has been created.</span></span> <span data-ttu-id="9acff-137">静态成员始终按类名（而不是实例名称）进行访问。</span><span class="sxs-lookup"><span data-stu-id="9acff-137">The static member is always accessed by the class name, not the instance name.</span></span> <span data-ttu-id="9acff-138">静态成员只有一个副本存在（与创建的类的实例数无关）。</span><span class="sxs-lookup"><span data-stu-id="9acff-138">Only one copy of a static member exists, regardless of how many instances of the class are created.</span></span> <span data-ttu-id="9acff-139">静态方法和属性无法在其包含类型中访问非静态字段和事件，它们无法访问任何对象的实例变量，除非在方法参数中显式传递它。</span><span class="sxs-lookup"><span data-stu-id="9acff-139">Static methods and properties cannot access non-static fields and events in their containing type, and they cannot access an instance variable of any object unless it's explicitly passed in a method parameter.</span></span>  
  
 <span data-ttu-id="9acff-140">更典型的做法是声明具有一些静态成员的非静态类（而不是将整个类都声明为静态）。</span><span class="sxs-lookup"><span data-stu-id="9acff-140">It is more typical to declare a non-static class with some static members, than to declare an entire class as static.</span></span> <span data-ttu-id="9acff-141">静态字段的两个常见用途是保留已实例化的对象数的计数，或是存储必须在所有实例间共享的值。</span><span class="sxs-lookup"><span data-stu-id="9acff-141">Two common uses of static fields are to keep a count of the number of objects that have been instantiated, or to store a value that must be shared among all instances.</span></span>  
  
 <span data-ttu-id="9acff-142">静态方法可以进行重载，但不能进行替代，因为它们属于类，而不属于类的任何实例。</span><span class="sxs-lookup"><span data-stu-id="9acff-142">Static methods can be overloaded but not overridden, because they belong to the class, and not to any instance of the class.</span></span>  
  
 <span data-ttu-id="9acff-143">虽然字段不能声明为 `static const`，不过 [const](../../language-reference/keywords/const.md) 字段在其行为方面本质上是静态的。</span><span class="sxs-lookup"><span data-stu-id="9acff-143">Although a field cannot be declared as `static const`, a [const](../../language-reference/keywords/const.md) field is essentially static in its behavior.</span></span> <span data-ttu-id="9acff-144">它属于类型，而不属于类型的实例。</span><span class="sxs-lookup"><span data-stu-id="9acff-144">It belongs to the type, not to instances of the type.</span></span> <span data-ttu-id="9acff-145">因此，可以使用用于静态字段的相同 `ClassName.MemberName` 表示法来访问 `const` 字段。</span><span class="sxs-lookup"><span data-stu-id="9acff-145">Therefore, `const` fields can be accessed by using the same `ClassName.MemberName` notation that's used for static fields.</span></span> <span data-ttu-id="9acff-146">无需进行对象实例化。</span><span class="sxs-lookup"><span data-stu-id="9acff-146">No object instance is required.</span></span>  
  
 <span data-ttu-id="9acff-147">C# 不支持静态局部变量（即在方法范围中声明的变量）。</span><span class="sxs-lookup"><span data-stu-id="9acff-147">C# does not support static local variables (that is, variables that are declared in method scope).</span></span>  
  
 <span data-ttu-id="9acff-148">可在成员的返回类型之前使用 `static` 关键字声明静态类成员，如下面的示例所示：</span><span class="sxs-lookup"><span data-stu-id="9acff-148">You declare static class members by using the `static` keyword before the return type of the member, as shown in the following example:</span></span>  
  
 [!code-csharp[AutomobileExample#2](snippets/static-classes-and-static-class-members/Program.cs#2)]  
  
 <span data-ttu-id="9acff-149">在首次访问静态成员之前以及在调用构造函数（如果有）之前，会初始化静态成员。</span><span class="sxs-lookup"><span data-stu-id="9acff-149">Static members are initialized before the static member is accessed for the first time and before the static constructor, if there is one, is called.</span></span> <span data-ttu-id="9acff-150">若要访问静态类成员，请使用类的名称（而不是变量名称）指定成员的位置，如下面的示例所示：</span><span class="sxs-lookup"><span data-stu-id="9acff-150">To access a static class member, use the name of the class instead of a variable name to specify the location of the member, as shown in the following example:</span></span>  
  
 [!code-csharp[AccessingStaticMembers#3](snippets/static-classes-and-static-class-members/Program.cs#3)]  
  
 <span data-ttu-id="9acff-151">如果类包含静态字段，则提供在类加载时初始化它们的静态构造函数。</span><span class="sxs-lookup"><span data-stu-id="9acff-151">If your class contains static fields, provide a static constructor that initializes them when the class is loaded.</span></span>  
  
 <span data-ttu-id="9acff-152">对静态方法的调用会采用 Microsoft 中间语言 (MSIL) 生成调用指令，而对实例方法的调用会生成 `callvirt` 指令，该指令还会检查是否存在 null 对象引用。</span><span class="sxs-lookup"><span data-stu-id="9acff-152">A call to a static method generates a call instruction in Microsoft intermediate language (MSIL), whereas a call to an instance method generates a `callvirt` instruction, which also checks for null object references.</span></span> <span data-ttu-id="9acff-153">但是在大多数时候，两者之间的性能差异并不显著。</span><span class="sxs-lookup"><span data-stu-id="9acff-153">However, most of the time the performance difference between the two is not significant.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="9acff-154">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="9acff-154">C# Language Specification</span></span>  

<span data-ttu-id="9acff-155">有关详细信息，请参阅 [C# 语言规范](/dotnet/csharp/language-reference/language-specification/introduction)中的[静态类](~/_csharplang/spec/classes.md#static-classes)和[静态和实例成员](~/_csharplang/spec/classes.md#static-and-instance-members)。</span><span class="sxs-lookup"><span data-stu-id="9acff-155">For more information, see [Static classes](~/_csharplang/spec/classes.md#static-classes) and [Static and instance members](~/_csharplang/spec/classes.md#static-and-instance-members) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="9acff-156">该语言规范是 C# 语法和用法的权威资料。</span><span class="sxs-lookup"><span data-stu-id="9acff-156">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="9acff-157">请参阅</span><span class="sxs-lookup"><span data-stu-id="9acff-157">See also</span></span>

- [<span data-ttu-id="9acff-158">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="9acff-158">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9acff-159">static</span><span class="sxs-lookup"><span data-stu-id="9acff-159">static</span></span>](../../language-reference/keywords/static.md)
- [<span data-ttu-id="9acff-160">类</span><span class="sxs-lookup"><span data-stu-id="9acff-160">Classes</span></span>](./classes.md)
- [<span data-ttu-id="9acff-161">class</span><span class="sxs-lookup"><span data-stu-id="9acff-161">class</span></span>](../../language-reference/keywords/class.md)
- [<span data-ttu-id="9acff-162">静态构造函数</span><span class="sxs-lookup"><span data-stu-id="9acff-162">Static Constructors</span></span>](./static-constructors.md)
- [<span data-ttu-id="9acff-163">实例构造函数</span><span class="sxs-lookup"><span data-stu-id="9acff-163">Instance Constructors</span></span>](./instance-constructors.md)
