---
description: 了解详细信息：调用活动验证
title: 调用活动验证
ms.date: 03/30/2017
ms.assetid: 22bef766-c505-4fd4-ac0f-7b363b238969
ms.openlocfilehash: dc710e76134fbd76f5217df4ea569f20e6de4445
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792656"
---
# <a name="invoking-activity-validation"></a><span data-ttu-id="bdad0-103">调用活动验证</span><span class="sxs-lookup"><span data-stu-id="bdad0-103">Invoking Activity Validation</span></span>

<span data-ttu-id="bdad0-104">活动验证提供了一种在执行任何活动配置之前标识和报告此配置中的错误的方法。</span><span class="sxs-lookup"><span data-stu-id="bdad0-104">Activity validation provides a method to identify and report errors in any activity’s configuration prior to its execution.</span></span> <span data-ttu-id="bdad0-105">当在工作流设计器中修改工作流，并且工作流设计器中显示任何验证错误或警告时，将执行验证。</span><span class="sxs-lookup"><span data-stu-id="bdad0-105">Validation occurs when a workflow is modified in the workflow designer and any validation errors or warnings are displayed in the workflow designer.</span></span> <span data-ttu-id="bdad0-106">此外，当调用工作流时，如果发生任何验证错误，默认验证逻辑将引发 <xref:System.Activities.InvalidWorkflowException>，此时，也将在运行时执行验证。</span><span class="sxs-lookup"><span data-stu-id="bdad0-106">Validation also occurs at run time when a workflow is invoked and if any validation errors occur, an <xref:System.Activities.InvalidWorkflowException> is thrown by the default validation logic.</span></span> <span data-ttu-id="bdad0-107">Windows Workflow Foundation (WF) 提供了 <xref:System.Activities.Validation.ActivityValidationServices> 一个类，工作流应用程序和工具开发人员可使用该类来显式验证活动。</span><span class="sxs-lookup"><span data-stu-id="bdad0-107">Windows Workflow Foundation (WF) provides the <xref:System.Activities.Validation.ActivityValidationServices> class that can be used by workflow application and tooling developers to explicitly validate an activity.</span></span> <span data-ttu-id="bdad0-108">本主题说明如何使用 <xref:System.Activities.Validation.ActivityValidationServices> 执行活动验证。</span><span class="sxs-lookup"><span data-stu-id="bdad0-108">This topic describes how to use <xref:System.Activities.Validation.ActivityValidationServices> to perform activity validation.</span></span>  
  
## <a name="using-activityvalidationservices"></a><span data-ttu-id="bdad0-109">使用 ActivityValidationServices</span><span class="sxs-lookup"><span data-stu-id="bdad0-109">Using ActivityValidationServices</span></span>  

 <span data-ttu-id="bdad0-110"><xref:System.Activities.Validation.ActivityValidationServices> 具有两种 <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> 重载，用于调用活动的验证逻辑。</span><span class="sxs-lookup"><span data-stu-id="bdad0-110"><xref:System.Activities.Validation.ActivityValidationServices> has two <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> overloads that are used to invoke an activity’s validation logic.</span></span> <span data-ttu-id="bdad0-111">第一种重载采用要验证的根活动，并返回验证错误和警告的集合。</span><span class="sxs-lookup"><span data-stu-id="bdad0-111">The first overload takes the root activity to be validated and returns a collection of validation errors and warnings.</span></span> <span data-ttu-id="bdad0-112">下面的示例使用含有两个必需参数的自定义 `Add` 活动。</span><span class="sxs-lookup"><span data-stu-id="bdad0-112">In the following example, a custom `Add` activity is used that has two required arguments.</span></span>  
  
```csharp  
public sealed class Add : CodeActivity<int>  
{  
    [RequiredArgument]  
    public InArgument<int> Operand1 { get; set; }  
  
    [RequiredArgument]  
    public InArgument<int> Operand2 { get; set; }  
  
    protected override int Execute(CodeActivityContext context)  
    {  
        return Operand1.Get(context) + Operand2.Get(context);  
    }  
}  
```  
  
 <span data-ttu-id="bdad0-113">`Add` 活动在 <xref:System.Activities.Statements.Sequence> 中使用，但未绑定该活动的两个必需参数，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="bdad0-113">The `Add` activity is used inside a <xref:System.Activities.Statements.Sequence>, but its two required arguments are not bound, as shown in the following example.</span></span>  
  
