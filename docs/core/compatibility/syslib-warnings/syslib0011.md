---
title: SYSLIB0011 警告
description: 了解有关生成编译时警告 SYSLIB0011 的过时信息。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 85b5e07b1ecd6852d8c8e93cc3e89ced4b021ef9
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189852"
---
# <a name="syslib0011-binaryformatter-serialization-is-obsolete"></a><span data-ttu-id="f6e2a-103">SYSLIB0011：BinaryFormatter 序列化已过时</span><span class="sxs-lookup"><span data-stu-id="f6e2a-103">SYSLIB0011: BinaryFormatter serialization is obsolete</span></span>

<span data-ttu-id="f6e2a-104">由于 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 存在[安全漏洞](../../../standard/serialization/binaryformatter-security-guide.md#binaryformatter-security-vulnerabilities)，从 .NET 5.0 开始，以下 API 标记为已过时。</span><span class="sxs-lookup"><span data-stu-id="f6e2a-104">Due to [security vulnerabilities](../../../standard/serialization/binaryformatter-security-guide.md#binaryformatter-security-vulnerabilities) in <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>, the following APIs are marked as obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="f6e2a-105">在代码中使用这些 API 会在编译时生成警告 `SYSLIB0011`。</span><span class="sxs-lookup"><span data-stu-id="f6e2a-105">Using them in code generates warning `SYSLIB0011` at compile time.</span></span>

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>

## <a name="workarounds"></a><span data-ttu-id="f6e2a-106">问题解决</span><span class="sxs-lookup"><span data-stu-id="f6e2a-106">Workarounds</span></span>

<span data-ttu-id="f6e2a-107">请考虑使用 <xref:System.Text.Json.JsonSerializer> 或 <xref:System.Xml.Serialization.XmlSerializer>，而不是 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>。</span><span class="sxs-lookup"><span data-stu-id="f6e2a-107">Consider using <xref:System.Text.Json.JsonSerializer> or <xref:System.Xml.Serialization.XmlSerializer> instead of <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span></span>

<span data-ttu-id="f6e2a-108">若要详细了解建议的操作，请参阅[修复 BinaryFormatter 过时和禁用错误](../../../standard/serialization/binaryformatter-security-guide.md)。</span><span class="sxs-lookup"><span data-stu-id="f6e2a-108">For more information about recommended actions, see [Resolving BinaryFormatter obsoletion and disablement errors](../../../standard/serialization/binaryformatter-security-guide.md).</span></span>

[!INCLUDE [suppress-syslib-warning](../../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a><span data-ttu-id="f6e2a-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f6e2a-109">See also</span></span>

- [<span data-ttu-id="f6e2a-110">修复 BinaryFormatter 过时和禁用错误</span><span class="sxs-lookup"><span data-stu-id="f6e2a-110">Resolving BinaryFormatter obsoletion and disablement errors</span></span>](../../../standard/serialization/binaryformatter-security-guide.md)
- [<span data-ttu-id="f6e2a-111">BinaryFormatter 序列化方法已过时，并且已在 ASP.NET 应用中禁用</span><span class="sxs-lookup"><span data-stu-id="f6e2a-111">BinaryFormatter serialization methods are obsolete and prohibited in ASP.NET apps</span></span>](../core-libraries/5.0/binaryformatter-serialization-obsolete.md)
