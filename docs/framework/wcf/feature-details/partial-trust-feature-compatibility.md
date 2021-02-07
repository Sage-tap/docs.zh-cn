---
description: 了解详细信息：部分信任功能兼容性
title: 部分信任功能兼容性
ms.date: 03/30/2017
ms.assetid: a36a540b-1606-4e63-88e0-b7c59e0e6ab7
ms.openlocfilehash: 470cedde3eb38508feb1c2950f7f504390914834
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99733523"
---
# <a name="partial-trust-feature-compatibility"></a><span data-ttu-id="2770f-103">部分信任功能兼容性</span><span class="sxs-lookup"><span data-stu-id="2770f-103">Partial Trust Feature Compatibility</span></span>

<span data-ttu-id="2770f-104">在部分受信任的环境中运行时，Windows Communication Foundation (WCF) 支持有限的功能子集。</span><span class="sxs-lookup"><span data-stu-id="2770f-104">Windows Communication Foundation (WCF) supports a limited subset of functionality when running in a partially-trusted environment.</span></span> <span data-ttu-id="2770f-105">部分信任中支持的功能围绕 [Supported Deployment Scenarios](supported-deployment-scenarios.md) 主题中所述的一组特定的方案而设计。</span><span class="sxs-lookup"><span data-stu-id="2770f-105">The features supported in partial trust are designed around a specific set of scenarios as described in the [Supported Deployment Scenarios](supported-deployment-scenarios.md) topic.</span></span>  
  
## <a name="minimum-permission-requirements"></a><span data-ttu-id="2770f-106">最低权限要求</span><span class="sxs-lookup"><span data-stu-id="2770f-106">Minimum Permission Requirements</span></span>  

 <span data-ttu-id="2770f-107">WCF 支持在以下任一标准命名权限集下运行的应用程序中的功能子集：</span><span class="sxs-lookup"><span data-stu-id="2770f-107">WCF supports a subset of features in applications running under either of the following standard named permission sets:</span></span>  
  
- <span data-ttu-id="2770f-108">“中等信任”权限</span><span class="sxs-lookup"><span data-stu-id="2770f-108">Medium Trust permissions</span></span>  
  
- <span data-ttu-id="2770f-109">“Internet 区域”权限</span><span class="sxs-lookup"><span data-stu-id="2770f-109">Internet Zone permissions</span></span>  
  
 <span data-ttu-id="2770f-110">如果尝试在部分受信任的应用程序中使用 WCF 并且具有更严格的权限，则可能会在运行时导致安全异常。</span><span class="sxs-lookup"><span data-stu-id="2770f-110">Attempting to use WCF in partially-trusted applications with more restrictive permissions may result in security exceptions at runtime.</span></span>  
  
## <a name="contracts"></a><span data-ttu-id="2770f-111">协定</span><span class="sxs-lookup"><span data-stu-id="2770f-111">Contracts</span></span>  

 <span data-ttu-id="2770f-112">在部分信任环境下运行时，协定受到以下限制：</span><span class="sxs-lookup"><span data-stu-id="2770f-112">Contracts are subject to the following restrictions when running under partial trust:</span></span>  
  
- <span data-ttu-id="2770f-113">实现 `[ServiceContract]` 接口的服务类必须为 `public` 类，且必须有一个 `public` 构造函数。</span><span class="sxs-lookup"><span data-stu-id="2770f-113">The service class that implements the `[ServiceContract]` interface must be `public` and have a `public` constructor.</span></span> <span data-ttu-id="2770f-114">如果该服务类定义 `[OperationContract]` 方法，则这些方法必须为 `public`方法。</span><span class="sxs-lookup"><span data-stu-id="2770f-114">If it defines `[OperationContract]` methods, these must be `public`.</span></span> <span data-ttu-id="2770f-115">如果该服务类实现 `[ServiceContract]` 接口，且 `private`接口为 `[ServiceContract]` 接口，则这些方法实现可以为显式实现或 `public`实现。</span><span class="sxs-lookup"><span data-stu-id="2770f-115">If it instead implements a `[ServiceContract]` interface, those method implementations can be explicit or `private`, provided that the `[ServiceContract]` interface is `public`.</span></span>  
  
- <span data-ttu-id="2770f-116">在使用 `[ServiceKnownType]` 属性时，指定的方法必须为 `public`方法。</span><span class="sxs-lookup"><span data-stu-id="2770f-116">When using the `[ServiceKnownType]` attribute, the method specified must be `public`.</span></span>  
  
