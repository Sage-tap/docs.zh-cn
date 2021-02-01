---
title: 如何了解向方法传递结构和向方法传递类引用之间的区别（C# 编程指南）
description: 使用 C# 向方法传递结构不同于向方法传递类实例。 此示例显示按值传递的结构和类实例。
ms.date: 07/20/2015
helpviewer_keywords:
- structs [C#], passing as method parameter
- passing parameters [C#], structs vs. classes
- methods [C#], passing classes vs. structs
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: 9c1313a6-32a8-4ea7-a59f-450f66af628b
ms.openlocfilehash: a4d969617b450fcd788764e97afe3aa1ff19a48c
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/27/2021
ms.locfileid: "98898796"
---
# <a name="how-to-know-the-difference-between-passing-a-struct-and-passing-a-class-reference-to-a-method-c-programming-guide"></a><span data-ttu-id="8e686-104">如何了解向方法传递结构和向方法传递类引用之间的区别（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="8e686-104">How to know the difference between passing a struct and passing a class reference to a method (C# Programming Guide)</span></span>

<span data-ttu-id="8e686-105">下面的示例演示向方法传递[结构](../../language-reference/builtin-types/struct.md)和向方法传递[类](../../language-reference/keywords/class.md)实例之间的区别。</span><span class="sxs-lookup"><span data-stu-id="8e686-105">The following example demonstrates how passing a [struct](../../language-reference/builtin-types/struct.md) to a method differs from passing a [class](../../language-reference/keywords/class.md) instance to a method.</span></span> <span data-ttu-id="8e686-106">在此示例中，这两个参数（结构和类实例）都按值传递，并且两个方法都更改了参数的一个字段的值。</span><span class="sxs-lookup"><span data-stu-id="8e686-106">In the example, both of the arguments (struct and class instance) are passed by value, and both methods change the value of one field of the argument.</span></span> <span data-ttu-id="8e686-107">但是，由于传递结构和传递类实例时所传递的内容不同，所以这两个方法的结果不同。</span><span class="sxs-lookup"><span data-stu-id="8e686-107">However, the results of the two methods are not the same because what is passed when you pass a struct differs from what is passed when you pass an instance of a class.</span></span>  
  
 <span data-ttu-id="8e686-108">因为结构是[值类型](../../language-reference/builtin-types/value-types.md)，所以[按值将结构传递](./passing-value-type-parameters.md)给方法时，该方法接收结构参数的副本并在其上运行。</span><span class="sxs-lookup"><span data-stu-id="8e686-108">Because a struct is a [value type](../../language-reference/builtin-types/value-types.md), when you [pass a struct by value](./passing-value-type-parameters.md) to a method, the method receives and operates on a copy of the struct argument.</span></span> <span data-ttu-id="8e686-109">该方法无法访问调用方法中的原始结构，因此无法对其进行任何更改。</span><span class="sxs-lookup"><span data-stu-id="8e686-109">The method has no access to the original struct in the calling method and therefore can't change it in any way.</span></span> <span data-ttu-id="8e686-110">它只能更改副本。</span><span class="sxs-lookup"><span data-stu-id="8e686-110">The method can change only the copy.</span></span>  
  
 <span data-ttu-id="8e686-111">类实例是[引用类型](../../language-reference/keywords/reference-types.md)，不是值类型。</span><span class="sxs-lookup"><span data-stu-id="8e686-111">A class instance is a [reference type](../../language-reference/keywords/reference-types.md), not a value type.</span></span> <span data-ttu-id="8e686-112">[按值将引用类型传递](./passing-reference-type-parameters.md)给方法时，方法接收对类实例的引用的副本。</span><span class="sxs-lookup"><span data-stu-id="8e686-112">When [a reference type is passed by value](./passing-reference-type-parameters.md) to a method, the method receives a copy of the reference to the class instance.</span></span> <span data-ttu-id="8e686-113">也就是说，被调用的方法接收实例的地址副本，而调用方法保留实例的原始地址。</span><span class="sxs-lookup"><span data-stu-id="8e686-113">That is, the called method receives a copy of the address of the instance, and the calling method retains the original address of the instance.</span></span> <span data-ttu-id="8e686-114">调用方法中的类实例具有地址，所调用的方法中的参数具有地址副本，且这两个地址引用同一个对象。</span><span class="sxs-lookup"><span data-stu-id="8e686-114">The class instance in the calling method has an address, the parameter in the called method has a copy of the address, and both addresses refer to the same object.</span></span> <span data-ttu-id="8e686-115">由于参数只包含地址副本，因此所调用的方法不能更改调用方法中类实例的地址。</span><span class="sxs-lookup"><span data-stu-id="8e686-115">Because the parameter contains only a copy of the address, the called method cannot change the address of the class instance in the calling method.</span></span> <span data-ttu-id="8e686-116">但是，被调用的方法可以使用该地址的副本来访问原始地址和地址副本引用的类成员。</span><span class="sxs-lookup"><span data-stu-id="8e686-116">However, the called method can use the copy of the address to access the class members that both the original address and the copy of the address reference.</span></span> <span data-ttu-id="8e686-117">如果所调用的方法更改了类成员，则调用方法中的原始类实例也会更改。</span><span class="sxs-lookup"><span data-stu-id="8e686-117">If the called method changes a class member, the original class instance in the calling method also changes.</span></span>  
  
 <span data-ttu-id="8e686-118">以下示例输出对差异进行了说明。</span><span class="sxs-lookup"><span data-stu-id="8e686-118">The output of the following example illustrates the difference.</span></span> <span data-ttu-id="8e686-119">调用 `ClassTaker` 方法更改了类实例的 `willIChange` 字段的值，因为该方法使用参数中的地址来查找类实例的指定字段。</span><span class="sxs-lookup"><span data-stu-id="8e686-119">The value of the `willIChange` field of the class instance is changed by the call to method `ClassTaker` because the method uses the address in the parameter to find the specified field of the class instance.</span></span> <span data-ttu-id="8e686-120">调用 `StructTaker` 方法不会更改调用方法中结构的 `willIChange` 字段，因为该参数的值是结构本身的副本，而不是其地址的副本。</span><span class="sxs-lookup"><span data-stu-id="8e686-120">The `willIChange` field of the struct in the calling method is not changed by the call to method `StructTaker` because the value of the argument is a copy of the struct itself, not a copy of its address.</span></span> <span data-ttu-id="8e686-121">`StructTaker` 更改副本，对 `StructTaker` 的调用完成时，副本丢失。</span><span class="sxs-lookup"><span data-stu-id="8e686-121">`StructTaker` changes the copy, and the copy is lost when the call to `StructTaker` is completed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e686-122">示例</span><span class="sxs-lookup"><span data-stu-id="8e686-122">Example</span></span>  

 [!code-csharp[PassingStructVsClass](snippets/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method/Program.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="8e686-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="8e686-123">See also</span></span>

- [<span data-ttu-id="8e686-124">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="8e686-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="8e686-125">类</span><span class="sxs-lookup"><span data-stu-id="8e686-125">Classes</span></span>](./classes.md)
- [<span data-ttu-id="8e686-126">结构类型</span><span class="sxs-lookup"><span data-stu-id="8e686-126">Structure types</span></span>](../../language-reference/builtin-types/struct.md)
- [<span data-ttu-id="8e686-127">传递参数</span><span class="sxs-lookup"><span data-stu-id="8e686-127">Passing Parameters</span></span>](./passing-parameters.md)
