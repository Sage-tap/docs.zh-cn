---
description: 了解详细信息：如何：创建自定义授权策略
title: 如何：创建自定义授权策略
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 05b0549b-882d-4660-b6f0-5678543e5475
ms.openlocfilehash: 41158944aec9b0a5b8cb28c51922b8a1b103317c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743702"
---
# <a name="how-to-create-a-custom-authorization-policy"></a><span data-ttu-id="b33cc-103">如何：创建自定义授权策略</span><span class="sxs-lookup"><span data-stu-id="b33cc-103">How to: Create a Custom Authorization Policy</span></span>

<span data-ttu-id="b33cc-104">Windows Communication Foundation (WCF) 中的标识模型基础结构支持基于声明的授权模型。</span><span class="sxs-lookup"><span data-stu-id="b33cc-104">The Identity Model infrastructure in Windows Communication Foundation (WCF) supports a claim-based authorization model.</span></span> <span data-ttu-id="b33cc-105">声明从令牌中提取，并可以选择由自定义授权策略进行处理，然后放入 <xref:System.IdentityModel.Policy.AuthorizationContext> 中，之后进行检查以做出授权决定。</span><span class="sxs-lookup"><span data-stu-id="b33cc-105">Claims are extracted from tokens, optionally processed by custom authorization policy, and then placed into an <xref:System.IdentityModel.Policy.AuthorizationContext> that can then be examined to make authorization decisions.</span></span> <span data-ttu-id="b33cc-106">可以使用自定义策略将声明从传入令牌转换成应用程序需要的声明。</span><span class="sxs-lookup"><span data-stu-id="b33cc-106">A custom policy can be used to transform claims from incoming tokens into claims expected by the application.</span></span> <span data-ttu-id="b33cc-107">通过这种方式，应用程序层可以与 WCF 支持的不同令牌类型提供的不同声明的详细信息分开。</span><span class="sxs-lookup"><span data-stu-id="b33cc-107">In this way, the application layer can be insulated from the details on the differing claims served up by the different token types that WCF supports.</span></span> <span data-ttu-id="b33cc-108">本主题演示如何实现自定义授权策略和如何将该策略添加到服务所使用的策略集中。</span><span class="sxs-lookup"><span data-stu-id="b33cc-108">This topic shows how to implement a custom authorization policy and how to add that policy to the collection of policies used by a service.</span></span>  
  
### <a name="to-implement-a-custom-authorization-policy"></a><span data-ttu-id="b33cc-109">实现自定义授权策略</span><span class="sxs-lookup"><span data-stu-id="b33cc-109">To implement a custom authorization policy</span></span>  
  
1. <span data-ttu-id="b33cc-110">定义一个从 <xref:System.IdentityModel.Policy.IAuthorizationPolicy> 派生的新类。</span><span class="sxs-lookup"><span data-stu-id="b33cc-110">Define a new class that derives from <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span></span>  
  
2. <span data-ttu-id="b33cc-111">实现只读 <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> 属性，方法是在该类的构造函数中生成唯一字符串并在访问此属性时返回该字符串。</span><span class="sxs-lookup"><span data-stu-id="b33cc-111">Implement the read-only <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> property by generating a unique string in the constructor for the class and returning that string whenever the property is accessed.</span></span>  
  
