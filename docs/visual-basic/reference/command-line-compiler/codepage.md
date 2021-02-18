---
description: 详细了解：-codepage (Visual Basic)
title: -codepage
ms.date: 03/09/2018
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
ms.openlocfilehash: 8bc68263bda298787a48dc06729ea17c5adfcfa5
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100468273"
---
# <a name="-codepage-visual-basic"></a>-codepage (Visual Basic)

指定要用于编译中所有源代码文件的代码页。  
  
## <a name="syntax"></a>语法  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a>自变量  
  
|术语|定义|  
|---|---|  
|`id`|必需。 编译器使用 `id` 指定的代码页解释源文件的编码。|  
  
## <a name="remarks"></a>备注  

 若要编译使用特定编码保存的源代码，可以使用 `-codepage` 指定应使用哪一个代码页。 `-codepage` 选项适用于编译中的所有源代码文件。 有关详细信息，请参阅 [.NET Framework 中的字符编码](../../../standard/base-types/character-encoding.md)。  
  
 若源代码文件是使用当前 ANSI 代码页、Unicode 或 UTF-8 保存的，并且带有签名，则无需使用 `-codepage` 选项。 若用户未从“编码”对话框指定其他编码，默认情况下，Visual Studio 使用当前 ANSI 代码页保存所有源代码文件。  Visual Studio 使用“编码”对话框打开使用其他代码页保存的源代码文件。   
  
> [!NOTE]
> `-codepage` 选项在 Visual Studio 开发环境内无法使用；仅当从命令行编译时才可用。  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 命令行编译器](index.md)