- <span data-ttu-id="2770f-117">`[MessageContract]` 类及其成员可以为 `public`。</span><span class="sxs-lookup"><span data-stu-id="2770f-117">`[MessageContract]` classes and their members can be `public`.</span></span> <span data-ttu-id="2770f-118">如果 `[MessageContract]` 类是在应用程序程序集中定义的，则该类可以为 `internal` 类并拥有 `internal` 成员。</span><span class="sxs-lookup"><span data-stu-id="2770f-118">If the `[MessageContract]` class is defined in the application assembly it can be `internal` and have `internal` members.</span></span>  
  
## <a name="system-provided-bindings"></a><span data-ttu-id="2770f-119">系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="2770f-119">System-Provided Bindings</span></span>  

 <span data-ttu-id="2770f-120">在部分信任环境中完全支持 <xref:System.ServiceModel.BasicHttpBinding> 和 <xref:System.ServiceModel.WebHttpBinding> 。</span><span class="sxs-lookup"><span data-stu-id="2770f-120">The <xref:System.ServiceModel.BasicHttpBinding> and <xref:System.ServiceModel.WebHttpBinding> are fully supported in a partial trust environment.</span></span> <span data-ttu-id="2770f-121">仅对传输安全模式支持 <xref:System.ServiceModel.WSHttpBinding> 。</span><span class="sxs-lookup"><span data-stu-id="2770f-121">The <xref:System.ServiceModel.WSHttpBinding> is supported for Transport security mode only.</span></span>  
  
 <span data-ttu-id="2770f-122">在部分信任环境中运行时，不支持使用除 HTTP 之外的传输的绑定（例如 <xref:System.ServiceModel.NetTcpBinding>、 <xref:System.ServiceModel.NetNamedPipeBinding>或 <xref:System.ServiceModel.NetMsmqBinding>）。</span><span class="sxs-lookup"><span data-stu-id="2770f-122">Bindings that use transports other than HTTP, such as the <xref:System.ServiceModel.NetTcpBinding>, the <xref:System.ServiceModel.NetNamedPipeBinding>, or the <xref:System.ServiceModel.NetMsmqBinding>, are not supported when running in a partial trust environment.</span></span>  
  
## <a name="custom-bindings"></a><span data-ttu-id="2770f-123">自定义绑定</span><span class="sxs-lookup"><span data-stu-id="2770f-123">Custom Bindings</span></span>  

 <span data-ttu-id="2770f-124">在部分信任环境中可以创建和使用自定义绑定，但必须遵循本节中指定的限制。</span><span class="sxs-lookup"><span data-stu-id="2770f-124">Custom bindings can be created and used in a partial trust environment, but must follow the restrictions specified in this section.</span></span>  
  
### <a name="transports"></a><span data-ttu-id="2770f-125">传输</span><span class="sxs-lookup"><span data-stu-id="2770f-125">Transports</span></span>  

 <span data-ttu-id="2770f-126">允许的传输绑定元素仅为 <xref:System.ServiceModel.Channels.HttpTransportBindingElement> 和 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="2770f-126">The only allowed transport binding elements are <xref:System.ServiceModel.Channels.HttpTransportBindingElement> and <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>.</span></span>  
  
### <a name="encoders"></a><span data-ttu-id="2770f-127">编码器</span><span class="sxs-lookup"><span data-stu-id="2770f-127">Encoders</span></span>  

 <span data-ttu-id="2770f-128">允许以下编码器：</span><span class="sxs-lookup"><span data-stu-id="2770f-128">The following encoders are allowed:</span></span>  
  
- <span data-ttu-id="2770f-129">文本编码器 (<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>)。</span><span class="sxs-lookup"><span data-stu-id="2770f-129">The text encoder (<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>).</span></span>  
  
- <span data-ttu-id="2770f-130">二进制编码器 (<xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>)。</span><span class="sxs-lookup"><span data-stu-id="2770f-130">The binary encoder (<xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>).</span></span>  
  
- <span data-ttu-id="2770f-131">Web 消息编码器 (<xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>)。</span><span class="sxs-lookup"><span data-stu-id="2770f-131">The Web Message encoder (<xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>).</span></span>  
  
 <span data-ttu-id="2770f-132">不支持消息传输优化机制 (MTOM) 编码器。</span><span class="sxs-lookup"><span data-stu-id="2770f-132">The Message Transmission Optimization Mechanism (MTOM) encoders are not supported.</span></span>  
  
