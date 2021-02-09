---
description: 详细了解：操作说明：在 Visual Basic 中将字符串发送到串行端口
title: 如何：将字符串发送到串行端口
ms.date: 07/20/2015
helpviewer_keywords:
- ports, sending strings to
- strings [Visual Basic], sending to serial ports
- My.Computer.Ports object
- serial ports, sending strings to
ms.assetid: 6ebf46cd-b2d0-4b2c-9a1f-be177b22ad52
ms.openlocfilehash: 66dedaab05090af2659701e57b37b4813447b8ef
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666480"
---
# <a name="how-to-send-strings-to-serial-ports-in-visual-basic"></a><span data-ttu-id="bd3c3-103">如何：在 Visual Basic 中将字符串发送到串行端口</span><span class="sxs-lookup"><span data-stu-id="bd3c3-103">How to: Send Strings to Serial Ports in Visual Basic</span></span>

<span data-ttu-id="bd3c3-104">本主题介绍在 Visual Basic 中如何使用 `My.Computer.Ports` 将字符串发送到计算机的串行端口。</span><span class="sxs-lookup"><span data-stu-id="bd3c3-104">This topic describes how to use `My.Computer.Ports` to send strings to the computer's serial ports in Visual Basic.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd3c3-105">示例</span><span class="sxs-lookup"><span data-stu-id="bd3c3-105">Example</span></span>  

 <span data-ttu-id="bd3c3-106">本示例将字符串发送到 COM1 串行端口。</span><span class="sxs-lookup"><span data-stu-id="bd3c3-106">This example sends a string to the COM1 serial port.</span></span> <span data-ttu-id="bd3c3-107">你可能需要使用计算机上的其他串行端口。</span><span class="sxs-lookup"><span data-stu-id="bd3c3-107">You may need to use a different serial port on your computer.</span></span>  
  
 <span data-ttu-id="bd3c3-108">使用 `My.Computer.Ports.OpenSerialPort` 方法获取对端口的引用。</span><span class="sxs-lookup"><span data-stu-id="bd3c3-108">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="bd3c3-109">有关详细信息，请参阅 <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>。</span><span class="sxs-lookup"><span data-stu-id="bd3c3-109">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
 <span data-ttu-id="bd3c3-110">`Using` 块允许应用程序在即使会生成异常的情况下也关闭串行端口。</span><span class="sxs-lookup"><span data-stu-id="bd3c3-110">The `Using` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="bd3c3-111">操作串行端口的所有代码都应出现在此块中，或者出现在 `Try...Catch...Finally` 块中。</span><span class="sxs-lookup"><span data-stu-id="bd3c3-111">All code that manipulates the serial port should appear within this block or within a `Try...Catch...Finally` block.</span></span>  
  
 <span data-ttu-id="bd3c3-112"><xref:System.IO.Ports.SerialPort.WriteLine%2A> 方法将数据发送到串行端口。</span><span class="sxs-lookup"><span data-stu-id="bd3c3-112">The <xref:System.IO.Ports.SerialPort.WriteLine%2A> method sends the data to the serial port.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#33)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bd3c3-113">编译代码</span><span class="sxs-lookup"><span data-stu-id="bd3c3-113">Compiling the Code</span></span>  
  
- <span data-ttu-id="bd3c3-114">本示例假定计算机正在使用 `COM1`。</span><span class="sxs-lookup"><span data-stu-id="bd3c3-114">This example assumes the computer is using `COM1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="bd3c3-115">可靠编程</span><span class="sxs-lookup"><span data-stu-id="bd3c3-115">Robust Programming</span></span>  

 <span data-ttu-id="bd3c3-116">本示例假定计算机正在使用 `COM1`；为了获得更大的灵活性，代码应允许用户从可用端口列表中选择所需的串行端口。</span><span class="sxs-lookup"><span data-stu-id="bd3c3-116">This example assumes the computer is using `COM1`; for more flexibility, the code should allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="bd3c3-117">有关详细信息，请参阅[如何：显示可用的串行端口](how-to-show-available-serial-ports.md)。</span><span class="sxs-lookup"><span data-stu-id="bd3c3-117">For more information, see [How to: Show Available Serial Ports](how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="bd3c3-118">本示例使用 `Using` 块来确保应用程序在即使会引发异常的情况下也关闭端口。</span><span class="sxs-lookup"><span data-stu-id="bd3c3-118">This example uses a `Using` block to make sure that the application closes the port even if it throws an exception.</span></span> <span data-ttu-id="bd3c3-119">有关详细信息，请参阅 [Using 语句](../../../language-reference/statements/using-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="bd3c3-119">For more information, see [Using Statement](../../../language-reference/statements/using-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd3c3-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bd3c3-120">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [<span data-ttu-id="bd3c3-121">如何：使用连接到串行端口的调制解调器拨号</span><span class="sxs-lookup"><span data-stu-id="bd3c3-121">How to: Dial Modems Attached to Serial Ports</span></span>](how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="bd3c3-122">如何：显示可用的串行端口</span><span class="sxs-lookup"><span data-stu-id="bd3c3-122">How to: Show Available Serial Ports</span></span>](how-to-show-available-serial-ports.md)
