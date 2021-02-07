---
description: '了解详细信息，如 (实体 SQL) '
title: LIKE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8300e6d2-875b-481e-9ef4-e1e7c12d46fa
ms.openlocfilehash: 932ddfcf8a8ab8b32f6a097f92ff2979e32239da
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748266"
---
# <a name="like-entity-sql"></a><span data-ttu-id="3ea9f-103">LIKE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="3ea9f-103">LIKE (Entity SQL)</span></span>

<span data-ttu-id="3ea9f-104">确定特定字符 `String` 是否与指定模式相匹配。</span><span class="sxs-lookup"><span data-stu-id="3ea9f-104">Determines whether a specific character `String` matches a specified pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ea9f-105">语法</span><span class="sxs-lookup"><span data-stu-id="3ea9f-105">Syntax</span></span>  
  
```sql  
match [NOT] LIKE pattern [ESCAPE escape]  
```  
  
## <a name="arguments"></a><span data-ttu-id="3ea9f-106">参数</span><span class="sxs-lookup"><span data-stu-id="3ea9f-106">Arguments</span></span>  

 `match`  
 <span data-ttu-id="3ea9f-107">计算结果为 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 的 `String` 表达式。</span><span class="sxs-lookup"><span data-stu-id="3ea9f-107">An [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expression that evaluates to a `String`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="3ea9f-108">要与指定 `String` 匹配的模式。</span><span class="sxs-lookup"><span data-stu-id="3ea9f-108">A pattern to match to the specified `String`.</span></span>  
  
 `escape`  
 <span data-ttu-id="3ea9f-109">一个转义符。</span><span class="sxs-lookup"><span data-stu-id="3ea9f-109">An escape character.</span></span>  
  
 <span data-ttu-id="3ea9f-110">NOT</span><span class="sxs-lookup"><span data-stu-id="3ea9f-110">NOT</span></span>  
 <span data-ttu-id="3ea9f-111">指定对 LIKE 的结果取反。</span><span class="sxs-lookup"><span data-stu-id="3ea9f-111">Specifies that the result of LIKE be negated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3ea9f-112">返回值</span><span class="sxs-lookup"><span data-stu-id="3ea9f-112">Return Value</span></span>  

 <span data-ttu-id="3ea9f-113">如果 `true` 与模式相匹配，则为 `string`；否则为 `false`。</span><span class="sxs-lookup"><span data-stu-id="3ea9f-113">`true` if the `string` matches the pattern; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3ea9f-114">备注</span><span class="sxs-lookup"><span data-stu-id="3ea9f-114">Remarks</span></span>  

 <span data-ttu-id="3ea9f-115">使用 LIKE 运算符的 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 表达式的计算方式十分类似于将相等性用作筛选条件的表达式。</span><span class="sxs-lookup"><span data-stu-id="3ea9f-115">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] expressions that use the LIKE operator are evaluated in much the same way as expressions that use equality as the filter criteria.</span></span> <span data-ttu-id="3ea9f-116">但是，使用 LIKE 运算符的 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 表达式可以包含文本和通配符。</span><span class="sxs-lookup"><span data-stu-id="3ea9f-116">However, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expressions that use the LIKE operator can include both literals and wildcard characters.</span></span>  
  
 <span data-ttu-id="3ea9f-117">下表说明模式 `string` 的语法。</span><span class="sxs-lookup"><span data-stu-id="3ea9f-117">The following table describes the syntax of the pattern `string`.</span></span>  
  
