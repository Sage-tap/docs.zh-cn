---
description: 了解详细信息： OperationContextScope
title: OperationContextScope
ms.date: 03/30/2017
ms.assetid: 11c11108-8eb4-4d49-95a0-83285a812262
ms.openlocfilehash: efe05bdf4071ef8dfd86cf4c393b2abb8d20ad31
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793202"
---
# <a name="operationcontextscope"></a><span data-ttu-id="5ca6f-103">OperationContextScope</span><span class="sxs-lookup"><span data-stu-id="5ca6f-103">OperationContextScope</span></span>

<span data-ttu-id="5ca6f-104">OperationContextScope 示例演示如何使用标头 (WCF) 调用发送额外的 Windows Communication Foundation 信息。</span><span class="sxs-lookup"><span data-stu-id="5ca6f-104">The OperationContextScope sample demonstrates how to send extra information on a Windows Communication Foundation (WCF) call using headers.</span></span> <span data-ttu-id="5ca6f-105">在此示例中，服务器和客户端都是控制台应用程序。</span><span class="sxs-lookup"><span data-stu-id="5ca6f-105">In this sample, both the server and client are console applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5ca6f-106">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="5ca6f-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="5ca6f-107">此示例演示客户端如何使用 <xref:System.ServiceModel.Channels.MessageHeader> 以 <xref:System.ServiceModel.OperationContextScope> 的方式发送额外的信息。</span><span class="sxs-lookup"><span data-stu-id="5ca6f-107">The sample demonstrates how a client can send additional information as a <xref:System.ServiceModel.Channels.MessageHeader> using <xref:System.ServiceModel.OperationContextScope>.</span></span> <span data-ttu-id="5ca6f-108"><xref:System.ServiceModel.OperationContextScope> 对象是通过将其范围设置为通道来创建的。</span><span class="sxs-lookup"><span data-stu-id="5ca6f-108">An <xref:System.ServiceModel.OperationContextScope> object is created by scoping it to a channel.</span></span> <span data-ttu-id="5ca6f-109">必须转换为远程服务的头可以添加到 <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> 集合中。</span><span class="sxs-lookup"><span data-stu-id="5ca6f-109">Headers that must be translated to the remote service can be added to the <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> collection.</span></span> <span data-ttu-id="5ca6f-110">可以通过访问 <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A> 在服务上检索添加到此集合中的头。</span><span class="sxs-lookup"><span data-stu-id="5ca6f-110">Headers added to this collection can be retrieved on the service by accessing <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A>.</span></span> <span data-ttu-id="5ca6f-111">它的调用是在多个通道进行的，添加到客户端的头然后将只应用于用来创建 <xref:System.ServiceModel.OperationContextScope> 的通道。</span><span class="sxs-lookup"><span data-stu-id="5ca6f-111">Its calls are made on multiple channels and then the headers added to the client only apply to the channel that was used to create the <xref:System.ServiceModel.OperationContextScope>.</span></span>  
  
## <a name="messageheaderreader"></a><span data-ttu-id="5ca6f-112">MessageHeaderReader</span><span class="sxs-lookup"><span data-stu-id="5ca6f-112">MessageHeaderReader</span></span>  

 <span data-ttu-id="5ca6f-113">这是从客户端接收消息，并尝试在 <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A> 集合中查找头的示例服务。</span><span class="sxs-lookup"><span data-stu-id="5ca6f-113">This is the sample service that receives a message from the client and tries to look up the header in the <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A> collection.</span></span> <span data-ttu-id="5ca6f-114">客户端传递在头中发送的 GUID，服务则检索自定义头，如果存在自定义头，则将其与客户端作为参数传递的 GUID 进行比较。</span><span class="sxs-lookup"><span data-stu-id="5ca6f-114">The client passes the GUID that it sent in the header and the service retrieves the custom header and, if present, compares it with the GUID passed as the argument by the client.</span></span>  
  
```csharp
public bool RetrieveHeader(string guid)  
{  
     MessageHeaders messageHeaderCollection =
             OperationContext.Current.IncomingMessageHeaders;  
     String guidHeader = null;  
  
     Console.WriteLine("Trying to check if IncomingMessageHeader " +  
               " collection contains header with value {0}", guid);  
     if (messageHeaderCollection.FindHeader(  
                       CustomHeader.HeaderName,
                       CustomHeader.HeaderNamespace) != -1)  
     {  
          guidHeader = messageHeaderCollection.GetHeader<String>(  
           CustomHeader.HeaderName, CustomHeader.HeaderNamespace);  
     }  
     else  
     {  
          Console.WriteLine("No header was found");  
     }  
     if (guidHeader != null)  
     {  
          Console.WriteLine("Found header with value {0}. "+
         "Does it match with GUID sent as parameter: {1}",
          guidHeader, guidHeader.Equals(guid));  
      }  
  
      Console.WriteLine();  
      //Return true if header is present and equals the guid sent by  
      // client as argument  
      return (guidHeader != null && guidHeader.Equals(guid));  
}  
```  
  
