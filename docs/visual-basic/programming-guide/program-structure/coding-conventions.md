---
description: 了解详细信息： Visual Basic 编码约定
title: 编码约定
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- examples [Visual Basic], coding conventions
- Visual Basic code, conventions
ms.assetid: c1df130b-fec6-49a5-becf-0a7e494a1d0f
ms.openlocfilehash: 424871ab0e77629ded977bd0be768ed8736d1761
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100460028"
---
# <a name="visual-basic-coding-conventions"></a><span data-ttu-id="4cb72-103">Visual Basic 编码约定</span><span class="sxs-lookup"><span data-stu-id="4cb72-103">Visual Basic Coding Conventions</span></span>

<span data-ttu-id="4cb72-104">Microsoft 将按照本主题中的准则开发示例和文档。</span><span class="sxs-lookup"><span data-stu-id="4cb72-104">Microsoft develops samples and documentation that follow the guidelines in this topic.</span></span> <span data-ttu-id="4cb72-105">如果遵循相同的编码约定，可能会获得以下好处：</span><span class="sxs-lookup"><span data-stu-id="4cb72-105">If you follow the same coding conventions, you may gain the following benefits:</span></span>  
  
- <span data-ttu-id="4cb72-106">你的代码将具有一致的外观，以便读者可以更好地专注于内容而非布局。</span><span class="sxs-lookup"><span data-stu-id="4cb72-106">Your code will have a consistent look, so that readers can better focus on content, not layout.</span></span>  
  
- <span data-ttu-id="4cb72-107">读者可以更快地了解你的代码，因为它们可以根据以前的经验做出假设。</span><span class="sxs-lookup"><span data-stu-id="4cb72-107">Readers understand your code more quickly because they can make assumptions based on previous experience.</span></span>  
  
- <span data-ttu-id="4cb72-108">您可以更轻松地复制、更改和维护代码。</span><span class="sxs-lookup"><span data-stu-id="4cb72-108">You can copy, change, and maintain the code more easily.</span></span>  
  
- <span data-ttu-id="4cb72-109">您可以帮助确保您的代码演示 Visual Basic 的 "最佳实践"。</span><span class="sxs-lookup"><span data-stu-id="4cb72-109">You help ensure that your code demonstrates "best practices" for Visual Basic.</span></span>  
  
## <a name="naming-conventions"></a><span data-ttu-id="4cb72-110">命名约定</span><span class="sxs-lookup"><span data-stu-id="4cb72-110">Naming Conventions</span></span>  
  
- <span data-ttu-id="4cb72-111">有关命名准则的信息，请参阅 [命名准则](../../../standard/design-guidelines/naming-guidelines.md) 主题。</span><span class="sxs-lookup"><span data-stu-id="4cb72-111">For information about naming guidelines, see [Naming Guidelines](../../../standard/design-guidelines/naming-guidelines.md) topic.</span></span>  
  
- <span data-ttu-id="4cb72-112">不要使用 "我的" 或 "我的" 作为变量名称的一部分。</span><span class="sxs-lookup"><span data-stu-id="4cb72-112">Do not use "My" or "my" as part of a variable name.</span></span> <span data-ttu-id="4cb72-113">这种做法会与 `My` 对象混淆。</span><span class="sxs-lookup"><span data-stu-id="4cb72-113">This practice creates confusion with the `My` objects.</span></span>  
  
- <span data-ttu-id="4cb72-114">不需要在自动生成的代码中更改对象的名称，使其符合指导原则。</span><span class="sxs-lookup"><span data-stu-id="4cb72-114">You do not have to change the names of objects in auto-generated code to make them fit the guidelines.</span></span>  
  
## <a name="layout-conventions"></a><span data-ttu-id="4cb72-115">布局约定</span><span class="sxs-lookup"><span data-stu-id="4cb72-115">Layout Conventions</span></span>  
  
- <span data-ttu-id="4cb72-116">将制表符插入为空格，并使用具有四个空格缩进的智能缩进。</span><span class="sxs-lookup"><span data-stu-id="4cb72-116">Insert tabs as spaces, and use smart indenting with four-space indents.</span></span>  
  
