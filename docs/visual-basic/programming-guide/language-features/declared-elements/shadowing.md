---
description: 了解详细信息： Visual Basic 中隐藏
title: 阴影操作
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], shadowing
- overriding, and shadowing
- shadowing
- duplicate names [Visual Basic]
- shadowing, by inheritance
- declared elements [Visual Basic], referencing
- shadowing, by scope
- declared elements [Visual Basic], hiding
- naming conflicts, shadowing
- declared elements [Visual Basic], shadowing
- shadowing, and overriding
- scope [Visual Basic], shadowing
- Shadows keyword [Visual Basic], about
- objects [Visual Basic], names
- names [Visual Basic], shadowing
ms.assetid: 54bb4c25-12c4-4181-b4a0-93546053964e
ms.openlocfilehash: 468ad72808d689016cacb8d2be56fa9f9fcd1eec
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100434818"
---
# <a name="shadowing-in-visual-basic"></a><span data-ttu-id="f3e8f-103">Visual Basic 中的隐藏</span><span class="sxs-lookup"><span data-stu-id="f3e8f-103">Shadowing in Visual Basic</span></span>

<span data-ttu-id="f3e8f-104">当两个编程元素共享同一名称时，其中一个元素可以 *隐藏或隐藏* 另一个。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-104">When two programming elements share the same name, one of them can hide, or *shadow*, the other one.</span></span> <span data-ttu-id="f3e8f-105">在这种情况下，隐藏的元素不可用于引用;相反，当你的代码使用元素名称时，Visual Basic 编译器会将其解析为隐藏元素。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-105">In such a situation, the shadowed element is not available for reference; instead, when your code uses the element name, the Visual Basic compiler resolves it to the shadowing element.</span></span>  
  
## <a name="purpose"></a><span data-ttu-id="f3e8f-106">目的</span><span class="sxs-lookup"><span data-stu-id="f3e8f-106">Purpose</span></span>  

 <span data-ttu-id="f3e8f-107">隐藏的主要目的是保护类成员的定义。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-107">The main purpose of shadowing is to protect the definition of your class members.</span></span> <span data-ttu-id="f3e8f-108">基类可能会发生更改，该更改将创建一个与已定义的元素同名的元素。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-108">The base class might undergo a change that creates an element with the same name as one you have already defined.</span></span> <span data-ttu-id="f3e8f-109">如果发生这种情况， `Shadows` 修饰符会强制通过类的引用解析为你定义的成员而不是新的基类元素。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-109">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span></span>  
  
## <a name="types-of-shadowing"></a><span data-ttu-id="f3e8f-110">隐藏类型</span><span class="sxs-lookup"><span data-stu-id="f3e8f-110">Types of Shadowing</span></span>  

 <span data-ttu-id="f3e8f-111">元素可通过两种不同的方式隐藏其他元素。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-111">An element can shadow another element in two different ways.</span></span> <span data-ttu-id="f3e8f-112">可以在包含隐藏元素的区域的子区域内声明隐藏元素，在这种情况下，隐藏是 *通过范围* 实现的。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-112">The shadowing element can be declared inside a subregion of the region containing the shadowed element, in which case the shadowing is accomplished *through scope*.</span></span> <span data-ttu-id="f3e8f-113">或派生类可以重新定义基类的成员，在这种情况下，将 *通过继承* 来完成隐藏。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-113">Or a deriving class can redefine a member of a base class, in which case the shadowing is done *through inheritance*.</span></span>  
  
