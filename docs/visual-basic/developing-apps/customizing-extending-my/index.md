---
description: 详细了解：利用 Visual Basic 自定义项目并扩展 My 对象
title: 自定义项目并扩展 My 对象
ms.date: 07/20/2015
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: 06ca80b9-1192-4eb5-8537-8ef5edfb9be0
ms.openlocfilehash: 69a8bdff78fcfda03ab03ef89b7407fb230c17bf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775456"
---
# <a name="customizing-projects-and-extending-my-with-visual-basic"></a><span data-ttu-id="30c78-103">利用 Visual Basic 自定义项目并扩展 My 对象</span><span class="sxs-lookup"><span data-stu-id="30c78-103">Customizing Projects and Extending My with Visual Basic</span></span>

<span data-ttu-id="30c78-104">可以自定义项目模板以提供其他 `My` 对象。</span><span class="sxs-lookup"><span data-stu-id="30c78-104">You can customize project templates to provide additional `My` objects.</span></span> <span data-ttu-id="30c78-105">这样，其他开发人员便可以轻松查找和使用你的对象。</span><span class="sxs-lookup"><span data-stu-id="30c78-105">This makes it easy for other developers to find and use your objects.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="30c78-106">本节内容</span><span class="sxs-lookup"><span data-stu-id="30c78-106">In this section</span></span>

- [<span data-ttu-id="30c78-107">扩展 Visual Basic 中的 My 命名空间</span><span class="sxs-lookup"><span data-stu-id="30c78-107">Extending the My Namespace in Visual Basic</span></span>](extending-the-my-namespace.md)  
 <span data-ttu-id="30c78-108">介绍如何在 Visual Basic 中将自定义成员和值添加到 `My` 命名空间。</span><span class="sxs-lookup"><span data-stu-id="30c78-108">Describes how to add custom members and values to the `My` namespace in Visual Basic.</span></span>
- [<span data-ttu-id="30c78-109">打包和部署自定义 My 扩展</span><span class="sxs-lookup"><span data-stu-id="30c78-109">Packaging and Deploying Custom My Extensions</span></span>](packaging-and-deploying-custom-my-extensions.md)  
 <span data-ttu-id="30c78-110">介绍如何使用 Visual Studio 模板发布自定义 `My` 命名空间扩展。</span><span class="sxs-lookup"><span data-stu-id="30c78-110">Describes how to publish custom `My` namespace extensions by using Visual Studio templates.</span></span>
- [<span data-ttu-id="30c78-111">扩展 Visual Basic 应用程序模型</span><span class="sxs-lookup"><span data-stu-id="30c78-111">Extending the Visual Basic Application Model</span></span>](extending-the-visual-basic-application-model.md)  
 <span data-ttu-id="30c78-112">介绍如何通过替代 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> 类的成员来向应用程序模型指定自己的扩展。</span><span class="sxs-lookup"><span data-stu-id="30c78-112">Describes how to specify your own extensions to the application model by overriding members of the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> class.</span></span>
- [<span data-ttu-id="30c78-113">自定义 My 中可用的对象</span><span class="sxs-lookup"><span data-stu-id="30c78-113">Customizing Which Objects are Available in My</span></span>](customizing-which-objects-are-available-in-my.md)  
 <span data-ttu-id="30c78-114">介绍如何通过设置项目的 \_MYTYPE 条件编译常量来控制要启用的 `My` 对象。</span><span class="sxs-lookup"><span data-stu-id="30c78-114">Describes how to control which `My` objects are enabled by setting your project's \_MYTYPE conditional-compilation constant.</span></span>

## <a name="related-sections"></a><span data-ttu-id="30c78-115">相关章节</span><span class="sxs-lookup"><span data-stu-id="30c78-115">Related sections</span></span>

- [<span data-ttu-id="30c78-116">使用 My 开发</span><span class="sxs-lookup"><span data-stu-id="30c78-116">Development with My</span></span>](../development-with-my/index.md)  
 <span data-ttu-id="30c78-117">介绍不同项目类型中默认可用的 `My` 对象。</span><span class="sxs-lookup"><span data-stu-id="30c78-117">Describes which `My` objects are available in different project types by default.</span></span>
- [<span data-ttu-id="30c78-118">Visual Basic 应用程序模型概述</span><span class="sxs-lookup"><span data-stu-id="30c78-118">Overview of the Visual Basic Application Model</span></span>](../development-with-my/overview-of-the-visual-basic-application-model.md)  
 <span data-ttu-id="30c78-119">介绍 Visual Basic 中用于控制 Windows 窗体应用程序行为的模型。</span><span class="sxs-lookup"><span data-stu-id="30c78-119">Describes Visual Basic's model for controlling the behavior of Windows Forms applications.</span></span>
- [<span data-ttu-id="30c78-120">My 对项目类型的依赖方式</span><span class="sxs-lookup"><span data-stu-id="30c78-120">How My Depends on Project Type</span></span>](../development-with-my/how-my-depends-on-project-type.md)  
 <span data-ttu-id="30c78-121">介绍不同项目类型中默认可用的 `My` 对象。</span><span class="sxs-lookup"><span data-stu-id="30c78-121">Describes which `My` objects are available in different project types by default.</span></span>
- [<span data-ttu-id="30c78-122">条件编译</span><span class="sxs-lookup"><span data-stu-id="30c78-122">Conditional Compilation</span></span>](../../programming-guide/program-structure/conditional-compilation.md)  
 <span data-ttu-id="30c78-123">讨论编译器如何使用条件编译来选择特定代码部分，以便编译和排除其他部分。</span><span class="sxs-lookup"><span data-stu-id="30c78-123">Discusses how the compiler uses conditional-compilation to select particular sections of code to compile and exclude other sections.</span></span>
- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>  
 <span data-ttu-id="30c78-124">介绍提供与当前应用程序相关的属性、方法和事件的 `My` 对象。</span><span class="sxs-lookup"><span data-stu-id="30c78-124">Describes the `My` object that provides properties, methods, and events related to the current application.</span></span>

## <a name="see-also"></a><span data-ttu-id="30c78-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="30c78-125">See also</span></span>

- [<span data-ttu-id="30c78-126">使用 Visual Basic 开发应用程序</span><span class="sxs-lookup"><span data-stu-id="30c78-126">Developing Applications with Visual Basic</span></span>](../index.md)
