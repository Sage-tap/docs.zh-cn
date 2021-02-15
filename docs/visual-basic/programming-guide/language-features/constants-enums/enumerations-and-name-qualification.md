---
description: '了解详细信息： (Visual Basic 的枚举和名称限定) '
title: 枚举和名称限定
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- Imports statement [Visual Basic], namespace declarations
- declaring namespaces [Visual Basic], enumerations
- name collisions
- ambiguous names [Visual Basic], enumerations
- enumerations [Visual Basic], name qualification
- names [Visual Basic], avoiding conflicts
- namespaces [Visual Basic], declaring
- naming conflicts, enumerations
- naming conflicts, qualifying names
- declaring enumerations
- references [Visual Basic], enumeration members
- naming conventions [Visual Basic], naming conflicts
- declarations [Visual Basic], namespaces
ms.assetid: 08ba2738-df52-4140-bc55-f57c871c9b73
ms.openlocfilehash: 83f5b894dad821fea920386be905de0b51f9c42f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100477471"
---
# <a name="enumerations-and-name-qualification-visual-basic"></a><span data-ttu-id="eae02-103">枚举和名称限定 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eae02-103">Enumerations and Name Qualification (Visual Basic)</span></span>

<span data-ttu-id="eae02-104">通常，在引用枚举成员时，必须使用枚举名称限定成员名称。</span><span class="sxs-lookup"><span data-stu-id="eae02-104">Normally, when referring to a member of an enumeration, you must qualify the member name with the enumeration name.</span></span> <span data-ttu-id="eae02-105">例如，若要引用枚举的 `Sunday` 成员 `Days` ，请使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="eae02-105">For example, to refer to the `Sunday` member of your `Days` enumeration, you would use the following syntax:</span></span>  
  
 [!code-vb[VbEnumsTask#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#18)]  
  
## <a name="using-the-imports-statement"></a><span data-ttu-id="eae02-106">使用 Imports 语句</span><span class="sxs-lookup"><span data-stu-id="eae02-106">Using the Imports Statement</span></span>  

 <span data-ttu-id="eae02-107">可以通过将 `Imports` 语句添加到代码的命名空间声明部分来避免使用完全限定的名称，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="eae02-107">You can avoid using fully qualified names by adding an `Imports` statement to the namespace declarations section of your code, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 <span data-ttu-id="eae02-108">`Imports`语句从被引用项目和程序集中导入命名空间名称，并从与该语句出现的模块相同的项目中导入命名空间名称。</span><span class="sxs-lookup"><span data-stu-id="eae02-108">An `Imports` statement imports namespace names from referenced projects and assemblies and from within the same project as the module in which the statement appears.</span></span> <span data-ttu-id="eae02-109">添加此语句后，无需限定即可引用枚举成员，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="eae02-109">Once this statement is added, you can refer to your enumeration members without qualification, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#24)]  
  
 <span data-ttu-id="eae02-110">通过组织枚举中的相关常量集，可以在不同的上下文中使用相同的常量名称。</span><span class="sxs-lookup"><span data-stu-id="eae02-110">By organizing sets of related constants in enumerations, you can use the same constant names in different contexts.</span></span> <span data-ttu-id="eae02-111">例如，可以对和枚举中的 weekday 常量使用相同的名称 `Days` `WorkDays` 。</span><span class="sxs-lookup"><span data-stu-id="eae02-111">For example, you can use the same names for the weekday constants in the `Days` and `WorkDays` enumerations.</span></span> <span data-ttu-id="eae02-112">如果对枚举使用 `Imports` 语句，则必须小心，以避免不明确的引用。</span><span class="sxs-lookup"><span data-stu-id="eae02-112">If you use the `Imports` statement with your enumerations, you must be careful to avoid ambiguous references.</span></span> <span data-ttu-id="eae02-113">请看下面的示例：</span><span class="sxs-lookup"><span data-stu-id="eae02-113">Consider the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 [!code-vb[VbEnumsTask#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#25)]  
  
 <span data-ttu-id="eae02-114">假定这 `Monday` 是 `Days` 枚举和枚举的成员 `Workdays` ，则此代码会生成编译器错误。</span><span class="sxs-lookup"><span data-stu-id="eae02-114">Assuming that `Monday` is a member of both the `Days` enumeration and the `Workdays` enumeration, this code generates a compiler error.</span></span> <span data-ttu-id="eae02-115">若要避免引用单个常量时出现不明确的引用，请使用其枚举来限定常量名称。</span><span class="sxs-lookup"><span data-stu-id="eae02-115">To avoid ambiguous references when referring to an individual constant, qualify the constant name with its enumeration.</span></span> <span data-ttu-id="eae02-116">下面的代码引用 `Saturday` 和枚举中的常量 `Days` `WorkDays` 。</span><span class="sxs-lookup"><span data-stu-id="eae02-116">The following code refers to the `Saturday` constants in the `Days` and `WorkDays` enumerations.</span></span>  
  
 [!code-vb[VbEnumsTask#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="eae02-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="eae02-117">See also</span></span>

- [<span data-ttu-id="eae02-118">常量和枚举</span><span class="sxs-lookup"><span data-stu-id="eae02-118">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
- [<span data-ttu-id="eae02-119">如何：声明枚举</span><span class="sxs-lookup"><span data-stu-id="eae02-119">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="eae02-120">如何：引用枚举成员</span><span class="sxs-lookup"><span data-stu-id="eae02-120">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="eae02-121">如何：在 Visual Basic 中循环访问枚举</span><span class="sxs-lookup"><span data-stu-id="eae02-121">How to: Iterate Through An Enumeration in Visual Basic</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="eae02-122">如何：确定与枚举值关联的字符串</span><span class="sxs-lookup"><span data-stu-id="eae02-122">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="eae02-123">何时使用枚举</span><span class="sxs-lookup"><span data-stu-id="eae02-123">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
- [<span data-ttu-id="eae02-124">常数和文本数据类型</span><span class="sxs-lookup"><span data-stu-id="eae02-124">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="eae02-125">Enum 语句</span><span class="sxs-lookup"><span data-stu-id="eae02-125">Enum Statement</span></span>](../../../language-reference/statements/enum-statement.md)
- [<span data-ttu-id="eae02-126">Imports 语句（.NET 命名空间和类型）</span><span class="sxs-lookup"><span data-stu-id="eae02-126">Imports Statement (.NET Namespace and Type)</span></span>](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="eae02-127">数据类型</span><span class="sxs-lookup"><span data-stu-id="eae02-127">Data Types</span></span>](../../../language-reference/data-types/index.md)
