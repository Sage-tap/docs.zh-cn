---
description: 了解详细信息：处理 DataAdapter 事件
title: 处理 DataAdapter 事件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 11515b25-ee49-4b1d-9294-a142147c1ec5
ms.openlocfilehash: 045a48ae545ad4354844dd451ff58618b760a9a8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723941"
---
# <a name="handling-dataadapter-events"></a><span data-ttu-id="830c0-103">处理 DataAdapter 事件</span><span class="sxs-lookup"><span data-stu-id="830c0-103">Handling DataAdapter Events</span></span>

<span data-ttu-id="830c0-104">ADO.NET <xref:System.Data.Common.DataAdapter> 公开三个可用于响应数据源中数据更改的事件。</span><span class="sxs-lookup"><span data-stu-id="830c0-104">The ADO.NET <xref:System.Data.Common.DataAdapter> exposes three events that you can use to respond to changes made to data at the data source.</span></span> <span data-ttu-id="830c0-105">下表演示了 `DataAdapter` 事件。</span><span class="sxs-lookup"><span data-stu-id="830c0-105">The following table shows the `DataAdapter` events.</span></span>  
  
|<span data-ttu-id="830c0-106">事件</span><span class="sxs-lookup"><span data-stu-id="830c0-106">Event</span></span>|<span data-ttu-id="830c0-107">描述</span><span class="sxs-lookup"><span data-stu-id="830c0-107">Description</span></span>|  
|-----------|-----------------|  
|`RowUpdating`|<span data-ttu-id="830c0-108">将要开始对某行执行 UPDATE、INSERT 或 DELETE 操作（通过调用 `Update` 方法之一）。</span><span class="sxs-lookup"><span data-stu-id="830c0-108">An UPDATE, INSERT, or DELETE operation on a row (by a call to one of the `Update` methods) is about to begin.</span></span>|  
|`RowUpdated`|<span data-ttu-id="830c0-109">对某行的 UPDATE、INSERT 或 DELETE 操作（通过调用 `Update` 方法之一）已完成。</span><span class="sxs-lookup"><span data-stu-id="830c0-109">An UPDATE, INSERT, or DELETE operation on a row (by a call to one of the `Update` methods) is complete.</span></span>|  
|`FillError`|<span data-ttu-id="830c0-110">执行 `Fill` 操作期间出错。</span><span class="sxs-lookup"><span data-stu-id="830c0-110">An error has occurred during a `Fill` operation.</span></span>|  
  
