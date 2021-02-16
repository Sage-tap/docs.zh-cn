---
description: '了解有关以下内容的详细信息：创建变体泛型接口 (Visual Basic) '
title: 创建变体泛型接口
ms.date: 07/20/2015
ms.assetid: d4037dd2-dfe9-4811-9150-93d4e8b20113
ms.openlocfilehash: 41da9040709ff053ba05cc7c44be989b7fa39c44
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100485258"
---
# <a name="creating-variant-generic-interfaces-visual-basic"></a><span data-ttu-id="8d2ae-103">创建变体泛型接口 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8d2ae-103">Creating Variant Generic Interfaces (Visual Basic)</span></span>

<span data-ttu-id="8d2ae-104">接口中的泛型类型参数可以声明为协变或逆变。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-104">You can declare generic type parameters in interfaces as covariant or contravariant.</span></span> <span data-ttu-id="8d2ae-105">协变允许接口方法具有与泛型类型参数定义的返回类型相比，派生程度更大的返回类型。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-105">*Covariance* allows interface methods to have more derived return types than that defined by the generic type parameters.</span></span> <span data-ttu-id="8d2ae-106">逆变允许接口方法具有与泛型形参指定的实参类型相比，派生程度更小的实参类型。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-106">*Contravariance* allows interface methods to have argument types that are less derived than that specified by the generic parameters.</span></span> <span data-ttu-id="8d2ae-107">具有协变或逆变泛型类型参数的泛型接口称为“变体”。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-107">A generic interface that has covariant or contravariant generic type parameters is called *variant*.</span></span>

> [!NOTE]
> <span data-ttu-id="8d2ae-108">.NET Framework 4 引入了对多个现有泛型接口的变体支持。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-108">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="8d2ae-109">有关 .NET Framework 中的变体接口的列表，请参阅 [泛型接口中的变体 (Visual Basic) ](variance-in-generic-interfaces.md)。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-109">For the list of the variant interfaces in the .NET Framework, see [Variance in Generic Interfaces (Visual Basic)](variance-in-generic-interfaces.md).</span></span>

## <a name="declaring-variant-generic-interfaces"></a><span data-ttu-id="8d2ae-110">声明变体泛型接口</span><span class="sxs-lookup"><span data-stu-id="8d2ae-110">Declaring Variant Generic Interfaces</span></span>

<span data-ttu-id="8d2ae-111">可通过对泛型类型参数使用 `in` 和 `out` 关键字来声明变体泛型接口。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-111">You can declare variant generic interfaces by using the `in` and `out` keywords for generic type parameters.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8d2ae-112">`ByRef` Visual Basic 中的参数不能为变体。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-112">`ByRef` parameters in Visual Basic cannot be variant.</span></span> <span data-ttu-id="8d2ae-113">值类型也不支持变体。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-113">Value types also do not support variance.</span></span>

<span data-ttu-id="8d2ae-114">可以使用 `out` 关键字将泛型类型参数声明为协变。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-114">You can declare a generic type parameter covariant by using the `out` keyword.</span></span> <span data-ttu-id="8d2ae-115">协变类型必须满足以下条件：</span><span class="sxs-lookup"><span data-stu-id="8d2ae-115">The covariant type must satisfy the following conditions:</span></span>

- <span data-ttu-id="8d2ae-116">类型仅用作接口方法的返回类型，不用作方法参数的类型。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-116">The type is used only as a return type of interface methods and not used as a type of method arguments.</span></span> <span data-ttu-id="8d2ae-117">下例演示了此要求，其中类型 `R` 为声明的协变。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-117">This is illustrated in the following example, in which the type `R` is declared covariant.</span></span>

    ```vb
    Interface ICovariant(Of Out R)
        Function GetSomething() As R
        ' The following statement generates a compiler error.
        ' Sub SetSomething(ByVal sampleArg As R)
    End Interface
    ```

    <span data-ttu-id="8d2ae-118">此规则有一个例外。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-118">There is one exception to this rule.</span></span> <span data-ttu-id="8d2ae-119">如果具有用作方法参数的逆变泛型委托，则可将类型用作该委托的泛型类型参数。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-119">If you have a contravariant generic delegate as a method parameter, you can use the type as a generic type parameter for the delegate.</span></span> <span data-ttu-id="8d2ae-120">下例中的类型 `R` 演示了此情形。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-120">This is illustrated by the type `R` in the following example.</span></span> <span data-ttu-id="8d2ae-121">有关详细信息，请参阅 [ (Visual Basic 的委托中的变体) ](variance-in-delegates.md) 和 [对 Func 和 Action 泛型委托使用变体 (Visual Basic) ](using-variance-for-func-and-action-generic-delegates.md)。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-121">For more information, see [Variance in Delegates (Visual Basic)](variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (Visual Basic)](using-variance-for-func-and-action-generic-delegates.md).</span></span>

    ```vb
    Interface ICovariant(Of Out R)
        Sub DoSomething(ByVal callback As Action(Of R))
    End Interface
    ```

