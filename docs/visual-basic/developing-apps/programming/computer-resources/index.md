---
description: 详细了解：访问计算机资源 (Visual Basic)
title: 访问计算机资源
ms.date: 07/20/2015
helpviewer_keywords:
- computer resources [Visual Basic]
- My.Computer object [Visual Basic], tasks
- computer resources [Visual Basic], accessing
ms.assetid: 75b81c88-f7c0-46e0-95c8-0c006d2120f9
ms.openlocfilehash: 20b91557bb5940be048f9c38e03b087c07f96c85
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792331"
---
# <a name="accessing-computer-resources-visual-basic"></a><span data-ttu-id="91019-103">访问计算机资源 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="91019-103">Accessing computer resources (Visual Basic)</span></span>

<span data-ttu-id="91019-104">`My.Computer` 对象是 `My` 中的三个中心对象之一，提供对信息和常用功能的访问权限。</span><span class="sxs-lookup"><span data-stu-id="91019-104">The `My.Computer` object is one of the three central objects in `My`, providing access to information and commonly used functionality.</span></span> <span data-ttu-id="91019-105">`My.Computer` 提供用于访问运行应用程序的计算机的方法、属性和事件。</span><span class="sxs-lookup"><span data-stu-id="91019-105">`My.Computer` provides methods, properties, and events for accessing the computer on which the application is running.</span></span> <span data-ttu-id="91019-106">其对象包括：</span><span class="sxs-lookup"><span data-stu-id="91019-106">Its objects include:</span></span>

- <xref:Microsoft.VisualBasic.Devices.Audio>
- <span data-ttu-id="91019-107">剪贴板 (<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>)</span><span class="sxs-lookup"><span data-stu-id="91019-107">Clipboard (<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>)</span></span>
- <xref:Microsoft.VisualBasic.Devices.Clock>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.Devices.ServerComputer.Info%2A>
- <xref:Microsoft.VisualBasic.Devices.Keyboard>
- <xref:Microsoft.VisualBasic.Devices.Mouse>
- <xref:Microsoft.VisualBasic.Devices.Network>
- <xref:Microsoft.VisualBasic.Devices.Ports>
- <span data-ttu-id="91019-108">注册表 (<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>)</span><span class="sxs-lookup"><span data-stu-id="91019-108">Registry (<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>)</span></span>

## <a name="in-this-section"></a><span data-ttu-id="91019-109">本节内容</span><span class="sxs-lookup"><span data-stu-id="91019-109">In this section</span></span>

[<span data-ttu-id="91019-110">播放声音</span><span class="sxs-lookup"><span data-stu-id="91019-110">Playing Sounds</span></span>](playing-sounds.md)  
<span data-ttu-id="91019-111">列出与 `My.Computer.Audio` 关联的任务，例如在后台播放声音。</span><span class="sxs-lookup"><span data-stu-id="91019-111">Lists tasks associated with `My.Computer.Audio`, such as playing a sound in the background.</span></span>

[<span data-ttu-id="91019-112">将数据存储到剪贴板以及从剪贴板读取数据</span><span class="sxs-lookup"><span data-stu-id="91019-112">Storing Data to and Reading from the Clipboard</span></span>](storing-data-to-and-reading-from-the-clipboard.md)  
<span data-ttu-id="91019-113">列出与 `My.Computer.Clipboard` 关联的任务，例如从剪贴板读取数据或向剪贴板写入数据。</span><span class="sxs-lookup"><span data-stu-id="91019-113">Lists tasks associated with `My.Computer.Clipboard`, such as reading data from or writing data to the Clipboard.</span></span>

[<span data-ttu-id="91019-114">获取有关计算机的信息</span><span class="sxs-lookup"><span data-stu-id="91019-114">Getting Information about the Computer</span></span>](getting-information-about-the-computer.md)  
<span data-ttu-id="91019-115">列出与 `My.Computer.Info` 关联的任务，例如确定计算机的全名或 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="91019-115">Lists tasks associated with `My.Computer.Info`, such as determining a computer's full name or IP addresses.</span></span>

[<span data-ttu-id="91019-116">访问键盘</span><span class="sxs-lookup"><span data-stu-id="91019-116">Accessing the Keyboard</span></span>](accessing-the-keyboard.md)  
<span data-ttu-id="91019-117">列出与 `My.Computer.Keyboard` 关联的任务，例如确定 Caps Lock 键是否已启用。</span><span class="sxs-lookup"><span data-stu-id="91019-117">Lists tasks associated with `My.Computer.Keyboard`, such as determining whether CAPS LOCK is on.</span></span>

[<span data-ttu-id="91019-118">访问鼠标</span><span class="sxs-lookup"><span data-stu-id="91019-118">Accessing the Mouse</span></span>](accessing-the-mouse.md)  
<span data-ttu-id="91019-119">列出与 `My.Computer.Mouse` 关联的任务，例如确定鼠标是否存在。</span><span class="sxs-lookup"><span data-stu-id="91019-119">Lists tasks associated with `My.Computer.Mouse`, such as determining whether a mouse is present.</span></span>

[<span data-ttu-id="91019-120">执行网络操作</span><span class="sxs-lookup"><span data-stu-id="91019-120">Performing Network Operations</span></span>](performing-network-operations.md)  
<span data-ttu-id="91019-121">列出与 `My.Computer.Network` 关联的任务，例如上传或下载文件。</span><span class="sxs-lookup"><span data-stu-id="91019-121">Lists tasks associated with `My.Computer.Network`, such as uploading or downloading files.</span></span>

[<span data-ttu-id="91019-122">访问计算机的端口</span><span class="sxs-lookup"><span data-stu-id="91019-122">Accessing the Computer's Ports</span></span>](accessing-the-computer-s-ports.md)  
<span data-ttu-id="91019-123">列出与 `My.Computer.Ports` 关联的任务，例如显示可用的串行端口或向串行端口发送字符串。</span><span class="sxs-lookup"><span data-stu-id="91019-123">Lists tasks associated with `My.Computer.Ports`, such as showing available serial ports or sending strings to serial ports.</span></span>

[<span data-ttu-id="91019-124">读取和写入注册表</span><span class="sxs-lookup"><span data-stu-id="91019-124">Reading from and Writing to the Registry</span></span>](reading-from-and-writing-to-the-registry.md)  
<span data-ttu-id="91019-125">列出与 `My.Computer.Registry` 关联的任务，例如从注册表项读取数据或向注册表项写入数据。</span><span class="sxs-lookup"><span data-stu-id="91019-125">Lists tasks associated with `My.Computer.Registry`, such as reading data from or writing data to registry keys.</span></span>
