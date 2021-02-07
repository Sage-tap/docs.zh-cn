---
description: '了解有关详细信息，请参阅如何：使用 LINQ to SQL 数据源创建数据服务 (WCF Data Services) '
title: 如何：使用 LINQ to SQL 数据源创建数据服务（WCF 数据服务）
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, LINQ to SQL
- WCF Data Services, providers
ms.assetid: 3b01c2fd-8c6e-4bf5-b38f-9e61bdc3c328
ms.openlocfilehash: 18c59cc8a067372f2a5c5b4b25d9aec77515ad98
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99766233"
---
# <a name="how-to-create-a-data-service-using-a-linq-to-sql-data-source-wcf-data-services"></a><span data-ttu-id="fa24f-103">如何：使用 LINQ to SQL 数据源创建数据服务（WCF 数据服务）</span><span class="sxs-lookup"><span data-stu-id="fa24f-103">How to: Create a Data Service Using a LINQ to SQL Data Source (WCF Data Services)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="fa24f-104">WCF Data Services 将实体数据作为数据服务公开。</span><span class="sxs-lookup"><span data-stu-id="fa24f-104">WCF Data Services exposes entity data as a data service.</span></span> <span data-ttu-id="fa24f-105">反射提供程序允许您定义基于任何公开返回实现的成员的类的数据模型 <xref:System.Linq.IQueryable%601> 。</span><span class="sxs-lookup"><span data-stu-id="fa24f-105">The reflection provider enables you to define a data model that is based on any class that exposes members that return an <xref:System.Linq.IQueryable%601> implementation.</span></span> <span data-ttu-id="fa24f-106">为了能够更新数据源中的数据，这些类还必须实现 <xref:System.Data.Services.IUpdatable> 接口。</span><span class="sxs-lookup"><span data-stu-id="fa24f-106">To be able to make updates to data in the data source, these classes must also implement the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="fa24f-107">有关详细信息，请参阅 [数据服务提供程序](data-services-providers-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="fa24f-107">For more information, see [Data Services Providers](data-services-providers-wcf-data-services.md).</span></span> <span data-ttu-id="fa24f-108">本主题演示如何创建通过使用反射提供程序来访问 Northwind 示例数据库的 LINQ to SQL 类，以及如何创建基于这些数据类的数据服务。</span><span class="sxs-lookup"><span data-stu-id="fa24f-108">This topic shows you how to create LINQ to SQL classes that access the Northwind sample database by using the reflection provider, as well as how to create the data service that is based on these data classes.</span></span>

## <a name="to-add-linq-to-sql-classes-to-a-project"></a><span data-ttu-id="fa24f-109">向项目中添加 LINQ to SQL 类</span><span class="sxs-lookup"><span data-stu-id="fa24f-109">To add LINQ to SQL classes to a project</span></span>

1. <span data-ttu-id="fa24f-110">在 Visual Basic 或 c # 应用程序中，在 "**项目**" 菜单上，单击 "**添加**  >  **新项**"。</span><span class="sxs-lookup"><span data-stu-id="fa24f-110">From within a Visual Basic or C# application, on the **Project** menu, click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="fa24f-111">单击 " **LINQ to SQL 类** " 模板。</span><span class="sxs-lookup"><span data-stu-id="fa24f-111">Click the **LINQ to SQL Classes** template.</span></span>

3. <span data-ttu-id="fa24f-112">将名称更改为 " **Northwind**"。</span><span class="sxs-lookup"><span data-stu-id="fa24f-112">Change the name to **Northwind.dbml**.</span></span>

4. <span data-ttu-id="fa24f-113">单击“添加”。</span><span class="sxs-lookup"><span data-stu-id="fa24f-113">Click **Add**.</span></span>

     <span data-ttu-id="fa24f-114">此时，Northwind.dbml 文件将随即添加到项目中且对象关系设计器（O/R 设计器）将打开。</span><span class="sxs-lookup"><span data-stu-id="fa24f-114">The Northwind.dbml file is added to the project and the Object Relational Designer (O/R Designer) opens.</span></span>