## <a name="rowupdating-and-rowupdated"></a><span data-ttu-id="830c0-111">RowUpdating 和 RowUpdated</span><span class="sxs-lookup"><span data-stu-id="830c0-111">RowUpdating and RowUpdated</span></span>  

 <span data-ttu-id="830c0-112">在数据源中处理对  `RowUpdating` 中某行的任何更新之前，将引发 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="830c0-112">`RowUpdating` is raised before any update to a row from the <xref:System.Data.DataSet> has been processed at the data source.</span></span> <span data-ttu-id="830c0-113">在数据源中处理对 `RowUpdated` 中某行的任何更新之后，将引发 `DataSet`。</span><span class="sxs-lookup"><span data-stu-id="830c0-113">`RowUpdated` is raised after any update to a row from the `DataSet` has been processed at the data source.</span></span> <span data-ttu-id="830c0-114">因此，可以使用 `RowUpdating` 执行下列操作：在更新行为发生之前对其进行修改，在更新将发生时提供附加处理，保留对已更新行的引用，取消当前更新并将其安排在以后进行批处理，等等。</span><span class="sxs-lookup"><span data-stu-id="830c0-114">As a result, you can use `RowUpdating` to modify update behavior before it happens, to provide additional handling when an update will occur, to retain a reference to an updated row, to cancel the current update and schedule it for a batch process to be processed later, and so on.</span></span> <span data-ttu-id="830c0-115">`RowUpdated` 对于响应更新期间发生的错误和异常是非常有用的。</span><span class="sxs-lookup"><span data-stu-id="830c0-115">`RowUpdated` is useful for responding to errors and exceptions that occur during the update.</span></span> <span data-ttu-id="830c0-116">您可以向 `DataSet` 以及重试逻辑等添加错误信息。</span><span class="sxs-lookup"><span data-stu-id="830c0-116">You can add error information to the `DataSet`, as well as retry logic, and so on.</span></span>  
  
 <span data-ttu-id="830c0-117">传递给 <xref:System.Data.Common.RowUpdatingEventArgs> 和 <xref:System.Data.Common.RowUpdatedEventArgs> 事件的 `RowUpdating` 和 `RowUpdated` 自变量包括：`Command` 属性，它引用用来执行更新的 `Command` 对象；`Row` 属性，它引用包含更新信息的 `DataRow` 对象；`StatementType` 属性，它指示所执行的更新类型；`TableMapping`（如果适用）；以及操作的 `Status`。</span><span class="sxs-lookup"><span data-stu-id="830c0-117">The <xref:System.Data.Common.RowUpdatingEventArgs> and <xref:System.Data.Common.RowUpdatedEventArgs> arguments passed to the `RowUpdating` and `RowUpdated` events include the following: a `Command` property that references the `Command` object being used to perform the update; a `Row` property that references the `DataRow` object containing the updated information; a `StatementType` property for what type of update is being performed; the `TableMapping`, if applicable; and the `Status` of the operation.</span></span>  
  
 <span data-ttu-id="830c0-118">可以使用 `Status` 属性来确定在执行该操作期间是否发生了错误；如果需要，还可以使用该属性来控制对当前行和结果行所执行的操作。</span><span class="sxs-lookup"><span data-stu-id="830c0-118">You can use the `Status` property to determine if an error has occurred during the operation and, if desired, to control the actions against the current and resulting rows.</span></span> <span data-ttu-id="830c0-119">当该事件发生时，`Status` 属性将为 `Continue` 或 `ErrorsOccurred`。</span><span class="sxs-lookup"><span data-stu-id="830c0-119">When the event occurs, the `Status` property equals either `Continue` or `ErrorsOccurred`.</span></span> <span data-ttu-id="830c0-120">下表演示为了控制更新过程中的后继操作，可以将 `Status` 属性设置为的值。</span><span class="sxs-lookup"><span data-stu-id="830c0-120">The following table shows the values to which you can set the `Status` property in order to control later actions during the update.</span></span>  
  
|<span data-ttu-id="830c0-121">状态</span><span class="sxs-lookup"><span data-stu-id="830c0-121">Status</span></span>|<span data-ttu-id="830c0-122">描述</span><span class="sxs-lookup"><span data-stu-id="830c0-122">Description</span></span>|  
|------------|-----------------|  
|`Continue`|<span data-ttu-id="830c0-123">继续执行更新操作。</span><span class="sxs-lookup"><span data-stu-id="830c0-123">Continue the update operation.</span></span>|  
|`ErrorsOccurred`|<span data-ttu-id="830c0-124">中止更新操作并引发异常。</span><span class="sxs-lookup"><span data-stu-id="830c0-124">Abort the update operation and throw an exception.</span></span>|  
|`SkipCurrentRow`|<span data-ttu-id="830c0-125">忽略当前行并继续执行更新操作。</span><span class="sxs-lookup"><span data-stu-id="830c0-125">Ignore the current row and continue the update operation.</span></span>|  
|`SkipAllRemainingRows`|<span data-ttu-id="830c0-126">中止更新操作但不引发异常。</span><span class="sxs-lookup"><span data-stu-id="830c0-126">Abort the update operation but do not throw an exception.</span></span>|  
  
 <span data-ttu-id="830c0-127">如果将 `Status` 属性设置为 `ErrorsOccurred`，则会引发异常。</span><span class="sxs-lookup"><span data-stu-id="830c0-127">Setting the `Status` property to `ErrorsOccurred` causes an exception to be thrown.</span></span> <span data-ttu-id="830c0-128">您可以通过将 `Errors` 属性设置为所需异常来控制所引发的异常。</span><span class="sxs-lookup"><span data-stu-id="830c0-128">You can control which exception is thrown by setting the `Errors` property to the desired exception.</span></span> <span data-ttu-id="830c0-129">如果使用 `Status` 的其他值之一，则可防止引发异常。</span><span class="sxs-lookup"><span data-stu-id="830c0-129">Using one of the other values for `Status` prevents an exception from being thrown.</span></span>  
  
 <span data-ttu-id="830c0-130">也可以使用 `ContinueUpdateOnError` 属性为更新的行处理错误。</span><span class="sxs-lookup"><span data-stu-id="830c0-130">You can also use the `ContinueUpdateOnError` property to handle errors for updated rows.</span></span> <span data-ttu-id="830c0-131">如果 `DataAdapter.ContinueUpdateOnError` 为 `true`，那么当行的更新导致引发异常时，该异常的文本被放入特定行的 `RowError` 信息中，并且处理将会继续而不会引发异常。</span><span class="sxs-lookup"><span data-stu-id="830c0-131">If `DataAdapter.ContinueUpdateOnError` is `true`, when an update to a row results in an exception being thrown, the text of the exception is placed into the `RowError` information of the particular row, and processing continues without throwing an exception.</span></span> <span data-ttu-id="830c0-132">这使您能够在 `Update` 完成时对错误作出响应；与此相反的是 `RowUpdated` 事件，它使您能够在遇到错误时响应错误。</span><span class="sxs-lookup"><span data-stu-id="830c0-132">This enables you to respond to errors when the `Update` is complete, in contrast to the `RowUpdated` event, which enables you to respond to errors when the error is encountered.</span></span>  
  
 <span data-ttu-id="830c0-133">以下代码示例显示如何添加和移除事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="830c0-133">The following code sample shows how to both add and remove event handlers.</span></span> <span data-ttu-id="830c0-134">`RowUpdating` 事件处理程序编写带有时间戳的所有已删除记录的日志。</span><span class="sxs-lookup"><span data-stu-id="830c0-134">The `RowUpdating` event handler writes a log of all deleted records with a time stamp.</span></span> <span data-ttu-id="830c0-135">`RowUpdated` 事件处理程序将错误信息添加到 `DataSet` 中行的 `RowError` 属性、取消显示异常，并继续处理（镜像 `ContinueUpdateOnError` = `true` 的行为）。</span><span class="sxs-lookup"><span data-stu-id="830c0-135">The `RowUpdated` event handler adds error information to the `RowError` property of the row in the `DataSet`, suppresses the exception, and continues processing (mirroring the behavior of `ContinueUpdateOnError` = `true`).</span></span>  
  
