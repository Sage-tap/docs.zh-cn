---
description: '了解详细信息：处理 XML 文件 (Visual Basic) '
title: 处理 .xml 文件
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments [Visual Basic], parsing [Visual Basic]
ms.assetid: 78a15cd0-7708-4e79-85d1-c154b7a14a8c
ms.openlocfilehash: 2314e7dafbd747f9a19b73d06d71c73631e53861
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100468390"
---
# <a name="processing-the-xml-file-visual-basic"></a><span data-ttu-id="a7c9b-103">处理 XML 文件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7c9b-103">Processing the XML File (Visual Basic)</span></span>

<span data-ttu-id="a7c9b-104">编译器为代码（已标记以生成文档）中的每个构造生成一个 ID 字符串。</span><span class="sxs-lookup"><span data-stu-id="a7c9b-104">The compiler generates an ID string for each construct in your code that is tagged to generate documentation.</span></span> <span data-ttu-id="a7c9b-105"> (有关如何标记代码的信息，请参阅 [XML 注释标记](../../language-reference/xmldoc/index.md)。 ) ID 字符串唯一标识构造。</span><span class="sxs-lookup"><span data-stu-id="a7c9b-105">(For information on how to tag your code, see [XML Comment Tags](../../language-reference/xmldoc/index.md).) The ID string uniquely identifies the construct.</span></span> <span data-ttu-id="a7c9b-106">处理 XML 文件的程序可以使用 ID 字符串来标识相应的 .NET Framework 元数据/反射项。</span><span class="sxs-lookup"><span data-stu-id="a7c9b-106">Programs that process the XML file can use the ID string to identify the corresponding .NET Framework metadata/reflection item.</span></span>  
  
 <span data-ttu-id="a7c9b-107">XML 文件不是代码的层次结构表示形式;它是一个平面列表，其中每个元素都有一个生成的 ID。</span><span class="sxs-lookup"><span data-stu-id="a7c9b-107">The XML file is not a hierarchical representation of your code; it is a flat list with a generated ID for each element.</span></span>  
  
 <span data-ttu-id="a7c9b-108">编译器在生成 ID 字符串时应遵循以下规则：</span><span class="sxs-lookup"><span data-stu-id="a7c9b-108">The compiler observes the following rules when it generates the ID strings:</span></span>  
  
- <span data-ttu-id="a7c9b-109">字符串不得包含空格。</span><span class="sxs-lookup"><span data-stu-id="a7c9b-109">No white space is placed in the string.</span></span>  
  
- <span data-ttu-id="a7c9b-110">ID 字符串的第一部分标识被标识的成员类型，单个字符后跟一个冒号。</span><span class="sxs-lookup"><span data-stu-id="a7c9b-110">The first part of the ID string identifies the kind of member being identified, with a single character followed by a colon.</span></span> <span data-ttu-id="a7c9b-111">使用以下成员类型。</span><span class="sxs-lookup"><span data-stu-id="a7c9b-111">The following member types are used.</span></span>  
  
|<span data-ttu-id="a7c9b-112">字符</span><span class="sxs-lookup"><span data-stu-id="a7c9b-112">Character</span></span>|<span data-ttu-id="a7c9b-113">说明</span><span class="sxs-lookup"><span data-stu-id="a7c9b-113">Description</span></span>|  
|---|---|  
|<span data-ttu-id="a7c9b-114">N</span><span class="sxs-lookup"><span data-stu-id="a7c9b-114">N</span></span>|<span data-ttu-id="a7c9b-115">namespace</span><span class="sxs-lookup"><span data-stu-id="a7c9b-115">namespace</span></span><br /><br /> <span data-ttu-id="a7c9b-116">不能将文档注释添加到命名空间，但可以对其进行 CREF 引用（如果支持）。</span><span class="sxs-lookup"><span data-stu-id="a7c9b-116">You cannot add documentation comments to a namespace, but you can make CREF references to them, where supported.</span></span>|  
|<span data-ttu-id="a7c9b-117">T</span><span class="sxs-lookup"><span data-stu-id="a7c9b-117">T</span></span>|<span data-ttu-id="a7c9b-118">类型： `Class` 、 `Module` 、 `Interface` 、 `Structure` 、 `Enum` 、 `Delegate`</span><span class="sxs-lookup"><span data-stu-id="a7c9b-118">type: `Class`, `Module`, `Interface`, `Structure`, `Enum`, `Delegate`</span></span>|  
|<span data-ttu-id="a7c9b-119">F</span><span class="sxs-lookup"><span data-stu-id="a7c9b-119">F</span></span>|<span data-ttu-id="a7c9b-120">定义域 `Dim`</span><span class="sxs-lookup"><span data-stu-id="a7c9b-120">field: `Dim`</span></span>|  
|<span data-ttu-id="a7c9b-121">P</span><span class="sxs-lookup"><span data-stu-id="a7c9b-121">P</span></span>|<span data-ttu-id="a7c9b-122">属性： `Property` (包括默认属性) </span><span class="sxs-lookup"><span data-stu-id="a7c9b-122">property: `Property` (including default properties)</span></span>|  
|<span data-ttu-id="a7c9b-123">M</span><span class="sxs-lookup"><span data-stu-id="a7c9b-123">M</span></span>|<span data-ttu-id="a7c9b-124">方法： `Sub` 、 `Function` 、 `Declare` 、 `Operator`</span><span class="sxs-lookup"><span data-stu-id="a7c9b-124">method: `Sub`, `Function`, `Declare`, `Operator`</span></span>|  
|<span data-ttu-id="a7c9b-125">E</span><span class="sxs-lookup"><span data-stu-id="a7c9b-125">E</span></span>|<span data-ttu-id="a7c9b-126">引发 `Event`</span><span class="sxs-lookup"><span data-stu-id="a7c9b-126">event: `Event`</span></span>|  
|<span data-ttu-id="a7c9b-127">!</span><span class="sxs-lookup"><span data-stu-id="a7c9b-127">!</span></span>|<span data-ttu-id="a7c9b-128">错误字符串</span><span class="sxs-lookup"><span data-stu-id="a7c9b-128">error string</span></span><br /><br /> <span data-ttu-id="a7c9b-129">字符串的其余部分提供有关错误的信息。</span><span class="sxs-lookup"><span data-stu-id="a7c9b-129">The rest of the string provides information about the error.</span></span> <span data-ttu-id="a7c9b-130">Visual Basic 编译器将为无法解析的链接生成错误信息。</span><span class="sxs-lookup"><span data-stu-id="a7c9b-130">The Visual Basic compiler generates error information for links that cannot be resolved.</span></span>|  
  
