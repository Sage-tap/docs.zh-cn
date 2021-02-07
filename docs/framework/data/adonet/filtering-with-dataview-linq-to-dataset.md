---
description: '了解详细信息：通过 DataView (LINQ to DataSet 进行筛选) '
title: 使用 DataView 进行筛选 (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5632d74a-ff53-4ea7-9fe7-4a148eeb1c68
ms.openlocfilehash: 152b2e1d82cd5cf0eac24fd952de26d83fbffe58
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724136"
---
# <a name="filtering-with-dataview-linq-to-dataset"></a><span data-ttu-id="d3f80-103">使用 DataView 进行筛选 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="d3f80-103">Filtering with DataView (LINQ to DataSet)</span></span>

<span data-ttu-id="d3f80-104">使用特定条件筛选数据，然后通过 UI 控件在客户端中表示该数据的能力是数据绑定的一个重要特征。</span><span class="sxs-lookup"><span data-stu-id="d3f80-104">The ability to filter data using specific criteria and then present the data to a client through a UI control is an important aspect of data binding.</span></span> <span data-ttu-id="d3f80-105"><xref:System.Data.DataView> 提供多种方式来筛选数据并返回满足指定筛选条件的数据行子集。</span><span class="sxs-lookup"><span data-stu-id="d3f80-105"><xref:System.Data.DataView> provides several ways to filter data and return subsets of data rows meeting specific filter criteria.</span></span> <span data-ttu-id="d3f80-106">除了基于字符串的筛选功能以外， <xref:System.Data.DataView> 还提供了对筛选条件使用 LINQ 表达式的功能。</span><span class="sxs-lookup"><span data-stu-id="d3f80-106">In addition to the string-based filtering capabilities, <xref:System.Data.DataView> also provides the ability to use LINQ expressions for the filtering criteria.</span></span> <span data-ttu-id="d3f80-107">LINQ 表达式允许执行比基于字符串的筛选更复杂而功能更强大的筛选操作。</span><span class="sxs-lookup"><span data-stu-id="d3f80-107">LINQ expressions allow for much more complex and powerful filtering operations than the string-based filtering.</span></span>  
  
 <span data-ttu-id="d3f80-108">使用 <xref:System.Data.DataView> 筛选数据有两种方式：</span><span class="sxs-lookup"><span data-stu-id="d3f80-108">There are two ways to filter data using a <xref:System.Data.DataView>:</span></span>  
  
- <span data-ttu-id="d3f80-109"><xref:System.Data.DataView>使用 Where 子句从 LINQ to DataSet 查询创建。</span><span class="sxs-lookup"><span data-stu-id="d3f80-109">Create a <xref:System.Data.DataView> from a LINQ to DataSet query with a Where clause.</span></span>  
  
- <span data-ttu-id="d3f80-110">使用 <xref:System.Data.DataView> 现有的基于字符串的筛选功能。</span><span class="sxs-lookup"><span data-stu-id="d3f80-110">Use the existing, string-based filtering capabilities of <xref:System.Data.DataView>.</span></span>  
  
## <a name="creating-dataview-from-a-query-with-filtering-information"></a><span data-ttu-id="d3f80-111">通过具有筛选信息的查询创建 DataView</span><span class="sxs-lookup"><span data-stu-id="d3f80-111">Creating DataView from a Query with Filtering Information</span></span>  

 <span data-ttu-id="d3f80-112"><xref:System.Data.DataView>可以通过 LINQ to DataSet 查询来创建对象。</span><span class="sxs-lookup"><span data-stu-id="d3f80-112">A <xref:System.Data.DataView> object can be created from a LINQ to DataSet query.</span></span> <span data-ttu-id="d3f80-113">如果该查询包含一个 `Where` 子句，则会使用查询中的筛选信息创建 <xref:System.Data.DataView>。</span><span class="sxs-lookup"><span data-stu-id="d3f80-113">If that query contains a `Where` clause, the <xref:System.Data.DataView> is created with the filtering information from the query.</span></span> <span data-ttu-id="d3f80-114">`Where` 子句中的表达式用于确定哪些数据行将包括在 <xref:System.Data.DataView> 中并作为筛选器的基础。</span><span class="sxs-lookup"><span data-stu-id="d3f80-114">The expression in the `Where` clause is used to determine which data rows will be included in the <xref:System.Data.DataView>, and is the basis for the filter.</span></span>  
  
 <span data-ttu-id="d3f80-115">基于表达式的筛选器具有比基于字符串的简单筛选器更强大、更复杂的筛选功能。</span><span class="sxs-lookup"><span data-stu-id="d3f80-115">Expression-based filters offer more powerful and complex filtering than the simpler string-based filters.</span></span> <span data-ttu-id="d3f80-116">基于字符串的筛选器和基于表达式的筛选器是互相排斥的。</span><span class="sxs-lookup"><span data-stu-id="d3f80-116">The string-based and expression-based filters are mutually exclusive.</span></span> <span data-ttu-id="d3f80-117">如果在通过查询创建 <xref:System.Data.DataView.RowFilter%2A> 后设置基于字符串的 <xref:System.Data.DataView>，则会清除从查询推断的基于表达式的筛选器。</span><span class="sxs-lookup"><span data-stu-id="d3f80-117">When the string-based <xref:System.Data.DataView.RowFilter%2A> is set after a <xref:System.Data.DataView> is created from a query, the expression based filter inferred from the query is cleared.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d3f80-118">在大多数情况下，用于筛选的表达式不应有副作用且必须是确定的。</span><span class="sxs-lookup"><span data-stu-id="d3f80-118">In most cases, the expressions used for filtering should not have side effects and must be deterministic.</span></span> <span data-ttu-id="d3f80-119">另外，表达式不应包含依赖于固定执行次数的任何逻辑，因为筛选操作可能会执行任意次。</span><span class="sxs-lookup"><span data-stu-id="d3f80-119">Also, the expressions should not contain any logic that depends on a set number of executions, because the filtering operations might be executed any number of times.</span></span>  
  
### <a name="example"></a><span data-ttu-id="d3f80-120">示例</span><span class="sxs-lookup"><span data-stu-id="d3f80-120">Example</span></span>  

 <span data-ttu-id="d3f80-121">下面的示例查询 SalesOrderDetail 表中数量大于 2 且小于 6 的订单，通过查询创建 <xref:System.Data.DataView>，并将 <xref:System.Data.DataView> 绑定到 <xref:System.Windows.Forms.BindingSource>：</span><span class="sxs-lookup"><span data-stu-id="d3f80-121">The following example queries the SalesOrderDetail table for orders with a quantity greater than 2 and less than 6; creates a <xref:System.Data.DataView> from that query; and binds the <xref:System.Data.DataView> to a <xref:System.Windows.Forms.BindingSource>:</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhere](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhere)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhere](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhere)]  
  
