---
description: '了解详细信息： Visual Basic (声明的元素名称) '
title: Declared Element Names
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic], case sensitivity
- names [Visual Basic], Visual Basic rules
- naming conventions [Visual Basic]
- element names [Visual Basic]
- declared elements [Visual Basic], identifiers
- declarations [Visual Basic], elements
- declared elements [Visual Basic], valid names
- '[] escape characters [Visual Basic]'
- names [Visual Basic], elements
- declaration statements [Visual Basic], declared elements
- declaring elements [Visual Basic]
- identifiers [Visual Basic], declared elements
- case sensitivity, declared element names
- escape characters [Visual Basic]
- names [Visual Basic], declared elements
- declared elements [Visual Basic], about declared elements
- escaped names [Visual Basic]
- declared elements [Visual Basic], names
- names [Visual Basic], naming conventions
- identifiers [Visual Basic], elements
ms.assetid: 09d8843b-c0dc-4afe-9dab-87c439a69e66
ms.openlocfilehash: ba0a6d6b236c0c4e9ce81c37a1cca4e709cc5588
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100425680"
---
# <a name="declared-element-names-visual-basic"></a><span data-ttu-id="1e465-103">已声明的元素名称 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e465-103">Declared Element Names (Visual Basic)</span></span>

<span data-ttu-id="1e465-104">每个已声明的元素都有一个名称，也称为 *标识符*，代码使用该名称来引用它。</span><span class="sxs-lookup"><span data-stu-id="1e465-104">Every declared element has a name, also called an *identifier*, which is what the code uses to refer to it.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="1e465-105">规则</span><span class="sxs-lookup"><span data-stu-id="1e465-105">Rules</span></span>  

 <span data-ttu-id="1e465-106">Visual Basic 中的元素名称必须遵循以下规则：</span><span class="sxs-lookup"><span data-stu-id="1e465-106">An element name in Visual Basic must observe the following rules:</span></span>  
  
- <span data-ttu-id="1e465-107">它必须以字母字符或下划线开头 (`_`) 。</span><span class="sxs-lookup"><span data-stu-id="1e465-107">It must begin with an alphabetic character or an underscore (`_`).</span></span>  
  
- <span data-ttu-id="1e465-108">它只能包含字母字符、十进制数字和下划线。</span><span class="sxs-lookup"><span data-stu-id="1e465-108">It must only contain alphabetic characters, decimal digits, and underscores.</span></span>  
  
- <span data-ttu-id="1e465-109">它必须至少包含一个字母字符或十进制数（如果以下划线开头）。</span><span class="sxs-lookup"><span data-stu-id="1e465-109">It must contain at least one alphabetic character or decimal digit if it begins with an underscore.</span></span>  
  
