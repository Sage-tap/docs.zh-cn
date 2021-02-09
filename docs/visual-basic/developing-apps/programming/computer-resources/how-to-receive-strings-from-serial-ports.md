---
description: 详细了解：操作说明：在 Visual Basic 中从串行端口接收字符串
title: 如何：从串行端口接收字符串
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, retrieving strings
- strings [Visual Basic], retrieving from serial ports
- My.Resources object
ms.assetid: 8371ce2c-e1c7-476b-a86d-9afc2614b6b7
ms.openlocfilehash: 5e6de24392c6102b6dc613d909c827cc32f513d0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666532"
---
# <a name="how-to-receive-strings-from-serial-ports-in-visual-basic"></a><span data-ttu-id="ccf60-103">如何：在 Visual Basic 中从串行端口接收字符串</span><span class="sxs-lookup"><span data-stu-id="ccf60-103">How to: Receive Strings From Serial Ports in Visual Basic</span></span>

<span data-ttu-id="ccf60-104">本主题介绍在 Visual Basic 中如何使用 `My.Computer.Ports` 从计算机的串行端口接收字符串。</span><span class="sxs-lookup"><span data-stu-id="ccf60-104">This topic describes how to use `My.Computer.Ports` to receive strings from the computer's serial ports in Visual Basic.</span></span>  
  
### <a name="to-receive-strings-from-the-serial-port"></a><span data-ttu-id="ccf60-105">从串行端口接收字符串</span><span class="sxs-lookup"><span data-stu-id="ccf60-105">To receive strings from the serial port</span></span>  
  
1. <span data-ttu-id="ccf60-106">初始化返回字符串。</span><span class="sxs-lookup"><span data-stu-id="ccf60-106">Initialize the return string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#38)]  
  
2. <span data-ttu-id="ccf60-107">确定应提供字符串的串行端口。</span><span class="sxs-lookup"><span data-stu-id="ccf60-107">Determine which serial port should provide the strings.</span></span> <span data-ttu-id="ccf60-108">此示例假定它是 `COM1`。</span><span class="sxs-lookup"><span data-stu-id="ccf60-108">This example assumes it is `COM1`.</span></span>  
  
3. <span data-ttu-id="ccf60-109">使用 `My.Computer.Ports.OpenSerialPort` 方法获取对端口的引用。</span><span class="sxs-lookup"><span data-stu-id="ccf60-109">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="ccf60-110">有关详细信息，请参阅 <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>。</span><span class="sxs-lookup"><span data-stu-id="ccf60-110">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
     <span data-ttu-id="ccf60-111">`Try...Catch...Finally` 块允许应用程序在即使会生成异常的情况下也关闭串行端口。</span><span class="sxs-lookup"><span data-stu-id="ccf60-111">The `Try...Catch...Finally` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="ccf60-112">操作串行端口的所有代码都应出现在此块中。</span><span class="sxs-lookup"><span data-stu-id="ccf60-112">All code that manipulates the serial port should appear within this block.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#39)]  
  
4. <span data-ttu-id="ccf60-113">创建 `Do` 循环，用于读取文本行，直到没有更多行可用。</span><span class="sxs-lookup"><span data-stu-id="ccf60-113">Create a `Do` loop for reading lines of text until no more lines are available.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#40)]  
  
5. <span data-ttu-id="ccf60-114">使用 <xref:System.IO.Ports.SerialPort.ReadLine> 方法来从串行端口读取下一个可用的文本行。</span><span class="sxs-lookup"><span data-stu-id="ccf60-114">Use the <xref:System.IO.Ports.SerialPort.ReadLine> method to read the next available line of text from the serial port.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#41)]  
  
6. <span data-ttu-id="ccf60-115">使用 `If` 语句可确定 <xref:System.IO.Ports.SerialPort.ReadLine> 方法是否返回 `Nothing`（这意味着没有更多文本可用）。</span><span class="sxs-lookup"><span data-stu-id="ccf60-115">Use an `If` statement to determine if the <xref:System.IO.Ports.SerialPort.ReadLine> method returns `Nothing` (which means no more text is available).</span></span> <span data-ttu-id="ccf60-116">如果它未返回 `Nothing`，则退出 `Do` 循环。</span><span class="sxs-lookup"><span data-stu-id="ccf60-116">If it does return `Nothing`, exit the `Do` loop.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#42)]  
  
