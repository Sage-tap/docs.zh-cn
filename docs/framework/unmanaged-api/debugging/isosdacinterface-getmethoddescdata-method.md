---
description: 了解详细信息： ISOSDacInterface：： GetMethodDescData 方法
title: ISOSDacInterface：： GetMethodDescData 方法
ms.date: 01/16/2019
api.name:
- ISOSDacInterface::GetMethodDescData Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetMethodDescData Method
helpviewer.keywords:
- ISOSDacInterface::GetMethodDescData Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: a1284aa4d810ed9d6db7ad3c1b471702b1dad54d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790420"
---
# <a name="isosdacinterfacegetmethoddescdata-method"></a><span data-ttu-id="e97b4-103">ISOSDacInterface：： GetMethodDescData 方法</span><span class="sxs-lookup"><span data-stu-id="e97b4-103">ISOSDacInterface::GetMethodDescData Method</span></span>

<span data-ttu-id="e97b4-104">获取给定 MethodDesc 指针的数据。</span><span class="sxs-lookup"><span data-stu-id="e97b4-104">Gets the data for the given MethodDesc pointer.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="e97b4-105">语法</span><span class="sxs-lookup"><span data-stu-id="e97b4-105">Syntax</span></span>

```cpp
HRESULT GetMethodDescData(
    CLRDATA_ADDRESS            methodDesc,
    CLRDATA_ADDRESS            ip,
    DacpMethodDescData *data,
    ULONG                      cRevertedRejitVersions,
    DacpReJitData      *rgRevertedRejitData,
    void                      *pcNeededRevertedRejitData
);
```

## <a name="parameters"></a><span data-ttu-id="e97b4-106">参数</span><span class="sxs-lookup"><span data-stu-id="e97b4-106">Parameters</span></span>

`methodDesc`\
<span data-ttu-id="e97b4-107">中MethodDesc 的地址。</span><span class="sxs-lookup"><span data-stu-id="e97b4-107">[in] The address of the MethodDesc.</span></span>

`ip`\
<span data-ttu-id="e97b4-108">中方法的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="e97b4-108">[in] The IP address of the method.</span></span>

`data`\
<span data-ttu-id="e97b4-109">弄与 MethodDesc 关联的、从内部 Api 返回的数据。</span><span class="sxs-lookup"><span data-stu-id="e97b4-109">[out] The data associated with the MethodDesc as returned from the internal APIs.</span></span>

`cRevertedRejitVersions`\
<span data-ttu-id="e97b4-110">弄已还原的 rejit 版本数。</span><span class="sxs-lookup"><span data-stu-id="e97b4-110">[out] The number of reverted rejit versions.</span></span>

`rgRevertedRejitData`\
<span data-ttu-id="e97b4-111">弄与从内部 Api 返回的已恢复 rejit 版本关联的数据。</span><span class="sxs-lookup"><span data-stu-id="e97b4-111">[out] The data associated with the reverted rejit versions as returned from the internal APIs.</span></span>

`pcNeededRevertedRejitData`\
<span data-ttu-id="e97b4-112">弄存储与还原的 ReJit 版本关联的数据所需的字节数。</span><span class="sxs-lookup"><span data-stu-id="e97b4-112">[out] The number of bytes required to store the data associated with the reverted ReJit versions.</span></span>

## <a name="remarks"></a><span data-ttu-id="e97b4-113">备注</span><span class="sxs-lookup"><span data-stu-id="e97b4-113">Remarks</span></span>

<span data-ttu-id="e97b4-114">提供的方法是接口的一部分 `ISOSDacInterface` ，并且对应于虚拟方法表的21槽。</span><span class="sxs-lookup"><span data-stu-id="e97b4-114">The provided method is part of the `ISOSDacInterface` interface and corresponds to the 21st slot of the virtual method table.</span></span> <span data-ttu-id="e97b4-115">若要使用它们， [`CLRDATA_ADDRESS`](../common-data-types-unmanaged-api-reference.md) 必须将定义为64位无符号整数。</span><span class="sxs-lookup"><span data-stu-id="e97b4-115">To be able to use them, [`CLRDATA_ADDRESS`](../common-data-types-unmanaged-api-reference.md) must be defined as a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="e97b4-116">要求</span><span class="sxs-lookup"><span data-stu-id="e97b4-116">Requirements</span></span>

<span data-ttu-id="e97b4-117">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e97b4-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="e97b4-118">**标头：** 内容</span><span class="sxs-lookup"><span data-stu-id="e97b4-118">**Header:** None</span></span>  
<span data-ttu-id="e97b4-119">**库：** 内容</span><span class="sxs-lookup"><span data-stu-id="e97b4-119">**Library:** None</span></span>  
<span data-ttu-id="e97b4-120">**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e97b4-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="e97b4-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="e97b4-121">See also</span></span>

- [<span data-ttu-id="e97b4-122">调试</span><span class="sxs-lookup"><span data-stu-id="e97b4-122">Debugging</span></span>](index.md)
- [<span data-ttu-id="e97b4-123">ISOSDacInterface 接口</span><span class="sxs-lookup"><span data-stu-id="e97b4-123">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)
