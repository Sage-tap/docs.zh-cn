---
title: .NET for Apache Spark 入门
description: 了解如何在 Windows、macOS 和 Ubuntu 上使用 .NET Core 运行 .NET for Apache Spark 应用。
ms.date: 10/09/2020
ms.topic: tutorial
ms.custom: mvc
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: 52d37f3c6b4907361bf0933942d8f1757669be24
ms.sourcegitcommit: 38999dc0ec4f7c4404de5ce0951b64c55997d9ab
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/02/2021
ms.locfileid: "99426783"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a><span data-ttu-id="a892a-103">教程：.NET for Apache Spark 入门</span><span class="sxs-lookup"><span data-stu-id="a892a-103">Tutorial: Get started with .NET for Apache Spark</span></span>

<span data-ttu-id="a892a-104">本教程介绍如何在 Windows、macOS 和 Ubuntu 上使用 .NET Core 运行 .NET for Apache Spark 应用。</span><span class="sxs-lookup"><span data-stu-id="a892a-104">This tutorial teaches you how to run a .NET for Apache Spark app using .NET Core on Windows, macOS, and Ubuntu.</span></span>

<span data-ttu-id="a892a-105">在本教程中，你将了解：</span><span class="sxs-lookup"><span data-stu-id="a892a-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="a892a-106">为 .NET for Apache Spark 作环境准备</span><span class="sxs-lookup"><span data-stu-id="a892a-106">Prepare your environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="a892a-107">编写你的第一个 .NET for Apache Spark 应用程序</span><span class="sxs-lookup"><span data-stu-id="a892a-107">Write your first .NET for Apache Spark application</span></span>
> * <span data-ttu-id="a892a-108">生成和运行 .NET for Apache Spark 应用程序</span><span class="sxs-lookup"><span data-stu-id="a892a-108">Build and run your .NET for Apache Spark application</span></span>

## <a name="prepare-your-environment"></a><span data-ttu-id="a892a-109">准备环境</span><span class="sxs-lookup"><span data-stu-id="a892a-109">Prepare your environment</span></span>

<span data-ttu-id="a892a-110">在开始编写应用之前，需要先设置一些必备依赖项。</span><span class="sxs-lookup"><span data-stu-id="a892a-110">Before you begin writing your app, you need to set up some prerequisite dependencies.</span></span> <span data-ttu-id="a892a-111">如果可从命令行环境运行 `dotnet`、`java`、`spark-shell`，则表示你的环境已准备就绪且你可跳到下一部分。</span><span class="sxs-lookup"><span data-stu-id="a892a-111">If you can run `dotnet`, `java`, `spark-shell` from your command line environment, then your environment is already prepared and you can skip to the next section.</span></span> <span data-ttu-id="a892a-112">如果无法运行任何或部分命令，请执行以下步骤。</span><span class="sxs-lookup"><span data-stu-id="a892a-112">If you cannot run any or all of the commands, do the following steps.</span></span>

### <a name="1-install-net"></a><span data-ttu-id="a892a-113">1.安装 .NET</span><span class="sxs-lookup"><span data-stu-id="a892a-113">1. Install .NET</span></span>

<span data-ttu-id="a892a-114">要开始构建 .NET 应用，需要下载并安装 .NET SDK（软件开发工具包）。</span><span class="sxs-lookup"><span data-stu-id="a892a-114">To start building .NET apps, you need to download and install the .NET SDK (Software Development Kit).</span></span>

<span data-ttu-id="a892a-115">下载并安装 [.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1)。</span><span class="sxs-lookup"><span data-stu-id="a892a-115">Download and install the [.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1).</span></span> <span data-ttu-id="a892a-116">安装 SDK 会将 `dotnet` 工具链添加到路径。</span><span class="sxs-lookup"><span data-stu-id="a892a-116">Installing the SDK adds the `dotnet` toolchain to your PATH.</span></span>

<span data-ttu-id="a892a-117">安装 .NET Core SDK 后，打开一个新的命令提示符或终端，然后运行 `dotnet`。</span><span class="sxs-lookup"><span data-stu-id="a892a-117">Once you've installed the .NET Core SDK, open a new command prompt or terminal and run `dotnet`.</span></span>

