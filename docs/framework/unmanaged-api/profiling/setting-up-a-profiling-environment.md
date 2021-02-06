---
description: 了解详细信息：设置分析环境
title: 设置分析环境
ms.date: 03/30/2017
helpviewer_keywords:
- environment variables, profiling API
- profiling API [.NET Framework], setting up environment
- COR_PROFILER environment variable
- Windows Service applications, profiling
- profiling API [.NET Framework], Windows Service applications
- COR_ENABLE_PROFILING environment variable
- profiling API [.NET Framework], enabling
ms.assetid: fefca07f-7555-4e77-be86-3c542e928312
ms.openlocfilehash: 88bfb50b02874bf79f03414213329c5dcc79a9fa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646343"
---
# <a name="setting-up-a-profiling-environment"></a><span data-ttu-id="ba91f-103">设置分析环境</span><span class="sxs-lookup"><span data-stu-id="ba91f-103">Setting Up a Profiling Environment</span></span>

> [!NOTE]
> <span data-ttu-id="ba91f-104">.NET Framework 4 中的分析发生了重大更改。</span><span class="sxs-lookup"><span data-stu-id="ba91f-104">There have been substantial changes to profiling in the .NET Framework 4.</span></span>  
  
 <span data-ttu-id="ba91f-105">托管进程（应用程序或服务）启动时，将加载公共语言运行时 (CLR)。</span><span class="sxs-lookup"><span data-stu-id="ba91f-105">When a managed process (application or service) starts, it loads the common language runtime (CLR).</span></span> <span data-ttu-id="ba91f-106">初始化 CLR 时，将评估以下两个环境变量以决定进程是否应连接到探查器：</span><span class="sxs-lookup"><span data-stu-id="ba91f-106">When the CLR is initialized, it evaluates the following two environmental variables to decide whether the process should connect to a profiler:</span></span>  
  
- <span data-ttu-id="ba91f-107">COR_ENABLE_PROFILING：仅当此环境变量存在并设置为 1 时，CLR 连接到探查器。</span><span class="sxs-lookup"><span data-stu-id="ba91f-107">COR_ENABLE_PROFILING: The CLR connects to a profiler only if this environment variable exists and is set to 1.</span></span>  
  
- <span data-ttu-id="ba91f-108">COR_PROFILER：如果 COR_ENABLE_PROFILING 检查通过，CLR 将连接到具有此 CLSID 或 ProgID 的探查器（已事先存储在注册表中）。</span><span class="sxs-lookup"><span data-stu-id="ba91f-108">COR_PROFILER: If the COR_ENABLE_PROFILING check passes, the CLR connects to the profiler that has this CLSID or ProgID, which must have been stored previously in the registry.</span></span> <span data-ttu-id="ba91f-109">COR_PROFILER 环境变量被定义为字符串，如以下两个示例中所示。</span><span class="sxs-lookup"><span data-stu-id="ba91f-109">The COR_PROFILER environment variable is defined as a string, as shown in the following two examples.</span></span>  
  
    ```cpp  
    set COR_PROFILER={32E2F4DA-1BEA-47ea-88F9-C5DAF691C94A}  
    set COR_PROFILER="MyProfiler"  
    ```  
  
 <span data-ttu-id="ba91f-110">若要分析 CLR 应用程序，必须在运行该应用程序之前设置 COR_ENABLE_PROFILING 和 COR_PROFILER 环境变量。</span><span class="sxs-lookup"><span data-stu-id="ba91f-110">To profile a CLR application, you must set the COR_ENABLE_PROFILING and COR_PROFILER environment variables before you run the application.</span></span> <span data-ttu-id="ba91f-111">还必须确保已注册探查器 DLL。</span><span class="sxs-lookup"><span data-stu-id="ba91f-111">You must also make sure that the profiler DLL is registered.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ba91f-112">从 .NET Framework 4 开始，无需注册探查器。</span><span class="sxs-lookup"><span data-stu-id="ba91f-112">Starting with the .NET Framework 4, profilers do not have to be registered.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ba91f-113">若要在 .NET Framework 4 和更高版本中使用 .NET Framework 版本2.0、3.0 和3.5 探查器，则必须设置 COMPLUS_ProfAPI_ProfilerCompatibilitySetting 环境变量。</span><span class="sxs-lookup"><span data-stu-id="ba91f-113">To use .NET Framework versions 2.0, 3.0, and 3.5 profilers in the .NET Framework 4 and later versions, you must set the COMPLUS_ProfAPI_ProfilerCompatibilitySetting environment variable.</span></span>  
  