```csharp  
Variable<int> Operand1 = new Variable<int>{ Default = 10 };  
Variable<int> Operand2 = new Variable<int>{ Default = 15 };  
Variable<int> Result = new Variable<int>();  
  
Activity wf = new Sequence  
{  
    Variables = { Operand1, Operand2, Result },  
    Activities =
    {  
        new Add(),  
        new WriteLine  
        {  
            Text = new InArgument<string>(env => "The result is " + Result.Get(env))  
        }  
    }  
};  
```  
  
 <span data-ttu-id="bdad0-114">此工作流可以通过调用 <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> 进行验证。</span><span class="sxs-lookup"><span data-stu-id="bdad0-114">This workflow can be validated by calling <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="bdad0-115"><xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> 返回活动及其所有子级包含的所有验证错误或警告的集合，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="bdad0-115"><xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> returns a collection of any validation errors or warnings contained by the activity and any children, as shown in the following example.</span></span>  
  
```csharp  
ValidationResults results = ActivityValidationServices.Validate(wf);  
  
if (results.Errors.Count == 0 && results.Warnings.Count == 0)  
{  
    Console.WriteLine("No warnings or errors");  
}  
else  
{  
    foreach (ValidationError error in results.Errors)  
    {  
        Console.WriteLine("Error: {0}", error.Message);  
    }  
    foreach (ValidationError warning in results.Warnings)  
    {  
        Console.WriteLine("Warning: {0}", warning.Message);  
    }  
}  
```  
  
 <span data-ttu-id="bdad0-116">当对此示例工作流调用 <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> 时，返回两个验证错误。</span><span class="sxs-lookup"><span data-stu-id="bdad0-116">When <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> is called on this sample workflow, two validation errors are returned.</span></span>  
  
 <span data-ttu-id="bdad0-117">**错误：未提供必要活动自变量“Operand2”的值。**</span><span class="sxs-lookup"><span data-stu-id="bdad0-117">**Error: Value for a required activity argument 'Operand2' was not supplied.**</span></span>  
<span data-ttu-id="bdad0-118">**错误：未提供必需活动参数 "Operand1" 的值。**</span><span class="sxs-lookup"><span data-stu-id="bdad0-118">**Error: Value for a required activity argument 'Operand1' was not supplied.**</span></span>  <span data-ttu-id="bdad0-119">如果已调用此工作流，将引发 <xref:System.Activities.InvalidWorkflowException>，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="bdad0-119">If this workflow was invoked, an <xref:System.Activities.InvalidWorkflowException> would be thrown, as shown in the following example.</span></span>  
  
```csharp  
try  
{  
    WorkflowInvoker.Invoke(wf);  
}  
catch (Exception ex)  
{  
    Console.WriteLine(ex);  
}  
```  
  
 <span data-ttu-id="bdad0-120">**System.Activities.InvalidWorkflowException:**</span><span class="sxs-lookup"><span data-stu-id="bdad0-120">**System.Activities.InvalidWorkflowException:**</span></span>  
