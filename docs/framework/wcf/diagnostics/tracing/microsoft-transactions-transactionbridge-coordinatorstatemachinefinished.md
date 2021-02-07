---
description: 了解有关以下内容的详细信息： TransactionBridge. CoordinatorStateMachineFinished
title: Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished
ms.date: 03/30/2017
ms.assetid: 16cb428d-d886-4789-a961-6fded4b0dbba
ms.openlocfilehash: 83cbc6fe80d0fc611c88e8074805cae870261305
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99759388"
---
# <a name="microsofttransactionstransactionbridgecoordinatorstatemachinefinished"></a>Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished

用于协调器登记的状态机已进入已完成状态。  
  
## <a name="description"></a>说明  

 本地事务管理器认为高级协调器登记已完成 2pc 处理时跟踪。 登记的结果可以是“已提交”、“已中止”或“已忘记”。 本地事务管理器在“准备”过程中对“只读”投票时也会进行跟踪。  
  
## <a name="see-also"></a>请参阅

- [跟踪](index.md)
- [使用跟踪来排除应用程序故障](using-tracing-to-troubleshoot-your-application.md)
- [管理和诊断](../index.md)