### <a name="example"></a><span data-ttu-id="d3f80-122">示例</span><span class="sxs-lookup"><span data-stu-id="d3f80-122">Example</span></span>  

 <span data-ttu-id="d3f80-123">下面的示例通过查询 2001 年 6 月 6 日以后达成的订单来创建 <xref:System.Data.DataView>：</span><span class="sxs-lookup"><span data-stu-id="d3f80-123">The following example creates a <xref:System.Data.DataView> from a query for orders placed after June 6, 2001:</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhere3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhere3)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhere3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhere3)]  
  
### <a name="example"></a><span data-ttu-id="d3f80-124">示例</span><span class="sxs-lookup"><span data-stu-id="d3f80-124">Example</span></span>  

 <span data-ttu-id="d3f80-125">筛选也可以与排序组合使用。</span><span class="sxs-lookup"><span data-stu-id="d3f80-125">Filtering can also be combined with sorting.</span></span> <span data-ttu-id="d3f80-126">下面的示例通过查询姓氏以“S”开始并按姓氏排序，然后按名字排序的联系人来创建 <xref:System.Data.DataView>：</span><span class="sxs-lookup"><span data-stu-id="d3f80-126">The following example creates a <xref:System.Data.DataView> from a query for contacts whose last name start with "S" and sorted by last name, then first name:</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhereOrderByThenBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhereorderbythenby)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhereOrderByThenBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhereorderbythenby)]  
  
