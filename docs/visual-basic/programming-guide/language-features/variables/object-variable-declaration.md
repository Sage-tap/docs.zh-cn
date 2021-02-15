---
description: '详细了解：对象变量声明 (Visual Basic) '
title: 对象变量声明
ms.date: 07/20/2015
helpviewer_keywords:
- early binding [Visual Basic]
- declarations [Visual Basic], class
- classes [Visual Basic], declaring
- binding [Visual Basic], late and early
- object variables [Visual Basic], declaring
- variables [Visual Basic], object
- declaring variables [Visual Basic], object variables
- declaring classes [Visual Basic]
- late binding [Visual Basic]
ms.assetid: 2a5a41a3-1aa8-4236-b1f0-2382af7bf715
ms.openlocfilehash: 853f9e775976022e52121c164884fd91ef0a831c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100463710"
---
# <a name="object-variable-declaration-visual-basic"></a><span data-ttu-id="6ef93-103">对象变量声明 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6ef93-103">Object Variable Declaration (Visual Basic)</span></span>

<span data-ttu-id="6ef93-104">使用 normal 声明语句声明对象变量。</span><span class="sxs-lookup"><span data-stu-id="6ef93-104">You use a normal declaration statement to declare an object variable.</span></span> <span data-ttu-id="6ef93-105">对于数据类型，指定 `Object` (，即 [对象数据类型](../../../language-reference/data-types/object-data-type.md)) 或要从中创建对象的更具体的类。</span><span class="sxs-lookup"><span data-stu-id="6ef93-105">For the data type, you specify either `Object` (that is, the [Object Data Type](../../../language-reference/data-types/object-data-type.md)) or a more specific class from which the object is to be created.</span></span>  
  
 <span data-ttu-id="6ef93-106">将变量声明为与 `Object` 将其声明为相同 <xref:System.Object?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="6ef93-106">Declaring a variable as `Object` is the same as declaring it as <xref:System.Object?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="6ef93-107">当使用特定的对象类声明变量时，它可以访问由此类及其继承的类公开的所有方法和属性。</span><span class="sxs-lookup"><span data-stu-id="6ef93-107">When you declare a variable with a specific object class, it can access all the methods and properties exposed by that class and the classes from which it inherits.</span></span> <span data-ttu-id="6ef93-108">如果使用声明变量 <xref:System.Object> ，则它只能访问类的成员 <xref:System.Object> ，除非你启用 `Option Strict Off` 后期绑定。</span><span class="sxs-lookup"><span data-stu-id="6ef93-108">If you declare the variable with <xref:System.Object>, it can access only the members of the <xref:System.Object> class, unless you turn `Option Strict Off` to allow late binding.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="6ef93-109">声明语法</span><span class="sxs-lookup"><span data-stu-id="6ef93-109">Declaration Syntax</span></span>  

 <span data-ttu-id="6ef93-110">使用以下语法声明对象变量：</span><span class="sxs-lookup"><span data-stu-id="6ef93-110">Use the following syntax to declare an object variable:</span></span>  
  
```vb  
Dim variablename As [New] { objectclass | Object }  
```  
  
 <span data-ttu-id="6ef93-111">你还可以在声明中指定 [Public](../../../language-reference/modifiers/public.md)、 [Protected](../../../language-reference/modifiers/protected.md)、 [Friend](../../../language-reference/modifiers/friend.md)、 `Protected Friend` 、 [Private](../../../language-reference/modifiers/private.md)、 [Shared](../../../language-reference/modifiers/shared.md)或 [Static](../../../language-reference/modifiers/static.md) 。</span><span class="sxs-lookup"><span data-stu-id="6ef93-111">You can also specify [Public](../../../language-reference/modifiers/public.md), [Protected](../../../language-reference/modifiers/protected.md), [Friend](../../../language-reference/modifiers/friend.md), `Protected Friend`, [Private](../../../language-reference/modifiers/private.md), [Shared](../../../language-reference/modifiers/shared.md), or [Static](../../../language-reference/modifiers/static.md) in the declaration.</span></span> <span data-ttu-id="6ef93-112">下面的示例声明是有效的：</span><span class="sxs-lookup"><span data-stu-id="6ef93-112">The following example declarations are valid:</span></span>  
  
```vb  
Private objA As Object  
Static objB As System.Windows.Forms.Label  
Dim objC As System.OperatingSystem  
```  
  
