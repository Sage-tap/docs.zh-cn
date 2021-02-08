---
description: 了解详细信息：创建自定义流控制活动
title: 创建自定义流控制活动
ms.date: 03/30/2017
ms.assetid: 27f409f6-2d1d-4cfb-9765-93eb2ad667d5
ms.openlocfilehash: c59bff08fe5b4d891a512de296f35de0ade34655
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787911"
---
# <a name="creating-custom-flow-control-activities"></a><span data-ttu-id="a1da2-103">创建自定义流控制活动</span><span class="sxs-lookup"><span data-stu-id="a1da2-103">Creating custom flow control activities</span></span>

<span data-ttu-id="a1da2-104">.NET Framework 包含各种流控制活动，这些活动的工作方式类似于抽象编程结构 (例如 <xref:System.Activities.Statements.Flowchart>) 或标准编程语句 (如 <xref:System.Activities.Statements.If>) 。</span><span class="sxs-lookup"><span data-stu-id="a1da2-104">The .NET Framework contains a variety of flow-control activities that function similarly to abstract programming structures (such as <xref:System.Activities.Statements.Flowchart>)   or to standard programming statements (such as <xref:System.Activities.Statements.If>).</span></span> <span data-ttu-id="a1da2-105">本主题讨论一个示例项目（ [非泛型 ForEach](./samples/non-generic-foreach.md)）的体系结构。</span><span class="sxs-lookup"><span data-stu-id="a1da2-105">This topic discusses the architecture of one of the sample projects, [Non-Generic ForEach](./samples/non-generic-foreach.md).</span></span>  
  
## <a name="creating-the-custom-class"></a><span data-ttu-id="a1da2-106">创建自定义类</span><span class="sxs-lookup"><span data-stu-id="a1da2-106">Creating the custom class</span></span>  

 <span data-ttu-id="a1da2-107">由于非泛型 ForEach 类将需要安排子活动，因此它需要从 <xref:System.Activities.NativeActivity> 派生，这是因为派生自 <xref:System.Workflow.Activities.CodeActivity> 的活动不具有此功能。</span><span class="sxs-lookup"><span data-stu-id="a1da2-107">Since the Non-Generic ForEach class will need to schedule child activities, it will need to derive from <xref:System.Activities.NativeActivity>, since activities that derive from <xref:System.Workflow.Activities.CodeActivity> do not have this functionality.</span></span>  
  
```csharp  
public sealed class ForEach : NativeActivity  
{
}
```  
  
 <span data-ttu-id="a1da2-108">自定义类需要多个成员来存储活动所使用的数据，并提供用于执行该活动的子活动的功能。</span><span class="sxs-lookup"><span data-stu-id="a1da2-108">The custom class requires several members to store data being used by the activity, and to provide functionality to execute the activity’s child activities.</span></span> <span data-ttu-id="a1da2-109">这些成员包括：</span><span class="sxs-lookup"><span data-stu-id="a1da2-109">These members include:</span></span>  
  
- <span data-ttu-id="a1da2-110">`valueEnumerator`：类型为 <xref:System.Activities.Variable%601> 的非公共 <xref:System.Collections.IEnumerator> 用于循环访问项集。</span><span class="sxs-lookup"><span data-stu-id="a1da2-110">`valueEnumerator`: The non-public <xref:System.Activities.Variable%601> of type <xref:System.Collections.IEnumerator> used to iterate over the collection of items.</span></span> <span data-ttu-id="a1da2-111">此成员的类型为 <xref:System.Activities.Variable%601>，由于它是在活动内部而非自变量或公共属性内部使用的，因此如果该对象具有活动外部的来源，则将使用此成员。</span><span class="sxs-lookup"><span data-stu-id="a1da2-111">This member is of type <xref:System.Activities.Variable%601> because it is used internally in the activity, rather than an argument or public property, which would be used if this object were to have an origin outside the activity.</span></span>  
  
- <span data-ttu-id="a1da2-112">`OnChildComplete`：在执行完每个子活动时执行的公共 <xref:System.Activities.CompletionCallback> 属性。</span><span class="sxs-lookup"><span data-stu-id="a1da2-112">`OnChildComplete`: The public <xref:System.Activities.CompletionCallback> property that executes when each child completes execution.</span></span> <span data-ttu-id="a1da2-113">此成员将定义为 CLR 属性，因为其值将不会随活动实例的不同而不同。</span><span class="sxs-lookup"><span data-stu-id="a1da2-113">This member is defined as a CLR property, since its value will not change for different instances of the activity.</span></span>  
  
