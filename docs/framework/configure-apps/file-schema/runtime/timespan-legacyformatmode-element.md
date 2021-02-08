---
description: 了解详细信息： <TimeSpan_LegacyFormatMode> 元素
title: <TimeSpan_LegacyFormatMode> 元素
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <TimeSpan_LegacyFormatMode> element
- TimeSpan_LegacyFormatMode element
ms.assetid: 865e7207-d050-4442-b574-57ea29d5e2d6
ms.openlocfilehash: 1fa5c3a15941004ebab9e3622d4b3e7b27130e22
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802380"
---
# <a name="timespan_legacyformatmode-element"></a><span data-ttu-id="1f567-103">\<TimeSpan_LegacyFormatMode> 元素</span><span class="sxs-lookup"><span data-stu-id="1f567-103">\<TimeSpan_LegacyFormatMode> Element</span></span>

<span data-ttu-id="1f567-104">确定运行时是否在格式设置操作中保留 <xref:System.TimeSpan?displayProperty=nameWithType> 值。</span><span class="sxs-lookup"><span data-stu-id="1f567-104">Determines whether the runtime preserves legacy behavior in formatting operations with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<TimeSpan_LegacyFormatMode>**  

## <a name="syntax"></a><span data-ttu-id="1f567-105">语法</span><span class="sxs-lookup"><span data-stu-id="1f567-105">Syntax</span></span>

