---
description: '了解更多详细信息：将数据分区 (Visual Basic) '
title: 数据分区
ms.date: 07/20/2015
ms.assetid: 69c59379-b66e-422c-b324-5b5c07760ef7
ms.openlocfilehash: 264a81d1217c7f5034058761033171b9c232fae2
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100465608"
---
# <a name="partitioning-data-visual-basic"></a><span data-ttu-id="b944d-103">将数据分区 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="b944d-103">Partitioning Data (Visual Basic)</span></span>

<span data-ttu-id="b944d-104">LINQ 中的分区是指将输入序列划分为两个部分的操作，无需重新排列元素，然后返回其中一个部分。</span><span class="sxs-lookup"><span data-stu-id="b944d-104">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="b944d-105">下图显示对字符序列进行三种不同的分区操作的结果。</span><span class="sxs-lookup"><span data-stu-id="b944d-105">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="b944d-106">第一个操作返回序列中的前三个元素。</span><span class="sxs-lookup"><span data-stu-id="b944d-106">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="b944d-107">第二个操作跳过前三个元素，返回剩余元素。</span><span class="sxs-lookup"><span data-stu-id="b944d-107">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="b944d-108">第三个操作跳过序列中的前两个元素，返回接下来的三个元素。</span><span class="sxs-lookup"><span data-stu-id="b944d-108">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 ![显示三个 LINQ 分区操作的图示。](./media/partitioning-data/linq-partitioning-operations.png)  
  
 <span data-ttu-id="b944d-110">下面一节列出了对序列进行分区的标准查询运算符方法。</span><span class="sxs-lookup"><span data-stu-id="b944d-110">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="b944d-111">运算符</span><span class="sxs-lookup"><span data-stu-id="b944d-111">Operators</span></span>  
  
|<span data-ttu-id="b944d-112">运算符名称</span><span class="sxs-lookup"><span data-stu-id="b944d-112">Operator Name</span></span>|<span data-ttu-id="b944d-113">描述</span><span class="sxs-lookup"><span data-stu-id="b944d-113">Description</span></span>|<span data-ttu-id="b944d-114">Visual Basic 查询表达式语法</span><span class="sxs-lookup"><span data-stu-id="b944d-114">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="b944d-115">更多信息</span><span class="sxs-lookup"><span data-stu-id="b944d-115">More Information</span></span>|  
|-------------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="b944d-116">Skip</span><span class="sxs-lookup"><span data-stu-id="b944d-116">Skip</span></span>|<span data-ttu-id="b944d-117">跳过序列中指定位置之前的元素。</span><span class="sxs-lookup"><span data-stu-id="b944d-117">Skips elements up to a specified position in a sequence.</span></span>|`Skip`|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b944d-118">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="b944d-118">SkipWhile</span></span>|<span data-ttu-id="b944d-119">基于谓词函数跳过元素，直到元素不符合条件。</span><span class="sxs-lookup"><span data-stu-id="b944d-119">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Skip While`|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b944d-120">Take</span><span class="sxs-lookup"><span data-stu-id="b944d-120">Take</span></span>|<span data-ttu-id="b944d-121">获取序列中指定位置之前的元素。</span><span class="sxs-lookup"><span data-stu-id="b944d-121">Takes elements up to a specified position in a sequence.</span></span>|`Take`|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b944d-122">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="b944d-122">TakeWhile</span></span>|<span data-ttu-id="b944d-123">基于谓词函数获取元素，直到元素不符合条件。</span><span class="sxs-lookup"><span data-stu-id="b944d-123">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Take While`|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="b944d-124">查询表达式语法示例</span><span class="sxs-lookup"><span data-stu-id="b944d-124">Query Expression Syntax Examples</span></span>  
  
### <a name="skip"></a><span data-ttu-id="b944d-125">跳过</span><span class="sxs-lookup"><span data-stu-id="b944d-125">Skip</span></span>  

 <span data-ttu-id="b944d-126">下面的代码示例使用 `Skip` Visual Basic 中的子句在返回数组中的剩余字符串之前，跳过字符串数组中的前四个字符串。</span><span class="sxs-lookup"><span data-stu-id="b944d-126">The following code example uses the `Skip` clause in Visual Basic to skip over the first four strings in an array of strings before returning the remaining strings in the array.</span></span>  
  
 [!code-vb[CsLINQPartitioning#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#1)]  
  
### <a name="skipwhile"></a><span data-ttu-id="b944d-127">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="b944d-127">SkipWhile</span></span>  

 <span data-ttu-id="b944d-128">下面的代码示例使用 `Skip While` Visual Basic 中的子句跳过数组中的字符串，而字符串的第一个字母为 "a"。</span><span class="sxs-lookup"><span data-stu-id="b944d-128">The following code example uses the `Skip While` clause in Visual Basic to skip over the strings in an array while the first letter of the string is "a".</span></span> <span data-ttu-id="b944d-129">返回数组中的剩余字符串。</span><span class="sxs-lookup"><span data-stu-id="b944d-129">The remaining strings in the array are returned.</span></span>  
  
 [!code-vb[CsLINQPartitioning#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#2)]  
  
### <a name="take"></a><span data-ttu-id="b944d-130">Take</span><span class="sxs-lookup"><span data-stu-id="b944d-130">Take</span></span>  

 <span data-ttu-id="b944d-131">下面的代码示例使用 `Take` Visual Basic 中的子句来返回字符串数组中的前两个字符串。</span><span class="sxs-lookup"><span data-stu-id="b944d-131">The following code example uses the `Take` clause in Visual Basic to return the first two strings in an array of strings.</span></span>  
  
 [!code-vb[CsLINQPartitioning#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#3)]  
  
### <a name="takewhile"></a><span data-ttu-id="b944d-132">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="b944d-132">TakeWhile</span></span>  

 <span data-ttu-id="b944d-133">下面的代码示例使用 `Take While` Visual Basic 中的子句来返回数组中的字符串，而字符串的长度为5个或更少。</span><span class="sxs-lookup"><span data-stu-id="b944d-133">The following code example uses the `Take While` clause in Visual Basic to return strings from an array while the length of the string is five or less.</span></span>  
  
 [!code-vb[CsLINQPartitioning#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="b944d-134">请参阅</span><span class="sxs-lookup"><span data-stu-id="b944d-134">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="b944d-135">标准查询运算符概述 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b944d-135">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="b944d-136">Skip 子句</span><span class="sxs-lookup"><span data-stu-id="b944d-136">Skip Clause</span></span>](../../../language-reference/queries/skip-clause.md)
- [<span data-ttu-id="b944d-137">Skip While 子句</span><span class="sxs-lookup"><span data-stu-id="b944d-137">Skip While Clause</span></span>](../../../language-reference/queries/skip-while-clause.md)
- [<span data-ttu-id="b944d-138">Take 子句</span><span class="sxs-lookup"><span data-stu-id="b944d-138">Take Clause</span></span>](../../../language-reference/queries/take-clause.md)
- [<span data-ttu-id="b944d-139">Take While 子句</span><span class="sxs-lookup"><span data-stu-id="b944d-139">Take While Clause</span></span>](../../../language-reference/queries/take-while-clause.md)
