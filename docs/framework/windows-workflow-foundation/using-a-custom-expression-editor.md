---
description: 了解详细信息：使用自定义表达式编辑器
title: 使用自定义表达式编辑器
ms.date: 03/30/2017
ms.assetid: 0901b58b-e037-44a8-8281-f6f54361cfca
ms.openlocfilehash: 0455088d879e51a31b0139f85f871be3fb87e7e6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755091"
---
# <a name="using-a-custom-expression-editor"></a><span data-ttu-id="ea0dc-103">使用自定义表达式编辑器</span><span class="sxs-lookup"><span data-stu-id="ea0dc-103">Using a Custom Expression Editor</span></span>

<span data-ttu-id="ea0dc-104">可以实现自定义表达式编辑器，以提供更丰富或更简单的表达式编辑体验。</span><span class="sxs-lookup"><span data-stu-id="ea0dc-104">A custom expression editor can be implemented to provide a richer or simpler expression editing experience.</span></span> <span data-ttu-id="ea0dc-105">在以下几种情况下，您可能需要使用自定义表达式编辑器：</span><span class="sxs-lookup"><span data-stu-id="ea0dc-105">There are several scenarios in which you might want to use a custom expression editor:</span></span>  
  
- <span data-ttu-id="ea0dc-106">为 IntelliSense 和重新承载的工作流设计器中的其他丰富的编辑功能提供支持。</span><span class="sxs-lookup"><span data-stu-id="ea0dc-106">To provide support for IntelliSense and other rich editing features in a rehosted workflow designer.</span></span> <span data-ttu-id="ea0dc-107">必须提供此功能，因为不能在重新承载应用程序中使用默认的 Visual Studio 表达式编辑器。</span><span class="sxs-lookup"><span data-stu-id="ea0dc-107">This functionality must be provided because the default Visual Studio expression editor cannot be used in rehosted applications.</span></span>  
  
- <span data-ttu-id="ea0dc-108">为简化业务分析人员用户的表达式编辑体验，使其不需要了解 Visual Basic 或处理 Visual Basic 表达式。</span><span class="sxs-lookup"><span data-stu-id="ea0dc-108">To simplify the expression editing experience for the business analyst users, so that they are not, for example, required to learn Visual Basic or deal with Visual Basic expressions.</span></span>  
  
 <span data-ttu-id="ea0dc-109">实现自定义表达式编辑器需要执行以下三个基本步骤：</span><span class="sxs-lookup"><span data-stu-id="ea0dc-109">Three basic steps are needed to implement a custom expression editor:</span></span>  
  
1. <span data-ttu-id="ea0dc-110">实现 <xref:System.Activities.Presentation.View.IExpressionEditorService> 接口。</span><span class="sxs-lookup"><span data-stu-id="ea0dc-110">Implement the <xref:System.Activities.Presentation.View.IExpressionEditorService> interface.</span></span> <span data-ttu-id="ea0dc-111">此接口可管理表达式编辑器的创建和析构。</span><span class="sxs-lookup"><span data-stu-id="ea0dc-111">This interface manages the creation and destruction of expression editors.</span></span>  
  
2. <span data-ttu-id="ea0dc-112">实现 <xref:System.Activities.Presentation.View.IExpressionEditorInstance> 接口。</span><span class="sxs-lookup"><span data-stu-id="ea0dc-112">Implement the <xref:System.Activities.Presentation.View.IExpressionEditorInstance> interface.</span></span> <span data-ttu-id="ea0dc-113">此接口实现针对表达式编辑 UI 的 UI。</span><span class="sxs-lookup"><span data-stu-id="ea0dc-113">This interface implements the UI for expression editing UI.</span></span>  
  
3. <span data-ttu-id="ea0dc-114">在重新承载的工作流应用程序中发布 <xref:System.Activities.Presentation.View.IExpressionEditorService>。</span><span class="sxs-lookup"><span data-stu-id="ea0dc-114">Publish the <xref:System.Activities.Presentation.View.IExpressionEditorService> in your rehosted workflow application.</span></span>  
  
## <a name="implementing-a-custom-expression-editor-in-a-class-library"></a><span data-ttu-id="ea0dc-115">在类库中实现自定义表达式编辑器</span><span class="sxs-lookup"><span data-stu-id="ea0dc-115">Implementing a Custom Expression Editor in a Class Library</span></span>  

 <span data-ttu-id="ea0dc-116">以下是实现 MyExpressionEditorService 库项目中包含的 `MyEditorService` 接口的（概念证明）<xref:System.Activities.Presentation.View.IExpressionEditorService> 类的代码示例。</span><span class="sxs-lookup"><span data-stu-id="ea0dc-116">Here is a sample of code for a (proof of concept) `MyEditorService` class that implements the <xref:System.Activities.Presentation.View.IExpressionEditorService> interface is contained in a MyExpressionEditorService library project.</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Activities.Presentation.View;  
