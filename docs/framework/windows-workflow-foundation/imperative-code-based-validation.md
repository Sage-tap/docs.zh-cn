---
description: 了解详细信息：命令性 Code-Based 验证
title: 基于命令性代码的验证
ms.date: 03/30/2017
ms.assetid: ae12537c-455e-42b1-82f4-cea4c46c023e
ms.openlocfilehash: 36759572393be613a569c4846e3610fcbbde2a51
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792695"
---
# <a name="imperative-code-based-validation"></a><span data-ttu-id="a7a0a-103">基于命令性代码的验证</span><span class="sxs-lookup"><span data-stu-id="a7a0a-103">Imperative Code-Based Validation</span></span>

<span data-ttu-id="a7a0a-104">基于命令性代码的验证为活动提供用于自身验证的简单方法，并且该方法可用于从 <xref:System.Activities.CodeActivity>、<xref:System.Activities.AsyncCodeActivity> 和 <xref:System.Activities.NativeActivity> 派生的活动。</span><span class="sxs-lookup"><span data-stu-id="a7a0a-104">Imperative code-based validation provides a simple way for an activity to provide validation about itself, and is available for activities that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, and <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="a7a0a-105">会向活动中添加确定所有验证错误或警告的验证代码。</span><span class="sxs-lookup"><span data-stu-id="a7a0a-105">Validation code that determines any validation errors or warnings is added to the activity.</span></span>  
  
## <a name="using-code-based-validation"></a><span data-ttu-id="a7a0a-106">使用基于代码的验证</span><span class="sxs-lookup"><span data-stu-id="a7a0a-106">Using Code-Based Validation</span></span>

