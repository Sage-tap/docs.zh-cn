---
description: 了解详细信息： IMetaDataTables：： GetUserString 方法
title: IMetaDataTables::GetUserString 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetUserString
helpviewer_keywords:
- IMetaDataTables::GetUserString method [.NET Framework metadata]
- GetUserString method, IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 35b8f0d6-9aba-4714-adb2-62020a38fb7e
topic_type:
- apiref
ms.openlocfilehash: 0909bfb2dbf4e6a34b746da7397a82845c2129c2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687670"
---
# <a name="imetadatatablesgetuserstring-method"></a><span data-ttu-id="0be9a-103">IMetaDataTables::GetUserString 方法</span><span class="sxs-lookup"><span data-stu-id="0be9a-103">IMetaDataTables::GetUserString Method</span></span>

<span data-ttu-id="0be9a-104">获取当前范围内字符串列中指定索引处的硬编码字符串。</span><span class="sxs-lookup"><span data-stu-id="0be9a-104">Gets the hard-coded string at the specified index in the string column in the current scope.</span></span>

## <a name="syntax"></a><span data-ttu-id="0be9a-105">语法</span><span class="sxs-lookup"><span data-stu-id="0be9a-105">Syntax</span></span>

```cpp
HRESULT GetUserString (
    [in]  ULONG       ixUserString,
    [out] ULONG       *pcbData,
    [out] const void  **ppData
);
```

## <a name="parameters"></a><span data-ttu-id="0be9a-106">参数</span><span class="sxs-lookup"><span data-stu-id="0be9a-106">Parameters</span></span>

`ixUserString`\
<span data-ttu-id="0be9a-107">中要从中检索硬编码字符串的索引值。</span><span class="sxs-lookup"><span data-stu-id="0be9a-107">[in] The index value from which the hard-coded string will be retrieved.</span></span>

`pcbData`\
<span data-ttu-id="0be9a-108">弄指向的大小的指针 `ppData` 。</span><span class="sxs-lookup"><span data-stu-id="0be9a-108">[out] A pointer to the size of `ppData`.</span></span>

`ppData`\
<span data-ttu-id="0be9a-109">弄指向返回的字符串的指针的指针。</span><span class="sxs-lookup"><span data-stu-id="0be9a-109">[out] A pointer to a pointer to the returned string.</span></span>

## <a name="requirements"></a><span data-ttu-id="0be9a-110">要求</span><span class="sxs-lookup"><span data-stu-id="0be9a-110">Requirements</span></span>

<span data-ttu-id="0be9a-111">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0be9a-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="0be9a-112">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="0be9a-112">**Header:** Cor.h</span></span>

<span data-ttu-id="0be9a-113">**库：** 用作 MsCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="0be9a-113">**Library:** Used as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="0be9a-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0be9a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="0be9a-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="0be9a-115">See also</span></span>

- [<span data-ttu-id="0be9a-116">IMetaDataTables 接口</span><span class="sxs-lookup"><span data-stu-id="0be9a-116">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="0be9a-117">IMetaDataTables2 接口</span><span class="sxs-lookup"><span data-stu-id="0be9a-117">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