using System.Activities.Presentation.Hosting;  
using System.Activities.Presentation.Model;  
  
namespace MyExpressionEditorService  
{  
    public class MyEditorService : IExpressionEditorService  
    {  
        public void CloseExpressionEditors()  
        {  
  
        }  
        public IExpressionEditorInstance CreateExpressionEditor(AssemblyContextControlItem assemblies, ImportedNamespaceContextItem importedNamespaces, List<ModelItem> variables, string text)  
        {  
            MyExpressionEditorInstance instance = new MyExpressionEditorInstance();  
            return instance;  
        }  
        public IExpressionEditorInstance CreateExpressionEditor(AssemblyContextControlItem assemblies, ImportedNamespaceContextItem importedNamespaces, List<ModelItem> variables, string text, System.Windows.Size initialSize)  
                {  
            MyExpressionEditorInstance instance = new MyExpressionEditorInstance();  
            return instance;  
        }  
        public IExpressionEditorInstance CreateExpressionEditor(AssemblyContextControlItem assemblies, ImportedNamespaceContextItem importedNamespaces, List<ModelItem> variables, string text, Type expressionType)  
            {  
            MyExpressionEditorInstance instance = new MyExpressionEditorInstance();  
            return instance;  
        }  
        public IExpressionEditorInstance CreateExpressionEditor(AssemblyContextControlItem assemblies, ImportedNamespaceContextItem importedNamespaces, List<ModelItem> variables, string text, Type expressionType, System.Windows.Size initialSize)  
        {  
            MyExpressionEditorInstance instance = new MyExpressionEditorInstance();  
            return instance;  
        }  
        public void UpdateContext(AssemblyContextControlItem assemblies, ImportedNamespaceContextItem importedNamespaces)  
        {  
  
        }  
  
    }  
}  
```  
  
 <span data-ttu-id="ea0dc-117">下面是实现 MyExpressionEditorService 库项目中 `MyExpressionEditorInstance` 接口的 <xref:System.Activities.Presentation.View.IExpressionEditorInstance> 类的代码。</span><span class="sxs-lookup"><span data-stu-id="ea0dc-117">Here is the code for a `MyExpressionEditorInstance` class that implements the <xref:System.Activities.Presentation.View.IExpressionEditorInstance> interface in a MyExpressionEditorService library project.</span></span>  
  
```csharp  
using System;  
using System.Activities.Presentation.View;  
using System.Windows;  
using System.Reflection;  
using System.Windows.Controls;  
  
namespace MyExpressionEditorService  
{  
    public class MyExpressionEditorInstance : IExpressionEditorInstance  
    {  
        private TextBox textBox = new TextBox();  
  
        public bool AcceptsReturn { get; set; }  
        public bool AcceptsTab { get; set; }  
        public bool HasAggregateFocus {  
            get  
            {  
                return true;  
            }  
        }  
  
        public System.Windows.Controls.ScrollBarVisibility HorizontalScrollBarVisibility { get; set; }  
        public System.Windows.Controls.Control HostControl {  
            get  
            {  
                return textBox;  
            }  
        }  
        public int MaxLines { get; set; }  
        public int MinLines { get; set; }  
        public string Text { get; set; }  
        public System.Windows.Controls.ScrollBarVisibility VerticalScrollBarVisibility { get; set; }  
  
        public event EventHandler Closing;  
        public event EventHandler GotAggregateFocus;  
        public event EventHandler LostAggregateFocus;  
        public event EventHandler TextChanged;  
  
        public bool CanCompleteWord()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanCopy()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanCut()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanDecreaseFilterLevel()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanGlobalIntellisense()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanIncreaseFilterLevel()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanParameterInfo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanPaste()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanQuickInfo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanRedo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanUndo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
  
