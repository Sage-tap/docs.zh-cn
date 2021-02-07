---
description: 了解详细信息：安全性概述
title: 安全概述
ms.date: 03/30/2017
ms.assetid: 33e09965-61d5-48cc-9e8c-3b047cc4f194
ms.openlocfilehash: 3aa6e5cbe444e9cfc417d79defce7e89a2034f71
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718819"
---
# <a name="security-overview"></a><span data-ttu-id="5f80b-103">安全概述</span><span class="sxs-lookup"><span data-stu-id="5f80b-103">Security overview</span></span>

<span data-ttu-id="5f80b-104">保护应用程序的安全是一个持续的过程。</span><span class="sxs-lookup"><span data-stu-id="5f80b-104">Securing an application is an ongoing process.</span></span> <span data-ttu-id="5f80b-105">因为不可能预知将来会出现哪种新的攻击技术，所以开发人员永远都不能保证某一应用程序可以免受所有的攻击。</span><span class="sxs-lookup"><span data-stu-id="5f80b-105">There will never be a point where a developer can guarantee that an application is safe from all attacks, because it is impossible to predict what kinds of future attacks new technologies will bring about.</span></span> <span data-ttu-id="5f80b-106">仅因为还没有人发现（或发布）系统中的安全性缺陷，也不意味着不存在或可能不存在安全性缺陷。</span><span class="sxs-lookup"><span data-stu-id="5f80b-106">Conversely, just because nobody has yet discovered (or published) security flaws in a system does not mean that none exist or could exist.</span></span> <span data-ttu-id="5f80b-107">在项目的设计阶段，您需要对安全性进行规划，并规划如何在应用程序生存期内维护其安全。</span><span class="sxs-lookup"><span data-stu-id="5f80b-107">You need to plan for security during the design phase of the project, as well as plan how security will be maintained over the lifetime of the application.</span></span>

## <a name="design-for-security"></a><span data-ttu-id="5f80b-108">安全性设计</span><span class="sxs-lookup"><span data-stu-id="5f80b-108">Design for Security</span></span>

 <span data-ttu-id="5f80b-109">在开发安全应用程序时遇到的最大问题之一是安全通常是事后的补救办法，即在项目的代码完成后才想起需要实现某些内容。</span><span class="sxs-lookup"><span data-stu-id="5f80b-109">One of the biggest problems in developing secure applications is that security is often an afterthought, something to implement after a project is code-complete.</span></span> <span data-ttu-id="5f80b-110">因为未考虑如何维护应用程序的安全，所以在开始阶段未注重应用程序安全性将导致所开发的应用程序不安全。</span><span class="sxs-lookup"><span data-stu-id="5f80b-110">Not building security into an application at the outset leads to insecure applications because little thought has been given to what makes an application secure.</span></span>

 <span data-ttu-id="5f80b-111">最新的安全实现会导致更多的 bug，因为软件会在新的限制下中断，或者必须重新编写才能容纳意想不到的功能。</span><span class="sxs-lookup"><span data-stu-id="5f80b-111">Last-minute security implementation leads to more bugs, as software breaks under the new restrictions or has to be rewritten to accommodate unanticipated functionality.</span></span> <span data-ttu-id="5f80b-112">每行修订的代码都可能引入新 Bug。</span><span class="sxs-lookup"><span data-stu-id="5f80b-112">Every line of revised code contains the possibility of introducing a new bug.</span></span> <span data-ttu-id="5f80b-113">因此，您在开发过程的初始阶段就应考虑安全性，使得安全性可与新功能的开发同步进行。</span><span class="sxs-lookup"><span data-stu-id="5f80b-113">For this reason, you should consider security early in the development process so that it can proceed in tandem with the development of new features.</span></span>

