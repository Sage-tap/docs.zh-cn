---
description: 详细了解：使用 Application 日志 (Visual Basic)
title: 使用应用程序日志
ms.date: 07/20/2015
helpviewer_keywords:
- logs, application
- application event logs, Visual Basic
- application event logs
ms.assetid: 2581afd1-5791-4bc4-86b2-46244e9fe468
ms.openlocfilehash: 0c05bd63cfbae668c58a87aa39651b6c3ef166ad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792266"
---
# <a name="working-with-application-logs-in-visual-basic"></a><span data-ttu-id="fc45f-103">使用 Application 日志 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fc45f-103">Working with Application Logs in Visual Basic</span></span>

<span data-ttu-id="fc45f-104">使用 `My.Application.Log` 和 `My.Log` 对象可以轻松将日志记录和跟踪信息写入日志。</span><span class="sxs-lookup"><span data-stu-id="fc45f-104">The `My.Application.Log` and `My.Log` objects make it easy to write logging and tracing information to logs.</span></span>

## <a name="how-messages-are-logged"></a><span data-ttu-id="fc45f-105">如何记录消息</span><span class="sxs-lookup"><span data-stu-id="fc45f-105">How Messages are Logged</span></span>

<span data-ttu-id="fc45f-106">首先，通过日志的 <xref:System.Diagnostics.TraceSource.Switch%2A> 属性的 <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A> 属性检查消息的严重性。</span><span class="sxs-lookup"><span data-stu-id="fc45f-106">First, the severity of the message is checked with the <xref:System.Diagnostics.TraceSource.Switch%2A> property of the log's <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A> property.</span></span> <span data-ttu-id="fc45f-107">默认情况下，只有严重性级别为“信息”及以上的消息才会传递到日志的 `TraceListener` 集合中指定的跟踪侦听器。</span><span class="sxs-lookup"><span data-stu-id="fc45f-107">By default, only messages of severity "Information" and higher are passed on to the trace listeners, specified in the log's `TraceListener` collection.</span></span> <span data-ttu-id="fc45f-108">然后，各侦听器会将消息的严重性与侦听器的 <xref:System.Diagnostics.TraceSource.Switch%2A> 属性进行比较。</span><span class="sxs-lookup"><span data-stu-id="fc45f-108">Then, each listener compares the severity of the message to the listener's <xref:System.Diagnostics.TraceSource.Switch%2A> property.</span></span> <span data-ttu-id="fc45f-109">如果消息的严重性足够很高，则侦听器将写出消息。</span><span class="sxs-lookup"><span data-stu-id="fc45f-109">If the message's severity is high enough, the listener writes out the message.</span></span>

<span data-ttu-id="fc45f-110">下图演示如何将写入 `WriteEntry` 方法的消息传递到日志的跟踪侦听器的 `WriteLine` 方法：</span><span class="sxs-lookup"><span data-stu-id="fc45f-110">The following diagram shows how a message written to the `WriteEntry` method gets passed to the `WriteLine` methods of the log's trace listeners:</span></span>

![显示 My 日志调用的图。](./media/working-with-application-logs/my-log-call-messages.png)

<span data-ttu-id="fc45f-112">可以通过更改应用程序的配置文件来更改日志和跟踪侦听器的行为。</span><span class="sxs-lookup"><span data-stu-id="fc45f-112">You can change the behavior of the log and the trace listeners by changing the application's configuration file.</span></span> <span data-ttu-id="fc45f-113">下图演示日志和配置文件各个部分之间的对应关系。</span><span class="sxs-lookup"><span data-stu-id="fc45f-113">The following diagram shows the correspondence between the parts of the log and the configuration file.</span></span>

![显示 My 日志配置的图。](./media/working-with-application-logs/my-log-configuration.png)

## <a name="where-messages-are-logged"></a><span data-ttu-id="fc45f-115">记录消息的位置</span><span class="sxs-lookup"><span data-stu-id="fc45f-115">Where Messages are Logged</span></span>

<span data-ttu-id="fc45f-116">如果程序集没有配置文件，则 `My.Application.Log` 和 `My.Log` 对象会将消息写入应用程序的调试输出（通过 <xref:System.Diagnostics.DefaultTraceListener> 类实现）。</span><span class="sxs-lookup"><span data-stu-id="fc45f-116">If the assembly has no configuration file, the `My.Application.Log` and `My.Log` objects write to the application's debug output (through the <xref:System.Diagnostics.DefaultTraceListener> class).</span></span> <span data-ttu-id="fc45f-117">此外， `My.Application.Log` 对象会将消息写入程序集的日志文件（通过 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> 类实现）， `My.Log` 对象会将消息写入 ASP.NET 网页的输出（通过 <xref:System.Web.WebPageTraceListener> 类实现）。</span><span class="sxs-lookup"><span data-stu-id="fc45f-117">In addition, the `My.Application.Log` object writes to the assembly's log file (through the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class), while the `My.Log` object writes to the ASP.NET Web page's output (through the <xref:System.Web.WebPageTraceListener> class).</span></span>

