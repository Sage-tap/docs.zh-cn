---
description: '了解详细信息： (Visual Basic 的集合初始值设定项) '
title: 集合初始值设定项
ms.date: 07/20/2015
f1_keywords:
- vb.CollectionInitializer
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: a9290329-77b0-4fdf-ae75-8fc17287f469
ms.openlocfilehash: afae9278092934ead4572f16fb1ec4a29d631803
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475456"
---
# <a name="collection-initializers-visual-basic"></a><span data-ttu-id="75b8d-103">集合初始值设定项 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="75b8d-103">Collection Initializers (Visual Basic)</span></span>

<span data-ttu-id="75b8d-104">集合初始值设定项提供了用于创建集合并在其中填充一组初始值的缩短语法。</span><span class="sxs-lookup"><span data-stu-id="75b8d-104">*Collection initializers* provide a shortened syntax that enables you to create a collection and populate it with an initial set of values.</span></span> <span data-ttu-id="75b8d-105">若要通过一组已知值（例如，菜单选项或类别列表、一组初始数字值、字符串（如日期或月份名称）或地理位置（如用于验证的州或省/自治区/直辖市列表）静态列表）创建集合，将会发现集合初始值设定项非常有用。</span><span class="sxs-lookup"><span data-stu-id="75b8d-105">Collection initializers are useful when you are creating a collection from a set of known values, for example, a list of menu options or categories, an initial set of numeric values, a static list of strings such as day or month names, or geographic locations such as a list of states that is used for validation.</span></span>

<span data-ttu-id="75b8d-106">有关集合的详细信息，请参阅[集合](../../concepts/collections.md)。</span><span class="sxs-lookup"><span data-stu-id="75b8d-106">For more information about collections, see [Collections](../../concepts/collections.md).</span></span>

<span data-ttu-id="75b8d-107">在 `From` 关键字后面使用大括号 (`{}`) 来标识集合初始值设定项。</span><span class="sxs-lookup"><span data-stu-id="75b8d-107">You identify a collection initializer by using the `From` keyword followed by braces (`{}`).</span></span> <span data-ttu-id="75b8d-108">这类似于[数组](../arrays/index.md)中所述的数组文本语法。</span><span class="sxs-lookup"><span data-stu-id="75b8d-108">This is similar to the array literal syntax that is described in [Arrays](../arrays/index.md).</span></span> <span data-ttu-id="75b8d-109">下面的示例展示了使用集合初始值设定项创建集合的各种方法。</span><span class="sxs-lookup"><span data-stu-id="75b8d-109">The following examples show various ways to use collection initializers to create collections.</span></span>

