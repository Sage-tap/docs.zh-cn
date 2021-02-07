---
description: 了解详细信息： <add>
title: <add>
ms.date: 03/30/2017
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
author: BrucePerlerMS
ms.openlocfilehash: c79fb66fb4e87f15c2bf7f2c02e57f473c7262a8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681859"
---
# \<add>

<span data-ttu-id="5c2bd-102">将指定的安全令牌处理程序添加到令牌处理程序集合。</span><span class="sxs-lookup"><span data-stu-id="5c2bd-102">Adds the specified security token handler to the token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="5c2bd-103">语法</span><span class="sxs-lookup"><span data-stu-id="5c2bd-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type=xs:string>  
        <optionalConfigurationElement>  
        </optionalConfigurationElement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5c2bd-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="5c2bd-104">Attributes and Elements</span></span>  

 <span data-ttu-id="5c2bd-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="5c2bd-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5c2bd-106">特性</span><span class="sxs-lookup"><span data-stu-id="5c2bd-106">Attributes</span></span>  
  
|<span data-ttu-id="5c2bd-107">属性</span><span class="sxs-lookup"><span data-stu-id="5c2bd-107">Attribute</span></span>|<span data-ttu-id="5c2bd-108">说明</span><span class="sxs-lookup"><span data-stu-id="5c2bd-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5c2bd-109">type</span><span class="sxs-lookup"><span data-stu-id="5c2bd-109">type</span></span>|<span data-ttu-id="5c2bd-110">要添加的令牌处理程序的 CLR 类型名称。</span><span class="sxs-lookup"><span data-stu-id="5c2bd-110">The CLR type name of the token handler to be added.</span></span> <span data-ttu-id="5c2bd-111">有关如何指定属性的详细信息 `type` ，请参阅 [自定义类型引用](/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references)。</span><span class="sxs-lookup"><span data-stu-id="5c2bd-111">For more information about how to specify the `type` attribute, see [Custom Type References](/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5c2bd-112">子元素</span><span class="sxs-lookup"><span data-stu-id="5c2bd-112">Child Elements</span></span>  
  
|<span data-ttu-id="5c2bd-113">元素</span><span class="sxs-lookup"><span data-stu-id="5c2bd-113">Element</span></span>|<span data-ttu-id="5c2bd-114">说明</span><span class="sxs-lookup"><span data-stu-id="5c2bd-114">Description</span></span>|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement>](samlsecuritytokenrequirement.md)|<span data-ttu-id="5c2bd-115">为 <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> 类、 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 类或其中任何一个类的派生类提供配置。</span><span class="sxs-lookup"><span data-stu-id="5c2bd-115">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
|[\<sessionTokenRequirement>](sessiontokenrequirement.md)|<span data-ttu-id="5c2bd-116">提供 <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> 类或派生类的配置。</span><span class="sxs-lookup"><span data-stu-id="5c2bd-116">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>|  
|[\<userNameSecurityTokenHandlerRequirement>](usernamesecuritytokenhandlerrequirement.md)|<span data-ttu-id="5c2bd-117">提供 <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> 类或派生类的配置。</span><span class="sxs-lookup"><span data-stu-id="5c2bd-117">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>|  
|[\<x509SecurityTokenHandlerRequirement>](x509securitytokenhandlerrequirement.md)|<span data-ttu-id="5c2bd-118">提供 <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> 类或派生类的可选配置。</span><span class="sxs-lookup"><span data-stu-id="5c2bd-118">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5c2bd-119">父元素</span><span class="sxs-lookup"><span data-stu-id="5c2bd-119">Parent Elements</span></span>  
  
