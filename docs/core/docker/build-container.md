---
title: 通过 Docker 使应用程序容器化的教程
description: 在本教程中，你将了解如何使用 Docker 容器化 .NET Core 应用。
ms.date: 04/27/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: c92f5823f56f74941afdd28638d30e759b2c51c9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740751"
---
# <a name="tutorial-containerize-a-net-core-app"></a><span data-ttu-id="eb8b7-103">教程：使 .NET Core 应用程序容器化</span><span class="sxs-lookup"><span data-stu-id="eb8b7-103">Tutorial: Containerize a .NET Core app</span></span>

<span data-ttu-id="eb8b7-104">在本教程中，你将了解如何使用 Docker 容器化 .NET Core 应用。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-104">In this tutorial, you'll learn how to containerize a .NET Core application with Docker.</span></span> <span data-ttu-id="eb8b7-105">容器具有很多特性和优点，如具有不可变的基础结构、提供可移植的体系结构和实现可伸缩性。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-105">Containers have many features and benefits, such as being an immutable infrastructure, providing a portable architecture, and enabling scalability.</span></span> <span data-ttu-id="eb8b7-106">此映像可用于为本地开发环境、私有云或公有云创建容器。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-106">The image can be used to create containers for your local development environment, private cloud, or public cloud.</span></span>

<span data-ttu-id="eb8b7-107">在本教程中，你将了解：</span><span class="sxs-lookup"><span data-stu-id="eb8b7-107">In this tutorial, you:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="eb8b7-108">创建并发布简单的 .NET Core 应用</span><span class="sxs-lookup"><span data-stu-id="eb8b7-108">Create and publish a simple .NET Core app</span></span>
> - <span data-ttu-id="eb8b7-109">创建并配置用于 .NET Core 的 Dockerfile</span><span class="sxs-lookup"><span data-stu-id="eb8b7-109">Create and configure a Dockerfile for .NET Core</span></span>
> - <span data-ttu-id="eb8b7-110">生成 Docker 映像</span><span class="sxs-lookup"><span data-stu-id="eb8b7-110">Build a Docker image</span></span>
> - <span data-ttu-id="eb8b7-111">创建并运行 Docker 容器</span><span class="sxs-lookup"><span data-stu-id="eb8b7-111">Create and run a Docker container</span></span>

<span data-ttu-id="eb8b7-112">你将了解用于 .NET Core 应用的 Docker 容器生成和部署任务。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-112">You'll understand the Docker container build and deploy tasks for a .NET Core application.</span></span> <span data-ttu-id="eb8b7-113">Docker 平台  使用 Docker 引擎  快速生成应用，并将应用打包为 Docker 映像  。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-113">The *Docker platform* uses the *Docker engine* to quickly build and package apps as *Docker images*.</span></span> <span data-ttu-id="eb8b7-114">这些映像采用 Dockerfile  格式编写，以供在分层容器中部署和运行。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-114">These images are written in the *Dockerfile* format to be deployed and run in a layered container.</span></span>

> [!NOTE]
> <span data-ttu-id="eb8b7-115">本教程不适用于 ASP.NET Core 应用  。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-115">This tutorial **is not** for ASP.NET Core apps.</span></span> <span data-ttu-id="eb8b7-116">如果使用的是 ASP.NET Core，请参阅教程[了解如何容器化 ASP.NET Core 应用程序](/aspnet/core/host-and-deploy/docker/building-net-docker-images)。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-116">If you're using ASP.NET Core, see the [Learn how to containerize an ASP.NET Core application](/aspnet/core/host-and-deploy/docker/building-net-docker-images) tutorial.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="eb8b7-117">先决条件</span><span class="sxs-lookup"><span data-stu-id="eb8b7-117">Prerequisites</span></span>

<span data-ttu-id="eb8b7-118">安装以下必备组件：</span><span class="sxs-lookup"><span data-stu-id="eb8b7-118">Install the following prerequisites:</span></span>

