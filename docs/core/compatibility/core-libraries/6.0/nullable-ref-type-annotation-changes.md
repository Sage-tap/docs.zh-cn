---
title: 中断性变更：可以为 Null 的引用类型注释的更改
description: 了解核心 .NET 库中的 .NET 6.0 中断性变更，在这些库中，一些可以为 Null 的引用类型注释已更改。
ms.date: 02/11/2021
ms.openlocfilehash: a0133ce49ba33d0e835b718f3f2b19180526c61b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100488192"
---
# <a name="changes-to-nullable-reference-type-annotations"></a><span data-ttu-id="d5d42-103">对可以为 Null 的引用类型注释的更改</span><span class="sxs-lookup"><span data-stu-id="d5d42-103">Changes to nullable reference type annotations</span></span>

<span data-ttu-id="d5d42-104">在 .NET 6.0 中，.NET 库中的一些“为 Null 性”注释已更改。</span><span class="sxs-lookup"><span data-stu-id="d5d42-104">In .NET 6.0, some nullability annotations in the .NET libraries have changed.</span></span>

## <a name="change-description"></a><span data-ttu-id="d5d42-105">更改描述</span><span class="sxs-lookup"><span data-stu-id="d5d42-105">Change description</span></span>

<span data-ttu-id="d5d42-106">在以前的 .NET 版本中，一些可以为 Null 的引用类型注释不正确，并且生成警告要么缺失要么不正确。</span><span class="sxs-lookup"><span data-stu-id="d5d42-106">In previous .NET versions, some nullable reference type annotations are incorrect, and build warnings are either absent or incorrect.</span></span> <span data-ttu-id="d5d42-107">从 .NET 6.0 开始，以前应用的一些注释已更新。</span><span class="sxs-lookup"><span data-stu-id="d5d42-107">Starting in .NET 6.0, some annotations that were previously applied have been updated.</span></span> <span data-ttu-id="d5d42-108">对于受影响的 API，将会生成新的生成警告，并且不再生成错误的生成警告。</span><span class="sxs-lookup"><span data-stu-id="d5d42-108">New build warnings will be produced and incorrect build warnings will no longer be produced for the affected APIs.</span></span>

<span data-ttu-id="d5d42-109">其中的某些更改被视为“中断性”变更，因为它们可能会导致新的生成时警告。</span><span class="sxs-lookup"><span data-stu-id="d5d42-109">Some of these changes are considered to be *breaking* because they can lead to new build-time warnings.</span></span> <span data-ttu-id="d5d42-110">迁移到 .NET 6.0 时，需要更新引用这些 API 的代码。</span><span class="sxs-lookup"><span data-stu-id="d5d42-110">When you migrate to .NET 6.0, code that references these APIs will need to be updated.</span></span>

<span data-ttu-id="d5d42-111">此页还介绍了其他不被视为中断性变更的更改。</span><span class="sxs-lookup"><span data-stu-id="d5d42-111">Other changes that aren't considered to be breaking are also documented on this page.</span></span> <span data-ttu-id="d5d42-112">任何引用已更新的 API 的代码都可以从删除不再必要的运算符或 pragma 中受益。</span><span class="sxs-lookup"><span data-stu-id="d5d42-112">Any code that references the updated APIs may benefit from removing operators or pragmas that are no longer unnecessary.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="d5d42-113">引入的版本</span><span class="sxs-lookup"><span data-stu-id="d5d42-113">Version introduced</span></span>

<span data-ttu-id="d5d42-114">6.0</span><span class="sxs-lookup"><span data-stu-id="d5d42-114">6.0</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="d5d42-115">更改原因</span><span class="sxs-lookup"><span data-stu-id="d5d42-115">Reason for change</span></span>

