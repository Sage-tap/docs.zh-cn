---
title: 教程：安装和使用 .NET 本地工具
description: 了解如何安装和使用 .NET 工具作为本地工具。
ms.topic: tutorial
ms.date: 12/11/2020
ms.openlocfilehash: 29c561d27aad99c0383fc8e0bb5a4543ae65705a
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2021
ms.locfileid: "102104123"
---
# <a name="tutorial-install-and-use-a-net-local-tool-using-the-net-cli"></a><span data-ttu-id="96091-103">教程：使用 .NET CLI 安装和使用 .NET 本地工具</span><span class="sxs-lookup"><span data-stu-id="96091-103">Tutorial: Install and use a .NET local tool using the .NET CLI</span></span>

<span data-ttu-id="96091-104"> 本文适用于： ✔️ .NET Core 3.0 SDK 及更高版本</span><span class="sxs-lookup"><span data-stu-id="96091-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

<span data-ttu-id="96091-105">本教程介绍如何安装和使用本地工具。</span><span class="sxs-lookup"><span data-stu-id="96091-105">This tutorial teaches you how to install and use a local tool.</span></span> <span data-ttu-id="96091-106">使用在[本系列的第一个教程](global-tools-how-to-create.md)中创建的工具。</span><span class="sxs-lookup"><span data-stu-id="96091-106">You use a tool that you create in the [first tutorial of this series](global-tools-how-to-create.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="96091-107">先决条件</span><span class="sxs-lookup"><span data-stu-id="96091-107">Prerequisites</span></span>

* <span data-ttu-id="96091-108">完成[本系列的第一个教程](global-tools-how-to-create.md)。</span><span class="sxs-lookup"><span data-stu-id="96091-108">Complete the [first tutorial of this series](global-tools-how-to-create.md).</span></span>
* <span data-ttu-id="96091-109">安装 .NET Core 2.1 运行时。</span><span class="sxs-lookup"><span data-stu-id="96091-109">Install the .NET Core 2.1 runtime.</span></span>

  <span data-ttu-id="96091-110">在本教程中，安装和使用面向 .NET Core 2.1 的工具，因此需要在计算机上安装该运行时。</span><span class="sxs-lookup"><span data-stu-id="96091-110">For this tutorial you install and use a tool that targets .NET Core 2.1, so you need to have that runtime installed on your machine.</span></span> <span data-ttu-id="96091-111">若要安装 2.1 运行时，请转到 [.NET Core 2.1 下载页面](https://dotnet.microsoft.com/download/dotnet/2.1)并在“运行应用 - 运行时”  列中查找运行时安装链接。</span><span class="sxs-lookup"><span data-stu-id="96091-111">To install the 2.1 runtime, go to the [.NET Core 2.1 download page](https://dotnet.microsoft.com/download/dotnet/2.1) and find the runtime installation link in the **Run apps - Runtime** column.</span></span>

## <a name="create-a-manifest-file"></a><span data-ttu-id="96091-112">创建清单文件</span><span class="sxs-lookup"><span data-stu-id="96091-112">Create a manifest file</span></span>

<span data-ttu-id="96091-113">若要安装仅用于本地访问的工具（对于当前目录和子目录），必须将其添加到清单文件。</span><span class="sxs-lookup"><span data-stu-id="96091-113">To install a tool for local access only (for the current directory and subdirectories), it has to be added to a manifest file.</span></span>

<span data-ttu-id="96091-114">在“microsoft.botsay”文件夹中，向上导航一个级别到“repository”文件夹   ：</span><span class="sxs-lookup"><span data-stu-id="96091-114">From the *microsoft.botsay* folder, navigate up one level to the *repository* folder:</span></span>

```console
cd ..
```

<span data-ttu-id="96091-115">通过运行 [dotnet new](dotnet-new.md) 命令来创建清单文件：</span><span class="sxs-lookup"><span data-stu-id="96091-115">Create a manifest file by running the [dotnet new](dotnet-new.md) command:</span></span>

```dotnetcli
dotnet new tool-manifest
```

<span data-ttu-id="96091-116">输出指示文件创建成功。</span><span class="sxs-lookup"><span data-stu-id="96091-116">The output indicates successful creation of the file.</span></span>

```console
The template "Dotnet local tool manifest file" was created successfully.
```

<span data-ttu-id="96091-117">.config/dotnet-tools.json 文件中尚无工具  ：</span><span class="sxs-lookup"><span data-stu-id="96091-117">The *.config/dotnet-tools.json* file has no tools in it yet:</span></span>

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {}
}
```

<span data-ttu-id="96091-118">清单文件中列出的工具可用于当前目录和子目录。</span><span class="sxs-lookup"><span data-stu-id="96091-118">The tools listed in a manifest file are available to the current directory and subdirectories.</span></span> <span data-ttu-id="96091-119">当前目录是包含具有清单文件的 .config 目录的目录  。</span><span class="sxs-lookup"><span data-stu-id="96091-119">The current directory is the one that contains the *.config* directory with the manifest file.</span></span>

<span data-ttu-id="96091-120">使用引用本地工具的 CLI 命令时，SDK 会在当前目录和父目录中搜索清单文件。</span><span class="sxs-lookup"><span data-stu-id="96091-120">When you use a CLI command that refers to a local tool, the SDK searches for a manifest file in the current directory and parent directories.</span></span> <span data-ttu-id="96091-121">如果它找到清单文件，但该文件不包含所引用的工具，则会通过父目录继续向上搜索。</span><span class="sxs-lookup"><span data-stu-id="96091-121">If it finds a manifest file, but the file doesn't include the referenced tool, it continues the search up through parent directories.</span></span> <span data-ttu-id="96091-122">搜索在找到所引用的工具或找到将 `isRoot` 设置为 `true` 的清单文件时结束。</span><span class="sxs-lookup"><span data-stu-id="96091-122">The search ends when it finds the referenced tool or it finds a manifest file with `isRoot` set to `true`.</span></span>

## <a name="install-botsay-as-a-local-tool"></a><span data-ttu-id="96091-123">将 botsay 作为本地工具安装</span><span class="sxs-lookup"><span data-stu-id="96091-123">Install botsay as a local tool</span></span>

<span data-ttu-id="96091-124">从在第一个教程中创建的包中安装该工具：</span><span class="sxs-lookup"><span data-stu-id="96091-124">Install the tool from the package that you created in the first tutorial:</span></span>

```dotnetcli
dotnet tool install --add-source ./microsoft.botsay/nupkg microsoft.botsay
```

<span data-ttu-id="96091-125">此命令将该工具添加到在上一步中创建的清单文件。</span><span class="sxs-lookup"><span data-stu-id="96091-125">This command adds the tool to the manifest file that you created in the preceding step.</span></span> <span data-ttu-id="96091-126">命令输出显示新安装的工具所在的清单文件：</span><span class="sxs-lookup"><span data-stu-id="96091-126">The command output shows which manifest file the newly installed tool is in:</span></span>

 ```console
 You can invoke the tool from this directory using the following command:
 'dotnet tool run botsay' or 'dotnet botsay'
 Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
 Entry is added to the manifest file /home/name/repository/.config/dotnet-tools.json
 ```

<span data-ttu-id="96091-127">.config/dotnet-tools.json 文件现在有一个工具  ：</span><span class="sxs-lookup"><span data-stu-id="96091-127">The *.config/dotnet-tools.json* file now has one tool:</span></span>

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "microsoft.botsay": {
      "version": "1.0.0",
      "commands": [
        "botsay"
      ]
    }
  }
}
```

## <a name="use-the-tool"></a><span data-ttu-id="96091-128">使用该工具</span><span class="sxs-lookup"><span data-stu-id="96091-128">Use the tool</span></span>

<span data-ttu-id="96091-129">通过运行“repository”  文件夹中的 `dotnet tool run` 命令来调用该工具：</span><span class="sxs-lookup"><span data-stu-id="96091-129">Invoke the tool by running the `dotnet tool run` command from the *repository* folder:</span></span>

```dotnetcli
dotnet tool run botsay hello from the bot
```

## <a name="restore-a-local-tool-installed-by-others"></a><span data-ttu-id="96091-130">还原其他人安装的本地工具</span><span class="sxs-lookup"><span data-stu-id="96091-130">Restore a local tool installed by others</span></span>

<span data-ttu-id="96091-131">通常将本地工具安装在存储库的根目录中。</span><span class="sxs-lookup"><span data-stu-id="96091-131">You typically install a local tool in the root directory of the repository.</span></span> <span data-ttu-id="96091-132">将清单文件签入到存储库后，其他开发人员可以获得最新的清单文件。</span><span class="sxs-lookup"><span data-stu-id="96091-132">After you check in the manifest file to the repository, other developers can get the latest manifest file.</span></span> <span data-ttu-id="96091-133">若要安装清单文件中列出的所有工具，他们可以运行单个 `dotnet tool restore` 命令。</span><span class="sxs-lookup"><span data-stu-id="96091-133">To install all of the tools listed in the manifest file, they can run a single `dotnet tool restore` command.</span></span>

1. <span data-ttu-id="96091-134">打开 .config/dotnet-tools.json  文件并将内容替换为以下 JSON：</span><span class="sxs-lookup"><span data-stu-id="96091-134">Open the *.config/dotnet-tools.json* file, and replace the contents with the following JSON:</span></span>

   ```json
   {
     "version": 1,
     "isRoot": true,
     "tools": {
       "microsoft.botsay": {
         "version": "1.0.0",
         "commands": [
           "botsay"
         ]
       },
       "dotnetsay": {
         "version": "2.1.3",
         "commands": [
           "dotnetsay"
         ]
       }
     }
   }
   ```

1. <span data-ttu-id="96091-135">将 `<name>` 替换为用于创建项目的名称。</span><span class="sxs-lookup"><span data-stu-id="96091-135">Replace `<name>` with the name you used to create the project.</span></span>

1. <span data-ttu-id="96091-136">保存更改。</span><span class="sxs-lookup"><span data-stu-id="96091-136">Save your changes.</span></span>

   <span data-ttu-id="96091-137">进行此更改等同于在其他人安装项目目录的包 `dotnetsay` 后从存储库获取最新版本。</span><span class="sxs-lookup"><span data-stu-id="96091-137">Making this change is the same as getting the latest version from the repository after someone else installed the package `dotnetsay` for the project directory.</span></span>

1. <span data-ttu-id="96091-138">运行 `dotnet tool restore` 命令。</span><span class="sxs-lookup"><span data-stu-id="96091-138">Run the `dotnet tool restore` command.</span></span>

   ```dotnetcli
   dotnet tool restore
   ```

   <span data-ttu-id="96091-139">该命令生成的输出如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="96091-139">The command produces output like the following example:</span></span>

   ```console
   Tool 'microsoft.botsay' (version '1.0.0') was restored. Available commands: botsay
   Tool 'dotnetsay' (version '2.1.3') was restored. Available commands: dotnetsay
   Restore was successful.
   ```

1. <span data-ttu-id="96091-140">验证工具是否可用：</span><span class="sxs-lookup"><span data-stu-id="96091-140">Verify that the tools are available:</span></span>

   ```dotnetcli
   dotnet tool list
   ```

   <span data-ttu-id="96091-141">输出是包和命令的列表，类似于以下示例：</span><span class="sxs-lookup"><span data-stu-id="96091-141">The output is a list of packages and commands, similar to the following example:</span></span>

   ```console
   Package Id      Version      Commands       Manifest
   --------------------------------------------------------------------------------------------
   microsoft.botsay 1.0.0        botsay         /home/name/repository/.config/dotnet-tools.json
   dotnetsay        2.1.3        dotnetsay      /home/name/repository/.config/dotnet-tools.json
   ```

1. <span data-ttu-id="96091-142">测试工具：</span><span class="sxs-lookup"><span data-stu-id="96091-142">Test the tools:</span></span>

   ```dotnetcli
   dotnet tool run dotnetsay hello from dotnetsay
   dotnet tool run botsay hello from botsay
   ```

## <a name="update-a-local-tool"></a><span data-ttu-id="96091-143">更新本地工具</span><span class="sxs-lookup"><span data-stu-id="96091-143">Update a local tool</span></span>

<span data-ttu-id="96091-144">本地工具 `dotnetsay` 的已安装版本为 2.1.3。</span><span class="sxs-lookup"><span data-stu-id="96091-144">The installed version of local tool `dotnetsay` is 2.1.3.</span></span>  <span data-ttu-id="96091-145">使用 [dotnet tool update](dotnet-tool-update.md) 命令将工具更新到最新版本。</span><span class="sxs-lookup"><span data-stu-id="96091-145">Use the [dotnet tool update](dotnet-tool-update.md) command to update the tool to the latest version.</span></span>

```dotnetcli
dotnet tool update dotnetsay
```

<span data-ttu-id="96091-146">输出指示新的版本号：</span><span class="sxs-lookup"><span data-stu-id="96091-146">The output indicates the new version number:</span></span>

```console
Tool 'dotnetsay' was successfully updated from version '2.1.3' to version '2.1.7'
(manifest file /home/name/repository/.config/dotnet-tools.json).
```

<span data-ttu-id="96091-147">update 命令查找包含包 ID 的第一个清单文件并对其进行更新。</span><span class="sxs-lookup"><span data-stu-id="96091-147">The update command finds the first manifest file that contains the package ID and updates it.</span></span> <span data-ttu-id="96091-148">如果搜索范围内的任何清单文件中都没有此类包 ID，SDK 会将新条目添加到最近的清单文件。</span><span class="sxs-lookup"><span data-stu-id="96091-148">If there is no such package ID in any manifest file that is in the scope of the search, the SDK adds a new entry to the closest manifest file.</span></span> <span data-ttu-id="96091-149">搜索范围上至父目录，直到找到具有 `isRoot = true` 的清单文件。</span><span class="sxs-lookup"><span data-stu-id="96091-149">The search scope is up through parent directories until a manifest file with `isRoot = true` is found.</span></span>

## <a name="remove-local-tools"></a><span data-ttu-id="96091-150">删除本地工具</span><span class="sxs-lookup"><span data-stu-id="96091-150">Remove local tools</span></span>

<span data-ttu-id="96091-151">通过运行 [dotnet tool uninstall](dotnet-tool-uninstall.md) 命令来删除已安装的工具：</span><span class="sxs-lookup"><span data-stu-id="96091-151">Remove the installed tools by running the [dotnet tool uninstall](dotnet-tool-uninstall.md) command:</span></span>

```dotnetcli
dotnet tool uninstall microsoft.botsay
```

```dotnetcli
dotnet tool uninstall dotnetsay
```

## <a name="troubleshoot"></a><span data-ttu-id="96091-152">疑难解答</span><span class="sxs-lookup"><span data-stu-id="96091-152">Troubleshoot</span></span>

<span data-ttu-id="96091-153">如果在学习本教程时收到错误消息，请参阅[排查 .NET 工具使用问题](troubleshoot-usage-issues.md)。</span><span class="sxs-lookup"><span data-stu-id="96091-153">If you get an error message while following the tutorial, see [Troubleshoot .NET tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="96091-154">请参阅</span><span class="sxs-lookup"><span data-stu-id="96091-154">See also</span></span>

<span data-ttu-id="96091-155">有关详细信息，请参阅 [.NET 工具](global-tools.md)</span><span class="sxs-lookup"><span data-stu-id="96091-155">For more information, see [.NET tools](global-tools.md)</span></span>
