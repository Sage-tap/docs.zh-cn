---
description: '了解详细信息：调用方信息 (Visual Basic) '
title: 调用方信息
ms.date: 07/20/2015
ms.assetid: 15d556eb-4d0c-4497-98a3-7f60abb7d6a1
ms.openlocfilehash: bcb4f553a9840a76f24825c3c2b7e2e98914abc2
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100437704"
---
# <a name="caller-information-visual-basic"></a><span data-ttu-id="6e4f4-103">调用方信息 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e4f4-103">Caller Information (Visual Basic)</span></span>

<span data-ttu-id="6e4f4-104">通过使用调用方信息特性，可获取有关方法的调用方的信息。</span><span class="sxs-lookup"><span data-stu-id="6e4f4-104">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="6e4f4-105">可以获取源代码的文件路径、源代码中的行号和调用方的成员名称。</span><span class="sxs-lookup"><span data-stu-id="6e4f4-105">You can obtain file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="6e4f4-106">此信息有助于跟踪、调试和创建诊断工具。</span><span class="sxs-lookup"><span data-stu-id="6e4f4-106">This information is helpful for tracing, debugging, and creating diagnostic tools.</span></span>  
  
 <span data-ttu-id="6e4f4-107">若要获取此信息，可以使用应用于可选参数的特性，每个特性都具有默认值。</span><span class="sxs-lookup"><span data-stu-id="6e4f4-107">To obtain this information, you use attributes that are applied to optional parameters, each of which has a default value.</span></span> <span data-ttu-id="6e4f4-108">下表列出在 <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> 命名空间中定义的调用方信息特性：</span><span class="sxs-lookup"><span data-stu-id="6e4f4-108">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>  
  
