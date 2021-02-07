---
description: 了解详细信息：乐观并发
title: 开放式并发
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e380edac-da67-4276-80a5-b64decae4947
ms.openlocfilehash: 1034720b2c57b863b87eef440424a7e2f4c2c6c9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739139"
---
# <a name="optimistic-concurrency"></a><span data-ttu-id="1adf7-103">开放式并发</span><span class="sxs-lookup"><span data-stu-id="1adf7-103">Optimistic Concurrency</span></span>

<span data-ttu-id="1adf7-104">在多用户环境中，有两种用于更新数据库中数据的模型：开放式并发和保守式并发。</span><span class="sxs-lookup"><span data-stu-id="1adf7-104">In a multiuser environment, there are two models for updating data in a database: optimistic concurrency and pessimistic concurrency.</span></span> <span data-ttu-id="1adf7-105">设计 <xref:System.Data.DataSet> 对象的目的是为了促进将开放式并发用于长时间运行的活动，例如对数据进行远程处理以及与数据进行交互时。</span><span class="sxs-lookup"><span data-stu-id="1adf7-105">The <xref:System.Data.DataSet> object is designed to encourage the use of optimistic concurrency for long-running activities, such as remoting data and interacting with data.</span></span>  
  
 <span data-ttu-id="1adf7-106">保守式并发涉及到锁定数据源中的行，以防止其他用户因修改数据而影响当前用户。</span><span class="sxs-lookup"><span data-stu-id="1adf7-106">Pessimistic concurrency involves locking rows at the data source to prevent other users from modifying data in a way that affects the current user.</span></span> <span data-ttu-id="1adf7-107">在保守式模型中，当用户执行会应用锁的操作时，其他用户将无法执行可能与锁发生冲突的操作，直到锁所有者释放锁为止。</span><span class="sxs-lookup"><span data-stu-id="1adf7-107">In a pessimistic model, when a user performs an action that causes a lock to be applied, other users cannot perform actions that would conflict with the lock until the lock owner releases it.</span></span> <span data-ttu-id="1adf7-108">此模型主要用于以下环境：对数据存在激烈争用，使得用锁保护数据的成本少于在发生并发冲突时回滚事务的成本。</span><span class="sxs-lookup"><span data-stu-id="1adf7-108">This model is primarily used in environments where there is heavy contention for data, so that the cost of protecting data with locks is less than the cost of rolling back transactions if concurrency conflicts occur.</span></span>  
  
 <span data-ttu-id="1adf7-109">因此，在保守式并发模型中，更新行的用户将会建立锁。</span><span class="sxs-lookup"><span data-stu-id="1adf7-109">Therefore, in a pessimistic concurrency model, a user who updates a row establishes a lock.</span></span> <span data-ttu-id="1adf7-110">在该用户完成更新并释放锁之前，其他任何用户都无法更改锁定行。</span><span class="sxs-lookup"><span data-stu-id="1adf7-110">Until the user has finished the update and released the lock, no one else can change that row.</span></span> <span data-ttu-id="1adf7-111">因此，如果锁定时间将会比较短（例如在以编程方式处理记录时），最好实现保守式并发。</span><span class="sxs-lookup"><span data-stu-id="1adf7-111">For this reason, pessimistic concurrency is best implemented when lock times will be short, as in programmatic processing of records.</span></span> <span data-ttu-id="1adf7-112">如果用户与数据进行交互，会使记录锁定相对长的时间，保守式并发并不是可伸缩的选项。</span><span class="sxs-lookup"><span data-stu-id="1adf7-112">Pessimistic concurrency is not a scalable option when users are interacting with data and causing records to be locked for relatively large periods of time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1adf7-113">如果你需要在同一个操作中更新多个行，则创建事务要比使用保守式锁定更具伸缩性。</span><span class="sxs-lookup"><span data-stu-id="1adf7-113">If you need to update multiple rows in the same operation, then creating a transaction is a more scalable option than using pessimistic locking.</span></span>  
  
 <span data-ttu-id="1adf7-114">对比之下，使用开放式并发的用户在读取行时不会锁定该行。</span><span class="sxs-lookup"><span data-stu-id="1adf7-114">By contrast, users who use optimistic concurrency do not lock a row when reading it.</span></span> <span data-ttu-id="1adf7-115">当用户要更新某行时，应用程序必须确定自读取该行以来，其他用户是否更改了该行。</span><span class="sxs-lookup"><span data-stu-id="1adf7-115">When a user wants to update a row, the application must determine whether another user has changed the row since it was read.</span></span> <span data-ttu-id="1adf7-116">开放式并发通常用于对数据争用较少的环境。</span><span class="sxs-lookup"><span data-stu-id="1adf7-116">Optimistic concurrency is generally used in environments with a low contention for data.</span></span> <span data-ttu-id="1adf7-117">由于不需要锁定任何记录，开放式并发将会提高性能，因为锁定记录需要更多的服务器资源。</span><span class="sxs-lookup"><span data-stu-id="1adf7-117">Optimistic concurrency improves performance because no locking of records is required, and locking of records requires additional server resources.</span></span> <span data-ttu-id="1adf7-118">另外，为了维护记录锁，需要与数据库服务器保持持久连接。</span><span class="sxs-lookup"><span data-stu-id="1adf7-118">Also, in order to maintain record locks, a persistent connection to the database server is required.</span></span> <span data-ttu-id="1adf7-119">由于在开放式并发模型中并不会这样，所以与服务器的连接可以在较少的时间内为更多的客户端提供服务。</span><span class="sxs-lookup"><span data-stu-id="1adf7-119">Because this is not the case in an optimistic concurrency model, connections to the server are free to serve a larger number of clients in less time.</span></span>  
  
 <span data-ttu-id="1adf7-120">在开放式并发模型中，如果当某用户接收到来自数据库的值后，另一用户在该用户试图修改该值之前即将其修改，则认为发生了冲突。</span><span class="sxs-lookup"><span data-stu-id="1adf7-120">In an optimistic concurrency model, a violation is considered to have occurred if, after a user receives a value from the database, another user modifies the value before the first user has attempted to modify it.</span></span> <span data-ttu-id="1adf7-121">首先通过以下示例说明服务器如何解决并发冲突。</span><span class="sxs-lookup"><span data-stu-id="1adf7-121">How the server resolves a concurrency violation is best shown by first describing the following example.</span></span>  
  
 <span data-ttu-id="1adf7-122">以下各表是根据一个开放式并发示例生成的。</span><span class="sxs-lookup"><span data-stu-id="1adf7-122">The following tables follow an example of optimistic concurrency.</span></span>  
  
 <span data-ttu-id="1adf7-123">下午 1:00，用户 1 从具有以下值的数据库中读取一行：</span><span class="sxs-lookup"><span data-stu-id="1adf7-123">At 1:00 p.m., User1 reads a row from the database with the following values:</span></span>  
  
 <span data-ttu-id="1adf7-124">**CustID&amp;#xA0;&amp;#xA0;&amp;#xA0;&amp;#xA0;&amp;#xA0;LastName&amp;#xA0;&amp;#xA0;&amp;#xA0;&amp;#xA0;&amp;#xA0;FirstName**</span><span class="sxs-lookup"><span data-stu-id="1adf7-124">**CustID     LastName     FirstName**</span></span>  
  
 <span data-ttu-id="1adf7-125">101SmithBob</span><span class="sxs-lookup"><span data-stu-id="1adf7-125">101          Smith             Bob</span></span>  
  
