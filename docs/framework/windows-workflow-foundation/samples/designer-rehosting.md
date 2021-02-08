---
description: 了解详细信息：设计器重新承载
title: 重新承载设计器
ms.date: 03/30/2017
ms.assetid: b676ad31-5f64-4d84-9a36-b4d7113a2f4d
ms.openlocfilehash: 84401ba7cfc2b5515a9dcfda36289893e55660e2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792526"
---
# <a name="designer-rehosting"></a><span data-ttu-id="8445e-103">重新承载设计器</span><span class="sxs-lookup"><span data-stu-id="8445e-103">Designer Rehosting</span></span>

<span data-ttu-id="8445e-104">设计器重新承载是一个常用方案，它是指在自定义应用程序内部承载工作流设计画布。</span><span class="sxs-lookup"><span data-stu-id="8445e-104">Designer rehosting is a common scenario that refers to hosting the workflow design canvas inside of a custom application.</span></span> <span data-ttu-id="8445e-105">Visual Studio 是大多数人所熟知的承载应用程序，然而在很多方案中，应用程序中的工作流设计器可能会很有用：</span><span class="sxs-lookup"><span data-stu-id="8445e-105">The hosting application most people are familiar with is Visual Studio, however there are a number of scenarios where showing the workflow designer in an application may be useful:</span></span>  
  
- <span data-ttu-id="8445e-106">监视应用程序（允许最终用户直观地查看进程以及有关进程的运行时数据，例如，当前活动状态、聚合执行时间数据或其他关于工作流实例的信息）。</span><span class="sxs-lookup"><span data-stu-id="8445e-106">Monitoring applications (allowing an end user to visualize the process, as well as runtime data about the process such as the currently active state, aggregate execution time data, or other information about an instance of the workflow).</span></span>  
  
- <span data-ttu-id="8445e-107">允许用户使用有限的活动集合自定义进程的应用程序。</span><span class="sxs-lookup"><span data-stu-id="8445e-107">Applications that allow a user to customize the process with a limited set of activities.</span></span>  
  
 <span data-ttu-id="8445e-108">为了支持这些类型的应用程序，.NET Framework 内附带了工作流设计器，它可以在 WPF 应用程序内或在具有适当的 WPF 承载编码的 WinForms 应用程序内承载。</span><span class="sxs-lookup"><span data-stu-id="8445e-108">To support these types of applications, the workflow designer ships inside the .NET Framework, and can be hosted inside a WPF application, or in a WinForms application with the appropriate WPF hosting code.</span></span> <span data-ttu-id="8445e-109">此示例演示：</span><span class="sxs-lookup"><span data-stu-id="8445e-109">This sample demonstrates:</span></span>  
  
- <span data-ttu-id="8445e-110">重新承载 WF 设计器。</span><span class="sxs-lookup"><span data-stu-id="8445e-110">Rehosting the WF designer.</span></span>  
  
- <span data-ttu-id="8445e-111">使用重新承载的工具箱和属性网格。</span><span class="sxs-lookup"><span data-stu-id="8445e-111">Using the rehosted toolbox and property grid as well.</span></span>  
  
## <a name="rehosting-the-designer"></a><span data-ttu-id="8445e-112">重新承载设计器</span><span class="sxs-lookup"><span data-stu-id="8445e-112">Rehosting the designer</span></span>  

 <span data-ttu-id="8445e-113">此示例演示如何创建 WPF 布局以包含在以下网格布局中可见的设计器（因空间有限，省略工具箱编码）。</span><span class="sxs-lookup"><span data-stu-id="8445e-113">This sample shows how to create the WPF layout to contain the designer, seen in the following grid layout (Toolbox code omitted for space concerns).</span></span> <span data-ttu-id="8445e-114">需注意包含设计器和属性网格的边框的命名。</span><span class="sxs-lookup"><span data-stu-id="8445e-114">Note the naming of the borders which contain the designer and property grid.</span></span>  
  
```xaml  
<Grid>  
    <Grid.ColumnDefinitions>  
        <ColumnDefinition Width="2*"/>  
        <ColumnDefinition Width="7*"/>  
        <ColumnDefinition Width="3*"/>  
    </Grid.ColumnDefinitions>  
    <Border Grid.Column="0">  
        <sapt:ToolboxControl>...</sapt:ToolboxControl>  
    </Border>  
    <Border Grid.Column="1" Name="DesignerBorder"/>  
    <Border Grid.Column="2" Name="PropertyBorder"/>  
</Grid>  
```  
  
 <span data-ttu-id="8445e-115">接下来，此示例创建设计器，并将其主 <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> 和 <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> 与用户界面中适当的容器相关联。</span><span class="sxs-lookup"><span data-stu-id="8445e-115">Next the sample creates the designer, and associates its primary <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> and <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> with the appropriate container in the user interface.</span></span> <span data-ttu-id="8445e-116">以下示例中有几行额外的代码需要解释一下。</span><span class="sxs-lookup"><span data-stu-id="8445e-116">There are a few additional lines of code in the following example that merit some explanation.</span></span> <span data-ttu-id="8445e-117"><xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A>需要调用来为 .NET Framework 附带的活动关联默认的活动设计器。</span><span class="sxs-lookup"><span data-stu-id="8445e-117">The <xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> call is required to associate the default activity designers for the activities shipped with .NET Framework.</span></span> <span data-ttu-id="8445e-118">调用 <xref:System.Activities.Presentation.WorkflowDesigner.Load%2A> 传入要编辑的 WF 项。</span><span class="sxs-lookup"><span data-stu-id="8445e-118"><xref:System.Activities.Presentation.WorkflowDesigner.Load%2A> is called to pass in the WF item to be edited.</span></span> <span data-ttu-id="8445e-119">最后，将 <xref:System.Activities.Presentation.WorkflowDesigner.View%2A>（主画布）和 <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A>（属性网格）放置在用户界面的图面上。</span><span class="sxs-lookup"><span data-stu-id="8445e-119">Finally, the <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (primary canvas) and <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> (property grid) are placed onto the user interface surface.</span></span>  
  