## <a name="late-binding-and-early-binding"></a><span data-ttu-id="6ef93-113">后期绑定和早期绑定</span><span class="sxs-lookup"><span data-stu-id="6ef93-113">Late Binding and Early Binding</span></span>  

 <span data-ttu-id="6ef93-114">有时，在代码运行之前，特定类是未知的。</span><span class="sxs-lookup"><span data-stu-id="6ef93-114">Sometimes the specific class is unknown until your code runs.</span></span> <span data-ttu-id="6ef93-115">在这种情况下，必须声明数据类型的对象变量 `Object` 。</span><span class="sxs-lookup"><span data-stu-id="6ef93-115">In this case, you must declare the object variable with the `Object` data type.</span></span> <span data-ttu-id="6ef93-116">这会创建对任何类型的对象的常规引用，并在运行时分配特定类。</span><span class="sxs-lookup"><span data-stu-id="6ef93-116">This creates a general reference to any type of object, and the specific class is assigned at run time.</span></span> <span data-ttu-id="6ef93-117">这称为 *后期绑定*。</span><span class="sxs-lookup"><span data-stu-id="6ef93-117">This is called *late binding*.</span></span> <span data-ttu-id="6ef93-118">后期绑定需要额外的执行时间。</span><span class="sxs-lookup"><span data-stu-id="6ef93-118">Late binding requires additional execution time.</span></span> <span data-ttu-id="6ef93-119">它还将代码限制为最近分配给它的类的方法和属性。</span><span class="sxs-lookup"><span data-stu-id="6ef93-119">It also limits your code to the methods and properties of the class you have most recently assigned to it.</span></span> <span data-ttu-id="6ef93-120">如果你的代码尝试访问不同类的成员，这可能会导致运行时错误。</span><span class="sxs-lookup"><span data-stu-id="6ef93-120">This can cause run-time errors if your code attempts to access members of a different class.</span></span>  
  
 <span data-ttu-id="6ef93-121">如果在编译时知道特定类，则应将对象变量声明为该类的。</span><span class="sxs-lookup"><span data-stu-id="6ef93-121">When you know the specific class at compile time, you should declare the object variable to be of that class.</span></span> <span data-ttu-id="6ef93-122">这称为 *早期绑定*。</span><span class="sxs-lookup"><span data-stu-id="6ef93-122">This is called *early binding*.</span></span> <span data-ttu-id="6ef93-123">早期绑定可提高性能，并保证代码访问特定类的所有方法和属性。</span><span class="sxs-lookup"><span data-stu-id="6ef93-123">Early binding improves performance and guarantees your code access to all the methods and properties of the specific class.</span></span> <span data-ttu-id="6ef93-124">在前面的示例声明中，如果变量 `objA` 仅使用类的对象 <xref:System.Windows.Forms.Label?displayProperty=nameWithType> ，则应 `As System.Windows.Forms.Label` 在其声明中指定。</span><span class="sxs-lookup"><span data-stu-id="6ef93-124">In the preceding example declarations, if variable `objA` uses only objects of class <xref:System.Windows.Forms.Label?displayProperty=nameWithType>, you should specify `As System.Windows.Forms.Label` in its declaration.</span></span>  
  
### <a name="advantages-of-early-binding"></a><span data-ttu-id="6ef93-125">早期绑定的优点</span><span class="sxs-lookup"><span data-stu-id="6ef93-125">Advantages of Early Binding</span></span>  

 <span data-ttu-id="6ef93-126">将对象变量声明为特定类具有以下优势：</span><span class="sxs-lookup"><span data-stu-id="6ef93-126">Declaring an object variable as a specific class gives you several advantages:</span></span>  
  
- <span data-ttu-id="6ef93-127">自动类型检查</span><span class="sxs-lookup"><span data-stu-id="6ef93-127">Automatic type checking</span></span>  
  
- <span data-ttu-id="6ef93-128">保证能够访问特定类的所有成员</span><span class="sxs-lookup"><span data-stu-id="6ef93-128">Guaranteed access to all members of the specific class</span></span>  
  
- <span data-ttu-id="6ef93-129">代码编辑器中的 Microsoft IntelliSense 支持</span><span class="sxs-lookup"><span data-stu-id="6ef93-129">Microsoft IntelliSense support in the Code Editor</span></span>  
  
