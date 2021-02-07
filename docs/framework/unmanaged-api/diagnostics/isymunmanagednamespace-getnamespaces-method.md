---
description: 了解详细信息： ISymUnmanagedNamespace：： GetNamespaces 方法
title: ISymUnmanagedNamespace::GetNamespaces 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace.GetNamespaces
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace::GetNamespaces
helpviewer_keywords:
- ISymUnmanagedNamespace::GetNamespaces method [.NET Framework debugging]
- GetNamespaces method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: 0ea9d9af-8709-4a46-872b-f54d9e840088
topic_type:
- apiref
ms.openlocfilehash: f17b16e2a3a7001d16c86dd6dc95241c1b0785e6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709901"
---
# <a name="isymunmanagednamespacegetnamespaces-method"></a><span data-ttu-id="cf953-103">ISymUnmanagedNamespace::GetNamespaces 方法</span><span class="sxs-lookup"><span data-stu-id="cf953-103">ISymUnmanagedNamespace::GetNamespaces Method</span></span>

<span data-ttu-id="cf953-104">获取此命名空间的子级。</span><span class="sxs-lookup"><span data-stu-id="cf953-104">Gets the children of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf953-105">语法</span><span class="sxs-lookup"><span data-stu-id="cf953-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces), length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf953-106">参数</span><span class="sxs-lookup"><span data-stu-id="cf953-106">Parameters</span></span>  

 `cNameSpaces`  
 <span data-ttu-id="cf953-107">中 `ULONG32` 指示数组大小的 `namespaces` 。</span><span class="sxs-lookup"><span data-stu-id="cf953-107">[in] A `ULONG32` that indicates the size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="cf953-108">弄指向的指针， `ULONG32` 该指针接收包含命名空间所需的缓冲区大小（以字符数表示）。</span><span class="sxs-lookup"><span data-stu-id="cf953-108">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="cf953-109">弄指向包含命名空间的缓冲区的指针。</span><span class="sxs-lookup"><span data-stu-id="cf953-109">[out] A pointer to the buffer that contains the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cf953-110">返回值</span><span class="sxs-lookup"><span data-stu-id="cf953-110">Return Value</span></span>  

 <span data-ttu-id="cf953-111">如果该方法成功，则 S_OK;否则，E_FAIL 或其他一些错误代码。</span><span class="sxs-lookup"><span data-stu-id="cf953-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf953-112">要求</span><span class="sxs-lookup"><span data-stu-id="cf953-112">Requirements</span></span>  

 <span data-ttu-id="cf953-113">**标头：** CorSym，CorSym</span><span class="sxs-lookup"><span data-stu-id="cf953-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf953-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="cf953-114">See also</span></span>

- [<span data-ttu-id="cf953-115">ISymUnmanagedNamespace 接口</span><span class="sxs-lookup"><span data-stu-id="cf953-115">ISymUnmanagedNamespace Interface</span></span>](isymunmanagednamespace-interface.md)
