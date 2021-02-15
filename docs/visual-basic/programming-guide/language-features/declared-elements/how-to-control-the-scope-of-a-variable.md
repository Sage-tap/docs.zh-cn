---
description: '了解有关详细信息，请参阅如何：控制变量 (Visual Basic 的作用域) '
title: 如何：控制变量的范围
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], scope
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- variables [Visual Basic], visibility
- scope [Visual Basic], declared elements
- scope [Visual Basic], variables
- scope [Visual Basic], Visual Basic
- declared elements [Visual Basic], visibility
- visibility [Visual Basic], variables
ms.assetid: 44b7f62a-cb5c-4d50-bce9-60ae68f87072
ms.openlocfilehash: c6da599f76883cba545efbdf9570aa05770602a2
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100429866"
---
# <a name="how-to-control-the-scope-of-a-variable-visual-basic"></a><span data-ttu-id="8a54d-103">如何：控制变量的范围 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8a54d-103">How to: Control the Scope of a Variable (Visual Basic)</span></span>

<span data-ttu-id="8a54d-104">通常，变量在声明它的整个区域内处于 *范围* 内，或者在引用中可见。</span><span class="sxs-lookup"><span data-stu-id="8a54d-104">Normally, a variable is in *scope*, or visible for reference, throughout the region in which you declare it.</span></span> <span data-ttu-id="8a54d-105">在某些情况下，变量的 *访问级别* 会影响其作用域。</span><span class="sxs-lookup"><span data-stu-id="8a54d-105">In some cases, the variable's *access level* can influence its scope.</span></span>  
  
 <span data-ttu-id="8a54d-106">有关详细信息，请参阅 [Scope in Visual Basic](scope.md)。</span><span class="sxs-lookup"><span data-stu-id="8a54d-106">For more information, see [Scope in Visual Basic](scope.md).</span></span>  
  
## <a name="scope-at-block-or-procedure-level"></a><span data-ttu-id="8a54d-107">块或过程级别的作用域</span><span class="sxs-lookup"><span data-stu-id="8a54d-107">Scope at Block or Procedure Level</span></span>  
  
#### <a name="to-make-a-variable-visible-only-within-a-block"></a><span data-ttu-id="8a54d-108">使变量仅在块中可见</span><span class="sxs-lookup"><span data-stu-id="8a54d-108">To make a variable visible only within a block</span></span>  
  
- <span data-ttu-id="8a54d-109">将变量的 [Dim 语句](../../../language-reference/statements/dim-statement.md) 置于该块的起始和终止声明语句之间，例如，在 `For` 循环的和语句之间 `Next` `For` 。</span><span class="sxs-lookup"><span data-stu-id="8a54d-109">Place the [Dim Statement](../../../language-reference/statements/dim-statement.md) for the variable between the initiating and terminating declaration statements of that block, for example between the `For` and `Next` statements of a `For` loop.</span></span>  
  
     <span data-ttu-id="8a54d-110">只能从块内引用该变量。</span><span class="sxs-lookup"><span data-stu-id="8a54d-110">You can refer to the variable only from within the block.</span></span>  
  
#### <a name="to-make-a-variable-visible-only-within-a-procedure"></a><span data-ttu-id="8a54d-111">使变量仅在过程中可见</span><span class="sxs-lookup"><span data-stu-id="8a54d-111">To make a variable visible only within a procedure</span></span>  
  
- <span data-ttu-id="8a54d-112">将变量的语句放置在 `Dim` 过程中，但在任何块 (（例如 `With` ... `End With` 块) ）的外部。</span><span class="sxs-lookup"><span data-stu-id="8a54d-112">Place the `Dim` statement for the variable inside the procedure but outside any block (such as a `With`...`End With` block).</span></span>  
  
     <span data-ttu-id="8a54d-113">您只能从过程内引用变量，包括过程中包含的任何块。</span><span class="sxs-lookup"><span data-stu-id="8a54d-113">You can refer to the variable only from within the procedure, including inside any block contained in the procedure.</span></span>  
  