|<span data-ttu-id="3ea9f-118">通配符</span><span class="sxs-lookup"><span data-stu-id="3ea9f-118">Wildcard Character</span></span>|<span data-ttu-id="3ea9f-119">说明</span><span class="sxs-lookup"><span data-stu-id="3ea9f-119">Description</span></span>|<span data-ttu-id="3ea9f-120">示例</span><span class="sxs-lookup"><span data-stu-id="3ea9f-120">Example</span></span>|  
|------------------------|-----------------|-------------|  
|%|<span data-ttu-id="3ea9f-121">包含零个或零个以上字符的任何 `string`。</span><span class="sxs-lookup"><span data-stu-id="3ea9f-121">Any `string` of zero or more characters.</span></span>|<span data-ttu-id="3ea9f-122">`title like '%computer%'``"computer"`在标题中的任意位置查找所有标题。</span><span class="sxs-lookup"><span data-stu-id="3ea9f-122">`title like '%computer%'` finds all titles with the word `"computer"` anywhere in the title.</span></span>|  
|<span data-ttu-id="3ea9f-123">_（下划线）</span><span class="sxs-lookup"><span data-stu-id="3ea9f-123">_ (underscore)</span></span>|<span data-ttu-id="3ea9f-124">任何单个字符。</span><span class="sxs-lookup"><span data-stu-id="3ea9f-124">Any single character.</span></span>|<span data-ttu-id="3ea9f-125">`firstname like '_ean'` 查找以开头的所有四个字母的名字 `"ean` ，如 "Dean" 或小红。</span><span class="sxs-lookup"><span data-stu-id="3ea9f-125">`firstname like '_ean'` finds all four-letter first names that end with `"ean`," such as Dean or Sean.</span></span>|  
|<span data-ttu-id="3ea9f-126">[ ]</span><span class="sxs-lookup"><span data-stu-id="3ea9f-126">[ ]</span></span>|<span data-ttu-id="3ea9f-127">指定范围 ([a-f]) 或集合 ([abcdef]) 中的任意单个字符。</span><span class="sxs-lookup"><span data-stu-id="3ea9f-127">Any single character in the specified range ([a-f]) or set ([abcdef]).</span></span>|<span data-ttu-id="3ea9f-128">`lastname like '[C-P]arsen'` 查找以 "arsen" 结尾并以 C 和 P 之间的任何单个字符开头的姓氏（如 Carsen 或 Larsen）。</span><span class="sxs-lookup"><span data-stu-id="3ea9f-128">`lastname like '[C-P]arsen'` finds last names ending with "arsen" and beginning with any single character between C and P, such as Carsen or Larsen.</span></span>|  
|<span data-ttu-id="3ea9f-129">[^]</span><span class="sxs-lookup"><span data-stu-id="3ea9f-129">[^]</span></span>|<span data-ttu-id="3ea9f-130">不在指定范围 ([^a-f]) 或集合 ([^abcdef]) 中的任意单个字符。</span><span class="sxs-lookup"><span data-stu-id="3ea9f-130">Any single character not in the specified range ([^a-f]) or set ([^abcdef]).</span></span>|<span data-ttu-id="3ea9f-131">`lastname like 'de[^l]%'` 查找所有以 "de" 开头的名称，并且不包含 "l" 作为下一字母。</span><span class="sxs-lookup"><span data-stu-id="3ea9f-131">`lastname like 'de[^l]%'` finds all last names that begin with "de" and do not include "l" as the following letter.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="3ea9f-132">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] LIKE 运算符和 ESCAPE 子句不适用于 `System.DateTime` 或 `System.Guid` 值。</span><span class="sxs-lookup"><span data-stu-id="3ea9f-132">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] LIKE operator and ESCAPE clause cannot be applied to `System.DateTime` or `System.Guid` values.</span></span>  
  
 <span data-ttu-id="3ea9f-133">LIKE 支持 ASCII 模式匹配和 Unicode 模式匹配。</span><span class="sxs-lookup"><span data-stu-id="3ea9f-133">LIKE supports ASCII pattern matching and Unicode pattern matching.</span></span> <span data-ttu-id="3ea9f-134">当所有参数都为 ASCII 字符时，将执行 ASCII 模式匹配。</span><span class="sxs-lookup"><span data-stu-id="3ea9f-134">When all parameters are ASCII characters, ASCII pattern matching is performed.</span></span> <span data-ttu-id="3ea9f-135">如果一个或多个参数为 Unicode，则所有参数都会转换为 Unicode，并执行 Unicode 模式匹配。</span><span class="sxs-lookup"><span data-stu-id="3ea9f-135">If one or more of the arguments are Unicode, all arguments are converted to Unicode and Unicode pattern matching is performed.</span></span> <span data-ttu-id="3ea9f-136">在将 Unicode 与 LIKE 一起使用时，尾随空格有意义；但对非 Unicode，尾随空格则没有意义。</span><span class="sxs-lookup"><span data-stu-id="3ea9f-136">When you use Unicode with LIKE, trailing blanks are significant; however, for non-Unicode, trailing blanks are not significant.</span></span> <span data-ttu-id="3ea9f-137">的模式字符串语法与 Transact-sql 的模式字符串语法 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 相同。</span><span class="sxs-lookup"><span data-stu-id="3ea9f-137">The pattern string syntax of [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is the same as that of Transact-SQL.</span></span>  
  
 <span data-ttu-id="3ea9f-138">模式可以包含常规字符和通配符。</span><span class="sxs-lookup"><span data-stu-id="3ea9f-138">A pattern can include regular characters and wildcard characters.</span></span> <span data-ttu-id="3ea9f-139">模式匹配过程中，常规字符必须与在字符 `string` 中指定的字符完全匹配。</span><span class="sxs-lookup"><span data-stu-id="3ea9f-139">During pattern matching, regular characters must exactly match the characters specified in the character `string`.</span></span> <span data-ttu-id="3ea9f-140">但是，通配符可以与字符串的任意部分相匹配。</span><span class="sxs-lookup"><span data-stu-id="3ea9f-140">However, wildcard characters can be matched with arbitrary fragments of the character string.</span></span> <span data-ttu-id="3ea9f-141">在与通配符一起使用时，LIKE 运算符比 = 和 != 字符串比较运算符更为灵活。</span><span class="sxs-lookup"><span data-stu-id="3ea9f-141">When it is used with wildcard characters, the LIKE operator is more flexible than the = and != string comparison operators.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3ea9f-142">如果是针对特定的提供程序，则可以使用特定于提供程序的扩展。</span><span class="sxs-lookup"><span data-stu-id="3ea9f-142">You may use provider-specific extensions if you target a specific provider.</span></span> <span data-ttu-id="3ea9f-143">但是，其他提供程序可能以不同方式对待这类构造。</span><span class="sxs-lookup"><span data-stu-id="3ea9f-143">However, such constructs may be treated differently by other providers, for example.</span></span> <span data-ttu-id="3ea9f-144">SqlServer 支持 [first-last] 和 [^first-last] 模式，前一个模式与介于“first”和“last”之间的一个字符完全匹配，而后一个模式与不在“first”和“last”之间的一个字符完全匹配。</span><span class="sxs-lookup"><span data-stu-id="3ea9f-144">SqlServer supports [first-last] and [^first-last] patterns where the former matches exactly one character between first and last, and the latter matches exactly one character that is not between first and last.</span></span>  
  
### <a name="escape"></a><span data-ttu-id="3ea9f-145">Escape</span><span class="sxs-lookup"><span data-stu-id="3ea9f-145">Escape</span></span>  

 <span data-ttu-id="3ea9f-146">使用 ESCAPE 子句可以搜索包含一个或多个特殊通配符（在上一部分的表中进行了介绍）的字符串。</span><span class="sxs-lookup"><span data-stu-id="3ea9f-146">By using the ESCAPE clause, you can search for character strings that include one or more of the special wildcard characters described in the table in the previous section.</span></span> <span data-ttu-id="3ea9f-147">例如，假定有几个文档在标题中包含文本“100%”，而您希望搜索所有这些文档。</span><span class="sxs-lookup"><span data-stu-id="3ea9f-147">For example, assume several documents include the literal "100%" in the title and you want to search for all of those documents.</span></span> <span data-ttu-id="3ea9f-148">由于百分号 (%) 字符是通配符，因此若要成功执行搜索，必须使用 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ESCAPE 子句对百分号字符进行转义。</span><span class="sxs-lookup"><span data-stu-id="3ea9f-148">Because the percent (%) character is a wildcard character, you must escape it using the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ESCAPE clause to successfully execute the search.</span></span> <span data-ttu-id="3ea9f-149">下面是一个此筛选的示例。</span><span class="sxs-lookup"><span data-stu-id="3ea9f-149">The following is an example of this filter.</span></span>  
  
```sql  
"title like '%100!%%' escape '!'"  
```  
  
 <span data-ttu-id="3ea9f-150">在此搜索表达式中，紧跟在惊叹号字符 (!) 之后的百分号通配符 (%)</span><span class="sxs-lookup"><span data-stu-id="3ea9f-150">In this search expression, the percent wildcard character (%) immediately following the exclamation point character (!) is treated as a literal, instead of as a wildcard character.</span></span> <span data-ttu-id="3ea9f-151">除了 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 通配符和方括号 (`[ ]`) 字符之外，可以使用任何字符作为转义符。</span><span class="sxs-lookup"><span data-stu-id="3ea9f-151">You can use any character as an escape character except for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] wildcard characters and the square bracket (`[ ]`) characters.</span></span> <span data-ttu-id="3ea9f-152">在前一个示例中，惊叹号 (!) 字符是转义字符。</span><span class="sxs-lookup"><span data-stu-id="3ea9f-152">In the previous example, the exclamation point (!) character is the escape character.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ea9f-153">示例</span><span class="sxs-lookup"><span data-stu-id="3ea9f-153">Example</span></span>  

 <span data-ttu-id="3ea9f-154">下面两个 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查询使用 LIKE 和 ESCAPE 运算符确定特定字符串是否与指定模式匹配。</span><span class="sxs-lookup"><span data-stu-id="3ea9f-154">The following two [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries use the LIKE and ESCAPE operators to determine whether a specific character string matches a specified pattern.</span></span> <span data-ttu-id="3ea9f-155">第一个查询搜索以字符 `Name` 开头的 `Down_`。</span><span class="sxs-lookup"><span data-stu-id="3ea9f-155">The first query searches for the `Name` that starts with the characters `Down_`.</span></span> <span data-ttu-id="3ea9f-156">此查询使用了 ESCAPE 选项，因为下划线 (`_`) 为通配符。</span><span class="sxs-lookup"><span data-stu-id="3ea9f-156">This query uses the ESCAPE option because the underscore (`_`) is a wildcard character.</span></span> <span data-ttu-id="3ea9f-157">如果不指定 ESCAPE 选项，则该查询将搜索所有以单词 `Name` 开头、后跟任意单个字符（下划线字符除外）的 `Down` 值。</span><span class="sxs-lookup"><span data-stu-id="3ea9f-157">Without specifying the ESCAPE option, the query would search for any `Name` values that start with the word `Down` followed by any single character other than the underscore character.</span></span> <span data-ttu-id="3ea9f-158">这些查询基于 AdventureWorks 销售模型。</span><span class="sxs-lookup"><span data-stu-id="3ea9f-158">The queries are based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="3ea9f-159">若要编译并运行此查询，请执行下列步骤：</span><span class="sxs-lookup"><span data-stu-id="3ea9f-159">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="3ea9f-160">按照 [如何：执行返回 PrimitiveType 结果的查询](../how-to-execute-a-query-that-returns-primitivetype-results.md)中的过程进行操作。</span><span class="sxs-lookup"><span data-stu-id="3ea9f-160">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="3ea9f-161">将以下查询作为参数传递给 `ExecutePrimitiveTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="3ea9f-161">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#LIKE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#like)]  
  
## <a name="see-also"></a><span data-ttu-id="3ea9f-162">请参阅</span><span class="sxs-lookup"><span data-stu-id="3ea9f-162">See also</span></span>

- [<span data-ttu-id="3ea9f-163">实体 SQL 引用</span><span class="sxs-lookup"><span data-stu-id="3ea9f-163">Entity SQL Reference</span></span>](entity-sql-reference.md)
