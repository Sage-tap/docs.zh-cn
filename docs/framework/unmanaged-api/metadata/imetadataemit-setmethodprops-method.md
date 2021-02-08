---
description: 了解详细信息： IMetaDataEmit：： SetMethodProps 方法
title: IMetaDataEmit::SetMethodProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetMethodProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetMethodProps
helpviewer_keywords:
- SetMethodProps method [.NET Framework metadata]
- IMetaDataEmit::SetMethodProps method [.NET Framework metadata]
ms.assetid: e0c6ac12-22ea-43f5-b799-8cda0faf3336
topic_type:
- apiref
ms.openlocfilehash: edecdc14abb386f8fa4cd70535f2b8c012bdc59f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772089"
---
# <a name="imetadataemitsetmethodprops-method"></a><span data-ttu-id="aadca-103">IMetaDataEmit::SetMethodProps 方法</span><span class="sxs-lookup"><span data-stu-id="aadca-103">IMetaDataEmit::SetMethodProps Method</span></span>

<span data-ttu-id="aadca-104">设置或更新在指定的相对虚拟地址上存储的功能，该方法由之前对 IMetaDataEmit 的调用定义的方法 [：:D efinemethod](imetadataemit-definemethod-method.md)。</span><span class="sxs-lookup"><span data-stu-id="aadca-104">Sets or updates the feature, stored at the specified relative virtual address, of a method defined by a prior call to [IMetaDataEmit::DefineMethod](imetadataemit-definemethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aadca-105">语法</span><span class="sxs-lookup"><span data-stu-id="aadca-105">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodProps (
    [in]  mdMethodDef md,
    [in]  DWORD       dwMethodFlags,  
    [in]  ULONG       ulCodeRVA,
    [in]  DWORD       dwImplFlags
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aadca-106">参数</span><span class="sxs-lookup"><span data-stu-id="aadca-106">Parameters</span></span>  

 `md`  
 <span data-ttu-id="aadca-107">中要更改的方法的标记。</span><span class="sxs-lookup"><span data-stu-id="aadca-107">[in] The token for the method to be changed.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="aadca-108">中成员特性。</span><span class="sxs-lookup"><span data-stu-id="aadca-108">[in] The member attributes.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="aadca-109">中代码的地址。</span><span class="sxs-lookup"><span data-stu-id="aadca-109">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="aadca-110">中方法的实现标志。</span><span class="sxs-lookup"><span data-stu-id="aadca-110">[in] The implementation flags for the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aadca-111">要求</span><span class="sxs-lookup"><span data-stu-id="aadca-111">Requirements</span></span>  

 <span data-ttu-id="aadca-112">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="aadca-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aadca-113">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="aadca-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="aadca-114">**库：** 用作 MSCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="aadca-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aadca-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aadca-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aadca-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="aadca-116">See also</span></span>

- [<span data-ttu-id="aadca-117">IMetaDataEmit 接口</span><span class="sxs-lookup"><span data-stu-id="aadca-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="aadca-118">IMetaDataEmit2 接口</span><span class="sxs-lookup"><span data-stu-id="aadca-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