<span data-ttu-id="a7a0a-107">从 <xref:System.Activities.CodeActivity>、<xref:System.Activities.AsyncCodeActivity> 和 <xref:System.Activities.NativeActivity> 派生的活动支持基于代码的验证。</span><span class="sxs-lookup"><span data-stu-id="a7a0a-107">Code-based validation is supported by activities that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, and <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="a7a0a-108">可以将验证代码放置在 <xref:System.Activities.CodeActivity.CacheMetadata%2A> 重写中，并且可以将验证错误或警告添加到元数据自变量中。</span><span class="sxs-lookup"><span data-stu-id="a7a0a-108">Validation code can be placed in the <xref:System.Activities.CodeActivity.CacheMetadata%2A> override, and validation errors or warnings can be added to the metadata argument.</span></span> <span data-ttu-id="a7a0a-109">在下面的示例中，如果 `Cost` 大于 `Price`，则会向元数据中添加一个验证错误。</span><span class="sxs-lookup"><span data-stu-id="a7a0a-109">In the following example, if the `Cost` is greater than the `Price`, a validation error is added to the metadata.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a7a0a-110">请注意，`Cost` 和 `Price` 不是针对活动的自变量，而是在设计时设置的属性。</span><span class="sxs-lookup"><span data-stu-id="a7a0a-110">Note that `Cost` and `Price` are not arguments to the activity, but are properties that are set at design time.</span></span> <span data-ttu-id="a7a0a-111">这就是为什么可以在 <xref:System.Activities.CodeActivity.CacheMetadata%2A> 重写中验证其值的原因。</span><span class="sxs-lookup"><span data-stu-id="a7a0a-111">That is why their values can be validated in the <xref:System.Activities.CodeActivity.CacheMetadata%2A> override.</span></span> <span data-ttu-id="a7a0a-112">流过某一参数的数据值不能在设计时验证，因为在运行时之前数据不流动，但可以对活动参数进行验证，以便确保通过使用 `RequiredArgument` 特性和重载组对它们进行限定。</span><span class="sxs-lookup"><span data-stu-id="a7a0a-112">The value of the data flowing through an argument cannot be validated at design time because the data does not flow until run time, but activity arguments can be validated to ensure that they are bound by using the `RequiredArgument` attribute and overload groups.</span></span> <span data-ttu-id="a7a0a-113">此示例代码查看 `Description` 自变量的 `RequiredArgument` 特性，如果未绑定，则会生成验证错误。</span><span class="sxs-lookup"><span data-stu-id="a7a0a-113">This example code sees the `RequiredArgument` attribute for the `Description` argument, and if it is not bound then a validation error is generated.</span></span> <span data-ttu-id="a7a0a-114">必需的参数在 [所需的参数和重载组](required-arguments-and-overload-groups.md)中进行了介绍。</span><span class="sxs-lookup"><span data-stu-id="a7a0a-114">Required arguments are covered in [Required Arguments and Overload Groups](required-arguments-and-overload-groups.md).</span></span>  
  
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
  
 <span data-ttu-id="a7a0a-115">默认情况下，调用 <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> 时会向元数据中添加一个验证错误。</span><span class="sxs-lookup"><span data-stu-id="a7a0a-115">By default, a validation error is added to the metadata when <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> is called.</span></span> <span data-ttu-id="a7a0a-116">若要添加验证警告，请使用接受 <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> 的 <xref:System.Activities.Validation.ValidationError> 重载，并通过设置 <xref:System.Activities.Validation.ValidationError> 属性来指定 <xref:System.Activities.Validation.ValidationError.IsWarning%2A> 表示一个警告。</span><span class="sxs-lookup"><span data-stu-id="a7a0a-116">To add a validation warning, use the <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> overload that takes a <xref:System.Activities.Validation.ValidationError>, and specify that the <xref:System.Activities.Validation.ValidationError> represents a warning by setting the <xref:System.Activities.Validation.ValidationError.IsWarning%2A> property.</span></span>  
  
 <span data-ttu-id="a7a0a-117">当在工作流设计器中修改工作流，并且工作流设计器中显示任何验证错误或警告时，将执行验证。</span><span class="sxs-lookup"><span data-stu-id="a7a0a-117">Validation occurs when a workflow is modified in the workflow designer and any validation errors or warnings are displayed in the workflow designer.</span></span> <span data-ttu-id="a7a0a-118">此外，当调用工作流时，如果发生任何验证错误，默认验证逻辑将引发 <xref:System.Activities.InvalidWorkflowException>，此时，也将在运行时执行验证。</span><span class="sxs-lookup"><span data-stu-id="a7a0a-118">Validation also occurs at run time when a workflow is invoked and if any validation errors occur, an <xref:System.Activities.InvalidWorkflowException> is thrown by the default validation logic.</span></span> <span data-ttu-id="a7a0a-119">有关调用验证和访问任何验证警告或错误的详细信息，请参阅 [调用活动验证](invoking-activity-validation.md)。</span><span class="sxs-lookup"><span data-stu-id="a7a0a-119">For more information about invoking validation and accessing any validation warnings or errors, see [Invoking Activity Validation](invoking-activity-validation.md).</span></span>  
  
 <span data-ttu-id="a7a0a-120">由 <xref:System.Activities.CodeActivity.CacheMetadata%2A> 引发的任何异常不会视为验证错误。</span><span class="sxs-lookup"><span data-stu-id="a7a0a-120">Any exceptions that are thrown from <xref:System.Activities.CodeActivity.CacheMetadata%2A> are not treated as validation errors.</span></span> <span data-ttu-id="a7a0a-121">这些异常将从对 <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> 的调用中转义，并且必须由调用方进行处理。</span><span class="sxs-lookup"><span data-stu-id="a7a0a-121">These exceptions will escape from the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> and must be handled by the caller.</span></span>  
  
 <span data-ttu-id="a7a0a-122">基于代码的验证对于验证包含代码的活动非常有用，但它看不到工作流中的其他活动。</span><span class="sxs-lookup"><span data-stu-id="a7a0a-122">Code-based validation is useful for validating the activity that contains the code, but it does not have visibility into the other activities in the workflow.</span></span> <span data-ttu-id="a7a0a-123">声明性约束验证提供了验证活动和工作流中的其他活动之间的关系的功能，并在 [声明性约束](declarative-constraints.md) 主题中进行了介绍。</span><span class="sxs-lookup"><span data-stu-id="a7a0a-123">Declarative constraints validation provides the ability to validate the relationships between an activity and other activities in the workflow, and is covered in the [Declarative Constraints](declarative-constraints.md) topic.</span></span>
