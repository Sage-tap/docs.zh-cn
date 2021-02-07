---
description: '了解详细信息： Boolean 数据类型 (Visual Basic) '
title: 布尔数据类型
ms.date: 07/20/2015
f1_keywords:
- vb.FALSE
- vb.TRUE
- vb.Boolean
helpviewer_keywords:
- Boolean data type
- Boolean values [Visual Basic], False keyword
- False keyword [Visual Basic]
- True keyword [Visual Basic]
- Boolean values [Visual Basic], True keyword
ms.assetid: 4858e630-4813-4216-a55e-f4d0feb884e4
ms.openlocfilehash: cdda6bc0571eb0a2a9ee6a079ffd276bfc89a9b4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99731404"
---
# <a name="boolean-data-type-visual-basic"></a><span data-ttu-id="15d21-103">Boolean 数据类型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="15d21-103">Boolean Data Type (Visual Basic)</span></span>

<span data-ttu-id="15d21-104">保存的值只能是 `True` 或 `False` 。</span><span class="sxs-lookup"><span data-stu-id="15d21-104">Holds values that can be only `True` or `False`.</span></span> <span data-ttu-id="15d21-105">关键字 `True` 和 `False` 对应于变量的两个状态 `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="15d21-105">The keywords `True` and `False` correspond to the two states of `Boolean` variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15d21-106">备注</span><span class="sxs-lookup"><span data-stu-id="15d21-106">Remarks</span></span>  

 <span data-ttu-id="15d21-107">使用 [布尔数据类型 (Visual Basic) ](boolean-data-type.md) 包含两状态值值，如 true/false、yes/no 或 on/off。</span><span class="sxs-lookup"><span data-stu-id="15d21-107">Use the [Boolean Data Type (Visual Basic)](boolean-data-type.md) to contain two-state values such as true/false, yes/no, or on/off.</span></span>  
  
 <span data-ttu-id="15d21-108">`Boolean` 的默认值为 `False`。</span><span class="sxs-lookup"><span data-stu-id="15d21-108">The default value of `Boolean` is `False`.</span></span>  
  
 <span data-ttu-id="15d21-109">`Boolean` 值不会存储为数字，并且存储的值不应与数字等效。</span><span class="sxs-lookup"><span data-stu-id="15d21-109">`Boolean` values are not stored as numbers, and the stored values are not intended to be equivalent to numbers.</span></span> <span data-ttu-id="15d21-110">永远不应编写依赖于和的等效数值的代码 `True` `False` 。</span><span class="sxs-lookup"><span data-stu-id="15d21-110">You should never write code that relies on equivalent numeric values for `True` and `False`.</span></span> <span data-ttu-id="15d21-111">应尽可能将变量的使用限制 `Boolean` 为它们的设计逻辑值。</span><span class="sxs-lookup"><span data-stu-id="15d21-111">Whenever possible, you should restrict usage of `Boolean` variables to the logical values for which they are designed.</span></span>  
  
## <a name="type-conversions"></a><span data-ttu-id="15d21-112">类型转换</span><span class="sxs-lookup"><span data-stu-id="15d21-112">Type Conversions</span></span>  

 <span data-ttu-id="15d21-113">当 Visual Basic 将数值数据类型值转换为时 `Boolean` ，0变为， `False` 所有其他值将变为 `True` 。</span><span class="sxs-lookup"><span data-stu-id="15d21-113">When Visual Basic converts numeric data type values to `Boolean`, 0 becomes `False` and all other values become `True`.</span></span> <span data-ttu-id="15d21-114">当 Visual Basic 将 `Boolean` 值转换为数值类型时，将 `False` 变为0并 `True` 变为-1。</span><span class="sxs-lookup"><span data-stu-id="15d21-114">When Visual Basic converts `Boolean` values to numeric types, `False` becomes 0 and `True` becomes -1.</span></span>  
  
 <span data-ttu-id="15d21-115">当在 `Boolean` 值和数值数据类型之间进行转换时，请记住，.NET Framework 转换方法并不总是产生与 Visual Basic 转换关键字相同的结果。</span><span class="sxs-lookup"><span data-stu-id="15d21-115">When you convert between `Boolean` values and numeric data types, keep in mind that the .NET Framework conversion methods do not always produce the same results as the Visual Basic conversion keywords.</span></span> <span data-ttu-id="15d21-116">这是因为 Visual Basic 转换会保持与以前版本兼容的行为。</span><span class="sxs-lookup"><span data-stu-id="15d21-116">This is because the Visual Basic conversion retains behavior compatible with previous versions.</span></span> <span data-ttu-id="15d21-117">有关详细信息，请参阅 [故障排除数据类型](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)中的 "布尔类型不会精确转换为数值类型"。</span><span class="sxs-lookup"><span data-stu-id="15d21-117">For more information, see "Boolean Type Does Not Convert to Numeric Type Accurately" in [Troubleshooting Data Types](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="15d21-118">编程提示</span><span class="sxs-lookup"><span data-stu-id="15d21-118">Programming Tips</span></span>  
  
- <span data-ttu-id="15d21-119">**负数。**</span><span class="sxs-lookup"><span data-stu-id="15d21-119">**Negative Numbers.**</span></span> <span data-ttu-id="15d21-120">`Boolean` 不是数值类型，不能表示负值。</span><span class="sxs-lookup"><span data-stu-id="15d21-120">`Boolean` is not a numeric type and cannot represent a negative value.</span></span> <span data-ttu-id="15d21-121">在任何情况下，不应使用 `Boolean` 来保存数值。</span><span class="sxs-lookup"><span data-stu-id="15d21-121">In any case, you should not use `Boolean` to hold numeric values.</span></span>  
  
- <span data-ttu-id="15d21-122">**键入字符。**</span><span class="sxs-lookup"><span data-stu-id="15d21-122">**Type Characters.**</span></span> <span data-ttu-id="15d21-123">`Boolean` 没有文本类型字符或标识符类型字符。</span><span class="sxs-lookup"><span data-stu-id="15d21-123">`Boolean` has no literal type character or identifier type character.</span></span>  
  
- <span data-ttu-id="15d21-124">**Framework 类型。**</span><span class="sxs-lookup"><span data-stu-id="15d21-124">**Framework Type.**</span></span> <span data-ttu-id="15d21-125">.NET Framework 中的对应类型是 <xref:System.Boolean?displayProperty=nameWithType> 结构。</span><span class="sxs-lookup"><span data-stu-id="15d21-125">The corresponding type in the .NET Framework is the <xref:System.Boolean?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15d21-126">示例</span><span class="sxs-lookup"><span data-stu-id="15d21-126">Example</span></span>  

 <span data-ttu-id="15d21-127">在下面的示例中， `runningVB` 是一个 `Boolean` 变量，用于存储简单的 yes/no 设置。</span><span class="sxs-lookup"><span data-stu-id="15d21-127">In the following example, `runningVB` is a `Boolean` variable, which stores a simple yes/no setting.</span></span>  
  
```vb  
Dim runningVB As Boolean  
' Check to see if program is running on Visual Basic engine.  
If scriptEngine = "VB" Then  
    runningVB = True  
End If  
```  
  
## <a name="see-also"></a><span data-ttu-id="15d21-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="15d21-128">See also</span></span>

- <xref:System.Boolean?displayProperty=nameWithType>
- [<span data-ttu-id="15d21-129">数据类型</span><span class="sxs-lookup"><span data-stu-id="15d21-129">Data Types</span></span>](index.md)
- [<span data-ttu-id="15d21-130">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="15d21-130">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="15d21-131">转换摘要</span><span class="sxs-lookup"><span data-stu-id="15d21-131">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="15d21-132">有效使用数据类型</span><span class="sxs-lookup"><span data-stu-id="15d21-132">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="15d21-133">数据类型疑难解答</span><span class="sxs-lookup"><span data-stu-id="15d21-133">Troubleshooting Data Types</span></span>](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="15d21-134">CType Function</span><span class="sxs-lookup"><span data-stu-id="15d21-134">CType Function</span></span>](../functions/ctype-function.md)