### <a name="security"></a><span data-ttu-id="2770f-133">安全</span><span class="sxs-lookup"><span data-stu-id="2770f-133">Security</span></span>  

 <span data-ttu-id="2770f-134">部分受信任的应用程序可以使用 WCF 的传输级安全功能来保护其通信。</span><span class="sxs-lookup"><span data-stu-id="2770f-134">Partially-trusted applications can use WCF's transport-level security features for securing their communication.</span></span> <span data-ttu-id="2770f-135">不支持消息级安全。</span><span class="sxs-lookup"><span data-stu-id="2770f-135">Message-level security is not supported.</span></span> <span data-ttu-id="2770f-136">将绑定配置为使用消息级别的安全会在运行时导致异常。</span><span class="sxs-lookup"><span data-stu-id="2770f-136">Configuring a binding to use message-level security results in an exception at runtime.</span></span>  
  
### <a name="unsupported-bindings"></a><span data-ttu-id="2770f-137">不支持的绑定</span><span class="sxs-lookup"><span data-stu-id="2770f-137">Unsupported Bindings</span></span>  

 <span data-ttu-id="2770f-138">不支持使用可靠消息传递、事务或消息级安全的绑定。</span><span class="sxs-lookup"><span data-stu-id="2770f-138">Bindings that use reliable messaging, transactions, or message-level security are not supported.</span></span>  
  
## <a name="serialization"></a><span data-ttu-id="2770f-139">序列化</span><span class="sxs-lookup"><span data-stu-id="2770f-139">Serialization</span></span>  

 <span data-ttu-id="2770f-140">在部分信任环境中支持 <xref:System.Runtime.Serialization.DataContractSerializer> 和 <xref:System.Xml.Serialization.XmlSerializer> 。</span><span class="sxs-lookup"><span data-stu-id="2770f-140">Both the <xref:System.Runtime.Serialization.DataContractSerializer> and the <xref:System.Xml.Serialization.XmlSerializer> are supported in a partial trust environment.</span></span> <span data-ttu-id="2770f-141">但是，使用 <xref:System.Runtime.Serialization.DataContractSerializer> 时需要遵循以下条件：</span><span class="sxs-lookup"><span data-stu-id="2770f-141">However, use of the <xref:System.Runtime.Serialization.DataContractSerializer> is subject to the following conditions:</span></span>  
  
- <span data-ttu-id="2770f-142">所有可序列化的 `[DataContract]` 类型必须为 `public`。</span><span class="sxs-lookup"><span data-stu-id="2770f-142">All serializable `[DataContract]` types must be `public`.</span></span>  
  
