---
description: '了解有关详细信息，请参阅如何：使用 LINQ (修改数据库中的数据 Visual Basic) '
title: 如何：使用 LINQ 修改数据库中的数据
ms.date: 07/20/2015
helpviewer_keywords:
- inserting rows [LINQ to SQL]
- deleting rows [LINQ to SQL]
- updating rows [LINQ to SQL]
- inserting data [Visual Basic]
- deleting data
- data [Visual Basic], updating
- updating data [LINQ]
- queries [LINQ in Visual Basic], data changes in database
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: cf52635f-0c1b-46c3-aff1-bdf181cf19b1
ms.openlocfilehash: b58ca542fbc6f4d63705e45b53edc8ded83ab88b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100422765"
---
# <a name="how-to-modify-data-in-a-database-by-using-linq-visual-basic"></a><span data-ttu-id="e1907-103">如何：使用 LINQ 修改数据库中的数据 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e1907-103">How to: Modify Data in a Database by Using LINQ (Visual Basic)</span></span>

<span data-ttu-id="e1907-104">Language-Integrated Query (LINQ) 查询可以轻松地访问数据库信息和修改数据库中的值。</span><span class="sxs-lookup"><span data-stu-id="e1907-104">Language-Integrated Query (LINQ) queries make it easy to access database information and modify values in the database.</span></span>

<span data-ttu-id="e1907-105">下面的示例演示如何创建一个新的应用程序，用于检索和更新 SQL Server 数据库中的信息。</span><span class="sxs-lookup"><span data-stu-id="e1907-105">The following example shows how to create a new application that retrieves and updates information in a SQL Server database.</span></span>

