---
description: '了解有关以下内容的详细信息：如何：访问 XML 子元素 (Visual Basic) '
title: 如何：访问 XML 子元素
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
ms.openlocfilehash: fad4d45853006762bc319b0ff8f9143ef13058da
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100433234"
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a><span data-ttu-id="bbc3a-103">如何：访问 XML 子元素 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bbc3a-103">How to: Access XML Child Elements (Visual Basic)</span></span>

<span data-ttu-id="bbc3a-104">此示例演示如何使用子轴属性访问 XML 元素中具有指定名称的所有 XML 子元素。</span><span class="sxs-lookup"><span data-stu-id="bbc3a-104">This example shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span> <span data-ttu-id="bbc3a-105">具体而言，它使用 <xref:System.Xml.Linq.XElement.Value%2A> 属性获取 `name` 子轴属性返回的集合中第一个元素的值。</span><span class="sxs-lookup"><span data-stu-id="bbc3a-105">In particular, it uses the <xref:System.Xml.Linq.XElement.Value%2A> property to get the value of the first element in the collection that the `name` child axis property returns.</span></span> <span data-ttu-id="bbc3a-106">`name`子轴属性获取对象中名为的所有子元素 `phone` `contact` 。</span><span class="sxs-lookup"><span data-stu-id="bbc3a-106">The `name` child axis property gets all child elements named `phone` in the `contact` object.</span></span> <span data-ttu-id="bbc3a-107">此示例还使用 `phone` 子轴属性来访问 `phone` 对象中包含的所有名为的子元素 `contact` 。</span><span class="sxs-lookup"><span data-stu-id="bbc3a-107">This example also uses the `phone` child axis property to access all child elements named `phone` that are contained in the `contact` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbc3a-108">示例</span><span class="sxs-lookup"><span data-stu-id="bbc3a-108">Example</span></span>  

 [!code-vb[VbXMLSamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#10)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="bbc3a-109">编译代码</span><span class="sxs-lookup"><span data-stu-id="bbc3a-109">Compile the code</span></span>  

 <span data-ttu-id="bbc3a-110">此示例需要：</span><span class="sxs-lookup"><span data-stu-id="bbc3a-110">This example requires:</span></span>  
  
- <span data-ttu-id="bbc3a-111">对 <xref:System.Xml.Linq> 命名空间的引用。</span><span class="sxs-lookup"><span data-stu-id="bbc3a-111">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbc3a-112">请参阅</span><span class="sxs-lookup"><span data-stu-id="bbc3a-112">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- [<span data-ttu-id="bbc3a-113">XML Child Axis Property</span><span class="sxs-lookup"><span data-stu-id="bbc3a-113">XML Child Axis Property</span></span>](../../../language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="bbc3a-114">XML 值属性</span><span class="sxs-lookup"><span data-stu-id="bbc3a-114">XML Value Property</span></span>](../../../language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="bbc3a-115">在 Visual Basic 中访问 XML</span><span class="sxs-lookup"><span data-stu-id="bbc3a-115">Accessing XML in Visual Basic</span></span>](accessing-xml.md)
- [<span data-ttu-id="bbc3a-116">XML</span><span class="sxs-lookup"><span data-stu-id="bbc3a-116">XML</span></span>](index.md)
