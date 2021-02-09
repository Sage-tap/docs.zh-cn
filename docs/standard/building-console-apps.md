---
description: 详细了解：.NET 中的控制台应用
title: 在 .NET 中创建控制台应用程序
ms.date: 03/30/2017
helpviewer_keywords:
- .NET, creating console applications
- application development [.NET], console
- console applications
ms.assetid: c21fb997-9f0e-40a5-8741-f73bba376bd8
ms.openlocfilehash: 9ebc0fbdc71cf0b6d30a07fc8a375899c5f55d52
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99676204"
---
# <a name="console-apps-in-net"></a><span data-ttu-id="00180-103">.NET 中的控制台应用</span><span class="sxs-lookup"><span data-stu-id="00180-103">Console apps in .NET</span></span>

<span data-ttu-id="00180-104">.NET 应用程序可以使用 <xref:System.Console?displayProperty=nameWithType> 类在控制台中读取和写入字符。</span><span class="sxs-lookup"><span data-stu-id="00180-104">.NET applications can use the <xref:System.Console?displayProperty=nameWithType> class to read characters from and write characters to the console.</span></span> <span data-ttu-id="00180-105">读取自控制台的数据是从标准输入流读取的，而写入到控制台的数据将写入标准输出流，并且写入控制台的错误数据将写入标准错误输出流。</span><span class="sxs-lookup"><span data-stu-id="00180-105">Data from the console is read from the standard input stream, data to the console is written to the standard output stream, and error data to the console is written to the standard error output stream.</span></span> <span data-ttu-id="00180-106">应用程序启动时，这些数据流会自动与控制台关联，并分别表示为 <xref:System.Console.In%2A>、<xref:System.Console.Out%2A> 和 <xref:System.Console.Error%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="00180-106">These streams are automatically associated with the console when the application starts and are presented as the <xref:System.Console.In%2A>, <xref:System.Console.Out%2A>, and <xref:System.Console.Error%2A> properties, respectively.</span></span>

<span data-ttu-id="00180-107"><xref:System.Console.In%2A?displayProperty=nameWithType> 属性的值是 <xref:System.IO.TextReader?displayProperty=nameWithType> 对象，而 <xref:System.Console.Out%2A?displayProperty=nameWithType> 和 <xref:System.Console.Error%2A?displayProperty=nameWithType> 属性的值都是 <xref:System.IO.TextWriter?displayProperty=nameWithType> 对象。</span><span class="sxs-lookup"><span data-stu-id="00180-107">The value of the <xref:System.Console.In%2A?displayProperty=nameWithType> property is a <xref:System.IO.TextReader?displayProperty=nameWithType> object, whereas the values of the <xref:System.Console.Out%2A?displayProperty=nameWithType> and <xref:System.Console.Error%2A?displayProperty=nameWithType> properties are <xref:System.IO.TextWriter?displayProperty=nameWithType> objects.</span></span> <span data-ttu-id="00180-108">你可以将这些属性与不表示控制台的流关联，以便可以将该流指向不同的输入位置或输出位置。</span><span class="sxs-lookup"><span data-stu-id="00180-108">You can associate these properties with streams that do not represent the console, making it possible for you to point the stream to a different location for input or output.</span></span> <span data-ttu-id="00180-109">例如，你可以通过将 <xref:System.Console.Out%2A?displayProperty=nameWithType> 属性设置为 <xref:System.IO.StreamWriter?displayProperty=nameWithType> 将输出重定向到一个文件，这将通过 <xref:System.Console.SetOut%2A?displayProperty=nameWithType> 方法封装 <xref:System.IO.FileStream?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="00180-109">For example, you can redirect the output to a file by setting the <xref:System.Console.Out%2A?displayProperty=nameWithType> property to a <xref:System.IO.StreamWriter?displayProperty=nameWithType>, which encapsulates a <xref:System.IO.FileStream?displayProperty=nameWithType> by means of the <xref:System.Console.SetOut%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="00180-110"><xref:System.Console.In%2A?displayProperty=nameWithType> 和 <xref:System.Console.Out%2A?displayProperty=nameWithType> 属性不需要引用相同流。</span><span class="sxs-lookup"><span data-stu-id="00180-110">The <xref:System.Console.In%2A?displayProperty=nameWithType> and <xref:System.Console.Out%2A?displayProperty=nameWithType> properties do not need to refer to the same stream.</span></span>

> [!NOTE]
> <span data-ttu-id="00180-111">有关生成控制台应用程序（包括 C#、Visual Basic 和 C++ 中的示例）的详细信息，请参阅 <xref:System.Console> 类文档。</span><span class="sxs-lookup"><span data-stu-id="00180-111">For more information about building console applications, including examples in C#, Visual Basic, and C++, see the documentation for the <xref:System.Console> class.</span></span>

<span data-ttu-id="00180-112">如果不存在控制台（比如在 Windows 窗体应用程序中），写入标准输出流的输出将不可见，因为没有可以将信息写入的控制台。</span><span class="sxs-lookup"><span data-stu-id="00180-112">If the console does not exist, for example, in a Windows Forms application, output written to the standard output stream will not be visible, because there is no console to write the information to.</span></span> <span data-ttu-id="00180-113">将信息写入不可访问的控制台不会引发异常。</span><span class="sxs-lookup"><span data-stu-id="00180-113">Writing information to an inaccessible console does not cause an exception to be raised.</span></span> <span data-ttu-id="00180-114">（例如在 Visual Studio 的项目属性页中，你始终可以将应用程序类型更改为“控制台应用程序”）。</span><span class="sxs-lookup"><span data-stu-id="00180-114">(You can always change the application type to **Console Application**, for example, in the project property pages in Visual Studio).</span></span>

<span data-ttu-id="00180-115">System.Console  类具有从控制台读取单独的字符或整行的方法。</span><span class="sxs-lookup"><span data-stu-id="00180-115">The **System.Console** class has methods that can read individual characters or entire lines from the console.</span></span> <span data-ttu-id="00180-116">其他方法转换数据和格式字符串，然后将设置了格式的字符串写入控制台。</span><span class="sxs-lookup"><span data-stu-id="00180-116">Other methods convert data and format strings, and then write the formatted strings to the console.</span></span> <span data-ttu-id="00180-117">有关设置字符串格式的详细信息，请参阅[格式设置类型](base-types/formatting-types.md)。</span><span class="sxs-lookup"><span data-stu-id="00180-117">For more information on formatting strings, see [Formatting types](base-types/formatting-types.md).</span></span>

> [!TIP]
> <span data-ttu-id="00180-118">控制台应用程序缺少在默认情况下启动的消息泵。</span><span class="sxs-lookup"><span data-stu-id="00180-118">Console applications lack a message pump that starts by default.</span></span> <span data-ttu-id="00180-119">因此，控制台调用 Microsoft Win32 计时器时可能会失败。</span><span class="sxs-lookup"><span data-stu-id="00180-119">Therefore, console calls to Microsoft Win32 timers might fail.</span></span>

## <a name="see-also"></a><span data-ttu-id="00180-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="00180-120">See also</span></span>

- <xref:System.Console?displayProperty=nameWithType>
- [<span data-ttu-id="00180-121">格式设置类型</span><span class="sxs-lookup"><span data-stu-id="00180-121">Formatting Types</span></span>](base-types/formatting-types.md)
