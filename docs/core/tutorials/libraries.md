---
title: 使用 .NET CLI 开发库
description: 了解如何使用 .NET CLI 创建 .NET 库。 将创建一个支持多个框架的库。
author: cartermp
ms.topic: how-to
ms.date: 12/14/2020
ms.openlocfilehash: 76d08007e191fe9090f3f14c906a40e84e37bd19
ms.sourcegitcommit: 4df8e005c074ceb1f978f007b222fe253be2baf3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/04/2021
ms.locfileid: "99548404"
---
# <a name="develop-libraries-with-the-net-cli"></a>使用 .NET CLI 开发库

本文介绍如何使用 .NET CLI 编写 .NET 的库。 CLI 提供可跨任何支持的 OS 工作的高效低级别体验。 仍可使用 Visual Studio 生成库，如果你首选这种体验，请[参阅 Visual Studio 指南](library-with-visual-studio.md)。

## <a name="prerequisites"></a>先决条件

需要在计算机上安装 [.NET SDK](https://dotnet.microsoft.com/download)。

对于本文档中处理 .NET Framework 版本的部分，需要在 Windows 计算机上安装 [.NET Framework](https://dotnet.microsoft.com/download/dotnet-framework)。

此外，如果想要支持较旧的 .NET Framework 目标，需要从 [.NET Framework 下载页](https://dotnet.microsoft.com/download/dotnet-framework)安装目标包或开发人员工具包。 请参阅此表：

| .NET Framework 版本 | 下载内容                                       |
| ---------------------- | ------------------------------------------------------ |
| 4.6.1                  | .NET Framework 4.6.1 目标包                    |
| 4.6                    | .NET Framework 4.6 目标包                      |
| 4.5.2                  | .NET Framework 4.5.2 开发人员工具包                    |
| 4.5.1                  | .NET Framework 4.5.1 开发人员工具包                    |
| 4.5                    | 适用于 Windows 8 的 Windows 软件开发工具包         |
| 4.0                    | Windows SDK for Windows 7 和 .NET Framework 4         |
| 2.0、3.0 和 3.5      | .NET Framework 3.5 SP1 运行时（或 Windows 8+ 版本） |

## <a name="how-to-target-net-50-or-net-standard"></a>如何以 .NET 5.0 或 .NET Standard 为目标

你可以通过将项目的目标框架添加到项目文件（.csproj 或 .fsproj）来控制项目的目标框架 。 有关如何选择以 .NET 5.0 还是 .NET Standard 为目标的指导，请参阅 [.NET 5 和 .NET Standard](../../standard/net-standard.md#net-5-and-net-standard)。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
  </PropertyGroup>
</Project>
```

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
  </PropertyGroup>
</Project>
```

如果希望面向 .NET Framework 版本 4.0 或更低版本，或者要使用 .NET Framework 中提供但 .NET Standard 中不提供的 API（例如 `System.Drawing`），请阅读以下部分，了解如何设定多目标。

## <a name="how-to-target-net-framework"></a>如何面向 .NET framework

> [!NOTE]
> 这些说明假定计算机上安装有 .NET Framework。 请参阅[先决条件](#prerequisites) 获取安装的依赖项。

请记住，此处使用的某些 .NET Framework 版本不再受支持。 有关不受支持的版本信息，请参阅 [.NET Framework 支持生命周期策略常见问题](https://support.microsoft.com/gp/framework_faq/en-us)。

如果要达到最大数量的开发人员和项目，可将 .NET Framework 4.0 用作基线目标。 若要以 .NET Framework 为目标，首先使用与要支持的 .NET Framework 版本相对应的正确目标框架名字对象 (TFM)。

| .NET Framework 版本 | TFM      |
| ---------------------- | -------- |
| .NET Framework 2.0     | `net20`  |
| .NET Framework 3.0     | `net30`  |
| .NET Framework 3.5     | `net35`  |
| .NET Framework 4.0     | `net40`  |
| .NET Framework 4.5     | `net45`  |
| .NET Framework 4.5.1   | `net451` |
| .NET Framework 4.5.2   | `net452` |
| .NET Framework 4.6     | `net46`  |
| .NET Framework 4.6.1   | `net461` |
| .NET Framework 4.6.2   | `net462` |
| .NET Framework 4.7     | `net47`  |
| .NET Framework 4.8     | `net48`  |

然后将此 TFM 插入项目文件的 `TargetFramework` 部分。 例如，下面展示了如何编写面向 .NET Framework 4.0 的库：

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net40</TargetFramework>
  </PropertyGroup>
</Project>
```

大功告成！ 虽然此库仅针对 .NET Framework 4 编译，但可在较新版本的 .NET Framework 上使用此库。

## <a name="how-to-multitarget"></a>如何设定多目标

> [!NOTE]
> 以下说明假定计算机上安装有 .NET Framework。 请参阅[先决条件](#prerequisites)部分，了解需要安装哪些依赖项以及在何处下载。

如果项目同时支持 .NET Framework 和 .NET，可能需要以较旧版本的 .NET Framework 为目标。 在此方案中，如果要为较新目标使用较新的 API 和语言构造，请在代码中使用 `#if` 指令。 可能还需要为要面向的每个平台添加不同的包和依赖项，以包含每种情况所需的不同 API。

例如，假设有一个库，它通过 HTTP 执行联网操作。 对于 .NET Standard 和 .NET Framework 版本 4.5 或更高版本，可从 `System.Net.Http` 命名空间使用 `HttpClient` 类。 但是，.NET Framework 的早期版本没有 `HttpClient` 类，因此可对早期版本使用 `System.Net` 命名空间中的 `WebClient` 类。

项目文件可能如下所示：

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netstandard2.0;net40;net45</TargetFrameworks>
  </PropertyGroup>

  <!-- Need to conditionally bring in references for the .NET Framework 4.0 target -->
  <ItemGroup Condition="'$(TargetFramework)' == 'net40'">
    <Reference Include="System.Net" />
  </ItemGroup>

  <!-- Need to conditionally bring in references for the .NET Framework 4.5 target -->
  <ItemGroup Condition="'$(TargetFramework)' == 'net45'">
    <Reference Include="System.Net.Http" />
    <Reference Include="System.Threading.Tasks" />
  </ItemGroup>
</Project>
```

在此处可看到三项主要更改：

1. `TargetFramework` 节点已替换为 `TargetFrameworks`，其中表示了三个 TFM。
1. `net40` 目标有一个 `<ItemGroup>` 节点，拉取一个 .NET Framework 引用。
1. `net45` 目标中有一个 `<ItemGroup>` 节点，拉取两个 .NET Framework 引用。

生成系统可识别以下用在 `#if` 指令中的处理器符号：

[!INCLUDE [Preprocessor symbols](../../../includes/preprocessor-symbols.md)]

以下是使用每目标条件编译的示例：

```csharp
using System;
using System.Text.RegularExpressions;
#if NET40
// This only compiles for the .NET Framework 4 targets
using System.Net;
#else
 // This compiles for all other targets
using System.Net.Http;
using System.Threading.Tasks;
#endif

namespace MultitargetLib
{
    public class Library
    {
#if NET40
        private readonly WebClient _client = new WebClient();
        private readonly object _locker = new object();
#else
        private readonly HttpClient _client = new HttpClient();
#endif

#if NET40
        // .NET Framework 4.0 does not have async/await
        public string GetDotNetCount()
        {
            string url = "https://www.dotnetfoundation.org/";

            var uri = new Uri(url);

            string result = "";

            // Lock here to provide thread-safety.
            lock(_locker)
            {
                result = _client.DownloadString(uri);
            }

            int dotNetCount = Regex.Matches(result, ".NET").Count;

            return $"Dotnet Foundation mentions .NET {dotNetCount} times!";
        }
#else
        // .NET Framework 4.5+ can use async/await!
        public async Task<string> GetDotNetCountAsync()
        {
            string url = "https://www.dotnetfoundation.org/";

            // HttpClient is thread-safe, so no need to explicitly lock here
            var result = await _client.GetStringAsync(url);

            int dotNetCount = Regex.Matches(result, ".NET").Count;

            return $"dotnetfoundation.org mentions .NET {dotNetCount} times in its HTML!";
        }
#endif
    }
}
```

如果使用 `dotnet build` 生成此项目，则在 `bin/` 文件夹下有三个目录：

```
net40/
net45/
netstandard2.0/
```

其中每个目录都包含每个目标的 `.dll` 文件。

## <a name="how-to-test-libraries-on-net"></a>如何在 .NET 上测试库

能够跨平台进行测试至关重要。 可使用现成的 [xUnit](https://xunit.net/) 或 MSTest。 它们都非常适合在 .NET 上对库进行单元测试。 如何使用测试项目设置解决方案取决于[解决方案的结构](#structuring-a-solution)。 下面的示例假设测试和源目录位于同一顶级目录下。

> [!NOTE]
> 此示例将使用某些 [.NET CLI](../tools/index.md) 命令。 有关详细信息，请参阅 [dotnet new](../tools/dotnet-new.md) 和 [dotnet sln](../tools/dotnet-sln.md)。

1. 设置解决方案。 可使用以下命令实现此目的：

   ```dotnetcli
   mkdir SolutionWithSrcAndTest
   cd SolutionWithSrcAndTest
   dotnet new sln
   dotnet new classlib -o MyProject
   dotnet new xunit -o MyProject.Test
   dotnet sln add MyProject/MyProject.csproj
   dotnet sln add MyProject.Test/MyProject.Test.csproj
   ```

   这将创建多个项目，并一个解决方案中将这些项目链接在一起。 `SolutionWithSrcAndTest` 的目录应如下所示：

   ```
   /SolutionWithSrcAndTest
   |__SolutionWithSrcAndTest.sln
   |__MyProject/
   |__MyProject.Test/
   ```

1. 导航到测试项目的目录，然后添加对 `MyProject` 中的 `MyProject.Test` 的引用。

   ```dotnetcli
   cd MyProject.Test
   dotnet add reference ../MyProject/MyProject.csproj
   ```

1. 还原包和生成项目：

   ```dotnetcli
   dotnet restore
   dotnet build
   ```

1. 执行 `dotnet test` 命令，验证 xUnit 是否在运行。 如果选择使用 MSTest，则应改为运行 MSTest 控制台运行程序。

大功告成！ 现在可以使用命令行工具跨所有平台测试库。 若要继续测试，现已设置好了所有内容，测试库将非常简单：

1. 对库进行更改。
1. 使用 `dotnet test` 命令在测试目录中从命令行运行测试。

调用 `dotnet test` 命令时，将自动重新生成代码。

## <a name="how-to-use-multiple-projects"></a>如何使用多个项目

对于较大的库，通常需要将功能置于不同项目中。

假设要生成一个可以惯用的 C# 和 F# 使用的库。 这意味着库的使用者可通过对 C# 或 F# 来说很自然的方式来使用它。 例如，在 C# 中，了能会这样使用库：

```csharp
using AwesomeLibrary.CSharp;

public Task DoThings(Data data)
{
    var convertResult = await AwesomeLibrary.ConvertAsync(data);
    var result = AwesomeLibrary.Process(convertResult);
    // do something with result
}
```

在 F# 中可能是这样：

```fsharp
open AwesomeLibrary.FSharp

let doWork data = async {
    let! result = AwesomeLibrary.AsyncConvert data // Uses an F# async function rather than C# async method
    // do something with result
}
```

这样的使用方案意味着被访问的 API 必须具有用于 C# 和 F# 的不同结构。  通常的方法是将库的所有逻辑因子转化到核心项目中，C# 和 F# 项目定义调用到核心项目的 API 层。  该部分的其余部分将使用以下名称：

* **AwesomeLibrary.Core** - 核心项目，其中包含库的所有逻辑
* **AwesomeLibrary.CSharp** - 具有打算在 C# 中使用的公共 API 的项目
* **AwesomeLibrary.FSharp** - 具有打算在 F# 中使用的公共 API 的项目

可在终端运行下列命令，生成与下列指南相同的结构：

```dotnetcli
mkdir AwesomeLibrary && cd AwesomeLibrary
dotnet new sln
mkdir AwesomeLibrary.Core && cd AwesomeLibrary.Core && dotnet new classlib
cd ..
mkdir AwesomeLibrary.CSharp && cd AwesomeLibrary.CSharp && dotnet new classlib
cd ..
mkdir AwesomeLibrary.FSharp && cd AwesomeLibrary.FSharp && dotnet new classlib -lang "F#"
cd ..
dotnet sln add AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
dotnet sln add AwesomeLibrary.CSharp/AwesomeLibrary.CSharp.csproj
dotnet sln add AwesomeLibrary.FSharp/AwesomeLibrary.FSharp.fsproj
```

这将添加上述三个项目和将它们链接在一起的解决方案文件。 创建解决方案文件并链接项目后，可从顶级还原和生成项目。

### <a name="project-to-project-referencing"></a>项目到项目的引用

引用项目的最佳方式是使用 .NET CLI 添加项目引用。 在 AwesomeLibrary.CSharp 和 AwesomeLibrary.FSharp 项目目录中，可运行下列命令：

```dotnetcli
dotnet add reference ../AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
```

AwesomeLibrary.CSharp 和 AwesomeLibrary.FSharp 的项目文件现在需要将 AwesomeLibrary.Core 作为 `ProjectReference` 目标引用。  可通过检查项目文件和查看其中的下列内容来进行验证：

```xml
<ItemGroup>
  <ProjectReference Include="..\AwesomeLibrary.Core\AwesomeLibrary.Core.csproj" />
</ItemGroup>
```

如果不想使用 .NET CLI，可手动将此部分添加到每个项目文件。

### <a name="structuring-a-solution"></a>结构化解决方案

多项目解决方案的另一个重要方面是建立良好的整体项目结构。 可根据自己的喜好随意组织代码，只要使用 `dotnet sln add` 将每个项目链接到解决方案文件，就可在解决方案级别运行 `dotnet restore` 和 `dotnet build`。
