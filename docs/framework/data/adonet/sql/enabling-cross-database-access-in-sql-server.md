---
description: 了解详细信息：在 SQL Server 中启用跨数据库访问
title: 在 SQL Server 中启用跨数据库访问
ms.date: 03/30/2017
ms.assetid: 10663fb6-434c-4c81-8178-ec894b9cf895
ms.openlocfilehash: 4e818b4f0294fdc7edd351a1e60203357579a320
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695861"
---
# <a name="enabling-cross-database-access-in-sql-server"></a><span data-ttu-id="0cdb6-103">在 SQL Server 中启用跨数据库访问</span><span class="sxs-lookup"><span data-stu-id="0cdb6-103">Enabling Cross-Database Access in SQL Server</span></span>

<span data-ttu-id="0cdb6-104">当某个数据库中的某一过程依赖另一个数据库中的对象时，会发生跨数据库所有权链接。</span><span class="sxs-lookup"><span data-stu-id="0cdb6-104">Cross-database ownership chaining occurs when a procedure in one database depends on objects in another database.</span></span> <span data-ttu-id="0cdb6-105">跨数据库所有权链与单个数据库中的所有权链接的工作方式相同，不同之处在于完整的所有权链要求将所有对象拥有者映射为同一登录帐户。</span><span class="sxs-lookup"><span data-stu-id="0cdb6-105">A cross-database ownership chain works in the same way as ownership chaining within a single database, except that an unbroken ownership chain requires that all the object owners are mapped to the same login account.</span></span> <span data-ttu-id="0cdb6-106">如果同一登录帐户拥有源数据库中的源对象和目标数据库中的目标对象，则 SQL Server 不会检查对目标对象的权限。</span><span class="sxs-lookup"><span data-stu-id="0cdb6-106">If the source object in the source database and the target objects in the target databases are owned by the same login account, SQL Server does not check permissions on the target objects.</span></span>  
  
## <a name="off-by-default"></a><span data-ttu-id="0cdb6-107">默认情况下为关</span><span class="sxs-lookup"><span data-stu-id="0cdb6-107">Off By Default</span></span>  

 <span data-ttu-id="0cdb6-108">默认情况下，跨数据库的所有权链接已关闭。</span><span class="sxs-lookup"><span data-stu-id="0cdb6-108">Ownership chaining across databases is turned off by default.</span></span> <span data-ttu-id="0cdb6-109">Microsoft 建议禁用跨数据库所有权链接，因为它会使您面临以下安全风险：</span><span class="sxs-lookup"><span data-stu-id="0cdb6-109">Microsoft recommends that you disable cross-database ownership chaining because it exposes you to the following security risks:</span></span>  
  
- <span data-ttu-id="0cdb6-110">数据库所有者和 `db_ddladmin` 成员或 `db_owners` 数据库角色可创建其他用户所拥有的对象。</span><span class="sxs-lookup"><span data-stu-id="0cdb6-110">Database owners and members of the `db_ddladmin` or the `db_owners` database roles can create objects that are owned by other users.</span></span> <span data-ttu-id="0cdb6-111">这些对象的目标可能是其他数据库中的对象。</span><span class="sxs-lookup"><span data-stu-id="0cdb6-111">These objects can potentially target objects in other databases.</span></span> <span data-ttu-id="0cdb6-112">这表示如果启用跨数据库所有权链接，您必须完全信任在所有数据库中具有数据的这些用户。</span><span class="sxs-lookup"><span data-stu-id="0cdb6-112">This means that if you enable cross-database ownership chaining, you must fully trust these users with data in all databases.</span></span>  
  
- <span data-ttu-id="0cdb6-113">具有 CREATE DATABASE 权限的用户可创建新数据库以及附加现有数据库。</span><span class="sxs-lookup"><span data-stu-id="0cdb6-113">Users with CREATE DATABASE permission can create new databases and attach existing databases.</span></span> <span data-ttu-id="0cdb6-114">如果启用了跨数据库所有权链接，则这些用户可以从新创建的或他们创建的附加数据库中访问他们在其中没有权限的其他数据库中的对象。</span><span class="sxs-lookup"><span data-stu-id="0cdb6-114">If cross-database ownership chaining is enabled, these users can access objects in other databases that they might not have privileges in from the newly created or attached databases that they create.</span></span>  
  
## <a name="enabling-cross-database-ownership-chaining"></a><span data-ttu-id="0cdb6-115">启用跨数据库所有权链接</span><span class="sxs-lookup"><span data-stu-id="0cdb6-115">Enabling Cross-database Ownership Chaining</span></span>  

 <span data-ttu-id="0cdb6-116">只能在完全信任高级权限用户的环境中启用跨数据库所有权链接。</span><span class="sxs-lookup"><span data-stu-id="0cdb6-116">Cross-database ownership chaining should only be enabled in environments where you can fully trust highly-privileged users.</span></span> <span data-ttu-id="0cdb6-117">可在设置所有数据库，或使用 Transact-SQL 命令 `sp_configure` 和 `ALTER DATABASE` 选择性地设置特定数据库期间，配置跨数据库所有权链接。</span><span class="sxs-lookup"><span data-stu-id="0cdb6-117">It can be configured during setup for all databases, or selectively for specific databases using the Transact-SQL commands `sp_configure` and `ALTER DATABASE`.</span></span>  
  
 <span data-ttu-id="0cdb6-118">若要有选择地配置跨数据库所有权链接，请使用 `sp_configure` 将服务器的所有权链接关闭。</span><span class="sxs-lookup"><span data-stu-id="0cdb6-118">To selectively configure cross-database ownership chaining, use `sp_configure` to turn it off for the server.</span></span> <span data-ttu-id="0cdb6-119">然后，使用包含 SET DB_CHAINING ON 的 ALTER DATABASE 命令仅为需要跨数据库所有权链接的数据库配置跨数据库所有权链接。</span><span class="sxs-lookup"><span data-stu-id="0cdb6-119">Then use the ALTER DATABASE command with SET DB_CHAINING ON to configure cross-database ownership chaining for only the databases that require it.</span></span>  
  
 <span data-ttu-id="0cdb6-120">下面的示例针对所有数据库启用跨数据库所有权链接：</span><span class="sxs-lookup"><span data-stu-id="0cdb6-120">The following sample turns on cross-database ownership chaining for all databases:</span></span>  
  
