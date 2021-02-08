---
description: 了解详细信息：如何：将更改提交到数据库
title: 如何：将更改提交到数据库
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c7cba174-9d40-491d-b32c-f2d73b7e9eab
ms.openlocfilehash: 31d85d94c74315a127b18bd41b4d1d1a7fe7d0b2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785844"
---
# <a name="how-to-submit-changes-to-the-database"></a><span data-ttu-id="7587e-103">如何：将更改提交到数据库</span><span class="sxs-lookup"><span data-stu-id="7587e-103">How to: Submit Changes to the Database</span></span>

<span data-ttu-id="7587e-104">无论您对对象做了多少项更改，都只是在更改内存中的副本。</span><span class="sxs-lookup"><span data-stu-id="7587e-104">Regardless of how many changes you make to your objects, changes are made only to in-memory replicas.</span></span> <span data-ttu-id="7587e-105">您并未对数据库中的实际数据做任何更改。</span><span class="sxs-lookup"><span data-stu-id="7587e-105">You have made no changes to the actual data in the database.</span></span> <span data-ttu-id="7587e-106">直到您对 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 显式调用 <xref:System.Data.Linq.DataContext>，您所做的更改才会传输到服务器。</span><span class="sxs-lookup"><span data-stu-id="7587e-106">Your changes are not transmitted to the server until you explicitly call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> on the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 <span data-ttu-id="7587e-107">当您进行此调用时，<xref:System.Data.Linq.DataContext> 会设法将您所做的更改转换为等效的 SQL 命令。</span><span class="sxs-lookup"><span data-stu-id="7587e-107">When you make this call, the <xref:System.Data.Linq.DataContext> tries to translate your changes into equivalent SQL commands.</span></span> <span data-ttu-id="7587e-108">你可以使用自己的自定义逻辑来重写这些操作，但提交的顺序由 <xref:System.Data.Linq.DataContext> 称为 *更改处理器* 的服务进行协调。</span><span class="sxs-lookup"><span data-stu-id="7587e-108">You can use your own custom logic to override these actions, but the order of submission is orchestrated by a service of the <xref:System.Data.Linq.DataContext> known as the *change processor*.</span></span> <span data-ttu-id="7587e-109">事件的顺序如下：</span><span class="sxs-lookup"><span data-stu-id="7587e-109">The sequence of events is as follows:</span></span>  
  
1. <span data-ttu-id="7587e-110">当您调用 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 时，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 会检查已知对象的集合以确定新实例是否已附加到它们。</span><span class="sxs-lookup"><span data-stu-id="7587e-110">When you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] examines the set of known objects to determine whether new instances have been attached to them.</span></span> <span data-ttu-id="7587e-111">如果已附加，这些新实例将添加到被跟踪对象的集合。</span><span class="sxs-lookup"><span data-stu-id="7587e-111">If they have, these new instances are added to the set of tracked objects.</span></span>  
  
2. <span data-ttu-id="7587e-112">所有具有挂起更改的对象将按照它们之间的依赖关系排序成一个对象序列。</span><span class="sxs-lookup"><span data-stu-id="7587e-112">All objects that have pending changes are ordered into a sequence of objects based on the dependencies between them.</span></span> <span data-ttu-id="7587e-113">如果一个对象的更改依赖于其他对象，则这个对象将排在其依赖项之后。</span><span class="sxs-lookup"><span data-stu-id="7587e-113">Objects whose changes depend on other objects are sequenced after their dependencies.</span></span>  
  
3. <span data-ttu-id="7587e-114">在即将传输任何实际更改时，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 会启动一个事务来包装由各条命令组成的系列。</span><span class="sxs-lookup"><span data-stu-id="7587e-114">Immediately before any actual changes are transmitted, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] starts a transaction to encapsulate the series of individual commands.</span></span>  
  
4. <span data-ttu-id="7587e-115">对对象的更改会逐个转换为 SQL 命令，然后发送到服务器。</span><span class="sxs-lookup"><span data-stu-id="7587e-115">The changes to the objects are translated one by one to SQL commands and sent to the server.</span></span>  
  
 <span data-ttu-id="7587e-116">此时，如果数据库检测到任何错误，都会造成提交进程停止并引发异常。</span><span class="sxs-lookup"><span data-stu-id="7587e-116">At this point, any errors detected by the database cause the submission process to stop, and an exception is raised.</span></span> <span data-ttu-id="7587e-117">将回滚对数据库的所有更改，就像未进行过提交一样。</span><span class="sxs-lookup"><span data-stu-id="7587e-117">All changes to the database are rolled back as if no submissions ever occurred.</span></span> <span data-ttu-id="7587e-118"><xref:System.Data.Linq.DataContext> 仍具有所有更改的完整记录。</span><span class="sxs-lookup"><span data-stu-id="7587e-118">The <xref:System.Data.Linq.DataContext> still has a full recording of all changes.</span></span> <span data-ttu-id="7587e-119">因此你可以设法修正问题并重新调用 <xref:System.Data.Linq.DataContext.SubmitChanges%2A>，就像下面的代码示例中那样。</span><span class="sxs-lookup"><span data-stu-id="7587e-119">You can therefore try to correct the problem and call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> again, as in the code example that follows.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7587e-120">示例</span><span class="sxs-lookup"><span data-stu-id="7587e-120">Example</span></span>  

 <span data-ttu-id="7587e-121">用于执行提交的事务成功完成后，<xref:System.Data.Linq.DataContext> 就会通过忽略更改跟踪信息接受对对象的更改。</span><span class="sxs-lookup"><span data-stu-id="7587e-121">When the transaction around the submission is completed successfully, the <xref:System.Data.Linq.DataContext> accepts the changes to the objects by ignoring the change-tracking information.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#1)]
 [!code-vb[DLinqSubmittingChanges#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="7587e-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="7587e-122">See also</span></span>

- [<span data-ttu-id="7587e-123">如何：检测到并解决冲突的提交</span><span class="sxs-lookup"><span data-stu-id="7587e-123">How to: Detect and Resolve Conflicting Submissions</span></span>](how-to-detect-and-resolve-conflicting-submissions.md)
- [<span data-ttu-id="7587e-124">如何：管理更改冲突</span><span class="sxs-lookup"><span data-stu-id="7587e-124">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
- [<span data-ttu-id="7587e-125">下载示例数据库</span><span class="sxs-lookup"><span data-stu-id="7587e-125">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="7587e-126">进行和提交数据更改</span><span class="sxs-lookup"><span data-stu-id="7587e-126">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
