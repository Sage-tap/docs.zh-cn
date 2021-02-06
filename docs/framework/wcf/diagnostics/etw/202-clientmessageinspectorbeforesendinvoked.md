---
description: 了解详细信息： 202-ClientMessageInspectorBeforeSendInvoked
title: 202 - ClientMessageInspectorBeforeSendInvoked
ms.date: 03/30/2017
ms.assetid: 0b02ca82-8a55-45e3-b2e2-ddfe28a7269c
ms.openlocfilehash: 0267304ba805c8f23109c820c8516a27958c3040
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99645043"
---
# <a name="202---clientmessageinspectorbeforesendinvoked"></a><span data-ttu-id="26d31-103">202 - ClientMessageInspectorBeforeSendInvoked</span><span class="sxs-lookup"><span data-stu-id="26d31-103">202 - ClientMessageInspectorBeforeSendInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="26d31-104">属性</span><span class="sxs-lookup"><span data-stu-id="26d31-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="26d31-105">ID</span><span class="sxs-lookup"><span data-stu-id="26d31-105">ID</span></span>|<span data-ttu-id="26d31-106">202</span><span class="sxs-lookup"><span data-stu-id="26d31-106">202</span></span>|  
|<span data-ttu-id="26d31-107">关键字</span><span class="sxs-lookup"><span data-stu-id="26d31-107">Keywords</span></span>|<span data-ttu-id="26d31-108">疑难解答，ServiceModel</span><span class="sxs-lookup"><span data-stu-id="26d31-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="26d31-109">级别</span><span class="sxs-lookup"><span data-stu-id="26d31-109">Level</span></span>|<span data-ttu-id="26d31-110">信息</span><span class="sxs-lookup"><span data-stu-id="26d31-110">Information</span></span>|  
|<span data-ttu-id="26d31-111">通道</span><span class="sxs-lookup"><span data-stu-id="26d31-111">Channel</span></span>|<span data-ttu-id="26d31-112">Microsoft-Windows-应用程序服务器-应用程序/分析</span><span class="sxs-lookup"><span data-stu-id="26d31-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="26d31-113">说明</span><span class="sxs-lookup"><span data-stu-id="26d31-113">Description</span></span>  

 <span data-ttu-id="26d31-114">服务模型在客户端消息检查器上调用 `BeforeSendRequest` 方法之后，将发出此事件。</span><span class="sxs-lookup"><span data-stu-id="26d31-114">This event is emitted after the Service Model has invoked the `BeforeSendRequest` method on a client message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="26d31-115">消息</span><span class="sxs-lookup"><span data-stu-id="26d31-115">Message</span></span>  

 <span data-ttu-id="26d31-116">调度程序对“%1”类型的 ClientMessageInspector 调用了“BeforeSendRequest”。</span><span class="sxs-lookup"><span data-stu-id="26d31-116">The Dispatcher invoked 'BeforeSendRequest' on a ClientMessageInspector of type  '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="26d31-117">详细信息</span><span class="sxs-lookup"><span data-stu-id="26d31-117">Details</span></span>  
  
|<span data-ttu-id="26d31-118">数据项名称</span><span class="sxs-lookup"><span data-stu-id="26d31-118">Data Item Name</span></span>|<span data-ttu-id="26d31-119">数据项类型</span><span class="sxs-lookup"><span data-stu-id="26d31-119">Data Item Type</span></span>|<span data-ttu-id="26d31-120">说明</span><span class="sxs-lookup"><span data-stu-id="26d31-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="26d31-121">TypeName</span><span class="sxs-lookup"><span data-stu-id="26d31-121">TypeName</span></span>|`xs:string`|<span data-ttu-id="26d31-122">所调用检查器的类型的 CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="26d31-122">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="26d31-123">HostReference</span><span class="sxs-lookup"><span data-stu-id="26d31-123">HostReference</span></span>|`xs:string`|<span data-ttu-id="26d31-124">对于 Web 承载的服务，此字段唯一标识 Web 层次结构中的服务。</span><span class="sxs-lookup"><span data-stu-id="26d31-124">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="26d31-125">其格式定义为 "网站名称应用程序虚拟路径&#124;服务虚拟路径&#124;ServiceName"。</span><span class="sxs-lookup"><span data-stu-id="26d31-125">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="26d31-126">示例： "Default Web Site//Calculatorapplication&#124;/CalculatorService.svc&#124;CalculatorService"。</span><span class="sxs-lookup"><span data-stu-id="26d31-126">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="26d31-127">应用程序域</span><span class="sxs-lookup"><span data-stu-id="26d31-127">AppDomain</span></span>|`xs:string`|<span data-ttu-id="26d31-128">由 AppDomain.CurrentDomain.FriendlyName 返回的字符串。</span><span class="sxs-lookup"><span data-stu-id="26d31-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
