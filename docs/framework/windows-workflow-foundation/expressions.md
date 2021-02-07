---
description: 了解更多：表达式
title: 表达式-WF
ms.date: 03/30/2017
ms.assetid: c42341a9-43a1-462c-bffb-c5de004aa428
ms.openlocfilehash: de16168585e2bbcbf8251c8e4b7c06784d72859d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742350"
---
# <a name="expressions"></a><span data-ttu-id="d7c3e-103">表达式</span><span class="sxs-lookup"><span data-stu-id="d7c3e-103">Expressions</span></span>

<span data-ttu-id="d7c3e-104">Windows Workflow Foundation (WF) 表达式是返回结果的任何活动。</span><span class="sxs-lookup"><span data-stu-id="d7c3e-104">A Windows Workflow Foundation (WF) expression is any activity that returns a result.</span></span> <span data-ttu-id="d7c3e-105">从 <xref:System.Activities.Activity%601> 间接派生的所有表达式活动，其中包含名为 <xref:System.Activities.OutArgument> 的 <xref:System.Activities.Activity%601.Result%2A> 属性作为活动的返回值。</span><span class="sxs-lookup"><span data-stu-id="d7c3e-105">All expression activities derive indirectly from <xref:System.Activities.Activity%601>, which contains an <xref:System.Activities.OutArgument> property named <xref:System.Activities.Activity%601.Result%2A> as the activity’s return value.</span></span> [!INCLUDE[wf1](../../../includes/wf1-md.md)] <span data-ttu-id="d7c3e-106">随附了从简单活动（如 <xref:System.Activities.Expressions.VariableValue%601> 和 <xref:System.Activities.Expressions.VariableReference%601>，它们通过运算符活动提供对单个工作流变量的访问）到复杂活动（如 <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> 和 <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>，它们提供对 Visual Basic 语言的全面访问，以获得结果）的广泛表达式活动。</span><span class="sxs-lookup"><span data-stu-id="d7c3e-106">ships with a wide range of expression activities from simple ones like <xref:System.Activities.Expressions.VariableValue%601> and <xref:System.Activities.Expressions.VariableReference%601>, which provide access to single workflow variable through operator activities, to complex activities such as <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> and <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> that offer access to the full breadth of Visual Basic language to produce the result.</span></span> <span data-ttu-id="d7c3e-107">可以通过从 <xref:System.Activities.CodeActivity%601> 或 <xref:System.Activities.NativeActivity%601> 派生来创建其他表达式活动。</span><span class="sxs-lookup"><span data-stu-id="d7c3e-107">Additional expression activities can be created by deriving from <xref:System.Activities.CodeActivity%601> or <xref:System.Activities.NativeActivity%601>.</span></span>

## <a name="using-expressions"></a><span data-ttu-id="d7c3e-108">使用表达式</span><span class="sxs-lookup"><span data-stu-id="d7c3e-108">Using Expressions</span></span>

 <span data-ttu-id="d7c3e-109">工作流设计器对 Visual Basic 项目中的所有表达式使用 <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> 和 <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601>，对 C# 工作流项目中的所有表达式使用 <xref:Microsoft.CSharp.Activities.CSharpValue%601> 和 <xref:Microsoft.CSharp.Activities.CSharpReference%601>。</span><span class="sxs-lookup"><span data-stu-id="d7c3e-109">Workflow designer uses <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> and <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> for all expressions in Visual Basic projects, and <xref:Microsoft.CSharp.Activities.CSharpValue%601> and <xref:Microsoft.CSharp.Activities.CSharpReference%601> for expressions in C# workflow projects.</span></span>

> [!NOTE]
> <span data-ttu-id="d7c3e-110">.NET Framework 4.5 中引入了对工作流项目中的 c # 表达式的支持。</span><span class="sxs-lookup"><span data-stu-id="d7c3e-110">Support for C# expressions in workflow projects was introduced in .NET Framework 4.5.</span></span> <span data-ttu-id="d7c3e-111">有关详细信息，请参阅 [c # 表达式](csharp-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="d7c3e-111">For more information, see [C# Expressions](csharp-expressions.md).</span></span>

 <span data-ttu-id="d7c3e-112">设计器生成的工作流保存在 XAML 中，其中表达式位于方括号中，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="d7c3e-112">Workflows produced by designer are saved in XAML, where expressions appear enclosed in square brackets, as in the following example.</span></span>

