---
description: 了解详细信息：如何：枚举计算机上存在的时区
title: 如何：枚举计算机上的时区
ms.date: 04/10/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET], enumerating
- enumerating time zones [.NET]
ms.assetid: bb7a42ab-6bd9-4c5c-b734-5546d51f8669
ms.openlocfilehash: 98227d61ed81828f9c0614f622fed9a9667c6f4e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702673"
---
# <a name="how-to-enumerate-time-zones-present-on-a-computer"></a><span data-ttu-id="c65dc-103">如何：枚举计算机上的时区</span><span class="sxs-lookup"><span data-stu-id="c65dc-103">How to: Enumerate time zones present on a computer</span></span>

<span data-ttu-id="c65dc-104">若要成功使用指定的时区，需要该时区的相关信息可供系统使用。</span><span class="sxs-lookup"><span data-stu-id="c65dc-104">Successfully working with a designated time zone requires that information about that time zone be available to the system.</span></span> <span data-ttu-id="c65dc-105">Windows XP 和 Windows Vista 操作系统将此信息存储在注册表中。</span><span class="sxs-lookup"><span data-stu-id="c65dc-105">The Windows XP and Windows Vista operating systems store this information in the registry.</span></span> <span data-ttu-id="c65dc-106">但是，尽管世界上存在的时区总数非常大，但注册表包含的信息只是其中的一个子集。</span><span class="sxs-lookup"><span data-stu-id="c65dc-106">However, although the total number of time zones that exist throughout the world is large, the registry contains information about only a subset of them.</span></span> <span data-ttu-id="c65dc-107">此外，注册表本身是一个动态结构，其内容可能发生有意或无意的更改。</span><span class="sxs-lookup"><span data-stu-id="c65dc-107">In addition, the registry itself is a dynamic structure whose contents are subject to both deliberate and accidental change.</span></span> <span data-ttu-id="c65dc-108">因此，应用程序无法保证系统上始终存在已定义且可用的特定时区。</span><span class="sxs-lookup"><span data-stu-id="c65dc-108">As a result, an application cannot always assume that a particular time zone is defined and available on a system.</span></span> <span data-ttu-id="c65dc-109">对于使用时区信息应用程序的许多应用程序来说，第一步是确定所需时区在本地系统上是否可用，或者向用户提供可供选择的时区列表。</span><span class="sxs-lookup"><span data-stu-id="c65dc-109">The first step for many applications that use time zone information applications is to determine whether required time zones are available on the local system, or to give the user a list of time zones from which to select.</span></span> <span data-ttu-id="c65dc-110">这要求应用程序枚举本地系统上定义的时区。</span><span class="sxs-lookup"><span data-stu-id="c65dc-110">This requires that an application enumerate the time zones defined on a local system.</span></span>

> [!NOTE]
> <span data-ttu-id="c65dc-111">如果应用程序依赖于可能未在本地系统上定义的特定时区，则该应用程序可以通过序列化和反序列化有关时区的信息来确保其存在。</span><span class="sxs-lookup"><span data-stu-id="c65dc-111">If an application relies on the presence of a particular time zone that may not be defined on a local system, the application can ensure its presence by serializing and deserializing information about the time zone.</span></span> <span data-ttu-id="c65dc-112">然后，可以将时区添加到列表控件，使应用程序用户可以选择它。</span><span class="sxs-lookup"><span data-stu-id="c65dc-112">The time zone can then be added to a list control so that the application user can select it.</span></span> <span data-ttu-id="c65dc-113">有关详细信息，请参阅 [如何：将时区保存到嵌入的资源](save-time-zones-to-an-embedded-resource.md) 和 [如何：从嵌入的资源还原时区](restore-time-zones-from-an-embedded-resource.md)。</span><span class="sxs-lookup"><span data-stu-id="c65dc-113">For details, see [How to: Save Time Zones to an Embedded Resource](save-time-zones-to-an-embedded-resource.md) and [How to: Restore time zones from an embedded resource](restore-time-zones-from-an-embedded-resource.md).</span></span>

### <a name="to-enumerate-the-time-zones-present-on-the-local-system"></a><span data-ttu-id="c65dc-114">枚举本地系统上存在的时区</span><span class="sxs-lookup"><span data-stu-id="c65dc-114">To enumerate the time zones present on the local system</span></span>

