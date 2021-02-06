---
description: 了解详细信息： My .Resources 对象
title: My.Resources 对象
ms.date: 07/20/2015
f1_keywords:
- My.Resources
- My.Resources.MyResources.ResourceManager
- My.Resources.MyResources.Culture
helpviewer_keywords:
- My.Resources object
ms.assetid: 34c3f2dc-7b87-432c-9d5f-17ea666bb266
ms.openlocfilehash: ecd8e79aacea85080dc341ae36b362a595893034
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640623"
---
# <a name="myresources-object"></a><span data-ttu-id="ae102-103">My.Resources 对象</span><span class="sxs-lookup"><span data-stu-id="ae102-103">My.Resources Object</span></span>

<span data-ttu-id="ae102-104">提供用于访问应用程序资源的属性和类。</span><span class="sxs-lookup"><span data-stu-id="ae102-104">Provides properties and classes for accessing the application's resources.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae102-105">备注</span><span class="sxs-lookup"><span data-stu-id="ae102-105">Remarks</span></span>  

 <span data-ttu-id="ae102-106">`My.Resources`对象提供对应用程序资源的访问权限，并允许您为应用程序动态检索资源。</span><span class="sxs-lookup"><span data-stu-id="ae102-106">The `My.Resources` object provides access to the application's resources and lets you dynamically retrieve resources for your application.</span></span> <span data-ttu-id="ae102-107">有关详细信息，请参阅 [ ( .net) 管理应用程序资源 ](/visualstudio/ide/managing-application-resources-dotnet)。</span><span class="sxs-lookup"><span data-stu-id="ae102-107">For more information, see [Managing Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
 <span data-ttu-id="ae102-108">`My.Resources` 对象只公开全局资源。</span><span class="sxs-lookup"><span data-stu-id="ae102-108">The `My.Resources` object exposes only global resources.</span></span> <span data-ttu-id="ae102-109">它不提供对与窗体关联的资源文件的访问权限。</span><span class="sxs-lookup"><span data-stu-id="ae102-109">It does not provide access to resource files associated with forms.</span></span> <span data-ttu-id="ae102-110">必须从窗体访问窗体资源。</span><span class="sxs-lookup"><span data-stu-id="ae102-110">You must access the form resources from the form.</span></span>  
  
 <span data-ttu-id="ae102-111">可以从对象访问应用程序的区域性特定资源文件 `My.Resources` 。</span><span class="sxs-lookup"><span data-stu-id="ae102-111">You can access the application's culture-specific resource files from the `My.Resources` object.</span></span> <span data-ttu-id="ae102-112">默认情况下， `My.Resources` 对象从与属性中的区域性匹配的资源文件中查找资源 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A> 。</span><span class="sxs-lookup"><span data-stu-id="ae102-112">By default, the `My.Resources` object looks up resources from the resource file that matches the culture in the <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A> property.</span></span> <span data-ttu-id="ae102-113">不过，您可以重写此行为，并指定要用于资源的特定区域性。</span><span class="sxs-lookup"><span data-stu-id="ae102-113">However, you can override this behavior and specify a particular culture to use for the resources.</span></span> <span data-ttu-id="ae102-114">有关详细信息，请参阅[桌面应用中的资源](../../../framework/resources/index.md)。</span><span class="sxs-lookup"><span data-stu-id="ae102-114">For more information, see [Resources in Desktop Apps](../../../framework/resources/index.md).</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ae102-115">属性</span><span class="sxs-lookup"><span data-stu-id="ae102-115">Properties</span></span>  

 <span data-ttu-id="ae102-116">对象的属性 `My.Resources` 提供对应用程序资源的只读访问。</span><span class="sxs-lookup"><span data-stu-id="ae102-116">The properties of the `My.Resources` object provide read-only access to your application's resources.</span></span> <span data-ttu-id="ae102-117">若要添加或删除资源，请使用 " **项目设计器**"。</span><span class="sxs-lookup"><span data-stu-id="ae102-117">To add or remove resources, use the **Project Designer**.</span></span> <span data-ttu-id="ae102-118">您可以使用资源中心访问通过 **项目设计器** 添加 `My.Resources.` *的资源*。</span><span class="sxs-lookup"><span data-stu-id="ae102-118">You can access resources added through the **Project Designer** by using `My.Resources.`*resourceName*.</span></span>  
  
 <span data-ttu-id="ae102-119">还可以通过在 **解决方案资源管理器** 中选择项目，然后在 "**项目**" 菜单中单击 "**添加新项**" 或 "**添加现有项**"，来添加或删除资源文件。</span><span class="sxs-lookup"><span data-stu-id="ae102-119">You can also add or remove resource files by selecting your project in **Solution Explorer** and clicking **Add New Item** or **Add Existing Item** from the **Project** menu.</span></span> <span data-ttu-id="ae102-120">你可以使用 resourceFileName 资源中心访问以这种方式添加的资源 `My.Resources.`  `.` 。</span><span class="sxs-lookup"><span data-stu-id="ae102-120">You can access resources added in this manner by using `My.Resources.`*resourceFileName*`.`*resourceName*.</span></span>  
  
 <span data-ttu-id="ae102-121">每个资源都有一个名称、类别和值，这些资源设置决定了访问资源的属性在对象中的显示方式 `My.Resources` 。</span><span class="sxs-lookup"><span data-stu-id="ae102-121">Each resource has a name, category, and value, and these resource settings determine how the property to access the resource appears in the `My.Resources` object.</span></span> <span data-ttu-id="ae102-122">对于在 **项目设计器** 中添加的资源：</span><span class="sxs-lookup"><span data-stu-id="ae102-122">For resources added in the **Project Designer**:</span></span>  
  