<span data-ttu-id="d5d42-116">从 .NET Core 3.0 开始，已将“为 Null 性”注释应用于 .NET 库。</span><span class="sxs-lookup"><span data-stu-id="d5d42-116">Starting in .NET Core 3.0, nullability annotations were applied to the .NET libraries.</span></span> <span data-ttu-id="d5d42-117">自这项工作伊始，已预料到这些注释中的错误。</span><span class="sxs-lookup"><span data-stu-id="d5d42-117">From the outset of the effort, mistakes in these annotations were anticipated.</span></span> <span data-ttu-id="d5d42-118">通过反馈和进一步测试，已确定受影响 API 的“为 Null 性”注释是不准确的。</span><span class="sxs-lookup"><span data-stu-id="d5d42-118">Through feedback and further testing, the nullable annotations for the affected APIs were determined to be inaccurate.</span></span> <span data-ttu-id="d5d42-119">更新后的注释正确地表示了 API 的“为 Null 性”协定。</span><span class="sxs-lookup"><span data-stu-id="d5d42-119">The updated annotations correctly represent the nullability contracts for the APIs.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="d5d42-120">建议的操作</span><span class="sxs-lookup"><span data-stu-id="d5d42-120">Recommended action</span></span>

<span data-ttu-id="d5d42-121">更新调用这些 API 的代码，以反映修订后的“为 Null 性”协定。</span><span class="sxs-lookup"><span data-stu-id="d5d42-121">Update code that calls these APIs to reflect the revised nullability contracts.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="d5d42-122">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="d5d42-122">Affected APIs</span></span>

<span data-ttu-id="d5d42-123">下表列出了受影响的 API：</span><span class="sxs-lookup"><span data-stu-id="d5d42-123">The following table lists the affected APIs:</span></span>

