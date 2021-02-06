---
description: '了解详细信息：演练：跨关系查询 (Visual Basic) '
title: 演练：跨关系查询 (Visual Basic)
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: a7da43e3-769f-4e07-bcd6-552b8bde66f4
ms.openlocfilehash: 002ec53c5a56d988dcd71af658a546d199473425
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650568"
---
# <a name="walkthrough-querying-across-relationships-visual-basic"></a><span data-ttu-id="7b9ac-103">演练：跨关系查询 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b9ac-103">Walkthrough: Querying Across Relationships (Visual Basic)</span></span>

<span data-ttu-id="7b9ac-104">本演练演示如何使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *关联* 来表示数据库中的外键关系。</span><span class="sxs-lookup"><span data-stu-id="7b9ac-104">This walkthrough demonstrates the use of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *associations* to represent foreign-key relationships in the database.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="7b9ac-105">本演练是使用 Visual Basic 开发设置编写的。</span><span class="sxs-lookup"><span data-stu-id="7b9ac-105">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7b9ac-106">先决条件</span><span class="sxs-lookup"><span data-stu-id="7b9ac-106">Prerequisites</span></span>  

 <span data-ttu-id="7b9ac-107">必须已完成 [演练：简单对象模型和查询 (Visual Basic) ](walkthrough-simple-object-model-and-query-visual-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="7b9ac-107">You must have completed [Walkthrough: Simple Object Model and Query (Visual Basic)](walkthrough-simple-object-model-and-query-visual-basic.md).</span></span> <span data-ttu-id="7b9ac-108">本演练建立在该演练基础之上，包括在 c:\linqtest 中须存在 northwnd.mdf 文件。</span><span class="sxs-lookup"><span data-stu-id="7b9ac-108">This walkthrough builds on that one, including the presence of the northwnd.mdf file in c:\linqtest.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="7b9ac-109">概述</span><span class="sxs-lookup"><span data-stu-id="7b9ac-109">Overview</span></span>  

 <span data-ttu-id="7b9ac-110">本演练由三项主要任务组成：</span><span class="sxs-lookup"><span data-stu-id="7b9ac-110">This walkthrough consists of three main tasks:</span></span>  
  
- <span data-ttu-id="7b9ac-111">添加一个实体类以表示 Northwind 示例数据库中的 Orders 表。</span><span class="sxs-lookup"><span data-stu-id="7b9ac-111">Adding an entity class to represent the Orders table in the sample Northwind database.</span></span>  
  
- <span data-ttu-id="7b9ac-112">向 `Customer` 类补充一些批注，以增强 `Customer` 和 `Order` 类之间的关系。</span><span class="sxs-lookup"><span data-stu-id="7b9ac-112">Supplementing annotations to the `Customer` class to enhance the relationship between the `Customer` and `Order` classes.</span></span>  
  
- <span data-ttu-id="7b9ac-113">创建并运行查询以测试通过使用 `Order` 类获取 `Customer` 信息的过程。</span><span class="sxs-lookup"><span data-stu-id="7b9ac-113">Creating and running a query to test the process of obtaining `Order` information by using the `Customer` class.</span></span>  
  
## <a name="mapping-relationships-across-tables"></a><span data-ttu-id="7b9ac-114">跨表映射关系</span><span class="sxs-lookup"><span data-stu-id="7b9ac-114">Mapping Relationships across Tables</span></span>  

 <span data-ttu-id="7b9ac-115">在 `Customer` 类定义的后面，创建包含如下代码的 `Order` 实体类定义，这些代码表示 `Orders.Customer` 作为外键与 `Customers.CustomerID` 相关。</span><span class="sxs-lookup"><span data-stu-id="7b9ac-115">After the `Customer` class definition, create the `Order` entity class definition that includes the following code, which indicates that `Orders.Customer` relates as a foreign key to `Customers.CustomerID`.</span></span>  
  
#### <a name="to-add-the-order-entity-class"></a><span data-ttu-id="7b9ac-116">添加 Order 实体类</span><span class="sxs-lookup"><span data-stu-id="7b9ac-116">To add the Order entity class</span></span>  
  
- <span data-ttu-id="7b9ac-117">在 `Customer` 类后面键入或粘贴如下代码：</span><span class="sxs-lookup"><span data-stu-id="7b9ac-117">Type or paste the following code after the `Customer` class:</span></span>  
  
     [!code-vb[DLinqWalk2VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#1)]  
  
## <a name="annotating-the-customer-class"></a><span data-ttu-id="7b9ac-118">对 Customer 类进行批注</span><span class="sxs-lookup"><span data-stu-id="7b9ac-118">Annotating the Customer Class</span></span>  

 <span data-ttu-id="7b9ac-119">在此步骤中，您要对 `Customer` 类进行批注，以指示它与 `Order` 类的关系。</span><span class="sxs-lookup"><span data-stu-id="7b9ac-119">In this step, you annotate the `Customer` class to indicate its relationship to the `Order` class.</span></span> <span data-ttu-id="7b9ac-120">（这种添加批注的操作并非绝对必需的，因为定义任一方向上的关系都足以满足创建链接的需要。</span><span class="sxs-lookup"><span data-stu-id="7b9ac-120">(This addition is not strictly necessary, because defining the relationship in either direction is sufficient to create the link.</span></span> <span data-ttu-id="7b9ac-121">但添加此批注确实便于您在任一方向上定位对象。）</span><span class="sxs-lookup"><span data-stu-id="7b9ac-121">But adding this annotation does enable you to easily navigate objects in either direction.)</span></span>  
  
#### <a name="to-annotate-the-customer-class"></a><span data-ttu-id="7b9ac-122">对 Customer 类进行批注</span><span class="sxs-lookup"><span data-stu-id="7b9ac-122">To annotate the Customer class</span></span>  
  
- <span data-ttu-id="7b9ac-123">将下面的代码键入或粘贴到 `Customer` 类中：</span><span class="sxs-lookup"><span data-stu-id="7b9ac-123">Type or paste the following code into the `Customer` class:</span></span>  
  
     [!code-vb[DLinqWalk2VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#2)]  
  
## <a name="creating-and-running-a-query-across-the-customer-order-relationship"></a><span data-ttu-id="7b9ac-124">跨 Customer-Order 关系创建并运行查询</span><span class="sxs-lookup"><span data-stu-id="7b9ac-124">Creating and Running a Query across the Customer-Order Relationship</span></span>  

 <span data-ttu-id="7b9ac-125">现在您可以直接从 `Order` 对象访问 `Customer` 对象，或反过来进行访问。</span><span class="sxs-lookup"><span data-stu-id="7b9ac-125">You can now access `Order` objects directly from the `Customer` objects, or in the opposite order.</span></span> <span data-ttu-id="7b9ac-126">客户和订单之间不需要显式 *联接* 。</span><span class="sxs-lookup"><span data-stu-id="7b9ac-126">You do not need an explicit *join* between customers and orders.</span></span>  
  
#### <a name="to-access-order-objects-by-using-customer-objects"></a><span data-ttu-id="7b9ac-127">使用 Customer 对象访问 Order 对象</span><span class="sxs-lookup"><span data-stu-id="7b9ac-127">To access Order objects by using Customer objects</span></span>  
  
1. <span data-ttu-id="7b9ac-128">通过将下面的代码键入或粘贴到 `Sub Main` 方法中修改此方法：</span><span class="sxs-lookup"><span data-stu-id="7b9ac-128">Modify the `Sub Main` method by typing or pasting the following code into the method:</span></span>  
  
     [!code-vb[DLinqWalk2VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#3)]  
  
2. <span data-ttu-id="7b9ac-129">按 F5 调试应用程序。</span><span class="sxs-lookup"><span data-stu-id="7b9ac-129">Press F5 to debug your application.</span></span>  
  
     <span data-ttu-id="7b9ac-130">消息框中会显示两个名称，并且控制台窗口会显示生成的 SQL 代码。</span><span class="sxs-lookup"><span data-stu-id="7b9ac-130">Two names appear in the message box, and the Console window shows the generated SQL code.</span></span>  
  
3. <span data-ttu-id="7b9ac-131">关闭此消息框以停止调试。</span><span class="sxs-lookup"><span data-stu-id="7b9ac-131">Close the message box to stop debugging.</span></span>  
  
## <a name="creating-a-strongly-typed-view-of-your-database"></a><span data-ttu-id="7b9ac-132">创建数据库的强类型化视图</span><span class="sxs-lookup"><span data-stu-id="7b9ac-132">Creating a Strongly Typed View of Your Database</span></span>  

 <span data-ttu-id="7b9ac-133">从数据库的强类型化视图着手要容易得多。</span><span class="sxs-lookup"><span data-stu-id="7b9ac-133">It is much easier to start with a strongly typed view of your database.</span></span> <span data-ttu-id="7b9ac-134">通过将 <xref:System.Data.Linq.DataContext> 对象强类型化，您无需调用 <xref:System.Data.Linq.DataContext.GetTable%2A>。</span><span class="sxs-lookup"><span data-stu-id="7b9ac-134">By strongly typing the <xref:System.Data.Linq.DataContext> object, you do not need calls to <xref:System.Data.Linq.DataContext.GetTable%2A>.</span></span> <span data-ttu-id="7b9ac-135">当您使用强类型化的 <xref:System.Data.Linq.DataContext> 对象时，您可以在所有查询中使用强类型化表。</span><span class="sxs-lookup"><span data-stu-id="7b9ac-135">You can use strongly typed tables in all your queries when you use the strongly typed <xref:System.Data.Linq.DataContext> object.</span></span>  
  
 <span data-ttu-id="7b9ac-136">在以下步骤中，您将创建 `Customers` 作为映射到数据库中的 Customers 表的强类型化表。</span><span class="sxs-lookup"><span data-stu-id="7b9ac-136">In the following steps, you will create `Customers` as a strongly typed table that maps to the Customers table in the database.</span></span>  
  
#### <a name="to-strongly-type-the-datacontext-object"></a><span data-ttu-id="7b9ac-137">对 DataContext 对象进行强类型化</span><span class="sxs-lookup"><span data-stu-id="7b9ac-137">To strongly type the DataContext object</span></span>  
  
1. <span data-ttu-id="7b9ac-138">将下面的代码添加到 `Customer` 类声明的上方。</span><span class="sxs-lookup"><span data-stu-id="7b9ac-138">Add the following code above the `Customer` class declaration.</span></span>  
  
     [!code-vb[DLinqWalk2VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#4)]  
  
2. <span data-ttu-id="7b9ac-139">将 `Sub Main` 修改为使用强类型化的 <xref:System.Data.Linq.DataContext>，如下所示：</span><span class="sxs-lookup"><span data-stu-id="7b9ac-139">Modify `Sub Main` to use the strongly typed <xref:System.Data.Linq.DataContext> as follows:</span></span>  
  
     [!code-vb[DLinqWalk2VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#5)]  
  
3. <span data-ttu-id="7b9ac-140">按 F5 调试应用程序。</span><span class="sxs-lookup"><span data-stu-id="7b9ac-140">Press F5 to debug your application.</span></span>  
  
     <span data-ttu-id="7b9ac-141">控制台窗口输出如下：</span><span class="sxs-lookup"><span data-stu-id="7b9ac-141">The Console window output is:</span></span>  
  
     `ID=WHITC`  
  
4. <span data-ttu-id="7b9ac-142">在控制台窗口中按 Enter，以关闭应用程序。</span><span class="sxs-lookup"><span data-stu-id="7b9ac-142">Press Enter in the Console window to close the application.</span></span>  
  
5. <span data-ttu-id="7b9ac-143">如果要保存此应用程序，请在 " **文件** " 菜单上，单击 " **全部保存** "。</span><span class="sxs-lookup"><span data-stu-id="7b9ac-143">On the **File** menu, click **Save All** if you want to save this application.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="7b9ac-144">后续步骤</span><span class="sxs-lookup"><span data-stu-id="7b9ac-144">Next Steps</span></span>  

 <span data-ttu-id="7b9ac-145">下一演练 ([演练：操作数据 (Visual Basic) ](walkthrough-manipulating-data-visual-basic.md)) 演示如何处理数据。</span><span class="sxs-lookup"><span data-stu-id="7b9ac-145">The next walkthrough ([Walkthrough: Manipulating Data (Visual Basic)](walkthrough-manipulating-data-visual-basic.md)) demonstrates how to manipulate data.</span></span> <span data-ttu-id="7b9ac-146">该演练不要求您保存本系列中已经完成的两个演练的结果。</span><span class="sxs-lookup"><span data-stu-id="7b9ac-146">That walkthrough does not require that you save the two walkthroughs in this series that you have already completed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b9ac-147">请参阅</span><span class="sxs-lookup"><span data-stu-id="7b9ac-147">See also</span></span>

- [<span data-ttu-id="7b9ac-148">通过演练学习</span><span class="sxs-lookup"><span data-stu-id="7b9ac-148">Learning by Walkthroughs</span></span>](learning-by-walkthroughs.md)
