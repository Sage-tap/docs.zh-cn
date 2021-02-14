---
description: '了解详细信息： XML (Visual Basic 中的嵌入表达式) '
title: XML 中的嵌入式表达式
ms.date: 07/20/2015
f1_keywords:
- vb.XmlEmbeddedExpression
helpviewer_keywords:
- embedded expressions [Visual Basic]
- LINQ to XML [Visual Basic], embedded expressions
- XML literals [Visual Basic], embedded expressions
ms.assetid: bf2eb779-b751-4b7c-854f-9f2161482352
ms.openlocfilehash: 52cf8341cb0a55abad230543bbc6367aea071142
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100433182"
---
# <a name="embedded-expressions-in-xml-visual-basic"></a><span data-ttu-id="dd385-103">XML 中的嵌入式表达式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd385-103">Embedded Expressions in XML (Visual Basic)</span></span>

<span data-ttu-id="dd385-104">使用嵌入式表达式可以创建包含在运行时计算的表达式的 XML 文本。</span><span class="sxs-lookup"><span data-stu-id="dd385-104">Embedded expressions enable you to create XML literals that contain expressions that are evaluated at run time.</span></span> <span data-ttu-id="dd385-105">嵌入式表达式的语法是 `<%=` `expression` `%>` ，这与 ASP.NET 中使用的语法相同。</span><span class="sxs-lookup"><span data-stu-id="dd385-105">The syntax for an embedded expression is `<%=` `expression` `%>`, which is the same as the syntax used in ASP.NET.</span></span>  
  
 <span data-ttu-id="dd385-106">例如，可以创建 XML 元素文本，并将嵌入式表达式与文本内容组合在一起。</span><span class="sxs-lookup"><span data-stu-id="dd385-106">For example, you can create an XML element literal, combining embedded expressions with literal text content.</span></span>  
  
 [!code-vb[VbXMLSamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#27)]  
  
 <span data-ttu-id="dd385-107">如果 `isbnNumber` 包含整数12345，并且 `modifiedDate` 包含日期3/5/2006，则在此代码执行时，的值 `book` 为：</span><span class="sxs-lookup"><span data-stu-id="dd385-107">If `isbnNumber` contains the integer 12345 and `modifiedDate` contains the date 3/5/2006, when this code executes, the value of `book` is:</span></span>  
  
```xml  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a><span data-ttu-id="dd385-108">嵌入式表达式位置和验证</span><span class="sxs-lookup"><span data-stu-id="dd385-108">Embedded Expression Location and Validation</span></span>  

 <span data-ttu-id="dd385-109">嵌入式表达式只能出现在 XML 文本表达式中的某些位置。</span><span class="sxs-lookup"><span data-stu-id="dd385-109">Embedded expressions can appear only at certain locations within XML literal expressions.</span></span> <span data-ttu-id="dd385-110">表达式位置控制表达式可以返回的类型以及 `Nothing` 处理方式。</span><span class="sxs-lookup"><span data-stu-id="dd385-110">The expression location controls which types the expression can return and how `Nothing` is handled.</span></span> <span data-ttu-id="dd385-111">下表描述了嵌入表达式的允许位置和类型。</span><span class="sxs-lookup"><span data-stu-id="dd385-111">The following table describes the allowed locations and types of embedded expressions.</span></span>  
  
|<span data-ttu-id="dd385-112">文本中的位置</span><span class="sxs-lookup"><span data-stu-id="dd385-112">Location in literal</span></span>|<span data-ttu-id="dd385-113">表达式的类型</span><span class="sxs-lookup"><span data-stu-id="dd385-113">Type of expression</span></span>|<span data-ttu-id="dd385-114">处理 `Nothing`</span><span class="sxs-lookup"><span data-stu-id="dd385-114">Handling of `Nothing`</span></span>|  
|---|---|---|  
|<span data-ttu-id="dd385-115">XML 元素名称</span><span class="sxs-lookup"><span data-stu-id="dd385-115">XML element name</span></span>|<xref:System.Xml.Linq.XName>|<span data-ttu-id="dd385-116">错误</span><span class="sxs-lookup"><span data-stu-id="dd385-116">Error</span></span>|  
|<span data-ttu-id="dd385-117">XML 元素内容</span><span class="sxs-lookup"><span data-stu-id="dd385-117">XML element content</span></span>|<span data-ttu-id="dd385-118">`Object` 或数组 `Object`</span><span class="sxs-lookup"><span data-stu-id="dd385-118">`Object` or array of `Object`</span></span>|<span data-ttu-id="dd385-119">忽略</span><span class="sxs-lookup"><span data-stu-id="dd385-119">Ignored</span></span>|  
|<span data-ttu-id="dd385-120">XML 元素特性名称</span><span class="sxs-lookup"><span data-stu-id="dd385-120">XML element attribute name</span></span>|<xref:System.Xml.Linq.XName>|<span data-ttu-id="dd385-121">错误，除非该属性值也为 `Nothing`</span><span class="sxs-lookup"><span data-stu-id="dd385-121">Error, unless the attribute value is also `Nothing`</span></span>|  
|<span data-ttu-id="dd385-122">XML 元素特性值</span><span class="sxs-lookup"><span data-stu-id="dd385-122">XML element attribute value</span></span>|`Object`|<span data-ttu-id="dd385-123">忽略属性声明</span><span class="sxs-lookup"><span data-stu-id="dd385-123">Attribute declaration ignored</span></span>|  
|<span data-ttu-id="dd385-124">XML 元素特性</span><span class="sxs-lookup"><span data-stu-id="dd385-124">XML element attribute</span></span>|<span data-ttu-id="dd385-125"><xref:System.Xml.Linq.XAttribute> 或的集合 <xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="dd385-125"><xref:System.Xml.Linq.XAttribute> or a collection of <xref:System.Xml.Linq.XAttribute></span></span>|<span data-ttu-id="dd385-126">忽略</span><span class="sxs-lookup"><span data-stu-id="dd385-126">Ignored</span></span>|  
|<span data-ttu-id="dd385-127">XML 文档根元素</span><span class="sxs-lookup"><span data-stu-id="dd385-127">XML document root element</span></span>|<span data-ttu-id="dd385-128"><xref:System.Xml.Linq.XElement> 或一个对象的集合 <xref:System.Xml.Linq.XElement> ，以及任意数量的 <xref:System.Xml.Linq.XProcessingInstruction> 和 <xref:System.Xml.Linq.XComment> 对象</span><span class="sxs-lookup"><span data-stu-id="dd385-128"><xref:System.Xml.Linq.XElement> or a collection of one <xref:System.Xml.Linq.XElement> object and an arbitrary number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects</span></span>|<span data-ttu-id="dd385-129">忽略</span><span class="sxs-lookup"><span data-stu-id="dd385-129">Ignored</span></span>|  
  
- <span data-ttu-id="dd385-130">XML 元素名称中的嵌入表达式的示例：</span><span class="sxs-lookup"><span data-stu-id="dd385-130">Example of an embedded expression in an XML element name:</span></span>  
  
     [!code-vb[VbXMLSamples#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#32)]  
  
- <span data-ttu-id="dd385-131">XML 元素内容中的嵌入表达式的示例：</span><span class="sxs-lookup"><span data-stu-id="dd385-131">Example of an embedded expression in the content of an XML element:</span></span>  
  
     [!code-vb[VbXMLSamples#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#33)]  
  
- <span data-ttu-id="dd385-132">XML 元素属性名称中的嵌入式表达式的示例：</span><span class="sxs-lookup"><span data-stu-id="dd385-132">Example of an embedded expression in an XML element attribute name:</span></span>  
  
     [!code-vb[VbXMLSamples#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#34)]  
  
- <span data-ttu-id="dd385-133">XML 元素特性值中的嵌入式表达式的示例：</span><span class="sxs-lookup"><span data-stu-id="dd385-133">Example of an embedded expression in an XML element attribute value:</span></span>  
  
     [!code-vb[VbXMLSamples#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#35)]  
  
- <span data-ttu-id="dd385-134">XML 元素特性中的嵌入式表达式的示例：</span><span class="sxs-lookup"><span data-stu-id="dd385-134">Example of an embedded expression in an XML element attribute:</span></span>  
  
     [!code-vb[VbXMLSamples#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#36)]  
  
- <span data-ttu-id="dd385-135">XML 文档根元素中的嵌入式表达式的示例：</span><span class="sxs-lookup"><span data-stu-id="dd385-135">Example of an embedded expression in an XML document root element:</span></span>  
  
     [!code-vb[VbXMLSamples#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#37)]  
  
 <span data-ttu-id="dd385-136">如果启用 `Option Strict` ，编译器会检查每个嵌入式表达式的类型是否扩大到了所需的类型。</span><span class="sxs-lookup"><span data-stu-id="dd385-136">If you enable `Option Strict`, the compiler checks that the type of each embedded expression widens to the required type.</span></span> <span data-ttu-id="dd385-137">唯一的例外是在代码运行时验证的 XML 文档的根元素。</span><span class="sxs-lookup"><span data-stu-id="dd385-137">The only exception is for the root element of an XML document, which is verified when the code runs.</span></span> <span data-ttu-id="dd385-138">如果在不进行编译的情况下进行编译 `Option Strict` ，则可以嵌入类型的表达式， `Object` 并在运行时验证其类型。</span><span class="sxs-lookup"><span data-stu-id="dd385-138">If you compile without `Option Strict`, you can embed expressions of type `Object` and their type is verified at run time.</span></span>  
  
 <span data-ttu-id="dd385-139">在内容可选的位置中， `Nothing` 将忽略包含的嵌入表达式。</span><span class="sxs-lookup"><span data-stu-id="dd385-139">In locations where content is optional, embedded expressions that contain `Nothing` are ignored.</span></span> <span data-ttu-id="dd385-140">这意味着，在 `Nothing` 使用 XML 文本之前，无需检查元素内容、特性值和数组元素。</span><span class="sxs-lookup"><span data-stu-id="dd385-140">This means you do not have to check that element content, attribute values, and array elements are not `Nothing` before you use an XML literal.</span></span> <span data-ttu-id="dd385-141">必需的值（如元素和属性名称）不能为 `Nothing` 。</span><span class="sxs-lookup"><span data-stu-id="dd385-141">Required values, such as element and attribute names, cannot be `Nothing`.</span></span>  
  
 <span data-ttu-id="dd385-142">有关使用特定类型文本中的嵌入表达式的详细信息，请参阅 [Xml 文档文本](../../../language-reference/xml-literals/xml-document-literal.md)和 [xml 元素文本](../../../language-reference/xml-literals/xml-element-literal.md)。</span><span class="sxs-lookup"><span data-stu-id="dd385-142">For more information about using an embedded expression in a particular type of literal, see [XML Document Literal](../../../language-reference/xml-literals/xml-document-literal.md), [XML Element Literal](../../../language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="scoping-rules"></a><span data-ttu-id="dd385-143">作用域规则</span><span class="sxs-lookup"><span data-stu-id="dd385-143">Scoping Rules</span></span>  

 <span data-ttu-id="dd385-144">编译器将每个 XML 文本转换为相应文本类型的构造函数调用。</span><span class="sxs-lookup"><span data-stu-id="dd385-144">The compiler converts each XML literal into a constructor call for the appropriate literal type.</span></span> <span data-ttu-id="dd385-145">XML 文本中的文本内容和嵌入式表达式作为参数传递给构造函数。</span><span class="sxs-lookup"><span data-stu-id="dd385-145">The literal content and embedded expressions in an XML literal are passed as arguments to the constructor.</span></span> <span data-ttu-id="dd385-146">这意味着，XML 文本可用的所有 Visual Basic 编程元素也可用于其嵌入式表达式。</span><span class="sxs-lookup"><span data-stu-id="dd385-146">This means that all Visual Basic programming elements available to an XML literal are also available to its embedded expressions.</span></span>  
  
 <span data-ttu-id="dd385-147">在 XML 文本中，可以访问用语句声明的 XML 命名空间前缀 `Imports` 。</span><span class="sxs-lookup"><span data-stu-id="dd385-147">Within an XML literal, you can access the XML namespace prefixes declared with the `Imports` statement.</span></span> <span data-ttu-id="dd385-148">您可以使用属性在元素中声明新的 XML 命名空间前缀或隐藏现有的 XML 命名空间前缀 `xmlns` 。</span><span class="sxs-lookup"><span data-stu-id="dd385-148">You can declare a new XML namespace prefix, or shadow an existing XML namespace prefix, in an element by using the `xmlns` attribute.</span></span> <span data-ttu-id="dd385-149">新命名空间可用于该元素的子节点，但不适用于嵌入的表达式中的 XML 文本。</span><span class="sxs-lookup"><span data-stu-id="dd385-149">The new namespace is available to the child nodes of that element, but not to XML literals in embedded expressions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dd385-150">使用 namespace 特性声明 XML 命名空间前缀时 `xmlns` ，属性值必须是常量字符串。</span><span class="sxs-lookup"><span data-stu-id="dd385-150">When you declare an XML namespace prefix by using the `xmlns` namespace attribute, the attribute value must be a constant string.</span></span> <span data-ttu-id="dd385-151">在这方面，使用属性的方式 `xmlns` 类似于使用 `Imports` 语句声明 XML 命名空间。</span><span class="sxs-lookup"><span data-stu-id="dd385-151">In this regard, using the `xmlns` attribute is like using the `Imports` statement to declare an XML namespace.</span></span> <span data-ttu-id="dd385-152">不能使用嵌入的表达式来指定 XML 命名空间值。</span><span class="sxs-lookup"><span data-stu-id="dd385-152">You cannot use an embedded expression to specify the XML namespace value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd385-153">请参阅</span><span class="sxs-lookup"><span data-stu-id="dd385-153">See also</span></span>

- [<span data-ttu-id="dd385-154">在 Visual Basic 中创建 XML</span><span class="sxs-lookup"><span data-stu-id="dd385-154">Creating XML in Visual Basic</span></span>](creating-xml.md)
- [<span data-ttu-id="dd385-155">XML 文档文本</span><span class="sxs-lookup"><span data-stu-id="dd385-155">XML Document Literal</span></span>](../../../language-reference/xml-literals/xml-document-literal.md)
- [<span data-ttu-id="dd385-156">XML 元素文本</span><span class="sxs-lookup"><span data-stu-id="dd385-156">XML Element Literal</span></span>](../../../language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="dd385-157">Option Strict 语句</span><span class="sxs-lookup"><span data-stu-id="dd385-157">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="dd385-158">Imports 语句（.NET 命名空间和类型）</span><span class="sxs-lookup"><span data-stu-id="dd385-158">Imports Statement (.NET Namespace and Type)</span></span>](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="dd385-159">XML 文本概述</span><span class="sxs-lookup"><span data-stu-id="dd385-159">XML Literals Overview</span></span>](xml-literals-overview.md)