3. <span data-ttu-id="b33cc-112">通过返回表示策略颁发者的 <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A>，实现只读 <xref:System.IdentityModel.Claims.ClaimSet> 属性。</span><span class="sxs-lookup"><span data-stu-id="b33cc-112">Implement the read-only <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> property by returning a <xref:System.IdentityModel.Claims.ClaimSet> that represents the policy issuer.</span></span> <span data-ttu-id="b33cc-113">它可能是表示应用程序的 `ClaimSet`，也可能是内置的 `ClaimSet`（例如，由静态 `ClaimSet` 属性返回的 <xref:System.IdentityModel.Claims.ClaimSet.System%2A>）。</span><span class="sxs-lookup"><span data-stu-id="b33cc-113">This could be a `ClaimSet` that represents the application or a built-in `ClaimSet` (for example, the `ClaimSet` returned by the static <xref:System.IdentityModel.Claims.ClaimSet.System%2A> property.</span></span>  
  
4. <span data-ttu-id="b33cc-114">按照下面过程中的说明，实现 <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> 方法。</span><span class="sxs-lookup"><span data-stu-id="b33cc-114">Implement the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method as described in the following procedure.</span></span>  
  
### <a name="to-implement-the-evaluate-method"></a><span data-ttu-id="b33cc-115">实现 Evaluate 方法</span><span class="sxs-lookup"><span data-stu-id="b33cc-115">To implement the Evaluate method</span></span>  
  
1. <span data-ttu-id="b33cc-116">需要向此方法传递两个参数：<xref:System.IdentityModel.Policy.EvaluationContext> 类的一个实例和一个对象引用。</span><span class="sxs-lookup"><span data-stu-id="b33cc-116">Two parameters are passed to this method: an instance of the <xref:System.IdentityModel.Policy.EvaluationContext> class and an object reference.</span></span>  
  
2. <span data-ttu-id="b33cc-117">如果自定义授权策略添加 <xref:System.IdentityModel.Claims.ClaimSet> 实例，而不考虑的当前内容 <xref:System.IdentityModel.Policy.EvaluationContext> ，则 `ClaimSet` 通过调用 <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> 方法并从方法返回来添加每个实例 `true` <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> 。</span><span class="sxs-lookup"><span data-stu-id="b33cc-117">If the custom authorization policy adds <xref:System.IdentityModel.Claims.ClaimSet> instances without regard to the current content of the <xref:System.IdentityModel.Policy.EvaluationContext>, then add each `ClaimSet` by calling the <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> method and return `true` from the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> method.</span></span> <span data-ttu-id="b33cc-118">返回 `true` 可向授权基础结构指示授权策略已执行其工作，不需要重新调用。</span><span class="sxs-lookup"><span data-stu-id="b33cc-118">Returning `true` indicates to the authorization infrastructure that the authorization policy has performed its work and does not need to be called again.</span></span>  
  
3. <span data-ttu-id="b33cc-119">如果自定义授权策略仅在 `EvaluationContext` 中已经存在特定的声明时才添加声明集，则通过检查由 `ClaimSet` 属性返回的 <xref:System.IdentityModel.Policy.EvaluationContext.ClaimSets%2A> 实例，查找这些声明。</span><span class="sxs-lookup"><span data-stu-id="b33cc-119">If the custom authorization policy adds claim sets only if certain claims are already present in the `EvaluationContext`, then look for those claims by examining the `ClaimSet` instances returned by the <xref:System.IdentityModel.Policy.EvaluationContext.ClaimSets%2A> property.</span></span> <span data-ttu-id="b33cc-120">如果声明已存在，则通过调用 <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> 方法添加新声明集，如果不再需要添加其他声明集，则返回 `true`，向授权基础结构指示授权策略已完成其工作。</span><span class="sxs-lookup"><span data-stu-id="b33cc-120">If the claims are present, then add the new claim sets by calling the <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> method and, if no more claim sets are to be added, return `true`, indicating to the authorization infrastructure that the authorization policy has completed its work.</span></span> <span data-ttu-id="b33cc-121">如果声明不存在，则返回 `false`，指示如果其他授权策略向 `EvaluationContext` 添加更多声明集，则应该重新调用授权策略。</span><span class="sxs-lookup"><span data-stu-id="b33cc-121">If the claims are not present, return `false`, indicating that the authorization policy should be called again if other authorization policies add more claim sets to the `EvaluationContext`.</span></span>  
  
4. <span data-ttu-id="b33cc-122">对于更为复杂的处理方案，可以使用 <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> 方法的第二个参数来存储一个状态变量，在对 <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> 方法的每个后续调用过程中，授权基础结构均将传回该变量以便进行特定的评估。</span><span class="sxs-lookup"><span data-stu-id="b33cc-122">In more complex processing scenarios, the second parameter of the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method is used to store a state variable that the authorization infrastructure will pass back during each subsequent call to the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method for a particular evaluation.</span></span>  
  
### <a name="to-specify-a-custom-authorization-policy-through-configuration"></a><span data-ttu-id="b33cc-123">通过配置指定自定义授权策略</span><span class="sxs-lookup"><span data-stu-id="b33cc-123">To specify a custom authorization policy through configuration</span></span>  
  
1. <span data-ttu-id="b33cc-124">在 `policyType` 元素的 `add` 元素的 `authorizationPolicies` 元素的 `serviceAuthorization` 属性中指定自定义授权策略的类型。</span><span class="sxs-lookup"><span data-stu-id="b33cc-124">Specify the type of the custom authorization policy in the `policyType` attribute in the `add` element in the `authorizationPolicies` element in the `serviceAuthorization` element.</span></span>  
  
    ```xml  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
        <serviceAuthorization serviceAuthorizationManagerType=  
                  "Samples.MyServiceAuthorizationManager" >  
          <authorizationPolicies>  
            <add policyType="Samples.MyAuthorizationPolicy" />  
          </authorizationPolicies>  
        </serviceAuthorization>  
      </behaviors>  
     </system.serviceModel>  
    </configuration>  
    ```  
  
### <a name="to-specify-a-custom-authorization-policy-through-code"></a><span data-ttu-id="b33cc-125">通过代码指定自定义授权策略</span><span class="sxs-lookup"><span data-stu-id="b33cc-125">To specify a custom authorization policy through code</span></span>  
  
1. <span data-ttu-id="b33cc-126">创建 <xref:System.Collections.Generic.List%601> 的一个 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>。</span><span class="sxs-lookup"><span data-stu-id="b33cc-126">Create a <xref:System.Collections.Generic.List%601> of <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span></span>  
  
2. <span data-ttu-id="b33cc-127">创建自定义授权策略的一个实例。</span><span class="sxs-lookup"><span data-stu-id="b33cc-127">Create an instance of the custom authorization policy.</span></span>  
  
3. <span data-ttu-id="b33cc-128">将该授权策略实例添加到列表中。</span><span class="sxs-lookup"><span data-stu-id="b33cc-128">Add the authorization policy instance to the list.</span></span>  
  
4. <span data-ttu-id="b33cc-129">对每个自定义授权策略重复步骤 2 和 3。</span><span class="sxs-lookup"><span data-stu-id="b33cc-129">Repeat steps 2 and 3 for each custom authorization policy.</span></span>  
  
5. <span data-ttu-id="b33cc-130">将列表的一个只读版本分配给 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="b33cc-130">Assign a read-only version of the list to the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A> property.</span></span>  
  
     [!code-csharp[c_CustomAuthPol#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#8)]
     [!code-vb[c_CustomAuthPol#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="b33cc-131">示例</span><span class="sxs-lookup"><span data-stu-id="b33cc-131">Example</span></span>  

 <span data-ttu-id="b33cc-132">下面的示例演示完整的 <xref:System.IdentityModel.Policy.IAuthorizationPolicy> 实现。</span><span class="sxs-lookup"><span data-stu-id="b33cc-132">The following example shows a complete <xref:System.IdentityModel.Policy.IAuthorizationPolicy> implementation.</span></span>  
  
 [!code-csharp[c_CustomAuthPol#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#5)]
 [!code-vb[c_CustomAuthPol#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="b33cc-133">请参阅</span><span class="sxs-lookup"><span data-stu-id="b33cc-133">See also</span></span>

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [<span data-ttu-id="b33cc-134">如何：比较声明</span><span class="sxs-lookup"><span data-stu-id="b33cc-134">How to: Compare Claims</span></span>](how-to-compare-claims.md)
- [<span data-ttu-id="b33cc-135">如何：为服务创建自定义授权管理器</span><span class="sxs-lookup"><span data-stu-id="b33cc-135">How to: Create a Custom Authorization Manager for a Service</span></span>](how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="b33cc-136">授权策略</span><span class="sxs-lookup"><span data-stu-id="b33cc-136">Authorization Policy</span></span>](../samples/authorization-policy.md)
