---
description: 了解详细信息：如何：访问硬件加密设备
title: 如何：访问硬件加密设备
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- encryption
- key card
- cryptography
- hardware encryption
- CspParameters
ms.assetid: b0e734df-6eb4-4b16-b48c-6f0fe82d5f17
ms.openlocfilehash: fcf12314490542848d20bd3a4977d68c386853bb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99685265"
---
# <a name="how-to-access-hardware-encryption-devices"></a><span data-ttu-id="4b96b-103">如何：访问硬件加密设备</span><span class="sxs-lookup"><span data-stu-id="4b96b-103">How to: Access Hardware Encryption Devices</span></span>

> [!NOTE]
> <span data-ttu-id="4b96b-104">本文适用于 Windows。</span><span class="sxs-lookup"><span data-stu-id="4b96b-104">This article applies to Windows.</span></span>

<span data-ttu-id="4b96b-105">可使用 <xref:System.Security.Cryptography.CspParameters> 类来访问硬件加密设备。</span><span class="sxs-lookup"><span data-stu-id="4b96b-105">You can use the <xref:System.Security.Cryptography.CspParameters> class to access hardware encryption devices.</span></span> <span data-ttu-id="4b96b-106">例如，可以使用此类将你的应用程序与智能卡、硬件随机数字生成器或特定加密算法的硬件实现进行集成。</span><span class="sxs-lookup"><span data-stu-id="4b96b-106">For example, you can use this class to integrate your application with a smart card, a hardware random number generator, or a hardware implementation of a particular cryptographic algorithm.</span></span>  

<span data-ttu-id="4b96b-107"><xref:System.Security.Cryptography.CspParameters> 类会创建一个加密服务提供程序 (CSP)，该程序可访问正确安装的硬件加密设备。</span><span class="sxs-lookup"><span data-stu-id="4b96b-107">The <xref:System.Security.Cryptography.CspParameters> class creates a cryptographic service provider (CSP) that accesses a properly installed hardware encryption device.</span></span>  <span data-ttu-id="4b96b-108">你可以通过使用注册表编辑器 (Regedit.exe) 检查下列注册表项来验证 CSP 的可用性：HKEY_LOCAL_MACHINE\Software\Microsoft\Cryptography\Defaults\Provider。</span><span class="sxs-lookup"><span data-stu-id="4b96b-108">You can verify the availability of a CSP by inspecting the following registry key using the Registry Editor (Regedit.exe):  HKEY_LOCAL_MACHINE\Software\Microsoft\Cryptography\Defaults\Provider.</span></span>  
  
### <a name="to-sign-data-using-a-key-card"></a><span data-ttu-id="4b96b-109">使用密钥卡对数据进行签名</span><span class="sxs-lookup"><span data-stu-id="4b96b-109">To sign data using a key card</span></span>  
  
1. <span data-ttu-id="4b96b-110">通过将整数提供程序类型和提供程序名称传递给构造函数，创建 <xref:System.Security.Cryptography.CspParameters> 类的新实例。</span><span class="sxs-lookup"><span data-stu-id="4b96b-110">Create a new instance of the <xref:System.Security.Cryptography.CspParameters> class, passing the integer provider type and the provider name to the constructor.</span></span>  
  
2. <span data-ttu-id="4b96b-111">将适当的标志传递给新创建的 <xref:System.Security.Cryptography.CspParameters> 对象的 <xref:System.Security.Cryptography.CspParameters.Flags%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="4b96b-111">Pass the appropriate flags to the <xref:System.Security.Cryptography.CspParameters.Flags%2A> property of the newly created <xref:System.Security.Cryptography.CspParameters> object.</span></span>  <span data-ttu-id="4b96b-112">例如，传递 <xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer> 标志。</span><span class="sxs-lookup"><span data-stu-id="4b96b-112">For example, pass the <xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer> flag.</span></span>  
  
3. <span data-ttu-id="4b96b-113">通过将 <xref:System.Security.Cryptography.CspParameters> 对象传递给构造函数，创建 <xref:System.Security.Cryptography.AsymmetricAlgorithm> 类（如 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 类）的新实例。</span><span class="sxs-lookup"><span data-stu-id="4b96b-113">Create a new instance of an <xref:System.Security.Cryptography.AsymmetricAlgorithm> class (for example, the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class), passing the <xref:System.Security.Cryptography.CspParameters> object to the constructor.</span></span>  
  
4. <span data-ttu-id="4b96b-114">使用其中一种 `Sign` 方法对你的数据进行签名，并使用其中一种 `Verify` 方法来验证你的数据。</span><span class="sxs-lookup"><span data-stu-id="4b96b-114">Sign your data using one of the `Sign` methods and verify your data using one of the `Verify` methods.</span></span>  
  
