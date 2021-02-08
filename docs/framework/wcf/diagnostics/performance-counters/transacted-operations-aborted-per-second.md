---
description: 了解详细信息：每秒中止的事务处理操作
title: Transacted Operations Aborted Per Second（每秒中止的事务处理操作次数）
ms.date: 03/30/2017
ms.assetid: 19fc993f-2b3d-4898-852e-3b98ec2153a5
ms.openlocfilehash: de130c18e065e48ed7ac18442b2bc5f82c2f6861
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99771192"
---
# <a name="transacted-operations-aborted-per-second"></a><span data-ttu-id="3bca3-103">Transacted Operations Aborted Per Second（每秒中止的事务处理操作次数）</span><span class="sxs-lookup"><span data-stu-id="3bca3-103">Transacted Operations Aborted Per Second</span></span>

<span data-ttu-id="3bca3-104">计数器名称：Transacted Operations Aborted Per Second（每秒中止的事务处理操作次数）。</span><span class="sxs-lookup"><span data-stu-id="3bca3-104">Counter Name: Transacted Operations Aborted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="3bca3-105">说明</span><span class="sxs-lookup"><span data-stu-id="3bca3-105">Description</span></span>  

 <span data-ttu-id="3bca3-106">在此服务中一秒内已中止的事务性操作的数量。</span><span class="sxs-lookup"><span data-stu-id="3bca3-106">Number of transactional operations that have been aborted in this service in a second.</span></span>  
  
 <span data-ttu-id="3bca3-107">此计数器的性能计数器类型 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值使用以下公式进行计算。</span><span class="sxs-lookup"><span data-stu-id="3bca3-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="3bca3-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="3bca3-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
