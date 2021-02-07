---
description: '了解详细信息： (Visual Basic 的聚合子句) '
title: Aggregate Clause
ms.date: 08/28/2018
f1_keywords:
- vb.QueryAggregateIn
- vb.QueryAggregate
- vb.QueryAggregateInto
helpviewer_keywords:
- Aggregate clause [Visual Basic]
- Aggregate statement [Visual Basic]
- queries [Visual Basic], Aggregate
ms.assetid: 1315a814-5db6-4077-b34b-b141e11cc0eb
ms.openlocfilehash: 404cb4091bc11132450cf0d8d001ce426439ece7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700658"
---
# <a name="aggregate-clause-visual-basic"></a><span data-ttu-id="4cd1e-103">Aggregate 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4cd1e-103">Aggregate Clause (Visual Basic)</span></span>

<span data-ttu-id="4cd1e-104">将一个或多个聚合函数应用于集合。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-104">Applies one or more aggregate functions to a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cd1e-105">语法</span><span class="sxs-lookup"><span data-stu-id="4cd1e-105">Syntax</span></span>  
  
```vb  
Aggregate element [As type] In collection _  
  [, element2 [As type2] In collection2, [...]]  
  [ clause ]  
  Into expressionList  
```  
  
## <a name="parts"></a><span data-ttu-id="4cd1e-106">组成部分</span><span class="sxs-lookup"><span data-stu-id="4cd1e-106">Parts</span></span>  
  
|<span data-ttu-id="4cd1e-107">术语</span><span class="sxs-lookup"><span data-stu-id="4cd1e-107">Term</span></span>|<span data-ttu-id="4cd1e-108">定义</span><span class="sxs-lookup"><span data-stu-id="4cd1e-108">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="4cd1e-109">必需。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-109">Required.</span></span> <span data-ttu-id="4cd1e-110">用于循环访问集合中的元素的变量。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-110">Variable used to iterate through the elements of the collection.</span></span>|  
|`type`|<span data-ttu-id="4cd1e-111">可选。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-111">Optional.</span></span> <span data-ttu-id="4cd1e-112">`element` 的类型。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-112">The type of `element`.</span></span> <span data-ttu-id="4cd1e-113">如果未指定类型， `element` 则将从中推断出的类型 `collection` 。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-113">If no type is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="4cd1e-114">必需。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-114">Required.</span></span> <span data-ttu-id="4cd1e-115">引用要对其执行操作的集合。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-115">Refers to the collection to operate on.</span></span>|  
|`clause`|<span data-ttu-id="4cd1e-116">可选。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-116">Optional.</span></span> <span data-ttu-id="4cd1e-117">一个或多个查询子句（如 `Where` 子句），用于优化要将聚合子句或子句应用于的查询结果。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-117">One or more query clauses, such as a `Where` clause, to refine the query result to apply the aggregate clause or clauses to.</span></span>|  
|`expressionList`|<span data-ttu-id="4cd1e-118">必需。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-118">Required.</span></span> <span data-ttu-id="4cd1e-119">一个或多个以逗号分隔的表达式，用于标识要应用于集合的聚合函数。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-119">One or more comma-delimited expressions that identify an aggregate function to apply to the collection.</span></span> <span data-ttu-id="4cd1e-120">您可以向聚合函数应用别名，以指定查询结果的成员名称。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-120">You can apply an alias to an aggregate function to specify a member name for the query result.</span></span> <span data-ttu-id="4cd1e-121">如果未提供别名，则使用聚合函数的名称。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-121">If no alias is supplied, the name of the aggregate function is used.</span></span> <span data-ttu-id="4cd1e-122">有关示例，请参阅本主题后面的有关聚合函数的部分。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-122">For examples, see the section about aggregate functions later in this topic.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4cd1e-123">备注</span><span class="sxs-lookup"><span data-stu-id="4cd1e-123">Remarks</span></span>  

 <span data-ttu-id="4cd1e-124">`Aggregate`子句可用于在查询中包括聚合函数。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-124">The `Aggregate` clause can be used to include aggregate functions in your queries.</span></span> <span data-ttu-id="4cd1e-125">聚合函数对一组值执行检查和计算，并返回单个值。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-125">Aggregate functions perform checks and computations over a set of values and return a single value.</span></span> <span data-ttu-id="4cd1e-126">您可以使用查询结果类型的成员访问计算值。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-126">You can access the computed value by using a member of the query result type.</span></span> <span data-ttu-id="4cd1e-127">可使用的标准聚合函数包括 `All` 、 `Any` 、、 `Average` `Count` 、、、 `LongCount` `Max` `Min` 和 `Sum` 函数。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-127">The standard aggregate functions that you can use are the `All`, `Any`, `Average`, `Count`, `LongCount`, `Max`, `Min`, and `Sum` functions.</span></span> <span data-ttu-id="4cd1e-128">这些函数对熟悉 SQL 中聚合的开发人员非常熟悉。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-128">These functions are familiar to developers who are familiar with aggregates in SQL.</span></span> <span data-ttu-id="4cd1e-129">本主题的下一节将对其进行介绍。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-129">They are described in the following section of this topic.</span></span>  
  
 <span data-ttu-id="4cd1e-130">聚合函数的结果作为查询结果类型的字段包含在查询结果中。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-130">The result of an aggregate function is included in the query result as a field of the query result type.</span></span> <span data-ttu-id="4cd1e-131">您可以为聚合函数结果提供别名，以指定将保存聚合值的查询结果类型的成员名称。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-131">You can supply an alias for the aggregate function result to specify the name of the member of the query result type that will hold the aggregate value.</span></span> <span data-ttu-id="4cd1e-132">如果未提供别名，则使用聚合函数的名称。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-132">If no alias is supplied, the name of the aggregate function is used.</span></span>  
  
 <span data-ttu-id="4cd1e-133">`Aggregate`子句可以开始查询，也可以在查询中将其作为附加子句包括在内。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-133">The `Aggregate` clause can begin a query, or it can be included as an additional clause in a query.</span></span> <span data-ttu-id="4cd1e-134">如果 `Aggregate` 子句开始查询，则结果为单个值，该值是在子句中指定的聚合函数的结果 `Into` 。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-134">If the `Aggregate` clause begins a query, the result is a single value that is the result of the aggregate function specified in the `Into` clause.</span></span> <span data-ttu-id="4cd1e-135">如果在子句中指定了多个聚合函数 `Into` ，则查询将返回单一类型，该类型具有一个单独的属性，用于引用子句中每个聚合函数的结果 `Into` 。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-135">If more than one aggregate function is specified in the `Into` clause, the query returns a single type with a separate property to reference the result of each aggregate function in the `Into` clause.</span></span> <span data-ttu-id="4cd1e-136">如果 `Aggregate` 子句作为附加子句包含在查询中，则查询集合中返回的类型将有一个单独的属性来引用子句中每个聚合函数的结果 `Into` 。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-136">If the `Aggregate` clause is included as an additional clause in a query, the type returned in the query collection will have a separate property to reference the result of each aggregate function in the `Into` clause.</span></span>  
  