|<span data-ttu-id="1adf7-126">列名称</span><span class="sxs-lookup"><span data-stu-id="1adf7-126">Column name</span></span>|<span data-ttu-id="1adf7-127">原始值</span><span class="sxs-lookup"><span data-stu-id="1adf7-127">Original value</span></span>|<span data-ttu-id="1adf7-128">当前值</span><span class="sxs-lookup"><span data-stu-id="1adf7-128">Current value</span></span>|<span data-ttu-id="1adf7-129">数据库中的值</span><span class="sxs-lookup"><span data-stu-id="1adf7-129">Value in database</span></span>|  
|-----------------|--------------------|-------------------|-----------------------|  
|<span data-ttu-id="1adf7-130">CustID</span><span class="sxs-lookup"><span data-stu-id="1adf7-130">CustID</span></span>|<span data-ttu-id="1adf7-131">101</span><span class="sxs-lookup"><span data-stu-id="1adf7-131">101</span></span>|<span data-ttu-id="1adf7-132">101</span><span class="sxs-lookup"><span data-stu-id="1adf7-132">101</span></span>|<span data-ttu-id="1adf7-133">101</span><span class="sxs-lookup"><span data-stu-id="1adf7-133">101</span></span>|  
|<span data-ttu-id="1adf7-134">LastName</span><span class="sxs-lookup"><span data-stu-id="1adf7-134">LastName</span></span>|<span data-ttu-id="1adf7-135">Smith</span><span class="sxs-lookup"><span data-stu-id="1adf7-135">Smith</span></span>|<span data-ttu-id="1adf7-136">Smith</span><span class="sxs-lookup"><span data-stu-id="1adf7-136">Smith</span></span>|<span data-ttu-id="1adf7-137">Smith</span><span class="sxs-lookup"><span data-stu-id="1adf7-137">Smith</span></span>|  
|<span data-ttu-id="1adf7-138">FirstName</span><span class="sxs-lookup"><span data-stu-id="1adf7-138">FirstName</span></span>|<span data-ttu-id="1adf7-139">Bob</span><span class="sxs-lookup"><span data-stu-id="1adf7-139">Bob</span></span>|<span data-ttu-id="1adf7-140">Bob</span><span class="sxs-lookup"><span data-stu-id="1adf7-140">Bob</span></span>|<span data-ttu-id="1adf7-141">Bob</span><span class="sxs-lookup"><span data-stu-id="1adf7-141">Bob</span></span>|  
  
 <span data-ttu-id="1adf7-142">下午 1:01，用户 2 读取同一行。</span><span class="sxs-lookup"><span data-stu-id="1adf7-142">At 1:01 p.m., User2 reads the same row.</span></span>  
  
 <span data-ttu-id="1adf7-143">下午 1:03，用户 2 将 FirstName 从“Bob”更改为“Robert”并更新数据库。</span><span class="sxs-lookup"><span data-stu-id="1adf7-143">At 1:03 p.m., User2 changes **FirstName** from "Bob" to "Robert" and updates the database.</span></span>  
  