- <span data-ttu-id="8d2ae-122">类型不用作接口方法的泛型约束。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-122">The type is not used as a generic constraint for the interface methods.</span></span> <span data-ttu-id="8d2ae-123">下面的代码阐释了这一点。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-123">This is illustrated in the following code.</span></span>

    ```vb
    Interface ICovariant(Of Out R)
        ' The following statement generates a compiler error
        ' because you can use only contravariant or invariant types
        ' in generic constraints.
        ' Sub DoSomething(Of T As R)()
    End Interface
    ```

<span data-ttu-id="8d2ae-124">可以使用 `in` 关键字将泛型类型参数声明为逆变。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-124">You can declare a generic type parameter contravariant by using the `in` keyword.</span></span> <span data-ttu-id="8d2ae-125">逆变类型只能用作方法参数的类型，不能用作接口方法的返回类型。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-125">The contravariant type can be used only as a type of method arguments and not as a return type of interface methods.</span></span> <span data-ttu-id="8d2ae-126">逆变类型还可用于泛型约束。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-126">The contravariant type can also be used for generic constraints.</span></span> <span data-ttu-id="8d2ae-127">以下代码演示如何声明逆变接口，以及如何将泛型约束用于其方法之一。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-127">The following code shows how to declare a contravariant interface and use a generic constraint for one of its methods.</span></span>

```vb
Interface IContravariant(Of In A)
    Sub SetSomething(ByVal sampleArg As A)
    Sub DoSomething(Of T As A)()
    ' The following statement generates a compiler error.
    ' Function GetSomething() As A
End Interface
```

<span data-ttu-id="8d2ae-128">此外，还可以在同一接口中同时支持协变和逆变，但需应用于不同的类型参数，如以下代码示例所示。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-128">It is also possible to support both covariance and contravariance in the same interface, but for different type parameters, as shown in the following code example.</span></span>

```vb
Interface IVariant(Of Out R, In A)
    Function GetSomething() As R
    Sub SetSomething(ByVal sampleArg As A)
    Function GetSetSomething(ByVal sampleArg As A) As R
End Interface
```

<span data-ttu-id="8d2ae-129">在 Visual Basic 中，如果不指定委托类型，则不能在变体接口中声明事件。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-129">In Visual Basic, you can't declare events in variant interfaces without specifying the delegate type.</span></span> <span data-ttu-id="8d2ae-130">此外，变体接口不能具有嵌套的类、枚举或结构，但它可以具有嵌套接口。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-130">Also, a variant interface can't have nested classes, enums, or structures, but it can have nested interfaces.</span></span> <span data-ttu-id="8d2ae-131">下面的代码阐释了这一点。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-131">This is illustrated in the following code.</span></span>

```vb
Interface ICovariant(Of Out R)
    ' The following statement generates a compiler error.
    ' Event SampleEvent()
    ' The following statement specifies the delegate type and
    ' does not generate an error.
    Event AnotherEvent As EventHandler

    ' The following statements generate compiler errors,
    ' because a variant interface cannot have
    ' nested enums, classes, or structures.

    'Enum SampleEnum : test : End Enum
    'Class SampleClass : End Class
    'Structure SampleStructure : Dim value As Integer : End Structure

    ' Variant interfaces can have nested interfaces.
    Interface INested : End Interface
End Interface
```

## <a name="implementing-variant-generic-interfaces"></a><span data-ttu-id="8d2ae-132">实现变体泛型接口</span><span class="sxs-lookup"><span data-stu-id="8d2ae-132">Implementing Variant Generic Interfaces</span></span>