## <a name="scope-at-module-or-namespace-level"></a><span data-ttu-id="8a54d-114">模块或命名空间级别的作用域</span><span class="sxs-lookup"><span data-stu-id="8a54d-114">Scope at Module or Namespace Level</span></span>  

 <span data-ttu-id="8a54d-115">为方便起见，单术语 *模块级别* 同样适用于模块、类和结构。</span><span class="sxs-lookup"><span data-stu-id="8a54d-115">For convenience, the single term *module level* applies equally to modules, classes, and structures.</span></span> <span data-ttu-id="8a54d-116">模块级别变量的访问级别确定其作用域。</span><span class="sxs-lookup"><span data-stu-id="8a54d-116">The access level of a module level variable determines its scope.</span></span> <span data-ttu-id="8a54d-117">包含模块、类或结构的命名空间还会影响范围。</span><span class="sxs-lookup"><span data-stu-id="8a54d-117">The namespace that contains the module, class, or structure also influences the scope.</span></span>  
  
#### <a name="to-make-a-variable-visible-throughout-a-module-class-or-structure"></a><span data-ttu-id="8a54d-118">使变量在整个模块、类或结构中可见</span><span class="sxs-lookup"><span data-stu-id="8a54d-118">To make a variable visible throughout a module, class, or structure</span></span>  
  
1. <span data-ttu-id="8a54d-119">将变量的语句放入 `Dim` 模块、类或结构中，但放在任何过程之外。</span><span class="sxs-lookup"><span data-stu-id="8a54d-119">Place the `Dim` statement for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="8a54d-120">在语句中包含 [Private](../../../language-reference/modifiers/private.md) 关键字 `Dim` 。</span><span class="sxs-lookup"><span data-stu-id="8a54d-120">Include the [Private](../../../language-reference/modifiers/private.md) keyword in the `Dim` statement.</span></span>  
  
3. <span data-ttu-id="8a54d-121">可以从模块、类或结构中的任何位置引用该变量，而不能从外部引用。</span><span class="sxs-lookup"><span data-stu-id="8a54d-121">You can refer to the variable from anywhere within the module, class, or structure, but not from outside it.</span></span>  
  
#### <a name="to-make-a-variable-visible-throughout-a-namespace"></a><span data-ttu-id="8a54d-122">使变量在整个命名空间中可见</span><span class="sxs-lookup"><span data-stu-id="8a54d-122">To make a variable visible throughout a namespace</span></span>  
  
1. <span data-ttu-id="8a54d-123">将变量的语句放入 `Dim` 模块、类或结构中，但放在任何过程之外。</span><span class="sxs-lookup"><span data-stu-id="8a54d-123">Place the `Dim` statement for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="8a54d-124">在语句中包含 [Friend](../../../language-reference/modifiers/friend.md) 或 [Public](../../../language-reference/modifiers/public.md) 关键字 `Dim` 。</span><span class="sxs-lookup"><span data-stu-id="8a54d-124">Include the [Friend](../../../language-reference/modifiers/friend.md) or [Public](../../../language-reference/modifiers/public.md) keyword in the `Dim` statement.</span></span>  
  
3. <span data-ttu-id="8a54d-125">可以从包含模块、类或结构的命名空间中的任何位置引用该变量。</span><span class="sxs-lookup"><span data-stu-id="8a54d-125">You can refer to the variable from anywhere within the namespace containing the module, class, or structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a54d-126">示例</span><span class="sxs-lookup"><span data-stu-id="8a54d-126">Example</span></span>  

 <span data-ttu-id="8a54d-127">下面的示例在模块级别声明一个变量，并将其可见性限制为模块中的代码。</span><span class="sxs-lookup"><span data-stu-id="8a54d-127">The following example declares a variable at module level and limits its visibility to code within the module.</span></span>  
  
