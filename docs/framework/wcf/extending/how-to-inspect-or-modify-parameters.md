---
description: 了解详细信息：如何：检查或修改参数
title: 如何：检查或修改参数
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ab6c0ac7-aac4-45ba-93d6-a0e9afd1756f
ms.openlocfilehash: 90358f2fbd7366b11135ec2ebd044f7864d8a1e0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99653779"
---
# <a name="how-to-inspect-or-modify-parameters"></a><span data-ttu-id="ab1c7-103">如何：检查或修改参数</span><span class="sxs-lookup"><span data-stu-id="ab1c7-103">How to: Inspect or Modify Parameters</span></span>

<span data-ttu-id="ab1c7-104">您可以通过实现 <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> 接口并将其插入到客户端或服务运行时，来检查或修改 Windows Communication Foundation (WCF) 客户端对象或 wcf 服务上的单个操作的传入或传出消息。</span><span class="sxs-lookup"><span data-stu-id="ab1c7-104">You can inspect or modify the incoming or outgoing messages for a single operation on a Windows Communication Foundation (WCF) client object or a WCF service by implementing the <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> interface and inserting it into the client or service runtime.</span></span> <span data-ttu-id="ab1c7-105">通常，操作行为用于为单个操作添加参数检查器；其他行为可以用于在更大范围内提供对运行库的方便访问。</span><span class="sxs-lookup"><span data-stu-id="ab1c7-105">Typically an operation behavior is used to add parameter inspectors for a single operation; other behaviors can be used to provide easy access to the runtime at a greater scope.</span></span> <span data-ttu-id="ab1c7-106">有关详细信息，请参阅 [扩展客户端](extending-clients.md) 和 [扩展调度](extending-dispatchers.md)程序。</span><span class="sxs-lookup"><span data-stu-id="ab1c7-106">For more information, see [Extending Clients](extending-clients.md) and [Extending Dispatchers](extending-dispatchers.md).</span></span>  
  
### <a name="inspecting-or-modifying-parameters"></a><span data-ttu-id="ab1c7-107">检查或修改参数</span><span class="sxs-lookup"><span data-stu-id="ab1c7-107">Inspecting or Modifying Parameters</span></span>  
  
1. <span data-ttu-id="ab1c7-108">实现 <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> 接口。</span><span class="sxs-lookup"><span data-stu-id="ab1c7-108">Implement the <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> interface.</span></span>  
  
2. <span data-ttu-id="ab1c7-109">实现 <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>、<xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>、<xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> 或 <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>（取决于要求的范围），以便将参数检查器添加到 <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=nameWithType> 或 <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=nameWithType> 属性。</span><span class="sxs-lookup"><span data-stu-id="ab1c7-109">Implement a <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> or <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> (depending upon the required scope) to add your parameter inspector to either the <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=nameWithType> or <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=nameWithType> properties.</span></span>  
  
3. <span data-ttu-id="ab1c7-110">在对 <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> 调用 <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> 或 <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> 方法前，插入行为。</span><span class="sxs-lookup"><span data-stu-id="ab1c7-110">Insert your behavior prior to calling <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> or the <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> method on the <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ab1c7-111">有关详细信息，请参阅 [配置和扩展运行时的行为](configuring-and-extending-the-runtime-with-behaviors.md)。</span><span class="sxs-lookup"><span data-stu-id="ab1c7-111">For details, see [Configuring and Extending the Runtime with Behaviors](configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab1c7-112">示例</span><span class="sxs-lookup"><span data-stu-id="ab1c7-112">Example</span></span>  

 <span data-ttu-id="ab1c7-113">下面的代码示例按顺序演示以下各项：</span><span class="sxs-lookup"><span data-stu-id="ab1c7-113">The following code examples show, in order:</span></span>  
  
- <span data-ttu-id="ab1c7-114">参数检查器实现。</span><span class="sxs-lookup"><span data-stu-id="ab1c7-114">A parameter inspector implementation.</span></span>  
  
- <span data-ttu-id="ab1c7-115">行为实现，它使用 、 和 插入参数检查器。</span><span class="sxs-lookup"><span data-stu-id="ab1c7-115">The behavior implementation that inserts the parameter inspector using a <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, and an <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="ab1c7-116">配置文件，它在客户端应用程序中加载和运行终结点行为，以便在客户端上插入参数检查器。</span><span class="sxs-lookup"><span data-stu-id="ab1c7-116">A configuration file that loads and runs the endpoint behavior in a client application to insert the parameter inspector on the client.</span></span>  
  
 [!code-csharp[Interceptors#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#4)]
 [!code-vb[Interceptors#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#4)]  
  
 [!code-csharp[Interceptors#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#5)]
 [!code-vb[Interceptors#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#5)]  
  
 [!code-xml[Interceptors#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/client.exe.config#3)]  
  
## <a name="see-also"></a><span data-ttu-id="ab1c7-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="ab1c7-117">See also</span></span>

- [<span data-ttu-id="ab1c7-118">使用行为配置和扩展运行时</span><span class="sxs-lookup"><span data-stu-id="ab1c7-118">Configuring and Extending the Runtime with Behaviors</span></span>](configuring-and-extending-the-runtime-with-behaviors.md)
