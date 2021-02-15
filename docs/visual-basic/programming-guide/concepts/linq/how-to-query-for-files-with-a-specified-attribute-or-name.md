---
description: '了解有关详细信息，请参阅如何：查询具有指定特性或名称的文件 (Visual Basic) '
title: 如何：查询具有指定属性或名称的文件
ms.date: 07/20/2015
ms.assetid: b26026a3-3f43-448f-a582-259997af6be0
ms.openlocfilehash: 3eb58bf683b97c5806145395cb489f0e85c2071b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100425719"
---
# <a name="how-to-query-for-files-with-a-specified-attribute-or-name-visual-basic"></a><span data-ttu-id="efed3-103">如何：查询具有指定特性或名称的文件 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="efed3-103">How to: Query for Files with a Specified Attribute or Name (Visual Basic)</span></span>

<span data-ttu-id="efed3-104">此示例演示了如何在指定目录树中查找具有指定文件扩展名（如“.txt”）的所有文件。</span><span class="sxs-lookup"><span data-stu-id="efed3-104">This example shows how to find all files that have a specified file name extension (for example ".txt") in a specified directory tree.</span></span> <span data-ttu-id="efed3-105">它还演示了如何基于时间在树中返回最新或最旧的文件。</span><span class="sxs-lookup"><span data-stu-id="efed3-105">It also shows how to return either the newest or oldest file in the tree based on the creation time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="efed3-106">示例</span><span class="sxs-lookup"><span data-stu-id="efed3-106">Example</span></span>  
  
```vb  
Module FindFileByExtension  
    Sub Main()  
  
        ' Change the drive\path if necessary  
        Dim root As String = "C:\Program Files\Microsoft Visual Studio 9.0"  
  
        'Take a snapshot of the folder contents  
        Dim dir As New System.IO.DirectoryInfo(root)  
  
        Dim fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories)  
  
        ' This query will produce the full path for all .txt files  
        ' under the specified folder including subfolders.  
        ' It orders the list according to the file name.  
        Dim fileQuery = From file In fileList _  
                        Where file.Extension = ".txt" _  
                        Order By file.Name _  
                        Select file  
  
        For Each file In fileQuery  
            Console.WriteLine(file.FullName)  
        Next  
  
        ' Create and execute a new query by using  
        ' the previous query as a starting point.  
        ' fileQuery is not executed again until the  
        ' call to Last  
        Dim fileQuery2 = From file In fileQuery _  
                         Order By file.CreationTime _  
                         Select file.Name, file.CreationTime  
  
        ' Execute the query  
        Dim newestFile = fileQuery2.Last  
  
        Console.WriteLine("\r\nThe newest .txt file is {0}. Creation time: {1}", _  
                newestFile.Name, newestFile.CreationTime)  
  
        ' Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
  
    End Sub  
End Module  
```  
  
## <a name="compile-the-code"></a><span data-ttu-id="efed3-107">编译代码</span><span class="sxs-lookup"><span data-stu-id="efed3-107">Compile the code</span></span>  

<span data-ttu-id="efed3-108">使用 `Imports` System. Linq 命名空间的语句创建 Visual Basic 控制台应用程序项目。</span><span class="sxs-lookup"><span data-stu-id="efed3-108">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="efed3-109">请参阅</span><span class="sxs-lookup"><span data-stu-id="efed3-109">See also</span></span>

- [<span data-ttu-id="efed3-110">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="efed3-110">LINQ to Objects (Visual Basic)</span></span>](linq-to-objects.md)
- [<span data-ttu-id="efed3-111">LINQ 和文件目录 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="efed3-111">LINQ and File Directories (Visual Basic)</span></span>](linq-and-file-directories.md)
