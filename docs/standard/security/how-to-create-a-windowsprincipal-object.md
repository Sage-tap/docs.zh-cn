---
description: 了解详细信息：如何：创建 WindowsPrincipal 对象
title: 如何：创建 WindowsPrincipal 对象
ms.date: 07/15/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WindowsPrincipal objects, creating
- security [.NET], creating a WindowsPrincipal object
- security [.NET], principals
- principal objects, creating
ms.assetid: 56eb10ca-e61d-4ed2-af7a-555fc4c25a25
ms.openlocfilehash: eee33eb419e8626b8b7f627b9ab1e46ea8dceab5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99685226"
---
# <a name="how-to-create-a-windowsprincipal-object"></a><span data-ttu-id="e2edf-103">如何：创建 WindowsPrincipal 对象</span><span class="sxs-lookup"><span data-stu-id="e2edf-103">How to: Create a WindowsPrincipal Object</span></span>

> [!NOTE]
> <span data-ttu-id="e2edf-104">本文适用于 Windows。</span><span class="sxs-lookup"><span data-stu-id="e2edf-104">This article applies to Windows.</span></span>
>
> <span data-ttu-id="e2edf-105">有关 ASP.NET Core 的信息，请参阅 [ASP.NET Core 安全性](/aspnet/core/security/)。</span><span class="sxs-lookup"><span data-stu-id="e2edf-105">For information about ASP.NET Core, see [ASP.NET Core Security](/aspnet/core/security/).</span></span>

<span data-ttu-id="e2edf-106">有两种方法来创建 <xref:System.Security.Principal.WindowsPrincipal> 对象，具体取决于代码必须重复执行基于角色的验证还是必须只能执行一次。</span><span class="sxs-lookup"><span data-stu-id="e2edf-106">There are two ways to create a <xref:System.Security.Principal.WindowsPrincipal> object, depending on whether code must repeatedly perform role-based validation or must perform it only once.</span></span>  
  
<span data-ttu-id="e2edf-107">如果代码必须重复执行基于角色的验证，则下列过程的第一个将生成更少的开销。</span><span class="sxs-lookup"><span data-stu-id="e2edf-107">If code must repeatedly perform role-based validation, the first of the following procedures produces less overhead.</span></span> <span data-ttu-id="e2edf-108">当代码只需要进行一次基于角色的验证时，你可以使用以下过程的第二个来创建 <xref:System.Security.Principal.WindowsPrincipal> 对象。</span><span class="sxs-lookup"><span data-stu-id="e2edf-108">When code needs to make role-based validations only once, you can create a <xref:System.Security.Principal.WindowsPrincipal> object by using the second of the following procedures.</span></span>  
  
### <a name="to-create-a-windowsprincipal-object-for-repeated-validation"></a><span data-ttu-id="e2edf-109">若要创建 WindowsPrincipal 对象用于重复验证</span><span class="sxs-lookup"><span data-stu-id="e2edf-109">To create a WindowsPrincipal object for repeated validation</span></span>  
  
1. <span data-ttu-id="e2edf-110">在由静态 <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> 属性所返回的 <xref:System.AppDomain> 对象上调用 <xref:System.AppDomain.SetPrincipalPolicy%2A>方法，向此方法传递 <xref:System.Security.Principal.PrincipalPolicy>枚举值，该值指示新策略应该是什么。</span><span class="sxs-lookup"><span data-stu-id="e2edf-110">Call the <xref:System.AppDomain.SetPrincipalPolicy%2A> method on the <xref:System.AppDomain> object that is returned by the static <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> property, passing the method a <xref:System.Security.Principal.PrincipalPolicy> enumeration value that indicates what the new policy should be.</span></span> <span data-ttu-id="e2edf-111">支持的值为 <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>、<xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal> 和 <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>。</span><span class="sxs-lookup"><span data-stu-id="e2edf-111">Supported values are <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>, <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal>, and <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>.</span></span> <span data-ttu-id="e2edf-112">下面的代码演示了此方法调用。</span><span class="sxs-lookup"><span data-stu-id="e2edf-112">The following code demonstrates this method call.</span></span>  
  
    ```csharp  
    AppDomain.CurrentDomain.SetPrincipalPolicy(  
        PrincipalPolicy.WindowsPrincipal);  
    ```  
  
    ```vb  
    AppDomain.CurrentDomain.SetPrincipalPolicy( _  
        PrincipalPolicy.WindowsPrincipal)  
    ```  
  