<span data-ttu-id="fc45f-118">在调试模式下运行应用程序时，可在 Visual Studio 的“输出”窗口中查看调试输出。</span><span class="sxs-lookup"><span data-stu-id="fc45f-118">The debug output can be viewed in the Visual Studio **Output** window when running your application in debug mode.</span></span> <span data-ttu-id="fc45f-119">若要打开“输出”  窗口中，请单击“调试”  菜单项，指向“Windows” ，然后单击“输出” 。</span><span class="sxs-lookup"><span data-stu-id="fc45f-119">To open the **Output** window, click the **Debug** menu item, point to **Windows**, and then click **Output**.</span></span> <span data-ttu-id="fc45f-120">在“输出”  窗口中，在“显示输出来源”  框中选择“调试”  。</span><span class="sxs-lookup"><span data-stu-id="fc45f-120">In the **Output** window, select **Debug** from the **Show output from** box.</span></span>

<span data-ttu-id="fc45f-121">默认情况下， `My.Application.Log` 将日志文件写入用户应用程序数据的路径。</span><span class="sxs-lookup"><span data-stu-id="fc45f-121">By default, `My.Application.Log` writes the log file in the path for the user's application data.</span></span> <span data-ttu-id="fc45f-122">可以通过 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.FullLogFileName%2A> 对象的 <xref:Microsoft.VisualBasic.Logging.Log.DefaultFileLogWriter%2A> 属性获取路径。</span><span class="sxs-lookup"><span data-stu-id="fc45f-122">You can get the path from the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.FullLogFileName%2A> property of the <xref:Microsoft.VisualBasic.Logging.Log.DefaultFileLogWriter%2A> object.</span></span> <span data-ttu-id="fc45f-123">路径的格式如下：</span><span class="sxs-lookup"><span data-stu-id="fc45f-123">The format of that path is as follows:</span></span>

`BasePath`\\`CompanyName`\\`ProductName`\\`ProductVersion`

<span data-ttu-id="fc45f-124">`BasePath` 的典型值如下所示：</span><span class="sxs-lookup"><span data-stu-id="fc45f-124">A typical value for `BasePath` is as follows.</span></span>

<span data-ttu-id="fc45f-125">C:\Documents and Settings\\`username`\Application Data</span><span class="sxs-lookup"><span data-stu-id="fc45f-125">C:\Documents and Settings\\`username`\Application Data</span></span>

<span data-ttu-id="fc45f-126">`CompanyName`、 `ProductName`和 `ProductVersion` 的值来自应用程序的程序集信息。</span><span class="sxs-lookup"><span data-stu-id="fc45f-126">The values of `CompanyName`, `ProductName`, and `ProductVersion` come from the application's assembly information.</span></span> <span data-ttu-id="fc45f-127">日志文件名称的格式为 *AssemblyName*.log，其中 *AssemblyName* 是程序集的文件名称（不含扩展名）。</span><span class="sxs-lookup"><span data-stu-id="fc45f-127">The form of the log file name is *AssemblyName*.log, where *AssemblyName* is the file name of the assembly without the extension.</span></span> <span data-ttu-id="fc45f-128">如果需要多个日志文件（如原始日志不可用或应用程序尝试写入日志时），日志文件名称的格式为 *AssemblyName*-*iteration*.log，其中 `iteration` 为一个正 `Integer`。</span><span class="sxs-lookup"><span data-stu-id="fc45f-128">If more than one log file is needed, such as when the original log is unavailable when the application attempts to write to the log, the form for the log file name is *AssemblyName*-*iteration*.log, where `iteration` is a positive `Integer`.</span></span>

<span data-ttu-id="fc45f-129">可以通过添加或更改计算机和应用程序的配置文件来重写默认行为。</span><span class="sxs-lookup"><span data-stu-id="fc45f-129">You can override the default behavior by adding or changing the computer's and the application's configuration files.</span></span> <span data-ttu-id="fc45f-130">有关详细信息，请参阅 [演练：更改 My.Application.Log 写入信息的位置](walkthrough-changing-where-my-application-log-writes-information.md)。</span><span class="sxs-lookup"><span data-stu-id="fc45f-130">For more information, see [Walkthrough: Changing Where My.Application.Log Writes Information](walkthrough-changing-where-my-application-log-writes-information.md).</span></span>

