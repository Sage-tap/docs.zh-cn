---
description: '了解详细信息：筛选数据 (Visual Basic) '
title: 筛选数据
ms.date: 07/20/2015
ms.assetid: 7749519a-7edc-49fe-aef9-6a353864af6c
ms.openlocfilehash: 2e259209df35a89eb4730f79ffccfee7cb64b9e9
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100428592"
---
# <a name="filtering-data-visual-basic"></a><span data-ttu-id="6a02e-103">筛选数据 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="6a02e-103">Filtering Data (Visual Basic)</span></span>

<span data-ttu-id="6a02e-104">筛选是指将结果集限制为仅包含满足指定条件的元素的操作。</span><span class="sxs-lookup"><span data-stu-id="6a02e-104">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="6a02e-105">它也称为选定内容。</span><span class="sxs-lookup"><span data-stu-id="6a02e-105">It is also known as selection.</span></span>

<span data-ttu-id="6a02e-106">下图演示了对字符序列进行筛选的结果。</span><span class="sxs-lookup"><span data-stu-id="6a02e-106">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="6a02e-107">筛选操作的谓词指定字符必须为“A”。</span><span class="sxs-lookup"><span data-stu-id="6a02e-107">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>

![显示 LINQ 筛选操作的图表](./media/filtering-data/linq-filter-operation.png)

<span data-ttu-id="6a02e-109">下面一节列出了执行所选内容的标准查询运算符方法。</span><span class="sxs-lookup"><span data-stu-id="6a02e-109">The standard query operator methods that perform selection are listed in the following section.</span></span>

## <a name="methods"></a><span data-ttu-id="6a02e-110">方法</span><span class="sxs-lookup"><span data-stu-id="6a02e-110">Methods</span></span>

|<span data-ttu-id="6a02e-111">方法名</span><span class="sxs-lookup"><span data-stu-id="6a02e-111">Method Name</span></span>|<span data-ttu-id="6a02e-112">描述</span><span class="sxs-lookup"><span data-stu-id="6a02e-112">Description</span></span>|<span data-ttu-id="6a02e-113">Visual Basic 查询表达式语法</span><span class="sxs-lookup"><span data-stu-id="6a02e-113">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="6a02e-114">详细信息</span><span class="sxs-lookup"><span data-stu-id="6a02e-114">More Information</span></span>|
|-----------------|-----------------|------------------------------------------|----------------------|
|<span data-ttu-id="6a02e-115">OfType</span><span class="sxs-lookup"><span data-stu-id="6a02e-115">OfType</span></span>|<span data-ttu-id="6a02e-116">根据其转换为特定类型的能力选择值。</span><span class="sxs-lookup"><span data-stu-id="6a02e-116">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="6a02e-117">不适用。</span><span class="sxs-lookup"><span data-stu-id="6a02e-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|<span data-ttu-id="6a02e-118">Where</span><span class="sxs-lookup"><span data-stu-id="6a02e-118">Where</span></span>|<span data-ttu-id="6a02e-119">选择基于谓词函数的值。</span><span class="sxs-lookup"><span data-stu-id="6a02e-119">Selects values that are based on a predicate function.</span></span>|`Where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a><span data-ttu-id="6a02e-120">查询表达式语法示例</span><span class="sxs-lookup"><span data-stu-id="6a02e-120">Query Expression Syntax Example</span></span>

<span data-ttu-id="6a02e-121">下面的示例使用 `Where` 从数组中筛选那些具有特定长度的字符串。</span><span class="sxs-lookup"><span data-stu-id="6a02e-121">The following example uses the `Where` to filter from an array those strings that have a specific length.</span></span>

```vb
Dim words() As String = {"the", "quick", "brown", "fox", "jumps"}

Dim query = From word In words
            Where word.Length = 3
            Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In query
    sb.AppendLine(str)
Next

' Display the results.
MsgBox(sb.ToString())

' This code produces the following output:

' the
' fox
```

## <a name="see-also"></a><span data-ttu-id="6a02e-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="6a02e-122">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="6a02e-123">标准查询运算符概述 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6a02e-123">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="6a02e-124">Where 子句</span><span class="sxs-lookup"><span data-stu-id="6a02e-124">Where Clause</span></span>](../../../language-reference/queries/where-clause.md)
- [<span data-ttu-id="6a02e-125">如何：筛选查询结果</span><span class="sxs-lookup"><span data-stu-id="6a02e-125">How to: Filter Query Results</span></span>](../../language-features/linq/how-to-filter-query-results-by-using-linq.md)
- [<span data-ttu-id="6a02e-126">如何：使用反射查询程序集的元数据 (LINQ)  (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="6a02e-126">How to: Query An Assembly's Metadata with Reflection (LINQ) (Visual Basic)</span></span>](how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [<span data-ttu-id="6a02e-127">如何：查询具有指定特性或名称的文件 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="6a02e-127">How to: Query for Files with a Specified Attribute or Name (Visual Basic)</span></span>](how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [<span data-ttu-id="6a02e-128">如何：按任意词或字段对文本数据进行排序或筛选 (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6a02e-128">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