### <a name="shadowing-through-scope"></a><span data-ttu-id="f3e8f-114">通过范围隐藏</span><span class="sxs-lookup"><span data-stu-id="f3e8f-114">Shadowing Through Scope</span></span>  

 <span data-ttu-id="f3e8f-115">同一模块、类或结构中的编程元素可以具有相同的名称，但范围不同。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-115">It is possible for programming elements in the same module, class, or structure to have the same name but different scope.</span></span> <span data-ttu-id="f3e8f-116">如果以这种方式声明了两个元素，而代码引用了它们共享的名称，则范围较窄的元素隐藏其他元素 (块范围是最窄的) 。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-116">When two elements are declared in this manner and the code refers to the name they share, the element with the narrower scope shadows the other element (block scope is the narrowest).</span></span>  
  
 <span data-ttu-id="f3e8f-117">例如，模块可以定义一个 `Public` 名为的变量 `temp` ，并且该模块中的一个过程可以声明同样名为的局部变量 `temp` 。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-117">For example, a module can define a `Public` variable named `temp`, and a procedure within the module can declare a local variable also named `temp`.</span></span> <span data-ttu-id="f3e8f-118">对中的的引用 `temp` 访问本地变量，而 `temp` 从该过程外部引用将访问该 `Public` 变量。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-118">References to `temp` from within the procedure access the local variable, while references to `temp` from outside the procedure access the `Public` variable.</span></span> <span data-ttu-id="f3e8f-119">在这种情况下，过程变量 `temp` 隐藏了模块变量 `temp` 。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-119">In this case, the procedure variable `temp` shadows the module variable `temp`.</span></span>  
  
 <span data-ttu-id="f3e8f-120">下图显示了两个名为 `temp` 的变量。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-120">The following illustration shows two variables, both named `temp`.</span></span> <span data-ttu-id="f3e8f-121">局部变量在 `temp` `temp` 从其自己的过程中被访问时隐藏了成员变量 `p` 。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-121">The local variable `temp` shadows the member variable `temp` when accessed from within its own procedure `p`.</span></span> <span data-ttu-id="f3e8f-122">不过， `MyClass` 关键字会绕过隐藏并访问成员变量。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-122">However, the `MyClass` keyword bypasses the shadowing and accesses the member variable.</span></span>  
  
 ![显示通过范围隐藏的图形。](./media/shadowing/shadow-scope-diagram.gif)
  
 <span data-ttu-id="f3e8f-124">有关通过范围进行隐藏的示例，请参阅 [如何：隐藏与您的变量](how-to-hide-a-variable-with-the-same-name-as-your-variable.md)同名的变量。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-124">For an example of shadowing through scope, see [How to: Hide a Variable with the Same Name as Your Variable](how-to-hide-a-variable-with-the-same-name-as-your-variable.md).</span></span>  
  