## <a name="configuring-log-settings"></a><span data-ttu-id="fc45f-131">配置日志设置</span><span class="sxs-lookup"><span data-stu-id="fc45f-131">Configuring Log Settings</span></span>

<span data-ttu-id="fc45f-132">`Log` 对象具有默认的实现，即使没有应用程序配置文件 app.config 也可工作。若要更改默认设置，必须添加包含新设置的配置文件。</span><span class="sxs-lookup"><span data-stu-id="fc45f-132">The `Log` object has a default implementation that works without an application configuration file, app.config. To change the defaults, you must add a configuration file with the new settings.</span></span> <span data-ttu-id="fc45f-133">有关更多信息，请参见 [Walkthrough: Filtering My.Application.Log Output](walkthrough-filtering-my-application-log-output.md)。</span><span class="sxs-lookup"><span data-stu-id="fc45f-133">For more information, see [Walkthrough: Filtering My.Application.Log Output](walkthrough-filtering-my-application-log-output.md).</span></span>

<span data-ttu-id="fc45f-134">日志配置部分位于 `<system.diagnostics>` 节点当中，该节点位于 app.config 文件的 `<configuration>` 节点之下。</span><span class="sxs-lookup"><span data-stu-id="fc45f-134">The log configuration sections are located in the `<system.diagnostics>` node in the main `<configuration>` node of the app.config file.</span></span> <span data-ttu-id="fc45f-135">日志信息在以下几个节点中定义：</span><span class="sxs-lookup"><span data-stu-id="fc45f-135">Log information is defined in several nodes:</span></span>

- <span data-ttu-id="fc45f-136">`Log` 对象的侦听器在名为 DefaultSource 的 `<sources>` 节点中定义。</span><span class="sxs-lookup"><span data-stu-id="fc45f-136">The listeners for the `Log` object are defined in the `<sources>` node named DefaultSource.</span></span>

- <span data-ttu-id="fc45f-137">`Log` 对象的严重性筛选器在名为 DefaultSource 的 `<switches>` 节点中定义。</span><span class="sxs-lookup"><span data-stu-id="fc45f-137">The severity filter for the `Log` object is defined in the `<switches>` node named DefaultSwitch.</span></span>

- <span data-ttu-id="fc45f-138">日志侦听器在 `<sharedListeners>` 节点中定义。</span><span class="sxs-lookup"><span data-stu-id="fc45f-138">The log listeners are defined in the `<sharedListeners>` node.</span></span>

 <span data-ttu-id="fc45f-139">以下代码示例演示了 `<sources>`、 `<switches>`和 `<sharedListeners>` 节点：</span><span class="sxs-lookup"><span data-stu-id="fc45f-139">Examples of `<sources>`, `<switches>`, and `<sharedListeners>` nodes are shown in the following code:</span></span>

```xml
<configuration>
  <system.diagnostics>
    <sources>
      <source name="DefaultSource" switchName="DefaultSwitch">
        <listeners>
          <add name="FileLog"/>
        </listeners>
      </source>
    </sources>
    <switches>
      <add name="DefaultSwitch" value="Information" />
    </switches>
    <sharedListeners>
      <add name="FileLog"
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
          Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,
          PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL"
        initializeData="FileLogWriter"
      />
    </sharedListeners>
  </system.diagnostics>
</configuration>
```

## <a name="changing-log-settings-after-deployment"></a><span data-ttu-id="fc45f-140">在部署后更改日志设置</span><span class="sxs-lookup"><span data-stu-id="fc45f-140">Changing Log Settings after Deployment</span></span>

<span data-ttu-id="fc45f-141">开发应用程序时，其配置设置存储在 app.config 文件中，如上面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="fc45f-141">When you develop an application, its configuration settings are stored in the app.config file, as shown in the examples above.</span></span> <span data-ttu-id="fc45f-142">部署应用程序后，仍然可以通过编辑配置文件来配置日志。</span><span class="sxs-lookup"><span data-stu-id="fc45f-142">After you deploy your application, you can still configure the log by editing the configuration file.</span></span> <span data-ttu-id="fc45f-143">在基于 Windows 的应用程序中，此文件的名称为 *applicationName*.exe.config，并且它必须位于可执行文件所在的相同文件夹中。</span><span class="sxs-lookup"><span data-stu-id="fc45f-143">In a Windows-based application, this file's name is *applicationName*.exe.config, and it must reside in the same folder as the executable file.</span></span> <span data-ttu-id="fc45f-144">对于 Web 应用程序，这是与项目关联的 Web.config 文件。</span><span class="sxs-lookup"><span data-stu-id="fc45f-144">For a Web application, this is the Web.config file associated with the project.</span></span>

