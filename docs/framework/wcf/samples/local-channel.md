---
description: 了解详细信息：本地通道
title: 本地通道
ms.date: 03/30/2017
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
ms.openlocfilehash: a580abc1e8dcd89c40c9fdc02001deb094eb0b05
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631744"
---
# <a name="local-channel"></a><span data-ttu-id="253ea-103">本地通道</span><span class="sxs-lookup"><span data-stu-id="253ea-103">Local Channel</span></span>

<span data-ttu-id="253ea-104">本地通道是用于同一应用程序域中的通信的 Windows Communication Foundation (WCF) 传输通道。</span><span class="sxs-lookup"><span data-stu-id="253ea-104">Local Channel is a Windows Communication Foundation (WCF) transport channel that is used for communication within the same application domain.</span></span> <span data-ttu-id="253ea-105">对于客户端和服务在相同应用程序域内运行，并且必须避免典型 WCF 通道堆栈（消息的序列化和反序列化）开销的方案，这十分有用。</span><span class="sxs-lookup"><span data-stu-id="253ea-105">This is useful for scenarios where the client and the service are running in the same application domain and the overhead of the typical WCF channel stack (serialization and deserialization of messages) must be avoided.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="253ea-106">演示</span><span class="sxs-lookup"><span data-stu-id="253ea-106">Demonstrates</span></span>  

 <span data-ttu-id="253ea-107">本地通道</span><span class="sxs-lookup"><span data-stu-id="253ea-107">Local Channel</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="253ea-108">讨论 (Discussion)</span><span class="sxs-lookup"><span data-stu-id="253ea-108">Discussion</span></span>  

 <span data-ttu-id="253ea-109">示例由两个项目文件组成：</span><span class="sxs-lookup"><span data-stu-id="253ea-109">The sample consists of two project files:</span></span>  
  
- <span data-ttu-id="253ea-110">**LocalChannel**：当前应用程序域中的本地通道的编程表示形式。</span><span class="sxs-lookup"><span data-stu-id="253ea-110">**LocalChannel**: The programmatic representation of the local channel within the current application domain.</span></span> <span data-ttu-id="253ea-111">在此项目中，发送组件将消息放置在内存中队列中，接收组件将消息从队列中取出以进行接收。</span><span class="sxs-lookup"><span data-stu-id="253ea-111">In this project, the sending component places the message in an in-memory queue and the receiving component de-queues the message to receive it.</span></span>  
  
- <span data-ttu-id="253ea-112">**ClientAndService**：此项目在控制台应用程序中承载服务，然后运行客户端，以便从同一应用程序域中调用服务。</span><span class="sxs-lookup"><span data-stu-id="253ea-112">**ClientAndService**: This project hosts a service in a console application and then runs a client to call the service from within the same application domain.</span></span>  
  
 <span data-ttu-id="253ea-113">本地通道设计跳过通道堆栈和序列化过程以提高速度。</span><span class="sxs-lookup"><span data-stu-id="253ea-113">The local channel design skips both the channel stack and the serialization process to increase speed.</span></span> <span data-ttu-id="253ea-114">本地传输通道使用队列实现，以将服务调用从客户端传输到服务并将值返回到客户端。</span><span class="sxs-lookup"><span data-stu-id="253ea-114">The local transport channel is implemented using a queue to transport service calls from the client to the service and to return back the value to the client.</span></span> <span data-ttu-id="253ea-115">示例复制对象，而不是对参数和返回值进行序列化。</span><span class="sxs-lookup"><span data-stu-id="253ea-115">Rather than serializing parameters and return values, the sample copies the objects.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="253ea-116">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="253ea-116">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="253ea-117">生成并运行 LocalChannel 解决方案。</span><span class="sxs-lookup"><span data-stu-id="253ea-117">Build and run the LocalChannel solution.</span></span>  
  
2. <span data-ttu-id="253ea-118">服务主机启动，客户端使用本地通道调用服务。</span><span class="sxs-lookup"><span data-stu-id="253ea-118">The service host is started and the client calls the service using the local channel.</span></span> <span data-ttu-id="253ea-119">出现控制台窗口，以显示服务调用的结果。</span><span class="sxs-lookup"><span data-stu-id="253ea-119">A console window appears to display the results of the service call.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="253ea-120">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="253ea-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="253ea-121">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="253ea-121">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="253ea-122">如果此目录不存在，请参阅[Windows Communication Foundation (wcf) ，并 Windows Workflow Foundation (的 WF](https://www.microsoft.com/download/details.aspx?id=21459)) .NET Framework Windows Communication Foundation ([!INCLUDE[wf1](../../../../includes/wf1-md.md)]</span><span class="sxs-lookup"><span data-stu-id="253ea-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="253ea-123">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="253ea-123">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`
