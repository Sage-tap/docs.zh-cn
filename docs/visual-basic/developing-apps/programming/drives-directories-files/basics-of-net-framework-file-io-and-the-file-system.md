---
description: 详细了解：.NET Framework 文件 I/O 和文件系统基础知识 (Visual Basic)
title: .NET Framework 文件 I/O 和文件系统基础知识
ms.date: 07/20/2015
helpviewer_keywords:
- file access, file I/O in Visual Basic
- file attributes, determining
- streams, fundamental operations
- file permissions
- streams
- streams, definition
ms.assetid: 49d837c0-cf28-416f-8606-4d83d7b479ef
ms.openlocfilehash: 78ab7f572f0e2cc6255af470f73a549a4d7f274a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666350"
---
# <a name="basics-of-net-framework-file-io-and-the-file-system-visual-basic"></a><span data-ttu-id="5b209-103">.NET Framework 文件 I/O 和文件系统基础知识 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5b209-103">Basics of .NET Framework File I/O and the File System (Visual Basic)</span></span>

<span data-ttu-id="5b209-104">使用 <xref:System.IO> 命名空间中的类与驱动器、文件和目录一起工作。</span><span class="sxs-lookup"><span data-stu-id="5b209-104">Classes in the <xref:System.IO> namespace are used to work with drives, files, and directories.</span></span>

