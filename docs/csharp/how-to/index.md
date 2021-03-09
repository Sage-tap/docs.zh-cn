---
title: 操作指南（C# 指南）
description: 快速提示及重点短代码示例集合
ms.date: 12/20/2017
ms.openlocfilehash: dae10bf0019c283f568c4850d3bfa0abad6df85a
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2021
ms.locfileid: "102258190"
---
# <a name="how-to-c"></a><span data-ttu-id="9f236-103">操作指南 (C#)</span><span class="sxs-lookup"><span data-stu-id="9f236-103">How to (C#)</span></span>

<span data-ttu-id="9f236-104">在《C# 指南》中的“操作指南”部分，你可快速了解常见问题的答案。</span><span class="sxs-lookup"><span data-stu-id="9f236-104">In the How to section of the C# Guide, you can find quick answers to common questions.</span></span> <span data-ttu-id="9f236-105">在某些情况下，可能会在多个部分列出相关文章。</span><span class="sxs-lookup"><span data-stu-id="9f236-105">In some cases, articles may be listed in multiple sections.</span></span> <span data-ttu-id="9f236-106">我们希望用户可从多个搜索路径找到操作指南。</span><span class="sxs-lookup"><span data-stu-id="9f236-106">We wanted to make them easy to find for multiple search paths.</span></span>

## <a name="general-c-concepts"></a><span data-ttu-id="9f236-107">C# 一般概念</span><span class="sxs-lookup"><span data-stu-id="9f236-107">General C# concepts</span></span>

<span data-ttu-id="9f236-108">此处介绍了 C# 开发者在实践中经常会用到的几个提示和技巧：</span><span class="sxs-lookup"><span data-stu-id="9f236-108">There are several tips and tricks that are common C# developer practices:</span></span>

