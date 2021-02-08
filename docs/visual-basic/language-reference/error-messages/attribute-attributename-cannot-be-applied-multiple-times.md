---
description: 了解详细信息： BC30663： <attributename> 不能多次应用特性 ""
title: 特性“<attributename>”不能应用多次
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: 84b77111a7401eb6f30eb7cd167f4b5689f33e77
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797141"
---
# <a name="bc30663-attribute-attributename-cannot-be-applied-multiple-times"></a><span data-ttu-id="6c9fc-103">BC30663：特性 " \<attributename> " 不能应用多次</span><span class="sxs-lookup"><span data-stu-id="6c9fc-103">BC30663: Attribute '\<attributename>' cannot be applied multiple times</span></span>

<span data-ttu-id="6c9fc-104">特性只能应用一次。</span><span class="sxs-lookup"><span data-stu-id="6c9fc-104">The attribute can only be applied once.</span></span> <span data-ttu-id="6c9fc-105">`AttributeUsage`特性确定特性是否可以应用多次。</span><span class="sxs-lookup"><span data-stu-id="6c9fc-105">The `AttributeUsage` attribute determines whether an attribute can be applied more than once.</span></span>

 <span data-ttu-id="6c9fc-106">**错误 ID：** BC30663</span><span class="sxs-lookup"><span data-stu-id="6c9fc-106">**Error ID:** BC30663</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="6c9fc-107">更正此错误</span><span class="sxs-lookup"><span data-stu-id="6c9fc-107">To correct this error</span></span>

1. <span data-ttu-id="6c9fc-108">请确保属性仅应用一次。</span><span class="sxs-lookup"><span data-stu-id="6c9fc-108">Make sure the attribute is only applied once.</span></span>

2. <span data-ttu-id="6c9fc-109">如果使用的是你开发的自定义特性，请考虑将其 `AttributeUsage` 特性更改为允许使用多种特性，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="6c9fc-109">If you are using custom attributes you developed, consider changing their `AttributeUsage` attribute to allow multiple attribute usage, as with the following example.</span></span>

```vb
<AttributeUsage(AllowMultiple := True)>
```

## <a name="see-also"></a><span data-ttu-id="6c9fc-110">请参阅</span><span class="sxs-lookup"><span data-stu-id="6c9fc-110">See also</span></span>

- <xref:System.AttributeUsageAttribute>
- [<span data-ttu-id="6c9fc-111">创建自定义特性</span><span class="sxs-lookup"><span data-stu-id="6c9fc-111">Creating Custom Attributes</span></span>](../../programming-guide/concepts/attributes/creating-custom-attributes.md)
- [<span data-ttu-id="6c9fc-112">AttributeUsage</span><span class="sxs-lookup"><span data-stu-id="6c9fc-112">AttributeUsage</span></span>](../../programming-guide/concepts/attributes/attributeusage.md)
