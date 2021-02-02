---
title: MULTISET (Entity SQL)
ms.date: 03/30/2017
ms.assetid: eb90a377-e47a-43a5-b308-e993b6d611e6
ms.openlocfilehash: abdcce0e98c924052e07b9001d7dd92051c13747
ms.sourcegitcommit: 38999dc0ec4f7c4404de5ce0951b64c55997d9ab
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/02/2021
ms.locfileid: "99427018"
---
# <a name="multiset-entity-sql"></a><span data-ttu-id="b6b9b-102">MULTISET (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="b6b9b-102">MULTISET (Entity SQL)</span></span>

<span data-ttu-id="b6b9b-103">根据值列表创建多集的实例。</span><span class="sxs-lookup"><span data-stu-id="b6b9b-103">Creates an instance of a multiset from a list of values.</span></span> <span data-ttu-id="b6b9b-104">MULTISET 构造函数中的所有值都必须具有兼容类型 `T`。</span><span class="sxs-lookup"><span data-stu-id="b6b9b-104">All the values in the MULTISET constructor must be of a compatible type `T`.</span></span> <span data-ttu-id="b6b9b-105">不允许使用空的多集构造函数。</span><span class="sxs-lookup"><span data-stu-id="b6b9b-105">Empty multiset constructors are not allowed.</span></span>

## <a name="syntax"></a><span data-ttu-id="b6b9b-106">语法</span><span class="sxs-lookup"><span data-stu-id="b6b9b-106">Syntax</span></span>

```sql
MULTISET ( expression [{, expression }] )
-- or
{ expression [{, expression }] }
```

## <a name="arguments"></a><span data-ttu-id="b6b9b-107">参数</span><span class="sxs-lookup"><span data-stu-id="b6b9b-107">Arguments</span></span>

`expression`  
 <span data-ttu-id="b6b9b-108">任何有效的值列表。</span><span class="sxs-lookup"><span data-stu-id="b6b9b-108">Any valid list of values.</span></span>

## <a name="return-value"></a><span data-ttu-id="b6b9b-109">返回值</span><span class="sxs-lookup"><span data-stu-id="b6b9b-109">Return Value</span></span>

<span data-ttu-id="b6b9b-110">类型集的集合 \<T> 。</span><span class="sxs-lookup"><span data-stu-id="b6b9b-110">A collection of type MULTISET\<T>.</span></span>

## <a name="remarks"></a><span data-ttu-id="b6b9b-111">备注</span><span class="sxs-lookup"><span data-stu-id="b6b9b-111">Remarks</span></span>

<!-- markdownlint-disable DOCSMD001 -->

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="b6b9b-112">提供了三种构造函数：行构造函数、对象构造函数和多集（或集合）构造函数。</span><span class="sxs-lookup"><span data-stu-id="b6b9b-112">provides three kinds of constructors: row constructors, object constructors, and multiset (or collection) constructors.</span></span> <span data-ttu-id="b6b9b-113">有关详细信息，请参阅 [构造类型](constructing-types-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="b6b9b-113">For more information, see [Constructing Types](constructing-types-entity-sql.md).</span></span>

<span data-ttu-id="b6b9b-114">多集构造函数根据值列表创建多集的实例。</span><span class="sxs-lookup"><span data-stu-id="b6b9b-114">The multiset constructor creates an instance of a multiset from a list of values.</span></span> <span data-ttu-id="b6b9b-115">该构造函数中的所有值都必须具有兼容类型。</span><span class="sxs-lookup"><span data-stu-id="b6b9b-115">All the values in the constructor must be of a compatible type.</span></span>

<span data-ttu-id="b6b9b-116">例如，下面的表达式创建整数的多集。</span><span class="sxs-lookup"><span data-stu-id="b6b9b-116">For example, the following expression creates a multiset of integers.</span></span>

`MULTISET(1, 2, 3)`

`{1, 2, 3}`

> [!NOTE]
> <span data-ttu-id="b6b9b-117">仅当包装多集具有单个多重集元素时才支持嵌套的多集文本;例如， `{{1, 2, 3}}` 。</span><span class="sxs-lookup"><span data-stu-id="b6b9b-117">Nested multiset literals are only supported when a wrapping multiset has a single multiset element; for example, `{{1, 2, 3}}`.</span></span> <span data-ttu-id="b6b9b-118">当包装多集具有多个多集元素（如 `{{1, 2}, {3, 4}}`）时，不支持嵌套多集文本。</span><span class="sxs-lookup"><span data-stu-id="b6b9b-118">When the wrapping multiset has multiple multiset elements (for example, `{{1, 2}, {3, 4}}`), nested multiset literals are not supported.</span></span>

## <a name="example"></a><span data-ttu-id="b6b9b-119">示例</span><span class="sxs-lookup"><span data-stu-id="b6b9b-119">Example</span></span>

<span data-ttu-id="b6b9b-120">下面的 Entity SQL 查询使用 MULTISET 运算符根据值列表创建多集的实例。</span><span class="sxs-lookup"><span data-stu-id="b6b9b-120">The following Entity SQL query uses the MULTISET operator to create an instance of a multiset from a list of values.</span></span> <span data-ttu-id="b6b9b-121">此查询基于 AdventureWorks 销售模型。</span><span class="sxs-lookup"><span data-stu-id="b6b9b-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="b6b9b-122">若要编译并运行此查询，请执行下列步骤：</span><span class="sxs-lookup"><span data-stu-id="b6b9b-122">To compile and run this query, follow these steps:</span></span>

1. <span data-ttu-id="b6b9b-123">执行 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的过程。</span><span class="sxs-lookup"><span data-stu-id="b6b9b-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>

2. <span data-ttu-id="b6b9b-124">将以下查询作为参数传递给 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="b6b9b-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>

[!code-sql[DP EntityServices Concepts#MULTISET](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#multiset)]

## <a name="see-also"></a><span data-ttu-id="b6b9b-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="b6b9b-125">See also</span></span>

- [<span data-ttu-id="b6b9b-126">构造类型</span><span class="sxs-lookup"><span data-stu-id="b6b9b-126">Constructing Types</span></span>](constructing-types-entity-sql.md)
- [<span data-ttu-id="b6b9b-127">实体 SQL 引用</span><span class="sxs-lookup"><span data-stu-id="b6b9b-127">Entity SQL Reference</span></span>](entity-sql-reference.md)
