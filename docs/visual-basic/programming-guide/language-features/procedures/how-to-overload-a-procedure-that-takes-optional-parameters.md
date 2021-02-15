---
description: '了解有关详细信息，请参阅如何：重载带有可选参数的过程 (Visual Basic) '
title: 如何：重载带有可选参数的过程
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], optional parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: 825f9d56-4cde-43fd-993a-b9171717e2eb
ms.openlocfilehash: dccef9d27c08ede2f35edc02c8bd5116aa6969b2
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100472938"
---
# <a name="how-to-overload-a-procedure-that-takes-optional-parameters-visual-basic"></a><span data-ttu-id="96bda-103">如何：重载带有可选参数的过程 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="96bda-103">How to: Overload a Procedure that Takes Optional Parameters (Visual Basic)</span></span>

<span data-ttu-id="96bda-104">如果过程有一个或多个 [可选](../../../language-reference/modifiers/optional.md) 参数，则不能定义与它的任何隐式重载匹配的重载版本。</span><span class="sxs-lookup"><span data-stu-id="96bda-104">If a procedure has one or more [Optional](../../../language-reference/modifiers/optional.md) parameters, you cannot define an overloaded version matching any of its implicit overloads.</span></span> <span data-ttu-id="96bda-105">有关详细信息，请参阅 [重载过程的注意事项](./considerations-in-overloading-procedures.md)中的 "可选参数的隐式重载"。</span><span class="sxs-lookup"><span data-stu-id="96bda-105">For more information, see "Implicit Overloads for Optional Parameters" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="one-optional-parameter"></a><span data-ttu-id="96bda-106">一个可选参数</span><span class="sxs-lookup"><span data-stu-id="96bda-106">One Optional Parameter</span></span>  
  
#### <a name="to-overload-a-procedure-that-takes-one-optional-parameter"></a><span data-ttu-id="96bda-107">重载采用一个可选参数的过程</span><span class="sxs-lookup"><span data-stu-id="96bda-107">To overload a procedure that takes one optional parameter</span></span>  
  
1. <span data-ttu-id="96bda-108">编写一个 `Sub` 或 `Function` 声明语句，其中包含参数列表中的可选参数。</span><span class="sxs-lookup"><span data-stu-id="96bda-108">Write a `Sub` or `Function` declaration statement that includes the optional parameter in the parameter list.</span></span> <span data-ttu-id="96bda-109">不要 `Optional` 在此重载版本中使用关键字。</span><span class="sxs-lookup"><span data-stu-id="96bda-109">Do not use the `Optional` keyword in this overloaded version.</span></span>  
  
2. <span data-ttu-id="96bda-110">在或关键字之前加上 `Sub` `Function` [Overloads](../../../language-reference/modifiers/overloads.md) 关键字。</span><span class="sxs-lookup"><span data-stu-id="96bda-110">Precede the `Sub` or `Function` keyword with the [Overloads](../../../language-reference/modifiers/overloads.md) keyword.</span></span>  
  
3. <span data-ttu-id="96bda-111">编写调用代码提供可选参数时应执行的过程代码。</span><span class="sxs-lookup"><span data-stu-id="96bda-111">Write the procedure code that should execute when the calling code supplies the optional argument.</span></span>  
  
4. <span data-ttu-id="96bda-112">`End Sub`适当地终止带有或语句的过程 `End Function` 。</span><span class="sxs-lookup"><span data-stu-id="96bda-112">Terminate the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
5. <span data-ttu-id="96bda-113">编写与第一个声明相同的第二个声明语句，只不过它不在参数列表中包含可选参数。</span><span class="sxs-lookup"><span data-stu-id="96bda-113">Write a second declaration statement that is identical to the first declaration except that it does not include the optional parameter in the parameter list.</span></span>  
  
