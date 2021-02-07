---
description: '了解详细信息：按 (实体 SQL 分组) '
title: GROUP BY (Entity SQL)
ms.date: 03/30/2017
ms.assetid: cf4f4972-4724-4945-ba44-943a08549139
ms.openlocfilehash: 16328b46a59a2a07622cda43dce30d8b4f1d3dde
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696927"
---
# <a name="group-by-entity-sql"></a><span data-ttu-id="dab17-103">GROUP BY (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="dab17-103">GROUP BY (Entity SQL)</span></span>

<span data-ttu-id="dab17-104">指定由查询 ([SELECT](select-entity-sql.md)) 表达式返回的对象要分入的组。</span><span class="sxs-lookup"><span data-stu-id="dab17-104">Specifies groups into which objects returned by a query ([SELECT](select-entity-sql.md)) expression are to be placed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dab17-105">语法</span><span class="sxs-lookup"><span data-stu-id="dab17-105">Syntax</span></span>  
  
```sql  
[ GROUP BY aliasedExpression [ ,...n ] ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="dab17-106">参数</span><span class="sxs-lookup"><span data-stu-id="dab17-106">Arguments</span></span>  

 `aliasedExpression`  
 <span data-ttu-id="dab17-107">要对其执行分组的任何有效查询表达式。</span><span class="sxs-lookup"><span data-stu-id="dab17-107">Any valid query expression on which grouping is performed.</span></span> <span data-ttu-id="dab17-108">`expression` 可以是属性或者是引用 FROM 子句所返回的属性的非聚合表达式。</span><span class="sxs-lookup"><span data-stu-id="dab17-108">`expression` can be a property or a non-aggregate expression that references a property returned by the FROM clause.</span></span> <span data-ttu-id="dab17-109">GROUP BY 子句中的每一个表达式的求值结果必须为可比较相等性的类型。</span><span class="sxs-lookup"><span data-stu-id="dab17-109">Each expression in a GROUP BY clause must evaluate to a type that can be compared for equality.</span></span> <span data-ttu-id="dab17-110">这些类型通常为标量基元类型，如数字、字符串和日期。</span><span class="sxs-lookup"><span data-stu-id="dab17-110">These types are generally scalar primitives such as numbers, strings, and dates.</span></span> <span data-ttu-id="dab17-111">不可按集合分组。</span><span class="sxs-lookup"><span data-stu-id="dab17-111">You cannot group by a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dab17-112">备注</span><span class="sxs-lookup"><span data-stu-id="dab17-112">Remarks</span></span>  

 <span data-ttu-id="dab17-113">如果 SELECT 子句中包含聚合函数，则 \<select list> GROUP by 将计算每个组的汇总值。</span><span class="sxs-lookup"><span data-stu-id="dab17-113">If aggregate functions are included in the SELECT clause \<select list>, GROUP BY calculates a summary value for each group.</span></span> <span data-ttu-id="dab17-114">指定 GROUP BY 时，选择列表中任何非聚合表达式内的每个属性名都应包含在 GROUP BY 列表中，或者 GROUP BY 表达式必须与选择列表表达式完全匹配。</span><span class="sxs-lookup"><span data-stu-id="dab17-114">When GROUP BY is specified, either each property name in any nonaggregate expression in the select list should be included in the GROUP BY list, or the GROUP BY expression must exactly match the select list expression.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dab17-115">如果未指定 ORDER BY 子句，则使用 GROUP BY 子句返回的组没有任何特定的顺序。</span><span class="sxs-lookup"><span data-stu-id="dab17-115">If the ORDER BY clause is not specified, groups returned by the GROUP BY clause are not in any particular order.</span></span> <span data-ttu-id="dab17-116">若要指定特定的数据排序，建议始终使用 ORDER BY 子句。</span><span class="sxs-lookup"><span data-stu-id="dab17-116">To specify a particular ordering of the data, we recommend that you always use the ORDER BY clause.</span></span>  
  
 <span data-ttu-id="dab17-117">指定 GROUP BY 子句时，无论是显式指定还是隐式指定（例如，通过查询中的 HAVING 子句指定），当前作用域都将隐藏，并且将引入新的作用域。</span><span class="sxs-lookup"><span data-stu-id="dab17-117">When a GROUP BY clause is specified, either explicitly or implicitly (for example, by a HAVING clause in the query), the current scope is hidden, and a new scope is introduced.</span></span>  
  
 <span data-ttu-id="dab17-118">SELECT 子句、HAVING 子句和 ORDER BY 子句将无法再引用 FROM 子句中指定的元素名。</span><span class="sxs-lookup"><span data-stu-id="dab17-118">The SELECT clause, the HAVING clause, and the ORDER BY clause will no longer be able to refer to element names specified in the FROM clause.</span></span> <span data-ttu-id="dab17-119">您只能引用分组表达式本身。</span><span class="sxs-lookup"><span data-stu-id="dab17-119">You can only refer to the grouping expressions themselves.</span></span> <span data-ttu-id="dab17-120">为此，可以为每个分组表达式指定新的名称（别名）。</span><span class="sxs-lookup"><span data-stu-id="dab17-120">To do this, you can assign new names (aliases) to each grouping expression.</span></span> <span data-ttu-id="dab17-121">如果没有为分组表达式指定别名， [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 将尝试使用别名生成规则来生成别名，如下例中所示。</span><span class="sxs-lookup"><span data-stu-id="dab17-121">If no alias is specified for a grouping expression, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to generate one by using the alias generation rules, as illustrated in the following example.</span></span>  
  
 `SELECT g1, g2, ...gn FROM c as c1`  
  
 `GROUP BY e1 as g1, e2 as g2, ...en as gn`  
  
 <span data-ttu-id="dab17-122">GROUP BY 子句中的表达式无法引用先前在相同 GROUP BY 子句中定义的名称。</span><span class="sxs-lookup"><span data-stu-id="dab17-122">Expressions in the GROUP BY clause cannot refer to names defined earlier in the same GROUP BY clause.</span></span>  
  
 <span data-ttu-id="dab17-123">除了分组名称外，还可以在 SELECT 子句、HAVING 子句和 ORDER BY 子句中指定聚合。</span><span class="sxs-lookup"><span data-stu-id="dab17-123">In addition to grouping names, you can also specify aggregates in the SELECT clause, HAVING clause, and the ORDER BY clause.</span></span> <span data-ttu-id="dab17-124">聚合中包含的表达式针对组中的每一个元素进行求值。</span><span class="sxs-lookup"><span data-stu-id="dab17-124">An aggregate contains an expression that is evaluated for each element of the group.</span></span> <span data-ttu-id="dab17-125">聚合运算符缩减所有这些表达式的值（通常，但非总是，缩减为单个值）。</span><span class="sxs-lookup"><span data-stu-id="dab17-125">The aggregate operator reduces the values of all these expressions (usually, but not always, into a single value).</span></span> <span data-ttu-id="dab17-126">聚合表达式可以引用父作用域中可见的原始元素名，或者引用 GROUP BY 子句本身引入的任何新名称。</span><span class="sxs-lookup"><span data-stu-id="dab17-126">The aggregate expression can make references to the original element names visible in the parent scope, or to any of the new names introduced by the GROUP BY clause itself.</span></span> <span data-ttu-id="dab17-127">虽然聚合出现在 SELECT 子句、HAVING 子句和 ORDER BY 子句中，但是实际上它们是在与分组表达式相同的作用域中求值的，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="dab17-127">Although the aggregates appear in the SELECT clause, HAVING clause, and ORDER BY clause, they are actually evaluated under the same scope as the grouping expressions, as illustrated in the following example.</span></span>  
  
 `SELECT name, sum(o.Price * o.Quantity) as total`  
  
 `FROM orderLines as o`  
  
 `GROUP BY o.Product as name`  
  
 <span data-ttu-id="dab17-128">此查询使用 GROUP BY 子句生成所有已订购产品的成本报表，并按产品细分。</span><span class="sxs-lookup"><span data-stu-id="dab17-128">This query uses the GROUP BY clause to produce a report of the cost of all products ordered, broken down by product.</span></span> <span data-ttu-id="dab17-129">它在分组表达式中为产品指定名称 `name` ，然后在 SELECT 列表中引用该名称。</span><span class="sxs-lookup"><span data-stu-id="dab17-129">It gives the name `name` to the product as part of the grouping expression, and then references that name in the SELECT list.</span></span> <span data-ttu-id="dab17-130">它还在 SELECT 列表中指定聚合 `sum` ，该聚合在内部引用订单行的价格和数量。</span><span class="sxs-lookup"><span data-stu-id="dab17-130">It also specifies the aggregate `sum` in the SELECT list that internally references the price and quantity of the order line.</span></span>  
  
 <span data-ttu-id="dab17-131">每一个 GROUP By 键表达式必须至少有一个对输入作用域的引用：</span><span class="sxs-lookup"><span data-stu-id="dab17-131">Each GROUP By key expression must have at least one reference to the input scope:</span></span>  
  
```sql  
SELECT FROM Persons as P  
GROUP BY Q + P   -- GOOD  
GROUP BY Q   -- BAD  
GROUP BY 1   -- BAD, a constant is not allowed  
```  
  
 <span data-ttu-id="dab17-132">有关使用 GROUP BY 的示例，请参阅 [HAVING](having-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="dab17-132">For an example of using GROUP BY, see [HAVING](having-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dab17-133">示例</span><span class="sxs-lookup"><span data-stu-id="dab17-133">Example</span></span>  

 <span data-ttu-id="dab17-134">下面的 Entity SQL 查询使用 GROUP BY 运算符来指定查询所返回的对象的分组。</span><span class="sxs-lookup"><span data-stu-id="dab17-134">The following Entity SQL query uses the GROUP BY operator to specify groups into which objects are returned by a query.</span></span> <span data-ttu-id="dab17-135">此查询基于 AdventureWorks 销售模型。</span><span class="sxs-lookup"><span data-stu-id="dab17-135">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="dab17-136">若要编译并运行此查询，请执行下列步骤：</span><span class="sxs-lookup"><span data-stu-id="dab17-136">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="dab17-137">按照 [如何：执行返回 PrimitiveType 结果的查询](../how-to-execute-a-query-that-returns-primitivetype-results.md)中的过程进行操作。</span><span class="sxs-lookup"><span data-stu-id="dab17-137">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="dab17-138">将以下查询作为参数传递给 `ExecutePrimitiveTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="dab17-138">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#GROUPBY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#groupby)]  
  
## <a name="see-also"></a><span data-ttu-id="dab17-139">请参阅</span><span class="sxs-lookup"><span data-stu-id="dab17-139">See also</span></span>

- [<span data-ttu-id="dab17-140">实体 SQL 引用</span><span class="sxs-lookup"><span data-stu-id="dab17-140">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="dab17-141">查询表达式</span><span class="sxs-lookup"><span data-stu-id="dab17-141">Query Expressions</span></span>](query-expressions-entity-sql.md)