### <a name="example"></a><span data-ttu-id="d3f80-127">示例</span><span class="sxs-lookup"><span data-stu-id="d3f80-127">Example</span></span>  

 <span data-ttu-id="d3f80-128">下面的示例使用 SoundEx 算法查找姓氏与“Zhu”相近的联系人。</span><span class="sxs-lookup"><span data-stu-id="d3f80-128">The following example uses the SoundEx algorithm to find contacts whose last name is similar to "Zhu".</span></span> <span data-ttu-id="d3f80-129">SoundEx 算法在 SoundEx 方法中实现。</span><span class="sxs-lookup"><span data-stu-id="d3f80-129">The SoundEx algorithm is implemented in the SoundEx method.</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVSoundExFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvsoundexfilter)]
 [!code-vb[DP DataView Samples#LDVSoundExFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvsoundexfilter)]  
  
 <span data-ttu-id="d3f80-130">SoundEx 是一种拼音算法，用于按英语发音来索引姓名，它最初由美国人口调查局开发。</span><span class="sxs-lookup"><span data-stu-id="d3f80-130">SoundEx is a phonetic algorithm used for indexing names by sound, as they are pronounced in English, originally developed by the U.S. Census Bureau.</span></span> <span data-ttu-id="d3f80-131">SoundEx 方法返回一个表示姓名的四字符代码，由一个英文字母后跟三个数字构成。</span><span class="sxs-lookup"><span data-stu-id="d3f80-131">The SoundEx method returns a four character code for a name consisting of an English letter followed by three numbers.</span></span> <span data-ttu-id="d3f80-132">字母是姓名的首字母，数字对姓名中剩余的辅音字母编码。</span><span class="sxs-lookup"><span data-stu-id="d3f80-132">The letter is the first letter of the name and the numbers encode the remaining consonants in the name.</span></span> <span data-ttu-id="d3f80-133">发音相近的姓名具有相同的 SoundEx 代码。</span><span class="sxs-lookup"><span data-stu-id="d3f80-133">Similar sounding names share the same SoundEx code.</span></span> <span data-ttu-id="d3f80-134">上一示例的 SoundEx 方法中使用的 SoundEx 实现如下所示：</span><span class="sxs-lookup"><span data-stu-id="d3f80-134">The SoundEx implementation used in the SoundEx method of the previous example is shown here:</span></span>  
  
 [!code-csharp[DP DataView Samples#SoundEx](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#soundex)]
 [!code-vb[DP DataView Samples#SoundEx](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#soundex)]  
  
## <a name="using-the-rowfilter-property"></a><span data-ttu-id="d3f80-135">使用 RowFilter 属性</span><span class="sxs-lookup"><span data-stu-id="d3f80-135">Using the RowFilter Property</span></span>  

 <span data-ttu-id="d3f80-136">现有的基于字符串的筛选功能 <xref:System.Data.DataView> 仍适用于 LINQ to DataSet 上下文。</span><span class="sxs-lookup"><span data-stu-id="d3f80-136">The existing string-based filtering functionality of <xref:System.Data.DataView> still works in the LINQ to DataSet context.</span></span> <span data-ttu-id="d3f80-137">有关基于字符串的筛选的详细信息 <xref:System.Data.DataView.RowFilter%2A> ，请参阅对 [数据进行排序和筛选](./dataset-datatable-dataview/sorting-and-filtering-data.md)。</span><span class="sxs-lookup"><span data-stu-id="d3f80-137">For more information about string-based <xref:System.Data.DataView.RowFilter%2A> filtering, see [Sorting and Filtering Data](./dataset-datatable-dataview/sorting-and-filtering-data.md).</span></span>  
  
 <span data-ttu-id="d3f80-138">下面的示例从 Contact 表创建 <xref:System.Data.DataView>，然后设置 <xref:System.Data.DataView.RowFilter%2A> 属性以返回联系人的姓氏为“Zhu”的行：</span><span class="sxs-lookup"><span data-stu-id="d3f80-138">The following example creates a <xref:System.Data.DataView> from the Contact table and then sets the <xref:System.Data.DataView.RowFilter%2A> property to return rows where the contact's last name is "Zhu":</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvrowfilter)]
 [!code-vb[DP DataView Samples#LDVRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvrowfilter)]  
  
 <span data-ttu-id="d3f80-139">在 <xref:System.Data.DataView> 从 <xref:System.Data.DataTable> 或 LINQ to DataSet 查询创建后，可以使用 <xref:System.Data.DataView.RowFilter%2A> 属性根据行的列值指定行的子集。</span><span class="sxs-lookup"><span data-stu-id="d3f80-139">After a <xref:System.Data.DataView> has been created from a <xref:System.Data.DataTable> or LINQ to DataSet query, you can use the <xref:System.Data.DataView.RowFilter%2A> property to specify subsets of rows based on their column values.</span></span> <span data-ttu-id="d3f80-140">基于字符串的筛选器和基于表达式的筛选器是互相排斥的。</span><span class="sxs-lookup"><span data-stu-id="d3f80-140">The string-based and expression-based filters are mutually exclusive.</span></span> <span data-ttu-id="d3f80-141">设置 <xref:System.Data.DataView.RowFilter%2A> 属性将清除从 LINQ to DataSet 查询推断的筛选表达式，并且不能重置筛选器表达式。</span><span class="sxs-lookup"><span data-stu-id="d3f80-141">Setting the <xref:System.Data.DataView.RowFilter%2A> property will clear the filter expression inferred from the LINQ to DataSet query, and the filter expression cannot be reset.</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhereSetRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywheresetrowfilter)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhereSetRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywheresetrowfilter)]  
  
 <span data-ttu-id="d3f80-142">如果要返回特定数据查询的结果而不是提供数据子集的动态视图，则可以使用 <xref:System.Data.DataView.Find%2A> 的 <xref:System.Data.DataView.FindRows%2A> 或 <xref:System.Data.DataView> 方法，而不设置 <xref:System.Data.DataView.RowFilter%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="d3f80-142">If you want to return the results of a particular query on the data, as opposed to providing a dynamic view of a subset of the data, you can use the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView>, rather than setting the <xref:System.Data.DataView.RowFilter%2A> property.</span></span> <span data-ttu-id="d3f80-143"><xref:System.Data.DataView.RowFilter%2A> 属性最适合用于用绑定控件显示筛选结果的数据绑定应用程序。</span><span class="sxs-lookup"><span data-stu-id="d3f80-143">The <xref:System.Data.DataView.RowFilter%2A> property is best used in a data-bound application where a bound control displays filtered results.</span></span> <span data-ttu-id="d3f80-144">设置 <xref:System.Data.DataView.RowFilter%2A> 属性会重新生成数据的索引，从而增加应用程序的系统开销并降低性能。</span><span class="sxs-lookup"><span data-stu-id="d3f80-144">Setting the <xref:System.Data.DataView.RowFilter%2A> property rebuilds the index for the data, adding overhead to your application and decreasing performance.</span></span> <span data-ttu-id="d3f80-145"><xref:System.Data.DataView.Find%2A> 和 <xref:System.Data.DataView.FindRows%2A> 方法使用当前索引，而不要求重新生成索引。</span><span class="sxs-lookup"><span data-stu-id="d3f80-145">The <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods use the current index without requiring the index to be rebuilt.</span></span> <span data-ttu-id="d3f80-146">如果只想调用 <xref:System.Data.DataView.Find%2A> 或 <xref:System.Data.DataView.FindRows%2A> 一次，则应使用现有的 <xref:System.Data.DataView>。</span><span class="sxs-lookup"><span data-stu-id="d3f80-146">If you are going to call <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> only once, then you should use the existing <xref:System.Data.DataView>.</span></span> <span data-ttu-id="d3f80-147">如果想要调用 <xref:System.Data.DataView.Find%2A> 或 <xref:System.Data.DataView.FindRows%2A> 多次，则应该创建一个新的 <xref:System.Data.DataView> 以便对想要搜索的列重新生成索引，然后调用 <xref:System.Data.DataView.Find%2A> 或 <xref:System.Data.DataView.FindRows%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="d3f80-147">If you are going to call <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> multiple times, you should create a new <xref:System.Data.DataView> to rebuild the index on the column you want to search on, and then call the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods.</span></span> <span data-ttu-id="d3f80-148">有关和方法的详细信息 <xref:System.Data.DataView.Find%2A> ， <xref:System.Data.DataView.FindRows%2A> 请参阅 [查找行](./dataset-datatable-dataview/finding-rows.md) 和 [DataView 性能](dataview-performance.md)。</span><span class="sxs-lookup"><span data-stu-id="d3f80-148">For more information about the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods see [Finding Rows](./dataset-datatable-dataview/finding-rows.md) and [DataView Performance](dataview-performance.md).</span></span>  
  
## <a name="clearing-the-filter"></a><span data-ttu-id="d3f80-149">清除筛选器</span><span class="sxs-lookup"><span data-stu-id="d3f80-149">Clearing the Filter</span></span>  

 <span data-ttu-id="d3f80-150">使用 <xref:System.Data.DataView> 属性设置筛选之后，可以清除 <xref:System.Data.DataView.RowFilter%2A> 上的筛选器。</span><span class="sxs-lookup"><span data-stu-id="d3f80-150">The filter on a <xref:System.Data.DataView> can be cleared after filtering has been set using the <xref:System.Data.DataView.RowFilter%2A> property.</span></span> <span data-ttu-id="d3f80-151"><xref:System.Data.DataView> 上的筛选器可以采用两种不同的方式清除：</span><span class="sxs-lookup"><span data-stu-id="d3f80-151">The filter on a <xref:System.Data.DataView> can be cleared in two different ways:</span></span>  
  
- <span data-ttu-id="d3f80-152">将 <xref:System.Data.DataView.RowFilter%2A> 属性设置为 `null`。</span><span class="sxs-lookup"><span data-stu-id="d3f80-152">Set the <xref:System.Data.DataView.RowFilter%2A> property to `null`.</span></span>  
  
- <span data-ttu-id="d3f80-153">将 <xref:System.Data.DataView.RowFilter%2A> 属性设置为一个空字符串。</span><span class="sxs-lookup"><span data-stu-id="d3f80-153">Set the <xref:System.Data.DataView.RowFilter%2A> property to an empty string.</span></span>  
  
### <a name="example"></a><span data-ttu-id="d3f80-154">示例</span><span class="sxs-lookup"><span data-stu-id="d3f80-154">Example</span></span>  

 <span data-ttu-id="d3f80-155">下面的示例通过查询创建 <xref:System.Data.DataView>，然后通过将 <xref:System.Data.DataView.RowFilter%2A> 属性设置为 `null` 来清除该筛选器：</span><span class="sxs-lookup"><span data-stu-id="d3f80-155">The following example creates a <xref:System.Data.DataView> from a query and then clears the filter by setting <xref:System.Data.DataView.RowFilter%2A> property to `null`:</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVClearRowFilter2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearrowfilter2)]
 [!code-vb[DP DataView Samples#LDVClearRowFilter2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearrowfilter2)]  
  
### <a name="example"></a><span data-ttu-id="d3f80-156">示例</span><span class="sxs-lookup"><span data-stu-id="d3f80-156">Example</span></span>  

 <span data-ttu-id="d3f80-157">下面的示例从表创建 <xref:System.Data.DataView>，设置 <xref:System.Data.DataView.RowFilter%2A> 属性，然后通过将 <xref:System.Data.DataView.RowFilter%2A> 属性设置为一个空的字符串来清除该筛选器：</span><span class="sxs-lookup"><span data-stu-id="d3f80-157">The following example creates a <xref:System.Data.DataView> from a table sets the <xref:System.Data.DataView.RowFilter%2A> property, and then clears the filter by setting the <xref:System.Data.DataView.RowFilter%2A> property to an empty string:</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVClearRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearrowfilter)]
 [!code-vb[DP DataView Samples#LDVClearRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearrowfilter)]  
  
## <a name="see-also"></a><span data-ttu-id="d3f80-158">请参阅</span><span class="sxs-lookup"><span data-stu-id="d3f80-158">See also</span></span>

- [<span data-ttu-id="d3f80-159">数据绑定和 LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="d3f80-159">Data Binding and LINQ to DataSet</span></span>](data-binding-and-linq-to-dataset.md)
- [<span data-ttu-id="d3f80-160">使用 DataView 进行排序</span><span class="sxs-lookup"><span data-stu-id="d3f80-160">Sorting with DataView</span></span>](sorting-with-dataview-linq-to-dataset.md)
