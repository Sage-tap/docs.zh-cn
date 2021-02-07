---
description: '了解详细信息：源格式化程序 (JSON) '
title: 源格式化程序 (JSON)
ms.date: 03/30/2017
ms.assetid: f9c0b295-55e7-48ea-b308-ba51c7d31143
ms.openlocfilehash: 124b0fbf81af2a3f548431f98f6a5d695d737074
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752335"
---
# <a name="feed-formatter-json"></a><span data-ttu-id="a1b57-103">源格式化程序 (JSON)</span><span class="sxs-lookup"><span data-stu-id="a1b57-103">Feed Formatter (JSON)</span></span>

<span data-ttu-id="a1b57-104">本示例演示如何使用自定义 <xref:System.ServiceModel.Syndication.SyndicationFeed> 和 <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> 来序列化 JavaScript 对象符号 (JSON) 格式的 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="a1b57-104">This sample shows how to serialize an instance of a <xref:System.ServiceModel.Syndication.SyndicationFeed> class in JavaScript Object Notation (JSON) format by using a custom <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> and the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
## <a name="architecture-of-the-sample"></a><span data-ttu-id="a1b57-105">示例的体系结构</span><span class="sxs-lookup"><span data-stu-id="a1b57-105">Architecture of the Sample</span></span>  

 <span data-ttu-id="a1b57-106">本示例实现一个从 `JsonFeedFormatter` 继承的名为 <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> 的类。</span><span class="sxs-lookup"><span data-stu-id="a1b57-106">The sample implements a class named `JsonFeedFormatter` that inherits from <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>.</span></span> <span data-ttu-id="a1b57-107">`JsonFeedFormatter` 类依靠 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 来读写 JSON 格式的数据。</span><span class="sxs-lookup"><span data-stu-id="a1b57-107">The `JsonFeedFormatter` class relies on the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> to read and write the data in JSON format.</span></span> <span data-ttu-id="a1b57-108">在内部，格式化程序使用名为 `JsonSyndicationFeed` 和 `JsonSyndicationItem` 的一组自定义数据协定类型来控制由序列化程序生成的 JSON 数据的格式。</span><span class="sxs-lookup"><span data-stu-id="a1b57-108">Internally, the formatter uses a custom set of data contract types named `JsonSyndicationFeed` and `JsonSyndicationItem` to control the format of the JSON data produced by the serializer.</span></span> <span data-ttu-id="a1b57-109">对于最终用户，这些实现的详细信息是不可见的，从而可以针对标准 <xref:System.ServiceModel.Syndication.SyndicationFeed> 和 <xref:System.ServiceModel.Syndication.SyndicationItem> 类进行调用。</span><span class="sxs-lookup"><span data-stu-id="a1b57-109">These implementation details are hidden from the end user, allowing calls to be made against the standard <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem> classes.</span></span>  
  
## <a name="writing-json-feeds"></a><span data-ttu-id="a1b57-110">编写 JSON 源</span><span class="sxs-lookup"><span data-stu-id="a1b57-110">Writing JSON feeds</span></span>  

 <span data-ttu-id="a1b57-111">通过与 `JsonFeedFormatter` 一起使用 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>（在本示例中实现），可实现编写 JSON 源，如下面的示例代码所示。</span><span class="sxs-lookup"><span data-stu-id="a1b57-111">Writing a JSON feed can be accomplished by using the `JsonFeedFormatter` (implemented in this sample) with the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> as shown in the following sample code.</span></span>  
  
```csharp  
//Basic feed with sample data  
SyndicationFeed feed = new SyndicationFeed("Custom JSON feed", "A Syndication extensibility sample", null);  
feed.LastUpdatedTime = DateTime.Now;  
feed.Items = from s in new string[] { "hello", "world" }  
select new SyndicationItem()  
{  
    Summary = SyndicationContent.CreatePlaintextContent(s)  
};  
  
//Write the feed out to a MemoryStream in JSON format  
DataContractJsonSerializer writeSerializer = new DataContractJsonSerializer(typeof(JsonFeedFormatter));  
writeSerializer.WriteObject(stream, new JsonFeedFormatter(feed));  
```  
  
## <a name="reading-a-json-feed"></a><span data-ttu-id="a1b57-112">读取 JSON 源</span><span class="sxs-lookup"><span data-stu-id="a1b57-112">Reading a JSON feed</span></span>  

 <span data-ttu-id="a1b57-113">使用 <xref:System.ServiceModel.Syndication.SyndicationFeed> 可以实现从 JSON 格式的数据流中获取 `JsonFeedFormatter`，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="a1b57-113">Obtaining a <xref:System.ServiceModel.Syndication.SyndicationFeed> from a stream of JSON-formatted data can be accomplished with the `JsonFeedFormatter` as show in the following code.</span></span>  
  
 `//Read in the feed using the DataContractJsonSerializer`  
  
 `DataContractJsonSerializer readSerializer = new DataContractJsonSerializer(typeof(JsonFeedFormatter));`  
  
 `JsonFeedFormatter formatter = readSerializer.ReadObject(stream) as JsonFeedFormatter;`  
  
 `SyndicationFeed feedRead = formatter.Feed;`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a1b57-114">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="a1b57-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="a1b57-115">确保已对 [Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="a1b57-115">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="a1b57-116">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="a1b57-116">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="a1b57-117">若要以单机配置或跨计算机配置来运行示例，请按照 [运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="a1b57-117">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a1b57-118">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="a1b57-118">The samples may already be installed on your computer.</span></span> <span data-ttu-id="a1b57-119">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="a1b57-119">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="a1b57-120">如果此目录不存在，请参阅[Windows Communication Foundation (wcf) ，并 Windows Workflow Foundation (的 WF](https://www.microsoft.com/download/details.aspx?id=21459)) .NET Framework Windows Communication Foundation ([!INCLUDE[wf1](../../../../includes/wf1-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1b57-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a1b57-121">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="a1b57-121">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\JsonFeeds`  
