---
description: 详细了解：中的对象和类 Visual Basic
title: 对象和类
ms.date: 05/26/2020
helpviewer_keywords:
- classes [Visual Basic]
- objects [Visual Basic]
ms.assetid: c68c5752-1006-46e1-975a-6717b62a42fc
ms.openlocfilehash: 9cefcc117c9dd4ac42940f342dbf75d8ddb4f41d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100462719"
---
# <a name="objects-and-classes-in-visual-basic"></a><span data-ttu-id="24b4c-103">Visual Basic 中的对象和类</span><span class="sxs-lookup"><span data-stu-id="24b4c-103">Objects and classes in Visual Basic</span></span>

<span data-ttu-id="24b4c-104">*对象* 结合了可以视为一个单元的代码和数据。</span><span class="sxs-lookup"><span data-stu-id="24b4c-104">An *object* is a combination of code and data that can be treated as a unit.</span></span> <span data-ttu-id="24b4c-105">对象可以是应用程序的一部分（如控件或窗体），</span><span class="sxs-lookup"><span data-stu-id="24b4c-105">An object can be a piece of an application, like a control or a form.</span></span> <span data-ttu-id="24b4c-106">也可以是整个应用程序。</span><span class="sxs-lookup"><span data-stu-id="24b4c-106">An entire application can also be an object.</span></span>

<span data-ttu-id="24b4c-107">在 Visual Basic 中创建应用程序时，会不断地处理对象。</span><span class="sxs-lookup"><span data-stu-id="24b4c-107">When you create an application in Visual Basic, you constantly work with objects.</span></span> <span data-ttu-id="24b4c-108">您可以使用 Visual Basic 提供的对象，例如控件、窗体和数据访问对象。</span><span class="sxs-lookup"><span data-stu-id="24b4c-108">You can use objects provided by Visual Basic, such as controls, forms, and data access objects.</span></span> <span data-ttu-id="24b4c-109">你还可以使用 Visual Basic 应用程序中的其他应用程序的对象。</span><span class="sxs-lookup"><span data-stu-id="24b4c-109">You can also use objects from other applications within your Visual Basic application.</span></span> <span data-ttu-id="24b4c-110">甚至可以创建你自己的对象，并为它们定义附加属性和方法。</span><span class="sxs-lookup"><span data-stu-id="24b4c-110">You can even create your own objects and define additional properties and methods for them.</span></span> <span data-ttu-id="24b4c-111">对象类似于程序的预制构建基块，可方便你编写一次代码片段，然后不断重用它。</span><span class="sxs-lookup"><span data-stu-id="24b4c-111">Objects act like prefabricated building blocks for programs — they let you write a piece of code once and reuse it over and over.</span></span>

<span data-ttu-id="24b4c-112">此主题详细介绍了对象。</span><span class="sxs-lookup"><span data-stu-id="24b4c-112">This topic discusses objects in detail.</span></span>

## <a name="objects-and-classes"></a><span data-ttu-id="24b4c-113">对象和类</span><span class="sxs-lookup"><span data-stu-id="24b4c-113">Objects and classes</span></span>

<span data-ttu-id="24b4c-114">Visual Basic 中的每个对象都由一个 *类* 定义。</span><span class="sxs-lookup"><span data-stu-id="24b4c-114">Each object in Visual Basic is defined by a *class*.</span></span> <span data-ttu-id="24b4c-115">类描述了对象的变量、属性、过程和事件。</span><span class="sxs-lookup"><span data-stu-id="24b4c-115">A class describes the variables, properties, procedures, and events of an object.</span></span> <span data-ttu-id="24b4c-116">对象是类实例；定义类之后，便可以根据需要创建任意多个对象。</span><span class="sxs-lookup"><span data-stu-id="24b4c-116">Objects are instances of classes; you can create as many objects you need once you have defined a class.</span></span>

<span data-ttu-id="24b4c-117">想想饼干切模和饼干，即可理解对象与其类之间的关系。</span><span class="sxs-lookup"><span data-stu-id="24b4c-117">To understand the relationship between an object and its class, think of cookie cutters and cookies.</span></span> <span data-ttu-id="24b4c-118">饼干切模是类。</span><span class="sxs-lookup"><span data-stu-id="24b4c-118">The cookie cutter is the class.</span></span> <span data-ttu-id="24b4c-119">它定义了每个饼干的特征，例如大小和形状。</span><span class="sxs-lookup"><span data-stu-id="24b4c-119">It defines the characteristics of each cookie, for example size and shape.</span></span> <span data-ttu-id="24b4c-120">类用于创建对象。</span><span class="sxs-lookup"><span data-stu-id="24b4c-120">The class is used to create objects.</span></span> <span data-ttu-id="24b4c-121">对象是饼干。</span><span class="sxs-lookup"><span data-stu-id="24b4c-121">The objects are the cookies.</span></span>

<span data-ttu-id="24b4c-122">必须先创建对象，然后才能访问其成员，但可以访问的成员除外， [`Shared`](../../../language-reference/modifiers/shared.md) 无需使用类的对象。</span><span class="sxs-lookup"><span data-stu-id="24b4c-122">You must create an object before you can access its members, except for [`Shared`](../../../language-reference/modifiers/shared.md) members which can be accessed without an object of the class.</span></span>

### <a name="create-an-object-from-a-class"></a><span data-ttu-id="24b4c-123">基于类创建对象</span><span class="sxs-lookup"><span data-stu-id="24b4c-123">Create an object from a class</span></span>

1. <span data-ttu-id="24b4c-124">确定要从哪个类创建对象，或定义自己的类。</span><span class="sxs-lookup"><span data-stu-id="24b4c-124">Determine from which class you want to create an object, or define your own class.</span></span> <span data-ttu-id="24b4c-125">例如：</span><span class="sxs-lookup"><span data-stu-id="24b4c-125">For example:</span></span>

   ```vb
   Public Class Customer
       Public Property AccountNumber As Integer
   End Class
   ```

