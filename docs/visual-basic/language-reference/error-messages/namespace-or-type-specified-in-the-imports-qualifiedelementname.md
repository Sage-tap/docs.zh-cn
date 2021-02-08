---
description: 了解有关以下内容的详细信息： BC40056：导入 "" 中指定的命名空间或类型 <qualifiedelementname> 不包含任何公共成员或找不到
title: Imports“<qualifiedelementname>”中指定的命名空间或类型不包含任何公共成员，或者找不到该命名空间或类型
ms.date: 07/20/2015
f1_keywords:
- bc40056
- vbc40056
helpviewer_keywords:
- BC40056
ms.assetid: b59f5754-444f-4378-9272-9678b437e84a
ms.openlocfilehash: e98ba70660823196e763300cd33ec1ba9a9db3b4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795698"
---
# <a name="bc40056-namespace-or-type-specified-in-the-imports-qualifiedelementname-doesnt-contain-any-public-member-or-cannot-be-found"></a><span data-ttu-id="7049b-103">BC40056：在导入 "" 中指定的命名空间或类型 \<qualifiedelementname> 不包含任何公共成员，或者找不到该命名空间或类型</span><span class="sxs-lookup"><span data-stu-id="7049b-103">BC40056: Namespace or type specified in the Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found</span></span>

<span data-ttu-id="7049b-104">导入 "" 中指定的命名空间或类型 \<qualifiedelementname> 不包含任何公共成员或找不到该命名空间或类型。</span><span class="sxs-lookup"><span data-stu-id="7049b-104">Namespace or type specified in the Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found.</span></span> <span data-ttu-id="7049b-105">请确保定义命名空间或类型，并且至少包含一个公共成员。</span><span class="sxs-lookup"><span data-stu-id="7049b-105">Make sure the namespace or the type is defined and contains at least one public member.</span></span> <span data-ttu-id="7049b-106">请确保别名不包含其他别名。</span><span class="sxs-lookup"><span data-stu-id="7049b-106">Make sure the alias name doesn't contain other aliases.</span></span>

<span data-ttu-id="7049b-107">`Imports`语句指定了一个包含元素，该元素无法找到或未定义任何 `Public` 成员。</span><span class="sxs-lookup"><span data-stu-id="7049b-107">An `Imports` statement specifies a containing element that either cannot be found or does not define any `Public` members.</span></span>

<span data-ttu-id="7049b-108">*包含元素* 可以是命名空间、类、结构、模块、接口或枚举。</span><span class="sxs-lookup"><span data-stu-id="7049b-108">A *containing element* can be a namespace, class, structure, module, interface, or enumeration.</span></span> <span data-ttu-id="7049b-109">包含元素包含变量、过程或其他包含元素等成员。</span><span class="sxs-lookup"><span data-stu-id="7049b-109">The containing element contains members, such as variables, procedures, or other containing elements.</span></span>

<span data-ttu-id="7049b-110">导入的目的是允许你的代码访问命名空间或类型成员，而无需对其进行限定。</span><span class="sxs-lookup"><span data-stu-id="7049b-110">The purpose of importing is to allow your code to access namespace or type members without having to qualify them.</span></span> <span data-ttu-id="7049b-111">你的项目可能还需要添加对命名空间或类型的引用。</span><span class="sxs-lookup"><span data-stu-id="7049b-111">Your project might also need to add a reference to the namespace or type.</span></span> <span data-ttu-id="7049b-112">有关详细信息，请参阅对已 [声明元素的引用](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)中的 "导入包含元素"。</span><span class="sxs-lookup"><span data-stu-id="7049b-112">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

<span data-ttu-id="7049b-113">如果编译器找不到指定的包含元素，则它无法解析使用它的引用。</span><span class="sxs-lookup"><span data-stu-id="7049b-113">If the compiler cannot find the specified containing element, then it cannot resolve references that use it.</span></span> <span data-ttu-id="7049b-114">如果找到元素但元素未公开任何 `Public` 成员，则不会成功进行引用。</span><span class="sxs-lookup"><span data-stu-id="7049b-114">If it finds the element but the element does not expose any `Public` members, then no reference can be successful.</span></span> <span data-ttu-id="7049b-115">在这两种情况下，导入元素是毫无意义的。</span><span class="sxs-lookup"><span data-stu-id="7049b-115">In either case it is meaningless to import the element.</span></span>

<span data-ttu-id="7049b-116">请记住，如果导入包含元素并为其分配了导入别名，则不能使用该导入别名导入另一个元素。</span><span class="sxs-lookup"><span data-stu-id="7049b-116">Keep in mind that if you import a containing element and assign an import alias to it, then you cannot use that import alias to import another element.</span></span> <span data-ttu-id="7049b-117">下面的代码生成编译器错误。</span><span class="sxs-lookup"><span data-stu-id="7049b-117">The following code generates a compiler error.</span></span>

```vb
Imports winfrm = System.Windows.Forms

' The following statement is INVALID  because it reuses an import alias.

Imports behave = winfrm.Design.Behavior`
```

<span data-ttu-id="7049b-118">**错误 ID：** BC40056</span><span class="sxs-lookup"><span data-stu-id="7049b-118">**Error ID:** BC40056</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="7049b-119">更正此错误</span><span class="sxs-lookup"><span data-stu-id="7049b-119">To correct this error</span></span>

1. <span data-ttu-id="7049b-120">验证是否可从你的项目访问包含元素。</span><span class="sxs-lookup"><span data-stu-id="7049b-120">Verify that the containing element is accessible from your project.</span></span>

2. <span data-ttu-id="7049b-121">验证包含元素的规范是否不包括来自其他导入的任何导入别名。</span><span class="sxs-lookup"><span data-stu-id="7049b-121">Verify that the specification of the containing element does not include any import alias from another import.</span></span>

3. <span data-ttu-id="7049b-122">验证包含元素是否至少公开一个 `Public` 成员。</span><span class="sxs-lookup"><span data-stu-id="7049b-122">Verify that the containing element exposes at least one `Public` member.</span></span>

## <a name="see-also"></a><span data-ttu-id="7049b-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="7049b-123">See also</span></span>

- [<span data-ttu-id="7049b-124">Imports 语句（.NET 命名空间和类型）</span><span class="sxs-lookup"><span data-stu-id="7049b-124">Imports Statement (.NET Namespace and Type)</span></span>](../statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="7049b-125">Namespace 语句</span><span class="sxs-lookup"><span data-stu-id="7049b-125">Namespace Statement</span></span>](../statements/namespace-statement.md)
- [<span data-ttu-id="7049b-126">公共</span><span class="sxs-lookup"><span data-stu-id="7049b-126">Public</span></span>](../modifiers/public.md)
- [<span data-ttu-id="7049b-127">Visual Basic 中的命名空间</span><span class="sxs-lookup"><span data-stu-id="7049b-127">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="7049b-128">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="7049b-128">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
