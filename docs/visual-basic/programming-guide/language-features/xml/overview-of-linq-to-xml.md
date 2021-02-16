---
description: 了解详细信息： LINQ to XML 的概述 Visual Basic
title: LINQ to XML 概述
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], about LINQ to XML
- LINQ [Visual Basic], LINQ to XML
ms.assetid: 01c62a79-6d58-468e-84fb-039c05947701
ms.openlocfilehash: e70998706f62076a2528ac646df29e0c7081cb3d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100480214"
---
# <a name="overview-of-linq-to-xml-in-visual-basic"></a><span data-ttu-id="89417-103">Visual Basic 中的 LINQ to XML 概述</span><span class="sxs-lookup"><span data-stu-id="89417-103">Overview of LINQ to XML in Visual Basic</span></span>

<span data-ttu-id="89417-104">Visual Basic [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 通过 xml 文本和 xml 轴属性提供对的支持。</span><span class="sxs-lookup"><span data-stu-id="89417-104">Visual Basic provides support for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] through XML literals and XML axis properties.</span></span> <span data-ttu-id="89417-105">这使你可以使用熟悉的方便语法在 Visual Basic 代码中处理 XML。</span><span class="sxs-lookup"><span data-stu-id="89417-105">This enables you to use a familiar, convenient syntax for working with XML in your Visual Basic code.</span></span> <span data-ttu-id="89417-106">使用 *xml 文本* 可以将 xml 直接包含在代码中。</span><span class="sxs-lookup"><span data-stu-id="89417-106">*XML literals* enable you to include XML directly in your code.</span></span> <span data-ttu-id="89417-107">利用 *xml 轴属性*，您可以访问 xml 文本的子节点、子代节点和属性。</span><span class="sxs-lookup"><span data-stu-id="89417-107">*XML axis properties* enable you to access child nodes, descendant nodes, and attributes of an XML literal.</span></span> <span data-ttu-id="89417-108">有关详细信息，请参阅 [Xml 文本概述](xml-literals-overview.md) 和 [访问 VISUAL BASIC 中的 xml](accessing-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="89417-108">For more information, see [XML Literals Overview](xml-literals-overview.md) and [Accessing XML in Visual Basic](accessing-xml.md).</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="89417-109">是内存中的 XML 编程 API，专门设计用于利用 Language-Integrated 查询 (LINQ) 。</span><span class="sxs-lookup"><span data-stu-id="89417-109">is an in-memory XML programming API designed specifically to take advantage of Language-Integrated Query (LINQ).</span></span> <span data-ttu-id="89417-110">尽管可以直接调用 LINQ Api，但只有 Visual Basic 允许你声明 XML 文本和直接访问 XML 轴属性。</span><span class="sxs-lookup"><span data-stu-id="89417-110">Although you can call the LINQ APIs directly, only Visual Basic enables you to declare XML literals and directly access XML axis properties.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="89417-111">ASP.NET 页面中的声明性代码不支持 XML 文本和 XML 轴属性。</span><span class="sxs-lookup"><span data-stu-id="89417-111">XML literals and XML axis properties are not supported in declarative code in an ASP.NET page.</span></span> <span data-ttu-id="89417-112">若要使用 Visual Basic XML 功能，请将代码放在 ASP.NET 应用程序的代码隐藏页中。</span><span class="sxs-lookup"><span data-stu-id="89417-112">To use Visual Basic XML features, put your code in a code-behind page in your ASP.NET application.</span></span>  
  
 <span data-ttu-id="89417-113">[播放按钮](./media/overview-of-linq-to-xml/play-video-icon-example.gif) 有关相关的视频演示，请参阅 [如何开始使用 LINQ to XML？](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-get-started-with-linq-to-xml) 和 [如何使用 LINQ to XML 创建 Excel 电子表格？](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-create-excel-spreadsheets-using-linq-to-xml)。</span><span class="sxs-lookup"><span data-stu-id="89417-113">[Play button](./media/overview-of-linq-to-xml/play-video-icon-example.gif) For related video demonstrations, see [How Do I Get Started with LINQ to XML?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-get-started-with-linq-to-xml) and [How Do I Create Excel Spreadsheets using LINQ to XML?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-create-excel-spreadsheets-using-linq-to-xml).</span></span>
  
## <a name="creating-xml"></a><span data-ttu-id="89417-114">创建 XML</span><span class="sxs-lookup"><span data-stu-id="89417-114">Creating XML</span></span>  

 <span data-ttu-id="89417-115">可以通过两种方式在 Visual Basic 中创建 XML 树。</span><span class="sxs-lookup"><span data-stu-id="89417-115">There are two ways to create XML trees in Visual Basic.</span></span> <span data-ttu-id="89417-116">你可以直接在代码中声明 XML 文本，或者可以使用 LINQ Api 创建树。</span><span class="sxs-lookup"><span data-stu-id="89417-116">You can declare an XML literal directly in code, or you can use the LINQ APIs to create the tree.</span></span> <span data-ttu-id="89417-117">这两个进程都使代码可以反映 XML 树的最终结构。</span><span class="sxs-lookup"><span data-stu-id="89417-117">Both processes enable the code to reflect the final structure of the XML tree.</span></span> <span data-ttu-id="89417-118">例如，下面的代码示例创建一个 XML 元素：</span><span class="sxs-lookup"><span data-stu-id="89417-118">For example, the following code example creates an XML element:</span></span>  
  
 [!code-vb[VbXmlSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
 <span data-ttu-id="89417-119">有关详细信息，请参阅 [在 Visual Basic 中创建 XML](creating-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="89417-119">For more information, see [Creating XML in Visual Basic](creating-xml.md).</span></span>  
  
## <a name="accessing-and-navigating-xml"></a><span data-ttu-id="89417-120">访问和导航 XML</span><span class="sxs-lookup"><span data-stu-id="89417-120">Accessing and Navigating XML</span></span>  

 <span data-ttu-id="89417-121">Visual Basic 提供了用于访问和导航 XML 结构的 XML 轴属性。</span><span class="sxs-lookup"><span data-stu-id="89417-121">Visual Basic provides XML axis properties for accessing and navigating XML structures.</span></span> <span data-ttu-id="89417-122">这些属性使你可以通过指定 XML 子元素名称来访问 XML 元素和特性。</span><span class="sxs-lookup"><span data-stu-id="89417-122">These properties enable you to access XML elements and attributes by specifying the XML child element names.</span></span> <span data-ttu-id="89417-123">或者，你可以显式调用用于导航和查找元素和属性的 LINQ 方法。</span><span class="sxs-lookup"><span data-stu-id="89417-123">Alternatively, you can explicitly call the LINQ methods for navigating and locating elements and attributes.</span></span> <span data-ttu-id="89417-124">例如，下面的代码示例使用 XML 轴属性来引用 XML 元素的特性和子元素。</span><span class="sxs-lookup"><span data-stu-id="89417-124">For example, the following code example uses XML axis properties to refer to the attributes and child elements of an XML element.</span></span> <span data-ttu-id="89417-125">此代码示例使用 LINQ 查询来检索子元素，并将其输出为 XML 元素，从而有效地执行转换。</span><span class="sxs-lookup"><span data-stu-id="89417-125">The code example uses a LINQ query to retrieve child elements and output them as XML elements, effectively performing a transform.</span></span>  
  
 [!code-vb[VbXmlSamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples3.vb#8)]  
  
 <span data-ttu-id="89417-126">有关详细信息，请参阅 [Visual Basic 中的访问 XML](accessing-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="89417-126">For more information, see [Accessing XML in Visual Basic](accessing-xml.md).</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="89417-127">XML 命名空间</span><span class="sxs-lookup"><span data-stu-id="89417-127">XML Namespaces</span></span>  

 <span data-ttu-id="89417-128">Visual Basic 使你能够使用语句指定全局 XML 命名空间的别名 `Imports` 。</span><span class="sxs-lookup"><span data-stu-id="89417-128">Visual Basic enables you to specify an alias to a global XML namespace by using the `Imports` statement.</span></span> <span data-ttu-id="89417-129">下面的示例演示如何使用 `Imports` 语句导入 XML 命名空间：</span><span class="sxs-lookup"><span data-stu-id="89417-129">The following example shows how to use the `Imports` statement to import an XML namespace:</span></span>  
  
 [!code-vb[VbXMLSamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#1)]  
  
 <span data-ttu-id="89417-130">访问 XML 轴属性并声明 xml 文档和元素的 XML 文本时，可以使用 XML 命名空间别名。</span><span class="sxs-lookup"><span data-stu-id="89417-130">You can use an XML namespace alias when you access XML axis properties and declare XML literals for XML documents and elements.</span></span>  
  
 <span data-ttu-id="89417-131">可以 <xref:System.Xml.Linq.XNamespace> 使用 [GetXmlNamespace 运算符](../../../language-reference/operators/getxmlnamespace-operator.md)检索特定命名空间前缀的对象。</span><span class="sxs-lookup"><span data-stu-id="89417-131">You can retrieve an <xref:System.Xml.Linq.XNamespace> object for a particular namespace prefix by using the [GetXmlNamespace Operator](../../../language-reference/operators/getxmlnamespace-operator.md).</span></span>  
  
 <span data-ttu-id="89417-132">有关详细信息，请参阅 [ (XML 命名空间) 的 Imports 语句 ](../../../language-reference/statements/imports-statement-xml-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="89417-132">For more information, see [Imports Statement (XML Namespace)](../../../language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
### <a name="using-xml-namespaces-in-xml-literals"></a><span data-ttu-id="89417-133">在 XML 文本中使用 XML 命名空间</span><span class="sxs-lookup"><span data-stu-id="89417-133">Using XML Namespaces in XML Literals</span></span>  

 <span data-ttu-id="89417-134">下面的示例演示如何创建 <xref:System.Xml.Linq.XElement> 使用 global 命名空间的对象 `ns` ：</span><span class="sxs-lookup"><span data-stu-id="89417-134">The following example shows how to create an <xref:System.Xml.Linq.XElement> object that uses the global namespace `ns`:</span></span>  
  
 [!code-vb[VbXMLSamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#2)]  
  
 <span data-ttu-id="89417-135">Visual Basic 编译器将包含 XML 命名空间别名的 XML 文本转换为等效代码，该代码使用 XML 表示法，使用 xml 命名空间和 `xmlns` 属性。</span><span class="sxs-lookup"><span data-stu-id="89417-135">The Visual Basic compiler translates XML literals that contain XML namespace aliases into equivalent code that uses the XML notation for using XML namespaces, with the `xmlns` attribute.</span></span> <span data-ttu-id="89417-136">在编译时，上一部分的示例中的代码将产生实质上与以下示例相同的可执行代码：</span><span class="sxs-lookup"><span data-stu-id="89417-136">When compiled, the code in the previous section's example produces essentially the same executable code as the following example:</span></span>  
  
 [!code-vb[VbXMLSamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#3)]  
  
### <a name="using-xml-namespaces-in-xml-axis-properties"></a><span data-ttu-id="89417-137">在 XML 轴属性中使用 XML 命名空间</span><span class="sxs-lookup"><span data-stu-id="89417-137">Using XML Namespaces in XML Axis Properties</span></span>  

 <span data-ttu-id="89417-138">在 xml 文本中声明的 XML 命名空间不可用于 XML 轴属性。</span><span class="sxs-lookup"><span data-stu-id="89417-138">XML namespaces declared in XML literals are not available for use in XML axis properties.</span></span> <span data-ttu-id="89417-139">但是，可以将全局命名空间与 XML 轴属性一起使用。</span><span class="sxs-lookup"><span data-stu-id="89417-139">However, global namespaces can be used with the XML axis properties.</span></span> <span data-ttu-id="89417-140">使用冒号分隔 XML 命名空间前缀和本地元素名称。</span><span class="sxs-lookup"><span data-stu-id="89417-140">Use a colon to separate the XML namespace prefix from the local element name.</span></span> <span data-ttu-id="89417-141">下面是一个示例：</span><span class="sxs-lookup"><span data-stu-id="89417-141">Following is an example:</span></span>  
  
 [!code-vb[VbXMLSamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="89417-142">请参阅</span><span class="sxs-lookup"><span data-stu-id="89417-142">See also</span></span>

- [<span data-ttu-id="89417-143">XML</span><span class="sxs-lookup"><span data-stu-id="89417-143">XML</span></span>](index.md)
- [<span data-ttu-id="89417-144">在 Visual Basic 中创建 XML</span><span class="sxs-lookup"><span data-stu-id="89417-144">Creating XML in Visual Basic</span></span>](creating-xml.md)
- [<span data-ttu-id="89417-145">在 Visual Basic 中访问 XML</span><span class="sxs-lookup"><span data-stu-id="89417-145">Accessing XML in Visual Basic</span></span>](accessing-xml.md)
- [<span data-ttu-id="89417-146">在 Visual Basic 中操作 XML</span><span class="sxs-lookup"><span data-stu-id="89417-146">Manipulating XML in Visual Basic</span></span>](manipulating-xml.md)
