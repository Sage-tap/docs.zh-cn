---
description: 了解详细信息： ICeeGen：： GetSectionDataLen 方法
title: ICeeGen::GetSectionDataLen 方法
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionDataLen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionDataLen
helpviewer_keywords:
- ICeeGen::GetSectionDataLen method [.NET Framework metadata]
- GetSectionDataLen method [.NET Framework metadata]
ms.assetid: e2a06ee4-b8ee-49c7-935a-c1031a29eef2
topic_type:
- apiref
ms.openlocfilehash: 9475112a6f25e9a4c57c4ded6cd11dab9bf352b9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721022"
---
# <a name="iceegengetsectiondatalen-method"></a><span data-ttu-id="6eb9d-103">ICeeGen::GetSectionDataLen 方法</span><span class="sxs-lookup"><span data-stu-id="6eb9d-103">ICeeGen::GetSectionDataLen Method</span></span>

<span data-ttu-id="6eb9d-104">获取指定节的长度。</span><span class="sxs-lookup"><span data-stu-id="6eb9d-104">Gets the length of the specified section.</span></span>  
  
 <span data-ttu-id="6eb9d-105">此方法已过时，不应使用。</span><span class="sxs-lookup"><span data-stu-id="6eb9d-105">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6eb9d-106">语法</span><span class="sxs-lookup"><span data-stu-id="6eb9d-106">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionDataLen (  
    [in]  HCEESECTION  section,  
    [out] ULONG        *dataLen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6eb9d-107">参数</span><span class="sxs-lookup"><span data-stu-id="6eb9d-107">Parameters</span></span>  

 `section`  
 <span data-ttu-id="6eb9d-108">中将检索其长度的数据部分。</span><span class="sxs-lookup"><span data-stu-id="6eb9d-108">[in] The data section whose length will be retrieved.</span></span>  
  
 `dataLen`  
 <span data-ttu-id="6eb9d-109">弄指定节的返回长度。</span><span class="sxs-lookup"><span data-stu-id="6eb9d-109">[out] The returned length of the specified section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6eb9d-110">备注</span><span class="sxs-lookup"><span data-stu-id="6eb9d-110">Remarks</span></span>  

 <span data-ttu-id="6eb9d-111">`GetSectionDataLen`仅当有特殊部分的要求不是由其他方法处理时才调用。</span><span class="sxs-lookup"><span data-stu-id="6eb9d-111">Call `GetSectionDataLen` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6eb9d-112">要求</span><span class="sxs-lookup"><span data-stu-id="6eb9d-112">Requirements</span></span>  

 <span data-ttu-id="6eb9d-113">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6eb9d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6eb9d-114">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="6eb9d-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6eb9d-115">**库：** 用作 MsCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="6eb9d-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6eb9d-116">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6eb9d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6eb9d-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="6eb9d-117">See also</span></span>

- [<span data-ttu-id="6eb9d-118">ICeeGen 接口</span><span class="sxs-lookup"><span data-stu-id="6eb9d-118">ICeeGen Interface</span></span>](iceegen-interface.md)
