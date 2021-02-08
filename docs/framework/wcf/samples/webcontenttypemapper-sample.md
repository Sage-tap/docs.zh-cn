---
description: 详细了解： WebContentTypeMapper 示例
title: WebContentTypeMapper 示例
ms.date: 03/30/2017
ms.assetid: a4fe59e7-44d8-43c6-a1f8-40c45223adca
ms.openlocfilehash: 274672bb8db1dc845b1cc1ced58b4c4a92232e9b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798142"
---
# <a name="webcontenttypemapper-sample"></a><span data-ttu-id="a7b61-103">WebContentTypeMapper 示例</span><span class="sxs-lookup"><span data-stu-id="a7b61-103">WebContentTypeMapper Sample</span></span>

<span data-ttu-id="a7b61-104">此示例演示如何将新内容类型映射到 Windows Communication Foundation (WCF) 消息正文格式。</span><span class="sxs-lookup"><span data-stu-id="a7b61-104">This sample demonstrates how to map new content types to Windows Communication Foundation (WCF) message body formats.</span></span>  
  
 <span data-ttu-id="a7b61-105"><xref:System.ServiceModel.Description.WebHttpEndpoint>元素插入 Web 消息编码器，这允许 WCF 在同一终结点接收 JSON、XML 或原始二进制消息。</span><span class="sxs-lookup"><span data-stu-id="a7b61-105">The <xref:System.ServiceModel.Description.WebHttpEndpoint> element plugs in the Web message encoder, which allows WCF to receive JSON, XML, or raw binary messages at the same endpoint.</span></span> <span data-ttu-id="a7b61-106">编码器通过查看请求的 HTTP 内容类型来确定消息的正文格式。</span><span class="sxs-lookup"><span data-stu-id="a7b61-106">The encoder determines the body format of the message by looking at the HTTP content-type of the request.</span></span> <span data-ttu-id="a7b61-107">本示例介绍 <xref:System.ServiceModel.Channels.WebContentTypeMapper> 类，该类允许用户控制内容类型和正文格式之间的映射。</span><span class="sxs-lookup"><span data-stu-id="a7b61-107">This sample introduces the <xref:System.ServiceModel.Channels.WebContentTypeMapper> class, which allows the user to control the mapping between content type and body format.</span></span>  
  
 <span data-ttu-id="a7b61-108">WCF 为内容类型提供了一组默认映射。</span><span class="sxs-lookup"><span data-stu-id="a7b61-108">WCF provides a set of default mappings for content types.</span></span> <span data-ttu-id="a7b61-109">例如，`application/json` 映射到 JSON，`text/xml` 映射到 XML。</span><span class="sxs-lookup"><span data-stu-id="a7b61-109">For example, `application/json` maps to JSON and `text/xml` maps to XML.</span></span> <span data-ttu-id="a7b61-110">未映射到 JSON 或 XML 的任何内容类型都将映射到原始二进制格式。</span><span class="sxs-lookup"><span data-stu-id="a7b61-110">Any content type that is not mapped to JSON or XML is mapped to raw binary format.</span></span>  
  
 <span data-ttu-id="a7b61-111">在某些方案（例如推送式 API）中，服务开发人员不控制由客户端返回的内容类型。</span><span class="sxs-lookup"><span data-stu-id="a7b61-111">In some scenarios (for example, push-style APIs), the service developer does not control the content type returned by the client.</span></span> <span data-ttu-id="a7b61-112">例如，客户端可以将 JSON 作为 `text/javascript` 而不是 `application/json` 返回。</span><span class="sxs-lookup"><span data-stu-id="a7b61-112">For example, clients might return JSON as `text/javascript` instead of `application/json`.</span></span> <span data-ttu-id="a7b61-113">在这种情况下，服务开发人员必须提供从 <xref:System.ServiceModel.Channels.WebContentTypeMapper> 派生的类型以正确处理给定的内容类型，如下面的示例代码所示。</span><span class="sxs-lookup"><span data-stu-id="a7b61-113">In this case, the service developer must provide a type that derives from <xref:System.ServiceModel.Channels.WebContentTypeMapper> to handle the given content type correctly, as shown in the following sample code.</span></span>  
  
