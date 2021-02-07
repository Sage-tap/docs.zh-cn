---
description: 了解详细信息：调试接口
title: 调试接口
ms.date: 02/07/2019
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
ms.openlocfilehash: 6e6cc07e200b9ecf6bf4039f4fd5fd69e27b6fda
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717961"
---
# <a name="debugging-interfaces"></a><span data-ttu-id="ad8f2-103">调试接口</span><span class="sxs-lookup"><span data-stu-id="ad8f2-103">Debugging Interfaces</span></span>

<span data-ttu-id="ad8f2-104">本节描述进行程序调试处理的非托管接口，所调试的程序在公共语言运行时 (CLR) 中执行。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-104">This section describes the unmanaged interfaces that handle the debugging of a program that is executing in the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ad8f2-105">本节内容</span><span class="sxs-lookup"><span data-stu-id="ad8f2-105">In This Section</span></span>  

 <span data-ttu-id="ad8f2-106">[ICLRDataEnumMemoryRegions 接口](iclrdataenummemoryregions-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-106">[ICLRDataEnumMemoryRegions Interface](iclrdataenummemoryregions-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-107">提供对由调用方指定的内存区域进行枚举的方法。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-107">Provides a method to enumerate regions of memory that are specified by callers.</span></span>  
  
 <span data-ttu-id="ad8f2-108">[ICLRDataEnumMemoryRegionsCallback 接口](iclrdataenummemoryregionscallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-108">[ICLRDataEnumMemoryRegionsCallback Interface](iclrdataenummemoryregionscallback-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-109">为 `EnumMemoryRegions` 提供一种回调方法，用于向调试器报告尝试枚举指定内存区域的结果。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-109">Provides a callback method for `EnumMemoryRegions` to report to the debugger, the result of an attempt to enumerate a specified region of memory.</span></span>  
  
 <span data-ttu-id="ad8f2-110">[ICLRDataTarget 接口](iclrdatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-110">[ICLRDataTarget Interface](iclrdatatarget-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-111">提供与目标 CLR 进程进行交互的方法。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-111">Provides methods for interaction with a target CLR process.</span></span>  
  
 <span data-ttu-id="ad8f2-112">[ICLRDataTarget2 接口](iclrdatatarget2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-112">[ICLRDataTarget2 Interface](iclrdatatarget2-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-113">数据访问服务层在目标进程中操作虚拟内存区域时所用的 `ICLRDataTarget` 的子类。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-113">A subclass of `ICLRDataTarget` that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
 <span data-ttu-id="ad8f2-114">[ICLRDataTarget3 接口](iclrdatatarget3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-114">[ICLRDataTarget3 Interface](iclrdatatarget3-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-115">提供对异常信息的访问的 [ICLRDataTarget2](iclrdatatarget2-interface.md) 的子类。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-115">A subclass of [ICLRDataTarget2](iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
 <span data-ttu-id="ad8f2-116">[ICLRDebugging 接口](iclrdebugging-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-116">[ICLRDebugging Interface](iclrdebugging-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-117">提供一些方法，用于处理模块的加载和卸载以进行调试。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-117">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
 <span data-ttu-id="ad8f2-118">[ICLRDebuggingLibraryProvider 接口](iclrdebugginglibraryprovider-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-118">[ICLRDebuggingLibraryProvider Interface](iclrdebugginglibraryprovider-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-119">包括 [ProvideLibrary 方法](iclrdebugginglibraryprovider-providelibrary-method.md) 方法，该方法可获取一个库提供程序回调接口，该接口允许根据需要定位和加载特定于公共语言运行时版本的调试库。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-119">Includes the [ProvideLibrary Method](iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
 <span data-ttu-id="ad8f2-120">[ICLRMetadataLocator 接口](iclrmetadatalocator-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-120">[ICLRMetadataLocator Interface](iclrmetadatalocator-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-121">数据访问服务层用于在目标进程中定位程序集的元数据的接口。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-121">Interface used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
 <span data-ttu-id="ad8f2-122">[ICorDebug 接口](icordebug-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-122">[ICorDebug Interface](icordebug-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-123">提供允许开发人员在 CLR 环境中调试应用程序的方法。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-123">Provides methods that allow developers to debug applications in the CLR environment.</span></span>  
  
 <span data-ttu-id="ad8f2-124">[ICorDebugAppDomain 接口](icordebugappdomain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-124">[ICorDebugAppDomain Interface](icordebugappdomain-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-125">提供用于调试应用程序域的方法。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-125">Provides methods for debugging application domains.</span></span>  
  
 <span data-ttu-id="ad8f2-126">[ICorDebugAppDomain2 接口](icordebugappdomain2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-126">[ICorDebugAppDomain2 Interface](icordebugappdomain2-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-127">提供处理数组、指针、函数指针和 ByRef 类型的方法。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-127">Provides methods to work with arrays, pointers, function pointers, and ByRef types.</span></span> <span data-ttu-id="ad8f2-128">此接口是 `ICorDebugAppDomain` 接口的扩展。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-128">This interface is an extension of the `ICorDebugAppDomain` interface.</span></span>  
  
 <span data-ttu-id="ad8f2-129">[ICorDebugAppDomain3 接口](icordebugappdomain3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-129">[ICorDebugAppDomain3 Interface](icordebugappdomain3-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-130">提供用于在应用程序域中使用 Windows 运行时类型的方法。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-130">Provides methods to work with the Windows Runtime types in an application domain.</span></span> <span data-ttu-id="ad8f2-131">此接口是 `ICorDebugAppDomain` 和 `ICorDebugAppDomain2` 接口的扩展。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-131">This interface is an extension of the `ICorDebugAppDomain` and `ICorDebugAppDomain2` interfaces.</span></span>  
  
 <span data-ttu-id="ad8f2-132">[ICorDebugAppDomain4 接口](icordebugappdomain4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-132">[ICorDebugAppDomain4 Interface](icordebugappdomain4-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-133">对 [ICorDebugAppDomain](icordebugappdomain-interface.md) 接口进行逻辑扩展，以从 COM 可调用包装器获取托管对象。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-133">Logically extends the [ICorDebugAppDomain](icordebugappdomain-interface.md) interface to get a managed object from a COM callable wrapper.</span></span>  
  
 <span data-ttu-id="ad8f2-134">[ICorDebugAppDomainEnum 接口](icordebugappdomainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-134">[ICorDebugAppDomainEnum Interface](icordebugappdomainenum-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-135">提供一种方法，此方法从枚举中的下一个位置开始，返回指定数目的 `ICorDebugAppDomain` 值。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-135">Provides a method that returns a specified number of `ICorDebugAppDomain` values starting at the next location in the enumeration.</span></span>  
  
 <span data-ttu-id="ad8f2-136">[ICorDebugArrayValue 接口](icordebugarrayvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-136">[ICorDebugArrayValue Interface](icordebugarrayvalue-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-137">表示一维或多维数组的 `ICorDebugHeapValue` 的子类。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-137">A subclass of `ICorDebugHeapValue` that represents a single-dimensional or multi-dimensional array.</span></span>  
  
 <span data-ttu-id="ad8f2-138">[ICorDebugAssembly 接口](icordebugassembly-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-138">[ICorDebugAssembly Interface](icordebugassembly-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-139">表示一个程序集。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-139">Represents an assembly.</span></span>  
  
 <span data-ttu-id="ad8f2-140">[ICorDebugAssembly2 接口](icordebugassembly2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-140">[ICorDebugAssembly2 Interface](icordebugassembly2-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-141">表示一个程序集。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-141">Represents an assembly.</span></span> <span data-ttu-id="ad8f2-142">此接口是 `ICorDebugAssembly` 接口的扩展。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-142">This interface is an extension of the `ICorDebugAssembly` interface.</span></span>  
  
 <span data-ttu-id="ad8f2-143">[ICorDebugAssembly3 接口](icordebugassembly3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-143">[ICorDebugAssembly3 Interface](icordebugassembly3-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-144">对 [ICorDebugAssembly](icordebugassembly-interface.md) 接口进行逻辑扩展，以便为容器程序集及其包含的程序集提供支持。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-144">Logically extends the [ICorDebugAssembly](icordebugassembly-interface.md) interface to provide support for container assemblies and their contained assemblies.</span></span> <span data-ttu-id="ad8f2-145">**仅在 .NET Native 上可用。**</span><span class="sxs-lookup"><span data-stu-id="ad8f2-145">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="ad8f2-146">[ICorDebugAssemblyEnum 接口](icordebugassemblyenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-146">[ICorDebugAssemblyEnum Interface](icordebugassemblyenum-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-147">实现 `ICorDebugEnum` 方法，并枚举 `ICorDebugAssembly` 数组。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-147">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugAssembly` arrays.</span></span>  
  
 <span data-ttu-id="ad8f2-148">[ICorDebugBlockingObjectEnum 接口](icordebugblockingobjectenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-148">[ICorDebugBlockingObjectEnum Interface](icordebugblockingobjectenum-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-149">为 [CorDebugBlockingObject](cordebugblockingobject-structure.md) 结构的列表提供枚举器。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-149">Provides an enumerator for a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>  
  
 <span data-ttu-id="ad8f2-150">[ICorDebugBoxValue 接口](icordebugboxvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-150">[ICorDebugBoxValue Interface](icordebugboxvalue-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-151">表示装箱的值类对象的 `ICorDebugHeapValue` 的子类。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-151">A subclass of `ICorDebugHeapValue` that represents a boxed value class object.</span></span>  
  
 <span data-ttu-id="ad8f2-152">[ICorDebugBreakpoint 接口](icordebugbreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-152">[ICorDebugBreakpoint Interface](icordebugbreakpoint-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-153">表示函数中的断点，或值的观察点。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-153">Represents a breakpoint in a function or a watch point on a value.</span></span>  
  
 <span data-ttu-id="ad8f2-154">[ICorDebugBreakpointEnum 接口](icordebugbreakpointenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-154">[ICorDebugBreakpointEnum Interface](icordebugbreakpointenum-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-155">实现 `ICorDebugEnum` 方法，并枚举 `ICorDebugBreakpoint` 数组。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-155">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugBreakpoint` arrays.</span></span>  
  
 <span data-ttu-id="ad8f2-156">[ICorDebugChain 接口](icordebugchain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-156">[ICorDebugChain Interface](icordebugchain-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-157">表示一个物理或逻辑调用堆栈段。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-157">Represents a segment of a physical or logical call stack.</span></span>  
  
 <span data-ttu-id="ad8f2-158">[ICorDebugChainEnum 接口](icordebugchainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-158">[ICorDebugChainEnum Interface](icordebugchainenum-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-159">实现 `ICorDebugEnum` 方法，并枚举 `ICorDebugChain` 数组。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-159">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugChain` arrays.</span></span>  
  
 <span data-ttu-id="ad8f2-160">[ICorDebugClass 接口](icordebugclass-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-160">[ICorDebugClass Interface](icordebugclass-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-161">表示基类型或复杂类型（即用户定义的类型）。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-161">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="ad8f2-162">如果该类型为泛型类型，则 `ICorDebugClass` 表示实例化的泛型类型。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-162">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
 <span data-ttu-id="ad8f2-163">[ICorDebugClass2 接口](icordebugclass2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-163">[ICorDebugClass2 Interface](icordebugclass2-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-164">表示泛型类或具有 <xref:System.Type> 类型的方法参数的类。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-164">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="ad8f2-165">此接口扩展了 `ICorDebugClass`。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-165">This interface extends `ICorDebugClass`.</span></span>  
  
 <span data-ttu-id="ad8f2-166">[ICorDebugCode 接口](icordebugcode-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-166">[ICorDebugCode Interface](icordebugcode-interface1.md)</span></span>\
 <span data-ttu-id="ad8f2-167">表示 Microsoft 中间语言 (MSIL) 代码段或本机代码段。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-167">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
 <span data-ttu-id="ad8f2-168">[ICorDebugCode2 接口](icordebugcode2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-168">[ICorDebugCode2 Interface](icordebugcode2-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-169">提供扩展 `ICorDebugCode` 的功能的方法。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-169">Provides methods that extend the capabilities of `ICorDebugCode`.</span></span>  
  
 <span data-ttu-id="ad8f2-170">[ICorDebugCode3 接口](icordebugcode3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-170">[ICorDebugCode3 Interface](icordebugcode3-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-171">提供扩展 [ICorDebugCode](icordebugcode-interface1.md) 和 [ICorDebugCode2](icordebugcode2-interface.md) 的方法，以提供有关托管返回值的信息。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-171">Provides a method that extends [ICorDebugCode](icordebugcode-interface1.md) and [ICorDebugCode2](icordebugcode2-interface.md) to provide information about a managed return value.</span></span>  
  
 <span data-ttu-id="ad8f2-172">[ICorDebugCode4 接口](icordebugcode4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-172">[ICorDebugCode4 Interface](icordebugcode4-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-173">提供一个方法，该方法使调试器可以枚举函数中的局部变量和参数。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-173">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
 <span data-ttu-id="ad8f2-174">[ICorDebugCodeEnum 接口](icordebugcodeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-174">[ICorDebugCodeEnum Interface](icordebugcodeenum-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-175">实现 `ICorDebugEnum` 方法，并枚举 `ICorDebugCode` 数组。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-175">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugCode` arrays.</span></span>  
  
 <span data-ttu-id="ad8f2-176">[ICorDebugComObjectValue 接口](icordebugcomobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-176">[ICorDebugComObjectValue Interface](icordebugcomobjectvalue-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-177">提供用来检索缓存的接口对象的方法。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-177">Provides methods to retrieve cached interface objects.</span></span>  
  
 <span data-ttu-id="ad8f2-178">[ICorDebugContext 接口](icordebugcontext-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-178">[ICorDebugContext Interface](icordebugcontext-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-179">表示一个上下文对象。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-179">Represents a context object.</span></span> <span data-ttu-id="ad8f2-180">此接口尚未实现。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-180">This interface has not been implemented yet.</span></span>  
  
 <span data-ttu-id="ad8f2-181">[ICorDebugController 接口](icordebugcontroller-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-181">[ICorDebugController Interface](icordebugcontroller-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-182">表示可以控制代码执行上下文的 <xref:System.Diagnostics.Process> 或 <xref:System.AppDomain> 范围。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-182">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
 <span data-ttu-id="ad8f2-183">[ICorDebugDataTarget 接口](icordebugdatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-183">[ICorDebugDataTarget Interface](icordebugdatatarget-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-184">提供一个回调接口，该接口可提供对特定目标进程的访问。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-184">Provides a callback interface that provides access to a particular target process.</span></span>  
  
 <span data-ttu-id="ad8f2-185">[ICorDebugDataTarget2 接口](icordebugdatatarget2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-185">[ICorDebugDataTarget2 Interface](icordebugdatatarget2-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-186">对 [ICorDebugDataTarget](icordebugdatatarget-interface.md) 接口进行逻辑扩展。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-186">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="ad8f2-187">**仅在 .NET Native 上可用。**</span><span class="sxs-lookup"><span data-stu-id="ad8f2-187">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="ad8f2-188">[ICorDebugDataTarget3 接口](icordebugdatatarget3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-188">[ICorDebugDataTarget3 Interface](icordebugdatatarget3-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-189">对 [ICorDebugDataTarget](icordebugdatatarget-interface.md) 接口进行逻辑扩展，以提供有关已加载模块的信息。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-189">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span> <span data-ttu-id="ad8f2-190">**仅在 .NET Native 上可用。**</span><span class="sxs-lookup"><span data-stu-id="ad8f2-190">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="ad8f2-191">[ICorDebugDebugEvent 接口](icordebugdebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-191">[ICorDebugDebugEvent Interface](icordebugdebugevent-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-192">定义所有 `ICorDebug` 调试事件派生的基接口。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-192">Defines the base interface from which all `ICorDebug` debug events derive.</span></span> <span data-ttu-id="ad8f2-193">**仅在 .NET Native 上可用。**</span><span class="sxs-lookup"><span data-stu-id="ad8f2-193">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="ad8f2-194">[ICorDebugEditAndContinueErrorInfo 接口](icordebugeditandcontinueerrorinfo-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-194">[ICorDebugEditAndContinueErrorInfo Interface](icordebugeditandcontinueerrorinfo-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-195">已过时。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-195">Obsolete.</span></span> <span data-ttu-id="ad8f2-196">不要使用此接口。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-196">Do not use this interface.</span></span>  
  
 <span data-ttu-id="ad8f2-197">[ICorDebugEditAndContinueSnapshot 接口](icordebugeditandcontinuesnapshot-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-197">[ICorDebugEditAndContinueSnapshot Interface](icordebugeditandcontinuesnapshot-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-198">已过时。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-198">Obsolete.</span></span> <span data-ttu-id="ad8f2-199">不要使用此接口。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-199">Do not use this interface.</span></span>  
  
 <span data-ttu-id="ad8f2-200">[ICorDebugEnum 接口](icordebugenum-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-200">[ICorDebugEnum Interface](icordebugenum-interface1.md)</span></span>\
 <span data-ttu-id="ad8f2-201">作为调试枚举器的抽象基接口。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-201">Serves as the abstract base interface for debugging enumerators.</span></span>  
  
 <span data-ttu-id="ad8f2-202">[ICorDebugErrorInfoEnum 接口](icordebugerrorinfoenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-202">[ICorDebugErrorInfoEnum Interface](icordebugerrorinfoenum-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-203">已过时。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-203">Obsolete.</span></span> <span data-ttu-id="ad8f2-204">不要使用此接口。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-204">Do not use this interface.</span></span>  
  
 <span data-ttu-id="ad8f2-205">[ICorDebugEval 接口](icordebugeval-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-205">[ICorDebugEval Interface](icordebugeval-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-206">提供使调试器能够在正在调试的代码的上下文中执行代码的方法。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-206">Provides methods to enable the debugger to execute code within the context of the code being debugged.</span></span>  
  
 <span data-ttu-id="ad8f2-207">[ICorDebugEval2 接口](icordebugeval2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-207">[ICorDebugEval2 Interface](icordebugeval2-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-208">扩展 `ICorDebugEval` 以对泛型类型提供支持。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-208">Extends `ICorDebugEval` to provide support for generic types.</span></span>  
  
 <span data-ttu-id="ad8f2-209">[ICorDebugExceptionDebugEvent 接口](icordebugexceptiondebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-209">[ICorDebugExceptionDebugEvent Interface](icordebugexceptiondebugevent-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-210">扩展 [ICorDebugDebugEvent](icordebugdebugevent-interface.md) 接口以支持异常事件。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-210">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support exception events.</span></span> <span data-ttu-id="ad8f2-211">**仅在 .NET Native 上可用。**</span><span class="sxs-lookup"><span data-stu-id="ad8f2-211">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="ad8f2-212">[ICorDebugExceptionObjectCallStackEnum 接口](icordebugexceptionobjectcallstackenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-212">[ICorDebugExceptionObjectCallStackEnum Interface](icordebugexceptionobjectcallstackenum-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-213">为嵌入在异常对象中的调用堆栈信息提供枚举器。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-213">Provides an enumerator for call stack information that is embedded in an exception object.</span></span>  
  
 <span data-ttu-id="ad8f2-214">[ICorDebugExceptionObjectValue 接口](icordebugexceptionobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-214">[ICorDebugExceptionObjectValue Interface](icordebugexceptionobjectvalue-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-215">扩展 [ICorDebugObjectValue](icordebugobjectvalue-interface.md) 接口以提供来自托管异常对象的堆栈跟踪信息。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-215">Extends the [ICorDebugObjectValue](icordebugobjectvalue-interface.md) interface to provide stack trace information from a managed exception object.</span></span>  
  
 <span data-ttu-id="ad8f2-216">[ICorDebugFrame 接口](icordebugframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-216">[ICorDebugFrame Interface](icordebugframe-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-217">表示当前堆栈上的帧。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-217">Represents a frame on the current stack.</span></span>  
  
 <span data-ttu-id="ad8f2-218">[ICorDebugFrameEnum 接口](icordebugframeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-218">[ICorDebugFrameEnum Interface](icordebugframeenum-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-219">实现 `ICorDebugEnum` 方法，并枚举 `ICorDebugFrame` 数组。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-219">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugFrame` arrays.</span></span>  
  
 <span data-ttu-id="ad8f2-220">[ICorDebugFunction 接口](icordebugfunction-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-220">[ICorDebugFunction Interface](icordebugfunction-interface1.md)</span></span>\
 <span data-ttu-id="ad8f2-221">表示一个托管函数或方法。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-221">Represents a managed function or method.</span></span>  
  
 <span data-ttu-id="ad8f2-222">[ICorDebugFunction2 接口](icordebugfunction2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-222">[ICorDebugFunction2 Interface](icordebugfunction2-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-223">对 `ICorDebugFunction` 进行逻辑扩展，以支持“仅我的代码”的单步执行调试。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-223">Logically extends `ICorDebugFunction` to provide support for Just My Code step-through debugging.</span></span>  
  
 <span data-ttu-id="ad8f2-224">[ICorDebugFunction3 接口](icordebugfunction3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-224">[ICorDebugFunction3 Interface](icordebugfunction3-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-225">对 [ICorDebugFunction](icordebugfunction-interface1.md) 接口进行逻辑扩展，以提供对 ReJIT 请求中的代码的访问。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-225">Logically extends the [ICorDebugFunction](icordebugfunction-interface1.md) interface to provide access to code from a ReJIT request.</span></span>  
  
 <span data-ttu-id="ad8f2-226">[ICorDebugFunctionBreakpoint 接口](icordebugfunctionbreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-226">[ICorDebugFunctionBreakpoint Interface](icordebugfunctionbreakpoint-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-227">扩展 `ICorDebugBreakpoint` 以支持函数中的断点。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-227">Extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
 <span data-ttu-id="ad8f2-228">[ICorDebugGCReferenceEnum 接口](icordebuggcreferenceenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-228">[ICorDebugGCReferenceEnum Interface](icordebuggcreferenceenum-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-229">提供针对将进行垃圾回收的对象的枚举器。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-229">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
 <span data-ttu-id="ad8f2-230">[ICorDebugGenericValue 接口](icordebuggenericvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-230">[ICorDebugGenericValue Interface](icordebuggenericvalue-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-231">应用于所有值的 `ICorDebugValue` 的子类。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-231">A subclass of `ICorDebugValue` that applies to all values.</span></span> <span data-ttu-id="ad8f2-232">此接口可为值提供 Get 和 Set 方法。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-232">This interface provides Get and Set methods for the value.</span></span>  
  
 <span data-ttu-id="ad8f2-233">[ICorDebugGuidToTypeEnum 接口](icordebugguidtotypeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-233">[ICorDebugGuidToTypeEnum Interface](icordebugguidtotypeenum-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-234">提供针对映射 GUID 的对象及其相应的 `ICorDebugType` 对象的枚举器。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-234">Provides an enumerator for an object that maps GUIDs and their corresponding `ICorDebugType` objects.</span></span>  
  
 <span data-ttu-id="ad8f2-235">[ICorDebugHandleValue 接口](icordebughandlevalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-235">[ICorDebugHandleValue Interface](icordebughandlevalue-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-236">`ICorDebugReferenceValue` 的一个子类，前者表示调试器已为其创建了垃圾回收句柄的引用值。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-236">A subclass of `ICorDebugReferenceValue` that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
 <span data-ttu-id="ad8f2-237">[ICorDebugHeapEnum 接口](icordebugheapenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-237">[ICorDebugHeapEnum Interface](icordebugheapenum-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-238">提供针对托管堆上的对象的枚举器。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-238">Provides an enumerator for objects on the managed heap.</span></span>  
  
 <span data-ttu-id="ad8f2-239">[ICorDebugHeapSegmentEnum 接口](icordebugheapsegmentenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-239">[ICorDebugHeapSegmentEnum Interface](icordebugheapsegmentenum-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-240">提供针对托管堆的内存区域的枚举器。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-240">Provides an enumerator for the memory regions of the managed heap.</span></span>  
  
 <span data-ttu-id="ad8f2-241">[ICorDebugHeapValue 接口](icordebugheapvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-241">[ICorDebugHeapValue Interface](icordebugheapvalue-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-242">表示 CLR 垃圾回收器已收集的对象的 `ICorDebugValue` 的子类。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-242">A subclass of `ICorDebugValue` that represents an object that has been collected by the CLR garbage collector.</span></span>  
  
 <span data-ttu-id="ad8f2-243">[ICorDebugHeapValue2 接口](icordebugheapvalue2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-243">[ICorDebugHeapValue2 Interface](icordebugheapvalue2-interface1.md)</span></span>\
 <span data-ttu-id="ad8f2-244">对运行时句柄提供支持的 `ICorDebugHeapValue` 的扩展。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-244">An extension of `ICorDebugHeapValue` that provides support for runtime handles.</span></span>  
  
 <span data-ttu-id="ad8f2-245">[ICorDebugHeapValue3 接口](icordebugheapvalue3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-245">[ICorDebugHeapValue3 Interface](icordebugheapvalue3-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-246">公开对象的监视器锁属性。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-246">Exposes the monitor lock properties of objects.</span></span>  
  
 <span data-ttu-id="ad8f2-247">[ICorDebugILCode 接口](icordebugilcode-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-247">[ICorDebugILCode Interface](icordebugilcode-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-248">表示中间语言 (IL) 代码段。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-248">Represents a segment of intermediate language (IL) code.</span></span>  
  
 <span data-ttu-id="ad8f2-249">[ICorDebugILCode2 接口](icordebugilcode2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-249">[ICorDebugILCode2 Interface](icordebugilcode2-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-250">对 [ICorDebugILCode](icordebugilcode-interface.md) 接口进行逻辑扩展，以提供返回函数的局部变量签名的标记的方法，并将探查器检测到的中间语言 (il) 偏移量映射到原始方法的 il 偏移量。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-250">Logically extends the [ICorDebugILCode](icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
 <span data-ttu-id="ad8f2-251">[ICorDebugILFrame 接口](icordebugilframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-251">[ICorDebugILFrame Interface](icordebugilframe-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-252">表示 MSIL 代码的堆栈帧。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-252">Represents a stack frame of MSIL code.</span></span>  
  
 <span data-ttu-id="ad8f2-253">[ICorDebugILFrame2 接口](icordebugilframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-253">[ICorDebugILFrame2 Interface](icordebugilframe2-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-254">`ICorDebugILFrame` 的逻辑扩展。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-254">A logical extension of `ICorDebugILFrame`.</span></span>  
  
 <span data-ttu-id="ad8f2-255">[ICorDebugILFrame3 接口](icordebugilframe3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-255">[ICorDebugILFrame3 Interface](icordebugilframe3-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-256">提供用于封装函数的返回值的方法。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-256">Provides a method that encapsulates the return value of a function.</span></span>  
  
 <span data-ttu-id="ad8f2-257">[ICorDebugILFrame4 接口](icordebugilframe4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-257">[ICorDebugILFrame4 Interface](icordebugilframe4-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-258">提供使你能够访问中间语言 (IL) 代码的堆栈帧中的局部变量和代码的方法。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-258">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="ad8f2-259">一个用于指定调试器是否可以访问在探查器 ReJIT 检测中添加的变量和代码的参数。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-259">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
 <span data-ttu-id="ad8f2-260">[ICorDebugInstanceFieldSymbol 接口](icordebuginstancefieldsymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-260">[ICorDebugInstanceFieldSymbol Interface](icordebuginstancefieldsymbol-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-261">表示某一实例字段的调试符号信息。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-261">Represents the debug symbol information for an instance field.</span></span> <span data-ttu-id="ad8f2-262">**仅在 .NET Native 上可用。**</span><span class="sxs-lookup"><span data-stu-id="ad8f2-262">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="ad8f2-263">[ICorDebugInternalFrame 接口](icordebuginternalframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-263">[ICorDebugInternalFrame Interface](icordebuginternalframe-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-264">标识调试器的帧类型。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-264">Identifies frame types for the debugger.</span></span>  
  
 <span data-ttu-id="ad8f2-265">[ICorDebugInternalFrame2 接口](icordebuginternalframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-265">[ICorDebugInternalFrame2 Interface](icordebuginternalframe2-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-266">提供有关内部帧的信息，包括堆栈地址和相对于 [ICorDebugFrame](icordebugframe-interface.md) 对象的位置。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-266">Provides information about internal frames, including stack address and position in relation to [ICorDebugFrame](icordebugframe-interface.md) objects.</span></span>  
  
 <span data-ttu-id="ad8f2-267">[ICorDebugLoadedModule 接口](icordebugloadedmodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-267">[ICorDebugLoadedModule Interface](icordebugloadedmodule-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-268">提供有关已加载模块的信息。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-268">Provides information about a loaded module.</span></span> <span data-ttu-id="ad8f2-269">**仅在 .NET Native 上可用。**</span><span class="sxs-lookup"><span data-stu-id="ad8f2-269">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="ad8f2-270">[ICorDebugManagedCallback 接口](icordebugmanagedcallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-270">[ICorDebugManagedCallback Interface](icordebugmanagedcallback-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-271">提供用于处理调试器回调的方法。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-271">Provides methods to process debugger callbacks.</span></span>  
  
 <span data-ttu-id="ad8f2-272">[ICorDebugManagedCallback2 接口](icordebugmanagedcallback2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-272">[ICorDebugManagedCallback2 Interface](icordebugmanagedcallback2-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-273">提供支持调试器异常处理和托管调试助手 (MDA) 的方法。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-273">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="ad8f2-274">`ICorDebugManagedCallback2` 是 `ICorDebugManagedCallback` 的逻辑扩展。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-274">`ICorDebugManagedCallback2` is a logical extension of `ICorDebugManagedCallback`.</span></span>  
  
 <span data-ttu-id="ad8f2-275">[ICorDebugManagedCallback3 接口](icordebugmanagedcallback3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-275">[ICorDebugManagedCallback3 Interface](icordebugmanagedcallback3-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-276">提供一个回调方法，该方法指示已发出启用的自定义调试器通知。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-276">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
 <span data-ttu-id="ad8f2-277">[ICorDebugMDA 接口](icordebugmda-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-277">[ICorDebugMDA Interface](icordebugmda-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-278">表示托管调试助手 (MDA) 消息。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-278">Represents a managed debugging assistant (MDA) message.</span></span>  
  
 <span data-ttu-id="ad8f2-279">[ICorDebugMemoryBuffer 接口](icordebugmemorybuffer-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-279">[ICorDebugMemoryBuffer Interface](icordebugmemorybuffer-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-280">表示内存中缓冲区。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-280">Represents an in-memory buffer.</span></span> <span data-ttu-id="ad8f2-281">**仅在 .NET Native 上可用。**</span><span class="sxs-lookup"><span data-stu-id="ad8f2-281">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="ad8f2-282">[ICorDebugMergedAssemblyRecord 接口](icordebugmergedassemblyrecord-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-282">[ICorDebugMergedAssemblyRecord Interface](icordebugmergedassemblyrecord-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-283">提供有关合并的程序集的信息。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-283">Provides information about a merged assembly.</span></span> <span data-ttu-id="ad8f2-284">**仅在 .NET Native 上可用。**</span><span class="sxs-lookup"><span data-stu-id="ad8f2-284">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="ad8f2-285">[ICorDebugMetaDataLocator 接口](icordebugmetadatalocator-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-285">[ICorDebugMetaDataLocator Interface](icordebugmetadatalocator-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-286">向调试器提供元数据信息。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-286">Provides metadata information to the debugger.</span></span>  
  
 <span data-ttu-id="ad8f2-287">[ICorDebugModule 接口](icordebugmodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-287">[ICorDebugModule Interface](icordebugmodule-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-288">表示 CLR 模块，它是可执行文件或动态链接库 (DLL)。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-288">Represents a CLR module, which is either an executable or a dynamic-link library (DLL).</span></span>  
  
 <span data-ttu-id="ad8f2-289">[ICorDebugModule2 接口](icordebugmodule2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-289">[ICorDebugModule2 Interface](icordebugmodule2-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-290">用作 `ICorDebugModule` 的逻辑扩展。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-290">Serves as a logical extension to `ICorDebugModule`.</span></span>  
  
 <span data-ttu-id="ad8f2-291">[ICorDebugModule3 接口](icordebugmodule3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-291">[ICorDebugModule3 Interface](icordebugmodule3-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-292">为动态模块创建符号读取器。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-292">Creates a symbol reader for a dynamic module.</span></span>  
  
 <span data-ttu-id="ad8f2-293">[ICorDebugModuleBreakpoint 接口](icordebugmodulebreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-293">[ICorDebugModuleBreakpoint Interface](icordebugmodulebreakpoint-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-294">扩展 `ICorDebugBreakpoint` 以提供对特定模块的访问。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-294">Extends `ICorDebugBreakpoint` to provide access to specific modules.</span></span>  
  
 <span data-ttu-id="ad8f2-295">[ICorDebugModuleDebugEvent 接口](icordebugmoduledebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-295">[ICorDebugModuleDebugEvent Interface](icordebugmoduledebugevent-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-296">扩展 [ICorDebugDebugEvent](icordebugdebugevent-interface.md) 接口以支持模块级事件。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-296">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support module-level events.</span></span> <span data-ttu-id="ad8f2-297">**仅在 .NET Native 上可用。**</span><span class="sxs-lookup"><span data-stu-id="ad8f2-297">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="ad8f2-298">[ICorDebugModuleEnum 接口](icordebugmoduleenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-298">[ICorDebugModuleEnum Interface](icordebugmoduleenum-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-299">实现 `ICorDebugEnum` 方法，并枚举 `ICorDebugModule` 数组。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-299">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugModule` arrays.</span></span>  
  
 <span data-ttu-id="ad8f2-300">[ICorDebugMutableDataTarget 接口](icordebugmutabledatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-300">[ICorDebugMutableDataTarget Interface](icordebugmutabledatatarget-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-301">扩展 [ICorDebugDataTarget](icordebugdatatarget-interface.md) 接口以支持可变数据目标。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-301">Extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
 <span data-ttu-id="ad8f2-302">[ICorDebugNativeFrame 接口](icordebugnativeframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-302">[ICorDebugNativeFrame Interface](icordebugnativeframe-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-303">用于本机帧的 `ICorDebugFrame` 的专用实现。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-303">A specialized implementation of `ICorDebugFrame` used for native frames.</span></span>  
  
 <span data-ttu-id="ad8f2-304">[ICorDebugNativeFrame2 接口](icordebugnativeframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-304">[ICorDebugNativeFrame2 Interface](icordebugnativeframe2-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-305">提供用于测试子帧与父帧关系的方法。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-305">Provides methods that test for child and parent frame relationships.</span></span>  
  
 <span data-ttu-id="ad8f2-306">[ICorDebugObjectEnum 接口](icordebugobjectenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-306">[ICorDebugObjectEnum Interface](icordebugobjectenum-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-307">实现 `ICorDebugEnum` 方法，并通过对象数组的相对虚拟地址 (RVA) 对其进行枚举。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-307">Implements `ICorDebugEnum` methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
 <span data-ttu-id="ad8f2-308">[ICorDebugObjectValue 接口](icordebugobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-308">[ICorDebugObjectValue Interface](icordebugobjectvalue-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-309">表示包含对象的值的 `ICorDebugValue` 的子类。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-309">A subclass of `ICorDebugValue` that represents a value that contains an object.</span></span>  
  
 <span data-ttu-id="ad8f2-310">[ICorDebugObjectValue2 接口](icordebugobjectvalue2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-310">[ICorDebugObjectValue2 Interface](icordebugobjectvalue2-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-311">扩展 `ICorDebugObjectValue` 以支持继承和重写。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-311">Extends `ICorDebugObjectValue` to support inheritance and overrides.</span></span>  
  
 <span data-ttu-id="ad8f2-312">[ICorDebugProcess 接口](icordebugprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-312">[ICorDebugProcess Interface](icordebugprocess-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-313">表示正在执行托管代码的进程。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-313">Represents a process that is executing managed code.</span></span>  
  
 <span data-ttu-id="ad8f2-314">[ICorDebugProcess2 接口](icordebugprocess2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-314">[ICorDebugProcess2 Interface](icordebugprocess2-interface1.md)</span></span>\
 <span data-ttu-id="ad8f2-315">`ICorDebugProcess` 的逻辑扩展。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-315">A logical extension of `ICorDebugProcess`.</span></span>  
  
 <span data-ttu-id="ad8f2-316">[ICorDebugProcess3 接口](icordebugprocess3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-316">[ICorDebugProcess3 Interface](icordebugprocess3-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-317">控制自定义调试器通知。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-317">Controls custom debugger notifications.</span></span>

 <span data-ttu-id="ad8f2-318">[ICorDebugProcess4 接口](icordebugprocess4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-318">[ICorDebugProcess4 Interface](icordebugprocess4-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-319">为进程外执行控制提供支持。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-319">Provides support for out of process execution control.</span></span>
  
 <span data-ttu-id="ad8f2-320">[ICorDebugProcess5 接口](icordebugprocess5-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-320">[ICorDebugProcess5 Interface](icordebugprocess5-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-321">扩展 [ICorDebugProcess](icordebugprocess-interface.md) 接口以支持对托管堆的访问，以提供有关托管对象的垃圾回收的信息，以及确定调试器是否从应用程序的本地本机映像缓存中加载图像。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-321">Extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application's local native image cache.</span></span>  
  
 <span data-ttu-id="ad8f2-322">[ICorDebugProcess6 接口](icordebugprocess6-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-322">[ICorDebugProcess6 Interface](icordebugprocess6-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-323">对 [ICorDebugProcess](icordebugprocess-interface.md) 接口进行逻辑扩展，以启用一些功能，如对以本机异常调试事件和虚拟模块拆分方式编码的托管调试事件进行解码。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-323">Logically extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span> <span data-ttu-id="ad8f2-324">**仅在 .NET Native 上可用。**</span><span class="sxs-lookup"><span data-stu-id="ad8f2-324">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="ad8f2-325">[ICorDebugProcess7 接口](icordebugprocess7-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-325">[ICorDebugProcess7 Interface](icordebugprocess7-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-326">提供了一种方法，用于配置调试器以处理目标进程中的内存中元数据更新。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-326">Provides a method that configures the debugger to handle in-memory metadata updates in the target process.</span></span>  
  
 <span data-ttu-id="ad8f2-327">[ICorDebugProcess8 接口](icordebugprocess8-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-327">[ICorDebugProcess8 Interface](icordebugprocess8-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-328">对 [ICorDebugProcess](icordebugprocess-interface.md) 接口进行逻辑扩展，以启用或禁用某些类型的 [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) 异常回调。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-328">Logically extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to enable or disable certain types of [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
 <span data-ttu-id="ad8f2-329">[ICorDebugProcessEnum 接口](icordebugprocessenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-329">[ICorDebugProcessEnum Interface](icordebugprocessenum-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-330">实现 `ICorDebugEnum` 方法，并枚举 `ICorDebugProcess` 数组。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-330">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugProcess` arrays.</span></span>  
  
 <span data-ttu-id="ad8f2-331">[ICorDebugReferenceValue 接口](icordebugreferencevalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-331">[ICorDebugReferenceValue Interface](icordebugreferencevalue-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-332">`ICorDebugValue` 的子类，它支持引用类型。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-332">A subclass of `ICorDebugValue` that supports reference types.</span></span>  
  
 <span data-ttu-id="ad8f2-333">[ICorDebugRegisterSet 接口](icordebugregisterset-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-333">[ICorDebugRegisterSet Interface](icordebugregisterset-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-334">表示在当前正在执行代码的计算机上可用的寄存器组。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-334">Represents the set of registers available on the machine that is currently executing code.</span></span>  
  
 <span data-ttu-id="ad8f2-335">[ICorDebugRegisterSet2 接口](icordebugregisterset2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-335">[ICorDebugRegisterSet2 Interface](icordebugregisterset2-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-336">为具有 64 个以上寄存器的硬件平台扩展 `ICorDebugRegisterSet` 的功能。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-336">Extends the capabilities of `ICorDebugRegisterSet` for hardware platforms that have more than 64 registers.</span></span>  
  
 <span data-ttu-id="ad8f2-337">[ICorDebugRemote 接口](icordebugremote-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-337">[ICorDebugRemote Interface](icordebugremote-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-338">提供启动托管调试器或将其附加到远程目标进程的能力。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-338">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
 <span data-ttu-id="ad8f2-339">[ICorDebugRemoteTarget 接口](icordebugremotetarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-339">[ICorDebugRemoteTarget Interface](icordebugremotetarget-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-340">提供使你能够在 CLR 环境中调试基于 Silverlight 的应用程序的方法。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-340">Provides methods that enable you to debug Silverlight-based applications in the CLR environment.</span></span>  
  
 <span data-ttu-id="ad8f2-341">[ICorDebugRuntimeUnwindableFrame 接口](icordebugruntimeunwindableframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-341">[ICorDebugRuntimeUnwindableFrame Interface](icordebugruntimeunwindableframe-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-342">提供对非托管方法的支持，这些方法需要公共语言运行时 (CLR) 来展开帧。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-342">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
 <span data-ttu-id="ad8f2-343">[ICorDebugStackWalk 接口](icordebugstackwalk-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-343">[ICorDebugStackWalk Interface](icordebugstackwalk-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-344">提供用于获取线程堆栈上的托管方法或帧的方法。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-344">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
 <span data-ttu-id="ad8f2-345">[ICorDebugStaticFieldSymbol 接口](icordebugstaticfieldsymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-345">[ICorDebugStaticFieldSymbol Interface](icordebugstaticfieldsymbol-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-346">表示某个静态字段的调试符号信息。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-346">Represents the debug symbol information for a static field.</span></span> <span data-ttu-id="ad8f2-347">**仅在 .NET Native 上可用。**</span><span class="sxs-lookup"><span data-stu-id="ad8f2-347">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="ad8f2-348">[ICorDebugStepper 接口](icordebugstepper-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-348">[ICorDebugStepper Interface](icordebugstepper-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-349">表示在代码执行过程中由调试器执行的一个步骤。此步骤作为命令颁发和完成之间的标识符使用，可以实现取消对某个步骤的执行。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-349">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
 <span data-ttu-id="ad8f2-350">[ICorDebugStepper2 接口](icordebugstepper2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-350">[ICorDebugStepper2 Interface](icordebugstepper2-interface1.md)</span></span>\
 <span data-ttu-id="ad8f2-351">提供对“仅我的代码”(JMC) 调试的支持。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-351">Provides support for Just My Code (JMC) debugging.</span></span>  
  
 <span data-ttu-id="ad8f2-352">[ICorDebugStepperEnum 接口](icordebugstepperenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-352">[ICorDebugStepperEnum Interface](icordebugstepperenum-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-353">实现 `ICorDebugEnum` 方法，并枚举 `ICorDebugStepper` 数组。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-353">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugStepper` arrays.</span></span>  
  
 <span data-ttu-id="ad8f2-354">[ICorDebugStringValue 接口](icordebugstringvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-354">[ICorDebugStringValue Interface](icordebugstringvalue-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-355">应用于字符串值的 `ICorDebugHeapValue` 的子类。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-355">A subclass of `ICorDebugHeapValue` that applies to string values.</span></span>  
  
 <span data-ttu-id="ad8f2-356">[ICorDebugSymbolProvider 接口](icordebugsymbolprovider-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-356">[ICorDebugSymbolProvider Interface](icordebugsymbolprovider-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-357">提供可用于检索调试符号信息的方法。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-357">Provides methods that can be used to retrieve debug symbol information.</span></span> <span data-ttu-id="ad8f2-358">**仅在 .NET Native 上可用。**</span><span class="sxs-lookup"><span data-stu-id="ad8f2-358">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="ad8f2-359">[ICorDebugSymbolProvider2 接口](icordebugsymbolprovider2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-359">[ICorDebugSymbolProvider2 Interface](icordebugsymbolprovider2-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-360">以逻辑方式扩展 [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) 接口以检索其他调试符号信息。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-360">Logically extends the [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span> <span data-ttu-id="ad8f2-361">**仅在 .NET Native 上可用。**</span><span class="sxs-lookup"><span data-stu-id="ad8f2-361">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="ad8f2-362">[ICorDebugThread 接口](icordebugthread-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-362">[ICorDebugThread Interface](icordebugthread-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-363">表示进程中的线程。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-363">Represents a thread in a process.</span></span> <span data-ttu-id="ad8f2-364">`ICorDebugThread` 实例的生存期与它表示的线程的生存期相同。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-364">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
 <span data-ttu-id="ad8f2-365">[ICorDebugThread2 接口](icordebugthread2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-365">[ICorDebugThread2 Interface](icordebugthread2-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-366">用作 `ICorDebugThread` 的逻辑扩展。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-366">Serves as a logical extension to `ICorDebugThread`.</span></span>  
  
 <span data-ttu-id="ad8f2-367">[ICorDebugThread3 接口](icordebugthread3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-367">[ICorDebugThread3 Interface](icordebugthread3-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-368">提供 [ICorDebugStackWalk](icordebugstackwalk-interface.md) 和相应接口的入口点。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-368">Provides the entry point to the [ICorDebugStackWalk](icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
 <span data-ttu-id="ad8f2-369">[ICorDebugThread4 接口](icordebugthread4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-369">[ICorDebugThread4 Interface](icordebugthread4-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-370">提供线程阻塞信息。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-370">Provides thread blocking information.</span></span>  
  
 <span data-ttu-id="ad8f2-371">[ICorDebugThreadEnum 接口](icordebugthreadenum-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-371">[ICorDebugThreadEnum Interface](icordebugthreadenum-interface1.md)</span></span>\
 <span data-ttu-id="ad8f2-372">实现 `ICorDebugEnum` 方法，并枚举 `ICorDebugThread` 数组。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-372">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugThread` arrays.</span></span>  
  
 <span data-ttu-id="ad8f2-373">[ICorDebugType 接口](icordebugtype-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-373">[ICorDebugType Interface](icordebugtype-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-374">表示基类型或复杂类型（即用户定义的类型）。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-374">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="ad8f2-375">如果该类型是泛型类型，则 `ICorDebugType` 表示未实例化的泛型类型。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-375">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
 <span data-ttu-id="ad8f2-376">[ICorDebugType2 接口](icordebugtype2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-376">[ICorDebugType2 Interface](icordebugtype2-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-377">扩展 [ICorDebugType](icordebugtype-interface.md) 接口以检索基类型或复杂 (用户定义的) 类型的类型标识符。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-377">Extends the [ICorDebugType](icordebugtype-interface.md) interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
 <span data-ttu-id="ad8f2-378">[ICorDebugTypeEnum 接口](icordebugtypeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-378">[ICorDebugTypeEnum Interface](icordebugtypeenum-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-379">实现 `ICorDebugEnum` 方法，并枚举 `ICorDebugType` 数组。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-379">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugType` arrays.</span></span>  
  
 <span data-ttu-id="ad8f2-380">[ICorDebugUnmanagedCallback 接口](icordebugunmanagedcallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-380">[ICorDebugUnmanagedCallback Interface](icordebugunmanagedcallback-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-381">提供与 CLR 没有直接关系的本机事件的通知。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-381">Provides notification of native events that are not directly related to the CLR.</span></span>  
  
 <span data-ttu-id="ad8f2-382">[ICorDebugValue](icordebugvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-382">[ICorDebugValue](icordebugvalue-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-383">表示正在调试的进程中的读取或写入值。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-383">Represents a read or write value in the process being debugged.</span></span>  
  
 <span data-ttu-id="ad8f2-384">[ICorDebugValue2](icordebugvalue2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-384">[ICorDebugValue2](icordebugvalue2-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-385">扩展 `ICorDebugValue` 以提供对 `ICorDebugType` 的支持。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-385">Extends `ICorDebugValue` to provide support for `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="ad8f2-386">[ICorDebugValue3 接口](icordebugvalue3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-386">[ICorDebugValue3 Interface](icordebugvalue3-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-387">扩展了 "ICorDebugValue" 和 "ICorDebugValue2" 接口，为大于 2 GB 的数组提供支持。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-387">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
 <span data-ttu-id="ad8f2-388">[ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-388">[ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-389">扩展 `ICorDebugBreakpoint` 以提供对特定值的访问。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-389">Extends `ICorDebugBreakpoint` to provide access to specific values.</span></span>  
  
 <span data-ttu-id="ad8f2-390">[ICorDebugValueEnum](icordebugvalueenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-390">[ICorDebugValueEnum](icordebugvalueenum-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-391">实现 `ICorDebugEnum` 方法，并枚举 `ICorDebugValue` 数组。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-391">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugValue` arrays.</span></span>  
  
 <span data-ttu-id="ad8f2-392">[ICorDebugVariableHome 接口](icordebugvariablehome-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-392">[ICorDebugVariableHome Interface](icordebugvariablehome-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-393">表示函数的局部变量或自变量。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-393">Represents a local variable or argument of a function.</span></span>  
  
 <span data-ttu-id="ad8f2-394">[ICorDebugVariableHomeEnum 接口](icordebugvariablehomeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-394">[ICorDebugVariableHomeEnum Interface](icordebugvariablehomeenum-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-395">提供对函数中的局部变量和参数的枚举器。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-395">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
 <span data-ttu-id="ad8f2-396">[ICorDebugVariableSymbol 接口](icordebugvariablesymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-396">[ICorDebugVariableSymbol Interface](icordebugvariablesymbol-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-397">检索变量的调试符号信息。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-397">Retrieves the debug symbol information for a variable.</span></span> <span data-ttu-id="ad8f2-398">**仅在 .NET Native 上可用。**</span><span class="sxs-lookup"><span data-stu-id="ad8f2-398">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="ad8f2-399">[ICorDebugVirtualUnwinder 接口](icordebugvirtualunwinder-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-399">[ICorDebugVirtualUnwinder Interface](icordebugvirtualunwinder-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-400">提供帮助堆栈展开的方法。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-400">Provides methods to help in stack unwinding.</span></span> <span data-ttu-id="ad8f2-401">**仅在 .NET Native 上可用。**</span><span class="sxs-lookup"><span data-stu-id="ad8f2-401">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="ad8f2-402">[ICorPublish 接口](icorpublish-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-402">[ICorPublish Interface](icorpublish-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-403">用作发布进程的常规接口。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-403">Serves as the general interface for the publishing processes.</span></span>  
  
 <span data-ttu-id="ad8f2-404">[ICorPublishAppDomain 接口](icorpublishappdomain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-404">[ICorPublishAppDomain Interface](icorpublishappdomain-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-405">表示并提供关于应用程序域的信息。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-405">Represents and provides information about an application domain.</span></span>  
  
 <span data-ttu-id="ad8f2-406">[ICorPublishAppDomainEnum 接口](icorpublishappdomainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-406">[ICorPublishAppDomainEnum Interface](icorpublishappdomainenum-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-407">提供遍历进程中当前存在的 `ICorPublishAppDomain` 对象的集合的方法。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-407">Provides methods that traverse a collection of `ICorPublishAppDomain` objects that currently exist within a process.</span></span>  
  
 <span data-ttu-id="ad8f2-408">[ICorPublishEnum 接口](icorpublishenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-408">[ICorPublishEnum Interface](icorpublishenum-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-409">用作发布枚举器的抽象基。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-409">Serves as the abstract base for publishing enumerators.</span></span>  
  
 <span data-ttu-id="ad8f2-410">[ICorPublishProcess 接口](icorpublishprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-410">[ICorPublishProcess Interface](icorpublishprocess-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-411">提供用于访问有关进程的信息的方法。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-411">Provides methods that access information about a process.</span></span>  
  
 <span data-ttu-id="ad8f2-412">[ICorPublishProcessEnum 接口](icorpublishprocessenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-412">[ICorPublishProcessEnum Interface](icorpublishprocessenum-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-413">提供遍历 `ICorPublishProcess` 对象的集合的方法。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-413">Provides methods that traverse a collection of `ICorPublishProcess` objects.</span></span>  

 <span data-ttu-id="ad8f2-414">[ISOSDacInterface 接口](isosdacinterface-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-414">[ISOSDacInterface Interface](isosdacinterface-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-415">提供用于访问中的数据的帮助器方法 `SOS` 。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-415">Provides helper methods to access data from `SOS`.</span></span>

 <span data-ttu-id="ad8f2-416">[IXCLRDataMethodDefinition 接口](ixclrdatamethoddefinition-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-416">[IXCLRDataMethodDefinition Interface](ixclrdatamethoddefinition-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-417">提供用于查询有关方法定义的信息的方法。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-417">Provides methods for querying information about a method definition.</span></span>

 <span data-ttu-id="ad8f2-418">[IXCLRDataMethodInstance 接口](ixclrdatamethodinstance-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-418">[IXCLRDataMethodInstance Interface](ixclrdatamethodinstance-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-419">提供用于查询有关方法实例的信息的方法。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-419">Provides methods for querying information about a method instance.</span></span>

 <span data-ttu-id="ad8f2-420">[IXCLRDataModule 接口](ixclrdatamodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-420">[IXCLRDataModule Interface](ixclrdatamodule-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-421">提供用于查询有关已加载模块的信息的方法。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-421">Provides methods for querying information about a loaded module.</span></span>

 <span data-ttu-id="ad8f2-422">[IXCLRDataProcess 接口](ixclrdataprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-422">[IXCLRDataProcess Interface](ixclrdataprocess-interface.md)</span></span>\
 <span data-ttu-id="ad8f2-423">提供用于查询有关进程的信息的方法。</span><span class="sxs-lookup"><span data-stu-id="ad8f2-423">Provides methods for querying information about a process.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="ad8f2-424">相关章节</span><span class="sxs-lookup"><span data-stu-id="ad8f2-424">Related Sections</span></span>  

 <span data-ttu-id="ad8f2-425">[调试组件类](debugging-coclasses.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-425">[Debugging Coclasses](debugging-coclasses.md)</span></span>\
 <span data-ttu-id="ad8f2-426">[调试全局静态函数](debugging-global-static-functions.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-426">[Debugging Global Static Functions](debugging-global-static-functions.md)</span></span>\
 <span data-ttu-id="ad8f2-427">[调试枚举](debugging-enumerations.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-427">[Debugging Enumerations](debugging-enumerations.md)</span></span>\
 <span data-ttu-id="ad8f2-428">[调试结构](debugging-structures.md)</span><span class="sxs-lookup"><span data-stu-id="ad8f2-428">[Debugging Structures](debugging-structures.md)</span></span>\
