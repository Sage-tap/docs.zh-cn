---
description: 了解详细信息： BC30955：无法将类型为 "" 的值 <typename1> 转换为 " <typename2> "
title: 类型“<typename1>”的值无法转换为“<typename2>”
ms.date: 07/20/2015
f1_keywords:
- vbc30955
- bc30955
helpviewer_keywords:
- BC30955
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
ms.openlocfilehash: a013e274a1776dee6a98add63138236ad11111b8
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100426551"
---
# <a name="bc30955-value-of-type-typename1-cannot-be-converted-to-typename2"></a><span data-ttu-id="27b40-103">BC30955：无法将类型 " \<typename1> " 的值转换为 " \<typename2> "</span><span class="sxs-lookup"><span data-stu-id="27b40-103">BC30955: Value of type '\<typename1>' cannot be converted to '\<typename2>'</span></span>

<span data-ttu-id="27b40-104">类型 "" 的值 \<typename1> 无法转换为 " \<typename2> "。</span><span class="sxs-lookup"><span data-stu-id="27b40-104">Value of type '\<typename1>' cannot be converted to '\<typename2>'.</span></span> <span data-ttu-id="27b40-105">类型不匹配可能是由于将文件引用与程序集 "" 的项目引用混合而造成的 \<assemblyname> 。</span><span class="sxs-lookup"><span data-stu-id="27b40-105">Type mismatch could be due to the mixing of a file reference with a project reference to assembly '\<assemblyname>'.</span></span> <span data-ttu-id="27b40-106">尝试将对项目 "" 中 "" 的文件引用替换为 \<filepath> \<projectname1> 对 "" 的项目引用 \<projectname2> 。</span><span class="sxs-lookup"><span data-stu-id="27b40-106">Try replacing the file reference to '\<filepath>' in project '\<projectname1>' with a project reference to '\<projectname2>'.</span></span>

 <span data-ttu-id="27b40-107">在项目同时进行项目引用和文件引用的情况下，编译器无法保证可以将一种类型转换为另一种类型。</span><span class="sxs-lookup"><span data-stu-id="27b40-107">In a situation where a project makes both a project reference and a file reference, the compiler cannot guarantee that one type can be converted to another.</span></span>

 <span data-ttu-id="27b40-108">下面的伪代码说明了可能生成此错误的情况。</span><span class="sxs-lookup"><span data-stu-id="27b40-108">The following pseudo-code illustrates a situation that can generate this error.</span></span>

 `' ================ Visual Basic project P1 ================`

 `'        P1 makes a PROJECT REFERENCE to project P2`

 `'        and a FILE REFERENCE to project P3.`

 `Public commonObject As P3.commonClass`

 `commonObject = P2.getCommonClass()`

 `' ================ Visual Basic project P2 ================`

 `'        P2 makes a PROJECT REFERENCE to project P3`

 `Public Function getCommonClass() As P3.commonClass`

 `Return New P3.commonClass`

 `End Function`

 `' ================ Visual Basic project P3 ================`

 `Public Class commonClass`

 `End Class`

 <span data-ttu-id="27b40-109">项目 `P1` 通过项目进行间接项目引用 `P2` `P3` ，并对进行直接文件引用 `P3` 。</span><span class="sxs-lookup"><span data-stu-id="27b40-109">Project `P1` makes an indirect project reference through project `P2` to project `P3`, and also a direct file reference to `P3`.</span></span> <span data-ttu-id="27b40-110">的声明 `commonObject` 使用对的文件引用 `P3` ，而对的调用 `P2.getCommonClass` 使用对的项目引用 `P3` 。</span><span class="sxs-lookup"><span data-stu-id="27b40-110">The declaration of `commonObject` uses the file reference to `P3`, while the call to `P2.getCommonClass` uses the project reference to `P3`.</span></span>

 <span data-ttu-id="27b40-111">出现这种情况的问题是，文件引用指定了 (的输出文件的文件路径和名称 `P3` （通常 p3.dll) ），而项目引用则 `P3` 按项目名称 () 标识源项目。</span><span class="sxs-lookup"><span data-stu-id="27b40-111">The problem in this situation is that the file reference specifies a file path and name for the output file of `P3` (typically p3.dll), while the project references identify the source project (`P3`) by project name.</span></span> <span data-ttu-id="27b40-112">因此，编译器无法 `P3.commonClass` 通过两个不同的引用来保证该类型来自相同的源代码。</span><span class="sxs-lookup"><span data-stu-id="27b40-112">Because of this, the compiler cannot guarantee that the type `P3.commonClass` comes from the same source code through the two different references.</span></span>

 <span data-ttu-id="27b40-113">当项目引用和文件引用混合时，通常会发生这种情况。</span><span class="sxs-lookup"><span data-stu-id="27b40-113">This situation typically occurs when project references and file references are mixed.</span></span> <span data-ttu-id="27b40-114">在上图中，如果 `P1` 直接引用项目 `P3` 而不是文件引用，则不会出现此问题。</span><span class="sxs-lookup"><span data-stu-id="27b40-114">In the preceding illustration, the problem would not occur if `P1` made a direct project reference to `P3` instead of a file reference.</span></span>

 <span data-ttu-id="27b40-115">**错误 ID：** BC30955</span><span class="sxs-lookup"><span data-stu-id="27b40-115">**Error ID:** BC30955</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="27b40-116">更正此错误</span><span class="sxs-lookup"><span data-stu-id="27b40-116">To correct this error</span></span>

- <span data-ttu-id="27b40-117">更改对项目引用的文件引用。</span><span class="sxs-lookup"><span data-stu-id="27b40-117">Change the file reference to a project reference.</span></span>

## <a name="see-also"></a><span data-ttu-id="27b40-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="27b40-118">See also</span></span>

- [<span data-ttu-id="27b40-119">Visual Basic 中的类型转换</span><span class="sxs-lookup"><span data-stu-id="27b40-119">Type Conversions in Visual Basic</span></span>](../../programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="27b40-120">管理项目中的引用</span><span class="sxs-lookup"><span data-stu-id="27b40-120">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
