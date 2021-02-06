---
description: 了解详细信息： LINQ to SQL 中的安全性
title: LINQ to SQL 中的安全性
ms.date: 03/30/2017
ms.assetid: d49787f7-414e-4c71-aa33-80a5895536b1
ms.openlocfilehash: 3d53def25aed83d96e0d32dfc964d9b49458fad7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662931"
---
# <a name="security-in-linq-to-sql"></a><span data-ttu-id="8537f-103">LINQ to SQL 中的安全性</span><span class="sxs-lookup"><span data-stu-id="8537f-103">Security in LINQ to SQL</span></span>

<span data-ttu-id="8537f-104">连接到数据库时始终都存在安全风险。</span><span class="sxs-lookup"><span data-stu-id="8537f-104">Security risks are always present when you connect to a database.</span></span> <span data-ttu-id="8537f-105">尽管 LINQ to SQL 可能包括一些使用 SQL Server 中的数据的新方法，但它并没有提供任何附加安全机制。</span><span class="sxs-lookup"><span data-stu-id="8537f-105">Although LINQ to SQL may include some new ways to work with data in SQL Server, it does not provide any additional security mechanisms.</span></span>  
  
## <a name="access-control-and-authentication"></a><span data-ttu-id="8537f-106">访问控制和身份验证</span><span class="sxs-lookup"><span data-stu-id="8537f-106">Access Control and Authentication</span></span>  

 <span data-ttu-id="8537f-107">LINQ to SQL 没有自己的用户模型或身份验证机制。</span><span class="sxs-lookup"><span data-stu-id="8537f-107">LINQ to SQL does not have its own user model or authentication mechanisms.</span></span> <span data-ttu-id="8537f-108">使用 SQL Server 安全性可控制对映射到对象模型的数据库、数据库表、视图和存储过程的访问。</span><span class="sxs-lookup"><span data-stu-id="8537f-108">Use SQL Server Security to control access to the database, database tables, views, and stored procedures that are mapped to your object model.</span></span> <span data-ttu-id="8537f-109">授予用户所需的最低访问权限并要求对用户身份验证使用强密码。</span><span class="sxs-lookup"><span data-stu-id="8537f-109">Grant the minimally required access to users and require strong passwords for user authentication.</span></span>  
  
## <a name="mapping-and-schema-information"></a><span data-ttu-id="8537f-110">映射和架构信息</span><span class="sxs-lookup"><span data-stu-id="8537f-110">Mapping and Schema Information</span></span>  

 <span data-ttu-id="8537f-111">对象模型或外部映射文件中的 SQL-CLR 类型映射和数据库架构信息可供访问文件系统中的这些文件的所有用户使用。</span><span class="sxs-lookup"><span data-stu-id="8537f-111">SQL-CLR type mapping and database schema information in your object model or external mapping file is available for all with access to those files in the file system.</span></span> <span data-ttu-id="8537f-112">假设架构信息将可供所有可以访问对象模型或外部映射文件的用户使用。</span><span class="sxs-lookup"><span data-stu-id="8537f-112">Assume that schema information will be available to all who can access the object model or external mapping file.</span></span> <span data-ttu-id="8537f-113">若要防止更广泛的架构信息访问，请使用文件安全机制来保护源文件和映射文件。</span><span class="sxs-lookup"><span data-stu-id="8537f-113">To prevent more widespread access to schema information, use file security mechanisms to secure source files and mapping files.</span></span>  
  
