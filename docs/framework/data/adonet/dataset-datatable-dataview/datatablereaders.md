---
description: 了解详细信息： Datatablereader
title: DataTableReader
ms.date: 03/30/2017
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
ms.openlocfilehash: b3e85ae05c07af18fe6219602b5b40f50a9fbc8a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652596"
---
# <a name="datatablereaders"></a><span data-ttu-id="8265d-103">DataTableReader</span><span class="sxs-lookup"><span data-stu-id="8265d-103">DataTableReaders</span></span>

<span data-ttu-id="8265d-104"><xref:System.Data.DataTableReader> 以一个或多个只读、只进结果集的形式提供 <xref:System.Data.DataTable> 或的 <xref:System.Data.DataSet> 的内容。</span><span class="sxs-lookup"><span data-stu-id="8265d-104">The <xref:System.Data.DataTableReader> presents the contents of a <xref:System.Data.DataTable> or a <xref:System.Data.DataSet> in the form of one or more read-only, forward-only result sets.</span></span>  
  
 <span data-ttu-id="8265d-105">从 **DataTable** 创建 **DataTableReader** 时，生成的 **DataTableReader** 对象包含一个结果集，该结果集的数据与创建它时所用的 **数据表** 相同，但已标记为已删除的任何行除外。</span><span class="sxs-lookup"><span data-stu-id="8265d-105">When you create a **DataTableReader** from a **DataTable**, the resulting **DataTableReader** object contains one result set with the same data as the **DataTable** from which it was created, except for any rows that have been marked as deleted.</span></span> <span data-ttu-id="8265d-106">列的显示顺序与原始 **DataTable** 中的顺序相同。</span><span class="sxs-lookup"><span data-stu-id="8265d-106">The columns appear in the same order as in the original **DataTable**.</span></span>  
  
 <span data-ttu-id="8265d-107">如果 **DataTableReader** 是通过调用创建的，则可以包含多个结果集 <xref:System.Data.DataSet.CreateDataReader%2A> 。</span><span class="sxs-lookup"><span data-stu-id="8265d-107">A **DataTableReader** may contain multiple result sets if it was created by calling <xref:System.Data.DataSet.CreateDataReader%2A>.</span></span> <span data-ttu-id="8265d-108">结果与 **DataSet** 对象的集合中的 **数据表** 顺序相同 <xref:System.Data.DataSet.Tables%2A> 。</span><span class="sxs-lookup"><span data-stu-id="8265d-108">The results are in the same order as the **DataTables** in the **DataSet** object's <xref:System.Data.DataSet.Tables%2A> collection.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8265d-109">本节内容</span><span class="sxs-lookup"><span data-stu-id="8265d-109">In This Section</span></span>  

 [<span data-ttu-id="8265d-110">创建 DataReader</span><span class="sxs-lookup"><span data-stu-id="8265d-110">Creating a DataReader</span></span>](creating-a-datareader.md)  
 <span data-ttu-id="8265d-111">讨论如何创建 **DataTableReader** 对象。</span><span class="sxs-lookup"><span data-stu-id="8265d-111">Discusses how to create a **DataTableReader** object.</span></span>  
  
 [<span data-ttu-id="8265d-112">导航数据表</span><span class="sxs-lookup"><span data-stu-id="8265d-112">Navigating DataTables</span></span>](navigating-datatables.md)  
 <span data-ttu-id="8265d-113">介绍如何使用 **Read** 方法在 **DataTableReader** 的内容中移动。</span><span class="sxs-lookup"><span data-stu-id="8265d-113">Describes the use of the **Read** method to move through the contents of a **DataTableReader**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8265d-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8265d-114">See also</span></span>

- [<span data-ttu-id="8265d-115">在 ADO.NET 中检索和修改数据</span><span class="sxs-lookup"><span data-stu-id="8265d-115">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- [<span data-ttu-id="8265d-116">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="8265d-116">ADO.NET Overview</span></span>](../ado-net-overview.md)