```vb  
' Assumes that connection is a valid SqlConnection object.  
Dim custAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers", connection)  
  
' Add handlers.  
AddHandler custAdapter.RowUpdating, New SqlRowUpdatingEventHandler( _  
  AddressOf OnRowUpdating)  
AddHandler custAdapter.RowUpdated, New SqlRowUpdatedEventHandler(  
  AddressOf OnRowUpdated)  
  
' Set DataAdapter command properties, fill DataSet, and modify DataSet.  
  
custAdapter.Update(custDS, "Customers")  
  
' Remove handlers.  
RemoveHandler custAdapter.RowUpdating, _  
  New SqlRowUpdatingEventHandler(AddressOf OnRowUpdating)  
RemoveHandler custAdapter.RowUpdated, _  
  New SqlRowUpdatedEventHandler(AddressOf OnRowUpdated)  
  
Private Shared Sub OnRowUpdating(sender As Object, _  
  args As SqlRowUpdatingEventArgs)  
  If args.StatementType = StatementType.Delete Then  
    Dim tw As System.IO.TextWriter = _  
  System.IO.File.AppendText("Deletes.log")  
    tw.WriteLine( _  
      "{0}: Customer {1} Deleted.", DateTime.Now, args.Row(_  
      "CustomerID", DataRowVersion.Original))  
    tw.Close()  
  End If  
End Sub  
  
Private Shared Sub OnRowUpdated( _  
  sender As Object, args As SqlRowUpdatedEventArgs)  
  If args.Status = UpdateStatus.ErrorsOccurred  
    args.Status = UpdateStatus.SkipCurrentRow  
    args.Row.RowError = args.Errors.Message  
  End If  
End Sub  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection object.  
SqlDataAdapter custAdapter = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers", connection);  
  
// Add handlers.  
custAdapter.RowUpdating += new SqlRowUpdatingEventHandler(OnRowUpdating);  
custAdapter.RowUpdated += new SqlRowUpdatedEventHandler(OnRowUpdated);  
  
// Set DataAdapter command properties, fill DataSet, modify DataSet.  
  
custAdapter.Update(custDS, "Customers");  
  
// Remove handlers.  
custAdapter.RowUpdating -= new SqlRowUpdatingEventHandler(OnRowUpdating);  
custAdapter.RowUpdated -= new SqlRowUpdatedEventHandler(OnRowUpdated);  
  
protected static void OnRowUpdating(  
  object sender, SqlRowUpdatingEventArgs args)  
{  
  if (args.StatementType == StatementType.Delete)  
  {  
    System.IO.TextWriter tw = System.IO.File.AppendText("Deletes.log");  
    tw.WriteLine(  
      "{0}: Customer {1} Deleted.", DateTime.Now,
       args.Row["CustomerID", DataRowVersion.Original]);  
    tw.Close();  
  }  
}  
  
protected static void OnRowUpdated(  
  object sender, SqlRowUpdatedEventArgs args)  
{  
  if (args.Status == UpdateStatus.ErrorsOccurred)  
  {  
    args.Row.RowError = args.Errors.Message;  
    args.Status = UpdateStatus.SkipCurrentRow;  
  }  
}  
```  
  
