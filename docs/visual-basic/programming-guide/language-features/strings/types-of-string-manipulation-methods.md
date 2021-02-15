---
description: 了解详细信息： Visual Basic 中的字符串操作方法的类型
title: 字符串操作方法的类型
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
ms.openlocfilehash: 02b127d5cd023a8bd73a3042a8bcec340ce63ed8
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100429749"
---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a><span data-ttu-id="44657-103">字符串操作方法的类型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="44657-103">Types of String Manipulation Methods in Visual Basic</span></span>

<span data-ttu-id="44657-104">可以通过多种不同的方法来分析和操作字符串。</span><span class="sxs-lookup"><span data-stu-id="44657-104">There are several different ways to analyze and manipulate your strings.</span></span> <span data-ttu-id="44657-105">某些方法是 Visual Basic 语言的一部分，其他方法是类中的固有方法 `String` 。</span><span class="sxs-lookup"><span data-stu-id="44657-105">Some of the methods are a part of the Visual Basic language, and others are inherent in the `String` class.</span></span>  
  
## <a name="visual-basic-language-and-the-net-framework"></a><span data-ttu-id="44657-106">Visual Basic 语言和 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="44657-106">Visual Basic Language and the .NET Framework</span></span>  

 <span data-ttu-id="44657-107">Visual Basic 方法用作语言的固有功能。</span><span class="sxs-lookup"><span data-stu-id="44657-107">Visual Basic methods are used as inherent functions of the language.</span></span> <span data-ttu-id="44657-108">在代码中，可以使用它们而无需进行限定。</span><span class="sxs-lookup"><span data-stu-id="44657-108">They may be used without qualification in your code.</span></span> <span data-ttu-id="44657-109">下面的示例演示了 Visual Basic 字符串操作命令的典型用法：</span><span class="sxs-lookup"><span data-stu-id="44657-109">The following example shows typical use of a Visual Basic string-manipulation command:</span></span>  
  
 [!code-vb[VbVbalrStrings#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#44)]  
  
 <span data-ttu-id="44657-110">在此示例中， `Mid` 函数对执行直接操作 `aString` ，并将值分配给 `bString` 。</span><span class="sxs-lookup"><span data-stu-id="44657-110">In this example, the `Mid` function performs a direct operation on `aString` and assigns the value to `bString`.</span></span>  
  
 <span data-ttu-id="44657-111">有关 Visual Basic 字符串操作方法的列表，请参阅 [字符串操作摘要](../../../language-reference/keywords/string-manipulation-summary.md)。</span><span class="sxs-lookup"><span data-stu-id="44657-111">For a list of Visual Basic string manipulation methods, see [String Manipulation Summary](../../../language-reference/keywords/string-manipulation-summary.md).</span></span>  
  
### <a name="shared-methods-and-instance-methods"></a><span data-ttu-id="44657-112">共享方法和实例方法</span><span class="sxs-lookup"><span data-stu-id="44657-112">Shared Methods and Instance Methods</span></span>  

 <span data-ttu-id="44657-113">还可以通过类的方法操作字符串 `String` 。</span><span class="sxs-lookup"><span data-stu-id="44657-113">You can also manipulate strings with the methods of the `String` class.</span></span> <span data-ttu-id="44657-114">中有两种类型的方法 `String` ： *共享* 方法和 *实例* 方法。</span><span class="sxs-lookup"><span data-stu-id="44657-114">There are two types of methods in `String`: *shared* methods and *instance* methods.</span></span>  
  
#### <a name="shared-methods"></a><span data-ttu-id="44657-115">共享方法</span><span class="sxs-lookup"><span data-stu-id="44657-115">Shared Methods</span></span>  

 <span data-ttu-id="44657-116">共享方法是源自 `String` 类本身，不需要该类的实例即可工作的方法。</span><span class="sxs-lookup"><span data-stu-id="44657-116">A shared method is a method that stems from the `String` class itself and does not require an instance of that class to work.</span></span> <span data-ttu-id="44657-117">可以使用类的名称限定这些方法 (`String`) ，而不是使用类的实例 `String` 。</span><span class="sxs-lookup"><span data-stu-id="44657-117">These methods can be qualified with the name of the class (`String`) rather than with an instance of the `String` class.</span></span> <span data-ttu-id="44657-118">例如：</span><span class="sxs-lookup"><span data-stu-id="44657-118">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#45)]  
  
 <span data-ttu-id="44657-119">在前面的示例中， <xref:System.String.Copy%2A?displayProperty=nameWithType> 方法是一个静态方法，它在给定的表达式上操作，并将生成的值分配给 `bString` 。</span><span class="sxs-lookup"><span data-stu-id="44657-119">In the preceding example, the <xref:System.String.Copy%2A?displayProperty=nameWithType> method is a static method, which acts upon an expression it is given and assigns the resulting value to `bString`.</span></span>  
  
#### <a name="instance-methods"></a><span data-ttu-id="44657-120">实例方法</span><span class="sxs-lookup"><span data-stu-id="44657-120">Instance Methods</span></span>  

 <span data-ttu-id="44657-121">相反，实例方法是特定实例的主干， `String` 必须使用实例名称进行限定。</span><span class="sxs-lookup"><span data-stu-id="44657-121">Instance methods, by contrast, stem from a particular instance of `String` and must be qualified with the instance name.</span></span> <span data-ttu-id="44657-122">例如：</span><span class="sxs-lookup"><span data-stu-id="44657-122">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#46)]  
  
 <span data-ttu-id="44657-123">在此示例中， <xref:System.String.Substring%2A?displayProperty=nameWithType> 方法是 (实例的方法 `String` ， `aString`) 。</span><span class="sxs-lookup"><span data-stu-id="44657-123">In this example, the <xref:System.String.Substring%2A?displayProperty=nameWithType> method is a method of the instance of `String` (that is, `aString`).</span></span> <span data-ttu-id="44657-124">它在上执行操作 `aString` ，并将该值分配给 `bString` 。</span><span class="sxs-lookup"><span data-stu-id="44657-124">It performs an operation on `aString` and assigns that value to `bString`.</span></span>  
  
 <span data-ttu-id="44657-125">有关详细信息，请参阅类的文档 <xref:System.String> 。</span><span class="sxs-lookup"><span data-stu-id="44657-125">For more information, see the documentation for the <xref:System.String> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44657-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="44657-126">See also</span></span>

- [<span data-ttu-id="44657-127">字符串介绍 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="44657-127">Introduction to Strings in Visual Basic</span></span>](introduction-to-strings.md)
