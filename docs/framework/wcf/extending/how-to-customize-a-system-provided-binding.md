---
description: 了解详细信息：如何：自定义 System-Provided 绑定
title: 如何：自定义系统提供的绑定
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f8b97862-e8bb-470d-8b96-07733c21fe26
ms.openlocfilehash: c0463a8e427e6503f0e68bc58eb488f9b0bad15a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668950"
---
# <a name="how-to-customize-a-system-provided-binding"></a><span data-ttu-id="5762d-103">如何：自定义系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="5762d-103">How to: Customize a System-Provided Binding</span></span>

<span data-ttu-id="5762d-104">Windows Communication Foundation (WCF) 包含多个系统提供的绑定，这些绑定允许您配置基础绑定元素的某些属性，但不是所有属性。</span><span class="sxs-lookup"><span data-stu-id="5762d-104">Windows Communication Foundation (WCF) includes several system-provided bindings that allow you to configure some of the properties of the underlying binding elements, but not all of the properties.</span></span> <span data-ttu-id="5762d-105">本主题演示如何设置绑定元素上的属性以创建自定义绑定。</span><span class="sxs-lookup"><span data-stu-id="5762d-105">This topic demonstrates how to set properties on the binding elements to create a custom binding.</span></span>  
  
 <span data-ttu-id="5762d-106">有关如何在不使用系统提供的绑定的情况下直接创建和配置绑定元素的更多信息，请参见 [自定义绑定](custom-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="5762d-106">For more information about how to directly create and configure binding elements without using the system-provided bindings, see [Custom Bindings](custom-bindings.md).</span></span>  
  
 <span data-ttu-id="5762d-107">有关创建和扩展自定义绑定的详细信息，请参阅 [扩展绑定](extending-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="5762d-107">For more information about creating and extending custom bindings, see [Extending Bindings](extending-bindings.md).</span></span>  
  
 <span data-ttu-id="5762d-108">在 WCF 中，所有绑定都由 *绑定元素* 组成。</span><span class="sxs-lookup"><span data-stu-id="5762d-108">In WCF all bindings are made up of *binding elements*.</span></span> <span data-ttu-id="5762d-109">每个绑定元素都是从 <xref:System.ServiceModel.Channels.BindingElement> 类派生的。</span><span class="sxs-lookup"><span data-stu-id="5762d-109">Each binding element derives from the <xref:System.ServiceModel.Channels.BindingElement> class.</span></span> <span data-ttu-id="5762d-110">系统提供的绑定（如 <xref:System.ServiceModel.BasicHttpBinding>）可创建和配置各自的绑定元素。</span><span class="sxs-lookup"><span data-stu-id="5762d-110">System-provided bindings such as <xref:System.ServiceModel.BasicHttpBinding> create and configure their own binding elements.</span></span> <span data-ttu-id="5762d-111">本主题演示如何访问和更改这些绑定元素的属性，这些属性不会直接在绑定上公开，具体而言，这些属性不会直接在 <xref:System.ServiceModel.BasicHttpBinding> 类上公开。</span><span class="sxs-lookup"><span data-stu-id="5762d-111">This topic shows you how to access and change the properties of these binding elements, which are not directly exposed on the binding; specifically, the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="5762d-112">各个绑定元素都包含在由 <xref:System.ServiceModel.Channels.BindingElementCollection> 类表示的集合中，并按如下顺序添加：事务流、可靠会话、安全、复合双工、单向、流安全、消息编码和传输协议。</span><span class="sxs-lookup"><span data-stu-id="5762d-112">The individual binding elements are contained in a collection represented by the <xref:System.ServiceModel.Channels.BindingElementCollection> class and are added in this order: Transaction Flow, Reliable Session, Security, Composite Duplex, One-way, Stream Security, Message Encoding, and Transport.</span></span> <span data-ttu-id="5762d-113">请注意，并不是每个绑定中都需要所列的所有绑定元素。</span><span class="sxs-lookup"><span data-stu-id="5762d-113">Note that not all the binding elements listed are required in every binding.</span></span> <span data-ttu-id="5762d-114">用户定义的绑定元素也可以出现在此绑定元素集合中，但必须按前面所述的相同顺序出现。</span><span class="sxs-lookup"><span data-stu-id="5762d-114">User-defined binding elements can also appear in this binding element collection and must appear in the same order as previously described.</span></span> <span data-ttu-id="5762d-115">例如，用户定义的传输协议必须为绑定元素集合中的最后一个元素。</span><span class="sxs-lookup"><span data-stu-id="5762d-115">For example, a user-defined transport must be the last element of the binding element collection.</span></span>  
  
 <span data-ttu-id="5762d-116"><xref:System.ServiceModel.BasicHttpBinding> 类包含三个绑定元素：</span><span class="sxs-lookup"><span data-stu-id="5762d-116">The <xref:System.ServiceModel.BasicHttpBinding> class contains three binding elements:</span></span>  
  
1. <span data-ttu-id="5762d-117">可选的安全绑定元素，即，与 HTTP 传输协议（消息级安全）一起使用的 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> 类，或在传输协议层提供安全性时使用的 <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> 类（这种情况下将使用 HTTPS 传输协议）。</span><span class="sxs-lookup"><span data-stu-id="5762d-117">An optional security binding element, either the <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> class used with the HTTP transport (message level security) or the <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> class, which is used when the transport layer provides security, in which case the HTTPS transport is used.</span></span>  
  
2. <span data-ttu-id="5762d-118">必需的消息编码器绑定元素，即，<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> 或 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="5762d-118">A required message encoder binding element, either <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> or <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>.</span></span>  
  
3. <span data-ttu-id="5762d-119">必需的传输绑定元素，即，<xref:System.ServiceModel.Channels.HttpTransportBindingElement> 或 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="5762d-119">A required transport binding element, either <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, or <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>.</span></span>  
  
 <span data-ttu-id="5762d-120">在此示例中，我们将创建绑定的一个实例，根据其生成 *自定义绑定* ，检查自定义绑定中的绑定元素，并在找到 HTTP 绑定元素时将其 `KeepAliveEnabled` 属性设置为 `false` 。</span><span class="sxs-lookup"><span data-stu-id="5762d-120">In this example we create an instance of the binding, generate a *custom binding* from it, examine the binding elements in the custom binding, and when we find the HTTP binding element, we set its `KeepAliveEnabled` property to `false`.</span></span> <span data-ttu-id="5762d-121">由于在 `KeepAliveEnabled` 上未直接公开 `BasicHttpBinding` 属性，因此必须创建一个自定义绑定以向下导航至绑定元素，并设置此属性。</span><span class="sxs-lookup"><span data-stu-id="5762d-121">The `KeepAliveEnabled` property is not exposed directly on the `BasicHttpBinding`, so we must create a custom binding to navigate down to the binding element and set this property.</span></span>  
  
### <a name="to-modify-a-system-provided-binding"></a><span data-ttu-id="5762d-122">修改系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="5762d-122">To modify a system-provided binding</span></span>  
  
1. <span data-ttu-id="5762d-123">创建 <xref:System.ServiceModel.BasicHttpBinding> 类的一个实例，并将其安全模式设置为消息级。</span><span class="sxs-lookup"><span data-stu-id="5762d-123">Create an instance of the <xref:System.ServiceModel.BasicHttpBinding> class and set its security mode to message-level.</span></span>  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#1)]
     [!code-vb[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#1)]  
  
2. <span data-ttu-id="5762d-124">从该绑定创建一个自定义绑定，并从该自定义绑定的一个属性创建 <xref:System.ServiceModel.Channels.BindingElementCollection> 类。</span><span class="sxs-lookup"><span data-stu-id="5762d-124">Create a custom binding from the binding and create a <xref:System.ServiceModel.Channels.BindingElementCollection> class from one of the custom binding's properties.</span></span>  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#2)]
     [!code-vb[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#2)]  
  
3. <span data-ttu-id="5762d-125">循环通过 <xref:System.ServiceModel.Channels.BindingElementCollection> 类，并在查找 <xref:System.ServiceModel.Channels.HttpTransportBindingElement> 类时，将其 <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> 属性设置为 `false`。</span><span class="sxs-lookup"><span data-stu-id="5762d-125">Loop through the <xref:System.ServiceModel.Channels.BindingElementCollection> class, and when you find the <xref:System.ServiceModel.Channels.HttpTransportBindingElement> class, set its <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> property to `false`.</span></span>  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#3)]
     [!code-vb[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="5762d-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="5762d-126">See also</span></span>

- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="5762d-127">自定义绑定</span><span class="sxs-lookup"><span data-stu-id="5762d-127">Custom Bindings</span></span>](custom-bindings.md)
