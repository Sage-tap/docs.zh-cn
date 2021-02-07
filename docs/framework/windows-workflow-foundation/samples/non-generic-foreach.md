---
description: 了解详细信息：非泛型 ForEach
title: 非泛型 ForEach
ms.date: 03/30/2017
ms.assetid: 576cd07a-d58d-4536-b514-77bad60bff38
ms.openlocfilehash: 16635da4ef57ff7b59e178f5954465d8b86bf488
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741947"
---
# <a name="non-generic-foreach"></a><span data-ttu-id="dfd09-103">非泛型 ForEach</span><span class="sxs-lookup"><span data-stu-id="dfd09-103">Non-Generic ForEach</span></span>

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] <span data-ttu-id="dfd09-104">的工具箱中附带了一组控制流活动，其中包括可用来循环访问 <xref:System.Activities.Statements.ForEach%601> 集合的 <xref:System.Collections.Generic.IEnumerable%601>。</span><span class="sxs-lookup"><span data-stu-id="dfd09-104">ships in its toolbox a set of Control Flow activities, including <xref:System.Activities.Statements.ForEach%601>, which allows iterating through <xref:System.Collections.Generic.IEnumerable%601> collections.</span></span>  
  
 <span data-ttu-id="dfd09-105"><xref:System.Activities.Statements.ForEach%601> 要求其 <xref:System.Activities.Statements.ForEach%601.Values%2A> 属性为 <xref:System.Collections.Generic.IEnumerable%601> 类型。</span><span class="sxs-lookup"><span data-stu-id="dfd09-105"><xref:System.Activities.Statements.ForEach%601> requires its <xref:System.Activities.Statements.ForEach%601.Values%2A> property to be of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="dfd09-106">这将阻止用户循环访问实现 <xref:System.Collections.Generic.IEnumerable%601> 接口（例如，<xref:System.Collections.ArrayList>）的数据结构。</span><span class="sxs-lookup"><span data-stu-id="dfd09-106">This precludes users from iterating over data structures that implement <xref:System.Collections.Generic.IEnumerable%601> interface (for example, <xref:System.Collections.ArrayList>).</span></span> <span data-ttu-id="dfd09-107">非泛型版本的 <xref:System.Activities.Statements.ForEach%601> 没有这一需求，不过与此对应的代价是，需要更复杂的运行时来确保集合中的值类型的兼容性。</span><span class="sxs-lookup"><span data-stu-id="dfd09-107">The non-generic version of <xref:System.Activities.Statements.ForEach%601> overcomes this requirement, at the expense of more run-time complexity for ensuring the compatibility of the types of the values in the collection.</span></span>  
  
 <span data-ttu-id="dfd09-108">此示例演示如何实现非泛型的 <xref:System.Activities.Statements.ForEach%601> 活动及其设计器。</span><span class="sxs-lookup"><span data-stu-id="dfd09-108">This sample shows how to implement a non-generic <xref:System.Activities.Statements.ForEach%601> activity and its designer.</span></span> <span data-ttu-id="dfd09-109">此活动可用于循环访问 <xref:System.Collections.ArrayList>。</span><span class="sxs-lookup"><span data-stu-id="dfd09-109">This activity can be used to iterate through <xref:System.Collections.ArrayList>.</span></span>  
  
## <a name="foreach-activity"></a><span data-ttu-id="dfd09-110">ForEach 活动</span><span class="sxs-lookup"><span data-stu-id="dfd09-110">ForEach Activity</span></span>  

 <span data-ttu-id="dfd09-111">C #/Visual Basic `foreach` 语句枚举集合中的元素，并对集合中的每个元素执行嵌入语句。</span><span class="sxs-lookup"><span data-stu-id="dfd09-111">The C#/Visual Basic `foreach` statement enumerates the elements of a collection, executing an embedded statement for each element of the collection.</span></span> <span data-ttu-id="dfd09-112">[!INCLUDE[wf1](../../../../includes/wf1-md.md)] 的 `foreach` 等效活动为 <xref:System.Activities.Statements.ForEach%601> 和 <xref:System.Activities.Statements.ParallelForEach%601>。</span><span class="sxs-lookup"><span data-stu-id="dfd09-112">The [!INCLUDE[wf1](../../../../includes/wf1-md.md)] equivalent activities of `foreach` are <xref:System.Activities.Statements.ForEach%601> and <xref:System.Activities.Statements.ParallelForEach%601>.</span></span> <span data-ttu-id="dfd09-113"><xref:System.Activities.Statements.ForEach%601> 活动包含一个值列表和一个主体。</span><span class="sxs-lookup"><span data-stu-id="dfd09-113">The <xref:System.Activities.Statements.ForEach%601> activity contains a list of values and a body.</span></span> <span data-ttu-id="dfd09-114">在运行时，将循环访问此列表，并对列表中的每个值执行主体。</span><span class="sxs-lookup"><span data-stu-id="dfd09-114">At runtime, the list is iterated and the body is executed for each value in the list.</span></span>  
  
 <span data-ttu-id="dfd09-115">对于大多数情况，此活动的泛型版本应为首选解决方案，因为它涵盖了应使用此活动的大多数方案，并且提供编译时类型检查。</span><span class="sxs-lookup"><span data-stu-id="dfd09-115">For most cases, the generic version of the activity should be the preferred solution, because it covers most of the scenarios in which it would be used, and provides type checking at compile time.</span></span> <span data-ttu-id="dfd09-116">非泛型版本可用于循环访问实现非泛型 <xref:System.Collections.IEnumerable> 接口的类型。</span><span class="sxs-lookup"><span data-stu-id="dfd09-116">The non-generic version can be used for iterating through types that implement the non-generic <xref:System.Collections.IEnumerable> interface.</span></span>  
  