1. <span data-ttu-id="c65dc-115">调用 <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="c65dc-115">Call the <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="c65dc-116">方法返回对象的泛型 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> 集合 <xref:System.TimeZoneInfo> 。</span><span class="sxs-lookup"><span data-stu-id="c65dc-116">The method returns a generic <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> collection of <xref:System.TimeZoneInfo> objects.</span></span> <span data-ttu-id="c65dc-117">集合中的项按其属性进行排序 <xref:System.TimeZoneInfo.DisplayName%2A> 。</span><span class="sxs-lookup"><span data-stu-id="c65dc-117">The entries in the collection are sorted by their <xref:System.TimeZoneInfo.DisplayName%2A> property.</span></span> <span data-ttu-id="c65dc-118">例如：</span><span class="sxs-lookup"><span data-stu-id="c65dc-118">For example:</span></span>

   [!code-csharp[System.TimeZone2.Concepts#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#1)]
   [!code-vb[System.TimeZone2.Concepts#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#1)]

2. <span data-ttu-id="c65dc-119"><xref:System.TimeZoneInfo>使用 c # 中的循环 (枚举集合中的各个对象 `foreach` ) 或 `For Each` .。。`Next`</span><span class="sxs-lookup"><span data-stu-id="c65dc-119">Enumerate the individual <xref:System.TimeZoneInfo> objects in the collection by using a `foreach` loop (in C#) or a `For Each`…`Next`</span></span> <span data-ttu-id="c65dc-120">循环 (Visual Basic) ，并对每个对象执行任何必要的处理。</span><span class="sxs-lookup"><span data-stu-id="c65dc-120">loop (in Visual Basic), and perform any necessary processing on each object.</span></span> <span data-ttu-id="c65dc-121">例如，以下代码枚举 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> <xref:System.TimeZoneInfo> 步骤1中返回的对象的集合，并在控制台上列出每个时区的显示名称。</span><span class="sxs-lookup"><span data-stu-id="c65dc-121">For example, the following code enumerates the <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> collection of <xref:System.TimeZoneInfo> objects returned in step 1 and lists the display name of each time zone on the console.</span></span>

   [!code-csharp[System.TimeZone2.Concepts#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#12)]
   [!code-vb[System.TimeZone2.Concepts#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#12)]

### <a name="to-present-the-user-with-a-list-of-time-zones-present-on-the-local-system"></a><span data-ttu-id="c65dc-122">向用户提供本地系统上存在的时区列表</span><span class="sxs-lookup"><span data-stu-id="c65dc-122">To present the user with a list of time zones present on the local system</span></span>

1. <span data-ttu-id="c65dc-123">调用 <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="c65dc-123">Call the <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="c65dc-124">方法返回对象的泛型 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> 集合 <xref:System.TimeZoneInfo> 。</span><span class="sxs-lookup"><span data-stu-id="c65dc-124">The method returns a generic <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> collection of <xref:System.TimeZoneInfo> objects.</span></span>

2. <span data-ttu-id="c65dc-125">将步骤1中返回的集合分配给 `DataSource` Windows 窗体或 ASP.NET 列表控件的属性。</span><span class="sxs-lookup"><span data-stu-id="c65dc-125">Assign the collection returned in step 1 to the `DataSource` property of a Windows forms or ASP.NET list control.</span></span>

3. <span data-ttu-id="c65dc-126">检索 <xref:System.TimeZoneInfo> 用户已选择的对象。</span><span class="sxs-lookup"><span data-stu-id="c65dc-126">Retrieve the <xref:System.TimeZoneInfo> object that the user has selected.</span></span>

<span data-ttu-id="c65dc-127">该示例为 Windows 应用程序提供了一个图例。</span><span class="sxs-lookup"><span data-stu-id="c65dc-127">The example provides an illustration for a Windows application.</span></span>

## <a name="example"></a><span data-ttu-id="c65dc-128">示例</span><span class="sxs-lookup"><span data-stu-id="c65dc-128">Example</span></span>

<span data-ttu-id="c65dc-129">该示例启动一个 Windows 应用程序，该应用程序在列表框中显示在系统上定义的时区。</span><span class="sxs-lookup"><span data-stu-id="c65dc-129">The example starts a Windows application that displays the time zones defined on a system in a list box.</span></span> <span data-ttu-id="c65dc-130">然后，该示例显示一个对话框，其中包含 <xref:System.TimeZoneInfo.DisplayName%2A> 用户选定的时区对象的属性值。</span><span class="sxs-lookup"><span data-stu-id="c65dc-130">The example then displays a dialog box that contains the value of the <xref:System.TimeZoneInfo.DisplayName%2A> property of the time zone object selected by the user.</span></span>

[!code-csharp[System.TimeZone2.Concepts#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#2)]
[!code-vb[System.TimeZone2.Concepts#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#2)]

<span data-ttu-id="c65dc-131">大多数列表控件 (如 <xref:System.Windows.Forms.ListBox?displayProperty=nameWithType> 或 <xref:System.Web.UI.WebControls.BulletedList?displayProperty=nameWithType> 控件) 使你可以将对象变量的集合分配给其属性，只要 `DataSource` 该集合实现了 <xref:System.Collections.IEnumerable> 接口。</span><span class="sxs-lookup"><span data-stu-id="c65dc-131">Most list controls (such as the <xref:System.Windows.Forms.ListBox?displayProperty=nameWithType> or <xref:System.Web.UI.WebControls.BulletedList?displayProperty=nameWithType> control) allow you to assign a collection of object variables to their `DataSource` property as long as that collection implements the <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="c65dc-132"> (泛型 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> 类执行此方法。 ) 若要显示集合中的单个对象，控件将调用该对象的 `ToString` 方法来提取用于表示对象的字符串。</span><span class="sxs-lookup"><span data-stu-id="c65dc-132">(The generic <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> class does this.) To display an individual object in the collection, the control calls that object's `ToString` method to extract the string that is used to represent the object.</span></span> <span data-ttu-id="c65dc-133">对于 <xref:System.TimeZoneInfo> 对象， `ToString` 方法返回 <xref:System.TimeZoneInfo> 对象的显示名称 (其 <xref:System.TimeZoneInfo.DisplayName%2A> 属性) 的值。</span><span class="sxs-lookup"><span data-stu-id="c65dc-133">In the case of <xref:System.TimeZoneInfo> objects, the `ToString` method returns the <xref:System.TimeZoneInfo> object's display name (the value of its <xref:System.TimeZoneInfo.DisplayName%2A> property).</span></span>

> [!NOTE]
> <span data-ttu-id="c65dc-134">由于列表控件调用对象的 `ToString` 方法，因此你可以将对象的集合分配 <xref:System.TimeZoneInfo> 给控件，使控件为每个对象显示有意义的名称，并检索 <xref:System.TimeZoneInfo> 用户已选择的对象。</span><span class="sxs-lookup"><span data-stu-id="c65dc-134">Because list controls call an object's `ToString` method, you can assign a collection of <xref:System.TimeZoneInfo> objects to the control, have the control display a meaningful name for each object, and retrieve the <xref:System.TimeZoneInfo> object that the user has selected.</span></span> <span data-ttu-id="c65dc-135">这样就无需为集合中的每个对象提取字符串，而是将字符串分配给一个集合，该集合将变为分配给该控件的 `DataSource` 属性，检索该用户选定的字符串，然后使用此字符串提取它所描述的对象。</span><span class="sxs-lookup"><span data-stu-id="c65dc-135">This eliminates the need to extract a string for each object in the collection, assign the string to a collection that is in turn assigned to the control's `DataSource` property, retrieve the string the user has selected, and then use this string to extract the object that it describes.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="c65dc-136">编译代码</span><span class="sxs-lookup"><span data-stu-id="c65dc-136">Compiling the code</span></span>

<span data-ttu-id="c65dc-137">此示例需要：</span><span class="sxs-lookup"><span data-stu-id="c65dc-137">This example requires:</span></span>

- <span data-ttu-id="c65dc-138">导入以下命名空间：</span><span class="sxs-lookup"><span data-stu-id="c65dc-138">That the following namespaces be imported:</span></span>

  <span data-ttu-id="c65dc-139"><xref:System> C # 代码中的 () </span><span class="sxs-lookup"><span data-stu-id="c65dc-139"><xref:System> (in C# code)</span></span>

  <xref:System.Collections.ObjectModel>

## <a name="see-also"></a><span data-ttu-id="c65dc-140">请参阅</span><span class="sxs-lookup"><span data-stu-id="c65dc-140">See also</span></span>

- [<span data-ttu-id="c65dc-141">日期、时间和时区</span><span class="sxs-lookup"><span data-stu-id="c65dc-141">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="c65dc-142">如何：将时区保存到嵌入的资源</span><span class="sxs-lookup"><span data-stu-id="c65dc-142">How to: Save time zones to an embedded resource</span></span>](save-time-zones-to-an-embedded-resource.md)
- [<span data-ttu-id="c65dc-143">如何：从嵌入的资源还原时区</span><span class="sxs-lookup"><span data-stu-id="c65dc-143">How to: Restore time zones from an embedded resource</span></span>](restore-time-zones-from-an-embedded-resource.md)
