---
description: '详细了解： <remove> bypasslist 的元素 (网络设置) '
title: bypasslist 的 <remove> 元素（网络设置）
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- <bypasslist>, remove element
- remove element, bypasslist
- bypasslist, remove element
- remove element, bypasslist
ms.assetid: 61dcfb4a-e3d9-4abf-a2cd-7d685fe2f64b
ms.openlocfilehash: 48441f1b402b339a1bd2ea069678afb4b1d5f2e1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740283"
---
# <a name="remove-element-for-bypasslist-network-settings"></a>bypasslist 的 \<remove> 元素（网络设置）

从代理跳过列表中删除 IP 地址或 DNS 名称。

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**  

## <a name="syntax"></a>语法

```xml
<remove
  address="regular expression"
/>
```

## <a name="attributes-and-elements"></a>特性和元素

下列各节描述了特性、子元素和父元素。

### <a name="attributes"></a>特性

|**Attribute**|**说明**|
|-------------------|---------------------|
|`address`|描述 IP 地址或 DNS 名称的正则表达式。|

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|**元素**|**说明**|
|-----------------|---------------------|
|[bypasslist](bypasslist-element-network-settings.md)|提供了一组正则表达式，描述不使用代理的地址。|

## <a name="remarks"></a>备注

`remove`元素从绕过代理服务器的地址列表中删除描述 IP 地址或 DNS 服务器名称的正则表达式。 地址在配置文件中或配置层次结构中的更高级别定义。

特性的值 `address` 应为描述一组 IP 地址或主机名的正则表达式。

有关正则表达式的详细信息，请参阅。[.NET Framework 正则表达式](../../../../standard/base-types/regular-expressions.md)。

## <a name="configuration-files"></a>配置文件

此元素可在应用程序配置文件或计算机配置文件 (Machine.config) 中使用。

## <a name="example"></a>示例

下面的示例删除 adventure-works.com 域的任何先前定义，然后将 contoso.com 域添加到跳过列表。

```xml
<configuration>
  <system.net>
    <defaultProxy>
      <bypasslist>
        <remove address="[a-z]+\.adventure-works\.com$" />
        <add address="[a-z]+\.contoso\.com$" />
      </bypasslist>
    </defaultProxy>
  </system.net>
</configuration>
```

## <a name="see-also"></a>请参阅

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [网络设置架构](index.md)