<span data-ttu-id="bdad0-121">**处理工作流树时遇到以下错误：** 
 **"Add"：未提供必需活动参数 "Operand2" 的值。** 
 **"Add"：未提供必需活动参数 "Operand1" 的值。**</span><span class="sxs-lookup"><span data-stu-id="bdad0-121">**The following errors were encountered while processing the workflow tree:**
 **'Add': Value for a required activity argument 'Operand2' was not supplied.**
 **'Add': Value for a required activity argument 'Operand1' was not supplied.**</span></span>  <span data-ttu-id="bdad0-122">为使此示例工作流有效，必须绑定 `Add` 活动的两个必需自变量。</span><span class="sxs-lookup"><span data-stu-id="bdad0-122">For this example workflow to be valid, the two required arguments of the `Add` activity must be bound.</span></span> <span data-ttu-id="bdad0-123">在下面的示例中，这两个必需自变量绑定到工作流变量和结果值。</span><span class="sxs-lookup"><span data-stu-id="bdad0-123">In the following example, the two required arguments are bound to workflow variables along with the result value.</span></span> <span data-ttu-id="bdad0-124">在此示例中，<xref:System.Activities.Activity%601.Result%2A> 参数与这两个必需参数绑定在一起。</span><span class="sxs-lookup"><span data-stu-id="bdad0-124">In this example the <xref:System.Activities.Activity%601.Result%2A> argument is bound along with the two required arguments.</span></span> <span data-ttu-id="bdad0-125">不必绑定 <xref:System.Activities.Activity%601.Result%2A> 自变量，因为如果未绑定该自变量，并不会导致验证错误。</span><span class="sxs-lookup"><span data-stu-id="bdad0-125">The <xref:System.Activities.Activity%601.Result%2A> argument is not required to be bound and does not cause a validation error if it is not.</span></span> <span data-ttu-id="bdad0-126">如果在工作流中的其他位置使用 <xref:System.Activities.Activity%601.Result%2A> 的值，工作流作者应负责绑定该参数。</span><span class="sxs-lookup"><span data-stu-id="bdad0-126">It is the responsibility of the workflow author to bind <xref:System.Activities.Activity%601.Result%2A> if its value is used elsewhere in the workflow.</span></span>  
  
```csharp  
new Add  
{  
    Operand1 = Operand1,  
    Operand2 = Operand2,  
    Result = Result  
}  
```  
  
### <a name="validating-required-arguments-on-the-root-activity"></a><span data-ttu-id="bdad0-127">验证根活动中的必需参数</span><span class="sxs-lookup"><span data-stu-id="bdad0-127">Validating Required Arguments on the Root Activity</span></span>  

 <span data-ttu-id="bdad0-128">如果工作流的根活动含有自变量，则在调用该工作流并向其传递参数之前，不会绑定这些自变量。</span><span class="sxs-lookup"><span data-stu-id="bdad0-128">If the root activity of a workflow has arguments, these are not bound until the workflow is invoked and parameters are passed to the workflow.</span></span> <span data-ttu-id="bdad0-129">因此，如果已调用工作流但未传入必需自变量，下面的工作流将通过验证，但会引发异常，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="bdad0-129">The following workflow passes validation, but an exception is thrown if the workflow is invoked without passing in the required arguments, as shown in the following example.</span></span>  
  
```csharp  
Activity wf = new Add();  
  
ValidationResults results = ActivityValidationServices.Validate(wf);  
// results has no errors or warnings, but when the workflow  
// is invoked, an InvalidWorkflowException is thrown.  
try  
{  
    WorkflowInvoker.Invoke(wf);  
}  
catch (Exception ex)  
{  
    Console.WriteLine(ex);  
}  
```  
  
 <span data-ttu-id="bdad0-130">**System.ArgumentException: The root activity's argument settings are incorrect.**</span><span class="sxs-lookup"><span data-stu-id="bdad0-130">**System.ArgumentException: The root activity's argument settings are incorrect.**</span></span>  
<span data-ttu-id="bdad0-131">**请修复工作流定义或提供输入值来修复这些错误：** 
 **"Add"：未提供必需活动参数 "Operand2" 的值。** 
 **"Add"：未提供必需活动参数 "Operand1" 的值。**</span><span class="sxs-lookup"><span data-stu-id="bdad0-131">**Either fix the workflow definition or supply input values to fix these errors:**
 **'Add': Value for a required activity argument 'Operand2' was not supplied.**
 **'Add': Value for a required activity argument 'Operand1' was not supplied.**</span></span>  <span data-ttu-id="bdad0-132">传递正确的自变量之后，工作流将成功完成，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="bdad0-132">After the correct arguments are passed, the workflow completes successfully, as shown in the following example.</span></span>  
  