```vb  
Module demonstrateScope  
    Private strMsg As String  
    Sub initializePrivateVariable()  
        strMsg = "This variable cannot be used outside this module."  
    End Sub  
    Sub usePrivateVariable()  
        MsgBox(strMsg)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="8a54d-128">在前面的示例中，模块中定义的所有过程 `demonstrateScope` 都可以引用 `String` 变量 `strMsg` 。</span><span class="sxs-lookup"><span data-stu-id="8a54d-128">In the preceding example, all the procedures defined in module `demonstrateScope` can refer to the `String` variable `strMsg`.</span></span> <span data-ttu-id="8a54d-129">调用此 `usePrivateVariable` 过程时，它将在对话框中显示字符串变量的内容 `strMsg` 。</span><span class="sxs-lookup"><span data-stu-id="8a54d-129">When the `usePrivateVariable` procedure is called, it displays the contents of the string variable `strMsg` in a dialog box.</span></span>  
  
 <span data-ttu-id="8a54d-130">对于前面的示例的以下更改，字符串变量 `strMsg` 可以在其声明的命名空间中的任何位置通过代码引用。</span><span class="sxs-lookup"><span data-stu-id="8a54d-130">With the following alteration to the preceding example, the string variable `strMsg` can be referred to by code anywhere in the namespace of its declaration.</span></span>  
  
```vb  
Public strMsg As String  
```  
  
## <a name="robust-programming"></a><span data-ttu-id="8a54d-131">可靠编程</span><span class="sxs-lookup"><span data-stu-id="8a54d-131">Robust Programming</span></span>  

 <span data-ttu-id="8a54d-132">变量的作用域越窄，使用同一名称的另一个变量无意引用它就越少机会。</span><span class="sxs-lookup"><span data-stu-id="8a54d-132">The narrower the scope of a variable, the fewer opportunities you have for accidentally referring to it in place of another variable with the same name.</span></span> <span data-ttu-id="8a54d-133">你还可以最大程度地减少引用匹配的问题。</span><span class="sxs-lookup"><span data-stu-id="8a54d-133">You can also minimize problems of reference matching.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="8a54d-134">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="8a54d-134">.NET Framework Security</span></span>  

 <span data-ttu-id="8a54d-135">变量的范围越窄，恶意代码使用它的机会就越小。</span><span class="sxs-lookup"><span data-stu-id="8a54d-135">The narrower the scope of a variable, the smaller the chances that malicious code can make improper use of it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a54d-136">请参阅</span><span class="sxs-lookup"><span data-stu-id="8a54d-136">See also</span></span>

- [<span data-ttu-id="8a54d-137">Visual Basic 中的范围</span><span class="sxs-lookup"><span data-stu-id="8a54d-137">Scope in Visual Basic</span></span>](scope.md)
- [<span data-ttu-id="8a54d-138">Visual Basic 中的生存期</span><span class="sxs-lookup"><span data-stu-id="8a54d-138">Lifetime in Visual Basic</span></span>](lifetime.md)
- [<span data-ttu-id="8a54d-139">Visual Basic 中的访问级别</span><span class="sxs-lookup"><span data-stu-id="8a54d-139">Access levels in Visual Basic</span></span>](access-levels.md)
- [<span data-ttu-id="8a54d-140">变量</span><span class="sxs-lookup"><span data-stu-id="8a54d-140">Variables</span></span>](../variables/index.md)
- [<span data-ttu-id="8a54d-141">变量声明</span><span class="sxs-lookup"><span data-stu-id="8a54d-141">Variable Declaration</span></span>](../variables/variable-declaration.md)
- [<span data-ttu-id="8a54d-142">Dim 语句</span><span class="sxs-lookup"><span data-stu-id="8a54d-142">Dim Statement</span></span>](../../../language-reference/statements/dim-statement.md)