5. <span data-ttu-id="fa24f-115">在 **服务器** / **数据库资源管理器** 的 "Northwind" 下，展开 "**表**" 并将 `Customers` 表拖到 "对象关系设计器 (O/R 设计器) "。</span><span class="sxs-lookup"><span data-stu-id="fa24f-115">In **Server**/**Database Explorer**, under Northwind, expand **Tables** and drag the `Customers` table onto the Object Relational Designer (O/R Designer).</span></span>

     <span data-ttu-id="fa24f-116">此时将随即创建一个 `Customer` 实体类并显示在设计图面上。</span><span class="sxs-lookup"><span data-stu-id="fa24f-116">A `Customer` entity class is created and appears on the design surface.</span></span>

6. <span data-ttu-id="fa24f-117">对 `Orders`、`Order_Details` 和 `Products` 表重复步骤 6。</span><span class="sxs-lookup"><span data-stu-id="fa24f-117">Repeat step 6 for the `Orders`, `Order_Details`, and `Products` tables.</span></span>

7. <span data-ttu-id="fa24f-118">右键单击表示 LINQ to SQL 类的新 .dbml 文件，然后单击 " **查看代码**"。</span><span class="sxs-lookup"><span data-stu-id="fa24f-118">Right-click the new .dbml file that represents the LINQ to SQL classes and click **View Code**.</span></span>

     <span data-ttu-id="fa24f-119">这将创建一个名为 Northwind.cs 的新代码隐藏页，其中包含从 <xref:System.Data.Linq.DataContext> 类（在此示例中为 `NorthwindDataContext`）继承的类的分部类定义。</span><span class="sxs-lookup"><span data-stu-id="fa24f-119">This creates a new code-behind page named Northwind.cs that contains a partial class definition for the class that inherits from the <xref:System.Data.Linq.DataContext> class, which in this case is `NorthwindDataContext`.</span></span>

8. <span data-ttu-id="fa24f-120">用下列代码替换 Northwind.cs 代码文件的内容。</span><span class="sxs-lookup"><span data-stu-id="fa24f-120">Replace the contents of the Northwind.cs code file with the following code.</span></span> <span data-ttu-id="fa24f-121">此代码通过扩展 <xref:System.Data.Linq.DataContext> 以及 LINQ to SQL 生成的数据类来实现反射提供程序：</span><span class="sxs-lookup"><span data-stu-id="fa24f-121">This code implements the reflection provider by extending the <xref:System.Data.Linq.DataContext> and data classes generated by LINQ to SQL:</span></span>

     [!code-csharp[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_linq_provider/cs/northwind.cs#linq2sqlprovider)]
     [!code-vb[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_linq_provider/vb/northwind.vb#linq2sqlprovider)]

### <a name="to-create-a-data-service-by-using-a-linq-to-sql-based-data-model"></a><span data-ttu-id="fa24f-122">使用基于 LINQ to SQL 的数据模型创建数据服务</span><span class="sxs-lookup"><span data-stu-id="fa24f-122">To create a data service by using a LINQ to SQL-based data model</span></span>

1. <span data-ttu-id="fa24f-123">在 **解决方案资源管理器** 中，右键单击 ASP.NET 项目的名称，然后单击 "**添加**  >  **新项**"。</span><span class="sxs-lookup"><span data-stu-id="fa24f-123">In **Solution Explorer**, right-click the name of your ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="fa24f-124">在 "**添加新项**" 对话框中，从 " **Web** " 类别中选择 " **WCF 数据服务**" 模板。</span><span class="sxs-lookup"><span data-stu-id="fa24f-124">In the **Add New Item** dialog box, select the **WCF Data Service** template from the **Web** category.</span></span>

   ![Visual Studio 2015 中的 WCF 数据服务项模板](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="fa24f-126">**WCF 数据服务** 模板在 visual studio 2015 中提供，但在 visual studio 2017 或更高版本中不可用。</span><span class="sxs-lookup"><span data-stu-id="fa24f-126">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017 or later.</span></span>

3. <span data-ttu-id="fa24f-127">提供服务的名称，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="fa24f-127">Supply a name for the service, and then click **OK**.</span></span>

     <span data-ttu-id="fa24f-128">Visual Studio 将为新服务创建 XML 标记和代码文件。</span><span class="sxs-lookup"><span data-stu-id="fa24f-128">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="fa24f-129">默认情况下，代码编辑器窗口将打开。</span><span class="sxs-lookup"><span data-stu-id="fa24f-129">By default, the code-editor window opens.</span></span>

4. <span data-ttu-id="fa24f-130">在数据服务的代码中，用数据模型的实体容器的类型（在此示例中为 `/* TODO: put your data source class name here */`）替换定义数据服务的类定义中的注释 `NorthwindDataContext`。</span><span class="sxs-lookup"><span data-stu-id="fa24f-130">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindDataContext`.</span></span>

5. <span data-ttu-id="fa24f-131">在数据服务的代码中，用下列代码替换 `InitializeService` 函数中的占位符代码：</span><span class="sxs-lookup"><span data-stu-id="fa24f-131">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>

     [!code-csharp[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_linq_provider/cs/northwind.svc.cs#enableaccess)]
     [!code-vb[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_linq_provider/vb/northwind.svc.vb#enableaccess)]

     <span data-ttu-id="fa24f-132">这使得授权客户端能够访问指定的三个实体集的资源。</span><span class="sxs-lookup"><span data-stu-id="fa24f-132">This enables authorized clients to access resources for the three specified entity sets.</span></span>

6. <span data-ttu-id="fa24f-133">若要使用 Web 浏览器测试 Northwind 数据服务，请按照主题 [从 Web 浏览器访问该服务](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="fa24f-133">To test the Northwind.svc data service by using a Web browser, follow the instructions in the topic [Accessing the Service from a Web Browser](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fa24f-134">请参阅</span><span class="sxs-lookup"><span data-stu-id="fa24f-134">See also</span></span>

- [<span data-ttu-id="fa24f-135">如何：使用 ADO.NET 实体框架数据源创建数据服务</span><span class="sxs-lookup"><span data-stu-id="fa24f-135">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source</span></span>](create-a-data-service-using-an-adonet-ef-data-wcf.md)
- [<span data-ttu-id="fa24f-136">如何：使用反射提供程序创建数据服务</span><span class="sxs-lookup"><span data-stu-id="fa24f-136">How to: Create a Data Service Using the Reflection Provider</span></span>](create-a-data-service-using-rp-wcf-data-services.md)
- [<span data-ttu-id="fa24f-137">数据服务提供程序</span><span class="sxs-lookup"><span data-stu-id="fa24f-137">Data Services Providers</span></span>](data-services-providers-wcf-data-services.md)
