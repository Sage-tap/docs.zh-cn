---
description: 了解详细信息：如何：使用 PrincipalPermissionAttribute 类限制访问
title: 如何：使用 PrincipalPermissionAttribute 类限制访问
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PrincipalPermissionAttribute class
- WCF, authorization
- WCF, security
ms.assetid: 5162f5c4-8781-4cc4-9425-bb7620eaeaf4
ms.openlocfilehash: 533bd3358d5e337071c6419264d1dac03b8987ca
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779343"
---
# <a name="how-to-restrict-access-with-the-principalpermissionattribute-class"></a><span data-ttu-id="a7950-103">如何：使用 PrincipalPermissionAttribute 类限制访问</span><span class="sxs-lookup"><span data-stu-id="a7950-103">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>

<span data-ttu-id="a7950-104">控制对 Windows 域计算机上的资源的访问是一项基本的安全任务。</span><span class="sxs-lookup"><span data-stu-id="a7950-104">Controlling the access to resources on a Windows-domain computer is a basic security task.</span></span> <span data-ttu-id="a7950-105">例如，应该只有某些用户才能查看敏感数据，例如工资单信息。</span><span class="sxs-lookup"><span data-stu-id="a7950-105">For example, only certain users should be able to view sensitive data, such as payroll information.</span></span> <span data-ttu-id="a7950-106">本主题解释如何通过要求用户属于某个预定义组来限制对方法的访问。</span><span class="sxs-lookup"><span data-stu-id="a7950-106">This topic explains how to restrict access to a method by demanding that the user belong to a predefined group.</span></span> <span data-ttu-id="a7950-107">有关工作示例，请参阅 [授权访问服务操作](./samples/authorizing-access-to-service-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="a7950-107">For a working sample, see [Authorizing Access to Service Operations](./samples/authorizing-access-to-service-operations.md).</span></span>  
  
 <span data-ttu-id="a7950-108">此任务由两个单独的过程组成。</span><span class="sxs-lookup"><span data-stu-id="a7950-108">The task consists of two separate procedures.</span></span> <span data-ttu-id="a7950-109">第一个过程创建组，并用用户填充它。</span><span class="sxs-lookup"><span data-stu-id="a7950-109">The first creates the group and populates it with users.</span></span> <span data-ttu-id="a7950-110">第二个过程应用 <xref:System.Security.Permissions.PrincipalPermissionAttribute> 类以指定组。</span><span class="sxs-lookup"><span data-stu-id="a7950-110">The second applies the <xref:System.Security.Permissions.PrincipalPermissionAttribute> class to specify the group.</span></span>  
  
### <a name="to-create-a-windows-group"></a><span data-ttu-id="a7950-111">创建 Windows 组</span><span class="sxs-lookup"><span data-stu-id="a7950-111">To create a Windows group</span></span>  
  
1. <span data-ttu-id="a7950-112">打开 " **计算机管理** " 控制台。</span><span class="sxs-lookup"><span data-stu-id="a7950-112">Open the **Computer Management** console.</span></span>  
  
2. <span data-ttu-id="a7950-113">在左侧面板中，单击 " **本地用户和组**"。</span><span class="sxs-lookup"><span data-stu-id="a7950-113">In the left panel, click **Local Users and Groups**.</span></span>  
  
3. <span data-ttu-id="a7950-114">右键单击 " **组**"，然后单击 " **新建组**"。</span><span class="sxs-lookup"><span data-stu-id="a7950-114">Right-click **Groups**, and click **New Group**.</span></span>  
  
4. <span data-ttu-id="a7950-115">在 " **组名称** " 框中，键入新组的名称。</span><span class="sxs-lookup"><span data-stu-id="a7950-115">In the **Group Name** box, type a name for the new group.</span></span>  
  
5. <span data-ttu-id="a7950-116">在 " **说明** " 框中，键入新组的描述。</span><span class="sxs-lookup"><span data-stu-id="a7950-116">In the **Description** box, type a description of the new group.</span></span>  
  
6. <span data-ttu-id="a7950-117">单击 " **添加** " 按钮将新成员添加到组中。</span><span class="sxs-lookup"><span data-stu-id="a7950-117">Click the **Add** button to add new members to the group.</span></span>  
  
7. <span data-ttu-id="a7950-118">如果你已经将自己添加到该组中，并且想要测试下面的代码，则必须注销计算机并重新登录，以便将自己包括到该组中。</span><span class="sxs-lookup"><span data-stu-id="a7950-118">If you have added yourself to the group and want to test the following code, you must log off the computer and log back on to be included in the group.</span></span>  
  
### <a name="to-demand-user-membership"></a><span data-ttu-id="a7950-119">要求用户具有成员资格</span><span class="sxs-lookup"><span data-stu-id="a7950-119">To demand user membership</span></span>  
  
1. <span data-ttu-id="a7950-120">打开包含已实现的服务协定代码 (WCF) 代码文件的 Windows Communication Foundation。</span><span class="sxs-lookup"><span data-stu-id="a7950-120">Open the Windows Communication Foundation (WCF) code file that contains the implemented service contract code.</span></span> <span data-ttu-id="a7950-121">有关实现协定的详细信息，请参阅 [实现服务协定](implementing-service-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="a7950-121">For more information about implementing a contract, see [Implementing Service Contracts](implementing-service-contracts.md).</span></span>  
  
2. <span data-ttu-id="a7950-122">将 <xref:System.Security.Permissions.PrincipalPermissionAttribute> 属性应用于每个必须限制到特定组的方法。</span><span class="sxs-lookup"><span data-stu-id="a7950-122">Apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to each method that must be restricted to a specific group.</span></span> <span data-ttu-id="a7950-123">将 <xref:System.Security.Permissions.SecurityAttribute.Action%2A> 属性设置为 <xref:System.Security.Permissions.SecurityAction.Demand>，并将 <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A> 属性设置为组名称。</span><span class="sxs-lookup"><span data-stu-id="a7950-123">Set the <xref:System.Security.Permissions.SecurityAttribute.Action%2A> property to <xref:System.Security.Permissions.SecurityAction.Demand> and the <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A> property to the name of the group.</span></span> <span data-ttu-id="a7950-124">例如：</span><span class="sxs-lookup"><span data-stu-id="a7950-124">For example:</span></span>  
  
     [!code-csharp[c_PrincipalPermissionAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#1)]
     [!code-vb[c_PrincipalPermissionAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#1)]  
  
    > [!NOTE]
    > <span data-ttu-id="a7950-125">如果将 <xref:System.Security.Permissions.PrincipalPermissionAttribute> 属性应用到某个协定，将会引发 <xref:System.Security.SecurityException>。</span><span class="sxs-lookup"><span data-stu-id="a7950-125">If you apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to a contract a <xref:System.Security.SecurityException> will be thrown.</span></span> <span data-ttu-id="a7950-126">只能在方法级别应用该属性。</span><span class="sxs-lookup"><span data-stu-id="a7950-126">You can only apply the attribute at the method level.</span></span>  
  
## <a name="using-a-certificate-to-control-access-to-a-method"></a><span data-ttu-id="a7950-127">使用证书控制对方法的访问</span><span class="sxs-lookup"><span data-stu-id="a7950-127">Using a Certificate to Control Access to a Method</span></span>  

 <span data-ttu-id="a7950-128">如果客户端凭据类型是证书，还可以使用 `PrincipalPermissionAttribute` 类控制对方法的访问。</span><span class="sxs-lookup"><span data-stu-id="a7950-128">You can also use the `PrincipalPermissionAttribute` class to control access to a method if the client credential type is a certificate.</span></span> <span data-ttu-id="a7950-129">为此，您必须具有证书的主题和指纹。</span><span class="sxs-lookup"><span data-stu-id="a7950-129">To do this, you must have the certificate's subject and thumbprint.</span></span>  
  
 <span data-ttu-id="a7950-130">若要检查证书的属性，请参阅 [如何：使用 MMC 管理单元查看证书](./feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)。</span><span class="sxs-lookup"><span data-stu-id="a7950-130">To examine a certificate for its properties, see [How to: View Certificates with the MMC Snap-in](./feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span> <span data-ttu-id="a7950-131">若要查找 "指纹" 值，请参阅 [如何：检索证书的指纹](./feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)。</span><span class="sxs-lookup"><span data-stu-id="a7950-131">To find the thumbprint value, see [How to: Retrieve the Thumbprint of a Certificate](./feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
#### <a name="to-control-access-using-a-certificate"></a><span data-ttu-id="a7950-132">使用证书控制访问</span><span class="sxs-lookup"><span data-stu-id="a7950-132">To control access using a certificate</span></span>  
  
1. <span data-ttu-id="a7950-133">将 <xref:System.Security.Permissions.PrincipalPermissionAttribute> 类应用于您要对其访问进行限制的方法。</span><span class="sxs-lookup"><span data-stu-id="a7950-133">Apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> class to the method you want to restrict access to.</span></span>  
  
2. <span data-ttu-id="a7950-134">将属性的操作设置为 <xref:System.Security.Permissions.SecurityAction.Demand?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="a7950-134">Set the action of the attribute to <xref:System.Security.Permissions.SecurityAction.Demand?displayProperty=nameWithType>.</span></span>  
  
3. <span data-ttu-id="a7950-135">将 `Name` 属性设置为包含主题名称和证书指纹的字符串。</span><span class="sxs-lookup"><span data-stu-id="a7950-135">Set the `Name` property to a string that consists of the subject name and the certificate's thumbprint.</span></span> <span data-ttu-id="a7950-136">用一个分号和一个空格将这两个值分隔开，如下面的示例所示：</span><span class="sxs-lookup"><span data-stu-id="a7950-136">Separate the two values with a semicolon and a space, as shown in the following example:</span></span>  
  
     [!code-csharp[c_PrincipalPermissionAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#2)]
     [!code-vb[c_PrincipalPermissionAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#2)]  
  
4. <span data-ttu-id="a7950-137">将 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> 属性设置为 <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>，如下面的配置示例所示：</span><span class="sxs-lookup"><span data-stu-id="a7950-137">Set the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property to <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> as shown in the following configuration example:</span></span>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
      <behavior name="SvcBehavior1">  
      <serviceAuthorization principalPermissionMode="UseAspNetRoles" />  
      </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     <span data-ttu-id="a7950-138">将此值设置为 `UseAspNetRoles` 表示 `Name` 的 `PrincipalPermissionAttribute` 属性将用于执行字符串比较。</span><span class="sxs-lookup"><span data-stu-id="a7950-138">Setting this value to `UseAspNetRoles` indicates that the `Name` property of the `PrincipalPermissionAttribute` will be used to perform a string comparison.</span></span> <span data-ttu-id="a7950-139">使用证书作为客户端凭据时，默认情况下，WCF 会将证书公用名和指纹连接起来，以创建客户端主要标识的唯一值。</span><span class="sxs-lookup"><span data-stu-id="a7950-139">When a certificate is used as a client credential, by default WCF concatenates the certificate common name and the thumbprint with a semicolon to create a unique value for the client's primary identity.</span></span> <span data-ttu-id="a7950-140">在将 `UseAspNetRoles` 设置为服务上的 `PrincipalPermissionMode` 之后，会将此主标识值与 `Name` 属性值进行比较，以确定用户的访问权限。</span><span class="sxs-lookup"><span data-stu-id="a7950-140">With `UseAspNetRoles` set as the `PrincipalPermissionMode` on the service, this primary identity value is compared with the `Name` property value to determine the access rights of the user.</span></span>  
  
     <span data-ttu-id="a7950-141">此外，在创建自承载服务时，还可以按照以下代码中的方式在代码中设置 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> 属性：</span><span class="sxs-lookup"><span data-stu-id="a7950-141">Alternatively, when creating a self-hosted service, set the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property in code as shown in the following code:</span></span>  
  
     [!code-csharp[c_PrincipalPermissionAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#3)]
     [!code-vb[c_PrincipalPermissionAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="a7950-142">请参阅</span><span class="sxs-lookup"><span data-stu-id="a7950-142">See also</span></span>

- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- <xref:System.Security.Permissions.SecurityAction.Demand>
- <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A>
- [<span data-ttu-id="a7950-143">授予对服务操作的访问权限</span><span class="sxs-lookup"><span data-stu-id="a7950-143">Authorizing Access to Service Operations</span></span>](./samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="a7950-144">安全性概述</span><span class="sxs-lookup"><span data-stu-id="a7950-144">Security Overview</span></span>](./feature-details/security-overview.md)
- [<span data-ttu-id="a7950-145">实现服务协定</span><span class="sxs-lookup"><span data-stu-id="a7950-145">Implementing Service Contracts</span></span>](implementing-service-contracts.md)
