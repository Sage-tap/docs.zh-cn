---
description: '了解有关以下内容的详细信息：创建 DataView 对象 (LINQ to DataSet) '
title: 创建 DataView 对象 (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 76057508-e12d-4779-a707-06a4c2568acf
ms.openlocfilehash: 4261e4bf55616a56652cb111d3660210dc3f96f3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99663815"
---
# <a name="creating-a-dataview-object-linq-to-dataset"></a><span data-ttu-id="1a160-103">创建 DataView 对象 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="1a160-103">Creating a DataView Object (LINQ to DataSet)</span></span>

<span data-ttu-id="1a160-104">可以通过两种方式 <xref:System.Data.DataView> 在 LINQ to DataSet 上下文中创建。</span><span class="sxs-lookup"><span data-stu-id="1a160-104">There are two ways to create a <xref:System.Data.DataView> in the LINQ to DataSet context.</span></span> <span data-ttu-id="1a160-105">您可以通过在 <xref:System.Data.DataView> LINQ to DataSet 查询中创建 <xref:System.Data.DataTable> ，也可以从类型化或非类型化的中创建 <xref:System.Data.DataTable> 。</span><span class="sxs-lookup"><span data-stu-id="1a160-105">You can create a <xref:System.Data.DataView> from a LINQ to DataSet query over a <xref:System.Data.DataTable>, or you can create it from a typed or un-typed <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="1a160-106">在这两种情况下，都可以 <xref:System.Data.DataView> 使用一个扩展方法创建，而 <xref:System.Data.DataTableExtensions.AsDataView%2A> <xref:System.Data.DataView> 不会直接在 LINQ to DataSet 上下文中可构造。</span><span class="sxs-lookup"><span data-stu-id="1a160-106">In both cases, you create the <xref:System.Data.DataView> by using one of the <xref:System.Data.DataTableExtensions.AsDataView%2A> extension methods; <xref:System.Data.DataView> is not directly constructible in the LINQ to DataSet context.</span></span>  
  
 <span data-ttu-id="1a160-107">创建 <xref:System.Data.DataView> 之后，您可以将其绑定到 Windows 窗体应用程序或 ASP.NET 应用程序中的 UI 控件上，或者更改筛选和排序设置。</span><span class="sxs-lookup"><span data-stu-id="1a160-107">After the <xref:System.Data.DataView> has been created, you can bind it to a UI control in a Windows forms application or an ASP.NET application, or change the filtering and sorting settings.</span></span>  
  
 <span data-ttu-id="1a160-108"><xref:System.Data.DataView> 构造一个索引，该索引可显著提高可使用该索引的操作（如筛选和排序）的性能。</span><span class="sxs-lookup"><span data-stu-id="1a160-108"><xref:System.Data.DataView> constructs an index, which significantly increases the performance of operations that can use the index, such as filtering and sorting.</span></span> <span data-ttu-id="1a160-109">创建 <xref:System.Data.DataView> 及修改任何排序或筛选信息时，均会生成 <xref:System.Data.DataView> 的索引。</span><span class="sxs-lookup"><span data-stu-id="1a160-109">The index for a <xref:System.Data.DataView> is built both when the <xref:System.Data.DataView> is created and when any of the sorting or filtering information is modified.</span></span> <span data-ttu-id="1a160-110">创建 <xref:System.Data.DataView> 然后设置排序或筛选信息会使索引生成至少两次：一次是在创建 <xref:System.Data.DataView> 时，另一次是在修改任何排序或筛选属性时。</span><span class="sxs-lookup"><span data-stu-id="1a160-110">Creating a <xref:System.Data.DataView> and then setting the sorting or filtering information later causes the index to be built at least twice: once when the <xref:System.Data.DataView> is created, and again when any of the sort or filter properties are modified.</span></span>  
  
 <span data-ttu-id="1a160-111">有关对进行筛选和排序的详细信息 <xref:System.Data.DataView> ，请参阅通过 [Dataview 进行筛选](filtering-with-dataview-linq-to-dataset.md) 和 [通过 dataview 进行排序](sorting-with-dataview-linq-to-dataset.md)。</span><span class="sxs-lookup"><span data-stu-id="1a160-111">For more information about filtering and sorting with <xref:System.Data.DataView>, see [Filtering with DataView](filtering-with-dataview-linq-to-dataset.md) and [Sorting with DataView](sorting-with-dataview-linq-to-dataset.md).</span></span>  
  
## <a name="creating-dataview-from-a-linq-to-dataset-query"></a><span data-ttu-id="1a160-112">通过 LINQ to DataSet 查询创建 DataView</span><span class="sxs-lookup"><span data-stu-id="1a160-112">Creating DataView from a LINQ to DataSet Query</span></span>  

 <span data-ttu-id="1a160-113"><xref:System.Data.DataView>可以从 LINQ to DataSet 查询的结果创建一个对象，其中的结果是对象的投影 <xref:System.Data.DataRow> 。</span><span class="sxs-lookup"><span data-stu-id="1a160-113">A <xref:System.Data.DataView> object can be created from the results of a LINQ to DataSet query, where the results are a projection of <xref:System.Data.DataRow> objects.</span></span> <span data-ttu-id="1a160-114">新创建的 <xref:System.Data.DataView> 会从创建它的查询继承筛选和排序信息。</span><span class="sxs-lookup"><span data-stu-id="1a160-114">The newly created <xref:System.Data.DataView> inherits the filtering and sorting information from the query it is created from.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1a160-115">在大多数情况下，用于筛选和排序的表达式不应有副作用且必须是确定的。</span><span class="sxs-lookup"><span data-stu-id="1a160-115">In most cases, the expressions used for filtering and sorting should not have side effects and must be deterministic.</span></span> <span data-ttu-id="1a160-116">另外，表达式不应包含依赖于固定执行次数的任何逻辑，因为排序和筛选操作可能会执行任意次。</span><span class="sxs-lookup"><span data-stu-id="1a160-116">Also, the expressions should not contain any logic that depend on a set number of executions, as the sorting and filtering operations may be executed any number of times.</span></span>  
  
 <span data-ttu-id="1a160-117">不支持通过返回匿名类型的查询或执行联接操作的查询创建 <xref:System.Data.DataView>。</span><span class="sxs-lookup"><span data-stu-id="1a160-117">Creating a <xref:System.Data.DataView> from a query that returns anonymous types or queries that perform join operations is not supported.</span></span>  
  
 <span data-ttu-id="1a160-118">在用于创建 <xref:System.Data.DataView> 的查询中仅支持以下查询运算符：</span><span class="sxs-lookup"><span data-stu-id="1a160-118">Only the following query operators are supported in a query used to create <xref:System.Data.DataView>:</span></span>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.Cast%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.OrderBy%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.OrderByDescending%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.Select%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.ThenBy%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.ThenByDescending%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.Where%2A>  
  
 <span data-ttu-id="1a160-119">请注意，当 <xref:System.Data.DataView> 从 LINQ to DataSet 查询创建时，该 <xref:System.Data.EnumerableRowCollectionExtensions.Select%2A> 方法必须是查询中调用的最后一个方法。</span><span class="sxs-lookup"><span data-stu-id="1a160-119">Note that when a <xref:System.Data.DataView> is created from a LINQ to DataSet query the <xref:System.Data.EnumerableRowCollectionExtensions.Select%2A> method must be the final method called in the query.</span></span> <span data-ttu-id="1a160-120">下面的示例对此进行了演示，该示例将创建 <xref:System.Data.DataView> 按总计到期时间排序的联机订单：</span><span class="sxs-lookup"><span data-stu-id="1a160-120">This is shown in the following example, which creates a <xref:System.Data.DataView> of online orders sorted by total due:</span></span>  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQuery1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquery1)]
 [!code-vb[DP DataView Samples#CreateLDVFromQuery1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquery1)]  
  
 <span data-ttu-id="1a160-121">还可以使用基于字符串的 <xref:System.Data.DataView.RowFilter%2A> 和属性，在 <xref:System.Data.DataView.Sort%2A> <xref:System.Data.DataView> 通过查询创建后对其进行筛选和排序。</span><span class="sxs-lookup"><span data-stu-id="1a160-121">You can also use the string-based <xref:System.Data.DataView.RowFilter%2A> and <xref:System.Data.DataView.Sort%2A> properties to filter and sort a <xref:System.Data.DataView> after it has been created from a query.</span></span> <span data-ttu-id="1a160-122">请注意，这将清除继承自查询的排序和筛选信息。</span><span class="sxs-lookup"><span data-stu-id="1a160-122">Note that this will clear the sorting and filtering information inherited from the query.</span></span> <span data-ttu-id="1a160-123">下面的示例创建一个 <xref:System.Data.DataView> 来自 LINQ to DataSet 查询的，该查询按以 "s" 开头的姓氏进行筛选。</span><span class="sxs-lookup"><span data-stu-id="1a160-123">The following example creates a <xref:System.Data.DataView> from a LINQ to DataSet query that filters by last names that start with 'S'.</span></span> <span data-ttu-id="1a160-124">将基于字符串的 <xref:System.Data.DataView.Sort%2A> 属性设置为先按姓氏升序排序，然后按名字降序排序：</span><span class="sxs-lookup"><span data-stu-id="1a160-124">The string-based <xref:System.Data.DataView.Sort%2A> property is set to sort on last names in ascending order and then first names in descending order:</span></span>  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquerystringsort)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquerystringsort)]  
  
