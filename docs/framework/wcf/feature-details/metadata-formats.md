---
description: 了解更多：元数据格式
title: 元数据格式
ms.date: 03/30/2017
ms.assetid: baad1e68-28fc-4a6a-8a43-75e47e7fa871
ms.openlocfilehash: f8c5d6dd5c75f38d4114f6232e9d1d6048a8343e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99733913"
---
# <a name="metadata-formats"></a><span data-ttu-id="67555-103">元数据格式</span><span class="sxs-lookup"><span data-stu-id="67555-103">Metadata formats</span></span>

<span data-ttu-id="67555-104">Windows Communication Foundation (WCF) 支持下表中的元数据格式。</span><span class="sxs-lookup"><span data-stu-id="67555-104">Windows Communication Foundation (WCF) supports the metadata formats in the following table.</span></span>  
  
## <a name="metadata-specifications-and-usage"></a><span data-ttu-id="67555-105">元数据的规范和用法</span><span class="sxs-lookup"><span data-stu-id="67555-105">Metadata Specifications and Usage</span></span>  
  
|<span data-ttu-id="67555-106">协议</span><span class="sxs-lookup"><span data-stu-id="67555-106">Protocol</span></span>|<span data-ttu-id="67555-107">规范和用法</span><span class="sxs-lookup"><span data-stu-id="67555-107">Specification and usage</span></span>|  
|--------------|-----------------------------|  
|<span data-ttu-id="67555-108">WSDL 1.1</span><span class="sxs-lookup"><span data-stu-id="67555-108">WSDL 1.1</span></span>|[<span data-ttu-id="67555-109">Web 服务描述语言 (WSDL) 1.1</span><span class="sxs-lookup"><span data-stu-id="67555-109">Web Services Description Language (WSDL) 1.1</span></span>](https://www.w3.org/TR/wsdl/)<br /><br /> <span data-ttu-id="67555-110">WCF 使用 Web 服务描述语言 (WSDL) 来描述服务。</span><span class="sxs-lookup"><span data-stu-id="67555-110">WCF uses Web Services Description Language (WSDL) to describe services.</span></span>|  
|<span data-ttu-id="67555-111">XML 架构</span><span class="sxs-lookup"><span data-stu-id="67555-111">XML Schema</span></span>|<span data-ttu-id="67555-112">[XML 架构第2部分：数据类型第二版](https://www.w3.org/TR/2004/REC-xmlschema-2-20041028/) 和 [XML 架构第1部分：结构第二版](https://www.w3.org/TR/2004/REC-xmlschema-1-20041028/)</span><span class="sxs-lookup"><span data-stu-id="67555-112">[XML Schema Part 2: Datatypes Second Edition](https://www.w3.org/TR/2004/REC-xmlschema-2-20041028/) and [XML Schema Part 1: Structures Second Edition](https://www.w3.org/TR/2004/REC-xmlschema-1-20041028/)</span></span><br /><br /> <span data-ttu-id="67555-113">WCF 使用 XML 架构描述消息中使用的数据类型。</span><span class="sxs-lookup"><span data-stu-id="67555-113">WCF uses the XML Schema to describe data types used in messages.</span></span>|  
|<span data-ttu-id="67555-114">WS Policy</span><span class="sxs-lookup"><span data-stu-id="67555-114">WS Policy</span></span>|[<span data-ttu-id="67555-115">Web 服务策略 1.2 - 框架 (WS-Policy)</span><span class="sxs-lookup"><span data-stu-id="67555-115">Web Services Policy 1.2 - Framework (WS-Policy)</span></span>](https://www.w3.org/Submission/WS-Policy/)<br /><br /> [<span data-ttu-id="67555-116">Web 服务策略 1.5 - 框架</span><span class="sxs-lookup"><span data-stu-id="67555-116">Web Services Policy 1.5 - Framework</span></span>](https://www.w3.org/TR/ws-policy/)<br /><br /> <span data-ttu-id="67555-117">WCF 将 WS-Policy 1.2 或1.5 规范与域特定断言结合使用来描述服务要求和功能。</span><span class="sxs-lookup"><span data-stu-id="67555-117">WCF uses the WS-Policy 1.2 or 1.5 specifications with domain-specific assertions to describe service requirements and capabilities.</span></span>|  
|<span data-ttu-id="67555-118">WS Policy 附件</span><span class="sxs-lookup"><span data-stu-id="67555-118">WS Policy Attachments</span></span>|[<span data-ttu-id="67555-119">Web Services Policy 1.2 - Attachment (WS-PolicyAttachment)（Web 服务策略 1.2 - 附件 (WS-PolicyAttachment)）</span><span class="sxs-lookup"><span data-stu-id="67555-119">Web Services Policy 1.2 - Attachment (WS-PolicyAttachment)</span></span>](https://www.w3.org/Submission/WS-PolicyAttachment/)<br /><br /> <span data-ttu-id="67555-120">WCF 实现 WS-Policy 附件，以在 WSDL 中的不同范围内附加策略表达式。</span><span class="sxs-lookup"><span data-stu-id="67555-120">WCF implements WS-Policy Attachments to attach policy expressions at various scopes in WSDL.</span></span>|  
|<span data-ttu-id="67555-121">WS 元数据交换</span><span class="sxs-lookup"><span data-stu-id="67555-121">WS Metadata Exchange</span></span>|[<span data-ttu-id="67555-122">Web 服务元数据交换 (WS-MetadataExchange) 1.1 版</span><span class="sxs-lookup"><span data-stu-id="67555-122">Web Services Metadata Exchange (WS-MetadataExchange) version 1.1</span></span>](http://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)<br /><br /> <span data-ttu-id="67555-123">WCF 实现 WS-MetadataExchange 来检索 XML 架构、WSDL 和 WS 策略。</span><span class="sxs-lookup"><span data-stu-id="67555-123">WCF implements WS-MetadataExchange to retrieve XML Schema, WSDL, and WS-Policy.</span></span>|  
|<span data-ttu-id="67555-124">WSDL 的 WS 寻址绑定</span><span class="sxs-lookup"><span data-stu-id="67555-124">WS Addressing Binding for WSDL</span></span>|[<span data-ttu-id="67555-125">Web 服务寻址 1.0 - WSDL 绑定</span><span class="sxs-lookup"><span data-stu-id="67555-125">Web Services Addressing 1.0 - WSDL Binding</span></span>](https://www.w3.org/TR/ws-addr-wsdl/)<br /><br /> <span data-ttu-id="67555-126">WCF 为 WSDL 实现 WS-Addressing 绑定，以便在 WSDL 中附加寻址信息。</span><span class="sxs-lookup"><span data-stu-id="67555-126">WCF implements WS-Addressing Binding for WSDL to attach addressing information in WSDL.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="67555-127">请参阅</span><span class="sxs-lookup"><span data-stu-id="67555-127">See also</span></span>

- [<span data-ttu-id="67555-128">系统提供的互操作性绑定支持的 Web 服务协议</span><span class="sxs-lookup"><span data-stu-id="67555-128">Web Services Protocols Supported by System-Provided Interoperability Bindings</span></span>](web-services-protocols-supported-by-system-provided-interoperability-bindings.md)
- [<span data-ttu-id="67555-129">WSDL 和策略</span><span class="sxs-lookup"><span data-stu-id="67555-129">WSDL and Policy</span></span>](wsdl-and-policy.md)
