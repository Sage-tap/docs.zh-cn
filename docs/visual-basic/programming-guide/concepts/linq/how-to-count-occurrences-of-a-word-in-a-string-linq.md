---
description: '了解有关详细信息，请参阅如何：对某个词在字符串中出现的次数进行计数 (LINQ)  (Visual Basic) '
title: 如何：对某个词在某一字符串中出现的次数进行计数 (LINQ)
ms.date: 07/20/2015
ms.assetid: bc367e46-f7cc-45f9-936f-754e661b7bb9
ms.openlocfilehash: dd00d1840f8f4eacdf949b0c1200b26f3692e00d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100464802"
---
# <a name="how-to-count-occurrences-of-a-word-in-a-string-linq-visual-basic"></a><span data-ttu-id="f9534-103">如何：对某个词在字符串中出现的次数进行计数 (LINQ)  (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="f9534-103">How to: Count Occurrences of a Word in a String (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="f9534-104">此示例演示如何使用 LINQ 查询对指定词在字符串中出现的次数进行计数。</span><span class="sxs-lookup"><span data-stu-id="f9534-104">This example shows how to use a LINQ query to count the occurrences of a specified word in a string.</span></span> <span data-ttu-id="f9534-105">请注意，若要执行计数，首先需调用 <xref:System.String.Split%2A> 方法来创建词数组。</span><span class="sxs-lookup"><span data-stu-id="f9534-105">Note that to perform the count, first the <xref:System.String.Split%2A> method is called to create an array of words.</span></span> <span data-ttu-id="f9534-106"><xref:System.String.Split%2A> 方法存在性能开销。</span><span class="sxs-lookup"><span data-stu-id="f9534-106">There is a performance cost to the <xref:System.String.Split%2A> method.</span></span> <span data-ttu-id="f9534-107">如果只需要统计字符串的字数，则应考虑改用 <xref:System.Text.RegularExpressions.Regex.Matches%2A> 或 <xref:System.String.IndexOf%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="f9534-107">If the only operation on the string is to count the words, you should consider using the <xref:System.Text.RegularExpressions.Regex.Matches%2A> or <xref:System.String.IndexOf%2A> methods instead.</span></span> <span data-ttu-id="f9534-108">但是，如果性能不是关键问题，或者已拆分句子以对其执行其他类型的查询，则使用 LINQ 来计数词或短语同样有意义。</span><span class="sxs-lookup"><span data-stu-id="f9534-108">However, if performance is not a critical issue, or you have already split the sentence in order to perform other types of queries over it, then it makes sense to use LINQ to count the words or phrases as well.</span></span>

## <a name="example"></a><span data-ttu-id="f9534-109">示例</span><span class="sxs-lookup"><span data-stu-id="f9534-109">Example</span></span>

```vb
Class CountWords

    Shared Sub Main()

        Dim text As String = "Historically, the world of data and the world of objects" &
                  " have not been well integrated. Programmers work in C# or Visual Basic" &
                  " and also in SQL or XQuery. On the one side are concepts such as classes," &
                  " objects, fields, inheritance, and .NET Framework APIs. On the other side" &
                  " are tables, columns, rows, nodes, and separate languages for dealing with" &
                  " them. Data types often require translation between the two worlds; there are" &
                  " different standard functions. Because the object world has no notion of query, a" &
                  " query can only be represented as a string without compile-time type checking or" &
                  " IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to" &
                  " objects in memory is often tedious and error-prone."

        Dim searchTerm As String = "data"

        ' Convert the string into an array of words.
        Dim dataSource As String() = text.Split(New Char() {" ", ",", ".", ";", ":"},
                                                 StringSplitOptions.RemoveEmptyEntries)

        ' Create and execute the query. It executes immediately
        ' because a singleton value is produced.
        ' Use ToLower to match "data" and "Data"
        Dim matchQuery = From word In dataSource
                      Where word.ToLowerInvariant() = searchTerm.ToLowerInvariant()
                      Select word

        ' Count the matches.
        Dim count As Integer = matchQuery.Count()
        Console.WriteLine(count & " occurrence(s) of the search term """ &
                          searchTerm & """ were found.")

        ' Keep console window open in debug mode.
        Console.WriteLine("Press any key to exit.")
        Console.ReadKey()
    End Sub
End Class
' Output:
' 3 occurrence(s) of the search term "data" were found.
```

## <a name="compile-the-code"></a><span data-ttu-id="f9534-110">编译代码</span><span class="sxs-lookup"><span data-stu-id="f9534-110">Compile the code</span></span>

<span data-ttu-id="f9534-111">使用 `Imports` System. Linq 命名空间的语句创建 Visual Basic 控制台应用程序项目。</span><span class="sxs-lookup"><span data-stu-id="f9534-111">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="f9534-112">请参阅</span><span class="sxs-lookup"><span data-stu-id="f9534-112">See also</span></span>

- [<span data-ttu-id="f9534-113">LINQ 和字符串 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f9534-113">LINQ and Strings (Visual Basic)</span></span>](linq-and-strings.md)
