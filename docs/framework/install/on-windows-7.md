---
title: 在 Windows 7 SP1 上安装 .NET Framework
description: 了解如何在 Windows 7 SP1 上安装 .NET Framework。
ms.date: 04/18/2019
ms.openlocfilehash: 900b38110626a93f37829045a8676ea87101d7e9
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899082"
---
# <a name="install-the-net-framework-on-windows-7-sp1-and-windows-server-2008-r2"></a>在 Windows 7 SP1 和 Windows Server 2008 R2 上安装 .NET Framework

在 Windows 上运行许多应用程序需要 .NET Framework。 可以按照以下说明进行安装。 在尝试运行应用程序后，可能转到了此页并在计算机上看到以下对话框：

![无法启动此应用程序](./media/this-application-could-not-be-started.png)

这些说明可帮助安装所需的 .NET Framework 版本。 [.NET Framework 4.8](https://github.com/Microsoft/dotnet/tree/master/releases/net48) 是最新版本。 Windows 7 SP1 和 Windows Server 2008 R2 支持它，且它包含在 [Windows 10 2019 年 5 月更新](https://support.microsoft.com/help/4028685/windows-10-get-the-update)中。

## <a name="net-framework-48"></a>.NET Framework 4.8

> [!div class="button"]
> [下载 .NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48)

[.NET Framework 4.8](https://github.com/Microsoft/dotnet/tree/master/releases/net48) 可用于运行针对 .NET Framework 4.0 或更高版本生成的应用程序。

### <a name="offline-installer"></a>脱机安装程序

在 Windows 7 上执行 .NET Framework 的脱机安装时，首先需要确保目标计算机上已安装最新的 [Microsoft 根证书颁发机构 2011](https://www.microsoft.com/pkiops/Docs/Repository.htm)。

certmgr.exe 工具可以自动安装证书，并从 Visual Studio 或 Windows SDK 获取该证书。 以下命令用于在运行 .NET Framework 安装程序之前安装证书：

```console
certmgr.exe /add MicRooCerAut2011_2011_03_22.crt /s /r localMachine root
```

## <a name="net-framework-35"></a>.NET Framework 3.5

[.NET Framework 3.5](https://dotnet.microsoft.com/download/dotnet-framework/net35-sp1) 包含在 Windows 7 中。

.NET Framework 3.5 支持为 .NET Framework 1.0 到 3.5 生成的应用。

## <a name="help"></a>帮助

如果无法确定已安装 .NET Framework 的正确版本，可以[联系 Microsoft 获取帮助](mailto:dotnet-install-help@service.microsoft.com?subject=Install-Help)。

## <a name="see-also"></a>另请参阅

- [下载 .NET Framework](https://dotnet.microsoft.com/download)
- [安装和卸载 .NET Framework 受阻疑难解答](troubleshoot-blocked-installations-and-uninstallations.md)
- [安装面向开发人员的 .NET Framework](guide-for-developers.md)
