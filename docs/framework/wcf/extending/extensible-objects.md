---
description: 了解详细信息：可扩展对象
title: 可扩展对象
ms.date: 03/30/2017
helpviewer_keywords:
- extensible objects [WCF]
ms.assetid: bc88cefc-31fb-428e-9447-6d20a7d452af
ms.openlocfilehash: 80082f4c94adf2d668ff4c241d286959d9a05038
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756690"
---
# <a name="extensible-objects"></a><span data-ttu-id="67e74-103">可扩展对象</span><span class="sxs-lookup"><span data-stu-id="67e74-103">Extensible Objects</span></span>

<span data-ttu-id="67e74-104">可扩展对象模式用于使用新功能扩展现有运行时类，或者向对象中添加新状态。</span><span class="sxs-lookup"><span data-stu-id="67e74-104">The extensible object pattern is used to either extend existing runtime classes with new functionality or to add new state to an object.</span></span> <span data-ttu-id="67e74-105">附加到可扩展对象之一的扩展名，在访问附加到公共可扩展对象的共享状态和功能过程的各个不同阶段启用行为，各可扩展对象可以访问该公共扩展对象。</span><span class="sxs-lookup"><span data-stu-id="67e74-105">Extensions, attached to one of the extensible objects, enable behaviors at very different stages in processing to access shared state and functionality attached to a common extensible object that they can access.</span></span>

## <a name="the-iextensibleobjectt-pattern"></a><span data-ttu-id="67e74-106">IExtensibleObject \<T> 模式</span><span class="sxs-lookup"><span data-stu-id="67e74-106">The IExtensibleObject\<T> Pattern</span></span>

<span data-ttu-id="67e74-107">可扩展对象模式中有三个接口：<xref:System.ServiceModel.IExtensibleObject%601>、<xref:System.ServiceModel.IExtension%601> 和 <xref:System.ServiceModel.IExtensionCollection%601>。</span><span class="sxs-lookup"><span data-stu-id="67e74-107">There are three interfaces in the extensible object pattern: <xref:System.ServiceModel.IExtensibleObject%601>, <xref:System.ServiceModel.IExtension%601>, and <xref:System.ServiceModel.IExtensionCollection%601>.</span></span>

<span data-ttu-id="67e74-108"><xref:System.ServiceModel.IExtensibleObject%601> 接口通过允许 <xref:System.ServiceModel.IExtension%601> 对象自定义类型的功能的这些类型实现。</span><span class="sxs-lookup"><span data-stu-id="67e74-108">The <xref:System.ServiceModel.IExtensibleObject%601> interface is implemented by types that allow <xref:System.ServiceModel.IExtension%601> objects to customize their functionality.</span></span>

<span data-ttu-id="67e74-109">可扩展的对象允许动态聚合 <xref:System.ServiceModel.IExtension%601> 对象。</span><span class="sxs-lookup"><span data-stu-id="67e74-109">Extensible objects allow dynamic aggregation of <xref:System.ServiceModel.IExtension%601> objects.</span></span> <span data-ttu-id="67e74-110">以下接口确定 <xref:System.ServiceModel.IExtension%601> 对象的特点：</span><span class="sxs-lookup"><span data-stu-id="67e74-110"><xref:System.ServiceModel.IExtension%601> objects are characterized by the following interface:</span></span>

```csharp
public interface IExtension<T>
where T : IExtensibleObject<T>
{
    void Attach(T owner);
    void Detach(T owner);
}
```

<span data-ttu-id="67e74-111">类型限制保证仅为是 <xref:System.ServiceModel.IExtensibleObject%601> 的类定义扩展名。</span><span class="sxs-lookup"><span data-stu-id="67e74-111">The type restriction guarantees that extensions can only be defined for classes that are <xref:System.ServiceModel.IExtensibleObject%601>.</span></span> <span data-ttu-id="67e74-112"><xref:System.ServiceModel.IExtension%601.Attach%2A> 和 <xref:System.ServiceModel.IExtension%601.Detach%2A> 提供聚合或解聚的通知。</span><span class="sxs-lookup"><span data-stu-id="67e74-112"><xref:System.ServiceModel.IExtension%601.Attach%2A> and <xref:System.ServiceModel.IExtension%601.Detach%2A> provide notification of aggregation or disaggregation.</span></span>

