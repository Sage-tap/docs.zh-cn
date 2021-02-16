---
title: 延迟表达式
description: '了解 F # 惰性表达式如何提高应用程序和库的性能。'
ms.date: 08/15/2020
ms.openlocfilehash: 0b8496467295ce6793f80c341af88bb1819f4a47
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100425498"
---
# <a name="lazy-expressions"></a><span data-ttu-id="3afac-103">延迟表达式</span><span class="sxs-lookup"><span data-stu-id="3afac-103">Lazy Expressions</span></span>

<span data-ttu-id="3afac-104">*惰性表达式* 是不会立即计算的表达式，而是在需要结果时计算的表达式。</span><span class="sxs-lookup"><span data-stu-id="3afac-104">*Lazy expressions* are expressions that are not evaluated immediately, but are instead evaluated when the result is needed.</span></span> <span data-ttu-id="3afac-105">这有助于提高代码的性能。</span><span class="sxs-lookup"><span data-stu-id="3afac-105">This can help to improve the performance of your code.</span></span>

## <a name="syntax"></a><span data-ttu-id="3afac-106">语法</span><span class="sxs-lookup"><span data-stu-id="3afac-106">Syntax</span></span>

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a><span data-ttu-id="3afac-107">备注</span><span class="sxs-lookup"><span data-stu-id="3afac-107">Remarks</span></span>

<span data-ttu-id="3afac-108">在前面的语法中， *expression* 是只在需要结果时计算的代码，而 *标识符* 是存储结果的值。</span><span class="sxs-lookup"><span data-stu-id="3afac-108">In the previous syntax, *expression* is code that is evaluated only when a result is required, and *identifier* is a value that stores the result.</span></span> <span data-ttu-id="3afac-109">值的类型为 `Lazy<'T>` ，其中用于的实际类型 `'T` 由表达式的结果确定。</span><span class="sxs-lookup"><span data-stu-id="3afac-109">The value is of type `Lazy<'T>`, where the actual type that is used for `'T` is determined from the result of the expression.</span></span>

<span data-ttu-id="3afac-110">利用迟缓表达式，你可以通过将表达式的执行限制为仅需要结果的情况来提高性能。</span><span class="sxs-lookup"><span data-stu-id="3afac-110">Lazy expressions enable you to improve performance by restricting the execution of an expressions to only those situations in which a result is needed.</span></span>

<span data-ttu-id="3afac-111">若要强制执行表达式，请调用方法 `Force` 。</span><span class="sxs-lookup"><span data-stu-id="3afac-111">To force the expressions to be performed, you call the method `Force`.</span></span> <span data-ttu-id="3afac-112">`Force` 导致执行只执行一次。</span><span class="sxs-lookup"><span data-stu-id="3afac-112">`Force` causes the execution to be performed only one time.</span></span> <span data-ttu-id="3afac-113">后续调用将 `Force` 返回相同的结果，但不执行任何代码。</span><span class="sxs-lookup"><span data-stu-id="3afac-113">Subsequent calls to `Force` return the same result, but do not execute any code.</span></span>

<span data-ttu-id="3afac-114">下面的代码演示了如何使用延迟表达式以及如何使用 `Force` 。</span><span class="sxs-lookup"><span data-stu-id="3afac-114">The following code illustrates the use of lazy expressions and the use of `Force`.</span></span> <span data-ttu-id="3afac-115">在此代码中，的类型 `result` 为 `Lazy<int>` ，并且 `Force` 方法返回 `int` 。</span><span class="sxs-lookup"><span data-stu-id="3afac-115">In this code, the type of `result` is `Lazy<int>`, and the `Force` method returns an `int`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

<span data-ttu-id="3afac-116">迟缓计算（但不 `Lazy` 是类型）也用于序列。</span><span class="sxs-lookup"><span data-stu-id="3afac-116">Lazy evaluation, but not the `Lazy` type, is also used for sequences.</span></span> <span data-ttu-id="3afac-117">有关详细信息，请参阅 [序列](sequences.md)。</span><span class="sxs-lookup"><span data-stu-id="3afac-117">For more information, see [Sequences](sequences.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3afac-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3afac-118">See also</span></span>

- [<span data-ttu-id="3afac-119">F# 语言参考</span><span class="sxs-lookup"><span data-stu-id="3afac-119">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="3afac-120">LazyExtensions 模块</span><span class="sxs-lookup"><span data-stu-id="3afac-120">LazyExtensions module</span></span>](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-lazyextensions.html)
