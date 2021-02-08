---
description: 了解详细信息： WCF 安全中的加密灵活性
title: WCF 安全中的加密灵活性
ms.date: 03/30/2017
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
ms.openlocfilehash: ab46034b16a846f7399220480fc928655d931be0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778342"
---
# <a name="cryptographic-agility-in-wcf-security"></a><span data-ttu-id="d4f44-103">WCF 安全中的加密灵活性</span><span class="sxs-lookup"><span data-stu-id="d4f44-103">Cryptographic agility in WCF security</span></span>

<span data-ttu-id="d4f44-104">此示例演示如何在标准/自定义算法中指定，以在 Windows Communication Foundation (WCF) 客户端和服务中提供加密敏捷实现。</span><span class="sxs-lookup"><span data-stu-id="d4f44-104">This sample shows how to specify in a standard/custom algorithm to provide a cryptographic agile implementation in a Windows Communication Foundation (WCF) client and service.</span></span> <span data-ttu-id="d4f44-105">该示例由下列项目组成：</span><span class="sxs-lookup"><span data-stu-id="d4f44-105">The sample is composed of the following projects:</span></span>

<span data-ttu-id="d4f44-106">**服务**</span><span class="sxs-lookup"><span data-stu-id="d4f44-106">**Service**</span></span>

<span data-ttu-id="d4f44-107">这是一个自承载的 WCF 服务，它可实现 `ICalculator` 接口，并使用启用了 <xref:System.ServiceModel.WSHttpBinding> 安全会话和可靠会话来保护终结点。</span><span class="sxs-lookup"><span data-stu-id="d4f44-107">This is a self-hosted WCF service that implements the `ICalculator` interface and secures the endpoint using the <xref:System.ServiceModel.WSHttpBinding> with secure session and reliable session disabled.</span></span> <span data-ttu-id="d4f44-108">该服务定义一个自定义 `SecurityAlgorithmSuite` 类，以指定要用于消息安全的加密算法。</span><span class="sxs-lookup"><span data-stu-id="d4f44-108">The service defines a custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>

<span data-ttu-id="d4f44-109">**客户端**</span><span class="sxs-lookup"><span data-stu-id="d4f44-109">**Client**</span></span>

<span data-ttu-id="d4f44-110">这是在身份验证成功后访问服务的 WCF 客户端。</span><span class="sxs-lookup"><span data-stu-id="d4f44-110">This is a WCF client that accesses the service after successful authentication.</span></span> <span data-ttu-id="d4f44-111">该客户端调用由 `ICalculator` 接口公开并由服务实现的操作。</span><span class="sxs-lookup"><span data-stu-id="d4f44-111">It invokes the operations exposed by the `ICalculator` interface and implemented by the service.</span></span> <span data-ttu-id="d4f44-112">该客户端也定义相同的自定义 `SecurityAlgorithmSuite` 类，以指定要用于消息安全的加密算法。</span><span class="sxs-lookup"><span data-stu-id="d4f44-112">The client also defines the same custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>

## <a name="to-use-this-sample"></a><span data-ttu-id="d4f44-113">使用此示例</span><span class="sxs-lookup"><span data-stu-id="d4f44-113">To use this sample</span></span>

1. <span data-ttu-id="d4f44-114">在 Visual Studio 2012 中打开 CryptoAgility 解决方案。</span><span class="sxs-lookup"><span data-stu-id="d4f44-114">Open the CryptoAgility.sln solution in Visual Studio 2012.</span></span>

2. <span data-ttu-id="d4f44-115">按 CTRL+SHIFT+B 生成解决方案。</span><span class="sxs-lookup"><span data-stu-id="d4f44-115">Press CTRL+SHIFT+B to build the solution.</span></span>

3. <span data-ttu-id="d4f44-116">打开文件资源管理器并导航到 \WCF\Basic\Security\CryptoAgility\Service\bin 目录，并通过右键单击 service.exe 并选择 "以 **管理员身份运行**"，以管理员权限运行 service.exe 文件。</span><span class="sxs-lookup"><span data-stu-id="d4f44-116">Open File Explorer and navigate to the \WCF\Basic\Security\CryptoAgility\Service\bin directory and run the service.exe file with administrator privileges by right-clicking service.exe and selecting **Run as administrator**.</span></span>

4. <span data-ttu-id="d4f44-117">导航到 \WCF\Basic\Security\CryptoAgility\Client\bin 目录并正常运行 client.exe 文件。</span><span class="sxs-lookup"><span data-stu-id="d4f44-117">Navigate to \WCF\Basic\Security\CryptoAgility\Client\bin directory and run the client.exe file normally.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d4f44-118">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="d4f44-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d4f44-119">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="d4f44-119">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="d4f44-120">如果此目录不存在，请参阅[Windows Communication Foundation (wcf) ，并 Windows Workflow Foundation (的 WF](https://www.microsoft.com/download/details.aspx?id=21459)) .NET Framework Windows Communication Foundation ([!INCLUDE[wf1](../../../../includes/wf1-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4f44-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d4f44-121">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="d4f44-121">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`

## <a name="see-also"></a><span data-ttu-id="d4f44-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="d4f44-122">See also</span></span>

- [<span data-ttu-id="d4f44-123">Windows Communication Foundation 安全性</span><span class="sxs-lookup"><span data-stu-id="d4f44-123">Windows Communication Foundation Security</span></span>](../feature-details/security.md)