| <span data-ttu-id="d5d42-124">API</span><span class="sxs-lookup"><span data-stu-id="d5d42-124">API</span></span> | <span data-ttu-id="d5d42-125">更改内容</span><span class="sxs-lookup"><span data-stu-id="d5d42-125">What changed</span></span> | <span data-ttu-id="d5d42-126">中断性或非中断性</span><span class="sxs-lookup"><span data-stu-id="d5d42-126">Breaking or nonbreaking</span></span> | <span data-ttu-id="d5d42-127">新增的版本</span><span class="sxs-lookup"><span data-stu-id="d5d42-127">Version added</span></span> |
| - | - | - |
| <xref:System.ComponentModel.ISite.Container?displayProperty=nameWithType> | <span data-ttu-id="d5d42-128">属性类型可以为 Null</span><span class="sxs-lookup"><span data-stu-id="d5d42-128">Property type is nullable</span></span> | <span data-ttu-id="d5d42-129">重大</span><span class="sxs-lookup"><span data-stu-id="d5d42-129">Breaking</span></span> | <span data-ttu-id="d5d42-130">预览版 1</span><span class="sxs-lookup"><span data-stu-id="d5d42-130">Preview 1</span></span> |
| <xref:System.Xml.Linq.XContainer.Add(System.Object[])?displayProperty=nameWithType> | <span data-ttu-id="d5d42-131">参数类型可以为 Null</span><span class="sxs-lookup"><span data-stu-id="d5d42-131">Parameter type is nullable</span></span> | <span data-ttu-id="d5d42-132">非中断性</span><span class="sxs-lookup"><span data-stu-id="d5d42-132">Nonbreaking</span></span> | <span data-ttu-id="d5d42-133">预览版 1</span><span class="sxs-lookup"><span data-stu-id="d5d42-133">Preview 1</span></span> |
| <xref:System.Xml.Linq.XContainer.AddFirst(System.Object[])?displayProperty=nameWithType> | <span data-ttu-id="d5d42-134">参数类型可以为 Null</span><span class="sxs-lookup"><span data-stu-id="d5d42-134">Parameter type is nullable</span></span> | <span data-ttu-id="d5d42-135">非中断性</span><span class="sxs-lookup"><span data-stu-id="d5d42-135">Nonbreaking</span></span> | <span data-ttu-id="d5d42-136">预览版 1</span><span class="sxs-lookup"><span data-stu-id="d5d42-136">Preview 1</span></span> |
| <xref:System.Xml.Linq.XContainer.ReplaceNodes(System.Object[])?displayProperty=nameWithType> | <span data-ttu-id="d5d42-137">参数类型可以为 Null</span><span class="sxs-lookup"><span data-stu-id="d5d42-137">Parameter type is nullable</span></span> | <span data-ttu-id="d5d42-138">非中断性</span><span class="sxs-lookup"><span data-stu-id="d5d42-138">Nonbreaking</span></span> | <span data-ttu-id="d5d42-139">预览版 1</span><span class="sxs-lookup"><span data-stu-id="d5d42-139">Preview 1</span></span> |
| <xref:System.Xml.Linq.XDocument.%23ctor(System.Object[])> | <span data-ttu-id="d5d42-140">参数类型可以为 Null</span><span class="sxs-lookup"><span data-stu-id="d5d42-140">Parameter type is nullable</span></span> | <span data-ttu-id="d5d42-141">非中断性</span><span class="sxs-lookup"><span data-stu-id="d5d42-141">Nonbreaking</span></span> | <span data-ttu-id="d5d42-142">预览版 1</span><span class="sxs-lookup"><span data-stu-id="d5d42-142">Preview 1</span></span> |
| <xref:System.Xml.Linq.XDocument.%23ctor(System.Xml.Linq.XDeclaration,System.Object[])> | <span data-ttu-id="d5d42-143">参数类型可以为 Null</span><span class="sxs-lookup"><span data-stu-id="d5d42-143">Parameter type is nullable</span></span> | <span data-ttu-id="d5d42-144">非中断性</span><span class="sxs-lookup"><span data-stu-id="d5d42-144">Nonbreaking</span></span> | <span data-ttu-id="d5d42-145">预览版 1</span><span class="sxs-lookup"><span data-stu-id="d5d42-145">Preview 1</span></span> |
| <xref:System.Xml.Linq.XElement.%23ctor(System.Xml.Linq.XName,System.Object[])> | <span data-ttu-id="d5d42-146">第二个参数类型可以为 Null</span><span class="sxs-lookup"><span data-stu-id="d5d42-146">Second parameter type is nullable</span></span> | <span data-ttu-id="d5d42-147">非中断性</span><span class="sxs-lookup"><span data-stu-id="d5d42-147">Nonbreaking</span></span> | <span data-ttu-id="d5d42-148">预览版 1</span><span class="sxs-lookup"><span data-stu-id="d5d42-148">Preview 1</span></span> |
| <xref:System.Xml.Linq.XElement.ReplaceAll(System.Object[])?displayProperty=nameWithType> | <span data-ttu-id="d5d42-149">参数类型可以为 Null</span><span class="sxs-lookup"><span data-stu-id="d5d42-149">Parameter type is nullable</span></span> | <span data-ttu-id="d5d42-150">非中断性</span><span class="sxs-lookup"><span data-stu-id="d5d42-150">Nonbreaking</span></span> | <span data-ttu-id="d5d42-151">预览版 1</span><span class="sxs-lookup"><span data-stu-id="d5d42-151">Preview 1</span></span> |
| <xref:System.Xml.Linq.XElement.ReplaceAttributes(System.Object[])?displayProperty=nameWithType> | <span data-ttu-id="d5d42-152">参数类型可以为 Null</span><span class="sxs-lookup"><span data-stu-id="d5d42-152">Parameter type is nullable</span></span> | <span data-ttu-id="d5d42-153">非中断性</span><span class="sxs-lookup"><span data-stu-id="d5d42-153">Nonbreaking</span></span> | <span data-ttu-id="d5d42-154">预览版 1</span><span class="sxs-lookup"><span data-stu-id="d5d42-154">Preview 1</span></span> |
| <xref:System.Xml.Linq.XNode.AddAfterSelf(System.Object[])?displayProperty=nameWithType> | <span data-ttu-id="d5d42-155">参数类型可以为 Null</span><span class="sxs-lookup"><span data-stu-id="d5d42-155">Parameter type is nullable</span></span> | <span data-ttu-id="d5d42-156">非中断性</span><span class="sxs-lookup"><span data-stu-id="d5d42-156">Nonbreaking</span></span> | <span data-ttu-id="d5d42-157">预览版 1</span><span class="sxs-lookup"><span data-stu-id="d5d42-157">Preview 1</span></span> |
| <xref:System.Xml.Linq.XNode.AddBeforeSelf(System.Object[])?displayProperty=nameWithType> | <span data-ttu-id="d5d42-158">参数类型可以为 Null</span><span class="sxs-lookup"><span data-stu-id="d5d42-158">Parameter type is nullable</span></span> | <span data-ttu-id="d5d42-159">非中断性</span><span class="sxs-lookup"><span data-stu-id="d5d42-159">Nonbreaking</span></span> | <span data-ttu-id="d5d42-160">预览版 1</span><span class="sxs-lookup"><span data-stu-id="d5d42-160">Preview 1</span></span> |
| <xref:System.Xml.Linq.XNode.ReplaceWith(System.Object[])?displayProperty=nameWithType> | <span data-ttu-id="d5d42-161">参数类型可以为 Null</span><span class="sxs-lookup"><span data-stu-id="d5d42-161">Parameter type is nullable</span></span> | <span data-ttu-id="d5d42-162">非中断性</span><span class="sxs-lookup"><span data-stu-id="d5d42-162">Nonbreaking</span></span> | <span data-ttu-id="d5d42-163">预览版 1</span><span class="sxs-lookup"><span data-stu-id="d5d42-163">Preview 1</span></span> |
| <xref:System.Xml.Linq.XStreamingElement.%23ctor(System.Xml.Linq.XName,System.Object)> | <span data-ttu-id="d5d42-164">第二个参数类型可以为 Null</span><span class="sxs-lookup"><span data-stu-id="d5d42-164">Second parameter type is nullable</span></span> | <span data-ttu-id="d5d42-165">非中断性</span><span class="sxs-lookup"><span data-stu-id="d5d42-165">Nonbreaking</span></span> | <span data-ttu-id="d5d42-166">预览版 1</span><span class="sxs-lookup"><span data-stu-id="d5d42-166">Preview 1</span></span> |
| <xref:System.Xml.Linq.XStreamingElement.%23ctor(System.Xml.Linq.XName,System.Object[])> | <span data-ttu-id="d5d42-167">第二个参数类型可以为 Null</span><span class="sxs-lookup"><span data-stu-id="d5d42-167">Second parameter type is nullable</span></span> | <span data-ttu-id="d5d42-168">非中断性</span><span class="sxs-lookup"><span data-stu-id="d5d42-168">Nonbreaking</span></span> | <span data-ttu-id="d5d42-169">预览版 1</span><span class="sxs-lookup"><span data-stu-id="d5d42-169">Preview 1</span></span> |
| <xref:System.Xml.Linq.XStreamingElement.Add(System.Object[])?displayProperty=nameWithType> | <span data-ttu-id="d5d42-170">参数类型可以为 Null</span><span class="sxs-lookup"><span data-stu-id="d5d42-170">Parameter type is nullable</span></span> | <span data-ttu-id="d5d42-171">非中断性</span><span class="sxs-lookup"><span data-stu-id="d5d42-171">Nonbreaking</span></span> | <span data-ttu-id="d5d42-172">预览版 1</span><span class="sxs-lookup"><span data-stu-id="d5d42-172">Preview 1</span></span> |
| <xref:System.Net.Http.HttpClient.PatchAsync%2A?displayProperty=nameWithType> | <span data-ttu-id="d5d42-173">`content` 参数类型可以为 Null</span><span class="sxs-lookup"><span data-stu-id="d5d42-173">`content` parameter type is nullable</span></span> | <span data-ttu-id="d5d42-174">非中断性</span><span class="sxs-lookup"><span data-stu-id="d5d42-174">Nonbreaking</span></span> | <span data-ttu-id="d5d42-175">预览版 1</span><span class="sxs-lookup"><span data-stu-id="d5d42-175">Preview 1</span></span> |
| <xref:System.Net.Http.HttpClient.PostAsync%2A?displayProperty=nameWithType> | <span data-ttu-id="d5d42-176">`content` 参数类型可以为 Null</span><span class="sxs-lookup"><span data-stu-id="d5d42-176">`content` parameter type is nullable</span></span>  | <span data-ttu-id="d5d42-177">非中断性</span><span class="sxs-lookup"><span data-stu-id="d5d42-177">Nonbreaking</span></span> | <span data-ttu-id="d5d42-178">预览版 1</span><span class="sxs-lookup"><span data-stu-id="d5d42-178">Preview 1</span></span> |
| <xref:System.Net.Http.HttpClient.PutAsync%2A?displayProperty=nameWithType> | <span data-ttu-id="d5d42-179">`content` 参数类型可以为 Null</span><span class="sxs-lookup"><span data-stu-id="d5d42-179">`content` parameter type is nullable</span></span>  | <span data-ttu-id="d5d42-180">非中断性</span><span class="sxs-lookup"><span data-stu-id="d5d42-180">Nonbreaking</span></span> | <span data-ttu-id="d5d42-181">预览版 1</span><span class="sxs-lookup"><span data-stu-id="d5d42-181">Preview 1</span></span> |
| <xref:System.Linq.Expressions.MethodCallExpression.Update(System.Linq.Expressions.Expression,System.Collections.Generic.IEnumerable{System.Linq.Expressions.Expression})?displayProperty=nameWithType> | <span data-ttu-id="d5d42-182">第一个参数类型可以为 Null</span><span class="sxs-lookup"><span data-stu-id="d5d42-182">First parameter type is nullable</span></span> | <span data-ttu-id="d5d42-183">非中断性</span><span class="sxs-lookup"><span data-stu-id="d5d42-183">Nonbreaking</span></span> | <span data-ttu-id="d5d42-184">预览版 1</span><span class="sxs-lookup"><span data-stu-id="d5d42-184">Preview 1</span></span> |
| <xref:System.Linq.Expressions.Expression%601.Update(System.Linq.Expressions.Expression,System.Collections.Generic.IEnumerable{System.Linq.Expressions.ParameterExpression})?displayProperty=nameWithType> | <span data-ttu-id="d5d42-185">返回类型不可以为 Null</span><span class="sxs-lookup"><span data-stu-id="d5d42-185">Return type is not nullable</span></span> | <span data-ttu-id="d5d42-186">非中断性</span><span class="sxs-lookup"><span data-stu-id="d5d42-186">Nonbreaking</span></span> | <span data-ttu-id="d5d42-187">预览版 1</span><span class="sxs-lookup"><span data-stu-id="d5d42-187">Preview 1</span></span> |
| <xref:System.Data.IDataRecord.GetBytes(System.Int32,System.Int64,System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="d5d42-188">`buffer` 参数类型可以为 Null</span><span class="sxs-lookup"><span data-stu-id="d5d42-188">`buffer` parameter type is nullable</span></span> | <span data-ttu-id="d5d42-189">重大</span><span class="sxs-lookup"><span data-stu-id="d5d42-189">Breaking</span></span> | <span data-ttu-id="d5d42-190">预览版 1</span><span class="sxs-lookup"><span data-stu-id="d5d42-190">Preview 1</span></span> |
| <xref:System.Data.IDataRecord.GetChars(System.Int32,System.Int64,System.Char[],System.Int32,System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="d5d42-191">`buffer` 参数类型可以为 Null</span><span class="sxs-lookup"><span data-stu-id="d5d42-191">`buffer` parameter type is nullable</span></span> | <span data-ttu-id="d5d42-192">重大</span><span class="sxs-lookup"><span data-stu-id="d5d42-192">Breaking</span></span> | <span data-ttu-id="d5d42-193">预览版 1</span><span class="sxs-lookup"><span data-stu-id="d5d42-193">Preview 1</span></span> |
| <xref:System.Data.Common.DbDataRecord.GetBytes(System.Int32,System.Int64,System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="d5d42-194">`buffer` 参数类型可以为 Null</span><span class="sxs-lookup"><span data-stu-id="d5d42-194">`buffer` parameter type is nullable</span></span> | <span data-ttu-id="d5d42-195">重大</span><span class="sxs-lookup"><span data-stu-id="d5d42-195">Breaking</span></span> | <span data-ttu-id="d5d42-196">预览版 1</span><span class="sxs-lookup"><span data-stu-id="d5d42-196">Preview 1</span></span> |
| <xref:System.Data.Common.DbDataRecord.GetChars(System.Int32,System.Int64,System.Char[],System.Int32,System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="d5d42-197">`buffer` 参数类型可以为 Null</span><span class="sxs-lookup"><span data-stu-id="d5d42-197">`buffer` parameter type is nullable</span></span> | <span data-ttu-id="d5d42-198">重大</span><span class="sxs-lookup"><span data-stu-id="d5d42-198">Breaking</span></span> | <span data-ttu-id="d5d42-199">预览版 1</span><span class="sxs-lookup"><span data-stu-id="d5d42-199">Preview 1</span></span> |

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.ComponentModel.ISite.Container`
- `M:System.Xml.Linq.XContainer.Add(System.Object[])`
- `M:System.Xml.Linq.XContainer.AddFirst(System.Object[])`
- `M:System.Xml.Linq.XContainer.ReplaceNodes(System.Object[])`
- `M:System.Xml.Linq.XDocument.#ctor(System.Object[])`
- `M:System.Xml.Linq.XDocument.#ctor(System.Xml.Linq.XDeclaration,System.Object[])`
- `M:System.Xml.Linq.XElement.#ctor(System.Xml.Linq.XName,System.Object[])`
- `M:System.Xml.Linq.XElement.ReplaceAll(System.Object[])`
- `M:System.Xml.Linq.XElement.ReplaceAttributes(System.Object[])`
- `M:System.Xml.Linq.XNode.AddAfterSelf(System.Object[])`
- `M:System.Xml.Linq.XNode.AddBeforeSelf(System.Object[])`
- `M:System.Xml.Linq.XNode.ReplaceWith(System.Object[])`
- `M:System.Xml.Linq.XStreamingElement.#ctor(System.Xml.Linq.XName,System.Object)`
- `M:System.Xml.Linq.XStreamingElement.#ctor(System.Xml.Linq.XName,System.Object[])`
- `M:System.Xml.Linq.XStreamingElement.Add(System.Object[])`
- `O:System.Net.Http.HttpClient.PatchAsync`
- `O:System.Net.Http.HttpClient.PostAsync`
- `O:System.Net.Http.HttpClient.PutAsync`
- `M:System.Linq.Expressions.MethodCallExpression.Update(System.Linq.Expressions.Expression,System.Collections.Generic.IEnumerable{System.Linq.Expressions.Expression})`
- `M:System.Linq.Expressions.Expression%601.Update(System.Linq.Expressions.Expression,System.Collections.Generic.IEnumerable{System.Linq.Expressions.ParameterExpression})`
- `M:System.Data.IDataRecord.GetBytes(System.Int32,System.Int64,System.Byte[],System.Int32,System.Int32)`
- `M:System.Data.IDataRecord.GetChars(System.Int32,System.Int64,System.Char[],System.Int32,System.Int32)`
- `M:System.Data.Common.DbDataRecord.GetBytes(System.Int32,System.Int64,System.Byte[],System.Int32,System.Int32)`
- `M:System.Data.Common.DbDataRecord.GetChars(System.Int32,System.Int64,System.Char[],System.Int32,System.Int32)`

-->