- <span data-ttu-id="eb8b7-119">[.NET Core 5.0 SDK](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="eb8b7-119">[.NET Core 5.0 SDK](https://dotnet.microsoft.com/download)</span></span>\
<span data-ttu-id="eb8b7-120">如果已安装 .NET Core，请使用 `dotnet --info` 命令来确定使用的是哪个 SDK。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-120">If you have .NET Core installed, use the `dotnet --info` command to determine which SDK you're using.</span></span>
- [<span data-ttu-id="eb8b7-121">Docker 社区版</span><span class="sxs-lookup"><span data-stu-id="eb8b7-121">Docker Community Edition</span></span>](https://www.docker.com/products/docker-desktop)
- <span data-ttu-id="eb8b7-122">Dockerfile 和 .NET Core 示例应用的临时工作文件夹  。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-122">A temporary working folder for the *Dockerfile* and .NET Core example app.</span></span> <span data-ttu-id="eb8b7-123">在本教程中，docker-working  用作工作文件夹的名称。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-123">In this tutorial, the name *docker-working* is used as the working folder.</span></span>

## <a name="create-net-core-app"></a><span data-ttu-id="eb8b7-124">创建 .Net Core 应用</span><span class="sxs-lookup"><span data-stu-id="eb8b7-124">Create .NET Core app</span></span>

<span data-ttu-id="eb8b7-125">需要有可供 Docker 容器运行的 .NET Core 应用。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-125">You need a .NET Core app that the Docker container will run.</span></span> <span data-ttu-id="eb8b7-126">打开终端、创建工作文件夹（如果尚没有），然后进入该文件夹。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-126">Open your terminal, create a working folder if you haven't already, and enter it.</span></span> <span data-ttu-id="eb8b7-127">在工作文件夹中，运行下面的命令，在名为“app”的子目录中新建一个项目  ：</span><span class="sxs-lookup"><span data-stu-id="eb8b7-127">In the working folder, run the following command to create a new project in a subdirectory named *app*:</span></span>

```dotnetcli
dotnet new console -o App -n NetCore.Docker
```

<span data-ttu-id="eb8b7-128">文件夹树将如下所示：</span><span class="sxs-lookup"><span data-stu-id="eb8b7-128">Your folder tree will look like the following:</span></span>

```
docker-working
    └──App
        ├──NetCore.Docker.csproj
        ├──Program.cs
        └──obj
            ├──NetCore.Docker.csproj.nuget.dgspec.json
            ├──NetCore.Docker.csproj.nuget.g.props
            ├──NetCore.Docker.csproj.nuget.g.targets
            ├──project.assets.json
            └──project.nuget.cache
```

<span data-ttu-id="eb8b7-129">`dotnet new` 命令会新建一个名为“应用”的文件夹，并生成一个“Hello World”控制台应用程序  。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-129">The `dotnet new` command creates a new folder named *App* and generates a "Hello World" console application.</span></span> <span data-ttu-id="eb8b7-130">从终端会话更改目录并导航到“App”文件夹  。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-130">Change directories and navigate into the *App* folder, from your terminal session.</span></span> <span data-ttu-id="eb8b7-131">使用 `dotnet run` 命令启动应用。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-131">Use the `dotnet run` command to start the app.</span></span> <span data-ttu-id="eb8b7-132">应用程序将运行，并在命令下方打印 `Hello World!`：</span><span class="sxs-lookup"><span data-stu-id="eb8b7-132">The application will run, and print `Hello World!` below the command:</span></span>

```dotnetcli
dotnet run
Hello World!
```

<span data-ttu-id="eb8b7-133">默认模板创建应用，此应用先打印输出到终端，然后立即终止。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-133">The default template creates an app that prints to the terminal and then immediately terminates.</span></span> <span data-ttu-id="eb8b7-134">本教程将使用无限循环的应用。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-134">For this tutorial, you'll use an app that loops indefinitely.</span></span> <span data-ttu-id="eb8b7-135">在文本编辑器中，打开“Program.cs”  文件。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-135">Open the *Program.cs* file in a text editor.</span></span>

> [!TIP]
> <span data-ttu-id="eb8b7-136">如果使用 Visual Studio Code，则从上一个终端会话中键入以下命令：</span><span class="sxs-lookup"><span data-stu-id="eb8b7-136">If you're using Visual Studio Code, from the previous terminal session type the following command:</span></span>
>
> ```console
> code .
> ```
>
> <span data-ttu-id="eb8b7-137">这会在 Visual Studio Code 中打开包含该项目的“App”文件夹  。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-137">This will open the *App* folder that contains the project in Visual Studio Code.</span></span>

<span data-ttu-id="eb8b7-138">Program.cs 应如下面的 C# 代码所示  ：</span><span class="sxs-lookup"><span data-stu-id="eb8b7-138">The *Program.cs* should look like the following C# code:</span></span>

```csharp
using System;

namespace NetCore.Docker
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

<span data-ttu-id="eb8b7-139">将此文件替换为以下每秒计数一次的代码：</span><span class="sxs-lookup"><span data-stu-id="eb8b7-139">Replace the file with the following code that counts numbers every second:</span></span>

```csharp
using System;
using System.Threading.Tasks;

namespace NetCore.Docker
{
    class Program
    {
        static async Task Main(string[] args)
        {
            var counter = 0;
            var max = args.Length != 0 ? Convert.ToInt32(args[0]) : -1;
            while (max == -1 || counter < max)
            {
                Console.WriteLine($"Counter: {++counter}");
                await Task.Delay(1000);
            }
        }
    }
}
```

<span data-ttu-id="eb8b7-140">保存此文件，并使用 `dotnet run` 再次测试程序。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-140">Save the file and test the program again with `dotnet run`.</span></span> <span data-ttu-id="eb8b7-141">请注意，此应用无限期运行。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-141">Remember that this app runs indefinitely.</span></span> <span data-ttu-id="eb8b7-142">使用取消命令 <kbd>Ctrl+C</kbd> 可以停止运行。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-142">Use the cancel command <kbd>Ctrl+C</kbd> to stop it.</span></span> <span data-ttu-id="eb8b7-143">下面是一个示例输出：</span><span class="sxs-lookup"><span data-stu-id="eb8b7-143">The following is an example output:</span></span>

```dotnetcli
dotnet run
Counter: 1
Counter: 2
Counter: 3
Counter: 4
^C
```

<span data-ttu-id="eb8b7-144">如果你在命令行中向应用传递一个数字，它就只会计数到这个数字，然后退出。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-144">If you pass a number on the command line to the app, it will only count up to that amount and then exit.</span></span> <span data-ttu-id="eb8b7-145">试一试用 `dotnet run -- 5` 计数到 5。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-145">Try it with `dotnet run -- 5` to count to five.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="eb8b7-146">`--` 之后的参数都不传递到 `dotnet run` 命令，而是传递到你的应用程序。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-146">Any parameters after `--` are not passed to the `dotnet run` command and instead are passed to your application.</span></span>

## <a name="publish-net-core-app"></a><span data-ttu-id="eb8b7-147">发布 .Net Core 应用</span><span class="sxs-lookup"><span data-stu-id="eb8b7-147">Publish .NET Core app</span></span>

<span data-ttu-id="eb8b7-148">在将 .NET Core 应用添加到 Docker 映像之前，必须先发布该应用。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-148">Before adding the .NET Core app to the Docker image, first it must be published.</span></span> <span data-ttu-id="eb8b7-149">最好让容器运行应用的已发布版本。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-149">It is best to have the container run the published version of the app.</span></span> <span data-ttu-id="eb8b7-150">若要发布应用，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="eb8b7-150">To publish the app, run the following command:</span></span>

```dotnetcli
dotnet publish -c Release
```

<span data-ttu-id="eb8b7-151">此命令将应用编译到“发布”文件夹中  。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-151">This command compiles your app to the *publish* folder.</span></span> <span data-ttu-id="eb8b7-152">从工作文件夹到“发布”文件夹的路径应为 `.\App\bin\Release\net5.0\publish\`</span><span class="sxs-lookup"><span data-stu-id="eb8b7-152">The path to the *publish* folder from the working folder should be `.\App\bin\Release\net5.0\publish\`</span></span>

#### <a name="windows"></a>[<span data-ttu-id="eb8b7-153">Windows</span><span class="sxs-lookup"><span data-stu-id="eb8b7-153">Windows</span></span>](#tab/windows)

<span data-ttu-id="eb8b7-154">在“应用”文件夹中获取“发布”文件夹的目录列表，以验证 NetCore.Docker.dll 文件是否已创建   。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-154">From the *App* folder, get a directory listing of the publish folder to verify that the *NetCore.Docker.dll* file was created.</span></span>

```powershell
dir .\bin\Release\net5.0\publish\

    Directory: C:\Users\dapine\App\bin\Release\net5.0\publish

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        4/27/2020   8:27 AM            434 NetCore.Docker.deps.json
-a----        4/27/2020   8:27 AM           6144 NetCore.Docker.dll
-a----        4/27/2020   8:27 AM         171520 NetCore.Docker.exe
-a----        4/27/2020   8:27 AM            860 NetCore.Docker.pdb
-a----        4/27/2020   8:27 AM            154 NetCore.Docker.runtimeconfig.json
```

#### <a name="linux"></a>[<span data-ttu-id="eb8b7-155">Linux</span><span class="sxs-lookup"><span data-stu-id="eb8b7-155">Linux</span></span>](#tab/linux)

<span data-ttu-id="eb8b7-156">使用 `ls` 命令获取目录列表，并验证 NetCore.Docker.dll 文件是否已创建  。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-156">Use the `ls` command to get a directory listing and verify that the *NetCore.Docker.dll* file was created.</span></span>

```bash
me@DESKTOP:/docker-working/app$ ls bin/Release/net5.0/publish
NetCore.Docker.deps.json  NetCore.Docker.dll  NetCore.Docker.pdb  NetCore.Docker.runtimeconfig.json
```

---

## <a name="create-the-dockerfile"></a><span data-ttu-id="eb8b7-157">创建 Dockerfile</span><span class="sxs-lookup"><span data-stu-id="eb8b7-157">Create the Dockerfile</span></span>

<span data-ttu-id="eb8b7-158">`docker build` 命令使用 Dockerfile  文件来创建容器映像。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-158">The *Dockerfile* file is used by the `docker build` command to create a container image.</span></span> <span data-ttu-id="eb8b7-159">此文件是名为“Dockerfile”  的文本文件，它没有扩展名。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-159">This file is a text file named *Dockerfile* that doesn't have an extension.</span></span>

<span data-ttu-id="eb8b7-160">在包含 .csproj 的目录中创建名为“Dockerfile”的文件，并在文本编辑器中将其打开   。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-160">Create a file named *Dockerfile* in directory containing the *.csproj* and open it in a text editor.</span></span> <span data-ttu-id="eb8b7-161">本教程将使用 ASP.NET Core 运行时映像（包含 .NET Core 运行时映像），并与 .NET Core 控制台应用程序相对应。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-161">This tutorial will use the ASP.NET Core runtime image (which contains the .NET Core runtime image) and corresponds with the .NET Core console application.</span></span>

```dockerfile
FROM mcr.microsoft.com/dotnet/aspnet:5.0
```

> [!NOTE]
> <span data-ttu-id="eb8b7-162">尽管可能已使用 `mcr.microsoft.com/dotnet/runtime:5.0` 映像，但此处有意使用 ASP.NET Core 运行时映像。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-162">The ASP.NET Core runtime image is used intentionally here, although the `mcr.microsoft.com/dotnet/runtime:5.0` image could have been used.</span></span>

<span data-ttu-id="eb8b7-163">`FROM` 关键字需要完全限定的 Docker 容器映像名称。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-163">The `FROM` keyword requires a fully qualified Docker container image name.</span></span> <span data-ttu-id="eb8b7-164">Microsoft 容器注册表（MCR，mcr.microsoft.com）是 Docker Hub 的联合，可托管可公开访问的容器。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-164">The Microsoft Container Registry (MCR, mcr.microsoft.com) is a syndicate of Docker Hub - which hosts publicly accessible containers.</span></span> <span data-ttu-id="eb8b7-165">`dotnet/core` 段是容器存储库，其中 `aspnet` 段是容器映像名称。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-165">The `dotnet/core` segment is the container repository, where as the `aspnet` segment is the container image name.</span></span> <span data-ttu-id="eb8b7-166">该映像使用 `5.0` 进行标记，它用于版本控制。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-166">The image is tagged with `5.0`, which is used for versioning.</span></span> <span data-ttu-id="eb8b7-167">因此，`mcr.microsoft.com/dotnet/aspnet:5.0` 是 .NET Core 5.0 运行时。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-167">Thus, `mcr.microsoft.com/dotnet/aspnet:5.0` is the .NET Core 5.0 runtime.</span></span> <span data-ttu-id="eb8b7-168">请确保拉取的运行时版本与 SDK 面向的运行时一致。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-168">Make sure that you pull the runtime version that matches the runtime targeted by your SDK.</span></span> <span data-ttu-id="eb8b7-169">例如，在上一节中创建的应用使用了 .NET Core 5.0 SDK，在 Dockerfile 中引用的基础映像被标记为 5.0。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-169">For example, the app created in the previous section used the .NET Core 5.0 SDK and the base image referred to in the *Dockerfile* is tagged with **5.0**.</span></span>

<span data-ttu-id="eb8b7-170">保存 Dockerfile 文件  。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-170">Save the *Dockerfile* file.</span></span> <span data-ttu-id="eb8b7-171">工作文件夹的目录结果应如下所示。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-171">The directory structure of the working folder should look like the following.</span></span> <span data-ttu-id="eb8b7-172">为节省本文的空间，省略了一些更深级别的文件和文件夹：</span><span class="sxs-lookup"><span data-stu-id="eb8b7-172">Some of the deeper-level files and folders have been omitted to save space in the article:</span></span>

```
docker-working
    └──App
        ├──Dockerfile
        ├──NetCore.Docker.csproj
        ├──Program.cs
        ├──bin
        │   └──Release
        │       └──net5.0
        │           └──publish
        │               ├──NetCore.Docker.deps.json
        │               ├──NetCore.Docker.exe
        │               ├──NetCore.Docker.dll
        │               ├──NetCore.Docker.pdb
        │               └──NetCore.Docker.runtimeconfig.json
        └──obj
            └──...
```

<span data-ttu-id="eb8b7-173">在终端中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="eb8b7-173">From your terminal, run the following command:</span></span>

```console
docker build -t counter-image -f Dockerfile .
```

<span data-ttu-id="eb8b7-174">Docker 会处理 Dockerfile  中的每一行。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-174">Docker will process each line in the *Dockerfile*.</span></span> <span data-ttu-id="eb8b7-175">`docker build` 命令中的 `.` 指示 Docker 在当前文件夹中查找 Dockerfile  。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-175">The `.` in the `docker build` command tells Docker to use the current folder to find a *Dockerfile*.</span></span> <span data-ttu-id="eb8b7-176">此命令生成映像，并创建指向相应映像的本地存储库“counter-image”  。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-176">This command builds the image and creates a local repository named **counter-image** that points to that image.</span></span> <span data-ttu-id="eb8b7-177">在此命令完成后，运行 `docker images` 以列出已安装的映像：</span><span class="sxs-lookup"><span data-stu-id="eb8b7-177">After this command finishes, run `docker images` to see a list of images installed:</span></span>

```console
docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
counter-image                           latest              e6780479db63        4 days ago          190MB
mcr.microsoft.com/dotnet/aspnet         5.0                 e6780479db63        4 days ago          190MB
```

<span data-ttu-id="eb8b7-178">请注意，两个映像共用相同的“IMAGE ID”  值。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-178">Notice that the two images share the same **IMAGE ID** value.</span></span> <span data-ttu-id="eb8b7-179">两个映像使用的 ID 值相同是因为，Dockerfile  中的唯一命令是在现有映像的基础之上生成新映像。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-179">The value is the same between both images because the only command in the *Dockerfile* was to base the new image on an existing image.</span></span> <span data-ttu-id="eb8b7-180">接下来，在 Dockerfile 中添加三个命令  。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-180">Let's add three commands to the *Dockerfile*.</span></span> <span data-ttu-id="eb8b7-181">两个命令都新建映像层，最后一个命令表示 counter-image 存储库条目指向的映像  。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-181">Each command creates a new image layer with the final command representing the **counter-image** repository entry points to.</span></span>

```dockerfile
COPY bin/Release/net5.0/publish/ App/
WORKDIR /App
ENTRYPOINT ["dotnet", "NetCore.Docker.dll"]
```

<span data-ttu-id="eb8b7-182">`COPY` 命令指示 Docker 将计算机上的指定文件夹复制到容器中的文件夹。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-182">The `COPY` command tells Docker to copy the specified folder on your computer to a folder in the container.</span></span> <span data-ttu-id="eb8b7-183">在此示例中，“publish”文件夹被复制到容器中的“App”文件夹   。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-183">In this example, the *publish* folder is copied to a folder named *App* in the container.</span></span>

<span data-ttu-id="eb8b7-184">`WORKDIR` 命令将容器内的当前目录更改为“App”   。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-184">The `WORKDIR` command changes the **current directory** inside of the container to *App*.</span></span>

<span data-ttu-id="eb8b7-185">下一个命令 `ENTRYPOINT` 指示 Docker 将容器配置为可执行文件运行。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-185">The next command, `ENTRYPOINT`, tells Docker to configure the container to run as an executable.</span></span> <span data-ttu-id="eb8b7-186">在容器启动时，`ENTRYPOINT` 命令运行。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-186">When the container starts, the `ENTRYPOINT` command runs.</span></span> <span data-ttu-id="eb8b7-187">当此命令结束时，容器也会自动停止。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-187">When this command ends, the container will automatically stop.</span></span>

<span data-ttu-id="eb8b7-188">在终端中，运行 `docker build -t counter-image -f Dockerfile .`；在此命令完成后，运行 `docker images`。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-188">From your terminal, run `docker build -t counter-image -f Dockerfile .` and when that command finishes, run `docker images`.</span></span>

```console
docker build -t counter-image -f Dockerfile .
Sending build context to Docker daemon  1.117MB
Step 1/4 : FROM mcr.microsoft.com/dotnet/aspnet:5.0
 ---> e6780479db63
Step 2/4 : COPY bin/Release/net5.0/publish/ App/
 ---> d1732740eed2
Step 3/4 : WORKDIR /App
 ---> Running in b1701a42f3ff
Removing intermediate container b1701a42f3ff
 ---> 919aab5b95e3
Step 4/4 : ENTRYPOINT ["dotnet", "NetCore.Docker.dll"]
 ---> Running in c12aebd26ced
Removing intermediate container c12aebd26ced
 ---> cd11c3df9b19
Successfully built cd11c3df9b19
Successfully tagged counter-image:latest

docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
counter-image                           latest              cd11c3df9b19        41 seconds ago      190MB
mcr.microsoft.com/dotnet/aspnet         5.0                 e6780479db63        4 days ago          190MB
```

<span data-ttu-id="eb8b7-189">Dockerfile  中的每个命令生成了一个层，并创建了“IMAGE ID”  。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-189">Each command in the *Dockerfile* generated a layer and created an **IMAGE ID**.</span></span> <span data-ttu-id="eb8b7-190">最终“IMAGE ID”是“cd11c3df9b19”（你的 ID 会有所不同），接下来在此映像的基础之上创建容器   。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-190">The final **IMAGE ID** (yours will be different) is **cd11c3df9b19** and next you'll create a container based on this image.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="eb8b7-191">创建容器</span><span class="sxs-lookup"><span data-stu-id="eb8b7-191">Create a container</span></span>

<span data-ttu-id="eb8b7-192">至此，已有包含应用的映像，可以创建容器了。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-192">Now that you have an image that contains your app, you can create a container.</span></span> <span data-ttu-id="eb8b7-193">可以通过两种方式来创建容器。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-193">You can create a container in two ways.</span></span> <span data-ttu-id="eb8b7-194">首先，新建已停止的容器。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-194">First, create a new container that is stopped.</span></span>

```console
docker create --name core-counter counter-image
0f281cb3af994fba5d962cc7d482828484ea14ead6bfe386a35e5088c0058851
```

<span data-ttu-id="eb8b7-195">上面的 `docker create` 命令在 counter-image 映像的基础之上创建容器  。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-195">The `docker create` command from above will create a container based on the **counter-image** image.</span></span> <span data-ttu-id="eb8b7-196">此命令的输出显示已创建容器的“CONTAINER ID”  （你的 ID 会有所不同）。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-196">The output of that command shows you the **CONTAINER ID** (yours will be different) of the created container.</span></span> <span data-ttu-id="eb8b7-197">若要查看所有  容器的列表，请使用 `docker ps -a` 命令：</span><span class="sxs-lookup"><span data-stu-id="eb8b7-197">To see a list of *all* containers, use the `docker ps -a` command:</span></span>

```console
docker ps -a
CONTAINER ID    IMAGE            COMMAND                   CREATED           STATUS     PORTS    NAMES
0f281cb3af99    counter-image    "dotnet NetCore.Dock…"    40 seconds ago    Created             core-counter
```

### <a name="manage-the-container"></a><span data-ttu-id="eb8b7-198">管理容器</span><span class="sxs-lookup"><span data-stu-id="eb8b7-198">Manage the container</span></span>

<span data-ttu-id="eb8b7-199">容器是使用特定名称 `core-counter` 创建的，此名称用于管理容器。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-199">The container was created with a specific name `core-counter`, this name is used to manage the container.</span></span> <span data-ttu-id="eb8b7-200">下面的示例使用 `docker start` 命令来启动容器，然后使用 `docker ps` 命令仅显示正在运行的容器：</span><span class="sxs-lookup"><span data-stu-id="eb8b7-200">The following example uses the `docker start` command to start the container, and then uses the `docker ps` command to only show containers that are running:</span></span>

```console
docker start core-counter
core-counter

docker ps
CONTAINER ID    IMAGE            COMMAND                   CREATED          STATUS          PORTS    NAMES
2f6424a7ddce    counter-image    "dotnet NetCore.Dock…"    2 minutes ago    Up 11 seconds            core-counter
```

<span data-ttu-id="eb8b7-201">同样，`docker stop` 命令会停止容器。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-201">Similarly, the `docker stop` command will stop the container.</span></span> <span data-ttu-id="eb8b7-202">下面的示例使用 `docker stop` 命令来停止容器，然后使用 `docker ps` 命令来显示未在运行的容器：</span><span class="sxs-lookup"><span data-stu-id="eb8b7-202">The following example uses the `docker stop` command to stop the container, and then uses the `docker ps` command to show that no containers are running:</span></span>

```console
docker stop core-counter
core-counter

docker ps
CONTAINER ID    IMAGE    COMMAND    CREATED    STATUS    PORTS    NAMES
```

### <a name="connect-to-a-container"></a><span data-ttu-id="eb8b7-203">连接到容器</span><span class="sxs-lookup"><span data-stu-id="eb8b7-203">Connect to a container</span></span>

<span data-ttu-id="eb8b7-204">在容器运行后，可以连接到它来查看输出。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-204">After a container is running, you can connect to it to see the output.</span></span> <span data-ttu-id="eb8b7-205">使用 `docker start` 和 `docker attach` 命令，启动容器并查看输出流。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-205">Use the `docker start` and `docker attach` commands to start the container and peek at the output stream.</span></span> <span data-ttu-id="eb8b7-206">在此示例中，<kbd>Ctrl+C</kbd> 击键用于从正在运行的容器中分离出来。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-206">In this example, the <kbd>Ctrl+C</kbd> keystroke is used to detach from the running container.</span></span> <span data-ttu-id="eb8b7-207">除非另行指定，否则此击键将结束容器中的进程，这会停止容器。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-207">This keystroke will end the process in the container unless otherwise specified, which would stop the container.</span></span> <span data-ttu-id="eb8b7-208">`--sig-proxy=false` 参数可确保 <kbd>Ctrl+C</kbd> 不会停止容器中的进程。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-208">The `--sig-proxy=false` parameter ensures that <kbd>Ctrl+C</kbd> will not stop the process in the container.</span></span>

<span data-ttu-id="eb8b7-209">从容器中分离出来后重新连接，以验证它是否仍在运行和计数。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-209">After you detach from the container, reattach to verify that it's still running and counting.</span></span>

```console
docker start core-counter
core-counter

docker attach --sig-proxy=false core-counter
Counter: 7
Counter: 8
Counter: 9
^C

docker attach --sig-proxy=false core-counter
Counter: 17
Counter: 18
Counter: 19
^C
```

### <a name="delete-a-container"></a><span data-ttu-id="eb8b7-210">删除容器</span><span class="sxs-lookup"><span data-stu-id="eb8b7-210">Delete a container</span></span>

<span data-ttu-id="eb8b7-211">就本文而言，你不希望存在不执行任何操作的容器。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-211">For the purposes of this article you don't want containers just hanging around doing nothing.</span></span> <span data-ttu-id="eb8b7-212">删除前面创建的容器。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-212">Delete the container you previously created.</span></span> <span data-ttu-id="eb8b7-213">如果容器正在运行，停止容器。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-213">If the container is running, stop it.</span></span>

```console
docker stop core-counter
```

<span data-ttu-id="eb8b7-214">下面的示例列出了所有容器。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-214">The following example lists all containers.</span></span> <span data-ttu-id="eb8b7-215">然后，它使用 `docker rm` 命令来删除容器，并再次检查是否有任何正在运行的容器。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-215">It then uses the `docker rm` command to delete the container, and then checks a second time for any running containers.</span></span>

```console
docker ps -a
CONTAINER ID    IMAGE            COMMAND                   CREATED          STATUS                        PORTS    NAMES
2f6424a7ddce    counter-image    "dotnet NetCore.Dock…"    7 minutes ago    Exited (143) 20 seconds ago            core-counter

docker rm core-counter
core-counter

docker ps -a
CONTAINER ID    IMAGE    COMMAND    CREATED    STATUS    PORTS    NAMES
```

### <a name="single-run"></a><span data-ttu-id="eb8b7-216">单次运行</span><span class="sxs-lookup"><span data-stu-id="eb8b7-216">Single run</span></span>

<span data-ttu-id="eb8b7-217">Docker 提供了 `docker run` 命令，用于将容器作为单一命令进行创建和运行。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-217">Docker provides the `docker run` command to create and run the container as a single command.</span></span> <span data-ttu-id="eb8b7-218">使用此命令，无需依次运行 `docker create` 和 `docker start`。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-218">This command eliminates the need to run `docker create` and then `docker start`.</span></span> <span data-ttu-id="eb8b7-219">另外，还可以将此命令设置为，在容器停止时自动删除容器。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-219">You can also set this command to automatically delete the container when the container stops.</span></span> <span data-ttu-id="eb8b7-220">例如，使用 `docker run -it --rm` 可以执行两项操作，先自动使用当前终端连接到容器，再在容器完成时删除容器：</span><span class="sxs-lookup"><span data-stu-id="eb8b7-220">For example, use `docker run -it --rm` to do two things, first, automatically use the current terminal to connect to the container, and then when the container finishes, remove it:</span></span>

```console
docker run -it --rm counter-image
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
^C
```

<span data-ttu-id="eb8b7-221">容器还会将参数传递给 .NET Core 应用的执行。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-221">The container also passes parameters into the execution of the .NET Core app.</span></span> <span data-ttu-id="eb8b7-222">指示 .NET Core 应用仅计数为 3 个传入 3 个。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-222">To instruct the .NET Core app to count only to 3 pass in 3.</span></span>

```console
docker run -it --rm counter-image 3
Counter: 1
Counter: 2
Counter: 3
```

<span data-ttu-id="eb8b7-223">使用 `docker run -it`，<kbd>Ctrl+C</kbd> 命令会停止在容器中运行的进程，进而停止容器。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-223">With `docker run -it`, the <kbd>Ctrl+C</kbd> command will stop process that is running in the container, which in turn, stops the container.</span></span> <span data-ttu-id="eb8b7-224">由于提供了 `--rm` 参数，因此在进程停止时自动删除容器。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-224">Since the `--rm` parameter was provided, the container is automatically deleted when the process is stopped.</span></span> <span data-ttu-id="eb8b7-225">验证它是否不存在：</span><span class="sxs-lookup"><span data-stu-id="eb8b7-225">Verify that it doesn't exist:</span></span>

```console
docker ps -a
CONTAINER ID    IMAGE    COMMAND    CREATED    STATUS    PORTS    NAMES
```

### <a name="change-the-entrypoint"></a><span data-ttu-id="eb8b7-226">更改 ENTRYPOINT</span><span class="sxs-lookup"><span data-stu-id="eb8b7-226">Change the ENTRYPOINT</span></span>

<span data-ttu-id="eb8b7-227">使用 `docker run` 命令，还可以修改 Dockerfile  中的 `ENTRYPOINT` 命令，并运行其他内容，但只能针对相应容器。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-227">The `docker run` command also lets you modify the `ENTRYPOINT` command from the *Dockerfile* and run something else, but only for that container.</span></span> <span data-ttu-id="eb8b7-228">例如，使用以下命令来运行 `bash` 或 `cmd.exe`。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-228">For example, use the following command to run `bash` or `cmd.exe`.</span></span> <span data-ttu-id="eb8b7-229">根据需要，编辑此命令。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-229">Edit the command as necessary.</span></span>

#### <a name="windows"></a>[<span data-ttu-id="eb8b7-230">Windows</span><span class="sxs-lookup"><span data-stu-id="eb8b7-230">Windows</span></span>](#tab/windows)

<span data-ttu-id="eb8b7-231">在本例中，`ENTRYPOINT` 更改为 `cmd.exe`。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-231">In this example, `ENTRYPOINT` is changed to `cmd.exe`.</span></span> <span data-ttu-id="eb8b7-232">通过按下 <kbd>Ctrl+C</kbd> 来结束进程并停止容器。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-232"><kbd>Ctrl+C</kbd> is pressed to end the process and stop the container.</span></span>

```console
docker run -it --rm --entrypoint "cmd.exe" counter-image

Microsoft Windows [Version 10.0.17763.379]
(c) 2018 Microsoft Corporation. All rights reserved.

C:\>dir
 Volume in drive C has no label.
 Volume Serial Number is 3005-1E84

 Directory of C:\

04/09/2019  08:46 AM    <DIR>          app
03/07/2019  10:25 AM             5,510 License.txt
04/02/2019  01:35 PM    <DIR>          Program Files
04/09/2019  01:06 PM    <DIR>          Users
04/02/2019  01:35 PM    <DIR>          Windows
               1 File(s)          5,510 bytes
               4 Dir(s)  21,246,517,248 bytes free

C:\>^C
```

#### <a name="linux"></a>[<span data-ttu-id="eb8b7-233">Linux</span><span class="sxs-lookup"><span data-stu-id="eb8b7-233">Linux</span></span>](#tab/linux)

<span data-ttu-id="eb8b7-234">在本例中，`ENTRYPOINT` 更改为 `bash`。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-234">In this example, `ENTRYPOINT` is changed to `bash`.</span></span> <span data-ttu-id="eb8b7-235">通过运行 `exit` 命令来结束进程并停止容器。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-235">The `exit` command is run which ends the process and stop the container.</span></span>

```bash
docker run -it --rm --entrypoint "bash" counter-image
root@b735b9799abf:/App# ls
NetCore.Docker.deps.json  NetCore.Docker.dll  NetCore.Docker.exe  NetCore.Docker.pdb  NetCore.Docker.runtimeconfig.json
root@b735b9799abf:/App# dotnet NetCore.Docker.dll 3
Counter: 1
Counter: 2
Counter: 3
root@b735b9799abf:/App# exit
exit
```

---

## <a name="essential-commands"></a><span data-ttu-id="eb8b7-236">重要命令</span><span class="sxs-lookup"><span data-stu-id="eb8b7-236">Essential commands</span></span>

<span data-ttu-id="eb8b7-237">Docker 包含许多不同的命令，可用于创建、管理以及与容器和映像进行交互。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-237">Docker has many different commands that create, manage, and interact with containers and images.</span></span> <span data-ttu-id="eb8b7-238">下面这些 Docker 命令对于管理容器来说至关重要：</span><span class="sxs-lookup"><span data-stu-id="eb8b7-238">These Docker commands are essential to managing your containers:</span></span>

- [<span data-ttu-id="eb8b7-239">docker build</span><span class="sxs-lookup"><span data-stu-id="eb8b7-239">docker build</span></span>](https://docs.docker.com/engine/reference/commandline/build/)
- [<span data-ttu-id="eb8b7-240">docker run</span><span class="sxs-lookup"><span data-stu-id="eb8b7-240">docker run</span></span>](https://docs.docker.com/engine/reference/commandline/run/)
- [<span data-ttu-id="eb8b7-241">docker ps</span><span class="sxs-lookup"><span data-stu-id="eb8b7-241">docker ps</span></span>](https://docs.docker.com/engine/reference/commandline/ps/)
- [<span data-ttu-id="eb8b7-242">docker stop</span><span class="sxs-lookup"><span data-stu-id="eb8b7-242">docker stop</span></span>](https://docs.docker.com/engine/reference/commandline/stop/)
- [<span data-ttu-id="eb8b7-243">docker rm</span><span class="sxs-lookup"><span data-stu-id="eb8b7-243">docker rm</span></span>](https://docs.docker.com/engine/reference/commandline/rm/)
- [<span data-ttu-id="eb8b7-244">docker rmi</span><span class="sxs-lookup"><span data-stu-id="eb8b7-244">docker rmi</span></span>](https://docs.docker.com/engine/reference/commandline/rmi/)
- [<span data-ttu-id="eb8b7-245">docker image</span><span class="sxs-lookup"><span data-stu-id="eb8b7-245">docker image</span></span>](https://docs.docker.com/engine/reference/commandline/image/)

## <a name="clean-up-resources"></a><span data-ttu-id="eb8b7-246">清理资源</span><span class="sxs-lookup"><span data-stu-id="eb8b7-246">Clean up resources</span></span>

<span data-ttu-id="eb8b7-247">在本教程中，你创建了容器和映像。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-247">During this tutorial, you created containers and images.</span></span> <span data-ttu-id="eb8b7-248">如果需要，请删除这些资源。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-248">If you want, delete these resources.</span></span> <span data-ttu-id="eb8b7-249">以下命令可用于</span><span class="sxs-lookup"><span data-stu-id="eb8b7-249">Use the following commands to</span></span>

01. <span data-ttu-id="eb8b7-250">列出所有容器</span><span class="sxs-lookup"><span data-stu-id="eb8b7-250">List all containers</span></span>

    ```console
    docker ps -a
    ```

02. <span data-ttu-id="eb8b7-251">按名称停止正在运行的容器。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-251">Stop containers that are running by their name.</span></span>

    ```console
    docker stop counter-image
    ```

03. <span data-ttu-id="eb8b7-252">删除容器</span><span class="sxs-lookup"><span data-stu-id="eb8b7-252">Delete the container</span></span>

    ```console
    docker rm counter-image
    ```

<span data-ttu-id="eb8b7-253">接下来，删除计算机上不再需要的任何映像。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-253">Next, delete any images that you no longer want on your machine.</span></span> <span data-ttu-id="eb8b7-254">依次删除 Dockerfile  创建的映像，以及 Dockerfile  所依据的 .NET Core 映像。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-254">Delete the image created by your *Dockerfile* and then delete the .NET Core image the *Dockerfile* was based on.</span></span> <span data-ttu-id="eb8b7-255">可以使用 IMAGE ID  或 REPOSITORY:TAG  格式字符串。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-255">You can use the **IMAGE ID** or the **REPOSITORY:TAG** formatted string.</span></span>

```console
docker rmi counter-image:latest
docker rmi mcr.microsoft.com/dotnet/aspnet:5.0
```

<span data-ttu-id="eb8b7-256">使用 `docker images` 命令来列出已安装的映像。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-256">Use the `docker images` command to see a list of images installed.</span></span>

> [!TIP]
> <span data-ttu-id="eb8b7-257">映像文件可能很大。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-257">Image files can be large.</span></span> <span data-ttu-id="eb8b7-258">通常情况下，需要删除在测试和开发应用期间创建的临时容器。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-258">Typically, you would remove temporary containers you created while testing and developing your app.</span></span> <span data-ttu-id="eb8b7-259">如果计划在相应运行时的基础之上生成其他映像，通常会将基础映像与运行时一同安装。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-259">You usually keep the base images with the runtime installed if you plan on building other images based on that runtime.</span></span>

## <a name="next-steps"></a><span data-ttu-id="eb8b7-260">后续步骤</span><span class="sxs-lookup"><span data-stu-id="eb8b7-260">Next steps</span></span>

- [<span data-ttu-id="eb8b7-261">了解如何容器化 ASP.NET Core 应用程序。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-261">Learn how to containerize an ASP.NET Core application.</span></span>](/aspnet/core/host-and-deploy/docker/building-net-docker-images)
- [<span data-ttu-id="eb8b7-262">试学“ASP.NET Core 微服务”教程。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-262">Try the ASP.NET Core Microservice Tutorial.</span></span>](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
- [<span data-ttu-id="eb8b7-263">查看支持容器的 Azure 服务。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-263">Review the Azure services that support containers.</span></span>](https://azure.microsoft.com/overview/containers/)
- [<span data-ttu-id="eb8b7-264">了解 Dockerfile 命令。</span><span class="sxs-lookup"><span data-stu-id="eb8b7-264">Read about Dockerfile commands.</span></span>](https://docs.docker.com/engine/reference/builder/)
- [<span data-ttu-id="eb8b7-265">了解用于 Visual Studio 的容器工具</span><span class="sxs-lookup"><span data-stu-id="eb8b7-265">Explore the Container Tools for Visual Studio</span></span>](/visualstudio/containers/overview)
