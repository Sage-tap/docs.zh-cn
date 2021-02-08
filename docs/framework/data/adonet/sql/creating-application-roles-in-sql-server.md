---
description: 了解详细信息：在 SQL Server 中创建应用程序角色
title: 在 SQL Server 中创建应用程序角色
ms.date: 03/30/2017
ms.assetid: 27442435-dfb2-4062-8c59-e2960833a638
ms.openlocfilehash: 20047d12a004230aebca1cf9d42b3893d36f3844
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786155"
---
# <a name="creating-application-roles-in-sql-server"></a><span data-ttu-id="43b6c-103">在 SQL Server 中创建应用程序角色</span><span class="sxs-lookup"><span data-stu-id="43b6c-103">Creating Application Roles in SQL Server</span></span>

<span data-ttu-id="43b6c-104">应用程序角色可提供对应用程序（而不是数据库角色或用户）分配权限的方法。</span><span class="sxs-lookup"><span data-stu-id="43b6c-104">Application roles provide a way to assign permissions to an application instead of a database role or user.</span></span> <span data-ttu-id="43b6c-105">用户可以连接到数据库、激活应用程序角色以及采用授予应用程序的权限。</span><span class="sxs-lookup"><span data-stu-id="43b6c-105">Users can connect to the database, activate the application role, and assume the permissions granted to the application.</span></span> <span data-ttu-id="43b6c-106">授予应用程序角色的权限在连接期间有效。</span><span class="sxs-lookup"><span data-stu-id="43b6c-106">The permissions granted to the application role are in force for the duration of the connection.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="43b6c-107">当客户端应用程序在连接字符串中提供应用程序角色名称和密码时，可激活应用程序角色。</span><span class="sxs-lookup"><span data-stu-id="43b6c-107">Application roles are activated when a client application supplies an application role name and a password in the connection string.</span></span> <span data-ttu-id="43b6c-108">因为密码必须存储在客户端计算机上，所以这些角色在二层应用程序上导致一个安全漏洞。</span><span class="sxs-lookup"><span data-stu-id="43b6c-108">They present a security vulnerability in a two-tier application because the password must be stored on the client computer.</span></span> <span data-ttu-id="43b6c-109">在三层应用程序中，您可以存储密码，以便其他应用程序用户将无法对其进行访问。</span><span class="sxs-lookup"><span data-stu-id="43b6c-109">In a three-tier application, you can store the password so that it cannot be accessed by users of the application.</span></span>  
  
## <a name="application-role-features"></a><span data-ttu-id="43b6c-110">应用程序角色功能</span><span class="sxs-lookup"><span data-stu-id="43b6c-110">Application Role Features</span></span>  

 <span data-ttu-id="43b6c-111">应用程序角色具有以下功能：</span><span class="sxs-lookup"><span data-stu-id="43b6c-111">Application roles have the following features:</span></span>  
  
- <span data-ttu-id="43b6c-112">与数据库角色不同，应用程序角色不包含成员。</span><span class="sxs-lookup"><span data-stu-id="43b6c-112">Unlike database roles, application roles contain no members.</span></span>  
  
- <span data-ttu-id="43b6c-113">当客户端应用程序向 `sp_setapprole` 系统存储过程提供应用程序角色名称和密码时，可激活应用程序角色。</span><span class="sxs-lookup"><span data-stu-id="43b6c-113">Application roles are activated when an application supplies the application role name and a password to the `sp_setapprole` system stored procedure.</span></span>  
  
- <span data-ttu-id="43b6c-114">密码必须存储在客户端计算机上，并且在运行时提供；应用程序角色无法从 SQL Server 内激活。</span><span class="sxs-lookup"><span data-stu-id="43b6c-114">The password must be stored on the client computer and supplied at run time; an application role cannot be activated from inside of SQL Server.</span></span>  
  
- <span data-ttu-id="43b6c-115">密码不加密。</span><span class="sxs-lookup"><span data-stu-id="43b6c-115">The password is not encrypted.</span></span> <span data-ttu-id="43b6c-116">参数密码作为单向哈希进行存储。</span><span class="sxs-lookup"><span data-stu-id="43b6c-116">The parameter password is stored as a one-way hash.</span></span>  
  
- <span data-ttu-id="43b6c-117">一旦激活，通过应用程序角色获取的权限在连接期间保持有效。</span><span class="sxs-lookup"><span data-stu-id="43b6c-117">Once activated, permissions acquired through the application role remain in effect for the duration of the connection.</span></span>  
  