```csharp  
protected override void OnInitialized(EventArgs e)  
{  
   base.OnInitialized(e);  
   // register metadata  
   (new DesignerMetadata()).Register();  
  
   // create the workflow designer  
   WorkflowDesigner wd = new WorkflowDesigner();  
   wd.Load(new Sequence());  
   DesignerBorder.Child = wd.View;  
   PropertyBorder.Child = wd.PropertyInspectorView;  
}  
```  
  
## <a name="using-the-rehosted-toolbox"></a><span data-ttu-id="8445e-120">使用重新承载的工具栏</span><span class="sxs-lookup"><span data-stu-id="8445e-120">Using the rehosted toolbox</span></span>  

 <span data-ttu-id="8445e-121">此示例在 XAML 中以声明方式使用重新承载的工具箱控件。</span><span class="sxs-lookup"><span data-stu-id="8445e-121">This sample uses the rehosted toolbox control declaratively in XAML.</span></span> <span data-ttu-id="8445e-122">请注意，在代码中可以将一个类型传递给 <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> 构造函数。</span><span class="sxs-lookup"><span data-stu-id="8445e-122">Note that in code, one can pass a type to the <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> constructor.</span></span>  
  
```xaml  
<!-- Copyright (c) Microsoft Corporation. All rights reserved-->  
<Window x:Class="Microsoft.Samples.DesignerRehosting.RehostingWfDesigner"  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:sapt="clr-namespace:System.Activities.Presentation.Toolbox;assembly=System.Activities.Presentation"  
        xmlns:sys="clr-namespace:System;assembly=mscorlib"  
        Title="Window1" Height="600" Width="900">  
    <Window.Resources>  
        <sys:String x:Key="AssemblyName">System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35</sys:String>  
    </Window.Resources>  
    <Grid>  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition Width="2*"/>  
            <ColumnDefinition Width="7*"/>  
            <ColumnDefinition Width="3*"/>  
        </Grid.ColumnDefinitions>  
        <Border Grid.Column="0">  
            <sapt:ToolboxControl>  
                <sapt:ToolboxCategory CategoryName="Basic">  
                    <sapt:ToolboxItemWrapper AssemblyName="{StaticResource AssemblyName}" >  
                        <sapt:ToolboxItemWrapper.ToolName>  
                            System.Activities.Statements.Sequence  
                        </sapt:ToolboxItemWrapper.ToolName>  
                       </sapt:ToolboxItemWrapper>  
                    <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">  
                        <sapt:ToolboxItemWrapper.ToolName>  
                            System.Activities.Statements.WriteLine  
                        </sapt:ToolboxItemWrapper.ToolName>  
  
                    </sapt:ToolboxItemWrapper>  
                    <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">  
                        <sapt:ToolboxItemWrapper.ToolName>  
                            System.Activities.Statements.If  
                        </sapt:ToolboxItemWrapper.ToolName>  
  
                    </sapt:ToolboxItemWrapper>  
                    <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">  
                        <sapt:ToolboxItemWrapper.ToolName>  
                            System.Activities.Statements.While  
                        </sapt:ToolboxItemWrapper.ToolName>  
  
                    </sapt:ToolboxItemWrapper>  
                </sapt:ToolboxCategory>  
            </sapt:ToolboxControl>  
        </Border>  
        <Border Grid.Column="1" Name="DesignerBorder"/>  
        <Border Grid.Column="2" Name="PropertyBorder"/>  
    </Grid>  
</Window>  
```  
  
#### <a name="using-the-sample"></a><span data-ttu-id="8445e-123">使用示例</span><span class="sxs-lookup"><span data-stu-id="8445e-123">Using the sample</span></span>  
  
1. <span data-ttu-id="8445e-124">在 Visual Studio 2010 中打开 DesignerRehosting 解决方案。</span><span class="sxs-lookup"><span data-stu-id="8445e-124">Open the DesignerRehosting.sln solution in Visual Studio 2010.</span></span>  
  
2. <span data-ttu-id="8445e-125">按 F5 编译并运行应用程序。</span><span class="sxs-lookup"><span data-stu-id="8445e-125">Press F5 to compile and run the application.</span></span>  
  
3. <span data-ttu-id="8445e-126">一个 WPF 应用程序启动并显示一个重新承载的设计器。</span><span class="sxs-lookup"><span data-stu-id="8445e-126">A WPF application starts with a rehosted designer.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8445e-127">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="8445e-127">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8445e-128">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="8445e-128">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="8445e-129">如果此目录不存在，请参阅[Windows Communication Foundation (wcf) ，并 Windows Workflow Foundation (的 WF](https://www.microsoft.com/download/details.aspx?id=21459)) .NET Framework Windows Communication Foundation ([!INCLUDE[wf1](../../../../includes/wf1-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8445e-129">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8445e-130">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="8445e-130">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\DesignerRehosting\Basic`