- <span data-ttu-id="4cb72-117">使用 **整齐的列表 (** 重新设置代码) 格式，以在代码编辑器中重新设置代码的格式。</span><span class="sxs-lookup"><span data-stu-id="4cb72-117">Use **Pretty listing (reformatting) of code** to reformat your code in the code editor.</span></span> <span data-ttu-id="4cb72-118">有关详细信息，请参阅 [选项、文本编辑器、基本 (Visual Basic) ](/visualstudio/ide/reference/options-text-editor-basic-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="4cb72-118">For more information, see [Options, Text Editor, Basic (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic).</span></span>  
  
- <span data-ttu-id="4cb72-119">每行仅使用一条语句。</span><span class="sxs-lookup"><span data-stu-id="4cb72-119">Use only one statement per line.</span></span> <span data-ttu-id="4cb72-120">不要使用 Visual Basic 行分隔符 (： ) 。</span><span class="sxs-lookup"><span data-stu-id="4cb72-120">Don't use the Visual Basic line separator character (:).</span></span>  
  
- <span data-ttu-id="4cb72-121">在语言允许的任何位置，避免使用显式行继续符 "_" 来取代隐式行继续符。</span><span class="sxs-lookup"><span data-stu-id="4cb72-121">Avoid using the explicit line continuation character "_" in favor of implicit line continuation wherever the language allows it.</span></span>  
  
- <span data-ttu-id="4cb72-122">每行仅使用一个声明。</span><span class="sxs-lookup"><span data-stu-id="4cb72-122">Use only one declaration per line.</span></span>  
  
- <span data-ttu-id="4cb72-123">如果在很多情况下 **(重新格式化) 的代码** 不会自动设置延续行的格式，则手动将连续行缩进一个制表位。</span><span class="sxs-lookup"><span data-stu-id="4cb72-123">If **Pretty listing (reformatting) of code** doesn't format continuation lines automatically, manually indent continuation lines one tab stop.</span></span> <span data-ttu-id="4cb72-124">但是，始终左对齐列表中的项。</span><span class="sxs-lookup"><span data-stu-id="4cb72-124">However, always left-align items in a list.</span></span>  
  
    ```vb  
    a As Integer,  
    b As Integer  
    ```  
  
- <span data-ttu-id="4cb72-125">在方法和属性定义之间添加至少一个空白行。</span><span class="sxs-lookup"><span data-stu-id="4cb72-125">Add at least one blank line between method and property definitions.</span></span>  
  
## <a name="commenting-conventions"></a><span data-ttu-id="4cb72-126">注释约定</span><span class="sxs-lookup"><span data-stu-id="4cb72-126">Commenting Conventions</span></span>  
  
- <span data-ttu-id="4cb72-127">将注释放在单独的行上，而不是放在代码行的末尾。</span><span class="sxs-lookup"><span data-stu-id="4cb72-127">Put comments on a separate line instead of at the end of a line of code.</span></span>  
  
- <span data-ttu-id="4cb72-128">以大写字母开始注释文本，并以句点结束注释文本。</span><span class="sxs-lookup"><span data-stu-id="4cb72-128">Start comment text with an uppercase letter, and end comment text with a period.</span></span>  
  
- <span data-ttu-id="4cb72-129">在注释分隔符 ( ") 与注释文本之间插入一个空格。</span><span class="sxs-lookup"><span data-stu-id="4cb72-129">Insert one space between the comment delimiter (') and the comment text.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#2)]  
  
- <span data-ttu-id="4cb72-130">不要在带格式的星号块中环绕注释。</span><span class="sxs-lookup"><span data-stu-id="4cb72-130">Do not surround comments with formatted blocks of asterisks.</span></span>  
  
## <a name="program-structure"></a><span data-ttu-id="4cb72-131">程序结构</span><span class="sxs-lookup"><span data-stu-id="4cb72-131">Program Structure</span></span>  
  
- <span data-ttu-id="4cb72-132">使用 `Main` 方法时，请为新的控制台应用程序使用默认构造，并使用 `My` 作为命令行参数。</span><span class="sxs-lookup"><span data-stu-id="4cb72-132">When you use the `Main` method, use the default construct for new console applications, and use `My` for command-line arguments.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#3)]  
  
## <a name="language-guidelines"></a><span data-ttu-id="4cb72-133">语言准则</span><span class="sxs-lookup"><span data-stu-id="4cb72-133">Language Guidelines</span></span>  
  
### <a name="string-data-type"></a><span data-ttu-id="4cb72-134">String 数据类型</span><span class="sxs-lookup"><span data-stu-id="4cb72-134">String Data Type</span></span>  
  
- <span data-ttu-id="4cb72-135">使用[字符串内插](../language-features/strings/interpolated-strings.md)来连接短字符串，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="4cb72-135">Use [string interpolation](../language-features/strings/interpolated-strings.md) to concatenate short strings, as shown in the following code.</span></span>
  
     ```vb
     MsgBox($"hello{vbCrLf}goodbye")
     ```
  
- <span data-ttu-id="4cb72-136">若要在循环中追加字符串，请使用 <xref:System.Text.StringBuilder> 对象。</span><span class="sxs-lookup"><span data-stu-id="4cb72-136">To append strings in loops, use the <xref:System.Text.StringBuilder> object.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#5)]  
  
### <a name="relaxed-delegates-in-event-handlers"></a><span data-ttu-id="4cb72-137">事件处理程序中的宽松委托</span><span class="sxs-lookup"><span data-stu-id="4cb72-137">Relaxed Delegates in Event Handlers</span></span>  

 <span data-ttu-id="4cb72-138">不要向事件处理程序 (对象和 EventArgs) 显式限定参数。</span><span class="sxs-lookup"><span data-stu-id="4cb72-138">Do not explicitly qualify the arguments (Object and EventArgs) to event handlers.</span></span> <span data-ttu-id="4cb72-139">如果未使用传递给事件的事件参数 (例如，发送方为 Object，e 作为 EventArgs) ，请使用宽松委托，并在代码中留下事件参数：</span><span class="sxs-lookup"><span data-stu-id="4cb72-139">If you are not using the event arguments that are passed to an event (for example, sender as Object, e as EventArgs), use relaxed delegates, and leave out the event arguments in your code:</span></span>  
  
 [!code-vb[VbVbalrGuidelines#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#7)]  
  
### <a name="unsigned-data-type"></a><span data-ttu-id="4cb72-140">无符号数据类型</span><span class="sxs-lookup"><span data-stu-id="4cb72-140">Unsigned Data Type</span></span>  
  
- <span data-ttu-id="4cb72-141">使用 `Integer` 而不是无符号类型，但它们是必需的。</span><span class="sxs-lookup"><span data-stu-id="4cb72-141">Use `Integer` rather than unsigned types, except where they are necessary.</span></span>  
  
### <a name="arrays"></a><span data-ttu-id="4cb72-142">数组</span><span class="sxs-lookup"><span data-stu-id="4cb72-142">Arrays</span></span>  
  
- <span data-ttu-id="4cb72-143">在声明行上初始化数组时，请使用短语法。</span><span class="sxs-lookup"><span data-stu-id="4cb72-143">Use the short syntax when you initialize arrays on the declaration line.</span></span> <span data-ttu-id="4cb72-144">例如，使用以下语法。</span><span class="sxs-lookup"><span data-stu-id="4cb72-144">For example, use the following syntax.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#8)]  
  
     <span data-ttu-id="4cb72-145">不要使用以下语法。</span><span class="sxs-lookup"><span data-stu-id="4cb72-145">Do not use the following syntax.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#9)]  
  
- <span data-ttu-id="4cb72-146">将数组指示符置于类型上，而不是变量上。</span><span class="sxs-lookup"><span data-stu-id="4cb72-146">Put the array designator on the type, not on the variable.</span></span> <span data-ttu-id="4cb72-147">例如，使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="4cb72-147">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#11)]  
  
     <span data-ttu-id="4cb72-148">不要使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="4cb72-148">Do not use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#10)]  
  
- <span data-ttu-id="4cb72-149">声明和初始化基本数据类型的数组时，请使用 {} 语法。</span><span class="sxs-lookup"><span data-stu-id="4cb72-149">Use the { } syntax when you declare and initialize arrays of basic data types.</span></span> <span data-ttu-id="4cb72-150">例如，使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="4cb72-150">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#12)]  
  
     <span data-ttu-id="4cb72-151">不要使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="4cb72-151">Do not use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#13)]  
  
### <a name="use-the-with-keyword"></a><span data-ttu-id="4cb72-152">使用 With 关键字</span><span class="sxs-lookup"><span data-stu-id="4cb72-152">Use the With Keyword</span></span>  

 <span data-ttu-id="4cb72-153">对一个对象进行一系列调用时，请考虑使用 `With` 关键字：</span><span class="sxs-lookup"><span data-stu-id="4cb72-153">When you make a series of calls to one object, consider using the `With` keyword:</span></span>  
  
 [!code-vb[VbVbalrGuidelines#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#15)]  
  
### <a name="use-the-trycatch-and-using-statements-when-you-use-exception-handling"></a><span data-ttu-id="4cb72-154">使用 Try .。。使用异常处理时捕获和使用语句</span><span class="sxs-lookup"><span data-stu-id="4cb72-154">Use the Try...Catch and Using Statements when you use Exception Handling</span></span>  

 <span data-ttu-id="4cb72-155">请勿使用 `On Error Goto`。</span><span class="sxs-lookup"><span data-stu-id="4cb72-155">Do not use `On Error Goto`.</span></span>  
  
### <a name="use-the-isnot-keyword"></a><span data-ttu-id="4cb72-156">使用 IsNot 关键字</span><span class="sxs-lookup"><span data-stu-id="4cb72-156">Use the IsNot Keyword</span></span>  

 <span data-ttu-id="4cb72-157">使用 `IsNot` 关键字而不是 `Not...Is Nothing` 。</span><span class="sxs-lookup"><span data-stu-id="4cb72-157">Use the `IsNot` keyword instead of `Not...Is Nothing`.</span></span>  
  
### <a name="new-keyword"></a><span data-ttu-id="4cb72-158">New 关键字</span><span class="sxs-lookup"><span data-stu-id="4cb72-158">New Keyword</span></span>  
  
- <span data-ttu-id="4cb72-159">使用短实例化。</span><span class="sxs-lookup"><span data-stu-id="4cb72-159">Use short instantiation.</span></span> <span data-ttu-id="4cb72-160">例如，使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="4cb72-160">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#21)]  
  
     <span data-ttu-id="4cb72-161">前面的行等效于：</span><span class="sxs-lookup"><span data-stu-id="4cb72-161">The preceding line is equivalent to this:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#22)]  
  
- <span data-ttu-id="4cb72-162">为新对象使用对象初始值设定项，而不使用无参数构造函数：</span><span class="sxs-lookup"><span data-stu-id="4cb72-162">Use object initializers for new objects instead of the parameterless constructor:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#23)]  
  
### <a name="event-handling"></a><span data-ttu-id="4cb72-163">事件处理</span><span class="sxs-lookup"><span data-stu-id="4cb72-163">Event Handling</span></span>  
  
- <span data-ttu-id="4cb72-164">使用 `Handles` 而不是 `AddHandler` ：</span><span class="sxs-lookup"><span data-stu-id="4cb72-164">Use `Handles` rather than `AddHandler`:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#24)]  
  
- <span data-ttu-id="4cb72-165">使用 `AddressOf` ，并且不显式实例化委托：</span><span class="sxs-lookup"><span data-stu-id="4cb72-165">Use `AddressOf`, and do not instantiate the delegate explicitly:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#25)]  
  
- <span data-ttu-id="4cb72-166">定义事件时，请使用 short 语法，并让编译器定义委托：</span><span class="sxs-lookup"><span data-stu-id="4cb72-166">When you define an event, use the short syntax, and let the compiler define the delegate:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#26)]  
  
- <span data-ttu-id="4cb72-167">在调用方法之前，不要验证事件是否为 `Nothing` null)  (`RaiseEvent` 。</span><span class="sxs-lookup"><span data-stu-id="4cb72-167">Do not verify whether an event is `Nothing` (null) before you call the `RaiseEvent` method.</span></span> <span data-ttu-id="4cb72-168">`RaiseEvent``Nothing`在引发事件之前进行检查。</span><span class="sxs-lookup"><span data-stu-id="4cb72-168">`RaiseEvent` checks for `Nothing` before it raises the event.</span></span>  
  
### <a name="using-shared-members"></a><span data-ttu-id="4cb72-169">使用共享成员</span><span class="sxs-lookup"><span data-stu-id="4cb72-169">Using Shared Members</span></span>  

 <span data-ttu-id="4cb72-170">`Shared`使用类名称（而不是从实例变量）调用成员。</span><span class="sxs-lookup"><span data-stu-id="4cb72-170">Call `Shared` members by using the class name, not from an instance variable.</span></span>  
  
### <a name="use-xml-literals"></a><span data-ttu-id="4cb72-171">使用 XML 文本</span><span class="sxs-lookup"><span data-stu-id="4cb72-171">Use XML Literals</span></span>  

 <span data-ttu-id="4cb72-172">XML 文本简化了在处理 XML (时遇到的最常见任务，例如，加载、查询和转换) 。</span><span class="sxs-lookup"><span data-stu-id="4cb72-172">XML literals simplify the most common tasks that you encounter when you work with XML (for example, load, query, and transform).</span></span> <span data-ttu-id="4cb72-173">当你用 XML 开发时，请遵循以下准则：</span><span class="sxs-lookup"><span data-stu-id="4cb72-173">When you develop with XML, follow these guidelines:</span></span>  
  
- <span data-ttu-id="4cb72-174">使用 XML 文本来创建 XML 文档和片段，而不是直接调用 XML Api。</span><span class="sxs-lookup"><span data-stu-id="4cb72-174">Use XML literals to create XML documents and fragments instead of calling XML APIs directly.</span></span>  
  
- <span data-ttu-id="4cb72-175">在文件或项目级别导入 XML 命名空间，以利用 XML 文本的性能优化。</span><span class="sxs-lookup"><span data-stu-id="4cb72-175">Import XML namespaces at the file or project level to take advantage of the performance optimizations for XML literals.</span></span>  
  
- <span data-ttu-id="4cb72-176">使用 XML 轴属性可以访问 XML 文档中的元素和属性。</span><span class="sxs-lookup"><span data-stu-id="4cb72-176">Use the XML axis properties to access elements and attributes in an XML document.</span></span>  
  
- <span data-ttu-id="4cb72-177">使用嵌入的表达式包含值和从现有值创建 XML，而不是使用 API 调用（如 `Add` 方法）：</span><span class="sxs-lookup"><span data-stu-id="4cb72-177">Use embedded expressions to include values and to create XML from existing values instead of using API calls such as the `Add` method:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#27)]  
  
### <a name="linq-queries"></a><span data-ttu-id="4cb72-178">LINQ 查询</span><span class="sxs-lookup"><span data-stu-id="4cb72-178">LINQ Queries</span></span>  
  
- <span data-ttu-id="4cb72-179">对查询变量使用有意义的名称：</span><span class="sxs-lookup"><span data-stu-id="4cb72-179">Use meaningful names for query variables:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#28)]  
  
- <span data-ttu-id="4cb72-180">为查询中的元素提供名称，以确保匿名类型的属性名称使用 Pascal 大小写正确地大写：</span><span class="sxs-lookup"><span data-stu-id="4cb72-180">Provide names for elements in a query to make sure that property names of anonymous types are correctly capitalized using Pascal casing:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#29)]  
  
- <span data-ttu-id="4cb72-181">如果结果中的属性名称模棱两可，请对属性重命名。</span><span class="sxs-lookup"><span data-stu-id="4cb72-181">Rename properties when the property names in the result would be ambiguous.</span></span> <span data-ttu-id="4cb72-182">例如，如果你的查询返回客户名称和订单 ID，请将它们重命名，而不是 `Name` `ID` 在结果中保留它们：</span><span class="sxs-lookup"><span data-stu-id="4cb72-182">For example, if your query returns a customer name and an order ID, rename them instead of leaving them as `Name` and `ID` in the result:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#30)]  
  
- <span data-ttu-id="4cb72-183">在查询变量和范围变量的声明中使用类型推理：</span><span class="sxs-lookup"><span data-stu-id="4cb72-183">Use type inference in the declaration of query variables and range variables:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#31)]  
  
- <span data-ttu-id="4cb72-184">对齐语句下的查询子句 `From` ：</span><span class="sxs-lookup"><span data-stu-id="4cb72-184">Align query clauses under the `From` statement:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#32)]  
  
- <span data-ttu-id="4cb72-185">在 `Where` 其他查询子句之前使用子句，以便后面的查询子句对筛选的数据集执行操作：</span><span class="sxs-lookup"><span data-stu-id="4cb72-185">Use `Where` clauses before other query clauses so that later query clauses operate on the filtered set of data:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#33)]  
  
- <span data-ttu-id="4cb72-186">使用 `Join` 子句显式定义联接运算，而不是使用 `Where` 子句隐式定义联接运算：</span><span class="sxs-lookup"><span data-stu-id="4cb72-186">Use the `Join` clause to explicitly define a join operation instead of using the `Where` clause to implicitly define a join operation:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#34)]  
  
## <a name="see-also"></a><span data-ttu-id="4cb72-187">请参阅</span><span class="sxs-lookup"><span data-stu-id="4cb72-187">See also</span></span>

- [<span data-ttu-id="4cb72-188">安全编码准则</span><span class="sxs-lookup"><span data-stu-id="4cb72-188">Secure Coding Guidelines</span></span>](../../../standard/security/secure-coding-guidelines.md)
