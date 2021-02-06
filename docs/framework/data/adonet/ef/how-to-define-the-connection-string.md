---
description: 了解详细信息：如何：定义连接字符串
title: 如何：定义连接字符串
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: 104264299e597bc142a689aa83f3207765d18c67
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650815"
---
# <a name="how-to-define-the-connection-string"></a><span data-ttu-id="6a5ab-103">如何：定义连接字符串</span><span class="sxs-lookup"><span data-stu-id="6a5ab-103">How to: Define the Connection String</span></span>

<span data-ttu-id="6a5ab-104">本主题介绍如何定义在连接到概念模型时使用的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="6a5ab-104">This topic shows how to define the connection string that is used when connecting to a conceptual model.</span></span> <span data-ttu-id="6a5ab-105">本主题基于 [AdventureWorks 销售](/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) 概念模型。</span><span class="sxs-lookup"><span data-stu-id="6a5ab-105">This topic is based on the [AdventureWorks Sales](/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) conceptual model.</span></span> <span data-ttu-id="6a5ab-106">AdventureWorks 销售模型在实体框架文档中的与任务相关的主题中使用。</span><span class="sxs-lookup"><span data-stu-id="6a5ab-106">The AdventureWorks Sales Model is used throughout the task-related topics in the Entity Framework documentation.</span></span> <span data-ttu-id="6a5ab-107">本主题假定您已经配置了实体框架并定义了 AdventureWorks 销售模型。</span><span class="sxs-lookup"><span data-stu-id="6a5ab-107">This topic assumes that you have already configured the Entity Framework and defined the AdventureWorks Sales Model.</span></span> <span data-ttu-id="6a5ab-108">有关详细信息，请参阅 [如何：手动定义模型和映射文件](/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="6a5ab-108">For more information, see [How to: Manually Define the Model and Mapping Files](/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)).</span></span> <span data-ttu-id="6a5ab-109">本主题中的过程也包括在 [如何：手动配置实体框架项目](/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))中。</span><span class="sxs-lookup"><span data-stu-id="6a5ab-109">The procedures in this topic are also included in [How to: Manually Configure an Entity Framework Project](/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).</span></span>

> [!NOTE]
> <span data-ttu-id="6a5ab-110">如果你在 Visual Studio 项目中使用实体数据模型向导，它会自动生成 .edmx 文件并将该项目配置为使用实体框架。</span><span class="sxs-lookup"><span data-stu-id="6a5ab-110">If you use the Entity Data Model Wizard in a Visual Studio project, it automatically generates an .edmx file and configures the project to use the Entity Framework.</span></span> <span data-ttu-id="6a5ab-111">有关详细信息，请参阅 [如何：使用实体数据模型向导](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="6a5ab-111">For more information, see [How to: Use the Entity Data Model Wizard](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>

## <a name="to-define-the-entity-framework-connection-string"></a><span data-ttu-id="6a5ab-112">定义实体框架连接字符串</span><span class="sxs-lookup"><span data-stu-id="6a5ab-112">To define the Entity Framework connection string</span></span>

- <span data-ttu-id="6a5ab-113">打开项目的应用程序配置文件 (app.config) 并添加以下连接字符串：</span><span class="sxs-lookup"><span data-stu-id="6a5ab-113">Open the project's application configuration file (app.config) and add the following connection string:</span></span>

```xml
<connectionStrings>
    <add name="AdventureWorksEntities"
         connectionString="metadata=.\AdventureWorks.csdl|.\AdventureWorks.ssdl|.\AdventureWorks.msl;
         provider=System.Data.SqlClient;provider connection string='Data Source=localhost;
         Initial Catalog=AdventureWorks;Integrated Security=True;Connection Timeout=60;
         multipleactiveresultsets=true'" providerName="System.Data.EntityClient" />
</connectionStrings>
```

<span data-ttu-id="6a5ab-114">如果你的项目没有应用程序配置文件，则可以通过从 "**项目**" 菜单中选择 "**添加新项**"，选择 "**常规**" 类别，选择 "**应用程序配置文件**"，然后单击 "**添加**" 来添加一个。</span><span class="sxs-lookup"><span data-stu-id="6a5ab-114">If your project does not have an application configuration file, you can add one by selecting **Add New Item** from the **Project** menu, selecting the **General** category, selecting **Application Configuration File**, and then clicking **Add**.</span></span>

## <a name="see-also"></a><span data-ttu-id="6a5ab-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="6a5ab-115">See also</span></span>

- <span data-ttu-id="6a5ab-116">[快速入门](/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6a5ab-116">[Quickstart](/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))</span></span>
- <span data-ttu-id="6a5ab-117">[如何：创建新的 .edmx 文件](/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6a5ab-117">[How to: Create a New .edmx File](/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))</span></span>
- <span data-ttu-id="6a5ab-118">[ADO.NET 实体数据模型工具](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6a5ab-118">[ADO.NET Entity Data Model  Tools](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
