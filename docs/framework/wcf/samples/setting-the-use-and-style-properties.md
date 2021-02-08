---
description: 了解详细信息：设置 Use 和 Style 属性
title: 设置 Use 和 Style 属性示例
ms.date: 03/30/2017
ms.assetid: c09a0600-116f-41cf-900a-1b7e4ea4e300
ms.openlocfilehash: 435ea23e4a34ec91ea764ae9435487c1e1313afd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792994"
---
# <a name="setting-the-use-and-style-properties"></a>设置 Use 和 Style 属性

本示例演示如何使用 <xref:System.ServiceModel.XmlSerializerFormatAttribute> 和 <xref:System.ServiceModel.DataContractFormatAttribute> 的 Use 和 Style 属性。 这些属性影响如何格式化消息。 默认情况下，使用设置为 <xref:System.ServiceModel.OperationFormatStyle.Document> 的样式格式化消息正文。 可以在服务协定级别或在操作协定级别指定这些设置。

> [!NOTE]
> 本主题的最后介绍了此示例的设置过程和生成说明。

<xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> 样式属性确定如何设置服务的 WSDL 元数据格式。 可能的值为 <xref:System.ServiceModel.OperationFormatStyle.Document> 和 <xref:System.ServiceModel.OperationFormatStyle.Rpc>。 RPC 意味着与操作交换的消息的 WSDL 表示形式包含参数，如同远程过程调用那样。 下面是一个示例。

```xml
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">
  <wsdl:part name="n1" type="xsd:double"/>
  <wsdl:part name="n2" type="xsd:double"/>
</wsdl:message>
```

将样式设置为 <xref:System.ServiceModel.OperationFormatStyle.Document> 意味着 WSDL 表示形式包含一个表示与操作交换的文档的元素，如下面的示例所示。

```xml
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">
  <wsdl:part name="parameters" element="tns:Add"/>
</wsdl:message>
```

<xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> 属性确定消息的格式。 可能的值为 <xref:System.ServiceModel.OperationFormatUse.Literal> 和 <xref:System.ServiceModel.OperationFormatUse.Encoded>；默认值为 <xref:System.ServiceModel.OperationFormatUse.Literal>。 文本表示该消息是 WSDL 中的一个架构文本实例，如下面的“文档/文本”示例所示。

```xml
<Add xmlns="http://Microsoft.ServiceModel.Samples">
  <n1>100</n1>
  <n2>15.99</n2>
</Add>
```

编码表明 WSDL 中的架构是根据 SOAP 1.1 第 5 节中的规则进行编码的抽象规范。 下面是一个 RPC/编码示例。

```xml
<q1:Add xmlns:q1="http://Microsoft.ServiceModel.Samples">
  <n1 xsi:type="xsd:double" xmlns="">100</n1>
  <n2 xsi:type="xsd:double" xmlns="">15.99</n2>
</q1:Add>
```

WS-I 基本配置文件 1.0 禁止使用 <xref:System.ServiceModel.OperationFormatUse.Encoded>，只能在旧式服务需要时使用它。 仅当使用 XmlSerializer 时，`Encoded` 消息格式才可用。

为了使你能够看到正在发送和接收的消息，此示例基于 [跟踪和消息日志记录](tracing-and-message-logging.md)。 已将服务配置和源代码修改为启用和使用跟踪和消息日志记录。 此外，配置 <xref:System.ServiceModel.WSHttpBinding> 时没有使用安全性，因此可以以未加密的格式查看记录的消息。 应使用 [服务跟踪查看器工具 ( # A0) ](../service-trace-viewer-tool-svctraceviewer-exe.md)来查看生成的跟踪日志 (E2e 和 Message) 。 将跟踪配置为在 C:\LOGS 文件夹中创建。 请在运行示例之前创建该文件夹。 若要在跟踪查看器工具中查看消息内容，请在工具的左窗格和右窗格中选择 " **消息** "。

下面的代码显示服务协定，该协定的 <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> 属性设置为 <xref:System.ServiceModel.OperationFormatUse>，消息正文格式从默认的 <xref:System.ServiceModel.OperationFormatStyle> 更改为 <xref:System.ServiceModel.OperationFormatStyle.Document>。

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"),
XmlSerializerFormat(Style = OperationFormatStyle.Rpc,
                                 Use = OperationFormatUse.Encoded)]
public interface IUseAndStyleCalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    [OperationContract]
    double Subtract(double n1, double n2);
    [OperationContract]
    double Multiply(double n1, double n2);
    [OperationContract]
    double Divide(double n1, double n2);
}
```

若要查看不同的 <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> 和 <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A> 设置之间的差异，请在服务中修改这些设置、重新生成客户端、运行示例并用服务跟踪查看器工具检查 c:\logs\message.logs 文件。 还可以通过查看来观察对元数据的影响 `http://localhost/ServiceModelSamples/service.svc?wsdl` 。 服务的元数据通常分为多页。 主 wsdl 页面包含 WSDL 绑定，但 `http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0` 用于观察消息定义的视图。

## <a name="to-set-up-build-and-run-the-sample"></a>设置、生成和运行示例

1. 确保已对 [Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。

2. 创建一个 C:\LOGS 目录，用于记录消息。 向用户授予对该目录的“网络服务”写权限。

3. 若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。

4. 若要以单机配置或跨计算机配置来运行示例，请按照 [运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。

> [!IMPORTANT]
> 您的计算机上可能已安装这些示例。 在继续操作之前，请先检查以下（默认）目录：
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> 如果此目录不存在，请参阅[Windows Communication Foundation (wcf) ，并 Windows Workflow Foundation (的 WF](https://www.microsoft.com/download/details.aspx?id=21459)) .NET Framework Windows Communication Foundation ([!INCLUDE[wf1](../../../../includes/wf1-md.md)] 此示例位于以下目录：
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\UseAndStyle`