- <span data-ttu-id="9f236-109">[使用对象初始值设定项初始化对象](../programming-guide/classes-and-structs/how-to-initialize-objects-by-using-an-object-initializer.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-109">[Initialize objects using an object initializer](../programming-guide/classes-and-structs/how-to-initialize-objects-by-using-an-object-initializer.md).</span></span>
- <span data-ttu-id="9f236-110">[了解向方法传递结构和传递类的区别](../programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-110">[Learn the differences between passing a struct and a class to a method](../programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md).</span></span>
- <span data-ttu-id="9f236-111">[使用运算符重载](../language-reference/operators/operator-overloading.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-111">[Use operator overloading](../language-reference/operators/operator-overloading.md).</span></span>
- <span data-ttu-id="9f236-112">[实现和调用自定义扩展方法](../programming-guide/classes-and-structs/how-to-implement-and-call-a-custom-extension-method.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-112">[Implement and call a custom extension method](../programming-guide/classes-and-structs/how-to-implement-and-call-a-custom-extension-method.md).</span></span>
- <span data-ttu-id="9f236-113">即使是 C# 程序员，也可能需要[使用 Visual Basic `My` 命名空间](../programming-guide/namespaces/how-to-use-the-my-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-113">Even C# programmers may want to [use the `My` namespace from Visual Basic](../programming-guide/namespaces/how-to-use-the-my-namespace.md).</span></span>
- <span data-ttu-id="9f236-114">[使用扩展方法创建新 `enum` 类型方法](../programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-114">[Create a new method for an `enum` type using extension methods](../programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).</span></span>

### <a name="class-record-and-struct-members"></a><span data-ttu-id="9f236-115">类、记录和结构成员</span><span class="sxs-lookup"><span data-stu-id="9f236-115">Class, record, and struct members</span></span>

<span data-ttu-id="9f236-116">创建类、记录和结构来实现程序。</span><span class="sxs-lookup"><span data-stu-id="9f236-116">You create classes, records, and structs to implement your program.</span></span> <span data-ttu-id="9f236-117">编写类、记录或结构时常会使用这些方法。</span><span class="sxs-lookup"><span data-stu-id="9f236-117">These techniques are commonly used when writing classes, records, or structs.</span></span>

- <span data-ttu-id="9f236-118">[声明自动实现的属性](../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-118">[Declare auto implemented properties](../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span></span>
- <span data-ttu-id="9f236-119">[声明和使用读/写属性](../programming-guide/classes-and-structs/how-to-declare-and-use-read-write-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-119">[Declare and use read/write properties](../programming-guide/classes-and-structs/how-to-declare-and-use-read-write-properties.md).</span></span>
- <span data-ttu-id="9f236-120">[定义常量](../programming-guide/classes-and-structs/how-to-define-constants.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-120">[Define constants](../programming-guide/classes-and-structs/how-to-define-constants.md).</span></span>
- <span data-ttu-id="9f236-121">[替代 `ToString` 方法以提供字符串输出](../programming-guide/classes-and-structs/how-to-override-the-tostring-method.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-121">[Override the `ToString` method to provide string output](../programming-guide/classes-and-structs/how-to-override-the-tostring-method.md).</span></span>
- <span data-ttu-id="9f236-122">[定义抽象属性](../programming-guide/classes-and-structs/how-to-define-abstract-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-122">[Define abstract properties](../programming-guide/classes-and-structs/how-to-define-abstract-properties.md).</span></span>
- <span data-ttu-id="9f236-123">[使用 XML 文档功能记录代码](../programming-guide/xmldoc/how-to-use-the-xml-documentation-features.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-123">[Use the xml documentation features to document your code](../programming-guide/xmldoc/how-to-use-the-xml-documentation-features.md).</span></span>
- <span data-ttu-id="9f236-124">[显式实现接口成员](../programming-guide/interfaces/how-to-explicitly-implement-interface-members.md)，使公共接口保持简洁。</span><span class="sxs-lookup"><span data-stu-id="9f236-124">[Explicitly implement interface members](../programming-guide/interfaces/how-to-explicitly-implement-interface-members.md) to keep your public interface concise.</span></span>
- <span data-ttu-id="9f236-125">[显式实现两个接口的成员](../programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-125">[Explicitly implement members of two interfaces](../programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md).</span></span>

### <a name="working-with-collections"></a><span data-ttu-id="9f236-126">使用集合</span><span class="sxs-lookup"><span data-stu-id="9f236-126">Working with collections</span></span>

<span data-ttu-id="9f236-127">这些文章有助于了解如何使用数据集合。</span><span class="sxs-lookup"><span data-stu-id="9f236-127">These articles help you work with collections of data.</span></span>

- <span data-ttu-id="9f236-128">[使用集合初始值设定项初始化字典](../programming-guide/classes-and-structs/how-to-initialize-a-dictionary-with-a-collection-initializer.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-128">[Initialize a dictionary with a collection initializer](../programming-guide/classes-and-structs/how-to-initialize-a-dictionary-with-a-collection-initializer.md).</span></span>

## <a name="working-with-strings"></a><span data-ttu-id="9f236-129">处理字符串</span><span class="sxs-lookup"><span data-stu-id="9f236-129">Working with strings</span></span>

<span data-ttu-id="9f236-130">字符串是用于显示或操作文本的基本数据类型。</span><span class="sxs-lookup"><span data-stu-id="9f236-130">Strings are the fundamental data type used to display or manipulate text.</span></span> <span data-ttu-id="9f236-131">这些文章介绍了字符串的常见处理方法。</span><span class="sxs-lookup"><span data-stu-id="9f236-131">These articles demonstrate common practices with strings.</span></span>

- <span data-ttu-id="9f236-132">[比较字符串](compare-strings.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-132">[Compare strings](compare-strings.md).</span></span>
- <span data-ttu-id="9f236-133">[修改字符串内容](modify-string-contents.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-133">[Modify the contents of a string](modify-string-contents.md).</span></span>
- <span data-ttu-id="9f236-134">[确定字符串是否表示数字](../programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-134">[Determine if a string represents a number](../programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md).</span></span>
- <span data-ttu-id="9f236-135">[使用 `String.Split` 分隔字符串](parse-strings-using-split.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-135">[Use `String.Split` to separate strings](parse-strings-using-split.md).</span></span>
- <span data-ttu-id="9f236-136">[将多个字符串合并为一个字符串](concatenate-multiple-strings.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-136">[Combine multiple strings into one](concatenate-multiple-strings.md).</span></span>
- <span data-ttu-id="9f236-137">[在字符串中搜索文本](search-strings.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-137">[Search for text in a string](search-strings.md).</span></span>

## <a name="convert-between-types"></a><span data-ttu-id="9f236-138">在类型间转换</span><span class="sxs-lookup"><span data-stu-id="9f236-138">Convert between types</span></span>

<span data-ttu-id="9f236-139">你可能需要将对象转换为其他类型。</span><span class="sxs-lookup"><span data-stu-id="9f236-139">You may need to convert an object to a different type.</span></span>

- <span data-ttu-id="9f236-140">[确定字符串是否表示数字](../programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-140">[Determine if a string represents a number](../programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md).</span></span>
- <span data-ttu-id="9f236-141">[在表示十六进制数的字符串和数字之间进行转换](../programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-141">[Convert between strings that represent hexadecimal numbers and the number](../programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md).</span></span>
- <span data-ttu-id="9f236-142">[将字符串转换为 `DateTime`](../../standard/base-types/parsing-datetime.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-142">[Convert a string to a `DateTime`](../../standard/base-types/parsing-datetime.md).</span></span>
- <span data-ttu-id="9f236-143">[将字节数组转换为 int](../programming-guide/types/how-to-convert-a-byte-array-to-an-int.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-143">[Convert a byte array to an int](../programming-guide/types/how-to-convert-a-byte-array-to-an-int.md).</span></span>
- <span data-ttu-id="9f236-144">[将字符串转换为数字](../programming-guide/types/how-to-convert-a-string-to-a-number.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-144">[Convert a string to a number](../programming-guide/types/how-to-convert-a-string-to-a-number.md).</span></span>
- <span data-ttu-id="9f236-145">[使用模式匹配、`as` 和 `is` 运算符安全强制转换为其他类型](safely-cast-using-pattern-matching-is-and-as-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-145">[Use pattern matching, the `as` and `is` operators to safely cast to a different type](safely-cast-using-pattern-matching-is-and-as-operators.md).</span></span>
- <span data-ttu-id="9f236-146">[定义自定义类型转换](../language-reference/operators/user-defined-conversion-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-146">[Define custom type conversions](../language-reference/operators/user-defined-conversion-operators.md).</span></span>
- <span data-ttu-id="9f236-147">[确定类型是否为可为 null 的值类型](../language-reference/builtin-types/nullable-value-types.md#how-to-identify-a-nullable-value-type)。</span><span class="sxs-lookup"><span data-stu-id="9f236-147">[Determine if a type is a nullable value type](../language-reference/builtin-types/nullable-value-types.md#how-to-identify-a-nullable-value-type).</span></span>
- <span data-ttu-id="9f236-148">[在可为 null 和不可为 null 的值类型之间转换](../language-reference/builtin-types/nullable-value-types.md#conversion-from-a-nullable-value-type-to-an-underlying-type)。</span><span class="sxs-lookup"><span data-stu-id="9f236-148">[Convert between nullable and non-nullable value types](../language-reference/builtin-types/nullable-value-types.md#conversion-from-a-nullable-value-type-to-an-underlying-type).</span></span>

## <a name="equality-and-ordering-comparisons"></a><span data-ttu-id="9f236-149">相等比较和排序比较</span><span class="sxs-lookup"><span data-stu-id="9f236-149">Equality and ordering comparisons</span></span>

<span data-ttu-id="9f236-150">可创建类型来定义自己的相等规则，或者定义该类型对象间的自然顺序。</span><span class="sxs-lookup"><span data-stu-id="9f236-150">You may create types that define their own rules for equality or define a natural ordering among objects of that type.</span></span>

- <span data-ttu-id="9f236-151">[基于引用的相等性测试](../programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-151">[Test for reference-based equality](../programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md).</span></span>
- <span data-ttu-id="9f236-152">[为类型定义基于值的相等](../programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-152">[Define value-based equality for a type](../programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md).</span></span>

## <a name="exception-handling"></a><span data-ttu-id="9f236-153">异常处理</span><span class="sxs-lookup"><span data-stu-id="9f236-153">Exception handling</span></span>

<span data-ttu-id="9f236-154">.NET 程序通过引发异常报告方法未能成功完成其任务。</span><span class="sxs-lookup"><span data-stu-id="9f236-154">.NET programs report that methods did not successfully complete their work by throwing exceptions.</span></span> <span data-ttu-id="9f236-155">通过这些文章可了解如何处理异常。</span><span class="sxs-lookup"><span data-stu-id="9f236-155">In these articles you'll learn to work with exceptions.</span></span>

- <span data-ttu-id="9f236-156">[使用 `try` 和 `catch` 处理异常](../programming-guide/exceptions/how-to-handle-an-exception-using-try-catch.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-156">[Handle exceptions using `try` and `catch`](../programming-guide/exceptions/how-to-handle-an-exception-using-try-catch.md).</span></span>
- <span data-ttu-id="9f236-157">[使用 `finally` 子句清理资源](../programming-guide/exceptions/how-to-execute-cleanup-code-using-finally.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-157">[Cleanup resources using `finally` clauses](../programming-guide/exceptions/how-to-execute-cleanup-code-using-finally.md).</span></span>
- <span data-ttu-id="9f236-158">[从非 CLS （公共语言规范）异常中恢复](../programming-guide/exceptions/how-to-catch-a-non-cls-exception.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-158">[Recover from non-CLS (Common Language Specification) exceptions](../programming-guide/exceptions/how-to-catch-a-non-cls-exception.md).</span></span>

## <a name="delegates-and-events"></a><span data-ttu-id="9f236-159">委托和事件</span><span class="sxs-lookup"><span data-stu-id="9f236-159">Delegates and events</span></span>

<span data-ttu-id="9f236-160">委托和事件为涉及松散耦合代码块的策略提供了功能。</span><span class="sxs-lookup"><span data-stu-id="9f236-160">Delegates and events provide a capability for strategies that involve loosely coupled blocks of code.</span></span>

- <span data-ttu-id="9f236-161">[声明、实例化和使用委托](../programming-guide/delegates/how-to-declare-instantiate-and-use-a-delegate.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-161">[Declare, instantiate, and use delegates](../programming-guide/delegates/how-to-declare-instantiate-and-use-a-delegate.md).</span></span>
- <span data-ttu-id="9f236-162">[合并多播委托](../programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-162">[Combine multicast delegates](../programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md).</span></span>

<span data-ttu-id="9f236-163">事件提供发布或订阅通知的机制。</span><span class="sxs-lookup"><span data-stu-id="9f236-163">Events provide a mechanism to publish or subscribe to notifications.</span></span>

- <span data-ttu-id="9f236-164">[订阅和取消订阅事件](../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-164">[Subscribe and unsubscribe from events](../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>
- <span data-ttu-id="9f236-165">[实现接口中声明的事件](../programming-guide/events/how-to-implement-interface-events.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-165">[Implement events declared in interfaces](../programming-guide/events/how-to-implement-interface-events.md).</span></span>
- <span data-ttu-id="9f236-166">[代码发布事件时，遵循 .NET 准则](../programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-166">[Conform to .NET guidelines when your code publishes events](../programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md).</span></span>
- <span data-ttu-id="9f236-167">[从派生类中引发在基类中定义的事件](../programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-167">[Raise events defined in base classes from derived classes](../programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md).</span></span>
- <span data-ttu-id="9f236-168">[实现自定义事件访问器](../programming-guide/events/how-to-implement-custom-event-accessors.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-168">[Implement custom event accessors](../programming-guide/events/how-to-implement-custom-event-accessors.md).</span></span>

## <a name="linq-practices"></a><span data-ttu-id="9f236-169">LINQ 做法</span><span class="sxs-lookup"><span data-stu-id="9f236-169">LINQ practices</span></span>

<span data-ttu-id="9f236-170">通过 LINQ 可编写代码来查询任何支持 LINQ 查询表达式模式的数据源。</span><span class="sxs-lookup"><span data-stu-id="9f236-170">LINQ enables you to write code to query any data source that supports the LINQ query expression pattern.</span></span> <span data-ttu-id="9f236-171">这些文章有助于你理解该模式并使用不同的数据源。</span><span class="sxs-lookup"><span data-stu-id="9f236-171">These articles help you understand the pattern and work with different data sources.</span></span>

- <span data-ttu-id="9f236-172">[查询集合](../programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-172">[Query a collection](../programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md).</span></span>
- <span data-ttu-id="9f236-173">[在查询中使用 Lambda 表达式](../programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-in-a-query.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-173">[Use lambda expressions in a query](../programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-in-a-query.md).</span></span>
- <span data-ttu-id="9f236-174">[在查询表达式中使用 `var`](../programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-174">[Use `var` in query expressions](../programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).</span></span>
- <span data-ttu-id="9f236-175">[从查询返回元素属性的子集](../programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-175">[Return subsets of element properties from a query](../programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md).</span></span>
- <span data-ttu-id="9f236-176">[编写使用复杂筛选的查询](../../standard/linq/write-queries-complex-filtering.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-176">[Write queries with complex filtering](../../standard/linq/write-queries-complex-filtering.md).</span></span>
- <span data-ttu-id="9f236-177">[对数据源的元素排序](../../standard/linq/sort-elements.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-177">[Sort elements of a data source](../../standard/linq/sort-elements.md).</span></span>
- <span data-ttu-id="9f236-178">[对多个键上的元素排序](../../standard/linq/sort-elements-multiple-keys.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-178">[Sort elements on multiple keys](../../standard/linq/sort-elements-multiple-keys.md).</span></span>
- <span data-ttu-id="9f236-179">[控制投影的类型](../../standard/linq/control-type-projection.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-179">[Control the type of a projection](../../standard/linq/control-type-projection.md).</span></span>
- <span data-ttu-id="9f236-180">[对某个值在源序列中出现的次数进行计数](../programming-guide/concepts/linq/how-to-count-occurrences-of-a-word-in-a-string-linq.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-180">[Count occurrences of a value in a source sequence](../programming-guide/concepts/linq/how-to-count-occurrences-of-a-word-in-a-string-linq.md).</span></span>
- <span data-ttu-id="9f236-181">[计算中间值](../../standard/linq/calculate-intermediate-values.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-181">[Calculate intermediate values](../../standard/linq/calculate-intermediate-values.md).</span></span>
- <span data-ttu-id="9f236-182">[合并来自多个源的数据](../programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-182">[Merge data from multiple sources](../programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md).</span></span>
- <span data-ttu-id="9f236-183">[查找两个序列之间的差集](../programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-183">[Find the set difference between two sequences](../programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md).</span></span>
- <span data-ttu-id="9f236-184">[调试空查询结果](../../standard/linq/debug-empty-query-results-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-184">[Debug empty query results](../../standard/linq/debug-empty-query-results-sets.md).</span></span>
- <span data-ttu-id="9f236-185">[向 LINQ 查询添加自定义方法](../programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-185">[Add custom methods to LINQ queries](../programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md).</span></span>

## <a name="multiple-threads-and-async-processing"></a><span data-ttu-id="9f236-186">多线程和异步处理</span><span class="sxs-lookup"><span data-stu-id="9f236-186">Multiple threads and async processing</span></span>

<span data-ttu-id="9f236-187">新式程序常使用异步操作。</span><span class="sxs-lookup"><span data-stu-id="9f236-187">Modern programs often use asynchronous operations.</span></span> <span data-ttu-id="9f236-188">这些文章可帮助你了解如何使用这些方法。</span><span class="sxs-lookup"><span data-stu-id="9f236-188">These articles will help you learn to use these techniques.</span></span>

- <span data-ttu-id="9f236-189">[使用 `System.Threading.Tasks.Task.WhenAll` 提高异步性能](../programming-guide/concepts/async/index.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-189">[Improve async performance using `System.Threading.Tasks.Task.WhenAll`](../programming-guide/concepts/async/index.md).</span></span>
- <span data-ttu-id="9f236-190">[使用 `async` 和 `await` 并行发出多个 Web 请求](../programming-guide/concepts/async/index.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-190">[Make multiple web requests in parallel using `async` and `await`](../programming-guide/concepts/async/index.md).</span></span>
- <span data-ttu-id="9f236-191">[使用线程池](../../standard/threading/the-managed-thread-pool.md#using-the-thread-pool)。</span><span class="sxs-lookup"><span data-stu-id="9f236-191">[Use a thread pool](../../standard/threading/the-managed-thread-pool.md#using-the-thread-pool).</span></span>

## <a name="command-line-args-to-your-program"></a><span data-ttu-id="9f236-192">程序的命令行参数</span><span class="sxs-lookup"><span data-stu-id="9f236-192">Command line args to your program</span></span>

<span data-ttu-id="9f236-193">通常情况下，C# 程序具有命令行参数。</span><span class="sxs-lookup"><span data-stu-id="9f236-193">Typically, C# programs have command line arguments.</span></span> <span data-ttu-id="9f236-194">通过这些文章可了解如何访问和处理这些命令行参数。</span><span class="sxs-lookup"><span data-stu-id="9f236-194">These articles teach you to access and process those command line arguments.</span></span>

- <span data-ttu-id="9f236-195">[使用 `for` 检索所有命令行参数](../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)。</span><span class="sxs-lookup"><span data-stu-id="9f236-195">[Retrieve all command line arguments with `for`](../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md).</span></span>