- <span data-ttu-id="ae102-123">名称确定属性的名称。</span><span class="sxs-lookup"><span data-stu-id="ae102-123">The name determines the name of the property,</span></span>  
  
- <span data-ttu-id="ae102-124">资源数据是属性的值。</span><span class="sxs-lookup"><span data-stu-id="ae102-124">The resource data is the value of the property,</span></span>  
  
- <span data-ttu-id="ae102-125">类别确定属性的类型：</span><span class="sxs-lookup"><span data-stu-id="ae102-125">The category determines the type of the property:</span></span>  
  
|<span data-ttu-id="ae102-126">类别</span><span class="sxs-lookup"><span data-stu-id="ae102-126">Category</span></span>|<span data-ttu-id="ae102-127">属性数据类型</span><span class="sxs-lookup"><span data-stu-id="ae102-127">Property data type</span></span>|  
|---|---|  
|<span data-ttu-id="ae102-128">**字符串**</span><span class="sxs-lookup"><span data-stu-id="ae102-128">**Strings**</span></span>|[<span data-ttu-id="ae102-129">字符串</span><span class="sxs-lookup"><span data-stu-id="ae102-129">String</span></span>](../data-types/string-data-type.md)|  
|<span data-ttu-id="ae102-130">**映像**</span><span class="sxs-lookup"><span data-stu-id="ae102-130">**Images**</span></span>|<xref:System.Drawing.Bitmap>|  
|<span data-ttu-id="ae102-131">**图标**</span><span class="sxs-lookup"><span data-stu-id="ae102-131">**Icons**</span></span>|<xref:System.Drawing.Icon>|  
|<span data-ttu-id="ae102-132">**音频**</span><span class="sxs-lookup"><span data-stu-id="ae102-132">**Audio**</span></span>|<xref:System.IO.UnmanagedMemoryStream><br /><br /> <span data-ttu-id="ae102-133"><xref:System.IO.UnmanagedMemoryStream>类派生自 <xref:System.IO.Stream> 类，因此它可用于采用流的方法，例如 <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="ae102-133">The <xref:System.IO.UnmanagedMemoryStream> class derives from the <xref:System.IO.Stream> class, so it can be used with methods that take streams, such as the <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A> method.</span></span>|  
|<span data-ttu-id="ae102-134">**文件**</span><span class="sxs-lookup"><span data-stu-id="ae102-134">**Files**</span></span>|<span data-ttu-id="ae102-135">-   文本文件的[字符串](../data-types/string-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="ae102-135">-   [String](../data-types/string-data-type.md) for text files.</span></span><br /><span data-ttu-id="ae102-136">-   <xref:System.Drawing.Bitmap> 用于图像文件。</span><span class="sxs-lookup"><span data-stu-id="ae102-136">-   <xref:System.Drawing.Bitmap> for image files.</span></span><br /><span data-ttu-id="ae102-137">-   <xref:System.Drawing.Icon> 图标文件。</span><span class="sxs-lookup"><span data-stu-id="ae102-137">-   <xref:System.Drawing.Icon> for icon files.</span></span><br /><span data-ttu-id="ae102-138">-   <xref:System.IO.UnmanagedMemoryStream> 用于声音文件。</span><span class="sxs-lookup"><span data-stu-id="ae102-138">-   <xref:System.IO.UnmanagedMemoryStream> for sound files.</span></span>|  
|<span data-ttu-id="ae102-139">**其他**</span><span class="sxs-lookup"><span data-stu-id="ae102-139">**Other**</span></span>|<span data-ttu-id="ae102-140">由设计器的 **类型** 列中的信息确定。</span><span class="sxs-lookup"><span data-stu-id="ae102-140">Determined by the information in the designer's **Type** column.</span></span>|  
  
## <a name="classes"></a><span data-ttu-id="ae102-141">类</span><span class="sxs-lookup"><span data-stu-id="ae102-141">Classes</span></span>  

 <span data-ttu-id="ae102-142">`My.Resources`对象将每个资源文件作为具有共享属性的类公开。</span><span class="sxs-lookup"><span data-stu-id="ae102-142">The `My.Resources` object exposes each resource file as a class with shared properties.</span></span> <span data-ttu-id="ae102-143">类名称与资源文件的名称相同。</span><span class="sxs-lookup"><span data-stu-id="ae102-143">The class name is the same as the name of the resource file.</span></span> <span data-ttu-id="ae102-144">如上一节所述，资源文件中的资源作为类中的属性公开。</span><span class="sxs-lookup"><span data-stu-id="ae102-144">As described in the previous section, the resources in a resource file are exposed as properties in the class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae102-145">示例</span><span class="sxs-lookup"><span data-stu-id="ae102-145">Example</span></span>  

 <span data-ttu-id="ae102-146">此示例将窗体的标题设置为 `Form1Title` 应用程序资源文件中名为的字符串资源。</span><span class="sxs-lookup"><span data-stu-id="ae102-146">This example sets the title of a form to the string resource named `Form1Title` in the application resource file.</span></span> <span data-ttu-id="ae102-147">要使此示例正常运行，应用程序的资源文件中必须具有一个名为的字符串 `Form1Title` 。</span><span class="sxs-lookup"><span data-stu-id="ae102-147">For the example to work, the application must have a string named `Form1Title` in its resource file.</span></span>  
  
 [!code-vb[VbVbalrMyResources#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="ae102-148">示例</span><span class="sxs-lookup"><span data-stu-id="ae102-148">Example</span></span>  

 <span data-ttu-id="ae102-149">此示例将窗体的图标设置为 `Form1Icon` 存储在应用程序的资源文件中的名为的图标。</span><span class="sxs-lookup"><span data-stu-id="ae102-149">This example sets the icon of the form to the icon named `Form1Icon` that is stored in the application's resource file.</span></span> <span data-ttu-id="ae102-150">要使此示例正常运行，应用程序的资源文件中必须具有一个名为的图标 `Form1Icon` 。</span><span class="sxs-lookup"><span data-stu-id="ae102-150">For the example to work, the application must have an icon named `Form1Icon` in its resource file.</span></span>  
  
 [!code-vb[VbVbalrMyResources#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="ae102-151">示例</span><span class="sxs-lookup"><span data-stu-id="ae102-151">Example</span></span>  

 <span data-ttu-id="ae102-152">此示例将窗体的背景图像设置为 `Form1Background` 应用程序资源文件中名为的图像资源。</span><span class="sxs-lookup"><span data-stu-id="ae102-152">This example sets the background image of a form to the image resource named `Form1Background`, which is in the application resource file.</span></span> <span data-ttu-id="ae102-153">要使此示例正常运行，应用程序的资源文件中必须具有一个名为的映像资源 `Form1Background` 。</span><span class="sxs-lookup"><span data-stu-id="ae102-153">For this example to work, the application must have an image resource named `Form1Background` in its resource file.</span></span>  
  
 [!code-vb[VbVbalrMyResources#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="ae102-154">示例</span><span class="sxs-lookup"><span data-stu-id="ae102-154">Example</span></span>  

 <span data-ttu-id="ae102-155">此示例播放存储为 `Form1Greeting` 在应用程序的资源文件中名为的音频资源的声音。</span><span class="sxs-lookup"><span data-stu-id="ae102-155">This example plays the sound that is stored as an audio resource named `Form1Greeting` in the application's resource file.</span></span> <span data-ttu-id="ae102-156">要使此示例正常运行，应用程序的资源文件中必须具有一个名为的音频资源 `Form1Greeting` 。</span><span class="sxs-lookup"><span data-stu-id="ae102-156">For the example to work, the application must have an audio resource named `Form1Greeting` in its resource file.</span></span> <span data-ttu-id="ae102-157">`My.Computer.Audio.Play`方法仅可用于 Windows 窗体应用程序。</span><span class="sxs-lookup"><span data-stu-id="ae102-157">The `My.Computer.Audio.Play` method is available only for Windows Forms applications.</span></span>  
  
 [!code-vb[VbVbalrMyResources#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="ae102-158">示例</span><span class="sxs-lookup"><span data-stu-id="ae102-158">Example</span></span>  

 <span data-ttu-id="ae102-159">此示例检索应用程序的字符串资源的法语区域性版本。</span><span class="sxs-lookup"><span data-stu-id="ae102-159">This example retrieves the French-culture version of a  string resource of the application.</span></span> <span data-ttu-id="ae102-160">资源命名为 `Message` 。</span><span class="sxs-lookup"><span data-stu-id="ae102-160">The resource is named `Message`.</span></span> <span data-ttu-id="ae102-161">若要更改 `My.Resources` 对象使用的区域性，示例使用 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A> 。</span><span class="sxs-lookup"><span data-stu-id="ae102-161">To change the culture that the `My.Resources` object uses, the example uses <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A>.</span></span>  
  
 <span data-ttu-id="ae102-162">要使此示例正常运行，应用程序的资源文件中必须具有一个名为的字符串 `Message` ，应用程序应具有该资源文件的法语区域性版本 Resources.fr。</span><span class="sxs-lookup"><span data-stu-id="ae102-162">For this example to work, the application must have a string named `Message` in its resource file, and the application should have the French-culture version of that resource file, Resources.fr-FR.resx.</span></span> <span data-ttu-id="ae102-163">如果应用程序没有资源文件的法语区域性版本，则 `My.Resource` 对象将从默认区域性资源文件中检索资源。</span><span class="sxs-lookup"><span data-stu-id="ae102-163">If the application does not have the French-culture version of the resource file, the `My.Resource` object retrieves the resource from the default-culture resource file.</span></span>  
  
 [!code-vb[VbVbalrMyResources#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="ae102-164">请参阅</span><span class="sxs-lookup"><span data-stu-id="ae102-164">See also</span></span>

- [<span data-ttu-id="ae102-165">管理应用程序资源 (.NET)</span><span class="sxs-lookup"><span data-stu-id="ae102-165">Managing Application Resources (.NET)</span></span>](/visualstudio/ide/managing-application-resources-dotnet)
- [<span data-ttu-id="ae102-166">桌面应用中的资源</span><span class="sxs-lookup"><span data-stu-id="ae102-166">Resources in Desktop Apps</span></span>](../../../framework/resources/index.md)