## <a name="connection-strings"></a><span data-ttu-id="8537f-114">连接字符串</span><span class="sxs-lookup"><span data-stu-id="8537f-114">Connection Strings</span></span>  

 <span data-ttu-id="8537f-115">应尽可能避免在连接字符串中使用密码。</span><span class="sxs-lookup"><span data-stu-id="8537f-115">Using passwords in connection strings should be avoided whenever possible.</span></span> <span data-ttu-id="8537f-116">连接字符串不仅会在自己的权限方面带来安全风险，而且在使用对象关系设计器或 SQLMetal 命令行工具时，连接字符串还可能会以明文形式添加到对象模型或外部映射文件。</span><span class="sxs-lookup"><span data-stu-id="8537f-116">Not only is a connection string a security risk in its own right, but the connection string may also be added in clear text to the object model or external mapping file when using the Object Relational Designer or SQLMetal command-line tool.</span></span> <span data-ttu-id="8537f-117">可通过文件系统访问对象模型或外部映射文件的任何用户都可以查看连接密码（如果该密码包含在连接字符串中）。</span><span class="sxs-lookup"><span data-stu-id="8537f-117">Anyone with access to the object model or external mapping file via the file system could see the connection password (if it is included in the connection string).</span></span>  
  
 <span data-ttu-id="8537f-118">若要最大程度地减少此类风险，请使用集成安全性与 SQL Server 进行可信连接。</span><span class="sxs-lookup"><span data-stu-id="8537f-118">To minimize such risks, use integrated security to make a trusted connection with SQL Server.</span></span> <span data-ttu-id="8537f-119">通过使用这种方法，您无需将密码存储在连接字符串中。</span><span class="sxs-lookup"><span data-stu-id="8537f-119">By using this approach, you do not have to store a password in the connection string.</span></span> <span data-ttu-id="8537f-120">有关详细信息，请参阅 [SQL Server 安全性](../sql-server-security.md)。</span><span class="sxs-lookup"><span data-stu-id="8537f-120">For more information, see [SQL Server Security](../sql-server-security.md).</span></span>  
  
 <span data-ttu-id="8537f-121">如果缺少集成安全性，则连接字符串中将需要明文密码。</span><span class="sxs-lookup"><span data-stu-id="8537f-121">In the absence of integrated security, a clear-text password will be needed in the connection string.</span></span> <span data-ttu-id="8537f-122">帮助保护连接字符串的最佳方法如下（按风险升序排列）：</span><span class="sxs-lookup"><span data-stu-id="8537f-122">The best way to help secure your connection string, in increasing order of risk, is as follows:</span></span>  
  
- <span data-ttu-id="8537f-123">使用集成安全性。</span><span class="sxs-lookup"><span data-stu-id="8537f-123">Use integrated security.</span></span>  
  
- <span data-ttu-id="8537f-124">通过密码保护连接字符串并尽可能减少连接字符串的传递。</span><span class="sxs-lookup"><span data-stu-id="8537f-124">Secure connection strings with passwords and minimize passing around connection strings.</span></span>  
  
- <span data-ttu-id="8537f-125">使用 <xref:System.Data.SqlClient.SqlConnection?displayProperty=nameWithType> 类来替代连接字符串，因为它可以限制公开的持续时间。</span><span class="sxs-lookup"><span data-stu-id="8537f-125">Use a <xref:System.Data.SqlClient.SqlConnection?displayProperty=nameWithType> class instead of a connection string since it limits the duration of exposure.</span></span> <span data-ttu-id="8537f-126">可使用 <xref:System.Data.Linq.DataContext?displayProperty=nameWithType> 来实例化 LINQ to SQL <xref:System.Data.SqlClient.SqlConnection> 类。</span><span class="sxs-lookup"><span data-stu-id="8537f-126">The LINQ to SQL <xref:System.Data.Linq.DataContext?displayProperty=nameWithType> class can be instantiated using a <xref:System.Data.SqlClient.SqlConnection>.</span></span>  
  
- <span data-ttu-id="8537f-127">最大程度地减少所有连接字符串的生存期和接触点。</span><span class="sxs-lookup"><span data-stu-id="8537f-127">Minimize lifetimes and touch points for all connection strings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8537f-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="8537f-128">See also</span></span>

- [<span data-ttu-id="8537f-129">背景信息</span><span class="sxs-lookup"><span data-stu-id="8537f-129">Background Information</span></span>](background-information.md)
- [<span data-ttu-id="8537f-130">常见问题解答</span><span class="sxs-lookup"><span data-stu-id="8537f-130">Frequently Asked Questions</span></span>](frequently-asked-questions.md)
