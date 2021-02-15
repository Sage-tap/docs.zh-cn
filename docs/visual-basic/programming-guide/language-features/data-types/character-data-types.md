---
description: '了解更多相关信息：字符数据类型 (Visual Basic) '
title: 字符数据类型
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], character
- String data type [Visual Basic], character data types
- character data types [Visual Basic]
- Char data type [Visual Basic], character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
ms.openlocfilehash: 2197c0210cb0c2287baff9856889334f5f95bd4d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466388"
---
# <a name="character-data-types-visual-basic"></a><span data-ttu-id="43de5-103">字符数据类型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43de5-103">Character Data Types (Visual Basic)</span></span>

<span data-ttu-id="43de5-104">Visual Basic 提供了用于处理可打印和可显示字符的 *字符数据类型* 。</span><span class="sxs-lookup"><span data-stu-id="43de5-104">Visual Basic provides *character data types* to deal with printable and displayable characters.</span></span> <span data-ttu-id="43de5-105">虽然这两种方法都能处理 Unicode 字符，但 `Char` 包含一个字符，但 `String` 包含无数个字符。</span><span class="sxs-lookup"><span data-stu-id="43de5-105">While they both deal with Unicode characters, `Char` holds a single character whereas `String` contains an indefinite number of characters.</span></span>  
  
 <span data-ttu-id="43de5-106">有关显示 Visual Basic 数据类型的并行比较的表，请参阅 [数据类型](../../../language-reference/data-types/index.md)。</span><span class="sxs-lookup"><span data-stu-id="43de5-106">For a table that displays a side-by-side comparison of the Visual Basic data types, see [Data Types](../../../language-reference/data-types/index.md).</span></span>  
  
## <a name="char-type"></a><span data-ttu-id="43de5-107">Char 类型</span><span class="sxs-lookup"><span data-stu-id="43de5-107">Char Type</span></span>  

 <span data-ttu-id="43de5-108">`Char`数据类型是单个双字节 (16 位) Unicode 字符。</span><span class="sxs-lookup"><span data-stu-id="43de5-108">The `Char` data type is a single two-byte (16-bit) Unicode character.</span></span> <span data-ttu-id="43de5-109">如果变量始终只存储一个字符，则将其声明为 `Char` 。</span><span class="sxs-lookup"><span data-stu-id="43de5-109">If a variable always stores exactly one character, declare it as `Char`.</span></span> <span data-ttu-id="43de5-110">例如：</span><span class="sxs-lookup"><span data-stu-id="43de5-110">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#1)]
  
 <span data-ttu-id="43de5-111">或变量中的每个可能值 `Char` `String` 都是 Unicode 字符集中的一个 *码位* 或字符代码。</span><span class="sxs-lookup"><span data-stu-id="43de5-111">Each possible value in a `Char` or `String` variable is a *code point*, or character code, in the Unicode character set.</span></span> <span data-ttu-id="43de5-112">Unicode 字符包含基本 ASCII 字符集、各种其他字母数字、重音、货币符号、分数、音调符号和数学符号以及技术符号。</span><span class="sxs-lookup"><span data-stu-id="43de5-112">Unicode characters include the basic ASCII character set, various other alphabet letters, accents, currency symbols, fractions, diacritics, and mathematical and technical symbols.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="43de5-113">Unicode 字符集为 *代理项对* 保留了 D800 到 DFFF (55296 到 55551 decimal) 的代码点，这需要 2 16 位值来表示单个码位。</span><span class="sxs-lookup"><span data-stu-id="43de5-113">The Unicode character set reserves the code points D800 through DFFF (55296 through 55551 decimal) for *surrogate pairs*, which require two 16-bit values to represent a single code point.</span></span> <span data-ttu-id="43de5-114">`Char`变量不能包含代理项对，且 `String` 使用两个位置来保存这种对。</span><span class="sxs-lookup"><span data-stu-id="43de5-114">A `Char` variable cannot hold a surrogate pair, and a `String` uses two positions to hold such a pair.</span></span>  
  
 <span data-ttu-id="43de5-115">有关详细信息，请参阅 [Char Data Type](../../../language-reference/data-types/char-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="43de5-115">For more information, see [Char Data Type](../../../language-reference/data-types/char-data-type.md).</span></span>  
  
## <a name="string-type"></a><span data-ttu-id="43de5-116">字符串类型</span><span class="sxs-lookup"><span data-stu-id="43de5-116">String Type</span></span>  

 <span data-ttu-id="43de5-117">`String`数据类型是由零个或多个双字节 (16 位) Unicode 字符组成的序列。</span><span class="sxs-lookup"><span data-stu-id="43de5-117">The `String` data type is a sequence of zero or more two-byte (16-bit) Unicode characters.</span></span> <span data-ttu-id="43de5-118">如果变量可以包含无限数量的字符，则将其声明为 `String` 。</span><span class="sxs-lookup"><span data-stu-id="43de5-118">If a variable can contain an indefinite number of characters, declare it as `String`.</span></span> <span data-ttu-id="43de5-119">例如：</span><span class="sxs-lookup"><span data-stu-id="43de5-119">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#2)]
  
 <span data-ttu-id="43de5-120">有关详细信息，请参阅 [String 数据类型](../../../language-reference/data-types/string-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="43de5-120">For more information, see [String Data Type](../../../language-reference/data-types/string-data-type.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43de5-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="43de5-121">See also</span></span>

- [<span data-ttu-id="43de5-122">基本数据类型</span><span class="sxs-lookup"><span data-stu-id="43de5-122">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="43de5-123">复合数据类型</span><span class="sxs-lookup"><span data-stu-id="43de5-123">Composite Data Types</span></span>](composite-data-types.md)
- [<span data-ttu-id="43de5-124">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="43de5-124">Generic Types in Visual Basic</span></span>](generic-types.md)
- [<span data-ttu-id="43de5-125">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="43de5-125">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="43de5-126">Visual Basic 中的类型转换</span><span class="sxs-lookup"><span data-stu-id="43de5-126">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="43de5-127">数据类型疑难解答</span><span class="sxs-lookup"><span data-stu-id="43de5-127">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="43de5-128">类型字符</span><span class="sxs-lookup"><span data-stu-id="43de5-128">Type Characters</span></span>](type-characters.md)