```xml
<Sequence xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">
  <Sequence.Variables>
    <Variable x:TypeArguments="x:Int32" Default="1" Name="a" />
    <Variable x:TypeArguments="x:Int32" Default="2" Name="b" />
    <Variable x:TypeArguments="x:Int32" Default="3" Name="c" />
    <Variable x:TypeArguments="x:Int32" Default="0" Name="r" />
  </Sequence.Variables>
  <Assign>
    <Assign.To>
      <OutArgument x:TypeArguments="x:Int32">[r]</OutArgument>
    </Assign.To>
    <Assign.Value>
      <InArgument x:TypeArguments="x:Int32">[a + b + c]</InArgument>
    </Assign.Value>
  </Assign>
</Sequence>
```

 <span data-ttu-id="d7c3e-113">在代码中定义工作流时，可以使用所有表达式活动。</span><span class="sxs-lookup"><span data-stu-id="d7c3e-113">When defining a workflow in code, any expression activities can be used.</span></span> <span data-ttu-id="d7c3e-114">下面的示例演示如何使用运算符活动的组合添加三个数字：</span><span class="sxs-lookup"><span data-stu-id="d7c3e-114">The following example shows the usage of a composition of operator activities to add three numbers:</span></span>

```csharp
Variable<int> a = new Variable<int>("a", 1);
Variable<int> b = new Variable<int>("b", 2);
Variable<int> c = new Variable<int>("c", 3);
Variable<int> r = new Variable<int>("r", 0);

Sequence w = new Sequence
{
    Variables = { a, b, c, r },
    Activities =
    {
        new Assign {
            To = new OutArgument<int>(r),
            Value = new InArgument<int> {
                Expression = new Add<int, int, int> {
                    Left = new Add<int, int, int> {
                        Left = new InArgument<int>(a),
                        Right = new InArgument<int>(b)
                    },
                    Right = new InArgument<int>(c)
                }
            }
        }
    }
};
```

 <span data-ttu-id="d7c3e-115">使用 c # lambda 表达式可以更简洁地地表示相同的工作流，如下面的示例中所示：</span><span class="sxs-lookup"><span data-stu-id="d7c3e-115">The same workflow can be expressed more compactly by using C# lambda expressions, as shown in the following example:</span></span>
  
```csharp
Variable<int> a = new Variable<int>("a", 1);
Variable<int> b = new Variable<int>("b", 2);
Variable<int> c = new Variable<int>("c", 3);
Variable<int> r = new Variable<int>("r", 0);

Sequence w = new Sequence
{
    Variables = { a, b, c, r },
    Activities =
    {
        new Assign {
            To = new OutArgument<int>(r),
            Value = new InArgument<int>((ctx) => a.Get(ctx) + b.Get(ctx) + c.Get(ctx))
        }
    }
};
```

## <a name="extending-available-expressions-with-custom-expression-activities"></a><span data-ttu-id="d7c3e-116">使用自定义表达式活动扩展可用的表达式</span><span class="sxs-lookup"><span data-stu-id="d7c3e-116">Extending Available Expressions with Custom Expression Activities</span></span>

 <span data-ttu-id="d7c3e-117">可以扩展 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 中的表达式，从而允许创建其他表达式活动。</span><span class="sxs-lookup"><span data-stu-id="d7c3e-117">Expressions in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] are extensible allowing for additional expression activities to be created.</span></span> <span data-ttu-id="d7c3e-118">下面的示例演示返回三个整数值之和的活动。</span><span class="sxs-lookup"><span data-stu-id="d7c3e-118">The following example shows an activity that returns a sum of three integer values.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Activities;

namespace ExpressionsDemo
{
    public sealed class AddThreeValues : CodeActivity<int>
    {
        public InArgument<int> Value1 { get; set; }
        public InArgument<int> Value2 { get; set; }
        public InArgument<int> Value3 { get; set; }

        protected override int Execute(CodeActivityContext context)
        {
            return Value1.Get(context) +
                   Value2.Get(context) +
                   Value3.Get(context);
        }
    }
}
```

 <span data-ttu-id="d7c3e-119">利用此新活动，你可以重写之前添加了三个值的工作流，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="d7c3e-119">With this new activity you can rewrite the previous workflow that added three values as shown in the following example:</span></span>

```csharp
Variable<int> a = new Variable<int>("a", 1);
Variable<int> b = new Variable<int>("b", 2);
Variable<int> c = new Variable<int>("c", 3);
Variable<int> r = new Variable<int>("r", 0);

Sequence w = new Sequence
{
    Variables = { a, b, c, r },
    Activities =
    {
        new Assign {
            To = new OutArgument<int>(r),
            Value = new InArgument<int> {
                Expression = new AddThreeValues() {
                    Value1 = new InArgument<int>(a),
                    Value2 = new InArgument<int>(b),
                    Value3 = new InArgument<int>(c)
                }
            }
        }
    }
};
```

 <span data-ttu-id="d7c3e-120">有关在代码中使用表达式的详细信息，请参阅 [使用命令性代码创作工作流、活动和表达式](authoring-workflows-activities-and-expressions-using-imperative-code.md)。</span><span class="sxs-lookup"><span data-stu-id="d7c3e-120">For more information about using expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>
