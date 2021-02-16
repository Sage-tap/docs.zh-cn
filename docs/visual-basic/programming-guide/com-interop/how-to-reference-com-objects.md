---
description: 了解有关详细信息，请参阅如何：从 Visual Basic 引用 COM 对象
title: 如何：从 Visual Basic 中引用 COM 对象
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], referencing COM objects
- referencing objects, COM objects from Visual Basic
- objects [Visual Basic], referencing
- COM objects, referencing
- interop assemblies
ms.assetid: 9c518fb4-27d9-4112-9e6a-5a7d0210af6f
ms.openlocfilehash: f0c08e5be9144bdefc3fe0b4609bad2421889d52
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100477562"
---
# <a name="how-to-reference-com-objects-from-visual-basic"></a><span data-ttu-id="489e9-103">如何：从 Visual Basic 中引用 COM 对象</span><span class="sxs-lookup"><span data-stu-id="489e9-103">How to: Reference COM Objects from Visual Basic</span></span>

<span data-ttu-id="489e9-104">在 Visual Basic 中，添加对具有类型库的 COM 对象的引用需要为 COM 库创建互操作程序集。</span><span class="sxs-lookup"><span data-stu-id="489e9-104">In Visual Basic, adding references to COM objects that have type libraries requires the creation of an interop assembly for the COM library.</span></span> <span data-ttu-id="489e9-105">对 COM 对象成员的引用将路由到互操作程序集，然后转发到实际的 COM 对象。</span><span class="sxs-lookup"><span data-stu-id="489e9-105">References to the members of the COM object are routed to the interop assembly and then forwarded to the actual COM object.</span></span> <span data-ttu-id="489e9-106">将 COM 对象的响应路由到互操作程序集并转发到 .NET Framework 应用程序。</span><span class="sxs-lookup"><span data-stu-id="489e9-106">Responses from the COM object are routed to the interop assembly and forwarded to your .NET Framework application.</span></span>  
  
 <span data-ttu-id="489e9-107">通过在 .NET 程序集中嵌入 COM 对象的类型信息，可以引用 COM 对象，而无需使用互操作程序集。</span><span class="sxs-lookup"><span data-stu-id="489e9-107">You can reference a COM object without using an interop assembly by embedding the type information for the COM object in a .NET assembly.</span></span> <span data-ttu-id="489e9-108">若要嵌入类型信息，请将对 `Embed Interop Types` COM 对象的引用的属性设置为 `True` 。</span><span class="sxs-lookup"><span data-stu-id="489e9-108">To embed type information, set the `Embed Interop Types` property to `True` for the reference to the COM object.</span></span> <span data-ttu-id="489e9-109">如果要使用命令行编译器进行编译，请使用 `/link` 选项来引用 COM 库。</span><span class="sxs-lookup"><span data-stu-id="489e9-109">If you are compiling by using the command-line compiler, use the `/link` option to reference the COM library.</span></span> <span data-ttu-id="489e9-110">有关详细信息，请参阅 [-link (Visual Basic) ](../../reference/command-line-compiler/link.md)。</span><span class="sxs-lookup"><span data-stu-id="489e9-110">For more information, see [-link (Visual Basic)](../../reference/command-line-compiler/link.md).</span></span>  
  
 <span data-ttu-id="489e9-111">从集成开发环境 (IDE) 添加对类型库的引用时，Visual Basic 会自动创建互操作程序集。</span><span class="sxs-lookup"><span data-stu-id="489e9-111">Visual Basic automatically creates interop assemblies when you add a reference to a type library from the integrated development environment (IDE).</span></span> <span data-ttu-id="489e9-112">在命令行中工作时，可以使用 Tlbimp 实用工具手动创建互操作程序集。</span><span class="sxs-lookup"><span data-stu-id="489e9-112">When working from the command line, you can use the Tlbimp utility to manually create interop assemblies.</span></span>  
  
### <a name="to-add-references-to-com-objects"></a><span data-ttu-id="489e9-113">添加对 COM 对象的引用</span><span class="sxs-lookup"><span data-stu-id="489e9-113">To add references to COM objects</span></span>  
  
1. <span data-ttu-id="489e9-114">在 " **项目** " 菜单上，选择 " **添加引用** "，然后单击对话框中的 " **COM** " 选项卡。</span><span class="sxs-lookup"><span data-stu-id="489e9-114">On the **Project** menu, choose **Add Reference** and then click the **COM** tab in the dialog box.</span></span>  
  
2. <span data-ttu-id="489e9-115">从 COM 对象列表中选择要使用的组件。</span><span class="sxs-lookup"><span data-stu-id="489e9-115">Select the component you want to use from the list of COM objects.</span></span>  
  
