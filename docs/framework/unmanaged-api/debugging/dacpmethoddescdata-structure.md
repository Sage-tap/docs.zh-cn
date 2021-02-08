---
description: 了解详细信息： DacpMethodDescData 结构
title: DacpMethodDescData 结构
ms.date: 02/01/2019
api.name:
- DacpMethodDescData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpMethodDescData Structure
helpviewer.keywords:
- DacpMethodDescData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: fe5b09874b3f8e123cb2501fcb00e3351aa44757
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801457"
---
# <a name="dacpmethoddescdata-structure"></a><span data-ttu-id="5432c-103">DacpMethodDescData 结构</span><span class="sxs-lookup"><span data-stu-id="5432c-103">DacpMethodDescData Structure</span></span>

<span data-ttu-id="5432c-104">定义方法的运行时信息的传输缓冲区。</span><span class="sxs-lookup"><span data-stu-id="5432c-104">Defines a transport buffer for a method's runtime information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="5432c-105">语法</span><span class="sxs-lookup"><span data-stu-id="5432c-105">Syntax</span></span>

```cpp
struct DacpMethodDescData
{
    int             bHasNativeCode;
    int             bIsDynamic;
    unsigned short  wSlotNumber;
    CLRDATA_ADDRESS NativeCodeAddr;
    CLRDATA_ADDRESS data;
    CLRDATA_ADDRESS MethodDescPtr;
    CLRDATA_ADDRESS nativeCodeInfo;
    CLRDATA_ADDRESS moduleInfo;
    mdToken         MDToken;
    CLRDATA_ADDRESS payloadGC;
    CLRDATA_ADDRESS payloadGC2;
    CLRDATA_ADDRESS managedDynamicMethodObject;
    CLRDATA_ADDRESS requestedIP;
    DacpReJitData   rejitDataCurrent;
    DacpReJitData   rejitDataRequested;
    unsigned long   cJittedRejitVersions;
};
```

## <a name="members"></a><span data-ttu-id="5432c-106">成员</span><span class="sxs-lookup"><span data-stu-id="5432c-106">Members</span></span>

