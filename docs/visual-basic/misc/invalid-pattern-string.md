---
description: 了解详细信息：无效的模式字符串
title: 无效模式字符串
ms.date: 07/20/2015
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
ms.openlocfilehash: 4fbf16dd43ac4ae44e1a99d85caae4a7baf99109
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100462056"
---
# <a name="invalid-pattern-string"></a>无效模式字符串

在搜索的 `Like` 操作中指定的模式字符串无效。  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
1. 查看列表中表达式的有效字符。  
  
2. 在模式范围内，请确保起始范围字符小于结束范围字符，如 `[a-z]`中所示。  
  
3. 在模式范围内，请确保不存在彼此相邻的多个连字符，如 `[a--z]`中所示。  
  
4. 以右括号结束模式范围。  
  
## <a name="see-also"></a>请参阅

- [Like 运算符](../language-reference/operators/like-operator.md)
