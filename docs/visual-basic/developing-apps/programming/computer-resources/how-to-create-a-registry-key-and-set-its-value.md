---
description: 详细了解：操作说明：在 Visual Basic 中创建注册表项并设置其值
title: 如何：创建注册表项并设置其值
ms.date: 07/20/2015
f1_keywords:
- RegistryKey.CreateSubKey
- RegistryKey.SetValue
helpviewer_keywords:
- registry keys [Visual Basic], creating
- registry [Visual Basic], adding values
- registry [Visual Basic], adding keys
- registry keys [Visual Basic], setting values
- examples [Visual Basic], registry
ms.assetid: d3e40f74-c283-480c-ab18-e5e9052cd814
ms.openlocfilehash: 73a6f5b2a092bb05df704fe6b9954ccbe13b5d90
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797726"
---
# <a name="how-to-create-a-registry-key-and-set-its-value-in-visual-basic"></a><span data-ttu-id="713fa-103">如何：在 Visual Basic 中创建注册表项并设置其值</span><span class="sxs-lookup"><span data-stu-id="713fa-103">How to: Create a Registry Key and Set Its Value in Visual Basic</span></span>

<span data-ttu-id="713fa-104">`My.Computer.Registry` 对象的 `CreateSubKey` 方法可用于创建注册表项。</span><span class="sxs-lookup"><span data-stu-id="713fa-104">The `CreateSubKey` method of the `My.Computer.Registry` object can be used to create a registry key.</span></span>

## <a name="procedure"></a><span data-ttu-id="713fa-105">过程</span><span class="sxs-lookup"><span data-stu-id="713fa-105">Procedure</span></span>

### <a name="to-create-a-registry-key"></a><span data-ttu-id="713fa-106">创建注册表项</span><span class="sxs-lookup"><span data-stu-id="713fa-106">To create a registry key</span></span>

- <span data-ttu-id="713fa-107">使用 `CreateSubKey` 方法，指定放置注册表项的配置单元以及注册表项的名称。</span><span class="sxs-lookup"><span data-stu-id="713fa-107">Use the `CreateSubKey` method, specifying which hive to place the key under as well as the name of the key.</span></span> <span data-ttu-id="713fa-108">参数 `Subkey` 不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="713fa-108">The parameter `Subkey` is not case-sensitive.</span></span> <span data-ttu-id="713fa-109">此示例在 HKEY_CURRENT_USER 下创建注册表项 `MyTestKey`。</span><span class="sxs-lookup"><span data-stu-id="713fa-109">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span></span>

    [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]

### <a name="to-create-a-registry-key-and-set-a-value-in-it"></a><span data-ttu-id="713fa-110">创建注册表项并设置其值</span><span class="sxs-lookup"><span data-stu-id="713fa-110">To create a registry key and set a value in it</span></span>

1. <span data-ttu-id="713fa-111">使用 `CreateSubkey` 方法，指定放置注册表项的配置单元以及注册表项的名称。</span><span class="sxs-lookup"><span data-stu-id="713fa-111">Use the `CreateSubkey` method, specifying which hive to place the key under as well as the name of the key.</span></span> <span data-ttu-id="713fa-112">此示例在 HKEY_CURRENT_USER 下创建注册表项 `MyTestKey`。</span><span class="sxs-lookup"><span data-stu-id="713fa-112">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span></span>

    [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]