        public void ClearSelection()  
        {  
            MessageBox.Show(MethodBase.GetCurrentMethod().Name);  
        }  
        public void Close()  
        {  
            MessageBox.Show(MethodBase.GetCurrentMethod().Name);  
        }  
        public bool CompleteWord()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool Copy()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool Cut()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool DecreaseFilterLevel()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public void Focus()  
        {  
            MessageBox.Show(MethodBase.GetCurrentMethod().Name);  
        }  
        public string GetCommittedText()  
        {  
            return "CommittedText";  
        }  
        public bool GlobalIntellisense()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool IncreaseFilterLevel()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool ParameterInfo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool Paste()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool QuickInfo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool Redo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool Undo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
    }  
}  
```  
  
### <a name="publishing-a-custom-expression-editor-in-a-wpf-project"></a><span data-ttu-id="ea0dc-118">在 WPF 项目中发布自定义表达式编辑器</span><span class="sxs-lookup"><span data-stu-id="ea0dc-118">Publishing a Custom Expression Editor in a WPF Project</span></span>  

 <span data-ttu-id="ea0dc-119">下面的代码演示如何在 WPF 应用程序中 rehost 设计器，以及如何创建和发布 `MyEditorService` 服务。</span><span class="sxs-lookup"><span data-stu-id="ea0dc-119">Here is the code that shows how to rehost the designer in a WPF application and how to create and publish the `MyEditorService` service.</span></span> <span data-ttu-id="ea0dc-120">使用此代码之前, 从包含 avalon2 应用程序的项目将引用添加到 MyExpressionEditorService 库项目。 </span><span class="sxs-lookup"><span data-stu-id="ea0dc-120">Before using this code, add a reference to the MyExpressionEditorService library project from the project that contains the avalon2 application.</span></span>  
  
```csharp  
using System.Windows;  
using System.Windows.Controls;  
using System.Activities.Presentation;  
using System.Activities.Statements;  
using System.Activities.Core.Presentation;  
using System.Activities.Presentation.View;  
using MyExpressionEditorService;  
  
namespace WpfApplication1  
{  
    /// <summary>  
    /// Interaction logic for MainWindow.xaml  
    /// </summary>  
    public partial class MainWindow : Window  
    {  
  
        private MyEditorService expressionEditorService;  
        public MainWindow()  
        {  
            InitializeComponent();  
            new DesignerMetadata().Register();  
            createDesigner();  
        }  
  
        public void createDesigner()  
        {  
            WorkflowDesigner designer = new WorkflowDesigner();  
            Sequence root = new Sequence()  
            {  
                Activities = {  
                new Assign(),  
                new WriteLine()}  
            };  
  
            designer.Load(root);  
  
            Grid.SetColumn(designer.View, 0);  
  
            // Create ExpressionEditorService
            this.expressionEditorService = new MyEditorService();  
  
            // Publish the instance of MyEditorService.  
            designer.Context.Services.Publish<IExpressionEditorService>(this.expressionEditorService);  
  
            MyGrid.Children.Add(designer.View);  
        }  
    }  
}  
```  
  
### <a name="notes"></a><span data-ttu-id="ea0dc-121">说明</span><span class="sxs-lookup"><span data-stu-id="ea0dc-121">Notes</span></span>  

 <span data-ttu-id="ea0dc-122">如果在自定义活动设计器中使用 **ExpressionTextBox** 控件，则无需使用接口的和方法来创建和销毁表达式 <xref:System.Activities.Presentation.View.IExpressionEditorService.CreateExpressionEditor%2A> 编辑器 <xref:System.Activities.Presentation.View.IExpressionEditorService.CloseExpressionEditors%2A> <xref:System.Activities.Presentation.View.IExpressionEditorService> 。</span><span class="sxs-lookup"><span data-stu-id="ea0dc-122">If you are using an **ExpressionTextBox** control in a custom activity designer, it is not necessary to create and destroy expression editors using the <xref:System.Activities.Presentation.View.IExpressionEditorService.CreateExpressionEditor%2A> and <xref:System.Activities.Presentation.View.IExpressionEditorService.CloseExpressionEditors%2A> methods of the <xref:System.Activities.Presentation.View.IExpressionEditorService> interface.</span></span> <span data-ttu-id="ea0dc-123"><xref:System.Activities.Presentation.View.ExpressionTextBox> 类可为您管理此过程。</span><span class="sxs-lookup"><span data-stu-id="ea0dc-123">The <xref:System.Activities.Presentation.View.ExpressionTextBox> class manages this for you.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea0dc-124">请参阅</span><span class="sxs-lookup"><span data-stu-id="ea0dc-124">See also</span></span>

- <xref:System.Activities.Presentation.View.IExpressionEditorService>
- <xref:System.Activities.Presentation.View.IExpressionEditorInstance>
- [<span data-ttu-id="ea0dc-125">在自定义设计器中使用 ExpressionTextBox</span><span class="sxs-lookup"><span data-stu-id="ea0dc-125">Using the ExpressionTextBox in a Custom Activity Designer</span></span>](./samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)