```csharp  
Add wf = new Add();  
  
ValidationResults results = ActivityValidationServices.Validate(wf);  
// results has no errors or warnings, and the workflow completes  
// successfully because the required arguments were passed.  
try  
{  
    Dictionary<string, object> wfparams = new Dictionary<string, object>  
    {  
        { "Operand1", 10 },  
        { "Operand2", 15 }  
    };  
  
    int result = WorkflowInvoker.Invoke(wf, wfparams);  
    Console.WriteLine("Result: {0}", result);  
}  
catch (Exception ex)  
{  
    Console.WriteLine(ex);  
}  
```  
  
> [!NOTE]
> <span data-ttu-id="bdad0-133">在此示例中，根活动已声明为 `Add`，而不是上述示例中的 `Activity`。</span><span class="sxs-lookup"><span data-stu-id="bdad0-133">In this example, the root activity was declared as `Add` instead of `Activity` as in the previous example.</span></span> <span data-ttu-id="bdad0-134">这使 `WorkflowInvoker.Invoke` 方法返回一个表示 `Add` 活动的结果的整数，而不是 `out` 自变量的字典。</span><span class="sxs-lookup"><span data-stu-id="bdad0-134">This allows the `WorkflowInvoker.Invoke` method to return a single integer that represents the results of the `Add` activity instead of a dictionary of `out` arguments.</span></span> <span data-ttu-id="bdad0-135">也可将 `wf` 变量声明为 `Activity<int>`。</span><span class="sxs-lookup"><span data-stu-id="bdad0-135">The variable `wf` could also have been declared as `Activity<int>`.</span></span>  
  
 <span data-ttu-id="bdad0-136">当验证根自变量时，主机应用程序应负责确保在调用工作流时传递所有必需自变量。</span><span class="sxs-lookup"><span data-stu-id="bdad0-136">When validating root arguments, it is the responsibility of the host application to ensure that all required arguments are passed when the workflow is invoked.</span></span>  
  
### <a name="invoking-imperative-code-based-validation"></a><span data-ttu-id="bdad0-137">调用基于命令性代码的验证</span><span class="sxs-lookup"><span data-stu-id="bdad0-137">Invoking Imperative Code-Based Validation</span></span>

<span data-ttu-id="bdad0-138">基于命令性代码的验证为活动提供用于自身验证的简单方法，并且该方法可用于从 <xref:System.Activities.CodeActivity>、<xref:System.Activities.AsyncCodeActivity> 和 <xref:System.Activities.NativeActivity> 派生的活动。</span><span class="sxs-lookup"><span data-stu-id="bdad0-138">Imperative code-based validation provides a simple way for an activity to provide validation about itself, and is available for activities that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, and <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="bdad0-139">会向活动中添加确定所有验证错误或警告的验证代码。</span><span class="sxs-lookup"><span data-stu-id="bdad0-139">Validation code that determines any validation errors or warnings is added to the activity.</span></span> <span data-ttu-id="bdad0-140">在对活动调用验证时，这些警告或错误会包含在对 <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> 的调用所返回的集合中。</span><span class="sxs-lookup"><span data-stu-id="bdad0-140">When validation is invoked on the activity, these warnings or errors are contained in the collection returned by the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="bdad0-141">下面的示例定义了一个 `CreateProduct` 活动。</span><span class="sxs-lookup"><span data-stu-id="bdad0-141">In the following example, a `CreateProduct` activity is defined.</span></span> <span data-ttu-id="bdad0-142">如果 `Cost` 大于 `Price`，则会向 <xref:System.Activities.CodeActivity.CacheMetadata%2A> 重写中的元数据添加一个验证错误。</span><span class="sxs-lookup"><span data-stu-id="bdad0-142">If the `Cost` is greater than the `Price`, a validation error is added to the metadata in the <xref:System.Activities.CodeActivity.CacheMetadata%2A> override.</span></span>  
  
