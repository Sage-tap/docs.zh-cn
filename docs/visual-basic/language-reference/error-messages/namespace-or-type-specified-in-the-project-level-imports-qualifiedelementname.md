---
description: 了解有关以下内容的详细信息： BC40057：在项目级 Imports "" 中指定的命名空间或类型 <qualifiedelementname> 不包含任何公共成员或找不到
title: 在项目级 Imports“<qualifiedelementname>”中指定的命名空间或类型不包含任何公共成员，或者找不到该命名空间或类型
ms.date: 07/20/2015
f1_keywords:
- vbc40057
- bc40057
helpviewer_keywords:
- BC40057
ms.assetid: 4ae3506e-2ebe-4ff3-995d-14ac60db5e9f
ms.openlocfilehash: 66ae40ca6a2feff78f80bdbc8886387e801f7db2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795685"
---
# <a name="bc40057-namespace-or-type-specified-in-the-project-level-imports-qualifiedelementname-doesnt-contain-any-public-member-or-cannot-be-found"></a><span data-ttu-id="b2f26-103">BC40057：在项目级 Imports "" 中指定的命名空间或类型 \<qualifiedelementname> 不包含任何公共成员，或者找不到该命名空间或类型</span><span class="sxs-lookup"><span data-stu-id="b2f26-103">BC40057: Namespace or type specified in the project-level Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found</span></span>

<span data-ttu-id="b2f26-104">项目级 Imports "" 中指定的命名空间或类型 \<qualifiedelementname> 不包含任何公共成员，或者找不到该命名空间或类型。</span><span class="sxs-lookup"><span data-stu-id="b2f26-104">Namespace or type specified in the project-level Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found.</span></span> <span data-ttu-id="b2f26-105">请确保定义命名空间或类型，并且至少包含一个公共成员。</span><span class="sxs-lookup"><span data-stu-id="b2f26-105">Make sure the namespace or the type is defined and contains at least one public member.</span></span> <span data-ttu-id="b2f26-106">请确保别名不包含其他别名。</span><span class="sxs-lookup"><span data-stu-id="b2f26-106">Make sure the alias name doesn't contain other aliases.</span></span>

 <span data-ttu-id="b2f26-107">项目的导入属性指定的包含元素无法找到或未定义任何 `Public` 成员。</span><span class="sxs-lookup"><span data-stu-id="b2f26-107">An import property of a project specifies a containing element that either cannot be found or does not define any `Public` members.</span></span>

 <span data-ttu-id="b2f26-108">*包含元素* 可以是命名空间、类、结构、模块、接口或枚举。</span><span class="sxs-lookup"><span data-stu-id="b2f26-108">A *containing element* can be a namespace, class, structure, module, interface, or enumeration.</span></span> <span data-ttu-id="b2f26-109">包含元素包含变量、过程或其他包含元素等成员。</span><span class="sxs-lookup"><span data-stu-id="b2f26-109">The containing element contains members, such as variables, procedures, or other containing elements.</span></span>

 <span data-ttu-id="b2f26-110">导入的目的是允许你的代码访问命名空间或类型成员，而无需对其进行限定。</span><span class="sxs-lookup"><span data-stu-id="b2f26-110">The purpose of importing is to allow your code to access namespace or type members without having to qualify them.</span></span> <span data-ttu-id="b2f26-111">你的项目可能还需要添加对命名空间或类型的引用。</span><span class="sxs-lookup"><span data-stu-id="b2f26-111">Your project might also need to add a reference to the namespace or type.</span></span> <span data-ttu-id="b2f26-112">有关详细信息，请参阅对已 [声明元素的引用](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)中的 "导入包含元素"。</span><span class="sxs-lookup"><span data-stu-id="b2f26-112">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

 <span data-ttu-id="b2f26-113">如果编译器找不到指定的包含元素，则它无法解析使用它的引用。</span><span class="sxs-lookup"><span data-stu-id="b2f26-113">If the compiler cannot find the specified containing element, then it cannot resolve references that use it.</span></span> <span data-ttu-id="b2f26-114">如果找到元素但元素未公开任何 `Public` 成员，则不会成功进行引用。</span><span class="sxs-lookup"><span data-stu-id="b2f26-114">If it finds the element but the element does not expose any `Public` members, then no reference can be successful.</span></span> <span data-ttu-id="b2f26-115">在这两种情况下，导入元素是毫无意义的。</span><span class="sxs-lookup"><span data-stu-id="b2f26-115">In either case it is meaningless to import the element.</span></span>

 <span data-ttu-id="b2f26-116">使用 " **项目设计器** " 可以指定要导入的元素。</span><span class="sxs-lookup"><span data-stu-id="b2f26-116">You use the **Project Designer** to specify elements to import.</span></span> <span data-ttu-id="b2f26-117">使用 "**引用**" 页的 "**导入的命名空间**" 部分。</span><span class="sxs-lookup"><span data-stu-id="b2f26-117">Use the **Imported namespaces** section of the **References** page.</span></span> <span data-ttu-id="b2f26-118">可以通过双击 "**解决方案资源管理器** 中的 **" 我的项目**"图标来转到"**项目设计器**"。</span><span class="sxs-lookup"><span data-stu-id="b2f26-118">You can get to the **Project Designer** by double-clicking the **My Project** icon in **Solution Explorer**.</span></span>

 <span data-ttu-id="b2f26-119">**错误 ID：** BC40057</span><span class="sxs-lookup"><span data-stu-id="b2f26-119">**Error ID:** BC40057</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="b2f26-120">更正此错误</span><span class="sxs-lookup"><span data-stu-id="b2f26-120">To correct this error</span></span>

1. <span data-ttu-id="b2f26-121">打开 " **项目设计器** "，并切换到 " **引用** " 页。</span><span class="sxs-lookup"><span data-stu-id="b2f26-121">Open the **Project Designer** and switch to the **Reference** page.</span></span>

2. <span data-ttu-id="b2f26-122">在 " **导入的命名空间** " 部分中，验证是否可以从项目访问包含元素。</span><span class="sxs-lookup"><span data-stu-id="b2f26-122">In the **Imported namespaces** section, verify that the containing element is accessible from your project.</span></span>

3. <span data-ttu-id="b2f26-123">验证包含元素是否至少公开一个 `Public` 成员。</span><span class="sxs-lookup"><span data-stu-id="b2f26-123">Verify that the containing element exposes at least one `Public` member.</span></span>

## <a name="see-also"></a><span data-ttu-id="b2f26-124">请参阅</span><span class="sxs-lookup"><span data-stu-id="b2f26-124">See also</span></span>

- [<span data-ttu-id="b2f26-125">项目设计器 -&gt;“引用”页 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b2f26-125">References Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/references-page-project-designer-visual-basic)
- [<span data-ttu-id="b2f26-126">管理项目和解决方案属性</span><span class="sxs-lookup"><span data-stu-id="b2f26-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="b2f26-127">公共</span><span class="sxs-lookup"><span data-stu-id="b2f26-127">Public</span></span>](../modifiers/public.md)
- [<span data-ttu-id="b2f26-128">Visual Basic 中的命名空间</span><span class="sxs-lookup"><span data-stu-id="b2f26-128">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="b2f26-129">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="b2f26-129">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