### <a name="to-generate-a-random-number-using-a-hardware-random-number-generator"></a><span data-ttu-id="4b96b-115">使用硬件随机数字生成器生成随机数</span><span class="sxs-lookup"><span data-stu-id="4b96b-115">To generate a random number using a hardware random number generator</span></span>  
  
1. <span data-ttu-id="4b96b-116">通过将整数提供程序类型和提供程序名称传递给构造函数，创建 <xref:System.Security.Cryptography.CspParameters> 类的新实例。</span><span class="sxs-lookup"><span data-stu-id="4b96b-116">Create a new instance of the <xref:System.Security.Cryptography.CspParameters> class, passing the integer provider type and the provider name to the constructor.</span></span>  
  
2. <span data-ttu-id="4b96b-117">通过将 <xref:System.Security.Cryptography.CspParameters> 对象传递给构造函数，创建 <xref:System.Security.Cryptography.RNGCryptoServiceProvider> 的新实例。</span><span class="sxs-lookup"><span data-stu-id="4b96b-117">Create a new instance of the <xref:System.Security.Cryptography.RNGCryptoServiceProvider>, passing the <xref:System.Security.Cryptography.CspParameters> object to the constructor.</span></span>  
  
3. <span data-ttu-id="4b96b-118">使用 <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> 或 <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A> 方法创建一个随机值。</span><span class="sxs-lookup"><span data-stu-id="4b96b-118">Create a random value using the <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> or <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b96b-119">示例</span><span class="sxs-lookup"><span data-stu-id="4b96b-119">Example</span></span>

<span data-ttu-id="4b96b-120">下列代码示例演示如何使用智能卡对数据进行签名。</span><span class="sxs-lookup"><span data-stu-id="4b96b-120">The following code example demonstrates how to sign data using a smart card.</span></span>  <span data-ttu-id="4b96b-121">此代码示例创建一个公开智能卡的 <xref:System.Security.Cryptography.CspParameters> 对象，然后使用 CSP 初始化 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 对象。</span><span class="sxs-lookup"><span data-stu-id="4b96b-121">The code example creates a <xref:System.Security.Cryptography.CspParameters> object that exposes a smart card, and then initializes an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object using the CSP.</span></span>  <span data-ttu-id="4b96b-122">然后此代码示例会对某些数据进行签名和验证。</span><span class="sxs-lookup"><span data-stu-id="4b96b-122">The code example then signs and verifies some data.</span></span>  

<span data-ttu-id="4b96b-123">由于 SHA1 出现冲突，我们建议 SHA256 或更好。</span><span class="sxs-lookup"><span data-stu-id="4b96b-123">Due to collision problems with SHA1, we recommend SHA256 or better.</span></span>
  
[!code-cpp[Cryptography.SmartCardCSP#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CPP/Cryptography.SmartCardCSP.cpp#1)]
[!code-csharp[Cryptography.SmartCardCSP#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CS/example.cs#1)]
[!code-vb[Cryptography.SmartCardCSP#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Cryptography.SmartCardCSP/VB/example.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4b96b-124">编译代码</span><span class="sxs-lookup"><span data-stu-id="4b96b-124">Compiling the Code</span></span>  
  
- <span data-ttu-id="4b96b-125">包括 <xref:System> 和 <xref:System.Security.Cryptography> 命名空间。</span><span class="sxs-lookup"><span data-stu-id="4b96b-125">Include the <xref:System> and <xref:System.Security.Cryptography> namespaces.</span></span>  
  
- <span data-ttu-id="4b96b-126">计算机上必须安装有智能卡读卡器和驱动程序。</span><span class="sxs-lookup"><span data-stu-id="4b96b-126">You must have a smart card reader and drivers installed on your computer.</span></span>  
  
- <span data-ttu-id="4b96b-127">必须使用特定于读卡器的信息来初始化 <xref:System.Security.Cryptography.CspParameters> 对象。</span><span class="sxs-lookup"><span data-stu-id="4b96b-127">You must initialize the <xref:System.Security.Cryptography.CspParameters> object using information specific to your card reader.</span></span>  <span data-ttu-id="4b96b-128">有关详细信息，请参阅读卡器的文档。</span><span class="sxs-lookup"><span data-stu-id="4b96b-128">For more information, see the documentation of your card reader.</span></span>

## <a name="see-also"></a><span data-ttu-id="4b96b-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="4b96b-129">See also</span></span>

- [<span data-ttu-id="4b96b-130">加密模型</span><span class="sxs-lookup"><span data-stu-id="4b96b-130">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="4b96b-131">加密服务</span><span class="sxs-lookup"><span data-stu-id="4b96b-131">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="4b96b-132">跨平台加密</span><span class="sxs-lookup"><span data-stu-id="4b96b-132">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="4b96b-133">ASP.NET Core 数据保护</span><span class="sxs-lookup"><span data-stu-id="4b96b-133">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