<span data-ttu-id="5b209-105"><xref:System.IO> 命名空间包含 <xref:System.IO.File> 和 <xref:System.IO.Directory> 类，它们提供用于操作文件和目录的 .NET Framework 功能。</span><span class="sxs-lookup"><span data-stu-id="5b209-105">The <xref:System.IO> namespace contains the <xref:System.IO.File> and <xref:System.IO.Directory> classes, which provide the .NET Framework functionality that manipulates files and directories.</span></span> <span data-ttu-id="5b209-106">由于这些对象的方法是静态或共享成员，因此可直接使用，无需首先创建类的实例。</span><span class="sxs-lookup"><span data-stu-id="5b209-106">Because the methods of these objects are static or shared members, you can use them directly without creating an instance of the class first.</span></span> <span data-ttu-id="5b209-107">与这些类相关联的是 <xref:System.IO.FileInfo> 和 <xref:System.IO.DirectoryInfo> 类，使用 `My` 功能的用户将对它们很熟悉。</span><span class="sxs-lookup"><span data-stu-id="5b209-107">Associated with these classes are the <xref:System.IO.FileInfo> and <xref:System.IO.DirectoryInfo> classes, which will be familiar to users of the `My` feature.</span></span> <span data-ttu-id="5b209-108">若要使用这些类，必须通过在受影响的代码开头包含 `Imports` 语句，完全限定名称或导入相应的命名空间。</span><span class="sxs-lookup"><span data-stu-id="5b209-108">To use these classes, you must fully qualify the names or import the appropriate namespaces by including the `Imports` statement(s) at the beginning of the affected code.</span></span> <span data-ttu-id="5b209-109">有关详细信息，请参阅 [Imports 语句（.NET 命名空间和类型）](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)。</span><span class="sxs-lookup"><span data-stu-id="5b209-109">For more information, see [Imports Statement (.NET Namespace and Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>

> [!NOTE]
> <span data-ttu-id="5b209-110">此部分中的其他主题使用 `My.Computer.FileSystem` 对象，而不使用 `System.IO` 类与驱动器、文件和目录一起工作。</span><span class="sxs-lookup"><span data-stu-id="5b209-110">Other topics in this section use the `My.Computer.FileSystem` object instead of `System.IO` classes to work with drives, files, and directories.</span></span> <span data-ttu-id="5b209-111">`My.Computer.FileSystem` 对象的主要目的是用在 Visual Basic 程序中。</span><span class="sxs-lookup"><span data-stu-id="5b209-111">The `My.Computer.FileSystem` object is intended primarily for use in Visual Basic programs.</span></span> <span data-ttu-id="5b209-112">`System.IO` 类旨在供任何支持 .NET Framework（包括 Visual Basic）的语言使用。</span><span class="sxs-lookup"><span data-stu-id="5b209-112">`System.IO` classes are intended for use by any language that supports the .NET Framework, including Visual Basic.</span></span>

## <a name="definition-of-a-stream"></a><span data-ttu-id="5b209-113">流的定义</span><span class="sxs-lookup"><span data-stu-id="5b209-113">Definition of a Stream</span></span>

<span data-ttu-id="5b209-114">.NET Framework 使用流来支持从文件中读取和写入文件。</span><span class="sxs-lookup"><span data-stu-id="5b209-114">The .NET Framework uses streams to support reading from and writing to files.</span></span> <span data-ttu-id="5b209-115">可以将流视为一维连续数据集，具有开始和结束，并且其中的游标指示流中的当前位置。</span><span class="sxs-lookup"><span data-stu-id="5b209-115">You can think of a stream as a one-dimensional set of contiguous data, which has a beginning and an end, and where the cursor indicates the current position in the stream.</span></span>

![光标显示了 Filestream 中的当前位置。](./media/basics-of-net-framework-file-io-and-the-file-system/filestream-cursor-position.gif)

## <a name="stream-operations"></a><span data-ttu-id="5b209-117">流操作</span><span class="sxs-lookup"><span data-stu-id="5b209-117">Stream Operations</span></span>

<span data-ttu-id="5b209-118">流中包含的数据可能来自内存、文件或 TCP/IP 套接字。</span><span class="sxs-lookup"><span data-stu-id="5b209-118">The data contained in the stream may come from memory, a file, or a TCP/IP socket.</span></span> <span data-ttu-id="5b209-119">流具有可应用于它们的基本操作：</span><span class="sxs-lookup"><span data-stu-id="5b209-119">Streams have fundamental operations that can be applied to them:</span></span>

- <span data-ttu-id="5b209-120">**读取**。</span><span class="sxs-lookup"><span data-stu-id="5b209-120">**Reading**.</span></span> <span data-ttu-id="5b209-121">可以从流读取数据，将数据从流传输到数据结构，如字符串或字节数组。</span><span class="sxs-lookup"><span data-stu-id="5b209-121">You can read from a stream, transferring data from the stream into a data structure, such as a string or an array of bytes.</span></span>

- <span data-ttu-id="5b209-122">**编写**。</span><span class="sxs-lookup"><span data-stu-id="5b209-122">**Writing**.</span></span> <span data-ttu-id="5b209-123">可以将数据写入流中，将数据从数据源传输到流。</span><span class="sxs-lookup"><span data-stu-id="5b209-123">You can write to a stream, transferring data from a data source into the stream.</span></span>

- <span data-ttu-id="5b209-124">**查找**。</span><span class="sxs-lookup"><span data-stu-id="5b209-124">**Seeking**.</span></span> <span data-ttu-id="5b209-125">可以查询和修改流中的位置。</span><span class="sxs-lookup"><span data-stu-id="5b209-125">You can query and modify your position in the stream.</span></span>

<span data-ttu-id="5b209-126">有关详细信息，请参阅 “[撰写流](../../../../standard/io/composing-streams.md)”。</span><span class="sxs-lookup"><span data-stu-id="5b209-126">For more information, see [Composing Streams](../../../../standard/io/composing-streams.md).</span></span>

## <a name="types-of-streams"></a><span data-ttu-id="5b209-127">流的类型</span><span class="sxs-lookup"><span data-stu-id="5b209-127">Types of Streams</span></span>

<span data-ttu-id="5b209-128">在 .NET Framework 中，流由 <xref:System.IO.Stream> 类表示，这形成了所有其他流的抽象类。</span><span class="sxs-lookup"><span data-stu-id="5b209-128">In the .NET Framework, a stream is represented by the <xref:System.IO.Stream> class, which forms the abstract class for all other streams.</span></span> <span data-ttu-id="5b209-129">不能直接创建 <xref:System.IO.Stream> 类的实例，但必须使用它执行的一个类。</span><span class="sxs-lookup"><span data-stu-id="5b209-129">You cannot directly create an instance of the <xref:System.IO.Stream> class, but must use one of the classes it implements.</span></span>

<span data-ttu-id="5b209-130">存在许多类型的流，但就处理文件输入/输出 (I/O) 而言，最重要的类型是 <xref:System.IO.FileStream> 类（提供从文件读取和写入文件的方式）和 <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> 类（提供在独立存储中创建文件和目录的方法）。</span><span class="sxs-lookup"><span data-stu-id="5b209-130">There are many types of streams, but for the purposes of working with file input/output (I/O), the most important types are the <xref:System.IO.FileStream> class, which provides a way to read from and write to files, and the <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> class, which provides a way to create files and directories in isolated storage.</span></span> <span data-ttu-id="5b209-131">处理文件 I/O 时可使用的其他流包括：</span><span class="sxs-lookup"><span data-stu-id="5b209-131">Other streams that can be used when working with file I/O include:</span></span>

- <xref:System.IO.BufferedStream>

- <xref:System.Security.Cryptography.CryptoStream>

- <xref:System.IO.MemoryStream>

- <span data-ttu-id="5b209-132"><xref:System.Net.Sockets.NetworkStream>.</span><span class="sxs-lookup"><span data-stu-id="5b209-132"><xref:System.Net.Sockets.NetworkStream>.</span></span>

<span data-ttu-id="5b209-133">下表列出了通常使用流完成的任务：</span><span class="sxs-lookup"><span data-stu-id="5b209-133">The following table lists tasks commonly accomplished with a stream:</span></span>

|<span data-ttu-id="5b209-134">功能</span><span class="sxs-lookup"><span data-stu-id="5b209-134">To</span></span>|<span data-ttu-id="5b209-135">查看</span><span class="sxs-lookup"><span data-stu-id="5b209-135">See</span></span>|
|---|---|
|<span data-ttu-id="5b209-136">读取和写入数据文件</span><span class="sxs-lookup"><span data-stu-id="5b209-136">Read and write to a data file</span></span>|[<span data-ttu-id="5b209-137">如何：对新建的数据文件进行读取和写入</span><span class="sxs-lookup"><span data-stu-id="5b209-137">How to: Read and Write to a Newly Created Data File</span></span>](../../../../standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)|
|<span data-ttu-id="5b209-138">从文件读取文本</span><span class="sxs-lookup"><span data-stu-id="5b209-138">Read text from a file</span></span>|[<span data-ttu-id="5b209-139">如何：从文件中读取文本</span><span class="sxs-lookup"><span data-stu-id="5b209-139">How to: Read Text from a File</span></span>](../../../../standard/io/how-to-read-text-from-a-file.md)|
|<span data-ttu-id="5b209-140">将文本写入文件</span><span class="sxs-lookup"><span data-stu-id="5b209-140">Write text to a file</span></span>|[<span data-ttu-id="5b209-141">如何：将文本写入文件</span><span class="sxs-lookup"><span data-stu-id="5b209-141">How to: Write Text to a File</span></span>](../../../../standard/io/how-to-write-text-to-a-file.md)|
|<span data-ttu-id="5b209-142">从字符串中读取字符</span><span class="sxs-lookup"><span data-stu-id="5b209-142">Read characters from a string</span></span>|[<span data-ttu-id="5b209-143">如何：从字符串中读取字符</span><span class="sxs-lookup"><span data-stu-id="5b209-143">How to: Read Characters from a String</span></span>](../../../../standard/io/how-to-read-characters-from-a-string.md)|
|<span data-ttu-id="5b209-144">向字符串写入字符</span><span class="sxs-lookup"><span data-stu-id="5b209-144">Write characters to a string</span></span>|[<span data-ttu-id="5b209-145">如何：向字符串写入字符</span><span class="sxs-lookup"><span data-stu-id="5b209-145">How to: Write Characters to a String</span></span>](../../../../standard/io/how-to-write-characters-to-a-string.md)|
|<span data-ttu-id="5b209-146">加密数据</span><span class="sxs-lookup"><span data-stu-id="5b209-146">Encrypt data</span></span>|[<span data-ttu-id="5b209-147">加密数据</span><span class="sxs-lookup"><span data-stu-id="5b209-147">Encrypting Data</span></span>](../../../../standard/security/encrypting-data.md)|
|<span data-ttu-id="5b209-148">解密数据</span><span class="sxs-lookup"><span data-stu-id="5b209-148">Decrypt data</span></span>|[<span data-ttu-id="5b209-149">解密数据</span><span class="sxs-lookup"><span data-stu-id="5b209-149">Decrypting Data</span></span>](../../../../standard/security/decrypting-data.md)|

## <a name="file-access-and-attributes"></a><span data-ttu-id="5b209-150">文件访问权限和属性</span><span class="sxs-lookup"><span data-stu-id="5b209-150">File Access and Attributes</span></span>

<span data-ttu-id="5b209-151">可以控制文件创建、打开，以及与 <xref:System.IO.FileAccess>、<xref:System.IO.FileMode>和 <xref:System.IO.FileShare> 枚举分享的方式，枚举中包含 <xref:System.IO.FileStream> 类的构造函数使用的标志。</span><span class="sxs-lookup"><span data-stu-id="5b209-151">You can control how files are created, opened, and shared with the <xref:System.IO.FileAccess>, <xref:System.IO.FileMode>, and <xref:System.IO.FileShare> enumerations, which contain the flags used by the constructors of the <xref:System.IO.FileStream> class.</span></span> <span data-ttu-id="5b209-152">例如，打开或新建 <xref:System.IO.FileStream> 时，<xref:System.IO.FileMode> 枚举允许指定是否打开文件供追加用、如果指定的文件不存在是否创建新文件、是否覆盖文件等。</span><span class="sxs-lookup"><span data-stu-id="5b209-152">For example, when you open or create a new <xref:System.IO.FileStream>, the <xref:System.IO.FileMode> enumeration allows you to specify whether the file is opened for appending, whether a new file is created if the specified file does not exist, whether the file is overwritten, and so forth.</span></span>

<span data-ttu-id="5b209-153"><xref:System.IO.FileAttributes> 枚举可启用特定于文件的信息收集。</span><span class="sxs-lookup"><span data-stu-id="5b209-153">The <xref:System.IO.FileAttributes> enumeration enables the gathering of file-specific information.</span></span> <span data-ttu-id="5b209-154"><xref:System.IO.FileAttributes> 枚举返回文件的存储属性，如是否压缩、加密、隐藏、只读、是否为存档、目录、系统文件或临时文件。</span><span class="sxs-lookup"><span data-stu-id="5b209-154">The <xref:System.IO.FileAttributes> enumeration returns the file's stored attributes, such as whether it is compressed, encrypted, hidden, read-only, an archive, a directory, a system file, or a temporary file.</span></span>

<span data-ttu-id="5b209-155">下表列出涉及文件访问和文件特性的任务：</span><span class="sxs-lookup"><span data-stu-id="5b209-155">The following table lists tasks involving file access and file attributes:</span></span>

|<span data-ttu-id="5b209-156">功能</span><span class="sxs-lookup"><span data-stu-id="5b209-156">To</span></span>|<span data-ttu-id="5b209-157">查看</span><span class="sxs-lookup"><span data-stu-id="5b209-157">See</span></span>|
|---|---|
|<span data-ttu-id="5b209-158">打开并追加文本到日志文件</span><span class="sxs-lookup"><span data-stu-id="5b209-158">Open and append text to a log file</span></span>|[<span data-ttu-id="5b209-159">如何：打开并追加到日志文件</span><span class="sxs-lookup"><span data-stu-id="5b209-159">How to: Open and Append to a Log File</span></span>](../../../../standard/io/how-to-open-and-append-to-a-log-file.md)|
|<span data-ttu-id="5b209-160">确定文件特性</span><span class="sxs-lookup"><span data-stu-id="5b209-160">Determine the attributes of a file</span></span>|<xref:System.IO.FileAttributes>|

## <a name="file-permissions"></a><span data-ttu-id="5b209-161">文件权限</span><span class="sxs-lookup"><span data-stu-id="5b209-161">File Permissions</span></span>

<span data-ttu-id="5b209-162">可使用 <xref:System.Security.Permissions.FileIOPermission> 类控制对文件和目录的访问权限。</span><span class="sxs-lookup"><span data-stu-id="5b209-162">Controlling access to files and directories can be done with the <xref:System.Security.Permissions.FileIOPermission> class.</span></span> <span data-ttu-id="5b209-163">这对使用 Web 窗体的开发人员来说尤其重要，这些窗体默认在名为 ASPNET 的特殊本地用户帐户上下文中运行，该帐户作为 ASP.NET 和 .NET Framework 安装的一部分创建。</span><span class="sxs-lookup"><span data-stu-id="5b209-163">This may be particularly important for developers working with Web Forms, which by default run within the context of a special local user account named ASPNET, which is created as part of the ASP.NET and .NET Framework installations.</span></span> <span data-ttu-id="5b209-164">此类应用程序请求对资源的访问权限时，ASPNET 用户帐户的权限有限，这可能会阻止用户执行从 Web 应用程序写入到文件等操作。</span><span class="sxs-lookup"><span data-stu-id="5b209-164">When such an application requests access to a resource, the ASPNET user account has limited permissions, which may prevent the user from performing actions such as writing to a file from a Web application.</span></span> <span data-ttu-id="5b209-165">有关详细信息，请参阅 <xref:System.Security.Permissions.FileIOPermission>。</span><span class="sxs-lookup"><span data-stu-id="5b209-165">For more information, see <xref:System.Security.Permissions.FileIOPermission>.</span></span>

## <a name="isolated-file-storage"></a><span data-ttu-id="5b209-166">独立的文件存储</span><span class="sxs-lookup"><span data-stu-id="5b209-166">Isolated File Storage</span></span>

<span data-ttu-id="5b209-167">独立存储是一种尝试，为解决在用户或代码可能缺少必要权限的情况下处理文件时所产生的问题。</span><span class="sxs-lookup"><span data-stu-id="5b209-167">Isolated storage is an attempt to solve problems created when working with files where the user or code may lack necessary permissions.</span></span> <span data-ttu-id="5b209-168">独立存储向每个用户分配数据隔离舱，它包含一个或多个存储区。</span><span class="sxs-lookup"><span data-stu-id="5b209-168">Isolated storage assigns each user a data compartment, which can hold one or more stores.</span></span> <span data-ttu-id="5b209-169">可以按用户和程序集使存储区彼此独立。</span><span class="sxs-lookup"><span data-stu-id="5b209-169">Stores can be isolated from each other by user and by assembly.</span></span> <span data-ttu-id="5b209-170">只有创建存储区的用户和程序集才有权访问存储区。</span><span class="sxs-lookup"><span data-stu-id="5b209-170">Only the user and assembly that created a store have access to it.</span></span> <span data-ttu-id="5b209-171">存储区充当完整的虚拟文件系统，可以在一个存储区中创建并操作目录和文件。</span><span class="sxs-lookup"><span data-stu-id="5b209-171">A store acts as a complete virtual file system—within one store you can create and manipulate directories and files.</span></span>

<span data-ttu-id="5b209-172">下表列出了通常与独立文件存储相关联的任务。</span><span class="sxs-lookup"><span data-stu-id="5b209-172">The following table lists tasks commonly associated with isolated file storage.</span></span>

|<span data-ttu-id="5b209-173">功能</span><span class="sxs-lookup"><span data-stu-id="5b209-173">To</span></span>|<span data-ttu-id="5b209-174">查看</span><span class="sxs-lookup"><span data-stu-id="5b209-174">See</span></span>|
|---|---|
|<span data-ttu-id="5b209-175">创建独立存储区</span><span class="sxs-lookup"><span data-stu-id="5b209-175">Create an isolated store</span></span>|[<span data-ttu-id="5b209-176">如何：获取独立存储的存储区</span><span class="sxs-lookup"><span data-stu-id="5b209-176">How to: Obtain Stores for Isolated Storage</span></span>](../../../../standard/io/how-to-obtain-stores-for-isolated-storage.md)|
|<span data-ttu-id="5b209-177">枚举独立存储区</span><span class="sxs-lookup"><span data-stu-id="5b209-177">Enumerate isolated stores</span></span>|[<span data-ttu-id="5b209-178">如何：枚举独立存储的存储区</span><span class="sxs-lookup"><span data-stu-id="5b209-178">How to: Enumerate Stores for Isolated Storage</span></span>](../../../../standard/io/how-to-enumerate-stores-for-isolated-storage.md)|
|<span data-ttu-id="5b209-179">删除独立存储区</span><span class="sxs-lookup"><span data-stu-id="5b209-179">Delete an isolated store</span></span>|[<span data-ttu-id="5b209-180">如何：删除独立存储中的存储区</span><span class="sxs-lookup"><span data-stu-id="5b209-180">How to: Delete Stores in Isolated Storage</span></span>](../../../../standard/io/how-to-delete-stores-in-isolated-storage.md)|
|<span data-ttu-id="5b209-181">在独立存储中创建文件或目录</span><span class="sxs-lookup"><span data-stu-id="5b209-181">Create a file or directory in isolated storage</span></span>|[<span data-ttu-id="5b209-182">如何：在独立存储中创建文件和目录</span><span class="sxs-lookup"><span data-stu-id="5b209-182">How to: Create Files and Directories in Isolated Storage</span></span>](../../../../standard/io/how-to-create-files-and-directories-in-isolated-storage.md)|
|<span data-ttu-id="5b209-183">在独立存储中查找文件</span><span class="sxs-lookup"><span data-stu-id="5b209-183">Find a file in isolated storage</span></span>|[<span data-ttu-id="5b209-184">如何：在独立存储中查找现有文件和目录</span><span class="sxs-lookup"><span data-stu-id="5b209-184">How to: Find Existing Files and Directories in Isolated Storage</span></span>](../../../../standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md)|
|<span data-ttu-id="5b209-185">在独立存储中从文件读取文件或向文件写入文件</span><span class="sxs-lookup"><span data-stu-id="5b209-185">Read from or write to a file in isolated storage</span></span>|[<span data-ttu-id="5b209-186">如何：在独立存储中读取和写入文件</span><span class="sxs-lookup"><span data-stu-id="5b209-186">How to: Read and Write to Files in Isolated Storage</span></span>](../../../../standard/io/how-to-read-and-write-to-files-in-isolated-storage.md)|
|<span data-ttu-id="5b209-187">在独立存储中删除文件或目录</span><span class="sxs-lookup"><span data-stu-id="5b209-187">Delete a file or directory in isolated storage</span></span>|[<span data-ttu-id="5b209-188">如何：在独立存储中删除文件和目录</span><span class="sxs-lookup"><span data-stu-id="5b209-188">How to: Delete Files and Directories in Isolated Storage</span></span>](../../../../standard/io/how-to-delete-files-and-directories-in-isolated-storage.md)|

## <a name="file-events"></a><span data-ttu-id="5b209-189">文件事件</span><span class="sxs-lookup"><span data-stu-id="5b209-189">File Events</span></span>

<span data-ttu-id="5b209-190"><xref:System.IO.FileSystemWatcher> 组件允许监视系统上或任何你对其具有网络访问权限的计算机上的文件和目录所作的更改。</span><span class="sxs-lookup"><span data-stu-id="5b209-190">The <xref:System.IO.FileSystemWatcher> component allows you to watch for changes in files and directories on your system or on any computer to which you have network access.</span></span> <span data-ttu-id="5b209-191">例如，如果修改了文件，可能想要向用户发送更改警报。</span><span class="sxs-lookup"><span data-stu-id="5b209-191">For example, if a file is modified, you might want to send a user an alert that the change has taken place.</span></span> <span data-ttu-id="5b209-192">发生更改时，会引发一个或多个事件并将其存储在缓冲区中，然后移交给 <xref:System.IO.FileSystemWatcher> 组件进行处理。</span><span class="sxs-lookup"><span data-stu-id="5b209-192">When changes occur, one or more events are raised, stored in a buffer, and handed to the <xref:System.IO.FileSystemWatcher> component for processing.</span></span>

## <a name="see-also"></a><span data-ttu-id="5b209-193">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5b209-193">See also</span></span>

- [<span data-ttu-id="5b209-194">撰写流</span><span class="sxs-lookup"><span data-stu-id="5b209-194">Composing Streams</span></span>](../../../../standard/io/composing-streams.md)
- [<span data-ttu-id="5b209-195">文件和流 I/O</span><span class="sxs-lookup"><span data-stu-id="5b209-195">File and Stream I/O</span></span>](../../../../standard/io/index.md)
- [<span data-ttu-id="5b209-196">异步文件 I/O</span><span class="sxs-lookup"><span data-stu-id="5b209-196">Asynchronous File I/O</span></span>](../../../../standard/io/asynchronous-file-i-o.md)
- [<span data-ttu-id="5b209-197">在 .NET Framework 文件 I/O 和文件系统中使用的类 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5b209-197">Classes Used in .NET Framework File I/O and the File System (Visual Basic)</span></span>](classes-used-in-net-framework-file-io-and-the-file-system.md)
