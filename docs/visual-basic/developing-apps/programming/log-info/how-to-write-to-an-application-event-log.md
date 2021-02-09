---
description: 详细了解：操作说明：写入应用程序事件日志 (Visual Basic)
title: 如何：将信息写入应用程序事件日志
ms.date: 07/20/2015
helpviewer_keywords:
- Computer.EventLog element
- WriteEntry method [Visual Basic]
- My.Computer.EventLog element
- event logs, writing to
ms.assetid: cadbc8c1-87af-4746-934e-55b79a4f6e2b
ms.openlocfilehash: ea53ff84f1fcf175912e35eb7433ece26886cf44
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797284"
---
# <a name="how-to-write-to-an-application-event-log-visual-basic"></a><span data-ttu-id="bd393-103">如何：写入应用程序事件日志 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bd393-103">How to: Write to an Application Event Log (Visual Basic)</span></span>

<span data-ttu-id="bd393-104">可以使用 `My.Application.Log` 和 `My.Log` 对象来写入有关应用程序中所发生事件的信息。</span><span class="sxs-lookup"><span data-stu-id="bd393-104">You can use the `My.Application.Log` and `My.Log` objects to write information about events that occur in your application.</span></span> <span data-ttu-id="bd393-105">本示例将演示如何配置事件日志侦听器，以便 `My.Application.Log` 将跟踪信息写入应用程序事件日志。</span><span class="sxs-lookup"><span data-stu-id="bd393-105">This example shows how to configure an event log listener so `My.Application.Log` writes tracing information to the Application event log.</span></span>

<span data-ttu-id="bd393-106">不能将信息写入安全日志。</span><span class="sxs-lookup"><span data-stu-id="bd393-106">You cannot write to the Security log.</span></span> <span data-ttu-id="bd393-107">只有 LocalSystem 或 Administrator 帐户的成员可以将信息写入系统日志。</span><span class="sxs-lookup"><span data-stu-id="bd393-107">In order to write to the System log, you must be a member of the LocalSystem or Administrator account.</span></span>

<span data-ttu-id="bd393-108">若要查看事件日志，可以使用“服务器资源管理器”  或“Windows 事件查看器” 。</span><span class="sxs-lookup"><span data-stu-id="bd393-108">To view an event log, you can use **Server Explorer** or **Windows Event Viewer**.</span></span> <span data-ttu-id="bd393-109">有关详细信息，请参阅 [.NET Framework 中的 ETW 事件](../../../../framework/performance/etw-events.md)。</span><span class="sxs-lookup"><span data-stu-id="bd393-109">For more information, see [ETW Events in the .NET Framework](../../../../framework/performance/etw-events.md).</span></span>

## <a name="to-add-and-configure-the-event-log-listener"></a><span data-ttu-id="bd393-110">添加和配置事件日志侦听器</span><span class="sxs-lookup"><span data-stu-id="bd393-110">To add and configure the event log listener</span></span>

1. <span data-ttu-id="bd393-111">在“解决方案资源管理器”  中右键单击 app.config，然后选择“打开” 。</span><span class="sxs-lookup"><span data-stu-id="bd393-111">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>

    <span data-ttu-id="bd393-112">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="bd393-112">\- or -</span></span>

    <span data-ttu-id="bd393-113">如果其中没有 app.config 文件，</span><span class="sxs-lookup"><span data-stu-id="bd393-113">If there is no app.config file,</span></span>

    1. <span data-ttu-id="bd393-114">在 **“项目”** 菜单上选择 **“添加新项”** 。</span><span class="sxs-lookup"><span data-stu-id="bd393-114">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="bd393-115">在“添加新项”  对话框中，选择“应用程序配置文件”  。</span><span class="sxs-lookup"><span data-stu-id="bd393-115">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="bd393-116">单击 **添加**。</span><span class="sxs-lookup"><span data-stu-id="bd393-116">Click **Add**.</span></span>

