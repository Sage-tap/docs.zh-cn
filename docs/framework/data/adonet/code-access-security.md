---
description: 了解更多相关信息：代码访问安全性和 ADO.NET
title: 代码访问安全性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 93e099eb-daa1-4f1e-b031-c1e10a996f88
ms.openlocfilehash: e7a6054cd7c222c700f5a83e46f5b44bfee23248
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99663997"
---
# <a name="code-access-security-and-adonet"></a><span data-ttu-id="49040-103">代码访问安全性和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="49040-103">Code Access Security and ADO.NET</span></span>

<span data-ttu-id="49040-104">.NET Framework 提供基于角色的安全性和代码访问安全性 (CAS)，这两种安全性都可以通过公共语言运行库 (CLR) 提供的公共基础结构实现。</span><span class="sxs-lookup"><span data-stu-id="49040-104">The .NET Framework offers role-based security as well as code access security (CAS), both of which are implemented using a common infrastructure supplied by the common language runtime (CLR).</span></span> <span data-ttu-id="49040-105">对于非托管代码，大多数应用程序都可以使用用户或主体权限执行。</span><span class="sxs-lookup"><span data-stu-id="49040-105">In the world of unmanaged code, most applications execute with the permissions of the user or principal.</span></span> <span data-ttu-id="49040-106">因此，当拥有提升权限的用户运行恶意软件或包含错误的软件时，计算机系统可能会受到损坏并危及私有数据。</span><span class="sxs-lookup"><span data-stu-id="49040-106">As a result, computer systems can be damaged and private data compromised when malicious or error-filled software is run by a user with elevated privileges.</span></span>  
  
 <span data-ttu-id="49040-107">相对而言，.NET Framework 中执行的托管代码包括单独应用于代码的代码访问安全性。</span><span class="sxs-lookup"><span data-stu-id="49040-107">By contrast, managed code executing in the .NET Framework includes code access security, which applies to code alone.</span></span> <span data-ttu-id="49040-108">是否允许运行代码取决于代码的来源或代码标识的其他方面，而不仅仅是主体标识。</span><span class="sxs-lookup"><span data-stu-id="49040-108">Whether the code is allowed to run or not depends on the code's origin or other aspects of the code's identity, not solely the identity of the principal.</span></span> <span data-ttu-id="49040-109">这样可以减小滥用托管代码的可能性。</span><span class="sxs-lookup"><span data-stu-id="49040-109">This reduces the likelihood that managed code can be misused.</span></span>  
  
