---
description: 详细了解：操作说明：在 Visual Basic 中创建目录
title: 如何：创建目录
ms.date: 07/20/2015
helpviewer_keywords:
- directories [Visual Basic], creating
- folders [Visual Basic], creating
ms.assetid: 0351a2ca-24d8-43b5-bb39-9b99e6401cff
ms.openlocfilehash: 39a0f1b2f482b27b6f207f0ca8a498db198e9d59
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797596"
---
# <a name="how-to-create-a-directory-in-visual-basic"></a>如何：在 Visual Basic 中创建目录

使用 `My.Computer.FileSystem` 对象的 `CreateDirectory` 方法来创建目录。  
  
 如果该目录已存在，则不引发任何异常。  
  
### <a name="to-create-a-directory"></a>创建目录  
  
- 使用 `CreateDirectory` 方法，指定将在其中创建目录的位置的完整路径。 此示例在 `NewDirectory` 中创建目录 `C:\Documents and Settings\All Users\Documents`。  
  
     [!code-vb[VbVbcnMyFileSystem#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#2)]  
  
## <a name="robust-programming"></a>可靠编程  

 以下情况可能会导致异常：  
  
- 目录名称格式不正确。 例如，它包含非法字符或仅为空白 (<xref:System.ArgumentException>)。  
  
- 要创建的目录的父目录为只读 (<xref:System.IO.IOException>)。  
  
- 目录名称为 `Nothing` (<xref:System.ArgumentNullException>)。  
  
- 目录名称过长 (<xref:System.IO.PathTooLongException>)。  
  
- 目录名称是一个冒号“:”(<xref:System.NotSupportedException>)。  
  
- 用户无权创建目录 (<xref:System.UnauthorizedAccessException>)。  
  
- 用户在部分信任情况下缺少权限 (<xref:System.Security.SecurityException>)。  
  
## <a name="see-also"></a>另请参阅

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CreateDirectory%2A>
- [创建、删除和移动文件和目录](creating-deleting-and-moving-files-and-directories.md)