## <a name="fillerror"></a><span data-ttu-id="830c0-136">FillError</span><span class="sxs-lookup"><span data-stu-id="830c0-136">FillError</span></span>  

 <span data-ttu-id="830c0-137">如果在执行 `DataAdapter` 操作期间出错，`FillError` 将发出 `Fill` 事件。</span><span class="sxs-lookup"><span data-stu-id="830c0-137">The `DataAdapter` issues the `FillError` event when an error occurs during a `Fill` operation.</span></span> <span data-ttu-id="830c0-138">当所添加行中的数据必须损失一些精度才能转换成 .NET Framework 类型时，通常会发生这种类型的错误。</span><span class="sxs-lookup"><span data-stu-id="830c0-138">This type of error commonly occurs when the data in the row being added could not be converted to a .NET Framework type without some loss of precision.</span></span>  
  
 <span data-ttu-id="830c0-139">如果在执行 `Fill` 操作期间出错，则当前行将不会被添加到 `DataTable`。</span><span class="sxs-lookup"><span data-stu-id="830c0-139">If an error occurs during a `Fill` operation, the current row is not added to the `DataTable`.</span></span> <span data-ttu-id="830c0-140">通过 `FillError` 事件可更正该错误并添加当前行，或者忽略已排除的行并继续执行 `Fill` 操作。</span><span class="sxs-lookup"><span data-stu-id="830c0-140">The `FillError` event enables you to resolve the error and add the row, or to ignore the excluded row and continue the `Fill` operation.</span></span>  
  
 <span data-ttu-id="830c0-141">传递给 `FillErrorEventArgs` 事件的 `FillError` 包含几项可用于响应和更正错误的属性。</span><span class="sxs-lookup"><span data-stu-id="830c0-141">The `FillErrorEventArgs` passed to the `FillError` event can contain several properties that enable you to respond to and resolve errors.</span></span> <span data-ttu-id="830c0-142">下表演示 `FillErrorEventArgs` 对象的属性。</span><span class="sxs-lookup"><span data-stu-id="830c0-142">The following table shows the properties of the `FillErrorEventArgs` object.</span></span>  
  