|<span data-ttu-id="1adf7-144">列名称</span><span class="sxs-lookup"><span data-stu-id="1adf7-144">Column name</span></span>|<span data-ttu-id="1adf7-145">原始值</span><span class="sxs-lookup"><span data-stu-id="1adf7-145">Original value</span></span>|<span data-ttu-id="1adf7-146">当前值</span><span class="sxs-lookup"><span data-stu-id="1adf7-146">Current value</span></span>|<span data-ttu-id="1adf7-147">数据库中的值</span><span class="sxs-lookup"><span data-stu-id="1adf7-147">Value in database</span></span>|  
|-----------------|--------------------|-------------------|-----------------------|  
|<span data-ttu-id="1adf7-148">CustID</span><span class="sxs-lookup"><span data-stu-id="1adf7-148">CustID</span></span>|<span data-ttu-id="1adf7-149">101</span><span class="sxs-lookup"><span data-stu-id="1adf7-149">101</span></span>|<span data-ttu-id="1adf7-150">101</span><span class="sxs-lookup"><span data-stu-id="1adf7-150">101</span></span>|<span data-ttu-id="1adf7-151">101</span><span class="sxs-lookup"><span data-stu-id="1adf7-151">101</span></span>|  
|<span data-ttu-id="1adf7-152">LastName</span><span class="sxs-lookup"><span data-stu-id="1adf7-152">LastName</span></span>|<span data-ttu-id="1adf7-153">Smith</span><span class="sxs-lookup"><span data-stu-id="1adf7-153">Smith</span></span>|<span data-ttu-id="1adf7-154">Smith</span><span class="sxs-lookup"><span data-stu-id="1adf7-154">Smith</span></span>|<span data-ttu-id="1adf7-155">Smith</span><span class="sxs-lookup"><span data-stu-id="1adf7-155">Smith</span></span>|  
|<span data-ttu-id="1adf7-156">FirstName</span><span class="sxs-lookup"><span data-stu-id="1adf7-156">FirstName</span></span>|<span data-ttu-id="1adf7-157">Bob</span><span class="sxs-lookup"><span data-stu-id="1adf7-157">Bob</span></span>|<span data-ttu-id="1adf7-158">Robert</span><span class="sxs-lookup"><span data-stu-id="1adf7-158">Robert</span></span>|<span data-ttu-id="1adf7-159">Bob</span><span class="sxs-lookup"><span data-stu-id="1adf7-159">Bob</span></span>|  
  
 <span data-ttu-id="1adf7-160">由于更新时数据库中的值匹配用户 2 具有的原始值，因此更新成功。</span><span class="sxs-lookup"><span data-stu-id="1adf7-160">The update succeeds because the values in the database at the time of update match the original values that User2 has.</span></span>  
  
 <span data-ttu-id="1adf7-161">下午 1:05，用户 1 将“Bob”的名更改为“James”并试图更新该行。</span><span class="sxs-lookup"><span data-stu-id="1adf7-161">At 1:05 p.m., User1 changes "Bob"'s first name to "James" and tries to update the row.</span></span>  
  
