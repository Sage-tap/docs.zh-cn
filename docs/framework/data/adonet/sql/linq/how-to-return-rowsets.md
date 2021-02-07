---
description: 了解详细信息：如何：返回行集
title: 如何：返回行集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 725718f5-da29-4841-9f53-aafef64ba977
ms.openlocfilehash: b799ce82542e6929f42485508b3a2c36cc42ee60
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723382"
---
# <a name="how-to-return-rowsets"></a><span data-ttu-id="98901-103">如何：返回行集</span><span class="sxs-lookup"><span data-stu-id="98901-103">How to: Return Rowsets</span></span>

<span data-ttu-id="98901-104">此示例从数据库中返回行集合，并包含用于筛选结果的输入参数。</span><span class="sxs-lookup"><span data-stu-id="98901-104">This example returns a rowset from the database, and includes an input parameter to filter the result.</span></span>  
  
 <span data-ttu-id="98901-105">当执行返回行集的存储过程时，请使用存储过程中存储返回的 *结果* 类。</span><span class="sxs-lookup"><span data-stu-id="98901-105">When you execute a stored procedure that returns a rowset, you use a *result* class that stores the returns from the stored procedure.</span></span> <span data-ttu-id="98901-106">有关详细信息，请参阅 [分析 LINQ to SQL 源代码](analyzing-linq-to-sql-source-code.md)。</span><span class="sxs-lookup"><span data-stu-id="98901-106">For more information, see [Analyzing LINQ to SQL Source Code](analyzing-linq-to-sql-source-code.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="98901-107">示例</span><span class="sxs-lookup"><span data-stu-id="98901-107">Example</span></span>  

 <span data-ttu-id="98901-108">下面的示例表示一个存储过程，该存储过程返回客户行并使用输入参数来仅返回将“London”列为客户城市的那些行。</span><span class="sxs-lookup"><span data-stu-id="98901-108">The following example represents a stored procedure that returns rows of customers and uses an input parameter to return only those rows that list "London" as the customer city.</span></span> <span data-ttu-id="98901-109">该示例假定有一个可枚举的 `CustomersByCityResult` 类。</span><span class="sxs-lookup"><span data-stu-id="98901-109">The example assumes an enumerable `CustomersByCityResult` class.</span></span>  
  
```sql  
CREATE PROCEDURE [dbo].[Customers By City]  
    (@param1 NVARCHAR(20))  
AS  
BEGIN  
    -- SET NOCOUNT ON added to prevent extra result sets from  
    -- interfering with SELECT statements.  
    SET NOCOUNT ON;  
    SELECT CustomerID, ContactName, CompanyName, City from Customers  
        as c where c.City=@param1  
END  
```  
  
 [!code-csharp[DLinqSprox#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#1)]
 [!code-vb[DLinqSprox#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="98901-110">请参阅</span><span class="sxs-lookup"><span data-stu-id="98901-110">See also</span></span>

- [<span data-ttu-id="98901-111">存储过程</span><span class="sxs-lookup"><span data-stu-id="98901-111">Stored Procedures</span></span>](stored-procedures.md)
- [<span data-ttu-id="98901-112">下载示例数据库</span><span class="sxs-lookup"><span data-stu-id="98901-112">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