## <a name="code-access-permissions"></a><span data-ttu-id="49040-110">代码访问权限</span><span class="sxs-lookup"><span data-stu-id="49040-110">Code Access Permissions</span></span>  

 <span data-ttu-id="49040-111">在执行代码时，代码会提供通过 CLR 安全系统计算的证据。</span><span class="sxs-lookup"><span data-stu-id="49040-111">When code is executed, it presents evidence that is evaluated by the CLR security system.</span></span> <span data-ttu-id="49040-112">通常，此证据由代码的来源（包括 URL、站点和区域）以及确保程序集标识的数字签名组成。</span><span class="sxs-lookup"><span data-stu-id="49040-112">Typically, this evidence comprises the origin of the code including URL, site, and zone, and digital signatures that ensure the identity of the assembly.</span></span>  
  
 <span data-ttu-id="49040-113">CLR 仅允许代码执行代码具有执行权限的那些操作。</span><span class="sxs-lookup"><span data-stu-id="49040-113">The CLR allows code to perform only those operations that the code has permission to perform.</span></span> <span data-ttu-id="49040-114">代码可以请求权限，而这些请求需要基于管理员设置的安全策略。</span><span class="sxs-lookup"><span data-stu-id="49040-114">Code can request permissions, and those requests are honored based on the security policy set by an administrator.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="49040-115">在 CLR 中指定的代码不能为自身授予权限。</span><span class="sxs-lookup"><span data-stu-id="49040-115">Code executing in the CLR cannot grant permissions to itself.</span></span> <span data-ttu-id="49040-116">例如，代码可以请求并获得比安全策略允许的权限少的权限，但决不会获得比安全策略允许的权限多的权限。</span><span class="sxs-lookup"><span data-stu-id="49040-116">For example, code can request and be granted fewer permissions than a security policy allows, but it will never be granted more permissions.</span></span> <span data-ttu-id="49040-117">在授予权限时，应该从无权限开始，然后为要执行的特定任务添加最少的权限。</span><span class="sxs-lookup"><span data-stu-id="49040-117">When granting permissions, start with no permissions at all and then add the narrowest permissions for the particular task being performed.</span></span> <span data-ttu-id="49040-118">一开始就使用所有权限，然后拒绝各个权限会导致应用程序不安全，应用程序可能会授予不必要的权限，从而使应用程序无意中包含安全漏洞。</span><span class="sxs-lookup"><span data-stu-id="49040-118">Starting with all permissions and then denying individual ones leads to insecure applications that may contain unintentional security holes from granting more permissions than required.</span></span> <span data-ttu-id="49040-119">有关详细信息，请参阅 [配置安全策略](/previous-versions/dotnet/netframework-4.0/7c9c2y1w(v=vs.100)) 和 [安全策略管理](/previous-versions/dotnet/netframework-4.0/c1k0eed6(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="49040-119">For more information, see [Configuring Security Policy](/previous-versions/dotnet/netframework-4.0/7c9c2y1w(v=vs.100)) and [Security Policy Management](/previous-versions/dotnet/netframework-4.0/c1k0eed6(v=vs.100)).</span></span>  
  
 <span data-ttu-id="49040-120">代码访问权限有三种类型：</span><span class="sxs-lookup"><span data-stu-id="49040-120">There are three types of code access permissions:</span></span>  
  
- <span data-ttu-id="49040-121">`Code access permissions`从 <xref:System.Security.CodeAccessPermission> 类派生。</span><span class="sxs-lookup"><span data-stu-id="49040-121">`Code access permissions` derive from the <xref:System.Security.CodeAccessPermission> class.</span></span> <span data-ttu-id="49040-122">需要具有权限才能访问受保护的资源（如文件和环境变量）和执行受保护的操作（如访问托管代码）。</span><span class="sxs-lookup"><span data-stu-id="49040-122">Permissions are required in order to access protected resources, such as files and environment variables, and to perform protected operations, such as accessing unmanaged code.</span></span>  
  
- <span data-ttu-id="49040-123">`Identity permissions`表示标识程序集的特征。</span><span class="sxs-lookup"><span data-stu-id="49040-123">`Identity permissions` represent characteristics that identify an assembly.</span></span> <span data-ttu-id="49040-124">对程序集授予权限需要基于证据，而证据可以包括如数字签名或代码来源等项。</span><span class="sxs-lookup"><span data-stu-id="49040-124">Permissions are granted to an assembly based on evidence, which can include items such as a digital signature or where the code originated.</span></span> <span data-ttu-id="49040-125">标识权限也从 <xref:System.Security.CodeAccessPermission> 基类派生。</span><span class="sxs-lookup"><span data-stu-id="49040-125">Identity permissions also derive from the <xref:System.Security.CodeAccessPermission> base class.</span></span>  
  
- <span data-ttu-id="49040-126">`Role-based security permissions`基于主体是否具有指定标识或是否是指定角色的成员。</span><span class="sxs-lookup"><span data-stu-id="49040-126">`Role-based security permissions` are based on whether a principal has a specified identity or is a member of a specified role.</span></span> <span data-ttu-id="49040-127"><xref:System.Security.Permissions.PrincipalPermission> 类允许对活动主体进行声明性和强制性权限检查。</span><span class="sxs-lookup"><span data-stu-id="49040-127">The <xref:System.Security.Permissions.PrincipalPermission> class allows both declarative and imperative permission checks against the active principal.</span></span>  
  
 <span data-ttu-id="49040-128">为了确定代码是否获得了访问某一资源或执行某一操作的授权，运行库的安全系统将遍历调用堆栈，将每个调用方已获得的权限与要求的权限进行比较。</span><span class="sxs-lookup"><span data-stu-id="49040-128">To determine whether code is authorized to access a resource or perform an operation, the runtime's security system traverses the call stack, comparing the granted permissions of each caller to the permission being demanded.</span></span> <span data-ttu-id="49040-129">如果调用堆栈中的任何调用方没有要求的权限，则会引发 <xref:System.Security.SecurityException> 并拒绝访问。</span><span class="sxs-lookup"><span data-stu-id="49040-129">If any caller in the call stack does not have the demanded permission, a <xref:System.Security.SecurityException> is thrown and access is refused.</span></span>  
  
### <a name="requesting-permissions"></a><span data-ttu-id="49040-130">请求权限</span><span class="sxs-lookup"><span data-stu-id="49040-130">Requesting Permissions</span></span>  

 <span data-ttu-id="49040-131">请求权限的目的是通知运行库您的应用程序要求哪些权限才能运行，并确保应用程序只接收到实际需要的权限。</span><span class="sxs-lookup"><span data-stu-id="49040-131">The purpose of requesting permissions is to inform the runtime which permissions your application requires in order to run, and to ensure that it receives only the permissions that it actually needs.</span></span> <span data-ttu-id="49040-132">例如，如果您的应用程序需要将数据写入本地磁盘，则需要 <xref:System.Security.Permissions.FileIOPermission>。</span><span class="sxs-lookup"><span data-stu-id="49040-132">For example, if your application needs to write data to the local disk, it requires <xref:System.Security.Permissions.FileIOPermission>.</span></span> <span data-ttu-id="49040-133">如果尚未授予该权限，则在应用程序尝试写入磁盘时将失败。</span><span class="sxs-lookup"><span data-stu-id="49040-133">If that permission hasn't been granted, the application will fail when it attempts to write to the disk.</span></span> <span data-ttu-id="49040-134">不过，如果应用程序请求 `FileIOPermission` 并且尚未授予该权限，则应用程序一开始即会生成异常，因此将不会加载。</span><span class="sxs-lookup"><span data-stu-id="49040-134">However, if the application requests `FileIOPermission` and that permission has not been granted, the application will generate the exception at the outset and will not load.</span></span>  
  
 <span data-ttu-id="49040-135">在应用程序只需从磁盘读取数据的情况下，您可以请求永远不为应用程序授予任何写入权限。</span><span class="sxs-lookup"><span data-stu-id="49040-135">In a scenario where the application only needs to read data from the disk, you can request that it never be granted any write permissions.</span></span> <span data-ttu-id="49040-136">在出现 Bug 或受到恶意攻击时，你的代码将不会损坏它所操作的数据。</span><span class="sxs-lookup"><span data-stu-id="49040-136">In the event of a bug or a malicious attack, your code cannot damage the data on which it operates.</span></span> <span data-ttu-id="49040-137">有关详细信息，请参阅 [请求权限](/previous-versions/dotnet/netframework-4.0/yd267cce(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="49040-137">For more information, see [Requesting Permissions](/previous-versions/dotnet/netframework-4.0/yd267cce(v=vs.100)).</span></span>  
  
## <a name="role-based-security-and-cas"></a><span data-ttu-id="49040-138">基于角色的安全性和 CAS</span><span class="sxs-lookup"><span data-stu-id="49040-138">Role-Based Security and CAS</span></span>  

 <span data-ttu-id="49040-139">同时实现基于角色的安全性和代码访问安全性 (CAS) 可增强应用程序的整体安全性。</span><span class="sxs-lookup"><span data-stu-id="49040-139">Implementing both role-based security and code-accessed security (CAS) enhances overall security for your application.</span></span> <span data-ttu-id="49040-140">基于角色的安全性可以基于 Windows 帐户或自定义标识，使有关安全主体的信息可用于当前线程。</span><span class="sxs-lookup"><span data-stu-id="49040-140">Role-based security can be based on a Windows account or a custom identity, making information about the security principal available to the current thread.</span></span> <span data-ttu-id="49040-141">此外，通常还要求应用程序基于用户提供的凭据提供对数据或资源的访问。</span><span class="sxs-lookup"><span data-stu-id="49040-141">In addition, applications are often required to provide access to data or resources based on credentials supplied by the user.</span></span> <span data-ttu-id="49040-142">通常情况下，这种应用程序会检查用户的角色，并根据这些角色提供对资源的访问。</span><span class="sxs-lookup"><span data-stu-id="49040-142">Typically, such applications check the role of a user and provide access to resources based on those roles.</span></span>  
  
 <span data-ttu-id="49040-143">基于角色的安全性使组件能够在运行时标识当前用户及其关联的角色。</span><span class="sxs-lookup"><span data-stu-id="49040-143">Role-based security enables a component to identify current users and their associated roles at run time.</span></span> <span data-ttu-id="49040-144">然后使用 CAS 策略映射此信息以确定运行时授予的一组权限。</span><span class="sxs-lookup"><span data-stu-id="49040-144">This information is then mapped using a CAS policy to determine the set of permissions granted at run time.</span></span> <span data-ttu-id="49040-145">对于指定的应用程序域，主机可以更改基于角色的默认安全策略并设置表示用户的默认安全主体和与该用户关联的角色。</span><span class="sxs-lookup"><span data-stu-id="49040-145">For a specified application domain, the host can change the default role-based security policy and set a default security principal that represents a user and the roles associated with that user.</span></span>  
  
 <span data-ttu-id="49040-146">CLR 使用权限来实现其用于对托管代码实施限制的机制。</span><span class="sxs-lookup"><span data-stu-id="49040-146">The CLR uses permissions to implement its mechanism for enforcing restrictions on managed code.</span></span> <span data-ttu-id="49040-147">基于角色的安全权限提供一种机制，用于发现用户（或代表该用户的代理）是否具有特定标识或者是否是指定角色的成员。</span><span class="sxs-lookup"><span data-stu-id="49040-147">Role-based security permissions provide a mechanism for discovering whether a user (or the agent acting on the user's behalf) has a particular identity or is a member of a specified role.</span></span> <span data-ttu-id="49040-148">有关详细信息，请参阅 [安全权限](/previous-versions/dotnet/netframework-4.0/5ba4k1c5(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="49040-148">For more information, see [Security Permissions](/previous-versions/dotnet/netframework-4.0/5ba4k1c5(v=vs.100)).</span></span>  
  
 <span data-ttu-id="49040-149">根据要生成的应用程序类型，还应考虑在数据库中实现基于角色的权限。</span><span class="sxs-lookup"><span data-stu-id="49040-149">Depending on the type of application you are building, you should also consider implementing role-based permissions in the database.</span></span> <span data-ttu-id="49040-150">有关 SQL Server 中基于角色的安全性的详细信息，请参阅 [SQL Server 安全性](./sql/sql-server-security.md)。</span><span class="sxs-lookup"><span data-stu-id="49040-150">For more information on role-based security in SQL Server, see [SQL Server Security](./sql/sql-server-security.md).</span></span>  
  
## <a name="assemblies"></a><span data-ttu-id="49040-151">程序集</span><span class="sxs-lookup"><span data-stu-id="49040-151">Assemblies</span></span>  

 <span data-ttu-id="49040-152">程序集构成 .NET Framework 应用程序部署、版本控制、重复使用、激活范围和安全权限的基本单元。</span><span class="sxs-lookup"><span data-stu-id="49040-152">Assemblies form the fundamental unit of deployment, version control, reuse, activation scoping, and security permissions for a .NET Framework application.</span></span> <span data-ttu-id="49040-153">程序集提供类型和资源的集合，二者结合在一起构成功能的逻辑单元。</span><span class="sxs-lookup"><span data-stu-id="49040-153">An assembly provides a collection of types and resources that are built to work together and form a logical unit of functionality.</span></span> <span data-ttu-id="49040-154">对于 CLR，类型不存在于程序集的上下文之外。</span><span class="sxs-lookup"><span data-stu-id="49040-154">To the CLR, a type does not exist outside the context of an assembly.</span></span> <span data-ttu-id="49040-155">有关创建和部署程序集的详细信息，请参阅 [用程序集编程](../../../standard/assembly/index.md)。</span><span class="sxs-lookup"><span data-stu-id="49040-155">For more information on creating and deploying assemblies, see [Programming with Assemblies](../../../standard/assembly/index.md).</span></span>  
  
### <a name="strong-naming-assemblies"></a><span data-ttu-id="49040-156">强命名程序集</span><span class="sxs-lookup"><span data-stu-id="49040-156">Strong-naming Assemblies</span></span>  

 <span data-ttu-id="49040-157">强名称（或数字签名）由程序集的标识组成，该标识包括程序集的简单文本名称、版本号和区域性信息（如果提供）、公钥和数字签名。</span><span class="sxs-lookup"><span data-stu-id="49040-157">A strong name, or digital signature, consists of the assembly's identity, which includes its simple text name, version number, and culture information (if provided), plus a public key and a digital signature.</span></span> <span data-ttu-id="49040-158">数字签名使用相应私钥从程序集文件生成。</span><span class="sxs-lookup"><span data-stu-id="49040-158">The digital signature is generated from an assembly file using the corresponding private key.</span></span> <span data-ttu-id="49040-159">程序集文件包含程序集清单，该清单包含组成程序集的所有文件的名称和哈希。</span><span class="sxs-lookup"><span data-stu-id="49040-159">The assembly file contains the assembly manifest, which contains the names and hashes of all the files that make up the assembly.</span></span>  
  
 <span data-ttu-id="49040-160">强命名程序集可为应用程序或组件提供唯一的标识，其他软件可以使用该标识显式引用应用程序或组件。</span><span class="sxs-lookup"><span data-stu-id="49040-160">Strong naming an assembly gives an application or component a unique identity that other software can use to refer explicitly to it.</span></span> <span data-ttu-id="49040-161">强命名可以保护程序集，防止包含恶意代码的程序集冒充。</span><span class="sxs-lookup"><span data-stu-id="49040-161">Strong naming guards assemblies against being spoofed by an assembly that contains hostile code.</span></span> <span data-ttu-id="49040-162">强命名还可以保证组件的不同版本之间的版本一致性。</span><span class="sxs-lookup"><span data-stu-id="49040-162">Strong-naming also ensures versioning consistency among different versions of a component.</span></span> <span data-ttu-id="49040-163">对于将要部署到全局程序集缓存 (GAC) 的程序集，必须进行强命名。</span><span class="sxs-lookup"><span data-stu-id="49040-163">You must strong name assemblies that will be deployed to the Global Assembly Cache (GAC).</span></span> <span data-ttu-id="49040-164">有关详细信息，请参阅[创建和使用具有强名称的程序集](../../../standard/assembly/create-use-strong-named.md)。</span><span class="sxs-lookup"><span data-stu-id="49040-164">For more information, see [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md).</span></span>  
  
## <a name="partial-trust-in-adonet-20"></a><span data-ttu-id="49040-165">ADO.NET 2.0 中的部分信任</span><span class="sxs-lookup"><span data-stu-id="49040-165">Partial Trust in ADO.NET 2.0</span></span>  

 <span data-ttu-id="49040-166">在 ADO.NET 2.0 中，适用于 SQL Server 的 .NET Framework 数据提供程序、适用于 OLE DB 的 .NET Framework 数据提供程序、适用于 ODBC 的 .NET Framework 数据提供程序和适用于 Oracle 的 .NET Framework 数据提供程序现在全部可以在部分信任的环境中运行。</span><span class="sxs-lookup"><span data-stu-id="49040-166">In ADO.NET 2.0, the .NET Framework Data Provider for SQL Server, the .NET Framework Data Provider for OLE DB, the .NET Framework Data Provider for ODBC, and the .NET Framework Data Provider for Oracle can now all run in partially trusted environments.</span></span> <span data-ttu-id="49040-167">在以前版本的 .NET Framework 中，非完全信任的应用程序仅支持 <xref:System.Data.SqlClient>。</span><span class="sxs-lookup"><span data-stu-id="49040-167">In previous releases of the .NET Framework, only <xref:System.Data.SqlClient> was supported in less than full-trust applications.</span></span>  
  
 <span data-ttu-id="49040-168">使用 SQL Server 提供程序的部分信任应用程序必须至少具有执行和 <xref:System.Data.SqlClient.SqlClientPermission> 权限。</span><span class="sxs-lookup"><span data-stu-id="49040-168">At minimum, a partially trusted application using the SQL Server provider must have execution and <xref:System.Data.SqlClient.SqlClientPermission> permissions.</span></span>  
  
### <a name="permission-attribute-properties-for-partial-trust"></a><span data-ttu-id="49040-169">部分信任的权限属性</span><span class="sxs-lookup"><span data-stu-id="49040-169">Permission Attribute Properties for Partial Trust</span></span>  

 <span data-ttu-id="49040-170">对于部分信任的方案，可以使用 <xref:System.Data.SqlClient.SqlClientPermissionAttribute> 成员进一步限制 SQL Server .NET Framework 数据提供程序可以使用的功能。</span><span class="sxs-lookup"><span data-stu-id="49040-170">For partial trust scenarios, you can use <xref:System.Data.SqlClient.SqlClientPermissionAttribute> members to further restrict the capabilities available for the .NET Framework Data Provider for SQL Server.</span></span>  
  
 <span data-ttu-id="49040-171">下表列出了可用的 <xref:System.Data.SqlClient.SqlClientPermissionAttribute> 属性及其说明：</span><span class="sxs-lookup"><span data-stu-id="49040-171">The following table lists the available <xref:System.Data.SqlClient.SqlClientPermissionAttribute> properties and their descriptions:</span></span>  
  
|<span data-ttu-id="49040-172">权限属性</span><span class="sxs-lookup"><span data-stu-id="49040-172">Permission attribute property</span></span>|<span data-ttu-id="49040-173">说明</span><span class="sxs-lookup"><span data-stu-id="49040-173">Description</span></span>|  
|-----------------------------------|-----------------|  
|`Action`|<span data-ttu-id="49040-174">获取或设置安全性操作。</span><span class="sxs-lookup"><span data-stu-id="49040-174">Gets or sets a security action.</span></span> <span data-ttu-id="49040-175">从 <xref:System.Security.Permissions.SecurityAttribute> 继承。</span><span class="sxs-lookup"><span data-stu-id="49040-175">Inherited from <xref:System.Security.Permissions.SecurityAttribute>.</span></span>|  
|`AllowBlankPassword`|<span data-ttu-id="49040-176">启用或禁用连接字符串中空白密码。</span><span class="sxs-lookup"><span data-stu-id="49040-176">Enables or disables the use of a blank password in a connection string.</span></span> <span data-ttu-id="49040-177">有效值为 `true`（启用空白密码的使用）和 `false`（禁用空白密码的使用）。</span><span class="sxs-lookup"><span data-stu-id="49040-177">Valid values are `true` (to enable the use of blank passwords) and `false` (to disable the use of blank passwords).</span></span> <span data-ttu-id="49040-178">从 <xref:System.Data.Common.DBDataPermissionAttribute> 继承。</span><span class="sxs-lookup"><span data-stu-id="49040-178">Inherited from <xref:System.Data.Common.DBDataPermissionAttribute>.</span></span>|  
|`ConnectionString`|<span data-ttu-id="49040-179">标识允许的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="49040-179">Identifies a permitted connection string.</span></span> <span data-ttu-id="49040-180">可标识多个连接字符串。</span><span class="sxs-lookup"><span data-stu-id="49040-180">Multiple connection strings can be identified.</span></span> <span data-ttu-id="49040-181">**注意：**  不要在连接字符串中包括用户 ID 或密码。</span><span class="sxs-lookup"><span data-stu-id="49040-181">**Note:**  Do not include a user ID or password in your connection string.</span></span> <span data-ttu-id="49040-182">此版本中，不能使用 .NET Framework 配置工具更改连接字符串限制。</span><span class="sxs-lookup"><span data-stu-id="49040-182">In this release, you cannot change connection string restrictions using the .NET Framework Configuration Tool.</span></span> <br /><br /> <span data-ttu-id="49040-183">从 <xref:System.Data.Common.DBDataPermissionAttribute> 继承。</span><span class="sxs-lookup"><span data-stu-id="49040-183">Inherited from <xref:System.Data.Common.DBDataPermissionAttribute>.</span></span>|  
|`KeyRestrictions`|<span data-ttu-id="49040-184">标识允许或不允许的连接字符串参数。</span><span class="sxs-lookup"><span data-stu-id="49040-184">Identifies connection string parameters that are allowed or disallowed.</span></span> <span data-ttu-id="49040-185">连接字符串参数以形式标识 *\<parameter name>=* 。</span><span class="sxs-lookup"><span data-stu-id="49040-185">Connection string parameters are identified in the form *\<parameter name>=*.</span></span> <span data-ttu-id="49040-186">可指定多个参数，并用分号 (;) 进行分隔。</span><span class="sxs-lookup"><span data-stu-id="49040-186">Multiple parameters can be specified, delimited using a semicolon (;).</span></span> <span data-ttu-id="49040-187">**注意：**  如果未指定 `KeyRestrictions` ，但将 `KeyRestrictionBehavior` 属性设置为 `AllowOnly` 或，则 `PreventUsage` 不允许使用其他连接字符串参数。</span><span class="sxs-lookup"><span data-stu-id="49040-187">**Note:**  If you do not specify `KeyRestrictions`, but you set `KeyRestrictionBehavior` property to `AllowOnly` or `PreventUsage`, no additional connection string parameters are allowed.</span></span> <span data-ttu-id="49040-188">从 <xref:System.Data.Common.DBDataPermissionAttribute> 继承。</span><span class="sxs-lookup"><span data-stu-id="49040-188">Inherited from <xref:System.Data.Common.DBDataPermissionAttribute>.</span></span>|  
|`KeyRestrictionBehavior`|<span data-ttu-id="49040-189">将连接字符串参数标识为唯一允许的附加参数 (`AllowOnly`)，或标识不允许的附加参数 (`PreventUsage`)。</span><span class="sxs-lookup"><span data-stu-id="49040-189">Identifies the connection string parameters as the only additional parameters allowed (`AllowOnly`), or identifies the additional parameters that are not allowed (`PreventUsage`).</span></span> <span data-ttu-id="49040-190">`AllowOnly` 为默认值。</span><span class="sxs-lookup"><span data-stu-id="49040-190">`AllowOnly` is the default.</span></span> <span data-ttu-id="49040-191">从 <xref:System.Data.Common.DBDataPermissionAttribute> 继承。</span><span class="sxs-lookup"><span data-stu-id="49040-191">Inherited from <xref:System.Data.Common.DBDataPermissionAttribute>.</span></span>|  
|`TypeID`|<span data-ttu-id="49040-192">在派生类中实现此属性时获取唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="49040-192">Gets a unique identifier for this attribute when implemented in a derived class.</span></span> <span data-ttu-id="49040-193">从 <xref:System.Attribute> 继承。</span><span class="sxs-lookup"><span data-stu-id="49040-193">Inherited from <xref:System.Attribute>.</span></span>|  
|`Unrestricted`|<span data-ttu-id="49040-194">表明是否声明对该资源的无限制权限。</span><span class="sxs-lookup"><span data-stu-id="49040-194">Indicates whether unrestricted permission to the resource is declared.</span></span> <span data-ttu-id="49040-195">从 <xref:System.Security.Permissions.SecurityAttribute> 继承。</span><span class="sxs-lookup"><span data-stu-id="49040-195">Inherited from <xref:System.Security.Permissions.SecurityAttribute>.</span></span>|  
  
#### <a name="connectionstring-syntax"></a><span data-ttu-id="49040-196">ConnectionString 语法</span><span class="sxs-lookup"><span data-stu-id="49040-196">ConnectionString Syntax</span></span>  

 <span data-ttu-id="49040-197">下面的示例演示如何使用配置文件的 `connectionStrings` 元素仅允许使用特定的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="49040-197">The following example demonstrates how to use the `connectionStrings` element of a configuration file to allow only a specific connection string to be used.</span></span> <span data-ttu-id="49040-198">有关从配置文件中存储和检索连接字符串的详细信息，请参阅 [连接字符串](connection-strings.md) 。</span><span class="sxs-lookup"><span data-stu-id="49040-198">See [Connection Strings](connection-strings.md) for more information on storing and retrieving connection strings from configuration files.</span></span>  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"
    connectionString="Data Source=(local);Initial
    Catalog=Northwind;Integrated Security=true;" />  
</connectionStrings>  
```  
  
#### <a name="keyrestrictions-syntax"></a><span data-ttu-id="49040-199">KeyRestrictions 语法</span><span class="sxs-lookup"><span data-stu-id="49040-199">KeyRestrictions Syntax</span></span>  

 <span data-ttu-id="49040-200">下面的示例启用相同的连接字符串，启用 `Encrypt` 和 `Packet Size` 连接字符串选项，但限制使用任何其他连接字符串选项。</span><span class="sxs-lookup"><span data-stu-id="49040-200">The following example enables the same connection string, enables the use of the `Encrypt` and `Packet Size` connection string options, but restricts the use of any other connection string options.</span></span>  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"
    connectionString="Data Source=(local);Initial
    Catalog=Northwind;Integrated Security=true;"  
    KeyRestrictions="Encrypt=;Packet Size=;"  
    KeyRestrictionBehavior="AllowOnly" />  
</connectionStrings>  
```  
  
#### <a name="keyrestrictionbehavior-with-preventusage-syntax"></a><span data-ttu-id="49040-201">包含 PreventUsage 的 KeyRestrictionBehavior 的语法</span><span class="sxs-lookup"><span data-stu-id="49040-201">KeyRestrictionBehavior with PreventUsage Syntax</span></span>  

 <span data-ttu-id="49040-202">下面的示例启用相同的连接字符串，并允许使用 `User Id`、`Password` 和 `Persist Security Info` 以外的所有其他连接参数。</span><span class="sxs-lookup"><span data-stu-id="49040-202">The following example enables the same connection string and allows all other connection parameters except for `User Id`, `Password` and `Persist Security Info`.</span></span>  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"
    connectionString="Data Source=(local);Initial
    Catalog=Northwind;Integrated Security=true;"  
    KeyRestrictions="User Id=;Password=;Persist Security Info=;"  
    KeyRestrictionBehavior="PreventUsage" />  
</connectionStrings>  
```  
  
#### <a name="keyrestrictionbehavior-with-allowonly-syntax"></a><span data-ttu-id="49040-203">包含 AllowOnly 的 KeyRestrictionBehavior 的语法</span><span class="sxs-lookup"><span data-stu-id="49040-203">KeyRestrictionBehavior with AllowOnly Syntax</span></span>  

 <span data-ttu-id="49040-204">以下示例启用两个连接字符串，其中还包含 `Initial Catalog`、`Connection Timeout`、`Encrypt` 和 `Packet Size` 参数。</span><span class="sxs-lookup"><span data-stu-id="49040-204">The following example enables two connection strings that also contain `Initial Catalog`, `Connection Timeout`, `Encrypt`, and `Packet Size` parameters.</span></span> <span data-ttu-id="49040-205">而所有其他的连接字符串参数都被限制。</span><span class="sxs-lookup"><span data-stu-id="49040-205">All other connection string parameters are restricted.</span></span>  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"
    connectionString="Data Source=(local);Initial
    Catalog=Northwind;Integrated Security=true;"  
    KeyRestrictions="Initial Catalog;Connection Timeout=;  
       Encrypt=;Packet Size=;"
    KeyRestrictionBehavior="AllowOnly" />  
  
  <add name="DatabaseConnection2"
    connectionString="Data Source=SqlServer2;Initial
    Catalog=Northwind2;Integrated Security=true;"  
    KeyRestrictions="Initial Catalog;Connection Timeout=;  
       Encrypt=;Packet Size=;"
    KeyRestrictionBehavior="AllowOnly" />  
</connectionStrings>  
```  
  
### <a name="enabling-partial-trust-with-a-custom-permission-set"></a><span data-ttu-id="49040-206">启用具有自定义权限集的部分信任</span><span class="sxs-lookup"><span data-stu-id="49040-206">Enabling Partial Trust with a Custom Permission Set</span></span>  

 <span data-ttu-id="49040-207">要对特定区域启用 <xref:System.Data.SqlClient> 权限，系统管理员必须创建自定义的权限集，并将其设置为特定区域的权限集。</span><span class="sxs-lookup"><span data-stu-id="49040-207">To enable the use of <xref:System.Data.SqlClient> permissions for a particular zone, a system administrator must create a custom permission set and set it as the permission set for a particular zone.</span></span> <span data-ttu-id="49040-208">不能修改默认权限集（如 `LocalIntranet`）。</span><span class="sxs-lookup"><span data-stu-id="49040-208">Default permission sets, such as `LocalIntranet`, cannot be modified.</span></span> <span data-ttu-id="49040-209">例如，若要包含 <xref:System.Data.SqlClient> 具有的代码的权限， <xref:System.Security.Policy.Zone> `LocalIntranet` 系统管理员可以复制的权限集 `LocalIntranet` ，将其重命名为 "CustomLocalIntranet"，添加 <xref:System.Data.SqlClient> 权限，使用 [Caspol.exe (代码访问安全策略工具) ](../../tools/caspol-exe-code-access-security-policy-tool.md)导入 CustomLocalIntranet 权限集，并将权限集设置 `LocalIntranet_Zone` 为 CustomLocalIntranet。</span><span class="sxs-lookup"><span data-stu-id="49040-209">For example, to include <xref:System.Data.SqlClient> permissions for code that has a <xref:System.Security.Policy.Zone> of `LocalIntranet`, a system administrator could copy the permission set for `LocalIntranet`, rename it to "CustomLocalIntranet", add the <xref:System.Data.SqlClient> permissions, import the CustomLocalIntranet permission set using the [Caspol.exe (Code Access Security Policy Tool)](../../tools/caspol-exe-code-access-security-policy-tool.md), and set the permission set of `LocalIntranet_Zone` to CustomLocalIntranet.</span></span>  
  
### <a name="sample-permission-set"></a><span data-ttu-id="49040-210">示例权限集</span><span class="sxs-lookup"><span data-stu-id="49040-210">Sample Permission Set</span></span>  

 <span data-ttu-id="49040-211">下面是在部分受信任方案中，SQL Server .NET Framework 数据提供程序的示例权限集。</span><span class="sxs-lookup"><span data-stu-id="49040-211">The following is a sample permission set for the .NET Framework Data Provider for SQL Server in a partially trusted scenario.</span></span> <span data-ttu-id="49040-212">有关创建自定义权限集的信息，请参阅 [使用 Caspol.exe配置权限集 ](/previous-versions/dotnet/netframework-4.0/4ybs46y6(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="49040-212">For information on creating custom permission sets, see [Configuring Permission Sets Using Caspol.exe](/previous-versions/dotnet/netframework-4.0/4ybs46y6(v=vs.100)).</span></span>  
  
```xml  
<PermissionSet class="System.Security.NamedPermissionSet"  
  version="1"  
  Name="CustomLocalIntranet"  
  Description="Custom permission set given to applications on  
    the local intranet">  
  
<IPermission class="System.Data.SqlClient.SqlClientPermission, System.Data, Version=2.0.0000.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
version="1"  
AllowBlankPassword="False">  
<add ConnectionString="Data Source=(local);Integrated Security=true;"  
 KeyRestrictions="Initial Catalog=;Connection Timeout=;  
   Encrypt=;Packet Size=;"
 KeyRestrictionBehavior="AllowOnly" />  
 </IPermission>  
</PermissionSet>  
```  
  
## <a name="verifying-adonet-code-access-using-security-permissions"></a><span data-ttu-id="49040-213">使用安全权限验证 ADO.NET 代码访问</span><span class="sxs-lookup"><span data-stu-id="49040-213">Verifying ADO.NET Code Access Using Security Permissions</span></span>  

 <span data-ttu-id="49040-214">对于部分信任方案，可以通过指定 <xref:System.Data.SqlClient.SqlClientPermissionAttribute> 来要求代码中的特定方法具有 CAS 特权。</span><span class="sxs-lookup"><span data-stu-id="49040-214">For partial-trust scenarios, you can require CAS privileges for particular methods in your code by specifying a <xref:System.Data.SqlClient.SqlClientPermissionAttribute>.</span></span> <span data-ttu-id="49040-215">如果当前受限制的安全策略不允许该权限，在运行代码之前将引发异常。</span><span class="sxs-lookup"><span data-stu-id="49040-215">If that privilege is not allowed by the restricted security policy in effect, an exception is thrown before your code is run.</span></span> <span data-ttu-id="49040-216">有关安全策略的详细信息，请参阅 [安全策略管理](/previous-versions/dotnet/netframework-4.0/c1k0eed6(v=vs.100)) 和 [安全策略最佳实践](/previous-versions/dotnet/netframework-4.0/sa4se9bc(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="49040-216">For more information on security policy, see [Security Policy Management](/previous-versions/dotnet/netframework-4.0/c1k0eed6(v=vs.100)) and [Security Policy Best Practices](/previous-versions/dotnet/netframework-4.0/sa4se9bc(v=vs.100)).</span></span>  
  
### <a name="example"></a><span data-ttu-id="49040-217">示例</span><span class="sxs-lookup"><span data-stu-id="49040-217">Example</span></span>  

 <span data-ttu-id="49040-218">以下示例演示如何编写要求特定连接字符串的代码。</span><span class="sxs-lookup"><span data-stu-id="49040-218">The following example demonstrates how to write code that requires a particular connection string.</span></span> <span data-ttu-id="49040-219">该示例模拟拒绝为 <xref:System.Data.SqlClient> 授予无限制权限的过程，系统管理员在实际工作中将会使用 CAS 策略实现该过程。</span><span class="sxs-lookup"><span data-stu-id="49040-219">It simulates denying unrestricted permissions to <xref:System.Data.SqlClient>, which a system administrator would implement using a CAS policy in the real world.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="49040-220">在设计 ADO.NET 的 CAS 权限时，正确的模式是以限制性最强的情况开始（无任何权限），然后添加代码执行特定任务所需的特定权限。</span><span class="sxs-lookup"><span data-stu-id="49040-220">When designing CAS permissions for ADO.NET, the correct pattern is to start with the most restrictive case (no permissions at all) and then add the specific permissions that are needed for the particular task that the code needs to perform.</span></span> <span data-ttu-id="49040-221">相反的模式是一开始就授予所有权限，然后拒绝特定权限，这样做是不安全的，因为表达同一连接字符串可以有许多方式。</span><span class="sxs-lookup"><span data-stu-id="49040-221">The opposite pattern, starting with all permissions and then denying a specific permission, is not secure because there are many ways of expressing the same connection string.</span></span> <span data-ttu-id="49040-222">例如，如果一开始就授予所有权限，然后尝试拒绝使用连接字符串“server=someserver”，则仍将允许使用“server=someserver.mycompany.com”。</span><span class="sxs-lookup"><span data-stu-id="49040-222">For example, if you start with all permissions and then attempt to deny the use of the connection string "server=someserver", the string "server=someserver.mycompany.com" would still be allowed.</span></span> <span data-ttu-id="49040-223">通过在开始时始终不授予任何权限，可以降低权限集中存在漏洞的几率。</span><span class="sxs-lookup"><span data-stu-id="49040-223">By always starting by granting no permissions at all, you reduce the chances that there are holes in the permission set.</span></span>  
  
 <span data-ttu-id="49040-224">下面的代码演示 `SqlClient` 如何执行安全请求，如果没有相应的 CAS 权限，将引发 <xref:System.Security.SecurityException>。</span><span class="sxs-lookup"><span data-stu-id="49040-224">The following code demonstrates how `SqlClient` performs the security demand, which throws a <xref:System.Security.SecurityException> if the appropriate CAS permissions are not in place.</span></span> <span data-ttu-id="49040-225">控制台窗口中显示 <xref:System.Security.SecurityException> 输出。</span><span class="sxs-lookup"><span data-stu-id="49040-225">The <xref:System.Security.SecurityException> output is displayed in the console window.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.CAS#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.CAS/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.CAS#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.CAS/VB/source.vb#1)]  
  
 <span data-ttu-id="49040-226">在控制台窗口中应看到以下输出：</span><span class="sxs-lookup"><span data-stu-id="49040-226">You should see this output in the Console window:</span></span>  
  
```output  
Failed, as expected: <IPermission class="System.Data.SqlClient.  
SqlClientPermission, System.Data, Version=2.0.0.0,
  Culture=neutral, PublicKeyToken=b77a5c561934e089" version="1"  
  AllowBlankPassword="False">  
<add ConnectionString="Data Source=(local);Initial Catalog=  
  Northwind;Integrated Security=SSPI" KeyRestrictions=""  
KeyRestrictionBehavior="AllowOnly"/>  
</IPermission>  
  
Connection opened, as expected.  
Failed, as expected: Request failed.  
```  
  
## <a name="interoperability-with-unmanaged-code"></a><span data-ttu-id="49040-227">与非托管代码的互操作性</span><span class="sxs-lookup"><span data-stu-id="49040-227">Interoperability with Unmanaged Code</span></span>  

 <span data-ttu-id="49040-228">在 CLR 外部运行的代码称为非托管代码。</span><span class="sxs-lookup"><span data-stu-id="49040-228">Code that runs outside the CLR is called unmanaged code.</span></span> <span data-ttu-id="49040-229">因此，安全机制（如 CAS）不能应用于非托管代码。</span><span class="sxs-lookup"><span data-stu-id="49040-229">Therefore, security mechanisms such as CAS cannot be applied to unmanaged code.</span></span> <span data-ttu-id="49040-230">COM 组件、ActiveX 接口和 Windows API 函数都是非托管代码的示例。</span><span class="sxs-lookup"><span data-stu-id="49040-230">COM components, ActiveX interfaces, and Windows API functions are examples of unmanaged code.</span></span> <span data-ttu-id="49040-231">在执行非托管代码时应考虑特殊安全注意事项，以便不会危害应用程序的整体安全性。</span><span class="sxs-lookup"><span data-stu-id="49040-231">Special security considerations apply when executing unmanaged code so that you do not jeopardize overall application security.</span></span> <span data-ttu-id="49040-232">有关详细信息，请参阅[与非托管代码交互操作](../../interop/index.md)。</span><span class="sxs-lookup"><span data-stu-id="49040-232">For more information, see [Interoperating with Unmanaged Code](../../interop/index.md).</span></span>  
  
 <span data-ttu-id="49040-233">.NET Framework 可以通过 COM 互操作提供访问，因此还支持与现有 COM 组件的向后兼容。</span><span class="sxs-lookup"><span data-stu-id="49040-233">The .NET Framework also supports backward compatibility to existing COM components by providing access through COM interop.</span></span> <span data-ttu-id="49040-234">通过使用 COM 互操作工具导入相关的 COM 类型，可以将 COM 组件合并到 .NET Framework 应用程序中。</span><span class="sxs-lookup"><span data-stu-id="49040-234">You can incorporate COM components into a .NET Framework application by using COM interop tools to import the relevant COM types.</span></span> <span data-ttu-id="49040-235">一旦导入后，就可以使用 COM 类型了。</span><span class="sxs-lookup"><span data-stu-id="49040-235">Once imported, the COM types are ready to use.</span></span> <span data-ttu-id="49040-236">通过将程序集元数据导出到类型库并将托管组件注册为 COM 组件，COM 互操作还可以使 COM 客户端访问托管代码。</span><span class="sxs-lookup"><span data-stu-id="49040-236">COM interop also enables COM clients to access managed code by exporting assembly metadata to a type library and registering the managed component as a COM component.</span></span> <span data-ttu-id="49040-237">有关详细信息，请参阅 [高级 COM 互操作性](/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="49040-237">For more information, see [Advanced COM Interoperability](/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49040-238">请参阅</span><span class="sxs-lookup"><span data-stu-id="49040-238">See also</span></span>

- [<span data-ttu-id="49040-239">保证 ADO.NET 应用程序的安全</span><span class="sxs-lookup"><span data-stu-id="49040-239">Securing ADO.NET Applications</span></span>](securing-ado-net-applications.md)
- <span data-ttu-id="49040-240">[本机代码和 .NET Framework 代码的安全性](/previous-versions/visualstudio/visual-studio-2010/1787tk12(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="49040-240">[Security in Native and .NET Framework Code](/previous-versions/visualstudio/visual-studio-2010/1787tk12(v=vs.100))</span></span>
- [<span data-ttu-id="49040-241">基于角色的安全性</span><span class="sxs-lookup"><span data-stu-id="49040-241">Role-Based Security</span></span>](../../../standard/security/role-based-security.md)
- [<span data-ttu-id="49040-242">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="49040-242">ADO.NET Overview</span></span>](ado-net-overview.md)