|<span data-ttu-id="1adf7-162">列名称</span><span class="sxs-lookup"><span data-stu-id="1adf7-162">Column name</span></span>|<span data-ttu-id="1adf7-163">原始值</span><span class="sxs-lookup"><span data-stu-id="1adf7-163">Original value</span></span>|<span data-ttu-id="1adf7-164">当前值</span><span class="sxs-lookup"><span data-stu-id="1adf7-164">Current value</span></span>|<span data-ttu-id="1adf7-165">数据库中的值</span><span class="sxs-lookup"><span data-stu-id="1adf7-165">Value in database</span></span>|  
|-----------------|--------------------|-------------------|-----------------------|  
|<span data-ttu-id="1adf7-166">CustID</span><span class="sxs-lookup"><span data-stu-id="1adf7-166">CustID</span></span>|<span data-ttu-id="1adf7-167">101</span><span class="sxs-lookup"><span data-stu-id="1adf7-167">101</span></span>|<span data-ttu-id="1adf7-168">101</span><span class="sxs-lookup"><span data-stu-id="1adf7-168">101</span></span>|<span data-ttu-id="1adf7-169">101</span><span class="sxs-lookup"><span data-stu-id="1adf7-169">101</span></span>|  
|<span data-ttu-id="1adf7-170">LastName</span><span class="sxs-lookup"><span data-stu-id="1adf7-170">LastName</span></span>|<span data-ttu-id="1adf7-171">Smith</span><span class="sxs-lookup"><span data-stu-id="1adf7-171">Smith</span></span>|<span data-ttu-id="1adf7-172">Smith</span><span class="sxs-lookup"><span data-stu-id="1adf7-172">Smith</span></span>|<span data-ttu-id="1adf7-173">Smith</span><span class="sxs-lookup"><span data-stu-id="1adf7-173">Smith</span></span>|  
|<span data-ttu-id="1adf7-174">FirstName</span><span class="sxs-lookup"><span data-stu-id="1adf7-174">FirstName</span></span>|<span data-ttu-id="1adf7-175">Bob</span><span class="sxs-lookup"><span data-stu-id="1adf7-175">Bob</span></span>|<span data-ttu-id="1adf7-176">James</span><span class="sxs-lookup"><span data-stu-id="1adf7-176">James</span></span>|<span data-ttu-id="1adf7-177">Robert</span><span class="sxs-lookup"><span data-stu-id="1adf7-177">Robert</span></span>|  
  
 <span data-ttu-id="1adf7-178">此时，由于数据库中的值（“Robert”）不再匹配 User1 所预期的原始值（“Bob”），因此 User1 遇到开放式并发冲突。</span><span class="sxs-lookup"><span data-stu-id="1adf7-178">At this point, User1 encounters an optimistic concurrency violation because the value in the database ("Robert") no longer matches the original value that User1 was expecting ("Bob").</span></span> <span data-ttu-id="1adf7-179">并发冲突仅向您表明更新失败。</span><span class="sxs-lookup"><span data-stu-id="1adf7-179">The concurrency violation simply lets you know that the update failed.</span></span> <span data-ttu-id="1adf7-180">现在，需要决定是用用户 1 提供的更改来重写用户 2 提供的更改还是取消用户 1 的更改。</span><span class="sxs-lookup"><span data-stu-id="1adf7-180">The decision now needs to be made whether to overwrite the changes supplied by User2 with the changes supplied by User1, or to cancel the changes by User1.</span></span>  
  