[!code-vb[VbVbalrCollectionInitializers#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#1)]

> [!NOTE]
> <span data-ttu-id="75b8d-110">C# 也提供集合初始值设定项。</span><span class="sxs-lookup"><span data-stu-id="75b8d-110">C# also provides collection initializers.</span></span> <span data-ttu-id="75b8d-111">C# 集合初始值设定项的功能与 Visual Basic 集合初始值设定项相同。</span><span class="sxs-lookup"><span data-stu-id="75b8d-111">C# collection initializers provide the same functionality as Visual Basic collection initializers.</span></span> <span data-ttu-id="75b8d-112">有关 C# 集合初始值设定项的详细信息，请参阅[对象和集合初始值设定项](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)。</span><span class="sxs-lookup"><span data-stu-id="75b8d-112">For more information about C# collection initializers, see [Object and Collection Initializers](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="75b8d-113">语法</span><span class="sxs-lookup"><span data-stu-id="75b8d-113">Syntax</span></span>

<span data-ttu-id="75b8d-114">集合初始值设定项先是包含 `From` 关键字，后跟用大括号 (`{}`) 括住的逗号分隔值列表，如以下代码所示。</span><span class="sxs-lookup"><span data-stu-id="75b8d-114">A collection initializer consists of a list of comma-separated values that are enclosed in braces (`{}`), preceded by the `From` keyword, as shown in the following code.</span></span>

[!code-vb[VbVbalrCollectionInitializers#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#2)]

<span data-ttu-id="75b8d-115">创建集合（如 <xref:System.Collections.Generic.List%601> 或 <xref:System.Collections.Generic.Dictionary%602>）时，必须在集合初始值设定项之前提供集合类型，如以下代码所示。</span><span class="sxs-lookup"><span data-stu-id="75b8d-115">When you create a collection, such as a <xref:System.Collections.Generic.List%601> or a <xref:System.Collections.Generic.Dictionary%602>, you must supply the collection type before the collection initializer, as shown in the following code.</span></span>

[!code-vb[VbVbalrCollectionInitializers#13](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#13)]

> [!NOTE]
> <span data-ttu-id="75b8d-116">不能合并集合初始值设定项和对象初始值设定项来初始化同一集合对象。</span><span class="sxs-lookup"><span data-stu-id="75b8d-116">You cannot combine both a collection initializer and an object initializer to initialize the same collection object.</span></span> <span data-ttu-id="75b8d-117">可以使用对象初始值设定项来初始化集合初始值设定项中的对象。</span><span class="sxs-lookup"><span data-stu-id="75b8d-117">You can use object initializers to initialize objects in a collection initializer.</span></span>

## <a name="creating-a-collection-by-using-a-collection-initializer"></a><span data-ttu-id="75b8d-118">使用集合初始值设定项创建集合</span><span class="sxs-lookup"><span data-stu-id="75b8d-118">Creating a Collection by Using a Collection Initializer</span></span>

<span data-ttu-id="75b8d-119">使用集合初始值设定项创建集合时，集合初始值设定项中提供的每个值都会传递到集合的相应 `Add` 方法中。</span><span class="sxs-lookup"><span data-stu-id="75b8d-119">When you create a collection by using a collection initializer, each value that is supplied in the collection initializer is passed to the appropriate `Add` method of the collection.</span></span> <span data-ttu-id="75b8d-120">例如，如果使用集合初始值设定项创建 <xref:System.Collections.Generic.List%601>，那么集合初始值设定项中的每个字符串值都会传递到 <xref:System.Collections.Generic.List%601.Add%2A> 方法中。</span><span class="sxs-lookup"><span data-stu-id="75b8d-120">For example, if you create a <xref:System.Collections.Generic.List%601> by using a collection initializer, each string value in the collection initializer is passed to the <xref:System.Collections.Generic.List%601.Add%2A> method.</span></span> <span data-ttu-id="75b8d-121">若要使用集合初始值设定项创建集合，指定的类型必须是有效的集合类型。</span><span class="sxs-lookup"><span data-stu-id="75b8d-121">If you want to create a collection by using a collection initializer, the specified type must be valid collection type.</span></span> <span data-ttu-id="75b8d-122">有效的集合类型示例包括实现 <xref:System.Collections.Generic.IEnumerable%601> 接口或继承 <xref:System.Collections.CollectionBase> 类的类。</span><span class="sxs-lookup"><span data-stu-id="75b8d-122">Examples of valid collection types include classes that implement the <xref:System.Collections.Generic.IEnumerable%601> interface or inherit the <xref:System.Collections.CollectionBase> class.</span></span> <span data-ttu-id="75b8d-123">指定的类型还必须公开满足以下条件的 `Add` 方法。</span><span class="sxs-lookup"><span data-stu-id="75b8d-123">The specified type must also expose an `Add` method that meets the following criteria.</span></span>

- <span data-ttu-id="75b8d-124">`Add` 方法必须可通过其中调用了集合初始值设定项的作用域获取。</span><span class="sxs-lookup"><span data-stu-id="75b8d-124">The `Add` method must be available from the scope in which the collection initializer is being called.</span></span> <span data-ttu-id="75b8d-125">若要在可以访问集合内非公开方法的方案中使用集合初始值设定项，不一定要公开 `Add` 方法。</span><span class="sxs-lookup"><span data-stu-id="75b8d-125">The `Add` method does not have to be public if you are using the collection initializer in a scenario where non-public methods of the collection can be accessed.</span></span>

- <span data-ttu-id="75b8d-126">`Add` 方法必须是集合类的实例成员或 `Shared` 成员，或必须是扩展方法。</span><span class="sxs-lookup"><span data-stu-id="75b8d-126">The `Add` method must be an instance member or `Shared` member of the collection class, or an extension method.</span></span>

- <span data-ttu-id="75b8d-127">`Add` 方法必须存在，可以根据重载解析规则与集合初始值设定项中提供的类型进行匹配。</span><span class="sxs-lookup"><span data-stu-id="75b8d-127">An `Add` method must exist that can be matched, based on overload resolution rules, to the types that are supplied in the collection initializer.</span></span>

 <span data-ttu-id="75b8d-128">例如，下面的代码示例展示了如何使用集合初始值设定项创建 `List(Of Customer)` 集合。</span><span class="sxs-lookup"><span data-stu-id="75b8d-128">For example, the following code example shows how to create a `List(Of Customer)` collection by using a collection initializer.</span></span> <span data-ttu-id="75b8d-129">代码运行时，每个 `Customer` 对象都会传递到泛型列表的 `Add(Customer)` 方法。</span><span class="sxs-lookup"><span data-stu-id="75b8d-129">When the code is run, each `Customer` object is passed to the `Add(Customer)` method of the generic list.</span></span>

[!code-vb[VbVbalrCollectionInitializers#9](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#9)]

<span data-ttu-id="75b8d-130">下面代码示例展示了不使用集合初始值设定项的等效代码。</span><span class="sxs-lookup"><span data-stu-id="75b8d-130">The following code example shows equivalent code that does not use a collection initializer.</span></span>

[!code-vb[VbVbalrCollectionInitializers#10](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#10)]

<span data-ttu-id="75b8d-131">如果集合内的 `Add` 方法包含与 `Customer` 对象的构造函数相匹配的参数，可以在集合初始值设定项内嵌套 `Add` 方法的参数值，如下一部分所述。</span><span class="sxs-lookup"><span data-stu-id="75b8d-131">If the collection has an `Add` method that has parameters that match the constructor for the `Customer` object, you could nest parameter values for the `Add` method within collection initializers, as discussed in the next section.</span></span> <span data-ttu-id="75b8d-132">如果集合没有此类 `Add` 方法，可以创建一个作为扩展方法。</span><span class="sxs-lookup"><span data-stu-id="75b8d-132">If the collection does not have such an `Add` method, you can create one as an extension method.</span></span> <span data-ttu-id="75b8d-133">有关如何创建 `Add` 方法作为集合扩展方法的示例，请参阅[如何：创建集合初始值设定项使用的 Add 扩展方法](how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)。</span><span class="sxs-lookup"><span data-stu-id="75b8d-133">For an example of how to create an `Add` method as an extension method for a collection, see [How to: Create an Add Extension Method Used by a Collection Initializer](how-to-create-an-add-extension-method-used-by-a-collection-initializer.md).</span></span> <span data-ttu-id="75b8d-134">有关如何创建可用于集合初始值设定项的自定义集合的示例，请参阅[如何：创建集合初始值设定项使用的集合](how-to-create-a-collection-used-by-a-collection-initializer.md)。</span><span class="sxs-lookup"><span data-stu-id="75b8d-134">For an example of how to create a custom collection that can be used with a collection initializer, see [How to: Create a Collection Used by a Collection Initializer](how-to-create-a-collection-used-by-a-collection-initializer.md).</span></span>

## <a name="nesting-collection-initializers"></a><span data-ttu-id="75b8d-135">嵌套集合初始值设定项</span><span class="sxs-lookup"><span data-stu-id="75b8d-135">Nesting Collection Initializers</span></span>

<span data-ttu-id="75b8d-136">可以在集合初始值设定项中嵌套值，从而标识要创建的集合的 `Add` 方法重载。</span><span class="sxs-lookup"><span data-stu-id="75b8d-136">You can nest values within a collection initializer to identify a specific overload of an `Add` method for the collection that is being created.</span></span> <span data-ttu-id="75b8d-137">传递给 `Add` 方法的值必须用逗号隔开，并用大括号 (`{}`) 括住，就像在数组文本或集合初始值设定项中一样。</span><span class="sxs-lookup"><span data-stu-id="75b8d-137">The values passed to the `Add` method must be separated by commas and enclosed in braces (`{}`), like you would do in an array literal or collection initializer.</span></span>

<span data-ttu-id="75b8d-138">使用嵌套值创建集合时，嵌套值的每个元素都会作为参数传递到与元素类型匹配的 `Add` 方法中。</span><span class="sxs-lookup"><span data-stu-id="75b8d-138">When you create a collection by using nested values, each element of the nested value list is passed as an argument to the `Add` method that matches the element types.</span></span> <span data-ttu-id="75b8d-139">例如，下面的代码示例创建 <xref:System.Collections.Generic.Dictionary%602>，其中键类型为 `Integer`，值类型为 `String`。</span><span class="sxs-lookup"><span data-stu-id="75b8d-139">For example, the following code example creates a <xref:System.Collections.Generic.Dictionary%602> in which the keys are of type `Integer` and the values are of type `String`.</span></span> <span data-ttu-id="75b8d-140">每个嵌套值列表与 `Dictionary` 的 <xref:System.Collections.Generic.Dictionary%602.Add%2A> 方法匹配。</span><span class="sxs-lookup"><span data-stu-id="75b8d-140">Each of the nested value lists is matched to the <xref:System.Collections.Generic.Dictionary%602.Add%2A> method for the `Dictionary`.</span></span>

[!code-vb[VbVbalrCollectionInitializers#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#5)]

<span data-ttu-id="75b8d-141">上面的代码示例等效于下面的代码。</span><span class="sxs-lookup"><span data-stu-id="75b8d-141">The previous code example is equivalent to the following code.</span></span>

[!code-vb[VbVbalrCollectionInitializers#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#6)]

<span data-ttu-id="75b8d-142">只有来自第一级嵌套的嵌套值列表会发送给集合类型的 `Add` 方法。</span><span class="sxs-lookup"><span data-stu-id="75b8d-142">Only nested value lists from the first level of nesting are sent to the `Add` method for the collection type.</span></span> <span data-ttu-id="75b8d-143">深层次的嵌套会被视为数组文本，并且嵌套值列表不与任何集合的 `Add` 方法匹配。</span><span class="sxs-lookup"><span data-stu-id="75b8d-143">Deeper levels of nesting are treated as array literals and the nested value lists are not matched to the `Add` method of any collection.</span></span>

## <a name="related-topics"></a><span data-ttu-id="75b8d-144">相关主题</span><span class="sxs-lookup"><span data-stu-id="75b8d-144">Related Topics</span></span>

|<span data-ttu-id="75b8d-145">Title</span><span class="sxs-lookup"><span data-stu-id="75b8d-145">Title</span></span>|<span data-ttu-id="75b8d-146">说明</span><span class="sxs-lookup"><span data-stu-id="75b8d-146">Description</span></span>|
|---|---|
|[<span data-ttu-id="75b8d-147">如何：创建供集合初始化程序使用的 Add 扩展方法</span><span class="sxs-lookup"><span data-stu-id="75b8d-147">How to: Create an Add Extension Method Used by a Collection Initializer</span></span>](how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)|<span data-ttu-id="75b8d-148">展示了如何创建 `Add` 扩展方法，以便在集合中填充集合初始值设定项中的值。</span><span class="sxs-lookup"><span data-stu-id="75b8d-148">Shows how to create an extension method called `Add` that can be used to populate a collection with values from a collection initializer.</span></span>|
|[<span data-ttu-id="75b8d-149">如何：创建供集合初始化程序使用的集合</span><span class="sxs-lookup"><span data-stu-id="75b8d-149">How to: Create a Collection Used by a Collection Initializer</span></span>](how-to-create-a-collection-used-by-a-collection-initializer.md)|<span data-ttu-id="75b8d-150">展示了如何在实现 `IEnumerable` 的集合类中添加 `Add` 方法，从而启用集合初始值设定项。</span><span class="sxs-lookup"><span data-stu-id="75b8d-150">Shows how to enable use of a collection initializer by including an `Add` method in a collection class that implements `IEnumerable`.</span></span>|

## <a name="see-also"></a><span data-ttu-id="75b8d-151">请参阅</span><span class="sxs-lookup"><span data-stu-id="75b8d-151">See also</span></span>

- [<span data-ttu-id="75b8d-152">集合</span><span class="sxs-lookup"><span data-stu-id="75b8d-152">Collections</span></span>](../../concepts/collections.md)
- [<span data-ttu-id="75b8d-153">数组</span><span class="sxs-lookup"><span data-stu-id="75b8d-153">Arrays</span></span>](../arrays/index.md)
- [<span data-ttu-id="75b8d-154">对象初始值设定项：命名和匿名类型</span><span class="sxs-lookup"><span data-stu-id="75b8d-154">Object Initializers: Named and Anonymous Types</span></span>](../objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="75b8d-155">新建操作员</span><span class="sxs-lookup"><span data-stu-id="75b8d-155">New Operator</span></span>](../../../language-reference/operators/new-operator.md)
- [<span data-ttu-id="75b8d-156">自动实现的属性</span><span class="sxs-lookup"><span data-stu-id="75b8d-156">Auto-Implemented Properties</span></span>](../procedures/auto-implemented-properties.md)
- [<span data-ttu-id="75b8d-157">如何：在 Visual Basic 中初始化数组变量</span><span class="sxs-lookup"><span data-stu-id="75b8d-157">How to: Initialize an Array Variable in Visual Basic</span></span>](../arrays/how-to-initialize-an-array-variable.md)
- [<span data-ttu-id="75b8d-158">局部类型推理</span><span class="sxs-lookup"><span data-stu-id="75b8d-158">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="75b8d-159">匿名类型</span><span class="sxs-lookup"><span data-stu-id="75b8d-159">Anonymous Types</span></span>](../objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="75b8d-160">Visual Basic 中的 LINQ 简介</span><span class="sxs-lookup"><span data-stu-id="75b8d-160">Introduction to LINQ in Visual Basic</span></span>](../linq/introduction-to-linq.md)
- [<span data-ttu-id="75b8d-161">如何：创建项列表</span><span class="sxs-lookup"><span data-stu-id="75b8d-161">How to: Create a List of Items</span></span>](../../concepts/linq/how-to-create-a-list-of-items.md)