2. <span data-ttu-id="e2edf-113">通过策略设置，使用静态 <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> 属性来检索封装当前 Windows 用户的主体。</span><span class="sxs-lookup"><span data-stu-id="e2edf-113">With the policy set, use the static <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> property to retrieve the principal that encapsulates the current Windows user.</span></span> <span data-ttu-id="e2edf-114">由于属性返回类型是 <xref:System.Security.Principal.IPrincipal>，因此你必须将结果转换为 <xref:System.Security.Principal.WindowsPrincipal> 类型。</span><span class="sxs-lookup"><span data-stu-id="e2edf-114">Because the property return type is <xref:System.Security.Principal.IPrincipal>, you must cast the result to a <xref:System.Security.Principal.WindowsPrincipal> type.</span></span> <span data-ttu-id="e2edf-115">以下代码将一个新 <xref:System.Security.Principal.WindowsPrincipal> 对象初始化为与当前线程关联的主体的值。</span><span class="sxs-lookup"><span data-stu-id="e2edf-115">The following code initializes a new <xref:System.Security.Principal.WindowsPrincipal> object to the value of the principal associated with the current thread.</span></span>  
  
    ```csharp  
    WindowsPrincipal myPrincipal =
        (WindowsPrincipal) Thread.CurrentPrincipal;  
    ```  
  
    ```vb  
    Dim myPrincipal As WindowsPrincipal = _  
        CType(Thread.CurrentPrincipal, WindowsPrincipal)
    ```  
  
3. <span data-ttu-id="e2edf-116">创建主体对象后，你可以使用若干方法中的一种对其进行验证。</span><span class="sxs-lookup"><span data-stu-id="e2edf-116">When the principal object has been created, you can use one of several methods to validate it.</span></span>  
  
### <a name="to-create-a-windowsprincipal-object-for-a-single-validation"></a><span data-ttu-id="e2edf-117">若要创建 WindowsPrincipal 对象用于单个验证</span><span class="sxs-lookup"><span data-stu-id="e2edf-117">To create a WindowsPrincipal object for a single validation</span></span>  
  
1. <span data-ttu-id="e2edf-118">通过调用静态 <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType> 方法初始化新的 <xref:System.Security.Principal.WindowsIdentity> 对象，该方法查询当前的 Windows 帐户并将有关该帐户的信息放置到新创建的标识对象中。</span><span class="sxs-lookup"><span data-stu-id="e2edf-118">Initialize a new <xref:System.Security.Principal.WindowsIdentity> object by calling the static <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType> method, which queries the current Windows account and places information about that account into the newly created identity object.</span></span> <span data-ttu-id="e2edf-119">下面的代码创建一个新的 <xref:System.Security.Principal.WindowsIdentity> 对象并将其初始化为当前经过身份验证的用户。</span><span class="sxs-lookup"><span data-stu-id="e2edf-119">The following code creates a new <xref:System.Security.Principal.WindowsIdentity> object and initializes it to the current authenticated user.</span></span>  
  
    ```csharp  
    WindowsIdentity myIdentity = WindowsIdentity.GetCurrent();  
    ```  
  
    ```vb  
    Dim myIdentity As WindowsIdentity = WindowsIdentity.GetCurrent()  
    ```  
  
2. <span data-ttu-id="e2edf-120">创建一个新的 <xref:System.Security.Principal.WindowsPrincipal> 对象并向其传递在上一步中创建的 <xref:System.Security.Principal.WindowsIdentity> 对象的值。</span><span class="sxs-lookup"><span data-stu-id="e2edf-120">Create a new <xref:System.Security.Principal.WindowsPrincipal> object and pass it the value of the <xref:System.Security.Principal.WindowsIdentity> object created in the preceding step.</span></span>  
  
    ```csharp  
    WindowsPrincipal myPrincipal = new WindowsPrincipal(myIdentity);  
    ```  
  
    ```vb  
    Dim myPrincipal As New WindowsPrincipal(myIdentity)  
    ```  
  
3. <span data-ttu-id="e2edf-121">创建主体对象后，你可以使用若干方法中的一种对其进行验证。</span><span class="sxs-lookup"><span data-stu-id="e2edf-121">When the principal object has been created, you can use one of several methods to validate it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2edf-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="e2edf-122">See also</span></span>

- [<span data-ttu-id="e2edf-123">主体和标识对象</span><span class="sxs-lookup"><span data-stu-id="e2edf-123">Principal and Identity Objects</span></span>](principal-and-identity-objects.md)
- [<span data-ttu-id="e2edf-124">ASP.NET Core 安全性</span><span class="sxs-lookup"><span data-stu-id="e2edf-124">ASP.NET Core Security</span></span>](/aspnet/core/security/)