2. <span data-ttu-id="bd393-117">在应用程序配置文件中找到 `<listeners>` 部分。</span><span class="sxs-lookup"><span data-stu-id="bd393-117">Locate the `<listeners>` section in the application configuration file.</span></span>

    <span data-ttu-id="bd393-118">`<listeners>` 部分位于 name 属性为“DefaultSource”的 `<source>` 部分当中，后者又嵌套在 `<system.diagnostics>` 部分当中，位于顶级 `<configuration>` 部分之下。</span><span class="sxs-lookup"><span data-stu-id="bd393-118">You will find the `<listeners>` section in the `<source>` section with the name attribute "DefaultSource", which is nested under the `<system.diagnostics>` section, which is nested under the top-level `<configuration>` section.</span></span>

3. <span data-ttu-id="bd393-119">将此元素添加到该 `<listeners>` 部分：</span><span class="sxs-lookup"><span data-stu-id="bd393-119">Add this element to that `<listeners>` section:</span></span>

    ```xml
    <add name="EventLog"/>
    ```

4. <span data-ttu-id="bd393-120">找到 `<sharedListeners>` 部分，该部分位于 `<system.diagnostics>` 部分当中，后者又位于顶级 `<configuration>` 部分之下。</span><span class="sxs-lookup"><span data-stu-id="bd393-120">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="bd393-121">将此元素添加到该 `<sharedListeners>` 部分：</span><span class="sxs-lookup"><span data-stu-id="bd393-121">Add this element to that `<sharedListeners>` section:</span></span>

    ```xml
    <add name="EventLog"
        type="System.Diagnostics.EventLogTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="APPLICATION_NAME"/>
    ```

    <span data-ttu-id="bd393-122">将 `APPLICATION_NAME` 替换为应用程序的名称。</span><span class="sxs-lookup"><span data-stu-id="bd393-122">Replace `APPLICATION_NAME` with the name of your application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="bd393-123">通常情况下，应用程序只将错误信息写入事件日志。</span><span class="sxs-lookup"><span data-stu-id="bd393-123">Typically, an application writes only errors to the event log.</span></span> <span data-ttu-id="bd393-124">有关筛选日志输出的信息，请参阅 [Walkthrough: Filtering My.Application.Log Output](walkthrough-filtering-my-application-log-output.md)。</span><span class="sxs-lookup"><span data-stu-id="bd393-124">For information on filtering log output, see [Walkthrough: Filtering My.Application.Log Output](walkthrough-filtering-my-application-log-output.md).</span></span>

## <a name="to-write-event-information-to-the-event-log"></a><span data-ttu-id="bd393-125">将事件信息写入事件日志</span><span class="sxs-lookup"><span data-stu-id="bd393-125">To write event information to the event log</span></span>

<span data-ttu-id="bd393-126">使用 `My.Application.Log.WriteEntry` 或 `My.Application.Log.WriteException` 方法可以将信息写入事件日志。</span><span class="sxs-lookup"><span data-stu-id="bd393-126">Use the `My.Application.Log.WriteEntry` or `My.Application.Log.WriteException` method to write information to the event log.</span></span> <span data-ttu-id="bd393-127">有关详细信息，请参阅[如何：编写日志消息](how-to-write-log-messages.md)和[如何：记录异常](how-to-log-exceptions.md)。</span><span class="sxs-lookup"><span data-stu-id="bd393-127">For more information, see [How to: Write Log Messages](how-to-write-log-messages.md) and [How to: Log Exceptions](how-to-log-exceptions.md).</span></span>

<span data-ttu-id="bd393-128">为程序集配置事件日志侦听器后，它将接收该程序集写入 `My.Application.Log` 的所有消息。</span><span class="sxs-lookup"><span data-stu-id="bd393-128">After you configure the event log listener for an assembly, it receives all messages that `My.Application.Log` writes from that assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="bd393-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="bd393-129">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="bd393-130">使用应用程序日志</span><span class="sxs-lookup"><span data-stu-id="bd393-130">Working with Application Logs</span></span>](working-with-application-logs.md)
- [<span data-ttu-id="bd393-131">如何：日志异常</span><span class="sxs-lookup"><span data-stu-id="bd393-131">How to: Log Exceptions</span></span>](how-to-log-exceptions.md)
- [<span data-ttu-id="bd393-132">演练：确定 My.Application.Log 在哪里写入信息</span><span class="sxs-lookup"><span data-stu-id="bd393-132">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](walkthrough-determining-where-my-application-log-writes-information.md)
