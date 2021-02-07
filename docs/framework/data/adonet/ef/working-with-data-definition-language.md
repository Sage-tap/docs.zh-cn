---
description: 了解更多相关信息：使用数据定义语言
title: 使用数据定义语言
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec50083d-44f4-4093-9b23-5eacd601f96e
ms.openlocfilehash: 2f924087d12b519e6086289a91dedce3a88199f5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99673019"
---
# <a name="working-with-data-definition-language"></a><span data-ttu-id="b9571-103">使用数据定义语言</span><span class="sxs-lookup"><span data-stu-id="b9571-103">Working with Data Definition Language</span></span>

<span data-ttu-id="b9571-104">从 .NET Framework 版本4开始，实体框架支持 (DDL) 的数据定义语言。</span><span class="sxs-lookup"><span data-stu-id="b9571-104">Starting with the .NET Framework version 4, the Entity Framework supports data definition language (DDL).</span></span> <span data-ttu-id="b9571-105">这样，您将能够基于连接字符串和存储元数据 (SSDL) 模型创建或删除数据库实例。</span><span class="sxs-lookup"><span data-stu-id="b9571-105">This allows you to create or delete a database instance based on the connection string and the metadata of the storage (SSDL) model.</span></span>  
  
 <span data-ttu-id="b9571-106"><xref:System.Data.Objects.ObjectContext> 的以下方法使用连接字符串和 SSDL 内容来完成以下操作：创建或删除数据库，检查数据库是否存在，以及查看生成的 DDL 脚本：</span><span class="sxs-lookup"><span data-stu-id="b9571-106">The following methods on the <xref:System.Data.Objects.ObjectContext> use the connection string and the SSDL content to accomplish the following: create or delete the database, check whether the database exists, and view the generated DDL script:</span></span>  
  
- <xref:System.Data.Objects.ObjectContext.CreateDatabase%2A>  
  
- <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A>  
  
- <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A>  
  
- <xref:System.Data.Objects.ObjectContext.CreateDatabaseScript%2A>  
  
> [!NOTE]
> <span data-ttu-id="b9571-107">假定有足够的权限可执行 DDL 命令。</span><span class="sxs-lookup"><span data-stu-id="b9571-107">Executing the DDL commands assumes sufficient permissions.</span></span>  
  
 <span data-ttu-id="b9571-108">以上列出的方法将大部分工作都委托给基础 ADO.NET 数据提供程序。</span><span class="sxs-lookup"><span data-stu-id="b9571-108">The methods previously listed delegate most of the work to the underlying ADO.NET data provider.</span></span> <span data-ttu-id="b9571-109">该提供程序负责确保用于生成数据库对象的命名约定与用于查询和更新的约定保持一致。</span><span class="sxs-lookup"><span data-stu-id="b9571-109">It is the provider’s responsibility to ensure that the naming convention used to generate database objects is consistent with conventions used for querying and updates.</span></span>  
  
 <span data-ttu-id="b9571-110">下面的示例演示如何基于现有模型生成数据库。</span><span class="sxs-lookup"><span data-stu-id="b9571-110">The following example shows you how to generate the database based on the existing model.</span></span> <span data-ttu-id="b9571-111">它还将新的实体对象添加到对象上下文中，然后将该对象保存到数据库中。</span><span class="sxs-lookup"><span data-stu-id="b9571-111">It also adds a new entity object to the object context and then saves it to the database.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="b9571-112">过程</span><span class="sxs-lookup"><span data-stu-id="b9571-112">Procedures</span></span>  
  
### <a name="to-define-a-database-based-on-the-existing-model"></a><span data-ttu-id="b9571-113">基于现有模型定义数据库</span><span class="sxs-lookup"><span data-stu-id="b9571-113">To define a database based on the existing model</span></span>  
  
1. <span data-ttu-id="b9571-114">创建控制台应用程序。</span><span class="sxs-lookup"><span data-stu-id="b9571-114">Create a console application.</span></span>  
  
2. <span data-ttu-id="b9571-115">向应用程序中添加现有模型。</span><span class="sxs-lookup"><span data-stu-id="b9571-115">Add an existing model to your application.</span></span>  
  
    1. <span data-ttu-id="b9571-116">添加一个名为的空模型 `SchoolModel` 。</span><span class="sxs-lookup"><span data-stu-id="b9571-116">Add an empty model named `SchoolModel`.</span></span> <span data-ttu-id="b9571-117">若要创建空模型，请参阅 [如何：创建新的 .Edmx 文件](/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100)) 主题。</span><span class="sxs-lookup"><span data-stu-id="b9571-117">To create an empty model, see the [How to: Create a New .edmx File](/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100)) topic.</span></span>  
  
     <span data-ttu-id="b9571-118">将 SchoolModel.edmx 文件添加到您的项目中。</span><span class="sxs-lookup"><span data-stu-id="b9571-118">The SchoolModel.edmx file is added to your project.</span></span>  
  
    1. <span data-ttu-id="b9571-119">从 [School 模型](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) 主题复制 school 模型的概念、存储和映射内容。</span><span class="sxs-lookup"><span data-stu-id="b9571-119">Copy the conceptual, storage, and mapping content for the School model from the [School Model](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) topic.</span></span>  
  
    2. <span data-ttu-id="b9571-120">打开 SchoolModel.edmx 文件并将内容粘贴在 `edmx:Runtime` 标记中。</span><span class="sxs-lookup"><span data-stu-id="b9571-120">Open the SchoolModel.edmx file and paste the content within the `edmx:Runtime` tags.</span></span>  
  
3. <span data-ttu-id="b9571-121">将以下代码添加到主函数中。</span><span class="sxs-lookup"><span data-stu-id="b9571-121">Add the following code to your main function.</span></span> <span data-ttu-id="b9571-122">此类代码将连接字符串初始化为数据库服务器，查看 DDL 脚本，创建数据库，将新实体添加到上下文，并将更改保存到数据库。</span><span class="sxs-lookup"><span data-stu-id="b9571-122">The code initializes the connection string to your database server, views the DDL script, creates the database, adds a new entity to the context, and saves the changes to the database.</span></span>  
  
     [!code-csharp[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/csharp/VS_Snippets_Data/DP ObjectServices Concepts/CS/Source.cs#ddl)]
     [!code-vb[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP ObjectServices Concepts/VB/Source.vb#ddl)]
