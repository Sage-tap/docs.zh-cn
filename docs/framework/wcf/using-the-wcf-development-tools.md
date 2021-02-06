---
description: 了解详细信息：使用 WCF 开发工具
title: 使用 WCF 开发工具
ms.date: 03/30/2017
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
ms.openlocfilehash: c96644fb66006447f6a05f6c08ea84fe2ed99ce8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631692"
---
# <a name="using-the-wcf-development-tools"></a><span data-ttu-id="09ee4-103">使用 WCF 开发工具</span><span class="sxs-lookup"><span data-stu-id="09ee4-103">Using the WCF Development Tools</span></span>

<span data-ttu-id="09ee4-104">本部分介绍可帮助你开发 WCFservice 的 Visual Studio 开发工具。</span><span class="sxs-lookup"><span data-stu-id="09ee4-104">This section describes the Visual Studio development tools that can assist you in developing your WCFservice.</span></span>  
  
 <span data-ttu-id="09ee4-105">您可以使用 Visual Studio 模板作为基础来快速生成自己的服务，然后使用 WCF 服务自动主机和 WCF 测试客户端来调试和测试您的服务。</span><span class="sxs-lookup"><span data-stu-id="09ee4-105">You can use the Visual Studio templates as a foundation to quickly build your own service, then use WCF Service Auto Host and WCF Test Client to debug and test your service.</span></span> <span data-ttu-id="09ee4-106">通过一起使用这些工具，可以快速完美地完成调试和测试过程，无需在早期阶段提交给承载模型。</span><span class="sxs-lookup"><span data-stu-id="09ee4-106">These tools together provide a fast and seamless debug and testing cycle, and preclude the need to commit to a hosting model at an early stage.</span></span>  

 > [!NOTE]
 > <span data-ttu-id="09ee4-107">从 Visual Studio 2017 开始，默认情况下不安装 WCF 开发工具。</span><span class="sxs-lookup"><span data-stu-id="09ee4-107">Starting with Visual Studio 2017, the WCF development tools are not installed by default.</span></span> <span data-ttu-id="09ee4-108">若要使用这些功能，必须确保在 Visual Studio 安装程序中选择 Windows Communication Foundation 组件。</span><span class="sxs-lookup"><span data-stu-id="09ee4-108">In order to use these features, you must ensure the Windows Communication Foundation component is selected in the Visual Studio installer.</span></span>
  