```xml
<TimeSpan_LegacyFormatMode
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1f567-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="1f567-106">Attributes and Elements</span></span>

<span data-ttu-id="1f567-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="1f567-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="1f567-108">特性</span><span class="sxs-lookup"><span data-stu-id="1f567-108">Attributes</span></span>

|<span data-ttu-id="1f567-109">属性</span><span class="sxs-lookup"><span data-stu-id="1f567-109">Attribute</span></span>|<span data-ttu-id="1f567-110">描述</span><span class="sxs-lookup"><span data-stu-id="1f567-110">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="1f567-111">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="1f567-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="1f567-112">指定运行时是否对值使用旧格式设置行为 <xref:System.TimeSpan?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="1f567-112">Specifies whether the runtime uses legacy formatting behavior with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="1f567-113">enabled 特性</span><span class="sxs-lookup"><span data-stu-id="1f567-113">enabled Attribute</span></span>

|<span data-ttu-id="1f567-114">值</span><span class="sxs-lookup"><span data-stu-id="1f567-114">Value</span></span>|<span data-ttu-id="1f567-115">说明</span><span class="sxs-lookup"><span data-stu-id="1f567-115">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="1f567-116">运行时不会还原旧的格式设置行为。</span><span class="sxs-lookup"><span data-stu-id="1f567-116">The runtime does not restore legacy formatting behavior.</span></span>|
|`true`|<span data-ttu-id="1f567-117">运行时将还原旧的格式设置行为。</span><span class="sxs-lookup"><span data-stu-id="1f567-117">The runtime restores legacy formatting behavior.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="1f567-118">子元素</span><span class="sxs-lookup"><span data-stu-id="1f567-118">Child Elements</span></span>

<span data-ttu-id="1f567-119">无。</span><span class="sxs-lookup"><span data-stu-id="1f567-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1f567-120">父元素</span><span class="sxs-lookup"><span data-stu-id="1f567-120">Parent Elements</span></span>

|<span data-ttu-id="1f567-121">元素</span><span class="sxs-lookup"><span data-stu-id="1f567-121">Element</span></span>|<span data-ttu-id="1f567-122">说明</span><span class="sxs-lookup"><span data-stu-id="1f567-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="1f567-123">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="1f567-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="1f567-124">包含有关运行时初始化选项的信息。</span><span class="sxs-lookup"><span data-stu-id="1f567-124">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1f567-125">备注</span><span class="sxs-lookup"><span data-stu-id="1f567-125">Remarks</span></span>

<span data-ttu-id="1f567-126">从 .NET Framework 4 开始， <xref:System.TimeSpan?displayProperty=nameWithType> 结构实现 <xref:System.IFormattable> 接口，并支持带有标准和自定义格式字符串的格式设置操作。</span><span class="sxs-lookup"><span data-stu-id="1f567-126">Starting with the .NET Framework 4, the <xref:System.TimeSpan?displayProperty=nameWithType> structure implements the <xref:System.IFormattable> interface and supports formatting operations with standard and custom format strings.</span></span> <span data-ttu-id="1f567-127">如果分析方法遇到不支持的格式说明符或格式字符串，则将引发 <xref:System.FormatException> 。</span><span class="sxs-lookup"><span data-stu-id="1f567-127">If a parsing method encounters an unsupported format specifier or format string, it throws a <xref:System.FormatException>.</span></span>

<span data-ttu-id="1f567-128">在 .NET Framework 的以前版本中， <xref:System.TimeSpan> 结构未实现， <xref:System.IFormattable> 并且不支持格式字符串。</span><span class="sxs-lookup"><span data-stu-id="1f567-128">In previous versions of the .NET Framework, the <xref:System.TimeSpan> structure did not implement <xref:System.IFormattable> and did not support format strings.</span></span> <span data-ttu-id="1f567-129">但是，很多开发人员都认为 <xref:System.TimeSpan> 确实支持一组格式字符串，并在 [复合格式设置操作](../../../../standard/base-types/composite-formatting.md) 中将它们用于方法（如） <xref:System.String.Format%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="1f567-129">However, many developers mistakenly assumed that <xref:System.TimeSpan> did support a set of format strings and used them in [composite formatting operations](../../../../standard/base-types/composite-formatting.md) with methods such as <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1f567-130">通常，如果某个类型实现 <xref:System.IFormattable> 并支持格式字符串，则使用不受支持的格式字符串的格式设置方法的调用通常会引发 <xref:System.FormatException> 。</span><span class="sxs-lookup"><span data-stu-id="1f567-130">Ordinarily, if a type implements <xref:System.IFormattable> and supports format strings, calls to formatting methods with unsupported format strings usually throw a <xref:System.FormatException>.</span></span> <span data-ttu-id="1f567-131">但是，因为未 <xref:System.TimeSpan> 实现 <xref:System.IFormattable> ，所以运行时将忽略格式字符串，而改为调用 <xref:System.TimeSpan.ToString?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="1f567-131">However, because <xref:System.TimeSpan> did not implement <xref:System.IFormattable>, the runtime ignored the format string and instead called the <xref:System.TimeSpan.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="1f567-132">这意味着，尽管格式字符串对格式设置操作没有影响，但它们的存在不会导致 <xref:System.FormatException> 。</span><span class="sxs-lookup"><span data-stu-id="1f567-132">This means that, although the format strings had no effect on the formatting operation, their presence did not result in a <xref:System.FormatException>.</span></span>

<span data-ttu-id="1f567-133">对于旧式代码传递复合格式设置方法和无效格式字符串的情况，并且无法重新编译该代码，可以使用 `<TimeSpan_LegacyFormatMode>` 元素来还原旧 <xref:System.TimeSpan> 行为。</span><span class="sxs-lookup"><span data-stu-id="1f567-133">For cases in which legacy code passes a composite formatting method and an invalid format string, and that code cannot be recompiled, you can use the `<TimeSpan_LegacyFormatMode>` element to restore the legacy <xref:System.TimeSpan> behavior.</span></span> <span data-ttu-id="1f567-134">将 `enabled` 此元素的特性设置为时 `true` ，复合格式设置方法将导致调用而不是 <xref:System.TimeSpan.ToString?displayProperty=nameWithType> <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> ，并且 <xref:System.FormatException> 不会引发。</span><span class="sxs-lookup"><span data-stu-id="1f567-134">When you set the `enabled` attribute of this element to `true`, the composite formatting method results in a call to <xref:System.TimeSpan.ToString?displayProperty=nameWithType> rather than <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, and a <xref:System.FormatException> is not thrown.</span></span>

## <a name="example"></a><span data-ttu-id="1f567-135">示例</span><span class="sxs-lookup"><span data-stu-id="1f567-135">Example</span></span>

<span data-ttu-id="1f567-136">下面的示例实例化一个 <xref:System.TimeSpan> 对象，并 <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> 使用不受支持的标准格式字符串尝试使用方法对其进行格式设置。</span><span class="sxs-lookup"><span data-stu-id="1f567-136">The following example instantiates a <xref:System.TimeSpan> object and attempts to format it with the <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> method by using an unsupported standard format string.</span></span>

[!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
[!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]

<span data-ttu-id="1f567-137">在 .NET Framework 3.5 或更早版本上运行此示例时，将显示以下输出：</span><span class="sxs-lookup"><span data-stu-id="1f567-137">When you run the example on the .NET Framework 3.5 or on an earlier version, it displays the following output:</span></span>

```console
12:30:45
```

<span data-ttu-id="1f567-138">如果在 .NET Framework 4 或更高版本上运行此示例，则这与输出明显不同：</span><span class="sxs-lookup"><span data-stu-id="1f567-138">This differs markedly from the output if you run the example on the .NET Framework 4 or later version:</span></span>

```console
Invalid Format
```

<span data-ttu-id="1f567-139">但是，如果将下面的配置文件添加到示例的目录中，然后在 .NET Framework 4 或更高版本上运行此示例，则输出将与示例在 .NET Framework 3.5 上运行时所生成的输出相同。</span><span class="sxs-lookup"><span data-stu-id="1f567-139">However, if you add the following configuration file to the example's directory and then run the example on the .NET Framework 4 or later version, the output is identical to that produced by the example when it is run on .NET Framework 3.5.</span></span>

```xml
<?xml version ="1.0"?>
<configuration>
   <runtime>
      <TimeSpan_LegacyFormatMode enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="1f567-140">请参阅</span><span class="sxs-lookup"><span data-stu-id="1f567-140">See also</span></span>

- [<span data-ttu-id="1f567-141">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="1f567-141">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="1f567-142">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="1f567-142">Configuration File Schema</span></span>](../index.md)