<span data-ttu-id="8d2ae-133">在类中实现变体泛型接口时，所用语法和用于固定接口的语法相同。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-133">You implement variant generic interfaces in classes by using the same syntax that is used for invariant interfaces.</span></span> <span data-ttu-id="8d2ae-134">以下代码示例演示如何在泛型类中实现协变接口。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-134">The following code example shows how to implement a covariant interface in a generic class.</span></span>

```vb
Interface ICovariant(Of Out R)
    Function GetSomething() As R
End Interface

Class SampleImplementation(Of R)
    Implements ICovariant(Of R)
    Public Function GetSomething() As R _
    Implements ICovariant(Of R).GetSomething
        ' Some code.
    End Function
End Class
```

<span data-ttu-id="8d2ae-135">实现变体接口的类是固定类。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-135">Classes that implement variant interfaces are invariant.</span></span> <span data-ttu-id="8d2ae-136">例如，考虑下面的代码。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-136">For example, consider the following code.</span></span>

```vb
 The interface is covariant.
Dim ibutton As ICovariant(Of Button) =
    New SampleImplementation(Of Button)
Dim iobj As ICovariant(Of Object) = ibutton

' The class is invariant.
Dim button As SampleImplementation(Of Button) =
    New SampleImplementation(Of Button)
' The following statement generates a compiler error
' because classes are invariant.
' Dim obj As SampleImplementation(Of Object) = button
```

## <a name="extending-variant-generic-interfaces"></a><span data-ttu-id="8d2ae-137">扩展变体泛型接口</span><span class="sxs-lookup"><span data-stu-id="8d2ae-137">Extending Variant Generic Interfaces</span></span>

<span data-ttu-id="8d2ae-138">扩展变体泛型接口时，必须使用 `in` 和 `out` 关键字来显式指定派生接口是否支持变体。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-138">When you extend a variant generic interface, you have to use the `in` and `out` keywords to explicitly specify whether the derived interface supports variance.</span></span> <span data-ttu-id="8d2ae-139">编译器不会根据正在扩展的接口来推断变体。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-139">The compiler does not infer the variance from the interface that is being extended.</span></span> <span data-ttu-id="8d2ae-140">例如，考虑以下接口。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-140">For example, consider the following interfaces.</span></span>

```vb
Interface ICovariant(Of Out T)
End Interface

Interface IInvariant(Of T)
    Inherits ICovariant(Of T)
End Interface

Interface IExtCovariant(Of Out T)
    Inherits ICovariant(Of T)
End Interface
```

<span data-ttu-id="8d2ae-141">在 `Invariant(Of T)` 接口中，泛型类型参数 `T` 是固定的，而在 `IExtCovariant (Of Out T)` 类型参数中是协变的，尽管这两个接口都扩展了同一接口。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-141">In the `Invariant(Of T)` interface, the generic type parameter `T` is invariant, whereas in `IExtCovariant (Of Out T)`the type parameter is covariant, although both interfaces extend the same interface.</span></span> <span data-ttu-id="8d2ae-142">此规则也适用于逆变泛型类型参数。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-142">The same rule is applied to contravariant generic type parameters.</span></span>

<span data-ttu-id="8d2ae-143">无论泛型类型参数 `T` 在接口中是协变还是逆变，都可以创建一个接口来扩展这两类接口，只要在扩展接口中，该 `T` 泛型类型参数为固定参数。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-143">You can create an interface that extends both the interface where the generic type parameter `T` is covariant and the interface where it is contravariant if in the extending interface the generic type parameter `T` is invariant.</span></span> <span data-ttu-id="8d2ae-144">以下代码示例阐释了这一点。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-144">This is illustrated in the following code example.</span></span>

```vb
Interface ICovariant(Of Out T)
End Interface

Interface IContravariant(Of In T)
End Interface

Interface IInvariant(Of T)
    Inherits ICovariant(Of T), IContravariant(Of T)
End Interface
```

<span data-ttu-id="8d2ae-145">但是，如果泛型类型参数 `T` 在一个接口中声明为协变，则无法在扩展接口中将其声明为逆变，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-145">However, if a generic type parameter `T` is declared covariant in one interface, you cannot declare it contravariant in the extending interface, or vice versa.</span></span> <span data-ttu-id="8d2ae-146">以下代码示例阐释了这一点。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-146">This is illustrated in the following code example.</span></span>