- <span data-ttu-id="43b6c-118">应用程序角色继承授予 `public` 角色的权限。</span><span class="sxs-lookup"><span data-stu-id="43b6c-118">The application role inherits permissions granted to the `public` role.</span></span>  
  
- <span data-ttu-id="43b6c-119">如果固定服务器角色 `sysadmin` 的成员激活某一应用程序角色，则安全上下文在连接期间切换为应用程序角色的上下文。</span><span class="sxs-lookup"><span data-stu-id="43b6c-119">If a member of the `sysadmin` fixed server role activates an application role, the security context switches to that of the application role for the duration of the connection.</span></span>  
  
- <span data-ttu-id="43b6c-120">如果您在具有应用程序角色的数据库中创建 `guest` 帐户，则不必为该应用程序角色或调用它的任何登录名创建数据库用户帐户。</span><span class="sxs-lookup"><span data-stu-id="43b6c-120">If you create a `guest` account in a database that has an application role, you do not need to create a database user account for the application role or for any of the logins that invoke it.</span></span> <span data-ttu-id="43b6c-121">只有当在另一个数据库中存在 `guest` 帐户时，应用程序才能直接访问另一数据库。</span><span class="sxs-lookup"><span data-stu-id="43b6c-121">Application roles can directly access another database only if a `guest` account exists in the second database</span></span>  
  
- <span data-ttu-id="43b6c-122">返回登录名的内置函数（如 SYSTEM_USER）返回调用应用程序角色的登录名。</span><span class="sxs-lookup"><span data-stu-id="43b6c-122">Built-in functions that return login names, such as SYSTEM_USER, return the name of the login that invoked the application role.</span></span> <span data-ttu-id="43b6c-123">返回数据库用户名的内置函数将返回应用程序角色的名称。</span><span class="sxs-lookup"><span data-stu-id="43b6c-123">Built-in functions that return database user names return the name of the application role.</span></span>  
  
### <a name="the-principle-of-least-privilege"></a><span data-ttu-id="43b6c-124">最低特权原则</span><span class="sxs-lookup"><span data-stu-id="43b6c-124">The Principle of Least Privilege</span></span>  

 <span data-ttu-id="43b6c-125">仅当密码遭泄漏时，应用程序角色才被授予必要的权限。</span><span class="sxs-lookup"><span data-stu-id="43b6c-125">Application roles should be granted only required permissions in case the password is compromised.</span></span> <span data-ttu-id="43b6c-126">在使用应用程序角色的任何数据库中，应撤消对 `public` 角色的权限。</span><span class="sxs-lookup"><span data-stu-id="43b6c-126">Permissions to the `public` role should be revoked in any database using an application role.</span></span> <span data-ttu-id="43b6c-127">在不希望应用程序角色的调用方具有访问权限的任何数据库中，禁用 `guest` 帐户。</span><span class="sxs-lookup"><span data-stu-id="43b6c-127">Disable the `guest` account in any database you do not want callers of the application role to have access to.</span></span>  
  
### <a name="application-role-enhancements"></a><span data-ttu-id="43b6c-128">应用程序角色增强</span><span class="sxs-lookup"><span data-stu-id="43b6c-128">Application Role Enhancements</span></span>  

 <span data-ttu-id="43b6c-129">在激活应用程序角色后，可将执行上下文切换回原始调用方，无需禁用连接池。</span><span class="sxs-lookup"><span data-stu-id="43b6c-129">The execution context can be switched back to the original caller after activating an application role, removing the need to disable connection pooling.</span></span> <span data-ttu-id="43b6c-130">`sp_setapprole` 过程具有一个创建 Cookie 的新选项，Cookie 包含有关调用方的上下文信息。</span><span class="sxs-lookup"><span data-stu-id="43b6c-130">The `sp_setapprole` procedure has a new option that creates a cookie, which contains context information about the caller.</span></span> <span data-ttu-id="43b6c-131">您可以通过调用 `sp_unsetapprole` 过程来还原会话，并向其传递 Cookie。</span><span class="sxs-lookup"><span data-stu-id="43b6c-131">You can revert the session by calling the `sp_unsetapprole` procedure, passing it the cookie.</span></span>  
  