```sql
EXECUTE sp_configure 'show advanced', 1;  
RECONFIGURE;  
EXECUTE sp_configure 'cross db ownership chaining', 1;  
RECONFIGURE;  
```  
  
 <span data-ttu-id="0cdb6-121">下面的示例针对特定数据库启用跨数据库所有权链接：</span><span class="sxs-lookup"><span data-stu-id="0cdb6-121">The following sample turns on cross-database ownership chaining for specific databases:</span></span>  
  
```sql
ALTER DATABASE Database1 SET DB_CHAINING ON;  
ALTER DATABASE Database2 SET DB_CHAINING ON;  
```  
  
### <a name="dynamic-sql"></a><span data-ttu-id="0cdb6-122">动态 SQL</span><span class="sxs-lookup"><span data-stu-id="0cdb6-122">Dynamic SQL</span></span>  

 <span data-ttu-id="0cdb6-123">在执行了动态创建的 SQL 语句的情况下跨数据库所有权链接将不起作用，除非同一用户同时存在于两个数据库中。</span><span class="sxs-lookup"><span data-stu-id="0cdb6-123">Cross-database ownership chaining does not work in cases where dynamically created SQL statements are executed unless the same user exists in both databases.</span></span> <span data-ttu-id="0cdb6-124">在 SQL Server 中，可以通过创建一个可访问另一个数据库中数据的存储过程并用两个数据库中都存在的证书为此过程签名来解决这个问题。</span><span class="sxs-lookup"><span data-stu-id="0cdb6-124">You can work around this in SQL Server by creating a stored procedure that accesses data in another database and signing the procedure with a certificate that exists in both databases.</span></span> <span data-ttu-id="0cdb6-125">这样，用户就可以访问该过程使用的数据库资源，而无需授予他们数据库访问或权限。</span><span class="sxs-lookup"><span data-stu-id="0cdb6-125">This gives users access to the database resources used by the procedure without granting them database access or permissions.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="0cdb6-126">外部资源</span><span class="sxs-lookup"><span data-stu-id="0cdb6-126">External Resources</span></span>  

 <span data-ttu-id="0cdb6-127">有关详细信息，请参阅以下资源。</span><span class="sxs-lookup"><span data-stu-id="0cdb6-127">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="0cdb6-128">资源</span><span class="sxs-lookup"><span data-stu-id="0cdb6-128">Resource</span></span>|<span data-ttu-id="0cdb6-129">说明</span><span class="sxs-lookup"><span data-stu-id="0cdb6-129">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="0cdb6-130">[使用 EXECUTE AS](/previous-versions/sql/sql-server-2008-r2/ms188304(v=sql.105)) 和 [跨数据库所有权链接选项](/sql/database-engine/configure-windows/cross-db-ownership-chaining-server-configuration-option)扩展数据库模拟。</span><span class="sxs-lookup"><span data-stu-id="0cdb6-130">[Extending Database Impersonation by Using EXECUTE AS](/previous-versions/sql/sql-server-2008-r2/ms188304(v=sql.105)) and [Cross DB Ownership Chaining Option](/sql/database-engine/configure-windows/cross-db-ownership-chaining-server-configuration-option).</span></span>|<span data-ttu-id="0cdb6-131">本文介绍如何为 SQL Server 实例配置跨数据库所有权链接。</span><span class="sxs-lookup"><span data-stu-id="0cdb6-131">Articles describe how to configure cross-database ownership chaining for an instance of SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0cdb6-132">请参阅</span><span class="sxs-lookup"><span data-stu-id="0cdb6-132">See also</span></span>

- [<span data-ttu-id="0cdb6-133">保证 ADO.NET 应用程序的安全</span><span class="sxs-lookup"><span data-stu-id="0cdb6-133">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="0cdb6-134">SQL Server 安全性概述</span><span class="sxs-lookup"><span data-stu-id="0cdb6-134">Overview of SQL Server Security</span></span>](overview-of-sql-server-security.md)
- [<span data-ttu-id="0cdb6-135">在 SQL Server 中使用存储过程管理权限</span><span class="sxs-lookup"><span data-stu-id="0cdb6-135">Managing Permissions with Stored Procedures in SQL Server</span></span>](managing-permissions-with-stored-procedures-in-sql-server.md)
- [<span data-ttu-id="0cdb6-136">在 SQL Server 中编写安全动态 SQL</span><span class="sxs-lookup"><span data-stu-id="0cdb6-136">Writing Secure Dynamic SQL in SQL Server</span></span>](writing-secure-dynamic-sql-in-sql-server.md)
- [<span data-ttu-id="0cdb6-137">SQL Server 中的签名存储过程</span><span class="sxs-lookup"><span data-stu-id="0cdb6-137">Signing Stored Procedures in SQL Server</span></span>](signing-stored-procedures-in-sql-server.md)
- [<span data-ttu-id="0cdb6-138">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="0cdb6-138">ADO.NET Overview</span></span>](../ado-net-overview.md)