<span data-ttu-id="a892a-118">如果该命令运行并打印出有关如何使用 dotnet 的信息，则可转到下一步。</span><span class="sxs-lookup"><span data-stu-id="a892a-118">If the command runs and prints out information about how to use dotnet, can move to the next step.</span></span> <span data-ttu-id="a892a-119">如果收到 `'dotnet' is not recognized as an internal or external command` 错误，请确保在运行命令之前已打开新的命令提示符或终端。</span><span class="sxs-lookup"><span data-stu-id="a892a-119">If you receive a `'dotnet' is not recognized as an internal or external command` error, make sure you opened a **new** command prompt or terminal before running the command.</span></span>

### <a name="2-install-java"></a><span data-ttu-id="a892a-120">2.安装 Java</span><span class="sxs-lookup"><span data-stu-id="a892a-120">2. Install Java</span></span>

<span data-ttu-id="a892a-121">安装适用于 Windows 和 macOS 的 [Java 8.1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)，或适用于 Ubuntu 的 [OpenJDK 8](https://openjdk.java.net/install/)。</span><span class="sxs-lookup"><span data-stu-id="a892a-121">Install [Java 8.1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) for Windows and macOS, or [OpenJDK 8](https://openjdk.java.net/install/) for Ubuntu.</span></span>

<span data-ttu-id="a892a-122">选择适用于操作系统的合适版本。</span><span class="sxs-lookup"><span data-stu-id="a892a-122">Select the appropriate version for your operating system.</span></span> <span data-ttu-id="a892a-123">例如，为 Windows x64 计算机选择 jdk-8u201-windows-x64.exe（如下所示），或为 macOS 计算机选择 jdk-8u231-macosx-x64.dmg 。</span><span class="sxs-lookup"><span data-stu-id="a892a-123">For example, select **jdk-8u201-windows-x64.exe** for a Windows x64 machine (as shown below) or **jdk-8u231-macosx-x64.dmg** for macOS.</span></span> <span data-ttu-id="a892a-124">然后，使用命令 `java` 来验证安装。</span><span class="sxs-lookup"><span data-stu-id="a892a-124">Then, use the command `java` to verify the installation.</span></span>

![Java 下载](https://dotnet.microsoft.com/static/images/java-jdk-downloads-windows.png?v=6BbJHoNyDO-PyYVciImr5wzh2AW_YHNcyb3p093AwPA)

### <a name="3-install-compression-software"></a><span data-ttu-id="a892a-126">3.安装压缩软件</span><span class="sxs-lookup"><span data-stu-id="a892a-126">3. Install compression software</span></span>

<span data-ttu-id="a892a-127">Apache Spark 以 .tgz 压缩文件的形式下载。</span><span class="sxs-lookup"><span data-stu-id="a892a-127">Apache Spark is downloaded as a compressed .tgz file.</span></span> <span data-ttu-id="a892a-128">使用提取程序（如 [7-Zip](https://www.7-zip.org/) 或 [WinZip](https://www.winzip.com/)）来提取文件。</span><span class="sxs-lookup"><span data-stu-id="a892a-128">Use an extraction program, like [7-Zip](https://www.7-zip.org/) or [WinZip](https://www.winzip.com/), to extract the file.</span></span>

### <a name="4-install-apache-spark"></a><span data-ttu-id="a892a-129">4.安装 Apache Spark</span><span class="sxs-lookup"><span data-stu-id="a892a-129">4. Install Apache Spark</span></span>

<span data-ttu-id="a892a-130">[下载并安装 Apache Spark](https://spark.apache.org/downloads.html)。</span><span class="sxs-lookup"><span data-stu-id="a892a-130">[Download and install Apache Spark](https://spark.apache.org/downloads.html).</span></span> <span data-ttu-id="a892a-131">需要从版本 2.3.\* 或者 2.4.0、2.4.1、2.4.3、2.4.4、2.4.5、2.4.6、2.4.7、3.0.0 或 3.0.1 中进行选择（.NET for Apache Spark 与其他版本的 Apache Spark 不兼容）。</span><span class="sxs-lookup"><span data-stu-id="a892a-131">You'll need to select from version 2.3.\* or 2.4.0, 2.4.1, 2.4.3, 2.4.4, 2.4.5, 2.4.6, 2.4.7, 3.0.0, or 3.0.1 (.NET for Apache Spark is not compatible with other versions of Apache Spark).</span></span>

<span data-ttu-id="a892a-132">以下步骤中使用的命令假定你已[下载并安装 Apache Spark 3.0.1](https://spark.apache.org/downloads.html)。</span><span class="sxs-lookup"><span data-stu-id="a892a-132">The commands used in the following steps assume you have [downloaded and installed Apache Spark 3.0.1](https://spark.apache.org/downloads.html).</span></span> <span data-ttu-id="a892a-133">若想要使用其他版本，请将 3.0.1 替换为适当的版本号。</span><span class="sxs-lookup"><span data-stu-id="a892a-133">If you wish to use a different version, replace **3.0.1** with the appropriate version number.</span></span> <span data-ttu-id="a892a-134">然后，提取 .tar 文件和 Apache Spark 文件。</span><span class="sxs-lookup"><span data-stu-id="a892a-134">Then, extract the **.tar** file and the Apache Spark files.</span></span>

<span data-ttu-id="a892a-135">要提取嵌套的 .tar 文件：</span><span class="sxs-lookup"><span data-stu-id="a892a-135">To extract the nested **.tar** file:</span></span>

* <span data-ttu-id="a892a-136">找到你已下载的 spark-3.0.1-bin-hadoop2.7.tgz 文件。</span><span class="sxs-lookup"><span data-stu-id="a892a-136">Locate the **spark-3.0.1-bin-hadoop2.7.tgz** file that you downloaded.</span></span>
* <span data-ttu-id="a892a-137">右键单击该文件，然后选择“7-Zip”->“提取到此处”。</span><span class="sxs-lookup"><span data-stu-id="a892a-137">Right click on the file and select **7-Zip -> Extract here**.</span></span>
* <span data-ttu-id="a892a-138">spark-3.0.1-bin-hadoop2.7.tar 是与你下载的 .tgz 文件一起创建的 。</span><span class="sxs-lookup"><span data-stu-id="a892a-138">**spark-3.0.1-bin-hadoop2.7.tar** is created alongside the **.tgz** file you downloaded.</span></span>

<span data-ttu-id="a892a-139">要提取 Apache Spark 文件：</span><span class="sxs-lookup"><span data-stu-id="a892a-139">To extract the Apache Spark files:</span></span>

* <span data-ttu-id="a892a-140">右键单击 spark-3.0.1-bin-hadoop2.7.tar，然后选择“7-Zip”->“提取文件...” </span><span class="sxs-lookup"><span data-stu-id="a892a-140">Right-click on **spark-3.0.1-bin-hadoop2.7.tar** and select **7-Zip -> Extract files...**</span></span>
* <span data-ttu-id="a892a-141">在“提取到”字段输入“C:\bin” 。</span><span class="sxs-lookup"><span data-stu-id="a892a-141">Enter **C:\bin** in the **Extract to** field.</span></span>
* <span data-ttu-id="a892a-142">取消勾选“提取到”字段下面的复选框。</span><span class="sxs-lookup"><span data-stu-id="a892a-142">Uncheck the checkbox below the **Extract to** field.</span></span>
* <span data-ttu-id="a892a-143">选择“确定”。</span><span class="sxs-lookup"><span data-stu-id="a892a-143">Select **OK**.</span></span>
* <span data-ttu-id="a892a-144">Apache Spark 文件会提取到 C:\bin\spark-3.0.1-bin-hadoop2.7</span><span class="sxs-lookup"><span data-stu-id="a892a-144">The Apache Spark files are extracted to C:\bin\spark-3.0.1-bin-hadoop2.7</span></span>\

![安装 Spark](./media/spark-extract-with-7-zip.png)

<span data-ttu-id="a892a-146">运行以下命令，以设置用于查找 Apache Spark 的环境变量。</span><span class="sxs-lookup"><span data-stu-id="a892a-146">Run the following commands to set the environment variables used to locate Apache Spark.</span></span> <span data-ttu-id="a892a-147">在 Windows 上，确保在管理员模式下运行命令提示符。</span><span class="sxs-lookup"><span data-stu-id="a892a-147">On Windows, make sure to run the command prompt in administrator mode.</span></span>

#### <a name="windows"></a>[<span data-ttu-id="a892a-148">Windows</span><span class="sxs-lookup"><span data-stu-id="a892a-148">Windows</span></span>](#tab/windows)

```console
setx /M HADOOP_HOME C:\bin\spark-3.0.1-bin-hadoop2.7\
setx /M SPARK_HOME C:\bin\spark-3.0.1-bin-hadoop2.7\
setx /M PATH "%PATH%;%HADOOP_HOME%;%SPARK_HOME%\bin" # Warning: Don't run this if your path is already long as it will truncate your path to 1024 characters and potentially remove entries!
```

#### <a name="maclinux"></a>[<span data-ttu-id="a892a-149">Mac/Linux</span><span class="sxs-lookup"><span data-stu-id="a892a-149">Mac/Linux</span></span>](#tab/linux)

```bash
export SPARK_HOME=~/bin/spark-3.0.1-bin-hadoop2.7/
export PATH="$SPARK_HOME/bin:$PATH"
source ~/.bashrc
```

---

<span data-ttu-id="a892a-150">安装所有内容并设置环境变量后，打开新的命令提示符或终端并运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="a892a-150">Once you've installed everything and set your environment variables, open a **new** command prompt or terminal and run the following command:</span></span>

```text
spark-submit --version
```

<span data-ttu-id="a892a-151">如果该命令运行并打印出版本信息，则可转到下一步。</span><span class="sxs-lookup"><span data-stu-id="a892a-151">If the command runs and prints version information, you can move to the next step.</span></span>

<span data-ttu-id="a892a-152">如果收到 `'spark-submit' is not recognized as an internal or external command` 错误，请确保已打开新的命令提示符。</span><span class="sxs-lookup"><span data-stu-id="a892a-152">If you receive a `'spark-submit' is not recognized as an internal or external command` error, make sure you opened a **new** command prompt.</span></span>

### <a name="5-install-net-for-apache-spark"></a><span data-ttu-id="a892a-153">5.安装 .NET for Apache Spark</span><span class="sxs-lookup"><span data-stu-id="a892a-153">5. Install .NET for Apache Spark</span></span>

<span data-ttu-id="a892a-154">从 .NET for Apache Spark GitHub 下载 [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases)。</span><span class="sxs-lookup"><span data-stu-id="a892a-154">Download the [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) release from the .NET for Apache Spark GitHub.</span></span> <span data-ttu-id="a892a-155">例如，如果你在使用 Windows 计算机并计划使用 .NET Core，请[下载 Windows x64 netcoreapp3.1 版本](https://github.com/dotnet/spark/releases)。</span><span class="sxs-lookup"><span data-stu-id="a892a-155">For example if you're on a Windows machine and plan to use .NET Core, [download the Windows x64 netcoreapp3.1 release](https://github.com/dotnet/spark/releases).</span></span>

<span data-ttu-id="a892a-156">要提取 Microsoft.Spark.Worker：</span><span class="sxs-lookup"><span data-stu-id="a892a-156">To extract the Microsoft.Spark.Worker:</span></span>

* <span data-ttu-id="a892a-157">找到你已下载的 Microsoft.Spark.Worker.netcoreapp3.1.win-x64-1.0.0.zip 文件。</span><span class="sxs-lookup"><span data-stu-id="a892a-157">Locate the **Microsoft.Spark.Worker.netcoreapp3.1.win-x64-1.0.0.zip** file that you downloaded.</span></span>
* <span data-ttu-id="a892a-158">右键单击并选择“7-Zip”->“提取文件...”。</span><span class="sxs-lookup"><span data-stu-id="a892a-158">Right-click and select **7-Zip -> Extract files...**.</span></span>
* <span data-ttu-id="a892a-159">在“提取到”字段输入“C:\bin” 。</span><span class="sxs-lookup"><span data-stu-id="a892a-159">Enter **C:\bin** in the **Extract to** field.</span></span>
* <span data-ttu-id="a892a-160">取消勾选“提取到”字段下面的复选框。</span><span class="sxs-lookup"><span data-stu-id="a892a-160">Uncheck the checkbox below the **Extract to** field.</span></span>
* <span data-ttu-id="a892a-161">选择“确定”。</span><span class="sxs-lookup"><span data-stu-id="a892a-161">Select **OK**.</span></span>

### <a name="6-install-winutils-windows-only"></a><span data-ttu-id="a892a-162">6.安装 WinUtils（仅限 Windows）</span><span class="sxs-lookup"><span data-stu-id="a892a-162">6. Install WinUtils (Windows only)</span></span>

<span data-ttu-id="a892a-163">.NET for Apache Spark 要求与 Apache Spark 一起安装 WinUtils。</span><span class="sxs-lookup"><span data-stu-id="a892a-163">.NET for Apache Spark requires WinUtils to be installed alongside Apache Spark.</span></span> <span data-ttu-id="a892a-164">[下载 winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe)。</span><span class="sxs-lookup"><span data-stu-id="a892a-164">[Download winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe).</span></span> <span data-ttu-id="a892a-165">然后，将 WinUtils 复制到 C:\bin\spark-3.0.1-bin-hadoop2.7\bin。</span><span class="sxs-lookup"><span data-stu-id="a892a-165">Then, copy WinUtils into **C:\bin\spark-3.0.1-bin-hadoop2.7\bin**.</span></span>

> [!NOTE]
> <span data-ttu-id="a892a-166">如果你在使用其他版本的 Hadoop（相关批注可参见 Spark 安装文件夹名称的末尾），请[选择与你的 Hadoop 版本兼容的 WinUtils 版本](https://github.com/steveloughran/winutils)。</span><span class="sxs-lookup"><span data-stu-id="a892a-166">If you are using a different version of Hadoop, which is annotated at the end of your Spark install folder name, [select the version of WinUtils](https://github.com/steveloughran/winutils) that's compatible with your version of Hadoop.</span></span>

### <a name="7-set-dotnet_worker_dir-and-check-dependencies"></a><span data-ttu-id="a892a-167">7.设置 DOTNET_WORKER_DIR 并检查依赖项</span><span class="sxs-lookup"><span data-stu-id="a892a-167">7. Set DOTNET_WORKER_DIR and check dependencies</span></span>

<span data-ttu-id="a892a-168">运行以下命令之一来设置 `DOTNET_WORKER_DIR` 环境变量，.NET 应用使用该变量查找 .NET for Apache Spark 辅助角色二进制文件。</span><span class="sxs-lookup"><span data-stu-id="a892a-168">Run one of the following commands to set the `DOTNET_WORKER_DIR` environment variable, which is used by .NET apps to locate .NET for Apache Spark worker binaries.</span></span> <span data-ttu-id="a892a-169">确保将 `<PATH-DOTNET_WORKER_DIR>` 替换为你下载并提取 `Microsoft.Spark.Worker` 的目录。</span><span class="sxs-lookup"><span data-stu-id="a892a-169">Make sure to replace `<PATH-DOTNET_WORKER_DIR>` with the directory where you downloaded and extracted the `Microsoft.Spark.Worker`.</span></span> <span data-ttu-id="a892a-170">在 Windows 上，确保在管理员模式下运行命令提示符。</span><span class="sxs-lookup"><span data-stu-id="a892a-170">On Windows, make sure to run the command prompt in administrator mode.</span></span>

#### <a name="windows"></a>[<span data-ttu-id="a892a-171">Windows</span><span class="sxs-lookup"><span data-stu-id="a892a-171">Windows</span></span>](#tab/windows)

```console
setx /M DOTNET_WORKER_DIR <PATH-DOTNET-WORKER-DIR>
```

#### <a name="maclinux"></a>[<span data-ttu-id="a892a-172">Mac/Linux</span><span class="sxs-lookup"><span data-stu-id="a892a-172">Mac/Linux</span></span>](#tab/linux)

```bash
export DOTNET_WORKER_DIR=<PATH-DOTNET-WORKER-DIR>
```

---

<span data-ttu-id="a892a-173">最后，仔细检查是否可从命令行运行 `dotnet`、`java`、`spark-shell`，然后再转到下一部分。</span><span class="sxs-lookup"><span data-stu-id="a892a-173">Finally, double-check that you can run `dotnet`, `java`, `spark-shell` from your command line before you move to the next section.</span></span>

## <a name="write-a-net-for-apache-spark-app"></a><span data-ttu-id="a892a-174">编写 .NET for Apache Spark 应用</span><span class="sxs-lookup"><span data-stu-id="a892a-174">Write a .NET for Apache Spark app</span></span>

### <a name="1-create-a-console-app"></a><span data-ttu-id="a892a-175">1.创建控制台应用</span><span class="sxs-lookup"><span data-stu-id="a892a-175">1. Create a console app</span></span>

<span data-ttu-id="a892a-176">在命令提示符处或终端中，运行以下命令来创建新的控制台应用程序：</span><span class="sxs-lookup"><span data-stu-id="a892a-176">In your command prompt or terminal, run the following commands to create a new console application:</span></span>

```dotnetcli
dotnet new console -o MySparkApp
cd MySparkApp
```

<span data-ttu-id="a892a-177">`dotnet` 命令将创建 `console` 类型的 `new` 应用程序。</span><span class="sxs-lookup"><span data-stu-id="a892a-177">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="a892a-178">`-o` 参数将创建名为 MySparkApp 的目录，其中会存储你的应用并填充必需文件。</span><span class="sxs-lookup"><span data-stu-id="a892a-178">The `-o` parameter creates a directory named *MySparkApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="a892a-179">`cd MySparkApp` 命令会将目录更改为你创建的应用目录。</span><span class="sxs-lookup"><span data-stu-id="a892a-179">The `cd MySparkApp` command changes the directory to the app directory you created.</span></span>

### <a name="2-install-nuget-package"></a><span data-ttu-id="a892a-180">2.安装 NuGet 包</span><span class="sxs-lookup"><span data-stu-id="a892a-180">2. Install NuGet package</span></span>

<span data-ttu-id="a892a-181">要在应用中使用 .NET for Apache Spark，请安装 Microsoft.Spark 包。</span><span class="sxs-lookup"><span data-stu-id="a892a-181">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="a892a-182">在命令提示符处或终端中运行下面的命令：</span><span class="sxs-lookup"><span data-stu-id="a892a-182">In your command prompt or terminal, run the following command:</span></span>

```dotnetcli
dotnet add package Microsoft.Spark
```

> [!NOTE]
> <span data-ttu-id="a892a-183">除非另行指定，否则本教程使用最新版本的 `Microsoft.Spark` NuGet 包。</span><span class="sxs-lookup"><span data-stu-id="a892a-183">This tutorial uses the latest version of the `Microsoft.Spark` NuGet package unless otherwise specified.</span></span>

### <a name="3-write-your-app"></a><span data-ttu-id="a892a-184">3.编写你的应用</span><span class="sxs-lookup"><span data-stu-id="a892a-184">3. Write your app</span></span>

<span data-ttu-id="a892a-185">在 Visual Studio Code 中打开 Program.cs 或打开任何文本编辑器，再将所有代码替换为以下内容：</span><span class="sxs-lookup"><span data-stu-id="a892a-185">Open *Program.cs* in Visual Studio Code, or any text editor, and replace all of the code with the following:</span></span>

```csharp
using Microsoft.Spark.Sql;
using static Microsoft.Spark.Sql.Functions;

namespace MySparkApp
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create Spark session
            SparkSession spark =
                SparkSession
                    .Builder()
                    .AppName("word_count_sample")
                    .GetOrCreate();

            // Create initial DataFrame
            string filePath = args[0];
            DataFrame dataFrame = spark.Read().Text(filePath);

            //Count words
            DataFrame words =
                dataFrame
                    .Select(Split(Col("value")," ").Alias("words"))
                    .Select(Explode(Col("words")).Alias("word"))
                    .GroupBy("word")
                    .Count()
                    .OrderBy(Col("count").Desc());

            // Display results
            words.Show();

            // Stop Spark session
            spark.Stop();
        }
    }
}
```

<span data-ttu-id="a892a-186">[SparkSession](xref:Microsoft.Spark.Sql.SparkSession) 是 Apache Spark 应用程序的入口点，用于管理应用程序的上下文和信息。</span><span class="sxs-lookup"><span data-stu-id="a892a-186">[SparkSession](xref:Microsoft.Spark.Sql.SparkSession) is the entrypoint of Apache Spark applications, which manages the context and information of your application.</span></span> <span data-ttu-id="a892a-187">使用 [Text](xref:Microsoft.Spark.Sql.DataFrameReader.Text%2A) 方法，`filePath` 指定的文件中的文本数据将读入 [DataFrame](xref:Microsoft.Spark.Sql.DataFrame)。</span><span class="sxs-lookup"><span data-stu-id="a892a-187">Using the [Text](xref:Microsoft.Spark.Sql.DataFrameReader.Text%2A) method, the text data from the file specified by the `filePath` is read into a [DataFrame](xref:Microsoft.Spark.Sql.DataFrame).</span></span> <span data-ttu-id="a892a-188">DataFrame 是一种将数据组织到一组命名列中的方法。</span><span class="sxs-lookup"><span data-stu-id="a892a-188">A DataFrame is a way of organizing data into a set of named columns.</span></span> <span data-ttu-id="a892a-189">然后，将应用一系列转换来拆分文件中的句子，对每个单词进行分组和计数，并按降序顺序进行排序。</span><span class="sxs-lookup"><span data-stu-id="a892a-189">Then, a series of transformations is applied to split the sentences in the file, group each of the words, count them and order them in descending order.</span></span> <span data-ttu-id="a892a-190">这些操作的结果存储在另一个 DataFrame 中。</span><span class="sxs-lookup"><span data-stu-id="a892a-190">The result of these operations is stored in another DataFrame.</span></span> <span data-ttu-id="a892a-191">请注意，此时不会执行任何操作，因为 .NET for Apache Spark 会对数据进行惰性计算。</span><span class="sxs-lookup"><span data-stu-id="a892a-191">Note that at this point, no operations have taken place because .NET for Apache Spark lazily evaluates the data.</span></span> <span data-ttu-id="a892a-192">在调用 [Show](xref:Microsoft.Spark.Sql.DataFrame.Show%2A) 方法之前，不会向控制台显示 `words` 转换为 DataFrame 的内容，即执行在上面的行中定义的操作。</span><span class="sxs-lookup"><span data-stu-id="a892a-192">It's not until the [Show](xref:Microsoft.Spark.Sql.DataFrame.Show%2A) method is called to display the contents of the `words` transformed DataFrame to the console that the operations defined in the lines above execute.</span></span> <span data-ttu-id="a892a-193">不再需要 Spark 会话后，请使用 [Stop](xref:Microsoft.Spark.Sql.SparkSession.Stop%2A) 方法停止会话。</span><span class="sxs-lookup"><span data-stu-id="a892a-193">Once you no longer need the Spark session, use the [Stop](xref:Microsoft.Spark.Sql.SparkSession.Stop%2A) method to stop your session.</span></span>

### <a name="4-create-data-file"></a><span data-ttu-id="a892a-194">4.创建数据文件</span><span class="sxs-lookup"><span data-stu-id="a892a-194">4. Create data file</span></span>

<span data-ttu-id="a892a-195">你的应用会处理包含多行文本的文件。</span><span class="sxs-lookup"><span data-stu-id="a892a-195">Your app processes a file containing lines of text.</span></span> <span data-ttu-id="a892a-196">在 MySparkApp 目录中创建一个名为 input.txt 的文件，其中包含以下文本：</span><span class="sxs-lookup"><span data-stu-id="a892a-196">Create a file called *input.txt* file in your *MySparkApp* directory, containing the following text:</span></span>

```text
Hello World
This .NET app uses .NET for Apache Spark
This .NET app counts words with Apache Spark
```

<span data-ttu-id="a892a-197">保存更改并关闭文件。</span><span class="sxs-lookup"><span data-stu-id="a892a-197">Save the changes and close the file.</span></span>

## <a name="run-your-net-for-apache-spark-app"></a><span data-ttu-id="a892a-198">运行 .NET for Apache Spark 应用</span><span class="sxs-lookup"><span data-stu-id="a892a-198">Run your .NET for Apache Spark app</span></span>

<span data-ttu-id="a892a-199">运行以下命令来构建应用程序：</span><span class="sxs-lookup"><span data-stu-id="a892a-199">Run the following command to build your application:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="a892a-200">导航到生成输出目录，并使用 `spark-submit` 命令提交要在 Apache Spark 上运行的应用程序。</span><span class="sxs-lookup"><span data-stu-id="a892a-200">Navigate to your build output directory and use the `spark-submit` command to submit your application to run on Apache Spark.</span></span> <span data-ttu-id="a892a-201">确保将 `<version>` 替换为 .NET 辅助角色的版本，并存储包含 input.txt 文件的路径的 `<path-of-input.txt>`。</span><span class="sxs-lookup"><span data-stu-id="a892a-201">Make sure to replace  `<version>` with the version of your .NET worker and `<path-of-input.txt>` with the path of your *input.txt* file is stored.</span></span>

### <a name="windows"></a>[<span data-ttu-id="a892a-202">Windows</span><span class="sxs-lookup"><span data-stu-id="a892a-202">Windows</span></span>](#tab/windows)

```console
spark-submit ^
--class org.apache.spark.deploy.dotnet.DotnetRunner ^
--master local ^
microsoft-spark-3-0_2.12-<version>.jar ^
dotnet MySparkApp.dll <path-of-input.txt>
```

### <a name="maclinux"></a>[<span data-ttu-id="a892a-203">Mac/Linux</span><span class="sxs-lookup"><span data-stu-id="a892a-203">Mac/Linux</span></span>](#tab/linux)

```bash
spark-submit \
--class org.apache.spark.deploy.dotnet.DotnetRunner \
--master local \
microsoft-spark-3-0_2.12-<version>.jar \
dotnet MySparkApp.dll <path-of-input.txt>
```

---

> [!NOTE]
> <span data-ttu-id="a892a-204">此命令假设已下载 Apache Spark 并添加到 PATH 环境变量，以便能够使用 `spark-submit`。</span><span class="sxs-lookup"><span data-stu-id="a892a-204">This command assumes you have downloaded Apache Spark and added it to your PATH environment variable to be able to use `spark-submit`.</span></span> <span data-ttu-id="a892a-205">如果不是，需要使用完整路径（例如 C:\bin\apache-spark\bin\spark-submit 或 ~/spark/bin/spark-submit）。</span><span class="sxs-lookup"><span data-stu-id="a892a-205">Otherwise, you'd have to use the full path (for example, *C:\bin\apache-spark\bin\spark-submit* or *~/spark/bin/spark-submit*).</span></span>

<span data-ttu-id="a892a-206">在应用运行时，input.txt 的字数统计数据会写入控制台。</span><span class="sxs-lookup"><span data-stu-id="a892a-206">When your app runs, the word count data of the *input.txt* file is written to the console.</span></span>

```console
+------+-----+
|  word|count|
+------+-----+
|  .NET|    3|
|Apache|    2|
|   app|    2|
|  This|    2|
| Spark|    2|
| World|    1|
|counts|    1|
|   for|    1|
| words|    1|
|  with|    1|
| Hello|    1|
|  uses|    1|
+------+-----+
```

<span data-ttu-id="a892a-207">祝贺你！</span><span class="sxs-lookup"><span data-stu-id="a892a-207">Congratulations!</span></span> <span data-ttu-id="a892a-208">你已成功创建并运行 .NET for Apache Spark 应用。</span><span class="sxs-lookup"><span data-stu-id="a892a-208">You successfully authored and ran a .NET for Apache Spark app.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a892a-209">后续步骤</span><span class="sxs-lookup"><span data-stu-id="a892a-209">Next steps</span></span>

<span data-ttu-id="a892a-210">在本教程中，你了解了如何执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="a892a-210">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="a892a-211">为 .NET for Apache Spark 作环境准备</span><span class="sxs-lookup"><span data-stu-id="a892a-211">Prepare your environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="a892a-212">编写你的第一个 .NET for Apache Spark 应用程序</span><span class="sxs-lookup"><span data-stu-id="a892a-212">Write your first .NET for Apache Spark application</span></span>
> * <span data-ttu-id="a892a-213">生成和运行 .NET for Apache Spark 应用程序</span><span class="sxs-lookup"><span data-stu-id="a892a-213">Build and run your .NET for Apache Spark application</span></span>

<span data-ttu-id="a892a-214">若要观看解说上述步骤的视频，请查看 [.NET for Apache Spark 101 视频系列](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App)。</span><span class="sxs-lookup"><span data-stu-id="a892a-214">To see a video explaining the steps above, check out the [.NET for Apache Spark 101 video series](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App).</span></span>

<span data-ttu-id="a892a-215">查看资源页以了解详细信息。</span><span class="sxs-lookup"><span data-stu-id="a892a-215">Check out the resources page to learn more.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="a892a-216">.NET for Apache Spark 资源</span><span class="sxs-lookup"><span data-stu-id="a892a-216">.NET for Apache Spark Resources</span></span>](../resources/index.md)