- <span data-ttu-id="a7c9b-131">的第二部分 `String` 是项的完全限定名，从命名空间的根开始。</span><span class="sxs-lookup"><span data-stu-id="a7c9b-131">The second part of the `String` is the fully qualified name of the item, starting at the root of the namespace.</span></span> <span data-ttu-id="a7c9b-132">项的名称、其封闭类型 (s) 和命名空间以句点分隔。</span><span class="sxs-lookup"><span data-stu-id="a7c9b-132">The name of the item, its enclosing type(s), and the namespace are separated by periods.</span></span> <span data-ttu-id="a7c9b-133">如果项本身的名称包含句点，则将其替换为数字符号 ( # ) 。</span><span class="sxs-lookup"><span data-stu-id="a7c9b-133">If the name of the item itself contains periods, they are replaced by the number sign (#).</span></span> <span data-ttu-id="a7c9b-134">假定没有任何项在其名称中直接具有数字符号。</span><span class="sxs-lookup"><span data-stu-id="a7c9b-134">It is assumed that no item has a number sign directly in its name.</span></span> <span data-ttu-id="a7c9b-135">例如，构造函数的完全限定名称将 `String` 为 `System.String.#ctor` 。</span><span class="sxs-lookup"><span data-stu-id="a7c9b-135">For example, the fully qualified name of the `String` constructor would be `System.String.#ctor`.</span></span>  
  
- <span data-ttu-id="a7c9b-136">对于属性和方法，如果方法带有自变量，则后跟用括号括起来的自变量列表。</span><span class="sxs-lookup"><span data-stu-id="a7c9b-136">For properties and methods, if there are arguments to the method, the argument list enclosed in parentheses follows.</span></span> <span data-ttu-id="a7c9b-137">如果没有任何自变量，则不会出现括号。</span><span class="sxs-lookup"><span data-stu-id="a7c9b-137">If there are no arguments, no parentheses are present.</span></span> <span data-ttu-id="a7c9b-138">确保自变量之间用逗号分隔。</span><span class="sxs-lookup"><span data-stu-id="a7c9b-138">The arguments are separated by commas.</span></span> <span data-ttu-id="a7c9b-139">每个参数的编码会直接在 .NET Framework 签名中对其进行编码。</span><span class="sxs-lookup"><span data-stu-id="a7c9b-139">The encoding of each argument follows directly how it is encoded in a .NET Framework signature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7c9b-140">示例</span><span class="sxs-lookup"><span data-stu-id="a7c9b-140">Example</span></span>  

 <span data-ttu-id="a7c9b-141">下面的代码演示如何生成类及其成员的 ID 字符串。</span><span class="sxs-lookup"><span data-stu-id="a7c9b-141">The following code shows how the ID strings for a class and its members are generated.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="a7c9b-142">请参阅</span><span class="sxs-lookup"><span data-stu-id="a7c9b-142">See also</span></span>

- [<span data-ttu-id="a7c9b-143">-doc</span><span class="sxs-lookup"><span data-stu-id="a7c9b-143">-doc</span></span>](../../reference/command-line-compiler/doc.md)
- [<span data-ttu-id="a7c9b-144">如何：创建 XML 文档</span><span class="sxs-lookup"><span data-stu-id="a7c9b-144">How to: Create XML Documentation</span></span>](how-to-create-xml-documentation.md)