## <a name="environment-variable-scope"></a><span data-ttu-id="ba91f-114">环境变量范围</span><span class="sxs-lookup"><span data-stu-id="ba91f-114">Environment Variable Scope</span></span>  

 <span data-ttu-id="ba91f-115">设置 COR_ENABLE_PROFILING 和 COR_PROFILER 环境变量的方式将决定其影响范围。</span><span class="sxs-lookup"><span data-stu-id="ba91f-115">How you set the COR_ENABLE_PROFILING and COR_PROFILER environment variables will determine their scope of influence.</span></span> <span data-ttu-id="ba91f-116">可以通过下列方式之一设置这些变量：</span><span class="sxs-lookup"><span data-stu-id="ba91f-116">You can set these variables in one of the following ways:</span></span>  
  
- <span data-ttu-id="ba91f-117">如果在 [ICorDebug：： CreateProcess](../debugging/icordebug-createprocess-method.md) 调用中设置变量，则这些变量将仅应用于当时正在运行的应用程序。</span><span class="sxs-lookup"><span data-stu-id="ba91f-117">If you set the variables in an [ICorDebug::CreateProcess](../debugging/icordebug-createprocess-method.md) call, they will apply only to the application that you are running at the time.</span></span> <span data-ttu-id="ba91f-118">（它们将也应用于由继承环境的应用程序启动的其他应用程序。）</span><span class="sxs-lookup"><span data-stu-id="ba91f-118">(They will also apply to other applications started by that application that inherit the environment.)</span></span>  
  
- <span data-ttu-id="ba91f-119">如果在“命令提示符”窗口中设置变量，则它们将应用于从该窗口中启动的所有应用程序。</span><span class="sxs-lookup"><span data-stu-id="ba91f-119">If you set the variables in a Command Prompt window, they will apply to all applications that are started from that window.</span></span>  
  
- <span data-ttu-id="ba91f-120">如果在用户级别设置变量，它们将应用于用文件资源管理器启动的所有应用程序。</span><span class="sxs-lookup"><span data-stu-id="ba91f-120">If you set the variables at the user level, they will apply to all applications that you start with File Explorer.</span></span> <span data-ttu-id="ba91f-121">在设置变量后打开的“命令提示符”窗口将具有这些环境设置，从该窗口中启动的任何应用程序也将如此。</span><span class="sxs-lookup"><span data-stu-id="ba91f-121">A Command Prompt window that you open after you set the variables will have these environment settings, and so will any application that you start from that window.</span></span> <span data-ttu-id="ba91f-122">若要在用户级别设置环境变量，请右键单击 **我的电脑**，依次单击 " **属性**"、" **高级** " 选项卡、" **环境变量**"，然后将变量添加到 " **用户变量** " 列表。</span><span class="sxs-lookup"><span data-stu-id="ba91f-122">To set environment variables at the user level, right-click **My Computer**, click **Properties**, click the **Advanced** tab, click **Environment Variables**, and add the variables to the **User variables** list.</span></span>  
  
