---
description: 了解详细信息：如何：执行返回 StructuralType 结果的查询
title: 如何：执行返回 StructuralType 结果的查询
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2314f2a2-b1c3-40c4-95bb-cdf9b21a7b53
ms.openlocfilehash: a5666fd84ed7253b58cc49babdfa5f5e4614146c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697538"
---
# <a name="how-to-execute-a-query-that-returns-structuraltype-results"></a><span data-ttu-id="57542-103">如何：执行返回 StructuralType 结果的查询</span><span class="sxs-lookup"><span data-stu-id="57542-103">How to: Execute a Query that Returns StructuralType Results</span></span>

<span data-ttu-id="57542-104">本主题演示如何使用 <xref:System.Data.EntityClient.EntityCommand> 对象针对概念模型执行命令，以及如何使用 <xref:System.Data.Metadata.Edm.StructuralType> 检索 <xref:System.Data.EntityClient.EntityDataReader> 结果。</span><span class="sxs-lookup"><span data-stu-id="57542-104">This topic shows how to execute a command against a conceptual model by using an <xref:System.Data.EntityClient.EntityCommand> object, and how to retrieve the <xref:System.Data.Metadata.Edm.StructuralType> results by using an <xref:System.Data.EntityClient.EntityDataReader>.</span></span> <span data-ttu-id="57542-105"><xref:System.Data.Metadata.Edm.EntityType>、<xref:System.Data.Metadata.Edm.RowType> 和 <xref:System.Data.Metadata.Edm.ComplexType> 类派生自 <xref:System.Data.Metadata.Edm.StructuralType> 类。</span><span class="sxs-lookup"><span data-stu-id="57542-105">The <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.RowType> and <xref:System.Data.Metadata.Edm.ComplexType> classes derive from the <xref:System.Data.Metadata.Edm.StructuralType> class.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="57542-106">运行本示例中的代码</span><span class="sxs-lookup"><span data-stu-id="57542-106">To run the code in this example</span></span>  
  
1. <span data-ttu-id="57542-107">将 [AdventureWorks 销售模型](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) 添加到项目中，并将项目配置为使用实体框架。</span><span class="sxs-lookup"><span data-stu-id="57542-107">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="57542-108">有关详细信息，请参阅 [如何：使用实体数据模型向导](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="57542-108">For more information, see [How to: Use the Entity Data Model Wizard](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="57542-109">在应用程序的代码页中，添加以下 `using` 语句（在 Visual Basic 中为 `Imports`）：</span><span class="sxs-lookup"><span data-stu-id="57542-109">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="57542-110">示例</span><span class="sxs-lookup"><span data-stu-id="57542-110">Example</span></span>  

 <span data-ttu-id="57542-111">本示例执行返回 <xref:System.Data.Metadata.Edm.EntityType> 结果的查询。</span><span class="sxs-lookup"><span data-stu-id="57542-111">This example executes a query that returns <xref:System.Data.Metadata.Edm.EntityType> results.</span></span> <span data-ttu-id="57542-112">如果将以下查询作为自变量传递给 `ExecuteStructuralTypeQuery` 函数，则该函数将显示有关 `Products` 的详细信息：</span><span class="sxs-lookup"><span data-stu-id="57542-112">If you pass the following query as an argument to the `ExecuteStructuralTypeQuery` function, the function displays details about the `Products`:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#SelectProduct](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#selectproduct)]  
  
 <span data-ttu-id="57542-113">如果传递参数化查询（如下面的查询），请将 <xref:System.Data.EntityClient.EntityParameter> 对象添加到 <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> 对象的 <xref:System.Data.EntityClient.EntityCommand> 属性。</span><span class="sxs-lookup"><span data-stu-id="57542-113">If you pass a parameterized query, like the following, add the <xref:System.Data.EntityClient.EntityParameter> objects to the <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> property on the <xref:System.Data.EntityClient.EntityCommand> object.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER_OR_EQUALS](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater_or_equals)]  
  
 [!code-csharp[DP EntityServices Concepts#eSQLStructuralTypes](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#esqlstructuraltypes)]
 [!code-vb[DP EntityServices Concepts#eSQLStructuralTypes](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#esqlstructuraltypes)]  
  
## <a name="see-also"></a><span data-ttu-id="57542-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="57542-114">See also</span></span>

- [<span data-ttu-id="57542-115">实体 SQL 引用</span><span class="sxs-lookup"><span data-stu-id="57542-115">Entity SQL Reference</span></span>](./language-reference/entity-sql-reference.md)
- [<span data-ttu-id="57542-116">用于实体框架的 EntityClient 提供程序</span><span class="sxs-lookup"><span data-stu-id="57542-116">EntityClient Provider for the Entity Framework</span></span>](entityclient-provider-for-the-entity-framework.md)
