---
description: 了解详细信息： ICorDebugAppDomain2：： GetArrayOrPointerType 方法
title: ICorDebugAppDomain2::GetArrayOrPointerType 方法
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain2.GetArrayOrPointerType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain2::GetArrayOrPointerType
helpviewer_keywords:
- GetArrayOrPointerType method [.NET Framework debugging]
- ICorDebugAppDomain2::GetArrayOrPointerType method [.NET Framework debugging]
ms.assetid: 97e493f5-3a62-4ec7-b42f-4af57bf71f57
topic_type:
- apiref
ms.openlocfilehash: e42d105e807bdb8c81f2d6f8ef6c2f65a4081d98
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754220"
---
# <a name="icordebugappdomain2getarrayorpointertype-method"></a><span data-ttu-id="7da22-103">ICorDebugAppDomain2::GetArrayOrPointerType 方法</span><span class="sxs-lookup"><span data-stu-id="7da22-103">ICorDebugAppDomain2::GetArrayOrPointerType Method</span></span>

<span data-ttu-id="7da22-104">获取指定类型的数组，或指定类型的指针或引用。</span><span class="sxs-lookup"><span data-stu-id="7da22-104">Gets an array of the specified type, or a pointer or reference to the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7da22-105">语法</span><span class="sxs-lookup"><span data-stu-id="7da22-105">Syntax</span></span>  
  
```cpp  
HRESULT GetArrayOrPointerType (  
    [in]  CorElementType    elementType,  
    [in]  ULONG32           nRank,  
    [in]  ICorDebugType     *pTypeArg,  
    [out] ICorDebugType     **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7da22-106">参数</span><span class="sxs-lookup"><span data-stu-id="7da22-106">Parameters</span></span>  

 `elementType`  
 <span data-ttu-id="7da22-107">中CorElementType 枚举的一个值，指定要创建的数组、指针或引用)  (基础本机类型。</span><span class="sxs-lookup"><span data-stu-id="7da22-107">[in] A value of the CorElementType enumeration that specifies the underlying native type (an array, pointer, or reference) to be created.</span></span>  
  
 `nRank`  
 <span data-ttu-id="7da22-108">中秩 (为数组的维数) 。</span><span class="sxs-lookup"><span data-stu-id="7da22-108">[in] The rank (that is, number of dimensions) of the array.</span></span> <span data-ttu-id="7da22-109">如果 `elementType` 指定指针或引用类型，则此值必须为0。</span><span class="sxs-lookup"><span data-stu-id="7da22-109">This value must be 0 if `elementType` specifies a pointer or reference type.</span></span>  
  
 `pTypeArg`  
 <span data-ttu-id="7da22-110">中指向 ICorDebugType 对象的指针，该对象表示要创建的数组、指针或引用的类型。</span><span class="sxs-lookup"><span data-stu-id="7da22-110">[in] A pointer to an ICorDebugType object that represents the type of array, pointer, or reference to be created.</span></span>  
  
 `ppType`  
 <span data-ttu-id="7da22-111">弄指向对象地址的指针 `ICorDebugType` ，该对象表示构造的数组、指针类型或引用类型。</span><span class="sxs-lookup"><span data-stu-id="7da22-111">[out] A pointer to the address of an `ICorDebugType` object that represents the constructed array, pointer type, or reference type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7da22-112">备注</span><span class="sxs-lookup"><span data-stu-id="7da22-112">Remarks</span></span>  

 <span data-ttu-id="7da22-113">*ElementType* 的值必须是下列值之一：</span><span class="sxs-lookup"><span data-stu-id="7da22-113">The value of *elementType* must be one of the following:</span></span>  
  
- <span data-ttu-id="7da22-114">ELEMENT_TYPE_PTR</span><span class="sxs-lookup"><span data-stu-id="7da22-114">ELEMENT_TYPE_PTR</span></span>  
  
- <span data-ttu-id="7da22-115">ELEMENT_TYPE_BYREF</span><span class="sxs-lookup"><span data-stu-id="7da22-115">ELEMENT_TYPE_BYREF</span></span>  
  
- <span data-ttu-id="7da22-116">ELEMENT_TYPE_ARRAY 或 ELEMENT_TYPE_SZARRAY</span><span class="sxs-lookup"><span data-stu-id="7da22-116">ELEMENT_TYPE_ARRAY or ELEMENT_TYPE_SZARRAY</span></span>  
  
 <span data-ttu-id="7da22-117">如果 *elementType* 的值是 ELEMENT_TYPE_PTR 或 ELEMENT_TYPE_BYREF，则 *nRank* 必须为零。</span><span class="sxs-lookup"><span data-stu-id="7da22-117">If the value of *elementType* is ELEMENT_TYPE_PTR or ELEMENT_TYPE_BYREF, *nRank* must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7da22-118">要求</span><span class="sxs-lookup"><span data-stu-id="7da22-118">Requirements</span></span>  

 <span data-ttu-id="7da22-119">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7da22-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7da22-120">**标头**：CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7da22-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7da22-121">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7da22-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7da22-122">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7da22-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