## <a name="testing-for-optimistic-concurrency-violations"></a><span data-ttu-id="1adf7-181">测试是否存在开放式并发冲突</span><span class="sxs-lookup"><span data-stu-id="1adf7-181">Testing for Optimistic Concurrency Violations</span></span>  

 <span data-ttu-id="1adf7-182">测试是否存在开放式并发冲突的方法有若干种。</span><span class="sxs-lookup"><span data-stu-id="1adf7-182">There are several techniques for testing for an optimistic concurrency violation.</span></span> <span data-ttu-id="1adf7-183">其中一种涉及到在表中包含时间戳列。</span><span class="sxs-lookup"><span data-stu-id="1adf7-183">One involves including a timestamp column in the table.</span></span> <span data-ttu-id="1adf7-184">数据库通常会提供时间戳功能，该功能可用于标识上次更新记录的日期和时间。</span><span class="sxs-lookup"><span data-stu-id="1adf7-184">Databases commonly provide timestamp functionality that can be used to identify the date and time when the record was last updated.</span></span> <span data-ttu-id="1adf7-185">当使用这种方法时，将在表定义中包含时间戳列。</span><span class="sxs-lookup"><span data-stu-id="1adf7-185">Using this technique, a timestamp column is included in the table definition.</span></span> <span data-ttu-id="1adf7-186">每当更新记录时，时间戳都将得到更新，以反映当前的日期和时间。</span><span class="sxs-lookup"><span data-stu-id="1adf7-186">Whenever the record is updated, the timestamp is updated to reflect the current date and time.</span></span> <span data-ttu-id="1adf7-187">在测试是否存在开放式并发冲突时，对表内容的任何查询都会返回时间戳列。</span><span class="sxs-lookup"><span data-stu-id="1adf7-187">In a test for optimistic concurrency violations, the timestamp column is returned with any query of the contents of the table.</span></span> <span data-ttu-id="1adf7-188">当试图执行更新时，数据库中的时间戳值将与所修改行中包含的原始时间戳值进行比较。</span><span class="sxs-lookup"><span data-stu-id="1adf7-188">When an update is attempted, the timestamp value in the database is compared to the original timestamp value contained in the modified row.</span></span> <span data-ttu-id="1adf7-189">如果两者匹配，则会执行更新，并用当前时间更新时间戳列以反映更新。</span><span class="sxs-lookup"><span data-stu-id="1adf7-189">If they match, the update is performed and the timestamp column is updated with the current time to reflect the update.</span></span> <span data-ttu-id="1adf7-190">如果两者不匹配，则发生了开放式并发冲突。</span><span class="sxs-lookup"><span data-stu-id="1adf7-190">If they do not match, an optimistic concurrency violation has occurred.</span></span>  
  
 <span data-ttu-id="1adf7-191">测试是否存在开放式并发冲突的另一种方法是验证某行中的所有原始列值是否仍匹配数据库中的相应值。</span><span class="sxs-lookup"><span data-stu-id="1adf7-191">Another technique for testing for an optimistic concurrency violation is to verify that all the original column values in a row still match those found in the database.</span></span> <span data-ttu-id="1adf7-192">例如，考虑以下查询：</span><span class="sxs-lookup"><span data-stu-id="1adf7-192">For example, consider the following query:</span></span>  
  
```sql
SELECT Col1, Col2, Col3 FROM Table1  
```  
  
 <span data-ttu-id="1adf7-193">若要在更新 Table1 中的某行时测试是否存在乐观并发冲突，请发出以下 UPDATE 语句：</span><span class="sxs-lookup"><span data-stu-id="1adf7-193">To test for an optimistic concurrency violation when updating a row in **Table1**, you would issue the following UPDATE statement:</span></span>  
  
