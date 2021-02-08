---
description: 了解有关以下内容的详细信息：结合使用多个身份验证方案和 WCF
title: 对 WCF 使用多个身份验证方案
ms.date: 03/30/2017
ms.assetid: f32a56a0-e2b2-46bf-a302-29e1275917f9
ms.openlocfilehash: fd03a13c5d38bbf26e2b6079d1320bc389c9f20b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779707"
---
# <a name="using-multiple-authentication-schemes-with-wcf"></a><span data-ttu-id="c3ceb-103">对 WCF 使用多个身份验证方案</span><span class="sxs-lookup"><span data-stu-id="c3ceb-103">Using Multiple Authentication Schemes with WCF</span></span>

<span data-ttu-id="c3ceb-104">WCF 现在允许您对单个终结点上指定多个身份验证方案。</span><span class="sxs-lookup"><span data-stu-id="c3ceb-104">WCF now allows you to specify multiple authentication schemes on a single endpoint.</span></span> <span data-ttu-id="c3ceb-105">此外，Web 承载的服务可以直接从 IIS 继承其身份验证设置。</span><span class="sxs-lookup"><span data-stu-id="c3ceb-105">Furthermore web hosted services can inherit their authentication settings directly from IIS.</span></span> <span data-ttu-id="c3ceb-106">自承载服务可以指定可使用的身份验证方案。</span><span class="sxs-lookup"><span data-stu-id="c3ceb-106">Self-hosted services can specify what authentication schemes can be used.</span></span> <span data-ttu-id="c3ceb-107">有关在 IIS 中设置身份验证设置的详细信息，请参阅 [Iis 身份验证](https://go.microsoft.com/fwlink/?LinkId=232458)</span><span class="sxs-lookup"><span data-stu-id="c3ceb-107">For more information about setting authentication settings in IIS, see [IIS Authentication](https://go.microsoft.com/fwlink/?LinkId=232458)</span></span>  
  
## <a name="iis-hosted-services"></a><span data-ttu-id="c3ceb-108">承载于 IIS 中的服务</span><span class="sxs-lookup"><span data-stu-id="c3ceb-108">IIS-Hosted Services</span></span>  

 <span data-ttu-id="c3ceb-109">对于承载于 IIS 中的服务，设置您希望在 IIS 中使用的身份验证方案。</span><span class="sxs-lookup"><span data-stu-id="c3ceb-109">For IIS-hosted services, set the authentication schemes you wish to use in IIS.</span></span> <span data-ttu-id="c3ceb-110">然后，在你的服务的 web.config 文件中，在绑定配置中将 clientCredential 类型指定为 "InheritedFromHost"，如下面的 XML 代码段中所示：</span><span class="sxs-lookup"><span data-stu-id="c3ceb-110">Then in your service’s web.config file, in your binding configuration specify clientCredential type as "InheritedFromHost" as shown in the following XML snippet:</span></span>  
  
```xml  
<bindings>  
      <basicHttpBinding>  
        <binding name="secureBinding">  
          <security mode="Transport">  
            <transport clientCredentialType="InheritedFromHost" />  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
```  
  
 <span data-ttu-id="c3ceb-111">你可以使用 ServiceAuthenticationBehavior 或元素指定你只希望将身份验证方案的一个子集用于服务 \<serviceAuthenticationManager> 。</span><span class="sxs-lookup"><span data-stu-id="c3ceb-111">You can specify that you only want a subset of authentication schemes to be used with your service using the ServiceAuthenticationBehavior or the \<serviceAuthenticationManager> element.</span></span> <span data-ttu-id="c3ceb-112">在代码中对此进行配置时，使用 ServiceAuthenticationBehavior，如下面的 XML 代码段中所示。</span><span class="sxs-lookup"><span data-stu-id="c3ceb-112">When configuring this in code use the ServiceAuthenticationBehavior as shown in the following code snippet.</span></span>  
  
```csharp  
// ...  
ServiceAuthenticationBehavior sab = null;  
sab = serviceHost.Description.Behaviors.Find<ServiceAuthenticationBehavior>();  
  
if (sab == null)  
{  
    sab = new ServiceAuthenticationBehavior();  
    sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
    serviceHost.Description.Behaviors.Add(sab);  
}  
else  
{  
     sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
}  
// ...  
```  
  
 <span data-ttu-id="c3ceb-113">在配置文件中配置此配置时，请使用 \<serviceAuthenticationManager> 元素，如下面的 XML 代码段中所示。</span><span class="sxs-lookup"><span data-stu-id="c3ceb-113">When configuring this in a config file, use the \<serviceAuthenticationManager> element as shown in the following XML snippet.</span></span>  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior name="limitedAuthBehavior">  
          <serviceAuthenticationManager authenticationSchemes="Negotiate, Digest, Basic"/>  
          <!-- ... -->  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
 <span data-ttu-id="c3ceb-114">这将确保只有一部分此处列出的身份验证方案将被考虑应用于服务终结点，具体是哪些身份验证方案取决于 IIS 中所选的内容。</span><span class="sxs-lookup"><span data-stu-id="c3ceb-114">This will ensure that only a subset of the authentication schemes listed here will be considered for applying on the service endpoint, depending on what is selected in the IIS.</span></span> <span data-ttu-id="c3ceb-115">这意味着，开发人员可以通过从 serviceAuthenticationManager 列表中省略基本身份验证而从列表中排除它，甚至即使在 IIS 中启用基本身份验证，它也将不会在服务终结点上应用</span><span class="sxs-lookup"><span data-stu-id="c3ceb-115">This means that a developer can exclude say Basic auth from the list by omitting it from the serviceAuthenticationManager listing and even if it is enabled in IIS, it will not be applied on the service endpoint</span></span>  
  
## <a name="self-hosted-services"></a><span data-ttu-id="c3ceb-116">自承载服务</span><span class="sxs-lookup"><span data-stu-id="c3ceb-116">Self-Hosted Services</span></span>  

 <span data-ttu-id="c3ceb-117">自承载服务在配置上稍有不同，因为没有要从其继承设置的 IIS。</span><span class="sxs-lookup"><span data-stu-id="c3ceb-117">Self-hosted services are configured a bit differently since there is no IIS to inherit settings from.</span></span> <span data-ttu-id="c3ceb-118">在这里，你将使用 \<serviceAuthenticationManager> 元素或 ServiceAuthenticationBehavior 指定将继承的身份验证设置。</span><span class="sxs-lookup"><span data-stu-id="c3ceb-118">Here you use the \<serviceAuthenticationManager> element or ServiceAuthenticationBehavior to specify the authentication settings that will be inherited.</span></span> <span data-ttu-id="c3ceb-119">在代码中如下所示：</span><span class="sxs-lookup"><span data-stu-id="c3ceb-119">In code it looks like this:</span></span>  
  
```csharp  
// ...  
ServiceAuthenticationBehavior sab = null;  
sab = serviceHost.Description.Behaviors.Find<ServiceAuthenticationBehavior>();  
  
if (sab == null)  
{  
    sab = new ServiceAuthenticationBehavior();  
    sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
    serviceHost.Description.Behaviors.Add(sab);  
}  
else  
{  
     sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
}  
// ...  
```  
  
 <span data-ttu-id="c3ceb-120">在配置中如下所示：</span><span class="sxs-lookup"><span data-stu-id="c3ceb-120">In config, it looks like this:</span></span>  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior name="limitedAuthBehavior">  
          <serviceAuthenticationManager authenticationSchemes="Negotiate, Digest, Basic"/>  
          <!-- ... -->  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
 <span data-ttu-id="c3ceb-121">然后，你可以在绑定设置中指定 InheritFromHost，如下面的 XML 代码段中所示。</span><span class="sxs-lookup"><span data-stu-id="c3ceb-121">And then you can specify InheritFromHost in your binding settings as shown in the following XML snippet.</span></span>  
  
```xml  
<bindings>  
      <basicHttpBinding>  
        <binding name="secureBinding">  
          <security mode="Transport">  
            <transport clientCredentialType="InheritedFromHost" />  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
```  
  
 <span data-ttu-id="c3ceb-122">或者，你可以通过在 HTTP 传输绑定元素上设置身份验证架构，在自定义绑定中指定身份验证架构，如下面的配置代码段所示。</span><span class="sxs-lookup"><span data-stu-id="c3ceb-122">Alternatively, you can specify the authentication schemes in a custom binding, by setting the authentication schemes on the HTTP transport binding element, as shown in the following config snippet.</span></span>  
  
```xml  
<binding name="multipleBinding">  
      <textMessageEncoding/>  
      <httpTransport authenticationScheme="Negotiate, Ntlm, Digest, Basic" />  
    </binding>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c3ceb-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="c3ceb-123">See also</span></span>

- [<span data-ttu-id="c3ceb-124">绑定与安全</span><span class="sxs-lookup"><span data-stu-id="c3ceb-124">Bindings and Security</span></span>](bindings-and-security.md)
- [<span data-ttu-id="c3ceb-125">终结点：地址、绑定和协定</span><span class="sxs-lookup"><span data-stu-id="c3ceb-125">Endpoints: Addresses, Bindings, and Contracts</span></span>](endpoints-addresses-bindings-and-contracts.md)
- [<span data-ttu-id="c3ceb-126">配置系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="c3ceb-126">Configuring System-Provided Bindings</span></span>](configuring-system-provided-bindings.md)
- [<span data-ttu-id="c3ceb-127">使用自定义绑定的安全功能</span><span class="sxs-lookup"><span data-stu-id="c3ceb-127">Security Capabilities with Custom Bindings</span></span>](security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="c3ceb-128">绑定</span><span class="sxs-lookup"><span data-stu-id="c3ceb-128">Bindings</span></span>](bindings.md)
- [<span data-ttu-id="c3ceb-129">自定义绑定</span><span class="sxs-lookup"><span data-stu-id="c3ceb-129">Custom Bindings</span></span>](../extending/custom-bindings.md)