- <span data-ttu-id="6ef93-130">提高代码的可读性</span><span class="sxs-lookup"><span data-stu-id="6ef93-130">Improved readability of your code</span></span>  
  
- <span data-ttu-id="6ef93-131">代码中的错误越少</span><span class="sxs-lookup"><span data-stu-id="6ef93-131">Fewer errors in your code</span></span>  
  
- <span data-ttu-id="6ef93-132">在编译时（而非运行时）捕获的错误</span><span class="sxs-lookup"><span data-stu-id="6ef93-132">Errors caught at compile time rather than run time</span></span>  
  
- <span data-ttu-id="6ef93-133">更快的代码执行</span><span class="sxs-lookup"><span data-stu-id="6ef93-133">Faster code execution</span></span>  
  
## <a name="access-to-object-variable-members"></a><span data-ttu-id="6ef93-134">对对象变量成员的访问</span><span class="sxs-lookup"><span data-stu-id="6ef93-134">Access to Object Variable Members</span></span>  

 <span data-ttu-id="6ef93-135">当 `Option Strict` 启用时 `On` ，对象变量仅可访问声明它所用的类的方法和属性。</span><span class="sxs-lookup"><span data-stu-id="6ef93-135">When `Option Strict` is turned `On`, an object variable can access only the methods and properties of the class with which you declare it.</span></span> <span data-ttu-id="6ef93-136">下面的示例对此进行了演示。</span><span class="sxs-lookup"><span data-stu-id="6ef93-136">The following example illustrates this.</span></span>  
  
```vb  
' Option statements must precede all other source file lines.  
Option Strict On  
' Imports statement must precede all declarations in the source file.  
Imports System.Windows.Forms  
Public Sub accessMembers()  
    Dim p As Object  
    Dim q As System.Windows.Forms.Label  
    p = New System.Windows.Forms.Label  
    q = New System.Windows.Forms.Label  
    Dim j, k As Integer  
    ' The following statement generates a compiler ERROR.  
    j = p.Left  
    ' The following statement retrieves the left edge of the label in pixels.  
    k = q.Left  
End Sub  
```  
  
 <span data-ttu-id="6ef93-137">在此示例中， `p` 仅可使用 <xref:System.Object> 类的成员，这不包括 `Left` 属性。</span><span class="sxs-lookup"><span data-stu-id="6ef93-137">In this example, `p` can use only the members of the <xref:System.Object> class itself, which do not include the `Left` property.</span></span> <span data-ttu-id="6ef93-138">另一方面， `q` 已声明为 <xref:System.Windows.Forms.Label>类型，因此它可以使用 <xref:System.Windows.Forms.Label> 命名空间中 <xref:System.Windows.Forms> 类的所有方法和属性。</span><span class="sxs-lookup"><span data-stu-id="6ef93-138">On the other hand, `q` was declared to be of type <xref:System.Windows.Forms.Label>, so it can use all the methods and properties of the <xref:System.Windows.Forms.Label> class in the <xref:System.Windows.Forms> namespace.</span></span>  
  
## <a name="flexibility-of-object-variables"></a><span data-ttu-id="6ef93-139">对象变量的灵活性</span><span class="sxs-lookup"><span data-stu-id="6ef93-139">Flexibility of Object Variables</span></span>  

 <span data-ttu-id="6ef93-140">使用继承层次结构中的对象时，可以选择使用哪个类来声明对象变量。</span><span class="sxs-lookup"><span data-stu-id="6ef93-140">When working with objects in an inheritance hierarchy, you have a choice of which class to use for declaring your object variables.</span></span> <span data-ttu-id="6ef93-141">在做出此选择的过程中，必须在对象赋值的灵活性与对类成员的访问之间取得平衡。</span><span class="sxs-lookup"><span data-stu-id="6ef93-141">In making this choice, you must balance flexibility of object assignment against access to members of a class.</span></span> <span data-ttu-id="6ef93-142">例如，请考虑导致类的继承层次结构 <xref:System.Windows.Forms.Form?displayProperty=nameWithType> ：</span><span class="sxs-lookup"><span data-stu-id="6ef93-142">For example, consider the inheritance hierarchy that leads to the <xref:System.Windows.Forms.Form?displayProperty=nameWithType> class:</span></span>  
  
 <xref:System.Object>  
  
 &nbsp;&nbsp;<xref:System.MarshalByRefObject>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;<xref:System.ComponentModel.Component>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Control>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ScrollableControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ContainerControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Form>  
  
 <span data-ttu-id="6ef93-143">假设你的应用程序定义了一个名为的窗体类 `specialForm` ，该类继承自类 <xref:System.Windows.Forms.Form> 。</span><span class="sxs-lookup"><span data-stu-id="6ef93-143">Suppose your application defines a form class called `specialForm`, which inherits from class <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="6ef93-144">您可以声明一个专门引用的对象变量 `specialForm` ，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="6ef93-144">You can declare an object variable that refers specifically to `specialForm`, as the following example shows.</span></span>  
  
