---
description: 了解更多：错误的 DLL 调用约定
title: 错误的 DLL 调用约定
ms.date: 07/20/2015
f1_keywords:
- vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
ms.openlocfilehash: 7e98ce5131d440a12bff4a4630da087102bdc4da
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797089"
---
# <a name="bad-dll-calling-convention"></a>错误的 DLL 调用约定

传递给动态链接库 (DLL) 的参数必须与例程所需的参数完全匹配。 调用约定涉及参数的数字、类型和顺序。 程序可能正在传递错误类型或参数数目的 DLL 中的例程。  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
1. 请确保所有参数类型都与你要调用的例程声明中指定的类型一致。  
  
2. 请确保传递的参数数目与要调用的例程声明中指定的参数数目相同。  
  
3. 如果 DLL 例程需要参数的值，请确保 `ByVal` 在例程的声明中为这些参数指定。  
  
## <a name="see-also"></a>请参阅

- [错误类型](../../programming-guide/language-features/error-types.md)
- [Call 语句](../statements/call-statement.md)
- [Declare Statement](../statements/declare-statement.md)