```sql
UPDATE Table1 Set Col1 = @NewCol1Value,  
              Set Col2 = @NewCol2Value,  
              Set Col3 = @NewCol3Value  
WHERE Col1 = @OldCol1Value AND  
      Col2 = @OldCol2Value AND  
      Col3 = @OldCol3Value  
```  
  
 <span data-ttu-id="1adf7-194">只要原始值匹配数据库中的值，就会执行更新。</span><span class="sxs-lookup"><span data-stu-id="1adf7-194">As long as the original values match the values in the database, the update is performed.</span></span> <span data-ttu-id="1adf7-195">如果已修改某个值，由于 WHERE 子句找不到匹配项，更新将不会修改该行。</span><span class="sxs-lookup"><span data-stu-id="1adf7-195">If a value has been modified, the update will not modify the row because the WHERE clause will not find a match.</span></span>  
  
 <span data-ttu-id="1adf7-196">请注意，建议始终在查询中返回唯一的主键值。</span><span class="sxs-lookup"><span data-stu-id="1adf7-196">Note that it is recommended to always return a unique primary key value in your query.</span></span> <span data-ttu-id="1adf7-197">否则，以上 UPDATE 语句会更新多个行，这可能会有悖于您的意图。</span><span class="sxs-lookup"><span data-stu-id="1adf7-197">Otherwise, the preceding UPDATE statement may update more than one row, which might not be your intent.</span></span>  
  
 <span data-ttu-id="1adf7-198">如果数据源中的列允许空值，则可能需要扩展 WHERE 子句，以查找本地表和数据源中的匹配空引用。</span><span class="sxs-lookup"><span data-stu-id="1adf7-198">If a column at your data source allows nulls, you may need to extend your WHERE clause to check for a matching null reference in your local table and at the data source.</span></span> <span data-ttu-id="1adf7-199">例如，以下 UPDATE 语句验证本地行中的空引用是否仍匹配数据源中的空引用，或者本地行中的值是否匹配数据源中的值。</span><span class="sxs-lookup"><span data-stu-id="1adf7-199">For example, the following UPDATE statement verifies that a null reference in the local row still matches a null reference at the data source, or that the value in the local row still matches the value at the data source.</span></span>  
  
```sql
UPDATE Table1 Set Col1 = @NewVal1  
  WHERE (@OldVal1 IS NULL AND Col1 IS NULL) OR Col1 = @OldVal1  
```  
  
 <span data-ttu-id="1adf7-200">当使用开放式并发模型时，也可以选择应用限制较少的条件。</span><span class="sxs-lookup"><span data-stu-id="1adf7-200">You may also choose to apply less restrictive criteria when using an optimistic concurrency model.</span></span> <span data-ttu-id="1adf7-201">例如，如果只在 WHERE 子句中使用主键列，那么无论自上次查询以来是否已更新其他列，数据都将被重写。</span><span class="sxs-lookup"><span data-stu-id="1adf7-201">For example, using only the primary key columns in the WHERE clause causes the data to be overwritten regardless of whether the other columns have been updated since the last query.</span></span> <span data-ttu-id="1adf7-202">也可以只将 WHERE 子句应用于特定列，除非自上次查询特定字段以来已将其更新，否则数据也会被重写。</span><span class="sxs-lookup"><span data-stu-id="1adf7-202">You can also apply a WHERE clause only to specific columns, resulting in data being overwritten unless particular fields have been updated since they were last queried.</span></span>  
  