## <a name="aggregate-functions"></a><span data-ttu-id="4cd1e-137">聚合函数</span><span class="sxs-lookup"><span data-stu-id="4cd1e-137">Aggregate Functions</span></span>

<span data-ttu-id="4cd1e-138">下面是可以与子句一起使用的标准聚合函数 `Aggregate` 。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-138">The following are the standard aggregate functions that can be used with the `Aggregate` clause.</span></span>  
  
### <a name="all"></a><span data-ttu-id="4cd1e-139">全部</span><span class="sxs-lookup"><span data-stu-id="4cd1e-139">All</span></span>

<span data-ttu-id="4cd1e-140">`true`如果集合中的所有元素都满足指定的条件，则返回; 否则返回 `false` 。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-140">Returns `true` if all elements in the collection satisfy a specified condition; otherwise returns `false`.</span></span> <span data-ttu-id="4cd1e-141">以下是一个示例：</span><span class="sxs-lookup"><span data-stu-id="4cd1e-141">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#5)]

### <a name="any"></a><span data-ttu-id="4cd1e-142">任何</span><span class="sxs-lookup"><span data-stu-id="4cd1e-142">Any</span></span>

<span data-ttu-id="4cd1e-143">`true`如果集合中的任何元素满足指定的条件，则返回; 否则返回 `false` 。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-143">Returns `true` if any element in the collection satisfies a specified condition; otherwise returns `false`.</span></span> <span data-ttu-id="4cd1e-144">以下是一个示例：</span><span class="sxs-lookup"><span data-stu-id="4cd1e-144">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#6)]

### <a name="average"></a><span data-ttu-id="4cd1e-145">平均值</span><span class="sxs-lookup"><span data-stu-id="4cd1e-145">Average</span></span>

<span data-ttu-id="4cd1e-146">计算集合中所有元素的平均值，或为集合中的所有元素计算提供的表达式。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-146">Computes the average of all elements in the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="4cd1e-147">以下是一个示例：</span><span class="sxs-lookup"><span data-stu-id="4cd1e-147">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#7)]

### <a name="count"></a><span data-ttu-id="4cd1e-148">计数</span><span class="sxs-lookup"><span data-stu-id="4cd1e-148">Count</span></span>