2. <span data-ttu-id="24b4c-126">编写 [Dim 语句](../../../language-reference/statements/dim-statement.md)来创建一个变量，以便可以向其分配类实例。</span><span class="sxs-lookup"><span data-stu-id="24b4c-126">Write a [Dim Statement](../../../language-reference/statements/dim-statement.md) to create a variable to which you can assign a class instance.</span></span> <span data-ttu-id="24b4c-127">变量应为相应类的类型。</span><span class="sxs-lookup"><span data-stu-id="24b4c-127">The variable should be of the type of the desired class.</span></span>

   ```vb
   Dim nextCustomer As Customer
   ```

3. <span data-ttu-id="24b4c-128">添加 [New 运算符](../../../language-reference/operators/new-operator.md)关键字，将变量初始化为新的类实例。</span><span class="sxs-lookup"><span data-stu-id="24b4c-128">Add the [New Operator](../../../language-reference/operators/new-operator.md) keyword to initialize the variable to a new instance of the class.</span></span>

   ```vb
   Dim nextCustomer As New Customer
   ```

4. <span data-ttu-id="24b4c-129">现在可以通过对象变量访问类成员。</span><span class="sxs-lookup"><span data-stu-id="24b4c-129">You can now access the members of the class through the object variable.</span></span>

   ```vb
   nextCustomer.AccountNumber = lastAccountNumber + 1
   ```

