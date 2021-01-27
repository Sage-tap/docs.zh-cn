---
ms.openlocfilehash: 27c6353f8f71254a505b434921f4b1e61e64cdda
ms.sourcegitcommit: 2b878d7011306b215dbf3d5dc9c1e78355a6dcd5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2021
ms.locfileid: "98758159"
---
### <a name="modernization-of-the-folderbrowserdialog"></a>FolderBrowserDialog 的现代化

.NET Core 的 Windows 窗体应用程序中的 <xref:System.Windows.Forms.FolderBrowserDialog> 控件已更改。

#### <a name="change-description"></a>更改描述

在 .NET Framework 中，Windows 窗体对 <xref:System.Windows.Forms.FolderBrowserDialog> 控件使用以下对话框：

![.NET Framework 中的 FolderBrowserDialogControl](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-framework.png)

在 .NET Core 3.0 中，Windows 窗体使用 Windows Vista 中引入的更新的基于 COM 的控件：

![.NET Core 中的 FolderBrowserDialogControl](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-core.png)

#### <a name="version-introduced"></a>引入的版本

3.0

#### <a name="recommended-action"></a>建议操作

此对话框将自动升级。

如果希望保留原始对话框，请在显示对话框之前将 <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> 属性设置为 `false`，如以下代码片段所示：

```csharp
var dialog = new FolderBrowserDialog();
dialog.AutoUpgradeEnabled = false;
dialog.ShowDialog();
```

#### <a name="category"></a>类别

Windows 窗体

#### <a name="affected-apis"></a>受影响的 API

- <xref:System.Windows.Forms.FolderBrowserDialog>

<!--

#### Affected APIs

- `T:System.Windows.Forms.FolderBrowserDialog`

-->