## <a name="the-wcf-developer-tools"></a><span data-ttu-id="09ee4-109">WCF 开发人员工具</span><span class="sxs-lookup"><span data-stu-id="09ee4-109">The WCF Developer Tools</span></span>  

 [<span data-ttu-id="09ee4-110">WCF Visual Studio 模板</span><span class="sxs-lookup"><span data-stu-id="09ee4-110">WCF Visual Studio Templates</span></span>](wcf-vs-templates.md)  
  
 <span data-ttu-id="09ee4-111">你可以使用 Visual Studio 中预定义的 Visual Studio 项目和项模板快速生成 WCF 服务和应用程序。</span><span class="sxs-lookup"><span data-stu-id="09ee4-111">You can use the predefined Visual Studio project and item templates in Visual Studio to quickly build WCF services and surrounding applications.</span></span>  
  
 [<span data-ttu-id="09ee4-112">WCF 服务主机 (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="09ee4-112">WCF Service Host (WcfSvcHost.exe)</span></span>](wcf-service-host-wcfsvchost-exe.md)  
  
 <span data-ttu-id="09ee4-113">WCF 服务自动主机 ( # A0) 使你可以启动 Visual Studio 调试器 (F5) 来自动承载和测试已实现的服务。</span><span class="sxs-lookup"><span data-stu-id="09ee4-113">The WCF Service Auto Host (WcfSvcHost.exe) allows you to launch the Visual Studio debugger (F5) to automatically host and test a service you have implemented.</span></span> <span data-ttu-id="09ee4-114">然后，你可以使用 WCF 测试客户端 ( # A0) 或你自己的客户端来测试服务，以查找并解决任何潜在错误。</span><span class="sxs-lookup"><span data-stu-id="09ee4-114">You can then test the service using the WCF Test Client (wcfTestClient.exe) or your own client to find and fix any potential errors.</span></span>  
  
 [<span data-ttu-id="09ee4-115">WCF 测试客户端 (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="09ee4-115">WCF Test Client (WcfTestClient.exe)</span></span>](wcf-test-client-wcftestclient-exe.md)  
  
 <span data-ttu-id="09ee4-116">WCF 测试客户端 ( # A0) 是一个 GUI 工具，它允许输入任意类型的参数、将该输入提交给服务并查看服务发回的响应。</span><span class="sxs-lookup"><span data-stu-id="09ee4-116">WCF Test Client (WcfTestClient.exe) is a GUI tool that allows you to input parameters of arbitrary types, submit that input to the service, and view the response the service sends back.</span></span> <span data-ttu-id="09ee4-117">与 WCF 服务自动主机结合使用时，可以提供无缝的服务测试体验。</span><span class="sxs-lookup"><span data-stu-id="09ee4-117">It provides a seamless service testing experience when combined with WCF Service Auto Host.</span></span>  
  
 [<span data-ttu-id="09ee4-118">从 XML 生成数据类型类</span><span class="sxs-lookup"><span data-stu-id="09ee4-118">Generating Data Type Classes from XML</span></span>](generating-data-type-classes-from-xml.md)  
  
 <span data-ttu-id="09ee4-119">可将存储在剪贴板中的 XML 数据粘贴到代码页中。</span><span class="sxs-lookup"><span data-stu-id="09ee4-119">XML data stored in the clipboard can be pasted into a code page.</span></span> <span data-ttu-id="09ee4-120">数据中定义的类将被转换为代码类型。</span><span class="sxs-lookup"><span data-stu-id="09ee4-120">The classes defined in the data will be converted to code types.</span></span>  
  
## <a name="using-the-tools-without-administrator-privilege"></a><span data-ttu-id="09ee4-121">在无管理员权限的情况下使用工具</span><span class="sxs-lookup"><span data-stu-id="09ee4-121">Using the Tools without Administrator privilege</span></span>  

 <span data-ttu-id="09ee4-122">为了使无管理员权限的用户能够开发 WCF 服务，在 http://+:8731/Design_Time_Addresses 安装 Visual Studio 的过程中，将为命名空间 "" 创建一个 ACL (访问控制列表) 。</span><span class="sxs-lookup"><span data-stu-id="09ee4-122">To enable users without administrator privilege to develop WCF services, an ACL (Access Control List) is created for the namespace "http://+:8731/Design_Time_Addresses" during the installation of Visual Studio.</span></span> <span data-ttu-id="09ee4-123">该 ACL 被设置为“(UI)”，这将包括登录到此计算机的所有交互用户。</span><span class="sxs-lookup"><span data-stu-id="09ee4-123">The ACL is set to (UI), which includes all interactive users logged on to the machine.</span></span> <span data-ttu-id="09ee4-124">管理员可以在此 ACL 中添加或移除用户，或者打开其他端口。此 ACL 支持 WCF 或 WF 模板以其各自的默认配置发送和接收数据。</span><span class="sxs-lookup"><span data-stu-id="09ee4-124">Administrators can add or remove users from this ACL, or open additional ports.This ACL enables WCF or WF templates to send and receive data in their default configuration.</span></span> <span data-ttu-id="09ee4-125">它还使用户可以使用 WCF 服务自动主机 ( # A0) ，而无需授予其管理员权限。</span><span class="sxs-lookup"><span data-stu-id="09ee4-125">It also enables users to use the WCF Service Auto Host (wcfSvcHost.exe) without granting them administrator privileges.</span></span>  
  
 <span data-ttu-id="09ee4-126">你可以使用提升的管理员帐户在 Windows Vista 中使用 Netsh.exe 工具来修改访问权限。</span><span class="sxs-lookup"><span data-stu-id="09ee4-126">You can modify access using the Netsh.exe tool in Windows Vista under the elevated administrator account.</span></span> <span data-ttu-id="09ee4-127">下面是使用 Netsh.exe 的示例。</span><span class="sxs-lookup"><span data-stu-id="09ee4-127">The following is an example of using Netsh.exe.</span></span>  
  
```console  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 <span data-ttu-id="09ee4-128">有关 Netsh.exe 的详细信息，请参阅 [如何使用 Netsh.exe 工具和 Command-Line 开关](/previous-versions/tn-archive/bb490939(v=technet.10))。</span><span class="sxs-lookup"><span data-stu-id="09ee4-128">For more information about Netsh.exe, see [How to Use the Netsh.exe Tool and Command-Line Switches](/previous-versions/tn-archive/bb490939(v=technet.10)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09ee4-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="09ee4-129">See also</span></span>

- [<span data-ttu-id="09ee4-130">WCF Visual Studio 模板</span><span class="sxs-lookup"><span data-stu-id="09ee4-130">WCF Visual Studio Templates</span></span>](wcf-vs-templates.md)
- [<span data-ttu-id="09ee4-131">WCF 服务主机 (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="09ee4-131">WCF Service Host (WcfSvcHost.exe)</span></span>](wcf-service-host-wcfsvchost-exe.md)
- [<span data-ttu-id="09ee4-132">WCF 测试客户端 (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="09ee4-132">WCF Test Client (WcfTestClient.exe)</span></span>](wcf-test-client-wcftestclient-exe.md)