## <a name="class-definition"></a><span data-ttu-id="dfd09-117">类定义</span><span class="sxs-lookup"><span data-stu-id="dfd09-117">Class Definition</span></span>  

 <span data-ttu-id="dfd09-118">下面的代码示例显示非泛型 `ForEach` 活动的定义。</span><span class="sxs-lookup"><span data-stu-id="dfd09-118">The following code example shows the definition of a non-generic `ForEach` activity.</span></span>  
  
```csharp  
[ContentProperty("Body")]  
public class ForEach : NativeActivity  
{  
    [RequiredArgument]  
    [DefaultValue(null)]  
    InArgument<IEnumerable> Values { get; set; }  
  
    [DefaultValue(null)]  
    [DependsOn("Values")]  
    ActivityAction<object> Body { get; set; }
}  
```  
  
 <span data-ttu-id="dfd09-119">Body（可选）</span><span class="sxs-lookup"><span data-stu-id="dfd09-119">Body (optional)</span></span>  
 <span data-ttu-id="dfd09-120"><xref:System.Activities.ActivityAction> 类型的 <xref:System.Object>，将对集合中的每个元素执行它。</span><span class="sxs-lookup"><span data-stu-id="dfd09-120">The <xref:System.Activities.ActivityAction> of type <xref:System.Object>, which is executed for each element in the collection.</span></span> <span data-ttu-id="dfd09-121">每个个体元素都通过其 `Argument` 属性传递到 Body。</span><span class="sxs-lookup"><span data-stu-id="dfd09-121">Each individual element is passed into the Body through its `Argument` property.</span></span>  
  
 <span data-ttu-id="dfd09-122">Values（可选）</span><span class="sxs-lookup"><span data-stu-id="dfd09-122">Values (optional)</span></span>  
 <span data-ttu-id="dfd09-123">循环访问的元素集合。</span><span class="sxs-lookup"><span data-stu-id="dfd09-123">The collection of elements that are iterated over.</span></span> <span data-ttu-id="dfd09-124">在运行时确保所有集合元素为兼容类型。</span><span class="sxs-lookup"><span data-stu-id="dfd09-124">Ensuring that all elements of the collection are of compatible types is done at run-time.</span></span>  
  
## <a name="example-of-using-foreach"></a><span data-ttu-id="dfd09-125">使用 ForEach 的示例</span><span class="sxs-lookup"><span data-stu-id="dfd09-125">Example of Using ForEach</span></span>  

 <span data-ttu-id="dfd09-126">下面的代码演示如何在应用程序中使用 ForEach 活动。</span><span class="sxs-lookup"><span data-stu-id="dfd09-126">The following code demonstrates how to use the ForEach activity in an application.</span></span>  
  
```csharp  
string[] names = { "bill", "steve", "ray" };  
  
DelegateInArgument<object> iterationVariable = new DelegateInArgument<object>() { Name = "iterationVariable" };  
  
Activity sampleUsage =  
    new ForEach  
    {  
       Values = new InArgument<IEnumerable>(c=> names),  
       Body = new ActivityAction<object>
       {
           Argument = iterationVariable,  
           Handler = new WriteLine  
           {  
               Text = new InArgument<string>(env => string.Format("Hello {0}",                                                               iterationVariable.Get(env)))  
           }  
       }  
   };  
```  
  