| <span data-ttu-id="5432c-107">成员</span><span class="sxs-lookup"><span data-stu-id="5432c-107">Member</span></span>                       | <span data-ttu-id="5432c-108">说明</span><span class="sxs-lookup"><span data-stu-id="5432c-108">Description</span></span>                                                                                     |
| ---------------------------- | ----------------------------------------------------------------------------------------------- |
| `bHasNativeCode`             | <span data-ttu-id="5432c-109">指示运行时是否具有可用于方法的给定实例化的本机代码。</span><span class="sxs-lookup"><span data-stu-id="5432c-109">Indicates if the runtime has native code available for the given instantiation of the method.</span></span> |
| `bIsDynamic`                 | <span data-ttu-id="5432c-110">指示是否通过轻型代码生成动态生成方法。</span><span class="sxs-lookup"><span data-stu-id="5432c-110">Indicates if the method is generated dynamically through lightweight code generation.</span></span>           |
| `wSlotNumber`                | <span data-ttu-id="5432c-111">方法表中的方法的槽号。</span><span class="sxs-lookup"><span data-stu-id="5432c-111">The method's slot number in the method table.</span></span>                                                   |
| `NativeCodeAddr`             | <span data-ttu-id="5432c-112">方法的初始本机地址。</span><span class="sxs-lookup"><span data-stu-id="5432c-112">The method's initial native address.</span></span>                                                            |
| `data`                       | <span data-ttu-id="5432c-113">指向运行时内部使用的缓冲区的指针。</span><span class="sxs-lookup"><span data-stu-id="5432c-113">Pointer to a buffer used internally by the runtime.</span></span>                                             |
| `MethodDescPtr`              | <span data-ttu-id="5432c-114">指向 `MethodDesc` 运行时中的的指针。</span><span class="sxs-lookup"><span data-stu-id="5432c-114">Pointer to the `MethodDesc` in the runtime.</span></span>                                                     |
| `nativeCodeInfo`             | <span data-ttu-id="5432c-115">指向由运行时内部用于跟踪方法的缓冲区的指针。</span><span class="sxs-lookup"><span data-stu-id="5432c-115">Pointer to a buffer used internally by the runtime to track methods.</span></span>                            |
| `moduleInfo`                 | <span data-ttu-id="5432c-116">指向由运行时内部用于模块信息的缓冲区的指针。</span><span class="sxs-lookup"><span data-stu-id="5432c-116">Pointer to a buffer used internally by the runtime for module information.</span></span>                      |
| `MDToken`                    | <span data-ttu-id="5432c-117">与给定方法关联的标记。</span><span class="sxs-lookup"><span data-stu-id="5432c-117">Token associated with the given method.</span></span>                                                         |
| `payloadGC`                  | <span data-ttu-id="5432c-118">指向运行时内部使用的垃圾回收缓冲区的指针。</span><span class="sxs-lookup"><span data-stu-id="5432c-118">Pointer to a garbage collection buffer used internally by the runtime.</span></span>                          |
| `payloadGC2`                 | <span data-ttu-id="5432c-119">指向运行时内部使用的垃圾回收缓冲区的指针。</span><span class="sxs-lookup"><span data-stu-id="5432c-119">Pointer to a garbage collection buffer used internally by the runtime.</span></span>                          |
| `managedDynamicMethodObject` | <span data-ttu-id="5432c-120">如果该方法是动态的，则运行时在内部使用此缓冲区进行信息跟踪。</span><span class="sxs-lookup"><span data-stu-id="5432c-120">If the method is dynamic, the runtime uses this buffer internally for information tracking.</span></span>     |
| `requestedIP`                | <span data-ttu-id="5432c-121">用于在给定本机代码地址时填充每个请求的结构。</span><span class="sxs-lookup"><span data-stu-id="5432c-121">Used to populate the structure per request when given a native code address.</span></span>                    |
| `rejitDataCurrent`           | <span data-ttu-id="5432c-122">有关该方法的最新检测版本的信息。</span><span class="sxs-lookup"><span data-stu-id="5432c-122">Information about the latest instrumented version of the method.</span></span>                                   |
| `rejitDataRequested`         | <span data-ttu-id="5432c-123">请求的本机地址的 Rejit 信息。</span><span class="sxs-lookup"><span data-stu-id="5432c-123">Rejit information for the requested native address.</span></span>                                             |
| `cJittedRejitVersions`       | <span data-ttu-id="5432c-124">方法已通过检测 rejitted 的次数。</span><span class="sxs-lookup"><span data-stu-id="5432c-124">Number of times the method has been rejitted through instrumentation.</span></span>                           |

## <a name="remarks"></a><span data-ttu-id="5432c-125">备注</span><span class="sxs-lookup"><span data-stu-id="5432c-125">Remarks</span></span>

<span data-ttu-id="5432c-126">此结构存在于运行时中，并且不会通过任何标头或库文件公开。</span><span class="sxs-lookup"><span data-stu-id="5432c-126">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="5432c-127">若要使用它，请定义上面指定的结构。</span><span class="sxs-lookup"><span data-stu-id="5432c-127">To use it, define the structure as specified above.</span></span>

## <a name="requirements"></a><span data-ttu-id="5432c-128">要求</span><span class="sxs-lookup"><span data-stu-id="5432c-128">Requirements</span></span>

<span data-ttu-id="5432c-129">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5432c-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="5432c-130">**标头：** 内容</span><span class="sxs-lookup"><span data-stu-id="5432c-130">**Header:** None</span></span>  
<span data-ttu-id="5432c-131">**库：** 内容</span><span class="sxs-lookup"><span data-stu-id="5432c-131">**Library:** None</span></span>  
<span data-ttu-id="5432c-132">**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5432c-132">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="5432c-133">请参阅</span><span class="sxs-lookup"><span data-stu-id="5432c-133">See also</span></span>

- [<span data-ttu-id="5432c-134">调试</span><span class="sxs-lookup"><span data-stu-id="5432c-134">Debugging</span></span>](index.md)
- [<span data-ttu-id="5432c-135">调试结构</span><span class="sxs-lookup"><span data-stu-id="5432c-135">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="5432c-136">常见数据类型</span><span class="sxs-lookup"><span data-stu-id="5432c-136">Common Data Types</span></span>](../common-data-types-unmanaged-api-reference.md)
