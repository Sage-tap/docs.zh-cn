---
description: '了解详细信息： (Visual Basic 的分部方法) '
title: 分部方法
ms.date: 07/20/2015
f1_keywords:
- vb.PartialMethod
- PartialMethod
helpviewer_keywords:
- custom logic into code [Visual Basic]
- partial methods [Visual Basic]
- partial [Visual Basic], methods [Visual Basic]
- methods [Visual Basic], partial methods
- inserting custom logic into code
ms.assetid: 74b3368b-b348-44a0-a326-7d7dc646f4e9
ms.openlocfilehash: d9be2d318ca0da9e1197949c88db5332832bdb3b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466713"
---
# <a name="partial-methods-visual-basic"></a><span data-ttu-id="4e2a5-103">分部方法 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4e2a5-103">Partial Methods (Visual Basic)</span></span>

<span data-ttu-id="4e2a5-104">利用分部方法，开发人员可以在代码中插入自定义逻辑。</span><span class="sxs-lookup"><span data-stu-id="4e2a5-104">Partial methods enable developers to insert custom logic into code.</span></span> <span data-ttu-id="4e2a5-105">通常，代码是设计器生成的类的一部分。</span><span class="sxs-lookup"><span data-stu-id="4e2a5-105">Typically, the code is part of a designer-generated class.</span></span> <span data-ttu-id="4e2a5-106">分部方法在由代码生成器创建的分部类中定义，并且通常用于提供已更改内容的通知。</span><span class="sxs-lookup"><span data-stu-id="4e2a5-106">Partial methods are defined in a partial class that is created by a code generator, and they are commonly used to provide notification that something has been changed.</span></span> <span data-ttu-id="4e2a5-107">开发人员可使用它们指定自定义行为来响应更改。</span><span class="sxs-lookup"><span data-stu-id="4e2a5-107">They enable the developer to specify custom behavior in response to the change.</span></span>  
  
 <span data-ttu-id="4e2a5-108">代码生成器的设计器仅定义方法签名和对方法的一次或多次调用。</span><span class="sxs-lookup"><span data-stu-id="4e2a5-108">The designer of the code generator defines only the method signature and one or more calls to the method.</span></span> <span data-ttu-id="4e2a5-109">如果开发人员想要自定义生成的代码的行为，则可以为方法提供实现。</span><span class="sxs-lookup"><span data-stu-id="4e2a5-109">Developers can then provide implementations for the method if they want to customize the behavior of the generated code.</span></span> <span data-ttu-id="4e2a5-110">当未提供实现时，编译器将删除对方法的调用，从而无额外的性能开销。</span><span class="sxs-lookup"><span data-stu-id="4e2a5-110">When no implementation is provided, calls to the method are removed by the compiler, resulting in no additional performance overhead.</span></span>  
  
## <a name="declaration"></a><span data-ttu-id="4e2a5-111">声明</span><span class="sxs-lookup"><span data-stu-id="4e2a5-111">Declaration</span></span>  

 <span data-ttu-id="4e2a5-112">生成的代码通过将关键字置于签名行的开头来标记分部方法的定义 `Partial` 。</span><span class="sxs-lookup"><span data-stu-id="4e2a5-112">The generated code marks the definition of a partial method by placing the keyword `Partial` at the start of the signature line.</span></span>  
  
```vb  
Partial Private Sub QuantityChanged()  
End Sub  
```  
  
 <span data-ttu-id="4e2a5-113">定义必须满足以下条件：</span><span class="sxs-lookup"><span data-stu-id="4e2a5-113">The definition must meet the following conditions:</span></span>  
  
- <span data-ttu-id="4e2a5-114">方法必须是 `Sub` 而不是 `Function` 。</span><span class="sxs-lookup"><span data-stu-id="4e2a5-114">The method must be a `Sub`, not a `Function`.</span></span>  
  
- <span data-ttu-id="4e2a5-115">方法的主体必须留空。</span><span class="sxs-lookup"><span data-stu-id="4e2a5-115">The body of the method must be left empty.</span></span>  
  
- <span data-ttu-id="4e2a5-116">访问修饰符必须是 `Private` 。</span><span class="sxs-lookup"><span data-stu-id="4e2a5-116">The access modifier must be `Private`.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="4e2a5-117">实现</span><span class="sxs-lookup"><span data-stu-id="4e2a5-117">Implementation</span></span>  

 <span data-ttu-id="4e2a5-118">实现主要包含在分部方法的主体中进行填充。</span><span class="sxs-lookup"><span data-stu-id="4e2a5-118">The implementation consists primarily of filling in the body of the partial method.</span></span> <span data-ttu-id="4e2a5-119">实现通常在独立于定义的分部类中，并由想要扩展生成的代码的开发人员编写。</span><span class="sxs-lookup"><span data-stu-id="4e2a5-119">The implementation is typically in a separate partial class from the definition, and is written by a developer who wants to extend the generated code.</span></span>  
  
