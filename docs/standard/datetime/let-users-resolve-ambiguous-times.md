---
description: 了解详细信息：如何：让用户解决不明确的时间
title: 如何：让用户解析不明确的时间
ms.date: 04/10/2017
helpviewer_keywords:
- time zones [.NET], ambiguous time
- ambiguous time [.NET]
ms.assetid: bca874ee-5b68-4654-8bbd-3711220ef332
ms.openlocfilehash: a64d20080ed021af273a2d114c7558615b8b04e4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782476"
---
# <a name="how-to-let-users-resolve-ambiguous-times"></a><span data-ttu-id="8e95a-103">如何：让用户解析不明确的时间</span><span class="sxs-lookup"><span data-stu-id="8e95a-103">How to: Let users resolve ambiguous times</span></span>

<span data-ttu-id="8e95a-104">不明确时间是指映射到多个协调世界时 (UTC) 的时间。</span><span class="sxs-lookup"><span data-stu-id="8e95a-104">An ambiguous time is a time that maps to more than one Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="8e95a-105">在向后调整时钟时间时，例如从时区的夏令时调整到标准时间这段转换期间，便会出现不明确时间。</span><span class="sxs-lookup"><span data-stu-id="8e95a-105">It occurs when the clock time is adjusted back in time, such as during the transition from a time zone's daylight saving time to its standard time.</span></span> <span data-ttu-id="8e95a-106">在处理不明确时间时，可执行以下任一操作：</span><span class="sxs-lookup"><span data-stu-id="8e95a-106">When handling an ambiguous time, you can do one of the following:</span></span>

- <span data-ttu-id="8e95a-107">如果不明确时间是用户输入的数据项，则可以让用户自行解决。</span><span class="sxs-lookup"><span data-stu-id="8e95a-107">If the ambiguous time is an item of data entered by the user, you can leave it to the user to resolve the ambiguity.</span></span>

- <span data-ttu-id="8e95a-108">假设一下时间如何映射到 UTC。</span><span class="sxs-lookup"><span data-stu-id="8e95a-108">Make an assumption about how the time maps to UTC.</span></span> <span data-ttu-id="8e95a-109">例如，可以假定不明确时间始终以时区的标准时间表示。</span><span class="sxs-lookup"><span data-stu-id="8e95a-109">For example, you can assume that an ambiguous time is always expressed in the time zone's standard time.</span></span>

<span data-ttu-id="8e95a-110">本主题演示如何让用户解决不明确的时间。</span><span class="sxs-lookup"><span data-stu-id="8e95a-110">This topic shows how to let a user resolve an ambiguous time.</span></span>

### <a name="to-let-a-user-resolve-an-ambiguous-time"></a><span data-ttu-id="8e95a-111">让用户解决不明确时间</span><span class="sxs-lookup"><span data-stu-id="8e95a-111">To let a user resolve an ambiguous time</span></span>

1. <span data-ttu-id="8e95a-112">获取用户输入的日期和时间。</span><span class="sxs-lookup"><span data-stu-id="8e95a-112">Get the date and time input by the user.</span></span>

2. <span data-ttu-id="8e95a-113">调用 <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> 方法以确定时间是否不明确。</span><span class="sxs-lookup"><span data-stu-id="8e95a-113">Call the <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> method to determine whether the time is ambiguous.</span></span>

3. <span data-ttu-id="8e95a-114">如果时间不明确，请调用 <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> 方法来检索对象的数组 <xref:System.TimeSpan> 。</span><span class="sxs-lookup"><span data-stu-id="8e95a-114">If the time is ambiguous, call the <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> method to retrieve an array of <xref:System.TimeSpan> objects.</span></span> <span data-ttu-id="8e95a-115">数组中的每个元素都包含一个 UTC 偏移量，不明确时间可以映射到该偏移量。</span><span class="sxs-lookup"><span data-stu-id="8e95a-115">Each element in the array contains a UTC offset that the ambiguous time can map to.</span></span>

4. <span data-ttu-id="8e95a-116">让用户选择所需时差。</span><span class="sxs-lookup"><span data-stu-id="8e95a-116">Let the user select the desired offset.</span></span>

5. <span data-ttu-id="8e95a-117">用本地时间减去用户所选时差，得出 UTC 日期和时间。</span><span class="sxs-lookup"><span data-stu-id="8e95a-117">Get the UTC date and time by subtracting the offset selected by the user from the local time.</span></span>

