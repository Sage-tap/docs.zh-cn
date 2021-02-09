---
description: 详细了解：文件编码 (Visual Basic)
title: 文件编码
ms.date: 07/20/2015
helpviewer_keywords:
- character encodings
- files [Visual Basic], encoding
- Unicode, file encoding
- file encoding
ms.assetid: ea2c5f5f-bbb1-4150-9928-b9951fa6bc57
ms.openlocfilehash: f573b5d8f83c27cbf4ddacb9fd40474d7d1be1ae
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675359"
---
# <a name="file-encodings-visual-basic"></a><span data-ttu-id="45a3c-103">文件编码 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45a3c-103">File Encodings (Visual Basic)</span></span>

<span data-ttu-id="45a3c-104">文件编码也称为字符编码，用于指定在处理文本时如何表示字符。</span><span class="sxs-lookup"><span data-stu-id="45a3c-104">File encodings, also known as character encodings, specify how to represent characters when text processing.</span></span> <span data-ttu-id="45a3c-105">虽然 Unicode 是最常用的编码，但根据编码能否处理某种语言字符，另一种编码可能更优。</span><span class="sxs-lookup"><span data-stu-id="45a3c-105">One encoding may be preferable over another in terms of which language characters it can or cannot handle, although Unicode is usually preferred.</span></span>

<span data-ttu-id="45a3c-106">读取或写入文件时，未正确匹配文件编码可能会导致发生异常或产生不正确的结果。</span><span class="sxs-lookup"><span data-stu-id="45a3c-106">When reading from or writing to files, improperly matching file encodings may result in exceptions or incorrect results.</span></span>

## <a name="types-of-encodings"></a><span data-ttu-id="45a3c-107">编码类型</span><span class="sxs-lookup"><span data-stu-id="45a3c-107">Types of Encodings</span></span>

<span data-ttu-id="45a3c-108">处理文件时，Unicode 是首选编码。</span><span class="sxs-lookup"><span data-stu-id="45a3c-108">Unicode is the preferred encoding when working with files.</span></span> <span data-ttu-id="45a3c-109">Unicode 是全球范围的字符编码标准，使用 16 位代码值来表示现代计算中使用的所有字符，包括印刷中使用的技术符号和特殊字符。</span><span class="sxs-lookup"><span data-stu-id="45a3c-109">Unicode is a worldwide character-encoding standard that uses 16-bit code values to represent all the characters used in modern computing, including technical symbols and special characters used in publishing.</span></span>

<span data-ttu-id="45a3c-110">以前的字符编码标准包括传统的字符集，如 Windows ANSI 字符集，该字符集使用 8 位代码值或 8 位值组合来表示特定语言或地理区域中使用的字符。</span><span class="sxs-lookup"><span data-stu-id="45a3c-110">Previous character-encoding standards consisted of traditional character sets, such as the Windows ANSI character set that uses 8-bit code values, or combinations of 8-bit values, to represent the characters used in a specific language or geographical region.</span></span>

## <a name="encoding-class"></a><span data-ttu-id="45a3c-111">编码类</span><span class="sxs-lookup"><span data-stu-id="45a3c-111">Encoding Class</span></span>

<span data-ttu-id="45a3c-112"><xref:System.Text.Encoding> 类表示字符编码。</span><span class="sxs-lookup"><span data-stu-id="45a3c-112">The <xref:System.Text.Encoding> class represents a character encoding.</span></span> <span data-ttu-id="45a3c-113">下表列出并描述了每个可用的编码类型。</span><span class="sxs-lookup"><span data-stu-id="45a3c-113">This table lists the type of encodings available and describes each.</span></span>

|<span data-ttu-id="45a3c-114">“属性”</span><span class="sxs-lookup"><span data-stu-id="45a3c-114">Name</span></span>|<span data-ttu-id="45a3c-115">说明</span><span class="sxs-lookup"><span data-stu-id="45a3c-115">Description</span></span>|
|---|---|
|<xref:System.Text.ASCIIEncoding>|<span data-ttu-id="45a3c-116">表示 Unicode 字符的 ASCII 字符编码。</span><span class="sxs-lookup"><span data-stu-id="45a3c-116">Represents an ASCII character encoding of Unicode characters.</span></span>|
|<xref:System.Text.UnicodeEncoding>|<span data-ttu-id="45a3c-117">表示 Unicode 字符的 UTF-16 编码。</span><span class="sxs-lookup"><span data-stu-id="45a3c-117">Represents a UTF-16 encoding of Unicode characters.</span></span>|
|<xref:System.Text.UTF32Encoding>|<span data-ttu-id="45a3c-118">表示 Unicode 字符的 UTF-32 编码。</span><span class="sxs-lookup"><span data-stu-id="45a3c-118">Represents a UTF-32 encoding of Unicode characters.</span></span>|
|<xref:System.Text.UTF7Encoding>|<span data-ttu-id="45a3c-119">表示 Unicode 字符的 UTF-7 编码。</span><span class="sxs-lookup"><span data-stu-id="45a3c-119">Represents a UTF-7 encoding of Unicode characters.</span></span>|
|<xref:System.Text.UTF8Encoding>|<span data-ttu-id="45a3c-120">表示 Unicode 字符的 UTF-8 编码。</span><span class="sxs-lookup"><span data-stu-id="45a3c-120">Represents a UTF-8 encoding of Unicode characters.</span></span>|

## <a name="see-also"></a><span data-ttu-id="45a3c-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="45a3c-121">See also</span></span>

- [<span data-ttu-id="45a3c-122">从文件读取</span><span class="sxs-lookup"><span data-stu-id="45a3c-122">Reading from Files</span></span>](reading-from-files.md)
- [<span data-ttu-id="45a3c-123">写入文件</span><span class="sxs-lookup"><span data-stu-id="45a3c-123">Writing to Files</span></span>](writing-to-files.md)