- <span data-ttu-id="1e465-110">长度不得超过1023个字符。</span><span class="sxs-lookup"><span data-stu-id="1e465-110">It must not be more than 1023 characters long.</span></span>  
  
 <span data-ttu-id="1e465-111">1023字符的长度限制还适用于完全限定名称（如）的整个字符串 `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement` 。</span><span class="sxs-lookup"><span data-stu-id="1e465-111">The length limit of 1023 characters also applies to the entire string of a fully qualified name, such as `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.</span></span>  
  
 <span data-ttu-id="1e465-112">下面的示例显示了一些有效的元素名称。</span><span class="sxs-lookup"><span data-stu-id="1e465-112">The following example shows some valid element names.</span></span>  
  
 `aB123__45`  
  
 `_567`  
  
 <span data-ttu-id="1e465-113">下面的示例显示一些无效的元素名称。</span><span class="sxs-lookup"><span data-stu-id="1e465-113">The following example shows some invalid element names.</span></span> <span data-ttu-id="1e465-114">第一个仅包含下划线，第二个以十进制数字开头，第三个包含无效字符 ($) 。</span><span class="sxs-lookup"><span data-stu-id="1e465-114">The first contains only an underscore, the second begins with a decimal digit, and the third contains an invalid character ($).</span></span>  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
> <span data-ttu-id="1e465-115">以下划线 () 开头的元素名称 `_` 不是 [语言独立性的一部分，Language-Independent 组件](../../../../standard/language-independence-and-language-independent-components.md) (cls) ，因此符合 cls 的代码不能使用定义此类名称的组件。</span><span class="sxs-lookup"><span data-stu-id="1e465-115">Element names starting with an underscore (`_`) are not part of the [Language Independence and Language-Independent Components](../../../../standard/language-independence-and-language-independent-components.md) (CLS), so CLS-compliant code cannot use a component that defines such names.</span></span> <span data-ttu-id="1e465-116">但元素名称中任何其他位置的下划线都符合 CLS。</span><span class="sxs-lookup"><span data-stu-id="1e465-116">However, an underscore in any other position in an element name is CLS-compliant.</span></span>  
  
### <a name="name-length-guidelines"></a><span data-ttu-id="1e465-117">名称长度准则</span><span class="sxs-lookup"><span data-stu-id="1e465-117">Name Length Guidelines</span></span>  

 <span data-ttu-id="1e465-118">在实际情况下，你的名称应尽可能简短，同时仍能清楚地确定元素的性质。</span><span class="sxs-lookup"><span data-stu-id="1e465-118">As a practical matter, your name should be as short as possible while still clearly identifying the nature of the element.</span></span> <span data-ttu-id="1e465-119">这可以提高代码的可读性，并减少行长度和源文件大小。</span><span class="sxs-lookup"><span data-stu-id="1e465-119">This improves the readability of your code and reduces line length and source-file size.</span></span>  
  
 <span data-ttu-id="1e465-120">另一方面，你的名称不应太短，因为它没有充分描述元素所表示的内容以及你的代码如何使用它。</span><span class="sxs-lookup"><span data-stu-id="1e465-120">On the other hand, your name should not be so short that it does not adequately describe what the element represents and how your code uses it.</span></span> <span data-ttu-id="1e465-121">这对于代码的可读性非常重要。</span><span class="sxs-lookup"><span data-stu-id="1e465-121">This is important for the readability of your code.</span></span> <span data-ttu-id="1e465-122">如果其他人正在尝试理解它，或者你在写入它后你需要很长的时间，则适当的元素名称可以节省相当多的时间。</span><span class="sxs-lookup"><span data-stu-id="1e465-122">If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, suitable element names can save a considerable amount of time.</span></span>  
  
## <a name="escaped-names"></a><span data-ttu-id="1e465-123">转义名称</span><span class="sxs-lookup"><span data-stu-id="1e465-123">Escaped Names</span></span>  

 <span data-ttu-id="1e465-124">通常，元素名称不能与 Visual Basic 保留的任何关键字（如或）匹配 `Case` `Friend` 。</span><span class="sxs-lookup"><span data-stu-id="1e465-124">Generally, an element name must not match any of the keywords reserved by Visual Basic, such as `Case` or `Friend`.</span></span> <span data-ttu-id="1e465-125">但是，您可以定义一个 *转义名称*，该名称由方括号 () 括起来 `[ ]` 。</span><span class="sxs-lookup"><span data-stu-id="1e465-125">However, you can define an *escaped name*, which is enclosed by brackets (`[ ]`).</span></span> <span data-ttu-id="1e465-126">转义名称可以匹配任何 Visual Basic 关键字，因为方括号会删除任何不明确的名称。</span><span class="sxs-lookup"><span data-stu-id="1e465-126">An escaped name can match any Visual Basic keyword, since the brackets remove any ambiguity.</span></span> <span data-ttu-id="1e465-127">稍后在代码中引用名称时也会用到方括号。</span><span class="sxs-lookup"><span data-stu-id="1e465-127">You also use the brackets when you refer to the name later in your code.</span></span>  
  
 <span data-ttu-id="1e465-128">通常，仅当以下情况下，才应使用转义名称：</span><span class="sxs-lookup"><span data-stu-id="1e465-128">In general, you should use escaped names only when:</span></span>  
  
- <span data-ttu-id="1e465-129">你的代码已从以前版本的 Visual Basic 迁移，此版本未保留用作名称的关键字;或</span><span class="sxs-lookup"><span data-stu-id="1e465-129">Your code has migrated from a previous version of Visual Basic that did not reserve the keyword being used as a name; or</span></span>  
  
- <span data-ttu-id="1e465-130">你使用的是以另一种语言编写的代码，但给定的关键字不是保留关键字。</span><span class="sxs-lookup"><span data-stu-id="1e465-130">You are working with code written in another language in which the given keyword is not reserved.</span></span>  
  
 <span data-ttu-id="1e465-131">否则，如果元素的名称与关键字冲突，则应考虑重命名该元素。</span><span class="sxs-lookup"><span data-stu-id="1e465-131">Otherwise, you should consider renaming the element if its name conflicts with a keyword.</span></span> <span data-ttu-id="1e465-132">集成开发环境 (IDE) 提供一种简单的方法来实现此目的。</span><span class="sxs-lookup"><span data-stu-id="1e465-132">The integrated development environment (IDE) provides an easy way to do this.</span></span> <span data-ttu-id="1e465-133">有关详细信息，请参阅 [重构](/visualstudio/ide/refactoring-in-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="1e465-133">For more information, see [Refactoring](/visualstudio/ide/refactoring-in-visual-studio).</span></span>  
  
## <a name="case-sensitivity-in-names"></a><span data-ttu-id="1e465-134">名称区分大小写</span><span class="sxs-lookup"><span data-stu-id="1e465-134">Case Sensitivity in Names</span></span>  

 <span data-ttu-id="1e465-135">Visual Basic 中的元素名称不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="1e465-135">Element names in Visual Basic are case-insensitive.</span></span> <span data-ttu-id="1e465-136">这意味着当编译器仅对字母大小写不同的两个名称进行比较时，它会将它们解释为同一名称。</span><span class="sxs-lookup"><span data-stu-id="1e465-136">This means that when the compiler compares two names that differ in alphabetic case only, it interprets them as the same name.</span></span> <span data-ttu-id="1e465-137">例如，它认为 `ABC` 和 `abc` 指的是同一个声明的元素。</span><span class="sxs-lookup"><span data-stu-id="1e465-137">For example, it considers `ABC` and `abc` to refer to the same declared element.</span></span>  
  
 <span data-ttu-id="1e465-138">但是，公共语言运行时 (CLR) 使用区分大小写绑定。</span><span class="sxs-lookup"><span data-stu-id="1e465-138">However, the common language runtime (CLR) uses case-sensitive binding.</span></span> <span data-ttu-id="1e465-139">因此，当你生成程序集或 DLL 并使其可供其他程序集使用时，则名称将不再不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="1e465-139">Therefore, when you produce an assembly or a DLL and make it available to other assemblies, your names are no longer case-insensitive.</span></span> <span data-ttu-id="1e465-140">例如，如果你用名为 `ABC`的元素定义类，而其他程序集通过公共语言运行时使用你的类，则元素必须指的是 `ABC`。</span><span class="sxs-lookup"><span data-stu-id="1e465-140">For example, if you define a class with an element called `ABC`, and other assemblies make use of your class through the common language runtime, they must refer to the element as `ABC`.</span></span> <span data-ttu-id="1e465-141">如果随后重新编译类并将元素名称更改为 `abc` ，则使用类的其他程序集将无法再访问该元素。</span><span class="sxs-lookup"><span data-stu-id="1e465-141">If you subsequently recompile your class and change the element's name to `abc`, the other assemblies using your class could no longer access that element.</span></span> <span data-ttu-id="1e465-142">因此，发布程序集的更新版本时，不应该更改公共元素的字母大小写。</span><span class="sxs-lookup"><span data-stu-id="1e465-142">Therefore, when you release an updated version of an assembly, you should not change the alphabetic case of any public elements.</span></span>  
  
## <a name="names-and-locales"></a><span data-ttu-id="1e465-143">名称和区域设置</span><span class="sxs-lookup"><span data-stu-id="1e465-143">Names and Locales</span></span>  

 <span data-ttu-id="1e465-144">名称比较与区域设置无关。</span><span class="sxs-lookup"><span data-stu-id="1e465-144">Comparison of names is independent of locale.</span></span> <span data-ttu-id="1e465-145">如果两个名称在一个区域设置中匹配，则保证它们在所有区域设置中匹配。</span><span class="sxs-lookup"><span data-stu-id="1e465-145">If two names match in one locale, they are guaranteed to match in all locales.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e465-146">请参阅</span><span class="sxs-lookup"><span data-stu-id="1e465-146">See also</span></span>

- [<span data-ttu-id="1e465-147">已声明的元素</span><span class="sxs-lookup"><span data-stu-id="1e465-147">Declared Elements</span></span>](index.md)
- [<span data-ttu-id="1e465-148">已声明元素的特性</span><span class="sxs-lookup"><span data-stu-id="1e465-148">Declared Element Characteristics</span></span>](declared-element-characteristics.md)
- [<span data-ttu-id="1e465-149">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="1e465-149">References to Declared Elements</span></span>](references-to-declared-elements.md)
- [<span data-ttu-id="1e465-150">语句</span><span class="sxs-lookup"><span data-stu-id="1e465-150">Statements</span></span>](../../../language-reference/statements/index.md)
