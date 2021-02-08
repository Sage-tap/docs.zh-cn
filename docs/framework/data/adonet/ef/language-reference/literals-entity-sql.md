---
description: '了解详细信息： (实体 SQL 的文字) '
title: 文本 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 092ef693-6e5f-41b4-b868-5b9e82928abf
ms.openlocfilehash: cae2ec7ab8cf19166dc3100a85473fca2ed0a7be
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791876"
---
# <a name="literals-entity-sql"></a><span data-ttu-id="416f6-103">文本 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="416f6-103">Literals (Entity SQL)</span></span>

<span data-ttu-id="416f6-104">本主题介绍 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 对于文字的支持。</span><span class="sxs-lookup"><span data-stu-id="416f6-104">This topic describes [!INCLUDE[esql](../../../../../../includes/esql-md.md)] support for literals.</span></span>  
  
## <a name="null"></a><span data-ttu-id="416f6-105">Null</span><span class="sxs-lookup"><span data-stu-id="416f6-105">Null</span></span>  

 <span data-ttu-id="416f6-106">空文字用于表示对任何类型均为空的值。</span><span class="sxs-lookup"><span data-stu-id="416f6-106">The null literal is used to represent the value null for any type.</span></span> <span data-ttu-id="416f6-107">空文字与任何类型兼容。</span><span class="sxs-lookup"><span data-stu-id="416f6-107">A null literal is compatible with any type.</span></span>  
  
 <span data-ttu-id="416f6-108">强制转换可以在空文字之上创建类型空值。</span><span class="sxs-lookup"><span data-stu-id="416f6-108">Typed nulls can be created by a cast over a null literal.</span></span> <span data-ttu-id="416f6-109">有关详细信息，请参阅 [CAST](cast-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="416f6-109">For more information, see [CAST](cast-entity-sql.md).</span></span>  
  
 <span data-ttu-id="416f6-110">有关可以使用自由浮动 null 文本的规则，请参阅 [Null 文本和类型推理](null-literals-and-type-inference-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="416f6-110">For rules about where free floating null literals can be used, see [Null Literals and Type Inference](null-literals-and-type-inference-entity-sql.md).</span></span>  
  
## <a name="boolean"></a><span data-ttu-id="416f6-111">布尔</span><span class="sxs-lookup"><span data-stu-id="416f6-111">Boolean</span></span>  

 <span data-ttu-id="416f6-112">布尔值文字由关键字 `true` 和 `false` 表示。</span><span class="sxs-lookup"><span data-stu-id="416f6-112">Boolean literals are represented by the keywords `true` and `false`.</span></span>  
  
## <a name="integer"></a><span data-ttu-id="416f6-113">Integer</span><span class="sxs-lookup"><span data-stu-id="416f6-113">Integer</span></span>  

 <span data-ttu-id="416f6-114">整型文字可以为类型 <xref:System.Int32> 或 <xref:System.Int64>。</span><span class="sxs-lookup"><span data-stu-id="416f6-114">Integer literals can be of type <xref:System.Int32> or <xref:System.Int64>.</span></span> <span data-ttu-id="416f6-115"><xref:System.Int32> 文字是一系列数字字符。</span><span class="sxs-lookup"><span data-stu-id="416f6-115">An <xref:System.Int32> literal is a series of numeric characters.</span></span> <span data-ttu-id="416f6-116"><xref:System.Int64> 文字是一系列数字字符，后跟一个大写 L。</span><span class="sxs-lookup"><span data-stu-id="416f6-116">An <xref:System.Int64> literal is series of numeric characters followed by an uppercase L.</span></span>  
  
## <a name="decimal"></a><span data-ttu-id="416f6-117">小数</span><span class="sxs-lookup"><span data-stu-id="416f6-117">Decimal</span></span>  

 <span data-ttu-id="416f6-118">固定点数字（小数）是一系列数字字符、一个圆点 (.) 和另一系列数字字符，后跟一个大写“M”。</span><span class="sxs-lookup"><span data-stu-id="416f6-118">A fixed-point number (decimal) is a series of numeric characters, a dot (.) and another series of numeric characters followed by an uppercase "M".</span></span>  
  
## <a name="float-double"></a><span data-ttu-id="416f6-119">浮点，双精度</span><span class="sxs-lookup"><span data-stu-id="416f6-119">Float, Double</span></span>  

 <span data-ttu-id="416f6-120">双精度浮点数字是一系列数字字符、一个圆点 (.) 和另一系列数字字符，后面可能跟一个指数。</span><span class="sxs-lookup"><span data-stu-id="416f6-120">A double-precision floating point number is a series of numeric characters, a dot (.) and another series of numeric characters possibly followed by an exponent.</span></span> <span data-ttu-id="416f6-121">单精度浮点数字（或浮点数）是双精度浮点数字语法后跟小写 f。</span><span class="sxs-lookup"><span data-stu-id="416f6-121">A single-precisions floating point number (or float) is a double-precision floating point number syntax followed by the lowercase f.</span></span>  
  
## <a name="string"></a><span data-ttu-id="416f6-122">字符串</span><span class="sxs-lookup"><span data-stu-id="416f6-122">String</span></span>  

 <span data-ttu-id="416f6-123">字符串是包含在引号内的一系列字符。</span><span class="sxs-lookup"><span data-stu-id="416f6-123">A string is a series of characters enclosed in quote marks.</span></span> <span data-ttu-id="416f6-124">引号可以同时为单引号 (`'`) 或同时为双引号 (")。</span><span class="sxs-lookup"><span data-stu-id="416f6-124">Quotes can be either both single-quotes (`'`) or both double-quotes (").</span></span> <span data-ttu-id="416f6-125">字符串文字可以是 Unicode 或非 Unicode。</span><span class="sxs-lookup"><span data-stu-id="416f6-125">Character string literals can be either Unicode or non-Unicode.</span></span> <span data-ttu-id="416f6-126">若要将字符串文字声明为 Unicode，请在文字之前加上大写“N”作为前缀。</span><span class="sxs-lookup"><span data-stu-id="416f6-126">To declare a character string literal as Unicode, prefix the literal with an uppercase "N".</span></span> <span data-ttu-id="416f6-127">默认值为非 Unicode 字符串文字。</span><span class="sxs-lookup"><span data-stu-id="416f6-127">The default is non-Unicode character string literals.</span></span> <span data-ttu-id="416f6-128">在 N 与字符串文字负载之间不能存在空格，并且 N 必须为大写。</span><span class="sxs-lookup"><span data-stu-id="416f6-128">There can be no spaces between the N and the string literal payload, and the N must be uppercase.</span></span>  
  
```sql  
'hello' -- non-Unicode character string literal  
N'hello' -- Unicode character string literal  
"x"  
N"This is a string!"  
'so is THIS'  
```  
  
## <a name="datetime"></a><span data-ttu-id="416f6-129">DateTime</span><span class="sxs-lookup"><span data-stu-id="416f6-129">DateTime</span></span>  

 <span data-ttu-id="416f6-130">日期时间文字独立于区域设置并由日期部分和时间部分组成。</span><span class="sxs-lookup"><span data-stu-id="416f6-130">A datetime literal is independent of locale and is composed of a date part and a time part.</span></span> <span data-ttu-id="416f6-131">日期部分和时间部分都是必需的，并且没有默认值。</span><span class="sxs-lookup"><span data-stu-id="416f6-131">Both date and time parts are mandatory and there are no default values.</span></span>  
  
 <span data-ttu-id="416f6-132">日期部分的格式必须为： `YYYY` - `MM` - `DD` ，其中 `YYYY` 是介于0001和9999之间的四位数年份值， `MM` 是介于1和12之间的月份， `DD` 是对给定月份有效的日期值 `MM` 。</span><span class="sxs-lookup"><span data-stu-id="416f6-132">The date part must have the format: `YYYY`-`MM`-`DD`, where `YYYY` is a four digit year value between 0001 and 9999, `MM` is the month between 1 and 12 and `DD` is the day value that is valid for the given month `MM`.</span></span>  
  
 <span data-ttu-id="416f6-133">时间部分的格式必须为：`HH`:`MM`[:`SS`[.fffffff]]，其中 `HH` 为介于 0 至 23 之间的小时值，`MM` 为介于 0 至 59 之间的分钟值，`SS` 为介于 0 至 59 之间的秒值，而 fffffff 为介于 0 至 9999999 之间的秒的小数部分值。</span><span class="sxs-lookup"><span data-stu-id="416f6-133">The time part must have the format: `HH`:`MM`[:`SS`[.fffffff]], where `HH` is the hour value between 0 and 23, `MM` is the minute value between 0 and 59, `SS` is the second value between 0 and 59 and fffffff is the fractional second value between 0 and 9999999.</span></span> <span data-ttu-id="416f6-134">所有值范围都包含两端。</span><span class="sxs-lookup"><span data-stu-id="416f6-134">All value ranges are inclusive.</span></span> <span data-ttu-id="416f6-135">秒的小数部分是可选的。</span><span class="sxs-lookup"><span data-stu-id="416f6-135">Fractional seconds are optional.</span></span> <span data-ttu-id="416f6-136">除非指定了秒的小数部分，否则秒是可选的；在指定了秒的小数部分时秒是必需的。</span><span class="sxs-lookup"><span data-stu-id="416f6-136">Seconds are optional unless fractional seconds are specified; in this case, seconds are required.</span></span> <span data-ttu-id="416f6-137">在未指定秒或秒的小数部分时，将使用默认值零。</span><span class="sxs-lookup"><span data-stu-id="416f6-137">When seconds or fractional seconds are not specified, the default value of zero will be used instead.</span></span>  
  
 <span data-ttu-id="416f6-138">在 DATETIME 符号与文字负载之间可以存在任意数目的空格，但是不能存在新行。</span><span class="sxs-lookup"><span data-stu-id="416f6-138">There can be any number of spaces between the DATETIME symbol and the literal payload, but no new lines.</span></span>  
  
```sql  
DATETIME'2006-10-1 23:11'  
DATETIME'2006-12-25 01:01:00.0000000' -- same as DATETIME'2006-12-25 01:01'  
```  
  
## <a name="time"></a><span data-ttu-id="416f6-139">时间</span><span class="sxs-lookup"><span data-stu-id="416f6-139">Time</span></span>  

 <span data-ttu-id="416f6-140">时间文字独立于区域设置并仅由时间部分组成。</span><span class="sxs-lookup"><span data-stu-id="416f6-140">A time literal is independent of locale and composed of a time part only.</span></span> <span data-ttu-id="416f6-141">时间部分为必选项，且没有默认值。</span><span class="sxs-lookup"><span data-stu-id="416f6-141">The time part is mandatory and there is no default value.</span></span> <span data-ttu-id="416f6-142">其格式必须为 HH:MM[:SS[.fffffff]]，其中 HH 为介于 0 至 23 之间的小时值，MM 为介于 0 至 59 之间的分钟值，SS 为介于 0 至 59 之间的秒值，而 fffffff 为介于 0 至 9999999 之间的秒的小数部分值。</span><span class="sxs-lookup"><span data-stu-id="416f6-142">It must have the format HH:MM[:SS[.fffffff]], where HH is the hour value between 0 and 23, MM is the minute value between 0 and 59, SS is the second value between 0 and 59, and fffffff is the second fraction value between 0 and 9999999.</span></span> <span data-ttu-id="416f6-143">所有值范围都包含两端。</span><span class="sxs-lookup"><span data-stu-id="416f6-143">All value ranges are inclusive.</span></span> <span data-ttu-id="416f6-144">秒的小数部分是可选的。</span><span class="sxs-lookup"><span data-stu-id="416f6-144">Fractional seconds are optional.</span></span> <span data-ttu-id="416f6-145">除非指定了秒的小数部分，否则秒是可选的；在指定了秒的小数部分时秒是必需的。</span><span class="sxs-lookup"><span data-stu-id="416f6-145">Seconds are optional unless fractional seconds are specified; in this case, seconds are required.</span></span> <span data-ttu-id="416f6-146">在未指定秒或秒的小数部分时，将使用默认值零。</span><span class="sxs-lookup"><span data-stu-id="416f6-146">When seconds or fractions are not specified, the default value of zero will be used instead.</span></span>  
  
 <span data-ttu-id="416f6-147">在 TIME 符号与文字负载之间可以存在任意数目的空格，但是不能存在新行。</span><span class="sxs-lookup"><span data-stu-id="416f6-147">There can be any number of spaces between the TIME symbol and the literal payload, but no new lines.</span></span>  
  
```sql  
TIME‘23:11’  
TIME‘01:01:00.1234567’  
```  
  
## <a name="datetimeoffset"></a><span data-ttu-id="416f6-148">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="416f6-148">DateTimeOffset</span></span>  

 <span data-ttu-id="416f6-149">datetimeoffset 文字独立于区域设置并由日期部分、时间部分和偏移量部分组成。</span><span class="sxs-lookup"><span data-stu-id="416f6-149">A datetimeoffset literal is independent of locale and composed of a date part, a time part, and an offset part.</span></span> <span data-ttu-id="416f6-150">所有日期、时间和偏移量部分都是必选项，并且没有默认值。</span><span class="sxs-lookup"><span data-stu-id="416f6-150">All date, time, and offset parts are mandatory and there are no default values.</span></span> <span data-ttu-id="416f6-151">日期部分的格式必须为 YYYY-MM-DD，其中 YYYY 是介于 0001 与 9999 之间的四位年度值，MM 是介于 1 与 12 之间的月份，而 DD 是对给定月份有效的日期值。</span><span class="sxs-lookup"><span data-stu-id="416f6-151">The date part must have the format YYYY-MM-DD, where YYYY is a four digit year value between 0001 and 9999, MM is the month between 1 and 12, and DD is the day value that is valid for the given month.</span></span> <span data-ttu-id="416f6-152">时间部分的格式必须为 HH:MM[:SS[.fffffff]]，其中 HH 为介于 0 至 23 之间的小时值，MM 为介于 0 至 59 之间的分钟值，SS 为介于 0 至 59 之间的秒值，而 fffffff 为介于 0 至 9999999 之间的秒的小数部分值。</span><span class="sxs-lookup"><span data-stu-id="416f6-152">The time part must have the format HH:MM[:SS[.fffffff]], where HH is the hour value between 0 and 23, MM is the minute value between 0 and 59, SS is the second value between 0 and 59, and fffffff is the fractional second value between 0 and 9999999.</span></span> <span data-ttu-id="416f6-153">所有值范围都包含两端。</span><span class="sxs-lookup"><span data-stu-id="416f6-153">All value ranges are inclusive.</span></span> <span data-ttu-id="416f6-154">秒的小数部分是可选的。</span><span class="sxs-lookup"><span data-stu-id="416f6-154">Fractional seconds are optional.</span></span> <span data-ttu-id="416f6-155">除非指定了秒的小数部分，否则秒是可选的；在指定了秒的小数部分时秒是必需的。</span><span class="sxs-lookup"><span data-stu-id="416f6-155">Seconds are optional unless fractional seconds are specified; in this case, seconds are required.</span></span> <span data-ttu-id="416f6-156">在未指定秒或秒的小数部分时，将使用默认值零。</span><span class="sxs-lookup"><span data-stu-id="416f6-156">When seconds or fractions are not specified, the default value of zero will be used instead.</span></span> <span data-ttu-id="416f6-157">偏移量部分的格式必须为 {+&#124;-} HH： MM，其中 HH 和 MM 与时间部分具有相同的含义。</span><span class="sxs-lookup"><span data-stu-id="416f6-157">The offset part must have the format {+&#124;-}HH:MM, where HH and MM have the same meaning as in the time part.</span></span> <span data-ttu-id="416f6-158">但是，偏移量的范围必须介于 -14:00 至 + 14:00 之间。</span><span class="sxs-lookup"><span data-stu-id="416f6-158">The range of the offset, however, must be between -14:00 and + 14:00</span></span>  
  
 <span data-ttu-id="416f6-159">在 DATETIMEOFFSET 符号与文字负载之间可以存在任意数目的空格，但是不能存在新行。</span><span class="sxs-lookup"><span data-stu-id="416f6-159">There can be any number of spaces between the DATETIMEOFFSET symbol and the literal payload, but no new lines.</span></span>  
  
```sql  
DATETIMEOFFSET‘2006-10-1 23:11 +02:00’  
DATETIMEOFFSET‘2006-12-25 01:01:00.0000000 -08:30’  
```  
  
> [!NOTE]
> <span data-ttu-id="416f6-160">有效的 Entity SQL 文字值可能处于 CLR 或数据源所支持的范围之外。</span><span class="sxs-lookup"><span data-stu-id="416f6-160">A valid Entity SQL literal value can fall outside the supported ranges for CLR or the data source.</span></span> <span data-ttu-id="416f6-161">这可能会导致异常。</span><span class="sxs-lookup"><span data-stu-id="416f6-161">This might result in an exception</span></span>  
  
## <a name="binary"></a><span data-ttu-id="416f6-162">二进制</span><span class="sxs-lookup"><span data-stu-id="416f6-162">Binary</span></span>  

 <span data-ttu-id="416f6-163">二进制字符串文字是由单引号分隔的一系列十六进制数字，后跟关键字“binary”或快捷方式符号 `X`/`x`。</span><span class="sxs-lookup"><span data-stu-id="416f6-163">A binary string literal is a sequence of hexadecimal digits delimited by single quotes following the keyword binary or the shortcut symbol `X` or `x`.</span></span> <span data-ttu-id="416f6-164">快捷方式符号 `X` 是不区分大小写的。</span><span class="sxs-lookup"><span data-stu-id="416f6-164">The shortcut symbol `X` is case insensitive.</span></span> <span data-ttu-id="416f6-165">在关键字 `binary` 与二进制字符串值之间可以有零个或零个以上空格。</span><span class="sxs-lookup"><span data-stu-id="416f6-165">A zero or more spaces are allowed between the keyword `binary` and the binary string value.</span></span>  
  
 <span data-ttu-id="416f6-166">十六进制字符也不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="416f6-166">Hexadecimal characters are also case insensitive.</span></span> <span data-ttu-id="416f6-167">如果文字由奇数个十六进制数字组成，则将通过在文字之前附加十六进制数字零作为前缀，使文字与下一个偶数十六进制数字对齐。</span><span class="sxs-lookup"><span data-stu-id="416f6-167">If the literal is composed of an odd number of hexadecimal digits, the literal will be aligned to the next even hexadecimal digit by prefixing the literal with a hexadecimal zero digit.</span></span> <span data-ttu-id="416f6-168">对于二进制字符串的大小，不存在正式的限制。</span><span class="sxs-lookup"><span data-stu-id="416f6-168">There is no formal limit on the size of the binary string.</span></span>  
  
```sql  
Binary'00ffaabb'  
X'ABCabc'  
BINARY    '0f0f0f0F0F0F0F0F0F0F'  
X'' –- empty binary string  
```  
  
## <a name="guid"></a><span data-ttu-id="416f6-169">Guid</span><span class="sxs-lookup"><span data-stu-id="416f6-169">Guid</span></span>  

 <span data-ttu-id="416f6-170">`GUID` 文本表示全局唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="416f6-170">A `GUID` literal represents a globally unique identifier.</span></span> <span data-ttu-id="416f6-171">它是由关键字构成的序列， `GUID` 后跟十六进制数字，格式为： 8-4-4-4-12 并用单引号括起来。</span><span class="sxs-lookup"><span data-stu-id="416f6-171">It is a sequence formed by the keyword `GUID` followed by hexadecimal digits in the form known as *registry* format: 8-4-4-4-12 enclosed in single quotes.</span></span> <span data-ttu-id="416f6-172">十六进制数字区分大小写。</span><span class="sxs-lookup"><span data-stu-id="416f6-172">Hexadecimal digits are case insensitive.</span></span>  
  
 <span data-ttu-id="416f6-173">在 GUID 符号与文字负载之间可以存在任意数目的空格，但是不能存在新行。</span><span class="sxs-lookup"><span data-stu-id="416f6-173">There can be any number of spaces between the GUID symbol and the literal payload, but no new lines.</span></span>  
  
```sql  
Guid'1afc7f5c-ffa0-4741-81cf-f12eAAb822bf'  
GUID  '1AFC7F5C-FFA0-4741-81CF-F12EAAB822BF'  
```  
  
## <a name="see-also"></a><span data-ttu-id="416f6-174">请参阅</span><span class="sxs-lookup"><span data-stu-id="416f6-174">See also</span></span>

- [<span data-ttu-id="416f6-175">Entity SQL 概述</span><span class="sxs-lookup"><span data-stu-id="416f6-175">Entity SQL Overview</span></span>](entity-sql-overview.md)
