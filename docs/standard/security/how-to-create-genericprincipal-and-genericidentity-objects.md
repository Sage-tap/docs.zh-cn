---
description: 了解详细信息：如何：创建 GenericPrincipal 和 GenericIdentity 对象
title: 如何：创建 GenericPrincipal 和 GenericIdentity 对象
ms.date: 07/15/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Creating Generic Identity Objects
- GenericPrincipal Objects
- Creating GenericPrincipal Objects
- GenericIdentity Objects
ms.assetid: 465694cf-258b-4747-9dae-35b01a5bcdbb
ms.openlocfilehash: 8c77a9afec7bd166a71abb6af19d8766b02d0523
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99685213"
---
# <a name="how-to-create-genericprincipal-and-genericidentity-objects"></a><span data-ttu-id="19451-103">如何：创建 GenericPrincipal 和 GenericIdentity 对象</span><span class="sxs-lookup"><span data-stu-id="19451-103">How to: Create GenericPrincipal and GenericIdentity Objects</span></span>

> [!NOTE]
> <span data-ttu-id="19451-104">本文适用于 Windows。</span><span class="sxs-lookup"><span data-stu-id="19451-104">This article applies to Windows.</span></span>
>
> <span data-ttu-id="19451-105">有关 ASP.NET Core 的信息，请参阅 [ASP.NET Core 安全性概述](/aspnet/core/security/)。</span><span class="sxs-lookup"><span data-stu-id="19451-105">For information about ASP.NET Core, see [Overview of ASP.NET Core Security](/aspnet/core/security/).</span></span>

<span data-ttu-id="19451-106">你可以将 <xref:System.Security.Principal.GenericIdentity> 类与类结合使用 <xref:System.Security.Principal.GenericPrincipal> ，以创建独立于 Windows 域的授权方案。</span><span class="sxs-lookup"><span data-stu-id="19451-106">You can use the <xref:System.Security.Principal.GenericIdentity> class in conjunction with the <xref:System.Security.Principal.GenericPrincipal> class to create an authorization scheme that exists independent of a Windows domain.</span></span>

### <a name="to-create-a-genericprincipal-object"></a><span data-ttu-id="19451-107">创建 GenericPrincipal 对象</span><span class="sxs-lookup"><span data-stu-id="19451-107">To create a GenericPrincipal object</span></span>

1. <span data-ttu-id="19451-108">创建标识类的一个新实例，并用希望它持有的名称对其进行初始化。</span><span class="sxs-lookup"><span data-stu-id="19451-108">Create a new instance of the identity class and initialize it with the name you want it to hold.</span></span> <span data-ttu-id="19451-109">以下代码创建一个新的 **GenericIdentity** 对象，并用名称 `MyUser` 对其进行初始化。</span><span class="sxs-lookup"><span data-stu-id="19451-109">The following code creates a new **GenericIdentity** object and initializes it with the name `MyUser`.</span></span>

    ```vb
    Dim myIdentity As New GenericIdentity("MyUser")
    ```

    ```csharp
    GenericIdentity myIdentity = new GenericIdentity("MyUser");
    ```

2. <span data-ttu-id="19451-110">创建 **GenericPrincipal** 类的一个新实例，并用先前创建的 **GenericIdentity** 对象和表示希望与此主体关联的角色的字符串数组对其进行初始化。</span><span class="sxs-lookup"><span data-stu-id="19451-110">Create a new instance of the **GenericPrincipal** class and initialize it with the previously created **GenericIdentity** object and an array of strings that represent the roles that you want associated with this principal.</span></span> <span data-ttu-id="19451-111">下面的代码示例指定表示一个管理员角色和一个用户角色的字符串数组。</span><span class="sxs-lookup"><span data-stu-id="19451-111">The following code example specifies an array of strings that represent an administrator role and a user role.</span></span> <span data-ttu-id="19451-112">然后用前面的 **GenericIdentity** 和该字符串数组对 **GenericPrincipal** 进行初始化。</span><span class="sxs-lookup"><span data-stu-id="19451-112">The **GenericPrincipal** is then initialized with the previous **GenericIdentity** and the string array.</span></span>

    ```vb
    Dim myStringArray As String() = {"Manager", "Teller"}
    DIm myPrincipal As New GenericPrincipal(myIdentity, myStringArray)
    ```

    ```csharp
    String[] myStringArray = {"Manager", "Teller"};
    GenericPrincipal myPrincipal = new GenericPrincipal(myIdentity, myStringArray);
    ```

