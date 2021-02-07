---
description: 了解详细信息： Windows Workflow Foundation 配置架构
title: Windows Workflow Foundation 配置架构
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 7ae70357-b150-4342-8f2a-d5eb6f9c6a0d
ms.openlocfilehash: bdc8164d4936436a41c217ce2eabddd9ec44c8d8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740049"
---
# <a name="windows-workflow-foundation-configuration-schema"></a><span data-ttu-id="d71e8-103">Windows Workflow Foundation 配置架构</span><span class="sxs-lookup"><span data-stu-id="d71e8-103">Windows Workflow Foundation Configuration Schema</span></span>

<span data-ttu-id="d71e8-104">Windows Workflow Foundation (WF) 配置元素，你可以配置工作流应用程序。</span><span class="sxs-lookup"><span data-stu-id="d71e8-104">Windows Workflow Foundation (WF) configuration elements enable you to configure workflow applications.</span></span> <span data-ttu-id="d71e8-105">对于工作流应用程序，除配置其他内容外，还可以配置跟踪。</span><span class="sxs-lookup"><span data-stu-id="d71e8-105">For a workflow application, you can configure among other things, tracking and tracing.</span></span> <span data-ttu-id="d71e8-106">有关跟踪的详细信息，请参阅[工作流跟踪](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)。</span><span class="sxs-lookup"><span data-stu-id="d71e8-106">For more information about tracking and tracing, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span> <span data-ttu-id="d71e8-107">对于工作流服务，还可以使用 Windows Communication Foundation (WCF) 配置元素。</span><span class="sxs-lookup"><span data-stu-id="d71e8-107">For workflow services, you can also use Windows Communication Foundation (WCF) configuration elements.</span></span> <span data-ttu-id="d71e8-108">有关 WCF 的详细信息，请参阅 [Wcf 配置架构](../wcf/index.md)。</span><span class="sxs-lookup"><span data-stu-id="d71e8-108">For more details about WCF, see [WCF Configuration Schema](../wcf/index.md).</span></span>  
  
 <span data-ttu-id="d71e8-109">由于配置文件的格式都是以 XML 形式设置的，因此，如果要使用文本编辑器手动编辑这些文件，则您必须熟悉 XML。</span><span class="sxs-lookup"><span data-stu-id="d71e8-109">Because configuration files are formatted as XML, you must be familiar with XML if you want to manually edit them using a text editor.</span></span> <span data-ttu-id="d71e8-110">否则，您可能会遇到一些问题，如找不到某个 XML 元素标记或特性。</span><span class="sxs-lookup"><span data-stu-id="d71e8-110">Otherwise, you may run into issues such as an unfound XML element tag or attribute.</span></span> <span data-ttu-id="d71e8-111">这是因为 XML 元素标记和特性是区分大小写的。</span><span class="sxs-lookup"><span data-stu-id="d71e8-111">This is because XML element tags and attributes are case-sensitive.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d71e8-112">本节内容</span><span class="sxs-lookup"><span data-stu-id="d71e8-112">In This Section</span></span>  

 [\<system.serviceModel>](system-servicemodel-of-workflow.md)  
 <span data-ttu-id="d71e8-113">描述 **ServiceModel** 元素。</span><span class="sxs-lookup"><span data-stu-id="d71e8-113">Describes the **ServiceModel** element.</span></span>
