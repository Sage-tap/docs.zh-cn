---
description: 了解详细信息： BC36810：编译项目中的 XML 架构时发生错误
title: 编译项目中的 XML 架构时发生错误
ms.date: 07/20/2015
f1_keywords:
- bc36810
- vbc36810
helpviewer_keywords:
- BC36810
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
ms.openlocfilehash: 78e88208c0d3df12e7bad8ab46b1d91bce559923
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796477"
---
# <a name="bc36810-errors-occurred-while-compiling-the-xml-schemas-in-the-project"></a><span data-ttu-id="13316-103">BC36810：编译项目中的 XML 架构时发生错误</span><span class="sxs-lookup"><span data-stu-id="13316-103">BC36810: Errors occurred while compiling the XML schemas in the project</span></span>

<span data-ttu-id="13316-104">编译项目中的 XML 架构时发生错误。</span><span class="sxs-lookup"><span data-stu-id="13316-104">Errors occurred while compiling the XML schemas in the project.</span></span> <span data-ttu-id="13316-105">因此，XML IntelliSense 不可用。</span><span class="sxs-lookup"><span data-stu-id="13316-105">Because of this, XML IntelliSense is not available.</span></span>

 <span data-ttu-id="13316-106">XML 架构定义中存在一个错误， (项目中包含的 XSD) 架构。</span><span class="sxs-lookup"><span data-stu-id="13316-106">There is an error in an XML Schema Definition (XSD) schema included in the project.</span></span> <span data-ttu-id="13316-107">如果添加的 XSD 架构 ( .xsd) 文件与项目的现有 XSD 架构集冲突，则会发生此错误。</span><span class="sxs-lookup"><span data-stu-id="13316-107">This error occurs when you add an XSD schema (.xsd) file that conflicts with the existing XSD schema set for the project.</span></span>

 <span data-ttu-id="13316-108">**错误 ID：** BC36810</span><span class="sxs-lookup"><span data-stu-id="13316-108">**Error ID:** BC36810</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="13316-109">更正此错误</span><span class="sxs-lookup"><span data-stu-id="13316-109">To correct this error</span></span>

- <span data-ttu-id="13316-110">双击 " **错误列表** " 窗口中的警告。</span><span class="sxs-lookup"><span data-stu-id="13316-110">Double-click the warning in the **Errors List** window.</span></span> <span data-ttu-id="13316-111">Visual Basic 将转到 XSD 文件中作为警告源的位置。</span><span class="sxs-lookup"><span data-stu-id="13316-111">Visual Basic will take you to the location in the XSD file that is the source of the warning.</span></span> <span data-ttu-id="13316-112">更正 XSD 架构中的错误。</span><span class="sxs-lookup"><span data-stu-id="13316-112">Correct the error in the XSD schema.</span></span>

- <span data-ttu-id="13316-113">确保所有必需的 XSD 架构 ( .xsd) 文件包含在项目中。</span><span class="sxs-lookup"><span data-stu-id="13316-113">Ensure that all required XSD schema (.xsd) files are included in the project.</span></span> <span data-ttu-id="13316-114">可能需要在 "**项目**" 菜单上单击 "**显示所有文件**" 才能在 **解决方案资源管理器** 中查看 .xsd 文件。</span><span class="sxs-lookup"><span data-stu-id="13316-114">You may need to click **Show All Files** on the **Project** menu to see your .xsd files in **Solution Explorer**.</span></span> <span data-ttu-id="13316-115">右键单击 .xsd 文件，然后单击 " **包括在项目中** " 以在项目中包含该文件。</span><span class="sxs-lookup"><span data-stu-id="13316-115">Right-click an .xsd file and then click **Include In Project** to include the file in your project.</span></span>

- <span data-ttu-id="13316-116">如果你使用的是 XML 到架构向导，则如果你从同一源推导多个架构，则可能会发生此错误。</span><span class="sxs-lookup"><span data-stu-id="13316-116">If you are using the XML to Schema Wizard, this error can occur if you infer schemas more than one time from the same source.</span></span> <span data-ttu-id="13316-117">在这种情况下，您可以从项目中删除现有的 XSD 架构文件，添加一个新的 XML 到架构项模板，然后提供项目的所有适用 XML 源的 XML 到架构向导。</span><span class="sxs-lookup"><span data-stu-id="13316-117">In this case, you can remove the existing XSD schema files from the project, add a new XML to Schema item template, and then provide the XML to Schema Wizard with all the applicable XML sources for your project.</span></span>

- <span data-ttu-id="13316-118">如果 XSD 架构中未发现任何错误，则 XML 编译器可能没有足够的信息来提供详细的错误消息。</span><span class="sxs-lookup"><span data-stu-id="13316-118">If no error is identified in your XSD schema, the XML compiler may not have enough information to provide a detailed error message.</span></span> <span data-ttu-id="13316-119">如果确保你的项目中包含的 .xsd 文件的 XML 命名空间与在 Visual Studio 中为 XML 架构集标识的 XML 命名空间相匹配，则你可能能够获取更详细的错误信息。</span><span class="sxs-lookup"><span data-stu-id="13316-119">You may be able to get more detailed error information if you ensure that the XML namespaces for the .xsd files included in your project match the XML namespaces identified for the XML Schema set in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="13316-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="13316-120">See also</span></span>

- [<span data-ttu-id="13316-121">错误列表窗口</span><span class="sxs-lookup"><span data-stu-id="13316-121">Error List Window</span></span>](/visualstudio/ide/reference/error-list-window)
- [<span data-ttu-id="13316-122">XML</span><span class="sxs-lookup"><span data-stu-id="13316-122">XML</span></span>](../../programming-guide/language-features/xml/index.md)
