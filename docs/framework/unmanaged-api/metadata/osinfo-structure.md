---
description: 了解详细信息： OSINFO 结构
title: OSINFO 结构
ms.date: 03/30/2017
api_name:
- OSINFO
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- OSINFO
helpviewer_keywords:
- OSINFO structure [.NET Framework metadata]
ms.assetid: fac7b480-7adb-4450-a5e9-690fed81ffae
topic_type:
- apiref
ms.openlocfilehash: 5027ef5cf4137aa1e781134b325407e1251fdd31
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799091"
---
# <a name="osinfo-structure"></a><span data-ttu-id="d2eaf-103">OSINFO 结构</span><span class="sxs-lookup"><span data-stu-id="d2eaf-103">OSINFO Structure</span></span>

<span data-ttu-id="d2eaf-104">包含有关程序集或模块的操作系统的详细信息。</span><span class="sxs-lookup"><span data-stu-id="d2eaf-104">Contains details about the operating system for an assembly or module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2eaf-105">语法</span><span class="sxs-lookup"><span data-stu-id="d2eaf-105">Syntax</span></span>  
  
```cpp  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;
    DWORD   dwOSMinorVersion;
} OSINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="d2eaf-106">成员</span><span class="sxs-lookup"><span data-stu-id="d2eaf-106">Members</span></span>  
  
|<span data-ttu-id="d2eaf-107">成员</span><span class="sxs-lookup"><span data-stu-id="d2eaf-107">Member</span></span>|<span data-ttu-id="d2eaf-108">说明</span><span class="sxs-lookup"><span data-stu-id="d2eaf-108">Description</span></span>|  
|------------|-----------------|  
|`dwOSPlatformId`|<span data-ttu-id="d2eaf-109">Microsoft Windows 平台函数定义的标识符值之一 `GetVersionEx` 。</span><span class="sxs-lookup"><span data-stu-id="d2eaf-109">One of the identifier values defined by the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="d2eaf-110">支持以下值：</span><span class="sxs-lookup"><span data-stu-id="d2eaf-110">The following values are supported:</span></span><br /><br /> <span data-ttu-id="d2eaf-111">-VER_PLATFORM_WIN32s 或0x0000，用于指定 Microsoft Windows 3.1。</span><span class="sxs-lookup"><span data-stu-id="d2eaf-111">-   VER_PLATFORM_WIN32s, or 0x0000, to specify Microsoft Windows 3.1.</span></span><br /><span data-ttu-id="d2eaf-112">-VER_PLATFORM_WIN32_WINDOWS 或0x0001，用于指定 Windows 95、Windows 98 或其上的操作系统。</span><span class="sxs-lookup"><span data-stu-id="d2eaf-112">-   VER_PLATFORM_WIN32_WINDOWS, or 0x0001, to specify Windows 95, Windows 98, or operating systems descended from them.</span></span><br /><span data-ttu-id="d2eaf-113">-VER_PLATFORM_WIN32_NT 或0x0002，用于指定其上的 Windows NT 或操作系统。</span><span class="sxs-lookup"><span data-stu-id="d2eaf-113">-   VER_PLATFORM_WIN32_NT, or 0x0002, to specify Windows NT or operating systems descended from it.</span></span>|  
|`dwOSMajorVersion`|<span data-ttu-id="d2eaf-114">操作系统主版本，或指示任何版本的 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="d2eaf-114">The operating system major version, or a NULL value to indicate any version.</span></span>|  
|`dwOSMinorVersion`|<span data-ttu-id="d2eaf-115">操作系统次要版本，或指示任何版本的 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="d2eaf-115">The operating system minor version, or a NULL value to indicate any version.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2eaf-116">备注</span><span class="sxs-lookup"><span data-stu-id="d2eaf-116">Remarks</span></span>  

 <span data-ttu-id="d2eaf-117">`OSINFO` 基于对 `OSVERSIONINFOEX` Microsoft Windows 平台函数的调用中使用的结构 `GetVersionEx` 。</span><span class="sxs-lookup"><span data-stu-id="d2eaf-117">`OSINFO` is based on the `OSVERSIONINFOEX` structure that is used in calls to the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="d2eaf-118">ASSEMBLYMETADATA 结构使用此结构来指示其操作系统支持。</span><span class="sxs-lookup"><span data-stu-id="d2eaf-118">This structure is used by the ASSEMBLYMETADATA structure to indicate its operating system support.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2eaf-119">要求</span><span class="sxs-lookup"><span data-stu-id="d2eaf-119">Requirements</span></span>  

 <span data-ttu-id="d2eaf-120">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d2eaf-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2eaf-121">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="d2eaf-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d2eaf-122">**库：** 用作 MsCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="d2eaf-122">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d2eaf-123">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2eaf-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2eaf-124">请参阅</span><span class="sxs-lookup"><span data-stu-id="d2eaf-124">See also</span></span>

- [<span data-ttu-id="d2eaf-125">元数据结构</span><span class="sxs-lookup"><span data-stu-id="d2eaf-125">Metadata Structures</span></span>](metadata-structures.md)
- [<span data-ttu-id="d2eaf-126">IMetaDataAssemblyEmit 接口</span><span class="sxs-lookup"><span data-stu-id="d2eaf-126">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
