---
description: 详细了解：操作说明：在 Visual Basic 中为用户设置创建属性网格
title: 如何：创建用户设置的属性网格
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], creating property grids for user settings
- user settings [Visual Basic], creating property grids
- property grids [Visual Basic], creating for user settings
- property grids
ms.assetid: b0bc737e-50d1-43d1-a6df-268db6e6f91c
ms.openlocfilehash: 19523f712207cac225ccf68e02e338a9e76fe358
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797843"
---
# <a name="how-to-create-property-grids-for-user-settings-in-visual-basic"></a><span data-ttu-id="94749-103">如何：在 Visual Basic 中创建用户设置的属性网格</span><span class="sxs-lookup"><span data-stu-id="94749-103">How to: Create Property Grids for User Settings in Visual Basic</span></span>

<span data-ttu-id="94749-104">可通过使用 `My.Settings` 对象的用户设置属性填充 <xref:System.Windows.Forms.PropertyGrid> 控件，创建用户设置的属性网格。</span><span class="sxs-lookup"><span data-stu-id="94749-104">You can create a property grid for user settings by populating a <xref:System.Windows.Forms.PropertyGrid> control with the user setting properties of the `My.Settings` object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="94749-105">若要使此示例正确运行，应用程序必须配置用户设置。</span><span class="sxs-lookup"><span data-stu-id="94749-105">In order for this example to work, your application must have its user settings configured.</span></span> <span data-ttu-id="94749-106">有关详细信息，请参阅[管理应用程序设置 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)。</span><span class="sxs-lookup"><span data-stu-id="94749-106">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
 <span data-ttu-id="94749-107">`My.Settings` 对象将每个设置公开为一个属性。</span><span class="sxs-lookup"><span data-stu-id="94749-107">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="94749-108">属性名称就是设置的名称，属性类型就是设置类型。</span><span class="sxs-lookup"><span data-stu-id="94749-108">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="94749-109">设置的“范围”确定属性是否为只读；“应用程序”范围设置的属性为只读，而“用户”范围设置的属性为读写。  </span><span class="sxs-lookup"><span data-stu-id="94749-109">The setting's **Scope** determines if the property is read-only; the property for an **Application**-scope setting is read-only, while the property for a **User**-scope setting is read-write.</span></span> <span data-ttu-id="94749-110">有关详细信息，请参阅 [My.Settings 对象](../../../language-reference/objects/my-settings-object.md)。</span><span class="sxs-lookup"><span data-stu-id="94749-110">For more information, see [My.Settings Object](../../../language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="94749-111">不能在运行时更改或保存应用程序范围设置的值。</span><span class="sxs-lookup"><span data-stu-id="94749-111">You cannot change or save the values of application-scope settings at run time.</span></span> <span data-ttu-id="94749-112">只有在创建应用程序（通过“项目设计器”）或编辑应用程序的配置文件时才能更改应用程序范围设置。</span><span class="sxs-lookup"><span data-stu-id="94749-112">Application-scope settings can be changed only when creating the application (through the **Project Designer**) or by editing the application's configuration file.</span></span> <span data-ttu-id="94749-113">有关详细信息，请参阅[管理应用程序设置 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)。</span><span class="sxs-lookup"><span data-stu-id="94749-113">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
 <span data-ttu-id="94749-114">此示例使用 <xref:System.Windows.Forms.PropertyGrid> 控件访问 `My.Settings` 对象的用户设置属性。</span><span class="sxs-lookup"><span data-stu-id="94749-114">This example uses a <xref:System.Windows.Forms.PropertyGrid> control to access the user-setting properties of the `My.Settings` object.</span></span> <span data-ttu-id="94749-115">默认情况下，<xref:System.Windows.Forms.PropertyGrid> 显示 `My.Settings` 对象的所有属性。</span><span class="sxs-lookup"><span data-stu-id="94749-115">By default, the <xref:System.Windows.Forms.PropertyGrid> shows all the properties of the `My.Settings` object.</span></span> <span data-ttu-id="94749-116">但是，用户设置属性具有 <xref:System.Configuration.UserScopedSettingAttribute> 特性。</span><span class="sxs-lookup"><span data-stu-id="94749-116">However, the user-setting properties have the <xref:System.Configuration.UserScopedSettingAttribute> attribute.</span></span> <span data-ttu-id="94749-117">此示例将 <xref:System.Windows.Forms.PropertyGrid> 的 <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> 属性设置为 <xref:System.Configuration.UserScopedSettingAttribute>，以仅显示用户设置属性。</span><span class="sxs-lookup"><span data-stu-id="94749-117">This example sets the <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> property of the <xref:System.Windows.Forms.PropertyGrid> to <xref:System.Configuration.UserScopedSettingAttribute> to display only the user-setting properties.</span></span>  
  