### <a name="the-dataadapterrowupdated-event"></a><span data-ttu-id="1adf7-203">DataAdapter.RowUpdated 事件</span><span class="sxs-lookup"><span data-stu-id="1adf7-203">The DataAdapter.RowUpdated Event</span></span>  

 <span data-ttu-id="1adf7-204"><xref:System.Data.Common.DataAdapter> 对象的 RowUpdated 事件可以与上述方法一起用来向应用程序提供有关乐观并发冲突的通知。</span><span class="sxs-lookup"><span data-stu-id="1adf7-204">The **RowUpdated** event of the <xref:System.Data.Common.DataAdapter> object can be used in conjunction with the techniques described earlier, to provide notification to your application of optimistic concurrency violations.</span></span> <span data-ttu-id="1adf7-205">在每次尝试从 DataSet 更新 Modified 行之后，都会发生 RowUpdated  。</span><span class="sxs-lookup"><span data-stu-id="1adf7-205">**RowUpdated** occurs after each attempt to update a **Modified** row from a **DataSet**.</span></span> <span data-ttu-id="1adf7-206">它使您能够添加特殊的处理代码，包括在发生异常时进行处理，添加自定义错误信息，添加重试逻辑等。</span><span class="sxs-lookup"><span data-stu-id="1adf7-206">This enables you to add special handling code, including processing when an exception occurs, adding custom error information, adding retry logic, and so on.</span></span> <span data-ttu-id="1adf7-207"><xref:System.Data.Common.RowUpdatedEventArgs> 对象为表中已修改的行返回 RecordsAffected 属性，其中包含特定更新命令所影响的行数。</span><span class="sxs-lookup"><span data-stu-id="1adf7-207">The <xref:System.Data.Common.RowUpdatedEventArgs> object returns a **RecordsAffected** property containing the number of rows affected by a particular update command for a modified row in a table.</span></span> <span data-ttu-id="1adf7-208">通过设置更新命令来测试是否存在乐观并发，如果乐观并发冲突已发生，由于没有更新任何记录，因此 RecordsAffected 属性最终将返回值 0。</span><span class="sxs-lookup"><span data-stu-id="1adf7-208">By setting the update command to test for optimistic concurrency, the **RecordsAffected** property will, as a result, return a value of 0 when an optimistic concurrency violation has occurred, because no records were updated.</span></span> <span data-ttu-id="1adf7-209">如果是这种情况，则将引发异常。</span><span class="sxs-lookup"><span data-stu-id="1adf7-209">If this is the case, an exception is thrown.</span></span> <span data-ttu-id="1adf7-210">RowUpdated 事件使你能够通过设置合适的 RowUpdatedEventArgs.Status 值（例如 UpdateStatus.SkipCurrentRow）来处理这种情况并避免异常  。</span><span class="sxs-lookup"><span data-stu-id="1adf7-210">The **RowUpdated** event enables you to handle this occurrence and avoid the exception by setting an appropriate **RowUpdatedEventArgs.Status** value, such as **UpdateStatus.SkipCurrentRow**.</span></span> <span data-ttu-id="1adf7-211">有关 RowUpdated 事件的详细信息，请参阅[处理 DataAdapter 事件](handling-dataadapter-events.md)。</span><span class="sxs-lookup"><span data-stu-id="1adf7-211">For more information about the **RowUpdated** event, see [Handling DataAdapter Events](handling-dataadapter-events.md).</span></span>  
  
 <span data-ttu-id="1adf7-212">或者，可以在调用 Update 之前将 DataAdapter.ContinueUpdateOnError 设置为 true，并在完成 Update 后响应存储在特定行的 RowError 属性中的错误信息    。</span><span class="sxs-lookup"><span data-stu-id="1adf7-212">Optionally, you can set **DataAdapter.ContinueUpdateOnError** to **true**, before calling **Update**, and respond to the error information stored in the **RowError** property of a particular row when the **Update** is completed.</span></span> <span data-ttu-id="1adf7-213">有关详细信息，请参阅 [Row Error 信息](./dataset-datatable-dataview/row-error-information.md)。</span><span class="sxs-lookup"><span data-stu-id="1adf7-213">For more information, see [Row Error Information](./dataset-datatable-dataview/row-error-information.md).</span></span>  
  
## <a name="optimistic-concurrency-example"></a><span data-ttu-id="1adf7-214">开放式并发示例</span><span class="sxs-lookup"><span data-stu-id="1adf7-214">Optimistic Concurrency Example</span></span>  

 <span data-ttu-id="1adf7-215">下面是一个简单的示例，通过设置 DataAdapter 的 UpdateCommand 来测试是否存在乐观并发，然后使用 RowUpdated 事件来测试是否存在乐观并发冲突  。</span><span class="sxs-lookup"><span data-stu-id="1adf7-215">The following is a simple example that sets the **UpdateCommand** of a **DataAdapter** to test for optimistic concurrency, and then uses the **RowUpdated** event to test for optimistic concurrency violations.</span></span> <span data-ttu-id="1adf7-216">当遇到乐观并发冲突时，应用程序将设置发出更新命令的目标行的 RowError，以反映乐观并发冲突。</span><span class="sxs-lookup"><span data-stu-id="1adf7-216">When an optimistic concurrency violation is encountered, the application sets the **RowError** of the row that the update was issued for to reflect an optimistic concurrency violation.</span></span>  
  
 <span data-ttu-id="1adf7-217">请注意，传递给 UPDATE 命令的 WHERE 子句的参数值映射到其相应列的 Original 值。</span><span class="sxs-lookup"><span data-stu-id="1adf7-217">Note that the parameter values passed to the WHERE clause of the UPDATE command are mapped to the **Original** values of their respective columns.</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers ORDER BY CustomerID", _  
  connection)  
  
' The Update command checks for optimistic concurrency violations  
' in the WHERE clause.  
adapter.UpdateCommand = New SqlCommand("UPDATE Customers " &  
  "(CustomerID, CompanyName) VALUES(@CustomerID, @CompanyName) " & _  
  "WHERE CustomerID = @oldCustomerID AND CompanyName = " &  
  "@oldCompanyName", connection)  