- <span data-ttu-id="2770f-143">`[DataMember]` 类型中的所有可序列化的 `[DataContract]` 字段或属性必须是公共字段或属性并且可以读取/写入。</span><span class="sxs-lookup"><span data-stu-id="2770f-143">All serializable `[DataMember]` fields or properties in a `[DataContract]` type must be public and read/write.</span></span> <span data-ttu-id="2770f-144">在部分受信任的应用程序中运行 WCF 时，不支持 [只读](https://go.microsoft.com/fwlink/?LinkID=98854) 字段的序列化和反序列化。</span><span class="sxs-lookup"><span data-stu-id="2770f-144">The serialization and deserialization of [readonly](https://go.microsoft.com/fwlink/?LinkID=98854) fields is not supported when running WCF in a partially-trusted application.</span></span>  
  
- <span data-ttu-id="2770f-145">在部分信任环境中， `[Serializable]`/ISerializable 编程模型不受支持。</span><span class="sxs-lookup"><span data-stu-id="2770f-145">The `[Serializable]`/ISerializable programming model is not supported in a partial trust environment.</span></span>  
  
- <span data-ttu-id="2770f-146">必须在代码或计算机级别配置 (machine.config) 中指定已知类型。</span><span class="sxs-lookup"><span data-stu-id="2770f-146">Known types must be specified in code or machine-level configuration (machine.config).</span></span> <span data-ttu-id="2770f-147">出于安全方面的原因，不能在应用程序级配置中指定已知类型。</span><span class="sxs-lookup"><span data-stu-id="2770f-147">Known types cannot be specified in application-level configuration for security reasons.</span></span>  
  
- <span data-ttu-id="2770f-148">实现 <xref:System.Runtime.Serialization.IObjectReference> 的类型在部分受信任的环境中会引发异常。</span><span class="sxs-lookup"><span data-stu-id="2770f-148">Types that implement <xref:System.Runtime.Serialization.IObjectReference> throw an exception in a partially-trusted environment.</span></span>  
  
 <span data-ttu-id="2770f-149">有关在部分受信任的应用程序中安全使用 [T:System.Runtime.Serialization.DataContractSerializer](partial-trust-best-practices.md) 的更多安全信息，请参见 <xref:System.Runtime.Serialization.DataContractSerializer> 中的“序列化”一节。</span><span class="sxs-lookup"><span data-stu-id="2770f-149">See the Serialization section in [Partial Trust Best Practices](partial-trust-best-practices.md) for more information about security when using <xref:System.Runtime.Serialization.DataContractSerializer> safely in a partially-trusted application.</span></span>  
  
### <a name="collection-types"></a><span data-ttu-id="2770f-150">集合类型</span><span class="sxs-lookup"><span data-stu-id="2770f-150">Collection Types</span></span>  

 <span data-ttu-id="2770f-151">一些集合类型可实现 <xref:System.Collections.Generic.IEnumerable%601> 和 <xref:System.Collections.IEnumerable>。</span><span class="sxs-lookup"><span data-stu-id="2770f-151">Some collection types implement both <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="2770f-152">示例包括实现 <xref:System.Collections.Generic.ICollection%601>的类型。</span><span class="sxs-lookup"><span data-stu-id="2770f-152">Examples include types that implement <xref:System.Collections.Generic.ICollection%601>.</span></span> <span data-ttu-id="2770f-153">这些类型可以实现 `public` 的 `GetEnumerator()`实现和 `GetEnumerator()`的显式实现。</span><span class="sxs-lookup"><span data-stu-id="2770f-153">Such types can implement a `public` implementation of `GetEnumerator()`, and an explicit implementation of `GetEnumerator()`.</span></span> <span data-ttu-id="2770f-154">在此情况下， <xref:System.Runtime.Serialization.DataContractSerializer> 调用 `public` 的 `GetEnumerator()`，而不调用 `GetEnumerator()`的显式实现。</span><span class="sxs-lookup"><span data-stu-id="2770f-154">In this case, <xref:System.Runtime.Serialization.DataContractSerializer> invokes the `public` implementation of `GetEnumerator()`, and not the explicit implementation of `GetEnumerator()`.</span></span> <span data-ttu-id="2770f-155">如果所有 `GetEnumerator()` 实现都不是 `public` 而全部是显式实现，则 <xref:System.Runtime.Serialization.DataContractSerializer> 调用 `IEnumerable.GetEnumerator()`。</span><span class="sxs-lookup"><span data-stu-id="2770f-155">If none of the `GetEnumerator()` implementations are `public` and all are explicit implementations, then <xref:System.Runtime.Serialization.DataContractSerializer> invokes `IEnumerable.GetEnumerator()`.</span></span>  
  
 <span data-ttu-id="2770f-156">对于集合类型，当在部分信任环境中运行 WCF 时，如果没有任何 `GetEnumerator()` 实现 `public` ，或者它们都不是显式接口实现，则引发安全异常。</span><span class="sxs-lookup"><span data-stu-id="2770f-156">For collection types when WCF is running in a partial trust environment, if none of the `GetEnumerator()` implementations are `public`, or none of them are explicit interface implementations, then a security exception is thrown.</span></span>  
  
### <a name="netdatacontractserializer"></a><span data-ttu-id="2770f-157">NetDataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="2770f-157">NetDataContractSerializer</span></span>  

 <span data-ttu-id="2770f-158">在部分信任环境中， <xref:System.Collections.Generic.List%601>不支持许多 .NET Framework 集合类型，如 <xref:System.Collections.ArrayList>、 <xref:System.Collections.Generic.Dictionary%602> 、 <xref:System.Collections.Hashtable> 和 <xref:System.Runtime.Serialization.NetDataContractSerializer> 。</span><span class="sxs-lookup"><span data-stu-id="2770f-158">Many .NET Framework collection types such as <xref:System.Collections.Generic.List%601>, <xref:System.Collections.ArrayList>, <xref:System.Collections.Generic.Dictionary%602> and <xref:System.Collections.Hashtable> are not supported by the <xref:System.Runtime.Serialization.NetDataContractSerializer> in partial trust.</span></span> <span data-ttu-id="2770f-159">这些类型设置了 `[Serializable]` 属性，如前面“序列化”一节中所述，此属性在部分信任环境中不受支持。</span><span class="sxs-lookup"><span data-stu-id="2770f-159">These types have the `[Serializable]` attribute set, and as stated previously in the Serialization section, this attribute is not supported in partial trust.</span></span> <span data-ttu-id="2770f-160"><xref:System.Runtime.Serialization.DataContractSerializer> 以特殊方式处理集合，因而能够避开此限制， <xref:System.Runtime.Serialization.NetDataContractSerializer> 没有这类机制可避开此限制。</span><span class="sxs-lookup"><span data-stu-id="2770f-160">The <xref:System.Runtime.Serialization.DataContractSerializer> treats collections in a special way and is thus able to get around this restriction, but the <xref:System.Runtime.Serialization.NetDataContractSerializer> has no such mechanism to circumvent this restriction.</span></span>  
  
 <span data-ttu-id="2770f-161">在部分信任环境中， <xref:System.DateTimeOffset> 不支持 <xref:System.Runtime.Serialization.NetDataContractSerializer> 类型。</span><span class="sxs-lookup"><span data-stu-id="2770f-161">The <xref:System.DateTimeOffset> type is not supported by the <xref:System.Runtime.Serialization.NetDataContractSerializer> in partial trust.</span></span>  
  
 <span data-ttu-id="2770f-162">在部分信任环境中运行时，无法将代理项用于 <xref:System.Runtime.Serialization.NetDataContractSerializer> （使用 <xref:System.Runtime.Serialization.SurrogateSelector> 机制）。</span><span class="sxs-lookup"><span data-stu-id="2770f-162">A surrogate cannot be used with the <xref:System.Runtime.Serialization.NetDataContractSerializer> (using the <xref:System.Runtime.Serialization.SurrogateSelector> mechanism) when running in partial trust.</span></span> <span data-ttu-id="2770f-163">请注意，此限制适用于使用代理项，而不适用于序列化代理项。</span><span class="sxs-lookup"><span data-stu-id="2770f-163">Note that this restriction applies to using a surrogate, not to serializing it.</span></span>  
  
## <a name="enabling-common-behaviors-to-run"></a><span data-ttu-id="2770f-164">使常见行为能够运行</span><span class="sxs-lookup"><span data-stu-id="2770f-164">Enabling Common Behaviors to Run</span></span>  

 <span data-ttu-id="2770f-165"><xref:System.Security.AllowPartiallyTrustedCallersAttribute> [\<commonBehaviors>](../../configure-apps/file-schema/wcf/commonbehaviors.md) 当应用程序在部分信任环境中运行时，未使用特性标记的服务或终结点行为将不会运行，如果应用程序在部分信任环境中运行，则不会运行添加到配置文件的部分中的)  (属性，并且在发生这种情况时</span><span class="sxs-lookup"><span data-stu-id="2770f-165">Service or endpoint behaviors not marked with the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute (APTCA) that are added to the [\<commonBehaviors>](../../configure-apps/file-schema/wcf/commonbehaviors.md) section of a configuration file are not run when the application runs in a partial trust environment and no exception is thrown when this occurs.</span></span> <span data-ttu-id="2770f-166">若要强制运行常见行为，必须执行下列选项之一：</span><span class="sxs-lookup"><span data-stu-id="2770f-166">To enforce the running of common behaviors, you must do one of the following options:</span></span>  
  
- <span data-ttu-id="2770f-167">使用 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 属性标记常见行为，以使其在部署为部分信任应用程序时能够运行。</span><span class="sxs-lookup"><span data-stu-id="2770f-167">Mark your common behavior with the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute so that it can run when deployed as a partial trust application.</span></span> <span data-ttu-id="2770f-168">请注意，可以在计算机上设置注册表项，以防运行标有 APTCA 的程序集。</span><span class="sxs-lookup"><span data-stu-id="2770f-168">Note that a registry entry can be set on the computer to prevent APTCA-marked assemblies from running.</span></span> <span data-ttu-id="2770f-169">.</span><span class="sxs-lookup"><span data-stu-id="2770f-169">.</span></span>  
  
- <span data-ttu-id="2770f-170">确保在将应用程序作为完全受信任的应用程序部署时，用户不能修改代码访问安全设置，从而无法在部分信任环境中运行该应用程序。</span><span class="sxs-lookup"><span data-stu-id="2770f-170">Ensure that if the application is deployed as a fully-trusted application that users cannot modify the code-access security settings to run the application in a partial trust environment.</span></span> <span data-ttu-id="2770f-171">如果用户可以这样做，则不会运行该行为，且不引发任何异常。</span><span class="sxs-lookup"><span data-stu-id="2770f-171">If they can do so, the behavior does not run and no exception is thrown.</span></span> <span data-ttu-id="2770f-172">若要确保这一点，请参阅使用 [Caspol.exe (代码访问安全策略工具)](../../tools/caspol-exe-code-access-security-policy-tool.md)中的 **levelfinal** 选项。</span><span class="sxs-lookup"><span data-stu-id="2770f-172">To ensure this, see the **levelfinal** option using [Caspol.exe (Code Access Security Policy Tool)](../../tools/caspol-exe-code-access-security-policy-tool.md).</span></span>  
  
 <span data-ttu-id="2770f-173">有关常见行为的示例，请参阅 [如何：锁定企业中的终结点](../extending/how-to-lock-down-endpoints-in-the-enterprise.md)。</span><span class="sxs-lookup"><span data-stu-id="2770f-173">For an example of a common behavior, see [How to: Lock Down Endpoints in the Enterprise](../extending/how-to-lock-down-endpoints-in-the-enterprise.md).</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="2770f-174">Configuration</span><span class="sxs-lookup"><span data-stu-id="2770f-174">Configuration</span></span>  

 <span data-ttu-id="2770f-175">有一个例外，部分受信任的代码只能加载本地文件中的 WCF 配置节 `app.config` 。</span><span class="sxs-lookup"><span data-stu-id="2770f-175">With one exception, partially-trusted code can only load WCF configuration sections in the local `app.config` file.</span></span> <span data-ttu-id="2770f-176">若要加载引用 machine.config 或根 web.config 文件中的 WCF 部分的 WCF 配置节，需要 ConfigurationPermission (无限制的) 。</span><span class="sxs-lookup"><span data-stu-id="2770f-176">To load WCF configuration sections that reference WCF sections in machine.config or in a root web.config file requires ConfigurationPermission(Unrestricted).</span></span> <span data-ttu-id="2770f-177">如果没有此权限，则在加载配置时，对 WCF 配置节 (行为、绑定) 在本地配置文件之外的绑定将导致异常。</span><span class="sxs-lookup"><span data-stu-id="2770f-177">Without this permission, references to WCF configuration sections (behaviors, bindings) outside of the local configuration file results in an exception when the configuration is loaded.</span></span>  
  
 <span data-ttu-id="2770f-178">一个例外情况是序列化的已知类型配置，如本主题中的“序列化”一节所述。</span><span class="sxs-lookup"><span data-stu-id="2770f-178">The one exception is known-type configuration for serialization, as described in the Serialization section of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2770f-179">仅当在完全信任环境下运行时，才支持配置扩展。</span><span class="sxs-lookup"><span data-stu-id="2770f-179">Configuration extensions are only supported when running under Full Trust.</span></span>  
  
## <a name="diagnostics"></a><span data-ttu-id="2770f-180">诊断</span><span class="sxs-lookup"><span data-stu-id="2770f-180">Diagnostics</span></span>  
  
### <a name="event-logging"></a><span data-ttu-id="2770f-181">事件日志记录</span><span class="sxs-lookup"><span data-stu-id="2770f-181">Event Logging</span></span>  

 <span data-ttu-id="2770f-182">部分信任环境下支持有限的事件日志记录。</span><span class="sxs-lookup"><span data-stu-id="2770f-182">Limited event logging is supported under partial trust.</span></span> <span data-ttu-id="2770f-183">事件日志中仅记录服务激活错误和跟踪/消息日志记录错误。</span><span class="sxs-lookup"><span data-stu-id="2770f-183">Only service activation faults and tracing/message logging failures are logged to the Event Log.</span></span> <span data-ttu-id="2770f-184">为了避免向事件日志写入过多消息，一个进程最多可以记录 5 个事件。</span><span class="sxs-lookup"><span data-stu-id="2770f-184">The maximum number of events that can be logged by a process is 5, to avoid writing excessive messages to the Event Log.</span></span>  
  
### <a name="message-logging"></a><span data-ttu-id="2770f-185">消息日志记录</span><span class="sxs-lookup"><span data-stu-id="2770f-185">Message Logging</span></span>  

 <span data-ttu-id="2770f-186">在部分信任环境中运行 WCF 时，消息日志记录不起作用。</span><span class="sxs-lookup"><span data-stu-id="2770f-186">Message logging does not work when WCF is run in a partial trust environment.</span></span> <span data-ttu-id="2770f-187">如果在部分信任下启用消息日志记录，不会出现服务激活失败，但不记录消息。</span><span class="sxs-lookup"><span data-stu-id="2770f-187">If enabled under partial trust, it does not fail service activation, but no message is logged.</span></span>  
  
### <a name="tracing"></a><span data-ttu-id="2770f-188">跟踪</span><span class="sxs-lookup"><span data-stu-id="2770f-188">Tracing</span></span>  

 <span data-ttu-id="2770f-189">在部分信任环境中运行时可使用有限的跟踪功能。</span><span class="sxs-lookup"><span data-stu-id="2770f-189">Restricted tracing functionality is available when running in a partial trust environment.</span></span> <span data-ttu-id="2770f-190">在 `listeners` 配置文件中 <> 元素中，唯一可以添加的类型是 <xref:System.Diagnostics.TextWriterTraceListener> 和新的 <xref:System.Diagnostics.EventSchemaTraceListener> 。</span><span class="sxs-lookup"><span data-stu-id="2770f-190">In the <`listeners`> element in the configuration file, the only types that you can add are <xref:System.Diagnostics.TextWriterTraceListener> and the new <xref:System.Diagnostics.EventSchemaTraceListener>.</span></span> <span data-ttu-id="2770f-191">使用标准的 <xref:System.Diagnostics.XmlWriterTraceListener> 可能会造成日志不完整或不正确。</span><span class="sxs-lookup"><span data-stu-id="2770f-191">Use of the standard <xref:System.Diagnostics.XmlWriterTraceListener> may result in incomplete or incorrect logs.</span></span>  
  
 <span data-ttu-id="2770f-192">支持的跟踪源有：</span><span class="sxs-lookup"><span data-stu-id="2770f-192">Supported trace sources are:</span></span>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.Runtime.Serialization>  
  
- <span data-ttu-id="2770f-193"><xref:System.IdentityModel.Claims>、<xref:System.IdentityModel.Policy>、<xref:System.IdentityModel.Selectors> 和 <xref:System.IdentityModel.Tokens>。</span><span class="sxs-lookup"><span data-stu-id="2770f-193"><xref:System.IdentityModel.Claims>, <xref:System.IdentityModel.Policy>, <xref:System.IdentityModel.Selectors>, and <xref:System.IdentityModel.Tokens>.</span></span>  
  
 <span data-ttu-id="2770f-194">不支持下面的跟踪源：</span><span class="sxs-lookup"><span data-stu-id="2770f-194">The following trace sources are not supported:</span></span>  
  
- <span data-ttu-id="2770f-195">CardSpace</span><span class="sxs-lookup"><span data-stu-id="2770f-195">CardSpace</span></span>  
  
- <xref:System.IO.Log>  

- <span data-ttu-id="2770f-196">[System.servicemodel. TransactionBridge](/previous-versions/aa346556(v=vs.110))]</span><span class="sxs-lookup"><span data-stu-id="2770f-196">[System.ServiceModel.Internal.TransactionBridge](/previous-versions/aa346556(v=vs.110))]</span></span>
  
 <span data-ttu-id="2770f-197">不应指定下面的 <xref:System.Diagnostics.TraceOptions> 枚举成员：</span><span class="sxs-lookup"><span data-stu-id="2770f-197">The following members of the <xref:System.Diagnostics.TraceOptions> enumeration should not be specified:</span></span>  
  
