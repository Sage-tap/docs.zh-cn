---
description: 详细了解：操作说明：在 Visual Basic 中更改用户设置
title: 如何：更改用户设置
ms.date: 07/20/2015
helpviewer_keywords:
- user settings [Visual Basic], changing in Visual Basic
- user settings
- My.Settings object [Visual Basic], changing user settings
- examples [Visual Basic], changing user settings
ms.assetid: 41250181-c594-4854-9988-8183b9eb03cf
ms.openlocfilehash: 3877c9fadbf1b5b79470dc9ad41fbaf8123e6770
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797856"
---
# <a name="how-to-change-user-settings-in-visual-basic"></a>如何：在 Visual Basic 中更改用户设置

可以通过将新值赋予 `My.Settings` 对象上的设置属性来更改用户设置。  
  
 `My.Settings` 对象将每个设置公开为一个属性。 属性名称就是设置的名称，属性类型就是设置类型。 设置的“范围”决定属性是否为只读；“应用程序”范围设置的属性是只读属性，而“用户”范围设置的属性是读-写属性。 有关详细信息，请参阅 [My.Settings 对象](../../../language-reference/objects/my-settings-object.md)。  
  
> [!NOTE]
> 虽然可以在运行时更改并保存用户范围设置的值，但是应用程序范围设置是只读的，不能以编程方式进行更改。 可以在创建应用程序时通过“项目设计器”，或者编辑应用程序的配置文件来更改应用程序范围设置。 有关详细信息，请参阅[管理应用程序设置 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)。  
  
## <a name="example"></a>示例  

 此示例更改 `Nickname` 用户设置的值。  
  
 [!code-vb[VbVbalrMyResources#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#7)]  
  
 若要使用本示例，应用程序必须具有类型为 `String` 的 `Nickname` 用户设置。  
  
 应用程序在关闭时会保存用户设置。 若要立即保存设置，请调用 `My.Settings.Save` 方法。 有关详细信息，请参阅[如何：在 Visual Basic 中保存用户设置](how-to-persist-user-settings.md)。  
  
## <a name="see-also"></a>另请参阅

- [My.Settings 对象](../../../language-reference/objects/my-settings-object.md)
- [如何：在 Visual Basic 中读取应用程序设置](how-to-read-application-settings.md)
- [如何：在 Visual Basic 中暂留用户设置](how-to-persist-user-settings.md)
- [如何：在 Visual Basic 中为用户设置创建属性网格](how-to-create-property-grids-for-user-settings.md)
- [管理应用程序设置 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