- <span data-ttu-id="ba91f-123">如果在计算机级别设置变量，它们将应用于在该计算机上启动的所有应用程序。</span><span class="sxs-lookup"><span data-stu-id="ba91f-123">If you set the variables at the computer level, they will apply to all applications that are started on that computer.</span></span> <span data-ttu-id="ba91f-124">在该计算机上打开的“命令提示符”窗口将具有这些环境设置，从该窗口中启动的任何应用程序也将如此。</span><span class="sxs-lookup"><span data-stu-id="ba91f-124">A Command Prompt window that you open on that computer will have these environment settings, and so will any application that you start from that window.</span></span> <span data-ttu-id="ba91f-125">这表示该计算机上的每个托管进程都将通过你的探查器启动。</span><span class="sxs-lookup"><span data-stu-id="ba91f-125">This means that every managed process on that computer will start with your profiler.</span></span> <span data-ttu-id="ba91f-126">若要在计算机级别设置环境变量，请右键单击 **我的电脑**，依次单击 " **属性**"、" **高级** " 选项卡、" **环境变量**" 和 " **系统变量** " 列表中的变量，然后重新启动计算机。</span><span class="sxs-lookup"><span data-stu-id="ba91f-126">To set environment variables at the computer level, right-click **My Computer**, click **Properties**, click the **Advanced** tab, click **Environment Variables**, add the variables to the **System variables** list, and then restart your computer.</span></span> <span data-ttu-id="ba91f-127">重启后，变量将在系统范围内可用。</span><span class="sxs-lookup"><span data-stu-id="ba91f-127">After restarting, the variables will be available system-wide.</span></span>  
  
 <span data-ttu-id="ba91f-128">如果要分析 Windows 服务，必须在设置环境变量并注册探查器 DLL 之后重启计算机。</span><span class="sxs-lookup"><span data-stu-id="ba91f-128">If you are profiling a Windows Service, you must restart your computer after you set the environment variables and register the profiler DLL.</span></span> <span data-ttu-id="ba91f-129">有关这些注意事项的详细信息，请参阅 [分析 Windows 服务](#windows_service)部分。</span><span class="sxs-lookup"><span data-stu-id="ba91f-129">For more information about these considerations, see the section [Profiling a Windows Service](#windows_service).</span></span>  
  
## <a name="additional-considerations"></a><span data-ttu-id="ba91f-130">其他注意事项</span><span class="sxs-lookup"><span data-stu-id="ba91f-130">Additional Considerations</span></span>  
  
- <span data-ttu-id="ba91f-131">探查器类实现 [ICorProfilerCallback](icorprofilercallback-interface.md) 和 [ICorProfilerCallback2](icorprofilercallback2-interface.md) 接口。</span><span class="sxs-lookup"><span data-stu-id="ba91f-131">The profiler class implements the [ICorProfilerCallback](icorprofilercallback-interface.md) and [ICorProfilerCallback2](icorprofilercallback2-interface.md) interfaces.</span></span> <span data-ttu-id="ba91f-132">在 .NET Framework 2.0 版中，探查器必须实现 `ICorProfilerCallback2`。</span><span class="sxs-lookup"><span data-stu-id="ba91f-132">In the .NET Framework version 2.0, a profiler must implement `ICorProfilerCallback2`.</span></span> <span data-ttu-id="ba91f-133">否则，将不会加载 `ICorProfilerCallback2`。</span><span class="sxs-lookup"><span data-stu-id="ba91f-133">If it does not, `ICorProfilerCallback2` will not be loaded.</span></span>  
  
- <span data-ttu-id="ba91f-134">在给定环境中一次只能由一个事件探查器分析进程。</span><span class="sxs-lookup"><span data-stu-id="ba91f-134">Only one profiler can profile a process at one time in a given environment.</span></span> <span data-ttu-id="ba91f-135">可以在不同环境中注册两个不同的探查器，但每个探查器必须分析单独的进程。</span><span class="sxs-lookup"><span data-stu-id="ba91f-135">You can register two different profilers in different environments, but each must profile separate processes.</span></span> <span data-ttu-id="ba91f-136">必须将探查器作为进程内 COM 服务器 DLL 实现，后者被映射到与正在被分析的进程相同的地址空间。</span><span class="sxs-lookup"><span data-stu-id="ba91f-136">The profiler must be implemented as an in-process COM server DLL, which is mapped into the same address space as the process that is being profiled.</span></span> <span data-ttu-id="ba91f-137">这表示探查器在进程内运行。</span><span class="sxs-lookup"><span data-stu-id="ba91f-137">This means that the profiler runs in-process.</span></span> <span data-ttu-id="ba91f-138">.NET Framework 不支持任何其他类型的 COM 服务器。</span><span class="sxs-lookup"><span data-stu-id="ba91f-138">The .NET Framework does not support any other type of COM server.</span></span> <span data-ttu-id="ba91f-139">例如，如果探查器要监视远程计算机上的应用程序，则它必须在每台计算机上实现收集器代理。</span><span class="sxs-lookup"><span data-stu-id="ba91f-139">For example, if a profiler wants to monitor applications from a remote computer, it must implement collector agents on each computer.</span></span> <span data-ttu-id="ba91f-140">这些代理将批处理结果，并将它们传递给中央数据收集计算机。</span><span class="sxs-lookup"><span data-stu-id="ba91f-140">These agents will batch results and communicate them to the central data collection computer.</span></span>  
  
- <span data-ttu-id="ba91f-141">由于探查器是在进程内实例化的 COM 对象，所以每个被分析的应用程序都将具有其自己的探查器副本。</span><span class="sxs-lookup"><span data-stu-id="ba91f-141">Because the profiler is a COM object that is instantiated in-process, each profiled application will have its own copy of the profiler.</span></span> <span data-ttu-id="ba91f-142">因此，单个探查器实例不一定要处理来自多个应用程序的数据。</span><span class="sxs-lookup"><span data-stu-id="ba91f-142">Therefore, a single profiler instance does not have to handle data from multiple applications.</span></span> <span data-ttu-id="ba91f-143">但是，必须向探查器的日志记录代码添加逻辑，以防日志文件从其他被分析的应用程序进行覆盖。</span><span class="sxs-lookup"><span data-stu-id="ba91f-143">However, you will have to add logic to the profiler's logging code to prevent log file overwrites from other profiled applications.</span></span>  
  
## <a name="initializing-the-profiler"></a><span data-ttu-id="ba91f-144">初始化探查器</span><span class="sxs-lookup"><span data-stu-id="ba91f-144">Initializing the Profiler</span></span>  

 <span data-ttu-id="ba91f-145">如果两次环境变量检查均通过，CLR 就会以与 COM `CoCreateInstance` 函数类似的方式创建探查器实例。</span><span class="sxs-lookup"><span data-stu-id="ba91f-145">When both environment variable checks pass, the CLR creates an instance of the profiler in a similar manner to the COM `CoCreateInstance` function.</span></span> <span data-ttu-id="ba91f-146">直接调用 `CoCreateInstance` 不会加载探查器。</span><span class="sxs-lookup"><span data-stu-id="ba91f-146">The profiler is not loaded through a direct call to `CoCreateInstance`.</span></span> <span data-ttu-id="ba91f-147">因此避免了调用 `CoInitialize`（需设置线程模型）。</span><span class="sxs-lookup"><span data-stu-id="ba91f-147">Therefore, a call to `CoInitialize`, which requires setting the threading model, is avoided.</span></span> <span data-ttu-id="ba91f-148">然后，CLR 将调用探查器中的 [ICorProfilerCallback：： Initialize](icorprofilercallback-initialize-method.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="ba91f-148">The CLR then calls the [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) method in the profiler.</span></span> <span data-ttu-id="ba91f-149">此方法的签名如下。</span><span class="sxs-lookup"><span data-stu-id="ba91f-149">The signature of this method is as follows.</span></span>  
  
```cpp  
HRESULT Initialize(IUnknown *pICorProfilerInfoUnk)  
```  
  
 <span data-ttu-id="ba91f-150">探查器必须查询 " `pICorProfilerInfoUnk` [ICorProfilerInfo](icorprofilerinfo-interface.md) " 或 " [ICorProfilerInfo2](icorprofilerinfo2-interface.md) " 接口指针并保存它，以便它可以在以后的分析期间请求详细信息。</span><span class="sxs-lookup"><span data-stu-id="ba91f-150">The profiler must query `pICorProfilerInfoUnk` for an [ICorProfilerInfo](icorprofilerinfo-interface.md) or [ICorProfilerInfo2](icorprofilerinfo2-interface.md) interface pointer and save it so that it can request more information later during profiling.</span></span>  
  
## <a name="setting-event-notifications"></a><span data-ttu-id="ba91f-151">设置事件通知</span><span class="sxs-lookup"><span data-stu-id="ba91f-151">Setting Event Notifications</span></span>  

 <span data-ttu-id="ba91f-152">然后，探查器调用 [ICorProfilerInfo：： SetEventMask](icorprofilerinfo-seteventmask-method.md) 方法来指定它感兴趣的通知的类别。</span><span class="sxs-lookup"><span data-stu-id="ba91f-152">The profiler then calls the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to specify which categories of notifications it is interested in.</span></span> <span data-ttu-id="ba91f-153">例如，如果探查器只关注函数进入和离开通知以及垃圾回收通知，它将指定以下内容。</span><span class="sxs-lookup"><span data-stu-id="ba91f-153">For example, if the profiler is interested only in function enter and leave notifications and garbage collection notifications, it specifies the following.</span></span>  
  
```cpp  
ICorProfilerInfo* pInfo;  
pICorProfilerInfoUnk->QueryInterface(IID_ICorProfilerInfo, (void**)&pInfo);  
pInfo->SetEventMask(COR_PRF_MONITOR_ENTERLEAVE | COR_PRF_MONITOR_GC)  
```  
  
 <span data-ttu-id="ba91f-154">通过以这种方式设置通知掩码，探查器可以限制它接收的通知。</span><span class="sxs-lookup"><span data-stu-id="ba91f-154">By setting the notifications mask in this manner, the profiler can limit which notifications it receives.</span></span> <span data-ttu-id="ba91f-155">此方法帮助用户构建简单探查器或具有特殊用途的探查器。</span><span class="sxs-lookup"><span data-stu-id="ba91f-155">This approach helps the user build a simple or special-purpose profiler.</span></span> <span data-ttu-id="ba91f-156">它还能减少发送探查器只会忽略的通知将浪费的 CPU 时间。</span><span class="sxs-lookup"><span data-stu-id="ba91f-156">It also reduces CPU time that would be wasted sending notifications that the profiler would just ignore.</span></span>  
  
 <span data-ttu-id="ba91f-157">某些探查器事件是不可变的。</span><span class="sxs-lookup"><span data-stu-id="ba91f-157">Certain profiler events are immutable.</span></span> <span data-ttu-id="ba91f-158">这表示，一旦在 `ICorProfilerCallback::Initialize` 回调中设置了这些事件，就不能将它们关闭，也不能打开新事件。</span><span class="sxs-lookup"><span data-stu-id="ba91f-158">This means that as soon as these events are set in the `ICorProfilerCallback::Initialize` callback, they cannot be turned off and new events cannot be turned on.</span></span> <span data-ttu-id="ba91f-159">试图更改不可变事件将导致 `ICorProfilerInfo::SetEventMask` 返回失败的 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="ba91f-159">Attempts to change an immutable event will result in `ICorProfilerInfo::SetEventMask` returning a failed HRESULT.</span></span>  
  
<a name="windows_service"></a>

## <a name="profiling-a-windows-service"></a><span data-ttu-id="ba91f-160">分析 Windows 服务</span><span class="sxs-lookup"><span data-stu-id="ba91f-160">Profiling a Windows Service</span></span>  

 <span data-ttu-id="ba91f-161">分析 Windows 服务与分析公共语言运行时应用程序相似。</span><span class="sxs-lookup"><span data-stu-id="ba91f-161">Profiling a Windows Service is like profiling a common language runtime application.</span></span> <span data-ttu-id="ba91f-162">两种分析操作都通过环境变量启用。</span><span class="sxs-lookup"><span data-stu-id="ba91f-162">Both profiling operations are enabled through environment variables.</span></span> <span data-ttu-id="ba91f-163">由于 Windows 服务已于操作系统启动时启动，本主题中之前所述的环境变量必须在系统启动前就已经存在并设置为所需的值。</span><span class="sxs-lookup"><span data-stu-id="ba91f-163">Because a Windows Service is started when the operating system starts, the environment variables discussed previously in this topic must already be present and set to the required values before the system starts.</span></span> <span data-ttu-id="ba91f-164">此外，必须已在系统上注册了分析 DLL。</span><span class="sxs-lookup"><span data-stu-id="ba91f-164">In addition, the profiling DLL must already be registered on the system.</span></span>  
  
 <span data-ttu-id="ba91f-165">设置 COR_ENABLE_PROFILING 和 COR_PROFILER 环境变量并注册探查器 DLL 后，应重启目标计算机，以便 Windows 服务能够检测这些更改。</span><span class="sxs-lookup"><span data-stu-id="ba91f-165">After you set the COR_ENABLE_PROFILING and COR_PROFILER environment variables and register the profiler DLL, you should restart the target computer so that the Windows Service can detect those changes.</span></span>  
  
 <span data-ttu-id="ba91f-166">请注意，这些更改将在整个系统范围内启用分析。</span><span class="sxs-lookup"><span data-stu-id="ba91f-166">Note that these changes will enable profiling on a system-wide basis.</span></span> <span data-ttu-id="ba91f-167">若要防止对随后运行的每个托管应用程序进行分析，应在重启目标计算机后删除系统环境变量。</span><span class="sxs-lookup"><span data-stu-id="ba91f-167">To prevent every managed application that subsequently runs from being profiled, you should delete the system environment variables after you restart the target computer.</span></span>  
  
 <span data-ttu-id="ba91f-168">此技术也会导致对每个 CLR 进程进行分析。</span><span class="sxs-lookup"><span data-stu-id="ba91f-168">This technique also leads to every CLR process getting profiled.</span></span> <span data-ttu-id="ba91f-169">探查器应将逻辑添加到它的 [ICorProfilerCallback：： Initialize](icorprofilercallback-initialize-method.md) 回调以检测当前进程是否感兴趣。</span><span class="sxs-lookup"><span data-stu-id="ba91f-169">The profiler should add logic to its [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback to detect whether the current process is of interest.</span></span> <span data-ttu-id="ba91f-170">如果不相关，探查器可使回调失败而不执行初始化。</span><span class="sxs-lookup"><span data-stu-id="ba91f-170">If it is not, the profiler can fail the callback without performing the initialization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba91f-171">请参阅</span><span class="sxs-lookup"><span data-stu-id="ba91f-171">See also</span></span>

- [<span data-ttu-id="ba91f-172">分析概述</span><span class="sxs-lookup"><span data-stu-id="ba91f-172">Profiling Overview</span></span>](profiling-overview.md)
