---
description: 详细了解：Authenticode（非托管 API 参考）
title: Authenticode（非托管 API 参考）
ms.date: 03/30/2017
ms.assetid: 7e8cc303-6e77-4116-aa8b-7ea297a3a467
ms.openlocfilehash: d7a1684fde900bfc01161193d0747b156c6856a8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772830"
---
# <a name="authenticode-unmanaged-api-reference"></a>Authenticode（非托管 API 参考）

支持验证码 XrML 许可证创建和验证模块。  
  
## <a name="in-this-section"></a>本节内容  

 [_AxlGetIssuerPublicKeyHash 函数](axlgetissuerpublickeyhash-function.md)  
 检索与用于对指定证书进行签名的私钥关联的公钥的 SHA-1 哈希。  
  
 [_AxlPublicKeyBlobToPublicKeyToken 函数](axlpublickeyblobtopublickeytoken-function.md)  
 从 CSP PUBLICKEYBLOB 格式计算强名称公钥标记。  
  
 [_AxlRSAKeyValueToPublicKeyToken 函数](axlrsakeyvaluetopublickeytoken-function.md)  
 将模数和指数转换为强名称公钥标记。  
  
 [CertFreeAuthenticodeSignerInfo 函数](certfreeauthenticodesignerinfo-function.md)  
 释放为 AXL_AUTHENTICODE_SIGNER_INFO 结构分配的资源。  
  
 [CertFreeAuthenticodeTimestamperInfo 函数](certfreeauthenticodetimestamperinfo-function.md)  
 释放为 AXL_AUTHENTICODE_TIMESTAMPER_INFO 结构分配的资源。  
  
 [CertTimestampAuthenticodeLicense 函数](certtimestampauthenticodelicense-function.md)  
 为由 CertCreateAuthenticodeLicense 创建的验证码 XrML 许可证添加时间戳。  
  
 [CertVerifyAuthenticodeLicense 函数](certverifyauthenticodelicense-function.md)  
 验证验证码 XrML 许可证的有效性。  
  
 [AXL_AUTHENTICODE_SIGNER_INFO 结构](axl-authenticode-signer-info-structure.md)  
 定义验证码签署人的信息。  
  
 [AXL_AUTHENTICODE_TIMESTAMPER_INFO 结构](axl-authenticode-timestamper-info-structure.md)  
 定义验证码时间戳签署人的信息。  
  
## <a name="see-also"></a>另请参阅

- [非托管 API 参考](../index.md)