adapter.UpdateCommand.Parameters.Add( _  
  "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
adapter.UpdateCommand.Parameters.Add( _  
  "@CompanyName", SqlDbType.NVarChar, 30, "CompanyName")  
  
' Pass the original values to the WHERE clause parameters.  
Dim parameter As SqlParameter = adapter.UpdateCommand.Parameters.Add( _  
  "@oldCustomerID", SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
parameter = adapter.UpdateCommand.Parameters.Add( _  
  "@oldCompanyName", SqlDbType.NVarChar, 30, "CompanyName")  
parameter.SourceVersion = DataRowVersion.Original  
  
' Add the RowUpdated event handler.  
AddHandler adapter.RowUpdated, New SqlRowUpdatedEventHandler( _  
  AddressOf OnRowUpdated)  
  
Dim dataSet As DataSet = New DataSet()  
adapter.Fill(dataSet, "Customers")  
  
' Modify the DataSet contents.  
adapter.Update(dataSet, "Customers")  
  
Dim dataRow As DataRow  
  
For Each dataRow In dataSet.Tables("Customers").Rows  
    If dataRow.HasErrors Then
       Console.WriteLine(dataRow (0) & vbCrLf & dataRow.RowError)  
    End If  
Next  
  
Private Shared Sub OnRowUpdated( _  
  sender As object, args As SqlRowUpdatedEventArgs)  
   If args.RecordsAffected = 0  
      args.Row.RowError = "Optimistic Concurrency Violation!"  
      args.Status = UpdateStatus.SkipCurrentRow  
   End If  
End Sub  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
SqlDataAdapter adapter = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers ORDER BY CustomerID",  
  connection);  
  
// The Update command checks for optimistic concurrency violations  
// in the WHERE clause.  
adapter.UpdateCommand = new SqlCommand("UPDATE Customers Set CustomerID = @CustomerID, CompanyName = @CompanyName " +  
   "WHERE CustomerID = @oldCustomerID AND CompanyName = @oldCompanyName", connection);  
adapter.UpdateCommand.Parameters.Add(  
  "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
adapter.UpdateCommand.Parameters.Add(  
  "@CompanyName", SqlDbType.NVarChar, 30, "CompanyName");  
  
// Pass the original values to the WHERE clause parameters.  
SqlParameter parameter = adapter.UpdateCommand.Parameters.Add(  
  "@oldCustomerID", SqlDbType.NChar, 5, "CustomerID");  
parameter.SourceVersion = DataRowVersion.Original;  
parameter = adapter.UpdateCommand.Parameters.Add(  
  "@oldCompanyName", SqlDbType.NVarChar, 30, "CompanyName");  
parameter.SourceVersion = DataRowVersion.Original;  
  
// Add the RowUpdated event handler.  
adapter.RowUpdated += new SqlRowUpdatedEventHandler(OnRowUpdated);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, "Customers");  
  
// Modify the DataSet contents.  
  
adapter.Update(dataSet, "Customers");  
  
foreach (DataRow dataRow in dataSet.Tables["Customers"].Rows)  
{  
    if (dataRow.HasErrors)  
       Console.WriteLine(dataRow [0] + "\n" + dataRow.RowError);  
}  
  
protected static void OnRowUpdated(object sender, SqlRowUpdatedEventArgs args)  
{  
  if (args.RecordsAffected == 0)
  {  
    args.Row.RowError = "Optimistic Concurrency Violation Encountered";  
    args.Status = UpdateStatus.SkipCurrentRow;  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="1adf7-218">请参阅</span><span class="sxs-lookup"><span data-stu-id="1adf7-218">See also</span></span>

- [<span data-ttu-id="1adf7-219">在 ADO.NET 中检索和修改数据</span><span class="sxs-lookup"><span data-stu-id="1adf7-219">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="1adf7-220">使用 DataAdapter 更新数据源</span><span class="sxs-lookup"><span data-stu-id="1adf7-220">Updating Data Sources with DataAdapters</span></span>](updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="1adf7-221">行错误信息</span><span class="sxs-lookup"><span data-stu-id="1adf7-221">Row Error Information</span></span>](./dataset-datatable-dataview/row-error-information.md)
- [<span data-ttu-id="1adf7-222">事务和并发</span><span class="sxs-lookup"><span data-stu-id="1adf7-222">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)
- [<span data-ttu-id="1adf7-223">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="1adf7-223">ADO.NET Overview</span></span>](ado-net-overview.md)