<span data-ttu-id="fc45f-145">应用程序首次执行创建类实例的代码时，它会检查配置文件以获取有关对象的信息。</span><span class="sxs-lookup"><span data-stu-id="fc45f-145">When your application executes the code that creates an instance of a class for the first time, it checks the configuration file for information about the object.</span></span> <span data-ttu-id="fc45f-146">对于 `Log` 对象，首次访问 `Log` 对象时会发生这种情况。</span><span class="sxs-lookup"><span data-stu-id="fc45f-146">For the `Log` object, this happens the first time the `Log` object is accessed.</span></span> <span data-ttu-id="fc45f-147">对于任何特定的对象，系统将仅检查一次配置文件，即应用程序首次创建对象时。</span><span class="sxs-lookup"><span data-stu-id="fc45f-147">The system examines the configuration file only once for any particular object—the first time your application creates the object.</span></span> <span data-ttu-id="fc45f-148">因此，可能需要重启应用程序以使更改生效。</span><span class="sxs-lookup"><span data-stu-id="fc45f-148">Therefore, you may need to restart the application for the changes to take effect.</span></span>

<span data-ttu-id="fc45f-149">在已部署的应用程序中，在应用程序未运行之前，可以通过重新配置 switch 对象启用跟踪代码。</span><span class="sxs-lookup"><span data-stu-id="fc45f-149">In a deployed application, you enable trace code by reconfiguring switch objects before your application starts.</span></span> <span data-ttu-id="fc45f-150">通常，此过程将要求启用和禁用 switch 对象、更改跟踪级别，以及重启应用程序。</span><span class="sxs-lookup"><span data-stu-id="fc45f-150">Typically, this involves turning the switch objects on and off or by changing the tracing levels, and then restarting your application.</span></span>

## <a name="security-considerations"></a><span data-ttu-id="fc45f-151">安全注意事项</span><span class="sxs-lookup"><span data-stu-id="fc45f-151">Security Considerations</span></span>

<span data-ttu-id="fc45f-152">将数据写入日志时应注意以下事项：</span><span class="sxs-lookup"><span data-stu-id="fc45f-152">Consider the following when writing data to the log:</span></span>

- <span data-ttu-id="fc45f-153">**避免泄露用户信息。**</span><span class="sxs-lookup"><span data-stu-id="fc45f-153">**Avoid leaking user information.**</span></span> <span data-ttu-id="fc45f-154">确保应用程序仅将批准的信息写入日志。</span><span class="sxs-lookup"><span data-stu-id="fc45f-154">Ensure that your application writes only approved information to the log.</span></span> <span data-ttu-id="fc45f-155">例如，应用程序日志中可以包含用户名，但不能包含用户密码。</span><span class="sxs-lookup"><span data-stu-id="fc45f-155">For example, it may be acceptable for the application log to contain user names, but not user passwords.</span></span>

- <span data-ttu-id="fc45f-156">**确保日志位于安全的位置。**</span><span class="sxs-lookup"><span data-stu-id="fc45f-156">**Make log locations secure.**</span></span> <span data-ttu-id="fc45f-157">任何包含潜在敏感信息的日志都应存储在安全的位置。</span><span class="sxs-lookup"><span data-stu-id="fc45f-157">Any log that contains potentially sensitive information should be stored in a secure location.</span></span>

- <span data-ttu-id="fc45f-158">**避免误导性信息。**</span><span class="sxs-lookup"><span data-stu-id="fc45f-158">**Avoid misleading information.**</span></span> <span data-ttu-id="fc45f-159">一般情况下，应用程序应先验证用户输入的所有数据，然后再使用这些数据。</span><span class="sxs-lookup"><span data-stu-id="fc45f-159">In general, your application should validate all data entered by a user before using that data.</span></span> <span data-ttu-id="fc45f-160">其中包括将数据写入应用程序日志。</span><span class="sxs-lookup"><span data-stu-id="fc45f-160">This includes writing data to the application log.</span></span>

- <span data-ttu-id="fc45f-161">**避免拒绝服务。**</span><span class="sxs-lookup"><span data-stu-id="fc45f-161">**Avoid denial of service.**</span></span> <span data-ttu-id="fc45f-162">如果应用程序将太多的信息写入日志，则可能填满日志或导致难以查找重要的信息。</span><span class="sxs-lookup"><span data-stu-id="fc45f-162">If your application writes too much information to the log, it could fill the log or make finding important information difficult.</span></span>

## <a name="see-also"></a><span data-ttu-id="fc45f-163">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fc45f-163">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="fc45f-164">记录来自应用程序的信息</span><span class="sxs-lookup"><span data-stu-id="fc45f-164">Logging Information from the Application</span></span>](index.md)