<span data-ttu-id="67e74-113">对于实现限制它们何时可能会添加到所有者中或从所有者中移除有效。</span><span class="sxs-lookup"><span data-stu-id="67e74-113">It is valid for implementations to restrict when they may be added and removed from an owner.</span></span> <span data-ttu-id="67e74-114">例如，可以完全禁止移除（这将禁止在所有者或扩展名处于某个特定状态时添加或移除扩展名）、禁止同时添加多个所有者，或者仅允许单个移除后进行单个添加。</span><span class="sxs-lookup"><span data-stu-id="67e74-114">For example, you can disallow removal entirely, disallowing adding or removing extensions when the owner or extension are in a certain state, disallow adding to multiple owners concurrently, or allow only a single addition followed by a single remove.</span></span>

<span data-ttu-id="67e74-115"><xref:System.ServiceModel.IExtension%601> 不表示与其他标准托管接口进行的任何交互。</span><span class="sxs-lookup"><span data-stu-id="67e74-115"><xref:System.ServiceModel.IExtension%601> does not imply any interactions with other standard managed interfaces.</span></span> <span data-ttu-id="67e74-116">具体地说，所有者对象上的 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 方法通常不与它的扩展名分离。</span><span class="sxs-lookup"><span data-stu-id="67e74-116">Specifically, the <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> method on the owner object does not normally detach its extensions.</span></span>

<span data-ttu-id="67e74-117">将扩展添加到集合时，将在 <xref:System.ServiceModel.IExtension%601.Attach%2A> 进入集合之前调用。</span><span class="sxs-lookup"><span data-stu-id="67e74-117">When an extension is added to the collection, <xref:System.ServiceModel.IExtension%601.Attach%2A> is called before it goes into the collection.</span></span> <span data-ttu-id="67e74-118">从集合中移除某个扩展 <xref:System.ServiceModel.IExtension%601.Detach%2A> 后，将在删除该扩展后调用。</span><span class="sxs-lookup"><span data-stu-id="67e74-118">When an extension is removed from the collection, <xref:System.ServiceModel.IExtension%601.Detach%2A> is called after it is removed.</span></span> <span data-ttu-id="67e74-119">这意味着 (假设适当的同步) 扩展只能在与之间的集合中找到 <xref:System.ServiceModel.IExtension%601.Attach%2A> <xref:System.ServiceModel.IExtension%601.Detach%2A> 。</span><span class="sxs-lookup"><span data-stu-id="67e74-119">This means (assuming appropriate synchronization) an extension can count on only being found in the collection while it is between <xref:System.ServiceModel.IExtension%601.Attach%2A> and <xref:System.ServiceModel.IExtension%601.Detach%2A>.</span></span>

<span data-ttu-id="67e74-120">传递给 <xref:System.ServiceModel.IExtensionCollection%601.FindAll%2A> 或 <xref:System.ServiceModel.IExtensionCollection%601.Find%2A> 的对象不需要是 <xref:System.ServiceModel.IExtension%601>（例如，可以传递任何对象），但返回的扩展名是 <xref:System.ServiceModel.IExtension%601>。</span><span class="sxs-lookup"><span data-stu-id="67e74-120">The object passed to <xref:System.ServiceModel.IExtensionCollection%601.FindAll%2A> or <xref:System.ServiceModel.IExtensionCollection%601.Find%2A> need not be <xref:System.ServiceModel.IExtension%601> (for example, you can pass any object), but the returned extension is an <xref:System.ServiceModel.IExtension%601>.</span></span>

