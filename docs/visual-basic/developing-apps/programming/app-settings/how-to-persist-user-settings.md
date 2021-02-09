---
description: 详细了解：操作说明：在 Visual Basic 中保存用户设置
title: 如何：永久保存用户设置
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], persisting user settings
- persistence [Visual Basic], persisting user settings [Visual Basic]
- user settings [Visual Basic], persisting
ms.assetid: 0e5e6415-b6e2-4602-9be0-a65fa167d007
ms.openlocfilehash: 43ca82442678356afacb8e05149a35d485603059
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797830"
---
# <a name="how-to-persist-user-settings-in-visual-basic"></a><span data-ttu-id="32780-103">如何：在 Visual Basic 中保存用户设置</span><span class="sxs-lookup"><span data-stu-id="32780-103">How to: Persist User Settings in Visual Basic</span></span>

<span data-ttu-id="32780-104">可以使用 `My.Settings.Save` 方法来保存对用户设置的更改。</span><span class="sxs-lookup"><span data-stu-id="32780-104">You can use the `My.Settings.Save` method to persist changes to the user settings.</span></span>  
  
 <span data-ttu-id="32780-105">通常情况下，将应用程序设计为在应用程序关闭时保存用户设置的更改。</span><span class="sxs-lookup"><span data-stu-id="32780-105">Typically, applications are designed to persist the changes to the user settings when the application shuts down.</span></span> <span data-ttu-id="32780-106">这是因为保存设置需要几秒钟，具体取决于多种因素。</span><span class="sxs-lookup"><span data-stu-id="32780-106">This is because saving the settings can take, depending on several factors, several seconds.</span></span>  
  
 <span data-ttu-id="32780-107">有关详细信息，请参阅 [My.Settings 对象](../../../language-reference/objects/my-settings-object.md)。</span><span class="sxs-lookup"><span data-stu-id="32780-107">For more information, see [My.Settings Object](../../../language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="32780-108">虽然可以在运行时更改并保存用户范围设置的值，但是应用程序范围设置是只读的，不能以编程方式进行更改。</span><span class="sxs-lookup"><span data-stu-id="32780-108">Although you can change and save the values of user-scope settings at run time, application-scope settings are read-only and cannot be changed programmatically.</span></span> <span data-ttu-id="32780-109">可以在创建应用程序时通过 **项目设计器**，或者编辑应用程序的配置文件来更改应用程序范围设置。</span><span class="sxs-lookup"><span data-stu-id="32780-109">You can change application-scope settings when creating the application, through the **Project Designer**, or by editing the application's configuration file.</span></span> <span data-ttu-id="32780-110">有关详细信息，请参阅[管理应用程序设置 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)。</span><span class="sxs-lookup"><span data-stu-id="32780-110">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="32780-111">示例</span><span class="sxs-lookup"><span data-stu-id="32780-111">Example</span></span>  

 <span data-ttu-id="32780-112">本示例更改 `LastChanged` 用户设置的值，并通过调用 `My.Settings.Save` 方法来保存此更改。</span><span class="sxs-lookup"><span data-stu-id="32780-112">This example changes the value of the `LastChanged` user setting and saves that change by calling the `My.Settings.Save` method.</span></span>  
  
 [!code-vb[VbVbalrMyResources#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#5)]  
  
 <span data-ttu-id="32780-113">若要使用本示例，应用程序必须具有类型为 `Date` 的 `LastChanged` 用户设置。</span><span class="sxs-lookup"><span data-stu-id="32780-113">For this example to work, your application must have a `LastChanged` user setting, of type `Date`.</span></span> <span data-ttu-id="32780-114">有关详细信息，请参阅[管理应用程序设置 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)。</span><span class="sxs-lookup"><span data-stu-id="32780-114">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32780-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="32780-115">See also</span></span>

- [<span data-ttu-id="32780-116">My.Settings 对象</span><span class="sxs-lookup"><span data-stu-id="32780-116">My.Settings Object</span></span>](../../../language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="32780-117">如何：在 Visual Basic 中读取应用程序设置</span><span class="sxs-lookup"><span data-stu-id="32780-117">How to: Read Application Settings in Visual Basic</span></span>](how-to-read-application-settings.md)
- [<span data-ttu-id="32780-118">如何：在 Visual Basic 中更改用户设置</span><span class="sxs-lookup"><span data-stu-id="32780-118">How to: Change User Settings in Visual Basic</span></span>](how-to-change-user-settings.md)
- [<span data-ttu-id="32780-119">如何：在 Visual Basic 中为用户设置创建属性网格</span><span class="sxs-lookup"><span data-stu-id="32780-119">How to: Create Property Grids for User Settings in Visual Basic</span></span>](how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="32780-120">管理应用程序设置 (.NET)</span><span class="sxs-lookup"><span data-stu-id="32780-120">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