- <xref:System.Diagnostics.TraceOptions.Callstack?displayProperty=nameWithType>  
  
- <xref:System.Diagnostics.TraceOptions.ProcessId?displayProperty=nameWithType>  
  
 <span data-ttu-id="2770f-198">在部分信任环境中使用跟踪时，应确保应用程序具有足够的权限来存储跟踪侦听器的输出。</span><span class="sxs-lookup"><span data-stu-id="2770f-198">When using tracing in a partial trust environment, ensure that the application has sufficient permissions to store the output of the trace listener.</span></span> <span data-ttu-id="2770f-199">例如，在使用 <xref:System.Diagnostics.TextWriterTraceListener> 将跟踪输出写入到文本文件中时，应确保应用程序具有成功写入到跟踪文件中所需的必要的 FileIOPermission。</span><span class="sxs-lookup"><span data-stu-id="2770f-199">For example, when using the <xref:System.Diagnostics.TextWriterTraceListener> to write trace output to a text file, ensure that the application has the necessary FileIOPermission required to successfully write to the trace file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2770f-200">若要避免在出现重复错误时扩散跟踪文件，WCF 在第一次安全失败之后禁用资源或操作跟踪。</span><span class="sxs-lookup"><span data-stu-id="2770f-200">To avoid flooding the trace files with duplicate errors, WCF disables tracing of the resource or action after the first security failure.</span></span> <span data-ttu-id="2770f-201">对于在第一次尝试访问资源或执行操作时出现的每个失败的资源访问，将会有一个异常跟踪。</span><span class="sxs-lookup"><span data-stu-id="2770f-201">There is one exception trace for each failed resource access, the first time an attempt is made to access the resource or perform the action.</span></span>  
  
