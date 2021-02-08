---
description: 了解更多相关信息： BC30014： "#ElseIf" 前面必须是匹配的 "#If" 或 "#ElseIf
title: “#ElseIf”前面必须是匹配的“#If”或“#ElseIf”
ms.date: 07/20/2015
f1_keywords:
- vbc30014
- bc30014
helpviewer_keywords:
- BC30014
ms.assetid: 5215585e-2efa-485a-9efe-9833a1cc83a0
ms.openlocfilehash: 5eeb9c2fc0fd7267d95a8713a7071cd08788e48b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796556"
---
# <a name="bc30014-elseif-must-be-preceded-by-a-matching-if-or-elseif"></a>BC30014： "#ElseIf" 前面必须是匹配的 "#If" 或 "#ElseIf"

`#ElseIf` 是条件编译指令。 `#ElseIf`子句前面必须是匹配的 `#If` or `#ElseIf` 子句。

 **错误 ID：** BC30014

## <a name="to-correct-this-error"></a>更正此错误

1. 检查 `#If` `#ElseIf` 插入的 `#ElseIf` 条件编译块或错误放置的，检查前面的或是否未与此分离 `#End If` 。

2. 如果 `#ElseIf` 前面有一个 `#Else` 指令，请删除 `#Else` 或将其更改为 `#ElseIf` 。

3. 如果其他一切正常，请将 `#If` 指令添加到条件编译块的开头。

## <a name="see-also"></a>请参阅

- [#If...Then...#Else 指令](../directives/if-then-else-directives.md)