## <a name="creating-a-dataview-from-a-datatable"></a><span data-ttu-id="1a160-125">从数据表创建 DataView</span><span class="sxs-lookup"><span data-stu-id="1a160-125">Creating a DataView from a DataTable</span></span>  

 <span data-ttu-id="1a160-126">除了从 LINQ to DataSet 查询创建，还 <xref:System.Data.DataView> 可以使用方法从创建对象 <xref:System.Data.DataTable> <xref:System.Data.DataTableExtensions.AsDataView%2A> 。</span><span class="sxs-lookup"><span data-stu-id="1a160-126">In addition to being created from a LINQ to DataSet query, a <xref:System.Data.DataView> object can be created from a <xref:System.Data.DataTable> by using the <xref:System.Data.DataTableExtensions.AsDataView%2A> method.</span></span>  
  
 <span data-ttu-id="1a160-127">下面的示例从 SalesOrderDetail 表创建 <xref:System.Data.DataView> 并将其设置为 <xref:System.Windows.Forms.BindingSource> 对象的数据源。</span><span class="sxs-lookup"><span data-stu-id="1a160-127">The following example creates a <xref:System.Data.DataView> from the SalesOrderDetail table and sets it as the data source of a <xref:System.Windows.Forms.BindingSource> object.</span></span> <span data-ttu-id="1a160-128">此对象充当 <xref:System.Windows.Forms.DataGridView> 控件的代理。</span><span class="sxs-lookup"><span data-stu-id="1a160-128">This object acts as a proxy for a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromtable)]
 [!code-vb[DP DataView Samples#CreateLDVFromTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromtable)]  
  
 <span data-ttu-id="1a160-129">在从 <xref:System.Data.DataView> 创建 <xref:System.Data.DataTable> 后，可以在其上设置筛选和排序。</span><span class="sxs-lookup"><span data-stu-id="1a160-129">Filtering and sorting can be set on the <xref:System.Data.DataView> after it has been created from a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="1a160-130">下面的示例从 Contact 表创建 <xref:System.Data.DataView> 并将 <xref:System.Data.DataView.Sort%2A> 属性设置为先按姓氏升序排序，然后按名字降序排序：</span><span class="sxs-lookup"><span data-stu-id="1a160-130">The following example creates a <xref:System.Data.DataView> from the Contact table and sets the <xref:System.Data.DataView.Sort%2A> property to sort on last names in ascending order and then first names in descending order:</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvstringsort)]
 [!code-vb[DP DataView Samples#LDVStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvstringsort)]  
  
 <span data-ttu-id="1a160-131">不过，在通过查询创建 <xref:System.Data.DataView.RowFilter%2A> 之后，设置 <xref:System.Data.DataView.Sort%2A> 或 <xref:System.Data.DataView> 属性会带来性能降低，因为 <xref:System.Data.DataView> 将会构造一个索引来支持筛选和排序操作。</span><span class="sxs-lookup"><span data-stu-id="1a160-131">However, there is a performance loss that comes with setting the <xref:System.Data.DataView.RowFilter%2A> or <xref:System.Data.DataView.Sort%2A> property after the <xref:System.Data.DataView> has been created from a query, because <xref:System.Data.DataView> constructs an index to support filtering and sorting operations.</span></span> <span data-ttu-id="1a160-132">设置 <xref:System.Data.DataView.RowFilter%2A> 或 <xref:System.Data.DataView.Sort%2A> 属性会重新生成数据的索引，从而增加应用程序的系统开销并降低性能。</span><span class="sxs-lookup"><span data-stu-id="1a160-132">Setting the <xref:System.Data.DataView.RowFilter%2A> or <xref:System.Data.DataView.Sort%2A> property rebuilds the index for the data, adding overhead to your application and decreasing performance.</span></span> <span data-ttu-id="1a160-133">在可能的情况下，最好在第一次创建 <xref:System.Data.DataView> 时指定筛选和排序信息并避免之后对其进行修改。</span><span class="sxs-lookup"><span data-stu-id="1a160-133">When possible, it is better to specify the filtering and sorting information when you first create the <xref:System.Data.DataView> and avoid modifying it afterwards.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a160-134">请参阅</span><span class="sxs-lookup"><span data-stu-id="1a160-134">See also</span></span>

- [<span data-ttu-id="1a160-135">数据绑定和 LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="1a160-135">Data Binding and LINQ to DataSet</span></span>](data-binding-and-linq-to-dataset.md)
- [<span data-ttu-id="1a160-136">使用 DataView 进行筛选</span><span class="sxs-lookup"><span data-stu-id="1a160-136">Filtering with DataView</span></span>](filtering-with-dataview-linq-to-dataset.md)
- [<span data-ttu-id="1a160-137">使用 DataView 进行排序</span><span class="sxs-lookup"><span data-stu-id="1a160-137">Sorting with DataView</span></span>](sorting-with-dataview-linq-to-dataset.md)