## <a name="wcf-service-host"></a><span data-ttu-id="2770f-202">WCF 服务主机</span><span class="sxs-lookup"><span data-stu-id="2770f-202">WCF Service Host</span></span>  

 <span data-ttu-id="2770f-203">WCF 服务主机不支持部分信任。</span><span class="sxs-lookup"><span data-stu-id="2770f-203">WCF service host does not support partial trust.</span></span> <span data-ttu-id="2770f-204">如果要在部分信任环境中使用 WCF 服务，请不要使用 Visual Studio 中的 WCF 服务库项目模板生成服务。</span><span class="sxs-lookup"><span data-stu-id="2770f-204">If you want to use a WCF service in partial trust, do not use the WCF Service Library Project template in Visual Studio to build your service.</span></span> <span data-ttu-id="2770f-205">而是在 Visual Studio 中创建一个新网站，方法是选择 "WCF 服务" 网站模板，该模板可以在支持 WCF 部分信任的 Web 服务器中承载服务。</span><span class="sxs-lookup"><span data-stu-id="2770f-205">Instead, create a new Web site in Visual Studio by choosing the WCF service Web site template, which can host the service in a Web server on which WCF partial trust is supported.</span></span>  
  
## <a name="other-limitations"></a><span data-ttu-id="2770f-206">其他限制</span><span class="sxs-lookup"><span data-stu-id="2770f-206">Other Limitations</span></span>  

  <span data-ttu-id="2770f-207">WCF 通常仅限于由宿主应用程序施加的安全注意事项。</span><span class="sxs-lookup"><span data-stu-id="2770f-207">WCF is generally limited to the security considerations imposed upon it by the hosting application.</span></span> <span data-ttu-id="2770f-208">例如，如果 WCF 承载于 XAML 浏览器应用程序 (XBAP) ，则会受到 XBAP 限制，如 [Windows Presentation Foundation 部分信任安全性](/dotnet/desktop/wpf/wpf-partial-trust-security)中所述。</span><span class="sxs-lookup"><span data-stu-id="2770f-208">For example, if WCF is hosted in a XAML Browser Application (XBAP), it is subject to XBAP limitations, as described in [Windows Presentation Foundation Partial Trust Security](/dotnet/desktop/wpf/wpf-partial-trust-security).</span></span>  
  
 <span data-ttu-id="2770f-209">在部分信任环境中运行 indigo2 时，不启用以下的其他功能：</span><span class="sxs-lookup"><span data-stu-id="2770f-209">The following additional features are not enabled when running indigo2 in a partial trust environment:</span></span>  
  
