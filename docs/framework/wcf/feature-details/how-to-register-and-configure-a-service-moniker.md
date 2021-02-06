---
description: 了解详细信息：如何：注册和配置服务标记
title: 如何：注册和配置服务名字对象
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], configure service monikers
- COM [WCF], register service monikers
ms.assetid: e5e16c80-8a8e-4eef-af53-564933b651ef
ms.openlocfilehash: 9c6867941a5b96c6ced0f8e371e10697144bd121
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643450"
---
# <a name="how-to-register-and-configure-a-service-moniker"></a>如何：注册和配置服务名字对象

使用 Windows Communication Foundation (使用类型协定的 COM 应用程序内的 WCF) 服务名字对象之前，必须使用 COM 注册所需的属性化类型，并使用所需的绑定配置来配置 COM 应用程序和名字对象。

## <a name="register-the-required-attributed-types-with-com"></a>向 COM 注册所需的属性化类型

1. 使用 "工作的 [元数据实用工具" 工具 ( # A0) ](../servicemodel-metadata-utility-tool-svcutil-exe.md) 工具从 WCF 服务中检索元数据协定。 这会生成 WCF 客户端程序集和客户端应用程序配置文件的源代码。

2. 确保将程序集中的类型标记为 `ComVisible`。 为此，请将以下属性添加到 Visual Studio 项目中的 *AssemblyInfo.cs* 文件。

    ```csharp
    [assembly: ComVisible(true)]
    ```

3. 将托管 WCF 客户端编译为具有强名称的程序集。 这要求使用加密密钥对进行签名。 有关详细信息，请参阅[使用强名称为程序集签名](../../../standard/assembly/sign-strong-name.md)。

4. 使用带有 `-tlb` 选项的程序集注册 (Regasm.exe) 工具向 COM 注册程序集中的类型。

5. 使用全局程序集缓存 (Gacutil.exe) 工具将该程序集添加到全局程序集缓存中。

    > [!NOTE]
    > 对程序集进行签名并将其添加到全局程序集缓存中是可选步骤，不过，这两个步骤可以简化在运行时从正确位置加载程序集的过程。

## <a name="configure-the-com-application-and-the-moniker-with-the-required-binding-configuration"></a>用所需的绑定配置配置 COM 应用程序和名字对象

- 在客户端应用程序的配置文件) 生成的客户端应用程序配置文件中，将配置定义 (，并将 [ ( # A0) ](../servicemodel-metadata-utility-tool-svcutil-exe.md) 生成的绑定定义。 例如，对于名为 CallCenterClient.exe 的 Visual Basic 6.0 可执行文件，配置应放置到该可执行文件所在目录中名为 CallCenterConfig.exe.config 的文件中。 此时，客户端应用程序就可以使用标记了。 请注意，如果使用 WCF 提供的标准绑定类型之一，则不需要绑定配置。

     注册下面的类型。

    ```csharp
    using System.ServiceModel;

    [ServiceContract]
    public interface IMathService
    {
        [OperationContract]
        public int Add(int x, int y);
        [OperationContract]
        public int Subtract(int x, int y);
    }
    ```

     使用 `wsHttpBinding` 绑定来公开应用程序。 对于给定的类型和应用程序配置，将使用以下的示例标记字符串。

    ```
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1
    ```

     或

    ```
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1, contract={36ADAD5A-A944-4d5c-9B7C-967E4F00A090}
    ```

     在将引用添加到包含 `IMathService` 类型的程序集后，你可以使用 Visual Basic 6.0 应用程序中的这些标记字符串中的任何一个，如下面的示例代码中所示。

    ```vb
    Dim mathProxy As IMathService
    Dim result As Integer

    Set mathProxy = GetObject( _
            "service4:address=http://localhost/MathService, _
            binding=wsHttpBinding, _
            bindingConfiguration=Binding1")

    result = mathProxy.Add(3, 5)
    ```

     在此示例中，绑定配置的定义 `Binding1` 存储在客户端应用程序的适当命名的配置文件中，如 *vb6appname.exe.config*。

    > [!NOTE]
    > 你可以在 C#、C++ 或其他任何 .NET 语言的应用程序中使用类似的代码。

    > [!NOTE]
    > 如果标记格式不正确，或者服务不可用，则对的调用将 `GetObject` 返回 "语法无效" 错误。 如果您收到此错误，请确保所使用的标记正确无误且服务可用。

     尽管本主题重点介绍如何将服务名字对象用于 Visual Basic 6.0 代码，但你可以使用其他语言的服务名字对象。 当通过 C++ 代码使用标记时，应使用“no_namespace named_guids raw_interfaces_only”导入 Svcutil.exe 生成的程序集，如下面的代码中所示。

    ```cpp
    #import "ComTestProxy.tlb" no_namespace named_guids
    ```

     这会修改导入的接口定义，以便所有方法均会返回一个 `HResult`。 其他任何返回值都将转换为 out 参数。 方法的总体执行情况保持不变。 这将允许您确定在代理上调用方法时出现异常的原因。 仅可通过 C++ 代码来使用此功能。

## <a name="see-also"></a>请参阅

- [ServiceModel 元数据实用工具 (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)
