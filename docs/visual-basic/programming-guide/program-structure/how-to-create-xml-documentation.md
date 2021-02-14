---
description: 了解有关详细信息，请参阅如何：在 Visual Basic 中创建 XML 文档
title: 如何：创建 XML 文档
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments
- XML documentation [Visual Basic], creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
ms.openlocfilehash: d54c79d820a170b246e5c85d7562487fbe66f39c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475950"
---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a>如何：在 Visual Basic 中创建 XML 文档

此示例演示如何将 XML 文档注释添加到代码。

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-xml-documentation-for-a-type-or-member"></a>为类型或成员创建 XML 文档

1. 在 **代码编辑器** 中，将光标置于要为其创建文档的类型或成员之上的行上。

2. 键入 `'''`)  (三个单引号。

    类型或成员的 XML 主干将添加到 **代码编辑器** 中。

3. 在适当的标记之间添加描述性信息。

    > [!NOTE]
    > 如果在 XML 文档块中添加额外的行，则每行都必须以开头 `'''` 。

4. 使用新的 XML 文档注释添加使用类型或成员的附加代码。

    IntelliSense 将显示该 \<summary> 类型或成员的标记中的文本。

5. 编译代码以生成包含文档注释的 XML 文件。 有关详细信息，请参阅 [-doc](../../reference/command-line-compiler/doc.md)。

## <a name="see-also"></a>请参阅

- [使用 XML 记录代码](documenting-your-code-with-xml.md)
- [XML 注释标记](../../language-reference/xmldoc/index.md)
- [-doc](../../reference/command-line-compiler/doc.md)