> [!NOTE]
> <span data-ttu-id="24b4c-130">应尽可能将变量声明为要向其分配的类类型。</span><span class="sxs-lookup"><span data-stu-id="24b4c-130">Whenever possible, you should declare the variable to be of the class type you intend to assign to it.</span></span> <span data-ttu-id="24b4c-131">这称为 *早期绑定*。</span><span class="sxs-lookup"><span data-stu-id="24b4c-131">This is called *early binding*.</span></span> <span data-ttu-id="24b4c-132">如果在编译时不知道类类型，可将变量声明为 [Object 数据类型](../../../language-reference/data-types/object-data-type.md)，从而调用晚期绑定。</span><span class="sxs-lookup"><span data-stu-id="24b4c-132">If you don't know the class type at compile time, you can invoke *late binding* by declaring the variable to be of the [Object Data Type](../../../language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="24b4c-133">不过，晚期绑定可能会降低性能，并限制对运行时对象成员的访问。</span><span class="sxs-lookup"><span data-stu-id="24b4c-133">However, late binding can make performance slower and limit access to the run-time object's members.</span></span> <span data-ttu-id="24b4c-134">有关详细信息，请参阅[对象变量声明](../variables/object-variable-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="24b4c-134">For more information, see [Object Variable Declaration](../variables/object-variable-declaration.md).</span></span>

### <a name="multiple-instances"></a><span data-ttu-id="24b4c-135">多个实例</span><span class="sxs-lookup"><span data-stu-id="24b4c-135">Multiple instances</span></span>

<span data-ttu-id="24b4c-136">新建的类对象通常彼此相同。</span><span class="sxs-lookup"><span data-stu-id="24b4c-136">Objects newly created from a class are often identical to each other.</span></span> <span data-ttu-id="24b4c-137">然而，作为单独对象后，便可以更改其变量和属性，与其他实例互不影响。</span><span class="sxs-lookup"><span data-stu-id="24b4c-137">Once they exist as individual objects, however, their variables and properties can be changed independently of the other instances.</span></span> <span data-ttu-id="24b4c-138">例如，如果向窗体添加三个复选框，那么每个复选框对象都是 <xref:System.Windows.Forms.CheckBox> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="24b4c-138">For example, if you add three check boxes to a form, each check box object is an instance of the <xref:System.Windows.Forms.CheckBox> class.</span></span> <span data-ttu-id="24b4c-139">各个 <xref:System.Windows.Forms.CheckBox> 对象共用类定义的一组通用特征和功能（属性、变量、过程和事件）。</span><span class="sxs-lookup"><span data-stu-id="24b4c-139">The individual <xref:System.Windows.Forms.CheckBox> objects share a common set of characteristics and capabilities (properties, variables, procedures, and events) defined by the class.</span></span> <span data-ttu-id="24b4c-140">不过，每个对象都有自己的名称，不仅可以分开启用和禁用，还可以位于窗体上的不同位置。</span><span class="sxs-lookup"><span data-stu-id="24b4c-140">However, each has its own name, can be separately enabled and disabled, and can be placed in a different location on the form.</span></span>

## <a name="object-members"></a><span data-ttu-id="24b4c-141">对象成员</span><span class="sxs-lookup"><span data-stu-id="24b4c-141">Object members</span></span>

<span data-ttu-id="24b4c-142">对象是应用程序元素，表示类 *实例*。</span><span class="sxs-lookup"><span data-stu-id="24b4c-142">An object is an element of an application, representing an *instance* of a class.</span></span> <span data-ttu-id="24b4c-143">字段、属性、方法和事件是对象的构建基块，构成了它的 *成员*。</span><span class="sxs-lookup"><span data-stu-id="24b4c-143">Fields, properties, methods, and events are the building blocks of objects and constitute their *members*.</span></span>

### <a name="member-access"></a><span data-ttu-id="24b4c-144">成员访问</span><span class="sxs-lookup"><span data-stu-id="24b4c-144">Member Access</span></span>

<span data-ttu-id="24b4c-145">按顺序指定对象变量的名称、句点 (`.`) 和成员名称即可访问对象的成员。</span><span class="sxs-lookup"><span data-stu-id="24b4c-145">You access a member of an object by specifying, in order, the name of the object variable, a period (`.`), and the name of the member.</span></span> <span data-ttu-id="24b4c-146">下面的示例设置 <xref:System.Windows.Forms.Label> 对象的 <xref:System.Windows.Forms.Control.Text%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="24b4c-146">The following example sets the <xref:System.Windows.Forms.Control.Text%2A> property of a <xref:System.Windows.Forms.Label> object.</span></span>

```vb
warningLabel.Text = "Data not saved"
```

#### <a name="intellisense-listing-of-members"></a><span data-ttu-id="24b4c-147">IntelliSense 列出成员</span><span class="sxs-lookup"><span data-stu-id="24b4c-147">IntelliSense listing of members</span></span>

<span data-ttu-id="24b4c-148">当你调用类的“列出成员”选项时（例如，将句点 (`.`) 作为成员访问运算符键入时），IntelliSense 会列出类的成员。</span><span class="sxs-lookup"><span data-stu-id="24b4c-148">IntelliSense lists members of a class when you invoke its List Members option, for example when you type a period (`.`) as a member-access operator.</span></span> <span data-ttu-id="24b4c-149">如果在声明为相应类实例的变量名称后键入句点，IntelliSense 会列出所有实例成员，而不列出任何共享成员。</span><span class="sxs-lookup"><span data-stu-id="24b4c-149">If you type the period following the name of a variable declared as an instance of that class, IntelliSense lists all the instance members and none of the shared members.</span></span> <span data-ttu-id="24b4c-150">如果在类名本身后面键入句点，IntelliSense 会列出所有共享成员，而不列出任何实例成员。</span><span class="sxs-lookup"><span data-stu-id="24b4c-150">If you type the period following the class name itself, IntelliSense lists all the shared members and none of the instance members.</span></span> <span data-ttu-id="24b4c-151">有关详细信息，请参阅[使用 IntelliSense](/visualstudio/ide/using-intellisense)。</span><span class="sxs-lookup"><span data-stu-id="24b4c-151">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>

### <a name="fields-and-properties"></a><span data-ttu-id="24b4c-152">字段和属性</span><span class="sxs-lookup"><span data-stu-id="24b4c-152">Fields and properties</span></span>

<span data-ttu-id="24b4c-153">*字段* 和 *属性* 表示对象中存储的信息。</span><span class="sxs-lookup"><span data-stu-id="24b4c-153">*Fields* and *properties* represent information stored in an object.</span></span> <span data-ttu-id="24b4c-154">可以使用赋值语句检索和设置它们的值，方法与在过程中检索和设置局部变量的方法一样。</span><span class="sxs-lookup"><span data-stu-id="24b4c-154">You retrieve and set their values with assignment statements the same way you retrieve and set local variables in a procedure.</span></span> <span data-ttu-id="24b4c-155">下面的示例检索 <xref:System.Windows.Forms.Control.Width%2A> 属性，并设置 <xref:System.Windows.Forms.Label> 对象的 <xref:System.Windows.Forms.Control.ForeColor%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="24b4c-155">The following example retrieves the <xref:System.Windows.Forms.Control.Width%2A> property and sets the <xref:System.Windows.Forms.Control.ForeColor%2A> property of a <xref:System.Windows.Forms.Label> object.</span></span>

```vb
Dim warningWidth As Integer = warningLabel.Width
warningLabel.ForeColor = System.Drawing.Color.Red
```

<span data-ttu-id="24b4c-156">请注意，字段亦称为“*成员变量*”。</span><span class="sxs-lookup"><span data-stu-id="24b4c-156">Note that a field is also called a *member variable*.</span></span>

<span data-ttu-id="24b4c-157">在以下情况下，使用属性过程：</span><span class="sxs-lookup"><span data-stu-id="24b4c-157">Use property procedures when:</span></span>

- <span data-ttu-id="24b4c-158">需要控制何时以及如何设置或检索值。</span><span class="sxs-lookup"><span data-stu-id="24b4c-158">You need to control when and how a value is set or retrieved.</span></span>

- <span data-ttu-id="24b4c-159">需要验证属性的一组明确定义的值。</span><span class="sxs-lookup"><span data-stu-id="24b4c-159">The property has a well-defined set of values that need to be validated.</span></span>

- <span data-ttu-id="24b4c-160">设置值会导致对象状态发生某明显变化，如 `IsVisible` 属性。</span><span class="sxs-lookup"><span data-stu-id="24b4c-160">Setting the value causes some perceptible change in the object's state, such as an `IsVisible` property.</span></span>

- <span data-ttu-id="24b4c-161">设置属性会导致其他内部变量或其他属性的值发生变化。</span><span class="sxs-lookup"><span data-stu-id="24b4c-161">Setting the property causes changes to other internal variables or to the values of other properties.</span></span>

- <span data-ttu-id="24b4c-162">必须先执行一系列步骤，然后才能设置或检索属性。</span><span class="sxs-lookup"><span data-stu-id="24b4c-162">A set of steps must be performed before the property can be set or retrieved.</span></span>

<span data-ttu-id="24b4c-163">在以下情况下，使用字段：</span><span class="sxs-lookup"><span data-stu-id="24b4c-163">Use fields when:</span></span>

- <span data-ttu-id="24b4c-164">值是自验证类型。</span><span class="sxs-lookup"><span data-stu-id="24b4c-164">The value is of a self-validating type.</span></span> <span data-ttu-id="24b4c-165">例如，如果将 `True` 或 `False` 之外的值赋给 `Boolean` 变量，则会发生错误或自动数据转换。</span><span class="sxs-lookup"><span data-stu-id="24b4c-165">For example, an error or automatic data conversion occurs if a value other than `True` or `False` is assigned to a `Boolean` variable.</span></span>

- <span data-ttu-id="24b4c-166">数据类型支持的范围中的任何值都有效。</span><span class="sxs-lookup"><span data-stu-id="24b4c-166">Any value in the range supported by the data type is valid.</span></span> <span data-ttu-id="24b4c-167">对于 `Single` 或 `Double` 类型的许多属性，同样如此。</span><span class="sxs-lookup"><span data-stu-id="24b4c-167">This is true of many properties of type `Single` or `Double`.</span></span>

- <span data-ttu-id="24b4c-168">属性是 `String` 数据类型，并且对字符串的大小或值没有约束。</span><span class="sxs-lookup"><span data-stu-id="24b4c-168">The property is a `String` data type, and there is no constraint on the size or value of the string.</span></span>

- <span data-ttu-id="24b4c-169">有关详细信息，请参阅[属性过程](../procedures/property-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="24b4c-169">For more information, see [Property Procedures](../procedures/property-procedures.md).</span></span>

> [!TIP]
> <span data-ttu-id="24b4c-170">始终保持非常量字段为私有。</span><span class="sxs-lookup"><span data-stu-id="24b4c-170">Always keep the non-constant fields private.</span></span> <span data-ttu-id="24b4c-171">要使其成为公共的，请改用属性。</span><span class="sxs-lookup"><span data-stu-id="24b4c-171">When you want to make it public, use a property instead.</span></span>

### <a name="methods"></a><span data-ttu-id="24b4c-172">方法</span><span class="sxs-lookup"><span data-stu-id="24b4c-172">Methods</span></span>

<span data-ttu-id="24b4c-173">“方法”是对象可以执行的操作。</span><span class="sxs-lookup"><span data-stu-id="24b4c-173">A *method* is an action that an object can perform.</span></span> <span data-ttu-id="24b4c-174">例如，<xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A> 是 <xref:System.Windows.Forms.ComboBox> 对象的方法，该对象将新条目添加到组合框。</span><span class="sxs-lookup"><span data-stu-id="24b4c-174">For example, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A> is a method of the <xref:System.Windows.Forms.ComboBox> object that adds a new entry to a combo box.</span></span>

<span data-ttu-id="24b4c-175">下面的示例演示 <xref:System.Windows.Forms.Timer> 对象的 <xref:System.Windows.Forms.Timer.Start%2A> 用法。</span><span class="sxs-lookup"><span data-stu-id="24b4c-175">The following example demonstrates the <xref:System.Windows.Forms.Timer.Start%2A> method of a <xref:System.Windows.Forms.Timer> object.</span></span>

```vb
Dim safetyTimer As New System.Windows.Forms.Timer
safetyTimer.Start()
```

<span data-ttu-id="24b4c-176">请注意，方法只是对象公开的 *过程*。</span><span class="sxs-lookup"><span data-stu-id="24b4c-176">Note that a method is simply a *procedure* that is exposed by an object.</span></span>

<span data-ttu-id="24b4c-177">有关详细信息，请参阅[过程](../procedures/index.md)。</span><span class="sxs-lookup"><span data-stu-id="24b4c-177">For more information, see [Procedures](../procedures/index.md).</span></span>

### <a name="events"></a><span data-ttu-id="24b4c-178">事件</span><span class="sxs-lookup"><span data-stu-id="24b4c-178">Events</span></span>

<span data-ttu-id="24b4c-179">事件是由对象识别的操作（如单击鼠标或按某个键），可以编写代码来响应这些操作。</span><span class="sxs-lookup"><span data-stu-id="24b4c-179">An event is an action recognized by an object, such as clicking the mouse or pressing a key, and for which you can write code to respond.</span></span> <span data-ttu-id="24b4c-180">事件可能是由用户操作或程序代码生成，也可能是由系统生成。</span><span class="sxs-lookup"><span data-stu-id="24b4c-180">Events can occur as a result of a user action or program code, or they can be caused by the system.</span></span> <span data-ttu-id="24b4c-181">提示事件发生的代码可以说是负责 *引发* 事件，而响应事件的代码则可以说是负责 *处理* 事件。</span><span class="sxs-lookup"><span data-stu-id="24b4c-181">Code that signals an event is said to *raise* the event, and code that responds to it is said to *handle* it.</span></span>

<span data-ttu-id="24b4c-182">还可以开发你自己的自定义事件，以便由对象引发并由其他对象处理。</span><span class="sxs-lookup"><span data-stu-id="24b4c-182">You can also develop your own custom events to be raised by your objects and handled by other objects.</span></span> <span data-ttu-id="24b4c-183">有关详细信息，请参阅[事件](../events/index.md)。</span><span class="sxs-lookup"><span data-stu-id="24b4c-183">For more information, see [Events](../events/index.md).</span></span>

### <a name="instance-members-and-shared-members"></a><span data-ttu-id="24b4c-184">实例成员和共享成员</span><span class="sxs-lookup"><span data-stu-id="24b4c-184">Instance members and shared members</span></span>

<span data-ttu-id="24b4c-185">创建类对象时，生成的是相应类实例。</span><span class="sxs-lookup"><span data-stu-id="24b4c-185">When you create an object from a class, the result is an instance of that class.</span></span> <span data-ttu-id="24b4c-186">未使用 [Shared](../../../language-reference/modifiers/shared.md) 关键字声明的成员是 *实例成员*，严格属于特定实例。</span><span class="sxs-lookup"><span data-stu-id="24b4c-186">Members that are not declared with the [Shared](../../../language-reference/modifiers/shared.md) keyword are *instance members*, which belong strictly to that particular instance.</span></span> <span data-ttu-id="24b4c-187">一个实例中的实例成员与同一类的另一实例中的同一成员互不影响。</span><span class="sxs-lookup"><span data-stu-id="24b4c-187">An instance member in one instance is independent of the same member in another instance of the same class.</span></span> <span data-ttu-id="24b4c-188">例如，一个实例成员变量可以在不同的实例中有不同的值。</span><span class="sxs-lookup"><span data-stu-id="24b4c-188">An instance member variable, for example, can have different values in different instances.</span></span>

<span data-ttu-id="24b4c-189">使用 `Shared` 关键字声明的成员是 *共享成员*，属于整个类，而不属于任何特定实例。</span><span class="sxs-lookup"><span data-stu-id="24b4c-189">Members declared with the `Shared` keyword are *shared members*, which belong to the class as a whole and not to any particular instance.</span></span> <span data-ttu-id="24b4c-190">无论创建多少类实例，或者即便未创建实例，共享成员也都只有一个。</span><span class="sxs-lookup"><span data-stu-id="24b4c-190">A shared member exists only once, no matter how many instances of its class you create, or even if you create no instances.</span></span> <span data-ttu-id="24b4c-191">例如，共享成员变量只有一个值，可供访问相应类的所有代码使用。</span><span class="sxs-lookup"><span data-stu-id="24b4c-191">A shared member variable, for example, has only one value, which is available to all code that can access the class.</span></span>

#### <a name="accessing-non-shared-members"></a><span data-ttu-id="24b4c-192">访问非共享成员</span><span class="sxs-lookup"><span data-stu-id="24b4c-192">Accessing non-shared members</span></span>

1. <span data-ttu-id="24b4c-193">请确保已创建类对象，并已将对象分配给对象变量。</span><span class="sxs-lookup"><span data-stu-id="24b4c-193">Make sure the object has been created from its class and assigned to an object variable.</span></span>

   ```vb
   Dim secondForm As New System.Windows.Forms.Form
   ```

2. <span data-ttu-id="24b4c-194">在访问成员的语句中，使用 *成员访问运算符* 的对象变量名称 (`.`) ，然后单击成员名称。</span><span class="sxs-lookup"><span data-stu-id="24b4c-194">In the statement that accesses the member, follow the object variable name with the *member-access operator* (`.`) and then the member name.</span></span>

   ```vb
   secondForm.Show()
   ```

#### <a name="accessing-shared-members"></a><span data-ttu-id="24b4c-195">访问共享成员</span><span class="sxs-lookup"><span data-stu-id="24b4c-195">Accessing shared members</span></span>

- <span data-ttu-id="24b4c-196">在类名称后跟 *成员访问运算符* (`.`) ，然后是成员名称。</span><span class="sxs-lookup"><span data-stu-id="24b4c-196">Follow the class name with the *member-access operator* (`.`) and then the member name.</span></span> <span data-ttu-id="24b4c-197">应始终通过类名直接访问对象的 `Shared` 成员。</span><span class="sxs-lookup"><span data-stu-id="24b4c-197">You should always access a `Shared` member of the object directly through the class name.</span></span>

   ```vb
   Console.WriteLine("This computer is called " & Environment.MachineName)
   ```

- <span data-ttu-id="24b4c-198">如果已创建了类对象，也可以通过对象的变量访问 `Shared` 成员。</span><span class="sxs-lookup"><span data-stu-id="24b4c-198">If you have already created an object from the class, you can alternatively access a `Shared` member through the object's variable.</span></span>

### <a name="differences-between-classes-and-modules"></a><span data-ttu-id="24b4c-199">类和模块的区别</span><span class="sxs-lookup"><span data-stu-id="24b4c-199">Differences between classes and modules</span></span>

<span data-ttu-id="24b4c-200">类和模块的主要区别是，类可以实例化成对象，而标准模块则不能。</span><span class="sxs-lookup"><span data-stu-id="24b4c-200">The main difference between classes and modules is that classes can be instantiated as objects while standard modules cannot.</span></span> <span data-ttu-id="24b4c-201">因为只有一个标准模块数据副本，所以当程序的一部分更改标准模块中的公共变量时，如果程序的其他任何部分读取了此变量，也会获得相同的值。</span><span class="sxs-lookup"><span data-stu-id="24b4c-201">Because there is only one copy of a standard module's data, when one part of your program changes a public variable in a standard module, any other part of the program gets the same value if it then reads that variable.</span></span> <span data-ttu-id="24b4c-202">相反，每个实例化的对象都有各自的对象数据。</span><span class="sxs-lookup"><span data-stu-id="24b4c-202">In contrast, object data exists separately for each instantiated object.</span></span> <span data-ttu-id="24b4c-203">还有一个区别是，与标准模块不同，类可以实现接口。</span><span class="sxs-lookup"><span data-stu-id="24b4c-203">Another difference is that unlike standard modules, classes can implement interfaces.</span></span> <span data-ttu-id="24b4c-204">如果用 [MustInherit](../../../language-reference/modifiers/mustinherit.md) 修饰符标记了某个类，则不能直接对其进行实例化。</span><span class="sxs-lookup"><span data-stu-id="24b4c-204">If a class is marked with the [MustInherit](../../../language-reference/modifiers/mustinherit.md) modifier, it can't be instantiated directly.</span></span> <span data-ttu-id="24b4c-205">但是，它仍与模块不同，因为在模块无法继承时可以继承。</span><span class="sxs-lookup"><span data-stu-id="24b4c-205">However, it's still different from a module as it can be inherited while modules can't be inherited.</span></span>

> [!NOTE]
> <span data-ttu-id="24b4c-206">将 `Shared` 修饰符应用于类成员时，它是与类本身相关联，而不是与特定的类实例相关联。</span><span class="sxs-lookup"><span data-stu-id="24b4c-206">When the `Shared` modifier is applied to a class member, it is associated with the class itself instead of a particular instance of the class.</span></span> <span data-ttu-id="24b4c-207">类成员是使用类名直接访问，方法与访问模块成员一样。</span><span class="sxs-lookup"><span data-stu-id="24b4c-207">The member is accessed directly by using the class name, the same way module members are accessed.</span></span>

<span data-ttu-id="24b4c-208">此外，类和模块对其成员划定的范围也不同。</span><span class="sxs-lookup"><span data-stu-id="24b4c-208">Classes and modules also use different scopes for their members.</span></span> <span data-ttu-id="24b4c-209">类中定义的成员将范围限定为类的特定实例内，并且仅存在于对象的生存期内。</span><span class="sxs-lookup"><span data-stu-id="24b4c-209">Members defined within a class are scoped within a specific instance of the class and exist only for the lifetime of the object.</span></span> <span data-ttu-id="24b4c-210">若要从类外部访问类成员，必须使用 *Object*.*Member* 格式的完全限定的名称。</span><span class="sxs-lookup"><span data-stu-id="24b4c-210">To access class members from outside a class, you must use fully qualified names in the format of *Object*.*Member*.</span></span>

<span data-ttu-id="24b4c-211">相比之下，在模块中声明的成员默认可公开访问，并且可由能够访问模块的任意代码进行访问。</span><span class="sxs-lookup"><span data-stu-id="24b4c-211">On the other hand, members declared within a module are publicly accessible by default, and can be accessed by any code that can access the module.</span></span> <span data-ttu-id="24b4c-212">也就是说，标准模块中的变量实际上是全局变量，因为它们在项目的任何位置都可见，并且存在于程序的生存期内。</span><span class="sxs-lookup"><span data-stu-id="24b4c-212">This means that variables in a standard module are effectively global variables because they are visible from anywhere in your project, and they exist for the life of the program.</span></span>

## <a name="reusing-classes-and-objects"></a><span data-ttu-id="24b4c-213">重用类和对象</span><span class="sxs-lookup"><span data-stu-id="24b4c-213">Reusing classes and objects</span></span>

<span data-ttu-id="24b4c-214">使用对象，只需声明变量和过程一次，即可根据需要随时重用它们。</span><span class="sxs-lookup"><span data-stu-id="24b4c-214">Objects let you declare variables and procedures once and then reuse them whenever needed.</span></span> <span data-ttu-id="24b4c-215">例如，如果要向应用程序添加拼写检查，可以定义所有变量和支持函数，以提供拼写检查功能。</span><span class="sxs-lookup"><span data-stu-id="24b4c-215">For example, if you want to add a spelling checker to an application you could define all the variables and support functions to provide spell-checking functionality.</span></span> <span data-ttu-id="24b4c-216">如果将拼写检查创建为类，可以添加对已编译程序集的引用，从而在其他应用程序中重用此类。</span><span class="sxs-lookup"><span data-stu-id="24b4c-216">If you create your spelling checker as a class, you can then reuse it in other applications by adding a reference to the compiled assembly.</span></span> <span data-ttu-id="24b4c-217">更好的是，可以使用别人已经开发的拼写检查类，从而减少自己的工作量。</span><span class="sxs-lookup"><span data-stu-id="24b4c-217">Better yet, you may be able to save yourself some work by using a spelling checker class that someone else has already developed.</span></span>

<span data-ttu-id="24b4c-218">.NET 提供了许多可供使用的组件示例。</span><span class="sxs-lookup"><span data-stu-id="24b4c-218">.NET provides many examples of components that are available for use.</span></span> <span data-ttu-id="24b4c-219">下面的示例使用 <xref:System> 命名空间中的 <xref:System.TimeZone> 类。</span><span class="sxs-lookup"><span data-stu-id="24b4c-219">The following example uses the <xref:System.TimeZone> class in the <xref:System> namespace.</span></span> <span data-ttu-id="24b4c-220"><xref:System.TimeZone> 提供的成员可检索当前计算机系统的时区信息。</span><span class="sxs-lookup"><span data-stu-id="24b4c-220"><xref:System.TimeZone> provides members that allow you to retrieve information about the time zone of the current computer system.</span></span>

```vb
Public Sub ExamineTimeZone()
    Dim tz As System.TimeZone = System.TimeZone.CurrentTimeZone
    Dim s As String = "Current time zone is "
    s &= CStr(tz.GetUtcOffset(Now).Hours) & " hours and "
    s &= CStr(tz.GetUtcOffset(Now).Minutes) & " minutes "
    s &= "different from UTC (coordinated universal time)"
    s &= vbCrLf & "and is currently "
    If tz.IsDaylightSavingTime(Now) = False Then s &= "not "
    s &= "on ""summer time""."
    Console.WriteLine(s)
End Sub
```

<span data-ttu-id="24b4c-221">在上面的示例中，第一个 [Dim 语句](../../../language-reference/statements/dim-statement.md)声明 <xref:System.TimeZone> 类型的对象变量，并将其分配到由 <xref:System.TimeZone.CurrentTimeZone%2A> 属性返回的 <xref:System.TimeZone> 对象。</span><span class="sxs-lookup"><span data-stu-id="24b4c-221">In the preceding example, the first [Dim Statement](../../../language-reference/statements/dim-statement.md) declares an object variable of type <xref:System.TimeZone> and assigns to it a <xref:System.TimeZone> object returned by the <xref:System.TimeZone.CurrentTimeZone%2A> property.</span></span>

## <a name="relationships-among-objects"></a><span data-ttu-id="24b4c-222">对象之间的关系</span><span class="sxs-lookup"><span data-stu-id="24b4c-222">Relationships among objects</span></span>

<span data-ttu-id="24b4c-223">对象可通过多种方式彼此关联。</span><span class="sxs-lookup"><span data-stu-id="24b4c-223">Objects can be related to each other in several ways.</span></span> <span data-ttu-id="24b4c-224">两种主要关系是 *分层* 和 *包含* 关系。</span><span class="sxs-lookup"><span data-stu-id="24b4c-224">The principal kinds of relationship are *hierarchical* and *containment*.</span></span>

### <a name="hierarchical-relationship"></a><span data-ttu-id="24b4c-225">分层关系</span><span class="sxs-lookup"><span data-stu-id="24b4c-225">Hierarchical relationship</span></span>

<span data-ttu-id="24b4c-226">如果类派生自更为基础的类，可以认为构成了 *分层关系*。</span><span class="sxs-lookup"><span data-stu-id="24b4c-226">When classes are derived from more fundamental classes, they are said to have a *hierarchical relationship*.</span></span> <span data-ttu-id="24b4c-227">当描述更为通用的类的子类型项时，类层次结构就很有用。</span><span class="sxs-lookup"><span data-stu-id="24b4c-227">Class hierarchies are useful when describing items that are a subtype of a more general class.</span></span>

<span data-ttu-id="24b4c-228">在下面的示例中，假设要定义一种特殊类型的 <xref:System.Windows.Forms.Button>，类似于普通的 <xref:System.Windows.Forms.Button>，不同之处在于公开了用于保留前景色和背景色的方法。</span><span class="sxs-lookup"><span data-stu-id="24b4c-228">In the following example, suppose you want to define a special kind of <xref:System.Windows.Forms.Button> that acts like a normal <xref:System.Windows.Forms.Button> but also exposes a method that reverses the foreground and background colors.</span></span>

#### <a name="define-a-class-that-is-derived-from-an-already-existing-class"></a><span data-ttu-id="24b4c-229">定义派生自现有类的类</span><span class="sxs-lookup"><span data-stu-id="24b4c-229">Define a class that is derived from an already existing class</span></span>

1. <span data-ttu-id="24b4c-230">使用 [Class 语句](../../../language-reference/statements/class-statement.md)定义要创建其所需对象的类。</span><span class="sxs-lookup"><span data-stu-id="24b4c-230">Use a [Class Statement](../../../language-reference/statements/class-statement.md) to define a class from which to create the object you need.</span></span>

   ```vb
   Public Class ReversibleButton
   ```

   <span data-ttu-id="24b4c-231">请务必在类的最后一行代码后添加 `End Class` 语句。</span><span class="sxs-lookup"><span data-stu-id="24b4c-231">Be sure an `End Class` statement follows the last line of code in your class.</span></span> <span data-ttu-id="24b4c-232">默认情况下，集成开发环境 (IDE) 会在你输入 `Class` 语句时自动生成 `End Class`。</span><span class="sxs-lookup"><span data-stu-id="24b4c-232">By default, the integrated development environment (IDE) automatically generates an `End Class` when you enter a `Class` statement.</span></span>

2. <span data-ttu-id="24b4c-233">在 `Class` 语句后面紧接着编写 [Inherits 语句](../../../language-reference/statements/inherits-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="24b4c-233">Follow the `Class` statement immediately with an [Inherits Statement](../../../language-reference/statements/inherits-statement.md).</span></span> <span data-ttu-id="24b4c-234">指定新类派生自的类。</span><span class="sxs-lookup"><span data-stu-id="24b4c-234">Specify the class from which your new class derives.</span></span>

   ```vb
   Inherits System.Windows.Forms.Button
   ```

   <span data-ttu-id="24b4c-235">新类继承了基类定义的所有成员。</span><span class="sxs-lookup"><span data-stu-id="24b4c-235">Your new class inherits all the members defined by the base class.</span></span>

3. <span data-ttu-id="24b4c-236">添加派生类公开的其他成员的代码。</span><span class="sxs-lookup"><span data-stu-id="24b4c-236">Add the code for the additional members your derived class exposes.</span></span> <span data-ttu-id="24b4c-237">例如，可以添加 `ReverseColors` 方法，派生类将如下所示：</span><span class="sxs-lookup"><span data-stu-id="24b4c-237">For example, you might add a `ReverseColors` method, and your derived class might look as follows:</span></span>

   ```vb
   Public Class ReversibleButton
       Inherits System.Windows.Forms.Button
           Public Sub ReverseColors()
               Dim saveColor As System.Drawing.Color = Me.BackColor
               Me.BackColor = Me.ForeColor
               Me.ForeColor = saveColor
          End Sub
   End Class
   ```

   <span data-ttu-id="24b4c-238">如果从类创建一个对象 `ReversibleButton` ，则它可以访问类的所有成员，以及 <xref:System.Windows.Forms.Button> `ReverseColors` 在中定义的方法和任何其他新成员 `ReversibleButton` 。</span><span class="sxs-lookup"><span data-stu-id="24b4c-238">If you create an object from the `ReversibleButton` class, it can access all the members of the <xref:System.Windows.Forms.Button> class, as well as the `ReverseColors` method and any other new members you define in `ReversibleButton`.</span></span>

<span data-ttu-id="24b4c-239">派生类继承基类的成员，因此随着类层次结构的不断深入，复杂性也随之增加。</span><span class="sxs-lookup"><span data-stu-id="24b4c-239">Derived classes inherit members from the class they are based on, allowing you to add complexity as you progress in a class hierarchy.</span></span> <span data-ttu-id="24b4c-240">有关详细信息，请参阅[继承基础知识](inheritance-basics.md)。</span><span class="sxs-lookup"><span data-stu-id="24b4c-240">For more information, see [Inheritance Basics](inheritance-basics.md).</span></span>

### <a name="compile-the-code"></a><span data-ttu-id="24b4c-241">编译代码</span><span class="sxs-lookup"><span data-stu-id="24b4c-241">Compile the code</span></span>

<span data-ttu-id="24b4c-242">请确保编译器可以访问要从中派生新类的类。</span><span class="sxs-lookup"><span data-stu-id="24b4c-242">Be sure the compiler can access the class from which you intend to derive your new class.</span></span> <span data-ttu-id="24b4c-243">也就是说，完全限定其名称（如上面的示例所示），或在 [Imports 语句（.NET 命名空间和类型）](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)中标识其命名空间。</span><span class="sxs-lookup"><span data-stu-id="24b4c-243">This might mean fully qualifying its name, as in the preceding example, or identifying its namespace in an [Imports Statement (.NET Namespace and Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span> <span data-ttu-id="24b4c-244">如果类在不同的项目中，可能需要添加对相应项目的引用。</span><span class="sxs-lookup"><span data-stu-id="24b4c-244">If the class is in a different project, you might need to add a reference to that project.</span></span> <span data-ttu-id="24b4c-245">有关详细信息，请参阅[管理项目中的引用](/visualstudio/ide/managing-references-in-a-project)。</span><span class="sxs-lookup"><span data-stu-id="24b4c-245">For more information, see [Managing references in a project](/visualstudio/ide/managing-references-in-a-project).</span></span>

### <a name="containment-relationship"></a><span data-ttu-id="24b4c-246">包含关系</span><span class="sxs-lookup"><span data-stu-id="24b4c-246">Containment relationship</span></span>

<span data-ttu-id="24b4c-247">另一种对象关联方式是使用 *包含关系*。</span><span class="sxs-lookup"><span data-stu-id="24b4c-247">Another way that objects can be related is a *containment relationship*.</span></span> <span data-ttu-id="24b4c-248">容器对象在逻辑上封装其他对象。</span><span class="sxs-lookup"><span data-stu-id="24b4c-248">Container objects logically encapsulate other objects.</span></span> <span data-ttu-id="24b4c-249">例如，<xref:System.OperatingSystem> 对象在逻辑上包含一个通过其 <xref:System.OperatingSystem.Version%2A> 属性返回的 <xref:System.Version> 对象。</span><span class="sxs-lookup"><span data-stu-id="24b4c-249">For example, the <xref:System.OperatingSystem> object logically contains a <xref:System.Version> object, which it returns through its <xref:System.OperatingSystem.Version%2A> property.</span></span> <span data-ttu-id="24b4c-250">请注意，容器对象实际上并不包含其他任何对象。</span><span class="sxs-lookup"><span data-stu-id="24b4c-250">Note that the container object does not physically contain any other object.</span></span>

#### <a name="collections"></a><span data-ttu-id="24b4c-251">集合</span><span class="sxs-lookup"><span data-stu-id="24b4c-251">Collections</span></span>

<span data-ttu-id="24b4c-252">一种特殊类型的对象包含关系用 *集合* 来表示。</span><span class="sxs-lookup"><span data-stu-id="24b4c-252">One particular type of object containment is represented by *collections*.</span></span> <span data-ttu-id="24b4c-253">集合是一组可以枚举的类似对象。</span><span class="sxs-lookup"><span data-stu-id="24b4c-253">Collections are groups of similar objects that can be enumerated.</span></span> <span data-ttu-id="24b4c-254">Visual Basic 支持中的特定语法 [.。。](../../../language-reference/statements/for-each-next-statement.md) 允许您循环访问集合中的项的下一条语句。</span><span class="sxs-lookup"><span data-stu-id="24b4c-254">Visual Basic supports a specific syntax in the [For Each...Next Statement](../../../language-reference/statements/for-each-next-statement.md) that allows you to iterate through the items of a collection.</span></span> <span data-ttu-id="24b4c-255">此外，借助集合，通常还可以使用 <xref:Microsoft.VisualBasic.Collection.Item%2A> 根据索引检索元素，或通过将元素与唯一字符串相关联进行检索。</span><span class="sxs-lookup"><span data-stu-id="24b4c-255">Additionally, collections often allow you to use an <xref:Microsoft.VisualBasic.Collection.Item%2A> to retrieve elements by their index or by associating them with a unique string.</span></span> <span data-ttu-id="24b4c-256">集合比数组更易于使用，因为无需使用索引，即可添加或删除项。</span><span class="sxs-lookup"><span data-stu-id="24b4c-256">Collections can be easier to use than arrays because they allow you to add or remove items without using indexes.</span></span> <span data-ttu-id="24b4c-257">鉴于它的易用性，集合通常用于存储窗体和控件。</span><span class="sxs-lookup"><span data-stu-id="24b4c-257">Because of their ease of use, collections are often used to store forms and controls.</span></span>

## <a name="related-topics"></a><span data-ttu-id="24b4c-258">相关主题</span><span class="sxs-lookup"><span data-stu-id="24b4c-258">Related topics</span></span>

<span data-ttu-id="24b4c-259">[演练：定义类](walkthrough-defining-classes.md)</span><span class="sxs-lookup"><span data-stu-id="24b4c-259">[Walkthrough: Defining Classes](walkthrough-defining-classes.md)</span></span>\
<span data-ttu-id="24b4c-260">分步说明了如何创建类。</span><span class="sxs-lookup"><span data-stu-id="24b4c-260">Provides a step-by-step description of how to create a class.</span></span>

<span data-ttu-id="24b4c-261">[重载属性和方法](overloaded-properties-and-methods.md)</span><span class="sxs-lookup"><span data-stu-id="24b4c-261">[Overloaded Properties and Methods](overloaded-properties-and-methods.md)</span></span>\
<span data-ttu-id="24b4c-262">重载属性和方法</span><span class="sxs-lookup"><span data-stu-id="24b4c-262">Overloaded Properties and Methods</span></span>

<span data-ttu-id="24b4c-263">[继承基础知识](inheritance-basics.md)</span><span class="sxs-lookup"><span data-stu-id="24b4c-263">[Inheritance Basics](inheritance-basics.md)</span></span>\
<span data-ttu-id="24b4c-264">介绍了继承修饰符、重写方法和属性（MyClass 和 MyBase）。</span><span class="sxs-lookup"><span data-stu-id="24b4c-264">Covers inheritance modifiers, overriding methods and properties, MyClass, and MyBase.</span></span>

<span data-ttu-id="24b4c-265">[对象生存期：如何创建和销毁对象](object-lifetime-how-objects-are-created-and-destroyed.md)</span><span class="sxs-lookup"><span data-stu-id="24b4c-265">[Object Lifetime: How Objects Are Created and Destroyed](object-lifetime-how-objects-are-created-and-destroyed.md)</span></span>\
<span data-ttu-id="24b4c-266">介绍了如何创建和释放类实例。</span><span class="sxs-lookup"><span data-stu-id="24b4c-266">Discusses creating and disposing of class instances.</span></span>

<span data-ttu-id="24b4c-267">[匿名类型](anonymous-types.md)</span><span class="sxs-lookup"><span data-stu-id="24b4c-267">[Anonymous Types](anonymous-types.md)</span></span>\
<span data-ttu-id="24b4c-268">介绍了如何创建和使用匿名类型，这样无需为数据类型编写类定义即可创建对象。</span><span class="sxs-lookup"><span data-stu-id="24b4c-268">Describes how to create and use anonymous types, which allow you to create objects without writing a class definition for the data type.</span></span>

<span data-ttu-id="24b4c-269">[对象初始值设定项：命名类型和匿名类型](object-initializers-named-and-anonymous-types.md)</span><span class="sxs-lookup"><span data-stu-id="24b4c-269">[Object Initializers: Named and Anonymous Types](object-initializers-named-and-anonymous-types.md)</span></span>\
<span data-ttu-id="24b4c-270">介绍了对象初始值设定项，用于通过一个表达式创建已命名和匿名类型的实例。</span><span class="sxs-lookup"><span data-stu-id="24b4c-270">Discusses object initializers, which are used to create instances of named and anonymous types by using a single expression.</span></span>

<span data-ttu-id="24b4c-271">[如何：推断匿名类型声明中的属性名称和类型](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)</span><span class="sxs-lookup"><span data-stu-id="24b4c-271">[How to: Infer Property Names and Types in Anonymous Type Declarations](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)</span></span>\
<span data-ttu-id="24b4c-272">介绍了如何推断匿名类型声明中的属性名称和类型。</span><span class="sxs-lookup"><span data-stu-id="24b4c-272">Explains how to infer property names and types in anonymous type declarations.</span></span> <span data-ttu-id="24b4c-273">收录了推理成功和失败的示例。</span><span class="sxs-lookup"><span data-stu-id="24b4c-273">Provides examples of successful and unsuccessful inference.</span></span>
