---
description: 了解详细信息： IMetaDataImport2：： GetVersionString 方法
title: IMetaDataImport2::GetVersionString 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetVersionString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetVersionString
helpviewer_keywords:
- GetVersionString method, IMetaDataImport2 interface [.NET Framework metadata]
- IMetaDataImport2::GetVersionString method [.NET Framework metadata]
ms.assetid: 308183ee-fd44-4432-9d86-ef00d181b49b
topic_type:
- apiref
ms.openlocfilehash: 6f7e296607dc3167936c69d52a8baae4f5555b88
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688554"
---
# <a name="imetadataimport2getversionstring-method"></a><span data-ttu-id="7847d-103">IMetaDataImport2::GetVersionString 方法</span><span class="sxs-lookup"><span data-stu-id="7847d-103">IMetaDataImport2::GetVersionString Method</span></span>

<span data-ttu-id="7847d-104">获取用于生成程序集的运行时的版本号。</span><span class="sxs-lookup"><span data-stu-id="7847d-104">Gets the version number of the runtime that was used to build the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7847d-105">语法</span><span class="sxs-lookup"><span data-stu-id="7847d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionString (  
   [out] LPWSTR      pwzBuf,  
   [in]  DWORD       ccBufSize,  
   [out] DWORD       *pccBufSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7847d-106">参数</span><span class="sxs-lookup"><span data-stu-id="7847d-106">Parameters</span></span>  

 `pwzBuf`  
 <span data-ttu-id="7847d-107">弄用于存储指定版本的字符串的数组。</span><span class="sxs-lookup"><span data-stu-id="7847d-107">[out] An array to store the string that specifies the version.</span></span>  
  
 `ccBufSize`  
 <span data-ttu-id="7847d-108">中数组的大小（以宽字符为范围） `pwzBuf` 。</span><span class="sxs-lookup"><span data-stu-id="7847d-108">[in] The size, in wide characters, of the `pwzBuf` array.</span></span>  
  
 `pccBufSize`  
 <span data-ttu-id="7847d-109">弄数组中返回的宽字符数，包括 null 结束符 `pwzBuf` 。</span><span class="sxs-lookup"><span data-stu-id="7847d-109">[out] The number of wide characters, including a null terminator, returned in the `pwzBuf` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7847d-110">备注</span><span class="sxs-lookup"><span data-stu-id="7847d-110">Remarks</span></span>  

 <span data-ttu-id="7847d-111">`GetVersionString`方法获取当前元数据范围的生成版本。</span><span class="sxs-lookup"><span data-stu-id="7847d-111">The `GetVersionString` method gets the built-for version of the current metadata scope.</span></span> <span data-ttu-id="7847d-112">如果从未保存过范围，则它将不会有内置版本，并将返回空字符串。</span><span class="sxs-lookup"><span data-stu-id="7847d-112">If the scope has never been saved, it will not have a built-for version, and an empty string will be returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7847d-113">要求</span><span class="sxs-lookup"><span data-stu-id="7847d-113">Requirements</span></span>  

 <span data-ttu-id="7847d-114">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7847d-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7847d-115">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="7847d-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7847d-116">**库：** 用作 MsCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="7847d-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7847d-117">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7847d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7847d-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="7847d-118">See also</span></span>

- [<span data-ttu-id="7847d-119">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="7847d-119">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="7847d-120">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="7847d-120">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