- <span data-ttu-id="2770f-210">Windows 管理规范 (WMI)</span><span class="sxs-lookup"><span data-stu-id="2770f-210">Windows Management Instrumentation (WMI)</span></span>  
  
- <span data-ttu-id="2770f-211">事件日志记录仅部分启用（请参见“ **诊断** ”一节的讨论）。</span><span class="sxs-lookup"><span data-stu-id="2770f-211">Event logging is only partially enabled (see discussion in **Diagnostics** section).</span></span>  
  
- <span data-ttu-id="2770f-212">性能计数器</span><span class="sxs-lookup"><span data-stu-id="2770f-212">Performance counters</span></span>  
  
 <span data-ttu-id="2770f-213">使用在部分信任环境中不受支持的 WCF 功能可能会在运行时导致异常。</span><span class="sxs-lookup"><span data-stu-id="2770f-213">Use of WCF features that are not supported in a partial trust environment may result in exceptions at runtime.</span></span>  
  
## <a name="unlisted-features"></a><span data-ttu-id="2770f-214">未列出的功能</span><span class="sxs-lookup"><span data-stu-id="2770f-214">Unlisted Features</span></span>  

 <span data-ttu-id="2770f-215">若要在部分信任环境中运行时发现不可用的信息或操作，最好的方法是尝试在 `try` 块的内部访问资源或执行操作，然后 `catch` 失败。</span><span class="sxs-lookup"><span data-stu-id="2770f-215">The best way to discover that a piece of information or action is unavailable when running in a partial trust environment is to try to access the resource or do the action inside of a `try` block, and then `catch` the failure.</span></span> <span data-ttu-id="2770f-216">若要避免在出现重复错误时扩散跟踪文件，WCF 在第一次安全失败之后禁用资源或操作跟踪。</span><span class="sxs-lookup"><span data-stu-id="2770f-216">To avoid flooding the trace files with duplicate errors, WCF disables tracing of the resource or action after the first security failure.</span></span> <span data-ttu-id="2770f-217">对于在第一次尝试访问资源或执行操作时出现的每个失败的资源访问，将会有一个异常跟踪。</span><span class="sxs-lookup"><span data-stu-id="2770f-217">There is one exception trace for each failed resource access, the first time an attempt is made to access the resource or perform the action.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2770f-218">请参阅</span><span class="sxs-lookup"><span data-stu-id="2770f-218">See also</span></span>

- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>
- [<span data-ttu-id="2770f-219">支持的部署方案</span><span class="sxs-lookup"><span data-stu-id="2770f-219">Supported Deployment Scenarios</span></span>](supported-deployment-scenarios.md)
- [<span data-ttu-id="2770f-220">部分信任最佳实践</span><span class="sxs-lookup"><span data-stu-id="2770f-220">Partial Trust Best Practices</span></span>](partial-trust-best-practices.md)