### <a name="to-add-a-user-setting-property-grid"></a><span data-ttu-id="94749-118">添加用户设置属性网格</span><span class="sxs-lookup"><span data-stu-id="94749-118">To add a user setting property grid</span></span>  
  
1. <span data-ttu-id="94749-119">将“PropertyGrid”控件从“工具箱”添加到应用程序的设计图面上（假定此处为 `Form1`）。</span><span class="sxs-lookup"><span data-stu-id="94749-119">Add the **PropertyGrid** control from the **Toolbox** to the design surface for your application, assumed here to be `Form1`.</span></span>  
  
     <span data-ttu-id="94749-120">属性网格控件的默认名称为 `PropertyGrid1`。</span><span class="sxs-lookup"><span data-stu-id="94749-120">The default name of the property-grid control is `PropertyGrid1`.</span></span>  
  
2. <span data-ttu-id="94749-121">双击 `Form1` 的设计图面打开窗体加载事件处理程序的代码。</span><span class="sxs-lookup"><span data-stu-id="94749-121">Double-click the design surface for `Form1` to open the code for the form-load event handler.</span></span>  
  
3. <span data-ttu-id="94749-122">将 `My.Settings` 对象设置为属性网格的选定对象。</span><span class="sxs-lookup"><span data-stu-id="94749-122">Set the `My.Settings` object as the selected object for the property grid.</span></span>  
  
     [!code-vb[VbVbalrMyResources#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#11)]  
  
4. <span data-ttu-id="94749-123">将属性网格配置为只显示用户设置。</span><span class="sxs-lookup"><span data-stu-id="94749-123">Configure the property grid to show only the user settings.</span></span>  
  
     [!code-vb[VbVbalrMyResources#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#12)]  
  
    > [!NOTE]
    > <span data-ttu-id="94749-124">若要只显示应用程序范围设置，请使用 <xref:System.Configuration.ApplicationScopedSettingAttribute> 特性而不是 <xref:System.Configuration.UserScopedSettingAttribute>。</span><span class="sxs-lookup"><span data-stu-id="94749-124">To show only the application-scope settings, use the <xref:System.Configuration.ApplicationScopedSettingAttribute> attribute instead of  <xref:System.Configuration.UserScopedSettingAttribute>.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="94749-125">可靠编程</span><span class="sxs-lookup"><span data-stu-id="94749-125">Robust Programming</span></span>  

 <span data-ttu-id="94749-126">应用程序在关闭时会保存用户设置。</span><span class="sxs-lookup"><span data-stu-id="94749-126">The application saves the user settings when the application shuts down.</span></span> <span data-ttu-id="94749-127">若要立即保存设置，请调用 `My.Settings.Save` 方法。</span><span class="sxs-lookup"><span data-stu-id="94749-127">To save the settings immediately, call the `My.Settings.Save` method.</span></span> <span data-ttu-id="94749-128">有关详细信息，请参阅[如何：在 Visual Basic 中保存用户设置](how-to-persist-user-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="94749-128">For more information, see [How to: Persist User Settings in Visual Basic](how-to-persist-user-settings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94749-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="94749-129">See also</span></span>

- [<span data-ttu-id="94749-130">My.Settings 对象</span><span class="sxs-lookup"><span data-stu-id="94749-130">My.Settings Object</span></span>](../../../language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="94749-131">如何：在 Visual Basic 中读取应用程序设置</span><span class="sxs-lookup"><span data-stu-id="94749-131">How to: Read Application Settings in Visual Basic</span></span>](how-to-read-application-settings.md)
- [<span data-ttu-id="94749-132">如何：在 Visual Basic 中更改用户设置</span><span class="sxs-lookup"><span data-stu-id="94749-132">How to: Change User Settings in Visual Basic</span></span>](how-to-change-user-settings.md)
- [<span data-ttu-id="94749-133">如何：在 Visual Basic 中暂留用户设置</span><span class="sxs-lookup"><span data-stu-id="94749-133">How to: Persist User Settings in Visual Basic</span></span>](how-to-persist-user-settings.md)
- [<span data-ttu-id="94749-134">管理应用程序设置 (.NET)</span><span class="sxs-lookup"><span data-stu-id="94749-134">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