## <a name="messageheaderclient"></a><span data-ttu-id="5ca6f-115">MessageHeaderClient</span><span class="sxs-lookup"><span data-stu-id="5ca6f-115">MessageHeaderClient</span></span>  

 <span data-ttu-id="5ca6f-116">这是客户端实现，它使用由 "工作的 [元数据实用工具" 工具生成的代理 ( # A0) ](../servicemodel-metadata-utility-tool-svcutil-exe.md) 与远程服务进行通信。</span><span class="sxs-lookup"><span data-stu-id="5ca6f-116">This is the client implementation that uses the proxy generated by [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to communicate with the remote service.</span></span> <span data-ttu-id="5ca6f-117">它首先创建 `MessageHeaderReaderClient` 的两个代理对象。</span><span class="sxs-lookup"><span data-stu-id="5ca6f-117">It first creates two proxy objects of `MessageHeaderReaderClient`.</span></span>  
  
```csharp
//Create two clients to the remote service.  
MessageHeaderReaderClient client1 = new MessageHeaderReaderClient();  
MessageHeaderReaderClient client2 = new MessageHeaderReaderClient();  
```  
  
 <span data-ttu-id="5ca6f-118">客户端然后创建 OperationContextScope 并将其范围设置为 `client1`。</span><span class="sxs-lookup"><span data-stu-id="5ca6f-118">Client then creates an OperationContextScope and scopes it to `client1`.</span></span> <span data-ttu-id="5ca6f-119">它将 <xref:System.ServiceModel.Channels.MessageHeader> 添加到 <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> 中，并在两个客户端上都进行一次调用。</span><span class="sxs-lookup"><span data-stu-id="5ca6f-119">It adds a <xref:System.ServiceModel.Channels.MessageHeader> to <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> and invokes one call on both clients.</span></span> <span data-ttu-id="5ca6f-120">它 `client1` `client2` 通过检查调用的返回值，确保仅在上发送标头 `RetrieveHeader` 。</span><span class="sxs-lookup"><span data-stu-id="5ca6f-120">It ensures that the header is sent only on `client1` and not on `client2` by checking the return value from the `RetrieveHeader` call.</span></span>  
  
```csharp
using (new OperationContextScope(client1.InnerChannel))  
{  
    //Create a new GUID that is sent as the header.  
    String guid = Guid.NewGuid().ToString();  
  
    //Create a MessageHeader for the GUID we just created.  
    MessageHeader customHeader = MessageHeader.CreateHeader(CustomHeader.HeaderName, CustomHeader.HeaderNamespace, guid);  
  
    //Add the header to the OutgoingMessageHeader collection.  
    OperationContext.Current.OutgoingMessageHeaders.Add(customHeader);  
  
    //Now call RetrieveHeader on both the proxies. Since the OperationContextScope is tied to
    //client1's InnerChannel, the header should only be added to calls made on that client.  
    //Calls made on client2 should not be sending the header across even though the call  
    //is made in the same OperationContextScope.  
    Console.WriteLine("Using client1 to send message");  
    Console.WriteLine("Did server retrieve the header? : Actual: {0}, Expected: True", client1.RetrieveHeader(guid));  
  
    Console.WriteLine();  
    Console.WriteLine("Using client2 to send message");  
    Console.WriteLine("Did server retrieve the header? : Actual: {0}, Expected: False", client2.RetrieveHeader(guid));  
}  
```  
  
 <span data-ttu-id="5ca6f-121">此示例是自承载的。</span><span class="sxs-lookup"><span data-stu-id="5ca6f-121">This sample is self-hosted.</span></span> <span data-ttu-id="5ca6f-122">下面提供了运行示例的示例输出：</span><span class="sxs-lookup"><span data-stu-id="5ca6f-122">The following sample output from running the sample is provided:</span></span>  
  
```console  
Prompt> Service.exe  
The service is ready.  
Press <ENTER> to terminate service.  
  
Trying to check if IncomingMessageHeader collection contains header with value 2239da67-546f-42d4-89dc-8eb3c06215d8  
Found header with value 2239da67-546f-42d4-89dc-8eb3c06215d8. Does it match with GUID sent as parameter: True  
  
Trying to check if IncomingMessageHeader collection contains header with value 2239da67-546f-42d4-89dc-8eb3c06215d8  
No header was found  
  
Prompt>Client.exe  
Using client1 to send message  
Did server retrieve the header? : Actual: True, Expected: True  
  
Using client2 to send message  
Did server retrieve the header? : Actual: False, Expected: False  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5ca6f-123">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="5ca6f-123">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5ca6f-124">确保已对 [Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="5ca6f-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="5ca6f-125">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="5ca6f-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="5ca6f-126">若要以单机配置或跨计算机配置来运行示例，请按照 [运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="5ca6f-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5ca6f-127">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="5ca6f-127">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5ca6f-128">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="5ca6f-128">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="5ca6f-129">如果此目录不存在，请参阅[Windows Communication Foundation (wcf) ，并 Windows Workflow Foundation (的 WF](https://www.microsoft.com/download/details.aspx?id=21459)) .NET Framework Windows Communication Foundation ([!INCLUDE[wf1](../../../../includes/wf1-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ca6f-129">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5ca6f-130">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="5ca6f-130">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\OperationContextScope`  