```csharp  
public class JsonContentTypeMapper : WebContentTypeMapper  
{  
    public override WebContentFormat  
               GetMessageFormatForContentType(string contentType)  
    {  
        if (contentType == "text/javascript")  
        {  
            return WebContentFormat.Json;  
        }  
        else  
        {  
            return WebContentFormat.Default;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="a7b61-114">该类型必须重写 <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> 方法。</span><span class="sxs-lookup"><span data-stu-id="a7b61-114">The type must override the <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> method.</span></span> <span data-ttu-id="a7b61-115">该方法必须计算 `contentType` 参数并返回下列值之一：<xref:System.ServiceModel.Channels.WebContentFormat.Json>、<xref:System.ServiceModel.Channels.WebContentFormat.Xml>、<xref:System.ServiceModel.Channels.WebContentFormat.Raw> 或 <xref:System.ServiceModel.Channels.WebContentFormat.Default>。</span><span class="sxs-lookup"><span data-stu-id="a7b61-115">The method must evaluate the `contentType` argument and return one of the following values: <xref:System.ServiceModel.Channels.WebContentFormat.Json>, <xref:System.ServiceModel.Channels.WebContentFormat.Xml>, <xref:System.ServiceModel.Channels.WebContentFormat.Raw>, or <xref:System.ServiceModel.Channels.WebContentFormat.Default>.</span></span> <span data-ttu-id="a7b61-116">返回 <xref:System.ServiceModel.Channels.WebContentFormat.Default> 时将遵从默认的 Web 消息编码器映射。</span><span class="sxs-lookup"><span data-stu-id="a7b61-116">Returning <xref:System.ServiceModel.Channels.WebContentFormat.Default> defers to the default Web message encoder mappings.</span></span> <span data-ttu-id="a7b61-117">在前面的示例代码中，`text/javascript` 内容类型映射到 JSON，所有其他映射保持不变。</span><span class="sxs-lookup"><span data-stu-id="a7b61-117">In the previous sample code, the `text/javascript` content type is mapped to JSON, and all other mappings remain unchanged.</span></span>  
  
 <span data-ttu-id="a7b61-118">若要使用 `JsonContentTypeMapper` 类，请在你的 Web.config 中使用以下设置：</span><span class="sxs-lookup"><span data-stu-id="a7b61-118">To use the `JsonContentTypeMapper` class, use the following in your Web.config:</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <standardEndpoint name="" contentTypeMapper="Microsoft.Samples.WebContentTypeMapper.JsonContentTypeMapper, JsonContentTypeMapper, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="a7b61-119">若要验证使用 JsonContentTypeMapper 的需求，请从上面的配置文件中移除 contentTypeMapper 特性。</span><span class="sxs-lookup"><span data-stu-id="a7b61-119">To verify the requirement for using the JsonContentTypeMapper, remove the contentTypeMapper attribute from the above configuration file.</span></span> <span data-ttu-id="a7b61-120">在尝试使用 `text/javascript` 来发送 JSON 内容时，客户端页加载将失败。</span><span class="sxs-lookup"><span data-stu-id="a7b61-120">The client page fails to load when attempting to use `text/javascript` to send JSON content.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a7b61-121">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="a7b61-121">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="a7b61-122">确保已对 [Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="a7b61-122">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="a7b61-123">按照 [生成 Windows Communication Foundation 示例](building-the-samples.md)中所述生成解决方案 WebContentTypeMapperSample。</span><span class="sxs-lookup"><span data-stu-id="a7b61-123">Build the solution WebContentTypeMapperSample.sln as described in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="a7b61-124">定位到 `http://localhost/ServiceModelSamples/JCTMClientPage.htm` (不要在浏览器中从项目目录) 打开 JCTMClientPage.htm。</span><span class="sxs-lookup"><span data-stu-id="a7b61-124">Navigate to `http://localhost/ServiceModelSamples/JCTMClientPage.htm` (do not open JCTMClientPage.htm in the browser from within the project directory).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a7b61-125">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="a7b61-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a7b61-126">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="a7b61-126">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="a7b61-127">如果此目录不存在，请参阅[Windows Communication Foundation (wcf) ，并 Windows Workflow Foundation (的 WF](https://www.microsoft.com/download/details.aspx?id=21459)) .NET Framework Windows Communication Foundation ([!INCLUDE[wf1](../../../../includes/wf1-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7b61-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a7b61-128">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="a7b61-128">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Ajax\WebContentTypeMapper`  