|<span data-ttu-id="830c0-143">属性</span><span class="sxs-lookup"><span data-stu-id="830c0-143">Property</span></span>|<span data-ttu-id="830c0-144">描述</span><span class="sxs-lookup"><span data-stu-id="830c0-144">Description</span></span>|  
|--------------|-----------------|  
|`Errors`|<span data-ttu-id="830c0-145">已发生的 `Exception`。</span><span class="sxs-lookup"><span data-stu-id="830c0-145">The `Exception` that occurred.</span></span>|  
|`DataTable`|<span data-ttu-id="830c0-146">出错时所填充的 `DataTable` 对象。</span><span class="sxs-lookup"><span data-stu-id="830c0-146">The `DataTable` object being filled when the error occurred.</span></span>|  
|`Values`|<span data-ttu-id="830c0-147">一个对象数组，它包含出错时所添加的行的值。</span><span class="sxs-lookup"><span data-stu-id="830c0-147">An array of objects that contains the values of the row being added when the error occurred.</span></span> <span data-ttu-id="830c0-148">`Values` 数组的序号引用与所添加的行的列的序号引用相对应。</span><span class="sxs-lookup"><span data-stu-id="830c0-148">The ordinal references of the `Values` array correspond to the ordinal references of the columns of the row being added.</span></span> <span data-ttu-id="830c0-149">例如，`Values[0]` 是作为当前行的第一列添加的值。</span><span class="sxs-lookup"><span data-stu-id="830c0-149">For example, `Values[0]` is the value that was being added as the first column of the row.</span></span>|  
|`Continue`|<span data-ttu-id="830c0-150">用于选择是否引发异常。</span><span class="sxs-lookup"><span data-stu-id="830c0-150">Allows you to choose whether or not to throw an exception.</span></span> <span data-ttu-id="830c0-151">如果将 `Continue` 属性设置为 `false`，则会暂停当前 `Fill` 操作并将会引发异常。</span><span class="sxs-lookup"><span data-stu-id="830c0-151">Setting the `Continue` property to `false` will halt the current `Fill` operation, and an exception will be thrown.</span></span> <span data-ttu-id="830c0-152">如果将 `Continue` 设置为 `true`，那么即使出错，仍将继续执行 `Fill` 操作。</span><span class="sxs-lookup"><span data-stu-id="830c0-152">Setting `Continue` to `true` continues the `Fill` operation despite the error.</span></span>|  
  
 <span data-ttu-id="830c0-153">下面的代码示例为 `FillError` 的 `DataAdapter` 事件添加一个事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="830c0-153">The following code example adds an event handler for the `FillError` event of the `DataAdapter`.</span></span> <span data-ttu-id="830c0-154">在 `FillError` 事件代码中，该示例可确定是否可能出现精度缺失，并可用于响应该异常。</span><span class="sxs-lookup"><span data-stu-id="830c0-154">In the `FillError` event code, the example determines if there is the potential for precision loss, providing the opportunity to respond to the exception.</span></span>  
  
```vb  
AddHandler adapter.FillError, New FillErrorEventHandler( _  
  AddressOf FillError)  
  
Dim dataSet As DataSet = New DataSet  
adapter.Fill(dataSet, "ThisTable")  
  
Private Shared Sub FillError(sender As Object, _  
  args As FillErrorEventArgs)  
  If args.Errors.GetType() Is Type.GetType("System.OverflowException") Then  
    ' Code to handle precision loss.  
    ' Add a row to table using the values from the first two columns.  
    DataRow myRow = args.DataTable.Rows.Add(New Object() _  
      {args.Values(0), args.Values(1), DBNull.Value})  
    ' Set the RowError containing the value for the third column.  
    myRow.RowError = _  
      "OverflowException encountered. Value from data source: " & _  
      args.Values(2)  
    args.Continue = True  
  End If  
End Sub  
```  
  
```csharp  
adapter.FillError += new FillErrorEventHandler(FillError);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, "ThisTable");  
  
protected static void FillError(object sender, FillErrorEventArgs args)  
{  
  if (args.Errors.GetType() == typeof(System.OverflowException))  
  {  
    // Code to handle precision loss.  
    //Add a row to table using the values from the first two columns.  
    DataRow myRow = args.DataTable.Rows.Add(new object[]  
       {args.Values[0], args.Values[1], DBNull.Value});  
    //Set the RowError containing the value for the third column.  
    myRow.RowError =
       "OverflowException Encountered. Value from data source: " +  
       args.Values[2];  
    args.Continue = true;  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="830c0-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="830c0-155">See also</span></span>

- [<span data-ttu-id="830c0-156">DataAdapter 和 DataReader</span><span class="sxs-lookup"><span data-stu-id="830c0-156">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="830c0-157">处理数据集事件</span><span class="sxs-lookup"><span data-stu-id="830c0-157">Handling DataSet Events</span></span>](./dataset-datatable-dataview/handling-dataset-events.md)
- [<span data-ttu-id="830c0-158">处理数据表事件</span><span class="sxs-lookup"><span data-stu-id="830c0-158">Handling DataTable Events</span></span>](./dataset-datatable-dataview/handling-datatable-events.md)
- [<span data-ttu-id="830c0-159">事件</span><span class="sxs-lookup"><span data-stu-id="830c0-159">Events</span></span>](../../../standard/events/index.md)
- [<span data-ttu-id="830c0-160">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="830c0-160">ADO.NET Overview</span></span>](ado-net-overview.md)