## <a name="application-role-alternatives"></a><span data-ttu-id="43b6c-132">应用程序角色替代项</span><span class="sxs-lookup"><span data-stu-id="43b6c-132">Application Role Alternatives</span></span>  

 <span data-ttu-id="43b6c-133">应用程序角色依赖于密码的安全性，而密码具有潜在的安全漏洞。</span><span class="sxs-lookup"><span data-stu-id="43b6c-133">Application roles depend on the security of a password, which presents a potential security vulnerability.</span></span> <span data-ttu-id="43b6c-134">密码被嵌入应用程序代码或保存在磁盘上就有可能泄露。</span><span class="sxs-lookup"><span data-stu-id="43b6c-134">Passwords may be exposed by being embedded in application code or saved on disk.</span></span>  
  
 <span data-ttu-id="43b6c-135">可能需要考虑以下替代方法。</span><span class="sxs-lookup"><span data-stu-id="43b6c-135">You may want to consider the following alternatives.</span></span>  
  
- <span data-ttu-id="43b6c-136">使用通过 EXECUTE AS 语句及其 NO REVERT 和 WITH COOKIE 字句切换的上下文。</span><span class="sxs-lookup"><span data-stu-id="43b6c-136">Use context switching with the EXECUTE AS statement with its NO REVERT and WITH COOKIE clauses.</span></span> <span data-ttu-id="43b6c-137">您可以在未映射为登录名的数据库中创建用户帐户。</span><span class="sxs-lookup"><span data-stu-id="43b6c-137">You can create a user account in a database that is not mapped to a login.</span></span> <span data-ttu-id="43b6c-138">然后，向此帐户分配权限。</span><span class="sxs-lookup"><span data-stu-id="43b6c-138">You then assign permissions to this account.</span></span> <span data-ttu-id="43b6c-139">对于很少登录的用户使用 EXECUTE AS 比较安全，因为它基于权限，而不基于密码。</span><span class="sxs-lookup"><span data-stu-id="43b6c-139">Using EXECUTE AS with a login-less user is more secure because it is permission-based, not password-based.</span></span> <span data-ttu-id="43b6c-140">有关详细信息，请参阅 [在 SQL Server 中通过模拟自定义权限](customizing-permissions-with-impersonation-in-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="43b6c-140">For more information, see [Customizing Permissions with Impersonation in SQL Server](customizing-permissions-with-impersonation-in-sql-server.md).</span></span>  
  
- <span data-ttu-id="43b6c-141">使用证书对存储过程进行签名，并仅授予执行这些过程的权限。</span><span class="sxs-lookup"><span data-stu-id="43b6c-141">Sign stored procedures with certificates, granting only permission to execute the procedures.</span></span> <span data-ttu-id="43b6c-142">有关详细信息，请参阅 [SQL Server 中的签名存储过程](signing-stored-procedures-in-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="43b6c-142">For more information, see [Signing Stored Procedures in SQL Server](signing-stored-procedures-in-sql-server.md).</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="43b6c-143">外部资源</span><span class="sxs-lookup"><span data-stu-id="43b6c-143">External Resources</span></span>  

 <span data-ttu-id="43b6c-144">有关详细信息，请参阅以下资源。</span><span class="sxs-lookup"><span data-stu-id="43b6c-144">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="43b6c-145">资源</span><span class="sxs-lookup"><span data-stu-id="43b6c-145">Resource</span></span>|<span data-ttu-id="43b6c-146">说明</span><span class="sxs-lookup"><span data-stu-id="43b6c-146">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="43b6c-147">应用程序角色</span><span class="sxs-lookup"><span data-stu-id="43b6c-147">Application Roles</span></span>](/sql/relational-databases/security/authentication-access/application-roles)|<span data-ttu-id="43b6c-148">描述如何在 SQL Server 2008 中创建和使用应用程序角色。</span><span class="sxs-lookup"><span data-stu-id="43b6c-148">Describes how to create and use application roles in SQL Server 2008.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="43b6c-149">请参阅</span><span class="sxs-lookup"><span data-stu-id="43b6c-149">See also</span></span>

- [<span data-ttu-id="43b6c-150">保证 ADO.NET 应用程序的安全</span><span class="sxs-lookup"><span data-stu-id="43b6c-150">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="43b6c-151">SQL Server 安全性概述</span><span class="sxs-lookup"><span data-stu-id="43b6c-151">Overview of SQL Server Security</span></span>](overview-of-sql-server-security.md)
- [<span data-ttu-id="43b6c-152">SQL Server 中的应用程序安全方案</span><span class="sxs-lookup"><span data-stu-id="43b6c-152">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="43b6c-153">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="43b6c-153">ADO.NET Overview</span></span>](../ado-net-overview.md)
