---
description: 了解详细 <add> 信息： <protocolMapping>
title: <add> 的 <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 08e62249-1641-41d1-91b1-66d7b46244e4
ms.openlocfilehash: 530ef6b2893eb55a979aba2ef7ec21efffc3070a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750242"
---
# <a name="add-of-protocolmapping"></a><span data-ttu-id="34be9-103">\<add> 的 \<protocolMapping></span><span class="sxs-lookup"><span data-stu-id="34be9-103">\<add> of \<protocolMapping></span></span>

<span data-ttu-id="34be9-104">表示传输协议方案 (（如 http、net.tcp、) net.pipe 等）与 Windows Communication Foundation (WCF) 绑定之间的默认协议映射。</span><span class="sxs-lookup"><span data-stu-id="34be9-104">Represents a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a Windows Communication Foundation (WCF) binding.</span></span> <span data-ttu-id="34be9-105">在运行时创建默认终结点时，WCF 会查看已配置的映射，并决定要将哪个绑定用于特定的地址。</span><span class="sxs-lookup"><span data-stu-id="34be9-105">When creating default endpoints at runtime, WCF looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<protocolMapping>**](protocolmapping.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="34be9-106">语法</span><span class="sxs-lookup"><span data-stu-id="34be9-106">Syntax</span></span>  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="34be9-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="34be9-107">Attributes and Elements</span></span>  

 <span data-ttu-id="34be9-108">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="34be9-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="34be9-109">特性</span><span class="sxs-lookup"><span data-stu-id="34be9-109">Attributes</span></span>  
  
|<span data-ttu-id="34be9-110">元素</span><span class="sxs-lookup"><span data-stu-id="34be9-110">Element</span></span>|<span data-ttu-id="34be9-111">说明</span><span class="sxs-lookup"><span data-stu-id="34be9-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="34be9-112">binding</span><span class="sxs-lookup"><span data-stu-id="34be9-112">binding</span></span>|<span data-ttu-id="34be9-113">一个字符串，指定在创建默认终结点时要用于终结点的绑定类型。</span><span class="sxs-lookup"><span data-stu-id="34be9-113">A string that specifies the type of binding to be used for an endpoint during default endpoint creation.</span></span>|  
|<span data-ttu-id="34be9-114">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="34be9-114">bindingConfiguration</span></span>|<span data-ttu-id="34be9-115">一个字符串，指定要引用的绑定配置节的名称。</span><span class="sxs-lookup"><span data-stu-id="34be9-115">A string that specifies the name of the binding configuration section to be referenced.</span></span>|  
|<span data-ttu-id="34be9-116">scheme</span><span class="sxs-lookup"><span data-stu-id="34be9-116">scheme</span></span>|<span data-ttu-id="34be9-117">要用于默认终结点的传输协议方案。</span><span class="sxs-lookup"><span data-stu-id="34be9-117">The transport protocol scheme to be used for the default endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="34be9-118">子元素</span><span class="sxs-lookup"><span data-stu-id="34be9-118">Child Elements</span></span>  

 <span data-ttu-id="34be9-119">无。</span><span class="sxs-lookup"><span data-stu-id="34be9-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="34be9-120">父元素</span><span class="sxs-lookup"><span data-stu-id="34be9-120">Parent Elements</span></span>  
  
|<span data-ttu-id="34be9-121">元素</span><span class="sxs-lookup"><span data-stu-id="34be9-121">Element</span></span>|<span data-ttu-id="34be9-122">说明</span><span class="sxs-lookup"><span data-stu-id="34be9-122">Description</span></span>|  
|-------------|-----------------|  
|[\<protocolMapping>](protocolmapping.md)|<span data-ttu-id="34be9-123">表示一个配置节，该配置节用于定义传输协议方案 (（如 http、net.tcp、net.pipe ) 等）之间的默认协议映射，并 Windows Communication Foundation (WCF) 绑定。</span><span class="sxs-lookup"><span data-stu-id="34be9-123">Represents a configuration section for defining default protocol mappings between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and Windows Communication Foundation (WCF) bindings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="34be9-124">示例</span><span class="sxs-lookup"><span data-stu-id="34be9-124">Example</span></span>  

 <span data-ttu-id="34be9-125">下面的配置示例演示 machine.config 文件中的默认协议映射。</span><span class="sxs-lookup"><span data-stu-id="34be9-125">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="34be9-126">您可以通过修改 machine.config 文件在计算机级别重写此默认映射。</span><span class="sxs-lookup"><span data-stu-id="34be9-126">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="34be9-127">或者，如果您只希望在应用程序范围内重写此映射，则可以在应用程序配置文件中重写此节，并为单独的协议方案更改映射。</span><span class="sxs-lookup"><span data-stu-id="34be9-127">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
```xml  
<protocolMapping>
  <add scheme="http"
       binding="basicHttpBinding" />
  <add scheme="net.tcp"
       binding="netTcpBinding" />
  <add scheme="net.pipe"
       binding="netNamedPipeBinding" />
  <add scheme="net.msmq"
       binding="netMsmqBinding" />
</protocolMapping>
```  
  
## <a name="see-also"></a><span data-ttu-id="34be9-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="34be9-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