<span data-ttu-id="67e74-121">如果集合中没有扩展名为，则 <xref:System.ServiceModel.IExtension%601> <xref:System.ServiceModel.IExtensionCollection%601.Find%2A> 返回 null，并 <xref:System.ServiceModel.IExtensionCollection%601.FindAll%2A> 返回一个空集合。</span><span class="sxs-lookup"><span data-stu-id="67e74-121">If no extension in the collection is an <xref:System.ServiceModel.IExtension%601>, <xref:System.ServiceModel.IExtensionCollection%601.Find%2A> returns null, and <xref:System.ServiceModel.IExtensionCollection%601.FindAll%2A> returns an empty collection.</span></span> <span data-ttu-id="67e74-122">如果多个扩展实现 <xref:System.ServiceModel.IExtension%601> ，则 <xref:System.ServiceModel.IExtensionCollection%601.Find%2A> 返回其中一个。</span><span class="sxs-lookup"><span data-stu-id="67e74-122">If multiple extensions implement <xref:System.ServiceModel.IExtension%601>, <xref:System.ServiceModel.IExtensionCollection%601.Find%2A> returns one of them.</span></span> <span data-ttu-id="67e74-123">从 <xref:System.ServiceModel.IExtensionCollection%601.FindAll%2A> 中返回的值是快照。</span><span class="sxs-lookup"><span data-stu-id="67e74-123">The value returned from <xref:System.ServiceModel.IExtensionCollection%601.FindAll%2A> is a snapshot.</span></span>

<span data-ttu-id="67e74-124">有两种主要方案。</span><span class="sxs-lookup"><span data-stu-id="67e74-124">There are two main scenarios.</span></span> <span data-ttu-id="67e74-125">第一个方案使用 <xref:System.ServiceModel.IExtensibleObject%601.Extensions%2A> 属性作为基于类型的字典插入对象状态，以使另一组件使用该类型进行查找。</span><span class="sxs-lookup"><span data-stu-id="67e74-125">The first scenario uses the <xref:System.ServiceModel.IExtensibleObject%601.Extensions%2A> property as a type-based dictionary to insert state on an object to enable another component to look it up using the type.</span></span>

<span data-ttu-id="67e74-126">第二个方案使用 <xref:System.ServiceModel.IExtension%601.Attach%2A> 和 <xref:System.ServiceModel.IExtension%601.Detach%2A> 属性使对象可以参与自定义行为，例如注册事件、监视状态转换等。</span><span class="sxs-lookup"><span data-stu-id="67e74-126">The second scenario uses the <xref:System.ServiceModel.IExtension%601.Attach%2A> and <xref:System.ServiceModel.IExtension%601.Detach%2A> properties to enable an object to participate in custom behavior, such as registering for events, watching state transitions, and so on.</span></span>

<span data-ttu-id="67e74-127"><xref:System.ServiceModel.IExtensionCollection%601> 接口是允许按照其类型检索 <xref:System.ServiceModel.IExtension%601> 的 <xref:System.ServiceModel.IExtension%601> 对象集合。</span><span class="sxs-lookup"><span data-stu-id="67e74-127">The <xref:System.ServiceModel.IExtensionCollection%601> interface is a collection of the <xref:System.ServiceModel.IExtension%601> objects that allow for retrieving the <xref:System.ServiceModel.IExtension%601> by its type.</span></span> <span data-ttu-id="67e74-128"><xref:System.ServiceModel.IExtensionCollection%601.Find%2A?displayProperty=nameWithType> 返回最近添加的对象，此对象是属于该类型的 <xref:System.ServiceModel.IExtension%601>。</span><span class="sxs-lookup"><span data-stu-id="67e74-128"><xref:System.ServiceModel.IExtensionCollection%601.Find%2A?displayProperty=nameWithType> returns the most recently added object that is an <xref:System.ServiceModel.IExtension%601> of that type.</span></span>

### <a name="extensible-objects-in-windows-communication-foundation"></a><span data-ttu-id="67e74-129">Windows Communication Foundation 中的可扩展对象</span><span class="sxs-lookup"><span data-stu-id="67e74-129">Extensible Objects in Windows Communication Foundation</span></span>

<span data-ttu-id="67e74-130"> (WCF) Windows Communication Foundation 中有四个可扩展对象：</span><span class="sxs-lookup"><span data-stu-id="67e74-130">There are four extensible objects in Windows Communication Foundation (WCF):</span></span>