2. <span data-ttu-id="713fa-113">使用 `SetValue` 方法设置值。</span><span class="sxs-lookup"><span data-stu-id="713fa-113">Set the value with the `SetValue` method.</span></span> <span data-ttu-id="713fa-114">此示例设置字符串值。</span><span class="sxs-lookup"><span data-stu-id="713fa-114">This example sets the string value.</span></span> <span data-ttu-id="713fa-115">“MyTestKeyValue”设置为“This is a test value”。</span><span class="sxs-lookup"><span data-stu-id="713fa-115">"MyTestKeyValue" to "This is a test value".</span></span>

    [!code-vb[VbResourceTasks#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#14)]

## <a name="example"></a><span data-ttu-id="713fa-116">示例</span><span class="sxs-lookup"><span data-stu-id="713fa-116">Example</span></span>

<span data-ttu-id="713fa-117">此示例在 HKEY_CURRENT_USER 下创建注册表项 `MyTestKey`，然后将字符串值 `MyTestKeyValue` 设置为 `This is a test value`。</span><span class="sxs-lookup"><span data-stu-id="713fa-117">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER and then sets the string value `MyTestKeyValue` to `This is a test value`.</span></span>

[!code-vb[VbResourceTasks#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#15)]

## <a name="robust-programming"></a><span data-ttu-id="713fa-118">可靠编程</span><span class="sxs-lookup"><span data-stu-id="713fa-118">Robust Programming</span></span>

<span data-ttu-id="713fa-119">检查注册表结构，查找适合项的位置。</span><span class="sxs-lookup"><span data-stu-id="713fa-119">Examine the registry structure to find a suitable location for your key.</span></span> <span data-ttu-id="713fa-120">例如，可能需要打开当前用户的 HKEY_CURRENT_USER\Software 项，并用公司的名称创建一项。</span><span class="sxs-lookup"><span data-stu-id="713fa-120">For example, you may want to open the HKEY_CURRENT_USER\Software key of the current user, and create a key with your company's name.</span></span> <span data-ttu-id="713fa-121">然后将注册表值添加到公司的项上。</span><span class="sxs-lookup"><span data-stu-id="713fa-121">Then add the registry values to your company's key.</span></span>

<span data-ttu-id="713fa-122">从 Web 应用程序读取注册表时，当前用户依赖于在 Web 应用程序中实现的身份验证和模拟。</span><span class="sxs-lookup"><span data-stu-id="713fa-122">When reading the registry from a Web application, the current user depends on the authentication and impersonation implemented in the Web application.</span></span>

<span data-ttu-id="713fa-123">将数据写入用户文件夹 (<xref:Microsoft.Win32.Registry.CurrentUser>) 比写入本地计算机 (<xref:Microsoft.Win32.Registry.LocalMachine>) 更安全。</span><span class="sxs-lookup"><span data-stu-id="713fa-123">It is more secure to write data to the user folder (<xref:Microsoft.Win32.Registry.CurrentUser>) rather than to the local computer (<xref:Microsoft.Win32.Registry.LocalMachine>).</span></span>

<span data-ttu-id="713fa-124">创建注册表值时，需要确定该值已存在时应执行的操作。</span><span class="sxs-lookup"><span data-stu-id="713fa-124">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="713fa-125">另一进程（可能是恶意进程）可能已创建了该值，并拥有对该值的访问权。</span><span class="sxs-lookup"><span data-stu-id="713fa-125">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="713fa-126">将数据放入注册表值后，其他进程即可使用这些数据。</span><span class="sxs-lookup"><span data-stu-id="713fa-126">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="713fa-127">若要防止出现这种情况，请使用 <xref:Microsoft.Win32.RegistryKey.GetValue%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="713fa-127">To prevent this, use the <xref:Microsoft.Win32.RegistryKey.GetValue%2A> method.</span></span> <span data-ttu-id="713fa-128">如果项不存在，则该方法返回 `Nothing`。</span><span class="sxs-lookup"><span data-stu-id="713fa-128">It returns `Nothing` if the key does not already exist.</span></span>

<span data-ttu-id="713fa-129">即使注册表项受 ACL（访问控制列表）保护，在注册表中以纯文本形式存储机密信息（例如密码）也不安全。</span><span class="sxs-lookup"><span data-stu-id="713fa-129">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by ACLs (Access Control Lists).</span></span>

<span data-ttu-id="713fa-130">以下情况可能会导致异常：</span><span class="sxs-lookup"><span data-stu-id="713fa-130">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="713fa-131">密钥名称是 `Nothing` (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="713fa-131">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="713fa-132">用户没有创建注册表项的权限 (<xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="713fa-132">The user does not have permissions to create registry keys (<xref:System.Security.SecurityException>).</span></span>

- <span data-ttu-id="713fa-133">项名称超过 255 个字符的限制 (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="713fa-133">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="713fa-134">项已关闭 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="713fa-134">The key is closed (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="713fa-135">注册表项为只读 (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="713fa-135">The registry key is read-only (<xref:System.UnauthorizedAccessException>).</span></span>

## <a name="net-framework-security"></a><span data-ttu-id="713fa-136">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="713fa-136">.NET Framework Security</span></span>

<span data-ttu-id="713fa-137">若要运行此进程，程序集需要 <xref:System.Security.Permissions.RegistryPermission> 类授予的特权等级。</span><span class="sxs-lookup"><span data-stu-id="713fa-137">To run this process, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.RegistryPermission> class.</span></span> <span data-ttu-id="713fa-138">如果在部分信任上下文中运行，该进程可能会因特权不足而引发异常。</span><span class="sxs-lookup"><span data-stu-id="713fa-138">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="713fa-139">同样，用户必须具有用于创建或写入设置的正确 ACL。</span><span class="sxs-lookup"><span data-stu-id="713fa-139">Similarly, the user must have the correct ACLs for creating or writing to settings.</span></span> <span data-ttu-id="713fa-140">例如，具有代码访问安全性权限的本地应用程序可能没有操作系统权限。</span><span class="sxs-lookup"><span data-stu-id="713fa-140">For example, a local application that has the code access security permission might not have operating system permission.</span></span> <span data-ttu-id="713fa-141">有关详细信息，请参阅 [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md)。</span><span class="sxs-lookup"><span data-stu-id="713fa-141">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="713fa-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="713fa-142">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy.CurrentUser%2A>
- <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A>
- [<span data-ttu-id="713fa-143">读取和写入注册表</span><span class="sxs-lookup"><span data-stu-id="713fa-143">Reading from and Writing to the Registry</span></span>](reading-from-and-writing-to-the-registry.md)
- [<span data-ttu-id="713fa-144">代码访问安全性基础知识</span><span class="sxs-lookup"><span data-stu-id="713fa-144">Code Access Security Basics</span></span>](../../../../framework/misc/code-access-security-basics.md)
