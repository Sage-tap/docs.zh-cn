---
description: 了解详细信息： CorNativeType 枚举
title: CorNativeType 枚举
ms.date: 03/30/2017
api_name:
- CorNativeType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeType
helpviewer_keywords:
- CorNativeType enumeration [.NET Framework metadata]
ms.assetid: e47a72f1-9609-48ed-bb34-97170d7f6890
topic_type:
- apiref
ms.openlocfilehash: d2313eef124f3308c4792b47da8b7c8bba984597
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784322"
---
# <a name="cornativetype-enumeration"></a><span data-ttu-id="65807-103">CorNativeType 枚举</span><span class="sxs-lookup"><span data-stu-id="65807-103">CorNativeType Enumeration</span></span>

<span data-ttu-id="65807-104">包含一些值，用于描述本机非托管类型。</span><span class="sxs-lookup"><span data-stu-id="65807-104">Contains values that describe native unmanaged types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65807-105">语法</span><span class="sxs-lookup"><span data-stu-id="65807-105">Syntax</span></span>  
  
```cpp  
typedef enum CorNativeType {  
  
    NATIVE_TYPE_END                  = 0x0,  
    NATIVE_TYPE_VOID                 = 0x1,  
    NATIVE_TYPE_BOOLEAN              = 0x2,  
    NATIVE_TYPE_I1                   = 0x3,  
    NATIVE_TYPE_U1                   = 0x4,  
    NATIVE_TYPE_I2                   = 0x5,  
    NATIVE_TYPE_U2                   = 0x6,  
    NATIVE_TYPE_I4                   = 0x7,  
    NATIVE_TYPE_U4                   = 0x8,  
    NATIVE_TYPE_I8                   = 0x9,  
    NATIVE_TYPE_U8                   = 0xa,  
    NATIVE_TYPE_R4                   = 0xb,  
    NATIVE_TYPE_R8                   = 0xc,  
    NATIVE_TYPE_SYSCHAR              = 0xd,  
    NATIVE_TYPE_VARIANT              = 0xe,  
    NATIVE_TYPE_CURRENCY             = 0xf,  
    NATIVE_TYPE_PTR                  = 0x10,  
  
    NATIVE_TYPE_DECIMAL              = 0x11,  
    NATIVE_TYPE_DATE                 = 0x12,  
    NATIVE_TYPE_BSTR                 = 0x13,  
    NATIVE_TYPE_LPSTR                = 0x14,  
    NATIVE_TYPE_LPWSTR               = 0x15,  
    NATIVE_TYPE_LPTSTR               = 0x16,  
    NATIVE_TYPE_FIXEDSYSSTRING       = 0x17,  
    NATIVE_TYPE_OBJECTREF            = 0x18,  
    NATIVE_TYPE_IUNKNOWN             = 0x19,  
    NATIVE_TYPE_IDISPATCH            = 0x1a,  
    NATIVE_TYPE_STRUCT               = 0x1b,  
    NATIVE_TYPE_INTF                 = 0x1c,  
    NATIVE_TYPE_SAFEARRAY            = 0x1d,  
    NATIVE_TYPE_FIXEDARRAY           = 0x1e,  
    NATIVE_TYPE_INT                  = 0x1f,  
    NATIVE_TYPE_UINT                 = 0x20,  
  
    NATIVE_TYPE_NESTEDSTRUCT         = 0x21,  
    NATIVE_TYPE_BYVALSTR             = 0x22,  
    NATIVE_TYPE_ANSIBSTR             = 0x23,  
    NATIVE_TYPE_TBSTR                = 0x24,  
    NATIVE_TYPE_VARIANTBOOL          = 0x25,  
    NATIVE_TYPE_FUNC                 = 0x26,  
  
    NATIVE_TYPE_ASANY                = 0x28,  
    NATIVE_TYPE_ARRAY                = 0x2a,  
    NATIVE_TYPE_LPSTRUCT             = 0x2b,  
    NATIVE_TYPE_CUSTOMMARSHALER      = 0x2c,  
    NATIVE_TYPE_IINSPECTABLE         = 0x2e,  
    NATIVE_TYPE_HSTRING              = 0x2f,  
  
    NATIVE_TYPE_ERROR                = 0x2d,
  
    NATIVE_TYPE_MAX                  = 0x50  
  
} CorNativeType;  
```  
  