```vb  
Private Sub QuantityChanged()  
'    Code for executing the desired action.  
End Sub  
```  
  
 <span data-ttu-id="4e2a5-120">前面的示例将在声明中完全复制签名，但可能会发生变化。</span><span class="sxs-lookup"><span data-stu-id="4e2a5-120">The previous example duplicates the signature in the declaration exactly, but variations are possible.</span></span> <span data-ttu-id="4e2a5-121">特别是，可以添加其他修饰符，如 `Overloads` 或 `Overrides` 。</span><span class="sxs-lookup"><span data-stu-id="4e2a5-121">In particular, other modifiers can be added, such as `Overloads` or `Overrides`.</span></span> <span data-ttu-id="4e2a5-122">只 `Overrides` 允许使用一个修饰符。</span><span class="sxs-lookup"><span data-stu-id="4e2a5-122">Only one `Overrides` modifier is permitted.</span></span> <span data-ttu-id="4e2a5-123">有关方法修饰符的详细信息，请参阅 [Sub 语句](../../../language-reference/statements/sub-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="4e2a5-123">For more information about method modifiers, see [Sub Statement](../../../language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="use"></a><span data-ttu-id="4e2a5-124">使用</span><span class="sxs-lookup"><span data-stu-id="4e2a5-124">Use</span></span>  

 <span data-ttu-id="4e2a5-125">调用分部方法的方法与调用任何其他过程一样 `Sub` 。</span><span class="sxs-lookup"><span data-stu-id="4e2a5-125">You call a partial method as you would call any other `Sub` procedure.</span></span> <span data-ttu-id="4e2a5-126">如果已实现方法，则将计算参数并执行方法的主体。</span><span class="sxs-lookup"><span data-stu-id="4e2a5-126">If the method has been implemented, the arguments are evaluated and the body of the method is executed.</span></span> <span data-ttu-id="4e2a5-127">但请记住，实现分部方法是可选的。</span><span class="sxs-lookup"><span data-stu-id="4e2a5-127">However, remember that implementing a partial method is optional.</span></span> <span data-ttu-id="4e2a5-128">如果未实现该方法，则对它的调用不起作用，并且不计算作为参数传递给方法的表达式。</span><span class="sxs-lookup"><span data-stu-id="4e2a5-128">If the method is not implemented, a call to it has no effect, and expressions passed as arguments to the method are not evaluated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e2a5-129">示例</span><span class="sxs-lookup"><span data-stu-id="4e2a5-129">Example</span></span>  

 <span data-ttu-id="4e2a5-130">在名为 "node.js" 的文件中，定义一个 `Product` 具有属性的类 `Quantity` 。</span><span class="sxs-lookup"><span data-stu-id="4e2a5-130">In a file named Product.Designer.vb, define a `Product` class that has a `Quantity` property.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#4)]  
  
 <span data-ttu-id="4e2a5-131">在名为 ".vb" 的文件中，提供的实现 `QuantityChanged` 。</span><span class="sxs-lookup"><span data-stu-id="4e2a5-131">In a file named Product.vb, provide an implementation for `QuantityChanged`.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#5)]  
  
 <span data-ttu-id="4e2a5-132">最后，在项目的 Main 方法中，声明一个 `Product` 实例，并为其属性提供初始值 `Quantity` 。</span><span class="sxs-lookup"><span data-stu-id="4e2a5-132">Finally, in the Main method of a project, declare a `Product` instance and provide an initial value for its `Quantity` property.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#6)]  
  
 <span data-ttu-id="4e2a5-133">此时将显示一个消息框，显示此消息：</span><span class="sxs-lookup"><span data-stu-id="4e2a5-133">A message box should appear that displays this message:</span></span>  
  
 `Quantity was changed to 100`  
  
## <a name="see-also"></a><span data-ttu-id="4e2a5-134">请参阅</span><span class="sxs-lookup"><span data-stu-id="4e2a5-134">See also</span></span>

- [<span data-ttu-id="4e2a5-135">Sub 语句</span><span class="sxs-lookup"><span data-stu-id="4e2a5-135">Sub Statement</span></span>](../../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="4e2a5-136">Sub 过程</span><span class="sxs-lookup"><span data-stu-id="4e2a5-136">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="4e2a5-137">可选参数</span><span class="sxs-lookup"><span data-stu-id="4e2a5-137">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="4e2a5-138">Partial</span><span class="sxs-lookup"><span data-stu-id="4e2a5-138">Partial</span></span>](../../../language-reference/modifiers/partial.md)
- [<span data-ttu-id="4e2a5-139">LINQ to SQL 中的代码生成</span><span class="sxs-lookup"><span data-stu-id="4e2a5-139">Code Generation in LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="4e2a5-140">通过使用分部方法添加业务逻辑</span><span class="sxs-lookup"><span data-stu-id="4e2a5-140">Adding Business Logic By Using Partial Methods</span></span>](../../../../framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)