6. <span data-ttu-id="8e95a-118">调用 `static` `Shared` Visual Basic .net) 方法中的 (<xref:System.DateTime.SpecifyKind%2A> ，将 UTC 日期和时间值的 <xref:System.DateTime.Kind%2A> 属性设置为 <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="8e95a-118">Call the `static` (`Shared` in Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> method to set the UTC date and time value's <xref:System.DateTime.Kind%2A> property to <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="8e95a-119">示例</span><span class="sxs-lookup"><span data-stu-id="8e95a-119">Example</span></span>

<span data-ttu-id="8e95a-120">以下示例将提示用户输入日期和时间，如果时间不明确，会让用户选择不明确时间映射到的 UTC 时间。</span><span class="sxs-lookup"><span data-stu-id="8e95a-120">The following example prompts the user to enter a date and time and, if it is ambiguous, lets the user select the UTC time that the ambiguous time maps to.</span></span>

[!code-csharp[System.TimeZone2.Concepts#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#11)]
[!code-vb[System.TimeZone2.Concepts#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#11)]

<span data-ttu-id="8e95a-121">示例代码的核心使用 <xref:System.TimeSpan> 对象数组来指示不明确时间与 UTC 之间的可能偏移量。</span><span class="sxs-lookup"><span data-stu-id="8e95a-121">The core of the example code uses an array of <xref:System.TimeSpan> objects to indicate possible offsets of the ambiguous time from UTC.</span></span> <span data-ttu-id="8e95a-122">但是，这些时差值对用户可能没有什么意义。</span><span class="sxs-lookup"><span data-stu-id="8e95a-122">However, these offsets are unlikely to be meaningful to the user.</span></span> <span data-ttu-id="8e95a-123">为了阐明时差的含义，该代码还会指示时差是表示本地时区的标准时间还是其夏令时。</span><span class="sxs-lookup"><span data-stu-id="8e95a-123">To clarify the meaning of the offsets, the code also notes whether an offset represents the local time zone's standard time or its daylight saving time.</span></span> <span data-ttu-id="8e95a-124">此代码通过将偏移量与属性的值进行比较来确定哪个时间是标准时间，哪个时间是夏令时 <xref:System.TimeZoneInfo.BaseUtcOffset%2A> 。</span><span class="sxs-lookup"><span data-stu-id="8e95a-124">The code determines which time is standard and which time is daylight by comparing the offset with the value of the <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property.</span></span> <span data-ttu-id="8e95a-125">此属性指示 UTC 与时区的标准时间之差。</span><span class="sxs-lookup"><span data-stu-id="8e95a-125">This property indicates the difference between the UTC and the time zone's standard time.</span></span>

<span data-ttu-id="8e95a-126">在此示例中，对本地时区的所有引用都是通过属性进行的 <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> ; 本地时区从不分配给对象变量。</span><span class="sxs-lookup"><span data-stu-id="8e95a-126">In this example, all references to the local time zone are made through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property; the local time zone is never assigned to an object variable.</span></span> <span data-ttu-id="8e95a-127">这是建议的做法，因为对方法的调用会 <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> 使本地时区分配到的任何对象无效。</span><span class="sxs-lookup"><span data-stu-id="8e95a-127">This is a recommended practice because a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method invalidates any objects that the local time zone is assigned to.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="8e95a-128">编译代码</span><span class="sxs-lookup"><span data-stu-id="8e95a-128">Compiling the code</span></span>

<span data-ttu-id="8e95a-129">此示例需要：</span><span class="sxs-lookup"><span data-stu-id="8e95a-129">This example requires:</span></span>

- <span data-ttu-id="8e95a-130"><xref:System>要导入的命名空间与 `using` c # 代码) 中 (必需的语句一起导入。</span><span class="sxs-lookup"><span data-stu-id="8e95a-130">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="8e95a-131">请参阅</span><span class="sxs-lookup"><span data-stu-id="8e95a-131">See also</span></span>

- [<span data-ttu-id="8e95a-132">日期、时间和时区</span><span class="sxs-lookup"><span data-stu-id="8e95a-132">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="8e95a-133">如何：解决不明确的时间</span><span class="sxs-lookup"><span data-stu-id="8e95a-133">How to: Resolve ambiguous times</span></span>](resolve-ambiguous-times.md)