```csharp  
public sealed class CreateProduct : CodeActivity  
{  
    public double Price { get; set; }  
    public double Cost { get; set; }  
  
    // [RequiredArgument] attribute will generate a validation error
    // if the Description argument is not set.  
    [RequiredArgument]  
    public InArgument<string> Description { get; set; }  
  
    protected override void CacheMetadata(CodeActivityMetadata metadata)  
    {  
        base.CacheMetadata(metadata);  
        // Determine when the activity has been configured in an invalid way.  
        if (this.Cost > this.Price)  
        {  
            // Add a validation error with a custom message.  
            metadata.AddValidationError("The Cost must be less than or equal to the Price.");  
        }  
    }  
  
    protected override void Execute(CodeActivityContext context)  
    {  
        // Not needed for the sample.  
    }  
}  
```  
  
 <span data-ttu-id="bdad0-143">在此示例中，使用 `CreateProduct` 活动配置工作流。</span><span class="sxs-lookup"><span data-stu-id="bdad0-143">In this example, a workflow is configured using the `CreateProduct` activity.</span></span> <span data-ttu-id="bdad0-144">在此工作流中，`Cost` 大于 `Price`，并且未设置必需的 `Description` 自变量。</span><span class="sxs-lookup"><span data-stu-id="bdad0-144">In this workflow, the `Cost` is greater than the `Price`, and the required `Description` argument is not set.</span></span> <span data-ttu-id="bdad0-145">当调用验证时，将返回以下错误。</span><span class="sxs-lookup"><span data-stu-id="bdad0-145">When validation is invoked, the following errors are returned.</span></span>  
  
```csharp  
Activity wf = new Sequence  
{  
    Activities =
    {  
        new CreateProduct  
        {  
            Cost = 75.00,  
            Price = 55.00  
            // Cost > Price and required Description argument not set.  
        },  
        new WriteLine  
        {  
            Text = "Product added."  
        }  
    }  
};  
  
ValidationResults results = ActivityValidationServices.Validate(wf);  
  
if (results.Errors.Count == 0 && results.Warnings.Count == 0)  
{  
    Console.WriteLine("No warnings or errors");  
}  
else  
{  
    foreach (ValidationError error in results.Errors)  
    {  
        Console.WriteLine("Error: {0}", error.Message);  
    }  
    foreach (ValidationError warning in results.Warnings)  
    {  
        Console.WriteLine("Warning: {0}", warning.Message);  
    }  
}  
```  
  
 <span data-ttu-id="bdad0-146">**Error: The Cost must be less than or equal to the Price.**</span><span class="sxs-lookup"><span data-stu-id="bdad0-146">**Error: The Cost must be less than or equal to the Price.**</span></span>  
<span data-ttu-id="bdad0-147">**Error: Value for a required activity argument 'Description' was not supplied.**</span><span class="sxs-lookup"><span data-stu-id="bdad0-147">**Error: Value for a required activity argument 'Description' was not supplied.**</span></span>
> [!NOTE]
> <span data-ttu-id="bdad0-148">自定义活动作者可以在活动的 <xref:System.Activities.CodeActivity.CacheMetadata%2A> 重写中提供验证逻辑。</span><span class="sxs-lookup"><span data-stu-id="bdad0-148">Custom activity authors can provide validation logic in an activity's <xref:System.Activities.CodeActivity.CacheMetadata%2A> override.</span></span> <span data-ttu-id="bdad0-149">由 <xref:System.Activities.CodeActivity.CacheMetadata%2A> 引发的任何异常不会视为验证错误。</span><span class="sxs-lookup"><span data-stu-id="bdad0-149">Any exceptions that are thrown from <xref:System.Activities.CodeActivity.CacheMetadata%2A> are not treated as validation errors.</span></span> <span data-ttu-id="bdad0-150">这些异常将从对 <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> 的调用中转义，并且必须由调用方进行处理。</span><span class="sxs-lookup"><span data-stu-id="bdad0-150">These exceptions will escape from the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> and must be handled by the caller.</span></span>  
  
