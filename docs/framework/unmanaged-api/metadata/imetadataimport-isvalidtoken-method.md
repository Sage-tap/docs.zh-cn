---
description: 了解详细信息： IMetaDataImport：： IsValidToken 方法
title: IMetaDataImport::IsValidToken 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.IsValidToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::IsValidToken
helpviewer_keywords:
- IMetaDataImport::IsValidToken method [.NET Framework metadata]
- IsValidToken method [.NET Framework metadata]
ms.assetid: aeb0fc63-9eff-4384-9284-cb9900572d74
topic_type:
- apiref
ms.openlocfilehash: 68589496213c93f81cfbd0992f9b210e03d6f178
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789055"
---
# <a name="imetadataimportisvalidtoken-method"></a><span data-ttu-id="39e7e-103">IMetaDataImport::IsValidToken 方法</span><span class="sxs-lookup"><span data-stu-id="39e7e-103">IMetaDataImport::IsValidToken Method</span></span>

<span data-ttu-id="39e7e-104">获取指示指定的标记是否包含对代码对象的有效引用的值。</span><span class="sxs-lookup"><span data-stu-id="39e7e-104">Gets a value indicating whether the specified token holds a valid reference to a code object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39e7e-105">语法</span><span class="sxs-lookup"><span data-stu-id="39e7e-105">Syntax</span></span>  
  
```cpp  
BOOL IsValidToken (  
   [in] mdToken     tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39e7e-106">参数</span><span class="sxs-lookup"><span data-stu-id="39e7e-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="39e7e-107">中要检查其引用有效性的标记。</span><span class="sxs-lookup"><span data-stu-id="39e7e-107">[in] The token to check the reference validity for.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="39e7e-108">返回值</span><span class="sxs-lookup"><span data-stu-id="39e7e-108">Return Value</span></span>  

 <span data-ttu-id="39e7e-109">`true` 如果 `tk` 是当前范围内的有效元数据标记，则为。</span><span class="sxs-lookup"><span data-stu-id="39e7e-109">`true` if `tk` is a valid metadata token within the current scope.</span></span> <span data-ttu-id="39e7e-110">否则为 `false`。</span><span class="sxs-lookup"><span data-stu-id="39e7e-110">Otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39e7e-111">要求</span><span class="sxs-lookup"><span data-stu-id="39e7e-111">Requirements</span></span>  

 <span data-ttu-id="39e7e-112">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="39e7e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39e7e-113">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="39e7e-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="39e7e-114">**库：** 作为中的资源包含 MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="39e7e-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="39e7e-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39e7e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39e7e-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="39e7e-116">See also</span></span>

- [<span data-ttu-id="39e7e-117">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="39e7e-117">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="39e7e-118">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="39e7e-118">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
