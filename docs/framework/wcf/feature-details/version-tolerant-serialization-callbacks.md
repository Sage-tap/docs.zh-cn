---
description: 了解详细信息： Version-Tolerant 序列化回调
title: 版本容错序列化回调
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OnDeserializedAttribute [WCF]
- OnDeserializingAttribute [WCF]
- OnSerializingAttribute [WCF]
- serialization [WCF], setting default values
- OnSerializedAttribute [WCF]
ms.assetid: aa4a3a6f-05ec-4efd-bdbf-2181e13e6468
ms.openlocfilehash: 8ee53e96b90ae6b0f2993a543fc129d75eb3481f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756001"
---
# <a name="version-tolerant-serialization-callbacks"></a><span data-ttu-id="9297f-103">版本容错序列化回调</span><span class="sxs-lookup"><span data-stu-id="9297f-103">Version-Tolerant Serialization Callbacks</span></span>

<span data-ttu-id="9297f-104">数据协定编程模型充分支持 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 和 <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> 类所支持的版本容错序列化回调方法。</span><span class="sxs-lookup"><span data-stu-id="9297f-104">The data contract programming model fully supports the version-tolerant serialization callback methods that the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> and <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> classes support.</span></span>  
  
## <a name="version-tolerant-attributes"></a><span data-ttu-id="9297f-105">版本容错属性</span><span class="sxs-lookup"><span data-stu-id="9297f-105">Version-Tolerant Attributes</span></span>  

 <span data-ttu-id="9297f-106">共有四个回调属性。</span><span class="sxs-lookup"><span data-stu-id="9297f-106">There are four callback attributes.</span></span> <span data-ttu-id="9297f-107">每个属性都可应用于序列化/反序列化引擎在不同时间调用的方法。</span><span class="sxs-lookup"><span data-stu-id="9297f-107">Each attribute can be applied to a method that the serialization/deserialization engine calls at various times.</span></span> <span data-ttu-id="9297f-108">下表说明使用每个属性的时间。</span><span class="sxs-lookup"><span data-stu-id="9297f-108">The table below explains when to use each attribute.</span></span>  
  
|<span data-ttu-id="9297f-109">Attribute</span><span class="sxs-lookup"><span data-stu-id="9297f-109">Attribute</span></span>|<span data-ttu-id="9297f-110">调用相应方法时。</span><span class="sxs-lookup"><span data-stu-id="9297f-110">When the corresponding method is called</span></span>|  
|---------------|---------------------------------------------|  
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|<span data-ttu-id="9297f-111">在序列化类型之前调用。</span><span class="sxs-lookup"><span data-stu-id="9297f-111">Called before serializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|<span data-ttu-id="9297f-112">在序列化类型之后调用。</span><span class="sxs-lookup"><span data-stu-id="9297f-112">Called after serializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|<span data-ttu-id="9297f-113">在反序列化类型之前调用。</span><span class="sxs-lookup"><span data-stu-id="9297f-113">Called before deserializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|<span data-ttu-id="9297f-114">在反序列化类型之后调用。</span><span class="sxs-lookup"><span data-stu-id="9297f-114">Called after deserializing the type.</span></span>|  
  
 <span data-ttu-id="9297f-115">该方法必须接受 <xref:System.Runtime.Serialization.StreamingContext> 参数。</span><span class="sxs-lookup"><span data-stu-id="9297f-115">The methods must accept a <xref:System.Runtime.Serialization.StreamingContext> parameter.</span></span>  
  
 <span data-ttu-id="9297f-116">这些方法主要计划用于版本控制或初始化。</span><span class="sxs-lookup"><span data-stu-id="9297f-116">These methods are primarily intended for use with versioning or initialization.</span></span> <span data-ttu-id="9297f-117">反序列化期间，不调用任何构造函数。</span><span class="sxs-lookup"><span data-stu-id="9297f-117">During deserialization, no constructors are called.</span></span> <span data-ttu-id="9297f-118">因此，如果传入流中缺少数据成员的数据，则这些成员可能不会正确初始化（为既定的默认值），例如，如果数据来自缺少某些数据成员的类型的上一版本。</span><span class="sxs-lookup"><span data-stu-id="9297f-118">Therefore, data members may not be correctly initialized (to intended default values) if the data for these members is missing in the incoming stream, for example, if the data comes from a previous version of a type that is missing some data members.</span></span> <span data-ttu-id="9297f-119">若要更正此错误，请使用加有 <xref:System.Runtime.Serialization.OnDeserializingAttribute> 标记的回调方法，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="9297f-119">To correct this, use the callback method marked with the <xref:System.Runtime.Serialization.OnDeserializingAttribute>, as shown in the following example.</span></span>  
  
 <span data-ttu-id="9297f-120">只能使用上述每个回调属性对每个类型标记一个方法。</span><span class="sxs-lookup"><span data-stu-id="9297f-120">You can mark only one method per type with each of the preceding callback attributes.</span></span>  
  
### <a name="example"></a><span data-ttu-id="9297f-121">示例</span><span class="sxs-lookup"><span data-stu-id="9297f-121">Example</span></span>  

 [!code-csharp[C_DataContract#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#9)]
 [!code-vb[C_DataContract#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="9297f-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="9297f-122">See also</span></span>

- <xref:System.Runtime.Serialization.OnSerializingAttribute>
- <xref:System.Runtime.Serialization.OnSerializedAttribute>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>
- <xref:System.Runtime.Serialization.StreamingContext>
- [<span data-ttu-id="9297f-123">版本容错序列化</span><span class="sxs-lookup"><span data-stu-id="9297f-123">Version Tolerant Serialization</span></span>](../../../standard/serialization/version-tolerant-serialization.md)
