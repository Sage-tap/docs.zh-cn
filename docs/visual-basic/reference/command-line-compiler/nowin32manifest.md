---
description: 详细了解：-nowin32manifest (Visual Basic)
title: -nowin32manifest
ms.date: 03/13/2018
helpviewer_keywords:
- /nowin32manifest compiler option [Visual Basic]
- nowin32manifest compiler option [Visual Basic]
- -nowin32manifest compiler option [Visual Basic]
ms.assetid: c0528aae-83b3-4425-99f0-19448e9843e3
ms.openlocfilehash: 3aa07ee26e47d48da69f1d1b34c8ec4643b7422e
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100426715"
---
# <a name="-nowin32manifest-visual-basic"></a><span data-ttu-id="56fbe-103">-nowin32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="56fbe-103">-nowin32manifest (Visual Basic)</span></span>

<span data-ttu-id="56fbe-104">指示编译器不在可执行文件中嵌入任何应用程序清单。</span><span class="sxs-lookup"><span data-stu-id="56fbe-104">Instructs the compiler not to embed any application manifest into the executable file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56fbe-105">语法</span><span class="sxs-lookup"><span data-stu-id="56fbe-105">Syntax</span></span>  
  
```console  
-nowin32manifest  
```  
  
## <a name="remarks"></a><span data-ttu-id="56fbe-106">备注</span><span class="sxs-lookup"><span data-stu-id="56fbe-106">Remarks</span></span>  

 <span data-ttu-id="56fbe-107">使用此选项时，除非在 Win32 资源文件或以后的生成步骤中提供应用程序清单，否则应用程序会受到 Windows Vista 上虚拟化的影响。</span><span class="sxs-lookup"><span data-stu-id="56fbe-107">When this option is used, the application will be subject to virtualization on Windows Vista unless you provide an application manifest in a Win32 Resource file or during a later build step.</span></span> <span data-ttu-id="56fbe-108">有关虚拟化的详细信息，请参阅 [Windows Vista 上的 ClickOnce 部署](/visualstudio/deployment/clickonce-deployment-on-windows-vista)。</span><span class="sxs-lookup"><span data-stu-id="56fbe-108">For more information about virtualization, see [ClickOnce Deployment on Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span></span>  
  
 <span data-ttu-id="56fbe-109">有关清单创建的详细信息，请参阅 [-win32manifest (Visual Basic)](win32manifest.md)。</span><span class="sxs-lookup"><span data-stu-id="56fbe-109">For more information about manifest creation, see [-win32manifest (Visual Basic)](win32manifest.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56fbe-110">请参阅</span><span class="sxs-lookup"><span data-stu-id="56fbe-110">See also</span></span>

- [<span data-ttu-id="56fbe-111">Visual Basic 命令行编译器</span><span class="sxs-lookup"><span data-stu-id="56fbe-111">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="56fbe-112">“项目设计器”->“应用程序”页 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="56fbe-112">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