- <span data-ttu-id="67e74-131"><xref:System.ServiceModel.ServiceHostBase> — 这是服务主机的基类。</span><span class="sxs-lookup"><span data-stu-id="67e74-131"><xref:System.ServiceModel.ServiceHostBase> – This is the base class for the service’s host.</span></span>  <span data-ttu-id="67e74-132">此类的扩展名可用于扩展 <xref:System.ServiceModel.ServiceHostBase> 自身的行为，或者用于存储每个服务的状态。</span><span class="sxs-lookup"><span data-stu-id="67e74-132">Extensions of this class can be used to extend the behavior of the <xref:System.ServiceModel.ServiceHostBase> itself or to store the state for each service.</span></span>

- <span data-ttu-id="67e74-133"><xref:System.ServiceModel.InstanceContext> — 此类将服务类型的实例与服务运行时相连。</span><span class="sxs-lookup"><span data-stu-id="67e74-133"><xref:System.ServiceModel.InstanceContext> – This class connects an instance of the service’s type with the service runtime.</span></span>  <span data-ttu-id="67e74-134">它包含有关该实例的信息以及对 <xref:System.ServiceModel.InstanceContext> 的包含 <xref:System.ServiceModel.ServiceHostBase> 的引用。</span><span class="sxs-lookup"><span data-stu-id="67e74-134">It contains information about the instance as well as a reference to the <xref:System.ServiceModel.InstanceContext>'s containing <xref:System.ServiceModel.ServiceHostBase>.</span></span> <span data-ttu-id="67e74-135">此类的扩展名可用于扩展 <xref:System.ServiceModel.InstanceContext> 的行为，或者用于存储每个服务的状态。</span><span class="sxs-lookup"><span data-stu-id="67e74-135">Extensions of this class can be used to extend the behavior of the <xref:System.ServiceModel.InstanceContext> or to store the state for each service.</span></span>

- <span data-ttu-id="67e74-136"><xref:System.ServiceModel.OperationContext> — 此类表示为每个操作收集的运行时的操作信息。</span><span class="sxs-lookup"><span data-stu-id="67e74-136"><xref:System.ServiceModel.OperationContext> – This class represents the operation information that the runtime gathers for each operation.</span></span>  <span data-ttu-id="67e74-137">这包括的信息有：传入消息头、传入消息属性和传入安全标识，以及其他信息。</span><span class="sxs-lookup"><span data-stu-id="67e74-137">This includes information such as the incoming message headers, the incoming message properties, the incoming security identity, and other information.</span></span>  <span data-ttu-id="67e74-138">此类的扩展名可以扩展 <xref:System.ServiceModel.OperationContext> 的行为，也可以存储每个操作的状态。</span><span class="sxs-lookup"><span data-stu-id="67e74-138">Extensions of this class can either extend the behavior of <xref:System.ServiceModel.OperationContext> or store the state for each operation.</span></span>

- <span data-ttu-id="67e74-139"><xref:System.ServiceModel.IContextChannel> –此接口允许检查由 WCF 运行时生成的通道和代理的每个状态。</span><span class="sxs-lookup"><span data-stu-id="67e74-139"><xref:System.ServiceModel.IContextChannel> – This interface allows for the inspection of each state for the channels and proxies built by the WCF runtime.</span></span>  <span data-ttu-id="67e74-140">此类的扩展名可以扩展 <xref:System.ServiceModel.IClientChannel> 的行为，也可以使用它存储每个通道的状态。</span><span class="sxs-lookup"><span data-stu-id="67e74-140">Extensions of this class can either extend the behavior of <xref:System.ServiceModel.IClientChannel> or can use it to store the state for each channel.</span></span>

<span data-ttu-id="67e74-141">下面的代码示例演示使用简单的扩展名来跟踪 <xref:System.ServiceModel.InstanceContext> 对象。</span><span class="sxs-lookup"><span data-stu-id="67e74-141">The following code example shows the use of a simple extension to track <xref:System.ServiceModel.InstanceContext> objects.</span></span>

[!code-csharp[IInstanceContextInitializer#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/iinstancecontextinitializer/cs/initializer.cs#1)]

## <a name="see-also"></a><span data-ttu-id="67e74-142">请参阅</span><span class="sxs-lookup"><span data-stu-id="67e74-142">See also</span></span>

- <xref:System.ServiceModel.IExtensibleObject%601>
- <xref:System.ServiceModel.IExtension%601>
- <xref:System.ServiceModel.IExtensionCollection%601>
