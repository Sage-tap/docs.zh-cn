---
description: '了解详细信息：排查数组 (Visual Basic) '
title: 数组疑难解答
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting arrays
- arrays [Visual Basic], initialization errors
- troubleshooting Visual Basic, arrays
- arrays [Visual Basic], compilation errors
- arrays [Visual Basic], declaration errors
- arrays [Visual Basic], troubleshooting
ms.assetid: f4e971c7-c0a4-4ed7-a77a-8d71039f266f
ms.openlocfilehash: 2aca3c1819ed6482e132ba432e5e70fbdf9a5b3a
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100454490"
---
# <a name="troubleshooting-arrays-visual-basic"></a><span data-ttu-id="26f2f-103">数组疑难解答 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="26f2f-103">Troubleshooting Arrays (Visual Basic)</span></span>

<span data-ttu-id="26f2f-104">此页列出了在使用数组时可能出现的一些常见问题。</span><span class="sxs-lookup"><span data-stu-id="26f2f-104">This page lists some common problems that can occur when working with arrays.</span></span>  
  
## <a name="compilation-errors-declaring-and-initializing-an-array"></a><span data-ttu-id="26f2f-105">声明和初始化数组的编译错误</span><span class="sxs-lookup"><span data-stu-id="26f2f-105">Compilation Errors Declaring and Initializing an Array</span></span>  

 <span data-ttu-id="26f2f-106">声明、创建和初始化数组的规则误解可能会引发编译错误。</span><span class="sxs-lookup"><span data-stu-id="26f2f-106">Compilation errors can arise from misunderstanding of the rules for declaring, creating, and initializing arrays.</span></span> <span data-ttu-id="26f2f-107">错误的最常见原因如下：</span><span class="sxs-lookup"><span data-stu-id="26f2f-107">The most common causes of errors are the following:</span></span>  
  
- <span data-ttu-id="26f2f-108">在数组变量声明中指定维度长度后，提供一个 [新的运算符](../../../language-reference/operators/new-operator.md) 子句。</span><span class="sxs-lookup"><span data-stu-id="26f2f-108">Supplying a [New Operator](../../../language-reference/operators/new-operator.md) clause after specifying dimension lengths in the array variable declaration.</span></span> <span data-ttu-id="26f2f-109">下面的代码行显示了此类型的无效声明。</span><span class="sxs-lookup"><span data-stu-id="26f2f-109">The following code lines show invalid declarations of this type.</span></span>  
  
     `Dim INVALIDsingleDimByteArray(2) As Byte = New Byte()`  
  
     `Dim INVALIDtwoDimShortArray(1, 1) As Short = New Short(,)`  
  
     `Dim INVALIDjaggedByteArray(1)() As Byte = New Byte()()`  
  
- <span data-ttu-id="26f2f-110">指定超出交错数组顶级数组的维度长度。</span><span class="sxs-lookup"><span data-stu-id="26f2f-110">Specifying dimension lengths for more than the top-level array of a jagged array.</span></span> <span data-ttu-id="26f2f-111">下面的代码行显示了此类型的无效声明。</span><span class="sxs-lookup"><span data-stu-id="26f2f-111">The following code line shows an invalid declaration of this type.</span></span>  
  
     `Dim INVALIDjaggedByteArray(1)(1) As Byte`  
  
- <span data-ttu-id="26f2f-112">`New`指定元素值时省略关键字。</span><span class="sxs-lookup"><span data-stu-id="26f2f-112">Omitting the `New` keyword when specifying the element values.</span></span> <span data-ttu-id="26f2f-113">下面的代码行显示了此类型的无效声明。</span><span class="sxs-lookup"><span data-stu-id="26f2f-113">The following code line shows an invalid declaration of this type.</span></span>  
  
     `Dim INVALIDoneDimShortArray() As Short = Short() {0, 1, 2, 3}`  
  
