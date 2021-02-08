---
description: 了解详细 <add> 信息： <filters>
title: <add> 的 <filters>
ms.date: 03/30/2017
ms.assetid: e3bf437c-dd99-49f3-9792-9a8721e6eaad
ms.openlocfilehash: 546ff41fddfd8a48e14508e27f09236c67c9abc9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802341"
---
# <a name="add-of-filters"></a><span data-ttu-id="6c935-103">\<add> 的 \<filters></span><span class="sxs-lookup"><span data-stu-id="6c935-103">\<add> of \<filters></span></span>

<span data-ttu-id="6c935-104">一个 XPath 筛选器，用于指定要记录的消息的种类。</span><span class="sxs-lookup"><span data-stu-id="6c935-104">A XPath filter that specifies the kind of message to be logged.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<diagnostics>**](diagnostics.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<messageLogging>**](messagelogging.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filters>**](filters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="6c935-105">语法</span><span class="sxs-lookup"><span data-stu-id="6c935-105">Syntax</span></span>  
  
```xml  
<filters>
  <add filter="String" />
</filters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6c935-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="6c935-106">Attributes and Elements</span></span>  

 <span data-ttu-id="6c935-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6c935-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6c935-108">特性</span><span class="sxs-lookup"><span data-stu-id="6c935-108">Attributes</span></span>  
  
|<span data-ttu-id="6c935-109">属性</span><span class="sxs-lookup"><span data-stu-id="6c935-109">Attribute</span></span>|<span data-ttu-id="6c935-110">说明</span><span class="sxs-lookup"><span data-stu-id="6c935-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6c935-111">filter</span><span class="sxs-lookup"><span data-stu-id="6c935-111">filter</span></span>|<span data-ttu-id="6c935-112">一个字符串，用于指定由 XPath 1.0 表达式定义的 XML 文档的查询。</span><span class="sxs-lookup"><span data-stu-id="6c935-112">A string that specifies a query on an XML document defined by an XPath 1.0 expression.</span></span> <span data-ttu-id="6c935-113">有关详细信息，请参阅 <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>。</span><span class="sxs-lookup"><span data-stu-id="6c935-113">For more information, see <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6c935-114">子元素</span><span class="sxs-lookup"><span data-stu-id="6c935-114">Child Elements</span></span>  

 <span data-ttu-id="6c935-115">无。</span><span class="sxs-lookup"><span data-stu-id="6c935-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6c935-116">父元素</span><span class="sxs-lookup"><span data-stu-id="6c935-116">Parent Elements</span></span>  
  
|<span data-ttu-id="6c935-117">元素</span><span class="sxs-lookup"><span data-stu-id="6c935-117">Element</span></span>|<span data-ttu-id="6c935-118">说明</span><span class="sxs-lookup"><span data-stu-id="6c935-118">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters.md)|<span data-ttu-id="6c935-119">包含用于控制所记录的消息类型的 XPath 筛选器集合。</span><span class="sxs-lookup"><span data-stu-id="6c935-119">Contains a collection of XPath filters used to control what kind of message is logged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c935-120">备注</span><span class="sxs-lookup"><span data-stu-id="6c935-120">Remarks</span></span>  

 <span data-ttu-id="6c935-121">如果将 `logMessagesAtTransportLevel` 指定为 `true`，筛选器将只应用于传输层。</span><span class="sxs-lookup"><span data-stu-id="6c935-121">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="6c935-122">筛选器不影响服务级别和格式不正确的消息日志记录。</span><span class="sxs-lookup"><span data-stu-id="6c935-122">Service level and malformed message logging are not affected by filters.</span></span>  
  
 <span data-ttu-id="6c935-123">若要向集合添加筛选器，请使用 `add` 关键字。</span><span class="sxs-lookup"><span data-stu-id="6c935-123">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="6c935-124">如果定义一个或多个筛选器，则仅记录与其中至少一个筛选器相匹配的消息。</span><span class="sxs-lookup"><span data-stu-id="6c935-124">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="6c935-125">如果未定义任何筛选器，则所有消息都可通过。</span><span class="sxs-lookup"><span data-stu-id="6c935-125">If no filter is defined, all messages pass through.</span></span>  
  
 <span data-ttu-id="6c935-126">筛选器支持完整的 XPath 语法，并按照其在配置文件中出现的顺序进行应用。</span><span class="sxs-lookup"><span data-stu-id="6c935-126">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="6c935-127">存在语法错误的筛选器会导致配置异常。</span><span class="sxs-lookup"><span data-stu-id="6c935-127">A syntactically incorrect filter results in a configuration exception.</span></span>  
  
 <span data-ttu-id="6c935-128">下面的示例演示如何配置一个筛选器，它仅记录具有 SOAP 标头部分的消息。</span><span class="sxs-lookup"><span data-stu-id="6c935-128">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c935-129">示例</span><span class="sxs-lookup"><span data-stu-id="6c935-129">Example</span></span>  

 <span data-ttu-id="6c935-130">下面的示例演示如何配置一个筛选器，它仅记录具有 SOAP 标头部分的消息。</span><span class="sxs-lookup"><span data-stu-id="6c935-130">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
```xml  
<messageLogging logEntireMessage="true"
                logMalformedMessages="true"
                logMessagesAtServiceLevel="true"
                logMessagesAtTransportLevel="true"
                maxMessagesToLog="420">
  <filters>
    <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">
      /soap:Envelope/soap:Headers
    </add>
  </filters>
</messageLogging>
```  
  
## <a name="see-also"></a><span data-ttu-id="6c935-131">请参阅</span><span class="sxs-lookup"><span data-stu-id="6c935-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [<span data-ttu-id="6c935-132">配置消息日志记录</span><span class="sxs-lookup"><span data-stu-id="6c935-132">Configuring Message Logging</span></span>](../../../wcf/diagnostics/configuring-message-logging.md)
- [\<messageLogging>](messagelogging.md)
