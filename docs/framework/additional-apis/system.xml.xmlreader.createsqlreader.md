---
description: 了解详细信息： CreateSqlReader 方法
title: 'CreateSqlReader 方法 ( # A0) '
ms.date: 10/17/2019
topic_type:
- apiref
api_name:
- System.Xml.XmlReader.CreateSqlReader
api_location:
- system.xml.dll
api_type:
- Assembly
ms.openlocfilehash: 61d594c0438c86863ce4052387439f5483d8a34c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740428"
---
# <a name="xmlreadercreatesqlreader-method"></a>XmlReader.CreateSqlReader 方法

使用指定的流、设置和用于分析的上下文信息创建一个新的 <xref:System.Xml.XmlReader> 实例。

```csharp
internal static XmlReader CreateSqlReader(Stream input,
  XmlReaderSettings settings, XmlParserContext inputContext)
```

## <a name="parameters"></a>参数

- `input` <xref:System.IO.Stream>  
  包含 XML 数据的流。

- `settings` <xref:System.Xml.XmlReaderSettings>  
  新 <xref:System.Xml.XmlReader> 实例的设置。 此值可为 `null`。

- `inputContext` <xref:System.Xml.XmlParserContext>  
  分析 XML 片段所需的上下文信息. 此值可为 `null`。

## <a name="returns"></a>返回

<xref:System.Xml.XmlReader>  
一个用于读取数据流中所含数据的对象。

## <a name="remarks"></a>备注

> [!WARNING]
> `XmlReader.CreateSqlReader`方法是内部的，不应在代码中直接使用。
>
> 在任何情况下，Microsoft 不支持在生产应用程序中使用此方法。

## <a name="requirements"></a>要求

**命名空间：** <xref:System.Xml>

**程序集：** System.Xml.dll

**.NET Framework 版本：** 自2.0 起可用。
