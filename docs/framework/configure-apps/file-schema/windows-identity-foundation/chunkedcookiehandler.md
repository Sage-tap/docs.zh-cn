---
description: 了解详细信息： <chunkedCookieHandler>
title: <chunkedCookieHandler>
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
ms.openlocfilehash: b0090706d3d7a9f62e17ae63ec16e4b3a869a812
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664283"
---
# \<chunkedCookieHandler>

配置 <xref:System.IdentityModel.Services.ChunkedCookieHandler> 。 仅当 `mode` 元素的属性 `<cookieHandler>` 为 "默认值" 或 "分块" 时，此元素才能存在。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cookieHandler>**](cookiehandler.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<chunkedCookieHandler>**  
  
## <a name="syntax"></a>语法  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode="Chunked||Default" >  
      <chunkedCookieHandler size=xs:int >  
      </chunkedCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  

 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|属性|说明|  
|---------------|-----------------|  
|chunkSize|任何一个 HTTP cookie 的 HTTP cookie 数据的最大大小（字符数）。 调整块区大小时必须小心谨慎。 Web 浏览器对 cookie 和每个域允许的数量有不同的限制。 例如，原始 Netscape 规范规定这些限制： 300 cookie 总数、每个 cookie 标头4096个字节 (包括元数据，而不仅仅是 cookie 值) 和每个域20个 cookie。 默认为 2000。 必需。|  
  
### <a name="child-elements"></a>子元素  

 无  
  
### <a name="parent-elements"></a>父元素  
  
|元素|说明|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|配置 <xref:System.IdentityModel.Services.CookieHandler> <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) 用于读取和写入 cookie 的。|  
  
## <a name="remarks"></a>备注  

 <xref:System.IdentityModel.Services.ChunkedCookieHandler>通过将 `mode` 元素的属性设置 `<cookieHandler>` 为 "默认值" 或 "分块" 指定时，可以指定 cookie 处理程序用来读取和写入 cookie 的块区大小，方法是包含一个 `<chunkedCookieHandler>` 子元素并设置其 `chunkSize` 属性。 如果该 `<chunkedCookieHandler>` 元素不存在，则使用默认的块区大小（2000字节）。 当 `mode` 特性设置为 "Custom" 时，不能指定此元素。  
  
 `<chunkedCookieHandler>`元素由 <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> 类表示。  
  
## <a name="example"></a>示例  

 下面的示例配置一个分块 cookie 处理程序，该处理程序以3000字节的块写入 cookie。  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a>请参阅

- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
