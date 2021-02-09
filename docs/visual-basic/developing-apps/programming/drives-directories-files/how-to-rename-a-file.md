---
description: 详细了解：操作说明：在 Visual Basic 中重命名文件
title: 如何：重命名文件
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], renaming files
- files [Visual Basic], renaming
ms.assetid: 0ea7e0c8-2cb2-4bf5-a00d-7b6e3c08a3bc
ms.openlocfilehash: cf182fa94befdfdcb1568052a0193d483670cf49
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797401"
---
# <a name="how-to-rename-a-file-in-visual-basic"></a><span data-ttu-id="b932f-103">如何：在 Visual Basic 中重命名文件</span><span class="sxs-lookup"><span data-stu-id="b932f-103">How to: Rename a File in Visual Basic</span></span>

<span data-ttu-id="b932f-104">使用 `My.Computer.FileSystem` 对象的 `RenameFile` 方法可通过提供当前位置、文件名和新文件名来重命名文件。</span><span class="sxs-lookup"><span data-stu-id="b932f-104">Use the `RenameFile` method of the `My.Computer.FileSystem` object to rename a file by supplying the current location, file name, and the new file name.</span></span> <span data-ttu-id="b932f-105">此方法不能用于移动文件；使用 `MoveFile` 方法可移动并重命名文件。</span><span class="sxs-lookup"><span data-stu-id="b932f-105">This method cannot be used to move a file; use the `MoveFile` method to move and rename the file.</span></span>  
  
### <a name="to-rename-a-file"></a><span data-ttu-id="b932f-106">重命名文件</span><span class="sxs-lookup"><span data-stu-id="b932f-106">To rename a file</span></span>  
  
- <span data-ttu-id="b932f-107">使用 `My.Computer.FileSystem.RenameFile` 方法可重命名文件。</span><span class="sxs-lookup"><span data-stu-id="b932f-107">Use the `My.Computer.FileSystem.RenameFile` method to rename a file.</span></span> <span data-ttu-id="b932f-108">此示例将名为 `Test.txt` 的文件重命名为 `SecondTest.txt`。</span><span class="sxs-lookup"><span data-stu-id="b932f-108">This example renames the file named `Test.txt` to `SecondTest.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#9)]  
  
 <span data-ttu-id="b932f-109">此代码示例也可作为 IntelliSense 代码片段。</span><span class="sxs-lookup"><span data-stu-id="b932f-109">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="b932f-110">在代码片段选取器中，该代码段位于“文件系统 - 处理驱动器、文件夹和文件”。</span><span class="sxs-lookup"><span data-stu-id="b932f-110">In the code snippet picker, the snippet is located in **File system - Processing Drives, Folders, and Files**.</span></span> <span data-ttu-id="b932f-111">有关详细信息，请参阅[代码片段](/visualstudio/ide/code-snippets)。</span><span class="sxs-lookup"><span data-stu-id="b932f-111">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="b932f-112">可靠编程</span><span class="sxs-lookup"><span data-stu-id="b932f-112">Robust Programming</span></span>  

 <span data-ttu-id="b932f-113">以下情况可能会导致异常：</span><span class="sxs-lookup"><span data-stu-id="b932f-113">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="b932f-114">路径由于以下原因之一而无效：是零长度字符串；仅为空白；包含无效字符；是一个设备路径（开头字符为 \\\\.\\）(<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="b932f-114">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="b932f-115">`newName` 包含路径信息 (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="b932f-115">`newName` contains path information (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="b932f-116">路径无效，因为它是 `Nothing` (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="b932f-116">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="b932f-117">`newName` 为 `Nothing` 或空字符串 (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="b932f-117">`newName` is `Nothing` or an empty string (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="b932f-118">源文件无效或不存在 (<xref:System.IO.FileNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="b932f-118">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="b932f-119">不存在具有 `newName` (<xref:System.IO.IOException>) 中指定名称的现有文件或目录。</span><span class="sxs-lookup"><span data-stu-id="b932f-119">There is an existing file or directory with the name specified in `newName` (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="b932f-120">路径超过了系统定义的最大长度 (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="b932f-120">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="b932f-121">路径中的文件名或目录名包含冒号 (:)，或格式无效 (<xref:System.NotSupportedException>)。</span><span class="sxs-lookup"><span data-stu-id="b932f-121">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="b932f-122">该用户缺少查看该路径所必需的权限 (<xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="b932f-122">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="b932f-123">用户没有所必需的权限 (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="b932f-123">The user does not have the required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b932f-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b932f-124">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.RenameFile%2A>
- [<span data-ttu-id="b932f-125">如何：移动文件</span><span class="sxs-lookup"><span data-stu-id="b932f-125">How to: Move a File</span></span>](how-to-move-a-file.md)
- [<span data-ttu-id="b932f-126">创建、删除和移动文件和目录</span><span class="sxs-lookup"><span data-stu-id="b932f-126">Creating, Deleting, and Moving Files and Directories</span></span>](creating-deleting-and-moving-files-and-directories.md)
- [<span data-ttu-id="b932f-127">如何：在同一目录中创建文件副本</span><span class="sxs-lookup"><span data-stu-id="b932f-127">How to: Create a Copy of a File in the Same Directory</span></span>](how-to-create-a-copy-of-a-file-in-the-same-directory.md)
- [<span data-ttu-id="b932f-128">如何：在不同的目录中创建文件的副本</span><span class="sxs-lookup"><span data-stu-id="b932f-128">How to: Create a Copy of a File in a Different Directory</span></span>](how-to-create-a-copy-of-a-file-in-a-different-directory.md)