3. <span data-ttu-id="19451-113">使用以下代码将主体附加到当前线程中。</span><span class="sxs-lookup"><span data-stu-id="19451-113">Use the following code to attach the principal to the current thread.</span></span> <span data-ttu-id="19451-114">这在以下情况下很有用：必须多次验证主体，必须由应用程序中运行的其他代码验证，或者必须由 <xref:System.Security.Permissions.PrincipalPermission> 对象验证。</span><span class="sxs-lookup"><span data-stu-id="19451-114">This is valuable in situations where the principal must be validated several times, it must be validated by other code running in your application, or it must be validated by a <xref:System.Security.Permissions.PrincipalPermission> object.</span></span> <span data-ttu-id="19451-115">不将主体附加到线程中，仍可对主体对象执行基于角色的验证。</span><span class="sxs-lookup"><span data-stu-id="19451-115">You can still perform role-based validation on the principal object without attaching it to the thread.</span></span> <span data-ttu-id="19451-116">有关详细信息，请参阅[替换主体对象](replacing-a-principal-object.md)。</span><span class="sxs-lookup"><span data-stu-id="19451-116">For more information, see [Replacing a Principal Object](replacing-a-principal-object.md).</span></span>

    ```vb
    Thread.CurrentPrincipal = myPrincipal
    ```

    ```csharp
    Thread.CurrentPrincipal = myPrincipal;
    ```

## <a name="example"></a><span data-ttu-id="19451-117">示例</span><span class="sxs-lookup"><span data-stu-id="19451-117">Example</span></span>

<span data-ttu-id="19451-118">下面的代码示例说明如何创建 **GenericPrincipal** 和 **GenericIdentity** 的实例。</span><span class="sxs-lookup"><span data-stu-id="19451-118">The following code example demonstrates how to create an instance of a **GenericPrincipal** and a **GenericIdentity**.</span></span> <span data-ttu-id="19451-119">此代码将这些对象的值显示到控制台中。</span><span class="sxs-lookup"><span data-stu-id="19451-119">This code displays the values of these objects to the console.</span></span>

```vb
Imports System.Security.Principal
Imports System.Threading

Public Class Class1

    Public Shared Sub Main()
        ' Create generic identity.
        Dim myIdentity As New GenericIdentity("MyIdentity")

        ' Create generic principal.
        Dim myStringArray As String() =  {"Manager", "Teller"}
        Dim myPrincipal As New GenericPrincipal(myIdentity, myStringArray)

        ' Attach the principal to the current thread.
        ' This is not required unless repeated validation must occur,
        ' other code in your application must validate, or the
        ' PrincipalPermission object is used.
        Thread.CurrentPrincipal = myPrincipal

        ' Print values to the console.
        Dim name As String = myPrincipal.Identity.Name
        Dim auth As Boolean = myPrincipal.Identity.IsAuthenticated
        Dim isInRole As Boolean = myPrincipal.IsInRole("Manager")

        Console.WriteLine("The name is: {0}", name)
        Console.WriteLine("The isAuthenticated is: {0}", auth)
        Console.WriteLine("Is this a Manager? {0}", isInRole)

    End Sub

End Class
```

```csharp
using System;
using System.Security.Principal;
using System.Threading;

public class Class1
{
    public static int Main(string[] args)
    {
    // Create generic identity.
    GenericIdentity myIdentity = new GenericIdentity("MyIdentity");

    // Create generic principal.
    String[] myStringArray = {"Manager", "Teller"};
    GenericPrincipal myPrincipal =
        new GenericPrincipal(myIdentity, myStringArray);

    // Attach the principal to the current thread.
    // This is not required unless repeated validation must occur,
    // other code in your application must validate, or the
    // PrincipalPermission object is used.
    Thread.CurrentPrincipal = myPrincipal;

    // Print values to the console.
    String name =  myPrincipal.Identity.Name;
    bool auth =  myPrincipal.Identity.IsAuthenticated;
    bool isInRole =  myPrincipal.IsInRole("Manager");

    Console.WriteLine("The name is: {0}", name);
    Console.WriteLine("The isAuthenticated is: {0}", auth);
    Console.WriteLine("Is this a Manager? {0}", isInRole);

    return 0;
    }
}
```

<span data-ttu-id="19451-120">执行时，应用程序显示类似于下面这样的输出。</span><span class="sxs-lookup"><span data-stu-id="19451-120">When executed, the application displays output similar to the following.</span></span>

```console
The Name is: MyIdentity
The IsAuthenticated is: True
Is this a Manager? True
```

## <a name="see-also"></a><span data-ttu-id="19451-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="19451-121">See also</span></span>

- <xref:System.Security.Principal.GenericIdentity>
- <xref:System.Security.Principal.GenericPrincipal>
- <xref:System.Security.Permissions.PrincipalPermission>
- [<span data-ttu-id="19451-122">替换 Principal 对象</span><span class="sxs-lookup"><span data-stu-id="19451-122">Replacing a Principal Object</span></span>](replacing-a-principal-object.md)
- [<span data-ttu-id="19451-123">主体和标识对象</span><span class="sxs-lookup"><span data-stu-id="19451-123">Principal and Identity Objects</span></span>](principal-and-identity-objects.md)
