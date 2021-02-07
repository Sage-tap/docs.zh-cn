---
description: 了解详细信息： WCF Data Services 协议实现详细信息
title: WCF 数据服务协议实现详细信息
ms.date: 03/30/2017
ms.assetid: 712d689b-fada-4cbb-bcdb-d65a3ef83b4c
ms.openlocfilehash: 123f41859fdf579a75bb925a63619e4089577911
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748240"
---
# <a name="wcf-data-services-protocol-implementation-details"></a><span data-ttu-id="30fa1-103">WCF 数据服务协议实现详细信息</span><span class="sxs-lookup"><span data-stu-id="30fa1-103">WCF Data Services Protocol Implementation Details</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

## <a name="odata-protocol-implementation-details"></a><span data-ttu-id="30fa1-104">OData 协议实现详细信息</span><span class="sxs-lookup"><span data-stu-id="30fa1-104">OData Protocol Implementation Details</span></span>  

<span data-ttu-id="30fa1-105">Open Data Protocol (OData) 要求实现协议的数据服务提供特定的最小功能集。</span><span class="sxs-lookup"><span data-stu-id="30fa1-105">The Open Data Protocol (OData) requires that a data service that implements the protocol provide a certain minimum set of functionalities.</span></span> <span data-ttu-id="30fa1-106">这些功能在协议文档中用 "应该" 和 "必须" 描述。</span><span class="sxs-lookup"><span data-stu-id="30fa1-106">These functionalities are described in the protocol documents in terms of "should" and "must".</span></span> <span data-ttu-id="30fa1-107">其他可选功能将根据 "可能" 进行描述。</span><span class="sxs-lookup"><span data-stu-id="30fa1-107">Other optional functionality is described in terms of "may".</span></span> <span data-ttu-id="30fa1-108">本文介绍 WCF Data Services 当前未实现的这些可选功能。</span><span class="sxs-lookup"><span data-stu-id="30fa1-108">This article describes these optional functionalities that are not currently implemented by WCF Data Services.</span></span>
  
### <a name="support-for-the-format-query-option"></a><span data-ttu-id="30fa1-109">对 $format 查询选项的支持</span><span class="sxs-lookup"><span data-stu-id="30fa1-109">Support for the $format Query Option</span></span>  

 <span data-ttu-id="30fa1-110">OData 协议支持 JavaScript 符号 (JSON) 和 Atom 馈送，并且 OData 提供 `$format` 系统查询选项，以允许客户端请求响应源的格式。</span><span class="sxs-lookup"><span data-stu-id="30fa1-110">The OData protocol supports both JavaScript Notation (JSON) and Atom feeds, and OData provides the `$format` system query option to allow a client to request the format of the response feed.</span></span> <span data-ttu-id="30fa1-111">此系统查询选项（如果数据服务支持）必须重写请求的 Accept 标头的值。</span><span class="sxs-lookup"><span data-stu-id="30fa1-111">This system query option, if supported by the data service, must override the value of the Accept header of the request.</span></span> <span data-ttu-id="30fa1-112">WCF Data Services 支持同时返回 JSON 和 Atom 源。</span><span class="sxs-lookup"><span data-stu-id="30fa1-112">WCF Data Services supports returning both JSON and Atom feeds.</span></span> <span data-ttu-id="30fa1-113">但是，默认实现不支持 `$format` 查询选项，它只使用 Accept 标头的值来确定响应的格式。</span><span class="sxs-lookup"><span data-stu-id="30fa1-113">However, the default implementation does not support the `$format` query option and uses only the value of the Accept header to determine the format of the response.</span></span> <span data-ttu-id="30fa1-114">某些情况下，您的数据服务可能需要支持 `$format` 查询选项，例如，当客户端不能设置 Accept 标头时。</span><span class="sxs-lookup"><span data-stu-id="30fa1-114">There are cases when your data service may need to support the `$format` query option, such as when clients cannot set the Accept header.</span></span> <span data-ttu-id="30fa1-115">为支持这些情况，您必须扩展您的数据服务以在 URI 中处理此选项。</span><span class="sxs-lookup"><span data-stu-id="30fa1-115">To support these scenarios, you must extend your data service to handle this option in the URI.</span></span>
  
## <a name="wcf-data-services-behaviors"></a><span data-ttu-id="30fa1-116">WCF 数据服务行为</span><span class="sxs-lookup"><span data-stu-id="30fa1-116">WCF Data Services Behaviors</span></span>  

 <span data-ttu-id="30fa1-117">以下 WCF Data Services 行为未通过 OData 协议显式定义：</span><span class="sxs-lookup"><span data-stu-id="30fa1-117">The following WCF Data Services behaviors are not explicitly defined by the OData protocol:</span></span>  
  
### <a name="default-sorting-behavior"></a><span data-ttu-id="30fa1-118">默认排序行为</span><span class="sxs-lookup"><span data-stu-id="30fa1-118">Default Sorting Behavior</span></span>  

 <span data-ttu-id="30fa1-119">当发送到数据服务的查询请求包括 `$top` 或 `$skip` 系统查询选项但不包括 `$orderby` 系统查询选项时，返回的源按键属性升序排序。</span><span class="sxs-lookup"><span data-stu-id="30fa1-119">When a query request that is sent to the data service includes a `$top` or `$skip` system query option and does not include the `$orderby` system query option, the returned feed is sorted by the key properties, in ascending order.</span></span> <span data-ttu-id="30fa1-120">这是因为需要顺序以确保结果正确分页。</span><span class="sxs-lookup"><span data-stu-id="30fa1-120">This is because ordering is required to ensure the correct paging of results.</span></span> <span data-ttu-id="30fa1-121">为此，数据服务向查询中添加排序表达式。</span><span class="sxs-lookup"><span data-stu-id="30fa1-121">To do this, the data service adds an ordering expression to the query.</span></span> <span data-ttu-id="30fa1-122">在数据服务中启用服务器驱动的分页时，也会发生此行为。</span><span class="sxs-lookup"><span data-stu-id="30fa1-122">This behavior also occurs when server-driven paging is enabled in the data service.</span></span> <span data-ttu-id="30fa1-123">有关详细信息，请参阅 [配置数据服务](configuring-the-data-service-wcf-data-services.md)。若要控制返回的源的排序，应将包含 `$orderby` 在查询 URI 中。</span><span class="sxs-lookup"><span data-stu-id="30fa1-123">For more information, see [Configuring the Data Service](configuring-the-data-service-wcf-data-services.md).To control the ordering of the returned feed, you should include `$orderby` in the query URI.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30fa1-124">请参阅</span><span class="sxs-lookup"><span data-stu-id="30fa1-124">See also</span></span>

- [<span data-ttu-id="30fa1-125">定义 WCF 数据服务</span><span class="sxs-lookup"><span data-stu-id="30fa1-125">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)
- [<span data-ttu-id="30fa1-126">WCF 数据服务客户端库</span><span class="sxs-lookup"><span data-stu-id="30fa1-126">WCF Data Services Client Library</span></span>](wcf-data-services-client-library.md)
