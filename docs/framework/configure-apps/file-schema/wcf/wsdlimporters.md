---
description: 了解详细信息： <wsdlImporters>
title: <wsdlImporters>
ms.date: 03/30/2017
ms.assetid: 270c7f93-eab7-47b6-8b94-ac3f5b7f17e4
ms.openlocfilehash: 55334d231a1467974bc58608ecd133e864a6535f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682119"
---
# \<wsdlImporters>

<span data-ttu-id="7a0e7-102">此配置元素指定可导入带有 WS-Policy 附件的 Web 服务描述语言 (WSDL) 1.1 元数据的所有 WSDL 导入程序。</span><span class="sxs-lookup"><span data-stu-id="7a0e7-102">This configuration element specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span> <span data-ttu-id="7a0e7-103">每个子元素都是一个 <`wsdlImporter`>，它指定导入元数据的方式，以及将该信息转换为各种表示协定和终结点信息的类。</span><span class="sxs-lookup"><span data-stu-id="7a0e7-103">Each child element is a <`wsdlImporter`> that specifies the way to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="7a0e7-104">它可以有选择地导入协定和终结点信息以及公开任何导入错误的属性，并接受与导入和转换过程相关的类型信息。</span><span class="sxs-lookup"><span data-stu-id="7a0e7-104">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="7a0e7-105">它还支持导入某些绑定信息和属性，这些信息和属性提供了对任何策略文档、WSDL 文档、WSDL 扩展和 XML 架构文档的访问。</span><span class="sxs-lookup"><span data-stu-id="7a0e7-105">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a0e7-106">请参阅</span><span class="sxs-lookup"><span data-stu-id="7a0e7-106">See also</span></span>

- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="7a0e7-107">WCF 客户端配置</span><span class="sxs-lookup"><span data-stu-id="7a0e7-107">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="7a0e7-108">客户端</span><span class="sxs-lookup"><span data-stu-id="7a0e7-108">Clients</span></span>](../../../wcf/feature-details/clients.md)