<span data-ttu-id="e1907-106">本主题中的示例使用 Northwind 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="e1907-106">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="e1907-107">如果你的开发计算机上没有此数据库，可以从 Microsoft 下载中心进行下载。</span><span class="sxs-lookup"><span data-stu-id="e1907-107">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="e1907-108">有关说明，请参阅 [下载示例数据库](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="e1907-108">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>

### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="e1907-109">创建与数据库的连接</span><span class="sxs-lookup"><span data-stu-id="e1907-109">To create a connection to a database</span></span>

1. <span data-ttu-id="e1907-110">在 Visual Studio 中，  / 通过单击 "**查看**" 菜单打开服务器资源管理器 **数据库资源管理器**，然后选择 "**服务器资源管理器** / **数据库资源管理器**"。</span><span class="sxs-lookup"><span data-stu-id="e1907-110">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking the **View** menu, and then select **Server Explorer**/**Database Explorer**.</span></span>

2. <span data-ttu-id="e1907-111">右键单击 **服务器资源管理器** 数据库资源管理器中的 "**数据连接** / "，然后单击 "**添加连接**"。</span><span class="sxs-lookup"><span data-stu-id="e1907-111">Right-click **Data Connections** in **Server Explorer**/**Database Explorer**, and click **Add Connection**.</span></span>

3. <span data-ttu-id="e1907-112">指定与 Northwind 示例数据库的有效连接。</span><span class="sxs-lookup"><span data-stu-id="e1907-112">Specify a valid connection to the Northwind sample database.</span></span>

### <a name="to-add-a-project-with-a-linq-to-sql-file"></a><span data-ttu-id="e1907-113">使用 LINQ to SQL 文件添加项目</span><span class="sxs-lookup"><span data-stu-id="e1907-113">To add a Project with a LINQ to SQL file</span></span>

1. <span data-ttu-id="e1907-114">在 Visual Studio 中的“文件”菜单上，指向“新建”，然后单击“项目”。</span><span class="sxs-lookup"><span data-stu-id="e1907-114">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="e1907-115">选择 Visual Basic **Windows 窗体应用程序** 作为项目类型。</span><span class="sxs-lookup"><span data-stu-id="e1907-115">Select Visual Basic **Windows Forms Application** as the project type.</span></span>

2. <span data-ttu-id="e1907-116">在 **“项目”** 菜单上，单击 **“添加新项”**。</span><span class="sxs-lookup"><span data-stu-id="e1907-116">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="e1907-117">选择 " **LINQ to SQL 类** " 项模板。</span><span class="sxs-lookup"><span data-stu-id="e1907-117">Select the **LINQ to SQL Classes** item template.</span></span>

3. <span data-ttu-id="e1907-118">命名文件 `northwind.dbml`。</span><span class="sxs-lookup"><span data-stu-id="e1907-118">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="e1907-119">单击 **添加**。</span><span class="sxs-lookup"><span data-stu-id="e1907-119">Click **Add**.</span></span> <span data-ttu-id="e1907-120">将为文件打开对象关系设计器 (O/R 设计器) `northwind.dbml` 。</span><span class="sxs-lookup"><span data-stu-id="e1907-120">The Object Relational Designer (O/R Designer) is opened for the `northwind.dbml` file.</span></span>

### <a name="to-add-tables-to-query-and-modify-to-the-designer"></a><span data-ttu-id="e1907-121">添加要查询和修改设计器的表</span><span class="sxs-lookup"><span data-stu-id="e1907-121">To add tables to query and modify to the designer</span></span>

1. <span data-ttu-id="e1907-122">在 **服务器资源管理器** / **数据库资源管理器** 中，展开与 Northwind 数据库的连接。</span><span class="sxs-lookup"><span data-stu-id="e1907-122">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="e1907-123">展开 **“表”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="e1907-123">Expand the **Tables** folder.</span></span>

     <span data-ttu-id="e1907-124">如果关闭了 O/R 设计器，则可以通过双击先前添加的文件重新打开它 `northwind.dbml` 。</span><span class="sxs-lookup"><span data-stu-id="e1907-124">If you have closed the O/R Designer, you can reopen it by double-clicking the `northwind.dbml` file that you added earlier.</span></span>

2. <span data-ttu-id="e1907-125">单击 "Customers" 表，并将其拖到设计器的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="e1907-125">Click the Customers table and drag it to the left pane of the designer.</span></span>

     <span data-ttu-id="e1907-126">设计器将为您的项目创建一个新的客户对象。</span><span class="sxs-lookup"><span data-stu-id="e1907-126">The designer creates a new Customer object for your project.</span></span>

3. <span data-ttu-id="e1907-127">保存更改并关闭设计器。</span><span class="sxs-lookup"><span data-stu-id="e1907-127">Save your changes and close the designer.</span></span>

4. <span data-ttu-id="e1907-128">保存你的项目。</span><span class="sxs-lookup"><span data-stu-id="e1907-128">Save your project.</span></span>

### <a name="to-add-code-to-modify-the-database-and-display-the-results"></a><span data-ttu-id="e1907-129">添加代码以修改数据库并显示结果</span><span class="sxs-lookup"><span data-stu-id="e1907-129">To add code to modify the database and display the results</span></span>

1. <span data-ttu-id="e1907-130">从 " **工具箱**" 中，将 <xref:System.Windows.Forms.DataGridView> 控件拖动到项目的默认 Windows 窗体 "Form1"。</span><span class="sxs-lookup"><span data-stu-id="e1907-130">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>

2. <span data-ttu-id="e1907-131">在将表添加到 O/R 设计器后，设计器会将 <xref:System.Data.Linq.DataContext> 对象添加到项目。</span><span class="sxs-lookup"><span data-stu-id="e1907-131">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="e1907-132">此对象包含可用于访问 Customers 表的代码。</span><span class="sxs-lookup"><span data-stu-id="e1907-132">This object contains code that you can use to access the Customers table.</span></span> <span data-ttu-id="e1907-133">它还包含用于定义表的本地 Customer 对象和 Customer 集合的代码。</span><span class="sxs-lookup"><span data-stu-id="e1907-133">It also contains code that defines  a local Customer object and a Customers collection for the table.</span></span> <span data-ttu-id="e1907-134"><xref:System.Data.Linq.DataContext>项目的对象根据 .dbml 文件的名称进行命名。</span><span class="sxs-lookup"><span data-stu-id="e1907-134">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="e1907-135">对于此项目，该 <xref:System.Data.Linq.DataContext> 对象的名称为 `northwindDataContext` 。</span><span class="sxs-lookup"><span data-stu-id="e1907-135">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>

     <span data-ttu-id="e1907-136">您可以 <xref:System.Data.Linq.DataContext> 在代码中创建对象的实例，并查询和修改 O/R 设计器指定的 Customers 集合。</span><span class="sxs-lookup"><span data-stu-id="e1907-136">You can create an instance of the <xref:System.Data.Linq.DataContext> object in your code and query and modify the Customers collection specified by the O/R Designer.</span></span> <span data-ttu-id="e1907-137">在通过调用对象的方法提交用户集合之前，对这些更改所做的更改不会反映在数据库中 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> <xref:System.Data.Linq.DataContext> 。</span><span class="sxs-lookup"><span data-stu-id="e1907-137">Changes that you make to the Customers collection are not reflected in the database until you submit them by calling the <xref:System.Data.Linq.DataContext.SubmitChanges%2A> method of the <xref:System.Data.Linq.DataContext> object.</span></span>

     <span data-ttu-id="e1907-138">双击 Windows 窗体 "Form1"，将代码添加到事件， <xref:System.Windows.Forms.Form.Load> 以查询作为的属性公开的 Customers 表 <xref:System.Data.Linq.DataContext> 。</span><span class="sxs-lookup"><span data-stu-id="e1907-138">Double-click the Windows Form, Form1, to add code to the <xref:System.Windows.Forms.Form.Load> event to query the Customers table that is exposed as a property of your <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="e1907-139">添加以下代码：</span><span class="sxs-lookup"><span data-stu-id="e1907-139">Add the following code:</span></span>

    ```vb
    Private db As northwindDataContext

    Private Sub Form1_Load(ByVal sender As System.Object,
                           ByVal e As System.EventArgs
                          ) Handles MyBase.Load
      db = New northwindDataContext()

      RefreshData()
    End Sub

    Private Sub RefreshData()
      Dim customers = From cust In db.Customers
                      Where cust.City(0) = "W"
                      Select cust

      DataGridView1.DataSource = customers
    End Sub
    ```

3. <span data-ttu-id="e1907-140">从 " **工具箱**" 中，将三个 <xref:System.Windows.Forms.Button> 控件拖到窗体上。</span><span class="sxs-lookup"><span data-stu-id="e1907-140">From the **Toolbox**, drag three <xref:System.Windows.Forms.Button> controls onto the form.</span></span> <span data-ttu-id="e1907-141">选择第一个 `Button` 控件。</span><span class="sxs-lookup"><span data-stu-id="e1907-141">Select the first `Button` control.</span></span> <span data-ttu-id="e1907-142">在 " **属性** " 窗口中，将控件的设置为，并将设置为 `Name` `Button` `AddButton` `Text` `Add` 。</span><span class="sxs-lookup"><span data-stu-id="e1907-142">In the **Properties** window, set the `Name` of the `Button` control to `AddButton` and the `Text` to `Add`.</span></span> <span data-ttu-id="e1907-143">选择第二个按钮，并将 `Name` 属性设置为 `UpdateButton` ，并将属性设置 `Text` 为 `Update` 。</span><span class="sxs-lookup"><span data-stu-id="e1907-143">Select the second button and set the `Name` property to `UpdateButton` and the `Text` property to `Update`.</span></span> <span data-ttu-id="e1907-144">选择第三个按钮，并将 `Name` 属性设置为 `DeleteButton` ，并将属性设置 `Text` 为 `Delete` 。</span><span class="sxs-lookup"><span data-stu-id="e1907-144">Select the third button and set the `Name` property to `DeleteButton` and the `Text` property to `Delete`.</span></span>

4. <span data-ttu-id="e1907-145">双击 " **添加** " 按钮，将代码添加到其 `Click` 事件。</span><span class="sxs-lookup"><span data-stu-id="e1907-145">Double-click the **Add** button to add code to its `Click` event.</span></span> <span data-ttu-id="e1907-146">添加以下代码：</span><span class="sxs-lookup"><span data-stu-id="e1907-146">Add the following code:</span></span>

    ```vb
    Private Sub AddButton_Click(ByVal sender As System.Object,
                                ByVal e As System.EventArgs
                               ) Handles AddButton.Click
      Dim cust As New Customer With {
        .City = "Wellington",
        .CompanyName = "Blue Yonder Airlines",
        .ContactName = "Jill Frank",
        .Country = "New Zealand",
        .CustomerID = "JILLF"}

      db.Customers.InsertOnSubmit(cust)

      Try
        db.SubmitChanges()
      Catch
        ' Handle exception.
      End Try

      RefreshData()
    End Sub
    ```

5. <span data-ttu-id="e1907-147">双击 " **更新** " 按钮以向其 `Click` 事件中添加代码。</span><span class="sxs-lookup"><span data-stu-id="e1907-147">Double-click the **Update** button to add code to its `Click` event.</span></span> <span data-ttu-id="e1907-148">添加以下代码：</span><span class="sxs-lookup"><span data-stu-id="e1907-148">Add the following code:</span></span>

    ```vb
    Private Sub UpdateButton_Click(ByVal sender As System.Object, _
                                   ByVal e As System.EventArgs
                                  ) Handles UpdateButton.Click
      Dim updateCust = (From cust In db.Customers
                        Where cust.CustomerID = "JILLF").ToList()(0)

      updateCust.ContactName = "Jill Shrader"
      updateCust.Country = "Wales"
      updateCust.CompanyName = "Red Yonder Airlines"
      updateCust.City = "Cardiff"

      Try
        db.SubmitChanges()
      Catch
        ' Handle exception.
      End Try

      RefreshData()
    End Sub
    ```

6. <span data-ttu-id="e1907-149">双击 " **删除** " 按钮以向其事件添加代码 `Click` 。</span><span class="sxs-lookup"><span data-stu-id="e1907-149">Double-click the **Delete** button to add code to its `Click` event.</span></span> <span data-ttu-id="e1907-150">添加以下代码：</span><span class="sxs-lookup"><span data-stu-id="e1907-150">Add the following code:</span></span>

    ```vb
    Private Sub DeleteButton_Click(ByVal sender As System.Object, _
                                   ByVal e As System.EventArgs
                                  ) Handles DeleteButton.Click
      Dim deleteCust = (From cust In db.Customers
                        Where cust.CustomerID = "JILLF").ToList()(0)

      db.Customers.DeleteOnSubmit(deleteCust)

      Try
        db.SubmitChanges()
      Catch
        ' Handle exception.
      End Try

      RefreshData()
    End Sub
    ```

7. <span data-ttu-id="e1907-151">按 F5 运行项目。</span><span class="sxs-lookup"><span data-stu-id="e1907-151">Press F5 to run your project.</span></span> <span data-ttu-id="e1907-152">单击 " **添加** " 以添加新记录。</span><span class="sxs-lookup"><span data-stu-id="e1907-152">Click **Add** to add a new record.</span></span> <span data-ttu-id="e1907-153">单击 " **更新** " 以修改新记录。</span><span class="sxs-lookup"><span data-stu-id="e1907-153">Click **Update** to modify the new record.</span></span> <span data-ttu-id="e1907-154">单击 " **删除** " 以删除新记录。</span><span class="sxs-lookup"><span data-stu-id="e1907-154">Click **Delete** to delete the new record.</span></span>

## <a name="see-also"></a><span data-ttu-id="e1907-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e1907-155">See also</span></span>

- [<span data-ttu-id="e1907-156">LINQ</span><span class="sxs-lookup"><span data-stu-id="e1907-156">LINQ</span></span>](index.md)
- [<span data-ttu-id="e1907-157">查询</span><span class="sxs-lookup"><span data-stu-id="e1907-157">Queries</span></span>](../../../language-reference/queries/index.md)
- [<span data-ttu-id="e1907-158">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="e1907-158">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="e1907-159">DataContext 方法（O/R 设计器）</span><span class="sxs-lookup"><span data-stu-id="e1907-159">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [<span data-ttu-id="e1907-160">如何：分配存储流程来执行更新、插入和删除操作（O/R 设计器）</span><span class="sxs-lookup"><span data-stu-id="e1907-160">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