|<span data-ttu-id="5c2bd-120">元素</span><span class="sxs-lookup"><span data-stu-id="5c2bd-120">Element</span></span>|<span data-ttu-id="5c2bd-121">说明</span><span class="sxs-lookup"><span data-stu-id="5c2bd-121">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|<span data-ttu-id="5c2bd-122">指定注册到终结点的安全令牌处理程序的集合。</span><span class="sxs-lookup"><span data-stu-id="5c2bd-122">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c2bd-123">备注</span><span class="sxs-lookup"><span data-stu-id="5c2bd-123">Remarks</span></span>  

 <span data-ttu-id="5c2bd-124">`<add>`元素可以采用单个子元素，该元素指定标记处理程序的配置。</span><span class="sxs-lookup"><span data-stu-id="5c2bd-124">The `<add>` element can take a single child element that specifies the configuration for the token handler.</span></span> <span data-ttu-id="5c2bd-125">这取决于通过元素的属性引用的处理程序类是否 `type` `<add>` 为此功能提供支持。</span><span class="sxs-lookup"><span data-stu-id="5c2bd-125">This is dependent on whether the handler class referenced through the `type` attribute of the `<add>` element provides support for this feature.</span></span> <span data-ttu-id="5c2bd-126">提供此功能的令牌处理程序类必须公开采用对象的构造函数 <xref:System.Xml.XmlElement> 。</span><span class="sxs-lookup"><span data-stu-id="5c2bd-126">Token handler classes that provide this feature must expose a constructor that takes an <xref:System.Xml.XmlElement> object.</span></span>  

```csharp  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 <span data-ttu-id="5c2bd-127">某些内置安全令牌处理程序类提供此功能。</span><span class="sxs-lookup"><span data-stu-id="5c2bd-127">Several of the built-in security token handler classes do provide this functionality.</span></span> <span data-ttu-id="5c2bd-128">这些类包括 <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> 、、、 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> 和 <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> 。</span><span class="sxs-lookup"><span data-stu-id="5c2bd-128">These classes are <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5c2bd-129">标记处理程序集合只能包含任何给定类型的单个处理程序。</span><span class="sxs-lookup"><span data-stu-id="5c2bd-129">The token handler collection can only contain a single handler of any given type.</span></span> <span data-ttu-id="5c2bd-130">这意味着，例如，如果你想要将派生自类的处理程序添加 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 到集合，则必须首先 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 从集合中删除默认情况下存在的。</span><span class="sxs-lookup"><span data-stu-id="5c2bd-130">This means, for example, that if you want to add a handler that is derived from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class to the collection, you must first remove the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, which is present by default, from the collection.</span></span> <span data-ttu-id="5c2bd-131">您可以使用 [\<remove>](remove.md) 元素从集合中移除单个处理程序或使用 [\<clear>](clear.md) 元素从集合中移除所有处理程序。</span><span class="sxs-lookup"><span data-stu-id="5c2bd-131">You can use the [\<remove>](remove.md) element to remove a single handler from the collection or use the [\<clear>](clear.md) element to remove all handlers from the collection.</span></span>  
  
 <span data-ttu-id="5c2bd-132">在处理程序上指定的设置将重写在元素下的标记处理程序集合上指定的等效设置 [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) ，以及在元素下的服务级别指定的设置 [\<identityConfiguration>](identityconfiguration.md) 。</span><span class="sxs-lookup"><span data-stu-id="5c2bd-132">Settings specified on a handler override equivalent settings specified on the token handler collection under the [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) element and those specified at the service-level under the [\<identityConfiguration>](identityconfiguration.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c2bd-133">示例</span><span class="sxs-lookup"><span data-stu-id="5c2bd-133">Example</span></span>  

 <span data-ttu-id="5c2bd-134">下面的 XML 演示 `<add>` 如何使用和元素将 `<remove>` 默认会话标记处理程序替换为自定义会话标记处理程序。</span><span class="sxs-lookup"><span data-stu-id="5c2bd-134">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="5c2bd-135">XML 是从示例获取的 `ClaimsAwareWebFarm` 。</span><span class="sxs-lookup"><span data-stu-id="5c2bd-135">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
