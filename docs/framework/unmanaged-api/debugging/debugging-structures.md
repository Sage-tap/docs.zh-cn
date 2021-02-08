---
description: 了解详细信息：调试结构
title: 调试结构
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged structures [.NET Framework], debugging
- debugging structures [.NET Framework]
- structures [.NET Framework debugging]
ms.assetid: 173ba2c2-ab34-49ae-b6a8-e5c49882bf05
ms.openlocfilehash: 2b3b9e3678b34a25f9bfa58fcf6913cfe95aa729
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791551"
---
# <a name="debugging-structures"></a><span data-ttu-id="e29c2-103">调试结构</span><span class="sxs-lookup"><span data-stu-id="e29c2-103">Debugging Structures</span></span>

<span data-ttu-id="e29c2-104">本节描述调试 API 使用的非托管结构。</span><span class="sxs-lookup"><span data-stu-id="e29c2-104">This section describes the unmanaged structures that the debugging API uses.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="e29c2-105">本节内容</span><span class="sxs-lookup"><span data-stu-id="e29c2-105">In This Section</span></span>

 <span data-ttu-id="e29c2-106">[CLRDATA_ADDRESS_RANGE 结构](clrdata-address-range-structure.md) 定义地址范围。</span><span class="sxs-lookup"><span data-stu-id="e29c2-106">[CLRDATA_ADDRESS_RANGE Structure](clrdata-address-range-structure.md) Defines an address range.</span></span>

 <span data-ttu-id="e29c2-107">[CLRDATA_IL_ADDRESS_MAP 结构](clrdata-il-address-map-structure.md) 定义用于寻址映射的 IL</span><span class="sxs-lookup"><span data-stu-id="e29c2-107">[CLRDATA_IL_ADDRESS_MAP Structure](clrdata-il-address-map-structure.md) Defines an IL to address mapping</span></span>

 <span data-ttu-id="e29c2-108">[CLR_DEBUGGING_VERSION 结构](clr-debugging-version-structure.md) 出于调试目的，定义公共语言运行时 (CLR) 的产品版本。</span><span class="sxs-lookup"><span data-stu-id="e29c2-108">[CLR_DEBUGGING_VERSION Structure](clr-debugging-version-structure.md) Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>

 <span data-ttu-id="e29c2-109">[CodeChunkInfo 结构](codechunkinfo-structure.md) 表示内存中的单个代码块。</span><span class="sxs-lookup"><span data-stu-id="e29c2-109">[CodeChunkInfo Structure](codechunkinfo-structure.md) Represents a single chunk of code in memory.</span></span>

 <span data-ttu-id="e29c2-110">[COR_ACTIVE_FUNCTION](cor-active-function-structure.md) 包含有关线程帧中当前处于活动状态的函数的信息。</span><span class="sxs-lookup"><span data-stu-id="e29c2-110">[COR_ACTIVE_FUNCTION](cor-active-function-structure.md) Contains information about the functions that are currently active in a thread's frames.</span></span>

 <span data-ttu-id="e29c2-111">[COR_ARRAY_LAYOUT 结构](cor-array-layout-structure.md) 提供有关内存中数组对象的布局的信息。</span><span class="sxs-lookup"><span data-stu-id="e29c2-111">[COR_ARRAY_LAYOUT Structure](cor-array-layout-structure.md) Provides information about the layout of an array object in memory.</span></span>

 <span data-ttu-id="e29c2-112">[COR_DEBUG_IL_TO_NATIVE_MAP](cor-debug-il-to-native-map-structure.md) 包含用于将 Microsoft 中间语言 (MSIL) 代码映射到本机代码的偏移量。</span><span class="sxs-lookup"><span data-stu-id="e29c2-112">[COR_DEBUG_IL_TO_NATIVE_MAP](cor-debug-il-to-native-map-structure.md) Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>

 <span data-ttu-id="e29c2-113">[COR_DEBUG_STEP_RANGE](cor-debug-step-range-structure.md) 包含一系列代码的偏移信息。</span><span class="sxs-lookup"><span data-stu-id="e29c2-113">[COR_DEBUG_STEP_RANGE](cor-debug-step-range-structure.md) Contains the offset information for a range of code.</span></span>

 <span data-ttu-id="e29c2-114">[COR_FIELD 结构](cor-field-structure.md) 提供有关对象中的字段的信息。</span><span class="sxs-lookup"><span data-stu-id="e29c2-114">[COR_FIELD Structure](cor-field-structure.md) Provides information about a field in an object.</span></span>

 <span data-ttu-id="e29c2-115">[COR_GC_REFERENCE 结构](cor-gc-reference-structure.md) 包含有关要进行垃圾回收的对象的信息。</span><span class="sxs-lookup"><span data-stu-id="e29c2-115">[COR_GC_REFERENCE Structure](cor-gc-reference-structure.md) Contains information about an object that is to be garbage-collected.</span></span>

 <span data-ttu-id="e29c2-116">[COR_HEAPINFO 结构](cor-heapinfo-structure.md) 提供有关垃圾回收堆的常规信息，包括是否可枚举。</span><span class="sxs-lookup"><span data-stu-id="e29c2-116">[COR_HEAPINFO Structure](cor-heapinfo-structure.md) Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>

 <span data-ttu-id="e29c2-117">[COR_HEAPOBJECT 结构](cor-heapobject-structure.md) 提供有关托管堆上的对象的信息。</span><span class="sxs-lookup"><span data-stu-id="e29c2-117">[COR_HEAPOBJECT Structure](cor-heapobject-structure.md) Provides information about an object on the managed heap.</span></span>

 <span data-ttu-id="e29c2-118">[COR_IL_MAP](cor-il-map-structure.md) 指定函数的相对偏移量中的更改。</span><span class="sxs-lookup"><span data-stu-id="e29c2-118">[COR_IL_MAP](cor-il-map-structure.md) Specifies changes in the relative offset of a function.</span></span>

 <span data-ttu-id="e29c2-119">[COR_SEGMENT 结构](cor-segment-structure.md) 包含有关托管堆中的内存区域的信息。</span><span class="sxs-lookup"><span data-stu-id="e29c2-119">[COR_SEGMENT Structure](cor-segment-structure.md) Contains information about a region of memory in the managed heap.</span></span>

 <span data-ttu-id="e29c2-120">[COR_TYPEID 结构](cor-typeid-structure.md) 包含一个类型标识符。</span><span class="sxs-lookup"><span data-stu-id="e29c2-120">[COR_TYPEID Structure](cor-typeid-structure.md) Contains a type identifier.</span></span>

 <span data-ttu-id="e29c2-121">[COR_TYPE_LAYOUT 结构](cor-type-layout-structure.md) 提供有关内存中对象的布局的信息。</span><span class="sxs-lookup"><span data-stu-id="e29c2-121">[COR_TYPE_LAYOUT Structure](cor-type-layout-structure.md) Provides information about the layout of an object in memory.</span></span>

 <span data-ttu-id="e29c2-122">[COR_VERSION](cor-version-structure.md) 存储公共语言运行时的由四个部分组成的标准版本号。</span><span class="sxs-lookup"><span data-stu-id="e29c2-122">[COR_VERSION](cor-version-structure.md) Stores the standard four-part version number of the common language runtime.</span></span>

 <span data-ttu-id="e29c2-123">[CorDebugBlockingObject 结构](cordebugblockingobject-structure.md) 定义一个对象，该对象阻止线程，以及线程被阻止的原因。</span><span class="sxs-lookup"><span data-stu-id="e29c2-123">[CorDebugBlockingObject Structure](cordebugblockingobject-structure.md) Defines an object that is blocking a thread and the reason why the thread is blocked.</span></span>

 <span data-ttu-id="e29c2-124">[CorDebugEHClause 结构](cordebugehclause-structure.md) 表示一种异常处理 (EH) 子句，适用于一段给定的中间语言 (IL) 。</span><span class="sxs-lookup"><span data-stu-id="e29c2-124">[CorDebugEHClause Structure](cordebugehclause-structure.md) Represents an exception handling (EH) clause for a given piece of intermediate language (IL).</span></span>

 <span data-ttu-id="e29c2-125">[CorDebugExceptionObjectStackFrame 结构](cordebugexceptionobjectstackframe-structure.md) 表示异常对象中的堆栈帧信息。</span><span class="sxs-lookup"><span data-stu-id="e29c2-125">[CorDebugExceptionObjectStackFrame Structure](cordebugexceptionobjectstackframe-structure.md) Represents stack frame information from an exception object.</span></span>

 <span data-ttu-id="e29c2-126">[CorDebugGuidToTypeMapping 结构](cordebugguidtotypemapping-structure.md) 将 Windows 运行时 GUID 映射到其对应的 [ICorDebugType](icordebugtype-interface.md) 对象。</span><span class="sxs-lookup"><span data-stu-id="e29c2-126">[CorDebugGuidToTypeMapping Structure](cordebugguidtotypemapping-structure.md) Maps a Windows Runtime GUID to its corresponding [ICorDebugType](icordebugtype-interface.md) object.</span></span>

 <span data-ttu-id="e29c2-127">[DacpGetModuleAddress 结构](dacpgetmoduleaddress-structure.md) 定义模块地址请求的容器。</span><span class="sxs-lookup"><span data-stu-id="e29c2-127">[DacpGetModuleAddress Structure](dacpgetmoduleaddress-structure.md) Defines the container for a module address request.</span></span>

 <span data-ttu-id="e29c2-128">[DacpMethodDescData 结构](dacpmethoddescdata-structure.md) 定义方法的运行时信息的传输缓冲区。</span><span class="sxs-lookup"><span data-stu-id="e29c2-128">[DacpMethodDescData Structure](dacpmethoddescdata-structure.md) Defines a transport buffer for a method's runtime information.</span></span>

 <span data-ttu-id="e29c2-129">[DacpModuleData 结构](dacpmoduledata-structure.md) 定义模块的运行时信息的传输缓冲区。</span><span class="sxs-lookup"><span data-stu-id="e29c2-129">[DacpModuleData Structure](dacpmoduledata-structure.md) Defines a transport buffer for a module's runtime information.</span></span>

 <span data-ttu-id="e29c2-130">[DacpReJitData 结构](dacprejitdata-structure.md) 定义有关给定探查器检测到的方法的基本信息。</span><span class="sxs-lookup"><span data-stu-id="e29c2-130">[DacpReJitData Structure](dacprejitdata-structure.md) Defines the basic information about a given profiler-instrumented method.</span></span>

 <span data-ttu-id="e29c2-131">[StackTrace_SimpleContext 结构](stacktrace-simplecontext-structure.md) 提供了一个简单的上下文，可以使用它代替完整的 `CONTEXT` 结构。</span><span class="sxs-lookup"><span data-stu-id="e29c2-131">[StackTrace_SimpleContext Structure](stacktrace-simplecontext-structure.md) Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>

## <a name="related-sections"></a><span data-ttu-id="e29c2-132">相关章节</span><span class="sxs-lookup"><span data-stu-id="e29c2-132">Related Sections</span></span>

 [<span data-ttu-id="e29c2-133">调试 Coclass</span><span class="sxs-lookup"><span data-stu-id="e29c2-133">Debugging Coclasses</span></span>](debugging-coclasses.md)

 [<span data-ttu-id="e29c2-134">调试接口</span><span class="sxs-lookup"><span data-stu-id="e29c2-134">Debugging Interfaces</span></span>](debugging-interfaces.md)

 [<span data-ttu-id="e29c2-135">调试全局静态函数</span><span class="sxs-lookup"><span data-stu-id="e29c2-135">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)

 [<span data-ttu-id="e29c2-136">调试枚举</span><span class="sxs-lookup"><span data-stu-id="e29c2-136">Debugging Enumerations</span></span>](debugging-enumerations.md)

 [<span data-ttu-id="e29c2-137">调试</span><span class="sxs-lookup"><span data-stu-id="e29c2-137">Debugging</span></span>](index.md)