|<span data-ttu-id="dfd09-127">条件</span><span class="sxs-lookup"><span data-stu-id="dfd09-127">Condition</span></span>|<span data-ttu-id="dfd09-128">Message</span><span class="sxs-lookup"><span data-stu-id="dfd09-128">Message</span></span>|<span data-ttu-id="dfd09-129">严重性</span><span class="sxs-lookup"><span data-stu-id="dfd09-129">Severity</span></span>|<span data-ttu-id="dfd09-130">异常类型</span><span class="sxs-lookup"><span data-stu-id="dfd09-130">Exception Type</span></span>|  
|---------------|-------------|--------------|--------------------|  
|<span data-ttu-id="dfd09-131">Values 为 `null`</span><span class="sxs-lookup"><span data-stu-id="dfd09-131">Values is `null`</span></span>|<span data-ttu-id="dfd09-132">未提供必需活动自变量“Values”的值。</span><span class="sxs-lookup"><span data-stu-id="dfd09-132">Value for a required activity argument 'Values' was not supplied.</span></span>|<span data-ttu-id="dfd09-133">错误</span><span class="sxs-lookup"><span data-stu-id="dfd09-133">Error</span></span>|<xref:System.InvalidOperationException>|  
  
## <a name="foreach-designer"></a><span data-ttu-id="dfd09-134">ForEachT 设计器</span><span class="sxs-lookup"><span data-stu-id="dfd09-134">ForEach Designer</span></span>  

 <span data-ttu-id="dfd09-135">此示例的活动设计器的外观与为内置 <xref:System.Activities.Statements.ForEach%601> 活动提供的设计器的外观相似。</span><span class="sxs-lookup"><span data-stu-id="dfd09-135">The activity designer for the sample is similar in appearance to the designer provided for the built-in <xref:System.Activities.Statements.ForEach%601> activity.</span></span> <span data-ttu-id="dfd09-136">设计器将显示在工具箱中的 " **示例**"、" **非泛型" 活动** 类别。</span><span class="sxs-lookup"><span data-stu-id="dfd09-136">The designer appears in the toolbox in the **Samples**, **Non-Generic Activities** category.</span></span> <span data-ttu-id="dfd09-137">设计器在 "工具箱" 中名为 " **ForEachWithBodyFactory** "，因为活动 <xref:System.Activities.Presentation.IActivityTemplateFactory> 在工具箱中公开，这将使用正确配置的来创建活动 <xref:System.Activities.ActivityAction> 。</span><span class="sxs-lookup"><span data-stu-id="dfd09-137">The designer is named **ForEachWithBodyFactory** in the toolbox, because the activity exposes an <xref:System.Activities.Presentation.IActivityTemplateFactory> in the toolbox, which creates the activity with a properly configured <xref:System.Activities.ActivityAction>.</span></span>  
  
```csharp  
public sealed class ForEachWithBodyFactory : IActivityTemplateFactory  
{  
    public Activity Create(DependencyObject target)  
    {  
        return new Microsoft.Samples.Activities.Statements.ForEach()  
        {  
            Body = new ActivityAction<object>()  
            {  
                Argument = new DelegateInArgument<object>()  
                {  
                    Name = "item"  
                }  
            }  
        };  
    }  
}  
```  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="dfd09-138">运行本示例的步骤</span><span class="sxs-lookup"><span data-stu-id="dfd09-138">To run this sample</span></span>  
  
1. <span data-ttu-id="dfd09-139">将您选择的项目设置为解决方案的启动项目：</span><span class="sxs-lookup"><span data-stu-id="dfd09-139">Set the project of your choice as the start-up project of the solution:</span></span>  
  
    1. <span data-ttu-id="dfd09-140">**CodeTestClient** 演示如何使用代码使用活动。</span><span class="sxs-lookup"><span data-stu-id="dfd09-140">**CodeTestClient** shows how to use the activity using code.</span></span>  
  
    2. <span data-ttu-id="dfd09-141">**DesignerTestClient** 演示如何在设计器中使用活动。</span><span class="sxs-lookup"><span data-stu-id="dfd09-141">**DesignerTestClient** shows how to use the activity within the designer.</span></span>  
  
2. <span data-ttu-id="dfd09-142">生成并运行该项目。</span><span class="sxs-lookup"><span data-stu-id="dfd09-142">Build and run the project.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="dfd09-143">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="dfd09-143">The samples may already be installed on your machine.</span></span> <span data-ttu-id="dfd09-144">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="dfd09-144">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="dfd09-145">如果此目录不存在，请参阅[Windows Communication Foundation (wcf) ，并 Windows Workflow Foundation (的 WF](https://www.microsoft.com/download/details.aspx?id=21459)) .NET Framework Windows Communication Foundation ([!INCLUDE[wf1](../../../../includes/wf1-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfd09-145">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="dfd09-146">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="dfd09-146">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericForEach`