<span data-ttu-id="4cd1e-149">计算集合中元素的数目。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-149">Counts the number of elements in the collection.</span></span> <span data-ttu-id="4cd1e-150">您可以提供一个可选 `Boolean` 表达式，以便仅对集合中满足条件的元素数进行计数。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-150">You can supply an optional `Boolean` expression to count only the number of elements in the collection that satisfy a condition.</span></span> <span data-ttu-id="4cd1e-151">以下是一个示例：</span><span class="sxs-lookup"><span data-stu-id="4cd1e-151">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#8)]

### <a name="group"></a><span data-ttu-id="4cd1e-152">Group</span><span class="sxs-lookup"><span data-stu-id="4cd1e-152">Group</span></span>

<span data-ttu-id="4cd1e-153">指作为 or 子句的结果进行分组的查询结果 `Group By` `Group Join` 。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-153">Refers to query results that are grouped as a result of a `Group By` or `Group Join` clause.</span></span> <span data-ttu-id="4cd1e-154">`Group`函数仅在 `Into` 或子句的子句中有效 `Group By` `Group Join` 。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-154">The `Group` function is valid only in the `Into` clause of a `Group By` or `Group Join` clause.</span></span> <span data-ttu-id="4cd1e-155">有关详细信息和示例，请参阅 [Group By 子句](group-by-clause.md) 和 [group Join 子句](group-join-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-155">For more information and examples, see [Group By Clause](group-by-clause.md) and [Group Join Clause](group-join-clause.md).</span></span>

### <a name="longcount"></a><span data-ttu-id="4cd1e-156">LongCount</span><span class="sxs-lookup"><span data-stu-id="4cd1e-156">LongCount</span></span>

<span data-ttu-id="4cd1e-157">计算集合中元素的数目。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-157">Counts the number of elements in the collection.</span></span> <span data-ttu-id="4cd1e-158">您可以提供一个可选 `Boolean` 表达式，以便仅对集合中满足条件的元素数进行计数。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-158">You can supply an optional `Boolean` expression to count only the number of elements in the collection that satisfy a condition.</span></span> <span data-ttu-id="4cd1e-159">以的形式返回结果 `Long` 。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-159">Returns the result as a `Long`.</span></span> <span data-ttu-id="4cd1e-160">有关示例，请参阅 `Count` 聚合函数。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-160">For an example, see the `Count` aggregate function.</span></span>

### <a name="max"></a><span data-ttu-id="4cd1e-161">Max</span><span class="sxs-lookup"><span data-stu-id="4cd1e-161">Max</span></span>

<span data-ttu-id="4cd1e-162">计算集合中的最大值，或为集合中的所有元素计算提供的表达式。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-162">Computes the maximum value from the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="4cd1e-163">以下是一个示例：</span><span class="sxs-lookup"><span data-stu-id="4cd1e-163">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#9)]

### <a name="min"></a><span data-ttu-id="4cd1e-164">Min</span><span class="sxs-lookup"><span data-stu-id="4cd1e-164">Min</span></span>

<span data-ttu-id="4cd1e-165">计算集合中的最小值，或为集合中的所有元素计算提供的表达式。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-165">Computes the minimum value from the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="4cd1e-166">以下是一个示例：</span><span class="sxs-lookup"><span data-stu-id="4cd1e-166">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#10)]

### <a name="sum"></a><span data-ttu-id="4cd1e-167">Sum</span><span class="sxs-lookup"><span data-stu-id="4cd1e-167">Sum</span></span>

<span data-ttu-id="4cd1e-168">计算集合中所有元素的和，或为集合中的所有元素计算提供的表达式。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-168">Computes the sum of all elements in the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="4cd1e-169">以下是一个示例：</span><span class="sxs-lookup"><span data-stu-id="4cd1e-169">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#15)]

## <a name="example"></a><span data-ttu-id="4cd1e-170">示例</span><span class="sxs-lookup"><span data-stu-id="4cd1e-170">Example</span></span>  

<span data-ttu-id="4cd1e-171">下面的示例演示如何使用子句将 `Aggregate` 聚合函数应用于查询结果。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-171">The following example shows how to use the `Aggregate` clause to apply aggregate functions to a query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#4)]  
  
## <a name="creating-user-defined-aggregate-functions"></a><span data-ttu-id="4cd1e-172">创建 User-Defined 聚合函数</span><span class="sxs-lookup"><span data-stu-id="4cd1e-172">Creating User-Defined Aggregate Functions</span></span>

 <span data-ttu-id="4cd1e-173">您可以通过向类型添加扩展方法，在查询表达式中包含您自己的自定义聚合函数 <xref:System.Collections.Generic.IEnumerable%601> 。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-173">You can include your own custom aggregate functions in a query expression by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> type.</span></span> <span data-ttu-id="4cd1e-174">然后，您的自定义方法可以对引用了聚合函数的可枚举集合执行计算或操作。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-174">Your custom method can then perform a calculation or operation on the enumerable collection that has referenced your aggregate function.</span></span> <span data-ttu-id="4cd1e-175">有关扩展方法的详细信息，请参阅[扩展方法](../../programming-guide/language-features/procedures/extension-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-175">For more information about extension methods, see [Extension Methods](../../programming-guide/language-features/procedures/extension-methods.md).</span></span>  
  
 <span data-ttu-id="4cd1e-176">例如，下面的示例显示了一个自定义聚合函数，该函数计算数字集合的中间值。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-176">For example, the following example shows a custom aggregate function that calculates the median value of a collection of numbers.</span></span> <span data-ttu-id="4cd1e-177">扩展方法有两个重载 `Median` 。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-177">There are two overloads of the `Median` extension method.</span></span> <span data-ttu-id="4cd1e-178">第一次重载接受类型为的集合作为输入 `IEnumerable(Of Double)` 。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-178">The first overload accepts, as input, a collection of type `IEnumerable(Of Double)`.</span></span> <span data-ttu-id="4cd1e-179">如果为 `Median` 类型的查询字段调用聚合函数 `Double` ，则将调用此方法。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-179">If the `Median` aggregate function is called for a query field of type `Double`, this method will be called.</span></span> <span data-ttu-id="4cd1e-180">方法的第二个重载 `Median` 可传递到任何泛型类型。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-180">The second overload of the `Median` method can be passed any generic type.</span></span> <span data-ttu-id="4cd1e-181">方法的泛型重载 `Median` 使用第二个参数，该参数引用 `Func(Of T, Double)` lambda 表达式，以便为集合中的类型 (值投影) 为类型的相应值 `Double` 。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-181">The generic overload of the `Median` method takes a second parameter that references the `Func(Of T, Double)` lambda expression to project a value for a type (from a collection) as the corresponding value of type `Double`.</span></span> <span data-ttu-id="4cd1e-182">然后，它将中间值的计算委托给该方法的其他重载 `Median` 。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-182">It then delegates the calculation of the median value to the other overload of the `Median` method.</span></span> <span data-ttu-id="4cd1e-183">有关 lambda 表达式的详细信息，请参阅 [Lambda 表达式](../../programming-guide/language-features/procedures/lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-183">For more information about lambda expressions, see [Lambda Expressions](../../programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#18)]  
  
 <span data-ttu-id="4cd1e-184">下面的示例演示了 `Median` 在类型的集合上调用聚合函数的示例查询， `Integer` 以及类型的集合 `Double` 。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-184">The following example shows sample queries that call the `Median` aggregate function on a collection of type `Integer`, and a collection of type `Double`.</span></span> <span data-ttu-id="4cd1e-185">对类型为的集合调用聚合函数的查询将 `Median` `Double` 调用接受的 `Median` 方法（作为输入的集合）的重载 `Double` 。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-185">The query that calls the `Median` aggregate function on the collection of type `Double` calls the overload of the `Median` method that accepts, as input, a collection of type `Double`.</span></span> <span data-ttu-id="4cd1e-186">对 `Median` 类型集合调用聚合函数的查询将 `Integer` 调用方法的泛型重载 `Median` 。</span><span class="sxs-lookup"><span data-stu-id="4cd1e-186">The query that calls the `Median` aggregate function on the collection of type `Integer` calls the generic overload of the `Median` method.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="4cd1e-187">请参阅</span><span class="sxs-lookup"><span data-stu-id="4cd1e-187">See also</span></span>

- [<span data-ttu-id="4cd1e-188">Visual Basic 中的 LINQ 简介</span><span class="sxs-lookup"><span data-stu-id="4cd1e-188">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="4cd1e-189">查询</span><span class="sxs-lookup"><span data-stu-id="4cd1e-189">Queries</span></span>](index.md)
- [<span data-ttu-id="4cd1e-190">Select 子句</span><span class="sxs-lookup"><span data-stu-id="4cd1e-190">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="4cd1e-191">From 子句</span><span class="sxs-lookup"><span data-stu-id="4cd1e-191">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="4cd1e-192">Where 子句</span><span class="sxs-lookup"><span data-stu-id="4cd1e-192">Where Clause</span></span>](where-clause.md)
- [<span data-ttu-id="4cd1e-193">Group By 子句</span><span class="sxs-lookup"><span data-stu-id="4cd1e-193">Group By Clause</span></span>](group-by-clause.md)