```vb  
Public Class specialForm  
    Inherits System.Windows.Forms.Form  
    ' Insert code defining methods and properties of specialForm.  
End Class  
Dim nextForm As New specialForm  
```  
  
 <span data-ttu-id="6ef93-145">前面的示例中的声明将变量限制 `nextForm` 为类的对象 `specialForm` ，但它还使可用于的所有方法和属性，以及继承的所有类的所有 `specialForm` `nextForm` 成员 `specialForm` 。</span><span class="sxs-lookup"><span data-stu-id="6ef93-145">The declaration in the preceding example limits the variable `nextForm` to objects of class `specialForm`, but it also makes all the methods and properties of `specialForm` available to `nextForm`, as well as all the members of all the classes from which `specialForm` inherits.</span></span>  
  
 <span data-ttu-id="6ef93-146">可以通过将对象变量声明为类型来使对象变量更通用 <xref:System.Windows.Forms.Form> ，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="6ef93-146">You can make an object variable more general by declaring it to be of type <xref:System.Windows.Forms.Form>, as the following example shows.</span></span>  
  
```vb  
Dim anyForm As System.Windows.Forms.Form  
```  
  
 <span data-ttu-id="6ef93-147">前面的示例中的声明使你可以将应用程序中的任何表单分配给 `anyForm` 。</span><span class="sxs-lookup"><span data-stu-id="6ef93-147">The declaration in the preceding example lets you assign any form in your application to `anyForm`.</span></span> <span data-ttu-id="6ef93-148">但是，虽然 `anyForm` 可以访问类的所有成员 <xref:System.Windows.Forms.Form> ，但它不能使用为特定窗体定义的任何其他方法或属性（如） `specialForm` 。</span><span class="sxs-lookup"><span data-stu-id="6ef93-148">However, although `anyForm` can access all the members of class <xref:System.Windows.Forms.Form>, it cannot use any of the additional methods or properties defined for specific forms such as `specialForm`.</span></span>  
  
 <span data-ttu-id="6ef93-149">基类的所有成员均可用于派生类，但派生类的其他成员对基类不可用。</span><span class="sxs-lookup"><span data-stu-id="6ef93-149">All the members of a base class are available to derived classes, but the additional members of a derived class are unavailable to the base class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ef93-150">请参阅</span><span class="sxs-lookup"><span data-stu-id="6ef93-150">See also</span></span>

- [<span data-ttu-id="6ef93-151">对象变量</span><span class="sxs-lookup"><span data-stu-id="6ef93-151">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="6ef93-152">对象变量赋值</span><span class="sxs-lookup"><span data-stu-id="6ef93-152">Object Variable Assignment</span></span>](object-variable-assignment.md)
- [<span data-ttu-id="6ef93-153">对象变量值</span><span class="sxs-lookup"><span data-stu-id="6ef93-153">Object Variable Values</span></span>](object-variable-values.md)
- [<span data-ttu-id="6ef93-154">如何：在 Visual Basic 中声明对象变量并为它分配对象</span><span class="sxs-lookup"><span data-stu-id="6ef93-154">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>](how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [<span data-ttu-id="6ef93-155">如何：访问对象的成员</span><span class="sxs-lookup"><span data-stu-id="6ef93-155">How to: Access Members of an Object</span></span>](how-to-access-members-of-an-object.md)
- [<span data-ttu-id="6ef93-156">新建操作员</span><span class="sxs-lookup"><span data-stu-id="6ef93-156">New Operator</span></span>](../../../language-reference/operators/new-operator.md)
- [<span data-ttu-id="6ef93-157">Option Strict 语句</span><span class="sxs-lookup"><span data-stu-id="6ef93-157">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="6ef93-158">局部类型推理</span><span class="sxs-lookup"><span data-stu-id="6ef93-158">Local Type Inference</span></span>](local-type-inference.md)
