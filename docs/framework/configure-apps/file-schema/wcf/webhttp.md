---
description: 了解详细信息： <webHttp>
title: <webHttp>
ms.date: 03/30/2017
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
ms.openlocfilehash: acd8d77e00828d132d076c867ff3164ca1ba7230
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664374"
---
# \<webHttp>

<span data-ttu-id="3095b-102">此元素通过配置指定终结点上的 <xref:System.ServiceModel.Description.WebHttpBehavior>。</span><span class="sxs-lookup"><span data-stu-id="3095b-102">This element specifies the <xref:System.ServiceModel.Description.WebHttpBehavior> on an endpoint through configuration.</span></span> <span data-ttu-id="3095b-103">此行为与标准绑定结合使用时 [\<webHttpBinding>](webhttpbinding.md) ，将为 Windows Communication Foundation (WCF) 服务启用 Web 编程模型。</span><span class="sxs-lookup"><span data-stu-id="3095b-103">This behavior, when used in conjunction with the [\<webHttpBinding>](webhttpbinding.md) standard binding, enables the Web programming model for a Windows Communication Foundation (WCF) service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webHttp>**  
  
## <a name="syntax"></a><span data-ttu-id="3095b-104">语法</span><span class="sxs-lookup"><span data-stu-id="3095b-104">Syntax</span></span>  
  
```xml  
<webHttp />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3095b-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="3095b-105">Attributes and Elements</span></span>  

 <span data-ttu-id="3095b-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="3095b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3095b-107">特性</span><span class="sxs-lookup"><span data-stu-id="3095b-107">Attributes</span></span>  
  
|<span data-ttu-id="3095b-108">属性</span><span class="sxs-lookup"><span data-stu-id="3095b-108">Attribute</span></span>|<span data-ttu-id="3095b-109">说明</span><span class="sxs-lookup"><span data-stu-id="3095b-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3095b-110">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="3095b-110">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="3095b-111">如果此属性设置为 `true`，WCF 基础结构将确定要使用的最佳格式。</span><span class="sxs-lookup"><span data-stu-id="3095b-111">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="3095b-112">默认情况下，禁用自动格式选择，以保证向后兼容性。</span><span class="sxs-lookup"><span data-stu-id="3095b-112">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="3095b-113">可以通过编程方式或配置启用自动格式选择。</span><span class="sxs-lookup"><span data-stu-id="3095b-113">Automatic format selection can be enabled programmatically or through configuration.</span></span>|  
|<span data-ttu-id="3095b-114">defaultBodyStyle</span><span class="sxs-lookup"><span data-stu-id="3095b-114">defaultBodyStyle</span></span>|<span data-ttu-id="3095b-115">指定返回的消息的默认正文样式。</span><span class="sxs-lookup"><span data-stu-id="3095b-115">Specifies the default body style of returned messages.</span></span> <span data-ttu-id="3095b-116">有关详细信息，请参阅 <xref:System.ServiceModel.Web.WebMessageBodyStyle> 和 [WCF Web HTTP 格式设置](../../../wcf/feature-details/wcf-web-http-formatting.md)。</span><span class="sxs-lookup"><span data-stu-id="3095b-116">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle> and [WCF Web HTTP Formatting](../../../wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="3095b-117">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="3095b-117">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="3095b-118">指定消息的默认传出响应格式。</span><span class="sxs-lookup"><span data-stu-id="3095b-118">Specifies the default outgoing response format for messages.</span></span> <span data-ttu-id="3095b-119">有关详细信息，请参阅 [WCF WEB HTTP 格式设置](../../../wcf/feature-details/wcf-web-http-formatting.md)。</span><span class="sxs-lookup"><span data-stu-id="3095b-119">For more information, see [WCF Web HTTP Formatting](../../../wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="3095b-120">faultExceptionEnabled</span><span class="sxs-lookup"><span data-stu-id="3095b-120">faultExceptionEnabled</span></span>|<span data-ttu-id="3095b-121">获取或设置用于指定在发生内部服务器错误（HTTP 状态代码：500）时是否生成 FaultException 的标志。</span><span class="sxs-lookup"><span data-stu-id="3095b-121">Gets or sets the flag that specifies whether a FaultException is generated when an internal server error (HTTP status code: 500) occurs.</span></span>|  
|<span data-ttu-id="3095b-122">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="3095b-122">helpEnabled</span></span>|<span data-ttu-id="3095b-123">获取或设置一个值，该值确定是否启用了帮助页。</span><span class="sxs-lookup"><span data-stu-id="3095b-123">Gets or sets a value that determines if the Help page is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3095b-124">子元素</span><span class="sxs-lookup"><span data-stu-id="3095b-124">Child Elements</span></span>  

 <span data-ttu-id="3095b-125">无。</span><span class="sxs-lookup"><span data-stu-id="3095b-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3095b-126">父元素</span><span class="sxs-lookup"><span data-stu-id="3095b-126">Parent Elements</span></span>  
  
|<span data-ttu-id="3095b-127">元素</span><span class="sxs-lookup"><span data-stu-id="3095b-127">Element</span></span>|<span data-ttu-id="3095b-128">说明</span><span class="sxs-lookup"><span data-stu-id="3095b-128">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="3095b-129">指定终结点行为集。</span><span class="sxs-lookup"><span data-stu-id="3095b-129">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3095b-130">请参阅</span><span class="sxs-lookup"><span data-stu-id="3095b-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpElement>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [<span data-ttu-id="3095b-131">AJAX 集成和 JSON 支持</span><span class="sxs-lookup"><span data-stu-id="3095b-131">AJAX Integration and JSON Support</span></span>](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [\<webHttpBinding>](webhttpbinding.md)