## <a name="using-validationsettings"></a><span data-ttu-id="bdad0-151">使用 ValidationSettings</span><span class="sxs-lookup"><span data-stu-id="bdad0-151">Using ValidationSettings</span></span>  

 <span data-ttu-id="bdad0-152">默认情况下，当 <xref:System.Activities.Validation.ActivityValidationServices> 调用验证时，将计算活动树中的所有活动。</span><span class="sxs-lookup"><span data-stu-id="bdad0-152">By default, all activities in the activity tree are evaluated when validation is invoked by <xref:System.Activities.Validation.ActivityValidationServices>.</span></span> <span data-ttu-id="bdad0-153"><xref:System.Activities.Validation.ValidationSettings> 允许通过配置其三个属性，采用多种不同方法来自定义验证。</span><span class="sxs-lookup"><span data-stu-id="bdad0-153"><xref:System.Activities.Validation.ValidationSettings> allows the validation to be customized in several different ways by configuring its three properties.</span></span> <span data-ttu-id="bdad0-154"><xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> 指定验证程序是应遍历整个活动树，还是仅向提供的活动应用验证逻辑。</span><span class="sxs-lookup"><span data-stu-id="bdad0-154"><xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> specifies whether the validator should walk the entire activity tree or only apply validation logic to the supplied activity.</span></span> <span data-ttu-id="bdad0-155">该值的默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="bdad0-155">The default for this value is `false`.</span></span> <span data-ttu-id="bdad0-156"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> 指定从类型映射到约束列表的其他约束。</span><span class="sxs-lookup"><span data-stu-id="bdad0-156"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> specifies additional constraint mapping from a type to a list of constraints.</span></span> <span data-ttu-id="bdad0-157">对于计算的活动树中的每个活动的基类型，将查找 <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>。</span><span class="sxs-lookup"><span data-stu-id="bdad0-157">For the base type of each activity in the activity tree being validated there is a lookup into <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>.</span></span> <span data-ttu-id="bdad0-158">如果找到匹配的约束列表，则会针对活动计算该列表中的所有约束。</span><span class="sxs-lookup"><span data-stu-id="bdad0-158">If a matching constraint list is found, all constraints in the list are evaluated for the activity.</span></span> <span data-ttu-id="bdad0-159"><xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> 指定验证程序是应计算所有约束还是仅计算 <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> 中指定的约束。</span><span class="sxs-lookup"><span data-stu-id="bdad0-159"><xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> specifies whether the validator should evaluate all constraints or only those specified in <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>.</span></span> <span data-ttu-id="bdad0-160">默认值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="bdad0-160">The default value is `false`.</span></span> <span data-ttu-id="bdad0-161"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> 和 <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> 有助于工作流主机作者为工作流添加其他验证，例如，适用于 FxCop 等工具的策略约束。</span><span class="sxs-lookup"><span data-stu-id="bdad0-161"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> and <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> are useful for workflow host authors to add additional validation for workflows, such as policy constraints for tools such as FxCop.</span></span> <span data-ttu-id="bdad0-162">有关约束的详细信息，请参阅 [声明性约束](declarative-constraints.md)。</span><span class="sxs-lookup"><span data-stu-id="bdad0-162">For more information about constraints, see [Declarative Constraints](declarative-constraints.md).</span></span>  
  
 <span data-ttu-id="bdad0-163">若要使用 <xref:System.Activities.Validation.ValidationSettings>，请配置所需属性，然后在调用 <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> 时传递这些属性。</span><span class="sxs-lookup"><span data-stu-id="bdad0-163">To use <xref:System.Activities.Validation.ValidationSettings>, configure the desired properties, and then pass it in the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="bdad0-164">在此示例中，将验证由包含自定义 <xref:System.Activities.Statements.Sequence> 活动的 `Add` 组成的工作流。</span><span class="sxs-lookup"><span data-stu-id="bdad0-164">In this example, a workflow that consists of a <xref:System.Activities.Statements.Sequence> with a custom `Add` activity is validated.</span></span> <span data-ttu-id="bdad0-165">`Add` 活动具有两个必需自变量。</span><span class="sxs-lookup"><span data-stu-id="bdad0-165">The `Add` activity has two required arguments.</span></span>  
  
