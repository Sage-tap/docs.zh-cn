---
description: 了解详细信息：声明创建和资源值
title: 声明创建和资源值
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], creation and resource values
ms.assetid: 30431f76-cbe7-4bad-bad7-8e43e23a82d4
ms.openlocfilehash: 20763c683c5bf5734a21a4315576a8f9f354ff35
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734979"
---
# <a name="claim-creation-and-resource-values"></a><span data-ttu-id="4ed70-103">声明创建和资源值</span><span class="sxs-lookup"><span data-stu-id="4ed70-103">Claim Creation and Resource Values</span></span>

<span data-ttu-id="4ed70-104"><xref:System.IdentityModel.Claims.Claim> 类提供了多种创建内置声明类型的实例的方法。</span><span class="sxs-lookup"><span data-stu-id="4ed70-104">The <xref:System.IdentityModel.Claims.Claim> class provides several methods for creating instances of built-in claims types.</span></span> <span data-ttu-id="4ed70-105">在这些方法中，以下方法不对提供的资源执行语义或格式检查：</span><span class="sxs-lookup"><span data-stu-id="4ed70-105">Of these methods, the following perform no semantic or format checking on the supplied resource:</span></span>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateDnsClaim%2A>  
  
- <span data-ttu-id="4ed70-106"><xref:System.IdentityModel.Claims.Claim.CreateHashClaim%2A>（不检查字节数组的长度或内容）</span><span class="sxs-lookup"><span data-stu-id="4ed70-106"><xref:System.IdentityModel.Claims.Claim.CreateHashClaim%2A> (does not check the length or content of the byte array)</span></span>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateNameClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateSpnClaim%2A>  
  
- <span data-ttu-id="4ed70-107"><xref:System.IdentityModel.Claims.Claim.CreateThumbprintClaim%2A>（不检查字节数组的长度或内容）</span><span class="sxs-lookup"><span data-stu-id="4ed70-107"><xref:System.IdentityModel.Claims.Claim.CreateThumbprintClaim%2A> (does not check the length or content of the byte array)</span></span>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateUpnClaim%2A>  
  
 <span data-ttu-id="4ed70-108">调用上述方法时应该小心，确保传入的资源值使用正确的格式和/或包含正确的信息类型。</span><span class="sxs-lookup"><span data-stu-id="4ed70-108">Care should be taken when calling the above methods to ensure that the resource values passed in are of the correct format or contain the correct kind of information (or both).</span></span>  
  
 <span data-ttu-id="4ed70-109">以下方法采用特定类型：</span><span class="sxs-lookup"><span data-stu-id="4ed70-109">The following methods take specific types:</span></span>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateDenyOnlyWindowsSidClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateMailAddressClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateRsaClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateUriClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateWindowsSidClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateX500DistinguishedNameClaim%2A>  
  
## <a name="see-also"></a><span data-ttu-id="4ed70-110">请参阅</span><span class="sxs-lookup"><span data-stu-id="4ed70-110">See also</span></span>

- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.ClaimSet>
- [<span data-ttu-id="4ed70-111">使用标识模型管理声明和授权</span><span class="sxs-lookup"><span data-stu-id="4ed70-111">Managing Claims and Authorization with the Identity Model</span></span>](managing-claims-and-authorization-with-the-identity-model.md)