- <span data-ttu-id="a1da2-114">`Values`：用于子活动的迭代的输入集合。</span><span class="sxs-lookup"><span data-stu-id="a1da2-114">`Values`: The collection of inputs used for the iterations of the child activity.</span></span> <span data-ttu-id="a1da2-115">此成员的类型为 <xref:System.Activities.InArgument%601>，因为该数据的来源位于活动外部，但集合的内容不应在活动执行期间发生更改。</span><span class="sxs-lookup"><span data-stu-id="a1da2-115">This member is of type <xref:System.Activities.InArgument%601>, since the origin of the data is outside the activity, but the contents of the collection is not expected to change during the execution of the activity.</span></span> <span data-ttu-id="a1da2-116">如果该活动需要此功能以便在活动执行期间更改此集合的内容（例如，添加或移除活动），则此成员应已定义为 <xref:System.Activities.ActivityAction>，之后，每当访问该成员时，系统都会对其进行计算，以使更改对该活动可用。</span><span class="sxs-lookup"><span data-stu-id="a1da2-116">If the activity needed the functionality to change the contents of this collection while the activity was executing (to add or remove activities, for instance), this member would have been defined as an <xref:System.Activities.ActivityAction>, which then would have been evaluated every time it was accessed, so that changes would be available to the activity.</span></span>  
  
- <span data-ttu-id="a1da2-117">`Body`：此成员定义将为 `Values` 集合中的每个项执行的活动。</span><span class="sxs-lookup"><span data-stu-id="a1da2-117">`Body`: This member defines the activity to be executed for each item in the `Values` collection.</span></span> <span data-ttu-id="a1da2-118">此成员定义为 <xref:System.Activities.ActivityAction>，以便每当访问此成员时，系统都会对其进行计算。</span><span class="sxs-lookup"><span data-stu-id="a1da2-118">This member is defined as an <xref:System.Activities.ActivityAction> so that it is evaluated every time it is accessed.</span></span>  
  
- <span data-ttu-id="a1da2-119">`Execute`：此方法使用 `InternalExecute`、`OnForEachComplete` 和 `GetStateAndExecute` 非公共成员来安排执行和分配 Body 成员中定义的子活动的完成处理程序。</span><span class="sxs-lookup"><span data-stu-id="a1da2-119">`Execute`: This method uses the `InternalExecute`, `OnForEachComplete`, and `GetStateAndExecute` non-public members to schedule the execution and assign the completion handler of the child activity defined in the Body member.</span></span>  
  
- <span data-ttu-id="a1da2-120">`CacheMetadata`：此成员为运行时提供了执行活动所需的信息。</span><span class="sxs-lookup"><span data-stu-id="a1da2-120">`CacheMetadata`: This member provides the runtime with the information it needs to execute the activity.</span></span> <span data-ttu-id="a1da2-121">默认情况下，一个活动的 `CacheMetadata` 方法会将该活动的所有公共成员告知运行时，但由于此活动对某些功能使用了私有成员，因此它需要告知运行时存在这些私有成员，以便运行时能注意到它们。</span><span class="sxs-lookup"><span data-stu-id="a1da2-121">By default, an activity’s `CacheMetadata` method will inform the runtime of all public members of the activity, but since this activity uses private members for some functionality, it needs to inform the runtime of their existence so that the runtime can be aware of them.</span></span> <span data-ttu-id="a1da2-122">在此示例中，将重写 `CacheMetadata` 函数以便能访问私有 `valueEnumerator` 成员。</span><span class="sxs-lookup"><span data-stu-id="a1da2-122">In this case, the `CacheMetadata` function is overridden so that the private `valueEnumerator` member can be accessed.</span></span> <span data-ttu-id="a1da2-123">此成员还为该活动的值创建了一个自变量，以便这些值能在执行期间传入该活动中。</span><span class="sxs-lookup"><span data-stu-id="a1da2-123">This member also creates an argument for the values for the activity so that they can be passed in to the activity during execution.</span></span>
