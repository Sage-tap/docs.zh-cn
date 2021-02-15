---
description: 了解详细信息： Visual Basic 中的数据类型
title: 数据类型
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], declaring
- typing
- data types [Visual Basic]
- Visual Basic code, data types
- data types [Visual Basic], improving speed with
ms.assetid: 5e1b9aaf-c7ca-4b29-9b22-0e82ed8e85e2
ms.openlocfilehash: f431b501b40d2fafd4422b1f3fa1ea3a2ebf56fb
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100483932"
---
# <a name="data-types-in-visual-basic"></a><span data-ttu-id="a4ec4-103">Visual Basic 中的数据类型</span><span class="sxs-lookup"><span data-stu-id="a4ec4-103">Data Types in Visual Basic</span></span>

<span data-ttu-id="a4ec4-104">编程元素的 *数据类型* 是指可以保留的数据种类以及相应类型数据的存储方式。</span><span class="sxs-lookup"><span data-stu-id="a4ec4-104">The *data type* of a programming element refers to what kind of data it can hold and how it stores that data.</span></span> <span data-ttu-id="a4ec4-105">数据类型适用于所有可以存储到计算机内存中或参与表达式求值的值。</span><span class="sxs-lookup"><span data-stu-id="a4ec4-105">Data types apply to all values that can be stored in computer memory or participate in the evaluation of an expression.</span></span> <span data-ttu-id="a4ec4-106">每个变量、文本、常量、枚举、属性、过程参数、过程自变量和过程返回值都有对应的数据类型。</span><span class="sxs-lookup"><span data-stu-id="a4ec4-106">Every variable, literal, constant, enumeration, property, procedure parameter, procedure argument, and procedure return value has a data type.</span></span>  
  
## <a name="declared-data-types"></a><span data-ttu-id="a4ec4-107">已声明的数据类型</span><span class="sxs-lookup"><span data-stu-id="a4ec4-107">Declared Data Types</span></span>  

 <span data-ttu-id="a4ec4-108">可以使用声明语句定义编程元素，并使用 `As` 子句指定其数据类型。</span><span class="sxs-lookup"><span data-stu-id="a4ec4-108">You define a programming element with a declaration statement, and you specify its data type with the `As` clause.</span></span> <span data-ttu-id="a4ec4-109">下表列出了用于声明各种元素的语句。</span><span class="sxs-lookup"><span data-stu-id="a4ec4-109">The following table shows the statements you use to declare various elements.</span></span>  
  