## <a name="members"></a><span data-ttu-id="65807-106">成员</span><span class="sxs-lookup"><span data-stu-id="65807-106">Members</span></span>  
  
|<span data-ttu-id="65807-107">成员</span><span class="sxs-lookup"><span data-stu-id="65807-107">Member</span></span>|<span data-ttu-id="65807-108">说明</span><span class="sxs-lookup"><span data-stu-id="65807-108">Description</span></span>|  
|------------|-----------------|  
|`NATIVE_TYPE_END`|<span data-ttu-id="65807-109">已过时。</span><span class="sxs-lookup"><span data-stu-id="65807-109">Obsolete.</span></span>|  
|`NATIVE_TYPE_VOID`|<span data-ttu-id="65807-110">已过时。</span><span class="sxs-lookup"><span data-stu-id="65807-110">Obsolete.</span></span>|  
|`NATIVE_TYPE_BOOLEAN`|<span data-ttu-id="65807-111">4字节布尔值，其中 TRUE 为非零，FALSE 为零。</span><span class="sxs-lookup"><span data-stu-id="65807-111">A 4-byte Boolean value, where TRUE is non-zero and FALSE is zero.</span></span>|  
|`NATIVE_TYPE_I1`|<span data-ttu-id="65807-112">8位有符号整数值。</span><span class="sxs-lookup"><span data-stu-id="65807-112">A signed 8-bit integer value.</span></span>|  
|`NATIVE_TYPE_U1`|<span data-ttu-id="65807-113">8位无符号整数值。</span><span class="sxs-lookup"><span data-stu-id="65807-113">An unsigned 8-bit integer value.</span></span>|  
|`NATIVE_TYPE_I2`|<span data-ttu-id="65807-114">16位带符号整数值。</span><span class="sxs-lookup"><span data-stu-id="65807-114">A signed 16-bit integer value.</span></span>|  
|`NATIVE_TYPE_U2`|<span data-ttu-id="65807-115">16位无符号整数值。</span><span class="sxs-lookup"><span data-stu-id="65807-115">An unsigned 16-bit integer value.</span></span>|  
|`NATIVE_TYPE_I4`|<span data-ttu-id="65807-116">带符号的 32 位整数值。</span><span class="sxs-lookup"><span data-stu-id="65807-116">A signed 32-bit integer value.</span></span>|  
|`NATIVE_TYPE_U4`|<span data-ttu-id="65807-117">32 位无符号整数值。</span><span class="sxs-lookup"><span data-stu-id="65807-117">An unsigned 32-bit integer value.</span></span>|  
|`NATIVE_TYPE_I8`|<span data-ttu-id="65807-118">一个有符号的64位整数值。</span><span class="sxs-lookup"><span data-stu-id="65807-118">A signed 64-bit integer value.</span></span>|  
|`NATIVE_TYPE_U8`|<span data-ttu-id="65807-119">64位无符号整数值。</span><span class="sxs-lookup"><span data-stu-id="65807-119">An unsigned 64-bit integer value.</span></span>|  
|`NATIVE_TYPE_R4`|<span data-ttu-id="65807-120">4字节浮点数值。</span><span class="sxs-lookup"><span data-stu-id="65807-120">A 4-byte floating-point numeric value.</span></span>|  
|`NATIVE_TYPE_R8`|<span data-ttu-id="65807-121">8字节浮点数值。</span><span class="sxs-lookup"><span data-stu-id="65807-121">An 8-byte floating-point numeric value.</span></span>|  
|`NATIVE_TYPE_SYSCHAR`|<span data-ttu-id="65807-122">已过时。</span><span class="sxs-lookup"><span data-stu-id="65807-122">Obsolete.</span></span>|  
|`NATIVE_TYPE_VARIANT`|<span data-ttu-id="65807-123">已过时。</span><span class="sxs-lookup"><span data-stu-id="65807-123">Obsolete.</span></span>|  
|`NATIVE_TYPE_CURRENCY`|<span data-ttu-id="65807-124">与托管类型对应的数值 COM 类型 <xref:System.Decimal> 。</span><span class="sxs-lookup"><span data-stu-id="65807-124">A numeric COM type that corresponds to the managed <xref:System.Decimal> type.</span></span>|  
|`NATIVE_TYPE_PTR`|<span data-ttu-id="65807-125">已过时。</span><span class="sxs-lookup"><span data-stu-id="65807-125">Obsolete.</span></span>|  
|`NATIVE_TYPE_DECIMAL`|<span data-ttu-id="65807-126">已过时。</span><span class="sxs-lookup"><span data-stu-id="65807-126">Obsolete.</span></span>|  
|`NATIVE_TYPE_DATE`|<span data-ttu-id="65807-127">已过时。</span><span class="sxs-lookup"><span data-stu-id="65807-127">Obsolete.</span></span>|  
|`NATIVE_TYPE_BSTR`|<span data-ttu-id="65807-128">COM 互操作。</span><span class="sxs-lookup"><span data-stu-id="65807-128">COM Interop.</span></span>|  
|`NATIVE_TYPE_LPSTR`|<span data-ttu-id="65807-129">一个 LPSTR 的字符串值。</span><span class="sxs-lookup"><span data-stu-id="65807-129">An LPSTR string value.</span></span>|  
|`NATIVE_TYPE_LPWSTR`|<span data-ttu-id="65807-130">一个 LPWSTR 的字符串值。</span><span class="sxs-lookup"><span data-stu-id="65807-130">An LPWSTR string value.</span></span>|  
|`NATIVE_TYPE_LPTSTR`|<span data-ttu-id="65807-131">一个 LPTSTR 的字符串值。</span><span class="sxs-lookup"><span data-stu-id="65807-131">An LPTSTR string value.</span></span>|  
|`NATIVE_TYPE_FIXEDSYSSTRING`|<span data-ttu-id="65807-132">固定的系统定义字符串值。</span><span class="sxs-lookup"><span data-stu-id="65807-132">A fixed, system-defined string value.</span></span>|  
|`NATIVE_TYPE_OBJECTREF`|<span data-ttu-id="65807-133">已过时。</span><span class="sxs-lookup"><span data-stu-id="65807-133">Obsolete.</span></span>|  
|`NATIVE_TYPE_IUNKNOWN`|<span data-ttu-id="65807-134">COM 互操作。</span><span class="sxs-lookup"><span data-stu-id="65807-134">COM Interop.</span></span>|  
|`NATIVE_TYPE_IDISPATCH`|<span data-ttu-id="65807-135">COM 互操作。</span><span class="sxs-lookup"><span data-stu-id="65807-135">COM Interop.</span></span>|  
|`NATIVE_TYPE_STRUCT`|<span data-ttu-id="65807-136">本机结构值。</span><span class="sxs-lookup"><span data-stu-id="65807-136">A native structure value.</span></span>|  
|`NATIVE_TYPE_INTF`|<span data-ttu-id="65807-137">COM 互操作。</span><span class="sxs-lookup"><span data-stu-id="65807-137">COM Interop.</span></span>|  
|`NATIVE_TYPE_SAFEARRAY`|<span data-ttu-id="65807-138">COM 互操作。</span><span class="sxs-lookup"><span data-stu-id="65807-138">COM Interop.</span></span>|  
|`NATIVE_TYPE_FIXEDARRAY`|<span data-ttu-id="65807-139">固定长度的数组值。</span><span class="sxs-lookup"><span data-stu-id="65807-139">A fixed-length array value.</span></span>|  
|`NATIVE_TYPE_INT`|<span data-ttu-id="65807-140">本机16位有符号整数值。</span><span class="sxs-lookup"><span data-stu-id="65807-140">A native 16-bit signed integer value.</span></span>|  
|`NATIVE_TYPE_UINT`|<span data-ttu-id="65807-141">本机16位无符号整数值。</span><span class="sxs-lookup"><span data-stu-id="65807-141">A native 16-bit unsigned integer value.</span></span>|  
|`NATIVE_TYPE_NESTEDSTRUCT`|<span data-ttu-id="65807-142">已过时。</span><span class="sxs-lookup"><span data-stu-id="65807-142">Obsolete.</span></span><br /><br /> <span data-ttu-id="65807-143">使用 NATIVE_TYPE_STRUCT。</span><span class="sxs-lookup"><span data-stu-id="65807-143">Use NATIVE_TYPE_STRUCT.</span></span>|  
|`NATIVE_TYPE_BYVALSTR`|<span data-ttu-id="65807-144">COM 互操作。</span><span class="sxs-lookup"><span data-stu-id="65807-144">COM Interop.</span></span>|  
|`NATIVE_TYPE_ANSIBSTR`|<span data-ttu-id="65807-145">COM 互操作。</span><span class="sxs-lookup"><span data-stu-id="65807-145">COM Interop.</span></span>|  
|`NATIVE_TYPE_TBSTR`|<span data-ttu-id="65807-146">COM 互操作。</span><span class="sxs-lookup"><span data-stu-id="65807-146">COM Interop.</span></span><br /><br /> <span data-ttu-id="65807-147">选择 "BSTR" 或 "ANSIBSTR"，具体取决于平台。</span><span class="sxs-lookup"><span data-stu-id="65807-147">Select BSTR or ANSIBSTR depending on the platform.</span></span>|  
|`NATIVE_TYPE_VARIANTBOOL`|<span data-ttu-id="65807-148">一个2字节的布尔值，其中 TRUE 为-1，FALSE 为零。</span><span class="sxs-lookup"><span data-stu-id="65807-148">A 2-byte Boolean value, where TRUE is -1 and FALSE is zero.</span></span>|  
|`NATIVE_TYPE_FUNC`|<span data-ttu-id="65807-149">函数指针。</span><span class="sxs-lookup"><span data-stu-id="65807-149">A function pointer.</span></span>|  
|`NATIVE_TYPE_ASANY`|<span data-ttu-id="65807-150">对任何本机类型的引用。</span><span class="sxs-lookup"><span data-stu-id="65807-150">A reference to any native type.</span></span>|  
|`NATIVE_TYPE_ARRAY`|<span data-ttu-id="65807-151">对具有未指定类型的成员的数组的引用。</span><span class="sxs-lookup"><span data-stu-id="65807-151">A reference to an array with members of an unspecified type.</span></span>|  
|`NATIVE_TYPE_LPSTRUCT`|<span data-ttu-id="65807-152">指向结构的32位整数指针。</span><span class="sxs-lookup"><span data-stu-id="65807-152">A 32-bit integer pointer to a structure.</span></span>|  
|`NATIVE_TYPE_CUSTOMMARSHALER`|<span data-ttu-id="65807-153">自定义封送拆收器本机类型。</span><span class="sxs-lookup"><span data-stu-id="65807-153">A custom marshaler native type.</span></span><br /><br /> <span data-ttu-id="65807-154">它后面必须是以下格式的字符串： "Native type name/0Custom 封送拆收器 type name/0Optional cookie/0" 或 "{Native type GUID}/0Custom 封送处理类型 name/0Optional cookie/0"</span><span class="sxs-lookup"><span data-stu-id="65807-154">This must be followed by a string of the following format: "Native type name/0Custom marshaler type name/0Optional cookie/0" or "{Native type GUID}/0Custom marshaler type name/0Optional cookie/0"</span></span>|  
|`NATIVE_TYPE_ERROR`|<span data-ttu-id="65807-155">COM 互操作。</span><span class="sxs-lookup"><span data-stu-id="65807-155">COM Interop.</span></span><br /><br /> <span data-ttu-id="65807-156">对于 ELEMENT_TYPE_I4 此类型映射到 VT_HRESULT。</span><span class="sxs-lookup"><span data-stu-id="65807-156">With ELEMENT_TYPE_I4 this type maps to VT_HRESULT.</span></span>|  
|`NATIVE_TYPE_IINSPECTABLE`|<span data-ttu-id="65807-157">本机 `IInspectable` 类型。</span><span class="sxs-lookup"><span data-stu-id="65807-157">A native `IInspectable` type.</span></span>|  
|`NATIVE_TYPE_HSTRING`|<span data-ttu-id="65807-158">一个本机 `HString` 。</span><span class="sxs-lookup"><span data-stu-id="65807-158">A native `HString`.</span></span>|  
|`NATIVE_TYPE_MAX`|<span data-ttu-id="65807-159">一个无效值。</span><span class="sxs-lookup"><span data-stu-id="65807-159">An invalid value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="65807-160">要求</span><span class="sxs-lookup"><span data-stu-id="65807-160">Requirements</span></span>  

 <span data-ttu-id="65807-161">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="65807-161">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65807-162">**标头：** Corhdr。h</span><span class="sxs-lookup"><span data-stu-id="65807-162">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="65807-163">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65807-163">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65807-164">请参阅</span><span class="sxs-lookup"><span data-stu-id="65807-164">See also</span></span>

- <xref:System.Runtime.InteropServices.UnmanagedType>
- [<span data-ttu-id="65807-165">元数据枚举</span><span class="sxs-lookup"><span data-stu-id="65807-165">Metadata Enumerations</span></span>](metadata-enumerations.md)
