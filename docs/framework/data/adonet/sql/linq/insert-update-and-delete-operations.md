---
description: 了解详细信息：插入、更新和删除操作
title: 插入、更新和删除操作
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 26a43a4f-83c9-4732-806d-bb23aad0ff6b
ms.openlocfilehash: 2d0470ed6abe654ca08f954c3de97de207adb75d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803810"
---
# <a name="insert-update-and-delete-operations"></a>插入、更新和删除操作

在 `Insert` 中执行 `Update`、`Delete` 和 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 操作的方法是：向对象模型中添加对象、更改和移除对象模型中的对象。 默认情况下，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 会将您所做的操作转换成 SQL，然后将这些更改提交至数据库。

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 在操作和保持对对象所做更改方面有着最大的灵活性。 实体对象可用（通过查询检索它们或通过重新构造它们）后，就可以像应用程序中的典型对象一样更改实体对象。 也就是说，可以更改它们的值，将它们添加到集合中，以及从集合中移除它们。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 会跟踪您所做的更改，并且在您调用 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 时就可以将这些更改传回数据库。

> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 不支持且无法识别级联删除操作。 如果要删除表中具有约束的行，则必须在 `ON DELETE CASCADE` 数据库的外键约束中设置规则，或者使用自己的代码先删除阻止删除父对象的子对象的子对象。 否则会引发异常。 有关详细信息，请参阅 [如何：从数据库中删除行](how-to-delete-rows-from-the-database.md)。

以下摘录会用到 Northwind 示例数据库中的 `Customer` 和 `Order` 类。 为简洁起见，不显示类定义。

[!code-csharp[DLinqCRUDOps#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCRUDOps/cs/Program.cs#1)]
[!code-vb[DLinqCRUDOps#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCRUDOps/vb/Module1.vb#1)]

当您调用 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 时，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 会自动生成并执行它为将您所做的更改传回数据库而必须具备的 SQL 命令。

> [!NOTE]
> 您可以使用自己的自定义逻辑来重写此行为，这通常是通过存储过程来实现的。 有关详细信息，请参阅 [开发人员在重写默认行为中的责任](responsibilities-of-the-developer-in-overriding-default-behavior.md)。
>
> 使用 Visual Studio 的开发人员可以使用对象关系设计器来开发用于实现此目的的存储过程。

## <a name="see-also"></a>请参阅

- [下载示例数据库](downloading-sample-databases.md)
- [自定义插入、更新和删除操作](customizing-insert-update-and-delete-operations.md)