7. <span data-ttu-id="ccf60-117">向 `If` 语句添加 `Else` 块以处理实际读取字符串的情况。</span><span class="sxs-lookup"><span data-stu-id="ccf60-117">Add an `Else` block to the `If` statement to handle the case if the string is actually read.</span></span> <span data-ttu-id="ccf60-118">该块将来自串行端口的字符串追加到返回字符串。</span><span class="sxs-lookup"><span data-stu-id="ccf60-118">The block appends the string from the serial port to the return string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#43)]  
  
8. <span data-ttu-id="ccf60-119">返回字符串。</span><span class="sxs-lookup"><span data-stu-id="ccf60-119">Return the string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#44)]  
  
## <a name="example"></a><span data-ttu-id="ccf60-120">示例</span><span class="sxs-lookup"><span data-stu-id="ccf60-120">Example</span></span>  

 [!code-vb[VbVbalrMyComputer#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#37)]  
  
 <span data-ttu-id="ccf60-121">此代码示例也可作为 IntelliSense 代码片段。</span><span class="sxs-lookup"><span data-stu-id="ccf60-121">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="ccf60-122">它位于代码片段选取器的“连接和网络”中。</span><span class="sxs-lookup"><span data-stu-id="ccf60-122">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="ccf60-123">有关详细信息，请参阅[代码片段](/visualstudio/ide/code-snippets)。</span><span class="sxs-lookup"><span data-stu-id="ccf60-123">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ccf60-124">编译代码</span><span class="sxs-lookup"><span data-stu-id="ccf60-124">Compiling the Code</span></span>  

 <span data-ttu-id="ccf60-125">本示例假定计算机正在使用 `COM1`。</span><span class="sxs-lookup"><span data-stu-id="ccf60-125">This example assumes the computer is using `COM1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="ccf60-126">可靠编程</span><span class="sxs-lookup"><span data-stu-id="ccf60-126">Robust Programming</span></span>  

 <span data-ttu-id="ccf60-127">本示例假定计算机正在使用 `COM1`。</span><span class="sxs-lookup"><span data-stu-id="ccf60-127">This example assumes the computer is using `COM1`.</span></span> <span data-ttu-id="ccf60-128">为了获得更大的灵活性，代码应允许用户从可用端口列表中选择所需的串行端口。</span><span class="sxs-lookup"><span data-stu-id="ccf60-128">For more flexibility, the code should allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="ccf60-129">有关详细信息，请参阅[如何：显示可用的串行端口](how-to-show-available-serial-ports.md)。</span><span class="sxs-lookup"><span data-stu-id="ccf60-129">For more information, see [How to: Show Available Serial Ports](how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="ccf60-130">此示例使用 `Try...Catch...Finally` 块确保应用程序关闭端口以及捕获任何超时异常。</span><span class="sxs-lookup"><span data-stu-id="ccf60-130">This example uses a `Try...Catch...Finally` block to make sure that the application closes the port and to catch any timeout exceptions.</span></span> <span data-ttu-id="ccf60-131">有关详细信息，请参阅 [Try...Catch...Finally 语句](../../../language-reference/statements/try-catch-finally-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="ccf60-131">For more information, see [Try...Catch...Finally Statement](../../../language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccf60-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ccf60-132">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [<span data-ttu-id="ccf60-133">如何：使用连接到串行端口的调制解调器拨号</span><span class="sxs-lookup"><span data-stu-id="ccf60-133">How to: Dial Modems Attached to Serial Ports</span></span>](how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="ccf60-134">如何：将字符串发送到串行端口</span><span class="sxs-lookup"><span data-stu-id="ccf60-134">How to: Send Strings to Serial Ports</span></span>](how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="ccf60-135">如何：显示可用的串行端口</span><span class="sxs-lookup"><span data-stu-id="ccf60-135">How to: Show Available Serial Ports</span></span>](how-to-show-available-serial-ports.md)
