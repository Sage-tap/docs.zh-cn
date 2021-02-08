---
description: 了解详细信息：在 ClaimSet 中查找声明
title: 在 ClaimSet 中查找声明
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- claims [WCF], finding in a claimset
- claims [WCF]
ms.assetid: a76ce107-aeb3-47d0-bfa9-134c53664e20
ms.openlocfilehash: 3ac4553e50f98f54e0a23aa9d759d7ae2f7caa8c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802926"
---
# <a name="finding-claims-in-a-claimset"></a>在 ClaimSet 中查找声明

在使用基于声明的授权时，一项常见任务就是检查 <xref:System.IdentityModel.Claims.ClaimSet> 的内容以查找特定类型的声明。 若要检查 <xref:System.IdentityModel.Claims.ClaimSet> 以查找是否存在特定声明，请使用 <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> 方法。 相对于直接在 <xref:System.IdentityModel.Claims.ClaimSet> 上循环，该方法可以提供更好的性能。 下面的示例演示此用法。 请注意，`claimType` 和 `claimRight` 参数可以为 `null`。 在此例中，这些参数将与所有声明类型以及声明权限相匹配。  
  
## <a name="example"></a>示例  

 [!code-csharp[c_FindClaimsPerf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_findclaimsperf/cs/c_findclaimsperf.cs#2)]
 [!code-vb[c_FindClaimsPerf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_findclaimsperf/vb/c_findclaimsperf.vb#2)]  
  
## <a name="see-also"></a>请参阅

- [使用标识模型管理声明和授权](managing-claims-and-authorization-with-the-identity-model.md)
