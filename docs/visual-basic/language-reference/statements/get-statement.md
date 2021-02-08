---
description: 了解详细信息： Get 语句
title: Get 语句
ms.date: 07/20/2015
f1_keywords:
- vb.Get
helpviewer_keywords:
- Get statement [Visual Basic], syntax
- Get statement [Visual Basic]
- properties [Visual Basic], read-only
- read-only properties
- Get keyword [Visual Basic]
- property procedures [Visual Basic], Get statements
ms.assetid: 56b05cdc-bd64-4dfd-bb12-824eacec6f94
ms.openlocfilehash: 1cda485867a941129ab2453d4c0900d1403f4e8d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99769034"
---
# <a name="get-statement"></a><span data-ttu-id="a8eab-103">Get 语句</span><span class="sxs-lookup"><span data-stu-id="a8eab-103">Get Statement</span></span>

<span data-ttu-id="a8eab-104">声明 `Get` 用于检索属性值的属性过程。</span><span class="sxs-lookup"><span data-stu-id="a8eab-104">Declares a `Get` property procedure used to retrieve the value of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8eab-105">语法</span><span class="sxs-lookup"><span data-stu-id="a8eab-105">Syntax</span></span>  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Get()  
    [ statements ]  
End Get  
```  
  
## <a name="parts"></a><span data-ttu-id="a8eab-106">组成部分</span><span class="sxs-lookup"><span data-stu-id="a8eab-106">Parts</span></span>  
  
|<span data-ttu-id="a8eab-107">术语</span><span class="sxs-lookup"><span data-stu-id="a8eab-107">Term</span></span>|<span data-ttu-id="a8eab-108">定义</span><span class="sxs-lookup"><span data-stu-id="a8eab-108">Definition</span></span>|  
|---|---|  
|`attributelist`|<span data-ttu-id="a8eab-109">可选。</span><span class="sxs-lookup"><span data-stu-id="a8eab-109">Optional.</span></span> <span data-ttu-id="a8eab-110">请参阅 [特性列表](attribute-list.md)。</span><span class="sxs-lookup"><span data-stu-id="a8eab-110">See [Attribute List](attribute-list.md).</span></span>|  
|`accessmodifier`|<span data-ttu-id="a8eab-111">在 `Get` 此属性中的最多一个和语句上是可选的 `Set` 。</span><span class="sxs-lookup"><span data-stu-id="a8eab-111">Optional on at most one of the `Get` and `Set` statements in this property.</span></span> <span data-ttu-id="a8eab-112">可以是以下其中一个值：</span><span class="sxs-lookup"><span data-stu-id="a8eab-112">Can be one of the following:</span></span><br /><br /> <span data-ttu-id="a8eab-113">-   [避免](../modifiers/protected.md)</span><span class="sxs-lookup"><span data-stu-id="a8eab-113">-   [Protected](../modifiers/protected.md)</span></span><br /><span data-ttu-id="a8eab-114">-   [友好](../modifiers/friend.md)</span><span class="sxs-lookup"><span data-stu-id="a8eab-114">-   [Friend](../modifiers/friend.md)</span></span><br /><span data-ttu-id="a8eab-115">-   [专有](../modifiers/private.md)</span><span class="sxs-lookup"><span data-stu-id="a8eab-115">-   [Private](../modifiers/private.md)</span></span><br />-   `Protected Friend`<br /><br /> <span data-ttu-id="a8eab-116">请参阅 [Visual Basic 中的访问级别](../../programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="a8eab-116">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>|  
|`statements`|<span data-ttu-id="a8eab-117">可选。</span><span class="sxs-lookup"><span data-stu-id="a8eab-117">Optional.</span></span> <span data-ttu-id="a8eab-118">调用属性过程时运行的一个或多个语句 `Get` 。</span><span class="sxs-lookup"><span data-stu-id="a8eab-118">One or more statements that run when the `Get` property procedure is called.</span></span>|  
|`End Get`|<span data-ttu-id="a8eab-119">必需。</span><span class="sxs-lookup"><span data-stu-id="a8eab-119">Required.</span></span> <span data-ttu-id="a8eab-120">终止属性过程的定义 `Get` 。</span><span class="sxs-lookup"><span data-stu-id="a8eab-120">Terminates the definition of the `Get` property procedure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8eab-121">备注</span><span class="sxs-lookup"><span data-stu-id="a8eab-121">Remarks</span></span>  

 <span data-ttu-id="a8eab-122">除非将属性标记为，否则每个属性都必须具有 `Get` 属性过程 `WriteOnly` 。</span><span class="sxs-lookup"><span data-stu-id="a8eab-122">Every property must have a `Get` property procedure unless the property is marked `WriteOnly`.</span></span> <span data-ttu-id="a8eab-123">此 `Get` 过程用于返回属性的当前值。</span><span class="sxs-lookup"><span data-stu-id="a8eab-123">The `Get` procedure is used to return the current value of the property.</span></span>  
  
 <span data-ttu-id="a8eab-124">当表达式请求属性值时，Visual Basic 会自动调用该属性的 `Get` 过程。</span><span class="sxs-lookup"><span data-stu-id="a8eab-124">Visual Basic automatically calls a property's `Get` procedure when an expression requests the property's value.</span></span>  
  
 <span data-ttu-id="a8eab-125">属性声明的主体只能在 `Get` `Set` [property 语句](property-statement.md) 和语句之间包含属性的和过程 `End Property` 。</span><span class="sxs-lookup"><span data-stu-id="a8eab-125">The body of the property declaration can contain only the property's `Get` and `Set` procedures between the [Property Statement](property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="a8eab-126">它无法存储这些过程以外的任何内容。</span><span class="sxs-lookup"><span data-stu-id="a8eab-126">It cannot store anything other than those procedures.</span></span> <span data-ttu-id="a8eab-127">特别是，它无法存储属性的当前值。</span><span class="sxs-lookup"><span data-stu-id="a8eab-127">In particular, it cannot store the property's current value.</span></span> <span data-ttu-id="a8eab-128">您必须将此值存储在属性的外部，因为如果将其存储在任一属性过程中，则其他属性过程将无法访问它。</span><span class="sxs-lookup"><span data-stu-id="a8eab-128">You must store this value outside the property, because if you store it inside either of the property procedures, the other property procedure cannot access it.</span></span> <span data-ttu-id="a8eab-129">常见的方法是将值存储在与属性在同一级别上声明的 [私有](../modifiers/private.md) 变量中。</span><span class="sxs-lookup"><span data-stu-id="a8eab-129">The usual approach is to store the value in a [Private](../modifiers/private.md) variable declared at the same level as the property.</span></span> <span data-ttu-id="a8eab-130">必须在应用的 `Get` 属性中定义一个过程。</span><span class="sxs-lookup"><span data-stu-id="a8eab-130">You must define a `Get` procedure inside the property to which it applies.</span></span>  
  
 <span data-ttu-id="a8eab-131">此 `Get` 过程默认为其包含属性的访问级别，除非你 `accessmodifier` 在语句中使用 `Get` 。</span><span class="sxs-lookup"><span data-stu-id="a8eab-131">The `Get` procedure defaults to the access level of its containing property unless you use `accessmodifier` in the `Get` statement.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="a8eab-132">规则</span><span class="sxs-lookup"><span data-stu-id="a8eab-132">Rules</span></span>  
  
- <span data-ttu-id="a8eab-133">**混合访问级别。**</span><span class="sxs-lookup"><span data-stu-id="a8eab-133">**Mixed Access Levels.**</span></span> <span data-ttu-id="a8eab-134">如果要定义读写属性，则可以选择为或过程指定不同的访问级别 `Get` `Set` ，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="a8eab-134">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="a8eab-135">如果执行此操作，则过程访问级别必须比属性的访问级别更严格。</span><span class="sxs-lookup"><span data-stu-id="a8eab-135">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="a8eab-136">例如，如果声明了属性 `Friend` ，则可以声明该 `Get` 过程 `Private` ，而不是 `Public` 。</span><span class="sxs-lookup"><span data-stu-id="a8eab-136">For example, if the property is declared `Friend`, you can declare the `Get` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="a8eab-137">如果要定义 `ReadOnly` 属性，则该 `Get` 过程表示整个属性。</span><span class="sxs-lookup"><span data-stu-id="a8eab-137">If you are defining a `ReadOnly` property, the `Get` procedure represents the entire property.</span></span> <span data-ttu-id="a8eab-138">不能为声明不同的访问级别 `Get` ，因为这会为属性设置两个访问级别。</span><span class="sxs-lookup"><span data-stu-id="a8eab-138">You cannot declare a different access level for `Get`, because that would set two access levels for the property.</span></span>  
  
- <span data-ttu-id="a8eab-139">**返回类型。**</span><span class="sxs-lookup"><span data-stu-id="a8eab-139">**Return Type.**</span></span> <span data-ttu-id="a8eab-140">[Property 语句](property-statement.md)可以声明其返回的值的数据类型。</span><span class="sxs-lookup"><span data-stu-id="a8eab-140">The [Property Statement](property-statement.md) can declare the data type of the value it returns.</span></span> <span data-ttu-id="a8eab-141">`Get`过程会自动返回该数据类型。</span><span class="sxs-lookup"><span data-stu-id="a8eab-141">The `Get` procedure automatically returns that data type.</span></span> <span data-ttu-id="a8eab-142">您可以指定任何数据类型或枚举、结构、类或接口的名称。</span><span class="sxs-lookup"><span data-stu-id="a8eab-142">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>  
  
     <span data-ttu-id="a8eab-143">如果 `Property` 语句未指定 `returntype` ，则该过程返回 `Object` 。</span><span class="sxs-lookup"><span data-stu-id="a8eab-143">If the `Property` statement does not specify `returntype`, the procedure returns `Object`.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="a8eab-144">行为</span><span class="sxs-lookup"><span data-stu-id="a8eab-144">Behavior</span></span>  
  
- <span data-ttu-id="a8eab-145">**从过程返回。**</span><span class="sxs-lookup"><span data-stu-id="a8eab-145">**Returning from a Procedure.**</span></span> <span data-ttu-id="a8eab-146">当 `Get` 过程返回到调用代码时，执行将在请求属性值的语句中继续执行。</span><span class="sxs-lookup"><span data-stu-id="a8eab-146">When the `Get` procedure returns to the calling code, execution continues within the statement that requested the property value.</span></span>  
  
     <span data-ttu-id="a8eab-147">`Get` 属性过程可以使用 [Return 语句](return-statement.md) 或通过将返回值分配给属性名称来返回值。</span><span class="sxs-lookup"><span data-stu-id="a8eab-147">`Get` property procedures can return a value using either the [Return Statement](return-statement.md) or by assigning the return value to the property name.</span></span> <span data-ttu-id="a8eab-148">有关详细信息，请参阅 [Function 语句](function-statement.md)中的 "返回值"。</span><span class="sxs-lookup"><span data-stu-id="a8eab-148">For more information, see "Return Value" in [Function Statement](function-statement.md).</span></span>  
  
     <span data-ttu-id="a8eab-149">`Exit Property`和 `Return` 语句导致直接从属性过程退出。</span><span class="sxs-lookup"><span data-stu-id="a8eab-149">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="a8eab-150">任意数量的 `Exit Property` 和 `Return` 语句可以出现在过程中的任何位置，并且可以混合使用 `Exit Property` 和 `Return` 语句。</span><span class="sxs-lookup"><span data-stu-id="a8eab-150">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
- <span data-ttu-id="a8eab-151">**返回值。**</span><span class="sxs-lookup"><span data-stu-id="a8eab-151">**Return Value.**</span></span> <span data-ttu-id="a8eab-152">若要从过程返回值 `Get` ，可将值分配给属性名称，或将其包含在 [return 语句](return-statement.md)中。</span><span class="sxs-lookup"><span data-stu-id="a8eab-152">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a [Return Statement](return-statement.md).</span></span> <span data-ttu-id="a8eab-153">`Return`语句同时分配 `Get` 过程返回值并退出该过程。</span><span class="sxs-lookup"><span data-stu-id="a8eab-153">The `Return` statement simultaneously assigns the `Get` procedure return value and exits the procedure.</span></span>  
  
     <span data-ttu-id="a8eab-154">如果使用时 `Exit Property` 没有为属性名称赋值，则该过程将 `Get` 返回属性数据类型的默认值。</span><span class="sxs-lookup"><span data-stu-id="a8eab-154">If you use `Exit Property` without assigning a value to the property name, the `Get` procedure returns the default value for the property's data type.</span></span> <span data-ttu-id="a8eab-155">有关详细信息，请参阅 [Function 语句](function-statement.md)中的 "返回值"。</span><span class="sxs-lookup"><span data-stu-id="a8eab-155">For more information, see "Return Value" in [Function Statement](function-statement.md).</span></span>  
  
     <span data-ttu-id="a8eab-156">下面的示例演示了只读属性 `quoteForTheDay` 可以返回保存在私有变量中的值的两种方法 `quoteValue` 。</span><span class="sxs-lookup"><span data-stu-id="a8eab-156">The following example illustrates two ways the read-only property `quoteForTheDay` can return the value held in the private variable `quoteValue`.</span></span>  
  
     [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]  
  
     [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]  
  
     [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]  
  
## <a name="example"></a><span data-ttu-id="a8eab-157">示例</span><span class="sxs-lookup"><span data-stu-id="a8eab-157">Example</span></span>  

 <span data-ttu-id="a8eab-158">下面的示例使用 `Get` 语句返回属性的值。</span><span class="sxs-lookup"><span data-stu-id="a8eab-158">The following example uses the `Get` statement to return the value of a property.</span></span>  
  
 [!code-vb[VbVbalrStatements#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="a8eab-159">请参阅</span><span class="sxs-lookup"><span data-stu-id="a8eab-159">See also</span></span>

- [<span data-ttu-id="a8eab-160">Set 语句</span><span class="sxs-lookup"><span data-stu-id="a8eab-160">Set Statement</span></span>](set-statement.md)
- [<span data-ttu-id="a8eab-161">Property Statement</span><span class="sxs-lookup"><span data-stu-id="a8eab-161">Property Statement</span></span>](property-statement.md)
- [<span data-ttu-id="a8eab-162">Exit 语句</span><span class="sxs-lookup"><span data-stu-id="a8eab-162">Exit Statement</span></span>](exit-statement.md)
- [<span data-ttu-id="a8eab-163">对象和类</span><span class="sxs-lookup"><span data-stu-id="a8eab-163">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="a8eab-164">演练：定义类</span><span class="sxs-lookup"><span data-stu-id="a8eab-164">Walkthrough: Defining Classes</span></span>](../../programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)