### <a name="threat-modeling"></a><span data-ttu-id="5f80b-114">威胁建模</span><span class="sxs-lookup"><span data-stu-id="5f80b-114">Threat Modeling</span></span>

 <span data-ttu-id="5f80b-115">您只有了解系统可能会受到的所有攻击，才能使系统免受这些攻击。</span><span class="sxs-lookup"><span data-stu-id="5f80b-115">You cannot protect a system against attack unless you understand all the potential attacks that it is exposed to.</span></span> <span data-ttu-id="5f80b-116">若要确定 ADO.NET 应用程序中安全漏洞的可能性和后果，需要评估安全威胁（称为 " *威胁建模*"）的过程。</span><span class="sxs-lookup"><span data-stu-id="5f80b-116">The process of evaluating security threats, called *threat modeling*, is necessary to determine the likelihood and ramifications of security breaches in your ADO.NET application.</span></span>

 <span data-ttu-id="5f80b-117">威胁建模由三个高级步骤组成：了解攻击者的目的、辨别系统安全性和确定威胁。</span><span class="sxs-lookup"><span data-stu-id="5f80b-117">Threat modeling is composed of three high-level steps: understanding the adversary’s view, characterizing the security of the system, and determining threats.</span></span>

 <span data-ttu-id="5f80b-118">威胁建模是一种迭代方法，用于评估应用程序中的漏洞，以找到可公开敏感数据的最危险的漏洞。</span><span class="sxs-lookup"><span data-stu-id="5f80b-118">Threat modeling is an iterative approach to assessing vulnerabilities in your application to find those that are the most dangerous because they expose the most sensitive data.</span></span> <span data-ttu-id="5f80b-119">一旦确定了漏洞，您就可以按安全性对其进行排列，并创建一组按优先顺序排列的措施以应对威胁。</span><span class="sxs-lookup"><span data-stu-id="5f80b-119">Once you identify the vulnerabilities, you rank them in order of severity and create a prioritized set of countermeasures to counter the threats.</span></span>

<span data-ttu-id="5f80b-120">有关更多信息，请参见以下资源：</span><span class="sxs-lookup"><span data-stu-id="5f80b-120">For more information, see the following resources:</span></span>