```csharp  
public sealed class Add : CodeActivity<int>  
{  
    [RequiredArgument]  
    public InArgument<int> Operand1 { get; set; }  
  
    [RequiredArgument]  
    public InArgument<int> Operand2 { get; set; }  
  
    protected override int Execute(CodeActivityContext context)  
    {  
        return Operand1.Get(context) + Operand2.Get(context);  
    }  
}  
```  
  
 <span data-ttu-id="bdad0-166">下面的 `Add` 活动在 <xref:System.Activities.Statements.Sequence> 中使用，但未绑定该活动的两个必需自变量。</span><span class="sxs-lookup"><span data-stu-id="bdad0-166">The following `Add` activity is used in a <xref:System.Activities.Statements.Sequence>, but its two required arguments are not bound.</span></span>  
  
```csharp  
Variable<int> Operand1 = new Variable<int> { Default = 10 };  
Variable<int> Operand2 = new Variable<int> { Default = 15 };  
Variable<int> Result = new Variable<int>();  
  
Activity wf = new Sequence  
{  
    Variables = { Operand1, Operand2, Result },  
    Activities =
    {  
        new Add(),  
        new WriteLine  
        {  
            Text = new InArgument<string>(env => "The result is " + Result.Get(env))  
        }  
    }  
};  
```  
  
 <span data-ttu-id="bdad0-167">在下面的示例中，将执行验证，并将 <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> 设置为 `true`，以便仅验证 <xref:System.Activities.Statements.Sequence> 根活动。</span><span class="sxs-lookup"><span data-stu-id="bdad0-167">For the following example, validation is performed with <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> set to `true`, so only the root <xref:System.Activities.Statements.Sequence> activity is validated.</span></span>  
  
```csharp  
ValidationSettings settings = new ValidationSettings  
{  
    SingleLevel = true  
};  
  
ValidationResults results = ActivityValidationServices.Validate(wf, settings);  
  
if (results.Errors.Count == 0 && results.Warnings.Count == 0)  
{  
    Console.WriteLine("No warnings or errors");  
}  
else  
{  
    foreach (ValidationError error in results.Errors)  
    {  
        Console.WriteLine("Error: {0}", error.Message);  
    }  
    foreach (ValidationError warning in results.Warnings)  
    {  
        Console.WriteLine("Warning: {0}", warning.Message);  
    }  
}  
```  
  
 <span data-ttu-id="bdad0-168">此代码显示以下输出内容：</span><span class="sxs-lookup"><span data-stu-id="bdad0-168">This code displays the following output:</span></span>  
  
 <span data-ttu-id="bdad0-169">**无警告或错误** 即使 `Add` 活动具有所需的未绑定参数，验证仍会成功，因为只计算根活动。</span><span class="sxs-lookup"><span data-stu-id="bdad0-169">**No warnings or errors** Even though the `Add` activity has required arguments that are not bound, validation is successful because only the root activity is evaluated.</span></span> <span data-ttu-id="bdad0-170">此验证类型对于只验证活动树中的特定元素非常有用，例如，在设计器中验证单个活动的属性更改。</span><span class="sxs-lookup"><span data-stu-id="bdad0-170">This type of validation is useful for validating only specific elements in an activity tree, such as validation of a property change of a single activity in a designer.</span></span> <span data-ttu-id="bdad0-171">请注意，如果将调用此工作流，将计算在工作流中配置的完全验证，并且将引发 <xref:System.Activities.InvalidWorkflowException>。</span><span class="sxs-lookup"><span data-stu-id="bdad0-171">Note that if this workflow is invoked, the full validation configured in the workflow is evaluated and an <xref:System.Activities.InvalidWorkflowException> would be thrown.</span></span> <span data-ttu-id="bdad0-172"><xref:System.Activities.Validation.ActivityValidationServices> 和 <xref:System.Activities.Validation.ValidationSettings> 仅配置主机显式调用的验证，而不会配置在调用工作流时所执行的验证。</span><span class="sxs-lookup"><span data-stu-id="bdad0-172"><xref:System.Activities.Validation.ActivityValidationServices> and <xref:System.Activities.Validation.ValidationSettings> configure only validation explicitly invoked by the host, and not the validation that occurs when a workflow is invoked.</span></span>
