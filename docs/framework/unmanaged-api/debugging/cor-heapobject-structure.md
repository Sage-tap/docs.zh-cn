---
description: 了解详细信息： COR_HEAPOBJECT 结构
title: COR_HEAPOBJECT 结构
ms.date: 03/30/2017
api_name:
- COR_HEAPOBJECT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_HEAPOBJECT
helpviewer_keywords:
- COR_HEAPOBJECT structure [.NET Framework debugging]
ms.assetid: a92fdf95-492b-49ae-a741-2186e5c1d7c5
topic_type:
- apiref
ms.openlocfilehash: f41e02e7c528063f4b7ed485cbadbabb4d3e5ca7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801795"
---
# <a name="cor_heapobject-structure"></a><span data-ttu-id="b5c48-103">COR_HEAPOBJECT 结构</span><span class="sxs-lookup"><span data-stu-id="b5c48-103">COR_HEAPOBJECT Structure</span></span>

<span data-ttu-id="b5c48-104">提供有关托管堆上的对象的信息。</span><span class="sxs-lookup"><span data-stu-id="b5c48-104">Provides information about an object on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5c48-105">语法</span><span class="sxs-lookup"><span data-stu-id="b5c48-105">Syntax</span></span>  
  
```cpp  
typedef struct _COR_HEAPOBJECT {  
    CORDB_ADDRESS address;
    ULONG64 size;
    COR_TYPEID type;
} COR_HEAPOBJECT;  
```  
  
## <a name="members"></a><span data-ttu-id="b5c48-106">成员</span><span class="sxs-lookup"><span data-stu-id="b5c48-106">Members</span></span>  
  
|<span data-ttu-id="b5c48-107">成员</span><span class="sxs-lookup"><span data-stu-id="b5c48-107">Member</span></span>|<span data-ttu-id="b5c48-108">说明</span><span class="sxs-lookup"><span data-stu-id="b5c48-108">Description</span></span>|  
|------------|-----------------|  
|`address`|<span data-ttu-id="b5c48-109">内存中的对象的地址。</span><span class="sxs-lookup"><span data-stu-id="b5c48-109">The address of the object in memory.</span></span>|  
|`size`|<span data-ttu-id="b5c48-110">对象的总大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="b5c48-110">The total size of the object, in bytes.</span></span>|  
|`type`|<span data-ttu-id="b5c48-111">表示对象类型的 [COR_TYPEID](cor-typeid-structure.md) 标记。</span><span class="sxs-lookup"><span data-stu-id="b5c48-111">A [COR_TYPEID](cor-typeid-structure.md) token that represents the type of the object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5c48-112">备注</span><span class="sxs-lookup"><span data-stu-id="b5c48-112">Remarks</span></span>  

 <span data-ttu-id="b5c48-113">`COR_HEAPOBJECT`可以通过枚举通过调用[ICorDebugProcess5：： EnumerateHeap](icordebugprocess5-enumerateheap-method.md)方法填充的[ICorDebugHeapEnum](icordebugheapenum-interface.md)接口对象来检索实例。</span><span class="sxs-lookup"><span data-stu-id="b5c48-113">`COR_HEAPOBJECT` instances can be retrieved by enumerating an [ICorDebugHeapEnum](icordebugheapenum-interface.md) interface object that is populated by calling the [ICorDebugProcess5::EnumerateHeap](icordebugprocess5-enumerateheap-method.md) method.</span></span>  
  
 <span data-ttu-id="b5c48-114">`COR_HEAPOBJECT`实例提供有关托管堆上的活动对象的信息，或有关对象的信息，该对象不是由任何对象的根，但垃圾回收器尚未收集。</span><span class="sxs-lookup"><span data-stu-id="b5c48-114">A `COR_HEAPOBJECT` instance provides information either about a live object on the managed heap, or about an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span>  
  
 <span data-ttu-id="b5c48-115">为了获得更好的性能，该 `COR_HEAPOBJECT.address` 字段是一个值，而不是 `CORDB_ADDRESS` 大部分调试 API 中使用的 ICorDebugValue 接口值。</span><span class="sxs-lookup"><span data-stu-id="b5c48-115">For better performance, the `COR_HEAPOBJECT.address` field is a `CORDB_ADDRESS` value rather than the ICorDebugValue interface value used in much of the debugging API.</span></span> <span data-ttu-id="b5c48-116">若要获取给定对象地址的 ICorDebugValue 对象，可以将 `CORDB_ADDRESS` 值传递给 [ICorDebugProcess5：： GetObject](icordebugprocess5-getobject-method.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="b5c48-116">To obtain an ICorDebugValue object for a given object address, you can pass the `CORDB_ADDRESS` value to the [ICorDebugProcess5::GetObject](icordebugprocess5-getobject-method.md) method.</span></span>  
  
 <span data-ttu-id="b5c48-117">为了获得更好的性能，该 `COR_HEAPOBJECT.type` 字段是一个值，而不是 `COR_TYPEID` 大部分调试 API 中使用的 ICorDebugType 接口值。</span><span class="sxs-lookup"><span data-stu-id="b5c48-117">For better performance, the `COR_HEAPOBJECT.type` field is a `COR_TYPEID` value rather than the ICorDebugType interface value used in much of the debugging API.</span></span> <span data-ttu-id="b5c48-118">若要获取给定类型 ID 的 ICorDebugType 对象，可以将 `COR_TYPEID` 值传递给 [ICorDebugProcess5：： GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="b5c48-118">To obtain an ICorDebugType object for a given type ID, you can pass the `COR_TYPEID` value to the [ICorDebugProcess5::GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) method.</span></span>  
  
 <span data-ttu-id="b5c48-119">`COR_HEAPOBJECT`结构包含引用计数的 COM 接口。</span><span class="sxs-lookup"><span data-stu-id="b5c48-119">The `COR_HEAPOBJECT` structure includes a reference-counted COM interface.</span></span> <span data-ttu-id="b5c48-120">如果 `COR_HEAPOBJECT` 通过调用 [ICorDebugHeapEnum：： Next](icordebugheapenum-next-method.md) 方法检索枚举器中的实例，则必须随后释放该引用。</span><span class="sxs-lookup"><span data-stu-id="b5c48-120">If you retrieve a `COR_HEAPOBJECT` instance from the enumerator by calling the [ICorDebugHeapEnum::Next](icordebugheapenum-next-method.md) method, you must subsequently release the reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5c48-121">要求</span><span class="sxs-lookup"><span data-stu-id="b5c48-121">Requirements</span></span>  

 <span data-ttu-id="b5c48-122">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b5c48-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5c48-123">**标头**：CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b5c48-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b5c48-124">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b5c48-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b5c48-125">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5c48-125">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5c48-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="b5c48-126">See also</span></span>

- [<span data-ttu-id="b5c48-127">调试结构</span><span class="sxs-lookup"><span data-stu-id="b5c48-127">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="b5c48-128">调试</span><span class="sxs-lookup"><span data-stu-id="b5c48-128">Debugging</span></span>](index.md)
