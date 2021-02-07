---
description: 了解详细信息： <backupList>
title: <backupList>
ms.date: 03/30/2017
ms.assetid: a3d9d1f9-4a53-45e9-a880-86c8bee0b833
ms.openlocfilehash: 5323c8dad827ebb95e3cad65b3ad527d04517e3a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749709"
---
# \<backupList>

<span data-ttu-id="fcf54-102">表示用于定义备份列表的配置节，该列表枚举当无法访问主终结点时路由服务将使用的一组终结点。</span><span class="sxs-lookup"><span data-stu-id="fcf54-102">Represents a configuration section for defining a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="fcf54-103">如果列表中的第一个终结点关闭，则路由服务会自动故障转移到列表中的下一个终结点。</span><span class="sxs-lookup"><span data-stu-id="fcf54-103">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="fcf54-104">这样，可以方便地提高应用程序的可靠性，而不必告诉客户端应用程序应如何处理复杂模式或所有服务的部署位置。</span><span class="sxs-lookup"><span data-stu-id="fcf54-104">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupLists>**](backuplists.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<backupList>**  
  
## <a name="syntax"></a><span data-ttu-id="fcf54-105">语法</span><span class="sxs-lookup"><span data-stu-id="fcf54-105">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fcf54-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="fcf54-106">Attributes and Elements</span></span>  

 <span data-ttu-id="fcf54-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="fcf54-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fcf54-108">特性</span><span class="sxs-lookup"><span data-stu-id="fcf54-108">Attributes</span></span>  
  
|<span data-ttu-id="fcf54-109">属性</span><span class="sxs-lookup"><span data-stu-id="fcf54-109">Attribute</span></span>|<span data-ttu-id="fcf54-110">说明</span><span class="sxs-lookup"><span data-stu-id="fcf54-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fcf54-111">name</span><span class="sxs-lookup"><span data-stu-id="fcf54-111">name</span></span>|<span data-ttu-id="fcf54-112">一个字符串，指定用于标识此终结点列表的名称。</span><span class="sxs-lookup"><span data-stu-id="fcf54-112">A string that specifies the name used to identify this endpoint list.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fcf54-113">子元素</span><span class="sxs-lookup"><span data-stu-id="fcf54-113">Child Elements</span></span>  
  
|<span data-ttu-id="fcf54-114">元素</span><span class="sxs-lookup"><span data-stu-id="fcf54-114">Element</span></span>|<span data-ttu-id="fcf54-115">说明</span><span class="sxs-lookup"><span data-stu-id="fcf54-115">Description</span></span>|  
|-------------|-----------------|  
|[\<filter>](filter.md)||  
  
### <a name="parent-elements"></a><span data-ttu-id="fcf54-116">父元素</span><span class="sxs-lookup"><span data-stu-id="fcf54-116">Parent Elements</span></span>  
  
|<span data-ttu-id="fcf54-117">元素</span><span class="sxs-lookup"><span data-stu-id="fcf54-117">Element</span></span>|<span data-ttu-id="fcf54-118">说明</span><span class="sxs-lookup"><span data-stu-id="fcf54-118">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="fcf54-119">备份终结点列表。</span><span class="sxs-lookup"><span data-stu-id="fcf54-119">A list of backup endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fcf54-120">备注</span><span class="sxs-lookup"><span data-stu-id="fcf54-120">Remarks</span></span>  

 <span data-ttu-id="fcf54-121">此节包含终结点的有序集合，如果在将消息发送到主终结点时发生通信异常，则会将消息传输到此集合。</span><span class="sxs-lookup"><span data-stu-id="fcf54-121">This section contains an ordered collection of endpoints that a message will be transmitted to in the event of a communications exception when sending to the primary endpoint.</span></span>  
  
 <span data-ttu-id="fcf54-122">如果发送到的属性中列出的主终结点 `endpointName` [\<add>](add-of-entries.md) 失败并出现通信异常，则路由服务会尝试将消息发送到此配置节中的第一个终结点。</span><span class="sxs-lookup"><span data-stu-id="fcf54-122">If a send to the primary endpoint listed in the `endpointName` attribute of [\<add>](add-of-entries.md) fails with a communications exception, the Routing Service will attempt to send the message to the first endpoint in this configuration section.</span></span> <span data-ttu-id="fcf54-123">如果此操作同样发生通信异常而导致发送失败，则路由服务会尝试将消息发送到此节包含的下一消息，直到发送尝试成功、返回除通信异常以外的故障或集合中的所有终结点均返回故障为止。</span><span class="sxs-lookup"><span data-stu-id="fcf54-123">If this also fails with a communications exception, the Routing Service will attempt to send the message to the next message contained in this section until the send attempt succeeds, returns a failure other than a communication exception, or all endpoints in the collection have returned a failure.</span></span>  
  
 <span data-ttu-id="fcf54-124">在以下示例中，如果发送到名为 "Destination" 的主终结点返回通信异常，则该服务将尝试将消息发送到 "alternateServiceQueue"。</span><span class="sxs-lookup"><span data-stu-id="fcf54-124">In the following example, if a send to the primary endpoint named "Destination" returns a communication exception, the service will attempt to send the message to the "alternateServiceQueue".</span></span> <span data-ttu-id="fcf54-125">如果此尝试也返回一个通信异常，则路由服务会尝试将消息发送到集合中的下一个终结点。</span><span class="sxs-lookup"><span data-stu-id="fcf54-125">If this attempt also returns a communication exception, the Routing Service will attempt to send the message to the next endpoint in the collection.</span></span>  
  
```xml  
<filterTables>
  <filterTable name="filterTable1">
    <add filterName="MatchAllFilter1"
         endpointName="Destination"
         backupList="backupEndpointList" />
  </filterTable>
</filterTables>
<backupLists>
  <backupList name="backupEndpointList">
    <add endpointName="backupServiceQueue" />
    <add endpointName="alternateServiceQueue" />
  </backupList>
</backupLists>
```  
  
## <a name="see-also"></a><span data-ttu-id="fcf54-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="fcf54-126">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
