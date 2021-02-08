---
description: 了解详细信息： <issuerNameRegistry>
title: <issuerNameRegistry>
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
ms.openlocfilehash: 73eb0d9d4d19f8e25f2db501e8cb3858d346ac2c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803849"
---
# \<issuerNameRegistry>

配置标记处理程序集合中的处理程序使用的颁发者名称注册表。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerNameRegistry>**  
  
## <a name="syntax"></a>语法  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerNameRegistry type=xs:string>  
          <optionalCustomConfigurationElements />  
        </issuerNameRegistry>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  

 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|属性|说明|  
|---------------|-----------------|  
|type|派生自类的类型 <xref:System.IdentityModel.Tokens.IssuerNameRegistry> 。 有关如何指定自定义的详细信息 `type` ，请参阅 [自定义类型引用]。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|说明|  
|-------------|-----------------|  
|[\<trustedIssuers>](trustedissuers.md)|当 `type` 属性指定基于配置的颁发者名称注册表 (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> 类) 时， [\<trustedIssuers>](trustedissuers.md) 必须指定元素。 [\<trustedIssuers>](trustedissuers.md)元素可以将 `<add>` 、 `<clear>` 或 `<remove>` 元素作为子元素。|  
  
### <a name="parent-elements"></a>父元素  
  
|元素|说明|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|为安全标记处理程序的集合提供配置。|  
  
## <a name="remarks"></a>备注  

 使用颁发者名称注册表验证所有颁发者令牌。 这是从类派生的对象 <xref:System.IdentityModel.Tokens.IssuerNameRegistry> 。 颁发者名称注册表用于将助记键名称关联到验证相应颁发者生成的令牌签名所需的加密材料。 颁发者名称注册表维护依赖方 (RP) 应用程序信任的颁发者的列表。 颁发者名称注册表的类型是使用属性指定的 `type` 。 `<issuerNameRegistry>`元素可以有一个或多个子元素，这些子元素提供指定类型的配置。 通过重写方法来提供处理这些子元素的逻辑 <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> 。  
  
 WIF 提供单一颁发者名称注册表类型，即 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> 类。 此类使用在配置中指定的一组受信任的颁发者证书。 它需要一个子配置元素， `<trustedIssuers>` 在该元素下配置受信任的颁发者证书的集合。 受信任的证书是使用 "证书指纹" 的 "ASN" 编码形式指定的，并且通过使用 `<add>` 、或元素在集合中添加或删除 `<clear>` `<remove>` 。  
  
 `<issuerNameRegistry>`元素由 <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> 类表示。  
  
> [!NOTE]
> 将 `<issuerNameRegistry>` 元素指定为元素的子元素 [\<identityConfiguration>](identityconfiguration.md) 已不推荐使用，但仍支持向后兼容。 元素上的设置将 `<securityTokenHandlerConfiguration>` 替代元素上的设置 `<identityConfiguration>` 。  
  
## <a name="example"></a>示例  

 下面的 XML 演示如何指定基于配置的颁发者名称注册表。  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a>请参阅

- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