|<span data-ttu-id="a4ec4-110">编程元素</span><span class="sxs-lookup"><span data-stu-id="a4ec4-110">Programming element</span></span>|<span data-ttu-id="a4ec4-111">数据类型声明</span><span class="sxs-lookup"><span data-stu-id="a4ec4-111">Data type declaration</span></span>|  
|-------------------------|---------------------------|  
|<span data-ttu-id="a4ec4-112">变量</span><span class="sxs-lookup"><span data-stu-id="a4ec4-112">Variable</span></span>|<span data-ttu-id="a4ec4-113">使用 [Dim 语句](../../../language-reference/statements/dim-statement.md)</span><span class="sxs-lookup"><span data-stu-id="a4ec4-113">In a [Dim Statement](../../../language-reference/statements/dim-statement.md)</span></span><br /><br /> <span data-ttu-id="a4ec4-114">`Dim`   `amount As Double`</span><span class="sxs-lookup"><span data-stu-id="a4ec4-114">`Dim`   `amount As Double`</span></span><br /><br /> <span data-ttu-id="a4ec4-115">`Static`   `yourName As String`</span><span class="sxs-lookup"><span data-stu-id="a4ec4-115">`Static`   `yourName As String`</span></span><br /><br /> <span data-ttu-id="a4ec4-116">`Public`   `billsPaid As Decimal = 0`</span><span class="sxs-lookup"><span data-stu-id="a4ec4-116">`Public`   `billsPaid As Decimal = 0`</span></span>|  
|<span data-ttu-id="a4ec4-117">文本</span><span class="sxs-lookup"><span data-stu-id="a4ec4-117">Literal</span></span>|<span data-ttu-id="a4ec4-118">含文本类型字符；请参阅[类型字符](type-characters.md)中的“文本类型字符”</span><span class="sxs-lookup"><span data-stu-id="a4ec4-118">With a literal type character; see "Literal Type Characters" in [Type Characters](type-characters.md)</span></span><br /><br /> <span data-ttu-id="a4ec4-119">`Dim searchChar As Char = "."`  `C`</span><span class="sxs-lookup"><span data-stu-id="a4ec4-119">`Dim searchChar As Char = "."`  `C`</span></span>|  
|<span data-ttu-id="a4ec4-120">返回的常量</span><span class="sxs-lookup"><span data-stu-id="a4ec4-120">Constant</span></span>|<span data-ttu-id="a4ec4-121">使用 [Const 语句](../../../language-reference/statements/const-statement.md)</span><span class="sxs-lookup"><span data-stu-id="a4ec4-121">In a [Const Statement](../../../language-reference/statements/const-statement.md)</span></span><br /><br /> <span data-ttu-id="a4ec4-122">`Const`   `modulus As Single = 4.17825F`</span><span class="sxs-lookup"><span data-stu-id="a4ec4-122">`Const`   `modulus As Single = 4.17825F`</span></span>|  
|<span data-ttu-id="a4ec4-123">枚举</span><span class="sxs-lookup"><span data-stu-id="a4ec4-123">Enumeration</span></span>|<span data-ttu-id="a4ec4-124">使用 [Enum 语句](../../../language-reference/statements/enum-statement.md)</span><span class="sxs-lookup"><span data-stu-id="a4ec4-124">In an [Enum Statement](../../../language-reference/statements/enum-statement.md)</span></span><br /><br /> <span data-ttu-id="a4ec4-125">`Public`   `Enum`   `colors`</span><span class="sxs-lookup"><span data-stu-id="a4ec4-125">`Public`   `Enum`   `colors`</span></span>|  
|<span data-ttu-id="a4ec4-126">properties</span><span class="sxs-lookup"><span data-stu-id="a4ec4-126">Property</span></span>|<span data-ttu-id="a4ec4-127">使用 [Property 语句](../../../language-reference/statements/property-statement.md)</span><span class="sxs-lookup"><span data-stu-id="a4ec4-127">In a [Property Statement](../../../language-reference/statements/property-statement.md)</span></span><br /><br /> <span data-ttu-id="a4ec4-128">`Property`   `region() As String`</span><span class="sxs-lookup"><span data-stu-id="a4ec4-128">`Property`   `region() As String`</span></span>|  
|<span data-ttu-id="a4ec4-129">过程参数</span><span class="sxs-lookup"><span data-stu-id="a4ec4-129">Procedure parameter</span></span>|<span data-ttu-id="a4ec4-130">使用 [Sub 语句](../../../language-reference/statements/sub-statement.md)、[Function 语句](../../../language-reference/statements/function-statement.md)或 [Operator 语句](../../../language-reference/statements/operator-statement.md)</span><span class="sxs-lookup"><span data-stu-id="a4ec4-130">In a [Sub Statement](../../../language-reference/statements/sub-statement.md), [Function Statement](../../../language-reference/statements/function-statement.md), or [Operator Statement](../../../language-reference/statements/operator-statement.md)</span></span><br /><br /> <span data-ttu-id="a4ec4-131">`Sub addSale(ByVal`   `amount`   `As Double)`</span><span class="sxs-lookup"><span data-stu-id="a4ec4-131">`Sub addSale(ByVal`   `amount`   `As Double)`</span></span>|  
|<span data-ttu-id="a4ec4-132">过程自变量</span><span class="sxs-lookup"><span data-stu-id="a4ec4-132">Procedure argument</span></span>|<span data-ttu-id="a4ec4-133">在调用的代码中；每个自变量都是一个已声明的编程元素或包含已声明元素的表达式</span><span class="sxs-lookup"><span data-stu-id="a4ec4-133">In the calling code; each argument is a programming element that has already been declared, or an expression containing declared elements</span></span><br /><br /> <span data-ttu-id="a4ec4-134">`subString = Left(`  `inputString`  `,`   `5`  `)`</span><span class="sxs-lookup"><span data-stu-id="a4ec4-134">`subString = Left(`  `inputString`  `,`   `5`  `)`</span></span>|  
|<span data-ttu-id="a4ec4-135">过程返回值</span><span class="sxs-lookup"><span data-stu-id="a4ec4-135">Procedure return value</span></span>|<span data-ttu-id="a4ec4-136">使用 [Function 语句](../../../language-reference/statements/function-statement.md)或 [Operator 语句](../../../language-reference/statements/operator-statement.md)</span><span class="sxs-lookup"><span data-stu-id="a4ec4-136">In a [Function Statement](../../../language-reference/statements/function-statement.md) or [Operator Statement](../../../language-reference/statements/operator-statement.md)</span></span><br /><br /> <span data-ttu-id="a4ec4-137">`Function convert(ByVal b As Byte)`   `As String`</span><span class="sxs-lookup"><span data-stu-id="a4ec4-137">`Function convert(ByVal b As Byte)`   `As String`</span></span>|  
  
 <span data-ttu-id="a4ec4-138">有关 Visual Basic 数据类型的列表，请参阅[数据类型](../../../language-reference/data-types/index.md)。</span><span class="sxs-lookup"><span data-stu-id="a4ec4-138">For a list of Visual Basic data types, see [Data Types](../../../language-reference/data-types/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4ec4-139">请参阅</span><span class="sxs-lookup"><span data-stu-id="a4ec4-139">See also</span></span>

- [<span data-ttu-id="a4ec4-140">类型字符</span><span class="sxs-lookup"><span data-stu-id="a4ec4-140">Type Characters</span></span>](type-characters.md)
- [<span data-ttu-id="a4ec4-141">基本数据类型</span><span class="sxs-lookup"><span data-stu-id="a4ec4-141">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="a4ec4-142">复合数据类型</span><span class="sxs-lookup"><span data-stu-id="a4ec4-142">Composite Data Types</span></span>](composite-data-types.md)
- [<span data-ttu-id="a4ec4-143">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a4ec4-143">Generic Types in Visual Basic</span></span>](generic-types.md)
- [<span data-ttu-id="a4ec4-144">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="a4ec4-144">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="a4ec4-145">Visual Basic 中的类型转换</span><span class="sxs-lookup"><span data-stu-id="a4ec4-145">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="a4ec4-146">结构</span><span class="sxs-lookup"><span data-stu-id="a4ec4-146">Structures</span></span>](structures.md)
- [<span data-ttu-id="a4ec4-147">元组</span><span class="sxs-lookup"><span data-stu-id="a4ec4-147">Tuples</span></span>](tuples.md)
- [<span data-ttu-id="a4ec4-148">数据类型疑难解答</span><span class="sxs-lookup"><span data-stu-id="a4ec4-148">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="a4ec4-149">数据类型</span><span class="sxs-lookup"><span data-stu-id="a4ec4-149">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="a4ec4-150">有效使用数据类型</span><span class="sxs-lookup"><span data-stu-id="a4ec4-150">Efficient Use of Data Types</span></span>](efficient-use-of-data-types.md)