- <span data-ttu-id="26f2f-114">) 提供 `New` 不带大括号的子句 (`{}` 。</span><span class="sxs-lookup"><span data-stu-id="26f2f-114">Supplying a `New` clause without braces (`{}`).</span></span> <span data-ttu-id="26f2f-115">下面的代码行显示了此类型的无效声明。</span><span class="sxs-lookup"><span data-stu-id="26f2f-115">The following code lines show invalid declarations of this type.</span></span>  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte()`  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte(2)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(,)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(1, 1)`  
  
## <a name="accessing-an-array-out-of-bounds"></a><span data-ttu-id="26f2f-116">访问超出界限的数组</span><span class="sxs-lookup"><span data-stu-id="26f2f-116">Accessing an Array Out of Bounds</span></span>  

 <span data-ttu-id="26f2f-117">初始化数组的过程为每个维度分配上限和下限。</span><span class="sxs-lookup"><span data-stu-id="26f2f-117">The process of initializing an array assigns an upper bound and a lower bound to each dimension.</span></span> <span data-ttu-id="26f2f-118">每次访问数组的元素时，必须为每个维度指定有效的索引或下标。</span><span class="sxs-lookup"><span data-stu-id="26f2f-118">Every access to an element of the array must specify a valid index, or subscript, for every dimension.</span></span> <span data-ttu-id="26f2f-119">如果任何索引低于其下限或高于其上限，则会引发 <xref:System.IndexOutOfRangeException> 异常。</span><span class="sxs-lookup"><span data-stu-id="26f2f-119">If any index is below its lower bound or above its upper bound, an <xref:System.IndexOutOfRangeException> exception results.</span></span> <span data-ttu-id="26f2f-120">编译器无法检测到此类错误，因此在运行时出现错误。</span><span class="sxs-lookup"><span data-stu-id="26f2f-120">The compiler cannot detect such an error, so an error occurs at run time.</span></span>  
  
### <a name="determining-bounds"></a><span data-ttu-id="26f2f-121">确定边界</span><span class="sxs-lookup"><span data-stu-id="26f2f-121">Determining Bounds</span></span>  

 <span data-ttu-id="26f2f-122">如果另一个组件将数组传递给您的代码（例如，作为过程参数），则您不知道该数组的大小或其维度的长度。</span><span class="sxs-lookup"><span data-stu-id="26f2f-122">If another component passes an array to your code, for example as a procedure argument, you do not know the size of that array or the lengths of its dimensions.</span></span> <span data-ttu-id="26f2f-123">在尝试访问任何元素之前，应始终确定数组的每个维度的上限。</span><span class="sxs-lookup"><span data-stu-id="26f2f-123">You should always determine the upper bound for every dimension of an array before you attempt to access any elements.</span></span> <span data-ttu-id="26f2f-124">如果数组是通过 Visual Basic 子句之外的其他方法创建的 `New` ，则下限可能不是0，并且最安全的做法是确定下限。</span><span class="sxs-lookup"><span data-stu-id="26f2f-124">If the array has been created by some means other than a Visual Basic `New` clause, the lower bound might be something other than 0, and it is safest to determine that lower bound as well.</span></span>  
  
### <a name="specifying-the-dimension"></a><span data-ttu-id="26f2f-125">指定维度</span><span class="sxs-lookup"><span data-stu-id="26f2f-125">Specifying the Dimension</span></span>  

 <span data-ttu-id="26f2f-126">确定多维数组的边界时，请注意如何指定维度。</span><span class="sxs-lookup"><span data-stu-id="26f2f-126">When determining the bounds of a multidimensional array, take care how you specify the dimension.</span></span> <span data-ttu-id="26f2f-127">`dimension`和方法的参数 <xref:System.Array.GetLowerBound%2A> <xref:System.Array.GetUpperBound%2A> 是从0开始的，而 `Rank` Visual Basic <xref:Microsoft.VisualBasic.Information.LBound%2A> 和函数的参数 <xref:Microsoft.VisualBasic.Information.UBound%2A> 是从1开始的。</span><span class="sxs-lookup"><span data-stu-id="26f2f-127">The `dimension` parameters of the <xref:System.Array.GetLowerBound%2A> and <xref:System.Array.GetUpperBound%2A> methods are 0-based, while the `Rank` parameters of the Visual Basic <xref:Microsoft.VisualBasic.Information.LBound%2A> and <xref:Microsoft.VisualBasic.Information.UBound%2A> functions are 1-based.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26f2f-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="26f2f-128">See also</span></span>

- [<span data-ttu-id="26f2f-129">数组</span><span class="sxs-lookup"><span data-stu-id="26f2f-129">Arrays</span></span>](index.md)
- [<span data-ttu-id="26f2f-130">如何：在 Visual Basic 中初始化数组变量</span><span class="sxs-lookup"><span data-stu-id="26f2f-130">How to: Initialize an Array Variable in Visual Basic</span></span>](how-to-initialize-an-array-variable.md)
