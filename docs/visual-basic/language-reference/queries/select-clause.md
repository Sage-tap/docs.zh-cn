---
description: '详细了解： Select 子句 (Visual Basic) '
title: Select 子句
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySelect
helpviewer_keywords:
- Select statement [Visual Basic]
- Select clause [Visual Basic]
- queries [Visual Basic], Select
ms.assetid: 27a3f61c-5960-4692-9b91-4d0c4b6178fe
ms.openlocfilehash: 029778ce8262a93eee9a69843579523e8434eb01
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99653571"
---
# <a name="select-clause-visual-basic"></a><span data-ttu-id="b012d-103">Select 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b012d-103">Select Clause (Visual Basic)</span></span>

<span data-ttu-id="b012d-104">定义查询的结果。</span><span class="sxs-lookup"><span data-stu-id="b012d-104">Defines the result of a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b012d-105">语法</span><span class="sxs-lookup"><span data-stu-id="b012d-105">Syntax</span></span>  
  
```vb  
Select [ var1 = ] fieldName1 [, [ var2 = ] fieldName2 [...] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="b012d-106">组成部分</span><span class="sxs-lookup"><span data-stu-id="b012d-106">Parts</span></span>  

 `var1`  
 <span data-ttu-id="b012d-107">可选。</span><span class="sxs-lookup"><span data-stu-id="b012d-107">Optional.</span></span> <span data-ttu-id="b012d-108">可用于引用列表达式的结果的别名。</span><span class="sxs-lookup"><span data-stu-id="b012d-108">An alias that can be used to reference the results of the column expression.</span></span>  
  
 `fieldName1`  
 <span data-ttu-id="b012d-109">必需。</span><span class="sxs-lookup"><span data-stu-id="b012d-109">Required.</span></span> <span data-ttu-id="b012d-110">要在查询结果中返回的字段的名称。</span><span class="sxs-lookup"><span data-stu-id="b012d-110">The name of the field to return in the query result.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b012d-111">备注</span><span class="sxs-lookup"><span data-stu-id="b012d-111">Remarks</span></span>  

 <span data-ttu-id="b012d-112">您可以使用 `Select` 子句来定义要从查询返回的结果。</span><span class="sxs-lookup"><span data-stu-id="b012d-112">You can use the `Select` clause to define the results to return from a query.</span></span> <span data-ttu-id="b012d-113">这使您可以定义由查询创建的新匿名类型的成员，或指定查询所返回的命名类型的成员。</span><span class="sxs-lookup"><span data-stu-id="b012d-113">This enables you to either define the members of a new anonymous type that is created by a query, or to target the members of a named type that is returned by a query.</span></span> <span data-ttu-id="b012d-114">`Select`查询不需要子句。</span><span class="sxs-lookup"><span data-stu-id="b012d-114">The `Select` clause is not required for a query.</span></span> <span data-ttu-id="b012d-115">如果未 `Select` 指定子句，则查询将基于为当前作用域标识的范围变量的所有成员返回一个类型。</span><span class="sxs-lookup"><span data-stu-id="b012d-115">If no `Select` clause is specified, the query will return a type based on all members of the range variables identified for the current scope.</span></span> <span data-ttu-id="b012d-116">有关详细信息，请参阅[匿名类型](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="b012d-116">For more information, see [Anonymous Types](../../programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span> <span data-ttu-id="b012d-117">当查询创建命名类型时，它将返回类型为的结果， <xref:System.Collections.Generic.IEnumerable%601> 其中 `T` 是创建的类型。</span><span class="sxs-lookup"><span data-stu-id="b012d-117">When a query creates a named type, it will return a result of type <xref:System.Collections.Generic.IEnumerable%601> where `T` is the created type.</span></span>  
  
 <span data-ttu-id="b012d-118">`Select`子句可以引用当前范围内的任何变量。</span><span class="sxs-lookup"><span data-stu-id="b012d-118">The `Select` clause can reference any variables in the current scope.</span></span> <span data-ttu-id="b012d-119">这包括 `From` 子句中)  (或子句中标识的范围变量 `From` 。</span><span class="sxs-lookup"><span data-stu-id="b012d-119">This includes range variables identified in the `From` clause (or `From` clauses).</span></span> <span data-ttu-id="b012d-120">它还包括使用别名创建的任何新变量、、 `Aggregate` `Let` `Group By` 或 `Group Join` 子句，或者 `Select` 查询表达式中上一个子句中的变量。</span><span class="sxs-lookup"><span data-stu-id="b012d-120">It also includes any new variables created with an alias by the `Aggregate`, `Let`, `Group By`, or `Group Join` clauses, or variables from a previous `Select` clause in the query expression.</span></span> <span data-ttu-id="b012d-121">`Select`子句还可以包括静态值。</span><span class="sxs-lookup"><span data-stu-id="b012d-121">The `Select` clause can also include static values.</span></span> <span data-ttu-id="b012d-122">例如，下面的代码示例演示一个查询表达式，其中子句将 `Select` 查询结果定义为具有四个成员的新匿名类型： `ProductName` 、 `Price` 、 `Discount` 和 `DiscountedPrice` 。</span><span class="sxs-lookup"><span data-stu-id="b012d-122">For example, the following code example shows a query expression in which the `Select` clause defines the query result as a new anonymous type with four members: `ProductName`, `Price`, `Discount`, and `DiscountedPrice`.</span></span> <span data-ttu-id="b012d-123">`ProductName`和 `Price` 成员值取自子句中定义的产品范围变量 `From` 。</span><span class="sxs-lookup"><span data-stu-id="b012d-123">The `ProductName` and `Price` member values are taken from the product range variable that is defined in the `From` clause.</span></span> <span data-ttu-id="b012d-124">`DiscountedPrice`成员值在子句中计算 `Let` 。</span><span class="sxs-lookup"><span data-stu-id="b012d-124">The `DiscountedPrice` member value is calculated in the `Let` clause.</span></span> <span data-ttu-id="b012d-125">该 `Discount` 成员是一个静态值。</span><span class="sxs-lookup"><span data-stu-id="b012d-125">The `Discount` member is a static value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#27)]  
  
 <span data-ttu-id="b012d-126">`Select`子句为后面的查询子句引入了一组新的范围变量，并且以前的范围变量不再位于范围内。</span><span class="sxs-lookup"><span data-stu-id="b012d-126">The `Select` clause introduces a new set of range variables for subsequent query clauses, and previous range variables are no longer in scope.</span></span> <span data-ttu-id="b012d-127">`Select`查询表达式中的最后一个子句确定查询的返回值。</span><span class="sxs-lookup"><span data-stu-id="b012d-127">The last `Select` clause in a query expression determines the return value of the query.</span></span> <span data-ttu-id="b012d-128">例如，以下查询将返回总计超过500的每个客户订单的公司名称和订单 ID。</span><span class="sxs-lookup"><span data-stu-id="b012d-128">For example, the following query returns the company name and order ID for every customer order for which the total exceeds 500.</span></span> <span data-ttu-id="b012d-129">第一个 `Select` 子句标识 `Where` 子句和第二个子句的范围变量 `Select` 。</span><span class="sxs-lookup"><span data-stu-id="b012d-129">The first `Select` clause identifies the range variables for the `Where` clause and the second `Select` clause.</span></span> <span data-ttu-id="b012d-130">第二个 `Select` 子句将查询返回的值标识为新的匿名类型。</span><span class="sxs-lookup"><span data-stu-id="b012d-130">The second `Select` clause identifies the values returned by the query as a new anonymous type.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#28)]  
  
 <span data-ttu-id="b012d-131">如果 `Select` 子句标识要返回的单个项，则查询表达式返回该项的类型的集合。</span><span class="sxs-lookup"><span data-stu-id="b012d-131">If the `Select` clause identifies a single item to return, the query expression returns a collection of the type of that single item.</span></span> <span data-ttu-id="b012d-132">如果 `Select` 子句标识多个要返回的项，则查询表达式将返回基于选定项的新匿名类型的集合。</span><span class="sxs-lookup"><span data-stu-id="b012d-132">If the `Select` clause identifies multiple items to return, the query expression returns a collection of a new anonymous type, based on the selected items.</span></span> <span data-ttu-id="b012d-133">例如，下面两个查询基于子句返回两个不同类型的集合 `Select` 。</span><span class="sxs-lookup"><span data-stu-id="b012d-133">For example, the following two queries return collections of two different types based on the `Select` clause.</span></span> <span data-ttu-id="b012d-134">第一个查询以字符串的形式返回公司名称的集合。</span><span class="sxs-lookup"><span data-stu-id="b012d-134">The first query returns a collection of company names as strings.</span></span> <span data-ttu-id="b012d-135">第二个查询返回 `Customer` 使用公司名称和地址信息填充的对象集合。</span><span class="sxs-lookup"><span data-stu-id="b012d-135">The second query returns a collection of `Customer` objects populated with the company names and address information.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#29)]  
  
## <a name="example"></a><span data-ttu-id="b012d-136">示例</span><span class="sxs-lookup"><span data-stu-id="b012d-136">Example</span></span>  

 <span data-ttu-id="b012d-137">下面的查询表达式使用 `From` 子句为集合声明范围变量 `cust` `customers` 。</span><span class="sxs-lookup"><span data-stu-id="b012d-137">The following query expression uses a `From` clause to declare a range variable `cust` for the `customers` collection.</span></span> <span data-ttu-id="b012d-138">`Select`子句选择客户名称和 ID 值，并填充 `CompanyName` `CustomerID` 新范围变量的和列。</span><span class="sxs-lookup"><span data-stu-id="b012d-138">The `Select` clause selects the customer name and ID value and populates the `CompanyName` and `CustomerID` columns of the new range variable.</span></span> <span data-ttu-id="b012d-139">`For Each`语句在每个返回的对象上循环，并显示 `CompanyName` `CustomerID` 每个记录的和列。</span><span class="sxs-lookup"><span data-stu-id="b012d-139">The `For Each` statement loops over each returned object and displays the `CompanyName` and `CustomerID` columns for each record.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="b012d-140">请参阅</span><span class="sxs-lookup"><span data-stu-id="b012d-140">See also</span></span>

- [<span data-ttu-id="b012d-141">Visual Basic 中的 LINQ 简介</span><span class="sxs-lookup"><span data-stu-id="b012d-141">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="b012d-142">查询</span><span class="sxs-lookup"><span data-stu-id="b012d-142">Queries</span></span>](index.md)
- [<span data-ttu-id="b012d-143">From 子句</span><span class="sxs-lookup"><span data-stu-id="b012d-143">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="b012d-144">Where 子句</span><span class="sxs-lookup"><span data-stu-id="b012d-144">Where Clause</span></span>](where-clause.md)
- [<span data-ttu-id="b012d-145">Order By 子句</span><span class="sxs-lookup"><span data-stu-id="b012d-145">Order By Clause</span></span>](order-by-clause.md)
- [<span data-ttu-id="b012d-146">匿名类型</span><span class="sxs-lookup"><span data-stu-id="b012d-146">Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)