|<span data-ttu-id="5f80b-121">资源</span><span class="sxs-lookup"><span data-stu-id="5f80b-121">Resource</span></span>|<span data-ttu-id="5f80b-122">说明</span><span class="sxs-lookup"><span data-stu-id="5f80b-122">Description</span></span>|
|--------------|-----------------|
|<span data-ttu-id="5f80b-123">安全工程门户上的 [威胁建模](https://www.microsoft.com/securityengineering/sdl/threatmodeling) 站点</span><span class="sxs-lookup"><span data-stu-id="5f80b-123">The [Threat Modeling](https://www.microsoft.com/securityengineering/sdl/threatmodeling) site on the Security Engineering Portal</span></span>|<span data-ttu-id="5f80b-124">此页上的资源将帮助您了解威胁建模的过程，并帮助您创建可以用于保护自己的应用程序的威胁模型</span><span class="sxs-lookup"><span data-stu-id="5f80b-124">The resources on this page will help you understand the threat modeling process and build threat models that you can use to secure your own applications</span></span>|

## <a name="the-principle-of-least-privilege"></a><span data-ttu-id="5f80b-125">最低特权原则</span><span class="sxs-lookup"><span data-stu-id="5f80b-125">The Principle of Least Privilege</span></span>

 <span data-ttu-id="5f80b-126">当设计、构建及部署应用程序时，您必须假定您的应用程序将受到攻击。</span><span class="sxs-lookup"><span data-stu-id="5f80b-126">When you design, build, and deploy your application, you must assume that your application will be attacked.</span></span> <span data-ttu-id="5f80b-127">通常，这些攻击来自使用运行此代码的用户的权限执行的恶意代码，</span><span class="sxs-lookup"><span data-stu-id="5f80b-127">Often these attacks come from malicious code that executes with the permissions of the user running the code.</span></span> <span data-ttu-id="5f80b-128">其他攻击可能源自被攻击者利用的善意代码。</span><span class="sxs-lookup"><span data-stu-id="5f80b-128">Others can originate with well-intentioned code that has been exploited by an attacker.</span></span> <span data-ttu-id="5f80b-129">在规划安全性时，始终假设将出现最糟糕的情况。</span><span class="sxs-lookup"><span data-stu-id="5f80b-129">When planning security, always assume the worst-case scenario will occur.</span></span>

 <span data-ttu-id="5f80b-130">您可以使用的一种措施是：尝试使用最小特权来运行代码，在代码周围树立尽可能多的障碍。</span><span class="sxs-lookup"><span data-stu-id="5f80b-130">One counter-measure you can employ is to try to erect as many walls around your code as possible by running with least privilege.</span></span> <span data-ttu-id="5f80b-131">最小特权原则指出，应在完成工作所需的最短时间内向所需的最少代码授予任何给定的特权。</span><span class="sxs-lookup"><span data-stu-id="5f80b-131">The principle of least privilege says that any given privilege should be granted to the least amount of code necessary for the shortest duration of time that is required to get the job done.</span></span>

 <span data-ttu-id="5f80b-132">创建安全应用程序的最好方法是在开始阶段不授予任何权限，然后对执行的特定任务添加最有限的权限。</span><span class="sxs-lookup"><span data-stu-id="5f80b-132">The best practice for creating secure applications is to start with no permissions at all and then add the narrowest permissions for the particular task being performed.</span></span> <span data-ttu-id="5f80b-133">相反，如果开始具有所有权限而以后拒绝个别权限，就会导致难以测试和维护的不安全应用程序，因为无意中授予过多的权限会造成完全漏洞。</span><span class="sxs-lookup"><span data-stu-id="5f80b-133">By contrast, starting with all permissions and then denying individual ones leads to insecure applications that are difficult to test and maintain because security holes may exist from unintentionally granting more permissions than required.</span></span>

<span data-ttu-id="5f80b-134">有关保护应用程序的详细信息，请参阅以下资源：</span><span class="sxs-lookup"><span data-stu-id="5f80b-134">For more information on securing your applications, see the following resources:</span></span>

|<span data-ttu-id="5f80b-135">资源</span><span class="sxs-lookup"><span data-stu-id="5f80b-135">Resource</span></span>|<span data-ttu-id="5f80b-136">说明</span><span class="sxs-lookup"><span data-stu-id="5f80b-136">Description</span></span>|
|--------------|-----------------|
|[<span data-ttu-id="5f80b-137">保护应用程序</span><span class="sxs-lookup"><span data-stu-id="5f80b-137">Securing Applications</span></span>](/visualstudio/ide/securing-applications)|<span data-ttu-id="5f80b-138">包含一般安全性主题的链接，</span><span class="sxs-lookup"><span data-stu-id="5f80b-138">Contains links to general security topics.</span></span> <span data-ttu-id="5f80b-139">还包含保护分布式应用程序、Web 应用程序、移动应用程序和桌面应用程序的主题的链接。</span><span class="sxs-lookup"><span data-stu-id="5f80b-139">Also contains links to topics for securing distributed applications, Web applications, mobile applications, and desktop applications.</span></span>|

## <a name="code-access-security-cas"></a><span data-ttu-id="5f80b-140">代码访问安全性 (CAS)</span><span class="sxs-lookup"><span data-stu-id="5f80b-140">Code Access Security (CAS)</span></span>

<span data-ttu-id="5f80b-141">代码访问安全性 (CAS) 是帮助限制代码对受保护资源和操作的访问权限的一种机制。</span><span class="sxs-lookup"><span data-stu-id="5f80b-141">Code access security (CAS) is a mechanism that helps limit the access that code has to protected resources and operations.</span></span> <span data-ttu-id="5f80b-142">在 .NET Framework 中，CAS 执行下列功能：</span><span class="sxs-lookup"><span data-stu-id="5f80b-142">In the .NET Framework, CAS performs the following functions:</span></span>

- <span data-ttu-id="5f80b-143">定义权限和权限集，它们表示访问各种系统资源的权限。</span><span class="sxs-lookup"><span data-stu-id="5f80b-143">Defines permissions and permission sets that represent the right to access various system resources.</span></span>

- <span data-ttu-id="5f80b-144">使管理员能够通过将权限集与代码组关联来配置安全策略。</span><span class="sxs-lookup"><span data-stu-id="5f80b-144">Enables administrators to configure security policy by associating sets of permissions with groups of code (code groups).</span></span>

- <span data-ttu-id="5f80b-145">使代码能够请求运行所必需的权限及其他一些有用的权限，并指定代码绝对不能拥有哪些权限。</span><span class="sxs-lookup"><span data-stu-id="5f80b-145">Enables code to request the permissions it requires in order to run, as well as the permissions that would be useful to have, and specifies which permissions the code must never have.</span></span>

- <span data-ttu-id="5f80b-146">根据代码要求的权限和安全策略允许的操作，向加载的每个程序集授予权限。</span><span class="sxs-lookup"><span data-stu-id="5f80b-146">Grants permissions to each assembly that is loaded, based on the permissions requested by the code and on the operations permitted by security policy.</span></span>

- <span data-ttu-id="5f80b-147">使代码能够要求其调用方拥有特定的权限。</span><span class="sxs-lookup"><span data-stu-id="5f80b-147">Enables code to demand that its callers have specific permissions.</span></span>

- <span data-ttu-id="5f80b-148">使代码能够要求其调用方拥有数字签名，从而只允许特定组织或特定站点的调用方来调用受保护的代码。</span><span class="sxs-lookup"><span data-stu-id="5f80b-148">Enables code to demand that its callers possess a digital signature, thus allowing only callers from a particular organization or site to call the protected code.</span></span>

- <span data-ttu-id="5f80b-149">通过将调用堆栈上为每个调用方授予的权限与调用方必须拥有的权限相比较，加强在运行时对代码的限制。</span><span class="sxs-lookup"><span data-stu-id="5f80b-149">Enforces restrictions on code at run time by comparing the granted permissions of every caller on the call stack to the permissions that callers must have.</span></span>

<span data-ttu-id="5f80b-150">若要将因攻击成功而导致的损害降到最低，请为你的代码选择安全上下文，以便只向资源授予其完成工作所必需的访问权限。</span><span class="sxs-lookup"><span data-stu-id="5f80b-150">To minimize the amount of damage that can occur if an attack succeeds, choose a security context for your code that grants access only to the resources it needs to get its work done and no more.</span></span>

<span data-ttu-id="5f80b-151">有关更多信息，请参见以下资源：</span><span class="sxs-lookup"><span data-stu-id="5f80b-151">For more information, see the following resources:</span></span>

|<span data-ttu-id="5f80b-152">资源</span><span class="sxs-lookup"><span data-stu-id="5f80b-152">Resource</span></span>|<span data-ttu-id="5f80b-153">说明</span><span class="sxs-lookup"><span data-stu-id="5f80b-153">Description</span></span>|
|--------------|-----------------|
|[<span data-ttu-id="5f80b-154">代码访问安全性和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5f80b-154">Code Access Security and ADO.NET</span></span>](code-access-security.md)|<span data-ttu-id="5f80b-155">从 ADO.NET 应用程序角度描述代码访问安全性、基于角色安全性以及部分受信任环境之间的交互。</span><span class="sxs-lookup"><span data-stu-id="5f80b-155">Describes the interactions between code access security, role-based security, and partially trusted environments from the perspective of an ADO.NET application.</span></span>|
|[<span data-ttu-id="5f80b-156">代码访问安全性</span><span class="sxs-lookup"><span data-stu-id="5f80b-156">Code Access Security</span></span>](../../misc/code-access-security.md)|<span data-ttu-id="5f80b-157">包含描述 .NET Framework 中 CAS 的主题的链接。</span><span class="sxs-lookup"><span data-stu-id="5f80b-157">Contains links to additional topics describing CAS in the .NET Framework.</span></span>|

## <a name="database-security"></a><span data-ttu-id="5f80b-158">数据库安全性</span><span class="sxs-lookup"><span data-stu-id="5f80b-158">Database Security</span></span>

<span data-ttu-id="5f80b-159">最小特权原则也适用于数据源。</span><span class="sxs-lookup"><span data-stu-id="5f80b-159">The principle of least privilege also applies to your data source.</span></span> <span data-ttu-id="5f80b-160">数据库安全性一般准则包括：</span><span class="sxs-lookup"><span data-stu-id="5f80b-160">Some general guidelines for database security include:</span></span>

- <span data-ttu-id="5f80b-161">使用最低可能的特权创建帐户。</span><span class="sxs-lookup"><span data-stu-id="5f80b-161">Create accounts with the lowest possible privileges.</span></span>

- <span data-ttu-id="5f80b-162">不允许用户访问管理帐户，只允许运行代码。</span><span class="sxs-lookup"><span data-stu-id="5f80b-162">Do not allow users access to administrative accounts just to get code working.</span></span>

- <span data-ttu-id="5f80b-163">不要将服务器端错误消息返回到客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="5f80b-163">Do not return server-side error messages to client applications.</span></span>

- <span data-ttu-id="5f80b-164">验证客户端和服务器端的所有输入。</span><span class="sxs-lookup"><span data-stu-id="5f80b-164">Validate all input at both the client and the server.</span></span>

- <span data-ttu-id="5f80b-165">使用参数化命令，避免动态 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="5f80b-165">Use parameterized commands and avoid dynamic SQL statements.</span></span>

- <span data-ttu-id="5f80b-166">为您使用的数据库启用安全审核和记录，以便违反任何安全性时得到警报。</span><span class="sxs-lookup"><span data-stu-id="5f80b-166">Enable security auditing and logging for the database you are using so that you are alerted to any security breaches.</span></span>

<span data-ttu-id="5f80b-167">有关更多信息，请参见以下资源：</span><span class="sxs-lookup"><span data-stu-id="5f80b-167">For more information, see the following resources:</span></span>

|<span data-ttu-id="5f80b-168">资源</span><span class="sxs-lookup"><span data-stu-id="5f80b-168">Resource</span></span>|<span data-ttu-id="5f80b-169">说明</span><span class="sxs-lookup"><span data-stu-id="5f80b-169">Description</span></span>|
|--------------|-----------------|
|[<span data-ttu-id="5f80b-170">SQL Server 安全性</span><span class="sxs-lookup"><span data-stu-id="5f80b-170">SQL Server Security</span></span>](./sql/sql-server-security.md)|<span data-ttu-id="5f80b-171">提供 SQL Server 安全性和应用方案的概述，这些应用方案提供用于创建针对 SQL Server 的安全 ADO.NET 应用程序的指南。</span><span class="sxs-lookup"><span data-stu-id="5f80b-171">Provides an overview of SQL Server security with application scenarios that provide guidance for creating secure ADO.NET applications that target SQL Server.</span></span>|
|<span data-ttu-id="5f80b-172">[数据访问策略的建议](/previous-versions/visualstudio/visual-studio-2008/8fxztkff(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="5f80b-172">[Recommendations for Data Access Strategies](/previous-versions/visualstudio/visual-studio-2008/8fxztkff(v=vs.90))</span></span>|<span data-ttu-id="5f80b-173">提供用于访问数据和执行数据库操作的建议。</span><span class="sxs-lookup"><span data-stu-id="5f80b-173">Provides recommendations for accessing data and performing database operations.</span></span>|

## <a name="security-policy-and-administration"></a><span data-ttu-id="5f80b-174">安全策略和管理</span><span class="sxs-lookup"><span data-stu-id="5f80b-174">Security Policy and Administration</span></span>

<span data-ttu-id="5f80b-175">不正确管理代码访问安全性 (CAS) 策略可能会导致安全漏洞。</span><span class="sxs-lookup"><span data-stu-id="5f80b-175">Improperly administering code access security (CAS) policy can potentially create security weaknesses.</span></span> <span data-ttu-id="5f80b-176">应用程序一旦部署，就应使用监视安全性的技术，因为将出现评估为新威胁的风险。</span><span class="sxs-lookup"><span data-stu-id="5f80b-176">Once an application is deployed, techniques for monitoring security should be used and risks evaluated as new threats emerge.</span></span>

<span data-ttu-id="5f80b-177">有关更多信息，请参见以下资源：</span><span class="sxs-lookup"><span data-stu-id="5f80b-177">For more information, see the following resources:</span></span>

|<span data-ttu-id="5f80b-178">资源</span><span class="sxs-lookup"><span data-stu-id="5f80b-178">Resource</span></span>|<span data-ttu-id="5f80b-179">说明</span><span class="sxs-lookup"><span data-stu-id="5f80b-179">Description</span></span>|
|--------------|-----------------|
|<span data-ttu-id="5f80b-180">[安全策略管理](/previous-versions/dotnet/netframework-4.0/c1k0eed6(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5f80b-180">[Security Policy Management](/previous-versions/dotnet/netframework-4.0/c1k0eed6(v=vs.100))</span></span>|<span data-ttu-id="5f80b-181">提供有关创建和管理安全策略的信息。</span><span class="sxs-lookup"><span data-stu-id="5f80b-181">Provides information on creating and administering security policy.</span></span>|
|<span data-ttu-id="5f80b-182">[安全策略最佳实践](/previous-versions/dotnet/netframework-4.0/sa4se9bc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5f80b-182">[Security Policy Best Practices](/previous-versions/dotnet/netframework-4.0/sa4se9bc(v=vs.100))</span></span>|<span data-ttu-id="5f80b-183">提供描述如何管理安全策略的链接。</span><span class="sxs-lookup"><span data-stu-id="5f80b-183">Provides links describing how to administer security policy.</span></span>|

## <a name="see-also"></a><span data-ttu-id="5f80b-184">请参阅</span><span class="sxs-lookup"><span data-stu-id="5f80b-184">See also</span></span>

- [<span data-ttu-id="5f80b-185">保证 ADO.NET 应用程序的安全</span><span class="sxs-lookup"><span data-stu-id="5f80b-185">Securing ADO.NET Applications</span></span>](securing-ado-net-applications.md)
- [<span data-ttu-id="5f80b-186">.NET 中的安全性</span><span class="sxs-lookup"><span data-stu-id="5f80b-186">Security in .NET</span></span>](../../../standard/security/index.md)
- [<span data-ttu-id="5f80b-187">SQL Server 安全性</span><span class="sxs-lookup"><span data-stu-id="5f80b-187">SQL Server Security</span></span>](./sql/sql-server-security.md)
- [<span data-ttu-id="5f80b-188">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="5f80b-188">ADO.NET Overview</span></span>](ado-net-overview.md)