|<span data-ttu-id="6e4f4-109">特性</span><span class="sxs-lookup"><span data-stu-id="6e4f4-109">Attribute</span></span>|<span data-ttu-id="6e4f4-110">说明</span><span class="sxs-lookup"><span data-stu-id="6e4f4-110">Description</span></span>|<span data-ttu-id="6e4f4-111">类型</span><span class="sxs-lookup"><span data-stu-id="6e4f4-111">Type</span></span>|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="6e4f4-112">包含调用方的源文件的完整路径。</span><span class="sxs-lookup"><span data-stu-id="6e4f4-112">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="6e4f4-113">这是编译时的文件路径。</span><span class="sxs-lookup"><span data-stu-id="6e4f4-113">This is the file path at compile time.</span></span>|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="6e4f4-114">源文件中调用方法的行号。</span><span class="sxs-lookup"><span data-stu-id="6e4f4-114">Line number in the source file at which the method is called.</span></span>|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="6e4f4-115">调用方的方法或属性名称。</span><span class="sxs-lookup"><span data-stu-id="6e4f4-115">Method or property name of the caller.</span></span> <span data-ttu-id="6e4f4-116">请参阅本主题后面的[成员名称](#MEMBERNAMES)。</span><span class="sxs-lookup"><span data-stu-id="6e4f4-116">See [Member Names](#MEMBERNAMES) later in this topic.</span></span>|`String`|  
  
## <a name="example"></a><span data-ttu-id="6e4f4-117">示例</span><span class="sxs-lookup"><span data-stu-id="6e4f4-117">Example</span></span>  

 <span data-ttu-id="6e4f4-118">下面的示例演示如何使用调用方信息特性。</span><span class="sxs-lookup"><span data-stu-id="6e4f4-118">The following example shows how to use Caller Info attributes.</span></span> <span data-ttu-id="6e4f4-119">每次调用 `TraceMessage` 方法时，调用方信息将替换为可选参数的变量。</span><span class="sxs-lookup"><span data-stu-id="6e4f4-119">On each call to the `TraceMessage` method, the caller information is substituted as arguments to the optional parameters.</span></span>  
  
```vb  
Private Sub DoProcessing()  
    TraceMessage("Something happened.")  
End Sub  
  
Public Sub TraceMessage(message As String,  
        <System.Runtime.CompilerServices.CallerMemberName> Optional memberName As String = Nothing,  
        <System.Runtime.CompilerServices.CallerFilePath> Optional sourcefilePath As String = Nothing,  
        <System.Runtime.CompilerServices.CallerLineNumber()> Optional sourceLineNumber As Integer = 0)  
  
    System.Diagnostics.Trace.WriteLine("message: " & message)  
    System.Diagnostics.Trace.WriteLine("member name: " & memberName)  
    System.Diagnostics.Trace.WriteLine("source file path: " & sourcefilePath)  
    System.Diagnostics.Trace.WriteLine("source line number: " & sourceLineNumber)  
End Sub  
  
' Sample output:  
'   message: Something happened.  
'   member name: DoProcessing  
'   source file path: C:\Users\username\Documents\Visual Studio 2012\Projects\CallerInfoVB\CallerInfoVB\Form1.vb  
'   source line number: 15  
```  
  
## <a name="remarks"></a><span data-ttu-id="6e4f4-120">备注</span><span class="sxs-lookup"><span data-stu-id="6e4f4-120">Remarks</span></span>  

 <span data-ttu-id="6e4f4-121">你必须为每个可选参数指定显式默认值。</span><span class="sxs-lookup"><span data-stu-id="6e4f4-121">You must specify an explicit default value for each optional parameter.</span></span> <span data-ttu-id="6e4f4-122">不能将调用方信息特性应用于未指定为可选的参数。</span><span class="sxs-lookup"><span data-stu-id="6e4f4-122">You can't apply Caller Info attributes to parameters that aren't specified as optional.</span></span>  
  
 <span data-ttu-id="6e4f4-123">调用方信息特性不会使参数成为可选参数。</span><span class="sxs-lookup"><span data-stu-id="6e4f4-123">The Caller Info attributes don't make a parameter optional.</span></span> <span data-ttu-id="6e4f4-124">相反，它们会在忽略此参数时影响传入的默认值。</span><span class="sxs-lookup"><span data-stu-id="6e4f4-124">Instead, they affect the default value that's passed in when the argument is omitted.</span></span>  
  
 <span data-ttu-id="6e4f4-125">在编译时，调用方信息值将作为文本传入中间语言 (IL)。</span><span class="sxs-lookup"><span data-stu-id="6e4f4-125">Caller Info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="6e4f4-126">与异常的 <xref:System.Exception.StackTrace%2A> 属性的结果不同，这些结果不受模糊处理的影响。</span><span class="sxs-lookup"><span data-stu-id="6e4f4-126">Unlike the results of the <xref:System.Exception.StackTrace%2A> property for exceptions, the results aren't affected by obfuscation.</span></span>  
  
 <span data-ttu-id="6e4f4-127">你可显式提供可选参数来控制调用方信息或隐藏调用方信息。</span><span class="sxs-lookup"><span data-stu-id="6e4f4-127">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>  
  
### <a name="member-names"></a><a name="MEMBERNAMES"></a> <span data-ttu-id="6e4f4-128">成员名称</span><span class="sxs-lookup"><span data-stu-id="6e4f4-128">Member Names</span></span>  

 <span data-ttu-id="6e4f4-129">可以使用 `CallerMemberName` 特性来避免将成员名称指定为所调用的方法的 `String` 参数。</span><span class="sxs-lookup"><span data-stu-id="6e4f4-129">You can use the `CallerMemberName` attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="6e4f4-130">通过使用这种技术，可以避免“重命名重构”  不更改 `String` 值的问题。</span><span class="sxs-lookup"><span data-stu-id="6e4f4-130">By using this technique, you avoid the problem that **Rename Refactoring** doesn't change the `String` values.</span></span> <span data-ttu-id="6e4f4-131">此好处对于以下任务特别有用：</span><span class="sxs-lookup"><span data-stu-id="6e4f4-131">This benefit is especially useful for the following tasks:</span></span>  
  
- <span data-ttu-id="6e4f4-132">使用跟踪和诊断例程。</span><span class="sxs-lookup"><span data-stu-id="6e4f4-132">Using tracing and diagnostic routines.</span></span>  
  
- <span data-ttu-id="6e4f4-133">在绑定数据时实现 <xref:System.ComponentModel.INotifyPropertyChanged> 接口。</span><span class="sxs-lookup"><span data-stu-id="6e4f4-133">Implementing the <xref:System.ComponentModel.INotifyPropertyChanged> interface when binding data.</span></span> <span data-ttu-id="6e4f4-134">此接口允许对象的属性通知绑定控件该属性已更改，以便此控件能够显示更新的信息。</span><span class="sxs-lookup"><span data-stu-id="6e4f4-134">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="6e4f4-135">如果没有 `CallerMemberName` 特性，则必须将属性名称指定为文本。</span><span class="sxs-lookup"><span data-stu-id="6e4f4-135">Without the `CallerMemberName` attribute, you must specify the property name as a literal.</span></span>  
  
 <span data-ttu-id="6e4f4-136">以下图表显示在使用 `CallerMemberName` 特性时返回的成员名称。</span><span class="sxs-lookup"><span data-stu-id="6e4f4-136">The following chart shows the member names that are returned when you use the `CallerMemberName` attribute.</span></span>  
  
|<span data-ttu-id="6e4f4-137">调用发生中</span><span class="sxs-lookup"><span data-stu-id="6e4f4-137">Calls occurs within</span></span>|<span data-ttu-id="6e4f4-138">成员名称结果</span><span class="sxs-lookup"><span data-stu-id="6e4f4-138">Member name result</span></span>|  
|-------------------------|------------------------|  
|<span data-ttu-id="6e4f4-139">方法、属性或事件</span><span class="sxs-lookup"><span data-stu-id="6e4f4-139">Method, property, or event</span></span>|<span data-ttu-id="6e4f4-140">从中发起调用的方法、属性或事件的名称。</span><span class="sxs-lookup"><span data-stu-id="6e4f4-140">The name of the method, property, or event from which the call originated.</span></span>|  
|<span data-ttu-id="6e4f4-141">构造函数</span><span class="sxs-lookup"><span data-stu-id="6e4f4-141">Constructor</span></span>|<span data-ttu-id="6e4f4-142">字符串“.ctor”</span><span class="sxs-lookup"><span data-stu-id="6e4f4-142">The string ".ctor"</span></span>|  
|<span data-ttu-id="6e4f4-143">静态构造函数</span><span class="sxs-lookup"><span data-stu-id="6e4f4-143">Static constructor</span></span>|<span data-ttu-id="6e4f4-144">字符串“.cctor”</span><span class="sxs-lookup"><span data-stu-id="6e4f4-144">The string ".cctor"</span></span>|  
|<span data-ttu-id="6e4f4-145">析构函数</span><span class="sxs-lookup"><span data-stu-id="6e4f4-145">Destructor</span></span>|<span data-ttu-id="6e4f4-146">字符串“Finalize”</span><span class="sxs-lookup"><span data-stu-id="6e4f4-146">The string "Finalize"</span></span>|  
|<span data-ttu-id="6e4f4-147">用户定义的运算符或转换</span><span class="sxs-lookup"><span data-stu-id="6e4f4-147">User-defined operators or conversions</span></span>|<span data-ttu-id="6e4f4-148">为成员生成的名称，例如，“op_Addition”。</span><span class="sxs-lookup"><span data-stu-id="6e4f4-148">The generated name for the member, for example, "op_Addition".</span></span>|  
|<span data-ttu-id="6e4f4-149">特性构造函数</span><span class="sxs-lookup"><span data-stu-id="6e4f4-149">Attribute constructor</span></span>|<span data-ttu-id="6e4f4-150">要应用特性的成员的名称。</span><span class="sxs-lookup"><span data-stu-id="6e4f4-150">The name of the member to which the attribute is applied.</span></span> <span data-ttu-id="6e4f4-151">如果该特性是成员中的任何元素（如参数、返回值或泛型参数），则此结果是与该元素关联的成员的名称。</span><span class="sxs-lookup"><span data-stu-id="6e4f4-151">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|  
|<span data-ttu-id="6e4f4-152">无包含的成员（例如，程序集级别或应用于类型的特性）</span><span class="sxs-lookup"><span data-stu-id="6e4f4-152">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="6e4f4-153">可选参数的默认值。</span><span class="sxs-lookup"><span data-stu-id="6e4f4-153">The default value of the optional parameter.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6e4f4-154">请参阅</span><span class="sxs-lookup"><span data-stu-id="6e4f4-154">See also</span></span>

- [<span data-ttu-id="6e4f4-155">特性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e4f4-155">Attributes (Visual Basic)</span></span>](../../language-reference/attributes.md)
- [<span data-ttu-id="6e4f4-156">常见特性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e4f4-156">Common Attributes (Visual Basic)</span></span>](attributes/common-attributes.md)
- [<span data-ttu-id="6e4f4-157">可选参数</span><span class="sxs-lookup"><span data-stu-id="6e4f4-157">Optional Parameters</span></span>](../language-features/procedures/optional-parameters.md)
- [<span data-ttu-id="6e4f4-158">Visual Basic 的编程概念 () </span><span class="sxs-lookup"><span data-stu-id="6e4f4-158">Programming Concepts (Visual Basic)</span></span>](index.md)