### <a name="shadowing-through-inheritance"></a><span data-ttu-id="f3e8f-125">通过继承隐藏</span><span class="sxs-lookup"><span data-stu-id="f3e8f-125">Shadowing Through Inheritance</span></span>  

 <span data-ttu-id="f3e8f-126">如果派生类重定义了从基类继承的编程元素，则重定义元素将隐藏原始元素。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-126">If a derived class redefines a programming element inherited from a base class, the redefining element shadows the original element.</span></span> <span data-ttu-id="f3e8f-127">可以用任何其他类型隐藏任何类型的已声明元素或重载元素集。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-127">You can shadow any type of declared element, or set of overloaded elements, with any other type.</span></span> <span data-ttu-id="f3e8f-128">例如， `Integer` 变量可以隐藏 `Function` 过程。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-128">For example, an `Integer` variable can shadow a `Function` procedure.</span></span> <span data-ttu-id="f3e8f-129">如果使用另一个过程来隐藏过程，则可以使用不同的参数列表和不同的返回类型。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-129">If you shadow a procedure with another procedure, you can use a different parameter list and a different return type.</span></span>  
  
 <span data-ttu-id="f3e8f-130">下图显示了 `b` 继承自的基类和派生类 `d` `b` 。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-130">The following illustration shows a base class `b` and a derived class `d` that inherits from `b`.</span></span> <span data-ttu-id="f3e8f-131">基类定义了一个名为的过程 `proc` ，派生类将使用另一个同名的过程来隐藏该过程。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-131">The base class defines a procedure named `proc`, and the derived class shadows it with another procedure of the same name.</span></span> <span data-ttu-id="f3e8f-132">第一 `Call` 条语句访问 `proc` 派生类中的隐藏。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-132">The first `Call` statement accesses the shadowing `proc` in the derived class.</span></span> <span data-ttu-id="f3e8f-133">不过， `MyBase` 关键字会绕过隐藏并访问基类中的隐藏过程。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-133">However, the `MyBase` keyword bypasses the shadowing and accesses the shadowed procedure in the base class.</span></span>  
  
 ![通过继承进行隐藏示意图](./media/shadowing/shadowing-inherit-diagram.gif)  
  
 <span data-ttu-id="f3e8f-135">有关通过继承进行隐藏的示例，请参阅 [如何：隐藏与您的变量](how-to-hide-a-variable-with-the-same-name-as-your-variable.md) 同名的变量和 [如何：隐藏继承的变量](how-to-hide-an-inherited-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-135">For an example of shadowing through inheritance, see [How to: Hide a Variable with the Same Name as Your Variable](how-to-hide-a-variable-with-the-same-name-as-your-variable.md) and [How to: Hide an Inherited Variable](how-to-hide-an-inherited-variable.md).</span></span>  
  
#### <a name="shadowing-and-access-level"></a><span data-ttu-id="f3e8f-136">隐藏和访问级别</span><span class="sxs-lookup"><span data-stu-id="f3e8f-136">Shadowing and Access Level</span></span>  

 <span data-ttu-id="f3e8f-137">不能始终使用派生类从代码访问隐藏元素。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-137">The shadowing element is not always accessible from the code using the derived class.</span></span> <span data-ttu-id="f3e8f-138">例如，它可能是声明的 `Private` 。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-138">For example, it might be declared `Private`.</span></span> <span data-ttu-id="f3e8f-139">在这种情况下，隐藏会失效，如果没有隐藏，编译器将解析对同一元素的任何引用。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-139">In such a case, shadowing is defeated and the compiler resolves any reference to the same element it would have if there had been no shadowing.</span></span> <span data-ttu-id="f3e8f-140">此元素是可访问的元素，它是从隐藏类向后 derivational 的最少步骤。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-140">This element is the accessible element the fewest derivational steps backward from the shadowing class.</span></span> <span data-ttu-id="f3e8f-141">如果隐藏的元素是一个过程，则将其解析为具有相同名称、参数列表和返回类型的最接近的可访问版本。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-141">If the shadowed element is a procedure, the resolution is to the closest accessible version with the same name, parameter list, and return type.</span></span>  
  
 <span data-ttu-id="f3e8f-142">下面的示例显示了三个类的继承层次结构。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-142">The following example shows an inheritance hierarchy of three classes.</span></span> <span data-ttu-id="f3e8f-143">每个类都定义一个 `Sub` 过程 `display` ，并且每个派生类都会 `display` 在其基类中隐藏该过程。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-143">Each class defines a `Sub` procedure `display`, and each derived class shadows the `display` procedure in its base class.</span></span>  
  
```vb  
Public Class firstClass  
    Public Sub display()  
        MsgBox("This is firstClass")  
    End Sub  
End Class  
Public Class secondClass  
    Inherits firstClass  
    Private Shadows Sub display()  
        MsgBox("This is secondClass")  
    End Sub  
End Class  
Public Class thirdClass  
    Inherits secondClass  
    Public Shadows Sub display()  
        MsgBox("This is thirdClass")  
    End Sub  
End Class  
Module callDisplay  
    Dim first As New firstClass  
    Dim second As New secondClass  
    Dim third As New thirdClass  
    Public Sub callDisplayProcedures()  
        ' The following statement displays "This is firstClass".  
        first.display()  
        ' The following statement displays "This is firstClass".  
        second.display()  
        ' The following statement displays "This is thirdClass".  
        third.display()  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="f3e8f-144">在前面的示例中，派生类 `secondClass` `display` 具有一个 `Private` 过程。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-144">In the preceding example, the derived class `secondClass` shadows `display` with a `Private` procedure.</span></span> <span data-ttu-id="f3e8f-145">当模块 `callDisplay` `display` 在中调用时 `secondClass` ，调用代码在外部， `secondClass` 因此无法访问私有 `display` 过程。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-145">When module `callDisplay` calls `display` in `secondClass`, the calling code is outside `secondClass` and therefore cannot access the private `display` procedure.</span></span> <span data-ttu-id="f3e8f-146">隐藏操作已失效，编译器将引用解析为基类 `display` 过程。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-146">Shadowing is defeated, and the compiler resolves the reference to the base class `display` procedure.</span></span>  
  
 <span data-ttu-id="f3e8f-147">但是，进一步的派生类 `thirdClass` 声明 `display` 为 `Public` ，因此中的代码 `callDisplay` 可以访问它。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-147">However, the further derived class `thirdClass` declares `display` as `Public`, so the code in `callDisplay` can access it.</span></span>  
  
## <a name="shadowing-and-overriding"></a><span data-ttu-id="f3e8f-148">隐藏和重写</span><span class="sxs-lookup"><span data-stu-id="f3e8f-148">Shadowing and Overriding</span></span>  

 <span data-ttu-id="f3e8f-149">不要将隐藏与重写混淆。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-149">Do not confuse shadowing with overriding.</span></span> <span data-ttu-id="f3e8f-150">当派生类从基类继承时，同时使用这两种方法，并将一个声明的元素重定义为另一个。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-150">Both are used when a derived class inherits from a base class, and both redefine one declared element with another.</span></span> <span data-ttu-id="f3e8f-151">但两者之间存在重大差异。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-151">But there are significant differences between the two.</span></span> <span data-ttu-id="f3e8f-152">有关比较，请参阅 [隐藏和重写之间的差异](differences-between-shadowing-and-overriding.md)。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-152">For a comparison, see [Differences Between Shadowing and Overriding](differences-between-shadowing-and-overriding.md).</span></span>  
  
## <a name="shadowing-and-overloading"></a><span data-ttu-id="f3e8f-153">隐藏和重载</span><span class="sxs-lookup"><span data-stu-id="f3e8f-153">Shadowing and Overloading</span></span>  

 <span data-ttu-id="f3e8f-154">如果在派生类中隐藏具有多个元素的同一个基类元素，则隐藏元素将成为该元素的重载版本。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-154">If you shadow the same base class element with more than one element in your derived class, the shadowing elements become overloaded versions of that element.</span></span> <span data-ttu-id="f3e8f-155">有关更多信息，请参见 [Procedure Overloading](../procedures/procedure-overloading.md)。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-155">For more information, see [Procedure Overloading](../procedures/procedure-overloading.md).</span></span>  
  
## <a name="accessing-a-shadowed-element"></a><span data-ttu-id="f3e8f-156">访问隐藏的元素</span><span class="sxs-lookup"><span data-stu-id="f3e8f-156">Accessing a Shadowed Element</span></span>  

 <span data-ttu-id="f3e8f-157">从派生类访问某个元素时，通常通过该派生类的当前实例执行此操作，方法是使用关键字限定元素名称 `Me` 。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-157">When you access an element from a derived class, you normally do so through the current instance of that derived class, by qualifying the element name with the `Me` keyword.</span></span> <span data-ttu-id="f3e8f-158">如果派生类隐藏了基类中的元素，则可以通过使用关键字限定基类元素来访问它 `MyBase` 。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-158">If your derived class shadows the element in the base class, you can access the base class element by qualifying it with the `MyBase` keyword.</span></span>  
  
 <span data-ttu-id="f3e8f-159">有关访问隐藏的元素的示例，请参阅 [如何：访问由派生类隐藏的变量](how-to-access-a-variable-hidden-by-a-derived-class.md)。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-159">For an example of accessing a shadowed element, see [How to: Access a Variable Hidden by a Derived Class](how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>  
  
### <a name="declaration-of-the-object-variable"></a><span data-ttu-id="f3e8f-160">对象变量的声明</span><span class="sxs-lookup"><span data-stu-id="f3e8f-160">Declaration of the Object Variable</span></span>  

 <span data-ttu-id="f3e8f-161">创建对象变量的方式还会影响派生类是访问隐藏元素还是访问隐藏的元素。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-161">How you create the object variable can also affect whether the derived class accesses a shadowing element or the shadowed element.</span></span> <span data-ttu-id="f3e8f-162">下面的示例从派生类创建两个对象，但一个对象声明为基类，另一个对象作为派生类。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-162">The following example creates two objects from a derived class, but one object is declared as the base class and the other as the derived class.</span></span>  
  
```vb  
Public Class baseCls  
    ' The following statement declares the element that is to be shadowed.  
    Public z As Integer = 100  
End Class  
Public Class dervCls  
    Inherits baseCls  
    ' The following statement declares the shadowing element.  
    Public Shadows z As String = "*"  
End Class  
Public Class useClasses  
    ' The following statement creates the object declared as the base class.  
    Dim basObj As baseCls = New dervCls()  
    ' Note that dervCls widens to its base class baseCls.  
    ' The following statement creates the object declared as the derived class.  
    Dim derObj As dervCls = New dervCls()  
    Public Sub showZ()
    ' The following statement outputs 100 (the shadowed element).  
        MsgBox("Accessed through base class: " & basObj.z)  
    ' The following statement outputs "*" (the shadowing element).  
        MsgBox("Accessed through derived class: " & derObj.z)  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="f3e8f-163">在前面的示例中，变量 `basObj` 被声明为基类。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-163">In the preceding example, the variable `basObj` is declared as the base class.</span></span> <span data-ttu-id="f3e8f-164">`dervCls`为对象分配对象将形成扩大转换，因此有效。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-164">Assigning a `dervCls` object to it constitutes a widening conversion and is therefore valid.</span></span> <span data-ttu-id="f3e8f-165">但是，基类无法访问派生类中的变量的隐藏版本 `z` ，因此编译器解析 `basObj.z` 为原始基类值。</span><span class="sxs-lookup"><span data-stu-id="f3e8f-165">However, the base class cannot access the shadowing version of the variable `z` in the derived class, so the compiler resolves `basObj.z` to the original base class value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3e8f-166">请参阅</span><span class="sxs-lookup"><span data-stu-id="f3e8f-166">See also</span></span>

- [<span data-ttu-id="f3e8f-167">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="f3e8f-167">References to Declared Elements</span></span>](references-to-declared-elements.md)
- [<span data-ttu-id="f3e8f-168">Visual Basic 中的范围</span><span class="sxs-lookup"><span data-stu-id="f3e8f-168">Scope in Visual Basic</span></span>](scope.md)
- [<span data-ttu-id="f3e8f-169">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="f3e8f-169">Widening and Narrowing Conversions</span></span>](../data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="f3e8f-170">Shadows</span><span class="sxs-lookup"><span data-stu-id="f3e8f-170">Shadows</span></span>](../../../language-reference/modifiers/shadows.md)
- [<span data-ttu-id="f3e8f-171">替代</span><span class="sxs-lookup"><span data-stu-id="f3e8f-171">Overrides</span></span>](../../../language-reference/modifiers/overrides.md)
- [<span data-ttu-id="f3e8f-172">Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="f3e8f-172">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="f3e8f-173">继承基础知识</span><span class="sxs-lookup"><span data-stu-id="f3e8f-173">Inheritance Basics</span></span>](../objects-and-classes/inheritance-basics.md)
