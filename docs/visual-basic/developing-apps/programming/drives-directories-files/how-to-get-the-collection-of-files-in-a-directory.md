---
description: 详细了解：操作说明：在 Visual Basic 中获取目录中的文件集合
title: 如何：获取目录中的文件集合
ms.date: 07/20/2015
helpviewer_keywords:
- folders, working with
- files [Visual Basic], accessing
ms.assetid: 6c8ba7e8-dd37-4853-92bf-762b67c98160
ms.openlocfilehash: bd799390c0ad0868f51387ba12e8612fe8948297
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797531"
---
# <a name="how-to-get-the-collection-of-files-in-a-directory-in-visual-basic"></a><span data-ttu-id="6a60b-103">如何：在 Visual Basic 中获取目录中的文件集合</span><span class="sxs-lookup"><span data-stu-id="6a60b-103">How to: Get the Collection of Files in a Directory in Visual Basic</span></span>

<span data-ttu-id="6a60b-104"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> 方法的重载返回字符串的只读集合，这些字符串表示目录内文件的名称：</span><span class="sxs-lookup"><span data-stu-id="6a60b-104">The overloads of the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> method return a read-only collection of strings representing the names of the files within a directory:</span></span>  
  
- <span data-ttu-id="6a60b-105">将 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> 重载用于指定目录中的简单文件搜索，而无需搜索子目录。</span><span class="sxs-lookup"><span data-stu-id="6a60b-105">Use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> overload for a simple file search in a specified directory, without searching subdirectories.</span></span>  
  
- <span data-ttu-id="6a60b-106">使用 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> 重载指定搜索的其他选项。</span><span class="sxs-lookup"><span data-stu-id="6a60b-106">Use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> overload to specify additional options for your search.</span></span> <span data-ttu-id="6a60b-107">可以使用 `wildCards` 参数来指定搜索模式。</span><span class="sxs-lookup"><span data-stu-id="6a60b-107">You can use the `wildCards` parameter to specify a search pattern.</span></span> <span data-ttu-id="6a60b-108">若要在搜索中包括子目录，请将 `searchType` 参数设置为 <xref:Microsoft.VisualBasic.FileIO.SearchOption.SearchAllSubDirectories?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="6a60b-108">To include subdirectories in the search, set the `searchType` parameter to <xref:Microsoft.VisualBasic.FileIO.SearchOption.SearchAllSubDirectories?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="6a60b-109">如果没有找到与指定模式匹配的文件，则返回一个空集合。</span><span class="sxs-lookup"><span data-stu-id="6a60b-109">An empty collection is returned if no files matching the specified pattern are found.</span></span>  
  
### <a name="to-list-files-in-a-directory"></a><span data-ttu-id="6a60b-110">列出目录中的文件</span><span class="sxs-lookup"><span data-stu-id="6a60b-110">To list files in a directory</span></span>  
  
- <span data-ttu-id="6a60b-111">使用其中一个 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> 方法重载，向 `directory` 参数中的搜索提供目录的名称和路径。</span><span class="sxs-lookup"><span data-stu-id="6a60b-111">Use one of the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> method overloads, supplying the name and path of the directory to search in the `directory` parameter.</span></span> <span data-ttu-id="6a60b-112">下面的示例返回目录中的所有文件，并将它们添加到 `ListBox1`。</span><span class="sxs-lookup"><span data-stu-id="6a60b-112">The following example returns all files in the directory and adds them to `ListBox1`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#32)]  
  
## <a name="robust-programming"></a><span data-ttu-id="6a60b-113">可靠编程</span><span class="sxs-lookup"><span data-stu-id="6a60b-113">Robust Programming</span></span>  

 <span data-ttu-id="6a60b-114">以下情况可能会导致异常：</span><span class="sxs-lookup"><span data-stu-id="6a60b-114">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="6a60b-115">路径由于以下原因之一而无效：是零长度字符串；仅为空白；包含无效字符；是一个设备路径（开头字符为 \\\\.\\）(<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="6a60b-115">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="6a60b-116">路径无效，因为它是 `Nothing` (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="6a60b-116">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="6a60b-117">`directory` 不存在 (<xref:System.IO.DirectoryNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="6a60b-117">`directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="6a60b-118">`directory` 指向某个现有文件 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="6a60b-118">`directory` points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="6a60b-119">路径超过了系统定义的最大长度 (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="6a60b-119">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="6a60b-120">路径中的文件名或目录名包含冒号 (:)，或格式无效 (<xref:System.NotSupportedException>)。</span><span class="sxs-lookup"><span data-stu-id="6a60b-120">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="6a60b-121">该用户缺少查看该路径所必需的权限 (<xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="6a60b-121">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="6a60b-122">该用户缺少必要的权限 (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="6a60b-122">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a60b-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6a60b-123">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A>
- [<span data-ttu-id="6a60b-124">如何：查找具有特定模式的文件</span><span class="sxs-lookup"><span data-stu-id="6a60b-124">How to: Find Files with a Specific Pattern</span></span>](how-to-find-files-with-a-specific-pattern.md)
- [<span data-ttu-id="6a60b-125">如何：查找具有特定模式的子目录</span><span class="sxs-lookup"><span data-stu-id="6a60b-125">How to: Find Subdirectories with a Specific Pattern</span></span>](how-to-find-subdirectories-with-a-specific-pattern.md)