6. <span data-ttu-id="96bda-114">编写调用代码未提供可选参数时应执行的过程代码。</span><span class="sxs-lookup"><span data-stu-id="96bda-114">Write the procedure code that should execute when the calling code does not supply the optional argument.</span></span> <span data-ttu-id="96bda-115">`End Sub`适当地终止带有或语句的过程 `End Function` 。</span><span class="sxs-lookup"><span data-stu-id="96bda-115">Terminate the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
     <span data-ttu-id="96bda-116">下面的示例演示了一个使用可选参数定义的过程，这是一组等效的两个重载过程，最后是无效和有效重载版本的示例。</span><span class="sxs-lookup"><span data-stu-id="96bda-116">The following example shows a procedure defined with an optional parameter,  an equivalent set of two overloaded procedures, and finally examples of both invalid and valid overloaded versions.</span></span>  
  
     [!code-vb[VbVbcnProcedures#59](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#59)]  
  
     [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
     [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
## <a name="multiple-optional-parameters"></a><span data-ttu-id="96bda-117">多个可选参数</span><span class="sxs-lookup"><span data-stu-id="96bda-117">Multiple Optional Parameters</span></span>  

 <span data-ttu-id="96bda-118">对于具有多个可选参数的过程，通常需要两个以上的重载版本。</span><span class="sxs-lookup"><span data-stu-id="96bda-118">For a procedure with more than one optional parameter, you normally need more than two overloaded versions.</span></span> <span data-ttu-id="96bda-119">例如，如果有两个可选参数，并且调用代码可以单独提供或省略每个参数，则需要四个重载版本，每个可用于提供的参数的每个可能组合。</span><span class="sxs-lookup"><span data-stu-id="96bda-119">For example, if there are two optional parameters, and the calling code can supply or omit each one independently of the other, you need four overloaded versions, one for each possible combination of supplied arguments.</span></span>  
  
 <span data-ttu-id="96bda-120">当可选参数的数目增加时，重载的复杂性会增加。</span><span class="sxs-lookup"><span data-stu-id="96bda-120">As the number of optional parameters increases, the complexity of the overloading increases.</span></span> <span data-ttu-id="96bda-121">除非提供的参数的某些组合是不可接受的，否则对于 N 个可选参数，你需要 2 ^ N 个重载版本。</span><span class="sxs-lookup"><span data-stu-id="96bda-121">Unless some combinations of supplied arguments are not acceptable, for N optional parameters you need 2 ^ N overloaded versions.</span></span> <span data-ttu-id="96bda-122">根据过程的性质，你可能会发现逻辑清晰地会调整定义所有重载版本的额外工作量。</span><span class="sxs-lookup"><span data-stu-id="96bda-122">Depending on the nature of the procedure, you might find that the clarity of logic justifies the extra effort of defining all the overloaded versions.</span></span>  
  
#### <a name="to-overload-a-procedure-that-takes-more-than-one-optional-parameter"></a><span data-ttu-id="96bda-123">重载一个具有多个可选参数的过程</span><span class="sxs-lookup"><span data-stu-id="96bda-123">To overload a procedure that takes more than one optional parameter</span></span>  
  
1. <span data-ttu-id="96bda-124">确定所提供的可选参数的哪些组合对于过程逻辑是可接受的。</span><span class="sxs-lookup"><span data-stu-id="96bda-124">Determine which combinations of supplied optional arguments are acceptable to the logic of the procedure.</span></span> <span data-ttu-id="96bda-125">如果一个可选参数依赖于另一个参数，则可能会产生不可接受的组合。</span><span class="sxs-lookup"><span data-stu-id="96bda-125">An unacceptable combination might arise if one optional parameter depends on another.</span></span> <span data-ttu-id="96bda-126">例如，如果一个参数接受某人的名字，另一个参数接受该用户的年龄，则提供年龄但省略名称的参数的组合是不可接受的。</span><span class="sxs-lookup"><span data-stu-id="96bda-126">For example, if one parameter accepts a person's name and another accepts the person's age, a combination of arguments supplying the age but omitting the name is unacceptable.</span></span>  
  
2. <span data-ttu-id="96bda-127">对于提供的可选参数的每个可接受组合，编写一个 `Sub` `Function` 定义相应参数列表的或声明语句。</span><span class="sxs-lookup"><span data-stu-id="96bda-127">For each acceptable combination of supplied optional arguments, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span></span> <span data-ttu-id="96bda-128">不要使用 `Optional` 关键字。</span><span class="sxs-lookup"><span data-stu-id="96bda-128">Do not use the `Optional` keyword.</span></span>  
  
3. <span data-ttu-id="96bda-129">在每个声明中，在或关键字之前加上 `Sub` `Function` [Overloads](../../../language-reference/modifiers/overloads.md) 关键字。</span><span class="sxs-lookup"><span data-stu-id="96bda-129">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../language-reference/modifiers/overloads.md) keyword.</span></span>  
  
4. <span data-ttu-id="96bda-130">在每个声明之后，编写调用代码提供对应于该声明的参数列表的参数列表时应执行的过程代码。</span><span class="sxs-lookup"><span data-stu-id="96bda-130">Following each declaration, write the procedure code that should execute when the calling code supplies an argument list corresponding to that declaration's parameter list.</span></span>  
  
5. <span data-ttu-id="96bda-131">根据需要，用或语句终止每个过程 `End Sub` `End Function` 。</span><span class="sxs-lookup"><span data-stu-id="96bda-131">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96bda-132">请参阅</span><span class="sxs-lookup"><span data-stu-id="96bda-132">See also</span></span>

- [<span data-ttu-id="96bda-133">过程</span><span class="sxs-lookup"><span data-stu-id="96bda-133">Procedures</span></span>](./index.md)
- [<span data-ttu-id="96bda-134">过程形参和实参</span><span class="sxs-lookup"><span data-stu-id="96bda-134">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="96bda-135">可选参数</span><span class="sxs-lookup"><span data-stu-id="96bda-135">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="96bda-136">参数数组</span><span class="sxs-lookup"><span data-stu-id="96bda-136">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="96bda-137">过程重载</span><span class="sxs-lookup"><span data-stu-id="96bda-137">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="96bda-138">过程疑难解答</span><span class="sxs-lookup"><span data-stu-id="96bda-138">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="96bda-139">如何：定义一个过程的多个版本</span><span class="sxs-lookup"><span data-stu-id="96bda-139">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="96bda-140">如何：调用重载过程</span><span class="sxs-lookup"><span data-stu-id="96bda-140">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="96bda-141">如何：重载参数数量不确定的过程</span><span class="sxs-lookup"><span data-stu-id="96bda-141">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="96bda-142">重载决策</span><span class="sxs-lookup"><span data-stu-id="96bda-142">Overload Resolution</span></span>](./overload-resolution.md)