3. <span data-ttu-id="489e9-116">若要简化对互操作程序集的访问，请将 `Imports` 语句添加到要在其中使用 COM 对象的类或模块的顶部。</span><span class="sxs-lookup"><span data-stu-id="489e9-116">To simplify access to the interop assembly, add an `Imports` statement to the top of the class or module in which you will use the COM object.</span></span> <span data-ttu-id="489e9-117">例如，下面的代码示例导入 `INKEDLib` 库中引用的对象的命名空间 `Microsoft InkEdit Control 1.0` 。</span><span class="sxs-lookup"><span data-stu-id="489e9-117">For example, the following code example imports the namespace `INKEDLib` for objects referenced in the `Microsoft InkEdit Control 1.0` library.</span></span>  
  
     [!code-vb[VbVbalrInterop#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#40)]  
  
### <a name="to-create-an-interop-assembly-using-tlbimp"></a><span data-ttu-id="489e9-118">使用 Tlbimp 创建互操作程序集</span><span class="sxs-lookup"><span data-stu-id="489e9-118">To create an interop assembly using Tlbimp</span></span>  
  
1. <span data-ttu-id="489e9-119">将 Tlbimp 的位置添加到搜索路径中（如果它不在搜索路径中），并且当前不在该位置的目录中。</span><span class="sxs-lookup"><span data-stu-id="489e9-119">Add the location of Tlbimp to the search path, if it is not already part of the search path and you are not currently in the directory where it is located.</span></span>  
  
2. <span data-ttu-id="489e9-120">从命令提示符调用 Tlbimp，提供以下信息：</span><span class="sxs-lookup"><span data-stu-id="489e9-120">Call Tlbimp from a command prompt, providing the following information:</span></span>  
  
    - <span data-ttu-id="489e9-121">包含类型库的 DLL 的名称和位置</span><span class="sxs-lookup"><span data-stu-id="489e9-121">Name and location of the DLL that contains the type library</span></span>  
  
    - <span data-ttu-id="489e9-122">应放置信息的命名空间的名称和位置</span><span class="sxs-lookup"><span data-stu-id="489e9-122">Name and location of the namespace where the information should be placed</span></span>  
  
    - <span data-ttu-id="489e9-123">目标互操作程序集的名称和位置</span><span class="sxs-lookup"><span data-stu-id="489e9-123">Name and location of the target interop assembly</span></span>  
  
     <span data-ttu-id="489e9-124">以下代码提供了一个示例：</span><span class="sxs-lookup"><span data-stu-id="489e9-124">The following code provides an example:</span></span>  
  
    ```console  
    Tlbimp test3.dll /out:NameSpace1 /out:Interop1.dll  
    ```  
  
     <span data-ttu-id="489e9-125">可以使用 Tlbimp 为类型库创建互操作程序集，即使对于未注册的 COM 对象也是如此。</span><span class="sxs-lookup"><span data-stu-id="489e9-125">You can use Tlbimp to create interop assemblies for type libraries, even for unregistered COM objects.</span></span> <span data-ttu-id="489e9-126">但是，互操作程序集所引用的 COM 对象必须在要使用它们的计算机上正确注册。</span><span class="sxs-lookup"><span data-stu-id="489e9-126">However, the COM objects referred to by interop assemblies must be properly registered on the computer where they are to be used.</span></span> <span data-ttu-id="489e9-127">你可以使用 Windows 操作系统随附的 Regsvr32 实用程序来注册 COM 对象。</span><span class="sxs-lookup"><span data-stu-id="489e9-127">You can register a COM object by using the Regsvr32 utility included with the Windows operating system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="489e9-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="489e9-128">See also</span></span>

- [<span data-ttu-id="489e9-129">COM 互操作</span><span class="sxs-lookup"><span data-stu-id="489e9-129">COM Interop</span></span>](index.md)
- [<span data-ttu-id="489e9-130">Tlbimp.exe（类型库导入程序）</span><span class="sxs-lookup"><span data-stu-id="489e9-130">Tlbimp.exe (Type Library Importer)</span></span>](../../../framework/tools/tlbimp-exe-type-library-importer.md)
- [<span data-ttu-id="489e9-131">Tlbexp.exe（类型库导出程序）</span><span class="sxs-lookup"><span data-stu-id="489e9-131">Tlbexp.exe (Type Library Exporter)</span></span>](../../../framework/tools/tlbexp-exe-type-library-exporter.md)
- [<span data-ttu-id="489e9-132">演练：使用 COM 对象实现继承</span><span class="sxs-lookup"><span data-stu-id="489e9-132">Walkthrough: Implementing Inheritance with COM Objects</span></span>](walkthrough-implementing-inheritance-with-com-objects.md)
- [<span data-ttu-id="489e9-133">互操作性疑难解答</span><span class="sxs-lookup"><span data-stu-id="489e9-133">Troubleshooting Interoperability</span></span>](troubleshooting-interoperability.md)
- [<span data-ttu-id="489e9-134">Imports 语句（.NET 命名空间和类型）</span><span class="sxs-lookup"><span data-stu-id="489e9-134">Imports Statement (.NET Namespace and Type)</span></span>](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
