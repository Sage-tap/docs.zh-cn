---
description: 详细了解：受保护的成员
title: 受保护的成员
ms.date: 10/22/2008
helpviewer_keywords:
- members [.NET Framework], protected
- protected members
- classes [.NET Framework], unsealed
- classes [.NET Framework], protected members
- unsealed classes
- customizing class behavior
ms.assetid: aa0b58ee-3956-494d-ab48-471ae5db8740
ms.openlocfilehash: 5860828a5a469c77fbee001d01460a488fda4edf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99731755"
---
# <a name="protected-members"></a><span data-ttu-id="37774-103">受保护的成员</span><span class="sxs-lookup"><span data-stu-id="37774-103">Protected Members</span></span>

<span data-ttu-id="37774-104">受保护的成员本身不提供任何扩展性，但它们可以通过子类化使扩展性更强大。</span><span class="sxs-lookup"><span data-stu-id="37774-104">Protected members by themselves do not provide any extensibility, but they can make extensibility through subclassing more powerful.</span></span> <span data-ttu-id="37774-105">它们可用于公开高级自定义选项，而不会不必要地使主公共接口复杂化。</span><span class="sxs-lookup"><span data-stu-id="37774-105">They can be used to expose advanced customization options without unnecessarily complicating the main public interface.</span></span>

 <span data-ttu-id="37774-106">框架设计者需要小心处理受保护的成员，因为名称“protected”会给人一种虚假的安全感。</span><span class="sxs-lookup"><span data-stu-id="37774-106">Framework designers need to be careful with protected members because the name "protected" can give a false sense of security.</span></span> <span data-ttu-id="37774-107">任何人都可以对非密封类进行子类化并访问受保护的成员，因此用于公共成员的所有相同的防御性编码实践都适用于受保护的成员。</span><span class="sxs-lookup"><span data-stu-id="37774-107">Anyone is able to subclass an unsealed class and access protected members, and so all the same defensive coding practices used for public members apply to protected members.</span></span>

 <span data-ttu-id="37774-108">✔️ 请考虑使用受保护的成员进行高级自定义。</span><span class="sxs-lookup"><span data-stu-id="37774-108">✔️ CONSIDER using protected members for advanced customization.</span></span>

 <span data-ttu-id="37774-109">✔️ 出于安全、文档和兼容性分析的目的，请务必将非密封类中的受保护成员视为公共成员。</span><span class="sxs-lookup"><span data-stu-id="37774-109">✔️ DO treat protected members in unsealed classes as public for the purpose of security, documentation, and compatibility analysis.</span></span>

 <span data-ttu-id="37774-110">任何人都可从类继承并访问受保护的成员。</span><span class="sxs-lookup"><span data-stu-id="37774-110">Anyone can inherit from a class and access the protected members.</span></span>

 <span data-ttu-id="37774-111">*Portions © 2005, 2009 Microsoft Corporation 版权所有。保留所有权利。*</span><span class="sxs-lookup"><span data-stu-id="37774-111">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="37774-112">在 Pearson Education, Inc. 授权下，由 Addison-Wesley Professional 作为 Microsoft Windows 开发系列的一部分再版自 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)（Framework 设计准则：可重用 .NET 库的约定、惯例和模式第 2 版），由 Krzysztof Cwalina 和 Brad Abrams 发布于 2008 年 10 月 22 日。</span><span class="sxs-lookup"><span data-stu-id="37774-112">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="37774-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="37774-113">See also</span></span>

- [<span data-ttu-id="37774-114">框架设计指南</span><span class="sxs-lookup"><span data-stu-id="37774-114">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="37774-115">扩展性设计</span><span class="sxs-lookup"><span data-stu-id="37774-115">Designing for Extensibility</span></span>](designing-for-extensibility.md)