```vb
Interface ICovariant(Of Out T)
End Interface

' The following statements generate a compiler error.
' Interface ICoContraVariant(Of In T)
'     Inherits ICovariant(Of T)
' End Interface
```

### <a name="avoiding-ambiguity"></a><span data-ttu-id="8d2ae-147">避免多义性</span><span class="sxs-lookup"><span data-stu-id="8d2ae-147">Avoiding Ambiguity</span></span>

<span data-ttu-id="8d2ae-148">实现变体泛型接口时，变体有时可能会导致多义性。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-148">When you implement variant generic interfaces, variance can sometimes lead to ambiguity.</span></span> <span data-ttu-id="8d2ae-149">应避免这种情况。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-149">This should be avoided.</span></span>

<span data-ttu-id="8d2ae-150">例如，如果在一个类中使用不同的泛型类型参数来显式实现同一变体泛型接口，便会产生多义性。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-150">For example, if you explicitly implement the same variant generic interface with different generic type parameters in one class, it can create ambiguity.</span></span> <span data-ttu-id="8d2ae-151">在这种情况下，编译器不会产生错误，但未指定将在运行时选择哪个接口实现。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-151">The compiler does not produce an error in this case, but it is not specified which interface implementation will be chosen at runtime.</span></span> <span data-ttu-id="8d2ae-152">这可能导致代码中出现微妙的 bug。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-152">This could lead to subtle bugs in your code.</span></span> <span data-ttu-id="8d2ae-153">请考虑以下代码示例。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-153">Consider the following code example.</span></span>

> [!NOTE]
> <span data-ttu-id="8d2ae-154">对于 `Option Strict Off` ，当存在不明确的接口实现时，Visual Basic 会生成编译器警告。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-154">With `Option Strict Off`, Visual Basic generates a compiler warning when there is an ambiguous interface implementation.</span></span> <span data-ttu-id="8d2ae-155">对于 `Option Strict On` ，Visual Basic 会生成编译器错误。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-155">With `Option Strict On`, Visual Basic generates a compiler error.</span></span>

```vb
' Simple class hierarchy.
Class Animal
End Class

Class Cat
    Inherits Animal
End Class

Class Dog
    Inherits Animal
End Class

' This class introduces ambiguity
' because IEnumerable(Of Out T) is covariant.
Class Pets
    Implements IEnumerable(Of Cat), IEnumerable(Of Dog)

    Public Function GetEnumerator() As IEnumerator(Of Cat) _
        Implements IEnumerable(Of Cat).GetEnumerator
        Console.WriteLine("Cat")
        ' Some code.
    End Function

    Public Function GetEnumerator1() As IEnumerator(Of Dog) _
        Implements IEnumerable(Of Dog).GetEnumerator
        Console.WriteLine("Dog")
        ' Some code.
    End Function

    Public Function GetEnumerator2() As IEnumerator _
        Implements IEnumerable.GetEnumerator
        ' Some code.
    End Function
End Class

Sub Main()
    Dim pets As IEnumerable(Of Animal) = New Pets()
    pets.GetEnumerator()
End Sub
```

<span data-ttu-id="8d2ae-156">在此示例中，没有指定 `pets.GetEnumerator` 方法如何在 `Cat` 和 `Dog` 之间选择。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-156">In this example, it is unspecified how the `pets.GetEnumerator` method chooses between `Cat` and `Dog`.</span></span> <span data-ttu-id="8d2ae-157">这可能导致代码中出现问题。</span><span class="sxs-lookup"><span data-stu-id="8d2ae-157">This could cause problems in your code.</span></span>

## <a name="see-also"></a><span data-ttu-id="8d2ae-158">请参阅</span><span class="sxs-lookup"><span data-stu-id="8d2ae-158">See also</span></span>

- [<span data-ttu-id="8d2ae-159">泛型接口中的变体 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8d2ae-159">Variance in Generic Interfaces (Visual Basic)</span></span>](variance-in-generic-interfaces.md)
- [<span data-ttu-id="8d2ae-160">对 Func 和 Action 泛型委托使用变体 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8d2ae-160">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](using-variance-for-func-and-action-generic-delegates.md)
