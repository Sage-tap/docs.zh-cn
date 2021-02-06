---
description: 了解有关以下方面的详细信息： TcpConnectError
title: System.ServiceModel.Channels.TcpConnectError
ms.date: 03/30/2017
ms.assetid: 22d93797-072e-405d-a3e0-5c519ddf290b
ms.openlocfilehash: e8c8e682100080e8622d0371505c9f3b9ddb84d0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99634383"
---
# <a name="systemservicemodelchannelstcpconnecterror"></a><span data-ttu-id="39b41-103">System.ServiceModel.Channels.TcpConnectError</span><span class="sxs-lookup"><span data-stu-id="39b41-103">System.ServiceModel.Channels.TcpConnectError</span></span>

<span data-ttu-id="39b41-104">TCP 连接操作失败。</span><span class="sxs-lookup"><span data-stu-id="39b41-104">The TCP connect operation failed.</span></span>  
  
## <a name="description"></a><span data-ttu-id="39b41-105">说明</span><span class="sxs-lookup"><span data-stu-id="39b41-105">Description</span></span>  

 <span data-ttu-id="39b41-106">此警告级别的跟踪指示未能连接到 TCP 终结点。</span><span class="sxs-lookup"><span data-stu-id="39b41-106">This warning level trace indicates a failure to connect to a TCP endpoint.</span></span> <span data-ttu-id="39b41-107">如果远程终结点在给定 IP 地址和端口没有响应，则可能出现此情况。</span><span class="sxs-lookup"><span data-stu-id="39b41-107">This could happen if the remote endpoint is not responding at a given IP address and port.</span></span> <span data-ttu-id="39b41-108">如果随后进行的连接到其他有效 IP 地址（如 IPv4 或 IPv6 地址，或表示给定主机名的其他 IP 地址）的尝试成功，则可以忽略此跟踪。</span><span class="sxs-lookup"><span data-stu-id="39b41-108">This trace can be ignored if subsequent attempts to connect to other valid IP addresses (such as IPv4 or IPv6 addresses, or other IP addresses representing a given hostname) succeed.</span></span> <span data-ttu-id="39b41-109">此跟踪内的异常可披露与错误有关的其他信息。</span><span class="sxs-lookup"><span data-stu-id="39b41-109">The exception within this trace can reveal additional information about the error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39b41-110">请参阅</span><span class="sxs-lookup"><span data-stu-id="39b41-110">See also</span></span>

- [<span data-ttu-id="39b41-111">跟踪</span><span class="sxs-lookup"><span data-stu-id="39b41-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="39b41-112">使用跟踪来排除应用程序故障</span><span class="sxs-lookup"><span data-stu-id="39b41-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="39b41-113">管理和诊断</span><span class="sxs-lookup"><span data-stu-id="39b41-113">Administration and Diagnostics</span></span>](../index.md)
