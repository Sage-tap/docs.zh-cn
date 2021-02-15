---
description: '了解有关详细信息，请参阅如何：使对象变量不引用任何实例 (Visual Basic) '
title: 如何：使对象变量不引用任何实例
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: 2897720b52e708847fdd139be512e578a7420241
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100481865"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a><span data-ttu-id="ed385-103">如何：使对象变量不引用任何实例 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ed385-103">How to: Make an Object Variable Not Refer to Any Instance (Visual Basic)</span></span>

<span data-ttu-id="ed385-104">您可以通过将对象变量设置为 " [无](../../../language-reference/nothing.md)" 来解除对象变量与任何对象实例的关联。</span><span class="sxs-lookup"><span data-stu-id="ed385-104">You can disassociate an object variable from any object instance by setting it to [Nothing](../../../language-reference/nothing.md).</span></span>  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a><span data-ttu-id="ed385-105">断开对象变量与任何对象实例的关联</span><span class="sxs-lookup"><span data-stu-id="ed385-105">To disassociate an object variable from any object instance</span></span>  
  
- <span data-ttu-id="ed385-106">`Nothing`在赋值语句中将变量设置为。</span><span class="sxs-lookup"><span data-stu-id="ed385-106">Set the variable to `Nothing` in an assignment statement.</span></span>  
  
    ```vb  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a><span data-ttu-id="ed385-107">可靠编程</span><span class="sxs-lookup"><span data-stu-id="ed385-107">Robust Programming</span></span>  

 <span data-ttu-id="ed385-108">如果你的代码尝试访问已设置为的对象变量的成员 `Nothing` ，则 <xref:System.NullReferenceException> 会发生。</span><span class="sxs-lookup"><span data-stu-id="ed385-108">If your code tries to access a member of an object variable that has been set to `Nothing`, a <xref:System.NullReferenceException> occurs.</span></span> <span data-ttu-id="ed385-109">如果将一个对象变量设置为 `Nothing` "频繁"，或者如果可能该变量未初始化，则最好将成员访问包含在 `Try...Catch...Finally` 块中。</span><span class="sxs-lookup"><span data-stu-id="ed385-109">If you set an object variable to `Nothing` frequently, or if it is possible the variable is not initialized, it is a good idea to enclose member accesses in a `Try...Catch...Finally` block.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="ed385-110">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="ed385-110">.NET Framework Security</span></span>  

 <span data-ttu-id="ed385-111">如果对包含机密数据或敏感数据的对象使用对象变量，则可以将变量设置为，以便在 `Nothing` 不主动处理其中一个对象时使用。</span><span class="sxs-lookup"><span data-stu-id="ed385-111">If you use an object variable for objects that contain confidential or sensitive data, you can set the variable to `Nothing` when you are not actively dealing with one of those objects.</span></span> <span data-ttu-id="ed385-112">这减少了恶意代码访问数据的可能性。</span><span class="sxs-lookup"><span data-stu-id="ed385-112">This reduces the chance of malicious code gaining access to the data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed385-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="ed385-113">See also</span></span>

- <xref:System.NullReferenceException>
- [<span data-ttu-id="ed385-114">对象变量</span><span class="sxs-lookup"><span data-stu-id="ed385-114">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="ed385-115">对象变量赋值</span><span class="sxs-lookup"><span data-stu-id="ed385-115">Object Variable Assignment</span></span>](object-variable-assignment.md)
- [<span data-ttu-id="ed385-116">无</span><span class="sxs-lookup"><span data-stu-id="ed385-116">Nothing</span></span>](../../../language-reference/nothing.md)
- [<span data-ttu-id="ed385-117">Try...Catch...Finally 语句</span><span class="sxs-lookup"><span data-stu-id="ed385-117">Try...Catch...Finally Statement</span></span>](../../../language-reference/statements/try-catch-finally-statement.md)
