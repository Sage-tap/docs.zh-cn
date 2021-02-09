---
description: 详细了解：操作说明：在 Visual Basic 中在不同的目录中创建文件的副本
title: 如何：在不同的目录中创建文件的副本
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: 88e2145c-d414-45a5-ad03-6f5d58ecca26
ms.openlocfilehash: 128a813ec3e5c759d5320d59a1e83f9d66af3bbd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797635"
---
# <a name="how-to-create-a-copy-of-a-file-in-a-different-directory-in-visual-basic"></a><span data-ttu-id="2d9cc-103">如何：在 Visual Basic 中在不同的目录中创建文件的副本</span><span class="sxs-lookup"><span data-stu-id="2d9cc-103">How to: Create a Copy of a File in a Different Directory in Visual Basic</span></span>

<span data-ttu-id="2d9cc-104">使用 `My.Computer.FileSystem.CopyFile` 方法可复制文件。</span><span class="sxs-lookup"><span data-stu-id="2d9cc-104">The `My.Computer.FileSystem.CopyFile` method allows you to copy files.</span></span> <span data-ttu-id="2d9cc-105">该方法的参数提供了各种功能，用于覆盖现有文件、重命名文件、显示操作进度以及允许用户取消操作。</span><span class="sxs-lookup"><span data-stu-id="2d9cc-105">Its parameters provide the ability to overwrite existing files, rename the file, show the progress of the operation, and allow the user to cancel the operation.</span></span>  
  
### <a name="to-copy-a-text-file-to-another-folder"></a><span data-ttu-id="2d9cc-106">将文本文件复制到其他文件夹</span><span class="sxs-lookup"><span data-stu-id="2d9cc-106">To copy a text file to another folder</span></span>  
  
- <span data-ttu-id="2d9cc-107">使用 `CopyFile` 方法并指定源文件和目标目录，可以复制文件。</span><span class="sxs-lookup"><span data-stu-id="2d9cc-107">Use the `CopyFile` method to copy a file, specifying a source file and the target directory.</span></span> <span data-ttu-id="2d9cc-108">通过 `overwrite` 参数，可以指定是否覆盖现有文件。</span><span class="sxs-lookup"><span data-stu-id="2d9cc-108">The `overwrite` parameter allows you to specify whether or not to overwrite existing files.</span></span> <span data-ttu-id="2d9cc-109">下面的代码示例演示如何使用 `CopyFile`。</span><span class="sxs-lookup"><span data-stu-id="2d9cc-109">The following code examples demonstrate how to use `CopyFile`.</span></span>  
  
     [!code-vb[VbFileIOMisc#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#24)]  
  
## <a name="robust-programming"></a><span data-ttu-id="2d9cc-110">可靠编程</span><span class="sxs-lookup"><span data-stu-id="2d9cc-110">Robust Programming</span></span>  

 <span data-ttu-id="2d9cc-111">以下情况可能会导致异常：</span><span class="sxs-lookup"><span data-stu-id="2d9cc-111">The following conditions may cause an exception to be thrown:</span></span>  
  
- <span data-ttu-id="2d9cc-112">路径由于以下原因之一而无效：是零长度字符串；仅为空白；包含无效字符；是一个设备路径（开头字符为 \\\\.\\）(<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="2d9cc-112">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="2d9cc-113">系统无法检索绝对路径 (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="2d9cc-113">The system could not retrieve the absolute path (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="2d9cc-114">路径无效，因为它是 `Nothing` (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="2d9cc-114">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="2d9cc-115">源文件无效或不存在 (<xref:System.IO.FileNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="2d9cc-115">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="2d9cc-116">合并路径指向现有目录 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="2d9cc-116">The combined path points to an existing directory (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="2d9cc-117">存在目标文件，并且 `overwrite` 设置为 `False` (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="2d9cc-117">The destination file exists and `overwrite` is set to `False` (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="2d9cc-118">用户没有足够的权限访问文件 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="2d9cc-118">The user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="2d9cc-119">目标文件夹中的同名文件正在使用中 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="2d9cc-119">A file in the target folder with the same name is in use (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="2d9cc-120">路径中的文件名或文件夹名包含冒号 (:)，或其格式无效 (<xref:System.NotSupportedException>)。</span><span class="sxs-lookup"><span data-stu-id="2d9cc-120">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="2d9cc-121">`ShowUI` 设置为 `True`、`onUserCancel` 设置为 `ThrowException`，并且用户已取消操作 (<xref:System.OperationCanceledException>)。</span><span class="sxs-lookup"><span data-stu-id="2d9cc-121">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and the user has cancelled the operation (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="2d9cc-122">`ShowUI` 设置为 `True`、`onUserCancel` 设置为 `ThrowException`，并出现未指定的 I/O 错误 (<xref:System.OperationCanceledException>)。</span><span class="sxs-lookup"><span data-stu-id="2d9cc-122">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="2d9cc-123">路径超过了系统定义的最大长度 (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="2d9cc-123">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="2d9cc-124">用户没有必需的权限 (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="2d9cc-124">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
- <span data-ttu-id="2d9cc-125">该用户缺少查看该路径所必需的权限 (<xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="2d9cc-125">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d9cc-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2d9cc-126">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- [<span data-ttu-id="2d9cc-127">如何：将具有特定模式的文件复制到目录中</span><span class="sxs-lookup"><span data-stu-id="2d9cc-127">How to: Copy Files with a Specific Pattern to a Directory</span></span>](how-to-copy-files-with-a-specific-pattern-to-a-directory.md)
- [<span data-ttu-id="2d9cc-128">如何：在同一目录中创建文件副本</span><span class="sxs-lookup"><span data-stu-id="2d9cc-128">How to: Create a Copy of a File in the Same Directory</span></span>](how-to-create-a-copy-of-a-file-in-the-same-directory.md)
- [<span data-ttu-id="2d9cc-129">如何：将目录复制到另一个目录</span><span class="sxs-lookup"><span data-stu-id="2d9cc-129">How to: Copy a Directory to Another Directory</span></span>](how-to-copy-a-directory-to-another-directory.md)
- [<span data-ttu-id="2d9cc-130">如何：重命名文件</span><span class="sxs-lookup"><span data-stu-id="2d9cc-130">How to: Rename a File</span></span>](how-to-rename-a-file.md)
