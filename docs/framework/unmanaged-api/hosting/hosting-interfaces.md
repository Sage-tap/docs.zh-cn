---
description: 了解更多：托管接口
title: 承载接口
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting]
- hosting interfaces [.NET Framework]
- unmanaged interfaces [.NET Framework], hosting
ms.assetid: cc64cb05-38da-418e-815a-daac8e8e26e5
ms.openlocfilehash: 596de1e74fc9c80e5f8b63f40c91a9ef29abcc6f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785180"
---
# <a name="hosting-interfaces"></a><span data-ttu-id="a8c24-103">承载接口</span><span class="sxs-lookup"><span data-stu-id="a8c24-103">Hosting Interfaces</span></span>

<span data-ttu-id="a8c24-104">本部分介绍了非托管主机可用于将公共语言运行时 (CLR) 集成到其应用程序的接口。</span><span class="sxs-lookup"><span data-stu-id="a8c24-104">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) into their applications.</span></span>  
  
 <span data-ttu-id="a8c24-105">.NET Framework 版本2.0 宿主接口取代了 .NET Framework 版本1.0 和1.1 接口。</span><span class="sxs-lookup"><span data-stu-id="a8c24-105">The .NET Framework version 2.0 hosting interfaces supersede the .NET Framework version 1.0 and 1.1 interfaces.</span></span> <span data-ttu-id="a8c24-106">两组接口之间存在重大差异。</span><span class="sxs-lookup"><span data-stu-id="a8c24-106">There are significant differences between the two sets of interfaces.</span></span> <span data-ttu-id="a8c24-107">混合它们可能会导致意外的行为，因此不建议这样做。</span><span class="sxs-lookup"><span data-stu-id="a8c24-107">Mixing them could cause unexpected behavior and is not recommended.</span></span>  
  
 <span data-ttu-id="a8c24-108">.NET Framework 版本3.0 和3.5 使用 .NET Framework 版本2.0 承载接口，不会引入任何承载功能。</span><span class="sxs-lookup"><span data-stu-id="a8c24-108">The .NET Framework versions 3.0 and 3.5 use the .NET Framework version 2.0 hosting interfaces, and do not introduce any hosting features.</span></span>  
  
 <span data-ttu-id="a8c24-109">.NET Framework 4 宿主接口取代了 .NET Framework 2.0 接口。</span><span class="sxs-lookup"><span data-stu-id="a8c24-109">The .NET Framework 4 hosting interfaces supersede the .NET Framework 2.0 interfaces.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="a8c24-110">本节内容</span><span class="sxs-lookup"><span data-stu-id="a8c24-110">In This Section</span></span>  

 [<span data-ttu-id="a8c24-111">弃用的 CLR 承载接口和 Coclass</span><span class="sxs-lookup"><span data-stu-id="a8c24-111">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="a8c24-112">介绍 .NET Framework 版本1.0 和1.1 中引入的托管接口。</span><span class="sxs-lookup"><span data-stu-id="a8c24-112">Describes the hosting interfaces introduced in the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="a8c24-113">CLR 承载接口</span><span class="sxs-lookup"><span data-stu-id="a8c24-113">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)  
 <span data-ttu-id="a8c24-114">介绍 .NET Framework 版本2.0 中引入的托管接口。</span><span class="sxs-lookup"><span data-stu-id="a8c24-114">Describes the hosting interfaces introduced in the .NET Framework version 2.0.</span></span>  
  
 [<span data-ttu-id="a8c24-115">.NET Framework 4 和 4.5 中添加的 CLR 承载接口</span><span class="sxs-lookup"><span data-stu-id="a8c24-115">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 <span data-ttu-id="a8c24-116">介绍 .NET Framework 4 中引入的托管接口。</span><span class="sxs-lookup"><span data-stu-id="a8c24-116">Describes the hosting interfaces introduced in the .NET Framework 4.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a8c24-117">相关章节</span><span class="sxs-lookup"><span data-stu-id="a8c24-117">Related Sections</span></span>  

 [<span data-ttu-id="a8c24-118">承载组件类</span><span class="sxs-lookup"><span data-stu-id="a8c24-118">Hosting Coclasses</span></span>](hosting-coclasses.md)  
  
 [<span data-ttu-id="a8c24-119">弃用的 CLR 承载函数</span><span class="sxs-lookup"><span data-stu-id="a8c24-119">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)  
  
 [<span data-ttu-id="a8c24-120">承载枚举</span><span class="sxs-lookup"><span data-stu-id="a8c24-120">Hosting Enumerations</span></span>](hosting-enumerations.md)  
  
 [<span data-ttu-id="a8c24-121">承载结构</span><span class="sxs-lookup"><span data-stu-id="a8c24-121">Hosting Structures</span></span>](hosting-structures.md)  
  
 [<span data-ttu-id="a8c24-122">承载</span><span class="sxs-lookup"><span data-stu-id="a8c24-122">Hosting</span></span>](index.md)  
  
 <span data-ttu-id="a8c24-123">[运行时主机](/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a8c24-123">[Runtime Hosts](/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))</span></span>
