---
description: 了解详细信息：如何：动态创建数据库
title: 如何：动态创建数据库
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb7f23c4-4572-4c38-9898-a287807d070c
ms.openlocfilehash: b9addce6befc63f91358d6ecae57e40d6123b200
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738970"
---
# <a name="how-to-dynamically-create-a-database"></a><span data-ttu-id="91ce2-103">如何：动态创建数据库</span><span class="sxs-lookup"><span data-stu-id="91ce2-103">How to: Dynamically Create a Database</span></span>

<span data-ttu-id="91ce2-104">在 LINQ to SQL 中，对象模型映射到关系数据库。</span><span class="sxs-lookup"><span data-stu-id="91ce2-104">In LINQ to SQL, an object model is mapped to a relational database.</span></span> <span data-ttu-id="91ce2-105">通过使用基于属性的映射或外部映射文件启用映射，以描述关系数据库的结构。</span><span class="sxs-lookup"><span data-stu-id="91ce2-105">Mapping is enabled by using attribute-based mapping or an external mapping file to describe the structure of the relational database.</span></span> <span data-ttu-id="91ce2-106">在两种方案中，存在足够的有关使用 <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> 方法创建新的数据库实例的关系数据库的信息。</span><span class="sxs-lookup"><span data-stu-id="91ce2-106">In both scenarios, there is enough information about the relational database that you can create a new instance of the database using the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="91ce2-107"><xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> 方法仅根据对象模型中已编码的信息创建数据库的副本。</span><span class="sxs-lookup"><span data-stu-id="91ce2-107">The <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method creates a replica of the database only to the extent of the information encoded in the object model.</span></span> <span data-ttu-id="91ce2-108">映射文件和您的对象模型中的属性可能不会对有关现有数据库结构的所有内容都进行编码。</span><span class="sxs-lookup"><span data-stu-id="91ce2-108">Mapping files and attributes from your object model might not encode everything about the structure of an existing database.</span></span> <span data-ttu-id="91ce2-109">映射信息不表示用户定义的函数、存储过程、触发器或 CHECK 约束的内容。</span><span class="sxs-lookup"><span data-stu-id="91ce2-109">Mapping information does not represent the contents of user-defined functions, stored procedures, triggers, or check constraints.</span></span> <span data-ttu-id="91ce2-110">这种行为足以满足各种数据库的需要。</span><span class="sxs-lookup"><span data-stu-id="91ce2-110">This behavior is sufficient for a variety of databases.</span></span>  
  
 <span data-ttu-id="91ce2-111">您可以在任意数量的方案中，尤其是在已知数据提供程序（如 Microsoft SQL Server 2008）可用时，使用 <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="91ce2-111">You can use the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method in any number of scenarios, especially if a known data provider like Microsoft SQL Server 2008 is available.</span></span> <span data-ttu-id="91ce2-112">典型的方案包括：</span><span class="sxs-lookup"><span data-stu-id="91ce2-112">Typical scenarios include the following:</span></span>  
  
- <span data-ttu-id="91ce2-113">您正在生成自动将自身安装到客户系统上的应用程序。</span><span class="sxs-lookup"><span data-stu-id="91ce2-113">You are building an application that automatically installs itself on a customer system.</span></span>  
  
- <span data-ttu-id="91ce2-114">您正在生成需要用本地数据库来保存其脱机状态的客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="91ce2-114">You are building a client application that needs a local database to save its offline state.</span></span>  
  
 <span data-ttu-id="91ce2-115">您还可以通过使用 .mdf 文件或只使用目录名（取决于您的连接字符串），将 <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> 方法与 SQL Server 一起使用。</span><span class="sxs-lookup"><span data-stu-id="91ce2-115">You can also use the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method with SQL Server by using an .mdf file or a catalog name, depending on your connection string.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="91ce2-116">使用连接字符串来定义要创建的数据库和作为数据库创建位置的服务器。</span><span class="sxs-lookup"><span data-stu-id="91ce2-116">uses the connection string to define the database to be created and on which server the database is to be created.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="91ce2-117">请尽可能使用 Windows 集成安全性连接到数据库，以便连接字符串不需要密码。</span><span class="sxs-lookup"><span data-stu-id="91ce2-117">Whenever possible, use Windows Integrated Security to connect to the database so that passwords are not required in the connection string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91ce2-118">示例</span><span class="sxs-lookup"><span data-stu-id="91ce2-118">Example</span></span>  

 <span data-ttu-id="91ce2-119">下面的代码提供了一个示例，此示例演示了如何创建一个名为 MyDVDs.mdf 的新数据库。</span><span class="sxs-lookup"><span data-stu-id="91ce2-119">The following code provides an example of how to create a new database named MyDVDs.mdf.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#5)]
 [!code-vb[DLinqSubmittingChanges#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="91ce2-120">示例</span><span class="sxs-lookup"><span data-stu-id="91ce2-120">Example</span></span>  

 <span data-ttu-id="91ce2-121">您可以使用对象模型按如下方式操作来创建数据库：</span><span class="sxs-lookup"><span data-stu-id="91ce2-121">You can use the object model to create a database by doing the following:</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#6)]
 [!code-vb[DLinqSubmittingChanges#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="91ce2-122">示例</span><span class="sxs-lookup"><span data-stu-id="91ce2-122">Example</span></span>  

 <span data-ttu-id="91ce2-123">生成自动将自身安装在客户系统上的应用程序时，请检查数据库是否已经存在，并且在创建新的数据库前将其删除。</span><span class="sxs-lookup"><span data-stu-id="91ce2-123">When building an application that automatically installs itself on a  customer system, see if the database already exists and drop it before creating a new one.</span></span> <span data-ttu-id="91ce2-124"><xref:System.Data.Linq.DataContext> 类提供帮助您完成此过程的 <xref:System.Data.Linq.DataContext.DatabaseExists%2A> 和 <xref:System.Data.Linq.DataContext.DeleteDatabase%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="91ce2-124">The <xref:System.Data.Linq.DataContext> class provides the <xref:System.Data.Linq.DataContext.DatabaseExists%2A> and <xref:System.Data.Linq.DataContext.DeleteDatabase%2A> methods to help you with this process.</span></span>  
  
 <span data-ttu-id="91ce2-125">下面的示例演示使用这些方法来实现此方法的一种方式：</span><span class="sxs-lookup"><span data-stu-id="91ce2-125">The following example shows one way these methods can be used to implement this approach:</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#7)]
 [!code-vb[DLinqSubmittingChanges#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="91ce2-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="91ce2-126">See also</span></span>

- [<span data-ttu-id="91ce2-127">基于特性的映射</span><span class="sxs-lookup"><span data-stu-id="91ce2-127">Attribute-Based Mapping</span></span>](attribute-based-mapping.md)
- [<span data-ttu-id="91ce2-128">外部映射</span><span class="sxs-lookup"><span data-stu-id="91ce2-128">External Mapping</span></span>](external-mapping.md)
- [<span data-ttu-id="91ce2-129">SQL-CLR 类型映射</span><span class="sxs-lookup"><span data-stu-id="91ce2-129">SQL-CLR Type Mapping</span></span>](sql-clr-type-mapping.md)
- [<span data-ttu-id="91ce2-130">背景信息</span><span class="sxs-lookup"><span data-stu-id="91ce2-130">Background Information</span></span>](background-information.md)
- [<span data-ttu-id="91ce2-131">进行和提交数据更改</span><span class="sxs-lookup"><span data-stu-id="91ce2-131">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
