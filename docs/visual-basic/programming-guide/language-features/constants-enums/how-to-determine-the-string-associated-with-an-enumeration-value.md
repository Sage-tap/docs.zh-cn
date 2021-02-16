---
description: '了解有关详细信息，请参阅如何：确定与枚举值关联的字符串 (Visual Basic) '
title: 如何：确定与枚举值关联的字符串
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- strings [Visual Basic], enumeration values
- values [Visual Basic], enumeration members
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
ms.openlocfilehash: 391cb097fa8163f7131cc30f85f8a4f85ba826a4
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100471599"
---
# <a name="how-to-determine-the-string-associated-with-an-enumeration-value-visual-basic"></a><span data-ttu-id="08b9f-103">如何：确定与枚举值关联的字符串 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="08b9f-103">How to: Determine the String Associated with an Enumeration Value (Visual Basic)</span></span>

<span data-ttu-id="08b9f-104"><xref:System.Enum.GetValues%2A>和 <xref:System.Enum.GetNames%2A> 方法允许您确定与枚举成员关联的字符串和值。</span><span class="sxs-lookup"><span data-stu-id="08b9f-104">The <xref:System.Enum.GetValues%2A> and <xref:System.Enum.GetNames%2A> methods allow you to determine the strings and values associated with enumeration members.</span></span>  
  
### <a name="to-determine-the-string-associated-with-an-enumeration"></a><span data-ttu-id="08b9f-105">确定与枚举关联的字符串</span><span class="sxs-lookup"><span data-stu-id="08b9f-105">To determine the string associated with an enumeration</span></span>  
  
- <span data-ttu-id="08b9f-106">使用 <xref:System.Enum.GetNames%2A> 方法检索与枚举成员关联的字符串。</span><span class="sxs-lookup"><span data-stu-id="08b9f-106">Use the <xref:System.Enum.GetNames%2A> method to retrieve the strings associated with the enumeration members.</span></span> <span data-ttu-id="08b9f-107">此示例声明一个枚举， `flavorEnum` 然后使用 <xref:System.Enum.GetNames%2A> 方法显示与每个成员关联的字符串。</span><span class="sxs-lookup"><span data-stu-id="08b9f-107">This example declares an enumeration, `flavorEnum`, then uses the <xref:System.Enum.GetNames%2A> method to display the strings associated with each member.</span></span>  
  
     [!code-vb[VbEnumsTask#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="08b9f-108">请参阅</span><span class="sxs-lookup"><span data-stu-id="08b9f-108">See also</span></span>

- <xref:System.Enum.GetValues%2A>
- <xref:System.Enum.GetNames%2A>
- <xref:System.Enum>
- [<span data-ttu-id="08b9f-109">如何：声明枚举</span><span class="sxs-lookup"><span data-stu-id="08b9f-109">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="08b9f-110">如何：引用枚举成员</span><span class="sxs-lookup"><span data-stu-id="08b9f-110">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="08b9f-111">枚举和名称限定</span><span class="sxs-lookup"><span data-stu-id="08b9f-111">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="08b9f-112">如何：在 Visual Basic 中循环访问枚举</span><span class="sxs-lookup"><span data-stu-id="08b9f-112">How to: Iterate Through An Enumeration in Visual Basic</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="08b9f-113">何时使用枚举</span><span class="sxs-lookup"><span data-stu-id="08b9f-113">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
- [<span data-ttu-id="08b9f-114">Enum 语句</span><span class="sxs-lookup"><span data-stu-id="08b9f-114">Enum Statement</span></span>](../../../language-reference/statements/enum-statement.md)
