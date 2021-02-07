---
description: 了解详细信息： User-Defined 函数
title: 用户定义函数
ms.date: 03/30/2017
ms.assetid: 3304c9b2-5c7a-4a95-9d45-4f260dcb606e
ms.openlocfilehash: d27abd78e15ad6cb5ce4e9440ac425159a0b5bdc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99680936"
---
# <a name="user-defined-functions"></a>用户定义函数

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 在您的对象模型中使用方法来表示用户定义的函数。 您可以通过应用 <xref:System.Data.Linq.Mapping.FunctionAttribute> 属性和 <xref:System.Data.Linq.Mapping.ParameterAttribute> 属性（如果需要）将方法指定为函数。 有关详细信息，请参阅 [LINQ to SQL 对象模型](the-linq-to-sql-object-model.md)。  
  
 为避免出现 <xref:System.InvalidOperationException>，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中用户定义的函数必须采用以下形式之一：  
  
- 包装为具有正确映射属性的方法调用的函数。 有关详细信息，请参阅 [基于属性的映射](attribute-based-mapping.md)。  
  
- 特定于 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的静态 SQL 方法。  
  
- .NET Framework 方法支持的函数。  
  
 本节中的主题说明了在您自行编写代码的情况下，如何在您的应用程序中构建和调用这些方法。 使用 Visual Studio 的开发人员通常会使用对象关系设计器来映射用户定义的函数。  
  
## <a name="in-this-section"></a>本节内容  

 [如何：使用标量值用户定义的函数](how-to-use-scalar-valued-user-defined-functions.md)  
 介绍如何实现返回标量值的函数。  
  
 [如何：使用表值用户定义的函数](how-to-use-table-valued-user-defined-functions.md)  
 介绍如何实现返回表值的函数。  
  
 [如何：以内联方式调用用户定义的函数](how-to-call-user-defined-functions-inline.md)  
 介绍如何对函数进行内联调用，以及进行内联调用时在执行方面的差异。
